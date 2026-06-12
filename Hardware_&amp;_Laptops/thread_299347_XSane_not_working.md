---
title: "XSane not working"
date: 2006-11-14
forum: Hardware &amp; Laptops
---

### Post by starNIX on 2006-11-14
So here's the deal.  My HP Scanjet 5300C worked fairly well under dapper but now in edgy,  xsane cannot find it.  

It shows up under device manager.

It shows up under "lsusb"

sane-find-scanner produces:
found USB scanner (vendor=0x03f0, product=0x0701) at libusb:003:005

Whats going on?  Is the xsane in Edgy just broken?  If so,  can I downgrade?  I really need my scanner back.

---

### Post by yabbadabbadont on 2006-11-14
What does "ls -lR /dev/bus/usb" output?

---

### Post by starNIX on 2006-11-19
I will have to get back to you on that.  I swapped my old dapper drive back in so I can use everything but I still have edgy on a different HD.

---

### Post by dyrer on 2006-11-29
I have same problem too with 6.10
/dev/bus/usb:
total 0
drwxr-xr-x 2 root root 80 2006-11-29 19:25 001
drwxr-xr-x 2 root root 80 2006-11-28 22:12 002
lrwxrwxrwx 1 root root 14 2006-11-28 22:12 devices -> .usbfs/devices

/dev/bus/usb/001:
total 0
crw-rw-r-- 1 root root    189, 0 2006-11-29 00:12 001
crw-rw-r-- 1 root scanner 189, 5 2006-11-29 19:32 006

/dev/bus/usb/002:
total 0
crw-rw-r-- 1 root root 189, 128 2006-11-29 00:12 001
crw-rw-r-- 1 root root 189, 130 2006-11-28 22:12 003

---

### Post by yabbadabbadont on 2006-11-29
> **dyrer said:**
> I have same problem too with 6.10
/dev/bus/usb:
total 0
drwxr-xr-x 2 root root 80 2006-11-29 19:25 001
drwxr-xr-x 2 root root 80 2006-11-28 22:12 002
lrwxrwxrwx 1 root root 14 2006-11-28 22:12 devices -> .usbfs/devices

/dev/bus/usb/001:
total 0
crw-rw-r-- 1 root root    189, 0 2006-11-29 00:12 001
crw-rw-r-- 1 root scanner 189, 5 2006-11-29 19:32 006

/dev/bus/usb/002:
total 0
crw-rw-r-- 1 root root 189, 128 2006-11-29 00:12 001
crw-rw-r-- 1 root root 189, 130 2006-11-28 22:12 003
Is your user a member of the scanner group?  Use "id username" to see your current group memberships.  If you are not a member of the scanner group, add yourself to it using, "sudo gpasswd -a username scanner".  You will have to log out and back in for the change to take affect.

---

### Post by dj1120 on 2006-12-01
I am also having a problem with Xsane. when I try to scan it just sits there and does nothing but when I scan thru the Gimp the scanner works. I uninstalled and reinstalled it to no avail does anyone  else have this problem?

---

### Post by hardyn on 2006-12-01
I spend too long trying to get my PSC1210 working, finially i did using the newest Hp drivers, not from Hp of course, but the name of the project escapes me.  and i did have to cycle the power on the scanner, it would not detect before this; i have no idea why.

---

### Post by Giblet5 on 2006-12-12
I'm having the same problem.

ScanJet 5300cxi

sane-find-scanner finds the ScanJet at libusb:005:006 but xsane can't find any scanner.

For what it's worth, the ScanJet doesn't work under Vista either. HP's software blows chunks and Vista fails to "locate a solution for this problem".

I had to dig up an XP box to scan some docs. ](*,)

---

### Post by linuxeiro on 2006-12-12
I have an Epson Perfection V10 scanner, and I have the same problem. Xsane fails to work. It crashes. We will have to wait for this bug to be solved.

---

### Post by starNIX on 2006-12-13
The weird part is that it works fine in Dapper.  It is broken however in Edgy.  So its not that they don't know how to make it work in LINUX,  but something has changed that has broken it.

---

### Post by dolphinsonar on 2007-01-15
Yes, Epson CX5400 Printer Scanner scanned in Dapper, not in Edgy, I can't find an answer anywhere.

---

### Post by jdmpike on 2007-01-18
I have the same problem here, though I am confident the scanner worked in 64-bit Edgy. I have moved my printer/scanner in my office on my 32-bit laptop and now xsane cannot locate any devices.

I hope one of the Linux masters in our community can help us debug this issue.

Peace, love, ubuntu,

jdmpike

---

### Post by jdmpike on 2007-01-20
Just following up a little bit.

Is there a bug associated with this? This is pretty high profile for me as it was something that changed semi-recently that broke what was fixed.

Can anyone help us out here?

Thanks so much,

jdmpike

---

### Post by producer on 2007-06-20
I've been trying for years to get my HP5300c working in any linux.  It's there in Hardware, xsane can't find it and my user *is* in the scanner group.  Someone was telling me that it was an avision scanner really and I should use that "backend", whatever a backend is.  Other people have told me that an Lide scanner won't work because of some kernel bug that requires a very complicated Kernel rebuild.
I would buy a new scanner, but I have no confidence that they would work either.   Yes, I had a little functionality under edgy, or was it Dapper(?), but only at 300dpi resolution.  Now even that is completely gone.
SOmebody else has said the Epson scanners work, *except* the Perfection 660.  Not exactly perfection, but I'm considering the 4490, bacuse it handles film well, allegedly.
Please somebody tell us what needs to be done.  If the HP 5300c could be made to work that would be great.  I really need a functioning scanner!

---

### Post by producer on 2007-06-22
OK it's a kernel problem, they changed it to get some bar code readers to work and they broke the HP5300c support.  Can someone recommend a good scanner that will work with Ubuntu Feisty Fawn (7.04)?  I've been wondering about the Epson Perfection 4490 Photo Scanner, but I can't find anyone to tell me if it's supported for sure.  I'd hate to order it and get it home and find that it didn't work, and then have 2 scanners that don't work and be out the $250 plus tax.  I need to scan photos, slides, and negatives, and maybe some text, but OCR is not a big deal and I don't need anything with document feeders or office attachements.  Some good resolution and colour depth would be good.

---

