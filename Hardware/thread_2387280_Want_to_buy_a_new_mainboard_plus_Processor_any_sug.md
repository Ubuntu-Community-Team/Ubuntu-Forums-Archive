---
title: "Want to buy a new mainboard plus Processor any suggestions"
date: 2018-03-17
forum: Hardware
---

### Post by Mike E Tomlinson on 2018-03-17
Any suggestions as to what board would be most compatible?  I was wanting a new ASUS Board but seems like they don't let us use anything but Windows.  GRRR 
I have been with ASUS for over 10 years, Never an issue. Suggestions would be appreciated. Just need Mainboard,Processor. GPU and  Ram.  Price around  16.00.00 give or take a few dollars.
Prefer Intel.

---

### Post by Yellow Pasque on 2018-03-17
Suggestion: Figure out what CPU you want first, so you know what socket you need on the mobo. I mean, people can give you suggestions, but you need to provide more detail on what you plan to do with the system. We can't guess how powerful a CPU you'll need, how much RAM you need or how many USB ports you need.

>  I was wanting a new ASUS Board but seems like they don't let us use anything but Windows.

This is news to me. Please explain.

> Price around 16.00.00

I'm going to guess that's not 16 American dollars? If you want people to shop for you, you should state your locale and maybe give a few vendors/sites that you'll be using for price reference.

---

### Post by Mike E Tomlinson on 2018-03-17
Thanks for the quick response and sorry I didn't give you  more info.

The ASUS ROG Maximus X Hero. When I was checking into it, said that it was only compatible with Windows
I phoned ASUS and they gave me a site to check for Compatibility. Sad thing is all the boards lilsted were of the DDR 3
Anyone have good experiences with other Mainboards, or know of anyone who has had any.  
I'm From Canada
My system right now is ASUS p9x79, 16 gig Kingston RAM, Gforce GTX 760. That is what I would like to replace.

I would like to buy a system that would be good till at least 4 years or so. Any suggestions would be appreciated

---

### Post by QIII on 2018-03-17
Hello!

I have twice edited your misspelling of "Windows".  Please spell it correctly from here on out.

Thank you.

---

### Post by Yellow Pasque on 2018-03-17
[https://phoronix.com/scan.php?page=category&item=Motherboards](https://phoronix.com/scan.php?page=category&item=Motherboards)

---

### Post by 1clue on 2018-03-17
What is your system for?
[LIST=1]
[*]Basic desktop
[*]Multimedia editing
[*]Gaming
[*]Programming
[*]Many VMs on a desktop box
[*]Server system
[*]Other
[/LIST]

We could give references all day, but let's start out with what you want to do with it, how much you want to spend, and any specifics about memory or drive type is most appealing to you.

Frankly I'm tempted to give you a link to supermicro, but if you want a basic desktop then that is probably not a good choice.

---

### Post by ank2 on 2018-03-17
> **Mike E Tomlinson said:**
> Any suggestions as to what board would be most compatible?  I was wanting a new ASUS Board but seems like they don't let us use anything but Windows.  GRRR 
I have been with ASUS for over 10 years, Never an issue. Suggestions would be appreciated. Just need Mainboard,Processor. GPU and  Ram.  Price around  16.00.00 give or take a few dollars.
Prefer Intel.

In my opinion any board will work with Ubuntu. If the hardware is bleeding edge it might take a few weeks or months until fully supported.

If you can, burn Ubuntu to a CD/DVD or install it on an USB stick and go to the retailer's shop and ask him if you can boot a desired machine from it to scope out if Ubuntu works on it.

---

### Post by Mike E Tomlinson on 2018-03-18
Thanks again. Again I apologize
I should have been more explicit.  
I will use it for almost everything movie editing gaming etc.
OOOPs about the 1600.00

				 				 					 						 	[**[COLOR=#000000]ank2[/COLOR]**]("https://ubuntuforums.org/member.php?u=1903870"), 	 [**[COLOR=#000000]Temüjin[/COLOR]**[COLOR=#000000]  th[/COLOR]**[COLOR=#000000][/COLOR]**]("https://ubuntuforums.org/member.php?u=327594")anks for the headsup on mainboards.

---

### Post by 1clue on 2018-03-18
> **ank2 said:**
> In my opinion any board will work with Ubuntu. If the hardware is bleeding edge it might take a few weeks or months until fully supported.

If you can, burn Ubuntu to a CD/DVD or install it on an USB stick and go to the retailer's shop and ask him if you can boot a desired machine from it to scope out if Ubuntu works on it.

In my experience it may take years for some less-common hardware to become supported, if it ever does. I've had that experience with motherboards and with printers. My Canon printer took more than 3 years to be supported after I bought it, and then it was a huge PITA to get it to stay working. Finally, almost 7 years in it works nicely.

---

### Post by rbmorse on 2018-03-18
My experience with ASUS motherboards and Linux has generally been very good over the years.  Any of the current offerings should work fine. One possible area of concern is the availability of solid drivers for the motherboard's wi-fi module (if equipped). Sometimes that takes a while to get caught up. 

If you want to be really careful about Linux support, I'd suggest looking at one of the 7th generation Intel CPU's and chipsets (a ROG Maximus with the Z-270 series chipset and a supported socket 1151 CPU). That's last year's model, so to speak, but they've been out long enough for any problems to have been exposed and dealt with.  Install the latest BIOS/UEFI update before installing the operating system and you should be good. 

For a general purpose machine I like the low TMD i7 CPU that is priced at around $300 - $325 USD.  That one always seems to be very close to the price/performance "sweet spot" in that it is full-featured and reasonably close in performance to the more powerful processors. You can spend more for more performance, but you have to spend a lot for very little gain and have to deal with higher power and cooling requirements, too. 

Right now I'm composing this on a machine built around an ASUS Z97-Pro motherboard with i7-4770K CPU.  It's been perfect for every Linux I've tried with it.  The 7th gen equivalent would be the Z270 Pro and the i7-7770 CPU.  I personally think the differences between the Pro and Maximus series motherboards are largely marketing, but take a look at the detailed specs to make sure you get the featureset you need.  I personally don't need integrated wi-fi, for example, so i don't buy it. 

This machine has 32GB of RAM installed and that is excessive.  Unless you know you have a _specific_ application that will benefit from more RAM there's no reason to buy more than 16GB for a Linux desktop computer.   My current memory commit is 3.1GB, and that's with /tmp set up on a ramdisk and the browser cache softlinked to /tmp.

---

### Post by 1clue on 2018-03-19
Regarding Asus specifically, I'd also have a concern about buggy boards and bad peripherals.

I'm currently typing on an Asus p6t motherboard. While it works fine for general purpose things, it has two specific issues which I find bothersome.

First, the built-in ethernet card is Realtek. Shortly after I bought the board I found out that Realtek and other bargain peripheral manufacturers save a few bucks by supplying minimal hardware and offloading much of the network stack to the CPU. Comparing it to a gigabit Intel ethernet controller, which has minimal CPU interrupts at full load, the Realtek card generates lots of interrupts. You won't likely notice a performance loss unless you saturate both the NIC and the CPU at the same time. Which I do.

Second, there's a bug in the board which affects virtualization. While there is currently a software workaround and I can run virtualization software like VirtualBox or KVM, it runs noticeably slower on this system compared to another system with roughly equivalent specs.

I bought the board knowing about the second issue, but figured it would only be a few weeks before a fix was presented. Unless it happened relatively recently the fix is still pending, the workaround is on the Linux side.

---

### Post by Yellow Pasque on 2018-03-19
> I'm currently typing on an Asus p6t motherboard. While it works fine for general purpose things, it has two specific issues which I find bothersome. First, the built-in ethernet card is Realtek.

This is not specific to Asus. The other major mainboard manufacturers use plenty of Realtek LAN chips too, especially in their lower and midrange priced boards.

I really don't have brand loyalty when it comes to mobo's. I've gotten some good and some quirky boards from every manufacturer.

---

### Post by 1clue on 2018-03-19
> **Temüjin said:**
> This is not specific to Asus. The other major mainboard manufacturers use plenty of Realtek LAN chips too, especially in their lower and midrange priced boards.

I really don't have brand loyalty when it comes to mobo's. I've gotten some good and some quirky boards from every manufacturer.

I didn't mean to imply that it was only Asus did this, nor did I mean it was a problem with every Asus board. I found 2 things about the board which not only bugged me but impacted my intended use of the system.  Now I pay attention to that sort of thing before buying.

I've found that, at least with respect to the systems I've been shopping for, if your motherboard has an Intel nic which uses the 'igb' driver, then generally speaking the rest of the components on the board are at least not bargain basement products.

---

### Post by rbmorse on 2018-03-19
> **1clue said:**
> Regarding Asus specifically, I'd also have a concern about buggy boards and bad peripherals.

I'm currently typing on an Asus p6t motherboard. While it works fine for general purpose things, it has two specific issues which I find bothersome.



The P6T motherboard is based upon the Intel X58 chipset which was released in 2008.  More contemporary models should better support VM operations.  I wouldn't hold my breath waiting for a solution from Intel. They eol'd the chipset in 2012.

---

### Post by 1clue on 2018-03-19
> **rbmorse said:**
> The P6T motherboard is based upon the Intel X58 chipset which was released in 2008.  More contemporary models should better support VM operations.  I wouldn't hold my breath waiting for a solution from Intel. They eol'd the chipset in 2012.

Yeah, I built this system when everything was new, gave up any hopes of a bios update years ago.

I posted the info about this system because it's the only Asus system I've built in my memory, and because it contains an object lesson I find still useful today: Make sure it works for what you want to do BEFORE you buy it. Don't assume that it will be fixed later.

---

### Post by rbmorse on 2018-03-20
That's good advice.

---

