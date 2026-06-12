---
title: "[SOLVED] rsync backup question"
date: 2008-08-16
forum: General Help
---

### Post by aheckler on 2008-08-16
I have an external HDD that I use to store my backups. On it, I have a script that runs a few basic commands to do just that. This is the main line:

```
rsync -a --delete /home/adam /path/to/external/HDD
```

As you can see, I have rsync using the --delete flag, which I thought would delete files on the external drive that no longer exist in my home folder. However, I checked just now and this is not the case. There are some old files in there that were deleted from my home directory long ago.

Why is this? I thought --delete would take care of this, but maybe I'm not reading rsync's man page closely eneough?

---

### Post by pparks1 on 2008-08-16
Your syntax looks correct to me.  The --delete flag tells it to delete files from the destination that no longer exist on the source.

---

### Post by aheckler on 2008-08-16
> **pparks1 said:**
> The --delete flag tells it to delete files from the destination that no longer exist on the source.

... which would essentially create a mirror of my home folder, correct? But it doesn't seem to be working this way. Perhaps there is some conflict with the -a flag?

---

### Post by pparks1 on 2008-08-16
I'm logging into my Ubuntu box right now to do some testing.  I'll post back results in just a couple of minutes.

---

### Post by pparks1 on 2008-08-16
Here is what I did; and it worked exactly as I expected.

sudo mkdir /folder1
sudo mkdir /folder2
sudo cp etc/* /folder1/.

du -h --max-depth=1 /folder1   (showed 620k)

sudo rsync -a /folder1/ /folder2/  (showed 620k as expected)


sudo rm /folder1/*.conf
du -h --max-depth=1 /folder1 (showed 516k)

sudo rsync -a --delete /folder1/ /folder2/
du -h --max-depth=1 /folder 2 (showed 516k)

---

### Post by aheckler on 2008-08-16
Hmm, that is weird. Why is it different for me? 

Let me do some testing of my own here...

---

### Post by aheckler on 2008-08-16
Running the script in the terminal returns this line:

```
IO error encountered -- skipping file deletion
```

Which explains my problem. The relevant section of the rsync man page is:

> If the sending side detects any I/O errors, then the deletion of any files at the destination will be automatically disabled. This is to prevent temporary filesystem failures (such as NFS errors) on the sending side causing a massive deletion of files on the destination. You can override this with the --ignore-errors option. 

Inserting the --ignore-errors flag into the script gave me the result I was hoping for!

Thanks for the help!

---

### Post by pparks1 on 2008-08-17
Cool...thanks for posting back with what was going on.  It's nice to question syntax sometimes and do a quick bit of checking to see if things really work as you think they do.

---

