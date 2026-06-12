---
title: "Cannot Use Sansa m250 MP3 Player"
date: 2006-08-13
forum: Hardware &amp; Laptops
---

### Post by zigx on 2006-08-13
NOTE MY SUBJECT HEADING IS INCORRECT, THE MODEL IS AN E250, NOT M250.  i am unable to change the thread's subject for some reason.




Hi All, 

I have searched the forums for help on this issue and i saw a few people with somewhat similar situations but i think mine is a bit different -- hence the new thread.

Basically i have a Sansa e250 MP3 player and when i attach it to my Ubuntu box (6.06) nothing happens.  The MP3 player says that it is connected but nothing gets mounted.

I looked in device manager and this is what i see:
[img]http://img70.imageshack.us/img70/9158/screenshotrj6.png[/img]

So clearly the system sees the MP3 player but i think either i need to mount it manually or maybe something else needs to be done but im not sure how/what to do.

Any input would be greatly appreciated!!


thanks for your time.

---

### Post by zigx on 2006-08-13
i forgot to mention that i installaed amaroK and i did not notice any change... i think this is because amaroK probably requires the device to me connected/mounted properly before you can use amaroK with it.

thanks.

---

### Post by zigx on 2006-08-13
updated subject with correct mp3 player model

---

### Post by texas697 on 2006-08-13
I just got one today, switch the usb mode in the players settings option, it will mount like any other mass storage device, drag and drop files to there folders.

---

### Post by zigx on 2006-08-13
Fixed it!  Correct mode is MSC found by scrolling on the LCD 

Settings > USB > MSC

---

### Post by jamesstansell on 2006-08-19
My son just got a Sansa e250, and we're using Dapper 6.06.1 as the host.

The first day the e250 connected fine and he was able to transfer files. Unfortunately the MP3's hadn't been ripped properly so they weren't valid files.  So he deleted them from the Sansa.

Now we have the ripping working but the e250 isn't connecting to allow file transfer.  It says connected at first, and the system log shows a promising udev message.  But then the e250 starts alternatively displaying connected / disconnected.

We've verified that the device is in MSC mode.  Has anyone else seen this behavior?

Thanks!

-james.

---

### Post by Spriggs on 2006-10-25
this might be a silly idea but did you connect it directly to the computer or using a hub? as far as i know it requires a lot of juice since it's recharging while you're still able to copy files. 

i tried to convert a movie using the windows tool (sorry ;)) but it didn't work. it plays fine under linux using but as soon as i try to play it on the sansa it says i need to convert it. anyone found a solution (or the settings of the video/ codec) to do this using any linux apps?

sorry for posting this here but this one seem to be the only decent thread about the sansa and i didn't want to open another one.

---

