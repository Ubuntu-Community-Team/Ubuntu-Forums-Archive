---
title: "USB Modeswitch not working on cold boot with 0bda:1a2b Realtek"
date: 2022-12-11
forum: Hardware
---

### Post by hkphooey on 2022-12-11
I've been doing dist-upgrades for the last few years, but this year when going from 20.04 to 22.04 a bunch of things broke, so I decided to install fresh. I was sideswiped by my USB wifi dongle, which was working fine before, but caused me no end of headaches with the new install. Long story short, it didn't boot up after reinstall and the reason was that the USB wifi dongle appeared in 'storage device' mode. But instead of just moving on the OS sat there and did nothing for 3 minutes, with a black screen, no error messages, causing me to reinstall several times, until once I booted up with the dongle disconnected, and figured out what the problem was. 

Previously adding a line to /usr/lib/udev/rules.d/40-usb_modeswitch.rules had worked fine. 
```
ATTR{idVendor}=="0bda", ATTR{idProduct}=="1a2b", RUN+="/usr/sbin/usb_modeswitch -K -v 0bda -p 1a2b"
```
Once added, my 20.04 Ubuntu would detect the modem, and switch it to product ID 0bda:c811 and would proceed with the boot. Obviously this is the first thing I tried. Obviously this did not work. 

Next searches around the internet suggested adding a file in /etc/usb_modeswitch.d/
```
cat /etc/usb_modeswitch.d/0bda:1a2b
# Dlink adapter
DefaultVendor=0x0bda
DefaultProduct=0x1a2b

TargetVendor=0x0bda
TargetProduct=0xc811

StandardEject=1
```
This also didn't work. Although now it was working on a reboot, but not on a cold boot. 

It seems that during the boot usb modeswitch wasn't firing off quick enough. I then tried forcing it manually with init.d 
```
cat /etc/init.d/10_usbmodeswitch
# Grrr
/usr/sbin/usb_modeswitch -K -v 0bda -p 1a2b
```

Once again, no joy, so my final attempt was to try and manipulate systemd to firing off usb modeswitch, according to other posts around the internet. 
```
cat /usr/lib/systemd/system/usb_modeswitch@.service
[Unit]
Description=USB_ModeSwitch_%i
Documentation=man:usb_modeswitch_dispatcher(1)
# added
DefaultDependencies=no
After=local-fs.target systemd-sysctl.service
Before=network-pre.target shutdown.target
Wants=network-pre.target
Conflicts=shutdown.target

[Service]
Type=oneshot
ExecStart=/usr/sbin/usb_modeswitch_dispatcher --switch-mode %i
# Testing
#ExecStart=/bin/echo "usb_modeswitch.service: device name is %i"
Environment="TMPDIR=/run"
```

Once again no good. So I've exhausted my options at the moment. It seems there are two problems:
[LIST=1]
[*]USB modeswitch is running too late in the boot process to catch the dongle at the correct time. 
[*]Something in the disk mounting/inspection procedure freezes when it sees the disk and doesn't proceed. 
[/LIST]
So now I'm inviting suggestions for anything else I can try. It seems to be related to something which changed between 20.04 and 22.04

Oh, I've also tried 
- turning on logging in /etc/usb_modeswitch.conf which results in zero logs. Maybe that's broken. 
- Setting SetStorageDelay=4 in that same file, as it mentions a possible issue with USB 3. 
- Trying a USB 2 port instead of USB 3.

---

### Post by hkphooey on 2022-12-15
Maybe the key is not with USB modeswitch, but to find out what's happening to stop the boot process when it encounters the USB device which it thinks is storage. 
Anyone have any idea what's going on at that point? Is the OS trying to mount it? Can I tell it not to do that?

---

### Post by hkphooey on 2022-12-17
Have found a lot of these errors in dmesg output at the time when the boot has stalled. 
"reset high-speed USB device number 3 using xhci_hcd" 
In context:

[FONT=Courier New][    1.884052] usb 3-3: new high-speed USB device number 3 using xhci_hcd
[    2.034168] usb 3-3: New USB device found, idVendor=0bda, idProduct=1a2b, bcdDevice= 2.00
[    2.034175] usb 3-3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.034178] usb 3-3: Product: DISK
[    2.034181] usb 3-3: Manufacturer: Realtek
[    2.041052] usb-storage 3-3:1.0: USB Mass Storage device detected
[    2.041291] scsi host9: usb-storage 3-3:1.0
[    2.041413] usbcore: registered new interface driver usb-storage
[    3.046504] scsi 9:0:0:0: CD-ROM            Realtek  Driver Storage   1.00 PQ: 0 ANSI: 0 CCS
[    3.051308] sr 9:0:0:0: [sr0] scsi3-mmc drive: 0x/0x caddy
[    3.051312] cdrom: Uniform CD-ROM driver Revision: 3.20
[    3.053026] sr 9:0:0:0: Attached scsi CD-ROM sr0
[    3.053093] sr 9:0:0:0: Attached scsi generic sg2 type 5
[    3.180113] usb 3-3: reset high-speed USB device number 3 using xhci_hcd
[   33.872148] usb 3-3: reset high-speed USB device number 3 using xhci_hcd
[   64.592179] usb 3-3: reset high-speed USB device number 3 using xhci_hcd[/FONT]

**Manually unplug USB dongle. **

[FONT=Courier New][   65.254357] usb 3-3: USB disconnect, device number 3
[   66.032016] raid6: avx2x4   gen() 22211 MB/s
[   66.100016] raid6: avx2x4   xor()  8108 MB/s
[   66.168016] raid6: avx2x2   gen() 24166 MB/s[/FONT]

---

### Post by hkphooey on 2023-01-29
So, a long time later, after several months of unplugging my USB wifi stick every time I boot, I've finally found the solution. Which of course came out of left field. 

To find it, I turned on the boot messages, by editing  /etc/default/grub and turning on boot messages:
[FONT=Courier New]#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX_DEFAULT=[/FONT]

When I next booted, I found that it was getting stuck with the message "scanning for btrfs filesystems". OK, strange, I didn't have any of those, but it seemed that Linux Mint's timemachine had installed the tools, as that's how it takes snapshots. 

So, I removed them with
[FONT=Courier New]sudo apt-get purge btrfs-progs [/FONT]
and then to apply the change to all kernels, I ran
[FONT=Courier New]sudo update-initramfs -ukall[/FONT]
...and like magic, the next boot completed with no delay. 

So in fact, after chasing around and obsessing with usb_modeswitch, it turns out it wasn't that at all.

---

