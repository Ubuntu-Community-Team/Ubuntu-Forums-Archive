---
title: "how to disable internal wifi card."
date: 2011-11-15
forum: Hardware
---

### Post by c2tarun on 2011-11-15
Hi friends.
I am using ubuntu 11.10. I have a internal wifi card of broadcom. It is really awful and buggy. Finally after hell lot of frustation I purchased a usb wifi adapter which is working fine.
Now I want to disable internal wifi card, because internal is also detecting wifi network and external is also. If I am connecting with internal's wifi connection my whole system is freezing.
My roommates are not so experienced in using linux so I want to disable internal wifi card completely.
Can anyone please tell me how to disable internal wifi card?

---

### Post by An Sanct on 2011-11-15
Greetings!

My guess is, you have a laptop or some sort of a portable computer. Normally, wireless connections can be shut down in BIOS. See the manual for that option or give us more info and we will help you.

---

### Post by northd_tech on 2011-11-15
Although it sounds like you are having Broadcom wireless driver module issues to me, can you copy/paste the results of these terminal commands here:

```
lspci -vvnn | grep 14
sudo lshw -C network
lsmod
rfkill list all
ls -l /etc/modprobe.d/
egrep 'b43|wl|ssb' /etc/modprobe.d/*
cat /etc/modules
dmesg | egrep 'b43|wl|irmware|oadcom|ssb|802.11|80211|ireless'
```

FWIW, I've had much better luck with most Broadcom wireless than nearly ANY USB wireless device- those can be very 'tricky' from my experience.

---

