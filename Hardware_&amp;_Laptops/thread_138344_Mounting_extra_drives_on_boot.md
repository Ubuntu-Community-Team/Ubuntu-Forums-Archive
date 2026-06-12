---
title: "Mounting extra drives on boot"
date: 2006-03-01
forum: Hardware &amp; Laptops
---

### Post by dom on 2006-03-01
Hi all,

I'm having some fun with multiple hard drives in my ubuntu 5.10 system.

I haven't much experience with this so perhaps I'm overlooking something basic.

All suggestions appreciated.

**My Setup**

Desktop system used by a number of people in the house
[U]
Scsci Disk.[/U]
**sda1 **is system
**sda2** is swap
**sda3** is general file storage, used by any and all users.

_IDE 1_
**hda1** is a 5gb spare for farting about with other distros as i see fit
**hda2** is a large ca. 75gb partition for my cd's, which i use to transfer music to a digital player and play through the stereo on shuffle without having to worry about changing cd's

_IDE 2_
**hdb1** has some bad segments or something, so i've 5gb there i don't use
**hdb2** is fine and ca. 35gb and currently i don't use or mount it.


Now, I tried to add sda3 and hda2 to fstab to be mounted.

sda3 is mounted fine !

hda2 does not mount, whether i specify ext3 or auto as the fs type.

after boot, i can mount the drive find with either 'mount -a' or 'mount /dev/hda2 /media/music'

further, when i put the last parameter in the fstab to 2 (as far as i can make out this should cause an fsck every once and a while - sda1 has the last parm set to '1')

as i was saying, when i set the last parm to '2', it moans about some errors.

but i can bypass that and mount and use the drive mannually without issue.

i have run fsck on both these driver, i got a message for one and nothing for the other, but neither produced any messages that was an obvious error.

so, anything crazy in the above ?

anything else i could try or look out for ?

i would rather have a diagnosis and potential solutions before i just redo the drive(s), but i'm already looking for another spare drive to hold the data in case i need to zap and re-part and re-format the hda.

many thanks and regards

dom

---

### Post by dom on 2006-03-23
hi,

can anybody pleae help me on this one ?

i'm booting from a scsi disk
i have an ide drive that i want to mount on boot
it won't mount.

if i do 'mount -a' after boot, all is fine.

fsck says it's fine, but adding a pass 2 to the fstab results in the boot being stalled with the message :

"fsck.ext3: No such file or dir while trying to open /dev/hda2"

if i just continue (CTRL-D) then it mounts the drive fine !!!

but i don't always want to be sitting at the pc while it boots. 

i would like it to just mount the drive.

/etc/modules has ide, ide-disk, ide-generic, ide-cd, and ide-mod in there, but it doesn't seem to matter.

is it possibly still module related ?

due to the modules not being available early enough at boot ?

any help appreciated, i'm out of my depth on this one but still trying to fix and asking for help where i can

dóm

---

