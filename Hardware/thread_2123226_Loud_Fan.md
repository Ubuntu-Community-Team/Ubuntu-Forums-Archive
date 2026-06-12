---
title: "Loud Fan"
date: 2013-03-07
forum: Hardware
---

### Post by kome7 on 2013-03-07
Greetings everyone. :P    
So i just made the transition from Windows 7 to Ubuntu last night(First time using Linux), and although evrything is working smoothly for the most part, i have a bit of a problem: My Latop fan seriously won't STFU!! Last night i thought it might have been due to the installation it went through and not turning it off for a few hours after, so i turned it off hoping it would resolve itself this morning. Well it didn't. As soon as i turned it on it's extremely loud and it only gets louder when i open up any apps. I tried shutting off a few starup program to see if it made a diffencr but it didn't. I'm also not doing anything heavy, or anything for that matter; it just constantly stays at that high speed causing it to be loud.    Prior to last night i was running Windows 7 Ultimate x64 and it ran smoother and the fan was rarely ever hearable. The only times it would become loud was when i watched Netflix for an hour or so or played GTA4. Is there anything i can do to 'fix' this? I like Ubuntu so far but this is kind of discouraging and i REALLY don't want to go back to Windows. :confused:   

 Here's some system specs:  Sony Vaio E series(Not sure of model # but the computer is less than 2 months old, it was build when ordered in late January.)  Intel® Core™ i7-3632QM CPU @ 2.20GHz × 8 cores  16 gigs of RAM Ubuntu 12.10 64 bit  Radeon HD 7600M Series 1 TB HD    

Is it possible i should be running the 32 bit version? System monitor shows no sign of heavy CPU or RAM usage. Someone help please!!  Thanks.     EDIT*********  So i tried these two:  [http://ubuntuforums.org/showthread.php?t=1420247&page=3&p=9197545#post9197545](http://ubuntuforums.org/showthread.php?t=1420247&page=3&p=9197545#post9197545) [http://forums.linuxmint.com/viewtopic.php?f=42&t=56323](http://forums.linuxmint.com/viewtopic.php?f=42&t=56323)  I think they're esssential the same thing, though. Didn't make a difference. However, the page where i'm asked for my encryption key is no longer there during boot-up. Now there's just a black screen with text asking for it.

---

### Post by kome7 on 2013-03-07
Sorry for the terrible indentations and no paragraphs. I edited and it messed it up for some reason.

---

### Post by kome7 on 2013-03-18
Bump. Haven't gotten any further. WOuld appreciate some input.

Kinf of concluded that this a common problem in Ubuntu.

---

### Post by Yellow Pasque on 2013-03-18
Is this one of those awful Intel/ATI hybrid GPU systems? (I'm guessing it is since i7-3632QM has an IGP built into it.)
```
lspci | grep VGA
```

---

### Post by dalpi on 2013-04-13
I have a sony vaio e laptop too. This is what I did to reduce the cpu temp:

1. Install the Jupiter applet ([http://www.webupd8.org/2012/03/jupiter-applet-officially-switches-to.html](http://www.webupd8.org/2012/03/jupiter-applet-officially-switches-to.html))
2. Do the pcie_aspm=force kernel fix ([http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html](http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html))
3. Apply power saving tweaks ([https://wiki.ubuntu.com/Kernel/PowerManagement/PowerSavingTweaks](https://wiki.ubuntu.com/Kernel/PowerManagement/PowerSavingTweaks))
4. I don't use bluetooth, so I kill it on startup ([http://askubuntu.com/questions/67758/how-can-i-deactivate-bluetooth-on-system-startup](http://askubuntu.com/questions/67758/how-can-i-deactivate-bluetooth-on-system-startup))

My idle cpu temp is about 45 C. However, when I run flash videos or use skype, the cpu temperature gets really high and usually stays high, i don't know why

---

