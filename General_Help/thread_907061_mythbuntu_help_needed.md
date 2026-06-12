---
title: "mythbuntu help needed"
date: 2008-09-01
forum: General Help
---

### Post by scubydoo on 2008-09-01
First of all i'd like to say hey and thanks you to anyone who can point me in the right direction.  I'm totally new to ubuntu and know VERY little about linux.  I'm familiar with windows and have always wanted to try out linux.  I was surfing the net and found out that it is possible to create a PVR with mythbuntu.  That really caught my eye and made me want to learn about linux.  sorry for the long intro, but I felt it best to give background info. i appologize if this thread is in the wrong part of the forums, (i'm new here).. :-(

 I have an older p4 system that i'd like to turn into my tivo like system.  I also have a hauppauge win-tv-HVR-1600. I got mythbuntu installed on a brand new hard drive I had laying around but I can't get the system to recognize the Hauppauge 1600.  I've searched the net and seen that the 1600 doesn't work with mythbuntu and i've also read that some people have gotten them to work.

i found one forum that told a few steps on how one person got theirs to work.  But I'm still having troubles.    one of my main troubles is copying firmware to a different directory.  can anyone explain how you do that with ubuntu?  please be nice for I'm once again a noob.  

the site I found a little help on was [http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=850841](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=850841)

I figured out the wget function and i did the tar (#4. tar -xzvf cx18-firmware.tar.gz )  but the next part I'm lost on.  


also with windows you can see your c: drive but i for teh life of me can't figure out if it is possible with ubuntu.  I had thought that if I could open up my C: drive and find the files i could move them around.

Once again., I thank you wholeheartedly .

---

### Post by sbhargav21 on 2008-09-08
I am also in the same boat. I installed mythbuntu 8.04 & followed Hardy steps to configure my ATI driver.
From the tutorial
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=850841](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=850841)
I have it working till Step 9

When I try to cat on dev/video0 it does not work.

Also another issue I have is my TV Out is in Black & white from Bios till OS .. I typed in TVStandatd & other parameters under Xorg.conf file but still not working.

Any help is appreciated. I wonder if anyone is from Northern Virginia reading this post.

---

### Post by yoda-sama on 2008-09-10
Scubydoo, something important to understand about Linux is that it handles drives more intelligently than Windows does.  You won't find any silly drive letter stuff here.  Linux allows you to mount drives as directories, and you can create those directories just about anywhere you want.  Generally anywhere under your /home directory is an area where you may freely write without elevated permissions and is usually on your primary hard drive (C: in Windows jargon) (unless, of course you mount an entire other drive, or a partition from another drive, as /home, hehe).

On the chance that you're looking for data from your a windows drive on a computer you're dual booting with (which is one other way I could interpret your quest to find a C:/) then that is possible but I won't bother getting into that without being sure I have to bother.

Btw, you're having permission issues when you're trying to copy those files.  When you copy to a place outside of /home (or wherever else you've given a general user write permission) you need to elevate your commands to superuser/root/administrator type level.  So you'd basically want to type:   sudo cp filename target_directory     and then give it your password when it asks (this will give you superuser privileges for the commands you type "sudo" before, and for reference sudo = "superuser do", if that helps you remember it any better).

But for now I'm having my own issues, namely getting mythbuntu to actually allow me to watch/record video from my HDHomerun despite the fact that it can communicate with the tuner well enough to scan channels and pull down free OTA programming data.  Anyone like to chime in on that one?  If I select Watch TV, it goes to a black screen for a second and brings me straight back to the menu.  No error messages or anything.  Recordings obviously don't go any better.  Very confusing.

---

