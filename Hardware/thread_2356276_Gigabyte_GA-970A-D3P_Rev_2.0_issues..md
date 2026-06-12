---
title: "Gigabyte GA-970A-D3P Rev 2.0 issues."
date: 2017-03-21
forum: Hardware
---

### Post by stchman on 2017-03-21
I have a system built on that motherboard with an AMD FX-6300, EVGA GTX 760 video card and a Samsung EVO 850 SSD.

I did the "iommu=soft" in my gub to get USB2 and USB3 working.
[https://ubuntuforums.org/showthread.php?t=2336077](https://ubuntuforums.org/showthread.php?t=2336077)

Everything appears to be working pretty good except that bootup is a little slow and shutdown is REALLY slow.  I had this system working great on Ubuntu 14.04LTS and upgraded to 16.04LTS.

The shutdown screen hangs for about 45 seconds for no apparent reason.

Anyone have any thoughts.

Thanks.

---

### Post by Kanehekili on 2017-03-23
What does "systemd-analyze blame" say? Or does it take so much time until you reach grub?

---

### Post by stchman on 2017-03-23
> **Kanehekili said:**
> What does "systemd-analyze blame" say? Or does it take so much time until you reach grub?
The shutdown is definitely way slower than the start up.  Is there a log file or something that tracks shutdown items?

Here is the output of system-analyze blame command.

```

          7.159s apt-daily.service
           540ms dev-sda5.device
           530ms upower.service
           462ms mnt-D_Drive.mount
           387ms networking.service
           290ms ModemManager.service
           204ms console-setup.service
           198ms accounts-daemon.service
           195ms lightdm.service
           179ms grub-common.service
           164ms systemd-logind.service
           156ms ninja.service
           153ms irqbalance.service
           145ms apport.service
           138ms ondemand.service
           124ms speech-dispatcher.service
           120ms lm-sensors.service
           117ms apparmor.service
           112ms iio-sensor-proxy.service
           108ms systemd-udev-trigger.service
           107ms systemd-user-sessions.service
           105ms rsyslog.service
           103ms media-storage.mount
            96ms NetworkManager.service
            90ms avahi-daemon.service
            88ms snapd.socket
            77ms thermald.service
            68ms keyboard-setup.service
            56ms gpu-manager.service
            48ms systemd-journald.service
            47ms udisks2.service
            39ms colord.service
            39ms plymouth-start.service
            33ms mnt-Windows.mount
            27ms ssh.service
            26ms systemd-tmpfiles-setup-dev.service
            25ms polkitd.service
            24ms systemd-udevd.service
            21ms systemd-modules-load.service
            18ms alsa-restore.service
            18ms binfmt-support.service
            17ms systemd-update-utmp.service
            17ms user@1000.service
            14ms snapd.autoimport.service
            12ms plymouth-read-write.service
            12ms sys-kernel-debug.mount
            12ms dev-hugepages.mount
            10ms dev-mqueue.mount
            10ms systemd-sysctl.service
             9ms systemd-timesyncd.service
             9ms pppd-dns.service
             9ms rtkit-daemon.service
             9ms systemd-tmpfiles-setup.service
             9ms systemd-journal-flush.service
             7ms kmod-static-nodes.service
             7ms resolvconf.service
             6ms dns-clean.service
             6ms proc-sys-fs-binfmt_misc.mount
             6ms ufw.service
             4ms systemd-random-seed.service
             4ms systemd-remount-fs.service
             4ms rc-local.service
             3ms setvtrgb.service
             3ms ureadahead-stop.service
             2ms systemd-update-utmp-runlevel.service
             2ms sys-fs-fuse-connections.mount
             1ms nvidia-persistenced.service
             1ms plymouth-quit-wait.service

```

---

### Post by Kanehekili on 2017-03-24
```
 7.159s apt-daily.service
```
doesn't look very good, but certainly is not main the issue and certainly irrelevant for shutdown. Since you wrote that you're using extra kernel switches to get USB running, this might be culprit. Usually some driver refuses to shut down or hangs while shutting down.
If you take the kernel command out of grub, does it shutdown faster? 
Two files might be worth looking at: 
*var/log/kern.log*
*/var/log/syslog*

Last not least, if you upgraded from 14.04 to 16.04 - it might be a good idea to do a clean install.

---

### Post by Kris_M on 2017-03-24
try this and see if it helps:
from my notes:
   [COLOR=#000000][SIZE=2]See  [/SIZE][/COLOR][https://ubuntuforums.org/showthread.php?t=1466577](https://ubuntuforums.org/showthread.php?t=1466577)[COLOR=#000000][SIZE=2]  post #9[/SIZE][/COLOR]
 [COLOR=#000000][SIZE=2]I added "nomodeset" to the UBUNTU item using Grub Customizer. I tested it first by doing a temp edit at the grub menu(highlight and press e.[/SIZE][/COLOR]
 [COLOR=#000000]&#8220;[/COLOR][COLOR=#000000][SIZE=2]linux    /boot/vmlinuz-4.4.0-59-generic root=UUID=14f8bc13-3090-4bbf-96c0-1f30ea3ec99a ro  quiet splash $vt_handoff nomodeset&#8221;[/SIZE][/COLOR]

---

### Post by Kanehekili on 2017-03-24
@Kris_M : Nomodeset is a severe kernel switch, as far as I know. I'd use it only as the last resort. See her for more infos:
[http://askubuntu.com/questions/207175/what-does-nomodeset-do](http://askubuntu.com/questions/207175/what-does-nomodeset-do)

---

### Post by Kris_M on 2017-03-24
> **Kanehekili said:**
> @Kris_M : Nomodeset is a severe kernel switch, as far as I know. I'd use it only as the last resort. See her for more infos:
[http://askubuntu.com/questions/207175/what-does-nomodeset-do](http://askubuntu.com/questions/207175/what-does-nomodeset-do)

what could it cost you other than maybe a few minutes of your time?  It has to do with Ubuntu's confusion with the display I'm using.  This way it doesn't think about it.  With it I get 4 sec shutdown and 10 sec boot. Before is was at least a minute on both sides.

But, whatever!

---

### Post by stchman on 2017-03-28
> **Kanehekili said:**
> ```
 7.159s apt-daily.service
```
doesn't look very good, but certainly is not main the issue and certainly irrelevant for shutdown. Since you wrote that you're using extra kernel switches to get USB running, this might be culprit. Usually some driver refuses to shut down or hangs while shutting down.
If you take the kernel command out of grub, does it shutdown faster? 
Two files might be worth looking at: 
*var/log/kern.log*
*/var/log/syslog*

Last not least, if you upgraded from 14.04 to 16.04 - it might be a good idea to do a clean install.

I did a clean install of 16.04.  I tried the upgrade route and it ran very slow.

---

