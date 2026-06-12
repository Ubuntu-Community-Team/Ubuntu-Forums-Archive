---
title: "Help with Intel ICH5 sound"
date: 2006-03-25
forum: Hardware &amp; Laptops
---

### Post by KiLLeR_WoMBaT on 2006-03-25
I have tried and tried and tried to get this working without reloading Breezy.  Can someone please help?  Here are the specifics again:

At first boot there is sound at the log in screen.  Once logged in there is no sound.  Attached are some screenshots of things I've been told to try and the output given.

cat /proc/asound/cards gives the following:

daniel@WoMBaT-Laptop:~$ cat /proc/asound/cards
0 [ICH5           ]: ICH4 - Intel ICH5
                     Intel ICH5 with ALC650F at 0xe8000c00, irq 17

The sound quit working after using Automatix, but I don't know what module it installed that broke the sound system.  If there is some log I need to post or the output of some command to better diagnose the problem then please let me know what it is and I will post it.

---

### Post by BOK on 2006-03-26
Never heard of a "ICH5", so please send the output of "lspci -vv" to see what device-name is given.

OT: Your card is (partly) recognized, my SiS7012 hasn't worked on ANY Linux...

---

### Post by KiLLeR_WoMBaT on 2006-03-26
[QUOTE=BOK]Never heard of a "ICH5", so please send the output of "lspci -vv" to see what device-name is given.

OT: Your card is (partly) recognized, my SiS7012 hasn't worked on ANY Linux...[/QUOTE]

Okay here is the output of lspci -vv:

---

### Post by KiLLeR_WoMBaT on 2006-03-27
Nothing?  Nobody?  I've only been trying to fix this for a month now.  Come on, where are all the seasoned linux veterans?  Ubuntu used to be famous for it's community help.  Somebody PLEASE assist me, I'm begging.

---

### Post by jajemera on 2006-07-20
Hello. You might be using a mono speaker, like the ones built in the pcs itself. I have an IBM Thinkcentre A50 and initially the sound isn`t working. What you should do is double click on the speaker icon, then on the preferences, check master mono and increase the volume(it is initially set to zero). That should work. In case you aren`t using a mono speaker, try tweaking the others tracks in the preferences list.:cool:

---

### Post by this is not kasker on 2007-03-18
Thanks jajemera that was helpful. I am also using the intel ICH5 and had the same problem. What jajemera said worked except I only had to unmute the PCM volume control instead of mono control.

---

