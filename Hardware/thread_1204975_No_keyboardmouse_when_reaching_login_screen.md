---
title: "No keyboard/mouse when reaching login screen"
date: 2009-07-05
forum: Hardware
---

### Post by Roboticexile on 2009-07-05
Hello Ladies and Gentlemen,

I've been running Jaunty on my laptop (Dell Latitude D600) for a couple of months now. I had a couple of hiccups with the wireless which are ongoing, but now I've run up against a huge unrelated hurdle.

I booted this morning, the loading bar was VERY slow to progress, but I waited, after a while I get some messages flying past too fast to read, and the load continues.

Eventually I got to the login screen, the cursor is blinking, but I cannot move the mouse/trackpad, or enter anything via the keyboard. I've been looking at other similar threads, who suggest that keying in Ctrl + Alt + F1 will take me to terminal, after a couple of lines i should be able to solve the problem. This is all fine and dandy, except that Ctrl + Alt +F1 won't work... None of the keys will respond at all! The only thing that works is the power button.

Other solutions I've read about feature making sure the keyboard is enabled in the BIOS. However, the laptop will respond to keyboard input during booting, or if I boot into a live disk. Thus I assume the keyboard and mouse actually work, they simply won't work when I run Ubuntu.

I COULD re-install Ubuntu as a last resort, however there are files I need to take off of the system before hand. I've tried removing the HDD, inserting it into a caddy and reading it on my desktop, however for some reason that comes up a bit odd. It shows my 30Gb drive as a 224Mb one, with no sign of my files, root system etc.

Please help, I'm at my wits end right now!

Thank you =]
Rob:KS

---

### Post by edvar on 2009-09-30
It just happened to me. Hal wasn't loading so I got no mouse, keyboard, sound or network available after I installed an upgrade to kernel 2.28.15.52 in Jaunty.

I tried several things but nothing worked then I realized the folder /etc/hal was empty!

I went to a Linux Mint Gloria VM I had installed on another computer and checked the contents of the folder. The folder structure is basically:

/etc/hal/fdi
/etc/hal/fdi/preprobe
/etc/hal/fdi/policy
/etc/hal/fdi/information

I recreated the folders on my Ubuntu Jaunty box and rebooted. After that I was back in business!

---

