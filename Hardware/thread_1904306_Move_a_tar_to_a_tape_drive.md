---
title: "Move a tar to a tape drive?"
date: 2012-01-04
forum: Hardware
---

### Post by acpuck1 on 2012-01-04
Sorry for posting what seems like it should be pretty straight forward. I couldn't find a solution and thought I would try here.

I am trying to backup and NFS share to a magnetic tape drive. However the tape drive does not hook directly into the NFS server, it is plugged into another server that has a SCSI port. I cannot simply tar -czf /dev/st0 the share from server hooked into the tape drive because of permissions.

What I have done is tar the share from the NFS server and copied it to the backup server with the tape drive. (This will all be done daily through scripting). Now, here is my problem, I need to copy the tarball onto the tape but I cannot find a command that will work. I tried straight up cp the_backup.tar.gz /dev/st0 and that does not work. I could get it to work if I extracted the tar to a directory and the compressed it again with tar -czf /dev/st0 /extracted_directory.

Any ideas of a command that will simply put an already compressed tar ball onto a magnetic tape drive?

---

### Post by dandnsmith on 2012-01-05
My rather distant recollections of using tape devices, both local and remote, suggest that the devices each have their own set of quirks and usable commands. You might be able to dd the tarball, but I rather expect that tar (or a package for the drive which uses a 'local' command) may be the only way to get the stuff to tape.
There might be some mileage in getting the share content via a pipe to the tar command, and thence to tape. I also seem to remember a remote version of tar (this might be what you tried, but I cannot remember the command, and don't have the documentation).

HTH

---

