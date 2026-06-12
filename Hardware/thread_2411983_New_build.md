---
title: "New build"
date: 2019-02-06
forum: Hardware
---

### Post by heroquestelf on 2019-02-06
Is it permissible to ask for assistance in building a Linux machine? (& obviously I don't mean physical or financial help.)

I know that certain manufacturers play well with Linux and certain ones don't. I was going through the compatibility sticky at the top of the page and honestly did not know where to start.

Can I ask for recommendations on builds that would work well for a dedicated Linux box?

---

### Post by oldfred on 2019-02-06
Almost all the vendors will not say they support Linux, but Linux normally works.

Very new hardware may require a bit more work. Vendors do not directly support Linux and developers have to modify drivers or support software or add features to kernel. Even those that do provide some support take a while before those changes are included in a distribution. But you can often search for issues and find missing drivers, if needed. 

I tend to like Intel based systems, but I see many posts where users like their AMD systems. But again some models may not be as easily to use as others.
Almost all need UEFI updates & SSD firmware updates.

       The Current Linux Performance On 22 Intel / AMD Desktop Systems Sept 2018
[https://www.phoronix.com/scan.php?page=article&item=22-systems-linux418&num=1](https://www.phoronix.com/scan.php?page=article&item=22-systems-linux418&num=1)

Often you can find comparisons of performance here:
       
 [http://openbenchmarking.org/](http://openbenchmarking.org/)

Server, desktop, gaming or other general use system?
Approx. Budget?

My last build was general purpose, but I wanted smaller system which made cost a bit more.
And when I built it 16.04 was not yet released, but I had to use it to get the kernel & drivers I needed. But recognized that it may break with so many updates before final release.
But I normally only install LTS - long term support versions.

I was glad I used pcpartpicker as it told me the drive I was going to buy would not fit and I needed the smaller laptop 2.5 size.
       oldfred's new SFF system with skylake i5-6500 and 16.04
[http://ubuntuforums.org/showthread.php?t=2315007&p=13449024#post13449024](http://ubuntuforums.org/showthread.php?t=2315007&p=13449024#post13449024)
[http://pcpartpicker.com/p/8QKkCJ](http://pcpartpicker.com/p/8QKkCJ)

---

### Post by Dennis N on 2019-02-06
Hi, your avatar and user name suggest you are a serious gamer, so this is probably too lame for you, but FWIW, I had good results with MSI B360 motherboard. Used with Linux only. Built in October, so still easily available stuff at good prices:

Specifics:

MSI B360M Pro-VD (for Intel Coffee Lake Processor)
Intel core i3-8100 (processor compatibility list on MSI web site)
2x4gB GSkill DDR4 memory (see compatibility list on MSI web site)
Corsair CX450M power supply (see compatibility list on MSI web site)
Crucial mx500 500gB m.2 SATA drive.
micro-ATX case.
no graphics card - using Intel integrated graphics

Ubuntu 18.04 installed and runs without any tweaks or special settings. Only UEFI setting I did was set boot type to 'UEFI Only'. Everything else left as defaults (as MSI recommends). I like it. UEFI bios is simple - no fancy graphics stuff to crash on you.

---

### Post by CatKiller on 2019-02-06
Desktop hardware is broadly a solved problem. Laptops are more finicky because of things like WiFi and hybrid graphics.

Avoid the very cheap stuff.

If you have WiFi, Intel's WiFi chips get the best support. Actually, all of Intel's networking chips work well.

Onboard sound generally works out of the box, since manufacturers have broadly standardised on the same set of cheap-and-cheerful hardware, unless they're "adding value" by using some freakish thing. If that turns out to be an issue, cheap USB sound devices are cheap.

RGB bling won't work. Some sensors won't work.

Intel graphics are the most painless, but are limited in performance by the hardware's capabilities.

Nvidia graphics are the most performant, but require the use of their proprietary driver. That driver is feature-equivalent to their Windows driver, which means that it does its own thing rather than what would work best in the wider Linux ecosystem. That can cause considerable friction, but when it works it works well.

AMD graphics are in-between. They perform better than Intel graphics, but not as well as Nvidia graphics, and their driver is very much a work-in-progress.

As oldfred says, we can give you more specific guidance when we know more about your budget and use-case.

[This](https://uk.pcpartpicker.com/list/42wBpG) was my last build, in case that's useful information.

---

### Post by aljames2 on 2019-02-06
New User myself...
I recently converted an older computer to run  Ubuntu Server for home network file storage & basic media hosting  for music.  There are other things I plan to do like remote access  outside the home (like a cloud) but haven't figured out how yet.  I'm  still learning.  Reading 2 books that is helping me learn Ubuntu &  command line work.

Still setting it all up but no problems on my hardware:

Gigabyte B85M-D3H
i3-4330
8Gb Crucial RAM stick
1 Samsung SSD for the OS
2 Storage HDDs
Low power, headless setup (no video, sound, or other cards)

Only problem I ran into that I thought was a hardware, ISO, or USB problem turned out to be a bug in the 18.04.1.0  Live Server (November release) download package.  [https://bugs.launchpad.net/subiquity/+bug/1810633](https://bugs.launchpad.net/subiquity/+bug/1810633)
Basically,  when I would run the check disk for defects prior to installation it would return "errors in 3  files".  There isn't actually an error in the files, just one of the  md5sum checker files in the package wasn't updated causing a false  positive.  At least this is my layman understanding of it.

---

### Post by robehickman on 2019-02-07
I disagree with the comment about AMD graphics hardware. While this was a problem something around 10 years ago, I find the open source AMD drivers very good and haven't had any problem with them. Worked fine running a hat in time under wine - the only game that's caught my attention recently - and also works fine with blender. The drivers are technically more up to date and work well with wayland, which the nvidia driver did not. I don't know what the situation with that exactly is now. I'm not inclined to support nvidia also because their drivers generate a soft error using gpu pass-through in virtualisation which must be hacked around.

---

