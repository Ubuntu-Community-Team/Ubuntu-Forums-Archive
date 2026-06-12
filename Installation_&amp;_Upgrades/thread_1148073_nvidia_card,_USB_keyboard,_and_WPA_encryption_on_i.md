---
title: "nvidia card, USB keyboard, and WPA encryption on install"
date: 2009-05-04
forum: Installation &amp; Upgrades
---

### Post by clanmackay on 2009-05-04
OK, deep breath.  One, two, three.

I am trying to install Intrepid on a hand-me-down box.  The only network connection I have rights to is wireless and WPA-encrypted, and I have no access to change its settings.  The only video card in the box is nvidia, which, as far as I understand, is unsupported in the native install for political reasons.

My first bit of fun was trying to install off the Intrepid CD.  I had a USB keyboard.  This keyboard works to change BIOS settings, and works at command prompts, but does nothing in the installation disk menu -- the point at which I would choose to install the OS.  OK.  Find a PS/2 keyboard. Got it.

Now I try to install again, with the PS/2 keyboard.  I get the animation of Ubuntu loading, then, rather than the graphical installer, I get dumped to a command prompt.  No problem, I've worked with command prompts all my life, and this is probably due to the nvidia kerfluffle.  Now all I have to do is use apt-get to search the non-free repository (?) and get the nvidia driver.  However: I cannot get my USB wifi adapter to connect to the base station because, apparently, there is no native support for WPA in iwconfig.  OK, well at least I can get the video working.  I drive to a friend's house, download the nvidia installer from their site, put in on a flash drive, and go home.

The installer runs, but it is not compiled to handle my video card.  It very helpfully tries to download a version that matches.  This, of course, fails.  So it then tries to compile a version for me from scratch, but this fails, for one of a number of reasons, such as not having the kernel headers, not having the right version of gcc, or something.

So, now it is imperative to get networking running.  Browsing the web on my Kindle, I find a very useful installation guide, universally praised, that basically amounts to two steps.  One, use apt-get to get a graphical network management tool.  Two, use this network management tool.

OK, breathe again.

*If apt-get would work, then my networking would be working*.  And even if I got this graphical networking tool and put it on my flash drive, *I still couldn't run it, as I cannot start X*.

I delved deeper and found wpa_supplicant, generated a passkey from the ASCII password for the network, set up a wpa_supplicant.conf file (all the while transcribing from the screen of my Kindle), but after an hour I couldn't get it working.  I have now driven back to my friend's house, where there is a Windows machine, on which I am currently typing.

**What now?** 

Thank you ever so much in advance.

---

### Post by clanmackay on 2009-05-06
I am really rather at my wit's end.  Do those here think that it is the case that if I get the nvidia driver running, that I will be able to go into the native X installation and connect to the WPA-encrypted network that way?  I know I wrote a long, frustrated post originally, but I do hope that someone is able to assist me.

Thanks again.

---

