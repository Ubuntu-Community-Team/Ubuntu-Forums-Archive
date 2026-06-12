---
title: "HP 530 + Hardy + Broadcom BCM4311 = impossible?"
date: 2008-08-31
forum: Hardware
---

### Post by Calmatory on 2008-08-31
I've been trying to figure this out for a great while now. This has literally caused me one sleepless night. :(

Don't redirect me to the HP 530 support thread. 
Don't redirect me to [here](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff).
Don't tell me to try 2b and/or compiling Ndiswrapper from source.
I've tried, read, tried more, experimented and tried even more with all the info i can obtain from that link and HP 530 thread. No success.

So, what is the problem? There is this wireless-button, which has blue led glowing when I install the driver with ndiswrapper. However, after I apply the hardy-fix, the led turns off. So basically when the device has the "ssb" module loaded, it "works", as in the led does glow, but right after I get the ndiswrapper module loaded, the whole device just "dies".

Possible causes? All I can think of is bad/wrong driver. However, I haven't found any other driver working either. I tried to search HP's site for XP driver, and I actually found one differing from the how-to mentioned above, but no luck with it either.

People have got it working in Gutsy. Actually I guess that Hardy is the problem.

I am just clueless. :(

---

### Post by Bucky Ball on 2008-08-31
**HP 530 + Hardy + Broadcom BCM4311 = impossible? NO - totally possible!!**

The b43 driver in hardy should take care of this problem without ndiswrapper. Ndiswrapper is a nightmare which I screwed around with for months in Gutsy. I then installed Hardy and things were up and running in 5 minutes.

If the blue light is glowing, why then are you running the ndiswrapper (which is making it stop)? If the blue light is running, then your wireless is working, probably just not configured to your router (or whatever access point you are using to connect).

Try (sounds like you might have already)

[B]System->Administration->Hardware Drivers.
[/B] 
In there, you should find the Broadcom b43 wireless driver. Is it ticked and in use? If it is, then it is conflicting with the ndiswrapper setup and you should try getting rid of the ndiswrapper set up.

If it isn't, tick that box and the rest (fingers crossed) should take care of itself. Worked for me.

Maybe start looking into the b43 driver and forget ndiswrapper. That method has been superceded. I would personally remove all reference and start again and see if it makes any difference. The one thing that has got me is that your blue light is coming on which is a positive sign and might just mean you have hit it already and ndiswrapper is just screwing things up. As I say, the config to your access point might be wrong (SSID and Wep security code correct?).

Open a terminal and type:

**sudo nano /etc/modprobe.d/blacklist**

You should find an entry in there that looks like this:

[B]# replaced by b43 and ssb.
blacklist bcm43xx[/B]

If the **blacklist bcm43xx** line is hashed out, remove the hash. The first part of this entry says it all - this driver has been replaced by b43 and ssb.

Hope this helps. Believe me, I know how frustrating the broadcom cards can be (which is part of the reason b43 was developed).

Good luck and welcome to the forums. :)

---

### Post by Calmatory on 2008-08-31
I did remove the ndiswrapper module and then removed ndiswrapper. Right now I am indeed using b43 diver, ticked and in use from Hardware Drivers. However, Network Manager still can't find the wireless network. I did completely remove any access filters from router, I am using it unsecured. I configured it exactly as the user manual said. 

What should happen if I press the wireless button? In Vista I remember that it tried to find networks.In Ubuntu, nothing happens. Oh, and the led is lit atm. :)

---

### Post by Bucky Ball on 2008-08-31
Sounds promising. Try:

**System->Administration->Network** (Not Network Tools)

Unlock and click on your wireless connection. Hit properties and fill in the details of your access point. Let me know how this goes.

Here's a little further info:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Hardy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Hardy)

[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

Oh, and in case you haven't got b43-fwcutter happening already, you may need to open a terminal and run this command:

**sudo apt-get install b43-fwcutter**

When you run this command it may ask you if you would like to install some other things. Agree and follow your nose. That should get things going (fingers crossed) and find your access point.

---

### Post by Calmatory on 2008-08-31
Hmm, I installed fwcutter and followed the guide in linuxwireless.org, still can't find AP's.

However, when I press the button, the wireless-led in my router blinks twice. only for once. If I press the button second time, nothing happens. 

I tried to manually configure the wireless network with no success, can't get the connection. When I try to "Connect to Other network", the wireless-led starts blinking again. Not much, but some 5 times in 3 seconds. Quite randomly. I guess that means that there is at least SOME kind of (primitive) connection between the laptop and the router.

I've read that the wireless-led in the laptop blinks when it connects/transfers data. So far I've never seen it doing so. :(

Edit: Actually the router randomly blinks the wireless-led now. Delay might be from 5 seconds to minutes, but it blinks it. Thus it might be that it doesn't necessarily blink it due to pressing the wireless-button in laptop.

---

### Post by Bucky Ball on 2008-08-31
Damn close. When you go to **System->Administration->Network Tools**, from the drop down menu, choose **wlan0** (not loopback). Is that showing 'enabled' and giving any signs of life? If so, the card is not the problem and you can concentrate on the router. The wireless light (blue glow) should be solid (they normally are) on the lappy, unless the hp 530 is a totally different setup.

I gotta hit the sack now, 1am over here. Will have more of a look around and think tomorrow. Let me know how you go. 

Found some other info on this page but is dated before hardy and b43 existed (so is using ndiswrapper). For a dell computer but you will notice 'britgamer' claims it worked a treat for their HP 530.

[http://ubuntuforums.org/showthread.php?t=650729](http://ubuntuforums.org/showthread.php?t=650729)

Good luck ... :)

---

### Post by David D. on 2008-08-31
I had this problem with the BCM4311 in my HP dv6100 series laptop.  After much searching and trial & error, I found a post which suggested the following, which solved the problem for me.

The fix was to remove and reinstall the B43 drivers.  In terminal:

sudo apt-get remove purge b43-fwcutter

sudo apt-get install b43-fwcutter

I do not remember who posted this originally, or I would give credit where credit is due.

---

### Post by Calmatory on 2008-08-31
No success. Last time I installed fwcutter there was no popup about writing the firmware. This time there was, and I applied to it. Thus the chip *should* be working, right? But it isn't. :|

---

### Post by IntuitiveNipple on 2008-08-31
Guys, check the log files!

**/var/log/kern.log** will give hardware/driver clues.

**/var/log/daemon.log** will give you *a lot* of NetworkManager reports.

---

### Post by Calmatory on 2008-08-31
This was obtained from /var/log/daemon.log. After I tried to "Connect to Other network" via nm-applet.

```
Sep  1 01:27:02 asdman-laptop NetworkManager: <info>  Activation (wlan0) started...
Sep  1 01:27:02 asdman-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Sep  1 01:27:02 asdman-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Sep  1 01:27:02 asdman-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Sep  1 01:27:02 asdman-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Sep  1 01:27:02 asdman-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Sep  1 01:27:02 asdman-laptop NetworkManager: <info>  Activation (wlan0/wireless): access point 'wlan' is unencrypted, no key needed.
Sep  1 01:27:04 asdman-laptop NetworkManager: <info>  retry to connect to global supplicant socket (try=1)
Sep  1 01:27:04 asdman-laptop NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD wlan0^I^Iwext^I/var/run/wpa_supplicant0^I'
Sep  1 01:27:04 asdman-laptop NetworkManager: <info>  SUP: response was 'OK'
Sep  1 01:27:04 asdman-laptop NetworkManager: <info>  Fully supported scan_capa_ssid mode.
Sep  1 01:27:04 asdman-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 1'
Sep  1 01:27:04 asdman-laptop NetworkManager: <info>  SUP: response was 'OK'
Sep  1 01:27:04 asdman-laptop NetworkManager: <info>  SUP: sending command 'ADD_NETWORK'
Sep  1 01:27:04 asdman-laptop NetworkManager: <info>  SUP: response was '0'
Sep  1 01:27:04 asdman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 776c616e'
Sep  1 01:27:04 asdman-laptop NetworkManager: <info>  SUP: response was 'OK'
Sep  1 01:27:04 asdman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 scan_ssid 1'
Sep  1 01:27:04 asdman-laptop NetworkManager: <info>  SUP: response was 'OK'
Sep  1 01:27:04 asdman-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE'
Sep  1 01:27:04 asdman-laptop NetworkManager: <info>  SUP: response was 'OK'
Sep  1 01:27:04 asdman-laptop NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0'
Sep  1 01:27:04 asdman-laptop NetworkManager: <info>  SUP: response was 'OK'
Sep  1 01:27:04 asdman-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Sep  1 01:27:06 asdman-laptop NetworkManager: <info>  Old device 'wlan0' activating, won't change.
Sep  1 01:27:39 asdman-laptop last message repeated 5 times
Sep  1 01:28:02 asdman-laptop last message repeated 4 times
Sep  1 01:28:04 asdman-laptop NetworkManager: <info>  Activation (wlan0/wireless): association took too long (>60s), failing activation.
Sep  1 01:28:04 asdman-laptop NetworkManager: <info>  Activation (wlan0) failure scheduled...
Sep  1 01:28:05 asdman-laptop NetworkManager: <info>  Activation (wlan0) failed for access point (wlan)
Sep  1 01:28:05 asdman-laptop NetworkManager: <info>  Activation (wlan0) failed.
Sep  1 01:28:05 asdman-laptop NetworkManager: <info>  Deactivating device wlan0.

```

It is actually able to configure the device, but not activate(connect to it?) it?

If it can't connect to the AP "wlan", I got no clue why not, as it is what I've set up with the router. It shouldn't be blocked by security, as I've disabled everything related to it.

---

### Post by falcon61102 on 2008-08-31
Could you post the results of:
```
sudo lshw -C network
```

---

### Post by Bucky Ball on 2008-08-31
and also results of

 **sudo iwlist wlan0 scan**

and 

**iwconfig**

Maybe it would be an idea to set an SSID and security key so you know exactly what you are trying to connect to and you know the details are right on the router and computer. Set the router to serve DHCP (plus while it is unsecure you next door neighbour may be having success connecting! lol).

:)

---

### Post by Calmatory on 2008-09-01
lshw -C network: ```
asdman@asdman-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 01
       serial: 00:1b:38:82:dc:38
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A ip=192.168.0.11 latency=64 maxlatency=56 mingnt=8 module=e100 multicast=yes
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1a:73:9e:01:6b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
asdman@asdman-laptop:~$ 

```
iwlist wlan0 scan: ```
asdman@asdman-laptop:~$ iwlist wlan0 scan
wlan0     No scan results

asdman@asdman-laptop:~$ 

```
iwconfig:```
asdman@asdman-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

asdman@asdman-laptop:~$ 

```


Well, I made the router to use WPA-PSK for now. :)

---

### Post by falcon61102 on 2008-09-01
You actually have a pretty commmon problem, here's a link with a walk through I made up a while ago for that card.  If you got any questions or hit any errors, post here and we'll help you through them.  Check out post 4:

[http://ubuntuforums.org/showthread.php?p=5703851#post5703851](http://ubuntuforums.org/showthread.php?p=5703851#post5703851)

---

### Post by Bucky Ball on 2008-09-01
Okay.

**System->Administration->Network**

Make sure there is no hardwire (ethernet cable) connection plugged in so we know we are only getting wireless. Unlock and click on your wireless connection (make sure it is ticked). Then:

**Properties**

For ESSID enter appropriate details. Then select your security type and enter the appropriate security key (network password). Make sure your configuration is set to 
[B]
Automatic Configuration (DHCP)[/B]

Next, open terminal and type:

**ifconfig wlan0 down**

then:

**ifconfig wlan0 up**

Any luck?

---

### Post by Calmatory on 2008-09-01
> **falcon61102 said:**
> You actually have a pretty commmon problem, here's a link with a walk through I made up a while ago for that card.  If you got any questions or hit any errors, post here and we'll help you through them.  Check out post 4:

[http://ubuntuforums.org/showthread.php?p=5703851#post5703851](http://ubuntuforums.org/showthread.php?p=5703851#post5703851)

Been there and done that. No success. After that, the wireless-led turned off. Just as I stated in my first post.

> **Bucky Ball said:**
> Okay.

**System->Administration->Network**

Make sure there is no hardwire (ethernet cable) connection plugged in so we know we are only getting wireless. Unlock and click on your wireless connection (make sure it is ticked). Then:

**Properties**

For ESSID enter appropriate details. Then select your security type and enter the appropriate security key (network password). Make sure your configuration is set to 
[B]
Automatic Configuration (DHCP)[/B]

Next, open terminal and type:

**ifconfig wlan0 down**

then:

**ifconfig wlan0 up**

Any luck?

No. :( Nothing interesting showing up in logs either.

---

### Post by IntuitiveNipple on 2008-09-01
Here's something to try:
```

sudo iwconfig wlan0 essid x mode managed

```
After you've done that, try selecting the WiFi network you want to associate with from Network Manager applet.

---

### Post by falcon61102 on 2008-09-01
Try this:
```
sudo rmmod ndiswrapper
sudo rmmod ssb
sudo modprobe ndiswrapper
```

One of your problems is that the module ssb is continuing to load even after the Hardy Fix.  If you can get that module to stop and ndiswrapper to load again, you should be able to see your access points.

---

### Post by Calmatory on 2008-09-01
Actually lshw -C network shows that the module is ndiswrapper, instead of ssb. Neither of posts above helped. :(

I've never seen that in Networking Tools wlan0 would be working as that it would show any info. Always after installing drivers with ndiswrapper/applying the Hardy fix, the wireless-led turns off.

---

### Post by Bucky Ball on 2008-09-02
Hey, been busy with uni stuff. This is a known bug and this might help you prevent ssb from loading first.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Hardy%20Bug%20Fix](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Hardy%20Bug%20Fix)

Good luck. :)

---

### Post by Calmatory on 2008-09-02
Let me repeat for nth time: It does NOT fix the problem. :(

It indeed loads ndiswrapper module instead of ssb, but even so the problem still exists, wireless ain't working. :( No AP's, nothing interesting in Network Tools wlan0 either.

---

### Post by Bucky Ball on 2008-09-02
If I come up with any ideas I'll let you know, but that is about me stumped. ;( Sorry.

You could try reposting in the wireless forum (which is where this should be) and you may get more help. Tell 'em exactly where you are now and see how you go. Good luck.

---

### Post by falcon61102 on 2008-09-02
If you've gone through all that and its still not working, I'm thinking its that you've either got the wrong drivers or, more likely, because you've tried so many things they may be causing a conflict.

---

### Post by Calmatory on 2008-09-02
> **falcon61102 said:**
> If you've gone through all that and its still not working, I'm thinking its that you've either got the wrong drivers or, more likely, because you've tried so many things they may be causing a conflict.
Very possible, and that is what I am guessing myself also.

Well, I'll do full reinstall in weekend and I will report back the findings.

Big thanks for everyone. :)

---

### Post by falcon61102 on 2008-09-02
Well good luck with everything.  Take a look at that walk through I posted a few post earlier, it was the same card and he was having trouble with it as well.  Hopefully it will get you up and running.

---

### Post by z0mbie on 2008-09-02
You might want to try this tutorial. It got my BCM43 card working:

[http://ubuntuforums.org/showthread.php?t=735444](http://ubuntuforums.org/showthread.php?t=735444)

---

