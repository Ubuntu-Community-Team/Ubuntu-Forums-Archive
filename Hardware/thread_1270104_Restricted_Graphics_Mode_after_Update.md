---
title: "Restricted Graphics Mode after Update"
date: 2009-09-19
forum: Hardware
---

### Post by f1ckratte on 2009-09-19
A few days ago I performed an update as i usually do.
The update stoped at a specific place (i dont know which paket it was installing). The mouse didnt move at all, keyboard commands didnt work too. I just reseted, but now when the computer starts my external screen goes on and off a few times and in the end nothing happens. At my internal laptop screen there's a box, "restricted graphics mode" with an "OK" button. Neither Mouse nor keyboard work, so I cant klick the ok button.
I hope you can help me....

I have an HP Pavillion dv5 1040-eg with an Nvidia M9600gt, Jaunty and Win7 running on it

---

### Post by scragar on 2009-09-19
OK, first thing to do is not to panic, when you go to boot the PC at the grub menu(if the menu doesn't appear press escape) highlight your ubuntu option and press **e** to edit it, then at the linke that starts:
```
kernel  /vm...
```
press **e** again to edit this, place a space at the end followed by 3, and press enter, the **b** to boot it with this option. This will stop the booting process at step 3(command line) rather than step 5(graphical interface) as normal.

From the command line can you please run:
```
sudo apt-get update
sudo apt-get upgrade
```
If you get told an error message about needing to run dpkg-reconfigure -a then please do so:
```
sudo dpkg-reconfigure -a
```
After that either reboot or type:
```
startx
```
And see if it worked.

---

### Post by f1ckratte on 2009-09-19
thx man, solved the problem...

you know thats what i really like  at linux, you get answers that really help you out, not like windo*s, they just tell you things you've allready done and at the end they tell you they cant help you at all...

Linux lives from its comunity and the comunity rocks  :guitar:

thx for all guys :KS:):KS

---

