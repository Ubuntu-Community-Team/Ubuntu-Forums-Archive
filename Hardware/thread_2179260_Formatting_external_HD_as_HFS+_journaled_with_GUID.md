---
title: "Formatting external HD as HFS+ journaled with GUID partition table (GPT)"
date: 2013-10-07
forum: Hardware
---

### Post by liquidcross on 2013-10-07
I've got an old Mac external backup HD I've been trying to upgrade to a GUID partition table (so I can encrypt it), but Disk Utility on the Mac won't reformat it properly. (Getting "cannot write to last block" errors.) So, I plugged it into my Linux box, and I'm easily able to make HFS+ volumes with GPT using Gparted. However, I can't make a journaled HFS+ volume that way, so I use the following command in Terminal instead:

**mkfs.hfs -J -v BackupDrive /dev/drive**

That makes a journaled HFS+ volume all right, but it's missing the GPT! Is there any way I can accomplish both? I've heard of a tool called gdisk, but I don't know if that's what I'm looking for.

---

