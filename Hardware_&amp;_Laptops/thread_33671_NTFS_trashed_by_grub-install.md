---
title: "NTFS trashed by grub-install"
date: 2005-05-11
forum: Hardware &amp; Laptops
---

### Post by mortensn on 2005-05-11
Hi guys

I've just installed Hoary on my brand new "vacuum cleaner" (looks that way, sounds that way... :-/) I've leased from my work through some tax evasion scheme we're having in Denmark. So the machine is by no way my basic machine but it would be nice if I could make the vc work again with xp. BTW it's a fujitsu siemens scaleo c.
[http://www.fujitsu-siemens.com/products/deskbound/personal_computers/scaleo_c.html](http://www.fujitsu-siemens.com/products/deskbound/personal_computers/scaleo_c.html)
fsc does not provide much hw detail but I can provide this if necessary.

I tried to install Mandrake 10.1 on the box but the system complained that it needed a driver for the nec dvd-burner - I don't know what Mandrake got confused about but I figured I could just as well try debian, which I've always wanted to try out but never got around to. Then I found out that somebody had made this nice new debian derivative Ubuntu and I figured, why not.

Ubunto booted nicely and went well untill partitioning. I think the partitioning menu was a bit confusing and could use some work. I'll take notes the next time...

The structure of the system was 
~300MB hda1 reiserfs  (some embedded instant on thingy)
~180GB hda2 ntfs (xp-home 0x7) 

I resized the ntfs to be 
~120GB still hda2 

and then made 
~10GB hda3 /
~50GB hda5 (in logical hda4) /home

I thought I'd use  linux for backing up my daughters dvd movies with Bamse&Kylling and thus I need a huge home or tmp.

Then after a successfull Hoary install I can only boot Ubuntu. Ok every 3'rd boot the system crashes and looses the usb mouse and keyboard and I have to take the power to the machine in order to make things right again... :-/

The windows boot starts to load stage2 but then switches back to the boot menu without an error along with a running timer of 6 secs... I didn't use rootnoverify in the start so the system complained about not being able to mount the ntfs partition but that didn't do the trick.

I chose to install grub on /dev/hda2 btw.

I've looked a bit about the geometry error solved by dfdisk -d /dev/hda | dfdisk --bla-bla-Icantremembertheoption from some other linux flavors (redhat had it). Allegedly grub misunderstood the partiton info or the partitioning software wrote a  partially wrong partition table. i don't remember exactly.

So what to do? I first tried to use fixboot or fixmbr but that didn't work. I think win said that it could not understand the partition but I thought that this was just a windows security-by-obscurity oddity... :-/ 

Well the I figured then I'd just try to reinstall XP - it is after all a new machine. How hard can it be? Well not more difficult than your average linux distro. And alas XP booted nicely. Oki then I booted on the Ubuntu install cd and found a shell and mounted devhda3, ran grub-install on devhda2 and tried to reboot. 

Ubuntu boots - winxphome does not.

Then I tried to mount devhda2 ro but mount complains about a thrashed bootsector! The partition is flawed. I can't mount it! How´t' h* did that happen?

So somewhere in ubuntu ntfs resize, ubuntu fdisk, fsc sata disk, winxp, grub or grub-install somethings wrong? Of course the error-40 (us error-16) is also a possibility... :)  

It's a peculiar thing that even though grub is said to be superior to lilo I've never experienced grub to work well. There's some russian tank about lilo. Does the job -  dirty but reliable.

Does anybody have an idea about where to look for a solution? I'd really hate to have to wipe the disk entirely though that may be the solution.

Morten

---

### Post by alastair on 2005-05-11
I don't really understand your partitioning rationale (or what hda1 is). But "resizes" always make me nervous. You might be best to try an XP "recovery" from the XP installl CD - at least to try and get XP booting again.

If successful ...

If you want to install Ubuntu - do the "resize" properly and - before installing Ubuntu - double check XP still boots!

---

### Post by mortensn on 2005-05-12
Thanks for your reply.

hda1 is a linux partition for the "Instant On" feature. I can reinstall this software if I want to. hda2 is XP home. hda3 is linux root, hda4 is logical partition for hda5-8. hda5 is linux home.

Well the installations are thrashed and the cause indeed was Ubuntu. 

So take heed when you try to resize or untill I solve this problem.

> If you want to install Ubuntu - do the "resize" properly and - before installing Ubuntu - double check XP still boots!

I did that. Xp does boot. When grub gets installed XP no longer boots. Then I can't mount the partition either.

I may get the partition geometries by other means and check whether the chs info is correct in the partition table if nobody has a better hint.



Morten

---

### Post by DutchLau on 2005-05-12
Although I'm using a SATA drive, I think we have the same situation. 

When I partitioned my drive, I figured I'd make a couple of partitions, your reasoning (I didn't have any OSes on it). I made a 15 GB partition (ext 2 - root) at the beginning of the HDD, a second 2 GB partition (swap) and a 128 GB partiton (ext 3 - home) - because it worked out nicely with these numbers. I left 15 GB of free space at the beginning of the drive after the swap and ext2 partitions so that I could install some windoze again if I ever wanted to (don't know why I ever would though  :razz: ).

It sounds like you might have messed something up in your partitioning. Did you "defragment" your HDD in windoze before trying to chop up your HDD? Did you make the partitions at the "end of the hard disk" as one of the options in the partitioning program? (I'm thinking that you might have made the partition at the start so that you chopped off all the windoze files and put your root there) If this is the case, then you've lost your xp home files. Did you try mounting the drive in Ubuntu yet to see if you could access it? (Information at [www.ubuntuguide.org](www.ubuntuguide.org))

>  Well the installations are thrashed and the cause indeed was Ubuntu. 

When I still had xp on my HDD I installed Mandrake (now Mandriva I believe) and Ubuntu without any problems whatsoever - so the problem is probably the admin  ;-) Try formatting your /home partition as FAT32 so winxp can also access it when you get it running again. But my advice is to try and retrieve the files from your xp partition (if you didn't overwrite them during your resizing) and save them on your new FAT32 HDD so you can put them on your xp drive again.  :grin:  After that reinstall xp on that big partition 120 GB I believe and your problems should be over. See if this works!  :-P 

Good luck and let us know your progress,

DutchLau

---

### Post by mortensn on 2005-05-12
My drive is a sata drive too.

Defragmentation shouldn't affect the outcome since it only affects the stored data and not the partition info. As previously stated, the error occurs after a fresh xp install (with a thorough format) followed by a 
   grub-install /dev/hda2

I'd never use FAT32 for anything linux. I'd rather use explore2fs. Works nicely. 

Or the ext2/3 driver from paragon. It's quite fairly priced and works well.

Morten

---

### Post by DutchLau on 2005-05-12
I had to do a defrag once because xp put files at the *end* of my HDD, so that's why I said it  :razz: 

Did you try mounting the NTFS partition with Linux to retrieve your precious files? I'm thinking that you might have "corrupted" your NTFS partition by "chopping" it with the partition editor. Maybe after you've backed them up you could try installing xp again if it's not too much of a problem. I've never really had the same problem you have and I haven't tried xp with SATA yet, I only have this computer a week orso.  :neutral:  I'm really sorry mate, but I don't know what you should do. There are many threads out there on reinstalling GRUB after installing xp and [this](http://ubuntuguide.org/#restoregrubmenuafterwindowsinstallation) might help you also. I'm really sorry I'm so vague, but this is why I would do also  :?: 

Good luck,

DutchLau

---

### Post by mortensn on 2005-05-12
Fixed the problem.

My problem was that I issued 

grub-install /dev/hda2

instead of 
grub-install /dev/hda

grub-install did not complain and I think the script ought to issue a warning before installing on /dev/hda[0-9]? I guess I was too used to good ole lilo which talks about hda1 as the device to be mounted during boot. I can't seem to discern the notation of "info grub" [http://docsrv.sco.com:8457/cgi-bin/info2html?(grub.info.gz)Installing%2520GRUB%2520using%2520grub-install](http://docsrv.sco.com:8457/cgi-bin/info2html?(grub.info.gz)Installing%2520GRUB%2520using%2520grub-install)

I fixed the problem by:
Booting on winxp install disk and ran fixboot from the rescue console.
Reooting Ubuntu install disk and choosing keboard and stopping just before the serious things (Ubuntu needs to load some modules and such). Could also have booted any other linux rescue disk...

Alt-F2 switches to a console
In the console I ran 
mkdir /mnt
mkdir /mnt/foo (actually redundant but anyways I always liked foo a lot...)
mount /dev/hda3 /mnt/foo
chroot /mnt/foo /sbin/grub-install /dev/hda

Tadaa. Now I wonder what happened to the good old i386 lore which said that you could install a bootloader two places. On the partition and in the mbr. I guess I have to find a grand wizard....

See also
[http://www.sims.berkeley.edu/~jhall/grub_install_hda1.html](http://www.sims.berkeley.edu/~jhall/grub_install_hda1.html)
which gave me the idea

---

### Post by DutchLau on 2005-05-12
Good job!  :grin: 

Happy to hear you fixed your problem!

"Jij wil knibbe" - It's about the only thing I know in Danish  :grin: 

DutchLau

---

### Post by mortensn on 2005-05-13
I'd recommend you to stop saying that,. Someone has pulled your leg.

---

