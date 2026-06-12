---
title: "SSD or HDD?"
date: 2011-08-05
forum: Hardware
---

### Post by ryuguns on 2011-08-05
Hello, I'm building a custom computer soon, I was wondering if I should get a solid state drive or a hard disk drive? Any good links?

---

### Post by akand074 on 2011-08-05
Both. Unless you don't have a lot of data. Put your OS/applications on the SSD and put your data on an HDD (because large sized SSDs are super expensive).

---

### Post by ryuguns on 2011-08-05
How do I do that? I don't have a clue. Sorry, I'm a hardware n00b. :'(

---

### Post by IWantFroyo on 2011-08-05
Linux runs very quickly on both, so I don't think speed would be an issue with HDDs (presuming you're planning to run Linux). My home-built computer works perfectly fine with an old 20gb HDD, and it still boots up faster than any Windows computer I've seen. Plus, I stream all my music, so I'll probably never end up using all 17gb left after an Ubuntu installation.

Bottom line: I would get an HDD, unless your computer is going to be filled with tons of media. Then I would recommend akand074's approach.

---

### Post by akand074 on 2011-08-05
> **ryuguns said:**
> How do I do that? I don't have a clue. Sorry, I'm a hardware n00b. :'(

best way is through a manual install, you can just point your main filesystem to the SSD and either put your home folder or create a new data folder and point it to your HDD. If you decide to get both, post back here or PM me and I can give you step by step instructions if you'd like.

Like the post above me said, it's not necessary to have an SSD, but if you do want the benefits of one, and you have a lot of data (i.e more than the size of the SSD) then getting both would be the best approach (like I have done).

---

### Post by oldfred on 2011-08-05
Hard drives fail and SSDs also fail. I would suggest whatever you do to buy two drives or the SSD & two drives. If you do a small SSD it can be just a boot drive with all your data on the hard drives. Unless you are compiling a lot of programs, video editing or other system intensive applications, the SSD will not give huge improvements for many things. You cannot type faster, and Internet connection controls download speeds. But SSD will boot faster & larger programs will load noticeably faster.

---

### Post by jbo5112 on 2011-08-05
I second the idea of getting both or even substituting the hard drives with a good NAS server (possibly self-built).  You'll want to make sure the SSD is mounted as "/" and maybe used for a swap partition*.  What I would recommend for the hard drive is to create a special folder that everyone has access to for all of your media (e.g. "/home/Media").  Then you can mount the hard drive there for 100's of GB or TB's of disk space, and create a folder there to save your documents (e.g. "/home/Media/<myaccount>"), if the SSD doesn't provide enough room.  If you want to get advanced about it, you can even set up your documents folder as a link to the folder on the hard drive.

Drive crashes are rare enough that I'm not worried about losing my system files and needing to reinstall Ubuntu, so I wouldn't bother backing up the SSD with mirroring.  However, if you can afford it 2 or 3+ drives in RAID would make for a nice media and backup server.  Hosting your all media on a network instead of using discs is rather nice, but it can eat up disk space quickly.  Fortunately, I think the "green" hard drives will still do nicely here.

*I'm not sure how much an SSD would like being used as swap space, but it would be good at it.  With current RAM prices, unless you're seriously tight on money, I would make sure you have an abundance of RAM, which will make a bigger deal than SSD vs HDD, and if possible, leave room for upgrades.  Linux will automatically use free RAM to cache the data read from disk, so you might only need to read your programs from disk once per boot.

---

