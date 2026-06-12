---
title: "Compaq cq60-220us acpi errors on bootup"
date: 2009-07-16
forum: Hardware
---

### Post by Mriswithe on 2009-07-16
I am running ubuntu 9.04 on a compaq laptop running a sata drive and every time I boot up be it from a suspend, hibernate or a complete shutdown/reset I get the following message, I pulled the message from the kern.log:
```
Jun 29 18:55:03 mriswithe-laptop kernel: [    7.740017] ata2.00: ACPI cmd 00/00:00:00:00:00:b0 failed (Emask=0x4 Stat=0x00 Err=0x01)
Jun 29 18:55:03 mriswithe-laptop kernel: [    8.224015] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jun 29 18:55:03 mriswithe-laptop kernel: [   13.224007] ata2.00: qc timeout (cmd 0x0)
Jun 29 18:55:03 mriswithe-laptop kernel: [   13.224016] ata2.00: ACPI cmd 00/00:00:00:00:00:b0 failed (Emask=0x4 Stat=0x00 Err=0x01)
Jun 29 18:55:03 mriswithe-laptop kernel: [   13.224061] ata2.00: ACPI: failed the second time, disabled
Jun 29 18:55:03 mriswithe-laptop kernel: [   13.224063] ata2.00: revalidation failed (errno=-5)
Jun 29 18:55:03 mriswithe-laptop kernel: [   13.224104] ata2: limiting SATA link speed to 1.5 Gbps
Jun 29 18:55:03 mriswithe-laptop kernel: [   13.708015] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
```

Only this part actually shows on startup

```
Jun 29 18:55:03 mriswithe-laptop kernel: [    7.740017] ata2.00: ACPI cmd 00/00:00:00:00:00:b0 failed (Emask=0x4 Stat=0x00 Err=0x01)
Jun 29 18:55:03 mriswithe-laptop kernel: [   13.224016] ata2.00: ACPI cmd 00/00:00:00:00:00:b0 failed (Emask=0x4 Stat=0x00 Err=0x01)
Jun 29 18:55:03 mriswithe-laptop kernel: [   13.224063] ata2.00: revalidation failed (errno=-5)
```

I don't know for sure but I am fairly certain that this is slowing down my startup, now this isn't the most important thing to me but when I was running feisty faun it did the same thing. my computer is a cq60-220us compaq laptop. 

Any info is greatly appreciated.

Mriswithe

---

### Post by adaren on 2009-07-16
My Compaq laptop has the same problem :confused:

---

### Post by shiny11100 on 2009-07-17
hey we have the same computer =)

it must just be an incompatibility with the presario CQ60 series or something because i have the same computer and the same problem... i dont think its a big problem but it slows down the booting a lot... my dell latitude C840 boots in half the time and its a lot slower computer...

it will probably be fixed soon =) bugs dont usually live long once they've been found, atleast with ubuntu... cant say the same for windows...

---

### Post by lenn-art on 2009-07-17
Same here Compaq CQ 60!

(and do your wifi work? Mine is gone after an update :( )

---

### Post by Mriswithe on 2009-07-17
I actually noticed two things that disrupt my wireless in 9.04. Installing adobe acrobat reader (no idea why, but I installed it... wireless stopped working... uninstalled and it worked again) Also check your hardware profiles to see if the madwifi alternate is available... if you are running 8.10 then I suggest upgrading as in 9.04 wifi worked right off without using the madwifi alternate driver.

---

### Post by adaren on 2009-07-17
I start to think maybe it's the driver for ICH9 SATA controller. 
My CQ60 blue screen when I install winXP SP2,saying that the drive have problems. :(

installing other OS(even winXP) on a vista designed computer could be frustrating :(

---

### Post by dli8ilb on 2009-09-21
sorry to bump this thread so hard, but i'm having a similar problem on a **Compaq Presario CQ60-211DX** Notebook running a fully up to date Jaunty.

at the grub menu, it boots just fine to the latest kernel (2.6.28-15-generic) and over the course of 15-20 seconds, spits out these messages:

```
Boot from (hd0,2) ext3  ddc911b4-blah-blah-blah-bunchofcharacters
Starting up ...
[    7.692015] ata2.00: ACPI cmd 00/00:00:00:00:00:b0 failed (Emask=0x4 Stat=0x00 Err=0x01)
[   13.176015] ata2.00: ACPI cmd 00/00:00:00:00:00:b0 failed (Emask=0x4 Stat=0x00 Err=0x01)
[   13.176062] ata2.00: revalidation failed (errno=-5)
```

it seems like this laptop should boot much faster (2.16GHz, 2GiB RAM)
has anyone found a solution?  is this only an issue with the Compaq Presario notebooks?

---

### Post by Mriswithe on 2009-09-21
> **adaren said:**
> I start to think maybe it's the driver for ICH9 SATA controller. 
My CQ60 blue screen when I install winXP SP2,saying that the drive have problems. :(
(
Actually this is because you have a sata chipset that winxp doesn't have drivers for natively the solution to this is to use nlite to slipstream(add to the install) the driver into the xp image, then reburn and use that. There is a guide out there for how to downgrade most vista compaq/hp laptops it is located here:

[Over here]("http://h30434.www3.hp.com/psg/board/message?message.uid=83267")

Now I did have other issues with xp such as abysmal reboot times (if you thought UBUNTU too long to load, you ain't seen nothin yet!) and horrible performance so I gave up and just run ubuntu with xp in a virtual box. 

I do still want to find out why this acpi error is popping up though as it does appear to slow down my restart times.

---

### Post by shiny11100 on 2009-10-05
just installed beta of 9.10 and it's still not fixed :confused:

---

### Post by shiny11100 on 2009-10-05
[SIZE=7]THOUGHT JUST CAME TO MIND!
[SIZE=2]audio card maybe? i have both vista and ubuntu and something that i have noticed is that in vista there's a lack of stereo mix in the audio devices menu...

i wouldn't be surprised because the audio card has caused me 2 other problems so far.... fallout 3 fails to start... and I CANT RECORD VIDEOS WITH AUDIO! (because of the lack of stereo mix :-s)

it's just a guess, but ***maybe*** it's a good guess ;)
[/SIZE][/SIZE]

---

### Post by shiny11100 on 2009-11-05
hey just an update... i ran the updater and (with a LOT of effort) updated Ubuntu (jeez it was a freaking nightmare to update O_O) and the startup errors are COMPLETELY GONE!!! WEWT!!!! =)

in case you're wondering why it was a nightmare to update... i ran the updater and when it restarted it just showed the login screen... my mouse/keyboard wouldn't work so i had to hold down the power button... then i started up and once it got to the login screen it froze and the screen kept flashing :confused: so i pressed the power button, booted into recovery mode, ran the package repair function... it took longer to run that then it did to install ubuntu... ok i restarted... hmm... still not working... i had to dig through a box of cords to find an ethernet cable, hook it up... ran the repair program again... once again it took REALLY LONG it asked me to say y/n to continue... i pressed y... my computer shut down... i booted into recovery again... ran package repair again... didnt take very long this time... pressed y and hit enter... waited a few seconds... hit enter... restarted and yay it worked again :) turned out two packages failed to install...

ANYWAY... the point of this is to say that this is finally fixed (yay!) and it starts up a lot faster (yay!)

---

