---
title: "auto-mount USB devices on startup AND hotplug"
date: 2008-08-21
forum: General Help
---

### Post by kellner on 2008-08-21
Hi, 

I have two external USB devices (a harddrive and a usb-stick) that ideally should behave in this way: 

- when attached to the PC, automount on startup with read-and-write permissions for the regular user that logs in (i.e. not limited to root), and always to the same mountpoint (/media/SOMETHING)

- when they are attached to the PC after startup, they should automatically be mounted, again with non-root permissions, at the same mountpoint (/media/SOMETHING)

Problems: 

I have to add that I'm a terribly lazy unmounter - I regularly pull the usb-stick without unmounting first. I know I shouldn't do this, but in my ideal world, I'd like ubuntu to take notice of it and free the device point. For what usually happens when I pull the stick and push it back in is that it gets assigned the next device letter (say, /dev/sdd1 instead of /dev/sdc1) and doesn't get mounted. 

Now, I thought I could solve all this by editing /etc/fstab and entering the appropriate UUIDs. I did this, and the first mounts worked fine - when I shut down the system and reboot with the devices plugged in, it works fine, too. 

Problems arise when I connect the devices after startup: an error-message occurs informing me that only root is allowed to mount the device. 

Second, when I pull out the stick and then push it back in, I'm informed that it can't be mounted to the mountpoint /media/SOMETHING because according to mtab, there's already another device mounted there. I suppose that this mtab entry is also responsible for the device letter assignments I described above. 

Any ideas as to what I could do to get the desired behaviour? Is there a way to automatically delete the entry from mtab after the device is pulled? And is there a way to allow non-root-users automount the devices after startup? 

Thanks in advance,

---

