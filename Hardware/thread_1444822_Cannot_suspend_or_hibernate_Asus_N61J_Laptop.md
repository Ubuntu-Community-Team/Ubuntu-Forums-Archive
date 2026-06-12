---
title: "Cannot suspend or hibernate Asus N61J Laptop"
date: 2010-04-01
forum: Hardware
---

### Post by ipsi on 2010-04-01
Recently got a new laptop for work, an Asus N61J, and I installed Ubuntu 9.10 on it. For whatever reason, the laptop will not suspend. I have no idea why, as it looks like it is going to, but ultimately dumps me back at the Unlock screen, as though I had just locked the computer, rather than suspending it.

However, it does kick me off my wireless network, so I think it *does* suspend, but only for a second or so.

Looking at /var/log/pm-suspend.log, I see

```
Initial commandline parameters: 
Fri Apr  2 12:25:45 NZDT 2010: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/000record suspend suspend: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk suspend suspend: Adding quirks from HAL: --quirk-dpms-on --quirk-dpms-suspend --quirk-vbe-post --quirk-vbemode-restore --quirk-vbestate-restore --quirk-vga-mode-3 
success.
/usr/lib/pm-utils/sleep.d/00logging suspend suspend: Linux andrew-laptop 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 04:38:19 UTC 2010 x86_64 GNU/Linux
Module                  Size  Used by
tun                    17056  2 
nls_iso8859_1           5280  1 
nls_cp437               6976  1 
vfat                   13184  1 
fat                    59832  1 vfat
cbc                     4224  315 
cryptd                  8008  0 
aes_x86_64              8992  318 
aes_generic            28480  1 aes_x86_64
binfmt_misc            10220  1 
ppdev                   8232  0 
bridge                 56384  0 
stp                     3012  1 bridge
bnep                   15168  2 
dm_crypt               14888  0 
usb_storage            66304  1 
snd_hda_codec_atihdmi     4320  1 
snd_hda_codec_realtek   277860  1 
ipt_REJECT              3584  1 
ipt_LOG                 6404  1 
xt_limit                3236  2 
xt_tcpudp               3616  7 
xt_state                2432  6 
ipt_addrtype            2912  4 
arc4                    2144  2 
ecb                     3296  3 
ath9k                 278176  0 
mac80211              210040  1 ath9k
ath                    10304  1 ath9k
ip6table_filter         3968  1 
ip6_tables             22608  1 ip6table_filter
nf_nat_irc              2688  0 
nf_conntrack_irc        6552  1 nf_nat_irc
nf_nat_ftp              3584  0 
nf_nat                 22452  2 nf_nat_irc,nf_nat_ftp
nf_conntrack_ipv4      16376  8 nf_nat
nf_defrag_ipv4          2400  1 nf_conntrack_ipv4
snd_hda_intel          31880  2 
snd_seq_dummy           3460  0 
snd_hda_codec          87584  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel
nf_conntrack_ftp        9016  1 nf_nat_ftp
snd_hwdep               9352  1 snd_hda_codec
nf_conntrack           80800  7 xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
snd_seq_oss            33440  0 
iptable_filter          3872  1 
snd_pcm_oss            44704  0 
snd_seq_midi            8192  0 
ip_tables              21200  1 iptable_filter
snd_mixer_oss          18976  1 snd_pcm_oss
snd_rawmidi            27296  1 snd_seq_midi
uvcvideo               65260  0 
snd_pcm                93160  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
x_tables               25832  8 ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,xt_state,ipt_addrtype,ip6_tables,ip_tables
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
videodev               43360  1 uvcvideo
v4l1_compat            16644  2 uvcvideo,videodev
v4l2_compat_ioctl32    13344  1 videodev
snd_timer              26992  2 snd_pcm,snd_seq
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
psmouse                57124  0 
joydev                 13088  0 
serio_raw               6596  0 
xhci                   40772  0 
btusb                  14260  2 
fglrx                2234552  32 
snd                    77096  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_seq_oss,snd_pcm_oss,snd_mixer_oss,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
atl1c                  36516  0 
cfg80211              109144  3 ath9k,mac80211,ath
soundcore               9088  1 snd
asus_laptop            21092  0 
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm
lp                     11908  0 
led_class               5256  2 ath9k,asus_laptop
parport                40528  2 ppdev,lp
video                  23612  0 
usbhid                 43968  0 
output                  3680  1 video
             total       used       free     shared    buffers     cached
Mem:       3982980    1122480    2860500          0      54648     361724
-/+ buffers/cache:     706108    3276872
Swap:     11671180          0   11671180
success.
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
/etc/pm/sleep.d/10_grub-common suspend suspend: success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.
/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: stop: Unknown instance: 
success.
/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
/usr/lib/pm-utils/sleep.d/96laptop-mode suspend suspend: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video suspend suspend: success.
/usr/lib/pm-utils/sleep.d/99video suspend suspend: kernel.acpi_video_flags = 0
success.
/etc/pm/sleep.d/action_wpa suspend suspend: success.
Fri Apr  2 12:25:47 NZDT 2010: performing suspend
Fri Apr  2 12:25:53 NZDT 2010: Awake.
Fri Apr  2 12:25:53 NZDT 2010: Running hooks for resume
/etc/pm/sleep.d/action_wpa resume suspend: success.
/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video resume suspend: success.
/usr/lib/pm-utils/sleep.d/96laptop-mode resume suspend: success.
/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
/usr/lib/pm-utils/sleep.d/49bluetooth resume suspend: not applicable.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
/etc/pm/sleep.d/10_grub-common resume suspend: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk resume suspend: success.
/usr/lib/pm-utils/sleep.d/000record resume suspend: success.
Fri Apr  2 12:25:53 NZDT 2010: Finished.
```

The two important lines seem to be

```
Fri Apr  2 12:25:47 NZDT 2010: performing suspend
Fri Apr  2 12:25:53 NZDT 2010: Awake.
```

Which indicates that yes, it did suspend - for 6 seconds. Which isn't terribly useful.

Does anyone have any ideas on what's going wrong, and how can I fix it?

Is it possible the laptop is just a little too new, and is missing some hardware drivers or something?

For what its worth, I'm using the Proprietary ATi Drivers, but otherwise have a fairly clean install of Ubuntu 9.10.

EDIT: I'm running the 64bit Version of Ubuntu.

---

### Post by ipsi on 2010-04-02
Little more information: It also, for some bizarre reason, unmutes my sound when it 'resumes' from suspend, which is kind of odd. Doesn't seem to touch anything else, though I think it may have killed or failed to restart my Open VPN process once. Testing again, that doesn't seem to be happening, so maybe I was just imagining it.

---

### Post by ipsi on 2010-04-03
Ok, it would seem to be a problem with one of the internal USB devices - I disabled all external ports in the BIOS, and it suspended! Yay!

However, I can't selectively disable them one by one in the BIOS - it's an all or nothing thing. So I need to tell Ubuntu to either not load the drivers for this particular USB device, or to completely disable it or something. Trouble is, I'm not sure how to go about doing that. Suggestions would be strongly appreciated.

---

### Post by ipsi on 2010-04-03
Ok, here's the output from /var/log/syslog regarding why it doesn't want to go to sleep:

```
Apr  3 19:49:08 andrew-laptop NetworkManager: <info>  Sleeping...
Apr  3 19:49:08 andrew-laptop NetworkManager: <info>  (wlan0): now unmanaged
Apr  3 19:49:08 andrew-laptop NetworkManager: <info>  (wlan0): device state change: 8 -> 1 (reason 37)
Apr  3 19:49:08 andrew-laptop NetworkManager: <info>  (wlan0): deactivating device (reason: 37).
Apr  3 19:49:08 andrew-laptop NetworkManager: <info>  (wlan0): canceled DHCP transaction, dhcp client pid 2206
Apr  3 19:49:08 andrew-laptop kernel: [   51.001203] wlan0: disassociating by local choice (reason=3)
Apr  3 19:49:08 andrew-laptop wpa_supplicant[1042]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Apr  3 19:49:08 andrew-laptop NetworkManager: <WARN>  check_one_route(): (wlan0) error -34 returned from rtnl_route_del(): Sucess#012
Apr  3 19:49:08 andrew-laptop dnsmasq[1208]: reading /etc/resolv.conf
Apr  3 19:49:08 andrew-laptop dnsmasq[1208]: using nameserver 192.168.0.1#53
Apr  3 19:49:08 andrew-laptop avahi-daemon[873]: Withdrawing address record for 192.168.0.105 on wlan0.
Apr  3 19:49:08 andrew-laptop avahi-daemon[873]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.0.105.
Apr  3 19:49:08 andrew-laptop avahi-daemon[873]: Interface wlan0.IPv4 no longer relevant for mDNS.
Apr  3 19:49:08 andrew-laptop NetworkManager: <info>  (wlan0): cleaning up...
Apr  3 19:49:08 andrew-laptop NetworkManager: <info>  (wlan0): taking down device.
Apr  3 19:49:08 andrew-laptop wpa_supplicant[1042]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Apr  3 19:49:08 andrew-laptop kernel: [   51.132498] wlan0: deauthenticating by local choice (reason=3)
Apr  3 19:49:08 andrew-laptop NetworkManager: <info>  (eth0): now unmanaged
Apr  3 19:49:08 andrew-laptop NetworkManager: <info>  (eth0): device state change: 2 -> 1 (reason 37)
Apr  3 19:49:08 andrew-laptop NetworkManager: <info>  (eth0): cleaning up...
Apr  3 19:49:08 andrew-laptop NetworkManager: <info>  (eth0): taking down device.
Apr  3 19:49:08 andrew-laptop avahi-daemon[873]: Withdrawing address record for fe80::225:d3ff:fece:c8c1 on wlan0.
Apr  3 19:49:10 andrew-laptop kernel: [   52.929213] PM: Syncing filesystems ... done.
Apr  3 19:49:10 andrew-laptop kernel: [   52.930188] PM: Preparing system for mem sleep
Apr  3 19:49:10 andrew-laptop kernel: [   52.930191] Freezing user space processes ... (elapsed 0.00 seconds) done.
Apr  3 19:49:10 andrew-laptop kernel: [   52.930589] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
Apr  3 19:49:10 andrew-laptop kernel: [   52.930624] PM: Entering mem sleep
Apr  3 19:49:10 andrew-laptop kernel: [   52.930639] Suspending console(s) (use no_console_suspend to debug)
Apr  3 19:49:10 andrew-laptop kernel: [   52.998478] pm_op(): usb_dev_suspend+0x0/0x10 returns -2
Apr  3 19:49:10 andrew-laptop kernel: [   52.998487] PM: Device usb3 failed to suspend: error -2
Apr  3 19:49:10 andrew-laptop kernel: [   52.998488] PM: Some devices failed to suspend
Apr  3 19:49:10 andrew-laptop kernel: [   53.097539] PM: resume devices took 0.100 seconds
Apr  3 19:49:10 andrew-laptop kernel: [   53.097756] PM: Finishing wakeup.
Apr  3 19:49:10 andrew-laptop kernel: [   53.097758] Restarting tasks ... done.
```

As you can see, the lines ```
Apr  3 19:49:10 andrew-laptop kernel: [   52.998478] pm_op(): usb_dev_suspend+0x0/0x10 returns -2
Apr  3 19:49:10 andrew-laptop kernel: [   52.998487] PM: Device usb3 failed to suspend: error -2
Apr  3 19:49:10 andrew-laptop kernel: [   52.998488] PM: Some devices failed to suspend
```
are what is causing the laptop to fail to suspend.

Output from lsusb:

```
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 13d3:5122 IMC Networks 
Bus 001 Device 004: ID 0b05:1788 ASUSTek Computer, Inc. 
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 004: ID 046d:c510 Logitech, Inc. Cordless Mouse
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

Now, I'm not sure whether it's referring to bus 3, device 1 or bus 1 device 3 (I would assume bus 3, but I could be wrong).

Assuming it is Bus 3, then here is the sudo lusb -v output for it:

```
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               3.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         3 
  bMaxPacketSize0         9
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0002 2.0 root hub
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.31-20-generic xhci_hcd
  iProduct                2 xHCI Host Controller
  iSerial                 1 0000:07:00.0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              12
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             4
  wHubCharacteristic 0x0009
    Per-port power switching
    Per-port overcurrent protection
    TT think time 8 FS bits
  bPwrOn2PwrGood       10 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
   Port 3: 0000.0100 power
   Port 4: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled
```

What I would really like is some way to tell Linux that the USB Device(s) that are failing to suspend don't exist. I can't go into the case and unplug them, and I really, really would like to be able to suspend/hibernate this laptop.

As I said above, disabling all USB devices fixes this problem, but that in turn prevents me from using a USB keyboard and/or mouse, so that to is not an option.

Googling around, I can't seem to find any instructions for actually doing this, but it's possible I'm using the wrong search terms.

---

### Post by ipsi on 2010-04-03
If anyone is reading this, this is just a quick reply because I'm hungry and tired, but it seems I was wrong (:O), and that usb3 may actually refer to USB 3.0.

Blacklisting the XHCI driver seems to support this theory, as things work differently when it tries to suspend or hibernate. Unfortunately, it still doesn't work but at least the behaviour is different!

Actually, Hibernate technically works. Very, very technically. Not something I'd use every day.

Hibernate spits out a bunch of messages when I select it, and starts eating the hard drive. Eventually it stops and does nothing else, leaving the text on the screen with a blinking underscore. If I manually power off and power back on, it does actually restore from the hibernate file! Only downside is my wireless doesn't like that (and I imagine there are a few other things that don't either), and it just seems like a really bad idea. But it does work.

---

### Post by nuage6 on 2010-04-13
On my HP 8540w I have created the following script 

/etc/pm/sleep.d/05_xhci

The content of this file is
```
#!/bin/sh
# Fix some issues with USB3

if [ "$1" = "suspend" ]
then
        modprobe -r xhci
fi

if [ "$1" = "resume" ]
then
        modprobe xhci
fi

```

chmod 755 /etc/pm/sleep.d/05_xhci

And now I can use my USB3 devices and go in suspend mode.
(Perhaps you need to change the script to hibernate)

Note that I use Lucid, version 10.4 beta 2
Perhaps you'll need to store this file on a folder called suspend.d
Thank you for the tips helping me to understand the issue.

Regards
Gab

---

### Post by John Dias on 2010-04-27
Hi [ipsi]("http://art.ubuntuforums.org/member.php?u=285138"),
I'm Brazilian, so my english....
I have the same problem of you with an Asus n71Jq-x1. I'm pretty sure you're succeed like me. I try with this versions of Ubuntu, and all worked fine:

    * Ubuntu 9.10 64bits
    * Ubuntu 10.4 R3 64bits
    * Ubuntu Studio 10.4 R3 64bits

The problem is about the ehci builtin controller and xhci module.
The better solutions is to disable all devices that uses ehci_hcd from Kernel, and to unload module xhci, before suspend/hibernate. For the last, you can use the nuage6's solution, but I prefer to use the "config.d", as I describe in section 2. Another solution is to complete disable usb support in BIOS, but I guess you don't need to do this.

1. Unbind ehci_hcd from kernel:

First, verify what devices you need to unload from kernel. Simple list the directory "/sys/bus/pci/drivers/ehci_hcd/" and pick all devices id that has names like "0000:00:1a.0". You may have more than one device listed.

```

# ls /sys/bus/pci/drivers/ehci_hcd/
0000:00:1a.0  bind    new_id     uevent
0000:00:1d.0  module  remove_id  unbind

```
I picked "0000:00:1a.0" and "0000:00:1d.0".

Because newer version of Ubuntu came with ehci_hcd builtin kernel, you have to unbind all devices. For this, create a file "/etc/pm/sleep.d/20_custom-ehci_hcd", with the  following content:
```

#!/bin/sh
# File: "/etc/pm/sleep.d/20_custom-ehci_hcd".
case "${1}" in
        hibernate|suspend)
              # Unbind ehci_hcd for first device XXXX:XX:XX.X:
               echo -n "XXXX:XX:XX.X" | tee /sys/bus/pci/drivers/ehci_hcd/unbind
              # Unbind ehci_hcd for second device XXXX:XX:XX.X:
               echo -n "XXXX:XX:XX.X" | tee /sys/bus/pci/drivers/ehci_hcd/unbind
        ;;
        resume|thaw)
              # Bind ehci_hcd for first device XXXX:XX:XX.X:
              echo -n "XXXX:XX:XX.X" | tee /sys/bus/pci/drivers/ehci_hcd/bind
              # Bind ehci_hcd for second device XXXX:XX:XX.X:
              echo -n "XXXX:XX:XX.X" | tee /sys/bus/pci/drivers/ehci_hcd/bind
        ;;
esac

```
**Obs**.: For this work for you, you have to substitue** "XXXX:XX:XX.X"** with your settings.
 
2. Unload modelue xhci (usb3):

Create a file "/etc/pm/config.d/usb3-suspend-workaround", with the  following content:
```

#File: "/etc/pm/config.d/usb3-suspend-workaround".
SUSPEND_MODULES="xhci"

```

Done. Good luck!:P

---

### Post by ipsi on 2010-04-27
Holy crap. That worked! Thanks a lot! That is going to make my life so, so much easier. Thus far everything works as expected after a resume, with the one (very minor!) annoyance that it unmutes my sound, and sets it to the lowest volume. Since I almost never use my work laptop for anything sound-related (not even IM notifications or anything), that's not actually a problem.

The only thing you missed in your instructions is that you need to make the "/etc/pm/sleep.d/20_custom-ehci_hcd" file executable (or, at least, I believe you do - the other files in that directory were), so it would be wise to execute the following command:

```
sudo chmod +x /etc/pm/sleep.d/20_custom-ehci_hcd
```

For others wondering, I just followed steps 1 & 2 in the above post, and everything worked.

---

### Post by stenlee on 2010-05-07
AWESOME !! . thanks man !! ... i can confirm that this solution works also for Asus U30JC.

---

### Post by frioux on 2010-05-08
Works great for me too; don't forget to do the chmod step that ipsi said (Asus w5a here.)

---

### Post by bobbyfiend on 2010-05-29
Just a drive-by FYI: this worked for me, even though I'm not running Ubuntu. I have PCLinuxOS 2010 on an Asus U30jc-A1. I had the same problem, and this solution (word-for-word, substituting my own device values where necessary, but without changing anything else) seems to have worked. Thanks, John Dias (and ipsi)!

---

### Post by Speedwagon on 2010-05-31
I was having the same problems, and followed what is said in this thread.  But, my suspend/hibernate moved on from a USB8 problem, to a new problem.


Now, in my syslog, I get:
```

wl 0000:06:07.0: PCI INT A disabled
pci_legacy_suspend(): wl_suspend+0x0/0x70 [wl] returns -5
pci_pm_suspend+0x0/0xf0 returns -5
Device 0000:06:07.0 failed to suspend: error -5
Some devices failed to suspend
```

After removing the wireless driver(Broadcom STA) and rebooting, it worked just fine.

So I guess I either need to run wired network only, or figure another solution for this driver.  Is there a similar way to just disable the wireless, like the usb?

---

### Post by atroposRandom on 2010-06-11
Your solution worked for my ASUS N61J as well.  Much thanks sir.

---

### Post by Takis on 2010-07-11
And also on a G60JX, though, like Greeble in [this thread]("http://wwww.ubuntuforums.org/showthread.php?t=1434808"), I have a craaaaazy flashing keyboard backlight when the laptop's suspended. Anybody else seen this?

---

### Post by abhijeet_itbhu on 2010-07-13
hi
I have laptop HP dv4 -1241 . I am using ubuntu 10.04 and having problem while suspending and hibernating my laptop . I am a beginner in linux , so someone please guide me in a simple way , how to sort it out

Abhijeet

---

### Post by zero7404 on 2010-07-22
> **nuage6 said:**
> On my HP 8540w I have created the following script 

/etc/pm/sleep.d/05_xhci

The content of this file is
```
#!/bin/sh
# Fix some issues with USB3

if [ "$1" = "suspend" ]
then
        modprobe -r xhci
fi

if [ "$1" = "resume" ]
then
        modprobe xhci
fi

```

chmod 755 /etc/pm/sleep.d/05_xhci

And now I can use my USB3 devices and go in suspend mode.
(Perhaps you need to change the script to hibernate)

Note that I use Lucid, version 10.4 beta 2
Perhaps you'll need to store this file on a folder called suspend.d
Thank you for the tips helping me to understand the issue.

Regards
Gab

i just tried this out for my machine (Envy 17) and it worked, went into suspend/sleep fine. but upon wake up, it was stuck at the screensaver. esc key and mouse click paused/resumed the screensaver, but i couldn't get back in to ubuntu ....

don't know how to fix this ...

---

### Post by kasimir on 2010-08-01
I got suspend to work using John Dias's method (thanks!), but hibernate still doesn't work. Looking at the logs, it just hibernates and then thaws immediately without any reason.

Here is the relevant part of the logs:

[ 1617.111123] ACPI: Preparing to enter system sleep state S4
[ 1617.191752] PM: Saving platform NVS memory
[ 1617.214333] Disabling non-boot CPUs ...
[ 1617.214357] CPU0 attaching NULL sched-domain.
[ 1617.214361] CPU1 attaching NULL sched-domain.
[ 1617.214364] CPU2 attaching NULL sched-domain.
[ 1617.214367] CPU3 attaching NULL sched-domain.
[ 1617.214370] CPU4 attaching NULL sched-domain.
[ 1617.214373] CPU5 attaching NULL sched-domain.
[ 1617.214376] CPU6 attaching NULL sched-domain.
[ 1617.214379] CPU7 attaching NULL sched-domain.
[ 1617.278247] CPU0 attaching NULL sched-domain.
[ 1617.279455] Breaking affinity for irq 25
[ 1617.280575] CPU 1 is now offline
[ 1617.282407] Breaking affinity for irq 26
[ 1617.283516] CPU 2 is now offline
[ 1617.285267] Breaking affinity for irq 27
[ 1617.286380] CPU 3 is now offline
[ 1617.288119] Breaking affinity for irq 28
[ 1617.289217] CPU 4 is now offline
[ 1617.290986] Breaking affinity for irq 12
[ 1617.291013] Breaking affinity for irq 23
[ 1617.292089] CPU 5 is now offline
[ 1617.293578] Breaking affinity for irq 1
[ 1617.293617] Breaking affinity for irq 17
[ 1617.294713] CPU 6 is now offline
[ 1617.296237] Breaking affinity for irq 9
[ 1617.296259] Breaking affinity for irq 16
[ 1617.397336] CPU 7 is now offline
[ 1617.397338] SMP alternatives: switching to UP code
[ 1617.403294] Extended CMOS year: 2000
[ 1617.403381] PM: Creating hibernation image: 
[ 1617.523005] PM: Need to copy 125533 pages
[ 1617.523008] PM: Normal pages needed: 36996 + 1024, available pages: 190642
[ 1617.867600] PM: Hibernation image created (125533 pages copied)
[ 1617.868366] CPU0: Thermal monitoring enabled (TM1)
[ 1617.868431] Extended CMOS year: 2000
[ 1617.868491] Enabling non-boot CPUs ...
[ 1617.868645] SMP alternatives: switching to SMP code
[ 1617.874210] Booting processor 1 APIC 0x2 ip 0x6000
[ 1617.884369] Initializing CPU#1

And then it continues turning on all the CPUs again.

---

### Post by kasimir on 2010-08-03
Found a workaround for my issue: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/612399](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/612399)

---

### Post by brocktice on 2010-08-20
Hi, I  modified this to automatically pull (and save, is that necessary?) the device IDs:

```

#!/bin/sh
# File: "/etc/pm/sleep.d/20_custom-ehci_hcd".
TMPLIST=/tmp/ehci-dev-list

case "${1}" in
        hibernate|suspend)
    echo -n '' > $TMPLIST
          for i in `ls /sys/bus/pci/drivers/ehci_hcd/ | egrep '[0-9a-z]+\:[0-9a-z]+\:.*$'`; do
              # Unbind ehci_hcd for first device XXXX:XX:XX.X:
               echo -n "$i" | tee /sys/bus/pci/drivers/ehci_hcd/unbind
           echo "$i" >> $TMPLIST
          done
        ;;
        resume|thaw)
    for i in `cat $TMPLIST`; do
              # Bind ehci_hcd for first device XXXX:XX:XX.X:
              echo -n "$i" | tee /sys/bus/pci/drivers/ehci_hcd/bind
    done
    rm $TMPLIST
        ;;
esac

```This seems to work fine. Should this be submitted somewhere for inclusion in Ubuntu? Is the tmplist thing ok? Should that be somehow changed?

---

### Post by Flupke on 2010-09-06
Works on U35JC too.

---

### Post by ekips on 2010-09-16
works for Asus U35F

---

### Post by drflan on 2010-09-16
Works on Asus N71JV. Thanks.

---

### Post by lizajane999 on 2010-09-21
**John Dias**' fix with **brocktice**'s mod works perfectly on my brand new N61J!

If you just copy/paste brocktice's mod, don't forget John Dias' step 2., I did at first and thought it wasn't working. 

:)

---

### Post by hedix on 2010-09-22
Cheers for the solution guys! Works like a charm on ASUS N61J.

---

### Post by JustusLibertas on 2010-10-04
OMG! Thank you so much! This nearly completes my transition to Linux permanently. FREE FROM WINDOWS!! 15 years I've been wishing for the day I could completely work on Linux. Thanks to WINE All the Adobe CS4 apps I need work.

John Dias' scripts worked for me on my Asus U50F-RBBAG05 Intel i3 laptop! I can now suspend Linux Mint. So, I don't have to use Windows when I'm on the run.

The only other bug I'm experiencing with Linux is that my speakers don't mute when I plug in my headphones. But, I'm sure the fix is out there or on the verge. This was the last worst thing I needed to fix.

Thank you again Ubuntu Community John Dias and ipsi!

\\:D/=D> You all ROCK!! :guitar:

---

### Post by CheBuzz on 2010-10-12
Also confirm that this worked for me.

And I also can confirm that the keyboard backlight is blinking in some random pattern for me during suspend.  I have an Asus G51J

---

### Post by molecula21 on 2010-10-18
Works like a charm on my U30JC. Thank you all!

---

### Post by mohammedsk on 2010-11-06
Thank you, it worked on ASUS G73JH, but after resume the USB ports are disabled. How can I enable them?

---

### Post by skullnerd on 2010-11-07
Works on the G51J as well.

Also in regards to this:

> **Takis said:**
> And also on a G60JX, though, like Greeble in [this thread]("http://wwww.ubuntuforums.org/showthread.php?t=1434808"), I have a craaaaazy flashing keyboard backlight when the laptop's suspended. Anybody else seen this?

Maybe something similar to [this post]("http://ubuntuforums.org/showthread.php?t=1546748") can help, because it worked on the 51.

---

### Post by WIGGMPk on 2010-11-12
Confirmed working for the ASUS G51J (Non-3D & Non-Backlight LED Keyboard)

However, in addition to this:

```
sudo chmod +x /etc/pm/sleep.d/20_custom-ehci_hcd
```

I also need to do this:

```
sudo chmod 755 /etc/pm/sleep.d/20_custom-ehci_hcd
```

Thank you for finally solving my suspend issues..

---

### Post by SalsaDoom on 2010-11-19
Anyone got this trick to work on 10.10? Looks like its been re-broken better than ever.

---

### Post by skullnerd on 2010-11-19
Yup, mine works in 10.10.  That's the first one I tried it on.

---

### Post by SalsaDoom on 2010-11-19
Hmmmm, thats odd. Even with this fix I get the exact same issue I had previous to 10.10. I wonder why this isn't working for me. I'm on a G73jh, but the fix did work until now like a charm. Bummer.

---

### Post by SalsaDoom on 2010-11-19
Whoops. So my bad. I had a few commands in the file that I had meant for another terminal :) tee hee! Nevermind ;) I read it twenty times but "cd" in the middle of the file somehow went unnoticed.

---

### Post by Todd S. on 2010-11-20
/bump

Just added this script to my system and it works perfectly! Thanks so much.

Asus K52
Kubuntu 10.10

---

### Post by XRayA4T on 2010-11-25
Worked on my Gigabyte T1005 with a small change. I needed to unbind the usb in /sys/bus/pci/drivers/xhci_hcd/ and obviously replace all ehci with xhci in 20_custom-xhci_hcd.

---

### Post by OskarV on 2010-11-26
This solution works with some modifications on my new Asus N43JF with USB3.0

What worked was I had to make a
/etc/pm/sleep.d/20_custom-ehci_hc
for the ehci devices per John Dias's description
and a seperate (maybe not neccesary)
/etc/pm/sleep.d/20_custom-xhci_hc
for my xhci devices (wich have different addresses then the ehci)

to fix the problem.... 

the /etc/pm/config.d/usb3-suspend-workaround file did not solve the problem for me so I skipped it.

---

### Post by bdoe on 2010-11-29
> **SalsaDoom said:**
> Anyone got this trick to work on 10.10? Looks like its been re-broken better than ever.
Broken for me as well...

Asus G73JH
Ubuntu 10.10 w/ PAE kernel

I can successfully suspend once. If I try to suspend again, it won't properly wake back up. Hibernation is a complete no-go. It launches my screensaver and then hangs.

---

### Post by Sosume on 2010-12-04
Also had to disable xhci like OskarV proposed. Now works on N71JQ.

> **OskarV said:**
> This solution works with some modifications on my new Asus N43JF with USB3.0

What worked was I had to make a
/etc/pm/sleep.d/20_custom-ehci_hc
for the ehci devices per John Dias's description
and a seperate (maybe not neccesary)
/etc/pm/sleep.d/20_custom-xhci_hc
for my xhci devices (wich have different addresses then the ehci)


---

### Post by ogrim on 2010-12-04
Also worked with N73JF. I had to disable both ehci and xhci.

---

### Post by enzyme on 2010-12-06
Works like a charm on Vaio VPCF1, Unbuntu 10.04.1 LTS, kernel 2.6.32.26.

This was a lot of help. Thanks!

---

### Post by nickbrett on 2010-12-07
Thanks, this fix works on my Asus U35jc

---

### Post by Mechabuntu on 2010-12-08
Great. I tried several proposed solutions for suspend freezes, but none worked. This one is the solution for me on Asus laptop X52J (I did not find any thread on this model).

Thanks Brocktice, and John Dias for automatic device list (this is the script I use).

Ubuntu 10.10     2.6.35-23-generic-pae    Asus X52J

---

### Post by kawfey on 2010-12-15
Suspend solution works for me with a Asus G60J, but i also get the keyboard backlight flickering problem. If i turn the backlight off before suspending it doesn't do this, so that's all right. I still have a problem with hibernation, as in it basically locks the computer prompting for my password.

---

### Post by marcb_ro on 2010-12-23
I can confirm this fix is working on my ASUS U52F. Thank you very much, you guys are real life-savers.

---

### Post by nakednous on 2011-01-04
Works great for me too. Thanks (asus N53J)

---

### Post by cuchito2001 on 2011-01-15
thks John Dias, ipsi, brocktice and XRayA4T -> (unbind the usb in /sys/bus/pci/drivers/xhci_hcd/).

Works Great on 10.10 x64 Asus N61j

My Script:

```
#!/bin/sh
# File: "/etc/pm/sleep.d/20_custom-ehci_hcd".
case "${1}" in
        hibernate|suspend)
              # Unbind ehci_hcd for first device 0000:00:1a.0:
               echo -n "0000:00:1a.0" | tee /sys/bus/pci/drivers/ehci_hcd/unbind
              # Unbind ehci_hcd for second device 0000:00:1d.0:
               echo -n "0000:00:1d.0" | tee /sys/bus/pci/drivers/ehci_hcd/unbind
          # Unbind xhci_hcd for third device 0000:07:00.0:
           echo -n "0000:07:00.0" | tee /sys/bus/pci/drivers/xhci_hcd/unbind
        ;;
        resume|thaw)
              # Bind ehci_hcd for first device 0000:00:1a.0:
              echo -n "0000:00:1a.0" | tee /sys/bus/pci/drivers/ehci_hcd/bind
              # Bind ehci_hcd for second device 0000:00:1d.0:
              echo -n "0000:00:1d.0" | tee /sys/bus/pci/drivers/ehci_hcd/bind
          # Bind xhci_hcd for third device 0000:07:00.0:
          echo -n "0000:07:00.0" | tee /sys/bus/pci/drivers/xhci_hcd/bind    
        ;;
esac
```

---

### Post by codecentral on 2011-01-18
Here's another script based on the scripts posted on this thread. It auto pulls the addresses from EHCI and XHCI:

[http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug](http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug)

Hope it will help someone.

---

### Post by Grayside on 2011-01-23
Asus N61JQ-XV1 needs both the ehci and xhci modifications. Blog post looks excellent if you need both, saw it right after I put individual scripts in place.

---

### Post by zero7404 on 2011-01-25
i was wondering if someone can help me i'm having trouble getting my system to suspend. i have an HP envy 17-1010NR, core i7, usb3, ATI 5850 graphics, broadcom wifi. not sure of what hardware in particular is failing to suspend, but it's listed in the syslog. here is the output from dmesg, i cleared the syslog before i printed, so all of below starts with the suspend request:

> [15807.625719] EXT4-fs (sda6): re-mounted. Opts: commit=0
[15808.342979] ehci_hcd 0000:00:1a.0: remove, state 4
[15808.342991] usb usb1: USB disconnect, address 1
[15808.342996] usb 1-1: USB disconnect, address 2
[15808.347299] ehci_hcd 0000:00:1a.0: USB bus 1 deregistered
[15808.347826] ehci_hcd 0000:00:1a.0: PCI INT A disabled
[15808.349266] ehci_hcd 0000:00:1d.0: remove, state 1
[15808.349278] usb usb2: USB disconnect, address 1
[15808.349282] usb 2-1: USB disconnect, address 2
[15808.349286] usb 2-1.5: USB disconnect, address 3
[15808.421128] ehci_hcd 0000:00:1d.0: USB bus 2 deregistered
[15808.421230] ehci_hcd 0000:00:1d.0: PCI INT A disabled
[15811.579940] PM: Syncing filesystems ... done.
[15811.583760] PM: Preparing system for mem sleep
[15811.583946] Freezing user space processes ... (elapsed 0.01 seconds) done.
[15811.602897] Freezing remaining freezable tasks ... (elapsed 0.01 seconds) done.
[15811.621688] PM: Entering mem sleep
[15811.621793] Suspending console(s) (use no_console_suspend to debug)
[15811.622467] sd 4:0:0:0: [sdb] Synchronizing SCSI cache
[15811.622748] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[15811.622751] sd 4:0:0:0: [sdb] Stopping disk
[15811.622847] sd 0:0:0:0: [sda] Stopping disk
[15811.627519] pm_op(): usb_dev_suspend+0x0/0x20 returns -32
[15811.627523] PM: Device 3-3 failed to suspend async: error -32
[15812.621436] PM: suspend of drv:sd dev:4:0:0:0 complete after 999.327 msecs
[15812.621583] PM: Some devices failed to suspend
[15812.621657] sd 0:0:0:0: [sda] Starting disk
[15812.621665] sd 4:0:0:0: [sdb] Starting disk
[15813.629684] PM: resume of drv:sd dev:4:0:0:0 complete after 1008.875 msecs
[15813.629704] PM: resume of drv:scsi_device dev:4:0:0:0 complete after 1008.663 msecs
[15813.629818] PM: resume of drv:scsi_disk dev:4:0:0:0 complete after 1006.665 msecs
[15813.636035] PM: resume of devices complete after 1015.311 msecs
[15813.636120] PM: resume devices took 1.010 seconds
[15813.636129] PM: Finishing wakeup.
[15813.636131] Restarting tasks ... done.
[15813.637071] video LNXVIDEO:01: Restoring backlight state
[15813.753687] r8169 0000:03:00.0: eth0: link down
[15813.754472] ADDRCONF(NETDEV_UP): eth0: link is not ready
[15813.760313] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[15813.760375] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[15813.760385] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[15813.760490] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[15813.760563] ehci_hcd 0000:00:1a.0: debug port 2
[15813.764483] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[15813.764529] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xd610a000
[15813.784111] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[15813.784337] hub 1-0:1.0: USB hub found
[15813.784347] hub 1-0:1.0: 3 ports detected
[15813.786072] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[15813.786120] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[15813.786131] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[15813.786220] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[15813.786292] ehci_hcd 0000:00:1d.0: debug port 2
[15813.790199] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[15813.790227] ehci_hcd 0000:00:1d.0: irq 21, io mem 0xd6109000
[15813.804655] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[15813.805047] hub 2-0:1.0: USB hub found
[15813.805057] hub 2-0:1.0: 3 ports detected
[15814.099929] usb 1-1: new high speed USB device using ehci_hcd and address 2
[15814.165159] EXT4-fs (sda6): re-mounted. Opts: commit=0
[15814.250800] hub 1-1:1.0: USB hub found
[15814.250968] hub 1-1:1.0: 6 ports detected
[15814.369732] usb 2-1: new high speed USB device using ehci_hcd and address 2
[15814.520402] hub 2-1:1.0: USB hub found
[15814.520528] hub 2-1:1.0: 8 ports detected
[15814.802670] usb 2-1.5: new high speed USB device using ehci_hcd and address 3
[15814.971272] uvcvideo: Found UVC 1.00 device HP ENVY HD Webcam (0408:1af1)
[15814.979721] input: HP ENVY HD Webcam as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.0/input/input14
[15823.765511] eth1: no IPv6 routers present

---

### Post by zero7404 on 2011-01-25
update:
i've been trying some scripts i dug up on the internet but nothing worked. i found myself on the following page, decided to give it a shot and it finally worked:

[http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug](http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug)

i now feel safe enough to clone my ubuntu installation seeing that i've got everything i want working configured.

---

### Post by gufide on 2011-02-06
work for me. Asus G60Jx-RBBX05

---

### Post by irv on 2011-02-06
I have a Dell Inspiron 1521, the suspend works, but when it go into hibernation it does not come out, so I thought I would try this script. It didn't work for me, in fact it made it worst. Suspend and hibernate both would not come back up. I had to force a restart. I deleted the scrip and all is back the way it was. It looks like my problem is something else. I am glad it help with the Asus.

---

### Post by TheUnwiseman on 2011-02-15
Excellent!  Worked for my ASUS X52J.  Thanks a lot!

---

### Post by castelinop on 2011-02-18
Thanks a lot [John Dias]("http://art.ubuntuforums.org/member.php?u=999407"), the solution provided worked on my Dell Inspiron 1545.

---

### Post by jamezelle on 2011-02-24
> **zero7404 said:**
> update:
i've been trying some scripts i dug up on the internet but nothing worked. i found myself on the following page, decided to give it a shot and it finally worked:

[http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug](http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug)

i now feel safe enough to clone my ubuntu installation seeing that i've got everything i want working configured.

thanks for the link to the thread, i was about to give up :)

---

### Post by helland71 on 2011-02-26
Works on U41J. Thanks.

---

### Post by suxen on 2011-03-06
> **codecentral said:**
> Here's another script based on the scripts posted on this thread. It auto pulls the addresses from EHCI and XHCI:

[http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug](http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug)

Hope it will help someone.

Yep, this did the trick for me( on asus u45jc, xubuntu 10.10). Using the "John Dias' + brocktice" original method worked as far as suspend is concerned. However, after resuming, my external usb devices (mouse, usb thumb drive) were no longer recognized by the system. I also removed the /etc/pm/config.d/usb3-suspend-workaround script from step 2. in John Dias prescription.

Thanks!

---

### Post by anjexe on 2011-03-06
i am confused please help me in clear way for my asus n43jf

---

### Post by anjexe on 2011-03-07
> **anjexe said:**
> i am confused please help me in clear way for my asus n43jf

i do so it works ;)

goto patch 
/etc/pm/sleep.d/

create document named : 20_custom-ehci_hcd

then as [http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug](http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug)

Insert the following code into the file i have just created:
    #!/bin/sh  TMPLIST_E=/tmp/ehci-dev-list TMPLIST_X=/tmp/xhci-dev-list E_DIR=/sys/bus/pci/drivers/ehci_hcd X_DIR=/sys/bus/pci/drivers/xhci_hcd E_BIND=$E_DIR""/bind E_UNBIND=$E_DIR""/unbind X_BIND=$X_DIR""/bind X_UNBIND=$X_DIR""/unbind   #param1 = temp file, param2 = device dir, param3 = unbind  unbindDev (){ #inspired by [http://art.ubuntuforums.org/showpost.php?p=9744970&postcount=19](http://art.ubuntuforums.org/showpost.php?p=9744970&postcount=19)       echo -n '' > $1     for i in `ls $2 | egrep '[0-9a-z]+\:[0-9a-z]+\:.*$'`; do       echo -n "$i" | tee $3       echo "$i" >> $1   done }  #param1 = tem file, param2 = bind bindDev(){   [ -f $1 ] || return      for i in `cat $1`; do     echo -n "$i" | tee $2    done   rm $1 }   case "${1}" in   hibernate|suspend)     unbindDev $TMPLIST_E $E_DIR $E_UNBIND     unbindDev $TMPLIST_X $X_DIR $X_UNBIND         ;;   resume|thaw)     bindDev $TMPLIST_E $E_BIND     bindDev $TMPLIST_X $X_BIND         ;; esac

and

dd executable permission:    sudo chmod 755 /etc/pm/sleep.d/20_custom-ehci_hcd

:popcorn:


tnx all

---

### Post by vall on 2011-03-24
I have a Sonny Vaio SR49VN. In my case, the laptop would not suspend only occasionally. I tried the solution posted here, but yet, simetimes I can suspend, sometimes not. Anyone has an idea what else I can try?

---

### Post by Aang_Aero on 2011-04-22
Confirmed:  The solution listed in posts **#7** & **#8** fixed [my hibernate/suspend issues]("http://ubuntuforums.org/showthread.php?t=1727721")! :P

Asus G73JW-A1
Ubuntu 10.04.2 64-bit

---

### Post by amgreenhawk on 2011-04-24
Just wanted to confirm that this workaround IS working in my system. (Both the steps outlined in posts #7 and #8  are required.)

Using Asus G73jh-1A. Ubuntu 10.10. 

Thanks!

---

### Post by hamidrjafari on 2011-04-25
It works on Asus U31F also! Great. Just that it doesn't come back by pressing a keyboard key, but it comes back by pressing laptop's power button and it is enough for me.

Thanks.

---

### Post by miceagol on 2011-05-03
I hereby confirm that [this suspend fix]("http://ubuntuforums.org/showpost.php?p=9180298&postcount=7") worked on Asus U31JG too. Thanks a lot! This has been bugging me for months. :D

PS: Also utilized the [follow-up post]("http://ubuntuforums.org/showpost.php?p=9180693&postcount=8") and did a reboot.

---

### Post by finishman on 2011-05-20
Hello

All methods worked for my Asus P42Jc for suspend...but I still cannot hibernate it...could someone help me?

---

### Post by oscariommi on 2011-06-21
Yeah! Helped my ASUS A73E with Ubuntu 11.04 PAE 32bit also! Great thanks!!!

---

### Post by bdoe on 2011-06-22
> **finishman said:**
> Hello

All methods worked for my Asus P42Jc for suspend...but I still cannot hibernate it...could someone help me?

If you can suspend but not hibernate, then you might not have enough swap space. Your swap partition needs to be at least as large as the amount of memory your computer has. I like to set my swap partition to be 1GB larger than my system memory, so for my laptop with 6GB of RAM, I set my swap to 7GB. It's probably overkill, but virtually assures that my hibernations don't fail due to lack of swap.

---

### Post by bogianen on 2011-06-24
Great Job! After a long time made of researches and vain attempts, thanks to the solutions posted at the #7 and #8 of this thread, now I am able to suspend and hibernate my PC.
At present I have a Gigabyte GA-790FXTA-UD5 motherboard and a Nvidia GeForce 7950 GT as a graphics card, with Kubuntu 11.04 and the solution here proposed works very well, but I believe that it could work with my old hardware too, a dead Asus A8N32-SLI Deluxe motherboard.

---

### Post by TiMBuS on 2011-07-09
Oh man I was about to go back to windows because there's no point in a new laptop that can't suspend. and bam. this thread solved it! the fix only took two minutes too. Why the hell isnt this being pushed out as an update? 
( answer: because it's ubuntu... =[ )

Asus X53E, if you were wondering.

Now to get the hardware multitouch working (hah)

---

### Post by tijs14tijs on 2011-07-26
Thank you all for supporting this thread, you just fixed a minor issue on my Asus K53S without knowing :P

---

### Post by supadid on 2011-08-11
Confirmed as working on ASUS P52F.

Thanks a lot! :)

---

### Post by nixahn on 2011-08-12
in my Asus g60j, the keyboard was flashing all the time after suspending. I found [[COLOR="Blue"]this[/COLOR]]("http://forum.notebookreview.com/linux-compatibility-software/451594-asus-rog-g73-ubuntu.html") thread that helped me modify my script to account for the problem;

```

#!/bin/sh
# File: "/etc/pm/sleep.d/20_custom-ehci_hcd".
# sudo gedit /etc/pm/sleep.d/20_custom-ehci_hcd
case "${1}" in
        hibernate|suspend)
              # Unbind ehci_hcd for first device 0000:00:1a.0:
               echo -n "0000:00:1a.0" | tee /sys/bus/pci/drivers/ehci_hcd/unbind
              # Unbind ehci_hcd for second device 0000:00:1d.0:
               echo -n "0000:00:1d.0" | tee /sys/bus/pci/drivers/ehci_hcd/unbind
              # sudo sh -c "echo 0 > /sys/class/leds/asus\:\:kbd_backlight/brightness"
              echo 0 > /sys/class/leds/asus\:\:kbd_backlight/brightness
        ;;
        resume|thaw)
              # Bind ehci_hcd for first device 0000:00:1a.0:
              echo -n "0000:00:1a.0" | tee /sys/bus/pci/drivers/ehci_hcd/bind
              # Bind ehci_hcd for second device 0000:00:1d.0:
              echo -n "0000:00:1d.0" | tee /sys/bus/pci/drivers/ehci_hcd/bind
              # sudo sh -c "echo 1 > /sys/class/leds/asus\:\:kbd_backlight/brightness"
              echo 1 > /sys/class/leds/asus\:\:kbd_backlight/brightness
        ;;
esac
# sudo chmod +x /etc/pm/sleep.d/20_custom-ehci_hcd

```

---

### Post by Jary316 on 2011-08-14
Thank you guys so much!

I have an Asus N61J and I am running Ubuntu 11.04 and I could not get hibernate to work at all.

This solution fixed it! Kudos to you guys! I hope this script gets included in the next release.

Thanks a lot.

---

### Post by frls89 on 2011-09-10
> **John Dias said:**
> Hi [ipsi]("http://art.ubuntuforums.org/member.php?u=285138"),
I'm Brazilian, so my english....
I have the same problem of you with an Asus n71Jq-x1. I'm pretty sure you're succeed like me. I try with this versions of Ubuntu, and all worked fine:

    * Ubuntu 9.10 64bits
    * Ubuntu 10.4 R3 64bits
    * Ubuntu Studio 10.4 R3 64bits

The problem is about the ehci builtin controller and xhci module.
The better solutions is to disable all devices that uses ehci_hcd from Kernel, and to unload module xhci, before suspend/hibernate. For the last, you can use the nuage6's solution, but I prefer to use the "config.d", as I describe in section 2. Another solution is to complete disable usb support in BIOS, but I guess you don't need to do this.

1. Unbind ehci_hcd from kernel:

First, verify what devices you need to unload from kernel. Simple list the directory "/sys/bus/pci/drivers/ehci_hcd/" and pick all devices id that has names like "0000:00:1a.0". You may have more than one device listed.

```

# ls /sys/bus/pci/drivers/ehci_hcd/
0000:00:1a.0  bind    new_id     uevent
0000:00:1d.0  module  remove_id  unbind

```
I picked "0000:00:1a.0" and "0000:00:1d.0".

Because newer version of Ubuntu came with ehci_hcd builtin kernel, you have to unbind all devices. For this, create a file "/etc/pm/sleep.d/20_custom-ehci_hcd", with the  following content:
```

#!/bin/sh
# File: "/etc/pm/sleep.d/20_custom-ehci_hcd".
case "${1}" in
        hibernate|suspend)
              # Unbind ehci_hcd for first device XXXX:XX:XX.X:
               echo -n "XXXX:XX:XX.X" | tee /sys/bus/pci/drivers/ehci_hcd/unbind
              # Unbind ehci_hcd for second device XXXX:XX:XX.X:
               echo -n "XXXX:XX:XX.X" | tee /sys/bus/pci/drivers/ehci_hcd/unbind
        ;;
        resume|thaw)
              # Bind ehci_hcd for first device XXXX:XX:XX.X:
              echo -n "XXXX:XX:XX.X" | tee /sys/bus/pci/drivers/ehci_hcd/bind
              # Bind ehci_hcd for second device XXXX:XX:XX.X:
              echo -n "XXXX:XX:XX.X" | tee /sys/bus/pci/drivers/ehci_hcd/bind
        ;;
esac

```
**Obs**.: For this work for you, you have to substitue** "XXXX:XX:XX.X"** with your settings.
 
2. Unload modelue xhci (usb3):

Create a file "/etc/pm/config.d/usb3-suspend-workaround", with the  following content:
```

#File: "/etc/pm/config.d/usb3-suspend-workaround".
SUSPEND_MODULES="xhci"

```

Done. Good luck!:P
Thanks you very much [John Dias]("http://ubuntuforums.org/member.php?u=999407") ;)
you instruction works great

---

### Post by gillza on 2011-10-05
Instructions in #7 and #8 worked for Asus G53SX-A1.

Thank you both authors!

---

### Post by mashutin on 2011-10-08
Hi all! I have notebook Asus A52F, lspci:
```
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 18)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 06)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
04:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 80)
04:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 80)
04:00.3 System peripheral: JMicron Technology Corp. MS Host Controller (rev 80)
04:00.4 System peripheral: JMicron Technology Corp. xD Host Controller (rev 80)
04:00.5 Ethernet controller: JMicron Technology Corp. JMC250 PCI Express Gigabit Ethernet Controller (rev 03)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05)

```
And I have Fedora15.1 (Russian Remix). I can't to solve my problem on forum.russianfedora.ru. And I wrote here. I have next problem: my notebook did not go away in hibernate and suspend. I found script here [http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug](http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug). Now if from root in terminal: pm-hibernate or pm-suspend, then all works. If to hibernate or suspend touch button off or closed display, then after resume I see error "kernel:[ 5294.754133] Disabling IRQ #17" and not works WiFi. Help me, please! How to fix error? Thanks.
/var/log/pm-suspend.log
```
Initial commandline parameters:
Sat Oct  8 12:16:02 MSK 2011: Running hooks for suspend.
Running hook /usr/lib64/pm-utils/sleep.d/00logging suspend suspend:
Linux asusnb 2.6.40.4-5.fc15.x86_64 #1 SMP Tue Aug 30 14:38:32 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
fuse                   62381  3
sunrpc                200079  1
cpufreq_ondemand        5934  4
acpi_cpufreq            9536  1
mperf                   1449  1 acpi_cpufreq
bnep                   14635  2
bluetooth             191587  7 bnep
nf_conntrack_ipv4       8358  2
nf_defrag_ipv4          1513  1 nf_conntrack_ipv4
xt_state                1306  2
nf_conntrack           67613  2 nf_conntrack_ipv4,xt_state
microcode              18587  0
joydev                  9615  0
serio_raw               4414  0
snd_hda_codec_hdmi     22499  1
snd_hda_codec_conexant    54661  1
arc4                    1417  2
intel_ips              11358  0
i2c_i801                9237  0
uvcvideo               57089  0
videodev               72104  1 uvcvideo
media                  11611  2 uvcvideo,videodev
v4l2_compat_ioctl32     7377  1 videodev
snd_hda_intel          23896  2
snd_hda_codec          82508  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               6328  1 snd_hda_codec
snd_seq                52322  0
snd_seq_device          5941  1 snd_seq
snd_pcm                78424  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
iTCO_wdt               13000  0
iTCO_vendor_support     2578  1 iTCO_wdt
asus_laptop            14561  0
sparse_keymap           3358  1 asus_laptop
jme                    27089  0
ath9k                  98147  0
mii                     4335  1 jme
mac80211              247332  1 ath9k
ath9k_common            2496  1 ath9k
ath9k_hw              271229  2 ath9k,ath9k_common
ath                    15098  2 ath9k,ath9k_hw
snd_timer              19372  2 snd_seq,snd_pcm
jmb38x_ms              11158  0
cfg80211              148129  3 ath9k,mac80211,ath
snd                    63380  13 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_seq,snd_seq_device,snd_pcm,snd_timer
soundcore               6267  1 snd
snd_page_alloc          7343  2 snd_hda_intel,snd_pcm
memstick                8883  1 jmb38x_ms
rfkill                 16436  5 bluetooth,asus_laptop,cfg80211
sdhci_pci               8849  0
sdhci                  22752  1 sdhci_pci
mmc_core               76665  1 sdhci
i915                  378728  8
drm_kms_helper         26474  1 i915
drm                   193923  4 i915,drm_kms_helper
i2c_algo_bit            4974  1 i915
i2c_core               25712  6 i2c_i801,videodev,i915,drm_kms_helper,drm,i2c_algo_bit
video                  12340  1 i915
             total       used       free     shared    buffers     cached
Mem:       2934172    1589740    1344432          0      39292     509872
-/+ buffers/cache:    1040576    1893596
Swap:      3071996          0    3071996

/usr/lib64/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib64/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib64/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib64/pm-utils/sleep.d/01grub suspend suspend:

/usr/lib64/pm-utils/sleep.d/01grub suspend suspend: success.
Running hook /etc/pm/sleep.d/20_custom-ehci_hcd suspend suspend:

/etc/pm/sleep.d/20_custom-ehci_hcd suspend suspend: success.
Running hook /usr/lib64/pm-utils/sleep.d/49bluetooth suspend suspend:

/usr/lib64/pm-utils/sleep.d/49bluetooth suspend suspend: success.
Running hook /usr/lib64/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Done.

/usr/lib64/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib64/pm-utils/sleep.d/56atd suspend suspend:

/usr/lib64/pm-utils/sleep.d/56atd suspend suspend: success.
Running hook /usr/lib64/pm-utils/sleep.d/56dhclient suspend suspend:

/usr/lib64/pm-utils/sleep.d/56dhclient suspend suspend: success.
Running hook /usr/lib64/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib64/pm-utils/sleep.d/75modules suspend suspend: success.
Running hook /usr/lib64/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib64/pm-utils/sleep.d/90clock suspend suspend: success.
Running hook /usr/lib64/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib64/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib64/pm-utils/sleep.d/95led suspend suspend:

/usr/lib64/pm-utils/sleep.d/95led suspend suspend: success.
Running hook /usr/lib64/pm-utils/sleep.d/95packagekit suspend suspend:

/usr/lib64/pm-utils/sleep.d/95packagekit suspend suspend: success.
Running hook /usr/lib64/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.

/usr/lib64/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib64/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib64/pm-utils/sleep.d/99video suspend suspend: success.
Sat Oct  8 12:16:02 MSK 2011: performing suspend
Sat Oct  8 12:16:14 MSK 2011: Awake.
Sat Oct  8 12:16:14 MSK 2011: Running hooks for resume
Running hook /usr/lib64/pm-utils/sleep.d/99video resume suspend:

/usr/lib64/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib64/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib64/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib64/pm-utils/sleep.d/95packagekit resume suspend:
method return sender=:1.87 -> dest=:1.86 reply_serial=2

/usr/lib64/pm-utils/sleep.d/95packagekit resume suspend: success.
Running hook /usr/lib64/pm-utils/sleep.d/95led resume suspend:

/usr/lib64/pm-utils/sleep.d/95led resume suspend: success.
Running hook /usr/lib64/pm-utils/sleep.d/94cpufreq resume suspend:

/usr/lib64/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib64/pm-utils/sleep.d/90clock resume suspend:

/usr/lib64/pm-utils/sleep.d/90clock resume suspend: success.
Running hook /usr/lib64/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.

/usr/lib64/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib64/pm-utils/sleep.d/56dhclient resume suspend:

/usr/lib64/pm-utils/sleep.d/56dhclient resume suspend: success.
Running hook /usr/lib64/pm-utils/sleep.d/56atd resume suspend:
Restarting atd (via systemctl):  [  OK  ]

/usr/lib64/pm-utils/sleep.d/56atd resume suspend: success.
Running hook /usr/lib64/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...Done.

/usr/lib64/pm-utils/sleep.d/55NetworkManager resume suspend: success.
Running hook /usr/lib64/pm-utils/sleep.d/49bluetooth resume suspend:

/usr/lib64/pm-utils/sleep.d/49bluetooth resume suspend: success.
Running hook /etc/pm/sleep.d/20_custom-ehci_hcd resume suspend:

/etc/pm/sleep.d/20_custom-ehci_hcd resume suspend: success.
Running hook /usr/lib64/pm-utils/sleep.d/01grub resume suspend:

/usr/lib64/pm-utils/sleep.d/01grub resume suspend: success.
Running hook /usr/lib64/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib64/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib64/pm-utils/sleep.d/00logging resume suspend:

/usr/lib64/pm-utils/sleep.d/00logging resume suspend: success.
Sat Oct  8 12:16:14 MSK 2011: Finished.

```

---

### Post by mashutin on 2011-10-09
Maybe I found solve. I added to kernel option "noirqdebug" and system resumed ok.

---

### Post by Thucydides411 on 2011-10-15
I confirm that solution #1 given in post #7, with the extra "chmod +x" command given in post #8, works for the Asus G53Jw. Make sure to use only solution #1, as solution #1 does not work in combination with solution #2. The only problem now is that the screen sometimes takes a long time to turn back on.

---

### Post by Jary316 on 2011-10-20
> **Thucydides411 said:**
> I confirm that solution #1 given in post #7, with the extra "chmod +x" command given in post #8, works for the Asus G53Jw. Make sure to use only solution #1, as solution #1 does not work in combination with solution #2. The only problem now is that the screen sometimes takes a long time to turn back on.

This solution used to work great on my Asus N61J with Ubuntu 11.04. I did an upgrade to Ubuntu 11.10 and since then, the problem is back.

Does this solution still works for people with Ubuntu 11.10 please or has it become obsolete for everyone else please?

Thank you.

---

### Post by Jary316 on 2011-10-21
> **Jary316 said:**
> This solution used to work great on my Asus N61J with Ubuntu 11.04. I did an upgrade to Ubuntu 11.10 and since then, the problem is back.

Does this solution still works for people with Ubuntu 11.10 please or has it become obsolete for everyone else please?

Thank you.

I have redone the steps with Ubuntu 11.10 and the solution now  works again! It may have been also because of some recent Ubuntu updates, or people who update from 11.04 to 11.10 may simple have to delete the files and repeat the steps, but it still works.

---

### Post by Jary316 on 2011-10-23
> **Jary316 said:**
> I have redone the steps with Ubuntu 11.10 and the solution now  works again! It may have been also because of some recent Ubuntu updates, or people who update from 11.04 to 11.10 may simple have to delete the files and repeat the steps, but it still works.

Actually (sorry for posting again), it sometimes does not work. The computer doesn't always go in hibernate, it sometimes just stays at a dark screen and I can only power it off. It seems to be about 50/50 but I have not run much tests.

---

### Post by snovik on 2011-10-23
Great solution. However in my case it works only for hibernate. "Suspend" does suspend but can not wake up. The laptop starts, hard disk lights for about 5 sec and then nothing happens. Hard reset starts a new boot.

ASUS X51R. Ubuntu 11.10

---

### Post by tredsyn on 2011-10-25
> **snovik said:**
> Great solution. However in my case it works only for hibernate. "Suspend" does suspend but can not wake up. The laptop starts, hard disk lights for about 5 sec and then nothing happens. Hard reset starts a new boot.


Same here. I'm not on an Asus laptop though, I'm using ECS 223. But I'm glad hibernate is now working.

---

### Post by asus-user on 2011-11-09
I am asus U30Jc user and I tested both: sleep and hibernate after applying this solution, and they worked fine.

Thanks guys  :)

---

### Post by alextacy on 2011-11-10
Hey all, I am having the same problems (again with an ASUS).

I know this is a bit dumb... but when i "create the file" in John Dias' solution... where do i save this file?!  

Sorry, still learning the ropes despite using ubuntu for a while... its all been working pretty well up till now on my old Dell... change machines & have a dual boot with windows & running into some problems, this being one of them.

I think there may be a few others out there that could do with a walk through as well!

If I find one I will post it up!

Ta

---

### Post by richbl on 2011-11-13
All,

Just a quick note that I was able to get suspend/hibernate to work with an ASUS N75SF.

[B]The solution for me was to use message #19 and message #7 (step #2). 
[/B]
Note that I'm also running the ironhide solution for managing Optimus drivers, so this may be part of the solution set.

In any case, thanks to these two posters for getting me up to speed in Ubuntu 11.10.

Rich

---

### Post by vdnick on 2011-12-13
Great work! Thank you!

U35JC work fine with this solution on LinuxMint12, ironhide - optimus enabled. 


> **brocktice said:**
> Hi, I  modified this to automatically pull (and save, is that necessary?) the device IDs:

```

#!/bin/sh
# File: "/etc/pm/sleep.d/20_custom-ehci_hcd".
TMPLIST=/tmp/ehci-dev-list

case "${1}" in
        hibernate|suspend)
    echo -n '' > $TMPLIST
          for i in `ls /sys/bus/pci/drivers/ehci_hcd/ | egrep '[0-9a-z]+\:[0-9a-z]+\:.*$'`; do
              # Unbind ehci_hcd for first device XXXX:XX:XX.X:
               echo -n "$i" | tee /sys/bus/pci/drivers/ehci_hcd/unbind
           echo "$i" >> $TMPLIST
          done
        ;;
        resume|thaw)
    for i in `cat $TMPLIST`; do
              # Bind ehci_hcd for first device XXXX:XX:XX.X:
              echo -n "$i" | tee /sys/bus/pci/drivers/ehci_hcd/bind
    done
    rm $TMPLIST
        ;;
esac

```This seems to work fine. Should this be submitted somewhere for inclusion in Ubuntu? Is the tmplist thing ok? Should that be somehow changed?

---

### Post by Nullifi3d on 2012-04-19
Confirmed that this works with Asus U50F. Don't forget the chmod.

---

### Post by tuiger on 2012-04-29
works great on the ASUS K52J  :P

> #!/bin/sh
# File: "/etc/pm/sleep.d/20_custom-ehci_hcd".
case "${1}" in
        hibernate|suspend)
              # Unbind ehci_hcd for first device 0000:00:1a.0:
               echo -n "0000:00:1a.0" | tee /sys/bus/pci/drivers/ehci_hcd/unbind
              # Unbind ehci_hcd for second device 0000:00:1d.0:
               echo -n "0000:00:1d.0" | tee /sys/bus/pci/drivers/ehci_hcd/unbind
        ;;
        resume|thaw)
              # Bind ehci_hcd for first device 0000:00:1a.0:
              echo -n "0000:00:1a.0" | tee /sys/bus/pci/drivers/ehci_hcd/bind
              # Bind ehci_hcd for second device 0000:00:1d.0:
              echo -n "0000:00:1d.0" | tee /sys/bus/pci/drivers/ehci_hcd/bind
        ;;
esac

sudo chmod +x /etc/pm/sleep.d/20_custom-ehci_hcd

Thanks a lot

---

### Post by entropy1 on 2012-05-01
The method of post #7 and post #19 worked for me with 64-bit Ubuntu 12.04 on an HP Elitebook 2740p.  It is necessary to make the file 20_custom-ehci_hcd executable.  Thank you!

---

### Post by wgregori on 2012-05-02
This solution is not working for my desktop with a fresh installation of Ubunutu 12.04.  The system will go through the suspend and hibernate process successfully but comes back on a second later.

Wayne





> **brocktice said:**
> Hi, I  modified this to automatically pull (and save, is that necessary?) the device IDs:

```

#!/bin/sh
# File: "/etc/pm/sleep.d/20_custom-ehci_hcd".
TMPLIST=/tmp/ehci-dev-list

case "${1}" in
        hibernate|suspend)
    echo -n '' > $TMPLIST
          for i in `ls /sys/bus/pci/drivers/ehci_hcd/ | egrep '[0-9a-z]+\:[0-9a-z]+\:.*$'`; do
              # Unbind ehci_hcd for first device XXXX:XX:XX.X:
               echo -n "$i" | tee /sys/bus/pci/drivers/ehci_hcd/unbind
           echo "$i" >> $TMPLIST
          done
        ;;
        resume|thaw)
    for i in `cat $TMPLIST`; do
              # Bind ehci_hcd for first device XXXX:XX:XX.X:
              echo -n "$i" | tee /sys/bus/pci/drivers/ehci_hcd/bind
    done
    rm $TMPLIST
        ;;
esac

```This seems to work fine. Should this be submitted somewhere for inclusion in Ubuntu? Is the tmplist thing ok? Should that be somehow changed?

---

### Post by overklox on 2012-05-03
If you have a board such as the [GA-970A-UD3]("http://www.gigabyte.us/products/product-page.aspx?pid=3907#ov") you will need to add scripts for OHCI and XHCI. Just modify the sections and replace with the appropriate module name.

(same script used for EHCI)
#!/bin/sh
# File: "/etc/pm/sleep.d/20_custom-ohci_hcd".
TMPLIST=/tmp/ohci-dev-list

case "${1}" in
        hibernate|suspend)
    echo -n '' > $TMPLIST
          for i in `ls /sys/bus/pci/drivers/ohci_hcd/ | egrep '[0-9a-z]+\:[0-9a-z]+\:.*$'`; do
              # Unbind ohci_hcd for first device XXXX:XX:XX.X:
               echo -n "$i" | tee /sys/bus/pci/drivers/ohci_hcd/unbind
           echo "$i" >> $TMPLIST
          done
        ;;
        resume|thaw)
    for i in `cat $TMPLIST`; do
              # Bind ohci_hcd for first device XXXX:XX:XX.X:
              echo -n "$i" | tee /sys/bus/pci/drivers/ohci_hcd/bind
    done
    rm $TMPLIST
        ;;
esac

---

### Post by illumilore on 2012-05-25
Suspend for my laptop seems to be very random for me. After creating a 20_custom-ehci_hcd file, going into suspend would no longer black the screen and then freeze everything to where you had to hold the power button to get the machine to turn off; the machine would suspend correctly some of the time, however it would sometimes get woken right back up the second it suspended. After messing around with /proc/acpi/wakeup, it seems that EHC2 needs to be disabled for it to stay in sleep mode, but that gets re-enabled every time a suspend cycle is completed (I am guessing due to the rebinding that the 20_*_hcd file does?). Also, to add to the randomness of whether it will stay in suspend mode or not, I will sometimes get hissing audio as it goes to sleep and wakes up.

---

### Post by wgregori on 2012-05-27
I've been struggling trying to get my Ubuntu 12.04 to suspend and hibernate... no luck so far.  Below is from my syslog... can anyone who understands this process take a look at this and see if there is something that I'm missing.

Thanks,
Wayne



```


May 27 12:48:34 wubuntu NetworkManager[943]: <info> sleep requested (sleeping: no  enabled: yes)
May 27 12:48:34 wubuntu NetworkManager[943]: <info> sleeping or disabling...
May 27 12:48:34 wubuntu NetworkManager[943]: <info> (eth0): now unmanaged
May 27 12:48:34 wubuntu NetworkManager[943]: <info> (eth0): device state change: activated -> unmanaged (reason 'sleeping') [100 10 37]
May 27 12:48:34 wubuntu NetworkManager[943]: <info> (eth0): deactivating device (reason 'sleeping') [37]
May 27 12:48:35 wubuntu NetworkManager[943]: <info> (eth0): canceled DHCP transaction, DHCP client pid 5204
May 27 12:48:35 wubuntu dnsmasq[5252]: exiting on receipt of SIGTERM
May 27 12:48:35 wubuntu NetworkManager[943]: <info> DNS: starting dnsmasq...
May 27 12:48:35 wubuntu avahi-daemon[955]: Withdrawing address record for fe80::21f:c6ff:fecf:90b8 on eth0.
May 27 12:48:35 wubuntu avahi-daemon[955]: Leaving mDNS multicast group on interface eth0.IPv6 with address fe80::21f:c6ff:fecf:90b8.
May 27 12:48:35 wubuntu avahi-daemon[955]: Interface eth0.IPv6 no longer relevant for mDNS.
May 27 12:48:35 wubuntu avahi-daemon[955]: Withdrawing address record for 192.168.1.41 on eth0.
May 27 12:48:35 wubuntu avahi-daemon[955]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.1.41.
May 27 12:48:35 wubuntu avahi-daemon[955]: Interface eth0.IPv4 no longer relevant for mDNS.
May 27 12:48:35 wubuntu NetworkManager[943]: <info> (eth0): writing resolv.conf to /sbin/resolvconf
May 27 12:48:35 wubuntu dnsmasq[5631]: started, version 2.59 cache disabled
May 27 12:48:35 wubuntu dnsmasq[5631]: compile time options: IPv6 GNU-getopt DBus i18n DHCP TFTP conntrack IDN
May 27 12:48:35 wubuntu dnsmasq[5631]: warning: no upstream servers configured
May 27 12:48:35 wubuntu NetworkManager[943]: <info> (eth0): cleaning up...
May 27 12:48:35 wubuntu NetworkManager[943]: <info> (eth0): taking down device.
May 27 12:48:35 wubuntu NetworkManager[943]: <info> (eth0): carrier now OFF (device state 10)
May 27 12:48:35 wubuntu dbus[787]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
May 27 12:48:35 wubuntu dbus[787]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
May 27 12:48:35 wubuntu anacron[5752]: Anacron 2.3 started on 2012-05-27
May 27 12:48:35 wubuntu anacron[5752]: Normal exit (0 jobs run)
May 27 12:48:37 wubuntu kernel: [22479.990735] ehci_hcd 0000:00:02.1: remove, state 1
May 27 12:48:37 wubuntu kernel: [22479.990747] usb usb1: USB disconnect, device number 1
May 27 12:48:37 wubuntu kernel: [22479.990749] usb 1-1: USB disconnect, device number 2
May 27 12:48:37 wubuntu kernel: [22479.997503] usb 1-4: USB disconnect, device number 4
May 27 12:48:37 wubuntu kernel: [22480.035219] ehci_hcd 0000:00:02.1: USB bus 1 deregistered
May 27 12:48:37 wubuntu kernel: [22480.035299] ehci_hcd 0000:00:02.1: PCI INT B disabled
May 27 12:48:37 wubuntu kernel: [22480.336161] usb 2-4: new full-speed USB device number 12 using ohci_hcd
May 27 12:48:37 wubuntu mtp-probe: checking bus 2, device 12: "/sys/devices/pci0000:00/0000:00:02.0/usb2/2-4"
May 27 12:48:37 wubuntu kernel: [22480.641118] uvcvideo: Found UVC 1.00 device <unnamed> (046d:09a1)
May 27 12:48:37 wubuntu kernel: [22480.667125] input: UVC Camera (046d:09a1) as /devices/pci0000:00/0000:00:02.0/usb2/2-4/2-4:1.0/input/input11
May 27 12:48:37 wubuntu mtp-probe: bus: 2, device: 12 was not an MTP device
May 27 12:48:38 wubuntu kernel: [22480.986812] PM: Marking nosave pages: 000000000009f000 - 0000000000100000
May 27 12:48:38 wubuntu kernel: [22480.986817] PM: Marking nosave pages: 00000000bfee0000 - 0000000100000000
May 27 12:48:38 wubuntu kernel: [22480.987634] PM: Marking nosave pages: 00000000b4000000 - 00000000b8000000
May 27 12:48:38 wubuntu kernel: [22480.987873] PM: Basic memory bitmaps created
May 27 12:49:42 wubuntu kernel: [22480.987874] PM: Syncing filesystems ... done.
May 27 12:49:42 wubuntu kernel: [22481.022830] Freezing user space processes ... (elapsed 0.01 seconds) done.
May 27 12:49:42 wubuntu kernel: [22481.036087] PM: Preallocating image memory... 
May 27 12:49:42 wubuntu kernel: [22481.072294] usb 2-1: new full-speed USB device number 13 using ohci_hcd
May 27 12:49:42 wubuntu kernel: [22481.297089] scsi9 : usb-storage 2-1:1.0
May 27 12:49:42 wubuntu kernel: [22482.304993] scsi 9:0:0:0: Direct-Access                                    PQ: 0 ANSI: 2 CCS
May 27 12:49:42 wubuntu kernel: [22482.305457] sd 9:0:0:0: Attached scsi generic sg1 type 0
May 27 12:49:42 wubuntu kernel: [22482.346883] done (allocated 604998 pages)
May 27 12:49:42 wubuntu kernel: [22482.346889] PM: Allocated 2419992 kbytes in 1.31 seconds (1847.32 MB/s)
May 27 12:49:42 wubuntu kernel: [22482.346891] Freezing remaining freezable tasks ... 
May 27 12:49:42 wubuntu kernel: [22482.349997] sd 9:0:0:0: [sdb] Test WP failed, assume Write Enabled
May 27 12:49:42 wubuntu kernel: [22482.360065] (elapsed 0.01 seconds) done.
May 27 12:49:42 wubuntu kernel: [22482.366990] sd 9:0:0:0: [sdb] Asking for cache data failed
May 27 12:49:42 wubuntu kernel: [22482.367034] sd 9:0:0:0: [sdb] Assuming drive cache: write through
May 27 12:49:42 wubuntu kernel: [22482.411985] sd 9:0:0:0: [sdb] Test WP failed, assume Write Enabled
May 27 12:49:42 wubuntu kernel: [22482.428984] sd 9:0:0:0: [sdb] Asking for cache data failed
May 27 12:49:42 wubuntu kernel: [22482.429026] sd 9:0:0:0: [sdb] Assuming drive cache: write through
May 27 12:49:42 wubuntu kernel: [22482.429062] sd 9:0:0:0: [sdb] Attached SCSI disk
May 27 12:49:42 wubuntu kernel: [22482.429125] Suspending console(s) (use no_console_suspend to debug)
May 27 12:49:42 wubuntu kernel: [22482.429432] sd 1:0:0:0: [sda] Synchronizing SCSI cache
May 27 12:49:42 wubuntu kernel: [22482.430042] parport_pc 00:09: disabled
May 27 12:49:42 wubuntu kernel: [22482.430135] serial 00:08: disabled
May 27 12:49:42 wubuntu kernel: [22482.430140] serial 00:08: wake-up capability disabled by ACPI
May 27 12:49:42 wubuntu kernel: [22482.431343] sata_nv 0000:00:07.0: PCI INT A disabled
May 27 12:49:42 wubuntu kernel: [22482.436042] ACPI handle has no context!
May 27 12:49:42 wubuntu kernel: [22482.632020] sd 4:0:0:0: [sdc] Synchronizing SCSI cache
May 27 12:49:42 wubuntu kernel: [22482.657527] PM: freeze of drv:sd dev:4:0:0:0 complete after 228.161 msecs
May 27 12:49:42 wubuntu kernel: [22482.657543] PM: freeze of drv:scsi dev:target4:0:0 complete after 228.149 msecs
May 27 12:49:42 wubuntu kernel: [22482.657550] PM: freeze of drv:scsi dev:host4 complete after 228.009 msecs
May 27 12:49:42 wubuntu kernel: [22482.657620] sata_nv 0000:00:08.0: PCI INT A disabled
May 27 12:49:42 wubuntu kernel: [22482.657624] PM: freeze of drv:sata_nv dev:0000:00:08.0 complete after 226.937 msecs
May 27 12:49:42 wubuntu kernel: [22482.664307] PM: freeze of drv:nvidia dev:0000:05:00.0 complete after 234.120 msecs
May 27 12:49:42 wubuntu kernel: [22482.664325] PM: freeze of drv:pcieport dev:0000:00:0e.0 complete after 233.817 msecs
May 27 12:49:42 wubuntu kernel: [22482.664361] PM: freeze of drv: dev:pci0000:00 complete after 233.546 msecs
May 27 12:49:42 wubuntu kernel: [22482.664372] PM: freeze of devices complete after 235.239 msecs
May 27 12:49:42 wubuntu kernel: [22482.664920] PM: late freeze of devices complete after 0.545 msecs
May 27 12:49:42 wubuntu kernel: [22482.664995] ACPI: Preparing to enter system sleep state S4
May 27 12:49:42 wubuntu kernel: [22482.665442] PM: Saving platform NVS memory
May 27 12:49:42 wubuntu kernel: [22482.665445] Disabling non-boot CPUs ...
May 27 12:49:42 wubuntu kernel: [22482.768010] CPU 1 is now offline
May 27 12:49:42 wubuntu kernel: [22482.768441] Extended CMOS year: 2000
May 27 12:49:42 wubuntu kernel: [22482.768498] PM: Creating hibernation image:
May 27 12:49:42 wubuntu kernel: [22482.772003] PM: Need to copy 337581 pages
May 27 12:49:42 wubuntu kernel: [22482.772003] PM: Normal pages needed: 337581 + 1024, available pages: 694127
May 27 12:49:42 wubuntu kernel: [22482.772003] PM: Restoring platform NVS memory
May 27 12:49:42 wubuntu kernel: [22482.772003] PCI-DMA: Resuming GART IOMMU
May 27 12:49:42 wubuntu kernel: [22482.772003] PCI-DMA: Restoring GART aperture settings
May 27 12:49:42 wubuntu kernel: [22482.772003] Extended CMOS year: 2000
May 27 12:49:42 wubuntu kernel: [22482.772003] Enabling non-boot CPUs ...
May 27 12:49:42 wubuntu kernel: [22482.772003] Booting Node 0 Processor 1 APIC 0x1
May 27 12:49:42 wubuntu kernel: [22482.772003] smpboot cpu 1: start_ip = 9a000
May 27 12:49:42 wubuntu kernel: [22482.780118] Calibrating delay loop (skipped) already calibrated this CPU
May 27 12:49:42 wubuntu kernel: [22482.780458] NMI watchdog enabled, takes one hw-pmu counter.
May 27 12:49:42 wubuntu kernel: [22482.784055] CPU1 is up
May 27 12:49:42 wubuntu kernel: [22482.784369] ACPI: Waking up from system sleep state S4
May 27 12:49:42 wubuntu kernel: [22482.784639] pci 0000:00:02.1: restoring config space at offset 0x1 (was 0xb00006, writing 0xb00002)
May 27 12:49:42 wubuntu kernel: [22482.784655] pata_amd 0000:00:06.0: restoring config space at offset 0x1 (was 0xb00001, writing 0xb00005)
May 27 12:49:42 wubuntu kernel: [22482.784668] sata_nv 0000:00:07.0: restoring config space at offset 0x1 (was 0xb00003, writing 0xb00007)
May 27 12:49:42 wubuntu kernel: [22482.784681] sata_nv 0000:00:08.0: restoring config space at offset 0x1 (was 0xb00003, writing 0xb00007)
May 27 12:49:42 wubuntu kernel: [22482.784691] pci 0000:00:09.0: restoring config space at offset 0x7 (was 0x2280a0a0, writing 0xa280a0a0)
May 27 12:49:42 wubuntu kernel: [22482.784704] forcedeth 0000:00:0a.0: restoring config space at offset 0x1 (was 0xb00007, writing 0xb80007)
May 27 12:49:42 wubuntu kernel: [22482.784755] pci 0000:00:00.0: Found enabled HT MSI Mapping
May 27 12:49:42 wubuntu kernel: [22482.784802] pci 0000:00:00.0: Found enabled HT MSI Mapping
May 27 12:49:42 wubuntu kernel: [22482.784850] pci 0000:00:00.0: Found enabled HT MSI Mapping
May 27 12:49:42 wubuntu kernel: [22482.784902] pci 0000:00:00.0: Found enabled HT MSI Mapping
May 27 12:49:42 wubuntu kernel: [22482.800022] firewire_ohci 0000:01:01.0: BAR 0: set to [mem 0xfdfff000-0xfdfff7ff] (PCI address [0xfdfff000-0xfdfff7ff])
May 27 12:49:42 wubuntu kernel: [22482.800027] firewire_ohci 0000:01:01.0: BAR 1: set to [io  0xac00-0xac7f] (PCI address [0xac00-0xac7f])
May 27 12:49:42 wubuntu kernel: [22482.800059] nvidia 0000:05:00.0: restoring config space at offset 0xc (was 0xfcfe0000, writing 0x0)
May 27 12:49:42 wubuntu kernel: [22482.800066] nvidia 0000:05:00.0: restoring config space at offset 0x3 (was 0x8, writing 0x0)
May 27 12:49:42 wubuntu kernel: [22482.800364] PM: early restore of devices complete after 15.863 msecs
May 27 12:49:42 wubuntu kernel: [22482.892461] ohci_hcd 0000:00:02.0: setting latency timer to 64
May 27 12:49:42 wubuntu kernel: [22482.892512] pata_amd 0000:00:06.0: setting latency timer to 64
May 27 12:49:42 wubuntu kernel: [22482.892534] sata_nv 0000:00:07.0: PCI INT A -> Link[APSI] -> GSI 21 (level, low) -> IRQ 21
May 27 12:49:42 wubuntu kernel: [22482.892536] sata_nv 0000:00:07.0: setting latency timer to 64
May 27 12:49:42 wubuntu kernel: [22482.892553] sata_nv 0000:00:08.0: PCI INT A -> Link[APSJ] -> GSI 20 (level, low) -> IRQ 20
May 27 12:49:42 wubuntu kernel: [22482.892557] sata_nv 0000:00:08.0: setting latency timer to 64
May 27 12:49:42 wubuntu kernel: [22482.892570] pci 0000:00:09.0: setting latency timer to 64
May 27 12:49:42 wubuntu kernel: [22482.894982] serial 00:08: activated
May 27 12:49:42 wubuntu kernel: [22482.895353] parport_pc 00:09: activated
May 27 12:49:42 wubuntu kernel: [22482.896082] sd 1:0:0:0: [sda] Starting disk
May 27 12:49:42 wubuntu kernel: [22482.896118] sd 4:0:0:0: [sdc] Starting disk
May 27 12:49:42 wubuntu kernel: [22482.950011] usb usb2: root hub lost power or was reset
May 27 12:49:42 wubuntu kernel: [22482.979094] firewire_core: skipped bus generations, destroying all nodes
May 27 12:49:42 wubuntu kernel: [22483.248024] PM: restore of drv:hub dev:2-0:1.0 complete after 352.225 msecs
May 27 12:49:42 wubuntu kernel: [22483.248034] PM: restore of drv: dev:ep_00 complete after 351.986 msecs
May 27 12:49:42 wubuntu kernel: [22483.248040] PM: restore of drv: dev:ep_81 complete after 351.996 msecs
May 27 12:49:42 wubuntu kernel: [22483.248059] PM: restore of drv:uvcvideo dev:2-4:1.0 complete after 351.510 msecs
May 27 12:49:42 wubuntu kernel: [22483.248067] PM: restore of drv: dev:ep_87 complete after 351.494 msecs
May 27 12:49:42 wubuntu kernel: [22483.248073] PM: restore of drv:uvcvideo dev:2-4:1.1 complete after 351.472 msecs
May 27 12:49:42 wubuntu kernel: [22483.248084] PM: restore of drv: dev:ep_00 complete after 351.222 msecs
May 27 12:49:42 wubuntu kernel: [22483.248088] PM: restore of drv:snd-usb-audio dev:2-4:1.2 complete after 351.463 msecs
May 27 12:49:42 wubuntu kernel: [22483.248091] PM: restore of drv:usb-storage dev:2-1:1.0 complete after 351.351 msecs
May 27 12:49:42 wubuntu kernel: [22483.248094] PM: restore of drv:snd-usb-audio dev:2-4:1.3 complete after 351.448 msecs
May 27 12:49:42 wubuntu kernel: [22483.248101] PM: restore of drv: dev:ep_00 complete after 351.432 msecs
May 27 12:49:42 wubuntu kernel: [22483.248106] PM: restore of drv: dev:ep_81 complete after 351.290 msecs
May 27 12:49:42 wubuntu kernel: [22483.248117] PM: restore of drv: dev:ep_86 complete after 351.424 msecs
May 27 12:49:42 wubuntu kernel: [22483.248121] PM: restore of drv:scsi dev:host9 complete after 351.354 msecs
May 27 12:49:42 wubuntu kernel: [22483.248124] PM: restore of drv: dev:ep_02 complete after 351.285 msecs
May 27 12:49:42 wubuntu kernel: [22483.248129] PM: restore of drv:scsi_host dev:host9 complete after 351.338 msecs
May 27 12:49:42 wubuntu kernel: [22483.248139] PM: restore of drv:scsi dev:target9:0:0 complete after 351.255 msecs
May 27 12:49:42 wubuntu kernel: [22483.248160] PM: restore of drv:sd dev:9:0:0:0 complete after 351.251 msecs
May 27 12:49:42 wubuntu kernel: [22483.248170] PM: restore of drv:scsi_device dev:9:0:0:0 complete after 351.237 msecs
May 27 12:49:42 wubuntu kernel: [22483.360032] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
May 27 12:49:42 wubuntu kernel: [22483.360053] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
May 27 12:49:42 wubuntu kernel: [22483.360148] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
May 27 12:49:42 wubuntu kernel: [22483.368142] ata1.00: ACPI cmd ef/03:46:00:00:00:a0 (SET FEATURES) filtered out
May 27 12:49:42 wubuntu kernel: [22483.368145] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
May 27 12:49:42 wubuntu kernel: [22483.368151] ata4.00: ACPI cmd ef/03:46:00:00:00:a0 (SET FEATURES) filtered out
May 27 12:49:42 wubuntu kernel: [22483.368155] ata4.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
May 27 12:49:42 wubuntu kernel: [22483.368274] ata3.00: ACPI cmd ef/03:46:00:00:00:a0 (SET FEATURES) filtered out
May 27 12:49:42 wubuntu kernel: [22483.384182] ata3.00: configured for UDMA/100
May 27 12:49:42 wubuntu kernel: [22483.384345] ata4.00: configured for UDMA/133
May 27 12:49:42 wubuntu kernel: [22483.384702] ata1.00: configured for UDMA/133
May 27 12:49:42 wubuntu kernel: [22483.401779] PM: restore of drv:sd dev:1:0:0:0 complete after 505.699 msecs
May 27 12:49:42 wubuntu kernel: [22483.401790] PM: restore of drv:scsi_device dev:1:0:0:0 complete after 505.687 msecs
May 27 12:49:42 wubuntu kernel: [22483.407015] PM: restore of drv:sd dev:4:0:0:0 complete after 510.896 msecs
May 27 12:49:42 wubuntu kernel: [22483.407026] PM: restore of drv:scsi_device dev:4:0:0:0 complete after 510.895 msecs
May 27 12:49:42 wubuntu kernel: [22483.416188] PM: restore of drv:forcedeth dev:0000:00:0a.0 complete after 523.612 msecs
May 27 12:49:42 wubuntu kernel: [22483.416201] PM: restore of drv:net dev:eth0 complete after 466.102 msecs
May 27 12:49:42 wubuntu kernel: [22483.424047] usb 2-2: reset full-speed USB device number 8 using ohci_hcd
May 27 12:49:42 wubuntu kernel: [22483.476025] firewire_core: rediscovered device fw0
May 27 12:49:42 wubuntu kernel: [22483.616023] ata2: SATA link down (SStatus 0 SControl 300)
May 27 12:49:42 wubuntu kernel: [22483.796013] usb 2-7: reset full-speed USB device number 9 using ohci_hcd
May 27 12:49:42 wubuntu kernel: [22483.864024] PM: restore of drv:hub dev:2-2:1.0 complete after 967.887 msecs
May 27 12:49:42 wubuntu kernel: [22483.864031] PM: restore of drv: dev:ep_00 complete after 967.889 msecs
May 27 12:49:42 wubuntu kernel: [22483.864037] PM: restore of drv: dev:ep_81 complete after 967.896 msecs
May 27 12:49:42 wubuntu kernel: [22484.004025] snd-usb-audio 2-7:1.0: no reset_resume for driver snd-usb-audio?
May 27 12:49:42 wubuntu kernel: [22484.004028] snd-usb-audio 2-7:1.1: no reset_resume for driver snd-usb-audio?
May 27 12:49:42 wubuntu kernel: [22484.004030] snd-usb-audio 2-7:1.2: no reset_resume for driver snd-usb-audio?
May 27 12:49:42 wubuntu kernel: [22484.004252] PM: restore of drv:usb dev:2-7:1.0 complete after 1108.102 msecs
May 27 12:49:42 wubuntu kernel: [22484.004257] PM: restore of drv:usb dev:2-7:1.2 complete after 1108.011 msecs
May 27 12:49:42 wubuntu kernel: [22484.004263] PM: restore of drv:usb dev:2-7:1.1 complete after 1108.045 msecs
May 27 12:49:42 wubuntu kernel: [22484.004267] PM: restore of drv: dev:ep_00 complete after 1107.999 msecs
May 27 12:49:42 wubuntu kernel: [22484.004270] PM: restore of drv:sound dev:card0 complete after 587.919 msecs
May 27 12:49:42 wubuntu kernel: [22484.004272] PM: restore of drv: dev:ep_81 complete after 1108.079 msecs
May 27 12:49:42 wubuntu kernel: [22484.253031] usb 2-2.1: reset low-speed USB device number 10 using ohci_hcd
May 27 12:49:42 wubuntu kernel: [22484.561033] PM: restore of drv: dev:ep_00 complete after 1664.627 msecs
May 27 12:49:42 wubuntu kernel: [22484.561036] PM: restore of drv:usbhid dev:2-2.1:1.0 complete after 1664.723 msecs
May 27 12:49:42 wubuntu kernel: [22484.561065] PM: restore of drv:usbhid dev:2-2.1:1.1 complete after 1664.705 msecs
May 27 12:49:42 wubuntu kernel: [22484.561069] PM: restore of drv:generic-usb dev:0003:046E:52C4.0004 complete after 556.789 msecs
May 27 12:49:42 wubuntu kernel: [22484.561074] PM: restore of drv: dev:ep_81 complete after 1664.738 msecs
May 27 12:49:42 wubuntu kernel: [22484.561079] PM: restore of drv: dev:ep_82 complete after 1664.697 msecs
May 27 12:49:42 wubuntu kernel: [22484.801030] usb 2-2.2: reset low-speed USB device number 11 using ohci_hcd
May 27 12:49:42 wubuntu kernel: [22485.100041] PM: restore of drv: dev:ep_00 complete after 2203.540 msecs
May 27 12:49:42 wubuntu kernel: [22485.100045] PM: restore of drv:usbhid dev:2-2.2:1.0 complete after 2203.587 msecs
May 27 12:49:42 wubuntu kernel: [22485.100054] PM: restore of drv:generic-usb dev:0003:046D:C50E.0006 complete after 538.945 msecs
May 27 12:49:42 wubuntu kernel: [22485.100057] PM: restore of drv: dev:ep_81 complete after 2203.578 msecs
May 27 12:49:42 wubuntu kernel: [22485.100095] PM: restore of devices complete after 2207.697 msecs
May 27 12:49:42 wubuntu kernel: [22485.176339] PM: Image restored successfully.
May 27 12:49:42 wubuntu kernel: [22485.176342] Restarting tasks ... 
May 27 12:49:42 wubuntu kernel: [22485.176390] usb 2-1: USB disconnect, device number 13
May 27 12:49:42 wubuntu kernel: [22485.177247] done.
May 27 12:49:42 wubuntu kernel: [22485.177273] PM: Basic memory bitmaps freed
May 27 12:49:42 wubuntu kernel: [22485.316027] usb 2-4: USB disconnect, device number 12
May 27 12:49:42 wubuntu rtkit-daemon[1784]: The canary thread is apparently starving. Taking action.
May 27 12:49:42 wubuntu rtkit-daemon[1784]: Demoting known real-time threads.
May 27 12:49:42 wubuntu rtkit-daemon[1784]: Successfully demoted thread 6186 of process 1782 (n/a).
May 27 12:49:42 wubuntu rtkit-daemon[1784]: Demoted 1 threads.
May 27 12:49:42 wubuntu rtkit-daemon[1784]: Successfully made thread 6186 of process 1782 (n/a) owned by '1000' RT at priority 5.
May 27 12:49:42 wubuntu rtkit-daemon[1784]: Supervising 1 threads of 1 processes of 1 users.
May 27 12:49:43 wubuntu mtp-probe: checking bus 2, device 13: "/sys/devices/pci0000:00/0000:00:02.0/usb2/2-1"
May 27 12:49:43 wubuntu mtp-probe: bus: 2, device: 13 was not an MTP device
May 27 12:49:43 wubuntu pulseaudio[1782]: [alsa-source] alsa-source.c: snd_pcm_avail: No such device
May 27 12:49:44 wubuntu acpid: client 1226[0:0] has disconnected
May 27 12:49:44 wubuntu acpid: client 1226[0:0] has disconnected
May 27 12:49:44 wubuntu acpid: client connected from 1226[0:0]
May 27 12:49:44 wubuntu acpid: 1 client rule loaded
May 27 12:49:44 wubuntu acpid: client connected from 1226[0:0]
May 27 12:49:44 wubuntu acpid: 1 client rule loaded
May 27 12:49:45 wubuntu anacron[6328]: Anacron 2.3 started on 2012-05-27
May 27 12:49:45 wubuntu anacron[6328]: Normal exit (0 jobs run)
May 27 12:49:46 wubuntu kernel: [22489.325531] ehci_hcd 0000:00:02.1: PCI INT B -> Link[APCL] -> GSI 22 (level, low) -> IRQ 22
May 27 12:49:46 wubuntu kernel: [22489.325609] ehci_hcd 0000:00:02.1: setting latency timer to 64
May 27 12:49:46 wubuntu kernel: [22489.325616] ehci_hcd 0000:00:02.1: EHCI Host Controller
May 27 12:49:46 wubuntu kernel: [22489.325846] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
May 27 12:49:46 wubuntu kernel: [22489.325914] ehci_hcd 0000:00:02.1: debug port 1
May 27 12:49:46 wubuntu kernel: [22489.325955] ehci_hcd 0000:00:02.1: cache line size of 32 is not supported
May 27 12:49:46 wubuntu kernel: [22489.325984] ehci_hcd 0000:00:02.1: irq 22, io mem 0xfeb00000
May 27 12:49:46 wubuntu kernel: [22489.336099] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
May 27 12:49:46 wubuntu kernel: [22489.336542] hub 1-0:1.0: USB hub found
May 27 12:49:46 wubuntu kernel: [22489.336553] hub 1-0:1.0: 9 ports detected
May 27 12:49:46 wubuntu kernel: [22489.488156] 9:1:2: usb_set_interface failed
May 27 12:49:46 wubuntu kernel: [22489.490743] 9:1:2: usb_set_interface failed
May 27 12:49:46 wubuntu kernel: [22489.493048] 9:1:2: usb_set_interface failed
May 27 12:49:46 wubuntu kernel: [22489.497061] 9:1:2: usb_set_interface failed
May 27 12:49:46 wubuntu kernel: [22489.500450] 9:1:2: usb_set_interface failed
May 27 12:49:46 wubuntu kernel: [22489.504072] 9:1:2: usb_set_interface failed
May 27 12:49:46 wubuntu kernel: [22489.507067] 9:1:2: usb_set_interface failed
May 27 12:49:46 wubuntu kernel: [22489.510048] 9:1:2: usb_set_interface failed
May 27 12:49:46 wubuntu kernel: [22489.513040] 9:1:2: usb_set_interface failed
May 27 12:49:46 wubuntu kernel: [22489.516070] 9:1:2: usb_set_interface failed
May 27 12:49:46 wubuntu kernel: [22489.519043] 9:1:2: usb_set_interface failed
May 27 12:49:46 wubuntu kernel: [22489.522031] 9:1:2: usb_set_interface failed
May 27 12:49:46 wubuntu kernel: [22489.525032] 9:1:2: usb_set_interface failed
May 27 12:49:46 wubuntu kernel: [22489.528262] 9:1:2: usb_set_interface failed
May 27 12:49:46 wubuntu kernel: [22489.531057] 9:1:2: usb_set_interface failed
May 27 12:49:46 wubuntu kernel: [22489.535043] 9:1:2: usb_set_interface failed
May 27 12:49:46 wubuntu kernel: [22489.538032] 9:1:2: usb_set_interface failed
May 27 12:49:46 wubuntu kernel: [22489.541033] 9:1:2: usb_set_interface failed
May 27 12:49:46 wubuntu kernel: [22489.544070] 9:1:2: usb_set_interface failed
May 27 12:49:46 wubuntu kernel: [22489.547046] 9:1:2: usb_set_interface failed
May 27 12:49:46 wubuntu kernel: [22489.550037] 9:1:2: usb_set_interface failed
May 27 12:49:46 wubuntu kernel: [22489.553033] 9:1:2: usb_set_interface failed
May 27 12:49:46 wubuntu kernel: [22489.556044] 9:1:2: usb_set_interface failed
May 27 12:49:46 wubuntu kernel: [22489.559037] 9:1:2: usb_set_interface failed
May 27 12:49:46 wubuntu kernel: [22489.562048] 9:1:2: usb_set_interface failed
May 27 12:49:46 wubuntu kernel: [22489.565038] 9:1:2: usb_set_interface failed
May 27 12:49:46 wubuntu kernel: [22489.568127] 9:1:2: usb_set_interface failed
May 27 12:49:46 wubuntu kernel: [22489.571049] 9:1:2: usb_set_interface failed
May 27 12:49:46 wubuntu kernel: [22489.574057] 9:1:2: usb_set_interface failed
May 27 12:49:46 wubuntu kernel: [22489.577053] 9:1:2: usb_set_interface failed
May 27 12:49:46 wubuntu kernel: [22489.580131] 9:1:2: usb_set_interface failed
May 27 12:49:46 wubuntu kernel: [22489.580150] usb 2-7: USB disconnect, device number 9
May 27 12:49:46 wubuntu kernel: [22489.580257] 9:1:2: usb_set_interface failed
May 27 12:49:46 wubuntu kernel: [22489.580498] 9:1:2: usb_set_interface failed
May 27 12:49:46 wubuntu kernel: [22489.582059] 9:1:2: usb_set_interface failed
May 27 12:49:46 wubuntu pulseaudio[1782]: [pulseaudio] udev-util.c: Failed to get card object.
May 27 12:49:46 wubuntu pulseaudio[1782]: [pulseaudio] module-alsa-card.c: Failed to find a working profile.
May 27 12:49:46 wubuntu pulseaudio[1782]: [pulseaudio] module.c: Failed to load module "module-alsa-card" (argument: "device_id="0" name="usb-0d8c_PnP_Audio_Device-00-Device" card_name="alsa_card.usb-0d8c_PnP_Audio_Device-00-Device" namereg_fail=false tsched=yes ignore_dB=no deferred_volume=yes card_properties="module-udev-detect.discovered=1""): initialization failed.
May 27 12:49:46 wubuntu kernel: [22489.720067] usb 2-2: USB disconnect, device number 8
May 27 12:49:46 wubuntu kernel: [22489.720077] usb 2-2.1: USB disconnect, device number 10
May 27 12:49:46 wubuntu kernel: [22489.828344] usb 2-2.2: USB disconnect, device number 11
May 27 12:49:46 wubuntu kernel: [22490.100051] usb 1-1: new high-speed USB device number 2 using ehci_hcd
May 27 12:49:46 wubuntu mtp-probe: checking bus 1, device 2: "/sys/devices/pci0000:00/0000:00:02.1/usb1/1-1"
May 27 12:49:46 wubuntu mtp-probe: bus: 1, device: 2 was not an MTP device
May 27 12:49:46 wubuntu kernel: [22490.244354] scsi10 : usb-storage 1-1:1.0
May 27 12:49:47 wubuntu kernel: [22490.468079] usb 1-4: new high-speed USB device number 4 using ehci_hcd
May 27 12:49:47 wubuntu anacron[6515]: Anacron 2.3 started on 2012-05-27
May 27 12:49:47 wubuntu anacron[6515]: Normal exit (0 jobs run)
May 27 12:49:47 wubuntu kernel: [22490.718302] uvcvideo: Found UVC 1.00 device <unnamed> (046d:09a1)
May 27 12:49:47 wubuntu mtp-probe: checking bus 1, device 4: "/sys/devices/pci0000:00/0000:00:02.1/usb1/1-4"
May 27 12:49:47 wubuntu NetworkManager[943]: <info> wake requested (sleeping: yes  enabled: yes)
May 27 12:49:47 wubuntu NetworkManager[943]: <info> waking up and re-enabling...
May 27 12:49:47 wubuntu kernel: [22490.750080] input: UVC Camera (046d:09a1) as /devices/pci0000:00/0000:00:02.1/usb1/1-4/1-4:1.0/input/input12
May 27 12:49:47 wubuntu mtp-probe: bus: 1, device: 4 was not an MTP device
May 27 12:49:47 wubuntu NetworkManager[943]: <info> (eth0): now managed
May 27 12:49:47 wubuntu NetworkManager[943]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
May 27 12:49:47 wubuntu kernel: [22491.168073] usb 2-2: new full-speed USB device number 14 using ohci_hcd
May 27 12:49:47 wubuntu NetworkManager[943]: <info> (eth0): bringing up device.
May 27 12:49:47 wubuntu NetworkManager[943]: <info> (eth0): carrier now ON (device state 20)
May 27 12:49:47 wubuntu NetworkManager[943]: <info> (eth0): preparing device.
May 27 12:49:47 wubuntu NetworkManager[943]: <info> (eth0): deactivating device (reason 'managed') [2]
May 27 12:49:47 wubuntu kernel: [22491.247313] scsi 10:0:0:0: Direct-Access                                    PQ: 0 ANSI: 2 CCS
May 27 12:49:47 wubuntu kernel: [22491.249122] sd 10:0:0:0: Attached scsi generic sg1 type 0
May 27 12:49:47 wubuntu kernel: [22491.254554] sd 10:0:0:0: [sdb] Test WP failed, assume Write Enabled
May 27 12:49:47 wubuntu kernel: [22491.256992] sd 10:0:0:0: [sdb] Asking for cache data failed
May 27 12:49:47 wubuntu kernel: [22491.257003] sd 10:0:0:0: [sdb] Assuming drive cache: write through
May 27 12:49:47 wubuntu kernel: [22491.262697] sd 10:0:0:0: [sdb] Test WP failed, assume Write Enabled
May 27 12:49:47 wubuntu kernel: [22491.264547] sd 10:0:0:0: [sdb] Asking for cache data failed
May 27 12:49:47 wubuntu kernel: [22491.264555] sd 10:0:0:0: [sdb] Assuming drive cache: write through
May 27 12:49:47 wubuntu kernel: [22491.264572] sd 10:0:0:0: [sdb] Attached SCSI disk
May 27 12:49:48 wubuntu kernel: [22491.375228] hub 2-2:1.0: USB hub found
May 27 12:49:48 wubuntu kernel: [22491.379920] hub 2-2:1.0: 4 ports detected
May 27 12:49:48 wubuntu ata_id[6605]: HDIO_GET_IDENTITY failed for '/dev/sdb': Invalid argument
May 27 12:49:48 wubuntu NetworkManager[943]: <info> (eth0): device state change: unavailable -> disconnected (reason 'none') [20 30 0]
May 27 12:49:48 wubuntu NetworkManager[943]: <info> Auto-activating connection 'Wired connection 1'.
May 27 12:49:48 wubuntu NetworkManager[943]: <info> Activation (eth0) starting connection 'Wired connection 1'
May 27 12:49:48 wubuntu NetworkManager[943]: <info> (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
May 27 12:49:48 wubuntu NetworkManager[943]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
May 27 12:49:48 wubuntu NetworkManager[943]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
May 27 12:49:48 wubuntu NetworkManager[943]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
May 27 12:49:48 wubuntu NetworkManager[943]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
May 27 12:49:48 wubuntu NetworkManager[943]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
May 27 12:49:48 wubuntu NetworkManager[943]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
May 27 12:49:48 wubuntu NetworkManager[943]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
May 27 12:49:48 wubuntu NetworkManager[943]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
May 27 12:49:48 wubuntu NetworkManager[943]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
May 27 12:49:48 wubuntu NetworkManager[943]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
May 27 12:49:48 wubuntu NetworkManager[943]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
May 27 12:49:48 wubuntu NetworkManager[943]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
May 27 12:49:48 wubuntu kernel: [22491.700047] usb 2-7: new full-speed USB device number 15 using ohci_hcd
May 27 12:49:48 wubuntu rtkit-daemon[1784]: Recovering from system lockup, not allowing further RT threads.
May 27 12:49:48  rtkit-daemon[1784]: last message repeated 4 times
May 27 12:49:48 wubuntu NetworkManager[943]: <info> dhclient started with pid 6621
May 27 12:49:48 wubuntu NetworkManager[943]: <info> Activation (eth0) Beginning IP6 addrconf.
May 27 12:49:48 wubuntu mtp-probe: checking bus 2, device 15: "/sys/devices/pci0000:00/0000:00:02.0/usb2/2-7"
May 27 12:49:48 wubuntu NetworkManager[943]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
May 27 12:49:48 wubuntu mtp-probe: bus: 2, device: 15 was not an MTP device
May 27 12:49:48 wubuntu kernel: [22492.074066] usb 2-2.1: new low-speed USB device number 16 using ohci_hcd
May 27 12:49:48 wubuntu mtp-probe: checking bus 2, device 16: "/sys/devices/pci0000:00/0000:00:02.0/usb2/2-2/2-2.1"
May 27 12:49:48 wubuntu kernel: [22492.227824] input: BTC USB Multimedia Keyboard as /devices/pci0000:00/0000:00:02.0/usb2/2-2/2-2.1/2-2.1:1.0/input/input13
May 27 12:49:48 wubuntu dhclient: Internet Systems Consortium DHCP Client 4.1-ESV-R4
May 27 12:49:48 wubuntu dhclient: Copyright 2004-2011 Internet Systems Consortium.
May 27 12:49:48 wubuntu dhclient: All rights reserved.
May 27 12:49:48 wubuntu dhclient: For info, please visit https://www.isc.org/software/dhcp/
May 27 12:49:48 wubuntu dhclient: 
May 27 12:49:48 wubuntu kernel: [22492.228850] generic-usb 0003:046E:52C4.0007: input,hidraw0: USB HID v1.10 Keyboard [BTC USB Multimedia Keyboard] on usb-0000:00:02.0-2.1/input0
May 27 12:49:48 wubuntu kernel: [22492.263259] input: BTC USB Multimedia Keyboard as /devices/pci0000:00/0000:00:02.0/usb2/2-2/2-2.1/2-2.1:1.1/input/input14
May 27 12:49:48 wubuntu mtp-probe: bus: 2, device: 16 was not an MTP device
May 27 12:49:49 wubuntu kernel: [22492.265769] generic-usb 0003:046E:52C4.0008: input,hiddev0,hidraw1: USB HID v1.10 Device [BTC USB Multimedia Keyboard] on usb-0000:00:02.0-2.1/input1
May 27 12:49:49 wubuntu kernel: [22492.341048] usb 2-2.2: new low-speed USB device number 17 using ohci_hcd
May 27 12:49:49 wubuntu dhclient: Listening on LPF/eth0/00:1f:c6:cf:90:b8
May 27 12:49:49 wubuntu dhclient: Sending on   LPF/eth0/00:1f:c6:cf:90:b8
May 27 12:49:49 wubuntu dhclient: Sending on   Socket/fallback
May 27 12:49:49 wubuntu dhclient: DHCPREQUEST of 192.168.1.41 on eth0 to 255.255.255.255 port 67
May 27 12:49:49 wubuntu NetworkManager[943]: <info> (eth0): DHCPv4 state changed nbi -> preinit
May 27 12:49:49 wubuntu dhclient: DHCPACK of 192.168.1.41 from 192.168.1.1
May 27 12:49:49 wubuntu dhclient: bound to 192.168.1.41 -- renewal in 42429 seconds.
May 27 12:49:49 wubuntu NetworkManager[943]: <info> (eth0): DHCPv4 state changed preinit -> reboot
May 27 12:49:49 wubuntu NetworkManager[943]: <info>   address 192.168.1.41
May 27 12:49:49 wubuntu NetworkManager[943]: <info>   prefix 24 (255.255.255.0)
May 27 12:49:49 wubuntu NetworkManager[943]: <info>   gateway 192.168.1.1
May 27 12:49:49 wubuntu NetworkManager[943]: <info>   nameserver '192.168.1.1'
May 27 12:49:49 wubuntu NetworkManager[943]: <info>   domain name 'netgear.com'
May 27 12:49:49 wubuntu NetworkManager[943]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
May 27 12:49:49 wubuntu NetworkManager[943]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) started...
May 27 12:49:49 wubuntu avahi-daemon[955]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.41.
May 27 12:49:49 wubuntu avahi-daemon[955]: New relevant interface eth0.IPv4 for mDNS.
May 27 12:49:49 wubuntu avahi-daemon[955]: Registering new address record for 192.168.1.41 on eth0.IPv4.
May 27 12:49:49 wubuntu mtp-probe: checking bus 2, device 17: "/sys/devices/pci0000:00/0000:00:02.0/usb2/2-2/2-2.2"
May 27 12:49:49 wubuntu mtp-probe: bus: 2, device: 17 was not an MTP device
May 27 12:49:49 wubuntu kernel: [22492.474491] input: Logitech USB RECEIVER as /devices/pci0000:00/0000:00:02.0/usb2/2-2/2-2.2/2-2.2:1.0/input/input15
May 27 12:49:49 wubuntu kernel: [22492.474751] generic-usb 0003:046D:C50E.0009: input,hidraw2: USB HID v1.11 Mouse [Logitech USB RECEIVER] on usb-0000:00:02.0-2.2/input0
May 27 12:49:49 wubuntu pulseaudio[1782]: [pulseaudio] alsa-mixer.c: Volume element Speaker has 8 channels. That's too much! I can't handle that!
May 27 12:49:49  pulseaudio[1782]: last message repeated 3 times
May 27 12:49:49 wubuntu rtkit-daemon[1784]: Recovering from system lockup, not allowing further RT threads.
May 27 12:49:50  rtkit-daemon[1784]: last message repeated 9 times
May 27 12:49:50 wubuntu NetworkManager[943]: <info> DNS: starting dnsmasq...
May 27 12:49:50 wubuntu dnsmasq[5631]: exiting on receipt of SIGTERM
May 27 12:49:50 wubuntu NetworkManager[943]: <info> (eth0): writing resolv.conf to /sbin/resolvconf
May 27 12:49:50 wubuntu dnsmasq[6675]: started, version 2.59 cache disabled
May 27 12:49:50 wubuntu dnsmasq[6675]: compile time options: IPv6 GNU-getopt DBus i18n DHCP TFTP conntrack IDN
May 27 12:49:50 wubuntu dnsmasq[6675]: using nameserver 192.168.1.1#53
May 27 12:49:50 wubuntu avahi-daemon[955]: Joining mDNS multicast group on interface eth0.IPv6 with address fe80::21f:c6ff:fecf:90b8.
May 27 12:49:50 wubuntu avahi-daemon[955]: New relevant interface eth0.IPv6 for mDNS.
May 27 12:49:50 wubuntu avahi-daemon[955]: Registering new address record for fe80::21f:c6ff:fecf:90b8 on eth0.*.
May 27 12:49:50 wubuntu NetworkManager[943]: <info> (eth0): device state change: ip-config -> activated (reason 'none') [70 100 0]
May 27 12:49:50 wubuntu NetworkManager[943]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
May 27 12:49:50 wubuntu NetworkManager[943]: <info> Activation (eth0) successful, device activated.
May 27 12:49:50 wubuntu NetworkManager[943]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) complete.
May 27 12:49:50 wubuntu dbus[787]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
May 27 12:49:51 wubuntu dbus[787]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
May 27 12:49:59 wubuntu kernel: [22502.928044] eth0: no IPv6 routers present
May 27 12:49:59 wubuntu ntpdate[6743]: adjust time server 91.189.94.4 offset -0.219808 sec
May 27 12:50:08 wubuntu NetworkManager[943]: <info> (eth0): IP6 addrconf timed out or failed.
May 27 12:50:08 wubuntu NetworkManager[943]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
May 27 12:50:08 wubuntu NetworkManager[943]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) started...
May 27 12:50:08 wubuntu NetworkManager[943]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) complete.

```

---

### Post by borikanes on 2012-06-03
Hey everyone,
  I tried a script posted somewhere online but it didn't work for me. I have a HP envy.  For the the script posted on #19 what is the XXXX:xx:xx:x??? how do I get that info from my computer. Thanks for your help!!

---

### Post by Todd S. on 2012-08-07
This worked like a charm under *buntu 10.x and 11.x, but no longer seems to work on 12.x. It even worked on my Arch Linux install. It's really very annoying, as I'm going to have to spend a great deal of time getting my Arch to work like I want it now. I had gone back to Xubuntu thinking everything would "just work", and for the most part it does, but a laptop that won't suspend is not really fulfilling its purpose in life.

---

### Post by marcelloconti on 2012-08-12
Work on Sony Vaio VGN-NW380F, ubuntu 12.04 LTS

---

### Post by vickycq on 2012-09-06
Thank you so much man! This solution worked perfectly on my Asus U32U.

---

### Post by WartinC on 2012-10-18
Thanks!!

Brocktice's script (msg #19) did the trick in Ubuntu 12.04. 

Don't forget to give it execution permissions, as someone said.

My netbook is a CX 30601, it doesn't have USB 3.0.

---

