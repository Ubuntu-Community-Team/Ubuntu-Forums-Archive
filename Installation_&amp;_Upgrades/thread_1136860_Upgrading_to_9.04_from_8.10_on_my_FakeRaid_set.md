---
title: "Upgrading to 9.04 from 8.10 on my FakeRaid set"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by nkalogridis on 2009-04-25
I upgraded my ubuntu 8.10 to the newly release 9.04. Everything went well but on reboot I got thrown at initramfs prompt. Investigating the problem I found the solution and I post it here in case someone has similar problems. 

**Problem**: 
The dmraid was not mounting the fakeraid devices and hence the system could not proceed booting. The temp solution was to execute:
```
dmraid -ay
```on the initramfs prompt and then 
```
exit
```That solved the booting problem but that meant I had to do that each time I rebooted.

**Cause**:
It appears that the new dmraid package that was installed during the upgrade is a little picky when you mount fakeraid devices that where previously initialized by other controllers. In my case I had a sil fakeraid controller on my previous motherboard and the new motherboard has the intel fakeraid controller. dmraid found both signatures on the drive and for some reason upon boot it didn't mount the devices. To see if you have a similar problem you can issue:
```
sudo dmraid -r -c
```if the result is something like this 
```
/dev/sda: "sil" and "isw" formats discovered (using isw)!
 /dev/sdb: "sil" and "isw" formats discovered (using isw)!
/dev/sda
 /dev/sdb
```then you probably having the same problems as me

**Permanent solution**:
Was to remove the old signatures of the sil controller (as I dont even need them anymore) from my hard disks. That fixed the booting problem. In order to remove the signature I used the following:
```
sudo dmraid -f sil -r -E
```(you should change the sil to whatever your old controller was).
[COLOR=Red][B]
WARNING !!![/B][/COLOR]: Please make sure that you remove signatures of controllers that you **don't need** to access  the partitions of the raid devices. Also please make sure that you understand what you are doing before executing any of the above commands. I don't want to cause any problems on your drives.

Hope this helps someone else in the same position

---

### Post by elproducto on 2009-05-04
Thank you so much I thought I would never figure this thing out.

---

### Post by pablolie on 2009-05-09
> **elproducto said:**
> Thank you so much I thought I would never figure this thing out.

for what it is worth, this piece of advice came too late for me on my dual boot. i entirely uninstalled Ubuntu.

i have tried to reinstall 9.04 onto my faeraid with the alternate CD, but the installation process will not even see the RAID drive i have configured in BIOS, and which both 8.04 and Vista had no problem detecting.

oh, i was also running 64 bit.

for now i am ununtuless on my main machine, courtesy of 9.04's fakeRAID handling...

---

### Post by moz_21 on 2009-06-23
Thanks for this, I am finally able to boot 9.04 without it dropping to BusyBox and having to dmraid -ay every time!

I really wish I had known this before since I figured out the way around it the first time, which was dd if=/dev/zero of=/dev/sdx, and it took forever.

---

