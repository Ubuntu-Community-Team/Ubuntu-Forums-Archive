---
title: "How to make Airvast PRISM3 wireless work?"
date: 2005-02-15
forum: Hardware &amp; Laptops
---

### Post by moephan on 2005-02-15
I'm a Linux newbie. I'm loving Ubuntu, but it doesn't support my wireless out of the box. There are lots of postings about getting wireless to work, but I have no idea which posting apply to me. I've tried a bunch of stuff, but I'd rather not try stuff with recompiling the kernel, etc... unless I know that it is actually something I need to do. This is getting pretty frustrating, and is the only thing keeping me from being able to really use Ubuntu. I'm hoping that it's an easy problem for someone who knows what to do. 

Here are my specs...

Wireless Card (according to Device Manager):
IEEE 802.11b PRISM3 USB

Wireless manufacturer:
AirVast Taiwan

Computer make and model:
ECS A535

It works fine with Windows XP.

Ideally, someone has gotten this configuration to work, and can tell us how to make it work. Otherwise, if someone could outline the general steps that I need to accomplish so that I can make heads or tails out of the other posting, that would also be helpful.

Cheers, Rick

---

### Post by jhudson on 2005-02-15
I believe this is the same card I have in my Balance laptop I purchased from WalMart and basically I used the wlan driver form the linux-wlan-ng. You can find it in Synaptic.
After downloading and installing ( get the doc also ), set up your config file according to your wireless lan setup then after login open a terminal and do.

sudo wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable 
sudo wlanctl-ng wlan0 lnxreq_autojoin ssid="" authtype=opensystem (for any within range) OR
sudo wlanctl-ng wlan0 lnxreq_autojoin ssid=(Your ESSID Here) authtype=opensystem
sudo iwconfig (to see your access point).

sudo dhclient wlan0
If you are using dhcp this should get you an id.
although device manager recognizes your card as a prism3_usb and wlan-ng uses prism2_usb this will still work great.
Hopes this helps
Jack Hudson Registered Linux User 365587

---

### Post by moephan on 2005-02-15
Jack,

Your directions were just what the doctor ordered. I NEVER would have figured this out on my own. For anyone else who's having this trouble, here are the steps I followed:

1. I installed linux-wlan-ng from synaptic

2. I added the following 4 lines to the bottom of /etc/network/interfaces
# The wireless network interface
auto wlan0
iface wlan0 inet dhcp
	wireless_mode managed

3.I entered the following commands:
sudo wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable
sudo wlanctl-ng wlan0 lnxreq_autojoin ssid="" authtype=opensystem
sudo iwconfig
sudo dhclient wlan0

My wireless modem is not secured, otherwise, looking at iwconfig outputs, I assume I'd have to figure out commands to pass in the keys, etc... 

Using the Network Settings Applet did not work for me. Also, when I rebooted, it took a while for the boot process to give up on bringing up the wireless card. 

Thanks again for your help. I hope anyone else finds this post helpful.

Cheers, Rick

---

### Post by lucan on 2005-03-01
[QUOTE=moephan]

authtype=opensystem
My wireless modem is not secured, otherwise, looking at iwconfig outputs, I assume I'd have to figure out commands to pass in the keys, etc... 

[/QUOTE]

hi,
do this means that the route cannot use WEP?

---

### Post by moephan on 2005-03-25
I think you can use wep using wlanctl-ng commands. Considering trying something like:

sudo wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable 
sudo wlanctl-ng wlan0  dot11WEPDefaultKeyID=0
sudo wlanctl-ng wlan0 dot11WEPDefaultKey0=12:34:56:78:90 (put in your WEP key)
sudo wlanctl-ng wlan0 lnxreq_autojoin ssid="" authtype=sharedkey
sudo iwconfig
sudo dhclient wlan0

That should get you on the right track and give you some search terms. You can do 
wlanctl-ng mibs
to see all the different stuff you can set.

Cheers, Rick

---

### Post by osoviajero on 2005-05-01
[QUOTE=moephan]Jack,

Your directions were just what the doctor ordered. I NEVER would have figured this out on my own. For anyone else who's having this trouble, here are the steps I followed:

1. I installed linux-wlan-ng from synaptic

2. I added the following 4 lines to the bottom of /etc/network/interfaces
# The wireless network interface
auto wlan0
iface wlan0 inet dhcp
	wireless_mode managed

3.I entered the following commands:
sudo wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable
sudo wlanctl-ng wlan0 lnxreq_autojoin ssid="" authtype=opensystem
sudo iwconfig
sudo dhclient wlan0

My wireless modem is not secured, otherwise, looking at iwconfig outputs, I assume I'd have to figure out commands to pass in the keys, etc... 

Using the Network Settings Applet did not work for me. Also, when I rebooted, it took a while for the boot process to give up on bringing up the wireless card. 

Thanks again for your help. I hope anyone else finds this post helpful.

Cheers, Rick[/QUOTE]


Hi there, I tried this and it worked until restart, then it won't. Plus item disappears from device manager. Any tips? I'm an extremely frustrated Linux newbie. Thanks.

---

### Post by moephan on 2005-09-07
osoviajero,

To enable your wireless modem in this way, you need to run these commands every time after you restart. It is most convenient to put them into a shell script and then run the script as su when you want to start up the wireless modem.

Stick with it. It seems the wireless support is oftern one of the hardest things for new linux users to get sorted out.

Cheers, Rick

---

### Post by osoviajero on 2005-09-25
[QUOTE=moephan]osoviajero,

To enable your wireless modem in this way, you need to run these commands every time after you restart. It is most convenient to put them into a shell script and then run the script as su when you want to start up the wireless modem.

Stick with it. It seems the wireless support is oftern one of the hardest things for new linux users to get sorted out.

Cheers, Rick[/QUOTE]
I'm now thrilled that the card is working perfectly upon startup. The thing I did differently was remove WEP encryption and instead use MAC address filtering to secure wireless network. Yeah! \\:D/

---

### Post by plamen5rov on 2006-07-05
Moephan, I have exactly the same laptop - ECS A535 - and it worked fine with Ubuntu 5.10 but I failed several times with installing the new Ubuntu 6.06 on it (the same result with the new Kubuntu and Xubuntu, BTW!).

How did you manage to do it? I think it has something to do with the display driver, but I'm also a Linux newbie...:(

---

