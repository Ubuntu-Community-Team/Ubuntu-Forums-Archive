---
title: "Wireless on an acer aspire one"
date: 2009-05-17
forum: Hardware
---

### Post by darave on 2009-05-17
I have an Acer aspire one running 9.04 netbook remix and I cant activate the wireless. when I right click on the signal icon to activate it, the box is grayed out and it wont let me click it as you can see in the pic. 

[IMG]http://i14.photobucket.com/albums/a305/reprograpphics/Screenshot-1.png[/IMG]

According to the guide: [https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)
wireless should work out of the box. 

I have tried loading back ports following this guide: [https://help.ubuntu.com/community/AspireOne110L](https://help.ubuntu.com/community/AspireOne110L)

Ive tried Ndiswrapper and Ive tried madwifi because both of those worked when I was using herron and ibex. But neither of them work in jaunty for me. 

Madwifi got the wireless led working but thats about it. 

Ive asked on other sites but they just pass the buck by giving me more guides try. 

Is there something im ment to do thats not driver related to get this thing working? 

Plz help!

Thanks in advance

---

### Post by jlh68 on 2009-05-17
Wireless does work out of the box.  At least on my Acer ONE it did.  Even the front switch works and the activity LEDs blink with WiFi activity. None of that worked with 8.10 except WiFi and I had to change drivers, but the 9.04 NR works.  

You might had done what I do sometimes.  That is I try to tweak and tinker with my OS, that I some time break the system or part of it.

Try reinstalling UNR using the Synaptic Package Manager and maybe that will reestablish the baseline operating system and your WiFi should work.

---

### Post by jlh68 on 2009-05-17
Oh, just thought of this.  Why don't you try using the WiFi switch on the front edge of the Acer ONE?  Just hold it over to the right for moment and then wait for 10-30 seconds for the WiFi to come on.

---

### Post by darave on 2009-05-17
Reinstalled nbr haven't touched anything and still in the same place. and I tried the wifi switch at the front too

---

### Post by linpus on 2009-05-17
left click on the wireless icon on the top left of the screen

click on create new wireless network, or if it a secure network try "connect to hidden wireless network"

i had to do this to get mine to work

---

### Post by darave on 2009-05-18
top left? you mean top right?

If I LC on that all I get


**Wired Network**
disconnected
**Wireless Networks**
wireless is diabled

---

### Post by jlh68 on 2009-05-18
Right click on the icon.  then click on "edit connections" to set up either wired, wireless, mobile broadband, VPN, or DSL. 

Wireless in your case.

---

### Post by darave on 2009-05-18
Did that, didnt do anything tho. I dont see why it would either seeing as the wireless is disabled.

---

### Post by doccpu on 2009-06-13
did new install of 8.10 on an acer one 8.9
It has NO clue that there is a wireless port. It does say the drivers are there but network manager doesn't have a clue its there. Is there any decent software to get it to load drivers, turn on drivers, add driver to linux then use the driver to see a network?

---

### Post by jlh68 on 2009-06-15
Go on and install 9.04 NR and see if that helps  Otherwise you have to follow the folloing:
Wireless Broken in Intrepid RC; how to install /home to an SD card

> [I]Two things: 1) Some reports that the latest Intrepid / updating from an Intrepid beta breaks wireless.

    *

      Note: The driver "ath5k" has been removed from the stock Intrepid kernel, because it's not working reliably on some machines. It works, however, on the AAo, you can easily get it by installing "linux-backports-modules-intrepid" christian-paratschek
    *

      Be sure to install the backports package first if you rely on the wireless card, before you do a system update. You may also have to disable competing drivers in the Restricted Drivers manager after rebooting. -- dsm-iv-tr 
[/I]

ath5k is in Jaunty and works just fine with an AAO.

---

### Post by Gh0sTly on 2009-12-04
Not to bring back a dead thread, but ive got a AAO AOA150, with a FRESH install of UNR 9.10, and my wifi doesnt work.  Any ideas?

---

