---
title: "Dell Pocket DJ with Ubuntu"
date: 2007-01-08
forum: Hardware &amp; Laptops
---

### Post by daxdog on 2007-01-08
I am still learning Ubuntu Linux and trying to get everything working.  I posted a request to the newbie's forum, but I have not gotten any responses.  Maybe this group can help.

I have a Dell Pocket DJ 5GB MP3 player.  When I plug it into my USB port, Linux recognizes it in device manager and with 'lsusb'.  
> 
george@george-laptop:~$ lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 041e:4132 Creative Technology, Ltd 
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  

Gnomad 2 and Neutrino both do not recognize the MP3 player.  What am I missing?  I would love to do away totally with XP, but if I can't get my MP3 player working I have to leave XP on the computer.

Almost forgot - I have a Toshiba A75-S226 running Edgy.  I don't know what other info you experts need.  I'm just a beginner.

---

### Post by daxdog on 2007-01-08
Here is the 'lsusb -v' results for the MP3 player:

> 
Bus 001 Device 002: ID 041e:4132 Creative Technology, Ltd 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x041e Creative Technology, Ltd
  idProduct          0x4132 
  bcdDevice            1.00
  iManufacturer           1 
  iProduct                2 
  iSerial                 3 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           39
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration         16 
    bmAttributes         0xc0
      Self Powered
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass         0 (Defined at Interface level)
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface             33 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval               4
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Maybe this will help...

---

### Post by daxdog on 2007-01-17
I guess this is not a solvable problem right now.  How do I get Ubuntu programmers to look into setting up this piece of hardware in Linux?  I would like for it to work in the future.

---

### Post by verbalshadow on 2007-02-06
you probably need to install one of two libs 

libnjb

or 

libmtp

Depending on which transfer protocal the device uses.
there are some app out there the will make syncing easier but i don't recall there names off hand.

---

### Post by daxdog on 2007-02-12
> **verbalshadow said:**
> you probably need to install one of two libs 

libnjb

or 

libmtp

Depending on which transfer protocal the device uses.
there are some app out there the will make syncing easier but i don't recall there names off hand.

I installed libnjb and nothing changed.  I was not able to find libmtp in the Synaptec Package Manager.

---

### Post by daxdog on 2007-02-13
I downloaded and installed libmtp.  The mp3 player is still not recognized.

---

### Post by lamalex on 2007-02-13
I recommend using amarok and compiling it from source. Give it everything you can that way regardless what you have now or in the future it will work, and I can assure you it will work with your Dell DJ. It works with my friends Dell DJ, and my brothers Zen.

---

### Post by daxdog on 2007-02-14
> **Iamalex said:**
> I recommend using amarok and compiling it from source. Give it everything you can that way regardless what you have now or in the future it will work, and I can assure you it will work with your Dell DJ. It works with my friends Dell DJ, and my brothers Zen.

I am still pretty ignorant when it comes to Linux.  I downloaded amarok-1.4.5.tar.bz2 and extracted it to its own folder.  I opened up a terminal window and typed "./configure".  I got the following message:

> checking how to run the C++ preprocessor... /lib/cpp
configure: error: C++ preprocessor "/lib/cpp" fails sanity check

I went into the Synaptic Package Manager and reinstalled anything to do with cpp.  No dice.  What should I try next?

---

### Post by drsaamah on 2007-03-09
If this problem could be solved that would be great!  I've only been using Linux for about four weeks now, and I also have Dell DJ (the 30 gig though--not the pocket).  I already use Amarok and I love it so if it could work with that, that would be awesome.

---

### Post by nicholas.Platt on 2007-03-14
[http://amarok.kde.org/Install_Guide#BuildingFromSource](http://amarok.kde.org/Install_Guide#BuildingFromSource)

I found this guide to building Amarok from source. It has instructions for Ubuntu users.
I'm still in the process of "make," but everything seems to be working as the guide lays out. I've got a Dell Pocket DJ 5gig also, so I'll let you know if this works with it.

I've got the latest firmware on my Dell, so make sure you do the same.
Go to Home | Settings & Info | Information | Version: 2.20.07. Assuming it works, of course.

**Edit:** Nope. Seems that all we can do is view the list "lsusb" provides.
hmm, just noticed: With the Dell DJ turned on, and headphones in, link it to the computer. In the terminal, type "lsusb -v". Does your DJ freeze with the headphones making a buzzing sound? I wonder if this means that Linux is trying to reach the DJ, but can't.

---

### Post by daxdog on 2007-05-12
Problem solved.  After fighting with this problem for months, I finally solved the problem yesterday.  Want to know how I did it?  I bought a SanDisk Sansa MP3 player!  It took about 15 minutes in Windows to install, but it was instantly accessable under Linux.

---

