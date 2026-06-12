---
title: "(Un)mount Windows Partition with gui"
date: 2008-01-12
forum: Hardware &amp; Laptops
---

### Post by JaggedOne on 2008-01-12
Whenever I mount and unmount my windows partition in the GUI it says I don't have permissions. I can do it with the CLI but I prefer not to use that if I have to. How do I set the permissions on the drive so I can mount and unmount it as a user.

Follow up question. I accidentally named the mount point for that drive WIndows instead of Windows. How do I fix that?

---

### Post by MobiusNZ on 2008-01-12
You'll need to edit your fstab file to allow user mount. 
```

#device        #mountpoint  #filesystem    #mount options       #extra stuff (just leave 0 0)
/dev/sdxx     /windows       nfts                 defaults,rw,user     0    0

```
(the option user allows non-root to dis/mount)

If you change the mountpoint make sure the directory exists...

---

### Post by JaggedOne on 2008-01-12
Sorry im a bit of a noob. What would be the command to do that?

---

### Post by Yellow Pasque on 2008-01-12
1. Verify the path of your drive 
```
sudo lshw -businfo -C disk
```

2. Get your mount point renamed how you want it (I'm assuming it's in the media directory)
```
cd /media
sudo mv WIndows/ Windows/
```

3. Edit fstab and add the 'user' option to the mount options for the drive path you got in step 1
```
sudo gedit /etc/fstab
```

---

### Post by MobiusNZ on 2008-01-12
> **JaggedOne said:**
> Sorry im a bit of a noob. What would be the command to do that?

Please note that the fstab file is where linux finds the information about the harddrive layout. ie it is a fairly critical system file. BACK IT UP BEFORE PLAYING WITH IT!!!

```

sudo cp /etc/fstab /etc/fstab.bak

```

Then edit like Temüjin says.

---

