---
title: "Installing a serial mouse on Xubuntu"
date: 2006-09-06
forum: Hardware &amp; Laptops
---

### Post by lkvee on 2006-09-06
I'd like to put my old serial mouse to work on a Sony Vaio PCV-L400 desktop (P2-400 MHz/6GB/192MB).   There's only one PS/2 port in this computer (for the keyboard0 and I'd like to save the USB ports for something else.   

I'm open to using a USB mouse.  In fact, xubuntu works with a USB mouse.   I'd like to take the time & effort to get the serial port to work. 

I've tried to change the xorg.conf file so that the mouse port location reads /dev/tty/S0 instead of /dev/input/mice.  I've also tried /dev/tty/S1

I'm not sure how to capture output when I run the command sudo dpkg-reconfigure xserver-xorg or when get the error messages using /dev/tty/S0 and dev/tty/S1   The Vaio has one serial port, 2 PCI slots, one parallel, one PS/2 port, one 15-pin VGA port, and one proprietary LCD port.

Anything else I can try?

---

### Post by zxee on 2006-09-07
> **lkvee said:**
> 
I'm not sure how to capture output when I run the command sudo dpkg-reconfigure xserver-xorg or when get the error messages using /dev/tty/S0 and dev/tty/S1   The Vaio has one serial port, 2 PCI slots, one parallel, one PS/2 port, one 15-pin VGA port, and one proprietary LCD port.

Anything else I can try?

I'm not sure what output you're wanting from the dpkg-reconfigure command?
Using >> after a command will send it to a file e.g. dmesg>> output.txt
Doesn't dpkg-reconfigure xserver-xorg allow you to select a serial mouse?

---

### Post by mpvano on 2006-09-07
FYI, most VAIO notebooks use the IBM standard pS2 wiring which has wiring for simultaneous use of BOTH a keyboard and mouse on the same connector.

You might consider using a standard mouse/kbd Y adapter to solve the problem if you can find one. (Their a little obscure). The one I have is made by Belkin and works fine on all the Dell servers, IBM Thinkpads, Toshiba Notebooks and VAIO notebooks I've ever tried it on. It does NOT work on some generic desktops I've tried it with, however.

I find this usually works a lot better than a serial interface. Modern mice seem to drop a lot of characters on serial IO and confuse the GUI. I think it's probably because they generate output faster than it can get through the serial port.

hope this helps....

Mario

---

### Post by lkvee on 2006-09-10
I actually acquired a PS/2 keyboard/mouse splitter.   Hooked it up, turned the computer on and watched what happened.

The keyboard works.   The mouse doesn't.

I still have some things I need to try.   I actually have more than one splitter, so I'll try that.   I'll make sure everything's connected before I turn on the Vaio.   I'll probably try more than one mouse, too.

Any way I can confirm xubuntu even sees a serial port?   I suspect the installation may have missed it even though I plugged in a mouse at that time (native PS/2 mouse with serial adapter).

Looks like a USB mouse in the future.

---

### Post by mpvano on 2006-09-11
Exactly what model mouse are you trying to use? Perhaps it's just too old or incompatible?

Note also that the splitter is NOT a Y cable. It has a keyboard and a mouse port. Keyboards sometimes work when plugged into either, but the mouse must be plugged into the one marked mouse.

Serial ports usually show up in dmesg like this:

$ dmesg | grep tty
[17179573.912000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a NS16550A
[17179573.916000] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a NS16550A

Make sure the serial port is enabled in the BIOS and that it's not shared with an IR adapter.

Be aware, as I told you before that most serial mice do NOT work reliably with modern X windows servers because they drop messages when the server is busy or power managed and get out of sync driving the pointer and GUI crazy. This is almost always a problem if your machine is slower than a pentium IV.

Maybe it's time to give it a decent burial?

---

### Post by lkvee on 2006-09-15
I got a PS/2 mouse up and running now.   I went into the BIOS setup and changed the PS/2 Mouse setting from Auto to Enabled.  I also took the KVM switch setup out of the picture and used a standalone mouse and keyboard.  I also made sure the peripherals were plugged into their correct ports on the Y-connector (this connector also has the mouse and keyboard clearly marked).

I'd still love to see the output for dmesg | grp tty but I might have to install xubuntu again.  Ummm, I forgot the login/password combination I used.  Oh well.

---

### Post by Shinoda on 2007-11-03
> **lkvee said:**
> I've tried to change the xorg.conf file so that the mouse port location reads /dev/tty/S0 instead of /dev/input/mice.  I've also tried /dev/tty/S1
That's [FONT=Courier New]/dev/ttyS0[/FONT]. Additionally [this]("http://ubuntuforums.org/showthread.php?t=202972#post1176847") may be helpful.

---

