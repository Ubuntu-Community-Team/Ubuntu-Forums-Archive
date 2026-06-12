---
title: "new to ubuntu"
date: 2005-11-04
forum: Hardware &amp; Laptops
---

### Post by davgard on 2005-11-04
I am brand new to Ubuntu. I just installed for the first time last night. I am looking for information on setting up or finding out how to use cd/dvd burning software. is it already installed as part of the base packages? also any documentation/ user guides that are available. like I said I am new to this distro. any info would be appreciated.

thanks

dave

---

### Post by earobinson on 2005-11-04
Check out this link it should get you what you wanted

[http://ubuntuforums.org/showthread.php?t=84731&highlight=apt-get+k3b](http://ubuntuforums.org/showthread.php?t=84731&highlight=apt-get+k3b)

---

### Post by Kyral on 2005-11-04
Nautilus' built in burner is there, however yah, get k3b. It OWNS (And YES you can install a "KDE app" on GNOME)

---

### Post by paddyg on 2005-11-04
i've got x-cd-roast as well

```
sudo apt-get install xcdroast
```

---

### Post by SickTwist on 2005-11-04
[QUOTE=davgard]I am brand new to Ubuntu. I just installed for the first time last night. I am looking for information on setting up or finding out how to use cd/dvd burning software. is it already installed as part of the base packages? also any documentation/ user guides that are available. like I said I am new to this distro. any info would be appreciated.

thanks

dave[/QUOTE]

After a default install, Serpentine (creates audio CDs) and Nautilus (creates data CDs) are both installed which should be able to handle most of your needs. Serpentine is under "Applications" --> "Sound & Video" --> "Serpentine Audio-CD Creator". Nautilus is the file manager. You can start it by selecting "Places" --> "Home Folder". Under the "Go" menu, there is an entry for "CD/DVD Creator".

There are many other graphical burning programms available in case you would like to try something else (Graveman, GnomeBaker, K3B, etc.). Search the forums for help installing these.

---

### Post by mit on 2005-11-04
what are the equivelant of Nero, any DVD and clone dvd in Windows terms?

---

### Post by aysiu on 2005-11-04
[Table of Equivalents of Windows software in Linux](http://www.linuxrsp.ru/win-lin-soft/table-eng.html#41)

---

### Post by mit on 2005-11-04
oh, thanks! :KS

---

### Post by davgard on 2005-11-04
thanks for the tip on finding K3b I've used it before. I like the look, but I always have  a problem when I try to burn a boot disk from an ISO file, just keeps creating another ISO file. guess I'll try again. got any tips on the configuration?

dave

---

### Post by Xian on 2005-11-04
[QUOTE=davgard]I always have  a problem when I try to burn a boot disk from an ISO file, just keeps creating another ISO file. guess I'll try again. got any tips on the configuration?[/QUOTE]
Open K3B, select Tools >> CD >> Burn Image.

---

### Post by SickTwist on 2005-11-05
[QUOTE=davgard]thanks for the tip on finding K3b I've used it before. I like the look, but I always have  a problem when I try to burn a boot disk from an ISO file, just keeps creating another ISO file. guess I'll try again. got any tips on the configuration?

dave[/QUOTE]

If you're running GNOME (Ubuntu), just right click on the ISO file and select "Write to Disc".

---

