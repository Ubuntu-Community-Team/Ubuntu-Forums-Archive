---
title: "linux laptop support in general"
date: 2005-10-07
forum: Hardware &amp; Laptops
---

### Post by replacement on 2005-10-07
a while ago, i read an article saying the decline in the market of desktop PC and the trend in "mobile computing". it makes me start wondering why linux on laptops is still in a hazy state. by that, i mean no complete or comparable acpi support, no hard drive suspension. you may say there're many posts/tutorials/hacks/patches/... addressing these issues. yes, i know that. but it seems a waste of time, doesn't it? i do enjoy the power and efficiency of linux/unix offers. it's just my thought linux would really gain significant popularity if it becomes more "mobile".

---

### Post by 23meg on 2005-10-07
what exactly do you recommend that should be done to make linux more "mobile"?

---

### Post by snowjunkie on 2005-10-07
Ubuntu works great on my laptop!

---

### Post by replacement on 2005-10-07
[QUOTE=23meg]what exactly do you recommend that should be done to make linux more "mobile"?[/QUOTE]

at least, i think (IMHO) the acpi should work comparable to their state in windows xp. the most important for mobile users is power management, sleep to the memory, sleep to the hard drive (hibernate). and these would be my minimum requirement. imagine you have to shutdown your laptop everytime you leave library or coffee shop when you run linux, and wait for a minute or two for it to boot up next time. these functions seem to work for certain brand/model/, but most of time it needs "hacking"

---

### Post by J D Wijbenga on 2005-10-08
Works great on my Acer Aspire 2000. Wireless, suspent, cd-burning, the lot. Ubuntu is realy good on laptops I think.

JD

---

### Post by imagine on 2005-10-08
[QUOTE=replacement]at least, i think (IMHO) the acpi should work comparable to their state in windows xp.[/QUOTE]True, but on the other hand, its not really the task of the Ubuntu or other OSS developers to fix the broken ACPI implementation for the notebook manufacturers. Although it boils down to that in the end...

In many cases the "Designed for Windows" sticker is nothing more than stating that the DSDT is not fully functional, but it was just put enough work in it that it works with the current versions of Windows.

Have a look at [http://acpi.sourceforge.net](http://acpi.sourceforge.net) about that:
*DSDT is an acronym for Differentiated System Description Table. This table contains the Differentiated Definition Block, which supplies the information and configuration information about the base system. It is always inserted into the ACPI Namespace by the OS at boot time. Unfortunately, many hardware vendors and OEMs are not capable of supplying fully functional tables (not even the members of the ACPI SIG), see also the blacklist. So there is a need to patch these tables by us.*

---

### Post by towsonu2003 on 2005-10-09
quote/ "True, but on the other hand, its not really the task of the Ubuntu or other OSS developers to fix the broken ACPI implementation for the notebook manufacturers." /quote

This is the most irritating respond I hear whenever I newbie asks "why isn't this supported?". I believe this is just a blaming game on the part of the linux developer community. It is a weird way of saying "sorry, we are not _able_ to make your driver work". 

There is no way manufacturers will give away their drivers for "free". They have contracts with Windows that _allows_ them to sell their products to windows customers. 

Linux develoepers (including but not only the "enterprize distro developers"), if they are keen in promoting linux to the _end_ user, have to do more extensive hacking to come up with generic drivers (or software) to enable win-drivers... ndiswrapper, although buggy and hard to use, is a good example to that. The linmodem project is another good example. Again, both of these projects need more support from the community (including the distro developers, who use these in their advantage while promoting their distros) so that they can become bug-free and universal. 

Think of this like: "Would my grandma want to leanr linux in its current state?" Until the answer is yes, Windows will win (i.e. we will buy laptops designed for windows), regardless of its politics and the practical disadvantages of its use. 

Also, as a response to users who say "hey it works with my laptop xyzt". Well, it works with mine too, but think big. It has to work with _all_ laptops. Take a look at the HCL list of ubuntu for laptops. Full of notes about how to tweak and fix and etc. If a laptop works fully with a linux distro, that means: 
1. install linux
2. run linux for the first time (push the power button and it runs no problem)
3. find drivers for your gadgets and install them (all gadgets are now fully working)
4. start doing your job

Note that there is no "tweak and play around" after the 3rd point. Until this happens with _all_ laptops running linux, your specific laptop means almost nothing. 

Please don't think I am insulting the linux community or anyone here. This is what I feel after my experience of linux with 6-7 months of installing-uninstalling-tweaking-breaking linux distros and compiling-recompiling-failing kernel and downloading-installing-compiling so-called drivers and driver-like-softwares. 

To me, ideally, linux community needs a project whose sole purpose is to _hack_ each and every gadget as it is manufactured, and find a way to release it legally under GPL. 

At least, the community needs smaller but numerous projects which will produce generic drivers (by writing them from scratch or by hacking the windows drivers) that will work with a range of gadget (such as the usbstorage which works with external enclosures as well as staff like digital cameras; or linmodems which makes it possible for winmodems to run; or ndiswrapper that adds support for a range of wireless cards)...

Thats what I think about driver support.

---

### Post by replacement on 2005-10-09
[QUOTE=towsonu2003]quote/ "True, but on the other hand, its not really the task of the Ubuntu or other OSS developers to fix the broken ACPI implementation for the notebook manufacturers." /quote

This is the most irritating respond I hear whenever I newbie asks "why isn't this supported?". I believe this is just a blaming game on the part of the linux developer community. It is a weird way of saying "sorry, we are not _able_ to make your driver work". 

There is no way manufacturers will give away their drivers for "free". They have contracts with Windows that _allows_ them to sell their products to windows customers. 

Linux develoepers (including but not only the "enterprize distro developers"), if they are keen in promoting linux to the _end_ user, have to do more extensive hacking to come up with generic drivers (or software) to enable win-drivers... ndiswrapper, although buggy and hard to use, is a good example to that. The linmodem project is another good example. Again, both of these projects need more support from the community (including the distro developers, who use these in their advantage while promoting their distros) so that they can become bug-free and universal. 

Think of this like: "Would my grandma want to leanr linux in its current state?" Until the answer is yes, Windows will win (i.e. we will buy laptops designed for windows), regardless of its politics and the practical disadvantages of its use. 

Also, as a response to users who say "hey it works with my laptop xyzt". Well, it works with mine too, but think big. It has to work with _all_ laptops. Take a look at the HCL list of ubuntu for laptops. Full of notes about how to tweak and fix and etc. If a laptop works fully with a linux distro, that means: 
1. install linux
2. run linux for the first time (push the power button and it runs no problem)
3. find drivers for your gadgets and install them (all gadgets are now fully working)
4. start doing your job

Note that there is no "tweak and play around" after the 3rd point. Until this happens with _all_ laptops running linux, your specific laptop means almost nothing. 

Please don't think I am insulting the linux community or anyone here. This is what I feel after my experience of linux with 6-7 months of installing-uninstalling-tweaking-breaking linux distros and compiling-recompiling-failing kernel and downloading-installing-compiling so-called drivers and driver-like-softwares. 

To me, ideally, linux community needs a project whose sole purpose is to _hack_ each and every gadget as it is manufactured, and find a way to release it legally under GPL. 

At least, the community needs smaller but numerous projects which will produce generic drivers (by writing them from scratch or by hacking the windows drivers) that will work with a range of gadget (such as the usbstorage which works with external enclosures as well as staff like digital cameras; or linmodems which makes it possible for winmodems to run; or ndiswrapper that adds support for a range of wireless cards)...

Thats what I think about driver support.[/QUOTE]

exactly, to the point. the big picture!!!!

---

### Post by skirkpatrick on 2005-10-09
Writing a driver for a device that you don't have the hardware specs for is incredibly difficult.  I can point you to the ivtv project that works on drivers for video capture cards.  I monitored their development mail list for a couple of months when I bought a new Hauppage card.  It's not that they are trying hard but it's hard to reverse engineer hardware especially when it's embedded in ASICs and FPGAs.

---

### Post by replacement on 2005-10-09
[QUOTE=skirkpatrick]Writing a driver for a device that you don't have the hardware specs for is incredibly difficult.  I can point you to the ivtv project that works on drivers for video capture cards.  I monitored their development mail list for a couple of months when I bought a new Hauppage card.  It's not that they are trying hard but it's hard to reverse engineer hardware especially when it's embedded in ASICs and FPGAs.[/QUOTE]

i think it all comes down to whether hardware makers will profit from selling their product that's going to run linux on them.

---

### Post by skirkpatrick on 2005-10-09
Most hardware manufacturers seem to fear that if they open up their design, their competitors will suck up all their innovation.  However, they aren't prepared to to support even proprietary Linux drivers because "the market is too small".  An laptops are even more integrated than desktops.

---

### Post by Starman on 2005-10-09
It really doesn't matter whose 'fault' it is. Whether its 'evil hardware venders', 'broken technology', etc... Both sides of this debate have supportable positions. It is much more difficult to keep up with drivers without vender support. I am amazed so many devices actually do just work. The flip side is that those users that aren't hobbyists or otherwise pre-disposed to spend time figuring out how to make devices functional will just abandon linux and return to WinXP.

With that said, the fact remains that the original point made in this thread is correct. Linux does not reliably support the capabilities mobile users depend on. Capabilities that are taken for granted in WinXP.

Ubuntu has done the best job of any of the linux distributions I've tried in laptop support but I still had to manually edit files and install individual driver files in order to get Dell wireless and Lid suspension to work. And what I accept for wireless and power mgmt on linux would be intolerable on WinXP.

Many thanks to those on this forum who have helped me get this far.

When I really need my battery to last or flawless wireless I boot to XP, otherwise I use ubuntu.

...my two cents

---

### Post by replacement on 2005-10-10
[QUOTE=Starman]It really doesn't matter whose 'fault' it is. Whether its 'evil hardware venders', 'broken technology', etc... Both sides of this debate have supportable positions. It is much more difficult to keep up with drivers without vender support. I am amazed so many devices actually do just work. The flip side is that those users that aren't hobbyists or otherwise pre-disposed to spend time figuring out how to make devices functional will just abandon linux and return to WinXP.

With that said, the fact remains that the original point made in this thread is correct. Linux does not reliably support the capabilities mobile users depend on. Capabilities that are taken for granted in WinXP.

Ubuntu has done the best job of any of the linux distributions I've tried in laptop support but I still had to manually edit files and install individual driver files in order to get Dell wireless and Lid suspension to work. And what I accept for wireless and power mgmt on linux would be intolerable on WinXP.

Many thanks to those on this forum who have helped me get this far.

When I really need my battery to last or flawless wireless I boot to XP, otherwise I use ubuntu.

...my two cents[/QUOTE]
or, you can go get an apple, forgive me saying the evil idea here. it would be interesting to see how it turns out after apple release their x86 line of product.

---

### Post by garnertr on 2005-10-10
I'm running Alienware Laptap, P4 1700, nothing fancy but i've been having a blast with it.  So far nothing big to report.

but it works fine for me...

---

### Post by hlfrk414 on 2005-10-10
I would like to throw this out, as a new member to this forum, as as someone who just started using linux a week ago.
*ahem*
[SIZE="4"]**I just got my wireless working on this laptop with Ndiswrapper! yayyyyyyy!!!**[/SIZE]
Thank you Kubuntu wiki! It only took compiling from source, overwriting the pakages built into the system, and then running the commands I had already done a hundred times! and at first it didn't look like it worked, as it listed my wireless as eth1, instead of wlan0! and then doing a total system freeze on the reboot! But now it works!
Thank you.

P.S. I am actually enjoying myself so far, as I like the OS. Plus I haven't had a software related challenge in a while. **Now** to get kubuntu to find the actual battery power level, No, the battery *isn't* at zero charge.

---

### Post by robins_web on 2005-10-10
The reason I use Ubuntu in the first place is that it's the only distro I've tried that works without a problem on my Compaq Presario 2200. I tried Fedora, SuSE, and a couple of others with no success.

---

### Post by nocturn on 2005-10-11
[QUOTE=replacement]a while ago, i read an article saying the decline in the market of desktop PC and the trend in "mobile computing". it makes me start wondering why linux on laptops is still in a hazy state. by that, i mean no complete or comparable acpi support, no hard drive suspension. you may say there're many posts/tutorials/hacks/patches/... addressing these issues. yes, i know that. but it seems a waste of time, doesn't it? i do enjoy the power and efficiency of linux/unix offers. it's just my thought linux would really gain significant popularity if it becomes more "mobile".[/QUOTE]

If laptop manufacturers would stick to standards (every acpi implementation the same), we would not be in this mess.  But as it stands, they all do everything differently, mostly even writing the hardware to comply with XP instead of the real standard.

---

### Post by towsonu2003 on 2005-10-12
while the linux gurus work on hacking drivers (which is a very basic need for linux to win the competition for end users like my mom, and even me), here is a question: what can a newbie (who actually wants to switch) do to contribute to this process (except, may be, posting to HCLs about own hardware)?

---

### Post by NeilSch on 2005-10-12
1. If you haven't already seen it, check out the thread "Laptops designed for Linux", especially this from vicG:

[QUOTE=vicG]Have you looked at [http://www.emperorlinux.com/](http://www.emperorlinux.com/)?  
You can have a laptop where everything not only works under Linux, but *IS* working under Linux when it arrives at your door.[/QUOTE]

2. There's not much that compares with _economic pressure_. Linux folks should get in the habit of asking vendors/shops at every opportunity: do you have laptops that conform to all standards that enable non-Windows OS developers to make full use of the hardware?

Folks who have already made purchases and have problems with Linux where non-standard interfaces are proven or suspected should be encouraged to contact their vendor and (politely) express their dissatisfaction, with a hint that this will impact future purchasing decisions. In particular, when the rev-eng driver gurus (the real heroes of this story) run into a brick wall on a particular make, there should be an email campaign to the vendor in which very specific questions (what is the code sequence that will enable feature blah on hardware blah) are posed. I highly doubt I'm saying anything new here.

3. Now, if there are any gurus reading this, how about helping **moi**? See thread "Unable to get online with Live CD on Toshiba Tecra A3" in the forum "Ubuntu Live CD" (Ubuntu Hoary Hedgehog 5.04, Hoary 5.04 Application Support).

---

