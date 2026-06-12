---
title: "Connecting to the internet"
date: 2006-06-11
forum: Hardware &amp; Laptops
---

### Post by bastos.sergio on 2006-06-11
Hello,
I am using an IceData 500 adsl modem to connect to the internet.  Using  some precompiled drivers that I found on the internet for ubuntu 6.06, I have been able to connect and ping internet sites...  However, I can't seem to make FireFox load up these pages.  The browser seems to get stuck on a "waiting for response" message and doesn't proceed further.
Anybody knows what could be wrong?
Thanks,

Sergio Bastos

---

### Post by bastos.sergio on 2006-06-12
24 hours later, and I'm still shooting a blank....
The logs show that I'm correctly connecting to the adsl provider:

[SIZE="1"]Jun 12 16:36:40 localhost kernel: [4294842.856000] xsm_p: down_interruptible failed,sem=OBC ,count=0
Jun 12 16:36:40 localhost kernel: [4294842.856000] WaitForObcCmdComplete: wait for obc failed (timed out),obc_flags=08
Jun 12 16:36:40 localhost kernel: [4294842.856000] ObcReset: Resetting OBC...
Jun 12 16:36:40 localhost kernel: [4294842.856000] IntInComplete: actual_length=0
Jun 12 16:36:40 localhost kernel: [4294842.857000] IntInComplete: actual_length=0
Jun 12 16:36:40 localhost kernel: [4294842.857000] USB_controlRead: err=-110
Jun 12 16:36:40 localhost kernel: [4294842.859000] IntInComplete: actual_length=0
Jun 12 16:36:40 localhost kernel: [4294843.248000] unicorn_usb: AdslStatus=1
Jun 12 16:36:40 localhost kernel: [4294843.248000] usbcore: registered new driver unicorn_usb
Jun 12 16:36:40 localhost kernel: [4294843.563000] unicorn_usb: MSW state: ACTIVATING
Jun 12 16:36:47 localhost kernel: [4294849.754000] unicorn_usb: MSW event: TO INITIALIZING
Jun 12 16:36:47 localhost kernel: [4294850.136000] unicorn_usb: MSW state: INITIALIZING
Jun 12 16:36:48 localhost kernel: [4294851.297000] unicorn_usb: created proc entry at /proc/net/atm/UNICORN:0
Jun 12 16:36:48 localhost pppd[5221]: Plugin rp-pppoe.so loaded.
Jun 12 16:36:48 localhost pppd[5384]: pppd 2.4.4b1 started by root, uid 0
Jun 12 16:36:55 localhost kernel: [4294858.255000] is_valid: freeing NULL
Jun 12 16:36:55 localhost kernel: [4294858.255000] xtm_stopmsgtimer: timer 00000000 not valid
Jun 12 16:36:55 localhost kernel: [4294858.462000] unicorn_usb: upRate=603cells/s,downRate=8000cells/s
Jun 12 16:36:55 localhost kernel: [4294858.462000] unicorn_usb: AdslStatus=1
Jun 12 16:36:55 localhost kernel: [4294858.462000] unicorn_usb: MSW event: AMSW SHOWTIME
Jun 12 16:36:55 localhost kernel: [4294858.462000] unicorn_usb: MSW state: SHOWTIME L0
Jun 12 16:37:04 localhost pppd[5384]: PPP session is 13
Jun 12 16:37:04 localhost pppd[5384]: Using interface ppp0
Jun 12 16:37:04 localhost pppd[5384]: Connect: ppp0 <--> dsl0
Jun 12 16:37:04 localhost pppd[5384]: PAP authentication succeeded
Jun 12 16:37:04 localhost pppd[5384]: peer from calling number 00:90:1A:A0:61:66 authorized
Jun 12 16:37:07 localhost pppd[5384]: local  IP address 81.193.182.80
Jun 12 16:37:07 localhost pppd[5384]: remote IP address 194.65.169.193
Jun 12 16:37:07 localhost pppd[5384]: primary   DNS address 194.65.100.117
Jun 12 16:37:30 localhost pppd[5290]: Plugin rp-pppoe.so loaded.
Jun 12 16:37:30 localhost pppd[5436]: pppd 2.4.4b1 started by root, uid 0
Jun 12 16:38:05 localhost pppd[5436]: Timeout waiting for PADO packets
Jun 12 16:39:10 localhost pppd[5436]: Timeout waiting for PADO packets
Jun 12 16:40:15 localhost pppd[5436]: Timeout waiting for PADO packets[/SIZE]

I'm able to ping:

[SIZE="1"]ssbastos@ssbastos-desktop:~$ ping -c 3 google.com
PING google.com (64.233.167.99) 56(84) bytes of data.
64 bytes from 64.233.167.99: icmp_seq=1 ttl=243 time=158 ms
64 bytes from 64.233.167.99: icmp_seq=2 ttl=243 time=158 ms
64 bytes from 64.233.167.99: icmp_seq=3 ttl=243 time=168 ms
[/SIZE]

But firefox still hangs.....
Interestingly, I've been able to download a few updates using synaptic.  Although, the downloads seem to need a couple of minutes to properly start in the aplication...

Sergio Bastos

---

### Post by golfbuf on 2006-06-12
[QUOTE=bastos.sergio]24 hours later, and I'm still shooting a blank....
The logs show that I'm correctly connecting to the adsl provider:

[SIZE="1"]Jun 12 16:36:40 localhost kernel: [4294842.856000] xsm_p: down_interruptible failed,sem=OBC ,count=0
Jun 12 16:36:40 localhost kernel: [4294842.856000] WaitForObcCmdComplete: wait for obc failed (timed out),obc_flags=08
Jun 12 16:36:40 localhost kernel: [4294842.856000] ObcReset: Resetting OBC...
Jun 12 16:36:40 localhost kernel: [4294842.856000] IntInComplete: actual_length=0
Jun 12 16:36:40 localhost kernel: [4294842.857000] IntInComplete: actual_length=0
Jun 12 16:36:40 localhost kernel: [4294842.857000] USB_controlRead: err=-110
Jun 12 16:36:40 localhost kernel: [4294842.859000] IntInComplete: actual_length=0
Jun 12 16:36:40 localhost kernel: [4294843.248000] unicorn_usb: AdslStatus=1
Jun 12 16:36:40 localhost kernel: [4294843.248000] usbcore: registered new driver unicorn_usb
Jun 12 16:36:40 localhost kernel: [4294843.563000] unicorn_usb: MSW state: ACTIVATING
Jun 12 16:36:47 localhost kernel: [4294849.754000] unicorn_usb: MSW event: TO INITIALIZING
Jun 12 16:36:47 localhost kernel: [4294850.136000] unicorn_usb: MSW state: INITIALIZING
Jun 12 16:36:48 localhost kernel: [4294851.297000] unicorn_usb: created proc entry at /proc/net/atm/UNICORN:0
Jun 12 16:36:48 localhost pppd[5221]: Plugin rp-pppoe.so loaded.
Jun 12 16:36:48 localhost pppd[5384]: pppd 2.4.4b1 started by root, uid 0
Jun 12 16:36:55 localhost kernel: [4294858.255000] is_valid: freeing NULL
Jun 12 16:36:55 localhost kernel: [4294858.255000] xtm_stopmsgtimer: timer 00000000 not valid
Jun 12 16:36:55 localhost kernel: [4294858.462000] unicorn_usb: upRate=603cells/s,downRate=8000cells/s
Jun 12 16:36:55 localhost kernel: [4294858.462000] unicorn_usb: AdslStatus=1
Jun 12 16:36:55 localhost kernel: [4294858.462000] unicorn_usb: MSW event: AMSW SHOWTIME
Jun 12 16:36:55 localhost kernel: [4294858.462000] unicorn_usb: MSW state: SHOWTIME L0
Jun 12 16:37:04 localhost pppd[5384]: PPP session is 13
Jun 12 16:37:04 localhost pppd[5384]: Using interface ppp0
Jun 12 16:37:04 localhost pppd[5384]: Connect: ppp0 <--> dsl0
Jun 12 16:37:04 localhost pppd[5384]: PAP authentication succeeded
Jun 12 16:37:04 localhost pppd[5384]: peer from calling number 00:90:1A:A0:61:66 authorized
Jun 12 16:37:07 localhost pppd[5384]: local  IP address 81.193.182.80
Jun 12 16:37:07 localhost pppd[5384]: remote IP address 194.65.169.193
Jun 12 16:37:07 localhost pppd[5384]: primary   DNS address 194.65.100.117
Jun 12 16:37:30 localhost pppd[5290]: Plugin rp-pppoe.so loaded.
Jun 12 16:37:30 localhost pppd[5436]: pppd 2.4.4b1 started by root, uid 0
Jun 12 16:38:05 localhost pppd[5436]: Timeout waiting for PADO packets
Jun 12 16:39:10 localhost pppd[5436]: Timeout waiting for PADO packets
Jun 12 16:40:15 localhost pppd[5436]: Timeout waiting for PADO packets[/SIZE]

I'm able to ping:

[SIZE="1"]ssbastos@ssbastos-desktop:~$ ping -c 3 google.com
PING google.com (64.233.167.99) 56(84) bytes of data.
64 bytes from 64.233.167.99: icmp_seq=1 ttl=243 time=158 ms
64 bytes from 64.233.167.99: icmp_seq=2 ttl=243 time=158 ms
64 bytes from 64.233.167.99: icmp_seq=3 ttl=243 time=168 ms
[/SIZE]

But firefox still hangs.....
Interestingly, I've been able to download a few updates using synaptic.  Although, the downloads seem to need a couple of minutes to properly start in the aplication...

Sergio Bastos[/QUOTE]


Just a stab in the dark .. does 'cat /etc/resolv.conf' show the same DNS as your connection?

Jun 12 16:37:07 localhost pppd[5384]: primary   DNS address 194.65.100.117

Have you tried other browsers to be certain it's not just a firefox problem?  If it's just firefox, try deleting your ~/.mozilla and creating a new one.

regards,

---

### Post by bastos.sergio on 2006-06-13
> 
Just a stab in the dark .. does 'cat /etc/resolv.conf' show the same DNS as your connection?


The file resolv.conf seems to be auto-updated upon every successful connection to the internet.  I don't think this is a firefox problem though.  It looks more like a gnome problem, as most gnome applications can't seem to get a stable connection.  Gaim, for instance, gets as far as downloading a cookie from the internet but then aborts....

I'm including a tcpdump of me pinging google, and of me requesting a page  from within firefox...  Maybe someone can read the tcpdump...  I just started learning all of this and am not very good at it....

Pinging the host:
[SIZE="1"]
ssbastos@ssbastos-desktop:~$ sudo tcpdump host [www.google.com](www.google.com) -vv -i ppp0 > ping.txt
tcpdump: listening on ppp0, link-type LINUX_SLL (Linux cooked), capture size 96 bytes
14 packets captured
32 packets received by filter
0 packets dropped by kernel

15:42:04.662858 IP (tos 0x0, ttl  64, id 0, offset 0, flags [DF], proto: ICMP (1), length: 84) bl4-180-131.dsl.telepac.pt > 64.233.183.103: ICMP echo request, id 53021, seq 1, length 64
15:42:04.751777 IP (tos 0x0, ttl 243, id 0, offset 0, flags [DF], proto: ICMP (1), length: 84) 64.233.183.103 > bl4-180-131.dsl.telepac.pt: ICMP echo reply, id 53021, seq 1, length 64
15:42:09.791651 IP (tos 0x0, ttl  64, id 0, offset 0, flags [DF], proto: ICMP (1), length: 84) bl4-180-131.dsl.telepac.pt > 64.233.183.103: ICMP echo request, id 53021, seq 2, length 64
15:42:09.880996 IP (tos 0x0, ttl 243, id 0, offset 0, flags [DF], proto: ICMP (1), length: 84) 64.233.183.103 > bl4-180-131.dsl.telepac.pt: ICMP echo reply, id 53021, seq 2, length 64
15:42:10.792883 IP (tos 0x0, ttl  64, id 0, offset 0, flags [DF], proto: ICMP (1), length: 84) bl4-180-131.dsl.telepac.pt > 64.233.183.103: ICMP echo request, id 53021, seq 3, length 64
15:42:10.880838 IP (tos 0x0, ttl 243, id 0, offset 0, flags [DF], proto: ICMP (1), length: 84) 64.233.183.103 > bl4-180-131.dsl.telepac.pt: ICMP echo reply, id 53021, seq 3, length 64
15:42:11.793734 IP (tos 0x0, ttl  64, id 0, offset 0, flags [DF], proto: ICMP (1), length: 84) bl4-180-131.dsl.telepac.pt > 64.233.183.103: ICMP echo request, id 53021, seq 4, length 64
15:42:11.880691 IP (tos 0x0, ttl 243, id 0, offset 0, flags [DF], proto: ICMP (1), length: 84) 64.233.183.103 > bl4-180-131.dsl.telepac.pt: ICMP echo reply, id 53021, seq 4, length 64
15:42:12.794579 IP (tos 0x0, ttl  64, id 0, offset 0, flags [DF], proto: ICMP (1), length: 84) bl4-180-131.dsl.telepac.pt > 64.233.183.103: ICMP echo request, id 53021, seq 5, length 64
15:42:12.880538 IP (tos 0x0, ttl 243, id 0, offset 0, flags [DF], proto: ICMP (1), length: 84) 64.233.183.103 > bl4-180-131.dsl.telepac.pt: ICMP echo reply, id 53021, seq 5, length 64
15:42:13.795427 IP (tos 0x0, ttl  64, id 0, offset 0, flags [DF], proto: ICMP (1), length: 84) bl4-180-131.dsl.telepac.pt > 64.233.183.103: ICMP echo request, id 53021, seq 6, length 64
15:42:13.880386 IP (tos 0x0, ttl 243, id 0, offset 0, flags [DF], proto: ICMP (1), length: 84) 64.233.183.103 > bl4-180-131.dsl.telepac.pt: ICMP echo reply, id 53021, seq 6, length 64
15:42:14.796275 IP (tos 0x0, ttl  64, id 0, offset 0, flags [DF], proto: ICMP (1), length: 84) bl4-180-131.dsl.telepac.pt > 64.233.183.103: ICMP echo request, id 53021, seq 7, length 64
15:42:14.880234 IP (tos 0x0, ttl 243, id 0, offset 0, flags [DF], proto: ICMP (1), length: 84) 64.233.183.103 > bl4-180-131.dsl.telepac.pt: ICMP echo reply, id 53021, seq 7, length 64
[/SIZE]

Calling a page within firefox:
[SIZE="1"]
ssbastos@ssbastos-desktop:~$ sudo tcpdump port 80 -vv -i ppp0 > port80.txt
tcpdump: listening on ppp0, link-type LINUX_SLL (Linux cooked), capture size 96 bytes
21 packets captured
42 packets received by filter
0 packets dropped by kernel

15:45:04.404909 IP (tos 0x0, ttl  64, id 37102, offset 0, flags [DF], proto: TCP (6), length: 60) bl4-180-131.dsl.telepac.pt.44544 > newslb12.thdo.bbc.co.uk.www: S, cksum 0xf418 (correct), 592449442:592449442(0) win 5808 <mss 1452,sackOK,timestamp 1613644 0,nop,wscale 2>
15:45:04.474454 IP (tos 0x0, ttl  56, id 0, offset 0, flags [DF], proto: TCP (6), length: 60) newslb12.thdo.bbc.co.uk.www > bl4-180-131.dsl.telepac.pt.44544: S, cksum 0x10c3 (correct), 3997781207:3997781207(0) ack 592449443 win 5792 <mss 1460,sackOK,timestamp 1071212626 1613644,nop,wscale 2>
15:45:04.474511 IP (tos 0x0, ttl  64, id 37103, offset 0, flags [DF], proto: TCP (6), length: 52) bl4-180-131.dsl.telepac.pt.44544 > newslb12.thdo.bbc.co.uk.www: ., cksum 0x5038 (correct), 1:1(0) ack 1 win 1452 <nop,nop,timestamp 1613714 1071212626>
15:45:04.475637 IP (tos 0x0, ttl  64, id 37104, offset 0, flags [DF], proto: TCP (6), length: 795) bl4-180-131.dsl.telepac.pt.44544 > newslb12.thdo.bbc.co.uk.www: P 1:744(743) ack 1 win 1452 <nop,nop,timestamp 1613715 1071212626>
15:45:04.745421 IP (tos 0x0, ttl  64, id 37105, offset 0, flags [DF], proto: TCP (6), length: 795) bl4-180-131.dsl.telepac.pt.44544 > newslb12.thdo.bbc.co.uk.www: P 1:744(743) ack 1 win 1452 <nop,nop,timestamp 1613985 1071212626>
15:45:05.285339 IP (tos 0x0, ttl  64, id 37106, offset 0, flags [DF], proto: TCP (6), length: 795) bl4-180-131.dsl.telepac.pt.44544 > newslb12.thdo.bbc.co.uk.www: P 1:744(743) ack 1 win 1452 <nop,nop,timestamp 1614525 1071212626>
15:45:06.365174 IP (tos 0x0, ttl  64, id 37107, offset 0, flags [DF], proto: TCP (6), length: 795) bl4-180-131.dsl.telepac.pt.44544 > newslb12.thdo.bbc.co.uk.www: P 1:744(743) ack 1 win 1452 <nop,nop,timestamp 1615605 1071212626>
15:45:08.524849 IP (tos 0x0, ttl  64, id 37108, offset 0, flags [DF], proto: TCP (6), length: 795) bl4-180-131.dsl.telepac.pt.44544 > newslb12.thdo.bbc.co.uk.www: P 1:744(743) ack 1 win 1452 <nop,nop,timestamp 1617765 1071212626>
15:45:08.823791 IP (tos 0x0, ttl  56, id 0, offset 0, flags [DF], proto: TCP (6), length: 60) newslb12.thdo.bbc.co.uk.www > bl4-180-131.dsl.telepac.pt.44544: S, cksum 0xff80 (correct), 3997781207:3997781207(0) ack 592449443 win 5792 <mss 1460,sackOK,timestamp 1071216974 1613714,nop,wscale 2>
15:45:08.823834 IP (tos 0x0, ttl  64, id 37109, offset 0, flags [DF], proto: TCP (6), length: 64) bl4-180-131.dsl.telepac.pt.44544 > newslb12.thdo.bbc.co.uk.www: ., cksum 0x7efc (correct), 744:744(0) ack 1 win 1452 <nop,nop,timestamp 1618064 1071216974,nop,nop,sack 1 {0:1}>
15:45:09.863874 IP (tos 0x0, ttl  64, id 23288, offset 0, flags [DF], proto: TCP (6), length: 60) bl4-180-131.dsl.telepac.pt.52095 > 64.233.183.103.www: S, cksum 0xa05f (correct), 596110936:596110936(0) win 5808 <mss 1452,sackOK,timestamp 1619104 0,nop,wscale 2>
15:45:09.953618 IP (tos 0x0, ttl 243, id 56018, offset 0, flags [none], proto: TCP (6), length: 44) 64.233.183.103.www > bl4-180-131.dsl.telepac.pt.52095: S, cksum 0x1630 (correct), 640638843:640638843(0) ack 596110937 win 8190 <mss 1452>
15:45:09.953660 IP (tos 0x0, ttl  64, id 23289, offset 0, flags [DF], proto: TCP (6), length: 40) bl4-180-131.dsl.telepac.pt.52095 > 64.233.183.103.www: ., cksum 0x3733 (correct), 1:1(0) ack 1 win 5808
15:45:09.953765 IP (tos 0x0, ttl  64, id 23290, offset 0, flags [DF], proto: TCP (6), length: 542) bl4-180-131.dsl.telepac.pt.52095 > 64.233.183.103.www: P 1:503(502) ack 1 win 5808
15:45:12.844189 IP (tos 0x0, ttl  64, id 37110, offset 0, flags [DF], proto: TCP (6), length: 795) bl4-180-131.dsl.telepac.pt.44544 > newslb12.thdo.bbc.co.uk.www: P 1:744(743) ack 1 win 1452 <nop,nop,timestamp 1622085 1071216974>
15:45:12.953172 IP (tos 0x0, ttl  64, id 23291, offset 0, flags [DF], proto: TCP (6), length: 542) bl4-180-131.dsl.telepac.pt.52095 > 64.233.183.103.www: P 1:503(502) ack 1 win 5808
15:45:18.952261 IP (tos 0x0, ttl  64, id 23292, offset 0, flags [DF], proto: TCP (6), length: 542) bl4-180-131.dsl.telepac.pt.52095 > 64.233.183.103.www: P 1:503(502) ack 1 win 5808
15:45:20.022090 IP (tos 0x0, ttl  56, id 13646, offset 0, flags [DF], proto: TCP (6), length: 52) newslb12.thdo.bbc.co.uk.www > bl4-180-131.dsl.telepac.pt.44544: F, cksum 0x1382 (correct), 1:1(0) ack 1 win 1448 <nop,nop,timestamp 1071228171 1613714>
15:45:20.023763 IP (tos 0x0, ttl  64, id 37111, offset 0, flags [DF], proto: TCP (6), length: 52) bl4-180-131.dsl.telepac.pt.44544 > newslb12.thdo.bbc.co.uk.www: F, cksum 0xd3d6 (correct), 744:744(0) ack 2 win 1452 <nop,nop,timestamp 1629265 1071228171>
15:45:20.092085 IP (tos 0x0, ttl  56, id 3801, offset 0, flags [DF], proto: TCP (6), length: 40) newslb12.thdo.bbc.co.uk.www > bl4-180-131.dsl.telepac.pt.44544: R, cksum 0x09d0 (correct), 3997781209:3997781209(0) win 0
15:45:30.950436 IP (tos 0x0, ttl  64, id 23293, offset 0, flags [DF], proto: TCP (6), length: 542) bl4-180-131.dsl.telepac.pt.52095 > 64.233.183.103.www: P 1:503(502) ack 1 win 5808
[/SIZE]

Hum....  Also, could this be an adsl driver issue?
The driver does seem to have problems connecting every once in a while....

---

### Post by joao82 on 2006-09-28
hi.
how did you installed your modem? I managed to make mine work quite well.
first I tried to follow these steps in [http://placide.home.sapo.pt/linux01.html](http://placide.home.sapo.pt/linux01.html) so I downloaded [http://placide.home.sapo.pt/linux/unicorn_dapper.tgz](http://placide.home.sapo.pt/linux/unicorn_dapper.tgz)

and did this:
cd Desktop
tar -xvzf unicorn.tgz
cd unicorn
sudo ./unicorn.sh

It asked for the username and password, then the modem was recognized but still no connection.
After that I followed the instructions in this link [http://contribdoc.caixamagica.pt/twiki/bin/view/Main/AdslIcedata500](http://contribdoc.caixamagica.pt/twiki/bin/view/Main/AdslIcedata500) for the  PPPOE part. So I downloaded the drivers at [http://www.bewan.com/bewan/drivers/bast-0.9.0.tgz](http://www.bewan.com/bewan/drivers/bast-0.9.0.tgz) and installed it.
Because it was a fresh installation of Ubuntu I had to download through Windows all the deb packages like "make", "cpp" etc from packages.ubuntu.com that would allow me to install the drivers. Also the Linux headers gave me problems.
In the driver's makefile file an instruction pointed at "/usr/src/linux" but it didn't exist. So I downloaded linux-headers-2.6.15-26-386_2.6.15-26.46_i386.deb in the ubuntu repositories and many other files that could have connection with it then installed all.
So then I edited the makefile and replaced "/usr/src/linux" for "usr/src/linux-2.6.15-26-386" (not bad for a noob uh?).
After doing all that the drivers could finally be installed using
# tar -zxf bast-0.9.0.tgz
# cd unicorn
# make all  
# sudo make install
with no errors.
Most of the steps after that were already done because of the initial script that I tried. But it's a very good point to blacklist the unicorn_usb_atm driver, although I didn't find the exact blacklist file.

I wish I could be more explicit but I really don't know when the modem started working. I was messing in the terminal windown and looked down and both green lights were on. I also remember editing the DNS in some file but  I can't remember exactly what I did. But now my modem is working 100%. It can be a bit stubborn sometimes because it may not connect at first try but with a little patience and a reboot it works.

btw, all the links are in portuguese hehe

---

### Post by www.rzr.online.fr on 2007-12-24
> **joao82 said:**
> hi.
how did you installed your modem? I managed to make mine work quite well.


On which kernel ?

  cat /proc/version
  lsusb

Later
--
[http://rzr.online.fr/q/unicorn](http://rzr.online.fr/q/unicorn)

---

