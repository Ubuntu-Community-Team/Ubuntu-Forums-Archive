---
title: "wireless card help in Dapper"
date: 2006-05-15
forum: Hardware &amp; Laptops
---

### Post by dspring on 2006-05-15
I have Dapper currentlly running on my HP/Compaq NX 9600 :-? laptop, FANTASTIC system, I am impressed!! No problem with ethernet but would like to get my wireless card to come on for more freedom and so I can use in my shop where there is no ethernet. It has the broadcom card and is currently showing hardware and driver present but the light won't come on so I have to assume it is not on. 1, how do I get it to come on with terminal or other, I have tried the GUI but looks like something else needs to be done first. Is Dapper ready for this or is it incomplete or broken yet in this area? Hoping someone with similar card or system can help me to get it working, I tried with Breezy earlier but with all the info could never get to work...I know the light will come on as it did once with Vector Linux, I'm back to Ubuntu because I like Gnome better and Breezy was better than the others so this time around I decided since it was not yet to be my main system I'd go with the latest... glad I did. Anyway, HELP! Thanks all help greatly appreciated!

David

---

### Post by roachk71 on 2006-05-16
First, if you're using NDISwrapper, you have to bring up the card's Windows driver  by running modprobe:

```
 sudo modprobe ndiswrapper
```
in a terminal window.

And you also have to configure device wlan0 in your network properties (under System-->Administration). Be sure to tell this dialog everything about your wireless network (SSID, WEP key, DNS servers, etc.) Then click Activate to bring it up.

Once all of this is done, you may have to open /etc/modules and insert modprobe after the first two or three entries, so that the driver gets loaded early in the boot sequence.

```
sudo gedit /etc/modules
```

This second step is necessary, since the module may not load by default at boot. 8)

You probably will have to reboot for the card to work correctly, as well.

Oh, and I should mention that some cards won't show lights, but usually work anyway.

---

### Post by dspring on 2006-05-16
Thanks, I'll try this later today and let you know how it works.

David

---

### Post by GraemeF on 2006-05-16
[QUOTE=roachk71]First, if you're using NDISwrapper, you have to bring up the card's Windows driver  by running modprobe:

```
 sudo modprobe ndiswrapper
```
in a terminal window.[/QUOTE]
This [always hangs with status D+]("http://ubuntuforums.org/showthread.php?t=177063") (according to ps) for me. :(

---

### Post by dspring on 2006-05-16
yes, did that. and then should it show something in the terminal? I did everything roachk71 said to try. 

David

---

### Post by roachk71 on 2006-05-18
[quote=GraemeF]This [always hangs with status D+]("http://ubuntuforums.org/showthread.php?t=177063") (according to ps) for me. :([/quote] 
Have you used ndiswrapper -i to install your Windows wireless driver? You'll need the original CD that came with the card, or a download of the driver archive from the manufacturer.
```
ndiswrapper -i /media/cdrom/path-to-{driver-name}.inf
``` 
Oh, and dspring, after a reboot, try pinging your network's IP address with the wired ethernet port disabled.

And I had forgotten to mention that ndiswrapper's usefulness also sometimes depends on your hardware configuration, sadly.

---

### Post by dspring on 2006-05-23
[QUOTE=roachk71]Have you used ndiswrapper -i to install your Windows wireless driver? You'll need the original CD that came with the card, or a download of the driver archive from the manufacturer.
```
ndiswrapper -i /media/cdrom/path-to-{driver-name}.inf
``` 
Oh, and dspring, after a reboot, try pinging your network's IP address with the wired ethernet port disabled.

And I had forgotten to mention that ndiswrapper's usefulness also sometimes depends on your hardware configuration, sadly.[/QUOTE]

Is there anything else I can try?

-l turns up that the driver is installed and present as well as the hardware
and    -m modprobe config already  contains alias directive.

---

### Post by dotdot on 2006-05-23
my whole laptop hangs .... when i try to get my network enabled.
sudo modprobe ndiswrapper  - finds the card
then go into networking - then enable the card.
..then it hangs the whole laptop - everytime.

all was ok in 5.10 - now .. i'm stuffed.

anyone else have any ideas on this pretty significant problem.

..

---

### Post by GraemeF on 2006-05-23
Yes, I've tried using the drivers from my CD as well as several different versions I downloaded. No joy.

I've now given up with my wireless card and I've run a wire to the PC, much to my wife's dismay ;)

Thanks anyway... G.

---

### Post by ingo on 2006-05-23
Hi Graeme,

don't dispair yet!!! If Ubuntu recognises your card but doesn't get an IP address there is a very simple way of doing things without ndiswrapper. I'll stick my post below this one. If you've got any questions, feel free :)

---

### Post by ingo on 2006-05-23
Hi there,

there is no need to install ndiswrapper as long as Ubuntu recognises your card. All you have to do is:

1. find out what your card is called by typing 
_sudo iwconfig_
It will probably be wlan0 or somehting like that
2. type
_sudo ifdown wlan0_ (or whatever your card is called)
3. type
_sudo iwconfig wlan0_ (or whatever your card is called) essid "YOUR NETWORK NAME" key s:YOUR WEP KEY PHRASE
4. type
_sudo ifup wlan0_ (or whatever your card is called)

Right, that should do it. 

And in case you're fed up with sudo type

_sudo bash_

at the start and then you've got a root shell.

Finally, it might be a good idea to write a simple script for this, as you'll probably get fed up typing all that lot every time you want to get into your network. Here is how:

get into the root shell (see above) and change into /usr/local/bin. Type

_touch mynetwork_ (or the name of your network or a nice short name you remember easily)

Now open the file /usr/local/bin/mynetwork with your favourite editor (I use vi, but nano is very user friendly...) and type the following:

#!/bin/bash
#my network

ifdown wlan0
iwconfig wlan0 essid "YOUR NETWORK NAME" key s:YOUR WEP KEY PHRASE
ifup wlan0

#end

Save it and Bob's your uncle. Now every time you want to log into your network just type 

sudo sh mynetwork

and you're in.

You might want to do write other scripts for other networks. If in doubt check the man pages for iwconfig (man iwconfig)

HTH 

Ingo

---

### Post by GraemeF on 2006-05-23
Hehe - I appreciate your enthusiasm :)
I've spent just as long trying to get the bcm-whatever driver working as I have ndiswrapper (it hangs just the same), but if there's another way then I'm willing to give it a try!

---

### Post by jml on 2006-05-24
First question, when you go into the Network MAnager do you see the wireless card listed as a connection option?  If yes, then first disable the wired connection, configure the wireless connection and then activate it.  Then see if you can connect.  I have an HP NX6110 and was having trouble getting wireless to work until I realized that I accidentally turned off the card by pushing the "antenna" button.  In Linux the blue activity light does not come on right away, it only flashes when data is being either transmitted or recieved.

If you do not see the wireless card listed as an option, then you may have a bit of trouble.  I was never able to get the Broadcom Card to work with Ubuntu.  The only Distro I could get it to work with was Mandriva 2006.  So I bought a Cisco Aironet 802.11 a/b/g  card, disabled the internal wireless card and had very few problems connecting.  The only problem is that Ubuntu does not yet support WPA encryption out of the box.  Version 6.06 may, however.  

If you are still having problems, check out this link.  Its the Ubuntu Wireless Troubleshooting Guide.

[https://wiki.ubuntu.com/WirelessTroubleshootingGuide](https://wiki.ubuntu.com/WirelessTroubleshootingGuide)

Joe

---

### Post by GraemeF on 2006-05-24
No joy. I get as far as the card being recognised and detected by the driver ("hardware present") but modprobe always hangs, and nothing wireless is listed by iwconfig.

Believe me, I've tried out everything I could find here on the forums, the wiki, and other places on the 'net with no luck. modprobe always hangs. I posted hoping that someone else had experienced the same problem and had found a way to fix it - all the information I have found assumes that modprobe works.

Anyway, thanks for your help guys :)
At least I'm all sorted, albeit with wires ;)

---

### Post by dspring on 2006-05-24
[QUOTE=ingo]Hi there,

there is no need to install ndiswrapper as long as Ubuntu recognises your card. All you have to do is:

1. find out what your card is called by typing 
_sudo iwconfig_
It will probably be wlan0 or somehting like that
2. type
_sudo ifdown wlan0_ (or whatever your card is called)
3. type
_sudo iwconfig wlan0_ (or whatever your card is called) essid "YOUR NETWORK NAME" key s:YOUR WEP KEY PHRASE
4. type
_sudo ifup wlan0_ (or whatever your card is called)

Right, that should do it. 

And in case you're fed up with sudo type

_sudo bash_

at the start and then you've got a root shell.

Finally, it might be a good idea to write a simple script for this, as you'll probably get fed up typing all that lot every time you want to get into your network. Here is how:

get into the root shell (see above) and change into /usr/local/bin. Type

_touch mynetwork_ (or the name of your network or a nice short name you remember easily)

Now open the file /usr/local/bin/mynetwork with your favourite editor (I use vi, but nano is very user friendly...) and type the following:

#!/bin/bash
#my network

ifdown wlan0
iwconfig wlan0 essid "YOUR NETWORK NAME" key s:YOUR WEP KEY PHRASE
ifup wlan0

#end

Save it and Bob's your uncle. Now every time you want to log into your network just type 

sudo sh mynetwork

and you're in.

You might want to do write other scripts for other networks. If in doubt check the man pages for iwconfig (man iwconfig)

HTH 

Ingo[/QUOTE]

Ok here is what I got when doing this,

dspring@laptop:~$ sudo iwconfig
Password:
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

dspring@laptop:~$ sudo ifdown eth1
ifdown: interface eth1 not configured
dspring@laptop:~$ sudo ifconfig eth1 essid 2WIRE700 key 1777698029
essid: Host name lookup failure
ifconfig: `--help' gives usage information.
dspring@laptop:~$ sudo ifup eth1
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFFLAGS: No such file or directory
SIOCSIFFLAGS: No such file or directory
Listening on LPF/eth1/00:90:4b:a2:ad:a1
Sending on   LPF/eth1/00:90:4b:a2:ad:a1
Sending on   Socket/fallback
receive_packet failed on eth1: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 19
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 16
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 17
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 1
send_packet: Network is down
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
dspring@laptop:~$ sudo ifup eth1
ifup: interface eth1 already configured

Now I couldn't get it to work but it does see the broadcom 4306. 
Next I tried WiFi Radar and didn't work BUT some how it changed the Nickname of "Broadcom 4306" to the essid of "2WIRE700" ..... how can I change that nickname back? One thing though in the terminal where I discovered this had changed, it did show the freqency which it didn't before. I am concerned about that nickname change though.. I screwed that up least I think I did. What do you think I should do ? Here is what it shows now:
dspring@laptop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"2WIRE700"  Nickname:"2WIRE700"
          Mode:Managed  Frequency=2.417 GHz  Access Point: Invalid
          Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Encryption key:1777-6980-29   Security mode:open
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

dspring@laptop:~$

David

---

### Post by popkid on 2006-05-24
Hi... 

Try this...

[http://ubuntuforums.org/showpost.php?p=899926&postcount=24]("http://ubuntuforums.org/showpost.php?p=899926&postcount=24")

 it should work for you I think... you will need to blacklist ndiswrapper and use bcm43xx instead

Hope this helps,

pK

---

### Post by dspring on 2006-05-25
Hey, thanks for the links on the forum, I'm going to give this a try.
What year Corvette..68 or 69? Nice yellow! I had a 61 fuel injected, bought it in 1970 for 1900 usd from an older friend, had 32,000 miles on it. Fantastic car, never been beat, did 140 top end and 11.42 in quarter mile. Ok back to Ubuntu.
Thanks, I'll check back here and let you all know if I get it working.

David

---

### Post by popkid on 2006-05-25
No problem, hope the link helps you out.

The Vette is a 69 small block

My pride and joy!

Don't see many of them in the UK!

[http://www.corvetteclub.org.uk/album_pic.php?pic_id=424]("http://www.corvetteclub.org.uk/album_pic.php?pic_id=424")

Your 61 sounds pretty impressive, would be worth a fortune now!

pK

---

### Post by dspring on 2006-05-25
Hey, got it up to the point the light came on. Then I screwed up the eth1 now it doesn't show up in the networking interface. Got any idea how to get it back?

David

---

### Post by popkid on 2006-05-25
When you say "screwed up the eth1"

what did you do?

Did you get wireless access at all, or not that far?

pK

---

### Post by dspring on 2006-05-27
[QUOTE=popkid]When you say "screwed up the eth1"

what did you do?

Did you get wireless access at all, or not that far?

pK[/QUOTE]

Have not gotten access thus far, I did figure out how to get the eth1 back into the network settings gui, remove ndiswrapper, ndisgtk and broadcom drivers using synaptic. I then reinstalled and got it back. Only problem is this time I went with the firmware for broadcom. I have gotten more information returned via terminal and the cards light flickers, and lshw returns 3 access points but still cannot connect. When I reboot the eth1 disappears again and I can't get it back unless I start over... so I have decided not to use the broadcom firmware and go back to try ndiswrapper since I have learned a lot from this like using nano, gedit and terminal and editing files etc. So If ndiswrapper doesn't work soon I'm going to give up until one of these kernals work with this stuff. Thanks for the help guys!

---

