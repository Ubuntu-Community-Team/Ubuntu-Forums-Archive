---
title: "ipod help please?"
date: 2005-11-07
forum: Hardware &amp; Laptops
---

### Post by earobinson on 2005-11-07
So I have been trying for a while to get my ipod to work with no success :(

```
root@null:/dev# dmesg | tail
[4453286.838000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000fea0000704938][4453288.045000] sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
[4453289.219000] hw tcp v4 csum failed
[4453423.003000] Warning: /proc/ide/hd?/settings interface is obsolete, and will be removed soon!
[4453676.201000] hw tcp v4 csum failed
[4454210.417000] hw tcp v4 csum failed
[4454355.072000] sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
[4454877.021000] hw tcp v4 csum failed
[4455075.947000] sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
[4455091.974000] hw tcp v4 csum failed
```

```
root@null:/dev# cat /var/log/messages | tail
Nov  7 22:25:13 localhost gconfd (root-25048): Resolved address "xml:readonly:/usr/share/gconf/local.mandatory" to a read-only configuration source at position 1
Nov  7 22:25:13 localhost gconfd (root-25048): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 2
Nov  7 22:25:13 localhost gconfd (root-25048): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 3
Nov  7 22:25:13 localhost gconfd (root-25048): Resolved address "xml:readonly:/usr/share/gconf/local.defaults" to a read-only configuration source at position 4Nov  7 22:25:13 localhost gconfd (root-25048): Resolved address "xml:readonly:/usr/share/gconf/cdd.defaults" to a read-only configuration source at position 5
Nov  7 22:25:13 localhost gconfd (root-25048): Resolved address "xml:readonly:/usr/share/gconf/debian.defaults" to a read-only configuration source at position 6
Nov  7 22:25:13 localhost gconfd (root-25048): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 7
Nov  7 22:25:43 localhost gconfd (root-25048): GConf server is not in use, shutting down.
Nov  7 22:25:43 localhost gconfd (root-25048): Exiting
Nov  7 22:30:53 localhost kernel: [4455075.947000] sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
```

```
root@null:/dev# ls -la /dev/s*
lrwxrwxrwx  1 root root 24 2005-11-06 01:58 /dev/sndstat -> /proc/asound/oss/sndstat
lrwxrwxrwx  1 root root 15 2005-11-06 01:58 /dev/stderr -> /proc/self/fd/2
lrwxrwxrwx  1 root root 15 2005-11-06 01:58 /dev/stdin -> /proc/self/fd/0
lrwxrwxrwx  1 root root 15 2005-11-06 01:58 /dev/stdout -> /proc/self/fd/1

/dev/shm:
total 0
drwxrwxrwt   2 root root 40 2005-11-06 01:58 .
drwxr-xr-x  12 root root  0 2005-11-07 07:36 ..

/dev/snd:
total 0
drwxr-xr-x   2 root root        0 2005-11-06 01:58 .
drwxr-xr-x  12 root root        0 2005-11-07 07:36 ..
crw-rw----   1 root audio 116,  0 2005-11-06 01:58 controlC0
crw-rw----   1 root audio 116, 24 2005-11-06 01:58 pcmC0D0c
crw-rw----   1 root audio 116, 16 2005-11-06 01:58 pcmC0D0p
crw-rw----   1 root audio 116, 25 2005-11-06 01:58 pcmC0D1c
crw-rw----   1 root audio 116, 26 2005-11-06 01:58 pcmC0D2c
crw-rw----   1 root audio 116, 27 2005-11-06 01:58 pcmC0D3c
crw-rw----   1 root audio 116, 20 2005-11-06 01:58 pcmC0D4p
crw-rw----   1 root audio 116, 33 2005-11-06 01:58 timer
```

need anything else?

I know that my firewire is not even there and i have tryed all sorts of modporbes any help?

Thanks for your time

---

### Post by Joe_lurker on 2005-11-08
I don't know if this help but here is the output of /var/log/messages when I attach my Internet Foot:
```
Nov  8 02:13:39 localhost kernel: [4329795.191000] scsi0 : SCSI emulation for IEEE-1394 SBP-2 Devices
Nov  8 02:13:40 localhost kernel: [4329796.296000] ieee1394: sbp2: Logged into SBP-2 device
Nov  8 02:13:40 localhost kernel: [4329796.300000]   Vendor: Apple     Model: iPod              Rev: 1.62
Nov  8 02:13:40 localhost kernel: [4329796.300000]   Type:   Direct-Access                      ANSI SCSI revision: 02
Nov  8 02:13:44 localhost kernel: [4329796.617000] sda: Spinning up disk......ready
Nov  8 02:13:44 localhost kernel: [4329799.663000] SCSI device sda: 7999488 512-byte hdwr sectors (4096 MB)
Nov  8 02:13:44 localhost kernel: [4329799.664000] sda: Write Protect is off
Nov  8 02:13:44 localhost kernel: [4329799.667000] SCSI device sda: drive cache: write through
Nov  8 02:13:44 localhost kernel: [4329799.675000] SCSI device sda: 7999488 512-byte hdwr sectors (4096 MB)
Nov  8 02:13:44 localhost kernel: [4329799.676000] sda: Write Protect is off
Nov  8 02:13:44 localhost kernel: [4329799.679000] SCSI device sda: drive cache: write through
Nov  8 02:13:44 localhost kernel: [4329799.679000]  /dev/scsi/host0/bus0/target0/lun0: [mac] p1 p2 p3
Nov  8 02:13:44 localhost kernel: [4329799.721000] Attached scsi removable disk sda at scsi0, channel 0, id 0, lun 0
Nov  8 02:13:44 localhost scsi.agent[23542]:      sd_mod: loaded sucessfully (for disk)
Nov  8 02:13:44 localhost ieee1394.agent[23578]:      sbp2: already loaded

```
I don't think the "hw tcp v4 csum failed" errors are relivent.  However it might point to a larger problem.  Did you install a fresh install or an upgrade?

-Joe

---

### Post by earobinson on 2005-11-08
fresh, im pretty sure its a kernel 2.6 bug that a lot of people have with firewire (sada is not even there). Im also pretty sure the answer is in modprobe but thats as far as i get :(

---

### Post by Joe_lurker on 2005-11-08
Which kernel?  I am using 2.6.12-9-686 and it works.  I have an IBM ThinkPad with built in firewire.  Where is the output from 'lsmod | grep ohci1394'?

-Joe

---

### Post by earobinson on 2005-11-09
```
earobinson@null:~/Desktop/p2p/amule$ cat /var/log/messages | tail
Nov  9 20:25:03 localhost kernel: [4458223.910000] usb 2-1: USB disconnect, address 77
Nov  9 20:25:03 localhost kernel: [4458223.999000] usb 2-1: new low speed USB device using uhci_hcd and address 78
Nov  9 20:25:03 localhost kernel: [4458224.172000] input: USB HID v1.00 Mouse [HP HP USB WHEEL MOUSE] on usb-0000:00:1d.1-1
Nov  9 20:25:03 localhost input.agent[31971]:      tsdev: already loaded
Nov  9 20:25:03 localhost usb.agent[31987]:      usbhid: already loaded
Nov  9 20:25:04 localhost input.agent[31971]:      mousedev: already loaded
Nov  9 20:25:04 localhost input.agent[32060]:      evdev: already loaded
Nov  9 20:25:04 localhost input.agent[32070]:      evdev: already loaded
Nov  9 20:25:04 localhost input.agent[32084]:      evdev: already loaded
Nov  9 20:25:04 localhost input.agent[31971]:      evdev: already loaded
```

yup same kernel  

```
ohci1394               34356  0
ieee1394              100792  2 ohci1394,sbp2

```

---

