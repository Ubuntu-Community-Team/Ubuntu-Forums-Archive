---
title: "Upgrade to 8.10 gives blank screen &amp; no response"
date: 2008-12-29
forum: Installation &amp; Upgrades
---

### Post by Sour Mash on 2008-12-29
I was running 8.04, it was OK but I couldn't get my wireless to work and an upgrade was suggested.

So I did the upgrade and all was well until reboot time and it's all gone wrong! I have a blank screen, a blinking cursor that I can't type at and the Caps Lock light is flashing. 
Pushing keys does nothing, not even the PrtSc button helps this time (last time I got this blank screen I randomly pushed butons and the only one that did anything was the screen print button - I hadn't got round to investigating this one.

Anyway, I was doing so well and now I'm crushed.

Attempting to see if some Ctrl + Del + something else combo would help I went through all the F keys and nothing, got to Ctrl + Del + B which rebooted.

I can see Grub loading and can hit Esc to get to a menus but I;m a bit lost now.

Any ideas please?

---

### Post by Piviul on 2008-12-29
What's happen if you press ctrl-alt-backspace? you hear X restarting? and if you press ctrl-alt-f1? You can see the shell prompt?

I had the same (?) problem and I think the cause is the bug [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-vga/+bug/308504;](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-vga/+bug/308504;) that's happen because I have a *recent* video ATI (Radeon HD 2400 PRO) and the radeonhd video driver is not in the official ubuntu repository.

The workaround I've found is to add the universe repository to /etc/apt/sources.list and then install xserver-xorg-video-radeonhd package; restarting X solve the problem.

I hope this will help you.

Piviul

---

### Post by Sour Mash on 2008-12-30
Thanks for your reply, I need a little hand holding with your suggestion as I'm very new to Linux. I left the machine overnight with it's blinking cursor and this morning I am presented with the sign on screen for xubuntu. However, the cursor is not flashing and I cannot type in the username box - nothing comes up on the screen. The Caps Lock light is flashing, the mouse pointer is showing but does not move.
The clock shows the time as 05:17 this morning, I left it at about 23:30 last night,

Any ideas what all this means??

Oh and your suggested key combinations do nothing at all :-(

---

### Post by K0sM on 2008-12-30
Ah! thats almost same problem I had, got the blank screen during a clean install. I'm using an old Sony Vaio 808(something..).

Pentium3 256mb ram. 16gigs. Intel videochip (I think).

I tried 8.04 and no problems there. So if I upgrade 8.04 to 8.10 will I be staring at a blank screen aswell?

thanx :)

---

### Post by Sour Mash on 2008-12-30
Based on my experience the answer is yes!

---

### Post by K0sM on 2008-12-30
Cooool,

I'm gonna try it tonight :)

---

### Post by K0sM on 2008-12-31
right, what I did last night was:

download the Xubuntu 8.10  PC (Intel x86) alternate install CD

[http://nl.archive.ubuntu.com/ubuntu-cdimage-xubuntu/releases/8.10/release/xubuntu-8.10-alternate-i386.iso]("http://nl.archive.ubuntu.com/ubuntu-cdimage-xubuntu/releases/8.10/release/xubuntu-8.10-alternate-i386.iso")

Then start installing without the graphics and it worked fine! took a long while though and I thought a few times during the installation process that it stalled. 

It hung during the login page. But thats because the acx111 wireless driver doesn't like my plugin card. fixed that and everything runs fine.

---

### Post by IanB2 on 2009-01-01
I too get the 'blank screen' with a fresh install of xubuntu 8.10. (using the alternate CD on an IBM T22 Thinkpad with 256MB RAM.)

There appears to be no keyboard combination 'alt ctrl F1' etc that will work. The laptop is completely unresponsive.

I'm going back to 8.04

---

### Post by Sour Mash on 2009-01-01
I gave up and reinstalled 8.04, it's a good move because it works :-) I also found that changing the WiFi card sorted out my connection so the only thing stopping me being really happy is the fact that I have to press the Screen Print button to get past that blank screen during boot up!

---

### Post by Matt Gotts on 2009-04-04
I'm so relieved to find that it's not just me having this issue!  I too downloaded the 8.10 cd, installed on an Ergo Preceptor 3 adn after a VERY long install the loading splash screen comes up, then blank.

I'll get 8.04 and go with that - I installed Ubuntu 7.10 from a CD I've got but it's VERY slooowww!

Would be interested if anyone has a fix that doesn't require a masters degree in computing to sort out!:p

---

### Post by Duckrow on 2009-04-12
I have had trouble installing Linux Mint 6 or Ubuntu 8.10 on a Dell GX260. Neither can handle the onboard graphics. I get the blank screen thing but once got an error message;
Ubuntu is running in low graphics mode
(EE) Intel(0): failed to destroy server context
(EE) Intel(0): failed to destroy server context

I can't then click the options of starting like that once, trying something different or finding other settings. It all kind of freezes.

I have googled it but havn't found anything yet.

However, Xubuntu 8.10 works fine. I may try adding Ubuntu desktop but am not clear - would that then be Ubuntu or is Xubuntu base very different?

---

