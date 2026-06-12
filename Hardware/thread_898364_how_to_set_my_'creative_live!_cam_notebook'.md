---
title: "how to set my 'creative live! cam notebook'"
date: 2008-08-23
forum: Hardware
---

### Post by _zax_ on 2008-08-23
how to set my 'creative live! cam notebook' on ubuntu?

---

### Post by lubes on 2008-10-06
> **_zax_ said:**
> how to set my 'creative live! cam notebook' on ubuntu?

hi,
I have the same webcam and this problem I solved by this "manual": [http://www.andreagrandi.it/2008/06/05/creative-live-cam-notebook-su-ubuntu-linux/](http://www.andreagrandi.it/2008/06/05/creative-live-cam-notebook-su-ubuntu-linux/)

new driver: [http://www.rastageeks.org/downloads/ov51x-jpeg/](http://www.rastageeks.org/downloads/ov51x-jpeg/)

now, my webcam work. I see it in 'xawtv' ('sudo apt-get install xawtv'), but in skype I cannot establish a call. error: 'Problem with Audio Playback'

any idea, please?

---

### Post by lubes on 2008-10-06
> **lubes said:**
> 
I cannot establish a call in skype. error: 'Problem with Audio Playback'
any idea, please?

so, this problem I solved by work-flow on this site:
[http://ubuntuforums.org/showthread.php?t=432295](http://ubuntuforums.org/showthread.php?t=432295)
and important is a version of skype in ubuntu amd64 hardy...

> **web said:**
> For users with sound problems due to PulseAudio, Medibuntu also offers the package "skype-static-oss". Once installed, skype can be run through pulse audio with "padsp skype".

now I have problem, with video on skype. I see and hear the other side, but the other side just hear me. in options->video devices I have my webcam and in other applications work OK (for example 'xawtv').

have someone solution of this problem?

---

### Post by duffrecords on 2008-12-19
Try the latest svn code of ov51x-jpeg from [http://www.rastageeks.org/ov51x-jpeg/index.php/Main_Page]("http://www.rastageeks.org/ov51x-jpeg/index.php/Main_Page").  Version 1.5.9 has an error on line 8377 but it is fixed in the development version.

---

### Post by pr2006pimp on 2009-02-09
I am new to ubuntu and I tried the italian site but had an error and a fatal one in thins part: 

root@noteboontu:~/ov51x-jpeg-1.5.7# modprobe ov51x-jpeg

and this is the error

&#8220;FATAL: Error inserting ov51x_jpeg (/lib/modules/2.6.24-19-generic/extra/ov51x-jpeg.ko): Unknown symbol in module, or unknown parameter (see dmesg)&#8221;

is there anything I can do to finally install my webcam?? Ive tried everything!!!

---

### Post by dixon on 2009-03-08
I want to buy the creative live! cam notebook. Did you manage to get it work in ubuntu? Also does the built in microphone work?

---

