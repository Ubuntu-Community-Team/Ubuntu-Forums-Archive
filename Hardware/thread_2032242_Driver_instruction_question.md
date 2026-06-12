---
title: "Driver instruction question"
date: 2012-07-23
forum: Hardware
---

### Post by raysa on 2012-07-23
I need to instal a driver that I have downloaded. The compiling instructions are just about followable, but I'm baffled by what the README file calls "Prerequisites".  It says:

[INDENT]You need the Linux kernel sources installed on the build machine, and make sure that the version of the running kernel must match the installed kernel sources. If you don't have the kernel sources, you can get it from [www.kernel.org](www.kernel.org).

Note: Please make sure the kernel is built with one of the "Support for
Host-side, EHCI, OHCI, or UHCI" option support.[/INDENT]

What are "kernel sources" and how can I check that they match?  I can see that the kernel on my machine is 3.2.0.26 generic (x86_64), but I don't understand what this instruction is telling me to check. 

And how do I do that other bit about "Support for Host-side etc"?

Thanks, Ray

---

### Post by QIII on 2012-07-23
What is the driver you are installing?

---

### Post by raysa on 2012-07-23
It's for an ASIX usb ethernet adapter, AX88772A.  Laughingly called "Plugable" and claimed to be fine with Linux.

Ray

---

### Post by Toz on 2012-07-23
The kernel config file for the current kernel is located in the /boot directory. You can view the file:
```
less /boot/config-$(uname -r)
```
...or search it for those options:
```
cat /boot/config-$(uname -r) | grep -i [eou]hci
```

Looks like they are included in 3.2.0-27-generic-pae (x86).

---

### Post by raysa on 2012-07-24
Thanks Toz. Found it OK, although I'm not sure what I'm looking for. But the second command confirms that the correct options are in place, so presumably I'm OK with the "Prerequisites".

Next question, please: 
There was a suggestion that the required driver asix.ko might be included in recent distros, so I did a search and sure enough asix.ko is present in my lib/modules/3.2.0.26-generic/kernel/drivers/net/usb directory. 
Does this mean I don't need to instal/compile the one I've downloaded (not something I'm familiar with)? 
But the adaptor doesn't work as is, so what do I need to do?

Thanks,
Ray

---

### Post by Toz on 2012-07-24
If the module is not already loaded:
```
lsmod | grep asix
```
...try loading it:
```
sudo modprobe asix
```

Then confirm with:
```
lsmod | grep asix
```

---

### Post by raysa on 2012-07-24
Thanks Toz. The module wan't loaded, but following your advice it is now.

But the adaptor still won't connect - it shows up in network manager but the whirly thing just keeps whirling and there's no connection.
What to try now?

Thanks, Ray

---

### Post by Toz on 2012-07-24
Lets have a look at some more information:
```
modinfo asix
```
```
nm-tool
```

Here is a guide that might help: [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide")

---

### Post by raysa on 2012-07-24
Thanks again, Toz.

Output from modinfo asix:

```
ray@ray-desktop:~$ modinfo asix
filename:       /lib/modules/3.2.0-27-generic/kernel/drivers/net/usb/asix.ko
license:        GPL
description:    ASIX AX8817X based USB 2.0 Ethernet Devices
version:        08-Nov-2011
author:         David Hollis
srcversion:     F32EB5E70237F69E7A1A7D1
alias:          usb:v0B95p7E2Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0pA877d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14EApAB11d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B95p772Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v05ACp1402d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp5055d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04BBp0930d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0039d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C05d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C05d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1557p7720d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13B1p0018d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0160d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B95p1780d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B95p7720d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B95p772Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04F1p3008d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1631p6200d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1189p0893d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp0017d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0056d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v6189p182Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p006Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p003Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0557p2009d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v08DDp90FFd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p420Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B95p1720d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p1A00d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0846p1040d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v077Bp2226d*dc*dsc*dp*ic*isc*ip*
depends:        usbnet
intree:         Y
vermagic:       3.2.0-27-generic SMP mod_unload modversions 
ray@ray-desktop:~$
```


The output from nm-tool depends on whether there is any connection at all.
When there is connection, it is hopelessly slow and unreliable, and the output is:

```
State: connecting

- Device: eth1  [Wired connection 2] -------------------------------------------
  Type:              Wired
  Driver:            asix
  State:             connecting (getting IP configuration)
  Default:           no
  HW Address:        00:50:B6:0B:52:3B

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on
```


When there is no connection, the output is:

```
State: connected (global)

- Device: eth1  [Wired connection 2] -------------------------------------------
  Type:              Wired
  Driver:            asix
  State:             connected
  Default:           yes
  HW Address:        00:50:B6:0B:52:3B

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.66
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254
```

I've looked at the "Shooting Guide" link, but that seems to be mostly about wireless probs rather than wired, and I couldn't see anything that I recognised (maybe because I am very non-tech!).

Sorry - they are the wrong way round. Hope it's clear which is which.

Thanks, Ray

---

### Post by Toz on 2012-07-24
Oh, I see. Its not a wireless device. My bad.

When its connected and slow, are there any error messages showing up in /var/log/syslog or /var/log/dmesg?

And also, have you confirmed that the cable you are using and the port it is connected to are good?

---

### Post by raysa on 2012-07-25
The cable is fine, Toz.  I've tried changing it, and both cables work fine with another computer.  The usb port seems fine, too - no probs with anything else connected to it.

I haven't had any connection at all today, so the only /var/log files produced relate to a no-connection state.  These files are miles long, but in case it's useful, here's just the start of the syslog:

Jul 25 07:25:22 ray-desktop rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="834" x-info="http://www.rsyslog.com"] rsyslogd was HUPed
Jul 25 07:25:22 ray-desktop NetworkManager[837]: <info> (eth1): IP6 addrconf timed out or failed.
Jul 25 07:25:22 ray-desktop NetworkManager[837]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Jul 25 07:25:22 ray-desktop NetworkManager[837]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) started...
Jul 25 07:25:22 ray-desktop NetworkManager[837]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Jul 25 07:25:24 ray-desktop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 19
Jul 25 07:25:43 ray-desktop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
Jul 25 07:25:44 ray-desktop anacron[991]: Job `cron.daily' terminated (mailing output)
Jul 25 07:25:44 ray-desktop anacron[991]: Tried to mail output of job `cron.daily', but mailer process (/usr/sbin/sendmail) exited with ststus 255
Jul 25 07:25:44 ray-desktop anacron[991]: Normal exit (1 job run)
Jul 25 07:25:47 ray-desktop NetworkManager[837]: <warn> (eth1): DHCPv4 request timed out.
Jul 25 07:25:47 ray-desktop NetworkManager[837]: <info> (eth1): canceled DHCP transaction, DHCP client pid 1833
Jul 25 07:25:47 ray-desktop NetworkManager[837]: <info> Activation (eth1) Stage 4 of 5 (IPv4 Configure Timeout) scheduled...
Jul 25 07:25:47 ray-desktop NetworkManager[837]: <info> Activation (eth1) Stage 4 of 5 (IPv4 Configure Timeout) started...
Jul 25 07:25:47 ray-desktop NetworkManager[837]: <info> (eth1): device state change: ip-config -> failed (reason 'ip-config-unavailable') [70 120 5]
Jul 25 07:25:48 ray-desktop NetworkManager[837]: <warn> Activation (eth1) failed.
Jul 25 07:25:48 ray-desktop NetworkManager[837]: <info> Activation (eth1) Stage 4 of 5 (IPv4 Configure Timeout) complete.
Jul 25 07:25:48 ray-desktop NetworkManager[837]: <info> (eth1): device state change: failed -> disconnected (reason 'none') [120 30 0]
Jul 25 07:25:48 ray-desktop NetworkManager[837]: <info> (eth1): deactivating device (reason 'none') [0]
Jul 25 07:25:50 ray-desktop NetworkManager[837]: <info> Auto-activating connection 'Wired connection 2'.
Jul 25 07:25:50 ray-desktop NetworkManager[837]: <info> Activation (eth1) starting connection 'Wired connection 2'
Jul 25 07:25:50 ray-desktop NetworkManager[837]: <info> (eth1): device state change: disconnected -> prepare (reason 'none') [30 40 0]


Thanks, Ray
PS: the adaptor itself seems OK - tried it elsewhere and got connection.

---

### Post by Toz on 2012-07-25
Your device is eth1. Do you have an eth0? Can you post back the full results of **nm-tool**? If you do have an eth0, have you tried disabling it?

---

### Post by raysa on 2012-07-26
eth0 is the original built-in adaptor. It was only when that started playing up that I plugged in the usb alternative, which named itself eth1. But connection was only ever with one or the other enabled, never both together.

But although this problem was not solved, the situation has moved on. After comparative internet speed tests and router-pinging, I strongly suspected a computer hardware fault, and as the machine is still under warranty I contacted the Acer technical helpline. 

Followed their advice and now the computer is completely buggered - won't even boot! So it's on its way back for repair/replacement, and I'm back on the spare laptop, which connects to the router like a dream.

Thanks for your help in trying to sort this out.

---

