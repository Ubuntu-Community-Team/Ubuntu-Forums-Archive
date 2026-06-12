---
title: "RAID configuration information"
date: 2011-03-14
forum: Hardware
---

### Post by mickey13 on 2011-03-14
I've inherited responsibility of an existing Ubuntu server.  I'm trying to get some information about it, such as:

1. What RAID configuration is it?

2. What is the size of the hard disks that make up the RAID?

How can I get that information?  Thanks in advance for your help.

---

### Post by fjgaude on 2011-03-14
Is the raid software or hardware?

If software, then run this command:

```
sudo mdadm -Es
```

This will scan the drives of any array on the machine.

If hardware, run this command:

```
sudo fdisk -l
```

That should do it for you. If not let us know.

---

### Post by mickey13 on 2011-03-14
Thanks for your reply.  fdisk -l gave me information about the partitions (/dev/sda1, /dev/sda2, /dev/sda3), but I didn't see any information about the RAID setup.

I don't have mdadm installed, and I'm not sure if it's a hardware or software RAID.  I suppose I can open up the machine and just look, but I'd prefer to take it offline to do that (can't do that at the moment though).  Is there a command to find that out?

---

### Post by fjgaude on 2011-03-14
This server, are you at its keyboard, down the LAN?

You can download mdadm:

```
sudo apt-get install mdadm
```

Then run the command given.

Hardware raid would show as a drive. You see only one drive with three partitions. Now if it is FAKEraid, that Windows uses, made from the BIOS, then we are dealing with something else. That will require the use dmraid software for the array to show in Linux.

---

