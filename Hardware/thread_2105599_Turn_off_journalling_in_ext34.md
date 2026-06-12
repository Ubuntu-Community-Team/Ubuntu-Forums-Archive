---
title: "Turn off journalling in ext3/4"
date: 2013-01-16
forum: Hardware
---

### Post by createdcreature on 2013-01-16
Basically, I have to turn off journalling for a tool called Shred to work properly. I have formatted ext4. Is there any way to solve this without going back to good ol' ext2 or similar? I know you have to add a date in fstab, but I don't understand what you need to do?

---

### Post by haqking on 2013-01-16
> **Robert Moyse said:**
> Basically, I have to turn off journalling for a tool called Shred to work properly. I have formatted ext4. Is there any way to solve this without going back to good ol' ext2 or similar? I know you have to add a date in fstab, but I don't understand what you need to do?

```
umount <partition or drive>
``````

tune4fs -O ^has_journal /dev/sdax
```where sdax is where you want to disable it

You may want to do a fs check after then reboot

You can check it is off with

```
sudo dumpe2fs /dev/sdax | more
```

again where x is the number of drive, and look for fs features, has_journal means it is enabled

Peace

---

### Post by tgalati4 on 2013-01-16
Shred is a simple, file overwriting tool.  Depending on your security requirements, there may be some data left over in journalling buffers, but for routine use you can still use the tool.  I think you might suffer a bigger risk by frequently turning journalling on and off on an ext4 system than by data exposure after using shred.  But that is just my opinion.

If you are working in a secured/classified environment, then you should probably only be running ext2 anyway.  If you are a casual home user, I would spend more time making a tinfoil hat. 

You have to add an ext4 option in fstab to turn journalling off:

According to

```
man mount
```

ext4 will interpret ext3 options:

       data={journal|ordered|writeback}
              Specifies the journalling mode for file data.  Metadata is always  journaled.   To  use  modes  other  than
              ordered  on  the root filesystem, pass the mode to the kernel as boot parameter, e.g.  rootflags=data=jour&#8208;
              nal.

              journal
                     All data is committed into the journal prior to being written into the main filesystem.

              ordered
                     This is the default mode.  All data is forced directly out to the main  file  system  prior  to  its
                     metadata being committed to the journal.

              writeback
                     Data ordering is not preserved - data may be written into the main filesystem after its metadata has
                     been committed to the journal.  This is rumoured to be the highest-throughput option.  It guarantees
                     internal  filesystem  integrity,  however it can allow old data to appear in files after a crash and
                     journal recovery.

And when data=somethingelse journaling is turned off.

Again the risk of messing up a bootable disk is not worth it to me.  Any vulnerable data should be on a separate ext2 partition--which is simple enough to create using gparted.

---

### Post by sudodus on 2013-01-16
> **tgalati4 said:**
> Shred is a simple, file overwriting tool.  Depending on your security requirements, there may be some data left over in journalling buffers, but for routine use you can still use the tool.  I think you might suffer a bigger risk by frequently turning journalling on and off on an ext4 system than by data exposure after using shred.  But that is just my opinion.
...
+1

An alternative is to use Ubuntu's encrypted home system (ecryptfs).

---

### Post by createdcreature on 2013-01-18
As my security requirements are very high, and I am not turning off the journal or using anything else apart from ext3/4, how would I clear the journal securely, if I left it on using shred.

---

