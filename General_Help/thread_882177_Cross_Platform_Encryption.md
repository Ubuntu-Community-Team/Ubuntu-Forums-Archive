---
title: "Cross Platform Encryption"
date: 2008-08-06
forum: General Help
---

### Post by malfist on 2008-08-06
I just bought another hard drive and I want to set it up to be encrypted, but I want windows and ubuntu to be able to access it.

Does anyone know how to do that?

---

### Post by tamoneya on 2008-08-06
Thats pretty easy to do with truecrypt: [http://www.truecrypt.org/](http://www.truecrypt.org/)

---

### Post by malfist on 2008-08-06
Is there a .deb or do I need to compile it from source?

---

### Post by tamoneya on 2008-08-06
its in the repos.```
sudo apt-get install truecrypt
```

---

### Post by malfist on 2008-08-06
nvm, there's a install script that has the deb.

---

### Post by am7146 on 2008-08-06
I also downloaded it and installed it from the .deb rather than apt-get.  It's important to make sure the versions match, or to do the encryption on the oldest version to make sure it works cross-machines.

I encrypted an entire USB drive on Windows and got a "broken pipe" problem on Linux.  I went the other way (encrypt on Linux and open under Windows) and it worked out.

I ended up reformatting it as FAT32 and putting a few 4gb truecrypt files on it rather than encrypting the whole drive.  This let me put a README.TXT with my contact info in the root and leave a little unencrypted space to move stuff around to friends and clients without truecrypt installed.  

Andy-

---

### Post by malfist on 2008-08-06
I've got my windows partition encypted in Truecrypt and my linux partition is encrypted with whatever the alt CD comes with and I just got a new harddrive for backup's and I want both OS's to be able to use it.

---

