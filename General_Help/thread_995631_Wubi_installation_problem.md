---
title: "Wubi installation problem?"
date: 2008-11-28
forum: General Help
---

### Post by DeeXener on 2008-11-28
Hi all!
Well as anyone could tell by me posting here I have a problem with Wubi. Oh joy.
So I installed Ubuntu through Wubi on a Vista Home Premium PC and Wubi downloaded the ISO and everything was going smoothly. At the point I need to restart my PC is when things get weird. It restarts and then I select Ubuntu as my OS during boot. When it enters the Ubuntu loading screen shows up and loads and then gives a text screen with a console line. I tried typing install, restart, etc. Anything general to see what was going on. Is Ubuntu supposed to install after the restart?

---

### Post by Orlsend on 2008-11-28
Could you write down the text that appears and then type it here?

---

### Post by col.panic on 2008-11-28
After it reboots I believe that it is supposed to boot into ubuntu to finish the last part of the instalation.  I would recommend uninstalling wubi under windows then download the iso seperately and then point wubi at the iso to do the reinstall.

I like to download linux distros with "download them all" a handy firefox extension.  It will allow you to specify a MD5 hash to verify that the download was good.

see:
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

---

### Post by DeeXener on 2008-11-29
Doesn't Wubi do a hash check? I thought it did.

> 
Checking file C:\ubuntu\install\ubuntu-8.10-desktop-amd64.iso
MD5: f9cdb7e9ad85263dde17f8fc81a6305b f9cdb7e9ad85263dde17f8fc81a6305b
File check successful!


Above is from metadl_log and it appears that Wubi does do a MD5 check.

But here is how it goes down. I hit 'exit' when the screen appears (even if I don't hit exit it takes me to install automatically) and then go to a menu for install types. I've tried pretty much all of them (normal, safe graphics mode, live cd...) and come up with the same thing.

After I select an option I get this at the top of the screen,
'Aperture beyond 4GB. Ignoring.'
Then Ubuntu goes to a loading screen. It gets to various points in loading whether it be mostly through or just from the point the bar bumps around. After it gets through mostly loading the colors of the loading screen seem to invert and I'm thrown into a blank screen where I can type. Suddenly some text flashes and I get taken to a screen about Ubuntu not guaranteeing a warranty and blah blah blah with a command line similar to 'ubuntu@ubuntu' I can type things like 'help' and get a bunch of commands but the command 'install' didn't do anything.

So might it have something to do with the aperture or maybe a graphics problem with the screen inverting?

---New Idea

By default Wubi downloads the amd64 version. I'm going to try the i386 but don't know if that will make a difference.

---

### Post by DeeXener on 2008-11-30
It was the ISO type. I needed the i386 instead of the amd64 that Wubi downloads automatically.

---

### Post by pietgrijs on 2009-01-24
So, I'm having the same problem, and I'm wondering: 
-how did you know which ISO was the right one?
-where did you find it?

---

### Post by pietgrijs on 2009-01-24
ow, I get it, it's the normal Ubuntu-iso you need. Great, I can find that one myself ;-)

---

### Post by pietgrijs on 2009-01-24
Well, I found the right ISO and installed Wubi again, but I still have the exact same problem. 
Any hints?

---

### Post by Yownanymous on 2009-01-24
> **col.panic said:**
> I like to download linux distros with "download them all" a handy firefox extension.  It will allow you to specify a MD5 hash to verify that the download was good.
Me too!

---

