---
title: "Trouble setting up dual monitors with Intel Haswell graphics card"
date: 2015-03-22
forum: Hardware
---

### Post by gil-jlem on 2015-03-22
I am very new to Ubuntu (64-bit, installed via flash drive), so please excuse any errors in the following information or misunderstandings in my replies.

My desktop's processor is Intel® Core™ i3-4130 CPU @ 3.40GHz × 4. Graphics card is Intel® Haswell.

My current monitor is an Acer V196HQL and I am trying to set up an additional monitor, an LG L196WTQ. I initially thought it would be as simple as using a VGA Monitor Y-Splitter cable, which I bought and plugged in.

However, instead of recognizing two different displays, my computer only recognized one display - "Unknown" (see screenshot #1). Both monitors are currently mirroring the same display.

I did some Googling and saw that the problem might be with the drivers for the graphics card. So I downloaded the Intel Graphics Installer, which wouldn't run until I upgraded from my OS from 14.04 (Tasty?) to 14.10 (Unicorn).

Then, based on what I read in the last post on this page [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1104230](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1104230) , I tried to update my kernel following the instructions someone gave, which apparently solved a seemingly-similar problem.

However, now when I try to run the Intel Graphics Installer, all goes well until the "Installing packages..." step, when I get the following error messages:

"Error running transaction: GDBus.Error:org.debian.apt.TransactionFailed: error-no-package: Package linux-headers-3.17.4-031704-generic isn't available" (see screenshot #2)

and then

"Package linux-headers-3.17.4-031704-generic isn't available" (see screenshot #3)

I'm afraid of screwing up my computer any further. I really need this dual monitor setup to work.

Any ideas? Thanks in advance!

---

### Post by dino99 on 2015-03-22
'kernel' is in fact several packages: 2 headers + 2 images
but 3.17 is not a supported kernel (transitional one)  [https://launchpad.net/ubuntu/+source/linux](https://launchpad.net/ubuntu/+source/linux)

you can dist-upgrade to 'vivid' to get the 3.19 kernel: edit /etc/apt/sources.list and change all the 'utopic' by 'vivid' then update & upgrade (disable first third party repo, like ppa if any)

sudo gedit /etc/apt/sources.list

---

### Post by gil-jlem on 2015-03-23
Thanks for the information 9d9!

I entered the sudo gedit /etc/apt/sources.list command into Terminal and it opened up something in my text editor. Can you please see the screenshot below and tell me if it's what I should be seeing?

[ATTACH=CONFIG]260857[/ATTACH]

If so, how do I then update and upgrade? And how do I disable the third-party ppa?

I'm sorry for the confusion - I'm a simple man who needs simple steps. :(

Thanks again for your help!

---

### Post by gordintoronto on 2015-03-23
A VGA splitter does just that: it splits the VGA signal so that two monitors can display the same image. Perhaps a monitor and a projector.

Look at the back of your computer. If there are two video ports, you can achieve what you want. Perhaps there is a VGA port and a DVI port?

---

### Post by gil-jlem on 2015-03-24
Wow gordintoronto - I can't believe I didn't realize that. Thanks a lot for pointing that out!

On the back of my computer I indeed have an HDMI port, so I bought an HDMI-VGA adapter today. Success! Two different displays. I am watching a class as I type this.

Now, do you think I screwed up my computer too badly with all the other stuff?

---

### Post by gordintoronto on 2015-03-25
If it's not broken, don't fix it!

---

