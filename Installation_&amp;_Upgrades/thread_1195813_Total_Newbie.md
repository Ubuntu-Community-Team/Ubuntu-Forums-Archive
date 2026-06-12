---
title: "Total Newbie"
date: 2009-06-24
forum: Installation &amp; Upgrades
---

### Post by Tclynch on 2009-06-24
Ok, so I'm giving Ubuntu a try. I downloaded 9 and burned the disc. Loaded it and allowed it t make it's own partition (btw, I am running Vista Home Premium, 320 gig HD, 3 gig ram, dual core) and so far, I am having these problems-

1) I allowed it to download some updates, but have been unable to install them due to not enough space on the disc. What??? 

2) I have noticed that I have problems with using Wifi. Basically, I have to be closer to my router to get wifi to work with Ubuntu...

3) Firefox- the "Back" button and the Bookmarks does not seem to work.


Any help for this newbi????

---

### Post by Snoober on 2009-06-24
1) How much space did you allow for the Ubuntu partition?
2) Check out [https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)
3) Try re-installing [Firefox]("http://www.mozilla.com/en-US/firefox/all.html").

---

### Post by ddrichardson on 2009-06-24
> **Tclynch said:**
> Ok, so I'm giving Ubuntu a try. I downloaded 9 and burned the disc. Loaded it and allowed it t make it's own partition (btw, I am running Vista Home Premium, 320 gig HD, 3 gig ram, dual core) and so far, I am having these problems-

1) I allowed it to download some updates, but have been unable to install them due to not enough space on the disc. What???
Can you open a terminal (Applications->Accessories->Terminal) and post the output after typing```
df
```> **Tclynch said:**
> 2) I have noticed that I have problems with using Wifi. Basically, I have to be closer to my router to get wifi to work with Ubuntu...Does this only happen with Ubuntu?

---

### Post by Tclynch on 2009-06-24
I allowed Ubuntu to set up the partition. I don't remember seeing a screen asking me how big of a partition. Did I miss something or do I need t reinstall Ubuntu?
  Yes, when I am using Vista, I have a longer range with my home wifi than with using Ubuntu.

---

### Post by Snoober on 2009-06-26
Did you use Wubi to install Ubuntu or did you just install it via the live CD? During installation you would have encountered the partition setup. Try what ddrichardson suggested and post it here.

---

### Post by bwitherell on 2009-06-26
> **ddrichardson said:**
> Can you open a terminal (Applications->Accessories->Terminal) and post the output after typing```
df
```Does this only happen with Ubuntu?

In order to see if you have enough space on your Ubuntu partition please open a terminal and run the df command as stated by ddrichardson. This will report back to you the size in blocks of your partitions, and the free space on each of your partitions.

To get the size of your partitions in a more human readable output ie: bytes, gigabytes, megabytes instead of blocks include the -h switch with the df command as demonstrated below.

```
df -h
``` 

for more info on the df command you can open a terminal and type:

```
man df
```

the man command shows a manual of a command. so the "man df" command above will show you a manual for the df command.

Hope this helps. Oh yes also please post the output of the "df -h" command.

---

