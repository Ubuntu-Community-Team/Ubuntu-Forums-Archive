---
title: "External drives and linux?"
date: 2006-03-08
forum: Hardware &amp; Laptops
---

### Post by Elvish Legion on 2006-03-08
[http://www.newegg.com/Product/Product.asp?Item=N82E16817146307]("http://www.newegg.com/Product/Product.asp?Item=N82E16817146307")

Would that work for linux (with a drive in it)? I'm thinking of using it as both extra storage and a dvd burner...as the external ones are way to expensive, this is a cheaper way to do the same things

---

### Post by taurus on 2006-03-08
I don't see any problem with it since you have to connect it to a USB port anyway.  Ubuntu will probably see it as /dev/sda1 then...

---

### Post by Michael Hopcroft on 2006-03-08
[QUOTE=taurus]I don't see any problem with it since you have to connect it to a USB port anyway.  Ubuntu will probably see it as /dev/sda1 then...[/QUOTE]
I have a couple of related questions. If I have a USB 2.0 external drive attached to my system but don't know the version of my USB port, would I be better off finding a PCI USB 2.0 card and installing it there?

I also have a second USB 2.0 external drive that isn't being read at all. However, it is formatted in NTSF (or whatever the preffered Windows XP protocol is called), so that might be why. How can this data be retrieved for use with Ubuntu?

---

### Post by StefanoCole on 2006-03-09
Well Michael, I think you can detect if your USB ports are 2.0 or 1.1 with the following command from terminal:
sudo lshw

Connecting an external USB hard disc to USB 2.0 ports is much much better in particular if you intend to read/write big size files. Otherwise you will have to wait a lot of time for the transfer to end. So, if your transfer times are fast enough then probably you already have USB 2.0 ports.
If you don't have 2.0 ports on your system there is the possibility to add them via a PCI board (it is a solution for desktop computers).

About the other external USB hard disc with NTFS file system which is not recognized I cannot tell you. Just take into account that you cannot write to NTFS, you can just read from it.

Stefano

---

