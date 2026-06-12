---
title: "HP nx7400 ipw3945 Wireless not functioning"
date: 2006-08-29
forum: Hardware &amp; Laptops
---

### Post by dietkinnie on 2006-08-29
Hi All,

I am new to ubuntu and it seems that my wireless isnt working. I had the same problem with fedora which i managed to solve on my other laptop, but as i said i am new to ubuntu and linux in general and would really appreciate anyones help. 

I tried installing the dirvers manually but when i tried to execute the command "make" i was shown the following... "make: command not found". It must be something stupid.


lspci -v shows the following 


0000:10:00.0 Network controller: Intel Corporation: Unknown device 4222 (rev 02)
        Subsystem: Hewlett-Packard Company: Unknown device 135c
        Flags: bus master, fast devsel, latency 0, IRQ 177
        Memory at f4000000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [c8] Power Management version 2
        Capabilities: [d0] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-
        Capabilities: [e0] #10 [0011]


uname -r shows :

2.6.15-26-386


--------------------------------------------------

I would really appreciate soma advise here,

Thanks and Best regards,

Robert.

---

### Post by ltmon on 2006-08-29
I got burnt by this one :)

The drivers already exist, don't bother installing them.  For future reference you need to install the "build-essential" package to compile anything.

The problem is the ipw3945 drivers also have a non-free component daemon that needs to be installed post-installation.  It is installed with the "linux-restricted-modules" package.  Make sure you have the "universe" section made available (especially in the dapper updates repository) and then install/upgrade the "linux-restricted-modules" package using Synaptic.

Once that's done the driver and card are very stable and have been working faultlessly for me.

L.

---

### Post by dietkinnie on 2006-08-30
Hi ltmon,

First of all thanks for you reply. I was trying do as you said but got lost and wasnt sure how to install/update the linux-restricted-modules. Well i did update some of the modules, but the wifi still isnt working.

Could you please descripe what i have to do in steps ??? I would really appreciate it !!!

Thanking you in advance.

Robert.

---

### Post by dietkinnie on 2006-09-03
Hi All,

I finally managed to configure wireless. I was using the wrong kernel. My laptop cpu is a Centrino Duo, so i had to install the following kernel using synaptic. 2.6.15-26-686 #1 SMP, after that restart your box and your card should be automatically detected.

Hope it helps someone out there.

I also installed wlassistant which is a very nice tool :cool:

---

### Post by bekiil on 2006-09-05
Good to hear that you have your wirelss working.
I got my working after installing (downloading!!) the network-manager-gnome

I have one problem, on the same laptop (NX7400 from HP)I cant load the speedstep-centrino module, it sayes:

user@nx7400:~$ sudo modprobe speedstep-centrino
Password:
FATAL: Error inserting speedstep_centrino (/lib/modules/2.6.15-26-686/kernel/arch/i386/kernel/cpu/cpufreq/speedstep-centrino.ko): No such device

I have the latest bios (F07) and the cpu is a T2400.

Hehe, Im quite sure the cpu is a centrino. Will there be a fix for this soon?
Thanks in advance.

---

### Post by bekiil on 2006-09-05
One other thing, I have completely abandoned Microsoft!. (waves goodbye)
Some person sayed to me, If you never had used Windows, and only used Linux/distro or a Mac, Windows would look as strange as "distro" do today, :)

I have the luck that i acutallly have used Linux (mostly slackware) for a few years now, in coop with Windows.

So, To the people that makes Ubuntu, Keep up the good work. Make sure that we that uses Ubuntu never gets a reason to go back to MS.

Bye.

---

### Post by ltmon on 2006-09-05
@bekiil

To get CPU frequency scaling to work on a Core Duo you need only install the SMP kernel:

```

sudo apt-get install linux-686-smp

```

Frequency scaling etc. should now work with no problem.  Speedstep-centrino will load without your intervention.

L.

---

### Post by bekiil on 2006-09-05
Done, no good, keep saying no such device

---

### Post by rsk on 2006-09-07
I don't know who else fell into this boat, but it took me 6 hours to figure out I was a moron. I had my router setup to do WAP, and kept using the gnome network manager to setup my WEP key, not realizing the difference until 10mins ago.

I changed my router to WEP, and viola, everything works out of the box.
BTW I'm on a ThinkPad T60, I've been reading these threads for hours, following up incase *anyone*, even one person had the same problem I did. (More details [here]("http://www.breakitdownblog.com/2006/09/07/ubuntu-606-thinkpad-t60-wifi-ipw3945-wepwap/"))

---

### Post by finni on 2006-11-03
> **bekiil said:**
> Good to hear that you have your wirelss working.
I got my working after installing (downloading!!) the network-manager-gnome

I have one problem, on the same laptop (NX7400 from HP)I cant load the speedstep-centrino module, it sayes:

user@nx7400:~$ sudo modprobe speedstep-centrino
Password:
FATAL: Error inserting speedstep_centrino (/lib/modules/2.6.15-26-686/kernel/arch/i386/kernel/cpu/cpufreq/speedstep-centrino.ko): No such device

I have the latest bios (F07) and the cpu is a T2400.

Hehe, Im quite sure the cpu is a centrino. Will there be a fix for this soon?
Thanks in advance.

You need to downgrade your bios to F06 to make speedstep-centrino to work. Then you need to read this topic and see it's links: [http://www.ubuntuforums.org/showthread.php?t=214301&highlight=nx7400](http://www.ubuntuforums.org/showthread.php?t=214301&highlight=nx7400).
I own a NX7400 (EY305ET#AK8) with T2400 and ipw3945 wireless. BTW, very nice laptop. :)

---

