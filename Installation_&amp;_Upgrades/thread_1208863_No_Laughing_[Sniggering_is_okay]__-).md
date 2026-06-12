---
title: "No Laughing [Sniggering is okay]  :-)"
date: 2009-07-09
forum: Installation &amp; Upgrades
---

### Post by phillw on 2009-07-09
[SIZE=2][FONT=Arial]Piglet (yes, that IS the official name of my laptop !) is a happy little scizophreniac. I have a vista partiton (sda1), Ubuntu (sda3) and swap (sda5)

For various reasons, I loaded Ubuntu 9.04 Desktop, then manually added the remainder of LAMP (Main reason - to learn better how they hang-out together !!)

Since then, I have altered and added quite a lot. And all is well in the world - Still dual boots for when I need Vista (Usually to support some poor windows person).

But, now I want to re-partition everything... 

The hard drive is 80GB, single core Celeron M with 1GB RAM.

[/FONT][/SIZE][SIZE=2][FONT=Arial]I have 2 users, 5 MySQL databases, osCommerce with a lot of ammendments to the PHP files, Firefox - with all my passwords imported from Vista, Security updates etc. etc. ....... Yeah, I'd really hate to lose it all.
[/FONT][/SIZE]
[SIZE=2][FONT=Arial]
Currently it is .....

sda1     53 GB - Vista
sda3     20 GB - Ubuntu 9.04
sda5      4 GB - Swap

What it will be is ...

sda1    20 GB - Vista
sda3    55 GB - Ubuntu
sda5      2 GB - Swap.

1st question. As I am using piglet as a means of learning hosting, etc. Is 2 GB Swap sufficient ? - there will only ever be 2 - 3 people on it.

Now for the bit that'll make you laugh / cringe / weep tears (of sorrow or laughter !!)

I don't want to lose my Ubuntu installation.

piglet has an internal DVD-RW and I also have an external USB DVD-RW.

If I boot a liveCD (the Ubuntu one, oddly enough !!)
can I cp -r /dev/sda3/. /dev/sr1 (or whatever it calls my external DVD-RW) to take a 'snap-shot' of my Ubuntu installation ?

Then I intend to use the LiveCD to re-slice the hard drive.
Followed by popping Vista onto it's slimmed down area.
Then  a standard install of Ubuntu & swap onto sda3 and sda5 respectively. (This is to set the GRUB installer back up happily while I have a cup of tea & a cigarrette)

The next step is where I think this method may fall apart ....... (You're probably laughing already !!)

I propose to then re-boot with the LiveCD and copy the earlier made DVD str8 back onto /dev/sda3 - over-writing the newly Installed one. 

I should get at least 7 out of 10 for thinking about it ... ;-)

But, what do you think my chances are of actually getting away with it ?

If it is a no-hoper, could someone suggest a way.

Regards,

Phill.:-k
[/FONT][/SIZE]

---

### Post by phillw on 2009-07-09
[SIZE=3][FONT=Arial]Found the answer ... and it looks a darn sight easier than what I was looking at doing !!!

[http://ubuntuforums.org/showthread.php?t=35087&highlight=backup+restore+Ubuntu](http://ubuntuforums.org/showthread.php?t=35087&highlight=backup+restore+Ubuntu)


Hmmmm.... I am even more happy (Yeah, it doesn't take a lot) 
It seems Gparted live CD will do the resizing for me, without me losing data - I am, however, still going to back-up my current Ubuntu Install !!


):P


[/FONT][/SIZE]

---

