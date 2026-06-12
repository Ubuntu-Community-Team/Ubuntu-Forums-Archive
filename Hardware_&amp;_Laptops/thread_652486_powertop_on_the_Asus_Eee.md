---
title: "powertop on the Asus Eee"
date: 2007-12-28
forum: Hardware &amp; Laptops
---

### Post by ramvi on 2007-12-28
Hi there!

The first thing powertop suggests on the Asus Eee is:
> Suggestion: Enable USB autosuspend by pressing the U key or adding
usbcore.autosuspend=1 to the kernel command line in the grub config

2.
> Suggestion: Disable 'hal' from polling your cdrom with:
hal-disable-polling --device /dev/scd0 'hal' is the component that auto-opens a
window if you plug in a CD but disables SATA power saving from kicking in.

3.
> Suggestion: increase the VM dirty writeback time from 5.00 to 15 seconds with:
  echo 1500 > /proc/sys/vm/dirty_writeback_centisecs
This wakes the disk up less frequenty for background VM activity



1. I've learned, by a bit of googeling, that the first suggestion is actually wrong and won't work
2. What's odd is that I don't have a cdrom in or connected to the Eee.
Hence "sudo hal-disable-polling --device /dev/scd0" returns "Cannot find storage device /dev/scd0."
3. I have tried to open up /proc/sys/vm/dirty_writeback_centisecs, which is an empty file (?), and write in 1500. This is gone the next time I start the computer though. **How can I make this stay?**



So there isn't a lot of power to save from the suggestions, but maybe there's something to fix in the top causes for wakeups?
  62.7% (  inf)       <interrupt> : PS/2 keyboard/mouse/touchpad 
  13.6% (  inf)       firefox-bin : schedule_timeout (process_timeout) 
   6.8% (  inf)       <interrupt> : uhci_hcd:usb4, HDA Intel, i915@pci:0000:00:02.0 
   5.1% (  inf)       <interrupt> : uhci_hcd:usb3, wifi0 
   5.1% (  inf)              Xorg : do_setitimer (it_real_fn) 
   3.4% (  inf)            lastfm : futex_wait (hrtimer_wakeup)

Whoa - 63% wakeups for the keyboard/touchpad! **Is there any fix for this?** Updating synaptic drivers?

---

### Post by kerry_s on 2007-12-28
what are you using? gnome,xfce4,kde,other

3. add that line to /etc/rc.local

can you please make your questions clearer/simple.
as far as i know eeepc uses xandros?-> [http://forums.xandros.com/](http://forums.xandros.com/)

---

### Post by ramvi on 2007-12-29
> **kerry_s said:**
> what are you using? gnome,xfce4,kde,other

3. add that line to /etc/rc.local

can you please make your questions clearer/simple.
as far as i know eeepc uses xandros?-> [http://forums.xandros.com/](http://forums.xandros.com/)

Oh right, sorry. I'm using Ubuntu Gutsy and want to get the most out of my battery.
3. Thanks :)

---

### Post by kerry_s on 2007-12-29
> **ramvi said:**
> Oh right, sorry. I'm using Ubuntu Gutsy and want to get the most out of my battery.
3. Thanks :)

okay with gnome you probably want to trim as much as you can, just like you would if you were using windows. what i would recommend is you create another user, say "battery" and in that setup trim as much as you can, like turning off the wallpaper, turning off automatic updates, maybe move everything to 1 panel. you might even try using 1 of the light weight window managers instead of gnome, there built to use less resources from the get go and you just add what you need. just keep in mine it only uses power if it's running, you want to control whats running to get the most. good luck

---

