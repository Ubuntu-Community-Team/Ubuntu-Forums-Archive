---
title: "Ubuntu 8.04 hangs when transfering files to samba share"
date: 2008-08-19
forum: Hardware
---

### Post by crazy1902 on 2008-08-19
Hi guys. I am brand new to Linux. I want to create a home media file server.

I installed Ubuntu 8.04 server edition with Samba.
After a week or so of tinkering I figured out the basic commands then created ext3 filesystem on a raid5 array hosted by a 3ware 9650se raid card.

The array is slightly over 2tb but I made a gpt label on the drive with parted and created the partition no problem.

I copied a lot of files onto the array when the linux box suddenly started hanging. This is what shows on the screen and I have to unplug the power to be able to restart the computer. After restart everything seems normal but as soon as I start copying files from my windows machines to the linux share it hangs again.

Here is the screenshot. I will try to OCR this so I can paste the text.
I have no idea what is going on.
[IMG]http://img398.imageshack.us/my.php?image=linuxerrorgv2.jpg[/IMG]

---

### Post by crazy1902 on 2008-08-19
Ok here is what the screen shows once the system hangs:

[72767.880279] Call Trace:
[72767.880305] [<ffffffff80285a74>] add_to_page_cache_lru+0x24/0x40
[72767.880327] [<ffffffff80285b0e>] __grab_cache_page+0x7e/0xa0
[72767.880354] [<ffffffff881eadab>] :ext3ext3_write_beg in+0x6b/0x1c0
[72767.880379] [<ffffffff802da69e>] __getblk+0x1e/0x250
[72767.880399] [<ffffffff80286a09>] generic_file_buffered_write+0x149/0x6b0
[72767.880432] [<ffffffff881f116d>] :ext3:__ext3_journal_stop +0x2d/0x60
[72767.880455] [<ffffffff802871bf>] __generic_file_aio_write_nolock+0x24f/0x400
[72767.880481] [<ffffffff802873d4>] generic_file_aio_write+0x64/0xd0
[72767.880507] [<ffffffff881e6653>] :ext3:ext3_file_write+0x23/0xc0
[72767.880527] [<ffffffff802b4c49>] do_sync_write+0xd9/0x120
[72767.880551] [<ffffffff80254260>] autoremove_wake_function+0x0/0x30
[72767.880575] [<ffffffff802c6c74>] fcntl_setlk+0x54/0x2d0
[72767.880596] [<ffffffff802b558d>] vfs_write+0xed/0x190
[72767.889615] [<ffffffff802b5df4>] sys_pwrite64+0x84/0xa0
[72767.880637] [<ffffffff8020c37e>] system_call+0x7e/0x83
[72767.889658]
[72767.880670]
[72767.880671] Code: 42 08 48 8b 07 48 89 4c c7 10 48 83 c0 01 03 f8 0e 48 89 07
[72767.880728] RIP [<ffffffff8028f39c>] lru_cache_add+0x2c/0x50
[72767.880748] RSP <ffff81007cde7ad0>
[72767.880763] CR2: ffffffffffffff8b
[72767.881023] --- [ end trace e5367919a8d79091 ]---

---

### Post by crazy1902 on 2008-08-19
If there is a Mod please delete this thread as I have recreated it in the "server" forum.

Sorry about this

---

