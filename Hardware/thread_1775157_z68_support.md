---
title: "z68 support"
date: 2011-06-04
forum: Hardware
---

### Post by then_dude on 2011-06-04
hello

i need a hardware upgrade, after 6 years my machine is very slow when virtualizing. 

i would like to buy a z68 chipset with a 2500k.
it will be an asrock z68 pro3 board. 

has anybody this setup running ? or this chipset and are there any know problems ? 

thanks so much

---

### Post by frans s on 2011-06-23
Hi 

I have just bought exactly this configuration.

windows runs ok but can not get ubuntu 64  b to work 
Using ubuntu 11.04 .
During installing the screen freezes and the only way out is to hard reset.

after numerous attempts I have it up and running but still freezes every 5 minutes

very frusty 

hope that running the updates will help 

any one same experiencing ( and hopefully a solution)

cheers

---

### Post by psusi on 2011-06-23
I believe the z68 is just a rebranding of the p68, which I have had working well since January.

---

### Post by abc1987 on 2011-06-26
I have an Asus P8Z68-V board and Ubuntu boots fine into the live CD with discrete graphics (my nVidia GeForce GTX 570). However it freezes on booting once installed. I have the motherboard's integrated graphics enabled as well though, so I'm going to try turning them off in case they're confusing it.

---

### Post by exobuzz on 2011-06-28
this may be relevant for you. after disabling the gpu power saving code in the kernel, my system runs without crashes/freezes.

[https://bugzilla.kernel.org/show_bug.cgi?id=38492](https://bugzilla.kernel.org/show_bug.cgi?id=38492)

---

### Post by exobuzz on 2011-06-28
> **psusi said:**
> I believe the z68 is just a rebranding of the p68, which I have had working well since January.

the z68 is a new chipset combining features of the p67 and h67. Did you mean p67 anyway ? it is not the same as that.

---

### Post by exobuzz on 2011-06-28
here's my current running kernel with my changes to disable power saving. Be interested to know if it helps you also - and hopefully we can get a proper fix for this soon.

[http://malus.exotica.org.uk/~buzz/ubuntu/kernel/z68/](http://malus.exotica.org.uk/~buzz/ubuntu/kernel/z68/)

---

### Post by frans s on 2011-06-29
thanks exobuzz , yes this is exactly what is happening.

However your solution is just a bridge to far for me 

I have no experience with changing the code and recompiling in linux ,any hits where to start to get this done or should i just wait until 11.10 ( and hope it's fixed)

---

### Post by exobuzz on 2011-06-29
See the link above. I uploaded my kernel. you can download the debs and install them from a terminal with "sudo dpkg -i filename.deb"

note if you have the asrock board, you should also download the tar.gz in the same folder. once booted, unpack it and do "sudo ./autorun.sh" to install - the vendor wireless works better than the in kernel one.

---

### Post by ratcheer on 2011-06-29
> **then_dude said:**
> hello

i need a hardware upgrade, after 6 years my machine is very slow when virtualizing. 

i would like to buy a z68 chipset with a 2500k.
it will be an asrock z68 pro3 board. 

has anybody this setup running ? or this chipset and are there any know problems ? 

thanks so much

I am running on a Gigabyte Z68A-D3-B3 with an Intel i5 2500. I had a lot of problems at the beginning, but after everything was solved, nothing can really be blamed on the chipset or CPU.

The DVD drive was plugged into a SATA III port and Linux would not deal with it at all. It had run fine that way on Windows 7. After I replugged it into a SATA II port, it worked.

Ubuntu 11.04 64-bit chose incorrect drivers for both the ethernet NIC and the wireless PCI card. I had to download the correct drivers and make new modules.

Now, everything is running very well. 

Tim

---

### Post by exobuzz on 2011-06-29
> **ratcheer said:**
> I am running on a Gigabyte Z68A-D3-B3 with an Intel i5 2500. I had a lot of problems at the beginning, but after everything was solved, nothing can really be blamed on the chipset or CPU.


no freezes/crashes with the gpu? If not, then the problem could be specific to these motherboards rather than the chipset.

---

### Post by ratcheer on 2011-06-29
> **exobuzz said:**
> no freezes/crashes with the gpu? If not, then the problem could be specific to these motherboards rather than the chipset.

What do you mean, "the gpu"? At any rate, I have had no issues of freezes or crashes.

Tim

---

### Post by exobuzz on 2011-06-29
> **ratcheer said:**
> What do you mean, "the gpu"? At any rate, I have had no issues of freezes or crashes.

Tim

see my earlier link to bugzilla. are you using the build in gfx ? looking at your sig i guess not. try using the intel gfx with the z68 and see how you get on. thats the issue anyway.

---

### Post by Hyper01 on 2011-07-02
> **frans s said:**
> thanks exobuzz , yes this is exactly what is happening.

However your solution is just a bridge to far for me
A more tractable workaround for you (based on exobuzz's discovery) may be: [http://ubuntuforums.org/showpost.php?p=11006756&postcount=3](http://ubuntuforums.org/showpost.php?p=11006756&postcount=3)

---

### Post by exobuzz on 2011-07-03
I don't know how i missed the kernel option. simpler like that. thanks.

---

### Post by anewbie on 2011-07-07
deleted

---

