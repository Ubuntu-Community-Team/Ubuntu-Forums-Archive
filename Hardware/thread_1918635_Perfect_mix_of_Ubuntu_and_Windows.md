---
title: "Perfect mix of Ubuntu and Windows?"
date: 2012-02-01
forum: Hardware
---

### Post by Cairo_Delgado on 2012-02-01
I have a simple questions for you all. On my laptop I dual boot between windows 7 and Ubuntu 11.04 (will upgrade to 11.10), I don't like the windows OS that much and only use it for my GAMING, iTunes, and other windows specific programs. I would prefer to completely replace windows on my computer with Ubuntu but I can't live without my windows specific programs that DON'T run in W.I.N.E.

Is it possible, or, do you all think that I would be able to run Ubuntu only on my laptop and then operate / install Windows 7 (8 when it comes out) in a virtual machine within Ubuntu and play my GAMES / run my programs that way? Or would I run into multiple problems trying to run more hard core windows specific programs in a virtual machine?

If problems would arise, or if you guys and girls know of any better ways for me to achieve this "Perfect Mix", then by all means let me know!:KS Im fairly new to Ubuntu and don't know much but love its fluidity, beauty, and power. I can't stop using it.

---

### Post by cortman on 2012-02-01
> **Cairo_Delgado said:**
> I have a simple questions for you all. On my laptop I dual boot between windows 7 and Ubuntu 11.04 (will upgrade to 11.10), I don't like the windows OS that much and only use it for my GAMING, iTunes, and other windows specific programs. I would prefer to completely replace windows on my computer with Ubuntu but I can't live without my windows specific programs that DON'T run in W.I.N.E.

Is it possible, or, do you all think that I would be able to run Ubuntu only on my laptop and then operate / install Windows 7 (8 when it comes out) in a virtual machine within Ubuntu and play my GAMES / run my programs that way? Or would I run into multiple problems trying to run more hard core windows specific programs in a virtual machine?

If problems would arise, or if you guys and girls know of any better ways for me to achieve this "Perfect Mix", then by all means let me know!:KS Im fairly new to Ubuntu and don't know much but love its fluidity, beauty, and power. I can't stop using it.

You could definitely run Win7 or 8 in a VBox inside Ubuntu- BUT performance would be pretty puny compared to a standard HD installation.
Honestly, your current setup is probably about the best. I still dual-boot between Win7 and Ubuntu (although I haven't booted into 7 for months). It doesn't take up much space on my HD and is there and quite fast whenever I may need it.
Why would you prefer to run Windows in a VBox? Maybe you have some other reason I'm not thinking of.

---

### Post by Cairo_Delgado on 2012-02-02
How much space did you set for your windows partition? How do I know how much space is efficient?

Switching between OS's is a pain, while having acess to windows within ubuntu seems like the better option. Plus I have partitioned my laptop and I heard that if the Windows partition gets a virus then it could effect my Ubuntu partition.

As far as diverting power goes, if I have a i5 / i7 processor with 4, 8, or 16gb of ram, and maybe a dedicated graphics card for added power do you think that it would divide those specs and then become ****** or still be adequate if I was to choose to use VM Ware / Virtual Box to emulate Windows.

Having windows in a separate partition for only using it to game (mostly) is ridiculous in my opinion.

---

### Post by cortman on 2012-02-02
Ok, I can understand that switching between OS's would be a pain. I haven't run Windows in a VBox yet, but all my Linux installations typically ran pretty slow, even with a nice sized chunk of ram apportioned to them (4-6 GB). Plus 3D effects have thus far refused to work for me. Don't know if that'd be a problem with Windows or not.
I have a 750 GB HD, and I think I have 200 GB set for Windows (which is way more than enough).
In my experience the problem with VBoxes is not that they need high spec, but that they don't utilize hardware very well.

---

### Post by snowpine on 2012-02-02
I would do it the other way around, install Windows as the "host" (to run games natively) and then Ubuntu as the "guest" in a virtual machine (for Linux goodness).

But of course it depends on the games in question. Minesweeper, solitaire, tetris, etc. will run fine in a Windows virtual machine. :)

---

### Post by TheFu on 2012-02-02
> **Cairo_Delgado said:**
> 
As far as diverting power goes, if I have a i5 / i7 processor with 4, 8, or 16gb of ram, and maybe a dedicated graphics card for added power do you think that it would divide those specs and then become ****** or still be adequate if I was to choose to use VM Ware / Virtual Box to emulate Windows.

**Virtualization works nicely on modern hardware except when it comes to heavy graphics and gaming.**  Your physical hardware doesn't matter to the virtual machine.  It sees emulated hardware - emulated GPU, emulated HDD controller, emulated NIC, emulated mouse, keyboard, CPU, RAM, USB ports, etc  ... everything is emulated.  

Ok, some games work just fine inside emulations, but those aren't FPS or newish games.  Perhaps games from 2003 would work fine. I dunno.

If you want good performance for modern games, you need the desired OS running on the desired hardware.

Ok, with that said, I'll admit to running Ubuntu inside a VM on a laptop running Win7x64.  It is extremely stable and I never have to deal with wifi setup issues in Linux. After all, to the Linux virtual machine, my wifi adapter looks like an Intel PRO/1000 NIC.  This Linux install is extremely functional and fast running this way.

I also run a few native (4) and virtual Linux machines (20 or so) on other hardware.

In the future, may I suggest that you choose the devices and hardware you purchase more selectively to avoid single-source-proprietary solutions, like those from Apple?  Look for devices that follow open standards and do not require proprietary software to be used.

---

### Post by Cairo_Delgado on 2012-02-04
Okay so I guess virtually running the Windows install isn't a good idea then. Those specs I listed for the computer aren't my computer, but, they are potential specs to the new computers I am choosing between buying. Dual booting windows with Ubuntu would be my next most preferred option since I don't want Ubuntu in a VM I want the actual thing, so, how would I correctly partition my system in windows and divide my space accordingly? Should I use  the Ubuntu live cd to partition or should I use some windows program in windows?

---

### Post by LinuxFan999 on 2012-02-04
> **cortman said:**
> Ok, I can understand that switching between OS's would be a pain. I haven't run Windows in a VBox yet, but **all my Linux installations typically ran pretty slow**, even with a nice sized chunk of ram apportioned to them (4-6 GB). Plus 3D effects have thus far refused to work for me. Don't know if that'd be a problem with Windows or not.
I have a 750 GB HD, and I think I have 200 GB set for Windows (which is way more than enough).
In my experience the problem with VBoxes is not that they need high spec, but that they don't utilize hardware very well.

I agree with you. The speed of My Linux installations in Virtualbox has varied from a little slow (Debian, Puppy Linux) to extremely sluggish (Google Chromium OS), no matter how much memory I give them, while operating systems like Haiku, and even Windows (especially Windows XP and earlier), are speedy.

---

