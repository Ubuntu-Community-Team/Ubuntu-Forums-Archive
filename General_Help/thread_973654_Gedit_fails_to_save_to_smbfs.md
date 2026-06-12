---
title: "Gedit fails to save to smbfs"
date: 2008-11-06
forum: General Help
---

### Post by cerberos on 2008-11-06
I can't get Gedit to save files to my smbfs' that I mount regularly.

I use this command to mount them:
```
gksudo "smbmount //deb-pc/data /smbMount/deb -o username=administrator,password=****,uid=1000"
```
And I can easily edit the files using command line editing tools, and files can be edited by OpenOffice.Org fine.
When I try and save the files in Gedit I get the following message in Gedit:
```
Could not save the file /asdfasdf/blah.txt
Unexpected error: Text File Busy
```
and the following is printed to the console if I run it from a console:
```
** (gedit:11762): WARNING **: Hit unhandled case 0 (Text file busy) in parse_error.

```
Lastly the permissions for the file are:
```
-rwxrwSrwx 1 gareth gareth 0 2008-11-07 13:29 2008 11 07 Gareth.txt

```
(my username is gareth)
So I'm at a loss for what the problem could be.

---

### Post by quazi on 2008-11-06
I'm not sure if this will help, but try using "mount -t cifs" instead of smbmount.  I've heard that smbfs is no longer maintained, and I'd hazard a guess that smbmount is the same as "mount -t smbfs" (although I'm not sure).

---

### Post by cerberos on 2008-11-06
Thanks for the suggestion but that didn't change anything, I think the two commands are equivilent anyway.

---

### Post by cerberos on 2008-11-08
Discovered what I think is the problem, Gedit doesn't remove its temporary files. Well at least that the problem at home when using sshfs, which I suspect is a similar problem to when at work I'll confirm this behavior at work on Monday.

---

### Post by Voland on 2008-11-14
So have I the same problem. Is there any solution?

---

### Post by cerberos on 2008-11-14
I haven't found a solution yet, I have determined that the problem at work using smbmount isn't the same problem I was having at home with sshfs (which has the awkward work around, but at least that works)

---

### Post by quazi on 2008-12-01
I've found that I have the same problem (tried a bunch of things including adding noperm,_netdev opetions).  I cannot replace files on a windows share, but I can delete them and then copy over a new file.

---

### Post by MarkusAurelius on 2008-12-06
I have been experimenting significant issues as well with smbfs on Intrepid.  I have waited for the usual updates as I have seen many questions about this in 8.10.  Unfortunately, these smbfs (cifs) problems are all over the forum...  It would appear that these should be tagged together to help indentify the problems with smbfs (cifs) in 8.20.

Basically, smbfs is broken in 8.10 (see [https://lists.ubuntu.com/archives/ubuntu-server-bugs/2008-October/006643.html](https://lists.ubuntu.com/archives/ubuntu-server-bugs/2008-October/006643.html))

I have a local server running Debian.  Samba has been running fine for ever on Windows XP, Mac OSX and previous versions of Ubuntu.  I have exactly the same "mount" setup on 8.10 as on 8.04 but it is broken on 8.10.  For example, all the reported problems about "not a directory (20), the Gedit one where the file can't be written", etc. etc.

I first noticed it when my rsync jobs failed with: "can't change permissions", or "file is not a directory" where smbfs "thinks" a file is a directory.

I have tried the various suggestions posted in the Forum, but to no avail...  Since Mac OSX and Windows are just fine with the Samba shares and as well as 8.04, then 8.10 has broken smbfs (cifs) ((or smbfs is bro ken in 8.10))

My work-around, at this time, is to use nfs.  I'm OK with that at the moment, but it is not a solution...  If that option is fine for you, go fo it...  I've seen others revert back to 8.04, which I also did as well, but we're not doing the Ubuntu community any good by doing so...  we must forge ahead...

I suspect that a fix will come soon enough as it has been reported (see above) as Bug 286828...

Personally, I'll keep watch on its progress..

Have a Great Day...

Regards!

---

### Post by Kellemora on 2008-12-06
Hi cerberos

I have removed smbfs from my machines entirely!

BECAUSE it prevents all the machines from seeing all the machines!

Or to make more sense of what I just said.

Load smbtree, if you don't have it loaded already.

Then type smbtree in your terminal, it will list all of your shares NOT BLOCKED by smbfs.

Uninstall smbfs and type smbtree again and VOILA, ALL of your shares will now show.

Still don't mean they will appear under Places/Network without going to Go/Location and typing in smb://IP number.

The latter is a BUG that has been ignored now for over 2 years!

TTUL
Gary

---

### Post by dorseye on 2009-03-01
3 months on this issue, any updates?

---

### Post by iiiyyyhhhsss on 2010-04-18
"Unexpected error: Text file busy"
 
It has been long time since the bug was found!
 
Any solutions?

---

