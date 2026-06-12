---
title: "Bizarre problem: internet stopped working on one partition only"
date: 2005-11-29
forum: General Help
---

### Post by aysiu on 2005-11-29
I don't know what's going on.
I have all sorts of partitions.
A couple of hours ago, I installed a fresh Kubuntu onto one of my unused partitions (I have two other Ubuntu installations on two other partitions). All of a sudden, the internet on my default Ubuntu installation (/dev/hda8) stopped working.

The bizarre thing is that internet works just fine on my other Ubuntu installation (/dev/hda3) and the new Kubuntu installation (/dev/hda6).

Why would the internet just stop working on /dev/hda8 after installing Kubuntu on a completely different partition?

Even during bootup, it can't locate the ntp.ubuntulinux.org clock sync. I looked in Networking and the usual Eth0 with DHCP is Active. Still--no email, no web.

Obviously my network cable is plugged in, as I can get internet on the same computer, using the same operating system... on two separate partitions.

Has anyone ever heard of such a thing? Any solutions?

P.S. I'm running this from /dev/hda3's Ubuntu right now.

---

### Post by amohanty on 2005-11-29
This might be completely off the mark, but I have only seen this on windows with multiple versions on the same box, but could it be some sort of residual IP conflict on your internal network? 

what does arp on some other machine on the same network return?

AM

---

### Post by aysiu on 2005-11-29
[QUOTE=amohanty]
what does arp on some other machine on the same network return?[/QUOTE] arp? Is that a command? Some other *machine* or some other *partition*?

**Edit**: On one of my working partitions, this is what I get ```
arp
Address                  HWtype  HWaddress           Flags Mask            Iface
192.168.0.1              ether   00:11:95:36:A3:5D   C                     eth0
``` If it's a residual IP conflict, I wonder if shutting down the computer altogether might make a difference (shutting down, as opposed to rebooting). Is there a way to clean out the cache?

By the way, if I type 192.168.0.1 in the non-working Breezy partition's Firefox, it just hangs. Usually, that will connect me to the router's configuration dialogue.

---

### Post by amohanty on 2005-11-29
Some use info and uses of arp can be found here:
[http://www.linux.com/guides/nag2/x-087-2-iface.verify.arp.shtml](http://www.linux.com/guides/nag2/x-087-2-iface.verify.arp.shtml)

In case the source of the problem is a ip conflict, you probably need to flush the kernel arp cache and reboot. 

I meant another machine on the same network. If the problem machine is the only machine on the network then the source lies elsewhere, something that might need some digging into.

To clear the cache you can use:
arp -d

Can you ping your router?
If so then you can check if port 80 on your router is accessible by:
telnet <192.168.0.1> 80

AM

---

### Post by aysiu on 2005-11-29
Thanks for the resources. I'll play around a bit--see what I can find.

---

