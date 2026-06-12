---
title: "[SOLVED] where did hard drive space go?"
date: 2008-10-06
forum: General Help
---

### Post by stewacide on 2008-10-06
For some reason my drive is reporting 51GB of used space, but only 29GB of files? What gives?

There's nothing in my trash. And there are no other drives attached.

---

### Post by Meow27 on 2008-10-06
are you using vmware server or some other VM software? they somtimes clog up hard disk space

---

### Post by tuxxy on 2008-10-06
Nothing in your user trash but how about other users or roots trash?

Run the following command in terminal and wait for the output, it will give you location of trash dirs

```
sudo find / -type d -iname *Trash* | grep Trash
```

Then navigate to them using nautilus example to root trash is below

```
sudo nautilus /root/.local/share/Trash/
```

Also sometimes you may have trouble deleting files using nautilus, if so you could run this command but be sure you dont need anything in your trash! 

```
sudo rm -rf /root/.local/share/Trash/files

```

Also df is much better than disk analyzer for correct disk usage

```
df
```

---

### Post by stewacide on 2008-10-06
If I start nautilus with sudo and go to the root trash folder nautilus hangs and says it can't read the contents or something like that, so I assume that's the problem. Will try from the command line...

edit -- Awesome, 'sudo rm -rf /root/.local/share/Trash/files' did it! Thanx!

---

### Post by tuxxy on 2008-10-06
Glad it worked out you can mark the thread solved aswell now :)

---

