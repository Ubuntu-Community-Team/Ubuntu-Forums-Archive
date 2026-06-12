---
title: "VT8251 SouthBridge"
date: 2005-11-07
forum: Hardware &amp; Laptops
---

### Post by jsradley on 2005-11-07
Hi,
Anyone know when the new VIA VT8251 SouthBridge will be supported.
I have just purchased a ASUS A8V-MX MoBo with one of these chips and at present can not find any version of Linux that will install, even with a PATA disk fitted, although Sun Solaris Express does install OK to the SATA2 disk.
Tried both SATA and AHCI modes, but Kernel messages say Unknown SouthBrdge.
Thanks
John

---

### Post by Teroedni on 2005-11-07
Hey could you give some more information about your hardware

Motherboard<---very important 
ram
Graphics
Hardrive 
cdrom


and could you tell what you have done and what error your getting?

---

### Post by mathijs on 2005-11-20
I have exactly the same problem.
I have an ASUS A8V-MX motherboard, which has a VT8251 southbridge chipset. In the BIOS there are three options for the SATA mode: SATA, RAID and AHCI. Neither of them works. 
My drive, BTW, is a Maxtor Diamondmax 160 GB (Sata of course). All versions of linux I tried (suse 10, ubuntu 5.10, knoppix 4.02) fail to recognize the drive.

The weird thing is that FreeBSD recognizes the drive immediatly, so the code to handle it must be out there.

---

### Post by joycey on 2005-11-23
There have been a few discussions about this on the kernel IDE mailing list.  The VT8251 should be supported by the AHCI driver but it is not working correctly when the PCI ID is added into the kernel.  You can find a couple of posts regarding this and hopefully soon a solution here:

[http://news.gmane.org/gmane.linux.ide](http://news.gmane.org/gmane.linux.ide)

Andrew

---

### Post by jamuir on 2005-12-08
I am also suffering from this problem.  Neither Ubuntu or Gentoo can detect my hard drive.

There is some interesting discussion here:

[http://forums.viaarena.com/messageview.aspx?catid=28&threadid=68455&enterthread=y](http://forums.viaarena.com/messageview.aspx?catid=28&threadid=68455&enterthread=y)

Here is a message from VIA:

[INDENT]Dear All: VIA apologizes for the SATA support in Linux. We will release a Linux SATA patch for VT8237 to resolve the PATA support problem with the kernel default module in Fedora Core 4 in early December. The support for VT8251 SATA will be available in early next January.

Regards, Venus[/INDENT]

-James

---

