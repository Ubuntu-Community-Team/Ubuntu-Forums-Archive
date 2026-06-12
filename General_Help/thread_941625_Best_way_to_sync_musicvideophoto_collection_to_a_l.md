---
title: "Best way to sync music/video/photo collection to a local server?"
date: 2008-10-08
forum: General Help
---

### Post by XtremeGamer99 on 2008-10-08
I have an old Compaq box running as a file server in my local network. The network, wired, runs at 100Mbps, and yet only gets about 2MBps typically (note the difference between Mb and MB). This is inefficient (for me, anyway) for transferring over large about of data such as music and videos. At the moment, I have an sshfs mount, and I just copy and paste my files to the server. Very slow. So I have three questions:

1) Is there a better way to do this? Like, somehow compress (but not lose) the data so that more data can be passed per second? I read somewhere that rsync can do this, but is the a guide anywhere to mount a remote filesystem automatically with rsync? I'm currently using this guide for the sshfs automount: [http://ubuntuforums.org/showthread.php?t=430312](http://ubuntuforums.org/showthread.php?t=430312). UI'm hoping that the copy & paste functionality will still be available, but faster, if mounted with rsync. Any ideas?

1.2) I sometimes mount my file server on my laptop from a remote location away from home -- such as college. My internet at home isn't that great, I think I get 128Kbps max upstream. So trying to get files from home can be tedious. Using a compression program like above, I think it'll be a lot easier to get files (though I know it'll never be very fast, but a little faster at least). Anyone have any input on this and if it'll work like I think?

2) I need a program that automatically syncs my music player (always located at /media/IAUDIO) with the music directory of the file server (always mounted/linked through somewhere in my home directory). Is there any kind of GUI program to do that? Maybe Unison? I dunno...

Thanks!

---

### Post by caleb12 on 2008-10-08
First off... rsync is a copying tool. You can pass user authentication through the rsync command for remote locations. The effect would be the same as mounting the location and then copying the files, however strictly speaking it's not "mounting" the location. A mounted location would be permanently accessible to the entire system whereas when using rsync it only becomes accessible for rsync and only for that command. Either way this may be what you meant... 

I use rsync to sync backup directories on an external hard drive and it works great especially in a script. Also, you can set rsync to only copy changed files and to use compression. So, once the files are copied and in place it becomes a very quick little tool... that will knock out large directories in no time. The best way to figure out rsync is... you guessed it... man rsync. It's a command line tool, and best used that way. The only problem I have with it, is that it will not do a strict mirror on the destination filesytem - meaning it will not delete files from the destination only copy changed files or added files. So, I tend to use rsync and unison in combination since unison will keep a log of all changes and I can propagate deletions from the source to the destination. But, like I said rsync is really very quick after it's setup... much quicker than unison in my opinion hence it's my first choice and unison is there as a backup. 


I don't know of anyway to automagically sync directories upon connecting, perhaps there is a way to add a script execution into UDEV or HAL so that when the device is connected the script is launched. I am sure there is a way, I just don't know what it is... Although, if someone else knows that would be great since I'd like to know myself... 

Ideally though you would need for your mounted directories to be static, which means you would have to add them to fstab so that the music player and fileserver location are always mounted to the same location... I know you need to start there. :) Beyond that, ya got me...

---

### Post by vanadium on 2008-10-08
[quote=caleb12]The only problem I have with it, is that it will not do a strict mirror on the destination filesytem - meaning it will not delete files from the destination only copy changed files or added files.[/quote]

You missed out the --delete option for that effect. The syntax for "full" mirroring is

[code]
rsync -av --delete <source> <destination>
[/quote]

To the original poster: I would not know how you can speed up a slow network. As caleb12 said, rsync acts fast in synchronising because it only commits the changes.

You would need a tool or mechanism that automatically launches an rsync when the music player is being connected. Unfortunately, I cannot help here.

---

### Post by caleb12 on 2008-10-08
> **vanadium said:**
> 
rsync -av --delete <source> <destination>


Ahhhh, apparently I need to RTFM a bit more... I must have skipped over that one, time to re-write my scripts... Unison was so bulky, I'd be glad to give it up... 

thanks!

---

