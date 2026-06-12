---
title: "Floppy disk entry in fstab"
date: 2008-08-07
forum: General Help
---

### Post by silkstone on 2008-08-07
My fstab looks like this...

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                            0  0  
# /dev/sda1
UUID=5fdbf72c-d69d-44cf-b12e-ea2b8230d754  /               ext3         relatime,errors=remount-ro          0  1  
# /dev/sda5
UUID=30ebe75a-3471-42bb-97c3-7c0f49d84ddb  none            swap         sw                                  0  0  
/dev/scd0                                  /media/cdrom0   udf,iso9660  user,noauto,exec,utf8               0  0  
/dev/scd1                                  /media/cdrom1   udf,iso9660  user,noauto,exec,utf8               0  0  
/dev/fd0                                   /media/floppy0  auto         rw,user,noauto,exec,utf8            0  0  

```

The 'floppy' line has always been there since I did a clean install of Hardy, but this machine has no floppy drive and I'm unlikely ever to use one.

Can I remove that line, or does it have some other purpose? If I do remove it, will it improve performance (e.g. boot-up time) as the OS will not be looking for something that isn't there?

---

### Post by iaculallad on 2008-08-07
You're safe to remove it from your fstab file if you don't have any floppy device installed. Doing this does not improve your system performance.

---

### Post by silkstone on 2008-08-07
Thanks. If it doesn't make any difference I'll probably leave it there, but it's helpful to know that it has no other use.

---

### Post by Krupski on 2008-08-07
> **silkstone said:**
> My fstab looks like this...

```


# before...
/dev/fd0       /media/floppy0  auto         rw,user,noauto,exec,utf8            0  0  

# after...
#/dev/fd0       /media/floppy0  auto         rw,user,noauto,exec,utf8            0  0 
^note


```



You can remove it - but it won't do anything for you.

Rather than deleting the line, just put a '#' at the start and turn it into a comment... in the UNLIKELY event that you want the line back someday.

-- Roger

---

