---
title: "recover data from partially overwritten partition (USB*HD)"
date: 2011-10-07
forum: Hardware
---

### Post by CryptKeeper777 on 2011-10-07
I made the stupid mistake to overwrite the partition on my external USB HD where I store data. Fortunately I realized my mistake fast enough, so just a little bit of the partition was already overwritten, so I suppose there's a good chance to recover quite a bit of the data. (and if not, that's not the end of the world, but I want at least give it a shot)

The story: I've just freshly installed Ubuntu. Before that, I saved the old installation in an image on a USB HD using fsarchiver, and I also saved my home folder unarchived to easily copy the data to the new installation. Unfortunately, in the process of rsyncing the home folder to and fro I somehow got rid of all hidden files. Not a huge problem, but I want at least my .vimrc and .bashrc back. So I decided to extract the old installation on my 500GB USB HD which is normally used to back up the data (< 500GB at the moment) on the 700GB data partition on my 1TB USB HD. Unfortunately I made a mistake typing the fsarchiver extraction command: I typed dest=/dev/sdd2 instead of dest=/dev/sdb2! sdd is the 1TB-HD and sdb the 500GB HD. I have several partitions on the 1TB-HD, but of course, sdd2 is not just any, but the 700GB data partition! I almost immediately realized my mistake and stopped fsarchiver, but the partition was already partially overwritten. But I think most of the data should still be recoverable.

But how can I recover the data? I did some googling but didn't find an exact solution, so I ask you guys. Please help me! :popcorn:

The data partition was formatted in FAT32.

---

### Post by WasMeHere on 2011-10-07
Hello CryptKeeper777,

I guess from your post, that you have experience of backup, partitioning etc. But you had bad luck. This is a reminder to all of us to keep all important data in at least two places.

There are tools (e.g. *photorec*) that ignore the file system and go after the underlying data, so it will still work even if your media's file system has been severely damaged or reformatted. This way I have recovered photos from a USB stick. It is certainly possible to operate on a huge disk and with other file types. Maybe it is not very convenient, but definitely possible to recover files.

I suggest you copy or clone whatever is readable now (the other partitions) from your damaged disk before doing risky things with it. I think of trying to recover or re-create the first part of the partition in order to see the files that are not overwritten. I don't know if it is possible, but it is certainly possible to do more than I know.

Good luck
Olle

---

### Post by CryptKeeper777 on 2011-10-07
Photorec looks quite perfect. The only problem left is that the partition is 700MB big and I have no other HD at hand with more than 500GB. Although I only stored about 400GB or less of data on the partition, more data could be recovered (deleted files), if I understand the whole file system and storage stuff correctly. Is there a way to switch to another storage device once the 500GB HD is filled up (if it ever gets filled up), or does Photorec that even automatically?

I tried to google for that but it's a bit difficult to formulate...

---

### Post by WasMeHere on 2011-10-07
Would it be worth the money to get a new HDD that is big enough? You will probably find ways to use it later on, for example as a second backup drive.

---

### Post by CryptKeeper777 on 2011-10-07
No at the moment that's not really an option, the data isn't important enough for that. I'll need another HD sooner or later, but at the moment it's not really necessary. 

But I installed PhotoRec, started it to see whether it works, and it does, like a charm! Only problem is that all filenames and directory structures (though I'm not really sure yet about the latter) are lost, so I have to go through all recovered files manually, but whatever.

The good thing is that I have a lot of MP3 files on the HD which I don't need, so I can continuously delete them. Looking at the recovered data during the recovery should solve the storage problem (500 vs. 700 GB). 

Thanks for your fast help!

---

### Post by WasMeHere on 2011-10-07
Yes, it is hard work to restore all filenames and directory structures. I'm glad that you can manage to use your small HDD by deleting mp3 files 'on the fly' :-)

Please mark the thread SOLVED if/when you are satisfied!

Have fun
Olle

---

### Post by CryptKeeper777 on 2011-10-07
Id doesn't recover the directory structure. It saves the recovered files in different folders, but it looks like it fills the folders up until they contain about 500 files and then starts a new one.

It's actually not that bad that this happened because there was much on the HD that I didn't need anymore anyway, and other stuff is on my brothers computer.

---

