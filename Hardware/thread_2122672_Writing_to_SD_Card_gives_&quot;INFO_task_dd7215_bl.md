---
title: "Writing to SD Card gives &quot;INFO: task dd:7215 blocked for more than 120 seconds.&quot;"
date: 2013-03-05
forum: Hardware
---

### Post by Ubuntiac on 2013-03-05
Hi there. I'm trying to write an image file to my sd card using dd. The trouble is that any time I try to use dd to the card with sudo, or make a new file system on the card, it just sits there forever seemingly doing nothing. If I look at mesg I see this over and over:

```
[11520.488950] INFO: task dd:7215 blocked for more than 120 seconds.
[11520.488957] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[11520.488961] dd              D ffff880073b2ba70     0  7215   7214 0x00000000
[11520.488968]  ffff880073b2b9c8 0000000000000086 ffff8800646d0820 ffff880073b2bfd8
[11520.488975]  ffff880073b2bfd8 ffff880073b2bfd8 ffff8800ab16e180 ffff8800646d0820
[11520.488980]  0000000000000003 ffff880073b2bd80 002f880073b2b918 00000000d8df3fcc
[11520.488986] Call Trace:
[11520.489000]  [<ffffffff8124374a>] ? part_round_stats+0x5a/0x70
[11520.489006]  [<ffffffff81246ff5>] ? queue_unplugged+0x65/0x120
[11520.489014]  [<ffffffff811b5bb0>] ? __wait_on_buffer+0x30/0x30
[11520.489021]  [<ffffffff814ba649>] schedule+0x29/0x70
[11520.489026]  [<ffffffff814ba71f>] io_schedule+0x8f/0xd0
[11520.489031]  [<ffffffff811b5bbe>] sleep_on_buffer+0xe/0x20
[11520.489036]  [<ffffffff814b8160>] __wait_on_bit+0x60/0x90
[11520.489042]  [<ffffffff811b5bb0>] ? __wait_on_buffer+0x30/0x30
[11520.489047]  [<ffffffff814b820c>] out_of_line_wait_on_bit+0x7c/0x90
[11520.489053]  [<ffffffff8107bec0>] ? autoremove_wake_function+0x40/0x40
[11520.489058]  [<ffffffff811b5baa>] __wait_on_buffer+0x2a/0x30
[11520.489064]  [<ffffffff811b7b23>] __block_write_begin+0x3f3/0x550
[11520.489069]  [<ffffffff811bbff0>] ? I_BDEV+0x10/0x10
[11520.489074]  [<ffffffff811bbff0>] ? I_BDEV+0x10/0x10
[11520.489079]  [<ffffffff811b7eb1>] block_write_begin+0x51/0xa0
[11520.489085]  [<ffffffff811211c7>] ? unlock_page+0x27/0x30
[11520.489090]  [<ffffffff811bc633>] blkdev_write_begin+0x23/0x30
[11520.489094]  [<ffffffff81120acc>] generic_file_buffered_write+0x11c/0x2b0
[11520.489101]  [<ffffffff8119df39>] ? file_update_time+0x49/0xf0
[11520.489107]  [<ffffffff81122579>] __generic_file_aio_write+0x1b9/0x3b0
[11520.489112]  [<ffffffff811bce46>] blkdev_aio_write+0x56/0xc0
[11520.489119]  [<ffffffff8108fa75>] ? cpuacct_charge+0x75/0xb0
[11520.489126]  [<ffffffff81184177>] do_sync_write+0xa7/0xe0
[11520.489132]  [<ffffffff81184848>] vfs_write+0xa8/0x180
[11520.489136]  [<ffffffff81184b92>] sys_write+0x52/0xa0
[11520.489141]  [<ffffffff814bc919>] ? do_device_not_available+0x19/0x20
[11520.489147]  [<ffffffff814c311d>] system_call_fastpath+0x1a/0x1f

```

Here's the command I'm using:
```
sudo dd if=./XBian1.0Alpha5.img of=/dev/mmcblk0
```

I'm on Kubuntu 12.10 using a Patriot 32Gb sd card in a Dell Latitude XT laptop with it's built in card reader. The SD card is seen fine by KDE and appears as /dev/mmcblk0

Any ideas?

---

