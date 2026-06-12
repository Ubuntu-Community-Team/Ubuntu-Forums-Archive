---
title: "[SOLVED] ffmpeg-php = DUMB"
date: 2008-08-06
forum: General Help
---

### Post by CrusaderAD on 2008-08-06
I followed the instructions listed here:

[http://ffmpeg-php.sourceforge.net/](http://ffmpeg-php.sourceforge.net/)

I get to ./configure && make and it gives me the error:

checking for ffmpeg headers... 
configure: error: ffmpeg headers not found. Make sure ffmpeg is compiled as shared libraries using the --enable-shared option

I tried a fix from this site:

[http://kb.bobcares.com/?View=entry&EntryID=252](http://kb.bobcares.com/?View=entry&EntryID=252)

But the files aren't located there. I searched and I still can't find them. I do have ffmpeg installed to it's newest version. What is wrong??

---

### Post by nbayiha on 2008-08-06
> Make sure ffmpeg is compiled as shared libraries using the --enable-shared option
Did you read that .
So try to compile using that option . Maybe it will work .

---

### Post by CrusaderAD on 2008-08-06
What would be the code for that?

---

### Post by nbayiha on 2008-08-06
When you compile  you just have to use this command ```
./configure --enable-shared

```
```
sudo make 
```
If it doesn't work use this one instead.
```
./configure --enable-libmp3lame --enable-libogg --enable-libvorbis --disable-mmx --enable-shared --enable-amr-nb --enable-libtheora

```

---

### Post by CrusaderAD on 2008-08-06
Tried that... I get this again:

checking for ffmpeg headers... 
configure: error: ffmpeg headers not found. Make sure ffmpeg is compiled as shared libraries using the --enable-shared option

---

### Post by nbayiha on 2008-08-06
I think i found a better how to for u to install ffmpeg-php.

Follow those command from the start and let see if it's gonna work .

[http://linux.justinhartman.com/FFmpeg,_FFmpeg-PHP,_Lame,_Libogg,_Libvorbis,_FLVtool2,_Mplayer,_Mencoder,_AMR_Installation](http://linux.justinhartman.com/FFmpeg,_FFmpeg-PHP,_Lame,_Libogg,_Libvorbis,_FLVtool2,_Mplayer,_Mencoder,_AMR_Installation)

---

### Post by CrusaderAD on 2008-08-06
I walked through this sob, now it says:

checking for ffmpeg libavcodec.so... configure: error: ffmpeg share libraries not found. Make sure you've built ffmpeg as shared libs using the --enable-shared option

This is ridiculous.

---

### Post by CrusaderAD on 2008-08-06
Thanks for your replies, I found that last website to be helpful. I've been trying this throughout the day. Still not working... from what I can gather, it's looking for these files when they either don't exist or they aren't located where it's looking.

---

### Post by nbayiha on 2008-08-06
Did you try to google your error. Maybe you will get more Help ?

---

### Post by CrusaderAD on 2008-08-06
Yeah... it seems like this is a BIG problem, but I haven't found a solution.

---

### Post by CrusaderAD on 2008-08-06
Here's something... it says the libavcodec.so is not found... when I look for it, I find this instead:

/usr/lib/libavcodec.so.1d

why is it different?

---

### Post by CrusaderAD on 2008-08-06
When I was running:

make
make install
ln -s /usr/local/lib/libavdevice.so.52 /usr/lib/libavdevice.so.52
ln -s /usr/local/lib/libavformat.so.52 /usr/lib/libavformat.so.52
ln -s /usr/local/lib/libavcodec.so.51 /usr/lib/libavcodec.so.51
ln -s /usr/local/lib/libavutil.so.49 /usr/lib/libavutil.so.49
ln -s /usr/local/lib/libmp3lame.so.0 /usr/lib/libmp3lame.so.0
ln -s /usr/local/lib/libavformat.so.51 /usr/lib/libavformat.so.51
ln -s /usr/local/lib/libamrnb.so.2 /usr/lib/libamrnb.so.2

"make" or "make install" gives me this output:

Makefile:1: config.mak: No such file or directory
libavdevice/Makefile:1: libavdevice/../config.mak: No such file or directory
libavformat/Makefile:1: libavformat/../config.mak: No such file or directory
libavcodec/Makefile:1: libavcodec/../config.mak: No such file or directory
libavutil/Makefile:1: libavutil/../config.mak: No such file or directory
make: *** No rule to make target `libavutil/../config.mak'.  Stop.

---

### Post by CrusaderAD on 2008-08-06
Do you think it was as easy as this?

[http://packages.ubuntu.com/hardy/source/ffmpeg-php](http://packages.ubuntu.com/hardy/source/ffmpeg-php)

---

### Post by CrusaderAD on 2008-08-07
It looks like just installing these two:

sudo apt-get install php-ffmpeg

sudo apt-get install ffmpeg

did the trick.

---

