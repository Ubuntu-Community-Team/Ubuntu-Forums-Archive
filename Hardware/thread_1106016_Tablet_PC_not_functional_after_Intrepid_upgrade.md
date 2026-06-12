---
title: "Tablet PC not functional after Intrepid upgrade"
date: 2009-03-25
forum: Hardware
---

### Post by Mark Phelps on 2009-03-25
I just upgraded from Hardy to Intrepid on my tablet PC (Fujitsu 4020) and discovered that virtually NONE of the tablet PC functions work anymore.

I looked into the xorg.conf file and nearly all of the mods I made for Hardy are commented out with the remarks that HAL is used now.

So, I did a search on this forum and got a 47-page list of responses!!  Since I really don't want to have to read through literally hundreds of pages of posts, I'm hoping that someone can point me to something that will provide some guidance on how to migrate the xorg.conf mods into "HAL".

It took me some time to get the Tablet working under Hardy, so I wrote down everything I did.  I've checked and all the packages are there, all the customized files are still there (.xbindkeysrc, .Xmodmap, modified xorg.conf, rotate script) but none of the tablet buttons work anymore, nor does the stylus.

Without the tablet functions, I might as well go back to Hardy.  But I'd like to have a go at getting the stuff working again in Intrepid.

Can anyone help??  

(thanks in advance)

Update: Having read further that xorg.conf is coming BACK into use in 9.04, I took the leap to simply uncomment all the stuff that Intrepid commented out and -- surprise -- nearly everything works now!

Tablet PC buttons don't work but I will be looking into that further.

---

### Post by Favux on 2009-03-25
Hi Mark,

That is the correct way to go about it.  The 10-wacom.fdi file will only give you a functioning stylus through HAL.  You can leave your mouse and Synaptic touchpad commented out.  Keyboard is a little trickier.  I use a single key bound to my rotation method to rotate.  HAL breaks single key keybindings, so you have to leave the keyboard uncommented.  If you don't need that you can leave it commented out.  Be sure those changes are reflected in "ServerLayout" also.

Sounds like you have it handled.

PS:  I use my "Q" key for rotation.  The key code changed from 205 in Hardy to 201 in Intrepid.

---

### Post by Mark Phelps on 2009-03-25
Favux:

Actually, the news isn't as good as it seemed at first. None of the keys on my tablet bezel work at all.  They don't appear to be generating any codes at all! 

How did you find out that the "Q" key code had changed? I tried using "xev" and while it displays something for the keyboard keys, it shows nothing for the bezel keys.  I need to use those keys because when the PC is in "tablet mode", the keyboard is covered.

While the bezel keys are not a showstopper, it's very disappointing to have something that took me a lot of work to figure out how to get working -- suddenly NOT work anymore. 

I'll probably do a restore back to 8.04 to do some checking when it last worked.

---

### Post by Favux on 2009-03-25
Hi Mark,

Make sure you have "hotkey-setup" installed in Synaptic.  What we TX2000 and TX2500 users use is described in the Key code addendum here:

[http://ubuntuforums.org/showthread.php?p=6274392#post6274392]("http://ubuntuforums.org/showthread.php?p=6274392#post6274392")

Don't know how much use it is to you.

---

### Post by Mark Phelps on 2009-03-26
Favux:

Thanks for the link.  It appears that I have hotkey-setup already installed.

However, still don't get any results through xev when I press any of the bezel keys.

Think at this point, I'm going to restore back to Hardy and see what I can find out there.  Given that Jaunty is supposed to be out in Beta today and will be released in a few weeks, might be better to wait for that.

You know if it's possible to skip an upgrade (i.e., Hardy --> Jaunty)?

UPDATE: Restored back to my Hardy setup -- and everything works again!! Now, xev DOES see the Tablet PC bezel keys.  

Since this is a specific problem involving xev, special keys, and Intrepid, I've opened a new thread for that problem.

Since my Hardy setup works OK, I'm sticking with it until the new thread yields some specific fix for Intrepid.

Please post any followon comments to the new thread.

---

