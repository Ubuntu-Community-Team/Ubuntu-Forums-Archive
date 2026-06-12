---
title: "run ethernet from wireless from my laptop"
date: 2015-04-26
forum: Hardware
---

### Post by beelzebufo on 2015-04-26
I have been trying this for months, I can connect, but the problem is that the unit (it's a bitcoin miner) has no screen so I need to get into it through the ethernet caple to make my settings, it also has a statid address of 192.168.1.98 or 192.168.0.99 can't remember which, but the ethernet address is 10.1.22.2 or something like that, on the laptop so they don't want to communicate. How can I change the ethernet address to 192.168.1-255 so that it will connect? I know it can be done using the dhcp connections, but i would like some guidance before I make it so I have no internet. i am running a dell leptop on ubuntugnome, and the btc miner is an anminer s3. ANY Help would be greatly appreciated. Oh I have the ipv4 settings to shared, I think I have everything the way it needs to be, I just need the btc miner to connect to it's static address.  The address for the wireless is something like 192.174.1.1-255

Thanks in advance
beelebufo

also, I am not sure this is in the right place, if a mod sees this and thinks I may have better luck, please move it. I am losing 30 bucks a month (not much I know, but it's something)

---

### Post by TheFu on 2015-04-26
The normal way to connect to a headless server is through ssh.  The server must already be running openssh-server or you won't get far.

Also, you need to absolutely KNOW the IP address for the server to which you want to connect. There isn't any other option. If you don't know, you need to figure it out.  Perhaps a subnet port scan would be helpful?

Lastly, 192.174.1.1-255 are public, route-able  IP addresses. I HOPE either you are mistaken or the IP used was provided by a network admin. If you just made this up, bad.

It is unclear from here how well you understand networking.  A primer can be found at grc.com/sn - episode 25 is what you want, if you need it.

---

### Post by beelzebufo on 2015-04-26
you are missing the point and you didn't read my post.  my wireless address is 172.16.2.241 so I was mistaken, I do understand networking probably as well as you do, I have the address for the unit, I have not tried ssh yet, just hadn't thought of it.  I am sorry if you are in a bad mood, but condescention isn't the way to make you feel better.  If you would like to talk about it, I am a counselor so please feel free to message me on here.    Also, my question was "[COLOR=#000000]How can I change the ethernet address to 192.168.1-255 so that it will connect"  But I will try the ssh route, maybe that will work, hopefully it does.  Next time, read the post before you try to lay into someone.  This time it backfired.[/COLOR]

---

### Post by TheFu on 2015-04-26
> **beelzebufo said:**
> you are missing the point and you didn't read my post.  my wireless address is 172.16.2.241 so I was mistaken, I do understand networking probably as well as you do, I have the address for the unit, I have not tried ssh yet, just hadn't thought of it.  I am sorry if you are in a bad mood, but condescention isn't the way to make you feel better.  If you would like to talk about it, I am a counselor so please feel free to message me on here.    Also, my question was "[COLOR=#000000]How can I change the ethernet address to 192.168.1-255 so that it will connect"  But I will try the ssh route, maybe that will work, hopefully it does.  Next time, read the post before you try to lay into someone.  This time it backfired.[/COLOR]

I read your post, carefully, 3 times, before replying.  Perhaps I'm just stupid and couldn't figure out what you wanted from all the inconsistent data?
I am sorry for my stupidity and that I don't think like you do. Something must be lost in translation - .... "It is unclear ... if you need it." That doesn't say you don't know networking, just that it is unclear to me.  

I'm actually having an excellent day.

Anyway, perhaps these links will help?
* [http://ubuntuguide.org/](http://ubuntuguide.org/)
* [https://help.ubuntu.com/lts/serverguide/](https://help.ubuntu.com/lts/serverguide/)

Good day.

---

### Post by beelzebufo on 2015-04-26
Thank you the fu, but no, you didn't understand what I was trying to ask at all, I thought I was pretty clear, here, I will make it easy, how do I change my ethernet OUT ip address to 192.168.1.98.  Is that possible?  And no, you are not stupid, something must have been lost in translation.  Is english your first language?

---

### Post by beelzebufo on 2015-04-26
also, will ssh work if I am running straight from the laptop to the unit?  I thought you had to be part of a full network for that to work, I suppose to units connected is a network, but.. yeah

---

### Post by beelzebufo on 2015-04-26
ssh didn't work either, I just need to figure out a way to get my ethernet coming out of my computer to share it's internet connection with my minerd dag nabbit.

---

