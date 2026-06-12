---
title: "Keyspan USA-19HS USB to serial adapter with Lucid"
date: 2011-07-12
forum: Hardware
---

### Post by Old Toshiba on 2011-07-12
Hello everyone,
 
I have been searching the internets for ways to get the Keyspan USA-19HS adapter to work with 10.04. So far, all I have found is methods to patch/compile kernels which are old and out of support. It looks like support for the serial adapter was dropped after 6.04.
 
My question is, does anybody have a better solution than recompiling the kernel for Lucid? I am currently running Lucid with kernel 2.6.35.
 
Thanks.

---

### Post by Old Toshiba on 2011-07-14
Update: The Keyspan adapter was not working due to a configuration setting in the program that was using it. Now that the program is configured correctly, it works just fine. ;)

---

### Post by Zalmor on 2012-08-27
> **Old Toshiba said:**
> Update: The Keyspan adapter was not working due to a configuration setting in the program that was using it. Now that the program is configured correctly, it works just fine. ;)

Just picked up one of these the other day.  My Ubuntu 12.04 LTS 64-bit currently sees the USA-19HS device via **lsusb** and/or **dmesg** in the terminal window.  Hopefully I spelled these correctly as I'm a newbie to Ubuntu.  What was your solution to get your program configured correctly.  It might help me here narrow down as to where to look on my two astronomy programs I'm trying to utilize to control my GOTO telescope.

---

### Post by mdecler2 on 2013-06-10
> **Zalmor said:**
> Just picked up one of these the other day.  My Ubuntu 12.04 LTS 64-bit currently sees the USA-19HS device via **lsusb** and/or **dmesg** in the terminal window.  Hopefully I spelled these correctly as I'm a newbie to Ubuntu.  What was your solution to get your program configured correctly.  It might help me here narrow down as to where to look on my two astronomy programs I'm trying to utilize to control my GOTO telescope.

I have a recurring kernel panic with the USA-19hs keyspan device when the "do_tty_hangup" is performed.  I reported my issue here: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/1018241](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/1018241).  No solution has been forthcoming.  Has anyone found a solution?  Does the next Ubuntu release have a fix?

---

