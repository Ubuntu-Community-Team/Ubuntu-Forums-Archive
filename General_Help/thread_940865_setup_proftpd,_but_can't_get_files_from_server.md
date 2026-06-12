---
title: "setup proftpd, but can't get files from server?"
date: 2008-10-07
forum: General Help
---

### Post by AppleSeed666 on 2008-10-07
Hello there

K, so i've searched this forum and also followed the help on this forum but now i'm stuck. I am trying to setup an ftp server on my ubuntu desktop version 8.04.1 by installing proftpd. I followed the instructions here: [http://ubuntuforums.org/showthread.php?t=79588](http://ubuntuforums.org/showthread.php?t=79588). However, to get it to run i had to setup the proftpd.conf with the gui (by installing and running gproftpd). 

I setup a user in the gproftpd gui (let's call him jimUser). jimUser has two directories, one for uploading and one for downloading. I set this up in the gproftpd gui as well.

Now, i can connect to the proftp server and can upload files to jimUser's specified upload directory, but i cannot get any files from jimUser's specified download directory? If i make it so that jimUser can upload and download from a single directory, that works,... but is there no way to make it so that jimUser can upload to a specific directory and download from a specific directory?

Does anyone have any ideas?

---

### Post by AppleSeed666 on 2008-10-07
Okay i think i figured it out. 

What you can do (for this example) is have jimUser's home directory set to something like /home/FTP-shared and then within that folder you have and upload and download directory, so you have these 3 directories:

/home/FTP-shared
/home/FTP-shared/download
/home/FTP-shared/upload

so, if jimUser's home directory is set to /home/FTP-shared when he ftp's in he can then see the download and the upload directories and then move into them and upload and download. Of course, you'll have to all all 3 directories to jimUser's list of directories and set up the permissions on the directories.

All of this i had to do via the gui gproftpd

---

