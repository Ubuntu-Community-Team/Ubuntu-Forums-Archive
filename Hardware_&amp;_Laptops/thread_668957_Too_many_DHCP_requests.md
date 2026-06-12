---
title: "Too many DHCP requests"
date: 2008-01-15
forum: Hardware &amp; Laptops
---

### Post by Rocket2DMn on 2008-01-15
I use my laptop on my university's wireless network, but I never had this problem through windows.  I didn't have any problems connecting today, but eventually I get an email from our IT people telling me my card has been disabled because of too many DHCP requests.
> Network access for [MY MAC ADDRESS] has been disabled at 01/15/08 15:00:09: Disabled because [MY MAC ADDRESS] (your computer's Wired/Wireless card) sent
too many DHCP requests. Your computer attempted and failed to acquire an IP address more than 60 times in 3600 seconds.

I had this problem over the summer, but figured it was just b/c I had a weak connection.  Is there a way to adjust the DHCP request frequency to help me avoid this problem?
My wireless card is an ipw2200 (intel pro wireless 2200 b/g)
Thanks in advance.

---

### Post by Rocket2DMn on 2008-01-16
bump

---

### Post by ugm6hr on 2008-01-16
I have no idea why that happened - maybe it is due to weak signal.

A potential solution (perhaps a little devious), is to use macchanger to change your MAC address every time you connect:
[https://help.ubuntu.com/community/AnonymizingNetworkMACAddresses](https://help.ubuntu.com/community/AnonymizingNetworkMACAddresses)

An automated detection system shouldn't recognise multiple connection attempts with different MAC addresses.

---

### Post by Rocket2DMn on 2008-01-16
Thanks, the thought had occurred to me, but my connection works better (and possibly requires) that my MAC address be registered.  I was hoping for a fix, surely there must be a setting somewhere that determines how often a DHCP request is sent.
Perhaps it's still sending requests once it's already connected?

---

### Post by ugm6hr on 2008-01-16
I do remember that Network Manager *scans* at intervals for wifi networks, but why would it request a new IP when *already* connected?

And if it was *unsuccessful* every minute, I think you would have noticed that you were disconnected for 6 minutes.

Very bizarre.

But perhaps it is a problem with NM - maybe try Wicd?

---

### Post by Yellow Pasque on 2008-01-16
DHCP can be used for other things (like a time server), so it's possible that the DHCP requests were unrelated to acquiring an IP.

What does your /etc/dhcp3/dhclient.conf look like?

---

### Post by Rocket2DMn on 2008-01-16
The computer was definitely requesting an IP address for itself, not a server.  I know this is a problem in areas of weak signal strength, but that wasn't my problem.
Here is my dhclient.conf
> # Configuration file for /sbin/dhclient, which is included in Debian's
#       dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#       man page for more information about the syntax of this file
#       and a more comprehensive list of the parameters understood by
#       dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#       not leave anything out (like the domain name, for example), then
#       few changes must be made to this file, if any.
#

send host-name "<hostname>";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-name-servers, host-name,
        netbios-name-servers, netbios-scope;
#require subnet-mask, domain-name-servers;
timeout 30;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}

#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}

---

### Post by Rocket2DMn on 2008-01-22
Gonna bump this again, still getting kicked off the wireless for too many DHCP requests.
Any ideas people?

---

### Post by ugm6hr on 2008-01-22
> **Rocket2DMn said:**
> Gonna bump this again, still getting kicked off the wireless for too many DHCP requests.
Any ideas people?

Still wondering if this is Network Manager misbehaving...  Have you tried an alternative roaming app - Wicd, wifi radar etc?

---

### Post by Rocket2DMn on 2008-01-22
I have not, but it seems that there should be a setting somewhere to control the DHCP request rate.  the dhclient.conf file seems to be the right place, but my numbers seem ok by just running simple calculations.  The email I received said I requested an IP more than 60 times in 1 hour, but that shouldn't be so based on the numbers from dhclient.
Do you think Wicd or wifi radar are any good?  I've never even heard of them.

EDIT: Just looked at wifi-radar (Wicd isn't in the repos), but it doesn't look like much.  I think I need to be configuring dhclient correctly.  I think I will make a post in the Networking and Wireless forums.  Thanks for your help.  I'll post back if I fix the problem.

---

### Post by ugm6hr on 2008-01-22
Wicd is not in the main repos - it is linked below in my sig.  It has its own repo (details given on its website).

I haven't used it since upgrading to Gutsy, since Network Manager no longer appears to misbehave.  But it has lots of fans, and is the default in the XFCE Mint version.  It certainly worked flawlessly when I used the last version.

Whether it fixes this problem is another question!

---

