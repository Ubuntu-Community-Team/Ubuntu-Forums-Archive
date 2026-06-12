---
title: "stupid tar question"
date: 2008-07-14
forum: General Help
---

### Post by vortmax on 2008-07-14
I have a ftp archive script written in php.  It logs into the server, downloads files to a designated directory (for that server), does some voodoo, then tar's them.

The script is being run from a different directory then the download directory, but with php, I can't cd into the download directory to run tar.

I can work around this by specifying path names in the tar call:

tar -cf $path/$archive_name.tar $path/SMSACT.DB $path/DHCPD.CON

but this produces a tar file with the entire directory structure leading up to the files.  I just want the two files (the dir structure is unneeded).

Is there a simple way to tell tar to ignore the directory structure and just tar the files?

I tried the -C option to no avail.

---

### Post by ibuclaw on 2008-07-14
When you say that you've tried the -C option, do you mean that you've done:
```
tar -cf $archive_name.tar SMSACT.DB DHCPD.CON -C $path
```?

Regards
Iain

---

### Post by bodhi.zazen on 2008-07-14
As far as I know you either need to cd into the directory , then make an archive.

You can remove the path at the time of extraction with --strip-components N

where N is the number to skip

For example :

tar --strip-components 2 -xvf archive.tar

will strip the first two directories when extracting.

---

### Post by vortmax on 2008-07-14
> **tinivole said:**
> When you say that you've tried the -C option, do you mean that you've done:
```
tar -cf $archive_name.tar SMSACT.DB DHCPD.CON -C $path
```?

Regards
Iain

yep, that's the exact syntax I used and it didn't work.

I did manage to get it to work like this:

```

cd $path;tar --remove-files -cf $archive_name.tar SMSACT.DB DHCPD.CON

```

but that seems kind of like a hack of a solution to me.

I can't change into the dir in a separate command for some reason.  I'm guessing it's a limitation with PHP, as I tried it with wide open permissions and it still failed.

---

### Post by ibuclaw on 2008-07-14
> **vortmax said:**
> I can't cd into the download directory to run tar.

Ah! The download directory needs its permissions/ownership changing then.

```
chmod +r $path
```
If you don't own it, then root powers may be needed.
```
sudo chmod +r $path
```

Regards
Iain

---

### Post by vortmax on 2008-07-14
> **tinivole said:**
> Ah! The download directory needs its permissions/ownership changing then.

```
chmod +r $path
```
If you don't own it, then root powers may be needed.
```
sudo chmod +r $path
```

Regards
Iain

I can cd into it if I concat the commands, but:

```

<?php

system("cd $path");
system("tar --remove-files -cf $archive_name.tar SMSACT.DB DHCPD.CON") ;
?>

```

does not work.  If I do

```

<?php

system("cd /home/test");
echo system("pwd");
?>

```

or


```

<?php

`cd /home/test`;
echo `pwd`;
?>

```

where /home/test has global wrx permissions, the parent dir that the script is located in is echo'd, not the /home/test dir.  I have also tried giving the DIR's and files I'm working with global wrx permissions as made sure the user running the script owned the files and dir's.

I think php might open a new shell for each system command or back tick operation, so the next command has no access to shell variables set by an earlier one.

---

