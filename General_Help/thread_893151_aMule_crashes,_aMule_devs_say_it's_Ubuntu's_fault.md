---
title: "aMule crashes, aMule devs say it's Ubuntu's fault"
date: 2008-08-18
forum: General Help
---

### Post by irinotecan on 2008-08-18
I have been having problems with aMule randomly crashing after a few hours of running on HH.  The forums over at amule.org say it's not their problem, it has something to do with Ubuntu not using up-to-date libraries that they depend on.

This is the backtrace from the crash:
```
(amule:29329): GLib-WARNING **: /build/buildd/glib2.0-2.16.4/glib/giounix.c:400 
Error while getting flags for FD: Bad file descriptor (9)


--------------------------------------------------------------------------------
A fatal error has occurred and aMule has crashed.
Please assist us in fixing this problem by posting the backtrace below in our
'aMule Crashes' forum and include as much information as possible regarding the
circumstances of this crash. The forum is located here:
    http://forum.amule.org/index.php?board=67.0
If possible, please try to generate a real backtrace of this crash:
    http://www.amule.org/wiki/index.php/Backtraces

----------------------------=| BACKTRACE FOLLOWS: |=----------------------------
Current version is: aMule SVN using wxGTK2 v2.8.7 (Snapshot: Mon Feb 18 07:02:15 CET 2008)
Running on: Linux 2.6.24-19-generic i686

[2] wxThreadHelperThread::~wxThreadHelperThread() in amule [0x8085b51]
[3] wxFatalSignalHandler in /usr/lib/libwx_baseu-2.8.so.0[0xb75b61d6]
[4] ?? in [0xb7f20420]
[5] ?? in [0x98c1d29]
[6] ?? in /usr/lib/libgdk-x11-2.0.so.0 [0xb6e56bdf]
[7] ?? in /usr/lib/libglib-2.0.so.0 [0xb6d3a0ed]
[8] g_main_context_dispatch in /usr/lib/libglib-2.0.so.0[0xb6d05dd6]
[9] ?? in /usr/lib/libglib-2.0.so.0 [0xb6d09193]
[10] g_main_loop_run in /usr/lib/libglib-2.0.so.0[0xb6d09577]
[11] gtk_main in /usr/lib/libgtk-x11-2.0.so.0[0xb7008264]
[12] wxEventLoop::Run() in /usr/lib/libwx_gtk2u_core-2.8.so.0[0xb778971c]
[13] wxAppBase::MainLoop() in /usr/lib/libwx_gtk2u_core-2.8.so.0[0xb782c32e]
[14] wxAppBase::OnRun() in /usr/lib/libwx_gtk2u_core-2.8.so.0[0xb782b981]
[15] wxEntry(int&, wchar_t**) in /usr/lib/libwx_baseu-2.8.so.0[0xb754605a]
[16] wxEntry(int&, char**) in /usr/lib/libwx_baseu-2.8.so.0[0xb7546107]
[17] std::basic_string<char, std::char_traits<char>, std::allocator<char> > std::operator+<char, std::char_traits<char>, std::allocator<char> >(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&) in amule [0x8162880]
[18] __libc_start_main in /lib/tls/i686/cmov/libc.so.6[0xb7253450]
[19] wxNotebook::SetPadding(wxSize const&) in amule[0x8084be1]


--------------------------------------------------------------------------------
Aborted

```

Does anyone have any ideas?

---

### Post by cariboo on 2008-08-18
Have you posted this bug on Launchpad. IF not include the backtrace, the devs are pretty good about getting back to you.

Jim

---

### Post by Vivaldi Gloria on 2008-08-18
> **irinotecan said:**
> Does anyone have any ideas?

Don't install the latest amule. Use the one in the repos. One older version but it works.

---

### Post by Festor on 2009-05-27
See this: [http://www.amule.org/amule/index.php?topic=15834.0](http://www.amule.org/amule/index.php?topic=15834.0)

And this: [http://www.amule.org/amule/index.php?topic=16647.0](http://www.amule.org/amule/index.php?topic=16647.0)

---

