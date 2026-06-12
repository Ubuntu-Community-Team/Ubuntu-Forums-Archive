---
title: "Static ip in Ibex"
date: 2008-11-09
forum: General Help
---

### Post by gvanto on 2008-11-09
I've just installed Intrepid Ibex and gotta say, very impressed with the slick looks! I recently purchased a static IP from our ISP and now need to set this up in ibex, however I have read a couple of places that setting up a static ip on ibex is very hard, if not impossible:

[http://digg.com/linux_unix/Ubuntu_8_10_Intrepid_Ibex_Review_Tutorial]("http://digg.com/linux_unix/Ubuntu_8_10_Intrepid_Ibex_Review_Tutorial")
(search for 'static ip' to see review by robvdl ) 

I was wondering if this is truely so hard and whether perhaps a good tutorial exists for setting a static IP up in Ibex?

Help much appreciated
Gerry
static-ip, ibex newbie

---

### Post by mlissner on 2008-11-09
I think you're confusing your internal IP with your external IP. I believe that if you purchased a static IP from your ISP, you will need to set that up on the modem from your ISP. 

The difference (as I understand it) is that internal IP's are used internally between you, your router/switch/etc, and external IP's are the ones that every server has in order to be findable.

---

### Post by Iowan on 2008-11-09
I don't run 8.10 yet, but some threads suggest that manual network configuration (static IP address in particular) is a problem due to a bug in Network Manager. [This]("http://ubuntuforums.org/showthread.php?t=975658") thread reports success, though.

---

### Post by mlissner on 2008-11-09
Although I don't think it's what gvanto is after, I've had good success with 8.10 and static IP (internal) addresses over wireless.

---

### Post by fatphilthethird on 2008-11-10
An external static IP will need to be set up through your router, not using the internal ubuntu network manager.

Fat

---

### Post by gvanto on 2008-11-11
Hey guys,

Thanks for responses.

I'm quite a network newbie so my knowledge of how to set this all up is a bit limited.

I would like the static IP address to appear to the outside world in such a way that I can ssh into my machine at home from anywhere  (and possibly use it as a webserver later, etc). The article below is pretty good, but it uses the dyndns (or similar) service, which I will not require (I think?) since I have a static IP given to us by the ISP.
[http://www.thinkdigit.com/forum/showthread.php?t=95175]("http://www.thinkdigit.com/forum/showthread.php?t=95175")

I am not sure how an internal static address comes into this? Is it required?

Any advice on how to go about this would be greatly appreciated.

I haven't managed to find a good howto on setting up an (external)
static ip configuration from Kubuntu (Hardy Heron - I've downgraded from Ibex for now, as I'm just more used to it)

Many thanks for any advice!
Gerry
Static Ip newbie!

---

### Post by Iowan on 2008-11-11
A bit more explanation of your network might he helpful.  Is this machine connected directly to internet, or is there a modem/router (DHCP device) in between?  Reason for asking: you might have several clients besides server sharing that one static address if the static address is assigned to a NATing router.  As mentioned (mlissner) the machine's address could be assigned by a DHCP server (even if it is a static lease - based on MAC address).  Although this is probably causing more confusion than help, you have lots of options we'd love to help you consider :)

---

### Post by Slim Odds on 2008-11-11
Most people have a router/modem that connects them to their ISP. This device must be told how to connect. One of the things that is needs to know is how to obtain an IP address.

You need to tell the router that your address is static and what it is.

Most of these devices also act as a firewall to isolate your computer(s) from direct access from the outside world. There is typically a setup in the router to allow selected ports to be forwarded to a computer behind the firewall.

There is also usually a way to allow a computer to be designated as the "DMZ" meaning that it's outside the firewall. I wouldn't recommend that as you have to be MUCH more careful about how you set that machine up.

---

### Post by gvanto on 2008-11-11
hey guys thanks alot, appreciate the help.

I have the following setup:
- PC running Hardy
- a ADSL modem/router connecting to the internet
- PC is connected to router directly with ethernet cable

Furthermore we have 2 laptops connecting wirelessly to the modem/router.

I have an IP address the ISP (iinet in sydney, au) has given me, which is the static IP - say I haven't actually tried it but perhaps its already static each time I connect :-) 

What I would like to do is set up the port-forwarding so it connects to the appropriate PC behind the router (looking in, from the outside world)

So I'm guessing I need to configure Kubuntu and/or the modem/router somehow with DHCP and whatnot, and this will allow ssh-ing into each machine from the outside world.

Only what settings to fiddle with in NetworkManager and whatnot, I have no idea - a tutorial covering basic Network 101 and setting up a static ip on kubuntu would be pretty good ?  (thanks alot for all the help on here so far)

many thanks
Gerry

---

### Post by mlissner on 2008-11-11
The general technique to configure the router/modem to have a specific IP address (this is the external one, which you will use to access the computer for ssh, etc). Once that's set, you need to set up your computer to connect to the router/modem on a certain internal IP address. If you use DHCP, you will end up with a different internal IP each time you connect, which is bad. 

The reason that is bad is because the next step to accessing your computer is to forward certain ports from the router/modem to the computer, and the way you do that is by creating rules on the modem/router such as "forward port 80 to ip address 192.168.1.50" (that would forward web requests to the correct computer, assuming it's at that internal address).

So, to recap:
1. Set up the modem/router to connect to the internet. Talk to your ISP about getting that done.
2. Set up the modem/router to forward certain ports to your server computer.
3. Set up the server computer to do interesting things (such as serve web content or SSH) when those ports are accessed.
4. Set up your server computer to be at a certain internal static IP address so the forwarded ports know where to find it.

The one other thing I should mention here is that if you do use DYNDNS, you might be able to save some money. What that does is allow you to have a dynamic external IP address such that whenever it changes, a daemon on your computer updates DNS information on the web. That way, when you want to access the computer, you type in yourcomputer.dyndns.com (or similar), the IP address is figured out by DYNDNS, and then you find your computer, even though the IP may have changed since the last time you went looking for it. The advantage here is that external static IP's are usually expensive, and you can dispose of them, if you wish. One other consideration is that if you are going to send email from your computer (as an email server), you may have issues with dynamic external IP addresses getting rejected by spam filters.

Hope this all helps. I went through a similar learning curve myself not too long ago.

---

### Post by gvanto on 2008-11-12
thanks for a very helpful response mlissner, this really does explain 
how the internal DHCP thing comes into it (this was puzzling me)

thanks a million!!

gerry

---

### Post by mlissner on 2008-11-12
No prob. It's a complicated thing with a lot of interconnected pieces. Glad to help.

---

### Post by gvanto on 2008-11-12
I've found a good article on this IP stuff at linuxhomenetworking.com , so gonna train myself up a little - I need it!

Thanks again for all the help, I'll keep my progress posted on here

Already have the static ip from the ISP, so looking forward to my little home server !

Gerry

---

