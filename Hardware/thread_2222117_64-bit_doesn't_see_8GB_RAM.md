---
title: "64-bit doesn't see 8GB RAM"
date: 2014-05-05
forum: Hardware
---

### Post by Aleksandar_Ristic on 2014-05-05
Hi,

I have installed Kubuntu 14.04 64-bit, but the system doesn't see 8GB of RAM. It shows only 4.

Configuration:

motherboard: Gigabyte B75M-HD3
CPU: 4xIntelCore i3-3240 @ 3.400Ghz 
RAM: 8GB

Any idea?

---

### Post by oldfred on 2014-05-05
Is UEFI/BIOS show all 8GB?

Some have found Linux sees issues that the other system does not see, or ignores.

Just reseating or cleaning contacts and reseating memory sometimes helps.

       sudo lshw | grep -m 1 -A 25 "*-memory"
sudo dmidecode --type memory


 Ubuntu not showing memory
look for something like "memory remap" or "memory extension" in your bios settings and enable it. It will do the trick
Memory check
wget [http://www.appelboor.com/dump/check-my-memory.py](http://www.appelboor.com/dump/check-my-memory.py)
python check-my-memory.py 
sudo python check-my-memory.py

---

### Post by Aleksandar_Ristic on 2014-05-06
Thanks oldfred,

it seems like the problem is not in Ubuntu installation, but in memory slot. I'll get a new motherboard and see if it will solve the problem.

Thnaks.

---

### Post by Yellow Pasque on 2014-05-07
It's best to use verified modules:
[http://download.gigabyte.us/FileList/Memory/memory_ga-b75m-hd3.pdf](http://download.gigabyte.us/FileList/Memory/memory_ga-b75m-hd3.pdf)

---

