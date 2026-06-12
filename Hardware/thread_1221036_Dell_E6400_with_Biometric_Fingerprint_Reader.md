---
title: "Dell E6400 with Biometric Fingerprint Reader"
date: 2009-07-23
forum: Hardware
---

### Post by Cortux on 2009-07-23
Hello All

I have Ubuntu 9.04 on a Dell E6400. I cant for the life of me figure how to get it to work. The only proof I have that it even exists is I physically see it and I have confirmed with the specs by service Tag on the Dell Website.

I even have the same issue with Vista (dual boot) but it doesnt bother me cause I hardly use it.

Please advise.

---

### Post by Cortux on 2009-07-23
Anyone, some direction ??

---

### Post by chronos00 on 2009-07-24
try the following command and paste here it's output:
```
 lsusb 
```

If you have the appropriate reader, you can follow this guide:

[http://www.guia-ubuntu.org/index.php?title=Fingerprint_Reader](http://www.guia-ubuntu.org/index.php?title=Fingerprint_Reader)

---

### Post by Cortux on 2009-07-26
This is the output you requested, I dont seem to be able to understand the language from the link.
 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0c45:63f8 Microdia 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 0a5c:5801 Broadcom Corp. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 413c:8158 Dell Computer Corp. 
Bus 003 Device 003: ID 413c:8157 Dell Computer Corp. 
Bus 003 Device 002: ID 0a5c:4500 Broadcom Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by Cortux on 2009-07-26
BTW, I did manage to get it to work in Vista but that makes no difference to me.

---

### Post by chronos00 on 2009-07-27
As you can see from the output of the command you ran, there is no mention of the fingerprint scanner. I have the same problem with a Sony VAIO, where Linux doesn't seem to find the scanner either.

You can try:```
sudo lshw | grep -i finger
``` or ```
sudo lspci | grep -i finger
```
to see if Ubuntu detects your reader

Finally you can also try to install fprint:```
sudo apt-get install fprint-demo
``` and run it:```
sudo fprint-demo
```

With some luck, it will detect your reader

---

### Post by Cortux on 2009-07-27
Luck doesnt seem to be on my side this time. Would you be able to assist in telling me which translator I can install to read the page at the link you posted, the one I currently have does not work.

Thanks

---

### Post by chronos00 on 2009-07-27
You can just use Google's translator:
[http://www.google.com/language_tools?hl=en](http://www.google.com/language_tools?hl=en)

Be aware that the guide I mentioned needs linux to detect your fingerprint reader (which doesn't seem to be the case).

---

### Post by fonfi on 2009-07-29
> **Cortux said:**
> 
Bus 005 Device 002: ID 0a5c:5801 Broadcom Corp. 


Te device mentioned above is the fingerprint reader. All E-series Latitudes, and Precisions based on this series, are equipped with this new biometric reader. Unfortunately it is not yet supported by any of the fingerprint projects (neither ThinkFinger, nor fprint), however fprint team is aware of existence of this chip, and they claim to work on it. We just have to wait... :)

Below is output of 'lsusb -v' for this device: 

```
Bus 005 Device 002: ID 0a5c:5801 Broadcom Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0a5c Broadcom Corp.
  idProduct          0x5801 
  bcdDevice            1.01
  iManufacturer           1 Broadcom Corp
  iProduct                2 5880
  iSerial                 3 0123456789ABCD
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          139
    bNumInterfaces          2
    bConfigurationValue     0
    iConfiguration          0 
    bmAttributes         0xc0
      Self Powered
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass       254 Application Specific Interface
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              4 Broadcom USH w/swipe sensor
      ** UNRECOGNIZED:  10 25 00 00 00 00 00 00 00 00 00 00 00 00 00 00
```

---

### Post by chronos00 on 2009-07-29
"USH w/swipe sensor"??

I would have never figured that out...

Tnaks a lot fonfi!
I'll use lsusb -v next time I don't find the hardware I'm looking for

---

### Post by Cortux on 2009-07-30
Thanks for that info, I can wait now knowing someone is working with it.
 
Is there any ETA on the fix.

---

### Post by fonfi on 2009-07-31
> **Cortux said:**
> 
Is there any ETA on the fix.

None that I'm aware of. 
I've been looking through the mailing list of the fprint project, and the last messages concerning this reader was sent in May or so. However, all new Latitudes are equipped with this hardware, and as the Latitude model is quite popular (especially in business world), I hope we won't have to wait much longer...

---

### Post by Cortux on 2009-07-31
Yes me too, It would be great to get the fingerprint reader working, with one or two other issues sorted out, I could then proceed to get rid of vista all together.
 
Thanks, Kindly keep me informed if you recieve any update regarding the fix.

---

### Post by pizza-is-good on 2009-08-04
Has the keyboard lighting started working?
It works fine for me. I didn't have to do anything to get it to work.

---

### Post by Cortux on 2009-08-05
Nope, I dont think it even has a light up keyboard. I was mistaken at first, but it doesnt even work in Vista which came preloaded.

---

### Post by fonfi on 2009-08-17
The backlight keyboard has nothing to do with OS. It is controlled by BIOS. Check for the backlight configuration there. If it is there, and it is activated, and still does not work, you probably have regular keyboard. I have seen, somewhere in the net, a comparison photo of these two keyboards, but I can't find it right now. If I find it, I'll post link here.

---

### Post by Cortux on 2009-08-18
Ok, thanks

I am seriously doubting it has the keyboard, as it does not have a key to activate it as i was told it should have.

---

### Post by fonfi on 2009-08-22
I can't find the mentioned comparison photo, but I have uploaded photo of my keyboard, with the switch on/off key. 

[http://codevision.pl/photos/keyboard.jpg]("http://codevision.pl/photos/keyboard.jpg")

If you don't have it, your keyboard is probably regular one. However you can easily replace it, buy one from Dell, on ebay or anywhere, and just replace it (requires to remove 2-3 screws). It's easy - really... And it does not violate any warranties. :)

---

### Post by Cortux on 2009-08-24
Oh crap, I dont have one. Im gonna look around to get it.

---

### Post by hibernatus on 2010-02-24
Hi all,

did you succeed to have your reader working?

If yes i would be very interested by the solution

Thanks

---

### Post by chronos00 on 2010-02-25
> **hibernatus said:**
> Hi all,
did you succeed to have your reader working?
If yes i would be very interested by the solution
Thanks

Do you have the same reader as Cortux?

In any case, the easiest way es just trying both biometric fingerprint projects available in Ubuntu's repos.

They are: FPrint and ThinkFinger

To install them just run:
```
 sudo aptitude install fprint-demo thinkfinger-tools 
```

Then, to try each one of them:
FPrint: ```
fprint-demo
```
ThinkFinger: ```
tf-tool
```

The first one has a GUI and seems to be a much more ambitious project, thou it is less functional. The latter is just a command line which will ask you to enrole your fingerprints.

If any of this worked out for you, you are on your way.
Just let me know and I'll guide you to configure your login security to use fingerprints.

Regards

---

### Post by hibernatus on 2010-02-25
Hi,

Yes i have the same version :

```

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 047d:101f Kensington PocketMouse Pro
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 005: ID 413c:8156 Dell Computer Corp. 
Bus 003 Device 003: ID 413c:8157 Dell Computer Corp. 
Bus 003 Device 004: ID 413c:8158 Dell Computer Corp. 
Bus 003 Device 002: ID 0a5c:4500 Broadcom Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 0a5c:5801 Broadcom Corp. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```


I have issue your recommandation, but infortunatly, when i start fprint demo => no devices found

---

### Post by chronos00 on 2010-02-25
I can't help you any further then.
Perhaps you could searchi FPrint's project web page ([http://reactivated.net/fprint/wiki/Main_Page]("http://reactivated.net/fprint/wiki/Main_Page")) and look if your device is supported.
You could also try downloading the latest version from their website and compiling / installing / whatever to see if your device is recently supported.

---

### Post by cajda on 2011-04-09
Hi,
I'm interest if there is any progress about this fingerprint reader. I have Dell E6410, which use also Broadcom 5880 (I don't have fingerprint reader, but I want to upgrade).
Probably it doesn't work with *fprint* and *ThinkFinger*.
Does anyone try another project like *Fingerprint GUI*?
Thank you!

---

