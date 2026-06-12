---
title: "how to transfer file"
date: 2010-01-07
forum: Hardware
---

### Post by cz8 on 2010-01-07
Here is a technical problem i encountered lately.
After a incomplete upgrading, my ubuntu's x server was stuffed up somehow.
Every time I boot up my Ubuntu, it only takes me to the CLI.
I tried heaps of way to start the xserver, It just doesn't do the trick.
(Here are the things I have tried.
[http://ubuntuforums.org/showthread.php?t=1365213](http://ubuntuforums.org/showthread.php?t=1365213))

so I decided to reinstall my ubuntu.
But the thing is I installed my Ubuntu in my windows( yes, a particular drive in windows). Therefore, to reinstall it i have to uninstall first, which implies that I am gonna lost all the previously saved files on my ubuntu.

Anyone can give my some pointers on how to transfer those file back to my windows.
I had wanted to try something like
> cp -r LocationOfFilesToBeTransfered /media/<medianame/flashdrivename>but I can't find the media name in the /media folder.
(my flashdrive is absolutely fine, because when i tried it on another computers, and there was a KINGSTON media in the /media folder)

Thanks a lot in advance.

---

### Post by prshah on 2010-01-07
> **cz8 said:**
> 
Every time I boot up my Ubuntu, it only takes me to the CLI.

But the thing is I installed my Ubuntu in my windows( yes, a particular drive in windows). Therefore, to reinstall it i have to uninstall first, which implies that I am gonna lost all the previously saved files on my ubuntu.

Anyone can give my some pointers on how to transfer those file back to my windows.

Installing Ubuntu "within windows" is a wubi install. Boot into ubuntu (command line) and then you can copy your files to your Windows drive, which will be available at "/host". Other partitions will be available at "/media".

---

### Post by cz8 on 2010-01-07
It worked!Thanks a lot,prshah!
I just tried 
> cp -r LocationOfTheFolder/FolderToBeCopied /host
And then I went back to windows, and i found the folder i wanted to copy in the partition that i installed my ubuntu.

---

