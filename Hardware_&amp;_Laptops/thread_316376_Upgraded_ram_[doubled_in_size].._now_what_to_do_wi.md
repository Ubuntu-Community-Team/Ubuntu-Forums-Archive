---
title: "Upgraded ram [doubled in size].. now what to do with swap?"
date: 2006-12-10
forum: Hardware &amp; Laptops
---

### Post by SimonTheMime on 2006-12-10
Well I assume that's why I'm getting the error:
> virtual memory exhausted: Cannot allocate memory
when installing VMWare. But anyways.. I doubled my ram to 2 gigs, and my swap is unchanged. How and what to can I safely change my swap size?

Thanks in advance ^__^\/

---

### Post by SimonTheMime on 2006-12-10
:\ Anybody, please

---

### Post by ciscosurfer on 2006-12-10
With 2G of RAM, you will very rarely (if ever) be using your Swap space.

You can check on swap by issuing **free** in a terminal (likelihood that you're actually using it is very close to nill). 

There's not need to change the size of your Swap, however, if you feel like to need to, or just want to mess around with it, then you can take a look at this thread as it discusses how to go about it: [http://ubuntuforums.org/showthread.php?t=297183](http://ubuntuforums.org/showthread.php?t=297183)

---

### Post by SimonTheMime on 2006-12-10
Thanks! Any idea then why I'm getting:

"virtual memory exhausted: Cannot allocate memory"?

---

### Post by ciscosurfer on 2006-12-10
Post the output of **free** for us to see.

If you're getting that error, its quite possible that Ubunt is recognizing all of your installed memory, you're exceeding the 2G assigned to RAM, and then your swap partition is not large enough.

---

### Post by SimonTheMime on 2006-12-10
```
simon@desu:~$ free
             total       used       free     shared    buffers     cached
Mem:       2075132     532012    1543120          0       8640     241832
-/+ buffers/cache:     281540    1793592
Swap:      3028212      79252    2948960
```

---

### Post by ciscosurfer on 2006-12-10
> **SimonTheMime said:**
> ```
simon@desu:~$ free
             total       used       free     shared    buffers     cached
Mem:       2075132     532012    1543120          0       8640     241832
-/+ buffers/cache:     281540    1793592
Swap:      3028212      79252    2948960
```With that much memory installed, I couldn't tell you why your swap is actually getting hit, because according to your output, you still have 1.5G of memory unused--your swap shouldn't be getting accessed.

---

### Post by SimonTheMime on 2006-12-10
Couldn't be that my ram is broken, non? 'Cause I just recently bought these two sticks o_o.

---

### Post by tomazb on 2006-12-10
> **SimonTheMime said:**
> Well I assume that's why I'm getting the error:

when installing VMWare. But anyways.. I doubled my ram to 2 gigs, and my swap is unchanged. How and what to can I safely change my swap size?

Thanks in advance ^__^\/

You did not provide enough info about Vmware, but I am assuming you are playiong with VMWare Server which needs enough swap and /tmp for itself - around 1.5 times the memory according to docs.

Usually you can find new commands by typing command "apropos" like
"apropos swap" which gives you this on Dapper:

mkswap (8)           - set up a Linux swap area
multiload_applet (1) - Multiload (cpu, load average, memory, net, swap) applet for the GNOME panel.
swapoff (8)          - enable/disable devices and files for paging and swapping
swapon (8)           - enable/disable devices and files for paging and swapping


First one appears to be the one for your needs. With it you can create file and tell the system to swap there.

---

### Post by SimonTheMime on 2006-12-10
For VMWare, I'm trying to install regular VMWare Workstation o__o.. never had this problem before Edgy, the same copy/version of VMWare.

I also tried installing a newer version, same problem :\

---

### Post by tomazb on 2006-12-10
Weird. Never seen this problem. But I usually prepare swap to be at least 2 times of max ram possible.

---

### Post by SimonTheMime on 2006-12-10
Installed gcc3.3, fixed the vmware problem o,o

---

