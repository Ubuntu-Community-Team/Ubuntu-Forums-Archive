---
title: "Problem to save on SMB network share"
date: 2008-11-05
forum: General Help
---

### Post by Memes11 on 2008-11-05
Hello,

I am a pure noob on Linux, I just come to Ubuntu 8.04 one month ago, and updated to 8.10 when it was available.

I face now a problem to write files on my NAS mounted in Samba. The problem appears in OpenOffice (Error saving the document <Name> General input/output error while accessing <FilePath>) and in TheGimp (Saving'<filePath>' failed : Could not open '<FilePath>' for writing : Not a directory). Copying file on the NAS, deleting it, ... all the basic operation work fine

I ran some tests and here are the results. All files are opened by double click in the file browser. I did the below serie with The Gimp (as I saw that OpenOffice problem may be something else). 
- file on the NAS, I save it under the same name and path. I got the error
- file in /home/Vincent. I save it under the same name and path. it works
- file on the NAS, I then save it in /home/Vincent (the file is not there yet). it works
- file on the NAS, I then save it in /home/Vincent (the file is already there, so need to replace it). it works
- file in /home/Vincent, I then save it on the NAS (the file is not there yet). it works
- file in /home/Vincent, I then save it on the NAS (the file is already there, so need to replace it). I got the error.

According to the above, it seems the problem is to rewrite an existing file.

For info, here is one line of my fstab file :

//QnapTS109/Public /media/NAS/Public	smbfs		username=desktop,password=desktop,ip=192.168.0.122,file_mode=0777,dir_mode=0777,iocharset=utf8	0	0

Does anybody already meet this issue?

Thanks

---

### Post by Memes11 on 2008-11-05
Hello again.

I forgot to say that the user "desktop" have full access on my NAS.

---

### Post by Memes11 on 2008-11-05
Hello,

I think I got the proof that it is indeed the Samba connection the issue. I copied some files with a copy paste in the file browser. one was already there, I asked for replacement and it failed. 

We got the same configuration as above.

Any ideas how to solve it?

Thanks

---

### Post by Memes11 on 2008-11-06
Anybody?

if it can helps, my NAS is a Qnap TS-109

---

### Post by Dilligaf on 2008-11-06
See this thread, it sounds like an ownership issue:  [http://ubuntuforums.org/showthread.php?t=731109 ]("http://ubuntuforums.org/showthread.php?t=731109")


Mike

---

### Post by webconnect on 2008-11-07
I am getting this same error:
"Error Saving: Not a directory"

Same results in Eclipse, same results in gedit.

My server is another ubuntu home server. It has not changed at all. I recently upgraded to 8.1 and this happened. I am using the same fstab setup as I was before it quit working.


:popcorn:

---

### Post by Memes11 on 2008-11-07
Hello,

Thanks for the advice, but I tried adding the gid and uid and still the same mistake. 

To be noted, this issue happened after upgrade to 8.10

---

### Post by psychopot on 2008-11-07
Some problem here after upgrading to Ubuntu 8.1 (from 8.04).

Here's my smb_connect_script:

sudo mount -t smbfs //%IP-addres%/Systeembeheer /home/%user%/Shares/Systeembeheer -o credentials=/root/.credentials,uid=1000,gid=1000

---

### Post by vivitron on 2008-11-08
I'm having the same issue after upgrading to 8.10... No problems in Hardy... but I must say, it is a huge problem here!

---

### Post by Memes11 on 2008-11-11
Did one bug was opened concerning this issue? If no, is there anybody who can do it?

---

### Post by rylleman on 2008-11-12
I too have this error.
Local drives ok, network drives, can't overwrite. Also if I try a chmod on a network file/folder I get "chmod: changing permissions of `testing2': Not a directory"
Machines still using 8.04 in network does not have this problem, only upgraded ones.
Is this a samba error?, Where do I file a bug report?

---

### Post by rylleman on 2008-11-12
There are a few bug reports on this. Seems to be a kernel error and using an older one seems to be the only solution for now...
[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/286828]("https://bugs.launchpad.net/ubuntu/+source/samba/+bug/286828")
[http://https://bugs.launchpad.net/ubuntu/+source/linux/+bug/279789]("/https://bugs.launchpad.net/ubuntu/+source/linux/+bug/279789")

---

