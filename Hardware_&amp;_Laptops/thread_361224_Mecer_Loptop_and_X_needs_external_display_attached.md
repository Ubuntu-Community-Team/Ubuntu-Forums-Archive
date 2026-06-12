---
title: "Mecer Loptop and X needs external display attached"
date: 2007-02-14
forum: Hardware &amp; Laptops
---

### Post by tobie.de.beer on 2007-02-14
Hi all,

I have a Mecer using the intel i8xx chipset. (N755?? and i845 if I remember correctly)

If I do not attach and external monitor, during startup, the Laptop stops with the Xserver with a blank screen - not enven [crtl][alt][backspace] or [ctrl][alt][del] or [ctrl][alt]F1] gets me out, however ubuntu's login tune still plays. If the an external monitor is attached, I get it all to work with the same stuff on both screens.

{ The TFT screen can do 1400x1050, sofar I got it to 1280x1024, but will try my luck with 9??resolutions. }

Any Ideas How I can get past the: "have to attach an external monitor during start-up" problem?

Thanks
Tobie

P.S. I've googled the poor win200 computer to a standstill....

---

### Post by veloce on 2007-02-15
Sounds like your xorg.conf file is set up for dual monitors in clone mode.  Check the serverlayout section.  

       Option "clone" "on"

Then you should edit it out.  Unfortunately, if you then want two screens to work again you'll have to put it back in.

915resolution is pretty straightforward.

---

### Post by tobie.de.beer on 2007-02-15
I went through all those options (as in the i810 manual) without any luck.

P.S. the ubuntu live CD also needs a monitor attached to be able to start X
(tried Dapper Drake DVD and Edgy all sorts) during text mode installation the screen also just goes at the end of intsalling packeges, but you can get it going again by pressing [ctrl][alt][backspace] but then without any display, Then I reboot after the disk has been silent for about 5 min. 
With a full system I manage to get out of X with [ctrl][alt][F1] then kill gdm and edit xorg.conf with vi and try X with xinit - but the same problem stays: need an external screen connected! for the LCD/TFT to work.
I also tried using the vga driver with the same problems :( 

I'll have to wait for the new intel driver and then check if it functions OK.

There is some options where you conect resistors to the VGA port but that only gives me 640x480 ( a very small screen in the middle of my 1400x1050 screen )

I got the proper info for the System: Mecer N755II8 with i82845G and P4 2.8GHz 1GB Ram

I had to revert back to windoze 2slowK.

T

---

### Post by veloce on 2007-02-15
Yep, that's weird behaviour.

The only other thing I can think of is, have you tried using the laptop's key combination to switch what screens are operating?  Or better yet, what is your bios' default screen configuration?  Can it be changed?

The fact that the behaviour is observed with the Live CD suggests hardware not drivers to me.

(Clutching at straws to try and prevent another person slipping back to windoze!)

---

### Post by lamalex on 2007-02-15
i believe that's part of X. I think they're fixing that in X.org version 7.2 but don't quote me on it. In order to do dual monitor in linux you must boot with it plugged in, hotswapping monitors doesn't work with the current version of X. .. I think. I hope I'm not making an *** of myself but I'm pretty sure I've read this before.

---

### Post by veloce on 2007-02-15
But this person's problem appears to be that dual (clone) monitors** is **working and he wants it to stop!  I **suspect** the bios defaults to clone mode, windows copes with this but Ubuntu doesn't.  As I understand it, when the live CD is booted, it goes straight into dual head clone mode. I can get this behaviour on my laptop by using the Fn+F8 key.

---

### Post by tobie.de.beer on 2007-02-16
Unfortunately the bios gives you almost no features :-( - maybe I must try to update that.

The problem is not that the deul monitor does work - that is fine, but I need to be able to use the laptop WITHOUT the second screen ATTACHED evertime I start-up! 

Using the [Fn][F?] key for the swapping of screens also does not help/work :-(

---

### Post by tobie.de.beer on 2008-03-16
I totally forgot to report on this issue.

I eventually got it all sorted by removing all modlines in the Xorg.conf file.

My wife is using the laptop now in her business - XP :-(

tobie

---

