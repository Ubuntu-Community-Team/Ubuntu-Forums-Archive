---
title: "Version 9.0.4 - how to install SMC EZ Connect USB Wireless?"
date: 2009-06-01
forum: Hardware
---

### Post by traynor on 2009-06-01
Hi -

I just installed Ubuntu 9.0.4 on a Dell Inspiron 1100 that has a bad onboard wireless card. So I've got an SMC EZ Connect USB card that Ubuntu is detecting, but I've no idea how to install it.

I've downloaded what I think are the right drivers but when I try to install them in the /home/ directory on Ubuntu it says I don't have the right privileges to do that (because root is disabled in Ubunutu 9, I think?)

Does anyone have any idea where to begin with this?

thanks,
-traynor

---

### Post by DavePlummer on 2009-06-01
I have an SMC "EZ Connect g" USB wirless adapter. Ubuntu 9.04, on laptops and desktops, has recognized it and activated the appropriate driver (zd1211rw) without any special action on my part, either with the adapter connected while booting, or when I plug it in after booting. Unless your laptop is somehow unique, I would expect it to work for you straight out of the box.

---

### Post by traynor on 2009-06-01
It is not working out of the box, either from a hard boot or if I just put the device in.

It's a Dell Inspiron.

Is there a set of steps I can take to make sure the device is installed correctly?

How do I see if that driver is present and active?

Would I need ndiswrapper for this?

---

### Post by DavePlummer on 2009-06-02
Sorry it's not working for you. It works for me on a Dell Latitude D620 and a Dell Inspiron 1545. To start troubleshooting, you could run lsusb in a terminal bofore and after inserting the adapter, to see if Ubuntu even sees a new USB device when it's inserted.

---

### Post by traynor on 2009-06-02
When I run lsusb from the terminal prompt it shows the device:
Bus 001 Device 002: ID 000a:XXXX Accton Technology Corp. SMCWUSB-G

So it's seeing the device, right? What next? I got this far yesterday...

According to a lot of forum posts I need to install the drivers for the device. I have them on a flash drive and put them on the machine, but Ubuntu won't let me write them to the home directory without root access. I'm stuck.

Any suggestions?

Thanks

---

### Post by DavePlummer on 2009-06-02
With the device plugged in, enter the command "lsmod". If you see "zd1211rw", the device has been recognized and the driver has been loaded. Using the  Network Manager applet, you should then be able to connect to available wireless networks. In my case I can connect using WPA2, with AES encryption.  If you don't see zd1211rw in the output, it is conceivable that you have a USB adapter with the same manufacturer and name as mine, but which uses a different chipset, and therefore needs a different driver, or you  may even need to use ndiswrapper with the adapter's Windows driver. I have seen some discussion of this situation surrounding SMC adapters but can't find it at the moment. I specifically bought my adapter because of the Zydas chipset, which is natively supported, and works like a charm for me. I will try to research the situation a little more, and will pass on anyhing that I find.

---

### Post by traynor on 2009-06-03
I ran lsmod and it does indeed see the zd1211rw device, but my networking app will not connect to my LAN via this device (it keeps trying to use the broken DELL onboard wi-fi card).

Where do I go from here?

Do I need to install drivers?

How do I install drivers in the "home" directory if I don't have root access privilges in Ubuntu 9.0.4?

Thanks for your help...

---

### Post by traynor on 2009-06-03
Is there anyone else out there with any idea what I should do here?

I can see the device, but apparently need drivers, but am having trouble installing them in Ubuntu 9.0.4

---

### Post by DavePlummer on 2009-06-03
Try to disable the built-in adapter in the BIOS. The Linux kernel seems to have identified your chipset and has loaded the driver that should work. If you can disable the built-in adapter, then you may be able to make some progress.

---

### Post by traynor on 2009-06-03
I think you're on to something there Dave. The system is putting the onboard wireless first.

Only problem is the BIOS on my Dell Inspiron 1100 is (very old) version A03 and the onboard wi-fi device is not visible in there anywhere and no way to disable it.

Is it possible to update the BIOS on the machine without an internet connection? All the forums I've seen with this suggestion are assuming the machine is connected to the internet.

I'm able to download the update from Dell Support and put it on a flash drive or CD, but what do I do with it once I get it onto Ubuntu? I don't even know how to copy files with the terminal prompt (yet) and when I drag and drop Ubuntu says I don't have permission to put files in the home directory (??)

Or any other suggestion on how I could disable the onboard wi-fi so Ubuntu will allow the USB Wireless to engage?

---

### Post by DavePlummer on 2009-06-04
I do BIOS updates by booting FreeDOS from a CD or USB flash drive, with the manufacturer's BIOS file and DOS utility on another USB flash drive. FreeDOS will assign a drive letter to each USB flash drive that's installed when booting. You can change to the appropriate drive and run the DOS-based BIOS update program. That said, I suspect that a BIOS update won't address your problem. I would not expect a BIOS update add the ability to disable the wireless adapter, althtough it is possible. The only other option would be to open the case and physically remove the adapter. That's easy on some laptops; harder on others. I'm not totally convinced, yet, that your USB adapter is properly identified. The ID numbers in your lsusb output are different from mine, and different from the values I've seen for that adapter on web sites that have Linux wireless info. I think that the only way to know for sure whether you can control the USB adapter is to disable the built-in adapter.

---

### Post by traynor on 2009-06-04
yeah, I just put the output code as XXXX rather than type it all out. I'm pretty sure Ubuntu is seeing the card properly. The exact ID it shows for it when I run lsusb is:

ID 083a:4505
(is this similar format to what yours shows?)


I hear what you're saying about the BIOS update probably not helping disable the internal wifi card.

I will see about taking it apart, finding the card and disconnecting it.

Stay tuned...

---

### Post by traynor on 2009-06-04
aaargh.

Heheheh, any idea where the wifi card is in a dell inspiron 1100? It's not under the keyboard as far as I can see, or under the memory hood or the other hood underneath the device.

Is it even possible to physically disable or remove the wifi card in a dell inspiron 1100?

Is there an alternate way to get Ubuntu to see and run the USB adapter?

---

### Post by DavePlummer on 2009-06-04
Your adapter does seem to match mine, and the kernel is loading the driver. I'm pretty confident that it will work if you can get the built-in adapter out of the way. Unfortunately, I have no idea where it's located on that machine. If it's integrated into the motherboard, you may be out of luck. You could check the Dell support site for manuals that might shed light on things. I know that they have good coverage for newer machines; I recently downloaded manuals for my wife's new Inspiron 1545.

---

### Post by traynor on 2009-06-05
so are you saying you think it may be impossible to add another wireless device to this machine?

If Ubuntu is seeing both devices, isn't there a way to make Ubuntu ignore the on-board device (like a "device manager" or something?)?

---

### Post by DavePlummer on 2009-06-05
Not necessarliy. My wife's laptop happily operates with two wireless adapters, one of which is the SMC adapter, each with it's own IP address. The broken built-in adapter in your machine may somehow be preventing Network Manager from using the USB adapter. There may also be some other problem that's preventing the machine from using the USB adapter. We just don;t know that, for sure. Disabling the bulit-in adapter, if you can, is a way to rule it out as the cause of the problem with the USB adapter.

---

### Post by traynor on 2009-06-07
I give up.

I've no way how to disable the bad internal wireless card on the Dell Inspiron 1100.

Thanks for your help! :)

---

### Post by sola on 2009-06-23
@Traynor

You probably have the second edition of the stick (just like me) which is not supported natively.

The second edition has the following model number (very small writing on the backside of the stick): SMCWUSBT-G2

This thread may be interesting for you:
[http://fostergrant.ubuntuforums.org/showthread.php?t=1017924](http://fostergrant.ubuntuforums.org/showthread.php?t=1017924)

It says that ndiswrapper should make it work but the guy had a problem with ndiswrapper not loading after restarting the machine (this is a different problem and can be solved)

Let us know if you have solved the problem and made the stick work properly.

---

