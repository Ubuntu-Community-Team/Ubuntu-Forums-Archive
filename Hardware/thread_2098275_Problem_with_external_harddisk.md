---
title: "Problem with external harddisk"
date: 2012-12-26
forum: Hardware
---

### Post by zlatankos on 2012-12-26
i use Ubuntu 12.04 
```
Notebook-PC:~$ uname -r
3.2.0-35-generic-pae
```I used an external disk yesterday , in the  beggining evething was ok. But when i do safely remove or unmount or  restart,shut down etc  and i try to reconnect it  i get the following  message :

```

         unable to mount

Error mounting: mount exited with exit code 13:   ntfs_mst_post_read_fixup_warn: magic: 0x43425355  size: 4096   usa_ofs:   1014  usa_count: 65535: Invalid argument
Actual VCN (0x800009f01000000) of index buffer is different from expected VCN (0x0).
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
```except from this some times i get no message and the nautilus doesnt show something.

when i used the hd to windows seems like it is corrupted and needs a  format, after format (to ntfs) everything is ok in windows whatever i do  write eject etc

but when i write and remove the disk in ubuntu then it get corrapted and  needs format to ntfs. Also this format is ok only in windows when i  tried it with gparted i get the following :
 (i tried format to ntfs , fat32 , ext3 ext4 with gparted and the result is the same....)

[IMG]http://img703.imageshack.us/img703/3605/snapshot2rk.png[/IMG]



before the format the problem seems like this in gparted

[IMG]http://img560.imageshack.us/img560/1653/snapshot1cs.png[/IMG]


summarizing it seems that there is problem when i write in disk and  remove it and using ubuntu, then the data or the file system is getting  corrupted...(in windows everything is fine)

thanks in advance 
and sorry if my english is too bad

---

### Post by fdrake on 2012-12-26
did you  try the suggestion of the error:
> 
run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! 


---

### Post by zlatankos on 2012-12-26
does this mean to run chkdsk then to boot with windows and then to restart and boot again with windows?

i did it but i dint i understant the meaning of twice and The usage of the /f parameter is very
important!                  

Also i mentioned that is beginning with  "checking filesystem on C" and not f ,  and im sure that i writed chkdsk /f
 i also tried it after format and with no format but nothing...

---

### Post by zlatankos on 2012-12-26
ok i found my mistake i run chkdsk and i did restart twice but nothing changed

---

