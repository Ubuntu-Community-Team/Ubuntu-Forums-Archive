---
title: "Problem installing ubuntu server 9.04 i386"
date: 2009-10-15
forum: Installation &amp; Upgrades
---

### Post by alex_z on 2009-10-15
Good time of day.
When you try to install this OS have problems at different stages of installation.  
 It is expressed either in the installation hangs on a blue screen or an error and the council to return to the main menu and from there to try to continue the installation. The most common problems arise when determining the disk or markup, but not always. I tried to install from a usb flash and dvd drive, same result. CD distribution and successfully tested. 

 hardware:  
 mb: asus p4s-800-mx se  
 cpu: pentium 4 3.2  
 ram: samsung 2x1G ddr400  
 hdd: wd 160G

```
m Product Name
[   12.500191] EIP: 0060:[<c01f2ffa>] EFLAGS: 00010202 CPU: 0
[   12.500198] EIP is at load_elf_binary+0x38a/0xbe0
[   12.500204] EAX: 00000000 EBX: 00000000 ECX: 00000500 EDX: f679f504
[   12.500208] ESI: f6039cb8 EDI: c05fabcf EBP: f678bf48 ESP: f678bea0
[   12.500214]  DS: 007b ES: 007b FS: 00d8 GS: 0000 SS: 0068
[   12.500220] Process grep (pid: 2429, ti=f678a000 task=f61ca5b0 task.ti=f678a000)
[   12.500226] Stack:
[   12.500229]  00000080 ffffffff f610dc00 f610db00 f6039c80 f678bfb8 00000007 f678bed0
[   12.500244]  f6174200 f61ca5b0 f610d400 00000000 f678bef8 c019dc2d f665eec0 f610d820
[   12.500259]  f610d800 ff6b2000 c1fbef60 c0856e80 00000100 f678befc f678bf0c 00000282
[   12.500276] Call Trace:
[   12.500281]  [<c019dc2d>] ? set_page_address+0xdd/0x1a0
[   12.500289]  [<c019ddaf>] ? page_address+0xbf/0xe0
[   12.500296]  [<c019de41>] ? kunmap_high+0x71/0xa0
[   12.500302]  [<c01f2c70>] ? load_elf_binary+0x0/0xbe0
[   12.500310]  [<c01c2169>] ? search_binary_handler+0xb9/0x260
[   12.500319]  [<c01c35a5>] ? do_execve+0x2b5/0x330
[   12.500326]  [<c0102353>] ? sys_execve+0x43/0x70
[   12.500332]  [<c0104062>] ? syscall_call+0x7/0xb
[   12.500339]  [<c0500000>] ? relay_hotcpu_callback+0x6d/0xbd
[   12.500347] Code: ff ff 64 a1 00 40 7b c0 83 60 0c bf 64 a1 00 40 7b c0 8b 80 cc 01 00 00 c7 40 78 00 00 00 00 83 45 c4 01 74 10 64 a1 00 90 7b c0 <81> 88 e8 01 00 ff 00 00 40 00 64 a1 00 40 7b c0 f6 80 ea 01 00 
[   12.500418] EIP: [<c01f2ffa>] load_elf_binary+0x38a/0xbe0 SS:ESP 0068:f678bea0
[   12.500427] ---[ end trace 4920237ae745bce7 ]---
[   12.502017] BUG: unable to handle kernel paging request at ff0001e8
[   12.502028] IP: [<c01f2ffa>] load_elf_binary+0x38a/0xbe0
[   12.502042] *pde = 00000000 
[   12.502049] Oops: 0002 [#3] SMP 
[   12.502055] last sysfs file: /sys/kernel/uevent_seqnum
[   12.502060] Modules linked in: usb_storage fbcon tileblit font bitblit softcursor vga16fb vgastate vesafb usbhid usbkbd
[   12.502080] 
[   12.502086] Pid: 2430, comm: cut Tainted: G      D    (2.6.28-11-generic #42-Ubuntu) System Product Name
[   12.502092] EIP: 0060:[<c01f2ffa>] EFLAGS: 00010202 CPU: 1
[   12.502098] EIP is at load_elf_binary+0x38a/0xbe0
[   12.502102] EAX: 00000000 EBX: 00000000 ECX: 00000500 EDX: f679e904
[   12.502106] ESI: f60d7db8 EDI: c05fabcf EBP: f60cdf48 ESP: f60cdea0
[   12.502110]  DS: 007b ES: 007b FS: 00d8 GS: 0000 SS: 0068
[   12.502115] Process cut (pid: 2430, ti=f60cc000 task=f61cbed0 task.ti=f60cc000)
[   12.502119] Stack:
[   12.502121]  00000080 ffffffff f67fbc00 f67fb500 f60d7d80 f60cdfb8 00000007 f60cded0
[   12.502134]  f612dc00 f61cbed0 f67fb700 00000000 f60cdef8 c019dc2d f6780460 f67fb620
[   12.502147]  f67fb600 ff6b3000 c1fbca80 c0856380 00000100 f60cdefc f60cdf0c 00000282
[   12.502161] Call Trace:
[   12.502165]  [<c019dc2d>] ? set_page_address+0xdd/0x1a0
[   12.502174]  [<c019ddaf>] ? page_address+0xbf/0xe0
[   12.502181]  [<c019de41>] ? kunmap_high+0x71/0xa0
[   12.502187]  [<c01f2c70>] ? load_elf_binary+0x0/0xbe0
[   12.502194]  [<c01c2169>] ? search_binary_handler+0xb9/0x260
[   12.502201]  [<c01c35a5>] ? do_execve+0x2b5/0x330
[   12.502208]  [<c0102353>] ? sys_execve+0x43/0x70
[   12.502216]  [<c0104062>] ? syscall_call+0x7/0xb
[   12.502222]  [<c0500000>] ? relay_hotcpu_callback+0x6d/0xbd
[   12.502232] Code: ff ff 64 a1 00 40 7b c0 83 60 0c bf 64 a1 00 40 7b c0 8b 80 cc 01 00 00 c7 40 78 00 00 00 00 83 45 c4 01 74 10 64 a1 00 90 7b c0 <81> 88 e8 01 00 ff 00 00 40 00 64 a1 00 40 7b c0 f6 80 ea 01 00 
[   12.502549] EIP: [<c01f2ffa>] load_elf_binary+0x38a/0xbe0 SS:ESP 0068:f60cdea0
[   12.502577] ---[ end trace 4920237ae745bce7 ]---
[   12.503046] BUG: unable to handle kernel paging request at ff0001e8
[   12.503054] IP: [<c01f2ffa>] load_elf_binary+0x38a/0xbe0
[   12.503065] *pde = 00000000 
[   12.503070] Oops: 0002 [#4] SMP 
[   12.503075] last sysfs file: /sys/kernel/uevent_seqnum
[   12.503080] Modules linked in: usb_storage fbcon tileblit font bitblit softcursor vga16fb vgastate vesafb usbhid usbkbd
[   12.503098] 
[   12.503103] Pid: 2431, comm: sed Tainted: G      D    (2.6.28-11-generic #42-Ubuntu) System Product Name
[   12.503109] EIP: 0060:[<c01f2ffa>] EFLAGS: 00010202 CPU: 1
[   12.503116] EIP is at load_elf_binary+0x38a/0xbe0
[   12.503120] EAX: 00000000 EBX: 00000000 ECX: 00000500 EDX: f679f204
[   12.503125] ESI: f60d7438 EDI: c05fabcf EBP: f6101f48 ESP: f6101ea0
[   12.503129]  DS: 007b ES: 007b FS: 00d8 GS: 0000 SS: 0068
[   12.503134] Process sed (pid: 2431, ti=f6100000 task=f61cb240 task.ti=f6100000)
[   12.503138] Stack:
[   12.503140]  00000080 ffffffff f67fbe00 f67fbf00 f60d7400 f6101fb8 00000007 f6101ed0
[   12.503153]  f612c400 f61cb240 f67fb800 00000000 f6101ef8 c019dc2d f67804c0 f67fb020
[   12.503168]  f67fb000 ff6b4000 c1fbeb20 c0855400 00000100 f6101efc f6101f0c 00000282
[   12.503184] Call Trace:
[   12.503188]  [<c019dc2d>] ? set_page_address+0xdd/0x1a0
[   12.503196]  [<c019ddaf>] ? page_address+0xbf/0xe0
[   12.503204]  [<c019de41>] ? kunmap_high+0x71/0xa0
[   12.503210]  [<c01f2c70>] ? load_elf_binary+0x0/0xbe0
[   12.503218]  [<c01c2169>] ? search_binary_handler+0xb9/0x260
[   12.503225]  [<c01c35a5>] ? do_execve+0x2b5/0x330
[   12.503231]  [<c0102353>] ? sys_execve+0x43/0x70
[   12.503238]  [<c0104062>] ? syscall_call+0x7/0xb
[   12.503244]  [<c0500000>] ? relay_hotcpu_callback+0x6d/0xbd
[   12.503253] Code: ff ff 64 a1 00 40 7b c0 83 60 0c bf 64 a1 00 40 7b c0 8b 80 cc 01 00 00 c7 40 78 00 00 00 00 83 45 c4 01 74 10 64 a1 00 90 7b c0 <81> 88 e8 01 00 ff 00 00 40 00 64 a1 00 40 7b c0 f6 80 ea 01 00 
[   12.503327] EIP: [<c01f2ffa>] load_elf_binary+0x38a/0xbe0 SS:ESP 0068:f6101ea0
[   12.503337] ---[ end trace 4920237ae745bce7 ]---
[   12.503808] BUG: unable to handle kernel paging request at ff0001e8
[   12.503822] IP: [<c01f2ffa>] load_elf_binary+0x38a/0xbe0
[   12.503833] *pde = 00000000 
[   12.503844] Oops: 0002 [#5] SMP 
[   12.503868] last sysfs file: /sys/kernel/uevent_seqnum
[   12.503878] Modules linked in: usb_storage fbcon tileblit font bitblit softcursor vga16fb vgastate vesafb usbhid usbkbd
[   12.504005] 
[   12.504009] Pid: 2432, comm: grep Tainted: G      D    (2.6.28-11-generic #42-Ubuntu) System Product Name
[   12.504014] EIP: 0060:[<c01f2ffa>] EFLAGS: 00010202 CPU: 1
[   12.504025] EIP is at load_elf_binary+0x38a/0xbe0
[   12.504029] EAX: 00000000 EBX: 00000000 ECX: 00000500 EDX: f679ef04
[   12.504039] ESI: f60d70b8 EDI: c05fabcf EBP: f60a7f48 ESP: f60a7ea0
[   12.504055]  DS: 007b ES: 007b FS: 00d8 GS: 0000 SS: 0068
[   12.504072] Process grep (pid: 2432, ti=f60a6000 task=f61c8000 task.ti=f60a6000)
[   12.504088] Stack:
[   12.504102]  00000080 ffffffff f6092100 f67fba00 f60d7080 f60a7fb8 00000007 00000000
[   12.504146]  f612c400 f61c8000 f6092a00 00000000 00000296 ff65e000 f6780540 f6092020
[   12.504195]  f6092000 ff65e000 c1fba6a0 c0856680 00000100 f60a7efc f60a7f0c 00000282
[   12.504209] Call Trace:
[   12.504212]  [<c019ddaf>] ? page_address+0xbf/0xe0
[   12.504219]  [<c019de41>] ? kunmap_high+0x71/0xa0
[   12.504224]  [<c01f2c70>] ? load_elf_binary+0x0/0xbe0
[   12.504231]  [<c01c2169>] ? search_binary_handler+0xb9/0x260
[   12.504250]  [<c01c35a5>] ? do_execve+0x2b5/0x330
[   12.504268]  [<c0102353>] ? sys_execve+0x43/0x70
[   12.504292]  [<c0104062>] ? syscall_call+0x7/0xb
[   12.504310]  [<c0500000>] ? relay_hotcpu_callback+0x6d/0xbd
[   12.504331] Code: ff ff 64 a1 00 40 7b c0 83 60 0c bf 64 a1 00 40 7b c0 8b 80 cc 01 00 00 c7 40 78 00 00 00 00 83 45 c4 01 74 10 64 a1 00 90 7b c0 <81> 88 e8 01 00 ff 00 00 40 00 64 a1 00 40 7b c0 f6 80 ea 01 00 
[   12.504751] EIP: [<c01f2ffa>] load_elf_binary+0x38a/0xbe0 SS:ESP 0068:f60a7ea0
[   12.504773] ---[ end trace 4920237ae745bce7 ]---
[   12.505697] BUG: unable to handle kernel paging request at ff0001e8
[   12.505706] IP: [<c01f2ffa>] load_elf_binary+0x38a/0xbe0
[   12.505717] *pde = 00000000 
[   12.505723] Oops: 0002 [#6] SMP 
[   12.505728] last sysfs file: /sys/kernel/uevent_seqnum
[   12.505733] Modules linked in: usb_storage fbcon tileblit font bitblit softcursor vga16fb vgastate vesafb usbhid usbkbd
[   12.505751] 
[   12.505757] Pid: 2433, comm: register-module Tainted: G      D    (2.6.28-11-generic #42-Ubuntu) System Product Name
[   12.505762] EIP: 0060:[<c01f2ffa>] EFLAGS: 00010202 CPU: 1
[   12.505769] EIP is at load_elf_binary+0x38a/0xbe0
[   12.505773] EAX: 00000000 EBX: 00000000 ECX: 00000500 EDX: f679f384
[   12.505777] ESI: f60d74b8 EDI: c05fabcf EBP: f61f1e7c ESP: f61f1dd4
[   12.505781]  DS: 007b ES: 007b FS: 00d8 GS: 0000 SS: 0068
[   12.505787] Process register-module (pid: 2433, ti=f61f0000 task=f61ce480 task.ti=f61f0000)
[   12.505791] Stack:
[   12.505794]  00000080 ffffffff f6092b00 f6092800 f60d7480 f61f1fb8 00000007 f61ce480
[   12.505808]  00000000 00000000 f640df00 f61ce480 c014ecb0 f61f1e08 f67804e0 f6092e20
[   12.505822]  f6092e00 c0618a41 00000100 00000000 00000100 f61f1e30 00000000 00000001
[   12.505837] Call Trace:
[   12.505842]  [<c014ecb0>] ? autoremove_wake_function+0x0/0x50
[   12.505855]  [<c01bd08d>] ? fsnotify_access+0x6d/0x80
[   12.505864]  [<c01bdcc3>] ? vfs_read+0xa3/0x100
[   12.505871]  [<c01bd460>] ? do_sync_read+0x0/0x110
[   12.505878]  [<c01f2c70>] ? load_elf_binary+0x0/0xbe0
[   12.505886]  [<c01c2169>] ? search_binary_handler+0xb9/0x260
[   12.505893]  [<c01f0d26>] ? load_script+0x1c6/0x220
[   12.505900]  [<c019dc2d>] ? set_page_address+0xdd/0x1a0
[   12.505908]  [<c019ddaf>] ? page_address+0xbf/0xe0
[   12.505915]  [<c019de41>] ? kunmap_high+0x71/0xa0
[   12.505921]  [<c01f0b60>] ? load_script+0x0/0x220
[   12.505928]  [<c01c2169>] ? search_binary_handler+0xb9/0x260
[   12.505935]  [<c01c35a5>] ? do_execve+0x2b5/0x330
[   12.505941]  [<c0102353>] ? sys_execve+0x43/0x70
[   12.505949]  [<c0104062>] ? syscall_call+0x7/0xb
[   12.505956]  [<c0500000>] ? relay_hotcpu_callback+0x6d/0xbd
[   12.505965] Code: ff ff 64 a1 00 40 7b c0 83 60 0c bf 64 a1 00 40 7b c0 8b 80 cc 01 00 00 c7 40 78 00 00 00 00 83 45 c4 01 74 10 64 a1 00 90 7b c0 <81> 88 e8 01 00 ff 00 00 40 00 64 a1 00 40 7b c0 f6 80 ea 01 00 
[   12.506043] EIP: [<c01f2ffa>] load_elf_binary+0x38a/0xbe0 SS:ESP 0068:f61f1dd4
[   12.506055] ---[ end trace 4920237ae745bce7 ]---
[   12.506792] BUG: unable to handle kernel paging request at ff0001e8
[   12.506814] IP: [<c01f2ffa>] load_elf_binary+0x38a/0xbe0
[   12.506841] *pde = 00000000 
[   12.506869] Oops: 0002 [#7] SMP 
[   12.506899] last sysfs file: /sys/kernel/uevent_seqnum
[   12.506909] Modules linked in: usb_storage fbcon tileblit font bitblit softcursor vga16fb vgastate vesafb usbhid usbkbd
[   12.507032] 
[   12.507043] Pid: 2434, comm: logger Tainted: G      D    (2.6.28-11-generic #42-Ubuntu) System Product Name
[   12.507060] EIP: 0060:[<c01f2ffa>] EFLAGS: 00010202 CPU: 1
[   12.507077] EIP is at load_elf_binary+0x38a/0xbe0
[   12.507087] EAX: 00000000 EBX: 00000000 ECX: 00000500 EDX: f679f084
[   12.507104] ESI: f60d79b8 EDI: c05fabcf EBP: f608bf48 ESP: f608bea0
[   12.507114]  DS: 007b ES: 007b FS: 00d8 GS: 0000 SS: 0068
[   12.507131] Process logger (pid: 2434, ti=f608a000 task=f61ccb60 task.ti=f608a000)
[   12.507147] Stack:
[   12.507161]  00000080 ffffffff f672ff00 f672f900 f60d7980 f608bfb8 00000007 f608bed0
[   12.507258]  f612c400 f61ccb60 f672fe00 00000000 f608bef8 c019dc2d f67801c0 f672f620
[   12.507321]  f672f600 ff6b6000 c1fbafc0 c0855400 00000100 f608befc f608bf0c 00000282
[   12.507408] Call Trace:
[   12.507412]  [<c019dc2d>] ? set_page_address+0xdd/0x1a0
[   12.507437]  [<c019ddaf>] ? page_address+0xbf/0xe0
[   12.507449]  [<c019de41>] ? kunmap_high+0x71/0xa0
[   12.507456]  [<c01f2c70>] ? load_elf_binary+0x0/0xbe0
[   12.507468]  [<c01c2169>] ? search_binary_handler+0xb9/0x260
[   12.507482]  [<c01c35a5>] ? do_execve+0x2b5/0x330
[   12.507500]  [<c0102353>] ? sys_execve+0x43/0x70
[   12.507513]  [<c0104062>] ? syscall_call+0x7/0xb
[   12.507525]  [<c0500000>] ? relay_hotcpu_callback+0x6d/0xbd
[   12.507551] Code: ff ff 64 a1 00 40 7b c0 83 60 0c bf 64 a1 00 40 7b c0 8b 80 cc 01 00 00 c7 40 78 00 00 00 00 83 45 c4 01 74 10 64 a1 00 90 7b c0 <81> 88 e8 01 00 ff 00 00 40 00 64 a1 00 40 7b c0 f6 80 ea 01 00 
[   12.508012] EIP: [<c01f2ffa>] load_elf_binary+0x38a/0xbe0 SS:ESP 0068:f608bea0
[   12.508042] ---[ end trace 4920237ae745bce7 ]---
[   20.435840] ISO 9660 Extensions: Microsoft Joliet Level 3
[   20.508298] ISO 9660 Extensions: RRIP_1991A
[   50.673367] BUG: unable to handle kernel paging request at ff0001e8
[   50.673377] IP: [<c01f2ffa>] load_elf_binary+0x38a/0xbe0
[   50.673394] *pde = 00000000 
[   50.673399] Oops: 0002 [#8] SMP 
[   50.673404] last sysfs file: /sys/devices/pci0000:00/0000:00:05.0/host1/target1:0:0/1:0:0:0/block/sr0/uevent
[   50.673409] Modules linked in: nls_cp437 isofs usb_storage fbcon tileblit font bitblit softcursor vga16fb vgastate vesafb usbhid usbkbd
[   50.673425] 
[   50.673430] Pid: 6415, comm: udpkg Tainted: G      D    (2.6.28-11-generic #42-Ubuntu) System Product Name
[   50.673434] EIP: 0060:[<c01f2ffa>] EFLAGS: 00010202 CPU: 0
[   50.673437] EIP is at load_elf_binary+0x38a/0xbe0
[   50.673440] EAX: 00000000 EBX: 00000000 ECX: 00000500 EDX: f6745504
[   50.673442] ESI: f61095b8 EDI: c05fabcf EBP: f605bf48 ESP: f605bea0
[   50.673445]  DS: 007b ES: 007b FS: 00d8 GS: 0000 SS: 0068
[   50.673448] Process udpkg (pid: 6415, ti=f605a000 task=f611b240 task.ti=f605a000)
[   50.673450] Stack:
[   50.673452]  00000080 ffffffff f66af000 f66af900 f6109580 f605bfb8 00000007 00000000
[   50.673461]  f612dc00 f611b240 f60ff500 00000000 00000296 ff421000 f60d9cc0 f6727b20
[   50.673470]  f6727b00 ff421000 c1f75e40 c0857300 00000100 f605befc f605bf0c 00000282
[   50.673480] Call Trace:
[   50.673483]  [<c019ddaf>] ? page_address+0xbf/0xe0
[   50.673489]  [<c019de41>] ? kunmap_high+0x71/0xa0
[   50.673494]  [<c01f2c70>] ? load_elf_binary+0x0/0xbe0
[   50.673498]  [<c01c2169>] ? search_binary_handler+0xb9/0x260
[   50.673504]  [<c01c35a5>] ? do_execve+0x2b5/0x330
[   50.673508]  [<c0102353>] ? sys_execve+0x43/0x70
[   50.673513]  [<c0104062>] ? syscall_call+0x7/0xb
[   50.673517]  [<c0500000>] ? relay_hotcpu_callback+0x6d/0xbd
[   50.673524] Code: ff ff 64 a1 00 40 7b c0 83 60 0c bf 64 a1 00 40 7b c0 8b 80 cc 01 00 00 c7 40 78 00 00 00 00 83 45 c4 01 74 10 64 a1 00 90 7b c0 <81> 88 e8 01 00 ff 00 00 40 00 64 a1 00 40 7b c0 f6 80 ea 01 00 
[   50.673576] EIP: [<c01f2ffa>] load_elf_binary+0x38a/0xbe0 SS:ESP 0068:f605bea0
[   50.673584] ---[ end trace 4920237ae745bce7 ]---
[  108.676018] usb 1-6: new high speed USB device using ehci_hcd and address 3
[  108.822561] usb 1-6: configuration #1 chosen from 1 choice
[  108.831765] scsi4 : SCSI emulation for USB Mass Storage devices
[  108.840612] usb-storage: device found at 3
[  108.848638] usb-storage: waiting for device to settle before scanning
[  113.856324] usb-storage: device scan complete
[  113.864304] scsi 4:0:0:0: Direct-Access     JetFlash Transcend 2GB    8.07 PQ: 0 ANSI: 2
[  113.882245] sd 4:0:0:0: [sdb] 3944446 512-byte hardware sectors: (2.01 GB/1.87 GiB)
[  113.900282] sd 4:0:0:0: [sdb] Write Protect is off
[  113.909153] sd 4:0:0:0: [sdb] Mode Sense: 03 00 00 00
[  113.917939] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  113.928785] sd 4:0:0:0: [sdb] 3944446 512-byte hardware sectors: (2.01 GB/1.87 GiB)
[  113.947280] sd 4:0:0:0: [sdb] Write Protect is off
[  113.956450] sd 4:0:0:0: [sdb] Mode Sense: 03 00 00 00
[  113.965439] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  113.973884]  sdb: sdb1
[  114.991744] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[  115.001101] sd 4:0:0:0: Attached scsi generic sg2 type 0 
```

---

### Post by phillw on 2009-10-15
The most common causes of 'odd' behaviour when installing are as follows

1) The cd that the install image was written to was not written at 4X speed (or, even below). It is a re-occuring theme & would be my 1st thing to check.
2) The lens on the cd-writer needs cleaning.

Whilst you can happily 'burn' music cd's at 52X speed - the iso-image required for installations has a much, much lower margin of error.

You do not say if you are installing onto a machine with windows already on it ?

Hope that is of help,

Phill.

---

