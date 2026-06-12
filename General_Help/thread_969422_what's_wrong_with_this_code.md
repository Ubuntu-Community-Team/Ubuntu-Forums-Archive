---
title: "what's wrong with this code"
date: 2008-11-03
forum: General Help
---

### Post by rusty_jones on 2008-11-03
the print out for my pc is;
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd6fdd6fd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   619145099   309572518+  83  Linux
/dev/sda2       619145100   625137344     2996122+   5  Extended
/dev/sda5       619145163   625137344     2996091   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000c1193

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63  1953520064   976760001    b  W95 FAT32

Disk /dev/sdc: 1053 MB, 1053556736 bytes
255 heads, 63 sectors/track, 128 cylinders, total 2057728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x73696420

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63     2056319     1028128+ v

in my conky rc file the entry is /dev/sdb1; why is the output showing the output for sda1?



${alignc}File systems

${color}/dev/sda1${color lightgreen} ${fs_used_perc /}%   ${fs_used /}/${fs_size /}   ${fs_bar /}
${color}/dev/sda3${color lightgreen} ${fs_used_perc /media/stuff/}% ${fs_used /media/stuff/}/${fs_size /media/stuff/} ${fs_bar /media/stuff/}
${color}/dev/sdb1${color lightgreen} ${fs_used_perc /}%   ${fs_used /}/${fs_size /}   ${fs_bar /}


Rusty

---

### Post by easybake on 2008-11-03
> ${color}/dev/sdb1${color lightgreen} ${fs_used_perc /}% ${fs_used /}/${fs_size /} ${fs_bar /}

The problem is that you aren't telling Conky the path to the device you want to measure. Conky doesn't read by line, it only reads the individual variables. You have to add the path to each of the variables. 

Like this ${fs_used_perc /home/easybake/blahblah}

---

