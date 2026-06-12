---
title: "Computer upgrade - GPU issues ??"
date: 2017-08-14
forum: Hardware
---

### Post by oygle on 2017-08-14
Have spent the last week trying to recover from fsck problems, ram problems and boot problems. Was able to boot to a live usb and update the data backup. So, I have Kubuntu again (17.04) and the data on an external drive. However, I'm hesitant to use the desktop now, as it is 9 yrs old, and those problems may occur again. Need to consider an upgrade.

This is what the current desktop is - ASUS P5QL PRO – [https://www.asus.com/Motherboards/P5QL_PRO/specifications/](https://www.asus.com/Motherboards/P5QL_PRO/specifications/)
4GB ram, 2 HDD's – a 500 GB and a 250 GB (Both hard drives are at least 9 yrs old)
eSATA port – for external drive backups

We live off-grid, so power usage is a **BIG** factor in considering what to purchase. The current desktop uses 150 watts when active and 125 watts in idle mode (screen saver on). There are many timesin autumn/winter when I can't use the desktop. That needs to change.

If I replace it with a laptop that will have the performance and storage needed, it will be quite expensive. However, if I purchase a desktop, the high power usage will again be restrictive in autumn/winter. However, I am evaluating this based on 2008 equipment. In terms of power, performance, storage and cost, I need a new desktop. But in terms of power consumption, I need a laptop.

But apparently newer CPU's are much more energy efficient. I have also heard that I may not need a GPU ?  The applications that I use are:

> Beyond Compare, Synaptic, KMyMoney, Filezilla, Firefox, Dolphin, Flash, hplip-gui, keepassx, kfind, simple-scan, baobab, claws mail, fdupes, flashplugin-installer, vlc, gphotofs, gimp, openssh-server, gufw, smartmontools

.. nothing really heavy on video usage. I don't do video or photo editing, although use GIMP occasionally. Do I need a GPU to fulfill the needs of those applications ?

---

### Post by oldfred on 2017-08-15
I do not think you need a gpu.
[http://www.phoronix.com/scan.php?page=article&item=intel-i5-6500&num=6](http://www.phoronix.com/scan.php?page=article&item=intel-i5-6500&num=6)

Your list of apps is very similar to mine. But my old 10 year old laptop only had 1.5GB of RAM, so I only run one large app and one smaller app normally as it would go to swap and get very slow.

My old desktop had a nVidia 9600Gt and somewhere I saw the newest Intel chips (do not know about AMD) had video close to those older gpu cards. But if a gamer you need the newest gpu for game performance.

My two new desktops, one is Haswell and I do have a nVidia 620GT video card, but only added it when I realized I bought the wrong model motherboard and it had HDMI & DisplayPort out and old monitor was DVI or VGA in.
Newer desktop is Skylake and uses only the Intel internal video. And I have not had any issues. 
 oldfred's new SFF system with skylake i5-6500 and 16.04
[http://ubuntuforums.org/showthread.php?t=2315007&p=13449024#post13449024](http://ubuntuforums.org/showthread.php?t=2315007&p=13449024#post13449024)
[http://pcpartpicker.com/p/8QKkCJ](http://pcpartpicker.com/p/8QKkCJ) 

Skylake system was more expensive because of the MiniITX case & SFX power supply. I believe they now have small cases that will still take a more standard ATX power supply.
And the lower powered Intel chips are a lot less expensive, but do have somewhat less video horsepower.
But I also have a Raspberry PI and am quite surprised with its performance.

I went & looked up performance. I guess I need a new monitor & could get better gpu performance from the Haswell graphics over the older nVidia GT620 card.
[https://www.videocardbenchmark.net/compare.php?cmp%5B%5D=2451&cmp%5B%5D=1429&cmp%5B%5D=3281](https://www.videocardbenchmark.net/compare.php?cmp%5B%5D=2451&cmp%5B%5D=1429&cmp%5B%5D=3281)

---

### Post by BenginM on 2017-08-15
Hiya , I'm not sure what graphic issue you're having.. is  the card a built-in iGPU or a discrete one?

when i built a list of  components/parts using [https://pcpartpicker.com/list/](https://pcpartpicker.com/list/) .. it add an Estimated default Wattage on the left & top panels 

for instance , i picked this last night ..

[https://pcpartpicker.com/list/dyw7LD](https://pcpartpicker.com/list/dyw7LD)

so, when you pick parts the default wattage of each part gets add up as you go ..

i was told it's generally preferred to pick a power supply that is double the W of what the system consumes at 
                      full load at stock settings.. they only work at half load so they are quieter, and there will be
                      room for expandability and you don't lose much cause of drop of efficiency at low 
                      loads.. 

So, lets say you will pick this [AMD - Ryzen 5 1600]("https://pcpartpicker.com/product/mV98TW/amd-ryzen-5-1600-32ghz-6-core-processor-yd1600bbaebox") CPU and build on it .. 


one would measure it for each part as taken the default CPU TDP 65W , the motherboard  70W TDP and the graphic card
                      Rx460 TDP 75W into account and some 1-2W per dimm , 2W per fan, 10W per hdd and so on ..

             the above build [https://pcpartpicker.com/list/L9G2yf](https://pcpartpicker.com/list/L9G2yf)

note also the better value CPUs on either side of Ryzen 7 1700 and Ryzen 5 1500X (so to speak) have 
                      65W TDPs and happen to actually draw about that much power , i skipped Ryzen 3 as it's also at 65W. if you'll upgrade the CPU with Ryzen i was told the  G.Skill Flare X , G.skill Fortis  RAMs are built for/with AMD Ryzen support in mind and a single bank of RAM type is recommend in general .

look at the Estimated Wattage of this build :

[https://pcpartpicker.com/list/WCnXcc](https://pcpartpicker.com/list/WCnXcc)

The intel's Skylake  i5-6500  i7-6700K , and Intel Core i5-6600K default TDP is at 91W . and they have the built-in iGPU Intel® HD Graphics 530

 the Broadwell processors 5775C core i7 4 cores/8 threads and core i5 5675C are at 65W, these two comes with the integrated iGPU Intel® Iris&#8482; Pro Graphics 6200

and all the Broadwell-E CPUs are at 140W, and these X Broadwell E desktop processors doesn't come with a built-in integrated GPU.

[TABLE="class: part-table tablesorter tablesorter-default"]
[TR]
[/TR]
[TR]
[TD="class: tdname"][/TD]
[/TR]
[/TABLE]


as this will be an upgrade , i don't know how many cores the current CPU has , but this is 2017 not 2001! and goin' to 18 , so i would suggest to consider pickin' a CPU with at least 4-6 cores as you will be using the KDE desktop , but even if using a lightweight desktop having those extra cores for mutlitasking doesn't hurt .. and 8-16GB of RAMs, now that's what is considered an upgrade .. all of this upgrade stuff will depends on your budget .

So are you going to upgrade the CPU and RAM only , or with a new Mobo as well .. because you have a few good options for the motherboard weather it's an Intel or an AMD CPU and mobo..

---

### Post by Dennis N on 2017-08-15
> We live off-grid, so power usage is a BIG factor in considering what to purchase. 

If one is concerned about power consumption, along with an easy build, consider Zotac barebones systems. I have Zotac ZBOX ID-18 UEFI system and CPU power consumption is 17 watts TDP with Intel Celeron 1007U processor. Power supply (external) is 65 watts. It turned out to be more capable than I expected. For barebones, you add your own ram and HDD or SSD and it is ready to use. I purchased it on sale December 24, 2014, along with 8 gB of ram and standard laptop HD, but later added a Samsung SSD. Perfect for general computing. Not a currently available model, however.

---

### Post by BloodyIron on 2017-08-15
Core 2's are horribly inefficient from a power perspective. I'd recommend recycling that computer and getting an i3 or i5, even if it's second hand, it will be worlds more efficient than that system! I'd recommend at least a 2xxx generation i3 or i5, but newer generations are more power efficient too.

---

### Post by oygle on 2017-08-16
> **oldfred said:**
> I do not think you need a gpu.
[http://www.phoronix.com/scan.php?page=article&item=intel-i5-6500&num=6](http://www.phoronix.com/scan.php?page=article&item=intel-i5-6500&num=6)

Your list of apps is very similar to mine. But my old 10 year old laptop only had 1.5GB of RAM, so I only run one large app and one smaller app normally as it would go to swap and get very slow.

Thanks for confirming that 'oldfred'., and for your other comments regards equipment.  :)

> **BenginM said:**
> Hiya , I'm not sure what graphic issue you're having.. is  the card a built-in iGPU or a discrete one?

Its a seperate GPU card, but I'm not keeping that computer, need to upgrade.

> **BenginM said:**
> 
when i built a list of  components/parts using [https://pcpartpicker.com/list/](https://pcpartpicker.com/list/) .. it add an Estimated default Wattage on the left & top panels 

for instance , i picked this last night ..

[https://pcpartpicker.com/list/dyw7LD](https://pcpartpicker.com/list/dyw7LD)

so, when you pick parts the default wattage of each part gets add up as you go ..


Great, that's a very handy site, especially to display the watts, thanks.

> **Dennis N said:**
> If one is concerned about power consumption, along with an easy build, consider Zotac barebones systems. I have Zotac ZBOX ID-18 UEFI system and CPU power consumption is 17 watts TDP with Intel Celeron 1007U processor. Power supply (external) is 65 watts. It turned out to be more capable than I expected. For barebones, you add your own ram and HDD or SSD and it is ready to use. I purchased it on sale December 24, 2014, along with 8 gB of ram and standard laptop HD, but later added a Samsung SSD. Perfect for general computing. Not a currently available model, however.

I'm running a Dell Inspiron 3542 laptop now, i7 CPU, 8 Gb ram and it only used 14 watts when fully charged. Are these Zotacs like a laptop ?

> **BloodyIron said:**
> Core 2's are horribly inefficient from a power perspective. I'd recommend recycling that computer and getting an i3 or i5, even if it's second hand, it will be worlds more efficient than that system! I'd recommend at least a 2xxx generation i3 or i5, but newer generations are more power efficient too.

Thanks; see the comment above regards the Dell laptop. It was less than $1,000.

---

### Post by mastablasta on 2017-08-17
> **oygle said:**
> 
I'm running a Dell Inspiron 3542 laptop now, i7 CPU, 8 Gb ram and it only used 14 watts when fully charged. Are these Zotacs like a laptop ?


zotacs are usually on ITX motherboards. ITX are used for small form factor PC often also used for media server boxes.

Intels marked with U have low power consumption. they are usually in laptops but also some of the smaller boxes or you can also add it yourself to small ITX motherbaords or porbably also to some larger ones. 

for your usage the default intel GPU will be overkill (they came a long way...) you can save power with CPU + GPU combo (now called APU) + if you add LED monitor you should get better power consumption as well.

you can also investigate Intel NUC, though storage will mostly be external with those. same goes for ITX boxes (for example check out the Mintbox). 

if you can live with a laptop i would go for that. it is cheaper than smallbox+monitor combination and made for low power consumption. plus when the grid goes out you can use battery. and these new laptops have batteries that last 8h+. if you need more time, you can purchase a larger battery or get a spare one. if you are strapped for cash you can buy a used one with warranty. if you go for a used one then go for the business model as they are better built and usually last longer + they usually also have upgrade options. something with 4th or 5th gen intel will reduce a lot of power consumption and it shouldn't cost more than 350 - 400 USD.

now for my curiousity - how do you get power? from the sun? what about other means (e.g. wind, watter)?

---

