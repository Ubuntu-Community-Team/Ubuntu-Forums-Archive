---
title: "New User Dell Inspiron 4100 w/Motorola WN825G"
date: 2010-12-02
forum: Hardware
---

### Post by mscuerman on 2010-12-02
I did a search and didn't find anything, but am new here, so please redirect me if I've missed something.

I have never used Linux before - total noob. :-/

I have just installed Ubuntu 10.10 on my old Dell Inspiron 4100 (PIII-1Ghz, 512MB, 30GB) which has a Motorola WN825G PCMCIA network card.  I've searched and tried to fumble my way through several online guides to using this card, but fear I may have missed something (obviously, since it still doesn't work) out of sheer noobitude and could use some guidance.

What I have done (I think!):
 - Found and installed ndiswrapper-common-1.56, ndiswrapper utils-1.9 and extracted the windows driver package for the NIC. Extracted ndis packages and did "make install"
 - Copied all the files (except the .exe files) that came with the driver to the laptop
 - Ran (via Terminal) #sudo ndiswrapper -i <path/to/driver>/bcmwl5.inf (also tried bcmwl5a.inf)
 - Edited /etc/network/interfaces as described in this post [http://ubuntuforums.org/showthread.php?t=132703](http://ubuntuforums.org/showthread.php?t=132703)

What is happening now:
 - Umm..not too much.  I can go into System>Administration>Network Tools and configure the Wireless Interface (wlan0), but now I have two items in the wireless tab - Wireless connection 1 and WRTG54G (the name I assigned to the connection at some point)
 - The wireless router is configured with WPA/PSK and works with my Windows box

Points of concern:
 - I had to assign the MAC address (which I kinda found when I was doing one of the commands in Terminal - not sure which one) for the NIC myself.  Shouldn't it have determined that automatically?
 - Is the PCMCIA slot even active?  The power and link lights are not illuminated on the NIC
 - I also entered the MAC address of the wireless router - not sure why, but it seemed to be recommended in the post referenced above, so I did it.


I may have missed a few steps or done something incorrectly, so any help that could be provided to a fresh-from-windows user would be greatly appreciated.  I am even willing to do a completely fresh install, if required, since I have not got much invested in this machine at this point, and would love to get it working so I can get used to linux and dump the MS Monkey.

TIA

Mark

---

### Post by TBABill on 2010-12-02
The bcmwl is for a Broadcom card so the best thing is to find out if the chipset is supported by either the b43 or STA drivers before trying to install the driver outside the repos. Have you already taken those steps by trying to go to System>Administration>Hardware? 
 
I have not used a PCMCIA adapter so I'm not sure it'll work but do you get anything for your wireless device using ```
lspci
``` in a terminal? If so, paste back the whole line for your network adapter.

---

### Post by mscuerman on 2010-12-02
Thanks for your reply, Bill. Here's what I got with lspci:

```
07:00.0 Network Controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN controller (rev 03)
```

I can't copy/paste since these are different machines, but I typed what it said on that line.  Just to clarify, the bcmwl5.inf is what came from the Motorola driver package on their site.  Can I assume that the chipset in there is by Broadcom?

---

### Post by TBABill on 2010-12-02
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx) 
Here's how to do it. Looks like you need the b43 driver. Have you gone to the top menu items SYSTEM>ADMINISTRATION>HARDWARE (or Additional Drivers in 10.10)? That's the preferred method.

---

### Post by mscuerman on 2010-12-02
Oh boy.  Ok, I'm going to go through that and see how I make out.  I tried the Additional drivers, but since there's no network, it doesn't seem like it does much right now.  It should be great for other drivers, though, once I get the network running, right?  Also, do I need to "undo" anything that I've done so far before I take the steps listed in the link you provided?

---

### Post by TBABill on 2010-12-02
Ok, here's an experiment from my post [http://ubuntuforums.org/showthread.php?p=10189927#post10189927](http://ubuntuforums.org/showthread.php?p=10189927#post10189927) This worked for me on the STA Broadcom driver. Perhaps you can try it on your device?
 
If you have no ethernet access you will need to get the driver from the LiveCD. I have never done so after the install, but just last night I got mine to work without ever plugging into a network. Just make sure you select the right driver. And this will ONLY work if you are reinstalling so if you do not want to do that at this time, disregard the rest of this message.
 
Boot from the LiveCD again. Once the system is fully up, go back to System>Administration>Hardware and select the b43 driver and tell it to activate it. Once it does you may just be able to click the network manager (top right) and connect. If you cannot, go to a terminal and ```
sudo modprobe b43
``` and then try to connect again. If that still does not work, just stop trying and wait till you can get to an ethernet connection or search for how to activate the LiveCD as one of your repositories and install from there. I tried last night but ran out of time so I gave up searching for making that work.
 
Anyway, if you get connected, then just double click "install Ubuntu 10.xx" from the desktop and install like you did before. Once it is done  you should have your driver still installed if the system acts like mine did. Mine was just an experiment that worked since I have never seen a post suggesting to do it, but it worked.
 
Thoughts?

---

### Post by mscuerman on 2010-12-02
I have no problem re-installing at all, but just to be clear - the LiveCD you're referring to is the CD I made from the ISO that I downloaded from the Ubuntu site, right?

---

### Post by TBABill on 2010-12-02
Yes that's the one. Good luck and post back if you get stuck along the way.

---

### Post by mscuerman on 2010-12-02
Ok, booted from the LiveCD.  Should I choose "Try Ubuntu" or "Install Ubuntu"? (Sorry - noob, remember? :) )

---

### Post by TBABill on 2010-12-02
Yes try Ubuntu. That boots you into a live session.

---

### Post by mscuerman on 2010-12-02
Ok, did the live session, clicked System>Administration>Additional Drivers and, after Searching for available drivers... a window opened that says "No proprietary drivers are in use on this system" and the list is empty.  I opened a terminal and typed ```
sudo modprobe b43
``` and it didn't do anything noticable (should I have used the -i switch?), but gave me no errors - just a new line for a command.  I tried Additional drivers again and same result.  Also tried to go into the Network icon in the upper right and Edit Connections - Wired shows "Auto eth0" but Wireless is blank.  Thoughts?

---

### Post by TBABill on 2010-12-02
Hmmm....Then I'm guessing you need the b43legacy driver maybe. Not sure. But if it isn't coming up with anything I don't have any other things we can try to get you running without having access to an ethernet port somehow.

---

### Post by mscuerman on 2010-12-02
Ok, I can take the laptop upstairs and plug it into the router to get access to the internet (just realized this - DUH!).  Once I do that, what steps should I follow at that point to try to get the wireless card to work?

---

### Post by TBABill on 2010-12-02
First try the same steps to see if the system offers you a choice of drivers. If it does not, then you may have to follow the steps provided in the link I posted above.
 

**Step 1.** 
To install b43-fwcutter issue the following command in a **terminal** (under the desktop menu **Applications > Accessories > Terminal**) and follow the prompts: 
~$ sudo apt-get install b43-fwcutter
**Step 2.** 
Under the desktop menu **System > Administration > Hardware/Additional Drivers**, the **b43** drivers can be activated for use. 
**Note:** A computer restart may be required before using the wifi card. 
**LiveCD/LiveUSB**


**Step 3.** 
For temporary use with the LiveCD and LiveUSB environments, instead of a computer restart, in a terminal issue the following commands: 
~$ sudo modprobe -r b43 ssb~$ sudo modprobe b43**Note:** Allow several seconds for the network manager to scan for available networks before attempting a connection.

---

### Post by mscuerman on 2010-12-02
Thanks!  I'll let you know how I make out.

---

### Post by mscuerman on 2010-12-02
Success!!

For all who are interested, the Broadcom chipsetted Motorola WN825G PCMCIA wireless network card DOES work under Ubuntu 10.10.

Here's what I had to do:

 - Boot my laptop with the LiveCD and choose "Try Ubuntu"
 - Connect a WIRED ethernet cable to my internet-connected wireless  router - I tried and tried to figure out how to do it another way and  couldn't.  I suspect it must be possible, but I couldn't get there, even  with the help of several experts including TBABill.
 - Click System>Administration>Synaptic Package Manager
 - Choose Reload (to make sure it gets a fresh list from all the repositories)
 - Type 'bcm' in the quick search box
 - Check ALL THREE of the options that appear there - 'firmware-b43-installer', 'b43-fwcutter' and 'bcmwl-modaliases'.
 - Click Mark All Upgrades and allow the software to be downloaded via the ethernet cable
 - When it's finished, close Synaptic
 - Click System>Administration>Additional Drivers (This was still  empty for me at first.  I think I had to restart or something before I  finally saw the b43 drivers)
 - Click on the b43 driver package and chose Activate WHILE STILL CONNECTED TO ETHERNET.
 - Once it activates, close the Additional Drivers and choose "Install  Ubuntu" - I had to do a fresh install which was no big deal since I had  nothing configured/installed at this point.  I'd only installed it the  previous day.
 - Make sure you're still connected to the internet via wired connection  and chose to allow Ubuntu to download updates during installation.
 - After the installation is complete, go back to Additional Drivers and  make sure you can activate your card (may require yet another reboot -  can't remember for sure), then go into your network settings and set up  your SSID and your security (you ARE using WEP or WPA/PSK, right?) and  wait for it to connect.

Thank you, TBABill, for your guidance and pointing me in the right  direction.  You gave me the things I needed to do and I was able to get  it working thanks to your input.

Can someone mark this as [ SOLVED ] now?  I'm not sure how.

---

### Post by TBABill on 2010-12-02
No problem and glad you got it worked out!

---

