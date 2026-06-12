---
title: "Linksys WPC54Gv2 doesn't work"
date: 2006-06-26
forum: Hardware &amp; Laptops
---

### Post by Arbiter on 2006-06-26
Hi all,

I just got a wireless network set up and I have a Linksys WPC54G version 2 PCMCIA card on my laptop.  I'm still a bit noobish when it comes to wireless and linux, but here's my problem.

I've used ndiswrapper already to load up the windows inf file.  Ndiswrapper tells me that the hardware is present, but when I try any iwlist commands or query the card in any way, it says its there but the "resource is not available".  The power light on the card comes on, but there's never any activity on the link light.  I know the card works because I've used it under windows for roughly a year now.  My laptop is a Sony FXA-32 900MHz Duron.

I don't know if this means anything, but I'm using Kubuntu and when I was looking around for a possible solution to the problem, I started poking around in the KDE information center and it tells me that my PCMCIA controller is not present and then when I look under my services, it says pcmcia-utils is loaded and starts at boot, but isn't running.

Any help would be greatly appreciated :D

---

### Post by nzruss on 2006-06-26
Check this link out. I had the same problem and this fixed it. 

[http://www.ubuntuforums.org/showthread.php?t=190967](http://www.ubuntuforums.org/showthread.php?t=190967)

Could be a number of thing's but most likely its the broadcom driver hogging the card, and requires blacklisting. Its not hard to get sorted, and the how-to on that link should be simple enough to follow.  Leave a post on that page if you have any prob's and i'll try to help.

---

### Post by Arbiter on 2006-06-26
I tried removing the broadcom driver, but it says its not present.  iwlist still says that the resource is temporarily unavailable.  Is there anything I can do to see what's hogging up the PCMCIA controller?

---

### Post by nzruss on 2006-06-26
How about: 

See what your card is reconised as, if you havent already: This will list all the networking information on your hardware to give you a clue as to the issue. - Note what your card is recognized as (wlan0 or eth1 etc... )

```

sudo lshw -C network 

```

Then try to see if its 'up' (make sure you replace wlan0 with whatever your wifi card is recognised as)
```

sudo ifup **wlan0** 

```

It *should* say 'already configured' or something to that effect. 

Try restarting the networking and then doing a scan 

```
sudo /etc/init.d/networking restart
sudo ifwlist **wlan0** scan

```

If that doesnt help, i'm not sure what it could be. It could be something as simple as the network manager actually using the card, but you should still be able to do a scan...

You could try 'reinstallation' (through synaptic) of your network manager...

---

### Post by Arbiter on 2006-06-27
This is getting stranger and stranger.

When I used the 'sudo ifup wlan0' it says "ignoring unknown interface", but I confirmed that the logical device name is wlan0.

Then when I try the 'sudo /etc/init.d/network restart' command, it tells me that the command is not found.

I'm at a total loss here.  :-k

---

### Post by nzruss on 2006-06-27
ok, how about:

```
 sudo lshw -C network 

and 

sudo ls /etc/init.d/

and 

sudo cat /etc/network/interfaces


``` 

that should list the hardware and all your network interfaces.

paste what you get back here, and we'll continue trying



(i'm no expert BTW... i'm still stuck with a wifi issue myself)

---

### Post by imagineer on 2006-06-27
[QUOTE=Arbiter]This is getting stranger and stranger.
Then when I try the 'sudo /etc/init.d/network restart' command, it tells me that the command is not found.
[/QUOTE]

In Ubuntu the command is networkING...   I haven't yet found the ifwlist equivalent.

so the command line should read.

sudo /etc/init.d/networking restart

Trying to get my Linksys WPC54G working also.  ](*,) 

Mark

---

### Post by nzruss on 2006-06-28
Ah yes, sorry. - changed my post incase anyone else tries it.. 

again. sorry.

---

