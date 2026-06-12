---
title: "New to Linux - Is my harddrive dead?"
date: 2005-06-27
forum: Hardware &amp; Laptops
---

### Post by thep on 2005-06-27
Please let me know if this is the wrong forum for this.

I've looked through the forum and lots of people have had this problem but everyone else's version will quit after 10 or 20 lines. I must be into the hundreds or thousands by now.

I have an external USB 2.0 harddrive, formatted as NTFS. It's about three years old and has always been a little buggy. Recently I plugged it into a Windows machine and got an error message which I can't remember, then I plugged it into my Ubuntu system and got this:

NTFS-fs error (device sda5): ntfs_end_buffer_async_read(): Buffer I/O error, Logical Block 84070700
NTFS-fs error (device sda5): ntfs_end_buffer_async_read(): Buffer I/O error, Logical Block 84070701
NTFS-fs error (device sda5): ntfs_end_buffer_async_read(): Buffer I/O error, Logical Block 84070702
NTFS-fs error (device sda5): ntfs_end_buffer_async_read(): Buffer I/O error, Logical Block 84070703
NTFS-fs error (device sda5): ntfs_end_buffer_async_read(): Buffer I/O error, Logical Block 84070704
NTFS-fs error (device sda5): ntfs_end_buffer_async_read(): Buffer I/O error, Logical Block 84070705
NTFS-fs error (device sda5): ntfs_end_buffer_async_read(): Buffer I/O error, Logical Block 84070706
NTFS-fs error (device sda5): ntfs_end_buffer_async_read(): Buffer I/O error, Logical Block 84070707
NTFS-fs error (device sda5): ntfs_end_buffer_async_read(): Buffer I/O error, Logical Block 84070708
NTFS-fs error (device sda5): ntfs_end_buffer_async_read(): Buffer I/O error, Logical Block 84070709
NTFS-fs error (device sda5): ntfs_end_buffer_async_read(): Buffer I/O error, Logical Block 84070710
NTFS-fs error (device sda5): ntfs_end_buffer_async_read(): Buffer I/O error, Logical Block 84070712
NTFS-fs error (device sda5): ntfs_end_buffer_async_read(): Buffer I/O error, Logical Block 84070713
NTFS-fs error (device sda5): ntfs_end_buffer_async_read(): Buffer I/O error, Logical Block 84070714
NTFS-fs error (device sda5): ntfs_end_buffer_async_read(): Buffer I/O error, Logical Block 84070715
NTFS-fs error (device sda5): ntfs_end_buffer_async_read(): Buffer I/O error, Logical Block 84070716
NTFS-fs error (device sda5): ntfs_end_buffer_async_read(): Buffer I/O error, Logical Block 84070717
NTFS-fs error (device sda5): ntfs_end_buffer_async_read(): Buffer I/O error, Logical Block 84070718
NTFS-fs error (device sda5): ntfs_end_buffer_async_read(): Buffer I/O error, Logical Block 84070719
NTFS-fs error (device sda5): ntfs_end_buffer_async_read(): Buffer I/O error, Logical Block 84070723
NTFS-fs error (device sda5): ntfs_end_buffer_async_read(): Buffer I/O error, Logical Block 84070724
NTFS-fs error (device sda5): ntfs_end_buffer_async_read(): Buffer I/O error, Logical Block 84070725
NTFS-fs error (device sda5): ntfs_end_buffer_async_read(): Buffer I/O error, Logical Block 84070726
NTFS-fs error (device sda5): ntfs_end_buffer_async_read(): Buffer I/O error, Logical Block 84070727
NTFS-fs error (device sda5): ntfs_end_buffer_async_read(): Buffer I/O error, Logical Block 84070728
NTFS-fs error (device sda5): ntfs_end_buffer_async_read(): Buffer I/O error, Logical Block 84070729
NTFS-fs error (device sda5): ntfs_end_buffer_async_read(): Buffer I/O error, Logical Block 84070730
NTFS-fs error (device sda5): ntfs_end_buffer_async_read(): Buffer I/O error, Logical Block 84070731
NTFS-fs error (device sda5): ntfs_end_buffer_async_read(): Buffer I/O error, Logical Block 84070752

and so on...

It's been printing this on the tty screens for the last couple hours at a speed of maybe 1 line a second. Every now and again it'll skip some blocks (maybe 2 blocks, maybe 21). I don't see this stopping.

Oh, and the messages are interspersed with a message telling me an inode is bad, and that I should run chkdsk--but I can't because I don't have windows anymore. So I try to tried plugging it into my roommates computer and the computer spends all this time trying to do stuff with my harddrive but just gives back errors.

I just want to know if my harddrive is dead or, if not, how I can fix it.  At this point, I would be quite happy to lose everything on the drive if it would just keep working.

If it's dead, I just want to know! HELP!

---

### Post by rockmusic88 on 2005-06-27
It seems to be dead, but you could try re-formating it and seing what hapens. would be really haelpful it we could see the windows error message you recieved.

---

