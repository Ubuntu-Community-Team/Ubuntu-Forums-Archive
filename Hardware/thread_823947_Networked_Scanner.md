---
title: "Networked Scanner"
date: 2008-06-09
forum: Hardware
---

### Post by D-Dan on 2008-06-09
Hi folks.

I have two PCs on my lan, both dual booting XP and Ubuntu.

After installing Ubuntu, I set about sharing the resources I want to share, printer, drive, mouse and keyboard (using synergy). I have remote desktop working using vnc (tight vnc on the windows side).

Now I want to share the scanner on PC1 across the network. I know it can be done Linux to Linux using SANE, and I have it working Windows to Windows using remote scan, but I'd also like to get Windows to Linux (ie - the scanner connected to a running windows install shared with the Ubuntu machine).

Ideally, I'd like to see a remotescan client on Ubuntu, though I understand there isn't one yet. So, is there a transparent way to share the scanner from:

Windows to Ubuntu
Windows to Windows
Ubuntu to Windows
Ubuntu to Ubuntu

All using the same package (in much the same way Synergy works across the network regardless of the OS in use on the two machines).

I'm trying to make sharing as transparent as possible, so that it just works.

I'm aware of the Twain/SANE bridge, but that seems to be a one way street and assumes Windows is the client. I need something that will work with all possible configurations.

It's possible I'll be adding a new machine to the network soon, so I'd like to solve this as soon and succinctly as possible.

TIA

Steve

---

