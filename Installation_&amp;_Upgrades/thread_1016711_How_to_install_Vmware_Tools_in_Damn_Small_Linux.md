---
title: "How to install Vmware Tools in Damn Small Linux?"
date: 2008-12-20
forum: Installation &amp; Upgrades
---

### Post by imjscn on 2008-12-20
I installed Vmware Workstation on WinXP Host, and I have made a Damn Small Linux Virtual Machine. Now I need to install Vmware Tools- it's not in the MyDSL Repository.
When I click VM/Install Vmware Tools, it suggest me to mount the virtual CD, how to do that?
I do find the linux.iso file in the host, but how can I install it into the guest?

---

### Post by lemming465 on 2008-12-28
VM/Install Vmware tools doesn't do what you expect.  The net effect is only to assign the virtual CD-ROM drive to the linux.iso image file.  Probably it connects the CD-ROM drive too.  If not, go back to the VM menu and connect the CD.

Ok, so you have the vmware tools CD image connected to the live VM.  Now what?  Probably it didn't automount, so next you need to mount it.  Then you will find a TAR file on it; you have to unpack that.  Having unpacked it, there is an installer script you can run.  Afterwards you'll have to rerun the /usr/bin/vmware-tools-config.pl script each time you install a new kernel, as the vmware glue modules for the tools will have to be rebuilt for the new kernel.  So you are going to do something like this:```

sudo -i
mkdir -p /media/cd
mount -r -t iso9660 /dev/cdrom /media/cd
cd /
tar xf /media/cd/*.tar
cd vmw*
bash install*
```

---

