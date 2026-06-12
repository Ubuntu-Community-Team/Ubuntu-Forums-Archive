---
title: "So I typoed rm *~"
date: 2008-08-31
forum: General Help
---

### Post by badp on 2008-08-31
I was coding some Python scripts and wanted to issue:

```
~/sh: rm *~
```

...to delete all of Gedit temporary files.

I actually typed:

```
~/sh: rm * ~
```






After one second I realized and unplugged the laptop in horror to avoid to lose the data for good.

Is my best option to get a live cd, apt-get install recover or e2undel and run it on the unmounted partition? Do they work on ext3 filesystems?

Or should I just give up?

---

### Post by Sycron on 2008-08-31
In my opinion , give up. I think you may still have acces to GNOME by login-in as root and typing ```
startx
```. Here you can recover things.

What did happen when you loged in after typing ```
rm * ~
``` ?

---

### Post by badp on 2008-08-31
It told me it couldn't delete a couple of folders.

I just read [http://linux.sys-con.com/node/117909](http://linux.sys-con.com/node/117909) which tells me that as long as those files were smaller than one block (like most config files or python scripts) I should be able to recover them relatively easily.

Maybe I'm overly hopeful.

---

### Post by Sycron on 2008-08-31
With that command you deleted your **home/your_user_name** files/folders.

---

### Post by badp on 2008-08-31
Wait, I misread your question. Sorry.

I didn't relogin. I'm using another computer now.

---

### Post by Sycron on 2008-08-31
> **badp said:**
> Wait, I misread your question. Sorry.

I didn't relogin. I'm using another computer now.

At least try.

---

### Post by badp on 2008-08-31
I'm just afraid that if I do, files might get created (logs, temporary files, etc.) and overwrite the blocks (or inodes or w/e) that belonged to my files. That'd make the loss almost permanent.

---

### Post by kellemes on 2008-08-31
> **badp said:**
> I'm just afraid that if I do, files might get created (logs, temporary files, etc.) and overwrite the blocks (or inodes or w/e) that belonged to my files. That'd make the loss almost permanent.

For recovery..
[http://www.mohdshakir.net/2007/10/31/data-recovery-with-photorec]("http://www.mohdshakir.net/2007/10/31/data-recovery-with-photorec")
Edit: more up to date link.. [http://www.psychocats.net/ubuntucat/recovering-windows-files-with-a-ubuntu-cd-iii-deleted-files/]("http://www.psychocats.net/ubuntucat/recovering-windows-files-with-a-ubuntu-cd-iii-deleted-files/")

And much more info..
[https://help.ubuntu.com/community/DataRecovery]("https://help.ubuntu.com/community/DataRecovery")

---

### Post by Sycron on 2008-08-31
Did you tried this ? [http://www.cyberciti.biz/tips/linuxunix-recover-deleted-files.html](http://www.cyberciti.biz/tips/linuxunix-recover-deleted-files.html)

---

### Post by Taxman415a on 2008-08-31
Yes, don't boot from the drive. If you do not overwrite anything, then you may be able to get some of the files back. So you're right to not want to boot from it. Best is to boot from the livecd and image the partition with ddrescue or somethig and then work on the image on another computer if you have the disk space. If not at least work while booted from the livecd. Any screwups and you're toast if you don't have a separate image to work from. Then of course, if it's important, keep better backups. ;)

Try installing some of the software listed here:
[http://ubuntu-rescue-remix.org/Software](http://ubuntu-rescue-remix.org/Software)
and read this guide too:
[http://www.informationweek.com/shared/printableArticle.jhtml?articleID=208403254](http://www.informationweek.com/shared/printableArticle.jhtml?articleID=208403254)

---

### Post by monkeyking on 2008-08-31
I've never had success recovering files on a linux system, that was caused by a user accidently deleting them.

I've only been able recover if it was a harddisk failurer or similar.


If you have any success recovering your files.
I would be glad knowing how you did.

---

### Post by badp on 2008-09-01
I've booted from a Xubuntu live cd. After some minutes to fix the huge characters issue (which I now am pretty sure is dpi-detection related, but this is a story about another thread) I got working.

First and foremost, rm ~ did nothing. My home folder is safe and so are the random config files sitting there. Ubuntu will boot normally. Woot!

Now I need to recover the lost scripts though.

Following the instructions on the article I've found on [http://linux.sys-con.com/node/117909](http://linux.sys-con.com/node/117909) I used debugfs, included in the Xubuntu live cd. The data I want recovered is at inodes 38096, 16125[22, 23, 26, 31, 32, 36, 39], 161263[2, 3], 161280[3, 5], 1613260, 1616[498, 503, 505, 519], 5375099 and 5342469... and a dozen more. I have filenames and I am confident that almost all files were smaller than 4 kB (and of those that were bigger I should be able to recode the remaining).

So I went ahead and tried 'cat <38096>'. Nothing happened.
I tried 'undelete <38096> realfilenamehere' and got 'Filesystem is opened in read/only mode.' Fair enough.

Now: the fsdebug manpage suggests against undelete'ing multiple files with their filenames, but rather to just undelete the files and have fsck rescue the files in lost+found. I can then move what I need back in ~/sh and call it a day.

fsck isn't though exactly "easy" to launch. I guess I could just set the partition as dirty with debugfs, reboot into Ubuntu and let the boot scripts do that for me. I am not though sure if that will recover my files or delete them again. During boot I have seen multiple times something that readed like:

```
[    xx.xxx] Deleting x orphan inodes
[    xx.xxy] Resumed ordered read mode on device.
```

which doesn't help my doubts.

Hints?

---

### Post by forger on 2008-09-01
> **Sycron said:**
> With that command you deleted your **home/your_user_name** files/folders.

No he didn't, rm ~ deletes the **files** that are in /home/yourusername
The folders would have be deleted if he used the -r parameter.

So you practically have deleted the files that are directly under /home/yourusername, the folders should be there and intact

---

### Post by badp on 2008-09-01
> **forger said:**
> No he didn't, rm ~ deletes the **files** that are in /home/yourusername
The folders would have be deleted if he used the -r parameter.

So you practically have deleted the files that are directly under /home/yourusername, the folders should be there and intact

Nope, those files are intact. I guess it's rm ~/* that does what you said. 'rm ~' deleted nothing that I could see.

So I have prepared the fsdebug commands (first I undel all inodes then I manually ln them back), made backups, opened the drive in write mode and am ready to paste them over in the terminal window.

What do I know. I'll cross my fingers and hope that manpage is up to date.

---

### Post by badp on 2008-09-01
And there they are.

A dozen of blank files.

Heh.

Well, thanks anyway guys. I guess I will just have to code them again.

---

