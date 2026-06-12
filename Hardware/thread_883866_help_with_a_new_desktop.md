---
title: "help with a new desktop?"
date: 2008-08-08
forum: Hardware
---

### Post by eltiolukee on 2008-08-08
hi, i'm luke.
i'm getting a new desktop tihs month, and i want it to be durable :P
and, my idea was to use some vitualization software so i could use linux, windows and even osx in the same desktop.
the problem is, i can't seem to find the hardware to make this work, so i came here to see if anyone could help me :P
okay, i'll tell you what i'm looking for:)

Processor: AMD Athlon 5600+ x2

Motherboard:
am2+ support; 4 ddr2 slots (support for more than 8 gb), 2+ sata2 ports, and obviously, linux compatibility :P

Video Card: something nice, not too expensive, and with drivers for linux xD

memory: i'll be using 2gb ddr2 kingston 800 x2

and i think that's it.
just feel free to recommend me anything, thanks! :)

---

### Post by tamoneya on 2008-08-08
> **eltiolukee said:**
> hi, i'm luke.
i'm getting a new desktop tihs month, and i want it to be durable :P
and, my idea was to use some vitualization software so i could use linux, windows and even osx in the same desktop.
the problem is, i can't seem to find the hardware to make this work, so i came here to see if anyone could help me :P
okay, i'll tell you what i'm looking for:)

Processor: AMD Athlon 5600+ x2

Motherboard:
am2+ support; 4 ddr2 slots (support for more than 8 gb), 2+ sata2 ports, and obviously, linux compatibility :P

Video Card: something nice, not too expensive, and with drivers for linux xD

memory: i'll be using 2gb ddr2 kingston 800 x2

and i think that's it.
just feel free to recommend me anything, thanks! :)

virtualizing is fine but what do you plan on using as your host OS?

---

### Post by eltiolukee on 2008-08-08
ah, i forgot to say xD
i plan on using some kind of hypervisor that IS a unix-based os , which i don't undestad yet (lol) but yeah, i'm gonna use that :P
did i express myself?
sorry bout my english, not my native lenguage :(

---

### Post by tamoneya on 2008-08-08
you english is pretty good actually.  If you hadnt mentioned it I probably wouldnt have noticed.

Honestly I think it would be easier to run as a dual/triple boot but anyways, what hypervisor do you have in mind?  It is more that we have to check the compatibility of the hypervisor with the hardware.

---

### Post by eltiolukee on 2008-08-08
> **tamoneya said:**
> you english is pretty good actually.  If you hadnt mentioned it I probably wouldnt have noticed.

Honestly I think it would be easier to run as a dual/triple boot but anyways, what hypervisor do you have in mind?  It is more that we have to check the compatibility of the hypervisor with the hardware.

uhm, i'm not sure, it was my dad's idea xD i think it's called Oracle VM, but not really sure about that name :P

---

### Post by tamoneya on 2008-08-08
> **eltiolukee said:**
> uhm, i'm not sure, it was my dad's idea xD i think it's called Oracle VM, but not really sure about that name :P

Im pretty certain that is not what you want.  Oracle is meant for servers and you will lose things like hardware acceleration.  You want to setup a dual boot.  You wont be able to run all your OSes at the same time but you do have them all installed on the same computer and you will be able to access all your files no matter what OS.

EDIT: I forgot the original question while posting.  So assuming that you are running a dual/triple boot The mother board and processor look okay.  I am personally an intel fan but there is nothing wrong with what you picked.  As for a video card I would recommend something like this if you are going to be gaming in windows: [http://www.newegg.com/Product/Product.aspx?Item=N82E16814130318](http://www.newegg.com/Product/Product.aspx?Item=N82E16814130318)
Otherwise go with something a little less powerful(cheaper but still new) like this:[http://www.newegg.com/Product/Product.aspx?Item=N82E16814130085](http://www.newegg.com/Product/Product.aspx?Item=N82E16814130085)

as for RAM i would recommend these sticks.  I use them in all my builds and they work great and are a nice price.
[http://www.newegg.com/Product/Product.aspx?Item=N82E16820231122](http://www.newegg.com/Product/Product.aspx?Item=N82E16820231122)

---

### Post by y@w on 2008-08-08
VMware ESXi is actually [free]("http://whatan00b.com/esxi-for-free") now. Though, you're probably going to need a server-class machine to run it. You'll have to check out the hardware compatability list to see if you can make it work, but that's definitely a viable option as well if you want to go the hypervisor route.

---

### Post by tamoneya on 2008-08-08
> **y@w said:**
> VMware ESXi is actually [free]("http://whatan00b.com/esxi-for-free") now. Though, you're probably going to need a server-class machine to run it. You'll have to check out the hardware compatability list to see if you can make it work, but that's definitely a viable option as well if you want to go the hypervisor route.

ESXi (and ESX) have trouble with sata and ide.  They arent techincally supported although they are supposed to work with some controllers.  I personally have tried getting ESX(i) working on a sata machine and couldnt get it to install.

---

### Post by y@w on 2008-08-08
> 
ESXi (and ESX) have trouble with sata and ide. They arent techincally supported although they are supposed to work with some controllers. I personally have tried getting ESX(i) working on a sata machine and couldnt get it to install.

Wouldn't that be more of a compatibility issue with the controller and/or motherboard? In any case.. a bare-metal hypervisor seems like overkill in this situation. I'd recommend Ubuntu as a host with VirtualBox or VMware GSX. Then you can be significantly more open as far as hardware goes. They'll run on pretty much anything i386 or x64 based.

---

### Post by tamoneya on 2008-08-08
> **y@w said:**
> Wouldn't that be more of a compatibility issue with the controller and/or motherboard? In any case.. a bare-metal hypervisor seems like overkill in this situation. I'd recommend Ubuntu as a host with VirtualBox or VMware GSX. Then you can be significantly more open as far as hardware goes. They'll run on pretty much anything i386 or x64 based.

Yes it would have to do with the controller.  The reason why sata doesnt work is because they dont put support into the drivers for sata controllers.  There are a handful of sata controllers which work but not many.

---

### Post by eltiolukee on 2008-08-08
> **tamoneya said:**
> Im pretty certain that is not what you want.  Oracle is meant for servers and you will lose things like hardware acceleration.  You want to setup a dual boot.  You wont be able to run all your OSes at the same time but you do have them all installed on the same computer and you will be able to access all your files no matter what OS.

EDIT: I forgot the original question while posting.  So assuming that you are running a dual/triple boot The mother board and processor look okay.  I am personally an intel fan but there is nothing wrong with what you picked.  As for a video card I would recommend something like this if you are going to be gaming in windows: [http://www.newegg.com/Product/Product.aspx?Item=N82E16814130318](http://www.newegg.com/Product/Product.aspx?Item=N82E16814130318)
Otherwise go with something a little less powerful(cheaper but still new) like this:[http://www.newegg.com/Product/Product.aspx?Item=N82E16814130085](http://www.newegg.com/Product/Product.aspx?Item=N82E16814130085)

as for RAM i would recommend these sticks.  I use them in all my builds and they work great and are a nice price.
[http://www.newegg.com/Product/Product.aspx?Item=N82E16820231122](http://www.newegg.com/Product/Product.aspx?Item=N82E16820231122)

actually, he told me that oracle's VMware was for desktops, and he works there, so the license isn't a problem xD

and, what motheboard is okay? i'm asking for advise on WHICH should i buy :P
video: not much, just the basic, i'll upgrade later, when i can pay for one myself :P

---

### Post by tashmooclam on 2008-08-08
I doubt you can run Apple OS 10 on hardware that is not Apple. I would buy a mac mini they are awesome little machines and they use very little electricity and take up very little space. If you have a Mac, then you can run Ubuntu, Apple and Windows.

---

### Post by tamoneya on 2008-08-08
> **eltiolukee said:**
> actually, he told me that oracle's VMware was for desktops, and he works there, so the license isn't a problem xD

and, what motheboard is okay? i'm asking for advise on WHICH should i buy :P
video: not much, just the basic, i'll upgrade later, when i can pay for one myself :P

Here is what I would use for a mobo.  [http://www.newegg.com/Product/Product.aspx?Item=N82E16813128341](http://www.newegg.com/Product/Product.aspx?Item=N82E16813128341)

It will take 4 DIMMs and supports AM2+.  Also it is a small form factor which is always nice.  You can put it in a microATX case if you like although it will fit in a larger case if you prefer.  Also it has integrated graphics.  Use that for now and then when as you say you get the money you can add a graphics card.

Also could you check on exactly what your dad wants you to use for this hypervisor.  I want to make sure this is going to work well for you and currently im still in doubt.  Oracle in general is a enterprise/server company and I just looked on their website and I dont see a single product aimed at consumers.

---

### Post by tamoneya on 2008-08-08
> **tashmooclam said:**
> I doubt you can run Apple OS 10 on hardware that is not Apple. I would buy a mac mini they are awesome little machines and they use very little electricity and take up very little space. If you have a Mac, then you can run Ubuntu, Apple and Windows.

Ever since apple moved to intel x86 processors it has been possible to run apple OSes on normal PC hardware if you put some thought into it.  It is beneficial since apple hardware carries a fairly high premium.  The performance/$ ratio is much higher if you build it like this.  

I however cannot tell you how well this hardware will work with apple.  If you want to do that look here: [http://www.hackint0sh.org/forum/forumdisplay.php?f=133](http://www.hackint0sh.org/forum/forumdisplay.php?f=133)

---

### Post by eltiolukee on 2008-08-08
> **tashmooclam said:**
> I doubt you can run Apple OS 10 on hardware that is not Apple. I would buy a mac mini they are awesome little machines and they use very little electricity and take up very little space. If you have a Mac, then you can run Ubuntu, Apple and Windows.

lol, i know, i'm using one now :P the only cons are the disk and the memory xD
AND the price, or at least in argentina, prices are 3 times in dollars. stupid taxes.


> **tamoneya said:**
> Here is what I would use for a mobo.  [http://www.newegg.com/Product/Product.aspx?Item=N82E16813128341](http://www.newegg.com/Product/Product.aspx?Item=N82E16813128341)

It will take 4 DIMMs and supports AM2+.  Also it is a small form factor which is always nice.  You can put it in a microATX case if you like although it will fit in a larger case if you prefer.  Also it has integrated graphics.  Use that for now and then when as you say you get the money you can add a graphics card.


only thing i can say about that mobo: WOW! i want xD

but, really, it's pretty good, even the integrated video. loved it.
let's see if dad says he'll buy it. i hope he does :D

---

### Post by tamoneya on 2008-08-09
> **eltiolukee said:**
> only thing i can say about that mobo: WOW! i want xD

but, really, it's pretty good, even the integrated video. loved it.
let's see if dad says he'll buy it. i hope he does :D

Its a great board.  Ive built with it myself.  Triple core processor.  I built it for work and it is running like a charm.

---

### Post by eltiolukee on 2008-08-09
> **tamoneya said:**
> Its a great board.  Ive built with it myself.  Triple core processor.  I built it for work and it is running like a charm.

uhm, one last question about this mobo.
it says it has 128 mb ddr3 onboard, what does that exactly mean?

---

### Post by tamoneya on 2008-08-09
> **eltiolukee said:**
> uhm, one last question about this mobo.
it says it has 128 mb ddr3 onboard, what does that exactly mean?

That is memory for the integrated graphics card.  ddr3 is faster than ddr2 and has been used for gfx cards for a while.  This also means that the graphics card wont be stealing from system memory.

---

### Post by starcannon on 2008-08-09
tamoneya in post #4 speaks correctly.
I have tried to install OSX into a virtual machine, I spent many many hours on it, I don't know if anyone has had a "success" but my attempts were what I'd consider failures.

Dual booting OSX and Linux would be your best option, then run windows in a virtual machine (I like *Sun Virtual Box* you may like something else).

I know that I have seen hackintosh for the AMD cpu's, but it seems like the biggest variety is for the Intel CPU's (someone correct me if I am wrong our outdated).

Anyway, GL with your project, you've definitely decided to look into the abyss with this one. 

P.S. if this is your first ever Linux install, or your first ever hackintosh install, I'd recommend doing one or the other as a single project(you can chop the hard drive up and install grub later if you choose to do hackintosh first). But to try and do all of this at once as a first timer on all of it... well lets just say, *very ambitious*

---

### Post by mikjp on 2008-08-09
> **tamoneya said:**
> Ever since apple moved to intel x86 processors it has been possible to run apple OSes on normal PC hardware if you put some thought into it.  It is beneficial since apple hardware carries a fairly high premium.  The performance/$ ratio is much higher if you build it like this.

Performance/$ is not the only thing that counts if you want to use a Macintosh. What about design/$ ratio of custom systems?

OTOH, I have installed Debian on my iBook :-)

mikko

---

### Post by eltiolukee on 2008-08-09
> **starcannon said:**
> tamoneya in post #4 speaks correctly.
I have tried to install OSX into a virtual machine, I spent many many hours on it, I don't know if anyone has had a "success" but my attempts were what I'd consider failures.

Dual booting OSX and Linux would be your best option, then run windows in a virtual machine (I like *Sun Virtual Box* you may like something else).

I know that I have seen hackintosh for the AMD cpu's, but it seems like the biggest variety is for the Intel CPU's (someone correct me if I am wrong our outdated).

Anyway, GL with your project, you've definitely decided to look into the abyss with this one. 

P.S. if this is your first ever Linux install, or your first ever hackintosh install, I'd recommend doing one or the other as a single project(you can chop the hard drive up and install grub later if you choose to do hackintosh first). But to try and do all of this at once as a first timer on all of it... well lets just say, *very ambitious*

not my first linux instal at all, i've been using linux for years now xD i've used ubuntu and mandriva, but in the hackintosh side, actually this is the first time i've heard of it xD

---

