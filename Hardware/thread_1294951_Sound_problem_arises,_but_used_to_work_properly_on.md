---
title: "Sound problem arises, but used to work properly on laptop"
date: 2009-10-18
forum: Hardware
---

### Post by Kellimus on 2009-10-18
[SIZE=4]EDIT: I fixed the problem finally after a few hours of searching!  Please delete this thread or mark as solved or something.  Thanks for your time![/SIZE]

Well, I don't know what the problem is.. Sound used to work completely fine (before today, and even this morning) and now when I try to watch Youtube videos/embedded sound, my sound turns into static, and I lose all other sound on my laptop..

Here are the specs of the laptop: [http://reviews.cnet.com/laptops/sony-vaio-fs660-w/4507-3121_7-31386637.html?tag=mncolBtm;rnav](http://reviews.cnet.com/laptops/sony-vaio-fs660-w/4507-3121_7-31386637.html?tag=mncolBtm;rnav)

There is a problem with my laptop's (and the main reason I switched to Ubuntu, thinking it would fix the problems) ACPI.. I do believe that's why I was getting LSASS.exe errors on Windows XP before I made the switch to Linux.. Sometimes, my laptop will not even load up and sometimes when it gets loaded up and starts booting into Linux, it will have an error finding my ACPI..Sometimes, it says it cannot find something (a weird decimal number that is always the same, starts with 5 and looks something like this: [5.829.....]) and boots into Ubuntu fine..

I've switched all options in my Sound Preferences to the OSS - Open Sound System and that did seem to cure the issues I was having with static sound on my Pidgen messenger, and while trying to listen to music, but I still get the static sound when trying to watch youtube videos, or come across embedded sound..  The weird thing is before it happened, the startup sound for Ubuntu sounded fine but now since the problem, the startup sound is also staticy, but my Pidgen sounds fine and so does my music..Up until I try to watch a youtube video, then everything takes a dive.

Could this be caused by my ACPI going out, or is it something I tinkered with inside Ubuntu that is causing this?  Help is appreciated ^_^

I am running Ubuntu 9.04 desktop edition and the problem only started happening today, after I went into Volume Control and muted some things that didn't need to be on.

---

### Post by Kellimus on 2009-10-18
Okay so I dug a bit into the forums and ran across this thread [http://ubuntuforums.org/showthread.php?p=6628921](http://ubuntuforums.org/showthread.php?p=6628921) and did the terminal commands and well, this is what came up (copied from my Tomboy note):

**In Terminal with command lspci**

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce Go 6200/6400] (rev a1)
06:03.0 CardBus bridge: Texas Instruments PCI7420 CardBus Controller
06:03.2 FireWire (IEEE 1394): Texas Instruments PCI7x20 1394a-2000 OHCI Two-Port PHY/Link-Layer Controller
06:03.3 Mass storage controller: Texas Instruments PCI7420/7620 Combo CardBus, 1394a-2000 OHCI and SD/MS-Pro Controller
06:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
06:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile (rev 03)

**In Terminal with command lsusb**

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c510 Logitech, Inc. Cordless Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

**In Terminal with command cat /proc/asound/cards**
 
0 [Intel          ]: HDA-Intel - HDA Intel
                     HDA Intel at 0x80000000 irq 16

**In Terminal with command cat /proc/asound/modules**

0 snd_hda_intel

**In Terminal with command aplay -l**

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC260 Analog [ALC260 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

**In Terminal with command arecord -l**

**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC260 Analog [ALC260 Analog]
  Subdevices: 1/1

And then I did the command killall pulseaudio -vvv and this is what was output on the Terminal....But the weird thing about it is that it made my sound work again..Haven't tested Youtube yet, but the sound works properly after running killall pulseaudio -vvv  This is what was output on the Terminal:

I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
D: main.c: Started as real root: no, suid root: yes
I: main.c: PolicyKit refuses acquire-high-priority privilege.
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
I: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
D: main.c: Can realtime: no, can high-priority: no
D: main.c: Can realtime: no, can high-priority: no
I: main.c: This is PulseAudio 0.9.14
D: main.c: Compilation host: i486-pc-linux-gnu
D: main.c: Compilation CFLAGS: -g -O2 -g -Wall -O3 -Wall -W -Wextra -pedantic -pipe -Wno-long-long -Wvla -Wno-overlength-strings -Wconversion -Wundef -Wformat -Wlogical-op -Wpacked -Wformat-security -Wmissing-include-dirs -Wformat-nonliteral -Wold-style-definition -Wdeclaration-after-statement -Wfloat-equal -Wmissing-declarations -Wmissing-prototypes -Wstrict-prototypes -Wredundant-decls -Wmissing-noreturn -Wshadow -Wendif-labels -Wpointer-arith -Wcast-align -Wwrite-strings -Wno-unused-parameter -ffast-math
D: main.c: Running on host: Linux i686 2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:49:34 UTC 2009
I: main.c: Page size is 4096 bytes
D: main.c: Compiled with Valgrind support: no
D: main.c: Running in valgrind mode: no
D: main.c: Optimized build: yes
I: main.c: Machine ID is bd480c77a6868980676b1f834abb43be.
I: main.c: Using runtime directory /home/kellimus/.pulse/bd480c77a6868980676b1f834abb43be:runtime.
I: main.c: Using state directory /home/kellimus/.pulse.
I: main.c: Running in system mode: no
I: main.c: Fresh high-resolution timers available! Bon appetit!
D: memblock.c: Using shared memory pool with 1024 slots of size 64.0 KiB each, total size is 64.0 MiB, maximum usable slot size is 65496
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-gconf.so': success
I: module.c: Loaded "module-gconf" (index: #0; argument: "").
I: module.c: Loaded "module-suspend-on-idle" (index: #1; argument: "").
I: module-device-restore.c: Sucessfully opened database file '/home/kellimus/.pulse/bd480c77a6868980676b1f834abb43be:device-volumes.i486-pc-linux-gnu.gdbm'.
I: module.c: Loaded "module-device-restore" (index: #2; argument: "").
I: module-stream-restore.c: Sucessfully opened database file '/home/kellimus/.pulse/bd480c77a6868980676b1f834abb43be:stream-volumes.i486-pc-linux-gnu.gdbm'.
I: module.c: Loaded "module-stream-restore" (index: #3; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-hal-detect.so': success
I: module-hal-detect.c: Trying capability alsa
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/computer_alsa_timer
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/computer_alsa_sequencer
D: module-hal-detect.c: Loading module-alsa-sink with arguments 'device_id=0 sink_name=alsa_output.pci_8086_2668_sound_card_0_alsa_playback_0 tsched=0'
D: alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
I: module-alsa-sink.c: Successfully opened device front:0.
I: module-alsa-sink.c: Successfully enabled mmap() mode.
I: (alsa-lib)control.c: Invalid CTL front:0
I: alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Using mixer control "Master".
I: module-device-restore.c: Restoring volume for sink alsa_output.pci_8086_2668_sound_card_0_alsa_playback_0.
I: module-device-restore.c: Restoring mute state for sink alsa_output.pci_8086_2668_sound_card_0_alsa_playback_0.
I: sink.c: Created sink 0 "alsa_output.pci_8086_2668_sound_card_0_alsa_playback_0" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: module-device-restore.c: Restoring volume for source alsa_output.pci_8086_2668_sound_card_0_alsa_playback_0.monitor.
I: module-device-restore.c: Restoring mute state for source alsa_output.pci_8086_2668_sound_card_0_alsa_playback_0.monitor.
I: source.c: Created source 0 "alsa_output.pci_8086_2668_sound_card_0_alsa_playback_0.monitor" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: module-alsa-sink.c: Using 8 fragments of size 1792 bytes, buffer time is 81.27ms
D: module-alsa-sink.c: hwbuf_unused=0
D: module-alsa-sink.c: setting avail_min=1
I: module-alsa-sink.c: Volume ranges from 0 to 64.
I: module-alsa-sink.c: Volume ranges from -64.00 dB to 0.00 dB.
I: alsa-util.c: ALSA device lacks independant volume controls for each channel.
I: module-alsa-sink.c: Using hardware volume control. Hardware dB scale supported.
D: alsa-util.c: snd_pcm_dump():
D: alsa-util.c: Soft volume PCM
D: alsa-util.c: Control: PCM Playback Volume
D: alsa-util.c: min_dB: -51
D: alsa-util.c: max_dB: 0
D: alsa-util.c: resolution: 256
D: alsa-util.c: Its setup is:
D: alsa-util.c:   stream       : PLAYBACK
D: alsa-util.c:   access       : MMAP_INTERLEAVED
D: alsa-util.c:   format       : S16_LE
D: alsa-util.c:   subformat    : STD
D: alsa-util.c:   channels     : 2
D: alsa-util.c:   rate         : 44100
D: alsa-util.c:   exact rate   : 44100 (44100/1)
D: alsa-util.c:   msbits       : 16
D: alsa-util.c:   buffer_size  : 3584
D: alsa-util.c:   period_size  : 448
D: alsa-util.c:   period_time  : 10158
D: alsa-util.c:   tstamp_mode  : ENABLE
D: alsa-util.c:   period_step  : 1
D: alsa-util.c:   avail_min    : 448
D: alsa-util.c:   period_event : 0
D: alsa-util.c:   start_threshold  : -1
D: alsa-util.c:   stop_threshold   : 1879048192
D: alsa-util.c:   silence_threshold: 0
D: alsa-util.c:   silence_size : 0
D: alsa-util.c:   boundary     : 1879048192
D: alsa-util.c: Slave: Hardware PCM card 0 'HDA Intel' device 0 subdevice 0
D: alsa-util.c: Its setup is:
D: alsa-util.c:   stream       : PLAYBACK
D: alsa-util.c:   access       : MMAP_INTERLEAVED
D: alsa-util.c:   format       : S16_LE
D: alsa-util.c:   subformat    : STD
D: alsa-util.c:   channels     : 2
D: alsa-util.c:   rate         : 44100
D: alsa-util.c:   exact rate   : 44100 (44100/1)
D: alsa-util.c:   msbits       : 16
D: alsa-util.c:   buffer_size  : 3584
D: alsa-util.c:   period_size  : 448
D: alsa-util.c:   period_time  : 10158
D: alsa-util.c:   tstamp_mode  : ENABLE
D: alsa-util.c:   period_step  : 1
D: alsa-util.c:   avail_min    : 448
D: alsa-util.c:   period_event : 0
D: alsa-util.c:   start_thre
D: module-alsa-sink.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+29
D: module-alsa-sink.c: Requested volume: 0:  71% 1:  71%
D: module-alsa-sink.c: Got hardware volume: 0:  71% 1:  71%
D: module-alsa-sink.c: Calculated software volume: 0: 100% 1: 100%
I: module-alsa-sink.c: Starting playback.
D: module-suspend-on-idle.c: Source alsa_output.pci_8086_2668_sound_card_0_alsa_playback_0.monitor becomes idle.
D: module-suspend-on-idle.c: Sink alsa_output.pci_8086_2668_sound_card_0_alsa_playback_0 becomes idle.
I: module.c: Loaded "module-alsa-sink" (index: #4; argument: "device_id=0 sink_name=alsa_output.pci_8086_2668_sound_card_0_alsa_playback_0 tsched=0").
D: module-hal-detect.c: Loading module-alsa-source with arguments 'device_id=0 source_name=alsa_input.pci_8086_2668_sound_card_0_alsa_capture_0 tsched=0'
D: alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
I: module-alsa-source.c: Successfully opened device front:0.
I: module-alsa-source.c: Successfully enabled mmap() mode.
I: (alsa-lib)control.c: Invalid CTL front:0
I: alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Using mixer control "Capture".
I: module-device-restore.c: Restoring volume for source alsa_input.pci_8086_2668_sound_card_0_alsa_capture_0.
I: module-device-restore.c: Restoring mute state for source alsa_input.pci_8086_2668_sound_card_0_alsa_capture_0.
I: source.c: Created source 1 "alsa_input.pci_8086_2668_sound_card_0_alsa_capture_0" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: module-alsa-source.c: Using 8 fragments of size 1792 bytes, buffer time is 81.27ms
D: module-alsa-source.c: hwbuf_unused=0
D: module-alsa-source.c: setting avail_min=1
I: module-alsa-source.c: Volume ranges from 0 to 35.
I: module-alsa-source.c: Volume ranges from 0.00 dB to 35.00 dB.
I: alsa-util.c: All 2 channels can be mapped to mixer channels.
I: module-alsa-source.c: Using hardware volume control. Hardware dB scale supported.
D: alsa-util.c: snd_pcm_dump():
D: alsa-util.c: Soft volume PCM
D: alsa-util.c: Control: PCM Playback Volume
D: alsa-util.c: min_dB: -51
D: alsa-util.c: max_dB: 0
D: alsa-util.c: resolution: 256
D: alsa-util.c: Its setup is:
D: alsa-util.c:   stream       : CAPTURE
D: alsa-util.c:   access       : MMAP_INTERLEAVED
D: alsa-util.c:   format       : S16_LE
D: alsa-util.c:   subformat    : STD
D: alsa-util.c:   channels     : 2
D: alsa-util.c:   rate         : 44100
D: alsa-util.c:   exact rate   : 44100 (44100/1)
D: alsa-util.c:   msbits       : 16
D: alsa-util.c:   buffer_size  : 3584
D: alsa-util.c:   period_size  : 448
D: alsa-util.c:   period_time  : 10158
D: alsa-util.c:   tstamp_mode  : ENABLE
D: alsa-util.c:   period_step  : 1
D: alsa-util.c:   avail_min    : 448
D: alsa-util.c:   period_event : 0
D: alsa-util.c:   start_threshold  : -1
D: alsa-util.c:   stop_threshold   : 1879048192
D: alsa-util.c:   silence_threshold: 0
D: alsa-util.c:   silence_size : 0
D: alsa-util.c:   boundary     : 1879048192
D: alsa-util.c: Slave: Hardware PCM card 0 'HDA Intel' device 0 subdevice 0
D: alsa-util.c: Its setup is:
D: alsa-util.c:   stream       : CAPTURE
D: alsa-util.c:   access       : MMAP_INTERLEAVED
D: alsa-util.c:   format       : S16_LE
D: alsa-util.c:   subformat    : STD
D: alsa-util.c:   channels     : 2
D: alsa-util.c:   rate         : 44100
D: alsa-util.c:   exact rate   : 44100 (44100/1)
D: alsa-util.c:   msbits       : 16
D: alsa-util.c:   buffer_size  : 3584
D: alsa-util.c:   period_size  : 448
D: alsa-util.c:   period_time  : 10158
D: alsa-util.c:   tstamp_mode  : ENABLE
D: alsa-util.c:   period_step  : 1
D: alsa-util.c:   avail_min    : 448
D: alsa-util.c:   period_event : 0
D: alsa-util.c:   start_thresh
D: module-alsa-source.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+28
D: module-alsa-source.c: Requested volume: 0:  41% 1:  41%
D: module-alsa-source.c: Got hardware volume: 0:  43% 1:  43%
D: module-alsa-source.c: Calculated software volume: 0:  98% 1:  98%
D: module-suspend-on-idle.c: Source alsa_input.pci_8086_2668_sound_card_0_alsa_capture_0 becomes idle.
I: module.c: Loaded "module-alsa-source" (index: #5; argument: "device_id=0 source_name=alsa_input.pci_8086_2668_sound_card_0_alsa_capture_0 tsched=0").
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_8086_2668_sound_card_0_alsa_control__1
I: module-hal-detect.c: Loaded 2 modules.
I: module.c: Loaded "module-hal-detect" (index: #6; argument: "tsched=0").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-esound-protocol-unix.so': success
I: module.c: Loaded "module-esound-protocol-unix" (index: #7; argument: "").
I: module.c: Loaded "module-native-protocol-unix" (index: #8; argument: "").
I: module-default-device-restore.c: Restored default sink 'alsa_output.pci_8086_2668_sound_card_0_alsa_playback_0'.
D: core-subscribe.c: Dropped redundant event due to change event.
I: module-default-device-restore.c: Restored default source 'alsa_input.pci_8086_2668_sound_card_0_alsa_capture_0'.
I: module.c: Loaded "module-default-device-restore" (index: #9; argument: "").
I: module.c: Loaded "module-rescue-streams" (index: #10; argument: "").
I: module.c: Loaded "module-always-sink" (index: #11; argument: "").
I: client.c: Created 0 "ConsoleKit Session /org/freedesktop/ConsoleKit/Session7"
D: module-console-kit.c: Added new session /org/freedesktop/ConsoleKit/Session7
I: module.c: Loaded "module-console-kit" (index: #12; argument: "").
I: module.c: Loaded "module-position-event-sounds" (index: #13; argument: "").
I: main.c: Daemon startup complete.
D: module-hal-detect.c: dbus: interface=org.freedesktop.DBus, path=/org/freedesktop/DBus, member=NameAcquired
D: module-console-kit.c: dbus: interface=org.freedesktop.DBus, path=/org/freedesktop/DBus, member=NameAcquired
I: module-suspend-on-idle.c: Sink alsa_output.pci_8086_2668_sound_card_0_alsa_playback_0 idle for too long, suspending ...
I: module-alsa-sink.c: Device suspended...
I: module-suspend-on-idle.c: Source alsa_output.pci_8086_2668_sound_card_0_alsa_playback_0.monitor idle for too long, suspending ...
I: module-suspend-on-idle.c: Source alsa_input.pci_8086_2668_sound_card_0_alsa_capture_0 idle for too long, suspending ...
I: module-alsa-source.c: Device suspended...

Tested out youtube and no sound, not even any static happens...All the other sound on my computer works perfectly but no Youtube videos..

Hope this information helps with finding the root of the problem and fixing it ^_^

Edit:  Well I noticed that after I played some music on my laptop, inside the terminal, this was output:

D: module-hal-detect.c: dbus: interface=org.freedesktop.ConsoleKit.Seat, path=/org/freedesktop/ConsoleKit/Seat1, member=SessionAdded
D: module-console-kit.c: dbus: interface=org.freedesktop.ConsoleKit.Seat, path=/org/freedesktop/ConsoleKit/Seat1, member=SessionAdded
D: module-hal-detect.c: dbus: interface=org.freedesktop.ConsoleKit.Seat, path=/org/freedesktop/ConsoleKit/Seat1, member=SessionAdded
D: module-console-kit.c: dbus: interface=org.freedesktop.ConsoleKit.Seat, path=/org/freedesktop/ConsoleKit/Seat1, member=SessionAdded
D: module-hal-detect.c: dbus: interface=org.freedesktop.ConsoleKit.Seat, path=/org/freedesktop/ConsoleKit/Seat1, member=SessionAdded
D: module-console-kit.c: dbus: interface=org.freedesktop.ConsoleKit.Seat, path=/org/freedesktop/ConsoleKit/Seat1, member=SessionAdded
D: module-hal-detect.c: dbus: interface=org.freedesktop.ConsoleKit.Seat, path=/org/freedesktop/ConsoleKit/Seat1, member=SessionAdded
D: module-console-kit.c: dbus: interface=org.freedesktop.ConsoleKit.Seat, path=/org/freedesktop/ConsoleKit/Seat1, member=SessionAdded
D: module-hal-detect.c: dbus: interface=org.freedesktop.ConsoleKit.Seat, path=/org/freedesktop/ConsoleKit/Seat1, member=SessionRemoved
D: module-console-kit.c: dbus: interface=org.freedesktop.ConsoleKit.Seat, path=/org/freedesktop/ConsoleKit/Seat1, member=SessionRemoved
D: module-hal-detect.c: dbus: interface=org.freedesktop.ConsoleKit.Seat, path=/org/freedesktop/ConsoleKit/Seat1, member=SessionRemoved
D: module-console-kit.c: dbus: interface=org.freedesktop.ConsoleKit.Seat, path=/org/freedesktop/ConsoleKit/Seat1, member=SessionRemoved
D: module-hal-detect.c: dbus: interface=org.freedesktop.ConsoleKit.Seat, path=/org/freedesktop/ConsoleKit/Seat1, member=SessionRemoved
D: module-console-kit.c: dbus: interface=org.freedesktop.ConsoleKit.Seat, path=/org/freedesktop/ConsoleKit/Seat1, member=SessionRemoved
D: module-hal-detect.c: dbus: interface=org.freedesktop.ConsoleKit.Seat, path=/org/freedesktop/ConsoleKit/Seat1, member=SessionRemoved
D: module-console-kit.c: dbus: interface=org.freedesktop.ConsoleKit.Seat, path=/org/freedesktop/ConsoleKit/Seat1, member=SessionRemoved
D: module-alsa-sink.c: Read hardware volume: 0:  75% 1:  75%
I: module-device-restore.c: Storing volume/mute for device sink:alsa_output.pci_8086_2668_sound_card_0_alsa_playback_0.
D: module-alsa-sink.c: Read hardware volume: 0:  76% 1:  76%
I: module-device-restore.c: Storing volume/mute for device sink:alsa_output.pci_8086_2668_sound_card_0_alsa_playback_0.
D: module-alsa-sink.c: Read hardware volume: 0:  78% 1:  78%
I: module-device-restore.c: Storing volume/mute for device sink:alsa_output.pci_8086_2668_sound_card_0_alsa_playback_0.
D: module-alsa-sink.c: Read hardware volume: 0:  81% 1:  81%
I: module-device-restore.c: Storing volume/mute for device sink:alsa_output.pci_8086_2668_sound_card_0_alsa_playback_0.
D: module-alsa-sink.c: Read hardware volume: 0:  83% 1:  83%
I: module-device-restore.c: Storing volume/mute for device sink:alsa_output.pci_8086_2668_sound_card_0_alsa_playback_0.
D: module-alsa-sink.c: Read hardware volume: 0:  85% 1:  85%
I: module-device-restore.c: Storing volume/mute for device sink:alsa_output.pci_8086_2668_sound_card_0_alsa_playback_0.
D: module-alsa-sink.c: Read hardware volume: 0:  89% 1:  89%
I: module-device-restore.c: Storing volume/mute for device sink:alsa_output.pci_8086_2668_sound_card_0_alsa_playback_0.
D: module-alsa-sink.c: Read hardware volume: 0:  93% 1:  93%
I: module-device-restore.c: Storing volume/mute for device sink:alsa_output.pci_8086_2668_sound_card_0_alsa_playback_0.
D: module-alsa-sink.c: Read hardware volume: 0:  96% 1:  96%
I: module-device-restore.c: Storing volume/mute for device sink:alsa_output.pci_8086_2668_sound_card_0_alsa_playback_0.
D: module-alsa-sink.c: Read hardware volume: 0:  98% 1:  98%
I: module-device-restore.c: Storing volume/mute for device sink:alsa_output.pci_8086_2668_sound_card_0_alsa_playback_0.
D: module-alsa-sink.c: Read hardware volume: 0: 100% 1: 100%
I: module-device-restore.c: Storing volume/mute for device sink:alsa_output.pci_8086_2668_sound_card_0_alsa_playback_0.
I: module-device-restore.c: Synced.

I pressed Ctrl + C (forgot the shift xD) and it output this:

D: module-hal-detect.c: dbus: interface=org.freedesktop.ConsoleKit.Seat, path=/org/freedesktop/ConsoleKit/Seat1, member=SessionAdded
D: module-console-kit.c: dbus: interface=org.freedesktop.ConsoleKit.Seat, path=/org/freedesktop/ConsoleKit/Seat1, member=SessionAdded
D: module-hal-detect.c: dbus: interface=org.freedesktop.ConsoleKit.Seat, path=/org/freedesktop/ConsoleKit/Seat1, member=SessionRemoved
D: module-console-kit.c: dbus: interface=org.freedesktop.ConsoleKit.Seat, path=/org/freedesktop/ConsoleKit/Seat1, member=SessionRemoved
^CI: main.c: Got signal SIGINT.
I: main.c: Exiting.
I: main.c: Daemon shutdown initiated.
I: module.c: Unloading "module-gconf" (index: #0).
I: module.c: Unloaded "module-gconf" (index: #0).
I: module.c: Unloading "module-suspend-on-idle" (index: #1).
I: module.c: Unloaded "module-suspend-on-idle" (index: #1).
I: module.c: Unloading "module-device-restore" (index: #2).
I: module.c: Unloaded "module-device-restore" (index: #2).
I: module.c: Unloading "module-stream-restore" (index: #3).
I: module.c: Unloaded "module-stream-restore" (index: #3).
I: module.c: Unloading "module-alsa-sink" (index: #4).
D: module-always-sink.c: Autoloading null-sink as no other sinks detected.
I: sink.c: Created sink 1 "auto_null" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: source.c: Created source 2 "auto_null.monitor" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
D: module-null-sink.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+27
I: module.c: Loaded "module-null-sink" (index: #14; argument: "sink_name=auto_null").
D: module-rescue-streams.c: No sink inputs to move away.
D: module-rescue-streams.c: No source outputs to move away.
D: module-alsa-sink.c: Thread shutting down
I: sink.c: Freeing sink 0 "alsa_output.pci_8086_2668_sound_card_0_alsa_playback_0"
I: source.c: Freeing source 0 "alsa_output.pci_8086_2668_sound_card_0_alsa_playback_0.monitor"
I: module.c: Unloaded "module-alsa-sink" (index: #4).
I: module.c: Unloading "module-alsa-source" (index: #5).
D: module-rescue-streams.c: No source outputs to move away.
D: module-alsa-source.c: Thread shutting down
I: source.c: Freeing source 1 "alsa_input.pci_8086_2668_sound_card_0_alsa_capture_0"
I: module.c: Unloaded "module-alsa-source" (index: #5).
I: module.c: Unloading "module-hal-detect" (index: #6).
I: module.c: Unloaded "module-hal-detect" (index: #6).
I: module.c: Unloading "module-esound-protocol-unix" (index: #7).
I: module.c: Unloaded "module-esound-protocol-unix" (index: #7).
I: module.c: Unloading "module-native-protocol-unix" (index: #8).
I: module.c: Unloaded "module-native-protocol-unix" (index: #8).
I: module.c: Unloading "module-default-device-restore" (index: #9).
I: module.c: Unloaded "module-default-device-restore" (index: #9).
I: module.c: Unloading "module-rescue-streams" (index: #10).
I: module.c: Unloaded "module-rescue-streams" (index: #10).
I: module.c: Unloading "module-always-sink" (index: #11).
I: module.c: Unloaded "module-always-sink" (index: #11).
I: module.c: Unloading "module-console-kit" (index: #12).
D: module-console-kit.c: Removing session /org/freedesktop/ConsoleKit/Session7
I: client.c: Freed 0 "ConsoleKit Session /org/freedesktop/ConsoleKit/Session7"
I: module.c: Unloaded "module-console-kit" (index: #12).
I: module.c: Unloading "module-position-event-sounds" (index: #13).
I: module.c: Unloaded "module-position-event-sounds" (index: #13).
I: module.c: Unloading "module-null-sink" (index: #14).
D: core-subscribe.c: Dropped redundant event due to remove event.
D: core-subscribe.c: Dropped redundant event due to remove event.
D: module-null-sink.c: Thread shutting down
I: sink.c: Freeing sink 1 "auto_null"
I: source.c: Freeing source 2 "auto_null.monitor"
I: module.c: Unloaded "module-null-sink" (index: #14).
D: core-subscribe.c: Dropped redundant event due to remove event.
I: main.c: Daemon terminated.

I'm a complete Ubuntu noob (but not a computer noob) so I'm not entirely too sure how to fix the Youtube no sound problem.. :(  Am I going to have to go in and add some C code and compile?  Help would be appreciated!! :D

---

### Post by Kellimus on 2009-10-19
I've installed Ubuntu-Studio because I make music and such, and the sound was working then just stopped again..

Do I need to download a new update for a library or something?

---

