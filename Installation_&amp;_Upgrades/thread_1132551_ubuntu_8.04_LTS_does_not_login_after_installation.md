---
title: "ubuntu 8.04 LTS does not login after installation"
date: 2009-04-22
forum: Installation &amp; Upgrades
---

### Post by hingolia on 2009-04-22
I have just installed [COLOR=red]ubuntu 8.04 LTS[/COLOR] but it does not allow me to login. It logs in momentarily but then brings me back to the login screen. I have run the same CD in live version and it works fine. I can also run the "failsafe genome" after installation. However, I cannot login to the normal mode. I think there is some problem with my graphics settings.

---

### Post by youknowwhat4q on 2009-04-22
> **hingolia said:**
> I have just installed [COLOR=red]ubuntu 8.04 LTS[/COLOR] but it does not allow me to login. It logs in momentarily but then brings me back to the login screen. I have run the same CD in live version and it works fine. I can also run the "failsafe **gnome**" after installation. However, I cannot login to the normal mode. I think there is some problem with my graphics settings.

Specs please.

---

### Post by hingolia on 2009-04-22
ubuntu
 
Release 8.04 (hardy)
Kernel Linux 2.6.24.16 generic
GNOME 2.22.1
 
Hardware
Memory: 439.0MiB
Processor: AMD Athlon(tm) 64 Processor 3200+
 
System Status
Available disk space: 31.9GiB
 
In the device drivers it says 
 
ATI Fire GL Enabled Not in use

---

### Post by youknowwhat4q on 2009-04-22
Ok, I am assuming  that you have a log in screen and that is how you are able to access fail-safe.  

Enter the following code in to the terminal and paste the results in to this thread.

```
lspci -v
```

---

### Post by hingolia on 2009-04-22
> **youknowwhat4q said:**
> Ok, I am assuming that you have a log in screen and that is how you are able to access fail-safe. 
 
Enter the following code in to the terminal and paste the results in to this thread.
 
```
lspci -v
```
 
 
Cannot copy paste, since ubuntu does not allow me to do configure my TCP/IP settings and go on to the internet.
 
This is some of what I see:
 
VGA Compatible Controller: ATI Technologies Inc RS480 [Radeon Xpress 200G Series] (prog-if 00 [VGA Controller])
 
Subsystem: HP Company Unknown Device 3009
Flags: Bus master, 66MHz, medium devsel, latency 64, IRQ 16
Memory at d00000000 (32-bit, prefetchable) [size=128M]
i/o ports at cc00 [size=256]
Memory at fdaf0000 (32-bit, non-prefetchable) [size=64K]
[virtual] Expansion ROM at fda00000 [disabled] [size=128K]
Capabilities: <access denied>

---

### Post by hingolia on 2009-04-22
> **youknowwhat4q said:**
> Ok, I am assuming that you have a log in screen and that is how you are able to access fail-safe. 
 
Enter the following code in to the terminal and paste the results in to this thread.
 
```
lspci -v
```
 
Display controller: ATI Technologies Inc Unknown device 5854
Subsystem: HP Company Unknown device 3008
Flags: 66MHz, medium devsel
Memory at c8000000 (32 bit, prefetchable) [disabled] [size=128M]
Memory at fdae0000 (32 bit, prefetchable) [disabled] [size=64K]
Capabilities: <access denied>

---

### Post by hingolia on 2009-04-22
> **youknowwhat4q said:**
> Ok, I am assuming that you have a log in screen and that is how you are able to access fail-safe. 
 
Enter the following code in to the terminal and paste the results in to this thread.
 
```
lspci -v
```
 
 
IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (prog - if 82 [Master Prip])
 
Subsystem: HP Company Unknown Device 3009
Flags: bu master, 66MHz, medium devsel, latency 64, IRQ 18
I/O ports at 01f0    [size=8]
I/O ports at 03f4    [size=1]
I/O ports at 0170   [size=8]
I/O ports at 0374   [size=1]
I/O ports at e400   [size=16]
 
capabilities: <access denied>

---

### Post by hingolia on 2009-04-22
> **youknowwhat4q said:**
> Ok, I am assuming that you have a log in screen and that is how you are able to access fail-safe. 
 
Enter the following code in to the terminal and paste the results in to this thread.
 
```
lspci -v
```
 
 
[COLOR=red]Multimedia Audio Controller IRQ 16[/COLOR]
[COLOR=red]VGA Controller IRQ 16[/COLOR]
[COLOR=red]Ethernet Controller IRQ 16[/COLOR]
IDE Interface Serial ATA Controller IRQ 17
IDE Interface IDE Controller IRQ 18
USB Controller IRQ 19
 
**Why are there multiple devices with the same IRQ?**

---

### Post by hingolia on 2009-04-22
**[SIZE=4]1. If this is an IRQ problem then what is the solution.[/SIZE]**
 
**[SIZE=4]2. If this is simply a problem with the graphics then what is the solution.[/SIZE]**
 
 
:confused::confused::confused::confused::confused:

---

### Post by youknowwhat4q on 2009-04-22
> **hingolia said:**
> [COLOR=red]Multimedia Audio Controller IRQ 16[/COLOR]
[COLOR=red]VGA Controller IRQ 16[/COLOR]
[COLOR=red]Ethernet Controller IRQ 16[/COLOR]
IDE Interface Serial ATA Controller IRQ 17
IDE Interface IDE Controller IRQ 18
USB Controller IRQ 19
 
**Why are there multiple devices with the same IRQ?**

Woah one at a time!

Are you using on board hardware for Audio. VGA and Ethernet?  If so that could be why it is reading the way is.

> 1. If this is an IRQ problem then what is the solution.

2. If this is simply a problem with the graphics then what is the solution.

I don't know, that is what I am trying to figure out, patience.



Give the following code a try and then see if you can login:
```
sudo dpkg-reconfigurexserver-xorg
```

---

### Post by hingolia on 2009-04-23
Rather than communicating directly........via the kernels framebuffer driver. Use framebuffer? Yes/No

Tried both options but to no effect. One thing that I notice is that there are horizontal lines that appear at the top of the screen when I try to login to the normal mode.

---

### Post by youknowwhat4q on 2009-04-23
> **hingolia said:**
> Rather than communicating directly........via the kernels framebuffer driver. Use framebuffer? Yes/No

Tried both options but to no effect. One thing that I notice is that there are horizontal lines that appear at the top of the screen when I try to login to the normal mode.

Hmmm...

I had a similar sitation with the horzontal lines, but they went away as soon as I update the system...  I assume that you have updated since installing?

If not:
```
sudo apt-get install update ; sudo apt-get auto remove ; sudo apt-get autoclean ; sudo apt-get check
```

That will update then clean out the temp files, as well as see if there are any broken dependencies.

Hopefully it is as simple of a fix.

---

### Post by hingolia on 2009-04-24
Here is the reply:
 
**sudo: unable to resolve host....**
 
Tried to solve this problem by editing the hosts file (solution from another thread) but unsuccessful as the modified file cannot be saved. 
 
failsafe genome is working OK accept for update manager gets stuck.

---

### Post by guitaria on 2009-07-18
I am having the same problem! Can someone please help me I can give specs and more details on my problem
 
Thank You

---

