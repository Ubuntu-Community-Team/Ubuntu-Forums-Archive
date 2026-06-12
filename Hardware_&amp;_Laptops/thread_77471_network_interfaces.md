---
title: "network interfaces"
date: 2005-10-16
forum: Hardware &amp; Laptops
---

### Post by withoutclass on 2005-10-16
At startup it seems that it takes quite some time for ubuntu to move on in the boot process after it hits configuring network interfaces.  It just seems to kind of hang/do a lot of work during this phase and was wondering if others were seeing this same thing occuring.

---

### Post by pepster on 2005-10-16
I have the same problem with Hoary on my laptop.

The funny part is that if I hit a Ctrl-C, I can later setup manually (sudo ifup eth...) in no time at all.

-Joseph

---

### Post by withoutclass on 2005-10-16
yea, im running a laptop too, it only really seemed to occur after i configured and activated my wireless card, even though i have eth0 set to default, the load at this portion takes about 30 seconds or so to complete

---

### Post by pepster on 2005-10-18
My problem must be different.
My wifi is disabled. /etc/network/interfaces says

auto lo eth1


(where eth0 is the wifi, eth1 ethernet)
I don't think my wifi even work under Linux, but I have no way to test it.

-Joseph

---

### Post by withoutclass on 2005-10-18
[QUOTE=pepster]My problem must be different.
My wifi is disabled. /etc/network/interfaces says

auto lo eth1


(where eth0 is the wifi, eth1 ethernet)
I don't think my wifi even work under Linux, but I have no way to test it.

-Joseph[/QUOTE]

if u go to administration u can activate your card using the networking section in the menu

---

### Post by Roybotnik on 2005-10-18
I have the same issue.  It seems like for any reason if one of my active network interfaces is disconnected, it hangs for a long time at the 'configuring network interfaces' section of the bootup screen.  It happens on both my laptop and my desktop.  

My laptop has both wifi and ethernet, and I noticed that if I disable the ethernet adapter and it is able to connect to a wireless network while booting up, it doesn't hang at all.  However, if no network is in range, it sits there for quite a long time.

---

### Post by pepster on 2005-10-19
Your experience seem to agree with my thoughts - that ubuntu trys to activate eth0 regardless. We need to find a way to tell it eth1 is the primary one.

-Joseph

---

### Post by pepster on 2005-10-19
Check your /etc/network/interfaces. If you see something like

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
       script grep
       map eth0


Comment it out and your boot may be faster. mine is now.


-Joseph

---

### Post by peterbe on 2005-11-20
Soon after bringing network interfaces up, the Ubuntu init process tries to bring up a connection to an NTP server. If you aren't connected to the Internet at that point, it will take a minute for the DNS search to time out. You will see the message "Synchronizing clock to ntp.ubuntulinux.org", and the system will appear to hang for 60 seconds.

 A simple solution is to enter the IP address of an NTP server instead. In my /etc/default/ntpdate file, I made the change

#NTPSERVERS="ntp.ubuntulinux.org"
# time.sr.sonic.net :
NTPSERVERS="209.204.159.18"

Then you will have only a very brief delay if the server is unreachable.

You would probably choose a server closer to where you live; the one I use is in
Northern California. (You could use the IP of the Ubuntu server ntp.ubuntu.iinux.org,
which is in the UK, for example).

In my case, I observed this problem on my laptop, which isn't always connected to the Internet.

---

### Post by jazzwhistle on 2006-01-31
> mapping hotplug
script grep
map eth0

Comment it out and your boot may be faster. mine is now.

Well that helped with the second hang on "bringing up interfaces", but the "configuring interfaces" part is about a minute on my fully updated breezy install. That said I feel lucky to have got wireless usb working at all. And my Deskjet 710c... and my Phillips webcam and my Sony Cybershot and... the list goes on.  

Great to back in linuxland after a few years waiting for things to improve, as I'm not yet up to contributing other than finding problems. Ubuntu is fantastic in all its flavours, and with dual boot XP and Ubuntu with vmware 5 I've got XP on another desktop within my linux box in case I need to work on Flash docs etc - yes I'm flying around KDE... feels great to zip around like that without waiting for explorer and programs to catch up.  People have been working hard. Once I get my DV cam running, I'm here for good.

And I can't stand that realllllly long boot. I'v chopped off various services, but that network gets me every time - and the worst thing is that I still have to wait 5 minutes before Opera brings Google. Any other ideas?

Cheers

---

### Post by iamajd on 2006-03-04
i was in a similar situation.
usually (at home, within the range of my network) its not a problem.
but when im away, it would take forever to boot.
i edited the following file:

/etc/dhcp3/dhclient.conf

find the line that says
#timeout 60

and change it to
timeout 10

when im at home, my dhcp responds within 10 seconds, so this seemed like a safe range.  hope that helps.

---

### Post by valaraukar on 2006-04-11
The same trouble. 
I've got two network cards one of them is connected to cabel modem(eth1), it is not used under linux.

Booting hangs up at "Configuring network interfaces" for 40-60 seconds.
Ip is static, no dhcp is used. Adding timeout 10 to /etc/dhcp3/dhclient.conf didn't help.

I think this may happen because of sendmail which i've installed recently.
Also it could be vmware.

Ctrl+C helps, but when i try to do ```
sudo ifup eth0
``` it hangs again and in dmesg i 've got
```

/dev/vmmon[3804]: Module vmmon: registered with major=10 minor=165
/dev/vmmon[3804]: Module vmmon: initialized
/dev/vmnet: open called by PID 3838 (vmnet-bridge)
/dev/vmnet: hub 0 does not exist, allocating memory.
/dev/vmnet: port on hub 0 successfully opened
bridge-eth0: peer interface eth0 not found, will wait for it to come up
bridge-eth0: attached
bridge-eth0: enabling the bridge
bridge-eth0: up
e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex

```


removed sendmail from if-up.d and everyting is ok now )

---

### Post by juan_suave on 2006-07-07
@iamajd:  Thanks, that edit worked perfectly for me.

---

