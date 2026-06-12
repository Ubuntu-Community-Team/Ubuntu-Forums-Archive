---
title: "HP Pavilion dv9275la: Failed to allocate mem resource"
date: 2007-06-30
forum: Hardware &amp; Laptops
---

### Post by Felipe_U on 2007-06-30
Hello,
       I bought a month ago a HP Pavilion dv9275la Notebook PC. I immediately installed Feisty Fawn and it works all right, although after GRUB it throws the following message:

[Some Numbers]* PCI: Failed to allocate mem resource [Some Numbers]*

* I didnt wrote the numbers in the [ ],  the message is just visible for a second or two before Ubuntu starts.

The other issue i have is that Ubuntu takes at least twice as much to start than Windows Vista Home Premium. Maybe the problem is related.

The specs for my machine are:
T5600 Processor, Intel Core 2 Duo
160 GB HardDisc Enhanced IDE 5400 RPM SATA (Dual HDD-80GB x 2)
2048 MB of RAM 667 MHz DDR2
Intel PRO/Wireless 3945 a/b/g + Bluetooth (Bluetooth not working)
DVD+-RW with Lightscribe
GeForce Go 7600
Integrated Webcam (Not working in Fesity)
Integrated Mic (Haven't tried it yet so I don't know if it works)
PCMCIA TV ATSC/NTSC HP Expresscard (Doesn't work)
One small Remote Control (Most of the buttons work)
One Media Buddy Remote Control (Doesn't work I have to plug in a USB IR receiber but  Feisty doesn't recognize it)

Here is the Output of lspci:
```

felipe@Earthdawn:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller AHCI (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce Go 7600] (rev a1)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
05:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
07:05.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)

```Could someone help me with the mem allocation issue or fixing any of the hardware that doesn't work? If i haven't provided enough info, let me know where I can find info and I'll post it here. BTW English is not my home language :)

Regards,
Felipe

---

### Post by Puppy Fan on 2007-07-04
On my HP Pavilion dv8339, Intel Core Duo 2250, 1024mgRAM, 100GB HDDx2.  I receive a :

Memory allocation error @ blahblahblah00000 # 6 blahblahblah...HP sucks!

HP has had ACPI issues that have led to mobo fans not coming on in their laptops running linux distributions, but I don't know if that has anything to do with the memory allocation resource errors.  I am actually glad to see you have the problem too, and that I didn't just have bad RAM or something else.  I really don't know what it means though.

Now I am trying to get GRUB to come back...Vista has eclipsed her.

:(

---

### Post by Felipe_U on 2007-07-04
Luckly Ubuntu works allright, the only issue I have is that it takes like 2 minutes to start. I'll be moving this post to the DV9000 Laptops thread :)

Regards,
Felipe

---

### Post by ajesh on 2007-07-05
Hi Felipe, 

I have a dv9334us with almost the same specs as yours and I also get the allocate mem resource error at boot up, but my Ubuntu Fiesty does not take two minutes to load, it takes less than a minute. 

However, it does seem slow compared to how much time my old desktop takes to load. 

Regards,
-Ajesh

---

### Post by Puppy Fan on 2007-07-06
OK...I don't know about you guys but I would like to get to the bottom of this.  Fueling my frustration with HP as a typical corporate monster that rarely takes responsibility for product defects and design flaws that they assume most customers won't notice, or be bothered by, is what I have discovered through researching running Linux OS's on Pavilion Notebooks 

BIOS Issues...HP does not provide adequate BIOS support for customers. 

There is sufficient documentation of problems that have caused the cooling fans to stop running leading to heat related failure and costly destruction.

What kills me is that those who have reported their findings as knowledgable HP laptop customers with technical expertise, have done more to isolate and provide solutions to some issues that they have passed along to HP.  

There are forums of messageboards at HP that are dedicated to product lines where some of these issues are discussed.

I am sure that there are plenty of discussions that touch on driver issues here, but I doubt there is much on BIOS issues that relate to running Fiesty Faun.  

So I am still looking for answers, ad still have difficlty running UBUNTU 7.04 and Vista on my dv8339us on sperate HDDs or the same. I am plagued by what looks like BIOS and Hardware compatibility issues.

Does anyone know where there is more in depth discussion of these issues.  Also, has anyone here had recovery partition issues or issues with recreating a recovery partition?  I have a hunch HP's software engineering team ended up stumped by a host of problems with Media Center notebooks...my machine even came with what looked like a Vongo rootkit.  

Whit

---

### Post by ajesh on 2007-07-14
I figured out why my boot up time takes a lot of time. 

It was spending a lot of time in "configuring network interfaces...." while booting up. After searching on the forums, it was recommended to comment out all lines in /etc/network/interfaces except the 
```
auto lo
iface lo inet loopback
```

lines. After I did this, the laptop boots very quickly and the wireless connection still works....

Thanks,
-Ajesh

---

### Post by Felipe_U on 2007-08-09
> **ajesh said:**
> I figured out why my boot up time takes a lot of time. 

It was spending a lot of time in "configuring network interfaces...." while booting up. After searching on the forums, it was recommended to comment out all lines in /etc/network/interfaces except the 
```
auto lo
iface lo inet loopback
```lines. After I did this, the laptop boots very quickly and the wireless connection still works....

Thanks,
-Ajesh

I'll try this out today. Did you report this to the [**Howto: Ubuntu on HP dv9000 series laptop (Covers dv9000 and dv9500 series)??**]("http://ubuntuforums.org/showthread.php?t=512059")

[quote=Puppy Fan]Does anyone know where there is more in depth discussion of these issues. Also, has anyone here had recovery partition issues or issues with recreating a recovery partition? I have a hunch HP's software engineering team ended up stumped by a host of problems with Media Center notebooks...my machine even came with what looked like a Vongo rootkit. 

Whit[/quote]

Try these links:[ **Howto: Ubuntu on HP dv9000 series laptop (Covers dv9000 and dv9500 series)**]("http://ubuntuforums.org/showthread.php?t=512059")

and

[**Official Hp Dv9000 Laptop Thread!!**]("http://ubuntuforums.org/showthread.php?t=431815")

My laptop works allright most of the time, I only have overheating issues when Im playing in windows and not very often(It has happened that it suddently powers off in rare ocassions, I don't know why it overheats so much, all the vents are clear)

On linux not one crash so far. Beryl looks good and I really havent tried most of the multimedia stuff that the laptop comes with.

Does anyone know where are the startup logs? I want to check them in case theres a more usefull mesage there related to the **[B]Failed to allocate mem resource message**[/B]

Regards,
Felipe

---

### Post by Felipe_U on 2007-08-10
> **ajesh said:**
> I figured out why my boot up time takes a lot of time. 

It was spending a lot of time in "configuring network interfaces...." while booting up. After searching on the forums, it was recommended to comment out all lines in /etc/network/interfaces except the 
```
auto lo
iface lo inet loopback
```lines. After I did this, the laptop boots very quickly and the wireless connection still works....

Thanks,
-Ajesh

Great now my Ubuntu Starts up under 21 seconds :). Thanks a lot man.

Regards,
Felipe

---

### Post by kiasanth on 2007-08-13
I get this message too during startup
[   ##.######] PCI: Failed to allocate mem resource #6:20000@f8000000 for 0000:01:00.0

the Error message above refers to a hardware item on your PCI bus that is trying to be allocated memory...
in my message 20000@f8000000 for 0000:01:00.0 refers to 128 Megs of ram (20000 is HEX for 128Meg) f8000000 is the location for the ram allocation and 0000:01:00.0 refers to my Video Cards location on the PCI bus. My particular video card has 128 Megs of ram on it hence the 20000(128 Meg Hex) being allocated.

So now you know what the numbers mean, does this help? doubt it, but it may be a graphics card problem as when I bought my HP system they tended to all come with nVidia cards. who knows?

Since my video card has no faults in the actual OS and even performs as well as I'd expect in 3D acceleration, I don't think there is actually a problem occuring in start-up that doesn't get remedied automatically before the HAL kicks in.

---

### Post by MikeDK on 2007-09-04
I believe its a Kernel issue the "Failed to allocate mem recources" dosnt show up in the AMD64 version of ubuntu, I have been told.

I have a Hp pavilion dv9232eu

1.6ghz cpu amd64 TL-52
and i have the same problem Kind regards MikeDK

---

### Post by Inxsible on 2007-09-04
I have HP dv9000t with Intel Core 2 duo and I see that "Failed to allocate......" error too.

I have been seeing it ever since I installed Ubuntu, so it has nothing to do with resource intensive apps like Compiz or Beryl etc.

But it sure would be nice to get to the bottom of this.

I shall try commenting out the other devices to get my laptop start under 21 seconds too :D

BTW...has anyone got their internal webcam working? mine is a microdia.

I installed the deb provided in the HP dv9000 series thread, but I cant get Kopete or aMSN to send video :(

---

### Post by MikeDK on 2007-09-04
you can try seaching google for microdia+pavilion+linux
you can also try do a lspci in terminal to see if it is the microdia and not Ricoh
 
if it is Ricoh try this site [http://www.arakhne.org/spip.php?rubrique31]("http://www.arakhne.org/spip.php?rubrique31")

---

### Post by Felipe_U on 2007-09-06
> **kiasanth said:**
> I get this message too during startup
[   ##.######] PCI: Failed to allocate mem resource #6:20000@f8000000 for 0000:01:00.0

the Error message above refers to a hardware item on your PCI bus that is trying to be allocated memory...
in my message 20000@f8000000 for 0000:01:00.0 refers to 128 Megs of ram (20000 is HEX for 128Meg) f8000000 is the location for the ram allocation and 0000:01:00.0 refers to my Video Cards location on the PCI bus. My particular video card has 128 Megs of ram on it hence the 20000(128 Meg Hex) being allocated.

So now you know what the numbers mean, does this help? doubt it, but it may be a graphics card problem as when I bought my HP system they tended to all come with nVidia cards. who knows?

Since my video card has no faults in the actual OS and even performs as well as I'd expect in 3D acceleration, I don't think there is actually a problem occuring in start-up that doesn't get remedied automatically before the HAL kicks in.

Thanks for the explanation.

Regards,
Felipe

---

### Post by MikeDK on 2008-01-22
just wanna add, that the Kernel issue is on the Bios Bug that also show in some DV series dont know how many veryies it affects

Kind Regards MikeDK

---

### Post by Felipe_U on 2008-04-04
> **Inxsible said:**
> 

BTW...has anyone got their internal webcam working? mine is a microdia.

I installed the deb provided in the HP dv9000 series thread, but I cant get Kopete or aMSN to send video :(

On Fesity I had to download the driver for my webcam. On gusty it worked right out of the box. I tried to use it with kopete but no luck so far. I don't remember the model of the webcam right now. The webcam works right in skype and Ekiga.

Regards,
Felipe

---

