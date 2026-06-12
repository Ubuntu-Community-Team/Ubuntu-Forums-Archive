---
title: "What happens if I rm-rf a mounted directory?"
date: 2008-08-26
forum: General Help
---

### Post by zackiv31 on 2008-08-26
I mounted an NFS drive into a users home directory.. I deleted the user and then tried to rm -rf that user directory...

A couple seconds in I was like oh s^&*.... did I just delete all my media files?

Well I checked and all seemed to be in tact... did I actually delete anything?

---

### Post by -Zeus- on 2008-08-26
did you press Ctrl+C while it was doing it, or did it finish by itself?

---

### Post by tamoneya on 2008-08-26
most likely it was starting to delete them and it just didnt process all the files.  Are you certain that you have every file.  Also what was the exact command.  Did you preceed it with sudo?

---

### Post by nickgaydos on 2008-08-26
I would just STAY away from those commands....they are BAAD :P

---

### Post by -Zeus- on 2008-08-26
not very helpful...

---

### Post by LateNiteTV on 2008-08-26
this is what i love about most people who use ubuntu: they have absolutely no idea what theyre doing, yet ubuntu allows them to soooooooo easily **** things up. reading posts like these will never get old.

---

### Post by -Zeus- on 2008-08-26
you're not very helpful either.

---

### Post by zackiv31 on 2008-08-26
oh ya.. I sudo -rf /home/user ...

Ctrl-C'd it after a couple seconds when i realized...

It was a mounted network drive... it's where I store all my media files... looking through briefly, I can't tell what it deleted :-/... but we're concluding it did delete some stuff?

---

### Post by -Zeus- on 2008-08-26
if you ctrl-C'ed it while it was running and there were no errors, then 99% chance that you have missing/corrupted files IMO.

---

### Post by HighFrictionZone on 2008-08-26
Well. If your files seem to be there, I don't think they were deleted much. Hopefully, it only got as far as deleting some of the files in the user's directory before you canceled it (you DID cancel it, right?) - in which case you lucked out because you halted the command before it got around to making your media files somewhat scarce.

Count yourself lucky, and remember not to do that again without quintuple checking.

---

### Post by zackiv31 on 2008-08-26
Is there a systematic way that rm -rf works?  Alphabetical or whatnot?  Theoretically if it goes file by file I should only have 1 corrupted file right?

I checked the directory.. and its got 95% of the files still.. (I don't know what 5% is gone, or even if that much is gone)

---

### Post by -Zeus- on 2008-08-26
> **HighFrictionZone said:**
> Well. If your files seem to be there, I don't think they were deleted much. Hopefully, it only got as far as deleting some of the files in the user's directory before you canceled it (you DID cancel it, right?) - in which case you lucked out because you halted the command before it got around to making your media files somewhat scarce.

Count yourself lucky, and remember not to do that again without quintuple checking.

I disagree.  I think that if it went "couple seconds" before he stopped it, I think that some files will be missing corrupted.  I did that once with a mountpoint folder that I thought was unmounted and it went about 2sec... it blew away everything in C:\ and C:\Documents and Settings (windows obviously)

---

### Post by -Zeus- on 2008-08-26
it goes alphabetically; yes, likely you will have 1 corrupted and >=0 missing, because it will finish the files one by one, so it would be very hard for it to corrupt more than one file :-P

---

### Post by LateNiteTV on 2008-08-26
> **zackiv31 said:**
> Is there a systematic way that rm -rf works?  Alphabetical or whatnot?  Theoretically if it goes file by file I should only have 1 corrupted file right?

I checked the directory.. and its got 95% of the files still.. (I don't know what 5% is gone, or even if that much is gone)

rm -rf: rm = remove. 
-r = recursive: delete everything in all subdirectories as well
-f = force. ignore everything, just delete it.

---

### Post by LateNiteTV on 2008-08-26
and rm works quick. it doesnt *delete* them, it just marks that space as being writable.

---

### Post by HighFrictionZone on 2008-08-26
Right, but he's talking about removing an entire user directory and a network mounted folder. I would assume this user directory to be non-empty (many usually are). Depending on the speed of the computer, and the speed of the network, it may not have finished processing all the OTHER contents of the user folder before it started work on the network folder. Though there MAY be some file fragmentation issue, generally if he stopped it in a few seconds, he might have lucked out and canceled it before the computer even finished establishing a connection to the mounted folder and thus might have avoided serious damage. At any rate, nobody will know until he tries accessing some of the media. I personally feel that, depending on how long "a few seconds are", he might have avoided too much damage.

At any rate, most operating systems do NOT save changes to disk right away, but instead to a buffer. That way, if you happen to be in the middle of, say, deleting a file and you decide to cancel it, it simply discards the changes and no harm is done, amongst other uses (similar uses include keeping files you've recently worked on in memory rather than making constant reads-and-writes to and from disk, for both speed and longevity purposes.

I would sincerely hope that whatever operating system is running on the computer hosting the mounted folder has at least that capability and thus damage to file which were not completely deleted would be avoided entirely in which case he only has to worry about having lost files which might not have happened at all because none of them seem missing.

I'm not saying it's impossible for him to have lost data, I'm merely saying that having a disk cache in memory seems to be a feature present in operating systems since the days of MSDOS and smartdrv.sys and I would imagine that any modern operating system would implement something at least equivalent to that, and that a modern implementation would probably have the capability to make sure that any canceled deletions do not end up with damaged data.

---

### Post by tamoneya on 2008-08-26
> **-Zeus- said:**
> it goes alphabetically; yes, likely you will have 1 corrupted and >=0 missing, because it will finish the files one by one, so it would be very hard for it to corrupt more than one file :-P

Actually it will just go in the order they are listed in the MFT.  As latenitetv said it doesnt delete the actual files it just removes the references.  These references are located in the MFT.  While it is common for things to be alphabetical in the MFT it is not necessarily the case especially if you start talking about different filesystem formats.

---

### Post by zackiv31 on 2008-08-26
well my directory was called media, and all my important files were in a upnp folder...

If it deleted some folder.. I dont remember what it was cause it was <C***

---

### Post by zackiv31 on 2008-08-26
The mounted drive was an Infrant (now Netgear) ReadyNAS NV...

The user directory was basically empty, I created it today for this exact purpose... (no NOT to delete it)... but to host read only access to my media.  Of course I didn't mount it read only.. doh

We'll assume I got out of it OK, although its hard to tell... It's thousands of mp3's and avis... not much else...

---

### Post by zackiv31 on 2008-08-26
Can someone point me to a good tutorial on unix permissions, since this is the root of the problem?

Like If a directory is chmod 555, but an nfs is mounted into it as read/write, can a user delete the files from that directory?

---

### Post by LateNiteTV on 2008-08-26
heres the breakdown of file perms in octal:
4 - read
2 - write
1 - execute

chmod 0444 gives -r--r--r--
chmod 0222 gives --w--w--w-
chmod 0111 gives ---x--x--x

now add them up
chmod 0666 gives -rw-rw-rw
chmod 0555 gives -r-xr-xr-x
chmod 0777 gives -rwxrwxrwx

---

### Post by LateNiteTV on 2008-08-26
lol im not a good teacher. thats the best ur gunna get out of me. google for "linux file permissions" or something like that.

---

### Post by zackiv31 on 2008-08-26
I understand the name/numbering convention.. my question is more specific..

If a directory is universal read (555) and I mount an nfs drive into it as read/write... will I be able to write (i.e. delete) files from it, even though the root of the directory is read only?

... still searching for a tutorial.

---

### Post by LateNiteTV on 2008-08-26
what command did you issue to mount it?

---

### Post by jerome1232 on 2008-08-26
I find the best way to find out is to test it, setup a directory with read only permissions, mount the nfs share as read/write inside of said folder,  then try to create a dummy file in it. My guess is it will work as you gave permissions as read/write when you mounted it.

---

### Post by zackiv31 on 2008-08-26
So there's no underlying rule for it?  I would assume one would take precedence over another?  And yes I am testing myself, but thought someone here might be able to explain in a minute what takes me a good half hour to test.... and even then (like how this thread started) I still might be wrong!

---

### Post by LateNiteTV on 2008-08-26
to tell you the truth... i dont know. i dont understand why you would mount the nfs share on someones home dir as opposed to say /mnt/home...

---

### Post by jerome1232 on 2008-08-27
It makes sense to me at least this is how I see it

make a folder read only
now make mount this share that is read/write to everybody in a subfolder

```
/home/user dr--r--r--
|
---/home/user/nfs-share drw-rw-rw-
   |
    ---everything here inherits the folders permissions and thus is rw to everybody
```

I could be wrong though

---

### Post by zackiv31 on 2008-08-27
Because I'm giving this person ftp access to the machine, and I want to restrict them to their home directory... FTP setup was easy with vsftpd... and I have them limited to their home directory... hence the need to mount the drive in their home directory...

ln -s doesn't work for this problem..

From some initial testing, it seems the mount options override the folder permissions... Does this make sense?  NFS just disregards the folder?

---

### Post by zackiv31 on 2008-08-27
Mounting the filesystem ro, I can't even sudo rm the files in that users directory... so this must be the end all be-all:

Whatever the mount options are, are recursively "applied" no matter what those individual files permissions say.

---

### Post by jerome1232 on 2008-08-27
So we know we can further restrict permissions but I wonder if you can loosen permisions up ie

on the server the directory to be shared is dr--r-----

could you mount it on the nfs client as drw-rw-r-- or something simliar that allows more than what was originally permited. If you don't want to test I guess I can wait until I can get a power supply and bring my linux computer back from the grave to test it.

---

### Post by zackiv31 on 2008-08-27
I would think that its different layers of security... Like if my NFS only allows read access... no matter how things try to mount it, when my box tries to write files to it, no matter how its mounted, the NFS should (most definitely right?) tell the box to screw, even if the box thinks it can write...

I actually have 4 shares on my nas, two are read only, and two are read write... they have the same fstabs, but the two that are read only tell me to f&(*# off when I try to delete... I guess now I know why...

---

