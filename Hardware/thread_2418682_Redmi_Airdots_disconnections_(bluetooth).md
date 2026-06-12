---
title: "Redmi Airdots disconnections (bluetooth)"
date: 2019-05-09
forum: Hardware
---

### Post by mohegan on 2019-05-09
I can connect the Redmi Airdots as headset (bluetooth) but It disconnect after few second. I tried with my computer and windows 10 and it works well (no disconnection). I tried with fedora and manjaro on live usb and I have the same disconnection.

Journactlv :
> mai 09 21:15:29 jack-XPS-L322X kernel: input: MX Anywhere 2 Keyboard as /devices/virtual/misc/uhid/0005:046D:B01F.000C/input/input55
mai 09 21:15:29 jack-XPS-L322X kernel: input: MX Anywhere 2 Mouse as /devices/virtual/misc/uhid/0005:046D:B01F.000C/input/input56
mai 09 21:15:29 jack-XPS-L322X kernel: hid-generic 0005:046D:B01F.000C: input,hidraw0: BLUETOOTH HID v0.03 Keyboard [MX Anywhere 2] on 7C:5C:F8:3B:B0:72
mai 09 21:15:29 jack-XPS-L322X systemd-logind[797]: Watching system buttons on /dev/input/event12 (MX Anywhere 2 Keyboard)
mai 09 21:15:31 jack-XPS-L322X PackageKit[4791]: daemon quit
mai 09 21:15:31 jack-XPS-L322X systemd[1]: packagekit.service: Main process exited, code=killed, status=15/TERM
mai 09 21:15:31 jack-XPS-L322X systemd[1]: packagekit.service: Succeeded.
mai 09 21:15:39 jack-XPS-L322X bluetoothd[4864]: Authentication attempt without agent
mai 09 21:15:39 jack-XPS-L322X bluetoothd[4864]: hfp_hf rejected E8:EC:A3:01:4E:BD: org.bluez.Error.Rejected
mai 09 21:15:39 jack-XPS-L322X bluetoothd[4864]: Authentication attempt without agent
mai 09 21:15:39 jack-XPS-L322X bluetoothd[4864]: Access denied: org.bluez.Error.Rejected


I tried few things but it can't work ! Please, help me !

---

### Post by milosb7931 on 2019-12-10
Hey, try this answer. I succeed to solve it with it:  [https://askubuntu.com/a/861247/616830](https://askubuntu.com/a/861247/616830)

---

