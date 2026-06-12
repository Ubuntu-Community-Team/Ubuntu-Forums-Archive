---
title: "Modem Blaster Drive"
date: 2008-01-15
forum: Hardware &amp; Laptops
---

### Post by ser_virtual on 2008-01-15
Hi there, 

I`m trying to configure a Creative Modem Blaster DI5633 dial up modem, which is a pciwinmodem with an HCF Conexant chipset.
I downloaded and installed the hcfpcimodem driver provided as free by Linuxant and it seems to have been correctly installed but when trying to dial nothing hapens. 

What can I do?

---

### Post by MikRose on 2008-03-17
Hi, I have been experimenting with modems on a dual-boot for several months and have had my ups and downs.  I know that one modem/driver from Linexant for my Conexant chipset (my internal Conexant modem) works for one version of Linux, and not on others, and that is the source of my troubles!!  

The only thing I can suggest for you is to ask if you have edited the "wvdial" file so it knows the phone number to dial, your username and password for the isp?  This is something I have learned, but maybe you've already done this since it's usually listed in the "how-to's" for installing a modem.  

You need to set Permissions for the "wvdial" file so you can edit it,
Open that file and enter your information (sometimes the username is *@isp, and sometime just *)
Save the file,
Then try the modem.

If this is too simplified coming from a semi-newby, I'm sure someone will set us straight!

---

