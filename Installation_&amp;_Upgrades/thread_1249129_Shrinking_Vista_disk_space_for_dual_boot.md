---
title: "Shrinking Vista disk space for dual boot"
date: 2009-08-25
forum: Installation &amp; Upgrades
---

### Post by rotithor on 2009-08-25
I have a sony VAIO laptop on which I am trying to dual boot Ubuntu 9.04 with Wondows Vista Home premium. I saw the dual boot video which suggested the first step to shrink the C: space to create a parition for Ubuntu.
On my Sony laptop I have 127GB of free space (55G used). However when I click computer->manage->shrink it says only 94MB available to shrink with a message:
"Size of available shrink space can be restricted if snapshots or page files are enabled on this volume"
Obviously, I need more than 94MB for Ubuntu. What are my options?
How do I make more shrink space available? what application is enabling snapshots/page files? can this be changed?
For dual boot; instead of trying to shrink via Vista to create empty partition, can I use the installer and use
"install side by side option" and create a partition while installing like that done with Windows XP dual boot? would that cause problem for Vista when it loads? is there any post clean up needed for Vista?
Will appreciate advice on this question
Thanks

---

### Post by raymondh on 2009-08-25
> **rotithor said:**
> I have a sony VAIO laptop on which I am trying to dual boot Ubuntu 9.04 with Wondows Vista Home premium. I saw the dual boot video which suggested the first step to shrink the C: space to create a parition for Ubuntu.
On my Sony laptop I have 127GB of free space (55G used). However when I click computer->manage->shrink it says only 94MB available to shrink with a message:
"Size of available shrink space can be restricted if snapshots or page files are enabled on this volume"
Obviously, I need more than 94MB for Ubuntu. What are my options?
How do I make more shrink space available? what application is enabling snapshots/page files? can this be changed?
For dual boot; instead of trying to shrink via Vista to create empty partition, can I use the installer and use
"install side by side option" and create a partition while installing like that done with Windows XP dual boot? would that cause problem for Vista when it loads? is there any post clean up needed for Vista?
Will appreciate advice on this question
Thanks

Hello,

Windows has the habit of placing files all around the partition.  Some of them are considered (by windows) as immovable files (i.e paging, MFT, etc).

Defrag and back-up.  See this [HOW-TO]("http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/").

Gparted can shrink as well.

Yes, you can use ubiquity (the installer) to set it up for you (side-by-side / guided resize)

Back-up.

---

### Post by NickArcifa on 2009-08-25
Hey  mate,

Vista's inbuilt option to shrink a hard drive is quite good, but unfortunatley it only normally lets you shrink a small amount even if you have a large amount of hard drive space left.

 OPTION 1: probably the quickest and easiest
I had a similar problem. This is what i would do. 
1. Download and Burn a Live CD of ubuntu 9.04 prefferabley or use a CD from The ubuntu website. 
2. Boot ubuntu off the cd, as your laptop is new you shouldn't have to alter your bios in anyway, but if it wont boot then get acess to you bios (when you first boot up your computer it should quickly flash and tell you a key to acess bios, usually f11, f12 or delete) and look for an option to change boot order and set the CD drive first. 
3. Let ubuntu load after pressing try ubuntu without changing anything on your computer (the first ubuntu live cd option). 
4. Once it has loaded go to system > administration > Partition editor. 
5. select your hardrive here and click the shrink button up the top  
6. specify the "new size of the hardrive" eg hardrive minus new partiton size. 
7. after shrinking your hardrive which will take a while, you should see unallocated space 8. click in this grey space and make a new partition formatted in ext3 or ext4 (i would pick 3 for stability). 
8. now close GPARTED (partiton editor) and click the install icon and follow the installation guide. 
9 IMPORTANT: make sure u specify which partition you install ubuntu on and pick the ext3 partiton you just made and set the mount point as "/", you might aswell click the format this partiton again just incase any errors happened during partitioning.

 OPTION 2:
1. find a free or trial partition editr for vista and follow the same type of steps as above.

I would rather do it with GPARTED as it as just easier and works quite fast and well, partition managers that work on vista are normally very technical, slow and can cause a BIG HEADACHE.

After install you will probably have to edit your menu.lst file, easy tutorials can be found on these forums, or a quick google search, if you don't understand i could do the best i can to help you out 

Hope this helps,
Nick Arcifa
email me at [email]nickarcifa@aapt.net.au[/email] if you need more help or just post here

---

### Post by drs305 on 2009-08-25
A word of caution on the "side by side" option during the Ubuntu install. Many new users have had problems with the partitioning step (4). If not done correctly, the user will end up with a 2.3-2.5GB partition, which is too small to run Ubuntu.

Check out this link on how to accomplish the "side by side" step correctly:
[http://ubuntuforums.org/showthread.php?p=7658271#post7658271]("http://ubuntuforums.org/showthread.php?p=7658271#post7658271")

Welcome to Ubuntu and the Ubuntu forums.

---

### Post by rotithor on 2009-08-26
Thanks for the helpful responses. I tried suggested steps for shrinking Vista partitio, ran into two issues:
-Even after trying the two defrag utilities and "perfectdisk" my Vista disk shows only 5.9G available that is not going to be adequate
-If I tried to shrink 5.9G via vista I get an error with Vista asking me to close and reboot all the time

I would like to try the other suggestion, that is using the installer on the Ubuntu 9.04 CD to create a partition and load Ubuntu. If I fire that up, when it goes to the partition part:
-It says The computer has no OS on it, that is, it does not detect Windows Vista present
-It shows two paritions /dev/sda1 (7.5G) and /dev/sda2 (178,8GB) and it would carve a new Ubuntu partition from sda2 in "side by side" mode.

When I did dual boot with XP, it had detected Windows XP in the first parition and installation was smooth. My question is:
-should it have detected Vista in the partition?
-Is the action of the installer/loader diferent had it detected Vista OS vs what it is currently seeing?
-If I carve Ubuntu in sda2 and install it there, will I run into problem with boot loader later because of this causing windoes Vista to not boot?

Don't want to land in no man's land so would like to get advice if this path would go as smothly as my XP dual boot installation or if I need some steps after Ubuntu installation to clean up to be able to dual boot and what those steps are.
Thanks in advance for suggestions.

---

### Post by drs305 on 2009-08-26
I don't use Vista so I won't go into specific  solutions, but I would recommend NOT doing anything with the Ubuntu installer until the partitioning issue is resolved. If Ubuntu doesn't see the Vista install I don't see anything good happening when it tries to take some space to make the Ubuntu install (other than you will probably get Ubuntu installed :-) ).

---

### Post by rotithor on 2009-08-26
Yes that is my concern, so the question is:
-why does the Ubuntu loader not see windows vista loader? all the tutorials and videos on dual boot with Vista that I have seen show that the partitioner does see  Windows Vista loader
-Is there a way to make the loader see Windows Vista loader so it may do the right thing? have others seen this problem? known soultions?
-My suspicion is that /sda1 would have the Vista loader
I agree that if the loader does not see it it will likely land me into no-man's-land with vista boot. 
Thanks

---

### Post by Mark Phelps on 2009-08-26
It's good that you're being cautious in shrinking your Vista OS partition.  Not everyone is.

The link below contains some suggestions on things you can do to try to get more space out of the Vista OS partition:

[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/]("http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/")

---

### Post by BiiPiiGii on 2009-08-27
Isn't there a way to use the wubi installer that comes on the ubuntu disc for a dual boot? Is that the better route to take other than shrinking the disk with either gparted or something else?  I ask because I'm trying to do that for my GF right now.  I'm installing windows 7 [beta] on her sony vaio and she wants to dual boot with Ubuntu because you can have hello kitty stuff [don't ask she's a 19 year old asian chic, apparently hello kitty is in till you die].  I'm not going to run Ubuntu on it though until I know what's going on with the partion shrik ordeal though..

---

### Post by Mark Phelps on 2009-08-27
Two things ...

First, Wubi is not intended to be a permanent solution.  It's a way to temporarily "try out" Ubuntu to see how well it works for you and how much you like it.  If you decide to keep it, you should then move it to it's own partition in a true dual-boot mode.

Second, Wubi is only certified to work up through Vista.  It's not certified for Windows 7 yet -- that's still in development.  So, installing it in Windows 7 is likely NOT to work.

---

### Post by rotithor on 2009-08-27
I have considered wubi installer option, but the paritioner does not see my windows Vista loader (says no OS installed) so I am a bit skeptical about that route. I think it will create a partition but Vista will have problem booting that way.

---

### Post by Mark Phelps on 2009-08-27
> **rotithor said:**
> I have considered wubi installer option, but the paritioner does not see my windows Vista loader (says no OS installed) so I am a bit skeptical about that route...

You're right to be skeptical...

You could try a couple of other approaches.

First, in my experience, the Alternate CD did a better job of detecting other OSs on the drive.  It's text-based install, so it's not as fancy, and I don't personally know if it also supports Wubi, but if it does, it might see the Vista install.

Second, if you want a true dual-boot, you could download and burn a GParted LiveCD, burn that, boot from that, and see if IT sees your Vista install.  If it does, after you use the Vista Disk Management tool to shrink the Vista OS partition, you could boot from the GParted LiveCD and use it to create the Ubuntu partitions, and then boot into the Ubuntu CD and choose manual partitioning to install there.  That will minimize the risk of your accidentally overwriting the Vista partition.

---

