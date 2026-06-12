---
title: "AMD M690T Chipset / HP 6715b"
date: 2007-06-30
forum: Hardware &amp; Laptops
---

### Post by drplix on 2007-06-30
I'm considering buying an HP 6715b laptop.  This has the Turion x2 processor and the fairly new AMD M690T chipset.  I haven't been able to find any reports about Linux support for this chipset.  Does anybody have experience with either this specific laptop or the AMD chipset?

Thanks for any info.

Peter

---

### Post by abrarey on 2007-07-05
I have the same laptop, ubuntu is working great but when i tried to installed I got some issues, video card wasn´t detected so I have to do some tricks I postit here. So if you decide to buy that notebook you can check here.

[http://ubuntuforums.org/showthread.php?t=488332&highlight=hp+6715b](http://ubuntuforums.org/showthread.php?t=488332&highlight=hp+6715b)

---

### Post by J-Red on 2007-07-05
I have the intel equivalent to that, (6710b) and so far I have everything working except for the optical drive. I had to do a bunch of stuff though first, my brother has all the steps taken on his blog (blaise.ca I think if you want to check it out) It will be different though since its the 6710b not the 6715b and uses an intel chipset. I'd say if you're willing to take a small risk, go for it!

---

### Post by drplix on 2007-07-08
Thanks for the response!  That's great news.  I was holding off buying until I heard any news.  I've been a Linux laptop user for more than 5 years.  Could never go back to win32.

---

### Post by jukoz on 2007-07-12
I have this laptop, with turion x2.
My problem is, that the second core is not recognized. Could this be because the chipset is not completely supported by the kernel?

PS Thanks for the tip on installing the graphic driver!

Ajt!

---

### Post by srd on 2007-07-12
look here
[http://ubuntuforums.org/showthread.php?t=499060](http://ubuntuforums.org/showthread.php?t=499060)

---

### Post by drplix on 2007-07-12
So I bought the 6715b. I installed Feisty 64 using the standard install.  The instructions for getting the graphics card detected work very well.  Only one thing I had to do...
> 
sudo apt-get update

before installing the graphics drivers.

Most things worked ok on first boot.  The biggest issues in order are:

1)  Broadcom WiFi Network bcm43xx  fails to load microcode.

I followed the instructions here:

[http://ubuntuforums.org/showthread.php?t=297092&highlight=dell+1390+ndiswrapper](http://ubuntuforums.org/showthread.php?t=297092&highlight=dell+1390+ndiswrapper)

but instead of the drivers referred to there go to HP support site and download the Win XP 32 bit driver SP34152A

2) SoundMax AD 1981 audio

Plays sound very well.  Problem is it will not record.  Have installed latest 1.14RC4 alsa kernel module but still not recording.

General observations.  Very smooth fast linux platform with good features.   And of course Ubuntu is way better than the Vista Prof that came preinstalled.

---

### Post by drplix on 2007-07-12
Should have mentioned.  You must build and install the latest ndiswrapper.  The version installed with synaptics does not work.

---

### Post by drplix on 2007-07-15
To get the SoundMax / Azalia card to work use this howto:

[https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

Note you must use the latest 1.0.14 alsa archives (not RC14 as mentioned in the howto)

Next do the following to get a consistent boot.

1) sudo alsaconf and select "SB600 Azalia"
2) Delete /etc/modprobe.d/alsa-base  (alsaconf installs */etc/modprobe.d/sound* which seems to be all you need)

Reboot.

Lo and behold.  Surround sound options and working recording. I used audacity to test.

---

### Post by drplix on 2007-07-19
One final thing.  Compiling my own alsa broke 32-bit apps like skype.  This is because the Feisty version of /usr/lib32/libasound.so.2.0.0 is not compatible with the latest 1.0.14 alsa.  To fix this you have to compile a 32 bit version of alsa-lib and replace the libasound.

Instructions for how to do this are in this thread...

[http://ubuntuforums.org/showthread.php?t=502377](http://ubuntuforums.org/showthread.php?t=502377)

---

### Post by drplix on 2007-09-17
32bit mode IDE.
-------------------

I came across this thread:

[http://ubuntuforums.org/showthread.php?t=551990](http://ubuntuforums.org/showthread.php?t=551990)

And this led me to discover that the install of Feisty on HP 6715b has 16bit IDE mode by default.  I've set it to 32 bit and all seems fine.  Edited /etc/hparm.conf and uncommented line #io_support=32.

or from shell:

sudo hdparm -c1 /dev/hda

---

