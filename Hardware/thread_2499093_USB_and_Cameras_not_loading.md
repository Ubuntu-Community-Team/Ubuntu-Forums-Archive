---
title: "USB and Cameras not loading"
date: 2024-07-11
forum: Hardware
---

### Post by Jonners59 on 2024-07-11
I have just hit a problem with using my built-in and USB cameras, and also my memory/USB sticks.  First noticed when I had to attend a TEAMS call, and all I could get was the virtualcamera, and then I tried my USB storage device.  Now I know they all work and the USB sockets are fine as they all work perfectly in the Windows OS.

Everything is iup to date, and I have tried everything I can find on the various forums.

[HTML]uname -aLinux GF63-Thin-9RCX 6.8.0-36-generic #36-Ubuntu SMP PREEMPT_DYNAMIC Mon Jun 10 10:49:14 UTC 2024 x86_64 x86_64 x86_64 GNU/Linux[/HTML]


```
lsusb -v | grep CameraCouldn't open device, some information will be missing
Couldn't open device, some information will be missing
Couldn't open device, some information will be missing
        wTerminalType      0x0201 Camera Sensor
Couldn't open device, some information will be missing
Bus 001 Device 018: ID 05a3:9331 ARC International Camera
  idProduct          0x9331 Camera
  iManufacturer           1 HD Web Camera
  iProduct                2 HD Web Camera
        wTerminalType      0x0201 Camera Sensor
Couldn't open device, some information will be missing
Couldn't open device, some information will be missing

```

The two cameras are listed.  The BISON is the plug-in USB camera and the ARC is the built-in.  Note that in the ABOVE output the Bison is missing.  It was there, but disappeared.
```
sudo lsusb | grep -i cam
Bus 001 Device 011: ID 5986:211b Bison Electronics Inc. HD Webcam
Bus 001 Device 018: ID 05a3:9331 ARC International Camera

```

```
udo lshw -class video
  *-display                 
       description: VGA compatible controller
       product: CoffeeLake-H GT2 [UHD Graphics 630]
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       logical name: /dev/fb0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list rom fb
       configuration: depth=32 driver=i915 latency=0 resolution=1920,1080
       resources: irq:148 memory:a2000000-a2ffffff memory:80000000-8fffffff ioport:6000(size=64) memory:c0000-dffff

```

```
sudo dmesg | grep -i 'usb'
[ 4929.051048] usb 1-3: USB disconnect, device number 2
[ 4967.793851] usb 2-4: USB disconnect, device number 2
[ 4967.891586] usb 1-4: USB disconnect, device number 3
[ 4969.901643] usb 1-3: new high-speed USB device number 6 using xhci_hcd
[ 4970.048119] usb 1-3: New USB device found, idVendor=05a3, idProduct=9331, bcdDevice= 1.05
[ 4970.048124] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 4970.048126] usb 1-3: Product: HD Web Camera
[ 4970.048128] usb 1-3: Manufacturer: HD Web Camera
[ 4970.048129] usb 1-3: SerialNumber: Ucamera001
[ 4970.048358] usb 1-3: Device is not authorized for usage
[ 4971.291730] usb 2-5: USB disconnect, device number 4
[ 5051.857390] usb 1-3: USB disconnect, device number 6
[ 5303.515660] usb 1-3: new high-speed USB device number 7 using xhci_hcd
[ 5303.642870] usb 1-3: New USB device found, idVendor=05a3, idProduct=9331, bcdDevice= 1.05
[ 5303.642881] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 5303.642886] usb 1-3: Product: HD Web Camera
[ 5303.642889] usb 1-3: Manufacturer: HD Web Camera
[ 5303.642892] usb 1-3: SerialNumber: Ucamera001
[ 5303.643251] usb 1-3: Device is not authorized for usage
[ 5489.879202] usb 1-3: USB disconnect, device number 7
[ 5490.130458] usb 1-3: new high-speed USB device number 8 using xhci_hcd
[ 5490.259504] usb 1-3: New USB device found, idVendor=05a3, idProduct=9331, bcdDevice= 1.05
[ 5490.259517] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 5490.259523] usb 1-3: Product: HD Web Camera
[ 5490.259527] usb 1-3: Manufacturer: HD Web Camera
[ 5490.259531] usb 1-3: SerialNumber: Ucamera001
[ 5490.259952] usb 1-3: Device is not authorized for usage
[ 5521.774381] usb 2-5: new SuperSpeed USB device number 5 using xhci_hcd
[ 5521.789677] usb 2-5: New USB device found, idVendor=05e3, idProduct=0756, bcdDevice=20.11
[ 5521.789689] usb 2-5: New USB device strings: Mfr=3, Product=4, SerialNumber=5
[ 5521.789694] usb 2-5: Product: USB Storage
[ 5521.789697] usb 2-5: Manufacturer: Genesys Logic
[ 5521.789701] usb 2-5: SerialNumber: 000000002011
[ 5521.790148] usb 2-5: Device is not authorized for usage
[ 5620.854823] usb 1-11: USB disconnect, device number 4
[ 5623.442458] usb 1-11: new high-speed USB device number 10 using xhci_hcd
[ 5623.585903] usb 1-11: New USB device found, idVendor=5986, idProduct=211b, bcdDevice= 3.04
[ 5623.585914] usb 1-11: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 5623.585919] usb 1-11: Product: HD Webcam
[ 5623.585923] usb 1-11: Manufacturer: SunplusIT Inc
[ 5623.586323] usb 1-11: Device is not authorized for usage
[ 5639.551281] usb 1-11: USB disconnect, device number 10
[ 5645.547806] usb 1-11: new high-speed USB device number 11 using xhci_hcd
[ 5645.683912] usb 1-11: New USB device found, idVendor=5986, idProduct=211b, bcdDevice= 3.04
[ 5645.683923] usb 1-11: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 5645.683928] usb 1-11: Product: HD Webcam
[ 5645.683932] usb 1-11: Manufacturer: SunplusIT Inc
[ 5645.687781] usb 1-11: Device is not authorized for usage
[ 5694.459244] usb 1-3: USB disconnect, device number 8
[ 5694.711573] usb 1-3: new high-speed USB device number 12 using xhci_hcd
[ 5694.841648] usb 1-3: New USB device found, idVendor=05a3, idProduct=9331, bcdDevice= 1.05
[ 5694.841657] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 5694.841661] usb 1-3: Product: HD Web Camera
[ 5694.841664] usb 1-3: Manufacturer: HD Web Camera
[ 5694.841667] usb 1-3: SerialNumber: Ucamera001
[ 5694.841982] usb 1-3: Device is not authorized for usage
[ 5857.813522] usb 1-3: USB disconnect, device number 12
[ 5858.063006] usb 1-3: new high-speed USB device number 13 using xhci_hcd
[ 5858.192002] usb 1-3: New USB device found, idVendor=05a3, idProduct=9331, bcdDevice= 1.05
[ 5858.192008] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 5858.192010] usb 1-3: Product: HD Web Camera
[ 5858.192011] usb 1-3: Manufacturer: HD Web Camera
[ 5858.192013] usb 1-3: SerialNumber: Ucamera001
[ 5858.192180] usb 1-3: Device is not authorized for usage
[ 6127.757734] usb 1-3: USB disconnect, device number 13
[ 6128.008070] usb 1-3: new high-speed USB device number 14 using xhci_hcd
[ 6128.137255] usb 1-3: New USB device found, idVendor=05a3, idProduct=9331, bcdDevice= 1.05
[ 6128.137266] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 6128.137271] usb 1-3: Product: HD Web Camera
[ 6128.137274] usb 1-3: Manufacturer: HD Web Camera
[ 6128.137278] usb 1-3: SerialNumber: Ucamera001
[ 6128.137645] usb 1-3: Device is not authorized for usage
[ 6957.325030] usb 1-3: USB disconnect, device number 14
[ 6957.577784] usb 1-3: new high-speed USB device number 15 using xhci_hcd
[ 6957.704981] usb 1-3: New USB device found, idVendor=05a3, idProduct=9331, bcdDevice= 1.05
[ 6957.704993] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 6957.704998] usb 1-3: Product: HD Web Camera
[ 6957.705002] usb 1-3: Manufacturer: HD Web Camera
[ 6957.705006] usb 1-3: SerialNumber: Ucamera001
[ 6957.705417] usb 1-3: Device is not authorized for usage
[ 7006.565774] usb 2-5: USB disconnect, device number 5
[ 7008.533101] usb 2-5: new SuperSpeed USB device number 6 using xhci_hcd
[ 7008.548374] usb 2-5: New USB device found, idVendor=05e3, idProduct=0756, bcdDevice=20.11
[ 7008.548385] usb 2-5: New USB device strings: Mfr=3, Product=4, SerialNumber=5
[ 7008.548388] usb 2-5: Product: USB Storage
[ 7008.548392] usb 2-5: Manufacturer: Genesys Logic
[ 7008.548394] usb 2-5: SerialNumber: 000000002011
[ 7008.548756] usb 2-5: Device is not authorized for usage
[ 7645.302604] usb 1-3: USB disconnect, device number 15
[ 7645.554215] usb 1-3: new high-speed USB device number 16 using xhci_hcd
[ 7645.683390] usb 1-3: New USB device found, idVendor=05a3, idProduct=9331, bcdDevice= 1.05
[ 7645.683405] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 7645.683411] usb 1-3: Product: HD Web Camera
[ 7645.683416] usb 1-3: Manufacturer: HD Web Camera
[ 7645.683421] usb 1-3: SerialNumber: Ucamera001
[ 7645.683906] usb 1-3: Device is not authorized for usage
[ 8192.124025] usb 1-3: USB disconnect, device number 16
[ 8192.377590] usb 1-3: new high-speed USB device number 17 using xhci_hcd
[ 8192.505587] usb 1-3: New USB device found, idVendor=05a3, idProduct=9331, bcdDevice= 1.05
[ 8192.505596] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 8192.505601] usb 1-3: Product: HD Web Camera
[ 8192.505605] usb 1-3: Manufacturer: HD Web Camera
[ 8192.505608] usb 1-3: SerialNumber: Ucamera001
[ 8192.505957] usb 1-3: Device is not authorized for usage
[ 9429.232241] usb 1-3: USB disconnect, device number 17
[ 9429.484315] usb 1-3: new high-speed USB device number 18 using xhci_hcd
[ 9429.612515] usb 1-3: New USB device found, idVendor=05a3, idProduct=9331, bcdDevice= 1.05
[ 9429.612528] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 9429.612533] usb 1-3: Product: HD Web Camera
[ 9429.612537] usb 1-3: Manufacturer: HD Web Camera
[ 9429.612541] usb 1-3: SerialNumber: Ucamera001
[ 9429.612964] usb 1-3: Device is not authorized for usage
[10056.309495] usbcore: deregistering interface driver uvcvideo
[10056.378225] usbcore: registered new interface driver uvcvideo



```



This changes nothing
```
systemctl --user restart pipewire

```
neither does this...
```
S[COLOR=#0C0D0E][FONT=ui-monospace]udo modprobe -r uvcvideo && sudo modprobe uvcvideo[/FONT][/COLOR]
```

---

### Post by #&amp;thj^% on 2024-07-11
Will this show it?
```
usbguard list-devices |grep block

```

EDIT: if it shows then my example may help
```
usbguard list-devices|grep 45: 
[COLOR="#FF0000"]45: block id 05e3:0749[/COLOR] serial "000000001532" name "USB3.0 Card Reader" hash "4CAepOp1f7y/qrb/BV/uvBKcDD3WjjZp5fKWyYo9b60=" parent-hash "VXFbt2m/i5krELu+kCSJysCj+m3eetVv3nfC72o9ceg=" via-port "2-2.2.2.3" with-interface 08:06:50 with-connect-type "unknown"

```
To allow it I use:
```
usbguard allow-device -p 45  

```
Now:
```
usbguard list-devices|grep 45: 
45: allow id 05e3:0749 serial "000000001532" name "USB3.0 Card Reader" hash "4CAepOp1f7y/qrb/BV/uvBKcDD3WjjZp5fKWyYo9b60=" parent-hash "VXFbt2m/i5krELu+kCSJysCj+m3eetVv3nfC72o9ceg=" via-port "2-2.2.2.3" with-interface 08:06:50 with-connect-type "unknown"

```

Gaul Dang It I forgot to show this as a help:
```
usbguard --help
 Usage: usbguard [OPTIONS] <command> [COMMAND OPTIONS] ...

 Options:

 Commands:
  get-parameter <name>           Get the value of a runtime parameter.
  set-parameter <name> <value>   Set the value of a runtime parameter.
  list-devices                   List all USB devices recognized by the USBGuard daemon.
  allow-device <id|rule|p-rule>  Authorize a device to interact with the system.
  block-device <id|rule|p-rule>  Deauthorize a device.
  reject-device <id|rule|p-rule> Deauthorize and remove a device from the system.

  list-rules                     List the rule set (policy) used by the USBGuard daemon.
  append-rule <rule>             Append a rule to the rule set.
  remove-rule <id>               Remove a rule from the rule set.

  generate-policy                Generate a rule set (policy) based on the connected USB devices.
  watch                          Watch for IPC interface events and print them to stdout.
  read-descriptor                Read a USB descriptor from a file and print it in human-readable form.

  add-user <name>                Add USBGuard IPC user/group (requires root privileges)
  remove-user <name>             Remove USBGuard IPC user/group (requires root privileges)


```

---

### Post by Jonners59 on 2024-07-12
Thank you.  That hit the button.  I didn't go through giving access as you showed, but instead just uninstalled Usbguard.

I have now discovered that sone directory permissions have changed too.  I tried to tidy up my desktop and update sone files and they won't save or move directory.  I.e. from Desktop to a directory in Documents.  Never ends!  &#128557;&#128557;



> **1fallen said:**
> Will this show it?
```
usbguard list-devices |grep block

```

EDIT: if it shows then my example may help
```
usbguard list-devices|grep 45: 
[COLOR="#FF0000"]45: block id 05e3:0749[/COLOR] serial "000000001532" name "USB3.0 Card Reader" hash "4CAepOp1f7y/qrb/BV/uvBKcDD3WjjZp5fKWyYo9b60=" parent-hash "VXFbt2m/i5krELu+kCSJysCj+m3eetVv3nfC72o9ceg=" via-port "2-2.2.2.3" with-interface 08:06:50 with-connect-type "unknown"

```
To allow it I use:
```
usbguard allow-device -p 45  

```
Now:
```
usbguard list-devices|grep 45: 
45: allow id 05e3:0749 serial "000000001532" name "USB3.0 Card Reader" hash "4CAepOp1f7y/qrb/BV/uvBKcDD3WjjZp5fKWyYo9b60=" parent-hash "VXFbt2m/i5krELu+kCSJysCj+m3eetVv3nfC72o9ceg=" via-port "2-2.2.2.3" with-interface 08:06:50 with-connect-type "unknown"

```

Gaul Dang It I forgot to show this as a help:
```
usbguard --help
 Usage: usbguard [OPTIONS] <command> [COMMAND OPTIONS] ...

 Options:

 Commands:
  get-parameter <name>           Get the value of a runtime parameter.
  set-parameter <name> <value>   Set the value of a runtime parameter.
  list-devices                   List all USB devices recognized by the USBGuard daemon.
  allow-device <id|rule|p-rule>  Authorize a device to interact with the system.
  block-device <id|rule|p-rule>  Deauthorize a device.
  reject-device <id|rule|p-rule> Deauthorize and remove a device from the system.

  list-rules                     List the rule set (policy) used by the USBGuard daemon.
  append-rule <rule>             Append a rule to the rule set.
  remove-rule <id>               Remove a rule from the rule set.

  generate-policy                Generate a rule set (policy) based on the connected USB devices.
  watch                          Watch for IPC interface events and print them to stdout.
  read-descriptor                Read a USB descriptor from a file and print it in human-readable form.

  add-user <name>                Add USBGuard IPC user/group (requires root privileges)
  remove-user <name>             Remove USBGuard IPC user/group (requires root privileges)


```

---

### Post by ajgreeny on 2024-07-12
It sounds as if some files or folders in your home may no longer be owned by you which will cause many difficulties so run command 
**ls -la**
to see if anything obvious shows in that list that is owned by root or some other user.

Have you misused any **sudo** commands to run GUI applications which could in the past change ownership of files in the user's home.

---

### Post by Jonners59 on 2024-07-12
Not that I am aware, but could possibly whilst trying all the suggestions from various threads...  But unlikely.

I'll give that CMD a bash over the weekend.

THANK YOU!

---

### Post by #&amp;thj^% on 2024-07-12
If you still have problems with permissions, a possible would be 
Before any changes mine looks like:
```
ls -la
total 2743700
drwx------ 34 me   me         4096 Jul 12 10:09  .
drwxr-xr-x  3 root root       4096 May 27 15:53  ..
-rw-------  1 me   me            0 Jun 25 13:01  :
-rwxr-xr-x  1 me   me     99670660 May 26 18:00  balenaEtcher-1.18.11-x64.AppImage
-rwxr-xr-x  1 me   me     96000789 Nov  9  2022  balenaEtcher-1.9.0-x64.AppImage
-rwxr-xr-x  1 me   me          846 Jun 14 12:35  .bash_aliases
-rw-------  1 me   me        11849 Jul 12 10:09  .bash_history
-rw-------  1 me   me            0 Jun  6 12:29  .bash_history-01921.tmp
-rw-------  1 me   me            0 Jun 15 11:46  .bash_history-05755.tmp
-rw-------  1 me   me            0 Jun 27 08:29  .bash_history-15603.tmp
-rw-------  1 me   me            0 Jul  6 15:55  .bash_history-28163.tmp
-rw-------  1 me   me        11061 Jul  7 13:49  .bash_history-48686.tmp
-rw-------  1 me   me            0 Jun 25 09:59  .bash_history-97098.tmp
-rw-r--r--  1 me   me           21 May 26 18:00  .bash_logout
-rw-r--r--  1 me   me         1248 Jun 24 15:23  .bashrc
drwxr-xr-x 40 me   me         4096 Jul 10 12:08  .cache
drwxr-xr-x  4 me   me         4096 May 27 16:09  .cachy
drwxr-xr-x  2 me   me         4096 May 27 16:13  cachyos-repo
-rw-r--r--  1 me   me         8708 May 13 08:17  cachyos-repo.tar.xz
drwxr-xr-x  4 me   me         4096 Jul  1 07:54  .cargo
drwxr-xr-x  3 me   me         4096 May 27 16:10  .cert
drwxr-xr-x 46 me   me         4096 Jul 11 08:22  .config
drwxr-xr-x 80 me   me        12288 Jun 26 08:48  .conky
-rw-------  1 me   me          508 May 26 18:00  dead.letter
drwxr-xr-x  2 me   me         4096 May 27 15:58  Desktop
-rw-r--r--  1 me   me           23 May 26 18:00  .dmrc
drwxr-xr-x  2 me   me        12288 Jul 11 10:08  Documents
drwxr-xr-x  4 me   me         4096 Jul 12 10:17  Downloads
drwxr-xr-x  2 me   me         4096 Jun 10 14:01  .encryptpad
-rwxr-xr-x  1 me   me     48762856 May 26 18:00  ExtremeCooling4Linux-v0.3-x86_64.AppImage
-rw-r--r--  1 me   me      1363502 Jun 12 15:06  fileperms
drwxr-xr-x  2 me   me         4096 May 27 16:10  .fonts
drwx------  5 me   me         4096 Jun 12 16:59  .gnupg
-rw-r--r--  1 me   me          559 May 26 18:00  .gtkrc-2.0
-rw-------  1 me   me            0 May  7 12:30  .ICEauthority
drwxr-xr-x 10 me   me         4096 Jun 10 08:20  .icons
drwxr-xr-x  8 me   me         4096 Jun 10 09:46  .kodi
-rwxr-xr-x  1 me   me    370685120 Jun 14 12:32  krita-5.2.0-x86_64.appimage
drwx------  4 me   me         4096 May 27 15:58  .local
drwxr-xr-x  2 me   me         4096 Jun 12 15:19  .MakeMKV
drwxr-xr-x  4 me   me         4096 May 27 16:11  .mozilla
drwxr-xr-x  6 me   me         4096 Jun 22 16:04  Music
drwxr-xr-x  4 me   me         4096 Jun  4 10:36  .npm
drwxr-xr-x  3 me   me         4096 May 27 16:11  .nv
-rw-r--r--  1 me   me          662 Jun 24 08:09  .nvidia-settings-rc
drwxr-xr-x  4 me   me         4096 Jul 11 08:20  Pictures
drwxr-xr-x  3 me   me         4096 May 27 16:11  .pki
-rw-r--r--  1 me   me          885 Jun 24 15:22  .profile
drwxr-xr-x  2 me   me         4096 May 27 15:58  Public
drwx------  2 me   me         4096 Jul  3 08:19  .pvpn-cli
drwxr-xr-x  8 me   me         4096 Jun  6 13:34  .PySolFC
-rw-------  1 me   me           70 Jul  7 12:12  .python_history
drwxr-xr-x  2 me   me         4096 Jun  4 10:31  repo
-rw-r--r--  1 me   me   2147483648 Jul 11 08:29  temp.file
drwxr-xr-x  2 me   me         4096 May 27 15:58  Templates
-rw-r--r--  1 me   me          129 Jun 10 12:07  test
-rw-------  1 me   me            0 Jul  7 12:10  test1
-rw-------  1 me   me            0 Jul  7 12:10 'test 2'
-rw-------  1 me   me            0 Jul  7 12:10  test3python
drwxr-xr-x 22 me   me         4096 May 27 16:12  .themes
drwxr-xr-x  3 root root       4096 Jun  4 09:24  timeshift
-rwx--x--x  1 me   me     44864704 Jun 27 11:12  ubpm_qt5-1.10.0-x86_64.AppImage
-rwx--x--x  1 me   me          124 Jun 25 12:26  umasaksystem.sh
-rwx--x--x  1 me   me          137 Jun 25 09:57  umask.sh
drwxr-xr-x  3 me   me         4096 May 27 16:12  .var
drwxr-xr-x  2 me   me         4096 Jun 19 10:19  Videos
-rw-------  1 me   me         1147 Jun 27 10:07  .viminfo
-rw-r--r--  1 me   me          173 May 26 18:00  .wget-hsts
-rw-------  1 me   me           58 Jul 12 10:08  .Xauthority
-rw-------  1 me   me       316971 Jul 12 10:28  .xsession-errors
-rw-------  1 me   me       110054 Jul 12 10:06  .xsession-errors.old
-rw-r--r--  1 me   me           56 May 26 18:00  .zshrc

```
Now a reset using "chown"
```
chown -hvR me /home/me

```
_[COLOR="#FF0000"]sudo is not needed[/COLOR]_. (replace "me" to the name of the owner you want to change it to.)
```
ls -la
total 2743824
drwx------ 34 me   me         4096 Jul 12 10:09  .
drwxr-xr-x  3 root root       4096 May 27 15:53  ..
-rw-------  1 me   me            0 Jun 25 13:01  :
-rwxr-xr-x  1 me   me     99670660 May 26 18:00  balenaEtcher-1.18.11-x64.AppImage
-rwxr-xr-x  1 me   me     96000789 Nov  9  2022  balenaEtcher-1.9.0-x64.AppImage
-rwxr-xr-x  1 me   me          846 Jun 14 12:35  .bash_aliases
-rw-------  1 me   me        11849 Jul 12 10:09  .bash_history
-rw-------  1 me   me            0 Jun  6 12:29  .bash_history-01921.tmp
-rw-------  1 me   me            0 Jun 15 11:46  .bash_history-05755.tmp
-rw-------  1 me   me            0 Jun 27 08:29  .bash_history-15603.tmp
-rw-------  1 me   me            0 Jul  6 15:55  .bash_history-28163.tmp
-rw-------  1 me   me        11061 Jul  7 13:49  .bash_history-48686.tmp
-rw-------  1 me   me            0 Jun 25 09:59  .bash_history-97098.tmp
-rw-r--r--  1 me   me           21 May 26 18:00  .bash_logout
-rw-r--r--  1 me   me         1248 Jun 24 15:23  .bashrc
drwxr-xr-x 40 me   me         4096 Jul 10 12:08  .cache
drwxr-xr-x  4 me   me         4096 May 27 16:09  .cachy
drwxr-xr-x  2 me   me         4096 May 27 16:13  cachyos-repo
-rw-r--r--  1 me   me         8708 May 13 08:17  cachyos-repo.tar.xz
drwxr-xr-x  4 me   me         4096 Jul  1 07:54  .cargo
drwxr-xr-x  3 me   me         4096 May 27 16:10  .cert
drwxr-xr-x 46 me   me         4096 Jul 11 08:22  .config
drwxr-xr-x 80 me   me        12288 Jun 26 08:48  .conky
-rw-------  1 me   me          508 May 26 18:00  dead.letter
drwxr-xr-x  2 me   me         4096 May 27 15:58  Desktop
-rw-r--r--  1 me   me           23 May 26 18:00  .dmrc
drwxr-xr-x  2 me   me        12288 Jul 11 10:08  Documents
drwxr-xr-x  4 me   me         4096 Jul 12 10:17  Downloads
drwxr-xr-x  2 me   me         4096 Jun 10 14:01  .encryptpad
-rwxr-xr-x  1 me   me     48762856 May 26 18:00  ExtremeCooling4Linux-v0.3-x86_64.AppImage
-rw-r--r--  1 me   me      1363502 Jun 12 15:06  fileperms
drwxr-xr-x  2 me   me         4096 May 27 16:10  .fonts
drwx------  5 me   me         4096 Jun 12 16:59  .gnupg
-rw-r--r--  1 me   me          559 May 26 18:00  .gtkrc-2.0
-rw-------  1 me   me            0 May  7 12:30  .ICEauthority
drwxr-xr-x 10 me   me         4096 Jun 10 08:20  .icons
drwxr-xr-x  8 me   me         4096 Jun 10 09:46  .kodi
-rwxr-xr-x  1 me   me    370685120 Jun 14 12:32  krita-5.2.0-x86_64.appimage
drwx------  4 me   me         4096 May 27 15:58  .local
drwxr-xr-x  2 me   me         4096 Jun 12 15:19  .MakeMKV
drwxr-xr-x  4 me   me         4096 May 27 16:11  .mozilla
drwxr-xr-x  6 me   me         4096 Jun 22 16:04  Music
drwxr-xr-x  4 me   me         4096 Jun  4 10:36  .npm
drwxr-xr-x  3 me   me         4096 May 27 16:11  .nv
-rw-r--r--  1 me   me          662 Jun 24 08:09  .nvidia-settings-rc
drwxr-xr-x  4 me   me         4096 Jul 11 08:20  Pictures
drwxr-xr-x  3 me   me         4096 May 27 16:11  .pki
-rw-r--r--  1 me   me          885 Jun 24 15:22  .profile
drwxr-xr-x  2 me   me         4096 May 27 15:58  Public
drwx------  2 me   me         4096 Jul  3 08:19  .pvpn-cli
drwxr-xr-x  8 me   me         4096 Jun  6 13:34  .PySolFC
-rw-------  1 me   me           70 Jul  7 12:12  .python_history
drwxr-xr-x  2 me   me         4096 Jun  4 10:31  repo
-rw-r--r--  1 me   me   2147483648 Jul 11 08:29  temp.file
drwxr-xr-x  2 me   me         4096 May 27 15:58  Templates
-rw-r--r--  1 me   me          129 Jun 10 12:07  test
-rw-------  1 me   me            0 Jul  7 12:10  test1
-rw-------  1 me   me            0 Jul  7 12:10 'test 2'
-rw-------  1 me   me            0 Jul  7 12:10  test3python
drwxr-xr-x 22 me   me         4096 May 27 16:12  .themes
drwxr-xr-x  3 root root       4096 Jun  4 09:24  timeshift
-rwx--x--x  1 me   me     44864704 Jun 27 11:12  ubpm_qt5-1.10.0-x86_64.AppImage
-rwx--x--x  1 me   me          124 Jun 25 12:26  umasaksystem.sh
-rwx--x--x  1 me   me          137 Jun 25 09:57  umask.sh
drwxr-xr-x  3 me   me         4096 May 27 16:12  .var
drwxr-xr-x  2 me   me         4096 Jun 19 10:19  Videos
-rw-------  1 me   me         1147 Jun 27 10:07  .viminfo
-rw-r--r--  1 me   me          173 May 26 18:00  .wget-hsts
-rw-------  1 me   me           58 Jul 12 10:08  .Xauthority
-rw-------  1 me   me       442953 Jul 12 10:36  .xsession-errors
-rw-------  1 me   me       110054 Jul 12 10:06  .xsession-errors.old
-rw-r--r--  1 me   me           56 May 26 18:00  .zshrc

``` 

Always have good back-ups in place before make any system changes.

For clarity:
This -h -h, --no-dereference
              affect symbolic links instead of any referenced file (useful only on systems that can
              change the ownership of a symlink)


and this -v, --verbose
              output a diagnostic for every file processed


and of course -R, --recursive
              operate on files and directories recursively

---

### Post by Jonners59 on 2024-07-14
Thought I had replied to this, this AM, seems not, but it was on my phone.

Thank you 1fallen.
I had a go yesterday.  I could not affect the directory where the files and documents etc. are all stored.  I keep everything on a separate partition which mounts to /media/Storage/  It says chmod failed for every line.  It says wright protected.  Tried changing it but that does not work.  I've tried using terminal and via recovery.  NOTHING works.  This ONLY started after the update and the installation of USBGuard.  SO no change there.

I also did as you advised, below, and sadly since then I can not boot into my desktop.  I get the log-in screen.  Log in, BUT then the screen goes black and hangs there.  Sometimes I get a curser top left, which sometimes flashes, sometimes not.

Any advise, please ;-(



> **1fallen said:**
> If you still have problems with permissions, a possible would be 
Before any changes mine looks like:
```
ls -la
total 2743700
drwx------ 34 me   me         4096 Jul 12 10:09  .
drwxr-xr-x  3 root root       4096 May 27 15:53  ..
-rw-------  1 me   me            0 Jun 25 13:01  :
-rwxr-xr-x  1 me   me     99670660 May 26 18:00  balenaEtcher-1.18.11-x64.AppImage
-rwxr-xr-x  1 me   me     96000789 Nov  9  2022  balenaEtcher-1.9.0-x64.AppImage
-rwxr-xr-x  1 me   me          846 Jun 14 12:35  .bash_aliases
-rw-------  1 me   me        11849 Jul 12 10:09  .bash_history
-rw-------  1 me   me            0 Jun  6 12:29  .bash_history-01921.tmp
-rw-------  1 me   me            0 Jun 15 11:46  .bash_history-05755.tmp
-rw-------  1 me   me            0 Jun 27 08:29  .bash_history-15603.tmp
-rw-------  1 me   me            0 Jul  6 15:55  .bash_history-28163.tmp
-rw-------  1 me   me        11061 Jul  7 13:49  .bash_history-48686.tmp
-rw-------  1 me   me            0 Jun 25 09:59  .bash_history-97098.tmp
-rw-r--r--  1 me   me           21 May 26 18:00  .bash_logout
-rw-r--r--  1 me   me         1248 Jun 24 15:23  .bashrc
drwxr-xr-x 40 me   me         4096 Jul 10 12:08  .cache
drwxr-xr-x  4 me   me         4096 May 27 16:09  .cachy
drwxr-xr-x  2 me   me         4096 May 27 16:13  cachyos-repo
-rw-r--r--  1 me   me         8708 May 13 08:17  cachyos-repo.tar.xz
drwxr-xr-x  4 me   me         4096 Jul  1 07:54  .cargo
drwxr-xr-x  3 me   me         4096 May 27 16:10  .cert
drwxr-xr-x 46 me   me         4096 Jul 11 08:22  .config
drwxr-xr-x 80 me   me        12288 Jun 26 08:48  .conky
-rw-------  1 me   me          508 May 26 18:00  dead.letter
drwxr-xr-x  2 me   me         4096 May 27 15:58  Desktop
-rw-r--r--  1 me   me           23 May 26 18:00  .dmrc
drwxr-xr-x  2 me   me        12288 Jul 11 10:08  Documents
drwxr-xr-x  4 me   me         4096 Jul 12 10:17  Downloads
drwxr-xr-x  2 me   me         4096 Jun 10 14:01  .encryptpad
-rwxr-xr-x  1 me   me     48762856 May 26 18:00  ExtremeCooling4Linux-v0.3-x86_64.AppImage
-rw-r--r--  1 me   me      1363502 Jun 12 15:06  fileperms
drwxr-xr-x  2 me   me         4096 May 27 16:10  .fonts
drwx------  5 me   me         4096 Jun 12 16:59  .gnupg
-rw-r--r--  1 me   me          559 May 26 18:00  .gtkrc-2.0
-rw-------  1 me   me            0 May  7 12:30  .ICEauthority
drwxr-xr-x 10 me   me         4096 Jun 10 08:20  .icons
drwxr-xr-x  8 me   me         4096 Jun 10 09:46  .kodi
-rwxr-xr-x  1 me   me    370685120 Jun 14 12:32  krita-5.2.0-x86_64.appimage
drwx------  4 me   me         4096 May 27 15:58  .local
drwxr-xr-x  2 me   me         4096 Jun 12 15:19  .MakeMKV
drwxr-xr-x  4 me   me         4096 May 27 16:11  .mozilla
drwxr-xr-x  6 me   me         4096 Jun 22 16:04  Music
drwxr-xr-x  4 me   me         4096 Jun  4 10:36  .npm
drwxr-xr-x  3 me   me         4096 May 27 16:11  .nv
-rw-r--r--  1 me   me          662 Jun 24 08:09  .nvidia-settings-rc
drwxr-xr-x  4 me   me         4096 Jul 11 08:20  Pictures
drwxr-xr-x  3 me   me         4096 May 27 16:11  .pki
-rw-r--r--  1 me   me          885 Jun 24 15:22  .profile
drwxr-xr-x  2 me   me         4096 May 27 15:58  Public
drwx------  2 me   me         4096 Jul  3 08:19  .pvpn-cli
drwxr-xr-x  8 me   me         4096 Jun  6 13:34  .PySolFC
-rw-------  1 me   me           70 Jul  7 12:12  .python_history
drwxr-xr-x  2 me   me         4096 Jun  4 10:31  repo
-rw-r--r--  1 me   me   2147483648 Jul 11 08:29  temp.file
drwxr-xr-x  2 me   me         4096 May 27 15:58  Templates
-rw-r--r--  1 me   me          129 Jun 10 12:07  test
-rw-------  1 me   me            0 Jul  7 12:10  test1
-rw-------  1 me   me            0 Jul  7 12:10 'test 2'
-rw-------  1 me   me            0 Jul  7 12:10  test3python
drwxr-xr-x 22 me   me         4096 May 27 16:12  .themes
drwxr-xr-x  3 root root       4096 Jun  4 09:24  timeshift
-rwx--x--x  1 me   me     44864704 Jun 27 11:12  ubpm_qt5-1.10.0-x86_64.AppImage
-rwx--x--x  1 me   me          124 Jun 25 12:26  umasaksystem.sh
-rwx--x--x  1 me   me          137 Jun 25 09:57  umask.sh
drwxr-xr-x  3 me   me         4096 May 27 16:12  .var
drwxr-xr-x  2 me   me         4096 Jun 19 10:19  Videos
-rw-------  1 me   me         1147 Jun 27 10:07  .viminfo
-rw-r--r--  1 me   me          173 May 26 18:00  .wget-hsts
-rw-------  1 me   me           58 Jul 12 10:08  .Xauthority
-rw-------  1 me   me       316971 Jul 12 10:28  .xsession-errors
-rw-------  1 me   me       110054 Jul 12 10:06  .xsession-errors.old
-rw-r--r--  1 me   me           56 May 26 18:00  .zshrc

```
Now a reset using "chown"
```
chown -hvR me /home/me

```
_[COLOR=#FF0000]sudo is not needed[/COLOR]_. (replace "me" to the name of the owner you want to change it to.)
```
ls -la
total 2743824
drwx------ 34 me   me         4096 Jul 12 10:09  .
drwxr-xr-x  3 root root       4096 May 27 15:53  ..
-rw-------  1 me   me            0 Jun 25 13:01  :
-rwxr-xr-x  1 me   me     99670660 May 26 18:00  balenaEtcher-1.18.11-x64.AppImage
-rwxr-xr-x  1 me   me     96000789 Nov  9  2022  balenaEtcher-1.9.0-x64.AppImage
-rwxr-xr-x  1 me   me          846 Jun 14 12:35  .bash_aliases
-rw-------  1 me   me        11849 Jul 12 10:09  .bash_history
-rw-------  1 me   me            0 Jun  6 12:29  .bash_history-01921.tmp
-rw-------  1 me   me            0 Jun 15 11:46  .bash_history-05755.tmp
-rw-------  1 me   me            0 Jun 27 08:29  .bash_history-15603.tmp
-rw-------  1 me   me            0 Jul  6 15:55  .bash_history-28163.tmp
-rw-------  1 me   me        11061 Jul  7 13:49  .bash_history-48686.tmp
-rw-------  1 me   me            0 Jun 25 09:59  .bash_history-97098.tmp
-rw-r--r--  1 me   me           21 May 26 18:00  .bash_logout
-rw-r--r--  1 me   me         1248 Jun 24 15:23  .bashrc
drwxr-xr-x 40 me   me         4096 Jul 10 12:08  .cache
drwxr-xr-x  4 me   me         4096 May 27 16:09  .cachy
drwxr-xr-x  2 me   me         4096 May 27 16:13  cachyos-repo
-rw-r--r--  1 me   me         8708 May 13 08:17  cachyos-repo.tar.xz
drwxr-xr-x  4 me   me         4096 Jul  1 07:54  .cargo
drwxr-xr-x  3 me   me         4096 May 27 16:10  .cert
drwxr-xr-x 46 me   me         4096 Jul 11 08:22  .config
drwxr-xr-x 80 me   me        12288 Jun 26 08:48  .conky
-rw-------  1 me   me          508 May 26 18:00  dead.letter
drwxr-xr-x  2 me   me         4096 May 27 15:58  Desktop
-rw-r--r--  1 me   me           23 May 26 18:00  .dmrc
drwxr-xr-x  2 me   me        12288 Jul 11 10:08  Documents
drwxr-xr-x  4 me   me         4096 Jul 12 10:17  Downloads
drwxr-xr-x  2 me   me         4096 Jun 10 14:01  .encryptpad
-rwxr-xr-x  1 me   me     48762856 May 26 18:00  ExtremeCooling4Linux-v0.3-x86_64.AppImage
-rw-r--r--  1 me   me      1363502 Jun 12 15:06  fileperms
drwxr-xr-x  2 me   me         4096 May 27 16:10  .fonts
drwx------  5 me   me         4096 Jun 12 16:59  .gnupg
-rw-r--r--  1 me   me          559 May 26 18:00  .gtkrc-2.0
-rw-------  1 me   me            0 May  7 12:30  .ICEauthority
drwxr-xr-x 10 me   me         4096 Jun 10 08:20  .icons
drwxr-xr-x  8 me   me         4096 Jun 10 09:46  .kodi
-rwxr-xr-x  1 me   me    370685120 Jun 14 12:32  krita-5.2.0-x86_64.appimage
drwx------  4 me   me         4096 May 27 15:58  .local
drwxr-xr-x  2 me   me         4096 Jun 12 15:19  .MakeMKV
drwxr-xr-x  4 me   me         4096 May 27 16:11  .mozilla
drwxr-xr-x  6 me   me         4096 Jun 22 16:04  Music
drwxr-xr-x  4 me   me         4096 Jun  4 10:36  .npm
drwxr-xr-x  3 me   me         4096 May 27 16:11  .nv
-rw-r--r--  1 me   me          662 Jun 24 08:09  .nvidia-settings-rc
drwxr-xr-x  4 me   me         4096 Jul 11 08:20  Pictures
drwxr-xr-x  3 me   me         4096 May 27 16:11  .pki
-rw-r--r--  1 me   me          885 Jun 24 15:22  .profile
drwxr-xr-x  2 me   me         4096 May 27 15:58  Public
drwx------  2 me   me         4096 Jul  3 08:19  .pvpn-cli
drwxr-xr-x  8 me   me         4096 Jun  6 13:34  .PySolFC
-rw-------  1 me   me           70 Jul  7 12:12  .python_history
drwxr-xr-x  2 me   me         4096 Jun  4 10:31  repo
-rw-r--r--  1 me   me   2147483648 Jul 11 08:29  temp.file
drwxr-xr-x  2 me   me         4096 May 27 15:58  Templates
-rw-r--r--  1 me   me          129 Jun 10 12:07  test
-rw-------  1 me   me            0 Jul  7 12:10  test1
-rw-------  1 me   me            0 Jul  7 12:10 'test 2'
-rw-------  1 me   me            0 Jul  7 12:10  test3python
drwxr-xr-x 22 me   me         4096 May 27 16:12  .themes
drwxr-xr-x  3 root root       4096 Jun  4 09:24  timeshift
-rwx--x--x  1 me   me     44864704 Jun 27 11:12  ubpm_qt5-1.10.0-x86_64.AppImage
-rwx--x--x  1 me   me          124 Jun 25 12:26  umasaksystem.sh
-rwx--x--x  1 me   me          137 Jun 25 09:57  umask.sh
drwxr-xr-x  3 me   me         4096 May 27 16:12  .var
drwxr-xr-x  2 me   me         4096 Jun 19 10:19  Videos
-rw-------  1 me   me         1147 Jun 27 10:07  .viminfo
-rw-r--r--  1 me   me          173 May 26 18:00  .wget-hsts
-rw-------  1 me   me           58 Jul 12 10:08  .Xauthority
-rw-------  1 me   me       442953 Jul 12 10:36  .xsession-errors
-rw-------  1 me   me       110054 Jul 12 10:06  .xsession-errors.old
-rw-r--r--  1 me   me           56 May 26 18:00  .zshrc

``` 

Always have good back-ups in place before make any system changes.

For clarity:
This -h -h, --no-dereference
              affect symbolic links instead of any referenced file (useful only on systems that can
              change the ownership of a symlink)


and this -v, --verbose
              output a diagnostic for every file processed


and of course -R, --recursive
              operate on files and directories recursively

---

### Post by #&amp;thj^% on 2024-07-14
> **Jonners59 said:**
> 
I also did as you advised, below, and sadly since then I can not boot into my desktop.  I get the log-in screen.  Log in, BUT then the screen goes black and hangs there.  Sometimes I get a curser top left, which sometimes flashes, sometimes not.

Any advise, please ;-(
That would not have anything to do with a broken-login
I personally ran the command 3 times, once before suggesting "chown -hvR me /home/me" to You.
And once more on another system and just now,
```
chown -hvR me /home/me >chown.txt
chown: changing ownership of '/home/me/mcolors': Operation not permitted
chown: changing ownership of '/home/me/plt': Operation not permitted
chown: changing ownership of '/home/me/zpcachys': Operation not permitte
```
And the rest is far to big for forums so a snippet with how the rest returned:
```
ownership of '/home/me/ExtremeCooling4Linux-v0.3-x86_64.AppImage' retained as me
ownership of '/home/me/.bash_aliases' retained as me
ownership of '/home/me/.kodi/userdata/Savestates' retained as me
ownership of '/home/me/.kodi/userdata/keymaps' retained as me
ownership of '/home/me/.kodi/userdata/Database/Addons33.db' retained as me
ownership of '/home/me/.kodi/userdata/Database/Epg16.db' retained as me
ownership of '/home/me/.kodi/userdata/Database/ViewModes6.db' retained as me
ownership of '/home/me/.kodi/userdata/Database/MyMusic83.db' retained as me
ownership of '/home/me/.kodi/userdata/Database/CDDB' retained as me
ownership of '/home/me/.kodi/userdata/Database/TV44.db' retained as me
ownership of '/home/me/.kodi/userdata/Database/MyVideos131.db' retained as me
ownership of '/home/me/.kodi/userdata/Database/Textures13.db' retained as me
ownership of '/home/me/.kodi/userdata/Database' retained as me
ownership of '/home/me/.kodi/userdata/Thumbnails/0/02c302a9.jpg' retained as me
ownership of '/home/me/.kodi/userdata/Thumbnails/0/0437e87e.jpg' retained as me
ownership of '/home/me/.kodi/userdata/Thumbnails/0' retained as me
ownership of '/home/me/.kodi/userdata/Thumbnails/7' retained as me
ownership of '/home/me/.kodi/userdata/Thumbnails/c' retained as me
ownership of '/home/me/.kodi/userdata/Thumbnails/9' retained as me
ownership of '/home/me/.kodi/userdata/Thumbnails/3' retained as me
ownership of '/home/me/.kodi/userdata/Thumbnails/4' retained as me
ownership of '/home/me/.kodi/userdata/Thumbnails/d' retained as me
ownership of '/home/me/.kodi/userdata/Thumbnails/f' retained as me
ownership of '/home/me/.kodi/userdata/Thumbnails/6/6ab21683.jpg' retained as me
ownership of '/home/me/.kodi/userdata/Thumbnails/6' retained as me
ownership of '/home/me/.kodi/userdata/Thumbnails/1' retained as me
ownership of '/home/me/.kodi/userdata/Thumbnails/a/a2c7d08c.jpg' retained as me
ownership of '/home/me/.kodi/userdata/Thumbnails/a' retained as me
ownership of '/home/me/.kodi/userdata/Thumbnails/e' retained as me
ownership of '/home/me/.kodi/userdata/Thumbnails/5' retained as me
ownership of '/home/me/.kodi/userdata/Thumbnails/Video/Bookmarks' retained as me
ownership of '/home/me/.kodi/userdata/Thumbnails/Video' retained as me
ownership of '/home/me/.kodi/userdata/Thumbnails/2' retained as me
ownership of '/home/me/.kodi/userdata/Thumbnails/8' retained as me
ownership of '/home/me/.kodi/userdata/Thumbnails/b' retained as me
ownership of '/home/me/.kodi/userdata/Thumbnails' retained as me
ownership of '/home/me/.kodi/userdata/profiles.xml' retained as me
ownership of '/home/me/.kodi/userdata/library' retained as me
ownership of '/home/me/.kodi/userdata/playlists/mixed' retained as me
ownership of '/home/me/.kodi/userdata/playlists/music' retained as me
ownership of '/home/me/.kodi/userdata/playlists/video' retained as me
ownership of '/home/me/.kodi/userdata/playlists' retained as me
ownership of '/home/me/.kodi/userdata/addon_data/skin.estuary/settings.xml' retained as me
ownership of '/home/me/.kodi/userdata/addon_data/skin.estuary' retained as me
ownership of '/home/me/.kodi/userdata/addon_data' retained as me
ownership of '/home/me/.kodi/userdata/RssFeeds.xml' retained as me
ownership of '/home/me/.kodi/userdata/guisettings.xml' retained as me
ownership of '/home/me/.kodi/userdata/peripheral_data/application_Mouse.xml' retained as me
ownership of '/home/me/.kodi/userdata/peripheral_data/application_Keyboard.xml' retained as me
ownership of '/home/me/.kodi/userdata/peripheral_data' retained as me
ownership of '/home/me/.kodi/userdata' retained as me
ownership of '/home/me/.kodi/addons/metadata.tvshows.themoviedb.org.python/LICENSE.txt' retained as me
ownership of '/home/me/.kodi/addons/metadata.tvshows.themoviedb.org.python/addon.xml' retained as me
ownership of '/home/me/.kodi/addons/metadata.tvshows.themoviedb.org.python/changelog.txt' retained as me
ownership of '/home/me/.kodi/addons/metadata.tvshows.themoviedb.org.python/libs/traktratings.py' retained as me
```
That's only a third of the return seen on my end.

EDIT:A third reboot and still good.

Dang I feel bad, but lacking anything helpful to work from I'm clueless.

---

### Post by #&amp;thj^% on 2024-07-14
At the login screen use {Ctrl+Alt+F3}
Login as you would normally and when returned to the prompt use:
```
startx
```
Try and remember anything that might help.

---

### Post by Jonners59 on 2024-07-15
For god's sake don't feel bad.  Not your fault.  It's just frustrating and you are working blind and I have little clue.

> **1fallen said:**
> That would not have anything to do with a broken-login
I personally ran the command 3 times, once before suggesting "chown -hvR me /home/me" to You.
And once more on another system and just now,
```
chown -hvR me /home/me >chown.txt
chown: changing ownership of '/home/me/mcolors': Operation not permitted
chown: changing ownership of '/home/me/plt': Operation not permitted
chown: changing ownership of '/home/me/zpcachys': Operation not permitte
```
And the rest is far to big for forums so a snippet with how the rest returned:
```
ownership of '/home/me/ExtremeCooling4Linux-v0.3-x86_64.AppImage' retained as me
ownership of '/home/me/.bash_aliases' retained as me
ownership of '/home/me/.kodi/userdata/Savestates' retained as me
ownership of '/home/me/.kodi/userdata/keymaps' retained as me
ownership of '/home/me/.kodi/userdata/Database/Addons33.db' retained as me
ownership of '/home/me/.kodi/userdata/Database/Epg16.db' retained as me
ownership of '/home/me/.kodi/userdata/Database/ViewModes6.db' retained as me
ownership of '/home/me/.kodi/userdata/Database/MyMusic83.db' retained as me
ownership of '/home/me/.kodi/userdata/Database/CDDB' retained as me
ownership of '/home/me/.kodi/userdata/Database/TV44.db' retained as me
ownership of '/home/me/.kodi/userdata/Database/MyVideos131.db' retained as me
ownership of '/home/me/.kodi/userdata/Database/Textures13.db' retained as me
ownership of '/home/me/.kodi/userdata/Database' retained as me
ownership of '/home/me/.kodi/userdata/Thumbnails/0/02c302a9.jpg' retained as me
ownership of '/home/me/.kodi/userdata/Thumbnails/0/0437e87e.jpg' retained as me
ownership of '/home/me/.kodi/userdata/Thumbnails/0' retained as me
ownership of '/home/me/.kodi/userdata/Thumbnails/7' retained as me
ownership of '/home/me/.kodi/userdata/Thumbnails/c' retained as me
ownership of '/home/me/.kodi/userdata/Thumbnails/9' retained as me
ownership of '/home/me/.kodi/userdata/Thumbnails/3' retained as me
ownership of '/home/me/.kodi/userdata/Thumbnails/4' retained as me
ownership of '/home/me/.kodi/userdata/Thumbnails/d' retained as me
ownership of '/home/me/.kodi/userdata/Thumbnails/f' retained as me
ownership of '/home/me/.kodi/userdata/Thumbnails/6/6ab21683.jpg' retained as me
ownership of '/home/me/.kodi/userdata/Thumbnails/6' retained as me
ownership of '/home/me/.kodi/userdata/Thumbnails/1' retained as me
ownership of '/home/me/.kodi/userdata/Thumbnails/a/a2c7d08c.jpg' retained as me
ownership of '/home/me/.kodi/userdata/Thumbnails/a' retained as me
ownership of '/home/me/.kodi/userdata/Thumbnails/e' retained as me
ownership of '/home/me/.kodi/userdata/Thumbnails/5' retained as me
ownership of '/home/me/.kodi/userdata/Thumbnails/Video/Bookmarks' retained as me
ownership of '/home/me/.kodi/userdata/Thumbnails/Video' retained as me
ownership of '/home/me/.kodi/userdata/Thumbnails/2' retained as me
ownership of '/home/me/.kodi/userdata/Thumbnails/8' retained as me
ownership of '/home/me/.kodi/userdata/Thumbnails/b' retained as me
ownership of '/home/me/.kodi/userdata/Thumbnails' retained as me
ownership of '/home/me/.kodi/userdata/profiles.xml' retained as me
ownership of '/home/me/.kodi/userdata/library' retained as me
ownership of '/home/me/.kodi/userdata/playlists/mixed' retained as me
ownership of '/home/me/.kodi/userdata/playlists/music' retained as me
ownership of '/home/me/.kodi/userdata/playlists/video' retained as me
ownership of '/home/me/.kodi/userdata/playlists' retained as me
ownership of '/home/me/.kodi/userdata/addon_data/skin.estuary/settings.xml' retained as me
ownership of '/home/me/.kodi/userdata/addon_data/skin.estuary' retained as me
ownership of '/home/me/.kodi/userdata/addon_data' retained as me
ownership of '/home/me/.kodi/userdata/RssFeeds.xml' retained as me
ownership of '/home/me/.kodi/userdata/guisettings.xml' retained as me
ownership of '/home/me/.kodi/userdata/peripheral_data/application_Mouse.xml' retained as me
ownership of '/home/me/.kodi/userdata/peripheral_data/application_Keyboard.xml' retained as me
ownership of '/home/me/.kodi/userdata/peripheral_data' retained as me
ownership of '/home/me/.kodi/userdata' retained as me
ownership of '/home/me/.kodi/addons/metadata.tvshows.themoviedb.org.python/LICENSE.txt' retained as me
ownership of '/home/me/.kodi/addons/metadata.tvshows.themoviedb.org.python/addon.xml' retained as me
ownership of '/home/me/.kodi/addons/metadata.tvshows.themoviedb.org.python/changelog.txt' retained as me
ownership of '/home/me/.kodi/addons/metadata.tvshows.themoviedb.org.python/libs/traktratings.py' retained as me
```
That's only a third of the return seen on my end.

EDIT:A third reboot and still good.

Dang I feel bad, but lacking anything helpful to work from I'm clueless.

---

### Post by Jonners59 on 2024-07-15
I shall try and find time today and have a go...

Thanks.

QUOTE=1fallen;14197389]At the login screen use {Ctrl+Alt+F3}
Login as you would normally and when returned to the prompt use:
```
startx
```
Try and remember anything that might help.[/QUOTE]

---

### Post by Jonners59 on 2024-07-15
Thank you.  Well, I tried the code **startx** just after login and it worked fine.  A couple of errors flashed by, but it got me in.  I then - stupidly - decided that as I was in, I would try and fix things myself.  Children should NEVER be allowed to play with such toys.  So I went into Synaptic and reinstalled key apps, as this worked for me with something else, similar.  So xfce4, Nvidia drivers etc.  and I thought it couldn't do any hard.  It'll just make sure everything is properly installed.  Whilst that was doing its thing, I thought I'd check the drives by opening GParted - "don't think Jon, just do as you are told"!!!!  That's when it all went wrong.  GParted was taking ages, I suspect finding the drive with the documents.  And then the whole thing froze on me.

Needless to say, I had made everything a million times worse.

After some hours of playing, rebooting, trying to install stuff, reinstall stuff and googling I tried to clean the installation that was taking place so did this:
```
sudo su /var/lib/apt/lists/lock /var/lib/dpkg/lock /var/lib/dpkg/lock-frontend /var/cache/apt/archieves/lock
```  
```
sudo apt-get update && apt-get upgrade
dpkg -configure -a
 apt-get remove gnome-session gnome-shell
 apt-get autoremove  &&  apt-get install ubuntu-desktop
```

I hoped from all the reading, that would clean stuff up, which it seemed to.

I then did:
```
sudo chmod 755 /home/me/.Xconfiguration
```

I did a reboot in to Ubuntu, and all was good.  I can now ALSO access the stored files.  So almost there.

The issues I have now are that in the **Additional Drivers** it states the driver installed is "Manually Installed", and the other drivers are not selectable.  I can't change them.  Lastly, the laptop takes ages to boot up.


> **1fallen said:**
> At the login screen use {Ctrl+Alt+F3}
Login as you would normally and when returned to the prompt use:
```
startx
```
Try and remember anything that might help.

---

### Post by #&amp;thj^% on 2024-07-15
Jonners59, I'm getting very confused now, your thread title "[xubuntu] USB and Cameras not loading" 
And one of your last posts show you installed Gnome " apt-get install ubuntu-desktop"

Any who, I remember a year back on "Xubuntu" dealing with a very slow boot as well, I just don't spend a lot of time trying to find that cause.

I keep good back-up's so A clean install and restore of what I need daily and all is well again.

---

### Post by Jonners59 on 2024-07-15
> **1fallen said:**
> Jonners59, I'm getting very confused now, your thread title "[xubuntu] USB and Cameras not loading" 
And one of your last posts show you installed Gnome " apt-get install ubuntu-desktop"
Yes, that is correct.  The blog WAS about the USB/Camera issue, but if you recall, going down to the 3rd post I said that I had resolved that, finding USBGuard as the culprit.  I then added that it seemed that it had left other things not working which I'll need to now sort out, to which you replied with the owenership as probably being the cause.  We then went down this new path, rather than a new blog.

> **Jonners59 said:**
>  Re: USB and Cameras not loading
                          Thank you.  That hit the button.  I didn't go through giving access as you showed, but instead just uninstalled Usbguard.

I have now discovered that sone directory permissions have changed too.   I tried to tidy up my desktop and update sone files and they won't save  or move directory.  I.e. from Desktop to a directory in Documents.   Never ends!  &#55357;&#56877;&#55357;&#56877;"


> **1fallen said:**
> Jonners59,
Any who, I remember a year back on "Xubuntu" dealing with a very slow  boot as well, I just don't spend a lot of time trying to find that  cause.
Yes, that's correct, and it never resolved.  The boot is still slow, but it got vastly slower.  It seems to be going back to the "just slow" now the more I reboot.

> **1fallen said:**
> Jonners59,
I keep good back-up's so A clean install and restore of what I need daily and all is well again.
Never really found a good backup that worked properly when rebuilding.  But that's just me.

---

### Post by #&amp;thj^% on 2024-07-15
Ok now we are all caught up.

Will you run the system-info script found in my signature, and paste back the link it gives you back here it may help us find something out of whack...LOL
I'm going off-line now so I'll check back tomorrow. ;)

---

### Post by Jonners59 on 2024-07-15
OK, shall have a go.

As a starter I do get these warnings with ```
Sudo apt-get update
```
[HTML]Reading package lists... Done
E: The repository 'https://ppa.launchpadcontent.net/mafoelffen/system-info/ubuntu noble Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
N: Skipping acquisition of configured file 'main/binary-i386/Packages', as repository 'https://packages.microsoft.com/repos/edge stable InRelease' doesn't support architecture 'i386'
W: https://ppa.launchpadcontent.net/danielrichter2007/grub-customizer/ubuntu/dists/noble/InRelease: Signature by key 59DAD276B942642B1BBD0EACA8AA1FAA3F055C03 uses weak algorithm (rsa1024)
W: https://ppa.launchpadcontent.net/yannubuntu/boot-repair/ubuntu/dists/noble/InRelease: Signature by key 3C48D16124B50277AF10D27F32B18A1260D8DA0B uses weak algorithm (rsa1024)
N: Missing Signed-By in the sources.list(5) entry for 'https://packages.microsoft.com/repos/ms-teams'
N: Missing Signed-By in the sources.list(5) entry for 'https://esm.ubuntu.com/infra/ubuntu'
N: Missing Signed-By in the sources.list(5) entry for 'https://esm.ubuntu.com/infra/ubuntu'
[/HTML]

Fingers crossed there'll be something for you to scrutinize when you get back

Report:
[https://paste.ubuntu.com/p/Xjw5Y5bPVn/](https://paste.ubuntu.com/p/Xjw5Y5bPVn/)

TTFN

---

### Post by #&amp;thj^% on 2024-07-16
Dual Boot I see.

May have found something here:
```
 *-display UNCLAIMED
       description: 3D controller
       product: GP107M [GeForce GTX 1050 Ti Mobile]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: 
           memory:a3000000-a3ffffff 
           memory:90000000-9fffffff 
           memory:a0000000-a1ffffff 
           ioport:5000(size=128) 
           memory:a4000000-a407ffff
```

No nVidia driver?

And your source list might need some pruning: /etc/apt/sources.list /etc/apt/sources.listd

"/etc/apt/sources.list.d/danielrichter2007-ubuntu-grub-customizer" is one I'd get rid of, but that's your choice.

also this one: "/etc/apt/sources.list.d/minetestdevs-ubuntu-daily-builds-lunar.list.distUpgrade:
File had no entries."
All of these seem worthless currently:
```
/etc/apt/sources.list.d/minetestdevs-ubuntu-stable-lunar.sources:
File had no entries.
/etc/apt/sources.list.d/skype-stable.list.distUpgrade:
File had no entries.
/etc/apt/sources.list.d/iconnor-ubuntu-zoneminder-1_34-jammy.sources.save:
File had no entries.
/etc/apt/sources.list.d/danielrichter2007-ubuntu-grub-customizer-kinetic.list.distUpgrade:
File had no entries.
/etc/apt/sources.list.d/third-party.sources.save:
File had no entries.
/etc/apt/sources.list.d/google-chrome.list.distUpgrade:
deb [arch=amd64] https://dl.google.com/linux/chrome/deb/ stable main 
/etc/apt/sources.list.d/minetestdevs-ubuntu-stable-lunar.sources.save:
File had no entries.
```
Your installed packages also show this as installed "grub-customizer" that can cause many problems, search the forums for that.

Now back to your Video driver you have these installed:
```
nvidia-cg-dev
nvidia-cg-toolkit
nvidia-common
nvidia-dkms-535-open
nvidia-modprobe
nvidia-prime
nvidia-primus-vk-wrapper
nvidia-profiler
nvidia-settings
```
Will you please show me this:
```
nvidia-smi
```
And you are still showing a XFCE4 session, I do see some Gnome packages as well.

You would be much better off trimming back on what you have installed, I'm only suggesting not telling you to do so.


I'm starting to see the possibility of package corruption with UN-nesacary sources.

---

### Post by Jonners59 on 2024-07-16
WOW that's a lot.  MANY thanks for the feedback.  
Yes, I'll want to do all these and your help to clean, tidy up and fix will be extremely grateful of.  That said, want to keep Skype and Chrome, and maybe one or two others as I use them from time to time.  Some things need Chrome...  But the rest - no probs.

> **1fallen said:**
> Dual Boot I see.

May have found something here:
```
 *-display UNCLAIMED
       description: 3D controller
       product: GP107M [GeForce GTX 1050 Ti Mobile]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: 
           memory:a3000000-a3ffffff 
           memory:90000000-9fffffff 
           memory:a0000000-a1ffffff 
           ioport:5000(size=128) 
           memory:a4000000-a407ffff
```

No nVidia driver?

Now back to your Video driver you have these installed:
```
nvidia-cg-dev
nvidia-cg-toolkit
nvidia-common
nvidia-dkms-535-open
nvidia-modprobe
nvidia-prime
nvidia-primus-vk-wrapper
nvidia-profiler
nvidia-settings
```
Will you please show me this:
```
nvidia-smi
```.

So the code for my 1st task seems to show no NVIDIA drivers, yet they WERE installed.  MMM  Shall I sudo apt-get install them?

```
nvidia-smi
Command 'nvidia-smi' not found, but can be installed with:
sudo apt install nvidia-utils-470         # version 470.256.02-0ubuntu0.24.04.1, or
sudo apt install nvidia-utils-470-server  # version 470.256.02-0ubuntu0.24.04.1
sudo apt install nvidia-utils-535         # version 535.183.01-0ubuntu0.24.04.1
sudo apt install nvidia-utils-535-server  # version 535.183.01-0ubuntu0.24.04.1
sudo apt install nvidia-utils-550         # version 550.90.07-0ubuntu0.24.04.1
sudo apt install nvidia-utils-525         # version 525.147.05-0ubuntu1
sudo apt install nvidia-utils-525-server  # version 525.147.05-0ubuntu1
sudo apt install nvidia-utils-550-server  # version 550.90.07-0ubuntu0.24.04.1
```

I await your command.

---

### Post by #&amp;thj^% on 2024-07-16
First thing on the list is to take care of your driver:
1st)
```
sudo apt autoremove --purge nvidia*
```
2nd) Install a good driver for that card of yours:
```
sudo apt install nvidia-driver-550 nvidia-dkms-550
```
3rd) Reboot, now how is your system? Play with it for a small bit of time, say 30 minutes, and then tell me your findings, quirky, studdering, freezes, anything that's not normal behavior.

Then we will work on the rest, small steps at first.

---

### Post by Jonners59 on 2024-07-16
> **1fallen said:**
> First thing on the list is to take care of your driver:
1st)
```
sudo apt autoremove --purge nvidia*
```
2nd) Install a good driver for that card of yours:
```
sudo apt install nvidia-driver-550 nvidia-dkms-550
```
3rd) Reboot, now how is your system? Play with it for a small bit of time, say 30 minutes, and then tell me your findings, quirky, studdering, freezes, anything that's not normal behavior.

Then we will work on the rest, small steps at first.

All done.  Took ages to download.  Seems to work fine.

So next up is what, remove Grub Customizer?

---

### Post by #&amp;thj^% on 2024-07-16
Well we can start there: (Did you verify nvidia with nvidia-smi?)
```
sudo add-apt-repository -r ppa:danielrichter2007/grub-customizer
```
Removes the source, and then the removal
```
sudo apt remove grub-customizer
```
Before we do any more show me the removal process.

If all goes well lets have a peek at those sources again.
```
inxi -r
```

---

### Post by #&amp;thj^% on 2024-07-16
I have an emergency @ work, I'll be back soon.

---

### Post by Jonners59 on 2024-07-16
> **1fallen said:**
> Well we can start there: (Did you verify nvidia with nvidia-smi?)

Oh no.  I didn't.  Just run it.

```
nvidia-smi
NVIDIA-SMI has failed because it couldn't communicate with the NVIDIA driver. Make sure that the latest NVIDIA driver is installed and running.
```

Don't get it.  It is listed and selected in Additional Drivers.  What does it mean?


[QUOTE=1fallen;14197565]```
sudo add-apt-repository -r ppa:danielrichter2007/grub-customizer
```
Removes the source, and then the removal
```
sudo apt remove grub-customizer
```
Before we do any more show me the removal process.

If all goes well lets have a peek at those sources again.
```
inxi -r
```

```
sudo apt remove grub-customizer
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following package was automatically installed and is no longer required:
  nvidia-firmware-550-550.90.07
Use 'sudo apt autoremove' to remove it.
The following packages will be REMOVED
  grub-customizer
0 to upgrade, 0 to newly install, 1 to remove and 40 not to upgrade.
After this operation, 8,583 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 915429 files and directories currently installed.)
Removing grub-customizer (5.2.5-0ubuntu1~ppa1n) ...
Processing triggers for desktop-file-utils (0.27-2build1) ...
Processing triggers for hicolor-icon-theme (0.17-2) ...
Processing triggers for gnome-menus (3.36.0-1.1ubuntu3) ...
Processing triggers for mate-menus (1.26.1-1build3) ...
Processing triggers for man-db (2.12.0-4build2) ...
Processing triggers for mailcap (3.70+nmu1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.6+22.04.20220217-0ubuntu5) ...
Rebuilding /usr/share/applications/bamf-2.index...


```

```
inxi -r
Repos:
  No active apt repos in: /etc/apt/sources.list
  No active apt repos in: /etc/apt/sources.list.d/danielrichter2007-ubuntu-grub-customizer-kinetic.sources
  No active apt repos in: /etc/apt/sources.list.d/google-chrome.sources
  No active apt repos in: /etc/apt/sources.list.d/iconnor-ubuntu-zoneminder-1_34-jammy.sources
  Active apt repos in: /etc/apt/sources.list.d/mafoelffen-ubuntu-system-info-noble.sources
    1: deb https://ppa.launchpadcontent.net/mafoelffen/system-info/ubuntu/ noble main
  Active apt repos in: /etc/apt/sources.list.d/microsoft-edge.sources
    1: deb https://packages.microsoft.com/repos/edge/ stable main
  No active apt repos in: /etc/apt/sources.list.d/minetestdevs-ubuntu-daily-builds-lunar.sources
  No active apt repos in: /etc/apt/sources.list.d/minetestdevs-ubuntu-stable-lunar.sources
  No active apt repos in: /etc/apt/sources.list.d/skype-stable.sources
  Active apt repos in: /etc/apt/sources.list.d/teams.sources
    1: deb https://packages.microsoft.com/repos/ms-teams stable main
  No active apt repos in: /etc/apt/sources.list.d/third-party.sources
  Active apt repos in: /etc/apt/sources.list.d/ubuntu-esm-infra.sources
    1: deb https://esm.ubuntu.com/infra/ubuntu jammy-infra-security jammy-infra-updates main
  Active apt repos in: /etc/apt/sources.list.d/ubuntu.sources
    1: deb deb-src http://archive.ubuntu.com/ubuntu noble noble-updates noble-backports noble-security main universe multiverse restricted
  No active apt repos in: /etc/apt/sources.list.d/yannubuntu-ubuntu-boot-repair-jammy.sources
  Active apt repos in: /etc/apt/sources.list.d/yannubuntu-ubuntu-boot-repair-noble.sources
    1: deb https://ppa.launchpadcontent.net/yannubuntu/boot-repair/ubuntu/ noble main


```

It's late here, now, so may end up picking up your update tomorrow.

Thank you

---

### Post by #&amp;thj^% on 2024-07-16
This is not right:
```
The following package was automatically installed and is no longer required:
  nvidia-firmware-550-550.90.07
```

Mine:
```
 apt list --installed|grep nvidia 

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

libnvidia-cfg1-555/noble,now 555.52.04-0ubuntu0~gpu24.04.1 amd64 [installed,automatic]
libnvidia-common-555/noble,now 555.52.04-0ubuntu0~gpu24.04.1 all [installed,automatic]
libnvidia-compute-555/noble,now 555.52.04-0ubuntu0~gpu24.04.1 amd64 [installed,automatic]
libnvidia-decode-555/noble,now 555.52.04-0ubuntu0~gpu24.04.1 amd64 [installed,automatic]
libnvidia-encode-555/noble,now 555.52.04-0ubuntu0~gpu24.04.1 amd64 [installed,automatic]
libnvidia-extra-555/noble,now 555.52.04-0ubuntu0~gpu24.04.1 amd64 [installed,automatic]
libnvidia-fbc1-555/noble,now 555.52.04-0ubuntu0~gpu24.04.1 amd64 [installed,automatic]
libnvidia-gl-555/noble,now 555.52.04-0ubuntu0~gpu24.04.1 amd64 [installed,automatic]
linux-signatures-nvidia-6.8.0-31-generic/oracular,now 6.8.0-31.31 amd64 [installed,automatic]
nvidia-compute-utils-555/noble,now 555.52.04-0ubuntu0~gpu24.04.1 amd64 [installed,automatic]
nvidia-dkms-555/noble,now 555.52.04-0ubuntu0~gpu24.04.1 amd64 [installed]
nvidia-driver-555/noble,now 555.52.04-0ubuntu0~gpu24.04.1 amd64 [installed]
nvidia-firmware-555-555.52.04/noble,now 555.52.04-0ubuntu0~gpu24.04.1 amd64 [installed,automatic]
nvidia-kernel-common-555/noble,now 555.52.04-0ubuntu0~gpu24.04.1 amd64 [installed,automatic]
nvidia-kernel-source-555/noble,now 555.52.04-0ubuntu0~gpu24.04.1 amd64 [installed,automatic]
nvidia-prime/oracular,now 0.8.17.2 all [installed,automatic]
nvidia-settings/oracular,now 510.47.03-0ubuntu4 amd64 [installed,automatic]
nvidia-utils-555/noble,now 555.52.04-0ubuntu0~gpu24.04.1 amd64 [installed,automatic]
xserver-xorg-video-nvidia-555/noble,now 555.52.04-0ubuntu0~gpu24.04.1 amd64 [installed,automatic]

```
Or just that view:
```
apt list --installed|grep nvidia-firmware 

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

nvidia-firmware-555-555.52.04/noble,now 555.52.04-0ubuntu0~gpu24.04.1 amd64 [installed,automatic]

```

You did purge all nvidia first right?
```
sudo apt autoremove --purge nvidia*
```

I'll see you tomorrow then.

And Please Don't use the 555 driver just yet, it got a few rough spots ATM

---

### Post by Jonners59 on 2024-07-17
> **1fallen said:**
> This is not right:
```
The following package was automatically installed and is no longer required:
  nvidia-firmware-550-550.90.07
```

Mine:
```
apt list --installed|grep nvidia

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

bumblebee-nvidia/noble,now 3.2.1-29ubuntu3 amd64 [installed]
libnvidia-cfg1-535/noble-updates,noble-security,now 535.183.01-0ubuntu0.24.04.1 amd64 [installed,automatic]
libnvidia-common-535/noble-updates,noble-updates,noble-security,noble-security,now 535.183.01-0ubuntu0.24.04.1 all [installed,automatic]
libnvidia-compute-535/noble-updates,noble-security,now 535.183.01-0ubuntu0.24.04.1 amd64 [installed,automatic]
libnvidia-compute-535/noble-updates,noble-security,now 535.183.01-0ubuntu0.24.04.1 i386 [installed]
libnvidia-decode-535/noble-updates,noble-security,now 535.183.01-0ubuntu0.24.04.1 amd64 [installed,automatic]
libnvidia-decode-535/noble-updates,noble-security,now 535.183.01-0ubuntu0.24.04.1 i386 [installed]
libnvidia-encode-535/noble-updates,noble-security,now 535.183.01-0ubuntu0.24.04.1 amd64 [installed,automatic]
libnvidia-encode-535/noble-updates,noble-security,now 535.183.01-0ubuntu0.24.04.1 i386 [installed]
libnvidia-extra-535/noble-updates,noble-security,now 535.183.01-0ubuntu0.24.04.1 amd64 [installed,automatic]
libnvidia-fbc1-535/noble-updates,noble-security,now 535.183.01-0ubuntu0.24.04.1 amd64 [installed,automatic]
libnvidia-fbc1-535/noble-updates,noble-security,now 535.183.01-0ubuntu0.24.04.1 i386 [installed]
libnvidia-gl-535/noble-updates,noble-security,now 535.183.01-0ubuntu0.24.04.1 amd64 [installed,automatic]
libnvidia-gl-535/noble-updates,noble-security,now 535.183.01-0ubuntu0.24.04.1 i386 [installed]
linux-modules-nvidia-535-6.8.0-1006-oracle/noble-updates,noble-security,now 6.8.0-1006.6+1 amd64 [installed,automatic]
linux-modules-nvidia-535-oracle/noble-updates,noble-security,now 6.8.0-1006.6+1 amd64 [installed,automatic]
linux-nvidia-tools-host/noble-updates,noble-updates,noble-security,noble-security,now 6.8.0-1009.9 all [installed]
linux-objects-nvidia-535-6.8.0-1006-oracle/noble-updates,noble-security,now 6.8.0-1006.6+1 amd64 [installed,automatic]
linux-objects-nvidia-535-server-6.8.0-38-generic/noble-updates,noble-security,now 6.8.0-38.38+1 amd64 [installed]
linux-signatures-nvidia-6.8.0-1006-oracle/noble-updates,noble-security,now 6.8.0-1006.6+1 amd64 [installed,automatic]
nvidia-compute-utils-535/noble-updates,noble-security,now 535.183.01-0ubuntu0.24.04.1 amd64 [installed,automatic]
nvidia-driver-525/noble,now 525.147.05-0ubuntu2 amd64 [installed]
nvidia-driver-535/noble-updates,noble-security,now 535.183.01-0ubuntu0.24.04.1 amd64 [installed]
nvidia-firmware-535-535.183.01/noble-updates,noble-security,now 535.183.01-0ubuntu0.24.04.1 amd64 [installed,automatic]
nvidia-kernel-common-535/noble-updates,noble-security,now 535.183.01-0ubuntu0.24.04.1 amd64 [installed,automatic]
nvidia-kernel-source-535/noble-updates,noble-security,now 535.183.01-0ubuntu0.24.04.1 amd64 [installed,automatic]
nvidia-prime/noble,noble,now 0.8.17.2 all [installed,automatic]
nvidia-primus-vk-common/noble,now 1.6.4-2 amd64 [installed,automatic]
nvidia-primus-vk-wrapper/noble,now 1.6.4-2 amd64 [installed]
nvidia-settings/noble,now 510.47.03-0ubuntu4 amd64 [installed,automatic]
nvidia-utils-535/noble-updates,noble-security,now 535.183.01-0ubuntu0.24.04.1 amd64 [installed,automatic]
xserver-xorg-video-nvidia-535/noble-updates,noble-security,now 535.183.01-0ubuntu0.24.04.1 amd64 [installed,automatic]



```


This is mine
```
apt list --installed|grep nvidia

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

bumblebee-nvidia/noble,now 3.2.1-29ubuntu3 amd64 [installed]
libnvidia-cfg1-535/noble-updates,noble-security,now 535.183.01-0ubuntu0.24.04.1 amd64 [installed,automatic]
libnvidia-common-535/noble-updates,noble-updates,noble-security,noble-security,now 535.183.01-0ubuntu0.24.04.1 all [installed,automatic]
libnvidia-compute-535/noble-updates,noble-security,now 535.183.01-0ubuntu0.24.04.1 amd64 [installed,automatic]
libnvidia-compute-535/noble-updates,noble-security,now 535.183.01-0ubuntu0.24.04.1 i386 [installed,automatic]
libnvidia-decode-535/noble-updates,noble-security,now 535.183.01-0ubuntu0.24.04.1 amd64 [installed,automatic]
libnvidia-decode-535/noble-updates,noble-security,now 535.183.01-0ubuntu0.24.04.1 i386 [installed,automatic]
libnvidia-encode-535/noble-updates,noble-security,now 535.183.01-0ubuntu0.24.04.1 amd64 [installed,automatic]
libnvidia-encode-535/noble-updates,noble-security,now 535.183.01-0ubuntu0.24.04.1 i386 [installed,automatic]
libnvidia-extra-535/noble-updates,noble-security,now 535.183.01-0ubuntu0.24.04.1 amd64 [installed,automatic]
libnvidia-fbc1-535/noble-updates,noble-security,now 535.183.01-0ubuntu0.24.04.1 amd64 [installed,automatic]
libnvidia-fbc1-535/noble-updates,noble-security,now 535.183.01-0ubuntu0.24.04.1 i386 [installed,automatic]
libnvidia-gl-535/noble-updates,noble-security,now 535.183.01-0ubuntu0.24.04.1 amd64 [installed,automatic]
libnvidia-gl-535/noble-updates,noble-security,now 535.183.01-0ubuntu0.24.04.1 i386 [installed,automatic]
linux-modules-nvidia-535-6.8.0-38-generic/noble-updates,noble-security,now 6.8.0-38.38+1 amd64 [installed,automatic]
linux-modules-nvidia-535-generic/noble-updates,noble-security,now 6.8.0-38.38+1 amd64 [installed]
linux-nvidia-tools-host/noble-updates,noble-updates,noble-security,noble-security,now 6.8.0-1009.9 all [installed]
linux-objects-nvidia-535-6.8.0-38-generic/noble-updates,noble-security,now 6.8.0-38.38+1 amd64 [installed,automatic]
linux-objects-nvidia-535-server-6.8.0-38-generic/noble-updates,noble-security,now 6.8.0-38.38+1 amd64 [installed]
linux-signatures-nvidia-6.8.0-38-generic/noble-updates,noble-security,now 6.8.0-38.38+1 amd64 [installed,automatic]
nvidia-compute-utils-535/noble-updates,noble-security,now 535.183.01-0ubuntu0.24.04.1 amd64 [installed,automatic]
nvidia-driver-535/noble-updates,noble-security,now 535.183.01-0ubuntu0.24.04.1 amd64 [installed]
nvidia-firmware-535-535.183.01/noble-updates,noble-security,now 535.183.01-0ubuntu0.24.04.1 amd64 [installed,automatic]
nvidia-kernel-common-535/noble-updates,noble-security,now 535.183.01-0ubuntu0.24.04.1 amd64 [installed,automatic]
nvidia-kernel-source-535/noble-updates,noble-security,now 535.183.01-0ubuntu0.24.04.1 amd64 [installed,automatic]
nvidia-prime/noble,noble,now 0.8.17.2 all [installed,automatic]
nvidia-settings/noble,now 510.47.03-0ubuntu4 amd64 [installed,automatic]
nvidia-utils-535/noble-updates,noble-security,now 535.183.01-0ubuntu0.24.04.1 amd64 [installed,automatic]
xserver-xorg-video-nvidia-535/noble-updates,noble-security,now 535.183.01-0ubuntu0.24.04.1 amd64 [installed,automatic]


```



> **1fallen said:**
> Or just that view:
```
apt list --installed|grep nvidia-firmware 

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

nvidia-firmware-555-555.52.04/noble,now 555.52.04-0ubuntu0~gpu24.04.1 amd64 [installed,automatic]

```

This is mine:

```
apt list --installed|grep nvidia-firmware 

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

nvidia-firmware-535-535.183.01/noble-updates,noble-security,now 535.183.01-0ubuntu0.24.04.1 amd64 [installed,automatic]

```


> **1fallen said:**
> You did purge all nvidia first right?
```
sudo apt autoremove --purge nvidia*
```

I'll see you tomorrow then.

And Please Don't use the 555 driver just yet, it got a few rough spots ATM

Yes.  I ran each code, in order, as listed and then rebooted as instructed.  The download of the packages took ages, but all done exactly as asked.

I am using the first in the list of Additional Drivers, ```
nvidia-drive-535 (proprietry, tested)
```

Whilst fixing this, is there anything else I can fix, such as sources list?

I'm in and out for much of the day with things at my son's school I need to deal with.  Your thoughts and suggestions are always welcome, as and when.

---

### Post by #&amp;thj^% on 2024-07-17
This time we are going to approach this differently, you still have leftovers from 535 as seen in your replies.
Lets just stick with nvidia-driver-535 then.
Please one more time run:
```
sudo apt autoremove --purge nvidia*
```
If you see anything you feel needs to be seen then please do so.
Now power off your machine.
Now boot up again (no restart) and show me this please:
```
apt list --installed|grep nvidia
```
We will continue from there.

---

### Post by Jonners59 on 2024-07-17
> **1fallen said:**
> 
Please one more time run:
```
sudo apt autoremove --purge nvidia*
```
If you see anything you feel needs to be seen then please do so.
Now power off your machine.
Now boot up again (no restart) and show me this please:
```
apt list --installed|grep nvidia
```
We will continue from there.

OK not good.  Did the first code, twice for good measure.  Each time it listed loads of Nvidia items not removed as they were not installed, which I thought a bit odd.  
```
sudo apt autoremove --purge nvidia*

Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Note: selecting 'nvidia-driver-550-server' for glob 'nvidia*'
Note: selecting 'nvidia-cuda-toolkit-doc' for glob 'nvidia*'
Note: selecting 'nvidia-imex' for glob 'nvidia*'
Note: selecting 'nvidia-cuda-toolkit-gcc' for glob 'nvidia*'
Note: selecting 'nvidia-headless-460' for glob 'nvidia*'
Note: selecting 'nvidia-headless-465' for glob 'nvidia*'
Note: selecting 'nvidia-headless-470' for glob 'nvidia*'
Note: selecting 'nvidia-dkms-470-server' for glob 'nvidia*'
Note: selecting 'nvidia-headless-510' for glob 'nvidia*'
Note: selecting 'nvidia-headless-515' for glob 'nvidia*'
Note: selecting 'nvidia-compute-utils-515-server' for glob 'nvidia*'
Note: selecting 'nvidia-headless-520' for glob 'nvidia*'
Note: selecting 'nvidia-headless-525' for glob 'nvidia*'
Note: selecting 'nvidia-headless-530' for glob 'nvidia*'
Note: selecting 'nvidia-headless-535' for glob 'nvidia*'
Note: selecting 'nvidia-headless-550' for glob 'nvidia*'
Note: selecting 'nvidia-fabricmanager-dev' for glob 'nvidia*'
Note: selecting 'nvidia-compute-utils-535-server' for glob 'nvidia*'
Note: selecting 'nvidia-driver-460-server' for glob 'nvidia*'
Note: selecting 'nvidia-primus-vk-common' for glob 'nvidia*'
Note: selecting 'nvidia-opencl-dev' for glob 'nvidia*'
Note: selecting 'nvidia-open-kernel-dkms-any' for glob 'nvidia*'
Note: selecting 'nvidia-cg-toolkit' for glob 'nvidia*'
Note: selecting 'nvidia-kernel-common-525-server' for glob 'nvidia*'
Note: selecting 'nvidia-libopencl1-dev' for glob 'nvidia*'
Note: selecting 'nvidia-texture-tools' for glob 'nvidia*'
Note: selecting 'nvidia-driver-525-open' for glob 'nvidia*'
Note: selecting 'nvidia-opencl-icd' for glob 'nvidia*'
Note: selecting 'nvidia-utils' for glob 'nvidia*'
Note: selecting 'nvidia-compute-utils-460' for glob 'nvidia*'
Note: selecting 'nvidia-compute-utils-465' for glob 'nvidia*'
Note: selecting 'nvidia-compute-utils-470' for glob 'nvidia*'
Note: selecting 'nvidia-headless-470-server' for glob 'nvidia*'
Note: selecting 'nvidia-compute-utils-510' for glob 'nvidia*'
Note: selecting 'nvidia-compute-utils-515' for glob 'nvidia*'
Note: selecting 'nvidia-compute-utils-520' for glob 'nvidia*'
Note: selecting 'nvidia-compute-utils-525' for glob 'nvidia*'
Note: selecting 'nvidia-compute-utils-530' for glob 'nvidia*'
Note: selecting 'nvidia-compute-utils-535' for glob 'nvidia*'
Note: selecting 'nvidia-compute-utils-550' for glob 'nvidia*'
Note: selecting 'nvidia-dkms-550-open' for glob 'nvidia*'
Note: selecting 'nvidia-dkms-460' for glob 'nvidia*'
Note: selecting 'nvidia-dkms-465' for glob 'nvidia*'
Note: selecting 'nvidia-dkms-470' for glob 'nvidia*'
Note: selecting 'nvidia-dkms-510' for glob 'nvidia*'
Note: selecting 'nvidia-dkms-515' for glob 'nvidia*'
Note: selecting 'nvidia-dkms-520' for glob 'nvidia*'
Note: selecting 'nvidia-dkms-525' for glob 'nvidia*'
Note: selecting 'nvidia-dkms-530' for glob 'nvidia*'
Note: selecting 'nvidia-dkms-535' for glob 'nvidia*'
Note: selecting 'nvidia-dkms-550' for glob 'nvidia*'
Note: selecting 'nvidia-driver-460' for glob 'nvidia*'
Note: selecting 'nvidia-driver-465' for glob 'nvidia*'
Note: selecting 'nvidia-driver-470' for glob 'nvidia*'
Note: selecting 'nvidia-headless-550-server-open' for glob 'nvidia*'
Note: selecting 'nvidia-driver-510' for glob 'nvidia*'
Note: selecting 'nvidia-driver-515' for glob 'nvidia*'
Note: selecting 'nvidia-driver-520' for glob 'nvidia*'
Note: selecting 'nvidia-driver-525' for glob 'nvidia*'
Note: selecting 'nvidia-driver-530' for glob 'nvidia*'
Note: selecting 'nvidia-driver-535' for glob 'nvidia*'
Note: selecting 'nvidia-driver-550' for glob 'nvidia*'
Note: selecting 'nvidia-dkms-460-server' for glob 'nvidia*'
Note: selecting 'nvidia-firmware-550-server-550.90.07' for glob 'nvidia*'
Note: selecting 'nvidia-headless-no-dkms-515-server' for glob 'nvidia*'
Note: selecting 'nvidia-dkms-520-open' for glob 'nvidia*'
Note: selecting 'nvidia-utils-535-server' for glob 'nvidia*'
Note: selecting 'nvidia-headless-no-dkms-535-server' for glob 'nvidia*'
Note: selecting 'nvidia-driver-470-server' for glob 'nvidia*'
Note: selecting 'nvidia-primus-vk-wrapper' for glob 'nvidia*'
Note: selecting 'nvidia-kernel-common-515-server' for glob 'nvidia*'
Note: selecting 'nvidia-kernel-source-535-server-open' for glob 'nvidia*'
Note: selecting 'nvidia-vulkan-icd' for glob 'nvidia*'
Note: selecting 'nvidia-kernel-common-535-server' for glob 'nvidia*'
Note: selecting 'nvidia-vaapi-driver' for glob 'nvidia*'
Note: selecting 'nvidia-headless-460-server' for glob 'nvidia*'
Note: selecting 'nvidia-headless' for glob 'nvidia*'
Note: selecting 'nvidia-kernel-dkms-any' for glob 'nvidia*'
Note: selecting 'nvidia-utils-460' for glob 'nvidia*'
Note: selecting 'nvidia-utils-465' for glob 'nvidia*'
Note: selecting 'nvidia-utils-470' for glob 'nvidia*'
Note: selecting 'nvidia-utils-510' for glob 'nvidia*'
Note: selecting 'nvidia-utils-515' for glob 'nvidia*'
Note: selecting 'nvidia-utils-520' for glob 'nvidia*'
Note: selecting 'nvidia-utils-525' for glob 'nvidia*'
Note: selecting 'nvidia-utils-530' for glob 'nvidia*'
Note: selecting 'nvidia-utils-535' for glob 'nvidia*'
Note: selecting 'nvidia-utils-550' for glob 'nvidia*'
Note: selecting 'nvidia-kernel-source-530-open' for glob 'nvidia*'
Note: selecting 'nvidia-egl-wayland-common' for glob 'nvidia*'
Note: selecting 'nvidia-kernel-source-550-server' for glob 'nvidia*'
Note: selecting 'nvidia-driver-550-server-open' for glob 'nvidia*'
Note: selecting 'nvidia-utils-525-server' for glob 'nvidia*'
Note: selecting 'nvidia-headless-515-open' for glob 'nvidia*'
Note: selecting 'nvidia-headless-no-dkms-525-server' for glob 'nvidia*'
Note: selecting 'nvidia-kernel-source-460-server' for glob 'nvidia*'
Note: selecting 'nvidia-kernel-source-515-open' for glob 'nvidia*'
Note: selecting 'nvidia-headless-no-dkms-535-server-open' for glob 'nvidia*'
Note: selecting 'nvidia-headless-no-dkms-530-open' for glob 'nvidia*'
Note: selecting 'nvidia-dkms-550-server-open' for glob 'nvidia*'
Note: selecting 'nvidia-utils-515-server' for glob 'nvidia*'
Note: selecting 'nvidia-firmware-550-server-550.67' for glob 'nvidia*'
Note: selecting 'nvidia-dkms-525-open' for glob 'nvidia*'
Note: selecting 'nvidia-headless-no-dkms-515-open' for glob 'nvidia*'
Note: selecting 'nvidia-headless-530-open' for glob 'nvidia*'
Note: selecting 'nvidia-legacy-390xx-opencl-icd' for glob 'nvidia*'
Note: selecting 'nvidia-kernel-source-470-server' for glob 'nvidia*'
Note: selecting 'nvidia-profiler' for glob 'nvidia*'
Note: selecting 'nvidia-driver-libs' for glob 'nvidia*'
Note: selecting 'nvidia-current-updates' for glob 'nvidia*'
Note: selecting 'nvidia-visual-profiler' for glob 'nvidia*'
Note: selecting 'nvidia-dkms-515-server' for glob 'nvidia*'
Note: selecting 'nvidia-dkms-535-server' for glob 'nvidia*'
Note: selecting 'nvidia-compute-utils-550-server' for glob 'nvidia*'
Note: selecting 'nvidia-primus-vk-wrapper:i386' for glob 'nvidia*'
Note: selecting 'nvidia-kernel-common-460' for glob 'nvidia*'
Note: selecting 'nvidia-kernel-common-465' for glob 'nvidia*'
Note: selecting 'nvidia-kernel-common-470' for glob 'nvidia*'
Note: selecting 'nvidia-kernel-source-535-open' for glob 'nvidia*'
Note: selecting 'nvidia-legacy-390xx-smi' for glob 'nvidia*'
Note: selecting 'nvidia-prebuilt-kernel' for glob 'nvidia*'
Note: selecting 'nvidia-kernel-common-510' for glob 'nvidia*'
Note: selecting 'nvidia-kernel-common-515' for glob 'nvidia*'
Note: selecting 'nvidia-kernel-common-520' for glob 'nvidia*'
Note: selecting 'nvidia-kernel-common-525' for glob 'nvidia*'
Note: selecting 'nvidia-kernel-common-530' for glob 'nvidia*'
Note: selecting 'nvidia-kernel-common-535' for glob 'nvidia*'
Note: selecting 'nvidia-kernel-common-550' for glob 'nvidia*'
Note: selecting 'nvidia-current' for glob 'nvidia*'
Note: selecting 'nvidia-compute-utils' for glob 'nvidia*'
Note: selecting 'nvidia-driver-525-server' for glob 'nvidia*'
Note: selecting 'nvidia-fs-modules' for glob 'nvidia*'
Note: selecting 'nvidia-firmware-535-535.161.08' for glob 'nvidia*'
Note: selecting 'nvidia-kernel-common' for glob 'nvidia*'
Note: selecting 'nvidia-driver-515-open' for glob 'nvidia*'
Note: selecting 'nvidia-compute-utils-460-server' for glob 'nvidia*'
Note: selecting 'nvidia-firmware-535-server-535.161.08' for glob 'nvidia*'
Note: selecting 'nvidia-cuda-dev' for glob 'nvidia*'
Note: selecting 'nvidia-cuda-doc' for glob 'nvidia*'
Note: selecting 'nvidia-headless-515-server' for glob 'nvidia*'
Note: selecting 'nvidia-fabricmanager' for glob 'nvidia*'
Note: selecting 'nvidia-firmware-535-535.171.04' for glob 'nvidia*'
Note: selecting 'nvidia-headless-535-server' for glob 'nvidia*'
Note: selecting 'nvidia-cuda-gdb' for glob 'nvidia*'
Note: selecting 'nvidia-firmware-535-server-535.171.04' for glob 'nvidia*'
Note: selecting 'nvidia-cuda-toolkit' for glob 'nvidia*'
Note: selecting 'nvidia-headless-no-dkms-535-open' for glob 'nvidia*'
Note: selecting 'nvidia-headless-550-open' for glob 'nvidia*'
Note: selecting 'nvidia-dkms-525-server' for glob 'nvidia*'
Note: selecting 'nvidia-headless-no-dkms-550-server' for glob 'nvidia*'
Note: selecting 'nvidia-prime' for glob 'nvidia*'
Note: selecting 'nvidia-firmware-550-550.54.15' for glob 'nvidia*'
Note: selecting 'nvidia-driver-515-server' for glob 'nvidia*'
Note: selecting 'nvidia-dkms-515-open' for glob 'nvidia*'
Note: selecting 'nvidia-driver-535-server' for glob 'nvidia*'
Note: selecting 'nvidia-kernel-common-550-server' for glob 'nvidia*'
Note: selecting 'nvidia-headless-520-open' for glob 'nvidia*'
Note: selecting 'nvidia-kernel-source-550-open' for glob 'nvidia*'
Note: selecting 'nvidia-384' for glob 'nvidia*'
Note: selecting 'nvidia-390' for glob 'nvidia*'
Note: selecting 'nvidia-fs-dkms' for glob 'nvidia*'
Note: selecting 'nvidia-compute-utils-470-server' for glob 'nvidia*'
Note: selecting 'nvidia-headless-525-server' for glob 'nvidia*'
Note: selecting 'nvidia-headless-535-open' for glob 'nvidia*'
Note: selecting 'nvidia-fs-prebuilt-kernel' for glob 'nvidia*'
Note: selecting 'nvidia-kernel-common-460-server' for glob 'nvidia*'
Note: selecting 'nvidia-kernel-source-550-server-open' for glob 'nvidia*'
Note: selecting 'nvidia-driver-530-open' for glob 'nvidia*'
Note: selecting 'nvidia-kernel-source-520-open' for glob 'nvidia*'
Note: selecting 'nvidia-headless-535-server-open' for glob 'nvidia*'
Note: selecting 'nvidia-settings' for glob 'nvidia*'
Note: selecting 'nvidia-headless-no-dkms-460' for glob 'nvidia*'
Note: selecting 'nvidia-headless-no-dkms-465' for glob 'nvidia*'
Note: selecting 'nvidia-headless-no-dkms-470' for glob 'nvidia*'
Note: selecting 'nvidia-cudnn' for glob 'nvidia*'
Note: selecting 'nvidia-headless-no-dkms-510' for glob 'nvidia*'
Note: selecting 'nvidia-headless-no-dkms-515' for glob 'nvidia*'
Note: selecting 'nvidia-headless-no-dkms-520' for glob 'nvidia*'
Note: selecting 'nvidia-headless-no-dkms-525' for glob 'nvidia*'
Note: selecting 'nvidia-headless-no-dkms-530' for glob 'nvidia*'
Note: selecting 'nvidia-headless-no-dkms-535' for glob 'nvidia*'
Note: selecting 'nvidia-headless-no-dkms-550' for glob 'nvidia*'
Note: selecting 'nvidia-headless-no-dkms-550-open' for glob 'nvidia*'
Note: selecting 'nvidia-libopencl1' for glob 'nvidia*'
Note: selecting 'nvidia-fabricmanager-dev-460' for glob 'nvidia*'
Note: selecting 'nvidia-fabricmanager-dev-470' for glob 'nvidia*'
Note: selecting 'nvidia-fabricmanager-dev-515' for glob 'nvidia*'
Note: selecting 'nvidia-fabricmanager-dev-525' for glob 'nvidia*'
Note: selecting 'nvidia-fabricmanager-dev-535' for glob 'nvidia*'
Note: selecting 'nvidia-fabricmanager-dev-550' for glob 'nvidia*'
Note: selecting 'nvidia-kernel-source-525-server' for glob 'nvidia*'
Note: selecting 'nvidia-dkms-530-open' for glob 'nvidia*'
Note: selecting 'nvidia-headless-no-dkms-470-server' for glob 'nvidia*'
Note: selecting 'nvidia-headless-no-dkms-520-open' for glob 'nvidia*'
Note: selecting 'nvidia-cuda-samples' for glob 'nvidia*'
Note: selecting 'nvidia-firmware-550-server-550.54.15' for glob 'nvidia*'
Note: selecting 'nvidia-kernel-common-470-server' for glob 'nvidia*'
Note: selecting 'nvidia-firmware-550-550.67' for glob 'nvidia*'
Note: selecting 'nvidia-fabricmanager-460' for glob 'nvidia*'
Note: selecting 'nvidia-fabricmanager-470' for glob 'nvidia*'
Note: selecting 'nvidia-fabricmanager-515' for glob 'nvidia*'
Note: selecting 'nvidia-fabricmanager-525' for glob 'nvidia*'
Note: selecting 'nvidia-fabricmanager-535' for glob 'nvidia*'
Note: selecting 'nvidia-fabricmanager-550' for glob 'nvidia*'
Note: selecting 'nvidia-driver-535-server-open' for glob 'nvidia*'
Note: selecting 'nvidia-headless-no-dkms-550-server-open' for glob 'nvidia*'
Note: selecting 'nvidia-utils-550-server' for glob 'nvidia*'
Note: selecting 'nvidia-driver-550-open' for glob 'nvidia*'
Note: selecting 'nvidia-kernel-source-515-server' for glob 'nvidia*'
Note: selecting 'nvidia-utils-460-server' for glob 'nvidia*'
Note: selecting 'nvidia-kernel-source-460' for glob 'nvidia*'
Note: selecting 'nvidia-kernel-source-465' for glob 'nvidia*'
Note: selecting 'nvidia-kernel-source-470' for glob 'nvidia*'
Note: selecting 'nvidia-kernel-source-510' for glob 'nvidia*'
Note: selecting 'nvidia-kernel-source-515' for glob 'nvidia*'
Note: selecting 'nvidia-headless-525-open' for glob 'nvidia*'
Note: selecting 'nvidia-kernel-source-535-server' for glob 'nvidia*'
Note: selecting 'nvidia-kernel-source-520' for glob 'nvidia*'
Note: selecting 'nvidia-kernel-source-525' for glob 'nvidia*'
Note: selecting 'nvidia-kernel-source-530' for glob 'nvidia*'
Note: selecting 'nvidia-kernel-source-535' for glob 'nvidia*'
Note: selecting 'nvidia-kernel-source-550' for glob 'nvidia*'
Note: selecting 'nvidia-headless-no-dkms-460-server' for glob 'nvidia*'
Note: selecting 'nvidia-driver-520-open' for glob 'nvidia*'
Note: selecting 'nvidia-dkms-535-server-open' for glob 'nvidia*'
Note: selecting 'nvidia-dkms-550-server' for glob 'nvidia*'
Note: selecting 'nvidia-imex-550' for glob 'nvidia*'
Note: selecting 'nvidia-driver-535-open' for glob 'nvidia*'
Note: selecting 'nvidia-kernel-source-525-open' for glob 'nvidia*'
Note: selecting 'nvidia-firmware-535-535.183.01' for glob 'nvidia*'
Note: selecting 'nvidia-compute-utils-525-server' for glob 'nvidia*'
Note: selecting 'nvidia-firmware-535-server-535.183.01' for glob 'nvidia*'
Note: selecting 'nvidia-headless-550-server' for glob 'nvidia*'
Note: selecting 'nvidia-settings-binary' for glob 'nvidia*'
Note: selecting 'nvidia-dkms-kernel' for glob 'nvidia*'
Note: selecting 'nvidia-modprobe' for glob 'nvidia*'
Note: selecting 'nvidia-utils-470-server' for glob 'nvidia*'
Note: selecting 'nvidia-cg-dev' for glob 'nvidia*'
Note: selecting 'nvidia-dkms-535-open' for glob 'nvidia*'
Note: selecting 'nvidia-cg-doc' for glob 'nvidia*'
Note: selecting 'nvidia-kernel-source' for glob 'nvidia*'
Note: selecting 'nvidia-common' for glob 'nvidia*'
Note: selecting 'nvidia-persistenced' for glob 'nvidia*'
Note: selecting 'nvidia-firmware-550-550.90.07' for glob 'nvidia*'
Note: selecting 'nvidia-headless-no-dkms-525-open' for glob 'nvidia*'
Note: selecting 'nvidia-driver-binary' for glob 'nvidia*'
Note: selecting 'nvidia-smi' for glob 'nvidia*'
Package 'nvidia-egl-wayland-common' is not installed, so not removed
Note, selecting 'nvidia-settings' instead of 'nvidia-settings-binary'
Note, selecting 'libnvtt-bin' instead of 'nvidia-texture-tools'
Package 'nvidia-libopencl1-dev' is not installed, so not removed
Package 'nvidia-current' is not installed, so not removed
Package 'nvidia-current-updates' is not installed, so not removed
Package 'nvidia-driver-libs' is not installed, so not removed
Package 'nvidia-vulkan-icd' is not installed, so not removed
Package 'nvidia-legacy-390xx-opencl-icd' is not installed, so not removed
Package 'nvidia-legacy-390xx-smi' is not installed, so not removed
Package 'nvidia-libopencl1' is not installed, so not removed
Package 'nvidia-390' is not installed, so not removed
Package 'nvidia-cuda-doc' is not installed, so not removed
Package 'nvidia-kernel-dkms-any' is not installed, so not removed
Package 'nvidia-open-kernel-dkms-any' is not installed, so not removed
Note, selecting 'nvidia-imex-550' instead of 'nvidia-imex'
Package 'nvidia-primus-vk-wrapper:i386' is not installed, so not removed
Package 'nvidia-firmware-535-server-535.171.04' is not installed, so not removed
Package 'nvidia-firmware-535-535.161.08' is not installed, so not removed
Package 'nvidia-firmware-550-server-550.67' is not installed, so not removed
Package 'nvidia-firmware-550-550.54.15' is not installed, so not removed
Package 'nvidia-settings' is not installed, so not removed
Package 'nvidia-prime' is not installed, so not removed
Package 'nvidia-common' is not installed, so not removed
Package 'nvidia-cuda-toolkit' is not installed, so not removed
Package 'nvidia-cuda-dev' is not installed, so not removed
Package 'nvidia-vaapi-driver' is not installed, so not removed
Package 'nvidia-driver-525' is not installed, so not removed
Package 'nvidia-driver-525-server' is not installed, so not removed
Package 'nvidia-driver-535' is not installed, so not removed
Package 'nvidia-driver-535-server' is not installed, so not removed
Package 'nvidia-primus-vk-wrapper' is not installed, so not removed
Package 'nvidia-fabricmanager-470' is not installed, so not removed
Package 'nvidia-fabricmanager-535' is not installed, so not removed
Package 'nvidia-fabricmanager-550' is not installed, so not removed
Package 'nvidia-cg-toolkit' is not installed, so not removed
Package 'nvidia-cudnn' is not installed, so not removed
Package 'nvidia-opencl-dev' is not installed, so not removed
Package 'nvidia-profiler' is not installed, so not removed
Package 'nvidia-cg-dev' is not installed, so not removed
Package 'nvidia-cg-doc' is not installed, so not removed
Package 'nvidia-compute-utils-510' is not installed, so not removed
Package 'nvidia-compute-utils-535' is not installed, so not removed
Package 'nvidia-compute-utils-515' is not installed, so not removed
Package 'nvidia-compute-utils-515-server' is not installed, so not removed
Package 'nvidia-compute-utils-535-server' is not installed, so not removed
Package 'nvidia-compute-utils-520' is not installed, so not removed
Package 'nvidia-compute-utils-525' is not installed, so not removed
Package 'nvidia-compute-utils-525-server' is not installed, so not removed
Package 'nvidia-compute-utils-550-server' is not installed, so not removed
Package 'nvidia-cuda-gdb' is not installed, so not removed
Package 'nvidia-cuda-toolkit-doc' is not installed, so not removed
Package 'nvidia-cuda-samples' is not installed, so not removed
Package 'nvidia-visual-profiler' is not installed, so not removed
Package 'nvidia-cuda-toolkit-gcc' is not installed, so not removed
Package 'nvidia-dkms-510' is not installed, so not removed
Package 'nvidia-dkms-535' is not installed, so not removed
Package 'nvidia-dkms-515' is not installed, so not removed
Package 'nvidia-dkms-515-open' is not installed, so not removed
Package 'nvidia-dkms-535-open' is not installed, so not removed
Package 'nvidia-dkms-515-server' is not installed, so not removed
Package 'nvidia-dkms-535-server' is not installed, so not removed
Package 'nvidia-dkms-520' is not installed, so not removed
Package 'nvidia-dkms-520-open' is not installed, so not removed
Package 'nvidia-dkms-525' is not installed, so not removed
Package 'nvidia-dkms-525-open' is not installed, so not removed
Package 'nvidia-dkms-525-server' is not installed, so not removed
Package 'nvidia-dkms-550' is not installed, so not removed
Package 'nvidia-kernel-source-550' is not installed, so not removed
Package 'nvidia-kernel-common-550' is not installed, so not removed
Package 'nvidia-firmware-550-550.67' is not installed, so not removed
Package 'nvidia-dkms-550-open' is not installed, so not removed
Package 'nvidia-kernel-source-550-open' is not installed, so not removed
Package 'nvidia-dkms-550-server' is not installed, so not removed
Package 'nvidia-kernel-source-550-server' is not installed, so not removed
Package 'nvidia-kernel-common-550-server' is not installed, so not removed
Package 'nvidia-firmware-550-server-550.54.15' is not installed, so not removed
Package 'nvidia-dkms-550-server-open' is not installed, so not removed
Package 'nvidia-kernel-source-550-server-open' is not installed, so not removed
Package 'nvidia-driver-510' is not installed, so not removed
Package 'nvidia-driver-515' is not installed, so not removed
Package 'nvidia-driver-515-open' is not installed, so not removed
Package 'nvidia-driver-535-open' is not installed, so not removed
Package 'nvidia-driver-515-server' is not installed, so not removed
Package 'nvidia-driver-520' is not installed, so not removed
Package 'nvidia-driver-520-open' is not installed, so not removed
Package 'nvidia-driver-525-open' is not installed, so not removed
Package 'nvidia-driver-550-open' is not installed, so not removed
Package 'nvidia-compute-utils-550' is not installed, so not removed
Package 'nvidia-utils-550' is not installed, so not removed
Package 'nvidia-driver-550-server' is not installed, so not removed
Package 'nvidia-utils-550-server' is not installed, so not removed
Package 'nvidia-driver-550-server-open' is not installed, so not removed
Package 'nvidia-fabricmanager-460' is not installed, so not removed
Package 'nvidia-fabricmanager-515' is not installed, so not removed
Package 'nvidia-fabricmanager-525' is not installed, so not removed
Package 'nvidia-fabricmanager-dev-460' is not installed, so not removed
Package 'nvidia-fabricmanager-dev-470' is not installed, so not removed
Package 'nvidia-fabricmanager-dev-515' is not installed, so not removed
Package 'nvidia-fabricmanager-dev-535' is not installed, so not removed
Package 'nvidia-fabricmanager-dev-525' is not installed, so not removed
Package 'nvidia-fabricmanager-dev-550' is not installed, so not removed
Package 'nvidia-fs-dkms' is not installed, so not removed
Package 'nvidia-headless-510' is not installed, so not removed
Package 'nvidia-headless-535' is not installed, so not removed
Package 'nvidia-headless-515' is not installed, so not removed
Package 'nvidia-headless-515-open' is not installed, so not removed
Package 'nvidia-headless-535-open' is not installed, so not removed
Package 'nvidia-headless-515-server' is not installed, so not removed
Package 'nvidia-headless-535-server' is not installed, so not removed
Package 'nvidia-headless-520' is not installed, so not removed
Package 'nvidia-headless-520-open' is not installed, so not removed
Package 'nvidia-headless-525' is not installed, so not removed
Package 'nvidia-headless-525-open' is not installed, so not removed
Package 'nvidia-headless-525-server' is not installed, so not removed
Package 'nvidia-headless-550' is not installed, so not removed
Package 'nvidia-headless-no-dkms-550' is not installed, so not removed
Package 'nvidia-headless-550-open' is not installed, so not removed
Package 'nvidia-headless-no-dkms-550-open' is not installed, so not removed
Package 'nvidia-headless-550-server' is not installed, so not removed
Package 'nvidia-headless-no-dkms-550-server' is not installed, so not removed
Package 'nvidia-headless-550-server-open' is not installed, so not removed
Package 'nvidia-headless-no-dkms-550-server-open' is not installed, so not removed
Package 'nvidia-headless-no-dkms-510' is not installed, so not removed
Package 'nvidia-headless-no-dkms-535' is not installed, so not removed
Package 'nvidia-headless-no-dkms-515' is not installed, so not removed
Package 'nvidia-headless-no-dkms-515-open' is not installed, so not removed
Package 'nvidia-headless-no-dkms-535-open' is not installed, so not removed
Package 'nvidia-headless-no-dkms-515-server' is not installed, so not removed
Package 'nvidia-headless-no-dkms-535-server' is not installed, so not removed
Package 'nvidia-headless-no-dkms-520' is not installed, so not removed
Package 'nvidia-headless-no-dkms-520-open' is not installed, so not removed
Package 'nvidia-headless-no-dkms-525' is not installed, so not removed
Package 'nvidia-headless-no-dkms-525-open' is not installed, so not removed
Package 'nvidia-headless-no-dkms-525-server' is not installed, so not removed
Package 'nvidia-imex-550' is not installed, so not removed
Package 'nvidia-kernel-common-510' is not installed, so not removed
Package 'nvidia-kernel-common-535' is not installed, so not removed
Package 'nvidia-kernel-common-515' is not installed, so not removed
Package 'nvidia-kernel-common-515-server' is not installed, so not removed
Package 'nvidia-kernel-common-535-server' is not installed, so not removed
Package 'nvidia-kernel-common-520' is not installed, so not removed
Package 'nvidia-kernel-common-525' is not installed, so not removed
Package 'nvidia-kernel-common-525-server' is not installed, so not removed
Package 'nvidia-kernel-source-510' is not installed, so not removed
Package 'nvidia-kernel-source-535' is not installed, so not removed
Package 'nvidia-kernel-source-515' is not installed, so not removed
Package 'nvidia-kernel-source-515-open' is not installed, so not removed
Package 'nvidia-kernel-source-535-open' is not installed, so not removed
Package 'nvidia-kernel-source-515-server' is not installed, so not removed
Package 'nvidia-kernel-source-535-server' is not installed, so not removed
Package 'nvidia-kernel-source-520' is not installed, so not removed
Package 'nvidia-kernel-source-520-open' is not installed, so not removed
Package 'nvidia-kernel-source-525' is not installed, so not removed
Package 'nvidia-kernel-source-525-open' is not installed, so not removed
Package 'nvidia-kernel-source-525-server' is not installed, so not removed
Package 'nvidia-modprobe' is not installed, so not removed
Package 'nvidia-primus-vk-common' is not installed, so not removed
Package 'nvidia-utils-510' is not installed, so not removed
Package 'nvidia-utils-535' is not installed, so not removed
Package 'nvidia-utils-515' is not installed, so not removed
Package 'nvidia-utils-515-server' is not installed, so not removed
Package 'nvidia-utils-535-server' is not installed, so not removed
Package 'nvidia-utils-520' is not installed, so not removed
Package 'nvidia-utils-525' is not installed, so not removed
Package 'nvidia-utils-525-server' is not installed, so not removed
Package 'nvidia-kernel-common-470' is not installed, so not removed
Package 'nvidia-dkms-470' is not installed, so not removed
Package 'nvidia-kernel-common-470-server' is not installed, so not removed
Package 'nvidia-dkms-470-server' is not installed, so not removed
Package 'nvidia-dkms-535-server-open' is not installed, so not removed
Package 'nvidia-compute-utils-460' is not installed, so not removed
Package 'nvidia-compute-utils-470' is not installed, so not removed
Package 'nvidia-compute-utils-460-server' is not installed, so not removed
Package 'nvidia-compute-utils-470-server' is not installed, so not removed
Package 'nvidia-compute-utils-465' is not installed, so not removed
Package 'nvidia-compute-utils-530' is not installed, so not removed
Package 'nvidia-dkms-460' is not installed, so not removed
Package 'nvidia-dkms-460-server' is not installed, so not removed
Package 'nvidia-dkms-465' is not installed, so not removed
Package 'nvidia-kernel-source-470' is not installed, so not removed
Package 'nvidia-kernel-source-470-server' is not installed, so not removed
Package 'nvidia-dkms-530' is not installed, so not removed
Package 'nvidia-dkms-530-open' is not installed, so not removed
Package 'nvidia-firmware-535-535.171.04' is not installed, so not removed
Package 'nvidia-firmware-535-server-535.161.08' is not installed, so not removed
Package 'nvidia-kernel-source-535-server-open' is not installed, so not removed
Package 'nvidia-driver-460' is not installed, so not removed
Package 'nvidia-driver-470' is not installed, so not removed
Package 'nvidia-driver-460-server' is not installed, so not removed
Package 'nvidia-driver-470-server' is not installed, so not removed
Package 'nvidia-driver-465' is not installed, so not removed
Package 'nvidia-utils-470' is not installed, so not removed
Package 'nvidia-utils-470-server' is not installed, so not removed
Package 'nvidia-driver-530' is not installed, so not removed
Package 'nvidia-driver-530-open' is not installed, so not removed
Package 'nvidia-driver-535-server-open' is not installed, so not removed
Package 'nvidia-driver-550' is not installed, so not removed
Package 'nvidia-headless-460' is not installed, so not removed
Package 'nvidia-headless-470' is not installed, so not removed
Package 'nvidia-headless-460-server' is not installed, so not removed
Package 'nvidia-headless-470-server' is not installed, so not removed
Package 'nvidia-headless-465' is not installed, so not removed
Package 'nvidia-headless-no-dkms-470' is not installed, so not removed
Package 'nvidia-headless-no-dkms-470-server' is not installed, so not removed
Package 'nvidia-headless-530' is not installed, so not removed
Package 'nvidia-headless-530-open' is not installed, so not removed
Package 'nvidia-headless-535-server-open' is not installed, so not removed
Package 'nvidia-headless-no-dkms-535-server-open' is not installed, so not removed
Package 'nvidia-headless-no-dkms-460' is not installed, so not removed
Package 'nvidia-headless-no-dkms-460-server' is not installed, so not removed
Package 'nvidia-headless-no-dkms-465' is not installed, so not removed
Package 'nvidia-headless-no-dkms-530' is not installed, so not removed
Package 'nvidia-headless-no-dkms-530-open' is not installed, so not removed
Package 'nvidia-kernel-common-460' is not installed, so not removed
Package 'nvidia-kernel-common-460-server' is not installed, so not removed
Package 'nvidia-kernel-common-465' is not installed, so not removed
Package 'nvidia-kernel-common-530' is not installed, so not removed
Package 'nvidia-kernel-source-460' is not installed, so not removed
Package 'nvidia-kernel-source-460-server' is not installed, so not removed
Package 'nvidia-kernel-source-465' is not installed, so not removed
Package 'nvidia-kernel-source-530' is not installed, so not removed
Package 'nvidia-kernel-source-530-open' is not installed, so not removed
Package 'nvidia-utils-460' is not installed, so not removed
Package 'nvidia-utils-460-server' is not installed, so not removed
Package 'nvidia-utils-465' is not installed, so not removed
Package 'nvidia-utils-530' is not installed, so not removed
Package 'nvidia-firmware-550-550.90.07' is not installed, so not removed
Package 'nvidia-firmware-550-server-550.90.07' is not installed, so not removed
Package 'nvidia-firmware-535-535.183.01' is not installed, so not removed
Package 'nvidia-firmware-535-server-535.183.01' is not installed, so not removed
0 to upgrade, 0 to newly install, 0 to remove and 5 not to upgrade.


```

I tried the second and Nvidia items were still listed, but I shut down with a view to trying the 2nd code again.
After reboot I couldn't log in.  I type my password and it reverts back to the login screen.  I tried Ubuntu, xububtu and all the same.  I tried Ubuntu Wayland and that I got in but no network...

Huston, we have a problem!PS I'm using my phone to type to you.

Fyi.  Just booted again into Recovery Mode.  I note new entries.
Linux 6.8.0-1006-oracle
Linux 6.8.0-lowlatency

OK, UPDATE AGAIN.  In Revoivery I scrolled down to the Generic and loaded fine.  So need to REMOVE the two oracle and lowlatency items.

Output from the 2nd code
```
apt list --installed|grep nvidia

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

bumblebee-nvidia/noble,now 3.2.1-29ubuntu3 amd64 [installed]
libnvidia-cfg1-535/noble-updates,noble-security,now 535.183.01-0ubuntu0.24.04.1 amd64 [installed,automatic]
libnvidia-common-535/noble-updates,noble-updates,noble-security,noble-security,now 535.183.01-0ubuntu0.24.04.1 all [installed,automatic]
libnvidia-compute-535/noble-updates,noble-security,now 535.183.01-0ubuntu0.24.04.1 amd64 [installed,automatic]
libnvidia-compute-535/noble-updates,noble-security,now 535.183.01-0ubuntu0.24.04.1 i386 [installed]
libnvidia-decode-535/noble-updates,noble-security,now 535.183.01-0ubuntu0.24.04.1 i386 [installed]
libnvidia-encode-535/noble-updates,noble-security,now 535.183.01-0ubuntu0.24.04.1 i386 [installed]
libnvidia-fbc1-535/noble-updates,noble-security,now 535.183.01-0ubuntu0.24.04.1 i386 [installed]
libnvidia-gl-535/noble-updates,noble-security,now 535.183.01-0ubuntu0.24.04.1 i386 [installed]
linux-nvidia-tools-host/noble-updates,noble-updates,noble-security,noble-security,now 6.8.0-1009.9 all [installed]
linux-objects-nvidia-535-6.8.0-1006-oracle/noble-updates,noble-security,now 6.8.0-1006.6+1 amd64 [installed,automatic]
linux-objects-nvidia-535-server-6.8.0-38-generic/noble-updates,noble-security,now 6.8.0-38.38+1 amd64 [installed]
linux-signatures-nvidia-6.8.0-1006-oracle/noble-updates,noble-security,now 6.8.0-1006.6+1 amd64 [installed,automatic]
xserver-xorg-video-nvidia-535/noble-updates,noble-security,now 535.183.01-0ubuntu0.24.04.1 amd64 [installed,automatic]


```

---

### Post by Jonners59 on 2024-07-17
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293980&stc=1[/IMG]  All nvidia items installed as per Synaptic - screenshot of filter.  Can I simply uninstall these from here?

---

### Post by #&amp;thj^% on 2024-07-17
I really hate ubunt-drivers, I'll never use it, as you can see why now....

Give me some time I need to be able to understand why it's not removed with "purge"

---

### Post by #&amp;thj^% on 2024-07-17
> **Jonners59 said:**
>  All nvidia items installed as per Synaptic - screenshot of filter.  Can I simply uninstall these from here?
Yes please try that first.

EDIT: This is a brand new install I had Ubuntu-Drivers let it do it's thing, and I got "nvidia-driver-535" I then ran the remove command as above, all went well.
Then I installed via CLI nvidia-driver-555 after a reboot though not directly after the removal.
Now:
```
 nvidia-smi
Wed Jul 17 14:19:01 2024       
+-----------------------------------------------------------------------------------------+
| NVIDIA-SMI 555.52.04              Driver Version: 555.52.04      CUDA Version: 12.5     |
|-----------------------------------------+------------------------+----------------------+
| GPU  Name                 Persistence-M | Bus-Id          Disp.A | Volatile Uncorr. ECC |
| Fan  Temp   Perf          Pwr:Usage/Cap |           Memory-Usage | GPU-Util  Compute M. |
|                                         |                        |               MIG M. |
|=========================================+========================+======================|
|   0  NVIDIA GeForce RTX 3050 ...    Off |   00000000:01:00.0 Off |                  N/A |
| N/A   30C    P0              8W /   60W |      15MiB /   4096MiB |      0%      Default |
|                                         |                        |                  N/A |
+-----------------------------------------+------------------------+----------------------+
                                                                                         
+-----------------------------------------------------------------------------------------+
| Processes:                                                                              |
|  GPU   GI   CI        PID   Type   Process name                              GPU Memory |
|        ID   ID                                                               Usage      |
|=========================================================================================|
|    0   N/A  N/A      2317      G   /usr/lib/xorg/Xorg                              4MiB |
+-----------------------------------------------------------------------------------------+

```

My Dear Friend Jonner59 is all this worth it?
By now with fresh clean install you should up and running now. (Just Saying :) )

---

### Post by Jonners59 on 2024-07-17
ok...  is it not safe to remove all those items in Synaptic, via Synaptic Package Manager?

---

### Post by #&amp;thj^% on 2024-07-17
> **Jonners59 said:**
> ok...  is it not safe to remove all those items in Synaptic, via Synaptic Package Manager?

I can't see one reason why it wouldn't be safe.

Remember I'm blind to see what your screen show you. :)

EDIT I can see though that "apt is not recognizing"  any of what it shows as installed.

This system is not worth fixing, not what you wanted to hear but.....

Please back-up what you want to keep to your Media-Back-up Drive and consider a fresh spanking clean system..:)

```
sudo dmesg | grep 'loading NVIDIA'
[sudo] password for me: 
[   12.255731] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  555.52.04  Tue Jun  4 13:54:58 UTC 2024

```

---

### Post by Jonners59 on 2024-07-18
> **1fallen said:**
> EDIT I can see though that "apt is not recognizing"  any of what it shows as installed.

This system is not worth fixing, not what you wanted to hear but.....

Please back-up what you want to keep to your Media-Back-up Drive and consider a fresh spanking clean system..:)

```
sudo dmesg | grep 'loading NVIDIA'
[sudo] password for me: 
[   12.255731] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  555.52.04  Tue Jun  4 13:54:58 UTC 2024

```

TBH I have never found a way to restore and have the layout, settings and apps installed as I had before such a recovery, as nice as it may seem.
Also, the problem is that you are the expert and I am not so, and we are in different time zones.  There is a gap between exchanges and as you said you can't see the laptop.  In real time we have spent no more than an hour on this.

That said
Today I booted in and went to synaptic and 
1. searched 6.8.0-38 and highlighted all the lowlatency items for complete removal  Carried out that action
2. I then searched 6.8.0-1006  And did same.
3. I then selected reinstall for the 6.8.0-38-generic

I then also did a terminal cmd you gave to look for nvidia ```
apt list --installed|grep nvidi
``` and got my list and then JUST highlighted those for removal in Synaptic. and I completed the action.

I then ran your cmd to look for nvidia items and none existed.  I rebooted with fingers crossed and all is good and working.  I did your cmd to search for nvidia items and it was empty
```
 apt list --installed|grep nvidia

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.


```

A search on nvidia website gives 550-100 as the very latest driver.  I have downloaded the *.run file....

I have since completed the cmd ```
sudo apt install nvidia-driver-550 nvidia-dkms-550
``` and re run ```
apt list --installed|grep nvidi
``` and done a couple of reboots.  All is as you stated EXCEPT in Additional Drivers, it will only allow "manually installed driver" and will not let me change it.  The others are greyed out, and there is no 550.  I may run the downloaded driver I got directly from Nvidia.

OK before trying the Nvidia downloaded driver I found this cmd which I am trying:```
sudo ubuntu-drivers autoinstall
```  And that worked, and gave me 535 (propria try, tested) automatically.

What's next?

I guess tidying up these:
```
E: The repository 'https://ppa.launchpadcontent.net/mafoelffen/system-info/ubuntu noble Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
N: Skipping acquisition of configured file 'main/binary-i386/Packages', as repository 'https://dl.google.com/linux/chrome/deb stable InRelease' doesn't support architecture 'i386'
W: https://ppa.launchpadcontent.net/yannubuntu/boot-repair/ubuntu/dists/noble/InRelease: Signature by key 3C48D16124B50277AF10D27F32B18A1260D8DA0B uses weak algorithm (rsa1024)
N: Skipping acquisition of configured file 'main/binary-i386/Packages', as repository 'https://packages.microsoft.com/repos/edge stable InRelease' doesn't support architecture 'i386'
N: Missing Signed-By in the sources.list(5) entry for 'https://repo.skype.com/deb'
N: Missing Signed-By in the sources.list(5) entry for 'https://packages.microsoft.com/repos/ms-teams'
N: Missing Signed-By in the sources.list(5) entry for 'https://esm.ubuntu.com/infra/ubuntu'
N: Missing Signed-By in the sources.list(5) entry for 'https://esm.ubuntu.com/infra/ubuntu'


```


I read on a number of blogs that Microsoft were not updating signatures and the like for their products, so IF I am to continue using them, which I shall, then I guess I'll have to live with these three\: Chrome, Teams and Skype.
```

N: Skipping acquisition of configured file 'main/binary-i386/Packages',  as repository 'https://dl.google.com/linux/chrome/deb stable InRelease'  doesn't support architecture 'i386'
N: Missing Signed-By in the sources.list(5) entry for 'https://repo.skype.com/deb'
N: Missing Signed-By in the sources.list(5) entry for 'https://packages.microsoft.com/repos/ms-teams'
N: Skipping acquisition of configured file  'main/binary-i386/Packages',  as repository  'https://packages.microsoft.com/repos/edge stable  InRelease' doesn't  support architecture 'i386'
```

That leaves these
```

E: The repository  'https://ppa.launchpadcontent.net/mafoelffen/system-info/ubuntu noble  Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W:  https://ppa.launchpadcontent.net/yannubuntu/boot-repair/ubuntu/dists/noble/InRelease:  Signature by key 3C48D16124B50277AF10D27F32B18A1260D8DA0B uses weak  algorithm (rsa1024)
N: Missing Signed-By in the sources.list(5) entry for 'https://esm.ubuntu.com/infra/ubuntu'
N: Missing Signed-By in the sources.list(5) entry for 'https://esm.ubuntu.com/infra/ubuntu'


```

---

### Post by #&amp;thj^% on 2024-07-18
Jonner59, No, time is not an issue, with me at all, I'm here till the dying end. Sometimes it just appears we was wasting our time.

Things described to me so far, has left me with the impression that this system has a lot of cruft, or degraded applications.

The mere fact you can only use Ubuntu-Drivers to install nVidia is one case I see, but you seem happy you have a verified working driver ATM

Please just stay on nVidia driver from the repos. And there is a PPA with I feel there is better support but your mileage may vary. ;)

The PPA is found here: [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
 
The 550.78 is listed as Current new feature branch release: 550.78
Avoid the Beta drivers listed there.


But every time you want or need a different driver version you must Un-install the current driver first.

Will you show me this please:
```
cd /etc/apt/sources.list.d/ && ls -la
```

---

### Post by Jonners59 on 2024-07-18
> **1fallen said:**
> Jonner59, No, time is not an issue, with me at all, I'm here till the dying end. Sometimes it just appears we was wasting our time.

Things described to me so far, has left me with the impression that this system has a lot of cruft, or degraded applications.

The mere fact you can only use Ubuntu-Drivers to install nVidia is one case I see, but you seem happy you have a verified working driver ATM

I was nearly addressing your concern in your last reply, that it was taking ages.


> **1fallen said:**
> Please just stay on nVidia driver from the repos. And there is a PPA with I feel there is better support but your mileage may vary. ;)

The PPA is found here: [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
 
The 550.78 is listed as Current new feature branch release: 550.78
Avoid the Beta drivers listed there.


But every time you want or need a different driver version you must Un-install the current driver first.


Added the repo using the code shown on the site The PPA is found here: [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa) site code
```
sudo add-apt-repository ppa:graphics-drivers/ppa
```

Hopefully that will keep me honest, well my laptop.

> **1fallen said:**
> Will you show me this please:
```
cd /etc/apt/sources.list.d/ && ls -la
```

Does this help?

```
cd /etc/apt/sources.list.d/ && ls -la
total 184
drwxr-xr-x 2 root root  4096 Jul 18 17:34 .
drwxr-xr-x 8 root root  4096 Jul 18 17:28 ..
-rw-r--r-- 1 root root   221 Jun  9 12:14 danielrichter2007-ubuntu-grub-customizer-kinetic.list.distUpgrade
-rw-r--r-- 1 root root     0 Jun 12 09:02 danielrichter2007-ubuntu-grub-customizer-kinetic.sources
-rw-r--r-- 1 root root     0 Jun 12 09:02 danielrichter2007-ubuntu-grub-customizer-kinetic.sources.save
-rw-r--r-- 1 root root  1245 Jul 15 22:08 danielrichter2007-ubuntu-grub-customizer-noble.sources.save
-rw-r--r-- 1 root root   191 Jun  9 12:14 google-chrome.list.distUpgrade
-rw-r--r-- 1 root root 15460 Jul 18 17:34 google-chrome.sources
-rw-r--r-- 1 root root 15460 Jul 18 16:51 google-chrome.sources.save
-rw-r--r-- 1 root root  9438 Jul 18 17:34 graphics-drivers-ubuntu-ppa-noble.sources
-rw-r--r-- 1 root root   203 Jun  9 12:14 iconnor-ubuntu-zoneminder-1_34-jammy.list.distUpgrade
-rw-r--r-- 1 root root   166 Nov 12  2022 iconnor-ubuntu-zoneminder-1_34-jammy.list.save
-rw-r--r-- 1 root root     0 Jun 12 08:55 iconnor-ubuntu-zoneminder-1_34-jammy.sources
-rw-r--r-- 1 root root     0 Jun 12 08:55 iconnor-ubuntu-zoneminder-1_34-jammy.sources.save
-rw-r--r-- 1 root root  1796 Jul 18 17:34 mafoelffen-ubuntu-system-info-noble.sources
-rw-r--r-- 1 root root  1796 Jul 18 16:51 mafoelffen-ubuntu-system-info-noble.sources.save
-rw-r--r-- 1 root root   194 Jun  9 12:14 microsoft-edge.list.distUpgrade
-rw-r--r-- 1 root root  1075 Jul 18 17:34 microsoft-edge.sources
-rw-r--r-- 1 root root  1063 Jul 18 16:51 microsoft-edge.sources.save
-rw-r--r-- 1 root root   205 Jun  9 12:14 minetestdevs-ubuntu-daily-builds-lunar.list.distUpgrade
-rw-r--r-- 1 root root     0 Jun 12 08:55 minetestdevs-ubuntu-daily-builds-lunar.sources
-rw-r--r-- 1 root root     0 Jun 12 08:55 minetestdevs-ubuntu-daily-builds-lunar.sources.save
-rw-r--r-- 1 root root   193 Jun  9 12:14 minetestdevs-ubuntu-stable-lunar.list.distUpgrade
-rw-r--r-- 1 root root     0 Jun 12 08:55 minetestdevs-ubuntu-stable-lunar.sources
-rw-r--r-- 1 root root     0 Jun 12 08:55 minetestdevs-ubuntu-stable-lunar.sources.save
-rw-r--r-- 1 root root    91 Jun  9 12:14 skype-stable.list.distUpgrade
-rw-r--r-- 1 root root    56 Nov 12  2022 skype-stable.list.save
-rw-r--r-- 1 root root    88 Jul 18 17:34 skype-stable.sources
-rw-r--r-- 1 root root    88 Jul 18 16:51 skype-stable.sources.save
-rw-r--r-- 1 root root   296 Jun  9 12:14 steam-beta.list.distUpgrade
-rw-r--r-- 1 root root   228 Jun  9 12:14 steam-stable.list.distUpgrade
-rw-r--r-- 1 root root   231 Jun  9 12:14 teams.list.distUpgrade
-rw-r--r-- 1 root root   196 Nov 12  2022 teams.list.save
-rw-r--r-- 1 root root   107 Jul 18 17:34 teams.sources
-rw-r--r-- 1 root root   107 Jul 18 16:51 teams.sources.save
-rw-r--r-- 1 root root     0 Jun 12 08:54 third-party.sources
-rw-r--r-- 1 root root     0 Jun 12 08:54 third-party.sources.save
-rw-r--r-- 1 root root   278 Jun  9 12:14 ubuntu-esm-infra.list.distUpgrade
-rw-r--r-- 1 root root   270 Nov 12  2022 ubuntu-esm-infra.list.save
-rw-r--r-- 1 root root   119 Jul 18 17:34 ubuntu-esm-infra.sources
-rw-r--r-- 1 root root   119 Jul 18 16:51 ubuntu-esm-infra.sources.save
-rw-r--r-- 1 root root   223 Jul 18 17:34 ubuntu.sources
-rw-r--r-- 1 root root   223 Jul 18 16:51 ubuntu.sources.save
-rw-r--r-- 1 root root    84 Jun 21 21:31 waydroid.list.distUpgrade
-rw-r--r-- 1 root root   236 Jun  9 12:14 yannubuntu-ubuntu-boot-repair-jammy.list.distUpgrade
-rw-r--r-- 1 root root   162 Nov 12  2022 yannubuntu-ubuntu-boot-repair-jammy.list.save
-rw-r--r-- 1 root root     0 Jun 12 09:02 yannubuntu-ubuntu-boot-repair-jammy.sources
-rw-r--r-- 1 root root     0 Jun 12 09:02 yannubuntu-ubuntu-boot-repair-jammy.sources.save
-rw-r--r-- 1 root root   702 Jul 18 17:34 yannubuntu-ubuntu-boot-repair-noble.sources
-rw-r--r-- 1 root root   702 Jul 18 16:51 yannubuntu-ubuntu-boot-repair-noble.sources.save

```

---

### Post by #&amp;thj^% on 2024-07-18
> **Jonners59 said:**
> 
Does this help?

```
cd /etc/apt/sources.list.d/ && ls -la
total 184
drwxr-xr-x 2 root root  4096 Jul 18 17:34 .
drwxr-xr-x 8 root root  4096 Jul 18 17:28 ..
-rw-r--r-- 1 root root   221 Jun  9 12:14 danielrichter2007-ubuntu-grub-customizer-kinetic.list.distUpgrade
-rw-r--r-- 1 root root     0 Jun 12 09:02 danielrichter2007-ubuntu-grub-customizer-kinetic.sources
-rw-r--r-- 1 root root     0 Jun 12 09:02 danielrichter2007-ubuntu-grub-customizer-kinetic.sources.save
-rw-r--r-- 1 root root  1245 Jul 15 22:08 danielrichter2007-ubuntu-grub-customizer-noble.sources.save
-rw-r--r-- 1 root root   191 Jun  9 12:14 google-chrome.list.distUpgrade
-rw-r--r-- 1 root root 15460 Jul 18 17:34 google-chrome.sources
-rw-r--r-- 1 root root 15460 Jul 18 16:51 google-chrome.sources.save
-rw-r--r-- 1 root root  9438 Jul 18 17:34 graphics-drivers-ubuntu-ppa-noble.sources
-rw-r--r-- 1 root root   203 Jun  9 12:14 iconnor-ubuntu-zoneminder-1_34-jammy.list.distUpgrade
-rw-r--r-- 1 root root   166 Nov 12  2022 iconnor-ubuntu-zoneminder-1_34-jammy.list.save
-rw-r--r-- 1 root root     0 Jun 12 08:55 iconnor-ubuntu-zoneminder-1_34-jammy.sources
-rw-r--r-- 1 root root     0 Jun 12 08:55 iconnor-ubuntu-zoneminder-1_34-jammy.sources.save
-rw-r--r-- 1 root root  1796 Jul 18 17:34 mafoelffen-ubuntu-system-info-noble.sources
-rw-r--r-- 1 root root  1796 Jul 18 16:51 mafoelffen-ubuntu-system-info-noble.sources.save
-rw-r--r-- 1 root root   194 Jun  9 12:14 microsoft-edge.list.distUpgrade
-rw-r--r-- 1 root root  1075 Jul 18 17:34 microsoft-edge.sources
-rw-r--r-- 1 root root  1063 Jul 18 16:51 microsoft-edge.sources.save
-rw-r--r-- 1 root root   205 Jun  9 12:14 minetestdevs-ubuntu-daily-builds-lunar.list.distUpgrade
-rw-r--r-- 1 root root     0 Jun 12 08:55 minetestdevs-ubuntu-daily-builds-lunar.sources
-rw-r--r-- 1 root root     0 Jun 12 08:55 minetestdevs-ubuntu-daily-builds-lunar.sources.save
-rw-r--r-- 1 root root   193 Jun  9 12:14 minetestdevs-ubuntu-stable-lunar.list.distUpgrade
-rw-r--r-- 1 root root     0 Jun 12 08:55 minetestdevs-ubuntu-stable-lunar.sources
-rw-r--r-- 1 root root     0 Jun 12 08:55 minetestdevs-ubuntu-stable-lunar.sources.save
-rw-r--r-- 1 root root    91 Jun  9 12:14 skype-stable.list.distUpgrade
-rw-r--r-- 1 root root    56 Nov 12  2022 skype-stable.list.save
-rw-r--r-- 1 root root    88 Jul 18 17:34 skype-stable.sources
-rw-r--r-- 1 root root    88 Jul 18 16:51 skype-stable.sources.save
-rw-r--r-- 1 root root   296 Jun  9 12:14 steam-beta.list.distUpgrade
-rw-r--r-- 1 root root   228 Jun  9 12:14 steam-stable.list.distUpgrade
-rw-r--r-- 1 root root   231 Jun  9 12:14 teams.list.distUpgrade
-rw-r--r-- 1 root root   196 Nov 12  2022 teams.list.save
-rw-r--r-- 1 root root   107 Jul 18 17:34 teams.sources
-rw-r--r-- 1 root root   107 Jul 18 16:51 teams.sources.save
-rw-r--r-- 1 root root     0 Jun 12 08:54 third-party.sources
-rw-r--r-- 1 root root     0 Jun 12 08:54 third-party.sources.save
-rw-r--r-- 1 root root   278 Jun  9 12:14 ubuntu-esm-infra.list.distUpgrade
-rw-r--r-- 1 root root   270 Nov 12  2022 ubuntu-esm-infra.list.save
-rw-r--r-- 1 root root   119 Jul 18 17:34 ubuntu-esm-infra.sources
-rw-r--r-- 1 root root   119 Jul 18 16:51 ubuntu-esm-infra.sources.save
-rw-r--r-- 1 root root   223 Jul 18 17:34 ubuntu.sources
-rw-r--r-- 1 root root   223 Jul 18 16:51 ubuntu.sources.save
-rw-r--r-- 1 root root    84 Jun 21 21:31 waydroid.list.distUpgrade
-rw-r--r-- 1 root root   236 Jun  9 12:14 yannubuntu-ubuntu-boot-repair-jammy.list.distUpgrade
-rw-r--r-- 1 root root   162 Nov 12  2022 yannubuntu-ubuntu-boot-repair-jammy.list.save
-rw-r--r-- 1 root root     0 Jun 12 09:02 yannubuntu-ubuntu-boot-repair-jammy.sources
-rw-r--r-- 1 root root     0 Jun 12 09:02 yannubuntu-ubuntu-boot-repair-jammy.sources.save
-rw-r--r-- 1 root root   702 Jul 18 17:34 yannubuntu-ubuntu-boot-repair-noble.sources
-rw-r--r-- 1 root root   702 Jul 18 16:51 yannubuntu-ubuntu-boot-repair-noble.sources.save

```

It helps a lot yes.
Good Grief, That is one big mess, is there any reason why if we clear all the junk out of your sources that you just can't re-add the ones you want/need to keep?

---

### Post by Jonners59 on 2024-07-18
No, you recommend as you see fit.  I do use TEAMS, SKYPE and CHROME.

Steam is there for my youngest.
and I do also use Boot-Repair

You pluck away as you see fit.

---

### Post by #&amp;thj^% on 2024-07-18
Lets start with this:
```
cd /etc/apt/sources.list.d
sudo rm -rf  danielrichter2007-ubuntu-grub-customizer-kinetic.list.distUpgrade danielrichter2007-ubuntu-grub-customizer-kinetic.sources danielrichter2007-ubuntu-grub-customizer-kinetic.sources.save danielrichter2007-ubuntu-grub-customizer-noble.sources.save iconnor-ubuntu-zoneminder-1_34-jammy.list.distUpgrade  iconnor-ubuntu-zoneminder-1_34-jammy.list.save  iconnor-ubuntu-zoneminder-1_34-jammy.sources iconnor-ubuntu-zoneminder-1_34-jammy.sources.save  mafoelffen-ubuntu-system-info-noble.sources  mafoelffen-ubuntu-system-info-noble.sources.save minetestdevs-ubuntu-daily-builds-lunar.list.distUpgrade minetestdevs-ubuntu-daily-builds-lunar.sources minetestdevs-ubuntu-daily-builds-lunar.sources.save minetestdevs-ubuntu-stable-lunar.list.distUpgrade minetestdevs-ubuntu-stable-lunar.sources minetestdevs-ubuntu-stable-lunar.sources.save skype-stable.list.distUpgrade skype-stable.list.save skype-stable.sources skype-stable.sources.save steam-beta.list.distUpgrade steam-stable.list.distUpgrade third-party.sources third-party.sources.save waydroid.list.distUpgrade yannubuntu-ubuntu-boot-repair-jammy.list.distUpgrade yannubuntu-ubuntu-boot-repair-jammy.list.save  yannubuntu-ubuntu-boot-repair-jammy.sources  yannubuntu-ubuntu-boot-repair-jammy.sources.save
```
Boot repair I left you with just Noble source.

And Now run and show me:
```
sudo apt update
```

---

### Post by Jonners59 on 2024-07-18
> **1fallen said:**
> Lets start with this:
```
cd /etc/apt/sources.list.d
sudo rm -rf  danielrichter2007-ubuntu-grub-customizer-kinetic.list.distUpgrade danielrichter2007-ubuntu-grub-customizer-kinetic.sources danielrichter2007-ubuntu-grub-customizer-kinetic.sources.save danielrichter2007-ubuntu-grub-customizer-noble.sources.save iconnor-ubuntu-zoneminder-1_34-jammy.list.distUpgrade  iconnor-ubuntu-zoneminder-1_34-jammy.list.save  iconnor-ubuntu-zoneminder-1_34-jammy.sources iconnor-ubuntu-zoneminder-1_34-jammy.sources.save  mafoelffen-ubuntu-system-info-noble.sources  mafoelffen-ubuntu-system-info-noble.sources.save minetestdevs-ubuntu-daily-builds-lunar.list.distUpgrade minetestdevs-ubuntu-daily-builds-lunar.sources minetestdevs-ubuntu-daily-builds-lunar.sources.save minetestdevs-ubuntu-stable-lunar.list.distUpgrade minetestdevs-ubuntu-stable-lunar.sources minetestdevs-ubuntu-stable-lunar.sources.save skype-stable.list.distUpgrade skype-stable.list.save skype-stable.sources skype-stable.sources.save steam-beta.list.distUpgrade steam-stable.list.distUpgrade third-party.sources third-party.sources.save waydroid.list.distUpgrade yannubuntu-ubuntu-boot-repair-jammy.list.distUpgrade yannubuntu-ubuntu-boot-repair-jammy.list.save  yannubuntu-ubuntu-boot-repair-jammy.sources  yannubuntu-ubuntu-boot-repair-jammy.sources.save
```
Boot repair I left you with just Noble source.

And Now run and show me:
```
sudo apt update
```








```
sudo rm -rf  danielrichter2007-ubuntu-grub-customizer-kinetic.list.distUpgrade danielrichter2007-ubuntu-grub-customizer-kinetic.sources danielrichter2007-ubuntu-grub-customizer-kinetic.sources.save danielrichter2007-ubuntu-grub-customizer-noble.sources.save iconnor-ubuntu-zoneminder-1_34-jammy.list.distUpgrade  iconnor-ubuntu-zoneminder-1_34-jammy.list.save  iconnor-ubuntu-zoneminder-1_34-jammy.sources iconnor-ubuntu-zoneminder-1_34-jammy.sources.save  mafoelffen-ubuntu-system-info-noble.sources  mafoelffen-ubuntu-system-info-noble.sources.save minetestdevs-ubuntu-daily-builds-lunar.list.distUpgrade minetestdevs-ubuntu-daily-builds-lunar.sources minetestdevs-ubuntu-daily-builds-lunar.sources.save minetestdevs-ubuntu-stable-lunar.list.distUpgrade minetestdevs-ubuntu-stable-lunar.sources minetestdevs-ubuntu-stable-lunar.sources.save skype-stable.list.distUpgrade skype-stable.list.save skype-stable.sources skype-stable.sources.save steam-beta.list.distUpgrade steam-stable.list.distUpgrade third-party.sources third-party.sources.save waydroid.list.distUpgrade yannubuntu-ubuntu-boot-repair-jammy.list.distUpgrade yannubuntu-ubuntu-boot-repair-jammy.list.save  yannubuntu-ubuntu-boot-repair-jammy.sources  yannubuntu-ubuntu-boot-repair-jammy.sources.save


```

```
sudo apt update
```
```
sudo apt update
Hit:1 https://ppa.launchpadcontent.net/graphics-drivers/ppa/ubuntu noble InRelease
Hit:2 https://ppa.launchpadcontent.net/yannubuntu/boot-repair/ubuntu noble InRelease
Hit:3 https://esm.ubuntu.com/infra/ubuntu jammy-infra-security InRelease
Hit:4 https://esm.ubuntu.com/infra/ubuntu jammy-infra-updates InRelease
Hit:5 http://archive.ubuntu.com/ubuntu noble InRelease
Hit:6 http://archive.ubuntu.com/ubuntu noble-updates InRelease
Hit:7 http://archive.ubuntu.com/ubuntu noble-backports InRelease
Hit:8 http://archive.ubuntu.com/ubuntu noble-security InRelease
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
12 packages can be upgraded. Run 'apt list --upgradable' to see them.
W: https://ppa.launchpadcontent.net/yannubuntu/boot-repair/ubuntu/dists/noble/InRelease: Signature by key 3C48D16124B50277AF10D27F32B18A1260D8DA0B uses weak algorithm (rsa1024)
N: Missing Signed-By in the sources.list(5) entry for 'https://esm.ubuntu.com/infra/ubuntu'
N: Missing Signed-By in the sources.list(5) entry for 'https://esm.ubuntu.com/infra/ubuntu'


```

required this.

```
sudo apt list --upgradable
Listing... Done
gnome-shell-common/noble-updates,noble-updates 46.0-0ubuntu6~24.04.1 all [upgradable from: 46.0-0ubuntu5.1]
gnome-shell/noble-updates 46.0-0ubuntu6~24.04.1 amd64 [upgradable from: 46.0-0ubuntu5.1]
graphviz/noble-updates 2.42.2-9ubuntu0.1 amd64 [upgradable from: 2.42.2-9build1]
libboost-log1.74.0/noble 1.74.0+ds1-23.1ubuntu3 amd64 [upgradable from: 1.74.0+ds1-22ubuntu1]
libboost-regex1.74.0/noble 1.74.0+ds1-23.1ubuntu3 amd64 [upgradable from: 1.74.0+ds1-22ubuntu1]
libcdt5/noble-updates 2.42.2-9ubuntu0.1 amd64 [upgradable from: 2.42.2-9build1]
libcgraph6/noble-updates 2.42.2-9ubuntu0.1 amd64 [upgradable from: 2.42.2-9build1]
libgvc6/noble-updates 2.42.2-9ubuntu0.1 amd64 [upgradable from: 2.42.2-9build1]
libgvpr2/noble-updates 2.42.2-9ubuntu0.1 amd64 [upgradable from: 2.42.2-9build1]
liblab-gamut1/noble-updates 2.42.2-9ubuntu0.1 amd64 [upgradable from: 2.42.2-9build1]
libpathplan4/noble-updates 2.42.2-9ubuntu0.1 amd64 [upgradable from: 2.42.2-9build1]
xkb-data/noble-updates,noble-updates 2.41-2ubuntu1.1 all [upgradable from: 2.41-2ubuntu1]

```

---

### Post by #&amp;thj^% on 2024-07-18
Take the upgrade and reboot.
Is all good so far?

---

### Post by Jonners59 on 2024-07-18
Sorry, it was taking its time and not properly working.  So tried in Synaptic and then tried in Recovery -> drop to root, and then rebooted and tried again.  Better but neither not 100%, see outputs below....

```
sudo apt update
[sudo] password for jonathan: 
Hit:1 https://ppa.launchpadcontent.net/graphics-drivers/ppa/ubuntu noble InRelease
Hit:2 https://ppa.launchpadcontent.net/yannubuntu/boot-repair/ubuntu noble InRelease
Hit:3 http://archive.ubuntu.com/ubuntu noble InRelease               
Hit:4 http://archive.ubuntu.com/ubuntu noble-updates InRelease       
Hit:5 http://archive.ubuntu.com/ubuntu noble-backports InRelease
Hit:6 https://esm.ubuntu.com/infra/ubuntu jammy-infra-security InRelease
Hit:7 http://archive.ubuntu.com/ubuntu noble-security InRelease
Hit:8 https://esm.ubuntu.com/infra/ubuntu jammy-infra-updates InRelease
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
2 packages can be upgraded. Run 'apt list --upgradable' to see them.
W: https://ppa.launchpadcontent.net/yannubuntu/boot-repair/ubuntu/dists/noble/InRelease: Signature by key 3C48D16124B50277AF10D27F32B18A1260D8DA0B uses weak algorithm (rsa1024)
N: Missing Signed-By in the sources.list(5) entry for 'https://esm.ubuntu.com/infra/ubuntu'
N: Missing Signed-By in the sources.list(5) entry for 'https://esm.ubuntu.com/infra/ubuntu'
```




```
sudo apt upgrade
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  libboost-log1.74.0 libboost-regex1.74.0
0 to upgrade, 0 to newly install, 0 to remove and 2 not to upgrade.

```

---

### Post by #&amp;thj^% on 2024-07-18
Show this please:
```
nvidia-smi
```

---

### Post by Jonners59 on 2024-07-18
> **1fallen said:**
> Show this please:
```
nvidia-smi
```

```
nvidia-smi
NVIDIA-SMI has failed because it couldn't communicate with the NVIDIA driver. Make sure that the latest NVIDIA driver is installed and running.


```

---

### Post by #&amp;thj^% on 2024-07-18
](*,) I rely on you for accurate information, you told me 535 was installed and working....

Dang are you sure this is worth it??? This is just not that complicated. ;)
lets peek here:
```
dpkg -l | grep -i nvidia
```

---

### Post by Jonners59 on 2024-07-18
> **1fallen said:**
> ](*,) I rely on you for accurate information, you told me 535 was installed and working....

Dang are you sure this is worth it??? This is just not that complicated. ;)
lets peek here:
```
dpkg -l | grep -i nvidia
```

No point getting up tight with me, I am just doing as I am told.  The "working" was based on the Additional Drivers" information, as stated before.  Before it would dull out the other drivers and only show/allow manually installed driver.  Did all the messing about and then the pothers became usable, so I changed the driver.  I also stated that it is odd that we installed 550 and it isn't even listed.  It is stated as installed in Synaptic and a couple of entries below..


```
dpkg -l | grep -i nvidia
ii  bbswitch-dkms                                    0.8-15ubuntu1                                  amd64        Interface for toggling the power on NVIDIA Optimus video cards (dkms)
ii  bumblebee                                        3.2.1-29ubuntu3                                amd64        NVIDIA Optimus support for Linux
rc  bumblebee-nvidia                                 3.2.1-29ubuntu3                                amd64        NVIDIA Optimus support using the proprietary NVIDIA driver
ii  libcg:amd64                                      3.1.0013-5build1                               amd64        Nvidia Cg core runtime library
ii  libcggl:amd64                                    3.1.0013-5build1                               amd64        Nvidia Cg Opengl runtime library
ii  libnvidia-cfg1-545:amd64                         545.29.06-0ubuntu0~gpu24.04.1                  amd64        NVIDIA binary OpenGL/GLX configuration library
ii  libnvidia-common-545                             545.29.06-0ubuntu0~gpu24.04.1                  all          Shared files used by the NVIDIA libraries
rc  libnvidia-compute-535:amd64                      535.183.01-0ubuntu0.24.04.1                    amd64        NVIDIA libcompute package
rc  libnvidia-compute-535-server:amd64               535.183.01-0ubuntu0.24.04.1                    amd64        NVIDIA libcompute package
ii  libnvidia-compute-545:amd64                      545.29.06-0ubuntu0~gpu24.04.1                  amd64        NVIDIA libcompute package
ii  libnvidia-compute-545:i386                       545.29.06-0ubuntu0~gpu24.04.1                  i386         NVIDIA libcompute package
rc  libnvidia-compute-550:amd64                      550.90.07-0ubuntu0.24.04.1                     amd64        NVIDIA libcompute package
ii  libnvidia-decode-545:amd64                       545.29.06-0ubuntu0~gpu24.04.1                  amd64        NVIDIA Video Decoding runtime libraries
ii  libnvidia-decode-545:i386                        545.29.06-0ubuntu0~gpu24.04.1                  i386         NVIDIA Video Decoding runtime libraries
ii  libnvidia-encode-545:amd64                       545.29.06-0ubuntu0~gpu24.04.1                  amd64        NVENC Video Encoding runtime library
ii  libnvidia-encode-545:i386                        545.29.06-0ubuntu0~gpu24.04.1                  i386         NVENC Video Encoding runtime library
ii  libnvidia-extra-545:amd64                        545.29.06-0ubuntu0~gpu24.04.1                  amd64        Extra libraries for the NVIDIA driver
ii  libnvidia-fbc1-545:amd64                         545.29.06-0ubuntu0~gpu24.04.1                  amd64        NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-fbc1-545:i386                          545.29.06-0ubuntu0~gpu24.04.1                  i386         NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-gl-545:amd64                           545.29.06-0ubuntu0~gpu24.04.1                  amd64        NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-gl-545:i386                            545.29.06-0ubuntu0~gpu24.04.1                  i386         NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
rc  linux-modules-nvidia-525-6.5.0-26-generic        6.5.0-26.26+1                                  amd64        Linux kernel nvidia modules for version 6.5.0-26
rc  linux-modules-nvidia-535-6.5.0-27-generic        6.5.0-27.28+2                                  amd64        Linux kernel nvidia modules for version 6.5.0-27
rc  linux-modules-nvidia-535-6.5.0-28-generic        6.5.0-28.29+2                                  amd64        Linux kernel nvidia modules for version 6.5.0-28
rc  linux-modules-nvidia-535-6.5.0-35-generic        6.5.0-35.35                                    amd64        Linux kernel nvidia modules for version 6.5.0-35
rc  linux-modules-nvidia-535-6.8.0-38-generic        6.8.0-38.38+1                                  amd64        Linux kernel nvidia modules for version 6.8.0-38
rc  linux-objects-nvidia-525-6.5.0-26-generic        6.5.0-26.26+1                                  amd64        Linux kernel nvidia modules for version 6.5.0-26 (objects)
rc  linux-objects-nvidia-535-6.5.0-27-generic        6.5.0-27.28+2                                  amd64        Linux kernel nvidia modules for version 6.5.0-27 (objects)
rc  linux-objects-nvidia-535-6.5.0-28-generic        6.5.0-28.29+2                                  amd64        Linux kernel nvidia modules for version 6.5.0-28 (objects)
rc  linux-objects-nvidia-535-6.5.0-35-generic        6.5.0-35.35                                    amd64        Linux kernel nvidia modules for version 6.5.0-35 (objects)
ii  linux-objects-nvidia-535-6.8.0-38-generic        6.8.0-38.38+1                                  amd64        Linux kernel nvidia modules for version 6.8.0-38 (objects)
ii  linux-signatures-nvidia-6.8.0-38-generic         6.8.0-38.38+1                                  amd64        Linux kernel signatures for nvidia modules for version 6.8.0-38-generic
ii  nouveau-firmware                                 20091212-0ubuntu2                              all          Firmware for nVidia graphics cards
rc  nvidia-compute-utils-535                         535.183.01-0ubuntu0.24.04.1                    amd64        NVIDIA compute utilities
ii  nvidia-compute-utils-545                         545.29.06-0ubuntu0~gpu24.04.1                  amd64        NVIDIA compute utilities
rc  nvidia-compute-utils-550                         550.90.07-0ubuntu0.24.04.1                     amd64        NVIDIA compute utilities
iF  nvidia-dkms-545                                  545.29.06-0ubuntu0~gpu24.04.1                  amd64        NVIDIA DKMS package
rc  nvidia-dkms-550                                  550.90.07-0ubuntu0.24.04.1                     amd64        NVIDIA DKMS package
iU  nvidia-driver-545                                545.29.06-0ubuntu0~gpu24.04.1                  amd64        NVIDIA driver metapackage
ii  nvidia-firmware-545-545.29.06                    545.29.06-0ubuntu0~gpu24.04.1                  amd64        Firmware files used by the kernel module
rc  nvidia-kernel-common-535                         535.183.01-0ubuntu0.24.04.1                    amd64        Shared files used with the kernel module
ii  nvidia-kernel-common-545                         545.29.06-0ubuntu0~gpu24.04.1                  amd64        Shared files used with the kernel module
rc  nvidia-kernel-common-550                         550.90.07-0ubuntu0.24.04.1                     amd64        Shared files used with the kernel module
ii  nvidia-kernel-source-545                         545.29.06-0ubuntu0~gpu24.04.1                  amd64        NVIDIA kernel source package
ii  nvidia-prime                                     0.8.17.2                                       all          Tools to enable NVIDIA's Prime
ii  nvidia-settings                                  510.47.03-0ubuntu4                             amd64        Tool for configuring the NVIDIA graphics driver
ii  nvidia-utils-545                                 545.29.06-0ubuntu0~gpu24.04.1                  amd64        NVIDIA driver support binaries
ii  primus                                           0~20150328-16                                  amd64        client-side GPU offloading for NVIDIA Optimus
ii  screen-resolution-extra                          0.18.3                                         all          Extension for the nvidia-settings control panel
ii  xserver-xorg-video-nvidia-545                    545.29.06-0ubuntu0~gpu24.04.1                  amd64        NVIDIA binary Xorg driver

```

---

### Post by #&amp;thj^% on 2024-07-18
Your being overly sensitive, for anyone to help you me or anyone we need accurate facts, and less of a point of view. I care deeply for our members here, and will when logical spend all the time needed to help them achieve success.

Ok For the best chance of a better out come lets login to a X11 session.(Please do that now)
After login to X11:
```
sudo apt clean
sudo apt update
sudo apt install -f
apt policy nvidia-driver-535
```
May I see those first please.

---

### Post by Jonners59 on 2024-07-18
Sorry for taking some time.  Had to sort out things for bed time and the rest of the clan

Don't have an X11, just an Ubuntu Xorg.  How that's OK.

```
sudo apt install -f
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
0 to upgrade, 0 to newly install, 0 to remove and 3 not to upgrade.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up nvidia-dkms-545 (545.29.06-0ubuntu0~gpu24.04.1) ...
update-initramfs: deferring update (trigger activated)
INFO:Enable nvidia
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
Removing old nvidia-545.29.06 DKMS files...
Deleting module nvidia-545.29.06 completely from the DKMS tree.
Loading new nvidia-545.29.06 DKMS files...
Building for 6.8.0-38-generic
Building for architecture x86_64
Building initial module for 6.8.0-38-generic
ERROR: Cannot create report: [Errno 17] File exists: '/var/crash/nvidia-dkms-545
.0.crash'
Error! Bad return status for module build on kernel: 6.8.0-38-generic (x86_64)
Consult /var/lib/dkms/nvidia/545.29.06/build/make.log for more information.
dpkg: error processing package nvidia-dkms-545 (--configure):
 installed nvidia-dkms-545 package post-installation script subprocess returned 
error exit status 10
dpkg: dependency problems prevent configuration of nvidia-driver-545:
 nvidia-driver-545 depends on nvidia-dkms-545 (<= 545.29.06-1); however:
  Package nvidia-dkms-545 is not configured yet.
 nvidia-driver-545 depends on nvidia-dkms-545 (>= 545.29.06); however:
  Package nvidia-dkms-545 is not configured yet.

No apport report written because the error message indicates it's a follow-up er
ror from a previous failure.
                            dpkg: error processing package nvidia-driver-545 (--
configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools (0.142ubuntu25.1) ...
update-initramfs: Generating /boot/initrd.img-6.8.0-38-generic
Errors were encountered while processing:
 nvidia-dkms-545
 nvidia-driver-545
E: Sub-process /usr/bin/dpkg returned an error code (1)


```



```
japt policy nvidia-driver-535
nvidia-driver-535:
  Installed: (none)
  Candidate: 535.183.01-0ubuntu0.24.04.1
  Version table:
     535.183.01-0ubuntu0.24.04.1 500
        500 http://archive.ubuntu.com/ubuntu noble-updates/restricted amd64 Packages
        500 http://archive.ubuntu.com/ubuntu noble-security/restricted amd64 Packages
     535.171.04-0ubuntu2 500
        500 http://archive.ubuntu.com/ubuntu noble/restricted amd64 Packages
     535.154.05-0ubuntu1 500
        500 https://ppa.launchpadcontent.net/graphics-drivers/ppa/ubuntu noble/main amd64 Packages


```

Not good?

---

### Post by #&amp;thj^% on 2024-07-18
We are going to need a bit of time now, I think I have a handle on the driver problem now, but It may take up an hour or more today.

I'm good with whatever you decide, continue today or tomorrow?

---

### Post by Jonners59 on 2024-07-18
Looking in Synaptic the only driver I can find that matches the one I downloaded from Nvidia for my machine (not installed) is xserver-xorg-video-nvidia-550  It is 550.100-0ubuntu0~gpu24.04.1 which is the same as the driver they recommend.  With Synaptic it would uninstall 545

---

### Post by Jonners59 on 2024-07-18
> **1fallen said:**
> We are going to need a bit of time now, I think I have a handle on the driver problem now, but It may take up an hour or more today.

I'm good with whatever you decide, continue today or tomorrow?


Nearly missed this message.  Given the message, best tomorrow.  Starting to get late now and need to settle down.

---

### Post by #&amp;thj^% on 2024-07-18
I understand fully :)
I think we can put the driver issue to solved tomorrow.

Something to look forward to..

---

### Post by Jonners59 on 2024-07-18
:lolflag: yes

---

### Post by #&amp;thj^% on 2024-07-19
What we need to do first is update and upgrade.
```
sudo apt update && sudo apt upgrade -y
```
And if needed with updates reboot.
Now I need to see these two returns:
```
dpkg -l | grep -i nvidia |grep ii
```
And this one 
```
dpkg -l | grep -i nvidia |grep rc
```
Then we begin the tedious process of removals.

---

### Post by Jonners59 on 2024-07-19
Hiya, thank you.

Shall do that and revert.  Friday night here so just taking wife, #1 and #3 sons out for a curry and then shall do when I return and revert.
Thank you

---

### Post by #&amp;thj^% on 2024-07-19
Bring me a side  of curry please LOL

---

### Post by Jonners59 on 2024-07-19
> **1fallen said:**
> Bring me a side  of curry please LOL

Back and somewhat stuffed and drunk.  Whoops.  Would if I could, m8.

To my homework

The most common command...

```
sudo apt update && sudo apt upgrade -y
[sudo] password for jonathan: 
Hit:1 http://archive.ubuntu.com/ubuntu noble InRelease
Hit:2 http://archive.ubuntu.com/ubuntu noble-updates InRelease                 
Hit:3 http://archive.ubuntu.com/ubuntu noble-backports InRelease               
Hit:4 http://archive.ubuntu.com/ubuntu noble-security InRelease                
Hit:5 https://ppa.launchpadcontent.net/graphics-drivers/ppa/ubuntu noble InRelease
Hit:6 https://ppa.launchpadcontent.net/yannubuntu/boot-repair/ubuntu noble InRelease
Hit:7 https://esm.ubuntu.com/infra/ubuntu jammy-infra-security InRelease
Hit:8 https://esm.ubuntu.com/infra/ubuntu jammy-infra-updates InRelease
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
3 packages can be upgraded. Run 'apt list --upgradable' to see them.
W: https://ppa.launchpadcontent.net/yannubuntu/boot-repair/ubuntu/dists/noble/InRelease: Signature by key 3C48D16124B50277AF10D27F32B18A1260D8DA0B uses weak algorithm (rsa1024)
N: Missing Signed-By in the sources.list(5) entry for 'https://esm.ubuntu.com/infra/ubuntu'
N: Missing Signed-By in the sources.list(5) entry for 'https://esm.ubuntu.com/infra/ubuntu'
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  libboost-log1.74.0 libboost-regex1.74.0
The following packages will be upgraded:
  xdg-desktop-portal-gnome
1 to upgrade, 0 to newly install, 0 to remove and 2 not to upgrade.
2 not fully installed or removed.
Need to get 134 kB of archives.
After this operation, 4,096 B of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 xdg-desktop-portal-gnome amd64 46.2-0ubuntu1 [134 kB]
Fetched 134 kB in 0s (2,702 kB/s)                
(Reading database ... 907316 files and directories currently installed.)
Preparing to unpack .../xdg-desktop-portal-gnome_46.2-0ubuntu1_amd64.deb ...
Unpacking xdg-desktop-portal-gnome (46.2-0ubuntu1) over (46.0-1build1) ...
Setting up xdg-desktop-portal-gnome (46.2-0ubuntu1) ...
Setting up nvidia-dkms-545 (545.29.06-0ubuntu0~gpu24.04.1) ...
update-initramfs: deferring update (trigger activated)
INFO:Enable nvidia
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
Removing old nvidia-545.29.06 DKMS files...
Deleting module nvidia-545.29.06 completely from the DKMS tree.
Loading new nvidia-545.29.06 DKMS files...
Building for 6.8.0-38-generic
Building for architecture x86_64
Building initial module for 6.8.0-38-generic
ERROR: Cannot create report: [Errno 17] File exists: '/var/crash/nvidia-dkms-545
.0.crash'
Error! Bad return status for module build on kernel: 6.8.0-38-generic (x86_64)
Consult /var/lib/dkms/nvidia/545.29.06/build/make.log for more information.
dpkg: error processing package nvidia-dkms-545 (--configure):
 installed nvidia-dkms-545 package post-installation script subprocess returned 
error exit status 10
dpkg: dependency problems prevent configuration of nvidia-driver-545:
 nvidia-driver-545 depends on nvidia-dkms-545 (<= 545.29.06-1); however:
  Package nvidia-dkms-545 is not configured yet.
 nvidia-driver-545 depends on nvidia-dkms-545 (>= 545.29.06); however:
  Package nvidia-dkms-545 is not configured yet.

dpkg: error processing package nvidia-driver-545 (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates it's a follow-up er
ror from a previous failure.
                            Processing triggers for bamfdaemon (0.5.6+22.04.2022
0217-0ubuntu5) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for desktop-file-utils (0.27-2build1) ...
Processing triggers for gnome-menus (3.36.0-1.1ubuntu3) ...
Processing triggers for mate-menus (1.26.1-1build3) ...
Processing triggers for libglib2.0-0t64:amd64 (2.80.0-6ubuntu3.1) ...
Processing triggers for libglib2.0-0t64:i386 (2.80.0-6ubuntu3.1) ...
Processing triggers for mailcap (3.70+nmu1ubuntu1) ...
Processing triggers for initramfs-tools (0.142ubuntu25.1) ...
update-initramfs: Generating /boot/initrd.img-6.8.0-38-generic
Errors were encountered while processing:
 nvidia-dkms-545
 nvidia-driver-545
E: Sub-process /usr/bin/dpkg returned an error code (1)

```


Not sure about some of those returns.
```
dpkg -l | grep -i nvidia |grep ii
ii  bbswitch-dkms                                    0.8-15ubuntu1                                  amd64        Interface for toggling the power on NVIDIA Optimus video cards (dkms)
ii  bumblebee                                        3.2.1-29ubuntu3                                amd64        NVIDIA Optimus support for Linux
ii  libcg:amd64                                      3.1.0013-5build1                               amd64        Nvidia Cg core runtime library
ii  libcggl:amd64                                    3.1.0013-5build1                               amd64        Nvidia Cg Opengl runtime library
ii  libnvidia-cfg1-545:amd64                         545.29.06-0ubuntu0~gpu24.04.1                  amd64        NVIDIA binary OpenGL/GLX configuration library
ii  libnvidia-common-545                             545.29.06-0ubuntu0~gpu24.04.1                  all          Shared files used by the NVIDIA libraries
ii  libnvidia-compute-545:amd64                      545.29.06-0ubuntu0~gpu24.04.1                  amd64        NVIDIA libcompute package
ii  libnvidia-compute-545:i386                       545.29.06-0ubuntu0~gpu24.04.1                  i386         NVIDIA libcompute package
ii  libnvidia-decode-545:amd64                       545.29.06-0ubuntu0~gpu24.04.1                  amd64        NVIDIA Video Decoding runtime libraries
ii  libnvidia-decode-545:i386                        545.29.06-0ubuntu0~gpu24.04.1                  i386         NVIDIA Video Decoding runtime libraries
ii  libnvidia-encode-545:amd64                       545.29.06-0ubuntu0~gpu24.04.1                  amd64        NVENC Video Encoding runtime library
ii  libnvidia-encode-545:i386                        545.29.06-0ubuntu0~gpu24.04.1                  i386         NVENC Video Encoding runtime library
ii  libnvidia-extra-545:amd64                        545.29.06-0ubuntu0~gpu24.04.1                  amd64        Extra libraries for the NVIDIA driver
ii  libnvidia-fbc1-545:amd64                         545.29.06-0ubuntu0~gpu24.04.1                  amd64        NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-fbc1-545:i386                          545.29.06-0ubuntu0~gpu24.04.1                  i386         NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-gl-545:amd64                           545.29.06-0ubuntu0~gpu24.04.1                  amd64        NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-gl-545:i386                            545.29.06-0ubuntu0~gpu24.04.1                  i386         NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  linux-objects-nvidia-535-6.8.0-38-generic        6.8.0-38.38+1                                  amd64        Linux kernel nvidia modules for version 6.8.0-38 (objects)
ii  linux-signatures-nvidia-6.8.0-38-generic         6.8.0-38.38+1                                  amd64        Linux kernel signatures for nvidia modules for version 6.8.0-38-generic
ii  nouveau-firmware                                 20091212-0ubuntu2                              all          Firmware for nVidia graphics cards
ii  nvidia-compute-utils-545                         545.29.06-0ubuntu0~gpu24.04.1                  amd64        NVIDIA compute utilities
ii  nvidia-firmware-545-545.29.06                    545.29.06-0ubuntu0~gpu24.04.1                  amd64        Firmware files used by the kernel module
ii  nvidia-kernel-common-545                         545.29.06-0ubuntu0~gpu24.04.1                  amd64        Shared files used with the kernel module
ii  nvidia-kernel-source-545                         545.29.06-0ubuntu0~gpu24.04.1                  amd64        NVIDIA kernel source package
ii  nvidia-prime                                     0.8.17.2                                       all          Tools to enable NVIDIA's Prime
ii  nvidia-settings                                  510.47.03-0ubuntu4                             amd64        Tool for configuring the NVIDIA graphics driver
ii  nvidia-utils-545                                 545.29.06-0ubuntu0~gpu24.04.1                  amd64        NVIDIA driver support binaries
ii  primus                                           0~20150328-16                                  amd64        client-side GPU offloading for NVIDIA Optimus
ii  screen-resolution-extra                          0.18.3                                         all          Extension for the nvidia-settings control panel
ii  xserver-xorg-video-nvidia-545                    545.29.06-0ubuntu0~gpu24.04.1                  amd64        NVIDIA binary Xorg driver

```

```
pkg -l | grep -i nvidia |grep rc
rc  bumblebee-nvidia                                 3.2.1-29ubuntu3                                amd64        NVIDIA Optimus support using the proprietary NVIDIA driver
rc  libnvidia-compute-535:amd64                      535.183.01-0ubuntu0.24.04.1                    amd64        NVIDIA libcompute package
rc  libnvidia-compute-535-server:amd64               535.183.01-0ubuntu0.24.04.1                    amd64        NVIDIA libcompute package
rc  libnvidia-compute-550:amd64                      550.90.07-0ubuntu0.24.04.1                     amd64        NVIDIA libcompute package
rc  linux-modules-nvidia-525-6.5.0-26-generic        6.5.0-26.26+1                                  amd64        Linux kernel nvidia modules for version 6.5.0-26
rc  linux-modules-nvidia-535-6.5.0-27-generic        6.5.0-27.28+2                                  amd64        Linux kernel nvidia modules for version 6.5.0-27
rc  linux-modules-nvidia-535-6.5.0-28-generic        6.5.0-28.29+2                                  amd64        Linux kernel nvidia modules for version 6.5.0-28
rc  linux-modules-nvidia-535-6.5.0-35-generic        6.5.0-35.35                                    amd64        Linux kernel nvidia modules for version 6.5.0-35
rc  linux-modules-nvidia-535-6.8.0-38-generic        6.8.0-38.38+1                                  amd64        Linux kernel nvidia modules for version 6.8.0-38
rc  linux-objects-nvidia-525-6.5.0-26-generic        6.5.0-26.26+1                                  amd64        Linux kernel nvidia modules for version 6.5.0-26 (objects)
rc  linux-objects-nvidia-535-6.5.0-27-generic        6.5.0-27.28+2                                  amd64        Linux kernel nvidia modules for version 6.5.0-27 (objects)
rc  linux-objects-nvidia-535-6.5.0-28-generic        6.5.0-28.29+2                                  amd64        Linux kernel nvidia modules for version 6.5.0-28 (objects)
rc  linux-objects-nvidia-535-6.5.0-35-generic        6.5.0-35.35                                    amd64        Linux kernel nvidia modules for version 6.5.0-35 (objects)
rc  nvidia-compute-utils-535                         535.183.01-0ubuntu0.24.04.1                    amd64        NVIDIA compute utilities
rc  nvidia-compute-utils-550                         550.90.07-0ubuntu0.24.04.1                     amd64        NVIDIA compute utilities
rc  nvidia-dkms-550                                  550.90.07-0ubuntu0.24.04.1                     amd64        NVIDIA DKMS package
rc  nvidia-kernel-common-535                         535.183.01-0ubuntu0.24.04.1                    amd64        Shared files used with the kernel module
rc  nvidia-kernel-common-550                         550.90.07-0ubuntu0.24.04.1                     amd64        Shared files used with the kernel module
ii  nvidia-kernel-source-545                         545.29.06-0ubuntu0~gpu24.04.1                  amd64        NVIDIA kernel source package


```

---

### Post by #&amp;thj^% on 2024-07-19
Ok I have a one liner to rid all nvidia installed currently.
```
sudo apt autoremove --purge bbswitch-dkms bumblebee libcg:amd64 ibcggl:amd64 libnvidia-cfg1-545:amd64 libnvidia-common-545 libnvidia-compute-545:amd64 libnvidia-compute-545:i386 libnvidia-decode-545:amd64 libnvidia-decode-545:i386 libnvidia-encode-545:amd64 libnvidia-encode-545:i386 libnvidia-extra-545:amd64 libnvidia-fbc1-545:amd64 libnvidia-fbc1-545:i386 libnvidia-gl-545:amd64 libnvidia-gl-545:i386 linux-objects-nvidia-535-6.8.0-38-generic linux-signatures-nvidia-6.8.0-38-generic nouveau-firmware nvidia-compute-utils-545 nvidia-firmware-545-545.29.06 nvidia-kernel-common-545 nvidia-kernel-source-545 nvidia-prime nvidia-settings nvidia-utils-545 primus xserver-xorg-video-nvidia-545
```
There will be some left we can get later, and PLEASE DON"T reboot yet!
Now just for kicks run again:
```
sudo apt autoremove --purge nvidia-driver* nvidia-dkms*
```

Now if all went good show me this again:
```
dpkg -l | grep -i nvidia |grep ii
```
As soon as I see that we can install the driver.

---

### Post by Jonners59 on 2024-07-19
Output:

```
sudo apt autoremove --purge bbswitch-dkms bumblebee libcg:amd64 ibcggl:amd64 libnvidia-cfg1-545:amd64 libnvidia-common-545 libnvidia-compute-545:amd64 libnvidia-compute-545:i386 libnvidia-decode-545:amd64 libnvidia-decode-545:i386 libnvidia-encode-545:amd64 libnvidia-encode-545:i386 libnvidia-extra-545:amd64 libnvidia-fbc1-545:amd64 libnvidia-fbc1-545:i386 libnvidia-gl-545:amd64 libnvidia-gl-545:i386 linux-objects-nvidia-535-6.8.0-38-generic linux-signatures-nvidia-6.8.0-38-generic nouveau-firmware nvidia-compute-utils-545 nvidia-firmware-545-545.29.06 nvidia-kernel-common-545 nvidia-kernel-source-545 nvidia-prime nvidia-settings nvidia-utils-545 primus xserver-xorg-video-nvidia-545
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
E: Unable to locate package ibcggl:amd64

```

Seems to have failed.

I took out ```
ibcggl:amd64
```

And ran this instead.
```
sudo apt autoremove --purge bbswitch-dkms bumblebee libcg:amd64 libnvidia-cfg1-545:amd64 libnvidia-common-545 libnvidia-compute-545:amd64 libnvidia-compute-545:i386 libnvidia-decode-545:amd64 libnvidia-decode-545:i386 libnvidia-encode-545:amd64 libnvidia-encode-545:i386 libnvidia-extra-545:amd64 libnvidia-fbc1-545:amd64 libnvidia-fbc1-545:i386 libnvidia-gl-545:amd64 libnvidia-gl-545:i386 linux-objects-nvidia-535-6.8.0-38-generic linux-signatures-nvidia-6.8.0-38-generic nouveau-firmware nvidia-compute-utils-545 nvidia-firmware-545-545.29.06 nvidia-kernel-common-545 nvidia-kernel-source-545 nvidia-prime nvidia-settings nvidia-utils-545 primus xserver-xorg-video-nvidia-545
```

Result:
```
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages will be REMOVED
  bbswitch-dkms* bumblebee* libcg* libcggl* libnvidia-cfg1-545*
  libnvidia-common-545* libnvidia-compute-545* libnvidia-compute-545:i386*
  libnvidia-decode-545* libnvidia-decode-545:i386* libnvidia-encode-545*
  libnvidia-encode-545:i386* libnvidia-extra-545* libnvidia-fbc1-545*
  libnvidia-fbc1-545:i386* libnvidia-gl-545* libnvidia-gl-545:i386*
  libprimus-vk1* linux-objects-nvidia-535-6.8.0-38-generic*
  linux-signatures-nvidia-6.8.0-38-generic* nouveau-firmware*
  nvidia-compute-utils-545* nvidia-dkms-545* nvidia-driver-545*
  nvidia-firmware-545-545.29.06* nvidia-headless-545*
  nvidia-headless-no-dkms-545* nvidia-kernel-common-545*
  nvidia-kernel-source-545* nvidia-prime* nvidia-settings* nvidia-utils-545*
  primus* primus-libs* primus-vk* screen-resolution-extra*
  xserver-xorg-video-nvidia-545*
0 to upgrade, 0 to newly install, 37 to remove and 2 not to upgrade.
3 not fully installed or removed.
After this operation, 1,257 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 907319 files and directories currently installed.)
Removing nvidia-driver-545 (545.29.06-0ubuntu0~gpu24.04.1) ...
Removing nvidia-headless-545 (545.29.06-0ubuntu0~gpu24.04.1) ...
Removing nvidia-dkms-545 (545.29.06-0ubuntu0~gpu24.04.1) ...
Removing all DKMS Modules
Done.
INFO:Disable nvidia
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
update-initramfs: deferring update (trigger activated)
Removing bbswitch-dkms (0.8-15ubuntu1) ...
Module bbswitch-0.8 for kernel 6.5.0-35-generic (x86_64).
Before uninstall, this module version was ACTIVE on this kernel.

bbswitch.ko.zst:
 - Uninstallation
   - Deleting from: /lib/modules/6.5.0-35-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.
depmod...
Module bbswitch-0.8 for kernel 6.8.0-38-generic (x86_64).
Before uninstall, this module version was ACTIVE on this kernel.

bbswitch.ko.zst:
 - Uninstallation
   - Deleting from: /lib/modules/6.8.0-38-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.
depmod...
Deleting module bbswitch-0.8 completely from the DKMS tree.
Removing primus-vk (1.6.4-2) ...
Removing primus (0~20150328-16) ...
Removing bumblebee (3.2.1-29ubuntu3) ...
Removing libcggl:amd64 (3.1.0013-5build1) ...
Removing libcg:amd64 (3.1.0013-5build1) ...
Removing xserver-xorg-video-nvidia-545 (545.29.06-0ubuntu0~gpu24.04.1) ...
Removing nvidia-headless-no-dkms-545 (545.29.06-0ubuntu0~gpu24.04.1) ...
Removing libnvidia-cfg1-545:amd64 (545.29.06-0ubuntu0~gpu24.04.1) ...
Removing libnvidia-gl-545:amd64 (545.29.06-0ubuntu0~gpu24.04.1) ...
Removing libnvidia-gl-545:i386 (545.29.06-0ubuntu0~gpu24.04.1) ...
Removing libnvidia-common-545 (545.29.06-0ubuntu0~gpu24.04.1) ...
Removing libnvidia-encode-545:i386 (545.29.06-0ubuntu0~gpu24.04.1) ...
Removing libnvidia-decode-545:i386 (545.29.06-0ubuntu0~gpu24.04.1) ...
Removing libnvidia-compute-545:i386 (545.29.06-0ubuntu0~gpu24.04.1) ...
Removing nvidia-utils-545 (545.29.06-0ubuntu0~gpu24.04.1) ...
Removing nvidia-compute-utils-545 (545.29.06-0ubuntu0~gpu24.04.1) ...
Removing libnvidia-encode-545:amd64 (545.29.06-0ubuntu0~gpu24.04.1) ...
Removing libnvidia-decode-545:amd64 (545.29.06-0ubuntu0~gpu24.04.1) ...
Removing libnvidia-extra-545:amd64 (545.29.06-0ubuntu0~gpu24.04.1) ...
Removing libnvidia-fbc1-545:i386 (545.29.06-0ubuntu0~gpu24.04.1) ...
Removing libnvidia-fbc1-545:amd64 (545.29.06-0ubuntu0~gpu24.04.1) ...
Removing libprimus-vk1:amd64 (1.6.4-2) ...
Removing linux-objects-nvidia-535-6.8.0-38-generic (6.8.0-38.38+1) ...
Removing linux-signatures-nvidia-6.8.0-38-generic (6.8.0-38.38+1) ...
Removing nouveau-firmware (20091212-0ubuntu2) ...
Removing nvidia-kernel-common-545 (545.29.06-0ubuntu0~gpu24.04.1) ...
update-initramfs: deferring update (trigger activated)
Removing nvidia-firmware-545-545.29.06 (545.29.06-0ubuntu0~gpu24.04.1) ...
Removing nvidia-kernel-source-545 (545.29.06-0ubuntu0~gpu24.04.1) ...
Removing nvidia-prime (0.8.17.2) ...
Removing nvidia-settings (510.47.03-0ubuntu4) ...
Removing primus-libs:amd64 (0~20150328-16) ...
Removing screen-resolution-extra (0.18.3) ...
Removing libnvidia-compute-545:amd64 (545.29.06-0ubuntu0~gpu24.04.1) ...
Processing triggers for desktop-file-utils (0.27-2build1) ...
Processing triggers for initramfs-tools (0.142ubuntu25.1) ...
update-initramfs: Generating /boot/initrd.img-6.8.0-38-generic
Processing triggers for gnome-menus (3.36.0-1.1ubuntu3) ...
Processing triggers for mate-menus (1.26.1-1build3) ...
Processing triggers for libc-bin (2.39-0ubuntu8.2) ...
Processing triggers for man-db (2.12.0-4build2) ...
Processing triggers for mailcap (3.70+nmu1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.6+22.04.20220217-0ubuntu5) ...
Rebuilding /usr/share/applications/bamf-2.index...
(Reading database ... 906141 files and directories currently installed.)
Purging configuration files for nvidia-prime (0.8.17.2) ...
Purging configuration files for nvidia-dkms-545 (545.29.06-0ubuntu0~gpu24.04.1) 
...
update-initramfs: deferring update (trigger activated)
Purging configuration files for libnvidia-compute-545:amd64 (545.29.06-0ubuntu0~
gpu24.04.1) ...
Purging configuration files for bumblebee (3.2.1-29ubuntu3) ...
Purging configuration files for nvidia-compute-utils-545 (545.29.06-0ubuntu0~gpu
24.04.1) ...
Purging configuration files for linux-objects-nvidia-535-6.8.0-38-generic (6.8.0
-38.38+1) ...
Purging configuration files for nvidia-settings (510.47.03-0ubuntu4) ...
Purging configuration files for nvidia-kernel-common-545 (545.29.06-0ubuntu0~gpu
24.04.1) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools (0.142ubuntu25.1) ...
update-initramfs: Generating /boot/initrd.img-6.8.0-38-generic
```


 Then ran ```
sudo apt autoremove --purge nvidia-driver* nvidia-dkms*
```

Output:

 ```
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Note: selecting 'nvidia-driver-550-server' for glob 'nvidia-driver*'
Note: selecting 'nvidia-driver-555-open' for glob 'nvidia-driver*'
Note: selecting 'nvidia-driver-460-server' for glob 'nvidia-driver*'
Note: selecting 'nvidia-driver-525-open' for glob 'nvidia-driver*'
Note: selecting 'nvidia-driver-390' for glob 'nvidia-driver*'
Note: selecting 'nvidia-driver-460' for glob 'nvidia-driver*'
Note: selecting 'nvidia-driver-465' for glob 'nvidia-driver*'
Note: selecting 'nvidia-driver-470' for glob 'nvidia-driver*'
Note: selecting 'nvidia-driver-510' for glob 'nvidia-driver*'
Note: selecting 'nvidia-driver-515' for glob 'nvidia-driver*'
Note: selecting 'nvidia-driver-520' for glob 'nvidia-driver*'
Note: selecting 'nvidia-driver-525' for glob 'nvidia-driver*'
Note: selecting 'nvidia-driver-530' for glob 'nvidia-driver*'
Note: selecting 'nvidia-driver-535' for glob 'nvidia-driver*'
Note: selecting 'nvidia-driver-545' for glob 'nvidia-driver*'
Note: selecting 'nvidia-driver-550' for glob 'nvidia-driver*'
Note: selecting 'nvidia-driver-555' for glob 'nvidia-driver*'
Note: selecting 'nvidia-driver-470-server' for glob 'nvidia-driver*'
Note: selecting 'nvidia-driver-550-server-open' for glob 'nvidia-driver*'
Note: selecting 'nvidia-driver-libs' for glob 'nvidia-driver*'
Note: selecting 'nvidia-driver-545-open' for glob 'nvidia-driver*'
Note: selecting 'nvidia-driver-525-server' for glob 'nvidia-driver*'
Note: selecting 'nvidia-driver-515-open' for glob 'nvidia-driver*'
Note: selecting 'nvidia-driver-515-server' for glob 'nvidia-driver*'
Note: selecting 'nvidia-driver-535-server' for glob 'nvidia-driver*'
Note: selecting 'nvidia-driver-530-open' for glob 'nvidia-driver*'
Note: selecting 'nvidia-driver-535-server-open' for glob 'nvidia-driver*'
Note: selecting 'nvidia-driver-550-open' for glob 'nvidia-driver*'
Note: selecting 'nvidia-driver-520-open' for glob 'nvidia-driver*'
Note: selecting 'nvidia-driver-535-open' for glob 'nvidia-driver*'
Note: selecting 'nvidia-driver-binary' for glob 'nvidia-driver*'
Package 'nvidia-driver-libs' is not installed, so not removed
Note: selecting 'nvidia-dkms-470-server' for glob 'nvidia-dkms*'
Note: selecting 'nvidia-dkms-390' for glob 'nvidia-dkms*'
Note: selecting 'nvidia-dkms-550-open' for glob 'nvidia-dkms*'
Note: selecting 'nvidia-dkms-460' for glob 'nvidia-dkms*'
Note: selecting 'nvidia-dkms-465' for glob 'nvidia-dkms*'
Note: selecting 'nvidia-dkms-470' for glob 'nvidia-dkms*'
Note: selecting 'nvidia-dkms-510' for glob 'nvidia-dkms*'
Note: selecting 'nvidia-dkms-515' for glob 'nvidia-dkms*'
Note: selecting 'nvidia-dkms-520' for glob 'nvidia-dkms*'
Note: selecting 'nvidia-dkms-525' for glob 'nvidia-dkms*'
Note: selecting 'nvidia-dkms-530' for glob 'nvidia-dkms*'
Note: selecting 'nvidia-dkms-535' for glob 'nvidia-dkms*'
Note: selecting 'nvidia-dkms-545' for glob 'nvidia-dkms*'
Note: selecting 'nvidia-dkms-550' for glob 'nvidia-dkms*'
Note: selecting 'nvidia-dkms-555' for glob 'nvidia-dkms*'
Note: selecting 'nvidia-dkms-460-server' for glob 'nvidia-dkms*'
Note: selecting 'nvidia-dkms-520-open' for glob 'nvidia-dkms*'
Note: selecting 'nvidia-dkms-550-server-open' for glob 'nvidia-dkms*'
Note: selecting 'nvidia-dkms-555-open' for glob 'nvidia-dkms*'
Note: selecting 'nvidia-dkms-525-open' for glob 'nvidia-dkms*'
Note: selecting 'nvidia-dkms-515-server' for glob 'nvidia-dkms*'
Note: selecting 'nvidia-dkms-535-server' for glob 'nvidia-dkms*'
Note: selecting 'nvidia-dkms-545-open' for glob 'nvidia-dkms*'
Note: selecting 'nvidia-dkms-525-server' for glob 'nvidia-dkms*'
Note: selecting 'nvidia-dkms-515-open' for glob 'nvidia-dkms*'
Note: selecting 'nvidia-dkms-530-open' for glob 'nvidia-dkms*'
Note: selecting 'nvidia-dkms-535-server-open' for glob 'nvidia-dkms*'
Note: selecting 'nvidia-dkms-550-server' for glob 'nvidia-dkms*'
Note: selecting 'nvidia-dkms-kernel' for glob 'nvidia-dkms*'
Note: selecting 'nvidia-dkms-535-open' for glob 'nvidia-dkms*'
Package 'nvidia-driver-390' is not installed, so not removed
Package 'nvidia-driver-460' is not installed, so not removed
Package 'nvidia-driver-470' is not installed, so not removed
Package 'nvidia-driver-465' is not installed, so not removed
Package 'nvidia-driver-510' is not installed, so not removed
Package 'nvidia-driver-525' is not installed, so not removed
Package 'nvidia-driver-515' is not installed, so not removed
Package 'nvidia-driver-515-open' is not installed, so not removed
Package 'nvidia-driver-525-open' is not installed, so not removed
Package 'nvidia-driver-520' is not installed, so not removed
Package 'nvidia-driver-520-open' is not installed, so not removed
Package 'nvidia-driver-530' is not installed, so not removed
Package 'nvidia-driver-535' is not installed, so not removed
Package 'nvidia-driver-530-open' is not installed, so not removed
Package 'nvidia-driver-535-open' is not installed, so not removed
Package 'nvidia-driver-545' is not installed, so not removed
Package 'nvidia-driver-545-open' is not installed, so not removed
Package 'nvidia-driver-550' is not installed, so not removed
Package 'nvidia-driver-550-open' is not installed, so not removed
Package 'nvidia-driver-555' is not installed, so not removed
Package 'nvidia-driver-555-open' is not installed, so not removed
Package 'nvidia-driver-525-server' is not installed, so not removed
Package 'nvidia-driver-535-server' is not installed, so not removed
Package 'nvidia-driver-515-server' is not installed, so not removed
Package 'nvidia-driver-550-server' is not installed, so not removed
Package 'nvidia-driver-550-server-open' is not installed, so not removed
Package 'nvidia-driver-460-server' is not installed, so not removed
Package 'nvidia-driver-470-server' is not installed, so not removed
Package 'nvidia-driver-535-server-open' is not installed, so not removed
Package 'nvidia-dkms-390' is not installed, so not removed
Package 'nvidia-dkms-460' is not installed, so not removed
Package 'nvidia-dkms-470' is not installed, so not removed
Package 'nvidia-dkms-465' is not installed, so not removed
Package 'nvidia-dkms-510' is not installed, so not removed
Package 'nvidia-dkms-525' is not installed, so not removed
Package 'nvidia-dkms-515' is not installed, so not removed
Package 'nvidia-dkms-515-open' is not installed, so not removed
Package 'nvidia-dkms-525-open' is not installed, so not removed
Package 'nvidia-dkms-520' is not installed, so not removed
Package 'nvidia-dkms-520-open' is not installed, so not removed
Package 'nvidia-dkms-530' is not installed, so not removed
Package 'nvidia-dkms-535' is not installed, so not removed
Package 'nvidia-dkms-530-open' is not installed, so not removed
Package 'nvidia-dkms-535-open' is not installed, so not removed
Package 'nvidia-dkms-545' is not installed, so not removed
Package 'nvidia-dkms-545-open' is not installed, so not removed
Package 'nvidia-dkms-550-open' is not installed, so not removed
Package 'nvidia-dkms-555' is not installed, so not removed
Package 'nvidia-dkms-555-open' is not installed, so not removed
Package 'nvidia-dkms-515-server' is not installed, so not removed
Package 'nvidia-dkms-535-server' is not installed, so not removed
Package 'nvidia-dkms-525-server' is not installed, so not removed
Package 'nvidia-dkms-550-server' is not installed, so not removed
Package 'nvidia-dkms-550-server-open' is not installed, so not removed
Package 'nvidia-dkms-470-server' is not installed, so not removed
Package 'nvidia-dkms-535-server-open' is not installed, so not removed
Package 'nvidia-dkms-460-server' is not installed, so not removed
The following packages will be REMOVED
  nvidia-dkms-550*
0 to upgrade, 0 to newly install, 1 to remove and 2 not to upgrade.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 906133 files and directories currently installed.)
Purging configuration files for nvidia-dkms-550 (550.90.07-0ubuntu0.24.04.1) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools (0.142ubuntu25.1) ...
update-initramfs: Generating /boot/initrd.img-6.8.0-38-generic


```
   
Then ran:
```
dpkg -l | grep -i nvidia |grep ii
``` 
It simply went to the input line again.  There was no output.


FYI, why does the Nvidia Drive not appear anywhere?

---

### Post by #&amp;thj^% on 2024-07-19
Now fixed:
```

sudo apt autoremove --purge bbswitch-dkms bumblebee libcg:amd64 libcggl:amd64 libnvidia-cfg1-545:amd64 libnvidia-common-545 libnvidia-compute-545:amd64 libnvidia-compute-545:i386 libnvidia-decode-545:amd64 libnvidia-decode-545:i386 libnvidia-encode-545:amd64 libnvidia-encode-545:i386 libnvidia-extra-545:amd64 libnvidia-fbc1-545:amd64 libnvidia-fbc1-545:i386 libnvidia-gl-545:amd64 libnvidia-gl-545:i386 linux-objects-nvidia-535-6.8.0-38-generic linux-signatures-nvidia-6.8.0-38-generic nouveau-firmware nvidia-compute-utils-545 nvidia-firmware-545-545.29.06 nvidia-kernel-common-545 nvidia-kernel-source-545 nvidia-prime nvidia-settings nvidia-utils-545 primus xserver-xorg-video-nvidia-545
```
Will talk about your last question after please, Lets stay focused on our task at hand please. :)

---

### Post by Jonners59 on 2024-07-19
:-)

See below...  I removed the item.  

I run your updated version too, and had the same output as my last reply.

So, what next?

---

### Post by #&amp;thj^% on 2024-07-19
What Driver Version do you want, your card can handle all, 535 is the stable release 550 has some improvements for wayland sessions. (Gnome Only)
While you decide, may I now see this:
```
dpkg -l | grep -i nvidia |grep rc
```
mine will report this:
```
 dpkg -l | grep -i nvidia |grep rc
ii  nvidia-kernel-source-535                           535.171.04-0ubuntu2                      amd64        NVIDIA kernel source package

```

---

### Post by Jonners59 on 2024-07-19
Well, NVIDIA suggests 550-100, so I shall go with their suggestion.


Output

```
rc  bumblebee-nvidia                                 3.2.1-29ubuntu3                                amd64        NVIDIA Optimus support using the proprietary NVIDIA driver
rc  libnvidia-compute-535:amd64                      535.183.01-0ubuntu0.24.04.1                    amd64        NVIDIA libcompute package
rc  libnvidia-compute-535-server:amd64               535.183.01-0ubuntu0.24.04.1                    amd64        NVIDIA libcompute package
rc  libnvidia-compute-550:amd64                      550.90.07-0ubuntu0.24.04.1                     amd64        NVIDIA libcompute package
rc  linux-modules-nvidia-525-6.5.0-26-generic        6.5.0-26.26+1                                  amd64        Linux kernel nvidia modules for version 6.5.0-26
rc  linux-modules-nvidia-535-6.5.0-27-generic        6.5.0-27.28+2                                  amd64        Linux kernel nvidia modules for version 6.5.0-27
rc  linux-modules-nvidia-535-6.5.0-28-generic        6.5.0-28.29+2                                  amd64        Linux kernel nvidia modules for version 6.5.0-28
rc  linux-modules-nvidia-535-6.5.0-35-generic        6.5.0-35.35                                    amd64        Linux kernel nvidia modules for version 6.5.0-35
rc  linux-modules-nvidia-535-6.8.0-38-generic        6.8.0-38.38+1                                  amd64        Linux kernel nvidia modules for version 6.8.0-38
rc  linux-objects-nvidia-525-6.5.0-26-generic        6.5.0-26.26+1                                  amd64        Linux kernel nvidia modules for version 6.5.0-26 (objects)
rc  linux-objects-nvidia-535-6.5.0-27-generic        6.5.0-27.28+2                                  amd64        Linux kernel nvidia modules for version 6.5.0-27 (objects)
rc  linux-objects-nvidia-535-6.5.0-28-generic        6.5.0-28.29+2                                  amd64        Linux kernel nvidia modules for version 6.5.0-28 (objects)
rc  linux-objects-nvidia-535-6.5.0-35-generic        6.5.0-35.35                                    amd64        Linux kernel nvidia modules for version 6.5.0-35 (objects)
rc  nvidia-compute-utils-535                         535.183.01-0ubuntu0.24.04.1                    amd64        NVIDIA compute utilities
rc  nvidia-compute-utils-550                         550.90.07-0ubuntu0.24.04.1                     amd64        NVIDIA compute utilities
rc  nvidia-kernel-common-535                         535.183.01-0ubuntu0.24.04.1                    amd64        Shared files used with the kernel module
rc  nvidia-kernel-common-550                         550.90.07-0ubuntu0.24.04.1                     amd64        Shared files used with the kernel module


```

---

### Post by #&amp;thj^% on 2024-07-19
Before we do anything we still need to tidy up left-overs:
We need to git rid of any possible things that might trip up our install, run:
```
sudo apt autoremove --purge bumblebee-nvidia libnvidia-compute-535:amd64 libnvidia-compute-535-server:amd64 libnvidia-compute-550:amd64  linux-modules-nvidia-525-6.5.0-26-generic linux-modules-nvidia-535-6.5.0-27-generic linux-modules-nvidia-535-6.5.0-28-generic linux-modules-nvidia-535-6.5.0-35-generic linux-modules-nvidia-535-6.8.0-38-generic linux-objects-nvidia-525-6.5.0-26-generic linux-objects-nvidia-535-6.5.0-27-generic linux-objects-nvidia-535-6.5.0-28-generic linux-objects-nvidia-535-6.5.0-35-generic nvidia-compute-utils-535 nvidia-compute-utils-550 nvidia-kernel-common-535 nvidia-kernel-common-550
```

---

### Post by Jonners59 on 2024-07-19
Done.
Both of these had no output:
```
dpkg -l | grep -i nvidia |grep rc
```
```
dpkg -l | grep -i nvidia |grep ii
```

Need to hit tha sack soon.

---

### Post by #&amp;thj^% on 2024-07-19
Nice, now we install the driver:
```
sudo apt install nvidia-driver-550 nvidia-dkms-550
```
If it succeeds with no errors, then reboot and then prove to me it is installed:
```
nvidia-smi
```

---

### Post by Jonners59 on 2024-07-19
OK, so it seemed to go perfectly.  I rebooted and tried the ```
nvidia-smi
``` and got the table as per the screen shot attached.  Additional Drivers the list is fixed as per 2nd screen shot.[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293995&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=293996&stc=1[/IMG]

```
sudo ubuntu-drivers devices

udevadm hwdb is deprecated. Use systemd-hwdb instead.
udevadm hwdb is deprecated. Use systemd-hwdb instead.
udevadm hwdb is deprecated. Use systemd-hwdb instead.
udevadm hwdb is deprecated. Use systemd-hwdb instead.
udevadm hwdb is deprecated. Use systemd-hwdb instead.
udevadm hwdb is deprecated. Use systemd-hwdb instead.
== /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0 ==
modalias : pci:v000010DEd00001C8Csv00001462sd0000127Ebc03sc02i00
vendor   : NVIDIA Corporation
model    : GP107M [GeForce GTX 1050 Ti Mobile]
manual_install: True
driver   : nvidia-driver-535 - distro non-free
driver   : nvidia-driver-390 - third-party non-free
driver   : nvidia-driver-545 - third-party non-free recommended
driver   : nvidia-driver-470 - distro non-free
driver   : nvidia-driver-470-server - distro non-free
driver   : nvidia-driver-535-server - distro non-free
driver   : xserver-xorg-video-nouveau - distro free builtin

$ lspci -k | grep -A 2 -i "VGA"

00:02.0 VGA compatible controller: Intel Corporation CoffeeLake-H GT2 [UHD Graphics 630]
    DeviceName: Onboard - Video
    Subsystem: Micro-Star International Co., Ltd. [MSI] CoffeeLake-H GT2 [UHD Graphics 630]

$ prime-select query
nvidia

$ nvidia-settings

(nvidia-settings:22229): GLib-GObject-CRITICAL **: 23:40:19.373: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
** Message: 23:40:19.424: PRIME: Requires offloading
** Message: 23:40:19.424: PRIME: is it supported? yes
** Message: 23:40:19.457: PRIME: Usage: /usr/bin/prime-select nvidia|intel|on-demand|query
** Message: 23:40:19.457: PRIME: on-demand mode: "1"
** Message: 23:40:19.457: PRIME: is "on-demand" mode supported? yes
jonathan@GF63-Thin-9RCX:~/Desktop$ sudo ubuntu-drivers devices
udevadm hwdb is deprecated. Use systemd-hwdb instead.
udevadm hwdb is deprecated. Use systemd-hwdb instead.
udevadm hwdb is deprecated. Use systemd-hwdb instead.
udevadm hwdb is deprecated. Use systemd-hwdb instead.
udevadm hwdb is deprecated. Use systemd-hwdb instead.
udevadm hwdb is deprecated. Use systemd-hwdb instead.
== /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0 ==
modalias : pci:v000010DEd00001C8Csv00001462sd0000127Ebc03sc02i00
vendor   : NVIDIA Corporation
model    : GP107M [GeForce GTX 1050 Ti Mobile]
manual_install: True
driver   : nvidia-driver-470-server - distro non-free
driver   : nvidia-driver-390 - third-party non-free
driver   : nvidia-driver-535 - distro non-free
driver   : nvidia-driver-535-server - distro non-free
driver   : nvidia-driver-470 - distro non-free
driver   : nvidia-driver-545 - third-party non-free recommended
driver   : xserver-xorg-video-nouveau - distro free builtin

~/Desktop$ dmesg | grep -i nvidia

dmesg: read kernel buffer failed: Operation not permitted
jonathan@GF63-Thin-9RCX:~/Desktop$ sudo dmesg | grep -i nvidia
[    5.081796] nvidia: module license 'NVIDIA' taints kernel.
[    5.081804] nvidia: module license taints kernel.
[    5.468972] nvidia-nvlink: Nvlink Core is being initialized, major device number 508
[    5.473181] nvidia 0000:01:00.0: enabling device (0006 -> 0007)
[    5.696653] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  550.100  Thu Jun 27 19:04:00 UTC 2024
[    5.713815] nvidia-modeset: Loading NVIDIA Kernel Mode Setting Driver for UNIX platforms  550.100  Thu Jun 27 18:13:10 UTC 2024
[    5.987486] [drm] [nvidia-drm] [GPU ID 0x00000100] Loading driver
[    7.388800] [drm] Initialized nvidia-drm 0.0.0 20160202 for 0000:01:00.0 on minor 0
[    7.414474] nvidia_uvm: module uses symbols nvUvmInterfaceDisableAccessCntr from proprietary module nvidia, inheriting taint.
[    7.460662] nvidia-uvm: Loaded the UVM driver, major device number 506.
```

Is this correct.#?



PS need to hit the sack as I am shattered.  I'll look for your reply tomorrow AM.

---

### Post by #&amp;thj^% on 2024-07-19
See you soon.

---

### Post by Jonners59 on 2024-07-20
Good morning...
So was the output I sent last night correct/what you hoped and expected?  And what if the "Additional Drivers", is that correct?  There is no 550 listed and none can be changed, it is stuck on manual.

It's a busy day so I'll try and pop in if I can to complete any tasks.  If you think it is all good, then I guess all that is left is to give you a huge thank you and close the case as solved, though with all these replies I may do a summary - I find it helps me (and others) when looking for solutions.

I'll than grab you to help fix another, but that may have to wait until I get back from Italy in September...

---

### Post by #&amp;thj^% on 2024-07-20
The only thing i see now that I would clear up is:
```
W: https://ppa.launchpadcontent.net/yannubuntu/boot-repair/ubuntu/dists/noble/InRelease: Signature by key 3C48D16124B50277AF10D27F32B18A1260D8DA0B uses weak algorithm (rsa1024)
N: Missing Signed-By in the sources.list(5) entry for 'https://esm.ubuntu.com/infra/ubuntu'
N: Missing Signed-By in the sources.list(5) entry for 'https://esm.ubuntu.com/infra/ubuntu'
```
But yes your driver looks good now finally...

Run it for a few days it should begin to smooth out.

How are your updates and upgrades now?
```
sudo apt update && sudo apt upgrade -y
```

I won't be around much today, work work work.
> There is no 550 listed and none can be changed, it is stuck on manual.
There is bug already known to them, but to see it use:
```
apt list nvidia-driver*|grep 550

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

nvidia-driver-550-open/oracular 550.100-0ubuntu0~gpu24.10.1 amd64
nvidia-driver-550-server-open/oracular 550.54.15-0ubuntu2 amd64
nvidia-driver-550-server/oracular 550.54.15-0ubuntu2 amd64
nvidia-driver-550/oracular 550.100-0ubuntu0~gpu24.10.1 amd64

``` 

I know very little about Ubuntu-Drivers and I don't use it.

There are a few of us here that have this motto>>"Live by the GUI Die by the GUI" I just prefer CLI. :)

---

### Post by Jonners59 on 2024-07-21
> **1fallen said:**
> The only thing i see now that I would clear up is:
```
W: https://ppa.launchpadcontent.net/yannubuntu/boot-repair/ubuntu/dists/noble/InRelease: Signature by key 3C48D16124B50277AF10D27F32B18A1260D8DA0B uses weak algorithm (rsa1024)
N: Missing Signed-By in the sources.list(5) entry for 'https://esm.ubuntu.com/infra/ubuntu'
N: Missing Signed-By in the sources.list(5) entry for 'https://esm.ubuntu.com/infra/ubuntu'
```
But yes your driver looks good now finally...

Run it for a few days it should begin to smooth out.

How are your updates and upgrades now?
```
sudo apt update && sudo apt upgrade -y
```



```
sudo apt update && sudo apt upgrade -y
```

And output:

```
Get:1 https://esm.ubuntu.com/infra/ubuntu jammy-infra-security InRelease [7,450 B]
Get:2 https://esm.ubuntu.com/infra/ubuntu jammy-infra-updates InRelease [7,449 B]
Hit:3 http://archive.ubuntu.com/ubuntu noble InRelease                         
Get:4 http://archive.ubuntu.com/ubuntu noble-updates InRelease [126 kB]        
Hit:5 http://archive.ubuntu.com/ubuntu noble-backports InRelease               
Hit:6 http://archive.ubuntu.com/ubuntu noble-security InRelease                
Get:7 http://archive.ubuntu.com/ubuntu noble-updates/main i386 Packages [144 kB]
Get:8 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 Packages [266 kB]
Get:9 http://archive.ubuntu.com/ubuntu noble-updates/universe amd64 Packages [301 kB]
Get:10 http://archive.ubuntu.com/ubuntu noble-updates/universe i386 Packages [126 kB]
Hit:11 https://ppa.launchpadcontent.net/graphics-drivers/ppa/ubuntu noble InRelease
Hit:12 https://ppa.launchpadcontent.net/yannubuntu/boot-repair/ubuntu noble InRelease
Fetched 977 kB in 2s (449 kB/s)
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
2 packages can be upgraded. Run 'apt list --upgradable' to see them.
W: https://ppa.launchpadcontent.net/yannubuntu/boot-repair/ubuntu/dists/noble/InRelease: Signature by key 3C48D16124B50277AF10D27F32B18A1260D8DA0B uses weak algorithm (rsa1024)
N: Missing Signed-By in the sources.list(5) entry for 'https://esm.ubuntu.com/infra/ubuntu'
N: Missing Signed-By in the sources.list(5) entry for 'https://esm.ubuntu.com/infra/ubuntu'
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  libboost-log1.74.0 libboost-regex1.74.0
0 to upgrade, 0 to newly install, 0 to remove and 2 not to upgrade.


```


> **1fallen said:**
> I won't be around much today, work work work.

So you are the one....  I knew someone was keeping the global ecconomy going...


> **1fallen said:**
> There is bug already known to them, but to see it use:
```
apt list nvidia-driver*|grep 550

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

nvidia-driver-550-open/oracular 550.100-0ubuntu0~gpu24.10.1 amd64
nvidia-driver-550-server-open/oracular 550.54.15-0ubuntu2 amd64
nvidia-driver-550-server/oracular 550.54.15-0ubuntu2 amd64
nvidia-driver-550/oracular 550.100-0ubuntu0~gpu24.10.1 amd64

``` 


Noted.  I tried ```
apt list nvidia-driver*|grep 550
``` and got the same warning, but nothing listed.  I tried just entering each line, it just said  "no such file or directory" for each of the drivers...

I then went in to Synaptic and typed just the first driver in search and it showed it as not installed.  So I selected it for installation and it came back with.
[B]To be removed
[/B]      nvidia-dkms-550
      nvidia-driver-550
      nvidia-kernel--source-550
[B]To be installed
[/B]      nvidia-dkms-550-open
      nvidia-kernel-source-550-open



I cancelled the operation at this point, awaiting your feedback.  I looked at a couple of the others, and they listed a whole string of different things to install and remove, which looked not too dissimilar to the ones we removed earlier.  Seems I have something different.

> **1fallen said:**
> I know very little about Ubuntu-Drivers and I don't use it.

There are a few of us here that have this motto>>"Live by the GUI Die by the GUI" I just prefer CLI. :smile:

:-D

Have a great day at work.....

---

### Post by #&amp;thj^% on 2024-07-21
If "nvidia-smi" still shows a working driver, why are you trying to install another driver?

Dose 
```
nvidia-smi
```
Show this table:
```
 nvidia-smi
Sun Jul 21 08:42:02 2024       
+-----------------------------------------------------------------------------------------+
| NVIDIA-SMI 555.58.02              Driver Version: 555.58.02      CUDA Version: 12.5     |
|-----------------------------------------+------------------------+----------------------+
| GPU  Name                 Persistence-M | Bus-Id          Disp.A | Volatile Uncorr. ECC |
| Fan  Temp   Perf          Pwr:Usage/Cap |           Memory-Usage | GPU-Util  Compute M. |
|                                         |                        |               MIG M. |
|=========================================+========================+======================|
|   0  NVIDIA GeForce RTX 3050 ...    Off |   00000000:01:00.0 Off |                  N/A |
| N/A   29C    P8              3W /   60W |      23MiB /   4096MiB |      0%      Default |
|                                         |                        |                  N/A |
+-----------------------------------------+------------------------+----------------------+
                                                                                         
+-----------------------------------------------------------------------------------------+
| Processes:                                                                              |
|  GPU   GI   CI        PID   Type   Process name                              GPU Memory |
|        ID   ID                                                               Usage      |
|=========================================================================================|
|    0   N/A  N/A      1520      G   /usr/lib/Xorg                                   4MiB |
+-----------------------------------------------------------------------------------------+

```
```
apt list nvidia-driver*
nvidia-driver-460-server/oracular 470.256.02-0ubuntu1 amd64
nvidia-driver-460/oracular 470.256.02-0ubuntu1 amd64
nvidia-driver-465/oracular 470.256.02-0ubuntu1 amd64
nvidia-driver-470-server/oracular 470.256.02-0ubuntu1 amd64
nvidia-driver-470/oracular 470.256.02-0ubuntu1 amd64
nvidia-driver-510/oracular 525.147.05-0ubuntu2 amd64
nvidia-driver-515-open/oracular 525.147.05-0ubuntu2 amd64
nvidia-driver-515-server/oracular 525.147.05-0ubuntu2 amd64
nvidia-driver-515/oracular 525.147.05-0ubuntu2 amd64
nvidia-driver-520-open/oracular 525.147.05-0ubuntu2 amd64
nvidia-driver-520/oracular 525.147.05-0ubuntu2 amd64
nvidia-driver-525-open/oracular 525.147.05-0ubuntu2 amd64
nvidia-driver-525-server/oracular 525.147.05-0ubuntu2 amd64
nvidia-driver-525/oracular 525.147.05-0ubuntu2 amd64
nvidia-driver-530-open/oracular 535.171.04-0ubuntu2 amd64
nvidia-driver-530/oracular 535.171.04-0ubuntu2 amd64
nvidia-driver-535-open/oracular 535.171.04-0ubuntu2 amd64
nvidia-driver-535-server-open/oracular 535.161.08-0ubuntu2 amd64
nvidia-driver-535-server/oracular 535.161.08-0ubuntu2 amd64
nvidia-driver-535/oracular 535.171.04-0ubuntu2 amd64
nvidia-driver-550-open/oracular 550.100-0ubuntu0~gpu24.10.1 amd64
nvidia-driver-550-server-open/oracular 550.54.15-0ubuntu2 amd64
nvidia-driver-550-server/oracular 550.54.15-0ubuntu2 amd64
nvidia-driver-550/oracular 550.100-0ubuntu0~gpu24.10.1 amd64
nvidia-driver-555-open/oracular 555.52.04-0ubuntu0~gpu24.10.1 amd64
nvidia-driver-555/oracular,now 555.52.04-0ubuntu0~gpu24.10.1 amd64 [installed]

```

Look with:
```
apt policy nvidia-driver-550 nvidia-dkms-550
nvidia-driver-550:
  [COLOR="#FF0000"]Installed: (none)[/COLOR]
  Candidate: 550.100-0ubuntu0~gpu24.10.1
  Version table:
     550.100-0ubuntu0~gpu24.10.1 500
        500 https://ppa.launchpadcontent.net/graphics-drivers/ppa/ubuntu oracular/main amd64 Packages
     550.67-0ubuntu3 500
        500 http://archive.ubuntu.com/ubuntu oracular/restricted amd64 Packages
nvidia-dkms-550:
 [COLOR="#FF0000"] Installed: (none)[/COLOR]
  Candidate: 550.100-0ubuntu0~gpu24.10.1
  Version table:
     550.100-0ubuntu0~gpu24.10.1 500
        500 https://ppa.launchpadcontent.net/graphics-drivers/ppa/ubuntu oracular/main amd64 Packages
     550.67-0ubuntu3 500
        500 http://archive.ubuntu.com/ubuntu oracular/multiverse amd64 Packages

```
Mine is different:
```
apt policy nvidia-driver-555 nvidia-dkms-555
nvidia-driver-555:
 [COLOR="#FF0000"] Installed: 555.52.04-0ubuntu0~gpu24.10.1[/COLOR]
  Candidate: 555.52.04-0ubuntu0~gpu24.10.1
  Version table:
 *** 555.52.04-0ubuntu0~gpu24.10.1 500
        500 https://ppa.launchpadcontent.net/graphics-drivers/ppa/ubuntu oracular/main amd64 Packages
        100 /var/lib/dpkg/status
nvidia-dkms-555:
 [COLOR="#FF0000"] Installed: 555.52.04-0ubuntu0~gpu24.10.1[/COLOR]
  Candidate: 555.52.04-0ubuntu0~gpu24.10.1
  Version table:
 *** 555.52.04-0ubuntu0~gpu24.10.1 500
        500 https://ppa.launchpadcontent.net/graphics-drivers/ppa/ubuntu oracular/main amd64 Packages
        100 /var/lib/dpkg/status

```

---

### Post by Jonners59 on 2024-07-21
> **1fallen said:**
> If "nvidia-smi" still shows a working driver, why are you trying to install another driver?

I'm not and didn't.  I noted yours was different and compared, as per my reply below.



Dose 
```
nvidia-smi
```
Show this table:
```
 nvidia-smi
Sun Jul 21 08:42:02 2024       
+-----------------------------------------------------------------------------------------+
| NVIDIA-SMI 555.58.02              Driver Version: 555.58.02      CUDA Version: 12.5     |
|-----------------------------------------+------------------------+----------------------+
| GPU  Name                 Persistence-M | Bus-Id          Disp.A | Volatile Uncorr. ECC |
| Fan  Temp   Perf          Pwr:Usage/Cap |           Memory-Usage | GPU-Util  Compute M. |
|                                         |                        |               MIG M. |
|=========================================+========================+======================|
|   0  NVIDIA GeForce RTX 3050 ...    Off |   00000000:01:00.0 Off |                  N/A |
| N/A   29C    P8              3W /   60W |      23MiB /   4096MiB |      0%      Default |
|                                         |                        |                  N/A |
+-----------------------------------------+------------------------+----------------------+
                                                                                         
+-----------------------------------------------------------------------------------------+
| Processes:                                                                              |
|  GPU   GI   CI        PID   Type   Process name                              GPU Memory |
|        ID   ID                                                               Usage      |
|=========================================================================================|
|    0   N/A  N/A      1520      G   /usr/lib/Xorg                                   4MiB |
+-----------------------------------------------------------------------------------------+

```[/QUOTE]


Here's mine.  I did post it the otrher day, noting ERR which I didn't know of it were an error or correct, but you said it was fine so I pressed on.

```
$ nvidia-smi
Sun Jul 21 16:48:39 2024       
+-----------------------------------------------------------------------------------------+
| NVIDIA-SMI 550.100                Driver Version: 550.100        CUDA Version: 12.4     |
|-----------------------------------------+------------------------+----------------------+
| GPU  Name                 Persistence-M | Bus-Id          Disp.A | Volatile Uncorr. ECC |
| Fan  Temp   Perf          Pwr:Usage/Cap |           Memory-Usage | GPU-Util  Compute M. |
|                                         |                        |               MIG M. |
|=========================================+========================+======================|
|   0  NVIDIA GeForce GTX 1050 Ti     Off |   00000000:01:00.0 Off |                  N/A |
| N/A   50C    P8             N/A / ERR!  |     285MiB /   4096MiB |      2%      Default |
|                                         |                        |                  N/A |
+-----------------------------------------+------------------------+----------------------+
                                                                                         
+-----------------------------------------------------------------------------------------+
| Processes:                                                                              |
|  GPU   GI   CI        PID   Type   Process name                              GPU Memory |
|        ID   ID                                                               Usage      |
|=========================================================================================|
|    0   N/A  N/A      9446      G   /usr/lib/xorg/Xorg                             86MiB |
|    0   N/A  N/A     11425      G   ...irefox/4539/usr/lib/firefox/firefox        196MiB |
+-----------------------------------------------------------------------------------------+


```


> **1fallen said:**
> ```
apt list nvidia-driver*
nvidia-driver-460-server/oracular 470.256.02-0ubuntu1 amd64
nvidia-driver-460/oracular 470.256.02-0ubuntu1 amd64
nvidia-driver-465/oracular 470.256.02-0ubuntu1 amd64
nvidia-driver-470-server/oracular 470.256.02-0ubuntu1 amd64
nvidia-driver-470/oracular 470.256.02-0ubuntu1 amd64
nvidia-driver-510/oracular 525.147.05-0ubuntu2 amd64
nvidia-driver-515-open/oracular 525.147.05-0ubuntu2 amd64
nvidia-driver-515-server/oracular 525.147.05-0ubuntu2 amd64
nvidia-driver-515/oracular 525.147.05-0ubuntu2 amd64
nvidia-driver-520-open/oracular 525.147.05-0ubuntu2 amd64
nvidia-driver-520/oracular 525.147.05-0ubuntu2 amd64
nvidia-driver-525-open/oracular 525.147.05-0ubuntu2 amd64
nvidia-driver-525-server/oracular 525.147.05-0ubuntu2 amd64
nvidia-driver-525/oracular 525.147.05-0ubuntu2 amd64
nvidia-driver-530-open/oracular 535.171.04-0ubuntu2 amd64
nvidia-driver-530/oracular 535.171.04-0ubuntu2 amd64
nvidia-driver-535-open/oracular 535.171.04-0ubuntu2 amd64
nvidia-driver-535-server-open/oracular 535.161.08-0ubuntu2 amd64
nvidia-driver-535-server/oracular 535.161.08-0ubuntu2 amd64
nvidia-driver-535/oracular 535.171.04-0ubuntu2 amd64
nvidia-driver-550-open/oracular 550.100-0ubuntu0~gpu24.10.1 amd64
nvidia-driver-550-server-open/oracular 550.54.15-0ubuntu2 amd64
nvidia-driver-550-server/oracular 550.54.15-0ubuntu2 amd64
nvidia-driver-550/oracular 550.100-0ubuntu0~gpu24.10.1 amd64apt list nvidia-driver*
Listing... Done
nvidia-driver-390/noble 390.157-0ubuntu7 amd64
nvidia-driver-460-server/noble-updates,noble-security 470.256.02-0ubuntu0.24.04.1 amd64
nvidia-driver-460/noble-updates,noble-security 470.256.02-0ubuntu0.24.04.1 amd64
nvidia-driver-465/noble-updates,noble-security 470.256.02-0ubuntu0.24.04.1 amd64
nvidia-driver-470-server/noble-updates,noble-security 470.256.02-0ubuntu0.24.04.1 amd64
nvidia-driver-470/noble-updates,noble-security 470.256.02-0ubuntu0.24.04.1 amd64
nvidia-driver-510/noble 525.147.05-0ubuntu2 amd64
nvidia-driver-515-open/noble 525.147.05-0ubuntu2 amd64
nvidia-driver-515-server/noble 525.147.05-0ubuntu2 amd64
nvidia-driver-515/noble 525.147.05-0ubuntu2 amd64
nvidia-driver-520-open/noble 525.147.05-0ubuntu2 amd64
nvidia-driver-520/noble 525.147.05-0ubuntu2 amd64
nvidia-driver-525-open/noble 525.147.05-0ubuntu2 amd64
nvidia-driver-525-server/noble 525.147.05-0ubuntu2 amd64
nvidia-driver-525/noble 525.147.05-0ubuntu2 amd64
nvidia-driver-530-open/noble-updates,noble-security 535.183.01-0ubuntu0.24.04.1 amd64
nvidia-driver-530/noble-updates,noble-security 535.183.01-0ubuntu0.24.04.1 amd64
nvidia-driver-535-open/noble-updates,noble-security 535.183.01-0ubuntu0.24.04.1 amd64
nvidia-driver-535-server-open/noble-updates,noble-security 535.183.01-0ubuntu0.24.04.1 amd64
nvidia-driver-535-server/noble-updates,noble-security 535.183.01-0ubuntu0.24.04.1 amd64
nvidia-driver-535/noble-updates,noble-security 535.183.01-0ubuntu0.24.04.1 amd64
nvidia-driver-545-open/noble 545.29.06-0ubuntu0~gpu24.04.1 amd64
nvidia-driver-545/noble 545.29.06-0ubuntu0~gpu24.04.1 amd64
nvidia-driver-550-open/noble 550.100-0ubuntu0~gpu24.04.1 amd64
nvidia-driver-550-server-open/noble-updates,noble-security 550.90.07-0ubuntu0.24.04.1 amd64
nvidia-driver-550-server/noble-updates,noble-security 550.90.07-0ubuntu0.24.04.1 amd64
nvidia-driver-550/noble,now 550.100-0ubuntu0~gpu24.04.1 amd64 [installed]
nvidia-driver-555-open/noble 555.52.04-0ubuntu0~gpu24.04.1 amd64
nvidia-driver-555/noble 555.52.04-0ubuntu0~gpu24.04.1 amd64

nvidia-driver-555-open/oracular 555.52.04-0ubuntu0~gpu24.10.1 amd64
nvidia-driver-555/oracular,now 555.52.04-0ubuntu0~gpu24.10.1 amd64 [installed]

```

Here's mine:

```
apt list nvidia-driver*
Listing... Done
nvidia-driver-390/noble 390.157-0ubuntu7 amd64
nvidia-driver-460-server/noble-updates,noble-security 470.256.02-0ubuntu0.24.04.1 amd64
nvidia-driver-460/noble-updates,noble-security 470.256.02-0ubuntu0.24.04.1 amd64
nvidia-driver-465/noble-updates,noble-security 470.256.02-0ubuntu0.24.04.1 amd64
nvidia-driver-470-server/noble-updates,noble-security 470.256.02-0ubuntu0.24.04.1 amd64
nvidia-driver-470/noble-updates,noble-security 470.256.02-0ubuntu0.24.04.1 amd64
nvidia-driver-510/noble 525.147.05-0ubuntu2 amd64
nvidia-driver-515-open/noble 525.147.05-0ubuntu2 amd64
nvidia-driver-515-server/noble 525.147.05-0ubuntu2 amd64
nvidia-driver-515/noble 525.147.05-0ubuntu2 amd64
nvidia-driver-520-open/noble 525.147.05-0ubuntu2 amd64
nvidia-driver-520/noble 525.147.05-0ubuntu2 amd64
nvidia-driver-525-open/noble 525.147.05-0ubuntu2 amd64
nvidia-driver-525-server/noble 525.147.05-0ubuntu2 amd64
nvidia-driver-525/noble 525.147.05-0ubuntu2 amd64
nvidia-driver-530-open/noble-updates,noble-security 535.183.01-0ubuntu0.24.04.1 amd64
nvidia-driver-530/noble-updates,noble-security 535.183.01-0ubuntu0.24.04.1 amd64
nvidia-driver-535-open/noble-updates,noble-security 535.183.01-0ubuntu0.24.04.1 amd64
nvidia-driver-535-server-open/noble-updates,noble-security 535.183.01-0ubuntu0.24.04.1 amd64
nvidia-driver-535-server/noble-updates,noble-security 535.183.01-0ubuntu0.24.04.1 amd64
nvidia-driver-535/noble-updates,noble-security 535.183.01-0ubuntu0.24.04.1 amd64
nvidia-driver-545-open/noble 545.29.06-0ubuntu0~gpu24.04.1 amd64
nvidia-driver-545/noble 545.29.06-0ubuntu0~gpu24.04.1 amd64
nvidia-driver-550-open/noble 550.100-0ubuntu0~gpu24.04.1 amd64
nvidia-driver-550-server-open/noble-updates,noble-security 550.90.07-0ubuntu0.24.04.1 amd64
nvidia-driver-550-server/noble-updates,noble-security 550.90.07-0ubuntu0.24.04.1 amd64
nvidia-driver-550/noble,now 550.100-0ubuntu0~gpu24.04.1 amd64 [installed]
nvidia-driver-555-open/noble 555.52.04-0ubuntu0~gpu24.04.1 amd64
nvidia-driver-555/noble 555.52.04-0ubuntu0~gpu24.04.1 amd64
```

> **1fallen said:**
> Look with:
```
apt policy nvidia-driver-550 nvidia-dkms-550
nvidia-driver-550:
  [COLOR=#FF0000]Installed: (none)[/COLOR]
  Candidate: 550.100-0ubuntu0~gpu24.10.1
  Version table:
     550.100-0ubuntu0~gpu24.10.1 500
        500 https://ppa.launchpadcontent.net/graphics-drivers/ppa/ubuntu oracular/main amd64 Packages
     550.67-0ubuntu3 500
        500 http://archive.ubuntu.com/ubuntu oracular/restricted amd64 Packages
nvidia-dkms-550:
 [COLOR=#FF0000] Installed: (none)[/COLOR]
  Candidate: 550.100-0ubuntu0~gpu24.10.1
  Version table:
     550.100-0ubuntu0~gpu24.10.1 500
        500 https://ppa.launchpadcontent.net/graphics-drivers/ppa/ubuntu oracular/main amd64 Packages
     550.67-0ubuntu3 500
        500 http://archive.ubuntu.com/ubuntu oracular/multiverse amd64 Packages

```


Here's mine
```
apt policy nvidia-driver-550 nvidia-dkms-550
nvidia-driver-550:
  Installed: 550.100-0ubuntu0~gpu24.04.1
  Candidate: 550.100-0ubuntu0~gpu24.04.1
  Version table:
 *** 550.100-0ubuntu0~gpu24.04.1 500
        500 https://ppa.launchpadcontent.net/graphics-drivers/ppa/ubuntu noble/main amd64 Packages
        100 /var/lib/dpkg/status
     550.90.07-0ubuntu0.24.04.1 500
        500 http://archive.ubuntu.com/ubuntu noble-updates/restricted amd64 Packages
        500 http://archive.ubuntu.com/ubuntu noble-security/restricted amd64 Packages
     550.67-0ubuntu3 500
        500 http://archive.ubuntu.com/ubuntu noble/restricted amd64 Packages
nvidia-dkms-550:
  Installed: 550.100-0ubuntu0~gpu24.04.1
  Candidate: 550.100-0ubuntu0~gpu24.04.1
  Version table:
 *** 550.100-0ubuntu0~gpu24.04.1 500
        500 https://ppa.launchpadcontent.net/graphics-drivers/ppa/ubuntu noble/main amd64 Packages
        100 /var/lib/dpkg/status
     550.90.07-0ubuntu0.24.04.1 500
        500 http://archive.ubuntu.com/ubuntu noble-updates/multiverse amd64 Packages
        500 http://archive.ubuntu.com/ubuntu noble-security/multiverse amd64 Packages
     550.67-0ubuntu3 500
        500 http://archive.ubuntu.com/ubuntu noble/multiverse amd64 Packages

```



> **1fallen said:**
> Mine is different:
```
apt policy nvidia-driver-555 nvidia-dkms-555
nvidia-driver-555:
 [COLOR=#FF0000] Installed: 555.52.04-0ubuntu0~gpu24.10.1[/COLOR]
  Candidate: 555.52.04-0ubuntu0~gpu24.10.1
  Version table:
 *** 555.52.04-0ubuntu0~gpu24.10.1 500
        500 https://ppa.launchpadcontent.net/graphics-drivers/ppa/ubuntu oracular/main amd64 Packages
        100 /var/lib/dpkg/status
nvidia-dkms-555:
 [COLOR=#FF0000] Installed: 555.52.04-0ubuntu0~gpu24.10.1[/COLOR]
  Candidate: 555.52.04-0ubuntu0~gpu24.10.1
  Version table:
 *** 555.52.04-0ubuntu0~gpu24.10.1 500
        500 https://ppa.launchpadcontent.net/graphics-drivers/ppa/ubuntu oracular/main amd64 Packages
        100 /var/lib/dpkg/status

```

Mine:

```
apt policy nvidia-driver-555 nvidia-dkms-555
nvidia-driver-555:
  Installed: (none)
  Candidate: 555.52.04-0ubuntu0~gpu24.04.1
  Version table:
     555.52.04-0ubuntu0~gpu24.04.1 500
        500 https://ppa.launchpadcontent.net/graphics-drivers/ppa/ubuntu noble/main amd64 Packages
nvidia-dkms-555:
  Installed: (none)
  Candidate: 555.52.04-0ubuntu0~gpu24.04.1
  Version table:
     555.52.04-0ubuntu0~gpu24.04.1 500
        500 https://ppa.launchpadcontent.net/graphics-drivers/ppa/ubuntu noble/main amd64 Packages

```

So is this all done now?  Just this to do?
```
W: https://ppa.launchpadcontent.net/yannubuntu/boot-repair/ubuntu/dists/noble/InRelease: Signature by key 3C48D16124B50277AF10D27F32B18A1260D8DA0B uses weak algorithm (rsa1024)
N: Missing Signed-By in the sources.list(5) entry for 'https://esm.ubuntu.com/infra/ubuntu'
N: Missing Signed-By in the sources.list(5) entry for 'https://esm.ubuntu.com/infra/ubuntu'
```

---

### Post by #&amp;thj^% on 2024-07-21
Great all the driver issue's look good now. :)

Do you still need help with removing the bad sources?

BTW, ubuntu-drivers will stay greyed out since we by passed it, and will show manually installed. Now if you were to remove and purge that Driver, it would or *should show the options again.

---

### Post by Jonners59 on 2024-07-21
> **1fallen said:**
> Great all the driver issue's look good now. :)

BTW, ubuntu-drivers will stay greyed out since we by passed it, and will show manually installed. Now if you were to remove and purge that Driver, it would or *should show the options again.

Thank you.  That's so good.  And I was wondering, so thank you for that.  As a matter of interest.  What would be the +ve and -ves and what would the impact have been IF I had installed the drive I downloaded from the manufacturer - nvidia.  I don't understand the differences of all these sources.


> **1fallen said:**
> 
Do you still need help with removing the bad sources?

They always say to "never look a gift horse in the mount".  Not calling you a horse, but if I can get that fixed I'd be chuffed.

---

### Post by #&amp;thj^% on 2024-07-21
> **Jonners59 said:**
> Thank you.  That's so good.  And I was wondering, so thank you for that.  As a matter of interest.  What would be the +ve and -ves and what would the impact have been IF I had installed the drive I downloaded from the manufacturer - nvidia.  I don't understand the differences of all these sources.
Well for this thread we speak of 3 different sources, 1st is the factory installed repos (Ubuntu) 2nd is a PPA or third party (you are using that source for the install) 3rd is the binary glob that is written by nVidia (the sh run file) which is fine but not built for Ubuntu per say, and comes if you look in the right place:
> Note that many Linux distributions provide their own packages of the NVIDIA Linux Graphics Driver in the distribution's native package management format. This may interact better with the rest of your distribution's framework, and you may want to use this rather than NVIDIA's official package.

Also note that SuSE users should read the SuSE NVIDIA Installer HOWTO before downloading the driver.



> **Jonners59 said:**
> 
They always say to "never look a gift horse in the mount".  Not calling you a horse, but if I can get that fixed I'd be chuffed.

:)
 ```
cd /etc/apt/sources.list.d/
sudo rm -rf yannubuntu-ubuntu-boot-repair-noble.sources yannubuntu-ubuntu-boot-repair-noble.sources.save ubuntu-esm-infra.list.distUpgrade ubuntu-esm-infra.list.save ubuntu-esm-infra.sources ubuntu-esm-infra.sources.save 
```

---

### Post by Jonners59 on 2024-07-21
> **1fallen said:**
> Well for this thread we speak of 3 different sources, 1st is the factory installed repos (Ubuntu) 2nd is a PPA or third party (you are using that source for the install) 3rd is the binary glob that is written by nVidia (the sh run file) which is fine but not built for Ubuntu per say, and comes if you look in the right place:


:)
 ```
cd /etc/apt/sources.list.d/
sudo rm -rf yannubuntu-ubuntu-boot-repair-noble.sources yannubuntu-ubuntu-boot-repair-noble.sources.save ubuntu-esm-infra.list.distUpgrade ubuntu-esm-infra.list.save ubuntu-esm-infra.sources ubuntu-esm-infra.sources.save 
```

Looks good.  I do need to reboot to make sure, but looks as if that worked - THANK YOU.

```
sudo apt update && sudo apt upgrade -y
Hit:1 http://archive.ubuntu.com/ubuntu noble InRelease
Hit:2 http://archive.ubuntu.com/ubuntu noble-updates InRelease
Hit:3 http://archive.ubuntu.com/ubuntu noble-backports InRelease                 
Hit:4 http://archive.ubuntu.com/ubuntu noble-security InRelease                  
Hit:5 https://ppa.launchpadcontent.net/graphics-drivers/ppa/ubuntu noble InRelease
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
2 packages can be upgraded. Run 'apt list --upgradable' to see them.
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  libboost-log1.74.0 libboost-regex1.74.0
0 to upgrade, 0 to newly install, 0 to remove and 2 not to upgrade.

```

Fingers crossed.

---

### Post by Jonners59 on 2024-07-21
I'm back and all seems good!!!!!

THANK YOU.  You are a star.  When I get back from Italy, after the summer I'll start on the other machine that's been causing me trouble.  Left it for ages.  It's still running 23:10.

---

