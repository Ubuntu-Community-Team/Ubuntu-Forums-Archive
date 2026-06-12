---
title: "Managing Disk Usage"
date: 2007-04-11
forum: Hardware &amp; Laptops
---

### Post by ebozzz on 2007-04-11
Is there a way to safely change the distribution of the file system. I'm a little concerned about my root and usr directories. A screen shot is attached. Thanks!

---

### Post by stalker145 on 2007-04-12
> **ebozzz said:**
> Is there a way to safely change the distribution of the file system. I'm a little concerned about my root and usr directories. A screen shot is attached. Thanks!

Being somewhat new to the guts of a Linux file system myself, I was just wondering what the concern was. I had to google for an [explanation of the /usr directory]("http://www.unet.univie.ac.at/aix/aixbman/admnconc/usr_fs_under.htm") and found myself still wondering.

Your capture shows that you still have a boatload of space remaining on your drive. The 74% usage of your /usr directory is just showing how much of total drive usage is in that directory. So, out of the few GiB used, 74% is in one directory. It's really no problem as far as I can see since there is so much remaining.

Now, I could be wrong, but I wouldn't fret about it.

---

### Post by ebozzz on 2007-04-12
My concern was the [COLOR="Red"]red[/COLOR] fields in my screen shot that in my mind indicates that those directories are close to full. I am still pretty new myself.Thanks.

---

### Post by stalker145 on 2007-04-13
> **ebozzz said:**
> My concern was the [COLOR="Red"]red[/COLOR] fields in my screen shot that in my mind indicates that those directories are close to full. I am still pretty new myself.Thanks.

Sorry for the delay. I took the night off and watched movies last night.

Now, as for your concern for the red-listed items: they're really of no concern. 

If you note the item that I've circled, that shows you that you, in fact, have a ~160GiB HDD of which only 5.3GiB is used. Your root directory (shown as / ) shows 100% use at a total size of 5.2GiB. The next line is showing that of the 100% (5.2) used in the root, you have 74.4% (3.8GiB) used by the /usr directory.
If you were to expand the little triangle next to usr, you would, more than likely, see 10 subdirectories and then corresponding bar graphs noting how much of the 3.8GiB used is in each subdirectory.
That said, the 100%, 74.4%, and all other measurements are simply telling you what percentage/amount of space is being used by each directory of the total **amount used** by the installed files. It has nothing to do with the amount of disk space available. If you really were running at 100% full on your HDD, I don't think your computer would be all that blazing fast nor would you be able to save even a simple text file.
There's no worries, just be sure to compare (as separated by the line through the circled item) the amount of space used with the amount of space available.

You're good :)

---

### Post by ebozzz on 2007-04-14
> **stalker145 said:**
> Sorry for the delay. I took the night off and watched movies last night.

Now, as for your concern for the red-listed items: they're really of no concern. 

If you note the item that I've circled, that shows you that you, in fact, have a ~160GiB HDD of which only 5.3GiB is used. Your root directory (shown as / ) shows 100% use at a total size of 5.2GiB. The next line is showing that of the 100% (5.2) used in the root, you have 74.4% (3.8GiB) used by the /usr directory.
If you were to expand the little triangle next to usr, you would, more than likely, see 10 subdirectories and then corresponding bar graphs noting how much of the 3.8GiB used is in each subdirectory.
That said, the 100%, 74.4%, and all other measurements are simply telling you what percentage/amount of space is being used by each directory of the total **amount used** by the installed files. It has nothing to do with the amount of disk space available. If you really were running at 100% full on your HDD, I don't think your computer would be all that blazing fast nor would you be able to save even a simple text file.
There's no worries, just be sure to compare (as separated by the line through the circled item) the amount of space used with the amount of space available.

You're good :)


Thank you Stalker! My major concern was that the /  and usr directories would become too full and cause some type of problems. I ran into an issue once where I was not able to login because of an error that stated that there was no available space. I am positive that the files on that drive were pretty similar to the drive pictured in my attachment. I saw all of the information regarding the free space but that red just bothered me. :)

---

