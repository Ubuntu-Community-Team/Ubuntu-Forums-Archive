---
title: "FiiO X3II not working in DAC mode in ubuntu 14.04.2 (64-bit)"
date: 2015-04-22
forum: Hardware
---

### Post by xsk3l3t0rx on 2015-04-22
so i just bought a hi-fi DAP (digital audio player) from FiiO so that i'd have excellent sound on the go. this particular DAP also can function as a high quality DAC between your computer and a preamp/headphone amp. it is confirmed working by other head-fi users on windows, mac, AND several flavors of linux. some of the confirmed are debian, suse, kubuntu (supposedly works OOTB by a fellow forum member), and gentoo. it is a class compliant micro usb interface, and although ubuntu does detect the DAC, it wreaks havoc on my system. i'm at work so i can give you in-depth info at this second, but i will update this post tonight. here's what i CAN tell you:

booting w/ DAP connected to PC:
*black screen at login window (wont boot with DAC connected

booting w/o DAP connected to PC:
*everything works fine/as usual.

booting w/o DAP connected, then once logged in and at desktop, i connect DAP
*all inputs/outputs disappear from pulseaudio
*aplay -l wont detect ANY audio inputs/outputs
*sudo alsa-reload AND/OR pulseaudio -k AND/OR pulseaudio --kill wont do anything. 
*computer wont logout/shutdown through menu, i have to hold the power button and HARD SHUTDOWN PC
*i can detect FiiO DAC in deadbeef music player

i use deadbeef to play music using the ALSA output, i dont use pulseaudio so that i may have bit-perfect playback and directly connect to the hardware with no conversions. i am running kernel 3.16

link to forum where issue is being discussed: [http://www.head-fi.org/t/743704/the-fiio-x3-2nd-gen-ex-x3k-x3ii-thread-192k-24b-cs4398-native-dsd-usb-dac-with-lo-and-inline-remote/2520](http://www.head-fi.org/t/743704/the-fiio-x3-2nd-gen-ex-x3k-x3ii-thread-192k-24b-cs4398-native-dsd-usb-dac-with-lo-and-inline-remote/2520) 
*i post as "xsk3l3t0rx"

---

### Post by matt_symes on 2015-04-22
Hi

Wow ! I don't own one of those devices and i have never owned any device that has that effect on a PC.

Let's forget the booting up problem for the moment.

When you plug the FiiO in after logging in, what does it say in dmesg or syslog ? Any clues there ?

Kind regards

---

### Post by xsk3l3t0rx on 2015-04-22
output of dmesg: [FONT=Lucida Console][165215.707165] FAT-fs (sde1): unable to read boot sector to mark fs as dirty
[165247.188518] usb 3-4: new high-speed USB device number 6 using xhci_hcd
[165247.426239] usb 3-4: New USB device found, idVendor=2972, idProduct=0003
[165247.426244] usb 3-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[165247.426247] usb 3-4: Product: FiiO USB Audio Class 2.0 DAC
[165247.426249] usb 3-4: Manufacturer: SmartAction
[165247.426251] usb 3-4: SerialNumber: 0007
[165247.429500] usb 3-4: 0:2 : does not exist
[/FONT]

output of syslog (i accidentally connected it in regular usb mass storage mode first, so ignore those first few lines, i unmounted/disconnected, started it in dac mode, then reconnected it to usb port): 
[FONT=Lucida Console]Apr 22 19:19:08 neptune kernel: [165215.672203] usb 3-4: USB disconnect, device number 5
Apr 22 19:19:08 neptune udisksd[2483]: Cleaning up mount point /media/david/fiio stick (device 8:65 no longer exist)
Apr 22 19:19:08 neptune kernel: [165215.707165] FAT-fs (sde1): unable to read boot sector to mark fs as dirty
Apr 22 19:19:40 neptune kernel: [165247.188518] usb 3-4: new high-speed USB device number 6 using xhci_hcd
Apr 22 19:19:40 neptune kernel: [165247.426239] usb 3-4: New USB device found, idVendor=2972, idProduct=0003
Apr 22 19:19:40 neptune kernel: [165247.426244] usb 3-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Apr 22 19:19:40 neptune kernel: [165247.426247] usb 3-4: Product: FiiO USB Audio Class 2.0 DAC
Apr 22 19:19:40 neptune kernel: [165247.426249] usb 3-4: Manufacturer: SmartAction
Apr 22 19:19:40 neptune kernel: [165247.426251] usb 3-4: SerialNumber: 0007
Apr 22 19:19:40 neptune kernel: [165247.429500] usb 3-4: 0:2 : does not exist
Apr 22 19:19:40 neptune mtp-probe: checking bus 3, device 6: "/sys/devices/pci0000:00/0000:00:14.0/usb3/3-4"
Apr 22 19:19:40 neptune mtp-probe: bus: 3, device: 6 was not an MTP device
Apr 22 19:21:58 neptune kernel: [165385.329895] threaded-ml[10226]: segfault at 24 ip 00007f0dfb29f080 sp 00007f0de36f8928 error 4 in chrome[7f0df70a7000+5153000]
Apr 22 19:22:46 neptune pulseaudio[20149]: [pulseaudio] main.c: User-configured server at {8b5145e35fbe9445a34263bb55184c58}unix:/run/user/1000/pulse/native, which appears to be local. Probing deeper.
Apr 22 19:22:46 neptune rtkit-daemon[1589]: Successfully made thread 20152 of process 20152 (n/a) owned by '1000' high priority at nice level -11.
Apr 22 19:22:46 neptune rtkit-daemon[1589]: Supervising 2 threads of 2 processes of 1 users.
Apr 22 19:22:46 neptune pulseaudio[20152]: [pulseaudio] pid.c: Daemon already running.
Apr 22 19:22:51 neptune pulseaudio[21176]: [pulseaudio] main.c: User-configured server at {8b5145e35fbe9445a34263bb55184c58}unix:/run/user/1000/pulse/native, which appears to be local. Probing deeper.
Apr 22 19:22:51 neptune rtkit-daemon[1589]: Successfully made thread 21181 of process 21181 (n/a) owned by '1000' high priority at nice level -11.
Apr 22 19:22:51 neptune rtkit-daemon[1589]: Supervising 2 threads of 2 processes of 1 users.
Apr 22 19:22:51 neptune pulseaudio[21181]: [pulseaudio] pid.c: Daemon already running.
Apr 20 21:23:01 neptune whoopsie[1239]: online
Apr 22 19:22:52 neptune whoopsie[1239]: Parsing /var/crash/_opt_google_chrome_chrome.1000.crash.
Apr 22 19:22:52 neptune whoopsie[1239]: Uploading /var/crash/_opt_google_chrome_chrome.1000.crash.
Apr 22 19:22:53 neptune kernel: [165440.041261] INFO: task pulseaudio:2303 blocked for more than 120 seconds.
Apr 22 19:22:53 neptune kernel: [165440.041265]       Tainted: P           OE 3.16.0-34-generic #47~14.04.1-Ubuntu
Apr 22 19:22:53 neptune kernel: [165440.041266] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Apr 22 19:22:53 neptune kernel: [165440.041267] pulseaudio      D ffff88041edd30c0     0  2303   2035 0x00000000
Apr 22 19:22:53 neptune kernel: [165440.041270]  ffff8803eb443b60 0000000000000082 ffff8800d48e1460 ffff8803eb443fd8
Apr 22 19:22:53 neptune kernel: [165440.041271]  00000000000130c0 00000000000130c0 ffff880408685180 ffff880404059c00
Apr 22 19:22:53 neptune kernel: [165440.041273]  ffff8803da8c2b50 ffff880404059c00 0000000000000004 ffff8803da8c2b30
Apr 22 19:22:53 neptune kernel: [165440.041274] Call Trace:
Apr 22 19:22:53 neptune kernel: [165440.041279]  [<ffffffff817689d9>] schedule+0x29/0x70
Apr 22 19:22:53 neptune kernel: [165440.041281]  [<ffffffff81569f75>] usb_kill_urb+0x65/0xa0
Apr 22 19:22:53 neptune kernel: [165440.041285]  [<ffffffff810b4d70>] ? prepare_to_wait_event+0x100/0x100
Apr 22 19:22:53 neptune kernel: [165440.041286]  [<ffffffff81568b28>] usb_hcd_flush_endpoint+0x198/0x200
Apr 22 19:22:53 neptune kernel: [165440.041289]  [<ffffffff812471fc>] ? kernfs_find_ns+0x9c/0xf0
Apr 22 19:22:53 neptune kernel: [165440.041290]  [<ffffffff8156bd69>] usb_disable_endpoint+0x59/0x90
Apr 22 19:22:53 neptune kernel: [165440.041292]  [<ffffffff8156bde9>] usb_disable_interface+0x49/0x60
Apr 22 19:22:53 neptune kernel: [165440.041294]  [<ffffffff8156c33e>] usb_set_interface+0x1be/0x380
Apr 22 19:22:53 neptune kernel: [165440.041302]  [<ffffffffc0702881>] snd_usb_init_sample_rate+0x251/0x350 [snd_usb_audio]
Apr 22 19:22:53 neptune kernel: [165440.041306]  [<ffffffffc070d46e>] snd_usb_pcm_prepare+0xbe/0x550 [snd_usb_audio]
Apr 22 19:22:53 neptune kernel: [165440.041313]  [<ffffffffc0648aea>] ? snd_pcm_lib_ioctl+0x15a/0x260 [snd_pcm]
Apr 22 19:22:53 neptune kernel: [165440.041316]  [<ffffffffc0640d77>] snd_pcm_do_prepare+0x17/0x30 [snd_pcm]
Apr 22 19:22:53 neptune kernel: [165440.041319]  [<ffffffffc064080d>] snd_pcm_action_single+0x2d/0x70 [snd_pcm]
Apr 22 19:22:53 neptune kernel: [165440.041323]  [<ffffffffc0640a6e>] snd_pcm_action_nonatomic+0x6e/0x80 [snd_pcm]
Apr 22 19:22:53 neptune kernel: [165440.041326]  [<ffffffffc0643962>] snd_pcm_common_ioctl1+0x472/0xd70 [snd_pcm]
Apr 22 19:22:53 neptune kernel: [165440.041329]  [<ffffffff8105af5c>] ? __do_page_fault+0x20c/0x560
Apr 22 19:22:53 neptune kernel: [165440.041332]  [<ffffffffc0644358>] snd_pcm_playback_ioctl1+0xf8/0x250 [snd_pcm]
Apr 22 19:22:53 neptune kernel: [165440.041335]  [<ffffffffc06444e0>] snd_pcm_playback_ioctl+0x30/0x40 [snd_pcm]
Apr 22 19:22:53 neptune kernel: [165440.041338]  [<ffffffff811e7090>] do_vfs_ioctl+0x2e0/0x4c0
Apr 22 19:22:53 neptune kernel: [165440.041339]  [<ffffffff811e72f1>] SyS_ioctl+0x81/0xa0
Apr 22 19:22:53 neptune kernel: [165440.041341]  [<ffffffff8176ca6d>] system_call_fastpath+0x1a/0x1f
Apr 22 19:22:53 neptune whoopsie[1239]: Sent; server replied with: No error
Apr 22 19:22:53 neptune whoopsie[1239]: Response code: 200
Apr 22 19:22:53 neptune whoopsie[1239]: Got command: OOPSID[/FONT]

---

### Post by matt_symes on 2015-04-23
Hi

> [FONT=Lucida Console]Apr 22 19:22:53 neptune kernel: [165440.041267] pulseaudio      D ffff88041edd30c0     0  2303   2035 0x00000000[/FONT]

Well pulse is hanging in the D state while trying to access a disk. The state is interruptible and explains why you can't kill pulse.

> [FONT=Lucida Console][165215.707165] FAT-fs (sde1): unable to read boot sector to mark fs as dirty[/FONT]

I assume that sde1 is the file system on the FiiO ? If so, I'm wondering if the above two log entries are related as the boot sector in sde1 cannot be read.

Can you repair the file system on sde1 ?

Kind regards

---

### Post by Rodrigo_Diez_Villa on 2015-07-06
I had the same symptoms on a different linux distro but I managed to get it working

For some reason Fiio X3ii was not playing very well on my Thinkpad's USB 3 ports. The solution was to disable USB 3 and to map all the physical USB ports to the USB 2 controller in the BIOS. After I did that, it worked for me and no problems so far

---

### Post by Manukyan_Michael on 2016-02-28
I've managed to make it work on my laptop. I've created **.asoundrc** in my home directory with the following content:

```

pcm.DAC {
   type hw
   card 2
   device 0
}


ctl.!default {
   type hw
   card "hw:2,0"
}


pcm.!default {
   type plug
   slave {
      pcm "DAC"
      rate "unchanged"
   }
}

```

Your card and device number may differ. You can get it using the following command:
```

 ~ &#57520; cat /proc/asound/DAC/pcm0p/info          
card: **2**
device: **0**
subdevice: 0
stream: PLAYBACK
id: USB Audio
name: USB Audio
subname: subdevice #0
class: 0
subclass: 0
subdevices_count: 1
subdevices_avail: 1

```

Also, sometimes Fiio won't work with xHCI USB controllers. You can remap them using the following command:
```

#!/bin/sh
rmmod xhci_pci
rmmod xhci_hcd
setpci -H1 -s 00:14.0 d8.l=0
setpci -H1 -s 00:14.0 d0.l=0

```

Where **00:14.0 **is your xHCI USB controller (which can be viewed using **lspci **&#8203;command).

---

