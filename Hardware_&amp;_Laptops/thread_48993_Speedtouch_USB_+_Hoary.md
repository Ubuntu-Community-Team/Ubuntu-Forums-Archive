---
title: "Speedtouch USB + Hoary"
date: 2005-07-14
forum: Hardware &amp; Laptops
---

### Post by irbaileyus on 2005-07-14
hi, i'd just thought i'd say i know that there are many posts on getting a speedtouch modem up and running but i've tried a lot of them and i seem to have come to a wall!  ](*,) 

i have tried the instructions for hoary at [www.linux-usb.org/SpeedTouch/ubuntu/](www.linux-usb.org/SpeedTouch/ubuntu/) with little success 

i also tried wiki.ubuntu.com//UKSpeedtouchDSLHowTo with the same result.

the closest i got was by using speedtouch-setup in the console window, but something seems to go wrong as the modem tries to load up the firmware.
the lights blink- two green, then usb red/amber/green then the adsl flashes amber ONCE then just stays amber and does nothing.

i know its not my adsl connection because i am using the modem now with windows and i had it running with mandrake a week or so ago.

if anybody can suggest anything that might help or can give me instructions if they've had a similar situation or even jus explain wots happening i would be very very very very very very grateful!!!  :)

bails

---

### Post by kayas80 on 2005-07-14
As a linux newbie I cant offer a great deal of technical advice but I have a few suggestions based on problems I encountered. I have the same speedtouch modem. I used the link you mention ([http://www.linux-usb.org/SpeedTouch/ubuntu/](http://www.linux-usb.org/SpeedTouch/ubuntu/)) as a guideline and managed to get it working (though it was tricky). 

1. Make sure you download the correct files.
2. Check you have the correct VPI and VCI numbers - dependent on your country

I've tried installing the speedtouch modem on a few different linux distributions and from my experience and what I've read USB modems are a real pain to get working.

Good luck

Oliver

---

### Post by kayas80 on 2005-07-14
I don't know what country you live in, but check whether your ISP uses either PPPoATM or PPPoE. I live in the UK where you can use either of the two so be careful you don't get caught out!

Oliver

---

### Post by irbaileyus on 2005-07-15
i'm pretty sure im using the right files, its the package the speedtouch-setup tells me to download, think i also tried using another firmware package that worked previously in mandrake.

i know the vpi=0 and vci=38 and my connection is PPPoA as those are the settings i used in mandrake and am using in windows.

are there any linux wizzes out there who know how the test if i've got this all setup right? any help would be much appreciated

ps thnx for the help oliver.

---

### Post by fig_jam_uk on 2005-07-16
I would personally recomend and ADSL router their pretty cheap and much better, and all you need in the machine is a NIC... jobs a good`en

---

