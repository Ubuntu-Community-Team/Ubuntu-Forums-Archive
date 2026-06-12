---
title: "Help booting from &quot;Mass Storage Device&quot;"
date: 2008-12-03
forum: Installation &amp; Upgrades
---

### Post by dshosu on 2008-12-03
Hey everyone I was wondering if there's a kind soul(s) out there who can help me figure out how to get my ubuntu on.

Here's the situation:

What I'm trying to do is install a bootable ubuntu on my Windows Mobile cell phone, used a 'mass storage device'. For those not familiar with this feature: It allows the user to choose type of USB connection my phone makes (ActiveSync, Modem, or Mass Storage) from the phone. So I can connect it to any computer via USB cable and use it as a 'mass storage device' (AKA: USB drive). So when I read you could install ubuntu on a USB drive...
via Live CD - [link]("http://www.pendrivelinux.com/2008/11/01/ubuntu-810-install-using-the-built-in-usb-installer/")
via Windows - [link]("http://www.pendrivelinux.com/2008/11/04/live-ubuntu-810-usb-persistent-install-windows/")

...I thought I'd give it a shot..alas it is not working as planned.

Here's the situation:
I've installed ubunto to my USB drive via Live CD AND Windows and so far had the same results.

Every time I boot my computer from the USB though it just hangs on the very first boot screen (HP, press ESC for boot options). I try pressing ESC and nothing happens it just stops.

This made me think that my computer won't boot from USB so I unplug the USB drive, boot normally, press ESC, enter BIOS, check boot order (1. USB, 2. CD, 3. Hard Drive), so I now I'm lost.

I have a HP tx2000 (tx2510us to be exact) and the phone I'm using is a Blackjack 2 (SGH-i617) running WM 6.1 Standard with a 4GB MicroSD card in it, if that helps. 

Much thanks in advance!

---

### Post by Nebutron on 2008-12-03
Interesting.  I am having a similar difficulty with my live usb installation on a regular USB drive.  In my case, I found that when I used my laptop (HP) to install the live image to USB, it worked fine on that machine, but would not work on my home desktop.  Just wouln't be recognized at boot.  That's the part that is similar to your situation. I also noticed that if I did the installation while booted to my regular HD, the image would not work at all.  If you did not do your install while booted to the CD, you may want to give that a shot.

---

### Post by dshosu on 2008-12-03
update.

Ok so using a boot cd that forced my computer to boot from USB I got the ubuntu loading screen (loading bar). Maybe Nebutron you could try this to solve your problem, or at least determine where the problem lies.? After several minutes I got this:

Which makes me think it's a problem with the flash drive? But I don't know where to begin with that...

[IMG]http://oregonstate.edu/~hewlettd/ubuntu/PIC-0003.jpg[/IMG]

---

### Post by Nebutron on 2008-12-03
Not sure what to make of those I/O errors on the flash drive.  It might be worth wiping it cleand and reformatting prior to doing your install.  Perhaps someone more knowledgeable about this than I can give you a more definitive answer.

---

