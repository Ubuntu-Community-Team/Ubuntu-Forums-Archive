---
title: "Encrypted private directory does not auto mount on loging"
date: 2008-11-10
forum: General Help
---

### Post by psypher on 2008-11-10
Hey all. Got interpid latest installed, setup encrypted private dir but as far as I understand, and confirmed by other users, this folder should be auto mounted at login which it doesn't. When I browse to the folder all I see is a shotcut file:

"THIS DIRECTORY HAS BEEN UNMOUNTED TO PROTECT YOUR DATA -- run mount.ecryptfs_private to mount again"

if i dbl click on the file my files immmediatly appear. 

Like I said other users say they do not have to do this and don't see this file. Where has things gone wrong. I have a very basic setup of Intrepid, didn't change anything fancy.

Thanks

---

### Post by reison on 2008-11-10
I'm having a similar issue: Private directory no longer appears as a mounted drive on my desktop or in Nautilus, but I can see and browse ~/home/user/Private and all my files are still fully accessible.

I received several Ubuntu updates this morning and didn't have this problem before applying them, though I don't really remember which updates they were.

---

### Post by psypher on 2008-11-11
but you don't have to dbl click the mount.ecryptfs_private shortcut to see them?

that different to my problem. my drive is not mounted and still encrypted until i dbl click that file, then it's all there. not usefull in my situation.

---

### Post by littlethingsdontkill on 2008-11-11
I think it has to do with the latest updates.
After installing them yesterday night and changing nothing else in the system my private directory is not mounted any more on reboot. I have not checked if it is completely invisible through the system but I can confirm the problem.
Has anybody filed a bug report yet?

---

### Post by reison on 2008-11-11
On my laptop this morning--different machine--Private did not mount automatically AND the folder contains the the link mentioned above by psypher.

My files in Private on the laptop are inaccessible, even if I double-click the link OR "mount.ecryptfs_private" from the command line:

> dreison@pc503927:~$ mount.ecryptfs_private 
keyctl_search: Required key not available

---

### Post by reison on 2008-11-11
First other thing I've noticed: I changed my login password yesterday and did not logout/login again until I started up my laptop this morning. When I logged in with my new password, Private and the files in it were not available to me. On a hunch, I changed my login password back to what it was before, logged out and back in.

Private does NOT auto-mount as it did before, but I do have access to the Private directory [and the files in it] now. 

Second thing I noticed: the password changed TO yesterday had a "!" in it, but the old one is only alphanumeric.

Seems like there may be numerous issues here.

---

### Post by pwaldo on 2008-11-11
I also have this problem after getting latest updates.  Private folder is no longer showm.  I tried manually mounting it:
```
paul@paul-laptop:~$ mount.ecryptfs_private 
mount: Operation not permitted
setreuid: Illegal seek

```

strace shows this:
```
paul@paul-laptop:~$ strace mount.ecryptfs_private 
execve("/sbin/mount.ecryptfs_private", ["mount.ecryptfs_private"], [/* 37 vars */]) = 0
[...]
socket(PF_FILE, SOCK_STREAM, 0)         = 3
fcntl(3, F_SETFL, O_RDWR|O_NONBLOCK)    = 0
connect(3, {sa_family=AF_FILE, path="/var/run/nscd/socket"}, 110) = -1 ENOENT (No such file or directory)
close(3)                                = 0
socket(PF_FILE, SOCK_STREAM, 0)         = 3
fcntl(3, F_SETFL, O_RDWR|O_NONBLOCK)    = 0
connect(3, {sa_family=AF_FILE, path="/var/run/nscd/socket"}, 110) = -1 ENOENT (No such file or directory)
close(3)                                = 0
[...]
setresuid(-1, 1002, -1)                 = 0
geteuid()                               = 1002
open("/home/paul/.ecryptfs/Private.sig", O_RDONLY) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=17, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fd6be60e000
read(3, "dc3c54d86caa7b8d\n", 4096)     = 17
close(3)                                = 0
munmap(0x7fd6be60e000, 4096)            = 0
keyctl(0xa, 0xfffffffc, 0x401ef7, 0xf403c0, 0) = 498957920
stat("/home/paul/.Private", {st_mode=S_IFDIR|0700, st_size=4096, ...}) = 0
stat("/home/paul/Private", {st_mode=S_IFDIR|0700, st_size=4096, ...}) = 0
open("/tmp/ecryptfs-paul-Private", O_RDWR) = 3
fcntl(3, F_GETFL)                       = 0x8002 (flags O_RDWR|O_LARGEFILE)
fstat(3, {st_mode=S_IFREG|0600, st_size=3, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fd6be60e000
[...]
setreuid(4294967295, 0)                 = -1 EPERM (Operation not permitted)
mount("/home/paul/.Private", "/home/paul/Private", "ecryptfs", 0, "rw,ecryptfs_sig=dc3c54d86caa7b8d"...) = -1 EPERM (Operation not permitted)
[...]

```

---

### Post by pwaldo on 2008-11-11
I think the latest libpam might be the cause of the breakage.  This page talks about how PAM automatically mounts the Private dir:
[https://wiki.ubuntu.com/EncryptedPrivateDirectory#Implementation]("https://wiki.ubuntu.com/EncryptedPrivateDirectory#Implementation")

I see this in /var/log/syslog:
```
Nov 11 09:47:57 paul-laptop gdm[5874]: pam_sm_authenticate: Called 
Nov 11 09:47:57 paul-laptop gdm[5874]: pam_sm_authenticate: username = [paul] 
Nov 11 09:47:57 paul-laptop gdm[5874]: Error attempting to parse .ecryptfsrc file; rc = [-5]
Nov 11 09:47:57 paul-laptop gdm[5874]: Unable to read salt value from user's .ecryptfsrc file; using default 
Nov 11 09:47:57 paul-laptop gdm[5874]: Mount of private directory return code [256]
N
```

I was able to mount the Private stuff using the technique here:
[https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering Your Data Manually]("https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering Your Data Manually")

HTH!

Paul

---

### Post by endesign on 2008-11-13
I also have lost the encrypted drive icon on the desktop after an upgrade a couple of days ago (almost certainly with the libpam upgrade in it). I still have the private folder in home and files are accessible from it.

---

### Post by psypher on 2008-11-14
2 bugs that could be related:

[https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/259631](https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/259631)
[https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/284443](https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/284443)

Noticed the one mentioning autologin being enabled and it says that it's actually by design and not a bug. 

I use autologin at the moment, will turn it off and test again at next reboot.

---

### Post by pwaldo on 2008-11-14
> **pwaldo said:**
> I also have this problem after getting latest updates.  Private folder is no longer showm.  I tried manually mounting it:
```
paul@paul-laptop:~$ mount.ecryptfs_private 
mount: Operation not permitted
setreuid: Illegal seek

```

Here are the permissions for these directories.  Do they look right?  Is the group correct?

```
paul@paul-laptop:~$ ls -ld /home/paul/.Private /home/paul/Private
drwx------ 3 paul paul 4096 2008-11-06 21:04 /home/paul/Private
drwx------ 3 paul paul 4096 2008-11-06 21:04 /home/paul/.Private
```

---

### Post by d-man97 on 2008-11-14
I have the same problem. It's not mounted as a separate partition anymore (on desktop/places menu/computer:///), but both ~/Private & ~/.Private are accessible directly at all times, containing identical files.

My logs have shown the following since I installed Intrepid:
```
Nov 13 21:37:41 dereksbox polkit-grant-helper-pam[7143]: pam_sm_authenticate: Called 
Nov 13 21:37:41 dereksbox polkit-grant-helper-pam[7143]: pam_sm_authenticate: username = [derek] 
Nov 13 21:37:41 dereksbox polkit-grant-helper-pam[7143]: Error attempting to parse .ecryptfsrc file; rc = [-5]
Nov 13 21:37:41 dereksbox polkit-grant-helper-pam[7143]: Unable to read salt value from user's .ecryptfsrc file; using default 
Nov 13 21:37:43 dereksbox polkit-grant-helper-pam[7144]: Passphrase key already in keyring 
Nov 13 21:37:43 dereksbox polkit-grant-helper-pam[7144]: Error attempting to add passphrase key to user session keyring; rc = [1] 
Nov 13 21:37:43 dereksbox polkit-grant-helper-pam[7144]: There is already a key in the user session keyring for the given passphrase. 
```

I have restarted about 5 times this morning, and this is the only message I have in any of my logs, filtered by 'pam', that affect the encrypted partition. Weird that it would stop working, and not mention it, huh?

---

### Post by am28111 on 2008-11-17
I also have this problem too. Running mount.ecryptfs_private for me gives me nothing. There is no error message so originally I assumed it worked, unfortunately this is not the case. 

I wonder if there is a bug report for this specific problem... I will search for it.

---

### Post by psypher on 2008-11-18
In my case the problem was solved by disabling autologin. Guess it's a security feature. Would be nice if the wiki could include this little important tidbit. Is there anyway I can add it? 

am28111: Check my previous post for links to some bugs already logged. See if that helps

---

### Post by bodhi.zazen on 2008-11-18
> **psypher said:**
> In my case the problem was solved by disabling autologin. Guess it's a security feature. Would be nice if the wiki could include this little important tidbit. Is there anyway I can add it? 

am28111: Check my previous post for links to some bugs already logged. See if that helps

The community pages are community (user) maintained, so yes, as long as you have a launcphad account you may edit the wiki.

If you wish to help with the wiki, feel free to join the wiki team / mailing list.

_Note_: I added the information are: Auto login to the wiki page.

---

### Post by am28111 on 2008-11-24
> **psypher said:**
> In my case the problem was solved by disabling autologin. Guess it's a security feature. Would be nice if the wiki could include this little important tidbit. Is there anyway I can add it? 

am28111: Check my previous post for links to some bugs already logged. See if that helps

Unfortunately the two bug reports that you mentioned don't cover my problem. Thank You, though. 

I was wondering if there was a way that I could delete the entire ecryptfs package with all its configuration files and try to install it fresh, to see if that works. I think the command is sudo apt-get purge ecryptfs-utils. I'll try that and reinstall to see if it works.

---

