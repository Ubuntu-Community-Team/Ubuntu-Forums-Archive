---
title: "Newbie Drivers Question"
date: 2009-02-14
forum: Hardware
---

### Post by rwfnetworking on 2009-02-14
Hey guys,

Awhile back I was looking for a way to get a Netgear WN511t PCMCIA Wireless card working under Ubuntu and came across this web site:

[http://madberry.org/2008/11/how-to-get-the-netgear-wn311t-to-work/](http://madberry.org/2008/11/how-to-get-the-netgear-wn311t-to-work/)

Apparently there is a means to use the Windows driver to make a Ubuntu driver, am I reading that right?  Is it possible to do this with other types of hardware as well?  I have nothing specific in mind, but although this web site detailed the WN311t, I was able to get the WN511t drivers extracted using  the same method and successfully got my WN511t working. My only issue was my PCMCIA card would not auto-connect at boot up and the only way it would work was to remove and insert the card.



Thanks,

Robert

---

### Post by geraldm on 2009-02-14
The referenced site uses ndiswrapper to create a "wrapper" around a binary file,
and through this wrapper, the binary might exist within the kernel.

This method is very controversial, because the kernel's license is GPL, and the
binary file can only be used as untrusted code.  Untrusted code does not belong in the kernel, and some would argue that even with a wrapper, it does not belong in the kernel.  This is kind of a last resort type of situation: the manufacturer does not want to disclose the specifications for the hardware it is selling, and so no driver can be written for it.  Sometimes a person would reverse-engineer the device, and then that source can be used if correctly licensed.  

The underlying issue is that the unknown hardware can have undisclosed problems, and remains a threat to the security of the machine it runs on.
A computer user should not be subjected to unnecessary risk.  
Good advice would be to avoid the ndiswrapper situation.

You can find a lot more information available on www.

---

