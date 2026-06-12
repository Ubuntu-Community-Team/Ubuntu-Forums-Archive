---
title: "Help me NOT put XP on my Wifes Thinkpad. :)"
date: 2005-11-06
forum: Hardware &amp; Laptops
---

### Post by MetalMusicAddict on 2005-11-06
My wifes Thinkpad 600e finally died. Was a great laptop. Some used **A21m**s for $300 came up for sale at my work. I got one because of their supposed great compatabillity with linux. Most things seem to work but Im still not sure.

_Stats_:
PIII 800MHz
14" screen
ATI video card
20gig HD
128megs RAM (gonna up this)
DVD-ROM
Onboard NIC/Modem
USB1

Not bad for the wife. ;)

OK. So heres the problem. Neither the onboard NIC nor the **Linksys WPC11** work. I have seen many threads on the **WPC11** but I still cant seem to get whats going on. Im not even sure what version it is.

Heres a pic of the back:
[[IMG]http://img493.imageshack.us/img493/2161/dscf17625qq.th.jpg[/IMG]](http://img493.imageshack.us/img493/2161/dscf17625qq.jpg)

So what commands do you need outputs from?
lsmod?
lspci?

Also this Thinkpad has a ATI GFX card in it. In the xorg what should the driver be? ATI? Should I try to install new ATI drivers? 

Any help is **TOTALLY** appreciated.

---

### Post by dbott67 on 2005-11-06
There's a good HOWTO on using ndiswrapper to get your NICs working.  You just need to find the Windows driver (either from the Linksys install CD or their website).

[https://wiki.ubuntu.com/SetupNdiswrapperHowto](https://wiki.ubuntu.com/SetupNdiswrapperHowto)

-Dave

---

### Post by MetalMusicAddict on 2005-11-06
Problem is Ubuntu seems to detect it fine on install. Lets me config it and everything. Just doesnt connect. No signal strenght. Ide rather use the native driver than ndiswrapper if possiable. I would also like to get the onboard NIC goin.

I do also get a beeping when I have the wireless card in the PCMCIA slot on boot.

---

### Post by TimelessRogue on 2005-11-06
Hey, I'm using a Linksys WPC11 Ver3 and had the same problem.  Since it was a fresh, virgin install I reinstalled with the card inserted and IN THE PRESENCE of a wifi connection (my local Simple Coffeeworks ... nice double latte and a scone got me through it all).  Presto!  All was well and working.  Bu it sounds like that's not your problem.

You may have to go into System/Administration/Networking and activate the connection ... just in case you haven't already done that.

Let us know ...

---

### Post by gw90se on 2005-11-06
[This](http://lxer.com/module/newswire/view/46385/) is the only way I finally got mine to work.

---

### Post by MetalMusicAddict on 2005-11-06
[QUOTE=TimelessRogue]Hey, I'm using a Linksys WPC11 Ver3 and had the same problem.  Since it was a fresh, virgin install I reinstalled with the card inserted and IN THE PRESENCE of a wifi connection (my local Simple Coffeeworks ... nice double latte and a scone got me through it all).  Presto!  All was well and working.  Bu it sounds like that's not your problem.

You may have to go into System/Administration/Networking and activate the connection ... just in case you haven't already done that.

Let us know ...[/QUOTE]
"IN THE PRESENCE of a wifi connection" is something Im unsure of because I dont broadcast it the SSID on my router. I know the SSID and passphrase for my router and I just input it. I figured if I point it to where it needs to go it shouldnt matter if its broadcasted.

---

### Post by TimelessRogue on 2005-11-06
What I meant by that was that (and I should have been more explanatory) was that I found that when I installed Breezy while I was at a wifi location with the WPC11 inserted, Breezy automaticly installed my card, detected the wifi connection and accessed the internet.  My previous install attempt was at home  with both DSL and wireless plugged in but no wifi available and Breezyfound/used the DSL connection but DID NOT install the WPC11 ... for what reason, I don't know.

What I DO know is I fiddled and tweaked to get wireless working per forum advice with no luck, then decided to take this on with the idea of finding the absolutely simplest, least complicated method of setting up wireless during the initial Breezy installation ... a method that would work for the newest of newbies.  I wasn't even sure it would work, but it did and that's all I can tell you ...

But like I said, it sounds as if that's not your problem anyway 'cause you said that the system has already recognized and installed your card.  I have seen some references here to problems related to using WEP.  Did you say you are using WEP and could that be your problem?

---

### Post by MetalMusicAddict on 2005-11-07
I actually got the wifi working. :) It wasnt the card. It was the router (kinda). I dont broadcast my SSID for security reasons. Every other wificard I use works fine this way except this one in linux. I dont want to leave it broadcasting.

Anyone know how to let it connect without having to broadcast the SSID?

---

### Post by daller on 2005-11-07
[QUOTE=MetalMusicAddict]I actually got the wifi working. :) It wasnt the card. It was the router (kinda). I dont broadcast my SSID for security reasons. Every other wificard I use works fine this way except this one in linux. I dont want to leave it broadcasting.

Anyone know how to let it connect without having to broadcast the SSID?[/QUOTE]

How do you connect?

modified your /etc/network/interfaces ???

Find out the Wireless NIC interface!

Go to a console, and type:

iwconfig

The output will tell you which interface is the one...

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"IBCWLAN"  Nickname:"ipw2100"
          Mode:Managed  Frequency:2.417 GHz  Access Point: 00:02:2D:52:9A:04
          Bit Rate=11 Mb/s   Tx-Power:off
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=80/100  Signal level=-78 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:111   Missed beacon:6

sit0      no wireless extensions.

...Here it's "eth1" so i'll use that in my example...


Insert this in /etc/network/interfaces:

iface eth1 inet dhcp
wireless-essid YOUR_SSID
wireless-key 01010101010101010101010101

Then run this, to connect:

sudo ifup eth1

...Please show me the output...

---

### Post by MetalMusicAddict on 2005-11-07
[QUOTE=daller]
Insert this in /etc/network/interfaces:

iface eth1 inet dhcp
wireless-essid YOUR_SSID
wireless-key 01010101010101010101010101[/QUOTE]
Ill give you the output but my "interfaces" is configured. ;) If you look at my post before this my problem now is that I *have* to broadcast my SSID from my router. I dont want to for security. Also my onboard NIC doesnt work.

---

### Post by daller on 2005-11-07
[QUOTE=MetalMusicAddict]Ill give you the output but my "interfaces" is configured. ;) If you look at my post before this my problem now is that I *have* to broadcast my SSID from my router. I dont want to for security. Also my onboard NIC doesnt work.[/QUOTE]

Well, the setup may be issue...

This will NOT work on a cloaked network:

iface eth1 inet dhcp
wireless-essid any

This will probably work:

iface eth1 inet dhcp
wireless-essid THE_SSID

...Cheers!

---

### Post by varunus on 2005-11-07
Try opening up a terminal, and typing:
```

sudo iwconfig eth1 essid YOUR_SSID

```
where eth1 is your network card interface name.

```
sudo iwconfig eth1 key YOUR_WEP_KEY
```

Then type

```
sudo dhclient eth1
```

That's the terminal way to set this up...hopefully it works for you.

You may also want to file a bug with the GNOME people if their applet doesn't let you connect to a non-broadcast SSID.

---

### Post by daller on 2005-11-07
Varunus> What does "sudo dhclient eth1" do?

---

### Post by mips on 2005-11-07
Have a look at  [http://ubuntuforums.org/showthread.php?t=77380&highlight=WPC11](http://ubuntuforums.org/showthread.php?t=77380&highlight=WPC11)
and **post5** in this thread  [http://ubuntuforums.org/showthread.php?t=4200&highlight=WPC11](http://ubuntuforums.org/showthread.php?t=4200&highlight=WPC11)

---

### Post by MetalMusicAddict on 2005-11-07
Heres what the wireless section of interfaces looks like with paranoid stuff removed:

```
iface eth0 inet static
address ***.***.***.***
netmask ***.***.***.***
gateway ***.***.***.***
wireless-essid *********
wireless-key ************************ (key is in hex)

auto eth0
```
Everything is there. This works fine for my broadcom/ndiswrapper setup on my Dell. For this card should there be another line that tells it to look for something?
I would really rather not have my router broadcast its SSID but this is the only way this card seems to work? Am I wrong?

Let me say again, Im not trying to do this with ndiswrapper.

---

### Post by varunus on 2005-11-09
The command "sudo dhclient eth1" uses DHCP (automatic IP address assignment) to get an IP address from your router.  Don't do it if you're using static IP addresses.  Instead, you'll have to use some "ifconfig" commands (you can use "man ifconfig" to read about them in the manuals, or i can post them up here if you need a quick fix.)

I'm pretty sure you can connect to non-broadcast SSIDs with some cards...did entering the commands not work?  I think it'd be easier to work on /etc/network/interfaces after you know that it works with just issuing commands to the card.

There are other options aside from hiding the SSID too, if it turns out not to work.  (For one, you could just ndiswrapper on this computer, as ndiswrapper works with most native cards too.)  You can also use MAC address filtering on the router so that only certain computers are allowed to connect even if the SSID is broadcast.  That might be a good workaround...

Sorry you're having so many issues.

---

### Post by MetalMusicAddict on 2005-11-09
Can this card be *made* to see a router that isnt broadcasting its SSID? That seems to be the only issue with the wireless.

Also Im having a video driver issue. The Thinkpad has a ATI GFX card in it. In the xorg what should the driver be? ATI? Should I try to install new ATI drivers?

---

### Post by varunus on 2005-11-09
You should use the official ATI drivers (Catalyst) just like on a windows PC.  The ones bundled with xorg, like the ones bundled with windows, work for 2D but not as well for 3D.

Install it through synaptic (its called the fglrx driver).  Here's a howto:
[http://ubuntuforums.org/showthread.php?p=408111](http://ubuntuforums.org/showthread.php?p=408111)

This is not the most up to date version, but its not bad at all.  If you want the newest version, go here:
[http://ubuntuforums.org/showthread.php?p=423589](http://ubuntuforums.org/showthread.php?p=423589)
This is not recommended unless you're having the widescreen not working bug with your laptop.

---

### Post by MetalMusicAddict on 2005-11-09
Thanx varunus. ;)

---

