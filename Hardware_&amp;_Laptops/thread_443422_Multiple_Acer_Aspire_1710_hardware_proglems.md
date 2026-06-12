---
title: "Multiple Acer Aspire 1710 hardware proglems"
date: 2007-05-14
forum: Hardware &amp; Laptops
---

### Post by ziret on 2007-05-14
I hope it's all right to ask more than one question in a post. I have an Acer Aspire 1710. This is my first use of a Linux platform. Here are my problems:

Wireless doesn't connect or show network. It seems to know there's a wireless card, but is unable to use it. I did the live CD of the last Ubuntu distro and it found and used the wireless card just fine. Is this going to be fixed, or can someone tell me how to fix it?

When suspending or hibernating, when I try to return to using the computer the screen stays completely black with a cursor line in the upper right hand corner. I have to turn the machine off and on again to use it.

My mouse and my touchpad fight each other. There is no touchpad shown in my system menu, but it kind of works. However, I want to have the mouse be left handed and the touch pad right handed. Whatever I set the mouse, the touchpad does too.

Microsoft Intellimouse is recognized as my mouse, but there is no way to change the wheel behavior nor is there any way to use the side buttons.

That's all for now. I haven't tried to use the other hardware buttons, so may have to write again. I really hope someone can help me.

Teri

---

### Post by Kobalt on 2007-05-14
All right then, one thing at a time :) 
Your wireless : do you know what kind of wifi card do you have ? If you don't know, please post the output of the following command line : *lspci*

---

### Post by ziret on 2007-05-14
Thank you! here it is

teri@Marcel:~$ lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV36 [GeForce FX Go5700] (rev a1)
03:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5788 Gigabit Ethernet (rev 03)
03:01.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
03:02.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
03:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
teri@Marcel:~$

---

### Post by Kobalt on 2007-05-15
Your wifi card is a Broadcom 4306 : > 03:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
Here is a way to get it working : [http://ubuntuforums.org/showthread.php?t=201902](http://ubuntuforums.org/showthread.php?t=201902)

Your suspend/hibernate problem can be caused by the absence of drivers for your graphic card. I see from lspci that it is a GeForce Go5700. See this in order to install your drivers : [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia?highlight=%28nvidia%29#head-7f830fe17ae6da7c546decbb10c32ff61471258e](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia?highlight=%28nvidia%29#head-7f830fe17ae6da7c546decbb10c32ff61471258e)

---

### Post by ziret on 2007-05-15
I will try those things and get back to you. Thanks!

---

### Post by ziret on 2007-05-15
I am working on this page [http://ubuntuforums.org/showthread.php?t=201902](http://ubuntuforums.org/showthread.php?t=201902)

When I get to step 2 here is what happens
teri@Marcel:~$ sudo rmmod bcm43xx
ERROR: Module bcm43xx does not exist in /proc/modules
teri@Marcel:~$ 

Apparently I don't know what to do with the wireless drivers once they are downloaded. Please help. 

Thank you.

---

### Post by Kobalt on 2007-05-15
It is fine if you have that output to* sudo rmmod bcm43xx* : the point of this command line is to remove the bcm43xx modules. If it tells you it's not there, then it's just fine and you can move on to the next step...

---

### Post by ziret on 2007-05-15
When I try to use the synaptic package manager this is what I get:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I don't know what this means.

Also, have you looked at the instructions for fixing the graphic driver? I'm a beginner and I haven't a ding dong clue what that is all about. Is there somewhere that this is laid out step by step in a troubleshooting manner? I am not even clear what the problem is, much less how to fix it.

I don't mean to sound rude, at all, I just don't understand.

Teri

---

### Post by ziret on 2007-05-15
Ubuntu tried to update my packages. This is a new message, plus the -a one above.

W: GPG error: [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A361B38AB6A4EB33

---

### Post by Kobalt on 2007-05-15
> **ziret said:**
> When I try to use the synaptic package manager this is what I get:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I don't know what this means.

Also, have you looked at the instructions for fixing the graphic driver? I'm a beginner and I haven't a ding dong clue what that is all about. Is there somewhere that this is laid out step by step in a troubleshooting manner? I am not even clear what the problem is, much less how to fix it.

I don't mean to sound rude, at all, I just don't understand.

Teri
First, run in a terminal ```
sudo dpkg --configure -a
```
Then in order to install the drivers, all you need to do (as stated in the instructions) is to go to System > Admin. > Restricted drivers manager and chose to install the drivers for you graphic card (that means ticking the box and validating).

---

### Post by ziret on 2007-05-15
OK, I got it to try to install the ndiswrapper. But then the VMWare-player eula comes up in a terminal screen and I cannot figure out how to agree to it, because when I click it nothing happens. Then I am back to square one.

Hope this helps.

---

### Post by Kobalt on 2007-05-15
> **ziret said:**
> Ubuntu tried to update my packages. This is a new message, plus the -a one above.

W: GPG error: [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A361B38AB6A4EB33
According to this (and to your previous thread) I assume you have tried to add the repositories for UbuntuStudio (are you another one looking for its theme?).
You seem not to have added the repositories GPG key properly. Run this command line in order to add it ```
wget -q http://archive.ubuntustudio.org/ubuntustudio.gpg -O- | sudo apt-key add - && sudo apt-get update
```

---

### Post by Kobalt on 2007-05-15
> **ziret said:**
> OK, I got it to try to install the ndiswrapper. But then the VMWare-player eula comes up in a terminal screen and I cannot figure out how to agree to it, because when I click it nothing happens. Then I am back to square one.

Hope this helps.
The VMWare-player eula ?? This has nothing to do with ndiswrapper... Did you try to install it for another purpose ?
You should be able to move down to the accept/decline part with the up/down arrows of your keyboard or Enter anyway...

---

### Post by ziret on 2007-05-15
I did that and then I got the screen I told you about where I am supposed to say OK but can't. Then everything says to run that program again, and I get the screen again.

---

### Post by Kobalt on 2007-05-15
Yes but how did you get to the point of installing VMWare-player ? What command line did you type just before, what step of the guide I directed you to got you to this point ?

---

### Post by ziret on 2007-05-15
OK, here is what happens now:

teri@Marcel:~$ sudo ndiswrapper -i -/home/teri/Desktop/wireless/bcmwl5.inf
driver bcmwl5 is already installed
teri@Marcel:~$ ndiswrapper -l
bcmw.15 : invalid driver!
bcmwl5 : invalid driver!
teri@Marcel:~$ sudo ndiswrapper -i /home/teri/Desktop/bcmwl5.inf
driver bcmwl5 is already installed
teri@Marcel:~$ ndiswrapper -l
bcmw.15 : invalid driver!
bcmwl5 : invalid driver!
teri@Marcel:~$

---

### Post by ziret on 2007-05-15
You said: Yes but how did you get to the point of installing VMWare-player ? What command line did you type just before, what step of the guide I directed you to got you to this point ?
__________________

I don't know how, but that bit is working now. I restarted a couple of times and it works. Now I just can't get it to do the driver thing.

---

### Post by ziret on 2007-05-15
You said: According to this (and to your previous thread) I assume you have tried to add the repositories for UbuntuStudio (are you another one looking for its theme?).
You seem not to have added the repositories GPG key properly. Run this command line in order to add it

Yes, I liked the theme. I did what you said and I'm sure the theme is here somewhere now. Thank you.

---

### Post by Kobalt on 2007-05-15
Ok then, for the drivers : once you download and extract them from the guide I directed you to, you get a folder that has a few files inside, some .sys and others .inf. Even though the command line *sudo ndiswrapper -i -/home/teri/Desktop/wireless/bcmwl5.inf* refers only to the bcmwl5.inf file it still needs the bcmwl5.sys file as well. So make sure to have it in your /wireless folder.

---

### Post by Kobalt on 2007-05-15
> **ziret said:**
> You said: According to this (and to your previous thread) I assume you have tried to add the repositories for UbuntuStudio (are you another one looking for its theme?).
You seem not to have added the repositories GPG key properly. Run this command line in order to add it

Yes, I liked the theme. I did what you said and I'm sure the theme is here somewhere now. Thank you.
You must run this command in order to install the theme : 
```
sudo apt-get install ubuntustudio-look
```

---

### Post by ziret on 2007-05-15
OK that's working. Now what?

---

### Post by Kobalt on 2007-05-15
Now you can follow up the guide from stage 7 ... ```
ndiswrapper -l
```
etc.

---

### Post by ziret on 2007-05-15
Thanks. Here is what happens:

teri@Marcel:~$ ndiswrapper -l
bcmw.15 : invalid driver!
bcmwl5 : invalid driver!
teri@Marcel:~$

---

### Post by Kobalt on 2007-05-15
All right then : these don't seem to be fitting drivers for your card. So first, let's remove those not working before adding a new one : ```
sudo ndiswrapper -e bcmwl5
sudo ndiswrapper -e bcmw.15
```
Now, do you have the windows drivers for your wifi card provided by your manufacturer (on a CD or on your windows partition) ?

---

### Post by ziret on 2007-05-15
done

---

### Post by Kobalt on 2007-05-15
> **ziret said:**
> done
Meaning :confused:

---

### Post by ziret on 2007-05-15
sorry, meaning, OK, I did that, what next?

---

### Post by Kobalt on 2007-05-15
Ok then do you have your windows drivers then ? If so, you must get those bcmwl5.inf & bcmwl5.sys files of yours and install them with ndiswrapper just like we did before with ```
sudo ndiswrapper -i /*path-to-your-windows-drivers*
```

---

### Post by ziret on 2007-05-15
No, I don't have them, but I can get them from Acer and then I'll do that.

Meanwhile, I have to go to work, so I'll work on this later.

Thanks for your help.

---

### Post by Kobalt on 2007-05-15
I have to go to sleep as well anyway. :)
You're welcome.

---

### Post by ziret on 2007-05-15
Good morning,

Here is what happens now:

teri@Marcel:~$ ndiswrapper -l
bcmwl5 : invalid driver!
net5211 : invalid driver!
teri@Marcel:~$ 

In the drivers that I downloaded from Acer, there are two folders, with two different drivers, one is a the bcmwl5.inf and the other is a net5211.inf. Is it possible I should be using the other driver? 

Teri

---

### Post by ziret on 2007-05-15
I am getting the same error as before. 

teri@Marcel:~$ sudo ndiswrapper -m
Password:
module configuration already contains alias directive

teri@Marcel:~$ sudo modprobe ndiswrapper
teri@Marcel:~$ 

When I go to networking, there's no wireless connection.

---

### Post by Kobalt on 2007-05-16
Now that is weird... 
I had a broadcom 4311 and whenever I tried to get it working using ndiswrapper from the repos I failed. Maybe you should try the latest version then. I suggest you follow [these steps]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show#head-f744e28e6c78eb83d22be77819b130016a8e51f3"), and if it's not working we'll head towards something else.

---

### Post by ziret on 2007-05-16
what do you mean, the latest version? I just downloaded it yesterday...

---

### Post by ziret on 2007-05-16
Here are the instructions from the previous instructions you sent--so doesn't this mean I installed the latest version yesterday? Dlo you still want me to proceed with the other directions? Shall I go directly to step 2?

---

### Post by Kobalt on 2007-05-16
You installed ndiswrapper from the repositories, not from the sources. Installing the latest version available means compiling it from the sources. It's all explained in the last link I gave you.

---

### Post by ziret on 2007-05-16
OK,. Is there any chance there is just going to be an upgrade for this? I just started using Ubuntu last week and it's taken over all my free time. When I look at this next raft of instructions it makes me want to cry, literally. I don't know if I can do it all.

---

### Post by Kobalt on 2007-05-16
Actually there is no upgrade possible, since it's different installation methods : compiling/packaging... 
Even though the instructions seem long, it's not that hard. Plus it's a good training I think. Though I understand your despair, since all of this is new and seems complicated and such, I can tell you that in the future you'll do all of this in less than 5 minutes. The problem here really seems to find the right path, but that path isn't that long my friend :)

---

### Post by ziret on 2007-05-16
I hope you are right, but it has been mighty long so far. I will try right now.

---

### Post by Kobalt on 2007-05-16
Great ;)

---

### Post by ziret on 2007-05-16
Before step one it says to test. Here is my output, which isn't what it shows in the tutorial

teri@Marcel:~$ user@ubuntu:~$ lspci
bash: user@ubuntu:~$: command not found
teri@Marcel:~$ 
teri@Marcel:~$ 
teri@Marcel:~$ 

should I go ahead with step one?

---

### Post by Kobalt on 2007-05-16
You don't need to enter the *user@ubuntu:~$* part, this is stated only so you know you're in a Terminal. You only need to enter the command line like this ```
lspci
```

---

### Post by ziret on 2007-05-16
Oh. Here is what I get doing it correctly

teri@Marcel:~$ lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV36 [GeForce FX Go5700] (rev a1)
03:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5788 Gigabit Ethernet (rev 03)
03:01.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
03:02.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
03:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
teri@Marcel:~$

---

### Post by Kobalt on 2007-05-16
Yes it's ok, you can go on to the next step : removing ndiswrapper, etc...

---

### Post by ziret on 2007-05-16
the instructions say:
Check the contents of the /etc/iftab file and make sure that no other device has the wlan0 driver name reserved for it:

user@ubuntu:~$ cat /etc/iftab

If there are any lines assigning the name wlan0 to a MAC identifier then either remove that line or comment it out with the "#" character. 

I get:
teri@Marcel:~$ cat /etc/iftab
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:c0:9f:41:af:d6 arp 1
eth1 mac 00:0b:6b:4a:b2:07 arp 1
teri@Marcel:~$ 

What does this mean? "If there are any lines assigning the name wlan0 to a MAC identifier then either remove that line or comment it out with the "#" character." 
How do I do this?

---

### Post by Kobalt on 2007-05-16
There is no wlan in your file, so you can move on to the next step.

---

### Post by ziret on 2007-05-16
Never mind, I figured that out. Here is the problem now. The directions refer to the HP driver, but mine is not th at and has different file names etc. How do I proceed from 
user@ubuntu:~$ mv sp33008.exe bcm4311

when I get 
teri@Marcel:~$ mv sp33008.exe bcm4311
mv: cannot stat `sp33008.exe': No such file or directoy

---

### Post by Kobalt on 2007-05-16
The drivers are actually given by HP, it's true, but it's common to many Broadcom cards... Since yours seemed not to be accepted, let's try with these.
Did you download the sp33008.exe file to your Home directory ? Make sure it's there. Then, create the bcm4311 folder with : ```
sudo mkdir bcm4311
```
Finally, move the sp33008.exe file there and extract it : ```
mv sp33008.exe /bcm4311
cd /bcm4311
cabextract sp33008.exe
```
Then go on with the instructions...

---

### Post by ziret on 2007-05-16
Oh, yesterday you said to use the files provided by Acer, because the others didn't work, so that's what I'm doing. YOu want me to use the HP ones now?

---

### Post by Kobalt on 2007-05-16
You can try with both, just to make sure...

---

### Post by ziret on 2007-05-16
Here's what I get with the HP driver

All done, no errors.
teri@Marcel:~/bcm4311$ sudo ndiswrapper -i bcmwl5.inf
driver bcmwl5 is already installed
teri@Marcel:~/bcm4311$ sudo ndiswrapper -i bcmwl5.inf
driver bcmwl5 is already installed
teri@Marcel:~/bcm4311$ 
teri@Marcel:~/bcm4311$ ndiswrapper -l
bcmwl5 : invalid driver!
teri@Marcel:~/bcm4311$

---

### Post by Kobalt on 2007-05-16
All right then you can remove it this way ```
sudo ndiswrapper -e bcmwl5.inf
```
and possibly try with the Acer drivers you got.

---

### Post by ziret on 2007-05-16
I get

teri@Marcel:~$ sudo ndiswrapper -e bcmwl5.inf
couldn't delete /etc/ndiswrapper/bcmwl5.inf: No such file or directory

---

### Post by Kobalt on 2007-05-16
oOops ! Sorry, my mistake : ```
sudo ndiswrapper -e bcmwl5
```
Here you go...

---

### Post by ziret on 2007-05-16
OK, I did that, now what?

---

### Post by Kobalt on 2007-05-16
Now you can try to install your Acer drivers. This way : ```
sudo ndiswrapper -i /path-to-your-drivers
```

---

### Post by ziret on 2007-05-16
where exactly are my drivers at this point?

---

### Post by ziret on 2007-05-16
teri@Marcel:~$ sudo ndiswrapper -i /teri/80211G/Driver
driver driver is already installed
teri@Marcel:~$

---

### Post by ziret on 2007-05-16
teri@Marcel:~$ cd bcm4311
teri@Marcel:~/bcm4311$ ndiswrapper -l
80211g : invalid driver!
bcm4311 : invalid driver!
bmc4311 : invalid driver!
driver : invalid driver!
teri@Marcel:~/bcm4311$ 

this seems to be recursive (I am going around in circles)

---

### Post by Kobalt on 2007-05-16
Clearly...
Let's try something completely different then : [http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

---

### Post by ziret on 2007-05-16
Here's what happens (nothing)

teri@Marcel:~$ cd bcm43xxfirmware
teri@Marcel:~/bcm43xxfirmware$ ./installbcm43xx.sh
Password:
teri@Marcel:~/bcm43xxfirmware$ 

when I  go to networking, there is still no wireless card

---

### Post by Kobalt on 2007-05-16
You can directly navigate to the bcm43xxfirmware directory and double-click on the ./installbcm43xx.sh file, then select *launch in a terminal*.

---

### Post by ziret on 2007-05-16
OK, I did that, and still no results.

---

### Post by Kobalt on 2007-05-16
Ok then, let's try this. Open the /etc/modules file and remove the last line that should be bcm43xx : ```
gksu gedit /etc/modules
```
Save and exit, and restart. Now you can try to double click on the script again.

---

### Post by Kobalt on 2007-05-16
And if this still doesn't work, since it's supposed to be an automated way of doing it, you can try the manual way : [http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174)

---

### Post by ziret on 2007-05-16
here is the contents of the modules file

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
sbp2

---

### Post by ziret on 2007-05-16
these instructions [http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174) are for dapper and edgy. I have feisty. Will they work?

---

### Post by Kobalt on 2007-05-16
Yes they are still valid for feisty.

---

### Post by ziret on 2007-05-16
Yeah, that didn't work, either. Windows is looking better by the minute.

---

### Post by Kobalt on 2007-05-17
I regret to tell you that but you must be doing something wrong... Out of the three methods I pointed you towards at least one should have worked. And these are not experimental procedures, they have proven to be working many times...

---

