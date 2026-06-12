---
title: "Upgraded to 9.04. Lost all internet connectivity!"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by Maconvert on 2009-04-25
Hello,

I just upgraded from 8.10 to 9.04 and, although it appeared to go smoothly, I now have no internet connectivity.
I tried pinging websites and IP address in the terminal and neither method worked.
I was able to get Firefox to load [www.google.ca](www.google.ca), but as soon as I clicked on the link to [www.gmail.com](www.gmail.com) my connection was gone.
I know my internet connection is fine because I'm posting this on another machine (XP) that's connected to the same router.
I'm using a wired connection.

Does anybody know what's going on here?

I look forward to your replies.

Thanks.

---

### Post by abn91c on 2009-04-25
try reloading the network applet, in Kubuntu re-adding the network manager to the taskbar seems to fixed the issue for lost connections(happened to me last night when upgrading to 9.04)

---

### Post by Maconvert on 2009-04-25
Hello,

Thanks for your reply.
I launched the Network Tools application in Ubuntu and I noticed that my "Network Device" was listed as "Loopback Interface". I then changed it to "Ethernet Interface (eth0)". I assumed that this would have fixed the problem, but I still couldn't get a webpage. Also, when I checked the "Network Tools" application again, it had switched back to "Loopback Interface".

Does anybody have any ideas here?

Regards.

---

### Post by aflores3 on 2009-04-26
I was having the same problem. I stumbled across this page: [https://help.ubuntu.com/9.04/serverguide/C/network-configuration.html](https://help.ubuntu.com/9.04/serverguide/C/network-configuration.html)

Here's the part that helped me> 
Ethernet

Most Ethernet configuration is centralized in a single file, /etc/network/interfaces. If you have no Ethernet devices, only the loopback interface will appear in this file, and it will look something like this:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0
```

If you have only one Ethernet device, eth0, and it gets its configuration from a DHCP server, and it should come up automatically at boot, only two additional lines are required:

```
auto eth0
iface eth0 inet dhcp
```

The first line specifies that the eth0 device should come up automatically when you boot. The second line means that interface (“iface”) eth0 should have an IPv4 address space (replace “inet” with “inet6” for an IPv6 device) and that it should get its configuration automatically from DHCP. Assuming your network and DHCP server are properly configured, this machine's network should need no further configuration to operate properly. The DHCP server will provide the default gateway (implemented via the route command), the device's IP address (implemented via the ifconfig command), and DNS servers used on the network (implemented in the /etc/resolv.conf file.) 

I just edited the /etc/network/interfaces to read exactly as it said.
hope that helps.

---

### Post by Maconvert on 2009-04-26
Hi,

Thanks for the tip, but that did not fix my problem.
Although my original "/etc/network/interfaces" only contained the first two lines of the one you showed me, even after making my file look exactly the same it would not work. 

Also, when I click on the network connectivity icon in the top task bar (which currently has a red circle with an X) a menu drops down with 3 options: Wired Network, Device not managed, VPN connections. Of these 3, the first 2 are grayed out and only "VPN Connections" (and it's sub-menus) is available to me.

So, I still do not have any internet connectivity on my downloader PC and I'm not very happy about it.

Does anybody else have any suggestions?

Cheers.

---

### Post by Kalrog on 2009-04-26
> **Maconvert said:**
> Hi,

Thanks for the tip, but that did not fix my problem.
Although my original "/etc/network/interfaces" only contained the first two lines of the one you showed me, even after making my file look exactly the same it would not work. 


I'm in the same situation as Maconvert it appears.  I just added those 2 lines to the interfaces file and it changed nothing.  I'm sitting here without a working network interface on my PC - everything worked great yesterday before the 8.10 to 9.04 upgrade.  I am on 64-bit KUbuntu though.  Thoughts?  Help?

---

### Post by Kalrog on 2009-04-26
I did find this bug leading me to add the network manager to the sys tray, but it is still giving me an error about eth0 not being managed - and still no network connectivity.

[https://bugs.launchpad.net/ubuntu-release-notes/+bug/349066](https://bugs.launchpad.net/ubuntu-release-notes/+bug/349066)

---

### Post by Maconvert on 2009-04-26
Sorry to hear about your troubles Kalrog, but glad to hear that I'm not the only one.

This sucks really.

I was just talking to my boss lately about how great Ubuntu was and I think that I've got him 90% convinced that it is the right solution for a kiosk contract we're bidding on. We'd probably even pay for the high-priority tech support too (at least for the first year) because it is still way cheaper than a bunch of XP licenses. However, if I can't get this resolved soon I'm pretty sure he's just going to go with what he knows - crappy XP. With that and Deep Freeze we should be ok. In any case, I don't want to look like a fool, so I'm definitely not going to press the point if he decides to go that route. I could argue that 8.10 was just fine, but I don't think that will convince him though. I'm pretty sure that an OS that totally loses internet connectivity is just too big a bug for him to deal with.

This is sad really, because I've loved working with Ubuntu over the last year and I was looking forward to using it in a work project.

Anyway, enough complaining already. Let's get this problem solved.

Cheers.

---

### Post by Maconvert on 2009-04-26
I have some more information that may help in daignosing my problem. 

On my router I went to the "Status > LAN" page and took a look.
In the "Active Clients" and "DHCP Clients" sections, my XP computer was the only one listed. I then rebooted my Ubuntu 9.04 machine and it's IP and MAC address then popped up in the "Active Clients" list but NOT the "DHCP Clients" list.
Then, afer a minute or so, it disappeared again from the "Active Clients" list.

Hopefully this will help.

In any case, although I have had some issues with Ubuntu is the last two versions, I've never had anything but smooth sailing where internet connectivity was concerned.

Cheers.

---

### Post by Maconvert on 2009-04-26
Hello Again,

I'm trying to provide as much information as I can to help solve this problem. I've attached two screenshots of my network settings to this post.
By the way, on my router page (the one I mentioned in my previous post) it listed the Ubuntu PC's IP address as 192.168.1.103. I'm not sure what the 192.168.1.2. is about. In any case, the only change I've made to my network was to upgrade from Ubuntu 8.10 to Ubuntu 9.04.

Regards.

---

### Post by dfoxpro on 2009-04-28
Re: Upgraded to 9.04. Lost all internet connectivity!
In my case i have a dualSO (1ºUbu810,2ºWinXp...3ºUbu904)

the first week all OS work perfect, but after upgrade the bios of my netbook (asus 1501 => 1903) after that the internet connection (only in the 904) was gone... but when i try in ubu810 and winxp all works without problem...

the other part that i see is in the network manager... the 904 got the ip, the subnet but no the broadcast.

its happen with only the 904 (livecd and clean instalation)..


Hardware:
Asus eeepc 1000ha

---

### Post by dfoxpro on 2009-04-28
Deleteme

---

### Post by Maconvert on 2009-05-02
Is anybody working on this?
I'm still stuck with a computer that has a nice GUI but no internet connection.
Do I really need to reinstall a fresh copy of Ubuntu 9.04 on this machine? If so, that sucks.

---

### Post by dfoxpro on 2009-05-07
> **Maconvert said:**
> Is anybody working on this?
... that sucks.

I'm pseudo-solve this problem ¬¬

If you connect to the internet across a bridge or router shut-off this-one, then shut-off the other host; shut-on the router and the 904 bugged will connect to the internet. finally shut-on the other host...

This solution sucks but works... please report all issues to launchpad to get a better solution.
[https://bugs.launchpad.net/ubuntu-release-notes/+bug/370674](https://bugs.launchpad.net/ubuntu-release-notes/+bug/370674)

---

### Post by Maconvert on 2009-05-07
Thanks, but I gave up and reformatted.
I'm going to do a fresh install next week.
What a pain.

---

### Post by AndBurns on 2009-05-16
I had exactly the same problem.  Following some threads elsewhere on the internet I determined that the problem was that the upgrade process had failed to upgrade my grub menu.lst file to include the new 9.04 compatible kernel.

So i edited the file /boot/grub/menu.lst manually inserting references to the newly installed 9.04 kernel.  In my case this was 2.6.28-11-generic.  I determined which it was by doring a directory of the /boot directory 

ls  -l /boot

and noting which was the most recent kernel.

I then inserted the following lines into my menu.lst file just above where various other such lines are -- after the line 

## ## End Default Options  ##

Here are the lines I inserted

title Ubuntu 9.04 Kernel 2.6.28-11-generic
uuid xxxxx   (NB this will be a long alphanumeric that is different from machine to machine and indicates which hard disk to use
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=xxxx (same as above) ro quiet pci=msi
/initrd /boot/initrd.img-2.6.28-11-generic
quiet

Hope this works for you.

---

