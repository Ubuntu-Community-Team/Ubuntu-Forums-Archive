---
title: "ati driver on ubuntu 9.04 login freeze"
date: 2009-06-02
forum: Hardware
---

### Post by darksniperx on 2009-06-02
I have installed ubuntu 9.04 and updated it.

The only thing that did not work properly was the resolution on my video card. After some searching, I found and article which told me to do "sudo dpkg-reconfigure xserver-xorg" although x server was not installed, and I did not not which one to install from the list. Then after looking for more info, I find that dpkg-reconfigure is obsolete, and it was recommended not to use it, but instead to install the driver from add/remove programs. Which I did, Ati x-org and then restarted ubuntu. My ubuntu loads up and as soon as it will get to login screen, I see 2 ubuntu loading logos on the first half of the screen and my background on lower half of the screen. My video card is ati m3.

What can I do to resolve this issue.

Thank you!

Edit:

Any hints or information would be appreciated

---

### Post by t3dium on 2009-06-04
It seems like I have an issue that looks very much like this one.
Anyone has an idea on this?

---

### Post by Mans2k on 2009-06-04
I have same problem with ATI Radeon 4870x2 on Ubuntu 9.04 :(

---

### Post by kannedheat on 2009-06-04
I had the same problem. Try this it worked for me.

Boot up to a terminal session and type:
```
apt-get remove --purge xorg-driver-fglrx
```
Since I used the ATI console
```
/urs/share/ati/fglrx -uninstall.sh
```
```
reboot
```
I was good to go. You might want to try
```
apt-get install xserver-xorg-video-radeon
```
If you need to get online through the terminal session 
```
iwconfig
```
```
ifconfig *$device_name* up
```
```
iwlist scan
``````
iwconfig *$device* essid "*connections name*"
```
```
dhclient *$device*
```
Good luck

---

### Post by darksniperx on 2009-06-05
Thanks for the reply, Although as much as I would have wanted to try out the code, I wasn't able to, since I have reinstalled ubuntu not too long before you have left the reply. But I have fixed the issues that I had with my display. 

I have noticed that r128 driver is already installed, but it does not detect my monitor, hence does not provide correct resolution. After analyzing xorg.conf file of other users, I have modified mine to add resolution modes and it works now.

Thanks for the relies.

---

### Post by t3dium on 2009-06-05
Thanks kannedheat!

Yesterday I tried removing the fglrx drivers and that indeed helped.
Will try to install the Radeon drivers this evening.

---

### Post by willmcgugan on 2009-06-05
> **darksniperx said:**
> Thanks for the reply, Although as much as I would have wanted to try out the code, I wasn't able to, since I have reinstalled ubuntu not too long before you have left the reply. But I have fixed the issues that I had with my display. 

I have noticed that r128 driver is already installed, but it does not detect my monitor, hence does not provide correct resolution. After analyzing xorg.conf file of other users, I have modified mine to add resolution modes and it works now.

Thanks for the relies.
Hi,

Would you mind giving a summary of the changes you made. I've been getting the same issue. Only a fresh install of Ubuntu works for me, but not at the native resolution of my laptop. If I install any of the drivers I get a garbled screen.

Will

---

### Post by darksniperx on 2009-06-05
> **willmcgugan said:**
> Hi,

Would you mind giving a summary of the changes you made. I've been getting the same issue. Only a fresh install of Ubuntu works for me, but not at the native resolution of my laptop. If I install any of the drivers I get a garbled screen.

Will

Hi Will,

Here is what looked like my original /etc/X11/xorg.conf file

```

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

I have modified the file to look like this:

```
Section "Device"
	Identifier	"ATI"
	Boardname 	"Ati Rage 128 M3"
	Driver		"r128"
	Screen		0
	Vendorname	"ATI"
	Option		"MergeFB" "off"
EndSection

Section "Monitor"
	Identifier	"My Monitor"
	HorizSync 	31.5 - 50.0
	VertRefresh 	40-90
EndSection

Section "Screen"
	Identifier "Screen 1"
	Device "ATI"
	Monitor "My Monitor"
	DefaultDepth 24
                Subsection "Display"
	              Depth 24
	              Modes "1024x768" "800x600" "640x480"
                EndSubsection

EndSection
```

Hope this helps!

---

