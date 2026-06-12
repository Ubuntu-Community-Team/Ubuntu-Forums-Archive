---
title: "&quot;Checking battery state...&quot;"
date: 2009-05-30
forum: Installation &amp; Upgrades
---

### Post by allnamesareinuse on 2009-05-30
I'm a complete Linux rookie so bear with me please.

I installed the OS just fine using [this walkthrough]("http://forums.govteen.com/showpost.php?p=4830084&postcount=2").  Installing an OS is nothing new and it went flawlessly.  Everything seemed to be fine, but after restarting the OS, I can no longer boot it back up.  I get the following:

[http://i43.tinypic.com/2qw37yu.jpg](http://i43.tinypic.com/2qw37yu.jpg)

I've Googled the heck out of this but have found no solution.  Any ideas?  :(

Basic specs:
DesktopPC
Windows 7
Intel Core 2 Duo E6400 (Allendale) 2.13GHz
Two NVIDIA GeForce 7900 GTX's

[COLOR=Red]EDIT: [/COLOR] I've discovered that this has something to do with dual GPUs.  When booting with one card, the OS boots fine.  I put the second card back in and the problem is back.

---

### Post by allnamesareinuse on 2009-05-31
Anyone?

---

### Post by cottfcfan on 2009-06-03
Same problem here.
Anyone know of a fix...?

---

### Post by rogier.de.groot on 2009-06-03
Try booting with the "acpi=off" parameter. This is not a permanent fix but should allow you to boot.

---

### Post by allnamesareinuse on 2009-06-05
> **rogier.de.groot said:**
> Try booting with the "acpi=off" parameter. This is not a permanent fix but should allow you to boot.

I don't have any idea what that means.  Could you explain in detail please?

---

### Post by rogier.de.groot on 2009-06-08
When te computer boots up, the boot manager (GRUB) comes up. This is what lets you pick either Linux or Windows for instance. In GRUB, select the normal boot-up line for your Ubuntu installation & press 'e'. This let's you edit some options in another screen. Select the line that starts with 'kernel' and press 'e' again. Add the option 'acpi=off' at the end of the line (without quotes) and press 'b' to continue booting. You can also edit /boot/grub/menu.lst to permanently add this option.

---

### Post by NeoDude007 on 2009-06-08
I get this same exact screen after (I think) the video drivers usually. No matter how many times I reinstall Ubuntu I end up getting this error as well. It seems like people have been getting this error for like the past 6 years according to Google searches which bring up a bunch of garbage.

How do people get around this?!?! There must be a way. I can't show off Linux and build the community if I cannot get past 800x600 resolution... I will make my own post about this when I gather more details. I am a lil tied up atm =/ Just wanted to say there are many people experiencing this issue.

---

### Post by allnamesareinuse on 2009-06-11
> **rogier.de.groot said:**
> When te computer boots up, the boot manager (GRUB) comes up. This is what lets you pick either Linux or Windows for instance. In GRUB, select the normal boot-up line for your Ubuntu installation & press 'e'. This let's you edit some options in another screen. Select the line that starts with 'kernel' and press 'e' again. Add the option 'acpi=off' at the end of the line (without quotes) and press 'b' to continue booting. You can also edit /boot/grub/menu.lst to permanently add this option.

After doing that it appears that there is a bunch of loading or checks and balances happening.  I see DOS scrolling through all sorts of stuff for about a minute or two and then it stops at the following:

[URL="http://i40.tinypic.com/15ea9uc.jpg"]http://i42.tinypic.com/ao8g9i.jpg
[/URL]

---

### Post by mwhite212 on 2009-06-11
I'm having the same issue. The live 8.10 CD works perfectly and when I try to do a WUBI install, it locks up at "Checking battery state." This seems to be a pretty common problem. I certainly hope it is being addressed.
 
If anyone knows a workaround, please enlighten us. But I really just don't understand how it could work for the live CD and not the install. What is happening under the hood to make that happen?

---

### Post by rogier.de.groot on 2009-06-20
Did you try booting with the "pnpbios=off" parameter added (also via GRUB), like the screenshot suggests?

---

### Post by slamhound on 2009-06-20
I think if you get to the screen described in the original post and you have two video cards, you need to run nvidia-xconfig -a (the -a enables all gpus).  

The procedure (and a workaround for one typical problem) is described in a reply to another poster's problem:

[http://ubuntuforums.org/showpost.php?p=7452633&postcount=2](http://ubuntuforums.org/showpost.php?p=7452633&postcount=2)

---

