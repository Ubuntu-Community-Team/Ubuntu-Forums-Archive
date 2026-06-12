---
title: "[SOLVED] FFMPEG - Installed?"
date: 2008-08-13
forum: General Help
---

### Post by CrusaderAD on 2008-08-13
I installed the packages ffmpeg and php-ffmpeg. I also added the extensions to my php.ini file. From what I've been told, it still isn't working. How can I test it? What could be wrong?

---

### Post by CrusaderAD on 2008-08-13
I was looking through the apache logs. I see this error in there a few times:

Unsupported codec for output stream #0.1 

Could that have anything to do with it?

---

### Post by WRDN on 2008-08-13
In the terminal, type "ffmpeg". If it is installed, the appropriate output will appear. You can also check in Synaptic to see if its installed.

---

### Post by CrusaderAD on 2008-08-14
It's installed and working. The only problem now is that the codecs don't seem to be loaded or working. Here an error I'm receiving:

Unsupported codec for output stream #0.1

---

### Post by decoherence on 2008-08-14
The version of ffmpeg that comes with ubuntu is crippled from a codec standpoint.

see here

[https://wiki.ubuntu.com/ffmpeg](https://wiki.ubuntu.com/ffmpeg)

---

### Post by sayakb on 2008-08-14
At a terminal, do:
```
sudo apt-get install ubuntu-restricted-extras
```Or follow [this]("http://ubuntuforums.org/showthread.php?t=856190") tutorial to install W32codecs (from the Medibuntu repo)

---

### Post by Mgiacchetti on 2008-08-14
you have to install ffmpeg from the medibuntu repo's

---

### Post by CrusaderAD on 2008-08-14
How do you install from the medibuntu repo's?

---

### Post by Mgiacchetti on 2008-08-14
hardy??

sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

others
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by sayakb on 2008-08-14
> **raptormanad said:**
> How do you install from the medibuntu repo's?

Did you read my previous post? Anyway, after doing what Mgiacchetti said, do:
```
sudo apt-get install w32codecs
```

---

### Post by CrusaderAD on 2008-08-14
I installed the ubuntu restricted packages and the w32codecs. Also the medibuntu keyring. As for the ffmpeg package, I show a large list at 

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

How do I know which one to use? What's the code to install the one I choose? Thank for all your help!

---

### Post by sayakb on 2008-08-14
The restricted packages and w32codecs both installed some ffmpeg codecs. Did you try playing the media files again?

You may also try VLC media player:
```
sudo apt-get install vlc
```
If you are playing real media, try Real Player for linux: [http://www.real.com/linux](http://www.real.com/linux)

---

### Post by CrusaderAD on 2008-08-14
It looks as if ffmpeg installed from the medibuntu repositories. If I run a ffmpeg -version I get:

FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 29 2008 18:21:25, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
ffmpeg      SVN-rUNKNOWN
libavutil   3212032
libavcodec  3352064
libavformat 3344896

The same thing I got before. Some Unknown version.

---

### Post by CrusaderAD on 2008-08-14
We're acutally using ubuntu server and we're uploading/streaming videos for a website.

---

### Post by CrusaderAD on 2008-08-14
Here's an update. I ran a mpg file the browser just fine, but when I attempt to run an flv file from the browser, it doesn't work. When I play them in VLC, the screen is black.

---

### Post by CrusaderAD on 2008-08-14
bump

---

### Post by sayakb on 2008-08-14
Open VLC and goto Settings->Preferences, **check** the Advanced options checkbox (bottom right)
Now expand Video and click on Output Modules. Change the *Video output module* from default to X11 Video output.

---

### Post by FakeOutdoorsman on 2008-08-14
I believe php5-ffmpeg/ffmpeg-php from the ubuntu repository isn't using ffmpeg directly, but using libavcodec and libavformat which are libraries of ffmpeg.  The php5-ffmpeg package will install libavcodec and libavformat from the Ubuntu repository which do not support restriced formats.  That is why you are getting the "unsupported codec for output stream #0.1" error.  Probably.  Your output format must be a restriced one or your ffmpeg code you are running may for a different version of ffmpeg.  Since the option names often change between ffmpeg revisions you can get this error if you use an outdated codec name.

You can try to uninstall php5-ffmpeg, install libavcodec and libavformat from Medibuntu (these versions allow most restricted codecs and formats), and then reinstall php5-ffmpeg.  Hopefully it will use Medibuntu's libav* instead of requesting Ubuntu's.  If not, then you will have to compile ffmpeg-php yourself.

What is the ffmpeg code you are using to convert the video?  It might be as simple as you using the wrong option names for your version of the ffmpeg libraries.

---

### Post by CrusaderAD on 2008-08-14
Thanks LinuxIsInnovation, that worked and it's now playing those files. I will post later and mark this as solved if the files work out in the browser. Any idea why an FLV file won't play in the browser? When I navigate to the file (in the browser) it asks me to download the file, rather than playing it like a mpeg file.

---

### Post by sayakb on 2008-08-14
For that, install :
```
sudo apt-get install flashplugin-nonfree
```
If it already is installed, try installing the gnash swf viewer.

---

### Post by CrusaderAD on 2008-08-14
The flashplugin-nonfree is installed. This is a server and I'm actually accessing the site from another pc on the network. Everything comes up but the FLV.

---

### Post by sayakb on 2008-08-14
If you ask me, I hate gnash, but see if installing gnash works..

---

### Post by CrusaderAD on 2008-08-20
Install the ffmpeg and php-ffmpeg packages from synaptic. Then edit the php.ini file and add the following lines:

extension=ffmpeg.so

Then restart apache. This worked for me.

---

