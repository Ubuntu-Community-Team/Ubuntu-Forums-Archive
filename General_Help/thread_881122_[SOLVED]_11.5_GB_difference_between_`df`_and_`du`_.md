---
title: "[SOLVED] 11.5 GB difference between `df` and `du` output"
date: 2008-08-05
forum: General Help
---

### Post by Felonious Punk on 2008-08-05
Was burning a disc the other day, and it came up with an 'out of tmp space' error. So I checked out the contents of my root filesystem, cleaned out some garbage that wasn't necessary, and df still said I only had 2.6 out of 18.3 GB of space available.
"Impossible!" I said to myself. :confused:
As you can see:

```
## df

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             18381960  14778256   2669928  85% /
/dev/sdb2             11172732    158888  10450768   2% /tmp
/dev/sdb5             40634444  14808044  23778520  39% /usr
/dev/sdb6             22353492   1569528  19657408   8% /home

```

18.3 GB total, 14.7 GB used, 2.6 GB available

/tmp, /usr, and /home are on separate partitions, so no chance of those filling root up.
Here's du:

```
## du -csxk /
3269144	/
3269144	total

```

3.2 GB used on root

Here's what /var takes up:

```
## du -csxk /var
1373656	/var
1373656	total

```

1.3 GB of root is /var.

What's taking up that 11.5 GB?
I've done a lot of web searching looking for some answers, but haven't found anything.
Can anyone help me?
I hope it's something incredibly stupid, that means it's easy to fix!
:KS
I just want my space back!

Thank you in advance for your help!
Stuart C. Bruce

---

### Post by russlar on 2008-08-05
try du -sh, you'll get results in GB and MB format. :)

---

### Post by jimv on 2008-08-05
sudo apt-get clean
sudo apt-get autoclean

---

### Post by kaivalagi on 2008-08-05
Did you run the du and df commands via sudo?, maybe something was created as root and you can't see it using a non-root user?

I found that trash from the root account was a cause for missing space on my drive previously...something similar here maybe?
 
Just a thought

---

### Post by Felonious Punk on 2008-08-05
Sorry, I should have put this in my first post, but I already tried cleaning up the packages and emptying the trash, both to no avail.
And yes, everything was run as root. Otherwise du gives you "Permission denied" errors in /var and some other places.
And
```
du -sh
```
just displays the output in a different format.

<sigh>

Thanks, though...

SCB

---

### Post by kaivalagi on 2008-08-05
The only other suggestion I can make is looking at it in more depth using a graphical too:

sudo apt-get install baobab

Then look for Accessories->Disk Usage Analyser

Sorry I can't be of more help, just can't think what it could be...

---

### Post by dcstar on 2008-08-06
> **Felonious Punk said:**
> 
.........
I hope it's something incredibly stupid, that means it's easy to fix!
:KS
I just want my space back!

Thank you in advance for your help!
Stuart C. Bruce

Running commands with User privileges will only show files that you have permission to read, use **sudo** if you want more meaningful results.

---

### Post by fyo on 2008-08-06
Ext3 reserves some space on your partition, default is 5%. This space is critical to mitigate the effects of fragmentation and also ensures that "root" processes don't crash immediately if a user fills up the disk (since the priveledged processes can use the reserved space, things like syslogd will continue to work for a while), which is quite helpful.

```
sudo tune2fs -l /dev/sda1 | grep Reserved
```

There's also a chance that your filesystem isn't taking up all the available space in the partition, although that should affect the shown (max) size in df as well. You can make the filesystem occupy the whole partition by running:

```
resize2fs /dev/sda1
```

If you are still experiencing problems, try giving us the full output of the tune2fs command above (without grep'ing for anything).

---

### Post by Felonious Punk on 2008-08-06
Congratulate me on my empty-head!
:lolflag:

Here's what happened...

Last week I moved /usr and /home into new partitions.
(Tried to move /var, but it didn't want to work. Tried creating /var/lock and /var/run on the mount point, but that's ok,
I have plenty of space on root)
Anyway, I forgot to empty out /usr on my root partition after copying everything in there to the new partition.
So, as soon as the separate /usr partition gets mounted during boot, all the stuff in there gets hidden from du,
but it still takes up the space as seen in df.
Delete /usr on root partition, create the mount point, my 11.5 GB is back where it should be.

Yay! :)

Thanks everyone for your ideas.

---

