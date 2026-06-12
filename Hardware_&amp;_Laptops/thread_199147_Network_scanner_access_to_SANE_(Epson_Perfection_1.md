---
title: "Network scanner access to SANE (Epson Perfection 1650)"
date: 2006-06-18
forum: Hardware &amp; Laptops
---

### Post by isoaglib on 2006-06-18
Hi,
I have changed some PCs in a LAN from Kanotix to Kubuntu 6.06 . I get _local_ scanner access working with kooka.

BUT I have no success with network acces - even if I can compare my previous _working_ setup from Kanotix.

I tried all sorts of inetd (direct saned and tcpd) and xinetd configurations, that I found with google and in the man pages.

I also added the saned.saned user to the group "scanner".

I checked several times to set the /etc/sane.d/net.conf of the client to the correct server.

Is there something broken with sane in dapper?
Or are there some hidden security settings that disable network sane access - even after starting xinetd with the right settings?

My system:
+ AMD K7 based
+ Kubuntu 6.06
+ Scanner: Epson Perfection 1650
+ USB connected
+ network scanning worked before with KANOTIX
+ _local_ scanning works fine!!!
+ REMOTE: no scanner is found by "scanimage -L"

Here is some debug output:
SANE_DEBUG_NET=128 scanimage -L
[sanei_debug] Setting debug level of net to 128.
[net] sane_init: authorize = 0x80491d0, version_code = 0xbfb4c428
[net] sane_init: SANE net backend version 1.0.13 (AF-indep+IPv6) from sane-backends 1.0.17
[net] sane_init: Client has little endian byte order
[net] sane_init: searching for config file
[net] sane_init: trying to add 192.168.0.10
[net] add_device: adding backend 192.168.0.10
[net] add_device: backend 192.168.0.10 added
[net] sane_init: done reading config
[net] sane_init: evaluating environment variable SANE_NET_HOSTS
[net] sane_init: done
[net] sane_get_devices: local_only = 0
[net] connect_dev: trying to connect to 192.168.0.10
[net] connect_dev: [0] connection succeeded (IPv4)
[net] connect_dev: sanei_w_init
[net] connect_dev: net_init (user=obry, local version=1.0.3)
[net] connect_dev: freeing init reply (status=Success, remote version=1.0.3)
[net] connect_dev: done


==>>
basic network access seems to work.
But the client doesn't find anything

##########
SANE_DEBUG_EPSON=128 saned -d128
[saned] main: starting debug mode (level 128)
[saned] main: trying to get port for service `sane-port' (getaddrinfo)
[saned] main: [0] socket () using IPv6
[saned] main: [0] setsockopt ()
[saned] main: [0] bind () to port 6566
[saned] main: [0] listen ()
[saned] main: [1] socket () using IPv4
[saned] main: [1] setsockopt ()
[saned] main: [1] bind () to port 6566
[saned] main: [1] bind failed: Address already in use
[saned] main: waiting for control connection
[saned] saned (AF-indep+IPv6) from sane-backends 1.0.17 ready
[saned] check_host: detected an IPv4-mapped address
[saned] check_host: access by remote host: ::ffff:192.168.0.12
[saned] check_host: remote host is not IN_LOOPBACK nor IN6_LOOPBACK
[saned] check_host: local hostname: kfd-server
[saned] check_host: local hostname(s) (from DNS): kfd-server
[saned] check_host: local hostname(s) (from DNS): (null)
[saned] check_host: local hostname(s) (from DNS): (null)
[saned] check_host: remote host doesn't have same addr as local
[saned] check_host: opening config file: /etc/hosts.equiv
[saned] check_host: can't open config file: /etc/hosts.equiv (No such file or directory)
[saned] check_host: opening config file: saned.conf
[saned] check_host: config file line: `#'
[saned] check_host: config file line: `# saned.conf'
[saned] check_host: config file line: `#'
[saned] check_host: config file line: `# The contents of the saned.conf  file  is  a  list  of  host  names,  IP'
[saned] check_host: config file line: `# addresses or IP subnets (CIDR notation) that are permitted to use local'
[saned] check_host: config file line: `# SANE devices. IPv6 addresses must be enclosed in brackets,  and  should'
[saned] check_host: config file line: `# always  be specified in their compressed form.'
[saned] check_host: config file line: `#'
[saned] check_host: config file line: `# The hostname matching is not case-sensitive.'
[saned] check_host: config file line: `#'
[saned] check_host: config file line: `#scan-client.somedomain.firm'
[saned] check_host: config file line: `#192.168.0.1'
[saned] check_host: config file line: `#192.168.0.1/29'
[saned] check_host: config file line: `#[2001:7a8:185e::42:12]'
[saned] check_host: config file line: `#[2001:7a8:185e::42:12]/64'
[saned] check_host: config file line: `#'
[saned] check_host: config file line: `# NOTE: /etc/inetd.conf (or /etc/xinetd.conf) and'
[saned] check_host: config file line: `# /etc/services must also be properly configured to start'
[saned] check_host: config file line: `# the saned daemon as documented in saned(8), services(4)'
[saned] check_host: config file line: `# and inetd.conf(4) (or xinetd.conf(5)).'
[saned] check_host: config file line: `192.168.0.6'
[saned] check_host: DNS lookup returns IP address: 192.168.0.6
[saned] check_host: DNS lookup returns IP address: 192.168.0.6
[saned] check_host: DNS lookup returns IP address: 192.168.0.6
[saned] check_host: config file line: `'
[saned] check_host: config file line: `192.168.0.10'
[saned] check_host: DNS lookup returns IP address: 192.168.0.10
[saned] check_host: DNS lookup returns IP address: 192.168.0.10
[saned] check_host: DNS lookup returns IP address: 192.168.0.10
[saned] check_host: config file line: `192.168.0.11'
[saned] check_host: DNS lookup returns IP address: 192.168.0.11
[saned] check_host: DNS lookup returns IP address: 192.168.0.11
[saned] check_host: DNS lookup returns IP address: 192.168.0.11
[saned] check_host: config file line: `192.168.0.12'
[saned] check_host: access granted from IP address ::ffff:192.168.0.12 (IPv4-mapped)
[saned] init: access granted
[saned] init: access granted to obry@::ffff:192.168.0.12
[saned] process_request: waiting for request
[saned] process_request: got request 1
[sanei_debug] Setting debug level of epson to 128.
[epson] sane_init: sane-backends 1.0.17
[epson] sane_init, ># epson.conf<
[epson] sane_init, >#<
[epson] sane_init, ># here are some examples for how to configure the EPSON backend<
[epson] sane_init, >#<
[epson] sane_init, ># SCSI scanner:<
[epson] sane_init, >#scsi EPSON<
[epson] sane_init, ># for the GT-6500, comment out the previous line and uncomment the following line:<
[epson] sane_init, >#scsi<
[epson] sane_init, >#<
[epson] sane_init, ># Parallel port scanner:<
[epson] sane_init, >#pio 0x278<
[epson] sane_init, >#pio 0x378<
[epson] sane_init, >#pio 0x3BC<
[epson] sane_init, >#<
[epson] sane_init, ># USB scanner:<
[epson] sane_init, ># There are two different methods of configuring a USB scanner: libusb and the kernel module<
[epson] sane_init, ># For any system with libusb support (which is pretty much any recent Linux distribution) the<
[epson] sane_init, ># following line is sufficient. This however assumes that the connected scanner (or to be more<
[epson] sane_init, ># accurate, it's device ID) is known to the backend.<
[epson] sane_init, >usb<
[epson] attach_one_usb()
[epson] SANE Epson Backend v0.2.45 - 2000-01-09
[epson] attach(, 3)
[epson] attach: opening
[epson] attach_one_usb(libusb:001:004)
[epson] SANE Epson Backend v0.2.45 - 2000-01-09
[epson] attach(libusb:001:004, 3)
[epson] attach: opening libusb:001:004
[epson] Found valid EPSON scanner: 0x4b8/0x110 (vendorID/productID)
[epson] reset()
[epson] send buf, size = 2
[epson] buf[0] 1b .
[epson] buf[1] 40 @
[epson] w_cmd_count = 1
[epson] r_cmd_count = 0
[epson] w_cmd_count = 1
[epson] r_cmd_count = 1
[epson] receive buf, expected = 1, got = 1
[epson] buf[0] 06 .
[epson] get_identity_information()
[epson] send buf, size = 2
[epson] buf[0] 1b .
[epson] buf[1] 49 I
[epson] w_cmd_count = 2
[epson] r_cmd_count = 1
[epson] w_cmd_count = 2
[epson] r_cmd_count = 2
[epson] receive buf, expected = 4, got = 4
[epson] buf[0] 02 .
[epson] buf[1] 02 .
[epson] buf[2] 6a j
[epson] buf[3] 00 .
[epson] code   02
[epson] status 02
[epson] count  106
[epson] w_cmd_count = 2
[epson] r_cmd_count = 4
[epson] receive buf, expected = 106, got = 106
[epson] buf[0] 42 B
[epson] buf[1] 38 8
[epson] buf[2] 52 R
[epson] buf[3] 32 2
[epson] buf[4] 00 .
[epson] buf[5] 52 R
[epson] buf[6] 3c <
[epson] buf[7] 00 .
[epson] buf[8] 52 R
[epson] buf[9] 48 H
[epson] buf[10] 00 .
[epson] buf[11] 52 R
[epson] buf[12] 4b K
[epson] buf[13] 00 .
[epson] buf[14] 52 R
[epson] buf[15] 50 P
[epson] buf[16] 00 .
[epson] buf[17] 52 R
[epson] buf[18] 5a Z
[epson] buf[19] 00 .
[epson] buf[20] 52 R
[epson] buf[21] 64 d
[epson] buf[22] 00 .
[epson] buf[23] 52 R
[epson] buf[24] 78 x
[epson] buf[25] 00 .
[epson] buf[26] 52 R
[epson] buf[27] 85 .
[epson] buf[28] 00 .
[epson] buf[29] 52 R
[epson] buf[30] 90 .
[epson] buf[31] 00 .
[epson] buf[32] 52 R
[epson] buf[33] 96 .
[epson] buf[34] 00 .
[epson] buf[35] 52 R
[epson] buf[36] a0 .
[epson] buf[37] 00 .
[epson] buf[38] 52 R
[epson] buf[39] af .
[epson] buf[40] 00 .
[epson] buf[41] 52 R
[epson] buf[42] b4 .
[epson] buf[43] 00 .
[epson] buf[44] 52 R
[epson] buf[45] c8 .
[epson] buf[46] 00 .
[epson] buf[47] 52 R
[epson] buf[48] d8 .
[epson] buf[49] 00 .
[epson] buf[50] 52 R
[epson] buf[51] f0 .
[epson] buf[52] 00 .
[epson] buf[53] 52 R
[epson] buf[54] 0a .
[epson] buf[55] 01 .
[epson] buf[56] 52 R
[epson] buf[57] 2c ,
[epson] buf[58] 01 .
[epson] buf[59] 52 R
[epson] buf[60] 40 @
[epson] buf[61] 01 .
[epson] buf[62] 52 R
[epson] buf[63] 5e ^
[epson] buf[64] 01 .
[epson] buf[65] 52 R
[epson] buf[66] 68 h
[epson] buf[67] 01 .
[epson] buf[68] 52 R
[epson] buf[69] 90 .
[epson] buf[70] 01 .
[epson] buf[71] 52 R
[epson] buf[72] e0 .
[epson] buf[73] 01 .
[epson] buf[74] 52 R
[epson] buf[75] 58 X
[epson] buf[76] 02 .
[epson] buf[77] 52 R
[epson] buf[78] d0 .
[epson] buf[79] 02 .
[epson] buf[80] 52 R
[epson] buf[81] 20
[epson] buf[82] 03 .
[epson] buf[83] 52 R
[epson] buf[84] 84 .
[epson] buf[85] 03 .
[epson] buf[86] 52 R
[epson] buf[87] b0 .
[epson] buf[88] 04 .
[epson] buf[89] 52 R
[epson] buf[90] 40 @
[epson] buf[91] 06 .
[epson] buf[92] 52 R
[epson] buf[93] 08 .
[epson] buf[94] 07 .
[epson] buf[95] 52 R
[epson] buf[96] 60 `
[epson] buf[97] 09 .
[epson] buf[98] 52 R
[epson] buf[99] 80 .
[epson] buf[100] 0c .
[epson] buf[101] 41 A
[epson] buf[102] 40 @
[epson] buf[103] 6a j
[epson] buf[104] 40 @
[epson] buf[105] 92 .
[epson] type    B 0x42
[epson] level   8 0x38
[epson] no option equipment installed
[epson] resolution (dpi): 50
[epson] resolution (dpi): 60
[epson] resolution (dpi): 72
[epson] resolution (dpi): 75
[epson] resolution (dpi): 80
[epson] resolution (dpi): 90
[epson] resolution (dpi): 100
[epson] resolution (dpi): 120
[epson] resolution (dpi): 133
[epson] resolution (dpi): 144
[epson] resolution (dpi): 150
[epson] resolution (dpi): 160
[epson] resolution (dpi): 175
[epson] resolution (dpi): 180
[epson] resolution (dpi): 200
[epson] resolution (dpi): 216
[epson] resolution (dpi): 240
[epson] resolution (dpi): 266
[epson] resolution (dpi): 300
[epson] resolution (dpi): 320
[epson] resolution (dpi): 350
[epson] resolution (dpi): 360
[epson] resolution (dpi): 400
[epson] resolution (dpi): 480
[epson] resolution (dpi): 600
[epson] resolution (dpi): 720
[epson] resolution (dpi): 800
[epson] resolution (dpi): 900
[epson] resolution (dpi): 1200
[epson] resolution (dpi): 1600
[epson] resolution (dpi): 1800
[epson] resolution (dpi): 2400
[epson] resolution (dpi): 3200
[epson] maximum scan area: x 27200 y 37440
[epson] fbf tlx 0.000000 tly 0.000000 brx 215.899994 bry 297.179993 [mm]
[epson] send buf, size = 2
[epson] buf[0] 1b .
[epson] buf[1] 44 D
[epson] w_cmd_count = 3
[epson] r_cmd_count = 4
[epson] w_cmd_count = 3
[epson] r_cmd_count = 5
[epson] receive buf, expected = 1, got = 1
[epson] buf[0] 06 .
[epson] send buf, size = 1
[epson] buf[0] 10 .
[epson] w_cmd_count = 4
[epson] r_cmd_count = 5
[epson] w_cmd_count = 4
[epson] r_cmd_count = 6
[epson] receive buf, expected = 1, got = 1
[epson] buf[0] 06 .
[epson] Max. supported color depth = 16
[epson] request_focus_position()
[epson] send buf, size = 2
[epson] buf[0] 1b .
[epson] buf[1] 71 q
[epson] w_cmd_count = 5
[epson] r_cmd_count = 6
[epson] w_cmd_count = 5
[epson] r_cmd_count = 7
[epson] receive buf, expected = 4, got = 4
[epson] buf[0] 02 .
[epson] buf[1] 02 .
[epson] buf[2] 02 .
[epson] buf[3] 00 .
[epson] w_cmd_count = 5
[epson] r_cmd_count = 8
[epson] receive buf, expected = 2, got = 2
[epson] buf[0] 00 .
[epson] buf[1] 40 @
[epson] Focus position = 0x40
[epson] Enabling 'Set Focus' support
[epson] send buf, size = 2
[epson] buf[0] 1b .
[epson] buf[1] 66 f
[epson] w_cmd_count = 6
[epson] r_cmd_count = 8
[epson] w_cmd_count = 6
[epson] r_cmd_count = 9
[epson] receive buf, expected = 4, got = 4
[epson] buf[0] 02 .
[epson] buf[1] 02 .
[epson] buf[2] 2a *
[epson] buf[3] 00 .
[epson] code   02
[epson] status 02
[epson] count  42
[epson] w_cmd_count = 6
[epson] r_cmd_count = 10
[epson] receive buf, expected = 42, got = 42
[epson] buf[0] 01 .
[epson] buf[1] 00 .
[epson] buf[2] 00 .
[epson] buf[3] 00 .
[epson] buf[4] 00 .
[epson] buf[5] 00 .
[epson] buf[6] 00 .
[epson] buf[7] 00 .
[epson] buf[8] 00 .
[epson] buf[9] 00 .
[epson] buf[10] 00 .
[epson] buf[11] 00 .
[epson] buf[12] 00 .
[epson] buf[13] 00 .
[epson] buf[14] 00 .
[epson] buf[15] 00 .
[epson] buf[16] 00 .
[epson] buf[17] 00 .
[epson] buf[18] 00 .
[epson] buf[19] 00 .
[epson] buf[20] 00 .
[epson] buf[21] 00 .
[epson] buf[22] 00 .
[epson] buf[23] 00 .
[epson] buf[24] 00 .
[epson] buf[25] 00 .
[epson] buf[26] 47 G
[epson] buf[27] 54 T
[epson] buf[28] 2d -
[epson] buf[29] 38 8
[epson] buf[30] 32 2
[epson] buf[31] 30 0
[epson] buf[32] 30 0
[epson] buf[33] 20
[epson] buf[34] 20
[epson] buf[35] 20
[epson] buf[36] 20
[epson] buf[37] 20
[epson] buf[38] 20
[epson] buf[39] 20
[epson] buf[40] 20
[epson] buf[41] 20
[epson] scanner model: GT-8200
[epson] close_scanner(fd = 0)
[epson] w_cmd_count = 6
[epson] r_cmd_count = 10
[epson] w_cmd_count = 6
[epson] r_cmd_count = 10
[epson] sane_init, ># For libusb support for unknown scanners use the following command<
[epson] sane_init, ># usb <product ID> <device ID><
[epson] sane_init, ># e.g.:<
[epson] sane_init, >usb 0x4b8 0x110<
[epson] attach_one_usb(libusb:001:004)
[epson] SANE Epson Backend v0.2.45 - 2000-01-09
[epson] attach(libusb:001:004, 3)
[epson] sane_init, ># And for the scanner module, use the following configuration:<
[epson] sane_init, >#usb /dev/usbscanner0<
[epson] sane_init, >#usb /dev/usb/scanner0<
[epson] sane_get_devices()



==>>
The backend at the server side seems to find GT-8200, but can't communicate it to the requesting client.

####
The xinet config, that I tried:
# default: off
# description: The sane server accepts requests
# for network access to a local scanner via the
# network.
service sane-port
{
  port        = 6566
  socket_type = stream
  protocol    = tcp
  wait        = no
  user        = saned
  group       = saned
  server      = /usr/sbin/saned
}


Should I issue a bug report?

Thanks,
Achim

---

### Post by frufo on 2007-11-15
Hello, 

I had a very similar problem with an epson Perfection. However this problem does not seem to be Epson-related. It is a permission problem:

In my Ubuntu (feisty fawn) the permissions of the scanner are set as follows:

crw-rw-r-- 1 root scanner 189, 29 2007-11-15 21:24 030

however although I have added the user saned to the group scanner (and scanning in saned-debug mode works like a charm) it seems that xinetd ONLY sets the group mentioned in its config, which is according to the saned-manpage:

service sane-port
              {
                 port        = 6566
                 socket_type = stream
                 wait        = no
                 user        = saned
                 group       = saned
                 server      = /usr/sbin/saned
              }

Changing it to:

service sane-port
              {
                 port        = 6566
                 socket_type = stream
                 wait        = no
                 user        = saned
                 group       = scanner
                 server      = /usr/sbin/saned
              }

made sane work like a charm....

Hope this helps......

Hartmut

---

### Post by jjalocha on 2008-01-23
Thank you, Hartmut, for your post!

After several weeks of frustration, I was finally able to access my Epson Stylus CX3900 all-in-one over the LAN thanks to your tip.

I don't use xinetd as you, but inetd. Thus the configuration file (/etc/saned.conf) looks different in this case. It was only necessary to change to group 'scanner':

```

sane-port  stream  tcp  nowait  saned.scanner  /usr/local/sbin/saned saned

```

Before that, I had the same problem: Remote host was only able to scan when server was running saned manually in "debug mode":

```

server$ SANE_DEBUG_EPSON=128 saned -d128

```

(Read more about that in [http://penguin-breeder.org/sane/saned/](http://penguin-breeder.org/sane/saned/))

---

### Post by jjalocha on 2008-01-23
I just checked the other solution, and it works perfect, too.

Add 'saned' user to 'scanner' group:

```

$ sudo adduser saned scanner

```

And set the default saned settings in '/etc/saned.conf':

```

sane-port  stream  tcp  nowait  saned.saned  /usr/local/sbin/saned saned

```

Restart inetd, and you're done:

```

$ sudo /etc/init.d/openbsd-inetd restart

```

---

### Post by apos on 2008-04-02
As of the older thread of above the solution is very easy for GUTSY / 7.04.
But the entry for inetd.conf is slightly different and "openbsd-inetd" moved to "inetd":

```
$ sudo adduser saned scanner
```

```
$ vim/nano /etc/saned.conf
# add the following line
sane-port  stream  tcp  nowait  saned.saned  /usr/sbin/saned saned
```

```
$ sudo /etc/init.d/inetd restart
```

Don't forget to add on the SERVER your allowed hosts in /etc/sane/saned.conf.

Don't forget to add on your CLIENTS the server address in /etc/sane/net.conf.

Greets Axel

---

### Post by isoaglib on 2008-05-20
Thanks,
this solution does also work for me.

Could anybody of the package admins setup the packages, so that the xinetd/inetd configs match to the default group name of the scanner device?

At least - now I got everything to work like charm, too.

Thanks,
Isoaglib

---

