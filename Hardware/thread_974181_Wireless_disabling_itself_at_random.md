---
title: "Wireless disabling itself at random"
date: 2008-11-07
forum: Hardware
---

### Post by Leperous on 2008-11-07
Hello,

Since upgrading to Ubuntu 8.10 a couple of weeks ago, my wireless adapter seems to want to disable itself every now and then seemingly at random - anywhere from after a few hours of up-time to just 20 minutes from boot. 

The laptop is a Sony Vaio with an Intel 3945 adapter, and a wireless switch at the front. When I boot into Ubuntu the light on the switch turns on, and when the wireless dies (without me even touching the switch) it turns off. Turning the switch off/on manually doesn't revive the wireless - the only way I know how to fix it is to reboot the system. Of course, the switch works normally otherwise.

The only real clue I have to what's going on is a "Wireless now disabled by radio killswitch" message in daemon.log (attached). What's causing it to be disabled? How can I restart the wireless without rebooting? What *is* the killswitch? (If it's the physical switch, then why does it not respond to me switching it on and off?)

I do not suspect this is due to faulty hardware as I have a Windows partition, which I also often use, but this issue doesn't arise over there. 

Attached are outputs from dmesg before and after the disconnects, and a snippet of the daemon log. Please let me know if I need to supply any more info, and thanks for looking.

> #uname -r
2.6.27-7-generic

While working:
> #sudo iwconfig
eth1      IEEE 802.11abg  ESSID:"NETGEAR"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1B:2F:EE:89:E6   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:off
          Power Management:off
          Link Quality=90/100  Signal level:-41 dBm  Noise level=-82 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


PS I'm also not doing it via a FN+key combination, as this happens sometimes when I'm AFK!

---

### Post by linMtheu on 2008-11-18
Had the exact same problem with Intel 3945 on a Vaio VGN-FE31H after upgrading to 8.10.

However, 2.6.27-8 *may* have corrected the problem...

---

### Post by warsong on 2008-11-18
I have the same card in my Dell inspiron 6400. Mine stays connected but it seems like the speeds are VERY slow. Not sure what to do.

---

### Post by Ichido on 2008-11-18
Humm...
Sounds familiar.
My Dell Inspiron 1525n also exhibited similar problems.
The Dell Forum had some good "Fixes", so I would first look to your Sony's Forum.
My 'Kill-Switch' is a Physical Slide Switch, which must be on BEFORE I boot or no Wifi!
I'm using the Network Manager: "nm-applet 0.6.6".
After installing "Wifi Radar", I now have Perfect (for now) Wifi in Roaming Mode and using WPA Encryption with my Home Wifi Router.

Great Encryption Site is: [https://www.grc.com/passwords.htm](https://www.grc.com/passwords.htm)


I also used these:

**_#1->_**
Ubuntu 8.04/Issues/WiFi LED does not work
From Dell Linux Wiki
< Ubuntu 8.04
Jump to: navigation, search

Description: WiFi LED on system does not work. 
Systems Affected: Inspiron E1505n, 1420n, 1525n and XPS M1330n. 
Impact: WiFi LED on system does not turn on when WiFi is in use, but wireless still works. 
Fix: Install linux-backports-modules for your kernel. For example, if running kernel 2.6.24-16-generic: 
$ sudo apt-get install linux-backports-modules-2.6.24-16-generic

**_#2 ->_**
The WLAN LED does not glow on recent Intel-based notebooks (including Sony Vaio, Dell Inspiron, Lenovo Thinkpad and many others - we know, please don't list yours here), using the iwl4965 or iwl3945 WiFi drivers.
This problem is fixed for Ubuntu 8.04 (Hardy) in the backported kernel modules. (Note, however, that it does not behave the same way as it used to. The light will not blink on and off, but will be steady.)
Please install 'linux-backports-modules-hardy':
:~$ sudo apt-get install linux-backports-modules-hardy
then:
:~$ sudo rmmod iwl3945; sudo modprobe iwl3945

I am currently using Hardy 8.04
Kernel Linux 2.6.24-21-Generic
Gnome 2.22.3

I'll check back to see how your doing.

**PS.** Advice for your Home Wifi:
Change your ESSID "Netgear" to something NON Brand Specific and no Home Address.
Also use MAC Filtering in addition to WPA or WPA2 if possible.

---

### Post by kublaykan on 2011-02-14
Hi, I found a solution for this problem, that I've experienced after install Ubuntu 10.10 Maverick in my HP Pavilion with the iwl3945ABG Wireless modem.
It worked with two commands

[http://www.geekmind.net/2011/01/linux-wifi-operation-not-possible-due.html](http://www.geekmind.net/2011/01/linux-wifi-operation-not-possible-due.html)

Thanks!

---

