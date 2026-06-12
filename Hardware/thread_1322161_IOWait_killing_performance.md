---
title: "IOWait killing performance"
date: 2009-11-10
forum: Hardware
---

### Post by finalhit on 2009-11-10
I'm a bit new to linux so I have no idea to debug this, but once in a while, my IOwait would skyrocket (i have system monitor applet running on one of my panels) and it would just drag my computer's performance down.

I don't think this is a hardware problem, because I dual-boot with xp in the same computer, and the problem doesn't seem to exist. (i really like ubuntu, and I don't want to use XP, but this is really quite a frustrating phenomena)

I don't multitask as much, and my memory usage seems below my existing memory (albeit a mere 512 mb). I typically stay below that.

I run eclipse/firefox/apache when I'm working (mysql is run on a separate computer). Or when I'm just using the computer for leisure, i just run firefox/totem/mplayer and the flash plugin.

After some usage, IOwait would just explode, and cause the computer to freeze, and makes the computer intolerably unresponsive. I'm not sure if this is a driver or application issue, so any pointers would be appreciated.

I really like ubuntu, and try to avoid going back to XP.

---

### Post by atwskris on 2009-11-19
Hi finalhit, I have been having a very similar ( if not the same ) iowait issue.
I also run eclipse and firefox + a vmware server for a dev server.

Randomly the iowait hits 100% and stays there for a quite some time ( 15 to 30+ minutes ). I usually have to start killing processes until it calms down enough to start over, restart the same applications and then continue on till the next random iowait bomb.

I have tried to install iotop and watch for any process that is causing an issue, but they all appear to be doing just fine, nothing stands out from the crowd.

There is very minimal cpu usage, ram is at %50 and the computer is more the capable, Intel Dual Core 3.0 Ghz , Corsair 4GB Ram 1066 Mhz, 2 Seagate 1TB 7200.12 Hard drives with RAID 0 OS partitions and a RAID 1 partition for the Home directory. The VM Ware WinXP installation is running off a completely separate hard drive ( 640GB Seagate ) .. need more info?

I would have to agree that this all starting becoming an issue after an upgrade to ubuntu 9.10 from 9.04. I really, really don't want to do an fresh install, but it is starting to appear that  way very quickly.

The ubuntu installation is not vanilla, but apart from changing the swappiness to help keep things in RAM ( noticed alot of swap being used for no reason when the Ram was only 25-50% in use ) I have not gone poking around to much. 

I have done a significant amount of googling for iowait on ubuntu 9.10 , firefox iowait, even as far as jfs iowait and swap iowait. There appears to be quite a few posts of this iowait performance killer, but no concrete answers.

Edit: I am running ubuntu 9.10 64 Bit ( forgot to mention that )

Hopefully someone has some insight, please let me know if there is any specific information you would require to help diagnose this issue.

Thanks in advance!

---

### Post by movieman on 2009-11-20
High I/O wait has been a known problem for several kernel versions, but I thought it would have been resolved by 9.10. One way we reduced the problem at work was to mount the disks with the noatime option so that they're not continually having to write out access time data; that's one of the big killers if you're reading a lot of files.

So far I've only seen high I/O waits in 9.10 when accessing NFS directories, when it can get pretty high.

---

### Post by atwskris on 2009-11-20
Hi movieman, Thanks for the reply!

I will have to check out the NFS mount I have setup for my VM-Ware dev. server ( also running ubuntu ) and look how to mount it with the noatime option. ( will have to research this is not bad thing for svn working copies )

There is lots of little files, svn + code, in the NFS mount. So the noatime may have a significant impact.

I will have to double check / run some tests that this iowait problem isn't happening when the NFS is not loaded, most of the time I am developing so everything is loaded up.

Is there any tools to use for watching the NFS mount / traffic / io caused by NFS ..? iotop doesn't seem to be giving me enough / the right information?

Again, Thanks for the reply, at least this gives me another direction to checkout!

---

### Post by movieman on 2009-11-20
I'm not sure whether noatime is relevant for NFS mounts, or whether it would have to be configured that way on the server rather than the client: I guess your client might be waiting for a server whose disk is slow?

Ah, yes, it does look like you can set noatime on NFS mounts, as Google found this page:

[http://blogs.techrepublic.com.com/opensource/?p=64](http://blogs.techrepublic.com.com/opensource/?p=64)

I'll have to try that on my system too :).

---

### Post by atwskris on 2009-11-20
That is a great post you found!

Looks like the nfsstat might be a useful source of information, also might be worth while to check out the number of threads the rcp is currently using. 

I am sure 8 ( the default ) should be more then enough for what I am doing.

I don't think I will need to increase the read/write block sizes, with the svn and multitude of small files, 8K should be enough?

Even if this doesn't rid the iowait problem will probably give me some better response times on the NFS mount.

At work now, so will have to try it out when I get back home, will let you know.

---

### Post by robertock on 2009-12-22
I had this same problem today and none of your solutions have worked. So I verified my /etc/fstab file and I found my problem: one of the directories (mount points) I've configured in the file doesn't exist. So after I create the directory, everything just back to normal. No more IOWait.

---

