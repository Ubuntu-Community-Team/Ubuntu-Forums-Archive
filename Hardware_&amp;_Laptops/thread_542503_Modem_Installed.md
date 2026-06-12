---
title: "Modem Installed"
date: 2007-09-04
forum: Hardware &amp; Laptops
---

### Post by Emm AAy on 2007-09-04
hello 

i am new to ubuntu and want to know that how do i check my modem installed properly i mean it shows in Administrative -> Hardware setting but how do i know that whether or not it conflicting.

i dial through Gnome-ppp dialer but it not detect any modem at either of their port.

---

### Post by geraldm on 2007-09-04
Provide more information:
What is the manufacturer of the modem?  model?  type {usb pci winmodem .. }
How did you try to install it? 
On booting, is it recognized in /var/log/dmesg file? 

Gerald

---

### Post by Emm AAy on 2007-09-04
Pc Tel 56k Winmodem (Conexant)
pci
i did not try to install it. It automatically shows in the hardaware section
On booting, is it recognized in /var/log/dmesg file?................? i dont know this process kindly help me in this process 

i actually run a command in terminal pppconfig/configppp and it starts a wizard i follow the instruction and it eventually reach where it probing for modem and halt, probing at port serial1 and then i manually configure at serial1.

After that i install gnome-ppp package after installing i try to connect, it first diagnose the modem and prompt for no success.

my modem is properly sloted in pci slot
and it working at windows xp

if there is a driver problem then tell me if there is a place where i could find its driver or there is no support for this device on linux.

also thanx for reply because i saw lots of ppl's see this thread and eventually only 1 reply to it.

---

### Post by geraldm on 2007-09-05
When gnome-ppp or other GUI programs ask for a modem, they would usually expect to
find an external modem, which would be connected to one of the serial lines.
This just asks which serial line the modem is on.  

You still need a driver for your PCI winmodem to setup the modem for use.
I do not know the name of a package or driver for this.  Try searching in the ubuntu
forums for keywords like 'conexant' or 'winmodem' as there should be many threads
available, or even a HOWTO for it. I found one:
[http://www.ubuntuforums.org/showthreads.php?t=488411](http://www.ubuntuforums.org/showthreads.php?t=488411)
There are likely many others, as winmodems are rather common (but disliked because they
are harder to set up)

dmesg: 
There is a file created upon booting, usually in /var/log/dmesg  This file shows which 
devices were discovered in booting, and shows how it was handled.  You can view it with
a text editor such as vi, nano, etc.  You can also enter the command "dmesg" to see the file.
There won't be much help in it for a winmodem that still needs a driver, 

good luck finding a driver for your modem.

Gerald

---

### Post by Emm AAy on 2007-09-05
i found what looks like a very similar device driver and i ll try to installed it tonight on my home pc and will let u know if there is a problem.

driver file has .deb extension and i ll try to installed through package manager hopefully it will do it for me.

---

