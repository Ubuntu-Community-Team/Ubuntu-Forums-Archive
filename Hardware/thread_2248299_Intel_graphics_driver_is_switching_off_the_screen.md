---
title: "Intel graphics driver is switching off the screen"
date: 2014-10-13
forum: Hardware
---

### Post by Stormlord on 2014-10-13
Hi,


I am using Xubuntu 14.04 64-bit and Chrome as my main browser.  The computer is a Lenovo Thinkpad R61 laptop with an Intel 965GM video card inside.  Although everything was going fine when I was using Xubuntu 12.04, now, with 14.04, I am facing a problem that I am not able to find either a solution or a successful workaround for.


When I'm trying to watch a flash video, most of the time it works fine but randomly, the playback will pause right after it starts and 3-4 seconds later the screen will go black.  By saying black, I mean it's switched off, not simply blank.  It doesn't go back on unless I restart the laptop.  Everything else keeps working fine when this happens, and I can even hear the sound of the video playing.  I can press Ctrl-W and close the Chrome window or Ctrl-Alt-F1 and go to TTY1 mode, logon and turn the system off normally using the poweroff command.


Sometimes, when I see the video pausing like that and rush to close its window before the screen goes black, I can avoid it from happening.  If I attempt to play the same video again right after that, it plays fine and, most of the time, many more videos play just fine afterwards.  Till it happens again for some unknown reason so far and the story goes on...


The only app that causes this on a standard basis is glmark2 on a specific test it runs, which is called "[ideas] speed=duration:".  All previous tests are ok.  I don't know about the tests after this specific one of course.  I never get to test them.


Additionally, Chrome has caused this problem two more times and both are not flash video related.  It happened for the first time when I clicked on the "Download Chrome" link on the google page at the point where it usually brings up a separate white window where the file links are and the second time when I clicked on a messenger contact in hotmail to see what happens now they brought msn back.  Never got to find out eventually.  :D


The point is that I've clicked the "Download Chrome" link tens of times after that and it always worked fine.  This issue is completely random.


It happens with both the Intel drivers installed with the system and the latest one I installed from Intel using their installer 1.0.6.  I also tried switching AccelMethod from SNA (the default) to UXA which seemed to save others from this issue but in my case it didn't.


As you understand, this is quite serious and it has become even more serious after the latest Chrome update to version 38 since it happens more often.


This is the beginning of the log entries concerning this, in syslog:
Oct 13 03:41:39 Lenovo kernel: [41804.816060] [drm] stuck on render ring
Oct 13 03:41:39 Lenovo kernel: [41804.816069] [drm] GPU crash dump saved to /sys/class/drm/card0/error
Oct 13 03:41:39 Lenovo kernel: [41804.816071] [drm] GPU hangs can indicate a bug anywhere in the entire gfx stack, including userspace.
Oct 13 03:41:39 Lenovo kernel: [41804.816079] [drm] Please file a _new_ bug report on bugs.freedesktop.org against DRI -> DRM/Intel
Oct 13 03:41:39 Lenovo kernel: [41804.816080] [drm] drm/i915 developers can then reassign to the right component if it's not a kernel issue.
Oct 13 03:41:39 Lenovo kernel: [41804.816081] [drm] The gpu crash dump is required to analyze gpu hangs, so please always attach it.
Oct 13 03:41:39 Lenovo kernel: [41804.817061] [drm:i915_set_reset_status] *ERROR* render ring hung inside bo (0xb99e000 ctx 0) at 0xb99f804
Oct 13 03:41:40 Lenovo kernel: [41805.332085] [drm:i915_reset] *ERROR* Failed to reset chip.
Oct 13 03:41:40 Lenovo kernel: [41805.332791] ------------[ cut here ]------------
Oct 13 03:41:40 Lenovo kernel: [41805.332879] WARNING: CPU: 1 PID: 1834 at /build/buildd/linux-3.13.0/drivers/gpu/drm/i915/intel_display.c:922 assert_pll+0x68/0x70 [i915]()
Oct 13 03:41:40 Lenovo kernel: [41805.332884] PLL state assertion failure (expected on, current off)


The file (/sys/class/drm/card0/error) it's referring to, is empty.  Nothing is actually saved in there.






I'd appreciate it if you could help on this one.  Thanks a lot everyone.  ;)

Just happened again when I tried to access Chrome store.

---

### Post by Toz on 2014-10-14
Have a read through [this thread]("http://ubuntuforums.org/showthread.php?t=2208072") and see if setting UXA acceleration method helps you as well.

---

### Post by Stormlord on 2014-10-14
> **Stormlord said:**
> 

It happens with both the Intel drivers installed with the system and the latest one I installed from Intel using their installer 1.0.6.  I also tried switching AccelMethod from SNA (the default) to UXA which seemed to save others from this issue but in my case it didn't.



Already tried this.

---

### Post by oblador on 2014-11-05
I have the same problem here. 

How can it be fixed?

---

### Post by zob on 2014-11-07
I will follow this thread. I have the same problem with a laptop I'm setting up for my mum. It's a toshiba satellite A200 also with the same intel graphics GM965/GL960.
Today I've tried both version 14.04.1 32 bit and 12.04.5 32 bit (kernel 3.13.0-39) and it occurs in both. 14.04 was with unity 3d and 12.04 with unity 2d. So they were different setups. The common denominator being Chrome 38 and a visit to Chrome webstore, there it crashes.
I get the same errors as OP (PLL state assertion failure (expected on, current off)). I also get a segfault from chrome in my syslog. I think it is this bug: [https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/1371834](https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/1371834)
Please have a look and help out if you can.

In fact, in between the two also tried 14.10 64bit and here it didn't crash (should have kept it). However I then downgraded to 12.04 to get unity 2d because remote desktops over teamviewer and chrome remote desktop didn't seem to work well with unity 3d (didn't redraw screen on client).

I just tried with the original 3.2 kernel on 12.04. Same thing happens chrome 38.0.2125.111-1 crashes when visiting chrome webshop. I can browse chrome webshop in firefox without any problems.
Furthermore I just tested with google-chrome-beta 39.0.2171.52-1 and google-chrome-unstable 40.0.2209.0-1 - unfortunately they also crash.

Interestingly chromium-browser 37.0.2062.120 does NOT crash. And, as mentioned, neither does firefox 33.

Just tested with google-chrome-stable 37.0.2062.120-1 that I downloaded from here: [http://mirror.pcbeta.com/google/chrome/deb/pool/main/g/google-chrome-stable/](http://mirror.pcbeta.com/google/chrome/deb/pool/main/g/google-chrome-stable/)
That does not crash either. Can anyone confirm that this only happens in chrome >= 38?

---

### Post by oblador on 2014-11-11
> **zob said:**
> Just tested with google-chrome-stable 37.0.2062.120-1 that I downloaded from here: [http://mirror.pcbeta.com/google/chrome/deb/pool/main/g/google-chrome-stable/](http://mirror.pcbeta.com/google/chrome/deb/pool/main/g/google-chrome-stable/)
That does not crash either. Can anyone confirm that this only happens in chrome >= 38?

Well, it didn't happen before. So I guess the upgrades caused this regression.

Here is the output of sudo inxi -U && inxi -c0 -Fzxxtcm5 && grep -Ei 'warn|fail|error|critical' /var/log/syslog

```

Starting inxi self updater.
Currently running inxi version number: 2.2.16
Current version patch number: 00
Updating inxi in /usr/bin using svn server as download source...
Successfully updated to svn server version: 2.2.16
New svn server version patch number: 00
To run the new version, just start inxi again.
----------------------------------------
Starting download of man page file now.
Checking Man page download URL...
Man file download URL verified: [http://inxi.googlecode.com/svn/trunk/inxi.1.gz](http://inxi.googlecode.com/svn/trunk/inxi.1.gz)
Downloading Man page file now.
Download/install of man page successful. Check to make sure it works: man inxi
System: Host: lagreca-pc Kernel: 3.13.0-24-generic i686 (32 bit gcc: 4.8.2)
Desktop: Xfce 4.11.6 (Gtk 2.24.23) dm: mdm
Distro: Linux Mint 17 Qiana
Machine: System: Dell product: Inspiron 1525 Chassis: type: 8
Mobo: Dell model: 0D109D Bios: Dell v: A13 date: 06/27/2008
CPU: Dual core Intel Core2 Duo T7250 (-MCP-) cache: 2048 KB
flags: (lm nx pae sse sse2 sse3 ssse3 vmx) bmips: 7980
clock speeds: min/max: 800/2001 MHz 1: 2001 MHz 2: 800 MHz
Graphics: Card: Intel Mobile GM965/GL960 Integrated Graphics Controller (primary)
bus-ID: 00:02.0 chip-ID: 8086:2a02
Display Server: X.Org 1.15.1 driver: intel
Resolution: 1280x800@60.0hz
GLX Renderer: Mesa DRI Intel 965GM x86/MMX/SSE2
GLX Version: 2.1 Mesa 10.1.0 Direct Rendering: Yes
Audio: Card Intel 82801H (ICH8 Family) HD Audio Controller
driver: snd_hda_intel bus-ID: 00:1b.0 chip-ID: 8086:284b
Sound: Advanced Linux Sound Architecture v: k3.13.0-24-generic
Network: Card-1: Marvell 88E8040 PCI-E Fast Ethernet Controller
driver: sky2 v: 1.30 port: de00 bus-ID: 09:00.0 chip-ID: 11ab:4354
IF: eth0 state: down mac: <filter>
Card-2: Broadcom BCM4311 802.11a/b/g
driver: b43-pci-bridge bus-ID: 0b:00.0 chip-ID: 14e4:4312
IF: wlan0 state: up mac: <filter>
Drives: HDD Total Size: 120.0GB (72.9% used)
ID-1: /dev/sda model: SAMSUNG_HM121HI size: 120.0GB serial: S1S5J56Q703454 temp: 49C
Partition: ID-1: / size: 15G used: 8.6G (62%) fs: ext4 dev: /dev/sda1
ID-2: swap-1 size: 1.07GB used: 0.00GB (0%) fs: swap dev: /dev/sda2
RAID: System: supported: N/A
No RAID devices: /proc/mdstat, md_mod kernel module present
Unused Devices: none
Sensors: System Temperatures: cpu: 71.0C mobo: N/A
Fan Speeds (in rpm): cpu: N/A
Processes: CPU - % used - top 5 active
1: cpu: 7.2% command: depmod pid: 3560 mem: 6.31MB (0.3%)
2: cpu: 3.0% command: init pid: 1 mem: 2.50MB (0.1%)
3: cpu: 2.2% command: X pid: 1439 mem: 12.61MB (0.6%)
4: cpu: 1.7% command: xfdesktop pid: 2031 mem: 17.61MB (0.8%)
5: cpu: 1.0% command: xfce4-terminal pid: 2760 mem: 14.02MB (0.6%)
Memory - MB / % used - top 5 active
1: mem: 23.94MB (1.1%) command: mintUpdate.py (started by: python) pid: 2070 cpu: 0.9%
2: mem: 17.61MB (0.8%) command: xfdesktop pid: 2031 cpu: 1.7%
3: mem: 15.33MB (0.7%) command: nm-applet pid: 2059 cpu: 0.6%
4: mem: 14.02MB (0.6%) command: xfce4-terminal pid: 2760 cpu: 1.0%
5: mem: 13.65MB (0.6%) command: xfce4-panel pid: 2026 cpu: 0.6%
Info: Processes: 163 Uptime: 1 min Memory: 189.7/2006.5MB
Init: Upstart v: 1.12.1 runlevel: 2 default: 2 Gcc sys: 4.8.2
Client: Shell (bash 4.3.111 running in xfce4-terminal) inxi: 2.2.16

```

I guess the problem is here:
```

Nov 11 10:06:00 lagreca-pc kernel: [37530.988049] [drm] GPU crash dump saved to /sys/class/drm/card0/error
Nov 11 10:06:00 lagreca-pc kernel: [37530.989066] [drm:i915_set_reset_status] *ERROR* render ring hung inside bo (0xec97000 ctx 0) at 0xec97ed4
Nov 11 10:06:00 lagreca-pc kernel: [37531.496227] [drm:i915_reset] *ERROR* Failed to reset chip.
Nov 11 10:06:05 lagreca-pc kernel: [37536.318406] Watchdog[8096]: segfault at 0 ip b0148ac7 sp ad1f6be0 error 6 in libcontent.so[af97e000+1180000]
Nov 11 10:06:10 lagreca-pc kernel: [37541.124202] [drm:i915_gem_wait_for_error] *ERROR* Timed out waiting for the gpu reset to complete
Nov 11 10:06:10 lagreca-pc kernel: [37541.218969] WARNING: CPU: 1 PID: 2066 at /build/buildd/linux-3.13.0/drivers/gpu/drm/i915/intel_display.c:922 assert_pll+0x73/0x80 [i915]()
Nov 11 10:06:10 lagreca-pc kernel: [37541.218972] PLL state assertion failure (expected on, current off)
Nov 11 10:06:10 lagreca-pc kernel: [37541.219091] [<c10567ee>] warn_slowpath_common+0x7e/0xa0
Nov 11 10:06:10 lagreca-pc kernel: [37541.219142] [<c1056843>] warn_slowpath_fmt+0x33/0x40
Nov 11 10:06:10 lagreca-pc kernel: [37541.219490] WARNING: CPU: 1 PID: 2066 at /build/buildd/linux-3.13.0/drivers/gpu/drm/i915/intel_display.c:922 assert_pll+0x73/0x80 [i915]()
Nov 11 10:06:10 lagreca-pc kernel: [37541.219492] PLL state assertion failure (expected on, current off)
Nov 11 10:06:10 lagreca-pc kernel: [37541.219600] [<c10567ee>] warn_slowpath_common+0x7e/0xa0
Nov 11 10:06:10 lagreca-pc kernel: [37541.219651] [<c1056843>] warn_slowpath_fmt+0x33/0x40
Nov 11 10:06:10 lagreca-pc kernel: [37541.276135] WARNING: CPU: 0 PID: 2066 at /build/buildd/linux-3.13.0/drivers/gpu/drm/i915/intel_display.c:1127 assert_pipe+0xd4/0xe0 [i915]()
Nov 11 10:06:10 lagreca-pc kernel: [37541.276138] pipe B assertion failure (expected on, current off)

```

This is serious. I hope someone pays the attention to our problem.

Unfortunately I'll need to install windows again. Back to the dual booting. 
This struggle with linux video drivers will go on forever. There's always a regression waiting at the next update.

Hi, Folks,

I've found this bug report which portrays the same problem I'm facing:

[https://bugs.freedesktop.org/show_bug.cgi?id=80568](https://bugs.freedesktop.org/show_bug.cgi?id=80568)

I guess someone else is also experiencing this situation.

---

### Post by tadpole1954 on 2014-11-20
I have the exact same problem.  I found a solution on another thread....   Please type **chrome://settings** in Chrome's address bar and hit **enter**.

Then go to the bottom of that page and click on **Show Advanced Settings**.

Then go to nearly the bottom of the new page and see if "Use hardware  acceleration when available" is ticked. If it is, try the Web Store  after you untick that setting and restart Chrome.

---

### Post by oblador on 2014-11-24
> **tadpole1954 said:**
> I have the exact same problem.  I found a solution on another thread....   Please type **chrome://settings** in Chrome's address bar and hit **enter**.

Then go to the bottom of that page and click on **Show Advanced Settings**.

Then go to nearly the bottom of the new page and see if "Use hardware  acceleration when available" is ticked. If it is, try the Web Store  after you untick that setting and restart Chrome.

Tadpole, that's not enough because we'd like to use chrome or chromium with hardware acceleration.

Instead of disabling hardware acceleration, you could try this possible workaround for the related bug:

"always_flush_cache=true always_flush_batch=true /usr/bin/google-chrome-stable"

More information here:
[https://bugs.freedesktop.org/show_bug.cgi?id=80568](https://bugs.freedesktop.org/show_bug.cgi?id=80568)

Thanks.

---

### Post by gsj5 on 2015-03-11
Hi,


I had similar issue as described above.  I'm happy to report that my problem has been fixed by applying following update per
[https://bugs.freedesktop.org/show_bug.cgi?id=80568#c99](https://bugs.freedesktop.org/show_bug.cgi?id=80568#c99) on the latest kernel release.   YMMV.


sudo apt-add-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get dist-upgrade 
sudo reboot

---

