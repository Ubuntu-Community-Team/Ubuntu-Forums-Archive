---
title: "intrepid ibex ate my internet"
date: 2008-10-31
forum: General Help
---

### Post by LodeRunner on 2008-10-31
Wish I could be more precise then that but, um, there ya go. I upgraded from Hardy (distro upgrade from the update manager), and now I'm screwed.

Network Manager doesn't list wired OR wireless connections anymore. I thought my wired was a restricted Broadcom driver... I no longer see that listed, so that could be a clue as to why the wired no longer works. However, the wireless driver is NDIS; I've verified that it's loaded and working. WiFi Radar is as blank as Network Manager. ifconfig shows eth0, loopback and pan0 (which I've never seen before.) ifup eth0 gives unknown interface. ifconfig up eth0 returns a prompt, but internet still does not work.

I'm using a Dell Vostro 1500, with the a-b-g-n-everything card.

I'm not one to idly complain, but I've been a user since Hoary and I have to say this is REALLY unacceptable.  Bugs are understandable, but the Internet is EVERYTHING... it's the main purpose of most computers nowadays, and it helps you fix any other Ubuntu problems that might arise.  New releases, LTS or not, should not kill internet, *period*. Extreme measures should be taken: backups should be made, revert options should be offered... and so on.

Back to the matter at hand... can anyone help me? I really don't have time for a full reinstall right now...

---

### Post by cariboo on 2008-10-31
So are you just complaining, or do you need help. We need more information then the make and model of the computer and this:

> a-b-g-n-everything card.


Could you paste the output of:

```
sudo lshw -C network
```

In your next post.

Jim

---

### Post by Yellow Pasque on 2008-10-31
Please give us some info to work with. Post output of:
```
sudo lshw -C network
cat /etc/network/interfaces
iwconfig
```

---

### Post by LodeRunner on 2008-10-31
Fortunately for me, I'm a not-completely-incompetent touch typist (even more fortunately, I have more than one computer):
```

*-network
description: Network Controller
Product: BCM4320 802.11a/b/g/n
Vendor: Broadcom Corporation
physical id: 0
bus info: pci@000:0c:00.0
version: 03
...
capabilities: pm msi pciexpress bus_master cap_list
configuration: driver=b43-pci-bridge latency=0 module=ssb

*-network
description: Ethernet interface
product: BCM4401-B0 100Base-TX
vendor: Broadcom Corporation
physical id: 0
bus info: pci@000:03:00.0
logical name: eth0
version 02
serial: blah mac
size: 10MB/s
capacity: 100MB/s
...
capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10MB/s

*-network DISABLED
description: Ethernet interface
physical id:2
logical name: pan0
serial: macity mac, blah
capabilities: ethernet physical
configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

---

### Post by LodeRunner on 2008-10-31
iwconfig: no wireless extensions for lo, eth0, or pan0

cat /etc/network/interfaces

auto lo
iface lo inet loopback


And again, lsmod and ndiswrapper -l have confirmed that the wireless driver is loaded just fine.

---

### Post by LodeRunner on 2008-10-31
Sorry if the minirant put you off, but I do think that a complete, irreversible, simultaneous breakage of both wired AND wireless internet from a non-beta release does merit a rant. I gave much more than the model of my computer in the first post, I'll do whatever other legwork you think might help, and in the end I'll thank you profusely if it works (somewhat less profusely if it doesn't.) I don't generally waste time with upfront pleasantries when my main workhorse is completely useless, though. If I don't get this thing fixed, I can't do my schoolwork. Worst comes to worse I can reinstall everything and twiddle it back the way I'm used to, but that's 7+ hours I just don't have right now.  Mother****ing calc 2 exam next week...

---

### Post by cariboo on 2008-10-31
Are you running any virtulization software? Because it looks like eth0 is bridged. If you are, try changing the network interface to nat to see if that solves your problem.

Jim

---

### Post by LodeRunner on 2008-10-31
> **cariboo907 said:**
> Are you running any virtulization software? Because it looks like eth0 is bridged. If you are, try changing the network interface to nat to see if that solves your problem.

Jim


Not that I can recall.  However, it has just occurred to me that I haven't used my wired connection in a long time... maybe not since Feisty. So, it's possible that it's been broken for a long time and I just haven't noticed. I'm sure that wired worked in Feisty, though, and I'm 110% sure that Intrepid killed the wireless.

What kind of software should I be looking for?  I do vaguely recall tinkering with OpenVPN a while back, but synaptic confirms it isn't currently installed. Left-clicking on the network manager tray icon shows a grayed-out "Disconnect VPN" option.

Or wait, by "virtualization" you didn't mean something like QEMU or Wine or Dosbox...?

EDIT: For the wired, it's entirely possible my friend did something while I wasn't looking. He's an ex-Gentoo guy... has a tendency to do all manner of crap to my computers when I'm not looking, all for my own good.

So, what should I be looking for?

---

### Post by LodeRunner on 2008-10-31
Bumpity bump bump.

---

### Post by LodeRunner on 2008-10-31
bump. nontrivial issue here damnit. IBEX KILLED MY INTERNET. 100% sure it's responsible for killing my wireless, maybe 70% sure it killed my wired.

ndiswrapper is modprobbed.  ndiswrapper -l confirms that the driver is loaded, but I don't have a wlan0.

---

### Post by LodeRunner on 2008-10-31
Thanks for the "help"... 

Solution is HERE:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Hardy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Hardy)

And it only took me 18 hours to find.

---

### Post by LodeRunner on 2008-11-01
Seriously, I thought crazy South African dude paid you guys to help out the forum noobs?

Either you're not getting paid enough, or there needs to be some firing.

---

