---
title: "I'm going mad! Desperate for help with mounting and..."
date: 2006-04-04
forum: Hardware &amp; Laptops
---

### Post by XPerienced on 2006-04-04
Hi!

It's almost 04.00 in my country and I'm going mad any second on f-ing Linux! 

I'm a beginner. I tired for a week and I like it alot, but now I'm going mad about two thing.

I formatted my harddrive with:
"sudo mke2fs -m 0 -j /dev/hdc" and that went good, but there's one annoying thing. The system shows 190 GB of 200 GB and that the same in Windows, but it take over 3 GB when it's formatted and that's too much. I thought I deactived it. It's for storage only. (EDIT: Deactiveated the "reservation" om 5%).

The next problem is that I can't mount the harddrive.

During the time I tried too configure SSH-server. Do you think a made it? No. I tried with FTP with SSL, I didn't make that either. In Windows it took about 20-30 minutes before everything was perfect, when I portforwarded, made accounts etc.

So what I so desperatelly need now is help! With this:

- Mounting my harddrive. I haven't made a directory. I could make it.

- Configure a FTP-client with SSL or SSH-server. It got to be a secure connection!

- And make the transfer work properlly.

I'm running out of patient. Oh, sorry. I mean I already did. ;-) 

It's complicated, but I need access to my files asap. And it annoys me I can't.

But I will continue the migration. I just need alot of help now to make it stable , the I promise I read books and learn my own way, but for now I need help.

XPerienced

---

### Post by Ptero-4 on 2006-04-04
For the mounting issues you need to check your /etc/fstab, you may have an outdated entry and that keeps your drive from getting mounted, you may also need to create a mount point for it but since you said that it worked fine b4 formatting it as ext3 you may have a mount point already.
For the FTP on SSL issue. You need SFTP (Secure FTP). SFTP is a protocol that allows FTP over SSL, regular FTP can't be run over SSL.

---

