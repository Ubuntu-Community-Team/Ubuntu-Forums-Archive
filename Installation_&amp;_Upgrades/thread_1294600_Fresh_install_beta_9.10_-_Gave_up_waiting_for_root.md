---
title: "Fresh install beta 9.10 - Gave up waiting for root device"
date: 2009-10-18
forum: Installation &amp; Upgrades
---

### Post by Bernardobr on 2009-10-18
Hi guys,
just gave a fresh install of ubuntu 9.10 beta on my notebook (filesystem was ext4). All went alright, but when I boot it, it gives me the 'Gave up waiting for root device' error and throws me a shell... if I type exit, it works, though takes like 1 min to boot, but if I do that on the next boot, it won't boot anymore, gives me kernel panic and other errors...
I have tried setting rootdelay=90 and no success, as this is the second boot (first one is for setting rootdelay), it just won't boot anymore...

I have tried installing 9.04 and beta 9.10, both give me the same error... any idea? Thank you advance
I have also tried uncommenting *#GRUB_DISABLE_LINUX_UUID*=true 

BTW: Notebook is acer 1410... HD is IDE, could this be a problem?

Edit: Reinstalled again, now the errors I get are:
A lot of
> end_request: I/O error, dev sda, sector xxxxxand then
> EXT4-fs error (device sda6): ext4_dx_find_entry: bad entry in directory #98137: directory entry across blocks - offset=24596, inode=0, rec_len=4096, name_len=1
init: caught segmentation fault, core dumped
kernel panic -- not syncing: Attempted to kill init!

I also get
> ata1.00: exception Emask 0x0 SAct 0x1 Serr 0x0 action 0x6 frozen

---

### Post by Bernardobr on 2009-10-19
Fixed by putting libata.noacpi=1 at the kernel line...
Will I need to put this parameter back everytime grub or a kernel updates? Should I send a bug report telling that this HD doesn't support the feature?

---

### Post by aspergerian on 2009-11-05
> **Bernardobr said:**
> Fixed by putting libata.noacpi=1 at the kernel line...
Will I need to put this parameter back everytime grub or a kernel updates? Should I send a bug report telling that this HD doesn't support the feature?

Bernard, 

Your 1410's error messages are akin to many of my 1410's, which runs 9.04 and 9.10 from a CD but not from an install. Thus (at this point) my typing libata.noacpi=1 seems unlikely until my 1410 boots from installed Ubuntu. 

Just for the record, where does one type "libata.noacpi=1"?  In the terminal when it opens? In some other directory?

---

