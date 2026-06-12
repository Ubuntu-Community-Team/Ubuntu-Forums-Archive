---
title: "Issues with the Lenovo Ideapad U430p"
date: 2013-10-05
forum: Hardware
---

### Post by rimez on 2013-10-05
I recently had to buy a new laptop quickly as my old one died shortly before an important business trip. I got lured into the build quality of the U430p which I simply assumed everything would work (or be made to work through tweaks). Unfortunately, there are some rather big issues which I cannot seem to resolve fully.

Manufacturer: Lenovo
Model: Ideapad U430p (not to be confused with the u430 touch)
RAM: 8gb
Processor: Intel i5 
GPU: Switchable - Nvidia Geforce GT 730M + Intel 
Standard OS: Win8 (completely removed)
Installed OS: Ubuntu 13.10 (current;y running on 3.12 mainline kernel)

Key Issues:
[LIST]
[*][COLOR=#808080]Poor WiFi reception with frequent drops - This is my biggest pain so far. In order to even get this wlan to work I had to use the 3.11 kernel or newer (that's why I'm using a beta version of Ubuntu on a production system instead of LTS).[/COLOR]
[LIST]
[*][COLOR=#808080]Today I've installed the 3.12rc3 mainline kernel provided by Ubuntu. It seems to have helped in that I haven't experienced any drops so far - maybe it's resolved? Too early to tell though. **EDIT: just dropped while writing this post :( However, it was able to reconnect by itself before it could not be recovered withought a restart**[/COLOR] **UPDATE: Just use a kernel newer than 3.11. Ubutu 14.04 is using 3.13 at the moment which works well. ** 
[*]I'm getting *loads* of messages in syslog for the card - not sure if it's usuefull or not 
[/LIST]
  
[*][COLOR=#696969]When I am in the office, I often use Virtualbox in dual-screen mode. Unfortunately with this laptop, whenever I try this, the X sessions freezes. Sometimes I'm still able to drop to a console (ctrl-alt f1) but sometimes I'm not. I suspect the Haswell gpu is the issue. Not sure though.[/COLOR]
[LIST]
[*][COLOR=#696969]Running the virtual without a second monitor attached works without issue.[/COLOR] 
[*][COLOR=#696969]UPDATE: FOrgot to mention, I also get these freezes in dualscreen when I try to display a libreoffice impress presentation (typing f5)... it's not just about VB (but VB is important to me). [/COLOR]**UPDATE:** The issue disappeared. Probably some unknown update fixed the issue. 
[/LIST]
 
[*][COLOR=#696969]I cannot get the Nvidia card working at all. Ubuntu only recognizes the Intel chipset (no option to install the nvidia drivers)[/COLOR]
[LIST]
[*][COLOR=#696969]Card *is* visible in lspci[/COLOR] - **UPDATE:** It's working now (using Ubuntu 14.04 at the moment). Just go into the software updates and install the official Nvidia blob + bumblebee. 
[/LIST]
   
[/LIST]

I would appreciate any help in getting these issues resolved. Anyone have experience with either this device or similar issues? 

I have to say, I've been using Linux since 1998 (exclusively since 2009) and this is the first time I have ever had such issues with one of my computers :( I'm really at a loss here. 

**lspci -nn: **
```
~$ lspci -nn00:00.0 Host bridge [0600]: Intel Corporation Haswell-ULT DRAM Controller [8086:0a04] (rev 09)
00:02.0 VGA compatible controller [0300]: Intel Corporation Haswell-ULT Integrated Graphics Controller [8086:0a16] (rev 09)
00:03.0 Audio device [0403]: Intel Corporation Device [8086:0a0c] (rev 09)
00:14.0 USB controller [0c03]: Intel Corporation Lynx Point-LP USB xHCI HC [8086:9c31] (rev 04)
00:16.0 Communication controller [0780]: Intel Corporation Lynx Point-LP HECI #0 [8086:9c3a] (rev 04)
00:1b.0 Audio device [0403]: Intel Corporation Lynx Point-LP HD Audio Controller [8086:9c20] (rev 04)
00:1c.0 PCI bridge [0604]: Intel Corporation Lynx Point-LP PCI Express Root Port 1 [8086:9c10] (rev e4)
00:1c.2 PCI bridge [0604]: Intel Corporation Lynx Point-LP PCI Express Root Port 3 [8086:9c14] (rev e4)
00:1c.3 PCI bridge [0604]: Intel Corporation Lynx Point-LP PCI Express Root Port 4 [8086:9c16] (rev e4)
00:1c.4 PCI bridge [0604]: Intel Corporation Lynx Point-LP PCI Express Root Port 5 [8086:9c18] (rev e4)
00:1d.0 USB controller [0c03]: Intel Corporation Lynx Point-LP USB EHCI #1 [8086:9c26] (rev 04)
00:1f.0 ISA bridge [0601]: Intel Corporation Lynx Point-LP LPC Controller [8086:9c43] (rev 04)
00:1f.2 SATA controller [0106]: Intel Corporation Lynx Point-LP SATA Controller 1 [AHCI mode] [8086:9c03] (rev 04)
00:1f.3 SMBus [0c05]: Intel Corporation Lynx Point-LP SMBus Controller [8086:9c22] (rev 04)
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
02:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b2] (rev 73)
09:00.0 3D controller [0302]: NVIDIA Corporation GK208M [GeForce GT 730M] [10de:1290] (rev a1)

```

Some error in syslog - no idea what it means though:( 
```
 Secure-U430p kernel: [  567.708327] ------------[ cut here ]------------Oct  5 17:41:40 Secure-U430p kernel: [  567.708336] WARNING: CPU: 2 PID: 35 at /home/apw/COD/linux/net/mac80211/sta_info.c:839 __sta_info_destroy+0x25b/0x390 [mac80211]()
Oct  5 17:41:40 Secure-U430p kernel: [  567.708338] Modules linked in: pci_stub vboxpci(OF) vboxnetadp(OF) vboxnetflt(OF) vboxdrv(OF) uvcvideo x86_pkg_temp_thermal videobuf2_vmalloc coretemp videobuf2_memops videobuf2_core videodev kvm_intel arc4 kvm joydev iwlmvm mac80211 btusb psmouse microcode serio_raw iwlwifi cfg80211 bnep rfcomm bluetooth snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_page_alloc parport_pc snd_seq_midi snd_seq_midi_event ppdev snd_rawmidi snd_seq snd_seq_device snd_timer ideapad_laptop sparse_keymap snd mei_me mei lpc_ich soundcore intel_smartconnect mac_hid binfmt_misc nls_iso8859_1 ext2 lp parport dm_crypt hid_generic usbhid hid crct10dif_pclmul crc32_pclmul ghash_clmulni_intel nouveau aesni_intel aes_x86_64 lrw gf128mul glue_helper ablk_helper i915 cryptd mxm_wmi ttm i2c_algo_bit drm_kms_helper ahci drm libahci r8169 mii wmi video
Oct  5 17:41:40 Secure-U430p kernel: [  567.708391] CPU: 2 PID: 35 Comm: kworker/2:0 Tainted: GF       W IO 3.12.0-031200rc3-generic #201309291835
Oct  5 17:41:40 Secure-U430p kernel: [  567.708393] Hardware name: LENOVO 20269           /Cherry 4A       , BIOS 7CCN13WW 06/11/2013
Oct  5 17:41:40 Secure-U430p kernel: [  567.708397] Workqueue: events iwl_mvm_reprobe_wk [iwlmvm]
Oct  5 17:41:40 Secure-U430p kernel: [  567.708399]  0000000000000347 ffff880253b5d748 ffffffff81747b27 0000000000000007
Oct  5 17:41:40 Secure-U430p kernel: [  567.708403]  0000000000000000 ffff880253b5d788 ffffffff8106759c ffff880250109634
Oct  5 17:41:40 Secure-U430p kernel: [  567.708407]  ffff880250109000 ffff880035a24600 ffff880035a26840 0000000000000000
Oct  5 17:41:40 Secure-U430p kernel: [  567.708410] Call Trace:
Oct  5 17:41:40 Secure-U430p kernel: [  567.708415]  [<ffffffff81747b27>] dump_stack+0x46/0x58
Oct  5 17:41:40 Secure-U430p kernel: [  567.708418]  [<ffffffff8106759c>] warn_slowpath_common+0x8c/0xc0
Oct  5 17:41:40 Secure-U430p kernel: [  567.708422]  [<ffffffff810675ea>] warn_slowpath_null+0x1a/0x20
Oct  5 17:41:40 Secure-U430p kernel: [  567.708431]  [<ffffffffa05cc32b>] __sta_info_destroy+0x25b/0x390 [mac80211]
Oct  5 17:41:40 Secure-U430p kernel: [  567.708444]  [<ffffffffa05ed5b8>] ? ieee80211_xmit+0xa8/0x110 [mac80211]
Oct  5 17:41:40 Secure-U430p kernel: [  567.708454]  [<ffffffffa05cc615>] sta_info_flush_defer+0x95/0xc0 [mac80211]
Oct  5 17:41:40 Secure-U430p kernel: [  567.708469]  [<ffffffffa0609652>] ieee80211_set_disassoc+0xd2/0x3d0 [mac80211]
Oct  5 17:41:40 Secure-U430p kernel: [  567.708483]  [<ffffffffa060d22c>] ieee80211_mgd_deauth+0x21c/0x260 [mac80211]
Oct  5 17:41:40 Secure-U430p kernel: [  567.708487]  [<ffffffff8109b076>] ? ttwu_do_activate.constprop.84+0x66/0x70
Oct  5 17:41:40 Secure-U430p kernel: [  567.708499]  [<ffffffffa05df548>] ieee80211_deauth+0x18/0x20 [mac80211]
Oct  5 17:41:40 Secure-U430p kernel: [  567.708511]  [<ffffffffa050ca72>] cfg80211_mlme_deauth+0xa2/0x160 [cfg80211]
Oct  5 17:41:40 Secure-U430p kernel: [  567.708522]  [<ffffffffa050cd5b>] cfg80211_mlme_down+0x6b/0x90 [cfg80211]
Oct  5 17:41:40 Secure-U430p kernel: [  567.708534]  [<ffffffffa0510e04>] cfg80211_disconnect+0x1d4/0x1e0 [cfg80211]
Oct  5 17:41:40 Secure-U430p kernel: [  567.708545]  [<ffffffffa04f2c50>] ? __cfg80211_stop_sched_scan+0x20/0x180 [cfg80211]
Oct  5 17:41:40 Secure-U430p kernel: [  567.708549]  [<ffffffff8109fd7d>] ? sched_clock_cpu+0xbd/0x110
Oct  5 17:41:40 Secure-U430p kernel: [  567.708558]  [<ffffffffa04e9be4>] cfg80211_leave+0xe4/0x100 [cfg80211]
Oct  5 17:41:40 Secure-U430p kernel: [  567.708566]  [<ffffffffa04e9cfb>] cfg80211_netdev_notifier_call+0xfb/0x680 [cfg80211]
Oct  5 17:41:40 Secure-U430p kernel: [  567.708571]  [<ffffffff817527c5>] ? __schedule+0x3d5/0x730
Oct  5 17:41:40 Secure-U430p kernel: [  567.708575]  [<ffffffff816af8af>] ? inetdev_event+0x2f/0x310
Oct  5 17:41:40 Secure-U430p kernel: [  567.708579]  [<ffffffff817598ed>] notifier_call_chain+0x4d/0x70
Oct  5 17:41:40 Secure-U430p kernel: [  567.708583]  [<ffffffff81091dd6>] raw_notifier_call_chain+0x16/0x20
Oct  5 17:41:40 Secure-U430p kernel: [  567.708586]  [<ffffffff8163ef80>] call_netdevice_notifiers_info+0x40/0x70
Oct  5 17:41:40 Secure-U430p kernel: [  567.708589]  [<ffffffff8163efc6>] call_netdevice_notifiers+0x16/0x20
Oct  5 17:41:40 Secure-U430p kernel: [  567.708592]  [<ffffffff8163f00d>] __dev_close_many+0x3d/0xd0
Oct  5 17:41:40 Secure-U430p kernel: [  567.708595]  [<ffffffff8163f1bb>] dev_close_many+0x8b/0x100
Oct  5 17:41:40 Secure-U430p kernel: [  567.708599]  [<ffffffff81640d98>] rollback_registered_many+0xd8/0x240
Oct  5 17:41:40 Secure-U430p kernel: [  567.708602]  [<ffffffff81640f1b>] unregister_netdevice_many+0x1b/0x70
Oct  5 17:41:40 Secure-U430p kernel: [  567.708613]  [<ffffffffa05dc03b>] ieee80211_remove_interfaces+0x12b/0x1f0 [mac80211]
Oct  5 17:41:40 Secure-U430p kernel: [  567.708622]  [<ffffffffa05c611f>] ieee80211_unregister_hw+0x5f/0x120 [mac80211]
Oct  5 17:41:40 Secure-U430p kernel: [  567.708628]  [<ffffffffa0692e42>] iwl_op_mode_mvm_stop+0x32/0xd0 [iwlmvm]
Oct  5 17:41:40 Secure-U430p kernel: [  567.708634]  [<ffffffffa0598076>] iwl_drv_stop+0x36/0xc0 [iwlwifi]
Oct  5 17:41:40 Secure-U430p kernel: [  567.708641]  [<ffffffffa059ba93>] iwl_pci_remove+0x33/0x50 [iwlwifi]
Oct  5 17:41:40 Secure-U430p kernel: [  567.708646]  [<ffffffff813bc226>] pci_device_remove+0x46/0xc0
Oct  5 17:41:40 Secure-U430p kernel: [  567.708649]  [<ffffffff814a4bdf>] __device_release_driver+0x7f/0xf0
Oct  5 17:41:40 Secure-U430p kernel: [  567.708652]  [<ffffffff814a4c7c>] device_release_driver+0x2c/0x40
Oct  5 17:41:40 Secure-U430p kernel: [  567.708656]  [<ffffffff814a3894>] device_reprobe+0x34/0x60
Oct  5 17:41:40 Secure-U430p kernel: [  567.708662]  [<ffffffffa06928d5>] iwl_mvm_reprobe_wk+0x25/0x60 [iwlmvm]
Oct  5 17:41:40 Secure-U430p kernel: [  567.708665]  [<ffffffff81083d0f>] process_one_work+0x17f/0x4d0
Oct  5 17:41:40 Secure-U430p kernel: [  567.708668]  [<ffffffff81084f4b>] worker_thread+0x11b/0x3d0
Oct  5 17:41:40 Secure-U430p kernel: [  567.708671]  [<ffffffff81084e30>] ? manage_workers.isra.20+0x1b0/0x1b0
Oct  5 17:41:40 Secure-U430p kernel: [  567.708675]  [<ffffffff8108c0d0>] kthread+0xc0/0xd0
Oct  5 17:41:40 Secure-U430p kernel: [  567.708679]  [<ffffffff8108c010>] ? flush_kthread_worker+0xb0/0xb0
Oct  5 17:41:40 Secure-U430p kernel: [  567.708682]  [<ffffffff8175e1fc>] ret_from_fork+0x7c/0xb0
Oct  5 17:41:40 Secure-U430p kernel: [  567.708686]  [<ffffffff8108c010>] ? flush_kthread_worker+0xb0/0xb0
Oct  5 17:41:40 Secure-U430p kernel: [  567.708688] ---[ end trace 3445d4053ce917b7 ]---
Oct  5 17:41:40 Secure-U430p kernel: [  567.708760] iwlwifi 0000:02:00.0: failed to update MAC 0c:8b:fd:31:5f:4c
Oct  5 17:41:40 Secure-U430p kernel: [  567.708764] iwlwifi 0000:02:00.0: failed to update power mode
Oct  5 17:41:40 Secure-U430p kernel: [  567.708767] iwlwifi 0000:02:00.0: failed to update MAC 0c:8b:fd:31:5f:4c
Oct  5 17:41:40 Secure-U430p kernel: [  567.708769] ------------[ cut here ]------------
```

Output for X -version
```
~$ X -version

X.Org X Server 1.14.3
Release Date: 2013-09-12
X Protocol Version 11, Revision 0
Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
Current Operating System: Linux Secure-U430p 3.12.0-031200rc3-generic #201309291835 SMP Sun Sep 29 22:37:02 UTC 2013 x86_64
Kernel command line: BOOT_IMAGE=/vmlinuz-3.12.0-031200rc3-generic root=/dev/mapper/ubuntu--vg-root ro acpi_osi=Linux splash plymouth:debug=1 quiet
Build Date: 03 October 2013  03:20:13PM
xorg-server 2:1.14.3-3ubuntu1 (For technical support please see http://www.ubuntu.com/support) 

```

---

### Post by mortemdei on 2013-10-06
I have the same machine and the same problems. The wifi does work though, you just have to reboot the system. I also haven't been able to make the nvidia card work.

---

### Post by martian1530 on 2013-10-23
Hi, I have the same laptop model and apparently the same issues.
The wifi problem is quite annoying (dmesg outputs the same errors as in the first post). After restart, everything works flawlessly, even on N-mode.
The graphics card is indeed visible in lspci, but working with it seems impossible. I tried to install bumblebee with no success. When I try to start an application using the Nvidia card, I get an error message:

```
[   22.274008] [ERROR]Cannot access secondary GPU - error: Could not load GPU driver
[   22.274042] [ERROR]Aborting because fallback start is disabled.


```

I tried a lot of possible fixes but nothing seems to help.
I guess the wifi problems will be fixed with new kernel releases (the wifi card model is quite new in this laptop), but the 3D card problems would like some resolving.
Anyone got any ideas?

---

### Post by mechevar21 on 2013-10-23
I was able to get wifi working by reinstalling the broadcom drivers for my Lenovo G780
```
sudo apt-get install --reinstall bcmwl-kernel-source
```

To get bumblebee working so that I could use my graphics card with a command like
```
optirun firefox
```
I had to install** bumblebee-nvidia** along with bumblebee

The one thing that is killing me with the Intel graphics is that I get a blank and responseless screen on logout or if I use ctrl+alt+f1 to go to a terminal prompt.  Any ideas?

---

### Post by mechevar21 on 2013-10-23
Ah, answered my own question.  Needed to edit grub to make everything work on my Lenovo G780
```
sudo gedit /etc/default/grub
```
Make sure the options were set like this
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="acpi_osi=Linux acpi_backlight=vendor"
```
Finally update everything
```
sudo update-grub
```

The brightness was really low on reboot, but editing the brightness via the control panel (not hardware keys) got things permanently set.

---

### Post by martian1530 on 2013-10-24
Thanks mechevar21 but let't keep this thread for the Lenovo Ideapad u430p.
So your answer is kind of irrelevant. The wifi card in my ideapad is Intel, not Broadcom.
Thanks for the suggestion to install the bumblebee-nvidia package as well. I did, but it didn't solve the problem.

---

### Post by mortemdei on 2013-10-25
Has anyone been able to install nvidia-prime? I always get an error when I try to install it.

---

### Post by noah-azpiri on 2013-11-13
Hi, 

Any news on this?
Has anyone tried 3.12 kernel with nvidia 331 drivers and bumbleebe?

---

### Post by mortemdei on 2013-11-14
I did but didn't work :(, maybe somebody could file a bug report for the kernel so that they fix the issue of linux not seeing the card for the next release?

---

### Post by jpbarroso on 2013-12-04
Hi! I've lenovo u430p and all working, inclusive NVIDIA 730M discrete card.
I've installed:
Ubuntu 13.10
New kernel 3.12: ([http://news.softpedia.com/news/How-to-Install-Linux-Kerrnel-3-12-in-Ubuntu-13-10-397013.shtml](http://news.softpedia.com/news/How-to-Install-Linux-Kerrnel-3-12-in-Ubuntu-13-10-397013.shtml))
(With this kernel WIFI runs much better)
NVIDIA with bumblebee: Install latest nvidia-drivers (331.20) and bumblebee with this ppa:
sudo add-apt-repository ppa:xorg-edgers/ppa [http://www.ubuntuupdates.org/ppa/xorg-edgers?dist=saucy](http://www.ubuntuupdates.org/ppa/xorg-edgers?dist=saucy)

I've installed: nvidia-331 and bumblebee (and all dependencies) 

My unique issue with this laptop is the touchpad, i've configured a lot of times, high, low sensibility... perhaps are personal notes but I think it's erratic and have strange behaviours.

---

### Post by noah-azpiri on 2013-12-04
Thanks jbparroso!
Awesome news! :-D I wil try this ASAP

---

### Post by mortemdei on 2013-12-04
It didn't work for me, would you mind posting a step by step of what you did for getting it to work?

---

### Post by Troublegum on 2013-12-09
I am just reporting that the nvidia card works fine with archlinux, linux kernel 3.12.3, bumblebee 3.2.1 and the proprietary nvidia drivers 331.20.
I just installed the necessary packages as outlined in the archlinux wiki. No need to edit any config files.
```
$ uname -a
Linux altair 3.12.3-1-ARCH #1 SMP PREEMPT Wed Dec 4 21:45:42 CET 2013 x86_64 GNU/Linux
```

```
$ lspci
00:00.0 Host bridge: Intel Corporation Haswell-ULT DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 09)
00:03.0 Audio device: Intel Corporation Device 0a0c (rev 09)
00:14.0 USB controller: Intel Corporation Lynx Point-LP USB xHCI HC (rev 04)
00:16.0 Communication controller: Intel Corporation Lynx Point-LP HECI #0 (rev 04)
00:1b.0 Audio device: Intel Corporation Lynx Point-LP HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 1 (rev e4)
00:1c.2 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 3 (rev e4)
00:1c.3 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 4 (rev e4)
00:1c.4 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 5 (rev e4)
00:1d.0 USB controller: Intel Corporation Lynx Point-LP USB EHCI #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Lynx Point-LP LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Lynx Point-LP SATA Controller 1 [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Lynx Point-LP SMBus Controller (rev 04)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller (rev 10)
02:00.0 Network controller: Intel Corporation Wireless 7260 (rev 73)
09:00.0 3D controller: NVIDIA Corporation GK208M [GeForce GT 730M] (rev ff)
```

```
$ glxinfo | grep OpenGL
OpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) Haswell Mobile 
OpenGL core profile version string: 3.1 (Core Profile) Mesa 9.2.4
OpenGL core profile shading language version string: 1.40
OpenGL core profile context flags: (none)
OpenGL core profile extensions:
OpenGL version string: 3.0 Mesa 9.2.4
OpenGL shading language version string: 1.30
OpenGL context flags: (none)
OpenGL extensions:
```


```
$ optirun glxinfo | grep OpenGL
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce GT 730M/PCIe/SSE2
OpenGL core profile version string: 4.3.0 NVIDIA 331.20
OpenGL core profile shading language version string: 4.30 NVIDIA via Cg compiler
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
OpenGL version string: 4.4.0 NVIDIA 331.20
OpenGL shading language version string: 4.40 NVIDIA via Cg compiler
OpenGL context flags: (none)
OpenGL profile mask: (none)
OpenGL extensions:
```

```
$ cat /etc/bumblebee/bumblebee.conf
# Configuration file for Bumblebee. Values should **not** be put between quotes


## Server options. Any change made in this section will need a server restart
# to take effect.
[bumblebeed]
# The secondary Xorg server DISPLAY number
VirtualDisplay=:8
# Should the unused Xorg server be kept running? Set this to true if waiting
# for X to be ready is too long and don't need power management at all.
KeepUnusedXServer=false
# The name of the Bumbleblee server group name (GID name)
ServerGroup=bumblebee
# Card power state at exit. Set to false if the card shoud be ON when Bumblebee
# server exits.
TurnCardOffAtExit=false
# The default behavior of '-f' option on optirun. If set to "true", '-f' will
# be ignored.
NoEcoModeOverride=false
# The Driver used by Bumblebee server. If this value is not set (or empty),
# auto-detection is performed. The available drivers are nvidia and nouveau
# (See also the driver-specific sections below)
Driver=
# Directory with a dummy config file to pass as a -configdir to secondary X
XorgConfDir=/etc/bumblebee/xorg.conf.d


## Client options. Will take effect on the next optirun executed.
[optirun]
# Acceleration/ rendering bridge, possible values are auto, virtualgl and
# primus.
Bridge=auto
# The method used for VirtualGL to transport frames between X servers.
# Possible values are proxy, jpeg, rgb, xv and yuv.
VGLTransport=proxy
# List of paths which are searched for the primus libGL.so.1 when using
# the primus bridge
PrimusLibraryPath=/usr/lib/primus:/usr/lib32/primus
# Should the program run under optirun even if Bumblebee server or nvidia card
# is not available?
AllowFallbackToIGC=false




# Driver-specific settings are grouped under [driver-NAME]. The sections are
# parsed if the Driver setting in [bumblebeed] is set to NAME (or if auto-
# detection resolves to NAME).
# PMMethod: method to use for saving power by disabling the nvidia card, valid
# values are: auto - automatically detect which PM method to use
#         bbswitch - new in BB 3, recommended if available
#       switcheroo - vga_switcheroo method, use at your own risk
#             none - disable PM completely
# https://github.com/Bumblebee-Project/Bumblebee/wiki/Comparison-of-PM-methods


## Section with nvidia driver specific options, only parsed if Driver=nvidia
[driver-nvidia]
# Module name to load, defaults to Driver if empty or unset
KernelDriver=nvidia
PMMethod=auto
# colon-separated path to the nvidia libraries
LibraryPath=/usr/lib/nvidia:/usr/lib32/nvidia
# comma-separated path of the directory containing nvidia_drv.so and the
# default Xorg modules path
XorgModulePath=/usr/lib/nvidia/xorg/,/usr/lib/xorg/modules
XorgConfFile=/etc/bumblebee/xorg.conf.nvidia


## Section with nouveau driver specific options, only parsed if Driver=nouveau
[driver-nouveau]
KernelDriver=nouveau
PMMethod=auto
XorgConfFile=/etc/bumblebee/xorg.conf.nouveau
```


```
$ cat /etc/bumblebee/xorg.conf.nvidia
Section "ServerLayout"
    Identifier  "Layout0"
    Option      "AutoAddDevices" "false"
    Option      "AutoAddGPU" "false"
EndSection


Section "Device"
    Identifier  "DiscreteNvidia"
    Driver      "nvidia"
    VendorName  "NVIDIA Corporation"


#   If the X server does not automatically detect your VGA device,
#   you can manually set it here.
#   To get the BusID prop, run `lspci | egrep 'VGA|3D'` and input the data
#   as you see in the commented example.
#   This Setting may be needed in some platforms with more than one
#   nvidia card, which may confuse the proprietary driver (e.g.,
#   trying to take ownership of the wrong device). Also needed on Ubuntu 13.04.
#   BusID "PCI:01:00:0"


#   Setting ProbeAllGpus to false prevents the new proprietary driver
#   instance spawned to try to control the integrated graphics card,
#   which is already being managed outside bumblebee.
#   This option doesn't hurt and it is required on platforms running
#   more than one nvidia graphics card with the proprietary driver.
#   (E.g. Macbook Pro pre-2010 with nVidia 9400M + 9600M GT).
#   If this option is not set, the new Xorg may blacken the screen and
#   render it unusable (unless you have some way to run killall Xorg).
    Option "ProbeAllGpus" "false"


    Option "NoLogo" "true"
    Option "UseEDID" "false"
    Option "UseDisplayDevice" "none"
EndSection
```


Hope this is helpful for some of you.
[ATTACH=CONFIG]248469[/ATTACH]

---

### Post by jpbarroso on 2013-12-10
[COLOR=#000000]mortemdei: step by step:
Ubuntu 13.10 x64 with latest updates[/COLOR]
[COLOR=#000000]New kernel 3.12:
[/COLOR][COLOR=#008080][FONT=Verdana]wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.12-saucy/linux-image-3.12.0-031200-generic_3.12.0-031200.201311031935_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.12-saucy/linux-image-3.12.0-031200-generic_3.12.0-031200.201311031935_amd64.deb)[/FONT][/COLOR]
[COLOR=#008080][FONT=Verdana]wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.12-saucy/linux-headers-3.12.0-031200-generic_3.12.0-031200.201311031935_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.12-saucy/linux-headers-3.12.0-031200-generic_3.12.0-031200.201311031935_amd64.deb)
[/FONT][/COLOR][COLOR=#008080][FONT=Verdana]sudo dpkg -i linux-image-3.12.0-031200-generic_3.12.0-031200.201311031935_amd64.deb[/FONT][/COLOR]
[COLOR=#008080][FONT=Verdana]sudo dpkg -i linux-headers-3.12.0-031200-generic_3.12.0-031200.201311031935_amd64.deb[/FONT][/COLOR]

[COLOR=#000000]NVIDIA, drivers 331.20 and bumblebee:[/COLOR]
sudo add-apt-repository ppa: xorg-edgers/ppa 
sudo apt-get update
sudo apt-get install nvidia-331
sudo apt-get install bumblebee

between steps I installed a lot of packages, but I dont think they are necessary, mainly restricted-extras and cinnamon as desktop:

sudo apt-get install ubuntu-restricted-extras
sudo add-apt-repository ppa:gwendal-lebihan-dev/cinnamon-stable
sudo apt-get update
sudo apt-get install cinnamon

---

### Post by mortemdei on 2013-12-11
This is weird. I just followed those steps with kernels 3.12, 3.12.3, and 3.13 rc3 and after reboot I get a blackscreen with a huge X as a mouse pointer. This is sad :/

---

### Post by mortemdei on 2013-12-11
It worked installing "bumblebee-nvidia" too, thanks for your help!

---

### Post by odwyer on 2013-12-14
I have the Lenovo U430p no touch laptop.  Installing the latest kernel worked for and fixed the wireless issue.


wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.12-saucy/linux-headers-3.12.0-031200-generic_3.12.0-031200.201311031935_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.12-saucy/linux-headers-3.12.0-031200-generic_3.12.0-031200.201311031935_amd64.deb)

wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.12-saucy/linux-headers-3.12.0-031200_3.12.0-031200.201311031935_all.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.12-saucy/linux-headers-3.12.0-031200_3.12.0-031200.201311031935_all.deb)

wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.12-saucy/linux-image-3.12.0-031200-generic_3.12.0-031200.201311031935_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.12-saucy/linux-image-3.12.0-031200-generic_3.12.0-031200.201311031935_amd64.deb)

sudo dpkg -i linux-headers-3.12.0-*.deb linux-image-3.12.0-*.deb


My wireless had been dropping every 5 minutes since I bought this laptop a few months ago but now it's working without any problems :)

---

### Post by rimez on 2014-04-17
Hi all, it's been a long time since I started this thread... until yesterday when I saw the posts about BB working I had pretty much given up on it. Thanks to you I have BB installed and it does seem to recognize (and use) the Nvidia card when I use the optirun <app> command. 

Thanks a million for this.

---

### Post by martian1530 on 2014-04-18
Hi guys,

With the recent release of Ubuntu 14.04 it looks like our problems with this laptop are gone, aren't they?

The wireless problem was fixed by kernel update, nvidia drivers are now included in the "Additional drivers" menu (and you can even switch between integrated GPU and Nvidia in the "Nvidia X server settings" application).

One thing bothers me though... as was mentioned before: The touchpad DOES feel a little weird. When you move the pointer in a diagonal way across the display really really slowly, you can literally see how it jumps horizontally and vertically. It's not a really smooth movement at all. On a Full HD display it looks kind of weird.

Does anyone have any idea how to tweak the touchpad driver?

Cheers :)
Martin

---

### Post by nonoob on 2014-06-01
Would you please tell the kernel version of yours now? My kernel is "3.13.0-27-generic" and I upgrade from 13.10. I was a bumblebee user before but now it seems that the performance is rather disappointing and there's no "Additional drivers".

---

### Post by nonoob on 2014-06-01
In my case, lspci cannot find any Nvidia controller and there's no "additional drivers" on Ubuntu14.04(upgraded from 13.10 and the kernel is 3.13.0-27-generic). Would you please tell the details a bit more? Many thanks!

For touchpad, I also have this issue and I presently have to turn off it:-(

> **martian1530 said:**
> Hi guys,

With the recent release of Ubuntu 14.04 it looks like our problems with this laptop are gone, aren't they?

The wireless problem was fixed by kernel update, nvidia drivers are now included in the "Additional drivers" menu (and you can even switch between integrated GPU and Nvidia in the "Nvidia X server settings" application).

One thing bothers me though... as was mentioned before: The touchpad DOES feel a little weird. When you move the pointer in a diagonal way across the display really really slowly, you can literally see how it jumps horizontally and vertically. It's not a really smooth movement at all. On a Full HD display it looks kind of weird.

Does anyone have any idea how to tweak the touchpad driver?

Cheers :)
Martin

---

### Post by martian1530 on 2014-06-16
The "Additional drivers" menu can be found in System settings -> Software & Updates -> Additional drivers tab. I'm using NVIDIA binary driver, version nvidia-331.
You can even install prime-indicator and use it to quickly switch between integrated and high-performance cards on the go.

[FONT=courier new]sudo add-apt-repository ppa:nilarimogard/webupd8[/FONT]
[FONT=courier new]sudo apt-get update[/FONT]
[FONT=courier new]sudo apt-get install prime-indicator[/FONT]

I'm currently using 14.04, Kernel 3.13.0-24.
I have to say my problems with the wifi has returned (or maybe they weren't fixed at all???) .. The wifi works as it pleases and usually it stops working several minutes after boot (network connection is not dropped but frames can not be transmitted or recieved). In 95% of situations I can not connect to my home wifi, which practically makes Ubuntu unusable. About the touchpad... I found out that Synaptics has a better linux driver which they include in the payed distributions of linux. So we are screwed when it comes to Ubuntu. I tried tweaking the touchpad in many different ways but the choppy feeling didn't disappear.

---

