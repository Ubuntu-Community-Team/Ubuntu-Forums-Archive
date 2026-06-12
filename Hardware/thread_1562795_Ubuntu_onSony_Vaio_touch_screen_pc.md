---
title: "Ubuntu onSony Vaio touch screen pc?"
date: 2010-08-28
forum: Hardware
---

### Post by Wtwine on 2010-08-28
Hi

Does anybody have experience with running a Sony Vaio 20.1'' Touch Screen wireless PC (VPC J118FG/B) machine on Ubuntu 10.04?  I am thinking of buying one but don't want to be stuck with a screen that doesn't play nicely with Ubuntu.

Thanks

---

### Post by xannaxprozaxx on 2010-11-28
Hello;
Won't be able to help much, but I'll share my experience.
I just did a fresh install of Ubuntu 10.4 on my brand new vaio j.
During install, the image was barely readable, but just enough to be able to decipher the text and find the "next" button.
I shrunk the C drive, added an NTFS partition "docs" to share files, added 25gigs for buntu and 8gigs for swap.
First login was difficult, Xorg crashed, after messing a bit with the propositions offered to me (I don't remember what I did exactly, but nothing more than clicking in the dialogs that appeared), I finally was able to log in a messy and garbled version of the buntu desktop.
However, after downloading the restricted Nvidia drivers when I got prompted to and restarting, everything went well. I got a really nice image, compiz effects are fast and snappy.
I still don't have sound (but I think it's on the way of being resolved), and I don't have touchscreen (in fact, I stumbled across this thread while looking for a solution to get touchscreen support).
The sound issue is a known bug, you have to update your ALSA drivers; however, I could not find any real info on how to get touchscreen.
So basically, as long as touchscreen is not a killer feature for you, yeah, it works quite well.
[edit] I have been searching and searching for someone to help with the touchscreen feature, to no avail. I think there must be very very few people that get a vaio j with touchscreen and decide to install Buntu on it. Most people wouldn't want to mess with it, so I think we are more or less on our own with this.

---

### Post by xannaxprozaxx on 2012-03-19
One year later, looking for help again about my vaio j, the only thread I find is this one, so here goes...
On boot, press F6, and select "nomodeset".
You will be able to boot a low-res x session fine.
You can proceed to install buntu like you usually do.
On reboot, keep [shift] pressed, to get to the grub menu (if you have dual-boot, you will get the grub menu anyway).
Highlight the first entry, press [e].
Look towards the end, there is a line that says "quiet boot", replace these words with "nomodeset".
[ctrl]-[x] to continue booting.
Change the sources to include canonical partners (any way is fine, "software sources" or editing the file via command-line).
Connect, then update your sources (open a terminal, sudo apt-get update)
Go to System -> Additional Drivers
Install your drivers (note: the first time, it told me I had no proprietary drivers in use, I had to wait 1mn and click again for some reason, then they restricted drivers showed).
It took a very long while to download, I don't know if my connection was being slow, or if the servers were overloaded, or if the file is simply huge. But it eventually downloaded and installed.
Reboot.
All fine!

Touchscreen: work
Sound: work
Keyboard hotkeys: work
Video drivers: work
100% functional ubuntu!

---

