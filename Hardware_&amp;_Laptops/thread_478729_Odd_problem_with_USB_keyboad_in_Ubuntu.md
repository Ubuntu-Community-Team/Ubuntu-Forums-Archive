---
title: "Odd problem with USB keyboad in Ubuntu"
date: 2007-06-19
forum: Hardware &amp; Laptops
---

### Post by Platypi007 on 2007-06-19
I have just recently switched to Ubuntu (I would have been switched nearly a month ago but my old laptop died while I was installing it...  Odd coincidence.

Now I have a new Acer with issues.  The issues include having Windows Vista preinstalled and having the Atheros AR5007EG wifi card.  Windows Vista is always an issue and apparently the only way to get the net card working at the moment is NDISWrapper (I'm still working on this one).

The issue for this post, however, is different.  And seems odd to me.  But perhaps someone can shed some light on the matter for me.

I hate laptop keyboards and use a USB keyboard for most of my work. I keep it plugged into a small unpowered hub with my mouse and printer so that I only have to unplug one cable when I go on the road.  The computer recognizes the keyboard before boot, and I can use the keyboard to log in to Ubuntu.  However, once it is done loading the keyboard no longer works.  

If I plug the keyboard directly into one of the USB ports on the laptop it works fine the whole time.  Why would it stop working after everything loads when I was able to use it to log in?  (I'm running 7.04)

---

### Post by coffeecat on 2007-06-19
> **Platypi007 said:**
> I have just recently switched to Ubuntu (I would have been switched nearly a month ago but my old laptop died while I was installing it...  Odd coincidence.

It wasn't trying to tell you something was it? :lol:

However - this keyboard business is odd. When you first switch on it's the bios that's recognising the keyboard, but when you get to the login screen, the xserver has already started so it really ought to continue to recognise the keyboard after the gnome (?kde) desktop has loaded.

I'm wondering if it's a voltage issue. Plugged directly in it's OK, but the hub is unpowered. Perhaps it gets just enough juice from the computer's usb port at login time but for some reason this drops below a threshold after the desktop starts up. Have you got a power supply for the hub or can you borrow a powered hub to try out?

---

### Post by Platypi007 on 2007-06-20
Perhaps after everything loads the printer is drawing enough power to prevent the keyboard from working?  Not sure why that would be since the printer has it's own power but...  when I get home and after I have got Ubuntu booting at ALL (Apparently something I did last night is preventing it from loading... all I can figure that I changed was installing NDISWrapper...  I'll get that figured out sometime) I can unplug the printer from the hub and see if that works.  I don't have a power adapter for the hub.

It just confuses me why it would work at the login screen and then stop working.  It works in Vista, and worked on the old laptop in XP that way, and of course with the BIOS it works.  It is a mystery to me...  Not a major issue since it works in a port, just very, very strange.

Of course right now I can't get into ubuntu at all so it doesn't matter.  Haha!

---

### Post by Platypi007 on 2007-06-20
well...  The keyboard works once everything is loaded up, with the mouse and printer still plugged into the hub...  However sometimes it stops responding and I must unplug it and plug it back in to get it to work again...

Any idea why it would stop responding?  Is there something I should check when it is not responding that would perhaps shed some light on what is going on?  Thus far I have seen no pattern as to when it stops working.

---

