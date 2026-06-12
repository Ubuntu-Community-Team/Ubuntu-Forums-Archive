---
title: "(Auto) Brightness control /flickering /dimming on Samsung"
date: 2015-03-31
forum: Hardware
---

### Post by bernovy on 2015-03-31
Dear Ubuntu community, I am posting here as I'm really hoping that someone can help me stop the screen brightness flickering on my Samsung XE700T. This post is a follow up from: [http://ubuntuforums.org/showthread.php?t=2216224&page=2&p=13246936#post13246936](http://ubuntuforums.org/showthread.php?t=2216224&page=2&p=13246936#post13246936) . 

The main problem I'm experiencing is that I cannot _physically_ affect the screen brightness on my slate as it seems to be automatically controlled by some kernel module / config file. 
[LIST]
[*]The brightness bar in power settings is functional. When I slide it left-right, I'm getting feedback but *it doesn't physically change the screen brightness.* 
[*]The Fn keys work and when I press them, a little rectangle pops up at the top right displaying the brightness level as I press the keys, but the keys *don't physically affect the brightness of the screen*. 
[*]Regardless of what commands I use in the terminal, the values in  /sys/class/backlight/intel_backlight change but the screen is not changing its *physical brightness level*. 
[/LIST]
 
I tried multiple Linux kernels without any luck. I am currently running 3.18.10 and I just downloaded 3.19.3 (I will install it and try it after I post this). The only Linux kernel which seems to somewhat stop the brightness flickering on my slate is 3.19.1 but it eats my battery (the gov is not as well optimised as 3.18, the CPU seems to stay a lot at 1700-2400MHz instead of 800 - 2400MHz like on 3.18.10).  So if possible, until 4.x comes out I would prefer to fix this problem on 3.18.x and any help from the community would be sincerely appreciated. Thank you very much! :KS

```
cat /proc/cmdline
BOOT_IMAGE=/vmlinuz-3.18.10-031810-generic root=/dev/mapper/ubuntu--vg-root ro acpi_osi=Linux quiet splash acpi_backlight=vendor vt.handoff=7
```

I'm now running on battery and my physical screen brightness is near near minimum despite the fact that the below values show it to be at maximum:
```
 /sys/class/backlight/intel_backlight
4648
4648
4648
```
(If I plug my slate into power supply, the physical screen brightness will increase a bit while the above values stay the same)

I only have 1 folder in:
```
ls /sys/class/backlight
intel_backlight
```

I added the necessary code lines to 
```
/usr/share/X11/xorg.conf.d/20-intel.conf
```

Xorg log output:
```
grep intel_backlight /var/log/Xorg.0.log[     7.553] (**) intel(0): Option "Backlight" "intel_backlight"
[     7.553] (**) intel(0): Found backlight control interface intel_backlight (type 'raw') for output eDP1
```

Currently loaded kernel modules:
```
lsmod
Module                  Size  Used by
ipt_MASQUERADE         12678  3 
nf_nat_masquerade_ipv4    13412  1 ipt_MASQUERADE
iptable_nat            12875  1 
nf_nat_ipv4            14267  1 iptable_nat
xt_CHECKSUM            12549  1 
iptable_mangle         12734  1 
bridge                109756  0 
stp                    12976  1 bridge
llc                    14441  2 stp,bridge
nvram                  14462  0 
msr                    12908  0 
ebtable_nat            12807  0 
ebtables               35359  1 ebtable_nat
nf_log_ipv6            12778  5 
xt_hl                  12521  6 
ip6t_rt                13537  3 
nf_conntrack_ipv6      18946  8 
nf_defrag_ipv6         35007  1 nf_conntrack_ipv6
ip6t_REJECT            12625  3 
nf_reject_ipv6         13523  1 ip6t_REJECT
nf_log_ipv4            12819  5 
nf_log_common          13425  2 nf_log_ipv4,nf_log_ipv6
dm_crypt               23456  1 
xt_LOG                 12690  10 
xt_limit               12711  13 
xt_tcpudp              12924  24 
xt_addrtype            12713  4 
nf_conntrack_ipv4      18953  10 
nf_defrag_ipv4         12758  1 nf_conntrack_ipv4
xt_conntrack           12760  17 
ipt_REJECT             12541  5 
nf_reject_ipv4         13183  1 ipt_REJECT
ip6table_filter        12815  1 
hid_sensor_gyro_3d     13324  0 
hid_sensor_accel_3d    13338  0 
ip6_tables             27504  1 ip6table_filter
hid_sensor_rotation    13444  0 
hid_sensor_magn_3d     13406  0 
hid_sensor_incl_3d     13324  0 
nf_conntrack_netbios_ns    12665  0 
hid_sensor_trigger     13134  10 hid_sensor_gyro_3d,hid_sensor_incl_3d,hid_sensor_accel_3d,hid_sensor_rotation,hid_sensor_magn_3d
industrialio_triggered_buffer    12882  5 hid_sensor_gyro_3d,hid_sensor_incl_3d,hid_sensor_accel_3d,hid_sensor_rotation,hid_sensor_magn_3d
kfifo_buf              13432  1 industrialio_triggered_buffer
nf_conntrack_broadcast    12589  1 nf_conntrack_netbios_ns
intel_rapl             19196  0 
industrialio           55454  8 hid_sensor_trigger,hid_sensor_gyro_3d,industrialio_triggered_buffer,hid_sensor_incl_3d,hid_sensor_accel_3d,hid_sensor_rotation,kfifo_buf,hid_sensor_magn_3d
nf_nat_ftp             12825  0 
hid_sensor_iio_common    14349  5 hid_sensor_gyro_3d,hid_sensor_incl_3d,hid_sensor_accel_3d,hid_sensor_rotation,hid_sensor_magn_3d
nf_nat                 26308  3 nf_nat_ftp,nf_nat_ipv4,nf_nat_masquerade_ipv4
x86_pkg_temp_thermal    14312  0 
intel_powerclamp       19099  0 
nf_conntrack_ftp       18715  1 nf_nat_ftp
coretemp               13638  0 
nf_conntrack          105684  10 nf_nat_ftp,nf_conntrack_netbios_ns,nf_nat,nf_nat_ipv4,xt_conntrack,nf_nat_masquerade_ipv4,nf_conntrack_broadcast,nf_conntrack_ftp,nf_conntrack_ipv4,nf_conntrack_ipv6
iptable_filter         12810  1 
ip_tables              27718  3 iptable_filter,iptable_mangle,iptable_nat
kvm_intel             149984  0 
x_tables               34102  17 ip6table_filter,xt_hl,xt_CHECKSUM,ip_tables,xt_tcpudp,ipt_MASQUERADE,xt_limit,xt_conntrack,xt_LOG,iptable_filter,ebtables,ip6t_rt,ipt_REJECT,iptable_mangle,ip6_tables,xt_addrtype,ip6t_REJECT
kvm                   475366  1 kvm_intel
crct10dif_pclmul       14268  0 
crc32_pclmul           13180  0 
ghash_clmulni_intel    13230  0 
dm_multipath           23188  0 
aesni_intel           169686  965 
snd_hda_codec_hdmi     52670  1 
aes_x86_64             17131  1 aesni_intel
lrw                    13323  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            14095  1 aesni_intel
snd_hda_codec_realtek    80467  1 
scsi_dh                14873  1 dm_multipath
ablk_helper            13597  1 aesni_intel
snd_hda_codec_generic    69995  1 snd_hda_codec_realtek
cryptd                 20531  484 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_hda_intel          30824  3 
uvcvideo               86723  0 
snd_hda_controller     31446  1 snd_hda_intel
videobuf2_vmalloc      13216  1 uvcvideo
serio_raw              13483  0 
snd_hda_codec         144641  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
videobuf2_memops       13362  1 videobuf2_vmalloc
snd_hwdep              17709  1 snd_hda_codec
videobuf2_core         51547  1 uvcvideo
v4l2_common            15715  1 videobuf2_core
snd_pcm               106273  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
videodev              163831  3 uvcvideo,v4l2_common,videobuf2_core
media                  22008  2 uvcvideo,videodev
snd_seq_midi           13564  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            31197  1 snd_seq_midi
arc4                   12573  2 
hid_multitouch         17657  0 
joydev                 17587  0 
iwldvm                243857  0 
btusb                  32691  0 
snd_seq                63540  2 snd_seq_midi_event,snd_seq_midi
mac80211              697212  1 iwldvm
ax88179_178a           23027  0 
usbnet                 44043  1 ax88179_178a
mii                    13981  2 usbnet,ax88179_178a
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
wacom                  82089  0 
snd_timer              30118  2 snd_pcm,snd_seq
hid_sensor_hub         19877  7 hid_sensor_trigger,hid_sensor_gyro_3d,hid_sensor_incl_3d,hid_sensor_accel_3d,hid_sensor_rotation,hid_sensor_magn_3d,hid_sensor_iio_common
iwlwifi               193813  1 iwldvm
snd                    84025  17 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
cfg80211              520257  3 iwlwifi,mac80211,iwldvm
soundcore              15091  2 snd,snd_hda_codec
mei_me                 19565  0 
mei                    88473  1 mei_me
lpc_ich                21176  0 
shpchp                 37216  0 
bnep                   23980  2 
rfcomm                 75066  8 
bluetooth             486890  22 bnep,btusb,rfcomm
mac_hid                13275  0 
tpm_infineon           17169  0 
parport_pc             32909  0 
ppdev                  17711  0 
lp                     17799  0 
parport                42481  3 lp,ppdev,parport_pc
nls_iso8859_1          12713  1 
uas                    22673  0 
usb_storage            67010  1 uas
hid_generic            12559  0 
usbhid                 53155  0 
hid                   110572  5 hid_multitouch,wacom,hid_generic,hid_sensor_hub,usbhid
i915                 1032047  3 
i2c_algo_bit           13564  1 i915
drm_kms_helper         99802  1 i915
drm                   323675  5 i915,drm_kms_helper
ahci                   34220  3 
libahci                32353  1 ahci
wmi                    19379  0 
video                  20649  1 i915
```

My rc.local:
```
cat /etc/rc.local 
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
echo 4000 > /sys/class/backlight/intel_backlight/brightness
fstrim /
exit 0
```

My grub:
```
cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT="0"
#GRUB_HIDDEN_TIMEOUT="0"
GRUB_HIDDEN_TIMEOUT_QUIET="true"
GRUB_TIMEOUT="3"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash video.use_native_backlight=1"
GRUB_CMDLINE_LINUX="acpi_osi=Linux"

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL="console"

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE="1920x1080"

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
GRUB_DISABLE_LINUX_UUID="true"

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

GRUB_DISABLE_OS_PROBER="true"
```

And for this error:
```
sudo modprobe samsung_laptop
modprobe: ERROR: could not insert 'samsung_laptop': No such device
```

I submitted the following bug reports (no answers to date):
[LIST]
[*][https://bugzilla.kernel.org/show_bug.cgi?id=95021](https://bugzilla.kernel.org/show_bug.cgi?id=95021) 
[*][https://bugs.launchpad.net/ubuntu/+source/linux-lts-utopic/+bug/1433410](https://bugs.launchpad.net/ubuntu/+source/linux-lts-utopic/+bug/1433410) 
[/LIST]

If it turns out that I can't control the brightness on my XE700T due to Linux kernel bugs, could someone please help me identify the config file or the module for auto-brightness as I would really like to disable it and stop the auto-flickering..It's unbelievably distracting and frustrating.
Also I'd be absolutely delighted if someone can please help me with some instructions on how to set my physical screen brightness to one stable level on startup. The command I have now in rc.local is not doing anything. Thank you!

---

