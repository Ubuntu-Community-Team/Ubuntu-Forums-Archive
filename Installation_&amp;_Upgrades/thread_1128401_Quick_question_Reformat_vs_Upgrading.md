---
title: "Quick question: Reformat vs Upgrading"
date: 2009-04-17
forum: Installation &amp; Upgrades
---

### Post by janthonywj on 2009-04-17
I'm having some issues with my laptop that randomly developed where Kubuntu completely freezes up except the mouse still moves. It happens somewhat randomly. It can happen 2 min after boot up, or 20 min, but it WILL happen. Usually during window movements or file movements or sometimes just out of no where. Anyone seen this?

Anyway, I think I originally installed with Kubuntu Jaunty Alpha 3 or 4. I've downloaded the RC and I'm about to reformat using that. 

My question is does it matter very much whether I redownload and reformat next week when the official release comes out, or will updating be equivalent?

---

### Post by Herman on 2009-04-17
Updating is equivalent. If you have been getting all your updates then you already have the latest software and you'll be wasting your time and bandwidth re-installing.
Unless you happen to like backing up and re-installing, some people do.

---

### Post by janthonywj on 2009-04-17
I was thinking that possibly the filesystem would be updated or something that would make it worth while, something that is probably more difficult to update without a clean install. I think my problems with it hanging up were with the very early stages of the ext4 filesystem. This time I still used the ext4 filesystem for root, but left home as ext3. I've heard some bugs have been worked out with ext4.

We will see if it works better, or it's very possible that have have some hardware issues.

---

### Post by Herman on 2009-04-17
I see, now that you have explained it that way your idea makes sense. 
I'm using a couple of test installations with the ext4 file system and I must say I'm very impressed with ext4 and I haven't had any problems with it at all myself.

Well it only takes half an hour to re-install, and it won't do any harm. I'm not sure if it'll actually help or not, but it might. Restoring all your files and customizing and tweaking your operating system is what takes the most time. 

You can save yourself a little time and some internet bandwidth by making a backup of all of your .deb files in /var/cache/apt/archives.
```
sudo cp /var/cache/apt/archives/*.deb /media/disc
```Where: you have a USB disk or some other kind of disc mounted at /media/disc with a little space to store a backup of your .deb files in.

After you re-install, you can copy all of your saved .deb files into your new /var/cache/apt/archives/ before you get updates and add software.
Then just get your updates and add your software in the same way you always do, but you'll find the process will be a lot quicker because you won't need to wait while your computer re-downloads most of it from the internet. It'll already be there in your /var/cache/apt/archives/, ready to be installed.

That little trick should speed things up for you quite a bit. :)

---

