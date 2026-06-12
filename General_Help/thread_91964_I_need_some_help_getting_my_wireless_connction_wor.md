---
title: "I need some help getting my wireless connction working"
date: 2005-11-18
forum: General Help
---

### Post by onesojourner on 2005-11-18
I have this in the new user sections but it isn't getting any traffic.

I have an old slow dell inpiron 7000. I have a dlink dwl-g630 cardbus. I installed ndiswrapper and the driver (i think) and the connection is there when i click sytem/admin/networking It says active and I typed in my network name and wep key. and it is set to active. when i click on the network icon up in top right it says disconnected. what did I do wrong?

---

### Post by Dr. Nick on 2005-11-18
are you able to disable wep and retest it? It can be easier to get it working without wep first just so you know the driver is set up.

---

### Post by onesojourner on 2005-11-19
I'm not sure if I'm doing it right but I took the password out. will that disable the wep? I also took the name out and niether one changed anything. the internet connection Icon in the top left still has a yallow triangle with a ! in it. it is set on wlan0. it says status disconnected.

---

### Post by iguanaphobic on 2005-11-19
1) Reset the wireless router to NOT use WEP.

2) Right-click on network applet, select properties, then select configure.

3) Highlight wireless connection and click properties.

4) Click the Network Name (ESSID) down arrow and select the wireless network by it's name. (Should simply be there, no need to manually type it in)

5) Change key type to Plain (ASCII) and select DHCP (If that is what your router is set to, otherwise add your IP information for your computer)

6) Apply changes. 

THis should do it. If you can connect to an open router, you can then add WEP and start troubleshooting that.

---

### Post by onesojourner on 2005-11-20
4) Click the Network Name (ESSID) down arrow and select the wireless network by it's name. (Should simply be there, no need to manually type it in)

I am not getting any network names. I am with in range.

---

### Post by onesojourner on 2005-11-21
anyone?

---

### Post by Efwis on 2005-11-21
I have a linksys wireless setup, in order to connect I had to edit the .conf files and manually put my essid name in, then it started working.

 in order for this to work you need to know exactly the name for the essid. like in my situation it was simply "linksys"

---

### Post by onesojourner on 2005-11-21
[QUOTE=Efwis]I have a linksys wireless setup, in order to connect I had to edit the .conf files and manually put my essid name in, then it started working.

 in order for this to work you need to know exactly the name for the essid. like in my situation it was simply "linksys"[/QUOTE]

sounds like a pain to add multiple locations (does this method even support multi locations?) but I can live with that. is there a thread that explains how to do this for some one like me that... step by step please.


thanks

---

### Post by Efwis on 2005-11-21
This is what worked for me, mind you this is for Broadcom chipsets, I'm not sure what chipset Dlink uses. pretty much all my issues got answered in the first 3 pages.

[http://www.ubuntuforums.org/showthread.php?t=25683&highlight=broadcom+chipset](http://www.ubuntuforums.org/showthread.php?t=25683&highlight=broadcom+chipset)

---

### Post by az on 2005-11-21
[QUOTE=onesojourner]sounds like a pain to add multiple locations (does this method even support multi locations?) but I can live with that. is there a thread that explains how to do this for some one like me that... step by step please.


thanks[/QUOTE]
I woudl start from the beginning and go look on the ndiswrapper wiki for the most recent version of the windows driver.  Even if your's works in windows, ndiswrapper is built using (always) the most recent version of the driver.  That means that even if you get it working, when you upgrade your version of ndiswrapper, you may need to go to the manufacturer's site and get newer windows drivers, if available.

In general, ndiswrapper supports scanning, so your essid should appear in the drop-down part of the networking app.  The fact that it is not there suggests that you do not have a wokring driver.  I may be wrong, since I have not used your card before.

Some linux-native wireless drivers do not support scanning for essids so in that case you need to enter your essid by hand.  There is no need to edit the /etc/notworking/interfaces file by hand since that is what the networking tool does.

---

### Post by Lambert on 2005-11-21
You shouldn't have to use ndiswrapper to get this card to work in breezy as I show it using the madwifi drivers.

802.11g 	DWL-G630 (rev. 1) 	man:168c dev:001a 	Cardbus 	Atheros 	Mad WiFi

However there is a g630 card out there with a marvell chipset so it is possible but this card seems kind of rare.

With the card in run this command 

lspci -v

There will be lines for different devices along the pci line but look for your wireless card. 

If it says atheros anywhere then you don't need ndiswrapper. Keep reading from here. If it is not atheros then skip down to the next section in bold.

remove the driver from ndiswrapper.

sudo ndiswrapper -e <driver>

then remove ndiswrapper module

sudo modprobe -r ndiswrapper

Take the card out and reinsert it then 

sudo lshw -C network

Find the card in the output and look for a line that begins with configuration: does it say driver=ath_pci if so then run

iwconfig

If you see ath0 with a bunch of lines with data next to it then the card and driver is working.

Then you can open network manager (system>admin>network) highlight wireless device click properties. Enter essid and dhcp or static depending how your ip address is assigned. If you have wep then enter that but as posted earlier, turn wep off on the router to connect and after you see it's working add wep back into the equation. Click ok then click activate.

**If it is not an atheros chipset then post back the contents of these commands**

1. sudo lshw -C network
2. lspci
3. iwconfig
4. ifconfig
5. sudo iwlist <logical_name> scan

logical name for ndiswrapper is usually wlan0. For other cards it's different such as ath0 for cards with atheros chipset.

---

### Post by Efwis on 2005-11-21
[QUOTE=azz]

Some linux-native wireless drivers do not support scanning for essids so in that case you need to enter your essid by hand.  There is no need to edit the /etc/notworking/interfaces file by hand since that is what the networking tool does.[/QUOTE]
I wasn't that lucky, the Networking tool didn't work for me, thats why I had to manually edit my file.

---

### Post by az on 2005-11-21
Looking here:
[https://wiki.ubuntu.com/HowToSetUpNdiswrapper](https://wiki.ubuntu.com/HowToSetUpNdiswrapper)
I found this:
[https://wiki.ubuntu.com/DWLG650WiFi](https://wiki.ubuntu.com/DWLG650WiFi)

Maybe the fact that the firmware is wrong is your problem.

If not, you can try the latest windows driver you find here:
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)

---

### Post by az on 2005-11-21
[QUOTE=Efwis]I wasn't that lucky, the Networking tool didn't work for me, thats why I had to manually edit my file.[/QUOTE]

Can you reproduce the problem?  If so, would you please file a bug report about it?  I cannot find an open bug which describes this.   (but I did not look very hard - please try that first!)

bugzilla.ubuntu.com

The package is gnome-system-tools.

---

### Post by Efwis on 2005-11-21
I will have to see if I can reproduce it or not. i was just happy to get it up and running after 2 days of fighting with ndiswrapper to begin with.

It would be nice if they could find a little easier way for it be installed, but thats just my opnion. I'm still relatively new to Linux, 6 months of using it, but I am a quick learner.

---

### Post by az on 2005-11-21
[QUOTE=Efwis]I will have to see if I can reproduce it or not. i was just happy to get it up and running after 2 days of fighting with ndiswrapper to begin with.
.[/QUOTE]

If you run

sudo mv /etc/networking/interfaces /etc/networking/interfaces.backup


and then try to configure your connection from scratch using the networking tool, you can copy the 
interfaces backup back to the original if it does not work.

Run 
sudo /etc/init.d/networking stop
before you run the networking tool, though.

---

### Post by onesojourner on 2005-11-22
[QUOTE=Lambert]
**If it is not an atheros chipset then post back the contents of these commands**

1. sudo lshw -C network
2. lspci
3. iwconfig
4. ifconfig
5. sudo iwlist <logical_name> scan

logical name for ndiswrapper is usually wlan0. For other cards it's different such as ath0 for cards with atheros chipset.[/QUOTE]


I am not sure If I did number 5 right, but here is what I get

0000:02:00.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface
        Subsystem: D-Link System Inc: Unknown device 3b08
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at 14820000 (32-bit, non-prefetchable) [size=8K]
        Memory at 14800000 (32-bit, non-prefetchable) [size=128K]
        Capabilities: <available only to root>

peter@oldlaptop:~$ Ispci -v
bash: Ispci: command not found
peter@oldlaptop:~$ sudo lshw -C network
Password:
  *-network
       description: Wireless interface
       product: ACX 111 54Mbps Wireless Interface
       vendor: Texas Instruments
       physical id: 0
       bus info: pci@02:00.0
       logical name: wlan0
       version: 00
       serial: 00:0f:3d:0b:c4:71
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=acx_pci multicast=yes wireless=IEEE 802.11b+/g+
       resources: iomemory:14820000-14821fff iomemory:14800000-1481ffff irq:11
peter@oldlaptop:~$ lspci
0000:00:00.0 Host bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 02)
0000:00:01.0 PCI bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 02)
0000:00:04.0 CardBus bridge: Texas Instruments PCI1220 (rev 02)
0000:00:04.1 CardBus bridge: Texas Instruments PCI1220 (rev 02)
0000:00:07.0 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:07.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:00:08.0 Multimedia audio controller: ESS Technology ES1968 Maestro 2
0000:01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage LT Pro AGP-133 (rev dc)
0000:02:00.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface
peter@oldlaptop:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11b+/g+  ESSID:"STA0BC471"  Nickname:"acx100 v0.2.0pre8"
          Mode:Auto  Frequency:2.412 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3
          Retry min limit:7   RTS thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

peter@oldlaptop:~$ ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1871 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1871 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:166249 (162.3 KiB)  TX bytes:166249 (162.3 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:0F:3D:0B:C4:71
          inet6 addr: fe80::20f:3dff:fe0b:c471/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11

peter@oldlaptop:~$ sudo iwlist wlan0
iwlist: unknown command `wlan0'
peter@oldlaptop:~$ sudo iwlist <wlan0>
bash: syntax error near unexpected token `newline'
peter@oldlaptop:~$

---

### Post by onesojourner on 2005-11-22
do you guys need more information. let me know what else I can tell you or get you about this problem and I will do it asap.

---

### Post by Dr. Nick on 2005-11-22
Could you post the output of ```
cat /etc/network/interfaces
```
I dont see it anywhere in this thread.

You say your card shows up in the netowrk panel but not your ssid? I would believe you to be out of range, or possibly the ssid broadcast has been shut off in the router.

Run ```
iwlist scan
``` and see what it says.

If you can get into your router and disable wep temporarily then edit your interfaces file and "hardcode" your ssid and the phrase wireless_enc off I believe.

If you post your interfaces file it may help troubleshoot some. I havent used ndiswrapper so not sure exactly whats going on.

---

### Post by onesojourner on 2005-11-22
ok I will be away from the computer for abother 5 hours but I will post up the results asap. I am broadcasting my ssid. I have a ppc another laptop and my ubuntu desktop and all 3 see it. its just this one laptop that isn't seeing it.

---

### Post by onesojourner on 2005-11-22
[QUOTE=Dr. Nick]Could you post the output of ```
cat /etc/network/interfaces
```
I dont see it anywhere in this thread.
[/QUOTE]

I typed this in terminal (is that what you meant?) and it says noch such file or directory

[QUOTE=Dr. Nick]


Run ```
iwlist scan
``` and see what it says.
[/QUOTE]

lo interface doesn't support scanning
wlan0 no scan results
sit0 interface dosn't support scanning

---

### Post by Dr. Nick on 2005-11-22
[QUOTE=onesojourner]I typed this in terminal (is that what you meant?) and it says noch such file or directory
[/QUOTE]

well that could be a problem, yes I meant in a terminal.
Hmm.... Do you have a ethernet connection? Just curious as you should have that file.

I will see if I can dig up a default file that you may be able to make your own

EDIT
Here is an edited version of mine, run sudo gedit /etc/network/interfaces and paste this and then save it after filling in the blanks

```

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

# The primary network interface

iface wlan0 inet dhcp

wireless-essid xxxx
wireless-key xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx





auto wlan0
```

---

### Post by onesojourner on 2005-11-22
nope. wireless is this laptops only hope of getting online.

---

### Post by Dr. Nick on 2005-11-22
OK, just curious on the ethernet since the interfaces file is needed for it aswell as wireless, see edit above and try that

---

### Post by onesojourner on 2005-11-22
Could not save the file "/ect/network/interfaces"

thats what i get when i try to save it.

i just copied it and pasted it just like you have it. is that what you mean by fill in the blanks or did i miss something on there?

---

### Post by Maverick911 on 2005-11-22
[QUOTE=azz]I woudl start from the beginning and go look on the ndiswrapper wiki for the most recent version of the windows driver.  Even if your's works in windows, ndiswrapper is built using (always) the most recent version of the driver.  .[/QUOTE]

Warning! Warning!

I had the latest version of ndiswrapper (1.5) and the latest windows driver downloaded from HP and.....

I spent 3 weeks trying to get the broadcom wireless to work at boot without messing around for 20 minutes with iwconfig, ifconfig, network settings, etc. etc. etc.. Sometimes it would work, sometimes no matter what I did I couldn't get wlan0 running.

I finally fixed it by going back to the ndiswrapper 1.1 that came with ubuntu. My wireless works properly now, so don't assume that the latest version of ndiswrapper is the answer.

Just lettin' ya know

---

### Post by Maverick911 on 2005-11-22
FWI, Here's the /etc/network/interfaces that finally got mine working.

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map wlan0

iface wlan0 inet static
address 192.168.0.3
netmask 255.255.255.0
gateway 192.168.0.1
wireless-essid Wireless100
wireless-key open XXXXXXXXXXXXXXXXXXXXXXXXXX

auto wlan0
```

Note: In System>Administration>Networking there is no way to specify whether or not WEP is open or restricted. Restricted is the default. If you want or need to set it to open you must do it in the interfaces file. I have my router set to open because Windows would drop my connection at regular intervals when it was set to restricted.
Also keep in mind that whenever you change settings in System>Administration>Networking, it will change your interfaces file, so go back and look to see if something you needed was changed.
Make sure your default gateway is set to wlan0 and disable eth0.

Good Luck!

---

### Post by Dr. Nick on 2005-11-22
[QUOTE=onesojourner]Could not save the file "/ect/network/interfaces"

thats what i get when i try to save it.

i just copied it and pasted it just like you have it. is that what you mean by fill in the blanks or did i miss something on there?[/QUOTE]

When I said fill in the blanks I meant just copy/paste it all then replace the X's your ssid and wep phrase. But if you couldnt save the file and you ran sudo infront of gedit I would think something else to be wrong. Did it ever ask you for the password to run it as root? Im not sure why it couldnt save it. :confused: 

Anyone see this happen before? You could try mavericks suggestion but I am not sure if the interfaces file will be created or not

---

### Post by onesojourner on 2005-11-23
ok I logged in as root and then I was allowed to save it. it never asked for a password when I was not root just the error message. Dr. Nick I put in your information so we will see what happens.

---

### Post by az on 2005-11-23
[QUOTE=Maverick911]
I finally fixed it by going back to the ndiswrapper 1.1 that came with ubuntu. My wireless works properly now, so don't assume that the latest version of ndiswrapper is the answer.

Just lettin' ya know[/QUOTE]


I agree.  I would not recommend that anyone recompile ndiswrapper.  The one that ships with ubuntu works fine.  But the windows driver (.INF file) you used in Hoary may need to be updated for it to keep working in Breezy.

---

### Post by onesojourner on 2005-11-23
still dont have it working. any more ideas

---

### Post by Dr. Nick on 2005-11-23
Did you restart after saving the interfaces file? I dont know what else it would be. hopefully someone else can help more

---

### Post by Lambert on 2005-11-23
I briefly ran back through this thread. It looks like you're trying to use ndiswrapper but this card is not using ndiswrapper. It's using the acx_pci driver.

> configuration: broadcast=yes driver=acx_pci multicast=yes wireless=IEEE 802.11b+/g+


1. Why are you using ndiswrapper? 

Here is my suggestion. 

1. If you want to use ndiswrapper then use this command.

```
sudo modprobe -r acx_pci
```

Then add acx_pci to the black list with this command

```
echo acx_pci >> /etc/modprobe.d/blacklist
```

At this point just reboot the machine.

Check for driver/hardware with 

```
ndiswrapper -l
```

Then make sure the module is loaded

```
lsmod | grep ndis
```

Then go into  networking and try to set up your network info and connect.

If you don't connect then post back the out put of

```
iwconfig
and 
ifconfig
```

2. You can also try with the native driver instead of ndiswrapper. If so ignore all steps above in 1.

```
sudo modprobe -r ndiswrapper
then
sudo ndiswrapper -e <driver>

```

Then go in to /etc/network/interfaces and remove ndiswrapper from there. Reboot.

try to connect now through networking.

What looks to be the problem is driver conflict. acx_pci is loaded and allocated to the device but you're also adding another driver in the mix through ndiswrapper.

What ever option you do post back with what you're trying, and as much other detail you can think of.

If you get stuck, there is a link in the bottom of my signature wireless troubleshootingguide. It's an incomplete guide/work in progress but you can look there to see if you can solve your problem.

In one of the commands to reply to me earlier you used Ispci. Note all commands in linux are lower case. this is actually a lower case L not a captital I.

---

### Post by onesojourner on 2005-11-23
[QUOTE=Lambert]
Then add acx_pci to the black list with this command

```
echo acx_pci >> /etc/modprobe.d/blacklist
```

[/QUOTE]

i get no such file or directory


I am not attached to ndiswrapper. I just want the wireless connection to work well.

---

### Post by Lambert on 2005-11-23
Not sure why not but do this then

Hit the keys 

alt+F2

type in 

gksudo nautilus

This puts you in nautilus as super user.

On the left pane click on file system, then click on etc, then on modprobe.d

Look through the files, do you see blacklist? You should see files similar to this.

todd@ubuntu:/etc/modprobe.d$ ls
aliases    arch          bluez              nvidia-kernel-nkc
aliases~   arch-aliases  ibm_acpi.modprobe  thinkpad
alsa-base  **blacklist **    isapnp             toshiba_acpi.modprobe

If not create it by alt+f2 then gksudo gedit and manually add acx_pci to the file. Here is a copy of mine.

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# watchdog drivers should be loaded only if a watchdog daemon is installed
blacklist acquirewdt
blacklist advantechwdt
blacklist alim1535_wdt
blacklist alim7101_wdt
blacklist cpu5wdt
blacklist eurotechwdt
blacklist i8xx_tco
blacklist ib700wdt
blacklist indydog
blacklist machzwd
blacklist mixcomwd
blacklist pcwd
blacklist pcwd_pci
blacklist pcwd_usb
blacklist sbc60xxwdt
blacklist sc1200wdt
blacklist sc520_wdt
blacklist scx200_wdt
blacklist softdog
blacklist w83627hf_wdt
blacklist w83877f_wdt
blacklist wafer5823wdt
blacklist wdt
blacklist wdt_pci

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

---

### Post by onesojourner on 2005-11-23
ok I coppied this in and saved it as acx_pci in the modprobe.d folder. I am rebooting now.

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# watchdog drivers should be loaded only if a watchdog daemon is installed
blacklist acquirewdt
blacklist advantechwdt
blacklist alim1535_wdt
blacklist alim7101_wdt
blacklist cpu5wdt
blacklist eurotechwdt
blacklist i8xx_tco
blacklist ib700wdt
blacklist indydog
blacklist machzwd
blacklist mixcomwd
blacklist pcwd
blacklist pcwd_pci
blacklist pcwd_usb
blacklist sbc60xxwdt
blacklist sc1200wdt
blacklist sc520_wdt
blacklist scx200_wdt
blacklist softdog
blacklist w83627hf_wdt
blacklist w83877f_wdt
blacklist wafer5823wdt
blacklist wdt
blacklist wdt_pci

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

---

### Post by onesojourner on 2005-11-23
still not connected. when I open ndiswrapper i am showing a password that is 20+* long. thats kind of wierd.

---

### Post by onesojourner on 2005-11-26
anyone have any more ideas? should I try a reinstall? seems like I am missing alot of folders I should have.

---

### Post by Dr. Nick on 2005-11-26
A reinstall never hurt anyone :) 
Its up to you, If its a fresh install and you dont have any data to risk losing you may as well reinstall it. If its a "used" and highly configured install you may think twice as It will lose alot of customization.

You do seem to be missing some needed files for some eason so a backup of personal data and a reinstall may help clean it up some.

---

### Post by onesojourner on 2005-11-26
I have done nothing with this computer except try to get the wireless going. so I guess since  my new 5.10 cds came in the mail I might as well do something useful with them.

---

### Post by onesojourner on 2006-01-06
Well I finally got my wireless working. I actually don't know what I did different this time. this is the 3rd ubuntu install on this laptop (with a few other distros in between) and now wireless works like a charm. I must have done something wrong during the other 2 installs, though I don't know what.

---

