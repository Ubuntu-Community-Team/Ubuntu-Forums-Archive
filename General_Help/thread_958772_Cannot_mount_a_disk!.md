---
title: "Cannot mount a disk!"
date: 2008-10-25
forum: General Help
---

### Post by linuxisevolution on 2008-10-25
I have a disk in my server that I would like to mount on a bunch of pcs that run Ubuntu. The server is Debian 4. I am using ssh. I know ssh is working because if I type top it gives me the servers specs. I have nfs file sharing working fine ( I can write and view the server's home directory, so thats where I would like to mount the cdrom ). The server is headless, so I do everything via ssh. I have tried this:

> mount -t iso9660 /dev/cdrom /home/guest/CDROM


and I get this:

> mount: block device /dev/cdrom is write-protected, mounting read-only


But, when I look at /home/winrid/server/CDROM , The cd contents are not there. I know that /home/winrid/server/CDROM and /home/guest/CDROM are the same folders because if I create that folder on the server, it shows up on my desktop. Any ideas? Thanks.

---

### Post by ddrichardson on 2008-10-25
I dont follow why they are the same folder - what if you mount it to the /home/winrid/server/CDROM?

---

### Post by linuxisevolution on 2008-10-25
> **ddrichardson said:**
> I dont follow why they are the same folder - what if you mount it to the /home/winrid/server/CDROM?

That is what I'm trying to do. How do I do it? :lolflag:

---

### Post by ddrichardson on 2008-10-25
The command you issued is mounting to a folder called /home/guest/CDROM not /home/winrid/server/CDROM, I didn't follow your logic about the folders being the same.

---

### Post by linuxisevolution on 2008-10-25
> **ddrichardson said:**
> The command you issued is mounting to a folder called /home/guest/CDROM not /home/winrid/server/CDROM, I didn't follow your logic about the folders being the same.

/home/guest/ is on the server. /home/winrid/server is where /home/guest is mounted, so the files in /home/guest appear in /home/winrid/server. So, if I create a /home/guest/CDROM on the server, I can view its contents in /home/winrid/server/CDROM. So, mounting it to /home/guest/CDROM would allow me to view the file contents in /home/winrid/server/CDROM. But the file contents are not there. If I put a file in /home/guest/CDROM I can view the exact same file in /home/winrid/server/CDROM. So, it must be something wrong with mount. So the question is: WHATS THE COMMAND I NEED?

---

### Post by ddrichardson on 2008-10-25
There is no need to shout.

The mount command is working, if it failed to mount it would have returned a failure which it isn't. I think the problem is because you are mounting a block device onto a device that is already mounted locally - if you mount on the server to, say /mnt/cdrom - does ls in that folder return the contents?

---

### Post by linuxisevolution on 2008-10-25
> **ddrichardson said:**
> There is no need to shout.

The mount command is working, if it failed to mount it would have returned a failure which it isn't. I think the problem is because you are mounting a block device onto a device that is already mounted locally - if you mount on the server to, say /mnt/cdrom - does ls in that folder return the contents?

Thanks. I'll try that. But, will I still be able to mount the mounted folder onto nfs? How do I view the cdrom's contents over the network?

---

### Post by linuxisevolution on 2008-10-25
> **ddrichardson said:**
> There is no need to shout.

The mount command is working, if it failed to mount it would have returned a failure which it isn't. I think the problem is because you are mounting a block device onto a device that is already mounted locally - if you mount on the server to, say /mnt/cdrom - does ls in that folder return the contents?

OK. I tried it, and when I ls /mnt/cdrom it works! But, how do I share this mounted directory? 

EDIT: ln /home/guest/CDROM /mnt/cdrom give me: > ln: `/home/guest/CDROM': hard link not allowed for directory
 So.. Am I screwed? lol

---

### Post by ddrichardson on 2008-10-25
The CDROM would need to be a NFS share itself, I would have thought. Use ssh to ls the required folder.

---

### Post by linuxisevolution on 2008-10-25
> **ddrichardson said:**
> The CDROM would need to be a NFS share itself, I would have thought. Use ssh to ls the required folder.

What do you mean "use ssh to ls the required folder"? I added the /mnt/cdrom to /etc/exports but I get > mount.nfs: access denied by server while mounting 192.168.1.125:/mnt/cdrom


Here is my /etc/exports:

> /home/guest 192.168.1.1/24(rw,no_root_squash,async)
/mnt/cdrom      192.168.1.1/24(rw,no_root_squash,async)


What is the exact command, I don't understand [I]your[I] logic now :)

---

### Post by linuxisevolution on 2008-10-25
> **ddrichardson said:**
> The CDROM would need to be a NFS share itself, I would have thought. Use ssh to ls the required folder.

I GOT IT TO WORK!!! ( this time, i have a good reason to yell ). I used sshfs. For other people, I used this command on the server:

> mount -t iso9660 /dev/hdc /mnt/cdrom


And then on my desktop:

> sshfs guest@192.168.1.125:/mnt/cdrom /home/winrid/networkdisk


It works. It's awesome. Now, I can install my software on more than one pc at once. This will make my job easier. I just take my lappy to work, setup sshfs on my laptop, and presto! Thanks for your help.

---

### Post by ddrichardson on 2008-10-26
Glad it worked - in other words for anyone else, you mounted the device on the server to the server's filesystem. Then mounted that folder as a network share.

---

