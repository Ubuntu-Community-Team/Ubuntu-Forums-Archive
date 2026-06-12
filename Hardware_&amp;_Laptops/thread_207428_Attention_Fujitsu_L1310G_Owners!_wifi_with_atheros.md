---
title: "Attention Fujitsu L1310G Owners! wifi with atheros fully working"
date: 2006-07-01
forum: Hardware &amp; Laptops
---

### Post by Eversmann on 2006-07-01
Finally i made it to work.

The problem in this laptop (like some others) is making the wifi to enable, because it's software-based.

After a few days, lots of tests, even trying to debug and disassemble the pm.exe file, finally it's working, thanks to the work of some other people who also spend lots of hours. This is the spirit of linux :-D

Going to do a step-by-step for the people who needs it:

I'm running 2.6.15-23 right now. This kernel works better than 2.6.15-25 atm.

First, you need to install linux headers if you actually don't have it for your kernel

```
sudo apt-get install linux-headers-$(uname -r)
```

First, you need madwifi-ng, not the one that ships with restricted modules, because those are based on madwifi-old. I had better experiences with linux restricted modules uninstalled, and running fglrx and madwifi compiled from the original drivers. But you can always keep it if you want to. For madwifi, you don't need to blacklist them, or adding the line to /etc/default/linux-restricted-modules-common, because installing madwifi removes the files it finds during the installation.

Go to [www.madwifi.org](www.madwifi.org) and grab the latests tarball. To install it, just follow this instructions: [http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo)

Once you have it installed go to this site: [http://www.marvec.org/amilo/](http://www.marvec.org/amilo/) and download the file it offers, and follow the instructions. It's very easy to install, just:

```
tar xvjf fsaa1655g.tar.bz2
cd fsaa1655g
make
sudo make install
```

You need to use the rfkill=0 option on modprobing ath_pci from then madwifi drivers, even the wifi light on the laptop is on, so let's edit the options file of modprobe

Go to /etc/modprobe.d/options and add these two lines at bottom of the file:

```
options ath_pci rfkill=0

options fsaa1655g radio=1
```


Then add fsaa1655g to the modules list at /etc/modules

If the light doesn't turn on, try this command: echo 1 > /proc/fsa1655g/radio and see what happens.

Reboot the machine.

After that, you should be able to run iwlist ath0 scan (be sure to have the card enabled with ifconfig ath0 up), and then make a iwconfig ath0 essid any or whatever you do to connect ;-)

I had no luck with NetworkManager and madwifi-ng, so if anyone knows how to run it......

I'm posting information about this laptop running ubuntu on the wiki, information that i'll try to keep updated:

[https://wiki.ubuntu.com/LaptopTestingTeam/FujitsuAmiloL1310G](https://wiki.ubuntu.com/LaptopTestingTeam/FujitsuAmiloL1310G)

I'll post all my tests and the work i've done on this laptop and ubuntu on another post, about fglrx, XGL, compiz, kernerls, ethernel.......

Hope it helps, any question, just post away ;-)

---

### Post by ldegryse on 2006-12-07
Thank you very much for this tip.

I have been searching for hours, asked Siemens without any results.

This one worked perfect.

I had to add some more packages before proceeding : 
make 
gcc

and then, it worked smooth.

It helped very much.

Thanks again

Luc

---

### Post by kolvas on 2007-01-03
hey eversmann!

happy new year

great job on the wifi working for the laptop. i have a couple of questions though of which you might be able to help me:

1. everything works great, when i trun the laptop on, the wifi LED turns on as well. my question is how do i turn it off? is there anyway i can make it NOT work on boot, but rather enable it when i need it?

2. i succeeded in making it work, however, only with encryption turned off (from my router). when i turned on encryption (WPA) i couldnt establish a connection. what parameters must i pass in order for it to work?

thanks,
vasilis

---

### Post by kolvas on 2007-01-11
either everyone's on vacation or this is a dead thread....

---

### Post by rfdparker2002 on 2007-02-14
> **kolvas said:**
> either everyone's on vacation or this is a dead thread....
No, I'm reading it, and it will be useful, but my L1310G, which I brought in 6/06 from from dabs.com and had used a PCIMA wireless card with, is currently sent off for repair: the cooling fan when weird (in [k]ubuntu and windoze) so this will be great when I get back I aiming to installing Kubuntu 6.10 and:
[LIST]
[*]Get fglrx and beryl working, without mouse freezes (found thread to fix that)
[*]Follow this for wireless without a card. and use it with KNetworkManager, which worked with my PCIMA card on dapper
[*]and other stuff when I remember (i'll edit this post)
[/LIST]

Also does this method make the wireless push on/off push button work, or do you have to use echo commands, which would give windoze newbs something to moan about.

Anyway, thanks for doing this Eversmann, I had being trying for ages with ndis-wrapper (which detected and supposedly activated the card, but it could never find APs or connect) and everything.

---

### Post by Eversmann on 2007-03-23
Sorry for not replying to this thread, being busy, and, have to say, kind of frustrated with edgy on this laptop, that's why i didn't update the wiki page.

The fans now works ok if i activate the polling_frequency at acpi kernel control

(this way: echo "5" > /proc/acpi/thermal_zone/THRM/polling_frequency )

But SD card reader doesn't work (and it used to do with 6.06), and finally, with latest beryl version 0.2.0, works the eyecandy too, but the fglrx drivers are really, really, really horrible. I've being trying to sell the laptop to buy a new one with an nvidia card......... you can figure it out ;-)

Now feistoy is so close, i'm excited to see how the new ubuntu child plays on the machine. When it's available, i'll do an installation from scratch.... too many trial and errors on it, if you know what i mean.....

---

### Post by yuppipl on 2007-04-08
solution of problem with ubuntu 7.04
[http://www.linuxquestions.org/questions/showthread.php?t=506363]("http://www.linuxquestions.org/questions/showthread.php?t=506363")

---

### Post by Eversmann on 2007-04-10
Mmm, that's a problem with building modules that requires config.h on the kernel, i don't see where's the solution resolved in ubuntu 7.04 and this laptop.

---

### Post by longleaves on 2007-05-16
Is there any News on getting the Wifi (Button) to work with the Laptop?
I can't install the fsaa1655g tool anymore..

It's due to the missing config.h but I can't figure out what to do from the suggested thread.

// Sorry should have figured that out first.

open the fsaa1655g.c file (pico fsaa*)
comment out the line #include config.h ( //#include config.h)
then proceed as above

---

### Post by jimmigoo on 2007-09-04
Hello everybody!!

This is my first post, and it's a positive one :)

In fact, just two minutes ago, I've finished the complete abilitation of WiFi card, 
and I'm on the Net with a Alice W-Gate modem-router by Telecom Italia. 

I've a Fujitsu-Siemens AMILO L1310G laptop, 
Kubuntu Edgy
Wicd for Wifi Connection, 
WEP Security Key (even with WPA-PSK security Key)
Static IP, Netmask and Gateway, 

I've installed the madwifi package, then I've donwloaded and installed the 
fsaa1655g module.

So, when I'd like to connect to the Net:
1) shell -> sudo modprobe fsaa1655g, and WifiCard LED turns ON; 
2) Wicd -> to connect to my Router
3) shell -> sudo pppoeconf, to have a ppp even for ath0 (wireless card)
4) Mozilla Firefox, wait for a moment, then SURF ON THE NET!!!!

Thanks everybody for help and support!!

I'd like to know if there's a kind of application to connect automatically to the net, 
without executing pppoeconf everytime...

I'm looking forward for seeing your reply...

Thanks...

jimmigoo
:lolflag:

---

### Post by MasthaX on 2007-09-25
Good day,

i have done this tutorial for several times now. and i keep getting error messages. This is what i did:

```

ifconfig ath0 down

```
gives:
PERMISSION denied

So i tried with sudo

```

sudo ifconfig ath0 down
sudo ifconfig wif0 down

```

that worked you would think, well it doenst give a message so i tried the madwifi bash file and its giving me this message:

FATAL:  module_wlan_scan_sta is in use
FATAL: module wlan is in use

I dont know how to solve this or force the networks to close or whatever can anyone help me?

---

### Post by onefilip on 2007-10-17
hi.
I have this computer laptop and i have installed madfiwi package and after I have done all that there is in the first post.
I have rebooted my laptop and now wireless it's ok...I can surfing on the net.
But I have a problem to switch off the hardware... the led of wireless is always on!
can you help me????

---

### Post by onefilip on 2007-10-17
sorry I found the solution about my problema...

Shell (terminal): sudo gedit /etc/modprobe.d/options

modify the value of "Radio=0"...reboot and Led wireless now is off...
to enable wifi modify radio=1...and reboot...
this solution is bad...but is the only for now!
otherS?

---

### Post by MasthaX on 2007-10-19
Some information about my problem:

I have succesfully installed madwifi and fsaal.. etc. i solved my problem by removing the modules who where in use. I removed the modules with rmmod and then i installed madwifi the problem with the network manager was solved when i installed [wicd](http://wicd.sourceforge.net) i chose madwifi as a WPA verification driver and it worked perfectly(as iam browsing with it right now).

---

### Post by Muflon on 2008-01-10
If you want a script to enable or disable the wireless light, here is one that I use.

```
#!/bin/bash
# Get the current status of the Wlan switch               
export fsaa1655gFile=/proc/fsaa1655g/radio
export WlanStatus=`cat $fsaa1655gFile`                     
echo "Current status = $WlanStatus"

if [[ "$WlanStatus" =~ "fsaa1655g: 0" ]] ; then
	echo "Wlan switched off, so turn it on"
	echo 1 | sudo tee $fsaa1655gFile
else
	echo "Wlan switched on, so turn it off"
	echo 0 | sudo tee $fsaa1655gFile
fi
```

---

