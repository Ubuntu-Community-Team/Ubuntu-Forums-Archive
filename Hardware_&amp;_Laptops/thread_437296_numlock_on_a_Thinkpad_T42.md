---
title: "numlock on a Thinkpad T42"
date: 2007-05-08
forum: Hardware &amp; Laptops
---

### Post by MikeMLP on 2007-05-08
I may be wrong, since most of the time I use an external keyboard, but I am fairly certain that on edgy, the numlock function on the T42 worked as expected (numlock is invoked by holding shift and pressing scroll lock), but on feisty, numlock does not function.  Instead, I must use a generic usb keyboard to toggle numlock.  Has anyone seen this type of behavior?  Is there a fix?  a setting? (though it seemed like on edgy things 'just worked' as they should) Is there a report on launchpad?

Thanks!

---

### Post by Jingo on 2007-05-10
Same problem. T42.

Solved it by disabling gnome's "remember_numlock_state".
Open up gconf-editor and search for "numlock", and you will see.

---

### Post by Titan3025 on 2007-05-20
I have the same problem with my t43p. I cannot manipulate the numlock LED since the upgrade to feisty. :-(

I also dont find that key in gconf :-( GNOME remembers my numlock state. I think there should be an option in the keyboard settings of GNOME, where each user can choose if he wants GNOME to remember the numlock state or keep it off by default.

I also think there should be a fix for the numlock LED bug introduced in feisty. With dapper everything worked fine on the t43p.

Cheers,
Titan3025

---

### Post by MikeMLP on 2007-05-24
Thank you both.  I will try that.  Unfortunately, in the mean time, my wireless has stopped working on Ubuntu, so I'm in windows most of the time now.  I normally wouldn't bump / cross-post in this way, but since this is a Thinkpad T4x thread, perhaps some of you have experienced a similar problem in the past week or so, possibly related to a recent update.  Here is the URL: 

[http://ubuntuforums.org/showthread.php?t=453956]("http://ubuntuforums.org/showthread.php?t=453956")

And next time I am in Ubuntu, I will definitely try that out, thanks!

edit: linked to this thread in launchpad bug #92482: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-keyboard/+bug/92482]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-keyboard/+bug/92482")

---

### Post by Titan3025 on 2007-10-27
The problem still persists with Gutsy :-(

---

### Post by callmeray on 2008-06-15
> **Titan3025 said:**
> I have the same problem with my t43p. I cannot manipulate the numlock LED since the upgrade to feisty. :-(

I also dont find that key in gconf :-( GNOME remembers my numlock state. I think there should be an option in the keyboard settings of GNOME, where each user can choose if he wants GNOME to remember the numlock state or keep it off by default.

I also think there should be a fix for the numlock LED bug introduced in feisty. With dapper everything worked fine on the t43p.

Cheers,
Titan3025

It's under /desktop/gnome/peripherals/keyboard/remember_numlock_state. Now if I can figure out how to get the indicator LED to work again . . .

---

