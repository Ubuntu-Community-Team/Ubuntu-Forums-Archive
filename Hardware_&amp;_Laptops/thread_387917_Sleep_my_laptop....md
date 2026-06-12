---
title: "Sleep my laptop..."
date: 2007-03-18
forum: Hardware &amp; Laptops
---

### Post by axrh on 2007-03-18
Hi Guys,

How do I get my laptop (thinkpad a22e) to fall asleep from within window maker?  In gnome I was able to close my lid and the laptop would go into sleep mode.  Ideally, I could do this with window maker also, but I'd be fine with having to choose sleep from an menu.  How can I put my computer to sleep from within window maker (I'm tired of having to log out every time).  If I close my lid, the screen turns off, but it is clear that the laptop is not in sleep mode (fans run, processor chirps, etc.).

Thanks!

---

### Post by axrh on 2007-03-19
Hi guys,

I've found a semi-fix to my problem.  I have an appicon that runs a small shell script that I wrote that sleeps my computer.  However, my script opens up a terminal that (unless I've used sudo recently) requires me to put in my password. There must be a way to sleep my laptop without using the gnome tools (or use the gnome sleep tools from window maker).  

I would appreciate _any_ advice.

Thanks!

---

### Post by PhilipGanchev on 2007-03-19
I use a Thinkpad A21m, which may be quite similar to yours.  I used ACPI to make it suspend when I close the lid, or press Fn+F14.  I have not got it to wake up from hybernation.  And when it wakes up from suspend, the sound does not work.  Since A21m is an old model, I had to enable ACPI in the kernel at boot time, by adding "acpi=force" at the end of the "kernel" line in /boot/grub/menu.lst.

I also added "deb [http://debian.isg.ee.ethz.ch/public](http://debian.isg.ee.ethz.ch/public) sarge ibm-acpi" to my /etc/apt/sources.list

Use "apt-cache search thinkpad" to see programs that apply to thinkpad laptops.  Sleep-related programs I get are: thinkpad-base, tpb, tpctl, ibm-acpi

Instead of ACPI, you might be able to use APM.  I don't remember why I decided to use ACPI.

Also see the wiki about Linux on thinkpads (do a web search).

If you find out how to make your computer play sound after it wakes up,

---

### Post by axrh on 2007-03-19
Hi,

I can actually use Fn F4 to go into sleep mode.  I made a change to some file int /etc earlier today and I only tested it with closing the lid (which didn't work).  Apparently it fixed Fn F4 though which I can live with.

Thanks!!!

---

### Post by axrh on 2007-03-19
BTW, my sound still works.  If anyone cares, this is what I did to make Fn F4 work:

in /etc/acpi/sleepbtn.sh
change the last line to /etc/acpi/sleep.sh sleep


Axel

---

### Post by PhilipGanchev on 2007-03-20
My last line is

acpi_fakekey $KEY_SLEEP

You are saying you removed that and replaced it with

/etc/acpi/sleep.sh sleep

Is that right?

---

### Post by axrh on 2007-03-20
Yup, that's exactly what I did.  Closing the laptop lid didn't work, but Fn F4 did (and sound worked when I woke the computer).

---

