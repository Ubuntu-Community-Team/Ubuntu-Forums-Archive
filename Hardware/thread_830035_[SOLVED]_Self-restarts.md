---
title: "[SOLVED] Self-restarts"
date: 2008-06-15
forum: Hardware
---

### Post by shimmering on 2008-06-15
Please help me. I'm going insane over Ubuntu because this is the second major problem I have run into and I am extremely frustrated about it, especially since I have big assignments due this week.

Straight to the point. I was browsing Firefox, listening to music and downloading some music when suddenly, Ubuntu self-restarts. Before Ubuntu loads up, the PC restarts itself again up until it simply shuts down at the end. Things got worse after that and the self-restarts are unpredictable.

I managed to pinpoint the problem to hardware fault. I tried booting up with the Live CD, but the problem persists. I also heard a whirring sound (besides the fan) that was not there previously. I pinpointed (guessed) the sound to the graphics card, I took it out and connected the monitor to the onboard graphics. This screwed up my screen resolution. I tried reconnecting the graphics card again, and the screen resolution remains really low, and I can't get it past 640 x 480!

I seriously don't know what to do now! And I am on the verge of madness. I suspect the RAM or the graphics card or overheating (the heat sink - at least that's what I think it is - feels really hot) are to be blamed, but I really don't know. I'm so clueless now. Can anybody help me, please???? :(

---

### Post by pytheas22 on 2008-06-15
I'd blame overheating, probably due to a faulty fan.  Check your BIOS--most have an option allowing you to force the system to shut down when the temperature reaches a certain point; that's probably what's going on.  Try raising the threshold or turning the auto-shutdown feature off (but this is dangerous and could fry your CPU, motherboard and other things if they really do get too hot) to see if the restarts keep happening, just so you know where the problem lies.

Removing your graphics card and falling back to the onboard video might help, especially if the faulty fan is on your video card.  Your BIOS might also have an option where you can monitor system temperature and fan speeds; take a look to figure out if any fans are running at low speeds, and replace them if necessary.  Opening the computer case and blowing a real fan on it can be a temporary solution, too.

---

### Post by shimmering on 2008-06-16
I have checked the BIOS. I'm not very sure how to raise the threshold since I couldn't find that option anywhere.  I took a look at the PC Health before and after self-restarts. This is what I got.

CPU fan speed - 5442 RPM, slightly fluctuating
System temperature - from 32 C to 47 C
CPU temperature - from 30 C to 41 C
JSYS FAN speed (?) - 0 RPM

It doesn't look too good to me, and it looks like overheating. There isn't an option to check the fan speed of the graphics card. Does the fan need replacing? :S

Thank you so, so much for your help! I really appreciate it. :)

---

### Post by pytheas22 on 2008-06-16
Actually the temperatures you're reporting should be alright, I think.  You don't need to start worrying until you get past 60 C, and even then you usually have a ways to go before anything gets fried.  Of course, you could be getting these lower temperatures because the system is idle, but when you're doing something the temperatures will increase and cause the shutdown.

On the other hand, it's strange that your system temperature is higher than that of the CPU.  Usually it's the other way around.  The reason for this could be that the graphics card is indeed overheating, which would cause the system temperature to rise more than that of the CPU.  Or it could be because the system fan is turned off (that's the one reporting 0 RPM).  You should make sure that all fans are plugged in.  But then again, the fan could just be off because it only comes on when the system reaches a certain temperature.

You could also unplug your PCI graphics card and use the onboard one to see if it makes a difference.

It might also be useful to you to install utilities so that you can watch system and CPU temperature from Ubuntu.  This [page]("http://www.techthrob.com/tech/linuxsensors.php") is an excellent guide for setting it all up.  Then you can see if the temperature is indeed dramatically increasing while you are working.

Finally, if the system is really shutting down because of temperature, you should find a message to that effect in the system log.  The next time your system shuts itself down, take a look at the log--you can use the utility at System>Administration>System Log--and find the entries matching the time that the system went down.  See if there's any mention of temperature or any other problems.

Let us know if you find anything useful; if not we can keep on looking for the source of the problem, whether it's overheating or not.

---

### Post by shimmering on 2008-06-17
I was able to find only 2 fans in the motherboard, one's the system and the other's the graphics card. BTW, the graphics card is an AGP one. I opened the system unit while the PC was running and found that the system fan was spinning normally. No idea about the fan of the graphics card since it is underneath it.

Following your suggestion, I then took out the graphics card. Lo and behold, the computer runs fine! :D It has been half an hour already, and Ubuntu has not restarted yet. The slight whine is gone too! I think the problem is now solved. I guess the graphics card is to be blamed. But can it be sent for repair now that it is found to be faulty? I am still not entirely sure what is wrong with it, though, or why it suddenly turned faulty.

I took a quick look at the system log, but I was unable to find any "errors". I'm posting an extract of it which I think covers the last minutes before Ubuntu restarted.

```
Jun 17 16:06:46 shim-pc parport0: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Jun 17 16:06:46 shim-pc kernel: [  300.569898] ppdev0: registered pardevice 
Jun 17 16:06:46 shim-pc kernel: [  300.770979] audit(1213690006.548:3): type=1503 operation="inode_permission" requested_mask="::rw" denied_mask="::rw" name="/dev/tty" pid=5903 profile="/usr/sbin/cupsd" namespace="default" 
Jun 17 16:06:47 shim-pc kernel: [  301.292887] sysctl table check failed: /dev/parport/parport0/devices/ppdev0/timeslice  Sysctl already exists 
Jun 17 16:06:47 shim-pc kernel: [  301.292906] Pid: 5912, comm: hpijs Tainted: P        2.6.24-18-generic #1 
Jun 17 16:06:47 shim-pc kernel: [  301.292934]  [set_fail+0x45/0x60] set_fail+0x45/0x60 
Jun 17 16:06:47 shim-pc kernel: [  301.292957]  [sysctl_check_table+0x296/0x5b0] sysctl_check_table+0x296/0x5b0 
Jun 17 16:06:47 shim-pc kernel: [  301.292961]  [sysctl_head_finish+0x18/0x30] sysctl_head_finish+0x18/0x30 
Jun 17 16:06:47 shim-pc kernel: [  301.292986]  [sysctl_check_table+0x2aa/0x5b0] sysctl_check_table+0x2aa/0x5b0 
Jun 17 16:06:47 shim-pc kernel: [  301.292990]  [sysctl_head_finish+0x18/0x30] sysctl_head_finish+0x18/0x30 
Jun 17 16:06:47 shim-pc kernel: [  301.293011]  [sysctl_check_table+0x2aa/0x5b0] sysctl_check_table+0x2aa/0x5b0 
Jun 17 16:06:47 shim-pc kernel: [  301.293015]  [sysctl_head_finish+0x18/0x30] sysctl_head_finish+0x18/0x30 
Jun 17 16:06:47 shim-pc kernel: [  301.293037]  [sysctl_check_table+0x2aa/0x5b0] sysctl_check_table+0x2aa/0x5b0 
Jun 17 16:06:47 shim-pc kernel: [  301.293040]  [sysctl_head_finish+0x18/0x30] sysctl_head_finish+0x18/0x30 
Jun 17 16:06:47 shim-pc kernel: [  301.293062]  [sysctl_check_table+0x2aa/0x5b0] sysctl_check_table+0x2aa/0x5b0 
Jun 17 16:06:47 shim-pc kernel: [  301.293066]  [sysctl_head_finish+0x18/0x30] sysctl_head_finish+0x18/0x30 
Jun 17 16:06:47 shim-pc kernel: [  301.293088]  [sysctl_check_table+0x2aa/0x5b0] sysctl_check_table+0x2aa/0x5b0 
Jun 17 16:06:47 shim-pc kernel: [  301.293091]  [sysctl_set_parent+0x19/0x30] sysctl_set_parent+0x19/0x30 
Jun 17 16:06:47 shim-pc kernel: [  301.293113]  [irda:register_sysctl_table+0x50/0x150] register_sysctl_table+0x50/0xa0 
Jun 17 16:06:47 shim-pc kernel: [  301.293124]  [<f8a9f90e>] parport_device_proc_register+0xae/0xe0 [parport] 
Jun 17 16:06:47 shim-pc kernel: [  301.293147]  [<f8a9de29>] parport_register_device+0x139/0x260 [parport] 
Jun 17 16:06:47 shim-pc kernel: [  301.293173]  [<f8d3b765>] pp_ioctl+0x445/0x830 [ppdev] 
Jun 17 16:06:47 shim-pc kernel: [  301.293181]  [<f8d3b240>] pp_irq+0x0/0x50 [ppdev] 
Jun 17 16:06:47 shim-pc kernel: [  301.293212]  [do_ioctl+0x78/0x90] do_ioctl+0x78/0x90 
Jun 17 16:06:47 shim-pc kernel: [  301.293229]  [vfs_ioctl+0x22e/0x2b0] vfs_ioctl+0x22e/0x2b0 
Jun 17 16:06:47 shim-pc kernel: [  301.293235]  [do_sys_open+0xbe/0xe0] do_sys_open+0xbe/0xe0 
Jun 17 16:06:47 shim-pc kernel: [  301.293249]  [sys_ioctl+0x56/0x70] sys_ioctl+0x56/0x70 
Jun 17 16:06:47 shim-pc kernel: [  301.293262]  [sysenter_past_esp+0x6b/0xa9] sysenter_past_esp+0x6b/0xa9 
Jun 17 16:06:47 shim-pc kernel: [  301.293306]  ======================= 
Jun 17 16:06:47 shim-pc kernel: [  301.293308] ppdev0: registered pardevice 
Jun 17 16:06:47 shim-pc hpijs: io/hpmud/pp.c 627: unable to read device-id ret=-110 
Jun 17 16:07:26 shim-pc kernel: [  340.718625] ppdev0: unregistered pardevice 
Jun 17 16:07:32 shim-pc anacron[5207]: Job `cron.daily' started 
Jun 17 16:07:32 shim-pc anacron[5918]: Updated timestamp for job `cron.daily' to 2008-06-17 
Jun 17 16:07:41 shim-pc parport0: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Jun 17 16:07:41 shim-pc kernel: [  356.000657] ppdev0: unregistered pardevice 
Jun 17 16:08:30 shim-pc hald: unmounted /dev/sdc1 from '/media/USB DISK' on behalf of uid 1000 
Jun 17 16:08:33 shim-pc kernel: [  407.613357] usb 5-8: USB disconnect, address 2 
Jun 17 16:08:33 shim-pc NetworkManager: <debug> [1213690113.599747] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_1307_163_00000000002AC0_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Jun 17 16:08:33 shim-pc NetworkManager: <debug> [1213690113.614565] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_118C_305D'). 
Jun 17 16:08:33 shim-pc NetworkManager: <debug> [1213690113.651812] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/storage_serial_USB_USB2FlashStorage_00000000002AC0_0_0'). 
Jun 17 16:08:33 shim-pc NetworkManager: <debug> [1213690113.658687] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_1307_163_00000000002AC0_if0_scsi_host_scsi_device_lun0'). 
Jun 17 16:08:33 shim-pc NetworkManager: <debug> [1213690113.661640] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_1307_163_00000000002AC0_if0_scsi_host'). 
Jun 17 16:08:33 shim-pc NetworkManager: <debug> [1213690113.671906] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_1307_163_00000000002AC0_if0'). 
Jun 17 16:08:33 shim-pc NetworkManager: <debug> [1213690113.693284] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_1307_163_00000000002AC0'). 
Jun 17 16:12:47 shim-pc syslogd 1.5.0#1ubuntu1: restart.
```

Thanks for recommending that utility! I will definitely make some time to download it later. 

A slight problem: I'm using the onboard graphics, and the resolution is horrible. Is there any way to increase it beyond 640*480? Anyway, I'm already overjoyed that I can work on my assignments without silly interruptions. So thank you, thank you, thank you! :guitar:

---

### Post by pytheas22 on 2008-06-17
I'm glad you seem to have found a solution.  Now let's hope the system really stays up with the graphics card removed.

As for fixing the resolution, first backup your current xorg.conf file just in case:
```

cp /etc/X11/xorg.conf ~/Desktop.xorg.conf.bak
```

then run this command to automatically reconfigure X:
```

sudo dpkg-reconfigure -phigh xserver-xorg
```

If that doesn't work for some reason (I've had flaky behavior with it in the past), please post the output of the command:
```

lspci
```

so that we can figure out if there's something else you need to do based on the kind of onboard graphics you're using.

As for repairing the graphics card, you might want to first try it in another machine to confirm that it's definitely faulty there too.  Otherwise I'm not sure what the repair policies on cards are.  It probably depends who you bought it from and who made; if I were you, I'd get in touch with one of those parties to see if they'll repair it.

---

### Post by shimmering on 2008-06-18
Oh yes! That works - it's big and nice now, thank you! :) Unfortunately, I purchased the graphics card overseas a year or two ago so I can't get it fixed there. :( I will try and find a local technician to fix that.

---

### Post by pytheas22 on 2008-06-18
I'm glad it worked, and thanks for the thanks.  Good luck with the graphics card.

---

