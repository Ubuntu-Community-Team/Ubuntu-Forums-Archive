---
title: "NTFS file recovery for Linux"
date: 2008-07-17
forum: General Help
---

### Post by weblordpepe on 2008-07-17
Hi there boys & girls. 

[B]Can somebody please recommend me a nice GUI application for recovering files/folders from an unaccessible NTFS drive? There are countless ones available but all require something called 'Windows' which I don't want.
[/B]

I have had not one, not two, but **three** NTFS filesystem / harddrive corruptions in a ROW. All using Windows XP. Not sure why, but every time I installed XP on a new disk, it would work for a while then die again.

The problem is that, it would work long enough for me to recover my files, but then the drive where I was booting from (with saved data) would get destroyed. BSOD!! This is using not only an old disk, but a proven reliable mid-age disk, and also a brand new 1TB disk.

Before narrowing it down to hardware failure I thought I'd boot up Linux. And oh yes it runs beautifully now.

So yes here I am. I would like to recover my files back from the NTFS volume but there's no way in hell I'm booting into XP again on this machine.

**Can someone please recommend me a nice program that'll let me scan for my C:\ or documents and then save them safely?**

---

### Post by Taxman415a on 2008-07-17
As far as I know, no one has written a fancy GUI tool. Though you could try wine I suppose. There are command line tools though. Google search through the ubuntu forum archives for ntfs file recovery tools or some combination of that to see if there are others, but install the package ntfsprogs and read the manpage. ntfsfix (in that package) is may be what you want to start with. Also have a look at some of the other packages here: [http://ubuntu-rescue-remix.org/Software](http://ubuntu-rescue-remix.org/Software)
All can be installed with apt-get, etc.

And if you're having that many corruption problems, it may very well be a hardware problem or perhaps you just have power that fluctuates really badly. There are several possibilities.

---

### Post by weblordpepe on 2008-07-17
Nice one thanks! In any event, I think I may do a DD to copy all those 0s and 1s off the disk to a safe file before I start messing around. Thanks :)

---

### Post by Sef on 2008-07-17
Look at this [article]("http://www.informationweek.com/news/storage/disaster_recovery/showArticle.jhtml?articleID=208403254") from Information Week.

---

### Post by Taxman415a on 2008-07-18
Nice link Sef. That one is going in my permanent collection for file recovery questions. The printable page link actually gives the whole article and makes it much less painful.

---

### Post by ramjet_1953 on 2008-07-18
In the past, I have had success with Gibson Research's SpinRIte Ver 6.0.

It's not free, but I guess if your data is worth recovering, it's worth paying out a little for it.

Here's a link to their website:

[http://www.grc.com/sr/spinrite.htm](http://www.grc.com/sr/spinrite.htm)

A lot of people have criticized their advertizing hype and some of the claims of this product, but the fact remains that in many cases it does an excellent job.

Regards,
Roger :cool:

---

