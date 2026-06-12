---
title: "Gigabyte GA-970A-D3P Rev 2.0 issues."
date: 2018-06-14
forum: Hardware
---

### Post by neoricalex on 2018-06-14
Hi there how re you?

I have the very same issue that @stchman at [this post]("https://ubuntuforums.org/showthread.php?t=2356276") (closed). 
Bootup is really slow.

I have a 18.04 clean install with IOMMU at BIOS enabled.

Someone have a clue? 

```
neo@desktop:~$ systemd-analyze blame 
         20.785s plymouth-quit-wait.service
          6.494s NetworkManager-wait-online.service
           716ms fwupd.service
           379ms dev-mapper-ubuntu\x2d\x2dvg\x2droot.device
           299ms NetworkManager.service
           286ms apparmor.service
           281ms systemd-logind.service
           265ms udisks2.service
           252ms plymouth-start.service
           230ms snap-core-4486.mount
           218ms networkd-dispatcher.service
           206ms dev-loop0.device
           201ms snap-gnome\x2dsystem\x2dmonitor-45.mount
           183ms dev-loop1.device
           180ms systemd-resolved.service
           178ms systemd-timesyncd.service
           173ms snap-gnome\x2dcalculator-154.mount
           171ms dev-loop2.device
           158ms snap-gnome\x2dcharacters-69.mount
           157ms snapd.service
           155ms snap-gnome\x2dlogs-25.mount
           137ms ModemManager.service
           134ms snap-gnome\x2dcalculator-178.mount
           130ms systemd-udev-trigger.service
           129ms snap-gnome\x2dlogs-37.mount
           127ms dev-loop3.device
           124ms snap-gnome\x2dsystem\x2dmonitor-36.mount
           113ms dev-loop8.device
           110ms accounts-daemon.service
           102ms dev-loop9.device
           101ms keyboard-setup.service
            92ms snap-core-4650.mount
            89ms dev-loop6.device
            84ms dev-loop10.device
            81ms systemd-journal-flush.service
            79ms dev-loop4.device
            79ms lvm2-pvscan@8:1.service
            75ms dev-loop5.device
            72ms motd-news.service
            69ms snap-gnome\x2d3\x2d26\x2d1604-64.mount
            68ms upower.service
            67ms dev-loop7.device
            66ms bolt.service
            63ms apport.service
            58ms systemd-journald.service
            56ms wpa_supplicant.service
            53ms polkit.service
            52ms dev-loop11.device
            52ms avahi-daemon.service
            52ms gpu-manager.service
            51ms grub-common.service
            51ms packagekit.service
            46ms thermald.service
            46ms user@1000.service
            43ms snap-gnome\x2dcharacters-101.mount
            42ms rsyslog.service
            42ms snap-gnome\x2d3\x2d26\x2d1604-59.mount
            41ms dns-clean.service
            37ms console-setup.service
            35ms lvm2-monitor.service
            31ms networking.service
            30ms speech-dispatcher.service
            29ms plymouth-read-write.service
            28ms systemd-tmpfiles-setup.service
            27ms systemd-udevd.service
            20ms alsa-restore.service
            19ms systemd-modules-load.service
            19ms systemd-tmpfiles-setup-dev.service
            17ms gdm.service
            16ms systemd-tmpfiles-clean.service
            14ms colord.service
            13ms systemd-sysctl.service
            12ms snapd.seeded.service
            12ms ureadahead-stop.service
             9ms sys-kernel-debug.mount
             9ms kerneloops.service
             8ms dev-hugepages.mount
             8ms pppd-dns.service
             8ms systemd-update-utmp-runlevel.service
             7ms systemd-update-utmp.service
             7ms systemd-remount-fs.service
             7ms kmod-static-nodes.service
             6ms systemd-random-seed.service
             6ms ufw.service
             6ms setvtrgb.service
             6ms dev-mapper-ubuntu\x2d\x2dvg\x2dswap_1.swap
             5ms dev-mqueue.mount
             5ms sys-fs-fuse-connections.mount
             5ms blk-availability.service
             3ms systemd-user-sessions.service
             3ms rtkit-daemon.service
             2ms sys-kernel-config.mount
           745us snapd.socket
lines 71-93/93 (END)
            14ms colord.service
            13ms systemd-sysctl.service
            12ms snapd.seeded.service
            12ms ureadahead-stop.service
             9ms sys-kernel-debug.mount
             9ms kerneloops.service
             8ms dev-hugepages.mount
             8ms pppd-dns.service
             8ms systemd-update-utmp-runlevel.service
             7ms systemd-update-utmp.service
             7ms systemd-remount-fs.service
             7ms kmod-static-nodes.service
             6ms systemd-random-seed.service
             6ms ufw.service
             6ms setvtrgb.service
             6ms dev-mapper-ubuntu\x2d\x2dvg\x2dswap_1.swap
             5ms dev-mqueue.mount
             5ms sys-fs-fuse-connections.mount
             5ms blk-availability.service
             3ms systemd-user-sessions.service
             3ms rtkit-daemon.service
             2ms sys-kernel-config.mount
           745us snapd.socket
```

---

### Post by oldfred on 2018-06-17
What video card?
What boot parameters are you now using?

Several more links.
        GIGABYTE GA-970A-DS3 motherboard not working with 64 bit kernel - IOMMU GRUB_CMDLINE_LINUX="iommu=soft"
[http://ubuntuforums.org/showthread.php?t=2111223&page=5](http://ubuntuforums.org/showthread.php?t=2111223&page=5)
[http://ubuntuforums.org/showthread.php?t=2292025](http://ubuntuforums.org/showthread.php?t=2292025)
[http://ubuntuforums.org/showthread.php?t=2242023](http://ubuntuforums.org/showthread.php?t=2242023)
[SOLVED] GA-970A-DS3P revision 1 no usb 3.0
[http://ubuntuforums.org/showthread.php?t=2188370](http://ubuntuforums.org/showthread.php?t=2188370)

---

### Post by neoricalex on 2018-07-06
Hi Oldfred thanks for the feedback, and sorry for the delay in my follow-up.

ive searched with a "journalctl -b" command and i have picked that red line:

```
radeon 0000:01:00.0: Invalid PCI ROM header signature: expecting 0xaa55, got 0xffff
```

My Video Card is a very standard radeon 6000 (only need Full HD):

```
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Cedar [Radeon HD 5000/6000/7350/8350 Series]
```

Thanks for the Help !

---

### Post by oldfred on 2018-07-06
I do not know AMD, but many posts in google & they say that is not the issue.

What kernel?
Many issues with -24 and slow boot. 
If you choose the older kernel in grub menu does it boot ok?

       failure to boot with linux-image-4.15.0-24-generic 
[https://bugs.launchpad.net/ubuntu/+bug/1779827](https://bugs.launchpad.net/ubuntu/+bug/1779827)

---

### Post by neoricalex on 2018-07-10
> **oldfred said:**
> 
Many issues with -24 and slow boot. 

Yes true. Up to 10 minutes to boot. ( Snappy Daemon Issue ).
With the old Kernel boot ok.

I will wait for a update to see. If nothing happens maybe a custom build of kernel solve that.

Thanks oldfred have a nice day!

---

