---
title: "how create linux recovery?"
date: 2011-07-02
forum: Hardware
---

### Post by samaneh on 2011-07-02
Hello.
How can i create disk recovery from my linux in acer aspire 5742z?
please help me.

---

### Post by d3v1150m471c on 2011-07-02
i prefer to use tar, which is installed by default on ubuntu. if you go to my site below you can find a tool called apt-oops if you're looking for debian package backups

otherwise:
```

# create a backup
tar cvpzf backup.tar.gz --exclude=/media --exclude=/proc --exclude=/lost+found --exclude=/mnt --exclude=/sys --exclude=backup.tar.gz

``````

# restore from backup
sudo tar xvpfz backup.tar.gz -C /

```

please note this process can take a lot of time and it's best do this from a mounted usb that can hold enough compressed data. you can do similar things with the rar command if you want to use it and encrypt your backups.

---

