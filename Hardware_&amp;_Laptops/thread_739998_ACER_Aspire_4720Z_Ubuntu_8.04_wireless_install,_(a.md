---
title: "ACER Aspire 4720Z Ubuntu 8.04 wireless install, (atheros AR5BXB63)"
date: 2008-03-30
forum: Hardware &amp; Laptops
---

### Post by surfduke2001 on 2008-03-30
I have installed Ubuntu test of 8.04 on My new laptop, (Dual Boot with the evil Vista, (LOL)). The only trouble was the wireless connect. 

I have done the following and it works now, (Make sure You have a hard line net connection) :

1. Install the ndisgtk program from the package Synaptic Package Manager
2. Windows XP atheros driver from acer.com.cn, pick Wireless Atheros driver.
3. Make a folder in documents file, (I named it Wireless driver).
4. Move the downloaded .zip file from desktop to the new wireless folder.
5. Right click on the .zip file, (and choose extra here).
6. Go to System>Administration>Windows Wirless Drivers, (NDISWRAPPER will open now, (after password is given)).
7. Choose Install Driver.
8. Goto location line, click on the right folder tab and browse to:
Document>Wireless driver>Wireless_Atheros_XP32_XP64_WHQL_(5.3.0.45_logo)>XP32_XP64_WHQL_5-3-0-45_(Negative-Pole)70510>net5211.inf
9. Choose to intall.
10. The driver should now appear in the list on the left.
11. Select the driver, (Left click to highlight), and choose the configure network button, (This will take a few moments.
12. Reboot, Choose the network manager on the tool bar.
13. Select a wireless network, (Surf........)

Have a great day,

Carl

---

### Post by ankgamer on 2008-03-31
Thanks!!
I have the same notebook!
It worked perfectly!

---

### Post by surfduke2001 on 2008-03-31
You are welcome! I love the new stuff. A few bugs are nothing to work around. 

Have agreat night,

Carl

---

### Post by rlward on 2008-04-01
2008.4.1
Carl
thanks.  Your solution worked for me also.  I found the driver at 
[http://down2.driversdown.com/Notebook/09.Wireless_Atheros_V5.3.0.56_XP_XB63_XB62%28WHQL%29.zip](http://down2.driversdown.com/Notebook/09.Wireless_Atheros_V5.3.0.56_XP_XB63_XB62%28WHQL%29.zip)
or
[http://tinyurl.com/265hyw](http://tinyurl.com/265hyw)
For me the Acer site in China was not available with any English navigation and the Canadian site had only Vista versions.
and I puzzled a bit selecting between what must have been a 32 bit versus 64 bit version.

Anyway, your assistance was very much appreciated! 
Rob

---

### Post by steb0ne on 2008-04-25
Thanks, this worked for me also on my new Compaq laptop with the atheros wireless card.

Thanks a lot

---

### Post by escalibur on 2008-04-27
Gracias amigo tengo el modelo acer aspire 4520 pero funciona perfecto , gracias ;):):):):):):):)

---

### Post by blobato on 2008-04-29
Perfect ! Great and simple solution !

Do you made your Wireless LED work ? How ?

Thank's

Bruno Lobato

---

### Post by stoner.hr on 2008-05-01
thanks for that info i onw i Toshiba u300 153 laptop with atheros ar5bxb63 chipset and this guide worked for me too , no aircrack though but it works with network manager i got i running with some old madwifi driver but it didnt worked with nm. update is awaited :D

cheers friend

---

### Post by r0cks0ul on 2008-05-02
I tried doing it on Gutsy didnt work.....

---

### Post by hyperandy on 2008-05-02
Ya it's interesting, this worked for my 8.04. But it should be noted, that because 8.04 and 7.10 detect the wireless card differently on this system you will need different drivers.

On 8.04 @ the command line running lspci -v shows:
```
04:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Subsystem: AMBIT Microsystem Corp. Unknown device 0428
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at 50000000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
```

On 7.10, if I remember correctly, the wireless card was being reported as a Atheros 5006EG 

Those are 2 different drivers. 

On 7.10 I used one I found at the Atheros Site and got driver 6.0.3.85 for Windows XP 32 Bits, the file name will be xp32-6.0.3.85.zip. The file inside was net5416.inf

On 8.04 because it was detected differently I had to use net5211.inf as Carl used in this FIX. 


On 7.10 I used ndiswrapper disabled the internal driver and it turned ON the wifi LED, but on 8.04 using the ndisGTK (ndiswrapper frontend) it did not turn on the LED when wifi was inabled. Currently I think it has something to do with a configuration of state-funcs (run sudo gedit /usr/share/acpi-support/state-funcs to see the functions) I am not sure what I need to change as I just started researching this, any assistance would be great!! I miss my little light. But I guess no LED is better then no Wifi.

Other then that this laptop still rocks. 3D has gotten better but still not perfect, at least a little more usable you don't have to jerry rig it to get it to work now. I love that the sound works out of the box now instead of having to rebuild Alsa drivers. You still have to configure the built-in Mic, but hey, it's only one line in one config file.

---

### Post by JesCed on 2008-05-03
Thank you very much, my friend. This solution worked perfectly on an Acer Aspire 3690-2767, and has solved the very irritating situation of having to boot into Vista (shudder) in order to use WiFi.

---

### Post by goincrazy23 on 2008-05-04
so im a noob to this but the ndis wrapper was successful only now it wont connect to anything i input and re-input my network info dozens of times trying different variations and it will not load any webpages once i hardline to my router it loads no problem but i seem to have no wireless options what am i doing wrong?

---

### Post by hyperandy on 2008-05-06
I don't know what you are doing but I do know if you manually adjust network setting (not using the GUI) then adjust make changed in the GUI you can mess things up. Also are you able to ping anything through the terminal. Just go to the terminal and type ping yahoo.com or whatever you want. I have seen you able to ping and not go through the browser because firefox is not automatically detecting your connection.

---

### Post by ratplant on 2008-05-08
I've been trying for two weeks to get wireless working in either 7.10 or 8.04 on a Toshiba A215-S5837 AMD64 laptop [(http://tinyurl.com/5aqqar)]("http://tinyurl.com/5aqqar"). It has an Atheros AR5BXB63 chipset as well, but so far, no success.

I looked into the madwifi drivers and those appear to still be for 32-bit only, so that leaves ndiswrapper as my only option.

Many other threads I've read suggest that the ath_pci and ath_hal modules should be blacklisted in /etc/modprobe.d/blacklist, and that ath_hal should be disabled in /etc/default/linux-restricted-modules-common.

I've also seen mentioned elsewhere that depmod -a must be run to make wifi work after installing the ndiswrapper module.

No variations I've tried have worked, and at this point, I've tried a *lot*, and done at least a dozen clean installs.

Another very strange thing that's happened on a couple clean install/ndiswrapper install attempts is that the network manager will briefly list my wired network above the "Manual Configuration" option, then my wired network disappears from the list, leaving only the Manual Config option.

I'm completely stuck at this point and could sure use some help. Has anyone gotten wireless working on one of these Toshibas?

Thanks!

Matt

---

### Post by hyperandy on 2008-05-08
What wireless card is being detected (lspci -v)and which driver are you running. Also have you tried to load the 32bit Version to see if that driver worked ok and it wasn't just the 64 bit version. Also if network manager keeps disconnecting have you checked to make sure the wireless card was showing up in the terminal running iwconfig.

---

### Post by ratplant on 2008-05-09
I believe lspci reported the card is a 5006-something,  but I'm at work right now so I'll post the relevant output of lspci -v tonight. There is a sticker on the back of the laptop that says the chipset is an AR5BXB63. I tried a 32-bit driver and got an error (when trying to load it with ndiswrapper I believe), and the card was showing up in iwconfig when I used the 64-bit driver linked from reply #4 in this thread.

The past couple days I've been trying to get an Asus WL-167g USB wireless adapter to work, so that's currently showing up in iwconfig as wlan0. No luck with the WL-167g either, BTW, even though it supposedly works "out-of-the-box".

Thanks!

Matt

---

### Post by ratplant on 2008-05-09
Here's my lspci -v output:

```
14:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Subsystem: AMBIT Microsystem Corp. Unknown device 042a
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at f8200000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: [40] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [60] Express Legacy Endpoint IRQ 0
	Capabilities: [90] MSI-X: Enable- Mask- TabSize=1

```

I see I remembered wrong about the 5006-something. There is also this from lshw:

```
 *-network UNCLAIMED
                description: Ethernet controller
                product: AR242x 802.11abg Wireless PCI Express Adapter
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:14:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix bus_master cap_list
                configuration: latency=0
```

I believe it's reporting unclaimed at the moment because I have been messing with the USB network dongle most recently.

Matt

---

### Post by robertor on 2008-05-15
Hi!
I have tried on a Toshiba Satellite L45-SP4056 and worked perfectly.
Thanks for the guide. I was near to compile ndiwsraper (like before).
Now my friend is very happy with his laptop on line.
Greets!
Roberto

---

### Post by premdiv on 2008-05-16
For me also its working fine except the LED and wifi switch. Is it possible to enable those also??? Iam a newbie....

Thanx in advance

---

### Post by robertor on 2008-05-16
> **premdiv said:**
> For me also its working fine except the LED and wifi switch. Is it possible to enable those also??? Iam a newbie....
Thanx in advance

Hi!
I don't have an acer aspire 4720z. I have a AcerAspire5050. To do work the wifi switch, y use acer_acpi module. you can download from [http://code.google.com/p/aceracpi/]("http://code.google.com/p/aceracpi/").
The led don't work... or work with very low energy.... in the dark... it bright very very low.

Greets!
Roberto

---

### Post by jmunita on 2008-05-18
Hi I have followed the steps mentioned here, but after installing the driver of Windows XP, I can not set the wifi this because I get off. As I fix this?

Help me plis :confused:

[http://www.subirimagenes.com/imagen-pantallazo-484011.html](http://www.subirimagenes.com/imagen-pantallazo-484011.html)

---

### Post by ryanconnarton on 2008-05-20
This does not work for me. It almost does but then it doesn't connect to the internet at the last step. I am running Ubuntu Studio. Does this make a difference? WHat should I do? I really don't wanna ditch Ubuntu Studio for Windows XP (forget Vista all together). Help me out you Linux gurus!

---

### Post by robertor on 2008-05-20
what does say a iwconfig? iwlist wlan0 scan?
have you ever tried acer_acpi module? with it you can turn on the wifi.
Greets!
Roberto

---

### Post by ratplant on 2008-05-20
I *finally* got wireless working on my Toshiba A215-S5837 AMD64 laptop after about a month of effort, and too many clean installs to count.

What finally worked was installing 32-bit Ubuntu and then following the instructions in post #1, using the 32-bit driver from the first link in post #4.

Still, there is some strangeness.

My wireless network again only briefly appeared under "Wireless Networks" in the network manager, then disappeared leaving only the "Manual Configuration" option. I use static IPs on my network, so I had to manually config anyway. I'm using a WEP 64-bit hex key. Yes, I know it's not the best, but that's how my other wireless devices are currently configured and I don't feel like changing them all right now.

The signal strength indicator also briefly appeared in the toolbar, then disappeared.

It took a couple minutes for the networking to realize I had unplugged the wired connection and start using the wireless.

Last, the transfer speeds are much slower than when I boot into Vista.

---

### Post by robertor on 2008-05-20
> **ratplant said:**
> 
Last, the transfer speeds are much slower than when I boot into Vista.

that's normal if you are using ndiswrapper. I think that the top for trnasfer using ndiswrapper are 2 Mbps.

Greets!
Roberto

---

### Post by isharra on 2008-05-26
> **robertor said:**
> that's normal if you are using ndiswrapper. I think that the top for trnasfer using ndiswrapper are 2 Mbps.

Since I'm getting 6Mbps transfers I wonder about that. Then again I'm using ndiswrapper compiled from svn rather than the default package. Oddly enough I switched to primarily using linux on this laptop because my vista wireless transfers were slow.

For what it's worth, 64 bit system install, xp64-5.3.0.56-whql.zip (no led lights). The 6.x.x.x series (working led) drivers seem to released for xp in 32bit only, the 7.x.x.x series uses a new driver athwx.sys which produces an oops with ndiswrapper.

---

### Post by Dragonlaw on 2008-05-26
THANK YOU SO MUCH!!!

I don't know who else to thank really. I was so scared that I couldn't get any internet access!

THANKS!

---

### Post by isharra on 2008-06-01
If you haven't been keeping track of [madwifi ticket 1679]("http://madwifi.org/ticket/1679") there's additional news for the driver. Sam Leffler posted a new hal firmware blob dated 50080528, with it and the current svn trunk madwifi code the wifi is working in 64bit (no led though). Just did about 4 hours of network tests, so far it seems that transfer speed is slightly lower that with ndiswrapper but latency is also down a bit so it's actually responding better for interactive applications.

---

### Post by Ub2daUntu on 2008-06-09
Hey i have the exact same laptop and the exactly same problem. no wireless. and i was following your steps and everything was going good up untill the point where i need to install the driver. I locate the .inf file and click install but it doesnt appear in the list at the left. Any ideas?

---

### Post by robertor on 2008-06-09
> **Ub2daUntu said:**
> Hey i have the exact same laptop and the exactly same problem. no wireless. and i was following your steps and everything was going good up untill the point where i need to install the driver. I locate the .inf file and click install but it doesnt appear in the list at the left. Any ideas?

Which .inf have you ever tried? When i install it on my laptop i have had to trid a pair of .inf files.
Greets!
Roberto

---

### Post by Syspeg on 2008-06-13
I have the same type of adapter. My Laptop is LG E510. 

This is one solution. 

Disable: 
* Atheros Hardware Access Layer (HAL)
* Support for Atheros 802.11 wireless LAN cards.  

Restart. 

Open a terminal. 

$ sudo apt-get install build-essential
$ wget [http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz)
$ tar xfz madwifi-ng-r2756+ar5007.tar.gz
$ cd madwifi-ng-r2756+ar5007
$ make
$ sudo make install
$ sudo modprobe ath_pci

Explanation in swedish is [here.]("http://syspeg.googlepages.com/programmering2")

---

### Post by Nidding on 2008-06-15
I don't have a wired connection, but only another computer from which I can download. Can anyone tell me how to get this fix to work in this way?

---

### Post by jim_reaper on 2008-06-16
Damn!
Worked for me. Downloading an ACER driver - who'da thought?!

---

### Post by Danielkida on 2008-06-19
I have a toshiba satellite L40 and ndiswrapper didnt work for me. When i click to install the driver my computer completely freezes up every time!

---

### Post by abhi0204 on 2008-06-23
> **surfduke2001 said:**
> I have installed Ubuntu test of 8.04 on My new laptop, (Dual Boot with the evil Vista, (LOL)). The only trouble was the wireless connect. 

I have done the following and it works now, (Make sure You have a hard line net connection) :

1. Install the ndisgtk program from the package Synaptic Package Manager
2. Windows XP atheros driver from acer.com.cn, pick Wireless Atheros driver.
3. Make a folder in documents file, (I named it Wireless driver).
4. Move the downloaded .zip file from desktop to the new wireless folder.
5. Right click on the .zip file, (and choose extra here).
6. Go to System>Administration>Windows Wirless Drivers, (NDISWRAPPER will open now, (after password is given)).
7. Choose Install Driver.
8. Goto location line, click on the right folder tab and browse to:
Document>Wireless driver>Wireless_Atheros_XP32_XP64_WHQL_(5.3.0.45_logo)>XP32_XP64_WHQL_5-3-0-45_(Negative-Pole)70510>net5211.inf
9. Choose to intall.
10. The driver should now appear in the list on the left.
11. Select the driver, (Left click to highlight), and choose the configure network button, (This will take a few moments.
12. Reboot, Choose the network manager on the tool bar.
13. Select a wireless network, (Surf........)

Have a great day,

Carl

Dear 

Till installing nidisgtk was ok. but on select the driver i got a funny message "Hardware Present : no"

can you please help.

regards 

abhi0204

---

### Post by abhi0204 on 2008-06-23
Dear

Till installing nidisgtk was ok. but on select the driver i got a funny message "Hardware Present : no"

can you please help.

regards

abhi0204

---

### Post by abhi0204 on 2008-06-23
> **surfduke2001 said:**
> I have installed Ubuntu test of 8.04 on My new laptop, (Dual Boot with the evil Vista, (LOL)). The only trouble was the wireless connect. 

I have done the following and it works now, (Make sure You have a hard line net connection) :

1. Install the ndisgtk program from the package Synaptic Package Manager
2. Windows XP atheros driver from acer.com.cn, pick Wireless Atheros driver.
3. Make a folder in documents file, (I named it Wireless driver).
4. Move the downloaded .zip file from desktop to the new wireless folder.
5. Right click on the .zip file, (and choose extra here).
6. Go to System>Administration>Windows Wirless Drivers, (NDISWRAPPER will open now, (after password is given)).
7. Choose Install Driver.
8. Goto location line, click on the right folder tab and browse to:
Document>Wireless driver>Wireless_Atheros_XP32_XP64_WHQL_(5.3.0.45_logo)>XP32_XP64_WHQL_5-3-0-45_(Negative-Pole)70510>net5211.inf
9. Choose to intall.
10. The driver should now appear in the list on the left.
11. Select the driver, (Left click to highlight), and choose the configure network button, (This will take a few moments.
12. Reboot, Choose the network manager on the tool bar.
13. Select a wireless network, (Surf........)

Have a great day,

Carl

Dear 

Till installing nidisgtk was ok. but on select the driver i got a funny message "Hardware Present : no"

can you please help.

regards 

abhi0204

---

### Post by jualin on 2008-06-23
Type > lspci on the Terminal and post the output. Also try pressing the "Wireless On or Off" button located on the upper part of your keyboard. I think that it has a "Satellite" icon (not sure, since i dont have the computer in front of me). Sometimes I press that button ny mistake and the wireless stops working.

---

### Post by unl3a5h3d on 2008-07-02
> **Danielkida said:**
> I have a toshiba satellite L40 and ndiswrapper didnt work for me. When i click to install the driver my computer completely freezes up every time!
I have the exact same problem, it freezes everytime. But I have an Acer Aspire 3680. How do I get it to work? Please and thanks!

---

