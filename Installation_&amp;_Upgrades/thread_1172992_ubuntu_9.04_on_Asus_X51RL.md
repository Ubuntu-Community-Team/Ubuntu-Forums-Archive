---
title: "ubuntu 9.04 on Asus X51RL"
date: 2009-05-29
forum: Installation &amp; Upgrades
---

### Post by spiner on 2009-05-29
Hi there.

I've been trying since long time to install ubuntu 9.04 on my Asus X51RL laptop without success; up to 8.04 everything was perfectly fine.

I've been looking in the web for informations really a lot, but none of the hints I found worked (including all the kernel parameters to be passed on boot command line).

Three different aspects of the problem: the famous "ata1: softreset failed" message, the fact that after the initial screen the system jumps into busybox prompt after playing a little bit with the hard disk and the fact that with the alternate CD after the bootstrap the cdrom drive is not recognized and no driver/module is available to be loaded.

My suspect is that the problem could be the need for the ide-scsi module that it's not there.

Is there anybody with the same laptop who was more lucky than me?

Any suggestion will be really appreciated.

Thanks in advance!

---

### Post by spiner on 2009-06-01
Hi again.

Am I the only one who bought this laptop? :D

Rgs.

---

### Post by dr.kandimba on 2009-06-09
No, you are not the only one. I also have this laptop and I can't install ubuntu :~(

---

### Post by woozly on 2009-06-09
Asus PRO55 work fine !
 
If you face ati mobile gpu try to reinstall ati catalyst driver.
 
- Start ubuntu in runlevel 1.
 
[IMG]http://img.ly/media/3183/large_grub.JPG?1244550556[/IMG]
> 
Select you system kernel press -->e 
go to --> kernel press -->e

 
[quote]grub edit> kernel /boot/vmlinuz-2.6....... init 1quote]
Add init 1 to the end ----> enter
press --> b to boot this option
 
init 1 = boot without GUI
 
NOTE: this is only a temporary configuration ... after reboot obtion is reseted.
 
- Download and install catalyst driver
 
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9-3-x86.x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9-3-x86.x86_64.run)
 
#wget --no-check-certificate [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9-3-x86.x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9-3-x86.x86_64.run)
 
./ati-driver-installer-9-3-x86.x86_64.run
 
chears 
woo

---

### Post by spiner on 2009-06-17
Hi there.

Solved, the installed DVD drive was not compatible with new kernels (tried to recompile the kernel tons of times but no result).

Changed the drive with another one (from Pioneer, the original one was Liteon) and now everything is ok.

---

### Post by orly2001 on 2010-02-21
hello everyone, i am a new ubuntu user, (20 feb 2010),

Asus x51rl ap010c: 1gb ram,t310(duo1,46ghz) dvd matsui, 160gb hdd, atheros 802.11bg, ati x1100. ricoh card reader sd, 
ex win vista, now Ubuntu karmic koala and very satisfied.


probs at install: mic was low, alsa mixer took care of that.
                       suspend to ram not working, doesn't bother me much but would be nice
                       hibernate was tricky but i don't remember excatcly.. maybe it was disactivating a software modem driver
other probs: none so far
other hardware: bluetooth dongle (usb-sitecom), works fine out of the box
                        trust flex cam web cam (omnivision drivers)found and  installed drivers from ubuntu forum, very easy
                        trust wireless optical 7 button mouse, out of the box
                        hp officejet 6310 over lan, out of the box
                        canon pixma, out of the box
                        wireless lan, out of the box

will now check: dvd writer, headphone jack, trust (micordia) web cam 15007, italian language, usb 3 port hub

battery lasts approx 15 mins more than with vista! 
I'm sorry if this is not very detailed or techy... and hope it helps!

---

