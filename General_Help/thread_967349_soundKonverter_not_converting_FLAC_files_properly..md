---
title: "soundKonverter not converting FLAC files properly."
date: 2008-11-01
forum: General Help
---

### Post by Gamzarme on 2008-11-01
Hello. I am wondering what might be the problem with my music converting process. I am using soundKonverter under Ubuntu to convert a multitude of file formats to a standard of 192 kbps MP3. For whatever reason FLAC refuses to be understood. I have extracted a log file that should help someone who knows how to read it help me.

Please take a quick look and let me know where in the process everything is breaking down.

This looks like part of the problem:
"Output: Could not find codec parameters (Audio: mp1, 448 kb/s)"

By the way, I am using ffmpeg to decode FLAC files, which is the only option available.

I had to install lame manually to get the correct encoding process for MP3 files.

Thanks for your help!! =)


SORRY, UbuntuForums.org uploading is not working right now..the entire website seems very unstable and slow...here is the log file.
```

Mime Type: audio/x-flac
Tags successfully read
Executing next step
Getting file
cp "/home/thomasp/Music/Processing/Converting/LED ZEPPELIN-Complete Studio Recordings(10CD)[EAC-FLAC](oan)/Led Zeppelin - 1/(01)-Good Times Bad Times-Led Zeppelin-1969.flac" "/tmp/kde-thomasp/soundkonverterUioY2a.flac"
 Got file
Executing next step
Decoding
/usr/bin/ffmpeg  -y -i "/tmp/kde-thomasp/soundkonverterUioY2a.flac" "/tmp/kde-thomasp/soundkonverterlePXqc.wav"
 Output: FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 29 2008 18:28:49, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)

 Output: [mp3 @ 0x7f37c1d63160]
 Output: Could not find codec parameters (Audio: mp1, 448 kb/s)

 Output: /tmp/kde-thomasp/soundkonverterUioY2a.flac: could not find codec parameters

Executing next step
Encoding
/usr/bin/lame  -q 2 --cbr -b 192 --resample 44.1 -m s --noreplaygain --ignore-tag-errors --add-id3v2 --pad-id3v2 --ta "Led Zeppelin" --tl "1" --tc "Track 1" --tg "Rock" --tn 1 --tt "Good Times Bad Times" --ty 1969 "/tmp/kde-thomasp/soundkonverterlePXqc.wav" "/tmp/kde-thomasp/soundkonverterUTbZra.mp3"
 Output: Assuming raw pcm input file

 Output: LAME: Can't get "TERM" environment string.
LAME 3.97 64bits (http://www.mp3dev.org/)

 Output: Using polyphase lowpass filter, transition band: 18671 Hz - 19205 Hz
Encoding /tmp/kde-thomasp/soundkonverterlePXqc.wav
      to /tmp/kde-thomasp/soundkonverterUTbZra.mp3
Encoding as 44.1 kHz 192 kbps stereo MPEG-1 Layer III (7.3x) qval=2

 Output: 
    Frame          |  CPU time/estim | REAL time/estim | play/CPU |    ETA 
     0/       ( 0%)|    0:00/     :  |    0:00/     :  |         x|     :  

     2/2     (100%)|    0:00/    0:00|    0:00/    0:00|   0.0000x|    0:00 

 Output: Writing LAME Tag...done

Executing next step
Writing tags
Executing next step
Moving file
cp "/tmp/kde-thomasp/soundkonverterUTbZra.mp3" "/home/thomasp/Music/Processing/Converted/Holding/Converting/LED ZEPPELIN-Complete Studio Recordings(10CD)[EAC-FLAC](oan)/Led Zeppelin - 1/(01)-Good Times Bad Times-Led Zeppelin-1969.new.mp3"
 File moved
Executing next step
Removing file from conversion list. Exit code 0
Finished logging

```

---

### Post by Pro-reason on 2008-11-02
That's a KDE app.  Perhaps you could try the GNOME version to see if it works better for you.

Install “soundconverter” instead of “soundkonverter”.

It's in the repositories (v1.0.1 for Hardy, and v1.3.2 for Intrepid).  You can also add [this extra repository](https://launchpad.net/~chameleondave/+archive) if you want version 1.4.1.

---

### Post by Gamzarme on 2008-11-02
The problem with soundconverter is that it wants to read each ID3 tag before converting. If there was any was to turn this feature off, I would be back to using soundconverter.

Before I was using dBpowerAMP under WINE, which was fine until WINE began not displaying certain dBpowerAMP status windows.

Is there anything to be gained from reading the log file I have posted?

Thank you for continuing to help with this small problem.

---

### Post by Gamzarme on 2008-11-02
Well...I do not know exactly what fixed it. I closed/opened the program a multiple of times, and now it works. =)

I installed the flac and faac packages, which are used now to decode flac and aac (I guess) instead of ffmpeg, which wasn't decoding properly.

---

