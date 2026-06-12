---
title: "Beginner: What is each folder in root for?"
date: 2008-12-01
forum: General Help
---

### Post by thenovices on 2008-12-01
Hi everyone,

I just recently installed Ubuntu, and I'm quite unfamiliar with the whole file system. I don't know what each folder in the root is for (bin, boot, dev, etc) and I don't know where I should be putting stuff. For example I just downloaded Eclipse, and I don't know where to put it.

If there is a website somewhere with this information, I'd appreciate it if someone would point me there.

Thanks in advance!

---

### Post by louieb on 2008-12-01
Ubuntu mostly follows the [Filesystem Hierarchy Standard]("http://www.pathname.com/fhs/pub/fhs-2.3.html") for UNIX. 
more here [Filesystem Hierarchy Standard - Wikipedia]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard")

---

### Post by linux_tech on 2008-12-01
The root folder is where everything starts, the root folder contains all other files and folders.

[http://ubuntu-tutorials.com/2006/12/20/explanation-of-the-ubuntu-linux-file-structure-ubuntu-all-versions/](http://ubuntu-tutorials.com/2006/12/20/explanation-of-the-ubuntu-linux-file-structure-ubuntu-all-versions/)

---

### Post by jakupl on 2008-12-01
In ubuntu you generally don't download programs from the www. Ubuntu uses repositories. Instead of downloading eclipse, just go to synaptic package manager and find eclipse, tab it and press the apply button. Or alternatively go to Applications --> Accessories --> Terminal, and write:

```
sudo apt-get install eclipse
```

You will find 99% of the programs you want in Synaptic Package Manager (System --> Administration --> Synaptic Package Manager).

Or use the more user friendly Add/Remove (Applications --> Add/Remove)
For more information, check this out [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by thenovices on 2008-12-01
> **jakupl said:**
> In ubuntu you generally don't download programs from the www. Ubuntu uses repositories. Instead of downloading eclipse, just go to synaptic package manager and find eclipse, tab it and press the apply button. Or alternatively go to Applications --> Accessories --> Terminal, and write:

```
sudo apt-get install eclipse
```

You will find 99% of the programs you want in Synaptic Package Manager (System --> Administration --> Synaptic Package Manager).

Or use the more user friendly Add/Remove (Applications --> Add/Remove)
For more information, check this out [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

thanks for the tip! I am aware of synaptic; eclipse is a self-contained application anyways, so you just download it and extract it.

Thanks to everybody else for the links!

---

