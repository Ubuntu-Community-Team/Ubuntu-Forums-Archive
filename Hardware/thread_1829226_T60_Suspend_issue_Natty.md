---
title: "T60 Suspend issue Natty"
date: 2011-08-20
forum: Hardware
---

### Post by dherkes on 2011-08-20
When I suspend my T60, either by closing the lid, or manually, it does not wake right back up.  Immediately after waking it goes back to sleep.  It does not seem to matter if the machine in on A/C or battery.  I have to press the power button to keep it awake.  Anyone else having this issue?

---

### Post by Toz on 2011-08-20
Welcome to the forums.

When you say "suspend manually", do you mean by issuing the **sudo pm-suspend** command?

Can you post back, right after a suspend attempt, the contents of **/var/log/pm-suspend.log** and the results of the two following commands:
```
lsmod
cat /var/log/syslog | grep "PM:"

```

---

### Post by dherkes on 2011-08-20
lsmod
Module                  Size  Used by
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
ipt_REJECT             12512  1 
xt_comment             12456  2 
ipt_LOG                12784  5 
xt_multiport           12533  2 
rfcomm                 38125  8 
sco                    17827  2 
xt_limit               12541  7 
xt_tcpudp              12531  15 
ipt_addrtype           12535  4 
bnep                   17785  2 
xt_state               12514  7 
l2cap                  48656  16 rfcomm,bnep
ip6table_filter        12711  1 
ip6_tables             22545  1 ip6table_filter
snd_hda_codec_analog    75442  1 
nf_nat_irc             12542  0 
nf_conntrack_irc       13138  1 nf_nat_irc
thinkpad_acpi          73750  1 
nf_nat_ftp             12548  0 
snd_hda_intel          24113  3 
snd_seq_midi           13132  0 
nf_nat                 24827  2 nf_nat_irc,nf_nat_ftp
joydev                 17322  0 
snd_hda_codec          90901  2 snd_hda_codec_analog,snd_hda_intel
pcmcia                 39671  0 
i915                  451033  2 
nf_conntrack_ipv4      19024  9 nf_nat
snd_rawmidi            25269  1 snd_seq_midi
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
nsc_ircc               23199  0 
drm_kms_helper         40745  1 i915
snd_hwdep              13274  1 snd_hda_codec
snd_seq_midi_event     14475  1 snd_seq_midi
nf_conntrack_ftp       13106  1 nf_nat_ftp
snd_pcm                80042  2 snd_hda_intel,snd_hda_codec
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
drm                   184164  3 i915,drm_kms_helper
arc4                   12473  2 
irda                  185091  1 nsc_ircc
nf_conntrack           69744  7 xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
yenta_socket           27230  0 
snd_timer              28659  2 snd_pcm,snd_seq
pcmcia_rsrc            18292  1 yenta_socket
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
btusb                  18160  2 
i2c_algo_bit           13184  1 i915
bluetooth              65493  9 rfcomm,sco,bnep,l2cap,btusb
snd                    55295  18 snd_hda_codec_analog,thinkpad_acpi,snd_hda_intel,snd_hda_codec,snd_rawmidi,snd_hwdep,snd_pcm,snd_seq,snd_timer,snd_seq_device
psmouse                73312  0 
crc_ccitt              12595  1 irda
serio_raw              12990  0 
tpm_tis                13993  0 
soundcore              12600  1 snd
iptable_filter         12706  1 
ath5k                 144534  0 
ath                    19141  1 ath5k
video                  18951  1 i915
mac80211              257001  1 ath5k
nvram                  14035  1 thinkpad_acpi
tpm                    21251  1 tpm_tis
tpm_bios               13460  1 tpm
ip_tables              18125  1 iptable_filter
cfg80211              156212  3 ath5k,ath,mac80211
x_tables               21907  12 ipt_REJECT,xt_comment,ipt_LOG,xt_multiport,xt_limit,xt_tcpudp,ipt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
ahci                   21591  2 
libahci                25548  1 ahci
e1000e                138627  0

cat /var/log/pm-suspend |grep "PM"

Aug 20 16:37:57 ThinkPad-T60 kernel: [30947.958211] PM: resume of devices complete after 1068.508 msecs
Aug 20 16:37:57 ThinkPad-T60 kernel: [30947.958424] PM: resume devices took 1.068 seconds
Aug 20 16:37:57 ThinkPad-T60 kernel: [30947.958497] PM: Finishing wakeup.
Aug 20 16:39:25 ThinkPad-T60 kernel: [31029.287585] PM: Syncing filesystems ... done.
Aug 20 16:39:25 ThinkPad-T60 kernel: [31029.412036] PM: Preparing system for mem sleep
Aug 20 16:39:25 ThinkPad-T60 kernel: [31029.444121] PM: Entering mem sleep
Aug 20 16:39:25 ThinkPad-T60 kernel: [31029.598760] PM: suspend of drv:psmouse dev:serio2 complete after 154.130 msecs
Aug 20 16:39:25 ThinkPad-T60 kernel: [31029.812025] PM: suspend of drv:HDA Intel dev:0000:00:1b.0 complete after 119.041 msecs
Aug 20 16:39:25 ThinkPad-T60 kernel: [31030.006497] PM: suspend of drv:sd dev:2:0:0:0 complete after 407.585 msecs
Aug 20 16:39:25 ThinkPad-T60 kernel: [31030.006507] PM: suspend of drv:scsi dev:target2:0:0 complete after 407.550 msecs
Aug 20 16:39:25 ThinkPad-T60 kernel: [31030.006515] PM: suspend of drv:scsi dev:host2 complete after 407.453 msecs
Aug 20 16:39:25 ThinkPad-T60 kernel: [31030.020032] PM: suspend of drv:ahci dev:0000:00:1f.2 complete after 327.311 msecs
Aug 20 16:39:25 ThinkPad-T60 kernel: [31030.020042] PM: suspend of drv: dev:pci0000:00 complete after 326.115 msecs
Aug 20 16:39:25 ThinkPad-T60 kernel: [31030.020049] PM: suspend of devices complete after 575.546 msecs
Aug 20 16:39:25 ThinkPad-T60 kernel: [31030.020051] PM: suspend devices took 0.576 seconds
Aug 20 16:39:25 ThinkPad-T60 kernel: [31030.072346] PM: late suspend of devices complete after 52.290 msecs
Aug 20 16:39:25 ThinkPad-T60 kernel: [31030.252050] PM: Saving platform NVS memory
Aug 20 16:39:25 ThinkPad-T60 kernel: [31030.252099] PM: Restoring platform NVS memory
Aug 20 16:39:25 ThinkPad-T60 kernel: [31030.701624] PM: early resume of devices complete after 21.583 msecs
Aug 20 16:39:25 ThinkPad-T60 kernel: [31030.876115] PM: resume of drv:usb dev:usb2 complete after 116.651 msecs
Aug 20 16:39:25 ThinkPad-T60 kernel: [31030.876144] PM: resume of drv:usb dev:usb3 complete after 116.663 msecs
Aug 20 16:39:25 ThinkPad-T60 kernel: [31030.876171] PM: resume of drv:usb dev:usb4 complete after 116.672 msecs
Aug 20 16:39:25 ThinkPad-T60 kernel: [31030.876198] PM: resume of drv:usb dev:usb5 complete after 116.679 msecs
Aug 20 16:39:25 ThinkPad-T60 kernel: [31030.876212] PM: resume of drv:hub dev:2-0:1.0 complete after 116.742 msecs
Aug 20 16:39:25 ThinkPad-T60 kernel: [31030.876224] PM: resume of drv: dev:ep_00 complete after 116.746 msecs
Aug 20 16:39:25 ThinkPad-T60 kernel: [31030.876233] PM: resume of drv:hub dev:3-0:1.0 complete after 116.745 msecs
Aug 20 16:39:25 ThinkPad-T60 kernel: [31030.876244] PM: resume of drv: dev:ep_00 complete after 116.749 msecs
Aug 20 16:39:25 ThinkPad-T60 kernel: [31030.876253] PM: resume of drv:hub dev:4-0:1.0 complete after 116.747 msecs
Aug 20 16:39:25 ThinkPad-T60 kernel: [31030.876264] PM: resume of drv: dev:ep_00 complete after 116.750 msecs
Aug 20 16:39:25 ThinkPad-T60 kernel: [31030.876274] PM: resume of drv:hub dev:5-0:1.0 complete after 116.749 msecs
Aug 20 16:39:25 ThinkPad-T60 kernel: [31030.876285] PM: resume of drv: dev:ep_00 complete after 116.752 msecs
Aug 20 16:39:25 ThinkPad-T60 kernel: [31030.876294] PM: resume of drv: dev:ep_81 complete after 116.821 msecs
Aug 20 16:39:25 ThinkPad-T60 kernel: [31030.876303] PM: resume of drv: dev:ep_81 complete after 116.811 msecs
Aug 20 16:39:25 ThinkPad-T60 kernel: [31030.876312] PM: resume of drv: dev:ep_81 complete after 116.802 msecs
Aug 20 16:39:25 ThinkPad-T60 kernel: [31030.876321] PM: resume of drv: dev:ep_81 complete after 116.792 msecs
Aug 20 16:39:25 ThinkPad-T60 kernel: [31030.904126] PM: resume of drv:usb dev:usb1 complete after 144.973 msecs
Aug 20 16:39:25 ThinkPad-T60 kernel: [31030.904141] PM: resume of drv:hub dev:1-0:1.0 complete after 144.691 msecs
Aug 20 16:39:25 ThinkPad-T60 kernel: [31030.904152] PM: resume of drv: dev:ep_00 complete after 144.695 msecs
Aug 20 16:39:25 ThinkPad-T60 kernel: [31030.904161] PM: resume of drv: dev:ep_81 complete after 144.708 msecs
Aug 20 16:39:25 ThinkPad-T60 kernel: [31031.680640] PM: resume of drv:sd dev:2:0:0:0 complete after 921.062 msecs
Aug 20 16:39:25 ThinkPad-T60 kernel: [31031.680657] PM: resume of drv:scsi_device dev:2:0:0:0 complete after 921.055 msecs
Aug 20 16:39:25 ThinkPad-T60 kernel: [31031.680668] PM: resume of drv:scsi_disk dev:2:0:0:0 complete after 856.896 msecs
Aug 20 16:39:25 ThinkPad-T60 kernel: [31031.820097] PM: resume of drv:pcmcia_socket dev:pcmcia_socket0 complete after 139.262 msecs
Aug 20 16:39:25 ThinkPad-T60 kernel: [31031.822208] PM: resume of devices complete after 1120.478 msecs
Aug 20 16:39:25 ThinkPad-T60 kernel: [31031.822417] PM: resume devices took 1.120 seconds
Aug 20 16:39:25 ThinkPad-T60 kernel: [31031.822491] PM: Finishing wakeup.
Aug 20 16:39:36 ThinkPad-T60 kernel: [31038.926069] PM: Syncing filesystems ... done.
Aug 20 16:39:36 ThinkPad-T60 kernel: [31039.152041] PM: Preparing system for mem sleep
Aug 20 16:39:36 ThinkPad-T60 kernel: [31039.184117] PM: Entering mem sleep
Aug 20 16:39:36 ThinkPad-T60 kernel: [31039.332234] PM: suspend of drv:psmouse dev:serio2 complete after 147.615 msecs
Aug 20 16:39:36 ThinkPad-T60 kernel: [31039.548018] PM: suspend of drv:HDA Intel dev:0000:00:1b.0 complete after 119.046 msecs
Aug 20 16:39:36 ThinkPad-T60 kernel: [31039.734607] PM: suspend of drv:sd dev:2:0:0:0 complete after 402.222 msecs
Aug 20 16:39:36 ThinkPad-T60 kernel: [31039.734617] PM: suspend of drv:scsi dev:target2:0:0 complete after 402.182 msecs
Aug 20 16:39:36 ThinkPad-T60 kernel: [31039.734625] PM: suspend of drv:scsi dev:host2 complete after 402.095 msecs
Aug 20 16:39:36 ThinkPad-T60 kernel: [31039.748020] PM: suspend of drv:ahci dev:0000:00:1f.2 complete after 319.307 msecs
Aug 20 16:39:36 ThinkPad-T60 kernel: [31039.748029] PM: suspend of drv: dev:pci0000:00 complete after 318.115 msecs
Aug 20 16:39:36 ThinkPad-T60 kernel: [31039.748036] PM: suspend of devices complete after 563.543 msecs
Aug 20 16:39:36 ThinkPad-T60 kernel: [31039.748039] PM: suspend devices took 0.564 seconds
Aug 20 16:39:36 ThinkPad-T60 kernel: [31039.800342] PM: late suspend of devices complete after 52.299 msecs
Aug 20 16:39:36 ThinkPad-T60 kernel: [31039.980048] PM: Saving platform NVS memory
Aug 20 16:39:36 ThinkPad-T60 kernel: [31039.980097] PM: Restoring platform NVS memory
Aug 20 16:39:36 ThinkPad-T60 kernel: [31040.325624] PM: early resume of devices complete after 21.583 msecs
Aug 20 16:39:36 ThinkPad-T60 kernel: [31040.504118] PM: resume of drv:usb dev:usb2 complete after 119.884 msecs
Aug 20 16:39:36 ThinkPad-T60 kernel: [31040.504147] PM: resume of drv:usb dev:usb3 complete after 119.895 msecs
Aug 20 16:39:36 ThinkPad-T60 kernel: [31040.504173] PM: resume of drv:usb dev:usb4 complete after 119.904 msecs
Aug 20 16:39:36 ThinkPad-T60 kernel: [31040.504199] PM: resume of drv:usb dev:usb5 complete after 119.912 msecs
Aug 20 16:39:36 ThinkPad-T60 kernel: [31040.504214] PM: resume of drv:hub dev:2-0:1.0 complete after 119.975 msecs
Aug 20 16:39:36 ThinkPad-T60 kernel: [31040.504225] PM: resume of drv: dev:ep_00 complete after 119.979 msecs
Aug 20 16:39:36 ThinkPad-T60 kernel: [31040.504235] PM: resume of drv:hub dev:3-0:1.0 complete after 119.977 msecs
Aug 20 16:39:36 ThinkPad-T60 kernel: [31040.504246] PM: resume of drv: dev:ep_00 complete after 119.981 msecs
Aug 20 16:39:36 ThinkPad-T60 kernel: [31040.504255] PM: resume of drv:hub dev:4-0:1.0 complete after 119.980 msecs
Aug 20 16:39:36 ThinkPad-T60 kernel: [31040.504266] PM: resume of drv: dev:ep_00 complete after 119.983 msecs
Aug 20 16:39:36 ThinkPad-T60 kernel: [31040.504275] PM: resume of drv:hub dev:5-0:1.0 complete after 119.982 msecs
Aug 20 16:39:36 ThinkPad-T60 kernel: [31040.504287] PM: resume of drv: dev:ep_00 complete after 119.985 msecs
Aug 20 16:39:36 ThinkPad-T60 kernel: [31040.504296] PM: resume of drv: dev:ep_81 complete after 120.053 msecs
Aug 20 16:39:36 ThinkPad-T60 kernel: [31040.504305] PM: resume of drv: dev:ep_81 complete after 120.044 msecs
Aug 20 16:39:36 ThinkPad-T60 kernel: [31040.504314] PM: resume of drv: dev:ep_81 complete after 120.035 msecs
Aug 20 16:39:36 ThinkPad-T60 kernel: [31040.504323] PM: resume of drv: dev:ep_81 complete after 120.025 msecs
Aug 20 16:39:36 ThinkPad-T60 kernel: [31040.528125] PM: resume of drv:usb dev:usb1 complete after 144.291 msecs
Aug 20 16:39:36 ThinkPad-T60 kernel: [31040.528139] PM: resume of drv:hub dev:1-0:1.0 complete after 143.920 msecs
Aug 20 16:39:36 ThinkPad-T60 kernel: [31040.528150] PM: resume of drv: dev:ep_00 complete after 143.923 msecs
Aug 20 16:39:36 ThinkPad-T60 kernel: [31040.528160] PM: resume of drv: dev:ep_81 complete after 143.937 msecs
Aug 20 16:39:36 ThinkPad-T60 kernel: [31040.977626] PM: resume of drv:sd dev:2:0:0:0 complete after 593.280 msecs
Aug 20 16:39:36 ThinkPad-T60 kernel: [31040.977670] PM: resume of drv:scsi_device dev:2:0:0:0 complete after 593.298 msecs
Aug 20 16:39:36 ThinkPad-T60 kernel: [31040.977681] PM: resume of drv:scsi_disk dev:2:0:0:0 complete after 530.166 msecs
Aug 20 16:39:36 ThinkPad-T60 kernel: [31041.116098] PM: resume of drv:pcmcia_socket dev:pcmcia_socket0 complete after 138.241 msecs
Aug 20 16:39:36 ThinkPad-T60 kernel: [31041.118552] PM: resume of devices complete after 792.853 msecs
Aug 20 16:39:36 ThinkPad-T60 kernel: [31041.118763] PM: resume devices took 0.792 seconds
Aug 20 16:39:36 ThinkPad-T60 kernel: [31041.118836] PM: Finishing wakeup.

---

### Post by Toz on 2011-08-20
1. Have you tried suspending by opening a terminal window and typing in:
```
sudo pm-suspend
```
I would like to see if the issue is related to the lid event.

2. Can you post the contents of /var/log/pm-suspend.log for the same period of time as the above log?

---

### Post by Toz on 2011-08-20
And one more request. What does the following return (type at a terminal window)?
```
ps -ef | grep power-manager | grep -v grep
```

---

### Post by dherkes on 2011-08-21
> **Toz said:**
> And one more request. What does the following return (type at a terminal window)?
```
ps -ef | grep power-manager | grep -v grep
```

dherkes@ThinkPad-T60:~$ ps -ef | grep power-manager | grep -v grep
dherkes   1524     1  0 Aug20 ?        00:00:01 xfce4-power-manager --restart --sm-client-id 2dfd0a451-73f9-433a-98f1-4dd10cc1c221
dherkes   1533     1  0 Aug20 ?        00:00:01 gnome-power-manager

The first output came from "pm-suspend"

---

### Post by dherkes on 2011-08-21
> **Toz said:**
> And one more request. What does the following return (type at a terminal window)?
```
ps -ef | grep power-manager | grep -v grep
```

I removed the gnome-power-manager, and the problem stopped.

Thank you.

---

### Post by Toz on 2011-08-21
Thats good news. Can you please mark the thread as solved from the Thread Tools links above?

---

