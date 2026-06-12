---
title: "Problem with 8.10 Persistant Install from USB"
date: 2009-04-17
forum: Installation &amp; Upgrades
---

### Post by homeriq5 on 2009-04-17
Hi all, 

I am trying to install ubuntu 8.10 to my 16 gb sandisk cruzer.  I used the usb-startup disk creator that came with jaunty to make it, and it boots just fine to the normal installation menu.  But, when I select "try ubuntu without installing first" to load the desktop, it goes to the loading bar window and then stops at this black screen with "busy box" and command line and doesnt do anything.  When I run "cat casper.log" at this problem it prints "can not mount /dev/loop on /cow".  Getting this to work is really important to me, if someone can help that would be great!  Is anyone else having this problem too?

---

### Post by homeriq5 on 2009-04-18
nobody?  Guess I'll stick with windows on my work desktop.

---

### Post by vikjon0 on 2009-05-05
I think this is a bug. I got the tip in another forum.
[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/219192](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/219192)

Anyone have any information about this?

Also some explaination would be good. I do not really understand. Is it correct that the casper stuff is coming from the target system in the ISO not from the system creating the USB boot?

---

