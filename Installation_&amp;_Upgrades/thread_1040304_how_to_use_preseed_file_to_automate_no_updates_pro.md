---
title: "how to use preseed file to automate no updates prompt?"
date: 2009-01-15
forum: Installation &amp; Upgrades
---

### Post by gsegree on 2009-01-15
I have successfully created a preseed file to make my ubuntu 8.10 installation pretty much unattended but during the install I'm being prompted twice.
1. Setup an encrypted private directory? 
[INDENT][I][LIST]
[*]Yes
[*]No
[/LIST][/I][/INDENT]
2. Do you want to allow automatic updates? 
[INDENT][I][LIST]
[*]No Automatic Updates
[*]Install Updates Automatically
[*]Manage system with Landscape
[/LIST][/I][/INDENT]

How can I provide an answer automatically for these 2 questions?

---

### Post by nickbooker on 2009-01-27
I'm not sure about the encrypted directory question, but for the unattended upgrades question try this:
```
d-i pkgsel/update-policy select none
```

---

### Post by MountainX on 2009-02-25
> **gsegree said:**
> I have successfully created a preseed file to make my ubuntu 8.10 installation pretty much unattended
where can I learn about doing this? Thanks

---

### Post by Curtor on 2009-07-09
[https://help.ubuntu.com/9.04/installation-guide/powerpc/preseed-using.html](https://help.ubuntu.com/9.04/installation-guide/powerpc/preseed-using.html) shows how to do a preseed.

From what I have googled, 
d-i user-setup/allow-password-weak boolean true
allows you to use a weak password without getting prompted, and
d-i user-setup/encrypt-home boolean false
says not to encrypt the home directory.

Right now, I am getting prompted on Ubuntu 9.04 as to if I want to unmount currently mounted partitions and format them as well. Seeing as this is the partition that I am installing from (my usb key), the answer is obviously no. But I don't know what that is yet in the preseed script.

---

