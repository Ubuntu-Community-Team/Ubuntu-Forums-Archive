---
title: "Why so quiet?"
date: 2008-08-14
forum: General Help
---

### Post by codeking on 2008-08-14
Why is Ubuntu's sound so quiet?  Any time I listen to music, I have to pump it all the way up to get the same volume as 15% on windows.

---

### Post by tuxxy on 2008-08-14
Have you tried editing settings in ALSA, my system seems to run louder on ubuntu!

---

### Post by codeking on 2008-08-14
No I haven't.  I'm sorta a linux noob, how do you do that?

---

### Post by rossjman1 on 2008-08-14
Right click on the speaker icon on the top panel and click Open Volume Control. Or you can open a terminal and type
```
alsamixer
```

---

### Post by Vivaldi Gloria on 2008-08-14
Double click the sound icon on the panel. Increase volume of PCM and what not.

---

### Post by Sam324 on 2008-08-14
I'm having the same problem.  It seems that it only happens in Windows apps.

---

### Post by Minipalmer on 2008-08-15
+1

I just tried to show a friend a video on youtube, and we could barely hear it through my laptop speakers it was so quiet.

Anyone have a fix?

---

### Post by Kraid on 2008-08-16
Hello there,
i damn got the same problem.
PCM is full, and i got a high definition audio thing...
any help? :(

---

### Post by Garratt on 2008-08-16
yea mine is quiet as hell, too, i have alsa mixer turned up full and  volume on speakers halfway... very very quiet.

i got amd nvidia mb, quad 2.2ghz cpu

my devices look ugly as hell,  i fixed gfx card drivers but rest of it only just works... but only just... if i could get it saying all my drivers are sweet would be nice :(

```
garratt@ubuntu:~$ lspci
00:00.0 RAM memory: nVidia Corporation Unknown device 0754 (rev a2)
00:01.0 ISA bridge: nVidia Corporation Unknown device 075c (rev a2)
00:01.1 SMBus: nVidia Corporation Unknown device 0752 (rev a1)
00:01.2 RAM memory: nVidia Corporation Unknown device 0751 (rev a1)
00:01.3 Co-processor: nVidia Corporation Unknown device 0753 (rev a2)
00:01.4 RAM memory: nVidia Corporation Unknown device 0568 (rev a1)
00:02.0 USB Controller: nVidia Corporation Unknown device 077b (rev a1)
00:02.1 USB Controller: nVidia Corporation Unknown device 077c (rev a1)
00:04.0 USB Controller: nVidia Corporation Unknown device 077d (rev a1)
00:04.1 USB Controller: nVidia Corporation Unknown device 077e (rev a1)
00:06.0 IDE interface: nVidia Corporation Unknown device 0759 (rev a1)
00:07.0 Audio device: nVidia Corporation Unknown device 0774 (rev a1)
00:08.0 PCI bridge: nVidia Corporation Unknown device 075a (rev a1)
00:09.0 IDE interface: nVidia Corporation Unknown device 0ad0 (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation Unknown device 0760 (rev a2)
00:10.0 PCI bridge: nVidia Corporation Unknown device 0778 (rev a1)
00:12.0 PCI bridge: nVidia Corporation Unknown device 075b (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Link Control
02:00.0 VGA compatible controller: nVidia Corporation Geforce 9600 GT 512mb (rev a1)
garratt@ubuntu:~$ 


```

rest of you guys should see how your drivers are: lspci in terminal

---

