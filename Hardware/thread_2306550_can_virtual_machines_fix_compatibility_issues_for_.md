---
title: "can virtual machines fix compatibility issues for peripherals?"
date: 2015-12-16
forum: Hardware
---

### Post by jeff153 on 2015-12-16
Because of work I must use Windows programs & operating system.

One big problem with Windows is everytime I upgrade... currently Windows 10 which will autoupgrade from now on... I seem to have issues with scanners, printers & other peripherals. Sometimes they will issue new drivers, sometimes not.

I am wondering whether I could use a Virtual Machine, like Oracle's [Virtual Box]("https://www.virtualbox.org/") to host Ubuntu and switch back & forth between the two operating systems, such that if/when Windows 10, or whatever new flavor they install won't interface with a printer, scanner or other peripheral, Ubuntu will through the Virtual Box interface.

Secondarily, if it will work, I would be interested in recommendations/resources for purchasing computers/peripherals that play well with Linux. I currently have an all-in-one printer that should still work, but the last driver updates were for Windows Vista. I also have about 4 scanners that have become paperweights. Even if these can be salvaged, I'm thinking of upgrading the printer/scanner to a wireless model that will also work with my kids' iPads (needed for school) & a mobile scanner.

Thank you for any help, recommendations etc.

---

### Post by SeijiSensei on 2015-12-16
Your experience seems the exact opposite of most people who find peripherals like printers and scanners better supported in Windows than in Linux.  

Most HP and Brother printers work well with Linux though I would select devices with direct network connectivity like my [Brother HL-3170CDW]("http://www.brother-usa.com/Printer/ModelDetail/1/hl3170cdw/overview").  VirtualBox requires the "Extension Pack" to work with USB devices because of patent issues, and setting up USB devices can sometimes require extra effort.  My printer sits directly on the network where every device I own, and the virtual machines that run on some of them, can see it.

If you use a virtual machine, you may want to set up networking in "bridged" mode so the VM gets an IP address on the local network rather than hiding behind the host machine in "NAT" mode.  That can help with automatic detection routines like CUPS uses.

You can find lists of supported printers at [openprinting.org](openprinting.org).  For scanners, look here: [http://www.sane-project.org/sane-supported-devices.html](http://www.sane-project.org/sane-supported-devices.html)

Also you can always try drivers for common printer "languages" like PostScript or HP PCL even if you don't have a specific driver from the manufacturer.  Microsoft did make life difficult when it removed the Apple Color LaserWriter Postscript driver from its libraries; I don't know if there is a generic PS driver available for Windows any more.

---

### Post by jeff153 on 2015-12-16
Thanks much, SeijiSensei.

One underlying/followup question I have is whether or not there would have to be Windows drivers that would work with Virtual Box or similar virtual machines for the peripherals in order for Ubuntu to be able to access them.

In other words, if there happened to be Ubuntu drivers available that would handle the peripherals, but not for the Windows operating system, could Ubuntu still operate the peripherals despite the host OS not being able to do so?

This is more a question for going forward... If I buy a printer/scanner/whatever that Ubuntu can utilize, would that be protection for me going forward if Windows 12 or whatever Microsoft decides to upgrade my computer to? ... even if their new Windows version will no longer operate the peripheral, could I still operate them via Ubuntu running on the virtual machine? ... assuming, of course, that Ubuntu would run it now.

---

### Post by SeijiSensei on 2015-12-16
A virtual machine doesn't use the printer drivers of its host, so no, it doesn't matter if the device is still supported by Windows.  As I said, though, the most reliable solution is to use a printer with its own network adapter rather than one that requires a USB connection to the host computer.  In that arrangement the VM is talking directly to the printer over the network, and the host computer is providing only the network interface.

---

### Post by jeff153 on 2015-12-16
> **SeijiSensei said:**
> Your experience seems the exact opposite of most people who find peripherals like printers and scanners better supported in Windows than in Linux.  

Most HP and Brother printers work well with Linux though I would select devices with direct network connectivity like my [Brother HL-3170CDW]("http://www.brother-usa.com/Printer/ModelDetail/1/hl3170cdw/overview").  VirtualBox requires the "Extension Pack" to work with USB devices because of patent issues, and setting up USB devices can sometimes require extra effort.  My printer sits directly on the network where every device I own, and the virtual machines that run on some of them, can see it.

If you use a virtual machine, you may want to set up networking in "bridged" mode so the VM gets an IP address on the local network rather than hiding behind the host machine in "NAT" mode.  That can help with automatic detection routines like CUPS uses.

Thanks for that [Brother HL-3170CDW]("http://www.brother-usa.com/Printer/ModelDetail/1/hl3170cdw/overview") recommendation, btw. That looks like it might be a near perfect printer for me. I have a small business, but don't print a ton & inkjet ink might dry up on me. I was hoping to find a good, inexpensive, wireless, color laser (or LED), duplex printer that would do airprint for the iPads, would work with Win10 & was Linux compatible. That is a lot of specs, and that unit appears to fit the bill.

Having the ability to reload the toner cartridges is also a nice feature.

Thanks again.

> **SeijiSensei said:**
> A virtual machine doesn't use the printer drivers of its host, so no, it doesn't matter if the device is still supported by Windows.

Awesome.

>   As I said, though, the most reliable solution is to use a printer with its own network adapter rather than one that requires a USB connection to the host computer.  In that arrangement the VM is talking directly to the printer over the network, and the host computer is providing only the network interface.

I'm not quite sure what that means or how to check for it. Would all wireless &/or ethernet capable printers have that? If not does the [Brother HL-3170CDW]("http://www.brother-usa.com/Printer/ModelDetail/1/hl3170cdw/overview") have it? If not, is there a piece of hardware that could provide that for printers that don't come with it out of the box?

---

### Post by SeijiSensei on 2015-12-16
Sorry if I was unclear.  That Brother has both a wired Ethernet port and wifi.  As I recall you can't use both simultaneously, but you can still print from wifi-enabled devices.  I have mine connected with an Ethernet cable into my router.  I installed the [Brother Android app]("https://play.google.com/store/apps/details?id=com.brother.mfc.brprint&hl=en") on my phone, and it saw the printer right away.  There's an app for iThings as well.

Most printers in this class probably have both wired and wireless network connections built in.  There are also small [print server boxes]("http://www.newegg.com/Network-Print-Servers/SubCategory/ID-387") that you can use with parallel port or USB printers, but for a new printer, I'd just go with one that already has network connectivity.

I bought mine from Amazon where, at the time, it was specially discounted down to about $200.  [Currently]("http://www.amazon.com/Brother-HL-3170CDW-Digital-Wireless-Networking/dp/B00BQU141C") it is selling for about $220 with free shipping.

Brother makes all-in-one devices as well of course.  When a friend replaced his desktop computer to which his all-in-one was connected via USB, we first tried the same arrangement with his new machine.  For reasons that were never obvious, getting his laptop to see his desktop reliably with Windows on both ends proved difficult.  I connected the device to his network, and everything works fine.  I believe you can even run the scanner from a networked client.

---

### Post by jeff153 on 2015-12-16
> **SeijiSensei said:**
> Sorry if I was unclear.  That Brother has both a wired Ethernet port and wifi.  As I recall you can't use both simultaneously, but you can still print from wifi-enabled devices.  I have mine connected with an Ethernet cable into my router.  I installed the [Brother Android app]("https://play.google.com/store/apps/details?id=com.brother.mfc.brprint&hl=en") on my phone, and it saw the printer right away.  There's an app for iThings as well.

Most printers in this class probably have both wired and wireless network connections built in.  There are also small [print server boxes]("http://www.newegg.com/Network-Print-Servers/SubCategory/ID-387") that you can use with parallel port or USB printers, but for a new printer, I'd just go with one that already has network connectivity.

I bought mine from Amazon where, at the time, it was specially discounted down to about $200.  [Currently]("http://www.amazon.com/Brother-HL-3170CDW-Digital-Wireless-Networking/dp/B00BQU141C") it is selling for about $220 with free shipping.

Brother makes all-in-one devices as well of course.  When a friend replaced his desktop computer to which his all-in-one was connected via USB, we first tried the same arrangement with his new machine.  For reasons that were never obvious, getting his laptop to see his desktop reliably with Windows on both ends proved difficult.  I connected the device to his network, and everything works fine.  I believe you can even run the scanner from a networked client.

Thanks much for all your time and trouble, and for sharing your expertise & experiences. That is a big help. I sent the link to the Brother printer to my wife and she quickly pointed out that I'd be without a scanner. I did notice, however, that my old Canon multi-function printer was listed on the SANE project list of scanners that might work (mine was untested). Perhaps I can figure out how to download & install that & see if perhaps I can at least get that scanner working. If so, the stand alone printer would probable work well.

Thanks again, you time and help are much appreciated!

---

### Post by SeijiSensei on 2015-12-16
Here's are color all-in-one devices if you decide to go that route: [http://www.brother-usa.com/MFC/Color_Laser_Multifunction/](http://www.brother-usa.com/MFC/Color_Laser_Multifunction/)

---

### Post by 1clue on 2015-12-16
Not so much with printers, but if your host has good drivers for a device and can export a virtio-style driver to the guest, then the answer is yes to your original question.

I've seen network cards (especially wireless cards) and various PCI cards and CDROMs not play nicely with Windows as the hardware gets older, but when you put Linux on the metal and Windows in a VM with a standardized virtual device then suddenly things work fine.

If your Linux host can use your printer and your Windows box can't, of course you could network share your printer and print from windows using your linux box as a print server, but that can be done without virtualization.

For the record, a Canon MF8050Cn (networked color laser all-in-one) works fine on Ubuntu and Gentoo but doesn't work at all on Windows 10.

---

### Post by jeff153 on 2015-12-17
> **SeijiSensei said:**
> Here's are color all-in-one devices if you decide to go that route: [http://www.brother-usa.com/MFC/Color_Laser_Multifunction/](http://www.brother-usa.com/MFC/Color_Laser_Multifunction/)

Thanks for that info as well,[COLOR=#000000] SeijiSensei.

I will definitely check those out.
[/COLOR]

> **1clue said:**
> Not so much with printers, but if your host has good drivers for a device and can export a virtio-style driver to the guest, then the answer is yes to your original question. {can virtual machines fix compatibility issues for peripherals?}

Thanks for your reply. I am a little confused, however, (which my wife would say is not uncommon). I'm quite a novice at this but it sounds like I may have at least one false premise here.

1. It has been awhile, but I thought I read that Windows does not like being the guest on a virtual machine & almost insists upon being the host. Is that not true?

In my case Windows 10 doesn't have drivers for my Canon MF5750 & vice versa. - Edit. I just googled it again (I've been without a printer & scanner for a month or more) & Canon may have new updated drivers for it. [Canon Europe]("http://www.canon-europe.com/support/consumer_products/products/fax__multifunctionals/laser/laserbase_mf_series/laserbase_mf5750.aspx?type=drivers&driverdetailid=tcm:13-998026&os=WINDOWS%2010%20%2864-bit%29&language=EN") lists Windows 10 on the driver download section, but it's dated 6-2015 & the ones I downloaded from Canon back then were dated September 2015 & were only listed compatible with Vista & earlier. I'll try the new ones as maybe the UK version will work where the US one didn't, but I'm a little skeptical as the Read Me file on this other one also says it will only work with the operating systems listed and they only go up to Vista. I'll wait 'til tomorrow after I shut it down for the night.

2. From what SeijiSensei said, it sounds to me like the guest on a VM could potentially still operate the printer/scanner etc. even if the host can't do so.

> **SeijiSensei said:**
> A virtual machine doesn't use the printer  drivers of its host, so no, it doesn't matter if the device is still  supported by Windows.  As I said, though, the most reliable solution is  to use a printer with its own network adapter rather than one that  requires a USB connection to the host computer.  In that arrangement the  VM is talking directly to the printer over the network, and the host  computer is providing only the network interface.

I had never heard of a [virtio-style driver]("http://www.linux-kvm.org/page/WindowsGuestDrivers/Download_Drivers"), but googled it... but still don't quite understand it. Do those give Linux all of the built in Windows drivers?

>  I've seen network cards (especially wireless cards) and various PCI cards and CDROMs not play nicely with Windows as the hardware gets older, but when you put Linux on the metal and Windows in a VM with a standardized virtual device then suddenly things work fine.

How do you run Windows in a VM? Don't you need a CD/DVD with Windows on it to install it as a guest?

>  If your Linux host can use your printer and your Windows box can't, of course you could network share your printer and print from windows using your linux box as a print server, but that can be done without virtualization.

Does that require two separate computers... one running Linux and another running Windows?

>  For the record, a Canon MF8050Cn (networked color laser all-in-one) works fine on Ubuntu and Gentoo but doesn't work at all on Windows 10.

That's the type of situation where it seems to me that having Linux & Windows on a VM can help protect against big problems, especially now that once one gets on "The Windows Train", they will just update it to a new OS periodically and it might break the compatibility of peripherals when they do. Linux shouldn't have that problem as it won't force you to update and if it's already working with peripherals should be able to continue doing so, or so it seems to me.

Thanks again for your reply. It's certainly given me some additional food for thought, though it also gives me some indication of how much I still don't know.

---

### Post by SeijiSensei on 2015-12-17
> **jeff153 said:**
> How do you run Windows in a VM? Don't you need a CD/DVD with Windows on it to install it as a guest?
Yes, or an .iso image of the Windows install disk.  I have Win7 running in VirtualBox VMs on a couple of machines.  However, because of licensing issues, it's often easier to run Linux on a Windows host than the reverse.

---

### Post by 1clue on 2015-12-17
> **jeff153 said:**
> Thanks for your reply. I am a little confused, however, (which my wife would say is not uncommon). I'm quite a novice at this but it sounds like I may have at least one false premise here.

1. It has been awhile, but I thought I read that Windows does not like being the guest on a virtual machine & almost insists upon being the host. Is that not true?


False.  Microsoft runs well as a guest in any mainstream virtualization scheme, including but not limited to kvm/qemu, vmware, parallels.  I'm sure that it probably runs fine in VirtualBox too but I don't use that software.  Microsoft supplies their own virtualization software, and they will support their OS on pretty much any mainstream non-microsoft VM host software.  I've used the support telling them that it's running on vmware, kvm and parallels platforms as appropriate.  They don't blink an eye.

> 
In my case Windows 10 doesn't have drivers for my Canon MF5750 & vice versa. - Edit. I just googled it again (I've been without a printer & scanner for a month or more) & Canon may have new updated drivers for it. [Canon Europe]("http://www.canon-europe.com/support/consumer_products/products/fax__multifunctionals/laser/laserbase_mf_series/laserbase_mf5750.aspx?type=drivers&driverdetailid=tcm:13-998026&os=WINDOWS%2010%20%2864-bit%29&language=EN") lists Windows 10 on the driver download section, but it's dated 6-2015 & the ones I downloaded from Canon back then were dated September 2015 & were only listed compatible with Vista & earlier. I'll try the new ones as maybe the UK version will work where the US one didn't, but I'm a little skeptical as the Read Me file on this other one also says it will only work with the operating systems listed and they only go up to Vista. I'll wait 'til tomorrow after I shut it down for the night.


That printer uses the same driver as my printer, I'll go pretend to be a european and see if I can get the driver.  Thanks!

> 
2. From what SeijiSensei said, it sounds to me like the guest on a VM could potentially still operate the printer/scanner etc. even if the host can't do so.


If you pass the hardware through to the guest (requires vt-d support in your hardware) then your guest can control the hardware directly.  Or, for networked (printer has an ethernet or wifi cable and that's how you see it) then the host has nothing to do with it.

> 
I had never heard of a [virtio-style driver]("http://www.linux-kvm.org/page/WindowsGuestDrivers/Download_Drivers"), but googled it... but still don't quite understand it. Do those give Linux all of the built in Windows drivers?


virtio is a driver for a virtual machine guest.  Traditionally the VM software tries to emulate a real-world device, like an ethernet controller.  A virtio (or 9p or a few others) driver is one that can only run inside a guest VM, it is designed to work directly with the VM host for faster throughput.

> 
How do you run Windows in a VM? Don't you need a CD/DVD with Windows on it to install it as a guest?


You need an iso (cd/dvd image) and you need to buy a license for each copy of the VM you run.  You might want to call Microsoft to figure out which license best matches your scenario.  Their licensing model changes frequently, and some of them are more tolerant of typical VM use than others.  Generally speaking, if you have 2 running copies that you run independently of each other (simultaneously or at different times) then you need 2 licenses for the OS, plus 2 licenses for each piece of payware software on the guest.  For example, if you have Microsoft Office on both guests then you need to pay twice for that.  If you have Sql Server on one but not the other, then you need to buy 1 copy of that.

That said, a backup of the VM does not count as a separate licensed copy.  The premise there is that you've backed it up in case of corruption or destruction of the first copy, if you need to use that backup then you remove the 'live' copy and restore the backup over the top of that live copy.

One common misconception is that Microsoft hates VMs.  Speaking as somebody who works with fortune 500 companies, EVERY large business uses VMs.  Many of them use KVM or VMware or some other virtualization scheme not sold by Microsoft.  If Microsoft had a problem with that, then there would be a whole lot more 'alternate operating systems' out there.  Microsoft does what their customers want them to do.  If you don't know what license to get, call the company and get advice.  The fact that you're asking means you're trying to be legal, so ask whatever questions come up and they'll answer it.  The help line for license help can't sell licenses, but they can point you to authorized license distributors so you know you get a valid license.

> 

Does that require two separate computers... one running Linux and another running Windows?


Sharing the printer between computers is independent of whether there is one piece of physical hardware or two or fifty.

> 
That's the type of situation where it seems to me that having Linux & Windows on a VM can help protect against big problems, especially now that once one gets on "The Windows Train", they will just update it to a new OS periodically and it might break the compatibility of peripherals when they do. Linux shouldn't have that problem as it won't force you to update and if it's already working with peripherals should be able to continue doing so, or so it seems to me.

Thanks again for your reply. It's certainly given me some additional food for thought, ***though it also gives me some indication of how much I still don't know.***

This part in bold.  If you think you know all of one specific topic, that's when you haven't even begun to learn.  May you never run out of questions.

---

### Post by jeff153 on 2015-12-17
> **SeijiSensei said:**
> Yes, or an .iso image of the Windows install disk.  I have Win7 running in VirtualBox VMs on a couple of machines.  However, because of licensing issues, it's often easier to run Linux on a Windows host than the reverse.

Thanks. Those seem rare nowadays since computers don't come with install disks anymore.

My brother did give me a Windows 8 install disk, though. He bought it somewhere, installed it, didn't like it & reverted back to his previous OS. Not sure if I can use it now or not.

I guess there's no way to burn one just from the OS running on one's machine, eh?

Of course, it's probably easier not to fight 'em and just run Windows as the host.

---

### Post by SeijiSensei on 2015-12-17
> **jeff153 said:**
> My brother did give me a Windows 8 install disk, though. He bought it somewhere, installed it, didn't like it & reverted back to his previous OS. Not sure if I can use it now or not.
If he also has an unused authorization code, those 25-character strings Windows uses, then you can install from that disc.

> I guess there's no way to burn one just from the OS running on one's machine, eh?

It depends on whether there is a "recovery" partition on your disk.  You should have a utility in Windows that would let you burn a set of legitimate DVDs.  If you do, you can create a set of disks with that and use your existing authorization code.  The installer might balk and say you already have a machine using that code.  Microsoft creates a unique machine identifier and stores it along with the authorization code on its servers.  In some cases you can reassign the code on the fly; otherwise you might have to call a support number.

---

### Post by 1clue on 2015-12-17
> **jeff153 said:**
> Thanks. Those seem rare nowadays since computers don't come with install disks anymore.

My brother did give me a Windows 8 install disk, though. He bought it somewhere, installed it, didn't like it & reverted back to his previous OS. Not sure if I can use it now or not.

I guess there's no way to burn one just from the OS running on one's machine, eh?

Of course, it's probably easier not to fight 'em and just run Windows as the host.

The windows 8 install disk will work, but if he's already used the key then you need a new license for it.  You can get one online from a reputable authorized reseller.

IMO not easier at all to run Windows as the host.  In my opinion it's less stable and the operating system I want to run the least, so it should be in a VM.

Burning a cd/dvd from the rescue partition will only work to reinstall Windows on that specific machine.  The rescue partition contains a modified Windows installation which is keyed to the specific hardware in question.  At one point I worked in IT for a fairly large company.  We bought PCs in groups, 10 or 20 at a time, the same model. When they got older and started getting hard disk failures we tried to install a broken machine with the rescue disk for another machine of the same model, it didn't work.  We had to buy rescue images from the manufacturer (the disks were bad, couldn't use rescue partition on that machine) and they had to mail us the CD.  Probably different now, but at the time the installer image was only good for about 20 serial numbers in a sequence.  We would get one or two off of the image, then have to buy another CD for the next set.  It still wound up being cheaper dollars-wise to order the CD but it was much more expensive when you're paying an IT staff to go through all the steps.  What's more, that image will NOT work for a VM running on the same exact hardware.  The VM software will cause the machine to look different, and the built-in software checks will refuse to let it run.

Your best bet for a VM is to make sure your VM software can run the version you want [http://www.linux-kvm.org/page/Guest_Support_Status#Windows_Family](http://www.linux-kvm.org/page/Guest_Support_Status#Windows_Family) and then go to Microsoft to download the ISO for it.  The version of kvm listed for Windows 10 is newer than the latest kvm listed in Ubuntu 15.04, so it's uncertain if you could get it working without going to what Canonical considers to be unstable software.

Once you get it installed and running, you have something like 90 days to buy a license before it starts complaining.

---

### Post by jeff153 on 2015-12-18
> **1clue said:**
> False.  Microsoft runs well as a guest in any mainstream virtualization scheme, including but not limited to kvm/qemu, vmware, parallels.  I'm sure that it probably runs fine in VirtualBox too but I don't use that software.  Microsoft supplies their own virtualization software, and they will support their OS on pretty much any mainstream non-microsoft VM host software.  I've used the support telling them that it's running on vmware, kvm and parallels platforms as appropriate.  They don't blink an eye.

Interesting, thanks. I didn't know of those other options. It looks like kvm/gemu runs on Linux only, vmware is proprietary & parallels is proprietary & for Macs?

Linux sounds very interesting and I love the concept, but I'm a little leery jumping in whole hog being the novice I am. I've tinkered with it a little bit as a VM on VirtualBox but haven't ever formatted a disk and installed an OS from scratch, nor partitioned a drive. I'm afraid I might be in over my head & get into some trouble trying to do so with my operating computer. I do have some several old ones that I've retired that would probably be good to try my hand at it, but they might be too old & slow to learn how to do so. That's basically why I tried VirtualBox. No need to partition anything. I was kind of surprised that Linux could read my Windows files. I thought the disks were formatted differently for Windows & Linux.

> That printer uses the same driver as my printer, I'll go pretend to be a european and see if I can get the driver.  Thanks!

I hope you have better luck than I did. It didn't work for me. The website listed Windows 8.1 & Windows 10, but the Readme file said it only supported up to Vista. In any event it still doesn't work for me. I may just end up using it for a fax & copy machine, & maybe even as a scanner if I get Linux going again & the SANE option works with it.

>  If you pass the hardware through to the guest (requires vt-d support in your hardware) then your guest can control the hardware directly.  Or, for networked (printer has an ethernet or wifi cable and that's how you see it) then the host has nothing to do with it.

I'm not familiar with vt-d support, but this printer isn't a network ready one. If I get another one it will be, however.

>  virtio is a driver for a virtual machine guest.  Traditionally the VM software tries to emulate a real-world device, like an ethernet controller.  A virtio (or 9p or a few others) driver is one that can only run inside a guest VM, it is designed to work directly with the VM host for faster throughput.

That is something built into the VM software? Is it something that requires some training and understanding to use?

>  You need an iso (cd/dvd image) and you need to buy a license for each copy of the VM you run.  You might want to call Microsoft to figure out which license best matches your scenario.  Their licensing model changes frequently, and some of them are more tolerant of typical VM use than others.  Generally speaking, if you have 2 running copies that you run independently of each other (simultaneously or at different times) then you need 2 licenses for the OS, plus 2 licenses for each piece of payware software on the guest.  For example, if you have Microsoft Office on both guests then you need to pay twice for that.  If you have Sql Server on one but not the other, then you need to buy 1 copy of that.

So you would need two licenses even if they both ran on the same machine... such as a dual boot situation... say Microsoft 10 as a host or standalone, and also as a guest, both on the same machine?

> One common misconception is that Microsoft hates VMs.  Speaking as somebody who works with fortune 500 companies, EVERY large business uses VMs.  Many of them use KVM or VMware or some other virtualization scheme not sold by Microsoft.  If Microsoft had a problem with that, then there would be a whole lot more 'alternate operating systems' out there.  Microsoft does what their customers want them to do.  If you don't know what license to get, call the company and get advice.  The fact that you're asking means you're trying to be legal, so ask whatever questions come up and they'll answer it.  The help line for license help can't sell licenses, but they can point you to authorized license distributors so you know you get a valid license.

Yes, that was a misconception I had. I thought I had read that Microsoft really frowned on it & tried to design the software to keep it from operating as a guest.

> [QUOTE]That's the type of situation where it seems to me that having Linux  & Windows on a VM can help protect against big problems, especially  now that once one gets on "The Windows Train", they will just update it  to a new OS periodically and it might break the compatibility of  peripherals when they do. Linux shouldn't have that problem as it won't  force you to update and if it's already working with peripherals should  be able to continue doing so, or so it seems to me.

Thanks again for your reply. It's certainly given me some additional food for thought, ***though it also gives me some indication of how much I still don't know.***

This part in bold.  If you think you know all of one specific topic, that's when you haven't even begun to learn.  May you never run out of questions.[/QUOTE]

Thanks for that. Maybe I shouldn't be discouraged then if I never can seem to reach the end. Of course I guess that would be impossible since they keep moving "the end" further out all of the time. ;)

---

### Post by kurt18947 on 2015-12-18
I have a Windows 10 install running as a guest on an Ubuntu host. It seems to work fine for my limited Windows usage. I'm not certain how gaming would work, for example. My Windows guest appears to have a maximum of 128 MB. of ram available to its video adapter so I don't know how well a graphics intensive app would run. Perhaps adding RAM beyond 4 GB. would help there so I could allot more RAM to the VM, I don't know.

One of my printers is a Brother inkjet multifunction, the other is a Samsung monochrome laser multifunction. Both can print and scan from either Ubuntu or Windows and both support wireless printing from phones & tablets I believe. I'm using Virtualbox and did have a bit of an issue with printing initially. The virtual network adapter default in my Virtualbox install is NAT. I could ping the networked printers but they wouldn't print. Virtualbox provides 4 virtual network adapters so I set a second virtual network adapter to be bridged. Now I can print and scan via the network.

---

### Post by SeijiSensei on 2015-12-18
Most games with demanding graphics won't run on Windows in a VirtualBox session.  VB presents a virtualized video adapter to the guest machine that games won't recognize.  I have to run Windows natively to play something like Dragon Age: Inquisition or Final Fantasy XIV, to take two examples that I know won't work in a VirtualBox.  So I have one machine with a dual-boot arrangement, with Kubuntu in a VirtualBox on the Windows side, and Win7 in a VB on the Linux side.

---

### Post by kurt18947 on 2015-12-19
> **SeijiSensei said:**
> Most games with demanding graphics won't run on Windows in a VirtualBox session.  VB presents a virtualized video adapter to the guest machine that games won't recognize.  I have to run Windows natively to play something like Dragon Age: Inquisition or Final Fantasy XIV, to take two examples that I know won't work in a VirtualBox.  So I have one machine with a dual-boot arrangement, with Kubuntu in a VirtualBox on the Windows side, and Win7 in a VB on the Linux side.

That's a good point and no surprise. I think the max memory I can dedicate to video in Virtualbox is 128 MB. I'm sure there are other factors as well.

---

### Post by 1clue on 2015-12-19
Is high performance video a requirement? 

If you just need normal business function including Web video then most virtualization engines would work fine.

---

### Post by SeijiSensei on 2015-12-20
> **1clue said:**
> Is high performance video a requirement? 

If you just need normal business function including Web video then most virtualization engines would work fine.

It doesn't sound like an issue for the OP.  I was just responding to kurt's inquiry.

---

### Post by 1clue on 2015-12-20
@jeff153,

The thing I see you needing to be careful about here is that the version of your virtualization engine can support the operating system you want to have as a guest.  The current KVM for Ubuntu, for example, does not support Windows 10 AFAICT, but you could install a newer version of it and it may work fine.  Or you could try it with the stock Ubuntu version.

Speaking as a business professional who has used what I consider to be the three major non-Microsoft engines (VMware, Parallels and kvm/qemu) on several platforms, virtualization can do most of what any business professional needs to do.  KVM/QEMU does most of what a business professional needs to do, although sometimes with more effort than one of the commercially supported products, and often without the limits that the commercially supported products have.

You need to pay attention to what your requirements are and pay attention to the versions of software at all points.  And, in the case of commercial software, pay attention to licensing options.  The commercial software part goes both ways:  If you're writing commercial software you need to be aware of what each library's license is and the ways that it is legal for you to link commercial software to free software.

If you're just using a Windows environment then you need to be aware of the licensing particulars of each package, and possibly find one that suits your needs. Windows, for example, usually has at least a half dozen licenses for each version of Windows.  Anything from an educational license, standard end-user license, enterprise license, developers license, and so on. Usually the standard end-user license allows one install on exactly one piece of hardware, with maybe 2 or 3 installs allowed before it freaks out.  There is usually a VM-friendly license in there somewhere, that lets you move the image around to different hosts and fire up a restored backup more easily.

Good luck and have fun.

---

### Post by SeijiSensei on 2015-12-21
> **1clue said:**
> Speaking as a business professional who has used what I consider to be the three major non-Microsoft engines (VMware, Parallels and kvm/qemu) on several platforms, virtualization can do most of what any business professional needs to do.
Are they as easy to install and configure as VirtualBox?  VMware isn't free as far as I know, while VirtualBox is GPL-licensed.  For someone just starting out with virtualization, is there a strong argument not to use VirtualBox?  It works fine for what I need to do as a single user.  I also don't know why it isn't considered to be a "major non-Microsoft engine."  It's owned and supported by Oracle after all.  Not my favorite IT company, but they've done a good job maintaining VB.

---

### Post by 1clue on 2015-12-21
VMware ESXi is free to use and VMware offers some Open Source products, but I don't know that ESXi is one.

ESXi is a bare-metal hypervisor, meaning that there is no operating system under it.  You install it directly on the hardware, and there is nothing on the system except the hypervisor and guests.  I use this with work, I don't really recommend it since VMware has difficulties with some things I consider to be fairly important.  One thing is management of disk space with over-allocated data stores and reclaiming unused guest space.  This is not a shortcoming of hypervisors, it's a shortcoming of ESXi.

I use virt-manager for KVM/QEMU, which makes it about as hard to use as ESXi with vSphere.  There are some extra hoops to jump through at the beginning, like hardware you want to donate to a guest needs to be handled separately by the host.

My argument with virtualbox is that it doesn't start all the VMs when the host boots.  VB is an end-user engine, which may be exactly what you want.  It's not what I want, therefore I have no significant experience with it.  It may or may not be as capable as KVM in other respects, but I stopped reading when I got to the part about a user starting the vm every time you use it.

My interest in virtualization is in the IT shop use case.  I want my VMs to be always running, even if I'm not logged into the system.  In fact, most of the VM hosts I use (all with the exception of Parallels) don't have a keyboard or mouse or monitor attached to the system.

I may not have been clear enough in my previous post.

I am not trying to downplay the significance or capability of VirtualBox.  I'm only trying to say that since it's not what I want, I don't know much about it except what I read some years back before I found out that it's not what I want.

To figure out how VMs work, it's probably no less capable than anything else out there.  For certain professional and private use cases, it's probably just right.  Since you seem to not need the VM to be continuously available to other computers as a server on a network, you may want to investigate it more.

---

