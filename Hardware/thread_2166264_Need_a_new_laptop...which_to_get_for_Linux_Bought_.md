---
title: "Need a new laptop...which to get for Linux? Bought an HP Noooooooooooooooooooooooooo"
date: 2013-08-08
forum: Hardware
---

### Post by thezman007 on 2013-08-08
Hello everyone ):P , 

I have been fiddling with Linux for a few years now, and have come around to using it exclusively at home and work (except for a Windows VM at work solely for Quickbooks, COME ON Quickbooks make it for Linux already...). Our aging netbook was nearly inoperative so we bit the bullet, got a small loan and bought an HP. What a mistake!!! I didn't know HP was so against Linux, but I will never be purchasing anything of theirs again. Anyways, I will be returning this laptop shortly and am wondering what to buy... Asus, Dell, what? 

Here are my thoughts:

The Dell: [http://www.samsclub.com/sams/inspiron-15v-intel-core-i5-3317u/prod10070249.ip?navAction=push](http://www.samsclub.com/sams/inspiron-15v-intel-core-i5-3317u/prod10070249.ip?navAction=push)

The Asus: [http://www.samsclub.com/sams/asus-15inch-notebook-r510ca-rb51/prod10830719.ip?navAction=push](http://www.samsclub.com/sams/asus-15inch-notebook-r510ca-rb51/prod10830719.ip?navAction=push)

Maybe an Acer??? [http://www.samsclub.com/sams/acer-v3-551g-x419-amd-a10-4600m/prod10960064.ip?navAction=](http://www.samsclub.com/sams/acer-v3-551g-x419-amd-a10-4600m/prod10960064.ip?navAction=)

Any thoughts? Does Linux play well with Intel CPU's? I've always been an AMD guy as I don't overclock and hate paying for names... Any help, insights, etc. will be greatly appreciated. Thanks :)

Edit: Looking to run Ubuntu 12.04 btw

---

### Post by james25 on 2013-08-08
What was wrong with the HP laptop? :confused: I am running Ubuntu 12.04 on an HP netbook right now. It is 32-bit and came installed with Windows 7 Starter which was just too much for it to handle, so I installed Ubuntu on it which in most cases, runs fine. :-)

---

### Post by pqwoerituytrueiwoq on 2013-08-08
Linux plays well with both Intel and AMD CPUs
If you want a linux friendly GPU there most friendly there is would be Intel
If you need virtualbox and you get intel look at a i3 CPU or better, the Celeron and Pentium's don't have VT support
The i3s are competitive with AMD quad cores, if you do video editing I suggest high end AMD CPUs (8 cores)

A lot of AMD desktop class CPUs are meant for overclocking in, i have a small OC on my desktop +300MHz

AMD does not update there proprietary drivers for new X servers after a few years, Nvidia has a better policy with that
This may be become irrelevant with mir coming out soon
Intel's GPUs use open source drivers
The open source drivers on some AMD chips now support power management (3.11 kernel) and should be in the next LTS
there have also been some recent improvements for Intel CPU power management in the 3.10 and 3.11 kernel

I do recommend 13.04 over 12.04, 14.04 will be the next LTS
I am using a new kernel than what shipped with 13.04 (3.9 on my desktop (i think i will upgrade to 3.11 and the newest Nvidia driver soon,the stock nvida driver for 13.04 does not work with 3.10+ kernels) and 3.11 on my laptop)
both systems are in my signature

What HP was it you had? It could have been a hybrid GPU or some windows 8 UEFI crap you had issues with
I was not that happy with my old HP laptop (CQ60-215DX), it runs hot and feels slow (AMD Athlon x2 2Ghz + Geforce Nvidia 8200m)
I am very happy with my asus laptop (see signature)

AMD APUs have a better GPU than a Intel CPU has, but Intel CPUs tend to be better than AMD CPUs
Do you need CPU or GPU more?

Edit have you heard of [GNUcash]("apt:gnucash")?

I have also seen people recommend leveno thinkpads for Linux

---

### Post by thezman007 on 2013-08-08
pqwoerituytrueiwoq

This is the laptop I bought:

[http://www.samsclub.com/sams/hp-17-3-notebook-amd-a6-5200/prod10450829.ip?navAction=push](http://www.samsclub.com/sams/hp-17-3-notebook-amd-a6-5200/prod10450829.ip?navAction=push)

I'm sure I could make it work eventually, but since I am trying to keep my wife convinced how great Linux is, why fight an uphill battle? It will be the sole computer of the home so CPU vs GPU is tough. Mostly, it will be for web surfing, a little word processing, etc. I would like the ability to stream to a largish screen though say 32". I am leaning toward the Asus, I've never owned one before but they seem like a good comp.

james25:

It didn't want to run an X window. It couldn't find a screen. It just seemed like the more I looked into it, the less HP wants to support open source software

---

### Post by thezman007 on 2013-08-08
Provided it will stream Youtube witout glitching that would probably be enough.

---

### Post by pqwoerituytrueiwoq on 2013-08-08
You would probably want to use 13.04 to get the newer driver for that HP laptop
If you don't need virtualbox a Intel Pentium should do fine, i have ran youtube full screen on my laptop on a 1080p and its 720p display at the same time and it ran perfectly

edit: look what i found:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16834231067](http://www.newegg.com/Product/Product.aspx?Item=N82E16834231067)
CPU is a bit week but it is a US retailer caring a computer with Ubuntu pre-installed!!!


I also found this:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16834230984](http://www.newegg.com/Product/Product.aspx?Item=N82E16834230984)
Only issues should should have in the wired network, based on test results for 12.10

---

### Post by ka2012 on 2013-08-08
Whats so bad about HP computers and linux? I have an HP laptop dual installed with windows and Ubuntu 12.04 and it everything seems to be working fine so far...

---

### Post by rob62158 on 2013-08-08
I have an Asus laptop and it runs great with Ubuntu. It has an AMD A6 processor with 4gigs ram and a Radion 6720 gpu.

---

### Post by thezman007 on 2013-08-08
Yes, I have looked into GNUcash, but unfortunately it doesn't track inventory and I need that for my business

edit: Nor will Quickbooks run in WINE

---

### Post by pqwoerituytrueiwoq on 2013-08-08
If you had a database that could store inventory could you replace quickbooks with gnucash and that or is there some integration you need?
i have one i made for my mom
it is accessed via web browser

---

### Post by james25 on 2013-08-08
> **ka2012 said:**
> Whats so bad about HP computers and linux? I have an HP laptop dual installed with windows and Ubuntu 12.04 and it everything seems to be working fine so far...

It's all working fine for me as well on Ubuntu 12.04 with my HP netbook.

---

### Post by thezman007 on 2013-08-08
Boy, you don't like computers at all do you? LOL Not sure I could handle both proggys independently (I know, I know, LAZY). It's awesome that Newegg has some preinstalled stuff. Unfortunately we took out a loan AT Sam's Club to buy the HP, so that's where I will have to purchase it.

---

### Post by pqwoerituytrueiwoq on 2013-08-08
the asus X75A series looks Linux friendly, i would say this is worth a try
[http://www.samsclub.com/sams/asus-17-3-notebook-intel-core-i3-2370m/prod9230238.ip?navAction=push](http://www.samsclub.com/sams/asus-17-3-notebook-intel-core-i3-2370m/prod9230238.ip?navAction=push)

---

### Post by thezman007 on 2013-08-08
I don't know, maybe it's not that bad and I'm worried about nothing??? Maybe it's just a kernel issue.

---

### Post by thezman007 on 2013-08-08
I am burning a copy of 13.04 now to see if that will fix the issue..Thanks for weighing in everyone, I will report back. :)

---

### Post by thezman007 on 2013-08-08
And 13.04 simply dies when trying to "Try Ubuntu without installing" Dead screen :( Nothing else

---

### Post by pqwoerituytrueiwoq on 2013-08-08
try xubuntu to see if it is a unity issue with needing a driver to run unity

---

### Post by leosubhadeep on 2013-08-08
The latest Lenovo laptops perform very well (can't say why) for linux distros. I have used Ubuntu, OpenSuse and Fedora on an old core2duo laptop of mine.=D>

---

### Post by Inma_de_la_Torre on 2013-08-08
HP anti-linux? :confused: I got into Linux because I bought a HP computer and it was one of the "courses" they were offering in their website. I know I have a weird graphics card and it took me a while to make everything to play nicely but it worked and as far as I know they actually support Fedora and other open source projects. They might not be the biggest linux supporters but they do more than others and their hardware is not linux unfriendly. 

What problem did you have with them? I ask as it might help others if you give more specifics. :D

---

### Post by thezman007 on 2013-08-08
I may have jumped the gun on HP being anti-Linux it seems :oops: as I turned the UEFI off in BIOS and 12.04 showed up graphically and all :) Dang it, I was really looking forward to spending more money on a cooler computer LOL Thanks for all the help everyone, time to install :)

---

### Post by Yellow Pasque on 2013-08-08
NVM: I typed too slowly again.

Don't get that Acer you linked to. It has hybrid/switchable AMD graphics. Avoid that like the plague!

The Dell and the Asus look pretty similar in terms of CPU/GPU. They both have an Intel HD4000 GPU, which is great for Linux. (Note that Sam's lists the Asus' CPU speed as 2.7GHz, which is the turbo speed. It runs at 1.8GHz normally.)

It would be nice to know what sound and wireless chipsets they use. It would also be nice to know the model of HP you're struggling with.

---

### Post by prodigy_ on 2013-08-08
Your HP looks like a nice enough laptop. So instead of replacing it, try solving the issues first. Chances are it'll work perfectly after some tinkering.

Suggestions:
1) Before trying to install Linux make sure you have the latest BIOS version (just in case). Especially if you're going to wipe Windows 8 completely (upgrading BIOS without a Windows installation may be hard or even impossible in some cases).
2) Specs show it comes with a 5400 RPM HDD. You might want to replace it with a good SSD to improve performance. And the HDD you could then use as an external USB drive (there is a lot of cheap enclosures for 2.5' drives).

---

### Post by Silvernail on 2013-08-09
The H P Pavilion All-In-One come with Ubuntu installed.  google searched it about 3 pm yesterday.

---

### Post by Inma_de_la_Torre on 2013-08-09
I know about Quickbooks not running on Wine, I tried myself. I use Gnucash, which is very nice if you are small business. But they don't have Estimates/Quotes and no way of tracking inventory. I actually considered moving to an open source solution a couple of years ago from Quickbooks in the office. Anyway I couldn't find anything (I'm still interested in the subject though as it seems to be one of the few things I can't find replacement in Linux)

You might be interested in this:

[PostBooks]("http://sourceforge.net/projects/postbooks/") 
[PostBooks 3.2]("http://www.osalt.com/postbooks")

Also you could check [LedgerSMB]("http://ledgersmb.org/"). The packages are in the usual Ubuntu repositories but it might not easy to install in a server, but what I read online.

I didn't know about this package when I was looking but it looks very interesting and promising. And it has an inventory section to track sales.

Alternatively you can go for any of the online accountancy services including the Quickbooks offering:

[QuickBooks Online]("http://quickbooks.intuit.com/online/")

Good luck! :D

---

### Post by Eddie Wilson on 2013-08-09
Well I have several laptops. Ubuntu 13.04 runs just fine on my Lenovo T61, and also on my HP G60-125nr. The only problems I have with my HP, which I also dual boot with Windows 7 that I use for my PLC software, is sometimes it will get caught in a startup loop. It is related to my wireless, but no problems at all with Ubuntu 13.04. Any laptop tech support people will want you to keep the original operating system on your computer and that is because that is what they have been trained to help people with. It's not so much that the HP support is against open source but it's because they know nothing much about it. Also most companies will void your warranty if you change your operating system to something different that they can't support.

---

