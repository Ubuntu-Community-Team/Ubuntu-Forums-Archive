---
title: "Printer model that works out of the box (no driver hunt needed)?"
date: 2013-02-10
forum: Hardware
---

### Post by glln0v on 2013-02-10
Can anybody recommend some Printer models that work off a default install of Ubuntu? Just plug in the printer and the drivers are already present in the default ubuntu install. Is this a reality at all?

Is there any models that have Scanning capabilities without having to install proprietary drivers from vendor's website?

What models have given you zero issues and just work trouble free? I prefer B&W Laser Printer. I'm interested in hearing about people who have actually used the printer and didn't have to install any drivers for 12.04 or later, not just a list of printers that "should" work.

---

### Post by sammiev on 2013-02-10
Epson Artisan 730 and I run it wireless as well.

---

### Post by ahallubuntu on 2013-02-11
~

---

### Post by glln0v on 2013-02-11
Thanx guys. 

Looks like these are Inkjet. I can't find Laser Printer on the Epson site. I guess they don't make laser printers? I was hoping to be able to get a Laser Printer.

---

### Post by kurt18947 on 2013-02-11
I think a majority of HP printers work with minimal if any additional software.  You might have to add HPLIP and HPLIP-GUI with an HP - or not.  I've not installed an HP laser so can't say.  And HP certainly has laser printers :) .  One thing I'd consider if looking for easy of installation.  If possible, select a model that's has been for sale for a number of months.  Decent linux support development may not be able to start until a model is released, unlike Windows.

---

### Post by Mark Phelps on 2013-02-13
Just so you know... my experience has been that while Ubuntu can often find a printer and install drivers, all too often, they are "basic" drivers, that is, they will just do printing.

To get the feature set available when using the same printers in Windows, I've had to install drivers specific to the printer.

However, I've also found that CUPS drivers work very well and often have an extensive feature set.

---

### Post by SeijiSensei on 2013-02-13
Database of supported printers from The Linux Foundation: [http://www.openprinting.org/printers](http://www.openprinting.org/printers)

---

### Post by offgridguy on 2013-02-13
Interesting thread, as installing printer drivers can be a hassle.  On a related note, I found
this in a fedora advertisement.

[COLOR=black][SIZE=3][SIZE=3]**Desktop:** Have you ever tried to use a new printer and been frustrated by error messages and having to hunt for the correct driver to  install? With the new easy printing feature in Fedora 14, plug your printer in and Fedora automatically finds and installs  the correct driver. This feature allows you to print in many different locations and churn out copies within minutes. It's  one of several innovations in Fedora 14 that let you take better advantage of your system's hardware. 

[SIZE=3][SIZE=3][SIZE=2][SIZE=2]I have ordered an install CD of fedora to see if it actu[SIZE=2]al[SIZE=2]ly lives up to the claim.:D[/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE]
[/SIZE][/SIZE][/COLOR]

---

### Post by agillator on 2013-02-13
Many printers work 'out of the box' with ubuntu but as noted above these seem to be using generic drivers for basic functions. A lot of each printer's capability is left unused without specific drivers. If this is what you want. I suspect most printers will work (see the list mentioned previously). Personally I use HP printers. I have found them to be hardy, reliable, and well supported through HPLIP. These days HPLIP is easy to install. Just download from HP, purge the version ubuntu installs, and run the downloaded version. It will install any dependencies necessary. Just follow the directions. It really is an easy process and sets up the drivers written by HP for your printer on Linux. All it takes these days is a little time.

---

### Post by glln0v on 2013-03-04
Guys, I will be satisfied with just basic printing functions, like being able to print off documents from Writer, etc.

Does the Linux Kernel have printing drivers built into it like it has other drivers built in? If so what printing drivers does it have built in? I am looking for a printer that I can literally buy off the shelf and plug into my computer and it just works; I won't need to manually install anything or tell ubuntu to search the web to find a driver to install or anything like that--the driver is already present in the kernel or in ubuntu, etc. Is this a realistic goal?

Sounds like I can do this if I go buy an Epson inkjet printer? Do I understand correclty?

Models that just work:
Epson Artisan 730
Epson Workforse
any others?

---

### Post by gordintoronto on 2013-03-04
I have a Brother HL-2170W, and it "just works."

I try a new version or distro of Linux about once a month, and printing is one of the first things I try. Printers/ Add/ Network, and away we go.

The printer is attached to my router by an Ethernet cable.

---

### Post by glln0v on 2013-03-05
> **gordintoronto said:**
> I have a Brother HL-2170W, and it "just works."

I try a new version or distro of Linux about once a month, and printing is one of the first things I try. Printers/ Add/ Network, and away we go.

The printer is attached to my router by an Ethernet cable.

Great. You didn't have to manually install any drivers right? You just plugged in the printer and Ubuntu already had what it needed to work the printer, right?

---

### Post by foresthill on 2013-03-05
If you can find a used HP 1320 Laserjet somewhere, these things are workhorses and work instantly on all versions of Ubuntu:

[img]http://mclean.schoolfusion.us/modules/groups/homepagefiles/cms/958755/Image/hp1320n.jpg[/img]

No networking capability, except through the parallel port. They do have a USB port though.

---

### Post by cetoka on 2013-03-05
I have an old Xerox Phaser 3121 black and white laser printer and I have a Samsung color laser printer CLP 315 both are working fine on my Ubuntu 12.04 LTS desktop.

---

### Post by Mark Phelps on 2013-03-05
> **glln0v said:**
> Sounds like I can do this if I go buy an Epson inkjet printer? Do I understand correclty?

Models that just work:
Epson Artisan 730
Epson Workforse
any others?

I too have an Artisan 730, use it in both 12.04 and 12.10, and while I did install the drivers using CUPS, they work quite well.

---

### Post by gordintoronto on 2013-03-05
> **glln0v said:**
> Great. You didn't have to manually install any drivers right? You just plugged in the printer and Ubuntu already had what it needed to work the printer, right?

With my Brother HL-2170W, I don't have to search for drivers, just point at the printer and say, "use that one."

---

