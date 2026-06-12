---
title: "Belkin wireless router help"
date: 2008-09-24
forum: Hardware
---

### Post by dodle on 2008-09-24
My in-laws purchased a Belkin Wireless G Router a while back.  They have complained that their internet has been slow ever since.  The internet and wireless lights are constantly blinking.  They have DSL, and I have noticed it being pretty slow as well.  Does anybody have any experience with these routers?

---

### Post by Crafty Kisses on 2008-09-25
What are the results of this command?
```
lshw -C network
```

---

### Post by dodle on 2008-09-25
Well..... unfortunately it's not hooked up to a linux machine.  *guilt*

---

### Post by caljohnsmith on 2008-09-25
Just an idea, but usually "blinking lights" on a router happens when there is data transfer, so do your in-laws have an open network, i.e. no encryption? That is what you get by default when you turn a router on "out-of-the box", so if they haven't configured it to use WEP/WPA, then maybe they've got some neighbors who are leeching and hogging all the bandwidth on it.

---

### Post by dodle on 2008-09-26
It's using WEP, but I was thinking about setting it to WPA because I've heard that it's better.  I'll try that tomorrow, and change their password.  While downloading, it doesn't seem like it's much faster than dial-up.  Can some DSL connections be as slow as that?  I'm sure it used to be faster though.

---

### Post by caljohnsmith on 2008-09-26
I would suggest first finding out what your download speed really is with one of these sites:

[www.speed.io](www.speed.io)
[www.dslreports.com](www.dslreports.com)
[www.speedtest.net](www.speedtest.net)

Make sure when you run the tests that you aren't using your internet connection in any other ways, i.e. no downloading, etc. Also, you should be able to log into your router configuration and see who is currently using the WLAN, so that will tell you if there are any leechers. But since you are using WEP, I highly doubt anyone is leeching off your WLAN; even though WEP is easily crackable with the right software and hardware, most average computer users don't know how and instead will just leech an open network.

---

### Post by markbuntu on 2008-09-26
I have one of those, works OOB with Ubuntu. I used firefox to set it up. Its address is 192.168.2.1. It is dirt simple.

Be sure to set a password or anyone else can and highjack the router. You can also hide it if you want to keep other people off of it by turning off broadcasting and then setup your folks computer to connect to it anyway. I have my Acer Aspire One with XP setup (soon to get Intrepid) to do that and it works fine.  

A day after I plugged it in I found 5 people were using it so I had to take action. Funny thing about that, they are all my neighbors and have their own password protected wireless routers and they were using mine. So I hid it and password protected it and set it up for WPA. The internet connection is much faster now. Be sure to scan your folks computer for viruses.

---

### Post by dodle on 2008-09-26
Here are the results from speedtest.net:  [[IMG]http://www.speedtest.net/result/329763934.png[/IMG]](http://www.speedtest.net)

---

### Post by dodle on 2008-09-26
I just updated the firmware on the router.  Webpages seem to be loading a little faster.  The speed test is still the same.  Also, the lights have not been blinking lately while we are not doing anything.  Downloading files still takes longer than I think should.  My files are downloading at around 25kbs, isn't that about dial-up speed?  It doesn't matter what server I am downloading from either.  I'm going to try hooking up my laptop directly to the DSL, bypassing the router and see if that makes a difference.

---

