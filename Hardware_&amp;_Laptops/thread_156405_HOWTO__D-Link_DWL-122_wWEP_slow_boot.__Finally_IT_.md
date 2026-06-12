---
title: "HOWTO : D-Link DWL-122 w/WEP slow boot.  Finally IT WORKS!! Thanks  to AZZ."
date: 2006-04-07
forum: Hardware &amp; Laptops
---

### Post by heislord5 on 2006-04-07
OK.  I could get my card to work as long as I turned encryption off.  But nothing I did to turn encryption on seemed to work.  Nothing!  The closest I could get was having the card recognize my router and access point thing, but still saying encryption was off when I did "iwconfig" to check status.  Otherwise I had to turn encryption off on my router to get internet access.  The thing that finally did it for me and got it working was adding the following to my interfaces (I had tried millions of variations, but this is the one that worked):

> iface wlan0 inet dhcp
wlan_ng_key0 57:92:00:40:50
wireless_mode managed
wireless_enc on
# wireless_key 57:92:00:40:50

auto wlan0

Thanks to AZZ for posting this solution....you're the man.
for keyword search linux-wlan-ng WEP dwl-122 encryption key reboot slow boot slow

---

### Post by heislord5 on 2006-04-07
As stated elsewhere I think the steps are:

install the linux-wlan-ng package included with ubuntu from the synaptic package manager.

Edit the /etc/network/interfaces to include the stuff outlined above....I think that's all you have to do.

Brad

---

### Post by Mr_Welfare on 2006-04-16
Hi,

I saw your thread and how you got your DWL-122 to work. I've had the same problem and have done a lot of editing to my

```
/etc/network/interfaces
```

without backing it up. Could you please post what your /etc/nework/interfaces looks like so I can enter that into mine? (Making changes for the key of course)

Thanks,

Mr_Welfare

---

### Post by heislord5 on 2006-04-16
full text of my interfaces file:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

iface wlan0 inet dhcp
wlan_ng_key0 12:34:56:78:90
wireless_mode managed
wireless_enc on

auto wlan0

---

### Post by Mr_Welfare on 2006-04-16
Ok thanks. I'll copy that in and give it a shot. The only thing is that don't you need your essid somewhere in there? Or is that automatically taken care of?

---

### Post by YuHoo on 2006-04-16
Just to point out to other users, he is using 64bit/40bit encryption. The current is 128bit encryption which consists of 26 characters. These are also HEX representations of ASCII letters. So in reality you could have a 5 letter passcode for 64/40 and a 13 letter for 128bit. 

Additionally D-Link offers experimental Linux drivers for all you ndis psychos. [http://support.dlink.com/faq/view.asp?prod_id=357](http://support.dlink.com/faq/view.asp?prod_id=357)

---

### Post by Mr_Welfare on 2006-04-16
[FONT=Verdana][SIZE=1][LEFT]So I have tried copying your
 
```
 
/etc/network/interfaces

```
 
(While changing the encryption code), but I still haven't had any luck. My adapter's (DWL-122 Ver. A2) "link" light just blinks on and off during the Ubuntu startup screen. Once the loader gets to the "Configuring Network" section, the light will blink, then turn off, blink, then turn off, etc. I have installed the *linux-wlan-ng* package from the synaptic package manager, so unless something else needs to be done, the only thing I can think of that might be causing a problem is the driver. Right now, I am using *ndiswrapper* and the Windows drivers off of the D-Link CD. I've heard that there is a native Linux driver for my adapter, but I'm not sure where to find it. What driver are you using? If it's different from the one that I'm using, could you please attach it to your next post?
 
Thanks,
 
Mr_Welfare
 
Note: I was also wondering how you configured your internet (wlan0) connection. Did you go through the terminal? If so, what lines of code did you use, and what files did you edit? If you went through the *System>Administrator>Networking*, how did you go about setting that up?
 
I just saw YuHoo's post and just to clarify, I am using a Hexidecimal 64 bit encryption code.
 
:-| Sorry for all the questions. :-| 
[/LEFT]

[/SIZE][/FONT]

---

### Post by YuHoo on 2006-04-16
I'll redirect you to my previous post. [http://support.dlink.com/faq/view.asp?prod_id=357](http://support.dlink.com/faq/view.asp?prod_id=357)
Scroll down the page and select the DWL-122. (For those with other cards/similar problems)

Before installing, uninstall the ndiswrapper and driver.
[ftp://ftp.linux-wlan.org/pub/linux-wlan-ng/](ftp://ftp.linux-wlan.org/pub/linux-wlan-ng/) is where it will take you, at the bottom of the page is the most current release. Get it. Then read the README provided on the site for install instructions. 

Also... questions are good. Without questions from beginning users, I'm useless on these forums. So, you keep me in business. It also helps others because they usually have many questions like you and it solves all the problems in one place. Very nice when you're searching for the answer. Finally, it makes me think critically about problems, perhaps things I don't think of. So if I encounter it on the forums or in life I can solve more of it and also understand the workings of linux better.

---

### Post by az on 2006-04-16
[QUOTE=Mr_Welfare][FONT=Verdana][SIZE=1][LEFT]So I have tried copying your
 
```
 
/etc/network/interfaces

```
 
(While changing the encryption code), but I still haven't had any luck. My adapter's (DWL-122 Ver. A2) "link" light just blinks on and off during the Ubuntu startup screen. Once the loader gets to the "Configuring Network" section, the light will blink, then turn off, blink, then turn off, etc. I have installed the *linux-wlan-ng* package from the synaptic package manager, so unless something else needs to be done, the only thing I can think of that might be causing a problem is the driver. Right now, I am using *ndiswrapper* and the Windows drivers off of the D-Link CD. I've heard that there is a native Linux driver for my adapter, but I'm not sure where to find it. What driver are you using? If it's different from the one that I'm using, could you please attach it to your next post?
 
Thanks,
 
Mr_Welfare
 
Note: I was also wondering how you configured your internet (wlan0) connection. Did you go through the terminal? If so, what lines of code did you use, and what files did you edit? If you went through the *System>Administrator>Networking*, how did you go about setting that up?
 
I just saw YuHoo's post and just to clarify, I am using a Hexidecimal 64 bit encryption code.
 
:-| Sorry for all the questions. :-| 
[/LEFT]

[/SIZE][/FONT][/QUOTE]

If ndiswrapper is being used, it will try to use the device and conflict with the native linux driver that you want to use.  

Remove the ndiswrapper windows driver and then reboot.

ndiswrapper -e netprism.inf

That should do it.

---

### Post by Mr_Welfare on 2006-04-16
[quote=azz]If ndiswrapper is being used, it will try to use the device and conflict with the native linux driver that you want to use. 
 
Remove the ndiswrapper windows driver and then reboot.
 
ndiswrapper -e netprism.inf
 
That should do it.[/quote]
 
Will the code ndiswrapper -e netprism.inf install the native driver, or remove the old one? If it won't install the native driver, where could I find a native driver for my specific adapter? (I haven't been able to find one yet).

---

### Post by heislord5 on 2006-04-16
Mr_Welfare,

in other words...you're doing too much.  The ndis and windows drivers is overdoing it.

When you install the  linux-wlan-ng package, included in ubuntu...you are installing the drivers.  When you change the interfaces file, that allows your encryption to work.

When you install ndis on top of that, you are double installing drivers, possibly causing problems.

I don't have ndiswrapper installed, but to know what it does type:

man nsidwrapper

at the command prompt. or maybe:

ndiswrapper -h

or something like that.  Should give you options and what the options mean.

You may be able to go to the symantic package installer to remove ndiswrapper.   But following AZZ's instructions to uninstall is probably best...he knows a lot more than I do about this.

So ndis and native drivers are two different incompatible ways to the same goal.

---

### Post by heislord5 on 2006-04-16
Also,

I can only vouche for 10 character encoding I used.  I just entered the numbers as they appears on the modem.  with : between every 2 characters..as you can see from my previous posts.  If you are using 26 character encoding, I can't vouche for whether or not DWL-122 can do it.  Sometimes all encodings are not supported by the drivers....so I would recommend you:

1) Find a thread where someone got your encoding to work with the driver you are using (ndis vs linux-wlan-ng) and get it working doing what they did

2) Completely uninstall changes you've made, switch your modem to 10 character encoding through the modems home page....if it's not already using 10 character encoding.  If you have  a windows PC using the same type of card, you can see how many characters it has for it's encoding key.  Then you can follow our instructions for getting it working with linux-wlan-ng and modifications to the interfaces file.

---

### Post by heislord5 on 2006-04-16
also,

I installed ubuntu from CD.  To enable repositories:


Go to synaptic package manager and select settings->repositories.

You should be able to edit the Ubuntu cd's repository to add universe and multiverse.

---

### Post by Mr_Welfare on 2006-04-16
Ok. A lot of information there thanks. I am already using 10 character (64 bit) encryption. I'm uninstalling the ndiswrapper right now and restarting, so hopefully I'll get it up and running. :)

---

### Post by Mr_Welfare on 2006-04-16
Ok. Now I have uninstalled the prism02 drivers from my ndiswrapper. (I thought that it would be good to let you know that Ndiswrapper is still installed, just in case this might cause a problem). Anyways, I seem to have run into even bigger problems. Now when I go into the *System>Administrator>Networking*, my card doesn't show up. (No wireless [wlan0] shows up as well.) I also reinstalled the linux-wlan-ng package just in case there might be a problem there, but had no luck. The code
 
```
sudo ifup wlan0 
```
 
gives me this mesage:
 
> <!--StartFragment-->wlanctl-ng: No such device
Failed to enable the device, exitcode= 1 .
run-parts: /etc/network/if-pre-up.d/linux-wlan-ng-pre-up exited with return code 1
Error for wireless request "Set Mode" (8B06) :
SET failed on device wlan0 ; No such device.
Error for wireless request "Set Encode" (8B2B) :
GET failed on device wlan0 ; No such device.
There is already a pid file /var/run/dhclient.wlan0.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP]("http://www.isc.org/products/DHCP")
 
sit0: unknown hardware address type 776
SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
sit0: unknown hardware address type 776
Bind socket to interface: No such device
Failed to bring up wlan0.
 
 
I noticed one thing as well. When I was installing the linux-wlan-ng package, in the desciption of the package, it said that I needed the linux-wlan-ng-modules-x.yy.zz. I have no idea what this is and how to install it.
 
I also thought that I should let eveyone know that I have not installed any repositories such as universe or multiuniverse , as the package manager seems to need an internet connection for it to run. (Sorry if there is a misunderstanding here)
 
Mr_Welfare

---

### Post by az on 2006-04-16
[QUOTE=Mr_Welfare]Ok. Now I have uninstalled the prism02 drivers from my ndiswrapper. (I thought that it would be good to let you know that Ndiswrapper is still installed, just in case this might cause a problem). Anyways, I seem to have run into even bigger problems. Now when I go into the *System>Administrator>Networking*, my card doesn't show up.
[/QUOTE]

That's because that particular device does not speak the same language as all the other wireless devices in linux, that's all.  That's why you need to change the interfaces file by hand instead of letting the networking tool do it.

[QUOTE=Mr_Welfare]

I noticed one thing as well. When I was installing the linux-wlan-ng package, in the desciption of the package, it said that I needed the linux-wlan-ng-modules-x.yy.zz. I have no idea what this is and how to install it.[/QUOTE]

The prism2_usb module is included in the ubuntu kernel.  That package description is wrong and is already changed in Dapper:
" The standard Ubuntu kernel already contains all necessary drivers. This
 package ships utilities and integration scripts to make above cards work
 seamlessly with the Ubuntu network infrastructure."

---

### Post by Mr_Welfare on 2006-04-16
So even if I can't see the card in the network settings, and even if the network can't start when using *sudo ifup wlan0*, then I'm still ok and good to go? I did edit the
 
/etc/network/interfaces 
 
by hand (according to the beginning of this thread) is that right? Also, am I supposed to put the essid somewhere in the 
 
/etc/network/interfaces
 
file? How would the adapter know what to connect to if the essid wasn't there?
 
Also, how do I go about uninstalling the whole ndiswrapper program? I have just uninstalled the driver prisma02.inf. Is this enough? Or do I need to uninstall the whole program?

---

### Post by az on 2006-04-16
[QUOTE=Mr_Welfare]So even if I can't see the card in the network settings, and even if the network can't start when using *sudo ifup wlan0*, then I'm still ok and good to go? I did edit the
 
/etc/network/interfaces 
 
by hand (according to the beginning of this thread) is that right? Also, am I supposed to put the essid somewhere in the 
 
/etc/network/interfaces
 
file? How would the adapter know what to connect to if the essid wasn't there?
[/QUOTE]

I think you should have a stanza like this:
auto wlan0

iface wlan0 inet dhcp
 wireless_mode managed
 wireless_essid abcdef
 wireless_enc on
 wlan_ng_key0 aa:bb:cc:dd:ee

 [QUOTE=Mr_Welfare]
Also, how do I go about uninstalling the whole ndiswrapper program? I have just uninstalled the driver prisma02.inf. Is this enough? Or do I need to uninstall the whole program?[/QUOTE]
Well, you can make ndiswrapper not do anything by removeing the inf file.  so that should work fine.  

Just for fun, reboot without the device, open a terminal and type:

tail -f /var/log/messages
and plug in the device.  Post the output.

---

### Post by Mr_Welfare on 2006-04-16
[quote=azz]
 
Just for fun, reboot without the device, open a terminal and type:
 
tail -f /var/log/messages
and plug in the device. Post the output.[/quote]
 
Here is the output.
 
[EMAIL="scott@Ubuntu:~$"]> [/EMAIL][EMAIL="scott@Ubuntu:~$"]scott@Ubuntu:~$[/EMAIL][EMAIL="scott@Ubuntu:~$"] tail -f /var/log/messages
Apr 16 19:35:12 localhost gconfd (scott-9897): Resolved address "xml:readwrite:/home/scott/.gconf" to a writable configuration source at position 2
Apr 16 19:35:12 localhost gconfd (scott-9897): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 3
Apr 16 19:35:12 localhost gconfd (scott-9897): Resolved address "xml:readonly:/usr/share/gconf/local.defaults" to a read-only configuration source at position 4Apr 16 19:35:12 localhost gconfd (scott-9897): Resolved address "xml:readonly:/usr/share/gconf/cdd.defaults" to a read-only configuration source at position 5
Apr 16 19:35:12 localhost gconfd (scott-9897): Resolved address "xml:readonly:/usr/share/gconf/debian.defaults" to a read-only configuration source at position 6
Apr 16 19:35:12 localhost gconfd (scott-9897): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 7
Apr 16 19:35:19 localhost gconfd (scott-9897): Resolved address "xml:readwrite:/home/scott/.gconf" to a writable configuration source at position 0
Apr 16 19:35:39 localhost kernel: [4294810.707000] usb 5-2.2: new high speed USB device using ehci_hcd and address 8[/EMAIL]
 
 (I changed the etc/network/interfaces to what you said to [changing the essid and key] but still nothing happened.)

---

### Post by az on 2006-04-17
[QUOTE=Mr_Welfare]Here is the output.
 Apr 16 19:35:39 localhost kernel: [4294810.707000] usb 5-2.2: new high speed USB device using ehci_hcd and address 8[/QUOTE]

That's it?

If you wait a few seconds is there more?  Because ubuntu is not seeing your device as anything it knows about.  Exactly what kind of device is it?

Also there is a new linux-wlan-ng package in Dapper:
[http://packages.ubuntu.com/dapper/admin/linux-wlan-ng-firmware](http://packages.ubuntu.com/dapper/admin/linux-wlan-ng-firmware)
"This package doesn't contain the firmware files, but a script to download the upstream source tarball and build a deb that contains them. Note that only some adapters really need a firmware file and that firmware files are not completely free (in the sense of freely redistributable), that's why this package exists."

Perhaps your card needs firmware?  I am not familiar with this.

---

### Post by az on 2006-04-17
[QUOTE=azz]
Also there is a new linux-wlan-ng package in Dapper:
[http://packages.ubuntu.com/dapper/admin/linux-wlan-ng-firmware](http://packages.ubuntu.com/dapper/admin/linux-wlan-ng-firmware)[/QUOTE]


I just installed it and read the documentation:
    These firmware files are not freely redistributable (or at least it is not
    sure if they are). The upstream authors of the driver put these firmware
    in the sources of the driver, but they are removed from the Debian source
    tarball due to these license problems.

If you are running breezy, nevermind - you already have the firmware you need.  In Dapper, I don't need the firmware to run the device.  I think that this is the case for most devices.

---

### Post by Mr_Welfare on 2006-04-17
[quote=azz]That's it?
 
If you wait a few seconds is there more? Because ubuntu is not seeing your device as anything it knows about. Exactly what kind of device is it? [/quote]
 
I haven't tried waiting for a few seconds, but if there was more, I think it would have displayed in the time it tooke me to copy and paste. Myabe not though... I'll give it a try and see. My device is a D-Link DWL-G122 Ver. A2.

---

### Post by Mr_Welfare on 2006-04-17
[quote=Mr_Welfare]I haven't tried waiting for a few seconds, but if there was more, I think it would have displayed in the time it tooke me to copy and paste. Myabe not though... I'll give it a try and see.[/quote]
 
No, there isn't any more output. I waited for a full minute just to be sure, but there wasn't anything more.

---

### Post by az on 2006-04-17
[QUOTE=Mr_Welfare]My device is a D-Link DWL-G122 Ver. A2.[/QUOTE]


Ah!  A G122 is not a DWL-122.  You have a G device.  Completely different chipset, and so the advice on this thread will not work for you.

Delete your /etc/network/interfaces wlan0 stanza and reenable the ndiswrapper driver (make sure you have the latest one).  

Then go back to the networking tool and try to configure your wireless.

Your device is a prism54 device.  Can you try the latest Dapper live cd to see if the linux native driver works - it should.

---

### Post by heislord5 on 2006-04-19
AZZ,

I reinstalled ubuntu DVD 5.10 version.  Then I installed the  linux-wlan-ng package.  Then I changed the interfaces file and my internet was up and running quickly.  Well, then it had updates...like 60 files.  Anyway, when the updates were done, I couldn't get internet working anymore.  Also, I couldn't reinstall linux-wlan-ng package, because it was trying to update it from the internet....which I don't have.  Any suggestions?  I've got the long pause on bootup again, lol.
Device doesn't show up in networking gui at all, and in past experience it shows up there when it is working (even though you have to configure it manually).

---

### Post by az on 2006-04-19
I can't think of a reason why it did that.  I don't think linux-wlan-ng is updated, so the version on the cd/dvd should still be current, or at least still work.

---

### Post by heislord5 on 2006-04-19
Well,

I had updated the stuff and deleted the CD-ROM repository in the repositories....I've reinstalled again and installed linux_ng_wlan and added the lines in my interfaces...once again it worked like a charm.  Now I'm going through those updates again.  This time I'll still have the CD-Rom repositories and hopefully I'll just have to reinstall the linux_ng_wlan package.  I see one of the packages being updated is the dhcp one.  When I know...I'll update this message, Lord willing.

---

### Post by Mr_Welfare on 2006-04-20
[quote=azz]Ah! A G122 is not a DWL-122. You have a G device. Completely different chipset, and so the advice on this thread will not work for you.
 
Delete your /etc/network/interfaces wlan0 stanza and reenable the ndiswrapper driver (make sure you have the latest one). 
 
Then go back to the networking tool and try to configure your wireless.
 
Your device is a prism54 device. Can you try the latest Dapper live cd to see if the linux native driver works - it should.[/quote]
 
I have reinstalled the ndiswrapper drivers (using PRISMA02.inf and PRISMA02.sys found on the CD that came with the adapter) and have deleted the /etc/network/interfaces wlan0 stanza, but still nothing happens. I have tried downloading the latest drivers from D-Link, but whenever I install them, ndiswrapper says that no hardware can be found. I'm sticking with the CD drivers for now. The strange thing too is that the network settings box says that wlan0 is enabled and active. Only I still can't get an internet or network connction unless I remove the WEP encryption. Is there anything else that might be going wrong here??
 
Mr_Welfare
 
Note: I have also uninstalled the linux-wlan-ng package from the packag manager if it makes a difference.

---

