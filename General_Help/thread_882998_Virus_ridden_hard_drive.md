---
title: "Virus ridden hard drive"
date: 2008-08-07
forum: General Help
---

### Post by Patricrawley on 2008-08-07
My friend has a really virus ridden hard drive and we are trying to reformat it with an ubuntu live disk. The install did not read the disk and said there were no devices available, the ide cables are plugged in so that isn't the issue. I also booted into linux with a live session and tried gparted but that also did not recognize any drives. Any suggestions? We dont have the money for a new hard drive and his windows only lasts about ten minutes before a blue screen of death from the virus's over running the pc. What can we do?

---

### Post by tamoneya on 2008-08-07
what is the output of running this command in terminal:```
sudo fdisk -l
```

Am i correct to assume this is a single drive system?

---

### Post by Patricrawley on 2008-08-07
It is a one drive system and there was no output. It just went to another line.

---

### Post by Patricrawley on 2008-08-07
bump

---

### Post by Shazaam on 2008-08-07
If the Ubuntu livecd version of gparted doesn't work go here, download the gparted livecd iso, burn it SLOWLY (4x if possible) as an image to cd....
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
This is a stand-alone version of gparted.

---

### Post by tamoneya on 2008-08-07
> **Patricrawley said:**
> bump

please do not bump for 24 hours.  As for what else to try can you give us the output of ```
dmesg | tail
```
Also do you have any model numbers or specs on the computer.  It would help to be able to look up chipsets and such.

---

### Post by HermanAB on 2008-08-07
It is best to repair Windows using BartPE.  Make a Windows bootable CD with ClamWin, Spybot S&D and Hijackthis, then you can easily repair any PC:
[http://www.nu2.nu/pebuilder/](http://www.nu2.nu/pebuilder/)

---

### Post by Patricrawley on 2008-08-07
I dont have any specs, sorry it's not my computer.


That gparted thing did not work either, Shazaam

We dont want to repair widows, Herman, we want to put Ubuntu on it and wipe the hard drive.

The output for the code you asked for all it gives is network and bluetooth information.

---

### Post by ugm6hr on 2008-08-07
2 thoughts:

1. Do a diagnostic check on the HD.  Most HD manufacturers have CDs available for download - or use the ultimatebootcd.

2. Wipe the HD completely using something like Active Killdisk.

Then try again.

---

### Post by lisati on 2008-08-07
It might be an idea to check the BIOS settings for the hard drive while you're at it, including any "audodetect" options that the machine's BIOS might provide. There is a possibility that the "nasties" have changed something just enough to throw things off.

---

### Post by alzie on 2008-08-07
This sounds similar to the problem I had on my wife's computer.  The MBR sector on the hard drive was corrupted.  I used a copy of Ultimate Boot CD to resurrect the drive.

[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

Using the diagnostic tools on the disc for her particular Hard Drive I was able to write the entire disk to zeros.  After I had done this I was able to fully format the drive and install her choice of Operating System.

I agree with other posters to check the bios to makes sure the boot order is correct.

You might try removing the Hard Drive and cables and inspecting them for signs of corrosion as well.  Simply removing and replacing has been know to make hard drives work again.

I hope this helps

---

### Post by Comhra on 2008-08-07
Or, you could format the HD  with Darik Nuke Disc, just type: 'quick' when you see the prompt.

---

### Post by Patricrawley on 2008-08-08
Sorry, i dont know when we can get back to trying to fix his computer. Thank you for all the suggestions though and I will take them all into consideration when we try to fix his computer the next time.

---

