---
title: "[SOLVED] Linux /windows sharing"
date: 2008-08-08
forum: General Help
---

### Post by sulekha on 2008-08-08
Hi,

 in my office there are some windows machines and the rest are all ubuntu 8.04  machines. now my question is how to access the data in Linux machines from windows machines without using samba

---

### Post by LitusMayol on 2008-08-08
Good question...

There's any way?

---

### Post by jocko on 2008-08-08
Without samba?
Set up ftp servers or something similar?
There's also something called "[Windows services for Unix (SFU)]("http://technet.microsoft.com/en-us/interopmigration/bb380242.aspx")" available from microsoft, which enables windows to use nfs, but using samba to connect to a windows share from a linux computer is probably a lot easier than using SFU to connect to an nfs share from a windows computer...

---

### Post by ilrudie on 2008-08-08
> **jocko said:**
> Without samba?
Set up ftp servers or something similar?
There's also something called "[Windows services for Unix (SFU)]("http://technet.microsoft.com/en-us/interopmigration/bb380242.aspx")" available from microsoft, which enables windows to use nfs, but using samba to connect to a windows share from a linux computer is probably a lot easier than using SFU to connect to an nfs share from a windows computer...

FTP is insecure.  If you setup an ssh server on your Linux machines windows users can use winscp to get at the files.  They will need an account on the Linux box and the account will need read access to the files (probably through a group).

---

### Post by nazish on 2008-08-08
> **ilrudie said:**
> FTP is insecure.  If you setup an ssh server on your Linux machines windows users can use winscp to get at the files.  They will need an account on the Linux box and the account will need read access to the files (probably through a group).

this seems to be a very reliable solution if you are very sure you dont want to use SAMBA

---

### Post by Sycron on 2008-08-08
I recommend Samba, for me it worked fine. And it is not so difficult to install. You can ask me what problems do you have when install it and i'll help you..

---

### Post by ilrudie on 2008-08-08
> **nazish said:**
> this seems to be a very reliable solution if you are very sure you dont want to use SAMBA

Its how we do it in a 200+ server Unix shop because it works and its secure.  We could use SAMBA but we don't.  We could use FTP but we don't.

---

### Post by sulekha on 2008-08-08
> **nazish said:**
> this seems to be a very reliable solution if you are very sure you dont want to use SAMBA


we checked sshfs, it is working well for sharing data b/w Linux machines. what about windows ..?? will installing cygwin on windows machines and starting ssh service on them, then using sshfs  solve the issue ?

---

### Post by ilrudie on 2008-08-08
> **sulekha said:**
> we checked sshfs, it is working well for sharing data b/w Linux machines. what about windows ..?? will installing cygwin on windows machines and starting ssh service on them, then using sshfs  solve the issue ?

Do you mean sharing between windows machines and other windows machines?  If you mean between windows machines and linux machines use winSCP.  If you mean between windows and windows SAMBA is what you get.

---

### Post by change_mode on 2008-08-08
What makes FTP insecure?

---

### Post by ilrudie on 2008-08-08
> **change_mode said:**
> What makes FTP insecure?

[http://en.wikipedia.org/wiki/File_Transfer_Protocol#Security_problems](http://en.wikipedia.org/wiki/File_Transfer_Protocol#Security_problems)

---

