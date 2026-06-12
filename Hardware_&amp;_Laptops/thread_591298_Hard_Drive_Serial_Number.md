---
title: "Hard Drive Serial Number"
date: 2007-10-25
forum: Hardware &amp; Laptops
---

### Post by RLovelett on 2007-10-25
Is there a way I can find my hard drive serial number.  I'm trying to run a VM to get one of my DRM locked PDF text books open.  But apparently the PDF is linked to my hard drive serial number.  So I want to extract it from Ubuntu and spoof it in my VM machine that way ***_perhaps_*** I can get my text book open before my next exam.

Or of course if someone has a way of cracking the PDF so that I don't need the DRM stuff :lolflag:

At any rate I'm just looking for the command in the terminal to retrieve my hard drive's serial number.

Thanks.

---

### Post by RLovelett on 2007-10-25
Well this just makes me feel stupid.  I was reading this thread about the [Ubuntu Hard Drive work issue.]("http://ubuntuforums.org/showthread.php?t=591230").

I ran the command
```
sudo smartctl -a /dev/sda
```

EDIT:
Need the volume serial number, not the one this command gives me.

---

### Post by Keith_Beef on 2007-10-25
> **RLovelett said:**
> Is there a way I can find my hard drive serial number.

You might get some joy from hdparm -I

K.

---

### Post by RLovelett on 2007-10-25
Ok apparently I was wrong.  That is not the serial I need.  I need the volume's serial number which is supposed to be 8 bit hex.  The number that I got was 9 digits long.  So that is not the right information.

Does anyone know how to get the volume's serial number?

---

### Post by blinan8088 on 2007-10-28
Is there a way to retrieve hard disk drive serial number without administrative privilege? I have tried hdparm and smartctl, both require 'sudo'.

Thanks in advance.

---

### Post by nick_h on 2007-10-28
Is the one given by:
```
sudo fdisk -l
```
the one you need?

---

