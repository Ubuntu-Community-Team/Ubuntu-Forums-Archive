---
title: "wifi printer not connecting after new router installation"
date: 2017-06-05
forum: Hardware
---

### Post by pjstock on 2017-06-05
I will dig into the mass of suggestions for how to install a wifi printer on Ubuntu but since my situation is a little bit unique I thought I would post the specifics here in the hopes that someone can guide to to a simple fix.

My Ubuntu 16.04 LTS had been happily talking to and printing wirelessly to my Brother HL-3070CW wireless printer for several years.

This weekend though I changed wifi routers (to try to investigate reliability issues) and changed name of my access point. or at least put the old name in ALL CAPS so that I could distinguish it from the old router if I had to. And that seemed to blow away the happy connection. 
and I cannot remember how I managed to get the wifi printing working when I first setup the printer those several years ago. (might I have first set it up on Windows? I was using Windows more frequently back then. could that even help?)
and for the moment I cannot seem to get the printer to see the Access Point nor can I get Ubuntu to see the printer via the network.

does anyone have any simple solution I could try before I get my hands really really dirty?

Peter

Hmm, on restarting everything (and setting the SSID back to the original name - not that I suspect that has anything to do with it.) I see to get some progress.
with only the wifi on (no LAN cable connection) The Add Printer dialogue in System Settings seems to identify the Brother printer on the Network, seems to find the drivers, seems to install it BUT.... fails to print a test page "printer not responding"
what am I missing here?

---

### Post by pdc on 2017-06-05
sorry to hear of your troubles; the ideal person would write down how they did all sorts of stuff: I certainly forget to do that;

I am not clear what you have done; so if I go over what I understand you may need to do:

1) the router needs to be talking to the printer; in this sort of way [https://www.youtube.com/watch?v=p-TzpVFUyv0](https://www.youtube.com/watch?v=p-TzpVFUyv0)

2) if that is all good, I wonder what ```
lpinfo -v
``` says please

---

### Post by pjstock on 2017-06-05
When I set this up the first time, several years ago, it was nowhere near as complicated as this. I would have remember this.

that video looks very helpful, except that my WLAN menus do not have a "Search SSID" option.
I do have:
Network > WLAN
and then: 
TCP/IP
SESS/WPS/AOSS (which is supposed to search for AOSS enabled routers, which I doubt mine is.) when I OK this I get "Setting WLAN" and then it just sits there.
WPS w/ PIN CODE
WLAN STATUS (which shows "ACTIVE 11g" when I drill down)
and WLAN ENABLE (which shows ON)

I did finally manage to run the Brother Printer Installer in Terminal. That seemed to be doing some good things and at the end of it, I was able to specify the IP Address of the printer and print a test page via the Ethernet cable, but not via Wifi.

peter@CollierDesk:~/Downloads/tmp$ lpinfo -v
network ipp
network beh
network lpd
network https
network ipps
network socket
network http
network ipp14
serial serial:/dev/ttyS0?baud=115200
serial serial:/dev/ttyS1?baud=115200
direct hp
network smb
direct hpfax
network dnssd://Brother%20HL-3070CW%20series._pdl-datastream._tcp.local/
peter@CollierDesk:~/Downloads/tmp$ ^C
peter@CollierDesk:~/Downloads/tmp$

Hmmm, my Network Configuration report shows a proming:

<wireless link status> Link OK, 11g (48Mbps, receiving signal = 3 operating Ch = 4

But when I Ping the IP Address shown  on the sheet (192.168.3.226) I get:
peter@CollierDesk:~/Downloads/tmp$ ping 192.168.3.226 -c 4
PING 192.168.3.226 (192.168.3.226) 56(84) bytes of data.
From 192.168.3.78 icmp_seq=1 Destination Host Unreachable
From 192.168.3.78 icmp_seq=2 Destination Host Unreachable
From 192.168.3.78 icmp_seq=3 Destination Host Unreachable
From 192.168.3.78 icmp_seq=4 Destination Host Unreachable

which doesn't sound good.

and, miraculously, the wifi printing suddenly seems to work. I have no idea why. or how.
which is a bit annoying. I don't like thinking things just happen by trial and error.

but the ping now is coming back:
peter@CollierDesk:~$ ping 192.168.3.226 -c 4
PING 192.168.3.226 (192.168.3.226) 56(84) bytes of data.
64 bytes from 192.168.3.226: icmp_seq=1 ttl=255 time=3.32 ms
64 bytes from 192.168.3.226: icmp_seq=2 ttl=255 time=2.72 ms
64 bytes from 192.168.3.226: icmp_seq=3 ttl=255 time=2.85 ms
64 bytes from 192.168.3.226: icmp_seq=4 ttl=255 time=8.86 ms

--- 192.168.3.226 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3004ms
rtt min/avg/max/mdev = 2.729/4.442/8.863/2.562 ms

who knows. 
But I wish I knew what the trick was.

---

### Post by pdc on 2017-06-06
so we hope it is all go there for you

---

