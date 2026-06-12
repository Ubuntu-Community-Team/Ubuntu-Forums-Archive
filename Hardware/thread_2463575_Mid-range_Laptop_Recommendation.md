---
title: "Mid-range Laptop Recommendation"
date: 2021-06-14
forum: Hardware
---

### Post by erosman on 2021-06-14
I am new to Linux & Ubuntu and I am planning to get a new mid-range laptop and install Ubuntu on it. I use laptop for general computing and programming (not games or heavy graphic work).

Being new, I am hoping for the least installation hassle.

Most available laptops use nvidia graphic card and from what I have read, there are driver issues with them.

I am hoping for some recommendation in laptops (let's say around 1000-1500 USD) to aim for.

*PS. I know Lenovo Thinkpad range use AMD graphic cards, but the widely available E15 seems to have over-heating problem.*

---

### Post by tea for one on 2021-06-14
Alternatively, you could investigate a device with Ubuntu pre-installed:-

[https://linuxpreloaded.com/](https://linuxpreloaded.com/)

---

### Post by sudodus on 2021-06-14
I have good experiences with **refurbished (second hand) enterprise class computers**. They are maybe 2-3 years old and usually Ubuntu works very well (much better than brand new hardware, where there might not yet be good Linux drivers).

You can check if there is some company in your region that takes care of used computers from big companies and other organizations, deletes the content of the storage device (HDD, SSD), and makes a general checkup of the hardware. It should also be possible to get a guarantee, that a refurbished computer should work for 6 or 12 months. Usually it is enough that it works during the first month after shipping to be rather sure that it will work for years.

The battery might be rather tired, so if you need a long working time on battery, maybe you should also add the cost for a new battery in the total price.

---

### Post by erosman on 2021-06-14
There is no Linux pre-loaded laptops where I am (all with Widows or DOS).

I prefer to get a new one, but it can be an older model.

I would prefer the highest spec possible, without running into installation headaches.

The commonly available brands are Lenovo, Acer, Asus (+ some Dell and HP).

---

### Post by SeijiSensei on 2021-06-14
Are you willing to overwrite any existing Windows implementation and make the system Linux-only?

If you want to "dual-boot" and select either Windows or Linux when the system starts up, that's more complex. Most laptop manufacturers, HP is a good example, partition the hard drives so that there is no available space to add another operating system. It's possible to resize the partitions using tools that come with the installation media like gparted, but you should be aware you might need to take this extra step if you want a dual-boot option.

I don't use dual-boot any more on systems where I don't expect to play games. Instead I use the native Linux KVM subsystem or VirtualBox to create a virtual machine on top of Linux, then install Windows there.

---

### Post by TheFu on 2021-06-14
Can I talk you out of buying a computer? Especially when you are new to Linux, spending money probably isn't necessary.

Use a virtual machine - a VM.

Chances are that your current system can easily run a Linux desktop, especially if you don't game.  Any Core i3 CPU (or better) with 4G of RAM or more can easily run a Lite Ubuntu install.  What I mean by lite is not Gnome3.  That leaves Xubuntu, Ubuntu-Mate, Ubuntu Cinnamon, Lubuntu and most certainly Ubuntu Server.

By going with a VM, you've removed all the hardware issues.  Virtual hardware will be presented to the OS. That virtual hardware will be extremely well supported.  I've been running my main desktop inside a VM since 2010-ish. When it is full screen, I don't notice the difference.

There is absolutely ZERO reason to spend over $600 for any new Linux laptop.  Spending more just isn't needed unless you plan to be a Java or Android program developer.  For all other languages, very little resources are actually needed, provided you stay away from Java and Electron-based tools.

In 2012, I switched from a Core i5 to a Chromebook running Lubuntu for my software development needs when on the road.  I was doing web-server back ends with a DBMS, running everything on that chromebook. Worked great. The Chromebook had a Celeron CPU.

BTW, I was a professional, cross-platform, C/C++ developer for 15+ yrs in the commercial software world. I splurged on my last laptop purchase.  It was an off-lease Asus 15 inch with 8G RAM, 8th-gen Core i5, 1080p screen ... for $305.  New, it was selling for $499.  It runs virtual machines nicely.  

When I travel, I pull my normal desktop VM over to the laptop and have everything I'm used to local.  VMs are extremely convenient - they abstract hardware dependencies away.  If the laptop breaks or gets stolen, I can walk into any electronics store, buy whatever laptop I need, then just load the hypervisor for the VM and copy over the VM files/data - bam. No setup. No configuration. Just point the hypervisor at the VM file(s) and say "run".  It is "my desktop" immediately.  

Plus, because it is Linux, I don't have to worry about license keys for anything.  All the software, tools, used for my development are F/LOSS too.  With F/LOSS, we are encouraged to share.

Read up on virtualization a bit.  Try it out.  Which hypervisor should be used depends on your hostOS.  I use KVM/QEMU which is Linux-only, but it is what all the huge VPS services use.  Amazon uses it. Linode uses it.  Basically, if you aren't VMware or Microsoft where they have to eat their own dogfood, then you are using KVM.

Most beginners at virtualization will probably start out using virtualbox from Oracle. Just be aware of their license agreement for any addons or guest additions.

Anyways, virtualization is a mandatory skill for all programmers and IT people today. If you aren't using it, learning it, then you are already behind.

I did say that 4G is enough RAM. That's true, but a little more RAM - say 8G makes everything easy for a few Linux VMs - if you want to run a few servers and a client-desktop - each inside different VMs on the same physical box.  For a very long time, I ran 15 VMs on a 16G RAM Core2 Duo E6600. Worked fine. Over the decades I've moved to Core i5 and most recently to a Ryzen 5 system for hosting my VMs.  With a NAS, automatic failover between 2+ VM hosts is possible, just like what enterprises do.  All for $0.  Plenty of useful skills to have.  So, if your current system has 8G of RAM or more, don't feel like you need to upgrade.  For VMs, the most performance comes from sufficient RAM and using an SSD for VM storage. They really don't get CPU bound anymore on a mid-range desktop system.

If you are always connected to the internet, then you can use a secure remote desktop from where you are back into your more powerful desktop.  I do that when traveling too.  A chromebook with a lite-ubuntu and x2go allows remote access over an encrypted tunnel to my desktop in my home office from anywhere with ISDN internet or better. All the processing happens on the remote Ryzen 5, not the local chromebook.  

Lots of options. Most without spending any money.

Now, if the company is paying and it is a use-it-or-lose it offer, then I'd get a Dell XPS 13inch ultrabook.  For the last 5 yrs, they've won all the laptop design awards, beating out whatever Apple is selling.  They are beautiful machines. On sale, they can be found for $1200 in the 4K screen versions.  The 1080p screens are sub-$1000.  Just checked, $950 today for the i3 version. $1000 today for an i5 version. Those do seem a little heavy to me - 2.5lbs.  My last chromebook was 1.98 lbs.

That $50 difference nearly doubles the passmarks. i3-1115G4 (6344 passmarks)  i5-1135G7 (10052 passmarks). I'd get the i5.  The i7 is $350 more but has 16G of RAM too - a huge jump.

I didn't check about RAM or SSD upgrades. You should. On these ultra-thin, light, laptops, always check that RAM and the SSD can be swapped. Always.  Don't get burned/stuck.

I like the used laptop when I'm paying.  They come with 1 yr warranties from reputable online sellers, BTW.

What sort of software development are you planning? It will probably be fine regardless, but Java and Android dev environments are hogs, so you'll want the fastest Core i9 and 64G of RAM if you are planning to do that sort of development.  Pretty much all other development works fine with a Core i3 and 8G of RAM.

---

### Post by sudodus on 2021-06-14
> **erosman said:**
> There is no pre-loaded laptops where I am (all with Widows or DOS).

I prefer to get a new one, but it can be an older model.

I would prefer the highest spec possible, without running into installation headaches.

The commonly available brands are Lenovo, Acer, Asus (+ some Dell and HP).

Look for Lenovo Thinkpad; Dell Precision, XPS, Latitude; HP ZBook, Elitebook. There are several models of each of these brands and model series, and there are other brands ...

---

### Post by oldfred on 2021-06-14
Most vendors, first level help desk will say they do not support Linux.
But indirectly vendors are starting to allow UEFI update directly from Linux.
I would consider systems that have fwupd as then they at least indirectly support Linux.
Dell was one of the first, probably because they also sold models with only Linux. But other brands are now adding models. But only newer systems support fwupd.

If getting new system, often better to be one generation older. Very new systems need newest kernel & drivers which may not be in current distributions, yet. There are ways to add ppa or download kernels & drivers, but more of a hassle than just using a current distribution.

[https://fwupd.org/](https://fwupd.org/)
Devices using LVFS for firmware updates
[https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist)

---

### Post by erosman on 2021-06-14
> **SeijiSensei said:**
> Are you willing to overwrite any existing Windows implementation and make the system Linux-only?

Indeed, I intend to have an Ubuntu only system.

> **TheFu said:**
> Use a virtual machine - a VM.

I was hoping to ditch Windows and I am concerned about the current specs of my laptop.

> **TheFu said:**
> Chances are that your current system can easily run a Linux desktop,  especially if you don't game.  Any Core i3 CPU (or better) with 4G of  RAM or more can easily run a Lite Ubuntu install.  What I mean by lite  is not Gnome3.

Possible... I have an Acer Aspire i5-3230m, 4gb RAM, 750gb HDD (70% free), NVIDIA GeForce, Win7. It has been giving me hassle with low RAM & 100% CPU usage, and needs an OS upgrade but not wise to spend money on Win10 and even then, it wont run better as win10 is more resource hungry.

However, the move will take me few weeks, to install  new system, get used to it, move my work to a new system and get it working. I would need my laptop runing in the meantime (& use to find answers for problems I run into with the new installation). In other words, I would need 2 laptops while the move is going on, therefore it is not possible to use my current laptop.

I am retired and mostly use laptop for programming (JavaScript) and general computing (browsing, watch video, play music, etc). My laptop is 6 years old and I was thinking of upgrading it and the cost is from my own pocket.

I might? need to install Android Dev suit, although I dont intend to do any Android App. I tried it and it run into so many problems on my system (which is already outdated) and after many downloads (5+gb), it finally didn't run properly so I gave it up. I only needed to run Firefox for Android (to test things) but sadly couldn't find a small emulator to do it.

I am aiming for ... 16gm RAM, 512 SSD, i7- 11th or 10th gen.


> **sudodus said:**
> Look for Lenovo Thinkpad; Dell Precision, XPS,  Latitude; HP ZBook, Elitebook. There are several models of each of these  brands and model series, and there are other brands ...

Thank you.

> **oldfred said:**
> Dell was one of the first, probably because they also sold models with  only Linux. But other brands are now adding models. But only newer  systems support fwupd.

If getting new system, often better to be one generation older. Very new  systems need newest kernel & drivers which may not be in current  distributions, yet. There are ways to add ppa or download kernels &  drivers, but more of a hassle than just using a current distribution.

I once had a Dell laptop and was not happy with it. I have had a few Acer laptops and been generally happy with them.

---

### Post by TheFu on 2021-06-14
Be careful with Acer.  Some of their models prevent Linux from working and some block the vt-x capabilities that a CPU has in a BIOS setting that cannot be changed.

Dell and Lenovo seem to have the best Linux support for the mass-made laptops, unless you choose a Linux-only vendor like System76 which only makes Linux laptops, but for a premium price.  All Linux laptops have similar issues after 2 yrs - the OS they came with needs to be replaced, but the vendor doesn't provide a clean upgrade path, so having well supported, massively deployed world-wide hardware is our best option.  That's where Dell and Lenovo shine.

I've owned Dell, Acer, Toshiba, Asus, and used work laptops from Lenovo and HP.  I have Asus and Dell laptops now and have retired 2 Dells and an Acer and a Toshiba laptop.

I just hate to see someone spend $100+ on a system that they might hate when it isn't necessary.  I'm sorta like you - I hold onto computers far too long.  With my last laptop purchase, I decided to try replacing computers 2x faster than previously and spending 50% less money.  The performance of a sub-$400 laptop can be really impressive. Buy another $400 laptop in 5 yrs and you've saved money overall, while probably still more than doubling the performance and other specs.  Just something to consider.  Plus, laptops aren't exactly built for end-user upgrades anymore.

I'll go away now.

---

### Post by dddman on 2021-06-14
Dell (my favored) currently has 600+ listings for open box (new or like new) computers @ eBay.
[https://www.ebay.com/sch/i.html?_from=R40&_nkw=computers+laptops&_sacat=175672&LH_TitleDesc=0&LH_ItemCondition=1500&Operating%2520System=Windows%252010&rt=nc&Brand=Dell&_dcat=177&_fsrp=1](https://www.ebay.com/sch/i.html?_from=R40&_nkw=computers+laptops&_sacat=175672&LH_TitleDesc=0&LH_ItemCondition=1500&Operating%2520System=Windows%252010&rt=nc&Brand=Dell&_dcat=177&_fsrp=1)

---

### Post by dddman on 2021-06-14
About "open box"

I should mention my current Dell cost new in 2018 $1700.  I purchased it new (open box) in 2019 for $800.  And yes this was an eBay purchase through a third party vendor.  Dell also sells refurbished and for reasons unknown 3rd party vendors are usually cheaper.

ps
It came with the Dell one year warranty.

---

### Post by SeijiSensei on 2021-06-14
I'm using a ten-year old Lenovo Y570 with an i5 and 6GB. Kubuntu 21.04 runs fine. I did replace the hard drive with an SSD which improved performance.  It has dual Intel/NVIDIA graphics.  I leave it in the NVIDIA mode.

I would never spend more than $1,000 for a brand-new laptop these days that is intended to run Linux. Linux runs fine on generic hardware. Unless you're planning on running compute-bound tasks (like 3D rendering or running big simulation models), I don't see any arguments for high-end hardware. Most of the time the computer is waiting for the dummy behind the keyboard to tell it what to do.

---

