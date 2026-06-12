---
title: "Gutsy and cups: something changed? Printer not working..."
date: 2007-10-24
forum: Hardware &amp; Laptops
---

### Post by phonky on 2007-10-24
Hi folks

I am the only guy with linux on a small university campus. we have a
canon imagerunner 3100 c printer, to which we connect via tcp/ip port 9100.
There's accounting printing activated, so we need to provide username/password to
print.

I installed some month ago or so a specific SQue driver for the printer, 
which creates a cups queue. configured
it and finally got it working at some point.

However, it doesn't anymore, and I don't know why. It may have to do with 
the gutsy upgrade? The print job is sent out, cups reports no problems, but nothing
gets printed...
(No error message at the printer, just plain nothing).

ideas anyone? would be really great to solve, [B]I was going to propose ubuntu
to my fellow students, but w/o printing that's a no-go.[/B]

---

### Post by cow_racer on 2007-10-24
> **phonky said:**
> Hi folks

I am the only guy with linux on a small university campus. we have a
canon imagerunner 3100 c printer, to which we connect via tcp/ip port 9100.
There's accounting printing activated, so we need to provide username/password to
print.

I installed some month ago or so a specific SQue driver for the printer, 
which creates a cups queue. configured
it and finally got it working at some point.

However, it doesn't anymore, and I don't know why. It may have to do with 
the gutsy upgrade? The print job is sent out, cups reports no problems, but nothing
gets printed...
(No error message at the printer, just plain nothing).

ideas anyone? would be really great to solve, [B]I was going to propose ubuntu
to my fellow students, but w/o printing that's a no-go.[/B]

Why not install gnome-cups-manager?  I couldn't use the default printer manager, so I install gnome-cups-manager and was able to set up my printer the way I set it up in many of the previous version.

---

### Post by phonky on 2007-10-25
I actually have gnome-cups-manager installed,
but that doesn't help me because I need to configure
username and password to be able to print, and I don't see
this anywhere in this manager.

---

### Post by phonky on 2007-11-03
Hmmmm,

it seams I can (sometimes) print when I start the process as root!!!
So for example

```
eog mypicture.jpg
``` won't print anything
but with
> sudo eog mypicture.jpg the job appears in the printers log,
although with an error.

I managed though to print a test page via
> sudo gnome-cups-manager and then print a test page on the net printer.

So why can root print and my normal ubuntu user cannot?

Thanks
fabio

---

### Post by speedj on 2008-01-07
I just solved this problem.

Please have a look at [https://wiki.ubuntu.com/HardwareSupportComponentsPrintersCanon](https://wiki.ubuntu.com/HardwareSupportComponentsPrintersCanon) at the imageRunner iR3xxx line, or directly at [http://dalbrizio.googlepages.com/how-to_#sque](http://dalbrizio.googlepages.com/how-to_#sque).

Ah, if only Canon had Linux in mind the half HP does.... 	](*,)

---

