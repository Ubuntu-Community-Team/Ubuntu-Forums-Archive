---
title: "Toshiba Qosmio optical drive issues"
date: 2010-04-01
forum: Hardware
---

### Post by Akira_Oni on 2010-04-01
I just installed Ubuntu 9.10 on this laptop:

[http://www.linlap.com/wiki/toshiba+qosmio+x305](http://www.linlap.com/wiki/toshiba+qosmio+x305)

Now my optical drive won't open when the operating system is booted (however before the OS boots it opens just fine) and while the drive can read the files on a disk I'm trying to play a DVD and it's not working for me. What should I do?

---

### Post by Fafler on 2010-04-02
First, open a terminal and type
```

sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list
sudo apt-get update
sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring 
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras app-install-data-medibuntu libdvdcss2
```

That should fix the DVD playing issue. The drive is probably locked by the os. Instead of using the eject button, left click on the drive icon and select eject.

---

### Post by Akira_Oni on 2010-04-02
That worked! Thanks! ^_^

---

### Post by nautiman on 2010-06-03
After installing 9.10, the optical drive (a Sony DW-D22A) on my desktop will not open although, just as with others, before the OS is fully loaded it opens just fine with the front button. 

I tried the software update suggested above,  but it has not solved the problem.  Also, strangely, the file browser shows 'unknown' in the Properties for the CD/DVD drive, while the Disk Utility has complete information for it in Properties.

---

