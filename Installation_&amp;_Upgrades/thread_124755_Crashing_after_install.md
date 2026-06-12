---
title: "Crashing after install"
date: 2006-02-02
forum: Installation &amp; Upgrades
---

### Post by ColinTh on 2006-02-02
My hardware..

AMD64 3000 2Gb RAM

Nforce 3 Motherboard (GA-K8NS Ultra-939)

I have installed Ubuntu Breezy (the 386 version) and all went well, I can use everything fine when I go to the desktop straight from finishing the installer.

The problem I have is after my first reboot, I can no longer log in, either from gdm or from a terminal.

I have found the following in syslog:

Feb  2 11:32:17 localhost /usr/sbin/cron[6869]: (CRON) INFO (Running @reboot jobs)
Feb  2 11:32:19 localhost kernel: [   92.602039] eth0: no IPv6 routers present
Feb  2 11:32:25 localhost kernel: [  172.565720] ------------[ cut here ]------------
Feb  2 11:32:25 localhost kernel: [  172.570071] kernel BUG at :49795!
Feb  2 11:32:25 localhost kernel: [  172.574546] invalid operand: 0000 [#1]
Feb  2 11:32:25 localhost kernel: [  172.578942] Modules linked in: rfcomm l2cap bluetooth powernow_k8 cpufreq_userspace cpufreq_stats freq_table cpufreq_powersave cpufreq_ondemand cpufreq_conservative apm ipv6 af_packet analog gameport floppy pcspkr rtc pci_hotplug snd_intel8x0 snd_ac97_codec snd_pcm_oss snd_mixer_oss snd_pcm snd_timer snd soundcore snd_page_alloc i2c_nforce2 i2c_core amd64_agp agpgart dm_mod tsdev evdev psmouse mousedev parport_pc lp parport md ext3 jbd processor skge forcedeth ehci_hcd ohci_hcd usbcore ide_cd cdrom ide_disk ide_generic sata_nv libata scsi_mod amd74xx ide_core unix vesafb capability commoncap vga16fb vgastate softcursor cfbimgblt cfbfillrect cfbcopyarea fbcon tileblit font bitblit
Feb  2 11:32:25 localhost kernel: [  172.624610] CPU:    0
Feb  2 11:32:25 localhost kernel: [  172.624612] EIP:    0060:[kmem_freepages+57/136]    Not tainted VLI
Feb  2 11:32:25 localhost kernel: [  172.624614] EFLAGS: 00010246   (2.6.12-9-386) 
Feb  2 11:32:25 localhost kernel: [  172.639079] EIP is at kmem_freepages+0x39/0x88
Feb  2 11:32:25 localhost kernel: [  172.644010] eax: 00000000   ebx: 00000001   ecx: 00000000   edx: c16e1f00
Feb  2 11:32:25 localhost kernel: [  172.649076] esi: dfffff80   edi: f70f8f01   ebp: 00000001   esp: dfa07f1c
Feb  2 11:32:25 localhost kernel: [  172.654349] ds: 007b   es: 007b   ss: 0068
Feb  2 11:32:25 localhost kernel: [  172.659739] Process events/0 (pid: 3, threadinfo=dfa06000 task=dfb35020)
Feb  2 11:32:25 localhost kernel: [  172.659908] Stack: dfffff80 f70ec740 f70f8f01 c01341d2 dfffff80 f70f8f01 dfffff80 dffffff0 
Feb  2 11:32:25 localhost kernel: [  172.671298]        00000005 dfffb640 c0135070 dfffff80 f70ec740 c03715e0 c03715e4 00000297 
Feb  2 11:32:25 localhost kernel: [  172.683074]        00000000 c01214c8 00000000 c0134f98 ffffffff ffffffff 00000001 00000000 
Feb  2 11:32:25 localhost kernel: [  172.695537] Call Trace:
Feb  2 11:32:25 localhost kernel: [  172.707760]  [slab_destroy+88/121] slab_destroy+0x58/0x79
Feb  2 11:32:25 localhost kernel: [  172.713972]  [cache_reap+216/269] cache_reap+0xd8/0x10d
Feb  2 11:32:25 localhost kernel: [  172.720110]  [worker_thread+343/443] worker_thread+0x157/0x1bb
Feb  2 11:32:25 localhost kernel: [  172.726124]  [cache_reap+0/269] cache_reap+0x0/0x10d
Feb  2 11:32:25 localhost kernel: [  172.732103]  [default_wake_function+0/18] default_wake_function+0x0/0x12
Feb  2 11:32:25 localhost kernel: [  172.738126]  [schedule+1086/1188] schedule+0x43e/0x4a4
Feb  2 11:32:25 localhost kernel: [  172.744022]  [default_wake_function+0/18] default_wake_function+0x0/0x12
Feb  2 11:32:25 localhost kernel: [  172.749923]  [worker_thread+0/443] worker_thread+0x0/0x1bb
Feb  2 11:32:25 localhost kernel: [  172.755711]  [kthread+109/151] kthread+0x6d/0x97
Feb  2 11:32:25 localhost kernel: [  172.761534]  [kthread+0/151] kthread+0x0/0x97
Feb  2 11:32:25 localhost kernel: [  172.767297]  [kernel_thread_helper+5/11] kernel_thread_helper+0x5/0xb
Feb  2 11:32:25 localhost kernel: [  172.773033] Code: 24 10 8d 97 00 00 00 40 8b 4e 44 c1 ea 0c d3 e3 c1 e2 05 8d 4b ff 03 15 30 6b 37 c0 83 f9 ff 74 12 0f ba 32 07 19 c0 85 c0 75 02 <0f> 0b 83 c2 20 49 eb e9 89 d8 f7 d8 50 6a 14 e8 df e3 ff ff 58 
Feb  2 11:32:31 localhost kernel: [  172.795224]  pdflush: bogus wakeup!
Feb  2 11:32:31 localhost kernel: [  179.006884] pdflush: bogus wakeup!
Feb  2 11:32:31 localhost kernel: [  179.013119] pdflush: bogus wakeup!
Feb  2 11:32:31 localhost kernel: [  179.019239] pdflush: bogus wakeup!
Feb  2 11:32:31 localhost kernel: [  179.025298] pdflush: bogus wakeup!
Feb  2 11:32:31 localhost kernel: [  179.031178] pdflush: bogus wakeup!
Feb  2 11:32:31 localhost kernel: [  179.036769] pdflush: bogus wakeup!

I'm really stuck with this, any and all help would be very appreciated.

I have tried various options in the kernel command line, currently I'm using :

Kernel command line: root=/dev/hda2 ro acpi=off pci=noacpi

Please, somebody help me :D

---

### Post by ColinTh on 2006-02-02
Just as a bit of an update,

I've accessed through vmware, so can actually use the system for the time being, but not ideal (no OpenGL etc). But I can at least access things.

Updating the kernel etc doesn't seem to have helped at all, I can start ok with the recovery option from grub, so suspect it might be something that gnome/X is loading?

Still hoping somebody has some ideas.

---

