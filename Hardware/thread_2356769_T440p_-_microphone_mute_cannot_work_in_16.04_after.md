---
title: "T440p - microphone mute cannot work in 16.04 after enable HWE kernel and X"
date: 2017-03-26
forum: Hardware
---

### Post by alfred7 on 2017-03-26
I start Ubuntu 14.10 on this T440p(Feb, 2015), and step by step upgrade to 15.04, 15.10, and finally LTS 16.04.

Before HWE: (kernel 4.4)
MIC_MUTE(Fn+F4) works under X, only the led of it does not light properly(Don't know why, because my work mate who is using same Laptop and Ubuntu 16.04 4.4 kernel does not have this issue); But 4.4 kernel has a very [annoying bug, the text console display will freeze after some time using;]("http://www.linuxquestions.org/questions/linux-kernel-70/linux-4-4-x-kernel-freezing-tty-issue-4175573093/")

After enable HWE: (kernel 4.8)
Text console freeze problem is fixed; But MIC_MUTE under X does not work; acpi_listen under X does NOT show anything for Fn+F4;
Under text console(Ctrl+Alt+F6 for my example), acpi_listen shows for Fn+F4:[INDENT][FONT=courier new]$ acpi_listen[/FONT][/INDENT]
[INDENT][FONT=courier new]button/f20 F20 00000080 00000000 K[/FONT][/INDENT]

Below command can toggle MIC_MUTE correctly (on both kernel)[INDENT]amixer set -c 1 Capture toggle
[/INDENT]

Do you think this maybe a bug for xserver or I mis-config something of xserver? Since my system on 4.4 kernel does not work properly too.
Oh, I have to mention, because I hate the T440p's clickpad(no physical buttons), I replace it with a newer module's touchpad which has physical buttons.
Maybe this confuse kernel/xserver to determine correct model of my laptop?

[FONT=courier new]$ dpkg -l \*hwe\*[/FONT]
[FONT=courier new]Desired=Unknown/Install/Remove/Purge/Hold[/FONT]
[FONT=courier new]| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend[/FONT]
[FONT=courier new]|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)[/FONT]
[FONT=courier new]||/ Name                                 Version                 Architecture            Description[/FONT]
[FONT=courier new]+++-====================================-=======================-=======================-==============================================================================[/FONT]
[FONT=courier new]ii  linux-generic-hwe-16.04              4.8.0.44.16             amd64                   Complete Generic Linux kernel and headers[/FONT]
[FONT=courier new]ii  linux-headers-generic-hwe-16.04      4.8.0.44.16             amd64                   Generic Linux kernel headers[/FONT]
[FONT=courier new]ii  linux-hwe-tools-4.8.0-41             4.8.0-41.44~16.04.1     amd64                   Linux kernel version specific tools for version 4.8.0-41[/FONT]
[FONT=courier new]ii  linux-image-generic-hwe-16.04        4.8.0.44.16             amd64                   Generic Linux kernel image[/FONT]
[FONT=courier new]ii  linux-signed-generic-hwe-16.04       4.8.0.44.16             amd64                   Complete Signed Generic Linux kernel and headers[/FONT]
[FONT=courier new]ii  linux-signed-image-generic-hwe-16.04 4.8.0.44.16             amd64                   Signed Generic Linux kernel image[/FONT]
[FONT=courier new]ii  linux-tools-generic-hwe-16.04        4.8.0.41.12             amd64                   Generic Linux kernel tools[/FONT]
[FONT=courier new]un  xorg-renamed-package-hwe-16.04       <none>                  <none>                  (no description available)[/FONT]
[FONT=courier new]ii  xserver-xorg-core-hwe-16.04          2:1.18.4-1ubuntu6.1~16. amd64                   Xorg X server - core server[/FONT]
[FONT=courier new]ii  xserver-xorg-hwe-16.04               1:7.7+13ubuntu4~16.04.2 amd64                   X.Org X server[/FONT]
[FONT=courier new]un  xserver-xorg-input-all-hwe-16.04     <none>                  <none>                  (no description available)[/FONT]
[FONT=courier new]ii  xserver-xorg-input-libinput-hwe-16.0 0.19.0-1ubuntu0.1~16.04 amd64                   X.Org X server -- libinput input driver[/FONT]
[FONT=courier new]un  xserver-xorg-input-vmmouse-hwe-16.04 <none>                  <none>                  (no description available)[/FONT]
[FONT=courier new]un  xserver-xorg-input-wacom-hwe-16.04   <none>                  <none>                  (no description available)[/FONT]
[FONT=courier new]ii  xserver-xorg-legacy-hwe-16.04        2:1.18.4-1ubuntu6.1~16. amd64                   setuid root Xorg server wrapper[/FONT]
[FONT=courier new]ii  xserver-xorg-video-all-hwe-16.04     1:7.7+13ubuntu4~16.04.2 amd64                   X.Org X server -- output driver metapackage[/FONT]
[FONT=courier new]ii  xserver-xorg-video-amdgpu-hwe-16.04  1.1.2-1~16.04.1         amd64                   X.Org X server -- AMDGPU display driver[/FONT]
[FONT=courier new]ii  xserver-xorg-video-ati-hwe-16.04     1:7.7.1-1~16.04.1       amd64                   X.Org X server -- AMD/ATI display driver wrapper[/FONT]
[FONT=courier new]ii  xserver-xorg-video-fbdev-hwe-16.04   1:0.4.4-1build5~16.04.1 amd64                   X.Org X server -- fbdev display driver[/FONT]
[FONT=courier new]ii  xserver-xorg-video-intel-hwe-16.04   2:2.99.917+git20160706- amd64                   X.Org X server -- Intel i8xx, i9xx display driver[/FONT]
[FONT=courier new]un  xserver-xorg-video-mach64-hwe-16.04  <none>                  <none>                  (no description available)[/FONT]
[FONT=courier new]ii  xserver-xorg-video-nouveau-hwe-16.04 1:1.0.12-2~16.04.1      amd64                   X.Org X server -- Nouveau display driver[/FONT]
[FONT=courier new]ii  xserver-xorg-video-qxl-hwe-16.04     0.1.4-3ubuntu3~16.04.1  amd64                   X.Org X server -- QXL display driver[/FONT]
[FONT=courier new]un  xserver-xorg-video-r128-hwe-16.04    <none>                  <none>                  (no description available)[/FONT]
[FONT=courier new]ii  xserver-xorg-video-radeon-hwe-16.04  1:7.7.1-1~16.04.1       amd64                   X.Org X server -- AMD/ATI Radeon display driver[/FONT]
[FONT=courier new]ii  xserver-xorg-video-vesa-hwe-16.04    1:2.3.4-1build2~16.04.1 amd64                   X.Org X server -- VESA display driver[/FONT]
[FONT=courier new]ii  xserver-xorg-video-vmware-hwe-16.04  1:13.1.0-2ubuntu3~16.04 amd64                   X.Org X server -- VMware display driver[/FONT]

---

