---
title: "CPU won't initialize on Lenovo G560"
date: 2011-03-15
forum: Hardware
---

### Post by azeam on 2011-03-15
Occasionally my Lenovo G560 won't start, it happens every 20-30 boots or so. It can find my hard drive, which is an Intel SSD drive (not the original drive), and if I choose recovery mode it stops at: 

```

azeam-Lenovo-G560 kernel: [    0.338802] Booting Node   0, Processors  #1

```

and what should happen after that is this:

```

azeam-Lenovo-G560 kernel: [    0.349026] Initializing CPU#1
azeam-Lenovo-G560 kernel: [    0.446720]  #2
azeam-Lenovo-G560 kernel: [    0.456857] Initializing CPU#2
azeam-Lenovo-G560 kernel: [    0.554543]  #3
azeam-Lenovo-G560 kernel: [    0.564679] Initializing CPU#3
azeam-Lenovo-G560 kernel: [    0.662302] Brought up 4 CPUs
azeam-Lenovo-G560 kernel: [    0.662305] Total of 4 processors activated (19154.89 BogoMIPS).

```

But it just stays there before initializing the CPUs, can't reboot or do anything. Tried to unplug all power sources, load default BIOS settings, different kernel versions etc. but it doesn't help. 

However, if I open up the laptop, unplug the hard drive and put it back in, the computer boots normally again, which leads me to believe that the SSD drive is somehow causing this. 

Because of the interval of 20ish boots between the problems I'm thinking that the fsck check could have something to do with it, but at the same time it doesn't make sense that it would cause problems with the CPU initializing process, or could it? The laptop is fairly new (I've had it for a couple of months) but I've only seen the fsck check run at boot once since I got it and considering the amount of times I've rebooted it should have been running much more often than that. Could that one time have been an exception and the fsck check is causing this and unplugging the drive resets the number of boots before the next check (and crash)? Any other ideas to what might be causing this?

---

### Post by winuxworx on 2011-08-05
I'm also experiencing this similar error at boot up.

every once in a while like once/10 bootups the error occurs.

when it boots its displays this menu of alternating normal and recovery mode bootup. when i choose normal boot up, its doesn't proceed to booting up the Ubuntu OS but only a black screen with cursor blinking at the top right corner. when i choose (recovery mode) it displays logs of whats going on like

Initializing cgroup subsys memory
Initializing ...
CPU: Physical Processor ID: 0
CPU: ...
mce: CPU supports...
CPU0: ...
using mwait in idle threads.
Performance Events: ...

... version:
... bit width:
... value mask:
... max period:
etc. etc. until
Booting Node   0, Processors #1


and stops right there.  What could be causing this problem? I tried to retry to reboot and this happens repeatedly until on arround 10th-15th it boots ok now.  Then this will be ok until the next 3 days its will get the same errors again.

Another thing happens is every once in a while when i'm using it after like arround 5 hours or so it will stop and freez then display changes to grey. after 3 sec, it goes back to normal. this happens every day after using it arround 5 hourse or so.

All this symptoms doesn't happen when i boot to windows 7

Is there any known problem in dual boot with ubuntu and windows?
Is there any known bugs on ubuntu?
I don't think its a hardware issue since some other guys with different unit is having the same exact problem.

btw, i'm using Compaq Core i3 processor
2 gig of ram
dual boot with ubuntu 10.10 and windows 7 pro

Thanks

---

### Post by mosestruong on 2011-08-17
I'm also getting this error, I'm using a G560 with intel core i5, 64bit ubuntu 11.04.:(

---

### Post by khanx on 2012-03-08
Hello!

I'm getting the same error with my system:


[INDENT]
System   
--------------------------------------------------------------------------------
 
  Manufacturer Hewlett-Packard 
  Model HP Pavilion dv7 Notebook PC 
  Total amount of system memory 4,00 GB RAM 
  System type 64-bit operating system 
  Number of processor cores 4 
 
Graphics   
--------------------------------------------------------------------------------
 
  Display adapter type ATI Mobility Radeon HD 4650 
  Total available graphics memory 2799 MB 
        Dedicated graphics memory 1024 MB 
        Dedicated system memory 0 MB 
        Shared system memory 1775 MB 
  Display adapter driver version 8.930.0.0 
  Primary monitor resolution 1600x900 
  DirectX version DirectX 10 
 
[/INDENT]

Can't even boot it with recovery. When it comes to processor loading it says that it's loading Node #1 and then Node #2...

After Node 2 the whole pc shuts down.

How do I send a detailed report ? There was a file in /var/log/X...

---

