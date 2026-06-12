---
title: "[SOLVED] Please I need Help with my new ubuntu  v8.10"
date: 2008-12-28
forum: Hardware
---

### Post by sadaruwan12 on 2008-12-28
Hi,

I'm a die hard Ubuntu user I've a AMD64 3200+ system and currently I'm using Ubuntu v8.04 on my system and I don't have any troubles. But when I switched to the new release of Ubuntu my internet connection went down and the network card stopped communicating with my ADSL router. I use a prolink H9000 single port router that works with out any problems with my current system. The IP range of this router starts from 10.0.0.5 I tried everything I know but I couldn't get the Ibex to connect to the internet. can any one out there help me with this. Earlier I thought it might be the drivers but no it wasn't I really don't why Ibex is not connecting with the net. But when I boot up the system the network adapter shows all the IP setting are ok and I'm connected to the network but when I try to connect to the net I can't. When I try to ping my router it's says "Network is unreachable" please help me.

:confused:

---

### Post by itix on 2008-12-29
Uuhmm. I think we could use a bit more information before we take a bite in this issue.

To what degree can you connect to the router? Does your computer discover the router at all? Is the issue that you can connect to the router but still not reach the internet??

If you can connect to the router, how many of the required information (ip, DNS etc) is given (right click and select connection information)?

---

### Post by sadaruwan12 on 2008-12-29
hx for the reply itix OK it's like this when I boot up my Ubuntu v8.10 the network manager shows that I'm connected to the network but when I try to reach the internet it doesn't work when I go to the connection information all the network setting are OK and they look like this,

Interface         : Ethernet(eth0)
Speed             : 100 Mb/s
Driver            : forcedeth

IP Address        : 10.0.0.xx
Broadcast Address : 10.255.255.255
Subnet Mask       : 255.0.0.0
Default Router    : 10.0.0.10
Primary DNS       : 10.0.0.10
Secondary DNS     : 0.0.0.0
Hardware Address  : 00:15:58:53:ED:FF

According to my other installation it seems right but when I disable the network and re-enables it the network manager can't find my router and the network and it says you're disconnected from the network. Even when I configure the network manager manually the same massage is displayed. When I try to restart my network adapter it gives an error massage and I've attached that to this reply. But when I connect an new version of the same brand I can connect to the internet and I can do anything with my network I really don't know why pleas help me.

:(

---

### Post by itix on 2008-12-29
That is really wierd... everything seams to be OK. I can't find a single thing that is wrong (except the eth0-problem in the attachment which is really wierd)

How long have you had the problem?

---

### Post by itix on 2008-12-29
Look what I found :)

[http://ubuntuforums.org/showthread.php?t=963440](http://ubuntuforums.org/showthread.php?t=963440)

I think this might be a bug in the forcedeth network driver.

Here is another one: [http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1096367.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1096367.html)


I think forcedeth needs to be downgraded to the version you had on Hardy (damn, this got complicated).

I wonder if Intrepid Ibex works with older kernels. It would probably be easier to downgrade the kernel (however I DON'T reccomend either).

Would it be a lot of trouble to install Hardy again? Hopefully forcedeth should be upgraded soon, but I don't really know how the hell you are supposed to upgrade without internet connection.

---

### Post by sadaruwan12 on 2008-12-30
> Would it be a lot of trouble to install Hardy again? Hopefully forcedeth should be upgraded soon, but I don't really know how the hell you are supposed to upgrade without internet connection.

Well it's like this currently I'm using Hardy Heron 'cos it's very stable and I didn't upgrade the system just removed every thing and installed the intrepid ibex then when I came across this bug I reinstalled Hardy then when some said to do some steps then again I again installed Ibex and tried when it didn't work I reinstalled Hardy again and I'm using it till now.

THX for the Help man you were grate. :D

---

### Post by itix on 2008-12-30
Ok, I think it is best to just use hardy then.

It'll be supported until october 2012 (it's an LTS ;) ) so I'm sure that forcedeth will be updated before your version expires...

---

