---
title: "Wacom Volito does not work with Edgy and 2.6.18.1 kernel"
date: 2006-11-17
forum: Hardware &amp; Laptops
---

### Post by morganevans on 2006-11-17
I've got a Wacom Volito pad which works fine with Edgy's installed kernel (forget which version) and the necessary changes to xorg.conf

However, I've compiled my own kernel and although the wacom driver is available (dmesg | grep wacom) the thing won't move so I suspect the kernel doesn't really support it at all.

From what I've read there's been recent problems with Wacom drivers and Edgy but this just seems to be the next in line.  Have anyone got their wacom pad working with Edgy and the 2.6.18.1 kernel?  If so how?

Thanks for your help

---

### Post by euchrid on 2006-11-20
Hi - I managed it with the 2.6.18.2 kernel; any use to you? I notice the 2.6.18.3 is out now as well... Here is my story - hope it helps you:

I've just spend **four days** trying to get my Volito 1 working in Edgy, and I had to use [linuxwacom]("http://linuxwacom.sourceforge.net/") in the end. I tried all the advice at [https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom), and swallowed all the bits about it being 'straightforward'. It wasn't. None of the advice on that page or relating to it worked for me. The whole wacom-tools thing would not work; I downloaded wacom-tools, wacom-kernel-source and xsever-xorg-input-wacom over the course of my trials, trying them alone and in conjunction with linuxwacom - and the best I got was a bad mouse with no right click and no sense of the screen area.

I tried following the guide in linuxwacom without having the first clue what was going on. I've only started with Linux last week, and it was a huge learning curve. However, even as a complete novice, I got it to work - eventually.

I am not sure what step I took that was actually necessary, but I ended up downloading and compiling and installing the newest stable kernel (2.6.18.* at the moment), removing all wacom packages using Synaptic (all of those wacom-tools related ones mentioned above), and deleting everything I could find relating to linuxwacom from my previous three (or more) attempts to get it to work, then downloading it for at least the third time, and following the instructions, very carefully, step by step.

At some point, I will write out detailed instructions that actually make sense for those new to Linux, or for those who simply can't make head or tail of the ones at linuxwacom, but I would say: persevere. It *does* work, but you need a lot of time and patience, and I'm pretty sure you need to remove all the supposedly 'easy-to-use' wacom-tools stuff and related.

I found that I had files in places other than where they were suggested by linuxwacom, and it was not easy to work out which one of the many kernel-related directories I was supposed to put things under; in the end, I used ./configure --enable wacom --with-kernel=/usr/src/linux-2.6.18.2 although linuxwacom thought my kernel was in another, almost identically named directory (which seemed to be created by the kernel).

Even now, none of this makes any sense to me; but I have, at last, a working Volito 1, with the stylus button right-click enabled and a nice movement, and automatic screen recognition (i.e. it's no longer working like a cheap rubbish mouse).

I only ended up on the 2.6.18 kernel because there was some advice somewhere about compiling the latest kernel possibly helping one of the many error messages I got in linuxwacom. 

When I've had a rest and calmed down, I'll work out what the hell I did to make things work, write it out in full and post it up, with a link from this message thread. Hope this has helped in the meantime!

Incidentally, now I know what to do, I think I could get a Wacom tablet up and running on a system (as long as it's pretty similar to mine) in about half an hour or less. The instructions look far more complicated than they actually are!

When I've posted up my detailed and hopefully understandable instructions, if you're still stuck, send me a message. Good luck!

---

### Post by euchrid on 2006-11-21
Finally finished writing up how I got my Volito to work with Edgy and 2.6.18.2 kernel - see: [http://ubuntuforums.org/showthread.php?t=303555]("http://ubuntuforums.org/showthread.php?t=303555")

Hope it's of use to you - or someone!

---

### Post by morganevans on 2006-11-22
Thanks euchrid.  I didn't exactly follow your instructions to the dot but I did compile linuxwacom and installed the wacom.ko in the relevant folder and added a few of your Option sections to my xorg.conf and after a restart - it worked!

---

### Post by euchrid on 2006-11-22
Glad it was some help. Probably best not follow my instructions too closely, anyway. If you're halfway there to begin with, the xorg.conf stuff and the drivers are probably all you need (I mention this in case anyone else has similar issues or is daunted by the long How-tos).

---

