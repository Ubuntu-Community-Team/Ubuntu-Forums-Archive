---
title: "Strange problem with WiFi (RTL8191SE, Toshiba A500 1HK)"
date: 2012-06-19
forum: Hardware
---

### Post by mind_exploit on 2012-06-19
Hello, guys,

I have this strange problem: with Ubuntu 12.04 on my Toshiba A500 1HK, with WiFi RTL8191SE. So, for the WiFi Ubuntu uses the driver in the kernel, and it works. But - with some strange behavior.

I'm able to connect to all the wireless networks and use them with no problem. But this lasts only for a short time - suddenly I'm unable to open anything from the internet. And the most interesting thing is that I'm still connected to the router. And the other devices, connected to the router, have internet connection as well.

I have this problem on every router I connect to, and had this problem on the other distros I was using - openSUSE, Fedora and ArchBang.

I thought that I may have problem on hardware level, but when I'm in windows - I don't lose internet connection ever.


So, can you give an advise, please, cause this is very unpleasant.

(For example - is there a command I can write in Terminal when I see that the internet connection is gone and I'm still connected to the router? ... the "ping" is not working too when I loose connection.)

Thanks in advance ...

---

### Post by Redblade20XX on 2012-06-19
When you first start up the computer, open a terminal and type in:
```
iwevent
```

This will monitor any wireless events that occur and the kernel acknowledges. Hopefully it will give us some information. Also you can check your /var/log/kernel.log to see if anything got logged in.

-Red

---

### Post by mind_exploit on 2012-07-11
Hello,

I tried with the iwevent, and so it gives:

[datetime]  wlan0  Scan request completed
[datetime]  wlan0  Scan request completed
.....

and from time to time it gets:

[datetime]  wlan0  New Access Point/Cell address:Not-Associated
[datetime]  wlan0  Association Response IEs:01282743........
[datetime]  wlan0  New Access Point/Cell address:[some mac address]

and in the moment it looses internet:

[datetime]  wlan0  Scan request completed
[datetime]  wlan0  Scan request completed
[datetime]  wlan0  New Access Point/Cell address:Not-Associated
[datetime]  wlan0  Scan request completed
[datetime]  wlan0  Scan request completed
...... 


and in the kern.log  on the same moment I have:

.... 
 cfg80211: All devices are disconnected, going to restore regulatory settings
 cfg80211: Restoring regulatory settings
 cfg80211: Calling CRDA to update world regulstory domain
 cfg80211: Ignoring regulatory request Set by core since the driver uses its own 
 cfg80211: World regulatory domain updated:
 cfg80211:      (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
 cfg80211:      ( {some frequences here} ...)
 wlan0: authenticate with {some MAC address} (try 1)
 wlan0: authenticate with {some MAC address} (try 2)
 wlan0: authenticate with {some MAC address} (try 3)
 wlan0: authentication with {some MAC address} timed out
 wlan0: direct probe to {some MAC address} (try 1/3)
 wlan0: direct probe to {some MAC address} (try 2/3)
 wlan0: direct probe to {some MAC address} (try 3/3)
 wlan0: direct probe to {some MAC address} timed out
... 

and the last 4 rows repeat to the end ... 


Does this help us understand the problem?

---

### Post by Redblade20XX on 2012-07-11
Seems like a kernel problem with the wifi driver if it's affecting across distros. Have you tried compiling the proprietary driver and installing them to see if the driver, in essence, is the problem?

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=48&Level=5&Conn=4&ProdID=226&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=48&Level=5&Conn=4&ProdID=226&DownTypeID=3&GetDown=false&Downloads=true) 

- Red

---

### Post by Dy1anW on 2012-07-11
Hi, I also have the same problem. I've been monitoring my network's status with iwevent as well, but it doesn't seem to notice when the connection drops. Line after line is the same:

[timestamp]  wlan0  Scan request completed

This is what I get on the *** end of kern.log:

Jul 11 22:06:23 [name] kernel: cfg80211: (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jul 11 22:06:24 [name] kernel: wlan0: authenticate with [MAC] (try 1)
Jul 11 22:06:24 [name] kernel: wlan0: authenticated
Jul 11 22:06:24 [name] kernel: wlan0: associate with [MAC] (try 1)
Jul 11 22:06:24 [name] kernel: wlan0: RX ReassocResp from [MAC]
Jul 11 22:06:24 [name] kernel: wlan0: associated
Jul 11 22:06:24 [name] kernel: iwlwifi Tx aggregation enabled on [MAC]
Jul 11 22:06:24 [name] kernel: wlan0: no IPv6 routers present
Jul 11 22:06:24 [name] kernel: cfg80211: Found new beacon on [freq] (Ch12) on phy0
Jul 11 22:06:24 [name] kernel: cfg80211: Found new beacon on [freq] (Ch13) on phy0

I'm not sure why it would want to start looking for new networks on its own. When I restart the network, I see similar log entries up to and including 'no IPv6 routers present', and my wireless connection will be fine again for a while, until it spontaneously decides to stop again. Even when it does stop, it still shows full signal strength.

---

### Post by mind_exploit on 2012-08-02
Hey, guys :)

I finally managed to solve it.

(Installed the driver from the drivers page that RedBlade gave the address for ... [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=48&Level=5&Conn=4&ProdID=226&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=48&Level=5&Conn=4&ProdID=226&DownTypeID=3&GetDown=false&Downloads=true) - and this fixed the thing at home, but at work the problem continued to appear.)

So, after some more research and inspecting the logs - I managed to find a solution for that. (I think I searched for "deauthenticaion from reason 2" then ... just don't remember exactly, cause wanted to wait a few days or weeks to see if the problem has REALLY gone away.) And so - I tried the solution and the problem now doesn't appear any more, any where.

And the solution is - to instasll wicd, and uninstall NetworkManager - following this article: [https://help.ubuntu.com/community/WICD/](https://help.ubuntu.com/community/WICD/)


Hope this helps to other guys that have the same problem - including Dy1anW as well :)

---

