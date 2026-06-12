---
title: "Intel Ethernet 82557/8/9 &quot;e100&quot; Problem"
date: 2006-04-05
forum: Hardware &amp; Laptops
---

### Post by muraii on 2006-04-05
Hi,

I may have put a request in the wrong forum, so I'm throwing it here.  Rather than repost everything, let me link to [what I've already written]("http://ubuntuforums.org/showthread.php?t=155236").

Again, if anyone can help, I'd greatly appreciate it.

---

### Post by muraii on 2006-04-06
Well, since there don't seem to be any other folks with this problem, as evidenced by the absence of replies, I'm not sure how helpful this will be to the Ubuntu community.  But, anyway....

(1)  I have installed with the "linux noapic nolapic" option.
(2)  I have checked my cables.
(3)  I have checked the port on my router.
(4)  I have disabled IPv6 in Ubuntu.
(5)  I have made a DOS boot floppy, put IBAUtil.exe on there, and disabled the Intel Boot Agent for the Intel Ethernet Pro card.
(6)  I have found that the module for this card--e100--is listed in the output of lsmod.
(7)  I have tried to ensure initiation of the e100 module with "modprobe e100".
(8)  I have activated the card several times from within Gnome, watching it think for two or three minutes before finally calling eth0 active.
(9)  I get a light on the router letting me know it sees *something* connected to its port, though it doesn't list my system in the DHCP log.
(10)  I have used dhclient to attempt an initiation of DHCP communication.
(11)  I have scoured the forums, Usenet, and the general internet for whatever I can find to help.
(12)  I have posted now four times here.
(13)  I have talked to an experienced Debian admin and user at work.
(14)  I have lost patience.

Sure, there's a certain Zen peace to be found in a system disconnected from the hustle and bustle of the net; but I think I'd like the option to jump out and apt-get some stuff to use on this machine.  Therefore, I'm getting another card, and hopefully all is well.  I hope anything I've posted here will be helpful for someone else.

Daniel

---

### Post by FarEast on 2006-04-06
I have a loptop(Thinkpad 390X) with a NIC which is driven by e100 module.  And I did not have to do anything to configure it manually.
What I'm wondering are:
> When I click "Activate" in the network utilities dialog in Gnome, the system
> thinks for a while (a minute or two) and then shows eth0 to be active.

It is too long...

> Link encap:Ethernet  HWaddr  00:90:27:EB:BA:22
> BROADCAST MULTICAST  MTU:1500 Metric:1
> RX packets:0 errors:0 dropped:0 overruns:0 frame:0
> TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
> collisions:0 txqueuelen:100
> RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)

The output shows that your machine has not got an IP address, for it does not contain the information of it.

If you like, please paste the content of /etc/network/interfaces .

---

### Post by muraii on 2006-04-06
[QUOTE=FarEast]
> When I click "Activate" in the network utilities dialog in Gnome, the system
> thinks for a while (a minute or two) and then shows eth0 to be active.

It is too long...
[/QUOTE]

Yeah, I assumed as much.  It should either work or not.

[QUOTE=FarEast]
> Link encap:Ethernet  HWaddr  00:90:27:EB:BA:22
> BROADCAST MULTICAST  MTU:1500 Metric:1
> RX packets:0 errors:0 dropped:0 overruns:0 frame:0
> TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
> collisions:0 txqueuelen:100
> RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)

The output shows that your machine has not got an IP address, for it does not contain the information of it.
[/QUOTE]

Yeah, I noticed that, too.  Even l0 has an address (127.0.0.1, of course).  I had thought that might've been the router not talking correctly to the card, but I use that port on a Windows laptop without issue.

[QUOTE=FarEast]If you like, please paste the content of /etc/network/interfaces .[/QUOTE]

I certainly will when I get home.  I looked through it last night and it appeared (to my limited understanding) to be fine.

Thank you.

---

### Post by muraii on 2006-04-06
It occurs to me that I might have been defeating myself all along.  I have the fairly common problem that the system hangs at boot up on "Starting hotplug subsystem".  I had read that I could speed up the system load (or let it load at all), and had also read that disabling the hotplug subsystem affected not only USB and other hot-swappable stuff, but networking as well (being hot-swappable as well).

Have I just been kicking myself in the face by hitting CTRL + C at boot, and then expecting networking to work?  Will it help at all if I just let it try to get past the hotplug subsystem start without my intervention?  Maybe I should at least try.

Holy crap.

---

### Post by muraii on 2006-04-06
I figured out the problem: the NIC I had blew.  I bought a $10 USR NIC, installed it, and turned the machine on.  I didn't have to apt-get anything, use Synaptic, load the CD that came with the NIC, or anything.  I booted, logged in, and started farting around with repositories and Yahoo! Mail.

I learned quite a bit from this, having run through all the forums and Usenet and googling the crap outta the web.  I might not have done that much if everything had worked, so I'm a better Linux user for it.

Cheers.

---

### Post by FarEast on 2006-04-07
> I might not have done that much if everything had worked,
> so I'm a better Linux user for it.

I think that it is 'pleasure' of using Linux;) .
Let's enjoy Linux life!!

---

