---
title: "Missing RAM - Corsair Vengeance LPX - Asus Prime B450-Plus"
date: 2019-05-13
forum: Hardware
---

### Post by heyup on 2019-05-13
New build system with 8GB (2 x 4GB) RAM. The BIOS shows memory 8192 MB (2 x 4096MB 2133MHz) of RAM. When I use the free command to check for available RAM it shows total RAM of 6098584K (5955M). Other tests show the same. The system shows total RAM of less than 6GB, but the BIOS says 8GB. I'm missing 25% of the RAM. 

I also have occasional system freezes; no mouse or keyboard function. I have to switch off power and reboot. These occur when I have multiple documents and/or web pages open at the same time, but otherwise the system is at idle and not under any heavy processing load. 

The supplier sent replacement RAM. This did not resolve the problem. Supplier then sent replacement motherboard. The problem remains. The system shows total RAM of approx 6GB, and occasional freezes occur.    

When I remove one RAM module, the free command shows 3512008K (3429M) of RAM i.e. approx 3.4GB. 

Tested the RAM with these commands:
$ free
$ free -m
$ cat /proc/meminfo
$ vmstat -s
$ sudo dmidecode --type memory

Is the problem the RAM, the motherboard, a compatibility issue, or something else? 

New build:
Motherboard: ASUS PRIME B450-PLUS 
CPU: AMD RYZEN 3 2200G 3.5Ghz 65W 4C/4T AM4AP
Memory: CORSAIR DDR4 2666 Vengeance LPX 8GB (2x4GB) CM4X4GF2666C16K4
System: Ubuntu 18.04 64 bit.

---

### Post by him610 on 2019-05-13
It would be more helpful if you were to show the results of those commands, between the code tags, rather than just saying you ran them.
This is what my 8GB looks like: ```
free -h
              total        used        free      shared  buff/cache   available
Mem:          7.2Gi       1.5Gi       4.5Gi       9.0Mi       1.2Gi       5.5Gi
Swap:         979Mi          0B       979Mi
```
If your BIOS indicates you have 8GB then you have 8GB - there is no MB or Memory issue.
Has your BIOS been updated to latest version?
Have you tried swapping the memory modules between the two slots?
Do you happen to have integrated graphics or a separate graphics card?
The AMD website,[https://www.amd.com/en/products/apu/amd-ryzen-3-2200g]("https://www.amd.com/en/products/apu/amd-ryzen-3-2200g") indicates your APU/CPU has integrated graphics which also demands onboard memory. 
How much memory did you allocate in your BIOS setup for graphics?
While you are at, please show the results, between code tags, of* inxi -Fxz*

---

### Post by TheFu on 2019-05-13
A) please don't describe the results. SHOW THEM!!!  Wrong interpretations are sometimes the issue. Show the EXACT command and the EXACT output. Please.  Also, use **code tags**.

B) My initial guess is that the BIOS is configured to give the iGPU 2G of vRAM. 
[https://www.phoronix.com/scan.php?page=news_item&px=Ryzen-3-2200G-vRAM-Size](https://www.phoronix.com/scan.php?page=news_item&px=Ryzen-3-2200G-vRAM-Size)

If I'm reading that article correctly, there doesn't seem to be a good reason to allocate more than 512MB of vRAM to the iGPU unless you are a gamer. For typical office stuff, it just doesn't matter.

---

### Post by heyup on 2019-05-17
Thank you for the replies. Apologies for delay responding. 

You are right. The problem was UMA frame buffer size. The BIOS was set to the default setting of 'Auto'. 

In the Advanced menu of the BIOS was a sub menu called NB Configuration. Under that the UMA frame buffer size was set to the default setting 'Auto'. Presumably it defaults to 2GB (25% of the total 8GB).

I changed the setting to 512M. Now the free command shows more memory. The default setting showed 5955MB. With the UMA frame buffer size at 512M, the free command shows 7467MB.

Default UMA frame buffer size setting 'auto':

```

$ free -m
              total        used        free      shared  buff/cache   available
Mem:           5955         417        4468          11        1069        5291
```

UMA frame buffer size set at 512MB:

```

$ free -m
              total        used        free      shared  buff/cache   available
Mem:           7467         374        6527           9         564        6852
```

I don't use games, only office use. I'll probably leave it at 512M for now and see what happens.

---

