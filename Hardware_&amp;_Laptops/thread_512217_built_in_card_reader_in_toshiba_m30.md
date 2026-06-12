---
title: "built in card reader in toshiba m30"
date: 2007-07-28
forum: Hardware &amp; Laptops
---

### Post by mr_biggie on 2007-07-28
hi all i'v just installed ubuntu on a toshiba m30 that i have reasently bought and i found out that there is no support for the built in sd card reader not the built in ir, does anyone know of any work around to get them working again, thanks a bunch

---

### Post by mtn on 2007-07-31
I'm trying to get the built in sd card reader on my Toshiba Satellite Pro A120 going. I'm not having any joy tho.

I have followed a few threads without luck.

With the card in the reader, I type ***df*** in the terminal but don't seem see the card

```
user@A120:~$ df
Filesystem           1K-blocks Used Available Use% Mounted on
/dev/sda1           14421344  4212008      9476776 31% /
varrun                  253744       276               253468   1% /var/run
varlock                 253744       0                   253744   0% /var/lock
procbususb         253744       108              253636   1% /proc/bus/usb
udev                     253744       108               253636   1% /dev
devshm               253744        0                   253744   0% /dev/shm
lrm                        253744       33788          219956   14% /lib/modules/2.6.20-16-generic/volatile
/dev/sda2            42291280  38167908   1975080 96% /home
user@A120:~$ 
```

I have also tried typing ***dmesg*** but just a huge list of errors!

[Example]
```
[ 8916.976000] APIC error on CPU1: 40(40)
```

Any help or suggestions would great.

---

