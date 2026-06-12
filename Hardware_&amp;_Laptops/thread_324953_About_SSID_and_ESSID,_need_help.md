---
title: "About SSID and ESSID, need help"
date: 2006-12-24
forum: Hardware &amp; Laptops
---

### Post by Sigudian on 2006-12-24
EDIT:
**Success!**
i acquired success by following [this post]("http://www.ubuntuforums.org/showthread.php?t=323481&highlight=belkin") 
witch send me on to [this how-to]("https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?action=show")
---end of EDIT---

Hi i got a new wireless network card for x-mas(if you think its early we open our presents late at the 24th des in Norway) its a Belkin Wireless G USB Network Adapter
** i have problems connection to my wirless nettwork**

i got it to work.... i think, but i cant quite connect yet. here is a screen shot of my network settings
[IMG]http://i90.photobucket.com/albums/k263/Sigudian/network_settings.png[/IMG]
you can see that it has two Wlan cards installed, i guess the wmaste0 is used for AD-hook connection.

here is my setting for the wlan0 card
[IMG]http://i90.photobucket.com/albums/k263/Sigudian/sett-wlan0.png[/IMG]
as you can see i have no password, i rather like to have a list of mac addresses allowed on my router.

here is my setup in my router
[IMG]http://i90.photobucket.com/albums/k263/Sigudian/router.png[/IMG]
[B]
Here is my problem and question[/B]
I cannot connect to my wireless network, my connection status is idle, and it trys to connect now and then. i cannot see anything wrong with my setup, can you?

is the problem that ubuntu only supports ESSID and my router sends only out SSID? or is that even a problem?
Is the problem that im broadcasting on the wrong channel? what channels should is use?
this works for my sisters windows laptop, and my PSP. 
 **[SIZE="3"]pleas help[/SIZE]**

---

### Post by cilynx on 2006-12-24
Broadcom and Ubuntu don't quite play nice.

See tutorial here:
[http://www.ubuntuforums.org/showthread.php?p=1071920&mode=linear](http://www.ubuntuforums.org/showthread.php?p=1071920&mode=linear)

---

### Post by Sigudian on 2006-12-24
Success!
thank you cilynx! i do not have bradcom card (as stated above), but what you said made me search for belkin, and i found a guide to install my chip sett. so thank you!!

---

### Post by cilynx on 2006-12-24
Congrats on getting it going.  Sorry about the mixup.  I've got Broadcom on the brain recently...

---

