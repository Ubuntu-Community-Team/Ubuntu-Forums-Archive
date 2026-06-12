---
title: "USB Dialup Modem Redux"
date: 2007-11-19
forum: Hardware &amp; Laptops
---

### Post by jwalling on 2007-11-19
I need dialup because I travel to remote areas that don't have DSL or wireless internet access.   Does anyone have a good experience using USB modems with Ubuntu?  I am interested in manufacturer model numbers and installation steps.

I read the previous posts on USB dialup modems and didn't find any ready solutions.  I did read that most USB modems are winmodems.  How can you tell if a USB modem is a winmodem?  For example, if a USB modem will work on  Macintosh does that rule out winmodem? (see [http://www.usb-ware.com/zoom-56k-usb.htm](http://www.usb-ware.com/zoom-56k-usb.htm) )

I did find this Linux **howto** but I am not sure it is current: [http://www.linux-usb.org/USB-guide/x332.html](http://www.linux-usb.org/USB-guide/x332.html)

I would like to buy my laptop from ZaReason or System76, but I need to know what works well before I make my purchase decision. My reasons for wanting a USB modem are a) internal modems are winmodems and b) RS-232 serial ports and PC-Cards are being phased out of laptops.  I would consider an Express Card modem however USB ports are much more common on laptops.

Thanks for your help.
---
*Postscript*:  I am reading this [**dialup thread**]("http://ubuntuforums.org/showthread.php?t=480717") - I may get some answers there but would like any feedback on USB Dialup modems working with Linux.
---
*Postscript2*: The [Zoom Dial-Up External USB Modem]("http://www.zoom.com/products/dial_up_external_usb.html") Model 3095F is advertised to work with Linux.  It looks promising and it is miniaturized!
---
*Postscript3*: Getting educated. There are 3 types of modems based on Hardware Controller, Controllerless/Winmodem, or Soft modem. [[see this tutorial]("http://www.usr.com/solutions/modem101.asp")].  To determine modem type and get chipset specs go [here]("http://xmodem.org/modems/usblist.html") and [here]("http://xmodem.org/chipsets/dips/roster.html"). Controlerless and Softmodem will require drivers. See these:
[http://linmodems.org/](http://linmodems.org/)
[http://www.linux.org/docs/ldp/howto/Modem-HOWTO.html](http://www.linux.org/docs/ldp/howto/Modem-HOWTO.html)

---

### Post by Bartender on 2007-11-20
I had high hopes for the 3095 but someone at another forum was unable to get it working.  He said that Zoom techies admitted to him that the drivers need more work.  That was a coupla months ago but I'd sure want to hear solid success stories before recommending it.
These two USB modems have reportedly worked in Linux.  I picked the names up from the forums.

Best Data 56USBSL
Zoom 2985

I can't guarantee they'll work but that's what the people said.  Worth checking out at least...

I don't know if you've read my "Dial-up" diary - er - thread, but the Sabrent adapter cable works as an intermediary between a serial modem and a PC with USB ports...

EDIT:  I followed your Zoom link.  $104!!  Sheesh

I visited their website 
[http://www.zoom.com/products/dial_up_external_usb.html](http://www.zoom.com/products/dial_up_external_usb.html)

It doesn't look like they offer the $100 model any more? 
The 3090AF is definitely a winmodem.
The 2985 comes with a Conexant chipset or an Agere chipset.  Both winmodem chipsets.  They "might" work with Linux drivers.

---

### Post by jwalling on 2007-11-20
No success finding a linux compatible USB 56K modem!

Bummer.

I am now considering an external 56K modem with on-board controller connected via USB adapter.

 TRENDnet TFM-560X 56Kbps RS-232 (Serial Port) External V.90 High Speed Voice/Fax Modem
  [http://www.newegg.com/Product/Product.aspx?Item=N82E16825134002](http://www.newegg.com/Product/Product.aspx?Item=N82E16825134002)

  TRENDnet TU-S9 USB to Serial Converter
  [http://www.newegg.com/Product/Product.aspx?Item=N82E16812107956](http://www.newegg.com/Product/Product.aspx?Item=N82E16812107956)

If anyone has experience installing the above combination or similar hardware, please post your experience and describe how you configured the Linux USB/PPP dialup.  

Thanks.
John Walling
Seattle, WA

---

### Post by Bartender on 2007-11-21
This Sabrent cable
[http://www.newegg.com/Product/Product.aspx?Item=N82E16812156008&Tpk=SBT-USC1M](http://www.newegg.com/Product/Product.aspx?Item=N82E16812156008&Tpk=SBT-USC1M)
works fine with Ubuntu

The modem will be detected at /dev/ttyACMO

---

### Post by jwalling on 2007-11-24
On order from Tiger Direct:

TRENDnet 56k (V.92) High Speed Voice/Fax Modem TFM-560X 
[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?Sku=T156-2080](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?Sku=T156-2080)
[http://www.trendnet.com/en/products/TFM-560X.htm](http://www.trendnet.com/en/products/TFM-560X.htm)


Sabrent 6-Foot USB to Serial Adapter Cable SBT-USC6K
[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?Sku=M501-1210](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?Sku=M501-1210)
[http://www.sabrent.com/products/specs/SBT-USC6K.htm](http://www.sabrent.com/products/specs/SBT-USC6K.htm)

I selected the older version of the Sabrent cable (6K vs. 6M)  because some reviewers complained about changes to the cable chipset.  

I will post my progress here, in 1-2 weeks.

-------------------------
Update Dec 20, 2007
I used pppconfig/pon/poff to setup and use the external modem.  I have been using the external modem without any problems for the past few weeks. I have not used the FAX feature.



----------------------
John
Saturday, November 24, 2007

---

### Post by aad on 2008-06-01
I know that this is an old thread but FWIW I was trying to get a USRobotics 5686E external modem to work via USB port using the Sabrent 6-Foot USB to Serial (9-pin) DB-9 RS-232 Adapter Cable.  This was for my sister`s newer HP which does not have the 9 pin serial port.  My sister has no choice but to use dialup as high speed is not an option where she resides  No problems what so ever using Gnome PPP to auto detect the connection.  Detected as USB0 and connected without a hiccup.  And no special driver was required to make it work.  The funny thing is that the same connection did not work with Windows XP even with the Cable driver installed.  Windows XP just would not recognize the modem.  Usually, it is the other way around, things that are usually plug and play in WinXp require some tinkering in Ubuntu.  This time the tables were turned in favor of Ubuntu.

---

### Post by zoomzoomzoom on 2008-06-07
I got the zoom 3095 working in Ubuntu 7.10.  Its bit of a pain but once set up works great and it is tiny.  [http://ubuntuforums.org/showthread.php?t=711646](http://ubuntuforums.org/showthread.php?t=711646)

If you just need usb cause your computer doesnt have serial port, keep your serial modem and get a cheapy serial to usb converter cable.  I suggest specifically looking for one with pl2303 chip, it will work pretty much universally in linux as module has been in kernel for some time.  However 2.6.24 and newer linux kernel such as Ubuntu 8.04 should have the "winchiphead" ch341.ko module included.  You dont need an expensive cable, one of the cheapies off ebay will work.  As I said when you do your ebay search perhaps best to search description for pl2303.  I learned all this the hard way, first bought a cheapie winchiphead cable which was going to take a kernel patch on older kernel I was using then.  When I got newer kernel linux I tried the winchiphead cable and it worked ok.  On ebay with bit searching, the winchiphead cables go for shipped price around US$5, the pl2303 cables can be had for one or two dollars more.

By way I also found windows wouldnt work with the winchiphead cable using the included driver.  It got too painful looking for other drivers on chinese language websites and I dont connect windows to internet very often anyway since its such a pain to keep it clean, updated, etc.

---

