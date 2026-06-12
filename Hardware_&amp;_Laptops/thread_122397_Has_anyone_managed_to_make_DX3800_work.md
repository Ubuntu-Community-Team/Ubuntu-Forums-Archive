---
title: "Has anyone managed to make DX3800 work?"
date: 2006-01-27
forum: Hardware &amp; Laptops
---

### Post by foxy123 on 2006-01-27
I received Epson DX3800 today but after two hours I cannot make it work under Ubuntu. I tested it in Windows and it works fine there. 

CUPS does not have a driver for this printer but there is a proprietary driver on Avasys: [http://www.avasys.jp/english/linux_e/dl_spc.html](http://www.avasys.jp/english/linux_e/dl_spc.html)

The driver I am trying to make work is pips-scx3700-2.6.3. I managed to compile it after several problems but I cannot print anything. I wonder if anyone here made it work?

---

### Post by foxy123 on 2006-02-01
well, I have installed new gutenprint drivers, which support DX3800 and I can print. Also the printer worked with C64 driver.

---

### Post by rob2nd9th on 2006-02-08
Could you run a step by step on this As I have tryed to reinstall my drivers but still drawing a blank on geting my DX3800 to work?
Thanks

---

### Post by foxy123 on 2006-02-08
[QUOTE=rob2nd9th]Could you run a step by step on this As I have tryed to reinstall my drivers but still drawing a blank on geting my DX3800 to work?
Thanks[/QUOTE]
OK, uninstall gimp-print using Synaptic or 'apt-get remove'.

Download gutenprint source from [here]("http://sourceforge.net/projects/gimp-print/") Choose Gutenprint 5.0.0-rc2 release

Untar the source, cd into the source directory and run
```
./configure
make
sudo checkinstall -D
```

you may do 'sudo make install' instead of 'checkinstall'

Then go to Preferences/Printing (I am not sure I do not use Gnome) and install a new printer choosing DX3800 driver (standard).

If you have any problems please post it here and some will be happy to help you out.

---

### Post by rob2nd9th on 2006-02-08
Have tried the above 2 time - but when I goto install new printer DX3800 is not on my list?? what am I doing wrong?:confused:

---

### Post by foxy123 on 2006-02-09
[QUOTE=rob2nd9th]Have tried the above 2 time - but when I goto install new printer DX3800 is not on my list?? what am I doing wrong?:confused:[/QUOTE]
it's strange because I've got it in the list of drivers.

---

### Post by rob2nd9th on 2006-02-09
Have got DX3800 standard installed now but cant get it to print a test page. Not shore what port / USB setings to use?:-?

---

### Post by Stonekeeper on 2006-02-17
Install printconf using synaptic.
Then type "sudo printconf"
This should setup the printer correctly :D

---

### Post by fubarbundy on 2006-02-27
It might be worth trying my installation method from [http://ubuntuforums.org/showthread.php?t=119595&highlight=gutenprint](http://ubuntuforums.org/showthread.php?t=119595&highlight=gutenprint)

This should give you a gutenprint that fits Ubuntu better, and it worked for me with a DX4200, which is basically the same printer, just with faster printing.

p.s. PLEASE DON'T USE THE PROPRIETARY DRIVER! The open one will work with a little perseverance, I promise! :D

---

### Post by f2d on 2006-03-05
I tried the installation of gutenprint suggested above, everything went smooth. Now I have the entry 
Stylus-DX3800---CUPS+Gutenprint-v5.0.0-rc2 
in my printer list. But it stops there.
When I try to print a test page, it does nothing for a while, and then it goes on doing nothing with the printer status going to "printer stopped".
Clicking on the printer properties, I have in the General tab a message:
Paused: Unable to open USB device "usb://EPSON/Stylus%20DX3800": No such device
Aha. Didn't even know there were such URLs.

Before that I managed to get the DX3800 scanner working in sane, using this Gentoo page [http://gentoo-wiki.com/HARDWARE_EPSON_CX3650_%26_DX3850](http://gentoo-wiki.com/HARDWARE_EPSON_CX3650_%26_DX3850)
so 1/ the usb connection does work, but 2/ this page had me change all sorts of permissions and hotplug files, which might explain that gutenprint is now "unable to open". I don't know.

Thanks in advance anyway.

  Florek

---

### Post by fubarbundy on 2006-03-07
Gah! Stupid forum just wiped out my long reply :-/

I might be able to shed some light on your problem (notice I say 'might' ;-))

I had what I *think* was a similar problem with my DX4200, and it turned out that sane was interfering with the printer part of my multifunction because it thought it was the scanner. The slight problem is I fixed this problem via a long and torturous route a while ago, so I'm not too fresh on my exact steps, but here's what I think is necessary.

A bit of background (from what I gather) - all USB devices have various identifying codes so that your system knows what to do with them. These include vendor ID, device ID,  device type and so forth. The problem is that these Epson multifunctions are seemingly actually three different USB devices as far as your computer is concerned - a 2 port USB hub, and a scanner and printer 'plugged into' this hub. So far, so good - that actually seems like a nice standard, easy way to deal with a multifunction device. The problem is that they all have the same product ID (0820 for my DX4200) and sane identifies scanners by default using only the vendor and product ID. So when you plug in your multifunction, sane grabs the whole lot. Or changes its permissions. Or something. Anyway, breaks it.

So what you have to do is change some of sane's rules for finding your scanner.

There are two files you need to edit:

/etc/udev/rules.d/45-libsane.rules (the number may be different)
/etc/hotplug/usb/libsane.usermap

In 45-libsane.rules, add the following (somewhere near the other Epson entries) and save (back up the original just in case):

```
# Epson Corp.|Stylus CX4200
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="0820", SYSFS{bInterfaceClass}=="0xff",MODE="664", GROUP="scanner"
```

**NOTE: you must change the product ID to the one for your multifunction model. To find out what this is, you can use the Device Manager under System/Administration. You should find your printer listed as USB2.0 MFP. Click on the advanced tab, and look for usb.product_id. Mine is listed as 0x820, which (bizarrely) should be entered in the above file as 0820.**

Technical explanation: bInterfaceClass is one identifying code for the scanner (unique to the scanner when combined with the vendor and product id). 0xff corresponds to 'Vendor Specific Interface' (the printer is 0x07)

The second file , libsane.usermap, needs to have the following lines added, again, somewhere near the other Epson device listings, and again, please back up first!:

```

# Epson Corp.|Stylus DX4200
libusbscanner             0x0080      0x04b8   0x0820    0x0000       0x0000       0x00         0x00            0x00            0xff            0x00               0x00               0x00000000
```

**Again, you need to change 0x0820 as appropriate. Again, notice the irritating difference in the format of this number!**

Technical info: The first number, 0x0080, is an instruction to identify the scanner by its interface subclass as well as its vendor ID and product ID. The 0xff corresponds to the scanner's 'Vendor Specific Interface'.

Now, you probably need to restart hotplug, udev, replug your multifunction, restart your computer and probably dance a voodoo ritual in order to get the changes all recognised.

Good luck. You'll need it :mrgreen: But you CAN get it working on Ubuntu, I promise!

p.s. please also see my post at [http://ubuntuforums.org/showthread.php?t=94064](http://ubuntuforums.org/showthread.php?t=94064) , although my advice here is better (re libsane.usermap)

---

### Post by f2d on 2006-03-14
Hooray! 

Using the info of the previous post, and the addendum below, the printer now works perfectly. 

Addendum: The product id for the DX3800 is 0x818, and there is already an Epson entry with this number in 45-libsane.rules (DX385). 
I had to comment it out, otherwise it wouln't work (unless it was some other mistake).

So look for the lines

# Epson Corp.|Stylus DX385
SYSFS{idVendor}=="04b8",SYSFS{idProduct}=="0818",MODE="664",GROUP="scanner"

and place a # in the beginning so that it looks like

# Epson Corp.|Stylus DX385
#SYSFS{idVendor}=="04b8",SYSFS{idProduct}=="0818",MODE="664",GROUP="scanner"

Thanks a lot.

Oh, and Sane still works, too. Incredible.

Cheers, 

     Florek

---

### Post by trapanator on 2006-06-07
[QUOTE=fubarbundy]/etc/hotplug/usb/libsane.usermap[/QUOTE]

this file doesn't exist in Ubuntu Dapper. How can I apply the 2nd part of your post?

---

