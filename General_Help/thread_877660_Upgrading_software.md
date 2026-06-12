---
title: "Upgrading software"
date: 2008-08-02
forum: General Help
---

### Post by ubockto on 2008-08-02
How do i upgrade my boinc manager software using the terminal command? at the moment, there is nothing in the update manager that will update it

---

### Post by collinp on 2008-08-02
If there is nothing in the Update manager, that means that the version in the repos has not been updated yet.

---

### Post by ubockto on 2008-08-02
ok, but i have downloaded the .sh file, how do i use that to update the software then?:lolflag:

---

### Post by collinp on 2008-08-02
navigate to the directory where the .sh file is stored with "cd /path/to/sh/file", then run the .sh file with "./shfilename.sh". I would suggest you remove the existing client before doing that tho as it could cause a conflict between packages.

---

### Post by Landier on 2008-08-28
using sh is really simple : you can find kinda quick install guide here : [http://boinc.berkeley.edu/wiki/Installing_on_Linux](http://boinc.berkeley.edu/wiki/Installing_on_Linux)

just sh ...... .sh
then in boinc folder : ./run_client --daemon; ./run_manager

working on Ubuntu 8.04 - Hardy Heron

---

