---
title: "Installing Ubuntu on broken laptop."
date: 2009-08-17
forum: Installation &amp; Upgrades
---

### Post by Dorrax on 2009-08-17
I have two laptops, one has been running ubuntu fine for a year now, and the other is three years older and has XP, and a broken monitor... I kind of dropped a wheelchair on it...

Anyway, the broken laptop still works, I just can't see anything without plugging it into another monitor, which I don't have. I saw that ubuntu comes with a remote desktop program, and I thought that might be a good way to make the broken laptop usable again. 

I have downloaded the live disc image, so I am getting ready to make an install disc. But it occurred to me that I won't be able to see what I'm doing as I install it. Does anyone know any workarounds? Can I use remote desktop when using a live cd and see it that way? How do blind users install and run ubuntu?

I realize I have a unique problem, so any help would be greatly appreciated.

FYI: The broken laptop is a Toshiba Satellite M45

---

### Post by jerrrys on 2009-08-17
from what i have read, you have s-vga output and xp installed.  plug it into a tv and see if you get lucky....

---

### Post by Dorrax on 2009-08-18
I don't have a cable for hooking to a TV. I have found some info for installing using a screen reader, but no luck making it work. I almost need key-by-key instructions for doing this.

---

### Post by jerrrys on 2009-08-18
how to make this laptop usable again without a screen; i do not know.  however if you want to retrieve your files from this broken laptop you may be able to do this with LAN.  your laptops have ethernet and ubuntu can read NTFS.  can this be done with only one working laptop? i am not sure. but i will investigate this further if this is what you want to do...

EDIT

[http://www.google.com/search?q=lan+ntfs+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=lan+ntfs+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by dandnsmith on 2009-08-18
> **Dorrax said:**
>  the broken laptop still works, I just can't see anything without plugging it into another monitor, which I don't have.

How can you be sure it still works, without plugging in an external monitor?

Beg, borrow, or buy some sort of cheap monitor, and use that for installation - otherwise, transfer the HDD to an identical laptop, and do the install on that.

Lacking a monitor you end up in the bind where you don't know things are working until you get them working, as you need either a display, or a working OS which has the network set up.

---

### Post by tgalati4 on 2009-08-18
Agreed, you need to borrow a monitor to at least do the installation.  Once installed, you can login with ssh -Y and run a graphical desktop remotely.  It's actually faster than you would expect in this mode.

Or, find an S-Video cable and use your TV.

One final method that I don't recommend, but it works sometimes:

Pull the harddisk from the borked machine and put it in the working laptop.  Install Ubuntu.  Put the drive in the broken laptop and try to boot.

---

