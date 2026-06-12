---
title: "How to maintain Ubuntu on an off-the-net machine?"
date: 2005-12-17
forum: Installation &amp; Upgrades
---

### Post by Zed on 2005-12-17
Hi all,

I just installed Ubuntu (server only, Breezy installation CD) on my ancient 233 MHz 64M Pentium laptop that ran Windows '95 back in the day. It doesn't have the hardware to get on the net, but it does have a USB port so I can truck large amounts of data to it by external hard drive.

Gathering up a bunch of debs and moving them over once is easy, but, going forward, I'll quickly go insane trying to resolve dependencies.

Is there some way to keep a profile of what the laptop has installed on my desktop so I can, in a reasonable fashion, ask the question: "what exactly do I need to move over (including dependencies)" to install package X? I'd be happy with exactly the functionality of the apt command-line tools if there were a way to get their output as if I was running them on the laptop (and I understand I'd have to keep this theoretical remote profile synced by hand.)

Or is it a better bet to mirror the repositories on a hard drive, and simply add that to the laptop's /etc/apt/sources.list?

Thanks.

---

### Post by cstudent on 2005-12-17
How do you connect to the net? If it's cable or dsl, does your modem has a usb connection? My dsl modem has both ethernet and usb and I've connected old machines without ethernet to the usb port and had things work. These were old machines running 98 that I was fixing for friends. Anyway, just an idea.

---

### Post by Zed on 2005-12-17
No, I don't currently have the hardware to get on the net via USB. And I'd like to get the laptop in a reasonable state for holiday travels, so I'd rather not try to solve that problem right now.

---

