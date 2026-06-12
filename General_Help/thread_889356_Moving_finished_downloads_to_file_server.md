---
title: "Moving finished downloads to file server"
date: 2008-08-14
forum: General Help
---

### Post by stromdal on 2008-08-14
I've set up a dedicated download box using Ubuntu and Torrentflux. This machine's only task is to DL files; it is not supposed to be a file server. Instead, I want to move the DL'ed files to my network file server (also an Ubuntu machine) - or rather; I want my file server to fetch the files from the DL server. Although I am new to Linux I believe a cron job using NFS would do the trick, but the finished DL's are stored in the same directory as the incomplete DL's, so I am uncertain about how to proceed. 

Is there anyone who has done this or can give me any pointers on how to solve this? Can I get TorrentFlux to move the finished files to a different directory (perhaps using a tool/hack)? Can I get the cron job to use the torrent to check whether a file is complete or not (perhaps one job running on the DL box moving the files and another running on the file server fetching the files)? Does Torrentflux-b4rt solve this problem?

---

### Post by wilbbe01 on 2008-08-14
I've never used it, but it sounds like something rsync might do.  From what I have read/heard with it I think it basically compares to see changes and keeps the remote directory in sync with the local one.

---

### Post by prshah on 2008-08-14
> **stromdal said:**
>  Instead, I want to move the DL'ed files to my network file server 

I don't know about torrentflux, but most torrent clients have an option to move finished downloads to a specific folder; you can either point that folder to a network machine (not a good idea since sometimes the network may be down) or some other directory on the local machine. Moving the files from the "other" directory to your server machine can be done with a cron job on either the server (pull) or on the torrentbox (push).

What script commands are exactly used varies depending on the type of network; if you use samba, a simple cp -R command will do the job; NFS, you can use rsync; but in my opinion, the simplest is scp (secure copy) but that requires SSH to be setup properly between your torrentbox and server (Specifically, the torrentbox should allow password-less logins from a specific machine, in this case, your fileserver, and silently ignore all the rest).

EDIT: rsync can be used in all situations (Even Samba), but again requires ssh server to be enabled on the torrent box or server box (depending on pull/push).

---

### Post by hyper_ch on 2008-08-14
yeah, you would need to have move the finished files somewhere else... the rest is simple ;)

---

### Post by wilbbe01 on 2008-08-14
So talking to a coworker today I came across another idea which sounded really simple.  Why not just mount the file server through nfs or something on the torrent box, and then you don't need to worry about transferring them.  They'll be stored on the file server all of the time?  You would have to check to see if a file is done I guess, but why not have samba or nfs or something mounted as the location for your torrents?  As for the network not being reliable enough as prshah said, if the two machines are physically close the likelyhood of the file server going down without the torrent box going down is probably pretty low.  I would just set up a samba mount to the file server on the torrent box and set that as the download location.  If you mount the drive correctly, as far as you could tell it woudl look local to the torrent box, while still accessible and normal looking from the file server.  I recommend that way, it sounds like a simple solution with few places for things to go wrong.  Good luck.

---

### Post by stromdal on 2008-08-15
wilbbe01: That WOULD be a simple solution, but for security reasons I have chosen to put the bittorrent box on a DMZ and the rest of the network inside a firewall. If security was not an issue I would simply put the bittorrent service ON the file server.

The thing I want to do, I suppose, is to have a cron job comparing the DL'ed file (zip, avi or whatever) to the SHA1 hash code contained in the .torrent file. If the two hashes match; move the file to a "Finished" directory. Once the files have been moved it's a simple job to get the file server to fetch the files from the BitTorrent box.

---

### Post by alexdd on 2008-08-15
I came across almost exactly this problem recently.  I solved it by using the ctorrent client, a simple command line bit torrent client.  You can make the client finish when it has completed downloading the file, for instance:

ctorrent -e 1 <torrent file>

will finish after downloading and seeding for an hour.  So knowing this, you can wrap the command in a shell script such that when it is finished, move all the files to a separate directory, eg:

cd active_torrent_dir
ctorrent -e 1 torrentfile
mv * /finished/torrent/directory

This does rely on having only one active torrent in the directory, but I don't think it would take much shell scripting to create a new directory for each new torrent.

Hope this helps.

Cheers,

Alex..

---

### Post by smeerbartje on 2009-03-05
But the best solution would be to install a torrent client which has the option to automatically move 'finished' files to another directory. Does someone know such a client (webbased)?

---

### Post by hyper_ch on 2009-03-05
rtorrent can do it. If you want a wui with it you'll need to compile it yourself.

---

