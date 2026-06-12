---
title: "howto backup entire folder into a zip"
date: 2008-07-25
forum: General Help
---

### Post by adhg on 2008-07-25
I have a folder and wish to backit up, for this I do:

cp -r /home/adriana/Desktop/myFolder /home/adriana/Desktop/dest

this works great but I wonder how can I backup all 'myFolder' to a zip file?

thank you! 

* I ssh to a remote machine and wish to zip it and 'transfer' it to my local computer (the one I'm sshing from). If there's a winning solution to do all this in one go...wow!!!

---

### Post by GreenN00b on 2008-07-25
Try this:
```
tar cfz <archive_name>.tar.gz <foldername>
```

---

### Post by adhg on 2008-07-25
no :-(

---

### Post by GreenN00b on 2008-07-25
You can also use file manager (Nautilus) to connect to that server with ssh by selecting File\Connect to server option. This way may be easier to perform file management tasks ...

Please note that if you archive from nautilus on a remote ssh server the files will be downloaded locally, archived and then uploaded back as far as I know

---

### Post by geirha on 2008-07-25
This should log into your remote-host, compress the folder, and store it as local-backup.tar.gz on your local machine
```

ssh adriana@remote-host "tar zcf - Desktop/myFolder" > local-backup.tar.gz

# This will list the contents of the archive
tar ztf local-backup.tar.gz

```

alternatively you can copy the folder recursively with scp first, then compress it locally:
```
scp -r adriana@remote-host:Desktop/myFolder ~/destination/myFolder
```

---

### Post by silkstone on 2008-07-25
Try...

tar cvpzf /home/adriana/Desktop/backup.tgz /home/adriana/Desktop/myFolder

That will save the backup.tgz file in Desktop, but obviously you can change that. Don't save it to myFolder or it may try to backup itself!

Or if you do want it there, use tar cvpzf /home/adriana/Desktop/backup.tgz --exclude=/home/adriana/Desktop/myFolder/backup.tgz /home/adriana/Desktop/myFolder

---

### Post by RuleMaker on 2008-07-25
Try to use PuTTY, it's the graphical interface for ssh, i didn't tried this.

> PuTTY is a popular graphical SSH client. Although the Windows client is more widely known, you can get the Linux version by installing the putty package from the Universe repository.

See the windows section for further information about PuTTY. 

---

