---
title: "strange random lockups with capslock and scroll lock leds flashing"
date: 2007-06-21
forum: Hardware &amp; Laptops
---

### Post by eldragon on 2007-06-21
every now and then, when i leave the computer idle.  after hours of idling....i get a complete lockup and caps/scroll lock leds start flashing..

sometimes, instead of this problem. i get a message that the volume control kas quit unexpectedly.

my setup:
DFI lanparty UT NF4 SLI-DR
athlon 64-939 3000
2gb (4x512 ddr400) dual channel
several ide drives (40g + 40g + 80g)
2x 80gig sata drives raid-0.
1 capture card pinnacle pctv pci (saa7134 chipset)
ati radeon x600 (with fglrx drivers)

UBUNTU feisty fawn up to date.


what logs should i post? i doubt the problem is the fglrx drivers, since the lockups started without a fglrx (or kernel) version change. 

this has been happening for weeks, yet i never experienced the problem while using the computer.

i should rule PSU out too, since this occurs while computer is idle. not under heavy load. 

any help troubleshooting this will be highly appreciated.....

thanks.

---

### Post by Trillian1138 on 2007-06-22
I've had the exact same problem! The flashing caps and scroll is the weirdest part. We don't have any hardware in common and the freeze doesn't leave any messages in /var/log/messages.

I've recently bought a wireless mouse and am using a new USB wireless LAN adapter, both of which I added around the time I started seeing the freezes. I'm trying to see if one or the other seems to be causing it, but I'm pretty sure they're not.

(As a side note, I've been having very occasional keyboard repeat issues where one key will repeat two dozen times without me holding it down. I recently moved from a USB to PS2 keyboard, as my old one died, so it's POSSIBLE that's the problem, but likewise seems unlikely.)

Please post if you find a sollution!!
-Jared

---

### Post by rjwboys on 2007-06-23
Ive been haveing the same problem letting the computer idle and sometimes when it doesnt idle i get the keyboard flashing and no errors in the /var/log/messages this has been going on for about a month now and i don't think its usb mouse / keyboard that doing it as i have a ps2 mouse/keyboard hooked up

> **Trillian1138 said:**
> I've had the exact same problem! The flashing caps and scroll is the weirdest part. We don't have any hardware in common and the freeze doesn't leave any messages in /var/log/messages.

I've recently bought a wireless mouse and am using a new USB wireless LAN adapter, both of which I added around the time I started seeing the freezes. I'm trying to see if one or the other seems to be causing it, but I'm pretty sure they're not.

(As a side note, I've been having very occasional keyboard repeat issues where one key will repeat two dozen times without me holding it down. I recently moved from a USB to PS2 keyboard, as my old one died, so it's POSSIBLE that's the problem, but likewise seems unlikely.)

Please post if you find a sollution!!
-Jared

---

### Post by CrispyFried on 2007-06-23
cant help with the problem but the blinking keyboard lights happen when the kernel wipes out (kernel panic?), its supposed to do that. guess its so you can tell the computer has dropped dead from across the room.

---

### Post by eldragon on 2007-06-24
yes.......i thought it would mean a "kernel cant handle this" type of thing....

there was a minor kernel update a few weeks ago, i dont know if it was it.


so far ive tried: 
disassembled /reassembled the entire pc.
disabled the saa7134 module from the kernel (rmmod saa7134_alsa saa7134)

reseated ram.

checked temps, everything ok.

right now: something extra happening is the volume control dies....and sometimes the system monitor which i have open to monitor cpu usage.

if anyone finds a solution, that would be great.

im still searching.

---

### Post by eldragon on 2007-06-27
ive endend up reinstalling.....how windowish of me.

nah, seriously, something had messed up with the sql server. not booting anymore.

i think i fould the problem: one of the sata cables was causing a false contact (i think).

so far so good. and i took the time to install on the raid-0 ... something i was postponing for a looong time..

now where did i leave that extra gig of ram i had removed?.... :D

---

### Post by otakuj462 on 2007-06-27
Skype 1.3 would occasionally make my system (Ubuntu 6.10) lock up in the manner mentioned above. Pretty scary that an app running in user mode would be able to do such a thing...

---

### Post by wavesound on 2007-12-12
HI
Just found this thread!!
Had the same thing here.
I was using the PC at the time with Firefox open and Open office spreadsheet running.
It all just stopped and sat there flashing the leds at me!

I think this still seems the most unstable Ubuntu I have installed.


Cheers
Bob

---

### Post by arathorn2nd on 2007-12-25
Same problem here if I leave the computer idle for half an hour or so. It happens 100% of the time.

Specs:
Seventeen 420W Power Supply
AthlonXP 2500@3200
Asus A7N8X-XE
nVidia GeForce 6800
Seagate 7200.8 80Gb
Seagate 7200.9 250Gb

Not related to the overclock or temperature, it happens even on underclock.

---

### Post by benner on 2008-01-04
there are a ton of other people with the same problems.  or at least the same symptoms.  but it seems to  happen on various versions of ubuntu, even happens on other distros.  32 and 64 systems.  ati and nvidia cards.     i just added another hard disk with windows and am getting the same thing on that so it must be hardware.   the most popular (supposed) solution seems to have something to do with this:

[http://ubuntuforums.org/showthread.php?t=644232&highlight=random+freezes](http://ubuntuforums.org/showthread.php?t=644232&highlight=random+freezes)

"...But I realized that when I boot with "noapic" parameter, system does not freeze or crash."

doesn't work for everyone though.  i can't disable apic in my bios.

 good luck.

---

### Post by Tux+ on 2008-03-23
I've just got this problem on Ubuntu 7.10. IT was working fine for at least 2 months till this happened. My usb keyboard and mouse (Logitech MX3100) stopped working. Since my motherboard doesn't work with my usb keyboard I have a ps2 keyboard tucked away at all times for those "just in case" situations.

All of a sudden the keyboard and mouse stopped working and I noticed the ps2 keyboard was flashing caps lock and scroll lock. I did a hard reset and I thought it froze again but it was usb keyboard and mouse not working. I unplugged the usb and plugged it back in and it worked. I rebooted again to make sure it worked after a restart and it did... but had another kernal panic.

I reset the bios to default because I have overclocked it and this time it's running fine. I will slowly clock it back up again but it's odd because the temps was o.k and I had overclocked it for at least a week or two before this happened. I switched out my old AMD athlon 3400 for a AMD Athlon 4000.

Specs of my linux machine:

DFI Lanparty NF4
2GB Corsair Value select
2 x Samsung 80GB SATA2 HDD
2 x Western Digital 230GB SATA2 HDD
Antec 450 Eath (Something) PSU
Dell bog standard keyboard PS2 naitive
Logitech MX3100 (USB keyboard and mouse)

Temps CPU were about 20-25 at the time and it was idle more or less with usual desktop apps open like firefox.

---

### Post by Darth_Salva on 2008-04-18
Same here... But i'm pretty sure is a hardware issue...

Well, i have my ubuntu since about a year, and just a few minutes i had for the first time this problem: I was watching "fotolog.com" of my girlfriend when suddently had the system freeze and caps/scroll lock flashing, no logs to read. I can argue is hardware related because i just brought 2 ddr rams (2x 512mb)... And like an hour ago i was experimenting with some other rams i have. Before that i've never had this kind of issue...

---

### Post by Tux+ on 2008-04-18
I too think it's hardware related. My system has been stable since I down clocked it slightly.

---

