---
title: "wont boot up"
date: 2008-12-19
forum: Installation &amp; Upgrades
---

### Post by PsYcHoTiC_MaDmAn on 2008-12-19
after getting it running albeit unstably (prone to spontaneously rebooting, freezing up etc) I reformatted the disk (EXT3) and installed Xubuntu 8.10 off a fresh DVD, which I both verified, and checked once I put it in.

following the on screen instructions I then attempted to install it. only to be met with messages allong the lines of

-bash: /usr/bin/groups: input/output error
ubuntu@ubuntu:~$

and 

/init: line 231: cant open /root/dev/console: no such file
{   273.488689} Kernel panic - not syncing: Attempting to kill init!

at which point the computer is frozen and nothing short of turinng off the power will fix it.

as my other threads no doubt indicate I'm not at all experienced with linux, and am finding it rather hard to get installed on this PC, (however on the other PC I had no trouble getting it installed and running, and it worked flawlessly)

bizarly, when I borrowed the hard disk from the computer that works (Windows XP) the computer then started up with no problems, albeit a bit slow 

the computer should be up to handling xubuntu 
CPU : AMD Athlon 1200+ ([edit]no such thing as a 12000+...)
RAM : 256MB PC2100 ddr
HDD : 20GB Seagate Barracuda.

---

### Post by overdrank on 2008-12-20
> **PsYcHoTiC_MaDmAn said:**
> 
the computer should be up to handling xubuntu 
CPU : AMD Athlon 12000+
RAM : 256MB PC2100 ddr
HDD : 20GB Seagate Barracuda.

Hi and the 256mb memory may be the issue, as the minimum is 384. You can try and use the alternate cd for install as it is text based install.

---

### Post by PsYcHoTiC_MaDmAn on 2008-12-20
> **overdrank said:**
> Hi and the 256mb memory may be the issue, as the minimum is 384. You can try and use the alternate cd for install as it is text based install.

I got xubuntu as it was supposed to require less than ubuntu and this from the site 

[quote="[http://www.xubuntu.org/get](http://www.xubuntu.org/get)"]ou need 128 MB RAM to run the Live CD or 192 MB RAM to install. The Alternate Install CD only requires you to have 64 MB RAM at install time. To install Xubuntu, you need 1.5 GB of free space on your hard disk. Once installed, Xubuntu can run with 192 MB RAM, but it is strongly recommended to have at least 256 MB RAM. [/quote]

hopefully I will be able to transfer a 512MB PC3200 stick over, but first I need to upgrade this machine in order to do so.

---

### Post by overdrank on 2008-12-20
> **PsYcHoTiC_MaDmAn said:**
> I got xubuntu as it was supposed to require less than ubuntu and this from the site 



hopefully I will be able to transfer a 512MB PC3200 stick over, but first I need to upgrade this machine in order to do so.

I can not contest the minimum specs on the site but I do believe the alternate cd would be better for the low memory. It has worked in the past for me but that was Feisty 7.04 the last install of xubuntu for me. :)

---

### Post by PsYcHoTiC_MaDmAn on 2008-12-31
An update on where things are. (hence the repeat on all 3 other threads I started otherwise)

tried installing XP pro afterwards, and had a page file error, so no luck then. 

however I recieved the RAM I'd ordered for the other pc (the one I'm typing on) so transferred the 512mb stick from the 1 machine to the other. 

attempted to boot off the CD, but had no luck again, no idea what the problem was (got through the choose language etc, and when I tried install it just froze up). so transferred the hard disk to the other machine (this 1 again) reformatted it, (Ext3) and installed it via USB stick (incidently, made a mistake with unetbootin, setting it to xubuntu, when i didnt realise it was the ubuntu I had selected) and installed all the updates. 

having done that I then transferred the hard disk back to the other machines, (with a degree of worry that what had previously happened would reoccur) and it booted up fine.

I've had it running for several hours, downloaded and installed flash player, and its running perfectly. 

so works fine with 512mb of RAM, but not so with only 256 (that goes for both ubuntu and xubuntu)

---

