---
title: "dlink dwl-g122 c1 wpa not working (wep works though)"
date: 2009-02-03
forum: Hardware
---

### Post by maitrebart on 2009-02-03
I googled several places on the net without much answers about the problem I have.

In ubuntu 8.04 lts, my dlink dongle works in wep mode, but not in wpa.
So I don't think it's a driver problem since in wpa the 'connected' led is on but the 'rx/tx' led is off (but flashing for 5 tries at login).
In wep it is working ok.

In the mean time, here are my outputs of the following commands:

[FONT="Courier New"]% lsusb
Bus 003 Device 003: ID 07d1:3c03 D-Link System 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 03f0:0205 Hewlett-Packard ScanJet 3300c
Bus 001 Device 001: ID 0000:0000  

% lsmod|grep rt
snd_mpu401_uart         9728  1 snd_mpu401
parport_pc             36260  1 
parport                37832  3 ppdev,lp,parport_pc
gameport               16008  1 analog
rt73usb                27136  0 
rt2x00usb              12800  1 rt73usb
rt2x00lib              22528  2 rt73usb,rt2x00usb
rfkill                  8596  1 rt2x00lib
input_polldev           5896  1 rt2x00lib
snd_rawmidi            25760  2 snd_mpu401_uart,snd_seq_midi
crc_itu_t               3072  1 rt2x00lib
mac80211              165652  2 rt2x00usb,rt2x00lib
snd                    56996  19 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401,snd_mpu401_uart,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
agpgart                34760  2 nvidia,nvidia_agp
usbcore               146412  5 rt73usb,rt2x00usb,ehci_hcd,ohci_hcd

% ifconfig
eth0      Link encap:Ethernet  HWaddr 00:e0:4d:30:6e:d7  
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:4dff:fe30:6ed7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1985 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1600 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1822296 (1.7 MB)  TX bytes:258614 (252.5 KB)
          Interrupt:20 Base address:0xd000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1193 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1193 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:60234 (58.8 KB)  TX bytes:60234 (58.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:17:9a:d1:34:32  
          inet addr:192.168.0.104  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-17-9A-D1-34-32-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

% iwconfig
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

[/FONT]

I tried many solutions provided on the net about the dwl-g122 (involving /etc/network/interface, modprobe's blacklist, etc). Many of them are dated around 2005-2007. So my guess is that if it was a driver issue, it would have been fixed in the mean time. Moreover, the hardware compatibility list for this device indicates it works out of the box for both wpa and wep.

I noticed one thing though: commands like 'sudo iwpriv wlan0 ...' outputs 'wlan0     no private ioctls.' which let me think it could be a driver problem actually.

I setup the network interfaces with network-admin where I enter the ssid, encryption, passkey, ip, gateway, etc.

So if someone has suggestions I can try, let me know.

Thank you.

---

### Post by maitrebart on 2009-02-03
Here are other outputs:

[FONT="Courier New"]% dmesg | grep 'rt[27]'
[   40.916016] usbcore: registered new interface driver rt73usb

% grep 'rt[27]\|wlan0' /var/log/messages

Feb  3 22:12:45 homer kernel: [   40.916016] usbcore: registered new interface driver rt73usb
Feb  3 22:12:45 homer kernel: [   42.629554] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[/FONT]
And these other greps:

[FONT="Courier New"]/var/log/daemon.log:Feb  3 22:12:45 homer avahi-daemon[5252]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.0.104.
/var/log/daemon.log:Feb  3 22:12:45 homer avahi-daemon[5252]: New relevant interface wlan0.IPv4 for mDNS.
/var/log/daemon.log:Feb  3 22:12:45 homer avahi-daemon[5252]: Registering new address record for 192.168.0.104 on wlan0.IPv4.

/var/log/udev:UEVENT[1233717159.860310] add      /devices/pci0000:00/0000:00:02.2/usb3/3-8/3-8:1.0/net/wlan0 (net)
/var/log/udev:DEVPATH=/devices/pci0000:00/0000:00:02.2/usb3/3-8/3-8:1.0/net/wlan0
/var/log/udev:INTERFACE=wlan0
/var/log/udev:UDEV  [1233717161.426766] add      /devices/pci0000:00/0000:00:02.2/usb3/3-8/3-8:1.0/net/wlan0 (net)
/var/log/udev:DEVPATH=/devices/pci0000:00/0000:00:02.2/usb3/3-8/3-8:1.0/net/wlan0
/var/log/udev:INTERFACE=wlan0
[/FONT]

---

### Post by maitrebart on 2009-02-21
I found out that I had to compile the rt73 driver.
All you need to know about how to compile and install the driver is at:

[http://ubuntuforums.org/showthread.php?t=400236]("http://ubuntuforums.org/showthread.php?t=400236")

However, my interface was still not coming up at boot. So here is another page that shows how to setup the interface at boot:

[http://ubuntuforums.org/showthread.php?t=684495]("http://ubuntuforums.org/showthread.php?t=684495")

(see the part about /etc/rc.local)

After all this, my interface was working. Well, not 100% of the time... 8v(

My guess is there is a connection problem (hardware) with my d-link router (which I encounter also in Windows). Up to now, I would say that 60% of the boots results in the interface working. When it's not, a second restart does. Rarely more (but it happened).

---

