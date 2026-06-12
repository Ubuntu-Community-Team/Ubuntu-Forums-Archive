---
title: "Ubuntu on Compact Flash"
date: 2009-04-18
forum: Hardware
---

### Post by taiji_jian on 2009-04-18
Hi All,

I really need some help here. 

I have a Thinkpad X40 with one of those horrible 1.8 inch hard drives with the increasing load-cycle problem. Unfortunately its behavior is built into the drive - you can't fix it with hdparm or firmware tools. 

So I looked into replacing the hard disk with a Compact Flash card and a CF/IDE adapter from Addonics. I have the same adapter mentioned in this blog post: 

[http://vort.org/2008/02/21/converting-an-ibm-x40-to-flash/](http://vort.org/2008/02/21/converting-an-ibm-x40-to-flash/)

The Compact Flash card I have is a Kingston Elite Pro 133x 32GB card.

This is the second time I've tried to do this; originally I used this adapter:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16812200174](http://www.newegg.com/Product/Product.aspx?Item=N82E16812200174)

Along with a different Compact Flash card. I ultimately RMA'd both that card and the adapter, because I thought the problems I was having were due to hardware failure. However, I am now having the same problems using an entirely different adapter and a new Compact Flash card. This leads me to think that the problem is Ubuntu-related. 

Here's what's going on: 

After a short time of use (a few minutes to an hour or so), the Compact Flash card starts spitting out I/O errors like this: 

```

[38480.476681] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET
driverbyte=DRIVER_OK,SUGGEST_OK
[38480.476689] end_request: I/O error, dev sda, sector 12375
[38480.476705] EXT3-fs error (device sda1): ext3_find_entry: reading
directory #2 offset 0

```

The card is then immediately remounted read-only for diagnostics. However, if I try to do anything to it at this point I always get "buffer I/O errors," or "device/resource busy" errors.

If I reboot, the card again works fine for a while, except that the filesystem is pretty chewed up and fsck takes a while to recombobulate it

The problem doesn't seem to be related to bad blocks on the card itself; I ran fsck -c -c overnight and it completed fine. 

If I try to unmount and remount the card after it fails, I get this:

```

[39095.647342] WARNING: at /build/buildd/linux-2.6.27/fs/buffer.c:1186
mark_buffer_dirty+0x85/0xa0()
[39095.647346] Modules linked in: ipv6 usb_storage libusual ext3 jbd
mbcache nls_iso8859_1 vfat fat i915 drm binfmt_misc af_packet bridge
stp bnep sco rfcomm l2cap bluetooth ppdev lp speedstep_centrino
cpufreq_userspace cpufreq_stats cpufreq_powersave cpufreq_ondemand
freq_table cpufreq_conservative wmi sbs sbshc pci_slot container
iptable_filter ip_tables x_tables mmc_block pcmcia snd_intel8x0
snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm
snd_seq_dummy thinkpad_acpi snd_seq_oss rfkill snd_seq_midi
snd_rawmidi led_class snd_seq_midi_event snd_seq nsc_ircc nvram
snd_timer sdhci_pci yenta_socket parport_pc irda psmouse video
rsrc_nonstatic wlan_scan_sta ath_rate_sample snd_seq_device sdhci
crc_ccitt parport output ath_pci battery ac evdev serio_raw pcspkr
mmc_core pcmcia_core button wlan ath_hal(P) intel_agp snd soundcore
agpgart snd_page_alloc shpchp iTCO_wdt iTCO_vendor_support pci_hotplug
squashfs loop aufs exportfs nls_cp437 isofs sr_mod cdrom sd_mod
crc_t10dif sg ata_piix pata_acpi ata_generic libata e1000 uhci_hcd
ehci_hcd scsi_mod usbcore dock thermal processor fan fbcon tileblit
font bitblit softcursor fuse
[39095.647493] Pid: 10127, comm: umount Tainted: P          2.6.27-7-generic #1
[39095.647498]  [<c037c3f6>] ? printk+0x1d/0x1f
[39095.647510]  [<c0131de9>] warn_on_slowpath+0x59/0x90
[39095.647519]  [<c0381fdf>] ? kprobe_flush_task+0x5f/0x80
[39095.647528]  [<c037e875>] ? __reacquire_kernel_lock+0x15/0x70
[39095.647535]  [<c037c9ae>] ? schedule+0x44e/0x790
[39095.647542]  [<c01475af>] ? finish_wait+0x4f/0x70
[39095.647548]  [<c037e61d>] ? _spin_lock+0xd/0x10
[39095.647554]  [<c01d78e5>] mark_buffer_dirty+0x85/0xa0
[39095.647560]  [<f8f96012>] journal_update_superblock+0x72/0xd0 [jbd]
[39095.647576]  [<f8f963d5>] journal_destroy+0xa5/0x100 [jbd]
[39095.647587]  [<f8fd9b19>] ext3_put_super+0x29/0x200 [ext3]
[39095.647607]  [<c037d3c8>] ? mutex_unlock+0x8/0x20
[39095.647612]  [<c01c7e3e>] ? invalidate_inodes+0xde/0xf0
[39095.647637]  [<c01b3fd2>] generic_shutdown_super+0x62/0x100
[39095.647645]  [<c037e61d>] ? _spin_lock+0xd/0x10
[39095.647650]  [<c01eb240>] ? vfs_quota_off+0x0/0x380
[39095.647659]  [<c01b4084>] kill_block_super+0x14/0x30
[39095.647665]  [<c01b4364>] deactivate_super+0x64/0x90
[39095.647670]  [<c01cb170>] mntput_no_expire+0xc0/0x120
[39095.647677]  [<c01cb779>] sys_umount+0x49/0xa0
[39095.647682]  [<c01cb7ee>] sys_oldumount+0x1e/0x20
[39095.647687]  [<c0103f7b>] sysenter_do_call+0x12/0x2f
[39095.647694]  [<c0370000>] ? default_device_exit+0x70/0xb0
[39095.647701]  =======================
[39095.647705] ---[ end trace ced61f96791ee7e0 ]---
[39095.694486] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET
driverbyte=DRIVER_OK,SUGGEST_OK
[39095.694498] end_request: I/O error, dev sda, sector 30937167
[39095.694506] __ratelimit: 20635 callbacks suppressed
[39095.694511] Buffer I/O error on device sda1, logical block 3867138
[39095.694515] lost page write due to I/O error on sda1
[39104.739603] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET
driverbyte=DRIVER_OK,SUGGEST_OK
[39104.739630] end_request: I/O error, dev sda, sector 63
[39104.739644] Buffer I/O error on device sda1, logical block 0
[39104.739656] Buffer I/O error on device sda1, logical block 1
[39104.739665] Buffer I/O error on device sda1, logical block 2
[39104.739675] Buffer I/O error on device sda1, logical block 3
[39104.739684] Buffer I/O error on device sda1, logical block 4
[39104.739693] Buffer I/O error on device sda1, logical block 5
[39104.739702] Buffer I/O error on device sda1, logical block 6
[39104.739712] Buffer I/O error on device sda1, logical block 7
[39104.739728] Buffer I/O error on device sda1, logical block 8
[39104.763059] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET
driverbyte=DRIVER_OK,SUGGEST_OK
[39104.763080] end_request: I/O error, dev sda, sector 63
[39104.767793] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET
driverbyte=DRIVER_OK,SUGGEST_OK
[39104.767814] end_request: I/O error, dev sda, sector 64
[39104.772512] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET
driverbyte=DRIVER_OK,SUGGEST_OK
[39104.772533] end_request: I/O error, dev sda, sector 65
[39111.210992] sd 0:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET
driverbyte=DRIVER_OK,SUGGEST_OK
[39111.211017] end_request: I/O error, dev sda, sector 65
[39111.216374] EXT3-fs: unable to read superblock

```

I'm really stuck; I can't see any reason why this shouldn't work for me, since Russel's Blog seems to have had no problems with it using almost identical hardware. 

If anyone can take the time to help me figure this out I'd really appreciate it.

---

### Post by taiji_jian on 2009-04-18
Update:

I can confirm that this is indeed Ubuntu-related. This morning I installed XP on the X40/CF card and it worked fine. Install went smoothly, and it has been chugging along with no complaints the rest of the day. I rebooted several times, and copied 15GB of stuff to it from my USB hard drive to stress test the CF card.

Any ideas?

---

### Post by rneches on 2009-04-26
That's weird. 

Many (most?) CF cards have defective DMA controllers (mine does). Evidently this is the difference between "gold" and regular CF cards; the "gold" ones aren't defective. 

Try disabling DMA. That may make it more reliable, but slower.

I'm running a stock Linus kernel, and the behavior seems to be to disable DMA if the controller doesn't behave itself. I think Windows does the same thing. Ubuntu may have patched their distribution kernel to be more tolerant of DMA naughtyness, since most hardware has some kind of harmless flakyness. Total speculation, though.

Russell

---

### Post by rneches on 2009-04-26
Did you follow this part of my instructions in the post?

/dev/hda {
        write_cache = on
        io32_support = 3
        dma = on
        lookahead = on
        interrupt_unmask = on
}

If so, try deleting that config file.

Russell

---

### Post by taiji_jian on 2009-04-26
Hi Russel,

Thanks a lot for taking time to look at my thread. I've been working on this as best I can on my own, and filed a bug about it on Launchpad:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/363786](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/363786)

I did try disabling DMA, both in hardware with my X40's BIOS, and in software with kernel boot parameters and hdparm. 

I also tried using the hdparm.conf you suggested. 

This appears to be a kernel bug. Over the weekend I installed Fedora 10 ran it with no problems for about 10 hours. 

I also tried using the 2.6.29 kernel from kernel.ubuntu.com. It *seemed* to work, but I couldn't really put the system under any kind of normal use load because the drivers for my graphics card are broken with that kernel. I also tried 2.6.30rc3 from kernel.ubunt.com and it DOES have the same problem. 

I'm getting kind of worried that even after Ubuntu moves to an upstream kernel version I still won't be able to do this.

---

### Post by bonestonne on 2009-04-26
hopefully this is a stupid question, but you remembered to disable a swap partition right?

---

### Post by taiji_jian on 2009-04-26
haha, yeah, no swap on my compact flash. I also mounted the root filesystem with noatime. I've also read about some people doing funky things with /var/log on a ramdisk, but I decided that might be more trouble than it's worth. Also, I actually use the logs.

---

