---
title: "No WiFi on Gateway M675 Laptop (Broadcom BCM4306)"
date: 2005-05-05
forum: Hardware &amp; Laptops
---

### Post by worldwidedvds on 2005-05-05
I have a Gateway M675 laptop.  I install Ubuntu on it fine.  I am having problems getting the wifi set up though.  I followed this [post](http://ubuntuforums.org/archive/index.php/t-22954.html) 
I can now get wlan0 to come up in the Network Config, but I can't get it to work.  I noticed that the antenna button on my laptop is not lit up though, so I'm not even sure if the wifi is active.

I also am not able to get the sound working on the laptop.

Any help would be greatly appreciated!

Thanks!

Sean

---

### Post by Staesys on 2005-05-05
I have a PCMCIA card with the same chipset which I got working with Ndiswrapper. For the longest time I couldn't get it to work with WEP, until I changed my wireless router and then it connected right away.

Can you see the wireless adaptor in the device manager? It's usually at the very bottom. If so, there's a few commands to try in the terminal to see what's going on.

```
iwconfig
``` 

Will show you all of the wireless adaptors. Is yours listed?

```
iwlist wlan0 scanning
``` 

Should show you all of the access points around you if your card supports scanning.

Assuming your card shows up and you can see access points with it, the next step is to try and connect.
```
iwconfig wlan0 essid <name of your AP>
dhclient wlan0
``` 

This should get you an ip address via DHCP from your AP.

```
ping www.yahoo.com
``` 

Should then get you a return from Yahoo.

Once you get the card working without WEP then you can try enabling it and go from there.

```
iwconfig wlan0 enc <key>
``` 

Will of course set your WEP encryption key.

Hopefully this will help get you connnected.

-Paul

---

### Post by Hieronymus on 2005-05-05
Well, as follows:

First download the ndiswrapper-1.2-rc1 package from [http://sourceforge.net/project/show...lease_id=319772]("http://sourceforge.net/project/showfiles.php?group_id=93482&package_id=125562&release_id=319772")
Because the 1.1 package that comes with ubuntu gives problems sometimes you have to remove it first, here is a howto to get everything working:

```

sudo modprobe -r bcmwl5
sudo rmmod ndiswrapper
sudo apt-get remove ndiswrapper-utils
sudo rm -r /etc/ndiswrapper/
sudo rm -r /etc/modprobe.d/ndiswrapper
sudo apt-get install linux-headers-2.6.10 (whatever version)
cd /usr/src/
sudo tar xvzf ndiswrapper-1.2-rc1
cd /usr/src/ndiswrapper-1.2-rc1/
sudo make
sudo make install
cd /the dir where your windows networkdrivers are/
sudo ndiswrapper -i bcmwl5 (or other driver name if you have another card)
sudo ndiswrapper -l (making sure the driver is installed)
sudo modprobe ndiswrapper
sudo dmesg (you sould see that the card is installed)
sudo iwlist wlan0 scan (to get a list of APs)
sudo ndiswrapper -m (ndiswrapper will now be loaded automatic at bootup)

```
 
btw for every bcmwl5 put your own driver name! if you are working with 64 bit Ubuntu get your broadcom 64 bit drivers here: [http://ubuntuforums.org/attachment.php?attachmentid=186]("http://ubuntuforums.org/attachment.php?attachmentid=186")
 
now goto System >> Administration >> networking, choose your wlan adapter, properties, check the radiobutton behind "This device is configured", set your essid, wep key and set the configuration to DHCP, close, activate and check if your inet works:

```

ping -c 3 ubuntuforums.org

```

Good luck, Hieronymus

---

### Post by worldwidedvds on 2005-05-05
[QUOTE=Hieronymus]Well, as follows:

First download the ndiswrapper-1.2-rc1 package from [http://sourceforge.net/project/show...lease_id=319772]("http://sourceforge.net/project/showfiles.php?group_id=93482&package_id=125562&release_id=319772")
Because the 1.1 package that comes with ubuntu gives problems sometimes you have to remove it first, here is a howto to get everything working:

```

sudo modprobe -r bcmwl5
sudo rmmod ndiswrapper
sudo apt-get remove ndiswrapper-utils
sudo rm -r /etc/ndiswrapper/
sudo rm -r /etc/modprobe.d/ndiswrapper
sudo apt-get install linux-headers-2.6.10 (whatever version)
cd /usr/src/
sudo tar xvzf ndiswrapper-1.2-rc1
cd /usr/src/ndiswrapper-1.2-rc1/
sudo make
sudo make install
cd /the dir where your windows networkdrivers are/
sudo ndiswrapper -i bcmwl5 (or other driver name if you have another card)
sudo ndiswrapper -l (making sure the driver is installed)
sudo modprobe ndiswrapper
sudo dmesg (you sould see that the card is installed)
sudo iwlist wlan0 scan (to get a list of APs)
sudo ndiswrapper -m (ndiswrapper will now be loaded automatic at bootup)

```
 
btw for every bcmwl5 put your own driver name! if you are working with 64 bit Ubuntu get your broadcom 64 bit drivers here: [http://ubuntuforums.org/attachment.php?attachmentid=186]("http://ubuntuforums.org/attachment.php?attachmentid=186")
 
now goto System >> Administration >> networking, choose your wlan adapter, properties, check the radiobutton behind "This device is configured", set your essid, wep key and set the configuration to DHCP, close, activate and check if your inet works:

```

ping -c 3 ubuntuforums.org

```

Good luck, Hieronymus[/QUOTE]
 Thanks guys.  I couldn't get the Netoworking gui to work for me.  But I was able to use the commands Staesys mentioned to get it up and running.

Now I just need to get the audio working on this thing.

---

