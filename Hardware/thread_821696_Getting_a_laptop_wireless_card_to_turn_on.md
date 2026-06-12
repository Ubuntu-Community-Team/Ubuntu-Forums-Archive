---
title: "Getting a laptop wireless card to turn on"
date: 2008-06-07
forum: Hardware
---

### Post by BlkMage on 2008-06-07
Just installed Ubuntu on my eMachines M6810 laptop. The built in wireless is turned on and off by holding the Function key and pressing F2, or at least that's the way it worked in Windows. Now, if I push those buttons the light below the keyboard for the wireless card doesn't come on and I can't connect to my home's wireless network. Is there a way that I can turn the card on in Linux or should I just buy a new card?

EDIT: And before anyone says it, I checked in iwconfig and Ubuntu knows it's there, so I figure the drivers are good.

---

### Post by duchovny on 2008-06-07
Is there suppose to be a light that indicates the wireless is on when you are in Windows? If so and you don't see a light in ubuntu I would check and see if the wireless works anyway. My Lenovo has a wireless switch and in Windows if the switch is in the "on" position I get a wireless light, but I've noticed when I'm in ubuntu and the wireless is in the "on" position I have no light at all, but the wireless works nonetheless.

---

### Post by BlkMage on 2008-06-07
> **duchovny said:**
> Is there suppose to be a light that indicates the wireless is on when you are in Windows? If so and you don't see a light in ubuntu I would check and see if the wireless works anyway. My Lenovo has a wireless switch and in Windows if the switch is in the "on" position I get a wireless light, but I've noticed when I'm in ubuntu and the wireless is in the "on" position I have no light at all, but the wireless works nonetheless.

Yes, there's a light just below the keyboard that lights up when the wireless is on in Windows. And it doesn't seem to be working without it. I even went in and typed the name of the network and the key myself, sitting in better proximity to the router than anything else in the house that uses it, still nothing. However, if I go over and plug in a networking cable from the router to the laptop, everything works great.

---

### Post by HunterThomson on 2008-06-07
Your wireless chip set is from Broadcom... Right?

---

### Post by HunterThomson on 2008-06-07
> **BlkMage said:**
> Yes, there's a light just below the keyboard that lights up when the wireless is on in Windows. And it doesn't seem to be working without it. I even went in and typed the name of the network and the key myself, sitting in better proximity to the router than anything else in the house that uses it, still nothing. However, if I go over and plug in a networking cable from the router to the laptop, everything works great.

Key... WEP or WPA? And in the network manager GIU it shows the network?

---

### Post by BlkMage on 2008-06-07
> **HunterThomson said:**
> Key... WEP or WPA? And in the network manager GIU it shows the network?

WEP 128-bit. And it does not show up on it's own.

And I'm not sure who makes the chipset, laptop is a few years old and I'm not sure how to check that in Ubuntu.

---

### Post by HunterThomson on 2008-06-07
> **BlkMage said:**
> WEP 128-bit. And it does not show up on it's own.

And I'm not sure who makes the chipset, laptop is a few years old and I'm not sure how to check that in Ubuntu.

I have not herd anyone having any problems with WEP. 

I have googled and found simpler laptops made by eMachines and they use Broadcom Wireless chipsets. It seems computer manufacturers use the same cipsest in all there computers i.e. HP broadcom, ASUS Atheros, Lenovo/IBM intel.... Go to system/administration or it mite be in administration and look for the Restricted drivers GUI and see if anything is in there.

---

### Post by BlkMage on 2008-06-07
> **HunterThomson said:**
> I have not herd anyone having any problems with WEP. 

I have googled and found simpler laptops made by eMachines and they use Broadcom Wireless chipsets. It seems computer manufacturers use the same cipsest in all there computers i.e. HP broadcom, ASUS Atheros, Lenovo/IBM intel.... Go to system/administration or it mite be in administration and look for the Restricted drivers GUI and see if anything is in there.

Do you mean go into Hardware and check the list of proprietary drivers? If so, the only thing there is my ATI video card, which I intend to fix as soon as I can get it online.

---

### Post by HunterThomson on 2008-06-07
> **BlkMage said:**
> Do you mean go into Hardware and check the list of proprietary drivers? If so, the only thing there is my ATI video card, which I intend to fix as soon as I can get it online.

OK, ya I am 7.10 not 8.04 and the location has changed. That is what I meant.

I am going to do a bit more googling to make sure you have broadcom wireless. And how to set up the broadcom...

If anyone with more knowledge on this can help pleas do:)

---

### Post by HunterThomson on 2008-06-07
OK I am moving along....

You do in fact have Broadcom:

broadcom 4306 chip

I am now reading how to set up the ndiswrapper.....

[http://ubuntuforums.org/archive/index.php/t-144403.html](http://ubuntuforums.org/archive/index.php/t-144403.html)

---

### Post by BlkMage on 2008-06-07
> **HunterThomson said:**
> OK I am moving along....

You do in fact have Broadcom:

broadcom 4306 chip

I am now reading how to set up the ndiswrapper.....

[http://ubuntuforums.org/archive/index.php/t-144403.html](http://ubuntuforums.org/archive/index.php/t-144403.html)

I was reading that myself, if I'm reading this correct, what I have to do is get the ndiswrapper driver, then type "sudo modprobe ndiswrapper -m" so that it will turn on and every time I boot the computer it will auto turn on for me.

This is my first day actually working with any kind of Linux. Did I get that right? And my next question would be where I get those drivers from.

---

### Post by HunterThomson on 2008-06-07
This it taking me a bit longer because I am also watching:

Manufacturing Consent

[http://isohunt.com/download/21025932/Manufacturing+Consent.torrent](http://isohunt.com/download/21025932/Manufacturing+Consent.torrent)

We have to get you online so you can download it:)

---

### Post by HunterThomson on 2008-06-07
> **BlkMage said:**
> I was reading that myself, if I'm reading this correct, what I have to do is get the ndiswrapper driver, then type "sudo modprobe ndiswrapper -m" so that it will turn on and every time I boot the computer it will auto turn on for me.

This is my first day actually working with any kind of Linux. Did I get that right? And my next question would be where I get those drivers from.

Yes that is what you need to type after you install the drivers...

I'll check...

---

### Post by HunterThomson on 2008-06-07
[http://www.wireless-driver.com/download/broadcom/Broadcom-4306-driver-download.htm](http://www.wireless-driver.com/download/broadcom/Broadcom-4306-driver-download.htm)

There are your divers that you need to download.

---

### Post by HunterThomson on 2008-06-07
First you will need to blacklist the drive that Ubuntu installed.
you will need to open shell and type:

sudo nano /etc/modprobe.d/blacklist

then add:

bcm43xx

at the end of the file then holed Ctrl and press X. Then Y to save the changes.

---

### Post by HunterThomson on 2008-06-07
Open that driver file I gave you a line to download and find:

bcmwl5.inf

and drag it to the desktop

---

### Post by HunterThomson on 2008-06-07
Now open a shell and type:

sudo apt-get update
sudo apt-get install build-essential

then:

sudo apt-get install linux-headers-`uname -r`
sudo ln -s /usr/src/linux-`uname -r` /lib/modules/`uname -r`/build

---

### Post by HunterThomson on 2008-06-07
Well maybe you didn't need to do the last step but you need that stuff anyway for other things:)

Now, open synaptic package manager and search for ndiswrapper the you should see three thing... check all three boxes and click apply..

---

### Post by HunterThomson on 2008-06-07
OK,
Now click "Places" in the taskbar and open the "Home" folder then right click and "Make New File" Name it bcm4311.... Then open the new file and drag the bcmwl5.inf file to it..... WEll open the driver folder you downloaded again and look for "bcmwl5.sys" file and drag it to that "New File" you named "bcm4311" also.

---

### Post by HunterThomson on 2008-06-07
Still with me?


Now open a shell and type:

cd bcm4311

then:

sudo ndiswrapper -i bcmwl5.inf

the output should look like this with NO Errors:

installing bcmwl5 ...
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2

Did it do that? Any problems so far?

---

### Post by BlkMage on 2008-06-07
> **HunterThomson said:**
> Still with me?


Now open a shell and type:

cd bcm4311

then:

sudo ndiswrapper -i bcmwl5.inf

the output should look like this with NO Errors:

installing bcmwl5 ...
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2

Did it do that? Any problems so far?

Sorry, been jumping between here and yardwork, but I have all of your posts in a .txt file along with the drivers on a thumbdrive, moving over to try this now.

---

### Post by HunterThomson on 2008-06-07
OK,
I will wait to hear your progress I don't what to post more instructions if I made a mistake and need to have you do something ells

---

### Post by BlkMage on 2008-06-07
...and I'm already getting a problem. The file you sent me to download doesn't have that file inside it. All I'm getting is a bunch of "bcm1xsup.dll" files. "bcmwl5.inf" is not there.

EDIT: However, I found the file on my own, will try it.

---

### Post by HunterThomson on 2008-06-07
> **BlkMage said:**
> ...and I'm already getting a problem. The file you sent me to download doesn't have that file inside it. All I'm getting is a bunch of "bcm1xsup.dll" files. "bcmwl5.inf" is not there.

EDIT: However, I found the file on my own, will try it.

I downloaded it and it is in there look agin

---

### Post by BlkMage on 2008-06-07
Got both files and got to the point you left off. There were a few less lines of "forcing parameter" stuff than you listed, but no errors. What now?

---

### Post by HunterThomson on 2008-06-07
pic

---

### Post by HunterThomson on 2008-06-07
> **BlkMage said:**
> Got both files and got to the point you left off. There were a few less lines of "forcing parameter" stuff than you listed, but no errors. What now?


OK good:)

One sec

---

### Post by BlkMage on 2008-06-07
> **HunterThomson said:**
> pic

Either way, I got both files and things have been taken care of. Next step?

---

### Post by HunterThomson on 2008-06-07
Now run this just to make sure it installed correctly;

ndiswrapper -l

it should say something like this:

installed drivers:
bcmwl5          driver installed, hardware (14E4:4324) present (alternate driver: bcm43xx)

---

### Post by BlkMage on 2008-06-07
> **HunterThomson said:**
> Now run this just to make sure it installed correctly;

ndiswrapper -l

it should say something like this:

installed drivers:
bcmwl5          driver installed, hardware (14E4:4324) present (alternate driver: bcm43xx)

bcmwl5 : driver installed
	device (14E4:4320) present (alternate driver: ssb)

There's my output. Will this work?

---

### Post by HunterThomson on 2008-06-07
> **BlkMage said:**
> bcmwl5 : driver installed
	device (14E4:4320) present (alternate driver: ssb)

There's my output. Will this work?

Yes that looks good it recognises your device "device (14E4:4320) present"

Now type this in the shell and cut and past the output for me to read:

iwconfig

---

### Post by BlkMage on 2008-06-07
> **HunterThomson said:**
> Yes that looks good it recognises your device "device (14E4:4320) present"

Now type this in the shell and cut and past the output for me to read:

iwconfig

james@Asuka:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"Geary"  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by HunterThomson on 2008-06-07
> **BlkMage said:**
> james@Asuka:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"Geary"  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Good good one sec

---

### Post by HunterThomson on 2008-06-07
in the shell type:

ifconfig wlan0 up

and the run:

iwconfig

and post the output one more time

---

### Post by BlkMage on 2008-06-07
> **HunterThomson said:**
> in the shell type:

ifconfig wlan0 up

and the run:

iwconfig

and post the output one more time

When I try the "ifconfig wlan0 up" part, it gives me

SIOCSIFFLAGS: Permission denied

???

---

### Post by HunterThomson on 2008-06-07
Forget that command anyway I am glad it didn't work:) I was just going to tell you not to do it:)

type this in the shell:

modprobe ndiswrapper

Then type this:

ndiswrapper -m

---

### Post by BlkMage on 2008-06-07
> **HunterThomson said:**
> Forget that command anyway I am glad it didn't work:) I was just going to tell you not to do it:)

type this in the shell:

modprobe ndiswrapper

Then type this:

ndiswrapper -m

Once again, that first step is a doozie. That modprobe command gives me

FATAL: Error inserting ndiswrapper (/lib/modules/2.6.24-16-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko): Operation not permitted

---

### Post by HunterThomson on 2008-06-07
> **BlkMage said:**
> Once again, that first step is a doozie. That modprobe command gives me

FATAL: Error inserting ndiswrapper (/lib/modules/2.6.24-16-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko): Operation not permitted

OK try this:

sudo modprobe ndiswrapper

---

### Post by BlkMage on 2008-06-07
> **HunterThomson said:**
> OK try this:

sudo modprobe ndiswrapper

Did the sudo modprobe, it went to the next line without saying anything.
Figured I'd try the original modprobe command, same thing happened.
THEN, when I tried with th -m I got this:

adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper ...
sh: cannot create /etc/modprobe.d/ndiswrapper: Permission denied
couldn't add module alias:  at /usr/sbin/ndiswrapper-1.9 line 882.

---

### Post by HunterThomson on 2008-06-07
> **BlkMage said:**
> Did the sudo modprobe, it went to the next line without saying anything.
Figured I'd try the original modprobe command, same thing happened.
THEN, when I tried with th -m I got this:

adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper ...
sh: cannot create /etc/modprobe.d/ndiswrapper: Permission denied
couldn't add module alias:  at /usr/sbin/ndiswrapper-1.9 line 882.

if you typed:

sudo modprobe ndiswrapper

and it didn't say anything then it worked:)

then run:

sudo ndiswrapper -m

this will probaly not sat anything ether

---

### Post by HunterThomson on 2008-06-07
What is up now did all go through with out error?

---

### Post by BlkMage on 2008-06-07
> **HunterThomson said:**
> if you typed:

sudo modprobe ndiswrapper

and it didn't say anything then it worked:)

then run:

sudo ndiswrapper -m

this will probaly not sat anything ether

When I did sudo ndiswrapper -m, it asked for my password then did this:

adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper ...

************************************************************************
*
* The update-modules command is deprecated and should not be used!
*
************************************************************************

---

### Post by HunterThomson on 2008-06-07
> **BlkMage said:**
> When I did sudo ndiswrapper -m, it asked for my password then did this:

adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper ...

************************************************************************
*
* The update-modules command is deprecated and should not be used!
*
************************************************************************

I think that it worked and is telling you not to use the update-modules because they will brake the driver you installed....

now click on the networkmanager icon on the task bar.... Dose it say anything about your wireless card or wireless connections???

---

### Post by BlkMage on 2008-06-07
> **HunterThomson said:**
> I think that it worked and is telling you not to use the update-modules because they will brake the driver you installed....

now click on the networkmanager icon on the task bar.... Dose it say anything about your wireless card or wireless connections???

It says the name is "wlan0:avahi" and the status is Disconnected.

---

### Post by HunterThomson on 2008-06-07
> **BlkMage said:**
> It says the name is "wlan0:avahi" and the status is Disconnected.

restart you computer

---

### Post by BlkMage on 2008-06-07
> **HunterThomson said:**
> restart you computer

Still not working.

EDIT: But the light is on.

---

### Post by dinub1 on 2008-06-07
> **BlkMage said:**
> Just installed Ubuntu on my eMachines M6810 laptop. The built in wireless is turned on and off by holding the Function key and pressing F2, or at least that's the way it worked in Windows. Now, if I push those buttons the light below the keyboard for the wireless card doesn't come on and I can't connect to my home's wireless network. Is there a way that I can turn the card on in Linux or should I just buy a new card?

EDIT: And before anyone says it, I checked in iwconfig and Ubuntu knows it's there, so I figure the drivers are good.

I do not know about your laptop technicalities. However light on or off you can always check if your wireless adapter is on or off.

The simplest way would be to install and use knetworkmanager. Its a fairily simple and intuitive utility that it auto detects your wireless card hardware, will also autodetect nearby wireless networks. Then you could connect to your own network. 
You can try typing in a terminal:

$ iwconfig

See what you get. If there is a driver installed for your card then program will report its status.... 
If knetworkamager does not report a wireless network available, but only a wired connection (if you have one) that would mean that you may need to manually install a driver for your card, if Linux supports it. If not you will need to install a Windows driver with Ndiswrapper.
Do experiment with the things and tell us what you get. We can go from there further.

---

### Post by HunterThomson on 2008-06-07
Type this in the shell:

sudo ifconfig wlan0 up

Then type:

ifconfig -a

and post the info

---

### Post by BlkMage on 2008-06-07
> **HunterThomson said:**
> Type this in the shell:

sudo ifconfig wlan0 up

Then type:

ifconfig -a

and post the info

james@Asuka:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:03:25:13:27:9c  
          inet addr:192.168.2.105  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::203:25ff:fe13:279c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6639 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5650 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6521475 (6.2 MB)  TX bytes:770322 (752.2 KB)
          Interrupt:23 Base address:0x4c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1991 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1991 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:99988 (97.6 KB)  TX bytes:99988 (97.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:90:4b:86:5b:de  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0:avahi Link encap:Ethernet  HWaddr 00:90:4b:86:5b:de  
          inet addr:169.254.8.123  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

wmaster0  Link encap:UNSPEC  HWaddr 00-90-4B-86-5B-DE-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

And if you will excuse me, I have a party to attend. I'll check back on this later tonight. And if I don't get the chance later, thanks for the help, at least it's trying something.

---

### Post by HunterThomson on 2008-06-07
> **BlkMage said:**
> james@Asuka:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:03:25:13:27:9c  
          inet addr:192.168.2.105  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::203:25ff:fe13:279c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6639 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5650 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6521475 (6.2 MB)  TX bytes:770322 (752.2 KB)
          Interrupt:23 Base address:0x4c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1991 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1991 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:99988 (97.6 KB)  TX bytes:99988 (97.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:90:4b:86:5b:de  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0:avahi Link encap:Ethernet  HWaddr 00:90:4b:86:5b:de  
          inet addr:169.254.8.123  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

wmaster0  Link encap:UNSPEC  HWaddr 00-90-4B-86-5B-DE-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

And if you will excuse me, I have a party to attend. I'll check back on this later tonight. And if I don't get the chance later, thanks for the help, at least it's trying something.

Well i think it is working now try and look in the network manager agin

---

### Post by HunterThomson on 2008-06-07
If not there are just a cupel more steps we can do it tomorrow. I'll be online all day but keep in mind I am in Hawaii

---

### Post by TroyDowling on 2008-06-07
I have an HP Pavilion DV9013ca which has a similar card; using the BCM43xx chipset. I had to work very hard to get this to work with hardy... here's how I managed to get it working in the end (Which is actually very easy, I just didn't know the tools existed).

1) Install the firmware extractor
```
sudo apt-get install b43-fwcutter
```

2) Run that program and follow the directions.

The reason that Broadcom cards don't work right away is because they run a proprietary firmware that Broadcom holds very secret. The driver has been reverse engineered to work with the newest Ubuntu, but you still need the firmware. After you run that, you *may* need to go into the "System > Administration > Hardware Drivers" and make sure the firmware box is checked off.

Tell me if this works for you. And welcome the the Ubuntu Newbies club! :p

---

### Post by HunterThomson on 2008-06-07
> **TroyDowling said:**
> I have an HP Pavilion DV9013ca which has a similar card; using the BCM43xx chipset. I had to work very hard to get this to work with hardy... here's how I managed to get it working in the end (Which is actually very easy, I just didn't know the tools existed).

1) Install the firmware extractor
```
sudo apt-get install b43-fwcutter
```

2) Run that program and follow the directions.

The reason that Broadcom cards don't work right away is because they run a proprietary firmware that Broadcom holds very secret. The driver has been reverse engineered to work with the newest Ubuntu, but you still need the firmware. After you run that, you *may* need to go into the "System > Administration > Hardware Drivers" and make sure the firmware box is checked off.

Tell me if this works for you. And welcome the the Ubuntu Newbies club! :p

Dose this use the ndiswrapper ? Or dose this use the free driver?

---

### Post by HunterThomson on 2008-06-07
I am pritty sure he just needs to edit:

/etc/modprobe.d/ndiswrapper

And comment out some stuff in:

/etc/network/interfaces


All has been going as it should. But I'll look into the thing your talking about....:-k

---

### Post by TroyDowling on 2008-06-07
My method uses the new Ubuntu-supported driver, b43. b43 took the place of the older bcm43xx driver that is now deprecated. It does not use NDISWrapper, which in my opinion is a quick and dirty fix for driver issues. I'm sure there are other ways to get his wireless card to work, I'm just posting the way that worked for me since it was so easy.

Type this in to see if your kernel is using the b43 driver:
```
sudo dmesg | grep b43
```

It looks like this for me:
```
[   46.994743] b43-phy0: Broadcom 4311 WLAN found
[   60.087744] input: b43-phy0 as /devices/virtual/input/input12
[   61.104832] Registered led device: b43-phy0:tx
[   61.105029] Registered led device: b43-phy0:rx
[   61.105171] Registered led device: b43-phy0:radio

```

---

### Post by HunterThomson on 2008-06-07
> **TroyDowling said:**
> I have an HP Pavilion DV9013ca which has a similar card; using the BCM43xx chipset. I had to work very hard to get this to work with hardy... here's how I managed to get it working in the end (Which is actually very easy, I just didn't know the tools existed).

1) Install the firmware extractor
```
sudo apt-get install b43-fwcutter
```

2) Run that program and follow the directions.

The reason that Broadcom cards don't work right away is because they run a proprietary firmware that Broadcom holds very secret. The driver has been reverse engineered to work with the newest Ubuntu, but you still need the firmware. After you run that, you *may* need to go into the "System > Administration > Hardware Drivers" and make sure the firmware box is checked off.b43-fwcutter[/code]

Tell me if this works for you. And welcome the the Ubuntu Newbies club! :p

:guitar::guitar:

WOW, that is the best driver I have ever herd of for Broadcom!!!

I spent all this time learning how to install and run ndiswrapper....
Arg... Well, I guess we will leave the desition up to BlkMage to continue with the last few steps of setting up the ndiswrapper or to remove it and install that driver.

Pros for using the ndiswrapper---

1- we spent all this time and it is almost up and running

2-??????

Pros for using the b43-fwcutter----

# Station mode
# Mesh networking mode
# Access Point mode (not quite yet, blocked by proper support in mac80211 and hostapd)
# Ad-Hoc (IBSS) mode
# Monitor and Promisc mode.
# "Monitor while operating" and multiple monitor interfaces.
# In-Hardware traffic de/encryption (relieves your CPU).
# LEDs to signal card state and traffic.
# In-Hardware MAC address filter.
# Packet injection (with radiotap; no FCS injection currently though hardware supports it - a radiotap flag is being discussed for this)

Cons for useing b43-fwcutter----

A whole new install from the strat

---

### Post by TroyDowling on 2008-06-07
Haha, yeah, b43 is pretty cool. I'd suggest the original poster starts over as this method provides a more stable system. For new users, stable is ALWAYS better. Less headaches. But like you said, it's up to him!

Best of luck in which ever method you choose,
Troy,

---

### Post by HunterThomson on 2008-06-07
> **TroyDowling said:**
> Haha, yeah, b43 is pretty cool. I'd suggest the original poster starts over as this method provides a more stable system. For new users, stable is ALWAYS better. Less headaches. But like you said, it's up to him!

Best of luck in which ever method you choose,
Troy,

Ya, he should use that b43... Ndiswrapper is strange and not preferable if there is a native linux driver available. That can do all that and is stable.

---

### Post by Ayuthia on 2008-06-08
Just to add to the mix, there are a few more steps that are needed for NDISwrapper to work with the Broadcom card.  As was just recently posted, the b43-fwcutter is for the b43 driver.  This is the new driver that replaces the bcm43xx driver.  When you saw the ssb as the alternate driver, that is the driver that is most likely causing your problems with connecting.  It comes with the b43 driver and will prevent NDISwrapper from working.  To see if that is really the case you can try:
```
sudo modprobe -r b43 ssb ndiswrapper
sudo modprobe ndiswrapper
```
Hopefully that will get your connection up and running for this session.  If that works, all you need to do next is add this:
```
echo blacklist b43|sudo tee -a /etc/modprobe.d/blacklist
```
What this will do is block out the b43 driver from loading.  After you type this, you should see it reply with 'b43'.  What it is doing is adding 'blacklist b43' to the end of /etc/modprobe.d/blacklist.  It is just a fancy way of adding things to the end of a file without having to go in there and edit manually.

Now if you want to go the b43 route, you can do what TroyDowling posted (make sure that you have a working internet connection at the time and have it get the firmware for you.  You will also need to add the following:
```
echo blacklist ndiswrapper|sudo tee -a /etc/modprobe.d/blacklist
```This will prevent the NDISwrapper module from loading.  However, if you did my step above and blacklisted b43, you will need to remove that 'blacklist b43' line from /etc/modprobe.d/blacklist or else you will not have a driver load up for you.

---

### Post by BlkMage on 2008-06-08
> **HunterThomson said:**
> Ya, he should use that b43... Ndiswrapper is strange and not preferable if there is a native linux driver available. That can do all that and is stable.

Yea, I think I'll try that other method. But I'll have to write down that code and try tomorrow, I can't get to the router for the hardline with people sleeping. I'll blacklist the ndiswrapper then install the b43-fwcutter. If it works, I'll be back to give thanks, if not, I'll be back for more help.

---

### Post by Ayuthia on 2008-06-08
> **BlkMage said:**
> Yea, I think I'll try that other method. But I'll have to write down that code and try tomorrow, I can't get to the router for the hardline with people sleeping. I'll blacklist the ndiswrapper then install the b43-fwcutter. If it works, I'll be back to give thanks, if not, I'll be back for more help.
You might want to check out this [link]("http://ubuntuforums.org/showthread.php?t=779754").  It has a list of Broadcom cards that might not work with the b43 driver in Ubuntu.  You can check your wireless card by doing this in the Terminal:
```
lspci -nn|grep 14e4
```This will list your Broadcom card.  You can check your kernel version by typing this in the Terminal:
```
uname -r
```

---

### Post by BlkMage on 2008-06-08
Alright, I checked that link, my card is supported. I blacklisted the ndiswrapper and installed the b43-fwcutter. This gave me the 2 computers icon at the clock. When I put in the name of the network and WEP myself, it changed to a signal strength icon and seemed to be seeing the network. However, the signal strength was at zero, even though I'm about 2 feet from the router, and it didn't accept the WEP. A few times it would wait a few minutes before asking again, and now there is no network icon by my clock, it just vanished.

We must be getting close...

EDIT: And I just realized that I lost the little light that used to indicate when the wireless radio was on.

---

### Post by HunterThomson on 2008-06-08
> **BlkMage said:**
> Alright, I checked that link, my card is supported. I blacklisted the ndiswrapper and installed the b43-fwcutter. This gave me the 2 computers icon at the clock. When I put in the name of the network and WEP myself, it changed to a signal strength icon and seemed to be seeing the network. However, the signal strength was at zero, even though I'm about 2 feet from the router, and it didn't accept the WEP. A few times it would wait a few minutes before asking again, and now there is no network icon by my clock, it just vanished.

We must be getting close...

EDIT: And I just realized that I lost the little light that used to indicate when the wireless radio was on.

OK,

So you blacklisted the ndiswrapper driver...
you installed the b43fwcutter.... 

What have you done to set it up?

---

### Post by BlkMage on 2008-06-09
> **HunterThomson said:**
> OK,

So you blacklisted the ndiswrapper driver...
you installed the b43fwcutter.... 

What have you done to set it up?

After the install and blacklist, nothing. You have to remember how long I've been working with Ubuntu, I don't know many commands yet.

---

### Post by HunterThomson on 2008-06-09
Here are the instructions on how to get it working...

[http://www.linuxwireless.org/en/users/Drivers/b43](http://www.linuxwireless.org/en/users/Drivers/b43)

I can walk you through it if you want:)

---

### Post by HunterThomson on 2008-06-09
Well looks like you mite have alredy done that stuff the link I gave you tell you to do....

Mite need to trouble shoot and configure.

---

### Post by Ayuthia on 2008-06-09
> **BlkMage said:**
> Alright, I checked that link, my card is supported. I blacklisted the ndiswrapper and installed the b43-fwcutter. This gave me the 2 computers icon at the clock. When I put in the name of the network and WEP myself, it changed to a signal strength icon and seemed to be seeing the network. However, the signal strength was at zero, even though I'm about 2 feet from the router, and it didn't accept the WEP. A few times it would wait a few minutes before asking again, and now there is no network icon by my clock, it just vanished.

We must be getting close...

EDIT: And I just realized that I lost the little light that used to indicate when the wireless radio was on.
Does the light stay off after you reboot?  Can you post the results of the following from the Terminal:
```
lshw -C network
sudo iwlist scan
```
Don't worry about doing  lshw -C network as super-user.  It is not really needed for us right now.

---

### Post by BlkMage on 2008-06-10
> **Ayuthia said:**
> Does the light stay off after you reboot?  Can you post the results of the following from the Terminal:
```
lshw -C network
sudo iwlist scan
```
Don't worry about doing  lshw -C network as super-user.  It is not really needed for us right now.

Sorry about the late replies, 11 hour work day yesterday :(
Anyways, realized today I got the light back after rebooting. And here's the full results of those 2 commands:

james@Asuka:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: c
       bus info: pci@0000:00:0c.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 74
       serial: 00:03:25:13:27:9c
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=via-rhine driverversion=1.4.3 ip=192.168.2.105 latency=64 maxlatency=8 mingnt=3 module=via_rhine multicast=yes
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:86:5b:de
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
james@Asuka:~$ sudo iwlist scan
[sudo] password for james: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

james@Asuka:~$

---

### Post by Ayuthia on 2008-06-10
Let's make sure that there are no conflicting modules:
```
sudo modprobe -r b43 ssb bcm43xx ndiswrapper
sudo modprobe b43
sudo ifconfig wlan0 up
sudo iwlist scan
```

---

### Post by BlkMage on 2008-06-10
> **Ayuthia said:**
> Let's make sure that there are no conflicting modules:
```
sudo modprobe -r b43 ssb bcm43xx ndiswrapper
sudo modprobe b43
sudo ifconfig wlan0 up
sudo iwlist scan
```

james@Asuka:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

---

### Post by BlkMage on 2008-06-13
Ayuthia, you still listening? HunterThomson? Anybody?

---

### Post by FAJALOU on 2008-06-13
Hi and welcome to Ubuntu.  I am running a Netgear PCI card, and I used ndiswrapper to have it work.  Unfortunately, it kept giving out like yours did, so i installed wicd, and it has worked well ever since.  Just as a secondary thought, if the package that you're trying now doesn't work, I would definately try wicd.  But you have some good people working with you.  I would stick to the regimen and see if they say anything else before taking my advice...  Just a thought.

---

