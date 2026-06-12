---
title: "Rip Audio from SWF"
date: 2008-09-30
forum: General Help
---

### Post by Dr Small on 2008-09-30
Is there some possible way to rip the audio from a SWF? I have tried ffmpeg, but it told me that SWF is an unsupported format for ripping.

Any ideas?

---

### Post by KeyserSoze93 on 2008-09-30
For nearly any format to format conversion, I have found mencoder to be a decent candidate.

I've not tried it with swf (though I have successfully with flv), but this page describes how to convert swf to avi, and with a bit of tweaking, we get this command line:

mencoder file.swf -o file.wav -oa pcm -vo null -vc dummy

And then once that's done, you can just use lame or whatever to encode the wav into whatever format you want.

---

### Post by Dr Small on 2008-09-30
The above command wouldn't work, and kept telling me that -oa and -vo were not mencoder switches. So I removed them, and then mencoder gave this warning:
```
[swf @ 0x876cbe8]Compressed SWF format not supported
LAVF_header: av_open_input_stream() failed
libavformat file format detected.
[swf @ 0x876cbe8]Compressed SWF format not supported
LAVF_header: av_open_input_stream() failed
============ Sorry, this file format is not recognized/supported =============
=== If this file is an AVI, ASF or MPEG stream, please contact the author! ===
Cannot open demuxer.


```

So... apparently, swf is not supported by mencoder either. Know of any other methods? I been searching around and can't find any. I really didn't want to have to record the audio from the speakers, if I didn't have to, though.

Dr Small

---

### Post by FakeOutdoorsman on 2008-09-30
Works for me with ffmpeg, but I'm not using the crippled version from the repository.  If it doesn't work with Ubuntu's ffmpeg, then you can try the Medibuntu repository or compile it yourself with support for restricted formats.

Investigate the file:
```
[frink@hedron ~]$ ffmpeg -i apehouse.swf
Input #0, swf, from 'apehouse.swf':
  Duration: 00:05:06.39, bitrate: 15 kb/s
    Stream #0.0: Audio: mp3, 11025 Hz, mono, s16, 16 kb/s
```
Copy the audio stream.  No need to re-encode:
```
ffmpeg -i apehouse.swf -acodec copy apehouse.mp3
```

---

### Post by oponto on 2009-10-31
trying to convert homo format youtube file:
```
ffmpeg -i megaloop -acodec copy megaloop_converted.mp3
```

output:
```
built on Apr 10 2009 23:18:41, gcc: 4.3.3
[swf @ 0x8d0aac0]Compressed SWF format not supported
megaloop: I/O error occurred
Usually that means that input file is truncated and/or corrupted.

```

it is swf format, but seems to be compressed somehow in swf. any solution to get the audio ?

---

### Post by oponto on 2009-11-03
okay let's try a different way:

how to extract music from the following swf-compressed file:

[FONT="Arial Black"]**[SIZE="4"][http://www.youtube.com/watch?v=f_M6cKJku80](http://www.youtube.com/watch?v=f_M6cKJku80)[/SIZE]**[/FONT]

---

### Post by FakeOutdoorsman on 2009-11-03
Watch video in Firefox.  The video file will appear in the */tmp* directory and stay there until you navigate away from the YouTube web page.  Get audio details with FFmpeg:
```
ffmpeg -i /tmp/FlashCXYWR1
```
FFmpeg will show audio information:
```
Stream #0.1: Audio: aac, 22050 Hz, stereo, s16
```
Now that you know the audio details you can copy it:
```
ffmpeg -i /tmp/FlashCXYWR1 -acodec copy output.aac
```
Or if you want MP4 container:
```
ffmpeg -i /tmp/FlashCXYWR1 -acodec copy -vn output.mp4
```

---

### Post by oponto on 2009-11-13
Absolutely works.
good job
Thanks man !


My fail as I suppose: 
First, I should have looked up for code how to find out about the audio format in the flash file. Then I tried to put it into mp3 format what ffmpeg just can't directly from aac. Right ?;)

---

### Post by FakeOutdoorsman on 2009-11-13
> **oponto said:**
> Absolutely works.
good job
Thanks man !


My fail as I suppose: 
First, I should have looked up for code how to find out about the audio format in the flash file. Then I tried to put it into mp3 format what ffmpeg just can't directly from aac. Right ?;)

The first command from my example was used to find out the format of the input.  If you want to encode to mp3:
```
ffmpeg -i input -ab 128k -ac 2 output.mp3
```
The *-ab* option is the bitrate, and *-ac* is the number of channels (1 is mono, 2 is stereo).  Note that FFmpeg from the repository has been stripped of restricted encoders, including *libmp3lame* which FFmpeg uses to encode to mp3.  Enabling these encoders is easy though:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

---

### Post by Dafydd on 2013-01-23
> **FakeOutdoorsman said:**
> Works for me with ffmpeg, but I'm not using the crippled version from the repository.  If it doesn't work with Ubuntu's ffmpeg, then you can try the Medibuntu repository or compile it yourself with support for restricted formats.

Investigate the file:
```
[frink@hedron ~]$ ffmpeg -i apehouse.swf
Input #0, swf, from 'apehouse.swf':
  Duration: 00:05:06.39, bitrate: 15 kb/s
    Stream #0.0: Audio: mp3, 11025 Hz, mono, s16, 16 kb/s
```
Copy the audio stream.  No need to re-encode:
```
ffmpeg -i apehouse.swf -acodec copy apehouse.mp3
```

Hi, this worked for me too.

---

### Post by oldos2er on 2013-01-23
Old, old thread closed.

---

