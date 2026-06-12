---
title: "lubuntu not booting without HDMI cable connected."
date: 2015-12-10
forum: Hardware
---

### Post by ajayraj-j on 2015-12-10
I am having lubuntu 14.04 LTS, which i installed on baytrail(x64) based PC. When i try to remove the HDMI to VGA connector boot fails, but when i connect HDMI, even if monitor is not connected, it will boot.
My idea is to use open ssh for remote access.

Windows 8.1 works absolutely fine without HDMI to VGA connector with this hardware, so ruled out any chances of hardware issue.

I tried various idea provided as mentioned for grub.cfg modification.
Below steps tried.

No luck with any of the links.
[http://ubuntuforums.org/showthread.php?t=1223504](http://ubuntuforums.org/showthread.php?t=1223504)
[http://askubuntu.com/questions/611991/ubuntu-14-04-with-unrecognized-monitor-or-without-monitor-boot-problem](http://askubuntu.com/questions/611991/ubuntu-14-04-with-unrecognized-monitor-or-without-monitor-boot-problem)
[http://askubuntu.com/questions/234081/how-to-boot-ubuntu-without-a-monitor-plugged-in](http://askubuntu.com/questions/234081/how-to-boot-ubuntu-without-a-monitor-plugged-in)

[http://www.ghacks.net/2010/11/28/configure-linux-to-boot-without-a-monitor/](http://www.ghacks.net/2010/11/28/configure-linux-to-boot-without-a-monitor/)

Tried modifying below mentioned also
[COLOR=#000000]GRUB_CMDLINE_LINUX_DEFAULT="quiet i915.modeset=0"

Using vesa driver as mentioned in one of the post   

[/COLOR]
But none them worked. Any idea how to solve the issue.

---

