---
title: "[SOLVED] How to tell if 32 bit or 64 bit?"
date: 2008-05-14
forum: Hardware
---

### Post by kalikid on 2008-05-14
...I just don't know which one I have. I had a new motherboard installed, and the technician told me it was a 64 bit. I downloaded and burned the new Ubuntu 64 bit AMD 8.04 Hardy. It wouldn't install, and I got an error message to install the correct version.

So I downloaded the standard 8.04 Hardy, and it did install. I'm confused. Unfortunately, I'm not able to right click "my computer" properties like you can in windows to get an answer. Not knowing quite what to do, I went to Synaptic Package Manager and installed SysInfo. This tool tells me I have "Authenic AMD 1.808.339 MHz Advanced Micro Devices K8 [Athlon 64 Operton.]" The motherboard manual the tech gave me is entitled NF61S Micro 754 User's Manual. I looked it up on the internet and it "supports Athlon 64 processor."

I'm not enough of a geek to comprehend this. I'm wanting to buy a new Windows XP disk so I can dual boot and don't want to make the make the costly mistake of getting the wrong one.

How can I tell what I have for sure? Or is the fact that the Ubuntu 64 bit AMD wouldn't install pretty much the answer and I should just buy the standard desktop pc XP disk?

Thanks for your help.

---

### Post by overdrank on 2008-05-14
> **kalikid said:**
> ...I just don't know which one I have. I had a new motherboard installed, and the technician told me it was a 64 bit. I downloaded and burned the new Ubuntu 64 bit AMD 8.04 Hardy. It wouldn't install, and I got an error message to install the correct version.

So I downloaded the standard 8.04 Hardy, and it did install. I'm confused. Unfortunately, I'm not able to right click "my computer" properties like you can in windows to get an answer. Not knowing quite what to do, I went to Synaptic Package Manager and installed SysInfo. This tool tells me I have "Authenic AMD 1.808.339 MHz Advanced Micro Devices K8 [Athlon 64 Operton.]" The motherboard manual the tech gave me is entitled NF61S Micro 754 User's Manual. I looked it up on the internet and it "supports Athlon 64 processor."

I'm not enough of a geek to comprehend this. I'm wanting to buy a new Windows XP disk so I can dual boot and don't want to make the make the costly mistake of getting the wrong one.

How can I tell what I have for sure? Or is the fact that the Ubuntu 64 bit AMD wouldn't install pretty much the answer and I should just buy the standard desktop pc XP disk?

Thanks for your help.

Hi and you can use this command to see the version of Ubuntu you are using 
```
 uname -a
Linux overdrank-desktop 2.6.24-17-generic #1 SMP Thu May 1 13:57:17 UTC 2008 x86_64 GNU/Linux

```
Then you can use this command for specs on your systems cpu
```
sudo lshw
```
Example 
description: Notebook
    product: HP Pavilion dv2000 (RE277EA#ABN)
    vendor: Hewlett-Packard
    version: F.11
    serial: 2CE642160Y
    width: 32 bits

---

### Post by kalikid on 2008-05-14
overdrank, very sweet command. Thanks, much for your help. Yep, everything's 32 bits except for memory & video card. You saved my **** on this one! Cheers.

---

