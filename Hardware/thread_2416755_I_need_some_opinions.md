---
title: "I need some opinions"
date: 2019-04-15
forum: Hardware
---

### Post by radu19842 on 2019-04-15
Since my desktop pc is gone , and not having much money i bought a Asus laptop with the next speqs. :

[B][COLOR=#333333][FONT=Arial]Notebook / Laptop  - ASUS 15.6'' X541NA
[/FONT][/COLOR][COLOR=#333333][FONT=Arial]Procesor - Intel® Celeron® Dual Core N3350 (2M Cache, up to 2.4 GHz) (2 x 1.10 GHz)
RAM - 4GB
Gpu - [/FONT][/COLOR][COLOR=#333333][FONT=Arial]GMA HD 500
SDD- 250 GB

[/FONT][/COLOR][/B][COLOR=#333333][FONT=Arial]Now if you don't mind can you tell me your opinion on it , Gimp , Pinta , Office and in general most of software works ok , but what about Inkscape , i know that small lightweight drawins,illustrations,logos etc. works ok , oh and what about Krita will it work with this system , like inkscape for not so "hardcore" graphics,any hope for small , lght work/projects  on Blender :(?
Now about the Integrate Gpu with is [/FONT][/COLOR]**[COLOR=#333333][FONT=Arial]GMA HD 500[/FONT][/COLOR]**[COLOR=#333333][FONT=Arial] says it has no ram memory at all , i guess it takes ram from **the 4 GB ram** installed,or in other way (don't know how) i will place the integrated gpu specs link belloW
[/FONT][/COLOR][TABLE="class: specs-table, width: 818"]
[TR]
[TD="class: specs-left"]**Integrated GPU specs GMA 500**[/TD]
[TD="class: specs-right"][/TD]
[/TR]
[/TABLE]
[http://www.notebookcheck.net/Intel-Graphics-Media-Accelerator-500-GMA-500.12614.0.html](http://www.notebookcheck.net/Intel-Graphics-Media-Accelerator-500-GMA-500.12614.0.html)
Read until the page end 
[h=5][B][COLOR=#54595D]
[/COLOR]**Thank you so much , have a great new week ! **:)[/B][/h]

---

### Post by TheFu on 2019-04-15
The N3350 has 1100 passmarks: [https://www.cpubenchmark.net/cpu.php?cpu=Intel+Celeron+N3350+%40+1.10GHz&id=2895](https://www.cpubenchmark.net/cpu.php?cpu=Intel+Celeron+N3350+%40+1.10GHz&id=2895) which a used chromebook from 2015 is faster (Acer C720 w/ Celeron 2950U).

I know nothing about that iGPU. Sorry. I don't game, so if 1080p videos playback with h.265, then that is good enough for me.

BTW, the easy way to share machine specs is to run:
```
inxi -bDz
```

The iGPU from intel makes keeping current drivers easy. Intel has been providing their iGPU drivers in a nice way to all distros.  They basically "just work."

I bought a used Asus F510A 2-3 months ago on ebay, $305.  It had 1 small blemish that I cannot see, but can feel on the screen bezel.  Mine came with a Core i5-8250U (that's an 8th-gen), 8G RAM, 1TB HDD (spinning), 1080p screen. The CPU is about 7600 passmarks. [https://www.cpubenchmark.net/cpu.php?cpu=Intel+Core+i5-8250U+%40+1.60GHz&id=3042](https://www.cpubenchmark.net/cpu.php?cpu=Intel+Core+i5-8250U+%40+1.60GHz&id=3042) - so about 6x faster than the N3300. Guess whether you should be happy would depend on the price paid.  Being light on money causes lots of difficulties.  Everything is working except the fingerprint reader, which I would only use for 3rd factor authentication, a) after something I know and b) something I have.  

I swapped out the 1TB before even booting (it was supposed to come with Win10), and put in a 2.5" SATA EVO SSD. I never intend to use Win10, ever, anywhere.

1500 passmark is my minimal travel laptop "happy" performance level. We are all different. In general, I learned to avoid any Nxxxx CPUs.  In some ways, I miss that C720 chromebook running Lubuntu. It was fast enough for remote desktops back to my real desktop at home and had great battery life.

There were $220 Dell Core i7 systems on eBay at the time, they didn't have anywhere near the battery.  I do prefer Dell laptop keyboards and miss having a GigE ether port built-in.

The only reason I'm responding is because I got a very similar model. In short, always check the passmarks before any computer/laptop purchase. Don't worry plus/minus 200 points - these are just comparison markers. As said below, don't get too stuck, but as relative performance comparisons, they are helpful to know what any system could do.

---

### Post by radu19842 on 2019-04-16
Hello , thank you **[COLOR=#ff0000]TheFu[/COLOR][COLOR=#000000] :) [/COLOR]**bellow is my system info ,now i want to ask you if you don't mind some questions , can i run **Blender** on this laptop (or an older version of blender) or [K3D ]("http://www.k-3d.org/")witch is an older program but i guess i could install it trough wine ? Nothing hardcore stuffed up designs , no animations in Blender or K3D just small projects . Also i dont ask about **Gimp** or** Pinta** since i see those work well , but how about **Inkscape/Krita** could i use them in a "decent" manner , again nothing fancy , some logos/images/some drawings ! The res works well ! Thank you and have a great day
**[COLOR=#ff0000]All he best ![/COLOR]** :)

**System:    Host: radu-X541NA Kernel: 4.18.0-17-generic x86_64 bits: 64**
**           Desktop: Xfce 4.12.3 Distro: Ubuntu 18.04.2 LTS**
**Machine:   Device: laptop System: ASUSTeK product: X541NA v: 1.0 serial: N/A**
**           Mobo: ASUSTeK model: X541NA v: 1.0 serial: N/A**
**           UEFI: American Megatrends v: X541NA.318 date: 02/27/2018**
**Battery    BAT0: charge: 17.7 Wh 51.9% condition: 34.1/34.6 Wh (99%)**
**CPU:       Dual core Intel Celeron N3350 (-MCP-) speed/max: 1083/2400 MHz**
**Graphics:  Card: Intel Device 5a85**
**           Display Server: x11 (X.Org 1.20.1 )**
**           drivers: modesetting (unloaded: fbdev,vesa)**
**           Resolution: 1366x768@60.02hz**
**           OpenGL: renderer: Mesa DRI Intel HD Graphics 500 (Broxton 2x6)**
**           version: 4.5 Mesa 18.2.8**
**Network:   Card-1: Realtek RTL810xE PCIE Fast Ethernet controller**
**           driver: r8169**
**           Card-2: Realtek RTL8723BE PCIe Wireless Network Adapter**
[B]           driver: rtl8723be
[/B]**Drives:    HDD Total Size: 256.1GB (4.2% used)**
**           ID-1: /dev/sda model: Micron_1100_MTFD size: 256.1GB**

---

### Post by mörgæs on 2019-04-21
Wouldn't it be easier if you just installed the programs and tested them?

---

### Post by Rubi1200 on 2019-04-21
Have to say I agree with mörgæs. 

Specs. and benchmark/passmark are all fine and well but everyone has a slightly different setup so the only way to know if it works on your system is to test.

If you intend only having Ubuntu, in other words not dual-booting with Windows or another OS, you could install, test, decide what is best for you and then reinstall only keeping/adding what you know worked best for you.

Perhaps not the ideal way, but I do it all the time and often reinstall 2-3 times until I am happy with the setup.

That, for me, is one of the perfect things about Linux. I know if I reinstall there won't be any surprises, no bloatware, no driver issues because I already tested the configuration.

---

### Post by TheFu on 2019-04-21
> **radu19842 said:**
> Hello , thank you **[COLOR=#ff0000]TheFu[/COLOR][COLOR=#000000] :) [/COLOR]**bellow is my system info ,now i want to ask you if you don't mind some questions , can i run **Blender** on this laptop (or an older version of blender) or [K3D ]("http://www.k-3d.org/")witch is an older program but i guess i could install it trough wine ? Nothing hardcore stuffed up designs , no animations in Blender or K3D just small projects . Also i dont ask about **Gimp** or** Pinta** since i see those work well , but how about **Inkscape/Krita** could i use them in a "decent" manner , again nothing fancy , some logos/images/some drawings ! The res works well ! Thank you and have a great day


I didn't see your reply until today. Email notifications haven't been working in the forums very well the last 6 months or so.  

As to all the programs that you use and how they might work, I cannot say. I don't use any of them.  I edit videos using different tools and wouldn't consider using those on an old chromebook (similar specs).  Video editing prefers lots of RAM and lots of CPU.  Trivial uses for The Gimp work on low end systems, but if you are applying gradients or transpose filters, it will be painful.

I agree - just install the programs and see how they work.  It's 90 seconds to install all of them. They don't run anything when they aren't running. It is just a few MB for each on storage.

Please use normal fonts and colors unless highlighting specific things.  I like to highlight suggested programs in my posts for people who are asking for suggestions, like you've done.

When posting code or any command output, it is best to use "code tags" - Adv Reply (#). **BOLD DOESN'T MAKE HUGE PARAGRAPHS EASIER TO READ.**

I just bought a Micron 1100 500G SSD for a VM server here, so I agree with that part of the system.

See how nice using CODE TAGS can be?```

$ inxi -Fz
System:    Host: posc Kernel: 4.15.0-47-generic x86_64 (64 bit)
           Desktop: Openbox 3.6.1 Distro: Ubuntu 16.04 xenial
Machine:   System: ASUSTeK (portable) product: X510UAR v: 1.0
           Mobo: ASUSTeK model: X510UAR v: 1.0
           Bios: American Megatrends v: X510UAR.303 date: 12/12/2017
CPU:       Quad core Intel Core i5-8250U (-HT-MCP-) cache: 6144 KB 
           clock speeds: max: 3400 MHz 1: 800 MHz 2: 800 MHz 3: 800 MHz
           4: 800 MHz 5: 800 MHz 6: 800 MHz 7: 800 MHz 8: 800 MHz
Graphics:  Card: Intel UHD Graphics 620
           Display Server: X.Org 1.19.6 driver: intel
           Resolution: 1920x1080@60.01hz
           GLX Renderer: Mesa DRI Intel UHD Graphics 620 (Kabylake GT2)
           GLX Version: 3.0 Mesa 18.0.5
Audio:     Card Intel Sunrise Point-LP HD Audio driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k4.15.0-47-generic
Network:   Card: Intel Wireless 8265 / 8275 driver: iwlwifi
           IF: wlp2s0 state: down mac: <filter>
Drives:    HDD Total Size: 500.1GB (6.7% used)
           ID-1: /dev/sda model: Samsung_SSD_860 size: 500.1GB
Partition: ID-1: / size: 25G used: 7.3G (32%) fs: ext4 dev: /dev/dm-1
           ID-2: /boot size: 721M used: 142M (21%) fs: ext2 dev: /dev/sda2
           ID-3: /home size: 74G used: 20G (28%) fs: ext4 dev: /dev/dm-3
           ID-4: swap-1 size: 4.79GB used: 0.00GB (0%) fs: swap dev: /dev/dm-2
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 40.0C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 264 Uptime: 6 days Memory: 3392.7/7859.5MB
           Client: Shell (bash) inxi: 2.2.35 
```
I use a minimal desktop, lighter than XFCE. For me, having CPU and RAM used for programs instead of fancy GUI stuff makes sense. In reality, I doubt it makes more than 50-150MB of RAM difference. On a 2G system, that difference might matter. IDK.

---

### Post by Yellow Pasque on 2019-04-22
Your system meets the minimum (but not recommended) requirements for Blender: [https://www.blender.org/download/requirements/](https://www.blender.org/download/requirements/)
It should run, but don't expect great performance. Hopefully, it will allow you to do the lighter projects you want to do without bogging down.

For the other programs in question, you should google their requirements. That will get you an answer quicker than asking on a forum.

---

### Post by radu19842 on 2019-04-25
> **mörgæs said:**
> Wouldn't it be easier if you just installed the programs and tested them?
Good evening , yes you are right it's easier but im afraid of "rosting" my integrated gpu ! :)

---

### Post by radu19842 on 2019-04-25
> **TheFu said:**
> I didn't see your reply until today. Email notifications haven't been working in the forums very well the last 6 months or so.  

As to all the programs that you use and how they might work, I cannot say. I don't use any of them.  I edit videos using different tools and wouldn't consider using those on an old chromebook (similar specs).  Video editing prefers lots of RAM and lots of CPU.  Trivial uses for The Gimp work on low end systems, but if you are applying gradients or transpose filters, it will be painful.

I agree - just install the programs and see how they work.  It's 90 seconds to install all of them. They don't run anything when they aren't running. It is just a few MB for each on storage.

Please use normal fonts and colors unless highlighting specific things.  I like to highlight suggested programs in my posts for people who are asking for suggestions, like you've done.

When posting code or any command output, it is best to use "code tags" - Adv Reply (#). **BOLD DOESN'T MAKE HUGE PARAGRAPHS EASIER TO READ.**

I just bought a Micron 1100 500G SSD for a VM server here, so I agree with that part of the system.

See how nice using CODE TAGS can be?```

$ inxi -Fz
System:    Host: posc Kernel: 4.15.0-47-generic x86_64 (64 bit)
           Desktop: Openbox 3.6.1 Distro: Ubuntu 16.04 xenial
Machine:   System: ASUSTeK (portable) product: X510UAR v: 1.0
           Mobo: ASUSTeK model: X510UAR v: 1.0
           Bios: American Megatrends v: X510UAR.303 date: 12/12/2017
CPU:       Quad core Intel Core i5-8250U (-HT-MCP-) cache: 6144 KB 
           clock speeds: max: 3400 MHz 1: 800 MHz 2: 800 MHz 3: 800 MHz
           4: 800 MHz 5: 800 MHz 6: 800 MHz 7: 800 MHz 8: 800 MHz
Graphics:  Card: Intel UHD Graphics 620
           Display Server: X.Org 1.19.6 driver: intel
           Resolution: 1920x1080@60.01hz
           GLX Renderer: Mesa DRI Intel UHD Graphics 620 (Kabylake GT2)
           GLX Version: 3.0 Mesa 18.0.5
Audio:     Card Intel Sunrise Point-LP HD Audio driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k4.15.0-47-generic
Network:   Card: Intel Wireless 8265 / 8275 driver: iwlwifi
           IF: wlp2s0 state: down mac: <filter>
Drives:    HDD Total Size: 500.1GB (6.7% used)
           ID-1: /dev/sda model: Samsung_SSD_860 size: 500.1GB
Partition: ID-1: / size: 25G used: 7.3G (32%) fs: ext4 dev: /dev/dm-1
           ID-2: /boot size: 721M used: 142M (21%) fs: ext2 dev: /dev/sda2
           ID-3: /home size: 74G used: 20G (28%) fs: ext4 dev: /dev/dm-3
           ID-4: swap-1 size: 4.79GB used: 0.00GB (0%) fs: swap dev: /dev/dm-2
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 40.0C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 264 Uptime: 6 days Memory: 3392.7/7859.5MB
           Client: Shell (bash) inxi: 2.2.35 
```
I use a minimal desktop, lighter than XFCE. For me, having CPU and RAM used for programs instead of fancy GUI stuff makes sense. In reality, I doubt it makes more than 50-150MB of RAM difference. On a 2G system, that difference might matter. IDK.
I understand , thank you so much ! :)

---

### Post by radu19842 on 2019-04-25
> **Temüjin said:**
> Your system meets the minimum (but not recommended) requirements for Blender: [https://www.blender.org/download/requirements/](https://www.blender.org/download/requirements/)
It should run, but don't expect great performance. Hopefully, it will allow you to do the lighter projects you want to do without bogging down.

For the other programs in question, you should google their requirements. That will get you an answer quicker than asking on a forum.
I want to make small projects , yes 3d , but not animations or heavy stuff , i hope for the best ! Thank you !

---

### Post by TheFu on 2019-04-25
> **radu19842 said:**
> Good evening , yes you are right it's easier but im afraid of "rosting" my integrated gpu ! :)

No CPUs or GPUs today will be fried by heat. They all automatically slow down to prevent damage.

---

### Post by zohaiblaghari on 2019-05-23
Hi, for the Krita thing i can say, it will work totally fine. i have a notebook with 3 gb ram and a dual core AMD processor. I always use krita for making youtube thumbnails and some Photo edits. i don't see any stutter in work but it hangs sometimes like if i accidentally make the brush so large.

---

### Post by crip720 on 2019-05-23
I am not sure but you might have a 'baytrail' cpu.  There is a bug that causes them to freeze the computer, usually at the worst time.  There is an easy work around for it, but it depends on the set up, works good for most.  Something to check out before it freezes a minute before you finish something.

---

