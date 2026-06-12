---
title: "HP DC7100: Bios update"
date: 2014-04-17
forum: Hardware
---

### Post by vanquishedangel on 2014-04-17
Ok so I upgraded my mothers computer so that she has the ability to keep using it. All she really does is play flash games and check email. Here are her specs:

HP DC7100
Intel pentuim 4 HT 64 bit 3.8 ghz
4 gigs ram
ATI Radeon 6450
Ubuntu 14.04 64bit

The issue is updating the bios, the website for HP only have bios for windows. I need to update the bios because of the upgraded processor and ram. I tried opening the .exe from hp and burning the .iso I found to a disk and running it from there but it did not work, the dvd writer she has is really old and may not be working properly, I also tried to use a usb stick but have had no luck with that either. Is there a way that this can be done in linux and I would need a step by step guide. I believe that hp has supported a version of linux on that computer back in the day. I tried using my computer to burn the disk as well but her dvd writer and mine are incompatible it seems. Mine can read and write disks and so can hers, but her computer can not read disks burned on my computer.

---

### Post by mörgæs on 2014-04-18
Some time ago I upgraded a DC7700. If I remember correctly I created a USB stick with Freedos and the .exe file and booted from that.

---

### Post by vanquishedangel on 2014-04-18
I tried freedos but was having issues getting the .exe to run. I instead swapped our disk drives while cleaning her computer and used the disk I burned on my computer. That worked and I applied the update, however the error still pops up, it is the microcode update error. 

I tried applying the update several times and still get errors each time. The computer however does boot and run despite the error. It is possible that this computer is reaching the end of its life. It used to slightly shock people when the case was touched, also the blue boot screen for hp is distorted, but Ubuntu when it boots displays correctly. The shock has stopped long ago however.

---

### Post by mörgæs on 2014-04-20
> **vanquishedangel said:**
> I tried freedos but was having issues getting the .exe to run. 
You need to be more exact. Please tell in all details what happened.

---

### Post by vanquishedangel on 2014-04-20
I used netbootin to install freedos to a usb stick, then I copied over the files in the DOS Flash folder from hp (sp40405.exe) after I extracted them. When booting from freedos the only option that worked was safe mode (granted I have little understanding of freedos, or dos for that matter, I was an IBM guy then), I could not find the files on the usb stick. I had printed out a sheet of commands for freedos as well as instructions for installing bios. The only things I could find were folders files within freedos itself.

I however got the bios cd to run and install on the computer by using my cd/dvd drive, but I am still getting the microcode error at boot. I know the processor works with this computer because I had two others back in the day with the exact same make and model for processors (sl8py) and desktop (hp dc7100). This was the third I had owned but was placed in storage because of problems with it (usb was hit or miss if it worked, it gave a light shock to those who touched the case, the disk drive is hit or miss, etc). I gave it to my mother because she was using an even older one that was not cutting it. It stopped shocking people, usb has been reliable for the last 2 years, the only problems that remain are cd/dvd drive. This microcode error is a new issue however.

---

