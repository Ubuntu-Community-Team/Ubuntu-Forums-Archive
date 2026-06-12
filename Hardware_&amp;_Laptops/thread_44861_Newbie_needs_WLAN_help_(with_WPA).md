---
title: "Newbie needs WLAN help (with WPA)"
date: 2005-06-27
forum: Hardware &amp; Laptops
---

### Post by mjbanks on 2005-06-27
I'm rather noob-ish, so please excuse me if I'm doing something stupid here  :?

I installed the driver for my wireless card (linksys wpc54gs) on my toshiba satellite laptop. I installed and setup wpa-supplicant the way described in this thread. I edited wpasupplicant.conf properly.

I then go to run this:

```
sudo ifconfig wlan0 up && /usr/sbin/wpa_supplicant -Bw -Dndiswrapper -iwlan0 -c/etc/wpa_supplicant.conf && dhclient wlan0
```

and I get some crazy error messages...

```
user@ubuntu:~$ sudo ifconfig wlan0 up && /usr/sbin/wpa_supplicant -Bw -Dndiswrapper -iwlan0 -c/etc/wpa_supplicant.conf && dhclient wlan0 
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium. 
All rights reserved. 
For info, please visit http://www.isc.org/products/DHCP 

sit0: unknown hardware address type 776 
can't create /var/lib/dhcp3/dhclient.leases: Permission denied 
SIOCSIFADDR: Permission denied 
SIOCSIFFLAGS: Permission denied 
SIOCSIFFLAGS: Permission denied sit0: unknown hardware address type 776 
Open a socket for LPF: Operation not permitted
```

Anybody have any ideas what's going wrong? I'm really liking ubuntu so far, and just wish I could get this wireless up and running.

Thanks!

---

### Post by elsewhere on 2005-06-28
Those are permission errors, I think you're missing a "sudo"

> sudo ifconfig wlan0 up && /usr/sbin/wpa_supplicant -Bw -Dndiswrapper -iwlan0 -c/etc/wpa_supplicant.conf && **sudo** dhclient wlan0

Not sure though, I simply use *ifup wlan0* to bring up my wireless (after wpa_sup is running).

Hope this helps ?

Cheers,
KV

---

### Post by mjbanks on 2005-06-28
Here's some further info. I downloaded and installed (ndiswrapper -i driver.inf) the driver for my Linksys WPC54GS card (from the Linksys site).

If I run 

```
sudo ifconfig wlan0 up && /usr/sbin/wpa_supplicant -w -Dndiswrapper -iwlan0 -c/etc/wpa_supplicant.conf -dd
``` 

this is the output I get:

```
Initializing interface (2) 'wlan0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
Own MAC address: xx:xx:xx:xx:xx:xx
Failed to enable WPA in the driver.
Failed to disable WPA in the driver.
rmdir[ctrl_interface]: Bad address
```

(mac address removed for security)

I'm not really understanding what's going on here, since I'm pretty new to all this. Does anyone have any ideas or suggestions?

For further info, I have my SSID broadcast disabled and MAC filtering set to "on" on the router, with the wireless MAC entered correctly (works under Windows). In the wpa_supplicat.conf, I have:

```
ap_scan=2
network={
	scan_ssid=1
        ssid="myssidhere"
        #psk="mypskhere"
        key_mgmt=WPA-PSK
        proto=WPA
}
```

Does any of that have an impact on anything?

Thanks,
Matt

---

### Post by mjbanks on 2005-06-29
Ok well if I add in a sudo before dhclient wlan0, this is the output I get...

```
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/wlan0/<mac address here>
Sending on   LPF/wlan0/<mac address here>
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

In the network settings dialog box, I set it to static IP to try and make the dhcp stuff go away, but that didn't work. DHCP works with this card in windows and on other wireless things on the network.

Any ideas?

Thanks,
Matt

---

### Post by elsewhere on 2005-06-29
From the output of your wpa_supplicant, it looks like there may be an issue with wpa_sup interacting with your card, or maybe even with ndiswrapper itself.  That would explain why you're not able to dhcp an address, because the card can't link with the AP.

What type of output are you getting from "iwconfig" ? Is wlan0 showing up, and isn't it showing an association with your AP ?

Also, is the driver you've installed into ndiswrapper correct for the wifi card ?  Does "ndiswrapper -l" confirm "driver present, hardware present" ?

Also, one last point, I ran into issues with wpa_supplicant when hiding my SSID.  May want to try broadcasting again to see if you can connect.

Sorry can't be a little more specific, maybe something here will help narrow down the problem ?

Cheers,
KV

---

### Post by mjbanks on 2005-06-29
If I run "ndiswrapper -l", it does say driver present, hardware present. Also, if I run iwconfig, there is info on wlan0. And I'm sure it's the correct driver also.

I'll try broadcasting the SSID tomorrow to see if that helps at all. 

I'm really hoping I can solve this issue because I would love to dump windows completely  ;-)

---

### Post by fizgig on 2005-06-30
Forget about dclient at first.  The way to figure out what's going on is to type **iwconfig** after running just the wpa_supplicant line.

In the results of the iwconfig command, look at the ESSID value.  If it's the name of your access point, you're good.  If it's something that looks like "any" (I forget the exact phrase) then you're not connected to your router and dhclient will never work.  From the error messages I see, looks like you'll get the "any" value which is bad.  (Another way to tell is to look at the Access Point value.  If it's all zeros, that's bad too)

I found wpa_supplicant only worked for me by prefixing **sudo **and using **-B** instead of **-Bw**.  Also, make sure that your conf file has the results of the wpa_passphrase so you have a crazy-long random-looking password in your conf file.

Finally, make sure you're using the right network driver.  I have to use ndiswrapper but I don't know what driver you're using (or how to find out what it is).  In short, I'd recommend no encryption at first just to see if your network driver is working (if you haven't yet).  In that scenario use the network utility in Gnome to connect and make sure you've configured your router for no encryption.  Once that's squared away you can concentrate your efforts on wpa_supplicant.

A neat page that details wpa_supplicant and got me working is [here]("http://hostap.epitest.fi/cgi-bin/viewcvs.cgi/*checkout*/hostap/wpa_supplicant/README?rev=HEAD&content-type=text/plain").

---

### Post by mjbanks on 2005-06-30
I know if I run iwconfig, the SSID says Any. I forget the command to set it in there? I have it set in the Gnome GUI. I thought it was "ifconfig wlan0 essid ESSID", but that's not it. I'll try it with no encryption tonight.

The other thing that bothers me is when I run it with -dd, it says Failed to enable WPA in the driver, which I don't uderstand. It's the same driver that's used in windows. It's the only driver available for the WPC54GS.

I'll play around more tonight. I know it's doable because other people here have done it with no problems. I also have a WPC54G card laying around that I could try. I would have to remove the driver with ndiswrapper first, which I have no clue how to do, then I could install the driver for the other card.

Also, the version of ndiswrapper that comes with Ubuntu is 1.0 RC2. The current version on sourceforge is 1.1. How would I go about updating that? I tried apt-get install ndiswrapper, but it didn't find anything. If that the way to update software anyway?

---

### Post by fizgig on 2005-06-30
As I mentioned before:  Did you try getting wireless to work without any security enabled at all?  You can easily do this via the gnome network manager.  That is a huge question so please let me know.

Assuming that you did get it to work without security enabled, the next step would be to disable the wireless card in the Gnome menu.  It wont be controlling it anymore.

The thing that sets the ssid of your wireless client is the wpa_supplicant program.  After you successfully run the program, your ssid will be set.

---

### Post by mjbanks on 2005-06-30
I'll be trying tonight with no encryption and ssid broadcast. I'm at work now, so I can't test it yet.

Also, whenever I've been playing with it, in the Gnome GUI the wireless card is active. Do I want it to deactivate it if I'm using wpa supplicant?

---

### Post by carlos_ on 2005-06-30
I just got my WPC54GS card working with WPA after running into a similar problem.  After running "ndiswraper -i driver.inf" and "sudo modprobe ndiswrapper", run "dmesg" and look at the ndiswrapper info... make sure it says something like:

encryption modes supported: WEP, WPA with TKIP, WPA with AES/CCMP

Mine only listed WEP.  This signalled to me that ndiswrapper wasn't reading the driver correctly.  I uninstalled ndiswrapper (I think it was version 1r02... or something like that).  I then went to sourceforge and got version 1.1 tar file and installed it manually.  This required me to install the kernel source which I simply did using synaptic (searched for "<KERNEL_VERSION>-headers".  Everything was pretty straightforward after that.

---

### Post by mjbanks on 2005-06-30
Carlos - I was sort of worried that my driver wasn't working just because it says WPA not supported. I'll check out the dmesg tonight. I wonder if there's any way to apt-get the newest ndiswrapper to upgrade it?

---

### Post by carlos_ on 2005-06-30
I'm a little new to ubuntu/debian apt-get/synaptic so I'm not sure.  The version of ndiswrapper that I tried initially (1r02 or something like that) came from synaptic using the default settings, so my guess would be that you would need to somehow add a new/different repository...?  After running "dmesg" you should be able to see which version of ndiswrapper you are running.

I can tell you that the wpc54gs driver from the ndiswrapper sourceforge wiki page is fine... I've used it various times with Mandrake/Mandriiva 10.1/2005LE and now Ubuntu.

Don't give up, the speedbooster works great (>54 MBps) once you get it up and running with ndiswrapper/wpa.

---

### Post by mjbanks on 2005-06-30
Speedbooster isn't too much of a concern for me... I'm running Sveasoft firmware on my WRT54GS routers (I have 2 linked with WDS). I have the transmit rate set to 200 on both, which is higher than the speedbooster would set channel 6 anyway.

By the way, I just saw this on the ndiswrapper page...

If you want to use apt-get add the following line to /etc/apt/sources.list: 

```
deb http://ndiswrapper.sourceforge.net/debian ./
```


I'm going to try adding that tonight when I get home from work and see if it's possible to upgrade ndiswrapper.

---

### Post by carlos_ on 2005-06-30
That's good to know about adding the sourceforge line to apt-get.

Just curious about your routers and firmware...I didn't know you could increase the speed.

1. Will firmware alone get you to 200 MBps?
2. What about the adapter?  Do you need a special driver?  Does it have to be Linksys GS?

---

### Post by mjbanks on 2005-06-30
Hi Carlos - sorry, I meant TX power (in mW). Basically, from my understanding, the router and card use boosted power to increase the speeds up to 125mbps. I also have "afterburner" mode set to on, which is the GNU name for Speedbooster

---

### Post by mjbanks on 2005-06-30
I'm trying to install the new ndiswrapper manually, and I'm having problems when I run make. I get some errors, saying commands aren't found in the headers folder. I downloaded the linux headers too. Any ideas?

---

### Post by carlos_ on 2005-06-30
I followed the instructions from the ndiswrapper wiki page:

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation)

It mentions you might have to make a link.  I didn't have to make a link... downloading the source-headers was sufficient.  However, I do believe I needed to make a link in Mandrake.

It might be unrelated, but I also downloaded gcc  compiler... I'm not sure what  your error message was.  Also, keep in mind you need to specify "sudo" (root priveleges) when executing most commands when installing new software.

---

### Post by mjbanks on 2005-07-01
I completely forgot to link things up. I'll have to try that tonight (or maybe next week since it's July 4th weekend). I'll download the gcc compiler as well.

When I went to uninstall ndiswrapper I was having some troubles. The kernal module that the ndiswrapper uninstall page refers to in /lib/modules/`uname -r`/misc isn't there. In fact, the misc directory isn't even there. What all did you do to uninstall the previous version? I want to make sure I have it all removed before I go ahead and install the new one.

Thanks,
Matt

---

### Post by mjbanks on 2005-07-01
OK here's some updates. With SSID broadcast and all encryption off, I can get online with the wireless. I uninstalled ndiswrapper, got gcc compiler and linux headers, installed newest ndiswrapper from source. In dmesg it now says WPA enabled in the driver.

Now my problems are with wpa_supplicant. I'm having trouble getting it to connect if I enable WPA.

Here's the errors I'm getting if I run:

```
sudo ifconfig wlan0 up && /usr/sbin/wpa_supplicant -Bw -Dndiswrapper -iwlan0 -c/etc/wpa_supplicant.conf && sudo dhclient wlan0
```

I get this:

```
Initializing interface (2) 'wlan0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
ioctl[SIOCSIWMODE]: Operation not permitted
Could not configure driver to use managed mode
SIOCSIFFLAGS: Permission denied
Could not set interface 'wlan0' UP
socket(PF_PACKET, SOCK_RAW): Operation not permitted
SIOCSIFFLAGS: Permission denied
rmdir[ctrl_interface]: Bad address
```

Anyone have any ideas what I'm doing wrong?

If I disable wpa on the router and just run ifup wlan0, it connects right away, gets an IP address by DHCP, and can browse the internet, lan, etc.

Thanks,
Matt

---

### Post by lonyz7 on 2005-07-06
What does your .config and wpa_supplicant.conf say? 

Just remember to take out your SSID and Passphrase before posting up here.

---

### Post by mjbanks on 2005-07-06
I'll post that info when I get home from work tonight. Which .config file are you referring to (location)?

---

