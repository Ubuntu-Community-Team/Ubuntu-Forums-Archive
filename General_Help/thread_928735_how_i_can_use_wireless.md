---
title: "how i can use wireless"
date: 2008-09-24
forum: General Help
---

### Post by THE BLUE DRAGON on 2008-09-24
hi i have laptop compac
and i use wireless on windwos but how i can use ot on ubuntu

---

### Post by qstraza on 2008-09-24
well is your wifi working properly?
whats the output of ```
iwconfig
```?

---

### Post by brookswm on 2008-09-24
I just set up my desktop to connect to my wireless router last night.  All I had to do was click on the wireless signal in the top right hand corner of Gnome and find the router I wanted to connect to.  It was password protected so I was prompted for that information, but I found it just as easy as connecting with XP or OS X.

---

### Post by THE BLUE DRAGON on 2008-09-24
> **qstraza said:**
> well is your wifi working properly?
whats the output of ```
iwconfig
```?

lo        no wireless extensions.

eth0      no wireless extensions.

????

---

### Post by Kevbert on 2008-09-24
You need to install some wireless firmware drivers.  Before you can do this you need to post the output from terminal of
```
lspci
```
Terminal can be found under Applications - Accessories.  To copy select the text so that it is highlighted with the mouse and press Ctrl-Shift-C to copy, open a new post and press Ctrl-V to post here.

---

### Post by THE BLUE DRAGON on 2008-09-24
lspci
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
02:04.0 Communication controller: Agere Systems LT WinModem (rev 02)
02:06.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)
02:0e.0 USB Controller: NEC Corporation USB (rev 41)
02:0e.1 USB Controller: NEC Corporation USB (rev 41)
02:0e.2 USB Controller: NEC Corporation USB 2.0 (rev 02)

what`s that mean plz help me

---

### Post by Kevbert on 2008-09-24
Can't see a wireless adapter there... What's the make and exact model of the laptop ?  Ubuntu hasn't seen your wireless adapter.  Is there a front panel switch to turn wireless on and off ?  Or do you use a USB dongle ?

---

### Post by THE BLUE DRAGON on 2008-09-24
my model 
laptop compac 
Evo N800c

---

### Post by Kevbert on 2008-09-24
Have you tried using the Fn+F2 key combination to try to turn on wireless ?
If you then enter
```
iwconfig
lspci
```
in terminal do you get anything different ?
If not you'll need to install the windows driver using ndiswrapper and ndisgtk which are on the Hardy CD under  /pool/main/n directory.  Double click on the deb files to install them, then select System - Administration - Windows Wireless Drivers and point to the windows wireless driver (an .inf file).

---

### Post by THE BLUE DRAGON on 2008-09-24
in terminal do you get anything different ?
nothing new it`s the seam thing
[COLOR="Teal"][COLOR="Teal"][COLOR="Navy"]
If not you'll need to install the windows driver using ndiswrapper and ndisgtk which are on the Hardy CD under /pool/main/n directory. Double click on the deb files to install them, then select System - Administration - Windows Wireless Drivers and point to the windows wireless driver (an .inf file).[/COLOR][/COLOR][/COLOR]

can u explane more i don`t anderstand

---

### Post by rob356 on 2008-09-24
I have an Evo N800c and it dosen't come with WiFi. You have to get either a USB wifi adapter or a PCMCIA wifi adapter.

---

### Post by THE BLUE DRAGON on 2008-09-24
> **rob356 said:**
> I have an Evo N800c and it dosen't come with WiFi. You have to get either a USB wifi adapter or a PCMCIA wifi adapter.

what u mean i can`t use wireless on ubuntu ](*,)](*,)

---

### Post by rob356 on 2008-09-24
No, did you buy a wireless card for your laptop? The Evo N800C does not come with built in wifi, you must buy an addon card.

---

### Post by THE BLUE DRAGON on 2008-09-24
no 
befor i install ubuntu i was use xp and i use wireless 
but when i install ubuntu it`s dosen`t work

---

### Post by rob356 on 2008-09-24
If you used wireless in XP, then what are you using for a wireless card, does you monitor have a bump, like 1 inch high on it? Do you have any usb wifi cards, or PCMCIA cards? We need to know what wireless card you are using.

---

### Post by THE BLUE DRAGON on 2008-09-24
i don`t know 
can u tell me how i can know
or where i can find the name on mt laptop

---

### Post by rob356 on 2008-09-24
Close the lid of your laptop. Do you have a kind of large bump on the top of the right side? If Not look on the left side of the laptop, is these something sticking out of the side of the right side? If not look on the back, is anything plugged into the USB ports?

---

### Post by THE BLUE DRAGON on 2008-09-24
i see only ( wieless lan w200 )

---

### Post by THE BLUE DRAGON on 2008-09-24
i am wait plz i need help

---

### Post by THE BLUE DRAGON on 2008-09-24
i see only ( wieless lan w200 )

---

### Post by rob356 on 2008-09-24
See [this page](https://help.ubuntu.com/community/WifiDocs/Device/CompaqW200). You are using ubuntu 8.04, and follow those directions EXACTALLY.

---

### Post by THE BLUE DRAGON on 2008-09-24
> guys i search in the web and i found 
[https://help.ubuntu.com/community/WifiDocs/Device/CompaqW200](https://help.ubuntu.com/community/WifiDocs/Device/CompaqW200)
i Installing the driver from
For 8.04 (2.6.24-16-generic) and 8.10 (2.6.26-5-generic):

svn co -r 1300 [https://orinoco.svn.sourceforge.net/svnroot/orinoco/branches/usb/](https://orinoco.svn.sourceforge.net/svnroot/orinoco/branches/usb/)

We now need to compile and install the driver:

  cd usb
  make
  sudo make install




what`s i must do now 
plz answer me

---

### Post by THE BLUE DRAGON on 2008-09-24
now i install 
sudo apt-get install build-essential subversion linux-headers-`uname -r` gcc-3.4-base cpp-3.4 curl
and i make Installing the driver 
but i have problem in Downloading the firmware 
cd \ firmware

bash: cd:  firmware: No such file or directory

??????

---

### Post by THE BLUE DRAGON on 2008-09-24
thanks now i can use it 
thanks very much

---

