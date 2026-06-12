---
title: "USB Drive storage"
date: 2013-03-09
forum: Hardware
---

### Post by Jonathan Andrew Upton on 2013-03-09
My USB drive used to have content on it, but I recently wiped it clean and it is now empty. Although it is completely empty, the Properties state that out of 1GB, 780MB still remains. I have tried clearing the recycling bin; I have addd content on and deleted but no luck. Any ideas?

---

### Post by agillator on 2013-03-09
Try getting a directory listing that includes hidden files and directories (ls -a). You should find a .Trash directory (perhaps named .Trash-1000). If you look in there you will see the files you have deleted. They have not really gone away. You can delete that directory or its two subdirectories and that will actually and finally delete the files and then you will see the full space available again. If you delete the .Trash directory the system will recreate an empty one.

---

### Post by ibjsb4 on 2013-03-09
If that doesn't work, you could install "gparted" on your main drive and wipe it.

[http://www.dedoimedo.com/computers/gparted.html#mozTocId309606](http://www.dedoimedo.com/computers/gparted.html#mozTocId309606)

Its in the software center or in terminal:

```
sudo apt-get install gparted
```

---

### Post by Jonathan Andrew Upton on 2013-03-11
Thanks, people. I just reformatted the USB drive and it is all fine. :-)

---

### Post by ibjsb4 on 2013-03-11
Congrads :) 

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

