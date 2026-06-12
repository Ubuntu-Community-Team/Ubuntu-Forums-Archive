---
title: "Trying to install Wacom CTH470 tablet"
date: 2011-10-23
forum: Hardware
---

### Post by Tamalin on 2011-10-23
I am trying to install a wacom bamboo tablet (model CTH470) on Ubuntu 10.10.  I installed the wacom-dkms package from the ppa:doctormo/wacom-plus repository, but the tablet doesn't seem to be working properly.  Running lsusb produces the following line:```
Bus 004 Device 008: ID 056a:00de Wacom Co., Ltd 

```
Running xsetwacom list produces no output.  The device also doesn't show up in xinput list.

What can I do about this?:

---

### Post by Favux on 2011-10-23
Hi Tamalin,

I'm afraid nothing if you also want touch to work along with the stylus.  Your model is brand new and the code needed to make touch work requires at least the 2.6.38 kernel, because that is when the mt.h (multi-touch header) was added.  So Maverick's 2.6.35 kernel won't work.  Instructions for your model are in appendix 3 of the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").

The three new models haven't been submitted to the kernel yet which is why DoctorMO's PPA doesn't have your model.

If you're OK with just the stylus and no touch we could try patching input-wacom.

---

### Post by Alexomnom on 2011-10-23
Good evening!

@Fauvx: Does that mean, that I also can't use my CTL-470/K right now on 11.10?
I'm searching 'bout a week for a solving for my problem, not beeing able to use my new gen Wacom-tablet...
I crashed a couple of times my linux-kernel, because of my poor tries to get it running, but nothing worked =/
(P.S.: Sorry for my poor English, I'm not a native speaker :) )

---

### Post by Favux on 2011-10-23
Hi Alexomnom,

Welcome to Ubuntu forums!

Yes, that is correct.  Because it is new the 3.0 kernel in Oneiric does not have your model in the wacom.ko (the usb kernel driver).  So you have to compile a wacom.ko that has your model.

You could follow appendix 3 linked in the BambooPT HOW TO above.  Or because you have the new Bamboo Pen you probably just need your model entered in wacom_wac.c so when the kernel module is compiled it is in the compiled wacom.ko.  However since input-wacom doesn't yet compile on 3.0 (although there is a work around) it is probably easier to follow appendix 3.  You'll just bring along touch stuff that is unnecessary to you, but no harm.

---

### Post by Alexomnom on 2011-10-23
wow....
finally...

Maybe that sounds a little bit melodramatic, but a few tears are running down my face.
Finally it works!
After 7 days and some sleepless nights, finally! As an Ubuntu-Newbie.
Thank you so much :))))

Now I can go to bed, without thinking about my new-not-working-bamboo.

Have a nice day, and may god safe you :D

---

### Post by Favux on 2011-10-23
Great!  Nice job Alexomnom!  :D

---

### Post by Tamalin on 2011-10-29
Wow, this is very nice, complete information I have been unable to find coherently anywhere is else.  Thank You.

---

### Post by ThierryMu on 2011-11-30
Hi,
I have a new Bamboo PT tablet CTH-470/K, I tried to install it under Ubuntu 11.10 Oneiric following this thread [http://ubuntuforums.org/showthread.php?t=1515562](http://ubuntuforums.org/showthread.php?t=1515562) and the appendix 3 (with the bamboo3).
But it isn't detected. It is plugged in usb (no wireless).
My kernel is "3.0.0-14-generic-pae".
There's the result of "lsusb":
```
Bus 006 Device 005: ID 056a:00de Wacom Co., Ltd 
```And in my syslog when I plugg the tablet, I see this  :
```
Nov 30 22:27:22 thierry-M70Vn kernel: [ 2749.356024] usb 6-2: new full speed USB device number 5 using uhci_hcd
Nov 30 22:27:22 thierry-M70Vn mtp-probe: checking bus 6, device 5: "/sys/devices/pci0000:00/0000:00:1d.0/usb6/6-2"
Nov 30 22:27:23 thierry-M70Vn mtp-probe: bus: 6, device: 5 was not an MTP device
```Have you got an idea ?
Thanks for your help, regards

Thierry

---

### Post by Favux on 2011-11-30
Hi ThierryMu,

Welcome to Ubuntu forums!

Sorry to hear it isn't working yet.  Hopefully there isn't a problem with Chris' update to input-wacom.  The compile went OK, and you didn't notice any errors?

Let's check if the newly compiled wacom.ko is auto-loading:
```
lsmod | grep wacom
```

---

### Post by ThierryMu on 2011-12-01
Hi Favux,
Thank for your welcome.
There's the result of "lsmod | grep wacom":
```
wacom                  42319  0 
```But I had to edit the "/etc/modules" file and I had to add at the end "wacom" (without the quotes) like it was noticed in this post : [http://ubuntuforums.org/showpost.php?p=9532802&postcount=24](http://ubuntuforums.org/showpost.php?p=9532802&postcount=24)

I didn't notice errors when I compile.
Thanks for your help.

---

### Post by Favux on 2011-12-01
Good, that was what I was leading up to.

But I gather it still isn't working?

You're the second person to try Chris' new input-wacom and not get it working.  So use the old instructions in appendix 3 and download the patch from linuxwacom-discuss thread.  We'll have to let Chris know something is wrong with his input-wacom patch.

---

### Post by Favux on 2011-12-01
Oh, shoot.  The problem is I forgot the -b switch so you're cloning the master not bamboo3.  The line should read:
```
git clone git://github.com/cbagwell/input-wacom.git -b bamboo3
```

---

### Post by ThierryMu on 2011-12-01
Hi Favux,
It's working now on Oneiric 11.10 with the pen but also with the fingers ! I followed the news intructions of the appendix 3 (with the 2.6.38 version) : nothing else to do !
If you're agree, I will explain your solution on the french Ubuntu forum (in mentionning your principal thread BambooPT)
Thanks a lot for your help, regards,

Thierry

---

### Post by ThierryMu on 2011-12-01
Here's how I proceeded :
```
cd desktop
git clone git://github.com/cbagwell/input-wacom.git -b bamboo3
cd input-wacom
./autogen.sh --prefix=/usr
sudo cp ./2.6.38/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
sudo depmod -a
```
Then I rebooted.

---

### Post by Favux on 2011-12-01
Great ThierryMu!

Thank you for showing/clarifying the instructions you used.  Of course you can post them on the French Ubuntu forum.

---

### Post by ThierryMu on 2011-12-01
> **Favux said:**
> 
Thank you for showing/clarifying the instructions you used.

You're welcome : it's me who am indebted to you :).

Here's the explanations in french : [http://forum.ubuntu-fr.org/viewtopic.php?pid=7289521#p7289521](http://forum.ubuntu-fr.org/viewtopic.php?pid=7289521#p7289521)

Regards.

---

### Post by ThierryMu on 2011-12-06
Hi,
Now that the tablet CTH-470/K works when it's plugged through usb, I try to use the Wacom Bamboo Wireless Kit ACK-40401. I didn't succeed.
The kit is recognized by Ubuntu 11.10 and there's the result of the command "sudo lsusb -v"
```
Bus 006 Device 002: ID 056a:0084 Wacom Co., Ltd 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x056a Wacom Co., Ltd
  idProduct          0x0084 
  bcdDevice            1.11
  iManufacturer           1 Wacom Co.,Ltd.
  iProduct                2 Wacom Wireless Receiver
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           84
    bNumInterfaces          3
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower               98mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      0 No Subclass
      bInterfaceProtocol      0 None
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.00
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      54
          Report Descriptor: (length is 54)
            Item(Global): Usage Page, data= [ 0x01 0xff ] 65281
                            (null)
            Item(Local ): Usage, data= [ 0x80 ] 128
                            (null)
            Item(Main  ): Collection, data= [ 0x02 ] 2
                            Logical
            Item(Global): Logical Minimum, data= [ 0x00 ] 0
            Item(Global): Logical Maximum, data= [ 0xff 0x00 ] 255
            Item(Global): Report ID, data= [ 0x80 ] 128
            Item(Global): Report Size, data= [ 0x08 ] 8
            Item(Global): Report Count, data= [ 0x1f ] 31
            Item(Main  ): Input, data= [ 0x01 ] 1
                            Constant Array Absolute No_Wrap Linear
                            Preferred_State No_Null_Position Non_Volatile Bitfield
            Item(Local ): Usage, data= [ 0x01 ] 1
                            (null)
            Item(Global): Report ID, data= [ 0x02 ] 2
            Item(Global): Report Count, data= [ 0x03 ] 3
            Item(Main  ): Feature, data= [ 0x02 ] 2
                            Data Variable Absolute No_Wrap Linear
                            Preferred_State No_Null_Position Non_Volatile Bitfield
            Item(Local ): Usage, data= [ 0x01 ] 1
                            (null)
            Item(Global): Report ID, data= [ 0x03 ] 3
            Item(Global): Report Count, data= [ 0x0c ] 12
            Item(Main  ): Feature, data= [ 0x02 ] 2
                            Data Variable Absolute No_Wrap Linear
                            Preferred_State No_Null_Position Non_Volatile Bitfield
            Item(Local ): Usage, data= [ 0x01 ] 1
                            (null)
            Item(Global): Report ID, data= [ 0x04 ] 4
            Item(Global): Report Count, data= [ 0x02 0x01 ] 258
            Item(Main  ): Feature, data= [ 0x02 ] 2
                            Data Variable Absolute No_Wrap Linear
                            Preferred_State No_Null_Position Non_Volatile Bitfield
            Item(Local ): Usage, data= [ 0x01 ] 1
                            (null)
            Item(Global): Report ID, data= [ 0x05 ] 5
            Item(Global): Report Count, data= [ 0x01 ] 1
            Item(Main  ): Feature, data= [ 0x02 ] 2
                            Data Variable Absolute No_Wrap Linear
                            Preferred_State No_Null_Position Non_Volatile Bitfield
            Item(Main  ): End Collection, data=none
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval             100
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      0 No Subclass
      bInterfaceProtocol      0 None
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.00
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      42
          Report Descriptor: (length is 42)
            Item(Global): Usage Page, data= [ 0x0d ] 13
                            Digitizer
            Item(Local ): Usage, data= [ 0x01 ] 1
                            Digitizer
            Item(Main  ): Collection, data= [ 0x01 ] 1
                            Application
            Item(Global): Report ID, data= [ 0x02 ] 2
            Item(Local ): Usage, data= [ 0x00 ] 0
                            Undefined
            Item(Global): Logical Minimum, data= [ 0x00 ] 0
            Item(Global): Logical Maximum, data= [ 0xff 0x00 ] 255
            Item(Global): Report Size, data= [ 0x08 ] 8
            Item(Global): Report Count, data= [ 0x09 ] 9
            Item(Main  ): Input, data= [ 0x02 ] 2
                            Data Variable Absolute No_Wrap Linear
                            Preferred_State No_Null_Position Non_Volatile Bitfield
            Item(Global): Report ID, data= [ 0x03 ] 3
            Item(Local ): Usage, data= [ 0x00 ] 0
                            Undefined
            Item(Global): Report Size, data= [ 0x08 ] 8
            Item(Global): Report Count, data= [ 0x09 ] 9
            Item(Main  ): Input, data= [ 0x02 ] 2
                            Data Variable Absolute No_Wrap Linear
                            Preferred_State No_Null_Position Non_Volatile Bitfield
            Item(Global): Report ID, data= [ 0x04 ] 4
            Item(Local ): Usage, data= [ 0x00 ] 0
                            Undefined
            Item(Global): Report Size, data= [ 0x08 ] 8
            Item(Global): Report Count, data= [ 0x09 ] 9
            Item(Main  ): Input, data= [ 0x02 ] 2
                            Data Variable Absolute No_Wrap Linear
                            Preferred_State No_Null_Position Non_Volatile Bitfield
            Item(Main  ): End Collection, data=none
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               4
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      0 No Subclass
      bInterfaceProtocol      0 None
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.00
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      23
          Report Descriptor: (length is 23)
            Item(Global): Usage Page, data= [ 0x00 0xff ] 65280
                            (null)
            Item(Local ): Usage, data= [ 0x01 ] 1
                            (null)
            Item(Main  ): Collection, data= [ 0x01 ] 1
                            Application
            Item(Global): Report ID, data= [ 0x02 ] 2
            Item(Local ): Usage, data= [ 0x01 ] 1
                            (null)
            Item(Global): Logical Minimum, data= [ 0x00 ] 0
            Item(Global): Logical Maximum, data= [ 0xff 0x00 ] 255
            Item(Global): Report Size, data= [ 0x08 ] 8
            Item(Global): Report Count, data= [ 0x3f ] 63
            Item(Main  ): Input, data= [ 0x02 ] 2
                            Data Variable Absolute No_Wrap Linear
                            Preferred_State No_Null_Position Non_Volatile Bitfield
            Item(Main  ): End Collection, data=none
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               2
Device Status:     0x0000
  (Bus Powered)
```Thanks for your help.
Regards,

Thierry

---

### Post by Favux on 2011-12-06
Hi ThierryMu,

As far as I'm aware the new BambooPT's Wireless Kit hasn't been added to the bluetooth stack yet.

The basic thing that probably needs to happen is it has to be switched from the regular speed interface to the high speed.  See the last few pages in this thread:  [http://ubuntuforums.org/showthread.php?t=674738](http://ubuntuforums.org/showthread.php?t=674738)

I don't know if you can piggyback on the graphire stuff in bluez.  If you could that would make it a lot easier.  You'll probably need some separate code for the Bamboo's like the Intuos4 requires.

I believe Przemo Firszt is the developer who added the Wacom Graphire Bluetooth to the kernel's bluez stack.  He's finally found some time to start adding the Intuos4 Wireless:  [http://sourceforge.net/mailarchive/forum.php?forum_name=linuxwacom-devel](http://sourceforge.net/mailarchive/forum.php?forum_name=linuxwacom-devel)  So he's the person to ask for help.  Linuxwacom-discuss would probably be the best place:  [https://lists.sourceforge.net/lists/listinfo/linuxwacom-discuss](https://lists.sourceforge.net/lists/listinfo/linuxwacom-discuss)

Hope this helps.

---

### Post by ThierryMu on 2011-12-06
Hi Favux,
Thank you one more time for your help and your enlightenment.
Regards.

---

### Post by folken1983 on 2011-12-06
> **ThierryMu said:**
> Here's how I proceeded :
```
cd desktop
git clone git://github.com/cbagwell/input-wacom.git -b bamboo3
cd input-wacom
./autogen.sh --prefix=/usr
sudo cp ./2.6.38/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
sudo depmod -a
```
Then I rebooted.

Thanks a lot! this worked for me on a laptop (dell m1330) and a desktop (XPS 8300), with the latest wacom bamboo pen (not touch).

---

### Post by Favux on 2011-12-06
Hi folken1983, ThierryMu, and everyone,

You should now be able to use the newly released input-wacom-0.12.0 tar as per part I. of the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").  Chris added third generation BambooPT support to it along with support for second generation BambooPT touch.

---

### Post by ThierryMu on 2011-12-06
> **Favux said:**
> You should now be able to use the newly released input-wacom-0.12.0 tar as per part I. of the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").  Chris added third generation BambooPT support to it along with support for second generation BambooPT touch.

I have installed this release : it works fine. No problem during the installation.
So the "famous" appendix 3 has disappeared :) : I think that it's easiest to understand how to do. Good work.
See you later.

---

### Post by sfworm on 2011-12-10
Hi there to all :)
I just got my Bamboo Fan Pan & Touch, CTH-470S-ITES and I'm desperate to make it work :( It took me hours and hours trying to follow all instructions from ubuntu forums but I can't make it work. I see that tablet lid is flashing when touching it but nothing else works.
I use Ubuntu 10.10, 2.6.35-31-generic. When I try lsmod | grep wacom I get
wacom                  29647  0

I'm not seeing the Appendix 3 in HOW TO post, so please help me?? :(

---

### Post by Favux on 2011-12-10
Hi sfworm,

Welcome to Ubuntu forums!

The reason appendix 3 is gone is the new models are now in the newly released input-wacom-0.12.0, part I.  So no need for separate instructions anymore.  See the notes on the third generation models near the top of the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").

Sorry, but you can't get your model working with Maverick.  You have to be in at least Natty, i.e. the 2.6.38 kernel, to get it working.

---

### Post by sfworm on 2011-12-17
Thanks for your reply :)

I installed Ubuntu 11.04 (I'm using classic view, still can't get used to Unity environment) and my Bamboo is working but there is one 'small' issue with stylus movements, those are not smooth and almost every 2-3rd second it freezes so I'm not able to draw smoothly :( I tried to search through forums, and I see that other had the same problem but none of the solutions works for me or I don't know how to apply them...

I suppose that people bothered you about this a 100 of times, but this is my first tablet I ever had so I don't have experience in using it at all (any kind, any model) so I'm not that much into terminology (pressure sensitive, multitouch, bla bla...I'm not even a designer, I just want to draw :))
Any suggestion or reference would be appreciated...please help :(

---

### Post by Favux on 2011-12-17
The work around most folks in Natty use is to log into *Gnome Classic without effects*.  At the log-in screen right click on the gear icon and the option will be there.  That also has the advantage of you not having to deal with Unity.  :)

Presumably it is the same bug that then makes Gimp unusable in Oneiric.  See this Launchpad bug report:  [https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/863154](https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/863154)  But if you use Alexia Death's patch to Gimp then Gimp becomes usable.  Here is a PPA with the patch already applied to Gimp:  [https://launchpad.net/~aapo-rantalainen/+archive/gimp26-noghostline](https://launchpad.net/~aapo-rantalainen/+archive/gimp26-noghostline)

No one has applied the patch to Natty's version of Gimp to see if it is the same bug and whether the patch fixes the problem there too.  You could ask Aapo Rantalainen if he'd be willing to add Natty to his PPA.

---

### Post by ThierryMu on 2011-12-18
Edit : message erased because it was the same as below (sorry)

---

### Post by ThierryMu on 2011-12-18
Hi,
We need to re-install wacom.ko after an upgrade of the kernel. So under Ubuntu Oneiric 11.10, after I upgraded from kernel 3.0.0.14 to 3.0.0.15, there's how I proceeded :
```
cd Desktop
wget http://prdownloads.sourceforge.net/linuxwacom/input-wacom-0.12.0.tar.bz2
tar xjvf input-wacom-0.12.0.tar.bz2
cd input-wacom-0.12.0
./configure --prefix=/usr
sudo cp ./2.6.38/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
sudo depmod -a
```
But if you have already intalled the new wacom.ko (with a previous kernel), you only have to do :
```
sudo cp Desktop/input-wacom-0.12.0/2.6.38/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
sudo depmod -a
```
After this, you need to reboot.
Regards

---

### Post by sfworm on 2011-12-20
Thanks for the post! I almost started to cry when I saw that the tablet is not responding after update but than I returned to this thread and tried the code and it's working :)

---

### Post by Naggobot on 2013-04-14
To update this info to some where. CTH-470 works in Ubuntu Precise out of the box. Only issues I had was the button configuration. [Wiki]("https://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration") lists following example for Bamboofun. 

```

xsetwacom set "Wacom BambooFun 4x5 pad" Button 1 "key esc" 
xsetwacom set "Wacom BambooFun 4x5 pad" Button 2 "key F12 "
xsetwacom set "Wacom BambooFun 4x5 pad" AbsWheelDown "key ctrl shift s"
xsetwacom set "Wacom BambooFun 4x5 pad" AbsWheelUp "key ctrl shift s"
xsetwacom set "Wacom BambooFun 4x5 pad" Button 3 "key KP_Next" 
xsetwacom set "Wacom BambooFun 4x5 pad" Button 4 "key KP_Prior" 

```

How ever CTH-470 is different device with different id 

```

xsetwacom --list

Wacom Bamboo 16FG 4x5 Pen stylus    id: 12    type: STYLUS    
Wacom Bamboo 16FG 4x5 Finger touch    id: 13    type: TOUCH     
Wacom Bamboo 16FG 4x5 Pen eraser    id: 18    type: ERASER    
Wacom Bamboo 16FG 4x5 Finger pad    id: 19    type: PAD       

```

Pad has only four buttons and no wheel. Properties can be set for buttons 1-3 and trying to 
set button 4 gives an error.

```

$ xsetwacom  --set "Wacom Bamboo 16FG 4x5 Finger pad" button 4 1
Unsupported offset into 'Wacom Button Actions' property.

```

After some trial and error I found out that the buttons are 1,9,8,3 from top to bottom. 
Configuring buttons according to wiki then becomes

```

xsetwacom set "Wacom Bamboo 16FG 4x5 Finger pad" Button 1 "key esc" 
xsetwacom set "Wacom Bamboo 16FG 4x5 Finger pad" Button 3 "key F12 "
 xsetwacom set "Wacom Bamboo 16FG 4x5 Finger pad" Button 8 "key KP_Next"
 xsetwacom set "Wacom Bamboo 16FG 4x5 Finger pad" Button 9 "key KP_Prior" 

```

and if you want gimp to zoom with center buttons then the correct config is

```

xsetwacom set "Wacom Bamboo 16FG 4x5 Finger pad" Button 1 1
xsetwacom set "Wacom Bamboo 16FG 4x5 Finger pad" Button 3 3
xsetwacom set "Wacom Bamboo 16FG 4x5 Finger pad" Button 8 "key minus"
xsetwacom set "Wacom Bamboo 16FG 4x5 Finger pad" Button 9 "key plus"
 
```

[In addition I found a good advice on how to reverse scrolling]("http://onethingwell.org/post/8779215052/reverse-scrolling-x11"). 
For me xinput --list gives

```

 Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; HID 04f3:0103                               id=11    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo 16FG 4x5 Pen stylus            id=12    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo 16FG 4x5 Finger touch          id=13    [slave  pointer  (2)]
&#9116;   &#8627; ETPS/2 Elantech Touchpad                    id=16    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo 16FG 4x5 Pen eraser            id=18    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo 16FG 4x5 Finger pad            id=19    [slave  pointer  (2)]

```
so instead of reversing the scroll for Wacom I reverted the scroll for Elantech touchpad 

```

xinput set-button-map 16 1 2 3 5 4 

```

so that the laptop touchpad will work the same as Wacom touch. I tested that with id 13 the command works for Wacom also.

---

