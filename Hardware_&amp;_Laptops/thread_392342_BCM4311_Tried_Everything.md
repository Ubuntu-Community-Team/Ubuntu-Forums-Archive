---
title: "BCM4311 Tried Everything"
date: 2007-03-24
forum: Hardware &amp; Laptops
---

### Post by stoopid1 on 2007-03-24
So, I have read about a dozen HOWTOs and tried just about every one of them.  I was able to get the wireless working but it loads about half a page and hangs up each time.  signal is strong.

i followed this tutorial to get to the state i am in now: [https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper)#head-098ca800f091658e3c14458a4224048957b02850]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper)#head-098ca800f091658e3c14458a4224048957b02850")

my laptop is a dv2020. I uses a BCM4311:
01:00.0 Network controller: Broadcom Corporation Unknown device 4311 (rev 01)

i used ndiswrapper 1.34 and sp33008.exe  and i'm using Ubuntu 6.10

I'm new to linux and ubuntu, so please be patient.

according to the tutorial iwconfig is supposed to give you a wlan0 but i get 

```
jacob@coitus:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"Porno Store"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:18:39:50:86:44   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:84/100  Signal level:-42 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
```

i don't think that makes a difference, but i'm not the best judge of that.

---

### Post by elephant007 on 2007-03-24
what management are you using?
So you are saying that you are able to get a signal, you're able to ping your router and when you go to visit a website it just hangs?  Is this one particular website or have you tired different ones?

One thing I would do is this, open a terminal and type
```
ping www.google.com
```

let that run and while it's pinging, open up your browser and go to a page that you've never been to, like [http://www.keepercorp.com]("http://www.keepercorp.com")
wait to see if the website freezes, if it does, check the terminal and see if the ping stops too

---

### Post by stoopid1 on 2007-03-24
anything i did, even check my email, made my wireless hang up.  

I however seemed to fix the problem.  I uninstalled the drivers for ndiswrapper, then i uninstalled ndiswrapper, removed the module from the kernel and restarted.  i re-did everthing while following the instructions religiously.  then, at the end of step 6, just before i had to restart, linux froze.....i restarted, right clicked on the network connection icon, selected wlan0 (which i was supprised to see) unplugged the ethernet cable, and it worked.  im scared to finishing the instructions...should i or shouldng i finish it?  I mean, i didnt even add ndiswrapper to /etc/modules

I just hope it wont hang up, or that once i restart it will continue to work

i wrote this msg using my wireless

---

