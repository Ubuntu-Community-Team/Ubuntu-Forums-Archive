---
title: "CPU Architecture"
date: 2013-04-21
forum: Hardware
---

### Post by Lyans on 2013-04-21
Hello Gurus!
I've been testing Ubuntu (and environments) for a while now and I'm looking to do the cleanest install possible.

My Question in fact is, what is my CPU Architecture based on Intel(R) Core(TM) i5-3570k CPU.

AMD64 or i386, other?

If I'm not mistaken it is a 64-bits system.
Is downloading Ubuntu-Desktop-64bits good enough?

Thanks a Lot! :)

---

### Post by matt_symes on 2013-04-21
Hi

It's 64bit you have there :)

It's called AMD64 due to historical reasons. They are both based on the intel instruction set.

You want to download the 64 bit version.

If you decide to install it, clone your existing hard drive before if you can.

Be aware of UEFI issues. I'm sure oldfred will be along at some point to explain them to you.

Kind regards

---

### Post by Lyans on 2013-04-21
Okay! Thanks a lot, for the fast reply!

Concerning UEFI issues, I'm using a Gigabyte Motherboard booting with a BIOS setup. That should be all right.

Do you have any hardware compatibility hints for me?

---

### Post by pqwoerituytrueiwoq on 2013-04-21
since you know that much about your motherboard/motherbord i assume it is a custom build, i don't think a retail motherboard will have the "secure boot" crap enabled by default as it would prevent installing xp and windows 7 (i think it would prevent 7, not 100% sure)

i also doubt a OEM is going to give you a unlocked CPU like a 3570k

you should be able to use uefi boot if you wanted to, using BIOS works as well

i doubt you are using integrated graphics with that cpu so you may want to add the xswat ppa for newer GPU drivers for your Nvidia/AMD gpu, i am sure you have a gaming class gpu in there
```
sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
```

---

### Post by Lyans on 2013-04-22
Thanks again for your support and advice.

You're right it is a custom desktop, originally build to work under Windows 7. 
Now I'm really looking for a Linux system.

I think that might be an excellent idea for the xswat ppa, since it is Nvidia card.

Can someone explain me the big differences between UEFI and BIOS?

---

