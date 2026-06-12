---
title: "Creating backups with limited diskspace"
date: 2008-11-17
forum: General Help
---

### Post by eludlow on 2008-11-17
I have SSH access to a server which I wish to create nightly back up of my www directory on.

The way I'd planned to do this is create a script which SSHs onto the server, creates the backup, FTPs it onto my backup server and then finally deletes the backup file.

However, creating the backup file busts my disk quota and so it doesn't actually get created.

How would people get around this?  Is there a way to create a sort of SSH "map" and then create the file directly on the backup server?

Thanks in advance,
Ed Ludlow

---

### Post by hyper_ch on 2008-11-17
where does it bust?

---

### Post by vanadium on 2008-11-17
You can mount your server with sshfs on the backup server. Then you can directly create the archive on the backup server, reading the locally mounted files.

---

### Post by eludlow on 2008-11-17
Thanks vanadium - playing with sshfs now, think it will do what I'm after.

Ed

---

### Post by hyper_ch on 2008-11-17
easiest way would probably be rsync over ssh.

---

### Post by vanadium on 2008-11-18
This will not create a "backup file", where I understand something like a tar.gz archive. I agree with you, however, that making a "mirror" using ssh would be the easiest, and for subsequent updates for the backup also (by far) the fastest option. Only disadvantage I see is that the data are not stored compressed on the server, if that is an issue.

---

