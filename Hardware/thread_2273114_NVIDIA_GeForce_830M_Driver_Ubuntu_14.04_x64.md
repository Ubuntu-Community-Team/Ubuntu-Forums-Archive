---
title: "NVIDIA GeForce 830M Driver Ubuntu 14.04 x64"
date: 2015-04-10
forum: Hardware
---

### Post by raffael-azevedo on 2015-04-10
[FONT=trebuchet ms]Greetings.

I'm having a little hard time with Ubuntu, so i'll ask for help (yes, already checked if already posted). The same problem was posted and solved for an user, i didn't find appropriate to use the same topic. Anyway, i moved from a Dell to a HP (previous had no graphic cards and latter does have) and my graphic card NVIDIA GeForce 830M was not recognized by the system. So i tried those solutions:

1) xorg-edgers PPA: Installed, but the final result was awful. I've installed the nvidia-340, 343, 346 and 349. None have worked for me;
2) mamarley/nvidia PPA: The same result. 
3) Exit X.server and install the archive from NVIDIA's website: i've installed from command line and after the installation, i logged on, but nothing happened. I think it may have broken my Unity somehow;
4) Installed Windows 8.1: Blergh. [-X

**THE PROBLEM: **Doesn't matter the driver i install, never gets better. Alwaysscrewup my desktop environment. The effect is always like have no antialiasing at all; moving windows always give the sensation of "serrated window. Even the scrolling is annoyng. 

Please, help.
Thanks in advance!
[/FONT]

---

### Post by Keith_Helms on 2015-04-11
Do you have one of those laptops with Nvidia Optimus where there are both Intel and Nvidia GPUs on board?  Does everything not moving display okay with some or all of those solutions and it's just motion that looks crummy?

If it's not an Optimus system and it's just motion that looks bad, you might be able to make it better by going into Nvidia X Server Settings and enabling sync to vblank under GL settings.

---

### Post by raffael-azevedo on 2015-04-11
[FONT=trebuchet ms]Well, i'd never realized that. Looking up on NVIDIA's website, i found that GeForce 830M does **have** support for Optimus technology. I should have thought of that before posting here. It seems that i have to do some research, because indeed, i didn't tested the graphic cards with games, just with the moving and screen things. Thank you, Keith. I'll do some research, some tests and post the result soon.

Regards.
[/FONT]

---

### Post by dino99 on 2015-04-11
with such a card you'll better dist-upgrade to 'vivid' (15.04) which have solved the nvidia issues now

---

### Post by Keith_Helms on 2015-04-11
> **9d9 said:**
> with such a card you'll better dist-upgrade to 'vivid' (15.04) which have solved the nvidia issues now

I'm curious about what nvidia issues that vivid has solved.  

The one outstanding issue I have with Nvidia Prime is that in an Optimus system vsynching to blank isn't available for the Nvidia GPU.  From what I've read it has to do with the Intel GPU "owning" the actual display device, the Nvidia GPU is not directly connected to a display, and the Intel GPU just reads the graphics data with no synching from the Nvidia buffer and puts it on the screen.   The impact to me is that when I have the Nvidia GPU selected under Prime, videos have some screen tearing artifacts.

---

