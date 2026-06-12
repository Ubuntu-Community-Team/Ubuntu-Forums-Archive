---
title: "Nvidia 7600gt fail after memory upgrade VGN-AR390E Sony"
date: 2009-03-20
forum: Installation &amp; Upgrades
---

### Post by eisenklopf on 2009-03-20
okay so Ubuntu 8.10 32 bit was running fine then I did a memory upgrade now it gives me the line that no drivers can be initialised and has to start in low graphics mode. Sony does state that the system shipped maxed at 2 Gigs but upon benchmarking it stated that the motherboard was capable of 4 Gigs. I tried one and two sticks of the 2Gig sticks I bought and the only way it boots with graphics support is if I just drop it back to 2 gigs overall. I ran "lspci -v -s 1:00" and here are my results. 01:00.0 VGA compatible controller: nVidia Corporation GeForce Go 7600 GT (rev a1)
	Subsystem: Sony Corporation Device 81fd
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at d1000000 (32-bit, non-prefetchable) [size=16M]
	Memory at <ignored> (64-bit, prefetchable)
	Memory at d0000000 (64-bit, non-prefetchable) [size=16M]
	I/O ports at 2000 [size=128]
	Capabilities: <access denied>
	Kernel modules: nvidiafb, nvidia
any ideas would be greatly appreciated. can I change the mapping without a custom bios? can I just limit what Ubuntu sees? Windows runs great with the extra memory so I really don't want to have to take it out but for the amount of time I run windows I very well may have to.

---

### Post by tommcd on 2009-03-20
Is the 4GB memory recognized in the system BIOS? Are you sure that Windows sees all 4GB RAM? Run memtest on the new RAM. You can run it from the live CD. What is the output of:
```
free -m
```
and 
```
cat /proc/meminfo
```
A memory upgrade should not cause a problem like this, unless the memory is faulty.

---

### Post by eisenklopf on 2009-03-20
> **tommcd said:**
> Is the 4GB memory recognized in the system BIOS? Are you sure that Windows sees all 4GB RAM? Run memtest on the new RAM. You can run it from the live CD. What is the output of:
```
free -m
```
and 
```
cat /proc/meminfo
```
A memory upgrade should not cause a problem like this, unless the memory is faulty.

yes windows sees all 4 but utilizes only 3 as it it 32 bit. Ubuntu as well is 32 bit and sees 3 so I am down to 3 now as the memory is the same as the old lady's comp so she got one stick. memtest has been done with no errors. will get back on the rest in a couple of hours.Either 2 gig stick alone and Ubuntu returns to normal. As soon as I put one of the one gig sticks back in or the other 2 gig stick in is hwen the issue applies.so in end memory is fine.

---

### Post by eisenklopf on 2009-03-20
> **tommcd said:**
> Is the 4GB memory recognized in the system BIOS? Are you sure that Windows sees all 4GB RAM? Run memtest on the new RAM. You can run it from the live CD. What is the output of:
```
free -m
```
and 
```
cat /proc/meminfo
```
A memory upgrade should not cause a problem like this, unless the memory is faulty.

mark@mark-vaio:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3037        380       2657          0         14        180
-/+ buffers/cache:        185       2851
Swap:         2706          0       2706

&

mark@mark-vaio:~$ cat /proc/meminfo
MemTotal:      3110716 kB
MemFree:       2572628 kB
Buffers:         17320 kB
Cached:         236780 kB
SwapCached:          0 kB
Active:         344440 kB
Inactive:       141880 kB
HighTotal:     2226752 kB
HighFree:      1747780 kB
LowTotal:       883964 kB
LowFree:        824848 kB
SwapTotal:     2771172 kB
SwapFree:      2771172 kB
Dirty:             796 kB
Writeback:           0 kB
AnonPages:      232220 kB
Mapped:          61340 kB
Slab:            28672 kB
SReclaimable:    14556 kB
SUnreclaim:      14116 kB
PageTables:       2356 kB
NFS_Unstable:        0 kB
Bounce:              0 kB
WritebackTmp:        0 kB
CommitLimit:   4326528 kB
Committed_AS:   351428 kB
VmallocTotal:   110584 kB

---

### Post by eisenklopf on 2009-03-20
Let me assure you it has nothing to do with the memory. It is definitely something to do with Sony's configuration or hardware. Both memory modules have been tested independently and individually with multiple testing programs and both together worked like a charm in Dell D630 with Ubuntu and windows. Both modules will work fine by themselves if I only use one in this machine. It's not until I cross the 2 Gig threshold that problems occur.

---

### Post by tommcd on 2009-03-20
Your "free -m" and /proc/meminfo indicate that Ubuntu is using 3GB memory, which is about what you would expect with 32 bit Ubuntu. 
So is the video working ok now?
If not, then backup your xorg.conf, reinstall the nvidia driver, stop X,  then run "sudo nvidia-xconfig. Then restart X or reboot and see if the video is fixed.
I'm not sure  how a memory upgrade would cause a problem with your graphics card.

---

### Post by eisenklopf on 2009-03-21
> **tommcd said:**
> Your "free -m" and /proc/meminfo indicate that Ubuntu is using 3GB memory, which is about what you would expect with 32 bit Ubuntu. 
So is the video working ok now?
If not, then backup your xorg.conf, reinstall the nvidia driver, stop X,  then run "sudo nvidia-xconfig. Then restart X or reboot and see if the video is fixed.
I'm not sure  how a memory upgrade would cause a problem with your graphics card.

No not working and already done. the closest I've got is to pass mem=2048M to the kernel but then my graphics are seriously messed up. I have a blue square for my cursor, terminal is a weird transparent thing that I can't see and all lines of text are black like being censored. 3GB is all that is installed at this moment. because of the issue I haven't worried about going to 64 bit. yes same issue with 64 bit live CD.

---

### Post by tommcd on 2009-03-21
The manual for your laptop on the Sony website does say there is a max of 2 GB memory. I would guess that your computer's BIOS just can't handle more than 2 GB memory. More than 2 GB memory must be interfering with the graphics card video memory somehow.

---

### Post by eisenklopf on 2009-03-21
> **tommcd said:**
> The manual for your laptop on the Sony website does say there is a max of 2 GB memory. I would guess that your computer's BIOS just can't handle more than 2 GB memory. More than 2 GB memory must be interfering with the graphics card video memory somehow.

yes I am aware that Sony says it's maxed at 2GB but benchmarking it revealed that the hardware would be able to handle 4GB. I'm not comfortable flashing a custom bios onto it so I'm looking for alternatives. I really wouldn't want to try a bios and have a $4000 paperweight. I was suggested mapping the memory addresses but I haven't done that before. Sounds safer than a custom bios so that might be tried  if i don't hear of something easier.

---

