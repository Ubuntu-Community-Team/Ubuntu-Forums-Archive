---
title: "Help! Screen resolution is far too low to use!"
date: 2008-05-11
forum: Hardware
---

### Post by Fzang on 2008-05-11
On my desktop the screen is like 19", but at the live session, the highest resolution is 600 x 800 or something, and the lowest (which zooms in so badly it renders the display unusable) is like 200 x 300

Why is the resolution so extremely low? Can I fix it?

---

### Post by DieB on 2008-05-11
to get you right, you actually are running the live-cd when this occurs?

so it might probably be somethin with your video-chip and drivers.

please type lspci in an trminal and post the output

---

### Post by Fzang on 2008-05-11
Output is attached as picture, because I have to transfer from 1 computer to other, as the ubuntu computer doesn't have my wireless drivers

Only read the white on the second picture, as I couldn't fit it all in 1

---

### Post by Fzang on 2008-05-11
Bump

---

### Post by unutbu on 2008-05-11
Go to System>Administration>Restricted Drivers Manager. Is the NVIDIA driver enabled?

---

### Post by Fzang on 2008-05-11
- Thread Revived! -

I've checked restricted drivers and the only thing that shows is my broadcom wireless card

Am I busted?

---

### Post by Fzang on 2008-05-12
Bump

---

### Post by unutbu on 2008-05-12
Post the output to 

```
COLUMNS=150 dpkg --list nvidia*
```

---

### Post by Fzang on 2008-05-12
There:

---

### Post by unutbu on 2008-05-12
I think you need to install the NVidia driver.

```
sudo apt-get install nvidia-glx-new
```

See [http://packages.ubuntu.com/hardy/nvidia-glx-new](http://packages.ubuntu.com/hardy/nvidia-glx-new)
for a description of the package. This page is for hardy; there are links at the top of the page for the other Ubuntu distributions.

---

### Post by Fzang on 2008-05-13
Would I be able to install the package in a live session? I don't want to install ubuntu before I know how to fix my hardware problems

---

### Post by unutbu on 2008-05-13
I don't know if you can install packages in a live session. I think the answer is yes, but I'm not absolutely certain. The live session, as I understand it, holds the entire operating system and file system in RAM memory. I don't see any reason why you can not treat that file system just like a file system stored on a hard drive.

Also, this is a completely safe thing to try. If it doesn't work, there will still be no change to your hard drive.

---

### Post by mapes12 on 2008-05-13
Do you have 8.04 installed?

If yes, then how did you install it? As an upgrade over the internet or from CD as a fresh install?

---

### Post by ubuntu-freak on 2008-05-13
You can install Ubuntu and force the correct resolution, by pressing Alt F2, typing "gksudo displayconfig-gtk" and your password when prompted, then select your resolution.
 
Nathan

---

### Post by Fzang on 2008-05-13
This is my second attempt to install ubuntu

At first I tried on my laptop but it had FAR too many hardware issues

Now I'm trying on my desktop instead

I installed Hardy from a live CD from scratch

Reason why I don't want to install before I have all problems solved is that I don't know how to remove the GRUB :(

EDIT:
I tried installing NVidia drivers and it gave me a resolution of some 1700 x 1300 which makes my screen so oversized that I have to mouse in the edges to move around on the huge screen

Eh....

---

### Post by Fzang on 2008-05-13
Man... I can't install anything without having internet connection

DAMMIT!

---

