---
title: "Ubuntu Installer unable to recognize my keyboard and mouse"
date: 2009-07-06
forum: Installation &amp; Upgrades
---

### Post by Tarantella on 2009-07-06
Hi,

I just tried several times to install ubuntu 9.04 in mi PC (it is a Gateway GT4230m with windows vista) but when the installer pops in the mouse and keyword just freezes, i cant control them.

I tried with another mouse that is not usb but it didnt worked.

My disc is working, i runned the utility to check if its integrity is good, and it is.

Can anyone help me please?

srry for my inglish.

---

### Post by Tarantella on 2009-07-06
Please someone help, im so tired of windows vista #-o

---

### Post by presence1960 on 2009-07-06
Go into your BIOS and see if you have an option for USB Legacy support. This will work for USB peripherals.

---

### Post by Tarantella on 2009-07-06
> **presence1960 said:**
> Go into your BIOS and see if you have an option for USB Legacy support. This will work for USB peripherals.

The option is enabled :(

---

### Post by presence1960 on 2009-07-06
did you MD5SUM the iso after you downloaded it. See here:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

The hashes to check against are here: [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

If they don't match exactly your image iso is no good.

---

### Post by Tarantella on 2009-07-06
> **presence1960 said:**
> did you MD5SUM the iso after you downloaded it. See here:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

The hashes to check against are here: [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

If they don't match exactly your image iso is no good.

Thx, didnt know about that. I just checked my iso file and it is OK. I also checked the CD integrity in the main menu (when they ask you if you want to try the OS without installing, or install i) and the result is good integrity :(

---

### Post by Tarantella on 2009-07-06
I just tried to use the "try ubuntu without installing it" from the boot menu. It loads perfectly but when the OS screen pops up it happens just the same. It's like the OS is missing my mouse and keyboard drivers or something, but it cant be, i just tried with other keyboard and other mouse...

The OS doesn't freezes, because I can see the clock running.

Is this a bug? help please

---

### Post by presence1960 on 2009-07-06
[http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

If all else fails try the alternate text based installer from here: [http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

---

### Post by Tarantella on 2009-07-06
> **presence1960 said:**
> [http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

If all else fails try the alternate text based installer from here: [http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

Oh thank you so much. I'm downloading it now, if it works (or not)I'll post here what happened.

---

### Post by Tarantella on 2009-07-07
It didnt work :(

The problem was the same, when the first screen shows (with the ubuntu logo and the option to install ubuntu or boot from first hard drive) the keyboard works just fine, but when I select "install ubuntu" and the other screen shows (with the language options) it just dies, and my mouse too.

why? :confused:

---

### Post by Tarantella on 2009-07-07
bump?

---

### Post by Tarantella on 2009-07-11
please?

---

### Post by lanenem on 2009-07-11
[FONT="Arial"]Same problem.  I have a dual boot computer.  Keyboard and mouse work fine in XP; in 9.04 they are completely dead.

Too bad.  I am interested in switching from MS, but: No sound in 8.x + No keyb in 9.04 + No mouse in 9.04 = No ubuntu for me.

Definite bug.


[/FONT]

---

### Post by alimooghashang on 2009-07-13
> **presence1960 said:**
> did you MD5SUM the iso after you downloaded it. See here:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

The hashes to check against are here: [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

If they don't match exactly your image iso is no good.
i have checked 
```
md5sum ubuntu-9.04-desktop-i386.iso 
66fa77789c7b8ff63130e5d5a272d67b  ubuntu-9.04-desktop-i386.iso
```

and the iso file is OK.
but the burned CD is worng

```

 md5sum -c md5sum.txt | grep -vi 'OK$'
md5sum: ./casper/filesystem.squashfs: Input/output error
./casper/filesystem.squashfs: FAILED open or read
md5sum: WARNING: 1 of 65 listed files could not be read
```


is there any way to make it correct?
how should i burn it which doesn't hurt?

---

