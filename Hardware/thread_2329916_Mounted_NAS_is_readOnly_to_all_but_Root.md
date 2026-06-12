---
title: "Mounted NAS is readOnly to all but Root"
date: 2016-07-06
forum: Hardware
---

### Post by kaiserman on 2016-07-06
I have a problem mounting my new Buffalo NAS. 


In fstab I have: 
```
//buffalo.local/Public /home/christian/NAS cifs username=admin,password=xxxxx,rw,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

```

It mounts alright, but the /NAS folder is read only. It takes root privileges to write to it.


I'm quite new to Linux, so I don´t really know what to check.
```
stat /home/christian/NAS
``` gives the following, which seems right.
```
Access: (0775/drwxrwxr-x)  Uid: ( 1000/christian)  Gid: ( 1000/christian)

```
I run Lubuntu 15.10.

---

### Post by TheFu on 2016-07-06
Support for 15.10 ends soon (if it hasn't already). Would be best to move to a supported release and try again.
Also, if this is a NAS, it would be best to use NFS with Linux clients, not CIFS.  Then file and directory permissions will be the native Unix ones we all expect.
With simple CIFS mounts, permissions are only controlled at mount time for 1 userid. So if your login to the Linux machine isn't "admin", then I wouldn't expect any other userid to have access.

Plus not all NAS devices implement the protocols 100%, to interoperability is always guess work.  Does the specific model of NAS have a how-to guide that shows how to connect from Ubuntu or Linux?  
[https://mginternet.wordpress.com/2012/01/05/mounting-a-buffalo-linkstation-share-on-ubuntu/](https://mginternet.wordpress.com/2012/01/05/mounting-a-buffalo-linkstation-share-on-ubuntu/) has an example use "guest" as the userid.

---

### Post by kaiserman on 2016-07-07
Thanks,
First of all I created an account on my NAS with exactly the same credentials as my standard linux login.
I tried nfs instead of cifs. No luck.

Guess  I have to upgrade Linux and have a go again.

---

### Post by TheFu on 2016-07-07
At this point, 16.04 or 14.04 are the best answers before doing anything else.  I doubt it will solve this, but it will get you 5 or 3 yrs of support, respectively.

If you are willing, NFS is the better solution for Unix file shares, but we need data and facts to be able to help. "No luck" is a little vague. Details - after the machine is on an LTS.

---

### Post by Morbius1 on 2016-07-07
> //buffalo.local/Public /home/christian/NAS cifs username=admin,password=xxxxx,rw,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
And what happens when you do this instead:
>  //buffalo.local/Public /home/christian/NAS cifs username=admin,password=xxxxx,rw,iocharset=utf8,file_mode=0777,dir_mode=0777,[COLOR=#0000cd]**nounix**[/COLOR] 0 0

---

### Post by kaiserman on 2016-07-08
Morbius1, the "nounix" option did the trick! The NAS is now writeable.

I will go for Lubuntu 16.04 anyway.
Thank you for your help.

---

