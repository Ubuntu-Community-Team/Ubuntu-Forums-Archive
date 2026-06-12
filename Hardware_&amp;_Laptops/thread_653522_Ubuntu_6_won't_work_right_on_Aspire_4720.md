---
title: "Ubuntu 6 won't work right on Aspire 4720"
date: 2007-12-30
forum: Hardware &amp; Laptops
---

### Post by rba1988 on 2007-12-30
Hello. I've installed Ubuntu 6 on my Acer Aspire 4720. It installed ok but I had the following problems:

-There's no sound
-It only detects the loopback interface

Basically that's it. It's just an Ubuntu laptop with no internet connection...useless. lol. I do use it for programming though (needed for school). But no internet and no sound makes it...well...useless in a way.

I tried to fix the wireless internet internet connection and got it working...sorta...Here's how I did it:
-I pushed the wifi button on the laptop and it detected the wireless card but put it to eth0. 
-I searched the internet for the ipw3945 firmware and got it loaded via alien -ing the rpm package and loading the ipw3945d in /sbin

Problems:
-it could detect the various access points but it doesn't seem to connect...

More problems:
-What do I have to do to get the sound working? I've searched the forums but it seems I can't find the right answer. I may need the snd-hda-intel driver or something...but I can't find it. Any help?
-What do I have to do to get some internet connectivity? :( It didn't detect my modem, lan card and wifi card (at first)..

First time use Ubuntu....help please.:D

---

### Post by Bartender on 2007-12-30
I'm hoping you've got broadband or can borrow some.  Try downloading/burning a copy of 7.10.  Lots of little fixes between 6 (.04 or .10?) and 7.10, especially wireless, sound, etc.

---

### Post by rba1988 on 2007-12-30
> **Bartender said:**
> I'm hoping you've got broadband or can borrow some.  Try downloading/burning a copy of 7.10.  Lots of little fixes between 6 (.04 or .10?) and 7.10, especially wireless, sound, etc.

Yeah...I guess I'll go for that. I just got this dvd from a friend. I heard all the great things about Ubuntu and decided to try it out. Came form Mac OS X. It's a good machine, but I'm afraid to tinker it. Linux is more of an adventure.

I just hope Ubuntu 7 will work right out of the box with my Aspire 4720 so I can finally start programming right.:D while listening to good music.:P

---

### Post by be4truth on 2007-12-30
I just installed Gutsy on my Aspire 4720. Have a look here:

[https://wiki.ubuntu.com/LaptopTestingTeam/AcerAspire4720]("https://wiki.ubuntu.com/LaptopTestingTeam/AcerAspire4720")

---

### Post by tdj2828 on 2008-01-10
Just got Aspire 4720z.  Installed Ubuntu 7.10...same issues---got the sound working 
after applying these:

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)
(specifically linux-backports-modules-generic was required)

Wifi was much harder.  The acer aspire 4720z comes with the 
wireless ethernet controller: Atheros Communications, Inc. AR5006EG 802.11
built in.  Turns out (after much searching) that Madwifi *is* the solution,
BUT it needs a patch for this specific card:

Got patch

[http://madwifi.org/ticket/1679](http://madwifi.org/ticket/1679)

from

[http://madwifi.org/wiki/Compatibility/Atheros](http://madwifi.org/wiki/Compatibility/Atheros) 

The 1679 ticket is not well put...basically here is what one must do (though do 
read the above pages first!):

<pre>
wget snapshots.madwifi.org/madwifi-ng/madwifi-ng-r2756-20071018.tar.gz
</pre>

Untar it, cd into the directory,


wget madwifi.org/attachment/ticket/1679/madwifi-ng-0933.ar2425.20071130.i386.patch?format=raw



patch -p0 < madwifi.org/attachment/ticket/1679/madwifi-ng-0933.ar2425.20071130.i386.patch?format=raw


Then compile the patched madwifi ([http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo))

Reboot your computer and, at least on mine, things worked fabulously.

One more note...I noticed a few newer users complaining about dhcp not working
for them with a secure network...what worked for me is to specify "key open", i.e.
here is the list and order of commands that got me online.


sudo ifconfig ath0 up
iwlist ath0 scanning
sudo iwconfig ath0 essid whatever_network
sudo iwconfig ath0 key s:abc123
sudo iwconfig ath0 key open
sudo dhclient

---

