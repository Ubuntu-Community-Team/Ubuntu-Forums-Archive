---
title: "Permissions With External HD?"
date: 2008-07-10
forum: Hardware
---

### Post by kidko on 2008-07-10
I recently purchased a LaCie 160gb "mobile disk" (see also: external mini-USB hard drive), originally formatted in FAT32. It mounted correctly and gave me read-write permission. However, since it is just going to be for Linux, I re-formatted it as ext3. Now, it mounts under root's permissions either; as my username, all I get is reading permission. It's fixable by running "sudo chmod 777 <mountpoint>," but is this permanent? When I unplug it, will the drive re-mount with full permissions? If it's not, how could I do that?

---

