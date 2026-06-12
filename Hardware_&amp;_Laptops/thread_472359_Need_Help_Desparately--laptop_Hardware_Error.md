---
title: "Need Help Desparately--laptop Hardware Error"
date: 2007-06-13
forum: Hardware &amp; Laptops
---

### Post by jccarr117 on 2007-06-13
Okay, guys, I need MAJOR help.  Today I just dual-installed Windows XP and Ubuntu.  Problem is, my XP now is prior SP2 and most drivers for my hardware.  I have a Dell Inspiron 8600.  When I go to connect to the internet, neither OS will work ( I use DSL and a Linksys router).  Specifically, I can access the internet wired using Ubuntu, but cannot get to the inernet from XP any way, and cannot access it wirelessly by Ubuntu.  The only thing I notice is that none of my wireless or network adapters are picked up by the Windows XP device manager.  When I try to install the ProSET utility by Dell, it claims that my network adapters are not present.  They are!  What do I do?  Help!

--I'm using the newest version of Ubuntu; I don't know numbers, but I know it's the newest of the standard Ubuntu.
--I want to say that the chips are Intel Broadcom--but I can't exactly look at them
--I did install windows first.
--I'm working on those two commands.

--I figured out--it is a PRO/Wireless LAN 2100 3B Mini PCI Adapter

---

### Post by jml on 2007-06-13
I'm no wireless expert, but a little more information would be helpful.  Post the output of the following two commands to this thread:  "ifconfig and iwconfig"  without the quotes.  They should be typed in as root using the sudo command from within the terminal.  Someone may be able to help you.

A few other questions.  What version of Ubuntu are you using?  And, what type of chip set does your wireless card use, (Intel, Broadcom, etc?)

One final question, did you install Windows first and then Ubuntu?  If you did it the other way around, it can cause problems with a dual boot system.  

Joe

---

### Post by DagMan on 2007-06-13
Also the output of lspci please

---

