---
title: "HP dv9000- any hope?"
date: 2006-12-28
forum: Hardware &amp; Laptops
---

### Post by koolguynet on 2006-12-28
Good morning!

This week I purchased a HP Pavilion dv9000.  I got a great deal on it and it has killer specs:

AMD Turion 64 X2
2GB RAM
17" Screen
256 MB Nvidia card
2x 100GB HDD's

Seriously, it is really sweet hardware.  Anyway, my intention was to keep Win XP Media Center on one of the HDD's for the rare times I want to watch/record TV on my notebook and  put Kubuntu 6.10 on the other HDD.  Now before I begin, I have searched the forum and notice that a lot of people are having problems getting this notebook to work on Ubuntu, but none have exactly matched my problem.

I downloaded the 64bt version on DVD (thank God for Bitorrent!) and placed it in the drive to boot to live cd.  The initial window came up, I selected Start and it began to boot from the DVD but kept freezing shortly thereafter.  So, I decided to go forward with a text based install.  The install worked, it booted up after installing and there was my Kubuntu.  Next step, I installed Firefox (it was interesting that the text install never asked me for the packages I wanted to install).  After Firefox, it was on the Automatix2 which I installed and then installed the normal Win Codecs, Nvidia driver, Gimp, etc.  After that install I rebooted and now I can't even get to the CLI.  I see the Kubuntu Splash screen and the bar starts to fill in and then freezes once it gets about 1/10th of the way there.  I am at a loss.  I really want to use Kubuntu on this notebook, any ideas?:-k

---

### Post by Iluvatar on 2006-12-29
Hi,

I have exactly the same notebook and after some troubles with the wlan and usb flash drives I got almost everything (except Webcam) working now. I am currently not using the 64 bit version, but maybe It's the same error. After I added  "apm=off noapic" when booting the kernel, it all worked fine.

HTH

Christian

---

### Post by anaconda on 2006-12-29
Hmm.. did automatix install 32-bit versions of the codecs etc? All of them aren't compatible with 64-bit ubuntu...

Or is there a version of automatix specially made for 64-bit ?? Dont know..

Which is why I moved to 32-bit version with my dv2000..

---

### Post by koolguynet on 2006-12-29
How do I add the 'apm=off noapic' ?  Also, automatix2 detected that it was 64 bit and installed 64bit software where available.

Thanks!

---

### Post by Iluvatar on 2006-12-30
Either add it in grub's menu.lst or just test it by editing the line directly in grub when booting.

HTH

---

### Post by louix on 2007-04-05
I dos'nt work for me. Please help to get my integrated HP Pavillon webcam to work.

---

### Post by tflanders on 2007-04-14
I also want to get my webcam working. I've followed some of the guides in the forums for webcams with linux drivers and didn't have any luck. I' running fiesty beta and soon the full release.

---

### Post by TheOneMrO on 2007-04-26
I recently installed Fiesty and everything works, headphone jacks and everything EXCEPT for the webcam. I also would like to try and get it working.

---

### Post by jak140 on 2007-04-26
To get your webcam working, download and install this driver:

[http://lsb.blogdns.net/ry5u870/](http://lsb.blogdns.net/ry5u870/)

Then install xawtv (sudo aptitude install xawtv) and use this line to launch it from terminal or edit the menu launcher to use this line: 
xawtv -nodga -device /dev/video0

If you don't use this line the program will not open if you are using nvidia drivers. To get the webcam to work with Ekiga set it up so that the webcam uses V4L2 and not V4L. You should have the option when setting up the program.



And while I have your attention, do Hibernate or Suspend work for any of you? If so, do you have an Intel or AMD processer? I have an Intel processer and only suspend works. The computer will not turn off completely if I try to put it into hibernate and I have to do a hard reset.

---

### Post by velotron on 2007-04-28
I battled getting my webcam working until I realized that this thread is about the DV9000z, I've got the DV9000t with intel  cpu.   If anyone's looking to get that going..  I just installed  linux-uvc-source (debian testing), 
ran make install from /usr/src/modules/linux-uvc, and then tested with kdetv.  yay!

---

