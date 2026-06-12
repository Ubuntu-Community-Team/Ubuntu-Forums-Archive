---
title: "XAMPP Server"
date: 2008-08-12
forum: General Help
---

### Post by mikeMarek on 2008-08-12
Correct me if I'm wrong, as I'm not sure if this is the correct area to post this. It's PHP-related so I thought this might be the place.

Anyways, I've downloaded XAMPP Server for use of PHP without having an actual website (got Dreamweaver CS3 but formated Windows and won't install until I ge my lappy as I only have one more installation on the CD left; man I love Linux being free). Anywho, It won't install correctly. I'm using this directly off the site:
```
tar xvfz xampp-linux-1.6.7.tar.gz -C /opt
```
Here's what I get as an error:
```

michael@mint ~ $ cd ./Documents/Program\ Installers/
michael@mint ~/Documents/Program Installers $ su
Password: 
mint Program Installers # tar xvfz xampp-linux-1.6.7.tar.gz -C /opt
tar: /opt: Cannot chdir: No such file or directory
tar: Error is not recoverable: exiting now
mint Program Installers # 

```
Any idea what this is? I've tried creating a directory called "opt", but still the same errors. Many thanks for any help and/or replies,
-Mike

---

### Post by Bachstelze on 2008-08-12
That's weird, the /opt dir should be there... Oh well, I guess you can still re-create it ;)

```
sudo mkdir /opt
```

(Moved to General Help)

---

