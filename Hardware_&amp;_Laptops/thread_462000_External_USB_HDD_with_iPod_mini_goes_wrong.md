---
title: "External USB HDD with iPod mini goes wrong"
date: 2007-06-02
forum: Hardware &amp; Laptops
---

### Post by Jeanpaul145 on 2007-06-02
I have an external 500GB USB2.0 hdd (the internal drive is from Hitachi, but I don't know what model exactly, or the interface of the internal disk.).
I also have en old iPod Mini with a storage capacity of 4GB, connected by USB2.0 as well. If I connect one or the other, everything works fine, but if I connect the external drive first and then the iPod, the iPod isn't mounted. It also doesn't seem to appear in /dev. However, in this case the iPos DOES draw electricity from the usb port, since it charges its battery.
I use Ubuntu Feisty 7.04.
What's wrong here? I've been trying to find the error, but all I know right now is that I can't fix this on my own...:(

---

### Post by Jeanpaul145 on 2007-06-02
Bump...Anybody?:(

---

### Post by Jeanpaul145 on 2007-06-13
Still no one?

---

### Post by etienne.navarro on 2007-06-25
Plug in your ipod and then in a terminal (Applications --> Accessories --> Terminal) type
```
dmesg
```

If you ipod is being detected by Ubuntu then it will show up and tell you what disk it is, e.g. /dev/sdb1.
You can then mount it by typing (in the terminal)
```
sudo mount /dev/sdb1 /media/sdb1
```
assuming your ipod is recognized as sdb1

---

### Post by Jeanpaul145 on 2007-06-25
well...
If I do

"ls -a /dev/sd*"

while both my external HDD and my ipod are connected I get to see an "/dev/sdb" where there used to be none, suggesting that it is somehow linked to my ipod.
Yes, i don't understand it, because there is no complemental "/dev/sdb1" entry, just the "/dev/sdb".
If I connect the ipod and disconnect it, and THEN run dmesg, I get to see a nice long list of stuff that I can't make heads or tails of.

addition: Come to think of it, it's almost as if the kernel sees my ipod, but not the partition stored on that same ipod, where the music is stored.

---

### Post by etienne.navarro on 2007-06-25
After you remove your ipod type this 
```
dmesg | tail -25
```
and paste the result in this thread.

Also do
```
sudo fdisk -l /dev/sdb
```
if it gives an error try /dev/sda or /dev/sdc and paste that information here too

---

