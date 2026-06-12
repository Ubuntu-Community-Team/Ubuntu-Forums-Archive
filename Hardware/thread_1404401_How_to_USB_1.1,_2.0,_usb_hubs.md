---
title: "How to: USB 1.1, 2.0, usb hubs"
date: 2010-02-11
forum: Hardware
---

### Post by Claus7 on 2010-02-11
Hello all,

here I will try to write some notes about usb technology and especially about usb 1.1 and usb 2.0 and how someone will be able to identify in an ubuntu box the types of those ports. Also, I will try to give some insight on the ubuntu hubs.

In the advent of new technologies things that were on the forefront follow the road to oblivion. For usb technology we are in the advent of version 3.0 which follows the 2.0 and 1.1.

I won't go so much back. My initial step would be the ports 1.0 which will be found on computers that are much older than 7 years or so maybe even double than that. Next the 1.1 technology appeared and finally the 2.0 . I won't deal with 1.0 . The difference of 1.1 and 1.0 is better performance so 1.0 was abandoned and does not need our attention. 

Now the difference between 2.0 and 1.1 is mainly to the speed transfer. In many computers you will find both of them and it is a real trick on how to find out which port belongs to which type. 

First of we have to know physically how many usb ports exist on our pc. For this to happen we have two choices. *Either* open widely our eyes and check our pc about them *or* find the vendor of our motherboard, google a little and find the specs of the usb ports. The latter in combination to the former will give us the full picture.

Let us assume now that we have 8 usb ports. Now how do we know what type is each one of them?

**lsusb** command will not always give the correct amount of usb ports available not even the right type of them. The commands that help in these circumstances are the **lshw** and the **lsusb -v** both run as root.

If you are lucky lsusb will show you all the usb ports you have as well as the type of each one of them. For example there were problems with ubuntu identifying all the usb ports a pc had. Apart from that you might have to do some configurations in the BIOS. So as you can understand this is not a trivial issue.

In general if you type lsusb what you will get is something like:
> Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

Here you can see that you have 4 usb ports which are unoccupied as the numbers after the ID are zero. Now, if you connect a device in one of those ports then the table might become like this:
> Bus 005 Device 043: ID 0d49:3200 Maxtor 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 

In this table you can see all the information on the previous one plus one more line (in general every time you plug a device a new line will appear on the initial table, here I get five usb ports, yet the system is supposed to have in total 8, in the back of my pc I have four that they work, so I cannot really tell the difference between the numbers 4,5 and 8, yet I hope that you can get the notion). That line has a maxtor hdd on and you can recognize both the name of the hdd as its id. Things to take a look:
on the first line you can see which bus is occupied. Yet on the device number you wee the number 43! What is going on? This is supposed to be an index number, which is incremented every time you plug a device on the specific usb port. Here it means that from the time I opened my pc I have connected a usb device on that port 43 times! 

And the question remains. Is this a 1.1 port or a 2.0 port? 

In order to find out you have to tupe sudo lsusb -v . In order to check, under the specs of the device you will see either:
> bcdUSB               1.10
or
> bcdUSB               2.00

For example for maxtor above I get:
> Bus 005 Device 043: ID 0d49:3200 Maxtor 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0d49 Maxtor
  idProduct          0x3200 
  bcdDevice            0.01

which means that this port is behaving as a 2.0 one. The bcdDevice I have seen that is not reliable to check the type of the port.

And we are done??? Nope! This seems to me pretty easy. Don't you think? Yes it is! If you look among other information you will come across these lines:
> Port 1: 0000.0503 highspeed power enable connect

In other words: in order for a port to behave as a 2.0 one, if possible, you should connect a device which i)supports the 2.0 technology ii) as well as being (mostly) self powered. In most computers that they are covering both 2.0 and 1.1 technology the most you will get is 2.0 speeds with only one device attached and transferring of data between the computer and the usb device of 480Mbits/s or 60MB/s. If you are using a 2.0 port then you are expecting speeds higher than 1.5MB/s. In order to reach the maximum of a usb 2.0 port then your hdd should support such a speed. In general 7200 rpm hdd reach the 15-16MB/s whereas the 5400 the 11MB/s. A formula in order to calculate such things is the [[1]]("http://www.pcguide.com/ref/hdd/perf/int_Rate.htm"):
> Data Transfer Rate = [(Spindle Speed / 60) * Sectors-Per-Track * 512 * 8 )] / 1,000,000  , units in MBits/s

So, if you have two hdd the transfer rate between the two depends on the speed of the slower of the two.

And how many are the 2.0 ports? Is there a possibility that you might connect a hdd to a 1.0 or 1.1 port? In order to verify this, you have to check the sudo lsusb -v output and see whether the port has converted to a 2.0 one or if it remains 1.1.

Hubs: What about hubs?
Hubs afaik are small apparatuses which enable us to enhance the 2.0 ports of our computer. What I have done is to connect to one of my usb ports an extension usb cable and there a usb hub with 4 usb 2.0 slots. There I connected two self powered hdd and found out that the drop of speed instead of plugging the devices straight to the computer was negligible. 

Recapitulation:
[LIST]
[*]In order to check a usb 2.0 port you have to connect there a device which supports that protocol. Then you have to check with the lsusb -v  command whether this port is indeed a 2.0 one or not. 

[*]If you transfer data  between two hdd the maximum rate you will get (both connected to 2.0 ports) will be the lower speed of the two. If it is higher than 1.5 MB/s you are on 2.0.

[*]Sometimes you might get lower speeds. This is because of the OS you use, so you have to check this out as well.

[*]The hubs do not seem to deteriorate performance at least connecting two devices in a 4 slot hub. It is preferable to connect them one at a time and not at once.
[/LIST]
These are all I can think of, concerning the usb technology. Hope this clears a little bit the issue.

Regards!

---

