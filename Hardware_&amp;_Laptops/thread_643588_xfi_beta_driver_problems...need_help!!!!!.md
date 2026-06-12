---
title: "xfi beta driver problems...need help!!!!!"
date: 2007-12-17
forum: Hardware &amp; Laptops
---

### Post by adramalech on 2007-12-17
here is my problem when i go to the make install command part after i do all the other steps by the guys who made the xfi beta driver work...it says that i should :

Q: dmesg shows "ctalsa: Unknown symbol malloc_sizes" and the thing stops here.  
A: Your kernel is compiled with SLUB. But SLAB is required because of malloc_sizes which is not in SLUB. 
---> Rebuild your Kernel with SLAB 

Q: dmesg shows "Unknown symbol __stack_chk_fail" and the thing stops here.
A: you need -fno-stack-protector" to CFLAGS
---> edit Makefile.conf and add -fno-stack-protector" to CFLAGS 

i dont know how to check to see if my kernel is compiled in slab instead of slub and
i have tried to do the -fno-stack-protector with no advail...anybody know how to fix my problem????


here is the url to look at what the steps are...they also made a patch..etc.
[http://blackbox.lostwave.net/x-fi/readme.txt ](http://blackbox.lostwave.net/x-fi/readme.txt )


this is my dmesg when i go to put make install command in the directory of my xfi crap..

[  357.599126] ctossrv: Unknown symbol __stack_chk_fail
[  357.602697] emupia: Unknown symbol InterlockedIncrement
[  357.602724] emupia: Unknown symbol heap_alloc
[  357.602749] emupia: Unknown symbol stack_free_page
[  357.602797] emupia: Unknown symbol stack_alloc
[  357.602851] emupia: Unknown symbol get_ossrv
[  357.602875] emupia: Unknown symbol unload_all_plugins
[  357.602900] emupia: Unknown symbol stack_alloc_page
[  357.602923] emupia: Unknown symbol ioctl_dispatch
[  357.602948] emupia: Unknown symbol heap_free
[  357.602999] emupia: Unknown symbol InterlockedDecrement
[  357.603024] emupia: Unknown symbol stack_free
[  357.604947] ctsfman: Unknown symbol heap_alloc
[  357.605036] ctsfman: Unknown symbol get_ossrv
[  357.605061] ctsfman: Unknown symbol ioctl_dispatch
[  357.605085] ctsfman: Unknown symbol heap_free
[  357.609178] ct20xut: Unknown symbol InterlockedIncrement
[  357.609212] ct20xut: Unknown symbol __stack_chk_fail
[  357.609234] ct20xut: Unknown symbol heap_alloc
[  357.609262] ct20xut: Unknown symbol unregister_plugin
[  357.609296] ct20xut: Unknown symbol heap_free
[  357.609330] ct20xut: Unknown symbol register_plugin
[  357.609352] ct20xut: Unknown symbol InterlockedDecrement
[  357.618702] ctexfifx: Unknown symbol InterlockedDecrement
[  357.618736] ctexfifx: Unknown symbol register_plugin
[  357.618768] ctexfifx: Unknown symbol unregister_plugin
[  357.618795] ctexfifx: Unknown symbol __stack_chk_fail
[  357.618837] ctexfifx: Unknown symbol heap_alloc
[  357.618869] ctexfifx: Unknown symbol InterlockedIncrement
[  357.618894] ctexfifx: Unknown symbol heap_free
[  357.620830] cthwiut: Unknown symbol InterlockedIncrement
[  357.620862] cthwiut: Unknown symbol __stack_chk_fail
[  357.620885] cthwiut: Unknown symbol heap_alloc
[  357.620912] cthwiut: Unknown symbol unregister_plugin
[  357.620945] cthwiut: Unknown symbol heap_free
[  357.620978] cthwiut: Unknown symbol register_plugin
[  357.621001] cthwiut: Unknown symbol InterlockedDecrement
[  357.641705] haxfi: Unknown symbol InterlockedDecrement
[  357.641849] haxfi: Unknown symbol get_ossrv
[  357.642035] haxfi: Unknown symbol heap_alloc
[  357.642112] haxfi: Unknown symbol InterlockedIncrement
[  357.642174] haxfi: Unknown symbol heap_free
[  357.645201] ctalsa: Unknown symbol bytes_to_order
[  357.645616] ctalsa: Unknown symbol get_ossrv
[  357.645699] ctalsa: Unknown symbol __stack_chk_fail
[  357.646110] ctalsa: Unknown symbol heap_alloc
[  357.646180] ctalsa: Unknown symbol malloc_sizes
[  357.646260] ctalsa: Unknown symbol ioctl_dispatch
[  357.646365] ctalsa: Unknown symbol heap_free
[  552.344207] ctossrv: Unknown symbol __stack_chk_fail
[  552.346171] emupia: Unknown symbol InterlockedIncrement
[  552.346198] emupia: Unknown symbol heap_alloc
[  552.346223] emupia: Unknown symbol stack_free_page
[  552.346310] emupia: Unknown symbol stack_alloc
[  552.346364] emupia: Unknown symbol get_ossrv
[  552.346386] emupia: Unknown symbol unload_all_plugins
[  552.346411] emupia: Unknown symbol stack_alloc_page
[  552.346434] emupia: Unknown symbol ioctl_dispatch
[  552.346458] emupia: Unknown symbol heap_free
[  552.346508] emupia: Unknown symbol InterlockedDecrement
[  552.346532] emupia: Unknown symbol stack_free
[  552.353584] ctsfman: Unknown symbol heap_alloc
[  552.353670] ctsfman: Unknown symbol get_ossrv
[  552.353693] ctsfman: Unknown symbol ioctl_dispatch
[  552.353717] ctsfman: Unknown symbol heap_free
[  552.358630] ct20xut: Unknown symbol InterlockedIncrement
[  552.358661] ct20xut: Unknown symbol __stack_chk_fail
[  552.358683] ct20xut: Unknown symbol heap_alloc
[  552.358710] ct20xut: Unknown symbol unregister_plugin
[  552.358743] ct20xut: Unknown symbol heap_free
[  552.358776] ct20xut: Unknown symbol register_plugin
[  552.358798] ct20xut: Unknown symbol InterlockedDecrement
[  552.368098] ctexfifx: Unknown symbol InterlockedDecrement
[  552.368131] ctexfifx: Unknown symbol register_plugin
[  552.368163] ctexfifx: Unknown symbol unregister_plugin
[  552.368189] ctexfifx: Unknown symbol __stack_chk_fail
[  552.368230] ctexfifx: Unknown symbol heap_alloc
[  552.368261] ctexfifx: Unknown symbol InterlockedIncrement
[  552.368286] ctexfifx: Unknown symbol heap_free
[  552.370854] cthwiut: Unknown symbol InterlockedIncrement
[  552.370885] cthwiut: Unknown symbol __stack_chk_fail
[  552.370907] cthwiut: Unknown symbol heap_alloc
[  552.370934] cthwiut: Unknown symbol unregister_plugin
[  552.370967] cthwiut: Unknown symbol heap_free
[  552.370999] cthwiut: Unknown symbol register_plugin
[  552.371021] cthwiut: Unknown symbol InterlockedDecrement
[  552.390840] haxfi: Unknown symbol InterlockedDecrement
[  552.390988] haxfi: Unknown symbol get_ossrv
[  552.391201] haxfi: Unknown symbol heap_alloc
[  552.391278] haxfi: Unknown symbol InterlockedIncrement
[  552.391336] haxfi: Unknown symbol heap_free
[  552.394429] ctalsa: Unknown symbol bytes_to_order
[  552.394710] ctalsa: Unknown symbol get_ossrv
[  552.394836] ctalsa: Unknown symbol __stack_chk_fail
[  552.395260] ctalsa: Unknown symbol heap_alloc
[  552.395323] ctalsa: Unknown symbol malloc_sizes
[  552.395400] ctalsa: Unknown symbol ioctl_dispatch
[  552.395630] ctalsa: Unknown symbol heap_free
[  660.134993] ctossrv: Unknown symbol __stack_chk_fail
[  660.140601] emupia: Unknown symbol InterlockedIncrement
[  660.140629] emupia: Unknown symbol heap_alloc
[  660.140654] emupia: Unknown symbol stack_free_page
[  660.140701] emupia: Unknown symbol stack_alloc
[  660.140754] emupia: Unknown symbol get_ossrv
[  660.140777] emupia: Unknown symbol unload_all_plugins
[  660.140818] emupia: Unknown symbol stack_alloc_page
[  660.140841] emupia: Unknown symbol ioctl_dispatch
[  660.140864] emupia: Unknown symbol heap_free
[  660.140914] emupia: Unknown symbol InterlockedDecrement
[  660.140939] emupia: Unknown symbol stack_free
[  660.143023] ctsfman: Unknown symbol heap_alloc
[  660.143111] ctsfman: Unknown symbol get_ossrv
[  660.143135] ctsfman: Unknown symbol ioctl_dispatch
[  660.143158] ctsfman: Unknown symbol heap_free
[  660.148038] ct20xut: Unknown symbol InterlockedIncrement
[  660.148070] ct20xut: Unknown symbol __stack_chk_fail
[  660.148091] ct20xut: Unknown symbol heap_alloc
[  660.148118] ct20xut: Unknown symbol unregister_plugin
[  660.148152] ct20xut: Unknown symbol heap_free
[  660.148185] ct20xut: Unknown symbol register_plugin
[  660.148207] ct20xut: Unknown symbol InterlockedDecrement
[  660.157620] ctexfifx: Unknown symbol InterlockedDecrement
[  660.157653] ctexfifx: Unknown symbol register_plugin
[  660.157684] ctexfifx: Unknown symbol unregister_plugin
[  660.157710] ctexfifx: Unknown symbol __stack_chk_fail
[  660.157752] ctexfifx: Unknown symbol heap_alloc
[  660.157784] ctexfifx: Unknown symbol InterlockedIncrement
[  660.157808] ctexfifx: Unknown symbol heap_free
[  660.160257] cthwiut: Unknown symbol InterlockedIncrement
[  660.160287] cthwiut: Unknown symbol __stack_chk_fail
[  660.160309] cthwiut: Unknown symbol heap_alloc
[  660.160335] cthwiut: Unknown symbol unregister_plugin
[  660.160368] cthwiut: Unknown symbol heap_free
[  660.160401] cthwiut: Unknown symbol register_plugin
[  660.160422] cthwiut: Unknown symbol InterlockedDecrement
[  660.179724] haxfi: Unknown symbol InterlockedDecrement
[  660.179864] haxfi: Unknown symbol get_ossrv
[  660.180047] haxfi: Unknown symbol heap_alloc
[  660.180121] haxfi: Unknown symbol InterlockedIncrement
[  660.180177] haxfi: Unknown symbol heap_free
[  660.185060] ctalsa: Unknown symbol bytes_to_order
[  660.185343] ctalsa: Unknown symbol get_ossrv
[  660.185469] ctalsa: Unknown symbol __stack_chk_fail
[  660.186119] ctalsa: Unknown symbol heap_alloc
[  660.186181] ctalsa: Unknown symbol malloc_sizes
[  660.186259] ctalsa: Unknown symbol ioctl_dispatch
[  660.186480] ctalsa: Unknown symbol heap_free

---

### Post by xzero1 on 2007-12-18
I'll take a crack at it. SLUB and SLAB are kernel compile options. Your kernel has been compiled using the newer SLUB allocator so you must recompile your kernel using the SLAB allocator or get a xfi driver version that uses the SLUB allocator.

---

### Post by adramalech on 2007-12-18
thanks for the info.....:lolflag:

what is the difference between slub and slab and will i encounter any problems???

furthermore, what is the best repos to get 2.6.22.x kernel for amd64 in slab???

is there a slub version of the sfi driver patch etc.???

---

### Post by adramalech on 2007-12-18
okay so i figured i would try and extract some lower file that wasn't extracted before install to see if it would help anything well this is what i got from the terminal when the make install command is run....

WARNING: Error inserting ctossrv (/lib/modules/2.6.22-14-generic/kernel/drivers/ssound/ctossrv.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting emupia (/lib/modules/2.6.22-14-generic/kernel/drivers/ssound/emupia.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting ctsfman (/lib/modules/2.6.22-14-generic/kernel/drivers/ssound/ctsfman.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting ct20xut (/lib/modules/2.6.22-14-generic/kernel/drivers/ssound/ct20xut.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting ctexfifx (/lib/modules/2.6.22-14-generic/kernel/drivers/ssound/ctexfifx.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting cthwiut (/lib/modules/2.6.22-14-generic/kernel/drivers/ssound/cthwiut.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting haxfi (/lib/modules/2.6.22-14-generic/kernel/drivers/ssound/haxfi.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting ctalsa (/lib/modules/2.6.22-14-generic/kernel/drivers/ssound/ctalsa.ko): Unknown symbol in module, or unknown parameter (see dmesg)
root@adramalech:~/Desktop/XFiDrv_Linux_US-1.04/XFiDrv_Linux_US-1.04# 

the demesg is the same as in the earlier posts...:(

---

### Post by xzero1 on 2007-12-19
Slub is newer but obviously not bug free!
Ok, we are talking about recompiling the kernel, but then you can compile the latest version as well and select more optimal options for your system. There will probably be problems especially with restricted drivers so proceed at your own risk! Canonical offers support for standard Ubuntu installs but the forums should be of help. There is an excellent Ubuntu thread that discusses compiling the kernel here:
[http://ubuntuforums.org/showthread.php?t=311158&highlight=master+kernel]("http://ubuntuforums.org/showthread.php?t=311158&highlight=master+kernel")

You may also want to use "kernel check" which greatly simplifies the process, see:
[http://ubuntuforums.org/showthread.php?t=618563&highlight=master+kernel]("http://ubuntuforums.org/showthread.php?t=618563&highlight=master+kernel")

Good luck.:)

---

### Post by adramalech on 2007-12-20
okay so i just used kernel check to find the latest kernel...i really like it because i hate having to look everywhere to find the latest one....so props for the info....i would just like to know if i can use slab with the latest kernel when i build it

---

### Post by xzero1 on 2007-12-21
Yes, I use it on my notebook and it fixes a suspend problem.:)

---

### Post by adramalech on 2007-12-26
now is there a way that the xfi sound card will ever work becuase i like my kernel and dont feel that i have to reinvent the wheel to get a stupid sound card working....is there a petition to sign or somewhere to complain to creative for their horrible driver that is crap...i feel that because of their crappy driver as i try to get my sound card working i am pretty much rewriting the entire kernel then having to modify THEIR code....:mad:

---

### Post by adramalech on 2007-12-27
okay so i used kernel check to get the latest build of kernel which is i got 2.6.23.12-generic

and so when it came to the page that pops up to customize the kernel...i made sure to check the box that complied the kernel in slab instead of slub and it know gives me a message that looks like this when i go to *make install* :

Copy module files...
cp: cannot stat `ctossrv.ko': No such file or directory
cp: cannot stat `emupia.ko': No such file or directory
cp: cannot stat `ctsfman.ko': No such file or directory
cp: cannot stat `haxfi.ko': No such file or directory
cp: cannot stat `ctalsa.ko': No such file or directory
cp: cannot stat `ct20xut.ko': No such file or directory
cp: cannot stat `ctexfifx.ko': No such file or directory
cp: cannot stat `cthwiut.ko': No such file or directory
make: *** [copy_modules] Error 1
:confused:

what does this mean....

---

