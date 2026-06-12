---
title: "Bios update released for HP DV6000 and DV9000 AMD notebooks"
date: 2007-12-14
forum: Hardware &amp; Laptops
---

### Post by Z_o-s-o on 2007-12-14
HP has just released Bios Rev. F3D for its AMD DV6000 and DV9000 notebooks.

Among other things, this addresses battery failure issues as well as uses a new fan control alorithm. 

The updated fan logic has made a 10-12 c difference in the idle temp of my Turion 64 2.0ghz.

---

### Post by lonniehenry on 2007-12-14
hp bios are sent down as windows .exe files.  I have completely removed windows from my machine.  How do I do an update to bios on a dv9005us?

---

### Post by Z_o-s-o on 2007-12-14
I read a thread somewhere on extracting the .exe and putting the contents on CD or USB drive, but luckily I still have Vista on a small partition.

---

### Post by Dark_Stang on 2007-12-14
So I'm looking at this and it's tempting... I've extracted the files from the executable, but I'm not sure what to use. Anybody done a bios update like this before? Here are the contents...
Complete Edit:

[http://www.linuxinsight.com/how-to-flash-motherboard-bios-from-linux-no-dos-windows-no-floppy-drive.html](http://www.linuxinsight.com/how-to-flash-motherboard-bios-from-linux-no-dos-windows-no-floppy-drive.html)

---

### Post by Z_o-s-o on 2007-12-14
Im not sure what to make of those instructions, since I did use windows to do mine.

I'd be very careful as you dont want to screw up with a bios flash

---

### Post by Rhubarb on 2007-12-14
This is how I usually update my BIOS: [http://ubuntuforums.org/showthread.php?t=318789](http://ubuntuforums.org/showthread.php?t=318789)
But unfortunately HP only supplies a windows only binary for the BIOS update.
(I sent them a comment about their clear lack of non Windows support)

I have also tried using wine to extract any files inside the binary
```
cabextract sp37159.exe
```
All this does is extract the Phoenix BIOS flashing application, the actual BIOS image is no where to be seen.
The Phoenix flashing application is again windows only, so it won't work with freeDOS.

I'll try to see if I can flash it with a live altered reactOS CD to see if it works.

---

### Post by Z_o-s-o on 2007-12-14
Im curious to see what kind of temp drops you guys get when you get it running.

---

### Post by Dark_Stang on 2007-12-14
I don't want to turn this thing into a paper weight on accident so... I think I'm going to wait or not do it at all. I'm not worried about overheating since it only goes to about 140 F (60 C) at most anway.

---

### Post by Rhubarb on 2007-12-15
Ok, after doing lots of hacking with reactOS I still can't get it to work.  It wants write access to some temporary folders (to write your old BIOS to a file, and to write out a log file), which can't seem to be done in a live CD environment.

I then tried to use a generic dos based flashing app (AWDFLASH.EXE) with the extracted Bios.wph file that gets created if you run the hp BIOS exe installer using wine (it gets created in ~/.wine/drive_c/W30A5F24) so I can use it on a FreeDOS live CD.
Unfortunantly that didn't work either, coming up with an error about the "application file doesn't match".

So the only way I guess is to install reactOS so you that you have write access to you C drive (or if you can figure out how to do it, make the reactOS live CD behave like it has write access just like the ubuntu live CD does).

I complain to HP about once every 4 months about their poor non-windows support.

---

### Post by chips24 on 2007-12-15
i have a DV2000

---

### Post by Z_o-s-o on 2007-12-15
Still the whole "fan recalibration" thing they've done must have been huge.

My Turion 64 single core has never idled a 41c since day one. Its usually idling at 54-55-56.

---

