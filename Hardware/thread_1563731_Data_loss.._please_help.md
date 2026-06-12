---
title: "Data loss.. please help"
date: 2010-08-29
forum: Hardware
---

### Post by dpacmittal on 2010-08-29
I have a bash script which I wrote to automate backups. It used rsync to backup directories of my choice. But today my external harddrive got mounted on a different folder under /media/. This caused the backup script to make newfolder under /media and copied all the data to this new folder which was in fact on the same partition as root.

Now the root partitions free space came down to zero due to this. However, I never notices all these things. I thought that the backup had went normally. I suspended the computer and after some time I resumed but my desktop didn't show. I restarted but the desktop never came. So I pressed Ctrl+Alt+f1,  checked what the issue was and after finding out about root being full, I uninstalled openoffice. But still root drive was showing 0bytes of free space. I still couldn't get to the desktop.

So I booted using live cd and transferred few files to another partition freeing up few GBs. After restarting the whole partition went corrupt. Grub showed the grub rescue prompt. I again booted into live CD. Checked gparted and it showed the partition as 'unknown'. I tried e2fsck without any switches. It showed thousands of multiply-claimed blocks.

However, they were never ending. So I cancelled it and tried TestDisk and Photorec. They managed to recover few GB of data but it was completely unorganised and finding a file would take ages amongst 150k recovered files. They are as good as useless.

Using testdisk, I found alternate superblock and used that superblock with e2fsck. This time the errors were less and it finished rather quickly. The disk was mountable again but it only had one folder - "Lost+Found".

I was happy to see the folder thinking all the files would be inside that but the folder never opened.

ls gives a segmentation fault in that folder. In terminal, typing cd <tab> gives me 10035 folders with naming as #number. So I had folders #1 to #10035 in lost+found folder but unfortunately I can't change the directory to those folders.

Now I am stuck with all the data loss (except for the data that photorec managed to recover which is as useless as the partition itself since even the filenames are messed up).

I want to know any possible solution to this horrific problem :(

---

### Post by gzarkadas on 2010-08-29
lost+found is readable only by root. You can either open a terminal and type `sudo -i' to enter an interactive root login (in your case this is necessary, since you will have to navigate the numerous folders in lost+found and try to recover your data) and then use `cd', `ls' and `cp' to copy stuff; or issue `gksudo nautilus' to open a root nautilus window and then switch to lost+found, if you prefer the GUI way.

Now, since you have run e2fsck, there is nothing left to do than to try and recover as much as you can from those directories in lost+ found. To ease this, use your older backups to recover as much of your files as you can and then search in lost+found for those that you have modified after your last backup.

For the future:

A. When you run out of space the first thing to try is to empty your trash and then reboot in recovery mode and start moving away stuff: 
1. Mount an external disk
2. First find what have filled your disk / partition and try to delete it or move it to the external disk if you want to keep it
3. Clean your /tmp to get some space (if it is in the same partition as the one that filled up).
4. Move to external disk, all old logs from /var/log (those with .gz at the end or with .1)
5. Check your free space with `df' and if it is adequate reboot in normal mode, or -if not- go to step 6
6. If you desperately need more space, move (don't delete) to external disk one, two or all of these entire trees: /usr/include, /usr/src and /usr/share/doc. Alternatively fire-up `aptitude' and remove some packages (but keep their configuration).

B. Use gparted to enter a label to your backup disk, so that it always mount at the same folder. Also modify your backup script to check the existence of the external drive before attempting to rsync.

---

### Post by gzarkadas on 2010-08-29
An amendment: don't try to recover anything, just your data files (those under /home) and your configuration (the files that you have changed under /etc). And perhaps anything useful that cannot be recovered easily in another way under /usr/local (if you have put anything there). 

For the rest of the system, it will probably be easier just to reinstall. If you can find the file /var/lib/dpkg/status (or the file that had this name before e2fsck was run), you can extract your installed packages names with the following command into a file (change [file] to whatever you like):
```

cat /var/lib/dpkg/status | grep -A 1 'Package:' | awk 'BEGIN{RS="--\n";FS="\n";ORS="\n";OFS=" "};{ if($2~/install ok installed/ || $2~/Essential: yes/) print substr($1,10,length($1)) }' > [file]

```Then, after reinstalling the system, you can reinstall all your packages with:
```

sudo apt-get install $(cat [file])

```Afterwards, plug in everything you have managed to recover from /etc and fill up what has been left missing to get your system as it used to be.

---

### Post by dpacmittal on 2010-08-29
Thanks for the reply. That was much appreciated.

I dropped to root (sudo su)  and used ls but it gave the same segmentation fault error. However I was able to copy all the files from the Lost+found folder to another partition using the following command:
```

find ./ -type f -exec cp \{\} /media/disk2/recovery/ \;

```

The data size was around 40GB which is pretty much everything I need. I mean all my files seem to be safe. However, the folder structure is gone. Is there anyway I can get my folder structure back using lost+found folder or any other means?

Thanks for all the help.

---

### Post by gzarkadas on 2010-08-30
You can try to get a partial directory structure by running 
```

cd /lost+found
tree -fid -o [largefile]

```
(if you omit the d switch it will also print files, but the output will be much more voluminous). The output file ([largefile]) could then subsequently be used to script the creation of a directory tree, and even put the files back in their locations (you 'll need to omit d for this).

However, it would require 10035 manual edits, because each top level directory in lost+found is a directory that got out of the original tree. The effort needed for this hardly justifies to pursue such an objective. It could be useful only for large tree fragments with lots of files; anything else is better to be done by hand.

---

