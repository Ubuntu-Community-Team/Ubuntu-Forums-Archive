---
title: "Able to access but unable to view Vista's shared folders"
date: 2008-10-10
forum: General Help
---

### Post by Aero-Z on 2008-10-10
Hi,

I got Samba installed but I'm unable to see Vista's shared folders with Nautilus. I see all shares with smbtree and I'm able to access those by typing the location into the address bar.

How can I make the folders appear in Nautilus?

Thanks

---

### Post by davidryder on 2008-10-10
It sounds like a share problem on your Vista machine. Did you enable sharing on the folders you want to share?

---

### Post by Aero-Z on 2008-10-10
> **davidryder said:**
> It sounds like a share problem on your Vista machine. Did you enable sharing on the folders you want to share?
Yes, like I said, I'm able to access those shared folders if I type the location into the address bar: smb:// but I'm unable to see those shared folders under Network in Nautilus. I see the Vista machine itself but not shared folders.

---

### Post by davidryder on 2008-10-10
You will probably want to edit your /etc/fstab file and add a mount point for your shares. After that you can add a Favorite in Nautilus to point to the mount location. 

```
sudo mkdir /mnt/vista
gksudo gedit /etc/fstab
```

Add a line like this:

```
//<network name of share>/<share path>/ /mnt/vista cifs username=<winodws_user>,password=<pass>,uid=<your_linux_username>,gid=<your_linux_username>,_netdev 0 0

for example:

//vista-pc/c/ /mnt/vista cifs username=shawn,password=pass4u,uid=aeroz,gid=aeroz,_netdev 0 0

```

Then mount the drive

```
sudo mount -a
```
Then you can navigate to /mnt/vista and there it is.

If you have more than one share name on your Vista machine you can add more directories in /mnt and the respective line in fstab.

If using the hostname doesn't work, you can use the IP address or refer to [this](http://ubuntuforums.org/showthread.php?t=88206)

---

### Post by Aero-Z on 2008-10-10
Is that a workaround or that's what Samba is supposed to do?

---

### Post by davidryder on 2008-10-10
The smb:// is different from using mount. Mounting it makes it appear as a regular drive so it's easier to navigate with CLI or Nautilus. I don't know how to navigate shares using Sambas network folders but I assure you it's a lesser alternative. 

Many many applications can't access Samba network drives but all of them are able to access shares mounted with the mount command or fstab.

---

### Post by Aero-Z on 2008-10-10
> **davidryder said:**
> The smb:// is different from using mount. Mounting it makes it appear as a regular drive so it's easier to navigate with CLI or Nautilus. I don't know how to navigate shares using Sambas network folders but I assure you it's a lesser alternative. 

Many many applications can't access Samba network drives but all of them are able to access shares mounted with the mount command or fstab.
Any difference if smbfs or cifs is used?

---

### Post by davidryder on 2008-10-10
SMBFS is being deprecated and being replaced with CIFS.

---

### Post by gerryg001 on 2009-03-15
With Hardy or later, cifs replaces smbmount and also the helpers for mount, so that mount -t smbfs or -t cifs are the same. As was said earlier, this gives you a far more flexible interface through your mount point.

I use rsync to backup vista after mounting like:
sudo mount -t cifs -o user=aname -o pass=mypass //vista2/C /mnt/vistac

The sticky problems are the speed, and vista's screwy security. Even with admin rights and the following directory shared, it can be difficult to access a /User/auser directory for backup.

---

