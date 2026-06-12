---
title: "How do I remove dual boot and become Ubuntu only?"
date: 2009-08-04
forum: Installation &amp; Upgrades
---

### Post by jrsc109 on 2009-08-04
Hi all

I've been running a dual boot (XP / 9.04) for a while now, and am ready to make the jump to solo 9.04.

In other words, how can I wipe the windows partition so it becomes a part of the linux install?

Does that make sense?  I want to remove windows from the pc.  When I boot the pc, I don't want to have to choose the OS from a grub menu, and I want the current windows partition (c drive) to become linux.

Will I have 2 drives or can I combine the current Ubuntu drive with the C: to make one large drive?

Would it be easier to just trash the entire hard-drive and start again?

I know there will be some issues (printing for one; I have a Dell AIO printer!!) but I intend to install XP as a virtual machine, through which I can print and access other files.

If anyone can offer any hints and tips; in relatively simple language, then that would be most helpful.

Thanks for your advice.

---

### Post by FirstByté on 2009-08-04
**[COLOR="Red"][SIZE="2"]PROCEED WITH CAUTION PLEASE!!![/SIZE][/COLOR]**

While I haven't tried this myself, you may look into this option if you are willing.

**BACKUP ALL YOUR FILES....!!!**

**INSERT A LiveCD**

install GPartEd if you haven't

```
~$ sudo apt-get install gparted
```

From System->Administration->Partition Editor

Right Click the Windoz partition and "Unmount" if it's still mounted. 
You may delete the partition. You can rescale the Ubuntu partition to take the entire space or Merge.

**Then reboot** (Note you'll have to quickly choose the Ubuntu option since you wouldn't have windoz partition any longer)


install Startup-Manager

```
~$ sudo apt-get install startup-manager
```

From System->Administration->Startup-Manager

Un-check "Show bootloader menu" under 'Misc'

Hopefully this should Make you UBUNTU PURE and GRub will still be happy

---

