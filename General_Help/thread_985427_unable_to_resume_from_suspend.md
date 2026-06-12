---
title: "unable to resume from suspend"
date: 2008-11-17
forum: General Help
---

### Post by EvilRobotDrew on 2008-11-17
I am having a weird, and aggravating problem on my laptop, when i put my laptop into suspend, everything seems to work, when i press the power button or open the laptop's lid, instead of resuming, my computer reboots. there is no dialog, no error messages, simply the laptop acting as if i just turned it on. Hibernate resumes fine, and i didn't have this problem with 8.04, it started after i upgraded to 8.10.

the specs for my laptop are accessible below.

i am using the ATI/AMD proprietary FGLRX gaphics driver

I will be happy to post any log files necessary.

---

### Post by th89 on 2008-11-17
Had a similar problem myself. Try the following - it seemed to work for me.
> 
*gksudo gedit /boot/grub/menu.lst*
Find the line that points to kernel in use and change it from:
*kernel /vmlinuz-2.6.24-19-generic root=UUID=3038efdc-5e7f-4752-93b9-552670e33c89 ro quiet splash*
to
*kernel /vmlinuz-2.6.24-19-generic root=UUID=3038efdc-5e7f-4752-93b9-552670e33c89 ro quiet splash noapic nolapic irqfixup*

(Origianlly found on [http://mirosol.kapsi.fi/tx2020/tx2000howto.htm](http://mirosol.kapsi.fi/tx2020/tx2000howto.htm))

Reboot and it should suspend correctly!

---

### Post by EvilRobotDrew on 2008-11-17
NO DICE!

> **th89 said:**
> Had a similar problem myself. Try the following - it seemed to work for me.

(Origianlly found on [http://mirosol.kapsi.fi/tx2020/tx2000howto.htm](http://mirosol.kapsi.fi/tx2020/tx2000howto.htm))

Reboot and it should suspend correctly!

this is an excerpt from my menu.lst

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=2b3789de-6121-42c3-9df8-2fe0eec75a10 ro quiet splash
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=2b3789de-6121-42c3-9df8-2fe0eec75a10 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

i changed it to:

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=2b3789de-6121-42c3-9df8-2fe0eec75a10 ro quiet splash noapic nolapic irqfixup
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=2b3789de-6121-42c3-9df8-2fe0eec75a10 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic


i had no luck, i still couldn't resume after suspend. i will look at that link, and do some more research, i am tempted to copy my home folder to an external drive and reinstall 8.04 after this semester, resume was buggy on 8.04, but it worked at least.

thanks for the post tho, and if anyonw has any ideas i would love to hear them

---

### Post by EvilRobotDrew on 2008-12-22
Absolutely no problem with suspend or resume in Fedora 10 which is good because I needed an excuse to switch distros anyway. I like Ubuntu, but it is also the first distro i have really used and i want to see more of the linux ecosystem.

---

