---
title: "Udev rules anyone?"
date: 2016-08-15
forum: Hardware
---

### Post by irvine_himself2 on 2016-08-15
I have a bash, (below, which mirrors the display to my Tv. The duplicate version I have in /home/memyself/HouseKeeping/ works without any problems from a panel quick launch icon. 

```
#!/bin/bash

# see https://askubuntu.com/questions/461553/which-command-line-commands-enable-mirror-feature-in-the-screen-display-gui
# also https://askubuntu.com/questions/119843/how-to-force-multiple-monitors-correct-resolutions-for-lightdm

# For refence, an inactive copy of this script is kept in /home/memyself/HouseKeeping/, but this is the one that does the work.
# This script is activated by Udev rule kept in /etc/udev/rules.d/70-MirrorToTv.rules
# Note Udev naming convention for rules is important!
# see https://blog.sleeplessbeastie.eu/2013/01/07/how-to-automatically-set-up-external-monitor/
# see https://hackaday.com/2009/09/18/how-to-write-udev-rules/
# see http://www.reactivated.net/writing_udev_rules.html 

# debug
/bin/echo "$(date) Executing udev monitor clone....." >> /home/memyself/Desktop/MirrorDebug.txt


# Check default screen is eDP1
if xrandr --query | grep "eDP1"; then
  # check HDMI is connected as "HDMI1" or "HDMI-1"
  if xrandr --query | grep "HDMI1"; then
     xrandr --output eDP1 --auto --primary --output HDMI1 --auto --same-as eDP1
   else if xrandr --query | grep "HDMI-1"; then
      xrandr --output eDP1 --auto --primary --output HDMI-1 --auto --same-as eDP1
     else
        xrandr --query
        echo -n "Neither HDMI1 nor HDMI-1 is present, hit return to exit"
        read YesNo
   fi
  fi
 else
    xrandr --query
    echo -n "Main display is not eDP1, hit return to exit"
    read YesNo
fi  
```

Note: I have set the permissions to allow the bash to run as a program.

I would like to have a udev rule that launches the bash automatically when the Tv is switched on and have tried various variations of the following without any success:

```
# Calls /usr/bin/MirrorToTv.sh when HDMI tv is connected

# see https://blog.sleeplessbeastie.eu/2013/01/07/how-to-automatically-set-up-external-monitor/
# see https://hackaday.com/2009/09/18/how-to-write-udev-rules/
# see http://www.reactivated.net/writing_udev_rules.html 

# Note Udev naming convention for rules is important!


KERNEL=="card0", SUBSYSTEM=="drm", ACTION=="change", RUN+="su memyself -c /usr/bin/MirrorToTv.sh"


```

The bash is stored in 

```
/usr/bin/MirrorToTV.sh
```

The udev rule is stored in 

```
/etc/udev/rules.d/70-MirrorToTv.rules
```

Noting the debug pipe and the fact there is no debug output, I am fairly sure the bash is never called. The problem is: Why?

Any advice is very welcome.

Irvine

---

### Post by irvine_himself2 on 2016-08-16
Although I am still unhappily plodding away with this, after a bit more research I can provide some more information.

Running 
```
dpkg-query -L udev | grep rules
```

I get 
```
/lib/udev/rules.d
/lib/udev/rules.d/60-drm.rules
/lib/udev/rules.d/40-vm-hotadd.rules
/lib/udev/rules.d/60-persistent-storage.rules
/lib/udev/rules.d/70-debian-uaccess.rules
/lib/udev/rules.d/60-cdrom_id.rules
/lib/udev/rules.d/73-special-net-names.rules
/lib/udev/rules.d/60-persistent-alsa.rules
/lib/udev/rules.d/78-graphics-card.rules
/lib/udev/rules.d/60-persistent-v4l.rules
/lib/udev/rules.d/80-debian-compat.rules
/lib/udev/rules.d/50-udev-default.rules
/lib/udev/rules.d/70-power-switch.rules
/lib/udev/rules.d/64-btrfs.rules
/lib/udev/rules.d/60-persistent-input.rules
/lib/udev/rules.d/80-drivers.rules
/lib/udev/rules.d/50-firmware.rules
/lib/udev/rules.d/70-mouse.rules
/lib/udev/rules.d/75-probe_mtd.rules
/lib/udev/rules.d/60-block.rules
/lib/udev/rules.d/73-usb-net-by-mac.rules
/lib/udev/rules.d/60-persistent-storage-tape.rules
/lib/udev/rules.d/78-sound-card.rules
/lib/udev/rules.d/80-net-setup-link.rules
/lib/udev/rules.d/75-net-description.rules
/lib/udev/rules.d/61-persistent-storage-android.rules
/lib/udev/rules.d/71-power-switch-proliant.rules
/lib/udev/rules.d/60-evdev.rules
/lib/udev/rules.d/60-serial.rules
/etc/udev/rules.d
memyself@Mine:~$ 
```

As you can see, udev is not seeing any rules in "/etc/udev/rules.d", but the rule is definately present in a directory listing for that folder:
```
memyself@Mine:/etc/udev/rules.d$ dir
70-MirrorToTv.rules
memyself@Mine:/etc/udev/rules.d$ 

```

Evidently, for some unknown reason, my udev rule is not being detected. If anybody has any Ideas about why or how to troubleshoot the problem, I would desperately like to hear from you.

Thanks
Irvine

---

### Post by ian-weisser on 2016-08-16
Are you really sure that rule (card0) matches your hardware?
Have you looked at dmesg output to see what the kernel reports when you plug in the TV?

---

### Post by irvine_himself2 on 2016-08-16
> **ian-weisser said:**
> Are you really sure that rule (card0) matches your hardware?
Have you looked at dmesg output to see what the kernel reports when you plug in the TV?

Thanks for the reply, here is output from " udevadm monitor" when I switch on the Tv.
```
memyself@Mine:~$ udevadm monitor
monitor will print the received events for:
UDEV - the event which udev sends out after rule processing
KERNEL - the kernel uevent

KERNEL[17686.284231] change   /devices/pci0000:00/0000:00:02.0/drm/card0 (drm)
UDEV  [17686.287016] change   /devices/pci0000:00/0000:00:02.0/drm/card0 (drm)
KERNEL[17686.601179] change   /devices/pci0000:00/0000:00:02.0/drm/card0 (drm)
UDEV  [17686.609692] change   /devices/pci0000:00/0000:00:02.0/drm/card0 (drm)
KERNEL[17689.564379] change   /devices/pci0000:00/0000:00:02.0/drm/card0 (drm)
UDEV  [17689.570223] change   /devices/pci0000:00/0000:00:02.0/drm/card0 (drm)
KERNEL[17697.677932] change   /devices/pci0000:00/0000:00:02.0/drm/card0 (drm)
UDEV  [17697.684603] change   /devices/pci0000:00/0000:00:02.0/drm/card0 (drm)

```

This is in fact almost identical to the example output in the [main tutorial]("https://blog.sleeplessbeastie.eu/2013/01/07/how-to-automatically-set-up-external-monitor/") I am using. Ie, the one I copied the rule from. (Note, I have tried copying similar rules from other sources which, (although differently worded,) achieve the same thing. Some do not mention the kernel, others do not define a user, None of them seem to work.)

As far as the dmesg output, there is nothing when I switch on the Tv

Before switching on Tv:
```

.............
[ 8798.584108] perf interrupt took too long (2504 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
[10947.647889] pcieport 0000:00:1c.4: AER: Corrected error received: id=00e4
[10947.647898] pcieport 0000:00:1c.4: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e4(Receiver ID)
[10947.647901] pcieport 0000:00:1c.4:   device [8086:9d14] error status/mask=00000001/00002000
[10947.647902] pcieport 0000:00:1c.4:    [ 0] Receiver Error        
[14910.036173] pcieport 0000:00:1c.4: AER: Corrected error received: id=00e4
[14910.036183] pcieport 0000:00:1c.4: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e4(Receiver ID)
[14910.036186] pcieport 0000:00:1c.4:   device [8086:9d14] error status/mask=00000001/00002000
[14910.036188] pcieport 0000:00:1c.4:    [ 0] Receiver Error        
[15447.580990] pcieport 0000:00:1c.4: AER: Corrected error received: id=00e4
[15447.580998] pcieport 0000:00:1c.4: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e4(Receiver ID)
[15447.581001] pcieport 0000:00:1c.4:   device [8086:9d14] error status/mask=00000001/00002000
[15447.581003] pcieport 0000:00:1c.4:    [ 0] Receiver Error         (First)
[16071.154004] [UFW BLOCK] IN=wlp2s0 OUT= MAC=94:65:9c:f6:20:5c:1c:67:58:21:00:94:08:00 SRC=173.194.122.247 DST=192.168.0.100 LEN=40 TOS=0x08 PREC=0x20 TTL=45 ID=20169 PROTO=TCP SPT=443 DPT=43556 WINDOW=0 RES=0x00 RST URGP=0 
[16071.155405] [UFW BLOCK] IN=wlp2s0 OUT= MAC=94:65:9c:f6:20:5c:1c:67:58:21:00:94:08:00 SRC=173.194.122.247 DST=192.168.0.100 LEN=40 TOS=0x08 PREC=0x20 TTL=45 ID=20170 PROTO=TCP SPT=443 DPT=43556 WINDOW=0 RES=0x00 RST URGP=0 
memyself@Mine:/etc/udev/rules.d$ 
```

After switching on the Tv:
```

.............
[ 8798.584108] perf interrupt took too long (2504 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
[10947.647889] pcieport 0000:00:1c.4: AER: Corrected error received: id=00e4
[10947.647898] pcieport 0000:00:1c.4: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e4(Receiver ID)
[10947.647901] pcieport 0000:00:1c.4:   device [8086:9d14] error status/mask=00000001/00002000
[10947.647902] pcieport 0000:00:1c.4:    [ 0] Receiver Error        
[14910.036173] pcieport 0000:00:1c.4: AER: Corrected error received: id=00e4
[14910.036183] pcieport 0000:00:1c.4: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e4(Receiver ID)
[14910.036186] pcieport 0000:00:1c.4:   device [8086:9d14] error status/mask=00000001/00002000
[14910.036188] pcieport 0000:00:1c.4:    [ 0] Receiver Error        
[15447.580990] pcieport 0000:00:1c.4: AER: Corrected error received: id=00e4
[15447.580998] pcieport 0000:00:1c.4: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e4(Receiver ID)
[15447.581001] pcieport 0000:00:1c.4:   device [8086:9d14] error status/mask=00000001/00002000
[15447.581003] pcieport 0000:00:1c.4:    [ 0] Receiver Error         (First)
[16071.154004] [UFW BLOCK] IN=wlp2s0 OUT= MAC=94:65:9c:f6:20:5c:1c:67:58:21:00:94:08:00 SRC=173.194.122.247 DST=192.168.0.100 LEN=40 TOS=0x08 PREC=0x20 TTL=45 ID=20169 PROTO=TCP SPT=443 DPT=43556 WINDOW=0 RES=0x00 RST URGP=0 
[16071.155405] [UFW BLOCK] IN=wlp2s0 OUT= MAC=94:65:9c:f6:20:5c:1c:67:58:21:00:94:08:00 SRC=173.194.122.247 DST=192.168.0.100 LEN=40 TOS=0x08 PREC=0x20 TTL=45 ID=20170 PROTO=TCP SPT=443 DPT=43556 WINDOW=0 RES=0x00 RST URGP=0 
memyself@Mine:/etc/udev/rules.d$ 
```

The more I look at this, the more I am convinced it is not detecting the rule.

Thanks again for replying
Irvine

---

### Post by steeldriver on 2016-08-16
dpkg -L udev only tells you about files owned by / installed by the udev **package **- it doesn't tell you anything about what rules udev is loading at runtime

---

### Post by irvine_himself2 on 2016-08-17
> **steeldriver said:**
> dpkg -L udev only tells you about files owned by / installed by the udev **package **- it doesn't tell you anything about what rules udev is loading at runtime

Thanks for pointing that out, I knew it seemed too easy. However, pointing to the debug pipe on line 14 of the bash, it still seems that the bash is not being called by the Udev rule. Does anyone know of a way to confirm what rules are being loaded, and more importantly, what, (if any,) error messages are being generated by specific Udev rules?

Thanks
Irvine

---

### Post by irvine_himself2 on 2016-08-17
Okay maybe I have it right this time. Googling around for a while, I found [this post]("https://unix.stackexchange.com/questions/182309/list-all-udev-rules-e-g-for-a-device") on Stack Exchange. After some experimentation, I came up with this basic test.
```
udevadm test $(udevadm info -q path -n /dev/dri/card0)
```

Which reulted in
```
memyself@Mine:~$ udevadm test $(udevadm info -q path -n /dev/dri/card0)
calling: test
version 229
This program is for debugging only, it does not run any program
specified by a RUN key. It may show incorrect results, because
some values may be different, or not available at a simulation run.

=== trie on-disk ===
tool version:          229
file size:         7043518 bytes
header size             80 bytes
strings            1757550 bytes
nodes              5285888 bytes
Load module index
timestamp of '/etc/systemd/network' changed
timestamp of '/lib/systemd/network' changed
Parsed configuration file /lib/systemd/network/99-default.link
Created link configuration context.
timestamp of '/etc/udev/rules.d' changed
timestamp of '/lib/udev/rules.d' changed
Reading rules file: /lib/udev/rules.d/20-lightworks.rules
.......
Reading rules file: /lib/udev/rules.d/69-libmtp.rules
Reading rules file: /lib/udev/rules.d/69-wacom.rules
Reading rules file: /lib/udev/rules.d/69-xorg-vmmouse.rules
**Reading rules file: /etc/udev/rules.d/70-MirrorToTv.rules**
Reading rules file: /lib/udev/rules.d/70-debian-uaccess.rules
Reading rules file: /lib/udev/rules.d/70-mouse.rules
Reading rules file: /lib/udev/rules.d/70-power-switch.rules
.....
Reading rules file: /lib/udev/rules.d/98-osscuse.rules
Reading rules file: /lib/udev/rules.d/99-systemd.rules
rules contain 393216 bytes tokens (32768 * 12 bytes), 35610 bytes strings
24446 strings (205596 bytes), 20877 de-duplicated (173556 bytes), 3570 trie nodes used
value '[dmi/id]sys_vendor' is 'TOSHIBA'
value '[dmi/id]sys_vendor' is 'TOSHIBA'
GROUP 44 /lib/udev/rules.d/50-udev-default.rules:35
IMPORT builtin 'path_id' /lib/udev/rules.d/60-drm.rules:3
RUN '/sbin/u-d-c-print-pci-ids' /lib/udev/rules.d/71-u-d-c-gpu-detection.rules:4
RUN 'uaccess' /lib/udev/rules.d/73-seat-late.rules:15
PROGRAM '/bin/readlink /etc/udev/rules.d/80-net-setup-link.rules' /lib/udev/rules.d/73-usb-net-by-mac.rules:6
starting '/bin/readlink /etc/udev/rules.d/80-net-setup-link.rules'
Process '/bin/readlink /etc/udev/rules.d/80-net-setup-link.rules' failed with exit code 1.
handling device node '/dev/dri/card0', devnum=c226:0, mode=0660, uid=0, gid=44
preserve permissions /dev/dri/card0, 020660, uid=0, gid=44
preserve already existing symlink '/dev/char/226:0' to '../dri/card0'
ACTION=add
DEVNAME=/dev/dri/card0
DEVPATH=/devices/pci0000:00/0000:00:02.0/drm/card0
DEVTYPE=drm_minor
ID_FOR_SEAT=drm-pci-0000_00_02_0
ID_PATH=pci-0000:00:02.0
ID_PATH_TAG=pci-0000_00_02_0
MAJOR=226
MINOR=0
SUBSYSTEM=drm
TAGS=:uaccess:seat:master-of-seat:
USEC_INITIALIZED=6767539
run: '/sbin/u-d-c-print-pci-ids'
run: 'uaccess'
Unload module index
Unloaded link configuration context.
memyself@Mine:~$ 
```

So, as you can see from the highlighted section, the my 70-MirrorToTv.rules is being loaded. The big question now is: Why is it not calling my bash?

Interestingly, when I try the more complex testing bash from the same source, (which uses regex, a subject with which I have only a very limited, passing familiarity,) my 70-MirrorToTv.rules doesn’t show up.
```
memyself@Mine:~$ /home/memyself/Desktop/test.sh
110:/lib/udev/rules.d/55-Argyll.rules                  ENV{COLORD_SENSOR_KIND}=="*?", ENV{ID_MODEL}=="", IMPORT{program}="usb_id --export %p"
035:/lib/udev/rules.d/50-udev-default.rules            SUBSYSTEM=="drm", GROUP="video"
003:/lib/udev/rules.d/60-drm.rules                     ACTION!="remove", SUBSYSTEM=="drm", SUBSYSTEMS=="pci|usb|platform", IMPORT{builtin}="path_id"
004:/lib/udev/rules.d/71-u-d-c-gpu-detection.rules     ACTION=="add", SUBSYSTEM=="drm", DEVPATH=="*/drm/card*", RUN+="/sbin/u-d-c-print-pci-ids"
015:/lib/udev/rules.d/73-seat-late.rules               TAG=="uaccess", ENV{MAJOR}!="", RUN{builtin}+="uaccess"
006:/lib/udev/rules.d/73-usb-net-by-mac.rules          PROGRAM="/bin/readlink /etc/udev/rules.d/80-net-setup-link.rules", RESULT=="/dev/null", GOTO="usb_net_by_mac_end"
memyself@Mine:~$ 
```

To get it to work, I had to customise the test bash as follows
```
udevadm test $(udevadm info -q path -n /dev/dri/card0) 2>&1 | \
sed -n 's/.* \(\/[^ ]*\)\.rules:\([0-9]\+\)/\1.rules \2/p' | \
while read -r f n; do printf "%03d:%-50s " $n "$f"; sed -n ${n}p $f; done
```

Noting that in both cases, to get the testing commands to work I had to use a path as a device name, Is this significant, and should I be looking at modifying my rule in a similar manner?

Thanks for your input
Irvine

---

### Post by irvine_himself2 on 2016-08-17
Okay, I have managed to tease out some more information, though I am not sure of the significance.

I found a script [here]("http://www.weather-watch.com/smf/index.php?topic=39257.0"), which, given a "clue", finds the full device paths for all devices hinted at by said "clue":
```
#see http://www.weather-watch.com/smf/index.php?topic=39257.0
CLUE=card0
for DEVICE in $(find /sys ! -type l -iname "*${CLUE}*"); do ls -dl $DEVICE; udevadm info -a -p $DEVICE; done
```

Copy pasting to my favourite text editor, I used "find 'HDMI'" to narrow down the ouput to the following:
```
......
......
drwxr-xr-x 3 root root 0 Aug 17 15:14 /sys/devices/pci0000:00/0000:00:02.0/drm/card0/card0-HDMI-A-1

Udevadm info starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/pci0000:00/0000:00:02.0/drm/card0/card0-HDMI-A-1':
    KERNEL=="card0-HDMI-A-1"
    SUBSYSTEM=="drm"
    DRIVER==""
    ATTR{dpms}=="Off"
    ATTR{edid}==""
    ATTR{enabled}=="disabled"
    ATTR{status}=="connected"

  looking at parent device '/devices/pci0000:00/0000:00:02.0/drm/card0':
    KERNELS=="card0"
    SUBSYSTEMS=="drm"
    DRIVERS==""
    ATTRS{error}=="no error state collected"
    ATTRS{gt_RP0_freq_mhz}=="1050"
    ATTRS{gt_RP1_freq_mhz}=="300"
    ATTRS{gt_RPn_freq_mhz}=="300"
    ATTRS{gt_act_freq_mhz}=="1033"
    ATTRS{gt_cur_freq_mhz}=="1033"
    ATTRS{gt_max_freq_mhz}=="1050"
    ATTRS{gt_min_freq_mhz}=="300"

  looking at parent device '/devices/pci0000:00/0000:00:02.0':
    KERNELS=="0000:00:02.0"
    SUBSYSTEMS=="pci"
    DRIVERS=="i915_bpo"
    ATTRS{boot_vga}=="1"
    ATTRS{broken_parity_status}=="0"
    ATTRS{class}=="0x030000"
    ATTRS{consistent_dma_mask_bits}=="39"
    ATTRS{d3cold_allowed}=="1"
    ATTRS{device}=="0x1916"
    ATTRS{dma_mask_bits}=="39"
    ATTRS{driver_override}=="(null)"
    ATTRS{enable}=="1"
    ATTRS{irq}=="130"
    ATTRS{local_cpulist}=="0-3"
    ATTRS{local_cpus}=="0f"
    ATTRS{msi_bus}=="1"
    ATTRS{numa_node}=="-1"
    ATTRS{subsystem_device}=="0xf840"
    ATTRS{subsystem_vendor}=="0x1179"
    ATTRS{vendor}=="0x8086"

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""

drwxr-xr-x 5 root root 0 Aug 17 15:14 /sys/devices/pci0000:00/0000:00:02.0/drm/card0/card0-eDP-1
......
......
```

Unfortunately, I am having as little luck using "card0-HDMI-A-1" as the kernel attribute, as I have with everything else I have tried.

Any comments or guidance would be more than welcome

Irvine

---

### Post by irvine_himself2 on 2016-08-18
"Possibly a major breakthrough. 

I was exploring "/Var/log/syslog" and et-voila, I found a few references like the following:
```
--- -    2016-08-18 18:09:57.292356320 +0100
+++ /var/log/syslog    2016-08-18 18:09:52.867803767 +0100
@@ -232,3 +232,11 @@
 Aug 18 18:09:04 Mine systemd[1]: Stopped udev Kernel Device Manager.
 Aug 18 18:09:04 Mine systemd[1]: Starting udev Kernel Device Manager...
 Aug 18 18:09:04 Mine systemd[1]: Started udev Kernel Device Manager.
+Aug 18 18:09:41 Mine systemd-udevd[24250]: failed to execute '/lib/udev/su' 'su memyself -c /usr/bin/MirrorToTv.sh': No such file or directory
+Aug 18 18:09:41 Mine systemd-udevd[24248]: Process 'su memyself -c /usr/bin/MirrorToTv.sh' failed with exit code 2.
+Aug 18 18:09:41 Mine systemd-udevd[24253]: failed to execute '/lib/udev/su' 'su memyself -c /usr/bin/MirrorToTv.sh': No such file or directory
+Aug 18 18:09:41 Mine systemd-udevd[24251]: Process 'su memyself -c /usr/bin/MirrorToTv.sh' failed with exit code 2.
+Aug 18 18:09:44 Mine systemd-udevd[24263]: failed to execute '/lib/udev/su' 'su memyself -c /usr/bin/MirrorToTv.sh': No such file or directory
+Aug 18 18:09:44 Mine systemd-udevd[24261]: Process 'su memyself -c /usr/bin/MirrorToTv.sh' failed with exit code 2.
+Aug 18 18:09:52 Mine systemd-udevd[24268]: failed to execute '/lib/udev/su' 'su memyself -c /usr/bin/MirrorToTv.sh': No such file or directory
+Aug 18 18:09:52 Mine systemd-udevd[24266]: Process 'su memyself -c /usr/bin/MirrorToTv.sh' failed with exit code 2.
```

The file is definitely present:
```

memyself@Mine:/usr/bin$ dir /usr/bin  >> /home/memyself/Desktop/DirUsrBin.txt
......
......
mf2pt1                      xzegrep
mf-nowin                  xzfgrep
mformat                      xzgrep
mfplain                      xzless
mft                      xzmore
mgrtopbm                  y4mcolorbars
mid3cp                      y4mdenoise
mid3iconv                  y4mscaler
mid3v2                      y4mtopnm
mimeopen                  y4mtoppm
mimetype                  y4munsharp
min12xxw                  ybmtopbm
minfo                      yelp
miniterm.py                  yes
**MirrorToTv.sh**                  yoshimi
mixer                      yuv2lav
mkfifo                      yuv4mpeg
mkfontdir                  yuvcorrect
mkfontscale                  yuvcorrect_tune
mkindex                      yuvdeinterlace
mkisofs                      yuvdenoise
mkjobtexmf                  yuvfps
mkmanifest                  yuvinactive
mk_modmap                  yuvkineco
mkocp                      yuvmedianfilter
mkofm                      yuvplay
mkpic                      yuvscaler
mksquashfs                  yuvsplittoppm
......
......
```

The permissipns are:
```
memyself@Mine:/usr/bin$ ls -l MirrorToTv.sh
-rwxr-xr-x 1 root root 1517 Aug 18 17:36 MirrorToTv.sh
```

Does anybody have any ideas why udev is not seeing the file?

By the way for anybody trying to follow this, should note that trying to use "card0-HDMI-A-1" as a kernel tag failed to produce a syslog error message, so "card0" is the correct device name.

Finally, frustratingly, or amusingly, (take your pick), this thread is now the top ranked Google search result:confused:  see  "[writing udev HDMI rules explained]("https://www.google.co.uk/search?q=writing+udev+HDMI+rules+explained&btnG=Search&safe=off&client=ubuntu&hs=1Nw&channel=fs")"

Any help, comments or advice is welcome

Irvine

---

### Post by steeldriver on 2016-08-18
The  '/lib/udev/su' part is suspicious - have you tried giving the absolute path to su?

```

 . . . RUN+="/bin/su memyself -c /usr/bin/MirrorToTv.sh"

```

---

### Post by os2 on 2016-08-18
You know you have to give sudo the appropriate authorisation to the screen user (ie, sudo) to allow udev to execute the script (as root) on the executing terminal.

```

#!/bin/bash

export DISPLAY=$(echo $DISPLAY | cut -c -2)
user=$(who | grep :0 | awk '{print $1}' | tail -n1)
export XAUTHORITY=/home/$user/.Xauthority

cmd="sudo DISPLAY=:0.0 -u $user sh"


```

---

### Post by irvine_himself2 on 2016-08-18
Thanks for your input, 

**Steeldriver**
I also had suspicions about '/lib/udev/su' and had tried following the advice [here]("https://superuser.com/questions/753806/systemd-udevd381-failed-to-execute-lib-udev-socket-org-fre-edesktop-hal-u") about purging "hal", which had no visible effect. After re-reading your post, (I am half asleep at the moment,having skipped my morning coffee, ciggy's and New York Times to experiment,) anyway, I modified the rule as you suggested. Big improvement:
```
 Aug 19 02:16:42 Mine systemd[1]: Stopped udev Kernel Device Manager.
 Aug 19 02:16:42 Mine systemd[1]: Starting udev Kernel Device Manager...
 Aug 19 02:16:42 Mine systemd[1]: Started udev Kernel Device Manager.
+Aug 19 02:17:01 Mine CRON[6072]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
+Aug 19 02:17:06 Mine systemd[1]: Started Session c10 of user memyself.
+Aug 19 02:17:06 Mine systemd-udevd[6074]: Process '/bin/su memyself -c /usr/bin/MirrorToTv.sh' failed with exit code 1.
+Aug 19 02:17:06 Mine systemd[1]: Started Session c11 of user memyself.
+Aug 19 02:17:06 Mine systemd-udevd[6088]: Process '/bin/su memyself -c /usr/bin/MirrorToTv.sh' failed with exit code 1.
+Aug 19 02:17:09 Mine systemd[1]: Started Session c12 of user memyself.
+Aug 19 02:17:09 Mine systemd-udevd[6104]: Process '/bin/su memyself -c /usr/bin/MirrorToTv.sh' failed with exit code 1.
```

Also, I am now getting output from my debug pipe, which is a first. So I think I am possibly reaching for the final sprint here, (touch wood.)

**Os2**
Thanks for that little snippet, One of the alternative rules I am playing with is 
```
# see https://bbs.archlinux.org/viewtopic.php?id=170294
KERNEL=="card0", SUBSYSTEM=="drm", ENV{DISPLAY}=":0", ENV{XAUTHORITY}="/home/memyself/.Xauthority", RUN+="/usr/bin/MirrorToTv.sh"
```

Which calls export XAUTHORITY in the bash with:
```
export DISPLAY=:0
export XAUTHORITY=/home/memyself/.Xauthority
```

Since it didn't seem fatal, (with the intention of sorting it out once I got to this stage,) I had been leaving the above in the bash regardless of which particular flavour of rule I was experimenting with. Your variations are both  welcome and illuminating.

My next step is coffee, lots and lots of coffee, several cigarettes, and a casual browse of the mornings papers. Once that mission is completed, I will get into the fine details of exactly why the bash failed and what permissions are needed. I will of course keep you all updated.

Thanks again
Irvine

---

### Post by irvine_himself2 on 2016-08-19
Okay, weird things are happening. 

Firstly, I am not quite sure what it was I did to get the syslog output above, (I was trying out various udevadm commands at the time,) but I have now lost it. On the other hand, while trying to figure out how I did it, I found some thing even better!
```
# see https://www.freedesktop.org/software/systemd/man/udevadm.html for other priority options
sudo udevadm control --log-priority=debug
```

When you combine the debug log-priority for udevadm with the "set -x" debug option for bash scripts, you can get some very detailed information about what is happening. Here is a full listing of the changes to syslog when I switch on my Tv.
```
--- -    2016-08-19 17:33:04.342899074 +0100
+++ /var/log/syslog    2016-08-19 17:32:56.519834875 +0100
@@ -9641,3 +9641,149 @@
 Aug 19 17:32:05 Mine systemd-udevd[7130]: Unload module index
 Aug 19 17:32:05 Mine systemd-udevd[7130]: Unloaded link configuration context.
 Aug 19 17:32:05 Mine systemd-udevd[6401]: worker [7130] exited
+Aug 19 17:32:45 Mine systemd-udevd[6401]: seq 3510 queued, 'change' 'drm'
+Aug 19 17:32:45 Mine systemd-udevd[6401]: Validate module index
+Aug 19 17:32:45 Mine systemd-udevd[6401]: Check if link configuration needs reloading.
+Aug 19 17:32:45 Mine systemd-udevd[6401]: seq 3510 forked new worker [7173]
+Aug 19 17:32:45 Mine systemd-udevd[7173]: seq 3510 running
+Aug 19 17:32:45 Mine systemd-udevd[7173]: value '[dmi/id]sys_vendor' is 'TOSHIBA'
+Aug 19 17:32:45 Mine systemd-udevd[7173]: value '[dmi/id]sys_vendor' is 'TOSHIBA'
+Aug 19 17:32:45 Mine systemd-udevd[7173]: IMPORT builtin 'path_id' /lib/udev/rules.d/60-drm.rules:3
+Aug 19 17:32:45 Mine systemd-udevd[7173]: **RUN 'uaccess' /lib/udev/rules.d/73-seat-late.rules:15**
+Aug 19 17:32:45 Mine systemd-udevd[7173]: PROGRAM '/bin/readlink /etc/udev/rules.d/80-net-setup-link.rules' /lib/udev/rules.d/73-usb-net-by-mac.rules:6
+Aug 19 17:32:45 Mine systemd-udevd[7174]: starting '/bin/readlink /etc/udev/rules.d/80-net-setup-link.rules'
+Aug 19 17:32:45 Mine systemd-udevd[7173]: Process '/bin/readlink /etc/udev/rules.d/80-net-setup-link.rules' failed with exit code 1.
+Aug 19 17:32:45 Mine systemd-udevd[7173]:** RUN '/bin/su memyself -c /usr/bin/MirrorToTv.sh' /etc/udev/rules.d/90-MirrorToTv.rules:10**
+Aug 19 17:32:45 Mine systemd-udevd[7173]: handling device node '/dev/dri/card0', devnum=c226:0, mode=0600, uid=0, gid=0
+Aug 19 17:32:45 Mine systemd-udevd[7173]: preserve already existing symlink '/dev/char/226:0' to '../dri/card0'
+Aug 19 17:32:45 Mine systemd-udevd[7173]: created db file '/run/udev/data/c226:0' for '/devices/pci0000:00/0000:00:02.0/drm/card0'
+Aug 19 17:32:45 Mine systemd-udevd[7175]: starting '/bin/su memyself -c /usr/bin/MirrorToTv.sh'
+Aug 19 17:32:45 Mine systemd[1]: Started Session c74 of user memyself.
+Aug 19 17:32:45 Mine systemd-udevd[7173]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ export DISPLAY=:0'
+Aug 19 17:32:45 Mine systemd-udevd[7173]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ DISPLAY=:0'
+Aug 19 17:32:45 Mine systemd-udevd[7173]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ export XAUTHORITY=/home/memyself/.Xauthority'
+Aug 19 17:32:45 Mine systemd-udevd[7173]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ XAUTHORITY=/home/memyself/.Xauthority'
+Aug 19 17:32:45 Mine systemd-udevd[7173]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ xrandr --query'
+Aug 19 17:32:45 Mine systemd-udevd[7173]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ grep eDP1'
+Aug 19 17:32:45 Mine systemd-udevd[7173]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(out) 'eDP1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 345mm x 194mm'
+Aug 19 17:32:45 Mine systemd-udevd[7173]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ grep HDMI1'
+Aug 19 17:32:45 Mine systemd-udevd[7173]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ xrandr --query'
+Aug 19 17:32:45 Mine systemd-udevd[7173]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(out) 'HDMI1 **[COLOR=#ff0000]disconnected[/COLOR]** (normal left inverted right x axis y axis)'
+Aug 19 17:32:45 Mine systemd-udevd[7173]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ xrandr --output eDP1 --auto --primary --output HDMI1 --auto --same-as eDP1'
+Aug 19 17:32:45 Mine systemd-udevd[7173]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ set +x'
+Aug 19 17:32:45 Mine systemd-udevd[7173]: Process '/bin/su memyself -c /usr/bin/MirrorToTv.sh' [COLOR=#ff0000]succeeded[/COLOR].
+Aug 19 17:32:45 Mine systemd-udevd[7173]:[COLOR=#ff0000] passed device to netlink monitor 0x55f1a3e6f3f0[/COLOR]
+Aug 19 17:32:45 Mine systemd-udevd[7173]: seq 3510 processed
+Aug 19 17:32:45 Mine systemd-udevd[6401]: cleanup idle workers
+Aug 19 17:32:45 Mine systemd-udevd[7173]: Unload module index
+Aug 19 17:32:45 Mine systemd-udevd[7173]: Unloaded link configuration context.
+Aug 19 17:32:45 Mine systemd-udevd[6401]: worker [7173] exited
+Aug 19 17:32:45 Mine systemd-udevd[6401]: seq 3511 queued, 'change' 'drm'
+Aug 19 17:32:45 Mine systemd-udevd[6401]: seq 3511 forked new worker [7188]
+Aug 19 17:32:45 Mine systemd-udevd[7188]: seq 3511 running
+Aug 19 17:32:45 Mine systemd-udevd[7188]: value '[dmi/id]sys_vendor' is 'TOSHIBA'
+Aug 19 17:32:45 Mine systemd-udevd[7188]: value '[dmi/id]sys_vendor' is 'TOSHIBA'
+Aug 19 17:32:45 Mine systemd-udevd[7188]: IMPORT builtin 'path_id' /lib/udev/rules.d/60-drm.rules:3
+Aug 19 17:32:45 Mine systemd-udevd[7188]: **RUN 'uaccess' /lib/udev/rules.d/73-seat-late.rules:15**
+Aug 19 17:32:45 Mine systemd-udevd[7188]: PROGRAM '/bin/readlink /etc/udev/rules.d/80-net-setup-link.rules' /lib/udev/rules.d/73-usb-net-by-mac.rules:6
+Aug 19 17:32:45 Mine systemd-udevd[7189]: starting '/bin/readlink /etc/udev/rules.d/80-net-setup-link.rules'
+Aug 19 17:32:45 Mine systemd-udevd[7188]: Process '/bin/readlink /etc/udev/rules.d/80-net-setup-link.rules' failed with exit code 1.
+Aug 19 17:32:45 Mine systemd-udevd[7188]: **RUN '/bin/su memyself -c /usr/bin/MirrorToTv.sh' /etc/udev/rules.d/90-MirrorToTv.rules:10**
+Aug 19 17:32:45 Mine systemd-udevd[7188]: handling device node '/dev/dri/card0', devnum=c226:0, mode=0600, uid=0, gid=0
+Aug 19 17:32:45 Mine systemd-udevd[7188]: preserve already existing symlink '/dev/char/226:0' to '../dri/card0'
+Aug 19 17:32:45 Mine systemd-udevd[7188]: created db file '/run/udev/data/c226:0' for '/devices/pci0000:00/0000:00:02.0/drm/card0'
+Aug 19 17:32:45 Mine systemd-udevd[7190]: starting '/bin/su memyself -c /usr/bin/MirrorToTv.sh'
+Aug 19 17:32:45 Mine systemd[1]: Started Session c75 of user memyself.
+Aug 19 17:32:45 Mine systemd-udevd[7188]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ export DISPLAY=:0'
+Aug 19 17:32:45 Mine systemd-udevd[7188]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ DISPLAY=:0'
+Aug 19 17:32:45 Mine systemd-udevd[7188]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ export XAUTHORITY=/home/memyself/.Xauthority'
+Aug 19 17:32:45 Mine systemd-udevd[7188]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ XAUTHORITY=/home/memyself/.Xauthority'
+Aug 19 17:32:45 Mine systemd-udevd[7188]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ xrandr --query'
+Aug 19 17:32:45 Mine systemd-udevd[7188]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ grep eDP1'
+Aug 19 17:32:45 Mine systemd-udevd[7188]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(out) 'eDP1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 345mm x 194mm'
+Aug 19 17:32:45 Mine systemd-udevd[7188]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ xrandr --query'
+Aug 19 17:32:45 Mine systemd-udevd[7188]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ grep HDMI1'
+Aug 19 17:32:45 Mine systemd-udevd[7188]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(out) 'HDMI1 **[COLOR=#ff0000]disconnected[/COLOR]** (normal left inverted right x axis y axis)'
+Aug 19 17:32:45 Mine systemd-udevd[7188]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ xrandr --output eDP1 --auto --primary --output HDMI1 --auto --same-as eDP1'
+Aug 19 17:32:45 Mine systemd-udevd[7188]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ set +x'
+Aug 19 17:32:45 Mine systemd-udevd[7188]: Process '/bin/su memyself -c /usr/bin/MirrorToTv.sh'[COLOR=#ff0000] succeeded[/COLOR].
+Aug 19 17:32:45 Mine systemd-udevd[7188]: [COLOR=#ff0000]passed device to netlink monitor 0x55f1a3e6f3f0[/COLOR]
+Aug 19 17:32:45 Mine systemd-udevd[7188]: seq 3511 processed
+Aug 19 17:32:45 Mine systemd-udevd[6401]: cleanup idle workers
+Aug 19 17:32:45 Mine systemd-udevd[7188]: Unload module index
+Aug 19 17:32:45 Mine systemd-udevd[7188]: Unloaded link configuration context.
+Aug 19 17:32:45 Mine systemd-udevd[6401]: worker [7188] exited
+Aug 19 17:32:48 Mine systemd-udevd[6401]: seq 3512 queued, 'change' 'drm'
+Aug 19 17:32:48 Mine systemd-udevd[6401]: Validate module index
+Aug 19 17:32:48 Mine systemd-udevd[6401]: Check if link configuration needs reloading.
+Aug 19 17:32:48 Mine systemd-udevd[6401]: seq 3512 forked new worker [7206]
+Aug 19 17:32:48 Mine systemd-udevd[7206]: seq 3512 running
+Aug 19 17:32:48 Mine systemd-udevd[7206]: value '[dmi/id]sys_vendor' is 'TOSHIBA'
+Aug 19 17:32:48 Mine systemd-udevd[7206]: value '[dmi/id]sys_vendor' is 'TOSHIBA'
+Aug 19 17:32:48 Mine systemd-udevd[7206]: IMPORT builtin 'path_id' /lib/udev/rules.d/60-drm.rules:3
+Aug 19 17:32:48 Mine systemd-udevd[7206]: **RUN 'uaccess' /lib/udev/rules.d/73-seat-late.rules:15**
+Aug 19 17:32:48 Mine systemd-udevd[7206]: PROGRAM '/bin/readlink /etc/udev/rules.d/80-net-setup-link.rules' /lib/udev/rules.d/73-usb-net-by-mac.rules:6
+Aug 19 17:32:48 Mine systemd-udevd[7207]: starting '/bin/readlink /etc/udev/rules.d/80-net-setup-link.rules'
+Aug 19 17:32:48 Mine systemd-udevd[7206]: Process '/bin/readlink /etc/udev/rules.d/80-net-setup-link.rules' failed with exit code 1.
+Aug 19 17:32:48 Mine systemd-udevd[7206]: **RUN '/bin/su memyself -c /usr/bin/MirrorToTv.sh' /etc/udev/rules.d/90-MirrorToTv.rules:10**
+Aug 19 17:32:48 Mine systemd-udevd[7206]: handling device node '/dev/dri/card0', devnum=c226:0, mode=0600, uid=0, gid=0
+Aug 19 17:32:48 Mine systemd-udevd[7206]: preserve already existing symlink '/dev/char/226:0' to '../dri/card0'
+Aug 19 17:32:48 Mine systemd-udevd[7206]: created db file '/run/udev/data/c226:0' for '/devices/pci0000:00/0000:00:02.0/drm/card0'
+Aug 19 17:32:48 Mine systemd-udevd[7208]: starting '/bin/su memyself -c /usr/bin/MirrorToTv.sh'
+Aug 19 17:32:48 Mine systemd[1]: Started Session c76 of user memyself.
+Aug 19 17:32:48 Mine systemd-udevd[7206]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ export DISPLAY=:0'
+Aug 19 17:32:48 Mine systemd-udevd[7206]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ DISPLAY=:0'
+Aug 19 17:32:48 Mine systemd-udevd[7206]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ export XAUTHORITY=/home/memyself/.Xauthority'
+Aug 19 17:32:48 Mine systemd-udevd[7206]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ XAUTHORITY=/home/memyself/.Xauthority'
+Aug 19 17:32:48 Mine systemd-udevd[7206]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ xrandr --query'
+Aug 19 17:32:48 Mine systemd-udevd[7206]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ grep eDP1'
+Aug 19 17:32:48 Mine systemd-udevd[7206]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(out) 'eDP1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 345mm x 194mm'
+Aug 19 17:32:48 Mine systemd-udevd[7206]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ xrandr --query'
+Aug 19 17:32:48 Mine systemd-udevd[7206]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ grep HDMI1'
+Aug 19 17:32:48 Mine systemd-udevd[7206]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(out) 'HDMI1 **[COLOR=#ff0000]connected[/COLOR]** (normal left inverted right x axis y axis)'
+Aug 19 17:32:48 Mine systemd-udevd[7206]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ xrandr --output eDP1 --auto --primary --output HDMI1 --auto --same-as eDP1'
+Aug 19 17:32:48 Mine systemd-udevd[7206]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ set +x'
+Aug 19 17:32:48 Mine systemd-udevd[7206]: Process '/bin/su memyself -c /usr/bin/MirrorToTv.sh' [COLOR=#ff0000]succeeded[/COLOR].
+Aug 19 17:32:48 Mine systemd-udevd[7206]:[COLOR=#ff0000] passed device to netlink monitor 0x55f1a3e6f3f0[/COLOR]
+Aug 19 17:32:48 Mine systemd-udevd[7206]: seq 3512 processed
+Aug 19 17:32:48 Mine systemd-udevd[6401]: cleanup idle workers
+Aug 19 17:32:48 Mine systemd-udevd[7206]: Unload module index
+Aug 19 17:32:48 Mine systemd-udevd[7206]: Unloaded link configuration context.
+Aug 19 17:32:48 Mine systemd-udevd[6401]: worker [7206] exited
+Aug 19 17:32:56 Mine systemd-udevd[6401]: seq 3513 queued, 'change' 'drm'
+Aug 19 17:32:56 Mine systemd-udevd[6401]: Validate module index
+Aug 19 17:32:56 Mine systemd-udevd[6401]: Check if link configuration needs reloading.
+Aug 19 17:32:56 Mine systemd-udevd[6401]: seq 3513 forked new worker [7222]
+Aug 19 17:32:56 Mine systemd-udevd[7222]: seq 3513 running
+Aug 19 17:32:56 Mine systemd-udevd[7222]: value '[dmi/id]sys_vendor' is 'TOSHIBA'
+Aug 19 17:32:56 Mine systemd-udevd[7222]: value '[dmi/id]sys_vendor' is 'TOSHIBA'
+Aug 19 17:32:56 Mine systemd-udevd[7222]: IMPORT builtin 'path_id' /lib/udev/rules.d/60-drm.rules:3
+Aug 19 17:32:56 Mine systemd-udevd[7222]: **RUN 'uaccess' /lib/udev/rules.d/73-seat-late.rules:15**
+Aug 19 17:32:56 Mine systemd-udevd[7222]: PROGRAM '/bin/readlink /etc/udev/rules.d/80-net-setup-link.rules' /lib/udev/rules.d/73-usb-net-by-mac.rules:6
+Aug 19 17:32:56 Mine systemd-udevd[7223]: starting '/bin/readlink /etc/udev/rules.d/80-net-setup-link.rules'
+Aug 19 17:32:56 Mine systemd-udevd[7222]: Process '/bin/readlink /etc/udev/rules.d/80-net-setup-link.rules' failed with exit code 1.
+Aug 19 17:32:56 Mine systemd-udevd[7222]: **RUN '/bin/su memyself -c /usr/bin/MirrorToTv.sh' /etc/udev/rules.d/90-MirrorToTv.rules:10**
+Aug 19 17:32:56 Mine systemd-udevd[7222]: handling device node '/dev/dri/card0', devnum=c226:0, mode=0600, uid=0, gid=0
+Aug 19 17:32:56 Mine systemd-udevd[7222]: preserve already existing symlink '/dev/char/226:0' to '../dri/card0'
+Aug 19 17:32:56 Mine systemd-udevd[7222]: created db file '/run/udev/data/c226:0' for '/devices/pci0000:00/0000:00:02.0/drm/card0'
+Aug 19 17:32:56 Mine systemd-udevd[7224]: starting '/bin/su memyself -c /usr/bin/MirrorToTv.sh'
+Aug 19 17:32:56 Mine systemd[1]: Started Session c77 of user memyself.
+Aug 19 17:32:56 Mine systemd-udevd[7222]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ export DISPLAY=:0'
+Aug 19 17:32:56 Mine systemd-udevd[7222]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ DISPLAY=:0'
+Aug 19 17:32:56 Mine systemd-udevd[7222]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ export XAUTHORITY=/home/memyself/.Xauthority'
+Aug 19 17:32:56 Mine systemd-udevd[7222]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ XAUTHORITY=/home/memyself/.Xauthority'
+Aug 19 17:32:56 Mine systemd-udevd[7222]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ xrandr --query'
+Aug 19 17:32:56 Mine systemd-udevd[7222]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ grep eDP1'
+Aug 19 17:32:56 Mine systemd-udevd[7222]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(out) 'eDP1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 345mm x 194mm'
+Aug 19 17:32:56 Mine systemd-udevd[7222]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ xrandr --query'
+Aug 19 17:32:56 Mine systemd-udevd[7222]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ grep HDMI1'
+Aug 19 17:32:56 Mine systemd-udevd[7222]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(out) 'HDMI1 [COLOR=#ff0000]**disconnected**[/COLOR] 1920x1080+0+0 (normal left inverted right x axis y axis) 0mm x 0mm' 
+Aug 19 17:32:56 Mine systemd-udevd[7222]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ xrandr --output eDP1 --auto --primary --output HDMI1 --auto --same-as eDP1'
+Aug 19 17:32:56 Mine systemd-udevd[7222]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ set +x'
+Aug 19 17:32:56 Mine systemd-udevd[7222]: Process '/bin/su memyself -c /usr/bin/MirrorToTv.sh'[COLOR=#ff0000] succeeded.[/COLOR]
+Aug 19 17:32:56 Mine systemd-udevd[7222]:[COLOR=#ff0000] passed device to netlink monitor 0x55f1a3e6f3f0[/COLOR]
+Aug 19 17:32:56 Mine systemd-udevd[7222]: seq 3513 processed
+Aug 19 17:32:56 Mine systemd-udevd[6401]: cleanup idle workers
+Aug 19 17:32:56 Mine systemd-udevd[7222]: Unload module index
+Aug 19 17:32:56 Mine systemd-udevd[7222]: Unloaded link configuration context.
+Aug 19 17:32:56 Mine systemd-udevd[6401]: worker [7222] exited
```

I have highlighted in red the bits that caught my attention. Nlote, the way the bash is called three times by udev mirrors the way the sytem  display window is called three times when the tv is switched on. 

For comparison, here is the output when I run the above script in a  terminal with the Tv connected, which, by the way works perfectly.
```
memyself@Mine:~$ /usr/bin/MirrorToTv.sh
+ export DISPLAY=:0
+ DISPLAY=:0
+ export XAUTHORITY=/home/memyself/.Xauthority
+ XAUTHORITY=/home/memyself/.Xauthority
+ xrandr --query
+ grep eDP1
eDP1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 345mm x 194mm
+ xrandr --query
+ grep HDMI1
HDMI1 connected (normal left inverted right x axis y axis)
+ xrandr --output eDP1 --auto --primary --output HDMI1 --auto --same-as eDP1
+ set +x
memyself@Mine:~$
```

At first, I thought, the "uaccess" rule was superseding my rule, so I changed my rules name to "90-MirrorToTv.rules". As you can see, this had no effect.

Is it possible that when the device is passed to "netlink monitor", it is somehow resetting the device?  

Your thoughts are very welcome
Irvine

Edit 

I meant to add that I have also found another possibly useful symptom. When I switch the laptop off, during shutdown it runs the above rule and for a very brief few seconds I have the laptop screen mirrored to the Tv. Similarly, when booting up I have a brief few seconds of mirrored screen before it reverts to the default state.

End edit

---

### Post by irvine_himself2 on 2016-08-20
**_[SIZE=4]Success![/SIZE]_**   :guitar:

Got to rush and take care of real life for a few hours, more details and testing to come. But I got it to work for the first time a few minutes ago. Unfortunately, I am very** LATE....**

Irvine

---

### Post by irvine_himself2 on 2016-08-20
Okay, everything seems to check out okay and I am finally ready to mark this thread solved. 

Firstly, with reference to post #13, I spent most of last night trying to figure out whether or not the "netlink monitor" was somehow overwriting the settings from the bash. After extensive research, and I do mean extensive, I found a lot of people trying to blame variations of the line indicated below for all their problems.
```
systemd-udevd[????]: passed device to netlink monitor ???????
```

However, I could find no evidence to support this, and absolutely no one had ever figured a way around it. Ergo, the mysterious "netlink monitor" was not rewriting my settings. This only really left the bash as the source of the failure. Since it was being executed, I obviously had the correct export authority, and, additionally, the bash runs perfectly from the panel. So, the only real clue left was the way, (again with reference to post #13.)  the Tv, (HDMI1,) alternated between being connected and disconnected.
```
....
....
+Aug 19 17:32:45 Mine systemd-udevd[7173]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ xrandr --query'
+Aug 19 17:32:45 Mine systemd-udevd[7173]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(out) 'HDMI1 **[COLOR=#ff0000]disconnected[/COLOR]** (normal left inverted right x axis y axis)'
+Aug 19 17:32:45 Mine systemd-udevd[7173]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ xrandr --output eDP1 --auto --primary --output HDMI1 --auto --same-as eDP1'
....
....
+Aug 19 17:32:45 Mine systemd-udevd[7188]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ xrandr --query'
+Aug 19 17:32:45 Mine systemd-udevd[7188]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ grep HDMI1'
+Aug 19 17:32:45 Mine systemd-udevd[7188]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(out) 'HDMI1 **[COLOR=#ff0000]disconnected[/COLOR]** (normal left inverted right x axis y axis)'
+Aug 19 17:32:45 Mine systemd-udevd[7188]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ xrandr --output eDP1 --auto --primary --output HDMI1 --auto --same-as eDP1'
....
....
+Aug 19 17:32:48 Mine systemd-udevd[7206]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ xrandr --query'
+Aug 19 17:32:48 Mine systemd-udevd[7206]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ grep HDMI1'
+Aug 19 17:32:48 Mine systemd-udevd[7206]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(out) 'HDMI1 **[COLOR=#ff0000]connected[/COLOR]** (normal left inverted right x axis y axis)'
+Aug 19 17:32:48 Mine systemd-udevd[7206]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ xrandr --output eDP1 --auto --primary --output HDMI1 --auto --same-as eDP1'
+Aug 19 17:32:48 Mine systemd-udevd[7206]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ set +x'
....
....
+Aug 19 17:32:56 Mine systemd-udevd[7222]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ xrandr --query'
+Aug 19 17:32:56 Mine systemd-udevd[7222]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ grep HDMI1'
+Aug 19 17:32:56 Mine systemd-udevd[7222]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(out) 'HDMI1 [COLOR=#ff0000]**disconnected**[/COLOR] 1920x1080+0+0 (normal left inverted right x axis y axis) 0mm x 0mm' 
+Aug 19 17:32:56 Mine systemd-udevd[7222]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ xrandr --output eDP1 --auto --primary --output HDMI1 --auto --same-as eDP1'
....
.....
```

So, I asked myself: "Self, do you think that the bash being called nearly simultaneously  multiple times could be creating some kind of interference?"

Definite possibilities here I thought, With that in mind, I modified the bash as follows. (Note, this is the production version, with debug helpers commented out):
```
#!/bin/bash 

# see https://askubuntu.com/questions/461553/which-command-line-commands-enable-mirror-feature-in-the-screen-display-gui
# also https://askubuntu.com/questions/119843/how-to-force-multiple-monitors-correct-resolutions-for-lightdm

# This script is activated by Udev rule kept in /etc/udev/rules.d/70-MirrorToTv.rules
# Note Udev naming convention for rules is important!
# see https://blog.sleeplessbeastie.eu/2013/01/07/how-to-automatically-set-up-external-monitor/
# see https://hackaday.com/2009/09/18/how-to-write-udev-rules/
# see http://www.reactivated.net/writing_udev_rules.html 

# Also see https://ubuntuforums.org/showthread.php?t=2334004 for development log

# debug, my own little debug trick
# /bin/echo "$(date) Executing udev monitor clone....." >> /home/memyself/Desktop/MirrorDebug.txt

# debug set -x, see http://www.cyberciti.biz/tips/debugging-shell-script.html
# set -x

# doesn't work without user autherity
export DISPLAY=:0
export XAUTHORITY=/home/memyself/.Xauthority


# Check default screen is eDP1
if xrandr --query | grep "eDP1 connected"; then
  # check HDMI is connected as "HDMI1"
  if xrandr --query | grep "HDMI1 connected"; then
    xrandr --output eDP1 --auto --primary --output HDMI1 --auto --same-as eDP1
   else if xrandr --query | grep "HDMI-1 connected"; then
      # when testing hardware, it was usually called HDMI1, but, as I recall, it occasionally called itself HDMI-1
      xrandr --output eDP1 --auto --primary --output HDMI-1 --auto --same-as eDP1
    fi
  fi
fi

# debug set +x, see http://www.cyberciti.biz/tips/debugging-shell-script.html
# set +x
```

You may imagine my surprise when it actually worked.

For reference, here is the correct udev rule
```
# Calls /usr/bin/MirrorToTv.sh when HDMI tv is connected

# see https://blog.sleeplessbeastie.eu/2013/01/07/how-to-automatically-set-up-external-monitor/
# see https://hackaday.com/2009/09/18/how-to-write-udev-rules/
# see http://www.reactivated.net/writing_udev_rules.html 

# Note Udev naming convention for rules is important!


KERNEL=="card0", SUBSYSTEM=="drm", ACTION=="change", RUN+="/bin/su memyself -c /usr/bin/MirrorToTv.sh"
```

And for comparison, here is the debug output from the working rule, (Note how the bash only tries to configure the Tv once):
```
--- -    2016-08-20 15:22:29.762576530 +0100
+++ /var/log/syslog    2016-08-20 15:22:22.379881414 +0100
@@ -297126,3 +297126,149 @@
 Aug 20 15:21:39 Mine systemd-udevd[5658]: Unload module index
 Aug 20 15:21:39 Mine systemd-udevd[5658]: Unloaded link configuration context.
 Aug 20 15:21:39 Mine systemd-udevd[1136]: worker [5658] exited
+Aug 20 15:22:10 Mine systemd-udevd[1136]: seq 3442 queued, 'change' 'drm'
+Aug 20 15:22:10 Mine systemd-udevd[1136]: Validate module index
+Aug 20 15:22:10 Mine systemd-udevd[1136]: Check if link configuration needs reloading.
+Aug 20 15:22:10 Mine systemd-udevd[1136]: seq 3442 forked new worker [5708]
+Aug 20 15:22:10 Mine systemd-udevd[5708]: seq 3442 running
+Aug 20 15:22:10 Mine systemd-udevd[5708]: value '[dmi/id]sys_vendor' is 'TOSHIBA'
+Aug 20 15:22:10 Mine systemd-udevd[5708]: value '[dmi/id]sys_vendor' is 'TOSHIBA'
+Aug 20 15:22:10 Mine systemd-udevd[5708]: IMPORT builtin 'path_id' /lib/udev/rules.d/60-drm.rules:3
+Aug 20 15:22:10 Mine systemd-udevd[5708]: RUN 'uaccess' /lib/udev/rules.d/73-seat-late.rules:15
+Aug 20 15:22:10 Mine systemd-udevd[5708]: PROGRAM '/bin/readlink /etc/udev/rules.d/80-net-setup-link.rules' /lib/udev/rules.d/73-usb-net-by-mac.rules:6
+Aug 20 15:22:10 Mine systemd-udevd[5709]: starting '/bin/readlink /etc/udev/rules.d/80-net-setup-link.rules'
+Aug 20 15:22:10 Mine systemd-udevd[5708]: Process '/bin/readlink /etc/udev/rules.d/80-net-setup-link.rules' failed with exit code 1.
+Aug 20 15:22:10 Mine systemd-udevd[5708]: RUN '/bin/su memyself -c /usr/bin/MirrorToTv.sh' /etc/udev/rules.d/90-MirrorToTv.rules:10
+Aug 20 15:22:10 Mine systemd-udevd[5708]: handling device node '/dev/dri/card0', devnum=c226:0, mode=0600, uid=0, gid=0
+Aug 20 15:22:10 Mine systemd-udevd[5708]: preserve already existing symlink '/dev/char/226:0' to '../dri/card0'
+Aug 20 15:22:10 Mine systemd-udevd[5708]: created db file '/run/udev/data/c226:0' for '/devices/pci0000:00/0000:00:02.0/drm/card0'
+Aug 20 15:22:10 Mine systemd-udevd[5710]: starting '/bin/su memyself -c /usr/bin/MirrorToTv.sh'
+Aug 20 15:22:10 Mine systemd[1]: Started Session c10 of user memyself.
+Aug 20 15:22:10 Mine systemd-udevd[5708]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ export DISPLAY=:0'
+Aug 20 15:22:10 Mine systemd-udevd[5708]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ DISPLAY=:0'
+Aug 20 15:22:10 Mine systemd-udevd[5708]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ export XAUTHORITY=/home/memyself/.Xauthority'
+Aug 20 15:22:10 Mine systemd-udevd[5708]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ XAUTHORITY=/home/memyself/.Xauthority'
+Aug 20 15:22:10 Mine systemd-udevd[5708]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ grep eDP1'
+Aug 20 15:22:10 Mine systemd-udevd[5708]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ xrandr --query'
+Aug 20 15:22:11 Mine systemd-udevd[5708]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(out) 'eDP1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 345mm x 194mm'
+Aug 20 15:22:11 Mine systemd-udevd[5708]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ xrandr --query'
+Aug 20 15:22:11 Mine systemd-udevd[5708]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ grep 'HDMI1 connected''
+Aug 20 15:22:11 Mine systemd-udevd[5708]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ xrandr --query'
+Aug 20 15:22:11 Mine systemd-udevd[5708]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ grep 'HDMI-1 connected''**    (Comment: skipped trying to configure the Tv as HDMI1 and tries HDMI1-1)**
+Aug 20 15:22:11 Mine systemd-udevd[5708]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ set +x'
+Aug 20 15:22:11 Mine systemd-udevd[5708]: Process '/bin/su memyself -c /usr/bin/MirrorToTv.sh' succeeded.
+Aug 20 15:22:11 Mine systemd-udevd[5708]: passed device to netlink monitor 0x5630b78140f0
+Aug 20 15:22:11 Mine systemd-udevd[5708]: seq 3442 processed
+Aug 20 15:22:11 Mine systemd-udevd[1136]: cleanup idle workers
+Aug 20 15:22:11 Mine systemd-udevd[5708]: Unload module index
+Aug 20 15:22:11 Mine systemd-udevd[5708]: Unloaded link configuration context.
+Aug 20 15:22:11 Mine systemd-udevd[1136]: worker [5708] exited
+Aug 20 15:22:11 Mine systemd-udevd[1136]: seq 3443 queued, 'change' 'drm'
+Aug 20 15:22:11 Mine systemd-udevd[1136]: seq 3443 forked new worker [5722]
+Aug 20 15:22:11 Mine systemd-udevd[5722]: seq 3443 running
+Aug 20 15:22:11 Mine systemd-udevd[5722]: value '[dmi/id]sys_vendor' is 'TOSHIBA'
+Aug 20 15:22:11 Mine systemd-udevd[5722]: value '[dmi/id]sys_vendor' is 'TOSHIBA'
+Aug 20 15:22:11 Mine systemd-udevd[5722]: IMPORT builtin 'path_id' /lib/udev/rules.d/60-drm.rules:3
+Aug 20 15:22:11 Mine systemd-udevd[5722]: RUN 'uaccess' /lib/udev/rules.d/73-seat-late.rules:15
+Aug 20 15:22:11 Mine systemd-udevd[5722]: PROGRAM '/bin/readlink /etc/udev/rules.d/80-net-setup-link.rules' /lib/udev/rules.d/73-usb-net-by-mac.rules:6
+Aug 20 15:22:11 Mine systemd-udevd[5723]: starting '/bin/readlink /etc/udev/rules.d/80-net-setup-link.rules'
+Aug 20 15:22:11 Mine systemd-udevd[5722]: Process '/bin/readlink /etc/udev/rules.d/80-net-setup-link.rules' failed with exit code 1.
+Aug 20 15:22:11 Mine systemd-udevd[5722]: RUN '/bin/su memyself -c /usr/bin/MirrorToTv.sh' /etc/udev/rules.d/90-MirrorToTv.rules:10
+Aug 20 15:22:11 Mine systemd-udevd[5722]: handling device node '/dev/dri/card0', devnum=c226:0, mode=0600, uid=0, gid=0
+Aug 20 15:22:11 Mine systemd-udevd[5722]: preserve already existing symlink '/dev/char/226:0' to '../dri/card0'
+Aug 20 15:22:11 Mine systemd-udevd[5722]: created db file '/run/udev/data/c226:0' for '/devices/pci0000:00/0000:00:02.0/drm/card0'
+Aug 20 15:22:11 Mine systemd-udevd[5724]: starting '/bin/su memyself -c /usr/bin/MirrorToTv.sh'
+Aug 20 15:22:11 Mine systemd[1]: Started Session c11 of user memyself.
+Aug 20 15:22:11 Mine systemd-udevd[5722]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ export DISPLAY=:0'
+Aug 20 15:22:11 Mine systemd-udevd[5722]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ DISPLAY=:0'
+Aug 20 15:22:11 Mine systemd-udevd[5722]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ export XAUTHORITY=/home/memyself/.Xauthority'
+Aug 20 15:22:11 Mine systemd-udevd[5722]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ XAUTHORITY=/home/memyself/.Xauthority'
+Aug 20 15:22:11 Mine systemd-udevd[5722]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ xrandr --query'
+Aug 20 15:22:11 Mine systemd-udevd[5722]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ grep eDP1'
+Aug 20 15:22:11 Mine systemd-udevd[5722]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(out) 'eDP1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 345mm x 194mm'
+Aug 20 15:22:11 Mine systemd-udevd[5722]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ xrandr --query'
+Aug 20 15:22:11 Mine systemd-udevd[5722]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ grep 'HDMI1 connected''
+Aug 20 15:22:11 Mine systemd-udevd[5722]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ xrandr --query'
+Aug 20 15:22:11 Mine systemd-udevd[5722]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ grep 'HDMI-1 connected''**    (Comment: skipped trying to configure the Tv as HDMI1 and tries HDMI1-1)**
+Aug 20 15:22:11 Mine systemd-udevd[5722]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ set +x'
+Aug 20 15:22:11 Mine systemd-udevd[5722]: Process '/bin/su memyself -c /usr/bin/MirrorToTv.sh' succeeded.
+Aug 20 15:22:11 Mine systemd-udevd[5722]: passed device to netlink monitor 0x5630b78140f0
+Aug 20 15:22:11 Mine systemd-udevd[5722]: seq 3443 processed
+Aug 20 15:22:11 Mine systemd-udevd[1136]: cleanup idle workers
+Aug 20 15:22:11 Mine systemd-udevd[5722]: Unload module index
+Aug 20 15:22:11 Mine systemd-udevd[5722]: Unloaded link configuration context.
+Aug 20 15:22:11 Mine systemd-udevd[1136]: worker [5722] exited
+Aug 20 15:22:14 Mine systemd-udevd[1136]: seq 3444 queued, 'change' 'drm'
+Aug 20 15:22:14 Mine systemd-udevd[1136]: Validate module index
+Aug 20 15:22:14 Mine systemd-udevd[1136]: Check if link configuration needs reloading.
+Aug 20 15:22:14 Mine systemd-udevd[1136]: seq 3444 forked new worker [5739]
+Aug 20 15:22:14 Mine systemd-udevd[5739]: seq 3444 running
+Aug 20 15:22:14 Mine systemd-udevd[5739]: value '[dmi/id]sys_vendor' is 'TOSHIBA'
+Aug 20 15:22:14 Mine systemd-udevd[5739]: value '[dmi/id]sys_vendor' is 'TOSHIBA'
+Aug 20 15:22:14 Mine systemd-udevd[5739]: IMPORT builtin 'path_id' /lib/udev/rules.d/60-drm.rules:3
+Aug 20 15:22:14 Mine systemd-udevd[5739]: RUN 'uaccess' /lib/udev/rules.d/73-seat-late.rules:15
+Aug 20 15:22:14 Mine systemd-udevd[5739]: PROGRAM '/bin/readlink /etc/udev/rules.d/80-net-setup-link.rules' /lib/udev/rules.d/73-usb-net-by-mac.rules:6
+Aug 20 15:22:14 Mine systemd-udevd[5740]: starting '/bin/readlink /etc/udev/rules.d/80-net-setup-link.rules'
+Aug 20 15:22:14 Mine systemd-udevd[5739]: Process '/bin/readlink /etc/udev/rules.d/80-net-setup-link.rules' failed with exit code 1.
+Aug 20 15:22:14 Mine systemd-udevd[5739]: RUN '/bin/su memyself -c /usr/bin/MirrorToTv.sh' /etc/udev/rules.d/90-MirrorToTv.rules:10
+Aug 20 15:22:14 Mine systemd-udevd[5739]: handling device node '/dev/dri/card0', devnum=c226:0, mode=0600, uid=0, gid=0
+Aug 20 15:22:14 Mine systemd-udevd[5739]: preserve already existing symlink '/dev/char/226:0' to '../dri/card0'
+Aug 20 15:22:14 Mine systemd-udevd[5739]: created db file '/run/udev/data/c226:0' for '/devices/pci0000:00/0000:00:02.0/drm/card0'
+Aug 20 15:22:14 Mine systemd-udevd[5741]: starting '/bin/su memyself -c /usr/bin/MirrorToTv.sh'
+Aug 20 15:22:14 Mine systemd[1]: Started Session c12 of user memyself.
+Aug 20 15:22:14 Mine systemd-udevd[5739]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ export DISPLAY=:0'
+Aug 20 15:22:14 Mine systemd-udevd[5739]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ DISPLAY=:0'
+Aug 20 15:22:14 Mine systemd-udevd[5739]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ export XAUTHORITY=/home/memyself/.Xauthority'
+Aug 20 15:22:14 Mine systemd-udevd[5739]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ XAUTHORITY=/home/memyself/.Xauthority'
+Aug 20 15:22:14 Mine systemd-udevd[5739]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ xrandr --query'
+Aug 20 15:22:14 Mine systemd-udevd[5739]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ grep eDP1'
+Aug 20 15:22:14 Mine systemd-udevd[5739]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(out) 'eDP1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 345mm x 194mm'
+Aug 20 15:22:14 Mine systemd-udevd[5739]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ grep 'HDMI1 connected''
+Aug 20 15:22:14 Mine systemd-udevd[5739]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ xrandr --query'
+Aug 20 15:22:14 Mine systemd-udevd[5739]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(out) 'HDMI1 connected (normal left inverted right x axis y axis)'
+Aug 20 15:22:14 Mine systemd-udevd[5739]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ xrandr --output eDP1 --auto --primary --output HDMI1 --auto --same-as eDP1'  **(Comment: this is where the Tv is configured)**
+Aug 20 15:22:14 Mine systemd-udevd[5739]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ set +x'
+Aug 20 15:22:14 Mine systemd-udevd[5739]: Process '/bin/su memyself -c /usr/bin/MirrorToTv.sh' succeeded.
+Aug 20 15:22:14 Mine systemd-udevd[5739]: passed device to netlink monitor 0x5630b78140f0
+Aug 20 15:22:14 Mine systemd-udevd[5739]: seq 3444 processed
+Aug 20 15:22:14 Mine systemd-udevd[1136]: cleanup idle workers
+Aug 20 15:22:14 Mine systemd-udevd[5739]: Unload module index
+Aug 20 15:22:14 Mine systemd-udevd[5739]: Unloaded link configuration context.
+Aug 20 15:22:14 Mine systemd-udevd[1136]: worker [5739] exited
+Aug 20 15:22:22 Mine systemd-udevd[1136]: seq 3445 queued, 'change' 'drm'
+Aug 20 15:22:22 Mine systemd-udevd[1136]: Validate module index
+Aug 20 15:22:22 Mine systemd-udevd[1136]: Check if link configuration needs reloading.
+Aug 20 15:22:22 Mine systemd-udevd[1136]: seq 3445 forked new worker [5753]
+Aug 20 15:22:22 Mine systemd-udevd[5753]: seq 3445 running
+Aug 20 15:22:22 Mine systemd-udevd[5753]: value '[dmi/id]sys_vendor' is 'TOSHIBA'
+Aug 20 15:22:22 Mine systemd-udevd[5753]: value '[dmi/id]sys_vendor' is 'TOSHIBA'
+Aug 20 15:22:22 Mine systemd-udevd[5753]: IMPORT builtin 'path_id' /lib/udev/rules.d/60-drm.rules:3
+Aug 20 15:22:22 Mine systemd-udevd[5753]: RUN 'uaccess' /lib/udev/rules.d/73-seat-late.rules:15
+Aug 20 15:22:22 Mine systemd-udevd[5753]: PROGRAM '/bin/readlink /etc/udev/rules.d/80-net-setup-link.rules' /lib/udev/rules.d/73-usb-net-by-mac.rules:6
+Aug 20 15:22:22 Mine systemd-udevd[5754]: starting '/bin/readlink /etc/udev/rules.d/80-net-setup-link.rules'
+Aug 20 15:22:22 Mine systemd-udevd[5753]: Process '/bin/readlink /etc/udev/rules.d/80-net-setup-link.rules' failed with exit code 1.
+Aug 20 15:22:22 Mine systemd-udevd[5753]: RUN '/bin/su memyself -c /usr/bin/MirrorToTv.sh' /etc/udev/rules.d/90-MirrorToTv.rules:10
+Aug 20 15:22:22 Mine systemd-udevd[5753]: handling device node '/dev/dri/card0', devnum=c226:0, mode=0600, uid=0, gid=0
+Aug 20 15:22:22 Mine systemd-udevd[5753]: preserve already existing symlink '/dev/char/226:0' to '../dri/card0'
+Aug 20 15:22:22 Mine systemd-udevd[5753]: created db file '/run/udev/data/c226:0' for '/devices/pci0000:00/0000:00:02.0/drm/card0'
+Aug 20 15:22:22 Mine systemd-udevd[5755]: starting '/bin/su memyself -c /usr/bin/MirrorToTv.sh'
+Aug 20 15:22:22 Mine systemd[1]: Started Session c13 of user memyself.
+Aug 20 15:22:22 Mine systemd-udevd[5753]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ export DISPLAY=:0'
+Aug 20 15:22:22 Mine systemd-udevd[5753]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ DISPLAY=:0'
+Aug 20 15:22:22 Mine systemd-udevd[5753]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ export XAUTHORITY=/home/memyself/.Xauthority'
+Aug 20 15:22:22 Mine systemd-udevd[5753]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ XAUTHORITY=/home/memyself/.Xauthority'
+Aug 20 15:22:22 Mine systemd-udevd[5753]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ grep eDP1'
+Aug 20 15:22:22 Mine systemd-udevd[5753]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ xrandr --query'
+Aug 20 15:22:22 Mine systemd-udevd[5753]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(out) 'eDP1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 345mm x 194mm'
+Aug 20 15:22:22 Mine systemd-udevd[5753]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ grep 'HDMI1 connected''
+Aug 20 15:22:22 Mine systemd-udevd[5753]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ xrandr --query'
+Aug 20 15:22:22 Mine systemd-udevd[5753]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ grep 'HDMI-1 connected''**    (Comment: skipped trying to configure the Tv as HDMI1 and tries HDMI1-1)**
+Aug 20 15:22:22 Mine systemd-udevd[5753]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ xrandr --query'
+Aug 20 15:22:22 Mine systemd-udevd[5753]: '/bin/su memyself -c /usr/bin/MirrorToTv.sh'(err) '+ set +x'
+Aug 20 15:22:22 Mine systemd-udevd[5753]: Process '/bin/su memyself -c /usr/bin/MirrorToTv.sh' succeeded.
+Aug 20 15:22:22 Mine systemd-udevd[5753]: passed device to netlink monitor 0x5630b78140f0
+Aug 20 15:22:22 Mine systemd-udevd[5753]: seq 3445 processed
+Aug 20 15:22:22 Mine systemd-udevd[1136]: cleanup idle workers
+Aug 20 15:22:22 Mine systemd-udevd[5753]: Unload module index
+Aug 20 15:22:22 Mine systemd-udevd[5753]: Unloaded link configuration context.
+Aug 20 15:22:22 Mine systemd-udevd[1136]: worker [5753] exited
```

There are no drugs that can give a buzz like solving a difficult technical problem, and, as an added bonus, I can now snooze my laptops' alarm clock without getting out of bed!

Have a nice day everyone, I think I am going to go back to bed and watch Tv.
Irvine

:popcorn:

---

### Post by ian-weisser on 2016-08-22
Thanks for sharing your solution with such a great and helpful writeup!

---

### Post by irvine_himself2 on 2016-08-22
Thanks, your welcome, 

For my next trick, I have decided to try something really challenging and build my own Arch Linux installation. After _only_ two day's, I have already got the the Arch  base installed as a dual boot with Ubuntu, and, (mainly from Ubuntu through "chroot",) am slowly building my knowledge base as I build and configure my dream distro.

Irvine

---

