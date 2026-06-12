---
title: "Suspend/resume and Hauppauge Nova-T 500"
date: 2009-10-18
forum: Hardware
---

### Post by dookka on 2009-10-18
I'm having a problem with suspend / resume and a Hauppauge Nova-T 500 TV card on Jaunty.
Initially it would hang on suspend (never switches off), so adding to /etc/pm/config.d/modules
SUSPEND_MODULES="dvb_usb_dib0700"
and a script /etc/pm/sleep.d/01-MYTH-BACKEND to stop/start mythtv-backend (otherwise dvb_usb_div0700 can't be unloaded)
Now it suspends.
When resuming, first time round everything is OK.
Second time round, resume take much longer (~22s vs. 7s) and TV doesn't work in Myth.  In dmesg:

[  112.792014] hub 2-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[  115.760011] hub 2-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[  118.728515] hub 2-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[  121.696016] hub 2-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[  121.696028] hub 2-0:1.0: unable to enumerate USB device on port 1
[  121.956027] usb 4-1: new full speed USB device using uhci_hcd and address 2
[  122.095063] usb 4-1: not running at top speed; connect to a high speed hub
[  122.122379] usb 4-1: configuration #1 chosen from 1 choice
[  122.127067] dvb-usb: found a 'Hauppauge Nova-TD-500 (84xxx)' in cold state, will try to load a firmware
[  122.127072] usb 4-1: firmware: requesting dvb-usb-dib0700-1.20.fw
[  122.141927] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.20.fw'
[  123.770084] dib0700: firmware started successfully.
[  124.272024] dvb-usb: found a 'Hauppauge Nova-TD-500 (84xxx)' in warm state.
[  124.272072] dvb-usb: This USB2.0 device cannot be run on a USB1.1 port. (it lacks a hardware PID filter)
[  124.272095] dvb-usb: Hauppauge Nova-TD-500 (84xxx) error while loading driver (-19)

Currently I have in /etc/pm/config.d/modules
SUSPEND_MODULES="rt61pci dvb_usb_dib0700 dib0070"
rt61pci so wifi can connect on resume, and dib0070 because:

[  109.802231] ------------[ cut here ]------------
[  109.802233] WARNING: at /build/buildd/linux-2.6.28/kernel/power/main.c:177 suspend_test_finish+0x80/0x90()
[  109.802234] Component: resume devices
[  109.802235] Modules linked in: nfs bridge stp bnep nfsd lockd nfs_acl auth_rpcgss sunrpc exportfs input_polldev video output xfs coretemp it87 hwmon_vid lp snd_hda_codec_nvhdmi snd_hda_codec_realtek arc4 ecb snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device ppdev lirc_imon lirc_dev usbhid nvidia(P) pcspkr snd soundcore snd_page_alloc parport_pc parport agpgart forcedeth ohci1394 ieee1394 fbcon tileblit font bitblit softcursor [last unloaded: dib0070]
[  109.802260] Pid: 4664, comm: pm-suspend Tainted: P           2.6.28-14-generic #47-Ubuntu
[  109.802261] Call Trace:
[  109.802264]  [<c0139aa0>] warn_slowpath+0x60/0x80
[  109.802266]  [<c015384a>] ? down_trylock+0x2a/0x40
[  109.802268]  [<c013a0fd>] ? try_acquire_console_sem+0xd/0x30
[  109.802270]  [<c02c7b00>] ? kobject_put+0x20/0x50
[  109.802273]  [<c04fde46>] ? printk+0x18/0x1a
[  109.802275]  [<c01650f0>] suspend_test_finish+0x80/0x90
[  109.802277]  [<c01651c6>] suspend_devices_and_enter+0xc6/0x160
[  109.802279]  [<c04fde46>] ? printk+0x18/0x1a
[  109.802280]  [<c0165449>] enter_state+0xc9/0x100
[  109.802282]  [<c01654fd>] state_store+0x7d/0xc0
[  109.802284]  [<c0165480>] ? state_store+0x0/0xc0
[  109.802285]  [<c02c79c4>] kobj_attr_store+0x24/0x30
[  109.802288]  [<c020ae92>] sysfs_write_file+0x92/0xf0
[  109.802290]  [<c01bdcf8>] vfs_write+0x98/0x110
[  109.802292]  [<c020ae00>] ? sysfs_write_file+0x0/0xf0
[  109.802293]  [<c01bde2d>] sys_write+0x3d/0x70
[  109.802295]  [<c0103f6b>] sysenter_do_call+0x12/0x2f
[  109.802297] ---[ end trace 134862aa5db89c29 ]---

dib0070 doesn't make any difference and now I don't know what to do.
I've attached my dmesg which contains a clean startup, a successful suspend/resume and an unsuccessful suspend/resume.
Oh, and uname -r:
2.6.28-14-generic

Any help appreciated!
dookka

---

### Post by vinylgroover on 2009-10-22
I also have this TV card and it would stop my computer from suspending it, just a blank screen...

I wrote this script which solved it, it doesn't take long to suspend/wake, maybe 5seconds... maybe it might work for you. Make sure your sudoers file allows the commands, I've got my sudo set to not ask for a password! /etc/sudoers add in line %admin ALL=NOPASSWD: ALL

**/usr/lib/pm-utils/sleep.d/01mythtv**

```

#!/bin/bash

. "${PM_FUNCTIONS}"

case "$1" in
  suspend|hibernate)
    sudo killall mythfrontend.real &> /dev/null
    sudo service mythtv-backend stop &> /dev/null
    sudo rmmod dvb_usb_dib0700 &> /dev/null
    ;;

  resume|thaw)
    sudo modprobe dvb_usb_dib0700 &> /dev/null
    sudo service mythtv-backend start &> /dev/null
    ;;
esac

```

---

### Post by dookka on 2009-10-26
Thanks for the reply!
I tried your script and it allowed one suspend/resume cycle as before but the TV card was dead on the second resume.

I think rmmodding dvb_usb_dib0700 fixes the card issue but now I think I also have a problem with the USB controllers and my motherboard (Gigabyte GA-73PVM-S2H), so I'll look in that direction.

By the way, I don't need to use sudo in my sleep.d hooks as the hooks are run as root anyway.

---

