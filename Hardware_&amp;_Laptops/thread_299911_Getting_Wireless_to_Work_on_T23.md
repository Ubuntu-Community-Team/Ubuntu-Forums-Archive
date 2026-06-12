---
title: "Getting Wireless to Work on T23"
date: 2006-11-14
forum: Hardware &amp; Laptops
---

### Post by shawn_duggan on 2006-11-14
I just got a T23 off eBay and I am trying to get it working with the wireless card that came with it - a Netopia 3D Reach (I do have a NetGear somewhere at work also). It looks like the driver cd that came with the card is using the TI ACX100 WLAN Adapter Driver.

I first got the wireless card working in XP by installing the driver from the cd. I then copied the *.inf, *.sys and 4 *.bin files to my usb key and fired up the Edgy live cd to see if I could get things working before I installed to disk.

I installed ndisgtk and installed the driver.  Things are not working. Below is my output from iwconfig then dmesg.  Maybe there is a better driver for me to use?  TIA to any who respond.

wlan0     IEEE 802.11b+  ESSID:"XXXX"  Nickname:"acx v0.3.21"
          Mode:Managed  Frequency:2.412 GHz  
Access Point: Not-Associated   
          Bit Rate:22 Mb/s   Tx-Power=18 dBm   Sensitivity=176/255  
          Retry min limit:7   RTS thr:off   
          Power Management:off
          Link Quality=67/100  Signal level=55/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

[17179813.760000] wlan0 (WE) : Driver using old /proc/net/wireless support, please fix driver!
[17180075.516000] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)
[17180075.520000] ndiswrapper (wrapper_init:129): loadndiswrapper failed (32512); check system log for messages from 'loadndisdriver'
[17180075.520000] ndiswrapper (wrapper_init:136): ndiswrapper: initialization failed
[17180270.120000] wlan0: changing radio power level to 18 dBm (41)
[17180270.248000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[17180538.404000] eth0: no IPv6 routers present

---

