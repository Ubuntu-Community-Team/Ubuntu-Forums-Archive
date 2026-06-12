---
title: "Attaching duplicate hard drive to Ubuntu machine"
date: 2015-04-30
forum: Hardware
---

### Post by craig37 on 2015-04-30
Hello,

Firstly I am very much a beginner when it comes to Ubuntu so this may either be asking the impossible or being rather silly but here goes...

We have a new infrastructure and we are currently building/migrating servers (mostly Ubuntu) onto that platform. I have been tasked with configuring and testing all the relevant backup scenarios. We are currently using VMWare Web client and NetApp VSC 5.0 and with version 5.0 they have removed the single file restore function. I am currently trying to perform a single file restore for an Ubuntu 12.04 machine and this is where I am encountering issues (not helped by my vague/limited Ubuntu knowledge).

I have read various articles whereby to perform a single file restore I need to mount the backup to a host, edit the settings of my Ubuntu VM, add an existing hard disk and then select the VMDK file from the mounted backup. All of which is straightforward enough. 

The problem is when I do this on my test machine I have 2 identical disks with the same UUID attached to the one machine and this seems to be causing the machine problems. My aim is to basically browse the additional disk so I can restore single files from it, if we are ever in that postion. I have read various articles describing similar issues but all with different solutions and so far I have hit a brick wall. I have managed to add the disk to a different Ubuntu machine (obviously different UUID) and then configure a mount point and browse the files that way. Ultimately we would prefer if we could attach the disk to the server which needs the file restore if this is possible.

So with that in mind, my question is 1) is it possible to add the same disk (from a different point in time) to the same machine and restore a single file from it? 2) if so, is possible to point me in the direction of how I make the changes on the system so this can happen.

It is also worth adding that ideally we would like to be able to do this without downtime or rebooting the server.

Any help would be greatly appreciated and let me know if more specific information is required.

The disks are being picked up as LVM2_member when I run the blkid command and have the same id.

---

### Post by TheFu on 2015-04-30
You can mount drives in different ways - not just by UUID.
* label
* path
* device
**man fstab** or  **man mount **have details.

Someone with limited Linux knowledge finding answers by web searching is like opening a complex mystery book and starting anew at chapter 35. Missing the background makes this very hard. Sadly, the only way I know to get it is by directed learning, time, experience and being around others who will mentor.

[http://blog.jdpfu.com/2014/12/28/learning-linux](http://blog.jdpfu.com/2014/12/28/learning-linux) has some links for learning.  There's a free PDF to become a "power user" and there are links to Ubuntu Server Guide.  Google will find these too.

From the other server, you could use NFS to mount it locally or just use sftp to browse.  ssh/scp/sftp are a way of life.

---

### Post by craig37 on 2015-04-30
Thanks for that, really appreciate the link and advice, I will definitely take a look at these.

I have managed to mount the restored drive on a different Ubuntu server using the mount command and that was fairly straightforward as this was a different server with a different disk so there were no conflicts with the UUID, LV name, VG group etc. My manager has advised though, that ideally (if it is possible) we want to perform the single file restore on the same machine by loading that restored drive on server it belonged to.

---

### Post by TheFu on 2015-04-30
Mount it by label, path or device name - not UUID. Might need to change the other mount (UUID) too. I dunno.

And to avoid umount, just use the **-o remount** option.

---

