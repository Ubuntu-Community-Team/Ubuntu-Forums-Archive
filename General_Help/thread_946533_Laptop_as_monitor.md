---
title: "Laptop as monitor"
date: 2008-10-13
forum: General Help
---

### Post by emobrad on 2008-10-13
Hey, I've been wondering for a while, I have an old laptop that is starting to become a big plastic brick (harddrive and processor wise), and I was wondering if it would be at all possible to turn that laptop into either another monitor, or have it so that I can use it as my main monitor (so that I can be on my computer late at night without the light from my old CRT monitor waking everyone up). I'm not really willing to crack it open and wire it differently, and I was just wondering if there's some sort of plug I need for it or if I'm just being a hopeless dreamer. Thanks.

---

### Post by krazykookmany on 2008-10-13
//

---

### Post by Sam on 2008-10-13
> Synergy lets you easily share a single mouse and keyboard between multiple computers with different operating systems, each with its own display, without special hardware. It's intended for users with multiple computers on their desk since each system uses its own monitor(s).

Redirecting the mouse and keyboard is as simple as moving the mouse off the edge of your screen. Synergy also merges the clipboards of all the systems into one, allowing cut-and-paste between systems. Furthermore, it synchronizes screen savers so they all start and stop together and, if screen locking is enabled, only one screen requires a password to unlock them all.

[img]http://synergy2.sourceforge.net/images/warp.gif[/img]
[http://synergy2.sourceforge.net/index.html](http://synergy2.sourceforge.net/index.html)

---

### Post by Vryko Lakas on 2008-10-13
Using your laptop as a second monitor should be possible, at least in theory. I've seen a CNet video for doing something similar in Windows/Mac:
[http://cnettv.cnet.com/9742-1_53-50002302.html]("http://cnettv.cnet.com/9742-1_53-50002302.html")
Wouldn't know how to execute it in Ubuntu, though.

*edit* Or you might could just use Synergy like Sam suggested.

---

### Post by emobrad on 2008-10-13
Thanks, I'll give synergy a try for sure and if that doesn't work then I'll try something else. Thanks guys!

---

### Post by niteshifter on 2008-10-13
Hi,

What you wish to do is not easily done. Not at all possible by simple plugging about - it's an intermediate to advanced (skill level) hardware hack.

However, don't give up on that old hardware: Install a Linux distro on it!

You might be surprised at what will run. Like you I have a plastic brick that I got to wondering about: Toshiba Satellite 4005CDS, 233Mhz Pentium II, 4GB hard disk, CDROM and floppy drive combo, 64MB of RAM. Has a Netgear PCMIA network card. Pretty puny by today's standards. So I (being on vacation) took a couple of days -  and since according to it's Win98 installation it's been 2730 days since last update - maybe I should update ;)

Tried a couple of different distros but problems with CD media meant a floppy boot  / network sourced install was needed. So after about an hour (with a broadband connection) the old clunker is now running Debian Etch with a standard installation. Which went by-the-numbers-no-hitches OK.

What will I do with it? As is - console only (no GUI) - I have a backup machine (ok, another backup machine) to look up and download files with. Maybe up the RAM (to a whopping 160MB!) and give Fluxbox a whirl. Maybe use it as a temporary / test server ... lot's of things to ponder!

---

### Post by KeyserSoze93 on 2008-10-15
Does the laptop run an OS at all? If so, you could set the laptop up as an xdmcp client, and run a near full speed session of the main box, displayed on the laptop. This is not preserve your session like vnc, but it will be a lot faster and allow you to set the resolution etc. on the client.

Of course, if the laptop won't boot at all then this is a bad solution, but I don't believe the client needs to be at all high powered to act as an x client.

---

