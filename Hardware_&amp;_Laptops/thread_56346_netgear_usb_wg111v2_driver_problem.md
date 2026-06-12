---
title: "netgear usb wg111v2 driver problem"
date: 2005-08-12
forum: Hardware &amp; Laptops
---

### Post by dajomu on 2005-08-12
This is what I've done so far. If anyone got any ideas that would be nice.
I installed the latest ndiswrapper for hoary on my laptop compaq evo n1020v.
I downloaded from [www.netgear.com](www.netgear.com) the latest driver for netgear wg111v2 - wg111v2_v1.0.0.5.zip
I unshielded the data1.cab and found the XP directory with the Net111v2.inf and WG111v2.sys files in it.
I did
[INDENT]ndiswrapper -i Net111v2.inf[/INDENT]
 

[INDENT]ndiswrapper -l[/INDENT]
[INDENT]Installed ndis drivers:
net111v2        driver present[/INDENT] 

As you can see there is no hardware present.

I tried
[INDENT]modprobe ndiswrapper[/INDENT] 
but nothing happens

The command, gave me this:
[INDENT]dmesg | grep ndiswrapper[/INDENT] 
[INDENT]diswrapper version 1.0rc2 loaded (preempt=yes,smp=no)
ndiswrapper: driver net111v2 (NETGEAR Inc.,03/24/2005,5.111.05.0324) added[/INDENT] 

iwconfig gives me
[INDENT]lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.[/INDENT]

---

### Post by kingojb on 2005-08-12
Is 1.0rc2 the version in the hoary repos? I don't think I ever got the wg111 to work with that version, it works with 1.1 for me though under Hoary and Breezy. Maybe try installing a more recent version.

---

### Post by dajomu on 2005-08-13
I got the thing installed following this how-to:
[https://wiki.ubuntu.com//SetupNdiswrapperHowto](https://wiki.ubuntu.com//SetupNdiswrapperHowto)

Thanks for all the help guys

---

### Post by krake on 2005-10-22
Just to let others with the same problem know:

The above mentioned ndiswrapper-howto in the wiki is great. However if you are using Breezy  there's no need to compile as it comes with ndiswrapper version 1.1 which I got to work with the netgear wg111v2 without any problems.

---

### Post by Kangaroo on 2005-11-13
Just to share my experiences with the WG111v2 (Realtek Chip RTL8187). 

I was trying to get the drivers from my windows cd installed with Ndiswrapper and ndisgtk supplied through the breezy-repositories (version 1.1 of Ndiswrapper). However after an afternoon of no luck i gave up yesterday. 

Today i saw, that there is a newer version of Ndiswrapper available on their website (Version 1.5). So after following dajomu's link i have downloaded the source and built a .deb and installed it. Et voila, it works. 

Despite from the packages mentioned in the wiki you will also need gcc-3.4 to build the .deb, so don't forget to download that as well. 

So i can not share krake's experience, that it just plain worked with 1.1 but at least i finally got it to work with 1.5.

edit: Just tried to unplug and re-plug the WG111v2 and that works flawlessly as well. The only thing i needed to do is to manually activate it in the network settings of network-admin.

edit2: If you have the same version of the WG111v2 (RTL8187) as i do, don't bother with downloading the setup.exe from Netgear's site and mess around with unshield. There's a download from Realtek's site with the .inf and .sys needed, without having to unshield.
[http://www.realtek.com.tw/downloads/downloads1-3.aspx?Keyword=RTL8187]("http://www.realtek.com.tw/downloads/downloads1-3.aspx?Keyword=RTL8187")

edit3: Just (23rd dec. '05) saw, that Realtek released a linux native driver on 20th dec. Haven't tried that one myself, but probably there won't be a need to work with ndiswrapper anymore (I always prefer "linux-native" stuff over "emulated" ;-))

---

### Post by daahli on 2005-12-30
hey,

I've been trying to get this adapter working all day, and just stumbled upon this thread. I downloaded the new realtek linux driver but have no idea howto install it. I know it's a script, but I'm a newbie and have no idea how to proceed.

Any help appreciated!

Thanks

---

### Post by antonius83 on 2006-02-23
Hello guys! I saw that it was no problem to install the wg111v2 on ubuntu with ndiswrapper.. but the problem is the with ndiswrapper you have no monitor mode! So I can't use programs like kismetm aircrack, airodump... But I found linux.drivers on the web. The problem is that I have no idea how to install them!! You said you found them too. Has anybody tried them?? 
Thank you

---

### Post by sohailubuntu on 2006-02-23
Just installed Ubuntu yesterday, having major issues installing driver for this adapter. Can someone please post a solution that works. I'm using ndiswrapper -i to install driver and it's saying already installed, but when I type 
ndiswrapper-l
incorrect driver?????

---

### Post by sohailubuntu on 2006-02-23
[QUOTE=dajomu]I got the thing installed following this how-to:
[https://wiki.ubuntu.com//SetupNdiswrapperHowto](https://wiki.ubuntu.com//SetupNdiswrapperHowto)

Thanks for all the help guys[/QUOTE]

I followed the instructions and I'm getting this message

root@Sohail:/# ndiswrapper -i /home/sohail/Desktop/Utility/data1.cab
Installing data1.cab
root@Sohail:/# modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.12-9-386/kernel/drivers/net /ndiswrapper/ndiswrapper.ko): Operation not permitted

why am I getting this error message ?

---

### Post by sohailubuntu on 2006-02-26
UPDATE: Problem fixed

I had installed multiple drivers, and deleted all the previous incorrect drivers and once again went throught the instructions.

---

### Post by impuwat on 2006-04-05
[QUOTE=daahli]hey,

I've been trying to get this adapter working all day, and just stumbled upon this thread. I downloaded the new realtek linux driver but have no idea howto install it. I know it's a script, but I'm a newbie and have no idea how to proceed.

Any help appreciated!

Thanks[/QUOTE]

I'm in the same position.  Just installed Ubuntu yesterday on a computer I put together from parts laying around.  It seems to be running well but now I want to connect it to my home wi-fi.  I have an extra Netgear WG111v2 I can use.  

I found a linux driver from [http://linux-wless.passys.nl/query_hostif.php?hostif=USB&zoek=Show](http://linux-wless.passys.nl/query_hostif.php?hostif=USB&zoek=Show) and used a pocket drive to transfer it and extracted it to the desktop in Ubuntu.  Now what?

I've researched the forums a little bit and found this thread.  Hopefully daahli, you found how to install the driver and can step me through it.  

Thank you.

---

### Post by gurkburk on 2006-04-19
Im having a pretty weird problem getting my wg111/usbwireless working on my laptop with ubuntu, ontop of that im pretty new to linux so im having problems solving this myself, as of now I use a network-cable whenever I wanto acces internet on my laptop, which feels pretty stupid since I have had wireless working in winxp all the time... oh well onwards to the actuall problem:

I have as I mentioned  I am using a laptop, a packard bell easynote(EasyNote B3602D), ive gotten ubuntu to work pretty good, the builtin-nic works with a cable etc, its just this usb-wireless problem thats left basically.

This is what I did to get as faar as I did (I used [https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto](https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto) to have a clue what to do).

[INDENT]1. downloaded latest drivers for windows (1.219) from [http://www.realtek.com.tw/downloads/downloads1-3.aspx?Keyword=RTL8187](http://www.realtek.com.tw/downloads/downloads1-3.aspx?Keyword=RTL8187) for the RTL8187L-chip.
2. Installed ndiswrapper-utils with the Synaptic Package Manager.
3. sudo ndiswrapper -i ./Netrtuw.inf
4. ndiswrapper -l gave me this result:
Installed ndis drivers:
netrtuw driver present, hardware present
So faar, so good.
5.  sudo depmod -a
6. sudo modprobe ndiswrapper
[/INDENT]
Now, it doesnt generate an errormsg, but the usb-device doesnt activate as it has a blue light thats supposed to indicate activity/power.. however it DOES appear in system-administrator-networking. Nomatter what I do here (set correct values for the wlan, activate/deactivate etc) the usb-card remains dead if you look at the light, and the command iwconfig results in:
```
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions
```

Appart from the obvious problem with the wlan-device not powering up at all, doing the[B] sudo modprobe ndiswrapper
[/B] actually **disables my keyboard**. Removing the usb-wlan wg111 from the usb-port brings the keyboard back, insert the usb-card and keyboard is disabled... VERY annoying.

Can anyone shed some light on this(these) problem(s)?

Thanks in advance

---

### Post by Mahones on 2006-04-30
I am having EXACTLY the same issue with the keyboard locking up, can someone PLEASE post some help on this one???

Thanks

Mahones

---

### Post by bacco_69 on 2006-05-03
I'm having the same problem: the card doesn't seem to activate (no blue light) and the console freezes!
I have Breezy Badger installed on an Acer TM250.
I currently have ndiswrapper 1.15, but the same problem was occurring with the version that comes with Breezy Badger.  

Any suggestion would be greatly appreciated

---

### Post by s2dpyro on 2007-05-07
Ok well i got everything installed right for my WG111 USB network card. the light turns on and everything but for some reason it doesn't the network manager window. the driver is installed right too because when i type ndiswrapper -l it says that the driver is installed but i still dont get the internet. i dont know what to do from here. and im new to this whole linux thing. so if you could please help me that would be great

---

### Post by jdizzle on 2007-07-05
[FONT="Comic Sans MS"][SIZE="3"]Hi. I'm also having problems getting my Netgear WG111v2 working properly under Feisty. I didn't have any problems installing it though. I installed the package [COLOR="Blue"]linux-wlan-ng (utilities for wireless prism2 cards)[/COLOR] and it showed I had wireless when I went to system/administration/network. I'm not positive it was the package, because I hadn't looked in Network Settings with it plugged in before I installed the package. I DO know that the light on the WG111v2 never blinked before I installed the package though. My problem is that I'm dealing with a VAIO laptop and I think the wired network card is dead because I couldn't even get it to work under Windows, and I don't have a phone line to try dial-up because I use VOIP. So this is my only way to connect this laptop with the outside world, and it doesn't work. I've tried DHCP and static configurations and going closer to my access point, but the indicator won't go green and I can't get online or even ping my access point. I'm pretty new to Linux, so I'm afraid I myself cannot be of much assistance, but if anyone has any idea of what I should try next, please let me know. I hope the linux-wlan-ng helps. Here is my iwconfig output:[/SIZE][/FONT]

[SIZE="2"]lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  IEEE 802.11g  Frequency:2.412 GHz  
          RTS thr:off   Fragment thr=2346 B   
          
wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0[/SIZE]

---

