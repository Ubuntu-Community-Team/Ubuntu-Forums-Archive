---
title: "HP Deskjet 4625 driver installation (with picture of printing output)"
date: 2013-11-02
forum: Hardware
---

### Post by hoffman2 on 2013-11-02
Guys,

I just bought a new HP Deskjet 4625 printer. 
I tried to installed the driver by plugging through USB.
Ubuntu recognized the printer and showed the recommended driver for this specific printer.

I installed and tried to print a test page but it didn't print right.

Any ideas to fix ?

Edit:

Here are all steps that I took when I install the HP 4625 printer on my Ubuntu
I went to "Printers" then I clicked "Add" under USB conection it listed two different driver, one without FAX and the other on with FAX.
I tried both. On each selection that I choosed, it went to other option where I choosed the one that is "Recommended" by the system.
The driver that says with FAX is not printing anything when I hit "Test Print Page" and the driver that says without FAX printed several pages when I hit "Test Print Page"
And the result is like this:
[IMG][[IMG]http://s14.postimg.org/phr8ktckd/HP_4625_Ubuntu_Output.jpg[/IMG]]("http://postimg.org/image/phr8ktckd/")[/IMG]

Hope this would help to solve my problem....

---

### Post by walterorlin on 2013-11-02
From the terminal run ```
sudo hpsetup
``` with the printer plugged in enter your password and a window should pop up if you don't put it in interactive mode. If you don't want to use a graphical user interface you can run ```
sudo hpsetup -i
``` which is a fairly simple set of text mode instructions that you can follow as another way to do this.

---

### Post by hoffman2 on 2013-11-03
> **walterorlin said:**
> From the terminal run ```
sudo hpsetup
``` with the printer plugged in enter your password and a window should pop up if you don't put it in interactive mode. If you don't want to use a graphical user interface you can run ```
sudo hpsetup -i
``` which is a fairly simple set of text mode instructions that you can follow as another way to do this.

I tried it out and it came out like this:
```
hoffmanp@hoffmanp-ThinkPad-E420:~$ sudo hpsetup
[sudo] password for hoffmanp: 
sudo: hpsetup: command not found
hoffmanp@hoffmanp-ThinkPad-E420:~$ sudo hpsetup -i
sudo: hpsetup: command not found
hoffmanp@hoffmanp-ThinkPad-E420:~$ 
```

any other ideas....

---

### Post by Morbius1 on 2013-11-03
it's hp-setup not hpsetup

---

### Post by hoffman2 on 2013-11-04
> **Morbius1 said:**
> it's hp-setup not hpsetup

Tried that too and this came out:

```
hoffmanp@hoffmanp-ThinkPad-E420:~$ sudo hp-setup
[sudo] password for hoffmanp: 

HP Linux Imaging and Printing System (ver. 3.12.2)
Printer/Fax Setup Utility ver. 9.0

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Searching... (bus=usb, search=(None), desc=0)
error: No devices found on bus: usb

Done.
hoffmanp@hoffmanp-ThinkPad-E420:~$ 

```

I had the printer connected to the laptop through USB.
Anyone?
:(

---

