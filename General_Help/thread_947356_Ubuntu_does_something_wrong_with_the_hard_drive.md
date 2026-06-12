---
title: "Ubuntu does something wrong with the hard drive"
date: 2008-10-14
forum: General Help
---

### Post by Serguei_89 on 2008-10-14
Hi

My CPU I/O wait graph in the system monitor applet regularly spikes to 100%, regardless of what I'm doing. Any small activity causes it to go nuts. and sometimes even just doing nothing, it spikes. It's not a particular process (top command shows nothing), but the CPU I/O wait.

On top of that, I regularly crash on bootup, because it found filesystem errors in root filesystem! Bios reports hard-drive problems as well. (I have to do fsck -t ext3 -t /dev/hda to fix the errors and boot again.)

I thought it was a hard-drive problem and I need to replace it, but badblocks utility reported 0 bad blocks and all problems vanished when I installed Debian. 

I went back to Ubuntu because Debian was a bit difficult (getting the video/sound playback to work I failed). And the hard-drive problems are back again.

I added the 
hdparm -B /dev/hda 
line to acpi suspend, resume and start scripts like it recommends here:
[http://www.linux-hero.com/rant/explanation-ubuntu-hard-drive-wear-and-tear](http://www.linux-hero.com/rant/explanation-ubuntu-hard-drive-wear-and-tear)

but the problems continue.

Also, I experienced similar problems when I briefly ran Linux Mint.

Serguei

---

### Post by Sef on 2008-10-14
1) What version of Ubuntu are you using?

2) What are your system specs?

3) It could be that Debian and its progeny do not work well on your hardware.

---

### Post by Serguei_89 on 2008-10-14
Hi 

I'm using Ubuntu 8.04.1 with all the updates as of today.

System specs are attached

Debian etch worked fine, no problems what so ever. But Ubuntu and Mint cause errors

---

