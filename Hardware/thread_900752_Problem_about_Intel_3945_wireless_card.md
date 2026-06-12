---
title: "Problem about Intel 3945 wireless card"
date: 2008-08-25
forum: Hardware
---

### Post by jasonkirk2006 on 2008-08-25
I have been trying to enable my Intel PRO/Wireless 3945ABG/BG card for some time. At the beginning, with default Ubuntu 8.04 (x64) configuration, I was getting this from dmesg:

```

...
iwl3945 : MAC is in deep sleep
iwl3945 : Unable to int nic
...

```

Then I applied updates and kernel version raised to 2.6.24-19. Also I have added noapic kernel option. Now, the result of dmesg |*grep 3945 is:

```

[   34.378207] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.25
[   34.378209] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   34.379070] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   34.591479] wmaster0: Selected rate control algorithm 'iwl-3945-rs'
[   41.640309] iwl3945: Tunable channels: 13 802.11bg, 23 802.11a channels

```

But there is no wireless signals received. Network Manager WLAN list is empty and I get the following :

```

# iwconfig wlan0
wlan0     IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

# iwlist wlan0 scan
wlan0     No scan results

```

Could anyone please help me in getting my 3945 card work? I have no problem with the default Vista configuration that came with my laptop. It sees the wireless networks around me. But I want to use Ubuntu.

---

### Post by Crafty Kisses on 2008-08-25
Please let me see:

```
dmesg | grep Wireless 
```

Let's see if we can see what's going wrong here.

The others of you, we will be very glad to help if we know what we are trying to fix. We are not familiar with every laptop ever made, nor are we going to try to guess which of two or three wireless cards you have that were supplied in your lappy. Simply run:
```

sudo lshw | grep Wireless
```You might see something like this:
```

chili@LAPTOP60:~$ sudo lshw | grep Wireless
[sudo] password for chili: 
description: Wireless interface
product: PRO/Wireless 3945ABG Network Connection
``` 

Now we know what we are trying to fix! If you have a 3945ABG, you might try:

```

 sudo apt-get install linux-backports-modules-hardy-generic
``` Let's see if your 3945ABG springs to life.

If you have any problems, tell us about it.

---

### Post by dideriksen on 2008-08-25
> **jasonkirk2006 said:**
> I have been trying to enable my Intel PRO/Wireless 3945ABG/BG card for some time. At the beginning, with default Ubuntu 8.04 (x64) configuration, I was getting this from dmesg:

```

...
iwl3945 : MAC is in deep sleep
iwl3945 : Unable to int nic
...

```

Then I applied updates and kernel version raised to 2.6.24-19. Also I have added noapic kernel option. Now, the result of dmesg |*grep 3945 is:

```

[   34.378207] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.25
[   34.378209] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   34.379070] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   34.591479] wmaster0: Selected rate control algorithm 'iwl-3945-rs'
[   41.640309] iwl3945: Tunable channels: 13 802.11bg, 23 802.11a channels

```

But there is no wireless signals received. Network Manager WLAN list is empty and I get the following :

```

# iwconfig wlan0
wlan0     IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

# iwlist wlan0 scan
wlan0     No scan results

```

Could anyone please help me in getting my 3945 card work? I have no problem with the default Vista configuration that came with my laptop. It sees the wireless networks around me. But I want to use Ubuntu.


Maybe you should try to connect the antenna somware with pressing a button.

---

### Post by jasonkirk2006 on 2008-08-25
Thank you for your reply, Codename.

Here is the info you requested:

```

# dmesg | grep -i Wireless
[   36.536284] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.25
[   36.537128] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection

```

Also:

```

# sudo lshw | grep -i Wireless
                description: Wireless interface
                product: PRO/Wireless 3945ABG Network Connection
                capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g


```

And finally:

```

# lsmod | grep 3945
iwl3945               104820  0 
iwlwifi_mac80211      251876  1 iwl3945
led_class               7176  1 iwl3945

```

There should be no need for an external antenna, i guess. And my wireless switch is on.

---

### Post by Crafty Kisses on 2008-08-25
Now let's take a look at:
```

sudo iwlist wlan0 scan
```Also do you have any encryption; WPA, WEP, etc.? Please have those details at your fingertips as we proceed. Do not post your key or password unless it's obscured: 092*******3, for example.

---

### Post by IntuitiveNipple on 2008-08-25
"MAC is in deep sleep" is usually an indication the firmware files haven't loaded. The files are:
```

$ ls -1 /lib/firmware/$(uname -r)/iwl*
/lib/firmware/2.6.24-21-generic/iwlwifi-3945-1.ucode
/lib/firmware/2.6.24-21-generic/iwlwifi-3945.ucode
/lib/firmware/2.6.24-21-generic/iwlwifi-4965-1.ucode
/lib/firmware/2.6.24-21-generic/iwlwifi-4965.ucode

```
That issue seems to have been overcome, but the symptoms you describe sound very much like the radio kill-switch is activated. To check the device is present:
```

$ lshal | awk '$0 ~ /^udi = .*/ {show=0} $0 ~ /^udi = .*ipw_wlan_switch.*/ { show=1} show == 1 {print $0}'
 
udi = '/org/freedesktop/Hal/devices/ipw_wlan_switch'
  info.capabilities = {'killswitch'} (string list)
  info.category = 'killswitch'  (string)
  info.interfaces = {'org.freedesktop.Hal.Device.KillSwitch'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_4222'  (string)
  info.product = 'Intel PRO/Wireless WLAN Switch'  (string)
  info.subsystem = 'unknown'  (string)
  info.udi = '/org/freedesktop/Hal/devices/ipw_wlan_switch'  (string)
  killswitch.access_method = 'ipw'  (string)
  killswitch.type = 'wlan'  (string)
  org.freedesktop.Hal.Device.KillSwitch.method_argnames = {'power', ''} (string list)
  org.freedesktop.Hal.Device.KillSwitch.method_execpaths = {'hal-system-killswitch-set-power', 'hal-system-killswitch-get-power'} (string list)
  org.freedesktop.Hal.Device.KillSwitch.method_names = {'SetPower', 'GetPower'} (string list)
  org.freedesktop.Hal.Device.KillSwitch.method_signatures = {'b', ''} (string list)

```

Check if the RF Kill-switch is active (radio is off):
```

$ find /sys -type f -name 'rf_kill' -exec cat {} \;
0

```
0 == not killed (radio power on)
1 == killed (radio power off)

---

### Post by jasonkirk2006 on 2008-08-26
Codename,

I wrote the output of iwlist in my first post - without sudo.

```
# iwlist wlan0 scan
wlan0     No scan results
```

Do i need to be root for iwlist? If my wireless works by chance, i can get output from iwlist without being root. My computer is not with me right now. I will try it and write the output here as soon as possible.

---

And IntuitiveNipple, thanks for your reply too.

How can i make sure that firmware files are loaded at all times? Or understand that they are loaded or not?

My computer has a hardware switch that controls wireless and bluetooth functions. I guess this is the radio kill switch you mentioned. I'm quite sure this switch was physically in the "on" position, when i did my tests. But anyway, i will try your code as soon as i get back to my computer - i'm away from it right now.

---

### Post by Crafty Kisses on 2008-08-26
Yeah you can try > sudo iwlist wlan0 scan

---

### Post by MONODA on 2008-08-26
i have the same card and I needed to add the file /etc/modprobe.d/iwl3945 with contents > alias wlan0 iwl3945
options iwl3945 disable_hw_scan=1 hwcrypto=1 if the file /etc/modprobe.d/ipw3945 exists, delete it. then reboot.

---

### Post by jasonkirk2006 on 2008-08-27
Sorry for the delay. I will post my reply tonight.

---

### Post by chappejw on 2008-08-27
Here is a solution to get your Intel ipw3945 wireless card working. :guitar:

The driver used to be in this package, **linux-restricted-modules-generic**, and it contained an updated firmware for that wireless card. However, this driver is now replaced with the iwl3945 found here: [http://linuxwireless.org/en/users/Drivers/iwl3945](http://linuxwireless.org/en/users/Drivers/iwl3945)   RE: Firmware replacement for ipw3945 poses no risk since it is loaded at runtime. Once you have that package your network manager should detect available networks and allow you to configure everything without a glitch. Let me know if that solves your issues, I have delt with this card extensively on Debian and Ubuntu.

---

### Post by jasonkirk2006 on 2008-08-28
Now, i'm back with my laptop. Sorry for the delay.

To IntuitiveRipple:

I'm using kernel version 2.6.24-19 so

```

$ ls -1 /lib/firmware/$(uname -r)/iwl*
/lib/firmware/2.6.24-19-generic/iwlwifi-3945-1.ucode
/lib/firmware/2.6.24-19-generic/iwlwifi-3945.ucode
/lib/firmware/2.6.24-19-generic/iwlwifi-4965-1-lbm.ucode
/lib/firmware/2.6.24-19-generic/iwlwifi-4965-1.ucode
/lib/firmware/2.6.24-19-generic/iwlwifi-4965.ucode

```

Unfortunately, the following line gives nothing

```
$ lshal | awk '$0 ~ /^udi = .*/ {show=0} $0 ~ /^udi = .*ipw_wlan_switch.*/ { show=1} show == 1 {print $0}'

```

But when i dumped the output of lshal to a text file, i recognized two parts of it to be similar to your output:

```

udi = '/org/freedesktop/Hal/devices/dell_wlan_switch'
  info.capabilities = {'killswitch'} (string list)
  info.category = 'killswitch'  (string)
  info.interfaces = {'org.freedesktop.Hal.Device.KillSwitch'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/platform_dcdbas'  (string)
  info.product = 'Dell WLAN Switch'  (string)
  info.subsystem = 'unknown'  (string)
  info.udi = '/org/freedesktop/Hal/devices/dell_wlan_switch'  (string)
  killswitch.access_method = 'dell'  (string)
  killswitch.type = 'wlan'  (string)
  org.freedesktop.Hal.Device.KillSwitch.method_argnames = {'power', ''} (string list)
  org.freedesktop.Hal.Device.KillSwitch.method_execpaths = {'hal-system-killswitch-set-power', 'hal-system-killswitch-get-power'} (string list)
  org.freedesktop.Hal.Device.KillSwitch.method_names = {'SetPower', 'GetPower'} (string list)
  org.freedesktop.Hal.Device.KillSwitch.method_signatures = {'b', ''} (string list)

```

and

```
udi = '/org/freedesktop/Hal/devices/net_00_1f_3c_13_84_cd'
  info.capabilities = {'net', 'net.80211'} (string list)
  info.category = 'net.80211'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_4222'  (string)
  info.product = 'WLAN Interface'  (string)
  info.udi = '/org/freedesktop/Hal/devices/net_00_1f_3c_13_84_cd'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'net'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.1/0000:0b:00.0/net/wlan0'  (string)
  net.80211.mac_address = 134151898317  (0x1f3c1384cd)  (uint64)
  net.address = '00:1f:3c:13:84:cd'  (string)
  net.arp_proto_hw_id = 1  (0x1)  (int)
  net.interface = 'wlan0'  (string)
  net.linux.ifindex = 4  (0x4)  (int)
  net.originating_device = '/org/freedesktop/Hal/devices/pci_8086_4222'  (string)
  net.physical_device = '/org/freedesktop/Hal/devices/pci_8086_4222'  (string)

```

It seems i have this switch. And the output of this line is zero, which means radio power is on (not killed).

```
$ find /sys -type f -name 'rf_kill' -exec cat {} \;
0
```

---

To Codename,

sudo iwlist sometimes gives

```
$ sudo iwlist wlan0 scan
wlan0     No scan results

```

and sometimes gives
```
$ sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning : Network is down

```

And when my wireless card works without any problem (this happen from time to time), both with and without sudo, iwlist correctly lists wireless networks aroun me.

---

To MONODA,

As for the /etc/modprobe.d/iwl3945 file, this modification gives me a very unstable system. 
Mouse freezes frequently, keyboard hits appear on screen with a large delay, and Rhytimbox hangs when playing mp3s on NTFS partitions. 
System Monitor says pulseaudio (and mount.ntfs-3g) consumes all the CPU cycles. But yes, when i managed to boot with this setting twice, wireless worked.

Unfortunately, i still have problems with this card and want to fix it. Any more suggestions?

---

### Post by jasonkirk2006 on 2008-08-29
> **chappejw said:**
> Here is the solution to get your Intel ipw3945 wireless card working. :guitar:

Make sure you have the package **linux-restricted-modules-generic** installed. This package contains the updated firmware for that wireless card. Compiling and installing it yourself is always a tedious operation. Note: replacing the firmware for this card poses no risk since it is loaded at runtime. Once you have that package your network manager should detect available networks and allow you to configure everything without a glitch. Let me know if that solves your issues, I have delt with this card extensively.

I'm running kernel 2.6.24-19. So i have the following packages installed :

```

linux-backports-modules-2.6.24-19-generic (version 2.6.24.19.17)
linux-restricted-modules-generic (version 2.6.24.19.21)

```

And I still have the same problem. Backports module is supposed to end my wifi led problem. But i still have this led off when the radio switch is on. I really appreciate any help.

---

### Post by jasonkirk2006 on 2008-08-31
I have seen on some of the threads that people talk about Gutsy being very good with 3945 wireless business. Some of them very sorry since they have upgraded to Hardy, which by default offers iwl3945 - new drivers.

I tried Ubuntu 7.10 x32 live and the symptoms were very similar. Unfortunately ipw3945 driver didn't work either. Here are some diagnosis:

dmesg 
```

$ dmesg | grep 3945
[  153.092000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.2mp.ubuntu1
[  153.092000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[  153.092000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
**[  155.664000] ipw3945: MAC is in deep sleep!**
[  159.464000] ipw3945: Unable to int nic

```

lshw
```

$ sudo lshw -C network
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:1d:09:3e:4d:73
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.18 duplex=full firmware=N/A ip=192.168.7.2 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 02
       **serial: ff:ff:ff:ff:ff:ff**
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=ipw3945 latency=0 module=ipw3945

```

iwconfig
```

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```

ifconfig
```

$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1D:09:3E:4D:73  
          inet addr:192.168.7.2  Bcast:192.168.7.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:9ff:fe3e:4d73/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:34 errors:0 dropped:0 overruns:0 frame:0
          TX packets:46 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2452 (2.3 KB)  TX bytes:5035 (4.9 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

finally lsmod
```

$ lsmod |*grep 3945
ipw3945               119840  1 
ieee80211              35656  1 ipw3945
```

Since there is no problem with Vista, i don't think that this is neither hardware nor BIOS/firmware problem. This must be something about linux kernel or wireless driver problem.

Any suggestions? Clean install? Trying 32-bit install instead of 64-bit? Or else?

---

### Post by Blackcabs on 2008-09-01
I am using Hardy 64 on a Brand new Acer travelmate 5720 that came with vista installed,, It has the same card as yours and worked fine on first boot.Personally i always think its a good idea to run the live cd first just to see if there are going to be any potental hardware problems.Don't quote me on this,, but im pretty sure that the default install uses the ipw3945 driver as mine did,, although i changed to the iwl3945 driver using the Compat-wireless testing git no problems. I really dont know what is going on with this card as alot of people are having problems

You try enabling the mac manually 
Networking  --->
  Wireless  --->
    <M> Improved wireless configuration API
    <M> Generic IEEE 802.11 Networking Stack (mac80211)

---

### Post by jo.cisco on 2008-09-01
> **MONODA said:**
> i have the same card and I needed to add the file /etc/modprobe.d/iwl3945 with contents  if the file /etc/modprobe.d/ipw3945 exists, delete it. then reboot.

thx this worked for me :D

---

### Post by jasonkirk2006 on 2008-09-02
> **Blackcabs said:**
> I am using Hardy 64 on a Brand new Acer travelmate 5720 that came with vista installed,, It has the same card as yours and worked fine on first boot.Personally i always think its a good idea to run the live cd first just to see if there are going to be any potental hardware problems.Don't quote me on this,, but im pretty sure that the default install uses the ipw3945 driver as mine did,, although i changed to the iwl3945 driver using the Compat-wireless testing git no problems. I really dont know what is going on with this card as alot of people are having problems

You try enabling the mac manually 
Networking  --->
  Wireless  --->
    <M> Improved wireless configuration API
    <M> Generic IEEE 802.11 Networking Stack (mac80211)

Thanks for your reply, Blackcabs,

In fact, wireless card ran fine at first boot with live cd. But the problem came afterwards. Anyway, i would still install Hardy, even if the wireless didn't work at first. It's linux! There has to be a solution :)

As for the ipw3945 driver, are you sure you are saying that Ubuntu 8.04 x64 edition came with ipw3945 instead of iwl3945? If so, it's something new and i never met such a thing. In many places i have read that Hardy uses the new (iwl) driver.

Anyway, what you wrote about enabling the MAC manually is something about kernel modification (or recompilation), right? I will try it - though i'm not qualified right now :confused:

---

### Post by jasonkirk2006 on 2008-09-02
> **jo.cisco said:**
> thx this worked for me :D

Hey, are you sure it works after several reboots? What is your brand and model? Do you think there are any side effects? (like i mentioned in my old posts - temporary freezes and high CPU utilizations)

---

### Post by IntuitiveNipple on 2008-09-02
Jason, because you've been trying so much, could you attach the latest /var/log/dmesg (you'll probably need to compress it as .gz).

I just want to be sure we're all thinking about the same hardware/kernel version configuration since you've tried so many :)

The outputs seem to show the device is alive but hiding.

This Vaio has the same 3945ABG and I've never had any issues with it, either with the ipw3945 driver under Gutsy or the new iwl3945 driver on Hardy and Intrepid.
```

06:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG Network Connection [8086:4222] (rev 02)

```

---

### Post by jasonkirk2006 on 2008-09-02
> **IntuitiveNipple said:**
> Jason, because you've been trying so much, could you attach the latest /var/log/dmesg (you'll probably need to compress it as .gz).

I just want to be sure we're all thinking about the same hardware/kernel version configuration since you've tried so many :)

The outputs seem to show the device is alive but hiding.

This Vaio has the same 3945ABG and I've never had any issues with it, either with the ipw3945 driver under Gutsy or the new iwl3945 driver on Hardy and Intrepid.
```

06:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG Network Connection [8086:4222] (rev 02)

```

Thanks, IntuitiveRipple.

Just for test, i was installing OpenSuse 11 64-bit. It was using kernel 2.6.25 and iwl3945. 2 of 5 reboots was problem again.

Now i switched back to Ubuntu 8.04 32-bit clean install (it was 64-bit last time). Both live user before install and the first boot after install was again disaster! Here i attach the several logs from OpenSuse 11 (64-bit) and Ubuntu 8.04 (32-bit). Ubuntu installation currently uses no updates (no backports, no restricted modules, etc.). Because updates changes dmesg logs (now it says "MAC is in deep sleep" and after updates it may say microcode error or insufficient power etc.)

Again when i boot Vista, no problem there.

Hope you find something :(

---

### Post by jo.cisco on 2008-09-02
> **jasonkirk2006 said:**
> Hey, are you sure it works after several reboots? What is your brand and model? Do you think there are any side effects? (like i mentioned in my old posts - temporary freezes and high CPU utilizations)

it worked from first reboot, and it connected to my WPA encrypted network. i'm running on a Lenovo 3000 N100 with a centrino duo CPU, and 1 gig RAM, not sure if u need any more into. no side effects experienced so far CPU utilization seems fine on both cores and i dont have any wireless related freezes or anything.

---

### Post by jasonkirk2006 on 2008-09-03
I want to ask (i hope) a last thing to those of you which have problems with this funny 3945abg card. May you be using your laptop on AC power and without batteries? I'll be glad if you reply here.

---

### Post by IntuitiveNipple on 2008-09-03
> **jasonkirk2006 said:**
> ...now it says "MAC is in deep sleep" and after updates it may say microcode error or insufficient power etc.)

If you can manage, don't install any kernel updates for now - keep it with this error so I can track the changes as we go.

I've been examining the log-files. We're helped by the fact the same card is in this Sony Vaio I'm using so we can compare results between them.

First thing I want to double-check is the actual PCI device ID since the lspci reports you provided didn't use the -nn option they aren't shown. I want to be absolutely sure we're dealing with the device we think we are! Here's the beginning of the output for this one:
```
sudo lspci -s 06:00.0 -vvvnn

06:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG Network Connection [8086:4222] (rev 02)
	Subsystem: Intel Corporation Unknown device [8086:1051]

```
It's the 8086:4222 I'm interested in for now.

Also, there is a bug report for what seems to be the same issue so please add a comment to it so we can track the issue more easily: "[iwl3945 can't wake up Intel(R) PRO/Wireless 3945 mini card](https://bugs.launchpad.net/+bug/203329)"

---

### Post by IntuitiveNipple on 2008-09-03
Jason, can you capture a boot log without the kernel command-line option "quiet" so we can get more detailed reports in /var/log/dmesg ?

You should be able to do that manually by interrupting GrUB as it starts, and then editing the menu option's entry by deleting "quiet splash" from the line that starts "kernel" and then, after pressing Enter, pressing B to boot with that entry.

Also, what make and model is the PC? This error seems to be more frequent with Dell models in the reports I've seen.

---

### Post by IntuitiveNipple on 2008-09-03
I'm getting a feeling this is caused by a problem with the Kill Switch as I first thought.

In the log-file you provided I noticed:
```

ubu32 kernel: [   36.576191] atkbd.c: Spurious ACK on isa0060/serio0. Some program might be trying access hardware directly.
ubu32 kernel: [   36.772058] atkbd.c: Unknown key pressed (translated set 2, code 0x0 on isa0060/serio0).
ubu32 kernel: [   36.772061] atkbd.c: Use 'setkeycodes 00 <keycode>' to make it known.
ubu32 kernel: [   36.775036] atkbd.c: Spurious ACK on isa0060/serio0. Some program might be trying access hardware directly.
ubu32 kernel: [   36.975457] atkbd.c: Spurious ACK on isa0060/serio0. Some program might be trying access hardware directly.

```
And I found some bug reports for other distributions that link this to the failure of the 3945.

So, let's try to discover if the failure to read the Kill Switch correctly could be causing this. Do this ***after*** you've removed the "quiet splash" options from the kernel command-line so we see more details.

With the PC switched off ensure the radio kill-switch is in the **on** position. Start the PC and let it boot. Log-in. From a command prompt start a log-monitor and then move the radio kill-switch to **off**. 

You should see a few messages reported. When they stop give it a second or two then move the switch back to **on**. There should be a few more messages. When they've stopped copy the messages to a reply here:
[code]
tail -f /var/log/kern.log

---

### Post by IntuitiveNipple on 2008-09-03
If you're using a Dell this might be a solution:

> 
Go to bios (F2 at Dell splash screen) on 'Wireless' go to 'Wi-Fi Catcher' and switch it to 'OFF'.

(From the thread "[Dell XPS M1530 wireless problems](http://ubuntuforums.org/showpost.php?p=5158330&postcount=10)")

If you find this helps add a comment to this bug report "[[XPS M1530] Wireless don't work (need to use 'noapic' kernel boot param)](https://bugs.launchpad.net/dell/+bug/190664)"

---

### Post by jasonkirk2006 on 2008-09-03
> **IntuitiveNipple said:**
> If you can manage, don't install any kernel updates for now - keep it with this error so I can track the changes as we go.

I've been examining the log-files. We're helped by the fact the same card is in this Sony Vaio I'm using so we can compare results between them.

First thing I want to double-check is the actual PCI device ID since the lspci reports you provided didn't use the -nn option they aren't shown. I want to be absolutely sure we're dealing with the device we think we are! Here's the beginning of the output for this one:
```
sudo lspci -s 06:00.0 -vvvnn

06:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG Network Connection [8086:4222] (rev 02)
	Subsystem: Intel Corporation Unknown device [8086:1051]

```
It's the 8086:4222 I'm interested in for now.

Also, there is a bug report for what seems to be the same issue so please add a comment to it so we can track the issue more easily: "[iwl3945 can't wake up Intel(R) PRO/Wireless 3945 mini card](https://bugs.launchpad.net/+bug/203329)"

Sorry, before i read your reply, i installed backports module. Now i'm running kernel 2.6.24-19-generic (Hardy 32-bit).

I'm using the same card with yours. Yes, it's a Dell XPS M1530 and here is what you want:

```
$ sudo lspci -vv -nn -s 0b:00.0
0b:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG Network Connection [[COLOR="Red"]**8086:4222**[/COLOR]] (rev 02)
	Subsystem: Intel Corporation Unknown device [8086:1021]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin A routed to IRQ 17
	Region 0: [virtual] Memory at f9eff000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [c8] Power Management version 2
		Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
		Address: 0000000000000000  Data: 0000
	Capabilities: [e0] Express Legacy Endpoint IRQ 0
		Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-
		Device: Latency L0s <512ns, L1 unlimited
		Device: AtnBtn- AtnInd- PwrInd-
		Device: Errors: Correctable- Non-Fatal- Fatal- Unsupported-
		Device: RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
		Device: MaxPayload 128 bytes, MaxReadReq 128 bytes
		Link: Supported Speed 2.5Gb/s, Width x1, ASPM L0s L1, Port 0
		Link: Latency L0s <128ns, L1 <64us
		Link: ASPM Disabled RCB 64 bytes CommClk- ExtSynch-
		Link: Speed 2.5Gb/s, Width x1

```

Now, as a result of upgraded kernel, "MAC is in deep sleep!" error disappeared. Now dmesg shows no clue. iwconfig lists wlan0 as an interface with wireless extension. But one can identify problem by issuing ifconfig, which does not list wlan0. Further with -a switch it lists:

```
$ ifconfig -a wlan0
wlan0     Link encap:Ethernet  **[COLOR="Red"]HWaddr ff:ff:ff:ff:ff:ff[/COLOR]**  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

Note that the MAC address is not recognized - so an unfunctional interface.

Just for reference, here is the filtered dmesg output after removing iwl module, and modprobing it again with disable_hw_scan option.

```
$ dmesg | grep 3945
[   24.465371] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.25
[   24.465373] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   24.465502] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   24.481995] wmaster0: Selected rate control algorithm 'iwl-3945-rs'
[  163.616883] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.25
[  163.616891] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[  163.617084] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[  163.625268] wmaster0: Selected rate control algorithm 'iwl-3945-rs'

```

---

### Post by jasonkirk2006 on 2008-09-03
> **IntuitiveNipple said:**
> I'm getting a feeling this is caused by a problem with the Kill Switch as I first thought.

In the log-file you provided I noticed:
```

ubu32 kernel: [   36.576191] atkbd.c: Spurious ACK on isa0060/serio0. Some program might be trying access hardware directly.
ubu32 kernel: [   36.772058] atkbd.c: Unknown key pressed (translated set 2, code 0x0 on isa0060/serio0).
ubu32 kernel: [   36.772061] atkbd.c: Use 'setkeycodes 00 <keycode>' to make it known.
ubu32 kernel: [   36.775036] atkbd.c: Spurious ACK on isa0060/serio0. Some program might be trying access hardware directly.
ubu32 kernel: [   36.975457] atkbd.c: Spurious ACK on isa0060/serio0. Some program might be trying access hardware directly.

```
And I found some bug reports for other distributions that link this to the failure of the 3945.

So, let's try to discover if the failure to read the Kill Switch correctly could be causing this. Do this ***after*** you've removed the "quiet splash" options from the kernel command-line so we see more details.

With the PC switched off ensure the radio kill-switch is in the **on** position. Start the PC and let it boot. Log-in. From a command prompt start a log-monitor and then move the radio kill-switch to **off**. 

You should see a few messages reported. When they stop give it a second or two then move the switch back to **on**. There should be a few more messages. When they've stopped copy the messages to a reply here:
[code]
tail -f /var/log/kern.log

Just for quick reply, i must denote that, these lines are the result of misbehaving touchpad. I intentionally skipped this story for the sake of clarity. when i bought my device, it came with BIOS version A07. Having difficulties with the wireless card, i decided to make a BIOS upgrade to A09. But this time touchpad started to act like crazy. Now i'm using i8042.nomux=1 kernel option to aviod this situation. But since i was test driving a clean install then, it was the time before adding this i8042.nomux option to kernel.

---

### Post by jasonkirk2006 on 2008-09-03
> **IntuitiveNipple said:**
> If you're using a Dell this might be a solution:

```

Go to bios (F2 at Dell splash screen) on 'Wireless' go to 'Wi-Fi Catcher' and switch it to 'OFF'. 

```


(From the thread "[Dell XPS M1530 wireless problems](http://ubuntuforums.org/showpost.php?p=5158330&postcount=10)")

If you find this helps add a comment to this bug report "[[XPS M1530] Wireless don't work (need to use 'noapic' kernel boot param)](https://bugs.launchpad.net/dell/+bug/190664)"

Sorry, i did applied this in the beginning. Unfortunately, not a fix! Neither wireless catcher, nor the noapic kernel option healed my wound. noapic seemed to do the job at first, bu then i saw problems here and there.

I will send detailed logs ASAP, but with modified kernel versions.

Thank you very much for your efforts.

---

### Post by IntuitiveNipple on 2008-09-03
I'm going to go out on a limb here, even if I end up wrong. My gut instinct tells me this is a radio kill-switch issue.

Now you explain the touchpad/BIOS issues, and your usual work-around, that could actually be masking clues for the iwl3945.

What we need is to see precisely what that driver is getting up to. I'm going to create a special iwl3945 debug module for you to install. It'll use DKMS (Dynamic Kernel Module Support) so you can easily add/remove it and move across different kernel versions. I might be a day or two getting it ready.

The first run will just through out a lot of debug messages as it initialises so we know everything it encounters. From that we might be in a a better position to point to the cause of this issue. It seems you aren't alone with this (on Dell machines) so we might be helping quite a few others too.

---

### Post by jasonkirk2006 on 2008-09-04
Yesterday, i thought i solved the case. I was using my computer with battery removed - only with AC power plugged (because i mainly use my computer on my desk). Yesterday i mounted the battery and used the computer with it. I rebooted it several times, with different operating systems and there was no wireless issue. Then i posted my 22nd reply. Afterwards i installed several packages (backports and some other stuff) and now problem insists.

It sounds odd but could it (mounting the battery) really be a solution? Since dmesg logs complain too much about insufficient power?

---

### Post by IntuitiveNipple on 2008-09-04
> **jasonkirk2006 said:**
> 
It sounds odd but could it (mounting the battery) really be a solution? Since dmesg logs complain too much about insufficient power?
Anything is possible. If you think about, a missing battery is going to cause some confusion for the kernel as it loads since, when it reads the ACPI DSDT (Differentiated System Description Table) that will tell it there's a battery (usually BAT0) installed.

I'm struggling to think of how the two could be linked but, as we both know, sometimes it computers do the weirdest things :)

If you can reliably reproduce the work-around (not quite a fix) from a cold power start then I might start to be persuaded:???:

---

### Post by jasonkirk2006 on 2008-09-04
> ... as we both know, sometimes it computers do the weirdest things :)

Indeed, they do!

> If you can reliably reproduce the work-around (not quite a fix) from a cold power start then I might start to be persuaded:???:

I'm afraid, no. With or without battery... No wireless right now. In fact, upon your request, turned to yesterday's state of the computer that had no wireless trouble via ghost image. Now i'm using kernel 2.6.24-16 and no other updates.

Attachd with this reply is the following log files:

**ubu32_varlogmess_no_quietsplash_switch_ON.txt.gz**
Computer started with "quiet splash" removed and wireless switch is in the ON (radio enabled) position.

**ubu32_varlogmess_no_quietsplash_switch_OFF.txt.gz**
Computer started with "quiet splash" removed and wireless switch is in the OFF (radio disabled) position.

NOTE: I tried the first case and then the second. Unfortunately, i don't know why, the second file is somehow seem to be the first file plus some more logs. I did turned off the computer before starting to the second case but the first part of second is completely same as the first. I hope you figure it out.

---

### Post by jasonkirk2006 on 2008-09-04
And here is the log while switch state changes from ON (1) to OFF (0):

```
$ tail -f /var/log/kern.log
Sep  4 13:20:00 ubu32 kernel: [   36.614995] Bluetooth: RFCOMM TTY layer initialized
Sep  4 13:20:00 ubu32 kernel: [   36.614999] Bluetooth: RFCOMM ver 1.8
Sep  4 13:20:47 ubu32 kernel: [   48.747411] CPU0 attaching NULL sched-domain.
Sep  4 13:20:47 ubu32 kernel: [   48.747415] CPU1 attaching NULL sched-domain.
Sep  4 13:20:47 ubu32 kernel: [   48.772381] CPU0 attaching sched-domain:
Sep  4 13:20:47 ubu32 kernel: [   48.772384]  domain 0: span 03
Sep  4 13:20:47 ubu32 kernel: [   48.772386]   groups: 01 02
Sep  4 13:20:47 ubu32 kernel: [   48.772388] CPU1 attaching sched-domain:
Sep  4 13:20:47 ubu32 kernel: [   48.772389]  domain 0: span 03
Sep  4 13:20:47 ubu32 kernel: [   48.772390]   groups: 02 01
Sep  4 13:23:20 ubu32 kernel: [   70.778810] atkbd.c: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
Sep  4 13:23:20 ubu32 kernel: [   70.778821] atkbd.c: Use 'setkeycodes e008 <keycode>' to make it known.
Sep  4 13:23:20 ubu32 kernel: [   70.799175] usb 7-2: USB disconnect, address 2
Sep  4 13:23:20 ubu32 kernel: [   70.799185] usb 7-2.1: USB disconnect, address 3
Sep  4 13:23:20 ubu32 kernel: [   70.915246] usb 7-2.2: USB disconnect, address 4
Sep  4 13:23:20 ubu32 kernel: [   70.961342] usb 7-2.3: USB disconnect, address 5
Sep  4 13:23:39 ubu32 kernel: [   74.540959] atkbd.c: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
Sep  4 13:23:39 ubu32 kernel: [   74.540969] atkbd.c: Use 'setkeycodes e008 <keycode>' to make it known.
Sep  4 13:23:40 ubu32 kernel: [   74.860233] usb 7-2: new full speed USB device using uhci_hcd and address 6
Sep  4 13:23:40 ubu32 kernel: [   74.890908] usb 7-2: configuration #1 chosen from 1 choice
Sep  4 13:23:40 ubu32 kernel: [   74.892692] hub 7-2:1.0: USB hub found
Sep  4 13:23:40 ubu32 kernel: [   74.902024] hub 7-2:1.0: 3 ports detected
Sep  4 13:23:40 ubu32 kernel: [   75.121606] usb 7-2.1: new full speed USB device using uhci_hcd and address 7
Sep  4 13:23:40 ubu32 kernel: [   75.142957] usb 7-2.1: configuration #1 chosen from 1 choice
Sep  4 13:23:40 ubu32 kernel: [   75.349340] usb 7-2.2: new full speed USB device using uhci_hcd and address 8
Sep  4 13:23:40 ubu32 kernel: [   75.450710] usb 7-2.2: configuration #1 chosen from 1 choice
Sep  4 13:23:41 ubu32 kernel: [   75.465435] input: Broadcom Corp as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2.2/7-2.2:1.0/input/input11
Sep  4 13:23:41 ubu32 kernel: [   75.505183] input,hidraw0: USB HID v1.11 Keyboard [Broadcom Corp] on usb-0000:00:1d.2-2.2
Sep  4 13:23:41 ubu32 kernel: [   75.706002] usb 7-2.3: new full speed USB device using uhci_hcd and address 9
Sep  4 13:23:41 ubu32 kernel: [   75.745481] usb 7-2.3: configuration #1 chosen from 1 choice
Sep  4 13:23:41 ubu32 kernel: [   75.760700] input: Broadcom Corp as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2.3/7-2.3:1.0/input/input12
Sep  4 13:23:41 ubu32 kernel: [   75.798019] input,hidraw1: USB HID v1.11 Mouse [Broadcom Corp] on usb-0000:00:1d.2-2.3

```

This is also taken after booting with no "quiet splash" option.

NOTE: Does removing "quiet splash" really change the verbosity of the log?

---

### Post by jasonkirk2006 on 2008-09-06
I downloaded Interpid Ibex 32-bit from [http://cdimage.ubuntu.com/daily/current/](http://cdimage.ubuntu.com/daily/current/) and installed. So far only 2 problems. I have restarted several times (approx 10, i think). Dmesg logs look different with Interpid.

Here is the dmesg logs at the time of the wireless problem:
```
$ dmesg | grep 3945
[   13.477755] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[   13.477758] iwl3945: Copyright(c) 2003-2008 Intel Corporation
[   13.477812] iwl3945 0000:0b:00.0: enabling device (0000 -> 0002)
[   13.477823] iwl3945 0000:0b:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   13.477842] iwl3945 0000:0b:00.0: setting latency timer to 64
[   13.477861] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
[   13.483873] iwl3945: Error: saturation power is -1, less than minimum expected 40
[   13.483875] iwl3945: Invalid power index
[   13.483877] iwl3945: initializing regulatory failed: -5
[   13.483934] iwl3945 0000:0b:00.0: PCI INT A disabled
[   13.483941] iwl3945: probe of 0000:0b:00.0 failed with error -5

```

And when there is no problem at all:
```
$ dmesg | grep 3945
[   13.284060] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[   13.284150] iwl3945: Copyright(c) 2003-2008 Intel Corporation
[   13.284323] iwl3945 0000:0b:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   13.284417] iwl3945 0000:0b:00.0: setting latency timer to 64
[   13.284436] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
[   13.349049] iwl3945: Tunable channels: 13 802.11bg, 23 802.11a channels
[   13.349430] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   13.446170] iwl3945 0000:0b:00.0: PCI INT A disabled
[   26.482707] iwl3945 0000:0b:00.0: enabling device (0000 -> 0002)
[   26.482720] iwl3945 0000:0b:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   26.482839] iwl3945 0000:0b:00.0: restoring config space at offset 0xf (was 0x100, writing 0x107)
[   26.482962] iwl3945 0000:0b:00.0: restoring config space at offset 0x4 (was 0x0, writing 0xf9eff000)
[   26.482985] iwl3945 0000:0b:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[   26.483016] iwl3945 0000:0b:00.0: restoring config space at offset 0x1 (was 0x100002, writing 0x100106)
[   26.483499] firmware: requesting iwlwifi-3945-1.ucode

```

I also attached the /var/log/messages logs for both success and failure situations.(**interpid32_varlogmessages_full_fail.txt.bz2** and **interpid32_varlogmessages_full_success.txt.bz2**)

Furhermore, there are several other logs and dumps in **Interpid_several_logs.zip** to give you more info about the system (information about the modules 3945 card uses, uname output and the monitored /var/log/kern.log file as wirless kill switch position changes - all with "quiet splash" kernel option removed).

---

### Post by jasonkirk2006 on 2008-09-06
Does this mean that the wireless kill switch is not recognized?

```
$ tail -f /var/log/syslog 
Sep  6 23:22:35 interpid32 kernel: [ 3480.977077] usb 6-2.2: new full speed USB device using uhci_hcd and address 24
Sep  6 23:22:35 interpid32 hcid[5314]: Device hci0 has been activated
Sep  6 23:22:35 interpid32 kernel: [ 3481.132207] usb 6-2.2: configuration #1 chosen from 1 choice
Sep  6 23:22:35 interpid32 kernel: [ 3481.140746] input: Broadcom Corp as /class/input/input20
Sep  6 23:22:35 interpid32 kernel: [ 3481.185135] input,hidraw1: USB HID v1.11 Keyboard [Broadcom Corp] on usb-0000:00:1d.2-2.2
Sep  6 23:22:35 interpid32 kernel: [ 3481.263123] usb 6-2.3: new full speed USB device using uhci_hcd and address 25
Sep  6 23:22:35 interpid32 kernel: [ 3481.396511] usb 6-2.3: configuration #1 chosen from 1 choice
Sep  6 23:22:35 interpid32 kernel: [ 3481.411664] input: Broadcom Corp as /class/input/input21
Sep  6 23:22:35 interpid32 kernel: [ 3481.455524] input,hidraw2: USB HID v1.11 Mouse [Broadcom Corp] on usb-0000:00:1d.2-2.3
Sep  6 23:22:36 interpid32 NetworkManager: <info>  Wireless now enabled by radio killswitch 
**Sep  6 23:35:49 interpid32 kernel: [ 4275.165138] atkbd.c: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).**
Sep  6 23:35:49 interpid32 kernel: [ 4275.165152] atkbd.c: Use 'setkeycodes e008 <keycode>' to make it known.
Sep  6 23:35:49 interpid32 kernel: [ 4275.320089] usb 6-2: USB disconnect, address 22
Sep  6 23:35:49 interpid32 kernel: [ 4275.320099] usb 6-2.1: USB disconnect, address 23
Sep  6 23:35:49 interpid32 kernel: [ 4275.320164] btusb_intr_complete: hci0 urb f6490600 failed to resubmit (19)
Sep  6 23:35:49 interpid32 kernel: [ 4275.321682] btusb_send_frame: hci0 urb effae880 submission failed
Sep  6 23:35:49 interpid32 hcid[5314]: HCI dev 0 down
Sep  6 23:35:49 interpid32 hcid[5314]: Stopping security manager 0
Sep  6 23:35:49 interpid32 hcid[5314]: Device hci0 has been disabled
Sep  6 23:35:49 interpid32 hcid[5314]: HCI dev 0 unregistered
Sep  6 23:35:49 interpid32 hcid[5314]: Unregister path: /org/bluez/hci0
Sep  6 23:35:49 interpid32 hcid[5314]: Device hci0 has been removed
Sep  6 23:35:49 interpid32 kernel: [ 4275.573877] usb 6-2.2: USB disconnect, address 24
Sep  6 23:35:49 interpid32 kernel: [ 4275.593365] usb 6-2.3: USB disconnect, address 25
Sep  6 23:35:52 interpid32 NetworkManager: <info>  Wireless now disabled by radio killswitch 
**Sep  6 23:36:57 interpid32 kernel: [ 4343.344409] atkbd.c: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).**
Sep  6 23:36:57 interpid32 kernel: [ 4343.344426] atkbd.c: Use 'setkeycodes e008 <keycode>' to make it known.
Sep  6 23:36:58 interpid32 kernel: [ 4343.800118] usb 6-2: new full speed USB device using uhci_hcd and address 26
Sep  6 23:36:58 interpid32 kernel: [ 4343.983147] usb 6-2: configuration #1 chosen from 1 choice
Sep  6 23:36:58 interpid32 kernel: [ 4343.986024] hub 6-2:1.0: USB hub found
Sep  6 23:36:58 interpid32 kernel: [ 4343.989085] hub 6-2:1.0: 3 ports detected
Sep  6 23:36:58 interpid32 kernel: [ 4344.289959] usb 6-2.1: new full speed USB device using uhci_hcd and address 27
Sep  6 23:36:58 interpid32 kernel: [ 4344.426914] usb 6-2.1: configuration #1 chosen from 1 choice
Sep  6 23:36:58 interpid32 hcid[5314]: HCI dev 0 registered
Sep  6 23:36:58 interpid32 hcid[5314]: HCI dev 0 up
Sep  6 23:36:58 interpid32 hcid[5314]: Device hci0 has been added
Sep  6 23:36:58 interpid32 hcid[5314]: Starting security manager 0
Sep  6 23:36:58 interpid32 kernel: [ 4344.508941] usb 6-2.2: new full speed USB device using uhci_hcd and address 28
Sep  6 23:36:58 interpid32 hcid[5314]: Device hci0 has been activated
Sep  6 23:36:59 interpid32 kernel: [ 4344.643057] usb 6-2.2: configuration #1 chosen from 1 choice
Sep  6 23:36:59 interpid32 kernel: [ 4344.651139] input: Broadcom Corp as /class/input/input22
Sep  6 23:36:59 interpid32 kernel: [ 4344.673121] input,hidraw1: USB HID v1.11 Keyboard [Broadcom Corp] on usb-0000:00:1d.2-2.2
Sep  6 23:36:59 interpid32 kernel: [ 4344.758910] usb 6-2.3: new full speed USB device using uhci_hcd and address 29
Sep  6 23:36:59 interpid32 kernel: [ 4344.897245] usb 6-2.3: configuration #1 chosen from 1 choice
Sep  6 23:36:59 interpid32 kernel: [ 4344.904229] input: Broadcom Corp as /class/input/input23
Sep  6 23:36:59 interpid32 kernel: [ 4344.949115] input,hidraw2: USB HID v1.11 Mouse [Broadcom Corp] on usb-0000:00:1d.2-2.3
Sep  6 23:36:59 interpid32 NetworkManager: <info>  Wireless now enabled by radio killswitch 

```

Although "NetworkManager" lines successfuly says wireless disabled or enabled by the radio killswitch?

---

### Post by jasonkirk2006 on 2008-09-06
And something i just noted:

```
$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:1d:09:3e:4d:73
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A ip=192.168.7.2 latency=0 module=sky2 multicast=yes
  *-network UNCLAIMED
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0

```

But modules are loaded:

```
$ lsmod | grep 3945
iwl3945                98804  0 
rfkill                 17048  1 iwl3945
mac80211              217076  1 iwl3945
led_class              12164  1 iwl3945
cfg80211               32392  2 iwl3945,mac80211

```

---

### Post by ALainONE on 2008-09-07
Hello!  Newbie here... I was scanning through the post and found this one out.  I have exactly the same problem...

Can someone please help me...

Following the post. Here are some of the details...  First off, my flavor of linux...

```
$ cat /etc/*-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.1"

$ uname -a
Linux a-nix 2.6.24-21-generic #1 SMP Tue Aug 12 13:37:22 UTC 2008 i686 GNU/Linux
```

And the following...

```
$ dmesg | grep Wireless
[   39.961498] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
[   39.961644] iwl3945: Detected Intel PRO/Wireless 3945BG Network Connection
```

```
$ sudo lshw | grep Wireless
                description: Wireless interface
                product: PRO/Wireless 3945ABG Network Connection
```

I've also ran...
```
sudo apt-get install linux-backports-modules-hardy-generic
```
but to no avail!

Lastly,
```
$ sudo iwlist wlan0 scan
wlan0     Failed to read scan data : Resource temporarily unavailable
```

Other info...

```
$ sudo lshw -C Network
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 02
       serial: 00:18:de:b7:3c:c1
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 00
       serial: 00:16:36:e7:62:8b
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI duplex=full firmware=0.5-1 ip=10.19.98.31 latency=0 link=yes module=e1000 multicast=yes port=twisted pair speed=100MB/s
```

Everything works fine, save for the wireless...

Thanks in advance!

---

### Post by ALainONE on 2008-09-10
I found a simple solution to my problem... just want to share in case someone finds their way to this post...

Problem: 
Intel PRO/Wireless 3945ABG NOT working!

System: 
Ubuntu 8.04.1 Hardy Heron LTS / 2.6.24-19-generic

Solution: 
I've tried all the post here and did not work for me (after all the longest keybashing ever)... believe it or not, It's the simplest solution ever (and why did I not think of that?!!!)... and here it is (with ndiswrapper)...

- Download the windows xp driver version 11.5.1.15/9.0.4.39 (link [[COLOR="RoyalBlue"]here[/COLOR]]("http://downloadcenter.intel.com/Filter_Results.aspx?strOSs=44&strTypes=all&ProductID=2259&OSFullName=Windows*%20XP%20Professional&lang=eng&sType=prev")).  

I was always working with the 12.0.4.0 version which came with my driver cd and this it seems is not compatible with ndiswrapper.

- Install the driver by way of System - Administration - Windows Wireless Drivers.  Load the "NETw4x32.inf" file, then install...

- Restart your notebook.

- You should see your wireless on your connection icon at the upper right corner of your screen.

- And that's it.  My wireless is now working flawlessly!!!

Sometimes we overlook the simplest of solution, but often times the simplest solutions are the best solutions!!!

footnote:
All thanks goes to this post [COLOR="Blue"][here]("http://ubuntuforums.org/showthread.php?t=895732&highlight=intel+pro%2Fwireless+3945")[/COLOR].

---

### Post by chappejw on 2008-09-11
I have the ipw3945 abg wireless working flawlessly from first install with Ubuntu 8.04 here are some details from my Toshiba laptop for comparison with anyone elses who is having trouble.

monkey@zoo:~$ locate 3945
/lib/firmware/2.6.24-16-generic/iwlwifi-3945-1.ucode
/lib/firmware/2.6.24-16-generic/iwlwifi-3945.ucode
/lib/firmware/2.6.24-17-generic/iwlwifi-3945-1.ucode
/lib/firmware/2.6.24-17-generic/iwlwifi-3945.ucode
/lib/firmware/2.6.24-18-generic/iwlwifi-3945-1.ucode
/lib/firmware/2.6.24-18-generic/iwlwifi-3945.ucode
/lib/firmware/2.6.24-19-generic/iwlwifi-3945-1.ucode
/lib/firmware/2.6.24-19-generic/iwlwifi-3945.ucode
/lib/modules/2.6.24-16-generic/ubuntu/wireless/iwlwifi/iwlwifi/compatible/iwl3945.ko
/lib/modules/2.6.24-17-generic/ubuntu/wireless/iwlwifi/iwlwifi/compatible/iwl3945.ko
/lib/modules/2.6.24-18-generic/ubuntu/wireless/iwlwifi/iwlwifi/compatible/iwl3945.ko
/lib/modules/2.6.24-19-generic/ubuntu/wireless/iwlwifi/iwlwifi/compatible/iwl3945.ko
monkey@zoo:~$

monkey@zoo:~$ dmesg | grep 3945
[   36.894551] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
[   36.894557] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   36.894761] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   38.710644] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
[   38.742990] wmaster0: Selected rate control algorithm 'iwl-3945-rs'

monkey@zoo:~$ lsmod
...
iwl3945                89844  0 
iwlwifi_mac80211      219108  1 iwl3945
...

Hope that may provide some useful information for comparison sake

---

### Post by jasonkirk2006 on 2008-09-11
> **chappejw said:**
> Here is the solution to get your Intel ipw3945 wireless card working. :guitar:

Make sure you have the package **linux-restricted-modules-generic** installed. This package contains the updated firmware for that wireless card. Compiling and installing it yourself is always a tedious operation. Note: replacing the firmware for this card poses no risk since it is loaded at runtime. Once you have that package your network manager should detect available networks and allow you to configure everything without a glitch. Let me know if that solves your issues, I have delt with this card extensively.

Hey, once you said (in your #11 post in this thread) linux-restricted-modules-generic package contains updated firmware for 3945. I have a question: 

**Is not the iwl3945 an open source project? If so why would it be restricted software? Furhtermore, i have this package installed but i cannot see any 3945 restricted modules in my System>Administration>Hardware Drivers. Could you please explain it?**

---

### Post by chappejw on 2008-09-12
Hi Jasonkirk2006, 

Yes, it is an open source project. Sorry, the last time I had to mess with my ipw3945 there was a working driver in the restricted modules under Feisty Fawn which was this version available via sourceforge. Intel had kind of developed it about 95% and then left it hanging for Linux community to finish off. located here..
[http://ipw3945.sourceforge.net/](http://ipw3945.sourceforge.net/)

That would be why you don't see it in restricted modules on Hardy. I suppose Intel revamped their old ipw3945 driver as the newer iwl3945 one, located here
[http://linuxwireless.org/en/users/Drivers/iwl3945](http://linuxwireless.org/en/users/Drivers/iwl3945)

I have not had any problems with this driver since getting the ipw3945 driver working on Feisty. I must have assumed that this driver was simply carried forward to hardy since it worked fine on Feisty Fawn. My bad.

---

### Post by dvlong on 2008-09-12
Do you provide analysis too????  :)

dvlong@longslap2:~$ locate 3945
/lib/firmware/2.6.24-19-generic/iwlwifi-3945-1.ucode
/lib/firmware/2.6.24-19-generic/iwlwifi-3945.ucode
/lib/modules/2.6.24-19-generic/ubuntu/wireless/iwlwifi/iwlwifi/compatible/iwl3945.ko


dvlong@longslap2:~$ dmesg | grep 3945
[   30.854060] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
[   30.854066] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   30.854267] iwl3945: Detected Intel PRO/Wireless 3945BG Network Connection
[   32.197349] iwl3945: Tunable channels: 13 802.11bg, 0 802.11a channels
[   32.197770] wmaster0: Selected rate control algorithm 'iwl-3945-rs'
[   37.418780] iwl3945: Microcode SW error detected.  Restarting 0x82000008.
[   37.418853] iwl3945: Error Reply type 0x00000005 cmd REPLY_SCAN_CMD (0x80) seq 0x4418 ser 0x0000004B
[   38.412717] iwl3945: Can't stop Rx DMA.

---

### Post by chappejw on 2008-09-12
dvlong what is the result of running this command? 
modprobe iwl3945

Perhaps the module iwl3945 is not being loaded...


On another note, there are potential solutions here...

[https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.24/+bug/226134](https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.24/+bug/226134)

and here...

[https://bugs.launchpad.net/linux/+bug/185470](https://bugs.launchpad.net/linux/+bug/185470)

---

### Post by dvlong on 2008-09-13
Thanks!

I've been through both of these threads - and have finally solved [?] for now.  I've put this in a different thread on the Networking & Wirless Forum but will place it here in case it points anyone in a right direction:

Both Pytheas22 and Chili555 have threads that many people have been helped by in this forum:

Networking & Wireless Forum - Re: Wireless only works if Wired network is plugged in first.

My Post...
After 2 weeks and finally getting frustrated enough with getting nowhere, I decided to start with a clean slate.

I reinstalled Hardy. Did all the updates.
then ran the codes:
1.sudo apt-get install linux-backports-modules-hardy-generic
2.sudo su
3.echo -e &#8220;alias wlan0 iwl3945 \noptions iwl3945 disable_hw_scan=1&#8243; > /etc/modprobe.d/iwl3945
4.reboot

When this didn't fix anything I was beginning to get nervous.

I then simply reset my router to the factory defaults, (this makes no sense because the wireless initially stopped working without touching the router) and made the necessary ip changes so that it doesn't conflict with my adsl modem settings, and my wireless began to work immediately.

My wireless router is a Linksys WRT54GL.

Now I can go back and work under the shade tree again!

---

