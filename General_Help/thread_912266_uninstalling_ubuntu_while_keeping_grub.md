---
title: "uninstalling ubuntu while keeping grub"
date: 2008-09-06
forum: General Help
---

### Post by mocthemad on 2008-09-06
hi people!

not too long ago, ubuntu won me over. i eventually want to transfer from vista to a linux OS, but for now i want to test a handful of distros on my laptop. i won't be uninstalling vista right now, it contains all the programs and files i need for the moment. unfortunately, i don't have enough space on my hard drive to allow for multiple distro installations.
my question is this: how can i uninstall ubuntu (8.04) COMPLETELY (freeing up all the space its installation took) without removing GRUB?

up until this point, i have followed the instructions here: [http://www.users.bigpond.net.au/hermanzone/p18.htm#If_you_are_about_to_uninstall_Ubuntu](http://www.users.bigpond.net.au/hermanzone/p18.htm#If_you_are_about_to_uninstall_Ubuntu) under the "Keep GRUB and Make a Dedicated GRUB Partition" section.

i used my ubuntu live CD and removed all directories except for /boot (vista wasn't touched).

now, however, i am stuck lookin at my partitions in my gparted live cd and there are two swap partitions which seem useless, as well as the partition Ubuntu was installed on (for some reason i cannot reduce its size down to 60mb which i am trying to do in order to keep GRUB there)

im typing this before i run to work, so i apologize for missing info. thanks for reading! :)

---

### Post by unutbu on 2008-09-06
Boot from the LiveCD.
Mount your ubuntu partition at /mnt ([http://ubuntuforums.org/showpost.php?p=5586420&postcount=3](http://ubuntuforums.org/showpost.php?p=5586420&postcount=3))

Remove all the files in the top level of /mnt/boot, but leave the files in /mnt/boot/grub alone. 

Things like this you can delete, except for the grub directory:
```

  /mnt/boot:
  total used in directory 61008 available 263491296
  drwxr-xr-x  3 root root     4096 2008-07-31 20:15 .
  drwxr-xr-x 21 root root     4096 2008-07-23 23:40 ..
  -rw-r--r--  1 root root   424317 2008-02-12 05:39 abi-2.6.22-14-generic
  -rw-r--r--  1 root root    75311 2008-02-12 05:39 config-2.6.22-14-generic
  -rw-r--r--  1 root root    89519 2008-05-01 19:58 config-2.6.25
[COLOR="Red"]**  drwxr-xr-x  2 root root     4096 2008-07-04 11:58 grub  # Don't delete this directory or its contents**[/COLOR]
  -rw-r--r--  1 root root  7227740 2008-07-31 20:15 initrd.img-2.6.22-14-generic
  -rw-r--r--  1 root root  7227961 2008-02-21 15:34 initrd.img-2.6.22-14-generic.bak
  -rw-r--r--  1 root root 41881529 2008-05-01 21:28 initrd.img-2.6.25
  -rw-r--r--  1 root root   103204 2007-09-28 06:06 memtest86+.bin
  -rw-r--r--  1 root root   823535 2008-02-12 05:39 System.map-2.6.22-14-generic
  -rw-r--r--  1 root root   886894 2008-05-01 20:51 System.map-2.6.25
  -rw-r--r--  1 root root  1764536 2008-02-12 05:39 vmlinuz-2.6.22-14-generic
  -rw-r--r--  1 root root  1834240 2008-05-01 20:51 vmlinuz-2.6.25
```

This will free up some more space.
You can use ```
gksu gedit /mnt/boot/grub/menu.lst
```
to remove the boot stanzas referring to Ubuntu. Just be sure to leave the Vista boot stanza, of course.

Then run GParted to make the partition smaller. 
You can also delete the Linux swap partitions.

---

### Post by mocthemad on 2008-09-07
thanks buddy! everything worked out for me in the end :)

---

