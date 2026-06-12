---
title: "Accessing a Moto G Stylus"
date: 2023-03-28
forum: Hardware
---

### Post by Autodave on 2023-03-28
This is the first one that has stumped me.....maybe because it is the first Moto cellphone that I have had.  I have an extra memory card in it for storing pics and videos.  However, I cannot figure out a way on Linux or Win 11 to copy them from the phone to my PC.  Anyone out there have any experience with this phone and copying files from it to Linux?

---

### Post by #&amp;thj^% on 2023-03-28
Shotwell always pop's up for me on my Moto G7 and dose it automatically.
Also check if:
```
 apt policy mtp-tools
mtp-tools:
  Installed: 1.1.19-1build1
  Candidate: 1.1.19-1build1
  Version table:
 *** 1.1.19-1build1 500
        500 http://us.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages
        100 /var/lheib/dpkg/status

```
There is another step I need when accessing from my computer, pulldown from top panel on phone and make sure file transfer and not Charge only is selected.
a snip from "lsusb"
```
Bus 003 Device 009: ID 22b8:2e82 Motorola PCS XT1541 [Moto G 3rd Gen]

```

---

### Post by ian-weisser on 2023-03-28
I've had Moto phones for years.

Plug in the phone.

On the phone, select "Use USB for: File Transfer"

Then the Moto shows up immediately in Ubuntu's File Manager. Click on it, and see both Internal Storage and (add-on) SD Card.

---

### Post by Autodave on 2023-03-28
> **ian-weisser said:**
> I've had Moto phones for years.

Plug in the phone.

On the phone, select "Use USB for: File Transfer"

Then the Moto shows up immediately in Ubuntu's File Manager. Click on it, and see both Internal Storage and (add-on) SD Card.


I almost replied to this and then I figured that I would try it ONE more time......I had tried it yesterday AND this morning with no luck......and it decided to work this time.  Why?  Dunno.  I hate cell phones.

Thanks for the help from both of you!

---

