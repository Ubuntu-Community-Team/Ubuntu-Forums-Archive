---
title: "I need help with drivers and few questions"
date: 2013-08-25
forum: Hardware
---

### Post by Yotam_Khrizman on 2013-08-25
Hello, i bought the DELL Vostro 3360
i received it with Ubuntu but installed on it Windows.
Then i installed Ubuntu 13.04 .

And not i have few problems,
1. I cant control my touchpad, and control i mean Disable,Scroll on the web.
2. I want to use my fingerprint device, and i dont know how to do it.
3. There is a way to install Corel Paintshop X5 on Ubuntu?

Please help me.

---

### Post by varunendra on 2013-08-25
1) If the default touchpad control applet (System Settings > Mouse & Touchpad > Touchpad tab) doesn't give you sufficient controls, you may try "gpointing-device-settings" application that gives some extensive controls. To install it -
```
sudo apt-get install gpointing-device-settings
```
Although it is a GUI application, it doesn't create a launcher icon in Unity. So you'll have to run it from terminal with "gpointing-device-settings" command.

2) Many of the inbuilt fingerprint devices I've seen in laptops don't seem to be automatically recognized (due to lack of appropriate driver). To see if yours is (or can be) recognized, please post back the full output of -
```
usb-devices
```

3) It 'may' install over 'wine' (to install wine - "sudo apt-get install wine"), but I can't be sure. "Inkscape" is the native Linux application which is equivalent to Corel Draw on windows, but I'm not sure if it is also equivalent to Corel Paintshop. If you wish to try it, install it with -
```
sudo apt-get install inkscape
```
Hope someone else may be able to offer a better suggestion on this one.

---

### Post by Mark Phelps on 2013-08-25
The only rating in the Wine DB for PaintShop Pro is Garbage -- meaning, it's not going to work:  > [http://appdb.winehq.org/objectManager.php?sClass=application&iId=6523](http://appdb.winehq.org/objectManager.php?sClass=application&iId=6523)

Realize this is for an old version, but there's no info to indicate that the newer versions will work any better.

---

### Post by Yotam_Khrizman on 2013-08-25
Ok.

Now the touchpad recognized as PS/2 drive
And the fingerprint device is recognized but i have no software.

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.08
S:  Manufacturer=Linux 3.8.0-29-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1a.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 6
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=0024 Rev=00.00
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=01 Lev=02 Prnt=02 Port=00 Cnt=01 Dev#=  3 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=ff(vend.) Sub=11 Prot=ff MxPS= 8 #Cfgs=  1
P:  Vendor=138a ProdID=0011 Rev=00.78
S:  SerialNumber=b50672262014
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 4 Cls=ff(vend.) Sub=00 Prot=00 Driver=(none)


T:  Bus=01 Lev=02 Prnt=02 Port=02 Cnt=02 Dev#=  4 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ff(vend.) Sub=ff Prot=ff MxPS=64 #Cfgs=  1
P:  Vendor=0bda ProdID=0129 Rev=39.60
S:  Manufacturer=Generic
S:  Product=USB2.0-CRW
S:  SerialNumber=20100201396000000
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=06 Prot=50 Driver=rts5139


T:  Bus=01 Lev=02 Prnt=02 Port=04 Cnt=03 Dev#=  5 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=0c45 ProdID=648b Rev=28.07
S:  Manufacturer=CNFB183F181090001VC2
S:  Product=Laptop_Integrated_Webcam_E4HD
C:  #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=0e(video) Sub=01 Prot=00 Driver=uvcvideo
I:  If#= 1 Alt= 0 #EPs= 0 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo


T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.08
S:  Manufacturer=Linux 3.8.0-29-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 8
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=0024 Rev=00.00
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=02 Lev=02 Prnt=02 Port=04 Cnt=01 Dev#=  4 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=ff(vend.) Sub=01 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=0a5c ProdID=21d7 Rev=01.12
S:  Manufacturer=Broadcom Corp
S:  Product=BCM43142A0
S:  SerialNumber=9C2A70CE404A
C:  #Ifs= 4 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=01 Prot=01 Driver=btusb
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=01 Prot=01 Driver=btusb
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 3 Alt= 0 #EPs= 0 Cls=fe(app. ) Sub=01 Prot=01 Driver=(none)


T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 4
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.08
S:  Manufacturer=Linux 3.8.0-29-generic xhci_hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:00:14.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=5000 MxCh= 4
D:  Ver= 3.00 Cls=09(hub  ) Sub=00 Prot=03 MxPS= 9 #Cfgs=  1
P:  Vendor=1d6b ProdID=0003 Rev=03.08
S:  Manufacturer=Linux 3.8.0-29-generic xhci_hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:00:14.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

---

### Post by varunendra on 2013-08-25
> **Yotam_Khrizman said:**
> 
T:  Bus=01 Lev=02 Prnt=02 Port=00 Cnt=01 Dev#=  3 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=ff(vend.) Sub=11 Prot=ff MxPS= 8 #Cfgs=  1
P:  **[COLOR="#800000"]Vendor=138a ProdID=0011 Rev=00.78[/COLOR]**
S:  SerialNumber=b50672262014
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 4 Cls=ff(vend.) Sub=00 Prot=00 **[COLOR="#FF0000"]Driver=(none)[/COLOR]**

The above is your Finger Print device, which evidently doesn't have a driver associated, because no default Linux driver recognizes it.

I have no idea how Finger Print reading works in Ubuntu, so can't be much helpful regarding this. But I can give you a few pointers which may hopefully help you get it working.

First, there seems to be an experimental driver available for it which is reportedly working for everyone who tried. Please read the comments starting from #19 in this bug report page - [https://bugs.launchpad.net/ubuntu/+source/libfprint/+bug/790183](https://bugs.launchpad.net/ubuntu/+source/libfprint/+bug/790183)

Additionally, this thread seems to be dedicated to address the additional setup if needed : [http://ubuntuforums.org/showthread.php?t=760018](http://ubuntuforums.org/showthread.php?t=760018)

Read on, and post back if you have questions or problems regarding above. I'm sure there are others who can offer much better help on this.

Finally, if it works, please let us all know. Confirmation and details of a fix is a great way to help others. Thanks ! :)

---

### Post by Yotam_Khrizman on 2013-08-26
> **varunendra said:**
> The above is your Finger Print device, which evidently doesn't have a driver associated, because no default Linux driver recognizes it.

I have no idea how Finger Print reading works in Ubuntu, so can't be much helpful regarding this. But I can give you a few pointers which may hopefully help you get it working.

First, there seems to be an experimental driver available for it which is reportedly working for everyone who tried. Please read the comments starting from #19 in this bug report page - [https://bugs.launchpad.net/ubuntu/+source/libfprint/+bug/790183](https://bugs.launchpad.net/ubuntu/+source/libfprint/+bug/790183)

Additionally, this thread seems to be dedicated to address the additional setup if needed : [http://ubuntuforums.org/showthread.php?t=760018](http://ubuntuforums.org/showthread.php?t=760018)

Read on, and post back if you have questions or problems regarding above. I'm sure there are others who can offer much better help on this.

Finally, if it works, please let us all know. Confirmation and details of a fix is a great way to help others. Thanks ! :)


Ok thanks... 

But what do i need to do with my touchpad?
And is there is a way to do Windows 7 on VirtualBox that the screen will be 16:9 ratio and not 4:3?

---

### Post by varunendra on 2013-08-26
> **Yotam_Khrizman said:**
> But what do i need to do with my touchpad?
And is there is a way to do Windows 7 on VirtualBox that the screen will be 16:9 ratio and not 4:3?

Where does it appear as a PS/2 mouse? In gpointing-device-settings GUI?
Did you have a "Touchpad" tab in "System Settings > Mouse & Touchpad" application? Do you still have it there ?

Please post back the outputs of -
```
xinput
cat /proc/bus/input/devices
```

As for Win7 on VBox, it should support all possible aspect ratios once you install "Guest Additions" in the guest OS from "Devices > Install Guest Additions..." menu of the running virtual machine window. It is like installing drivers for the virtual hardware. If having troubles with that, I'd suggest to start a new thread in "[Virtualisation]("http://ubuntuforums.org/forumdisplay.php?f=308")" section of the forums, and ask your question there providing full details of the problem.

---

### Post by Yotam_Khrizman on 2013-08-26
> **varunendra said:**
> Where does it appear as a PS/2 mouse? In gpointing-device-settings GUI?
Did you have a "Touchpad" tab in "System Settings > Mouse & Touchpad" application? Do you still have it there ?

Please post back the outputs of -
```
xinput
cat /proc/bus/input/devices
```

As for Win7 on VBox, it should support all possible aspect ratios once you install "Guest Additions" in the guest OS from "Devices > Install Guest Additions..." menu of the running virtual machine window. It is like installing drivers for the virtual hardware. If having troubles with that, I'd suggest to start a new thread in "[Virtualisation]("http://ubuntuforums.org/forumdisplay.php?f=308")" section of the forums, and ask your question there providing full details of the problem.
```

yotam@yotam-Dell-System-Vostro-3360:~$ xinput
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                       id=10    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                       id=11    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Generic Mouse                          id=14    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; Laptop_Integrated_Webcam_E4HD               id=12    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=13    [slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                            id=15    [slave  keyboard (3)]
yotam@yotam-Dell-System-Vostro-3360:~$ cat /proc/bus/input/devices
I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
U: Uniq=
H: Handlers=kbd event0 
B: PROP=0
B: EV=3
B: KEY=10000000000000 0


I: Bus=0019 Vendor=0000 Product=0003 Version=0000
N: Name="Sleep Button"
P: Phys=PNP0C0E/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: PROP=0
B: EV=3
B: KEY=4000 0 0


I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input2
U: Uniq=
H: Handlers=event2 
B: PROP=0
B: EV=21
B: SW=1


I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
U: Uniq=
H: Handlers=kbd event3 
B: PROP=0
B: EV=3
B: KEY=10000000000000 0


I: Bus=0011 Vendor=0001 Product=0001 Version=ab83
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input4
U: Uniq=
H: Handlers=sysrq kbd event4 
B: PROP=0
B: EV=120013
B: KEY=1100f02902002 8380307cf910f001 feffffdfffefffff fffffffffffffffe
B: MSC=10
B: LED=7


I: Bus=0003 Vendor=046d Product=c52f Version=0111
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:14.0-1/input0
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1:1.0/input/input5
U: Uniq=
H: Handlers=mouse0 event5 
B: PROP=0
B: EV=17
B: KEY=ffff0000 0 0 0 0
B: REL=143
B: MSC=10


I: Bus=0003 Vendor=046d Product=c52f Version=0111
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:14.0-1/input1
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1:1.1/input/input6
U: Uniq=
H: Handlers=kbd event6 
B: PROP=0
B: EV=1f
B: KEY=4837fff072ff32d bf54444600000000 1 20f908b17c000 677bfad9415fed 9ed68000004400 10000002
B: REL=40
B: ABS=100000000
B: MSC=10


I: Bus=0019 Vendor=0000 Product=0000 Version=0000
N: Name="Dell WMI hotkeys"
P: Phys=wmi/input0
S: Sysfs=/devices/virtual/input/input7
U: Uniq=
H: Handlers=rfkill kbd event7 
B: PROP=0
B: EV=13
B: KEY=1500b00000000 200300000 0 0
B: MSC=10


I: Bus=0003 Vendor=0c45 Product=648b Version=2807
N: Name="Laptop_Integrated_Webcam_E4HD"
P: Phys=usb-0000:00:1a.0-1.5/button
S: Sysfs=/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.0/input/input8
U: Uniq=
H: Handlers=kbd event8 
B: PROP=0
B: EV=3
B: KEY=100000 0 0 0


I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=LNXVIDEO/video/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input9
U: Uniq=
H: Handlers=kbd event9 
B: PROP=0
B: EV=3
B: KEY=3e000b00000000 0 0 0


I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH HDMI/DP,pcm=3"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input10
U: Uniq=
H: Handlers=event10 
B: PROP=0
B: EV=21
B: SW=140


I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH Mic"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input11
U: Uniq=
H: Handlers=event11 
B: PROP=0
B: EV=21
B: SW=10


I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH Headphone"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input12
U: Uniq=
H: Handlers=event12 
B: PROP=0
B: EV=21
B: SW=4


I: Bus=0011 Vendor=0002 Product=0001 Version=0000
N: Name="PS/2 Generic Mouse"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input13
U: Uniq=
H: Handlers=mouse1 event13 
B: PROP=0
B: EV=7
B: KEY=70000 0 0 0 0
B: REL=3


``````

yotam@yotam-Dell-System-Vostro-3360:~$ xinput
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                       id=10    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                       id=11    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Generic Mouse                          id=14    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; Laptop_Integrated_Webcam_E4HD               id=12    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=13    [slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                            id=15    [slave  keyboard (3)]
yotam@yotam-Dell-System-Vostro-3360:~$ cat /proc/bus/input/devices
I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
U: Uniq=
H: Handlers=kbd event0 
B: PROP=0
B: EV=3
B: KEY=10000000000000 0


I: Bus=0019 Vendor=0000 Product=0003 Version=0000
N: Name="Sleep Button"
P: Phys=PNP0C0E/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: PROP=0
B: EV=3
B: KEY=4000 0 0


I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input2
U: Uniq=
H: Handlers=event2 
B: PROP=0
B: EV=21
B: SW=1


I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
U: Uniq=
H: Handlers=kbd event3 
B: PROP=0
B: EV=3
B: KEY=10000000000000 0


I: Bus=0011 Vendor=0001 Product=0001 Version=ab83
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input4
U: Uniq=
H: Handlers=sysrq kbd event4 
B: PROP=0
B: EV=120013
B: KEY=1100f02902002 8380307cf910f001 feffffdfffefffff fffffffffffffffe
B: MSC=10
B: LED=7


I: Bus=0003 Vendor=046d Product=c52f Version=0111
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:14.0-1/input0
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1:1.0/input/input5
U: Uniq=
H: Handlers=mouse0 event5 
B: PROP=0
B: EV=17
B: KEY=ffff0000 0 0 0 0
B: REL=143
B: MSC=10


I: Bus=0003 Vendor=046d Product=c52f Version=0111
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:14.0-1/input1
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1:1.1/input/input6
U: Uniq=
H: Handlers=kbd event6 
B: PROP=0
B: EV=1f
B: KEY=4837fff072ff32d bf54444600000000 1 20f908b17c000 677bfad9415fed 9ed68000004400 10000002
B: REL=40
B: ABS=100000000
B: MSC=10


I: Bus=0019 Vendor=0000 Product=0000 Version=0000
N: Name="Dell WMI hotkeys"
P: Phys=wmi/input0
S: Sysfs=/devices/virtual/input/input7
U: Uniq=
H: Handlers=rfkill kbd event7 
B: PROP=0
B: EV=13
B: KEY=1500b00000000 200300000 0 0
B: MSC=10


I: Bus=0003 Vendor=0c45 Product=648b Version=2807
N: Name="Laptop_Integrated_Webcam_E4HD"
P: Phys=usb-0000:00:1a.0-1.5/button
S: Sysfs=/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.0/input/input8
U: Uniq=
H: Handlers=kbd event8 
B: PROP=0
B: EV=3
B: KEY=100000 0 0 0


I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=LNXVIDEO/video/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input9
U: Uniq=
H: Handlers=kbd event9 
B: PROP=0
B: EV=3
B: KEY=3e000b00000000 0 0 0


I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH HDMI/DP,pcm=3"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input10
U: Uniq=
H: Handlers=event10 
B: PROP=0
B: EV=21
B: SW=140


I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH Mic"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input11
U: Uniq=
H: Handlers=event11 
B: PROP=0
B: EV=21
B: SW=10


I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH Headphone"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input12
U: Uniq=
H: Handlers=event12 
B: PROP=0
B: EV=21
B: SW=4


I: Bus=0011 Vendor=0002 Product=0001 Version=0000
N: Name="PS/2 Generic Mouse"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input13
U: Uniq=
H: Handlers=mouse1 event13 
B: PROP=0
B: EV=7
B: KEY=70000 0 0 0 0
B: REL=3





```

That's what i get with those 2  commands
GUI Point read my touchpad as  PS/2


And about the other issue (WIN 7) How do i install it?!
I dont have Devices up on the task bar.

---

### Post by varunendra on 2013-08-26
> **Yotam_Khrizman said:**
> yotam@yotam-Dell-System-Vostro-3360:~$ xinput
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                       id=10    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                       id=11    [slave  pointer  (2)]
&#9116;   &#8627;**[COLOR="#FF0000"] PS/2 Generic Mouse [/COLOR]**                         id=14    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; Laptop_Integrated_Webcam_E4HD               id=12    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=13    [slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                            id=15    [slave  keyboard (3)]
*<snip>*

I: Bus=0011 **[COLOR="#FF0000"]Vendor=0002 Product=0001[/COLOR]** Version=0000
N: **[COLOR="#FF0000"]Name="PS/2 Generic Mouse"[/COLOR]**
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input13
U: Uniq=
H: Handlers=mouse1 event13 
B: PROP=0
B: EV=7
B: KEY=70000 0 0 0 0
B: REL=3
Okay, I'm totally stumped by those outputs. May sound an utterly stupid question, but just to rule out the obvious - is there any other pointing device, of any kind, connected besides the touch pad? I hope not.

And.. does the default Mouse & Touchpad controlling application still show a "Touchpad" tab? Did it have it earlier?


> And about the other issue (WIN 7) How do i install it?!
I dont have Devices up on the task bar.
The "Devices" menu is part of the virtual machine window, not the VBox window. So it will appear when a virtual machine is running and the window, in which it is running, is in focus.

**PS:**
Please use '***[COLOR="#000080"]Code[/COLOR]***' tags to post commands and output codes. It puts the output in a nice box, preserving its formatting, thus making the post look clean, compact and more readable. :)
Just click on the "**#**" button on the top of edit box to generate the tags, then copy-paste the code in-between the tags. You may follow the "Code Tags example" link in my signature to see an elaborated example. Thanks!

---

### Post by Yotam_Khrizman on 2013-08-27
> **varunendra said:**
> Okay, I'm totally stumped by those outputs. May sound an utterly stupid question, but just to rule out the obvious - is there any other pointing device, of any kind, connected besides the touch pad? I hope not.

And.. does the default Mouse & Touchpad controlling application still show a "Touchpad" tab? Did it have it earlier?



The "Devices" menu is part of the virtual machine window, not the VBox window. So it will appear when a virtual machine is running and the window, in which it is running, is in focus.

**PS:**
Please use '***[COLOR=#000080]Code[/COLOR]***' tags to post commands and output codes. It puts the output in a nice box, preserving its formatting, thus making the post look clean, compact and more readable. :)
Just click on the "**#**" button on the top of edit box to generate the tags, then copy-paste the code in-between the tags. You may follow the "Code Tags example" link in my signature to see an elaborated example. Thanks!



You saw the other device, its the Logitech USB Receiver.
Nothing else us connected.

And in the Vbox, i have no menu at all.

---

