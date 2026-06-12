---
title: "Which choice in Kbuntu install"
date: 2009-07-02
forum: Installation &amp; Upgrades
---

### Post by webbdawg on 2009-07-02
I have a sony vaio VGN-SZ330P laptop, which I just upgraded my hard drive to a 320gB 7200rpm wd-scorpio. I partitioned off 100gb for a kubuntu install and left it unformatted. Win XP Pro occupies the first partition at 200gB.

When I go to install Kbuntu I get the 3 choices of install side by side (same partition), Use the whole disk or the advanced. SO I go to the advanced and get a whole slew of choices and that is where I get confused.

I still  want to be able to choose my OS at boot (with Win XP being the default, in case I walk away on a slow boot).

If I install to the second partition:
[LIST]
[*]Is Kbuntu a good choice for a laptop?
[*]Which Install choice should I use?
[*]If I choose Advanced, which Choice should I use?
[*]Will I get the grub loader choices?
[/LIST]

If there is some good documentation where can I find it.

Thanks

---

### Post by merlinus on 2009-07-02
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

---

### Post by webbdawg on 2009-07-02
After looking at the guides, it looks as though I should have just left my hard drive one big partition??

---

### Post by merlinus on 2009-07-02
I do not think so, as long as you are willing to use the manual (advanced) partitioning method.  THis will require you to specify sizes, formats, and mountpoints for your linux partitions.

My suggestion is 10-15G for /, 1.5G /swap, and the rest for /home, where application configurations and personal data are stored, and this will not require backing up when reinstalling or installing a newer version.

At this point in time I would use ext3 rather than ext4, as there have been a number of cases of lost data with it.

---

### Post by webbdawg on 2009-07-02
Thanks, before I do this install I need to back up my current drive. I was thinking of just doing an image. Any suggestioins on a good program for making bootalbe disk images for restoring.

I will make an image before the Kbuntu install (win xp only) and after (win xp and kbunto).

Thanks

---

