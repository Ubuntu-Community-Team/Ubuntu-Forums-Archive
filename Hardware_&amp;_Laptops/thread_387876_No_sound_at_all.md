---
title: "No sound at all??"
date: 2007-03-18
forum: Hardware &amp; Laptops
---

### Post by Opeth115 on 2007-03-18
Ok well i just installed feisty and everything works awesome i even got beryl up and running.  the only thing that doesn't seem to work is my audio card.  i have a Sound Blast X-Fi Xtreme Audio card and i can't get any sound out of it anyone have any solution to this?

edit:  also oh yea my ipod will not be recognized at all either  (nvm fixed)

---

### Post by Opeth115 on 2007-03-19
anybody have any sort of solution for this?  my sound is really important as im a major music person.

---

### Post by Opeth115 on 2007-03-19
Bump maybe?  this is my lspci output  it says i have a different sound card theni really do... i have an onboard sound but would much rather use the audio card i bought.

```
00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
00:03.0 Communication controller: Intel Corporation 82P965/G965 HECI Controller (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82566DC Gigabit Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #2 (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801H (ICH8 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GS] (rev a1)
03:00.0 IDE interface: Marvell Technology Group Ltd. Unknown device 6101 (rev b1)
[COLOR="Red"]07:01.0 Multimedia audio controller: Creative Labs SB Audigy LS[/COLOR]
07:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)

```

---

### Post by Opeth115 on 2007-03-19
Could anyone please help me with my sound problem neaither my onboard audio nor my audio card works i wuold like at least one to function for me so i can listen to music and create it.

---

### Post by r4ik on 2007-03-19
Try,

[http://www.ubuntuforums.org/showthread.php?t=205449&highlight=sound+guide](http://www.ubuntuforums.org/showthread.php?t=205449&highlight=sound+guide)

Good luck !

---

### Post by gilgongo on 2007-03-19
I don't know if this is your problem, but what worked for me is this:

1. Open a terminal
2. Type "alsamixer"
3. You will see an application that looks like it came out of the 1980s.
4. Use the arrow keys to navigate to the PCM volume and turn it up, or unmute it (using the "m" key) if necessary. You may have to mute/unmute/modify other things too.
5. Hit Esc to save and see if you now have better sound.

---

### Post by Opeth115 on 2007-03-19
Ok well neither of thsoe worked and i have found out that my sound card has no linux drivers for the time being and someone mentioned theyd be released in Q2 2007... What does that mean lol?  also i have an onboard sound card on my mother board which is a DP965LT is their anyway that i would be able to get that going instead of my actual sound card untill the drivers are released?

---

### Post by Opeth115 on 2007-03-21
Can anyone help me with getting my onboard audio to work?? i enabled it in biod and ubuntu sees it and i can select it but still no sound...

---

### Post by srt4play on 2007-03-21
Have you removed your PCI sound card to make sure there's no conflicts between the two?

---

### Post by Opeth115 on 2007-03-22
Ok well i got my sound to work in ubuntu but i had an amd64 version installed so i decided to reinstall to i386 but no i can''t get sound anymroe.   I thought id be able to do the same thing as i did before but i guess not.  My audio card was still plugged in when i started and i had audio during the initial install, but after i downloaded and installed all the updates (541 or something around there) my sound no longer works.

---

### Post by Opeth115 on 2007-03-22
ok thanks everyone ig ot it all i had to do was disable it in bios and then renable it...

---

### Post by santho on 2007-03-22
That's what I had to set my alsamixer to to get back the sound. Not the first time I had this issue, which is why I made a screenshot this time. Hope this helps somebody.

[http://www.ifsr.de/~thomas/tmp/alsamixer.png]("http://www.ifsr.de/~thomas/tmp/alsamixer.png")

---

