---
title: "KQemu Not Found?"
date: 2008-10-21
forum: General Help
---

### Post by Gannon8 on 2008-10-21
I did:
```
sudo apt-get install kqemu-common
```
To install the kqemu acceleration driver. However, whenever I start Qemu, I get an error:
```
Could not open '/dev/kqemu' - QEMU acceleration layer not activated: No such file or directory
```
There are no man pages on kqemu (even after the -u argument), no kqemu command, and no kernel modules. So why isn't kqemu being started?

---

### Post by Loranga on 2008-10-27
> **Gannon8 said:**
> I did:
```
sudo apt-get install kqemu-common
```
To install the kqemu acceleration driver. However, whenever I start Qemu, I get an error:
```
Could not open '/dev/kqemu' - QEMU acceleration layer not activated: No such file or directory
```
There are no man pages on kqemu (even after the -u argument), no kqemu command, and no kernel modules. So why isn't kqemu being started?

Will your problem get solved if you install kqemu-source also?

---

### Post by HerCsD on 2008-11-23
Indeed you need to have the kqemu source also installed in order for kqemu acceleration to be run properly.Do note,however you need to run as sudo when running qemu with acceleration layer!

---

### Post by Lacoste on 2008-11-26
Thanks, this fixed my problem as well.

L

---

### Post by SneakyWho_am_i on 2009-04-04
> **HerCsD said:**
> Indeed you need to have the kqemu source also installed in order for kqemu acceleration to be run properly.Do note,however you need to run as sudo when running qemu with acceleration layer!

**Thank you** HerCsD for making my life a little bit easier.

---

### Post by nisp on 2009-05-11
> **SneakyWho_am_i said:**
> **Thank you** HerCsD for making my life a little bit easier.
Hi all !
I'm runnning Ubuntu 8.04 as well and I have installed all packages required by qemu and kemu, kqemu sources included; anyway I'm still getting (I'm running qemu as sudo):
"Could not open '/dev/kqemu' - QEMU acceleration layer not activated: No such file or directory"
Do I have to manually create such a device, I gess no. Any idea?
Thanks a lot in advance !
Nisp

---

### Post by Gannon8 on 2009-05-11
> **nisp said:**
> Hi all !
I'm runnning Ubuntu 8.04 as well and I have installed all packages required by qemu and kemu, kqemu sources included; anyway I'm still getting (I'm running qemu as sudo):
"Could not open '/dev/kqemu' - QEMU acceleration layer not activated: No such file or directory"
Do I have to manually create such a device, I gess no. Any idea?
Thanks a lot in advance !
Nisp

Please post in your own thread. This one is too old.

I think I still have that problem, but I don't use emulation anymore (computer is too slow)

So, yeah, no one post here.

---

