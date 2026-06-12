---
title: "Missing WiFi-support for Lenovo Ideapad MIIX 310"
date: 2021-11-21
forum: Hardware
---

### Post by sinolog on 2021-11-21
Hi there from Switzerland

am complete newbie.

after installing ubuntu mate i cannot get wifi to work! i think it doesnt detect it. have read on other sites i should do an update from github. but i cant even plug in my mobile phone with usb tethering activated and connect to internet.

MUCH CONFUSED and any help much APPRECIATED! 

thanks @allU!
sinolog

---

### Post by jeremy31 on 2021-11-21
Can you open terminal and post results for ```
lspci -nnk | grep -iA3 net; dpkg -l | grep linux-modules-extra-$(uname -r)
```

---

### Post by sinolog on 2021-11-21
THANKS for reply. here you go:

ii  linux-modules-extra-5.11.0-16-generic    5.11.0-16.17                                                         amd64        Linux kernel extra modules for version 5.11.0 on 64 bit x86 SMP

---

### Post by jeremy31 on 2021-11-21
Ok, results for ```
lshw -C network
```
Check in BIOS to see if WLAN is enabled as I know I can disable wifi on this Lenovo in BIOS

---

### Post by sinolog on 2021-11-21
cannot see option in bios to disable wifi. there is an option to load default settings though.

result of code:
WARNING: you should run this program as super-user.
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

i truly appreciate your time and help! :-)

---

### Post by tea for one on 2021-11-21
> **sinolog said:**
> 
result of code:
WARNING: you should run this program as super-user.
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

Prefix the command with sudo
```
sudo lshw -C network
```
Type your password and press enter (there will no echo)
Go to advanced reply and copy/paste the output in code tags

---

### Post by sinolog on 2021-11-21
i did that.

it shows (for a few milliseconds) PCi(syfs) ??? and then USB
then both msgs disappear.

---

### Post by jeremy31 on 2021-11-21
See the wireless script link in my signature and post results

---

### Post by sinolog on 2021-11-21
ok. how can i get to the second line and then send both lines as one command? or do i send them individually?

ok. how can i get to the second line and then send both lines as one command? or do i send them individually?


i mean this for example:
[COLOR=#000000]When troubleshooting wireless, it's important that your system is fully updated by opening a terminal, CTRL+ALT+T. Using a wired internet connection, please run:[/COLOR]
[COLOR=#000000]Code:
sudo apt update
sudo apt dist-upgrade[/COLOR]

---

### Post by jeremy31 on 2021-11-21
Copy the entire thing and paste into terminal, all 3 lines at once

---

### Post by sinolog on 2021-11-21
tried to insall pastebinit.

E: Unable to locate package pastebinit

---

### Post by jeremy31 on 2021-11-21
Just try this, one line at a time
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info
chmod +x wireless-info
./wireless-info
```

---

### Post by sinolog on 2021-11-21
its hard to copy and paste because i am on another machine right now that has wifi. otherwise i d have to copy paste it to a usb and "transport it" to other computer thats running ubuntu, but no internet connection. can you please tell me: should i use your method 1 now?

wget -N -t 5 -T 10 [https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info](https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info) && \
chmod +x wireless-info && \
./wireless-info

ok. i will do that. but i will have to type. how can i get to the second command line then? THANKS.&#12290;

ok. sorry. i will try it one line at at time.

---

### Post by jeremy31 on 2021-11-21
You will likely have to follow the offline instructions on the page [https://ubuntuforums.org/showthread.php?t=2082305&p=12350385&viewfull=1#post12350385](https://ubuntuforums.org/showthread.php?t=2082305&p=12350385&viewfull=1#post12350385)

---

### Post by sinolog on 2021-11-21
ok. here is what i entered and what i got as result. i will try method 2 now...:


qiu@qiu-MIIX-310-10ICR:~$ wget -N -t 5 -T 10 [https://github.com/UbuntuForums/wire.../wireless-info](https://github.com/UbuntuForums/wire.../wireless-info) && \
chmod +x wireless-info && \
./wireless-info
--2021-11-21 21:56:43--  [https://github.com/UbuntuForums/wire.../wireless-info](https://github.com/UbuntuForums/wire.../wireless-info)
Resolving github.com (github.com)... failed: Temporary failure in name resolution.
wget: unable to resolve host address ‘github.com’

---

### Post by sinolog on 2021-11-21
didnt quite get explanation.

have tried this:


[COLOR=#000000]If you can't connect to internet -[/COLOR]

[COLOR=#000000]* Download the script on another computer by right-clicking [/COLOR][this link]("https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info")[COLOR=#000000], and choose to "Save" the link target.[/COLOR]
[COLOR=#000000]* [/COLOR][B]Copy the downloaded file to your Ubuntu Desktop (see the "NOTE 2" below) and,
* run it from there as follows -

**1)** Right-click the downloaded file > click "Properties" > go to "Permissions" tab > tick the "Execute" checkbox > close the box.

first i copied all the text into a TXT-file and put into ubuntu-lenovo and tried to -- permissions--allow executing file as program. but check box wont let me. then i have also tried to only save the link as target with the same result (which doesnt make sense to me bc no internet and therefore no link to follow on ubuntu...

awaiting further instructions...:-/
[/B]

---

### Post by sinolog on 2021-11-21
could you maybe instruct me how to establish an internet connection with usb-tethering with my google pixel 5. that might make things easier to download the driver directly...

---

### Post by sinolog on 2021-11-21
i have tried this before but to no avail...

---

### Post by jeremy31 on 2021-11-21
Open terminal and enter one line at a time
```
cd Desktop
ls -al | grep wireless
```
Post result

---

### Post by sinolog on 2021-11-21
nothing happened.
shows only "changed to desktop"

qiu@qiu-MIIX-310-10ICR:~/Desktop$ (Desktop in light blue)

---

### Post by jeremy31 on 2021-11-21
Where did you put that file and what is it named?

---

### Post by sinolog on 2021-11-21
AH. i havent put it on the desktop. i have now. its called ubuntu2.txt. now i can make it "executing file as program"

---

### Post by jeremy31 on 2021-11-21
in terminal ```
cd Desktop
mv ubuntu2.txt wireless-info
chmod +x wireless-info
./wireless-info
```
Hopefully it will work and create a wireless-info.txt file copy the wireless-info.txt back to the computer with internet and paste the contents in code tags

---

### Post by sinolog on 2021-11-21
```
########## wireless info START ##########


Report from: 21 Nov 2021 22:41 CET +0100


Booted last: 21 Nov 2021 00:00 CET +0100


Script from: 25 Jan 2020 03:34 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 21.04
Release:	21.04
Codename:	hirsute


##### kernel ############################


Linux 5.11.0-16-generic #17-Ubuntu SMP Wed Apr 14 20:12:43 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash


##### desktop ###########################


MATE


##### lspci #############################


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 009: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 001 Device 005: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 001 Device 006: ID 258a:1015 SIPODEV USB Composite Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no


##### secure boot #######################


SecureBoot enabled


##### lsmod #############################


snd_soc_sst_cht_bsw_rt5645    28672  3
snd_soc_acpi           16384  4 snd_soc_acpi_intel_match,snd_sof_intel_byt,snd_intel_sst_acpi,snd_soc_sst_cht_bsw_rt5645
snd_soc_rt5645        172032  2 snd_soc_sst_cht_bsw_rt5645
snd_soc_rl6231         20480  1 snd_soc_rt5645
snd_soc_core          294912  5 soundwire_intel,snd_sof,snd_soc_sst_atom_hifi2_platform,snd_soc_rt5645,snd_soc_sst_cht_bsw_rt5645
cfg80211              892928  0
snd_pcm               118784  11 soundwire_intel,snd_sof,snd_sof_intel_ipc,snd_compress,snd_hdmi_lpe_audio,snd_soc_sst_atom_hifi2_platform,snd_soc_core,snd_soc_rt5645,snd_soc_sst_cht_bsw_rt5645,snd_pcm_dmaengine


##### interfaces ########################


[/etc/network/interfaces]
source-directory /etc/network/interfaces.d


##### ifconfig ##########################


1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd <MAC address>
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever


##### iwconfig ##########################


lo        no wireless extensions.


##### route #############################


##### resolv.conf #######################


[777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']


nameserver 127.0.0.53
options edns0 trust-ad
search .


##### network managers ##################


Installed:


	NetworkManager


Running:


root         594       1  0 21:23 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true


##### NetworkManager config #############


[[/etc/NetworkManager/conf.d/default-wifi-powersave-on.conf]]
[connection]
wifi.powersave = 3


[[/etc/NetworkManager/NetworkManager.conf]]
[main]
plugins=ifupdown,keyfile
[ifupdown]
managed=false
[device]
wifi.scan-rand-mac-address=no


[[/usr/lib/NetworkManager/conf.d/10-dns-resolved.conf]]
[main]
dns=systemd-resolved


[[/usr/lib/NetworkManager/conf.d/10-globally-managed-devices.conf]]
[keyfile]
unmanaged-devices=*,except:type:wifi,except:type:gsm,except:type:cdma


[[/usr/lib/NetworkManager/conf.d/no-mac-addr-change.conf]]
[device-31-mac-addr-change]
match-device=driver:eagle_sdio,driver:wl
wifi.scan-rand-mac-address=no


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/Wi-Fi connection 1.nmconnection]] (600 root)
[connection] id=Wi-Fi connection 1 | type=wifi | permissions=
[wifi] mac-address-blacklist= | ssid=WWWVisitor
[ipv4] method=auto
[ipv6] method=auto


##### Netplan config ####################


[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager


##### iw reg get ########################


Region: Europe/Berlin (based on set time zone)


global
country 00: DFS-UNSET
	(2402 - 2472 @ 40), (N/A, 20), (N/A)
	(2457 - 2482 @ 20), (N/A, 20), (N/A), AUTO-BW, PASSIVE-SCAN
	(2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, PASSIVE-SCAN
	(5170 - 5250 @ 80), (N/A, 20), (N/A), AUTO-BW, PASSIVE-SCAN
	(5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, AUTO-BW, PASSIVE-SCAN
	(5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, PASSIVE-SCAN
	(5735 - 5835 @ 80), (N/A, 20), (N/A), PASSIVE-SCAN
	(57240 - 63720 @ 2160), (N/A, 0), (N/A)


##### iwlist channels ###################


lo        no frequency information.


##### iwlist scan #######################


lo        Interface doesn't support scanning.


##### module infos ######################


[cfg80211]
filename:       /lib/modules/5.11.0-16-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       5.11.0-16-generic SMP mod_unload modversions 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[cfg80211]
bss_entries_limit: 1000
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


##### /etc/modules ######################


##### modprobe options ##################


[/etc/modprobe.d/amd64-microcode-blacklist.conf]
blacklist microcode


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac


[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off


[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode


[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


##### rc.local ##########################


grep: /etc/rc.local: No such file or directory


##### pm-utils ##########################


##### udev rules ########################


##### dmesg #############################


########## wireless info END ############
```

---

### Post by sinolog on 2021-11-21
ok. finally. MY bad...:/

---

### Post by sinolog on 2021-11-21
```


########## wireless info START ##########


Report from: 21 Nov 2021 22:41 CET +0100


Booted last: 21 Nov 2021 00:00 CET +0100


Script from: 25 Jan 2020 03:34 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 21.04
Release:	21.04
Codename:	hirsute


##### kernel ############################


Linux 5.11.0-16-generic #17-Ubuntu SMP Wed Apr 14 20:12:43 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash


##### desktop ###########################


MATE


##### lspci #############################


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 009: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 001 Device 005: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 001 Device 006: ID 258a:1015 SIPODEV USB Composite Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no


##### secure boot #######################


SecureBoot enabled


##### lsmod #############################


snd_soc_sst_cht_bsw_rt5645    28672  3
snd_soc_acpi           16384  4 snd_soc_acpi_intel_match,snd_sof_intel_byt,snd_intel_sst_acpi,snd_soc_sst_cht_bsw_rt5645
snd_soc_rt5645        172032  2 snd_soc_sst_cht_bsw_rt5645
snd_soc_rl6231         20480  1 snd_soc_rt5645
snd_soc_core          294912  5 soundwire_intel,snd_sof,snd_soc_sst_atom_hifi2_platform,snd_soc_rt5645,snd_soc_sst_cht_bsw_rt5645
cfg80211              892928  0
snd_pcm               118784  11 soundwire_intel,snd_sof,snd_sof_intel_ipc,snd_compress,snd_hdmi_lpe_audio,snd_soc_sst_atom_hifi2_platform,snd_soc_core,snd_soc_rt5645,snd_soc_sst_cht_bsw_rt5645,snd_pcm_dmaengine


##### interfaces ########################


[/etc/network/interfaces]
source-directory /etc/network/interfaces.d


##### ifconfig ##########################


1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd <MAC address>
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever


##### iwconfig ##########################


lo        no wireless extensions.


##### route #############################


##### resolv.conf #######################


[777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']


nameserver 127.0.0.53
options edns0 trust-ad
search .


##### network managers ##################


Installed:


	NetworkManager


Running:


root         594       1  0 21:23 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true


##### NetworkManager config #############


[[/etc/NetworkManager/conf.d/default-wifi-powersave-on.conf]]
[connection]
wifi.powersave = 3


[[/etc/NetworkManager/NetworkManager.conf]]
[main]
plugins=ifupdown,keyfile
[ifupdown]
managed=false
[device]
wifi.scan-rand-mac-address=no


[[/usr/lib/NetworkManager/conf.d/10-dns-resolved.conf]]
[main]
dns=systemd-resolved


[[/usr/lib/NetworkManager/conf.d/10-globally-managed-devices.conf]]
[keyfile]
unmanaged-devices=*,except:type:wifi,except:type:gsm,except:type:cdma


[[/usr/lib/NetworkManager/conf.d/no-mac-addr-change.conf]]
[device-31-mac-addr-change]
match-device=driver:eagle_sdio,driver:wl
wifi.scan-rand-mac-address=no


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/Wi-Fi connection 1.nmconnection]] (600 root)
[connection] id=Wi-Fi connection 1 | type=wifi | permissions=
[wifi] mac-address-blacklist= | ssid=WWWVisitor
[ipv4] method=auto
[ipv6] method=auto


##### Netplan config ####################


[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager


##### iw reg get ########################


Region: Europe/Berlin (based on set time zone)


global
country 00: DFS-UNSET
	(2402 - 2472 @ 40), (N/A, 20), (N/A)
	(2457 - 2482 @ 20), (N/A, 20), (N/A), AUTO-BW, PASSIVE-SCAN
	(2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, PASSIVE-SCAN
	(5170 - 5250 @ 80), (N/A, 20), (N/A), AUTO-BW, PASSIVE-SCAN
	(5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, AUTO-BW, PASSIVE-SCAN
	(5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, PASSIVE-SCAN
	(5735 - 5835 @ 80), (N/A, 20), (N/A), PASSIVE-SCAN
	(57240 - 63720 @ 2160), (N/A, 0), (N/A)


##### iwlist channels ###################


lo        no frequency information.


##### iwlist scan #######################


lo        Interface doesn't support scanning.


##### module infos ######################


[cfg80211]
filename:       /lib/modules/5.11.0-16-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       5.11.0-16-generic SMP mod_unload modversions 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[cfg80211]
bss_entries_limit: 1000
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


##### /etc/modules ######################


##### modprobe options ##################


[/etc/modprobe.d/amd64-microcode-blacklist.conf]
blacklist microcode


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac


[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off


[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode


[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


##### rc.local ##########################


grep: /etc/rc.local: No such file or directory


##### pm-utils ##########################


##### udev rules ########################


##### dmesg #############################


########## wireless info END ############



```

---

### Post by jeremy31 on 2021-11-21
Check BIOS settings, no wifi device at all discovered

---

### Post by sinolog on 2021-11-21
i dont see an option with wifi in bios. i selected LOAD DEFAULT SETTINGS. shall i generate wifi-info again?

---

### Post by sinolog on 2021-11-21
i did LOAD DEFAULT SETTINGS and fiddled with top right wifi-connections symbol. now cursor froze. will restart

---

### Post by jeremy31 on 2021-11-21
You don't see a screen like this in BIOS [https://youtu.be/pC07Rv--Pf8?t=17](https://youtu.be/pC07Rv--Pf8?t=17) the video shows the Wireless LAN setting at 16 seconds

---

### Post by sinolog on 2021-11-21
my bios looks completely different. i know that one displayed from my yoga. but mine looks different. i ll try to post a pic

---

### Post by sinolog on 2021-11-21
[https://photos.app.goo.gl/14cGYkJU5RndxFBB8](https://photos.app.goo.gl/14cGYkJU5RndxFBB8)

---

### Post by sinolog on 2021-11-21
wow. suddenly wifi networks are available. have no idea why it is working now.

i ll try it out and keep you posted. as i said: there was no wifi-option in bios per se...

thanks so far and i am sure i will need more help. haha.

---

### Post by sinolog on 2021-11-21
thanks a lot jeremy. how can i return the favour? would you like a postcard from switzerland? you can write me your address in a pn. very happy that it worked. for whatever reason. and now i can use this old machine with 20 gigs of free disk space and it works like a charm instead of being stuck with high ressource-consuming windows 10.

you gave my ideapad a second life (sic - metaverse:-) 

THANKS FOR THAT!

---

### Post by jeremy31 on 2021-11-21
Enjoy, no postcard needed

---

