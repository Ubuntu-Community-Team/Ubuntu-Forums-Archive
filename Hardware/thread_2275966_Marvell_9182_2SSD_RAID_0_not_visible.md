---
title: "Marvell 9182 2*SSD RAID 0 not visible"
date: 2015-04-29
forum: Hardware
---

### Post by vkmaxx on 2015-04-29
I wanted to install 15.04 Ubuntu on my Marvell 9182 RAID 0 but I can't see my drive under Ubuntu.

I tried to follow solution from here:
[http://ubuntuforums.org/showthread.php?t=2116826](http://ubuntuforums.org/showthread.php?t=2116826)
[http://en.wikipedia.org/wiki/List_of_Marvell_Technology_Group_chipsets#88SE91xx_chipsets_Linux_support](http://en.wikipedia.org/wiki/List_of_Marvell_Technology_Group_chipsets#88SE91xx_chipsets_Linux_support)

But it doesn't work. After entering:
```
[COLOR=#000000]sudo /bin/echo 1b4b 91a2 > /sys/bus/pci/drivers/ahci/new_id[/COLOR]
```
I get "permission denied" :/

Marvell is working in RAID mode, not AHCI.

---

### Post by vkmaxx on 2015-05-07
Anybody?

---

### Post by vkmaxx on 2015-07-17
After a lot of reading I was able to access SSD raid on my Marvell 8192.
Here the solution, open terminal and become Super user:
```
sudo su
```

then execute 
 ```
[FONT=monospace][COLOR=#000000]/bin/echo 1b4b 91a2 > /sys/bus/pci/drivers/ahci/new_id [/COLOR][/FONT]
```[FONT=monospace][COLOR=#000000]
There will be no confirmation or error. That's it :)
The 1b4b 91a2 is valid for my marvell 9182 [FONT=monospace][COLOR=#000000]controller [/COLOR][/FONT]on G1.Sniper mobo , you need to check it with
[/COLOR][/FONT]```

 [FONT=monospace][COLOR=#000000]lspci -nnk|grep "Marvell"[/COLOR]
[/FONT]
 
```[FONT=monospace][COLOR=#000000]

[/COLOR]
[/FONT]

---

### Post by vkmaxx on 2016-05-19
This doesn't work under newer kenel, under 16.04 live boot after entering:
```
sudo su
sudo /bin/echo 1b4b 91a2 > /sys/bus/pci/drivers/ahci/new_id 
```
I get:
```
/bin/echo: write error: File exists
```
How to fix this?

---

