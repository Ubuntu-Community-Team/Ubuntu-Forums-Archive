---
title: "[SOLVED] Upgrade or replace hardware?"
date: 2007-08-07
forum: Hardware &amp; Laptops
---

### Post by m9ke on 2007-08-07
Edit:  marking solved.  Upgrades in progress.

I was given an old PC (384 MB PC 100 or PC133 RAM); 50GB IDE HD.  It was a perfect sand box to start playing with Ubuntu, and it's worked out great.

The logic board on this PC is very old. It's a K7SEM.  Full specs here: [http://www.klondike.ru/spec/MotherBoards/EliteGroup/SocketA/k7sem.htm](http://www.klondike.ru/spec/MotherBoards/EliteGroup/SocketA/k7sem.htm)

I have installed Feisty.  Net access via wired enet is good, email works, IM works. And I have a USB 2.0 board for it, which I have not yet installed but is supposed to work with Linux.

I'd be interested in opinions about whether it would be better to buy another box, or to spend the $250 or so at Newegg to upgrade to 1GB RAM and 500 GB HD.

If I am going to use this as my main computer, it will need to run the apps bundled with Fiesty, plus SlimServer, a music server requiring very little resources supporting a wireless music player called a Squeezebox.

Also it needs to have storage for my docs (minimal) *and* 200-300 CDs which I have digitized in FLAC format.  I have a 500 GB USB disk formatted for Windows which now holds my music, but maybe it's better to have the tunes on an internal drive, allowing me to use the other big drive for back up.

I have looked around and for 400 bucks or so I can get a newer (used) computer which supports faster SATA drives and probably has a faster main bus.

Thoughts?

---

### Post by dasunst3r on 2007-08-07
If a home server is what you would like to build, you might want to consider Debian.  Opt out of a desktop environment and you will have a lean, mean server on your hands.  After installation, just install Samba, sshd, and webmin and you will be well off.

---

### Post by m9ke on 2007-08-07
Thanks for your quick reply.  Actually the main job of this machine is a desktop.  SlimServer is very lean and runs fine on my Windows laptop.

---

### Post by logos34 on 2007-08-07
I'm all for teaching old hardware new tricks and that board sounds antiquated but on closer inspection it's not all that bad.  Onboard video is only 16-bit though, and probably only supports 8MB frame buffer max.  Realistically 16-32MB should be your min.  You could always bargain hunt for an older 4xAGP card (might even find one with s-video/tv-out to boot).  Let's see, you already have an upgrade usb2.0 card to add.  Sounds like it has two sticks of ram--one 256 + 128 MB pc100 or 133.  You know, linux doesn't need a lot of memory, and you could take out the smaller ram stick and put in a 512MB to bring it up to 768MB.  Only about $60 for that (Newegg).  As for the drive, I saw a 500GB IDE Maxtor just the other day at Fry's for $99.  So for suprisingly little you could upgrade.

On the other hand, if the power supply in this thing is at least 250W you could get a NEW board with integrated graphics, processor (AMD) and a gig of ram for around $250, and use the same case, power supply and optical drive.  But that still leaves the new drive.

Basically I guess it comes down to whether you want to sink a little cash into some extra ram and maybe video card for an aging system (which will get you by for the time being), or a little more on new core components, or still more for a newer (used) box.

---

### Post by m9ke on 2007-08-07
Thank you for a thoughful reply logos34.  I appreciate your pointing out the issue with the onboard video.  This box runs fine on the existing RAM, so on reflection 768 MB would be fine, most likely.

I always use Newegg as my baseline for pricing stuff.  If I could really get a 500 GB drive for a hundred bucks I could still be under what I thought I'd spend for the drive and RAM even if I added a video card.  I will search around the forums and try to figure out a couple of cards that are known to work with Ubuntu and keep an eye out.

Thanks again for your help.
m9ke

---

