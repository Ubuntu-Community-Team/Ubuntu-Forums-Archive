---
title: "NTFS drives not mounted in Hardy, ntfs-3g installed."
date: 2008-06-11
forum: Hardware
---

### Post by derfinsterling on 2008-06-11
So, I've had the same problem as some others here - After the Upgrade to Hardy, my NTFS partitions wouldn't be mounted and my external harddrive wouldn't mount on plugging in as well.

Found a solution here on these forums (somewhere) that the link to the libfuse.so.2 package is simply wrong.

So I changed it:
sudo mv /usr/local/lib/libfuse.so.2 /usr/local/lib/libfuse.so.2.old
sudo ln -s /lib/libfuse.so.2.7.2 /usr/local/lib/libfuse.so.2

That works. I can access the internal and external disks once more.

Then sooner or later, another update comes in and screws this over again and I have to redo it.

That's getting kinda boring - so my question is: Any way to make this permanent?

I already tried re-installing ntfs-3g, storage device manager and a bunch of other stuff.

I though about uninstalling and reinstalling libfuse, but it's got a bunch of dependencies that I'm just not comfortable screwing around with.

So - any advice?

---

### Post by stchman on 2008-06-11
> **derfinsterling said:**
> So, I've had the same problem as some others here - After the Upgrade to Hardy, my NTFS partitions wouldn't be mounted and my external harddrive wouldn't mount on plugging in as well.

Found a solution here on these forums (somewhere) that the link to the libfuse.so.2 package is simply wrong.

So I changed it:
sudo mv /usr/local/lib/libfuse.so.2 /usr/local/lib/libfuse.so.2.old
sudo ln -s /lib/libfuse.so.2.7.2 /usr/local/lib/libfuse.so.2

That works. I can access the internal and external disks once more.

Then sooner or later, another update comes in and screws this over again and I have to redo it.

That's getting kinda boring - so my question is: Any way to make this permanent?

I already tried re-installing ntfs-3g, storage device manager and a bunch of other stuff.

I though about uninstalling and reinstalling libfuse, but it's got a bunch of dependencies that I'm just not comfortable screwing around with.

So - any advice?

Did you upgrade Ubuntu via the upgrade route or the clean install route?  If upgrade route that is probably your problem.

I recommend a clean install.  The ntfs-3g package is installed by default and used by default on ALL NTFS drives in Ubuntu.  In the fstab file the ntfs = ntfs-3g.

After a clean install of Hardy your NTFS external and internal drives should function as they should.

---

