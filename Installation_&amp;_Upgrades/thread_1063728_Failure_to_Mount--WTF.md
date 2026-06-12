---
title: "Failure to Mount--WTF?"
date: 2009-02-08
forum: Installation &amp; Upgrades
---

### Post by jacobroecker on 2009-02-08
Ok this one has got my head hurting.  I've got a rather nice computer from my neighbour who had a bit of a security issue right before it died.  She wanted me to get the files off the machine, fix it up (install linux) and let her use it for her boys.

Ok, cool.  Not the first time I've done something like this.  So I start by loading the 8.10 CD in live mode so I can pull the files of the HD and onto an external.  Once on the external I figured I'd just go ahead and scan them to clean them for bugs.  

The Hard Drive wouldn't mount.

So it's got two drives.  I'll install Ubuntu on the nearly empty drive and then be able to mount the other one.  

The install wouldn't take on the secondary hard drive.

So I figured I'd just ignore the fact that I cared about her files, tell her there was no hope to save them, and install Ubuntu on the primary drive.

The install wouldn't take on the primary drive either.

So, I've never seen anything like this before.  This is an area of computing that I need some help with.  Her computer was obviously compromised.  At 3:00am of the last day it was working someone was using her bank information to withdraw all the money from her account.  Then "magically" both hard drives stopped working.

Can someone write a 'virus' or other bug to permanently damage the hard disks?  It's just a little suspicious to me that both hard drives died at the exact same time, and that both are now 'beyond repair.'

I'd appreciate knowing if security issues like this are real, and I'd appreciate any advice on how to move forward before I just go find another hard drive and stick the thing in there.  

Please advise.

-Jacob

---

### Post by demon_hunter on 2009-02-08
this is probaly a trojan horse and a key log virus mixed in some way.

I would personally hire someone to remove them 

But if you do this make sure they sign a contract for 

"complete virus removal"

overwise they could remove it and it could come back strait away because the havent done it proply

Demon_hunter

---

### Post by jacobroecker on 2009-02-08
Ok, so you're telling me that the drives might still be used even though there's no way to mount them?  Cool.  How do I do that?

As far as removal goes I'm sure that reformatting the entire drive will help remove the viruses.

---

### Post by taurus on 2009-02-08
When you said "The install wouldn't take on the primary drive either", what do you mean by that?  The installer doesn't know there is a harddrive or the installer can't write to it?

From the LiveCD, open a terminal and post the output of this command.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by demon_hunter on 2009-02-08
you would probably have to look for it on the terminal and force it to recognise it 

ask for the code for that as that's not my strong point

hope this helps

---

