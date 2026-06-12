---
title: "how safe is the partitioner"
date: 2009-03-08
forum: Installation &amp; Upgrades
---

### Post by gbswales on 2009-03-08
I just tried the install from the live CD and I am confused when it gets to the partitioner. This does not seem to show me what drives/partitions just the one bar that shows how ubuntu configuration will be set up - going to manual didnt help me much.

For now I have used WUBI to install but the problem with this is that while I can access the content on my second hard drive I cant access my documents etc on the C drive (preumably because it is running inside a file on that drive) 

I do back up stuff as well as having a clean windows install ISO - however I dont have storage large enough to make a complete ISO of my current C:/ drive therefore it would be a lot of work rebuilding my drive if something goes wrong - can someone tell me for certain that the first partitioner option in the latest ubuntu distro (live cd) will not trash my windows system and is it easy enough to set ubuntus total space to 30GB

Also is it easy to uninstall if I need to - this is my third or fourth attempt - to install but the first on my live PC all the others were on an old PC and I gave up with things like finding drivers for wireless adapters

--------------------------------------------------------------------------------

---

### Post by dstew on 2009-03-08
You can easily trash your Windows system with the Ubuntu partitioner, or with any partitioner for that matter. The usual problem is letting the partitioner "use entire disk", which tells it you don't want to preserve your Windows.

I like to partition before I start installing. I use the [GParted Live CD]("http://gparted.sourceforge.net/livecd.php"). The same program may also be present on your Ubuntu Live CD (System --> Administration --> Partition Editor). I partition before I install because it just seems more relaxed. Since you are doing just one thing (partitioning) you give it your full attention, and I think you are less likely to make a fatal mistake.

---

### Post by Neo_The_User on 2009-03-08
A program is only as safe as the person who is using it.

---

### Post by zvacet on 2009-03-08
Partitioner is safe if you don´t select "use entire disc" option.As **dstew** said you can partition your HD with Gparted live CD and after that you can not be wrong.When you doing partitioning make separate home partition,because you will find it very useful.

---

