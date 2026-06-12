---
title: "Data off of a broken MAC HD"
date: 2011-04-09
forum: Hardware
---

### Post by Khodeir on 2011-04-09
Hey all,

I'm not sure this is the right spot for this post, but here goes... 

I have a broken laptop hard drive from an old macbook and a ubuntu pc with which to recover the data from it. Now, I thought this was gonna be pretty straightforward. I was actually just gonna copy the home folder (documents, videos, music, pictures, etc) to my pc and then simply copy that to a new hard drive (when i get off my *** and buy it). 

Well, first of all, the permissions on this drive are all ****** up. I don't even get read privileges. Secondly, as soon as i looked at this root drive i got greedy and figured "Why not take a complete image and restore it on the new drive?" This is where it got annoying. 

I used this command to begin with 

```
dd if=/dev/sda2 conv=noerror,sync of=MacHD.img bs=512
``` 

It started off at 9Mbps so i thought it must have been so goddamn slow because of a hardware problem. I let it run to no avail because sooner or later i get an input/output error and it all stops progressing. So i killed it.

Then, I figured why not break it up into bits so that i can resume from where i left off if it all goes to **** again:

```
dd if=/dev/sda2 conv=noerror,sync | split -b 2000m
```

No luck.. it slows down gradually to about 2.7Mbps and then halts. 

Fu*k dd! 

So I hit the forums and found this: [http://ubuntuforums.org/showthread.php?t=890202](http://ubuntuforums.org/showthread.php?t=890202)

Pretty simple, all i have to do is copy the whole drive to my pc, right?

```
sudo cp -r /media/Macintosh\ HD /usr/MACHD/
```

I let that run for a while and when i got impatient, I killed it and used the GUI (sudo nautilus)... 12 hours - 2 Mbps... goddamn!

I don't wanna run it for 12 hours only to find that the **** i copied isnt bootable. My question is:


[SIZE="4"][CENTER]Skip to question if you don't wanna read my blabber![/CENTER]
[/SIZE]

If you copy the folder in which a drive is mounted and then have dd make an image of that folder, is it still bootable? Also, is there a reason that my SATA drive is copying at 2Mbps? Is there anything i can do to bumb that up to.. i dunno.. 2 Gbps? :D

Thanks, 
Khodeir

---

### Post by coffeecat on 2011-04-09
With regard to the permissions problem, the permissions on your Mac HD are not messed up. The reason for the access denied problem is that your UID in MacOS is probably 501 and in Ubuntu 1000. Ditto for the GIDs (group IDs) Also, the home folder on the Mac probably has no "other" access allowed. MacOS and Linux use the same system of Unix permissions.

The solution is simple. Just use a 'gksudo nautilus' file browser to navigate into your Mac home folder and subfolders. If you use a Microsoft filesystem to copy to you can drag and drop into an ordinary nautilus browser. If you use a Linux filesystem, you'll need a second 'gksudo nautilus' and your files will probably then be owned by root once they have been copied. That's easily fixed with a recursive 'sudo chown', and that's why it's probably easier to copy to a Microsoft filesystem such as NTFS or FAT32.

dd is slow because it copies every byte, even those unused by the filesystem. It won't speed up even if you swear at it. :wink:

I guess cp is slow because the Linux hfs+ driver won't be as efficient as the Mac one. It has had to be reverse-engineered. Which means that when you use the GUI to copy as above, you'll probably find it to be slow as well.

---

### Post by Khodeir on 2011-04-09
Thanks for the reply, Coffeecat. You were, of course, right about browsing as root. It worked like a charm :D(so glad to see my files are intact). I've kept the gui transfer i talked about going and so far it has gotten 38.6 GB from a total of 143GB... 7 more hours... think i should keep it going? 

My main goal is to let dd loose on the copy of the drive and make a bootable image.. is this even gonna work?

---

### Post by coffeecat on 2011-04-09
> **Khodeir said:**
> My main goal is to let dd loose on the copy of the drive and make a bootable image.. is this even gonna work?

I don't know. If you can run MacOS on that drive - even if it means putting it in another Mac - you could install Carbon Copy Cloner to make a clone. CCC is free - [http://www.bombich.com/](http://www.bombich.com/) - and although slow it's quicker than dd.

---

