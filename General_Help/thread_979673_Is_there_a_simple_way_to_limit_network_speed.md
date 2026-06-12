---
title: "Is there a simple way to limit network speed?"
date: 2008-11-12
forum: General Help
---

### Post by Cadmus on 2008-11-12
Bit of an odd one this, but I hope there's a straightforward solution.

Is there a way to limit the bandwidth available to a network interface? Preferably using built-in commands?

The reason I'm asking is I want to test some software over long-distance networking, and it would be a lot easier if I could build some virtual machines, then just throttle their interfaces to internet speeds.

I'm using VirtualboxOSE for the virtual machines if there's an option there that will do what I want.

---

### Post by The Cog on 2008-11-12
tc is the Linux Traffic Control program. It's not simple though.
[http://lartc.org/](http://lartc.org/)
I'be never tried traffic control so don't know what the full capabilities are. However, don't forget that possibly the biggest difference to your software's behaviour will be because of the longer round-trip-time rather than because of the bandwidth limits. I'm not sure if tc can emulate network latency.

---

### Post by Rhubarb on 2008-11-12
After doing a quick search in synaptic, here are 2 results that look promising:

**iprelay**
> User-space bandwidth shaping TCP proxy daemon
iprelay can shape the TCP traffic forwarded through it to a specified
bandwidth and allow this bandwidth to be changed on-the-fly. Multiple
data streams to different sockets may be shaped to the same total
bandwidth, much like a traffic shaping router would. However, this
application runs in user space, and works by acting as a TCP proxy.

Here's what the author would like you to know: ip_relay sprang from
the fact that I use a modem for home Internet connectivity, and once
a large download has started, other Internet activities: telnet,
surfing, VOIP, are largely useless. With ip_relay, you can suddenly
decide to shape your downloads to 50% of your available bandwidth,
and make use of the more interactive applications.

After using ip_relay for a while, it became obvious to me that it had
another use: simulating bandwidth limits for other applications. Most
notably was testing VNC over an ethernet connection, but at modem
speeds.

The original software is called ip_relay
([http://www.stewart.com.au/ip_relay/](http://www.stewart.com.au/ip_relay/)) but its name has been changed
according to Debian policy.

**shaperd**
> Shaperd is a user-mode program that can shape traffic passing through
a Linux box. As it runs as a normal daemon, some kind of packet-forwarding
mechanism is needed. This can be done with the BSD divert sockets patch
for Linux 2.2, or with netfilter's built-in libipq under Linux 2.4.

---

### Post by loell on 2008-11-12
[http://www.ubuntugeek.com/use-bandwidth-shapers-wondershaper-or-trickle-to-limit-internet-connection-speed.html]("http://www.ubuntugeek.com/use-bandwidth-shapers-wondershaper-or-trickle-to-limit-internet-connection-speed.html")

---

### Post by Rhubarb on 2008-11-12
Thanks loell,
**trickle** is the other app that I forgot to mention there, I've used it before, it works very well for TCP.

---

### Post by loell on 2008-11-12
no problem, hadn't i scan ubuntugeek's tutorial, i wouldn't have known trickle either. i only knew shaper**d**.

---

### Post by Cadmus on 2008-11-12
Thanks for the fast replies, trickle looks like it might be what I'm after. You make a good point about latency though, I'll take a bit more of a look to see if I can introduce that.

---

### Post by binbash on 2008-11-12
+1 for trickle

---

### Post by Cadmus on 2008-11-14
Hmm, for more complex network management there's [this]("http://www.linuxfoundation.org/en/Net:Netem") which seems to be able to perform fairly complex network manipulation.

From what I've read on /. and the like people tend to use it on a mini-box between real machines in more real-world tests. Having such a machine though would be damn handy at times.

---

### Post by Zhukov on 2008-11-14
TC is much of an overwight :/ If I were you, I would avoid it for small purpouses.

Best regards!

---

### Post by Cadmus on 2008-11-14
You're right, for what I'm doing it's probably a bit heavy, but why think small for the future :) I've got a few plans for network devices and tc could be damn handy later.

---

### Post by Zhukov on 2008-11-16
lol, ok then

Just one advice, understand how tc works before doing some confs.

It may save you a lot of time =)

Also, check this out, since you are into learning new stuff:

[http://opalsoft.net/qos/DS.htm](http://opalsoft.net/qos/DS.htm)
[http://l7-filter.sourceforge.net/](http://l7-filter.sourceforge.net/)

---

### Post by Tomab on 2008-11-26
I've found a really _simple_ way do limit your speed in Ubuntu.


The program I found is called 'wondershaper'
```

sudo apt-get install wondershaper

```



Then after the install, i executed this:
```

sudo wondershaper <ethernet> <max kilobit down> <max kilobit up>

```



For example, if you want to limit your speed to **500** kilobyte down/**50** kilobyte up:
Calculate **500***8 = **4000** kbit.
Calculate **50***8 = **400** kbit.
(Remember: 8 bit in 1 Byte)

Then run this:
```

sudo wondershaper <ethernet> **4000** **400**

```

Make sure to replace <ethernet> with your network adapters name (e.g. eth0)



I use this because my internet vendors line in to me are really no good, I have to limit my speed to 990/90,
or else if my speed goes above 1000 or 1100, my internet line stops.

---

