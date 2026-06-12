---
title: "CPU Confusion"
date: 2009-12-07
forum: Hardware
---

### Post by mikemikemike on 2009-12-07
I am having a lot of system spec confusion. 

One program claimed I only have a 1.00Ghz Processor. Which is false. Its at least 1.73Ghz Processor.

**sudo lshw **tells me :  
```
 *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 CPU         T5300  @ 1.73GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Core(TM)2 CPU         T5
          slot: U2E1
          size: 800MHz
          capacity: 2048MHz
          width: 64 bits
```Now heres my question. Shouldn't the results include both cores? (see example below, not my processor speeds) : 

```
_processor    : 1_
vendor_id    : GenuineIntel
cpu family    : 6
model        : 23
model name    : Intel® Core™2 Duo CPU     E7200  @ 2.53GHz
stepping    : 6
cpu MHz        : 2527.000
 _processor    : 0_
vendor_id    : GenuineIntel
cpu family    : 6
model        : 23
model name    : Intel® Core™2 Duo CPU     E7200  @ 2.53GHz
stepping    : 6
cpu MHz        : 1596.000

```Under System Monitor its reads 2 Cores Each T5300 at 1.73Ghz,



I just want to make sure that I am running at max capacity. 


Thank you everyone.

---

### Post by HappyFeet on 2009-12-07
It does show 2 cores. You are fine.

---

### Post by mikemikemike on 2009-12-07
instead of making a new thread I will ask here. 

I know it can be dangerous and often not smart to edit things you don't know about but the tweak

**Tweak**
 
[LIST]
[*]First we have to gain access to your /etc/sysctl.conf file.
[/LIST]
 [URL="http://www.salatti.net/tweak-ubuntu-for-speed#about"]
[/URL]

```
sudo gedit /etc/sysctl.conf
```


 
[LIST]
[*]Just scroll to the bottom of the page and add the tag listed below. The number you want depends on how much ram you have and what you do with your system. Please read the about above this to make your decision. I have mine set to 0 on a dual core laptop with 1 gig of ram and have seen no issues and a good performance gain.
[/LIST]
 ```
vm.swappiness=0
```


This entire file contains the symbol ' # ' . Before I add this entry at the bottom, should it have a ' # ' and also a blank space in front of it?

---

### Post by Yellow Pasque on 2009-12-08
If you want the line to be read, then you won't have any '#' in front of it, because those lines are marked as comments.

Also, set swapiness to 10 or 20, but not 0.

---

### Post by mikemikemike on 2009-12-08
Just curious, why not 0? Like the user above I have 1gb ram and dual core.

---

### Post by gradinaruvasile on 2009-12-08
I dont think that its really that good idea for beginners to make this sort of changes...

And i wouldnt worry about the max speed. Bear in mind that newer Linux kernels have built-in CPU governors and the default is ondemand i think. Governor means CPU speed control essentially. Most CPUs support a thing called stepping - it has more speeds levels (3-4). 
I for example use a Dell D630 laptop that has Core2Duo T7300 CPU - It has a max speed of 2 GHz. But in idle mode (when not loaded) it runs at 800 MHz.
This way it cools down very well and doesnt consume much power.
But if i use CPU intensive apps it raises its speed to 2 GHz.

This is a good thing especially for laptops.

Probably you have a stepping level of 1.0 GHz when idle. That was reported by that program. There are many programs that can monitor/adjust the CPU speed. One of them is a nice applet that can be added to the taskbar and it shows the CPU speed levels in real time and lets you adjust the governors if you want.
Its called gnome-cpufreq-applet. Install it in a terminal:

sudo apt-get install gnome-cpufreq-applet

And then you will have the option to add it to your panel (by default it monitors cpu0, add a second one and set it to cpu1).

---

