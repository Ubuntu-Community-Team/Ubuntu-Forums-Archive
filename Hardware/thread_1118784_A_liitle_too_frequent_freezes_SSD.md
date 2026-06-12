---
title: "A liitle too frequent freezes: SSD?"
date: 2009-04-07
forum: Hardware
---

### Post by dclement on 2009-04-07
Hello,

I thought my rather old laptop would perform petter with a SSD. So I bought a rather low-end Transcend 32 GB IDE (SLC).

Following many advices, I chose ext2 with no swap (RAM is 2 GB).

In the past month, I had no less than 3 complete freezes. Only a hard reset would work. I then had file corruption in my /home.

I reinstalled the traditional HD, and no more problem in 15 days. So...

- was it a mere coincidence (ahem...)
- is Transcend crap?
- is it the lack of swap space or the ext2 filesystem?
- is it the IDE/SSD combination?

I'm puzzled, because I thought I would order my next laptop directly with a SSD, but now I hesitate. OTTH, my wife has an eee-PC with exactly the same setup and no trouble...

I'd be glad to read advice or user feedback.

TIA - best regards, Daniel

I'd be glad

---

### Post by andrewc6l on 2009-04-08
These pauses appear to happen when manufacturers use a particular controller. (Unfortunately, a lot of them use it).

Here's a really good article:

[http://www.anandtech.com/storage/showdoc.aspx?i=3531](http://www.anandtech.com/storage/showdoc.aspx?i=3531)

(I just noticed you were having freezes, not pauses... but the article is still good :-) )

---

### Post by dclement on 2009-04-08
Thanks for the link to the article, it's full of interesting details.

I confirm applications start lightning fast, but the overall performance does not seem to improve as much (low end SSD, once again).

As for the "pauses", I've seen a couple of them too. But they are never as severe as these complete freezes from which only a hard reset will recover.

It does happen at times with a HDD, but in this case, I think the ext3 filesystem proves more reliable on the next startup.

Many things to consider...

---

