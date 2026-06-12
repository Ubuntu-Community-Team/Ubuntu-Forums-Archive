---
title: "Ubuntu 22.04.1 used memory too high"
date: 2023-01-10
forum: Hardware
---

### Post by dxyzhou-tiger on 2023-01-10
Hi, 
I have Intel 11-Gen i7-1185GE @2.8GHz Embedded CPU (4 cores). When Ubuntu 22.04.1 is started, it shows 3.2 GB is used. On my Intel 1-Gen i7-10700K @3.80GHz desktop, it only takes 0.9 GB used memory immediately the system is started.

The memory used by all modules (applications) using ps_mem, is about 200MB. 
I am wondering where is about 2GB memory located for? 

Thank you,
Tiger

---

### Post by TheFu on 2023-01-10
What does top, htop, glances, free show is using the RAM?

"too high" is extremely subjective.  If you have a GUI (i.e. a desktop install), expect about 1GB or RAM to be used ... a little less for lighter DEs and a little more for a heavy DE like Gnome3 or Gnome4.

The system I'm on now looks like this:
```
$ free -hm
              total        used        free      shared  buff/cache   available
Mem:            31G         18G        9.8G        160M        3.4G         12G
Swap:          4.3G        2.1G        2.1G

```
That says, I have 32GB of RAM and 18G is being used by the OS and programs.  9.8G is "free" and 3.4G is being used for disk and network buffers.  The system is using about 50% of the 4.3G swap. This is a bit maddening, since there is free RAM available.  I'd want zero swap used until RAM is actually exhausted.

Here's another system:
```
$ free -hm
              total        used        free      shared  buff/cache   available
Mem:           14Gi       3.1Gi       353Mi       2.0Mi        11Gi        11Gi
Swap:         4.1Gi       157Mi       3.9Gi
```
16GB of RAM, but it has an integrated GPU with the CPU ... that is likely taking 1-2GB of the RAM.  That other system isn't running any GUI or anywhere as many programs, so only 3.1G of RAM is used, but 11G is used for buffers.  Very little swap is being used. Excellent.

And 1 last system:
```
$ free -hm
              total        used        free      shared  buff/cache   available
Mem:          3.8Gi       919Mi       234Mi        10Mi       2.7Gi       2.7Gi
Swap:         4.1Gi        20Mi       4.1Gi
```
This one is a light desktop (no DE) and has only 4GB of RAM installed. Still, 2.7G is being used for disk and network buffers. Almost no swap is used.  See how the more RAM that isn't used for programs gets used for buffers?  That's a good thing.  Could that be happening on your system?

Certain commonly used programs, like the bloated modern web browsers, are known to be RAM hogs. Instead of using Chrome or Firefox, use Lynx or Dillo. Obviously, those 2 browsers aren't full featured, but might be sufficient for many uses.

---

### Post by tea for one on 2023-01-10
Intel NUC8i3BEH
Ubuntu 22.04
Gnome 42.1
Wayland session
Firefox 109 and Gnome Terminal in use.
```
edited@edited-22-04:~$ free -hm
               total        used        free      shared  buff/cache   available
Mem:           7.6Gi       1.2Gi       4.4Gi       405Mi       2.1Gi       5.8Gi
Swap:          3.0Gi          0B       3.0Gi
edited@edited-22-04:~$ 
```
Just offering info for comparison.

---

### Post by dxyzhou-tiger on 2023-01-10
Ok, It's true that 'too high' is subjective. 
smemstat : Total usage: 213M. 
Free -m : total: 3600, used 3200, free 109, shared 123 buff 272  available 61.
ps_mem also retuns 200MB. 

This is embedded, 4G total. To increase, we have to respin the board. I am trying to focus on used memory whether or not some device drivers can be disabled or programs can be uninstalled so that we can gain the available memory. I am having hard time to figure out how 3.2 GB memory is allocated for what drivers/programs. In BIOS there are large blocks of memory are reserved. PCIe BARs are supposed to be virtual memory. And programs totaled only about 200MB used.
So is there any way to have a list memory used ( by whatever drivers/programs) that sums up to be equal to used memory, in my case 3.2GB. ?
Thank you,
Tiger

---

### Post by TheFu on 2023-01-10
> **tea for one said:**
>  ```
$ free -hm
               total        used        free      shared  buff/cache   available
Mem:           7.6Gi       1.2Gi       4.4Gi       405Mi       2.1Gi       5.8Gi
Swap:          3.0Gi          0B       3.0Gi
 
```
Just offering info for comparison.

That's a good point.  I was showing 2 20.04 and 1 18.04 system above.
Here's an xubuntu 22.04 accessed via ssh (not logged in):
```
$ free -hm
               total        used        free      shared  buff/cache   available
Mem:           3.8Gi       285Mi       3.1Gi       7.0Mi       441Mi       3.3Gi
Swap:          975Mi          0B       975Mi
```
Logged in via a GUI ... I use fvwm and it is using 285MB.  

And a 22.04 server via ssh:
```
$ free -hm
               total        used        free      shared  buff/cache   available
Mem:           1.9Gi       169Mi       1.5Gi       3.0Mi       228Mi       1.6Gi
Swap:          1.0Gi          0B       1.0Gi
```
No GUI at all, saves 100MB.

Both of those 22.04 systems are running inside virtual machines and have fake, extremely compatible, hardware.  Or at least the OS thinks they do. ;)  I hadn't patched either since the last time they were used ... probably in early Dec.  Patching the server now and it seems there are 60+ patches being applied, including a new kernel. Not surprising.  After patching, before rebooting,  about 20MB more RAM is used.  After rebooting, 175MB RAM used. That's slightly interesting to me.  With servers, I strive to provide the amount of RAM the workload needs, but no more.  2GB is my initial default until I have a few weeks of monitoring to show what the workload requires.  Most of my servers easily fit in 512MB, some even in 384MB of RAM.  

Patching the xubuntu 22.04 system now. I've logged in with a GUI (fvwm).  There's a new version of firefox.  Forced the snap to refresh.  Now that system is using 1.2GB with the new firefox snap running pointing at cnn.com.  Uuug.  Snaps are bloated.  CNN is bloated.

For desktops, I start with 3-4GB thanks to the bloated browser problem. There really isn't much choice, but it is interesting to see how some websites behave with dillo.  Dillo tames most extremely busy news websites to just the stories.

---

### Post by SeijiSensei on 2023-01-10
The buffer/cache figure consists of memory being used to cache disk transactions. It's actually also "free" memory that will be released if needed when additional applications are opened.

The number that matters most is memory "available." That includes both free memory and memory used for caching/buffering.

---

### Post by dxyzhou-tiger on 2023-01-24
Hi,
Finally, I found that it is the Intel E810 Ethernet Controller causing the problem. The kernel driver loaded is ice. E810 is 1G and 25G dual ethernet phy. Each PCIe interface takes 1 GB memory. It is on CPU PCI root port. We don't have interface in the BIOS for  configuration of E810. Is there anyway in the driver configuration that can limit the memory usage?

Thank you
dxyzhou-tiger

---

### Post by fer-at on 2023-02-24
Hi,
I came across this thread as I was having a similar problem. I have a system with 32GB of ram and I was stumped as to why I was constantly with only 5-6GB free running nothing but a text document on Libreoffice Writer, a dictionary app and some music in the background. I figured that the culprit was window management, or some process associated with it.

I would open my document on Writer then resize it to the left of the screen using the Active Screen Edges features, then do the same with Goldendict. Then I would resize both at the same time by pulling the middle line to give Writer more space. That caused a mini-freeze of a few seconds, but I never bothered much with it. By running top on a terminal window on my second monitor and repeating the process I realized that RAM usage skyrocketed by 10-12GB during that "mini-freeze" and stayed up there even after I closed both Writer and Goldendict, going down to normally expected values only after a reboot. I reckon the problem may be related to the fact that Writer runs native Wayland, while Goldendict uses xwayland, but I'm not sure. To stop this from happening again I just stopped using Active Screen Edges to resize windows.

Edit: Just an update. I repeated the process to try to identify the process hogging all the memory up. This time I didn't even get the mini-freeze, but memory usage went up all the same from ~ 3500 MiB used to ~ 16000 MiB. Going up and down the list of processes on top I couldn't eyeball any spike in memory usage. Gnome-shell remained at about 1.3 - 1.4%, soffice.bin, which is Libreoffice writer, remained at 1.7% and goldendict at 0.7%. There's no process above 2%, and yet memory is going somewhere, even though the system seems to be operating normally. This is standard ubuntu 22.04.2.

---

