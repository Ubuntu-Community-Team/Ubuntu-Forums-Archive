---
title: "mounting smb shares at 1 mountpoint?"
date: 2008-07-17
forum: General Help
---

### Post by thinking on 2008-07-17
hi all

i just wanted to create something like raid0 using smb shares
in case a smb share is full of hard disk capacity the second share should be used and so on
can it be done transparently like sofware raid using mdadm or like that?

i got a suggestion for lvm or unionfs but i found some posts which dont seem to be promising

unionfs dont seem to be able to do this
lvm = i have no idea and as far as i can see its grouping /dev partitions together which i dont have
raif = [http://www.fsl.cs.sunysb.edu/project-raif.html]("http://www.fsl.cs.sunysb.edu/project-raif.html") im not sure if there is a better, more often used/tested/documented/easier implementation

so anybody knows or has a hint how to group shares from a remote host together OR group local directories together in another directory

thx all

---

### Post by rbmorse on 2008-07-17
you want LVM. I can't help you set it up, but it will do what you want (combine separate partitions into one logical unit).

---

### Post by thinking on 2008-07-21
i already read about this and every example i found used some hard drive's on localhost, so im asking one more question, just to be absolutely sure its the right direction.

Do you mean by using LVM that its possible to combine 2 or more remote samba shares on localhost at 1 mountpoint, which means im not able to use /dev/hd.. devices, but have to use remote samba shares (and i think this means smbmount and then lvm to achive this)?

the reason why im asking is because i already read lvm docs but i only found references for /dev devices and since lvm is a kernel module i think its purpose is to combine hard drives (or some kinds of block devices) to logical groups and not remote shares, which are already paritiond and formated
and i didnt really find anything related to lvm and samba

thx for your help

---

