---
title: "Help with my Dell Inspiron 1720 and the wireless card!"
date: 2008-05-12
forum: Hardware
---

### Post by diannita86 on 2008-05-12
Hi there! I got a big problem. I got a new Dell Inspiron 1720 laptop. I really don't like Windows Vista, so I decided to change to ubuntu, because I'm an Ubuntu lover =D (Ubuntu 8.04)
Everything was fine until I decided to get connected to a wireless network, so I noticed my wireless card doesn't work.
I've tried several howtos but it didn't work. It's a Dell Wireless 1505 Wireless-N MiniCard. I really need some help, so... HELP ME please!:(

If you need more information, let me know

---

### Post by notepad on 2008-07-27
with some difficulty and searching, i got my 1720 to connect to my wireless network by doing this;

download the windows driver package for the 1505 wireless mini card from here: [http://ftp.us.dell.com/network/Dell_multi-device_A17_R174291.exe](http://ftp.us.dell.com/network/Dell_multi-device_A17_R174291.exe)

beware: 80mb download

run it in windows to get the file named bcmwl5.inf located in DRIVER_US.

sudo apt-get install ndisgtk

system > administration > wireless windows drivers > install new driver

locate your bcmwl5.inf file and press install.

you may need to reboot and now your wireless mini card works in ubuntu.

left click the network icon in the system tray and select manual configuration. click on the unlock button and enter your ubuntu user password. go to wireless connection and click properties. disable roaming mode because it seems to be unreliable and manually enter your essid, password type (hopefully you are using wpa and not wep), your password and select dhcp for configuration under connection settings (hopefully you are running a dhcp server on your wireless access point/router/modem).

it should connect. if it doesnt connect and you cant work out why (like me) it could be because you have told your wireless router not to broadcast the essid. you must broadcast the essid from your wireless access point/router/modem or ubuntu will not connect.

i recommend using an exclusive mac address access control so your neighbours and war drivers cant use your wireless (more of a problem if you are using wep authentication protocol).

---

