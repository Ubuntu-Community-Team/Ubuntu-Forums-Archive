---
title: "gnump3d bash shell script issue"
date: 2009-01-14
forum: Installation &amp; Upgrades
---

### Post by Masiv on 2009-01-14
Hi all,

I am attempting to run gnump3d as a streaming server for my media/web/ftp server. Simple enough, and I know a ton of folks have already installed it to rousing success. However, I seem to be hitting a block, and I have no idea how to fix it. The reason for my stating this is a bash shell script issue, is because when I check the /etc/init.d/ folder, I cannot find the gnump3d shell script.

After I download the tarball, extract and make install, I can modify the gnump3d.conf file. After this is complete, I go ahead and attempt /etc/init.d/gnump3d restart. This returns me this:

sudo: etc/init.d/gnump3d: comman not found.

I have zero idea what I did wrong, or even if I received a bad install of gnump3d. I downloaded the most recent version from the website (3.0) and it seems as though everything is installed correctly after the "make install" command. I have the most recent version of apache2 and perl, so I know thats not the problem. Has anyone encountered this before? As I say above, when I check the /etc/init.d folder, I can find my proftpd and my samba shell scripts, but not the gnump3d one.

I wish I could just grab the bash shell script out of a zip file, but I don't think thats possible. Any help would be appreciated. Thanks!

---

### Post by LostDakota on 2010-03-03
I know this is a touch late, but I start gnump3d with ```
sudo gnump3d --fast --background
``` . I had an earlier version that started the way you describe, but it no works. The '--background' acts kinda like a daemon. Add that command to your startup programs.

---

