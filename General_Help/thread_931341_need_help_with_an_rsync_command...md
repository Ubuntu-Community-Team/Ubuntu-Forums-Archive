---
title: "need help with an rsync command.."
date: 2008-09-27
forum: General Help
---

### Post by srossnz on 2008-09-27
Hi,

I have a folder on my ubuntu desktop and it is an rsync of my website.  I use this command in terminal to do the sync:

rsync -av [email]root@xxx.xxx.xx.xx[/email]:/home /home/user/Desktop/rsync

Now, the problem is that if files are removed on my webserver these changes are not reflected in my local directory.  I am unsure what change in my code is needed to ensure my local copy has new data and also removes old data.  Thanks for any help!

---

### Post by koenn on 2008-09-27
rsync -av --delete /src /dest

means you'll delete files in /dest if they don't exist in /src.
man rsync and read the part about --delete

---

