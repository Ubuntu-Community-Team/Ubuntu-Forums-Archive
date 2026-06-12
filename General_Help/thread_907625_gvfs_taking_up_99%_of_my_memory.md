---
title: "gvfs taking up 99% of my memory"
date: 2008-09-01
forum: General Help
---

### Post by chez17 on 2008-09-01
My system says my 10GB hard drive is full after a basic install from the Live CDs and a couple small programs. I was trying to download the Red Alert disks that were just released and it says I am out of memory. This is not possible. I downloaded and ran xdiskusage and it says the /home/dave/.gvfs is taking 99% of the memory. I did some research and found this post:

[http://ubuntuforums.org/showthread.php?t=789570](http://ubuntuforums.org/showthread.php?t=789570)

but the solution was too advanced for me. Can someone either tell me a new solution or translate the one above into noob terms?

Thanks for your time,
Dave

---

### Post by eggdeng on 2008-09-01
As far as I can see, all the poster did (which might be relevant to your situation) was remove the file which seems to be full. If you want to follow in his steps, open a terminal and copy and paste
```
sudo umount gvfs-fuse-daemon
```
then
```
sudo rm -r /home/username/.gvfs
```
where username = your username. Copy & paste the command rather than typing it yourself as any mistake might take your system with it.
I know nothing about gvfs so I can't guarantee a)that this will work, b)that it won't damage your system. If anything goes wrong, I have never met you before. 8)

---

