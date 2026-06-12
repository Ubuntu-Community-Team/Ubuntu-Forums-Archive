---
title: "Openoffice won't start variant 2"
date: 2008-08-29
forum: General Help
---

### Post by phorgan1 on 2008-08-29
I started a different thread because the others I saw on this differed from mine in one respect.  Like them running any openoffice application results in a brief glimpse of a splash screen, but unlike them, running from the command line results in no output at all.  I return immediately to the command prompt, (along with the brief glimpse of the splash screen).  I did an apt-get purge "openoffice*", then apt-get install openoffice.org.  I did rm -rf .openoffice.org2, did apt-get remove openoffice.org-gtk (as mentioned on another site).  Nothing changes the behavior.  None of the logs under /var/log change their timestamps when I try to run openoffice so I don't think any errors are logged.  Running soffice.bin and oosplash.bin directly get the same behavior, i.e. brief splash, no error message.  Running soffice.bin in gdb results in a seg fault, unfortunately I don't have any symbols, but here's the stack backtrace:

Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread 0xb501b720 (LWP 16390)]
0xb4e6b4ea in ?? () from /usr/lib/openoffice/program/libgcc3_uno.so
(gdb) where
#0  0xb4e6b4ea in ?? () from /usr/lib/openoffice/program/libgcc3_uno.so
#1  0xb68a6cf5 in __gxx_exception_cleanup (code=_URC_FOREIGN_EXCEPTION_CAUGHT, 
    exc=0x1) at ../../../../gcc/libstdc++-v3/libsupc++/eh_throw.cc:55
#2  0xb67c365b in _Unwind_DeleteException (exc=0x1)
    at ../../../gcc-4.3.1/libgcc/../gcc/unwind.inc:276
#3  0xb68a5be0 in __cxa_end_catch ()
    at ../../../../gcc/libstdc++-v3/libsupc++/eh_catch.cc:127
#4  0xb762556a in ?? () from /usr/lib/openoffice/program/libutl680li.so
#5  0xb7626f22 in ?? () from /usr/lib/openoffice/program/libutl680li.so
#6  0xb7627f5c in utl::UcbLockBytes::CreateLockBytes ()
   from /usr/lib/openoffice/program/libutl680li.so
#7  0xb7636442 in ?? () from /usr/lib/openoffice/program/libutl680li.so
#8  0xb7636f3f in utl::UcbStreamHelper::CreateStream ()
   from /usr/lib/openoffice/program/libutl680li.so
#9  0xb6ad58e9 in ?? () from /usr/lib/openoffice/program/libsfx680li.so
#10 0xb6c94809 in ?? () from /usr/lib/openoffice/program/libsfx680li.so
#11 0xb6c94a84 in SfxDispatcher::SfxDispatcher ()
   from /usr/lib/openoffice/program/libsfx680li.so
#12 0xb6ad0bc1 in ?? () from /usr/lib/openoffice/program/libsfx680li.so
#13 0xb6ac3e4a in SfxApplication::GetOrCreate ()
   from /usr/lib/openoffice/program/libsfx680li.so
#14 0xb6cc2a4e in ?? () from /usr/lib/openoffice/program/libsfx680li.so
#15 0xb6cc2daa in ?? () from /usr/lib/openoffice/program/libsfx680li.so
#16 0xb72fd373 in ?? ()
   from /usr/lib/openoffice/program/libuno_cppuhelpergcc3.so.3
#17 0xb72f9180 in ?? ()
   from /usr/lib/openoffice/program/libuno_cppuhelpergcc3.so.3
#18 0xb72fa07b in ?? ()
   from /usr/lib/openoffice/program/libuno_cppuhelpergcc3.so.3
#19 0xb72fce18 in ?? ()
   from /usr/lib/openoffice/program/libuno_cppuhelpergcc3.so.3
#20 0xb72f9180 in ?? ()
   from /usr/lib/openoffice/program/libuno_cppuhelpergcc3.so.3
#21 0xb72fa0e9 in ?? ()
   from /usr/lib/openoffice/program/libuno_cppuhelpergcc3.so.3
#22 0xb4c7cbcd in ?? () from /usr/lib/openoffice/program/bootstrap.uno.so
#23 0xb4c777d7 in ?? () from /usr/lib/openoffice/program/bootstrap.uno.so
#24 0x08078041 in desktop::Desktop::Main ()
#25 0xb7c0edb6 in ?? () from /usr/lib/openoffice/program/libvcl680li.so
#26 0xb7c0eeb5 in SVMain () from /usr/lib/openoffice/program/libvcl680li.so
#27 0x08068909 in main ()

Hope this helps.

Patrick

---

