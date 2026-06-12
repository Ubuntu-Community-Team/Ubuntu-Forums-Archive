---
title: "Error while updating."
date: 2009-01-26
forum: Installation &amp; Upgrades
---

### Post by Karnigan on 2009-01-26
I have a Dell Inspiron Mini 9 which came preloaded with Ubuntu. I've some experience with older distributions of RedHat, but in general my Linux-based experience (and knowledge, obviously) is quite limited.

I've recently begun using the mini as a wireless gateway, essentially. I found a post on these forums illustrating how to, via the terminal, take the incoming wireless signal and share it to the wired NIC device (which I have connected to my PC). It's worked pretty well, although it's been somewhat flaky (e.g. upon restarting, I've always had to go through the series of commands to get the sharing to work properly.)

I'm getting off topic, though.

The auto-updater notified me I had updates to download. To avoid the whole restart/reprogram sequence to have the internet sharing work, I put off the download for about a week. When I finally got around to it, oh boy- world of hurt.

The update downloaded just fine. Upon installation, however, it locked up the computer. I rebooted it and it sat at a screen with a flashing "_" for about five minutes, then continued to successfully load into the operating system. I had no USB or touchpad mouse functionality. After messing with a few key commands I navigated my way to the mouse properties, checked and unchecked a few boxes, and the mouse came back (touchpad, not USB). I proceeded to attempt and finish the update, figured I'd troubleshoot the mouse thing later.

It froze again during the update in around the same spot. After letting it sit for quite a long time to be sure it was actually frozen and not just lagged/bogged down, I held down the power button and forced a shutdown. Upon reboot, it loads into the default tan/brown/whatever background with a mouse cursor and absolutely nothing else. It will sit at this screen for about forty-five minutes, then go into sleep mode. Oh- interestingly enough, the USB mouse works at this point. If I try to use the Ctrl+Alt+F-key command to access the terminal, it locks completely and I have to force a shutdown. Upon hitting the power button from this screen, something interesting happens. It drops the colored background and goes to the black screen with white text, and says the following:

Initializing IP Masquerading.. done.
Initializing IP Masquerading kernel modules.. done.

Then it powers down.

I'm inclined to believe that something to do with my internet sharing (as it modified ipmasq settings) is causing this to lock on bootup and somehow keeping the GUI from loading.

I've tried to mess with various BIOS settings, enabling/disabling network devices, etc, hoping for something, but this was to no avail. I also booted into the diagnostics mode, but that only checks hardware functionality, and everything is A-OK.

I have a Ubuntu disc that came with it, but there's one problem with that- it's a mini, so it has no drives aside from the solid-state hard disk. I fear I may be forced into finding/buying a USB CD drive.

I cannot, for the life of me, figure out how to just boot into some sort of terminal.

Please bestow your wisdom upon me!

Oh, lastly, my apologies if this isn't in the right place. First timer here.

p.s., system specs might be useful.

Netbook model: Dell Inspiron Mini 9
Product Name: Inspiron 910
CPU: 1600MHz Intel Atom CPU N270
CPU Cache Size: 512KB
Memory: 1024mb DDR (400mhz)
HDD: 4GB solid-state STEC ATA DISK vs020.1.0(PM)

---

### Post by Karnigan on 2009-01-26
Okay, I managed to get to the terminal from that screen by hitting Ctrl+Alt+F1 - it locked up the first time, but now it's solid. I've logged into sudo (sudo -s) as I've read just using "sudo" at the beginning of every command for some reason doesn't always do the trick.

Upon typing the suggested "dpkg --configure -a" it feeds me this info:

Setting up gdm (2.20.7-0ubuntu1.1netbook3belmont2) ...
[flashing underscore]

And it just sits there. For ages. I even tried going back through the whole setup w/ the ip masquerading and whatnot, just to see if it did anything. It did not.

I'm baffled :-/

Edit: I exercised a little patience after entering the "dpkg --configure -a" command and it finally handled things on its own. It still had some sort of error with updating some games, but when I got it loaded back into the GUI and let it finish the update, everything worked out. Maybe I just needed to write it out, haha.

---

