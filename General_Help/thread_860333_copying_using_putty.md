---
title: "copying using putty?"
date: 2008-07-15
forum: General Help
---

### Post by gazz1982 on 2008-07-15
I am connecting to a linux server using putty from a windows pc, how can I copy a directory from the linux server to the windows pc is it along the lines of:

cp dir_name/ c:/directory_to_copy_file_to/

is it that simple. I dont want to test it just in case it mucks anything up as I'm copying from works server.

I also have an ubuntu pc if that is easier

Thanks

---

### Post by nloding on 2008-07-15
Go get WinSCP -- scp is the file transfer portion of it all.  Putty simply connects to a the shell.  Use WinSCP, connect with the same user/pass/hostname/port you would with Putty, and it looks just like a standard FTP program.

---

