---
title: "nvidia graphics problems - second life wont load.. plz help!"
date: 2011-11-28
forum: Hardware
---

### Post by paulqueen on 2011-11-28
i am having a problem running secondlife.

my graphics card is nvidia 9600 M GS on an asus m50vm-x1 laptop.

my output from second life is:
```

paulq@futant:~/secondlifelinux$ ./secondlife
64-bit Linux detected.
Running from /home/paulq/secondlifelinux
 - Installing menu entries in /home/paulq/.local/share/applications
2011-11-29T04:31:08Z INFO: (anonymous namespace)::LogControlFile::loadFile: logging reconfigured from /home/paulq/secondlifelinux/app_settings/logcontrol.xml
2011-11-29T04:31:08Z INFO: loadSettingsFromDirectory: Attempting to load settings for the group Global - from location Default
2011-11-29T04:31:08Z INFO: loadSettingsFromDirectory: Loaded settings file /home/paulq/secondlifelinux/app_settings/settings.xml
2011-11-29T04:31:08Z INFO: loadSettingsFromDirectory: Attempting to load settings for the group PerAccount - from location Default
2011-11-29T04:31:08Z INFO: loadSettingsFromDirectory: Loaded settings file /home/paulq/secondlifelinux/app_settings/settings_per_account.xml
2011-11-29T04:31:08Z INFO: loadSettingsFromDirectory: Attempting to load settings for the group CrashSettings - from location Default
2011-11-29T04:31:08Z INFO: loadSettingsFromDirectory: Loaded settings file /home/paulq/secondlifelinux/app_settings/settings_crash_behavior.xml
2011-11-29T04:31:08Z INFO: loadSettingsFromDirectory: Attempting to load settings for the group Warnings - from location Default
2011-11-29T04:31:08Z INFO: loadSettingsFromDirectory: Loaded settings file /home/paulq/secondlifelinux/app_settings/ignorable_dialogs.xml
2011-11-29T04:31:08Z WARNING: set: Invalid control VersionChannelName
2011-11-29T04:31:08Z INFO: initParseCommandLine: Language en
2011-11-29T04:31:08Z INFO: initParseCommandLine: Location US
2011-11-29T04:31:08Z INFO: initParseCommandLine: Variant UTF-8
2011-11-29T04:31:08Z INFO: loadSettingsFromDirectory: Attempting to load settings for the group Global - from location User
2011-11-29T04:31:08Z WARNING: loadFromFile: Cannot find file /home/paulq/.secondlife/user_settings//home/paulq/.secondlife/user_settings/settings.xml to load.
2011-11-29T04:31:08Z INFO: loadSettingsFromDirectory: Cannot load /home/paulq/.secondlife/user_settings//home/paulq/.secondlife/user_settings/settings.xml - No settings found.
2011-11-29T04:31:08Z INFO: loadSettingsFromDirectory: Attempting to load settings for the group CrashSettings - from location User
2011-11-29T04:31:08Z WARNING: loadFromFile: Cannot find file /home/paulq/.secondlife/user_settings/settings_crash_behavior.xml to load.
2011-11-29T04:31:08Z INFO: loadSettingsFromDirectory: Cannot load /home/paulq/.secondlife/user_settings/settings_crash_behavior.xml - No settings found.
2011-11-29T04:31:08Z INFO: loadSettingsFromDirectory: Attempting to load settings for the group Warnings - from location User
2011-11-29T04:31:08Z WARNING: loadFromFile: Cannot find file /home/paulq/.secondlife/user_settings/ignorable_dialogs.xml to load.
2011-11-29T04:31:08Z INFO: loadSettingsFromDirectory: Cannot load /home/paulq/.secondlife/user_settings/ignorable_dialogs.xml - No settings found.
2011-11-29T04:31:08Z INFO: loadSettingsFromDirectory: Attempting to load settings for the group Global - from location Session
2011-11-29T04:31:08Z INFO: loadSettingsFromDirectory: Attempting to load settings for the group Global - from location UserSession
2011-11-29T04:31:08Z WARNING: LLUIColorTable::loadFromFilename: Unable to parse color file /home/paulq/.secondlife/skins/default/colors.xml
2011-11-29T04:31:08Z WARNING: LLUIColorTable::loadFromFilename: Unable to parse color file /home/paulq/.secondlife/user_settings/colors.xml
2011-11-29T04:31:08Z INFO: init: Configuration initialized.
2011-11-29T04:31:08Z INFO: init: LLCurl initialized.
2011-11-29T04:31:08Z INFO: init: Threads initialized.
2011-11-29T04:31:08Z INFO: init: UI initialized.
2011-11-29T04:31:09Z INFO: init: Notifications initialized.
2011-11-29T04:31:09Z INFO: initialize: is array
2011-11-29T04:31:09Z INFO: writeSystemInfo: Second Life version 3.2.1
2011-11-29T04:31:09Z INFO: writeSystemInfo: Local time: 2011-11-28T23:31:09 EST
2011-11-29T04:31:09Z INFO: writeSystemInfo: CPU info:
processor	: 0 
vendor_id	: GenuineIntel 
cpu family	: 6 
model		: 23 
model name	: Intel(R) Core(TM)2 Duo CPU     P8400  @ 2.26GHz 
stepping	: 6 
cpu MHz		: 2261.508 
cache size	: 3072 KB 
physical id	: 0 
siblings	: 2 
core id		: 0 
cpu cores	: 2 
apicid		: 0 
initial apicid	: 0 
fpu		: yes 
fpu_exception	: yes 
cpuid level	: 10 
wp		: yes 
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xt 
r pdcm sse4_1 lahf_lm tpr_shadow vnmi flexpriority 
bogomips	: 4523.01 
clflush size	: 64 
cache_alignment	: 64 
address sizes	: 36 bits physical, 48 bits virtual 
power management: 
 
processor	: 1 
vendor_id	: GenuineIntel 
cpu family	: 6 
model		: 23 
model name	: Intel(R) Core(TM)2 Duo CPU     P8400  @ 2.26GHz 
stepping	: 6 
cpu MHz		: 2261.508 
cache size	: 3072 KB 
physical id	: 0 
siblings	: 2 
core id		: 1 
cpu cores	: 2 
apicid		: 1 
initial apicid	: 1 
fpu		: yes 
fpu_exception	: yes 
cpuid level	: 10 
wp		: yes 
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xt 
r pdcm sse4_1 lahf_lm tpr_shadow vnmi flexpriority 
bogomips	: 4522.44 
clflush size	: 64 
cache_alignment	: 64 
address sizes	: 36 bits physical, 48 bits virtual 
power management: 
 

->mHasSSE:     1
->mHasSSE2:    1
->mHasAltivec: 0
->mCPUMHz:     2261.51
->mCPUString:  Intel(R) Core(TM)2 Duo CPU     P8400  @ 2.26GHz (2261.51 MHz)

2011-11-29T04:31:09Z INFO: writeSystemInfo: Memory info:
2011-11-29T04:31:09Z <mem>            Active:       984212
2011-11-29T04:31:09Z <mem>      Active(anon):       505404
2011-11-29T04:31:09Z <mem>      Active(file):       478808
2011-11-29T04:31:09Z <mem>         AnonPages:       503704
2011-11-29T04:31:09Z <mem>            Bounce:            0
2011-11-29T04:31:09Z <mem>           Buffers:        59280
2011-11-29T04:31:09Z <mem>            Cached:      2078752
2011-11-29T04:31:09Z <mem>       CommitLimit:      6222860
2011-11-29T04:31:09Z <mem>      Committed_AS:      1910712
2011-11-29T04:31:09Z <mem>       DirectMap2M:      4134912
2011-11-29T04:31:09Z <mem>       DirectMap4k:        58880
2011-11-29T04:31:09Z <mem>             Dirty:         4548
2011-11-29T04:31:09Z <mem> HardwareCorrupted:            0
2011-11-29T04:31:09Z <mem>    HugePages_Free:            0
2011-11-29T04:31:09Z <mem>    HugePages_Rsvd:            0
2011-11-29T04:31:09Z <mem>    HugePages_Surp:            0
2011-11-29T04:31:09Z <mem>   HugePages_Total:            0
2011-11-29T04:31:09Z <mem>      Hugepagesize:         2048
2011-11-29T04:31:09Z <mem>          Inactive:      1657428
2011-11-29T04:31:09Z <mem>    Inactive(anon):         4676
2011-11-29T04:31:09Z <mem>    Inactive(file):      1652752
2011-11-29T04:31:09Z <mem>       KernelStack:         2072
2011-11-29T04:31:09Z <mem>            Mapped:       134656
2011-11-29T04:31:09Z <mem>           MemFree:      1255932
2011-11-29T04:31:09Z <mem>          MemTotal:      4063272
2011-11-29T04:31:09Z <mem>           Mlocked:           68
2011-11-29T04:31:09Z <mem>      NFS_Unstable:            0
2011-11-29T04:31:09Z <mem>        PageTables:        20284
2011-11-29T04:31:09Z <mem>      SReclaimable:        78988
2011-11-29T04:31:09Z <mem>        SUnreclaim:        20136
2011-11-29T04:31:09Z <mem>             Shmem:         6476
2011-11-29T04:31:09Z <mem>              Slab:        99124
2011-11-29T04:31:09Z <mem>        SwapCached:            0
2011-11-29T04:31:09Z <mem>          SwapFree:      4191224
2011-11-29T04:31:09Z <mem>         SwapTotal:      4191224
2011-11-29T04:31:09Z <mem>       Unevictable:           68
2011-11-29T04:31:09Z <mem>       VmallocUsed:       316940
2011-11-29T04:31:09Z <mem>         Writeback:            0
2011-11-29T04:31:09Z <mem>      WritebackTmp:            0
2011-11-29T04:31:09Z <mem>         timestamp: 2011-11-29T04:31:08.13Z

2011-11-29T04:31:09Z INFO: writeSystemInfo: OS: Linux 2.6
2011-11-29T04:31:09Z INFO: writeSystemInfo: OS info: Linux 2.6.32-5-amd64 #1 SMP Mon Oct 3 03:59:20 UTC 2011 x86_64
2011-11-29T04:31:09Z INFO: writeSystemInfo: Timers: rdtsc
2011-11-29T04:31:09Z INFO: writeDebugInfo: Opening debug file /home/paulq/.secondlife/logs/debug_info.log
2011-11-29T04:31:09Z INFO: LLUpdaterServiceImpl::setState: setting state to 1
2011-11-29T04:31:09Z INFO: LLUpdaterServiceImpl::restartTimer: will check for update again in 0 seconds
2011-11-29T04:31:09Z INFO: init: J2C Engine is: KDU v6.4.1
2011-11-29T04:31:09Z INFO: init: libcurl version is: libcurl/7.21.1 OpenSSL/1.0.0d zlib/1.2.5 c-ares/1.7.1
2011-11-29T04:31:09Z INFO: init: UI initialization is done.
2011-11-29T04:31:09Z INFO: updateVectorize: Vectorization         : DISABLED
2011-11-29T04:31:09Z INFO: updateVectorize: Vector Processor      : COMPILER DEFAULT
2011-11-29T04:31:09Z INFO: updateVectorize: Vectorized Skinning   : ENABLED
2011-11-29T04:31:09Z INFO: updateVectorize: Vectorization         : DISABLED
2011-11-29T04:31:09Z INFO: updateVectorize: Vector Processor      : COMPILER DEFAULT
2011-11-29T04:31:09Z INFO: updateVectorize: Vectorized Skinning   : ENABLED
2011-11-29T04:31:09Z INFO: updateVectorize: Vectorization         : DISABLED
2011-11-29T04:31:09Z INFO: updateVectorize: Vector Processor      : COMPILER DEFAULT
2011-11-29T04:31:09Z INFO: updateVectorize: Vectorized Skinning   : DISABLED
2011-11-29T04:31:09Z INFO: grab_dbus_syms: Found DSO: libdbus-glib-1.so.2
2011-11-29T04:31:09Z INFO: init: Hardware test initialization done.
2011-11-29T04:31:09Z INFO: initCache: Headers: 143165 Textures size: 327 MB
2011-11-29T04:31:09Z INFO: purgeAllTextures: Deleting files in directory: /home/paulq/.secondlife/cache/texturecache/0
2011-11-29T04:31:09Z INFO: purgeAllTextures: Deleting files in directory: /home/paulq/.secondlife/cache/texturecache/1
2011-11-29T04:31:09Z INFO: purgeAllTextures: Deleting files in directory: /home/paulq/.secondlife/cache/texturecache/2
2011-11-29T04:31:09Z INFO: purgeAllTextures: Deleting files in directory: /home/paulq/.secondlife/cache/texturecache/3
2011-11-29T04:31:09Z INFO: purgeAllTextures: Deleting files in directory: /home/paulq/.secondlife/cache/texturecache/4
2011-11-29T04:31:09Z INFO: purgeAllTextures: Deleting files in directory: /home/paulq/.secondlife/cache/texturecache/5
2011-11-29T04:31:09Z INFO: purgeAllTextures: Deleting files in directory: /home/paulq/.secondlife/cache/texturecache/6
2011-11-29T04:31:09Z INFO: purgeAllTextures: Deleting files in directory: /home/paulq/.secondlife/cache/texturecache/7
2011-11-29T04:31:09Z INFO: purgeAllTextures: Deleting files in directory: /home/paulq/.secondlife/cache/texturecache/8
2011-11-29T04:31:09Z INFO: purgeAllTextures: Deleting files in directory: /home/paulq/.secondlife/cache/texturecache/9
2011-11-29T04:31:09Z INFO: purgeAllTextures: Deleting files in directory: /home/paulq/.secondlife/cache/texturecache/a
2011-11-29T04:31:09Z INFO: purgeAllTextures: Deleting files in directory: /home/paulq/.secondlife/cache/texturecache/b
2011-11-29T04:31:09Z INFO: purgeAllTextures: Deleting files in directory: /home/paulq/.secondlife/cache/texturecache/c
2011-11-29T04:31:09Z INFO: purgeAllTextures: Deleting files in directory: /home/paulq/.secondlife/cache/texturecache/d
2011-11-29T04:31:09Z INFO: purgeAllTextures: Deleting files in directory: /home/paulq/.secondlife/cache/texturecache/e
2011-11-29T04:31:09Z INFO: purgeAllTextures: Deleting files in directory: /home/paulq/.secondlife/cache/texturecache/f
2011-11-29T04:31:09Z WARNING: ll_apr_warn_status: APR: No such file or directory
2011-11-29T04:31:09Z WARNING: open:  Attempting to open filename: /home/paulq/.secondlife/cache/texturecache/texture.entries
2011-11-29T04:31:09Z INFO: purgeAllTextures: The entire texture cache is cleared.
2011-11-29T04:31:09Z INFO: purgeTextures: TEXTURE CACHE: Purging.
2011-11-29T04:31:09Z INFO: initCache: VFS CACHE SIZE: 102 MB
2011-11-29T04:31:09Z INFO: LLVFS: Attempting to open VFS index file /home/paulq/.secondlife/cache/index.db2.x.671617182
2011-11-29T04:31:09Z INFO: LLVFS: Attempting to open VFS data file /home/paulq/.secondlife/cache/data.db2.x.671617182
2011-11-29T04:31:09Z INFO: presizeDataFile: Pre-sized VFS data file to 106954752 bytes
2011-11-29T04:31:09Z INFO: LLVFS: Using VFS index file /home/paulq/.secondlife/cache/index.db2.x.671617182
2011-11-29T04:31:09Z INFO: LLVFS: Using VFS data file /home/paulq/.secondlife/cache/data.db2.x.671617182
2011-11-29T04:31:09Z INFO: LLVFS: Attempting to open VFS index file /home/paulq/secondlifelinux/app_settings/static_index.db2
2011-11-29T04:31:09Z INFO: LLVFS: Attempting to open VFS data file /home/paulq/secondlifelinux/app_settings/static_data.db2
2011-11-29T04:31:09Z INFO: LLVFS: Using VFS index file /home/paulq/secondlifelinux/app_settings/static_index.db2
2011-11-29T04:31:09Z INFO: LLVFS: Using VFS data file /home/paulq/secondlifelinux/app_settings/static_data.db2
2011-11-29T04:31:09Z INFO: init: Cache initialization is done.
2011-11-29T04:31:09Z INFO: initWindow: Initializing window...
2011-11-29T04:31:09Z INFO: LLViewerWindow: NOTE: ALL NOTIFICATIONS THAT OCCUR WILL GET ADDED TO IGNORE LIST FOR LATER RUNS.
2011-11-29T04:31:09Z INFO: ll_try_gtk_init: Starting GTK Initialization.
2011-11-29T04:31:09Z INFO: ll_try_gtk_init: GTK Initialized.
2011-11-29T04:31:09Z INFO: ll_try_gtk_init: - Compiled against GTK version 2.4.14
2011-11-29T04:31:09Z INFO: ll_try_gtk_init: - Running against GTK version 2.20.1
2011-11-29T04:31:09Z INFO: ll_try_gtk_init: - GTK version is good.
2011-11-29T04:31:09Z INFO: createContext: createContext, fullscreen=0 size=1024x738
2011-11-29T04:31:09Z INFO: createContext: Compiled against SDL 1.2.14
2011-11-29T04:31:09Z INFO: createContext:  Running against SDL 1.2.14
2011-11-29T04:31:09Z INFO: createContext: Original aspect ratio was 1280:800=1.6
2011-11-29T04:31:09Z INFO: createContext: createContext: creating window 1024x738x32
2011-11-29T04:31:09Z WARNING: createContext: createContext: window creation failure. SDL: Couldn't find matching GLX visual
2011-11-29T04:31:09Z INFO: destroyContext: destroyContext begins
2011-11-29T04:31:09Z INFO: destroyContext: shutdownGL begins
2011-11-29T04:31:09Z INFO: destroyContext: SDL_QuitSS/VID begins
2011-11-29T04:31:09Z INFO: OSMessageBoxSDL: Creating a dialog because we're in windowed mode and GTK is happy.

(<unknown>:3565): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so: wrong ELF class: ELFCLASS64

(<unknown>:3565): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so: wrong ELF class: ELFCLASS64

(<unknown>:3565): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so: wrong ELF class: ELFCLASS64

(<unknown>:3565): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so: wrong ELF class: ELFCLASS64

(<unknown>:3565): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so: wrong ELF class: ELFCLASS64

(<unknown>:3565): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so: wrong ELF class: ELFCLASS64

(<unknown>:3565): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so: wrong ELF class: ELFCLASS64

(<unknown>:3565): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so: wrong ELF class: ELFCLASS64

(<unknown>:3565): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so: wrong ELF class: ELFCLASS64

(<unknown>:3565): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so: wrong ELF class: ELFCLASS64

(<unknown>:3565): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so: wrong ELF class: ELFCLASS64

(<unknown>:3565): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so: wrong ELF class: ELFCLASS64

(<unknown>:3565): GdkPixbuf-WARNING **: Bug! loader 'png' didn't set an error on failure

(<unknown>:3565): Gtk-WARNING **: Error loading theme icon 'gtk-dialog-warning' for stock: Internal error: Image loader module 'png' failed to complete an operation, but didn't give a reason for the failure
2011-11-29T04:31:10Z INFO: quitCursors: Skipping quitCursors: mWindow already gone.
2011-11-29T04:31:10Z INFO: destroyContext: destroyContext begins
2011-11-29T04:31:10Z INFO: destroyContext: shutdownGL begins
2011-11-29T04:31:10Z INFO: destroyContext: SDL_QuitSS/VID begins
2011-11-29T04:31:10Z WARNING: createWindow: LLWindowManager::create() : Error creating window.
2011-11-29T04:31:10Z WARNING: LLViewerWindow: Failed to create window, to be shutting Down, be sure your graphics driver is updated.
2011-11-29T04:31:15Z WARNING: LLViewerWindow: Unable to create window, be sure screen is set at 32-bit color and your graphics driver is configured correctly.  See README-linux.txt or README-solaris.txt for further information.
*** Bad shutdown. ***

You are running the Second Life Viewer on a x86_64 platform.  The
most common problems when launching the Viewer (particularly
'bin/do-not-directly-run-secondlife-bin: not found' and 'error while
loading shared libraries') may be solved by installing your Linux
distribution's 32-bit compatibility packages.
For example, on Ubuntu and other Debian-based Linuxes you might run:
$ sudo apt-get install ia32-libs ia32-libs-gtk ia32-libs-kde ia32-libs-sdl

```

my output from sudo fgrep NVRM /var/log/messages is:
```
Nov 28 20:37:12 futant kernel: [    7.620886] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  195.36.31  Thu Jun  3 08:19:50 PDT 2010
Nov 28 21:26:46 futant kernel: [    7.455789] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  290.10  Wed Nov 16 17:39:29 PST 2011
Nov 28 22:54:40 futant kernel: [ 5286.989557] NVRM: API mismatch: the client has the version 195.36.31, but
Nov 28 22:54:40 futant kernel: [ 5286.989558] NVRM: this kernel module has the version 290.10.  Please
Nov 28 22:54:40 futant kernel: [ 5286.989559] NVRM: make sure that this kernel module and all NVIDIA driver
Nov 28 22:54:40 futant kernel: [ 5286.989561] NVRM: components have the same version.
Nov 28 22:54:43 futant kernel: [ 5290.090562] NVRM: API mismatch: the client has the version 195.36.31, but
Nov 28 22:54:43 futant kernel: [ 5290.090563] NVRM: this kernel module has the version 290.10.  Please
Nov 28 22:54:43 futant kernel: [ 5290.090565] NVRM: make sure that this kernel module and all NVIDIA driver
Nov 28 22:54:43 futant kernel: [ 5290.090566] NVRM: components have the same version.
Nov 28 22:54:47 futant kernel: [ 5293.181013] NVRM: API mismatch: the client has the version 195.36.31, but
Nov 28 22:54:47 futant kernel: [ 5293.181015] NVRM: this kernel module has the version 290.10.  Please
Nov 28 22:54:47 futant kernel: [ 5293.181016] NVRM: make sure that this kernel module and all NVIDIA driver
Nov 28 22:54:47 futant kernel: [ 5293.181017] NVRM: components have the same version.
Nov 28 22:56:05 futant kernel: [    7.694608] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  195.36.31  Thu Jun  3 08:19:50 PDT 2010

```

my output from dpkg -l | grep nvidia is:
```
ii  libgl1-nvidia-alternatives               195.36.31-6                         simplifies replacing MESA libGL with GPU vendor libraries
ii  libgl1-nvidia-glx                        195.36.31-6                         NVIDIA binary OpenGL libraries
ii  libglx-nvidia-alternatives               195.36.31-6                         simplifies replacing Xorg module libglx.so with GPU vendor library
ii  nvidia-glx                               195.36.31-6                         NVIDIA binary Xorg driver
rc  nvidia-installer-cleanup                 20111111+1                          Cleanup after driver installation with the nvidia-installer
ii  nvidia-kernel-2.6.32-5-amd64             195.36.31-6+2.6.32-38               NVIDIA binary kernel module for Linux 2.6.32-5-amd64
ii  nvidia-kernel-common                     20100522+1                          NVIDIA binary kernel module support files
ii  nvidia-kernel-source                     195.36.31-6                         NVIDIA binary kernel module source
rc  nvidia-settings                          290.10-1                            Tool for configuring the NVIDIA graphics driver
rc  nvidia-support                           20111111+1                          NVIDIA binary graphics driver support files
ii  nvidia-vdpau-driver                      195.36.31-6                         NVIDIA vdpau driver

```

please help if you can. thanks much.

```

```

---

### Post by paulqueen on 2011-11-29
bumping for help!

---

### Post by paulqueen on 2011-11-30
please anyhow have a clue what i need to do to get this working?

i have spent the last three days searching sites and trying stuff to no avail.

im not a linux genius by any means, just a noob. a noob who needs help.

thanks and bump

---

### Post by typhoon_tip on 2011-11-30
Have you read your own error message at the last row ?

Try to run this command:
```
sudo apt-get install ia32-libs ia32-libs-gtk ia32-libs-kde ia32-libs-sdl
```

32 bits compatibility packs for 64 bit version. Run that command (maybe it will install a lot of things) and try again.

---

### Post by scarleo on 2011-11-30
It seems to me that you also have two different versions of the driver installed. I don't have any experience from NVIDIA with Ubuntu but it doesn't sound like a good thing to have. Maybe try remove the older version.

---

### Post by typhoon_tip on 2011-11-30
> **scarleo said:**
> It seems to me that you also have two different versions of the driver installed. I don't have any experience from NVIDIA with Ubuntu but it doesn't sound like a good thing to have. Maybe try remove the older version.

It seems correct to me. Most likely are only the 32 bits libraries missing, because on a 64 bits machine they are necessary to run 32 bits apps.

---

### Post by paulqueen on 2011-11-30
> **typhoon_tip said:**
> Have you read your own error message at the last row ?

Try to run this command:
```
sudo apt-get install ia32-libs ia32-libs-gtk ia32-libs-kde ia32-libs-sdl
```

32 bits compatibility packs for 64 bit version. Run that command (maybe it will install a lot of things) and try again.



hmm not sure how i missed that ... thanks. i will give it a shot tomorrow afternoon and post my results. i am so hoping this oversight you pointed out to me is the quick solution to all of this.

as for two different versions of drivers i dont know how to uninstall them? ive ran 'rmmod nvidia' a couple times after trying different drivers to no avail.

---

### Post by scarleo on 2011-11-30
> **typhoon_tip said:**
> It seems correct to me. Most likely are only the 32 bits libraries missing, because on a 64 bits machine they are necessary to run 32 bits apps.

Ok, you are probably right, just to be clear I was referring to this part which made me say it seems like two different versions are installed:

```

NVRM: loading NVIDIA UNIX x86_64 Kernel Module  195.36.31  Thu Jun  3 08:19:50 PDT 2010 
NVRM: loading NVIDIA UNIX x86_64 Kernel Module  290.10  Wed Nov 16 17:39:29 PST 2011 
NVRM: API mismatch: the client has the version 195.36.31, but 
NVRM: this kernel module has the version 290.10.  Please 
NVRM: make sure that this kernel module and all NVIDIA driver 
NVRM: components have the same version.

```

---

### Post by typhoon_tip on 2011-11-30
> **scarleo said:**
> Ok, you are probably right, just to be clear I was referring to this part which made me say it seems like two different versions are installed:

```

NVRM: loading NVIDIA UNIX x86_64 Kernel Module  195.36.31  Thu Jun  3 08:19:50 PDT 2010 
NVRM: loading NVIDIA UNIX x86_64 Kernel Module  290.10  Wed Nov 16 17:39:29 PST 2011 
NVRM: API mismatch: the client has the version 195.36.31, but 
NVRM: this kernel module has the version 290.10.  Please 
NVRM: make sure that this kernel module and all NVIDIA driver 
NVRM: components have the same version.

```

Yup, understood don't worry. :) It seems happening in Ubuntu after installing post-upgrade updates. If that was the case, conflicting driver, I think entire system would crash at start.

---

### Post by paulqueen on 2011-12-01
> **typhoon_tip said:**
> Yup, understood don't worry. :) It seems happening in Ubuntu after installing post-upgrade updates. If that was the case, conflicting driver, I think entire system would crash at start.


```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package ia32-libs-kde
E: Unable to locate package ia32-libs-sdl

```

so F%#@... now what? i tried adding some debian squeeze repositories to no avail. seirously im just a noob at this linux thing .. i cut my teeth a little but im tryin to learn more

---

### Post by typhoon_tip on 2011-12-01
> **paulqueen said:**
> ```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package ia32-libs-kde
E: Unable to locate package ia32-libs-sdl

```

so F%#@... now what? i tried adding some debian squeeze repositories to no avail. seirously im just a noob at this linux thing .. i cut my teeth a little but im tryin to learn more

No panic, don't worry :) But, do not mess around with sources, they can led to self-destruction of the system ! First of all, get back to the original state of Software sources (you can tick/untick specific sources to activate/deactivate them). Make sure you have enabled partners as well.

Then, before installing, run this command:
```
sudo apt-get update
```

Then again:
```
sudo apt-get install ia32-libs ia32-libs-gtk ia32-libs-kde ia32-libs-sdl
```

Post result of first command if any error arise.

---

### Post by paulqueen on 2011-12-01
> **typhoon_tip said:**
> No panic, don't worry :) But, do not mess around with sources, they can led to self-destruction of the system ! First of all, get back to the original state of Software sources (you can tick/untick specific sources to activate/deactivate them). Make sure you have enabled partners as well.

Then, before installing, run this command:
```
sudo apt-get update
```

Then again:
```
sudo apt-get install ia32-libs ia32-libs-gtk ia32-libs-kde ia32-libs-sdl
```

Post result of first command if any error arise.



i already tried that.... it didnt find the sdl and the kde ones, it did install the others though.. or maybe just gtk and i had the regular libs already. either way, couldnt find kde or sdl

---

### Post by paulqueen on 2011-12-02
after running 'sudo apt-get update' i then ran 'sudo apt-get install ia32-libs ia32-libs-gtk ia32-libs-kde ia32-libs-sdl' and got this:

```

paulq@futant:~$ sudo apt-get install ia32-libs ia32-libs-gtk ia32-libs-kde ia32-libs-sdl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package ia32-libs-kde
E: Unable to locate package ia32-libs-sdl

```


???????

---

### Post by typhoon_tip on 2011-12-02
I think you messed up heavily your sources file, only option you have is to return to the default ones.

I cannot give you mine because I am in China, so I use local modified sources to access fast local mirrors. Somebody please post a default sources.list file so he can replace his file.

After replacing sources.list file, run
```
sudo apt-get update
sudo apt-get upgrade
```

Before doing anything else.

---

### Post by typhoon_tip on 2011-12-02
Wait, before doing that, I have an idea, try to run this one instead of the suggested command:

```
sudo apt-get install ia32-libs ia32-libs-gtk
```

It should run... and install several hundred megabytes of libraries.

---

### Post by paulqueen on 2011-12-04
> **typhoon_tip said:**
> Wait, before doing that, I have an idea, try to run this one instead of the suggested command:

```
sudo apt-get install ia32-libs ia32-libs-gtk
```

It should run... and install several hundred megabytes of libraries.


thanks but it didn't work. apparently i already have those installed and up to date. second life still gives me the same message. =\


```
paulq@futant:~$ sudo apt-get install ia32-libs ia32-libs-gtk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ia32-libs-gtk is already the newest version.
ia32-libs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```


am i just s.o.l?

---

### Post by paulqueen on 2011-12-06
i fixed it ... by giving in and installing the latest ubuntu =\

much to my chagrin i have admitted defeat and upgraded ... and im not sure if i like it. it seems a bit of a resource hog, but i guess i have to give it time to tweak it out and stuff before fully judging.

either way, secondlife worked instantly after installing the 32bit libraries this time. so that is a plus.

thanks for offering help everyone!

---

### Post by typhoon_tip on 2011-12-06
Which version were you using before ? I thought it was already the latest... Sorry for not asking.

---

### Post by typhoon_tip on 2011-12-06
> **scarleo said:**
> Ok, you are probably right, just to be clear I was referring to this part which made me say it seems like two different versions are installed:

```

NVRM: loading NVIDIA UNIX x86_64 Kernel Module  195.36.31  Thu Jun  3 08:19:50 PDT 2010 
NVRM: loading NVIDIA UNIX x86_64 Kernel Module  290.10  Wed Nov 16 17:39:29 PST 2011 
NVRM: API mismatch: the client has the version 195.36.31, but 
NVRM: this kernel module has the version 290.10.  Please 
NVRM: make sure that this kernel module and all NVIDIA driver 
NVRM: components have the same version.

```

Since he didn't have Ubuntu 11.10 as I was implicitly thinking... you may as well been right, there was a dual version driver installation messed up ! :popcorn:

---

### Post by theasprint on 2011-12-06
Solved already?

Owhkayy...

---

