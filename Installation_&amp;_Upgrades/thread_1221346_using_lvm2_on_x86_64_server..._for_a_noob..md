---
title: "using lvm2 on x86_64 server... for a noob."
date: 2009-07-23
forum: Installation &amp; Upgrades
---

### Post by parkerbender on 2009-07-23
I'm trying to setup a new file server, I have a pair of sata drives, the first disk was setup on lvm from the install disk.  I'm now trying to stick the second disk to the first, using lvm, preferably with a gui frontend.  The goal is to end up with this computer having an optional kdu gui, when an extra computer is needed, but it would be fine if it booted to terminal, or either way, really.  currently it's running gnome, on server 9.04.  entire first drive is lvm, there's a 10gb partition on the second drive for swap, and then the rest of the second hdd is formatted ext3, but blank.

there probably is a tutorial or something to explain to me how to do this, but i've been wading through them, and trying this and that, (plus, they're all like four years old) and nothing seems to work, so, i figured i'd just ask.

Thanks for any help!

-Parker

ps.  if I could go back to the install disk, go to manual partition config, and set this all up... i'm not far enough along that it would bother me to wipe all of this and start clean...

...if it's easier!

---

### Post by parkerbender on 2009-07-24
bump?  Anyone have any ideas about lvm?  is it even the easiest way to combine the two disks, or is there an easier one?

Thanks!

---

### Post by parkerbender on 2009-07-24
bump... one more try...

Any ideas at all?

Am I in the wrong forum?

Thanks for any reply!

-Parker

---

### Post by Herman on 2009-07-24
:D Probably no-one is answering because nobody knows, or those who know are smart enough for their services to be in demand and thus their time is valuable and therefore limited.

Sorry, but I can't directly answer your question myself.
I was trying to do something like what I think you mean a couple of weeks ago, but I was only trying it out in a pair of USB flash memory sticks. One has Ubuntu Karmic Koala in it in encrypted LVM as in this link, [Ubuntu Karmic Koala Encrypted LVM Flash Memory Installation]("http://members.iinet.net/%7Eherman546/p19.html"). I tried to expand the logical volume into an empty USB flash memory stick and I succeeded in doing so, or at least it seemed as if I did. The step that 'borked' my installation was the last step, trying to resize the encrypted file system to fill up the extra space.

Have you read  [How to Resize a LUKS Encrypted File System]("http://ubuntuforums.org/showthread.php?p=4530641") - bodhi.zazen - Ubuntu Web Forums? (I didn't find that tutorial until it was too late).
According to my understanding of the contents of that tutorial, my particular problem was that a crpto file system can't (simply and easily) be extended across more than one disc, unless there's something more for me to learn somewhere. Someday maybe I'll find out. In the _NOTE _under 'Resizing ~ Overview' in that tutorial, bodhi.zazen doesn't say it's impossible, he just says he's not sure if it's possible. 

Have I properly understood what you're trying to do?

I was thinking of re-installing with just LVM and no encryption to see if I could learn the LVM part of things by itself, but for now there are some other things I want to do, so I'm leaving it in my list of things to learn about later. 

You didn't mention if you are only using LVM or if you have encrypted LVM. If you're just using plain LVM then hopefully the link to bodhi.zazen's tutorial will help you.

Please let me know what happens, if you have time. I'm interested in this subject too.

---

