# FFMPEG
FFMPEG codes

- [Social Media Basic Video Editing](https://medium.com/abraia/basic-video-editing-for-social-media-with-ffmpeg-commands-1e873801659)
- Encoding requirement for IGTV : 
  - MP4 Container format
  - H.264 Video Codec
  - AAC Audio
  - 3500kbps bitrate
  - 30 FPS
  - 60 seconds maximum in length
  - 1080p 16:9 max (vertical or horizontal)


```
ffmpeg -i INPUT.MOV -vf scale=-2:720 -c:v libx264 -profile:v main -level:v 3.0 -x264-params scenecut=0:open_gop=0:min-keyint=72:keyint=72 -c:a aac -preset slow -crf 23 -r 30 -sn -f mp4 OUTPUT.mp4

```

-i INPUT.MOV - Input movie file.

-vf scale=-2:720 - Video filter to scale to 720p while keeping aspect ratio.

-c:v libx264 - Use x264 video codec.

-profile:v main -level:v 3.1 - Mostly for H.264 compatibility for older devices. This seems to be the profile Apple devices export to.

-x264-params scenecut=0:open_gop=0:min-keyint=72:keyint=72:ref=4 - Some x264 codec options I use to improve video for streaming.

-c:a aac - Use AAC audio codec.

-preset slow - Slower presets will result in better quality. Feel free to also try slower and veryslow.

-crf 23 - Constant Rate Factor encoding mode that adjusts the file data rate up or down to achieve a selected quality level rather than a specific data rate.

-b:v 3500k - Targets video bitrate to 3500k.

-b:a 256k - Targets audio bitrate to 256k.

-ar 44100 - Sets audio sample rate to 44.1 kHz.

-r 30 - Sets the framerate to 30.

-f mp4 - Sets the MP4 container format. This is optional if you have .mp4 in the output filename.

OUTPUT.mp4 - The encoded output movie file.
