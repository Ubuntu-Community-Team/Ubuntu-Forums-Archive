---
title: "Realtek RTL8168C(P)/8111C(P) works whenever it feels like it!"
date: 2008-09-07
forum: Hardware
---

### Post by riahc3 on 2008-09-07
Hey

I have a problem that the Realtek RTL8168C(P)/8111C(P) on my laptop works whenever it wants. Sometimes internet works, sometimes it doesnt. Is there a driver update or something that I can do to make it work?

---

### Post by Crafty Kisses on 2008-09-07
You may diagnose these network settings by activating and deactivating the wireless network interface from the Terminal, which shows some diagnostic messages:
```

sudo ifdown wlan0
sudo ifup wlan0
```

You may diagnose the network adapter status with commands:

```
ifconfig
iwconfig
dmesg
tail /etc/var/messages

```

I also want to see the results of this command:```
lshw -C network
```

I'm thinking it could also be packet loss, it certainly sounds like it.

Packet loss can be caused by a number of factors, including signal degradation over the network medium, oversaturated network links, corrupted packets rejected in-transit, faulty networking hardware, maligned system drivers or network applications, or normal routing routines.

Some network transport protocols such as TCP provide for reliable delivery of packets. In the event of packet loss, the receiver asks for retransmission or the sender automatically resends any segments that have not been acknowledged.

You might want to check if there is any interference with like a phone or a microwave or even possibly a lamp. I know it sounds stupid but my lamp for some reason was causing some interference with my router, that can all lead to packet loss.

For the driver update, you can see if there is a newer .inf file out or something to that nature and install it using **ndiswrapper.**

---

### Post by riahc3 on 2008-09-07
Its a wired connection, not a wireless. Wireless has never worked. We'll leave wireless for another thread :P

Sorry bout not mentioning that; Can I still do those commands?

---

### Post by riahc3 on 2008-09-07
Anyone?

---

### Post by riahc3 on 2008-09-09
Bumping this thread up

---

### Post by Crafty Kisses on 2008-09-10
You should try to deactivate the roaming mode. Go into System > Admin. > Networking, select the interface you want to configure and click on Properties. Uncheck the roaming mode to be able to enter your personal config, save it and exit.

I'd also like to see the results of this command:
```
cat /etc/network/interfaces
```
Make sure to remove any credentials that might appear before posting.

---

### Post by riahc3 on 2008-09-14
> **Codename said:**
> You should try to deactivate the roaming mode. Go into System > Admin. > Networking, select the interface you want to configure and click on Properties. Uncheck the roaming mode to be able to enter your personal config, save it and exit.


Already tried this out. Same off/on results.

> **Codename said:**
> 
I'd also like to see the results of this command:
```
cat /etc/network/interfaces
```
Make sure to remove any credentials that might appear before posting.

Results:
```

auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth0

```

Anything else? This problem is very annoying...

---

### Post by Idefix82 on 2008-09-17
Are you dual booting with some version of Windows?
I have exactly the same problem with exactly the same card. One solution which seems to work for some people (not for me) is to enable Wake-on-LAN in Windows. Aparently sometimes the problem is that windows switches the card off and Linux can't switch it back on again.
If that doesn't work for you, get back to me. I am myself about to try out the solution suggested here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/212497/comments/48]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/212497/comments/48")
If you want to try this out, make sure to download the correct version (32 or 64 bit).

---

### Post by riahc3 on 2008-09-24
Yes Im dualbooting with a wubi Vista install. I dont think I have WOL enabled.

---

### Post by Idefix82 on 2008-09-25
Well, I did get my Ethernet card to work. You should enable WOL under Windows and of course in your BIOS and then follow this very simple tutorial:
[http://www.jamesonwilliams.com/hardy-r8168.html]("http://www.jamesonwilliams.com/hardy-r8168.html")

---

### Post by riahc3 on 2008-10-10
Now it just works slow.

---

### Post by taigaChi on 2008-10-21
On a related note, I've had the biggest problems getting my home server to boot using Wake-on-lan (WOL) on a Gigabyte P35-DS4 Mobo with Realtek r8168 NIC. Under Kubuntu Hardy after fresh install WOL was working perfectly at first.

I had made the mistake of trying to install windows on the box, then decided to wipe the partition and go only ubuntu, when WOL stopped working. Turns out there were two unrelated problems compounding the issue, here's what solved it:

1.) follow directions that tell you to enable WOL when booted in Windows, this "reactivates" the NIC to stay on which apparently the Linux driver cannot do (any ideas why this is only a feature in Windows?)

2.) remove the buggy NetworkManager and switch to wicd instead. For me the server is on a wired connection, so all the wireless features are unimportant to me, although wicd seems superior to NetworkManager in wifi as well. NOTE: this is for Kubuntu, for Ubuntu you might have to remove network-manager-gnome

```

sudo -s
echo "deb http://apt.wicd.net hardy extras" >> /etc/apt/sources.list
aptitude -y purge network-manager network-manager-dev network-manager-kde knetworkmanager
wget -q http://apt.wicd.net/wicd.gpg -O- | apt-key add -
aptitude update
aptitude -y install wicd
dhclient eth0
exit

```

CAUTION: the above commands pull up a root shell so that's what the "exit" is for at the end, you wouldn't want to stay in a root shell if you don't have to be!

So to sum up, what happened was that Windows had disabled my NIC (solved using 1.), then at some point after updates NetworkManager broke WOL trying to be too smart and disabling my NIC before shutdown -h now (solved using 2.) I've also experienced NetworkManager and knetworkmanager problems on my laptop (Kubuntu Hardy) where a simple wired connection would "freak out" and not constantly trying to connect but repeatedly failed, and a switch to wicd solved that problem as well. 

Now WOL works every time!

P.S.: when you do 1.) and 2.) above you don't need to omit the -i flag from /etc/init.d/halt command

---

### Post by Black Blade on 2008-10-21
I have a way to get your wireless working I had the same problem and it might fix your wired too let me know if you want it I'd have to send you files.

---

### Post by riahc3 on 2008-10-23
> **Black Blade said:**
> I have a way to get your wireless working I had the same problem and it might fix your wired too let me know if you want it I'd have to send you files.

Post them here; Megaupload or rapidshare...

---

