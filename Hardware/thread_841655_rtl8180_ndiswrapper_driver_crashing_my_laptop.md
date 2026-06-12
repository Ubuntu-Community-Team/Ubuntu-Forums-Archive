---
title: "rtl8180 ndiswrapper driver crashing my laptop"
date: 2008-06-26
forum: Hardware
---

### Post by cuak on 2008-06-26
I've got a CLEVO laptop (rebranded as Bangho in Argentina).

it's a BanghóMov CQ1406CC with Celeron 530, Chipset VIA VN896CE + VT8237A
the equivalent CLEVO model seems to be the CLEVO M660SR 

I'm running ubuntu 8.04 with kernel 2.6.24-19-generic, all updates from update manager has been installed.

anyway, the built-in usb wireless adapter is a RTL8187

output from lsusb:
Bus 005 Device 005: ID 0bda:8187 Realtek Semiconductor Corp. 

I did blacklist the native linux driver (rtl8187)
and I'm using the rtl8187 Win98 driver on ndiswrapper

output from ndiswrapper -l:
netrtuw : driver installed
	device (0BDA:8187) present (alternate driver: rtl8187)

I can connect with the nm-applet to my wireless network, but every now and then, the laptop crashes, it stops responding, and I'm forced to press the power button to shut it down. 

when I boot I see no panic, core files, logs or any related messages to help me provide a bug report.

if I remove the ndiswrapper driver, the computer doesn't crash at all.

how can I grab more information about this issue? 

the laptop freezing is very random, I experience it 2 or 3 times a day, and I can't force it to "crash".

how can I get a traceback, debug log or anything related to a system freeze like this?


thanks!

---

### Post by phidia on 2008-06-26
You can look in /var/log (syslog, message. dmesg, or xorg) could contain output related to the freezing/crashing.

---

### Post by cuak on 2008-06-26
> **phidia said:**
> You can look in /var/log (syslog, message. dmesg, or xorg) could contain output related to the freezing/crashing.

thanks for the reply.
There's nothing in the logs, it seems the kernel suddenly stops responding without even writing a single event to logfiles.

what can be done to trace/debug this? any hints?

---

### Post by Adridar on 2008-06-26
I couldn't get ndiswrapper to work on my laptop either, kept trying to get it to run my wireless card, but it ended up completely killing my installation of Linux, so I hadda reinstall. I ended up scrapping ndiswrapper and going with MadWifi, was finally able to get my wireless up and running under Hardy x64....my wireless card is the dreaded Atheros AR5007EG, it took some work to get it to work, and I know your wireless card is different, but mine runs like a charm using MadWifi....should check it out if you don't have any luck with ndiswrapper :-).

Cheers

---

### Post by phidia on 2008-06-26
Actually [madwifi]("http://madwifi.org/") is solely for wireless cards with an atheros chipset. (see their wire-up at that link)

There is a guide [here]("http://rtl8180-sa2400.sourceforge.net/") I don't know how helpful that will be though. The community documentation on network devices is [here]("https://help.ubuntu.com/community/NetworkDevices").

Maybe ndiswrapper isn't installed correctly or you need the latest version (the latest [stable version is 1.53]("http://sourceforge.net/project/showfiles.php?group_id=93482"))
Check out the ndiswrapper [troubleshooting guide]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,troubleshooting/") too.

---

### Post by cuak on 2008-06-30
> **phidia said:**
> Actually [madwifi]("http://madwifi.org/") is solely for wireless cards with an atheros chipset. (see their wire-up at that link)

There is a guide [here]("http://rtl8180-sa2400.sourceforge.net/") I don't know how helpful that will be though. The community documentation on network devices is [here]("https://help.ubuntu.com/community/NetworkDevices").

Maybe ndiswrapper isn't installed correctly or you need the latest version (the latest [stable version is 1.53]("http://sourceforge.net/project/showfiles.php?group_id=93482"))
Check out the ndiswrapper [troubleshooting guide]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,troubleshooting/") too.

I've been running ndiswrapper 1.50 (the one that comes with hardy) and now I've compiled version 1.53, and reinstalled the driver.

it still crashes.

can someone point me out how to obtain information about the crash when nothing gets written to the logs and the kernel suddenly stops responding?

thanks!

---

### Post by daniel.hartman on 2008-07-07
I am having similar problems with a Broadcom BCM4306.  The crashes are intermittent and generally occur during heavy network bandwidth (e.g., Samba).  The problems began when I upgraded from Gutsy to Hardy Heron and the native driver resulted in a 1Mb/s Bit Rate, so I resorted to ndiswrapper and got my Bit Rate to 54Mb/s.

Here is what I see from dmesg:

```

[36430.916346] Oops: 0000 [#1] SMP
[36430.916351] Modules linked in: ext2 usb_storage libusual usbhid hid
ohci_hcd ssb ndiswrapper binfmt_misc bc_cast(PF) bc_rijn(PF) bc_idea(PF)
bc_3des(PF) bc_bf128(PF) bc_bf448(PF) bc_twofish(PF) bc_gost(PF)
bc_des(PF) bc_blowfish(PF) bc(PF) ipv6 rfcomm l2cap bluetooth nfsd lockd
nfs_acl auth_rpcgss sunrpc exportfs ppdev powernow_k8 cpufreq_stats
cpufreq_conservative cpufreq_userspace cpufreq_powersave
cpufreq_ondemand freq_table container dock sbs sbshc af_packet
iptable_filter ip_tables x_tables sbp2 parport_pc lp parport joydev
pcmcia zc0301 compat_ioctl32 evdev gspca snd_usb_audio snd_usb_lib
videodev v4l2_common serio_raw v4l1_compat snd_hwdep psmouse sdhci
tifm_7xx1 fglrx(P) pcspkr mmc_core tifm_core yenta_socket rsrc_nonstatic
pcmcia_core snd_atiixp video output snd_seq_dummy battery
snd_atiixp_modem snd_ac97_codec snd_seq_oss ac ac97_bus snd_pcm_oss
snd_mixer_oss snd_seq_midi k8temp snd_rawmidi snd_seq_midi_event snd_pcm
wmi_acer snd_seq snd_timer snd_seq_device button snd soundcore
snd_page_alloc i2c_piix4 i2c_core shpchp ati_agp pci_hotplug agpgart
ext3 jbd mbcache sg sr_mod cdrom sd_mod atiixp ide_core ata_generic
8139cp pata_atiixp 8139too mii ohci1394 pata_acpi ieee1394 libata
scsi_mod ehci_hcd usbcore thermal processor fan fbcon tileblit font
bitblit softcursor fuse
[36430.916463]
[36430.916467] Pid: 5896, comm: ntos_wq Tainted: PF (2.6.24-19-generic #1)
[36430.916473] EIP: 0060:[<f9dbf9fa>] EFLAGS: 00010246 CPU: 0
[36430.916484] EIP is at 0xf9dbf9fa
[36430.916488] EAX: 00000000 EBX: ef451ef0 ECX: 00000001 EDX: 00000006
[36430.916492] ESI: f88c1000 EDI: f88c1000 EBP: ef451ed8 ESP: ef451ea0
[36430.916496]  DS: 007b ES: 007b FS: 00d8 GS: 0000 SS: 0068
[36430.916501] Process ntos_wq (pid: 5896, ti=ef450000 task=f2b95140 task.ti=ef450000)
[36430.916505] Stack: 54011000 f88c1000 00000000 000000b3 f8870000 00004108 ef06c000 00000001
[36430.916515]        c02a1988 c031c428 dfac8724 00000000 00000287 ef7959c0 ef451f08 f9dc506a
[36430.916524]        ef451ef0 f8874000 f88c1000 00000000 00003082 10015401 04320000 f2b90000
[36430.916533] Call Trace:
[36430.916585]  [<c02a1988>] sock_wfree+0x38/0x40
[36430.916598]  [<c031c428>] _spin_lock_bh+0x8/0x20
[36430.916820]  [<f8c96cd0>] kdpc_worker+0x0/0x110 [ndiswrapper]
[36430.916863]  [<f8c913d4>] deserialized_irq_handler+0x14/0x40 [ndiswrapper]
[36430.916910]  [<f8c96d6f>] kdpc_worker+0x9f/0x110 [ndiswrapper]
[36430.916988]  [<c013ce8f>] run_workqueue+0xbf/0x160
[36430.917039]  [<c013d930>] worker_thread+0x0/0xe0
[36430.917052]  [<c013d9b4>] worker_thread+0x84/0xe0
[36430.917072]  [<c0140c40>] autoremove_wake_function+0x0/0x40
[36430.917105]  [<c013d930>] worker_thread+0x0/0xe0
[36430.917117]  [<c0140982>] kthread+0x42/0x70
[36430.917122]  [<c0140940>] kthread+0x0/0x70
[36430.917138]  [<c0105677>] kernel_thread_helper+0x7/0x10
[36430.917182]  =======================
[36430.917184] Code: ff 80 bf d7 10 00 00 00 89 45 f4 74 09 6a 00 8b c7 e8 0b 35 ff ff 83 7d f4 00 75 0c 8b ce 8b f7
[36430.917221] EIP: [<f9dbf9fa>] 0xf9dbf9fa SS:ESP 0068:ef451ea0
[36430.917235] ---[ end trace df0a0552aab464f7 ]---

```

I have to have a terminal open "pre-crash", since a crash results in not being able to open a terminal.

It is my understanding that the reference to ntos_wq indicates that it might be an ndiswrapper problem.

Currently, I'm using version 1.52:

```

# ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.24-19-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.52
vermagic:       2.6.24-19-generic SMP mod_unload 586
#

```

According to [http://ndiswrapper.sourceforge.net](http://ndiswrapper.sourceforge.net), version 1.53 of ndiswrapper:  "Fixed oops on unload if using our workqueue implementation with SMP enabled."  

I'm reluctant to install and compile version 1.53 when I'm not sure if this is my problem and a package might be available soon through Ubuntu's updates....

---

### Post by offchance on 2008-08-24
I have the exact problem as the original poster! it is good to see someone explain a problem I myself have been having for some time (although I'm not glad he has the problem to begin with...). 

I switched from gutsy to hardy, networkmanager to wicd, and it's all the same. if I use my wireless I will have crashes.

---

