---
title: "Trash problems on OVH server...hard drive full"
date: 2008-10-08
forum: General Help
---

### Post by kelfa on 2008-10-08
Ubuntu w/gnome

Hey guys I know this has probably been beaten to death.  But I am using Utorrent and deleted the data w/.torrent inside of Utorr.

I also emptied the wastebasket  of all the files, but it still shows my drive as being almost full.  The folder where I save my stuff is empty so its not there or the wastebasket anymore.

Yet Utorrent still shows that I have no space left as does system manager.

Help for a complete ubuntu noob plz...
Thanks guys

---

### Post by tuxxy on 2008-10-08
Nothing in your user trash but how about roots trash?

Run the following command in terminal and wait for the output, it will give you location of trash dirs, or you could skip this step if you already know the locations.

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

Also df is accurate at displaying HD usage.

```
df
```

---

### Post by kelfa on 2008-10-08
Sorry for being so slow at this, my first stab at ubuntu.

How do I open a "terminal" to type those commands.

In my disk usage manager it shows 200gb used out of 250, but like I said I deleted everything in Utorrent and cleared wastebasket.  THere is also nothing in my deleted files folder.

---

