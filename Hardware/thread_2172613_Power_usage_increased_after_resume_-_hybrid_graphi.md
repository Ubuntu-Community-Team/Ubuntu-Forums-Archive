---
title: "Power usage increased after resume - hybrid graphics?"
date: 2013-09-05
forum: Hardware
---

### Post by benjamindaines2 on 2013-09-05
MacBook Pro 8,2 efi boot with intel i915.  When I boot up my power usage is around 11-12W, however, if I put the computer to sleep and wake it back up, power usage goes up to 24-27W.  I suspect that the ATI graphics chip is being powered on.  It does not show up in lspci or does the radeon module load.  VGA_Switcheroo isn't enabled and [COLOR=#333333][FONT=UbuntuRegular]/sys/kernel/debug/vgaswitcheroo/switch does not exist.  vga_switcheroo is compiled into my kernel.  I boot via grub-efi and my grub.cfg is attached.  Powertop shows pretty normal power usage as far as processes go.   Any ideas?  Thanks. 


```
[/FONT][/COLOR]menuentry 'Kubuntu GNU/Linux - Intel Graphics' --class kubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-a1130c29-9df2-434e-b910-3b76fd35b2b5' {recordfail
	load_video
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_gpt
	insmod btrfs
	set gfxpayload=keep
	outb 0x728 1
	outb 0x710 2
	outb 0x740 2
	outb 0x750 0	
	set root='hd0,gpt3'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt3 --hint-efi=hd0,gpt3 --hint-baremetal=ahci0,gpt3  a1130c29-9df2-434e-b910-3b76fd35b2b5
	else
	  search --no-floppy --fs-uuid --set=root a1130c29-9df2-434e-b910-3b76fd35b2b5
	fi
	linux	/@/boot/vmlinuz-3.10.9-031009-generic root=UUID=a1130c29-9df2-434e-b910-3b76fd35b2b5 ro rootflags=subvol=@   crashkernel=384M-2G:64M,2G-:128M quiet splash radeon.modeset=0 i915.modeset=1 i915.lvds_channel_mode=2 i915.lvds_use_ssc=0 i915.i915_enable_rc6=1 $vt_handoff
	initrd	/@/boot/initrd.img-3.10.9-031009-generic

}[COLOR=#333333][FONT=UbuntuRegular]
```
[/FONT][/COLOR]

---

### Post by benjamindaines2 on 2013-09-05
fixed 

[http://ubuntuforums.org/showthread.php?t=1695746&page=27&p=10695119#post10695119](http://ubuntuforums.org/showthread.php?t=1695746&page=27&p=10695119#post10695119)

---

