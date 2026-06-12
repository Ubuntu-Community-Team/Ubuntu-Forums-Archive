---
title: "Configuring apt... Freeze 25%"
date: 2005-12-29
forum: Installation &amp; Upgrades
---

### Post by Ian Foster on 2005-12-29
I have just got 5.10 from the Personal Computer World DVD.
I made an iso CD using a linux command from my old OS
I tried to install 5.10 butthe system freezes when it gets to
"Configuring APT..." 25% - "Setting up primary installation repository"
This happens every time at the same point

I have made a new CD from my XP system - exactly the same problem

Has anyone else seen this?
Is there a fix?

Thanks

---

### Post by aysiu on 2005-12-30
Did you do a checksum to verify the integrity of the ISO image before burning it?

Did you try burning it at a slow speed?

---

### Post by Luthy on 2005-12-30
having the same problem. i got my cd's from shipit.ubuntu.com and its stuck at 25% right now im using the live cd to access the internet. i had Simply mepis on mine b4 switching to ubuntu. ive tried twice. i have more cd's. should i try them?

---

### Post by kenweill on 2005-12-30
The problem is in your hardware.

I have experience the same problem before. With ASROCK motherboard and Intel Celeron D processor.

It comes to a halt whether you're using Linux or Windows.

Even if you're inside the BIOS, it will came to a hault.

Thats my experience.

I don't know with you.

Try to enter into your BIOS and just do nothing. Wait. 

From my experience, after between 10-15 minutes, it will came to a halt.

---

### Post by Lindhardsen on 2006-01-02
I'm having the exact same problem, and I have tried instaling from both ubuntu cd/dvd and from kubuntu cd.

Every time the installation hits the "Configuring apt - 25%", the installation halts. looking at the cnsole screen shows that I have SCSI error / Medium error / I/O error.:( :( 

So with three different medias, the installation stops at the same spot.

Also, I have tried this with different hardware. The only hw that is the same all the way trough, is my CPU. 

So what hardware is it that you would say is faulthy? What can I do to do get this installed???

Thanks for any responses.

/Jan

HW:
ASUS AS8-v
NEC DVD readder/writer
Intel Celeron Processor
Club 3D graphics adapter

---

### Post by Lindhardsen on 2006-01-03
Does anyone have any ideas... Please

I'm abouty to explode now - have tried this  installation 20 different ways in different configurations,a nd it crashed every time :mad: 

If I only knew the source of the problem....

---

### Post by izi on 2006-02-04
Got the same problem here... :( 

Im using:

P4 2.66
MSI 848P Nevo-V
NEC - DVD

Could the NEC-DVD be the issue here ?

---

### Post by Lindhardsen on 2006-02-04
I never found the source of the problem, but I did find a work-around.

In some forums on other istes I found indications that this is an issue actually with the Celeron processor together with the DVD drive. 
So I decided just to find a quick and dirty...

I downloaded the mini cdrom image, which the DVD drive can read, and installed most of the stuff over the internet. This of corse requires good bandwidth.

You can find the mini.iso here:
[ftp://ftp.ubuntu.com/ubuntu/dists/breezy/main/installer-i386/current/images/netboot/mini.iso]("ftp://ftp.ubuntu.com/ubuntu/dists/breezy/main/installer-i386/current/images/netboot/mini.iso")

/Jan

---

### Post by egerio on 2006-02-05
[QUOTE=Lindhardsen]I never found the source of the problem, but I did find a work-around.

In some forums on other istes I found indications that this is an issue actually with the Celeron processor together with the DVD drive. 
So I decided just to find a quick and dirty...

I downloaded the mini cdrom image, which the DVD drive can read, and installed most of the stuff over the internet. This of corse requires good bandwidth.

You can find the mini.iso here:
[ftp://ftp.ubuntu.com/ubuntu/dists/breezy/main/installer-i386/current/images/netboot/mini.iso]("ftp://ftp.ubuntu.com/ubuntu/dists/breezy/main/installer-i386/current/images/netboot/mini.iso")

/Jan[/QUOTE]
Thanks Jan, The mini iso worked. It stalled when downloading from the US mirror, but worked when I used the Canada mirror.
art

---

