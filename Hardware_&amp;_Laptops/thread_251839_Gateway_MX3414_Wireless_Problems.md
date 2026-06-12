---
title: "Gateway MX3414 Wireless Problems"
date: 2006-09-06
forum: Hardware &amp; Laptops
---

### Post by Leecs1014 on 2006-09-06
idk if anyone else has had this problem, but my MX3414 will lose wireless connection when i am on forums with pages of pictures or when i am downloading.  it will lose connectivity, so i open up View Wireless Networks.  when i do this, i go to disable/enable and then the computer will freeze.  anyone else had this problem and if so what did you do.  thanks

---

### Post by yourearthlymaster on 2006-09-06
Im running am MX7514, but I cant even figure out how to get my wireless thingy to work.  I know I have one built in, it worked fine with widows, but I dont get how to work it in linux.  
total newb, I know.  
but when I figure it out, I'd love to try and help you.

---

### Post by Neobuntu on 2006-09-06
If the freeze is related to your wireless then you may have two driver modules trying to run the one device.

Determine which chipset your wireless device has and if you're using the actuall XP driver (by ndiswrapper) you may need to blacklist the one automatically trying to work. Search for what others (here) are doing with that chipset.

Oh, and a anti-competitive Microsoft alined and mostly software device (where the chipset maker will not play) AND that's more difficult to set up in Windows, is hardly a fair observation but I understand your confusion. That's what Micosoft does excell at; well.

Don't forget, one can online order a replacement wireless device that's known to work with zero driver(module) setup for less than $10. For the now rare situation; when everything doesn't just work, it's a very small price to pay for free and much better (and quickly and more benifically improving) software for life.

Hope this helps.

---

### Post by azraelx401 on 2006-09-06
> **Leecs1014 said:**
> idk if anyone else has had this problem, but my MX3414 will lose wireless connection when i am on forums with pages of pictures or when i am downloading.  it will lose connectivity, so i open up View Wireless Networks.  when i do this, i go to disable/enable and then the computer will freeze.  anyone else had this problem and if so what did you do.  thanks

well yea it could be that you have to drivers competing for one device and that's a battle that no one will win unless you blacklist one of them.  but if you know you only have one driver running then you might want to check how your wireless router is doing.  my linksys router started doing that a month ago and then it just stopped working.  the lights were on but nobody was home.  so i went out and bought a new one.  the linksys router was pretty old so now with my new one i keep my connection at all times.  but also is your wireless card built in?  how far are you from the router?  have you installed more then one network utility?

---

### Post by azraelx401 on 2006-09-06
> **yourearthlymaster said:**
> Im running am MX7514, but I cant even figure out how to get my wireless thingy to work.  I know I have one built in, it worked fine with widows, but I dont get how to work it in linux.  
total newb, I know.  
but when I figure it out, I'd love to try and help you.

you need to check to make sure you have the a driver installed for it

sudo lmod | grep ipw2200

substitue ipw2200 with the driver you should have.  now if after you run that you get a message then the driver is installed.  second thing make sure that the card is enabled. 

go to System > Administration > Networking.  You should see a wireless card icon just click on that and make sure it's enabled.

---

### Post by Leecs1014 on 2006-09-06
i had a geek squad buddy of mine over and he checked out the router, and his notebook and my desktop were working fine, but when i got my laptop up and running and did the same stuff, it died so it has to be the computer itself, i just dont know what it is

---

### Post by rabbi1337 on 2006-09-06
Not to go off your issue, I was wondering if you managed to get sound up and running on your machine? And if so, how? Thanks in advance.

---

### Post by Neobuntu on 2006-09-08
Take the wireless out of the picture by hooking up a cat5 cable to the ethernet port from the notebook and connecting to the router. If you still have the problem, it's not the wireless device.

If you don't have the problem you may have range problems or the driver issues we have disscussed. Wireless introduces several variables. 

As a  side note; Wireless or not, you may also want to set up static addresses so that your boot up doesn't wait for DHCP.

---

