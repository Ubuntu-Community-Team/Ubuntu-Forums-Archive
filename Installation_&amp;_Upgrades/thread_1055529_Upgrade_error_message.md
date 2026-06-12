---
title: "Upgrade error message"
date: 2009-01-30
forum: Installation &amp; Upgrades
---

### Post by bluesalt on 2009-01-30
I've installed Ubuntu8.10 but I got this error message when upgrading

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF

I googled this in the Ubuntu forums and found that it's a KDE thing?
What do I do?

Also, when I check for updates I get the message that some packages are dangerous as they are not authenticated but they are listed as recommended. Should I still download them? 

Thanks

---

### Post by trot2millah on 2009-01-30
I as well am having this problem, and in the terminal it suggests to run "apt-get updgrade," but that's what I was doing in the first place, and it does not fix the problem.

---

### Post by sisco311 on 2009-01-30
> **bluesalt said:**
> I've installed Ubuntu8.10 but I got this error message when upgrading

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217**247D1CFF**

I googled this in the Ubuntu forums and found that it's a KDE thing?
What do I do?

Also, when I check for updates I get the message that some packages are dangerous as they are not authenticated but they are listed as recommended. Should I still download them? 

Thanks
In a terminal:
```
gpg --keyserver keyserver.ubuntu.com --recv **247d1cff**
```
```
gpg --export --armor **247d1cff** | sudo apt-key add -
```
and
```
sudo apt-get update
```

> **trot2millah said:**
> I as well am having this problem, and in the terminal it suggests to run "apt-get updgrade," but that's what I was doing in the first place, and it does not fix the problem.
Run the above commands. Replace the **bold** text (if is required).

---

### Post by trot2millah on 2009-01-30
When I run the first command, I get this error message back:
```
chris@ubuntu:~$ sudo gpg --keyserver keyserver.ubuntu.com --recv 247d1cff
gpg: WARNING: unsafe ownership on configuration file `/home/chris/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error
chris@ubuntu:~$ 

```

---

### Post by sisco311 on 2009-01-30
> **trot2millah said:**
> When I run the first command, I get this error message back:
```
chris@ubuntu:~$ sudo gpg --keyserver keyserver.ubuntu.com --recv 247d1cff
gpg: WARNING: unsafe ownership on configuration file `/home/chris/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error
chris@ubuntu:~$ 

```

Okay. Download launchpad-update-final.zip from [http://ubuntuforums.org/showpost.php?p=6638010&postcount=42]("http://ubuntuforums.org/showpost.php?p=6638010&postcount=42"). Extract the archive in your home directory and run it:
```
sudo ~/launchpad-update intrepid
```
Replace intrepid with hardy if you are using 8.04.

---

### Post by bluesalt on 2009-02-03
Thank you very much for your help

---

