---
title: "Brother DCP6690cw wireless A3 printer"
date: 2010-11-27
forum: Hardware
---

### Post by FEQ on 2010-11-27
Hi,

I have followed the posts for installing the Brother printer drivers (lpr and cups), which seemed to install OK after using the sudo force commands, but can't get this printer to function. I'm using 64 bit Ubuntu 10.10, and while I can see the brother printer (listed in printing admin) every time I try and print to it I get an error saying the printer is not connected.
The printer works fine from windows 7 so is definitely on the network.
The device URI is:
lpd://BRW78E4008F3786/BINARY_P1
I have also tried entering the IP address instead of BRW78E4008F3786 to no avail. All errors say its unable to find the printer, even though it does when you click the find network printer choice, in the find printer dialog. The printer uses WPA2 security with a passkey to connect to the wireless network.
Is there something about the queue (BINARY_P1) that can be changed? Any clues please?

Thank you
FEQ

---

### Post by FEQ on 2010-11-29
FIXED...

After much frustration it appears that after I re-booted the machine and then replaced the BRW78E4008F3786 in the URI with the actual IP address again, everything is fine... 


hope this helps someone else.

---

