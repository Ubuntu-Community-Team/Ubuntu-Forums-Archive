---
title: "easy way to sync 2 computers?"
date: 2008-03-02
forum: Hardware &amp; Laptops
---

### Post by hessiess on 2008-03-02
is their any easy way to sync the data between my desktop and laptop so that everything is automatically backed up, and i don't haft to worry about copying files. the two computers must also be capable of being used while not connected, my laptop goes pritymuch everywhere I go. I would also like to be able to specify what is synced, eg i do not want the trash folders synced :) .

thay are both running 7.04 and the file system is almost identical. both computers have about 15 gig of data, excluding the OS, both have a separate home partition. 


also it would be handy if when i plugged in a memory stick the entire continence was dumped to a file on the comp.

---

### Post by mrsteveman1 on 2008-03-02
Rsync can sync specific folders or file sets between 2 network computers pretty well. I use it on my laptop to backup iTunes to the server here, and its been quite fast and reliable for me.

Getting the system to run scripts when you insert a memory stick is more complicated, Linux has deliberately avoided the sort of mess that comes with things like windows autorun, but I'm sure its possible, for instance with udev rules. Not something that would be easy to setup, i barely understand how udev rules work as it is :D

But yea, rsync can work well in that situation. I assume you only want to sync user data and not the entire OS (which is a bad idea anyway).

---

### Post by hessiess on 2008-03-02
thanks for the sugestion, il look in to it :)

the only reason why i want to automatically back up memory sticks is thay have a habit of becoming corrupted. would I haft to wright a script to do this? I'm not that good at programing.

yes, just files, not the whole OS

---

### Post by mrsteveman1 on 2008-03-02
Udev is definitely what you want in that case, as far as i know its the only way to get scripts to run when hardware changes etc.

I'll look around and see how to format the rule so that a script runs when the stick is inserted.

---

### Post by mrsteveman1 on 2008-03-02
OK heres what i did, I made a new file:

```
/etc/udev/rules.d/99-plugscript.rules
```

with the following contents:

```
KERNEL=="sdb", ACTION=="add", RUN+="/usr/bin/usbbackup.sh"
```

This runs the specified script whenever /dev/sdb appears, you can change it to match the device name of whatever your memory stick is called, SD cards are sometimes called mmcblk0 etc, i have never used a MS card so im not sure what they are called.

In the script i merely put in:

```
#!/bin/sh

echo "i worked" > /home/steve/confirm.txt
```

I made the script executable, then i restarted udev:

```
sudo /etc/init.d/udev restart
```

And plugged in the stick, when i checked /home/steve/confirm.txt i found the contents of the text i put in the script, meaning the functionality works, and anything you stick in that script will execute when the device appears in the device tree.

---

### Post by hessiess on 2008-04-29
So, I set the script to rsync the usb drive with /home/a/ALL/backup

contents of script.
```
rsync -avz /media/disk/ /home/a/ALL/backup
```

this only works when I run

```
sudo /etc/init.d/udev restart
```

with the drive conected. If I plug it in nothing happens

---

### Post by Whiffle on 2008-04-29
I've been using unison for a while now to keep my laptop and desktop in sync.  I don't have it setup to do it automatically, I just sync it whenever I feel like it.  It works pretty darn well so far.

[http://www.cis.upenn.edu/~bcpierce/unison/](http://www.cis.upenn.edu/~bcpierce/unison/)

---

### Post by hessiess on 2008-04-29
> **Whiffle said:**
> I've been using unison for a while now to keep my laptop and desktop in sync.  I don't have it setup to do it automatically, I just sync it whenever I feel like it.  It works pretty darn well so far.

[http://www.cis.upenn.edu/~bcpierce/unison/](http://www.cis.upenn.edu/~bcpierce/unison/)

can it Handel 2 way syncing? if I change and or create new files on both computers.

I am trying to avoid the current problem of having each computer with a copy of a file, and both of them contain reinvent but different work. becouse of this it is imposable to simply copy one file over anouther, the two haft to be merged manually.

---

### Post by Whiffle on 2008-04-29
Yep

---

### Post by hessiess on 2008-04-29
is SSH or sockets easer to set up? I know verry little about networking. I am running feisty on one computer and gusty on the outher, will i haft to compile it, or is the version in the gusty and feisty repo the same?

---

### Post by Whiffle on 2008-04-29
SSH is what I use, you just need sshd installed and running on each computer.  I'm not sure which versions are in each of the repos, but I think it will complain if they're different.

---

### Post by hessiess on 2008-04-29
managed to sync a test directory in both directions, but it took 15 min for 22 meg of data. at that rate it would take days to sync everything.

---

### Post by Whiffle on 2008-04-29
Thats really odd, I use it to sync my entire music collection and it isn't all that slow.  Hmm :/

---

### Post by hessiess on 2008-05-01
seems to be related to the wireless network, and an old 4 port ruter. moveing the laptop closer to the wireless ruter reduces the time from weeks to about 5 howers. still rarther slow for 16 gig of data.

---

