---
title: "Problems running &quot;make&quot;"
date: 2008-11-10
forum: Hardware
---

### Post by mattbrad on 2008-11-10
Evening all,

I recently bought a Fujitsu Siemens Amilo 2727 and it turns out getting the wireless card to work is a bit of a bodge.

Basically im trying to install a package that will let me initialize the wireless card. The package is called acerhk.

When i untar the package, and run the make command i get the following error ... 

matt@matt-laptop:~/Desktop/acerhk-0.5.35$ sudo make
make -C /lib/modules/`uname -r`/build SUBDIRS= M=/home/matt/Desktop/acerhk-0.5.35 V= modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
 CC [M]  /home/matt/Desktop/acerhk-0.5.35/acerhk.o
/home/matt/Desktop/acerhk-0.5.35/acerhk.c: In function ‘call_bios_6xx’:
/home/matt/Desktop/acerhk-0.5.35/acerhk.c:582: error: bp cannot be used in asm here
make[2]: *** [/home/matt/Desktop/acerhk-0.5.35/acerhk.o] Error 1
make[1]: *** [_module_/home/matt/Desktop/acerhk-0.5.35] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [acerhk.ko] Error 2

Im led to beleive that this is a problem with my "kernel headers", but i think ive done the neccessary install to update my headers?! Anyone got any ideas?!

Any help would be great, its a usual story, but im pretty new to ubunutu!! Especially messing around with installing things etc etc!!

---

### Post by mattbrad on 2008-11-11
Someone?
Anyone?

I've just got a raft of updates through the update manager, but none seemed to help!!

---

### Post by pelle.k on 2008-11-11
but acerhk is already in the kernel? You are running intrepid right?
```
modprobe -l acer*
```
Are they loaded?
```
lsmod | grep acer
```

In case you need to compile it anyway:
```
sudo apt-get install linux-headers-generic build-essentials
```

Btw, was there no "./configure" step involved?

---

### Post by mattbrad on 2008-11-11
Hi, thanks for the advice. I tried your first command, but it errors saying "cant have multiple wildcards". I did your second command and got ...

acerhk                 33588  0 

And i ran your third one (minus the trailing s) and it was already upto date!

yes im running intrepid and ive been told that i need to install this acerhk thing so i can active my wireless card, which is stupidly disabled by default. To activate it needs a hot key (in windows land anyway!!)

---

### Post by mattbrad on 2008-11-11
Strangely, i re downloaded the acerhk package and tried to run make again and this time i got the following error ...

matt@matt-laptop:~/Desktop/acerhk-0.5.35$ make
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/matt/Desktop/acerhk-0.5.35 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /home/matt/Desktop/acerhk-0.5.35/acerhk.o
gcc: -pg and -fomit-frame-pointer are incompatible
make[2]: *** [/home/matt/Desktop/acerhk-0.5.35/acerhk.o] Error 1
make[1]: *** [_module_/home/matt/Desktop/acerhk-0.5.35] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [acerhk.ko] Error 2

---

### Post by Leslie Viljoen on 2008-11-11
> **mattbrad said:**
> Hi, thanks for the advice. I tried your first command, but it errors saying "cant have multiple wildcards". I did your second command and got ...

acerhk                 33588  0 


This indicates that the driver is already compiled and loaded! The errors you get compiling make me think that the code you are downloading is for a different version of GCC, or for a different architecture. Either way, you may need to download a different package.

I'd first check versions - only try compiling a driver again if you are sure it is newer than the one loaded, and that it is likely to work better than the one loaded (ie. a bug was fixed that will help you).

To see what version is loaded, "modinfo acerhk" may help.

---

### Post by pelle.k on 2008-11-12
acerhk 0.5.35 is already in the kernel. But apparently it doesn't work too well on 64bit. But you're running 32bit right?

So you need to figure out if you can enable the wlan now. If you press the wireless keys (fn+something?), does it show in dmesg? (run the cmmand AFTER pressing the keys)
```
dmesg | tail
```

I did have the same problem with my LG notebook, but all i had to do was enable it in windows *ONCE*, and after that it'd always work in linux. (unless i disable it windows again of course). Just throwing that out there...

Can you paste the output of
```
sudo ls /proc/driver/acerhk
```

---

### Post by mattbrad on 2008-11-12
when i run dmesg | tail i get ...

```

matt@matt-laptop:~$ dmesg | tail
[ 5378.835045]   groups: 1 0
[ 7142.857726] __ratelimit: 3 callbacks suppressed
[ 7142.857747] type=1505 audit(1226521721.788:17): operation="profile_replace" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=9847
[ 7143.066025] type=1505 audit(1226521721.996:18): operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=9852
[ 7143.066416] type=1505 audit(1226521721.996:19): operation="profile_replace" name="/usr/sbin/cupsd" name2="default" pid=9852
[ 7143.116343] type=1505 audit(1226521722.048:20): operation="profile_replace" name="/usr/sbin/mysqld" name2="default" pid=9858
[ 7144.761749] type=1505 audit(1226521723.693:21): operation="profile_replace" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=9968
[ 7144.974093] type=1505 audit(1226521723.905:22): operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=9973
[ 7144.976576] type=1505 audit(1226521723.905:23): operation="profile_replace" name="/usr/sbin/cupsd" name2="default" pid=9973
[ 7145.027371] type=1505 audit(1226521723.957:24): operation="profile_replace" name="/usr/sbin/mysqld" name2="default" pid=9977


```

and when i run the second command, sudo ls /proc/driver/acerhk i get ...

```
blueled  info  key  led  wirelessled
```

---

### Post by pelle.k on 2008-11-13
Allright, now just (if that is a file and not a directory)
```
echo 1 | sudo tee /proc/driver/acerhk/wirelessled
```
And you should have a working wireless interface :) (sorry about the complicated command line wrangling, it's just a glorified eqvivalent to the one below really)
If you want it to be automatic, then put
```
echo 1 > /proc/driver/acerhk/wirelessled
```
in /etc/rc.local (that file gets executed at bootup).
If it doesn't work, or you have another problem (such as getting it working after suspend), just tell us about it.

---

### Post by mattbrad on 2008-11-18
Ive been messing with this for a while now and still no joy! To the extend that ive just removed all ubuntu partitions and started with a fresh install of Ibex.

You say acerhk is already installed in ibex? Whats the best plan of action for a fresh install?

Just to run through your help so far, here is my current output from the commands you gave me:

**modprobe -l acer***
/lib/modules/2.6.27-7-generic/kernel/ubuntu/misc/acerhk.ko
/lib/modules/2.6.27-7-generic/kernel/drivers/misc/acer-wmi.ko

**lsmod | grep acer**
Returns nothing

**dmesg | tail**
[  133.853446] type=1503 audit(1227042452.403:10): operation="socket_create" family="appletalk" sock_type="dgram" protocol=0 pid=5704 profile="/usr/sbin/cupsd"
[  133.853461] type=1503 audit(1227042452.403:11): operation="socket_create" family="econet" sock_type="dgram" protocol=0 pid=5704 profile="/usr/sbin/cupsd"
[  133.853480] type=1503 audit(1227042452.403:12): operation="socket_create" family="ash" sock_type="dgram" protocol=0 pid=5704 profile="/usr/sbin/cupsd"
[  133.853495] type=1503 audit(1227042452.403:13): operation="socket_create" family="x25" sock_type="seqpacket" protocol=0 pid=5704 profile="/usr/sbin/cupsd"
[  133.853619] type=1503 audit(1227042452.403:14): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=7 name="/proc/5704/net/dev" pid=5704 profile="/usr/sbin/cupsd"
[  439.138940] r8169: eth0: link up
[  439.139649] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  439.581994] NET: Registered protocol family 17
[  449.760049] eth0: no IPv6 routers present
[ 1962.721713] r8169: eth0: link down

**sudo ls /proc/driver/acerhk**
ls: cannot access /proc/driver/acerhk: No such file or directory


It would appear that ive taken a few steps backwards, but i was a little worried about all the config changes id already made, as it added 5 mins onto the startup load time!!

Any help would be greatly appreciated!

---

### Post by pelle.k on 2008-11-19
First of all, did you get it to work before, with the steps i provided?

Second, the module isn't loaded. Just
```
sudo modprobe acerhk
```
to load it temporary, and you may put "acerhk" in /etc/modules to have it load automatically at startup.

Now you *should* get it working by what i wrote in my latest post in this thread. If not, do another "dmesg | tail" just after you completed all the previous steps.

---

### Post by mattbrad on 2008-11-19
Hi, i never got it working on the previous install. I presumed that i might have messed something up along the way, being that it took 5 minutes to start up!!

I've now followed all your steps (again!) and im not sure where im at! The wireless led now lights up when i startup, ive added acerhk to the modules file, but im not sure how/where to access this interface you mention?!

I've tried the function+F1 button, which is how i turn on wireless in windows and nothing happens. 

When i run dmesg | tail i get the following output:

> 
matt@matt-laptop:~$ dmesg | tail
[   70.431322]  domain 0: span 0-1 level MC
[   70.431328]   groups: 1 0
[   94.607988] NET: Registered protocol family 10
[   94.610831] lo: Disabled Privacy Extensions
[   94.613647] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  170.011238] r8169: eth0: link up
[  170.011940] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  170.137481] NET: Registered protocol family 17
[  180.312067] eth0: no IPv6 routers present
[  547.560154] r8169: eth0: link down


Sorry for the total lack of knowledge in all this, my previous experience of ubuntu never needed me to jigg around with the wireless setup!!

---

### Post by pelle.k on 2008-11-19
Ok, to sum it up.
[LIST]
[*]acerhk gets loaded at bootup (verify with "lsmod | grep acerhk", you don't need to paste that here though)
[*]it's activated (verify with "cat /proc/driver/acerhk/wirelessled", is should be "1", again no need to paste that here if it does work)
[/LIST]

So, you should have a wlan0 interface. Try to scan with;
```
sudo iwlist scan
```

If it's not there, clear /etc/rc.local of the modification we did there, and put this in /etc/modprobe.d/options
```
options acerhk autowlan=1
```

If that doesn't work (reboot, then try to scan again), can you please paste the output of;
```
dmesg | grep -i acer
```
```
dmesg | grep -i wlan
```

And, as a last resort (if we dont get this working) you can still try setting it up with ndiswrapper i guess. But, we'll cross that bridge whern we get to it.

---

### Post by mattbrad on 2008-11-19
hmm, acerhk does indeed get loaded at bootup. But when i run **cat /proc/driver/acerhk/wirelessled** i get nothing, its just blank.

When i scan for the interface im presented with the following:
> 
matt@matt-laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.


So i did the two changes to rc.local and modprobe/options, rebooted, scanned again, and still no luck!
**dmesg | grep -i acer**
> 
matt@matt-laptop:~$ dmesg | grep -i acer
[    0.609576] tracer: 772 pages allocated for 65536 entries of 48 bytes
[   13.070289] input: Acer hotkey driver as /devices/virtual/input/input6
[   13.101255] Acer Travelmate hotkey driver v0.5.34


**dmesg | grep -i wlan**
> 
matt@matt-laptop:~$ dmesg | grep -i wlan
[   13.005728] wlan: 0.9.4


Just a thought, me having a internet cable plugged into the laptop whilst im doing all this will mess any of these tests up will it??

---

### Post by pelle.k on 2008-11-20
> Just a thought, me having a internet cable plugged into the laptop whilst im doing all this will mess any of these tests up will it??
Nope.

> But when i run cat /proc/driver/acerhk/wirelessled i get nothing, its just blank.
Sorry about that. You should probably use "sudo" with that command. But don't bother with that. Since the wireless led did light up, it must have been working.

So, i guess you did try the **autowlan=1** modification right? Well, try adding "usedritek=1" to that line as well. (also, if the wireless doesn't get light up by this alone, add the modification we did to /etc/rc.local as well)

Is it an Atheros card? (paste "lspci | grep -i ar5")
Is the module loaded? (paste "dmesg | grep ath")

---

### Post by mattbrad on 2008-11-20
Yes ive still got the wlan=1 in my modprobe/options file, and ive now added the other line, so it reads:

> 
options acerhk autowlan=1 
options acerhk usedritek=1


After adding the second one, i tried the hotkey, nothing happened. Restarted, tried the hotkey, nothing happened!! You did mean add that as a seperate line didnt you? And not to stick it on the end of the other acerhk line??

**lspci | grep -i ar5**
Returns nothing

**dmesg | grep ath**
> 
matt@matt-laptop:~$ dmesg | grep ath
[   12.572110] ath_hal: module license 'Proprietary' taints kernel.
[   12.576029] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   12.760596] ath_pci: 0.9.4
[   12.760642] ath_pci 0000:08:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   12.760656] ath_pci 0000:08:00.0: setting latency timer to 64
[   12.808935] ath_pci 0000:08:00.0: PCI INT A disabled


Thanks for all your help on this!!

---

### Post by pelle.k on 2008-11-20
Ok man, i *think* i've found the solution for you. It would seem this solution has worked for a few others with your problem.

Now, first remove the option(s) you put into **/etc/modprobe.d/options**
Then, remove the line you added to **/etc/rc.local**

This is really easy, and if it works, :popcorn:
Add this to a new file, put it in **/etc/modprobe.d/amilo_special_keys.modprobe**
```
install acerhk /sbin/modprobe --ignore-install acerhk force_series=6805 autowlan=1; echo 1 > /proc/driver/acerhk/wirelessled
```

Please tell us how it went!

---

### Post by mattbrad on 2008-11-21
hhhmmmm, still nothing!! I removed those lines from rc.local and modprobe/options and created the file called /etc/modprobe.d/amilo_special_keys.modprobe and put that line in it?! I dont need t give this file special permissions do i? I created it by running "touch" and then sudo gedit to add the line?!

Still when i press my funcion key nothing seems to happen! What *should* happen when i press it? Should it bring up the little bars in the top left hand corner, or open a window, or does it simply enable the wireless card in the back ground?!

Either way, i still cant get an pages up in my browser!!

You must think im a nightmare!! haha.

---

### Post by mattbrad on 2008-11-21
hhhmmmm, still nothing!! I removed those lines from rc.local and modprobe/options and created the file called /etc/modprobe.d/amilo_special_keys.modprobe and put that line in it?! I dont need t give this file special permissions do i? I created it by running "touch" and then sudo gedit to add the line?!

Still when i press my funcion key nothing seems to happen! What *should* happen when i press it? Should it bring up the little bars in the top left hand corner, or open a window, or does it simply enable the wireless card in the back ground?!

Either way, i still cant get an pages up in my browser!!

You must think im a nightmare!! haha.

---

### Post by pelle.k on 2008-11-21
> You must think im a nightmare!! haha.
No man, not at all. I mean, this stuff is not exactly super obvious to begin with.
With the last modification i gave you, you shouldn't have to press fn+wireless, even though this key should be working now (enable/disable wireless, though it does that quietly). i.e. the wireless interface should be "working" by default, after booting up.
Now, this doesn't mean you have a working Internet connection by default.
You should connect to a AP (Access point, meaning wireless router), and normally that is done with network-manager. When you click it (it should be in the system tray), you should be presented with a list of networks.
Then click one, and from there, things should be pretty straight forward.

Now, it should be working, since i took this tip from a guy who was actually running an amilo 2727 himself. It was on hardy heron (aka 8.04 LTS) though, but it should work on intrepid as well.

If you're unsure of the interface is working, just post the output of
```
ifconfig -a
```
here, but it's easy to spot. It's probably called wlan0 or ath0 or something like that.

---

### Post by mattbrad on 2008-11-22
Still no sign of being able to search for networks. When i open the Network Manager the Wireless tab is there, but i can't seem to automatically search for any connections?!

Also of note, my output of ifoncig -a is ...

> 
matt@matt-laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0a:e4:cd:48:6f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:220 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:376 (376.0 B)  TX bytes:376 (376.0 B)

pan0      Link encap:Ethernet  HWaddr 2a:0c:0f:35:65:12  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


Just to be sure, i tried this before and after pressing my function key, with the same result?!!

---

### Post by pelle.k on 2008-11-22
Allright man. We gave it a good shot. May i recommend you try the LTS release of ubuntu instead? It may not be as exciting as intrepid, but at least it will at least work with your wireless (from what i understand), unless of course you've got some real exotic hardware instead of what *should* be in there :)

Sorry we didn't get it working, and i must admit, i'm all out of ideas.

---

### Post by mattbrad on 2008-12-13
Back again! This time i decided to take your advice and install hardy to see if i could get it working.

And so far, its a marked improvement! I've managed to find this tutorial ...
[http://madwifi-project.org/wiki/UserDocs/MiniPCI#FujistsuSiemensAmiloLi2727withAtherosAR2425AR5007EG802.11abgPCI-erev01](http://madwifi-project.org/wiki/UserDocs/MiniPCI#FujistsuSiemensAmiloLi2727withAtherosAR2425AR5007EG802.11abgPCI-erev01)

And ive loaded the acer hotkey (even though you mentioned that it was built in) and im mid way through the madwifi tutorial. So far i've got the card to scan for access points and it picks up my router, but i cant seem to connect to it. I scan for routers by running

```

sudo iwlist ath0 scan

```


Then i try and connect to my router by doing
```
iwconfig ath0 essid "routername"
```


Then this is where i come unstuck. Im not sure whether to use wep or wpa, nor do i know how to find out which i should use?! Also the tutorial asks whether im using an open key or a shared one?! 

This is probably pretty basic stuff, but it seems to have me stumped! When i follow the tutorial through i get to running

```
sudo dhclient ath0
```

And it comes back with ...

```

matt@matt-laptop:~/Desktop$ sudo dhclient ath0
There is already a pid file /var/run/dhclient.pid with pid 12286
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/06:16:44:d1:7c:6e
Sending on   LPF/ath0/06:16:44:d1:7c:6e
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


```

Any help would be greatly appreciated!

---

### Post by Hyper Tails on 2008-12-13
I need help getting make working too when I want to install a programm from tar.bzz on my desktop
or any location (I think)

---

### Post by pelle.k on 2008-12-14
> I need help getting make working too when I want to install a programm from tar.bzz on my desktop
Hyper Tails, you will need to do some research. The thing with source tarballs is that you souldn't install those on a binary distro such as ubuntu unless you know what you're doing, and also there are no magic tricks to it. It depends on the distro as well, but generally you have to research what -dev (development) packages you need installed to build the source, what build tools you need to have installed, and what packages you need installed to run the binaries when they're installed. To make that extra interesting, you need to apply that differently to whatever distro you are using.
The best thing would be to start a new thread describing what source tarball it is you're trying to compile and install, and also what version of ubuntu you are using (inluding if it's 32 or 64 bit).

> So far i've got the card to scan for access points and it picks up my router, but i cant seem to connect to it. I scan for routers by running

Allright! Halfway there!

> Also the tutorial asks whether im using an open key or a shared one?! 
Yeah, and this stuff need to match exactly what is set in the router, so the best thing would be to log in to the router using a wired connection, and find these things out. This is probably the reason you're not getting associated with the router, and thus no IP lease.

---

### Post by mattbrad on 2008-12-15
Huray! A minor miracle! I finally got the laptop working with my wireless router! I followed the steps in that tutorial and it worked fine. Instead of setting up madwifi to use WPA i changed my router to WEP and it let me connect.

Now, it doesn't seem to save the settings of the steps that i did in the tutorial when i restart?! I added the specific lines to /etc/modprobe.d/options and the led light is now constantly on. 

I surely wont have to go through all that every time i boot up?!

---

### Post by pelle.k on 2008-12-16
See, all the commands you used to "set up" the wireless to connect to the AP are temporary. You may set up a new connection manually using network-manager, but this network should have been visible from the start in networkmanager, and clickable so that you could set a (WEP) password. See this is exactly what networkmanager is supposed to do.
But anyway, right click networkmanager, choose "edit connections" and add a wirless network with WEP authentication manually then. It's the same thing you did really.
If there *is* some bug in networkmanager that just keeps you from connecting, we can set it up manually in /etc/network/interfaces, but let's just see if you can do it in networkmanager first, shall we?

---

