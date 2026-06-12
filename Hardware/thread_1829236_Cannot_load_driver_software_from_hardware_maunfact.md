---
title: "Cannot load driver software from hardware maunfacturers disc"
date: 2011-08-20
forum: Hardware
---

### Post by George Stephenson on 2011-08-20
"Blocked: wine start /unix
The file "media /EPSON/EPSetup.exe" is not marked as executable. If this was downloaded or copied from an untrusted source, it may be dangerous to run. For more details, read about the _executable bit_."

It's not an untrusted source, it's a disc from the box my printer/scanner came in. Therefore it's not dangerous to run.  I read the executable bit and could not understand a word of it.  

How do I force UBUNTU to execute setup programs from all my hardware suppliers discs?


](*,)

---

### Post by tom4everitt on 2011-08-20
Good news and bad news:

Good news is that it's pretty easy to make a file executable if you want to. 

1. Open Nautilus as root: 
    - press alt+f2
    - type "gksu nautilus" (without quotes), press enter
2. Find the file you want to change (probably in /media somewhere), right click, choose Properties, choose the tab "Permissions", make it executable.


Bad news is that the file "/EPSON/EPSetup.exe" looks like a .exe file, and .exe files are Windows specific (generally). 



But what is that you're trying to do, exactly? There's a pretty good chance you don't need that CD at all, actually. Printers, for example, generally work out of the box, with no need to install software from CD (one of the advantages of Linux/Ubuntu).

---

### Post by George Stephenson on 2011-08-24
Thanks, tom4everitt, I'll give it a try.

I'm trying to get the scanner part of my new Epson SX425W printer to work. The old one (DX6050) bust and so had to be replaced.  That scanner worked perfectly (after much head-banging) in Xsane.  The new printer works, as CUPS has a driver for it.  I am trying to load the Epson disc in Wine, as I have a few such MS/Windows programs which used to work in 10.04, but now don't in 11.04.  I'll give "Nautilus in Root" a try, but I don't know what that is yet.

---

### Post by tom4everitt on 2011-08-24
Okay, yes, .exe files can be executed with Wine - that's pretty much what Wine is for after all. I don't think you should need execution permission to execute something in Wine, but it doesn't hurt. 

Nautilus as root is essentially a way to manage your files as administrator (=root). Normally when you view your files with Nautilus (Nautilus is the name of the standard file browser) you do it as a normal user, and a normal user does not have the permission to change file permissions and ownership of other users file. 

So opening Nautilus as root is essentially a way to give yourself a little more authority :)

---

### Post by coffeecat on 2011-08-24
@George Stephenson, it's not quite clear from your posts what happened, if anything, when you tried xsane with your new Epson scanner.

An Epson scanner is more likely than not to have a viable Linux driver in Ubuntu but there was a bug with Epson scanners - I really don't know whether this is still so in 11.04 - that prevented some supported Epson scanners from being recognised. Have a look at this thread:

[http://ubuntuforums.org/showthread.php?t=1581065](http://ubuntuforums.org/showthread.php?t=1581065)

It's for a different model to yours but the principle is the same. If you would like to try the same fix, please post the output of these two terminal commands (with the scanner plugged in with a USB cable and switched on):

```
cat /etc/sane.d/epson2.conf
lsusb
```

---

### Post by George Stephenson on 2011-08-26
Thank you, Coffeecat,

In short, I've had to replace my DX6050 scanner with a new SX425W from Epson.  I tried to load the new scanner with a procedure I saved that I derived from lines of commands I copied from old forum posts.  This has worked every time I've had to reload the DX6050 at each Ubuntu upgrade.

The  new BUS = 001 ; DEVICE = 005 ; PRODUCTID = 04b8 ; DEVICEID = 0864

I've tried several times to put these values into the right files (libsane rules, epson conf) but to no avail. So I thought I could use the Epson disc through Wine, but even after using nautilus as root it won't work.

Any ideas? - also the new version of Terminal won't allow me to copy and paste the outputs you requested.

---

### Post by coffeecat on 2011-08-26
It would be worth trying the fix I linked to earlier but before we go any further, **please** post the terminal output I asked for before:

```
cat /etc/sane.d/epson2.conf
```

I don't want to be getting you writing to that before we see what is there to start with.

Also:

> I've tried several times to put these values into the right files (libsane rules, epson conf) but to no avail.

Please clarify. Do you mean that whatever you wrote did not work, or that you were not able to write to configuration files?

---

### Post by .... on 2011-08-26
Printer drivers aren't going to work through wine. That's a dead end. In general, Windows drivers won't work on Linux unless you have some kind of wrapper (e.g. ndiswrapper allows the use of some Win XP wireless drivers).

---

