---
title: "Getting Nvidia to work in Ubuntu 9.10"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by Delenir on 2009-10-31
I want to use Ubuntu, I really do. But for the past few versions they just do not seem to support my graphics card, an Nvidia Geforce 9100M G. There does not seem to be any easy, or functional way to get this thing to work. Not only can I not use effects, but I can't even get the native resolution on my notebook to show up. I have even tried the Nvidia drivers right from their site and have run into numerous problems like saying I have an X server open (no clue what that even is). I have searched high and low and also could not find any reliable videos or sites with pictures that explains how to get this going. I don't even know if it's supposed to work on this chipset... please help me from having to crawl back to Winblows again :(

---

### Post by Meroveus on 2009-10-31
XServer is what presents the GUI.  Now you know.
If 9.10 boots at all, then do so, and log in.
Open a terminal window, and type:
sudo stop gdm
You will be presented with a black screen, and you'll need to log in again.
This will stop the XServer and allow you to install your video driver using the installation instructions on the nvidia download page.  Follow them all.
Incidentally, I downloaded and installed a new nvidia driver (1.90) and installed it manually today.  it is working (with issues), but the issues are exactly the same as I had with 1.85.
when you're done, reboot.

---

### Post by Delenir on 2010-03-02
I got it to work, months later, thanks :)

---

