---
title: "Viewing Battery Information"
date: 2008-08-20
forum: General Help
---

### Post by abross on 2008-08-20
Hi.  I'm relatively new to Linux.  I was wondering what it is that I type into the terminal to view battery information kind of like this:

[IMG]http://ubuntu.files.wordpress.com/2007/04/battery-stats.png[/IMG]

I've already tried typing in what was typed in in the image but that didn't work.  Thanks

Ari

---

### Post by mb_webguy on 2008-08-20
```
cd  /proc/acpi/battery/
ls -lsa
```
If there is an "info" file here, then "cat info" will give you the information.  If you see a directory (for example I have a directory called BAT0), then cd to that directory, and look for the info file.

---

### Post by abross on 2008-08-20
Thanks for getting back to me so soon.  Here is what I got

```
abross@abross-laptop:~$ cd /proc/acpi/battery
abross@abross-laptop:/proc/acpi/battery$ ls -lsa
total 0
0 dr-xr-xr-x  3 root root 0 2008-08-20 22:10 .
0 dr-xr-xr-x 11 root root 0 2008-08-20 20:58 ..
0 dr-xr-xr-x  2 root root 0 2008-08-20 22:10 CMB0
abross@abross-laptop:/proc/acpi/battery$ 

```

---

### Post by abross on 2008-08-21
What do I do now?*

---

### Post by mb_webguy on 2008-08-21
Type "cd CMB0" to change to the CMB0 directory, then "ls -lsa" to view the contents of the directory.  I'm sure the info file you're looking for will be there, so type "cat info" to view the contents.

---

### Post by abross on 2008-08-21
Thanks.  It worked.  But instead of cat info, I had to use cat state.

---

