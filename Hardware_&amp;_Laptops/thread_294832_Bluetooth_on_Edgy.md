---
title: "Bluetooth on Edgy"
date: 2006-11-07
forum: Hardware &amp; Laptops
---

### Post by cbudden on 2006-11-07
Hey.

Since I have used edgy, I have had bluetooth problems.  I have a w810i phone, and I can send files to the phone from my laptop, but my phone cannot see the laptop if I try to send a file to it.  It worked fine in dapper and my phone can see the machine fine using a Dapper live CD.

Whats up?

Thanks in advance.

Chris B

---

### Post by graz848 on 2006-11-17
I have EXACTLY the opposite problem: can easily send files from my k750i to computer but gnome-obex-send doesn't see my mobile when trying to send something from pc. All was right in Dapper.
Help us please!!! :) thanxx

---

### Post by flapane on 2006-11-18
> **cbudden said:**
> Hey.

Since I have used edgy, I have had bluetooth problems.  I have a w810i phone, and I can send files to the phone from my laptop, but my phone cannot see the laptop if I try to send a file to it.  It worked fine in dapper and my phone can see the machine fine using a Dapper live CD.

Whats up?

Thanks in advance.

Chris B

same problem here
DAMN

---

### Post by Burkey on 2006-11-22
> **graz848 said:**
> I have EXACTLY the opposite problem: can easily send files from my k750i to computer but gnome-obex-send doesn't see my mobile when trying to send something from pc. All was right in Dapper.
Help us please!!! :) thanxx

Me too! I have a K610i  Looks like this is a bug in Edgy.. to add insult to injury, it is marked in some places there as FIXED.. with the very next comment being people saying it is NOT fixed.

---

### Post by mario_7 on 2006-11-22
All I have to do to be able to see my phone on the dropdown list is (while send to... window is opened) to take mobile and refresh services offered by PC (then the phone pings PC and usually appears on the list).

---

### Post by flapane on 2006-11-25
> **cbudden said:**
> Hey.

Since I have used edgy, I have had bluetooth problems.  I have a w810i phone, and I can send files to the phone from my laptop, but my phone cannot see the laptop if I try to send a file to it.  It worked fine in dapper and my phone can see the machine fine using a Dapper live CD.

Whats up?

Thanks in advance.

Chris B

bump

---

### Post by cbudden on 2006-12-03
Anyone got any further with this?

---

### Post by GenX on 2006-12-04
Can you tell me how to create a bluetooth internet connection from my Sony W600i to my laptop that has built in bluetooth?

---

### Post by allanlewis on 2006-12-04
> **GenX said:**
> Can you tell me how to create a bluetooth internet connection from my Sony W600i to my laptop that has built in bluetooth?
GenX,

There are plenty of tutorials on this topic around the forums - try searching for "bluetooth internet" or similar. My question at the beginning of this thread was about my phone not being able to see my PC, and not the other way round - which is what you want to do.

Good luck!

Anyway, has anyone made any progress as to what changed in Edgy?

---

### Post by flapane on 2006-12-04
no:(

---

### Post by cbudden on 2006-12-04
Is there an existing bug report?  If there isn't what package should the bug be submitted under?  bluez-utils?

---

### Post by elektronaut on 2007-01-06
[Launchpad Bug is here.](https://launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/70718) Pay attention to Marcel's workarounds.

---

### Post by wolfchri on 2007-01-13
Just add Marcels workaround to /etc/rc.local in order to get rid of this problem without having to jump to the command line every time.

See my  /etc/rc.local as a example:
```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

# to detect the card reader on the HP NX6325
setpci -s 02:04.2 4c=0x22

# to work around the nasty bluetooth bug in Edgy 
hciconfig hci0 inqmode 0

exit 0
```

---

### Post by flapane on 2007-01-13
i am not at home, can't wait to try this workaround!!!

---

