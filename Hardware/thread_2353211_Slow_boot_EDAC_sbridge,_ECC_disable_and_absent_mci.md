---
title: "Slow boot: EDAC sbridge, ECC disable and absent mci handler"
date: 2017-02-19
forum: Hardware
---

### Post by Drone4four on 2017-02-19
My machine takes approximately 2.5 minutes for Ubuntu 16.04 to get from Grub to LDM.
My Ubuntu 16.04 is installed on an SSD and I have a fast Core i7 CPU. Plymouth is pretty ugly too.

Attached is an image of where it temporarily hangs for a long time during boot. It might be hard to see what the message it.  Here it is verbatim. 

```

[    9.558623] EDAC sbridge: ECC is disabled. Aborting
[    9.558724] EDAC sbridge: Couldn't find mci handler

```

[Here](http://pastebin.com/RmN6TTej) is my dmesg in full.

One member of Ask Ubuntu addresses [someone else experiencing a similar issue]("http://askubuntu.com/questions/784700/ubuntu-16-04-boot-error") by saying:

> 
This error isn't really a error at all, it is just a warning. If you want it to go away, enable ECC in your BIOS. I don't have this though and never have seen it so it may have side effects. It is a option for your RAM.


Changing BIOS settings can be a delicate procedure.  If I flip the switch in my BIOS and ECC isn’t an option for my RAM, do I run the risk of destroying my hardware?

---

### Post by DuckHook on 2017-02-20
You likely already know this, but for the lurkers out there:

ECC is a special type of RAM that contains an extra parity bit in addition to the normal bits that make up every byte. If parity checking is activated on the MOBO, then every time memory is accessed, its contents are checksummed against the parity bit to see if a stray cosmic ray hasn't flipped one of the bits. This is a known RAM phenomenon and happens more frequently than people realize. ECC memory is used in mission-critical industries—like banking, the ISS or nuclear missile control systems—where absolute accuracy and dependability are non-negotiable. If you don't have ECC memory installed in your system, you shouldn't be turning this on. I doubt that doing so will damage anything—I imagine most MOBOs are smart enough to figure things out—but it is not physically possible to run ECC on non-ECC RAM, so it is pointless at best and potential trouble at worst, so why do it?

The messages that you are seeing are not errors but alerts. The kernel generates them on every ECC-capable system that doesn't have ECC memory installed and they are nothing to worry about. They show up in my dmesg as well and I have boot times measured in seconds. Your system is probably waiting for something else entirely and the ECC/mci alerts were just the last things to output to your TTY before the real culprit slows everything down.

Please do:```
systemd-analyze blame
```…which will show what boot processes are hogging the most time in descending order. The culprit(s) will often be stuff like waiting for a network connection, a wrong disk UUID for swap, etc. Note that with systemd, boot processes can by multithreaded so your boot times may be faster than the sum of the services.

Off topic, but you may wish to change your sig. It describes a machine that bears no resemblance to the one described in the body of your post, which will confuse the forum search functions and scare the children.

---

### Post by Drone4four on 2017-02-20
> **DuckHook said:**
> The messages that you are seeing are not errors but alerts. The kernel generates them on every ECC-capable system that doesn't have ECC memory installed and they are nothing to worry about. They show up in my dmesg as well and I have boot times measured in seconds. Your system is probably waiting for something else entirely and the ECC/mci alerts were just the last things to output to your TTY before the real culprit slows everything down.

This is really interesting.  I didn't realize dmesg doesn't project the entire accurate picture of Linux at boot.  

> Please do:```
systemd-analyze blame
```&#8230;which will show what boot processes are hogging the most time in descending order. The culprit(s) will often be stuff like waiting for a network connection, a wrong disk UUID for swap, etc. Note that with systemd, boot processes can by multithreaded so your boot times may be faster than the sum of the services.
Here is systemd-analyze blame:

```

          2min 47.484s apt-daily.service
          7.322s NetworkManager-wait-online.service
          5.110s udev-configure-printer@-devices-pci0000:00-0000:00:1c.7-0000:08:00.0-usb5-5\x2d4.service
          1.091s snapd.refresh.service
           882ms dev-sda1.device
           540ms lvm2-monitor.service
           389ms systemd-fsck@dev-disk-by\x2duuid-817cc471\x2d4e6a\x2d4e31\x2d8822\x2d49671a751e7c.service
           199ms apparmor.service
           192ms php7.0-fpm.service
           160ms sftpcloudfs.service
           140ms timidity.service
           140ms upower.service
           125ms ModemManager.service
           117ms networking.service
           115ms accounts-daemon.service
           112ms NetworkManager.service
            97ms systemd-logind.service
            83ms systemd-udev-trigger.service
            82ms avahi-daemon.service
            78ms thermald.service
            72ms irqbalance.service
            68ms udisks2.service
            66ms systemd-udevd.service
            65ms snap-hello\x2dworld-27.mount
            65ms apport.service
            63ms gpu-manager.service
            60ms console-setup.service
            60ms teamviewerd.service
            57ms gdomap.service
            56ms virtualbox.service
            52ms speech-dispatcher.service
            50ms ondemand.service
            49ms keyboard-setup.service
            48ms systemd-modules-load.service
            47ms systemd-journald.service
            45ms lightdm.service
            40ms binfmt-support.service
            38ms rsyslog.service
            36ms systemd-tmpfiles-setup-dev.service
            33ms colord.service
            31ms home.mount
            30ms systemd-timesyncd.service
            25ms grub-common.service
            24ms packagekit.service
            22ms ssh.service
            21ms glances.service
            20ms user@1000.service
            19ms iodined.service
            18ms geoclue.service
            16ms polkitd.service
            16ms snap-core-1240.mount
            15ms snap-core-1079.mount
            14ms alsa-restore.service
            14ms snap-core-1222.mount
            14ms hddtemp.service
            13ms snapd.autoimport.service
            12ms plymouth-start.service
            11ms plymouth-read-write.service
            11ms systemd-tmpfiles-setup.service
            10ms systemd-update-utmp.service
            10ms lm-sensors.service
             9ms dev-hugepages.mount
             9ms sys-kernel-debug.mount
             8ms systemd-tmpfiles-clean.service
             8ms systemd-remount-fs.service
             8ms systemd-journal-flush.service
             8ms wpa_supplicant.service
             8ms pppd-dns.service
             6ms dev-mqueue.mount
             6ms systemd-random-seed.service
             6ms kmod-static-nodes.service
             5ms systemd-user-sessions.service
             4ms ufw.service
             4ms dns-clean.service
             3ms resolvconf.service
             3ms systemd-sysctl.service
             3ms proc-sys-fs-binfmt_misc.mount
             3ms rc-local.service
             2ms systemd-update-utmp-runlevel.service
             2ms rtkit-daemon.service
             2ms ureadahead-stop.service
             1ms sys-fs-fuse-connections.mount
             1ms setvtrgb.service
             1ms nvidia-persistenced.service
             1ms openvpn.service
             1ms plymouth-quit-wait.service
             1ms dev-loop0.device
             1ms dev-loop4.device
           982us dev-loop3.device
           918us dev-loop1.device
           490us snapd.socket
```
Apt looks like the problem. What can you make of this data? 

Check this out too: ```
$ systemd-analyze 
Startup finished in 8.934s (kernel) + 10.154s (userspace) = 19.088s
```
It's worth noting that my 2 minute boot time only happens some times.  For example, when X crashes, when I have no choice but to press reset button on my tower, THEN it takes 2+ mins to boot.  But when I can shut down the O/S properly, then it doesn't take 2 minutes. It takes 10 or so seconds, which could be why systemd-analyze says, 19 seconds there.


With respect to my sig, you said:
>  Off topic, but you may wish to change your sig. It describes a machine that bears no resemblance to the one described in the body of your post, which will confuse the forum search functions and scare the children.

My sig is rather unique. The hardware is so old and obsolete that not a single soul on our beloved internetz would (30 years after it being on the market) ever search for.  It is such an antique that I highly doubt that this sig would confuse search engines.  But if it is indeed a problem, I can take it down.  I hesitate to do so b/c I think it's really funny as a throw back to the 1980s.

---

### Post by DuckHook on 2017-02-20
> **Drone4four said:**
> …I didn't realize dmesg doesn't project the entire accurate picture of Linux at boot.Actually, there is no one report that will give you the total picture. Nor would you likely want one, because there are so many thousands of things that occur in such a short time at boot that you would be buried under an avalanche of data. All reporting functions have to draw the line somewhere, and they end up giving you summaries which combine a string of processes into one line.> Here is systemd-analyze blame:
```

          2min 47.484s apt-daily.service
…
```
Apt looks like the problem. What can you make of this data?Again, apt may not be the real problem. It may be behaving as it should, and it's what you state next that is the real cause…
> It's worth noting that my 2 minute boot time only happens some times.  For example, when X crashes, when I have no choice but to press reset button on my tower, THEN it takes 2+ mins to boot.  But when I can shut down the O/S properly, then it doesn't take 2 minutes. It takes 10 or so seconds, which could be why systemd-analyze says, 19 seconds…My money would be on your dirty shutdown. It probably leaves all sorts of dangling processes and even broken ones that must be cleaned up or timed out by the system the next time you boot up. X crashes are themselves alarming. If I were you, I would be very concerned about them and want to get to the bottom of why they are happening.

The next time X crashes, don't hit the hard reset button before trying a few other things first:

[LIST=1]
[*]Try shutting down X gracefully with <Ctrl>+<Alt>+<Backspace>. You may have to first reconfigure your OS to re-enable this key combo, which recent distros have turned off by default. Instructions here: [http://askubuntu.com/questions/367983/how-do-i-enable-ctrl-alt-backspace-to-kill-the-x-server](http://askubuntu.com/questions/367983/how-do-i-enable-ctrl-alt-backspace-to-kill-the-x-server)
[*]If that doesn't work, try switching to a TTY console with <Ctrl>+<Alt>+<F1> and do:```
reboot
```…or:```
poweroff
```Use *sudo* if you need to.
[*]If that still doesn't work, it's time to try the sysrq methods which will pass system calls to the kernel at a very basic level.
[list]First, try <Alt>+<Sysrq>+<k>. Again, this combo is disabled in a default install. Instructions to re-enable are here: [http://askubuntu.com/questions/526691/alt-prtsc-k-not-working](http://askubuntu.com/questions/526691/alt-prtsc-k-not-working)
[*]Lastly, if all else fails, do REISUB as explained here: [https://ubuntuforums.org/showthread.php?t=617349](https://ubuntuforums.org/showthread.php?t=617349)[/list]
[*]Only when all else fails should you hit the physical reset button, which is pretty much the nuclear option when it comes to the OS.
[/LIST]
I'm 90% sure that your problem arises from the dirty shutdowns. The long apt process is probably only another pseudo-indicator that your system is struggling to recover from them. It should be noted that dirty shutdowns are a bigger issue than merely the lengthy boot times the next time around. Your real concern should be corrupted data from unflushed disk caches or partially-written files.
> …My sig is rather unique. The hardware is so old and obsolete that not a single soul on our beloved internetz would (30 years after it being on the market) ever search for.  It is such an antique that I highly doubt that this sig would confuse search engines.  But if it is indeed a problem, I can take it down.  I hesitate to do so b/c I think it's really funny as a throw back to the 1980s.Please don't change your sig on account of what I said. I was just pointing out the incongruity. It's charming and unique… but it does stale-date people like you and me though! :p

---

### Post by Drone4four on 2017-02-20
> **DuckHook said:**
> The next time X crashes, don't hit the hard reset button before trying a few other things first:
[LIST=1]
[*]Try shutting down X gracefully with <Ctrl>+<Alt>+<Backspace>. You may have to first reconfigure your OS to re-enable this key combo, which recent distros have turned off by default. Instructions here: [http://askubuntu.com/questions/367983/how-do-i-enable-ctrl-alt-backspace-to-kill-the-x-server](http://askubuntu.com/questions/367983/how-do-i-enable-ctrl-alt-backspace-to-kill-the-x-server)
[*]If that doesn't work, try switching to a TTY console with <Ctrl>+<Alt>+<F1> and do:```
reboot
```…or:```
poweroff
```Use *sudo* if you need to.
[*]If that still doesn't work, it's time to try the sysrq methods which will pass system calls to the kernel at a very basic level.
[list]First, try <Alt>+<Sysrq>+<k>. Again, this combo is disabled in a default install. Instructions to re-enable are here: [http://askubuntu.com/questions/526691/alt-prtsc-k-not-working](http://askubuntu.com/questions/526691/alt-prtsc-k-not-working)
[*]Lastly, if all else fails, do REISUB as explained here: [https://ubuntuforums.org/showthread.php?t=617349](https://ubuntuforums.org/showthread.php?t=617349)[/list]
[*]Only when all else fails should you hit the physical reset button, which is pretty much the nuclear option when it comes to the OS.
[/LIST]
I'm 90% sure that your problem arises from the dirty shutdowns. The long apt process is probably only another pseudo-indicator that your system is struggling to recover from them. It should be noted that dirty shutdowns are a bigger issue than merely the lengthy boot times the next time around. Your real concern should be corrupted data from unflushed disk caches or partially-written files.

Aye, thanks for your advice, **DuckHook**.  I prolly should have also indicated that I did try the TTY techniqe like I usually do to load top in sudo mode to kill X .  I wasn't able to switch VTs at all.  My system was completely locked.  I recall 10 years ago Ctrl+A+Backspace was enabled by default.  I'll re enable it and use it when necessary.  I also hadn't heard of <Alt>+<Sysrq>+<k> or REISUB.  I'll look into it and play around with them. Thanks again, **DuckHook**. =D

---

### Post by DuckHook on 2017-02-21
> **Drone4four said:**
> …My system was completely locked.  I recall 10 years ago Ctrl+A+Backspace was enabled by default.  I'll re enable it and use it when necessary…If your system is completely locked, it is unlikely that <Ctrl>+<Alt>+<Backspace> will unlock it. <Alt>+<Sysrq>+<k> or REISUB would seem to be the only option. I suggest starting a separate thread dealing with your system lockup. The best solution would be to get a stable X environment on your gear so that these measures become just a bad memory.

Good Luck and Happy Ubuntu-ing!

---

