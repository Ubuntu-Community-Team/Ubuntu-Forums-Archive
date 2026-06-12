---
title: "bios bug?"
date: 2007-09-13
forum: Hardware &amp; Laptops
---

### Post by ats1080s on 2007-09-13
[   0.056XXX] PCI: BIOS BUG #81 [49435000] FOUND

i get this every time i try to install.....i downloaded the alternate version and i got everything to install but when i reboot it never loads linux.  the XXX changes every time i reboot.  i did some searching and found some other bios bugs but none of them were the same as mine.

btw, my laptop is an HP dv6119us, 1GB RAM, AMD Turion x2 64bit processor

---

### Post by hardyn on 2007-09-13
maybe flash up the bios?

BUT PLEASE be careful

---

### Post by ats1080s on 2007-09-13
tried that already.  then i went back to the one i had on before.  according to other people it should still boot, but mine gets a black screen and then nothing

---

### Post by kellemes on 2007-09-13
So you reverted the BIOS-update?

---

### Post by psusi on 2007-09-13
Your bios is fubar.  It isn't returning the correct answer when it is asked if it supports pci.

---

### Post by ats1080s on 2007-09-14
thats awesome.  how the hell do i fix that.  its done it with 2 versions of bios.  if this helps at all ACPI wont read my battery right either.  says its an 88000mAH which apparently is a 12 cell and mines only a 6 cell

> **kellemes said:**
> So you reverted the BIOS-update?

yes, it didnt do anything so i reverted back to the old one.

---

### Post by vooch1 on 2007-09-14
I have the same message appearing when I boot into Ubuntu. The OS boots fine, and Ubuntu runs well, however I have no sound. In checking some other posts, I have seen an option to disable ACPI in the bootloader, but this has not fixed my issue. I am using a Toshiba A135-S4467 Satellite Notebook.

I don't think this is a hardware issue related to any one brand, I think it's a problem with Ubuntu.

---

### Post by psusi on 2007-09-14
No, it is broken bios.  If you feel like compiling the kernel yourself then you could disable that check and maybe it will work, but the bios is supposed to return a 0 if it is working correctly, not an 81, as yours is. 

Wait a second though, you can boot up the livecd ok?  That doesn't make sense.  Have you tried powering off completely and doing a cold boot?

---

### Post by ats1080s on 2007-09-14
> **psusi said:**
> No, it is broken bios.  If you feel like compiling the kernel yourself then you could disable that check and maybe it will work, but the bios is supposed to return a 0 if it is working correctly, not an 81, as yours is. 

Wait a second though, you can boot up the livecd ok?  That doesn't make sense.  Have you tried powering off completely and doing a cold boot?

if you were talking to vooch1, i dunno.  i have never gotten any form of ubuntu to work.  however ive never had any problem with any other OS.  the only thing ive done as said in the first post is installed it with the alternate install cd and could not boot from the hard drive either

---

### Post by hardyn on 2007-09-14
what about another distro?

---

### Post by psusi on 2007-09-14
Have you tried booting into recovery mode?  And add the nosplash and noquiet parameters to the boot line.  

It looks like the kernel should continue executing, just without making use of the bios pci services.  This will probably lead to probelms with xwindows though.

---

### Post by ats1080s on 2007-09-14
> **hardyn said:**
> what about another distro?

ive tried other ones and they all work fine.  i wanted to give ubuntu a try but i guess ill have to wait untill the next release or untill i get a new laptop

---

### Post by qj0n on 2007-09-16
I've got the same problem on my Toshiba with Phoenix BIOS. Some of ACPI staff work olny on Windows. It is because of th agreement between Toshiba and Microsoft. As far as I know There's nothing can be done about it. I just can't control the speed of fan check temperature etc.

---

### Post by buu700 on 2007-09-16
boot with noapic nolapic irqfixup. everything works perfectly! (i have the same laptop)

---

### Post by ats1080s on 2007-09-17
> **buu700 said:**
> boot with noapic nolapic irqfixup. everything works perfectly! (i have the same laptop)

thanks, ill give it a try.  hopefully it will work for me too :)

---

### Post by vooch1 on 2007-09-17
> **buu700 said:**
> boot with noapic nolapic irqfixup. everything works perfectly! (i have the same laptop)

buu700,

A couple of questions:

1.)Who was this directed at?

2.) Where do I enter these arguments for boot?

Heck, I'll try it on my laptop as well. Ubuntu works awesome except no sound, that's the only thing I'm having a problem. I tried Fedora7, that worked well but the sound had a problem, in addition to a jumping mouse.

Thanks for everyone's help!

---

### Post by nowshining on 2007-09-18
if it's still under warranty then you should take it back where you have bought it or do a call-in and let them know your problems - it might be that your motherboard is going out or it in itself is the actual cause of the problem. - answer to OP

---

### Post by buu700 on 2007-09-18
> **vooch1 said:**
> buu700,

A couple of questions:

1.)Who was this directed at?

2.) Where do I enter these arguments for boot?

Heck, I'll try it on my laptop as well. Ubuntu works awesome except no sound, that's the only thing I'm having a problem. I tried Fedora7, that worked well but the sound had a problem, in addition to a jumping mouse.

Thanks for everyone's help!

1) anyone with an HP dv6119us

2) after you boot the cd to install ubuntu, you press F6 and enter that before going into livecd mode

---

### Post by hardyn on 2007-09-18
> **qj0n said:**
> I've got the same problem on my Toshiba with Phoenix BIOS. Some of ACPI staff work olny on Windows. It is because of th agreement between Toshiba and Microsoft. As far as I know There's nothing can be done about it. I just can't control the speed of fan check temperature etc.

Can you find any documentation stating this?  This more of that bloody MS collusion... my business class was a long time ago, but from what i remember this kind of stuff is against a free market and illegal.

is there a spec for "open ACPI"?  i know changing firmware across the industry is pretty difficult, but if you could get a couple of big players like HP and DELL behind it, it only seems like the rest of the industry would be forced to follow, then we could be free of most of this sillyness.

---

### Post by psusi on 2007-09-18
ACPI IS an open standard.  The problem is, most vendors aren't compliant with the standard, and they just ship windows drivers to work around their brokenness.

---

### Post by ats1080s on 2007-09-19
good news and bad news....it booted with those parameters but ndiswrapper, or any wireless for that matter, will not work.  see here for my other post [http://ubuntuforums.org/showthread.php?t=554156](http://ubuntuforums.org/showthread.php?t=554156)

---

### Post by jazzz337 on 2007-09-23
Try this link it worked for me to get my wireless up and runing I had to use a static ip the first time so that my laptop could find my router after that it worked fine on dhcp

//ubuntuforums.org/showthread.php?t=405990

I have the same bios bug #81  but as far as i can tell every thing seems to be working would still like to know what it is though.

---

### Post by buu700 on 2007-09-23
_Instructions on getting wireless working with a bcm43xx chipset (which the dv6119us has)_

Recently the bcm43xx-fwcutter which provided firmware/drivers stopped working, because the site that it extracted them from went down. However, there is an EXTREMELY easy to make it work!

Just extract the attached archive to /lib/firmware (as root of course)

(Then, if you don't already know, nvidia drivers con be downloaded from System>Administration>Restricted Drivers Manager)

Also, by the way, while noapic nolapic irqfixup works, i recently found out that noapic irqpoll noirqdebug is actually slightly better, because with the first one, it keeps detecting an audio cd for some reason (unless that was just some weird problem unrelated to the boot parameters...) (to change yours without reinstalling ubuntu, use the command gksudo gedit /boot/grub/menu.lst and then just replace "noapic nolapic irqfixup" with "noapic irqpoll noirqdebug" and save)

---

