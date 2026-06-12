---
title: "Partitioning gone horribly wrong..."
date: 2008-10-18
forum: General Help
---

### Post by EcthelionGenesis on 2008-10-18
It was bound to happen some day... GParted has killed my data partition. While I do have a backup of important work, it'd be nice if I could recover my video collection etc.

Essentially, I was trying to put in an extended partition to install some more distros on. In the process, I had to resize my data partition, (/dev/sda2) for which I used a Live CD and GParted. Most of the process went fine, but then:

[FONT="Courier New"]\TRASH-~1\FILES\AGAVE_~1.DEB is 318k, but it has 1 clusters (16k).[/FONT]

AAAH!

I have uploaded the html details file outputted [here]("http://ectheliongenesis.googlepages.com/gparted_details.htm"), if you're interested?

Doing a [FONT="Courier New"]dosfsck -a -w -v /dev/sda2[/FONT] results in a long list of nasty looking checksum fails and ends in a segfault. Nice.

So, is this recoverable? Or should I just delete the partition and start again?

Any help appreciated :)

---

### Post by mikewhatever on 2008-10-18
You can try using photorec to recover files.
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

---

