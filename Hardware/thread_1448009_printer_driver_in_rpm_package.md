---
title: "printer driver in rpm package"
date: 2010-04-06
forum: Hardware
---

### Post by boondocks on 2010-04-06
I've received a printer driver which is in an rpm package.
This is for "CUPS Ver.1.1.17 or higher"
Is it possible to use this rpm package in Ubuntu?

---

### Post by slooow on 2010-04-06
Yes, have a look for 'man rpm' on the commandline in a terminal. Probably something like rpm -i <package-name> where -i stands for install. However in most cases there is a deb package available for ubuntu. Then it is dpkg -i <package-name>.

---

### Post by boondocks on 2010-04-06
Thanks for the response.
> **slooow said:**
> Yes, have a look for 'man rpm' on the commandline in a terminal. Probably something like rpm -i <package-name> where -i stands for install.
There was no man page for rpm when I did 'man rpm'.
I will have to install rpm itself.
> **slooow said:**
> However in most cases there is a deb package available for ubuntu. Then it is dpkg -i <package-name>.
There is no deb package available for this.

---

### Post by boondocks on 2010-04-06
In fact this rpm package is for:
[LIST]
[*]Fedora Core 6
[*]OpenSUSE 10.2
[*]Intel x86-32 architecture.
[/LIST]

---

### Post by lisati on 2010-04-06
I haven't used it myself, but you might find alien useful in converting the rpm package to a deb file that Ubuntu can use.
Have a look here: [https://help.ubuntu.com/community/RPM/AlienHowto](https://help.ubuntu.com/community/RPM/AlienHowto)

---

### Post by boondocks on 2010-04-06
> **lisati said:**
> I haven't used it myself, but you might find alien useful in converting the rpm package to a deb file that Ubuntu can use.
Have a look here: [https://help.ubuntu.com/community/RPM/AlienHowto](https://help.ubuntu.com/community/RPM/AlienHowto)
Thanks, I will take a look at alien.

---

### Post by boondocks on 2010-04-06
The printer driver rpm is for the Intel x86-32 architecture.
But this is a "ubuntu-9.10-desktop-amd64.iso" system.

The alien man page does not mention anything about this...
so I am wondering if I use alien to convert a 32-bit rpm on a 64-bit system.
Will this cause problems/issues?

---

