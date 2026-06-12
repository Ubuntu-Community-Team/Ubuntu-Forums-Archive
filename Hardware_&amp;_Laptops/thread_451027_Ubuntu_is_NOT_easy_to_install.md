---
title: "Ubuntu is NOT easy to install"
date: 2007-05-21
forum: Hardware &amp; Laptops
---

### Post by machette on 2007-05-21
My HP Presario V1000 hardware list:
[IMG]http://140.134.4.20/~d8825313/hw.jpg[/IMG]

I download Ubuntu 7.04 Desktop version, and burn on CD.

Ubuntu iso file seem to not be the problem, beause I can install that one into VMware by mount iso file
So I try to install Ubuntu Desktop on my Notebook.

Installation Problem:
1. Boot by that CD
2. Select the first option to start to install
3. Wait a long time
4. Show "buffer I/O error on device fd0, logical block 0"
5. Go into yellow desktop, but no anything on the desktop
6. Go into dark
7. That's all

---

### Post by vikramsharma on 2007-05-22
> **machette said:**
> My HP Presario V1000 hardware list:
[IMG]http://140.134.4.20/~d8825313/hw.jpg[/IMG]

I download Ubuntu 7.04 Desktop version, and burn on CD.

Ubuntu iso file seem to not be the problem, beause I can install that one into VMware by mount iso file
So I try to install Ubuntu Desktop on my Notebook.

Installation Problem:
1. Boot by that CD
2. Select the first option to start to install
3. Wait a long time
4. Show "buffer I/O error on device fd0, logical block 0"
5. Go into yellow desktop, but no anything on the desktop
6. Go into dark
7. That's all

I might be wrong but isn't fd0 floppy disk. That might be the reason you are getting the error.

---

### Post by aysiu on 2007-05-22
Read this:
[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/97306](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/97306)

---

### Post by beeryf on 2007-05-22
if you don't have a floppy drive check your bios to see if you're listing one there. if so just tell your bios you don't have one. this is what i had to do for this error to stop.

---

### Post by slimdog360 on 2007-05-22
so you have a problem then all of a sudden that make ubuntu hard to install?

---

### Post by machette on 2007-05-22
> **slimdog360 said:**
> so you have a problem then all of a sudden that make ubuntu hard to install?

Yes, after I turn off the floppy in BIOS

Installation Problem:
1. Boot by that CD
2. Select the first option to start to install
3. Wait a long time
5. Go into yellow desktop
6. A error message from GNOME:

> There was an error starting the GNOME settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include:
the remote application did not send a reply,
the message bus security policy blocked the reply, the reply timeout expired,
or ...

Actually, hard to install

---

