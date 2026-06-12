---
title: "Broadcom Crystal HD on 10.10"
date: 2010-10-27
forum: Hardware
---

### Post by ntimperio on 2010-10-27
I just got an ASUS 1005PR and THINK that linux (ubuntu 10.10 32bit) recognizes the Broadcom Crystal HD card.  However, when I try to watch 1080p video in linux it is choppy (about 1 frame every 2 seconds).  Same video in windows is smooth.  I'm using the movie player that comes with ubuntu.  How can I verify that Linux is working with the Broadcom hardware?  Is there anything I should be doing with the movie player to use this card?

thanks,
Nicholas

---

### Post by joshruehlig on 2010-10-28
The only video player that uses broadcom crystal decoding in linux is xine (in xbmc). (At least last time I configured my card).

XBMC isnt packaged for ubuntu 10.10 yet, and regular XBMC doesn't have crystal HD support.
So either way if you are using ubuntu 10.10 you need to buil xbmc. Heres instructions for Ubuntu 10.04. [http://ubuntuforums.org/showthread.php?t=1504329](http://ubuntuforums.org/showthread.php?t=1504329) (post 5)

Once Configured XBMC should play most videos just fine on any old netbook unless it's not h264 encoded or is very very high bitrates.
------------------
It may take a good amount of frustration to get this configured in ubuntu 10.10 as of now (but possible). But...
I read when Dharma build of XBMC comes out they'll package it for ubuntu 10.10 and it will most likely have crystal HD support built in. So when that happens it will just be copying and pasting two lines of code, as well as download/installing the driver. Much easier and faster to get working....

---

### Post by ntimperio on 2010-10-28
Thanks Josh.  I'll give 10.04 and XBMC a shot.

---

### Post by joshruehlig on 2010-10-28
Also i think you computer can do 64 bit so for a little more performance boost check that out.

Tell m if you need help ill see what I can do

---

### Post by johntaylor1887 on 2010-11-05
Hi. I am having a hard time getting the Crystal HD card to work. I installed the drivers and firmware, but 720 and 1080 vids are still very 
choppy. Doing lsmod shows crystalhd. 

Btw, I did a minimal install of 10.10 and have Acer Aspire One netbook.

Will using xine help?

---

### Post by joshruehlig on 2010-11-05
> **johntaylor1887 said:**
> Hi. I am having a hard time getting the Crystal HD card to work. I installed the drivers and firmware, but 720 and 1080 vids are still very 
choppy. Doing lsmod shows crystalhd. 

Btw, I did a minimal install of 10.10 and have Acer Aspire One netbook.

Will using xine help?

did u follow instructions to build xbmc with crystalhd support?
also videos need to be h264 encoded to use the card

---

### Post by johntaylor1887 on 2010-11-06
> **joshruehlig said:**
> did u follow instructions to build xbmc with crystalhd support?
also videos need to be h264 encoded to use the card

No, I did not. It seems like I may have wasted my money on this card, as I got it for HD flash video which is not yet supported with flash in linux. Btw, I installed Win7 on it just for the heck of it, and windows would not even see the card. 

Oh well, time to reinstall ubuntu and try to sell the card. Thanks anyway.

---

### Post by joshruehlig on 2010-11-06
> **johntaylor1887 said:**
> No, I did not. It seems like I may have wasted my money on this card, as I got it for HD flash video which is not yet supported with flash in linux. Btw, I installed Win7 on it just for the heck of it, and windows would not even see the card. 

Oh well, time to reinstall ubuntu and try to sell the card. Thanks anyway.

Well in windows u need to install the driver, then download flash 10.1 or 10.2
But I have noticed little difference when running flash in windows. In a media player you can get almost any h264 movie to flaw flawlessly on the weakest of processors.

---

### Post by johntaylor1887 on 2010-11-06
> **joshruehlig said:**
> Well in windows u need to install the driver

I did try to install the driver in windows, but it kept telling me there was no card installed. Ubuntu could see it though. Weird. Anyway, the card is now removed, and ubuntu is back on. I guess I'll have to live without HD on it.

---

### Post by joshruehlig on 2010-11-06
> **johntaylor1887 said:**
> I did try to install the driver in windows, but it kept telling me there was no card installed. Ubuntu could see it though. Weird. Anyway, the card is now removed, and ubuntu is back on. I guess I'll have to live without HD on it.

For flash I agree but I am getting 1080p h264 file running on my netbook now even without my broadcom card. [https://launchpad.net/~ripps818/+archive/coreavc](https://launchpad.net/~ripps818/+archive/coreavc)

---

### Post by johntaylor1887 on 2011-02-18
> **joshruehlig said:**
> For flash I agree but I am getting 1080p h264 file running on my netbook now even without my broadcom card. [https://launchpad.net/~ripps818/+archive/coreavc](https://launchpad.net/~ripps818/+archive/coreavc)

And what am I suppose to install after adding the ppa?

---

### Post by joshruehlig on 2011-02-18
> **johntaylor1887 said:**
> And what am I suppose to install after adding the ppa?

[http://forum.eeeuser.com/viewtopic.php?id=89922](http://forum.eeeuser.com/viewtopic.php?id=89922)

check this thread

---

