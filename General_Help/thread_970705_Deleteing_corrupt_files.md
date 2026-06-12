---
title: "Deleteing corrupt files"
date: 2008-11-04
forum: General Help
---

### Post by sudanto on 2008-11-04
I'm having trouble deleting or renaming a couple corrupted files on my web server.

If I SSH into the server and use **rm -f**, to delete or **mv**, to try and rename the file neither will work.

Does anyone have a suggestion?

These corrupted files are fouling up my FTP client from creating error-free scheduled backups to a local machine.

Thanks.

---

### Post by taurus on 2008-11-04
Do you get any error message when you try to either delete or rename those files?  Do you have permission to write to that directory?

---

### Post by sudanto on 2008-11-04
Thanks for asking.

I don't get any error messages when I try and delete the file. When I try to rename it, it says the file does not exist.

When I try and check the permissions

```
[clamato]$ ls -l Upasika\ Sumi\ and\ Kaz
```

it returns

```
ls: Upasika Sumi and Kaz: No such file or directory
```

thanks.

---

### Post by Wayne_V on 2008-11-04
try "ls -lb U*" and see if there are any imbedded special characters in the name.

---

### Post by sudanto on 2008-11-04
Thanks for the suggestion.

Another friend of mine introduced me to ```
rm -i*Sumi*
```
Which did the job!

I suspect there was a special character somewhere that was tripping me up. Perhaps a space at the end of the filename.

Cheers.

---

