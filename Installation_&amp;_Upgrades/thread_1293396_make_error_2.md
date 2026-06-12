---
title: "make error 2"
date: 2009-10-17
forum: Installation &amp; Upgrades
---

### Post by u_kapaley256 on 2009-10-17
Hi all,
I am trying to install gyachi on my system and after a lot of fighting with the configure i get a make error(error 2)! thats awesome.And i have no idea whatsoever what to do with it and google doesnt help either.
I hope you guys will be able to help
I have some of the output here :- 

Thanks 

util.c: In function ‘play_sound’:
util.c:2689: warning: ‘my_command’ is used uninitialized in this function
yahoochat.c: In function ‘ymsg_reject_buddy_cb’:
yahoochat.c:1841: warning: ‘ptr’ may be used uninitialized in this function
yahoochat.c: In function ‘ymsg_messenger_logout’:
yahoochat.c:969: warning: ‘ptr’ may be used uninitialized in this function
yahoochat.c: In function ‘ymsg_passthrough’:
yahoochat.c:928: warning: ‘ptr’ may be used uninitialized in this function
pmwindow.c: In function ‘create_pm_session’:
pmwindow.c:659: warning: ‘yphoto’ may be used uninitialized in this function
In file included from afl.c:30:
wine/winbase.h:544: warning: ‘packed’ attribute ignored for field of type ‘CHAR[8]’
cpudetect.c:448: warning: ‘sigill_handler’ defined but not used
In file included from win32.h:13,
                 from driver.c:18:
wine/winbase.h:544: warning: ‘packed’ attribute ignored for field of type ‘CHAR[8]’
In file included from driver.c:20:
wine/pe_image.h:60: warning: ‘packed’ attribute ignored for field of type ‘BYTE’
wine/pe_image.h:62: warning: ‘packed’ attribute ignored for field of type ‘BYTE’
wine/pe_image.h:64: warning: ‘packed’ attribute ignored for field of type ‘BYTE’
wine/pe_image.h:66: warning: ‘packed’ attribute ignored for field of type ‘BYTE’
wine/pe_image.h:67: warning: ‘packed’ attribute ignored for field of type ‘BYTE’
wine/pe_image.h:69: warning: ‘packed’ attribute ignored for field of type ‘BYTE’
In file included from ext.c:29:
wine/winbase.h:544: warning: ‘packed’ attribute ignored for field of type ‘CHAR[8]’
ext.c: In function ‘VirtualAlloc’:
ext.c:516: warning: format ‘%ld’ expects type ‘long int’, but argument 3 has type ‘DWORD’
In file included from wine/pe_image.h:5,
                 from pe_resource.c:24:
wine/winbase.h:544: warning: ‘packed’ attribute ignored for field of type ‘CHAR[8]’
In file included from pe_resource.c:24:
wine/pe_image.h:60: warning: ‘packed’ attribute ignored for field of type ‘BYTE’
wine/pe_image.h:62: warning: ‘packed’ attribute ignored for field of type ‘BYTE’
wine/pe_image.h:64: warning: ‘packed’ attribute ignored for field of type ‘BYTE’
wine/pe_image.h:66: warning: ‘packed’ attribute ignored for field of type ‘BYTE’
wine/pe_image.h:67: warning: ‘packed’ attribute ignored for field of type ‘BYTE’
wine/pe_image.h:69: warning: ‘packed’ attribute ignored for field of type ‘BYTE’
In file included from registry.c:16:
wine/winbase.h:544: warning: ‘packed’ attribute ignored for field of type ‘CHAR[8]’
In file included from resource.c:24:
wine/winbase.h:544: warning: ‘packed’ attribute ignored for field of type ‘CHAR[8]’
In file included from wine/module.h:11,
                 from resource.c:28:
wine/pe_image.h:60: warning: ‘packed’ attribute ignored for field of type ‘BYTE’
wine/pe_image.h:62: warning: ‘packed’ attribute ignored for field of type ‘BYTE’
wine/pe_image.h:64: warning: ‘packed’ attribute ignored for field of type ‘BYTE’
wine/pe_image.h:66: warning: ‘packed’ attribute ignored for field of type ‘BYTE’
wine/pe_image.h:67: warning: ‘packed’ attribute ignored for field of type ‘BYTE’
wine/pe_image.h:69: warning: ‘packed’ attribute ignored for field of type ‘BYTE’
resource.c: In function ‘LoadMessageA’:
resource.c:402: warning: format ‘%08lx’ expects type ‘long unsigned int’, but argument 2 has type ‘HMODULE’
resource.c:402: warning: format ‘%08lx’ expects type ‘long unsigned int’, but argument 3 has type ‘UINT’
resource.c:402: warning: format ‘%ld’ expects type ‘long int’, but argument 5 has type ‘unsigned int’
In file included from win32.h:13,
                 from vfl.c:16:
wine/winbase.h:544: warning: ‘packed’ attribute ignored for field of type ‘CHAR[8]’
In file included from win32.c:35:
wine/winbase.h:544: warning: ‘packed’ attribute ignored for field of type ‘CHAR[8]’
In file included from wine/module.h:11,
                 from win32.c:40:
wine/pe_image.h:60: warning: ‘packed’ attribute ignored for field of type ‘BYTE’
wine/pe_image.h:62: warning: ‘packed’ attribute ignored for field of type ‘BYTE’
wine/pe_image.h:64: warning: ‘packed’ attribute ignored for field of type ‘BYTE’
wine/pe_image.h:66: warning: ‘packed’ attribute ignored for field of type ‘BYTE’
wine/pe_image.h:67: warning: ‘packed’ attribute ignored for field of type ‘BYTE’
wine/pe_image.h:69: warning: ‘packed’ attribute ignored for field of type ‘BYTE’
win32.c: In function ‘expGetSystemInfo’:
win32.c:1021: warning: format ‘%ld’ expects type ‘long int’, but argument 3 has type ‘DWORD’
win32.c:1048: warning: format ‘%ld’ expects type ‘long int’, but argument 3 has type ‘DWORD’
win32.c: In function ‘expGetFullPathNameA’:
win32.c:3534: warning: assignment discards qualifiers from pointer target type
win32.c: In function ‘expExitProcess’:
win32.c:4408: warning: format ‘%ld’ expects type ‘long int’, but argument 2 has type ‘DWORD’
win32.c: At top level:
win32.c:3245: warning: ‘qtx_dir’ defined but not used
In file included from wine/heap.h:12,
                 from module.c:35:
wine/winbase.h:544: warning: ‘packed’ attribute ignored for field of type ‘CHAR[8]’
In file included from wine/module.h:11,
                 from module.c:36:
wine/pe_image.h:60: warning: ‘packed’ attribute ignored for field of type ‘BYTE’
wine/pe_image.h:62: warning: ‘packed’ attribute ignored for field of type ‘BYTE’
wine/pe_image.h:64: warning: ‘packed’ attribute ignored for field of type ‘BYTE’
wine/pe_image.h:66: warning: ‘packed’ attribute ignored for field of type ‘BYTE’
wine/pe_image.h:67: warning: ‘packed’ attribute ignored for field of type ‘BYTE’
wine/pe_image.h:69: warning: ‘packed’ attribute ignored for field of type ‘BYTE’
module.c: In function ‘MODULE_LoadLibraryExA’:
module.c:332: warning: format ‘%08lx’ expects type ‘long unsigned int’, but argument 3 has type ‘DWORD’
module.c: In function ‘MODULE_GetProcAddress’:
module.c:963: warning: assignment from incompatible pointer type
In file included from pe_image.c:57:
wine/winbase.h:544: warning: ‘packed’ attribute ignored for field of type ‘CHAR[8]’
In file included from pe_image.c:60:
wine/pe_image.h:60: warning: ‘packed’ attribute ignored for field of type ‘BYTE’
wine/pe_image.h:62: warning: ‘packed’ attribute ignored for field of type ‘BYTE’
wine/pe_image.h:64: warning: ‘packed’ attribute ignored for field of type ‘BYTE’
wine/pe_image.h:66: warning: ‘packed’ attribute ignored for field of type ‘BYTE’
wine/pe_image.h:67: warning: ‘packed’ attribute ignored for field of type ‘BYTE’
wine/pe_image.h:69: warning: ‘packed’ attribute ignored for field of type ‘BYTE’
pe_image.c: In function ‘dump_exports’:
pe_image.c:91: warning: format ‘%ld’ expects type ‘long int’, but argument 3 has type ‘DWORD’
pe_image.c:91: warning: format ‘%ld’ expects type ‘long int’, but argument 4 has type ‘DWORD’
pe_image.c:103: warning: format ‘%4ld’ expects type ‘long int’, but argument 2 has type ‘unsigned int’
pe_image.c: In function ‘PE_FindExportedFunction’:
pe_image.c:209: warning: format ‘%ld’ expects type ‘long int’, but argument 2 has type ‘DWORD’
pe_image.c: In function ‘calc_vma_size’:
pe_image.c:364: warning: format ‘%4.4lx’ expects type ‘long unsigned int’, but argument 3 has type ‘DWORD’
pe_image.c:364: warning: format ‘%8.8lx’ expects type ‘long unsigned int’, but argument 4 has type ‘DWORD’
pe_image.c:364: warning: format ‘%8.8lx’ expects type ‘long unsigned int’, but argument 5 has type ‘DWORD’
pe_image.c:364: warning: format ‘%8.8lx’ expects type ‘long unsigned int’, but argument 6 has type ‘DWORD’
pe_image.c:364: warning: format ‘%8.8lx’ expects type ‘long unsigned int’, but argument 7 has type ‘DWORD’
pe_image.c:364: warning: format ‘%8.8lx’ expects type ‘long unsigned int’, but argument 8 has type ‘DWORD’
pe_image.c:364: warning: format ‘%8.8lx’ expects type ‘long unsigned int’, but argument 11 has type ‘DWORD’
pe_image.c: In function ‘do_relocations’:
pe_image.c:387: warning: format ‘%lx’ expects type ‘long unsigned int’, but argument 3 has type ‘DWORD’
pe_image.c: In function ‘PE_LoadImage’:
pe_image.c:461: warning: format ‘%ld’ expects type ‘long int’, but argument 2 has type ‘DWORD’
pe_image.c:469: warning: format ‘%ld’ expects type ‘long int’, but argument 2 has type ‘DWORD’
pe_image.c:483: warning: format ‘%08lx’ expects type ‘long unsigned int’, but argument 3 has type ‘DWORD’
pe_image.c:534: warning: format ‘%08lx’ expects type ‘long unsigned int’, but argument 3 has type ‘DWORD’
pe_image.c:607: warning: format ‘%lx’ expects type ‘long unsigned int’, but argument 2 has type ‘DWORD’
pe_image.c:607: warning: format ‘%lx’ expects type ‘long unsigned int’, but argument 3 has type ‘DWORD’
pe_image.c:609: warning: format ‘%lx’ expects type ‘long unsigned int’, but argument 3 has type ‘DWORD’
pe_image.c:637: warning: format ‘%lx’ expects type ‘long unsigned int’, but argument 5 has type ‘DWORD’
pe_image.c:637: warning: format ‘%lx’ expects type ‘long unsigned int’, but argument 6 has type ‘DWORD’
pe_image.c:637: warning: format ‘%lx’ expects type ‘long unsigned int’, but argument 7 has type ‘DWORD’
pe_image.c: In function ‘PE_InitDLL’:
pe_image.c:929: warning: format ‘%ld’ expects type ‘long int’, but argument 4 has type ‘DWORD’
protocol.c: In function ‘ytspextract’:
protocol.c:589: warning: implicit declaration of function ‘pthread_yield’
protocol.c: In function ‘loginYVoice’:
protocol.c:754: warning: comparison with string literal results in unspecified behaviour
sound.c: In function ‘play_incoming’:
sound.c:232: warning: implicit declaration of function ‘pthread_yield’
gyacheupload-ui.c: In function ‘on_close_ok_prop’:
gyacheupload-ui.c:696: warning: ‘event’ is used uninitialized in this function
gyachi-alsa.c: In function ‘alsa_open_device’:
gyachi-alsa.c:161: warning: the address of ‘hwparams’ will always evaluate as ‘true’
gyachi-gtkspell.c:32:31: error: gtkspell/gtkspell.h: No such file or directory
gyachi-gtkspell.c: In function ‘gtk_spell_activate’:
gyachi-gtkspell.c:55: error: ‘GtkSpell’ undeclared (first use in this function)
gyachi-gtkspell.c:55: error: (Each undeclared identifier is reported only once
gyachi-gtkspell.c:55: error: for each function it appears in.)
gyachi-gtkspell.c:55: error: ‘spell’ undeclared (first use in this function)
gyachi-gtkspell.c:58: warning: implicit declaration of function ‘gtkspell_get_from_text_view’
gyachi-gtkspell.c:62: warning: implicit declaration of function ‘gtkspell_new_attach’
gyachi-gtkspell.c:73: warning: implicit declaration of function ‘gtkspell_detach’
make[3]: *** [gyachi-gtkspell.lo] Error 1
make[2]: *** [all-recursive] Error 1
make[1]: *** [all-recursive] Error 1
make: *** [all] Error 2

---

### Post by rb0171610 on 2009-10-17
> **u_kapaley256 said:**
> Hi all,
I am trying to install gyachi on my system and after a lot of fighting with the configure i get a make error(error 2)! thats awesome.And i have no idea whatsoever what to do with it and google doesnt help either.
I hope you guys will be able to help
I have some of the output here :- 

Thanks 

gyachi-gtkspell.c:32:31: error: gtkspell/gtkspell.h: No such file or directory
gyachi-gtkspell.c: In function &#8216;gtk_spell_activate&#8217;:
gyachi-gtkspell.c:55: error: &#8216;GtkSpell&#8217; undeclared (first use in this function)
gyachi-gtkspell.c:55: error: (Each undeclared identifier is reported only once
gyachi-gtkspell.c:55: error: for each function it appears in.)
gyachi-gtkspell.c:55: error: &#8216;spell&#8217; undeclared (first use in this function)
gyachi-gtkspell.c:58: warning: implicit declaration of function &#8216;gtkspell_get_from_text_view&#8217;
gyachi-gtkspell.c:62: warning: implicit declaration of function &#8216;gtkspell_new_attach&#8217;
gyachi-gtkspell.c:73: warning: implicit declaration of function &#8216;gtkspell_detach&#8217;
make[3]: *** [gyachi-gtkspell.lo] Error 1
make[2]: *** [all-recursive] Error 1
make[1]: *** [all-recursive] Error 1
make: *** [all] Error 2
Do you have gtkspell and/or required gtkspell libraries installed?

---

### Post by rb0171610 on 2009-10-17
libgtkspell-dev - Development files for GtkSpell
libgtkspell0 - a spell-checking addon for GTK's TextView widget
libgtk2-spell-perl - Perl interface to the GtkSpell library

try:
```
sudo apt-get update
sudo apt-get install libgtkspell-dev libgtkspell0
```Then try to compile again.
I don't think the Perl package is necessary, but you can also install that if this doesn't solve your problem.

---

### Post by u_kapaley256 on 2009-10-17
Hi,
I used to think that all the dependencies are satisfied once i am done with the config.So i got to learn from you.

I installed the packages that you had suggested and then did the make and the make install and though i got some errors in make,no major tantrums 

But the app wont start!!
It cant be seen in the applications menu and although the <Alt>F2 run command recognises nothing shows up.

It would be great if you can throw some light on this.

Thanks for helping out last time.  

udayan@udayan:/media/sda1/linux_soft/gyachi-1.1.71$ make >> out_make
util.c: In function ‘play_sound’:
util.c:2689: warning: ‘my_command’ is used uninitialized in this function
yahoochat.c: In function ‘ymsg_reject_buddy_cb’:
yahoochat.c:1841: warning: ‘ptr’ may be used uninitialized in this function
yahoochat.c: In function ‘ymsg_messenger_logout’:
yahoochat.c:969: warning: ‘ptr’ may be used uninitialized in this function
yahoochat.c: In function ‘ymsg_passthrough’:
yahoochat.c:928: warning: ‘ptr’ may be used uninitialized in this function
pmwindow.c: In function ‘create_pm_session’:
pmwindow.c:659: warning: ‘yphoto’ may be used uninitialized in this function
In file included from afl.c:30:
wine/winbase.h:544: warning: ‘packed’ attribute ignored for field of type ‘CHAR[8]’
cpudetect.c:448: warning: ‘sigill_handler’ defined but not used
In file included from win32.h:13,
                 from driver.c:18:
wine/winbase.h:544: warning: ‘packed’ attribute ignored for field of type ‘CHAR[8]’
In file included from driver.c:20:
wine/pe_image.h:60: warning: ‘packed’ attribute ignored for field of type ‘BYTE’
wine/pe_image.h:62: warning: ‘packed’ attribute ignored for field of type ‘BYTE’
wine/pe_image.h:64: warning: ‘packed’ attribute ignored for field of type ‘BYTE’
wine/pe_image.h:66: warning: ‘packed’ attribute ignored for field of type ‘BYTE’
wine/pe_image.h:67: warning: ‘packed’ attribute ignored for field of type ‘BYTE’
wine/pe_image.h:69: warning: ‘packed’ attribute ignored for field of type ‘BYTE’
In file included from ext.c:29:
wine/winbase.h:544: warning: ‘packed’ attribute ignored for field of type ‘CHAR[8]’
ext.c: In function ‘VirtualAlloc’:
ext.c:516: warning: format ‘%ld’ expects type ‘long int’, but argument 3 has type ‘DWORD’
In file included from wine/pe_image.h:5,
                 from pe_resource.c:24:
wine/winbase.h:544: warning: ‘packed’ attribute ignored for field of type ‘CHAR[8]’
In file included from pe_resource.c:24:
wine/pe_image.h:60: warning: ‘packed’ attribute ignored for field of type ‘BYTE’
wine/pe_image.h:62: warning: ‘packed’ attribute ignored for field of type ‘BYTE’
wine/pe_image.h:64: warning: ‘packed’ attribute ignored for field of type ‘BYTE’
wine/pe_image.h:66: warning: ‘packed’ attribute ignored for field of type ‘BYTE’
wine/pe_image.h:67: warning: ‘packed’ attribute ignored for field of type ‘BYTE’
wine/pe_image.h:69: warning: ‘packed’ attribute ignored for field of type ‘BYTE’
In file included from registry.c:16:
wine/winbase.h:544: warning: ‘packed’ attribute ignored for field of type ‘CHAR[8]’
In file included from resource.c:24:
wine/winbase.h:544: warning: ‘packed’ attribute ignored for field of type ‘CHAR[8]’
In file included from wine/module.h:11,
                 from resource.c:28:
wine/pe_image.h:60: warning: ‘packed’ attribute ignored for field of type ‘BYTE’
wine/pe_image.h:62: warning: ‘packed’ attribute ignored for field of type ‘BYTE’
wine/pe_image.h:64: warning: ‘packed’ attribute ignored for field of type ‘BYTE’
wine/pe_image.h:66: warning: ‘packed’ attribute ignored for field of type ‘BYTE’
wine/pe_image.h:67: warning: ‘packed’ attribute ignored for field of type ‘BYTE’
wine/pe_image.h:69: warning: ‘packed’ attribute ignored for field of type ‘BYTE’
resource.c: In function ‘LoadMessageA’:
resource.c:402: warning: format ‘%08lx’ expects type ‘long unsigned int’, but argument 2 has type ‘HMODULE’
resource.c:402: warning: format ‘%08lx’ expects type ‘long unsigned int’, but argument 3 has type ‘UINT’
resource.c:402: warning: format ‘%ld’ expects type ‘long int’, but argument 5 has type ‘unsigned int’
In file included from win32.h:13,
                 from vfl.c:16:
wine/winbase.h:544: warning: ‘packed’ attribute ignored for field of type ‘CHAR[8]’
In file included from win32.c:35:
wine/winbase.h:544: warning: ‘packed’ attribute ignored for field of type ‘CHAR[8]’
In file included from wine/module.h:11,
                 from win32.c:40:
wine/pe_image.h:60: warning: ‘packed’ attribute ignored for field of type ‘BYTE’
wine/pe_image.h:62: warning: ‘packed’ attribute ignored for field of type ‘BYTE’
wine/pe_image.h:64: warning: ‘packed’ attribute ignored for field of type ‘BYTE’
wine/pe_image.h:66: warning: ‘packed’ attribute ignored for field of type ‘BYTE’
wine/pe_image.h:67: warning: ‘packed’ attribute ignored for field of type ‘BYTE’
wine/pe_image.h:69: warning: ‘packed’ attribute ignored for field of type ‘BYTE’
win32.c: In function ‘expGetSystemInfo’:
win32.c:1021: warning: format ‘%ld’ expects type ‘long int’, but argument 3 has type ‘DWORD’
win32.c:1048: warning: format ‘%ld’ expects type ‘long int’, but argument 3 has type ‘DWORD’
win32.c: In function ‘expGetFullPathNameA’:
win32.c:3534: warning: assignment discards qualifiers from pointer target type
win32.c: In function ‘expExitProcess’:
win32.c:4408: warning: format ‘%ld’ expects type ‘long int’, but argument 2 has type ‘DWORD’
win32.c: At top level:
win32.c:3245: warning: ‘qtx_dir’ defined but not used
In file included from wine/heap.h:12,
                 from module.c:35:
wine/winbase.h:544: warning: ‘packed’ attribute ignored for field of type ‘CHAR[8]’
In file included from wine/module.h:11,
                 from module.c:36:
wine/pe_image.h:60: warning: ‘packed’ attribute ignored for field of type ‘BYTE’
wine/pe_image.h:62: warning: ‘packed’ attribute ignored for field of type ‘BYTE’
wine/pe_image.h:64: warning: ‘packed’ attribute ignored for field of type ‘BYTE’
wine/pe_image.h:66: warning: ‘packed’ attribute ignored for field of type ‘BYTE’
wine/pe_image.h:67: warning: ‘packed’ attribute ignored for field of type ‘BYTE’
wine/pe_image.h:69: warning: ‘packed’ attribute ignored for field of type ‘BYTE’
module.c: In function ‘MODULE_LoadLibraryExA’:
module.c:332: warning: format ‘%08lx’ expects type ‘long unsigned int’, but argument 3 has type ‘DWORD’
module.c: In function ‘MODULE_GetProcAddress’:
module.c:963: warning: assignment from incompatible pointer type
In file included from pe_image.c:57:
wine/winbase.h:544: warning: ‘packed’ attribute ignored for field of type ‘CHAR[8]’
In file included from pe_image.c:60:
wine/pe_image.h:60: warning: ‘packed’ attribute ignored for field of type ‘BYTE’
wine/pe_image.h:62: warning: ‘packed’ attribute ignored for field of type ‘BYTE’
wine/pe_image.h:64: warning: ‘packed’ attribute ignored for field of type ‘BYTE’
wine/pe_image.h:66: warning: ‘packed’ attribute ignored for field of type ‘BYTE’
wine/pe_image.h:67: warning: ‘packed’ attribute ignored for field of type ‘BYTE’
wine/pe_image.h:69: warning: ‘packed’ attribute ignored for field of type ‘BYTE’
pe_image.c: In function ‘dump_exports’:
pe_image.c:91: warning: format ‘%ld’ expects type ‘long int’, but argument 3 has type ‘DWORD’
pe_image.c:91: warning: format ‘%ld’ expects type ‘long int’, but argument 4 has type ‘DWORD’
pe_image.c:103: warning: format ‘%4ld’ expects type ‘long int’, but argument 2 has type ‘unsigned int’
pe_image.c: In function ‘PE_FindExportedFunction’:
pe_image.c:209: warning: format ‘%ld’ expects type ‘long int’, but argument 2 has type ‘DWORD’
pe_image.c: In function ‘calc_vma_size’:
pe_image.c:364: warning: format ‘%4.4lx’ expects type ‘long unsigned int’, but argument 3 has type ‘DWORD’
pe_image.c:364: warning: format ‘%8.8lx’ expects type ‘long unsigned int’, but argument 4 has type ‘DWORD’
pe_image.c:364: warning: format ‘%8.8lx’ expects type ‘long unsigned int’, but argument 5 has type ‘DWORD’
pe_image.c:364: warning: format ‘%8.8lx’ expects type ‘long unsigned int’, but argument 6 has type ‘DWORD’
pe_image.c:364: warning: format ‘%8.8lx’ expects type ‘long unsigned int’, but argument 7 has type ‘DWORD’
pe_image.c:364: warning: format ‘%8.8lx’ expects type ‘long unsigned int’, but argument 8 has type ‘DWORD’
pe_image.c:364: warning: format ‘%8.8lx’ expects type ‘long unsigned int’, but argument 11 has type ‘DWORD’
pe_image.c: In function ‘do_relocations’:
pe_image.c:387: warning: format ‘%lx’ expects type ‘long unsigned int’, but argument 3 has type ‘DWORD’
pe_image.c: In function ‘PE_LoadImage’:
pe_image.c:461: warning: format ‘%ld’ expects type ‘long int’, but argument 2 has type ‘DWORD’
pe_image.c:469: warning: format ‘%ld’ expects type ‘long int’, but argument 2 has type ‘DWORD’
pe_image.c:483: warning: format ‘%08lx’ expects type ‘long unsigned int’, but argument 3 has type ‘DWORD’
pe_image.c:534: warning: format ‘%08lx’ expects type ‘long unsigned int’, but argument 3 has type ‘DWORD’
pe_image.c:607: warning: format ‘%lx’ expects type ‘long unsigned int’, but argument 2 has type ‘DWORD’
pe_image.c:607: warning: format ‘%lx’ expects type ‘long unsigned int’, but argument 3 has type ‘DWORD’
pe_image.c:609: warning: format ‘%lx’ expects type ‘long unsigned int’, but argument 3 has type ‘DWORD’
pe_image.c:637: warning: format ‘%lx’ expects type ‘long unsigned int’, but argument 5 has type ‘DWORD’
pe_image.c:637: warning: format ‘%lx’ expects type ‘long unsigned int’, but argument 6 has type ‘DWORD’
pe_image.c:637: warning: format ‘%lx’ expects type ‘long unsigned int’, but argument 7 has type ‘DWORD’
pe_image.c: In function ‘PE_InitDLL’:
pe_image.c:929: warning: format ‘%ld’ expects type ‘long int’, but argument 4 has type ‘DWORD’
protocol.c: In function ‘ytspextract’:
protocol.c:589: warning: implicit declaration of function ‘pthread_yield’
protocol.c: In function ‘loginYVoice’:
protocol.c:754: warning: comparison with string literal results in unspecified behaviour
sound.c: In function ‘play_incoming’:
sound.c:232: warning: implicit declaration of function ‘pthread_yield’
gyacheupload-ui.c: In function ‘on_close_ok_prop’:
gyacheupload-ui.c:696: warning: ‘event’ is used uninitialized in this function
gyachi-alsa.c: In function ‘alsa_open_device’:
gyachi-alsa.c:161: warning: the address of ‘hwparams’ will always evaluate as ‘true’

---

### Post by rb0171610 on 2009-10-17
[quote=u_kapaley256;8119447]Hi,
I used to think that all the dependencies are satisfied once i am done with the config.So i got to learn from you.

I installed the packages that you had suggested and then did the make and the make install and though i got some errors in make,no major tantrums 

But the app wont start!!
It cant be seen in the applications menu and although the <Alt>F2 run command recognises nothing shows up.

It would be great if you can throw some light on this.

Thanks for helping out last time.[quote]
No problem. The last I knew, correct me if I am wrong, the Gyachi project was no longer being updated. This may be what is causing the problem, it is simply outdated and no longer compatible with currently installed libraries that you are building it against.  That being said, since you were able to compile it, I would try running it in the terminal by typing the command name.
  The alt + F2 seems like a wonderful way to start a program, as opposed to the search + point + click icon in the start menu method, an advanced user who is having problems with a program will try running the program from the command line to get more feedback:
```
program_name
```
sometimes the program has switches like 'verbose', to find out type program name followed by --help:
```
program_name --help 
```
might return:
```
program_name
       -v verbose
       -d debug mode
```

If it shows up in the start menu in Gnome, sometimes u can find the name of the executable that way. 

The executable is probably found in /usr/bin/
(user binaries)
so you if you do not know the exact program name, try searching /usr/bin/ for it.  First update the index (database) with:
```
sudo updatedb
```

and then search for it:
```
locate gyachi
``` 
or 
```
locate gy*
``` 
or 
```
locate  Gy*
```
or
```
ls /usr/bin/gy*
```
or
```
ls /usr/bin/g*
```
or
```
ls /usr/bin/G*
```
until you find something that matches.  

Good luck.

---

