---
title: "Screen blinks in 9.10 on MSI Wind U123"
date: 2010-02-27
forum: Hardware
---

### Post by crlang13 on 2010-02-27
Hey,

I've been trying to solve this problem for ages - been searching all over for a solution.

When I first boot up, the brightness indicator applet comes up in the top right of the screen, saying the screen brightness is at about 50%.  It then flickers back and forth between 50 and 60% for up to a minute.  Both the applet reading and the screen do this.

If, after the initial flicker stops, I try to adjust the brightness, it does it again!

Any ideas?

---

### Post by exup35 on 2010-02-27
is this when the netbook is on mains power or just the battery?

---

### Post by crlang13 on 2010-02-27
generally both, but it generally lasts longer on battery.

---

### Post by kstella on 2010-02-28
This problem has been around for a while; it's even been in the release notes for months.

[http://www.ubuntu.com/getubuntu/releasenotes/910#Brightness%20flickering%20on%20MSI%20Wind%20netbooks%20with%20KMS](http://www.ubuntu.com/getubuntu/releasenotes/910#Brightness%20flickering%20on%20MSI%20Wind%20netbooks%20with%20KMS)

I really hope we don't have to wait till Lucid comes out before they fix this. :/

One trick that works for me is holding down the right-click button on the desktop for a few seconds; for some reason, that makes it go away faster. When someone else suggested it, I thought it was ridiculous, but it actually worked.

---

### Post by crlang13 on 2010-02-28
> **kstella said:**
> This problem has been around for a while; it's even been in the release notes for months.


I've noticed.  I've been doing some research on fixing the problem.

It looks like you can solve the problem if you update the bios.  This would be easy except MSI only offers the easy way through Internet Explorer on Windows... YAY!

It's gets a little bit trickier if you don't have windows (like me)... You need to make a bootable usb with free dos and go from there.  I was going to give it a go today, I just need to pick up a spare USB.

I'll report later.

---

### Post by crlang13 on 2010-02-28
IT'S FIXED!

I updated the bios which was a bit of a pain, but totally not a problem.

To anyone who is following this thread, check out: [http://jamsubuntu.blogspot.com/2008/12/upgrading-msi-wind-to-10a-bios.html](http://jamsubuntu.blogspot.com/2008/12/upgrading-msi-wind-to-10a-bios.html)

It's a bit dated.  Instead of making a new partition, I made a bootable USB with freedos on in.  I then threw the bios stuff on there.

The blog also says to shut down, unplug and leave it for about 20 seconds.  Reboot, press del, etc.  I sort of forgot to do that...  but still worked.

---

### Post by saleminkb on 2010-03-27
I'm having an issue doing this, I have the live usb of Freedos, with the bios files, but when I try to run it in freedos it gives me the error, "ERROR: This program must be run in MS-DOS mode". I use UNetBootIn to create the live usb, did you do something else?

---

### Post by saleminkb on 2010-03-27
Never mind it works, I just didn't have the AC Adapter plugged in.

---

