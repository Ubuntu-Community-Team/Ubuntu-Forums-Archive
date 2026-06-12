---
title: "[SOLVED] Mono &amp;amp; KeePass 2"
date: 2008-09-11
forum: General Help
---

### Post by Ux64 on 2008-09-11
Hi!

Has anyone got KeePass 2.X working with Ubuntu, I mean Linux with Mono?

KeePass keeps crashing when writing password. Immediately after second letter program crashes. After that UI handler thread seems to be dead. 

```

Offset and length were out of bounds for the array or count is greater thanthe number of elements from index to the end of the source collection.
mscorlib
  at System.Buffer.BlockCopy (System.Array src, Int32 srcOffset, System.Array dest, Int32 destOffset, Int32 count) [0x00000] 
  at System.Security.SecureString.InsertAt (Int32 index, Char c) [0x00000] 
  at KeePass.UI.SecureEdit.RemoveInsert (Int32 nLeftRem, Int32 nRightRem, System.String strInsert) [0x00000] 
  at KeePass.UI.SecureEdit.OnPasswordTextChanged (System.Object sender, System.EventArgs e) [0x00000] 
  at System.Windows.Forms.Control.OnTextChanged (System.EventArgs e) [0x00000] 
  at System.Windows.Forms.TextBoxBase.OnTextChanged (System.EventArgs e) [0x00000] 
  at System.Windows.Forms.TextBoxBase.WndProc (System.Windows.Forms.Message& m) [0x00000] 
  at System.Windows.Forms.TextBox.WndProc (System.Windows.Forms.Message& m) [0x00000] 
  at System.Windows.Forms.Control+ControlWindowTarget.OnMessage (System.Windows.Forms.Message& m) [0x00000] 
  at System.Windows.Forms.Control+ControlNativeWindow.WndProc (System.Windows.Forms.Message& m) [0x00000] 
  at System.Windows.Forms.NativeWindow.WndProc (IntPtr hWnd, Msg msg, IntPtr wParam, IntPtr lParam) [0x00000] 
  at System.Windows.Forms.XplatUIX11.DispatchMessage (System.Windows.Forms.MSG& msg) [0x00000] 
  at System.Windows.Forms.XplatUI.DispatchMessage (System.Windows.Forms.MSG& msg) [0x00000] 
  at System.Windows.Forms.Application.RunLoop (Boolean Modal, System.Windows.Forms.ApplicationContext context) [0x00000] 
  at System.Windows.Forms.Form.ShowDialog (IWin32Window ownerWin32) [0x00000] 
  at System.Windows.Forms.Form.ShowDialog () [0x00000] 
  at (wrapper remoting-invoke-with-check) System.Windows.Forms.Form:ShowDialog ()
  at KeePass.Forms.MainForm.OpenDatabase (KeePassLib.Serialization.IOConnectionInfo ioConnection, KeePassLib.Keys.CompositeKey cmpKey, Boolean bOpenLocal) [0x00000] 
  at KeePass.Forms.MainForm.OnFileOpen (System.Object sender, System.EventArgs e) [0x00000] 
  at System.Windows.Forms.ToolStripItem.OnClick (System.EventArgs e) [0x00000] 
  at System.Windows.Forms.ToolStripButton.OnClick (System.EventArgs e) [0x00000] 
  at System.Windows.Forms.ToolStripItem.HandleClick (System.EventArgs e) [0x00000] 
  at System.Windows.Forms.ToolStripItem.FireEvent (System.EventArgs e, ToolStripItemEventType met) [0x00000] 
  at (wrapper remoting-invoke-with-check) System.Windows.Forms.ToolStripItem:FireEvent (System.EventArgs,System.Windows.Forms.ToolStripItemEventType)
  at System.Windows.Forms.ToolStrip.OnMouseUp (System.Windows.Forms.MouseEventArgs mea) [0x00000] 
  at System.Windows.Forms.Control.WmLButtonUp (System.Windows.Forms.Message& m) [0x00000] 
  at System.Windows.Forms.Control.WndProc (System.Windows.Forms.Message& m) [0x00000] 
  at System.Windows.Forms.ScrollableControl.WndProc (System.Windows.Forms.Message& m) [0x00000] 
  at System.Windows.Forms.ToolStrip.WndProc (System.Windows.Forms.Message& m) [0x00000] 
  at System.Windows.Forms.Control+ControlWindowTarget.OnMessage (System.Windows.Forms.Message& m) [0x00000] 
  at System.Windows.Forms.Control+ControlNativeWindow.WndProc (System.Windows.Forms.Message& m) [0x00000] 
  at System.Windows.Forms.NativeWindow.WndProc (IntPtr hWnd, Msg msg, IntPtr wParam, IntPtr lParam) [0x00000] 
  at System.Windows.Forms.XplatUIX11.DispatchMessage (System.Windows.Forms.MSG& msg) [0x00000] 
  at System.Windows.Forms.XplatUI.DispatchMessage (System.Windows.Forms.MSG& msg) [0x00000] 
  at System.Windows.Forms.Application.RunLoop (Boolean Modal, System.Windows.Forms.ApplicationContext context) [0x00000] 
  at System.Windows.Forms.Application.Run (System.Windows.Forms.ApplicationContext context) [0x00000] 
  at System.Windows.Forms.Application.Run (System.Windows.Forms.Form mainForm) [0x00000] 
  at KeePass.Program.Main (System.String[] args) [0x00000] 
Void BlockCopy(System.Array, Int32, System.Array, Int32, Int32)

```

After digging around I found following thread from KeePass Open Discussion:
[http://sourceforge.net/forum/forum.php?thread_id=2202915&forum_id=329220](http://sourceforge.net/forum/forum.php?thread_id=2202915&forum_id=329220)

I  it solved my problem.

 - Thanks

---

### Post by Noiano on 2008-10-05
did you build keepass successfully? If so could you please tell me how to do?
What about keepass 1.x? is it possible to build it using mono?

---

### Post by Ux64 on 2008-10-28
> **Noiano said:**
> did you build keepass successfully? If so could you please tell me how to do?
What about keepass 1.x? is it possible to build it using mono?

Nope. I used ready build version. Why bother to build, when NET is multiplatform? 

Actually latest mono runs latest keepass without major problems. I just forgot to report that. It was earlier than it didn't work out. ( I didn't make trough analysis, but just simply tried if it works )

---

### Post by Didjit on 2008-11-12
I keep getting this:

```
** (KeePass.exe:11749): WARNING **: The following assembly referenced from /home/chris/Desktop/KeePass-2.06-Beta/KeePass.exe could not be loaded:
     Assembly:   System.Windows.Forms    (assemblyref_index=1)
     Version:    2.0.0.0
     Public Key: b77a5c561934e089
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/home/chris/Desktop/KeePass-2.06-Beta/).

```


Is there something special I need to do? I just run by "mono KeePass.exe"
Running 64bit if that matters.
Tx

Didjit

---

### Post by Noiano on 2008-11-13
> **Didjit said:**
> I keep getting this:

```
** (KeePass.exe:11749): WARNING **: The following assembly referenced from /home/chris/Desktop/KeePass-2.06-Beta/KeePass.exe could not be loaded:
     Assembly:   System.Windows.Forms    (assemblyref_index=1)
     Version:    2.0.0.0
     Public Key: b77a5c561934e089
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/home/chris/Desktop/KeePass-2.06-Beta/).

```


Is there something special I need to do? I just run by "mono KeePass.exe"
Running 64bit if that matters.
Tx

Didjit

You need to install the package libmono-winforms2.0-cil

---

### Post by Didjit on 2008-11-13
Well, closer. Then I get this huge error.  Any ideas?

```

  at (wrapper managed-to-native) System.Diagnostics.FileVersionInfo.GetVersionInfo_internal (string) <0x0004b>
  at (wrapper managed-to-native) System.Diagnostics.FileVersionInfo.GetVersionInfo_internal (string) <0xffffffff>
  at System.Diagnostics.FileVersionInfo.GetVersionInfo (string) <0x000af>
  at KeePass.Plugins.PluginManager.LoadPlugins (System.IO.FileInfo[]) <0x000ae>
  at KeePass.Plugins.PluginManager.LoadAllPlugins (string) <0x00094>
  at KeePass.Forms.MainForm.OnFormLoad (object,System.EventArgs) <0x04929>
  at System.Windows.Forms.Form.OnLoad (System.EventArgs) <0x0007b>
  at System.Windows.Forms.Form.OnLoadInternal (System.EventArgs) <0x00080>
  at System.Windows.Forms.Form.OnCreateControl () <0x00054>
  at System.Windows.Forms.Control.CreateControl () <0x00146>
  at System.Windows.Forms.Control.WmShowWindow (System.Windows.Forms.Message&) <0x000cd>
  at System.Windows.Forms.Control.WndProc (System.Windows.Forms.Message&) <0x0029c>
  at System.Windows.Forms.ScrollableControl.WndProc (System.Windows.Forms.Message&) <0x00016>
  at System.Windows.Forms.ContainerControl.WndProc (System.Windows.Forms.Message&) <0x0006b>
  at System.Windows.Forms.Form.WndProc (System.Windows.Forms.Message&) <0x00253>
  at KeePass.Forms.MainForm.WndProc (System.Windows.Forms.Message&) <0x008f1>
  at ControlWindowTarget.OnMessage (System.Windows.Forms.Message&) <0x00025>
  at ControlNativeWindow.WndProc (System.Windows.Forms.Message&) <0x00038>
  at System.Windows.Forms.NativeWindow.WndProc (intptr,System.Windows.Forms.Msg,intptr,intptr) <0x001e0>
  at System.Windows.Forms.XplatUIX11.SendMessage (intptr,System.Windows.Forms.Msg,intptr,intptr) <0x00202>
  at System.Windows.Forms.XplatUIX11.MapWindow (System.Windows.Forms.Hwnd,System.Windows.Forms.WindowType) <0x002d8>
  at System.Windows.Forms.XplatUIX11.CreateWindow (System.Windows.Forms.CreateParams) <0x01afd>
  at System.Windows.Forms.XplatUI.CreateWindow (System.Windows.Forms.CreateParams) <0x00023>
  at System.Windows.Forms.NativeWindow.CreateHandle (System.Windows.Forms.CreateParams) <0x00045>
  at System.Windows.Forms.Control.CreateHandle () <0x00092>
  at System.Windows.Forms.Form.CreateHandle () <0x0001b>
  at System.Windows.Forms.Control.CreateControl () <0x0007e>
  at System.Windows.Forms.Control.SetVisibleCore (bool) <0x0008a>
  at System.Windows.Forms.Form.SetVisibleCore (bool) <0x001e2>
  at System.Windows.Forms.Control.set_Visible (bool) <0x00042>
  at (wrapper remoting-invoke-with-check) System.Windows.Forms.Control.set_Visible (bool) <0xffffffff>
  at System.Windows.Forms.Application.RunLoop (bool,System.Windows.Forms.ApplicationContext) <0x002d9>
  at System.Windows.Forms.Application.Run (System.Windows.Forms.ApplicationContext) <0x0006a>
  at System.Windows.Forms.Application.Run (System.Windows.Forms.Form) <0x00033>
  at KeePass.Program.Main (string[]) <0x00731>
  at (wrapper runtime-invoke) KeePass.Program.runtime_invoke_void_string[] (object,intptr,intptr,intptr) <0xffffffff>

Native stacktrace:

    mono [0x529d21]
    mono [0x43f99d]
    /lib/libpthread.so.0 [0x7fc1f308e0f0]
    mono [0x4da50c]
    mono [0x4da6d7]
    mono [0x49fa5b]
    mono [0x49ffe3]
    [0x4114397b]

Debug info from gdb:

(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 0x7fc1f3d60710 (LWP 13661)]
[New Thread 0x40d3e950 (LWP 13663)]
[New Thread 0x40073950 (LWP 13662)]
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
0x00007fc1f308cf4b in read () from /lib/libpthread.so.0
  3 Thread 0x40073950 (LWP 13662)  0x00007fc1f308d851 in nanosleep ()
   from /lib/libpthread.so.0
  2 Thread 0x40d3e950 (LWP 13663)  0x00007fc1f308a2d9 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/libpthread.so.0
  1 Thread 0x7fc1f3d60710 (LWP 13661)  0x00007fc1f308cf4b in read ()
   from /lib/libpthread.so.0

Thread 3 (Thread 0x40073950 (LWP 13662)):
#0  0x00007fc1f308d851 in nanosleep () from /lib/libpthread.so.0
#1  0x00000000004c56e2 in ?? ()
#2  0x00007fc1f30863ea in start_thread () from /lib/libpthread.so.0
#3  0x00007fc1f2b6ec6d in clone () from /lib/libc.so.6
#4  0x0000000000000000 in ?? ()

Thread 2 (Thread 0x40d3e950 (LWP 13663)):
#0  0x00007fc1f308a2d9 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/libpthread.so.0
#1  0x00000000004c8565 in ?? ()
#2  0x00000000004ca81b in ?? ()
#3  0x00000000004db96e in ?? ()
#4  0x0000000000470b93 in ?? ()
#5  0x000000000048d41b in ?? ()
#6  0x00000000004d9d33 in ?? ()
#7  0x00000000004f1582 in ?? ()
#8  0x00007fc1f30863ea in start_thread () from /lib/libpthread.so.0
#9  0x00007fc1f2b6ec6d in clone () from /lib/libc.so.6
#10 0x0000000000000000 in ?? ()

Thread 1 (Thread 0x7fc1f3d60710 (LWP 13661)):
#0  0x00007fc1f308cf4b in read () from /lib/libpthread.so.0
#1  0x00007fc1f350f56e in ?? () from /usr/lib/libglib-2.0.so.0
#2  0x00007fc1f350fa56 in ?? () from /usr/lib/libglib-2.0.so.0
#3  0x00007fc1f35104cb in g_spawn_sync () from /usr/lib/libglib-2.0.so.0
#4  0x00007fc1f3510988 in g_spawn_command_line_sync ()
   from /usr/lib/libglib-2.0.so.0
#5  0x0000000000529dc8 in ?? ()
#6  0x000000000043f99d in ?? ()
#7  <signal handler called>
#8  0x00000000004da50c in ?? ()
#9  0x00000000004da6d7 in ?? ()
#10 0x000000000049fa5b in ?? ()
#11 0x000000000049ffe3 in ?? ()
#12 0x000000004114397b in ?? ()
#13 0x0000000002623b30 in ?? ()
#14 0x000000004191c8d4 in ?? ()
#15 0xffffffffffffffff in ?? ()
#16 0x00007fc1eaf0faa0 in ?? ()
#17 0x00007fc1eb1ded80 in ?? ()
#18 0x00007ffffbd8f7a0 in ?? ()
#19 0x00007ffffbd8f5b0 in ?? ()
#20 0x00007fc1f3bbd780 in ?? ()
#21 0x00007fc1f1256300 in ?? ()
#22 0x00007fc1eb1e6348 in ?? ()
#23 0x00007fc1eaf0fd48 in ?? ()
#24 0x0000000041143780 in ?? ()
#25 0x00007fc1f3bc5c40 in ?? ()
#26 0x00007fc1f3bc73f0 in ?? ()
#27 0x00007fc1eb1e6348 in ?? ()
#28 0x00007fc1f1259f00 in ?? ()
#29 0x00007fc1eaf10ea0 in ?? ()
#30 0x000000004114334f in ?? ()
#31 0x00007fc1eb1ded80 in ?? ()
#32 0x00007fc1f3bc5c40 in ?? ()
#33 0x00007ffffbd8f770 in ?? ()
#34 0x00000000412b50c6 in ?? ()
#35 0x00007fc1eaec3460 in ?? ()
#36 0x0000000002623b31 in ?? ()
#37 0x00007fc1f3d60708 in ?? ()
#38 0x00007fc1e4024200 in ?? ()
#39 0x0000000041141aa5 in ?? ()
#40 0x00007fc1eb1ded80 in ?? ()
#41 0x00007ffffbd8fe90 in ?? ()
#42 0x00007ffffbd8f7b0 in ?? ()
#43 0x00007fc1f3bbd780 in ?? ()
#44 0x00007fc1f1256300 in ?? ()
#45 0x00007fc1f3bc5c40 in ?? ()
#46 0x00007fc1f3bc73f0 in ?? ()
#47 0x4064600000000000 in ?? ()
#48 0x40100c907da4e871 in ?? ()
#49 0x0000000042c00000 in ?? ()
#50 0x0000000000000000 in ?? ()
#0  0x00007fc1f308cf4b in read () from /lib/libpthread.so.0


=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================


```

---

### Post by Noiano on 2008-11-14
which version of mono are you using?

---

### Post by Didjit on 2008-11-14
Ah. 1.9.1 Which now I think is the problem. KeePass needs 2X, right?

---

### Post by Noiano on 2008-11-14
> **Didjit said:**
> Ah. 1.9.1 Which now I think is the problem. KeePass needs 2X, right?

no, version 1.9.1 is good enough. I only have mono + that library I mentioned in my previous post...that's pretty weird, you know?:confused:

---

### Post by Didjit on 2008-11-14
And you are running the Portable KeyPass?

---

### Post by Noiano on 2008-11-15
> **Didjit said:**
> And you are running the Portable KeyPass?

Yes I am...I just type mono Keepass.exe and it works...again it's very strange :confused:

---

### Post by Didjit on 2008-11-15
Ok, well I'm running 64 bit Ubuntu, so there may be something there...

Didjit

---

### Post by Ux64 on 2008-11-17
> **Didjit said:**
> Ok, well I'm running 64 bit Ubuntu, so there may be something there...

Shouldn't make any difference. Because I'm using it too. And it worked just fine. Those libs were important and also enough new keepass and mono. After that it did work.

I'm still hoping to get twofish encryption instead of aes for keepass. But strangely enough, I got comment like there is no twofish for .net. Hmm. Ok. So they're waiting for 100% ready .net lib for it.

---

### Post by jakommo on 2009-01-16
Did you solve the Problem?
I got the same at my 64bit System.
At work I`m using 32bit Ubuntu and had no problem.

Greez

jakommo

---

### Post by Didjit on 2009-01-18
Not me. I went back to 1.X anyway since my mobile device supported only 1.X . I use KeePassX on my desktop.

Didjit

---

### Post by Samhain77 on 2009-03-27
Have you tried to verify how you type it? Pay attention to capital letters:

```
mono KeePass.exe
```

it works for me with mono 1.91 and Keepass 2.07B on Intrepid

---

### Post by jakommo on 2009-03-27
hmm strange I tried some days ago with 2.07B and it didn't work (same error as with 2.06B). Are you running amd64?

---

### Post by jwrinkle on 2009-04-03
I appear to have same problem.  Ubuntu 8.10 64 bit, mono-2.0-develop (mono v 1.91 amd64), libmono-winforms2.0-cil, libmono-winforms1.0-cil, portable keepass 2.07 :

```

jason@x2x64:~/Desktop/portakeepass 2.07$ mono KeePass.exe 
Stacktrace:

  at (wrapper managed-to-native) System.Diagnostics.FileVersionInfo.GetVersionInfo_internal (string) <0x0004b>
  at (wrapper managed-to-native) System.Diagnostics.FileVersionInfo.GetVersionInfo_internal (string) <0xffffffff>
  at System.Diagnostics.FileVersionInfo.GetVersionInfo (string) <0x000aa>
  at KeePass.Plugins.PluginManager.LoadPlugins (System.IO.FileInfo[]) <0x000ae>
  at KeePass.Plugins.PluginManager.LoadAllPlugins (string) <0x0008f>
  at KeePass.Forms.MainForm.OnFormLoad (object,System.EventArgs) <0x045a8>
  at System.Windows.Forms.Form.OnLoad (System.EventArgs) <0x0007b>
  at System.Windows.Forms.Form.OnLoadInternal (System.EventArgs) <0x00080>
  at System.Windows.Forms.Form.OnCreateControl () <0x00054>
  at System.Windows.Forms.Control.CreateControl () <0x00146>
  at System.Windows.Forms.Control.WmShowWindow (System.Windows.Forms.Message&) <0x000cd>
  at System.Windows.Forms.Control.WndProc (System.Windows.Forms.Message&) <0x0029c>
  at System.Windows.Forms.ScrollableControl.WndProc (System.Windows.Forms.Message&) <0x00016>
  at System.Windows.Forms.ContainerControl.WndProc (System.Windows.Forms.Message&) <0x0006b>
  at System.Windows.Forms.Form.WndProc (System.Windows.Forms.Message&) <0x00253>
  at KeePass.Forms.MainForm.WndProc (System.Windows.Forms.Message&) <0x005d7>
  at ControlWindowTarget.OnMessage (System.Windows.Forms.Message&) <0x00025>
  at ControlNativeWindow.WndProc (System.Windows.Forms.Message&) <0x00038>
  at System.Windows.Forms.NativeWindow.WndProc (intptr,System.Windows.Forms.Msg,intptr,intptr) <0x001e0>
  at System.Windows.Forms.XplatUIX11.SendMessage (intptr,System.Windows.Forms.Msg,intptr,intptr) <0x001e8>
  at System.Windows.Forms.XplatUIX11.MapWindow (System.Windows.Forms.Hwnd,System.Windows.Forms.WindowType) <0x002d8>
  at System.Windows.Forms.XplatUIX11.CreateWindow (System.Windows.Forms.CreateParams) <0x01afd>
  at System.Windows.Forms.XplatUI.CreateWindow (System.Windows.Forms.CreateParams) <0x00023>
  at System.Windows.Forms.NativeWindow.CreateHandle (System.Windows.Forms.CreateParams) <0x00045>
  at System.Windows.Forms.Control.CreateHandle () <0x00092>
  at System.Windows.Forms.Form.CreateHandle () <0x0001b>
  at System.Windows.Forms.Control.CreateControl () <0x0007e>
  at System.Windows.Forms.Control.SetVisibleCore (bool) <0x0008a>
  at System.Windows.Forms.Form.SetVisibleCore (bool) <0x001dc>
  at System.Windows.Forms.Control.set_Visible (bool) <0x00042>
  at (wrapper remoting-invoke-with-check) System.Windows.Forms.Control.set_Visible (bool) <0xffffffff>
  at System.Windows.Forms.Application.RunLoop (bool,System.Windows.Forms.ApplicationContext) <0x002d4>
  at System.Windows.Forms.Application.Run (System.Windows.Forms.ApplicationContext) <0x00065>
  at System.Windows.Forms.Application.Run (System.Windows.Forms.Form) <0x0002e>
  at KeePass.Program.Main (string[]) <0x009ac>
  at (wrapper runtime-invoke) KeePass.Program.runtime_invoke_void_string[] (object,intptr,intptr,intptr) <0xffffffff>

Native stacktrace:

	mono [0x529d21]
	mono [0x43f99d]
	/lib/libpthread.so.0 [0x7f16527290f0]
	mono [0x4da50c]
	mono [0x4da6d7]
	mono [0x49fa5b]
	mono [0x49ffe3]
	[0x40beefcb]

Debug info from gdb:

(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 0x7f165340e710 (LWP 10507)]
[New Thread 0x40bc2950 (LWP 10509)]
[New Thread 0x41124950 (LWP 10508)]
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
0x00007f16522024b2 in select () from /lib/libc.so.6
  3 Thread 0x41124950 (LWP 10508)  0x00007f1652728851 in nanosleep ()
   from /lib/libpthread.so.0
  2 Thread 0x40bc2950 (LWP 10509)  0x00007f16527252d9 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/libpthread.so.0
  1 Thread 0x7f165340e710 (LWP 10507)  0x00007f16522024b2 in select ()
   from /lib/libc.so.6

Thread 3 (Thread 0x41124950 (LWP 10508)):
#0  0x00007f1652728851 in nanosleep () from /lib/libpthread.so.0
#1  0x00000000004c56e2 in ?? ()
#2  0x00007f16527213ea in start_thread () from /lib/libpthread.so.0
#3  0x00007f1652209cbd in clone () from /lib/libc.so.6
#4  0x0000000000000000 in ?? ()

Thread 2 (Thread 0x40bc2950 (LWP 10509)):
#0  0x00007f16527252d9 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/libpthread.so.0
#1  0x00000000004c8565 in ?? ()
#2  0x00000000004ca81b in ?? ()
#3  0x00000000004db96e in ?? ()
#4  0x0000000000470b93 in ?? ()
#5  0x000000000048d41b in ?? ()
#6  0x00000000004d9d33 in ?? ()
#7  0x00000000004f1582 in ?? ()
#8  0x00007f16527213ea in start_thread () from /lib/libpthread.so.0
#9  0x00007f1652209cbd in clone () from /lib/libc.so.6
#10 0x0000000000000000 in ?? ()

Thread 1 (Thread 0x7f165340e710 (LWP 10507)):
#0  0x00007f16522024b2 in select () from /lib/libc.so.6
#1  0x00007f1652bab5cc in g_spawn_sync () from /usr/lib/libglib-2.0.so.0
#2  0x00007f1652bab9a8 in g_spawn_command_line_sync ()
   from /usr/lib/libglib-2.0.so.0
#3  0x0000000000529dc8 in ?? ()
#4  0x000000000043f99d in ?? ()
#5  <signal handler called>
#6  0x00000000004da50c in ?? ()
#7  0x00000000004da6d7 in ?? ()
#8  0x000000000049fa5b in ?? ()
#9  0x000000000049ffe3 in ?? ()
#10 0x0000000040beefcb in ?? ()
#11 0x00000000011c3b30 in ?? ()
#12 0x000000004010ca84 in ?? ()
#13 0xffffffffffffffff in ?? ()
#14 0x00007f164a8fd908 in ?? ()
#15 0x00007f164a974118 in ?? ()
#16 0x00007fff5b429f70 in ?? ()
#17 0x00007fff5b429d80 in ?? ()
#18 0x00007f164a973690 in ?? ()
#19 0x00007f164a8c8540 in ?? ()
#20 0x00007f164a94e2a0 in ?? ()
#21 0x00007f164a8fdaa0 in ?? ()
#22 0x0000000040beeddb in ?? ()
#23 0x00007f164a8e67e0 in ?? ()
#24 0x00007f164a8c6cb0 in ?? ()
#25 0x00007f164a94e2a0 in ?? ()
#26 0x00007f1653263f00 in ?? ()
#27 0x00007f164a5efea0 in ?? ()
#28 0x0000000040bee9cf in ?? ()
#29 0x00007f164a974118 in ?? ()
#30 0x00007f164a8e67e0 in ?? ()
#31 0x00007fff5b429f40 in ?? ()
#32 0x0000000041f37766 in ?? ()
#33 0x00007f164a7b0280 in ?? ()
#34 0x00000000011c3b31 in ?? ()
#35 0x00007f165340e708 in ?? ()
#36 0x00000000017c5b10 in ?? ()
#37 0x0000000040bed1d0 in ?? ()
#38 0x00007f164a974118 in ?? ()
#39 0x00007fff5b42a5d0 in ?? ()
#40 0x00007fff5b429f80 in ?? ()
#41 0x00007f164a973690 in ?? ()
#42 0x00007f164a8c8540 in ?? ()
#43 0x00007f164a8e67e0 in ?? ()
#44 0x00007f164a8c6cb0 in ?? ()
#45 0x4064600000000000 in ?? ()
#46 0x40100c907da4e871 in ?? ()
#47 0x0000000042c00000 in ?? ()
#48 0x0000000000000000 in ?? ()
#0  0x00007f16522024b2 in select () from /lib/libc.so.6


=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Aborted
```

I have also tried building from source (2.07).  When I do that and mono the .exe the program seems to run fine; however, it crashes and gives the folloving when I tried to load a database file (even a freshly created one).  It then crashes on startup before the password/keyfile prompt as it tries to load last open database:

```
Invalid IL code in KeePass.Forms.KeyPromptForm:.ctor (): IL_002a: call      0x06000828


KeePass
  at (wrapper remoting-invoke-with-check) KeePass.Forms.KeyPromptForm:.ctor ()
  at KeePass.Forms.MainForm.OpenDatabase (KeePassLib.Serialization.IOConnectionInfo ioConnection, KeePassLib.Keys.CompositeKey cmpKey, Boolean bOpenLocal) [0x00000] 
  at KeePass.Forms.MainForm.OnFileOpen (System.Object sender, System.EventArgs e) [0x00000] 
  at System.Windows.Forms.ToolStripItem.OnClick (System.EventArgs e) [0x00000] 
  at System.Windows.Forms.ToolStripButton.OnClick (System.EventArgs e) [0x00000] 
  at System.Windows.Forms.ToolStripItem.HandleClick (System.EventArgs e) [0x00000] 
  at System.Windows.Forms.ToolStripItem.FireEvent (System.EventArgs e, ToolStripItemEventType met) [0x00000] 
  at (wrapper remoting-invoke-with-check) System.Windows.Forms.ToolStripItem:FireEvent (System.EventArgs,System.Windows.Forms.ToolStripItemEventType)
  at System.Windows.Forms.ToolStrip.OnMouseUp (System.Windows.Forms.MouseEventArgs mea) [0x00000] 
  at System.Windows.Forms.Control.WmLButtonUp (System.Windows.Forms.Message& m) [0x00000] 
  at System.Windows.Forms.Control.WndProc (System.Windows.Forms.Message& m) [0x00000] 
  at System.Windows.Forms.ScrollableControl.WndProc (System.Windows.Forms.Message& m) [0x00000] 
  at System.Windows.Forms.ToolStrip.WndProc (System.Windows.Forms.Message& m) [0x00000] 
  at KeePass.UI.CustomToolStripEx.WndProc (System.Windows.Forms.Message& m) [0x00000] 
  at System.Windows.Forms.Control+ControlWindowTarget.OnMessage (System.Windows.Forms.Message& m) [0x00000] 
  at System.Windows.Forms.Control+ControlNativeWindow.WndProc (System.Windows.Forms.Message& m) [0x00000] 
  at System.Windows.Forms.NativeWindow.WndProc (IntPtr hWnd, Msg msg, IntPtr wParam, IntPtr lParam) [0x00000] 
  at System.Windows.Forms.XplatUIX11.DispatchMessage (System.Windows.Forms.MSG& msg) [0x00000] 
  at System.Windows.Forms.XplatUI.DispatchMessage (System.Windows.Forms.MSG& msg) [0x00000] 
  at System.Windows.Forms.Application.RunLoop (Boolean Modal, System.Windows.Forms.ApplicationContext context) [0x00000] 
  at System.Windows.Forms.Application.Run (System.Windows.Forms.ApplicationContext context) [0x00000] 
  at System.Windows.Forms.Application.Run (System.Windows.Forms.Form mainForm) [0x00000] 
  at KeePass.Program.Main (System.String[] args) [0x00000] 
Void OpenDatabase(KeePassLib.Serialization.IOConnectionInfo, KeePassLib.Keys.CompositeKey, Boolean)


```

---

### Post by jakommo on 2009-04-03
It's a pity I tried it on jaunty beta (64bit) with 2.07B portable but it still doesn't work.

---

### Post by user2037 on 2009-04-13
I'm getting the same "Invalid IL code... Void OpenDatabase..." issue.

Compiling Mono 2.2 from source worked for me, but that caused other problems with Banshee.

Unfortunately it seems that Mono is quite a mess on Ubuntu and Debian as many patches have been added to the 1.x branch.

---

### Post by directhex on 2009-04-13
> **jakommo said:**
> It's a pity I tried it on jaunty beta (64bit) with 2.07B portable but it still doesn't work.

Seems fine here? What exactly is it doing/not doing?

---

### Post by Ux64 on 2009-05-01
> **jakommo said:**
> It's a pity I tried it on jaunty beta (64bit) with 2.07B portable but it still doesn't work.

I tried it with Jaunty (Final) just moments ago. And it did work perfectly for me. I would like to use that 2.07 beta for production too. (With proper backups) But I'm still looking for twofish plugin for it. I don't prefer using AES if proper alternatives are available.

---

### Post by jakommo on 2009-05-04
> **Ux64 said:**
> I tried it with Jaunty (Final) just moments ago. And it did work perfectly for me. I would like to use that 2.07 beta for production too. (With proper backups) But I'm still looking for twofish plugin for it. I don't prefer using AES if proper alternatives are available.

Ok it works now for me too, the problem was I hadn't installed libmono-winforms2.0-cli after upgrading to jaunty.

---

### Post by user2037 on 2009-05-07
Keepass 2 started working with the Jaunty upgrade. However, trying to change the theme by setting "MONO_THEME" has apparently caused problems because subsequent attempts to run Kp2 again fail.

---

