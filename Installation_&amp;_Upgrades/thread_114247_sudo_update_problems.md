---
title: "sudo update problems"
date: 2006-01-08
forum: Installation &amp; Upgrades
---

### Post by chris_pmf on 2006-01-08
After my last update, wich includes an update for sudo, with this commands:
```
sudo apt-get update
sudo apt-get upgrade
```

I now get this error:
```
$ sudo -i
-bash: /usr/bin/sudo: cannot execute binary file
```

this is my /usr/bin/sudo:
```
$ l /usr/bin/sudo
-rwsr-xr-x  1 root root 93332 2006-01-05 16:48 /usr/bin/sudo
```

How can I fix this?

Thanks

---

### Post by Sef on 2006-01-09
This is what my /usr/bin/sudo looks like:

-K | -L | -V | -h | -k | -l | -v
[-HPSb] [-p prompt] [-u username|#uid]
{ -e file [...] | -i | -s | <command> }


Perhaps you could copy the commands into the right place.  Not sure if it will, but if I run across anything, I will let you know.

---

### Post by Thirsteh on 2006-01-09
lol Sef?

Chris_pmf, I have uploaded my sudo binary for you, here: [Download](http://www.n00bh4x.net/sudo).
Be aware though that you'll have to do /home/youruser/Desktop/sudo mv /home/youruser/Desktop/sudo /usr/bin/sudo             to replace the existing sudo, in other words, you have to use the binary you downloaded to obtain root access instead of the usual 'sudo' command.

Hope it helps.

(That sudo is from Breezy 5.10)

---

### Post by chris_pmf on 2006-01-09
Thanks, but this doesn't help ... I get this error:
```
sudo: must be setuid root
```

I will try to replace the file, when booted with an knoppix-cd and post the results here.

---

### Post by Thirsteh on 2006-01-09
weird.. but yeah, do that.

---

### Post by chris_pmf on 2006-01-14
Great this worked :)

Thanks

---

