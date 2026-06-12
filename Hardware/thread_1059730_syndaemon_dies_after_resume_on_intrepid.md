---
title: "syndaemon dies after resume on intrepid"
date: 2009-02-04
forum: Hardware
---

### Post by alias_knagg on 2009-02-04
I have been digging into this for a while now, and I'm pretty certain it has not been mentioned anywhere before.

The situation:

Ubuntu 8.10, 2.6.27-9-generic, dell inspiron 6000, xserver-xorg-input-synaptics 0.15.2-0ubuntu7

# cat /etc/hal/fdi/policy/shmconfig.fdi
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
 <device>
  <match key="input.x11_driver" string="synaptics">
   <merge key="input.x11_options.SHMConfig" type="string">True</merge>
  </match>
 </device>
</deviceinfo>
No active SHM in xorg.conf

syndaemon starts nicely by hand, and from system->prefs->session

# ps aux | grep sy[n]
root     19030  0.4  0.0   2988   508 ?        Ss   09:42   0:09 syndaemon -d -t

However, after a resume it is just gone.

With the -S option as mentioned in:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/295236](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/295236)
it survives, but stops working after resume.

I have tried a workaround by way of a small script:
/usr/lib/pm-utils/sleep.d/55syndaemon-resume
my log lines verifies that it does get called, and the right function executed, but apparently it fires too early in the resume sequence since I am then greeted with an error on the root terminal.
Almost identical to bug 295236.

# X Error of failed request:  BadDevice, invalid or uninitialized input device
  Major opcode of failed request:  146 (XInputExtension)
  Minor opcode of failed request:  4 (X_CloseDevice)
  Serial number of failed request:  22691
  Current serial number in output stream:  22692

What to try now?
Any suggestions?

---

### Post by mbeierl on 2009-02-05
I can also confirm that on my AMD64 Intrepid, syndaemon is no longer able to disable the touchpad after resume.

If I start a new syndaemon from the command line, I see:
```

/usr/bin/syndaemon -i 10 -S
Disable
Enable
kDisable
Enable
Disable
Enable

```
but all the while, the mouse pointer still moves when I brush the touchpad.

---

### Post by alias_knagg on 2009-02-06
Just posted a bug:
[https://bugs.launchpad.net/ubuntu/+source/xfree86-driver-synaptics/+bug/326117](https://bugs.launchpad.net/ubuntu/+source/xfree86-driver-synaptics/+bug/326117)

---

