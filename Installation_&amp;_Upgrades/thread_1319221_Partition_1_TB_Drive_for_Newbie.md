---
title: "Partition 1 TB Drive for Newbie"
date: 2009-11-08
forum: Installation &amp; Upgrades
---

### Post by Netlink on 2009-11-08
Guys
Newbie to linux from Windoz World :-)
I am trying to setup a server and of course I have chosen Ubuntu.
 
Server Specs.
**[COLOR=red]Intel Core 2 Quad Q9300 2.5GHz[/COLOR], RAM 6GB DDR2, [COLOR=red]1TB HDD[/COLOR], DVDRW,**
 
I want to Dedicate the whole 1TB drive to Ubuntu (what can I say, storage is cheap nowdays :-))
 
It is a new server, I bought 2 with intent on Running Windows server 2008 on both. The other Windoz works fine but I have decided to put Ubuntu on this one. I need Linux for this project that is why I dove into the Ubuntu world.
 
Here is what it will be doing. It will be a video server, so that huge 1TB HD needs to be patitioned correctly to hold my videos. I already have over 200GB of videos and once I set this up the size will Slowly grow. 
 
I will host only two domains on it. No outside clients so very few people will have access to mess with my settings.
How can I "properly" partition it?
 
**1. I need to create a Separate Ubuntu Home partition in case things go wrong later down the road it makes it easy to just reinstall without loosing my other files.**
 
**2. Is it best to, Partition then install or install and Partition?**
Being from windows world I don't usually worry about partitions coz I can Dice them and slice them anytime I need without loosing data. I know folks here can do same in their sleep on Ubuntu but remember I a newbie, I am bound to mess up alot.
 
I already played around with GParted and you guessed it, I had to reinstall Ubuntu 3 times! Works slightly different than my Windows "Paragon Partition Manager", Well now I know about Live CD!
 
Main Question is this, Can someone Guide me on how to best slice and Dice my 1TB Drive. I will have only Ubuntu and of course the other server stuff. No other Destro or any of that .....
 
**Here is how I had it when Windowz 2008 R2 was still running on there**
C:\=125 GB
D:\=50 GB
F:\=400 GB
G:\=400 GB
 
**Breakdown**
C:\=Operating System
D:\=OS Backup
F:\=Domain-1
G:\=Domain-2
 
I had secondary drive for backup.
I use vitual Directories in IIS(Apache) to dump stuff for each domain in their respective partition.
 
Anyone willing to help me Slice and Drice my Drive to neatly accomodate Ubuntu Server? 
Most of the space on the server will be used by the Video files I store.
 
Sorry for being so long winded but being a tech I prefer having too much information than having none at all. Trust me I have received those emails "I can't login"

---

