---
title: "Dell laptop &amp; Netgear WG111v2 issues"
date: 2006-03-31
forum: Hardware &amp; Laptops
---

### Post by jeremyb on 2006-03-31
im a linux noob, and almost have my wireless connection working on my Dell Latitude C810 with a NetGearWG111v2 usb wifi card (plugged into a pcmcia 4 port 2.0 card).

The Network settings shows Wireless Connection, ethernet connection and modem connection. ive set wlan0 as the default (when i restart it doesnt seem to be getting saved though)

i typed in iwconfig and it shows my wlan0 settings and such. 

ive typed in ndiswrapper -l and it says (net111v2 driver present, hardware present)

I'm not getting any internet though. on my gf's laptop (XP) she can connect just fine. 

any ideas on how to diagnose whats going on?
btw talk to me like im three.

any help vey much appreciated-----ive searched here, google etc and just cant figure out the last step.

thank you
jeremy

---

### Post by rwestgeest on 2006-04-01
iwconfig settings visible sounds promising

have you tried iwlist wlan0 scanning ? Do you get scan results? If so then ifup wlan0 should do the trick. 

This should be the same as 'activate' on wlan0 in your network configuration dialog.

---

### Post by jml on 2006-04-01
Are you trying to connect to an encrypted wireless network?  If yes, temporarily disable encryption and then see if you can connect.  If you can, then you know that the hardward is ok.  Turn encryption back on your access point and then you can start working on sorting out the encryption piece.  Ubuntu supports WEP encryption.  You go into network manager, highlight your wireless card, click on properties and type in the WEP Key.  Close out the properties box and reactivate your wireless card.  That should do it.  If you are using WPA encryption, things get a bit more complicated.  You will need to download and configure an application called wpa_supplicant.

Joe

---

### Post by jeremyb on 2006-04-01
so, i took off the security on my network (makes sense), also i tried assigning a 64 and 128bit Wep key and it didnt work (i was previously using a WPA key, which i now realize isnt compatible and it still didnt work. 

I did a "iwlist wlan0 scan" and got:
wlan0     No scan results

then i did a "sudo ifup wlan0" and got:
ifup: interface wlan0 already configured

typing "route -n" gave me:
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

"ifconfig" returns:
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5733 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5733 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:520070 (507.8 KiB)  TX bytes:520070 (507.8 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:0F:B5:BC:D7:11
          inet6 addr: fe80::20f:b5ff:febc:d711/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


does this mean anything to anybody?

I'm currently using the wired eth0 connection, but really need to get wifi working so i can use internet at school.

thanks again for any help anyone might be able to give.
jeremy

---

### Post by jeremyb on 2006-04-02
ive read the wifi wiki about 12 times, and that hasnt helped me. Ive read for about the last 5 hours on sites after googling the problem and that hasnt gotten me anywhere.

I've disabled the encryption on my router, nothing.

ive set encryption to 64 bit and entered the wep code, nothing.

same with 128.

i typed "sudo iwlist wlan0 scan"    and got: 
wlan0    No scan results

any other advice on what to do?

any other linux distro thats more wifi friendly?

thanks again for any help.
jeremy

---

### Post by jeremyb on 2006-04-02
any moderators have any ideas?

---

