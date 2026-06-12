---
title: "NVIDIA driver problem, among other things"
date: 2008-11-22
forum: Hardware
---

### Post by Venue on 2008-11-22
Hello, im new to linux so bear with me
recently, i tried installing my Creative X-Fi drivers, which i could not get to install. but after i tried installing them, i restarted my computer, and after the Ubuntu loading screen, i would get a popup saying that Ubuntu was running in low graphics mode. i would click continue, and just get a black screen. finally i was able to get in, and i saw that my graphics drivers were now set to CTALSA drivers instead of nVidia drivers. I thought that maybe my drivers got corrupted so i downloaded new drivers, started installing them (i exited X server) and i got an error during installation.

 ERROR: Unable to load the kernel module 'nvidia.ko'.  This happens most
       frequently when this kernel module was built against the wrong or
       improperly configured kernel sources, with a version of gcc that differs
       from the one used to build the target kernel, or if a driver such as
       rivafb/nvidiafb is present and prevents the NVIDIA kernel module from
       obtaining ownership of the NVIDIA graphics device(s).
       
       Please see the log entries 'Kernel module load error' and 'Kernel
       messages' at the end of the file '/var/log/nvidia-installer.log' for
       more information.
-> Kernel module load error: Segmentation fault
-> Kernel messages:
   [  513.645059] Pid: 7422, comm: insmod Tainted: PF       (2.6.24-21-generic
   #1)
   [  513.645124] EIP: 0060:[<c0215542>] EFLAGS: 00010206 CPU: 0
   [  513.645186] EIP is at kobject_get_path+0x12/0x90
   [  513.645241] EAX: 00000010 EBX: 00001003 ECX: 00000010 EDX: 000000d0
   [  513.645303] ESI: ff74d878 EDI: 00000025 EBP: 000000d0 ESP: f5c21de0
   [  513.645365]  DS: 007b ES: 007b FS: 00d8 GS: 0033 SS: 0068
   [  513.645423] Process insmod (pid: 7422, ti=f5c20000 task=f6a825c0
   task.ti=f5c20000)
   [  513.645491] Stack: ff74d878 c03fae7c ff74d878 fffffff4 00000000 c0215d80
   ff74d878 ff74d878 
   [  513.645627]        c03fae40 00000000 c01d7919 00000000 c03b6593 ff74d878
   f7c851d8 f6ab2000 
   [  513.645763]        00000007 f6e663e8 f5c21e58 c03fae8c ff74d878 00000000
   c03fae40 ff74d878 
   [  513.645899] Call Trace:
   [  513.645986]  [<c0215d80>] kobject_uevent_env+0xb0/0x3d0
   [  513.646052]  [<c01d7919>] sysfs_create_dir+0x29/0x50
   [  513.646120]  [<c02159ed>] kobject_register+0x3d/0x50
   [  513.646182]  [<c02820b1>] bus_add_driver+0x71/0x1e0
   [  513.646248]  [<c0227586>] __pci_register_driver+0x56/0x90
   [  513.646314]  [<f8acd11d>] nvidia_init_module+0x11d/0x803 [nvidia]
   [  513.646481]  [<c0150706>] sys_init_module+0x126/0x19c0
   [  513.646557]  [<c0214417>] _atomic_dec_and_lock+0x47/0x70
   [  513.646622]  [<c0253ddb>] acpi_bus_register_driver+0x0/0x38
   [  513.646693]  [<c01043b2>] sysenter_past_esp+0x6b/0xa9
   [  513.646760]  =======================
   [  513.646810] Code: b5 ff ff ff 8d 43 04 89 43 04 89 43 08 c7 43 0c 01 00
   00 00 5b c3 8d 76 00 55 89 d5 57 bf 01 00 00 00 56 89 c6 53 89 c3 83 ec 04
   <8b> 03 85 c0 74 14 e8 d3 4f 00 00 8b 5b 10 85 db 8d 7c 38 01 75 
   [  513.647237] EIP: [<c0215542>] kobject_get_path+0x12/0x90 SS:ESP
   0068:f5c21de0
   [  513.647316] ---[ end trace 805a5e38786ea50f ]---





any help would be greatly appreciated.

---

### Post by mikewhatever on 2008-11-22
You could try several possible solutions before installing and re-installing drivers, that is among other things, of cause.

1. sudo dpkg-reconfigure -phigh xserver-xorg
2. Boot into recovery mode (seconds boot option) and select to fix xserver.

If you need to install an nvidia driver, it can easily be done from cli with <sudo apt-get install nvidia-glx>. You have to know you card model though, in fact, I think the errors you got may be related to the wrong driver. If you need help on that, post your card specs among other things.

---

