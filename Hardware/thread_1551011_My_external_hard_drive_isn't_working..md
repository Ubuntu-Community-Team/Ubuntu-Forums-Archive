---
title: "My external hard drive isn't working."
date: 2010-08-11
forum: Hardware
---

### Post by distorted on 2010-08-11
Hey all,

(Ubuntu 9.10)
My external hard drive isn't working correctly. I tried a different USB port, no response. I'm a newbie in Ubuntu, so help me out, please. [http://ubuntuforums.org/showthread.php?p=9704541#post9704541](http://ubuntuforums.org/showthread.php?p=9704541#post9704541)

Device Manager
USB Device
Model: Rugged USB
Vendor: LaCie, Ltd.
Serial:
Connection: USB 
USB Version:???
Connected at: ???
Remote Wakeup: No
Bus Powered: No
Max. Power: 2 mA

(Windows XP) 
I ran my Windows XP. It was working there.
LACIE
Type: Local Disc
File System: FAT32
Device Status: The device is working properly. 


Thank you.

---

### Post by waynefoutz on 2010-08-11
put it back in the windows machine, on the little icon for devices next to the clock in the right hand corner, click, "safely remove usb external drive" 

it should work fine from then on.

either that or use this guide to force mount it.

[https://help.ubuntu.com/community/Mount/USB]("https://help.ubuntu.com/community/Mount/USB")

When you pull the plug on them on a windows machine, a lot of times this will be the result for some reason. Maybe one of the smarter geeks can explain why. But from now on, when using it in windows, remove it this way to avoid the problem. I also right click and unmount them before I yank them out when running Linux.

---

### Post by distorted on 2010-08-11
I always check on 'Safely Remove Hardware.' It's not that.

```
 
$sudo fdisk -l
[sudo] password for dis: 

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00064a14

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      120376   966920188+  83  Linux
/dev/sda2          120377      121601     9839812+   5  Extended
/dev/sda5          120377      121601     9839781   82  Linux swap / Solaris
$ sudo mkdir /media/external
$ sudo mount -t vfat /dev/sdb1 /media/external -o uid=1000,gid=100,utf8,dmask=027,fmask=137
mount: special device /dev/sdb1 does not exist
sudo blkid
/dev/sda1: UUID="ef7b1d0a-ac7a-4414-a2da-d38deaa31205" TYPE="ext3" 
/dev/sda5: UUID="0dee2f3a-0e81-49ce-88dd-a3d66832c490" TYPE="swap" 


```

I don't know what's the deal now? I'm lost.

---

### Post by IcarusR on 2010-08-12
You can only mount drives that ubuntu sees & there is no /dev/sdb1 is not listed in your fdisk output.
Ubuntu does not see your external drive for some reason.

Try unplugging it, then reconnect it & in a terminal type 

```
dmesg
```

& see if it says any thing about the drive or usb at the end.

---

### Post by distorted on 2010-08-13
Ahh...I see. Thanks for your help. Lots of errors. I thnk it's some of my .mp3 files. How to fix or delete them without wiping my external hard drive clean?

```

[   80.976428] FAT: Filesystem error (dev sdb5)
[   80.976432]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   80.976436]     File system has been set read-only
[   80.976617] FAT: Filesystem error (dev sdb5)
[   80.976619]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   80.976709] FAT: Filesystem error (dev sdb5)
[   80.976710]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   80.976793] FAT: Filesystem error (dev sdb5)
[   80.976795]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   80.976878] FAT: Filesystem error (dev sdb5)
[   80.976880]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   80.976962] FAT: Filesystem error (dev sdb5)
[   80.976964]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   80.977046] FAT: Filesystem error (dev sdb5)
[   80.977047]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   80.977130] FAT: Filesystem error (dev sdb5)
[   80.977132]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   80.977215] FAT: Filesystem error (dev sdb5)
[   80.977216]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   80.977297] FAT: Filesystem error (dev sdb5)
[   80.977298]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   80.977376] FAT: Filesystem error (dev sdb5)
[   80.977377]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   80.977448] FAT: Filesystem error (dev sdb5)
[   80.977449]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   80.977519] FAT: Filesystem error (dev sdb5)
[   80.977520]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   80.977590] FAT: Filesystem error (dev sdb5)
[   80.977591]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   80.977661] FAT: Filesystem error (dev sdb5)
[   80.977662]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   80.977739] FAT: Filesystem error (dev sdb5)
[   80.977741]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   80.977823] FAT: Filesystem error (dev sdb5)
[   80.977825]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   80.977907] FAT: Filesystem error (dev sdb5)
[   80.977909]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   80.979111] FAT: Filesystem error (dev sdb5)
[   80.979114]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   80.979242] FAT: Filesystem error (dev sdb5)
[   80.979245]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   80.979342] FAT: Filesystem error (dev sdb5)
[   80.979344]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   80.979428] FAT: Filesystem error (dev sdb5)
[   80.979430]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   80.979519] FAT: Filesystem error (dev sdb5)
[   80.979521]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   80.979605] FAT: Filesystem error (dev sdb5)
[   80.979607]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   80.979689] FAT: Filesystem error (dev sdb5)
[   80.979691]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   80.979773] FAT: Filesystem error (dev sdb5)
[   80.979775]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   80.979858] FAT: Filesystem error (dev sdb5)
[   80.979859]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   80.979938] FAT: Filesystem error (dev sdb5)
[   80.979939]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   80.980021] FAT: Filesystem error (dev sdb5)
[   80.980023]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   80.980094] FAT: Filesystem error (dev sdb5)
[   80.980096]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   80.980166] FAT: Filesystem error (dev sdb5)
[   80.980167]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   80.980237] FAT: Filesystem error (dev sdb5)
[   80.980238]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   80.980310] FAT: Filesystem error (dev sdb5)
[   80.980311]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   80.980389] FAT: Filesystem error (dev sdb5)
[   80.980391]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   80.980491] FAT: Filesystem error (dev sdb5)
[   80.980493]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   80.980579] FAT: Filesystem error (dev sdb5)
[   80.980581]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   80.983389] FAT: Filesystem error (dev sdb5)
[   80.983391]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   80.983407] FAT: Filesystem error (dev sdb5)
[   80.983409]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  772.948446] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  772.948450] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[  772.948723] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  783.919435] eth0: no IPv6 routers present


```

Also, my external hard drive isn't working with Deja Dup Backup Tool:
```
BackendException: Error stating file '/media/LACIE/FOUND.001': Input/output error
```
You think it's smart for me to get another internal hard drive?

---

### Post by distorted on 2010-08-14
::bump::

---

### Post by aysiu on 2010-08-14
Maybe this might help:
[http://www.delodder.be/blog/linux/fat_get_cluster-invalid-cluster-chain-i_pos-0-fat-filesystem-panic-dev/](http://www.delodder.be/blog/linux/fat_get_cluster-invalid-cluster-chain-i_pos-0-fat-filesystem-panic-dev/)

---

### Post by distorted on 2010-08-17
:pI tried that, it's not that.  I think it's more python and my video card, nvidia. [http://www.sucka.net/2010/03/nvidia-drivers-ubuntu-10-04-lucid-lynx/](http://www.sucka.net/2010/03/nvidia-drivers-ubuntu-10-04-lucid-lynx/)
```
[COLOR=#c20cb9][B]
sudo[/B][/COLOR] [COLOR=#c20cb9]**nano**[/COLOR] [COLOR=#000000]**/**[/COLOR]etc[COLOR=#000000]**/**[/COLOR]default[COLOR=#000000]**/**[/COLOR]grub 

```*On line #18, uncomment (uncomment = remove the “#” in front of the line “[I]#GRUB_GFXMODE=640×480*” and change the resolution to whatever you want. Here is how it should look:[/I] GRUB_GFXMODE=1024x768

My file is new, no code on my file. What's wrong with my file?

Resolved.:razz:

---

### Post by efflandt on 2010-08-18
Did you format it or use it "as is"?  If Linux finds sdb5, that is a logical partition which should be contained within an extended partition (or is it part of a Windows logical disk volume?).  Or did the drive come with some software that automatically encrypts the data (since FAT32 has no concept of file permissions)?  Apparently Linux is having trouble deciphering it.

Normally an external USB drive would come with just a single primary partition, which in this case would likely be /dev/sdb1.  Although, USB flash sticks with U3 also have a pseudo cdrom device with Windows software that shows up as an sr device.

What shows up in dmesg about that USB device before stumbling on sdb5?

---

### Post by IcarusR on 2010-08-18
Try either running chkdsk from windows or fsck from ubuntu on the drive.

---

### Post by distorted on 2010-08-19
I got to show you. dmesg
```

[    4.733578] Call Trace:
[    4.733587]  [<c01cd1f4>] oom_kill_process+0xa4/0x2b0
[    4.733591]  [<c01cd869>] ? select_bad_process+0xa9/0xe0
[    4.733595]  [<c01cd8f1>] __out_of_memory+0x51/0xa0
[    4.733598]  [<c01cd998>] out_of_memory+0x58/0xb0
[    4.733602]  [<c01d01a7>] __alloc_pages_slowpath+0x407/0x4a0
[    4.733607]  [<c01d037a>] __alloc_pages_nodemask+0x13a/0x170
[    4.733611]  [<c01d03cc>] __get_free_pages+0x1c/0x30
[    4.733615]  [<c01adf5a>] ring_buffer_resize+0x18a/0x2a0
[    4.733619]  [<c01af535>] tracing_resize_ring_buffer+0x25/0x80
[    4.733624]  [<c01b3292>] tracing_entries_write+0xe2/0x160
[    4.733628]  [<c01b2aa7>] ? trace_nowake_buffer_unlock_commit+0x37/0x50
[    4.733634]  [<c02f56c4>] ? security_file_permission+0x14/0x20
[    4.733639]  [<c0208444>] ? rw_verify_area+0x64/0xe0
[    4.733644]  [<c058cf97>] ? unlock_kernel+0x27/0x30
[    4.733647]  [<c0208562>] vfs_write+0xa2/0x1a0
[    4.733654]  [<c0354439>] ? copy_to_user+0x39/0x130
[    4.733656]  [<c01b31b0>] ? tracing_entries_write+0x0/0x160
[    4.733658]  [<c0208e82>] sys_write+0x42/0x70
[    4.733661]  [<c01033ec>] syscall_call+0x7/0xb
[    4.733662] Mem-Info:
[    4.733663] DMA per-cpu:
[    4.733665] CPU    0: hi:    0, btch:   1 usd:   0
[    4.733666] CPU    1: hi:    0, btch:   1 usd:   0
[    4.733667] CPU    2: hi:    0, btch:   1 usd:   0
[    4.733668] CPU    3: hi:    0, btch:   1 usd:   0
[    4.733669] CPU    4: hi:    0, btch:   1 usd:   0
[    4.733670] CPU    5: hi:    0, btch:   1 usd:   0
[    4.733671] CPU    6: hi:    0, btch:   1 usd:   0
[    4.733672] CPU    7: hi:    0, btch:   1 usd:   0
[    4.733673] Normal per-cpu:
[    4.733674] CPU    0: hi:  186, btch:  31 usd: 180
[    4.733676] CPU    1: hi:  186, btch:  31 usd: 152
[    4.733677] CPU    2: hi:  186, btch:  31 usd:  72
[    4.733678] CPU    3: hi:  186, btch:  31 usd:  83
[    4.733679] CPU    4: hi:  186, btch:  31 usd:  90
[    4.733680] CPU    5: hi:  186, btch:  31 usd:  59
[    4.733681] CPU    6: hi:  186, btch:  31 usd: 126
[    4.733682] CPU    7: hi:  186, btch:  31 usd:  73
[    4.733683] HighMem per-cpu:
[    4.733684] CPU    0: hi:  186, btch:  31 usd: 180
[    4.733685] CPU    1: hi:  186, btch:  31 usd:  20
[    4.733686] CPU    2: hi:  186, btch:  31 usd: 182
[    4.733687] CPU    3: hi:  186, btch:  31 usd: 181
[    4.733688] CPU    4: hi:  186, btch:  31 usd: 133
[    4.733690] CPU    5: hi:  186, btch:  31 usd: 164
[    4.733691] CPU    6: hi:  186, btch:  31 usd: 162
[    4.733692] CPU    7: hi:  186, btch:  31 usd:  82
[    4.733694] active_anon:109 inactive_anon:64 isolated_anon:0
[    4.733695]  active_file:188 inactive_file:667 isolated_file:0
[    4.733696]  unevictable:0 dirty:0 writeback:0 unstable:0
[    4.733696]  free:621330 slab_reclaimable:374 slab_unreclaimable:4597
[    4.733697]  mapped:281 shmem:40 pagetables:26 bounce:0
[    4.733701] DMA free:3520kB min:64kB low:80kB high:96kB active_anon:0kB inactive_anon:0kB active_file:0kB inactive_file:0kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:15848kB mlocked:0kB dirty:0kB writeback:0kB mapped:0kB shmem:0kB slab_reclaimable:0kB slab_unreclaimable:92kB kernel_stack:0kB pagetables:0kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? yes
[    4.733708] lowmem_reserve[]: 0 865 3275 3275
[    4.733713] Normal free:3536kB min:3728kB low:4660kB high:5592kB active_anon:0kB inactive_anon:0kB active_file:76kB inactive_file:152kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:885944kB mlocked:0kB dirty:0kB writeback:0kB mapped:4kB shmem:0kB slab_reclaimable:1496kB slab_unreclaimable:18296kB kernel_stack:1160kB pagetables:0kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:226 all_unreclaimable? no
[    4.733717] lowmem_reserve[]: 0 0 19281 19281
[    4.733724] HighMem free:2478264kB min:512kB low:3108kB high:5704kB active_anon:436kB inactive_anon:256kB active_file:676kB inactive_file:2516kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:2468000kB mlocked:0kB dirty:0kB writeback:0kB mapped:1120kB shmem:160kB slab_reclaimable:0kB slab_unreclaimable:0kB kernel_stack:0kB pagetables:104kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:64 all_unreclaimable? no
[    4.733727] lowmem_reserve[]: 0 0 0 0
[    4.733730] DMA: 4*4kB 2*8kB 4*16kB 3*32kB 2*64kB 1*128kB 2*256kB 1*512kB 2*1024kB 0*2048kB 0*4096kB = 3520kB
[    4.733735] Normal: 0*4kB 0*8kB 0*16kB 1*32kB 1*64kB 1*128kB 1*256kB 0*512kB 1*1024kB 1*2048kB 0*4096kB = 3552kB
[    4.733741] HighMem: 108*4kB 49*8kB 26*16kB 15*32kB 10*64kB 5*128kB 3*256kB 3*512kB 3*1024kB 4*2048kB 601*4096kB = 2478264kB
[    4.733747] 911 total pagecache pages
[    4.733748] 0 pages in swap cache
[    4.733749] Swap cache stats: add 0, delete 0, find 0/0
[    4.733750] Free swap  = 0kB
[    4.733751] Total swap = 0kB
[    4.738030] 849920 pages RAM
[    4.738031] 622594 pages HighMem
[    4.738032] 13808 pages reserved
[    4.738033] 688 pages shared
[    4.738034] 212282 pages non-shared
[    4.738036] Out of memory: kill process 405 (plymouthd) score 38 or a child
[    4.738037] Killed process 405 (plymouthd)
[    4.741796] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0090270002400de9]
[    4.741834] ureadahead invoked oom-killer: gfp_mask=0xd0, order=0, oom_adj=0
[    4.741837] ureadahead cpuset=/ mems_allowed=0
[    4.741840] Pid: 404, comm: ureadahead Not tainted 2.6.32-24-generic #39-Ubuntu
[    4.741842] Call Trace:
[    4.741847]  [<c01cd1f4>] oom_kill_process+0xa4/0x2b0
[    4.741850]  [<c01cd869>] ? select_bad_process+0xa9/0xe0
[    4.741852]  [<c01cd8f1>] __out_of_memory+0x51/0xa0
[    4.741854]  [<c01cd998>] out_of_memory+0x58/0xb0
[    4.741856]  [<c01d01a7>] __alloc_pages_slowpath+0x407/0x4a0
[    4.741859]  [<c01d037a>] __alloc_pages_nodemask+0x13a/0x170
[    4.741861]  [<c01d03cc>] __get_free_pages+0x1c/0x30
[    4.741864]  [<c01adf5a>] ring_buffer_resize+0x18a/0x2a0
[    4.741866]  [<c01af535>] tracing_resize_ring_buffer+0x25/0x80
[    4.741869]  [<c01b3292>] tracing_entries_write+0xe2/0x160
[    4.741872]  [<c01b2aa7>] ? trace_nowake_buffer_unlock_commit+0x37/0x50
[    4.741875]  [<c02f56c4>] ? security_file_permission+0x14/0x20
[    4.741879]  [<c0208444>] ? rw_verify_area+0x64/0xe0
[    4.741882]  [<c058cf97>] ? unlock_kernel+0x27/0x30
[    4.741884]  [<c0208562>] vfs_write+0xa2/0x1a0
[    4.741886]  [<c0354439>] ? copy_to_user+0x39/0x130
[    4.741889]  [<c01b31b0>] ? tracing_entries_write+0x0/0x160
[    4.741891]  [<c0208e82>] sys_write+0x42/0x70
[    4.741893]  [<c01033ec>] syscall_call+0x7/0xb
[    4.741895] Mem-Info:
[    4.741896] DMA per-cpu:
[    4.741897] CPU    0: hi:    0, btch:   1 usd:   0
[    4.741898] CPU    1: hi:    0, btch:   1 usd:   0
[    4.741899] CPU    2: hi:    0, btch:   1 usd:   0
[    4.741901] CPU    3: hi:    0, btch:   1 usd:   0
[    4.741902] CPU    4: hi:    0, btch:   1 usd:   0
[    4.741903] CPU    5: hi:    0, btch:   1 usd:   0
[    4.741904] CPU    6: hi:    0, btch:   1 usd:   0
[    4.741905] CPU    7: hi:    0, btch:   1 usd:   0
[    4.741906] Normal per-cpu:
[    4.741907] CPU    0: hi:  186, btch:  31 usd: 180
[    4.741909] CPU    1: hi:  186, btch:  31 usd: 152
[    4.741910] CPU    2: hi:  186, btch:  31 usd:  72
[    4.741911] CPU    3: hi:  186, btch:  31 usd:  83
[    4.741912] CPU    4: hi:  186, btch:  31 usd:  91
[    4.741913] CPU    5: hi:  186, btch:  31 usd:  59
[    4.741914] CPU    6: hi:  186, btch:  31 usd: 126
[    4.741916] CPU    7: hi:  186, btch:  31 usd:  73
[    4.741916] HighMem per-cpu:
[    4.741918] CPU    0: hi:  186, btch:  31 usd: 180
[    4.741919] CPU    1: hi:  186, btch:  31 usd:  20
[    4.741920] CPU    2: hi:  186, btch:  31 usd: 182
[    4.741921] CPU    3: hi:  186, btch:  31 usd: 181
[    4.741922] CPU    4: hi:  186, btch:  31 usd: 155
[    4.741923] CPU    5: hi:  186, btch:  31 usd: 164
[    4.741924] CPU    6: hi:  186, btch:  31 usd: 162
[    4.741926] CPU    7: hi:  186, btch:  31 usd:  82
[    4.741928] active_anon:81 inactive_anon:64 isolated_anon:0
[    4.741929]  active_file:231 inactive_file:672 isolated_file:0
[    4.741930]  unevictable:0 dirty:0 writeback:0 unstable:0
[    4.741930]  free:621361 slab_reclaimable:375 slab_unreclaimable:4605
[    4.741931]  mapped:262 shmem:40 pagetables:14 bounce:0
[    4.741935] DMA free:3520kB min:64kB low:80kB high:96kB active_anon:0kB inactive_anon:0kB active_file:0kB inactive_file:0kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:15848kB mlocked:0kB dirty:0kB writeback:0kB mapped:0kB shmem:0kB slab_reclaimable:0kB slab_unreclaimable:92kB kernel_stack:0kB pagetables:0kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? yes
[    4.741938] lowmem_reserve[]: 0 865 3275 3275
[    4.741943] Normal free:3536kB min:3728kB low:4660kB high:5592kB active_anon:0kB inactive_anon:0kB active_file:108kB inactive_file:192kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:885944kB mlocked:0kB dirty:0kB writeback:0kB mapped:4kB shmem:0kB slab_reclaimable:1500kB slab_unreclaimable:18328kB kernel_stack:1152kB pagetables:0kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:228 all_unreclaimable? no
[    4.741946] lowmem_reserve[]: 0 0 19281 19281
[    4.741951] HighMem free:2478388kB min:512kB low:3108kB high:5704kB active_anon:324kB inactive_anon:256kB active_file:816kB inactive_file:2496kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:2468000kB mlocked:0kB dirty:0kB writeback:0kB mapped:1044kB shmem:160kB slab_reclaimable:0kB slab_unreclaimable:0kB kernel_stack:0kB pagetables:56kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? no
[    4.741955] lowmem_reserve[]: 0 0 0 0
[    4.741957] DMA: 4*4kB 2*8kB 4*16kB 3*32kB 2*64kB 1*128kB 2*256kB 1*512kB 2*1024kB 0*2048kB 0*4096kB = 3520kB
[    4.741963] Normal: 0*4kB 0*8kB 0*16kB 1*32kB 1*64kB 1*128kB 1*256kB 0*512kB 1*1024kB 1*2048kB 0*4096kB = 3552kB
[    4.741968] HighMem: 125*4kB 48*8kB 28*16kB 16*32kB 10*64kB 5*128kB 3*256kB 3*512kB 3*1024kB 4*2048kB 601*4096kB = 2478388kB
[    4.741974] 959 total pagecache pages
[    4.741975] 0 pages in swap cache
[    4.741976] Swap cache stats: add 0, delete 0, find 0/0
[    4.741977] Free swap  = 0kB
[    4.741978] Total swap = 0kB
[    4.746170] 849920 pages RAM
[    4.746171] 622594 pages HighMem
[    4.746172] 13808 pages reserved
[    4.746173] 525 pages shared
[    4.746174] 212289 pages non-shared
[    4.746176] Out of memory: kill process 404 (ureadahead) score 36 or a child
[    4.746177] Killed process 404 (ureadahead)
[    4.746959] ureadahead: page allocation failure. order:0, mode:0xd0
[    4.746961] Pid: 404, comm: ureadahead Not tainted 2.6.32-24-generic #39-Ubuntu
[    4.746962] Call Trace:
[    4.746966]  [<c058a676>] ? printk+0x1d/0x1f
[    4.746969]  [<c01d020e>] __alloc_pages_slowpath+0x46e/0x4a0
[    4.746971]  [<c01d037a>] __alloc_pages_nodemask+0x13a/0x170
[    4.746975]  [<c01fc0b2>] new_slab+0x1a2/0x200
[    4.746977]  [<c01fd78d>] __slab_alloc+0xbd/0x220
[    4.746979]  [<c01fe0e8>] __kmalloc+0xd8/0x190
[    4.746981]  [<c01adf33>] ? ring_buffer_resize+0x163/0x2a0
[    4.746983]  [<c01adf33>] ? ring_buffer_resize+0x163/0x2a0
[    4.746985]  [<c01adf33>] ring_buffer_resize+0x163/0x2a0
[    4.746988]  [<c01af535>] tracing_resize_ring_buffer+0x25/0x80
[    4.746990]  [<c01b3292>] tracing_entries_write+0xe2/0x160
[    4.746993]  [<c01b2aa7>] ? trace_nowake_buffer_unlock_commit+0x37/0x50
[    4.746996]  [<c02f56c4>] ? security_file_permission+0x14/0x20
[    4.746999]  [<c0208444>] ? rw_verify_area+0x64/0xe0
[    4.747002]  [<c058cf97>] ? unlock_kernel+0x27/0x30
[    4.747004]  [<c0208562>] vfs_write+0xa2/0x1a0
[    4.747006]  [<c0354439>] ? copy_to_user+0x39/0x130
[    4.747008]  [<c01b31b0>] ? tracing_entries_write+0x0/0x160
[    4.747010]  [<c0208e82>] sys_write+0x42/0x70
[    4.747013]  [<c01033ec>] syscall_call+0x7/0xb
[    4.747014] Mem-Info:
[    4.747015] DMA per-cpu:
[    4.747016] CPU    0: hi:    0, btch:   1 usd:   0
[    4.747017] CPU    1: hi:    0, btch:   1 usd:   0
[    4.747018] CPU    2: hi:    0, btch:   1 usd:   0
[    4.747019] CPU    3: hi:    0, btch:   1 usd:   0
[    4.747020] CPU    4: hi:    0, btch:   1 usd:   0
[    4.747022] CPU    5: hi:    0, btch:   1 usd:   0
[    4.747023] CPU    6: hi:    0, btch:   1 usd:   0
[    4.747024] CPU    7: hi:    0, btch:   1 usd:   0
[    4.747025] Normal per-cpu:
[    4.747026] CPU    0: hi:  186, btch:  31 usd: 180
[    4.747027] CPU    1: hi:  186, btch:  31 usd: 122
[    4.747028] CPU    2: hi:  186, btch:  31 usd:  72
[    4.747029] CPU    3: hi:  186, btch:  31 usd:  83
[    4.747030] CPU    4: hi:  186, btch:  31 usd:  91
[    4.747031] CPU    5: hi:  186, btch:  31 usd:  59
[    4.747032] CPU    6: hi:  186, btch:  31 usd: 126
[    4.747033] CPU    7: hi:  186, btch:  31 usd:  73
[    4.747034] HighMem per-cpu:
[    4.747035] CPU    0: hi:  186, btch:  31 usd: 180
[    4.747036] CPU    1: hi:  186, btch:  31 usd:  20
[    4.747038] CPU    2: hi:  186, btch:  31 usd: 182
[    4.747039] CPU    3: hi:  186, btch:  31 usd: 181
[    4.747040] CPU    4: hi:  186, btch:  31 usd: 155
[    4.747041] CPU    5: hi:  186, btch:  31 usd: 164
[    4.747042] CPU    6: hi:  186, btch:  31 usd: 162
[    4.747043] CPU    7: hi:  186, btch:  31 usd:  82
[    4.747046] active_anon:81 inactive_anon:64 isolated_anon:0
[    4.747046]  active_file:231 inactive_file:672 isolated_file:0
[    4.747047]  unevictable:0 dirty:0 writeback:0 unstable:0
[    4.747047]  free:619620 slab_reclaimable:375 slab_unreclaimable:4614
[    4.747048]  mapped:262 shmem:40 pagetables:14 bounce:0
[    4.747052] DMA free:28kB min:64kB low:80kB high:96kB active_anon:0kB inactive_anon:0kB active_file:0kB inactive_file:0kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:15848kB mlocked:0kB dirty:0kB writeback:0kB mapped:0kB shmem:0kB slab_reclaimable:0kB slab_unreclaimable:128kB kernel_stack:0kB pagetables:0kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? yes
[    4.747055] lowmem_reserve[]: 0 865 3275 3275
[    4.747059] Normal free:64kB min:3728kB low:4660kB high:5592kB active_anon:0kB inactive_anon:0kB active_file:108kB inactive_file:192kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:885944kB mlocked:0kB dirty:0kB writeback:0kB mapped:4kB shmem:0kB slab_reclaimable:1500kB slab_unreclaimable:18328kB kernel_stack:1152kB pagetables:0kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:228 all_unreclaimable? no
[    4.747063] lowmem_reserve[]: 0 0 19281 19281
[    4.747067] HighMem free:2478388kB min:512kB low:3108kB high:5704kB active_anon:324kB inactive_anon:256kB active_file:816kB inactive_file:2496kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:2468000kB mlocked:0kB dirty:0kB writeback:0kB mapped:1044kB shmem:160kB slab_reclaimable:0kB slab_unreclaimable:0kB kernel_stack:0kB pagetables:56kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? no
[    4.747070] lowmem_reserve[]: 0 0 0 0
[    4.747072] DMA: 0*4kB 0*8kB 0*16kB 0*32kB 0*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 0kB
[    4.747078] Normal: 0*4kB 0*8kB 0*16kB 0*32kB 0*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 0kB
[    4.747083] HighMem: 125*4kB 48*8kB 28*16kB 16*32kB 10*64kB 5*128kB 3*256kB 3*512kB 3*1024kB 4*2048kB 601*4096kB = 2478388kB
[    4.747089] 959 total pagecache pages
[    4.747090] 0 pages in swap cache
[    4.747091] Swap cache stats: add 0, delete 0, find 0/0
[    4.747092] Free swap  = 0kB
[    4.747093] Total swap = 0kB
[    4.751264] 849920 pages RAM
[    4.751266] 622594 pages HighMem
[    4.751267] 13808 pages reserved
[    4.751268] 525 pages shared
[    4.751268] 214087 pages non-shared
[    4.751271] SLUB: Unable to allocate memory on node -1 (gfp=0xd0)
[    4.751272]   cache: kmalloc-64, object size: 64, buffer size: 64, default order: 0, min order: 0
[    4.751274]   node 0: slabs: 3263, objs: 208832, free: 0
[    8.077725] usb-storage: device scan complete
[    8.078447] scsi 6:0:0:0: Direct-Access     WDC WD12 00BEVS-60UST0         PQ: 0 ANSI: 2 CCS
[    8.079236] sd 6:0:0:0: Attached scsi generic sg3 type 0
[    8.079926] sd 6:0:0:0: [sdb] 234441648 512-byte logical blocks: (120 GB/111 GiB)
[    8.080422] sd 6:0:0:0: [sdb] Write Protect is off
[    8.080425] sd 6:0:0:0: [sdb] Mode Sense: 00 38 00 00
[    8.080427] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    8.081546] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    8.081551]  sdb: sdb1 < sdb5 >
[    8.084153] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    8.084157] sd 6:0:0:0: [sdb] Attached SCSI disk
[    9.181752] Adding 9839772k swap on /dev/sda5.  Priority:-1 extents:1 across:9839772k 
[    9.299561] EXT3 FS on sda1, internal journal
[    9.328335] udev: starting version 151
[    9.991664] type=1505 audit(1282197390.727:2):  operation="profile_load" pid=650 name="/sbin/dhclient3"
[    9.992034] type=1505 audit(1282197390.727:3):  operation="profile_load" pid=650 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[    9.992235] type=1505 audit(1282197390.727:4):  operation="profile_load" pid=650 name="/usr/lib/connman/scripts/dhclient-script"
[   10.941720] lp: driver loaded but no devices found
[   10.997716] vga16fb: initializing
[   10.997719] vga16fb: mapped to 0xc00a0000
[   10.997758] fb0: VGA16 VGA frame buffer device
[   11.005209] Linux agpgart interface v0.103
[   11.422752] nvidia: module license 'NVIDIA' taints kernel.
[   11.422754] Disabling lock debugging due to kernel taint
[   12.228146] nvidia 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.228152] nvidia 0000:02:00.0: setting latency timer to 64
[   12.228155] vgaarb: device changed decodes: PCI:0000:02:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   12.228246] NVRM: loading NVIDIA UNIX x86 Kernel Module  195.36.24  Thu Apr 22 09:18:20 PDT 2010
[   12.259378] Console: switching to colour frame buffer device 80x30
[   13.088448]   alloc irq_desc for 22 on node -1
[   13.088450]   alloc kstat_irqs on node -1
[   13.088455] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   13.088474] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   13.272019] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input5
[   13.948394] ip_tables: (C) 2000-2006 Netfilter Core Team
[   14.468551] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   14.468665] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[   14.468667] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
[   14.468669] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   15.275750] e1000e 0000:00:19.0: irq 30 for MSI/MSI-X
[   15.331222] e1000e 0000:00:19.0: irq 30 for MSI/MSI-X
[   15.331410] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.626677] type=1505 audit(1282197397.379:5):  operation="profile_load" pid=1072 name="/usr/share/gdm/guest-session/Xsession"
[   16.627758] type=1505 audit(1282197397.379:6):  operation="profile_replace" pid=1073 name="/sbin/dhclient3"
[   16.628144] type=1505 audit(1282197397.379:7):  operation="profile_replace" pid=1073 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   16.628362] type=1505 audit(1282197397.379:8):  operation="profile_replace" pid=1073 name="/usr/lib/connman/scripts/dhclient-script"
[   16.757429] type=1505 audit(1282197397.510:9):  operation="profile_load" pid=1074 name="/usr/bin/evince"
[   16.762159] type=1505 audit(1282197397.515:10):  operation="profile_load" pid=1074 name="/usr/bin/evince-previewer"
[   16.765116] type=1505 audit(1282197397.519:11):  operation="profile_load" pid=1074 name="/usr/bin/evince-thumbnailer"
[   16.907937] type=1505 audit(1282197397.662:12):  operation="profile_load" pid=1075 name="/usr/lib/firefox-3.6.8/firefox-*bin"
[   16.909814] type=1505 audit(1282197397.662:13):  operation="profile_load" pid=1075 name="/usr/lib/firefox-3.6.8/firefox-*bin//firefox_java"
[   16.910913] type=1505 audit(1282197397.662:14):  operation="profile_load" pid=1075 name="/usr/lib/firefox-3.6.8/firefox-*bin//firefox_openjdk"
[   16.932239] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[   16.932241] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[   16.932396] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   18.096110] ioremap reserve_memtype failed -22
[   19.929975] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   19.929977] apm: disabled - APM is not SMP safe.
[   22.712346] ppdev: user-space parallel port driver
[   27.062186] eth0: no IPv6 routers present
[   32.431120] CPU0 attaching NULL sched-domain.
[   32.431124] CPU1 attaching NULL sched-domain.
[   32.431125] CPU2 attaching NULL sched-domain.
[   32.431126] CPU3 attaching NULL sched-domain.
[   32.431128] CPU4 attaching NULL sched-domain.
[   32.431129] CPU5 attaching NULL sched-domain.
[   32.431130] CPU6 attaching NULL sched-domain.
[   32.431131] CPU7 attaching NULL sched-domain.
[   32.497679] CPU0 attaching sched-domain:
[   32.497683]  domain 0: span 0,4 level SIBLING
[   32.497686]   groups: 0 (cpu_power = 589) 4 (cpu_power = 589)
[   32.497692]   domain 1: span 0-7 level MC
[   32.497697]    groups: 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178)
[   32.497703] CPU1 attaching sched-domain:
[   32.497704]  domain 0: span 1,5 level SIBLING
[   32.497705]   groups: 1 (cpu_power = 589) 5 (cpu_power = 589)
[   32.497708]   domain 1: span 0-7 level MC
[   32.497710]    groups: 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178)
[   32.497715] CPU2 attaching sched-domain:
[   32.497716]  domain 0: span 2,6 level SIBLING
[   32.497717]   groups: 2 (cpu_power = 589) 6 (cpu_power = 589)
[   32.497720]   domain 1: span 0-7 level MC
[   32.497722]    groups: 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178)
[   32.497727] CPU3 attaching sched-domain:
[   32.497728]  domain 0: span 3,7 level SIBLING
[   32.497729]   groups: 3 (cpu_power = 589) 7 (cpu_power = 589)
[   32.497732]   domain 1: span 0-7 level MC
[   32.497733]    groups: 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178)
[   32.497739] CPU4 attaching sched-domain:
[   32.497740]  domain 0: span 0,4 level SIBLING
[   32.497741]   groups: 4 (cpu_power = 589) 0 (cpu_power = 589)
[   32.497744]   domain 1: span 0-7 level MC
[   32.497745]    groups: 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178)
[   32.497751] CPU5 attaching sched-domain:
[   32.497752]  domain 0: span 1,5 level SIBLING
[   32.497753]   groups: 5 (cpu_power = 589) 1 (cpu_power = 589)
[   32.497756]   domain 1: span 0-7 level MC
[   32.497757]    groups: 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178)
[   32.497763] CPU6 attaching sched-domain:
[   32.497764]  domain 0: span 2,6 level SIBLING
[   32.497765]   groups: 6 (cpu_power = 589) 2 (cpu_power = 589)
[   32.497768]   domain 1: span 0-7 level MC
[   32.497769]    groups: 2,6 (cpu_power = 1178) 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178)
[   32.497774] CPU7 attaching sched-domain:
[   32.497776]  domain 0: span 3,7 level SIBLING
[   32.497777]   groups: 7 (cpu_power = 589) 3 (cpu_power = 589)
[   32.497780]   domain 1: span 0-7 level MC
[   32.497781]    groups: 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178) 1,5 (cpu_power = 1178) 2,6 (cpu_power = 1178)
[   59.937874] FAT: Filesystem error (dev sdb5)
[   59.937877]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   59.937879]     File system has been set read-only
[   59.938026] FAT: Filesystem error (dev sdb5)
[   59.938028]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   59.938115] FAT: Filesystem error (dev sdb5)
[   59.938116]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   59.938198] FAT: Filesystem error (dev sdb5)
[   59.938200]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   59.938283] FAT: Filesystem error (dev sdb5)
[   59.938284]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   59.938366] FAT: Filesystem error (dev sdb5)
[   59.938368]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   59.938450] FAT: Filesystem error (dev sdb5)
[   59.938451]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   59.938533] FAT: Filesystem error (dev sdb5)
[   59.938534]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   59.938618] FAT: Filesystem error (dev sdb5)
[   59.938619]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   59.938698] FAT: Filesystem error (dev sdb5)
[   59.938699]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   59.938776] FAT: Filesystem error (dev sdb5)
[   59.938777]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   59.938848] FAT: Filesystem error (dev sdb5)
[   59.938850]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   59.938920] FAT: Filesystem error (dev sdb5)
[   59.938921]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   59.939014] FAT: Filesystem error (dev sdb5)
[   59.939015]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   59.939088] FAT: Filesystem error (dev sdb5)
[   59.939089]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   59.939167] FAT: Filesystem error (dev sdb5)
[   59.939169]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   59.939315] FAT: Filesystem error (dev sdb5)
[   59.939317]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   59.939408] FAT: Filesystem error (dev sdb5)
[   59.939409]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   59.940516] FAT: Filesystem error (dev sdb5)
[   59.940518]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   59.940602] FAT: Filesystem error (dev sdb5)
[   59.940603]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   59.940686] FAT: Filesystem error (dev sdb5)
[   59.940688]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   59.940769] FAT: Filesystem error (dev sdb5)
[   59.940771]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   59.940863] FAT: Filesystem error (dev sdb5)
[   59.940865]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   59.940950] FAT: Filesystem error (dev sdb5)
[   59.940951]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   59.941034] FAT: Filesystem error (dev sdb5)
[   59.941035]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   59.941117] FAT: Filesystem error (dev sdb5)
[   59.941118]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   59.941201] FAT: Filesystem error (dev sdb5)
[   59.941202]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   59.941280] FAT: Filesystem error (dev sdb5)
[   59.941281]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   59.941359] FAT: Filesystem error (dev sdb5)
[   59.941360]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   59.941431] FAT: Filesystem error (dev sdb5)
[   59.941433]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   59.941571] FAT: Filesystem error (dev sdb5)
[   59.941572]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   59.941662] FAT: Filesystem error (dev sdb5)
[   59.941664]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   59.941735] FAT: Filesystem error (dev sdb5)
[   59.941737]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   59.941814] FAT: Filesystem error (dev sdb5)
[   59.941816]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   59.941898] FAT: Filesystem error (dev sdb5)
[   59.941899]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   59.941999] FAT: Filesystem error (dev sdb5)
[   59.942001]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   59.943817] FAT: Filesystem error (dev sdb5)
[   59.943819]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   59.943829] FAT: Filesystem error (dev sdb5)
[   59.943832]     fat_get_cluster: invalid cluster chain (i_pos 0)
[ 2515.222345] FAT: Filesystem error (dev sdb5)
[ 2515.222347]     fat_get_cluster: invalid cluster chain (i_pos 0)
[ 2545.098627] FAT: Filesystem error (dev sdb5)
[ 2545.098629]     fat_get_cluster: invalid cluster chain (i_pos 0)
[ 2640.501904] FAT: Filesystem error (dev sdb5)
[ 2640.501907]     fat_get_cluster: invalid cluster chain (i_pos 0)
[ 2657.814552] FAT: Filesystem error (dev sdb5)
[ 2657.814556]     fat_get_cluster: invalid cluster chain (i_pos 0)


```

fsck 
```

fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
/dev/sda1 is mounted.

```

---

### Post by S.R on 2010-08-19
What does ```
lshw or lsusb
``` say about your external drive being  recognized? If recognized there I think you will need to manually add  it to etc/fstab and maybe you will need to create the mount point.

A good discussion on the UUID for adding the external to etc/fstab is  here: [https://help.ubuntu.com/community/UsingUUID](https://help.ubuntu.com/community/UsingUUID) and there are numerous  threads on making a mount point if you need to.

---

### Post by distorted on 2010-08-19
I will need to manually add it. I will read the discussion. Thanks for the help.

---

### Post by S.R on 2010-08-20
Sounds like you at least have a start. If you are fairly new with using an editor and don't want to learn Vim right off the bat you can go to the terminal and type:

```
gedit /etc/fstab
```I know a hundred heads are probably doing 360's right now off of that suggestion.

Wouldn't mind hearing how things turn out for you though.

---

### Post by distorted on 2010-08-26
I was out of town, sorry for delaying.
lsusb
```

Bus 008 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundatio+n 1.1 root hub
**Bus 002 Device 002: ID 059f:100d LaCie, Ltd **
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 0011:7788  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Then, gedit /etc/fstab
```

proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
UUID=ae44f760-cce0-4f16-8f93-57e7f15b28f4 none            swap    sw              0       0 
```

---

### Post by S.R on 2010-08-26
Unless somebody disagrees I see your external and you need to add it to your fstab using the information on my previous post. You good to go from here or do you need a starting point?

---

### Post by distorted on 2010-08-26
Starting point is needed. Thanks for the help. Appreciate it.

---

### Post by S.R on 2010-08-26
Is there by chance a HFS partition on your external drive? Did some quick research and seems people were having problems with a partition on that drive that if I am remembering correctly is used to set the drive up.

I am thinking that maybe Ubuntu could be looking at that partition and just kind of ignoring the drive.

Could be worth looking into before you go to much trouble.

[http://ubuntuforums.org/showthread.php?t=1351811](http://ubuntuforums.org/showthread.php?t=1351811)

---

### Post by distorted on 2010-08-27
/dev/sdb 
      Partition 1
        Properties for Disk Entity 
        /dev/sdb1 
       Size: 3.82 GB 
       Partition Type: W95 FAT32
       Mount Point: /media/usb0
       Mount Point when Rebooted: No
       File system: vfat32

It's my flash drive, not my external hard drive.

     Unpartitioned space
       Properties for Disk Entity 
       /dev/sdb
       Size:0.00 GB
       Partition Type: None
       Mount Point: Unmounted
       Mount Point when Rebooted: No
       File System: No filesystem

I will reboot and take off my flash drive.
[EDIT]
It's not that and my external hard drive is missing, now. 
```

Bus 008 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by S.R on 2010-09-04
I thought the problem child was your external. Sorry it has taken me so long to get back to you.

---

