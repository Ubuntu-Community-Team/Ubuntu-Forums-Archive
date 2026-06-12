---
title: "Installation issues"
date: 2009-11-10
forum: Installation &amp; Upgrades
---

### Post by Major Payne on 2009-11-10
I'm a new user to Ubuntu and have used FreeBSD way back in 99. My *nix skills are rusty at best.

I'm making a assumption here. 

1) I won't be able to upgrade from 9.04 server to 9.10 Desktop so a fresh install is needed

I burn the 9.10 desktop to a CD insert it into my computer and nothing happens. I reboot the computer 3-4 times each time it state that it's attempting to locate a boot sector (can't remember exact phrase) fails and then continues to boot to the hard drive...

Help. isn't the ISO supposed to be bootable?

---

### Post by Muskegman on 2009-11-10
> **Major Payne said:**
> I'm a new user to Ubuntu and have used FreeBSD way back in 99. My *nix skills are rusty at best.

I'm making a assumption here. 

1) I won't be able to upgrade from 9.04 server to 9.10 Desktop so a fresh install is needed

I burn the 9.10 desktop to a CD insert it into my computer and nothing happens. I reboot the computer 3-4 times each time it state that it's attempting to locate a boot sector (can't remember exact phrase) fails and then continues to boot to the hard drive...

Help. isn't the ISO supposed to be bootable?

First of all did you set your BIOS to boot from the CD drive? and if you did it could be possible that you have a bad copy on the CD. Did you check the CD for defects and do a checksum? It may also help if when you do burn the iso. image to burn it at the slowest speed possible.

---

### Post by Bucky Ball on 2009-11-10
In your server boot why don't you go to Synaptic Package Manager (System->Admin) search for and install:

ubuntu-desktop

Should be that simple.

And yea, you need to set the BIOS to boot from the optical drive if you're going the full install but I figure you know that if you managed to install the server. ;-) Should be 'delete' of F1 or something just after the machine cranks up to get to the BIOS.

Welcome to the forums and welcome back to Linux. I imagine a lot has changed in a decade.

---

### Post by Major Payne on 2009-11-10
Yes, I have set the BIOS and it's set to check the CD first.

I can re download the image from ubuntu's website and retry it. I had the program check the burn and it said it was fine but that doesn't mean the download was

Update: I ran a checksum and they match.


Bucky Ball: I have the Desktop installed on server 9.04 but It does not load properly So i figure I might as well start over and get the proper version loaded that I need. 

I'm running a CS server off of the computer

---

### Post by Bucky Ball on 2009-11-10
Did you read my last post #3??

---

### Post by Major Payne on 2009-11-10
Yeah I read post 3.

I have installed the desktop on server 9.04 but most people say it's stupid to do that. 
On top of that when i type my password into the desktop it gives me a init error (i'll get it when home) and then dumps me back to the desktop log in. 

With this problem I cant get to system admin

and yes LOTS of things have changed

---

### Post by tchoklat on 2009-11-10
I would do a "$ sudo apt-get -r dist-upgrade" to upgrade to karmic, this is what I do as I move from release to release.

---

### Post by Major Payne on 2009-11-10
But can that be used to go from Server 9.04 to desktop 9.10?

---

### Post by tchoklat on 2009-11-10
> **Major Payne said:**
> But can that be used to go from Server 9.04 to desktop 9.10?
 
 
Oops sorry, missed that. No probably not.

---

