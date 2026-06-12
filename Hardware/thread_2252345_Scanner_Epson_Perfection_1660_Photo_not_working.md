---
title: "Scanner Epson Perfection 1660 Photo not working"
date: 2014-11-11
forum: Hardware
---

### Post by 3WrKB4C on 2014-11-11
I installed the scanner using the *.deb drivers provided by Epson. The installation went fine, without any warning or error.
However I cannot scan. I performed various tests:

1) Simple scan starts, and if I try to scan it hangs for sometime, after which in some cases it says the scanner is not reachable, some other times it simply hangs without results.

2) Iscan also produces random outputs; sometimes it does not give any feedback, sometimes it says no scanner is connected. I tried also with sudo iscan, but not change.

3) I installed and tried xsane. It starts and normally it detects two different scanners; when I select the right one, 1660, it hangs.

I also made sure that my account is in the groups "saned" and "scanner", but no change whatsoever.

I'm really starting to get very very frustrated, since ubuntu trusty is not working at all: I spent lots of money for a new fancy notebook and now I have problems with bluetooth, with touchpad and with scanner. I am really committed to linux but enough is enough! :mad:

---

### Post by Pilot6 on 2014-11-11
Which debs did you install?

---

### Post by 3WrKB4C on 2014-11-11
I am running ubuntu 14.04 on an Asus X751LA, with cpu intel i7
I installed:
iscan-data_1.32.0-1_all.deb
iscan_2.30.0-1~usb0.1.ltdl7_amd64.deb

---

### Post by Pilot6 on 2014-11-11
I think I know what's the problem. Try to disable xhci in UEFI (aka BIOS).
Sometimes old scanners behave this way.

---

### Post by pqwoerituytrueiwoq on 2014-11-11
can you run 
```
scanimage -L
```
also try it on a live cd/usb if it does not list anything
i assume this is a usb scanner

some time after ubuntu 10.04 through 14.04 there was a issue with scanimage crashing alot, it was fixed in 14.10, the update can be install on 14.04, here are the debs/installer for them
[https://www.mediafire.com/?iq2s6qaw9y4slcs](https://www.mediafire.com/?iq2s6qaw9y4slcs)

---

### Post by 3WrKB4C on 2014-11-13
Thanks to Pilot6 I solved the problem! The option xhci in uefi (under USB settings) was set to "Smart Auto". I disabled it and the scanner started working perfectly!
Thanks a lot!
Thanks also to [ 						 							]("http://ubuntuforums.org/member.php?u=865458")[**[COLOR=#000000]pqwoerituytrueiwoq[/COLOR]**]("http://ubuntuforums.org/member.php?u=865458") for trying to help.
If I manage, I will set this thread as Solved.

---

