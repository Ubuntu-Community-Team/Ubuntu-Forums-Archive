---
title: "Ethernet card is down."
date: 2005-08-03
forum: Hardware &amp; Laptops
---

### Post by agl on 2005-08-03
Hi.

I have just converted. I upgraded from Warty to Hoary through synaptic, and that caused everything to be better. Except my internet connection died, i am connected to the internet via my ethernetcard which is not found by linux, but which has been, and I am now writing via the LiveCD, so the hardware works. I have read a lot on the forum and found;

lspci, shows that my ethernet card is a 3com, and it is found.

Tried to use ifdown and ifup eth0, but it says that I have no ethernet card.

Tried to edit /etc/network/interfaces/ but that gave little sense to me.

Where do I go from here

Anton.

---

### Post by odin on 2005-08-03
Follow this link [http://www.ubuntuforums.org/showthread.php?t=53700](http://www.ubuntuforums.org/showthread.php?t=53700) and try to see if the example helps you.this example is for a wireless card just forget about the wireless options.

---

### Post by agl on 2005-08-03
Hi, and thanks for writing.

I see that I have forgot some info.

I am assigned an IP address in the Network Tools program.

My ethernet card is not active in the GUI network thingy. It only shows a inactive modem connection... The program, and the other network applications I have tried, do not recognize my ethernet card.

But I will try to look more at the link you gave me. 

Thank you.

---

### Post by agl on 2005-08-04
ok I tried to edit the etc/network/interfaces again without any result. Ifup says:

sit0:unknown hardware address type 776
SIOCSIFADDR:No such device
eth0: error while getting interface flags : no such device
eth0: error while getting interface flags : no such device
sit0:unknown hardware address type 776
Bind socket to interface: No such device

I have no idea what to do now... please help. It seems that alot of people have similar problems, there has to be a sollution.

Anton.

---

### Post by agl on 2005-08-04
Hi again, I am keeping this thread alive and updating on my situation...

dmesg said that there is a problem with my 3c59x
it says: 
0000:00:03.0 : 3com PCI 3c556B Hurricane at 0x1400. vers LKI.1.19

...

*** EEPROM MAC address is invalid
3c59x : vortex_probel fails. Returns -22
3c59x : probe of 0000:00:03.0 failed with error -22

I am writing it down on paper, so I am not writing the entire section. 

Modprobe 3c59x just turned out with nothing - which is good or so claims the info command  :) But it did not make anything work.

I wondered, according to dmesg most of my devices use IRQ 11 is that normal

I promise that if I get this to work I will post it here... it seems to me that many people don't write what solved their problem, which is a shame.

Anton.

---

### Post by agl on 2005-08-06
I have solved the problem. It turned out to be problems with ACPI, which are common with my IBM T20. The problem was solved by changing to APM.

[http://www.ubuntuforums.org/showthread.php?t=2620&highlight=apm+switch](http://www.ubuntuforums.org/showthread.php?t=2620&highlight=apm+switch)

I also used the command apm=on I have no idea if it did anything.
I had some problems with a very long "wait" before nautilus would start. Which was a network problem, it took ubuntu a thousand years to determine my host. I solved by adding a line I had removed in the /etc/network/interfaces
auto lo

Anton.

---

