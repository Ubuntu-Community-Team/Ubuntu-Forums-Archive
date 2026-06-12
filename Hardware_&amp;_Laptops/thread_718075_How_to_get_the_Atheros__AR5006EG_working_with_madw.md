---
title: "How to get the Atheros  AR5006EG working with madwifi"
date: 2008-03-07
forum: Hardware &amp; Laptops
---

### Post by bluefox83 on 2008-03-07
I Discovered that it's really not that hard to get the Atheros  AR5006EG card working in gutsy. Simply go to [http://madwifi.org/ticket/1679](http://madwifi.org/ticket/1679) and get the latest snapshot, I put mine in /home/bluefox/downloads  then i extracted the tar file by right clicking and selecting "extract here". then i opened a terminal, and cd'd into the directory it made, and did "make" and then "sudo make install" there's no need for ./configure since there is no configure script. After that, edit /etc/modules and add (in this order) :

wlan_scan_sta
wlan_wep
ath_pci


Then simply do "sudo modprobe wlan_scan_sta ; sudo modprobe wlan_wep ; sudo modprobe ath_pci" 

If you were using ndiswrapper be sure to do sudo modprobe -r ndiswrapper before you try to load ath_pci or it wont start.

Also, go back and add ndiswrapper to your /etc/modprobe.d/blacklist   or just remove ndiswrapper, I'm chosing to keep it just incase something happens, 

FYI, if for some reason you upgrade your kernel, you will need to repeat the compiling process, and make certain to do a "make clean" before recompiling, or you'll have problems.

---

### Post by em3raldxiii on 2008-03-09
Okay, this all *seemed* to complete for me with no errors whatsoever.  But ... um ... forgive me for being rather dense, but what now?  I mean, I followed your instructions closely, and I received no errors.  Everything seemed quite smooth.  But I have absolutely no idea what to do now.  I can't seem to wrap my head around madwifi - it *looks* like it does all the right stuff, and according to everything I have read, it's the most wonderful driver out there for my Asus motherboard's onboard wireless ... which happens to be this very precise Atheros "card".

Anyhoo ... I am going to try rebooting to see if it makes any difference.  And does it matter if I have the wired connection plugged in?  That's how I have been connecting to the router so far ...

Thanks for this quick and simple howto, though.  I appreciate it.

[EDIT] Okay, rebooting did nothing.  Still no changes in my Network tool, and iwconfig still just gives me two entries, each that say *no wireless extensions* ... what am I missing?

---

### Post by scottro on 2008-03-09
I believe that's actually for the AR5007EG card.  The AR5007EG is incorrectly seen as AR5006EG on 32 bit systems (and sometimes on 64 bit as well--though sometimes, on 64 bit it's seen as AR242X).  

One way to tell is to look in WIndows Device Manager if WIndows is still on the machine.  

On the Acer laptops, at least, and possibly on others, there will also be a sticker on the bottom saying it's  Atheros AR5BXB63.

I never looked into the 5006EG card as I didn't have it.  I don't know if that patched snapshot works for anything covered by MadWiFi or only for the AR5007EG.  At any rate, for the AR5006EG, if it really is one (but they seem to be disappearing in favor of the AR5007EG) I see on MadWifi's site that at least one person says it works with the patched snapshot--but of course, they too might have been fooled by lspci.  :)

A few more notes on MY experience with an Acer laptop.  (MY is all caps, meaning I might have just gotten lucky by leaving out a few of your steps.)

With ndiswrapper--before removing it, use it to remove the drivers you might have installed with it--usually either 5211 or 5416.  
ndiswrapper -e net5211  
(for example).

I didn't have to add anything to modules.  I simply did 

modprobe ath_pci

(I didn't modprobe the other two that you list either, however, it didn't give me any trouble.)

It might be worth mentioning, for those with Acers at least, that even though the wireless will work, the wireless LED will not light up.  

Despite the slight differences in our experiences, I think that your howto is going to be very helpful for people--it's quick and to the point, making it easier for newcomers to follow.  

Oops, one possibly important point.  I don't know if it will compile if the user hasn't installed build-essential first.  
apt-get install build-essential.

@em3raldxiii

I'd try a couple of things.  In a terminal
modprobe ath_pci

Then do lsmod |grep ath to make sure that worked. 

Also do 
dmesg |grep HAL

If you get nothing back, that's a good sign.  If you get back something like HAL error 3 or error 13 or something else, that's not a good sign.  :)

Now, if you got that far and are getting no HAL from dmesg and a listing showing ath_pci among other things from the lsmod, see if you have any luck doing 

sudo ifconfig ath0 up
iwlist scan

The desired result is that it will show wireless networks in your area.  If it does, then NetworkManager should begin to show them as well.

---

### Post by em3raldxiii on 2008-03-11
@scottro 
Okay, here's some outputs for you after modprobe ath_pci ... thanks for the help!

$ lsmod |grep ath
ath_pci               202808  0
wlan                  271904  3 wlan_wep,wlan_scan_sta,ath_pci
ath_hal               261248  1 ath_pci

$ dmesg |grep HAL
[   27.333227] MadWifi: unable to attach hardware: 'Hardware revision not supported' (HAL status 13)

That gives me something to work with. Any more support is of course greatly appreciated, and I will post here of my successes (or lack thereof) ;)

---

