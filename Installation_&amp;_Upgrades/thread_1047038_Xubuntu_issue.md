---
title: "Xubuntu issue"
date: 2009-01-22
forum: Installation &amp; Upgrades
---

### Post by Godfredson on 2009-01-22
I have just installed xubuntu onto my computer, I was under the impression this would be a smaller version of ubuntu but still have the graphical interface.  I've started it up, and it gave me a command line login, and I logged in, but now it looks like it's a completely command line interface.

Please tell me I'm wrong and I did something wrong.

I also have a disc for flubuntu if you think that is more of what I want than xubuntu.

---

### Post by Godfredson on 2009-01-22
Apparently I have to build the graphical interface, but when I type pico in the section needed to do it, it tells me command does not exist, someone please help.

I'm basically following a video step by step on what to do, haven't a clue what any of this is.

I tried replacing it with vi as suggested, which worked, but brought me to a blank page with a lot of underscores running down the left side of the screen, no text.

---

### Post by utnubuuser on 2009-01-22
xubuntu is basically ubuntu with xfce instead of gnome (I think it's a little more involved than that but...).

Is your xserver running?  sudo startx

If you've still no gui desktop:
sudo apt-get update
sudo apt-get install xfce

---

### Post by Godfredson on 2009-01-22
> **utnubuuser said:**
> xubuntu is basically ubuntu with xfce instead of gnome (I think it's a little more involved than that but...).

Is your xserver running?  sudo startx**_----Command not found_**

If you've still no gui desktop:
sudo apt-get update**_----Reading package lists...Done_**
sudo apt-get install xfce**_----E: Couldn't find package xfce_**

I've underlined and bolded what happened with each command.

---

### Post by Partyboi2 on 2009-01-22
Maybe you have not got xserver installed
try
```
sudo apt-get install xserver-xorg
```
then
```
sudo startx
```
to install the xubuntu desktop you would need to type
```
sudo apt-get install xubuntu-desktop
```

---

### Post by Godfredson on 2009-01-22
> **Partyboi2 said:**
> Maybe you have not got xserver installed
try
```
sudo apt-get install xserver-xorg
```**_----0 upgraded 0 newly installed 0 to remove and 0 not upgraded_**
then
```
sudo startx
```**_----command not found_**
to install the xubuntu desktop you would need to type
```
sudo apt-get install xubuntu-desktop
```**_----command not found_**

those are my responses

---

### Post by Godfredson on 2009-01-22
Someone save me? lol

---

### Post by stefangr1 on 2009-01-22
> **Godfredson said:**
> Someone save me? lol

If you login with your username (when you have arrived at the command line login), can you type:

startx

to start the graphics, and then post the output you get (I mean the error messages)?

Also, did you try the live cd, and did that work as expected?

Can you tell a bit more about your hardware (especially the video card)?

---

### Post by Godfredson on 2009-01-22
> **stefangr1 said:**
> If you login with your username (when you have arrived at the command line login), can you type:

startx

to start the graphics, and then post the output you get (I mean the error messages)?

Also, did you try the live cd, and did that work as expected?

Can you tell a bit more about your hardware (especially the video card)?

Can't tell you much, really crappy computer to be honest, just wanted to run a version of ubuntu to get the gui to run smoother.

At this point it's become far too frustrating, and I think I'm going to attempt to install my fluxbuntu CD, I'm hoping that it will automatically set up the gui.

---

### Post by snowpine on 2009-01-22
Hi Godfredson,
Xubuntu is supposed to have a GUI (Xfce), so definitely something is wrong. :(

If you post your computer's specs (processor, amount of ram) I can try to suggest a good OS for you. Here are the recommended specs for Ubuntu and Xubuntu: [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

Fluxbuntu is very cool, and it should have a GUI as well (Fluxbox). However in my experience, it is not as up-to-date and user-friendly as Xubuntu...

---

### Post by Godfredson on 2009-01-22
> **snowpine said:**
> Hi Godfredson,
Xubuntu is supposed to have a GUI (Xfce), so definitely something is wrong. :(

If you post your computer's specs (processor, amount of ram) I can try to suggest a good OS for you. Here are the recommended specs for Ubuntu and Xubuntu: [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

Fluxbuntu is very cool, and it should have a GUI as well (Fluxbox). However in my experience, it is not as up-to-date and user-friendly as Xubuntu...

I know the processor is under 200 mgh, the ram I'm running on I believe is 128.

---

### Post by Godfredson on 2009-01-22
Save me? lol

---

### Post by snowpine on 2009-01-22
Hi Godfredson, 
I love Ubuntu :) but I think on a slow computer with only 128mb of ram, you might be happier with Puppy Linux ([www.puppylinux.org](www.puppylinux.org)). It is a lot less demanding of resources than Xubuntu or Fluxbuntu. 

If you want to stick with the 'Buntu family, I do think Fluxbuntu is the lightest/fastest choice. Installing Xubuntu would almost certainly require the Alternate CD instead of the Live CD due to your limited ram. Good luck!

---

### Post by Godfredson on 2009-01-22
> **snowpine said:**
> Hi Godfredson, 
I love Ubuntu :) but I think on a slow computer with only 128mb of ram, you might be happier with Puppy Linux ([www.puppylinux.org](www.puppylinux.org)). It is a lot less demanding of resources than Xubuntu or Fluxbuntu. 

If you want to stick with the 'Buntu family, I do think Fluxbuntu is the lightest/fastest choice. Installing Xubuntu would almost certainly require the Alternate CD instead of the Live CD due to your limited ram. Good luck!

I've actually gone back and looked and realized I only have 90 mb of ram, will puppy still run?

---

### Post by Jose Catre-Vandis on 2009-01-24
From Puppy wiki
>  Minimum Hardware Requirements

Puppy has been tested on a few very old machines but the best results for the standard release of Puppy Linux to run at a reasonable pace have been achieved with the following:

CPU : Pentium 166MMX
RAM : 128 MB physical RAM for releases since version 1.0.2 or failing that a Linux swap file and/or swap partition is required for all included applications to run; 64 MB for releases previous to 1.0.2
Hard Drive : None
CDROM : 20x and up

However:
[http://www.murga-linux.com/puppy/viewtopic.php?p=101137](http://www.murga-linux.com/puppy/viewtopic.php?p=101137)

---

### Post by Partyboi2 on 2009-01-24
With 90 mb of ram you could look at [[COLOR=Blue]darn small linux[/COLOR]]("http://damnsmalllinux.org/") as another option.

---

