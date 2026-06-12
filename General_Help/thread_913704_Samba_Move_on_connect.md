---
title: "Samba: Move on connect"
date: 2008-09-08
forum: General Help
---

### Post by TheDonkey on 2008-09-08
Hello, I have a fairly simple problem, but I still need some advising,

I'm currently adding a Torrent client to my Server box so that I don't have to run my monster gaming PC at night(The server is a laptop) problem is, the Harddrive in the machine is only 10GB, 4 of which is taken up between the OS, my Server apps, other stuff.

So my question is,
Is there some form of Samba mode, where all the contents of a folder will be moved to a remote PC when it goes online?

IE, My box downloads a couple 700MB files at night, then in the morning, soon as I turn on my computer, they get moved to mine?

In previous times, when I was running a Windows server, I created a Batch script that ran on startup that copied and deleted the contents of the downloads folder, but that's less than ideal.

Any solutions welcome, and thanks in advance.

---

### Post by iaculallad on 2008-09-08
What you'll be needing is a file/folder synchronization app. Try rsync.

---

### Post by ryanhaigh on 2008-09-08
I think you are going to end up writing a similar script to what you previously had although you can change it so that it runs on the server. Just ping the desktop IP every 5 minutes (or less) and once the IP can be pinged try to copy the files and delete the originals once the copy is done. Alternately you could just write the script for the client (your desktop) and have it run on startup using either cron/rc.local or your gnome session startup.

I don't think rsync would work in this situation because you don't want to keep the files on the server.

---

### Post by TheDonkey on 2008-09-08
> **ryanhaigh said:**
> I think you are going to end up writing a similar script to what you previously had although you can change it so that it runs on the server. Just ping the desktop IP every 5 minutes (or less) and once the IP can be pinged try to copy the files and delete the originals once the copy is done. Alternately you could just write the script for the client (your desktop) and have it run on startup using either cron/rc.local or your gnome session startup.

I don't think rsync would work in this situation because you don't want to keep the files on the server.

My desktop is a Vista machine, so yeah, no Cron, but I understand running things on Startup from Vista.

I would very much prefer for the script to be run on the server,

Is there a comprehensive guide as to the Logic commands in linux? (I'm a Windows guy, and when my XP server crashed, I switched to a laptop and decided to use Ubuntu for once)

Pinging every 5 minutes and copying on connect seems like the best method.


On a note unrelated to this entirely, I'm using TorrentFlux as my Client, as it seems to be the only client that can run on a non-GUI install, is there some form of function where it'll save files to one directory, then move them somewhere else on complete.

I just installed it today and haven't tried downloading anything yet, but it seems that it'd be a bad thing if the script copied and deleted incomplete files.

So how would I go about managing that(again, I haven't tried downloading anything yet, so I'm not sure of the methods used, file extension, hidden directory, etc)

---

### Post by ryanhaigh on 2008-09-08
I would recommend a bash script for this sort of thing. The advanced bash scripting guide should have all you need: [http://www.tldp.org/LDP/abs/html/](http://www.tldp.org/LDP/abs/html/)

Bash is good because it allows you to use normal console commands in a script.

For example:

```

#!/bin/bash

#infinite loop so that we do this forever
while [ 1 ]; do
    ping -c 1 -W 5 192.168.0.1
    if [ $? == 0 ]
    then
        echo 'the return code of ping indicates desktop is available'
        #this is where you would do what you need to to move the files
    else
        echo 'the return code of ping indicates the desktop is not available'
    fi
sleep 120
done

```

I cannot recall how to use smbclient to move file so you will have to figure that part out yourself but the man page for the smbclient command will certainly be helpful, just open a terminal and use:
```
man smbclient
```
This same documentation is generally available on the web just google man smbclient, it is also available in System>Help.

---

### Post by ryanhaigh on 2008-09-08
Just wanted to add that there is a cli client for transmission (the default torrent app on Ubuntu 8.04. The package is [apt://transmission-cli]("apt://transmission-cli") so if your current client doesn't support moving perhaps this one will.

There is also rtorrent which I have read about many times.

---

