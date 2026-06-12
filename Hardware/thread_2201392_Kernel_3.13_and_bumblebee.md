---
title: "Kernel 3.13 and bumblebee"
date: 2014-01-24
forum: Hardware
---

### Post by Salvatore.tip on 2014-01-24
Hi everyone.
I have a laptop (Asus U36S) with nvidia optimus card.
I'm on Ubuntu 12.04 LTS.
To make less overheat and to use the nvidia gpu, I installed bumblebee and it worked fine until yesterday.
Yesterday in fact, I installed the new 3.13 Kernel and bumblebee refused to work ( no secondary GPU found and so on ).

Now I have some questions.
1 Should I install bumblebee or there is no need on 3.13?
2 if not: then how can I disable the nvidia card to generate less heat and noise and better battery life? 
3 if yes: how can I install it, what nvidia drivers should I pick?

Thanks in advance for the help

---

### Post by Salvatore.tip on 2014-01-25
I just installed the latest bumblebee from xorg edgers with the latest nvidia-331.38 from the same ppa.
This is what I'm getting:

```

salvo@salvo-U36SD:~$ optirun -vvv glxgears
[   82.164218] [DEBUG]Reading file: /etc/bumblebee/bumblebee.conf
[   82.164498] [INFO]Configured driver: nvidia
[   82.164606] [DEBUG]optirun version 3.2.1 starting...
[   82.164613] [DEBUG]Active configuration:
[   82.164616] [DEBUG] bumblebeed config file: /etc/bumblebee/bumblebee.conf
[   82.164619] [DEBUG] X display: :8
[   82.164622] [DEBUG] LD_LIBRARY_PATH: /usr/lib/nvidia-331:/usr/lib32/nvidia-331
[   82.164625] [DEBUG] Socket path: /var/run/bumblebee.socket
[   82.164628] [DEBUG] Accel/display bridge: auto
[   82.164631] [DEBUG] VGL Compression: proxy
[   82.164633] [DEBUG] VGLrun extra options: 
[   82.164636] [DEBUG] Primus LD Path: /usr/lib/x86_64-linux-gnu/primus:/usr/lib/i386-linux-gnu/primus
[   82.164715] [DEBUG]Using auto-detected bridge virtualgl
[   82.596372] [INFO]Response: No - error: Could not load GPU driver


[   82.596391] [ERROR]Cannot access secondary GPU - error: Could not load GPU driver


[   82.596398] [DEBUG]Socket closed.
[   82.596417] [ERROR]Aborting because fallback start is disabled.
[   82.596432] [DEBUG]Killing all remaining processes.

```

Also bbswitch ( v 0.8 ) seems not working too, the nvidia GPU is always ON. 

I have to force it OFF with:


```
[COLOR=#333333][FONT=Consolas]
tee /proc/acpi/bbswitch <<<OFF[/FONT][/COLOR]
```
[COLOR=#333333][FONT=Consolas]
[/FONT][/COLOR]Other infos:

```
salvo@salvo-U36SD:~$ dmesg | grep -C 10 bbswitch[    3.362249]    inputs:
[    3.362251]      Internal Mic=0x19
[    3.362253]      Mic=0x18
[    3.362254] realtek: No valid SSID, checking pincfg 0x40079a2d for NID 0x1d
[    3.362256] realtek: Enabling init ASM_ID=0x9a2d CODEC_ID=10ec0269
[    3.366672] init: alsa-restore main process (952) terminated with status 19
[    3.375567] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input19
[    3.376267] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input18
[    3.377595] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input17
[    3.646849] init: anacron main process (994) killed by TERM signal
[    3.703563] bbswitch: module verification failed: signature and/or  required key missing - tainting kernel
[    3.703861] bbswitch: version 0.8
[    3.703868] bbswitch: Found integrated VGA device 0000:00:02.0: \_SB_.PCI0.GFX0
[    3.703874] bbswitch: Found discrete VGA device 0000:01:00.0: \_SB_.PCI0.PEG0.GFX0
[    3.703885] ACPI Warning: \_SB_.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
[    3.704028] bbswitch: detected an Optimus _DSM function
[    3.704039] pci 0000:01:00.0: enabling device (0000 -> 0003)
[    3.704076] bbswitch: Succesfully loaded. Discrete card 0000:01:00.0 is on
[    3.706510] bbswitch: disabling discrete graphics
[    3.706522] ACPI Warning: \_SB_.PCI0.PEG0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
[    3.954878] [drm] Enabling RC6 states: RC6 on, RC6p off, RC6pp off
[    4.490218] init: plymouth-stop pre-start process (2171) terminated with status 1
[    5.018616] wlan0: authenticate with a0:f3:c1:e5:67:a2
[    5.040984] wlan0: send auth to a0:f3:c1:e5:67:a2 (try 1/3)
[    5.043278] wlan0: authenticated
[    5.046147] wlan0: associate with a0:f3:c1:e5:67:a2 (try 1/3)
[    5.050220] wlan0: RX AssocResp from a0:f3:c1:e5:67:a2 (capab=0x431 status=0 aid=3)
[    5.050271] wlan0: associated
[    5.050286] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   82.309315] bbswitch: enabling discrete graphics
[   82.736435] nvidia: module license 'NVIDIA' taints kernel.
[   82.736439] Disabling lock debugging due to kernel taint
[   82.739559] nvidia: Unknown symbol acpi_os_wait_events_complete (err 0)



```

```

salvo@salvo-U36SD:~$ uname -r
3.13.0-031300-generic

```

```

salvo@salvo-U36SD:~$ X -version


X.Org X Server 1.11.3
Release Date: 2011-12-16
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.42-37-generic x86_64 Ubuntu
Current Operating System: Linux salvo-U36SD 3.13.0-031300-generic #201401192235 SMP Mon Jan 20 03:36:48 UTC 2014 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-031300-generic root=UUID=36bdd24a-d971-4c3b-ace9-ab3b9e15e338 ro quiet
Build Date: 16 October 2013  04:41:23PM
xorg-server 2:1.11.4-0ubuntu10.14 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.30.2



```

---

