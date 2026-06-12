---
title: "Intel 6230 advanced-N Bluetooth device not found"
date: 2012-02-18
forum: Hardware
---

### Post by kyosaku on 2012-02-18
Hi there,

I have always wanted to use bluetooth on my Vaio notebook VGN-C1S, and since I only have two USB slots on this sweet little machine, I chose to replace the preinstalled Intel 3945 by a WLAN Bluetooth Combo miniPCIe "Intel 6230 Advanced-N".  

After succesful installation and boot, the device gets recognized on my Ubuntu 11.10 x64 and WIFI/WLAN works fine with no problems.  So far, so good. But the bluetooth device is not recognized, and it does not show up on bluetooth system settings.

I have already send the first card back to retailer, for another one, suspecting it was broke.  So got a replacement today, built it in - same problem.

Tried to make it work under Windows XP, too, with the latest bluetooth and WIFI drivers - same thing there - WIFI ok, but no bluetooth device available.

So I contacted Intel support, but they just said they couldn't give support to end users and suggested contacting computer manufacturer for compatibility issues (which I did in the meantime, too, posting in the Sony forums - no answer as of now).

Here are some basic informations, which I don't know if they're of any use, but I read a lot of threads and tried some things.  So maybe these outpouts will be of some meaning to someone out there ...

Kernel version is:  3.0.0-16-generic 

Can it be that my system is just plain too old to support bluetooth (VGNC1S = 2006 model), or is the bios too old (Phoenix Netbios 4.0 Release 6.1) ?
Any help or suggestions are greatly appreciated ! I really would like to get this thing running and hate the idea of having to send it back after having invested so much time (and devotion ...) in solving this.

---

### Post by Starks on 2012-02-18
You put a new card in an ancient machine, what were you expecting? I used to have a laptop with the 3945, good card. As for the 6230, I have that in my current laptop. You need to load the module with "sudo modprobe iwlwifi 11n_disable=1" after unloading it with "sudo rmmod iwlwifi" for full wireless speed.

Unless there's a hotkey on the keyboard or a BIOS setting, you might be screwed for BT.

What does "rfkill list" say?

---

### Post by kyosaku on 2012-02-20
thank you for taking the time to answer, here's the requested output

{{{ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes}}}


I just wonder what happened to the specifications that used to be detailed on products before sale - when you used to know what kind of system would run with a given hardware, just by looking at the product's description.  neither intel nor the distributing company give any information as to any standard required, besides miniPCIe.

I'll try the highspeed trick with WIFI and see if it works.  Any other ideas are greatly appreciated.

---

### Post by kyosaku on 2012-02-20
PS: oh i forgot, I enabled the WLAN by hardware when testing bluetooth, even if  current output suggests the opposite

---

### Post by kyosaku on 2012-02-25
any ideas ?

meanwhile I tried to make Intel 6230 workin full wireless speed - but it didn't work out either.

here's what CL says:

$ sudo rmmod iwlwifi
ERROR: Module iwlwifi does not exist in /proc/modules
$ sudo modprobe iwlwifi 11n_disable=1
FATAL: Module iwlwifi not found.

what is wrong ? you and I are using the same card !

---

### Post by ahallubuntu on 2012-02-25
You assumed that you could use bluetooth on this old Sony just by installing a WiFi card that also has a bluetooth module.  I don't think that's a valid assumption.  The chipset of the laptop may also need to be able to use the bluetooth, which may not be possible.  The fact that it works at all (for WiFi) is a big plus.  At least you have 802.11n (right)?)  

Where did you buy this card?  Are you sure it's a true 6230 card?  I've had some bad experiences buying Intel wireless cards from Asian suppliers; they have sometimes sent the wrong cards that had similar part numbers.  In one recent case I received a "G" version of the Intel 6200 (Russian version).  Amazingly, the 10.04 kernel driver (iwlagn) recognized it as an N card and connected to my router at N speed - but Windows only saw it as "G" and so did newer kernels in newer versions of Ubuntu.  (I got a refund.)

This thread suggests FYI that even if you could get bluetooth running on this card you could have WiFi issues:

[http://askubuntu.com/questions/69234/centrino-advanced-n-6230-and-bluetooth-wireless-problems-with-dell-xps-15z](http://askubuntu.com/questions/69234/centrino-advanced-n-6230-and-bluetooth-wireless-problems-with-dell-xps-15z)

and the recommended fix there (seen it before) is:


# rmmod iwlagn
# modprobe iwlagn 11n_disable=1 power_level=5

though that DISABLES 802.11n which means your card is basically running at the G speed of your old wireless card.  FYI, I use a couple of Intel non-BT cards (5100, 5300) successfully in different laptops with Ubuntu and get decent wireless speeds - no need to "disable" the N speeds.

---

### Post by kyosaku on 2012-03-03
Hi first of all let me thank you for taking the time to answer.

As I have had correspondence with Intel I am quite sure this card is a genuine Intel.  What they basically said in an email reply was: if it shows up in the windows xp device manager as Intel 6230 Advanced-N, then it has to be Intel 6230 Advanced-N.

I bought the card from a friendly and competent german distributor "Leicke", who tried to help me out by sending a second card and even accepting taking it back - which by the way I did not do, because I have finally decided to keep it for an eventual fix (concerning max. wireless speed under Ubuntu - not more than 54 mbit/s - or installing the card in another system, whose mainboard would hopefully be compatible).

The reason I assumed the system would be compatible with bluetooth was that there seemed to exist a version the Sony Vaio VGN-C1S that had it installed and working.  But apparently it was only sold in the UK.  

Finally I might add, that a german user on ubuntuusers.de told me that there was probably also an issue because I installed and adapted miniPCIe half size on a miniPCIe full size socket.  Something with connections, I did not understand.  But hey, I am glad to have been given the opportunity to learn something on this.

If noone else has a grain of salt to add concerning this matter, I would like to thank all the people in this thread for their help !

---

### Post by sysmatck on 2012-09-24
So sad to read this post now. I am in a very similar situation...

I bought this combo card too, and my hardware is a VGN-FE550G; running on Lubuntu 11.10 i686

Wifi is working ok (didn't do speed tests) but bluetooth does not recognizes as mentioned before. The debug commands also return the same contents...

Even though, I guess this card should work, I mean, is the same manufacturer, maybe a BIOS update would be required, but in my dumb opinion all miniPCIs devices should be able to work; the same way desktop PCIs runs old and new boards!

Guess I will try with another combo cards, maybe an cheap generic card will do the job!

---

### Post by sysmatck on 2012-09-25
> **kyosaku said:**
> Hi first of all let me thank you for taking the time to answer.

As I have had correspondence with Intel I am quite sure this card is a genuine Intel.  What they basically said in an email reply was: if it shows up in the windows xp device manager as Intel 6230 Advanced-N, then it has to be Intel 6230 Advanced-N.

I bought the card from a friendly and competent german distributor "Leicke", who tried to help me out by sending a second card and even accepting taking it back - which by the way I did not do, because I have finally decided to keep it for an eventual fix (concerning max. wireless speed under Ubuntu - not more than 54 mbit/s - or installing the card in another system, whose mainboard would hopefully be compatible).

The reason I assumed the system would be compatible with bluetooth was that there seemed to exist a version the Sony Vaio VGN-C1S that had it installed and working.  But apparently it was only sold in the UK.  

Finally I might add, that a german user on ubuntuusers.de told me that there was probably also an issue because I installed and adapted miniPCIe half size on a miniPCIe full size socket.  Something with connections, I did not understand.  But hey, I am glad to have been given the opportunity to learn something on this.

If noone else has a grain of salt to add concerning this matter, I would like to thank all the people in this thread for their help !

Hey, I'm thinking, maybe your distributor "Leicke" has an intel 6200 chipset card, or an intel 1030; Both have Linux Drivers, if you have that freedom with the supplier, it might worth trying!

---

### Post by kyosaku on 2012-09-25
Thankyou for your suggestion.  Unfortunately, the time window for possible return has expired.  Nonetheless I can recommend 'Leicke', as their customer support was willing to take the card back and do a refund.In the end  I chose not to do this and decided to keep it anyway and buy a cheap bluetooth dongle in addition - also because I had gotten a little exhausted and really didn't want to go through another return process.    - Now I have kept the card and have one in reserve, which is ok considering that the price was really good.  Who knows, maybe one day I'll need one ?

---

