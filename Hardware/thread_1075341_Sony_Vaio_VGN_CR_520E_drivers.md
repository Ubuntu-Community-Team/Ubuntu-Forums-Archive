---
title: "Sony Vaio VGN CR 520E drivers"
date: 2009-02-20
forum: Hardware
---

### Post by jaishankar on 2009-02-20
Hi All,

 I am quite new to Linux/Ubuntu. A couple of days ago I used WUBI to install Ubuntu 8.10 on my Vaio laptop running on Vista Home Premium (32 Bit OS). I must say this was the easiest OS installation I have ever done. Exactly as mentioned in the WUBI welcome screen, it was a one click-complete OS installation. Wow :-) I am amazed.

 Day 1, was struggling a bit with the administrator settings. But finally got it after some research in here. Configured a Static IP for my wireless internet connection. I am beginning to like the user interface of Ubuntu and the graphics.

Day 2, wanted to use skype. Went to Skype site downloaded the .deb file. Does not work 'Incorrect Architecture' error. After some research I got to know I have a 64 bit Ubuntu installation.

 'uname -a' command result on terminal

Linux ubuntu 2.6.27-11-generic #1 SMP Thu Jan 29 19:28:32 UTC 2009 x86_64 GNU/Linux 

After some more research, I found I can install skype through medibuntu repository. I successfully installed skype. Only now I fgured out, both my microphone and webcam (laptop inbuilt) were not recognised.

How/ where can I get the drivers for my microphone and webcam for my Sony Vaio VGN CR 520 E/R laptop?
Sony provides drivers only for Vista. The different hardware and their drivers for Vista OS can be found here.
[http://esupport.sony.com/US/perl/swu-list.pl?mdl=VGNCR520E](http://esupport.sony.com/US/perl/swu-list.pl?mdl=VGNCR520E)

P.S: This is my first post in Ubutnu forums...

Thanks
Jai

---

### Post by jaishankar on 2009-02-20
Update: Got the microphone working. Solution was to change the input source from mic to front mic in Volume control.

Still unable to figure out what is wrong with webcam.

Found this thread. [http://test.ubuntuforums.org/showthread.php?t=821343](http://test.ubuntuforums.org/showthread.php?t=821343)
I followed the steps exactly. My Ubuntu version is 8.10 with kernel 2.6.27-11-generic
This was the result of lsusb : Bus 003 Device 003: ID 05ca:1839 Ricoh Co., Ltd

Still I could not get this working.

xawtv /dev/video0 results the following

This is xawtv-3.95.dfsg.1, running on Linux/x86_64 (2.6.27-11-generic)
xinerama 0: 1280x800+0+0
can't open /dev/video0: No such file or directory
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video0: No such file or directory
v4l2: open /dev/video0: No such file or directory
v4l: open /dev/video0: No such file or directory
no video grabber device available

Any help is highly appreciated.
T

---

### Post by jaishankar on 2009-02-20
Any pointers...

It is really frustrating after 3 days of research and still no working results.

Thanks

---

### Post by cariboo on 2009-02-20
You shouldn't answer your own posts, as it looks like someone is helping you already. It is forum policy to only bump your thread every 24 hours.

That being said have you had a look at this [Howto]("http://www.arakhne.org/ricoh/bugs_and_solutions.html")?

Jim

---

### Post by Squid Spectre on 2009-02-20
Looks like what you're using could be looking at the wrong device file or simply not configured to even handle device files. My webcam works with an application called "Cheese" which takes video and picture, similar to the one posted. However, that app looks like it's meant to watch televion and you're pointing to the dev file to get it to play, though a seemingly viable way to read right from the device it seems like it might be a bit dated.

Try Cheese from the application installer, I think you'll be happier with the result or at least have a more accurate idea as to what the problem is.

---

### Post by jaishankar on 2009-02-20
> **cariboo907 said:**
> You shouldn't answer your own posts, as it looks like someone is helping you already. It is forum policy to only bump your thread every 24 hours.

That being said have you had a look at this [Howto]("http://www.arakhne.org/ricoh/bugs_and_solutions.html")?

Jim

Thanks a ton Jim:p That did the trick. 

So the complete solution will be to follow the instructions in the above mentioned thread and then load the uvc video kernel module by using the link you have mentioned.

Thanks again.
Jai

P.S: I dint know it was against forum rules to bump thread less than 24 hours. Sorry about that.

---

### Post by onlyraider on 2010-02-25
The how to no longer seems to be online? I've got a similar problem with my Vaio cr 120E webcam!

---

