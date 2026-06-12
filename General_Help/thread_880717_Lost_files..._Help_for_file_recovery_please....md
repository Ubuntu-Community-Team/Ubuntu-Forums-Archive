---
title: "Lost files... Help for file recovery please..."
date: 2008-08-05
forum: General Help
---

### Post by chris1979 on 2008-08-05
Hi!

Installed UBUNTU 8.04 desktop edition on my Asus M2N laptop recently by the Wubi installation method. Love UBUNTU and in particular the applications that go with it. I started experimenting with GIMP and made some really nice designs which I saved in the pictures folder.

Trying to update UBUNTU and install some packages to get the sound into the system, I must have done something completely wrong because UBUNTU refused to load since then.

Hoping to recover the lost files, I have now reinstalled UBUNTU, but I have tried to search for the files without any luck. I supposed the files should still be on my harddisk some place BUT WHERE? And how do I get hold of these files again? Is there some kind of special terminal command you can use to search the entire drive? Windows once crashed while all my pictures were still on the harddisk, but I managed to reinstall Windows and get the pictures onto a portable drive. I guess the same should be possible in UBUNTU or?

Hope someone is able to help be out.

Chris

---

### Post by hyper_ch on 2008-08-05
how did you reinstall?

---

### Post by caljohnsmith on 2008-08-05
Unfortunately, if you reinstalled Ubuntu over your previous Ubuntu that was not working, then realistically speaking you're not going to be able to recover those files. If you reinstalled somewhere else, then the chances are extremely high that you would be able to rescue those files.

For the future, if something like that happens again, you can boot up the Live CD for example, mount the Ubuntu partition that's on your HDD, and then copy the files you want to rescue over to say another partition, USB stick, etc.

---

### Post by aysiu on 2008-08-05
So you accidentally deleted that folder? You'll probably have to use *photorec* to recover those files. You may be able to get some of them back. Some may be unrecoverable if they were overwritten by the fresh Ubuntu installation.

I made a little tutorial on Photorec:
[http://www.psychocats.net/ubuntucat/recovering-windows-files-with-a-ubuntu-cd-iii-deleted-files/](http://www.psychocats.net/ubuntucat/recovering-windows-files-with-a-ubuntu-cd-iii-deleted-files/)

It's focused on recovering files from an NTFS partition, but you can just change the answer to that question to the Ext3 one and follow the rest of the same steps.

---

### Post by mangy_mathan on 2008-08-05
As has already been said, if you simply reinstalled and overwrote everything, you probably won't be able to recover the files. In the future, you may want to place your /home directory in its own partition, thus allowing you to overwrite and even ruin your root without harming your personal files.

There's a tutorial on how to do that.

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Wish there was more we could do.

---

### Post by aysiu on 2008-08-05
> **mangy_mathan said:**
> As has already been said, if you simply reinstalled and overwrote everything, you probably won't be able to recover the files. I disagree. As far as I can tell, reinstalling doesn't overwrite *everything*, only the space needed for the OS itself. So let's say it's a 60 GB hard drive and a fresh install of Ubuntu is 3.5 GB. Only 3.5 GB of the hard drive would be unrecoverable.

I think *photorec* is worth a shot. It may not save everything, but it could probably save most of the pictures.

---

### Post by dbeckwitt on 2008-08-05
if you want to do a quick scan of the HDD, and you know the filename, simply do the following
from a command prompt.  go to root  "cd /"
run the following " sudo find -name nameofyoufile.*"

---

### Post by Ptero-4 on 2008-08-05
Did you just delete the disk image (this is how wubi installs ubuntu)? If you did chances are your stuff went with it.

BTW. This should go to the Wubi section, since the OP says he installed through wubi.

---

### Post by dbeckwitt on 2008-08-05
if you want to do a quick scan of the HDD, and you know the filename, simply do the following
from a command prompt.  go to root  "cd /"
run the following " sudo find -name nameofyoufile.*"

---

### Post by aysiu on 2008-08-05
> **Ptero-4 said:**
> Did you just delete the disk image (this is how wubi installs ubuntu)? If you did chances are your stuff went with it.

BTW. This should go to the Wubi section, since the OP says he installed through wubi.
That's a good point. I've moved it over there.

chris1979, did you delete the disk image of Ubuntu, reinstall over it, or use a method other than Wubi for the reinstallation of Ubuntu?

---

