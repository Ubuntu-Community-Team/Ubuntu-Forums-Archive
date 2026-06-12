---
title: "Harddrive advice"
date: 2012-02-11
forum: Hardware
---

### Post by SnickerSnack on 2012-02-11
I recently put together a new desktop (see sig), but I'm still using the harddrive out of my old laptop that died.  It's 320GB, and most likely 5400RPM.

I read this article: [http://www.zdnet.com/blog/ou/how-higher-rpm-hard-drives-rip-you-off/322](http://www.zdnet.com/blog/ou/how-higher-rpm-hard-drives-rip-you-off/322), and I wanted to see if anyone can comment on the validity of the article's claims.  I was considering getting a small 10k RPM drive, but it would seem that I'd be better off getting a slower drive and setting aside a large partition that is rarely ever mounted.

Also, are the partitions always ordered sequentially on the drive from the outer edge to the center?  Will sda[i] always be faster than sda[i+1]?

I'll continue to use the 320GB drive for storage once the new install is set up, so I don't need a lot of space.  For the windows install, I have several games on Steam that take up a lot of space - probably ~30GB.  I think win7 probably takes around 50GB.  For the linux install, I think 7GB would be sufficient, but I've always used 15GB in the past for the root partition and then about 20GB for the home directory.  Perhaps 120GB total is all that would be needed in the boot drive.  If the article is correct, then I could get a 600GB 7200RPM drive, partition ~150GB for OSes and home directories.  It would all sit on the fastest 25% of the drive, and I'd rarely even mount the slowest 75%.

Another option: I could borrow a spare drive from a friend, backup the 320GB drive, wipe it and put a fresh install on it.  But, I don't know if the 5400RPM would still be a problem for system performance.

Any advice is appreciated.

---

### Post by wolfen69 on 2012-02-11
If you can afford it, an SSD is the fastest.

---

### Post by sudodus on 2012-02-11
> **wolfen69 said:**
> If you can afford it, an SSD is the fastest.
+1
and nowadays the price gap is not that big :-)

---

### Post by SnickerSnack on 2012-02-11
I could see using an ssd for the linux root directory, but won't windows run down an ssd quickly because of the (comparatively) frequent writes?  I don't want to have to replace the root drive in only a few years.

As I understand it, an ssd is very good for something that gets written once and read often after that, but bad for something that gets written often.

Edit: Also, I'll mostly be using it for sequential read/write, so ssd is not that much of a benefit, as I understand it.

Edit: With most (all?) web browsers on linux, all the temporary internet files are put in the home directory, so I suppose if I use chrome/ff only on windows, then I don't have to worry much about windows (via internet explorer) running down the drive?

---

### Post by ahallubuntu on 2012-02-11
> **SnickerSnack said:**
> I could see using an ssd for the linux root directory, but won't windows run down an ssd quickly because of the (comparatively) frequent writes?  I don't want to have to replace the root drive in only a few years.

As I understand it, an ssd is very good for something that gets written once and read often after that, but bad for something that gets written often.

You are confusing SSD with a regular flash drive.  SSD devices use flash memory for storage, but the controllers use sophisticated mapping algorithms to balance repeated writes over the entire flash array, not just to the same flash location over and over and over again.  A single file that you keep editing on an SSD may move to different locations on the flash drive invisible to you.

A regular USB flash drive, by contrast, has none of this balancing.  You can use it for storage, but if you keep writing to the same location, eventually you will wear it out - hundreds of thousands of times, though.

A 5400PM drive can be slow for performance, but all of my laptops have had them, and I have been satisfied with performance.  Would a 7200RPM desktop drive be faster?  Of course.  What can you live with?  If you can afford it, buy an SSD or a desktop 7200RPM drive.  If not, stick with the laptop drive, it should be fine just a tad slower.

---

### Post by SnickerSnack on 2012-02-12
> **ahallubuntu said:**
> You are confusing SSD with a regular flash drive.  SSD devices use flash memory for storage, but the controllers use sophisticated mapping algorithms to balance repeated writes over the entire flash array, not just to the same flash location over and over and over again.  A single file that you keep editing on an SSD may move to different locations on the flash drive invisible to you.

A regular USB flash drive, by contrast, has none of this balancing.  You can use it for storage, but if you keep writing to the same location, eventually you will wear it out - hundreds of thousands of times, though.

A 5400PM drive can be slow for performance, but all of my laptops have had them, and I have been satisfied with performance.  Would a 7200RPM desktop drive be faster?  Of course.  What can you live with?  If you can afford it, buy an SSD or a desktop 7200RPM drive.  If not, stick with the laptop drive, it should be fine just a tad slower.

I've read about wear leveling, but I didn't have it in mind while writing my last post.  I also didn't know if it was sufficient to overcome the wear of an OS that writes to root directory frequently (like windows does).  Thanks for pointing that out to me.

I was already considering an ssd at the time I made the original post, but I didn't want to make the post too broad.  I wanted to get more information about the usefulness of platter drives before weighing them against ssds.  But, it would seem that the overwhelming advice is that ssds are better.

Also, money is not much of a barrier.  I *can* afford to spend on a nice drive, I'm just reluctant to spend a lot of money unnecessarily.  If it would cost me 300+ USD to get a decent speed boost, then I wouldn't do it, but ~150 USD is okay (still more than I want to spend, but okay).  I see several 120-128GB ssds on newegg around $150, though most of the ocz drives have low ratings.

Edit: Does wear leveling work if I have the drive partitioned?  Will the windows partition die out before the linux partition if I don't leave it enough space to spread out the wear?

Edit: I'm thinking about getting this: [http://www.newegg.com/Product/Product.aspx?Item=N82E16820227726](http://www.newegg.com/Product/Product.aspx?Item=N82E16820227726)

---

### Post by wolfen69 on 2012-02-12
> **SnickerSnack said:**
> 
Edit: I'm thinking about getting this: [http://www.newegg.com/Product/Product.aspx?Item=N82E16820227726](http://www.newegg.com/Product/Product.aspx?Item=N82E16820227726)

That looks like a great drive. I have an agility 2 in my netbook, and it's been great. I wouldn't worry too much about wearing out, as I heard you could write many GB's per day and it would be 15 years before you would have to worry about it. I'm sure your computer would be obsolete by that point. ;)

---

### Post by SnickerSnack on 2012-02-13
Well, it's ordered, so we'll see if it does what I need.

Thanks for all the replies.

Edit: The same exact one just went on sale. :)  After I ordered it. :(
Edit: I've cancelled and reordered.

---

