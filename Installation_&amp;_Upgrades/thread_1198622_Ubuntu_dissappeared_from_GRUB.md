---
title: "Ubuntu dissappeared from GRUB"
date: 2009-06-27
forum: Installation &amp; Upgrades
---

### Post by volley on 2009-06-27
Hello,

Two items containing Ubuntu kernel dissappeared from GRUB, although Ubuntu Memory Check is still  there. Ubuntu is still installed on my hard disc, but I can not boot it from GRUB or elsewhere. 
Repairing the installation is not an option from the live CD. 
Re-installing Ubuntu fails because there is already 65 GB Ubuntu kernel installed on one partition. 
I am thinking of deleting the entire Ubuntu partition from my Windows installation and re-installing Ubuntu.
I would appreciate if somebody tells me whether this is a good idea (or if you have a better idea) and would advice me whether to carry it out or not.

Regards,
Alex

---

### Post by Herman on 2009-06-27
I have heard of Windows boot entries disappearing from GRUB, but this is the first time I have ever heard of a Ubuntu boot entry disappearing. With Windows boot entries, the most common reason is because people try to make Windows boot first by copying and pasting the boot entry above Ubuntu in the debain automagic kernels list.
I can't imagine how a Ubuntu entry could disappear like that.

Normally we don't like to advise people to re-install because we like to teach people how Ubuntu can easily be fixed. One of the great things about a free, open source operating system is that it's a lot easier to fix. 

The reality is, most of the time re-installing is probably the fastest and easiest way for new users to solve all their problems. I have to admit that when I was a new user, I used to re-install quite often.
One great thing about Ubuntu is, it only takes about half an hour to re-install. If you didn't have a lot of fancy settings and customizations, or a lot of data to back up and restore, re-installing is one quick way to get rid of a lot of problems.

If you want help trying to fix your problem, it will take longer as it will be necessary to provide a lot more information and wait for replies. You could boot a Live CD and run some commands to get a copy of your /boot/grub/menu.lst for a start, and someone here could tell you how to fix it. The advantage of that is, you might learn how to do it quickly without help if the same problem ever happens again. Here's a link that should help you get started, [Rescue your Linux system with a Live CD]("http://members.iinet.net.au/%7Eherman546/p10.html#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD")[COLOR=#666666][COLOR=#000000] - includes commands for opening vital files.[/COLOR][/COLOR]

There's no automatic boot loader fixer yet in the Live CD, unfortunately.

Regards, Herman :)

---

