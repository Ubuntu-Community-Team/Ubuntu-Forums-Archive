---
title: "Accessing Fileserver with Apps"
date: 2005-11-12
forum: General Help
---

### Post by Stormspace on 2005-11-12
I am running a Centos box and a Win2000 box as fileservers on my netowork. One hold documents and the other holds media files(Music, Video, Etc.). I want to be able to play and rip music directly to thw Win 2000 box through a file share, but none of the music apps I have tried allows for the music to not be local. Is there an app that does this? I've tried Xmms and Rhythmbox.

---

### Post by grendel_khan on 2005-11-13
Do you have the file share mounted on your Ubuntu box? If you have it mounted, you should be able to access it just like any part of the local filesystem.

---

### Post by Stormspace on 2005-11-13
It is mounted, but when I enter /home/mccallj/Desktop/Music into Xmms it won't take it. In fact if I just use the browse function none of the mounted shares show up in the file browser.

---

### Post by grendel_khan on 2005-11-16
So you can get to it in Nautilus (the regular file browser) but not in XMMS's file browser?

---

### Post by Stormspace on 2005-11-16
[QUOTE=grendel_khan]So you can get to it in Nautilus (the regular file browser) but not in XMMS's file browser?[/QUOTE]

Neither browser functions.

---

### Post by Stormspace on 2005-11-17
Just wanted to bump this thread. As a recap I cannot navigate through the filesystem to any mounted shares on my box. For instance a mounted share "Music" sitting on my desktop cannot be accessed via 

cd /home/username/Desktop/Music

Does that mounted share exist elsewhere? 

Also on the mounted shares I get prompted for a userid, domain, and password. I can fill in the information, but the prompt keeps coming back. If I click cancel the share opens and displays the contents fine. Do I need to change a config file somewhere to to keep this from happening. 

I'm using a Peer tp Peer network, not a network with a domain, but I DID boot this PC onto a domain during part of the setup process.

---

### Post by grendel_khan on 2005-11-22
Could you paste in the output of 'mount'?

---

### Post by Stormspace on 2005-11-22
[QUOTE=grendel_khan]Could you paste in the output of 'mount'?[/QUOTE]

I would if I knew how. I used the "connect to network server" option in the places menu. Is there a place to go and capture the mount information?

---

### Post by mannheim on 2005-11-22
Remore shares that are put on the desktop are not actually "mounted" in the unix sense, I believe. They are therefore not part of the filesystem under / or /mnt or anywhere else.

Some gnome applications can access them, via the usual "Open" dialog box which has a list of places on the left pane, including these mounts. But most applications can't.

So mostly, you have to drag and drop and copy files from the share to somewhere local where you can use them.

If you want to really "mount" the share as part of the filesystem, I think you need another tool. For example the package "smbfs" (available in the official repositories) has tools which allow you to really mount a Windows (smb) share.

---

### Post by Stormspace on 2005-11-22
OK, That makes sense. I'll check out that program and see if I can get it configured. Thx!

---

