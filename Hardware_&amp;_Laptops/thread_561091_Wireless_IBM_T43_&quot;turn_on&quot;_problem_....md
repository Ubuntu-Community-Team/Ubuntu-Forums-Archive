---
title: "Wireless IBM T43 &quot;turn on&quot; problem ..."
date: 2007-09-27
forum: Hardware &amp; Laptops
---

### Post by qaweb on 2007-09-27
Hi,

I've just installed Ubuntu on my IBM Laptop T43... what a liberation...except..
The "wifi LED" indicator comes on during/after POST but turns off and stays off when I try to configure and add a Wep Key.  Reboot?  Then it never comes on again.  

Yet, mysteriously [FONT="Courier New"][COLOR="DarkRed"]sudo iwlist[/COLOR][/FONT] reports my wireless AP and those of 3 or 4 neighbors.  Something's "On".

I've used  [FONT="Courier New"][COLOR="DarkRed"]sudo ifconfig[/COLOR][/FONT] which reports the WiFi adapter is recognized but all traffic counters are zero.

I wonder if it's not the WiFi component but the F5 key that toggled the Card "on/off" ....

Yes, I've searched and read a lot on how to configure the WiFi component in the IBM Thinkpad...
but most of what I've seen talks about (re)compiling an ACPI driver ... way over my head.
Any useful tools or gentle suggestions for this new escapee from Windows?

Thank you,

Allan

---

### Post by giox on 2007-09-27
Can you type this on terminal:

lspci

and check what type of wireless card are you using.

Please post the output.

---

### Post by stelloscuro on 2007-10-23
[B]sudo apt-get remove network-manager
[/B]
This cured it for me!

---

### Post by aaronjab on 2008-02-01
Definitely ensure your machine is completely up to date... I had issues in the beginning with the wireless adapter but after a comprehensive update (with all updated repositories) everything worked perfectly.

-Cheers

---

