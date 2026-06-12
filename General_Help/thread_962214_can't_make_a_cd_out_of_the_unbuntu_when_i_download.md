---
title: "can't make a cd out of the unbuntu when i download"
date: 2008-10-29
forum: General Help
---

### Post by sausaged on 2008-10-29
ok well i downloaded ubuntu and infrarecorder but when i try to find the image using infrarecorder it just shows all the normal files, so i change it to Disc Images (*iso, *cue, *img) i go through all the files i downloaded and the only file i can find is    Bootable_NoEmulation.img . So i try to put it onto the blank CD i had (so far so good) but nothing happens when i put it in my drive and reboot. Maybe i made a simple mistake or am missing something. Please offer any advice you can, thanks.

---

### Post by jpkotta on 2008-10-29
You need to find out where you downloaded the .iso.  Search for files that are over 600 MB and end in ".iso".

---

### Post by pooyaplus on 2008-10-29
The default place where the system stores the downloaded files no matter what type they are in, is the home folder. 
Or maybe you are using a download manager and you set to get the downloading files somewhere else. 

try these commands in the terminal:
```

locate <filename>

```

or

```
whereis <filename>
```

---

### Post by Kevbert on 2008-10-29
Welcome to Ubuntu. 
You need to select the Actions menu and Burn Image and then browse to where the ISO file is. See [[COLOR="Red"]here[/COLOR]]("https://help.ubuntu.com/community/BurningIsoHowto"). Have you performed a hash check ? (this is important). For hash check info go [[COLOR="Red"]here[/COLOR]]("https://help.ubuntu.com/community/HowToMD5SUM").
Good luck and if you have more questions please ask.

---

### Post by sausaged on 2008-10-30
i havn't done a hask check yet but i'll looking into it, i did find the files but i didn't find an .iso i found a .img and burnt it to a disk but wouldn't the other files have to go onto the cd aswell? do i just put them all on 1 after another? i tried just the .img but nothing happens when i put it in and restart pc

---

### Post by jpkotta on 2008-10-30
What you download is an image.  You don't burn the image *file* to the disk.  Rather, you burn the *image* to the disk.  The image is like a copy of the disk, which happens to be a file on the hard drive instead of pits and lands on a CD.  So, you will never burn more than one image to a CD.  When you're done, there should not be just one file on the disk; there should be hundreds: all the files that were contained in the image.

I've never seen an Ubuntu image called .img.  Maybe it got renamed.  Or maybe you should redownload it. 
[http://ubuntu-releases.cs.umn.edu/8.04.1/ubuntu-8.04.1-desktop-i386.iso](http://ubuntu-releases.cs.umn.edu/8.04.1/ubuntu-8.04.1-desktop-i386.iso) from [http://ubuntu-releases.cs.umn.edu/](http://ubuntu-releases.cs.umn.edu/) (my preferred mirror).

---

### Post by sausaged on 2008-10-30
hmmm i think i may have an idea, the first time i downloaded i think i i might have just stuck it in a folder that is hidden or something, i can't find it but re-downloading it into some easyer to find should solve that problem, thanks everyone for the help

---

### Post by Yashiro on 2008-10-30
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

