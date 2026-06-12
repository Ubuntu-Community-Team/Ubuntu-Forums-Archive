---
title: "USB problems and weird output on terminal screen"
date: 2008-11-08
forum: General Help
---

### Post by jrz on 2008-11-08
I have an external drive which I have been using to back up files to, and today I tried to connect it and saw the drive icon appear and quickly disappear, and received an error message saying:
 Couldn't find /media/New Volume
 please check the spelling and try again.

I looked in the /media directory and saw nothing there that hasn't been there, and tried reconnecting the drive and this time received an error message saying:
 Couldn't find /media New Volume
 please select another viewer and try again.

On a third attempt nothing at all happened, the drive didn't mount and no error messages occurred.

I then tried connecting an empty Kingston memory stick, and nothing at all happens.

I had a terminal screen open and notice it has a great number of messages which appear to have popped up while this was going on, but I have no idea what they mean.

Message from syslogd@amd at Sun Nov  9 11:22:56 2008 ...
amd kernel: [514405.299422] SMP 

Message from syslogd@amd at Sun Nov  9 11:22:55 2008 ...
amd kernel: [514405.299420] Oops: 0000 [#1]

Message from syslogd@amd at Sun Nov  9 11:22:56 2008 ...
amd kernel: [514405.299508] EIP:    0060:[make_class_name+53/160]    Not tainted VLI

Message from syslogd@amd at Sun Nov  9 11:22:56 2008 ...
amd kernel: [514405.299510] EFLAGS: 00010202   (2.6.20-17-generic #2)

Message from syslogd@amd at Sun Nov  9 11:22:56 2008 ...
amd kernel: [514405.299528] EIP is at make_class_name+0x35/0xa0

Message from syslogd@amd at Sun Nov  9 11:22:56 2008 ...
amd kernel: [514405.299531] eax: 00000000   ebx: ffffffff   ecx: ffffffff   edx: 0000000b

Message from syslogd@amd at Sun Nov  9 11:22:56 2008 ...
amd kernel: [514405.299535] esi: de8d8c91   edi: 00000000   ebp: 00000000   esp: ddcd1e50

Message from syslogd@amd at Sun Nov  9 11:22:56 2008 ...
amd kernel: [514405.299538] ds: 007b   es: 007b   ss: 0068

Message from syslogd@amd at Sun Nov  9 11:22:56 2008 ...
amd kernel: [514405.299541] Process khubd (pid: 1942, ti=ddcd0000 task=dde17580 task.ti=ddcd0000)

Message from syslogd@amd at Sun Nov  9 11:22:56 2008 ...
amd kernel: [514405.299544] Stack: cb6b8e04 de8eaec0 cb6b8dfc cb6b8e04 de8eae40 c0258901 00000000 de8eaec8 

Message from syslogd@amd at Sun Nov  9 11:22:56 2008 ...
amd kernel: [514405.299551]        cb6b8dfc d1f8ec00 00000246 ffffffed c0258988 cb6b8c00 de8d2a50 cb6b8c00 

Message from syslogd@amd at Sun Nov  9 11:22:56 2008 ...
amd kernel: [514405.299558]        d1f8ec00 de8d012b d1f8ec30 d1f8ec00 de8ca825 d1f8eef4 cf52de18 def53f60 

Message from syslogd@amd at Sun Nov  9 11:22:56 2008 ...
amd kernel: [514405.299565] Call Trace:

Message from syslogd@amd at Sun Nov  9 11:22:56 2008 ...
amd kernel: [514405.299573]  [class_device_del+161/288] class_device_del+0xa1/0x120

Message from syslogd@amd at Sun Nov  9 11:22:56 2008 ...
amd kernel: [514405.299583]  [class_device_unregister+8/16] class_device_unregister+0x8/0x10

Message from syslogd@amd at Sun Nov  9 11:22:56 2008 ...
amd kernel: [514405.299507] CPU:    0

Message from syslogd@amd at Sun Nov  9 11:22:56 2008 ...
amd kernel: [514405.299589]  [<de8d2a50>] __scsi_remove_device+0x30/0x80 [scsi_mod]

Message from syslogd@amd at Sun Nov  9 11:22:56 2008 ...
amd kernel: [514405.299650]  [<de8d012b>] scsi_forget_host+0x4b/0x60 [scsi_mod]

Message from syslogd@amd at Sun Nov  9 11:22:56 2008 ...
amd kernel: [514405.299670]  [<de8ca825>] scsi_remove_host+0x55/0xe0 [scsi_mod]

Message from syslogd@amd at Sun Nov  9 11:22:56 2008 ...
amd kernel: [514405.299688]  [<def45cae>] storage_disconnect+0xe/0x20 [usb_storage]

Message from syslogd@amd at Sun Nov  9 11:22:56 2008 ...
amd kernel: [514405.299707]  [<de882d20>] usb_unbind_interface+0x50/0xa0 [usbcore]

Message from syslogd@amd at Sun Nov  9 11:22:56 2008 ...
amd kernel: [514405.299762]  [__device_release_driver+104/160] __device_release_driver+0x68/0xa0

Message from syslogd@amd at Sun Nov  9 11:22:56 2008 ...
amd kernel: [514405.299769]  [device_release_driver+35/64] device_release_driver+0x23/0x40

Message from syslogd@amd at Sun Nov  9 11:22:56 2008 ...
amd kernel: [514405.299775]  [bus_remove_device+92/144] bus_remove_device+0x5c/0x90

Message from syslogd@amd at Sun Nov  9 11:22:56 2008 ...
amd kernel: [514405.299781]  [device_del+338/432] device_del+0x152/0x1b0

Message from syslogd@amd at Sun Nov  9 11:22:56 2008 ...
amd kernel: [514405.299789]  [<de8801ee>] usb_disable_device+0x7e/0xe0 [usbcore]

Message from syslogd@amd at Sun Nov  9 11:22:56 2008 ...
amd kernel: [514405.299809]  [<de87c597>] usb_disconnect+0x97/0x130 [usbcore]

Message from syslogd@amd at Sun Nov  9 11:22:56 2008 ...
amd kernel: [514405.299833]  [<de87d2ff>] hub_thread+0x26f/0xc20 [usbcore]

Message from syslogd@amd at Sun Nov  9 11:22:56 2008 ...
amd kernel: [514405.299864]  [autoremove_wake_function+0/80] autoremove_wake_function+0x0/0x50

Message from syslogd@amd at Sun Nov  9 11:22:56 2008 ...
amd kernel: [514405.299879]  [<de87d090>] hub_thread+0x0/0xc20 [usbcore]

Message from syslogd@amd at Sun Nov  9 11:22:56 2008 ...
amd kernel: [514405.299894]  [kthread+186/240] kthread+0xba/0xf0

Message from syslogd@amd at Sun Nov  9 11:22:56 2008 ...
amd kernel: [514405.299900]  [kthread+0/240] kthread+0x0/0xf0

Message from syslogd@amd at Sun Nov  9 11:22:56 2008 ...
amd kernel: [514405.299906]  [kernel_thread_helper+7/16] kernel_thread_helper+0x7/0x10

Message from syslogd@amd at Sun Nov  9 11:22:56 2008 ...
amd kernel: [514405.299918]  =======================

Message from syslogd@amd at Sun Nov  9 11:22:56 2008 ...
amd kernel: [514405.299919] Code: ff ff 89 6c 24 10 31 ed 89 d9 89 74 24 08 89 c6 89 7c 24 0c 89 c7 89 e8 89 14 24 f2 ae f7 d1 49 8b 04 24 89 ca 89 d9 8b 38 89 e8 <f2> ae f7 d1 49 8d 44 0a 02 ba d0 00 00 00 e8 48 ab f1 ff ba f4 

Message from syslogd@amd at Sun Nov  9 11:22:56 2008 ...
amd kernel: [514405.299945] EIP: [make_class_name+53/160] make_class_name+0x35/0xa0 SS:ESP 0068:ddcd1e50
joe@amd:~$ 

Can anyone make sense of this?

---

