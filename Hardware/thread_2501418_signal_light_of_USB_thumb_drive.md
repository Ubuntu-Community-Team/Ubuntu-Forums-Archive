---
title: "signal light of USB thumb drive"
date: 2024-10-06
forum: Hardware
---

### Post by mangada on 2024-10-06
Some USB thumb drive has signal light, which will flash when the USB thumb drive is being accessed, is my mind right?

---

### Post by sudodus on 2024-10-06
What do you mean by 'right in most cases'?

I think it flashes when read from or written to.

But generally, both for USB drives with and without signal light, **all partitions on it should be unmounted before you unplug it**. Run
```

sudo umount /dev/sdx*

```
where x is the drive letter (for example a or b) in a terminal window and wait for the prompt to appear.

You can also click on the eject symbol if you use a graphical tool (for example Files) and wait for the eject symbol to disappear.

This way you can be sure that all write operations have finished (that all buffers are flushed).

---

### Post by mangada on 2024-10-10
During boot, signal light of USB thumb drive flashes more than 5 second?

---

### Post by TheFu on 2024-10-10
> **mangada said:**
> Some USB thumb drive has signal light, which will flash when the USB thumb drive is being accessed, is my mind right?

I'm not a qualified psychologist, so I can't say anything about your mind, but some USB flash storage does have an LED that flashes when active.  I have a few like that, but most don't bother.  It is a more expensive to manufacture flash storage with an LED than not to do that.

Under linux, as sudodus points out, we can't trust any LED on flash storage to provide a clue as to when it is safe to remove the device.  It cannot be mounted or file system corruption is likely.  The solution is to use the "eject" button in a GUI program or the **umount** or **fusermount -u** commands to un-mount the file system. Which command should be used depends on how the file system was mounted.

---

