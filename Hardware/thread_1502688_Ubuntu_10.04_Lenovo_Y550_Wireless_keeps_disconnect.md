---
title: "Ubuntu 10.04 Lenovo Y550 Wireless keeps disconnecting at random time interval"
date: 2010-06-05
forum: Hardware
---

### Post by ryufly on 2010-06-05
I have been using ubuntu 10.04 on my Lenovo Y550 laptop for more than a month.
And the wireless connection keeps dropping at random time interval.
I have been googling around. Seems like I am not the only one having this problem.
Is it a bug or something?

---

### Post by ryufly on 2010-06-05
No one?

---

### Post by srs713 on 2010-07-31
I have had this happen in only one place only so far. At one coffee shop I have MANY WiFi routers detected in the area. More than anywhere else. I keep getting knocked off-line here, but can go 5~6 hours without problems elsewhere.

I have to keep a terminal open and use "sudo ifconfig wlan0 down" to shut off the wireless, then reconnect to the router using the WiFi icon on the control panel. Simply hitting reconnect doesn't work. I HAVE to take the connection down for it to talk to the router again.

I think it is a problem with the client daemon having trouble handling multiple routers on one channel. As I said I've never had this problem anywhere else, but most places I go have only 3~5 routers in the area. This spot has 8~15 depending on where you sit.

---

### Post by ryufly on 2010-09-04
> **srs713 said:**
> I have had this happen in only one place only so far. At one coffee shop I have MANY WiFi routers detected in the area. More than anywhere else. I keep getting knocked off-line here, but can go 5~6 hours without problems elsewhere.

I have to keep a terminal open and use "sudo ifconfig wlan0 down" to shut off the wireless, then reconnect to the router using the WiFi icon on the control panel. Simply hitting reconnect doesn't work. I HAVE to take the connection down for it to talk to the router again.

I think it is a problem with the client daemon having trouble handling multiple routers on one channel. As I said I've never had this problem anywhere else, but most places I go have only 3~5 routers in the area. This spot has 8~15 depending on where you sit.

I am having the excatly same problem as you metioned. It's really annoying. 
Unfortunately, I live in a place covered by multiple wirelesses. (Definitely more than 8 )
As you said, simply hitting reconnect doesn't work.
Thanks for the tip "sudo ifconfig wlan0 down".

So it is my understanding that this has nothing to do with my settings or anything.
I only have my place to blame.
Is there any workaround? 
Can I fix this by upgrading the firmware or something? 

Or I can only sit there and wait for it to disconnect and then restart wlan0?

---

