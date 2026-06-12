---
title: "ubuntu 10.10 &amp; atheros 5001 wireless"
date: 2010-11-16
forum: Hardware
---

### Post by cpickeri on 2010-11-16
Hi,

I did a fresh install of ubuntu 10.10 on my compaq cq50 106 laptop. Upon installing everything worked great right out of the gates. 

Now a few weeks later, for some unknown reason, my wireless device no longer works. All I get is the 'device not ready' message in the network manager.

When I look at the information from the lshw it tells me the wirelees device is disabled. 

Cannot figure out what has changed here.

Thanks.

---

### Post by Yellow Pasque on 2010-11-16
Maybe a kernel update hosed things. Post any relevant output from dmesg as well as:
```
sudo iwconfig
sudo lshw -C network
```

---

### Post by cpickeri on 2010-11-17
You'll never believe what the fix was to this one.
-I booted up vista as this is a dual partition.
-In Vista my wireless device was also not working.
-I enabled it and used the wireless as per norm.
-rebooted in ubuntu and everything is working fine.

Disabling it in vista somehow also disabled it in Ubuntu...maybe a firmware switch or something??

thanks for the help.

cheers

---

### Post by manco1911 on 2010-11-17
ah, haha, i remember that. 
Yes, i had the same issue.. i say had, cause i learned to avoid it, lol. It seems like if windows could switch it right from "bios". 
Quick solution, enable your wifi card on BIOS instead of booting windows, reboot on to ubuntu.. the problem persists, its only faster to fix, lol.

---

### Post by scottmcarthur on 2010-11-17
That is crazy!  I have been dealing with the same problem with a Compaq cq50 for the past week or so.  It was strange, when I first installed Ubuntu, the wireless worked fine the suddenly stopped.

There was another thread that I read that said that if you are plugged into a wired network, then the wireless is automatically disabled, but his did not work for me.  I thought that maybe the card had broken, so I reinstalled Vista and it worked just fine, but after installing Ubuntu again, I got nada.

If you were able to enable it in windows and then it worked in Ubuntu, how long will that last?  Will you constantly be booting to windows to turn it on and then reboot to Ubuntu?

Does your wireless button above the keyboard work?

Any one have any ideas on a permanent solution?

---

### Post by scottmcarthur on 2010-11-17
[]("http://ubuntuforums.org/member.php?u=593433")manco1911, how are you enabling this in the BIOS of a cq50?  I have looked for something there and it is actually very limited and does not seem to have anything that will do that.  Maybe I am overlooking something?

---

### Post by manco1911 on 2010-11-17
@cpickeri
I dont have a cq50. Sorry i didn's specify it. 
Im running an Asus G50vt. I did had an option to enable/disable wifi on BIOS.

I asume you dont have a phisical switch for the wireless card, right?

On my case, it only happened if ON windows, i switched off my wifi card (generaly for battery saving purpose) and i forgoted to enable it again. 
And when i booted after that into Ubuntu, it wouldn't recognize it. Is this your case or is it every single time ?

---

### Post by scottmcarthur on 2010-11-17
I do not currently have windows installed.  There is a button to enable/disable the wifi, but it does not seem to work in Ubuntu at all.
The card is recognized, drivers are good, but the device is just disabled.  I can not seem to find a way to enable it!
The guide here:
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Drivers](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Drivers)

pretty much indicates that this is usually caused by a hardware switch.

**But **running [FONT=Courier New]rfkill  list[/FONT] indicates that the wifi is software blocked, not hardware blocked, like a switch.  GRR!

<digging> <digging> <digging>
gotta find the answer!

---

### Post by scottmcarthur on 2010-11-17
**[SIZE=7]YES![/SIZE]**

Open a command window and issue the command 

[FONT=Courier New][SIZE=5]sudo rfkill unblock wlan[/SIZE][/FONT]

Did that and **BAM, **everything lit up and works!!

Sure would be nice to have that included in the network GUI drop down.

---

### Post by scottmcarthur on 2010-11-18
Just a note though, hitting the wifi button disabled it, but it had problems re-establishing the connection to the router.  kind of FAIL, kind of annoying, but still a huge step forward.

---

### Post by Pabx on 2010-11-21
> **scottmcarthur said:**
> **[size=7]yes![/size]**

open a command window and issue the command 

[font=courier new][size=5]sudo rfkill unblock wlan[/size][/font]

did that and **bam, **everything lit up and works!!

Sure would be nice to have that included in the network gui drop down.

ooooo myyy gooood!!!!!!

Thank you!!!!!!!!!!!!!!! 

I tried everything! And it was that easy!!!!!!!!!

---

### Post by berkboss on 2010-12-02
Hmm... This is not working for my computer. I am using an Acer Aspire 4720z. Anymore Ideas anyone?

---

### Post by AndyP79 on 2011-01-24
> **scottmcarthur said:**
> **[SIZE=7]YES![/SIZE]**

Open a command window and issue the command 

[FONT=Courier New][SIZE=5]sudo rfkill unblock wlan[/SIZE][/FONT]

Did that and **BAM, **everything lit up and works!!

Sure would be nice to have that included in the network GUI drop down.

THANK YOU!!!!!!! Holy crap, I had a post on this last night in which I got a little frustrated and ranted and raved all pissed of, and tried 3 different OS, now, I got my wifi back. 
THANK YOU!!!!

---

