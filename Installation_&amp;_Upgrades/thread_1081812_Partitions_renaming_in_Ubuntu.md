---
title: "Partitions renaming in Ubuntu??"
date: 2009-02-26
forum: Installation &amp; Upgrades
---

### Post by Will4 on 2009-02-26
Hey folks,

can you give me an advise on what software to use for formating NTFS and renaming a partition within ubuntu and without doing it at a Windows PC??

much appreciation,

Will

---

### Post by yther on 2009-02-26
I'm not sure about renaming, but I think any form of **fdisk** can do that.  Try **cfdisk** or **gparted**, for a CLI and GUI version, respectively.  As for creation and formatting, either **ntfs-3g** or **ntfstools** should provide that.  It looks (from the blurb in the .deb) like ntfstools gives the **mkntfs** command, which&#8212;as you might expect&#8212;allows you to make a NTFS volume.

I have not used this for anything important, but I *read* from my laptop's NTFS volume almost every day.  Vista has never complained about anything Linux has done to the files on that drive.  :)

---

### Post by Will4 on 2009-02-26
OK thanks yther,
i'll give it a try... of course, it never occurs to me to try [B]mkntfs...

thanks!
[/B]

---

### Post by Herman on 2009-02-27
GParted can Detect, Read, Create, Grow, Shrink, Move, Copy, Check and Label your NTFS, refer to the following link, [GParted Features]("http://gparted.sourceforge.net/features.php").

It helps if you are using the latest version of GParted, I don't think GParted in Hardy Heron has the labelling feature, but Intrepid Ibex's and later GParted, or recent  GParted Live CD or Parted Magic CDs should have all the features you require.

They may be being a little optomistic claiming GParted can 'Check' NTFS, I think they mean they mark it with a 'dirty' flag and let Windows check it next time Windows boots.
Nevertheless, GParted is by far the best partition editor around.

GParted is in your Ubuntu 'Desktop' Live CD, just go 'System'-->'Administration'-->'Partition Editor', (GParted).

You can also easily install GParted in your hard disk installed Ubuntu operating system.

---

