---
title: "Um /home and /home/home and /disk/home"
date: 2008-10-21
forum: General Help
---

### Post by dave.com on 2008-10-21
Anyone know stuff about moving a orphan /home partition back into /root ?

I saved /home and re-installed Ubuntu, I haven't made a /home partion's fstab entry, now when /home partition is mounted on /root/home I have a permissions conflict. Same users accounts in them. My desktop is gone, and if I close a window can't open it once again. Nor can I open anything atm. I dun wanna close muh command-line terminal because I won't get it back.

Old /home (the /home partition) has a lot of stuff, the re-installation /home installed by ubuntu has a good .dmrc but mostly nuthin. Some general
saved working state stuff which is prolly handy (but who knows?). Some of the old /home partition stuff has 'issues', like icon shortcuts displayed as files, Desktop is all folders and script files instead of shortcuts, file browsers look more like windows with files in 'em all the gui layout for navigating is kinda, um.. not present in our Time and Space.  

I want to fix my little problem at /home, it has to be done either now or the next time I snarl up... erm, start up /home. There's another /home directory nested inside /disk/home as well. No idea what its doing there. I can't see inside it now the partition is mounted off / to know whether I'd care it is there or not. I can't see inside one user in /home/<user> from another user, or if I can I can't move or merge or copy anything there. /home/home is like a mirror of /home/<user> it has the same directory tree as /home ie /home/home/<user> (I don't think there is anything important inside it tho).

I don't have much space in /root partition for a /home, the /disk/home partition is almost 300Gb and has used like 60Gb. The /root partition is like 25Gb space and using like 3-4Gb including /home. It isn't enough space. 

PS: Is /home a candidate for option similar to /boot partition in the installation LiveCD (ie choose not to write over an existing /home partition).

---

### Post by ronnielsen1 on 2008-10-21
> Anyone know stuff about moving a orphan /home partition back into /root ?
If you're talking about your personal home it should go into /home - not into /root/home. Ubuntu doesn't seem to have an option to save /home but what I have done before is to save my personal files (/home/ron) on a different partition and then once I do a new install I took the folder /ron and copied it into the new /home/ron (empty one created by the new install) I only copies the folders and files (otherwise you will end up with /home/user/user)
As long as you copy all your folders, files including hidden files, your settings should all be back.

---

### Post by dave.com on 2008-10-21
Kewl, thanks man I'll get on it in a few. Gunna break for dinner and a movie.

---

