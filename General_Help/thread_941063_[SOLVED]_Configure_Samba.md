---
title: "[SOLVED] Configure Samba"
date: 2008-10-07
forum: General Help
---

### Post by dathanalley on 2008-10-07
Hello all,

I have a little problem.  I created an FTP Server using Linux Ubuntu Server6.0, and VSFTPD for work.  Basically I wanted our managers in other States to be able to rwx on their particular directories.  Then I wanted us here at our corporate office to have a mapped network drive on our machines.  Each of the managers has their own home folder (abc, def, geh) under our shared folder here at the office(aaa).  I set all the users (abc, def, geh & aaa) to have the same primary group (manager).  But when we create a folder in abc, def, or geh here at the office using aaa's login, it puts the file permissions as drwxr-x--x.  Can I use a Samba configuration to automatically set the file permissions as drwxrwx--x when we create a new folder using aaa's account?

Thanks in advance,
Ubuntu Noob

---

### Post by dathanalley on 2008-10-08
Does anyone know what I'm talking about?  Can anyone help me out?

---

### Post by dathanalley on 2008-10-08
Ok, after intense searching for 2 days, I found the answer in this link [http://www.mail-archive.com/ubuntu-au@lists.ubuntu.com/msg01440.html](http://www.mail-archive.com/ubuntu-au@lists.ubuntu.com/msg01440.html) 

I did the following:
In your smb.conf on a per-share basis, set the "create mask" and
> "directory mask" options as needed.  In your case, "create mask = 0666"
> and "directory mask = 0777" will ensure all files and directories are
> created with the correct permissions (again, I would hope you
> investigate matching up your user accounts instead, and set these to
> 0640 and 0750 respectively).

Thanks again

---

