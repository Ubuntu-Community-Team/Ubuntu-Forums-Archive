---
title: "Noob with GRUB &amp; Partitions"
date: 2009-07-11
forum: Installation &amp; Upgrades
---

### Post by Narufox on 2009-07-11
Hi, I recently decided to format/reinstall XP but while I'm at it place an Ubuntu instillation on there as well. I can't use discs, and I have a 600gb external USB HD to cover what I can't achieve with my 40gb Internal HD, but I have a question about partitioning. Here's the planned setup:

40gb: 15gb Linux partition (ubuntu), 15gb NFSC (windows)
600gb: Not quite sure.

The main harddrive will store the OS's and I'll use the external for media files/documents/games until I can replace it with another Internal. I'm not quite sure how to partition it, can the files be available to linux and windows? I'm quite confused lol

Also, I'm not sure how to start an Ubuntu Network Partition through GRUB (once again, no burnable discs @ the moment so the easiest option I can think of is a Network Installation) and last time I tried it had a bunch of errors half way through the download. 

Help please!! :p

---

### Post by earthpigg on 2009-07-12
you are a bit computer savvy, right? can point and click your way around graphical interfaces without having your hand held through every step as long as it is somewhat intuitive?

easy method:

1. stop thinking about grub. if you do things in the correct order, you will not have to worry about it.

2. back up whatever you currently have on your internal hard drive.

3. install Windows XP. run defrag as many times as you have patience for.

4. pop the ubuntu cd in. manual partition. resize windows partition down to 20gb. make a 2gb partition for linux-swap. make an 18gb partition, ext3 or ext4, set the mountpoint to /, and flag it as bootable. (<--- this is where your ability to point and click around a bit and figure things out will come in handy. its all pretty intuitive, if you know the key words to look for... like mount point and ext3 and whatnot.)

5. are you nearly always going to have that external hard drive plugged in? if so, we may as well bookmark it in the file manager. once ubuntu is installed, go to places -> computer -> navigate to your 'pictures' folder on the external hard drive -> bookmarks -> add bookmark. remove the default bookmarks if you like, since we wont be using them. keep in mind that the more things you have bookmarked, the slower the file manager will be when it starts up.


ubuntu will be able to read the windows partition, windows will not be able to read the ubuntu partition. ubuntu will be able to read your external hard drive. if windows can read your external hard drive now, it will continue to be able to do so... we aren't going to change your external hard drive at all.

other people may post in this thread telling you that you should use your external hard drive as your /home. if you want that external hard drive being unplugged to render ubuntu unbootable, then go for it.

ext3 vs ext4? ext3 is tried and true, ext4 is wave of the future. flip a coin or google search.

why 2gigs for linux-swap? ask a dozen different people, and they will give you a dozen different 'rules of thumb.' got 4 gigs of ram? dont bother with a swap. got 500mb of ram? make it 2 gigs.


questions? :P

---

### Post by Narufox on 2009-07-12
Hi, thanks for your help.

Problem: I can't use discs. Rather, I don't have any burnable CD's (It's not that I can't afford them, it's that it's 7 miles to the store and I don't have a vehicle for the weekend and I really miss Ubuntu)

No doubt I'll use ext3, as it's stable. And I have 1gb RAM so 2gig Swap partition right? Also, I have to format the external as I'm using it to install XP on my internal. It's somewhat complicated but it's the only way without a disc (I don't have an XP installation CD, but I have that covered). So just leave the media partition on the external as fat32 and Ubuntu will recognize it? Cool. And I'd rather use an internal partition for /home because it's way faster, and it won't always be connected like you said and I still want to use Ubuntu, heh. 

I'm still a bit confused about installing Ubuntu through a netboot, though.

---

### Post by earthpigg on 2009-07-12
got a thumb drive handy?

the ubuntu wiki is outstanding.

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent#Installing%20Ubuntu%20on%20USB%20drive%20using%20Windows](https://wiki.ubuntu.com/LiveUsbPendrivePersistent#Installing%20Ubuntu%20on%20USB%20drive%20using%20Windows)

you can use your external hard drive for that as well, if you want.

2 gig swap will be fine.

you dont need to use a seperate partition for /home at all, if you dont want. it does have many advantages - but since you will only have 20 gigs for the entire ubuntu install, i would not recommend it... not always easy to know in advance how much you will need for a dedicated /home partition. some software takes up more space on /home than others, and who knows what software specifically you will find yourself interested in using?

---

