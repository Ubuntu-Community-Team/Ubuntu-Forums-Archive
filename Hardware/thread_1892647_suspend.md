---
title: "suspend"
date: 2011-12-08
forum: Hardware
---

### Post by FokkerCharlie on 2011-12-08
Hello!

I have Ubuntu 11.10 running on my Toshiba A660 (Core i7, Nvidia proprietary graphics) laptop working fine, apart from suspend.

About 1/3 times, suspend fails- the screen blanks, but keeps running- screen backlight stays on, and after a while the fan starts running quite fast.

I tried suspending from VT1, and no messages are generated.  I had a look at this page:
[https://wiki.ubuntu.com/DebuggingKernelSuspend](https://wiki.ubuntu.com/DebuggingKernelSuspend)

but it seems that it's about resume issues rather than suspend problems.

Any more suggestions on how to proceed?

Thanks in advance!
Charlie

---

### Post by Toz on 2011-12-08
Interesting that it works sometimes and not others. There has to be some difference between the times that it suspends successfully and times that it doesn't. 

There is a log file located at **/var/log/pm-suspend.log** that might be helpful. If you can initiate the suspend hang from a command prompt, you can enable enhanced debugging by:
```
$ sudo bash
# export PM_DEBUG=true
# pm-suspend
```
...then the **/var/log/pm-suspend.log** file will have more detail.

You might also find some clues in your syslog:
```
cat /var/log/syslog | grep PM:
```

Feel free to post back the contents of those log files if you want a second set of eyes to look at them.

---

### Post by bluexrider on 2011-12-08
bug report a regression issue

[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/863834](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/863834)

---

### Post by FokkerCharlie on 2011-12-12
Hi Toz

Thanks for this.  I am trying to recreate the problem and get a useful log, but my lappy's going through a phase of suspending correctly at the moment!  I'll post here when I have something to report.

Toz, I think that bug refers to a different issue.  Thanks all the same!

Charlie

---

### Post by FokkerCharlie on 2011-12-15
OK!

I went for ages doing suspends from the sudo bash terminal, and it worked fine every time.  When I tried another method (using hotkey, from a terminal or VT1) it failed, but the log doesn't seem to show anything interesting:

```
Initial commandline parameters: 
Tue Dec 13 23:20:01 AST 2011: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux charlie-Satellite-A660 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:28:43 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
usbhid                 47198  0 
hid                    95463  1 usbhid
usb_storage            57901  0 
uas                    18027  0 
arc4                   12529  0 
ppp_mppe               13077  0 
ipt_MASQUERADE         12759  0 
xt_state               12578  0 
ipt_REJECT             12576  0 
xt_tcpudp              12603  0 
iptable_filter         12810  0 
nf_nat_h323            17002  0 
nf_conntrack_h323      62913  1 nf_nat_h323
nf_nat_pptp            12629  0 
nf_conntrack_pptp      13830  1 nf_nat_pptp
nf_conntrack_proto_gre    13656  1 nf_conntrack_pptp
nf_nat_proto_gre       12767  1 nf_nat_pptp
nf_nat_tftp            12489  0 
nf_conntrack_tftp      12953  1 nf_nat_tftp
nf_nat_sip             17086  0 
nf_conntrack_sip       29730  1 nf_nat_sip
nf_nat_irc             12643  0 
nf_conntrack_irc       13383  1 nf_nat_irc
nf_nat_ftp             12704  0 
nf_conntrack_ftp       13452  1 nf_nat_ftp
iptable_nat            13229  0 
nf_nat                 25890  9 ipt_MASQUERADE,nf_nat_h323,nf_nat_pptp,nf_nat_proto_gre,nf_nat_tftp,nf_nat_sip,nf_nat_irc,nf_nat_ftp,iptable_nat
nf_conntrack_ipv4      19716  3 iptable_nat,nf_nat
nf_conntrack           82342  18 ipt_MASQUERADE,xt_state,nf_nat_h323,nf_conntrack_h323,nf_nat_pptp,nf_conntrack_pptp,nf_conntrack_proto_gre,nf_nat_tftp,nf_conntrack_tftp,nf_nat_sip,nf_conntrack_sip,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_conntrack_ftp,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
ip_tables              27473  2 iptable_filter,iptable_nat
x_tables               29846  7 ipt_MASQUERADE,xt_state,ipt_REJECT,xt_tcpudp,iptable_filter,iptable_nat,ip_tables
ppp_async              17539  0 
crc_ccitt              12667  1 ppp_async
mmc_block              22923  0 
ipx                    28556  0 
p8023                  12789  1 ipx
rfcomm                 47946  0 
bnep                   18436  2 
pci_stub               12622  1 
vboxpci                23200  0 
vboxnetadp             13382  0 
vboxnetflt             23441  0 
vboxdrv               282739  3 vboxpci,vboxnetadp,vboxnetflt
mceusb                 17906  0 
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
dm_crypt               23199  1 
snd_hda_codec_hdmi     32040  4 
snd_hda_codec_realtek   330769  1 
snd_hda_intel          33390  3 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
btusb                  18600  0 
bluetooth             166112  11 rfcomm,bnep,btusb
snd_hwdep              13668  1 snd_hda_codec
joydev                 17693  0 
snd_pcm                96714  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
uvcvideo               72711  1 
videodev               92992  2 uvcvideo
snd_seq_midi           13324  0 
v4l2_compat_ioctl32    17083  1 videodev
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
nvidia              11713772  52 
lib80211_crypt_tkip    17390  0 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
wl                   2568210  0 
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
ir_lirc_codec          12898  0 
lirc_dev               19204  1 ir_lirc_codec
psmouse                73882  0 
ir_sony_decoder        12549  0 
snd                    68266  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ir_jvc_decoder         12546  0 
serio_raw              13166  0 
i7core_edac            27942  0 
edac_core              53746  3 i7core_edac
lib80211               14991  2 lib80211_crypt_tkip,wl
ir_rc6_decoder         12546  0 
soundcore              12680  1 snd
ir_rc5_decoder         12546  0 
ir_nec_decoder         12546  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mei                    41480  0 
jmb38x_ms              17646  0 
memstick               16569  1 jmb38x_ms
rc_rc6_mce             12502  0 
toshiba_bluetooth      12807  0 
ene_ir                 22796  0 
rc_core                26963  10 mceusb,ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,rc_rc6_mce,ene_ir
sparse_keymap          13890  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
vesafb                 13809  1 
sdhci_pci              14032  0 
ahci                   26002  4 
sdhci                  32166  1 sdhci_pci
libahci                26861  1 ahci
r8169                  52788  0 
video                  19412  0 
             total       used       free     shared    buffers     cached
Mem:       8124760    7934996     189764          0      97552    5082456
-/+ buffers/cache:    2754988    5369772
Swap:      8787964      64220    8723744

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Sessions still open, not unmounting
Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting

/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
nVidia binary video drive detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Tue Dec 13 23:20:05 AST 2011: performing suspend
```

So, I'm most interested to know what's the difference in the two methods?  It's very odd!

Cheers
Charlie

---

### Post by Toz on 2011-12-16
That is odd.

Can you try getting more detailed logs using the procedure from post #2? And if you can provide a good log file as well as a bad one, it would be interesting to see what the differences are and possibly identify the issue.

Since it works when you execute it from a bash terminal, lets generate a good log file. From the bash terminal:
```
$ sudo bash
# export PM_DEBUG=true
# pm-suspend
```
...save the suspend.log file as the good file:
```
sudo mv /var/log/pm-suspend.log /var/log/suspend.log.good
```

Now for comparison's sake, lets get a log file from when you press the suspend hotkey. This is going to involve the editing of a system file:
```
sudo gedit /usr/lib/pm-utils/functions
```
...and add after the first two lines the following:
```
export PM_DEBUG=true
```
...so that the beginning of the file looks like this:
> 
#!/bin/sh
# vim:noexpandtab
export PM_DEBUG=true

...Save the file and press the suspend hotkey.

When you recover the system, post back the contents of the files:
- /var/log/pm-suspend.log.good
- /var/log/pm-suspend.log

When you're done, remember to go back and remove "export PM_DEBUG=true" from the **/usr/lib/pm-utils/functions** file so that you don't end up with large log files every time you suspend.

---

### Post by FokkerCharlie on 2011-12-18
Hi Toz

Thanks for your input on this.

Things have become stranger here.  Since an update a few days ago (didn't notice exactly what was included, but I was invited to reboot afterwards, so I'm guessing a kernel upgrade of some sort), suspending has been working, but resuming has not.  That applies to both the hotkey and bash-terminal method.

The logs are below, but it looks like they both end before the wakeup starts, so not that useful, I guess?

From the terminal first:

```
+ log Initial commandline parameters: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Initial commandline parameters:  = -n ]
+ printf %s\n Initial commandline parameters: 
Initial commandline parameters: 
+ load_hook_blacklist
+ [  ]
+ return
+ load_hook_parameters
+ [  ]
+ [  ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ date
+ log Sun Dec 18 13:33:45 AST 2011: Running hooks for suspend.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Sun Dec 18 13:33:45 AST 2011: Running hooks for suspend. = -n ]
+ printf %s\n Sun Dec 18 13:33:45 AST 2011: Running hooks for suspend.
Sun Dec 18 13:33:45 AST 2011: Running hooks for suspend.
+ run_hooks sleep suspend suspend
+ _run_hooks sleep suspend suspend
+ local syshooks=/etc/pm/sleep.d
+ local phooks=/usr/lib/pm-utils/sleep.d
+ command_exists before_hooks
+ type before_hooks
+ return 0
+ before_hooks
+ [ -z  ]
+ return 0
+ local sort=sort
+ local base
+ local hook
+ local oifs= 	

+ local nifs=

+ IFS=

+ [  = reverse ]
+ IFS= 	

+ sort
+ uniq
+ [ -O /etc/pm/sleep.d/10_grub-common ]
+ echo 10_grub-common
+ [ -O /etc/pm/sleep.d/10_unattended-upgrades-hibernate ]
+ echo 10_unattended-upgrades-hibernate
+ [ -O /etc/pm/sleep.d/novatel_3g_suspend ]
+ echo novatel_3g_suspend
+ [ -O /usr/lib/pm-utils/sleep.d/000kernel-change ]
+ echo 000kernel-change
+ [ -O /usr/lib/pm-utils/sleep.d/00logging ]
+ echo 00logging
+ [ -O /usr/lib/pm-utils/sleep.d/00powersave ]
+ echo 00powersave
+ [ -O /usr/lib/pm-utils/sleep.d/01PulseAudio ]
+ echo 01PulseAudio
+ [ -O /usr/lib/pm-utils/sleep.d/49bluetooth ]
+ echo 49bluetooth
+ [ -O /usr/lib/pm-utils/sleep.d/55NetworkManager ]
+ echo 55NetworkManager
+ [ -O /usr/lib/pm-utils/sleep.d/60_wpa_supplicant ]
+ echo 60_wpa_supplicant
+ [ -O /usr/lib/pm-utils/sleep.d/75modules ]
+ echo 75modules
+ [ -O /usr/lib/pm-utils/sleep.d/90clock ]
+ echo 90clock
+ [ -O /usr/lib/pm-utils/sleep.d/94cpufreq ]
+ echo 94cpufreq
+ [ -O /usr/lib/pm-utils/sleep.d/95anacron ]
+ echo 95anacron
+ [ -O /usr/lib/pm-utils/sleep.d/95hdparm-apm ]
+ echo 95hdparm-apm
+ [ -O /usr/lib/pm-utils/sleep.d/95led ]
+ echo 95led
+ [ -O /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler ]
+ echo 98video-quirk-db-handler
+ [ -O /usr/lib/pm-utils/sleep.d/99video ]
+ echo 99video
+ IFS= 	

+ [  -a  = reverse -a  ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/000kernel-change ]
+ [ -f /usr/lib/pm-utils/sleep.d/000kernel-change ]
+ hook=/usr/lib/pm-utils/sleep.d/000kernel-change
+ run_hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/000kernel-change
+ local hook=000kernel-change
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:000kernel-change ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:0kernel-change ]
+ [ -x /usr/lib/pm-utils/sleep.d/000kernel-change ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: 
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=000kernel-change
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 000kernel-change ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/00logging ]
+ [ -f /usr/lib/pm-utils/sleep.d/00logging ]
+ hook=/usr/lib/pm-utils/sleep.d/00logging
+ run_hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/00logging
+ local hook=00logging
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:00logging ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:logging ]
+ [ -x /usr/lib/pm-utils/sleep.d/00logging ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/00logging suspend suspend
+ [ -n /var/log/pm-suspend.log ]
+ /bin/uname -a
Linux charlie-Satellite-A660 3.0.0-15-generic #24-Ubuntu SMP Mon Dec 12 15:23:55 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
+ lsmod
Module                  Size  Used by
usb_storage            57901  0 
uas                    18027  0 
arc4                   12529  2 
ppp_mppe               13077  2 
ppp_async              17539  1 
crc_ccitt              12667  1 ppp_async
ipx                    28556  0 
p8023                  12789  1 ipx
bnep                   18436  2 
rfcomm                 47946  8 
pci_stub               12622  1 
vboxpci                23200  0 
vboxnetadp             13382  0 
vboxnetflt             23441  0 
vboxdrv               282739  3 vboxpci,vboxnetadp,vboxnetflt
mceusb                 17906  0 
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
dm_crypt               23199  1 
snd_hda_codec_hdmi     32040  4 
nvidia              11713772  52 
joydev                 17693  0 
snd_hda_codec_realtek   330769  1 
uvcvideo               72711  0 
videodev               92992  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
btusb                  18600  2 
bluetooth             166112  23 bnep,rfcomm,btusb
snd_hda_intel          33390  3 
snd_hda_codec         104931  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
psmouse                73882  0 
serio_raw              13166  0 
snd_pcm                96714  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
lib80211_crypt_tkip    17390  0 
i7core_edac            27942  0 
edac_core              53746  3 i7core_edac
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
wl                   2568210  0 
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
jmb38x_ms              17646  0 
snd                    68266  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
memstick               16569  1 jmb38x_ms
lib80211               14991  2 lib80211_crypt_tkip,wl
mei                    41480  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
sparse_keymap          13890  0 
ir_lirc_codec          12898  0 
lirc_dev               19204  1 ir_lirc_codec
ir_sony_decoder        12549  0 
ir_jvc_decoder         12546  0 
ir_rc6_decoder         12546  0 
ir_rc5_decoder         12546  0 
toshiba_bluetooth      12807  0 
ir_nec_decoder         12546  0 
rc_rc6_mce             12502  0 
ene_ir                 22796  0 
rc_core                26963  10 mceusb,ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,rc_rc6_mce,ene_ir
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47198  0 
hid                    95463  1 usbhid
vesafb                 13809  1 
ahci                   26002  4 
libahci                26861  1 ahci
sdhci_pci              14032  0 
sdhci                  32166  1 sdhci_pci
r8169                  52788  0 
video                  19412  0 
+ free
             total       used       free     shared    buffers     cached
Mem:       8124724    6484728    1639996          0      24212    5140836
-/+ buffers/cache:    1319680    6805044
Swap:      8787964         16    8787948
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/00logging suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/00logging suspend suspend: 
/usr/lib/pm-utils/sleep.d/00logging suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=00logging
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 00logging ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/00powersave ]
+ [ -f /usr/lib/pm-utils/sleep.d/00powersave ]
+ hook=/usr/lib/pm-utils/sleep.d/00powersave
+ run_hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/00powersave
+ local hook=00powersave
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:00powersave ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:powersave ]
+ [ -x /usr/lib/pm-utils/sleep.d/00powersave ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/00powersave suspend suspend
+ command_exists pm-powersave
+ type pm-powersave
+ return 0
+ pm-powersave false
+ set -a
+ PM_UTILS_LIBDIR=/usr/lib/pm-utils
+ PM_UTILS_ETCDIR=/etc/pm
+ PM_UTILS_RUNDIR=/var/run/pm-utils
+ PATH=/sbin:/usr/sbin:/bin:/usr/bin:/usr/lib/pm-utils/bin
+ PM_LOGFILE=/var/log/pm-powersave.log
+ TEMPORARY_CPUFREQ_GOVERNOR=performance
+ LOCKDIR=/var/run/pm-utils/locks
+ STORAGEDIR=/var/run/pm-utils/pm-powersave/storage
+ NA=254
+ NX=253
+ DX=252
+ PM_FUNCTIONS=/usr/lib/pm-utils/functions
+ PM_QUIRKDB=/usr/lib/pm-utils/video-quirks
+ PM_LKW_QUIRKS=/var/cache/pm-utils/last_known_working.quirkdb
+ LC_COLLATE=C
+ HIBERNATE_MODE=
+ HIBERNATE_RESUME_POST_VIDEO=no
+ SLEEP_MODULE=auto
+ SUSPEND_MODULES=
+ HOOK_BLACKLIST=
+ ADD_PARAMETERS=
+ DROP_PARAMETERS=
+ PARAMETERS=/var/run/pm-utils/pm-powersave/storage/parameters
+ INHIBIT=/var/run/pm-utils/pm-powersave/storage/inhibit
+ PM_CMDLINE=false
+ BEFORE_HOOKS=
+ MODULE_HELP=
+ SUSPEND_MODULE=
+ HIBERNATE_MODULE=
+ SUSPEND_HYBRID_MODULE=
+ PM_HIBERNATE_DELAY=900
+ PM_RTC=/sys/class/rtc/rtc0
+ [ -f /usr/lib/pm-utils/defaults ]
+ . /usr/lib/pm-utils/defaults
+ [ -f /usr/lib/pm-utils/pm-powersave.defaults ]
+ set +a
+ [ -f /etc/pm/config.d/*[!~] ]
+ continue
+ [ -f /etc/pm/pm-powersave.config.d/*[!~] ]
+ continue
+ . /usr/lib/pm-utils/functions
+ is_set true
+ return 0
+ set -x
+ profiling
+ [  = true ]
+ profiling
+ [  = true ]
+ profiling
+ [  = true ]
+ [ auto = auto ]
+ SLEEP_MODULE=tuxonice uswsusp
+ mod=/usr/lib/pm-utils/module.d/tuxonice
+ [ -f /usr/lib/pm-utils/module.d/tuxonice ]
+ . /usr/lib/pm-utils/module.d/tuxonice
+ export TUXONICE_LOC
+ [ -d /sys/power/tuxonice ]
+ [ -d /sys/power/suspend2 ]
+ [ -n  ]
+ [ -z  -a -n  ]
+ [ -z  -a -n  ]
+ mod=/usr/lib/pm-utils/module.d/uswsusp
+ [ -f /usr/lib/pm-utils/module.d/uswsusp ]
+ . /usr/lib/pm-utils/module.d/uswsusp
+ [ -z  ]
+ command_exists s2ram
+ type s2ram
+ return 127
+ [ -z  ]
+ [ -f /sys/power/disk ]
+ grep -q disk /sys/power/state
+ [ -c /dev/snapshot ]
+ command_exists s2disk
+ type s2disk
+ return 127
+ [ -z  ]
+ grep -q mem /sys/power/state
+ command_exists s2both
+ type s2both
+ return 127
+ [ -z  ]
+ grep -q mem /sys/power/state
+ SUSPEND_MODULE=kernel
+ [ -z  ]
+ [ -f /sys/power/disk ]
+ grep -q disk /sys/power/state
+ HIBERNATE_MODULE=kernel
+ [ -z  -a -w /sys/class/rtc/rtc0/wakealarm ]
+ check_suspend
+ [ -n kernel ]
+ check_hibernate
+ [ -n kernel ]
+ is_set no
+ return 1
+ SUSPEND_HYBRID_MODULE=kernel
+ lock_and_load
+ try_lock pm-powersave.lock
+ local lock=/var/run/pm-utils/locks/pm-powersave.lock
+ mkdir -p /var/run/pm-utils/locks
+ touch /var/run/pm-utils/locks/pm-powersave.lock
+ exec
+ flock -x -n 3
+ return 0
+ trap remove_powersave_lock 0
+ mkdir -p /var/run/pm-utils/pm-powersave/storage
+ rm -f /var/run/pm-utils/pm-powersave/storage/inhibit
+ load_hook_blacklist
+ [  ]
+ return
+ init_logfile /var/log/pm-powersave.log
+ [ -z /var/log/pm-powersave.log ]
+ [ -h /var/log/pm-powersave.log ]
+ [ -f /var/log/pm-powersave.log -a ! -O /var/log/pm-powersave.log ]
+ export LOGGING=true
+ exec
+ exit 0
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/00powersave suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/00powersave suspend suspend: 
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=00powersave
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 00powersave ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/01PulseAudio ]
+ [ -f /usr/lib/pm-utils/sleep.d/01PulseAudio ]
+ hook=/usr/lib/pm-utils/sleep.d/01PulseAudio
+ run_hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/01PulseAudio
+ local hook=01PulseAudio
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:01PulseAudio ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:PulseAudio ]
+ [ -x /usr/lib/pm-utils/sleep.d/01PulseAudio ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend
+ suspend_pulse
+ get_pulse_users
+ test_pulse_system
+ getent passwd pulse
+ awk -F: {print $3}
+ PULSE_SYSTEM_USER=109
+ [ -z 109 ]
+ ps -C pulseaudio -o uid=
+ tr -d  
+ sed s/109//
+ getent passwd 1000
+ cut -f1 -d:
+ THIS_USER=charlie
+ save_pulse_state sink charlie
+ su charlie -c -- pacmd list-sinks
+ sed -n s/^[[:space:]*]*//; /\(index\|mute\)/p
+ index=
+ read field value
Sessions still open, not unmounting
+ [ index = index ]
+ index=0
+ read field value
+ [ muted = index ]
+ savestate pulse:charlie:sink0 no
+ [ -n no ]
+ echo no
+ read field value
+ [ index = index ]
+ index=1
+ read field value
+ [ muted = index ]
+ savestate pulse:charlie:sink1 no
+ [ -n no ]
+ echo no
+ read field value
+ save_pulse_state source charlie
+ su charlie -c -- pacmd list-sources
+ + index=
sed -n+  s/^[[:space:]*]*//; /\(index\|mute\)/p
read field value
Sessions still open, not unmounting
+ [ index = index ]
+ index=0
+ read field value
+ [ muted = index ]
+ savestate pulse:charlie:source0 yes
+ [ -n yes ]
+ echo yes
+ read field value
+ [ index = index ]
+ index=1
+ read field value
+ [ muted = index ]
+ savestate pulse:charlie:source1 yes
+ [ -n yes ]
+ echo yes
+ read field value
+ [ index = index ]
+ index=2
+ read field value
+ [ muted = index ]
+ savestate pulse:charlie:source2 yes
+ [ -n yes ]
+ echo yes
+ read field value
+ su charlie -c -- pacmd suspend true
+ get_pulse_users
+ test_pulse_system
+ getent passwd pulse
+ awk -F: {print $3}
+ PULSE_SYSTEM_USER=109
+ [ -z 109 ]
+ ps -C pulseaudio -o uid=
+ + tr -d  
sed s/109//
+ getent passwd 1000
+ cut -f1 -d:
+ THIS_USER=charlie
+ su charlie -c -- ck-list-sessions | grep "active = TRUE"
+ mute_pulse sink charlie
+ su+  charlie -c -- pacmd list-sinkssed
 -n+  s/^[[:space:]*]*//; /\(index\|mute\)/p
index=
+ read field value
Sessions still open, not unmounting
+ [ index = index ]
+ index=0
+ su charlie -c -- pacmd                         set-sink-mute 0 yes
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
+ read field value
+ [ muted = index ]
+ read field value
+ [ index = index ]
+ index=1
+ su charlie -c -- pacmd                         set-sink-mute 1 yes
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
+ read field value
+ [ muted = index ]
+ read field value
+ mute_pulse source charlie
+ su charlie -c -- pacmd list-sources
+ sed -n+  s/^[[:space:]*]*//; /\(index\|mute\)/p
index=
+ read field value
Sessions still open, not unmounting
+ [ index = index ]
+ index=0
+ su charlie -c -- pacmd                         set-source-mute 0 yes
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
+ read field value
+ [ muted = index ]
+ read field value
+ [ index = index ]
+ index=1
+ su charlie -c -- pacmd                         set-source-mute 1 yes
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
+ read field value
+ [ muted = index ]
+ read field value
+ [ index = index ]
+ index=2
+ su charlie -c -- pacmd                         set-source-mute 2 yes
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
+ read field value
+ [ muted = index ]
+ read field value
+ break
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=01PulseAudio
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 01PulseAudio ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/10_grub-common ]
+ hook=/etc/pm/sleep.d/10_grub-common
+ run_hook /etc/pm/sleep.d/10_grub-common suspend suspend
+ _run_hook /etc/pm/sleep.d/10_grub-common suspend suspend
+ log Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /etc/pm/sleep.d/10_grub-common suspend suspend: = -n ]
+ printf %s\n Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
+ hook_ok /etc/pm/sleep.d/10_grub-common
+ local hook=10_grub-common
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:10_grub-common ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:_grub-common ]
+ [ -x /etc/pm/sleep.d/10_grub-common ]
+ return 0
+ /etc/pm/sleep.d/10_grub-common suspend suspend
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /etc/pm/sleep.d/10_grub-common suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /etc/pm/sleep.d/10_grub-common suspend suspend: 
/etc/pm/sleep.d/10_grub-common suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=10_grub-common
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 10_grub-common ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/10_unattended-upgrades-hibernate ]
+ hook=/etc/pm/sleep.d/10_unattended-upgrades-hibernate
+ run_hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend
+ _run_hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend
+ log Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: = -n ]
+ printf %s\n Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
+ hook_ok /etc/pm/sleep.d/10_unattended-upgrades-hibernate
+ local hook=10_unattended-upgrades-hibernate
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:10_unattended-upgrades-hibernate ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:_unattended-upgrades-hibernate ]
+ [ -x /etc/pm/sleep.d/10_unattended-upgrades-hibernate ]
+ return 0
+ /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: 
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=10_unattended-upgrades-hibernate
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 10_unattended-upgrades-hibernate ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/49bluetooth ]
+ [ -f /usr/lib/pm-utils/sleep.d/49bluetooth ]
+ hook=/usr/lib/pm-utils/sleep.d/49bluetooth
+ run_hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/49bluetooth
+ local hook=49bluetooth
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:49bluetooth ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:bluetooth ]
+ [ -x /usr/lib/pm-utils/sleep.d/49bluetooth ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend
+ [ -f /proc/acpi/ibm/bluetooth ]
+ exit 254
+ local status=254
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: 
/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: + hook_exit_status 254
+ log not applicable.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ not applicable. = -n ]
+ printf %s\n not applicable.
not applicable.
+ LAST_HOOK=49bluetooth
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 49bluetooth ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/55NetworkManager ]
+ [ -f /usr/lib/pm-utils/sleep.d/55NetworkManager ]
+ hook=/usr/lib/pm-utils/sleep.d/55NetworkManager
+ run_hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/55NetworkManager
+ local hook=55NetworkManager
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:55NetworkManager ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:NetworkManager ]
+ [ -x /usr/lib/pm-utils/sleep.d/55NetworkManager ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend
+ suspend_nm
+ printf Having NetworkManager put all interaces to sleep...
Having NetworkManager put all interaces to sleep...+ dbus_send --print-reply --system --dest=org.freedesktop.NetworkManager /org/freedesktop/NetworkManager org.freedesktop.NetworkManager.sleep
+ command dbus-send --print-reply --system --dest=org.freedesktop.NetworkManager /org/freedesktop/NetworkManager org.freedesktop.NetworkManager.sleep
+ return 254
+ echo Failed.
Failed.
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: 
/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=55NetworkManager
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 55NetworkManager ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/60_wpa_supplicant ]
+ [ -f /usr/lib/pm-utils/sleep.d/60_wpa_supplicant ]
+ hook=/usr/lib/pm-utils/sleep.d/60_wpa_supplicant
+ run_hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/60_wpa_supplicant
+ local hook=60_wpa_supplicant
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:60_wpa_supplicant ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:_wpa_supplicant ]
+ [ -x /usr/lib/pm-utils/sleep.d/60_wpa_supplicant ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend
Selected interface 'eth1'
OK
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: 
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=60_wpa_supplicant
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 60_wpa_supplicant ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/75modules ]
+ [ -f /usr/lib/pm-utils/sleep.d/75modules ]
+ hook=/usr/lib/pm-utils/sleep.d/75modules
+ run_hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/75modules
+ local hook=75modules
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:75modules ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:modules ]
+ [ -x /usr/lib/pm-utils/sleep.d/75modules ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/75modules suspend suspend
+ suspend_modules
+ [ -z  ]
+ return 254
+ local status=254
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/75modules suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/75modules suspend suspend: 
/usr/lib/pm-utils/sleep.d/75modules suspend suspend: + hook_exit_status 254
+ log not applicable.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ not applicable. = -n ]
+ printf %s\n not applicable.
not applicable.
+ LAST_HOOK=75modules
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 75modules ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/90clock ]
+ [ -f /usr/lib/pm-utils/sleep.d/90clock ]
+ hook=/usr/lib/pm-utils/sleep.d/90clock
+ run_hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/90clock
+ local hook=90clock
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:90clock ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:clock ]
+ [ -x /usr/lib/pm-utils/sleep.d/90clock ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/90clock suspend suspend
+ is_set 
+ return 2
+ exit 254
+ local status=254
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/90clock suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/90clock suspend suspend: 
/usr/lib/pm-utils/sleep.d/90clock suspend suspend: + hook_exit_status 254
+ log not applicable.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ not applicable. = -n ]
+ printf %s\n not applicable.
not applicable.
+ LAST_HOOK=90clock
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 90clock ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/94cpufreq ]
+ [ -f /usr/lib/pm-utils/sleep.d/94cpufreq ]
+ hook=/usr/lib/pm-utils/sleep.d/94cpufreq
+ run_hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/94cpufreq
+ local hook=94cpufreq
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:94cpufreq ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:cpufreq ]
+ [ -x /usr/lib/pm-utils/sleep.d/94cpufreq ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend
+ [ -d /sys/devices/system/cpu/ ]
+ hibernate_cpufreq
+ cd /sys/devices/system/cpu/
+ [ -L cpu0/cpufreq ]
+ gov=cpu0/cpufreq/scaling_governor
+ [ -f cpu0/cpufreq/scaling_governor ]
+ grep -q performance cpu0/cpufreq/scaling_available_governors
+ savestate cpu0_governor
+ [ -n  ]
+ cat
+ echo performance
+ [ -L cpu1/cpufreq ]
+ gov=cpu1/cpufreq/scaling_governor
+ [ -f cpu1/cpufreq/scaling_governor ]
+ grep -q performance cpu1/cpufreq/scaling_available_governors
+ savestate cpu1_governor
+ [ -n  ]
+ cat
+ echo performance
+ [ -L cpu2/cpufreq ]
+ gov=cpu2/cpufreq/scaling_governor
+ [ -f cpu2/cpufreq/scaling_governor ]
+ grep -q performance cpu2/cpufreq/scaling_available_governors
+ savestate cpu2_governor
+ [ -n  ]
+ cat
+ echo performance
+ [ -L cpu3/cpufreq ]
+ gov=cpu3/cpufreq/scaling_governor
+ [ -f cpu3/cpufreq/scaling_governor ]
+ grep -q performance cpu3/cpufreq/scaling_available_governors
+ savestate cpu3_governor
+ [ -n  ]
+ cat
+ echo performance
+ [ -L cpu4/cpufreq ]
+ gov=cpu4/cpufreq/scaling_governor
+ [ -f cpu4/cpufreq/scaling_governor ]
+ grep -q performance cpu4/cpufreq/scaling_available_governors
+ savestate cpu4_governor
+ [ -n  ]
+ cat
+ echo performance
+ [ -L cpu5/cpufreq ]
+ gov=cpu5/cpufreq/scaling_governor
+ [ -f cpu5/cpufreq/scaling_governor ]
+ grep -q performance cpu5/cpufreq/scaling_available_governors
+ savestate cpu5_governor
+ [ -n  ]
+ cat
+ echo performance
+ [ -L cpu6/cpufreq ]
+ gov=cpu6/cpufreq/scaling_governor
+ [ -f cpu6/cpufreq/scaling_governor ]
+ grep -q performance cpu6/cpufreq/scaling_available_governors
+ savestate cpu6_governor
+ [ -n  ]
+ cat
+ echo performance
+ [ -L cpu7/cpufreq ]
+ gov=cpu7/cpufreq/scaling_governor
+ [ -f cpu7/cpufreq/scaling_governor ]
+ grep -q performance cpu7/cpufreq/scaling_available_governors
+ savestate cpu7_governor
+ [ -n  ]
+ cat
+ echo performance
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: 
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=94cpufreq
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 94cpufreq ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/95anacron ]
+ [ -f /usr/lib/pm-utils/sleep.d/95anacron ]
+ hook=/usr/lib/pm-utils/sleep.d/95anacron
+ run_hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/95anacron
+ local hook=95anacron
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:95anacron ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:anacron ]
+ [ -x /usr/lib/pm-utils/sleep.d/95anacron ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/95anacron suspend suspend
stop: Unknown instance: 
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/95anacron suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/95anacron suspend suspend: 
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=95anacron
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 95anacron ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/95hdparm-apm ]
+ [ -f /usr/lib/pm-utils/sleep.d/95hdparm-apm ]
+ hook=/usr/lib/pm-utils/sleep.d/95hdparm-apm
+ run_hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/95hdparm-apm
+ local hook=95hdparm-apm
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:95hdparm-apm ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:hdparm-apm ]
+ [ -x /usr/lib/pm-utils/sleep.d/95hdparm-apm ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend
+ local status=254
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: 
/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: + hook_exit_status 254
+ log not applicable.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ not applicable. = -n ]
+ printf %s\n not applicable.
not applicable.
+ LAST_HOOK=95hdparm-apm
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 95hdparm-apm ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/95led ]
+ [ -f /usr/lib/pm-utils/sleep.d/95led ]
+ hook=/usr/lib/pm-utils/sleep.d/95led
+ run_hook /usr/lib/pm-utils/sleep.d/95led suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/95led suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/95led
+ local hook=95led
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:95led ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:led ]
+ [ -x /usr/lib/pm-utils/sleep.d/95led ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/95led suspend suspend
+ local status=254
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/95led suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/95led suspend suspend: 
/usr/lib/pm-utils/sleep.d/95led suspend suspend: + hook_exit_status 254
+ log not applicable.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ not applicable. = -n ]
+ printf %s\n not applicable.
not applicable.
+ LAST_HOOK=95led
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 95led ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/98video-quirk-db-handler ]
+ [ -f /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler ]
+ hook=/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler
+ run_hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler
+ local hook=98video-quirk-db-handler
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:98video-quirk-db-handler ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:video-quirk-db-handler ]
+ [ -x /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend
+ [[ -n true ]]
+ export 'PS4=${BASH_SOURCE}@${LINENO}(${FUNCNAME[0]}): '
+ PS4='${BASH_SOURCE}@${LINENO}(${FUNCNAME[0]}): '
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@10(): set -x
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@25(): possible_video_quirks=' --quirk-dpms-on
	   --quirk-dpms-suspend
	   --quirk-s3-mode
	   --quirk-s3-bios
	   --quirk-vbe-post
	   --quirk-vbe-post
	   --quirk-vga-mode-3
	   --quirk-vbemode-restore
	   --quirk-vbestate-restore
	   --quirk-reset-brightness
	   --quirk-radeon-off
	   --quirk-no-fb
	   --quirk-save-pci'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@40(): possible_system_properties='system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@343(): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@347(): precache_dmivars
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@170(precache_dmivars): local p q f
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.firmware.version
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.firmware.version* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_firmware_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_firmware_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.firmware.version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@107(dmisysget): _dmisysget bios_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@100(_dmisysget): [[ -r /sys/class/dmi/id/bios_version ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@101(_dmisysget): read RES
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=1.10
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=1.10
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_firmware_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.firmware.vendor
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.vendor =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.firmware.vendor* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_firmware_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_firmware_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.firmware.vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@106(dmisysget): _dmisysget bios_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@100(_dmisysget): [[ -r /sys/class/dmi/id/bios_vendor ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@101(_dmisysget): read RES
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=TOSHIBA
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=TOSHIBA
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_firmware_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.firmware.release_date
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.release_date =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.firmware.release_date* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_firmware_release_date
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_firmware_release_date
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.firmware.release_date
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@108(dmisysget): _dmisysget bios_date
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@100(_dmisysget): [[ -r /sys/class/dmi/id/bios_date ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@101(_dmisysget): read RES
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=04/19/10
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=04/19/10
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_firmware_release_date
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.hardware.vendor
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.hardware.vendor =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.hardware.vendor* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_hardware_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_hardware_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.hardware.vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@109(dmisysget): _dmisysget sys_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@100(_dmisysget): [[ -r /sys/class/dmi/id/sys_vendor ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@101(_dmisysget): read RES
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=TOSHIBA
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=TOSHIBA
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_hardware_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.hardware.product
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.hardware.product =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.hardware.product* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_hardware_product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_hardware_product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.hardware.product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@110(dmisysget): _dmisysget product_name
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@100(_dmisysget): [[ -r /sys/class/dmi/id/product_name ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@101(_dmisysget): read RES
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES='Satellite A660'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES='Satellite A660'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_hardware_product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.hardware.version
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.hardware.version =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.hardware.version* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_hardware_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_hardware_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.hardware.version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@111(dmisysget): _dmisysget product_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@100(_dmisysget): [[ -r /sys/class/dmi/id/product_version ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@101(_dmisysget): read RES
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=PSAW3E-01100TEN
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=PSAW3E-01100TEN
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_hardware_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.board.product
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.board.product =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.board.product* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_board_product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_board_product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.board.product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@112(dmisysget): _dmisysget board_name
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@100(_dmisysget): [[ -r /sys/class/dmi/id/board_name ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@101(_dmisysget): read RES
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=NWQAA
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=NWQAA
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_board_product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.board.version
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.board.version =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.board.version* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_board_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_board_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.board.version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@113(dmisysget): _dmisysget board_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@100(_dmisysget): [[ -r /sys/class/dmi/id/board_version ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@101(_dmisysget): read RES
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=1.00
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=1.00
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_board_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.board.vendor
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.board.vendor =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.board.vendor* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_board_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_board_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.board.vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@114(dmisysget): _dmisysget board_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@100(_dmisysget): [[ -r /sys/class/dmi/id/board_vendor ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@101(_dmisysget): read RES
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=TOSHIBA
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=TOSHIBA
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_board_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.hardware.primary_video.vendor
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.hardware.primary_video.vendor =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.hardware.primary_video.vendor* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_hardware_primary_video_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_hardware_primary_video_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.hardware.primary_video.vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@115(dmisysget): videoget vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@65(videoget): local dev pci
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@66(videoget): pci=/sys/bus/pci/devices
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:00.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:00.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:03.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:03.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:08.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:08.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:08.1/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:08.1/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:08.2/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:08.2/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:08.3/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:08.3/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:10.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:10.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:10.1/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:10.1/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:16.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:16.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x078000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1a.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1a.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x0c0320 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1b.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1b.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x040300 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.1/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.1/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.2/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.2/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.3/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.3/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.4/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.4/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1d.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1d.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x0c0320 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1e.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1e.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060401 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1f.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1f.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060100 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1f.2/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1f.2/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x010601 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1f.3/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1f.3/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x0c0500 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:01:00.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:01:00.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x030000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@70(videoget): case $1 in
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@71(videoget): cat /sys/bus/pci/devices/0000:01:00.0/vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@71(videoget): RES=0x10de
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@91(videoget): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=0x10de
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=0x10de
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_hardware_primary_video_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.hardware.primary_video.product
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.hardware.primary_video.product =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.hardware.primary_video.product* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_hardware_primary_video_product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_hardware_primary_video_product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.hardware.primary_video.product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@116(dmisysget): videoget device
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@65(videoget): local dev pci
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@66(videoget): pci=/sys/bus/pci/devices
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:00.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:00.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:03.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:03.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:08.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:08.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:08.1/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:08.1/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:08.2/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:08.2/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:08.3/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:08.3/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:10.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:10.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:10.1/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:10.1/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:16.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:16.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x078000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1a.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1a.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x0c0320 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1b.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1b.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x040300 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.1/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.1/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.2/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.2/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.3/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.3/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.4/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.4/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1d.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1d.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x0c0320 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1e.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1e.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060401 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1f.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1f.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060100 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1f.2/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1f.2/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x010601 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1f.3/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1f.3/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x0c0500 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:01:00.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:01:00.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x030000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@70(videoget): case $1 in
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@72(videoget): cat /sys/bus/pci/devices/0000:01:00.0/device
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@72(videoget): RES=0x0a29
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@91(videoget): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=0x0a29
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=0x0a29
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_hardware_primary_video_product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.hardware.primary_video.driver
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.hardware.primary_video.driver =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.hardware.primary_video.driver* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_hardware_primary_video_driver
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_hardware_primary_video_driver
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.hardware.primary_video.driver
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@117(dmisysget): videoget driver
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@65(videoget): local dev pci
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@66(videoget): pci=/sys/bus/pci/devices
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:00.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:00.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:03.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:03.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:08.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:08.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:08.1/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:08.1/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:08.2/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:08.2/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:08.3/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:08.3/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:10.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:10.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:10.1/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:10.1/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:16.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:16.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x078000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1a.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1a.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x0c0320 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1b.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1b.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x040300 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.1/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.1/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.2/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.2/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.3/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.3/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.4/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.4/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1d.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1d.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x0c0320 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1e.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1e.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060401 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1f.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1f.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060100 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1f.2/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1f.2/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x010601 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1f.3/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1f.3/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x0c0500 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:01:00.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:01:00.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x030000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@70(videoget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@74(videoget): [[ -L /sys/bus/pci/devices/0000:01:00.0/driver ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@75(videoget): readlink /sys/bus/pci/devices/0000:01:00.0/driver
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@75(videoget): RES=../../../../bus/pci/drivers/nvidia
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@76(videoget): RES=nvidia
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@91(videoget): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=nvidia
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=nvidia
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_hardware_primary_video_driver
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.hardware.primary_video.using_kms
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.hardware.primary_video.using_kms =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.hardware.primary_video.using_kms* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_hardware_primary_video_using_kms
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_hardware_primary_video_using_kms
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.hardware.primary_video.using_kms
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@118(dmisysget): videoget using_kms
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@65(videoget): local dev pci
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@66(videoget): pci=/sys/bus/pci/devices
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:00.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:00.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:03.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:03.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:08.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:08.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:08.1/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:08.1/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:08.2/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:08.2/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:08.3/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:08.3/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:10.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:10.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:10.1/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:10.1/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:16.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:16.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x078000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1a.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1a.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x0c0320 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1b.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1b.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x040300 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.1/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.1/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.2/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.2/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.3/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.3/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.4/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.4/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1d.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1d.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x0c0320 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1e.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1e.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060401 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1f.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1f.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060100 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1f.2/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1f.2/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x010601 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1f.3/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1f.3/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x0c0500 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:01:00.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:01:00.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x030000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@70(videoget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@84(videoget): using_kms
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@60(using_kms): grep -q -E '(nouveau|drm)fb' /proc/fb
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@87(videoget): RES=false
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@91(videoget): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=false
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=false
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_hardware_primary_video_using_kms
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.kernel.version
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.kernel.version =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.kernel.version* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_kernel_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_kernel_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.kernel.version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@119(dmisysget): uname -r
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@119(dmisysget): RES=3.0.0-15-generic
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=3.0.0-15-generic
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=3.0.0-15-generic
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_kernel_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@181(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@352(): has_parameter --quirk-test
//usr/lib/pm-utils/functions@239(has_parameter): get_parameters
//usr/lib/pm-utils/functions@234(get_parameters): cat /var/run/pm-utils/pm-suspend/storage/parameters
/usr/lib/pm-utils/functions@243(has_parameter): return 1
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@358(): using_kms
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@60(using_kms): grep -q -E '(nouveau|drm)fb' /proc/fb
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@363(): using_nvidia
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@54(using_nvidia): [[ -d /sys/module/nvidia ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@365(): remove_parameters --quirk-dpms-on --quirk-dpms-suspend --quirk-s3-mode --quirk-s3-bios --quirk-vbe-post --quirk-vbe-post --quirk-vga-mode-3 --quirk-vbemode-restore --quirk-vbestate-restore --quirk-reset-brightness --quirk-radeon-off --quirk-no-fb --quirk-save-pci
/usr/lib/pm-utils/functions@210(remove_parameters): local p
/usr/lib/pm-utils/functions@211(remove_parameters): '[' --quirk-dpms-on = all ']'
/usr/lib/pm-utils/functions@214(remove_parameters): echo ''
/usr/lib/pm-utils/functions@215(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@216(remove_parameters): echo --quirk-dpms-on
/usr/lib/pm-utils/functions@215(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@216(remove_parameters): echo --quirk-dpms-suspend
/usr/lib/pm-utils/functions@215(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@216(remove_parameters): echo --quirk-s3-mode
/usr/lib/pm-utils/functions@215(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@216(remove_parameters): echo --quirk-s3-bios
/usr/lib/pm-utils/functions@215(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@216(remove_parameters): echo --quirk-vbe-post
/usr/lib/pm-utils/functions@215(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@216(remove_parameters): echo --quirk-vbe-post
/usr/lib/pm-utils/functions@215(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@216(remove_parameters): echo --quirk-vga-mode-3
/usr/lib/pm-utils/functions@215(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@216(remove_parameters): echo --quirk-vbemode-restore
/usr/lib/pm-utils/functions@215(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@216(remove_parameters): echo --quirk-vbestate-restore
/usr/lib/pm-utils/functions@215(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@216(remove_parameters): echo --quirk-reset-brightness
/usr/lib/pm-utils/functions@215(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@216(remove_parameters): echo --quirk-radeon-off
/usr/lib/pm-utils/functions@215(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@216(remove_parameters): echo --quirk-no-fb
/usr/lib/pm-utils/functions@215(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@216(remove_parameters): echo --quirk-save-pci
/usr/lib/pm-utils/functions@219(remove_parameters): grep -vxFf /var/run/pm-utils/pm-suspend/storage/parameters.rm /var/run/pm-utils/pm-suspend/storage/parameters
/usr/lib/pm-utils/functions@221(remove_parameters): cp -f /var/run/pm-utils/pm-suspend/storage/parameters.new /var/run/pm-utils/pm-suspend/storage/parameters
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@366(): echo 'nVidia binary video drive detected, not using quirks.'
nVidia binary video drive detected, not using quirks.
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: 
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=98video-quirk-db-handler
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 98video-quirk-db-handler ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ get_parameters
+ cat /var/run/pm-utils/pm-suspend/storage/parameters
+ export PM_CMDLINE=
+ rm -f /var/run/pm-utils/pm-suspend/storage/parameters.new
+ [ -f /etc/pm/sleep.d/99video ]
+ [ -f /usr/lib/pm-utils/sleep.d/99video ]
+ hook=/usr/lib/pm-utils/sleep.d/99video
+ run_hook /usr/lib/pm-utils/sleep.d/99video suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/99video suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/99video
+ local hook=99video
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:99video ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:video ]
+ [ -x /usr/lib/pm-utils/sleep.d/99video ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/99video suspend suspend
+ command_exists vbetool
+ type vbetool
+ return 0
+ command_exists radeontool
+ type radeontool
+ return 0
+ maybe_chvt
+ is_set 
+ return 2
+ fgconsole
+ savestate console
+ [ -n  ]
+ cat
+ chvt 63
+ suspend_video
+ local acpi_flag=0
+ quirk 
+ is_set 
+ return 2
+ quirk 
+ is_set 
+ return 2
+ sysctl -w kernel.acpi_video_flags=0
kernel.acpi_video_flags = 0
+ quirk 
+ is_set 
+ return 2
+ quirk 
+ is_set 
+ return 2
+ quirk 
+ is_set 
+ return 2
+ quirk 
+ is_set 
+ return 2
+ quirk 
+ is_set 
+ return 2
+ quirk 
+ is_set 
+ return 2
+ quirk 
+ is_set 
+ return 2
+ save_fbcon
+ local con
+ [ -f /sys/class/graphics/fb0/state ]
+ echo 1
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/99video suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/99video suspend suspend: 
/usr/lib/pm-utils/sleep.d/99video suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=99video
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 99video ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/novatel_3g_suspend ]
+ hook=/etc/pm/sleep.d/novatel_3g_suspend
+ run_hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend
+ _run_hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend
+ log Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend: = -n ]
+ printf %s\n Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
+ hook_ok /etc/pm/sleep.d/novatel_3g_suspend
+ local hook=novatel_3g_suspend
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:novatel_3g_suspend ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:novatel_3g_suspend ]
+ [ -x /etc/pm/sleep.d/novatel_3g_suspend ]
+ return 0
+ /etc/pm/sleep.d/novatel_3g_suspend suspend suspend
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /etc/pm/sleep.d/novatel_3g_suspend suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /etc/pm/sleep.d/novatel_3g_suspend suspend suspend: 
/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=novatel_3g_suspend
+ IFS=

+ IFS= 	

+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ return 0
+ date
+ log Sun Dec 18 13:33:51 AST 2011: performing suspend
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Sun Dec 18 13:33:51 AST 2011: performing suspend = -n ]
+ printf %s\n Sun Dec 18 13:33:51 AST 2011: performing suspend
Sun Dec 18 13:33:51 AST 2011: performing suspend
+ sync
+ do_suspend
+ echo -n mem
```

Now the hotkey:

```
+ log Initial commandline parameters: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Initial commandline parameters:  = -n ]
+ printf %s\n Initial commandline parameters: 
Initial commandline parameters: 
+ load_hook_blacklist
+ [  ]
+ return
+ load_hook_parameters
+ [  ]
+ [  ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ date
+ log Sun Dec 18 13:42:08 AST 2011: Running hooks for suspend.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Sun Dec 18 13:42:08 AST 2011: Running hooks for suspend. = -n ]
+ printf %s\n Sun Dec 18 13:42:08 AST 2011: Running hooks for suspend.
Sun Dec 18 13:42:08 AST 2011: Running hooks for suspend.
+ run_hooks sleep suspend suspend
+ _run_hooks sleep suspend suspend
+ local syshooks=/etc/pm/sleep.d
+ local phooks=/usr/lib/pm-utils/sleep.d
+ command_exists before_hooks
+ type before_hooks
+ return 0
+ before_hooks
+ [ -z  ]
+ return 0
+ local sort=sort
+ local base
+ local hook
+ local oifs= 	

+ local nifs=

+ IFS=

+ [  = reverse ]
+ IFS= 	

+ sort
+ uniq
+ [ -O /etc/pm/sleep.d/10_grub-common ]
+ echo 10_grub-common
+ [ -O /etc/pm/sleep.d/10_unattended-upgrades-hibernate ]
+ echo 10_unattended-upgrades-hibernate
+ [ -O /etc/pm/sleep.d/novatel_3g_suspend ]
+ echo novatel_3g_suspend
+ [ -O /usr/lib/pm-utils/sleep.d/000kernel-change ]
+ echo 000kernel-change
+ [ -O /usr/lib/pm-utils/sleep.d/00logging ]
+ echo 00logging
+ [ -O /usr/lib/pm-utils/sleep.d/00powersave ]
+ echo 00powersave
+ [ -O /usr/lib/pm-utils/sleep.d/01PulseAudio ]
+ echo 01PulseAudio
+ [ -O /usr/lib/pm-utils/sleep.d/49bluetooth ]
+ echo 49bluetooth
+ [ -O /usr/lib/pm-utils/sleep.d/55NetworkManager ]
+ echo 55NetworkManager
+ [ -O /usr/lib/pm-utils/sleep.d/60_wpa_supplicant ]
+ echo 60_wpa_supplicant
+ [ -O /usr/lib/pm-utils/sleep.d/75modules ]
+ echo 75modules
+ [ -O /usr/lib/pm-utils/sleep.d/90clock ]
+ echo 90clock
+ [ -O /usr/lib/pm-utils/sleep.d/94cpufreq ]
+ echo 94cpufreq
+ [ -O /usr/lib/pm-utils/sleep.d/95anacron ]
+ echo 95anacron
+ [ -O /usr/lib/pm-utils/sleep.d/95hdparm-apm ]
+ echo 95hdparm-apm
+ [ -O /usr/lib/pm-utils/sleep.d/95led ]
+ echo 95led
+ [ -O /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler ]
+ echo 98video-quirk-db-handler
+ [ -O /usr/lib/pm-utils/sleep.d/99video ]
+ echo 99video
+ IFS= 	

+ [  -a  = reverse -a  ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/000kernel-change ]
+ [ -f /usr/lib/pm-utils/sleep.d/000kernel-change ]
+ hook=/usr/lib/pm-utils/sleep.d/000kernel-change
+ run_hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/000kernel-change
+ local hook=000kernel-change
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:000kernel-change ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:0kernel-change ]
+ [ -x /usr/lib/pm-utils/sleep.d/000kernel-change ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: 
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=000kernel-change
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 000kernel-change ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/00logging ]
+ [ -f /usr/lib/pm-utils/sleep.d/00logging ]
+ hook=/usr/lib/pm-utils/sleep.d/00logging
+ run_hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/00logging
+ local hook=00logging
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:00logging ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:logging ]
+ [ -x /usr/lib/pm-utils/sleep.d/00logging ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/00logging suspend suspend
+ [ -n /var/log/pm-suspend.log ]
+ /bin/uname -a
Linux charlie-Satellite-A660 3.0.0-15-generic #24-Ubuntu SMP Mon Dec 12 15:23:55 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
+ lsmod
Module                  Size  Used by
bnep                   18436  2 
rfcomm                 47946  8 
pci_stub               12622  1 
vboxpci                23200  0 
vboxnetadp             13382  0 
vboxnetflt             23441  0 
vboxdrv               282739  3 vboxpci,vboxnetadp,vboxnetflt
mceusb                 17906  0 
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
dm_crypt               23199  1 
snd_hda_codec_hdmi     32040  4 
joydev                 17693  0 
uvcvideo               72711  0 
videodev               92992  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
btusb                  18600  2 
bluetooth             166112  23 bnep,rfcomm,btusb
snd_hda_codec_realtek   330769  1 
lib80211_crypt_tkip    17390  0 
psmouse                73882  0 
serio_raw              13166  0 
snd_hda_intel          33390  3 
i7core_edac            27942  0 
wl                   2568210  0 
snd_hda_codec         104931  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
jmb38x_ms              17646  0 
snd_hwdep              13668  1 snd_hda_codec
edac_core              53746  3 i7core_edac
memstick               16569  1 jmb38x_ms
snd_pcm                96714  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
lib80211               14991  2 lib80211_crypt_tkip,wl
mei                    41480  0 
nvidia              11713772  42 
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
sparse_keymap          13890  0 
ir_lirc_codec          12898  0 
lirc_dev               19204  1 ir_lirc_codec
ir_sony_decoder        12549  0 
ir_jvc_decoder         12546  0 
ir_rc6_decoder         12546  0 
ir_rc5_decoder         12546  0 
rc_rc6_mce             12502  0 
ir_nec_decoder         12546  0 
toshiba_bluetooth      12807  0 
ene_ir                 22796  0 
rc_core                26963  10 mceusb,ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,rc_rc6_mce,ir_nec_decoder,ene_ir
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usb_storage            57901  0 
uas                    18027  0 
usbhid                 47198  0 
hid                    95463  1 usbhid
vesafb                 13809  1 
ahci                   26002  3 
libahci                26861  1 ahci
r8169                  52788  0 
sdhci_pci              14032  0 
sdhci                  32166  1 sdhci_pci
video                  19412  0 
+ free
             total       used       free     shared    buffers     cached
Mem:       8124724    1768680    6356044          0     144052     574196
-/+ buffers/cache:    1050432    7074292
Swap:      8787964          0    8787964
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/00logging suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/00logging suspend suspend: 
/usr/lib/pm-utils/sleep.d/00logging suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=00logging
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 00logging ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/00powersave ]
+ [ -f /usr/lib/pm-utils/sleep.d/00powersave ]
+ hook=/usr/lib/pm-utils/sleep.d/00powersave
+ run_hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/00powersave
+ local hook=00powersave
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:00powersave ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:powersave ]
+ [ -x /usr/lib/pm-utils/sleep.d/00powersave ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/00powersave suspend suspend
+ command_exists pm-powersave
+ type pm-powersave
+ return 0
+ pm-powersave false
+ set -a
+ PM_UTILS_LIBDIR=/usr/lib/pm-utils
+ PM_UTILS_ETCDIR=/etc/pm
+ PM_UTILS_RUNDIR=/var/run/pm-utils
+ PATH=/sbin:/usr/sbin:/bin:/usr/bin:/usr/lib/pm-utils/bin
+ PM_LOGFILE=/var/log/pm-powersave.log
+ TEMPORARY_CPUFREQ_GOVERNOR=performance
+ LOCKDIR=/var/run/pm-utils/locks
+ STORAGEDIR=/var/run/pm-utils/pm-powersave/storage
+ NA=254
+ NX=253
+ DX=252
+ PM_FUNCTIONS=/usr/lib/pm-utils/functions
+ PM_QUIRKDB=/usr/lib/pm-utils/video-quirks
+ PM_LKW_QUIRKS=/var/cache/pm-utils/last_known_working.quirkdb
+ LC_COLLATE=C
+ HIBERNATE_MODE=
+ HIBERNATE_RESUME_POST_VIDEO=no
+ SLEEP_MODULE=auto
+ SUSPEND_MODULES=
+ HOOK_BLACKLIST=
+ ADD_PARAMETERS=
+ DROP_PARAMETERS=
+ PARAMETERS=/var/run/pm-utils/pm-powersave/storage/parameters
+ INHIBIT=/var/run/pm-utils/pm-powersave/storage/inhibit
+ PM_CMDLINE=false
+ BEFORE_HOOKS=
+ MODULE_HELP=
+ SUSPEND_MODULE=
+ HIBERNATE_MODULE=
+ SUSPEND_HYBRID_MODULE=
+ PM_HIBERNATE_DELAY=900
+ PM_RTC=/sys/class/rtc/rtc0
+ [ -f /usr/lib/pm-utils/defaults ]
+ . /usr/lib/pm-utils/defaults
+ [ -f /usr/lib/pm-utils/pm-powersave.defaults ]
+ set +a
+ [ -f /etc/pm/config.d/*[!~] ]
+ continue
+ [ -f /etc/pm/pm-powersave.config.d/*[!~] ]
+ continue
+ . /usr/lib/pm-utils/functions
+ export PM_DEBUG=true
+ is_set true
+ return 0
+ set -x
+ profiling
+ [  = true ]
+ profiling
+ [  = true ]
+ profiling
+ [  = true ]
+ [ auto = auto ]
+ SLEEP_MODULE=tuxonice uswsusp
+ mod=/usr/lib/pm-utils/module.d/tuxonice
+ [ -f /usr/lib/pm-utils/module.d/tuxonice ]
+ . /usr/lib/pm-utils/module.d/tuxonice
+ export TUXONICE_LOC
+ [ -d /sys/power/tuxonice ]
+ [ -d /sys/power/suspend2 ]
+ [ -n  ]
+ [ -z  -a -n  ]
+ [ -z  -a -n  ]
+ mod=/usr/lib/pm-utils/module.d/uswsusp
+ [ -f /usr/lib/pm-utils/module.d/uswsusp ]
+ . /usr/lib/pm-utils/module.d/uswsusp
+ [ -z  ]
+ command_exists s2ram
+ type s2ram
+ return 127
+ [ -z  ]
+ [ -f /sys/power/disk ]
+ grep -q disk /sys/power/state
+ [ -c /dev/snapshot ]
+ command_exists s2disk
+ type s2disk
+ return 127
+ [ -z  ]
+ grep -q mem /sys/power/state
+ command_exists s2both
+ type s2both
+ return 127
+ [ -z  ]
+ grep -q mem /sys/power/state
+ SUSPEND_MODULE=kernel
+ [ -z  ]
+ [ -f /sys/power/disk ]
+ grep -q disk /sys/power/state
+ HIBERNATE_MODULE=kernel
+ [ -z  -a -w /sys/class/rtc/rtc0/wakealarm ]
+ check_suspend
+ [ -n kernel ]
+ check_hibernate
+ [ -n kernel ]
+ is_set no
+ return 1
+ SUSPEND_HYBRID_MODULE=kernel
+ lock_and_load
+ try_lock pm-powersave.lock
+ local lock=/var/run/pm-utils/locks/pm-powersave.lock
+ mkdir -p /var/run/pm-utils/locks
+ touch /var/run/pm-utils/locks/pm-powersave.lock
+ exec
+ flock -x -n 3
+ return 0
+ trap remove_powersave_lock 0
+ mkdir -p /var/run/pm-utils/pm-powersave/storage
+ rm -f /var/run/pm-utils/pm-powersave/storage/inhibit
+ load_hook_blacklist
+ [  ]
+ return
+ init_logfile /var/log/pm-powersave.log
+ [ -z /var/log/pm-powersave.log ]
+ [ -h /var/log/pm-powersave.log ]
+ [ -f /var/log/pm-powersave.log -a ! -O /var/log/pm-powersave.log ]
+ export LOGGING=true
+ exec
+ exit 0
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/00powersave suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/00powersave suspend suspend: 
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=00powersave
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 00powersave ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/01PulseAudio ]
+ [ -f /usr/lib/pm-utils/sleep.d/01PulseAudio ]
+ hook=/usr/lib/pm-utils/sleep.d/01PulseAudio
+ run_hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/01PulseAudio
+ local hook=01PulseAudio
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:01PulseAudio ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:PulseAudio ]
+ [ -x /usr/lib/pm-utils/sleep.d/01PulseAudio ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend
+ suspend_pulse
+ get_pulse_users
+ test_pulse_system
+ getent passwd pulse
+ awk -F: {print $3}
+ PULSE_SYSTEM_USER=109
+ [ -z 109 ]
+ ps -C pulseaudio -o uid=
+ tr -d  
+ sed s/109//
+ getent passwd 1000
+ cut -f1 -d:
+ THIS_USER=charlie
+ save_pulse_state sink charlie
+ su+  charlie -csed -- -n pacmd list-sinks s/^[[:space:]*]*//; /\(index\|mute\)/p

+ index=
+ read field value
Sessions still open, not unmounting
+ [ index = index ]
+ index=0
+ read field value
+ [ muted = index ]
+ savestate pulse:charlie:sink0 no
+ [ -n no ]
+ echo no
+ read field value
+ [ index = index ]
+ index=1
+ read field value
+ [ muted = index ]
+ savestate pulse:charlie:sink1 yes
+ [ -n yes ]
+ echo yes
+ read field value
+ save_pulse_state source charlie
+ su charlie -c -- pacmd list-sources
+ sed -n s/^[[:space:]*]*//; /\(index\|mute\)/p
+ index=
+ read field value
Sessions still open, not unmounting
+ [ index = index ]
+ index=0
+ read field value
+ [ muted = index ]
+ savestate pulse:charlie:source0 yes
+ [ -n yes ]
+ echo yes
+ read field value
+ [ index = index ]
+ index=1
+ read field value
+ [ muted = index ]
+ savestate pulse:charlie:source1 yes
+ [ -n yes ]
+ echo yes
+ read field value
+ [ index = index ]
+ index=2
+ read field value
+ [ muted = index ]
+ savestate pulse:charlie:source2 yes
+ [ -n yes ]
+ echo yes
+ read field value
+ su charlie -c -- pacmd suspend true
+ get_pulse_users
+ test_pulse_system
+ getent passwd pulse
+ awk -F: {print $3}
+ PULSE_SYSTEM_USER=109
+ [ -z 109 ]
+ ps -C pulseaudio -o uid=
+ tr -d  
+ sed s/109//
+ getent passwd 1000
+ cut -f1 -d:
+ THIS_USER=charlie
+ su charlie -c -- ck-list-sessions | grep "active = TRUE"
+ mute_pulse sink charlie
+ su charlie -c -- pacmd list-sinks
+ sed -n s/^[[:space:]*]*//; /\(index\|mute\)/p
+ index=
+ read field value
Sessions still open, not unmounting
+ [ index = index ]
+ index=0
+ su charlie -c -- pacmd                         set-sink-mute 0 yes
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
+ read field value
+ [ muted = index ]
+ read field value
+ [ index = index ]
+ index=1
+ su charlie -c -- pacmd                         set-sink-mute 1 yes
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
+ read field value
+ [ muted = index ]
+ read field value
+ mute_pulse source charlie
+ su charlie -c -- pacmd list-sources
+ + sed -nindex=
 s/^[[:space:]*]*//; /\(index\|mute\)/p
+ read field value
Sessions still open, not unmounting
+ [ index = index ]
+ index=0
+ su charlie -c -- pacmd                         set-source-mute 0 yes
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
+ read field value
+ [ muted = index ]
+ read field value
+ [ index = index ]
+ index=1
+ su charlie -c -- pacmd                         set-source-mute 1 yes
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
+ read field value
+ [ muted = index ]
+ read field value
+ [ index = index ]
+ index=2
+ su charlie -c -- pacmd                         set-source-mute 2 yes
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
+ read field value
+ [ muted = index ]
+ read field value
+ break
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=01PulseAudio
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 01PulseAudio ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/10_grub-common ]
+ hook=/etc/pm/sleep.d/10_grub-common
+ run_hook /etc/pm/sleep.d/10_grub-common suspend suspend
+ _run_hook /etc/pm/sleep.d/10_grub-common suspend suspend
+ log Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /etc/pm/sleep.d/10_grub-common suspend suspend: = -n ]
+ printf %s\n Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
+ hook_ok /etc/pm/sleep.d/10_grub-common
+ local hook=10_grub-common
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:10_grub-common ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:_grub-common ]
+ [ -x /etc/pm/sleep.d/10_grub-common ]
+ return 0
+ /etc/pm/sleep.d/10_grub-common suspend suspend
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /etc/pm/sleep.d/10_grub-common suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /etc/pm/sleep.d/10_grub-common suspend suspend: 
/etc/pm/sleep.d/10_grub-common suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=10_grub-common
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 10_grub-common ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/10_unattended-upgrades-hibernate ]
+ hook=/etc/pm/sleep.d/10_unattended-upgrades-hibernate
+ run_hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend
+ _run_hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend
+ log Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: = -n ]
+ printf %s\n Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
+ hook_ok /etc/pm/sleep.d/10_unattended-upgrades-hibernate
+ local hook=10_unattended-upgrades-hibernate
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:10_unattended-upgrades-hibernate ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:_unattended-upgrades-hibernate ]
+ [ -x /etc/pm/sleep.d/10_unattended-upgrades-hibernate ]
+ return 0
+ /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: 
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=10_unattended-upgrades-hibernate
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 10_unattended-upgrades-hibernate ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/49bluetooth ]
+ [ -f /usr/lib/pm-utils/sleep.d/49bluetooth ]
+ hook=/usr/lib/pm-utils/sleep.d/49bluetooth
+ run_hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/49bluetooth
+ local hook=49bluetooth
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:49bluetooth ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:bluetooth ]
+ [ -x /usr/lib/pm-utils/sleep.d/49bluetooth ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend
+ [ -f /proc/acpi/ibm/bluetooth ]
+ exit 254
+ local status=254
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: 
/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: + hook_exit_status 254
+ log not applicable.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ not applicable. = -n ]
+ printf %s\n not applicable.
not applicable.
+ LAST_HOOK=49bluetooth
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 49bluetooth ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/55NetworkManager ]
+ [ -f /usr/lib/pm-utils/sleep.d/55NetworkManager ]
+ hook=/usr/lib/pm-utils/sleep.d/55NetworkManager
+ run_hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/55NetworkManager
+ local hook=55NetworkManager
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:55NetworkManager ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:NetworkManager ]
+ [ -x /usr/lib/pm-utils/sleep.d/55NetworkManager ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend
+ suspend_nm
+ printf Having NetworkManager put all interaces to sleep...
Having NetworkManager put all interaces to sleep...+ dbus_send --print-reply --system --dest=org.freedesktop.NetworkManager /org/freedesktop/NetworkManager org.freedesktop.NetworkManager.sleep
+ command dbus-send --print-reply --system --dest=org.freedesktop.NetworkManager /org/freedesktop/NetworkManager org.freedesktop.NetworkManager.sleep
+ return 254
+ echo Failed.
Failed.
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: 
/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=55NetworkManager
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 55NetworkManager ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/60_wpa_supplicant ]
+ [ -f /usr/lib/pm-utils/sleep.d/60_wpa_supplicant ]
+ hook=/usr/lib/pm-utils/sleep.d/60_wpa_supplicant
+ run_hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/60_wpa_supplicant
+ local hook=60_wpa_supplicant
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:60_wpa_supplicant ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:_wpa_supplicant ]
+ [ -x /usr/lib/pm-utils/sleep.d/60_wpa_supplicant ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: 
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=60_wpa_supplicant
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 60_wpa_supplicant ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/75modules ]
+ [ -f /usr/lib/pm-utils/sleep.d/75modules ]
+ hook=/usr/lib/pm-utils/sleep.d/75modules
+ run_hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/75modules
+ local hook=75modules
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:75modules ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:modules ]
+ [ -x /usr/lib/pm-utils/sleep.d/75modules ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/75modules suspend suspend
+ suspend_modules
+ [ -z  ]
+ return 254
+ local status=254
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/75modules suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/75modules suspend suspend: 
/usr/lib/pm-utils/sleep.d/75modules suspend suspend: + hook_exit_status 254
+ log not applicable.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ not applicable. = -n ]
+ printf %s\n not applicable.
not applicable.
+ LAST_HOOK=75modules
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 75modules ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/90clock ]
+ [ -f /usr/lib/pm-utils/sleep.d/90clock ]
+ hook=/usr/lib/pm-utils/sleep.d/90clock
+ run_hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/90clock
+ local hook=90clock
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:90clock ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:clock ]
+ [ -x /usr/lib/pm-utils/sleep.d/90clock ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/90clock suspend suspend
+ is_set 
+ return 2
+ exit 254
+ local status=254
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/90clock suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/90clock suspend suspend: 
/usr/lib/pm-utils/sleep.d/90clock suspend suspend: + hook_exit_status 254
+ log not applicable.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ not applicable. = -n ]
+ printf %s\n not applicable.
not applicable.
+ LAST_HOOK=90clock
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 90clock ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/94cpufreq ]
+ [ -f /usr/lib/pm-utils/sleep.d/94cpufreq ]
+ hook=/usr/lib/pm-utils/sleep.d/94cpufreq
+ run_hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/94cpufreq
+ local hook=94cpufreq
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:94cpufreq ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:cpufreq ]
+ [ -x /usr/lib/pm-utils/sleep.d/94cpufreq ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend
+ [ -d /sys/devices/system/cpu/ ]
+ hibernate_cpufreq
+ cd /sys/devices/system/cpu/
+ [ -L cpu0/cpufreq ]
+ gov=cpu0/cpufreq/scaling_governor
+ [ -f cpu0/cpufreq/scaling_governor ]
+ grep -q performance cpu0/cpufreq/scaling_available_governors
+ savestate cpu0_governor
+ [ -n  ]
+ cat
+ echo performance
+ [ -L cpu1/cpufreq ]
+ gov=cpu1/cpufreq/scaling_governor
+ [ -f cpu1/cpufreq/scaling_governor ]
+ grep -q performance cpu1/cpufreq/scaling_available_governors
+ savestate cpu1_governor
+ [ -n  ]
+ cat
+ echo performance
+ [ -L cpu2/cpufreq ]
+ gov=cpu2/cpufreq/scaling_governor
+ [ -f cpu2/cpufreq/scaling_governor ]
+ grep -q performance cpu2/cpufreq/scaling_available_governors
+ savestate cpu2_governor
+ [ -n  ]
+ cat
+ echo performance
+ [ -L cpu3/cpufreq ]
+ gov=cpu3/cpufreq/scaling_governor
+ [ -f cpu3/cpufreq/scaling_governor ]
+ grep -q performance cpu3/cpufreq/scaling_available_governors
+ savestate cpu3_governor
+ [ -n  ]
+ cat
+ echo performance
+ [ -L cpu4/cpufreq ]
+ gov=cpu4/cpufreq/scaling_governor
+ [ -f cpu4/cpufreq/scaling_governor ]
+ grep -q performance cpu4/cpufreq/scaling_available_governors
+ savestate cpu4_governor
+ [ -n  ]
+ cat
+ echo performance
+ [ -L cpu5/cpufreq ]
+ gov=cpu5/cpufreq/scaling_governor
+ [ -f cpu5/cpufreq/scaling_governor ]
+ grep -q performance cpu5/cpufreq/scaling_available_governors
+ savestate cpu5_governor
+ [ -n  ]
+ cat
+ echo performance
+ [ -L cpu6/cpufreq ]
+ gov=cpu6/cpufreq/scaling_governor
+ [ -f cpu6/cpufreq/scaling_governor ]
+ grep -q performance cpu6/cpufreq/scaling_available_governors
+ savestate cpu6_governor
+ [ -n  ]
+ cat
+ echo performance
+ [ -L cpu7/cpufreq ]
+ gov=cpu7/cpufreq/scaling_governor
+ [ -f cpu7/cpufreq/scaling_governor ]
+ grep -q performance cpu7/cpufreq/scaling_available_governors
+ savestate cpu7_governor
+ [ -n  ]
+ cat
+ echo performance
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: 
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=94cpufreq
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 94cpufreq ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/95anacron ]
+ [ -f /usr/lib/pm-utils/sleep.d/95anacron ]
+ hook=/usr/lib/pm-utils/sleep.d/95anacron
+ run_hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/95anacron
+ local hook=95anacron
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:95anacron ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:anacron ]
+ [ -x /usr/lib/pm-utils/sleep.d/95anacron ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/95anacron suspend suspend
stop: Unknown instance: 
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/95anacron suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/95anacron suspend suspend: 
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=95anacron
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 95anacron ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/95hdparm-apm ]
+ [ -f /usr/lib/pm-utils/sleep.d/95hdparm-apm ]
+ hook=/usr/lib/pm-utils/sleep.d/95hdparm-apm
+ run_hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/95hdparm-apm
+ local hook=95hdparm-apm
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:95hdparm-apm ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:hdparm-apm ]
+ [ -x /usr/lib/pm-utils/sleep.d/95hdparm-apm ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend
+ local status=254
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: 
/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: + hook_exit_status 254
+ log not applicable.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ not applicable. = -n ]
+ printf %s\n not applicable.
not applicable.
+ LAST_HOOK=95hdparm-apm
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 95hdparm-apm ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/95led ]
+ [ -f /usr/lib/pm-utils/sleep.d/95led ]
+ hook=/usr/lib/pm-utils/sleep.d/95led
+ run_hook /usr/lib/pm-utils/sleep.d/95led suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/95led suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/95led
+ local hook=95led
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:95led ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:led ]
+ [ -x /usr/lib/pm-utils/sleep.d/95led ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/95led suspend suspend
+ local status=254
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/95led suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/95led suspend suspend: 
/usr/lib/pm-utils/sleep.d/95led suspend suspend: + hook_exit_status 254
+ log not applicable.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ not applicable. = -n ]
+ printf %s\n not applicable.
not applicable.
+ LAST_HOOK=95led
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 95led ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/98video-quirk-db-handler ]
+ [ -f /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler ]
+ hook=/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler
+ run_hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler
+ local hook=98video-quirk-db-handler
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:98video-quirk-db-handler ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:video-quirk-db-handler ]
+ [ -x /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend
+ [[ -n true ]]
+ export 'PS4=${BASH_SOURCE}@${LINENO}(${FUNCNAME[0]}): '
+ PS4='${BASH_SOURCE}@${LINENO}(${FUNCNAME[0]}): '
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@10(): set -x
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@25(): possible_video_quirks=' --quirk-dpms-on
	   --quirk-dpms-suspend
	   --quirk-s3-mode
	   --quirk-s3-bios
	   --quirk-vbe-post
	   --quirk-vbe-post
	   --quirk-vga-mode-3
	   --quirk-vbemode-restore
	   --quirk-vbestate-restore
	   --quirk-reset-brightness
	   --quirk-radeon-off
	   --quirk-no-fb
	   --quirk-save-pci'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@40(): possible_system_properties='system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@343(): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@347(): precache_dmivars
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@170(precache_dmivars): local p q f
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.firmware.version
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.firmware.version* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_firmware_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_firmware_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.firmware.version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@107(dmisysget): _dmisysget bios_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@100(_dmisysget): [[ -r /sys/class/dmi/id/bios_version ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@101(_dmisysget): read RES
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=1.10
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=1.10
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_firmware_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.firmware.vendor
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.vendor =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.firmware.vendor* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_firmware_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_firmware_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.firmware.vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@106(dmisysget): _dmisysget bios_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@100(_dmisysget): [[ -r /sys/class/dmi/id/bios_vendor ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@101(_dmisysget): read RES
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=TOSHIBA
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=TOSHIBA
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_firmware_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.firmware.release_date
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.release_date =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.firmware.release_date* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_firmware_release_date
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_firmware_release_date
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.firmware.release_date
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@108(dmisysget): _dmisysget bios_date
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@100(_dmisysget): [[ -r /sys/class/dmi/id/bios_date ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@101(_dmisysget): read RES
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=04/19/10
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=04/19/10
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_firmware_release_date
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.hardware.vendor
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.hardware.vendor =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.hardware.vendor* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_hardware_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_hardware_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.hardware.vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@109(dmisysget): _dmisysget sys_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@100(_dmisysget): [[ -r /sys/class/dmi/id/sys_vendor ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@101(_dmisysget): read RES
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=TOSHIBA
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=TOSHIBA
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_hardware_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.hardware.product
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.hardware.product =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.hardware.product* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_hardware_product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_hardware_product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.hardware.product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@110(dmisysget): _dmisysget product_name
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@100(_dmisysget): [[ -r /sys/class/dmi/id/product_name ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@101(_dmisysget): read RES
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES='Satellite A660'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES='Satellite A660'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_hardware_product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.hardware.version
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.hardware.version =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.hardware.version* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_hardware_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_hardware_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.hardware.version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@111(dmisysget): _dmisysget product_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@100(_dmisysget): [[ -r /sys/class/dmi/id/product_version ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@101(_dmisysget): read RES
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=PSAW3E-01100TEN
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=PSAW3E-01100TEN
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_hardware_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.board.product
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.board.product =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.board.product* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_board_product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_board_product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.board.product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@112(dmisysget): _dmisysget board_name
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@100(_dmisysget): [[ -r /sys/class/dmi/id/board_name ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@101(_dmisysget): read RES
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=NWQAA
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=NWQAA
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_board_product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.board.version
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.board.version =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.board.version* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_board_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_board_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.board.version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@113(dmisysget): _dmisysget board_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@100(_dmisysget): [[ -r /sys/class/dmi/id/board_version ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@101(_dmisysget): read RES
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=1.00
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=1.00
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_board_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.board.vendor
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.board.vendor =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.board.vendor* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_board_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_board_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.board.vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@114(dmisysget): _dmisysget board_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@100(_dmisysget): [[ -r /sys/class/dmi/id/board_vendor ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@101(_dmisysget): read RES
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=TOSHIBA
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=TOSHIBA
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_board_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.hardware.primary_video.vendor
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.hardware.primary_video.vendor =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.hardware.primary_video.vendor* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_hardware_primary_video_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_hardware_primary_video_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.hardware.primary_video.vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@115(dmisysget): videoget vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@65(videoget): local dev pci
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@66(videoget): pci=/sys/bus/pci/devices
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:00.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:00.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:03.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:03.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:08.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:08.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:08.1/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:08.1/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:08.2/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:08.2/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:08.3/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:08.3/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:10.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:10.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:10.1/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:10.1/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:16.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:16.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x078000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1a.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1a.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x0c0320 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1b.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1b.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x040300 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.1/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.1/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.2/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.2/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.3/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.3/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.4/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.4/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1d.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1d.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x0c0320 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1e.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1e.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060401 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1f.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1f.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060100 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1f.2/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1f.2/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x010601 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1f.3/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1f.3/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x0c0500 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:01:00.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:01:00.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x030000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@70(videoget): case $1 in
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@71(videoget): cat /sys/bus/pci/devices/0000:01:00.0/vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@71(videoget): RES=0x10de
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@91(videoget): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=0x10de
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=0x10de
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_hardware_primary_video_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.hardware.primary_video.product
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.hardware.primary_video.product =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.hardware.primary_video.product* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_hardware_primary_video_product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_hardware_primary_video_product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.hardware.primary_video.product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@116(dmisysget): videoget device
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@65(videoget): local dev pci
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@66(videoget): pci=/sys/bus/pci/devices
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:00.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:00.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:03.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:03.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:08.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:08.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:08.1/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:08.1/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:08.2/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:08.2/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:08.3/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:08.3/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:10.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:10.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:10.1/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:10.1/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:16.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:16.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x078000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1a.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1a.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x0c0320 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1b.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1b.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x040300 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.1/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.1/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.2/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.2/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.3/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.3/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.4/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.4/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1d.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1d.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x0c0320 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1e.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1e.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060401 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1f.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1f.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060100 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1f.2/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1f.2/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x010601 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1f.3/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1f.3/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x0c0500 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:01:00.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:01:00.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x030000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@70(videoget): case $1 in
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@72(videoget): cat /sys/bus/pci/devices/0000:01:00.0/device
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@72(videoget): RES=0x0a29
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@91(videoget): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=0x0a29
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=0x0a29
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_hardware_primary_video_product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.hardware.primary_video.driver
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.hardware.primary_video.driver =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.hardware.primary_video.driver* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_hardware_primary_video_driver
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_hardware_primary_video_driver
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.hardware.primary_video.driver
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@117(dmisysget): videoget driver
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@65(videoget): local dev pci
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@66(videoget): pci=/sys/bus/pci/devices
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:00.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:00.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:03.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:03.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:08.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:08.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:08.1/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:08.1/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:08.2/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:08.2/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:08.3/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:08.3/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:10.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:10.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:10.1/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:10.1/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:16.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:16.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x078000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1a.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1a.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x0c0320 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1b.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1b.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x040300 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.1/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.1/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.2/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.2/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.3/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.3/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.4/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.4/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1d.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1d.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x0c0320 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1e.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1e.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060401 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1f.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1f.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060100 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1f.2/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1f.2/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x010601 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1f.3/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1f.3/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x0c0500 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:01:00.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:01:00.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x030000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@70(videoget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@74(videoget): [[ -L /sys/bus/pci/devices/0000:01:00.0/driver ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@75(videoget): readlink /sys/bus/pci/devices/0000:01:00.0/driver
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@75(videoget): RES=../../../../bus/pci/drivers/nvidia
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@76(videoget): RES=nvidia
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@91(videoget): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=nvidia
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=nvidia
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_hardware_primary_video_driver
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.hardware.primary_video.using_kms
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.hardware.primary_video.using_kms =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.hardware.primary_video.using_kms* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_hardware_primary_video_using_kms
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_hardware_primary_video_using_kms
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.hardware.primary_video.using_kms
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@118(dmisysget): videoget using_kms
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@65(videoget): local dev pci
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@66(videoget): pci=/sys/bus/pci/devices
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:00.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:00.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:03.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:03.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:08.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:08.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:08.1/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:08.1/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:08.2/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:08.2/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:08.3/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:08.3/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:10.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:10.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:10.1/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:10.1/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:16.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:16.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x078000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1a.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1a.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x0c0320 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1b.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1b.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x040300 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.1/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.1/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.2/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.2/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.3/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.3/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.4/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.4/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1d.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1d.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x0c0320 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1e.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1e.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060401 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1f.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1f.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060100 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1f.2/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1f.2/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x010601 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1f.3/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1f.3/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x0c0500 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:01:00.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:01:00.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x030000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@70(videoget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@84(videoget): using_kms
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@60(using_kms): grep -q -E '(nouveau|drm)fb' /proc/fb
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@87(videoget): RES=false
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@91(videoget): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=false
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=false
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_hardware_primary_video_using_kms
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.kernel.version
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.kernel.version =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.kernel.version* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_kernel_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_kernel_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.kernel.version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@119(dmisysget): uname -r
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@119(dmisysget): RES=3.0.0-15-generic
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=3.0.0-15-generic
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=3.0.0-15-generic
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_kernel_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@181(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@352(): has_parameter --quirk-test
//usr/lib/pm-utils/functions@240(has_parameter): get_parameters
//usr/lib/pm-utils/functions@235(get_parameters): cat /var/run/pm-utils/pm-suspend/storage/parameters
/usr/lib/pm-utils/functions@244(has_parameter): return 1
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@358(): using_kms
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@60(using_kms): grep -q -E '(nouveau|drm)fb' /proc/fb
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@363(): using_nvidia
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@54(using_nvidia): [[ -d /sys/module/nvidia ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@365(): remove_parameters --quirk-dpms-on --quirk-dpms-suspend --quirk-s3-mode --quirk-s3-bios --quirk-vbe-post --quirk-vbe-post --quirk-vga-mode-3 --quirk-vbemode-restore --quirk-vbestate-restore --quirk-reset-brightness --quirk-radeon-off --quirk-no-fb --quirk-save-pci
/usr/lib/pm-utils/functions@211(remove_parameters): local p
/usr/lib/pm-utils/functions@212(remove_parameters): '[' --quirk-dpms-on = all ']'
/usr/lib/pm-utils/functions@215(remove_parameters): echo ''
/usr/lib/pm-utils/functions@216(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@217(remove_parameters): echo --quirk-dpms-on
/usr/lib/pm-utils/functions@216(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@217(remove_parameters): echo --quirk-dpms-suspend
/usr/lib/pm-utils/functions@216(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@217(remove_parameters): echo --quirk-s3-mode
/usr/lib/pm-utils/functions@216(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@217(remove_parameters): echo --quirk-s3-bios
/usr/lib/pm-utils/functions@216(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@217(remove_parameters): echo --quirk-vbe-post
/usr/lib/pm-utils/functions@216(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@217(remove_parameters): echo --quirk-vbe-post
/usr/lib/pm-utils/functions@216(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@217(remove_parameters): echo --quirk-vga-mode-3
/usr/lib/pm-utils/functions@216(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@217(remove_parameters): echo --quirk-vbemode-restore
/usr/lib/pm-utils/functions@216(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@217(remove_parameters): echo --quirk-vbestate-restore
/usr/lib/pm-utils/functions@216(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@217(remove_parameters): echo --quirk-reset-brightness
/usr/lib/pm-utils/functions@216(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@217(remove_parameters): echo --quirk-radeon-off
/usr/lib/pm-utils/functions@216(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@217(remove_parameters): echo --quirk-no-fb
/usr/lib/pm-utils/functions@216(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@217(remove_parameters): echo --quirk-save-pci
/usr/lib/pm-utils/functions@220(remove_parameters): grep -vxFf /var/run/pm-utils/pm-suspend/storage/parameters.rm /var/run/pm-utils/pm-suspend/storage/parameters
/usr/lib/pm-utils/functions@222(remove_parameters): cp -f /var/run/pm-utils/pm-suspend/storage/parameters.new /var/run/pm-utils/pm-suspend/storage/parameters
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@366(): echo 'nVidia binary video drive detected, not using quirks.'
nVidia binary video drive detected, not using quirks.
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: 
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=98video-quirk-db-handler
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 98video-quirk-db-handler ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ get_parameters
+ cat /var/run/pm-utils/pm-suspend/storage/parameters
+ export PM_CMDLINE=
+ rm -f /var/run/pm-utils/pm-suspend/storage/parameters.new
+ [ -f /etc/pm/sleep.d/99video ]
+ [ -f /usr/lib/pm-utils/sleep.d/99video ]
+ hook=/usr/lib/pm-utils/sleep.d/99video
+ run_hook /usr/lib/pm-utils/sleep.d/99video suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/99video suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/99video
+ local hook=99video
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:99video ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:video ]
+ [ -x /usr/lib/pm-utils/sleep.d/99video ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/99video suspend suspend
+ command_exists vbetool
+ type vbetool
+ return 0
+ command_exists radeontool
+ type radeontool
+ return 0
+ maybe_chvt
+ is_set 
+ return 2
+ fgconsole
+ savestate console
+ [ -n  ]
+ cat
+ chvt 63
+ suspend_video
+ local acpi_flag=0
+ quirk 
+ is_set 
+ return 2
+ quirk 
+ is_set 
+ return 2
+ sysctl -w kernel.acpi_video_flags=0
kernel.acpi_video_flags = 0
+ quirk 
+ is_set 
+ return 2
+ quirk 
+ is_set 
+ return 2
+ quirk 
+ is_set 
+ return 2
+ quirk 
+ is_set 
+ return 2
+ quirk 
+ is_set 
+ return 2
+ quirk 
+ is_set 
+ return 2
+ quirk 
+ is_set 
+ return 2
+ save_fbcon
+ local con
+ [ -f /sys/class/graphics/fb0/state ]
+ echo 1
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/99video suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/99video suspend suspend: 
/usr/lib/pm-utils/sleep.d/99video suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=99video
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 99video ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/novatel_3g_suspend ]
+ hook=/etc/pm/sleep.d/novatel_3g_suspend
+ run_hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend
+ _run_hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend
+ log Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend: = -n ]
+ printf %s\n Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
+ hook_ok /etc/pm/sleep.d/novatel_3g_suspend
+ local hook=novatel_3g_suspend
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:novatel_3g_suspend ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:novatel_3g_suspend ]
+ [ -x /etc/pm/sleep.d/novatel_3g_suspend ]
+ return 0
+ /etc/pm/sleep.d/novatel_3g_suspend suspend suspend
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /etc/pm/sleep.d/novatel_3g_suspend suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /etc/pm/sleep.d/novatel_3g_suspend suspend suspend: 
/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=novatel_3g_suspend
+ IFS=

+ IFS= 	

+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ return 0
+ date
+ log Sun Dec 18 13:42:12 AST 2011: performing suspend
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Sun Dec 18 13:42:12 AST 2011: performing suspend = -n ]
+ printf %s\n Sun Dec 18 13:42:12 AST 2011: performing suspend
Sun Dec 18 13:42:12 AST 2011: performing suspend
+ sync
+ do_suspend
+ echo -n mem
```

Cheers
Charlie

---

### Post by Toz on 2011-12-18
The plot thickens.

What happens when you try to resume? Blank screen? Reboot?

I notice you have virtualbox installed. Do you have running VMs when trying to suspend?
There was a virtualbox bug (I thought this bug had been fixed), but try this to see just in case. Run:
```
sudo /etc/init.d/vboxdrv stop
```
...prior to suspending. If that works, we can automatically suspend those modules.

```
sudo /etc/init.d/vboxdrv start
```
...to restart the services.

Otherwise, you might want to try running:
```
sudo sh -c "sync; echo 1 > /sys/power/pm_trace; pm-suspend"
```
...again and posting back the results of dmesg to see if there is anything coming up now.

---

### Post by FokkerCharlie on 2011-12-18
OK, the Virtualbox solution didn't work- I seem to have the same problem.

Here's the output from dmesg:

[http://ubuntuone.com/49s8rsNGlBBxB220XgxCPP]("http://ubuntuone.com/49s8rsNGlBBxB220XgxCPP")

I use an encrypted home folder, and I'm a bit surprised to see the log flooded with eCryptfs messages.  Note that the 'no_console_suspend' flag that is in the first few boot lines (an earlier debugging effort) has been taken out.

Is the problem to do with encryption?

Cheers
Charlie

---

### Post by Toz on 2011-12-18
Sorry, whats the output from dmesg?

Also, what happens on resume? black screen? Auto reboot? Flashing LEDs?

EDIT: Which kernel are you running?
```
uname -r
```

---

### Post by FokkerCharlie on 2011-12-18
Sorry!  My mistake.

Added the link to my dmesg file in the post where it should have been:
[http://ubuntuone.com/49s8rsNGlBBxB220XgxCPP](http://ubuntuone.com/49s8rsNGlBBxB220XgxCPP)

On attempting to resume, there's no blinking LEDs or anything, the screen remains blank, but the LCD backlight comes on.

I tried suspending from the login screen (immediately after boot), and that caused the suspend to fail as previously described.  I don't know whether that's useful debugging information or not.

Any ideas?

Thanks for your continued input, and patience.
Charlie

---

### Post by Toz on 2011-12-18
Interesting. I notice you're running kernel 3.0.0.15 (I believe that its still in testing). There is a known regression in this kernel version where suspend is failing to work for a number of systems (see: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/904569]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/904569")).

Can you boot the previous kernel version and see if suspend works there?

---

### Post by FokkerCharlie on 2011-12-19
Hmmm, that's interesting.  I guess it came in from the 'proposed' repo or something.

Anyway, reverted back to the -14 kernel, here's some more logs:

First, a good suspend from the bash terminal:

```
+ log Initial commandline parameters: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Initial commandline parameters:  = -n ]
+ printf %s\n Initial commandline parameters: 
Initial commandline parameters: 
+ load_hook_blacklist
+ [  ]
+ return
+ load_hook_parameters
+ [  ]
+ [  ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ date
+ log Mon Dec 19 11:43:38 AST 2011: Running hooks for suspend.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Mon Dec 19 11:43:38 AST 2011: Running hooks for suspend. = -n ]
+ printf %s\n Mon Dec 19 11:43:38 AST 2011: Running hooks for suspend.
Mon Dec 19 11:43:38 AST 2011: Running hooks for suspend.
+ run_hooks sleep suspend suspend
+ _run_hooks sleep suspend suspend
+ local syshooks=/etc/pm/sleep.d
+ local phooks=/usr/lib/pm-utils/sleep.d
+ command_exists before_hooks
+ type before_hooks
+ return 0
+ before_hooks
+ [ -z  ]
+ return 0
+ local sort=sort
+ local base
+ local hook
+ local oifs= 	

+ local nifs=

+ IFS=

+ [  = reverse ]
+ IFS= 	

+ sort
+ uniq
+ [ -O /etc/pm/sleep.d/10_grub-common ]
+ echo 10_grub-common
+ [ -O /etc/pm/sleep.d/10_unattended-upgrades-hibernate ]
+ echo 10_unattended-upgrades-hibernate
+ [ -O /etc/pm/sleep.d/novatel_3g_suspend ]
+ echo novatel_3g_suspend
+ [ -O /usr/lib/pm-utils/sleep.d/000kernel-change ]
+ echo 000kernel-change
+ [ -O /usr/lib/pm-utils/sleep.d/00logging ]
+ echo 00logging
+ [ -O /usr/lib/pm-utils/sleep.d/00powersave ]
+ echo 00powersave
+ [ -O /usr/lib/pm-utils/sleep.d/01PulseAudio ]
+ echo 01PulseAudio
+ [ -O /usr/lib/pm-utils/sleep.d/49bluetooth ]
+ echo 49bluetooth
+ [ -O /usr/lib/pm-utils/sleep.d/55NetworkManager ]
+ echo 55NetworkManager
+ [ -O /usr/lib/pm-utils/sleep.d/60_wpa_supplicant ]
+ echo 60_wpa_supplicant
+ [ -O /usr/lib/pm-utils/sleep.d/75modules ]
+ echo 75modules
+ [ -O /usr/lib/pm-utils/sleep.d/90clock ]
+ echo 90clock
+ [ -O /usr/lib/pm-utils/sleep.d/94cpufreq ]
+ echo 94cpufreq
+ [ -O /usr/lib/pm-utils/sleep.d/95anacron ]
+ echo 95anacron
+ [ -O /usr/lib/pm-utils/sleep.d/95hdparm-apm ]
+ echo 95hdparm-apm
+ [ -O /usr/lib/pm-utils/sleep.d/95led ]
+ echo 95led
+ [ -O /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler ]
+ echo 98video-quirk-db-handler
+ [ -O /usr/lib/pm-utils/sleep.d/99video ]
+ echo 99video
+ IFS= 	

+ [  -a  = reverse -a  ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/000kernel-change ]
+ [ -f /usr/lib/pm-utils/sleep.d/000kernel-change ]
+ hook=/usr/lib/pm-utils/sleep.d/000kernel-change
+ run_hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/000kernel-change
+ local hook=000kernel-change
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:000kernel-change ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:0kernel-change ]
+ [ -x /usr/lib/pm-utils/sleep.d/000kernel-change ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: 
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=000kernel-change
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 000kernel-change ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/00logging ]
+ [ -f /usr/lib/pm-utils/sleep.d/00logging ]
+ hook=/usr/lib/pm-utils/sleep.d/00logging
+ run_hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/00logging
+ local hook=00logging
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:00logging ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:logging ]
+ [ -x /usr/lib/pm-utils/sleep.d/00logging ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/00logging suspend suspend
+ [ -n /var/log/pm-suspend.log ]
+ /bin/uname -a
Linux charlie-Satellite-A660 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:28:43 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
+ lsmod
Module                  Size  Used by
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
pci_stub               12622  1 
vboxpci                23200  0 
vboxnetadp             13382  0 
vboxnetflt             23441  0 
vboxdrv               282739  3 vboxpci,vboxnetadp,vboxnetflt
parport_pc             36962  0 
dm_crypt               23199  1 
ppdev                  17113  0 
mceusb                 17906  0 
binfmt_misc            17540  1 
snd_hda_codec_hdmi     32040  4 
snd_hda_codec_realtek   330769  1 
snd_hda_intel          33390  3 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96714  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
nvidia              11713772  42 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
ir_lirc_codec          12898  0 
lirc_dev               19204  1 ir_lirc_codec
joydev                 17693  0 
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
ir_sony_decoder        12549  0 
lib80211_crypt_tkip    17390  0 
mei                    41480  0 
usbhid                 47198  0 
snd                    68266  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ir_jvc_decoder         12546  0 
wl                   2568210  0 
uvcvideo               72711  0 
ir_rc6_decoder         12546  0 
videodev               92992  1 uvcvideo
soundcore              12680  1 snd
ir_rc5_decoder         12546  0 
v4l2_compat_ioctl32    17083  1 videodev
hid                    95463  1 usbhid
psmouse                73882  0 
toshiba_bluetooth      12807  0 
jmb38x_ms              17646  0 
serio_raw              13166  0 
rc_rc6_mce             12502  0 
memstick               16569  1 jmb38x_ms
sparse_keymap          13890  0 
i7core_edac            27942  0 
edac_core              53746  3 i7core_edac
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lib80211               14991  2 lib80211_crypt_tkip,wl
ir_nec_decoder         12546  0 
ene_ir                 22796  0 
rc_core                26963  10 mceusb,ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,rc_rc6_mce,ir_nec_decoder,ene_ir
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
vesafb                 13809  1 
sdhci_pci              14032  0 
r8169                  52788  0 
ahci                   26002  3 
libahci                26861  1 ahci
sdhci                  32166  1 sdhci_pci
video                  19412  0 
+ free
             total       used       free     shared    buffers     cached
Mem:       8124760    1159840    6964920          0      85260     360632
-/+ buffers/cache:     713948    7410812
Swap:      8787964          0    8787964
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/00logging suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/00logging suspend suspend: 
/usr/lib/pm-utils/sleep.d/00logging suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=00logging
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 00logging ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/00powersave ]
+ [ -f /usr/lib/pm-utils/sleep.d/00powersave ]
+ hook=/usr/lib/pm-utils/sleep.d/00powersave
+ run_hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/00powersave
+ local hook=00powersave
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:00powersave ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:powersave ]
+ [ -x /usr/lib/pm-utils/sleep.d/00powersave ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/00powersave suspend suspend
+ command_exists pm-powersave
+ type pm-powersave
+ return 0
+ pm-powersave false
+ set -a
+ PM_UTILS_LIBDIR=/usr/lib/pm-utils
+ PM_UTILS_ETCDIR=/etc/pm
+ PM_UTILS_RUNDIR=/var/run/pm-utils
+ PATH=/sbin:/usr/sbin:/bin:/usr/bin:/usr/lib/pm-utils/bin
+ PM_LOGFILE=/var/log/pm-powersave.log
+ TEMPORARY_CPUFREQ_GOVERNOR=performance
+ LOCKDIR=/var/run/pm-utils/locks
+ STORAGEDIR=/var/run/pm-utils/pm-powersave/storage
+ NA=254
+ NX=253
+ DX=252
+ PM_FUNCTIONS=/usr/lib/pm-utils/functions
+ PM_QUIRKDB=/usr/lib/pm-utils/video-quirks
+ PM_LKW_QUIRKS=/var/cache/pm-utils/last_known_working.quirkdb
+ LC_COLLATE=C
+ HIBERNATE_MODE=
+ HIBERNATE_RESUME_POST_VIDEO=no
+ SLEEP_MODULE=auto
+ SUSPEND_MODULES=
+ HOOK_BLACKLIST=
+ ADD_PARAMETERS=
+ DROP_PARAMETERS=
+ PARAMETERS=/var/run/pm-utils/pm-powersave/storage/parameters
+ INHIBIT=/var/run/pm-utils/pm-powersave/storage/inhibit
+ PM_CMDLINE=false
+ BEFORE_HOOKS=
+ MODULE_HELP=
+ SUSPEND_MODULE=
+ HIBERNATE_MODULE=
+ SUSPEND_HYBRID_MODULE=
+ PM_HIBERNATE_DELAY=900
+ PM_RTC=/sys/class/rtc/rtc0
+ [ -f /usr/lib/pm-utils/defaults ]
+ . /usr/lib/pm-utils/defaults
+ [ -f /usr/lib/pm-utils/pm-powersave.defaults ]
+ set +a
+ [ -f /etc/pm/config.d/*[!~] ]
+ continue
+ [ -f /etc/pm/pm-powersave.config.d/*[!~] ]
+ continue
+ . /usr/lib/pm-utils/functions
+ export PM_DEBUG=true
+ is_set true
+ return 0
+ set -x
+ profiling
+ [  = true ]
+ profiling
+ [  = true ]
+ profiling
+ [  = true ]
+ [ auto = auto ]
+ SLEEP_MODULE=tuxonice uswsusp
+ mod=/usr/lib/pm-utils/module.d/tuxonice
+ [ -f /usr/lib/pm-utils/module.d/tuxonice ]
+ . /usr/lib/pm-utils/module.d/tuxonice
+ export TUXONICE_LOC
+ [ -d /sys/power/tuxonice ]
+ [ -d /sys/power/suspend2 ]
+ [ -n  ]
+ [ -z  -a -n  ]
+ [ -z  -a -n  ]
+ mod=/usr/lib/pm-utils/module.d/uswsusp
+ [ -f /usr/lib/pm-utils/module.d/uswsusp ]
+ . /usr/lib/pm-utils/module.d/uswsusp
+ [ -z  ]
+ command_exists s2ram
+ type s2ram
+ return 127
+ [ -z  ]
+ [ -f /sys/power/disk ]
+ grep -q disk /sys/power/state
+ [ -c /dev/snapshot ]
+ command_exists s2disk
+ type s2disk
+ return 127
+ [ -z  ]
+ grep -q mem /sys/power/state
+ command_exists s2both
+ type s2both
+ return 127
+ [ -z  ]
+ grep -q mem /sys/power/state
+ SUSPEND_MODULE=kernel
+ [ -z  ]
+ [ -f /sys/power/disk ]
+ grep -q disk /sys/power/state
+ HIBERNATE_MODULE=kernel
+ [ -z  -a -w /sys/class/rtc/rtc0/wakealarm ]
+ check_suspend
+ [ -n kernel ]
+ check_hibernate
+ [ -n kernel ]
+ is_set no
+ return 1
+ SUSPEND_HYBRID_MODULE=kernel
+ lock_and_load
+ try_lock pm-powersave.lock
+ local lock=/var/run/pm-utils/locks/pm-powersave.lock
+ mkdir -p /var/run/pm-utils/locks
+ touch /var/run/pm-utils/locks/pm-powersave.lock
+ exec
+ flock -x -n 3
+ return 0
+ trap remove_powersave_lock 0
+ mkdir -p /var/run/pm-utils/pm-powersave/storage
+ rm -f /var/run/pm-utils/pm-powersave/storage/inhibit
+ load_hook_blacklist
+ [  ]
+ return
+ init_logfile /var/log/pm-powersave.log
+ [ -z /var/log/pm-powersave.log ]
+ [ -h /var/log/pm-powersave.log ]
+ [ -f /var/log/pm-powersave.log -a ! -O /var/log/pm-powersave.log ]
+ export LOGGING=true
+ exec
+ exit 0
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/00powersave suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/00powersave suspend suspend: 
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=00powersave
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 00powersave ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/01PulseAudio ]
+ [ -f /usr/lib/pm-utils/sleep.d/01PulseAudio ]
+ hook=/usr/lib/pm-utils/sleep.d/01PulseAudio
+ run_hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/01PulseAudio
+ local hook=01PulseAudio
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:01PulseAudio ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:PulseAudio ]
+ [ -x /usr/lib/pm-utils/sleep.d/01PulseAudio ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend
+ suspend_pulse
+ get_pulse_users
+ test_pulse_system
+ getent passwd pulse
+ awk -F: {print $3}
+ PULSE_SYSTEM_USER=109
+ [ -z 109 ]
+ ps -C pulseaudio -o uid=
+ tr -d  
+ sed s/109//
+ getent passwd 1000
+ cut -f1 -d:
+ THIS_USER=charlie
+ save_pulse_state sink charlie
+ su charlie -c -- pacmd list-sinks
+ + index=
sed -n+  s/^[[:space:]*]*//; /\(index\|mute\)/p
read field value
Sessions still open, not unmounting
+ [ index = index ]
+ index=0
+ read field value
+ [ muted = index ]
+ savestate pulse:charlie:sink0 no
+ [ -n no ]
+ echo no
+ read field value
+ [ index = index ]
+ index=1
+ read field value
+ [ muted = index ]
+ savestate pulse:charlie:sink1 yes
+ [ -n yes ]
+ echo yes
+ read field value
+ save_pulse_state source charlie
+ + su charliesed -c -n -- s/^[[:space:]*]*//; /\(index\|mute\)/p pacmd list-sources

+ index=
+ read field value
Sessions still open, not unmounting
+ [ index = index ]
+ index=0
+ read field value
+ [ muted = index ]
+ savestate pulse:charlie:source0 yes
+ [ -n yes ]
+ echo yes
+ read field value
+ [ index = index ]
+ index=1
+ read field value
+ [ muted = index ]
+ savestate pulse:charlie:source1 yes
+ [ -n yes ]
+ echo yes
+ read field value
+ [ index = index ]
+ index=2
+ read field value
+ [ muted = index ]
+ savestate pulse:charlie:source2 yes
+ [ -n yes ]
+ echo yes
+ read field value
+ su charlie -c -- pacmd suspend true
+ get_pulse_users
+ test_pulse_system
+ getent+  passwd pulse
awk -F: {print $3}
+ PULSE_SYSTEM_USER=109
+ [ -z 109 ]
+ ps -C pulseaudio -o+  uid=
tr -d  
+ sed s/109//
+ getent+  passwdcut 1000 -f1
 -d:
+ THIS_USER=charlie
+ su charlie -c -- ck-list-sessions | grep "active = TRUE"
+ mute_pulse sink charlie
+ su charlie -c -- pacmd list-sinks
+ sed -n s/^[[:space:]*]*//; /\(index\|mute\)/p
+ index=
+ read field value
Sessions still open, not unmounting
+ [ index = index ]
+ index=0
+ su charlie -c -- pacmd                         set-sink-mute 0 yes
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
+ read field value
+ [ muted = index ]
+ read field value
+ [ index = index ]
+ index=1
+ su charlie -c -- pacmd                         set-sink-mute 1 yes
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
+ read field value
+ [ muted = index ]
+ read field value
+ mute_pulse source charlie
+ su charlie -c -- pacmd list-sources
+ + sed -n s/^[[:space:]*]*//; /\(index\|mute\)/p
index=
+ read field value
Sessions still open, not unmounting
+ [ index = index ]
+ index=0
+ su charlie -c -- pacmd                         set-source-mute 0 yes
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
+ read field value
+ [ muted = index ]
+ read field value
+ [ index = index ]
+ index=1
+ su charlie -c -- pacmd                         set-source-mute 1 yes
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
+ read field value
+ [ muted = index ]
+ read field value
+ [ index = index ]
+ index=2
+ su charlie -c -- pacmd                         set-source-mute 2 yes
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
+ read field value
+ [ muted = index ]
+ read field value
+ break
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=01PulseAudio
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 01PulseAudio ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/10_grub-common ]
+ hook=/etc/pm/sleep.d/10_grub-common
+ run_hook /etc/pm/sleep.d/10_grub-common suspend suspend
+ _run_hook /etc/pm/sleep.d/10_grub-common suspend suspend
+ log Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /etc/pm/sleep.d/10_grub-common suspend suspend: = -n ]
+ printf %s\n Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
+ hook_ok /etc/pm/sleep.d/10_grub-common
+ local hook=10_grub-common
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:10_grub-common ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:_grub-common ]
+ [ -x /etc/pm/sleep.d/10_grub-common ]
+ return 0
+ /etc/pm/sleep.d/10_grub-common suspend suspend
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /etc/pm/sleep.d/10_grub-common suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /etc/pm/sleep.d/10_grub-common suspend suspend: 
/etc/pm/sleep.d/10_grub-common suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=10_grub-common
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 10_grub-common ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/10_unattended-upgrades-hibernate ]
+ hook=/etc/pm/sleep.d/10_unattended-upgrades-hibernate
+ run_hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend
+ _run_hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend
+ log Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: = -n ]
+ printf %s\n Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
+ hook_ok /etc/pm/sleep.d/10_unattended-upgrades-hibernate
+ local hook=10_unattended-upgrades-hibernate
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:10_unattended-upgrades-hibernate ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:_unattended-upgrades-hibernate ]
+ [ -x /etc/pm/sleep.d/10_unattended-upgrades-hibernate ]
+ return 0
+ /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: 
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=10_unattended-upgrades-hibernate
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 10_unattended-upgrades-hibernate ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/49bluetooth ]
+ [ -f /usr/lib/pm-utils/sleep.d/49bluetooth ]
+ hook=/usr/lib/pm-utils/sleep.d/49bluetooth
+ run_hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/49bluetooth
+ local hook=49bluetooth
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:49bluetooth ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:bluetooth ]
+ [ -x /usr/lib/pm-utils/sleep.d/49bluetooth ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend
+ [ -f /proc/acpi/ibm/bluetooth ]
+ exit 254
+ local status=254
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: 
/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: + hook_exit_status 254
+ log not applicable.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ not applicable. = -n ]
+ printf %s\n not applicable.
not applicable.
+ LAST_HOOK=49bluetooth
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 49bluetooth ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/55NetworkManager ]
+ [ -f /usr/lib/pm-utils/sleep.d/55NetworkManager ]
+ hook=/usr/lib/pm-utils/sleep.d/55NetworkManager
+ run_hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/55NetworkManager
+ local hook=55NetworkManager
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:55NetworkManager ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:NetworkManager ]
+ [ -x /usr/lib/pm-utils/sleep.d/55NetworkManager ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend
+ suspend_nm
+ printf Having NetworkManager put all interaces to sleep...
Having NetworkManager put all interaces to sleep...+ dbus_send --print-reply --system --dest=org.freedesktop.NetworkManager /org/freedesktop/NetworkManager org.freedesktop.NetworkManager.sleep
+ command dbus-send --print-reply --system --dest=org.freedesktop.NetworkManager /org/freedesktop/NetworkManager org.freedesktop.NetworkManager.sleep
+ return 254
+ echo Failed.
Failed.
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: 
/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=55NetworkManager
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 55NetworkManager ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/60_wpa_supplicant ]
+ [ -f /usr/lib/pm-utils/sleep.d/60_wpa_supplicant ]
+ hook=/usr/lib/pm-utils/sleep.d/60_wpa_supplicant
+ run_hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/60_wpa_supplicant
+ local hook=60_wpa_supplicant
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:60_wpa_supplicant ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:_wpa_supplicant ]
+ [ -x /usr/lib/pm-utils/sleep.d/60_wpa_supplicant ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: 
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=60_wpa_supplicant
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 60_wpa_supplicant ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/75modules ]
+ [ -f /usr/lib/pm-utils/sleep.d/75modules ]
+ hook=/usr/lib/pm-utils/sleep.d/75modules
+ run_hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/75modules
+ local hook=75modules
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:75modules ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:modules ]
+ [ -x /usr/lib/pm-utils/sleep.d/75modules ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/75modules suspend suspend
+ suspend_modules
+ [ -z  ]
+ return 254
+ local status=254
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/75modules suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/75modules suspend suspend: 
/usr/lib/pm-utils/sleep.d/75modules suspend suspend: + hook_exit_status 254
+ log not applicable.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ not applicable. = -n ]
+ printf %s\n not applicable.
not applicable.
+ LAST_HOOK=75modules
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 75modules ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/90clock ]
+ [ -f /usr/lib/pm-utils/sleep.d/90clock ]
+ hook=/usr/lib/pm-utils/sleep.d/90clock
+ run_hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/90clock
+ local hook=90clock
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:90clock ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:clock ]
+ [ -x /usr/lib/pm-utils/sleep.d/90clock ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/90clock suspend suspend
+ is_set 
+ return 2
+ exit 254
+ local status=254
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/90clock suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/90clock suspend suspend: 
/usr/lib/pm-utils/sleep.d/90clock suspend suspend: + hook_exit_status 254
+ log not applicable.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ not applicable. = -n ]
+ printf %s\n not applicable.
not applicable.
+ LAST_HOOK=90clock
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 90clock ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/94cpufreq ]
+ [ -f /usr/lib/pm-utils/sleep.d/94cpufreq ]
+ hook=/usr/lib/pm-utils/sleep.d/94cpufreq
+ run_hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/94cpufreq
+ local hook=94cpufreq
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:94cpufreq ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:cpufreq ]
+ [ -x /usr/lib/pm-utils/sleep.d/94cpufreq ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend
+ [ -d /sys/devices/system/cpu/ ]
+ hibernate_cpufreq
+ cd /sys/devices/system/cpu/
+ [ -L cpu0/cpufreq ]
+ gov=cpu0/cpufreq/scaling_governor
+ [ -f cpu0/cpufreq/scaling_governor ]
+ grep -q performance cpu0/cpufreq/scaling_available_governors
+ savestate cpu0_governor
+ [ -n  ]
+ cat
+ echo performance
+ [ -L cpu1/cpufreq ]
+ gov=cpu1/cpufreq/scaling_governor
+ [ -f cpu1/cpufreq/scaling_governor ]
+ grep -q performance cpu1/cpufreq/scaling_available_governors
+ savestate cpu1_governor
+ [ -n  ]
+ cat
+ echo performance
+ [ -L cpu2/cpufreq ]
+ gov=cpu2/cpufreq/scaling_governor
+ [ -f cpu2/cpufreq/scaling_governor ]
+ grep -q performance cpu2/cpufreq/scaling_available_governors
+ savestate cpu2_governor
+ [ -n  ]
+ cat
+ echo performance
+ [ -L cpu3/cpufreq ]
+ gov=cpu3/cpufreq/scaling_governor
+ [ -f cpu3/cpufreq/scaling_governor ]
+ grep -q performance cpu3/cpufreq/scaling_available_governors
+ savestate cpu3_governor
+ [ -n  ]
+ cat
+ echo performance
+ [ -L cpu4/cpufreq ]
+ gov=cpu4/cpufreq/scaling_governor
+ [ -f cpu4/cpufreq/scaling_governor ]
+ grep -q performance cpu4/cpufreq/scaling_available_governors
+ savestate cpu4_governor
+ [ -n  ]
+ cat
+ echo performance
+ [ -L cpu5/cpufreq ]
+ gov=cpu5/cpufreq/scaling_governor
+ [ -f cpu5/cpufreq/scaling_governor ]
+ grep -q performance cpu5/cpufreq/scaling_available_governors
+ savestate cpu5_governor
+ [ -n  ]
+ cat
+ echo performance
+ [ -L cpu6/cpufreq ]
+ gov=cpu6/cpufreq/scaling_governor
+ [ -f cpu6/cpufreq/scaling_governor ]
+ grep -q performance cpu6/cpufreq/scaling_available_governors
+ savestate cpu6_governor
+ [ -n  ]
+ cat
+ echo performance
+ [ -L cpu7/cpufreq ]
+ gov=cpu7/cpufreq/scaling_governor
+ [ -f cpu7/cpufreq/scaling_governor ]
+ grep -q performance cpu7/cpufreq/scaling_available_governors
+ savestate cpu7_governor
+ [ -n  ]
+ cat
+ echo performance
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: 
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=94cpufreq
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 94cpufreq ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/95anacron ]
+ [ -f /usr/lib/pm-utils/sleep.d/95anacron ]
+ hook=/usr/lib/pm-utils/sleep.d/95anacron
+ run_hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/95anacron
+ local hook=95anacron
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:95anacron ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:anacron ]
+ [ -x /usr/lib/pm-utils/sleep.d/95anacron ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/95anacron suspend suspend
stop: Unknown instance: 
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/95anacron suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/95anacron suspend suspend: 
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=95anacron
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 95anacron ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/95hdparm-apm ]
+ [ -f /usr/lib/pm-utils/sleep.d/95hdparm-apm ]
+ hook=/usr/lib/pm-utils/sleep.d/95hdparm-apm
+ run_hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/95hdparm-apm
+ local hook=95hdparm-apm
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:95hdparm-apm ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:hdparm-apm ]
+ [ -x /usr/lib/pm-utils/sleep.d/95hdparm-apm ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend
+ local status=254
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: 
/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: + hook_exit_status 254
+ log not applicable.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ not applicable. = -n ]
+ printf %s\n not applicable.
not applicable.
+ LAST_HOOK=95hdparm-apm
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 95hdparm-apm ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/95led ]
+ [ -f /usr/lib/pm-utils/sleep.d/95led ]
+ hook=/usr/lib/pm-utils/sleep.d/95led
+ run_hook /usr/lib/pm-utils/sleep.d/95led suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/95led suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/95led
+ local hook=95led
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:95led ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:led ]
+ [ -x /usr/lib/pm-utils/sleep.d/95led ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/95led suspend suspend
+ local status=254
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/95led suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/95led suspend suspend: 
/usr/lib/pm-utils/sleep.d/95led suspend suspend: + hook_exit_status 254
+ log not applicable.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ not applicable. = -n ]
+ printf %s\n not applicable.
not applicable.
+ LAST_HOOK=95led
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 95led ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/98video-quirk-db-handler ]
+ [ -f /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler ]
+ hook=/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler
+ run_hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler
+ local hook=98video-quirk-db-handler
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:98video-quirk-db-handler ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:video-quirk-db-handler ]
+ [ -x /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend
+ [[ -n true ]]
+ export 'PS4=${BASH_SOURCE}@${LINENO}(${FUNCNAME[0]}): '
+ PS4='${BASH_SOURCE}@${LINENO}(${FUNCNAME[0]}): '
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@10(): set -x
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@25(): possible_video_quirks=' --quirk-dpms-on
	   --quirk-dpms-suspend
	   --quirk-s3-mode
	   --quirk-s3-bios
	   --quirk-vbe-post
	   --quirk-vbe-post
	   --quirk-vga-mode-3
	   --quirk-vbemode-restore
	   --quirk-vbestate-restore
	   --quirk-reset-brightness
	   --quirk-radeon-off
	   --quirk-no-fb
	   --quirk-save-pci'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@40(): possible_system_properties='system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@343(): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@347(): precache_dmivars
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@170(precache_dmivars): local p q f
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.firmware.version
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.firmware.version* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_firmware_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_firmware_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.firmware.version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@107(dmisysget): _dmisysget bios_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@100(_dmisysget): [[ -r /sys/class/dmi/id/bios_version ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@101(_dmisysget): read RES
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=1.10
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=1.10
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_firmware_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.firmware.vendor
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.vendor =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.firmware.vendor* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_firmware_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_firmware_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.firmware.vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@106(dmisysget): _dmisysget bios_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@100(_dmisysget): [[ -r /sys/class/dmi/id/bios_vendor ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@101(_dmisysget): read RES
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=TOSHIBA
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=TOSHIBA
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_firmware_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.firmware.release_date
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.release_date =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.firmware.release_date* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_firmware_release_date
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_firmware_release_date
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.firmware.release_date
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@108(dmisysget): _dmisysget bios_date
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@100(_dmisysget): [[ -r /sys/class/dmi/id/bios_date ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@101(_dmisysget): read RES
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=04/19/10
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=04/19/10
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_firmware_release_date
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.hardware.vendor
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.hardware.vendor =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.hardware.vendor* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_hardware_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_hardware_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.hardware.vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@109(dmisysget): _dmisysget sys_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@100(_dmisysget): [[ -r /sys/class/dmi/id/sys_vendor ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@101(_dmisysget): read RES
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=TOSHIBA
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=TOSHIBA
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_hardware_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.hardware.product
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.hardware.product =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.hardware.product* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_hardware_product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_hardware_product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.hardware.product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@110(dmisysget): _dmisysget product_name
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@100(_dmisysget): [[ -r /sys/class/dmi/id/product_name ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@101(_dmisysget): read RES
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES='Satellite A660'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES='Satellite A660'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_hardware_product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.hardware.version
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.hardware.version =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.hardware.version* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_hardware_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_hardware_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.hardware.version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@111(dmisysget): _dmisysget product_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@100(_dmisysget): [[ -r /sys/class/dmi/id/product_version ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@101(_dmisysget): read RES
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=PSAW3E-01100TEN
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=PSAW3E-01100TEN
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_hardware_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.board.product
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.board.product =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.board.product* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_board_product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_board_product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.board.product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@112(dmisysget): _dmisysget board_name
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@100(_dmisysget): [[ -r /sys/class/dmi/id/board_name ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@101(_dmisysget): read RES
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=NWQAA
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=NWQAA
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_board_product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.board.version
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.board.version =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.board.version* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_board_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_board_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.board.version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@113(dmisysget): _dmisysget board_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@100(_dmisysget): [[ -r /sys/class/dmi/id/board_version ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@101(_dmisysget): read RES
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=1.00
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=1.00
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_board_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.board.vendor
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.board.vendor =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.board.vendor* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_board_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_board_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.board.vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@114(dmisysget): _dmisysget board_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@100(_dmisysget): [[ -r /sys/class/dmi/id/board_vendor ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@101(_dmisysget): read RES
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=TOSHIBA
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=TOSHIBA
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_board_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.hardware.primary_video.vendor
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.hardware.primary_video.vendor =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.hardware.primary_video.vendor* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_hardware_primary_video_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_hardware_primary_video_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.hardware.primary_video.vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@115(dmisysget): videoget vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@65(videoget): local dev pci
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@66(videoget): pci=/sys/bus/pci/devices
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:00.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:00.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:03.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:03.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:08.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:08.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:08.1/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:08.1/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:08.2/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:08.2/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:08.3/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:08.3/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:10.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:10.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:10.1/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:10.1/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:16.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:16.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x078000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1a.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1a.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x0c0320 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1b.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1b.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x040300 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.1/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.1/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.2/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.2/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.3/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.3/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.4/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.4/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1d.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1d.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x0c0320 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1e.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1e.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060401 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1f.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1f.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060100 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1f.2/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1f.2/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x010601 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1f.3/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1f.3/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x0c0500 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:01:00.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:01:00.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x030000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@70(videoget): case $1 in
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@71(videoget): cat /sys/bus/pci/devices/0000:01:00.0/vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@71(videoget): RES=0x10de
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@91(videoget): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=0x10de
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=0x10de
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_hardware_primary_video_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.hardware.primary_video.product
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.hardware.primary_video.product =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.hardware.primary_video.product* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_hardware_primary_video_product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_hardware_primary_video_product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.hardware.primary_video.product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@116(dmisysget): videoget device
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@65(videoget): local dev pci
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@66(videoget): pci=/sys/bus/pci/devices
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:00.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:00.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:03.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:03.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:08.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:08.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:08.1/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:08.1/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:08.2/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:08.2/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:08.3/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:08.3/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:10.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:10.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:10.1/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:10.1/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:16.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:16.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x078000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1a.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1a.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x0c0320 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1b.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1b.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x040300 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.1/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.1/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.2/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.2/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.3/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.3/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.4/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.4/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1d.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1d.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x0c0320 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1e.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1e.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060401 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1f.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1f.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060100 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1f.2/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1f.2/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x010601 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1f.3/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1f.3/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x0c0500 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:01:00.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:01:00.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x030000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@70(videoget): case $1 in
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@72(videoget): cat /sys/bus/pci/devices/0000:01:00.0/device
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@72(videoget): RES=0x0a29
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@91(videoget): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=0x0a29
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=0x0a29
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_hardware_primary_video_product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.hardware.primary_video.driver
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.hardware.primary_video.driver =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.hardware.primary_video.driver* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_hardware_primary_video_driver
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_hardware_primary_video_driver
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.hardware.primary_video.driver
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@117(dmisysget): videoget driver
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@65(videoget): local dev pci
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@66(videoget): pci=/sys/bus/pci/devices
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:00.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:00.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:03.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:03.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:08.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:08.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:08.1/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:08.1/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:08.2/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:08.2/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:08.3/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:08.3/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:10.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:10.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:10.1/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:10.1/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:16.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:16.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x078000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1a.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1a.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x0c0320 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1b.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1b.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x040300 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.1/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.1/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.2/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.2/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.3/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.3/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.4/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.4/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1d.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1d.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x0c0320 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1e.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1e.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060401 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1f.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1f.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060100 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1f.2/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1f.2/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x010601 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1f.3/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1f.3/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x0c0500 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:01:00.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:01:00.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x030000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@70(videoget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@74(videoget): [[ -L /sys/bus/pci/devices/0000:01:00.0/driver ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@75(videoget): readlink /sys/bus/pci/devices/0000:01:00.0/driver
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@75(videoget): RES=../../../../bus/pci/drivers/nvidia
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@76(videoget): RES=nvidia
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@91(videoget): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=nvidia
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=nvidia
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_hardware_primary_video_driver
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.hardware.primary_video.using_kms
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.hardware.primary_video.using_kms =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.hardware.primary_video.using_kms* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_hardware_primary_video_using_kms
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_hardware_primary_video_using_kms
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.hardware.primary_video.using_kms
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@118(dmisysget): videoget using_kms
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@65(videoget): local dev pci
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@66(videoget): pci=/sys/bus/pci/devices
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:00.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:00.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:03.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:03.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:08.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:08.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:08.1/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:08.1/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:08.2/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:08.2/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:08.3/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:08.3/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:10.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:10.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:10.1/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:10.1/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:16.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:16.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x078000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1a.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1a.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x0c0320 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1b.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1b.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x040300 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.1/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.1/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.2/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.2/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.3/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.3/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.4/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.4/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1d.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1d.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x0c0320 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1e.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1e.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060401 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1f.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1f.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060100 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1f.2/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1f.2/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x010601 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1f.3/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1f.3/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x0c0500 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:01:00.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:01:00.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x030000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@70(videoget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@84(videoget): using_kms
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@60(using_kms): grep -q -E '(nouveau|drm)fb' /proc/fb
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@87(videoget): RES=false
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@91(videoget): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=false
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=false
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_hardware_primary_video_using_kms
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.kernel.version
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.kernel.version =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.kernel.version* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_kernel_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_kernel_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.kernel.version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@119(dmisysget): uname -r
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@119(dmisysget): RES=3.0.0-14-generic
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=3.0.0-14-generic
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=3.0.0-14-generic
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_kernel_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@181(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@352(): has_parameter --quirk-test
//usr/lib/pm-utils/functions@240(has_parameter): get_parameters
//usr/lib/pm-utils/functions@235(get_parameters): cat /var/run/pm-utils/pm-suspend/storage/parameters
/usr/lib/pm-utils/functions@244(has_parameter): return 1
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@358(): using_kms
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@60(using_kms): grep -q -E '(nouveau|drm)fb' /proc/fb
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@363(): using_nvidia
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@54(using_nvidia): [[ -d /sys/module/nvidia ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@365(): remove_parameters --quirk-dpms-on --quirk-dpms-suspend --quirk-s3-mode --quirk-s3-bios --quirk-vbe-post --quirk-vbe-post --quirk-vga-mode-3 --quirk-vbemode-restore --quirk-vbestate-restore --quirk-reset-brightness --quirk-radeon-off --quirk-no-fb --quirk-save-pci
/usr/lib/pm-utils/functions@211(remove_parameters): local p
/usr/lib/pm-utils/functions@212(remove_parameters): '[' --quirk-dpms-on = all ']'
/usr/lib/pm-utils/functions@215(remove_parameters): echo ''
/usr/lib/pm-utils/functions@216(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@217(remove_parameters): echo --quirk-dpms-on
/usr/lib/pm-utils/functions@216(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@217(remove_parameters): echo --quirk-dpms-suspend
/usr/lib/pm-utils/functions@216(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@217(remove_parameters): echo --quirk-s3-mode
/usr/lib/pm-utils/functions@216(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@217(remove_parameters): echo --quirk-s3-bios
/usr/lib/pm-utils/functions@216(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@217(remove_parameters): echo --quirk-vbe-post
/usr/lib/pm-utils/functions@216(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@217(remove_parameters): echo --quirk-vbe-post
/usr/lib/pm-utils/functions@216(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@217(remove_parameters): echo --quirk-vga-mode-3
/usr/lib/pm-utils/functions@216(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@217(remove_parameters): echo --quirk-vbemode-restore
/usr/lib/pm-utils/functions@216(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@217(remove_parameters): echo --quirk-vbestate-restore
/usr/lib/pm-utils/functions@216(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@217(remove_parameters): echo --quirk-reset-brightness
/usr/lib/pm-utils/functions@216(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@217(remove_parameters): echo --quirk-radeon-off
/usr/lib/pm-utils/functions@216(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@217(remove_parameters): echo --quirk-no-fb
/usr/lib/pm-utils/functions@216(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@217(remove_parameters): echo --quirk-save-pci
/usr/lib/pm-utils/functions@220(remove_parameters): grep -vxFf /var/run/pm-utils/pm-suspend/storage/parameters.rm /var/run/pm-utils/pm-suspend/storage/parameters
/usr/lib/pm-utils/functions@222(remove_parameters): cp -f /var/run/pm-utils/pm-suspend/storage/parameters.new /var/run/pm-utils/pm-suspend/storage/parameters
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@366(): echo 'nVidia binary video drive detected, not using quirks.'
nVidia binary video drive detected, not using quirks.
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: 
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=98video-quirk-db-handler
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 98video-quirk-db-handler ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ get_parameters
+ cat /var/run/pm-utils/pm-suspend/storage/parameters
+ export PM_CMDLINE=
+ rm -f /var/run/pm-utils/pm-suspend/storage/parameters.new
+ [ -f /etc/pm/sleep.d/99video ]
+ [ -f /usr/lib/pm-utils/sleep.d/99video ]
+ hook=/usr/lib/pm-utils/sleep.d/99video
+ run_hook /usr/lib/pm-utils/sleep.d/99video suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/99video suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/99video
+ local hook=99video
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:99video ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:video ]
+ [ -x /usr/lib/pm-utils/sleep.d/99video ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/99video suspend suspend
+ command_exists vbetool
+ type vbetool
+ return 0
+ command_exists radeontool
+ type radeontool
+ return 0
+ maybe_chvt
+ is_set 
+ return 2
+ + fgconsole
savestate console
+ [ -n  ]
+ cat
+ chvt 63
+ suspend_video
+ local acpi_flag=0
+ quirk 
+ is_set 
+ return 2
+ quirk 
+ is_set 
+ return 2
+ sysctl -w kernel.acpi_video_flags=0
kernel.acpi_video_flags = 0
+ quirk 
+ is_set 
+ return 2
+ quirk 
+ is_set 
+ return 2
+ quirk 
+ is_set 
+ return 2
+ quirk 
+ is_set 
+ return 2
+ quirk 
+ is_set 
+ return 2
+ quirk 
+ is_set 
+ return 2
+ quirk 
+ is_set 
+ return 2
+ save_fbcon
+ local con
+ [ -f /sys/class/graphics/fb0/state ]
+ echo 1
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/99video suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/99video suspend suspend: 
/usr/lib/pm-utils/sleep.d/99video suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=99video
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 99video ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/novatel_3g_suspend ]
+ hook=/etc/pm/sleep.d/novatel_3g_suspend
+ run_hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend
+ _run_hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend
+ log Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend: = -n ]
+ printf %s\n Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
+ hook_ok /etc/pm/sleep.d/novatel_3g_suspend
+ local hook=novatel_3g_suspend
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:novatel_3g_suspend ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:novatel_3g_suspend ]
+ [ -x /etc/pm/sleep.d/novatel_3g_suspend ]
+ return 0
+ /etc/pm/sleep.d/novatel_3g_suspend suspend suspend
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /etc/pm/sleep.d/novatel_3g_suspend suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /etc/pm/sleep.d/novatel_3g_suspend suspend suspend: 
/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=novatel_3g_suspend
+ IFS=

+ IFS= 	

+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ return 0
+ date
+ log Mon Dec 19 11:43:44 AST 2011: performing suspend
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Mon Dec 19 11:43:44 AST 2011: performing suspend = -n ]
+ printf %s\n Mon Dec 19 11:43:44 AST 2011: performing suspend
Mon Dec 19 11:43:44 AST 2011: performing suspend
+ sync
+ do_suspend
+ echo -n mem
+ date
+ log Mon Dec 19 11:43:55 AST 2011: Awake.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Mon Dec 19 11:43:55 AST 2011: Awake. = -n ]
+ printf %s\n Mon Dec 19 11:43:55 AST 2011: Awake.
Mon Dec 19 11:43:55 AST 2011: Awake.
+ date
+ log Mon Dec 19 11:43:55 AST 2011: Running hooks for resume
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Mon Dec 19 11:43:55 AST 2011: Running hooks for resume = -n ]
+ printf %s\n Mon Dec 19 11:43:55 AST 2011: Running hooks for resume
Mon Dec 19 11:43:55 AST 2011: Running hooks for resume
+ run_hooks sleep resume suspend reverse
+ _run_hooks sleep resume suspend reverse
+ local syshooks=/etc/pm/sleep.d
+ local phooks=/usr/lib/pm-utils/sleep.d
+ command_exists before_hooks
+ type before_hooks
+ return 0
+ before_hooks
+ [ -z  ]
+ return 0
+ local sort=sort
+ local base
+ local hook
+ local oifs= 	

+ local nifs=

+ IFS=

+ [ reverse = reverse ]
+ sort=sort -r
+ IFS= 	

+ + [sort -O -r /etc/pm/sleep.d/10_grub-common
 ]
+ echo 10_grub-common
+ + [ -O /etc/pm/sleep.d/10_unattended-upgrades-hibernateuniq ]

+ echo 10_unattended-upgrades-hibernate
+ [ -O /etc/pm/sleep.d/novatel_3g_suspend ]
+ echo novatel_3g_suspend
+ [ -O /usr/lib/pm-utils/sleep.d/000kernel-change ]
+ echo 000kernel-change
+ [ -O /usr/lib/pm-utils/sleep.d/00logging ]
+ echo 00logging
+ [ -O /usr/lib/pm-utils/sleep.d/00powersave ]
+ echo 00powersave
+ [ -O /usr/lib/pm-utils/sleep.d/01PulseAudio ]
+ echo 01PulseAudio
+ [ -O /usr/lib/pm-utils/sleep.d/49bluetooth ]
+ echo 49bluetooth
+ [ -O /usr/lib/pm-utils/sleep.d/55NetworkManager ]
+ echo 55NetworkManager
+ [ -O /usr/lib/pm-utils/sleep.d/60_wpa_supplicant ]
+ echo 60_wpa_supplicant
+ [ -O /usr/lib/pm-utils/sleep.d/75modules ]
+ echo 75modules
+ [ -O /usr/lib/pm-utils/sleep.d/90clock ]
+ echo 90clock
+ [ -O /usr/lib/pm-utils/sleep.d/94cpufreq ]
+ echo 94cpufreq
+ [ -O /usr/lib/pm-utils/sleep.d/95anacron ]
+ echo 95anacron
+ [ -O /usr/lib/pm-utils/sleep.d/95hdparm-apm ]
+ echo 95hdparm-apm
+ [ -O /usr/lib/pm-utils/sleep.d/95led ]
+ echo 95led
+ [ -O /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler ]
+ echo 98video-quirk-db-handler
+ [ -O /usr/lib/pm-utils/sleep.d/99video ]
+ echo 99video
+ IFS= 	

+ [ reverse -a reverse = reverse -a novatel_3g_suspend ]
+ [ novatel_3g_suspend > novatel_3g_suspend ]
+ [ ! reverse ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/novatel_3g_suspend ]
+ hook=/etc/pm/sleep.d/novatel_3g_suspend
+ run_hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend
+ _run_hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend
+ log Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend: = -n ]
+ printf %s\n Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:
+ hook_ok /etc/pm/sleep.d/novatel_3g_suspend
+ local hook=novatel_3g_suspend
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:novatel_3g_suspend ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:novatel_3g_suspend ]
+ [ -x /etc/pm/sleep.d/novatel_3g_suspend ]
+ return 0
+ /etc/pm/sleep.d/novatel_3g_suspend resume suspend
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /etc/pm/sleep.d/novatel_3g_suspend resume suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /etc/pm/sleep.d/novatel_3g_suspend resume suspend: 
/etc/pm/sleep.d/novatel_3g_suspend resume suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=novatel_3g_suspend
+ IFS=

+ IFS= 	

+ [ reverse -a reverse = reverse -a novatel_3g_suspend ]
+ [ 99video > novatel_3g_suspend ]
+ [ ! reverse ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/99video ]
+ [ -f /usr/lib/pm-utils/sleep.d/99video ]
+ hook=/usr/lib/pm-utils/sleep.d/99video
+ run_hook /usr/lib/pm-utils/sleep.d/99video resume suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/99video resume suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/99video
+ local hook=99video
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:99video ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:video ]
+ [ -x /usr/lib/pm-utils/sleep.d/99video ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/99video resume suspend
+ command_exists vbetool
+ type vbetool
+ return 0
+ command_exists radeontool
+ type radeontool
+ return 0
+ resume_video
+ quirk 
+ is_set 
+ return 2
+ quirk 
+ is_set 
+ return 2
+ quirk 
+ is_set 
+ return 2
+ quirk 
+ is_set 
+ return 2
+ resume_fbcon
+ local con
+ [ -f /sys/class/graphics/fb0/state ]
+ echo 0
+ quirk 
+ is_set 
+ return 2
+ quirk 
+ is_set 
+ return 2
+ quirk 
+ is_set 
+ return 2
+ return 0
+ maybe_deallocvt
+ state_exists console
+ [ -O /var/run/pm-utils/pm-suspend/storage/state:console ]
+ restorestate console
+ state_exists console
+ [ -O /var/run/pm-utils/pm-suspend/storage/state:console ]
+ cat /var/run/pm-utils/pm-suspend/storage/state:console
+ chvt 7
+ deallocvt 63
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/99video resume suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/99video resume suspend: 
/usr/lib/pm-utils/sleep.d/99video resume suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=99video
+ IFS=

+ IFS= 	

+ [ reverse -a reverse = reverse -a 99video ]
+ [ 98video-quirk-db-handler > 99video ]
+ [ ! reverse ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/98video-quirk-db-handler ]
+ [ -f /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler ]
+ hook=/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler
+ run_hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler
+ local hook=98video-quirk-db-handler
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:98video-quirk-db-handler ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:video-quirk-db-handler ]
+ [ -x /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend
+ [[ -n true ]]
+ export 'PS4=${BASH_SOURCE}@${LINENO}(${FUNCNAME[0]}): '
+ PS4='${BASH_SOURCE}@${LINENO}(${FUNCNAME[0]}): '
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@10(): set -x
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@25(): possible_video_quirks=' --quirk-dpms-on
	   --quirk-dpms-suspend
	   --quirk-s3-mode
	   --quirk-s3-bios
	   --quirk-vbe-post
	   --quirk-vbe-post
	   --quirk-vga-mode-3
	   --quirk-vbemode-restore
	   --quirk-vbestate-restore
	   --quirk-reset-brightness
	   --quirk-radeon-off
	   --quirk-no-fb
	   --quirk-save-pci'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@40(): possible_system_properties='system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@343(): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@436(): state_exists video_quirks
/usr/lib/pm-utils/functions@185(state_exists): '[' -O /var/run/pm-utils/pm-suspend/storage/state:video_quirks ']'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@440(): has_parameter --store-quirks-as-lkw
//usr/lib/pm-utils/functions@240(has_parameter): get_parameters
//usr/lib/pm-utils/functions@235(get_parameters): cat /var/run/pm-utils/pm-suspend/storage/parameters
/usr/lib/pm-utils/functions@244(has_parameter): return 1
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: 
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=98video-quirk-db-handler
+ IFS=

+ IFS= 	

+ [ reverse -a reverse = reverse -a 98video-quirk-db-handler ]
+ [ 95led > 98video-quirk-db-handler ]
+ [ ! reverse ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/95led ]
+ [ -f /usr/lib/pm-utils/sleep.d/95led ]
+ hook=/usr/lib/pm-utils/sleep.d/95led
+ run_hook /usr/lib/pm-utils/sleep.d/95led resume suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/95led resume suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/95led
+ local hook=95led
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:95led ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:led ]
+ [ -x /usr/lib/pm-utils/sleep.d/95led ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/95led resume suspend
+ local status=254
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/95led resume suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/95led resume suspend: 
/usr/lib/pm-utils/sleep.d/95led resume suspend: + hook_exit_status 254
+ log not applicable.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ not applicable. = -n ]
+ printf %s\n not applicable.
not applicable.
+ LAST_HOOK=95led
+ IFS=

+ IFS= 	

+ [ reverse -a reverse = reverse -a 95led ]
+ [ 95hdparm-apm > 95led ]
+ [ ! reverse ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/95hdparm-apm ]
+ [ -f /usr/lib/pm-utils/sleep.d/95hdparm-apm ]
+ hook=/usr/lib/pm-utils/sleep.d/95hdparm-apm
+ run_hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/95hdparm-apm
+ local hook=95hdparm-apm
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:95hdparm-apm ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:hdparm-apm ]
+ [ -x /usr/lib/pm-utils/sleep.d/95hdparm-apm ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: 
/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=95hdparm-apm
+ IFS=

+ IFS= 	

+ [ reverse -a reverse = reverse -a 95hdparm-apm ]
+ [ 95anacron > 95hdparm-apm ]
+ [ ! reverse ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/95anacron ]
+ [ -f /usr/lib/pm-utils/sleep.d/95anacron ]
+ hook=/usr/lib/pm-utils/sleep.d/95anacron
+ run_hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/95anacron
+ local hook=95anacron
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:95anacron ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:anacron ]
+ [ -x /usr/lib/pm-utils/sleep.d/95anacron ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/95anacron resume suspend
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/95anacron resume suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/95anacron resume suspend: 
/usr/lib/pm-utils/sleep.d/95anacron resume suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=95anacron
+ IFS=

+ IFS= 	

+ [ reverse -a reverse = reverse -a 95anacron ]
+ [ 94cpufreq > 95anacron ]
+ [ ! reverse ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/94cpufreq ]
+ [ -f /usr/lib/pm-utils/sleep.d/94cpufreq ]
+ hook=/usr/lib/pm-utils/sleep.d/94cpufreq
+ run_hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/94cpufreq
+ local hook=94cpufreq
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:94cpufreq ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:cpufreq ]
+ [ -x /usr/lib/pm-utils/sleep.d/94cpufreq ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend
+ [ -d /sys/devices/system/cpu/ ]
+ thaw_cpufreq
+ cd /sys/devices/system/cpu/
+ [ -f cpu0/cpufreq/scaling_governor ]
+ state_exists cpu0_governor
+ [ -O /var/run/pm-utils/pm-suspend/storage/state:cpu0_governor ]
+ restorestate cpu0_governor
+ state_exists cpu0_governor
+ [ -O /var/run/pm-utils/pm-suspend/storage/state:cpu0_governor ]
+ cat /var/run/pm-utils/pm-suspend/storage/state:cpu0_governor
+ [ -f cpu1/cpufreq/scaling_governor ]
+ state_exists cpu1_governor
+ [ -O /var/run/pm-utils/pm-suspend/storage/state:cpu1_governor ]
+ restorestate cpu1_governor
+ state_exists cpu1_governor
+ [ -O /var/run/pm-utils/pm-suspend/storage/state:cpu1_governor ]
+ cat /var/run/pm-utils/pm-suspend/storage/state:cpu1_governor
+ [ -f cpu2/cpufreq/scaling_governor ]
+ state_exists cpu2_governor
+ [ -O /var/run/pm-utils/pm-suspend/storage/state:cpu2_governor ]
+ restorestate cpu2_governor
+ state_exists cpu2_governor
+ [ -O /var/run/pm-utils/pm-suspend/storage/state:cpu2_governor ]
+ cat /var/run/pm-utils/pm-suspend/storage/state:cpu2_governor
+ [ -f cpu3/cpufreq/scaling_governor ]
+ state_exists cpu3_governor
+ [ -O /var/run/pm-utils/pm-suspend/storage/state:cpu3_governor ]
+ restorestate cpu3_governor
+ state_exists cpu3_governor
+ [ -O /var/run/pm-utils/pm-suspend/storage/state:cpu3_governor ]
+ cat /var/run/pm-utils/pm-suspend/storage/state:cpu3_governor
+ [ -f cpu4/cpufreq/scaling_governor ]
+ state_exists cpu4_governor
+ [ -O /var/run/pm-utils/pm-suspend/storage/state:cpu4_governor ]
+ restorestate cpu4_governor
+ state_exists cpu4_governor
+ [ -O /var/run/pm-utils/pm-suspend/storage/state:cpu4_governor ]
+ cat /var/run/pm-utils/pm-suspend/storage/state:cpu4_governor
+ [ -f cpu5/cpufreq/scaling_governor ]
+ state_exists cpu5_governor
+ [ -O /var/run/pm-utils/pm-suspend/storage/state:cpu5_governor ]
+ restorestate cpu5_governor
+ state_exists cpu5_governor
+ [ -O /var/run/pm-utils/pm-suspend/storage/state:cpu5_governor ]
+ cat /var/run/pm-utils/pm-suspend/storage/state:cpu5_governor
+ [ -f cpu6/cpufreq/scaling_governor ]
+ state_exists cpu6_governor
+ [ -O /var/run/pm-utils/pm-suspend/storage/state:cpu6_governor ]
+ restorestate cpu6_governor
+ state_exists cpu6_governor
+ [ -O /var/run/pm-utils/pm-suspend/storage/state:cpu6_governor ]
+ cat /var/run/pm-utils/pm-suspend/storage/state:cpu6_governor
+ [ -f cpu7/cpufreq/scaling_governor ]
+ state_exists cpu7_governor
+ [ -O /var/run/pm-utils/pm-suspend/storage/state:cpu7_governor ]
+ restorestate cpu7_governor
+ state_exists cpu7_governor
+ [ -O /var/run/pm-utils/pm-suspend/storage/state:cpu7_governor ]
+ cat /var/run/pm-utils/pm-suspend/storage/state:cpu7_governor
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: 
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=94cpufreq
+ IFS=

+ IFS= 	

+ [ reverse -a reverse = reverse -a 94cpufreq ]
+ [ 90clock > 94cpufreq ]
+ [ ! reverse ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/90clock ]
+ [ -f /usr/lib/pm-utils/sleep.d/90clock ]
+ hook=/usr/lib/pm-utils/sleep.d/90clock
+ run_hook /usr/lib/pm-utils/sleep.d/90clock resume suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/90clock resume suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/90clock
+ local hook=90clock
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:90clock ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:clock ]
+ [ -x /usr/lib/pm-utils/sleep.d/90clock ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/90clock resume suspend
+ is_set 
+ return 2
+ exit 254
+ local status=254
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/90clock resume suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/90clock resume suspend: 
/usr/lib/pm-utils/sleep.d/90clock resume suspend: + hook_exit_status 254
+ log not applicable.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ not applicable. = -n ]
+ printf %s\n not applicable.
not applicable.
+ LAST_HOOK=90clock
+ IFS=

+ IFS= 	

+ [ reverse -a reverse = reverse -a 90clock ]
+ [ 75modules > 90clock ]
+ [ ! reverse ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/75modules ]
+ [ -f /usr/lib/pm-utils/sleep.d/75modules ]
+ hook=/usr/lib/pm-utils/sleep.d/75modules
+ run_hook /usr/lib/pm-utils/sleep.d/75modules resume suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/75modules resume suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/75modules
+ local hook=75modules
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:75modules ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:modules ]
+ [ -x /usr/lib/pm-utils/sleep.d/75modules ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/75modules resume suspend
+ resume_modules
+ modreload
+ [ -O /var/run/pm-utils/pm-suspend/storage/module:* ]
+ continue
+ echo Reloaded unloaded modules.
Reloaded unloaded modules.
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/75modules resume suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/75modules resume suspend: 
/usr/lib/pm-utils/sleep.d/75modules resume suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=75modules
+ IFS=

+ IFS= 	

+ [ reverse -a reverse = reverse -a 75modules ]
+ [ 60_wpa_supplicant > 75modules ]
+ [ ! reverse ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/60_wpa_supplicant ]
+ [ -f /usr/lib/pm-utils/sleep.d/60_wpa_supplicant ]
+ hook=/usr/lib/pm-utils/sleep.d/60_wpa_supplicant
+ run_hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/60_wpa_supplicant
+ local hook=60_wpa_supplicant
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:60_wpa_supplicant ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:_wpa_supplicant ]
+ [ -x /usr/lib/pm-utils/sleep.d/60_wpa_supplicant ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: 
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=60_wpa_supplicant
+ IFS=

+ IFS= 	

+ [ reverse -a reverse = reverse -a 60_wpa_supplicant ]
+ [ 55NetworkManager > 60_wpa_supplicant ]
+ [ ! reverse ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/55NetworkManager ]
+ [ -f /usr/lib/pm-utils/sleep.d/55NetworkManager ]
+ hook=/usr/lib/pm-utils/sleep.d/55NetworkManager
+ run_hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/55NetworkManager
+ local hook=55NetworkManager
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:55NetworkManager ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:NetworkManager ]
+ [ -x /usr/lib/pm-utils/sleep.d/55NetworkManager ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend
+ resume_nm
+ printf Having NetworkManager wake interfaces back up...
Having NetworkManager wake interfaces back up...+ dbus_send --print-reply --system --dest=org.freedesktop.NetworkManager /org/freedesktop/NetworkManager org.freedesktop.NetworkManager.wake
+ command dbus-send --print-reply --system --dest=org.freedesktop.NetworkManager /org/freedesktop/NetworkManager org.freedesktop.NetworkManager.wake
+ return 254
+ echo Failed.
Failed.
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: 
/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=55NetworkManager
+ IFS=

+ IFS= 	

+ [ reverse -a reverse = reverse -a 55NetworkManager ]
+ [ 49bluetooth > 55NetworkManager ]
+ [ ! reverse ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/49bluetooth ]
+ [ -f /usr/lib/pm-utils/sleep.d/49bluetooth ]
+ hook=/usr/lib/pm-utils/sleep.d/49bluetooth
+ run_hook /usr/lib/pm-utils/sleep.d/49bluetooth resume suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/49bluetooth resume suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/49bluetooth resume suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/49bluetooth resume suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/49bluetooth resume suspend:
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth resume suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/49bluetooth
+ local hook=49bluetooth
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:49bluetooth ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:bluetooth ]
+ [ -x /usr/lib/pm-utils/sleep.d/49bluetooth ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/49bluetooth resume suspend
+ [ -f /proc/acpi/ibm/bluetooth ]
+ exit 254
+ local status=254
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/49bluetooth resume suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/49bluetooth resume suspend: 
/usr/lib/pm-utils/sleep.d/49bluetooth resume suspend: + hook_exit_status 254
+ log not applicable.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ not applicable. = -n ]
+ printf %s\n not applicable.
not applicable.
+ LAST_HOOK=49bluetooth
+ IFS=

+ IFS= 	

+ [ reverse -a reverse = reverse -a 49bluetooth ]
+ [ 10_unattended-upgrades-hibernate > 49bluetooth ]
+ [ ! reverse ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/10_unattended-upgrades-hibernate ]
+ hook=/etc/pm/sleep.d/10_unattended-upgrades-hibernate
+ run_hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend
+ _run_hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend
+ log Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: = -n ]
+ printf %s\n Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
+ hook_ok /etc/pm/sleep.d/10_unattended-upgrades-hibernate
+ local hook=10_unattended-upgrades-hibernate
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:10_unattended-upgrades-hibernate ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:_unattended-upgrades-hibernate ]
+ [ -x /etc/pm/sleep.d/10_unattended-upgrades-hibernate ]
+ return 0
+ /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: 
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=10_unattended-upgrades-hibernate
+ IFS=

+ IFS= 	

+ [ reverse -a reverse = reverse -a 10_unattended-upgrades-hibernate ]
+ [ 10_grub-common > 10_unattended-upgrades-hibernate ]
+ [ ! reverse ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/10_grub-common ]
+ hook=/etc/pm/sleep.d/10_grub-common
+ run_hook /etc/pm/sleep.d/10_grub-common resume suspend
+ _run_hook /etc/pm/sleep.d/10_grub-common resume suspend
+ log Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /etc/pm/sleep.d/10_grub-common resume suspend: = -n ]
+ printf %s\n Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
+ hook_ok /etc/pm/sleep.d/10_grub-common
+ local hook=10_grub-common
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:10_grub-common ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:_grub-common ]
+ [ -x /etc/pm/sleep.d/10_grub-common ]
+ return 0
+ /etc/pm/sleep.d/10_grub-common resume suspend
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /etc/pm/sleep.d/10_grub-common resume suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /etc/pm/sleep.d/10_grub-common resume suspend: 
/etc/pm/sleep.d/10_grub-common resume suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=10_grub-common
+ IFS=

+ IFS= 	

+ [ reverse -a reverse = reverse -a 10_grub-common ]
+ [ 01PulseAudio > 10_grub-common ]
+ [ ! reverse ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/01PulseAudio ]
+ [ -f /usr/lib/pm-utils/sleep.d/01PulseAudio ]
+ hook=/usr/lib/pm-utils/sleep.d/01PulseAudio
+ run_hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/01PulseAudio
+ local hook=01PulseAudio
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:01PulseAudio ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:PulseAudio ]
+ [ -x /usr/lib/pm-utils/sleep.d/01PulseAudio ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend
+ resume_pulse
+ get_pulse_users
+ test_pulse_system
+ getent passwd pulse
+ awk -F: {print $3}
+ PULSE_SYSTEM_USER=109
+ [ -z 109 ]
+ ps -C pulseaudio -o uid=+ 
tr -d  
+ sed s/109//
+ getent passwd 1000
+ cut -f1 -d:
+ THIS_USER=charlie
+ restore_pulse_state sink charlie
+ su charlie -c -- pacmd list-sinks
+ sed -n s/^[[:space:]*]*index: //p
+ read index
Sessions still open, not unmounting
+ state_exists pulse:charlie:sink0
+ [ -O /var/run/pm-utils/pm-suspend/storage/state:pulse:charlie:sink0 ]
+ restorestate pulse:charlie:sink0
+ state_exists pulse:charlie:sink0
+ [ -O /var/run/pm-utils/pm-suspend/storage/state:pulse:charlie:sink0 ]
+ cat /var/run/pm-utils/pm-suspend/storage/state:pulse:charlie:sink0
+ su charlie -c -- pacmd                     set-sink-mute                     0                     no
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
+ read index
+ state_exists pulse:charlie:sink1
+ [ -O /var/run/pm-utils/pm-suspend/storage/state:pulse:charlie:sink1 ]
+ restorestate pulse:charlie:sink1
+ state_exists pulse:charlie:sink1
+ [ -O /var/run/pm-utils/pm-suspend/storage/state:pulse:charlie:sink1 ]
+ cat /var/run/pm-utils/pm-suspend/storage/state:pulse:charlie:sink1
+ su charlie -c -- pacmd                     set-sink-mute                     1                     yes
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
+ read index
+ restore_pulse_state source charlie
+ su charlie -c -- pacmd list-sources
+ sed -n s/^[[:space:]*]*index: //p
+ read index
Sessions still open, not unmounting
+ state_exists pulse:charlie:source0
+ [ -O /var/run/pm-utils/pm-suspend/storage/state:pulse:charlie:source0 ]
+ restorestate pulse:charlie:source0
+ state_exists pulse:charlie:source0
+ [ -O /var/run/pm-utils/pm-suspend/storage/state:pulse:charlie:source0 ]
+ cat /var/run/pm-utils/pm-suspend/storage/state:pulse:charlie:source0
+ su charlie -c -- pacmd                     set-source-mute                     0                     yes
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
+ read index
+ state_exists pulse:charlie:source1
+ [ -O /var/run/pm-utils/pm-suspend/storage/state:pulse:charlie:source1 ]
+ restorestate pulse:charlie:source1
+ state_exists pulse:charlie:source1
+ [ -O /var/run/pm-utils/pm-suspend/storage/state:pulse:charlie:source1 ]
+ cat /var/run/pm-utils/pm-suspend/storage/state:pulse:charlie:source1
+ su charlie -c -- pacmd                     set-source-mute                     1                     yes
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
+ read index
+ state_exists pulse:charlie:source2
+ [ -O /var/run/pm-utils/pm-suspend/storage/state:pulse:charlie:source2 ]
+ restorestate pulse:charlie:source2
+ state_exists pulse:charlie:source2
+ [ -O /var/run/pm-utils/pm-suspend/storage/state:pulse:charlie:source2 ]
+ cat /var/run/pm-utils/pm-suspend/storage/state:pulse:charlie:source2
+ su charlie -c -- pacmd                     set-source-mute                     2                     yes
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
+ read index
+ su charlie -c -- pacmd suspend false
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=01PulseAudio
+ IFS=

+ IFS= 	

+ [ reverse -a reverse = reverse -a 01PulseAudio ]
+ [ 00powersave > 01PulseAudio ]
+ [ ! reverse ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/00powersave ]
+ [ -f /usr/lib/pm-utils/sleep.d/00powersave ]
+ hook=/usr/lib/pm-utils/sleep.d/00powersave
+ run_hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/00powersave
+ local hook=00powersave
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:00powersave ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:powersave ]
+ [ -x /usr/lib/pm-utils/sleep.d/00powersave ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/00powersave resume suspend
+ command_exists pm-powersave
+ type pm-powersave
+ return 0
+ pm-powersave
+ set -a
+ PM_UTILS_LIBDIR=/usr/lib/pm-utils
+ PM_UTILS_ETCDIR=/etc/pm
+ PM_UTILS_RUNDIR=/var/run/pm-utils
+ PATH=/sbin:/usr/sbin:/bin:/usr/bin:/usr/lib/pm-utils/bin
+ PM_LOGFILE=/var/log/pm-powersave.log
+ TEMPORARY_CPUFREQ_GOVERNOR=performance
+ LOCKDIR=/var/run/pm-utils/locks
+ STORAGEDIR=/var/run/pm-utils/pm-powersave/storage
+ NA=254
+ NX=253
+ DX=252
+ PM_FUNCTIONS=/usr/lib/pm-utils/functions
+ PM_QUIRKDB=/usr/lib/pm-utils/video-quirks
+ PM_LKW_QUIRKS=/var/cache/pm-utils/last_known_working.quirkdb
+ LC_COLLATE=C
+ HIBERNATE_MODE=
+ HIBERNATE_RESUME_POST_VIDEO=no
+ SLEEP_MODULE=auto
+ SUSPEND_MODULES=
+ HOOK_BLACKLIST=
+ ADD_PARAMETERS=
+ DROP_PARAMETERS=
+ PARAMETERS=/var/run/pm-utils/pm-powersave/storage/parameters
+ INHIBIT=/var/run/pm-utils/pm-powersave/storage/inhibit
+ PM_CMDLINE=
+ BEFORE_HOOKS=
+ MODULE_HELP=
+ SUSPEND_MODULE=
+ HIBERNATE_MODULE=
+ SUSPEND_HYBRID_MODULE=
+ PM_HIBERNATE_DELAY=900
+ PM_RTC=/sys/class/rtc/rtc0
+ [ -f /usr/lib/pm-utils/defaults ]
+ . /usr/lib/pm-utils/defaults
+ [ -f /usr/lib/pm-utils/pm-powersave.defaults ]
+ set +a
+ [ -f /etc/pm/config.d/*[!~] ]
+ continue
+ [ -f /etc/pm/pm-powersave.config.d/*[!~] ]
+ continue
+ . /usr/lib/pm-utils/functions
+ export PM_DEBUG=true
+ is_set true
+ return 0
+ set -x
+ profiling
+ [  = true ]
+ profiling
+ [  = true ]
+ profiling
+ [  = true ]
+ [ auto = auto ]
+ SLEEP_MODULE=tuxonice uswsusp
+ mod=/usr/lib/pm-utils/module.d/tuxonice
+ [ -f /usr/lib/pm-utils/module.d/tuxonice ]
+ . /usr/lib/pm-utils/module.d/tuxonice
+ export TUXONICE_LOC
+ [ -d /sys/power/tuxonice ]
+ [ -d /sys/power/suspend2 ]
+ [ -n  ]
+ [ -z  -a -n  ]
+ [ -z  -a -n  ]
+ mod=/usr/lib/pm-utils/module.d/uswsusp
+ [ -f /usr/lib/pm-utils/module.d/uswsusp ]
+ . /usr/lib/pm-utils/module.d/uswsusp
+ [ -z  ]
+ command_exists s2ram
+ type s2ram
+ return 127
+ [ -z  ]
+ [ -f /sys/power/disk ]
+ grep -q disk /sys/power/state
+ [ -c /dev/snapshot ]
+ command_exists s2disk
+ type s2disk
+ return 127
+ [ -z  ]
+ grep -q mem /sys/power/state
+ command_exists s2both
+ type s2both
+ return 127
+ [ -z  ]
+ grep -q mem /sys/power/state
+ SUSPEND_MODULE=kernel
+ [ -z  ]
+ [ -f /sys/power/disk ]
+ grep -q disk /sys/power/state
+ HIBERNATE_MODULE=kernel
+ [ -z  -a -w /sys/class/rtc/rtc0/wakealarm ]
+ check_suspend
+ [ -n kernel ]
+ check_hibernate
+ [ -n kernel ]
+ is_set no
+ return 1
+ SUSPEND_HYBRID_MODULE=kernel
+ lock_and_load
+ try_lock pm-powersave.lock
+ local lock=/var/run/pm-utils/locks/pm-powersave.lock
+ mkdir -p /var/run/pm-utils/locks
+ touch /var/run/pm-utils/locks/pm-powersave.lock
+ exec
+ flock -x -n 3
+ return 0
+ trap remove_powersave_lock 0
+ mkdir -p /var/run/pm-utils/pm-powersave/storage
+ rm -f /var/run/pm-utils/pm-powersave/storage/inhibit
+ load_hook_blacklist
+ [  ]
+ return
+ init_logfile /var/log/pm-powersave.log
+ [ -z /var/log/pm-powersave.log ]
+ [ -h /var/log/pm-powersave.log ]
+ [ -f /var/log/pm-powersave.log -a ! -O /var/log/pm-powersave.log ]
+ export LOGGING=true
+ exec
+ exit 0
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/00powersave resume suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/00powersave resume suspend: 
/usr/lib/pm-utils/sleep.d/00powersave resume suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=00powersave
+ IFS=

+ IFS= 	

+ [ reverse -a reverse = reverse -a 00powersave ]
+ [ 00logging > 00powersave ]
+ [ ! reverse ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/00logging ]
+ [ -f /usr/lib/pm-utils/sleep.d/00logging ]
+ hook=/usr/lib/pm-utils/sleep.d/00logging
+ run_hook /usr/lib/pm-utils/sleep.d/00logging resume suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/00logging resume suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/00logging
+ local hook=00logging
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:00logging ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:logging ]
+ [ -x /usr/lib/pm-utils/sleep.d/00logging ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/00logging resume suspend
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/00logging resume suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/00logging resume suspend: 
/usr/lib/pm-utils/sleep.d/00logging resume suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=00logging
+ IFS=

+ IFS= 	

+ [ reverse -a reverse = reverse -a 00logging ]
+ [ 000kernel-change > 00logging ]
+ [ ! reverse ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/000kernel-change ]
+ [ -f /usr/lib/pm-utils/sleep.d/000kernel-change ]
+ hook=/usr/lib/pm-utils/sleep.d/000kernel-change
+ run_hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/000kernel-change
+ local hook=000kernel-change
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:000kernel-change ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:0kernel-change ]
+ [ -x /usr/lib/pm-utils/sleep.d/000kernel-change ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: 
/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=000kernel-change
+ IFS=

+ IFS= 	

+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ return 0
+ date
+ log Mon Dec 19 11:43:58 AST 2011: Finished.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Mon Dec 19 11:43:58 AST 2011: Finished. = -n ]
+ printf %s\n Mon Dec 19 11:43:58 AST 2011: Finished.
Mon Dec 19 11:43:58 AST 2011: Finished.
+ exit 0
+ remove_suspend_lock
+ release_lock pm-suspend.lock
+ local lock=/var/run/pm-utils/locks/pm-suspend.lock
+ rm -f /var/run/pm-utils/locks/pm-suspend.lock
+ return 0
```

Now a good suspend from the hotkey:

```
+ log Initial commandline parameters: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Initial commandline parameters:  = -n ]
+ printf %s\n Initial commandline parameters: 
Initial commandline parameters: 
+ load_hook_blacklist
+ [  ]
+ return
+ load_hook_parameters
+ [  ]
+ [  ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ date
+ log Mon Dec 19 11:44:27 AST 2011: Running hooks for suspend.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Mon Dec 19 11:44:27 AST 2011: Running hooks for suspend. = -n ]
+ printf %s\n Mon Dec 19 11:44:27 AST 2011: Running hooks for suspend.
Mon Dec 19 11:44:27 AST 2011: Running hooks for suspend.
+ run_hooks sleep suspend suspend
+ _run_hooks sleep suspend suspend
+ local syshooks=/etc/pm/sleep.d
+ local phooks=/usr/lib/pm-utils/sleep.d
+ command_exists before_hooks
+ type before_hooks
+ return 0
+ before_hooks
+ [ -z  ]
+ return 0
+ local sort=sort
+ local base
+ local hook
+ local oifs= 	

+ local nifs=

+ IFS=

+ [  = reverse ]
+ IFS= 	

+ + sort
[ -O /etc/pm/sleep.d/10_grub-common ]
+ uniq+ 
echo 10_grub-common
+ [ -O /etc/pm/sleep.d/10_unattended-upgrades-hibernate ]
+ echo 10_unattended-upgrades-hibernate
+ [ -O /etc/pm/sleep.d/novatel_3g_suspend ]
+ echo novatel_3g_suspend
+ [ -O /usr/lib/pm-utils/sleep.d/000kernel-change ]
+ echo 000kernel-change
+ [ -O /usr/lib/pm-utils/sleep.d/00logging ]
+ echo 00logging
+ [ -O /usr/lib/pm-utils/sleep.d/00powersave ]
+ echo 00powersave
+ [ -O /usr/lib/pm-utils/sleep.d/01PulseAudio ]
+ echo 01PulseAudio
+ [ -O /usr/lib/pm-utils/sleep.d/49bluetooth ]
+ echo 49bluetooth
+ [ -O /usr/lib/pm-utils/sleep.d/55NetworkManager ]
+ echo 55NetworkManager
+ [ -O /usr/lib/pm-utils/sleep.d/60_wpa_supplicant ]
+ echo 60_wpa_supplicant
+ [ -O /usr/lib/pm-utils/sleep.d/75modules ]
+ echo 75modules
+ [ -O /usr/lib/pm-utils/sleep.d/90clock ]
+ echo 90clock
+ [ -O /usr/lib/pm-utils/sleep.d/94cpufreq ]
+ echo 94cpufreq
+ [ -O /usr/lib/pm-utils/sleep.d/95anacron ]
+ echo 95anacron
+ [ -O /usr/lib/pm-utils/sleep.d/95hdparm-apm ]
+ echo 95hdparm-apm
+ [ -O /usr/lib/pm-utils/sleep.d/95led ]
+ echo 95led
+ [ -O /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler ]
+ echo 98video-quirk-db-handler
+ [ -O /usr/lib/pm-utils/sleep.d/99video ]
+ echo 99video
+ IFS= 	

+ [  -a  = reverse -a  ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/000kernel-change ]
+ [ -f /usr/lib/pm-utils/sleep.d/000kernel-change ]
+ hook=/usr/lib/pm-utils/sleep.d/000kernel-change
+ run_hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/000kernel-change
+ local hook=000kernel-change
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:000kernel-change ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:0kernel-change ]
+ [ -x /usr/lib/pm-utils/sleep.d/000kernel-change ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: 
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=000kernel-change
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 000kernel-change ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/00logging ]
+ [ -f /usr/lib/pm-utils/sleep.d/00logging ]
+ hook=/usr/lib/pm-utils/sleep.d/00logging
+ run_hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/00logging
+ local hook=00logging
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:00logging ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:logging ]
+ [ -x /usr/lib/pm-utils/sleep.d/00logging ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/00logging suspend suspend
+ [ -n /var/log/pm-suspend.log ]
+ /bin/uname -a
Linux charlie-Satellite-A660 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:28:43 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
+ lsmod
Module                  Size  Used by
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
pci_stub               12622  1 
vboxpci                23200  0 
vboxnetadp             13382  0 
vboxnetflt             23441  0 
vboxdrv               282739  3 vboxpci,vboxnetadp,vboxnetflt
parport_pc             36962  0 
dm_crypt               23199  1 
ppdev                  17113  0 
mceusb                 17906  0 
binfmt_misc            17540  1 
snd_hda_codec_hdmi     32040  4 
snd_hda_codec_realtek   330769  1 
snd_hda_intel          33390  3 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96714  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
nvidia              11713772  46 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
ir_lirc_codec          12898  0 
lirc_dev               19204  1 ir_lirc_codec
joydev                 17693  0 
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
ir_sony_decoder        12549  0 
lib80211_crypt_tkip    17390  0 
mei                    41480  0 
usbhid                 47198  0 
snd                    68266  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ir_jvc_decoder         12546  0 
wl                   2568210  0 
uvcvideo               72711  0 
ir_rc6_decoder         12546  0 
videodev               92992  1 uvcvideo
soundcore              12680  1 snd
ir_rc5_decoder         12546  0 
v4l2_compat_ioctl32    17083  1 videodev
hid                    95463  1 usbhid
psmouse                73882  0 
toshiba_bluetooth      12807  0 
jmb38x_ms              17646  0 
serio_raw              13166  0 
rc_rc6_mce             12502  0 
memstick               16569  1 jmb38x_ms
sparse_keymap          13890  0 
i7core_edac            27942  0 
edac_core              53746  3 i7core_edac
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lib80211               14991  2 lib80211_crypt_tkip,wl
ir_nec_decoder         12546  0 
ene_ir                 22796  0 
rc_core                26963  10 mceusb,ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,rc_rc6_mce,ir_nec_decoder,ene_ir
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
vesafb                 13809  1 
sdhci_pci              14032  0 
r8169                  52788  0 
ahci                   26002  3 
libahci                26861  1 ahci
sdhci                  32166  1 sdhci_pci
video                  19412  0 
+ free
             total       used       free     shared    buffers     cached
Mem:       8124760    1363552    6761208          0      85552     421004
-/+ buffers/cache:     856996    7267764
Swap:      8787964          0    8787964
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/00logging suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/00logging suspend suspend: 
/usr/lib/pm-utils/sleep.d/00logging suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=00logging
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 00logging ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/00powersave ]
+ [ -f /usr/lib/pm-utils/sleep.d/00powersave ]
+ hook=/usr/lib/pm-utils/sleep.d/00powersave
+ run_hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/00powersave
+ local hook=00powersave
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:00powersave ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:powersave ]
+ [ -x /usr/lib/pm-utils/sleep.d/00powersave ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/00powersave suspend suspend
+ command_exists pm-powersave
+ type pm-powersave
+ return 0
+ pm-powersave false
+ set -a
+ PM_UTILS_LIBDIR=/usr/lib/pm-utils
+ PM_UTILS_ETCDIR=/etc/pm
+ PM_UTILS_RUNDIR=/var/run/pm-utils
+ PATH=/sbin:/usr/sbin:/bin:/usr/bin:/usr/lib/pm-utils/bin
+ PM_LOGFILE=/var/log/pm-powersave.log
+ TEMPORARY_CPUFREQ_GOVERNOR=performance
+ LOCKDIR=/var/run/pm-utils/locks
+ STORAGEDIR=/var/run/pm-utils/pm-powersave/storage
+ NA=254
+ NX=253
+ DX=252
+ PM_FUNCTIONS=/usr/lib/pm-utils/functions
+ PM_QUIRKDB=/usr/lib/pm-utils/video-quirks
+ PM_LKW_QUIRKS=/var/cache/pm-utils/last_known_working.quirkdb
+ LC_COLLATE=C
+ HIBERNATE_MODE=
+ HIBERNATE_RESUME_POST_VIDEO=no
+ SLEEP_MODULE=auto
+ SUSPEND_MODULES=
+ HOOK_BLACKLIST=
+ ADD_PARAMETERS=
+ DROP_PARAMETERS=
+ PARAMETERS=/var/run/pm-utils/pm-powersave/storage/parameters
+ INHIBIT=/var/run/pm-utils/pm-powersave/storage/inhibit
+ PM_CMDLINE=false
+ BEFORE_HOOKS=
+ MODULE_HELP=
+ SUSPEND_MODULE=
+ HIBERNATE_MODULE=
+ SUSPEND_HYBRID_MODULE=
+ PM_HIBERNATE_DELAY=900
+ PM_RTC=/sys/class/rtc/rtc0
+ [ -f /usr/lib/pm-utils/defaults ]
+ . /usr/lib/pm-utils/defaults
+ [ -f /usr/lib/pm-utils/pm-powersave.defaults ]
+ set +a
+ [ -f /etc/pm/config.d/*[!~] ]
+ continue
+ [ -f /etc/pm/pm-powersave.config.d/*[!~] ]
+ continue
+ . /usr/lib/pm-utils/functions
+ export PM_DEBUG=true
+ is_set true
+ return 0
+ set -x
+ profiling
+ [  = true ]
+ profiling
+ [  = true ]
+ profiling
+ [  = true ]
+ [ auto = auto ]
+ SLEEP_MODULE=tuxonice uswsusp
+ mod=/usr/lib/pm-utils/module.d/tuxonice
+ [ -f /usr/lib/pm-utils/module.d/tuxonice ]
+ . /usr/lib/pm-utils/module.d/tuxonice
+ export TUXONICE_LOC
+ [ -d /sys/power/tuxonice ]
+ [ -d /sys/power/suspend2 ]
+ [ -n  ]
+ [ -z  -a -n  ]
+ [ -z  -a -n  ]
+ mod=/usr/lib/pm-utils/module.d/uswsusp
+ [ -f /usr/lib/pm-utils/module.d/uswsusp ]
+ . /usr/lib/pm-utils/module.d/uswsusp
+ [ -z  ]
+ command_exists s2ram
+ type s2ram
+ return 127
+ [ -z  ]
+ [ -f /sys/power/disk ]
+ grep -q disk /sys/power/state
+ [ -c /dev/snapshot ]
+ command_exists s2disk
+ type s2disk
+ return 127
+ [ -z  ]
+ grep -q mem /sys/power/state
+ command_exists s2both
+ type s2both
+ return 127
+ [ -z  ]
+ grep -q mem /sys/power/state
+ SUSPEND_MODULE=kernel
+ [ -z  ]
+ [ -f /sys/power/disk ]
+ grep -q disk /sys/power/state
+ HIBERNATE_MODULE=kernel
+ [ -z  -a -w /sys/class/rtc/rtc0/wakealarm ]
+ check_suspend
+ [ -n kernel ]
+ check_hibernate
+ [ -n kernel ]
+ is_set no
+ return 1
+ SUSPEND_HYBRID_MODULE=kernel
+ lock_and_load
+ try_lock pm-powersave.lock
+ local lock=/var/run/pm-utils/locks/pm-powersave.lock
+ mkdir -p /var/run/pm-utils/locks
+ touch /var/run/pm-utils/locks/pm-powersave.lock
+ exec
+ flock -x -n 3
+ return 0
+ trap remove_powersave_lock 0
+ mkdir -p /var/run/pm-utils/pm-powersave/storage
+ rm -f /var/run/pm-utils/pm-powersave/storage/inhibit
+ load_hook_blacklist
+ [  ]
+ return
+ init_logfile /var/log/pm-powersave.log
+ [ -z /var/log/pm-powersave.log ]
+ [ -h /var/log/pm-powersave.log ]
+ [ -f /var/log/pm-powersave.log -a ! -O /var/log/pm-powersave.log ]
+ export LOGGING=true
+ exec
+ exit 0
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/00powersave suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/00powersave suspend suspend: 
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=00powersave
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 00powersave ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/01PulseAudio ]
+ [ -f /usr/lib/pm-utils/sleep.d/01PulseAudio ]
+ hook=/usr/lib/pm-utils/sleep.d/01PulseAudio
+ run_hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/01PulseAudio
+ local hook=01PulseAudio
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:01PulseAudio ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:PulseAudio ]
+ [ -x /usr/lib/pm-utils/sleep.d/01PulseAudio ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend
+ suspend_pulse
+ get_pulse_users
+ test_pulse_system
+ getent passwd pulse
+ awk -F: {print $3}
+ PULSE_SYSTEM_USER=109
+ [ -z 109 ]
+ ps -C pulseaudio -o uid=+ 
tr -d  
+ sed s/109//
+ getent passwd 1000
+ cut -f1 -d:
+ THIS_USER=charlie
+ save_pulse_state sink charlie
+ su charlie -c -- pacmd list-sinks
+ + index=
sed+  -nread s/^[[:space:]*]*//; /\(index\|mute\)/p field
 value
Sessions still open, not unmounting
+ [ index = index ]
+ index=0
+ read field value
+ [ muted = index ]
+ savestate pulse:charlie:sink0 no
+ [ -n no ]
+ echo no
+ read field value
+ [ index = index ]
+ index=1
+ read field value
+ [ muted = index ]
+ savestate pulse:charlie:sink1 yes
+ [ -n yes ]
+ echo yes
+ read field value
+ save_pulse_state source charlie
+ su charlie+  -c -- pacmd list-sources
sed+  -n s/^[[:space:]*]*//; /\(index\|mute\)/p
index=
+ read field value
Sessions still open, not unmounting
+ [ index = index ]
+ index=0
+ read field value
+ [ muted = index ]
+ savestate pulse:charlie:source0 yes
+ [ -n yes ]
+ echo yes
+ read field value
+ [ index = index ]
+ index=1
+ read field value
+ [ muted = index ]
+ savestate pulse:charlie:source1 yes
+ [ -n yes ]
+ echo yes
+ read field value
+ [ index = index ]
+ index=2
+ read field value
+ [ muted = index ]
+ savestate pulse:charlie:source2 yes
+ [ -n yes ]
+ echo yes
+ read field value
+ su charlie -c -- pacmd suspend true
+ get_pulse_users
+ test_pulse_system
+ getent passwd pulse
+ awk -F: {print $3}
+ PULSE_SYSTEM_USER=109
+ [ -z 109 ]
+ ps+  -C pulseaudio -o uid=
tr -d  + 
sed s/109//
+ getent passwd 1000
+ cut -f1 -d:
+ THIS_USER=charlie
+ su charlie -c -- ck-list-sessions | grep "active = TRUE"
+ mute_pulse sink charlie
+ su charlie -c -- pacmd list-sinks
+ + index=
sed+  -nread s/^[[:space:]*]*//; /\(index\|mute\)/p
 field value
Sessions still open, not unmounting
+ [ index = index ]
+ index=0
+ su charlie -c -- pacmd                         set-sink-mute 0 yes
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
+ read field value
+ [ muted = index ]
+ read field value
+ [ index = index ]
+ index=1
+ su charlie -c -- pacmd                         set-sink-mute 1 yes
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
+ read field value
+ [ muted = index ]
+ read field value
+ mute_pulse source charlie
+ su charlie -c -- pacmd list-sources
+ + sedindex=
+ read field -n value
 s/^[[:space:]*]*//; /\(index\|mute\)/p
Sessions still open, not unmounting
+ [ index = index ]
+ index=0
+ su charlie -c -- pacmd                         set-source-mute 0 yes
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
+ read field value
+ [ muted = index ]
+ read field value
+ [ index = index ]
+ index=1
+ su charlie -c -- pacmd                         set-source-mute 1 yes
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
+ read field value
+ [ muted = index ]
+ read field value
+ [ index = index ]
+ index=2
+ su charlie -c -- pacmd                         set-source-mute 2 yes
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
+ read field value
+ [ muted = index ]
+ read field value
+ break
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=01PulseAudio
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 01PulseAudio ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/10_grub-common ]
+ hook=/etc/pm/sleep.d/10_grub-common
+ run_hook /etc/pm/sleep.d/10_grub-common suspend suspend
+ _run_hook /etc/pm/sleep.d/10_grub-common suspend suspend
+ log Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /etc/pm/sleep.d/10_grub-common suspend suspend: = -n ]
+ printf %s\n Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
+ hook_ok /etc/pm/sleep.d/10_grub-common
+ local hook=10_grub-common
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:10_grub-common ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:_grub-common ]
+ [ -x /etc/pm/sleep.d/10_grub-common ]
+ return 0
+ /etc/pm/sleep.d/10_grub-common suspend suspend
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /etc/pm/sleep.d/10_grub-common suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /etc/pm/sleep.d/10_grub-common suspend suspend: 
/etc/pm/sleep.d/10_grub-common suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=10_grub-common
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 10_grub-common ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/10_unattended-upgrades-hibernate ]
+ hook=/etc/pm/sleep.d/10_unattended-upgrades-hibernate
+ run_hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend
+ _run_hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend
+ log Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: = -n ]
+ printf %s\n Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
+ hook_ok /etc/pm/sleep.d/10_unattended-upgrades-hibernate
+ local hook=10_unattended-upgrades-hibernate
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:10_unattended-upgrades-hibernate ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:_unattended-upgrades-hibernate ]
+ [ -x /etc/pm/sleep.d/10_unattended-upgrades-hibernate ]
+ return 0
+ /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: 
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=10_unattended-upgrades-hibernate
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 10_unattended-upgrades-hibernate ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/49bluetooth ]
+ [ -f /usr/lib/pm-utils/sleep.d/49bluetooth ]
+ hook=/usr/lib/pm-utils/sleep.d/49bluetooth
+ run_hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/49bluetooth
+ local hook=49bluetooth
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:49bluetooth ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:bluetooth ]
+ [ -x /usr/lib/pm-utils/sleep.d/49bluetooth ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend
+ [ -f /proc/acpi/ibm/bluetooth ]
+ exit 254
+ local status=254
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: 
/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: + hook_exit_status 254
+ log not applicable.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ not applicable. = -n ]
+ printf %s\n not applicable.
not applicable.
+ LAST_HOOK=49bluetooth
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 49bluetooth ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/55NetworkManager ]
+ [ -f /usr/lib/pm-utils/sleep.d/55NetworkManager ]
+ hook=/usr/lib/pm-utils/sleep.d/55NetworkManager
+ run_hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/55NetworkManager
+ local hook=55NetworkManager
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:55NetworkManager ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:NetworkManager ]
+ [ -x /usr/lib/pm-utils/sleep.d/55NetworkManager ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend
+ suspend_nm
+ printf Having NetworkManager put all interaces to sleep...
Having NetworkManager put all interaces to sleep...+ dbus_send --print-reply --system --dest=org.freedesktop.NetworkManager /org/freedesktop/NetworkManager org.freedesktop.NetworkManager.sleep
+ command dbus-send --print-reply --system --dest=org.freedesktop.NetworkManager /org/freedesktop/NetworkManager org.freedesktop.NetworkManager.sleep
+ return 254
+ echo Failed.
Failed.
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: 
/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=55NetworkManager
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 55NetworkManager ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/60_wpa_supplicant ]
+ [ -f /usr/lib/pm-utils/sleep.d/60_wpa_supplicant ]
+ hook=/usr/lib/pm-utils/sleep.d/60_wpa_supplicant
+ run_hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/60_wpa_supplicant
+ local hook=60_wpa_supplicant
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:60_wpa_supplicant ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:_wpa_supplicant ]
+ [ -x /usr/lib/pm-utils/sleep.d/60_wpa_supplicant ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: 
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=60_wpa_supplicant
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 60_wpa_supplicant ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/75modules ]
+ [ -f /usr/lib/pm-utils/sleep.d/75modules ]
+ hook=/usr/lib/pm-utils/sleep.d/75modules
+ run_hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/75modules
+ local hook=75modules
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:75modules ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:modules ]
+ [ -x /usr/lib/pm-utils/sleep.d/75modules ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/75modules suspend suspend
+ suspend_modules
+ [ -z  ]
+ return 254
+ local status=254
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/75modules suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/75modules suspend suspend: 
/usr/lib/pm-utils/sleep.d/75modules suspend suspend: + hook_exit_status 254
+ log not applicable.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ not applicable. = -n ]
+ printf %s\n not applicable.
not applicable.
+ LAST_HOOK=75modules
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 75modules ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/90clock ]
+ [ -f /usr/lib/pm-utils/sleep.d/90clock ]
+ hook=/usr/lib/pm-utils/sleep.d/90clock
+ run_hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/90clock
+ local hook=90clock
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:90clock ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:clock ]
+ [ -x /usr/lib/pm-utils/sleep.d/90clock ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/90clock suspend suspend
+ is_set 
+ return 2
+ exit 254
+ local status=254
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/90clock suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/90clock suspend suspend: 
/usr/lib/pm-utils/sleep.d/90clock suspend suspend: + hook_exit_status 254
+ log not applicable.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ not applicable. = -n ]
+ printf %s\n not applicable.
not applicable.
+ LAST_HOOK=90clock
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 90clock ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/94cpufreq ]
+ [ -f /usr/lib/pm-utils/sleep.d/94cpufreq ]
+ hook=/usr/lib/pm-utils/sleep.d/94cpufreq
+ run_hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/94cpufreq
+ local hook=94cpufreq
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:94cpufreq ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:cpufreq ]
+ [ -x /usr/lib/pm-utils/sleep.d/94cpufreq ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend
+ [ -d /sys/devices/system/cpu/ ]
+ hibernate_cpufreq
+ cd /sys/devices/system/cpu/
+ [ -L cpu0/cpufreq ]
+ gov=cpu0/cpufreq/scaling_governor
+ [ -f cpu0/cpufreq/scaling_governor ]
+ grep -q performance cpu0/cpufreq/scaling_available_governors
+ savestate cpu0_governor
+ [ -n  ]
+ cat
+ echo performance
+ [ -L cpu1/cpufreq ]
+ gov=cpu1/cpufreq/scaling_governor
+ [ -f cpu1/cpufreq/scaling_governor ]
+ grep -q performance cpu1/cpufreq/scaling_available_governors
+ savestate cpu1_governor
+ [ -n  ]
+ cat
+ echo performance
+ [ -L cpu2/cpufreq ]
+ gov=cpu2/cpufreq/scaling_governor
+ [ -f cpu2/cpufreq/scaling_governor ]
+ grep -q performance cpu2/cpufreq/scaling_available_governors
+ savestate cpu2_governor
+ [ -n  ]
+ cat
+ echo performance
+ [ -L cpu3/cpufreq ]
+ gov=cpu3/cpufreq/scaling_governor
+ [ -f cpu3/cpufreq/scaling_governor ]
+ grep -q performance cpu3/cpufreq/scaling_available_governors
+ savestate cpu3_governor
+ [ -n  ]
+ cat
+ echo performance
+ [ -L cpu4/cpufreq ]
+ gov=cpu4/cpufreq/scaling_governor
+ [ -f cpu4/cpufreq/scaling_governor ]
+ grep -q performance cpu4/cpufreq/scaling_available_governors
+ savestate cpu4_governor
+ [ -n  ]
+ cat
+ echo performance
+ [ -L cpu5/cpufreq ]
+ gov=cpu5/cpufreq/scaling_governor
+ [ -f cpu5/cpufreq/scaling_governor ]
+ grep -q performance cpu5/cpufreq/scaling_available_governors
+ savestate cpu5_governor
+ [ -n  ]
+ cat
+ echo performance
+ [ -L cpu6/cpufreq ]
+ gov=cpu6/cpufreq/scaling_governor
+ [ -f cpu6/cpufreq/scaling_governor ]
+ grep -q performance cpu6/cpufreq/scaling_available_governors
+ savestate cpu6_governor
+ [ -n  ]
+ cat
+ echo performance
+ [ -L cpu7/cpufreq ]
+ gov=cpu7/cpufreq/scaling_governor
+ [ -f cpu7/cpufreq/scaling_governor ]
+ grep -q performance cpu7/cpufreq/scaling_available_governors
+ savestate cpu7_governor
+ [ -n  ]
+ cat
+ echo performance
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: 
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=94cpufreq
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 94cpufreq ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/95anacron ]
+ [ -f /usr/lib/pm-utils/sleep.d/95anacron ]
+ hook=/usr/lib/pm-utils/sleep.d/95anacron
+ run_hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/95anacron
+ local hook=95anacron
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:95anacron ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:anacron ]
+ [ -x /usr/lib/pm-utils/sleep.d/95anacron ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/95anacron suspend suspend
stop: Unknown instance: 
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/95anacron suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/95anacron suspend suspend: 
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=95anacron
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 95anacron ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/95hdparm-apm ]
+ [ -f /usr/lib/pm-utils/sleep.d/95hdparm-apm ]
+ hook=/usr/lib/pm-utils/sleep.d/95hdparm-apm
+ run_hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/95hdparm-apm
+ local hook=95hdparm-apm
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:95hdparm-apm ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:hdparm-apm ]
+ [ -x /usr/lib/pm-utils/sleep.d/95hdparm-apm ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend
+ local status=254
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: 
/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: + hook_exit_status 254
+ log not applicable.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ not applicable. = -n ]
+ printf %s\n not applicable.
not applicable.
+ LAST_HOOK=95hdparm-apm
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 95hdparm-apm ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/95led ]
+ [ -f /usr/lib/pm-utils/sleep.d/95led ]
+ hook=/usr/lib/pm-utils/sleep.d/95led
+ run_hook /usr/lib/pm-utils/sleep.d/95led suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/95led suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/95led
+ local hook=95led
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:95led ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:led ]
+ [ -x /usr/lib/pm-utils/sleep.d/95led ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/95led suspend suspend
+ local status=254
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/95led suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/95led suspend suspend: 
/usr/lib/pm-utils/sleep.d/95led suspend suspend: + hook_exit_status 254
+ log not applicable.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ not applicable. = -n ]
+ printf %s\n not applicable.
not applicable.
+ LAST_HOOK=95led
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 95led ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/98video-quirk-db-handler ]
+ [ -f /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler ]
+ hook=/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler
+ run_hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler
+ local hook=98video-quirk-db-handler
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:98video-quirk-db-handler ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:video-quirk-db-handler ]
+ [ -x /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend
+ [[ -n true ]]
+ export 'PS4=${BASH_SOURCE}@${LINENO}(${FUNCNAME[0]}): '
+ PS4='${BASH_SOURCE}@${LINENO}(${FUNCNAME[0]}): '
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@10(): set -x
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@25(): possible_video_quirks=' --quirk-dpms-on
	   --quirk-dpms-suspend
	   --quirk-s3-mode
	   --quirk-s3-bios
	   --quirk-vbe-post
	   --quirk-vbe-post
	   --quirk-vga-mode-3
	   --quirk-vbemode-restore
	   --quirk-vbestate-restore
	   --quirk-reset-brightness
	   --quirk-radeon-off
	   --quirk-no-fb
	   --quirk-save-pci'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@40(): possible_system_properties='system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@343(): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@347(): precache_dmivars
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@170(precache_dmivars): local p q f
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.firmware.version
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.firmware.version* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_firmware_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_firmware_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.firmware.version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@107(dmisysget): _dmisysget bios_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@100(_dmisysget): [[ -r /sys/class/dmi/id/bios_version ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@101(_dmisysget): read RES
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=1.10
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=1.10
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_firmware_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.firmware.vendor
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.vendor =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.firmware.vendor* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_firmware_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_firmware_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.firmware.vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@106(dmisysget): _dmisysget bios_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@100(_dmisysget): [[ -r /sys/class/dmi/id/bios_vendor ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@101(_dmisysget): read RES
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=TOSHIBA
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=TOSHIBA
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_firmware_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.firmware.release_date
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.release_date =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.firmware.release_date* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_firmware_release_date
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_firmware_release_date
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.firmware.release_date
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@108(dmisysget): _dmisysget bios_date
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@100(_dmisysget): [[ -r /sys/class/dmi/id/bios_date ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@101(_dmisysget): read RES
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=04/19/10
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=04/19/10
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_firmware_release_date
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.hardware.vendor
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.hardware.vendor =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.hardware.vendor* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_hardware_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_hardware_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.hardware.vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@109(dmisysget): _dmisysget sys_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@100(_dmisysget): [[ -r /sys/class/dmi/id/sys_vendor ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@101(_dmisysget): read RES
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=TOSHIBA
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=TOSHIBA
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_hardware_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.hardware.product
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.hardware.product =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.hardware.product* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_hardware_product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_hardware_product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.hardware.product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@110(dmisysget): _dmisysget product_name
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@100(_dmisysget): [[ -r /sys/class/dmi/id/product_name ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@101(_dmisysget): read RES
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES='Satellite A660'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES='Satellite A660'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_hardware_product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.hardware.version
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.hardware.version =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.hardware.version* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_hardware_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_hardware_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.hardware.version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@111(dmisysget): _dmisysget product_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@100(_dmisysget): [[ -r /sys/class/dmi/id/product_version ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@101(_dmisysget): read RES
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=PSAW3E-01100TEN
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=PSAW3E-01100TEN
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_hardware_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.board.product
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.board.product =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.board.product* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_board_product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_board_product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.board.product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@112(dmisysget): _dmisysget board_name
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@100(_dmisysget): [[ -r /sys/class/dmi/id/board_name ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@101(_dmisysget): read RES
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=NWQAA
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=NWQAA
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_board_product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.board.version
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.board.version =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.board.version* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_board_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_board_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.board.version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@113(dmisysget): _dmisysget board_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@100(_dmisysget): [[ -r /sys/class/dmi/id/board_version ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@101(_dmisysget): read RES
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=1.00
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=1.00
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_board_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.board.vendor
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.board.vendor =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.board.vendor* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_board_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_board_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.board.vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@114(dmisysget): _dmisysget board_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@100(_dmisysget): [[ -r /sys/class/dmi/id/board_vendor ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@101(_dmisysget): read RES
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=TOSHIBA
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=TOSHIBA
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_board_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.hardware.primary_video.vendor
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.hardware.primary_video.vendor =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.hardware.primary_video.vendor* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_hardware_primary_video_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_hardware_primary_video_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.hardware.primary_video.vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@115(dmisysget): videoget vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@65(videoget): local dev pci
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@66(videoget): pci=/sys/bus/pci/devices
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:00.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:00.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:03.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:03.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:08.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:08.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:08.1/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:08.1/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:08.2/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:08.2/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:08.3/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:08.3/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:10.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:10.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:10.1/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:10.1/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:16.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:16.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x078000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1a.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1a.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x0c0320 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1b.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1b.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x040300 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.1/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.1/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.2/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.2/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.3/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.3/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.4/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.4/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1d.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1d.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x0c0320 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1e.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1e.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060401 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1f.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1f.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060100 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1f.2/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1f.2/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x010601 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1f.3/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1f.3/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x0c0500 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:01:00.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:01:00.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x030000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@70(videoget): case $1 in
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@71(videoget): cat /sys/bus/pci/devices/0000:01:00.0/vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@71(videoget): RES=0x10de
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@91(videoget): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=0x10de
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=0x10de
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_hardware_primary_video_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.hardware.primary_video.product
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.hardware.primary_video.product =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.hardware.primary_video.product* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_hardware_primary_video_product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_hardware_primary_video_product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.hardware.primary_video.product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@116(dmisysget): videoget device
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@65(videoget): local dev pci
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@66(videoget): pci=/sys/bus/pci/devices
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:00.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:00.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:03.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:03.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:08.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:08.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:08.1/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:08.1/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:08.2/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:08.2/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:08.3/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:08.3/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:10.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:10.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:10.1/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:10.1/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:16.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:16.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x078000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1a.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1a.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x0c0320 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1b.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1b.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x040300 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.1/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.1/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.2/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.2/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.3/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.3/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.4/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.4/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1d.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1d.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x0c0320 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1e.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1e.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060401 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1f.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1f.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060100 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1f.2/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1f.2/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x010601 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1f.3/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1f.3/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x0c0500 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:01:00.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:01:00.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x030000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@70(videoget): case $1 in
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@72(videoget): cat /sys/bus/pci/devices/0000:01:00.0/device
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@72(videoget): RES=0x0a29
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@91(videoget): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=0x0a29
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=0x0a29
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_hardware_primary_video_product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.hardware.primary_video.driver
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.hardware.primary_video.driver =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.hardware.primary_video.driver* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_hardware_primary_video_driver
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_hardware_primary_video_driver
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.hardware.primary_video.driver
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@117(dmisysget): videoget driver
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@65(videoget): local dev pci
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@66(videoget): pci=/sys/bus/pci/devices
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:00.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:00.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:03.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:03.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:08.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:08.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:08.1/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:08.1/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:08.2/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:08.2/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:08.3/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:08.3/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:10.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:10.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:10.1/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:10.1/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:16.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:16.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x078000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1a.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1a.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x0c0320 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1b.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1b.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x040300 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.1/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.1/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.2/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.2/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.3/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.3/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.4/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.4/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1d.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1d.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x0c0320 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1e.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1e.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060401 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1f.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1f.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060100 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1f.2/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1f.2/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x010601 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1f.3/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1f.3/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x0c0500 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:01:00.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:01:00.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x030000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@70(videoget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@74(videoget): [[ -L /sys/bus/pci/devices/0000:01:00.0/driver ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@75(videoget): readlink /sys/bus/pci/devices/0000:01:00.0/driver
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@75(videoget): RES=../../../../bus/pci/drivers/nvidia
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@76(videoget): RES=nvidia
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@91(videoget): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=nvidia
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=nvidia
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_hardware_primary_video_driver
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.hardware.primary_video.using_kms
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.hardware.primary_video.using_kms =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.hardware.primary_video.using_kms* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_hardware_primary_video_using_kms
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_hardware_primary_video_using_kms
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.hardware.primary_video.using_kms
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@118(dmisysget): videoget using_kms
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@65(videoget): local dev pci
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@66(videoget): pci=/sys/bus/pci/devices
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:00.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:00.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:03.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:03.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:08.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:08.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:08.1/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:08.1/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:08.2/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:08.2/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:08.3/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:08.3/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:10.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:10.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:10.1/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:10.1/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:16.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:16.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x078000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1a.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1a.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x0c0320 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1b.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1b.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x040300 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.1/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.1/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.2/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.2/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.3/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.3/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.4/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.4/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1d.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1d.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x0c0320 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1e.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1e.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060401 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1f.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1f.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060100 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1f.2/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1f.2/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x010601 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1f.3/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1f.3/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x0c0500 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:01:00.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:01:00.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x030000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@70(videoget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@84(videoget): using_kms
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@60(using_kms): grep -q -E '(nouveau|drm)fb' /proc/fb
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@87(videoget): RES=false
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@91(videoget): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=false
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=false
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_hardware_primary_video_using_kms
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.kernel.version
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.kernel.version =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.kernel.version* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_kernel_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_kernel_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.kernel.version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@119(dmisysget): uname -r
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@119(dmisysget): RES=3.0.0-14-generic
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=3.0.0-14-generic
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=3.0.0-14-generic
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_kernel_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@181(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@352(): has_parameter --quirk-test
//usr/lib/pm-utils/functions@240(has_parameter): get_parameters
//usr/lib/pm-utils/functions@235(get_parameters): cat /var/run/pm-utils/pm-suspend/storage/parameters
/usr/lib/pm-utils/functions@244(has_parameter): return 1
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@358(): using_kms
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@60(using_kms): grep -q -E '(nouveau|drm)fb' /proc/fb
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@363(): using_nvidia
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@54(using_nvidia): [[ -d /sys/module/nvidia ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@365(): remove_parameters --quirk-dpms-on --quirk-dpms-suspend --quirk-s3-mode --quirk-s3-bios --quirk-vbe-post --quirk-vbe-post --quirk-vga-mode-3 --quirk-vbemode-restore --quirk-vbestate-restore --quirk-reset-brightness --quirk-radeon-off --quirk-no-fb --quirk-save-pci
/usr/lib/pm-utils/functions@211(remove_parameters): local p
/usr/lib/pm-utils/functions@212(remove_parameters): '[' --quirk-dpms-on = all ']'
/usr/lib/pm-utils/functions@215(remove_parameters): echo ''
/usr/lib/pm-utils/functions@216(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@217(remove_parameters): echo --quirk-dpms-on
/usr/lib/pm-utils/functions@216(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@217(remove_parameters): echo --quirk-dpms-suspend
/usr/lib/pm-utils/functions@216(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@217(remove_parameters): echo --quirk-s3-mode
/usr/lib/pm-utils/functions@216(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@217(remove_parameters): echo --quirk-s3-bios
/usr/lib/pm-utils/functions@216(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@217(remove_parameters): echo --quirk-vbe-post
/usr/lib/pm-utils/functions@216(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@217(remove_parameters): echo --quirk-vbe-post
/usr/lib/pm-utils/functions@216(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@217(remove_parameters): echo --quirk-vga-mode-3
/usr/lib/pm-utils/functions@216(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@217(remove_parameters): echo --quirk-vbemode-restore
/usr/lib/pm-utils/functions@216(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@217(remove_parameters): echo --quirk-vbestate-restore
/usr/lib/pm-utils/functions@216(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@217(remove_parameters): echo --quirk-reset-brightness
/usr/lib/pm-utils/functions@216(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@217(remove_parameters): echo --quirk-radeon-off
/usr/lib/pm-utils/functions@216(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@217(remove_parameters): echo --quirk-no-fb
/usr/lib/pm-utils/functions@216(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@217(remove_parameters): echo --quirk-save-pci
/usr/lib/pm-utils/functions@220(remove_parameters): grep -vxFf /var/run/pm-utils/pm-suspend/storage/parameters.rm /var/run/pm-utils/pm-suspend/storage/parameters
/usr/lib/pm-utils/functions@222(remove_parameters): cp -f /var/run/pm-utils/pm-suspend/storage/parameters.new /var/run/pm-utils/pm-suspend/storage/parameters
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@366(): echo 'nVidia binary video drive detected, not using quirks.'
nVidia binary video drive detected, not using quirks.
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: 
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=98video-quirk-db-handler
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 98video-quirk-db-handler ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ get_parameters
+ cat /var/run/pm-utils/pm-suspend/storage/parameters
+ export PM_CMDLINE=
+ rm -f /var/run/pm-utils/pm-suspend/storage/parameters.new
+ [ -f /etc/pm/sleep.d/99video ]
+ [ -f /usr/lib/pm-utils/sleep.d/99video ]
+ hook=/usr/lib/pm-utils/sleep.d/99video
+ run_hook /usr/lib/pm-utils/sleep.d/99video suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/99video suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/99video
+ local hook=99video
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:99video ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:video ]
+ [ -x /usr/lib/pm-utils/sleep.d/99video ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/99video suspend suspend
+ command_exists vbetool
+ type vbetool
+ return 0
+ command_exists radeontool
+ type radeontool
+ return 0
+ maybe_chvt
+ is_set 
+ return 2
+ fgconsole
+ savestate console
+ [ -n  ]
+ cat
+ chvt 63
+ suspend_video
+ local acpi_flag=0
+ quirk 
+ is_set 
+ return 2
+ quirk 
+ is_set 
+ return 2
+ sysctl -w kernel.acpi_video_flags=0
kernel.acpi_video_flags = 0
+ quirk 
+ is_set 
+ return 2
+ quirk 
+ is_set 
+ return 2
+ quirk 
+ is_set 
+ return 2
+ quirk 
+ is_set 
+ return 2
+ quirk 
+ is_set 
+ return 2
+ quirk 
+ is_set 
+ return 2
+ quirk 
+ is_set 
+ return 2
+ save_fbcon
+ local con
+ [ -f /sys/class/graphics/fb0/state ]
+ echo 1
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/99video suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/99video suspend suspend: 
/usr/lib/pm-utils/sleep.d/99video suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=99video
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 99video ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/novatel_3g_suspend ]
+ hook=/etc/pm/sleep.d/novatel_3g_suspend
+ run_hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend
+ _run_hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend
+ log Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend: = -n ]
+ printf %s\n Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
+ hook_ok /etc/pm/sleep.d/novatel_3g_suspend
+ local hook=novatel_3g_suspend
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:novatel_3g_suspend ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:novatel_3g_suspend ]
+ [ -x /etc/pm/sleep.d/novatel_3g_suspend ]
+ return 0
+ /etc/pm/sleep.d/novatel_3g_suspend suspend suspend
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /etc/pm/sleep.d/novatel_3g_suspend suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /etc/pm/sleep.d/novatel_3g_suspend suspend suspend: 
/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=novatel_3g_suspend
+ IFS=

+ IFS= 	

+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ return 0
+ date
+ log Mon Dec 19 11:44:32 AST 2011: performing suspend
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Mon Dec 19 11:44:32 AST 2011: performing suspend = -n ]
+ printf %s\n Mon Dec 19 11:44:32 AST 2011: performing suspend
Mon Dec 19 11:44:32 AST 2011: performing suspend
+ sync
+ do_suspend
+ echo -n mem
+ date
+ log Mon Dec 19 11:44:43 AST 2011: Awake.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Mon Dec 19 11:44:43 AST 2011: Awake. = -n ]
+ printf %s\n Mon Dec 19 11:44:43 AST 2011: Awake.
Mon Dec 19 11:44:43 AST 2011: Awake.
+ date
+ log Mon Dec 19 11:44:43 AST 2011: Running hooks for resume
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Mon Dec 19 11:44:43 AST 2011: Running hooks for resume = -n ]
+ printf %s\n Mon Dec 19 11:44:43 AST 2011: Running hooks for resume
Mon Dec 19 11:44:43 AST 2011: Running hooks for resume
+ run_hooks sleep resume suspend reverse
+ _run_hooks sleep resume suspend reverse
+ local syshooks=/etc/pm/sleep.d
+ local phooks=/usr/lib/pm-utils/sleep.d
+ command_exists before_hooks
+ type before_hooks
+ return 0
+ before_hooks
+ [ -z  ]
+ return 0
+ local sort=sort
+ local base
+ local hook
+ local oifs= 	

+ local nifs=

+ IFS=

+ [ reverse = reverse ]
+ sort=sort -r
+ IFS= 	

+ sort -r+ 
[ -O /etc/pm/sleep.d/10_grub-common ]
+ + echouniq 10_grub-common

+ [ -O /etc/pm/sleep.d/10_unattended-upgrades-hibernate ]
+ echo 10_unattended-upgrades-hibernate
+ [ -O /etc/pm/sleep.d/novatel_3g_suspend ]
+ echo novatel_3g_suspend
+ [ -O /usr/lib/pm-utils/sleep.d/000kernel-change ]
+ echo 000kernel-change
+ [ -O /usr/lib/pm-utils/sleep.d/00logging ]
+ echo 00logging
+ [ -O /usr/lib/pm-utils/sleep.d/00powersave ]
+ echo 00powersave
+ [ -O /usr/lib/pm-utils/sleep.d/01PulseAudio ]
+ echo 01PulseAudio
+ [ -O /usr/lib/pm-utils/sleep.d/49bluetooth ]
+ echo 49bluetooth
+ [ -O /usr/lib/pm-utils/sleep.d/55NetworkManager ]
+ echo 55NetworkManager
+ [ -O /usr/lib/pm-utils/sleep.d/60_wpa_supplicant ]
+ echo 60_wpa_supplicant
+ [ -O /usr/lib/pm-utils/sleep.d/75modules ]
+ echo 75modules
+ [ -O /usr/lib/pm-utils/sleep.d/90clock ]
+ echo 90clock
+ [ -O /usr/lib/pm-utils/sleep.d/94cpufreq ]
+ echo 94cpufreq
+ [ -O /usr/lib/pm-utils/sleep.d/95anacron ]
+ echo 95anacron
+ [ -O /usr/lib/pm-utils/sleep.d/95hdparm-apm ]
+ echo 95hdparm-apm
+ [ -O /usr/lib/pm-utils/sleep.d/95led ]
+ echo 95led
+ [ -O /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler ]
+ echo 98video-quirk-db-handler
+ [ -O /usr/lib/pm-utils/sleep.d/99video ]
+ echo 99video
+ IFS= 	

+ [ reverse -a reverse = reverse -a novatel_3g_suspend ]
+ [ novatel_3g_suspend > novatel_3g_suspend ]
+ [ ! reverse ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/novatel_3g_suspend ]
+ hook=/etc/pm/sleep.d/novatel_3g_suspend
+ run_hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend
+ _run_hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend
+ log Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend: = -n ]
+ printf %s\n Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:
+ hook_ok /etc/pm/sleep.d/novatel_3g_suspend
+ local hook=novatel_3g_suspend
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:novatel_3g_suspend ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:novatel_3g_suspend ]
+ [ -x /etc/pm/sleep.d/novatel_3g_suspend ]
+ return 0
+ /etc/pm/sleep.d/novatel_3g_suspend resume suspend
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /etc/pm/sleep.d/novatel_3g_suspend resume suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /etc/pm/sleep.d/novatel_3g_suspend resume suspend: 
/etc/pm/sleep.d/novatel_3g_suspend resume suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=novatel_3g_suspend
+ IFS=

+ IFS= 	

+ [ reverse -a reverse = reverse -a novatel_3g_suspend ]
+ [ 99video > novatel_3g_suspend ]
+ [ ! reverse ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/99video ]
+ [ -f /usr/lib/pm-utils/sleep.d/99video ]
+ hook=/usr/lib/pm-utils/sleep.d/99video
+ run_hook /usr/lib/pm-utils/sleep.d/99video resume suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/99video resume suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/99video
+ local hook=99video
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:99video ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:video ]
+ [ -x /usr/lib/pm-utils/sleep.d/99video ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/99video resume suspend
+ command_exists vbetool
+ type vbetool
+ return 0
+ command_exists radeontool
+ type radeontool
+ return 0
+ resume_video
+ quirk 
+ is_set 
+ return 2
+ quirk 
+ is_set 
+ return 2
+ quirk 
+ is_set 
+ return 2
+ quirk 
+ is_set 
+ return 2
+ resume_fbcon
+ local con
+ [ -f /sys/class/graphics/fb0/state ]
+ echo 0
+ quirk 
+ is_set 
+ return 2
+ quirk 
+ is_set 
+ return 2
+ quirk 
+ is_set 
+ return 2
+ return 0
+ maybe_deallocvt
+ state_exists console
+ [ -O /var/run/pm-utils/pm-suspend/storage/state:console ]
+ restorestate console
+ state_exists console
+ [ -O /var/run/pm-utils/pm-suspend/storage/state:console ]
+ cat /var/run/pm-utils/pm-suspend/storage/state:console
+ chvt 7
+ deallocvt 63
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/99video resume suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/99video resume suspend: 
/usr/lib/pm-utils/sleep.d/99video resume suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=99video
+ IFS=

+ IFS= 	

+ [ reverse -a reverse = reverse -a 99video ]
+ [ 98video-quirk-db-handler > 99video ]
+ [ ! reverse ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/98video-quirk-db-handler ]
+ [ -f /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler ]
+ hook=/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler
+ run_hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler
+ local hook=98video-quirk-db-handler
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:98video-quirk-db-handler ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:video-quirk-db-handler ]
+ [ -x /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend
+ [[ -n true ]]
+ export 'PS4=${BASH_SOURCE}@${LINENO}(${FUNCNAME[0]}): '
+ PS4='${BASH_SOURCE}@${LINENO}(${FUNCNAME[0]}): '
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@10(): set -x
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@25(): possible_video_quirks=' --quirk-dpms-on
	   --quirk-dpms-suspend
	   --quirk-s3-mode
	   --quirk-s3-bios
	   --quirk-vbe-post
	   --quirk-vbe-post
	   --quirk-vga-mode-3
	   --quirk-vbemode-restore
	   --quirk-vbestate-restore
	   --quirk-reset-brightness
	   --quirk-radeon-off
	   --quirk-no-fb
	   --quirk-save-pci'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@40(): possible_system_properties='system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@343(): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@436(): state_exists video_quirks
/usr/lib/pm-utils/functions@185(state_exists): '[' -O /var/run/pm-utils/pm-suspend/storage/state:video_quirks ']'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@440(): has_parameter --store-quirks-as-lkw
//usr/lib/pm-utils/functions@240(has_parameter): get_parameters
//usr/lib/pm-utils/functions@235(get_parameters): cat /var/run/pm-utils/pm-suspend/storage/parameters
/usr/lib/pm-utils/functions@244(has_parameter): return 1
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: 
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=98video-quirk-db-handler
+ IFS=

+ IFS= 	

+ [ reverse -a reverse = reverse -a 98video-quirk-db-handler ]
+ [ 95led > 98video-quirk-db-handler ]
+ [ ! reverse ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/95led ]
+ [ -f /usr/lib/pm-utils/sleep.d/95led ]
+ hook=/usr/lib/pm-utils/sleep.d/95led
+ run_hook /usr/lib/pm-utils/sleep.d/95led resume suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/95led resume suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/95led
+ local hook=95led
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:95led ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:led ]
+ [ -x /usr/lib/pm-utils/sleep.d/95led ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/95led resume suspend
+ local status=254
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/95led resume suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/95led resume suspend: 
/usr/lib/pm-utils/sleep.d/95led resume suspend: + hook_exit_status 254
+ log not applicable.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ not applicable. = -n ]
+ printf %s\n not applicable.
not applicable.
+ LAST_HOOK=95led
+ IFS=

+ IFS= 	

+ [ reverse -a reverse = reverse -a 95led ]
+ [ 95hdparm-apm > 95led ]
+ [ ! reverse ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/95hdparm-apm ]
+ [ -f /usr/lib/pm-utils/sleep.d/95hdparm-apm ]
+ hook=/usr/lib/pm-utils/sleep.d/95hdparm-apm
+ run_hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/95hdparm-apm
+ local hook=95hdparm-apm
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:95hdparm-apm ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:hdparm-apm ]
+ [ -x /usr/lib/pm-utils/sleep.d/95hdparm-apm ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: 
/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=95hdparm-apm
+ IFS=

+ IFS= 	

+ [ reverse -a reverse = reverse -a 95hdparm-apm ]
+ [ 95anacron > 95hdparm-apm ]
+ [ ! reverse ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/95anacron ]
+ [ -f /usr/lib/pm-utils/sleep.d/95anacron ]
+ hook=/usr/lib/pm-utils/sleep.d/95anacron
+ run_hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/95anacron
+ local hook=95anacron
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:95anacron ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:anacron ]
+ [ -x /usr/lib/pm-utils/sleep.d/95anacron ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/95anacron resume suspend
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/95anacron resume suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/95anacron resume suspend: 
/usr/lib/pm-utils/sleep.d/95anacron resume suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=95anacron
+ IFS=

+ IFS= 	

+ [ reverse -a reverse = reverse -a 95anacron ]
+ [ 94cpufreq > 95anacron ]
+ [ ! reverse ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/94cpufreq ]
+ [ -f /usr/lib/pm-utils/sleep.d/94cpufreq ]
+ hook=/usr/lib/pm-utils/sleep.d/94cpufreq
+ run_hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/94cpufreq
+ local hook=94cpufreq
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:94cpufreq ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:cpufreq ]
+ [ -x /usr/lib/pm-utils/sleep.d/94cpufreq ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend
+ [ -d /sys/devices/system/cpu/ ]
+ thaw_cpufreq
+ cd /sys/devices/system/cpu/
+ [ -f cpu0/cpufreq/scaling_governor ]
+ state_exists cpu0_governor
+ [ -O /var/run/pm-utils/pm-suspend/storage/state:cpu0_governor ]
+ restorestate cpu0_governor
+ state_exists cpu0_governor
+ [ -O /var/run/pm-utils/pm-suspend/storage/state:cpu0_governor ]
+ cat /var/run/pm-utils/pm-suspend/storage/state:cpu0_governor
+ [ -f cpu1/cpufreq/scaling_governor ]
+ state_exists cpu1_governor
+ [ -O /var/run/pm-utils/pm-suspend/storage/state:cpu1_governor ]
+ restorestate cpu1_governor
+ state_exists cpu1_governor
+ [ -O /var/run/pm-utils/pm-suspend/storage/state:cpu1_governor ]
+ cat /var/run/pm-utils/pm-suspend/storage/state:cpu1_governor
+ [ -f cpu2/cpufreq/scaling_governor ]
+ state_exists cpu2_governor
+ [ -O /var/run/pm-utils/pm-suspend/storage/state:cpu2_governor ]
+ restorestate cpu2_governor
+ state_exists cpu2_governor
+ [ -O /var/run/pm-utils/pm-suspend/storage/state:cpu2_governor ]
+ cat /var/run/pm-utils/pm-suspend/storage/state:cpu2_governor
+ [ -f cpu3/cpufreq/scaling_governor ]
+ state_exists cpu3_governor
+ [ -O /var/run/pm-utils/pm-suspend/storage/state:cpu3_governor ]
+ restorestate cpu3_governor
+ state_exists cpu3_governor
+ [ -O /var/run/pm-utils/pm-suspend/storage/state:cpu3_governor ]
+ cat /var/run/pm-utils/pm-suspend/storage/state:cpu3_governor
+ [ -f cpu4/cpufreq/scaling_governor ]
+ state_exists cpu4_governor
+ [ -O /var/run/pm-utils/pm-suspend/storage/state:cpu4_governor ]
+ restorestate cpu4_governor
+ state_exists cpu4_governor
+ [ -O /var/run/pm-utils/pm-suspend/storage/state:cpu4_governor ]
+ cat /var/run/pm-utils/pm-suspend/storage/state:cpu4_governor
+ [ -f cpu5/cpufreq/scaling_governor ]
+ state_exists cpu5_governor
+ [ -O /var/run/pm-utils/pm-suspend/storage/state:cpu5_governor ]
+ restorestate cpu5_governor
+ state_exists cpu5_governor
+ [ -O /var/run/pm-utils/pm-suspend/storage/state:cpu5_governor ]
+ cat /var/run/pm-utils/pm-suspend/storage/state:cpu5_governor
+ [ -f cpu6/cpufreq/scaling_governor ]
+ state_exists cpu6_governor
+ [ -O /var/run/pm-utils/pm-suspend/storage/state:cpu6_governor ]
+ restorestate cpu6_governor
+ state_exists cpu6_governor
+ [ -O /var/run/pm-utils/pm-suspend/storage/state:cpu6_governor ]
+ cat /var/run/pm-utils/pm-suspend/storage/state:cpu6_governor
+ [ -f cpu7/cpufreq/scaling_governor ]
+ state_exists cpu7_governor
+ [ -O /var/run/pm-utils/pm-suspend/storage/state:cpu7_governor ]
+ restorestate cpu7_governor
+ state_exists cpu7_governor
+ [ -O /var/run/pm-utils/pm-suspend/storage/state:cpu7_governor ]
+ cat /var/run/pm-utils/pm-suspend/storage/state:cpu7_governor
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: 
/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=94cpufreq
+ IFS=

+ IFS= 	

+ [ reverse -a reverse = reverse -a 94cpufreq ]
+ [ 90clock > 94cpufreq ]
+ [ ! reverse ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/90clock ]
+ [ -f /usr/lib/pm-utils/sleep.d/90clock ]
+ hook=/usr/lib/pm-utils/sleep.d/90clock
+ run_hook /usr/lib/pm-utils/sleep.d/90clock resume suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/90clock resume suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/90clock
+ local hook=90clock
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:90clock ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:clock ]
+ [ -x /usr/lib/pm-utils/sleep.d/90clock ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/90clock resume suspend
+ is_set 
+ return 2
+ exit 254
+ local status=254
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/90clock resume suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/90clock resume suspend: 
/usr/lib/pm-utils/sleep.d/90clock resume suspend: + hook_exit_status 254
+ log not applicable.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ not applicable. = -n ]
+ printf %s\n not applicable.
not applicable.
+ LAST_HOOK=90clock
+ IFS=

+ IFS= 	

+ [ reverse -a reverse = reverse -a 90clock ]
+ [ 75modules > 90clock ]
+ [ ! reverse ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/75modules ]
+ [ -f /usr/lib/pm-utils/sleep.d/75modules ]
+ hook=/usr/lib/pm-utils/sleep.d/75modules
+ run_hook /usr/lib/pm-utils/sleep.d/75modules resume suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/75modules resume suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/75modules
+ local hook=75modules
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:75modules ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:modules ]
+ [ -x /usr/lib/pm-utils/sleep.d/75modules ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/75modules resume suspend
+ resume_modules
+ modreload
+ [ -O /var/run/pm-utils/pm-suspend/storage/module:* ]
+ continue
+ echo Reloaded unloaded modules.
Reloaded unloaded modules.
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/75modules resume suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/75modules resume suspend: 
/usr/lib/pm-utils/sleep.d/75modules resume suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=75modules
+ IFS=

+ IFS= 	

+ [ reverse -a reverse = reverse -a 75modules ]
+ [ 60_wpa_supplicant > 75modules ]
+ [ ! reverse ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/60_wpa_supplicant ]
+ [ -f /usr/lib/pm-utils/sleep.d/60_wpa_supplicant ]
+ hook=/usr/lib/pm-utils/sleep.d/60_wpa_supplicant
+ run_hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/60_wpa_supplicant
+ local hook=60_wpa_supplicant
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:60_wpa_supplicant ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:_wpa_supplicant ]
+ [ -x /usr/lib/pm-utils/sleep.d/60_wpa_supplicant ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: 
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=60_wpa_supplicant
+ IFS=

+ IFS= 	

+ [ reverse -a reverse = reverse -a 60_wpa_supplicant ]
+ [ 55NetworkManager > 60_wpa_supplicant ]
+ [ ! reverse ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/55NetworkManager ]
+ [ -f /usr/lib/pm-utils/sleep.d/55NetworkManager ]
+ hook=/usr/lib/pm-utils/sleep.d/55NetworkManager
+ run_hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/55NetworkManager
+ local hook=55NetworkManager
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:55NetworkManager ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:NetworkManager ]
+ [ -x /usr/lib/pm-utils/sleep.d/55NetworkManager ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend
+ resume_nm
+ printf Having NetworkManager wake interfaces back up...
Having NetworkManager wake interfaces back up...+ dbus_send --print-reply --system --dest=org.freedesktop.NetworkManager /org/freedesktop/NetworkManager org.freedesktop.NetworkManager.wake
+ command dbus-send --print-reply --system --dest=org.freedesktop.NetworkManager /org/freedesktop/NetworkManager org.freedesktop.NetworkManager.wake
+ return 254
+ echo Failed.
Failed.
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: 
/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=55NetworkManager
+ IFS=

+ IFS= 	

+ [ reverse -a reverse = reverse -a 55NetworkManager ]
+ [ 49bluetooth > 55NetworkManager ]
+ [ ! reverse ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/49bluetooth ]
+ [ -f /usr/lib/pm-utils/sleep.d/49bluetooth ]
+ hook=/usr/lib/pm-utils/sleep.d/49bluetooth
+ run_hook /usr/lib/pm-utils/sleep.d/49bluetooth resume suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/49bluetooth resume suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/49bluetooth resume suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/49bluetooth resume suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/49bluetooth resume suspend:
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth resume suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/49bluetooth
+ local hook=49bluetooth
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:49bluetooth ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:bluetooth ]
+ [ -x /usr/lib/pm-utils/sleep.d/49bluetooth ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/49bluetooth resume suspend
+ [ -f /proc/acpi/ibm/bluetooth ]
+ exit 254
+ local status=254
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/49bluetooth resume suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/49bluetooth resume suspend: 
/usr/lib/pm-utils/sleep.d/49bluetooth resume suspend: + hook_exit_status 254
+ log not applicable.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ not applicable. = -n ]
+ printf %s\n not applicable.
not applicable.
+ LAST_HOOK=49bluetooth
+ IFS=

+ IFS= 	

+ [ reverse -a reverse = reverse -a 49bluetooth ]
+ [ 10_unattended-upgrades-hibernate > 49bluetooth ]
+ [ ! reverse ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/10_unattended-upgrades-hibernate ]
+ hook=/etc/pm/sleep.d/10_unattended-upgrades-hibernate
+ run_hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend
+ _run_hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend
+ log Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: = -n ]
+ printf %s\n Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:
+ hook_ok /etc/pm/sleep.d/10_unattended-upgrades-hibernate
+ local hook=10_unattended-upgrades-hibernate
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:10_unattended-upgrades-hibernate ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:_unattended-upgrades-hibernate ]
+ [ -x /etc/pm/sleep.d/10_unattended-upgrades-hibernate ]
+ return 0
+ /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: 
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=10_unattended-upgrades-hibernate
+ IFS=

+ IFS= 	

+ [ reverse -a reverse = reverse -a 10_unattended-upgrades-hibernate ]
+ [ 10_grub-common > 10_unattended-upgrades-hibernate ]
+ [ ! reverse ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/10_grub-common ]
+ hook=/etc/pm/sleep.d/10_grub-common
+ run_hook /etc/pm/sleep.d/10_grub-common resume suspend
+ _run_hook /etc/pm/sleep.d/10_grub-common resume suspend
+ log Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /etc/pm/sleep.d/10_grub-common resume suspend: = -n ]
+ printf %s\n Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:
+ hook_ok /etc/pm/sleep.d/10_grub-common
+ local hook=10_grub-common
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:10_grub-common ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:_grub-common ]
+ [ -x /etc/pm/sleep.d/10_grub-common ]
+ return 0
+ /etc/pm/sleep.d/10_grub-common resume suspend
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /etc/pm/sleep.d/10_grub-common resume suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /etc/pm/sleep.d/10_grub-common resume suspend: 
/etc/pm/sleep.d/10_grub-common resume suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=10_grub-common
+ IFS=

+ IFS= 	

+ [ reverse -a reverse = reverse -a 10_grub-common ]
+ [ 01PulseAudio > 10_grub-common ]
+ [ ! reverse ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/01PulseAudio ]
+ [ -f /usr/lib/pm-utils/sleep.d/01PulseAudio ]
+ hook=/usr/lib/pm-utils/sleep.d/01PulseAudio
+ run_hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/01PulseAudio
+ local hook=01PulseAudio
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:01PulseAudio ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:PulseAudio ]
+ [ -x /usr/lib/pm-utils/sleep.d/01PulseAudio ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend
+ resume_pulse
+ get_pulse_users
+ test_pulse_system
+ + awkgetent -F: passwd {print $3} pulse

+ PULSE_SYSTEM_USER=109
+ [ -z 109 ]
+ ps+  -C pulseaudio -o uid=tr
 -d  
+ sed s/109//
+ getent passwd+  1000
cut -f1 -d:
+ THIS_USER=charlie
+ restore_pulse_state sink charlie
+ su charlie -c -- pacmd list-sinks
+ sed -n s/^[[:space:]*]*index: //p
+ read index
Sessions still open, not unmounting
+ state_exists pulse:charlie:sink0
+ [ -O /var/run/pm-utils/pm-suspend/storage/state:pulse:charlie:sink0 ]
+ restorestate pulse:charlie:sink0
+ state_exists pulse:charlie:sink0
+ [ -O /var/run/pm-utils/pm-suspend/storage/state:pulse:charlie:sink0 ]
+ cat /var/run/pm-utils/pm-suspend/storage/state:pulse:charlie:sink0
+ su charlie -c -- pacmd                     set-sink-mute                     0                     no
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
+ read index
+ state_exists pulse:charlie:sink1
+ [ -O /var/run/pm-utils/pm-suspend/storage/state:pulse:charlie:sink1 ]
+ restorestate pulse:charlie:sink1
+ state_exists pulse:charlie:sink1
+ [ -O /var/run/pm-utils/pm-suspend/storage/state:pulse:charlie:sink1 ]
+ cat /var/run/pm-utils/pm-suspend/storage/state:pulse:charlie:sink1
+ su charlie -c -- pacmd                     set-sink-mute                     1                     yes
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
+ read index
+ restore_pulse_state source charlie
+ su charlie -c -- pacmd list-sources
+ read index
+ sed -n s/^[[:space:]*]*index: //p
Sessions still open, not unmounting
+ state_exists pulse:charlie:source0
+ [ -O /var/run/pm-utils/pm-suspend/storage/state:pulse:charlie:source0 ]
+ restorestate pulse:charlie:source0
+ state_exists pulse:charlie:source0
+ [ -O /var/run/pm-utils/pm-suspend/storage/state:pulse:charlie:source0 ]
+ cat /var/run/pm-utils/pm-suspend/storage/state:pulse:charlie:source0
+ su charlie -c -- pacmd                     set-source-mute                     0                     yes
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
+ read index
+ state_exists pulse:charlie:source1
+ [ -O /var/run/pm-utils/pm-suspend/storage/state:pulse:charlie:source1 ]
+ restorestate pulse:charlie:source1
+ state_exists pulse:charlie:source1
+ [ -O /var/run/pm-utils/pm-suspend/storage/state:pulse:charlie:source1 ]
+ cat /var/run/pm-utils/pm-suspend/storage/state:pulse:charlie:source1
+ su charlie -c -- pacmd                     set-source-mute                     1                     yes
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
+ read index
+ state_exists pulse:charlie:source2
+ [ -O /var/run/pm-utils/pm-suspend/storage/state:pulse:charlie:source2 ]
+ restorestate pulse:charlie:source2
+ state_exists pulse:charlie:source2
+ [ -O /var/run/pm-utils/pm-suspend/storage/state:pulse:charlie:source2 ]
+ cat /var/run/pm-utils/pm-suspend/storage/state:pulse:charlie:source2
+ su charlie -c -- pacmd                     set-source-mute                     2                     yes
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
+ read index
+ su charlie -c -- pacmd suspend false
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=01PulseAudio
+ IFS=

+ IFS= 	

+ [ reverse -a reverse = reverse -a 01PulseAudio ]
+ [ 00powersave > 01PulseAudio ]
+ [ ! reverse ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/00powersave ]
+ [ -f /usr/lib/pm-utils/sleep.d/00powersave ]
+ hook=/usr/lib/pm-utils/sleep.d/00powersave
+ run_hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/00powersave
+ local hook=00powersave
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:00powersave ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:powersave ]
+ [ -x /usr/lib/pm-utils/sleep.d/00powersave ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/00powersave resume suspend
+ command_exists pm-powersave
+ type pm-powersave
+ return 0
+ pm-powersave
+ set -a
+ PM_UTILS_LIBDIR=/usr/lib/pm-utils
+ PM_UTILS_ETCDIR=/etc/pm
+ PM_UTILS_RUNDIR=/var/run/pm-utils
+ PATH=/sbin:/usr/sbin:/bin:/usr/bin:/usr/lib/pm-utils/bin
+ PM_LOGFILE=/var/log/pm-powersave.log
+ TEMPORARY_CPUFREQ_GOVERNOR=performance
+ LOCKDIR=/var/run/pm-utils/locks
+ STORAGEDIR=/var/run/pm-utils/pm-powersave/storage
+ NA=254
+ NX=253
+ DX=252
+ PM_FUNCTIONS=/usr/lib/pm-utils/functions
+ PM_QUIRKDB=/usr/lib/pm-utils/video-quirks
+ PM_LKW_QUIRKS=/var/cache/pm-utils/last_known_working.quirkdb
+ LC_COLLATE=C
+ HIBERNATE_MODE=
+ HIBERNATE_RESUME_POST_VIDEO=no
+ SLEEP_MODULE=auto
+ SUSPEND_MODULES=
+ HOOK_BLACKLIST=
+ ADD_PARAMETERS=
+ DROP_PARAMETERS=
+ PARAMETERS=/var/run/pm-utils/pm-powersave/storage/parameters
+ INHIBIT=/var/run/pm-utils/pm-powersave/storage/inhibit
+ PM_CMDLINE=
+ BEFORE_HOOKS=
+ MODULE_HELP=
+ SUSPEND_MODULE=
+ HIBERNATE_MODULE=
+ SUSPEND_HYBRID_MODULE=
+ PM_HIBERNATE_DELAY=900
+ PM_RTC=/sys/class/rtc/rtc0
+ [ -f /usr/lib/pm-utils/defaults ]
+ . /usr/lib/pm-utils/defaults
+ [ -f /usr/lib/pm-utils/pm-powersave.defaults ]
+ set +a
+ [ -f /etc/pm/config.d/*[!~] ]
+ continue
+ [ -f /etc/pm/pm-powersave.config.d/*[!~] ]
+ continue
+ . /usr/lib/pm-utils/functions
+ export PM_DEBUG=true
+ is_set true
+ return 0
+ set -x
+ profiling
+ [  = true ]
+ profiling
+ [  = true ]
+ profiling
+ [  = true ]
+ [ auto = auto ]
+ SLEEP_MODULE=tuxonice uswsusp
+ mod=/usr/lib/pm-utils/module.d/tuxonice
+ [ -f /usr/lib/pm-utils/module.d/tuxonice ]
+ . /usr/lib/pm-utils/module.d/tuxonice
+ export TUXONICE_LOC
+ [ -d /sys/power/tuxonice ]
+ [ -d /sys/power/suspend2 ]
+ [ -n  ]
+ [ -z  -a -n  ]
+ [ -z  -a -n  ]
+ mod=/usr/lib/pm-utils/module.d/uswsusp
+ [ -f /usr/lib/pm-utils/module.d/uswsusp ]
+ . /usr/lib/pm-utils/module.d/uswsusp
+ [ -z  ]
+ command_exists s2ram
+ type s2ram
+ return 127
+ [ -z  ]
+ [ -f /sys/power/disk ]
+ grep -q disk /sys/power/state
+ [ -c /dev/snapshot ]
+ command_exists s2disk
+ type s2disk
+ return 127
+ [ -z  ]
+ grep -q mem /sys/power/state
+ command_exists s2both
+ type s2both
+ return 127
+ [ -z  ]
+ grep -q mem /sys/power/state
+ SUSPEND_MODULE=kernel
+ [ -z  ]
+ [ -f /sys/power/disk ]
+ grep -q disk /sys/power/state
+ HIBERNATE_MODULE=kernel
+ [ -z  -a -w /sys/class/rtc/rtc0/wakealarm ]
+ check_suspend
+ [ -n kernel ]
+ check_hibernate
+ [ -n kernel ]
+ is_set no
+ return 1
+ SUSPEND_HYBRID_MODULE=kernel
+ lock_and_load
+ try_lock pm-powersave.lock
+ local lock=/var/run/pm-utils/locks/pm-powersave.lock
+ mkdir -p /var/run/pm-utils/locks
+ touch /var/run/pm-utils/locks/pm-powersave.lock
+ exec
+ flock -x -n 3
+ return 0
+ trap remove_powersave_lock 0
+ mkdir -p /var/run/pm-utils/pm-powersave/storage
+ rm -f /var/run/pm-utils/pm-powersave/storage/inhibit
+ load_hook_blacklist
+ [  ]
+ return
+ init_logfile /var/log/pm-powersave.log
+ [ -z /var/log/pm-powersave.log ]
+ [ -h /var/log/pm-powersave.log ]
+ [ -f /var/log/pm-powersave.log -a ! -O /var/log/pm-powersave.log ]
+ export LOGGING=true
+ exec
+ exit 0
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/00powersave resume suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/00powersave resume suspend: 
/usr/lib/pm-utils/sleep.d/00powersave resume suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=00powersave
+ IFS=

+ IFS= 	

+ [ reverse -a reverse = reverse -a 00powersave ]
+ [ 00logging > 00powersave ]
+ [ ! reverse ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/00logging ]
+ [ -f /usr/lib/pm-utils/sleep.d/00logging ]
+ hook=/usr/lib/pm-utils/sleep.d/00logging
+ run_hook /usr/lib/pm-utils/sleep.d/00logging resume suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/00logging resume suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/00logging
+ local hook=00logging
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:00logging ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:logging ]
+ [ -x /usr/lib/pm-utils/sleep.d/00logging ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/00logging resume suspend
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/00logging resume suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/00logging resume suspend: 
/usr/lib/pm-utils/sleep.d/00logging resume suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=00logging
+ IFS=

+ IFS= 	

+ [ reverse -a reverse = reverse -a 00logging ]
+ [ 000kernel-change > 00logging ]
+ [ ! reverse ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/000kernel-change ]
+ [ -f /usr/lib/pm-utils/sleep.d/000kernel-change ]
+ hook=/usr/lib/pm-utils/sleep.d/000kernel-change
+ run_hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/000kernel-change
+ local hook=000kernel-change
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:000kernel-change ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:0kernel-change ]
+ [ -x /usr/lib/pm-utils/sleep.d/000kernel-change ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: 
/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=000kernel-change
+ IFS=

+ IFS= 	

+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ return 0
+ date
+ log Mon Dec 19 11:44:47 AST 2011: Finished.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Mon Dec 19 11:44:47 AST 2011: Finished. = -n ]
+ printf %s\n Mon Dec 19 11:44:47 AST 2011: Finished.
Mon Dec 19 11:44:47 AST 2011: Finished.
+ exit 0
+ remove_suspend_lock
+ release_lock pm-suspend.lock
+ local lock=/var/run/pm-utils/locks/pm-suspend.lock
+ rm -f /var/run/pm-utils/locks/pm-suspend.lock
+ return 0
```

And finally a failed suspend from the hotkey:

```
+ log Initial commandline parameters: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Initial commandline parameters:  = -n ]
+ printf %s\n Initial commandline parameters: 
Initial commandline parameters: 
+ load_hook_blacklist
+ [  ]
+ return
+ load_hook_parameters
+ [  ]
+ [  ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ date
+ log Mon Dec 19 11:45:21 AST 2011: Running hooks for suspend.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Mon Dec 19 11:45:21 AST 2011: Running hooks for suspend. = -n ]
+ printf %s\n Mon Dec 19 11:45:21 AST 2011: Running hooks for suspend.
Mon Dec 19 11:45:21 AST 2011: Running hooks for suspend.
+ run_hooks sleep suspend suspend
+ _run_hooks sleep suspend suspend
+ local syshooks=/etc/pm/sleep.d
+ local phooks=/usr/lib/pm-utils/sleep.d
+ command_exists before_hooks
+ type before_hooks
+ return 0
+ before_hooks
+ [ -z  ]
+ return 0
+ local sort=sort
+ local base
+ local hook
+ local oifs= 	

+ local nifs=

+ IFS=

+ [  = reverse ]
+ IFS= 	

+ sort
+ [ -O /etc/pm/sleep.d/10_grub-common ]
+ + echo 10_grub-commonuniq

+ [ -O /etc/pm/sleep.d/10_unattended-upgrades-hibernate ]
+ echo 10_unattended-upgrades-hibernate
+ [ -O /etc/pm/sleep.d/novatel_3g_suspend ]
+ echo novatel_3g_suspend
+ [ -O /usr/lib/pm-utils/sleep.d/000kernel-change ]
+ echo 000kernel-change
+ [ -O /usr/lib/pm-utils/sleep.d/00logging ]
+ echo 00logging
+ [ -O /usr/lib/pm-utils/sleep.d/00powersave ]
+ echo 00powersave
+ [ -O /usr/lib/pm-utils/sleep.d/01PulseAudio ]
+ echo 01PulseAudio
+ [ -O /usr/lib/pm-utils/sleep.d/49bluetooth ]
+ echo 49bluetooth
+ [ -O /usr/lib/pm-utils/sleep.d/55NetworkManager ]
+ echo 55NetworkManager
+ [ -O /usr/lib/pm-utils/sleep.d/60_wpa_supplicant ]
+ echo 60_wpa_supplicant
+ [ -O /usr/lib/pm-utils/sleep.d/75modules ]
+ echo 75modules
+ [ -O /usr/lib/pm-utils/sleep.d/90clock ]
+ echo 90clock
+ [ -O /usr/lib/pm-utils/sleep.d/94cpufreq ]
+ echo 94cpufreq
+ [ -O /usr/lib/pm-utils/sleep.d/95anacron ]
+ echo 95anacron
+ [ -O /usr/lib/pm-utils/sleep.d/95hdparm-apm ]
+ echo 95hdparm-apm
+ [ -O /usr/lib/pm-utils/sleep.d/95led ]
+ echo 95led
+ [ -O /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler ]
+ echo 98video-quirk-db-handler
+ [ -O /usr/lib/pm-utils/sleep.d/99video ]
+ echo 99video
+ IFS= 	

+ [  -a  = reverse -a  ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/000kernel-change ]
+ [ -f /usr/lib/pm-utils/sleep.d/000kernel-change ]
+ hook=/usr/lib/pm-utils/sleep.d/000kernel-change
+ run_hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/000kernel-change
+ local hook=000kernel-change
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:000kernel-change ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:0kernel-change ]
+ [ -x /usr/lib/pm-utils/sleep.d/000kernel-change ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: 
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=000kernel-change
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 000kernel-change ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/00logging ]
+ [ -f /usr/lib/pm-utils/sleep.d/00logging ]
+ hook=/usr/lib/pm-utils/sleep.d/00logging
+ run_hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/00logging
+ local hook=00logging
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:00logging ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:logging ]
+ [ -x /usr/lib/pm-utils/sleep.d/00logging ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/00logging suspend suspend
+ [ -n /var/log/pm-suspend.log ]
+ /bin/uname -a
Linux charlie-Satellite-A660 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:28:43 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
+ lsmod
Module                  Size  Used by
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
pci_stub               12622  1 
vboxpci                23200  0 
vboxnetadp             13382  0 
vboxnetflt             23441  0 
vboxdrv               282739  3 vboxpci,vboxnetadp,vboxnetflt
parport_pc             36962  0 
dm_crypt               23199  1 
ppdev                  17113  0 
mceusb                 17906  0 
binfmt_misc            17540  1 
snd_hda_codec_hdmi     32040  4 
snd_hda_codec_realtek   330769  1 
snd_hda_intel          33390  3 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96714  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
nvidia              11713772  46 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
ir_lirc_codec          12898  0 
lirc_dev               19204  1 ir_lirc_codec
joydev                 17693  0 
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
ir_sony_decoder        12549  0 
lib80211_crypt_tkip    17390  0 
mei                    41480  0 
usbhid                 47198  0 
snd                    68266  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ir_jvc_decoder         12546  0 
wl                   2568210  0 
uvcvideo               72711  0 
ir_rc6_decoder         12546  0 
videodev               92992  1 uvcvideo
soundcore              12680  1 snd
ir_rc5_decoder         12546  0 
v4l2_compat_ioctl32    17083  1 videodev
hid                    95463  1 usbhid
psmouse                73882  0 
toshiba_bluetooth      12807  0 
jmb38x_ms              17646  0 
serio_raw              13166  0 
rc_rc6_mce             12502  0 
memstick               16569  1 jmb38x_ms
sparse_keymap          13890  0 
i7core_edac            27942  0 
edac_core              53746  3 i7core_edac
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lib80211               14991  2 lib80211_crypt_tkip,wl
ir_nec_decoder         12546  0 
ene_ir                 22796  0 
rc_core                26963  10 mceusb,ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,rc_rc6_mce,ir_nec_decoder,ene_ir
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
vesafb                 13809  1 
sdhci_pci              14032  0 
r8169                  52788  0 
ahci                   26002  3 
libahci                26861  1 ahci
sdhci                  32166  1 sdhci_pci
video                  19412  0 
+ free
             total       used       free     shared    buffers     cached
Mem:       8124760    1489680    6635080          0      86372     469768
-/+ buffers/cache:     933540    7191220
Swap:      8787964          0    8787964
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/00logging suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/00logging suspend suspend: 
/usr/lib/pm-utils/sleep.d/00logging suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=00logging
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 00logging ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/00powersave ]
+ [ -f /usr/lib/pm-utils/sleep.d/00powersave ]
+ hook=/usr/lib/pm-utils/sleep.d/00powersave
+ run_hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/00powersave
+ local hook=00powersave
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:00powersave ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:powersave ]
+ [ -x /usr/lib/pm-utils/sleep.d/00powersave ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/00powersave suspend suspend
+ command_exists pm-powersave
+ type pm-powersave
+ return 0
+ pm-powersave false
+ set -a
+ PM_UTILS_LIBDIR=/usr/lib/pm-utils
+ PM_UTILS_ETCDIR=/etc/pm
+ PM_UTILS_RUNDIR=/var/run/pm-utils
+ PATH=/sbin:/usr/sbin:/bin:/usr/bin:/usr/lib/pm-utils/bin
+ PM_LOGFILE=/var/log/pm-powersave.log
+ TEMPORARY_CPUFREQ_GOVERNOR=performance
+ LOCKDIR=/var/run/pm-utils/locks
+ STORAGEDIR=/var/run/pm-utils/pm-powersave/storage
+ NA=254
+ NX=253
+ DX=252
+ PM_FUNCTIONS=/usr/lib/pm-utils/functions
+ PM_QUIRKDB=/usr/lib/pm-utils/video-quirks
+ PM_LKW_QUIRKS=/var/cache/pm-utils/last_known_working.quirkdb
+ LC_COLLATE=C
+ HIBERNATE_MODE=
+ HIBERNATE_RESUME_POST_VIDEO=no
+ SLEEP_MODULE=auto
+ SUSPEND_MODULES=
+ HOOK_BLACKLIST=
+ ADD_PARAMETERS=
+ DROP_PARAMETERS=
+ PARAMETERS=/var/run/pm-utils/pm-powersave/storage/parameters
+ INHIBIT=/var/run/pm-utils/pm-powersave/storage/inhibit
+ PM_CMDLINE=false
+ BEFORE_HOOKS=
+ MODULE_HELP=
+ SUSPEND_MODULE=
+ HIBERNATE_MODULE=
+ SUSPEND_HYBRID_MODULE=
+ PM_HIBERNATE_DELAY=900
+ PM_RTC=/sys/class/rtc/rtc0
+ [ -f /usr/lib/pm-utils/defaults ]
+ . /usr/lib/pm-utils/defaults
+ [ -f /usr/lib/pm-utils/pm-powersave.defaults ]
+ set +a
+ [ -f /etc/pm/config.d/*[!~] ]
+ continue
+ [ -f /etc/pm/pm-powersave.config.d/*[!~] ]
+ continue
+ . /usr/lib/pm-utils/functions
+ export PM_DEBUG=true
+ is_set true
+ return 0
+ set -x
+ profiling
+ [  = true ]
+ profiling
+ [  = true ]
+ profiling
+ [  = true ]
+ [ auto = auto ]
+ SLEEP_MODULE=tuxonice uswsusp
+ mod=/usr/lib/pm-utils/module.d/tuxonice
+ [ -f /usr/lib/pm-utils/module.d/tuxonice ]
+ . /usr/lib/pm-utils/module.d/tuxonice
+ export TUXONICE_LOC
+ [ -d /sys/power/tuxonice ]
+ [ -d /sys/power/suspend2 ]
+ [ -n  ]
+ [ -z  -a -n  ]
+ [ -z  -a -n  ]
+ mod=/usr/lib/pm-utils/module.d/uswsusp
+ [ -f /usr/lib/pm-utils/module.d/uswsusp ]
+ . /usr/lib/pm-utils/module.d/uswsusp
+ [ -z  ]
+ command_exists s2ram
+ type s2ram
+ return 127
+ [ -z  ]
+ [ -f /sys/power/disk ]
+ grep -q disk /sys/power/state
+ [ -c /dev/snapshot ]
+ command_exists s2disk
+ type s2disk
+ return 127
+ [ -z  ]
+ grep -q mem /sys/power/state
+ command_exists s2both
+ type s2both
+ return 127
+ [ -z  ]
+ grep -q mem /sys/power/state
+ SUSPEND_MODULE=kernel
+ [ -z  ]
+ [ -f /sys/power/disk ]
+ grep -q disk /sys/power/state
+ HIBERNATE_MODULE=kernel
+ [ -z  -a -w /sys/class/rtc/rtc0/wakealarm ]
+ check_suspend
+ [ -n kernel ]
+ check_hibernate
+ [ -n kernel ]
+ is_set no
+ return 1
+ SUSPEND_HYBRID_MODULE=kernel
+ lock_and_load
+ try_lock pm-powersave.lock
+ local lock=/var/run/pm-utils/locks/pm-powersave.lock
+ mkdir -p /var/run/pm-utils/locks
+ touch /var/run/pm-utils/locks/pm-powersave.lock
+ exec
+ flock -x -n 3
+ return 0
+ trap remove_powersave_lock 0
+ mkdir -p /var/run/pm-utils/pm-powersave/storage
+ rm -f /var/run/pm-utils/pm-powersave/storage/inhibit
+ load_hook_blacklist
+ [  ]
+ return
+ init_logfile /var/log/pm-powersave.log
+ [ -z /var/log/pm-powersave.log ]
+ [ -h /var/log/pm-powersave.log ]
+ [ -f /var/log/pm-powersave.log -a ! -O /var/log/pm-powersave.log ]
+ export LOGGING=true
+ exec
+ exit 0
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/00powersave suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/00powersave suspend suspend: 
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=00powersave
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 00powersave ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/01PulseAudio ]
+ [ -f /usr/lib/pm-utils/sleep.d/01PulseAudio ]
+ hook=/usr/lib/pm-utils/sleep.d/01PulseAudio
+ run_hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/01PulseAudio
+ local hook=01PulseAudio
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:01PulseAudio ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:PulseAudio ]
+ [ -x /usr/lib/pm-utils/sleep.d/01PulseAudio ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend
+ suspend_pulse
+ get_pulse_users
+ test_pulse_system
+ getent passwd pulse
+ awk -F: {print $3}
+ PULSE_SYSTEM_USER=109
+ [ -z 109 ]
+ ps -C pulseaudio -o uid=
+ tr -d  
+ sed s/109//
+ getent passwd 1000
+ cut -f1 -d:
+ THIS_USER=charlie
+ save_pulse_state sink charlie
+ su charlie -c -- pacmd list-sinks
+ sed -n s/^[[:space:]*]*//; /\(index\|mute\)/p
+ index=
+ read field value
Sessions still open, not unmounting
+ [ index = index ]
+ index=0
+ read field value
+ [ muted = index ]
+ savestate pulse:charlie:sink0 no
+ [ -n no ]
+ echo no
+ read field value
+ [ index = index ]
+ index=1
+ read field value
+ [ muted = index ]
+ savestate pulse:charlie:sink1 yes
+ [ -n yes ]
+ echo yes
+ read field value
+ save_pulse_state source charlie
+ su charlie+  -c -- pacmd list-sourcessed
 -n s/^[[:space:]*]*//; /\(index\|mute\)/p
+ index=
+ read field value
Sessions still open, not unmounting
+ [ index = index ]
+ index=0
+ read field value
+ [ muted = index ]
+ savestate pulse:charlie:source0 yes
+ [ -n yes ]
+ echo yes
+ read field value
+ [ index = index ]
+ index=1
+ read field value
+ [ muted = index ]
+ savestate pulse:charlie:source1 yes
+ [ -n yes ]
+ echo yes
+ read field value
+ [ index = index ]
+ index=2
+ read field value
+ [ muted = index ]
+ savestate pulse:charlie:source2 yes
+ [ -n yes ]
+ echo yes
+ read field value
+ su charlie -c -- pacmd suspend true
+ get_pulse_users
+ test_pulse_system
+ getent passwd pulse
+ awk -F: {print $3}
+ PULSE_SYSTEM_USER=109
+ [ -z 109 ]
+ ps -C pulseaudio -o uid=
+ tr -d  
+ sed s/109//
+ getent passwd 1000
+ cut -f1 -d:
+ THIS_USER=charlie
+ su charlie -c -- ck-list-sessions | grep "active = TRUE"
+ mute_pulse sink charlie
+ su charlie -c -- pacmd list-sinks
+ + sed -n s/^[[:space:]*]*//; /\(index\|mute\)/p
index=
+ read field value
Sessions still open, not unmounting
+ [ index = index ]
+ index=0
+ su charlie -c -- pacmd                         set-sink-mute 0 yes
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
+ read field value
+ [ muted = index ]
+ read field value
+ [ index = index ]
+ index=1
+ su charlie -c -- pacmd                         set-sink-mute 1 yes
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
+ read field value
+ [ muted = index ]
+ read field value
+ mute_pulse source charlie
+ su charlie -c -- pacmd list-sources
+ sed+  -n s/^[[:space:]*]*//; /\(index\|mute\)/p
index=
+ read field value
Sessions still open, not unmounting
+ [ index = index ]
+ index=0
+ su charlie -c -- pacmd                         set-source-mute 0 yes
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
+ read field value
+ [ muted = index ]
+ read field value
+ [ index = index ]
+ index=1
+ su charlie -c -- pacmd                         set-source-mute 1 yes
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
+ read field value
+ [ muted = index ]
+ read field value
+ [ index = index ]
+ index=2
+ su charlie -c -- pacmd                         set-source-mute 2 yes
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
+ read field value
+ [ muted = index ]
+ read field value
+ break
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=01PulseAudio
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 01PulseAudio ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/10_grub-common ]
+ hook=/etc/pm/sleep.d/10_grub-common
+ run_hook /etc/pm/sleep.d/10_grub-common suspend suspend
+ _run_hook /etc/pm/sleep.d/10_grub-common suspend suspend
+ log Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /etc/pm/sleep.d/10_grub-common suspend suspend: = -n ]
+ printf %s\n Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
+ hook_ok /etc/pm/sleep.d/10_grub-common
+ local hook=10_grub-common
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:10_grub-common ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:_grub-common ]
+ [ -x /etc/pm/sleep.d/10_grub-common ]
+ return 0
+ /etc/pm/sleep.d/10_grub-common suspend suspend
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /etc/pm/sleep.d/10_grub-common suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /etc/pm/sleep.d/10_grub-common suspend suspend: 
/etc/pm/sleep.d/10_grub-common suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=10_grub-common
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 10_grub-common ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/10_unattended-upgrades-hibernate ]
+ hook=/etc/pm/sleep.d/10_unattended-upgrades-hibernate
+ run_hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend
+ _run_hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend
+ log Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: = -n ]
+ printf %s\n Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
+ hook_ok /etc/pm/sleep.d/10_unattended-upgrades-hibernate
+ local hook=10_unattended-upgrades-hibernate
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:10_unattended-upgrades-hibernate ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:_unattended-upgrades-hibernate ]
+ [ -x /etc/pm/sleep.d/10_unattended-upgrades-hibernate ]
+ return 0
+ /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: 
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=10_unattended-upgrades-hibernate
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 10_unattended-upgrades-hibernate ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/49bluetooth ]
+ [ -f /usr/lib/pm-utils/sleep.d/49bluetooth ]
+ hook=/usr/lib/pm-utils/sleep.d/49bluetooth
+ run_hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/49bluetooth
+ local hook=49bluetooth
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:49bluetooth ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:bluetooth ]
+ [ -x /usr/lib/pm-utils/sleep.d/49bluetooth ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend
+ [ -f /proc/acpi/ibm/bluetooth ]
+ exit 254
+ local status=254
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: 
/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: + hook_exit_status 254
+ log not applicable.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ not applicable. = -n ]
+ printf %s\n not applicable.
not applicable.
+ LAST_HOOK=49bluetooth
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 49bluetooth ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/55NetworkManager ]
+ [ -f /usr/lib/pm-utils/sleep.d/55NetworkManager ]
+ hook=/usr/lib/pm-utils/sleep.d/55NetworkManager
+ run_hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/55NetworkManager
+ local hook=55NetworkManager
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:55NetworkManager ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:NetworkManager ]
+ [ -x /usr/lib/pm-utils/sleep.d/55NetworkManager ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend
+ suspend_nm
+ printf Having NetworkManager put all interaces to sleep...
Having NetworkManager put all interaces to sleep...+ dbus_send --print-reply --system --dest=org.freedesktop.NetworkManager /org/freedesktop/NetworkManager org.freedesktop.NetworkManager.sleep
+ command dbus-send --print-reply --system --dest=org.freedesktop.NetworkManager /org/freedesktop/NetworkManager org.freedesktop.NetworkManager.sleep
+ return 254
+ echo Failed.
Failed.
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: 
/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=55NetworkManager
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 55NetworkManager ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/60_wpa_supplicant ]
+ [ -f /usr/lib/pm-utils/sleep.d/60_wpa_supplicant ]
+ hook=/usr/lib/pm-utils/sleep.d/60_wpa_supplicant
+ run_hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/60_wpa_supplicant
+ local hook=60_wpa_supplicant
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:60_wpa_supplicant ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:_wpa_supplicant ]
+ [ -x /usr/lib/pm-utils/sleep.d/60_wpa_supplicant ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: 
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=60_wpa_supplicant
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 60_wpa_supplicant ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/75modules ]
+ [ -f /usr/lib/pm-utils/sleep.d/75modules ]
+ hook=/usr/lib/pm-utils/sleep.d/75modules
+ run_hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/75modules
+ local hook=75modules
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:75modules ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:modules ]
+ [ -x /usr/lib/pm-utils/sleep.d/75modules ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/75modules suspend suspend
+ suspend_modules
+ [ -z  ]
+ return 254
+ local status=254
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/75modules suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/75modules suspend suspend: 
/usr/lib/pm-utils/sleep.d/75modules suspend suspend: + hook_exit_status 254
+ log not applicable.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ not applicable. = -n ]
+ printf %s\n not applicable.
not applicable.
+ LAST_HOOK=75modules
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 75modules ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/90clock ]
+ [ -f /usr/lib/pm-utils/sleep.d/90clock ]
+ hook=/usr/lib/pm-utils/sleep.d/90clock
+ run_hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/90clock
+ local hook=90clock
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:90clock ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:clock ]
+ [ -x /usr/lib/pm-utils/sleep.d/90clock ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/90clock suspend suspend
+ is_set 
+ return 2
+ exit 254
+ local status=254
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/90clock suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/90clock suspend suspend: 
/usr/lib/pm-utils/sleep.d/90clock suspend suspend: + hook_exit_status 254
+ log not applicable.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ not applicable. = -n ]
+ printf %s\n not applicable.
not applicable.
+ LAST_HOOK=90clock
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 90clock ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/94cpufreq ]
+ [ -f /usr/lib/pm-utils/sleep.d/94cpufreq ]
+ hook=/usr/lib/pm-utils/sleep.d/94cpufreq
+ run_hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/94cpufreq
+ local hook=94cpufreq
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:94cpufreq ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:cpufreq ]
+ [ -x /usr/lib/pm-utils/sleep.d/94cpufreq ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend
+ [ -d /sys/devices/system/cpu/ ]
+ hibernate_cpufreq
+ cd /sys/devices/system/cpu/
+ [ -L cpu0/cpufreq ]
+ gov=cpu0/cpufreq/scaling_governor
+ [ -f cpu0/cpufreq/scaling_governor ]
+ grep -q performance cpu0/cpufreq/scaling_available_governors
+ savestate cpu0_governor
+ [ -n  ]
+ cat
+ echo performance
+ [ -L cpu1/cpufreq ]
+ gov=cpu1/cpufreq/scaling_governor
+ [ -f cpu1/cpufreq/scaling_governor ]
+ grep -q performance cpu1/cpufreq/scaling_available_governors
+ savestate cpu1_governor
+ [ -n  ]
+ cat
+ echo performance
+ [ -L cpu2/cpufreq ]
+ gov=cpu2/cpufreq/scaling_governor
+ [ -f cpu2/cpufreq/scaling_governor ]
+ grep -q performance cpu2/cpufreq/scaling_available_governors
+ savestate cpu2_governor
+ [ -n  ]
+ cat
+ echo performance
+ [ -L cpu3/cpufreq ]
+ gov=cpu3/cpufreq/scaling_governor
+ [ -f cpu3/cpufreq/scaling_governor ]
+ grep -q performance cpu3/cpufreq/scaling_available_governors
+ savestate cpu3_governor
+ [ -n  ]
+ cat
+ echo performance
+ [ -L cpu4/cpufreq ]
+ gov=cpu4/cpufreq/scaling_governor
+ [ -f cpu4/cpufreq/scaling_governor ]
+ grep -q performance cpu4/cpufreq/scaling_available_governors
+ savestate cpu4_governor
+ [ -n  ]
+ cat
+ echo performance
+ [ -L cpu5/cpufreq ]
+ gov=cpu5/cpufreq/scaling_governor
+ [ -f cpu5/cpufreq/scaling_governor ]
+ grep -q performance cpu5/cpufreq/scaling_available_governors
+ savestate cpu5_governor
+ [ -n  ]
+ cat
+ echo performance
+ [ -L cpu6/cpufreq ]
+ gov=cpu6/cpufreq/scaling_governor
+ [ -f cpu6/cpufreq/scaling_governor ]
+ grep -q performance cpu6/cpufreq/scaling_available_governors
+ savestate cpu6_governor
+ [ -n  ]
+ cat
+ echo performance
+ [ -L cpu7/cpufreq ]
+ gov=cpu7/cpufreq/scaling_governor
+ [ -f cpu7/cpufreq/scaling_governor ]
+ grep -q performance cpu7/cpufreq/scaling_available_governors
+ savestate cpu7_governor
+ [ -n  ]
+ cat
+ echo performance
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: 
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=94cpufreq
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 94cpufreq ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/95anacron ]
+ [ -f /usr/lib/pm-utils/sleep.d/95anacron ]
+ hook=/usr/lib/pm-utils/sleep.d/95anacron
+ run_hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/95anacron
+ local hook=95anacron
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:95anacron ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:anacron ]
+ [ -x /usr/lib/pm-utils/sleep.d/95anacron ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/95anacron suspend suspend
stop: Unknown instance: 
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/95anacron suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/95anacron suspend suspend: 
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=95anacron
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 95anacron ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/95hdparm-apm ]
+ [ -f /usr/lib/pm-utils/sleep.d/95hdparm-apm ]
+ hook=/usr/lib/pm-utils/sleep.d/95hdparm-apm
+ run_hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/95hdparm-apm
+ local hook=95hdparm-apm
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:95hdparm-apm ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:hdparm-apm ]
+ [ -x /usr/lib/pm-utils/sleep.d/95hdparm-apm ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend
+ local status=254
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: 
/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: + hook_exit_status 254
+ log not applicable.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ not applicable. = -n ]
+ printf %s\n not applicable.
not applicable.
+ LAST_HOOK=95hdparm-apm
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 95hdparm-apm ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/95led ]
+ [ -f /usr/lib/pm-utils/sleep.d/95led ]
+ hook=/usr/lib/pm-utils/sleep.d/95led
+ run_hook /usr/lib/pm-utils/sleep.d/95led suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/95led suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/95led
+ local hook=95led
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:95led ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:led ]
+ [ -x /usr/lib/pm-utils/sleep.d/95led ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/95led suspend suspend
+ local status=254
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/95led suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/95led suspend suspend: 
/usr/lib/pm-utils/sleep.d/95led suspend suspend: + hook_exit_status 254
+ log not applicable.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ not applicable. = -n ]
+ printf %s\n not applicable.
not applicable.
+ LAST_HOOK=95led
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 95led ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/98video-quirk-db-handler ]
+ [ -f /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler ]
+ hook=/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler
+ run_hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler
+ local hook=98video-quirk-db-handler
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:98video-quirk-db-handler ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:video-quirk-db-handler ]
+ [ -x /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend
+ [[ -n true ]]
+ export 'PS4=${BASH_SOURCE}@${LINENO}(${FUNCNAME[0]}): '
+ PS4='${BASH_SOURCE}@${LINENO}(${FUNCNAME[0]}): '
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@10(): set -x
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@25(): possible_video_quirks=' --quirk-dpms-on
	   --quirk-dpms-suspend
	   --quirk-s3-mode
	   --quirk-s3-bios
	   --quirk-vbe-post
	   --quirk-vbe-post
	   --quirk-vga-mode-3
	   --quirk-vbemode-restore
	   --quirk-vbestate-restore
	   --quirk-reset-brightness
	   --quirk-radeon-off
	   --quirk-no-fb
	   --quirk-save-pci'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@40(): possible_system_properties='system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@343(): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@347(): precache_dmivars
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@170(precache_dmivars): local p q f
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.firmware.version
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.firmware.version* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_firmware_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_firmware_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.firmware.version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@107(dmisysget): _dmisysget bios_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@100(_dmisysget): [[ -r /sys/class/dmi/id/bios_version ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@101(_dmisysget): read RES
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=1.10
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=1.10
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_firmware_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.firmware.vendor
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.vendor =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.firmware.vendor* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_firmware_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_firmware_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.firmware.vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@106(dmisysget): _dmisysget bios_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@100(_dmisysget): [[ -r /sys/class/dmi/id/bios_vendor ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@101(_dmisysget): read RES
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=TOSHIBA
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=TOSHIBA
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_firmware_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.firmware.release_date
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.release_date =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.firmware.release_date* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_firmware_release_date
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_firmware_release_date
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.firmware.release_date
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@108(dmisysget): _dmisysget bios_date
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@100(_dmisysget): [[ -r /sys/class/dmi/id/bios_date ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@101(_dmisysget): read RES
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=04/19/10
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=04/19/10
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_firmware_release_date
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.hardware.vendor
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.hardware.vendor =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.hardware.vendor* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_hardware_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_hardware_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.hardware.vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@109(dmisysget): _dmisysget sys_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@100(_dmisysget): [[ -r /sys/class/dmi/id/sys_vendor ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@101(_dmisysget): read RES
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=TOSHIBA
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=TOSHIBA
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_hardware_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.hardware.product
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.hardware.product =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.hardware.product* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_hardware_product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_hardware_product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.hardware.product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@110(dmisysget): _dmisysget product_name
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@100(_dmisysget): [[ -r /sys/class/dmi/id/product_name ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@101(_dmisysget): read RES
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES='Satellite A660'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES='Satellite A660'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_hardware_product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.hardware.version
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.hardware.version =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.hardware.version* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_hardware_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_hardware_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.hardware.version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@111(dmisysget): _dmisysget product_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@100(_dmisysget): [[ -r /sys/class/dmi/id/product_version ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@101(_dmisysget): read RES
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=PSAW3E-01100TEN
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=PSAW3E-01100TEN
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_hardware_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.board.product
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.board.product =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.board.product* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_board_product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_board_product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.board.product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@112(dmisysget): _dmisysget board_name
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@100(_dmisysget): [[ -r /sys/class/dmi/id/board_name ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@101(_dmisysget): read RES
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=NWQAA
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=NWQAA
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_board_product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.board.version
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.board.version =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.board.version* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_board_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_board_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.board.version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@113(dmisysget): _dmisysget board_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@100(_dmisysget): [[ -r /sys/class/dmi/id/board_version ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@101(_dmisysget): read RES
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=1.00
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=1.00
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_board_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.board.vendor
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.board.vendor =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.board.vendor* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_board_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_board_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.board.vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@114(dmisysget): _dmisysget board_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@100(_dmisysget): [[ -r /sys/class/dmi/id/board_vendor ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@101(_dmisysget): read RES
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=TOSHIBA
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=TOSHIBA
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_board_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.hardware.primary_video.vendor
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.hardware.primary_video.vendor =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.hardware.primary_video.vendor* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_hardware_primary_video_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_hardware_primary_video_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.hardware.primary_video.vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@115(dmisysget): videoget vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@65(videoget): local dev pci
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@66(videoget): pci=/sys/bus/pci/devices
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:00.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:00.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:03.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:03.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:08.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:08.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:08.1/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:08.1/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:08.2/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:08.2/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:08.3/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:08.3/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:10.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:10.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:10.1/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:10.1/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:16.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:16.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x078000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1a.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1a.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x0c0320 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1b.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1b.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x040300 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.1/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.1/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.2/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.2/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.3/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.3/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.4/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.4/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1d.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1d.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x0c0320 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1e.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1e.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060401 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1f.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1f.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060100 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1f.2/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1f.2/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x010601 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1f.3/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1f.3/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x0c0500 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:01:00.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:01:00.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x030000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@70(videoget): case $1 in
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@71(videoget): cat /sys/bus/pci/devices/0000:01:00.0/vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@71(videoget): RES=0x10de
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@91(videoget): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=0x10de
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=0x10de
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_hardware_primary_video_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.hardware.primary_video.product
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.hardware.primary_video.product =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.hardware.primary_video.product* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_hardware_primary_video_product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_hardware_primary_video_product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.hardware.primary_video.product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@116(dmisysget): videoget device
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@65(videoget): local dev pci
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@66(videoget): pci=/sys/bus/pci/devices
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:00.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:00.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:03.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:03.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:08.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:08.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:08.1/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:08.1/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:08.2/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:08.2/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:08.3/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:08.3/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:10.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:10.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:10.1/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:10.1/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:16.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:16.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x078000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1a.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1a.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x0c0320 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1b.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1b.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x040300 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.1/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.1/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.2/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.2/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.3/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.3/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.4/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.4/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1d.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1d.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x0c0320 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1e.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1e.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060401 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1f.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1f.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060100 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1f.2/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1f.2/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x010601 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1f.3/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1f.3/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x0c0500 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:01:00.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:01:00.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x030000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@70(videoget): case $1 in
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@72(videoget): cat /sys/bus/pci/devices/0000:01:00.0/device
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@72(videoget): RES=0x0a29
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@91(videoget): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=0x0a29
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=0x0a29
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_hardware_primary_video_product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.hardware.primary_video.driver
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.hardware.primary_video.driver =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.hardware.primary_video.driver* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_hardware_primary_video_driver
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_hardware_primary_video_driver
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.hardware.primary_video.driver
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@117(dmisysget): videoget driver
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@65(videoget): local dev pci
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@66(videoget): pci=/sys/bus/pci/devices
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:00.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:00.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:03.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:03.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:08.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:08.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:08.1/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:08.1/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:08.2/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:08.2/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:08.3/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:08.3/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:10.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:10.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:10.1/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:10.1/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:16.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:16.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x078000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1a.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1a.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x0c0320 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1b.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1b.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x040300 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.1/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.1/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.2/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.2/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.3/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.3/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.4/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.4/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1d.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1d.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x0c0320 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1e.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1e.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060401 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1f.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1f.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060100 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1f.2/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1f.2/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x010601 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1f.3/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1f.3/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x0c0500 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:01:00.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:01:00.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x030000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@70(videoget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@74(videoget): [[ -L /sys/bus/pci/devices/0000:01:00.0/driver ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@75(videoget): readlink /sys/bus/pci/devices/0000:01:00.0/driver
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@75(videoget): RES=../../../../bus/pci/drivers/nvidia
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@76(videoget): RES=nvidia
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@91(videoget): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=nvidia
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=nvidia
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_hardware_primary_video_driver
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.hardware.primary_video.using_kms
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.hardware.primary_video.using_kms =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.hardware.primary_video.using_kms* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_hardware_primary_video_using_kms
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_hardware_primary_video_using_kms
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.hardware.primary_video.using_kms
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@118(dmisysget): videoget using_kms
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@65(videoget): local dev pci
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@66(videoget): pci=/sys/bus/pci/devices
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:00.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:00.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:03.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:03.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:08.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:08.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:08.1/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:08.1/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:08.2/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:08.2/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:08.3/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:08.3/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:10.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:10.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:10.1/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:10.1/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x088000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:16.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:16.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x078000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1a.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1a.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x0c0320 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1b.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1b.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x040300 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.1/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.1/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.2/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.2/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.3/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.3/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1c.4/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1c.4/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1d.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1d.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x0c0320 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1e.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1e.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060401 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1f.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1f.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060100 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1f.2/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1f.2/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x010601 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:1f.3/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:1f.3/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x0c0500 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:01:00.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:01:00.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x030000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@70(videoget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@84(videoget): using_kms
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@60(using_kms): grep -q -E '(nouveau|drm)fb' /proc/fb
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@87(videoget): RES=false
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@91(videoget): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=false
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=false
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_hardware_primary_video_using_kms
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.kernel.version
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.kernel.version =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.kernel.version* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_kernel_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_kernel_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.kernel.version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@119(dmisysget): uname -r
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@119(dmisysget): RES=3.0.0-14-generic
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=3.0.0-14-generic
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=3.0.0-14-generic
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_kernel_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@181(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@352(): has_parameter --quirk-test
//usr/lib/pm-utils/functions@240(has_parameter): get_parameters
//usr/lib/pm-utils/functions@235(get_parameters): cat /var/run/pm-utils/pm-suspend/storage/parameters
/usr/lib/pm-utils/functions@244(has_parameter): return 1
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@358(): using_kms
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@60(using_kms): grep -q -E '(nouveau|drm)fb' /proc/fb
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@363(): using_nvidia
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@54(using_nvidia): [[ -d /sys/module/nvidia ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@365(): remove_parameters --quirk-dpms-on --quirk-dpms-suspend --quirk-s3-mode --quirk-s3-bios --quirk-vbe-post --quirk-vbe-post --quirk-vga-mode-3 --quirk-vbemode-restore --quirk-vbestate-restore --quirk-reset-brightness --quirk-radeon-off --quirk-no-fb --quirk-save-pci
/usr/lib/pm-utils/functions@211(remove_parameters): local p
/usr/lib/pm-utils/functions@212(remove_parameters): '[' --quirk-dpms-on = all ']'
/usr/lib/pm-utils/functions@215(remove_parameters): echo ''
/usr/lib/pm-utils/functions@216(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@217(remove_parameters): echo --quirk-dpms-on
/usr/lib/pm-utils/functions@216(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@217(remove_parameters): echo --quirk-dpms-suspend
/usr/lib/pm-utils/functions@216(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@217(remove_parameters): echo --quirk-s3-mode
/usr/lib/pm-utils/functions@216(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@217(remove_parameters): echo --quirk-s3-bios
/usr/lib/pm-utils/functions@216(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@217(remove_parameters): echo --quirk-vbe-post
/usr/lib/pm-utils/functions@216(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@217(remove_parameters): echo --quirk-vbe-post
/usr/lib/pm-utils/functions@216(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@217(remove_parameters): echo --quirk-vga-mode-3
/usr/lib/pm-utils/functions@216(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@217(remove_parameters): echo --quirk-vbemode-restore
/usr/lib/pm-utils/functions@216(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@217(remove_parameters): echo --quirk-vbestate-restore
/usr/lib/pm-utils/functions@216(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@217(remove_parameters): echo --quirk-reset-brightness
/usr/lib/pm-utils/functions@216(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@217(remove_parameters): echo --quirk-radeon-off
/usr/lib/pm-utils/functions@216(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@217(remove_parameters): echo --quirk-no-fb
/usr/lib/pm-utils/functions@216(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@217(remove_parameters): echo --quirk-save-pci
/usr/lib/pm-utils/functions@220(remove_parameters): grep -vxFf /var/run/pm-utils/pm-suspend/storage/parameters.rm /var/run/pm-utils/pm-suspend/storage/parameters
/usr/lib/pm-utils/functions@222(remove_parameters): cp -f /var/run/pm-utils/pm-suspend/storage/parameters.new /var/run/pm-utils/pm-suspend/storage/parameters
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@366(): echo 'nVidia binary video drive detected, not using quirks.'
nVidia binary video drive detected, not using quirks.
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: 
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=98video-quirk-db-handler
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 98video-quirk-db-handler ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ get_parameters
+ cat /var/run/pm-utils/pm-suspend/storage/parameters
+ export PM_CMDLINE=
+ rm -f /var/run/pm-utils/pm-suspend/storage/parameters.new
+ [ -f /etc/pm/sleep.d/99video ]
+ [ -f /usr/lib/pm-utils/sleep.d/99video ]
+ hook=/usr/lib/pm-utils/sleep.d/99video
+ run_hook /usr/lib/pm-utils/sleep.d/99video suspend suspend
+ _run_hook /usr/lib/pm-utils/sleep.d/99video suspend suspend
+ log Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend: = -n ]
+ printf %s\n Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
+ hook_ok /usr/lib/pm-utils/sleep.d/99video
+ local hook=99video
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:99video ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:video ]
+ [ -x /usr/lib/pm-utils/sleep.d/99video ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/99video suspend suspend
+ command_exists vbetool
+ type vbetool
+ return 0
+ command_exists radeontool
+ type radeontool
+ return 0
+ maybe_chvt
+ is_set 
+ return 2
+ + fgconsole
savestate console
+ [ -n  ]
+ cat
+ chvt 63
+ suspend_video
+ local acpi_flag=0
+ quirk 
+ is_set 
+ return 2
+ quirk 
+ is_set 
+ return 2
+ sysctl -w kernel.acpi_video_flags=0
kernel.acpi_video_flags = 0
+ quirk 
+ is_set 
+ return 2
+ quirk 
+ is_set 
+ return 2
+ quirk 
+ is_set 
+ return 2
+ quirk 
+ is_set 
+ return 2
+ quirk 
+ is_set 
+ return 2
+ quirk 
+ is_set 
+ return 2
+ quirk 
+ is_set 
+ return 2
+ save_fbcon
+ local con
+ [ -f /sys/class/graphics/fb0/state ]
+ echo 1
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /usr/lib/pm-utils/sleep.d/99video suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/99video suspend suspend: 
/usr/lib/pm-utils/sleep.d/99video suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=99video
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 99video ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/novatel_3g_suspend ]
+ hook=/etc/pm/sleep.d/novatel_3g_suspend
+ run_hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend
+ _run_hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend
+ log Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend: = -n ]
+ printf %s\n Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
+ hook_ok /etc/pm/sleep.d/novatel_3g_suspend
+ local hook=novatel_3g_suspend
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:novatel_3g_suspend ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:novatel_3g_suspend ]
+ [ -x /etc/pm/sleep.d/novatel_3g_suspend ]
+ return 0
+ /etc/pm/sleep.d/novatel_3g_suspend suspend suspend
+ local status=0
+ log 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [  = -n ]
+ printf %s\n 

+ log -n /etc/pm/sleep.d/novatel_3g_suspend suspend suspend: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /etc/pm/sleep.d/novatel_3g_suspend suspend suspend: 
/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: + hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=novatel_3g_suspend
+ IFS=

+ IFS= 	

+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ return 0
+ date
+ log Mon Dec 19 11:45:25 AST 2011: performing suspend
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Mon Dec 19 11:45:25 AST 2011: performing suspend = -n ]
+ printf %s\n Mon Dec 19 11:45:25 AST 2011: performing suspend
Mon Dec 19 11:45:25 AST 2011: performing suspend
+ sync
+ do_suspend
+ echo -n mem
```

I hope you know what you're looking for, because I'm thoroughly lost!

Cheers
Charlie

---

### Post by Toz on 2011-12-19
Unfortunately, nothing of significance shows up between the good and bad hotkey logs (other than the fact that an awake event is never triggered for the bad hotkey attempt).

Are there any discernible patterns to the successful/unsuccessful suspends? 

- Does the first hotkey attempt always work and the second one fail?
- Does the command line suspend __always__ work? Even if you try hotkey first?

Here is a link to a new method of locating the offending hash that is preventing resume: [https://wiki.ubuntu.com/Kernel/Reference/S3SystemTapDebug]("https://wiki.ubuntu.com/Kernel/Reference/S3SystemTapDebug"). Its a little complicated (need to install a debug kernel) and still under development, but it might help identify the cause of the hang.

---

### Post by FokkerCharlie on 2012-02-11
Hi again

I have finally found time to take another look at this, and am getting a bit stuck.  In particular, it seems that the testing kernel that the instructions on the page attempt to install does not exist in the repos for the current (3.0.0-15), so I installed the -12 version.

However, booting that kernel is a bit strange: it seems that the graphics are messed up, and the nvidia driver is not in use.

COuld you advise- can I run the rest of the debugging steps listed while using the -15 kernel, or do I have to boot and fix the -12 version?

Thanks in advance for helping with what I suspect is a stupid question!

Cheers
Charlie

---

### Post by FokkerCharlie on 2012-03-02
Right!

OK, so I ran the script using the -12 kernel.  I ran the following:

```
sudo ./s3test -s
```

And strangely, the log files appear to be empty.  However, the system did seem to hang, and in accordance with the insctructions on the [previously linked page]("https://wiki.ubuntu.com/Kernel/Reference/S3SystemTapDebug"), I ran the locatehang script after rebooting.  Here's the output:

```
$ sudo ./locatehang 
[sudo] password for charlie: 
Looking for function that matches hash from the Magic Number from the kernel log.
  Magic: 3:476:552 maps to hash: 867a43
  Hash matches: disable_nonboot_cpus() (address: ffffffff81060790)
```

Having a google of this does turn some stuff up, but it's a bit beyond me, tbh.  Any thoughts?

Thanks in advance!

Charlie

---

### Post by Toz on 2012-03-02
From what I understand, suspend has to be run on one cpu, so in systems where there is more than one cpu/core, the secondary ones are offlined in the suspend process and onlined during the resume process. Found a more complete description of the process [_here_]("http://lxr.free-electrons.com/source/Documentation/power/suspend-and-cpuhotplug.txt"). Usually this happens normally, but in your case, there seems to be a hangup.

Are there any configuration settings in your bios related to cpu off-lining?

As a test, try manually off-lining the secondary cpus then initiating a suspend/resume cycle (as root):
```
echo 0 > /sys/devices/system/cpu/cpu*/online
```
...and onlining them after resume:
```
echo 1 > /sys/devices/system/cpu/cpu*/online
```

---

### Post by FokkerCharlie on 2012-03-02
Hi Toz

Thanks again for your response.

I don't think that there is anything in the BIOS about CPU offlining, I will double-check.

Regarding the manual offlining command that you suggest, I want to double-check what you mean- if I enter the command verbatim in a terminal, I get this:

```
$ sudo echo 0 > /sys/devices/system/cpu/cpu*/online
bash: /sys/devices/system/cpu/cpu*/online: ambiguous redirect

```

But I'm not sure that's the idea.  If I try manipulate the CPUs individually, it's giving me a permissions problem:

```
sudo echo 0 > /sys/devices/system/cpu/cpu1/online
bash: /sys/devices/system/cpu/cpu1/online: Permission denied
```

Hang on, this one seems to work:

```
echo 0 | sudo tee /sys/devices/system/cpu/cpu*/online
```

Charlie

---

### Post by FokkerCharlie on 2012-03-02
Right.

Got that working in terms of offlining secondary CPUs.  Suspended fine 3 times, but on the forth attempt, I got a kernel panic.  I'll try a few more times, and report back.

Charlie

---

### Post by FokkerCharlie on 2012-03-03
OK, managed to recreate the suspend issue with the CPUs offline.  Interestingly (or maybe not), I see the CAPS lock flashing for a few seconds, then it stays lit.  I guess this is a kernel panic, but I'm not an expert on that.

In any case, suspend fails, then running locatehang after a reboot does not turn anything up.

:(

---

### Post by Toz on 2012-03-03
Hmmmm. Have you tried the most recent kernel? We're up to 16 now.

---

### Post by FokkerCharlie on 2012-03-03
Yes, using the -16 kernel.  I was going to try running the test script again, but now the -12-dbgsym kernel doesn't want to boot properly :(

Interesting aside- I did boot the 12-dbgsym kernel in recovery mode (accidentally!), and attempted to shutdown the system with 'sudo halt'.  All went normally, until the final message "System Halted", which remained on the screen, and my lappy did not turn itself off.

Maybe it's ghosts?  Wooooooo!

Charlie

---

### Post by Toz on 2012-03-03
I'm afraid I'm out of ideas. I noticed that you had a launchpad bug report for a similar problem a while back. Might be time to create another bug report.

---

### Post by FokkerCharlie on 2012-03-16
Hmmm.

I have been busy collecting information to put into the bug, and it seems that adding the kernel parameter "nolapic" makes suspend work OK.  Unfortunately, that reduces my CPU to only one core, which seems a shame!

Before I go ahead and file the bug, anything else we should consider?

Charlie

**EDIT** Scrub that.  Looks like it was just a lucky streak!!

---

### Post by FokkerCharlie on 2012-03-17
New bug filed

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/957759]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/957759")

---

