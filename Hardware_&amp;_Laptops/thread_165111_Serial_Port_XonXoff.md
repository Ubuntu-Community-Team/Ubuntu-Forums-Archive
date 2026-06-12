---
title: "Serial Port Xon/Xoff"
date: 2006-04-24
forum: Hardware &amp; Laptops
---

### Post by rgmussel on 2006-04-24
I have a Thinkpad Z60t. It has no internal serial port but I have a USB to serial cable. That is attached to a null-modem cable, which is attached to a Soekris board, for which I am trying to upgrade the BIOS and flash the memory for a wireless node.

I use Minicom to connect to the serial port and I can reach the Soekris card without any problems. When I try to upload the new BIOS, the connection is cut from Minicom or the laptop, not from the Soekris board. Minicom returns "NAK not found" and "Retry timed out". I suspect, based on Soekris's website and various google searches, that there is some hardware control still on, which I know needs to be turned off. However, I have no idea how to turn XON/XOFF in this situation.

I did run "stty -ixoff", but to no avail. ](*,) 

Any suggestions?

Thanks.

Ross

---

### Post by rgmussel on 2006-04-24
The exact message I receive is:

> &#9474;Retry 0: NAK on sector                                       &#9474;
&#9474;Retry 0: NAK on sector                                       &#9474;
&#9474;Xmodem sectors/kbytes sent:   2/ 0kRetry 0: Cancelled        &#9474;
&#9474;Transfer incomplete                                          &#9474;
&#9474; READY: press any key to continue... 

Don't know if that helps someone help me. I also tried swapping cables, but to no avail.

Ross

---

