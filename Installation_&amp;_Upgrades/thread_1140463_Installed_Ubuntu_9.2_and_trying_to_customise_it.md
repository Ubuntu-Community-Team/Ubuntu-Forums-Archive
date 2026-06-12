---
title: "Installed Ubuntu 9.2 and trying to customise it"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by Titoolsen on 2009-04-27
I have installed Ubuntu 9.2 on my older Pentium 4 PC. I have a few problems:

Although the OS recognises the USB Belink wireless drive it doesn't commit the encryption password to memory hence I have to type this each time I boot the PC. Is it possible to commit it to memory?

I have tried showing a DVD but Movie Player fails to read the DVD and asks for a plug-in that it can't then find.

The Desk top and the documents folder seems restricted to 9.10 mb. How do I increase this so I can manage downloads and how to I increase the memory of the Documents folder?

I have a 194 GB disk and I can access that from the 'Places' menu.

How to I load a webcam?

Thanks

---

### Post by lisati on 2009-04-27
9.2? Huh? I think you mean 9.04......

Have you tried searching [http://help.ubuntu.com](http://help.ubuntu.com) yet?

---

### Post by Titoolsen on 2009-05-17
Sorry - been away!

Yes it is 9.4 - I have searched the various HELP menus and can't find out exactly what to do next. I am immediately trying to understand how to link my desktop and Documents folder to the large 186gb HD. From various responses I see that I have to re-partition my hard disk and have downloaded gparted package. Now what!

When I open Gparted the menu shows 5 sections in the left panel /dev/sda1 then underneath sda2, sda6, sda7, sda5

---

### Post by Mark Phelps on 2009-05-17
> **Titoolsen said:**
> I have installed Ubuntu 9.2 on my older Pentium 4 PC. I have a few problems:

These all-in-one posts generally don't work.  If you want specific help, it's better to first, search the forums for posts with similar problems, and if you can't find anything, post one problem per thread.

So, to continue ...

> I have tried showing a DVD but Movie Player fails to read the DVD and asks for a plug-in that it can't then find.
It generally prompts for permission to download and install packages have have the missing codecs.  It's best to provide us the specific error message you're getting.

> 
The Desk top and the documents folder seems restricted to 9.10 mb. How do I increase this so I can manage downloads and how to I increase the memory of the Documents folder?

Folders don't have specific size limits; the size limits are set by the partition.  And, "memory" has nothing at all to do with partition size.  

So, to determine the partition sizes, open the Partition Editor and look at the sizes shown.  If you have no entry under System --> Administration --> Partition Editor, then open Synaptic and install GParted.

> 
How to I load a webcam? 
Start a separate thread for this problem.

---

