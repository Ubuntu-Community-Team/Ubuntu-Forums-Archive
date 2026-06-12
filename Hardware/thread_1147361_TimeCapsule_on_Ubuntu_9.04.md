---
title: "TimeCapsule on Ubuntu 9.04"
date: 2009-05-03
forum: Hardware
---

### Post by Nick_R on 2009-05-03
hi all,

I have just (2 hours) switched from 15 years of Windows to Ubuntu... so far I am very impressed!

What I can't find is a step by step (for a newbi like me!) to gaining access to an Apple Timecapsule.  Does anyone know of one that exists?  

Thanks heaps,
Nick

---

### Post by Sealbhach on 2009-05-03
Well, it looks like it can be done, see the post in this thread by ytene:

[http://www.uluga.ubuntuforums.org/showthread.php?t=670535](http://www.uluga.ubuntuforums.org/showthread.php?t=670535)

Perhaps you could PM him and he could help you if you run into difficulty.

.

---

### Post by ytene on 2009-06-22
Hi Nick,

I have some good news and some bad news. 

Firstly, the good news. I have refined my configuration for my Time Capsule and managed to get it to work quite well under most circumstances.

Now the bad news. The latest version of ubuntu - 9.04 Jaunty Jackalope - has known issues with connecting to TC's. You can read more about it in the thread, here

[http://http://ubuntuforums.org/showthread.php?t=1178484]("http://http://ubuntuforums.org/showthread.php?t=1178484")

A brief summary: it turns out that improvements to the CIFS filing system with the latest release of ubuntu have highlighted a series of bugs in the Time Capsule version of the code. As a result there are problems connecting 9.04 to a Time Capsule. Some people are not able to connect; others, like me, are getting reasonable read-only connections but experiencing alarming data corruption when writing data back to the capsule from certain applications.

For example, I can save an image from FireFox directly to the Capsule, but if I open an OpenOffice Writer odt document, edit it and then save it, not only will it b0rk at the save command, but it will corrupt the file on the Capsule all at the same time. [ And as this wasn't immediately obvious, I had a happy time restoring from tape...]

So my best advice to you, if you want a reliable, stable and error free connection to a Time Capsule would be to stick with ubuntu 8.10 or 8.04 for now. Personally I couldn't get on with 8.10 and am happily using 8.04LTS, to which I have added upgraded packages such as OOo 3.0 and FireFox 3.0.11 and so on.

Hope this helps.

On a related topic... ubuntu 9.04 ships with the latest release of Amarok [ 2.0? ] and I have had problems with this as well. My 8.04 build, with Amarok, can play Apple Lossless Audio files [ I have transcoded my entire CD collection to Apple Lossless, via a Mac Mini, and stored the library on the Time Capsule ] absolutely perfectly. The out-of-the-box Amarok 2.0 that ships with ubuntu 9.04 will not play Apple Lossless. I've done a lot of messing around, pulled in codecs from medibuntu [ worth a look for things like codecs, Google Earth, Skype and the like, if you haven't found it ].

---

