---
title: "[SOLVED] Modified entire filesystem permissions! Can no longer boot, not even Usplash"
date: 2008-09-07
forum: General Help
---

### Post by Predator106 on 2008-09-07
Hi, well, I made a completely stupidly horrible mistake, and am regretting it now, I ended up hosing my filesystem, from what I see...

Well, I wanted to move my entire Ubuntu file system (copy) onto my external, then do the same to my Windows install. 

Can you even copy the entire filesystem when it's in use? 

Either way, I didn't know so I booted into the LiveCD, backed up windows and tried to copy Ubuntu. It complained about permissions so I ran nautilus as root, so as to copy the folders/files.

It STILL complained about permissions, this is something I don't understand. I thought root had read/write access to EVERYTHING, shouldn't it have those permissions?

Anyways, here's where the problem happens, I then select all the folders and goto properties, making the top 2 sections under the permissions tab being under create and delete, and read/write.

After clicking okay, it went through it all and I noticed the background was gone, so were the icons everywhere, it gave me some weird error that wasn't even a language (it could have been binary, but it looked almost encrypted) I thought rebooting may fix it, because I didn't understand why this would happen, I didn't actually do anything to the LiveCD that I was booted into... which doesn't make sense to me.

So I figured it was just being buggy or something, tried to reboot, had to guess which button, since the icon was gone and the text was scrambled like crazy, I booted into my normal Ubuntu, fearing the worst, and ended up with not even being able to boot into Usplash.

Here is the list of what happened, at ctrl+alt+F8 (or later), because the other terminals weren't responsive, even after ctrl+c. I was greeted with BusyBox built-in-shell (ash) which is apparently a slimmed version of bash I guess, from what I gathered, it certainly isn't as helpful. All it said was to type in help, and I could do about 20 commands, etc. The first terminal (default one) said Target filesystem doesn't have /sbin/init.

Back at the ash terminal, below help is '(initramfs)usplash[1308]seg fault at .(blah blah, what looks like a GUID/UID) error 6'.

Not entirely sure why I'm listing off this, as it has to be some kind of permission error, I suppose that it will magically "better" what I have done.

Will I have to reinstall Ubuntu----eeck, I had so much customization going on... I really, really, really don't want to.

I also found this:

[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

I should've found this before I started/should have asked before I did this. I had a really bad feeling, as I've had similar things happen before.

How in the world do I encounter permission problems like this, there was another time where I screwed up a user's account(not mine) wanted to copy their home directory into mine, delete the account and recreate and migrate the stuff over, but it wouldn't let me, so under root I did it, and root took ownership, but I could not give ownership back to the user (so they couldn't use the files/folders).

This is certainly one of the things I have to learn in Linux, file permissions really baffle me as I've been so used to Windows all this time. Also, what is the policy of file locking, isn't it always optional, the program's choice. I think I read somewhere that you could delete Linux while running it. Is that true?

Bottom Line: How can I restore the permissions, and continue backing up/migrating Ubuntu without reinstalling. I would prefer to not reinstall, but if I have to, what are the things I should backup to keep a lot of settings & customizations?

Thanks.

---

### Post by Predator106 on 2008-09-07
Bump, I don't like being without Ubuntu :) .

---

### Post by Neo_The_User on 2008-09-07
Un-do whatever you did that messed it up via Ubuntu disk.

---

### Post by Predator106 on 2008-09-07
What? Are you kidding me? How in the world is that even a helpful answer.... OBVIOUSLY I want to undo what I have done. I certainly wouldn't want to REDO what I have done....

It's not like I simply moved a folder or changed the permissions of one folder, NO, I changed the permissions to the ENTIRE FILESYSTEM.....

I'm not trying to be mean or blunt, but you stated a really obvious method.

I mean, even if I do manage to make it boot, won't their be inconsistent file permissions? Thus it would be less secure, isn't there a way to fix this. And could someone answer my other questions too..?


(Sorry for being somewhat annoyed).

---

### Post by Predator106 on 2008-09-07
I thank you, even though it was being obvious, apparently it helped "set me straight", so thanks again...

Well, maybe I asked too many question also :).

But I pretty much answered most of it on my own, I suppose I just panicked because I thought my entire Ubuntu install was ruined (even though I will probably reinstall when I hit Intrepid, for a cleaner install...).

But for anybody Googling this, this will hopefully be the first one on the list or will sub-link what I have linked...

These are very useful, and READ this BEFORE you try to copy or move one filesystem on one hard drive to another HDD. (Trying to use a bunch of keywords, just because I know how a pain it was to google for the right thing).

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

[http://ubuntuforums.org/showthread.php?t=431645](http://ubuntuforums.org/showthread.php?t=431645)

---

### Post by Neo_The_User on 2008-09-09
I'm just saying, when I make a mistake in Ubuntu, I can always use the CD to fix it (unless it's a problem with video) and get it back the way it was usually hence the term RESCUE DISK!

---

