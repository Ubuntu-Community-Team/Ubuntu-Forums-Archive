---
title: "Transferring forum from one server to another"
date: 2008-11-26
forum: General Help
---

### Post by Legal_bits on 2008-11-26
Hi!
Got referred to this forum by a good friend of mine.
I am the webmaster of a LARP organisation, very recently elected, and I found out the forum-server was windows based.
Having next to no experience with Linux, we have now purchased a Windows based one.
But I have no idea how to transfer the files from our old server, to our new.

(if you need additional information, you need only ask)

Any help would be greatly appreciated.


Cheers.

---

### Post by kanikilu on 2008-11-26
Knowing next to nothing about your servers, I can't say for sure, but if SSH is installed on the Linux server, you could always use a SFTP client on the Windows server to transfer the files from the old server. Personally, I use [WinSCP](http://winscp.net/) on Windows to do that.

---

### Post by Legal_bits on 2008-11-26
I have ssh installed yes, but how would I go about doing that?
Commands, etc.?

---

### Post by kanikilu on 2008-11-26
Is the Windows server operational now? If so, just install WinSCP on your Windows server, then connect to your Linux server (you just need the hostname or IP and a username/password) and transfer the files. You shouldn't need to do anything *from* the Linux server. If it's possible, I think this will be the easiest thing for you to do.

If the Windows server is not up yet, I suppose your only option would be to use external storage (USB or even NFS or SMB share on another server) and then transfer from this intermediate storage to the new server.

I can't really give you specific commands at this point. You might want to look into the sftp or scp commands though, if you are going to need to transfer the files from the Linux server to another server over the network.

---

### Post by Legal_bits on 2008-11-26
Great!
I'll try that right away!

My deepest thanks to you!

---

