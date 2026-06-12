---
title: "Unable to pair with bluetooth headphones"
date: 2008-09-13
forum: Hardware
---

### Post by jdpipe on 2008-09-13
I am unable to pair Ubuntu Hardy with my Nokia BH-501 headset. It seems that for some reason the connection is timing out before I can enter the passkey, and I can't work out a way of automatically sending the passkey quickly enough. Just after entering the 'hcitool auth' command, bluetooth-applet briefly flashes a dialog asking for the passkey, but I can respond to it quickly enough before it disappears again.

Possibly related to bug #230932 but I can't be sure.

I type the following from the console:

john@roadwork:~$ sudo hcitool cc  00:0D:3C:A6:E8:1C
john@roadwork:~$ sudo hcitool auth  00:0D:3C:A6:E8:1C 
HCI authentication request failed: Connection timed out
john@roadwork:~$ 

In a separate window, I get the following output from hcidump -X -V

< HCI Command: Create Connection (0x01|0x0005) plen 13
    bdaddr 00:0D:3C:A6:E8:1C ptype 0xcc18 rswitch 0x01 clkoffset 0x0000
    Packet type: DM1 DM3 DM5 DH1 DH3 DH5 
> HCI Event: Command Status (0x0f) plen 4
    Create Connection (0x01|0x0005) status 0x00 ncmd 1
> HCI Event: Connect Complete (0x03) plen 11
    status 0x00 handle 11 bdaddr 00:0D:3C:A6:E8:1C type ACL encrypt 0x00
< ACL data: handle 11 flags 0x02 dlen 10
    L2CAP(s): Info req: type 2
< HCI Command: Read Remote Supported Features (0x01|0x001b) plen 2
    handle 11
> HCI Event: Read Remote Supported Features (0x0b) plen 11
    status 0x00 handle 11
    Features: 0xff 0xff 0x8f 0x78 0x18 0x18 0x00 0x80
> HCI Event: Command Status (0x0f) plen 4
    Read Remote Supported Features (0x01|0x001b) status 0x00 ncmd 1
< HCI Command: Write Link Policy Settings (0x02|0x000d) plen 4
    handle 11 policy 0x0f
    Link policy: RSWITCH HOLD SNIFF PARK 
> HCI Event: Command Complete (0x0e) plen 6
    Write Link Policy Settings (0x02|0x000d) ncmd 1
    status 0x00 handle 11
< HCI Command: Remote Name Request (0x01|0x0019) plen 10
    bdaddr 00:0D:3C:A6:E8:1C mode 2 clkoffset 0x0000
> HCI Event: Command Status (0x0f) plen 4
    Remote Name Request (0x01|0x0019) status 0x00 ncmd 1
> HCI Event: Page Scan Repetition Mode Change (0x20) plen 7
    bdaddr 00:0D:3C:A6:E8:1C mode 1
> HCI Event: Max Slots Change (0x1b) plen 3
    handle 11 slots 5
> ACL data: handle 11 flags 0x02 dlen 16
    L2CAP(s): Info rsp: type 2 result 0
      Extended feature mask 0x0000
> HCI Event: Remote Name Req Complete (0x07) plen 255
    status 0x00 bdaddr 00:0D:3C:A6:E8:1C name 'Nokia BH-501'
> HCI Event: Number of Completed Packets (0x13) plen 5
    handle 11 packets 1
< HCI Command: Authentication Requested (0x01|0x0011) plen 2
    handle 11
> HCI Event: Command Status (0x0f) plen 4
    Authentication Requested (0x01|0x0011) status 0x00 ncmd 1
> HCI Event: Link Key Request (0x17) plen 6
    bdaddr 00:0D:3C:A6:E8:1C
< HCI Command: Link Key Request Negative Reply (0x01|0x000c) plen 6
    bdaddr 00:0D:3C:A6:E8:1C
> HCI Event: PIN Code Request (0x16) plen 6
    bdaddr 00:0D:3C:A6:E8:1C
> HCI Event: Command Complete (0x0e) plen 10
    Link Key Request Negative Reply (0x01|0x000c) ncmd 1
    status 0x00 bdaddr 00:0D:3C:A6:E8:1C
< HCI Command: Disconnect (0x01|0x0006) plen 3
    handle 11 reason 0x13
    Reason: Remote User Terminated Connection
> HCI Event: Command Status (0x0f) plen 4
    Disconnect (0x01|0x0006) status 0x00 ncmd 1
> HCI Event: Disconn Complete (0x05) plen 4
    status 0x00 handle 11 reason 0x16
    Reason: Connection Terminated by Local Host

I have previously been able to pair this headphone with Ubuntu and have used it successfully to listen to music. It currently works fine with my phone. I am placing it it in pairing mode before running the above commands. The manual says that the required pairing passkey should be '0000', and I edited /etc/bluetooth/hcid.conf to use that value.

Any thoughts?

Cheers
JP

---

### Post by jdpipe on 2008-09-13
Looks like this has been reported as a bug, so I'll follow it up over there:
[https://bugs.launchpad.net/ubuntu/+source/bluez-utils/+bug/241000](https://bugs.launchpad.net/ubuntu/+source/bluez-utils/+bug/241000)

---

### Post by IntuitiveNipple on 2008-09-13
In the meantime give [Blueman](http://blueman.tuxfamily.org/) a try, it handles many connection issues very well. There's a recent build of it in the [Blueman Launchpad repository](https://edge.launchpad.net/~blueman/+archive).

---

### Post by jdpipe on 2008-09-13
Interesting :-)

When I ran Blueman and attempted to connect to the device, even when the device was in pairing mode, it showed cycling connect/disconnect every second or so. But when using Blueman I asked to 'connect to Audio service --> Headset' it then *stayed* connected, and this time asked me to enter the passkey. So now I am paired with the device, it seems. Thanks very much!

---

### Post by IntuitiveNipple on 2008-09-13
When I found Blueman it was like a revelation - it just gets things done. I like it so much I joined the development team although recently my contribution has been limited to trying to isolate a very obscure bug that causes a Bluetooth mouse to be registered multiple times, and de-registered too, which eventually leads to a kernel RIP panic.

---

### Post by suyog on 2009-10-12
Hi,
I am trying to connect my BH-501 in Ubuntu 9.04.
I am able to connect to audio sink , which I guess is A2DP.
But How do i stream music to headset? When i play music , its played by laptop speakers.

I am using latest build from blueman 1.20. I really liked improvements in 1.20 , as everything else just works very easily.

Please let me know if you know solution.

Suyog

---

### Post by walmis on 2009-10-14
> **suyog said:**
> Hi,
I am trying to connect my BH-501 in Ubuntu 9.04.
I am able to connect to audio sink , which I guess is A2DP.
But How do i stream music to headset? When i play music , its played by laptop speakers.

I am using latest build from blueman 1.20. I really liked improvements in 1.20 , as everything else just works very easily.

Please let me know if you know solution.

Suyog

You should install a program called pavucontrol. Then, after connecting to your headset you can move audio streams from programs to your headset.

---

### Post by suyog on 2009-10-15
I was able to do it !!! I followed How to as described in link
[http://jackycxh.blog.35.cn/2009/07/26/howto-use-a-bluetooth-headset-with-ubuntu-jaunty/](http://jackycxh.blog.35.cn/2009/07/26/howto-use-a-bluetooth-headset-with-ubuntu-jaunty/)

---

