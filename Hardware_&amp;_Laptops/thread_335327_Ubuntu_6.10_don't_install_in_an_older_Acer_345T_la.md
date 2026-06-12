---
title: "Ubuntu 6.10 don't install in an older Acer 345T laptop"
date: 2007-01-10
forum: Hardware &amp; Laptops
---

### Post by garduino on 2007-01-10
Hi:

I' want to install Ubuntu as the only operating system in an older laptop Acer 345T (with 192 MB RAM and 6 GB HD).

After wait a lot of time, I'get an error about some IRQ not working, that I've solved using (as the same process recommend) the parameter "irqpoll".

After that trying again, take a lot, really a lot of time to boot the live, and when try to install, the first screenshot of installer don't end of displaying, and get frozed.

Does exist some method, more appropiated to install Ubuntu in such slow and old hardware?

Thanks in Advance by the help.

---

### Post by kerry_s on 2007-01-10
Grab the alternate cd and install in text mode. Also with those specs you should try xubuntu instead. There is also Fluxbuntu with fluxbox for low spec machines. You might also want to try PCLinuxOS minime it works great on my acer.
-> [http://cdimage.ubuntu.com/xubuntu/releases/6.10/release/xubuntu-6.10-alternate-i386.iso](http://cdimage.ubuntu.com/xubuntu/releases/6.10/release/xubuntu-6.10-alternate-i386.iso)
-> [http://modzer0.cs.uaf.edu/~hardwarehank/fluxbuntu/rev2/fluxbuntu-nbuild1-rev2-desktop-i386.iso](http://modzer0.cs.uaf.edu/~hardwarehank/fluxbuntu/rev2/fluxbuntu-nbuild1-rev2-desktop-i386.iso)
-> [http://ftp.belnet.be/linux/pclinuxos/live-cd/english/preview/pclinuxos-p93a-minime.iso](http://ftp.belnet.be/linux/pclinuxos/live-cd/english/preview/pclinuxos-p93a-minime.iso)

---

### Post by garduino on 2007-01-10
Thanks by your response and useful information and links!

> **kerry_s said:**
> Grab the alternate cd and install in text mode.

Can you point me how to get the alternate CD? I've downloaded the ISO of 6.10 and burn the common live CD, but don't know about the alternate.

---

### Post by garduino on 2007-01-10
> **garduino said:**
> Can you point me how to get the alternate CD? I've downloaded the ISO of 6.10 and burn the common live CD, but don't know about the alternate.

Sorry, bad question. I've found in the download page.

Cheers.

---

### Post by garduino on 2007-01-12
Finally I've installed [Xubuntu]("http://www.xubuntu.org/") from the main CD (using the alternate may be a better option if a fast installation is required).

Some useful tips:

[LIST]
[*]Use "irqpoll" at boot.
[*]Use "fb=false" at boot.
[*]If the installation seems freezed, only wait and wait (some touch to the mouse may give you the sound of the hd awake again :) )
[/LIST]

Cheers.

---

### Post by do2or on 2007-12-01
You can try to start the installation CD and at boot press the F4 key and select 600X800X16 
Press F6, and the quiet before adding: 
acpi=off xforcevga vga=788 noapic nolapic noscsi nopcmcia
before: quiet --
press Enter and the installation start 

At first boot GRUB start, you have 3 seconds press "Esc" 
And press "E" 
chose line 2
And press "E" 
And add this: 
acpi=off xforcevga vga=788 noapic nolapic noscsi nopcmcia 
before: quiet --

Now you have to change the GRUB boot options: 
Open Console  ant type:
Gksudo gedit /boot/grub/menu.lst 
Enter your administrator password 
And select the file begin with: 
Start default options 
And add this 
acpi=off xforcevga vga=788 noapic nolapic noscsi nopcmcia
before: quiet --
and save it

---

