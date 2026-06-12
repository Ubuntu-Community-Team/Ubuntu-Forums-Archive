---
title: "Lost disk space"
date: 2008-07-20
forum: General Help
---

### Post by spoketire on 2008-07-20
I recently deleted two 40GiB disk image files from a directory inside home/[myuser]/, but doing this didn't free up any disk space.  I did this after running gksudo nautilus, to allow myself to delete whatever I wanted.  Now it says I've used up 120GB, when I can only account for roughly 40GB.

The trashcan on the bottom right of my desktop shows nothing, and when I do gksudo nautilus again and click on Trash in the file browser, the window becomes gray and unresponsive.  I tried just letting it do its thing once, and  it just sat there for about 2 hours with no progress.  I had to force stop it, and the whole time, I could hear that my hard drive was busy (the sound didn't stop till I rebooted).

Maybe it just looks like I deleted the files, but they're still there.  I would appreciate any help.

---

### Post by Viper666 on 2008-07-20
edit: ops my mistake... didnt read quite well...

tried a reboot or a search for those files and see if they show up anywhere else?

---

### Post by coffeecat on 2008-07-20
Have a look in ~/.local/share/Trash/files. Also, have a look at [this thread]("http://ubuntuforums.org/showthread.php?t=856469"). The OP of that thread seems to have had the same problem as you.

**Edit:** By the way, in case you haven't come across the convention before, ~ = /home/yourusername.

---

### Post by hyper_ch on 2008-07-20
I guess you didn't press the shift key upon deletion and as you used gksudo nautilus you move them to the root trash. you need to empty that one.

---

### Post by MobiusNZ on 2008-07-20
You can find the largest files in your system by opening up a terminal and entering

```
find /home -type f -ls | sort -k 7 -r -n | head
```

Replace /home with whatever directory you want to search.

---

### Post by coffeecat on 2008-07-20
> **hyper_ch said:**
> I guess you didn't press the shift key upon deletion and as you used gksudo nautilus you move them to the root trash. you need to empty that one.

Good point. **spoketire**, have a look in /root/.local/share/Trash/files.

---

### Post by spoketire on 2008-07-21
The files showed up in /root/.local/share/Trash/files and I was able to delete them just fine.  Thanks everyone for the help!

I'm curious though, why did this process work so smoothly (and quickly), but my computer froze when I ran nautilus as root and clicked on the Trash link in the Places sidebar?

Edit: My root trash link still does this now.  Also, in /root/.local/share/Trash/files, I had everything selected before pressing Shift-Del, and it said the total size was 108GB.  When I got done deleting, it only freed up 61GB.  I guess I'm still missing at least 40GB!?

---

### Post by Potatoj316 on 2008-07-21
In the future if you want to analize what is using up disk space and dont want to use a terminal command.  (nothing against the terminal but for file size comparison I dont think its the best way, GUI can display better, in my oppinion) you can use disk upage analyzer, its in the accessories menu.

---

### Post by hyper_ch on 2008-07-21
> **Potatoj316 said:**
> In the future if you want to analize what is using up disk space and dont want to use a terminal command.  (nothing against the terminal but for file size comparison I dont think its the best way, GUI can display better, in my oppinion) you can use disk upage analyzer, its in the accessories menu.

not really
```

cd /
sudo du > output.txt

```

---

### Post by spoketire on 2008-07-21
I don't know if anyone saw the edit to my previous edit, since I accidentally added it after there were already replies, but now I have some more details anyway.

Disk Usage Analyzer says that / takes up 43 GB, but GParted says that I've used 53.67 GiB of my hard drive (which is the only mounted hard drive).  Why is there a discrepancy here?  Does it have to do with reserved space for the OS to run when the disk is full?

---

