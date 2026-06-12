---
title: "error kpkg configure a"
date: 2008-11-09
forum: General Help
---

### Post by sixsixseven9 on 2008-11-09
when ever i run update manager that says error please run "kpkg --configure -a" i run it in terminal and it asks for my password and then it says command not found . after enter something similar to that it gives me a different error that says something about the directory /var/lib/dpkg/updates/0004. i go into the directory and the file 0004 just says #padding.

i also have not been able to install anything when i run anything that requires an install.. i havent even been able to install flash.

i need help

---

### Post by Rocket2DMn on 2008-11-09
The correct command is
```
sudo dpkg --configure -a
```
Then run
```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```
You should then be able to go install flash.

---

### Post by sixsixseven9 on 2008-11-09
ooh i see now that i have done that it brings up the error about ```
dpkg: parse error, in file `/var/lib/dpkg/updates/0004' near line 1:
 newline in field name `#padding'

```
spoke to soon... after i run ```
sudo apt-get update 
``` it brings up this
```
W: GPG error: http://packages.medibuntu.org intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

```
again it goes back to ```
dpkg --configure -a
```

---

### Post by Rocket2DMn on 2008-11-09
I don't know what that file is, but I don't think it's supposed to be there (appears to be a file fragment).  Let's delete it.  Please be careful to run this command exactly as I type it (use copy and paste):
```
sudo rm /var/lib/dpkg/updates/0004
```
Then proceed normally.

---

### Post by sixsixseven9 on 2008-11-09
yes yes the file is gone now im guessing it should work now right?

oh but i answer that question myself and it repeats the thing about dpkg --configure -a 
i run i and then it says i need superuser privilege

---

### Post by Rocket2DMn on 2008-11-09
Yup!  Post back if you have further problems!

---

### Post by adult swim on 2008-11-09
youve got to run ```
sudo dpkg --configure -a
```

---

### Post by sixsixseven9 on 2008-11-09
oh im getting somewhere now... now after running ```
sudo dpkg --configure -a
```(i am aware that you need to run sudo for the commands but sometimes i forger0 i then continue to run ```
sudo apt-get update 
``` and at the end it then says i my want to run ```
apt-get update
``` but i just did....

wait i might have just fixed it but i must wait... i decided to run

```
sudo apt-get upgrade
```

and it has been working fine until it stoped at 

```
ldconfig deferred processing now taking place

```

it is telling me to restart 
i will restart now and report back....

everything seems to be in working order....

---

### Post by Rocket2DMn on 2008-11-09
Awesome.  Make a new post in the thread if the problem persists instead of updating your last post, otherwise we won't know that the thread has changed.  Cheers.

---

### Post by sixsixseven9 on 2008-11-09
ok i will make sure to....

---

