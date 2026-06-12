---
title: "some confusion regarding mounting nfs partitions for a cluster"
date: 2008-05-04
forum: Hardware
---

### Post by HPCE_Larry on 2008-05-04
I am trying to build a beowulf cluster, generally following the configuration this guy came up with here: [http://www.calvin.edu/~adams/research/microwulf/sys/microwulf_notes.pdf](http://www.calvin.edu/~adams/research/microwulf/sys/microwulf_notes.pdf)

My chief difficulty stems from where I must edit fstab. My partitions are roughly as follows:

22gig /root
22gig /home
2gig swap
8gig /root for node1
8gig /root for node2

There is an ubuntu server install on each of the 2 nodes. The instructions read

"Before you can export the diskless nodes root partitions over NFS, you must
mount them somewhere on the head node. I mounted them to /nodes/nfs/node1,
/nodes/nfs/node2 and /nodes/nfs/node3. Feel free to change this, but those
are the locations I will reference for the rest of this howto. Put appropriate
entries in /etc/fstab so these are mounted automatically at boot."

which doesn't help too much if one is new to this. I have added ```
/dev/sda6       /nodes/nfs/node1   ext3   defaults 0 2
/dev/sda7       /nodes/nfs/node2   ext3   defaults 0 2
``` to my fstab file.

My question is this: How can I tell this actually worked? Will I see these partitions under computer? Do I have to create a folder called /nodes/nfs ?

---

### Post by HPCE_Larry on 2008-05-07
I know this topic is not exactly common but surely someone knows. If not, is there another forum I could be pointed to?

---

### Post by ajt on 2009-01-12
Hello,

I've started a new discussion, to try and bring together threads in different forums about Ubuntu clustering at:

[http://ubuntuforums.org/showthread.php?p=6495259]("http://ubuntuforums.org/showthread.php?p=6495259")

    Tony.

---

