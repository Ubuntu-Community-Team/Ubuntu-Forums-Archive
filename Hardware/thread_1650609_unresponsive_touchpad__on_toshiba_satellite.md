---
title: "unresponsive touchpad  on toshiba satellite"
date: 2010-12-21
forum: Hardware
---

### Post by the jaq on 2010-12-21
I recently installed 10.10 on a toshiba satellite a105-s2712, which
has seen one nightmare after another. It is of the same era as a higher end
toshiba  that I have been using with ubuntu (without much trouble)
since 4.1. Due to other failures I installed the O/S from a netboot.
This method did not install gui (maybe I overlooked an option) so I sudo
apt-get install ubuntu-desktop, which brings me here:

The touch pad is unresponsive (but there is a cursor) at login screen
and desktop. An external mouse works fine.

"xinput list" shows the SynPS/2 Synaptics TouchPad device.
"xinput -list-props ID" says the device is enabled
"xinput test ID" is unresponsive to all movements and clicks.

I can't find any similar issues on the boards. Any suggestions? Thanks in advance

---

### Post by the jaq on 2010-12-22
I forgot about the wonderland of magic solutions where you wake up the next day and things magically work

I did append /etc/default/grub as done [here]("http://ubuntuforums.org/showthread.php?t=1565548&highlight=vaio+touch+pad"), but I am sceptical this changed anything. I will revert these changes and report back later.
[URL="http://ubuntuforums.org/showthread.php?t=1565548&highlight=vaio+touch+pad"]
[/URL]

---

