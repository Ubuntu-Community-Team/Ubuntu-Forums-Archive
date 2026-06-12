---
title: "Easy: How do I start LXDE?"
date: 2009-09-15
forum: Installation &amp; Upgrades
---

### Post by clevertomato on 2009-09-15
Just installed base system using alternate cd. Ran update, safe-upgrade, and full-upgrade. installed --without-recommends lxde. try to start it with startx. I'm told it's not installed but to get it I install xinit. So I do aptitude install xinit. Ok. Still can't start lxde. I mean HOW do I start lxde? Man, this shouldn't be so difficult.

---

### Post by earthpigg on 2009-09-15
sounds like you need a [display manager]("http://en.wikipedia.org/wiki/Display_manager") to make life easy on yourself. gdm is the most popular, and will automatically detect what window managers and desktop enviornments you have installed.

> sudo apt-get install gdm

reboot.

[here]("http://sites.google.com/site/masonux/home/notes-to-myself#TOC-Initial-System-Setup") is how i install an LXDE system.

if you do not want any display manager, let us know and we can walk you through the hard/awkward way.

---

### Post by clevertomato on 2009-09-15
Thanks for the reply.

Here's my goal and maybe you can advise me more. I recently installed full-blown Ubuntu 9.04 on a newish PC to learn my way around linux (a little). Then I thought it'd be fun to get a "lite" version going on my old P II 266 with 256 MB of RAM. I wanted to stick with the same distro instead of learning two different linux systems. I heard about Lubuntu, but then realized it's not out yet. Then I heard about U-lite, but for some reason can't get it installed. So, I thought I'd try installing a base command-line ubuntu system and put lxde on it. I know nothing about Masonux. All I really want is a relatively beginner-friendly ubuntu-based linux to play with on this ancient PC. Ubuntu + lxde seems like the way to go (i.e. what Lubuntu promises to be), but getting that done is proving to be incredibly difficult for me so far. Should I check out Masonux?

BTW, I'm an experienced "power user" of Windows, but just a beginner with linux.

Shawn

---

### Post by clevertomato on 2009-09-15
CTM, Thanks again for the reply. Because of your link, I read about Masonux. It sounds like exactly what I'm looking for. Hopefully I'll have more success at installing it than what I've had so far with base Ubuntu + lxde or U-lite. On the one hand, it's just an old slow PC that I want to play with so it's not important in any way. On the other hand, for crying out loud, a guy ought to be able to get SOME linux install working decently on an old PC, even just for playing with. Here I go to give it a shot...

---

### Post by earthpigg on 2009-09-16
best of luck, & let me know what you think :D

it uses the same installers as full-blown ubuntu, so if you could/couldn't get that to work then masonux will be the same.

---

### Post by clevertomato on 2009-09-16
Darn. It's not working. I'm getting same thing I've seen before with some previous attempts at installing U-lite or booting into live CD of Lubuntu. It boots, then tries to go into the GUI but freezes with an all black screen and little white clock or watch-looking icon in the center. Totally frozen then.

What I did: I already had a working command-line install going so I didn't want to wait for the actual masonux download. I followed all relevant steps on the "Notes to Myself" page (except I used aptitude instead of apt-get, which as far as I know shouldn't be a problem).

My system: Asus P2L97 motherboard, Intel Pentium II 266 Mhz with 256 MB RAM, my original display adapter was Diamond Viper V330 with Riva 128 but it caused problems so I replaced it with a Raven AGP by Quantum3D (3dfx), Adaptec 2940UW with 9 GB IBM SCSI hd, 3com 3c905c-TX NIC.

Did I mention before all this LXDE stuff I successfully installed the regular Ubuntu Jaunty on this same old PC and it all worked fine--it was SLOW as molasses, but everything worked fine. I sure hope someone can give me a clue or help walk me through solving this. I've really gotten my hopes up for trying to make the switch from Windows to Ubuntu on my current PC and would like to be able to use this old PC with a lighter and faster Ubuntu to help me get up to speed.

Shawn

---

### Post by clevertomato on 2009-09-16
Update: Earlier I had to switch from Diamond Viper V330 to Raven AGP (3dfx) to be able to see all the screen in command-line only. Now with the window manager stuff installed and trying to start automatically (but failing) I switched back to the Diamond Viper V330. It's a crappier card, but the system loaded with it. Problem is as soon as I get into LXDE, I get: "The NetworkManager applet could not find some required resources. It cannot continue." So I have no network connection. It'd be nice to get nm working, but if I cannot, I at least need network connectivity somehow. I had it in command-line mode. This old PC will only ever have the wired NIC in it. How can I get network connectivity working in LXDE now?

...and does anyone have any ideas of why LXDE isn't working with my Raven AGP display adapter or how I could get it to? Gnome worked with it when I install full-blown Ubuntu 9.04.

Shawn

---

### Post by earthpigg on 2009-09-16
hi,

nm-applet is set up to only run in gnome and xfce by default. you can either blame the devs of NetworkManager or the package maintainer at Debian or Ubuntu for that. either way, its easy to fix.

[source]("http://sites.google.com/site/masonux/home/notes-to-myself"): 
> 
sed -i 's/OnlyShowIn/#OnlyShowIn/g' /etc/xdg/autostart/nm-applet.desktop 

will comment out the OnlyShownIn line of /etc/xdg/autostart/nm-applet.desktop to allow nm-applet to function outside of gnome and xfce. if you dont trust my command, you can add the "#" yourself:

> sudo leafpad /etc/xdg/autostart/nm-applet.desktop

---

### Post by RTrev on 2009-11-03
> **shawnboy said:**
> Just installed base system using alternate cd. Ran update, safe-upgrade, and full-upgrade. installed --without-recommends lxde. try to start it with startx. I'm told it's not installed but to get it I install xinit. So I do aptitude install xinit. Ok. Still can't start lxde. I mean HOW do I start lxde? Man, this shouldn't be so difficult.

Install xorg.  Then I believe startx will begin working.

---

