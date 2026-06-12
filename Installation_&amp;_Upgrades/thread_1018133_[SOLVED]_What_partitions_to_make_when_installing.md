---
title: "[SOLVED] What partitions to make when installing"
date: 2008-12-21
forum: Installation &amp; Upgrades
---

### Post by Aizawa on 2008-12-21
I read that,for easier upgrading of linux or switching distros you should make a separate partition (in this case the dude told me to call it /home, apparently) to save documents or music or whatever you want to save.. What should my partitioning table look like? I have 1024mb of RAM, and I've both read that I shouldn't make the.. Swap? Yeah, well, the swap partition any bigger than my RAM is. Someone else told me to make it twice as big as my ram (Max 4gb)..

Anyway, I do switch distros all the time, and it would be kind of neat to be able to have part of my hard drive dedicated for saving all that stuff. 
So my ram is 1024mb, and I guess I would like to have 20gb on that partition for saving stuff.. Soo.. Uh..

I really don't know how to work that partitioning table.

Sorry if this post is sort of.. cluttered

---

### Post by Partyboi2 on 2008-12-21
When you get to the partitioning stage of the install choose "manual" and create a ext3, / (root) about 10-15 gig this is for the system files with the mount point set to / and then create a swap partition (2gig) and finally a ext3  /home partition of 20 gig with the mount point set as /home.


Your / (root) can be smaller then 10 gig if you are limited with space.

---

### Post by skern03 on 2008-12-21
Try this: 5 GB for root (/), 1 or 2 GB for swap, and the rest of the drive for /home.

When you do an install/upgrade/reinstall, just partition with the same sizes, and reformat the root partition. Leave /home alone, and you'll be fine. BTW, use ext3 journaling file system.

> **Aizawa said:**
> I read that,for easier upgrading of linux or switching distros you should make a separate partition (in this case the dude told me to call it /home, apparently) to save documents or music or whatever you want to save.. What should my partitioning table look like? I have 1024mb of RAM, and I've both read that I shouldn't make the.. Swap? Yeah, well, the swap partition any bigger than my RAM is. Someone else told me to make it twice as big as my ram (Max 4gb)..

Anyway, I do switch distros all the time, and it would be kind of neat to be able to have part of my hard drive dedicated for saving all that stuff. 
So my ram is 1024mb, and I guess I would like to have 20gb on that partition for saving stuff.. Soo.. Uh..

I really don't know how to work that partitioning table.

Sorry if this post is sort of.. cluttered

---

### Post by Aizawa on 2008-12-21
But then I can't install with .deb:s? (Since they install to /usr/share or something..)

So then I'd have to do manual installs all the time..? I'm very new to Linux, as you might have guessed..

---

### Post by skern03 on 2008-12-21
Not sure what to tell you about the ".deb:s"... I just use the liveCD to install, and yes, you would be committed to a manual install. 

But really, after doing it both ways, I found the manual install much safer and better in the long run. Largely because if you do a complete "clean" install and let Ubuntu set itself up, you'll lose all of your settings and documents. 

With root (/) and /home on on their own partitions, you get to keep your settings. For example, when I reinstall/install Ubuntu with this setup, I always go back in and install the apps I like to use, like Amarok (love the lyrics script feature!) and Thunderbird. With my files and settings intact on /home, the apps come back up the way I left them. And, I don't lose my documents.

Now I'm sure there are other ways to do it - like copying your /home somewhere else, then copying it back. But why bother when you get the same thing with a partition? It's just easier.

Again, JMHO.

> **Aizawa said:**
> But then I can't install with .deb:s? (Since they install to /usr/share or something..)

So then I'd have to do manual installs all the time..? I'm very new to Linux, as you might have guessed..

---

### Post by Aizawa on 2008-12-21
Alright, this might seem stupid, but don't you install to the root partition? Like, /usr/share?

If that's the case Shouldn't you have like 10 or 20 gb for the /home partition, since it's just documents and settings?

---

### Post by skern03 on 2008-12-21
There are no stupid questions. We all start somewhere! 

When you install, you'll be prompted through the steps to partition a drive. The first partition you create is mounted as root, which is expressed as "/" in the dialog box. Normally, 5 GB is ample, but you can increase it if you want, even as large as the other post on this thread. If you have a small drive, say 20 GB or under, then definitely keep it to 5 GB. Ubuntu only takes up about 3 GB. So yes, you do install to the root. Make sure you click the Reformat checkbox and select, as mentioned before, ext3 for the file system.

The next partition you create and mount is swap. Set it to 1 or 2 GB, again depending on how big your drive is. There won't be any option to reformat.

The third partition to create and mount is /home. Unless you plan to install another OS, then just leave it at the remainder of the drive space. Use ext3 again, and in the mount drop-down, choose /home. This is like the documents and settings folder in Windows XP. It's where user settings and documents are kept. For example, you would have a /home/aizawa folder, if that's your login name; if you set me up as a user on the system, I'd have a /home/steve folder.

I'm including a screen shot that shows a 10 GB drive partitioned more or less as described above. Since I was a little short on drive space, I set the root to 4 GB. One of these days, I'll treat myself to a new drive! ;-)


> **Aizawa said:**
> Alright, this might seem stupid, but don't you install to the root partition? Like, /usr/share?

If that's the case Shouldn't you have like 10 or 20 gb for the /home partition, since it's just documents and settings?

---

### Post by Aizawa on 2008-12-22
But if I only have 20 gigs for the root partition I wont be able to install many programs, will I? Because .deb packages install to /usr/.. What I meant with manual installs was, do I need to download tarballs and install them to my /home folder? Because as I said 20 gigs is not very much. My drive is 160gb total, though.. You might have thought it was smaller.

Just to clarify, this isn't a usb drive I'm installing to. I dunno if that matters though.

---

### Post by skern03 on 2008-12-22
It's a little confusing that there is a folder called /root, but we all refer to "/" as root. You are installing the OS to / and that includes /usr and all the other directories.

Regarding the amount of space to dedicate to the OS, if you want to include more, by all means, go ahead. I'm just not sure you need all that much, but then, I don't know what you plan to install. I have OpenOffice, Amarok, Foxfire, Thunderbird, a slew of games and more, and I still have plenty of room with a 4 GB partition for the OS. If you're coming from windoze to Linux, you'll be surprised at how little space is taken up by apps.

You're right - I did misunderstand what you meant by manual installs; I thought you were referring to manual partitioning of the drive!!

Anyway, I'm not that familiar with the installation via debs tarballs. I usually can find what I want in Synaptic Package Manager; if necessary, I'll figure out how to add another source, and then install from there. Or, alternatively, you can use sudo apt-get install <my package>. You'll still need to ensure the source is available.

But if you need to install the way you describe, yes, you can put the tarballs on your desktop or wherever - that'll be on /home - which should be the largest partition.

So your scheme could look like so:
20 GB / (root) for the OS
2 GB swap
138 GB /home



> **Aizawa said:**
> But if I only have 20 gigs for the root partition I wont be able to install many programs, will I? Because .deb packages install to /usr/.. What I meant with manual installs was, do I need to download tarballs and install them to my /home folder? Because as I said 20 gigs is not very much. My drive is 160gb total, though.. You might have thought it was smaller.

Just to clarify, this isn't a usb drive I'm installing to. I dunno if that matters though.

---

### Post by Aizawa on 2008-12-23
Alright, sweet, thanks!

---

