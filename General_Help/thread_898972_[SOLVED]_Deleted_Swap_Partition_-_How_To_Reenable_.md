---
title: "[SOLVED] Deleted Swap Partition - How To Reenable It?"
date: 2008-08-23
forum: General Help
---

### Post by rabidg00se on 2008-08-23
Hey all, I recently had to remove my Vista partitions and extend my Ubuntu into the space Now, in order to make the unallocated and Ubuntu partitions contiguous I had to delete the swap partition. I recreated it with GParted at the end of the drive, as sda6. Booting into Ubuntu, I now have no swap. Everything else works just fine, but the system monitor reports using "0 bytes (0.0%) of 0 bytes" of swap memory - ie., nothing.

How do I reenable swap on sda6? I'm asking, rather than just poking around, because it probably has something to do with fstab, and...yeah, I'm not going near fstab.

---

### Post by Tim Sharitt on 2008-08-23
If you want swap tuned on at start up you will have to edit your fstab. It's really not that hard, just be careful and pay attention to what you're doing.
First open /etc/fstab as root in a text editor. For gedit:
```
gksu gedit /etc/fstab
```
You should see a line that looks something like:
```
UUID=e042d3e9-9111-43a3-9316-168e9ade7d66     none    swap   sw         0       0

```
You can replace the UUID=e042d3e9-9111-43a3-9316-168e9ade7d66 part with /dev/sda6 or the uuid of the new partition.

If you absolutely don't want to do this you can always turn swap on manually each time.
```
sudo swapon /dev/sda6
```

---

### Post by rabidg00se on 2008-08-23
I just edited fstab (and I survived!), although I can't reboot X at the moment to make sure it works. It looks like it should though, so thanks a lot!

---

