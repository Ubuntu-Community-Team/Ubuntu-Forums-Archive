---
title: "Intel GMA 4500 Issues"
date: 2010-02-04
forum: Hardware
---

### Post by cj100570 on 2010-02-04
I just purchased an Acer Aspire 5740 and decided to install Jaunty on it. Big mistake! It appears to have installed correctly, I hear the login screen sounds, but it boots to a black screen from which there seems no escape. I've been a longtime Ubuntu user and figured I could figure it out but this is bigger than me. I only have access to my smartphone to search for answers and that's not working out so well any help you guys/gals can offer will be greatly appreciated.

---

### Post by ian2773 on 2010-02-06
On the GRUB boot menu use e to edit the command list and add the following just before the 'quiet splash' entry:-

i915.modeset=0

Then do CTRL-x to boot, you should find that Ubuntu will then boot correctly.

Once in Ubuntu....

Open a terminal and type the following:-

sudo gedit etc/default/grub

Find the line GRUB_CMDLINE_LINUX_DEFAULT and add i915.modeset=0 to it

The line should now read:-

GRUB_CMDLINE_LINUX_DEFAULT="i915.modeset=0 quiet splash"

Save the file.

Next, in terminal type update-grub

Reboot, and this should fix the issue.

Hope this helps.

---

### Post by cj100570 on 2010-02-06
The GRUB boot menu doesn't even show up but I'll give this a try and report back. Thanks.

---

### Post by fjskmdl on 2010-02-06
Hi, i'm thinking of installing ubuntu too, please let me know if the suggestion works :)

How did you make a backup of windows 7? since it doesnt have installation cds with the purchase...

---

### Post by cj100570 on 2010-02-06
How did you make a backup of windows 7? since it doesnt have installation cds with the purchase...[/QUOTE]

I didn't. The 1st thing I did upon getting the laptop was banish Windows from it. I can always order a system restore disc if for some strange reason I need to. As it stands right now I've gotten Lucid Lynx to run on the laptop with no issues. Strangely enough, the only current distro that'll run on it right out of the box is Linux Mint Helena but that'll only run at 800x600. Not 1 single distro I've tried, 6 in total, will boot into safe graphics mode. To me that's a serious issue since that's supposed to be the fall back for installation issues related to video and it should work!

---

### Post by cj100570 on 2010-02-07
> **ian2773 said:**
> On the GRUB boot menu use e to edit the command list and add the following just before the 'quiet splash' entry:-

i915.modeset=0

Then do CTRL-x to boot, you should find that Ubuntu will then boot correctly.

Once in Ubuntu....

Open a terminal and type the following:-

sudo gedit etc/default/grub

Find the line GRUB_CMDLINE_LINUX_DEFAULT and add i915.modeset=0 to it

The line should now read:-

GRUB_CMDLINE_LINUX_DEFAULT="i915.modeset=0 quiet splash"

Save the file.

Next, in terminal type update-grub

Reboot, and this should fix the issue.

Hope this helps.

Unfortunately this didn't work for me and actually briefly created another problem. Previously I was able to connect my laptop to an external monitor and see my desktop but I can't with the suggested fix. Oddly enough I can see my system booting on the laptop now but after a few moments some text races by and the screen goes blank again. It's looking like I'm gonna have to set this laptop aside until Lucid comes out. I'm so disappointed in Ubuntu right now. :cry:

---

### Post by Giggity on 2010-02-08
I also have an Acer 5750, and I can get Ubuntu to boot on by installing it with Safe Graphics.  Unfortunately, the maximum resolution I can set is 1024x768.  The native resolution is 1366x768.

Any ideas on how to fix this?  I'd hate to have to return this laptop just because of the graphics.

---

### Post by cj100570 on 2010-02-08
> **Giggity said:**
> I also have an Acer 5750, and I can get Ubuntu to boot on by installing it with Safe Graphics.  Unfortunately, the maximum resolution I can set is 1024x768.  The native resolution is 1366x768.

Any ideas on how to fix this?  I'd hate to have to return this laptop just because of the graphics.

You're better off than me because I can't even get it to install in safe graphics mode. At this point I've given up getting Jaunty to work and I'm running Lucid. Everything works!

---

### Post by Giggity on 2010-02-08
Good to know.  Downloading it now!

---

### Post by cj100570 on 2010-02-13
Unfortunately I'm gonna have to reinstall Windows 7 on this laptop. I can't get 1 single distro, with the exception of Linux Mint Helena & Lucid Lynx, to work. Unfortunately Lucid has developed a nasty little issue of not displaying the login screen if the laptop is restarted and Mint will only run at 800x600. This is truly a disappointing situation.

---

