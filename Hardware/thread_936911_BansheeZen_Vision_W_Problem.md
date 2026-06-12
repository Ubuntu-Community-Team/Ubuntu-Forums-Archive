---
title: "Banshee/Zen Vision W Problem"
date: 2008-10-03
forum: Hardware
---

### Post by Jmeyering on 2008-10-03
I'm trying to connect my Creative Zen vision w to Banshee and when I do banshee just quits on me, when ran in terminal this is the error I get. I'm running Intrepid Alpha 6. 

jared@jared-laptop:~$ banshee
[Info  09:00:31.422] Running Banshee 1.2.1
[Info  09:00:33.573] All services are started 1.925148s
[Info  09:00:34.891] nereid Client Started
PTP: Opening session
Stacktrace:

  at (wrapper managed-to-native) System.Object.__icall_wrapper_mono_string_new_wrapper (intptr) <0x00004>
  at (wrapper managed-to-native) System.Object.__icall_wrapper_mono_string_new_wrapper (intptr) <0xffffffff>
  at (wrapper unknown) Mtp.FolderStruct.PtrToStructure (intptr,object) <0xffffffff>
  at (wrapper runtime-invoke) Mtp.MtpDeviceStruct.runtime_invoke_void_intptr_object (object,intptr,intptr,intptr) <0xffffffff>
  at (wrapper managed-to-native) System.Runtime.InteropServices.Marshal.PtrToStructure (intptr,System.Type) <0x00004>
  at (wrapper managed-to-native) System.Runtime.InteropServices.Marshal.PtrToStructure (intptr,System.Type) <0xffffffff>
  at Mtp.Folder.GetRootFolders (Mtp.MtpDevice) <0x00072>
  at Mtp.MtpDevice.GetRootFolders () <0x0000a>
  at Mtp.MtpDevice.SetDefaultFolders () <0x0001e>
  at Mtp.MtpDevice..ctor (Mtp.MtpDeviceHandle,Mtp.MtpDeviceStruct) <0x00039>
  at Mtp.MtpDevice..ctor (intptr,bool,Mtp.MtpDeviceStruct) <0x0004b>
  at Mtp.MtpDevice.Detect () <0x000c3>
  at Banshee.Dap.Mtp.MtpSource.DeviceInitialize (Banshee.Hardware.IDevice) <0x000c7>
  at Banshee.Dap.DapService.FindDeviceSource (Banshee.Hardware.IDevice) <0x000a5>
  at <>c__CompilerGenerated1.<MapDevice>c__6 () <0x0040b>
  at Banshee.Kernel.DelegateJob.RunJob () <0x0000c>
  at Banshee.Kernel.Job.Run () <0x0000b>
  at Banshee.Kernel.Scheduler.ProcessJobThread () <0x0014f>
  at (wrapper runtime-invoke) System.Object.runtime_invoke_void (object,intptr,intptr,intptr) <0xffffffff>

Native stacktrace:

	banshee-1 [0x817d3de]
	banshee-1 [0x807f78b]
	[0xb7f65410]
	banshee-1(mono_string_new_wrapper+0x23) [0x809cac3]
	[0xb5068f47]
	[0xb39c0e73]
	[0xb39c055b]
	banshee-1 [0x80c6728]
	[0xb503392a]
	[0xb39c0acb]
	[0xb39c0a43]
	[0xb39c08bf]
	[0xb39c06c2]
	[0xb39c0634]
	[0xb3db118c]
	[0xb3daf998]
	[0xb3dae00e]
	[0xb3f38c34]
	[0xb3f3629d]
	[0xb3f3627c]
	[0xb3f35f30]
	[0xb79d6059]
	banshee-1(mono_runtime_delegate_invoke+0x35) [0x8098c55]
	banshee-1 [0x80d620f]
	banshee-1 [0x8127f4e]
	banshee-1 [0x81404b5]
	/lib/tls/i686/cmov/libpthread.so.0 [0xb7e5c50f]
	/lib/tls/i686/cmov/libc.so.6(clone+0x5e) [0xb7db37ee]

Debug info from gdb:

(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 0xb7ca66d0 (LWP 9741)]
[New Thread 0xb3ebbb90 (LWP 9768)]
[New Thread 0xb3b64b90 (LWP 9760)]
[New Thread 0xb3c6fb90 (LWP 9759)]
[New Thread 0xb3d74b90 (LWP 9758)]
[New Thread 0xb475fb90 (LWP 9753)]
[New Thread 0xb4864b90 (LWP 9752)]
[New Thread 0xb4969b90 (LWP 9751)]
[New Thread 0xb6370b90 (LWP 9744)]
[New Thread 0xb747cb90 (LWP 9743)]
[New Thread 0xb7a1fb90 (LWP 9742)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
0xb7f65430 in __kernel_vsyscall ()
  11 Thread 0xb7a1fb90 (LWP 9742)  0xb7f65430 in __kernel_vsyscall ()
  10 Thread 0xb747cb90 (LWP 9743)  0xb7f65430 in __kernel_vsyscall ()
  9 Thread 0xb6370b90 (LWP 9744)  0xb7f65430 in __kernel_vsyscall ()
  8 Thread 0xb4969b90 (LWP 9751)  0xb7f65430 in __kernel_vsyscall ()
  7 Thread 0xb4864b90 (LWP 9752)  0xb7f65430 in __kernel_vsyscall ()
  6 Thread 0xb475fb90 (LWP 9753)  0xb7f65430 in __kernel_vsyscall ()
  5 Thread 0xb3d74b90 (LWP 9758)  0xb7f65430 in __kernel_vsyscall ()
  4 Thread 0xb3c6fb90 (LWP 9759)  0xb7f65430 in __kernel_vsyscall ()
  3 Thread 0xb3b64b90 (LWP 9760)  0xb7f65430 in __kernel_vsyscall ()
  2 Thread 0xb3ebbb90 (LWP 9768)  0xb7f65430 in __kernel_vsyscall ()
  1 Thread 0xb7ca66d0 (LWP 9741)  0xb7f65430 in __kernel_vsyscall ()

Thread 11 (Thread 0xb7a1fb90 (LWP 9742)):
#0  0xb7f65430 in __kernel_vsyscall ()
#1  0xb7e63906 in nanosleep () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081114a8 in ?? ()
#3  0xb7e5c50f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#4  0xb7db37ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 10 (Thread 0xb747cb90 (LWP 9743)):
#0  0xb7f65430 in __kernel_vsyscall ()
#1  0xb7e60075 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08114897 in ?? ()
#3  0x08116ecc in ?? ()
#4  0x08116f0c in ?? ()
#5  0x08129b6a in ?? ()
#6  0x080b5c6a in ?? ()
#7  0x080d61a4 in ?? ()
#8  0x08127f4e in ?? ()
#9  0x081404b5 in ?? ()
#10 0xb7e5c50f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#11 0xb7db37ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 9 (Thread 0xb6370b90 (LWP 9744)):
#0  0xb7f65430 in __kernel_vsyscall ()
#1  0xb7e603a2 in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08114848 in ?? ()
#3  0x08116ecc in ?? ()
#4  0x08116f0c in ?? ()
#5  0x08129b6a in ?? ()
#6  0x080d3243 in ?? ()
#7  0xb598caa2 in ?? ()
#8  0xb598c94b in ?? ()
#9  0xb6380220 in ?? ()
#10 0xb79d6059 in ?? ()
#11 0x08098c55 in mono_runtime_delegate_invoke ()
#12 0x080d620f in ?? ()
#13 0x08127f4e in ?? ()
#14 0x081404b5 in ?? ()
#15 0xb7e5c50f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#16 0xb7db37ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 8 (Thread 0xb4969b90 (LWP 9751)):
#0  0xb7f65430 in __kernel_vsyscall ()
#1  0xb7e603a2 in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08114848 in ?? ()
#3  0x08114912 in ?? ()
#4  0x08129fb5 in ?? ()
#5  0x080d4e09 in ?? ()
#6  0xb4a3dbcf in ?? ()
#7  0xb4a3d94f in ?? ()
#8  0xb4a3d75f in ?? ()
#9  0xb4a3d64e in ?? ()
#10 0x0809e8e3 in mono_runtime_invoke_array ()
#11 0x0809ea74 in ?? ()
#12 0x080d9223 in ?? ()
#13 0x080d9650 in ?? ()
#14 0x080d61a4 in ?? ()
#15 0x08127f4e in ?? ()
#16 0x081404b5 in ?? ()
#17 0xb7e5c50f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#18 0xb7db37ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 7 (Thread 0xb4864b90 (LWP 9752)):
#0  0xb7f65430 in __kernel_vsyscall ()
#1  0xb7e603a2 in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08114848 in ?? ()
#3  0x08114912 in ?? ()
#4  0x08129fb5 in ?? ()
#5  0x080d4e09 in ?? ()
#6  0xb4a3dbcf in ?? ()
#7  0xb4a3d94f in ?? ()
#8  0xb4a3d75f in ?? ()
#9  0xb4a3d64e in ?? ()
#10 0x0809e8e3 in mono_runtime_invoke_array ()
#11 0x0809ea74 in ?? ()
#12 0x080d9223 in ?? ()
#13 0x080d9650 in ?? ()
#14 0x080d61a4 in ?? ()
#15 0x08127f4e in ?? ()
#16 0x081404b5 in ?? ()
#17 0xb7e5c50f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#18 0xb7db37ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 6 (Thread 0xb475fb90 (LWP 9753)):
#0  0xb7f65430 in __kernel_vsyscall ()
#1  0xb7e603a2 in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08114848 in ?? ()
#3  0x08114912 in ?? ()
#4  0x08129fb5 in ?? ()
#5  0x080d4e09 in ?? ()
#6  0xb4a3dbcf in ?? ()
#7  0xb4a3d94f in ?? ()
#8  0xb4a3d75f in ?? ()
#9  0xb4a3d64e in ?? ()
#10 0x0809e8e3 in mono_runtime_invoke_array ()
#11 0x0809ea74 in ?? ()
#12 0x080d9223 in ?? ()
#13 0x080d9650 in ?? ()
#14 0x080d61a4 in ?? ()
#15 0x08127f4e in ?? ()
#16 0x081404b5 in ?? ()
#17 0xb7e5c50f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#18 0xb7db37ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 5 (Thread 0xb3d74b90 (LWP 9758)):
#0  0xb7f65430 in __kernel_vsyscall ()
#1  0xb7da8f77 in poll () from /lib/tls/i686/cmov/libc.so.6
#2  0xb3da5629 in ?? ()
#3  0xb3da55d5 in ?? ()
#4  0x09fb4c5a in ?? ()
#5  0xb3d8ca4d in avahi_simple_poll_run () from /usr/lib/libavahi-common.so.3
#6  0xb3d8d320 in avahi_simple_poll_iterate ()
   from /usr/lib/libavahi-common.so.3
#7  0xb3d8d370 in avahi_simple_poll_loop () from /usr/lib/libavahi-common.so.3
#8  0xb3da5593 in ?? ()
#9  0xb3da54ca in ?? ()
#10 0xb79d6059 in ?? ()
#11 0x08098c55 in mono_runtime_delegate_invoke ()
#12 0x080d620f in ?? ()
#13 0x08127f4e in ?? ()
#14 0x081404b5 in ?? ()
#15 0xb7e5c50f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#16 0xb7db37ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 4 (Thread 0xb3c6fb90 (LWP 9759)):
#0  0xb7f65430 in __kernel_vsyscall ()
#1  0xb7e63328 in accept () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08124e79 in ?? ()
#3  0x080ddd4b in ?? ()
#4  0xb3dad8fa in ?? ()
#5  0xb3dad70f in ?? ()
#6  0xb3dad5f6 in ?? ()
#7  0xb79d6059 in ?? ()
#8  0x08098c55 in mono_runtime_delegate_invoke ()
#9  0x080d620f in ?? ()
#10 0x08127f4e in ?? ()
#11 0x081404b5 in ?? ()
#12 0xb7e5c50f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#13 0xb7db37ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 3 (Thread 0xb3b64b90 (LWP 9760)):
#0  0xb7f65430 in __kernel_vsyscall ()
#1  0xb7da8f77 in poll () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7eafc32 in ?? () from /usr/lib/libglib-2.0.so.0
#3  0xb7eb02c2 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#4  0xb510d8b0 in ?? () from /usr/lib/libORBit-2.so.0
#5  0xb7ed705f in ?? () from /usr/lib/libglib-2.0.so.0
#6  0xb7e5c50f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#7  0xb7db37ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 2 (Thread 0xb3ebbb90 (LWP 9768)):
#0  0xb7f65430 in __kernel_vsyscall ()
#1  0xb7dabc01 in select () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7ee59bb in g_spawn_sync () from /usr/lib/libglib-2.0.so.0
#3  0xb7ee5d6c in g_spawn_command_line_sync () from /usr/lib/libglib-2.0.so.0
#4  0x0817d495 in ?? ()
#5  0x0807f78b in ?? ()
#6  <signal handler called>
#7  0xb7d492c3 in strlen () from /lib/tls/i686/cmov/libc.so.6
#8  0x0809ca3a in mono_string_new ()
#9  0x0809cac3 in mono_string_new_wrapper ()
#10 0xb5068f47 in ?? ()
#11 0xb39c0e73 in ?? ()
#12 0xb39c055b in ?? ()
#13 0x080c6728 in ?? ()
#14 0xb503392a in ?? ()
#15 0xb39c0acb in ?? ()
#16 0xb39c0a43 in ?? ()
#17 0xb39c08bf in ?? ()
#18 0xb39c06c2 in ?? ()
#19 0xb39c0634 in ?? ()
#20 0xb3db118c in ?? ()
#21 0xb3daf998 in ?? ()
#22 0xb3dae00e in ?? ()
#23 0xb3f38c34 in ?? ()
#24 0xb3f3629d in ?? ()
#25 0xb3f3627c in ?? ()
#26 0xb3f35f30 in ?? ()
#27 0xb79d6059 in ?? ()
#28 0x08098c55 in mono_runtime_delegate_invoke ()
#29 0x080d620f in ?? ()
#30 0x08127f4e in ?? ()
#31 0x081404b5 in ?? ()
#32 0xb7e5c50f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#33 0xb7db37ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 1 (Thread 0xb7ca66d0 (LWP 9741)):
#0  0xb7f65430 in __kernel_vsyscall ()
#1  0xb7da8f77 in poll () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7eafc32 in ?? () from /usr/lib/libglib-2.0.so.0
#3  0xb7eb02c2 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#4  0xb6c37299 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#5  0xb3fcb1de in ?? ()
#6  0xb3fcb1a8 in ?? ()
#7  0xb3fcaf4b in ?? ()
#8  0xb6eaf56d in ?? ()
#9  0xb6eaf453 in ?? ()
#10 0xb6eaf35a in ?? ()
#11 0xb79d40c4 in ?? ()
#12 0xb79c81c3 in ?? ()
#13 0x0809cb86 in mono_runtime_exec_main ()
#14 0x0809d1ab in mono_runtime_run_main ()
#15 0x0805aeee in mono_main ()
#16 0x0805a3f2 in ?? ()
#17 0xb7ce8685 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#18 0x0805a331 in ?? ()
#0  0xb7f65430 in __kernel_vsyscall ()


=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Aborted (core dumped)


Any Help would be greatly appreciated! thanks!

---

### Post by tgalati4 on 2008-10-03
>banshee --debug

will hopefully give more information before the dump.

---

### Post by Jmeyering on 2008-10-03
When I ran banshee with debug I got this

jared@jared-laptop:~$ banshee --debug
** Running Mono with --debug   **
[Debug 14:45:31.308] NDesk.DBus.Bus.Session.RequestName ('org.bansheeproject.Banshee') => PrimaryOwner
[Info  14:45:31.325] Running Banshee 1.2.1
[Debug 14:45:32.513] Core service started (DBusServiceManager, 0.002023s)
[Debug 14:45:32.533] Core service started (DBusCommandService, 0.018332s)
[Debug 14:45:32.622] Opened SQLite connection to /home/jared/.config/banshee-1/banshee.db
[Debug 14:45:32.623] Core service started (DbConnection, 0.09003s)
[Debug 14:45:32.636] Database version 17 is up to date
[Debug 14:45:32.659] Core service started (PreferenceService, 0.017399s)
[Debug 14:45:32.662] Core service started (SourceManager, 0.002288s)
[Debug 14:45:32.892] Core service started (MediaProfileManager, 0.23028s)
[Debug 14:45:32.897] Core service started (PlayerEngine, 0.004013s)
[Debug 14:45:32.906] Configuration client extension loaded (Banshee.GnomeBackend.GConfConfigurationClient)
[Debug 14:45:32.996] IO provider extension loaded (Banshee.IO.Unix.Provider)
[Debug 14:45:33.006] Core service started (TranscoderService, 0.013991s)
[Debug 14:45:33.010] Core service started (PlaybackController, 0.003527s)
[Debug 14:45:33.011] Core service started (ImportSourceManager, 0.000581s)
[Debug 14:45:33.019] Core service started (LibraryImportManager, 0.007585s)
[Debug 14:45:33.042] Core service started (UserJobManager, 0.000767s)
[Debug 14:45:33.084] Core service started (HardwareManager, 0.040265s)
[Debug 14:45:33.138] Adding icon theme search path: /usr/share/banshee-1/icons
[Debug 14:45:33.139] Core service started (GtkElementsService, 0.054326s)
[Debug 14:45:33.230] Core service started (InterfaceActionService, 0.090599s)
[Debug 14:45:33.231] Album artwork path set to /home/jared/.cache/album-art
[Debug 14:45:33.231] Core service started (ArtworkManager, 0.001252s)
[Debug 14:45:33.983] Core service started (NereidPlayerInterface, 0.751748s)
[Debug 14:45:33.987] Extension service started (DapService, 0.002049s)
[Debug 14:45:33.989] Extension service started (DaapService, 0.001401s)
[Debug 14:45:34.004] Using GNOME 2.22 API for Multimedia Keys
[Debug 14:45:34.004] Extension service started (MultimediaKeysService, 0.014593s)
[Debug 14:45:34.041] Extension service started (BookmarksService, 0.036314s)
[Debug 14:45:34.047] Extension service started (CoverArtService, 0.0061s)
[Debug 14:45:34.050] Extension service started (MiniModeService, 0.002938s)
[Debug 14:45:34.213] Extension service started (NotificationAreaService, 0.162814s)
[Debug 14:45:34.330] Extension service started (AudioCdService, 0.102836s)
[Debug 14:45:34.386] Extension service started (LastfmRecommendationService, 0.049492s)
[Debug 14:45:34.405] Audioscrobbler state: connected
[Debug 14:45:34.431] Extension service started (AudioscrobblerService, 0.039402s)
[Debug 14:45:34.436] Extension service started (GnomeService, 0.004671s)
[Debug 14:45:34.442] Extension service started (BooScriptService, 0.00471s)
[Debug 14:45:34.724] Extension service started (PodcastService, 0.277638s)
[Debug 14:45:34.865] GStreamer pipeline does not run: audioconvert ! lame mode=4 bitrate=128 ! id3v2mux
[Debug 14:45:34.866] GStreamer pipeline does not run: audioconvert ! xingenc bitrate=128 ! id3v2mux
[Debug 14:45:34.965] GStreamer pipeline does not run: audioconvert ! fluwmaenc bitrate=64000 vbr=false ! fluasfmux
[Debug 14:45:34.966] Extension service started (GStreamerCoreService, 0.240805s)
[Debug 14:45:35.018] Player state change: NotReady -> Ready
[Debug 14:45:35.051] Player state change: Ready -> Idle
[Info  14:45:35.061] All services are started 2.553737s
[Debug 14:45:35.598] Loaded IScreensaverManager: Banshee.GnomeBackend.GnomeScreensaverManager
[Info  14:45:36.205] nereid Client Started
[Debug 14:45:36.255] Dap support extension loaded: Banshee.Dap.Mtp
[Debug 14:45:36.479] Dap support extension loaded: Banshee.Dap.Ipod
[Debug 14:45:36.700] Found DAAP share Big Pimpin_PW, trying to resolve...
[Debug 14:45:36.703] Found DAAP share Podcasts (jjob), trying to resolve...
[Debug 14:45:36.930] Managed to resolve DAAP share Big Pimpin_PW.
[Debug 14:45:36.962] OnServiceResolved provided 10.7.5.180
[Debug 14:45:36.967] Using address 10.7.5.180
[Debug 14:45:36.979] Managed to resolve DAAP share Podcasts (jjob).
[Debug 14:45:36.981] OnServiceResolved provided 10.7.1.161
[Debug 14:45:36.981] Using address 10.7.1.161



Then When I try to connect I get this right after that.


PTP: Opening session
Stacktrace:

  at (wrapper managed-to-native) System.Object.__icall_wrapper_mono_string_new_wrapper (intptr) <0x00004>
  at (wrapper managed-to-native) System.Object.__icall_wrapper_mono_string_new_wrapper (intptr) <0xffffffff>
  at (wrapper unknown) Mtp.FolderStruct.PtrToStructure (intptr,object) <0xffffffff>
  at (wrapper runtime-invoke) Mtp.MtpDeviceStruct.runtime_invoke_void_intptr_object (object,intptr,intptr,intptr) <0xffffffff>
  at (wrapper managed-to-native) System.Runtime.InteropServices.Marshal.PtrToStructure (intptr,System.Type) <0x00004>
  at (wrapper managed-to-native) System.Runtime.InteropServices.Marshal.PtrToStructure (intptr,System.Type) <0xffffffff>
  at Mtp.Folder.GetRootFolders (Mtp.MtpDevice) [0x0001e] in /build/buildd/banshee-1.2.1/src/Libraries/Mtp/Mtp/Folder.cs:123
  at Mtp.MtpDevice.GetRootFolders () [0x00000] in /build/buildd/banshee-1.2.1/src/Libraries/Mtp/Mtp/MtpDevice.cs:164
  at Mtp.MtpDevice.SetDefaultFolders () [0x00000] in /build/buildd/banshee-1.2.1/src/Libraries/Mtp/Mtp/MtpDevice.cs:133
  at Mtp.MtpDevice..ctor (Mtp.MtpDeviceHandle,Mtp.MtpDeviceStruct) [0x00025] in /build/buildd/banshee-1.2.1/src/Libraries/Mtp/Mtp/MtpDevice.cs:118
  at Mtp.MtpDevice..ctor (intptr,bool,Mtp.MtpDeviceStruct) [0x00000] in /build/buildd/banshee-1.2.1/src/Libraries/Mtp/Mtp/MtpDevice.cs:122
  at Mtp.MtpDevice.Detect () [0x0002d] in /build/buildd/banshee-1.2.1/src/Libraries/Mtp/Mtp/MtpDevice.cs:261
  at Banshee.Dap.Mtp.MtpSource.DeviceInitialize (Banshee.Hardware.IDevice) [0x00059] in /build/buildd/banshee-1.2.1/src/Dap/Banshee.Dap.Mtp/Banshee.Dap.Mtp/MtpSource.cs:85
  at Banshee.Dap.DapService.FindDeviceSource (Banshee.Hardware.IDevice) [0x00025] in /build/buildd/banshee-1.2.1/src/Dap/Banshee.Dap/Banshee.Dap/DapService.cs:127
  at <>c__CompilerGenerated1.<MapDevice>c__6 () [0x000b6] in /build/buildd/banshee-1.2.1/src/Dap/Banshee.Dap/Banshee.Dap/DapService.cs:163
  at Banshee.Kernel.DelegateJob.RunJob () [0x00000] in /build/buildd/banshee-1.2.1/src/Core/Banshee.Core/Banshee.Kernel/DelegateJob.cs:45
  at Banshee.Kernel.Job.Run () [0x00000] in /build/buildd/banshee-1.2.1/src/Core/Banshee.Core/Banshee.Kernel/Job.cs:39
  at Banshee.Kernel.Scheduler.ProcessJobThread () [0x000a5] in /build/buildd/banshee-1.2.1/src/Core/Banshee.Core/Banshee.Kernel/Scheduler.cs:234
  at (wrapper runtime-invoke) System.Object.runtime_invoke_void (object,intptr,intptr,intptr) <0xffffffff>

Native stacktrace:

	banshee-1 [0x817d3de]
	banshee-1 [0x807f78b]
	[0xb7f01410]
	banshee-1(mono_string_new_wrapper+0x23) [0x809cac3]
	[0xb600766f]
	[0xb39adcc3]
	[0xb39ad3ab]
	banshee-1 [0x80c6728]
	[0xb603efca]
	[0xb39ad91b]
	[0xb39ad893]
	[0xb39ad70f]
	[0xb39ad512]
	[0xb39ad484]
	[0xb39ad0fc]
	[0xb39a7088]
	[0xb39a66c6]
	[0xb3c4ce6f]
	[0xb3c4a4d5]
	[0xb3c4a4b4]
	[0xb3c4a168]
	[0xb7972059]
	banshee-1(mono_runtime_delegate_invoke+0x35) [0x8098c55]
	banshee-1 [0x80d620f]
	banshee-1 [0x8127f4e]
	banshee-1 [0x81404b5]
	/lib/tls/i686/cmov/libpthread.so.0 [0xb7df850f]
	/lib/tls/i686/cmov/libc.so.6(clone+0x5e) [0xb7d4f7ee]

Debug info from gdb:

(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 0xb7c426d0 (LWP 11108)]
[New Thread 0xb3bfeb90 (LWP 11214)]
[New Thread 0xb3894b90 (LWP 11135)]
[New Thread 0xb39a4b90 (LWP 11134)]
[New Thread 0xb3ab9b90 (LWP 11133)]
[New Thread 0xb44bcb90 (LWP 11123)]
[New Thread 0xb45d1b90 (LWP 11122)]
[New Thread 0xb46d6b90 (LWP 11121)]
[New Thread 0xb6232b90 (LWP 11114)]
[New Thread 0xb7418b90 (LWP 11110)]
[New Thread 0xb79bbb90 (LWP 11109)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
0xb7f01430 in __kernel_vsyscall ()
  11 Thread 0xb79bbb90 (LWP 11109)  0xb7f01430 in __kernel_vsyscall ()
  10 Thread 0xb7418b90 (LWP 11110)  0xb7f01430 in __kernel_vsyscall ()
  9 Thread 0xb6232b90 (LWP 11114)  0xb7f01430 in __kernel_vsyscall ()
  8 Thread 0xb46d6b90 (LWP 11121)  0xb7f01430 in __kernel_vsyscall ()
  7 Thread 0xb45d1b90 (LWP 11122)  0xb7f01430 in __kernel_vsyscall ()
  6 Thread 0xb44bcb90 (LWP 11123)  0xb7f01430 in __kernel_vsyscall ()
  5 Thread 0xb3ab9b90 (LWP 11133)  0xb7f01430 in __kernel_vsyscall ()
  4 Thread 0xb39a4b90 (LWP 11134)  0xb7f01430 in __kernel_vsyscall ()
  3 Thread 0xb3894b90 (LWP 11135)  0xb7f01430 in __kernel_vsyscall ()
  2 Thread 0xb3bfeb90 (LWP 11214)  0xb7f01430 in __kernel_vsyscall ()
  1 Thread 0xb7c426d0 (LWP 11108)  0xb7f01430 in __kernel_vsyscall ()

Thread 11 (Thread 0xb79bbb90 (LWP 11109)):
#0  0xb7f01430 in __kernel_vsyscall ()
#1  0xb7dff906 in nanosleep () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081114a8 in ?? ()
#3  0xb7df850f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#4  0xb7d4f7ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 10 (Thread 0xb7418b90 (LWP 11110)):
#0  0xb7f01430 in __kernel_vsyscall ()
#1  0xb7dfc075 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08114897 in ?? ()
#3  0x08116ecc in ?? ()
#4  0x08116f0c in ?? ()
#5  0x08129b6a in ?? ()
#6  0x080b5c6a in ?? ()
#7  0x080d61a4 in ?? ()
#8  0x08127f4e in ?? ()
#9  0x081404b5 in ?? ()
#10 0xb7df850f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#11 0xb7d4f7ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 9 (Thread 0xb6232b90 (LWP 11114)):
#0  0xb7f01430 in __kernel_vsyscall ()
#1  0xb7dfc3a2 in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08114848 in ?? ()
#3  0x08116ecc in ?? ()
#4  0x08116f0c in ?? ()
#5  0x08129b6a in ?? ()
#6  0x080d3243 in ?? ()
#7  0xb623c04a in ?? ()
#8  0xb623bb9b in ?? ()
#9  0xb623a360 in ?? ()
#10 0xb7972059 in ?? ()
#11 0x08098c55 in mono_runtime_delegate_invoke ()
#12 0x080d620f in ?? ()
#13 0x08127f4e in ?? ()
#14 0x081404b5 in ?? ()
#15 0xb7df850f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#16 0xb7d4f7ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 8 (Thread 0xb46d6b90 (LWP 11121)):
#0  0xb7f01430 in __kernel_vsyscall ()
#1  0xb7dfc3a2 in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08114848 in ?? ()
#3  0x08114912 in ?? ()
#4  0x08129fb5 in ?? ()
#5  0x080d4e09 in ?? ()
#6  0xb481a527 in ?? ()
#7  0xb481a2a7 in ?? ()
#8  0xb481a0b7 in ?? ()
#9  0xb4819fa6 in ?? ()
#10 0x0809e8e3 in mono_runtime_invoke_array ()
#11 0x0809ea74 in ?? ()
#12 0x080d9223 in ?? ()
#13 0x080d9650 in ?? ()
#14 0x080d61a4 in ?? ()
#15 0x08127f4e in ?? ()
#16 0x081404b5 in ?? ()
#17 0xb7df850f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#18 0xb7d4f7ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 7 (Thread 0xb45d1b90 (LWP 11122)):
#0  0xb7f01430 in __kernel_vsyscall ()
#1  0xb7dfc3a2 in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08114848 in ?? ()
#3  0x08114912 in ?? ()
#4  0x08129fb5 in ?? ()
#5  0x080d4e09 in ?? ()
#6  0xb481a527 in ?? ()
#7  0xb481a2a7 in ?? ()
#8  0xb481a0b7 in ?? ()
#9  0xb4819fa6 in ?? ()
#10 0x0809e8e3 in mono_runtime_invoke_array ()
#11 0x0809ea74 in ?? ()
#12 0x080d9223 in ?? ()
#13 0x080d9650 in ?? ()
#14 0x080d61a4 in ?? ()
#15 0x08127f4e in ?? ()
#16 0x081404b5 in ?? ()
#17 0xb7df850f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#18 0xb7d4f7ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 6 (Thread 0xb44bcb90 (LWP 11123)):
#0  0xb7f01430 in __kernel_vsyscall ()
#1  0xb7dfc3a2 in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08114848 in ?? ()
#3  0x08114912 in ?? ()
#4  0x08129fb5 in ?? ()
#5  0x080d4e09 in ?? ()
#6  0xb481a527 in ?? ()
#7  0xb481a2a7 in ?? ()
#8  0xb481a0b7 in ?? ()
#9  0xb4819fa6 in ?? ()
#10 0x0809e8e3 in mono_runtime_invoke_array ()
#11 0x0809ea74 in ?? ()
#12 0x080d9223 in ?? ()
#13 0x080d9650 in ?? ()
#14 0x080d61a4 in ?? ()
#15 0x08127f4e in ?? ()
#16 0x081404b5 in ?? ()
#17 0xb7df850f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#18 0xb7d4f7ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 5 (Thread 0xb3ab9b90 (LWP 11133)):
#0  0xb7f01430 in __kernel_vsyscall ()
#1  0xb7d44f77 in poll () from /lib/tls/i686/cmov/libc.so.6
#2  0xb3c4ff71 in ?? ()
#3  0xb3c4ff1d in ?? ()
#4  0x0a9dee3a in ?? ()
#5  0xb3ad1a4d in avahi_simple_poll_run () from /usr/lib/libavahi-common.so.3
#6  0xb3ad2320 in avahi_simple_poll_iterate ()
   from /usr/lib/libavahi-common.so.3
#7  0xb3ad2370 in avahi_simple_poll_loop () from /usr/lib/libavahi-common.so.3
#8  0xb3c4fedb in ?? ()
#9  0xb3c4fe12 in ?? ()
#10 0xb7972059 in ?? ()
#11 0x08098c55 in mono_runtime_delegate_invoke ()
#12 0x080d620f in ?? ()
#13 0x08127f4e in ?? ()
#14 0x081404b5 in ?? ()
#15 0xb7df850f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#16 0xb7d4f7ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 4 (Thread 0xb39a4b90 (LWP 11134)):
#0  0xb7f01430 in __kernel_vsyscall ()
#1  0xb7dff328 in accept () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08124e79 in ?? ()
#3  0x080ddd4b in ?? ()
#4  0xb39a5fb2 in ?? ()
#5  0xb39a5dc7 in ?? ()
#6  0xb39a5cae in ?? ()
#7  0xb7972059 in ?? ()
#8  0x08098c55 in mono_runtime_delegate_invoke ()
#9  0x080d620f in ?? ()
#10 0x08127f4e in ?? ()
#11 0x081404b5 in ?? ()
#12 0xb7df850f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#13 0xb7d4f7ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 3 (Thread 0xb3894b90 (LWP 11135)):
#0  0xb7f01430 in __kernel_vsyscall ()
#1  0xb7d44f77 in poll () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7e4bc32 in ?? () from /usr/lib/libglib-2.0.so.0
#3  0xb7e4c2c2 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#4  0xb4eb48b0 in ?? () from /usr/lib/libORBit-2.so.0
#5  0xb7e7305f in ?? () from /usr/lib/libglib-2.0.so.0
#6  0xb7df850f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#7  0xb7d4f7ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 2 (Thread 0xb3bfeb90 (LWP 11214)):
#0  0xb7f01430 in __kernel_vsyscall ()
#1  0xb7d47c01 in select () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7e819bb in g_spawn_sync () from /usr/lib/libglib-2.0.so.0
#3  0xb7e81d6c in g_spawn_command_line_sync () from /usr/lib/libglib-2.0.so.0
#4  0x0817d495 in ?? ()
#5  0x0807f78b in ?? ()
#6  <signal handler called>
#7  0xb7ce52c3 in strlen () from /lib/tls/i686/cmov/libc.so.6
#8  0x0809ca3a in mono_string_new ()
#9  0x0809cac3 in mono_string_new_wrapper ()
#10 0xb600766f in ?? ()
#11 0xb39adcc3 in ?? ()
#12 0xb39ad3ab in ?? ()
#13 0x080c6728 in ?? ()
#14 0xb603efca in ?? ()
#15 0xb39ad91b in ?? ()
#16 0xb39ad893 in ?? ()
#17 0xb39ad70f in ?? ()
#18 0xb39ad512 in ?? ()
#19 0xb39ad484 in ?? ()
#20 0xb39ad0fc in ?? ()
#21 0xb39a7088 in ?? ()
#22 0xb39a66c6 in ?? ()
#23 0xb3c4ce6f in ?? ()
#24 0xb3c4a4d5 in ?? ()
#25 0xb3c4a4b4 in ?? ()
#26 0xb3c4a168 in ?? ()
#27 0xb7972059 in ?? ()
#28 0x08098c55 in mono_runtime_delegate_invoke ()
#29 0x080d620f in ?? ()
#30 0x08127f4e in ?? ()
#31 0x081404b5 in ?? ()
#32 0xb7df850f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#33 0xb7d4f7ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 1 (Thread 0xb7c426d0 (LWP 11108)):
#0  0xb7f01430 in __kernel_vsyscall ()
#1  0xb7d44f77 in poll () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7e4bc32 in ?? () from /usr/lib/libglib-2.0.so.0
#3  0xb7e4c2c2 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#4  0xb6b2c299 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#5  0xb3cf103e in ?? ()
#6  0xb3cf1008 in ?? ()
#7  0xb3cf0dab in ?? ()
#8  0xb6da4e1d in ?? ()
#9  0xb6da4d03 in ?? ()
#10 0xb6da4c0a in ?? ()
#11 0xb79700c4 in ?? ()
#12 0xb79641c3 in ?? ()
#13 0x0809cb86 in mono_runtime_exec_main ()
#14 0x0809d1ab in mono_runtime_run_main ()
#15 0x0805aeee in mono_main ()
#16 0x0805a3f2 in ?? ()
#17 0xb7c84685 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#18 0x0805a331 in ?? ()
#0  0xb7f01430 in __kernel_vsyscall ()


=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Aborted (core dumped)

Not entirely sure what you wanted but I hope I got it for you. I'm pretty new at this. Thanks for helping! I really appreciate it!
Jared

---

### Post by Jmeyering on 2008-10-04
bump

---

