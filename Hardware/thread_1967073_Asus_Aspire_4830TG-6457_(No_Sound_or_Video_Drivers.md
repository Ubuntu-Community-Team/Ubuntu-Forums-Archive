---
title: "Asus Aspire 4830TG-6457 (No Sound or Video Drivers Available)"
date: 2012-04-27
forum: Hardware
---

### Post by Growlbacks on 2012-04-27
Hello all!

Well I am finally stuck on my machine and needed it for school and now time for some Windows in a box to make my job easy until there are drivers for the laptop.

Here is the laptop break down on hardware as listed per the vendor website:
[http://us.acer.com/ac/en/US/content/model/LX.RGL02.177](http://us.acer.com/ac/en/US/content/model/LX.RGL02.177)

It was working prior to the update to 12.04 for both video and Audio and as of now ... no luck. I have done all the updates and reboots and searched online with no success.

Looking forward to getting this to function properly and appreciate all of your help.

Thank you again, 

Rick

---

### Post by gonzo the great on 2012-04-28
That is rather peculiar.
I have a very similar laptop Timeline X 4830TG-6450. I installed 12.04 today and almost everything works out of the box. There were 2 minor issues though:
1. Screen brightness could not be adjusted [a recurrent team to many acers it seems, but with a simple workaround. I followed these instructions and it now works: [http://askubuntu.com/questions/125471/cannot-change-brightness-on-an-acer-aspire-5745-dg]](http://askubuntu.com/questions/125471/cannot-change-brightness-on-an-acer-aspire-5745-dg]) Have to note this was also the case in 11.10.
2. Both graphic chips were running all the time, draining a lot of the battery power. The solution was installing bumblebee 3.0 and now that also works flawlessly.

Sound worked out of the box.
Try making a clean install rather than an upgrade from a previous version. with us having all the same components [except for the processor. mine is i5-2430M], i can't see a reason why it wouldn't work.

cheers;
g

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-04-28
Your computer is not Asus, it's Acer. Can you please change the thread title?

---

