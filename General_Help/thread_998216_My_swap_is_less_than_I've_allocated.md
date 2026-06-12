---
title: "My swap is less than I've allocated"
date: 2008-11-30
forum: General Help
---

### Post by portis on 2008-11-30
Hello, everybody.

I've a 2GB swap partition.

$sudo fdisk /dev/sda

   Device Boot      Start         End      Blocks   Id  System
/dev/sda8           19177       19444     2152678+  82  Linux swap/Solaris

$sudo parted
$print list

Number  Start   End     Size    Type      File system  Flags
8      158GB   160GB   2204MB  logical   linux-swap


But when I use top command, it's less than 2GB.

$top

Mem:   2028004k total,  2011380k used,    16624k free,       72k buffers
Swap:  1358404k total,       28k used,  1358376k free,   227488k cached

Can anyone tell me why? Thanks.

---

### Post by Elfy on 2008-11-30
At a guess do you have the 32bit ubuntu installed because I believe that's about all it will recognise.

---

### Post by portis on 2008-11-30
Thanks for your reply.

It's a 64bit intrepid.

---

