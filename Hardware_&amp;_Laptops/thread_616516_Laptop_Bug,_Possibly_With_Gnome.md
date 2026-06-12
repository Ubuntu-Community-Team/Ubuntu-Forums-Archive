---
title: "Laptop Bug, Possibly With Gnome?"
date: 2007-11-18
forum: Hardware &amp; Laptops
---

### Post by b3n87 on 2007-11-18
Hello, I need help filing, or maybe fixing, a bug.

I recently brought a laptop with a Santa Rosa chipset, which i believe is part of the problem.

Basicly, I couldn't boot the LiveCD or install with the alternative CD when the power plug was plugged in. I had to fully charge the battery then install I could install from the LiveCD fine. 32bit btw.

When I rip a CD, it can rip pretty fast, 12x times speed, when I plug the power cable in it immediatly drops to 1.8x and lower.

The reason I think its Gnome is because I installed the new Mandriva KDE fine, and Sabayon KDE, both fine with no problems.

Any one know anything about this bug, or something I can do to help file the bug report?

Best regards

Ben

---

### Post by scrooge_74 on 2007-11-18
If you don't get a reply file a bug report so developers can look at this issue

---

### Post by buzzmandt on 2007-11-18
try kde ubuntu
sudo apt-get install kubuntu-desktop
then switch to kde session and see if the bug is still present, that will differentiate from kde/gnome or gnome/ubuntu

---

### Post by b3n87 on 2007-11-18
thanks for the quick replise, when i booted the Fedora 8 live CD it failed too boot
and with Ubuntu it kept logging an error in the terminal, Ill write it down and report back the error

Im gonna download a KDE based LiveCD and test that - good reason to tr KDE 4 :D

---

### Post by b3n87 on 2007-11-18
oh yeah anything symptom is that DVD playback becomes extremely jerky and completely unwatchable when the power plug is in. if its running from the battery its fine!

is this something to do wit DMA maybe? as i said running from the battery its fine, so not sure :S

---

### Post by b3n87 on 2007-11-20
I think the bug is with Ubuntu/Kubuntu, they seem to strugle with it the most. with the following error:

SQUASHFS error: sb_bread failed reading block 0x989c1
SQUASHFS error: Unable to read fragment cache block [2626b921]
SQUASHFS error: Unable to read page, block 2626b921, size 4ea7
SQUASHFS error: sb_bread failed reading block 0x989c1

I wrote this done on a notepad and typed it in by hand, so there maybe be a small typo there but I'm sure thats correct.

When the power cable is plugged IN and you boot a liveCD with Ubuntu/Kubuntu then thats the error that I recieve.

Fedora 8 Gnome, doesnt boot the LiveCD
Fedora 8 KDE, does boot fine
Sabayon 3.4e pauses when booting, appears to crash, but then boots fine

I tried open suse 10.3 to but I cant remember the results so I'll try again later.

Can anyone else help me pin point this bug, i want to try and get it reported to get fixed before the LTS is released. These Santa Rosa chipset's are being popular so would be usual :)

Any one have ANY ideas please help.

---

