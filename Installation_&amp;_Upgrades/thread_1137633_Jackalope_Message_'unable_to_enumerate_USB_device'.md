---
title: "Jackalope: Message 'unable to enumerate USB device' spammed repeatedly."
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by Tillanz on 2009-04-25
During startup, the message

[ linearly increasing number e.g. 85.023546] hub 1-0:1.0: unable to enumerate USB device on port 8

appears several times.

I am able to continue to the GNOME Desktop normally, and my system is essentially functional - my USB keyboard and mouse work fine.

However, if I press Ctrl+Alt+F1 to return to the command line I find this message continues to appear, making that form of accessing the command line practically useless.  

Is there a way to disable these messages?

---

### Post by Bearly Able on 2009-05-15
I had the same message (with port 4) when I booted into Jackalope the first time, after upgrading a week ago.  I'm guessing the device in question is an internal card reader, which I know to be faulty.  I've not been aware of it occurring again until now.  

I'm trying to reboot after a problem with the GUI.  The boot screen started normally, a message appeared saying it was checking the hard drive because of an unclean shut-down, and after a few seconds it started to do this.  I waited, because on the previous occasion it booted fine after a few minutes, but it's now been over an hour and it's showing no sign of stopping.  (I'm now using my laptop.)  As I have idea what is happening or why, I'm at a loss as to what to do next.

Any help from someone more knowledgeable would be greatly appreciated!  Thanks.

---

### Post by Bearly Able on 2009-05-16
OK, I finally stumbled upon this command ```
lsusb
```elsewhere in the forums, which let me check my USB ports.  This confirmed that it is the card reader causing the error, and physically disconnecting it has stopped the messages and allowed me to load Ubuntu.  If there's any other way, I didn't manage to find it.

---

