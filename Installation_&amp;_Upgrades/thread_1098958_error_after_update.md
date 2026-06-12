---
title: "error after update"
date: 2009-03-17
forum: Installation &amp; Upgrades
---

### Post by yui789 on 2009-03-17
today after updating some packages i got this message

E: mdadm: subprocess post-installation script returned error exit status 2

in the synaptic panel appears an error after
setting up mdadm (2.6.7-3ubuntu8 )...
Generating array device nodes... rm: cannot remove `md0-': Read-only file system
mknod: `md0-': Read-only file system
rm: cannot remove `md0-': Read-only file system
rm: cannot remove `md1-': Read-only file system
mknod: `md1-': Read-only file system
rm: cannot remove `md1-': Read-only file system
rm: cannot remove `md2-': Read-only file system
mknod: `md2-': Read-only file system
rm: cannot remove `md2-': Read-only file system
rm: cannot remove `md3-': Read-only file system
mknod: `md3-': Read-only file system
rm: cannot remove `md3-': Read-only file system
rm: cannot remove `md4-': Read-only file system
mknod: `md4-': Read-only file system
rm: cannot remove `md4-': Read-only file system
rm: cannot remove `md5-': Read-only file system
mknod: `md5-': Read-only file system
rm: cannot remove `md5-': Read-only file system
rm: cannot remove `md6-': Read-only file system
mknod: `md6-': Read-only file system
rm: cannot remove `md6-': Read-only file system
rm: cannot remove `md7-': Read-only file system
mknod: `md7-': Read-only file system
rm: cannot remove `md7-': Read-only file system
rm: cannot remove `md8-': Read-only file system
mknod: `md8-': Read-only file system
rm: cannot remove `md8-': Read-only file system
rm: cannot remove `md9-': Read-only file system
mknod: `md9-': Read-only file system
rm: cannot remove `md9-': Read-only file system
rm: cannot remove `md10-': Read-only file system
mknod: `md10-': Read-only file system
rm: cannot remove `md10-': Read-only file system
rm: cannot remove `md11-': Read-only file system
mknod: `md11-': Read-only file system
rm: cannot remove `md11-': Read-only file system
rm: cannot remove `md12-': Read-only file system
mknod: `md12-': Read-only file system
rm: cannot remove `md12-': Read-only file system
rm: cannot remove `md13-': Read-only file system
mknod: `md13-': Read-only file system
rm: cannot remove `md13-': Read-only file system
rm: cannot remove `md14-': Read-only file system
mknod: `md14-': Read-only file system
rm: cannot remove `md14-': Read-only file system
rm: cannot remove `md15-': Read-only file system
mknod: `md15-': Read-only file system
rm: cannot remove `md15-': Read-only file system
rm: cannot remove `md16-': Read-only file system
mknod: `md16-': Read-only file system
rm: cannot remove `md16-': Read-only file system
rm: cannot remove `md17-': Read-only file system
mknod: `md17-': Read-only file system
rm: cannot remove `md17-': Read-only file system
rm: cannot remove `md18-': Read-only file system
mknod: `md18-': Read-only file system
rm: cannot remove `md18-': Read-only file system
rm: cannot remove `md19-': Read-only file system
mknod: `md19-': Read-only file system
rm: cannot remove `md19-': Read-only file system
rm: cannot remove `md20-': Read-only file system
mknod: `md20-': Read-only file system
rm: cannot remove `md20-': Read-only file system
rm: cannot remove `md21-': Read-only file system
mknod: `md21-': Read-only file system
rm: cannot remove `md21-': Read-only file system
rm: cannot remove `md22-': Read-only file system
mknod: `md22-': Read-only file system
rm: cannot remove `md22-': Read-only file system
rm: cannot remove `md23-': Read-only file system
mknod: `md23-': Read-only file system
rm: cannot remove `md23-': Read-only file system
rm: cannot remove `md24-': Read-only file system
mknod: `md24-': Read-only file system
rm: cannot remove `md24-': Read-only file system
rm: cannot remove `md25-': Read-only file system
mknod: `md25-': Read-only file system
rm: cannot remove `md25-': Read-only file system
rm: cannot remove `md26-': Read-only file system
mknod: `md26-': Read-only file system
rm: cannot remove `md26-': Read-only file system
rm: cannot remove `md27-': Read-only file system
mknod: `md27-': Read-only file system
rm: cannot remove `md27-': Read-only file system
rm: cannot remove `md28-': Read-only file system
mknod: `md28-': Read-only file system
rm: cannot remove `md28-': Read-only file system
rm: cannot remove `md29-': Read-only file system
mknod: `md29-': Read-only file system
rm: cannot remove `md29-': Read-only file system
rm: cannot remove `md30-': Read-only file system
mknod: `md30-': Read-only file system
rm: cannot remove `md30-': Read-only file system
rm: cannot remove `md31-': Read-only file system
mknod: `md31-': Read-only file system
rm: cannot remove `md31-': Read-only file system
done.
 Removing any system startup links for /etc/init.d/mdadm-raid ...
update-initramfs: deferring update (trigger activated)
/etc/init.d/mdadm: 77: TERM: parameter not set
invoke-rc.d: initscript mdadm, action "start" failed.
dpkg: error processing mdadm (--configure):
 subprocess post-installation script returned error exit status 2


the same error appears if i try to install any package (the other packages install ok ). ubuntu8.10 32bit

---

### Post by LegendofTom on 2009-03-17
Try:
```
sudo apt-get clean
sudo apt-get update
```

---

### Post by yui789 on 2009-03-17
doesn't work, same error

---

