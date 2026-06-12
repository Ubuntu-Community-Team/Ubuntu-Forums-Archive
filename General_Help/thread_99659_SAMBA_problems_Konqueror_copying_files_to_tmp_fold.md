---
title: "SAMBA problems: Konqueror copying files to tmp folder"
date: 2005-12-06
forum: General Help
---

### Post by Ghostsyn on 2005-12-06
Here the situation - its basically that i have a fileserver setup with samba and everything works well (from windows) but when i try to access the share konqueror wont let me open things without it copying it to my tmp folder first. 

I can browse the share and copy files from it without a problem. I just cant do anything *directly* off of the share. Attempts to mount it (disk & filesystems) have returned a error. Can someone point me in the right direction for finding out the information i need to fix this? (keeping in mind that i am very much green to linux - but i take instruction well) thanks.:smile:

---

### Post by Ghostsyn on 2005-12-06
anyone?

---

### Post by jferrando on 2005-12-06
Try to mount them:

#!/bin/bash
#Mount samba filesystems
echo "Mount samba filesystems"
echo -n "User windows: "
read username
echo -n "Password windows: "
read -s password

mount -t smbfs //server/datos /home/username/datos -o username=$username,password=$password,uid=jferrando,gid=jferrando

---

### Post by mlomker on 2005-12-06
[QUOTE=Ghostsyn]anyone?[/QUOTE]

jferrando is correct--it'll only do that when it isn't mounted.  You should be able to mount your drives as he suggested.  I use a tool that's a little more sophisticated (and complicated) called **fusesmb**, but it really just does the same thing.

---

### Post by SteveH on 2005-12-13
Nope!

[COLOR="Sienna"]mount -t smbfs //octopus/sjh /octopus -o username=sjh,password=xyzxyz,uid=steve,gid=steve[/COLOR]

gives the following error:

[COLOR="Sienna"]mount: wrong fs type, bad option, bad superblock on //octopus/sjh,  missing codepage or other error[/COLOR]

But konqueror can see the samba share using the URL: [COLOR="Sienna"]smb://octopus/sjh[/COLOR] and the same username & password.

---

### Post by mlomker on 2005-12-13
I'm not sure what you're doing with the uid/gid there.  I found [this page]("http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html") yesterday and it is a great overview.  

I use a credentials file, myself...username/pass on the command-line had odd results for me (I think that's because I have special characters in my password).

---

### Post by SteveH on 2005-12-14
I tried using credentials, with and without uid/gid - still fails.

A search on Google suggested I may need the smbfs package. Is this correct? Where do I get it?

---

### Post by jferrando on 2005-12-14
Do you have **[COLOR="Red"]smbfs[/COLOR]** package installed?
If getting syntax problems, install [COLOR="Red"]**webmin**[/COLOR], log into the app,
[http://localhost:10000](http://localhost:10000),
and then go to filesystems dialog and add mount for the samba filesystem.

It's easy, you should not have problems with this.

---

### Post by mlomker on 2005-12-14
[QUOTE=SteveH]Is this correct? Where do I get it?[/QUOTE]

Yes, I was assuming that you had that installed.  It's in the repos, so you should see it in Synaptic.

---

