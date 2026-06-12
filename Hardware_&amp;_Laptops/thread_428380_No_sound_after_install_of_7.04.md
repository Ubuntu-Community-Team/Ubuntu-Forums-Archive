---
title: "No sound after install of 7.04"
date: 2007-04-30
forum: Hardware &amp; Laptops
---

### Post by fbaptista on 2007-04-30
Hi there,

I am quite new to Linux and installed release 7.04 on a Toshiba Satellite S1800-504 Notebook. Most HW components worked immediately, except for the sound.

I already searched forums for a solution, but so far none of them worked.

I attached some system output in order to provide more detailed info.

Thanks for your help.

Kind regards,
Fernando

---

### Post by ruien on 2007-04-30
Hi.

Had a similar problem and I want to ask you if you have sound in headset but not in laptop speakers?

If so I had the same problem and I had to flash my bios to an older version and then it worked fine. Neither opensuse, FC7 or ubuntu 7.04 worked with latest bios on this laptop wich is a Fujitsu Siemens XA1526 .

---

### Post by Mike Ozornin on 2007-04-30
> **ruien said:**
> Hi.
Had a similar problem and I want to ask you if you have sound in headset but not in laptop speakers?.
I have the same  :(

---

### Post by fbaptista on 2007-04-30
Thanks for your reply ruien, but unfortunately it didn't help.

Actually the sound card doesn't work at all, nor on loudspeakers nor on output jack, since the sound module doesn't get loaded during boot.

see following dmesg output:
[I]
[   35.964000] ali15x3_smbus 0000:00:08.0: ALI15X3_smb region uninitialized - upgrade BIOS or use force_addr=0xaddr
[   35.964000] ali15x3_smbus 0000:00:08.0: ALI15X3 not detected, module not inserted.[/I]

---

