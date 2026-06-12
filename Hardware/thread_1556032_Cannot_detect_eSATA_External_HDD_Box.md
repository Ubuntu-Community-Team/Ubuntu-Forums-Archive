---
title: "Cannot detect eSATA External HDD Box"
date: 2010-08-18
forum: Hardware
---

### Post by billyauhk on 2010-08-18
I recently bought an eSATA+USB external HD box and a WD hard disk, and would like to connect it to my Ubuntu notebook thru eSATA. I have read some guide on the web and installed scsiadd, tried out scsiadd -s 3, but it does not work.

I have checked that the BIOS have been set to the AHCI mode, and when I ask the BIOS to boot with the eSATA disk, it *correctly* tells me media error (as the hard disk is entirely new).

So what's left to me is why Ubuntu cannot detect the disk. Can anyone help?

(I have tried to do play with the silly command:
for i in {1..100};do scsiadd -s $i;done
)

---

### Post by dougalkerr on 2010-09-06
I am trying to do the same with a Toshiba drive. Have you had any luck from anywhere?

---

