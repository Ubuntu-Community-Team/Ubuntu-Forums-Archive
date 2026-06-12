---
title: "Banshee, Tomboy, Gnome-Do, etc crashing on loading &quot;Got a SIGSEGV...&quot;"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by TheApe on 2009-11-03
Hi everyone.

When trying to load either gnome-do, banshee, tomboy or f-spot, I got crash with the same error message

[COLOR="Red"]Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.[/COLOR]

I don't know why this problem started, Maybe because of a "forced" halt. (My notebook has no battery, so if I accidentally unplug it, it shuts down)

Here is the complete output error from banshee
```
Stacktrace:

  at (wrapper managed-to-native) System.IO.MonoIO.Open (string,System.IO.FileMode,System.IO.FileAccess,System.IO.FileShare,System.IO.FileOptions,System.IO.MonoIOError&) <0x00004>
  at (wrapper managed-to-native) System.IO.MonoIO.Open (string,System.IO.FileMode,System.IO.FileAccess,System.IO.FileShare,System.IO.FileOptions,System.IO.MonoIOError&) <0xffffffff>
  at System.IO.FileStream..ctor (string,System.IO.FileMode,System.IO.FileAccess,System.IO.FileShare,int,bool,System.IO.FileOptions) <0x00296>
  at System.IO.FileStream..ctor (string,System.IO.FileMode,System.IO.FileAccess,System.IO.FileShare) <0x0001f>
  at (wrapper remoting-invoke-with-check) System.IO.FileStream..ctor (string,System.IO.FileMode,System.IO.FileAccess,System.IO.FileShare) <0xffffffff>
  at System.IO.File.OpenRead (string) <0x00021>
  at System.IO.StreamReader..ctor (string,System.Text.Encoding,bool,int) <0x00072>
  at System.IO.StreamReader..ctor (string) <0x00026>
  at (wrapper remoting-invoke-with-check) System.IO.StreamReader..ctor (string) <0xffffffff>
  at Banshee.Base.XdgBaseDirectorySpec.GetUserDirectory (string,string) <0x000b2>
  at Banshee.Base.Paths..cctor () <0x00054>
  at (wrapper runtime-invoke) System.Object.runtime_invoke_void (object,intptr,intptr,intptr) <0xffffffff>
  at Banshee.Gui.GtkBaseClient..cctor () <0xffffffff>
  at Banshee.Gui.GtkBaseClient..cctor () <0x00009>
  at (wrapper runtime-invoke) System.Object.runtime_invoke_void (object,intptr,intptr,intptr) <0xffffffff>
  at Nereid.Client.Main (string[]) <0xffffffff>
  at Nereid.Client.Main (string[]) <0x0000b>
  at (wrapper runtime-invoke) Nereid.Client.runtime_invoke_void_string[] (object,intptr,intptr,intptr) <0xffffffff>
  at (wrapper managed-to-native) System.AppDomain.ExecuteAssembly (System.Reflection.Assembly,string[]) <0x00004>
  at (wrapper managed-to-native) System.AppDomain.ExecuteAssembly (System.Reflection.Assembly,string[]) <0xffffffff>
  at System.AppDomain.ExecuteAssemblyInternal (System.Reflection.Assembly,string[]) <0x00028>
  at System.AppDomain.ExecuteAssembly (string,System.Security.Policy.Evidence,string[]) <0x00021>
  at (wrapper remoting-invoke-with-check) System.AppDomain.ExecuteAssembly (string,System.Security.Policy.Evidence,string[]) <0xffffffff>
  at System.AppDomain.ExecuteAssembly (string) <0x00014>
  at (wrapper remoting-invoke-with-check) System.AppDomain.ExecuteAssembly (string) <0xffffffff>
  at Booter.Booter.BootClient (string) <0x00055>
  at Booter.Booter.Main () <0x00188>
  at (wrapper runtime-invoke) System.Object.runtime_invoke_void (object,intptr,intptr,intptr) <0xffffffff>

Native stacktrace:

	mono [0x806d944]
	mono [0x808616b]
	[0xb805a410]
	mono [0x815389b]
	mono [0x8153b7d]
	mono [0x80fc77e]
	[0xb71fe556]
	[0xb71fd80f]
	[0xb71fd560]
	[0xb71fd51c]
	[0xb71fd4b2]
	[0xb71fd3a3]
	[0xb71fd317]
	[0xb71fd2ca]
	[0xb71fbb0b]
	[0xb71fb665]
	[0xb79de1ae]
	mono [0x80be75d]
	mono [0x8198be8]
	mono [0x81afc35]
	mono [0x81b1b41]
	mono [0x807029f]
	[0xb7c68066]
	[0xb79de1ae]
	mono [0x80be75d]
	mono [0x8198be8]
	mono [0x81afc35]
	mono [0x81b1b41]
	mono [0x807029f]
	[0xb7c68066]
	[0xb71fb553]
	mono(mono_runtime_exec_main+0xe5) [0x80bad75]
	[0xb71fb4fd]
	[0xb71fb421]
	[0xb71fb31a]
	[0xb71fb2c6]
	[0xb71fb23d]
	[0xb71fb1fa]
	[0xb71fa33e]
	[0xb79de3a9]
	[0xb79de1ae]
	mono(mono_runtime_exec_main+0xe5) [0x80bad75]
	mono(mono_runtime_run_main+0x16b) [0x80bb4eb]
	mono(mono_main+0x1727) [0x805c917]
	mono [0x805ac62]
	/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7dec775]
	mono [0x805aba1]

Debug info from gdb:

(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 0xb7da26e0 (LWP 10224)]
[New Thread 0xb75e7b90 (LWP 10226)]
[New Thread 0xb79ddb90 (LWP 10225)]
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
0xb805a430 in __kernel_vsyscall ()
  3 Thread 0xb79ddb90 (LWP 10225)  0xb805a430 in __kernel_vsyscall ()
  2 Thread 0xb75e7b90 (LWP 10226)  0xb805a430 in __kernel_vsyscall ()
  1 Thread 0xb7da26e0 (LWP 10224)  0xb805a430 in __kernel_vsyscall ()

Thread 3 (Thread 0xb79ddb90 (LWP 10225)):
#0  0xb805a430 in __kernel_vsyscall ()
#1  0xb7f6c8f6 in nanosleep () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081492e8 in ?? ()
#3  0xb7f654ff in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#4  0xb7eba49e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 2 (Thread 0xb75e7b90 (LWP 10226)):
#0  0xb805a430 in __kernel_vsyscall ()
#1  0xb7f690e5 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x0814c607 in ?? ()
#3  0x0814f1f4 in ?? ()
#4  0x0814f25c in ?? ()
#5  0x08169b02 in ?? ()
#6  0x080d565a in ?? ()
#7  0x080f7639 in ?? ()
#8  0x081653b6 in ?? ()
#9  0x08183355 in ?? ()
#10 0xb7f654ff in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#11 0xb7eba49e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 1 (Thread 0xb7da26e0 (LWP 10224)):
#0  0xb805a430 in __kernel_vsyscall ()
#1  0xb7eb6a87 in syscall () from /lib/tls/i686/cmov/libc.so.6
#2  0x0806d9e7 in ?? ()
#3  0x0808616b in ?? ()
#4  <signal handler called>
#5  0x0814d063 in ?? ()
#6  0x0815389b in ?? ()
#7  0x08153b7d in ?? ()
#8  0x080fc77e in ?? ()
#9  0xb71fe556 in ?? ()
#10 0xb71fd80f in ?? ()
#11 0xb71fd560 in ?? ()
#12 0xb71fd51c in ?? ()
#13 0xb71fd4b2 in ?? ()
#14 0xb71fd3a3 in ?? ()
#15 0xb71fd317 in ?? ()
#16 0xb71fd2ca in ?? ()
#17 0xb71fbb0b in ?? ()
#18 0xb71fb665 in ?? ()
#19 0xb79de1ae in ?? ()
#20 0x080be75d in ?? ()
#21 0x08198be8 in ?? ()
#22 0x081afc35 in ?? ()
#23 0x081b1b41 in ?? ()
#24 0x0807029f in ?? ()
#25 0xb7c68066 in ?? ()
#26 0xb79de1ae in ?? ()
#27 0x080be75d in ?? ()
#28 0x08198be8 in ?? ()
#29 0x081afc35 in ?? ()
#30 0x081b1b41 in ?? ()
#31 0x0807029f in ?? ()
#32 0xb7c68066 in ?? ()
#33 0xb71fb553 in ?? ()
#34 0x080bad75 in mono_runtime_exec_main ()
#35 0xb71fb4fd in ?? ()
#36 0xb71fb421 in ?? ()
#37 0xb71fb31a in ?? ()
#38 0xb71fb2c6 in ?? ()
#39 0xb71fb23d in ?? ()
#40 0xb71fb1fa in ?? ()
#41 0xb71fa33e in ?? ()
#42 0xb79de3a9 in ?? ()
#43 0xb79de1ae in ?? ()
#44 0x080bad75 in mono_runtime_exec_main ()
#45 0x080bb4eb in mono_runtime_run_main ()
#46 0x0805c917 in mono_main ()
#47 0x0805ac62 in ?? ()
#48 0xb7dec775 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#49 0x0805aba1 in ?? ()
#0  0xb805a430 in __kernel_vsyscall ()

=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================
```

I've already tried reinstalling all mono packages and libc6. But none worked.

Does anyone has any hint about it?
Thanks!!

---

### Post by directhex on 2009-11-03
Try runnign with --debug

---

### Post by TheApe on 2009-11-03
Directhex,

Here is the output with the "--debug". (I think it's pretty much the same)
Thanks!

```
$ banshee --debug
** Running Mono with --debug   **
Stacktrace:

  at (wrapper managed-to-native) System.IO.MonoIO.Open (string,System.IO.FileMode,System.IO.FileAccess,System.IO.FileShare,System.IO.FileOptions,System.IO.MonoIOError&) <0x00004>
  at (wrapper managed-to-native) System.IO.MonoIO.Open (string,System.IO.FileMode,System.IO.FileAccess,System.IO.FileShare,System.IO.FileOptions,System.IO.MonoIOError&) <0xffffffff>
  at System.IO.FileStream..ctor (string,System.IO.FileMode,System.IO.FileAccess,System.IO.FileShare,int,bool,System.IO.FileOptions) <0x00296>
  at System.IO.FileStream..ctor (string,System.IO.FileMode,System.IO.FileAccess,System.IO.FileShare) <0x0001f>
  at (wrapper remoting-invoke-with-check) System.IO.FileStream..ctor (string,System.IO.FileMode,System.IO.FileAccess,System.IO.FileShare) <0xffffffff>
  at System.IO.File.OpenRead (string) <0x00021>
  at System.IO.StreamReader..ctor (string,System.Text.Encoding,bool,int) <0x00072>
  at System.IO.StreamReader..ctor (string) <0x00026>
  at (wrapper remoting-invoke-with-check) System.IO.StreamReader..ctor (string) <0xffffffff>
  at Banshee.Base.XdgBaseDirectorySpec.GetUserDirectory (string,string) [0x00042] in /build/buildd/banshee-1.4.3/src/Core/Banshee.Core/Banshee.Base/XdgBaseDirectorySpec.cs:53
  at Banshee.Base.Paths..cctor () [0x00000] in /build/buildd/banshee-1.4.3/src/Core/Banshee.Core/Banshee.Base/ApplicationContext.cs:1
  at (wrapper runtime-invoke) System.Object.runtime_invoke_void (object,intptr,intptr,intptr) <0xffffffff>
  at Banshee.Gui.GtkBaseClient..cctor () [0x00014] in /build/buildd/banshee-1.4.3/src/Core/Banshee.ThickClient/Banshee.Gui/GtkBaseClient.cs:41
  at Banshee.Gui.GtkBaseClient..cctor () [0x00000] in /build/buildd/banshee-1.4.3/src/Core/Banshee.ThickClient/Banshee.Addins.Gui/AddinDetailsDialog.cs:1
  at (wrapper runtime-invoke) System.Object.runtime_invoke_void (object,intptr,intptr,intptr) <0xffffffff>
  at Nereid.Client.Main (string[]) [0x00006] in /build/buildd/banshee-1.4.3/src/Clients/Nereid/Nereid/Client.cs:49
  at Nereid.Client.Main (string[]) [0x00000] in /build/buildd/banshee-1.4.3/src/Clients/Nereid/Nereid/Client.cs:48
  at (wrapper runtime-invoke) Nereid.Client.runtime_invoke_void_string[] (object,intptr,intptr,intptr) <0xffffffff>
  at (wrapper managed-to-native) System.AppDomain.ExecuteAssembly (System.Reflection.Assembly,string[]) <0x00004>
  at (wrapper managed-to-native) System.AppDomain.ExecuteAssembly (System.Reflection.Assembly,string[]) <0xffffffff>
  at System.AppDomain.ExecuteAssemblyInternal (System.Reflection.Assembly,string[]) <0x00028>
  at System.AppDomain.ExecuteAssembly (string,System.Security.Policy.Evidence,string[]) <0x00021>
  at (wrapper remoting-invoke-with-check) System.AppDomain.ExecuteAssembly (string,System.Security.Policy.Evidence,string[]) <0xffffffff>
  at System.AppDomain.ExecuteAssembly (string) <0x00014>
  at (wrapper remoting-invoke-with-check) System.AppDomain.ExecuteAssembly (string) <0xffffffff>
  at Booter.Booter.BootClient (string) [0x00000] in /build/buildd/banshee-1.4.3/src/Clients/Booter/Booter/Entry.cs:106
  at Booter.Booter.Main () [0x000d3] in /build/buildd/banshee-1.4.3/src/Clients/Booter/Booter/Entry.cs:100
  at (wrapper runtime-invoke) System.Object.runtime_invoke_void (object,intptr,intptr,intptr) <0xffffffff>

Native stacktrace:

	mono [0x806d944]
	mono [0x808616b]
	[0xb7fb0410]
	mono [0x815389b]
	mono [0x8153b7d]
	mono [0x80fc77e]
	[0xb7106cbe]
	[0xb7105f77]
	[0xb7105cc8]
	[0xb7105c84]
	[0xb7105c1a]
	[0xb7105b0b]
	[0xb7105a7f]
	[0xb7105a32]
	[0xb7104273]
	[0xb7103dcd]
	[0xb79341ae]
	mono [0x80be75d]
	mono [0x8198be8]
	mono [0x81afc35]
	mono [0x81b1b41]
	mono [0x807029f]
	[0xb7bbe066]
	[0xb79341ae]
	mono [0x80be75d]
	mono [0x8198be8]
	mono [0x81afc35]
	mono [0x81b1b41]
	mono [0x807029f]
	[0xb7bbe066]
	[0xb7103cbb]
	mono(mono_runtime_exec_main+0xe5) [0x80bad75]
	[0xb7103c65]
	[0xb7103b89]
	[0xb7103a82]
	[0xb7103a2e]
	[0xb71039a5]
	[0xb7103962]
	[0xb7102c3e]
	[0xb79343a9]
	[0xb79341ae]
	mono(mono_runtime_exec_main+0xe5) [0x80bad75]
	mono(mono_runtime_run_main+0x16b) [0x80bb4eb]
	mono(mono_main+0x1727) [0x805c917]
	mono [0x805ac62]
	/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7d42775]
	mono [0x805aba1]

Debug info from gdb:

(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 0xb7cf86e0 (LWP 15044)]
[New Thread 0xb753db90 (LWP 15052)]
[New Thread 0xb7933b90 (LWP 15051)]
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
0xb7fb0430 in __kernel_vsyscall ()
  3 Thread 0xb7933b90 (LWP 15051)  0xb7fb0430 in __kernel_vsyscall ()
  2 Thread 0xb753db90 (LWP 15052)  0xb7fb0430 in __kernel_vsyscall ()
  1 Thread 0xb7cf86e0 (LWP 15044)  0xb7fb0430 in __kernel_vsyscall ()

Thread 3 (Thread 0xb7933b90 (LWP 15051)):
#0  0xb7fb0430 in __kernel_vsyscall ()
#1  0xb7ec28f6 in nanosleep () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081492e8 in ?? ()
#3  0xb7ebb4ff in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#4  0xb7e1049e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 2 (Thread 0xb753db90 (LWP 15052)):
#0  0xb7fb0430 in __kernel_vsyscall ()
#1  0xb7ebf0e5 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x0814c607 in ?? ()
#3  0x0814f1f4 in ?? ()
#4  0x0814f25c in ?? ()
#5  0x08169b02 in ?? ()
#6  0x080d565a in ?? ()
#7  0x080f7639 in ?? ()
#8  0x081653b6 in ?? ()
#9  0x08183355 in ?? ()
#10 0xb7ebb4ff in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#11 0xb7e1049e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 1 (Thread 0xb7cf86e0 (LWP 15044)):
#0  0xb7fb0430 in __kernel_vsyscall ()
#1  0xb7ec20fb in read () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x0806da5e in ?? ()
#3  0x0808616b in ?? ()
#4  <signal handler called>
#5  0x0814d063 in ?? ()
#6  0x0815389b in ?? ()
#7  0x08153b7d in ?? ()
#8  0x080fc77e in ?? ()
#9  0xb7106cbe in ?? ()
#10 0xb7105f77 in ?? ()
#11 0xb7105cc8 in ?? ()
#12 0xb7105c84 in ?? ()
#13 0xb7105c1a in ?? ()
#14 0xb7105b0b in ?? ()
#15 0xb7105a7f in ?? ()
#16 0xb7105a32 in ?? ()
#17 0xb7104273 in ?? ()
#18 0xb7103dcd in ?? ()
#19 0xb79341ae in ?? ()
#20 0x080be75d in ?? ()
#21 0x08198be8 in ?? ()
#22 0x081afc35 in ?? ()
#23 0x081b1b41 in ?? ()
#24 0x0807029f in ?? ()
#25 0xb7bbe066 in ?? ()
#26 0xb79341ae in ?? ()
#27 0x080be75d in ?? ()
#28 0x08198be8 in ?? ()
#29 0x081afc35 in ?? ()
#30 0x081b1b41 in ?? ()
#31 0x0807029f in ?? ()
#32 0xb7bbe066 in ?? ()
#33 0xb7103cbb in ?? ()
#34 0x080bad75 in mono_runtime_exec_main ()
#35 0xb7103c65 in ?? ()
#36 0xb7103b89 in ?? ()
#37 0xb7103a82 in ?? ()
#38 0xb7103a2e in ?? ()
#39 0xb71039a5 in ?? ()
#40 0xb7103962 in ?? ()
#41 0xb7102c3e in ?? ()
#42 0xb79343a9 in ?? ()
#43 0xb79341ae in ?? ()
#44 0x080bad75 in mono_runtime_exec_main ()
#45 0x080bb4eb in mono_runtime_run_main ()
#46 0x0805c917 in mono_main ()
#47 0x0805ac62 in ?? ()
#48 0xb7d42775 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#49 0x0805aba1 in ?? ()
#0  0xb7fb0430 in __kernel_vsyscall ()

=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

```

---

### Post by directhex on 2009-11-03
Looks like your profile's been corrupted

Try mv ~/.config/banshee-1 ~/.config/banshee-1.bak (or something like that anyway)

---

### Post by TheApe on 2009-11-03
> **directhex said:**
> Looks like your profile's been corrupted

Try mv ~/.config/banshee-1 ~/.config/banshee-1.bak (or something like that anyway)
I tryed renaming the conf file, but the crash is still happening.

Tks, by the way.

---

### Post by directhex on 2009-11-03
I'm lost then. It's apparently dying trying to get ahold of your config folder, but that's all i can see. Try #banshee on gimpnet

---

### Post by sharm on 2009-11-04
If you are still having problems, I'll happily take a look at whatever error you're getting when starting Tomboy.  Try starting from a terminal with `tomboy --debug` and we'll see what the output is.

Also, please share what version of Tomboy you're using.  :-)

---

### Post by TheApe on 2009-11-05
Hi, Sharm!

Something very strange happened, now all of the softwares that I've mentioned are running fine. :shock:

Thanks for helping!

[]'s

---

### Post by humphreybc on 2009-11-07
Hi, I've just run into this problem today, and I think it could have been a hard shutdown corruption problem as my laptop overheated and died today and it wouldn't boot till I ran fsck and fixed a whole heap of stuff...

I've tried reinstalling all the mono packages but no luck, it's taken out Banshee and Gnome-Do.

Do you have any idea how yours managed to right itself?

---

### Post by TheApe on 2009-11-07
Hi, humpreybc!

I'm sure that I've run into this problem also by a hard shutdown.
I don't know what fixed it, but I tried the following:

```
mv ~/.config/banshee-1 ~/.config/banshee-1.bak
```

It hasn't worked instantly, but might work for you.
Another thing that I've done was apt-get upgrade.

Good lucky, man.

---

### Post by humphreybc on 2009-11-07
Thanks for your reply, but I fixed it by running this command:

```

rm -rf ~/.wapi

```

It was an input/output error caused by the hard shutdown. I've experienced problems with file system corruption in Windows, but never with Linux until now... I didn't think they were that common with Linux?

---

### Post by directhex on 2009-11-08
> **humphreybc said:**
> I've experienced problems with file system corruption in Windows, but never with Linux until now... I didn't think they were that common with Linux?

Depends on the filesystem you use, really

I've lost data to every FS under the sun

---

