---
title: "trouble installing!"
date: 2009-09-21
forum: Installation &amp; Upgrades
---

### Post by nagasadow13 on 2009-09-21
i have already installed ubuntu 9.04 as a second operating system on my asus eee pc 1000h. all was well in the beginning but when i booted it up one day all it did was display a black screen with a bunch of typing then it asked for my username and my password and all it showed was
nagasadow13@nagasadow13-laptop:~$
all i want to do is get back to the desktop and maybe learn how to switch to and from the desktop and the black screen. any help would be fantastic! on the other hand i was told to get ubuntu net book remix so i tried but the only downloadable file are zip files which is fine but i dont know how to format it so i could boot it from a thumb drive. i have the program bitzipper i also have the program winimage any in depth instructions on what to do would be highly appreciated!! there was also talk of changing the video setting on my computer any help?? thank you

---

### Post by snowpine on 2009-09-21
The desktop in Linux is called X... so next time you get that command prompt, try typing:

```
startx
```

Please post any errors or messages back here so we can try to help you troubleshoot...

---

### Post by nagasadow13 on 2009-09-21
i tried startx but the only thing that happens is the screen faintly blinks a couple of times and then the screen reads
nagasadow13@nagasadow13-laptop:~$ (followed by a small box symbol)
in the top left hand corner of the screen in a fairly small font size. it will not let me type anything after it any suggestions or instructions?? thank you

---

### Post by stlsaint on 2009-09-21
> **nagasadow13 said:**
> i tried startx but the only thing that happens is the screen faintly blinks a couple of times and then the screen reads
nagasadow13@nagasadow13-laptop:~$ (followed by a small box symbol)
in the top left hand corner of the screen in a fairly small font size. it will not let me type anything after it any suggestions or instructions?? thank you

what you are seeings is called CLI or Command Line Interface...
Im not quite sure what error your getting tho?

---

### Post by snowpine on 2009-09-21
Cool, that is a good sign!

Reboot back to the "command line interface" and type:

```
sudo apt-get install ubuntu-desktop
```

This should restore your system back to the basic Ubuntu desktop in case you accidentally deleted something important. :)

---

### Post by Bucky Ball on 2009-09-21
Try to boot in via the recovery kernel. Watch the screen and see if it throws any more light on your problem. 

UNR is installable via an existing Ubuntu install with 9.04 - you shouldn't need to download zip and make a USB boot.

---

### Post by gadolinio on 2009-09-21
I've downloaded the netbook remix version, and it was a .img file what i got. Then with the application called imageWriter i "burnt" the image to a usb drive; it worked ok in live mode at least. Didn't tried installing it

---

### Post by nagasadow13 on 2009-09-22
to snowpine thanks for the info i tried the command you suggested it seemed to be working fine but then it said i had missing archives. so i said 'f' it and just reinstalled the whole thing. i do have question about how to get rid of the previous version that i installed. i know i shouldnt be so inpatient but i have been working on fixing this little dilemma for over a week now. i am aware of gpart but i was curious about any tips one could offer out there?! bottom line is i would like to just have one ubuntu 9.04 installed on my hard disk at one time, and be able to have a decent amount of disk space available with said operating system to reap its full benefits. any instructions tips advice step by steps anything to help in anyway would be highly appreciated in the greatest regard!! thank you

---

