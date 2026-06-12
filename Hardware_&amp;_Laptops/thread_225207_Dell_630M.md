---
title: "Dell 630M"
date: 2006-07-29
forum: Hardware &amp; Laptops
---

### Post by rhart on 2006-07-29
Hi

I have been trying out Ubunto 6.06 on my Dell 630M and I am very pleased so far, it has detected all of the hardware and my Wifi works, though I've had to turn off the WPA in my router as ubuntu's wifi config doesn't seem to support WPA. 

The only minor problem is the screen resolution which under windows runs at 1280 x 800, however under Ubuntu it will only run at 1024 x 768.

But that is it

Ralph Hart

---

### Post by ko16736 on 2006-08-05
I am having the **exact same problem.** On the exact same computer. I haven't tried fixing it or anything yet, so someone please post here to help us out.

---

### Post by ianmillington on 2006-08-29
Basically there is no resolution setting of 1280 x 800 in the default set up of xorg.

Other more knowledgable people will be able to show you how no doubt but basically you need the to download the 915 resolution package and then edit the xorg.conf file IIRC.

Unfortunately my setup was changed for me by the IT guy at work, but it is worth doing as the difference was startling. 

Ian

---

### Post by viraldhimar on 2006-08-30
Hey guys,

I also have a Dell 630m for awhile now 1yr and to get the 1280x800 you have to use 915resolution. If it isn't installed when you install Dapper do 
sudo apt-get install 915resolution

After installation as root (aka sudo or do sudo -i root to stop typing sudo)
915resolution -l (thats "l" as in linux) to list all the modes that support you lappy.

Next pick a mode that you are never going to use such as 38 and do:
915resoultion 38 1280 800 32 

To overwrite it. Now the only problem is having this done everytime you boot up so what I did and I don't know if this is right is put the above line  into my bootmisc.sh (/etc/init.d/bootmisc.sh) Basically this loads anything you need to on boot.

put /usr/bin/915resolution 38 1280 800 32 right after:

[ -z "$DELAYLOGIN" ] && DELAYLOGIN=yes
[ -z "$EDITMOTD" ] && EDITMOTD=yes
[ -f /etc/default/rcS ] && . /etc/default/rcS
/usr/sbin/915resolution 1280 800 32  <-- right here.

save and exit and reboot. That should do it!

---

### Post by freund on 2006-11-04
> I have been trying out Ubunto 6.06 on my Dell 630M and I am very pleased so far, it has detected all of the hardware and my Wifi works, though I've had to turn off the WPA in my router as ubuntu's wifi config doesn't seem to support WPA.

I got it to work manually thru a script:

#!/bin/bash
PATH=/sbin:/bin:/usr/bin:/usr/sbin/
#for hidden SSID
iwconfig eth1 essid yah
sleep 2
wpa_supplicant -Bw -ieth1 -c/etc/wpa_supplicant.conf -Dwext
sleep 3
dhclient eth1

I found the sleep 3 & 3 necessary

My config file is:
ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=wheel
eapol_version=1
ap_scan=1
fast_reauth=1

#network={
#	ssid="any"
#	key_mgmt=NONE
#}


# Only WPA-PSK is used. Any valid cipher combination is accepted.
network={
	ssid="yah"
#	scan_ssid=0
	proto=WPA
	key_mgmt=WPA-PSK
	pairwise=TKIP
	group=TKIP WEP104 WEP40
#	psk="DaPassPhrase" have to generate yourself thru  #usr/sbin/wpa_passphrase
        psk=hahahahahahahahahahahahahahahahahah
	priority=1
}

---

