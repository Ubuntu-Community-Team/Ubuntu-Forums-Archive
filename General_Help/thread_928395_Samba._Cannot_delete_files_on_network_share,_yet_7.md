---
title: "Samba. Cannot delete files on network share, yet 777 rights were granted."
date: 2008-09-23
forum: General Help
---

### Post by Roasted on 2008-09-23
I have a Samba setup here. Everybody writes to my desktop as a means of backing up files.

My brother is unable to delete files in his share. He gets "make sure the disk is not full or write-protected and that the file is not currently in use."

I granted 777 rights to his folder. Why the hell is it denied? What can I look for? I thought sudo chmod 777 to his folder was all I'd need to do to give him full blown access.

---

### Post by Meson on 2008-09-23
There are separate permissions for the share.  They are applied over the actual permissions of the directory in the filesystem.  So the directories permissions on your computer represent he most lenient permissions possible, however when you create the share you can limit them further (but not reduce them).

To edit the permissions of the share you need to look in /etc/samba/smb.conf or I'm pretty sure Ubuntu has a nice GUI for doing it.

---

### Post by Roasted on 2008-09-24
Where in smb.conf? I'm looking all over the entire config file and I see nothing relevant to what I need.

Only thing I see is simply

Browseable = yes
Writable = yes

djfaklsjdl;kfsa

---

### Post by Roasted on 2008-09-24
Let me just be a little more descriptive here since I'm about to hit the sack for the night.

I set up Samba. My brother has a share on my computer. It's mapped on his XP computer. I noticed he had his backup kind of sloppy, as far as how things were organized. I went to move everything to a folder and delete everything else, and it said access denied. It won't let me delete anything.

So I thought I'd try in the GUI of my Ubuntu machine. Nope. Still can't. 

"share" is the main directory on my spare hard drive for backups.
"curt" is a folder (user) that resides in the share folder for backups.

I granted 777 rights to "share"

Doesn't curt and all of the others in the share folder take on the same rights?

Note - I even tried issuing 777 rights to curt's individual folder, and it still barked at me with an error.

The Goal: I need Curt to be able to read/write/delete ANY file and ANY folder within "share/curt". That is HIS folder for backing items up, I want him to organize it the way he would like.

---

### Post by Meson on 2008-09-24
You need to read the smb.conf manual page, you can access it by typing "man smb.conf" into the terminal.

You'll be adding a section that defines your brother share (or modifying the current one) to something like:
```

[curts_share]
path = /share/curt
read only = no

```

There is an ENORMOUS amount of options listed in this file.  There are quite a few options which allow you to specify permissions in the octal format.  You need to look through the man page and define the share exactly how you want it.  (And again, I'm pretty sure that there is a GUI somewhere to help you do this)

---

### Post by Roasted on 2008-09-24
fyi, adding that tag didn't work. 

I'll read the man page tomorrow. I'm past due on sleep. Thanks for the help thus far! I'll post back tomorrow afternoon when I work on this some more.

Anymore from anybody else, awhile?

---

### Post by FluffyElmo on 2008-09-24
From the command line you can give chmod a -R option to make it recursively change permissions on all files/sub-directories. The default is to just change the directory you specify. 

So from the command line above share you could type:
```
chmod -R 777 ./share/*
```

The '/*' may not be necessary but won't hurt. If you get an error try running it with *sudo* in front of the command. Also, typing *ls -l* in a directory will show a detailed directory listing with permissions and file sizes shown.

---

### Post by Meson on 2008-09-24
> **Roasted said:**
> Anymore from anybody else, awhile?

Roasted... are you from PA?


Changing the permissions of the directory is not what you need to do.  You need to change the permissions of the SHARE.  Think of the share as a layer inbetween the directory and the remote user.  The user sees the permissions of the SHARE not the directory.  The share only has access to the folder as far as the directory permissions let it.

So if the directory is rwx, the share can do whatever it wants.  If the directory is r-x, then the share can at best be r-x, but it can aslo be r-- or --x or ---, but it can never be rwx or -w-, or anything with a write.

---

### Post by bab1 on 2008-09-24
@ Meson,

> There are separate permissions for the share. They are applied over the actual permissions of the directory in the filesystem....

> Changing the permissions of the directory is not what you need to do. You need to change the permissions of the SHARE. Think of the share as a layer in between the directory and the remote user.

These two statements are not so.  The Samba server in no way grants or denies permissions for the file system.  Samba only *[COLOR="RoyalBlue"]authenticates[/COLOR]* the users access to the share.  All *[COLOR="SeaGreen"]authorization[/COLOR]* is done through the FS permissions.  File creation can be controlled Samba with create and dir masks.  In my Samba setup I force a common group (smbusers) even if it is a guest (I named smbguest).  It's even possible to limit the authenticated users ability to delete files, but this is done using the Linux "sticky bit", not Samba.  

@ Roasted,
I can't tell you without seeing the file structure why the world rights are not allowing the files to be moved or deleted but the answer is in the FS structure and user ownership. Not *** directly ***with Samba.

How about a post of with how you mounted the share, some the directory contents and file structure, and the share portion of your smb.conf file.

---

### Post by TeXtonyx on 2008-09-24
You asked for any ideas. I have one though it may not apply. Firefox inexplicably refused
to download files into /home/textonyx/Downloads. I tried chmod 777 lots of time on the
Downloads directory and they all failed. Finally I tried chown, after  finding out the 
reason I couldn't download was because the directory was owned by root and it wouldn't
let an ordinary user write to it. I have not tested to see if this idea applies to Samba shares.
The good news is that I came across a bunch of excellent tutorials by swerdna.
[http://www.swerdna.net.au/linux.html](http://www.swerdna.net.au/linux.html)
A Script that Troubleshoots Samba
Automagically diagnose configuration errors for Workgroups 
TeX: He has several other tutorial pertaining to Samba also. 
It may be a group hug thing, good luck  -- TeXtonyx

---

### Post by Roasted on 2008-09-24
> **TeXtonyx said:**
> You asked for any ideas. I have one though it may not apply. Firefox inexplicably refused
to download files into /home/textonyx/Downloads. I tried chmod 777 lots of time on the
Downloads directory and they all failed. Finally I tried chown, after  finding out the 
reason I couldn't download was because the directory was owned by root and it wouldn't
let an ordinary user write to it. I have not tested to see if this idea applies to Samba shares.
The good news is that I came across a bunch of excellent tutorials by swerdna.
[http://www.swerdna.net.au/linux.html](http://www.swerdna.net.au/linux.html)
A Script that Troubleshoots Samba
Automagically diagnose configuration errors for Workgroups 
TeX: He has several other tutorial pertaining to Samba also. 
It may be a group hug thing, good luck  -- TeXtonyx


When I right click on the folders in particular, it says Jason owns Jason, and root owns everything else.

How can I fix this? Do I have to have the users on this system as admins?

---

### Post by Meson on 2008-09-24
> **bab1 said:**
> Samba only *[COLOR="RoyalBlue"]authenticates[/COLOR]* the users access to the share.  All *[COLOR="SeaGreen"]authorization[/COLOR]* is done through the FS permissions. 

Samba can control the permissions of the share.  The path to a Samba share can have a mode of 777 (rwxrwxrwx) but the share definition can limit the share to be read only.

It's just like in Windows if you disable "Simple file sharing" then for each folder you see a Share tab and a Security tab.  The Security tab controls the permissions of the folder on the local system while the Share tab controls the effective permissions of a remote user.  The Share permissions can be as lenient but no more lenient then the permissions set by the Security tab.

The same goes for Samba.  The directory permissions are just the limiting factor.  If the OP wants to control the share permissions through the filesystem permissions, then he should enable full read-write access through the share and adjust the filesystem accordingly.  What seems to be the case though, is that the default permissions for the Samba share are read-only.

---

### Post by Roasted on 2008-09-24
Read only? They can write to their shares. They just can't delete. But it's only certain files. Like if I create a blank folder, I can delete it. But the folder he wrote to the computer last week? Can't delete it.

I just need to make sure they have full blown full control of their designated share. Each share is password protected with their own account, so as long as Curt can do whateverrrrrr Curt wants to do to his folder, he can. 

Make sense?

---

### Post by bab1 on 2008-09-24
I really hate to quote myself but:> Not  directly with Samba.  I say this because the OP stated: > Only thing I see is simply

Browseable = yes
Writable = yes

Yes, Samba can control browse and write, but the OP says that the share **is writeable**.

later he states:> Read only? They can write to their shares. They just can't delete. But it's only certain files. Like if I create a blank folder, I can delete it. But the folder he wrote to the computer last week? Can't delete it.

His problem is with the file system and not Samba.

EDIT:
> When I right click on the folders in particular, it says Jason owns Jason, and root owns everything else.

How can I fix this? Do I have to have the users on this system as admins?

Use:```
chown
```

This is the tool to change ownership of files and directories

---

### Post by Roasted on 2008-09-24
Yeah, I understand my problem isn't Samba. It's the permissions on the folders themselves.

Sooo... how do I fix it?

---

### Post by bab1 on 2008-09-24
> Yeah, I understand my problem isn't Samba. It's the permissions on the folders themselves.

Sooo... how do I fix it?

As I said, it might be *[COLOR="Darkgreen"]ownership[/COLOR]* of the files.  This is can be changed by the **[COLOR="Red"]chown[/COLOR]** command.  We can't see your file structure, so we don't know for sure.  Try listing the output of ```
ls -l
``` of the directory in question.

EDIT: We need to see the perms and ownership of both the **directory and the files**

---

### Post by Roasted on 2008-09-24
I'll be home in a couple hours. I'll upload some screenshots then. Thanks!

---

### Post by bab1 on 2008-09-24
Thanks for letting me know.  I'll be out for a while too.  :-)

Edit:  A tip -- just capture the output and paste it in side the [code] brackets.  This is the # icon in the advanced menu

---

### Post by Meson on 2008-09-24
> **Roasted said:**
> Read only? They can write to their shares. They just can't delete.

This issue is still with smb.conf.  You need to change the fmask and dmask of the files that are created.  You should want something like read-write for files and read-write-execute for folders.  (6 and 7 respectively)  Keep in mind that when talking about file permissions, "mask" is the opposite of what you want to take place (so 1 and 0 respectively)

---

### Post by kylebridge on 2008-09-24
Here's the command I used and it worked, for a while...

sudo chown -hR username /home/server/Public/Calendars

It changes ownership of the folder to username, and all of the files contained.

The problem I'm having is as soon as a windows user accesses or saves one of the shared files, the owner changes back to "nobody". Is there any way I can permanently change the owner? I'm sharing about 3 dozen files in a Windows workgroup, and can't have these files become unavailable to the users.  I'm also really new to Linux, I've only been using Ubuntu for a week or two, so I'm a little gun shy about changing a lot of this stuff.

---

### Post by Roasted on 2008-09-24
> **Meson said:**
> This issue is still with smb.conf.  You need to change the fmask and dmask of the files that are created.  You should want something like read-write for files and read-write-execute for folders.  (6 and 7 respectively)  Keep in mind that when talking about file permissions, "mask" is the opposite of what you want to take place (so 1 and 0 respectively)

I don't believe that's true. Here's why.

My folder is perfectly fine. Curt, Tyler, and Pam's are not.

For the user section in the smb.conf file, each user has the same exact permission.

Yet, mine is fine. Their's is not. How is that still a Samba issue? Besides, I've used this SAME EXACT smb.conf file before. I have it saved on a flash drive, so whenever I format I just load it back up and everything works.

---

### Post by stickmangumby on 2008-09-24
It seems like this discussion is going around in circles a bit.

We need you to post the output of the following:

```

sudo testparm

```

(Press enter when it prompts you to press it to "see a dump of your service definitions)

And:

```

pwd
ls -al

```
(From the root of your shares).

To quote the smb.conf man page, "The access rights granted by the server are masked by the access rights granted to the specified or guest UNIX user by the host system. The server does not grant more access than the host system grants."

---

### Post by Meson on 2008-09-24
> **Roasted said:**
> My folder is perfectly fine. Curt, Tyler, and Pam's are not.

But aren't you accessing your folder from your local computer and they from a remote computer via Samba?

Try showing us some info like the output of the following:
```

$ ls -al /samba_share
$ ls -al /samba_share/curt
$ ls -al /samba_share/pam
$ ls -al /samba_share/roasted

$ cat /etc/samba/smb.conf

```

Also, place the output between code tags (<code> stuff </code> - replace the <> with []) so it's easier to read.  One for the ls commands and one for smb.conf.

I've also found AppArmor to be the culprit in mysterious permissions issues.  Try disabling it for awhile: ```
$ sudo /etc/init.d/apparmor stop
```

---

### Post by bab1 on 2008-09-24
I agree with stickmangumby.  We are getting nowhere just talking.  Nothing can be dianosed without the data. 

Not to be jumping on Meson all the time, but this is wrong:> Keep in mind that when talking about file permissions, "mask" is the opposite of what you want to take place (so 1 and 0)...

The linux umask is that way but not Samba.  See: [http://www.cyberciti.biz/tips/how-do-i-set-permissions-to-samba-shares.html]("http://www.cyberciti.biz/tips/how-do-i-set-permissions-to-samba-shares.html")

---

### Post by bab1 on 2008-09-24
> But aren't you accessing your folder from your local computer and they from a remote computer via Samba?

Don't assume anything.  ;-)

---

### Post by Meson on 2008-09-24
> **bab1 said:**
> Not to be jumping on Meson all the time, but this is wrong:

The linux umask is that way but not Samba.  See: [http://www.cyberciti.biz/tips/how-do-i-set-permissions-to-samba-shares.html]("http://www.cyberciti.biz/tips/how-do-i-set-permissions-to-samba-shares.html")

*kneels*  - my bad, there I go assuming again!

---

### Post by Roasted on 2008-09-24
sudo testparm-



jason@jason-hardy:~$ sudo testparm
[sudo] password for jason: 
Load smb config files from /etc/samba/smb.conf
Processing section "[jason]"
Processing section "[curt]"
Processing section "[tyler]"
Processing section "[pam]"
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
	netbios name = HARDY
	server string = %h server (Samba, Ubuntu)
	obey pam restrictions = Yes
	passdb backend = tdbsam
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *passwd:*password\supdated\ssuccessfully* .
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	panic action = /usr/share/samba/panic-action %d
	invalid users = root

[jason]
	path = /home/jason
	invalid users = curt, tyler, pam
	valid users = jason
	read only = No

[curt]
	path = /media/share/curt
	invalid users = pam, tyler
	valid users = curt, jason
	read only = No

[tyler]
	path = /media/share/tyler
	invalid users = curt, pam
	valid users = tyler, jason
	read only = No

[pam]
	path = /media/share/pam
	invalid users = curt, tyler
	valid users = pam, jason
	read only = No

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
jason@jason-hardy:~$ 




ls -al


jason@jason-hardy:~$ ls -al
total 1116
drwxr-xr-x  66 jason jason   4096 2008-09-24 21:21 .
drwxr-xr-x   7 root  root    4096 2008-08-05 17:53 ..
drwx------   3 jason jason   4096 2008-07-08 22:15 .adobe
drwxr-xr-x   2 jason jason   4096 2008-09-24 00:03 Alice in Chains
drwxr-xr-x   2 jason jason   4096 2008-09-21 13:16 .audacity1.3-jason
drwxr-xr-x   4 jason jason   4096 2008-09-21 13:16 .audacity-data
drwxr-xr-x   3 jason jason   4096 2008-07-10 20:08 .avidemux
-rw-------   1 jason jason   9951 2008-09-24 08:14 .bash_history
-rw-r--r--   1 jason jason    220 2008-07-08 17:33 .bash_logout
-rw-r--r--   1 jason jason   2940 2008-07-08 17:33 .bashrc
drwxr-xr-x   4 jason jason   4096 2008-07-08 21:50 .cache
drwxr-xr-x   2 jason jason   4096 2008-09-21 13:16 Chopped MP3s (ringtones)
drwx------   3 jason jason   4096 2008-07-10 22:33 .compiz
drwxr-xr-x  10 jason jason   4096 2008-07-21 23:05 .config
-rw-r--r--   1 jason jason     58 2008-09-24 08:09 .DCOPserver_jason-hardy__0
lrwxrwxrwx   1 jason jason     38 2008-09-24 08:09 .DCOPserver_jason-hardy_:0 -> /home/jason/.DCOPserver_jason-hardy__0
drwxr-xr-x   2 jason jason   4096 2008-09-24 00:37 Desktop
-rw-------   1 jason jason     26 2008-09-24 00:15 .dmrc
drwxr-xr-x   7 jason jason   4096 2008-08-29 15:07 Documents
drwxr-xr-x   3 jason jason   4096 2008-09-15 22:31 .dropbox
drwxr-xr-x   5 jason jason   4096 2008-07-20 01:49 .dvdcss
-rw-------   1 jason jason     16 2008-07-08 21:39 .esd_auth
drwxr-xr-x   7 jason jason   4096 2008-09-23 20:19 .evolution
drwx------   2 jason jason   4096 2008-09-15 18:02 .filezilla
drwxr-xr-x   9 jason jason   4096 2008-05-22 19:21 Finished
drwxr-xr-x   2 jason jason   4096 2008-08-08 02:06 .fontconfig
drwxr-xr-x   5 jason jason   4096 2008-07-14 23:07 FrostWire
drwxr-xr-x   6 jason jason   4096 2008-09-23 20:59 .frostwire4.17
drwx------   5 jason jason   4096 2008-09-24 00:15 .gconf
drwx------   2 jason jason   4096 2008-09-24 21:23 .gconfd
drwxr-xr-x  22 jason jason   4096 2008-09-22 00:05 .gimp-2.4
-rw-r-----   1 jason jason      0 2008-09-24 17:44 .gksu.lock
drwxr-xr-x   3 jason jason   4096 2008-08-03 13:15 .gnome
drwx------  14 jason jason   4096 2008-09-23 22:51 .gnome2
drwx------   2 jason jason   4096 2008-09-14 01:30 .gnome2_private
drwx------   2 jason jason   4096 2008-09-24 00:15 .gnupg
drwx------   6 jason jason   4096 2008-08-12 16:20 .googleearth
drwxr-xr-x   9 jason jason   4096 2008-05-12 20:29 google-earth
drwxr-xr-x   2 jason jason   4096 2008-08-09 13:11 .gstreamer-0.10
-rw-r--r--   1 jason jason    108 2008-09-24 00:16 .gtk-bookmarks
-rw-r--r--   1 jason jason    222 2008-08-11 20:41 .gtk-custom-papers
dr-x------   3 jason jason      0 2008-09-24 00:15 .gvfs
drwxr--r--   2 jason jason   4096 2008-09-16 22:45 .hardinfo
-rw-------   1 jason jason  19469 2008-09-24 08:09 .ICEauthority
drwxr-xr-x   3 jason jason   4096 2008-07-12 01:34 .icons
drwxr-xr-x   2 jason jason   4096 2008-09-23 20:27 Incomplete
drwxr-xr-x   4 jason jason   4096 2008-08-25 23:05 .java
drwx------   3 jason jason   4096 2008-07-10 22:09 .kde
-rw-r-----   1 jason jason      6 2008-08-25 23:46 .ktorrent.lock
drwxr-xr-x   3 jason jason   4096 2008-07-08 21:39 .local
drwx------   3 jason jason   4096 2008-07-08 22:15 .macromedia
drwxr-xr-x   3 jason jason   4096 2008-07-10 22:11 .mcop
drwx------   3 jason jason   4096 2008-07-08 21:39 .metacity
drwx------   4 jason jason   4096 2008-07-09 00:23 .mozilla
drwx------   3 jason jason   4096 2008-07-09 00:23 .mozilla-thunderbird
drwxr-xr-x   2 jason jason   4096 2008-07-12 22:59 .mplayer
drwxr-xr-x 100 jason jason   4096 2008-09-01 00:03 Music
drwxr-xr-x   2 jason jason  20480 2008-09-21 12:48 Music Videos
drwxr-xr-x   3 jason jason   4096 2008-09-21 21:06 .nautilus
drwx------   3 jason jason   4096 2008-08-26 17:03 .openoffice.org2
drwxr-xr-x  53 jason jason   4096 2008-09-14 10:54 Pictures
-rw-r--r--   1 jason jason    586 2008-07-08 17:33 .profile
drwxr-xr-x   2 jason jason   4096 2008-07-14 23:19 .pulse
-rw-------   1 jason jason    256 2008-07-08 21:39 .pulse-cookie
drwx------   5 jason jason   4096 2008-09-24 21:18 .purple
drwxr-xr-x   2 jason jason   4096 2008-08-05 17:34 .qt
drwxr-xr-x   2 jason jason   4096 2008-07-22 22:00 .quicksynergy
-rw-------   1 jason jason   2188 2008-08-31 23:23 .recently-used
-rw-r--r--   1 jason jason 745716 2008-09-24 21:21 .recently-used.xbel
-rw-r--r--   1 jason jason    237 2008-09-16 16:14 .registry
drwxrwx---   3 jason jason   4096 2008-08-02 14:14 .sane
drwxr-xr-x   2 jason jason   4096 2008-09-24 08:14 Shared
drwx------   2 jason jason   4096 2008-07-08 21:39 .ssh
-rw-r--r--   1 jason jason      0 2008-07-08 21:40 .sudo_as_admin_successful
drwxr-xr-x  52 jason jason   4096 2008-07-12 02:09 .themes
drwx------   5 jason jason   4096 2008-07-12 11:47 .thumbnails
drwxr-xr-x   5 jason jason   4096 2008-08-25 23:45 .transmission
-rw-------   1 jason jason   1947 2008-07-17 23:13 .Trash
drwxr-xr-x   2 jason jason   4096 2008-07-08 21:40 .update-manager-core
drwx------   2 jason jason   4096 2008-07-25 16:52 .update-notifier
drwxr-xr-x   3 jason jason   4096 2008-09-16 16:19 USB Jumpdrive Backup
drwxr-xr-x   2 jason jason   4096 2008-09-16 16:14 Videos
drwxr-xr-x   3 jason jason   4096 2008-07-20 01:48 .vlc
drwxr-xr-x   2 jason jason   4096 2008-08-09 13:29 .wapi
-rw-------   1 jason jason    122 2008-09-24 00:15 .Xauthority
drwxr-xr-x   2 jason jason   4096 2008-07-17 23:09 .xine
-rw-r--r--   1 jason jason    146 2008-07-13 16:23 .xscreensaver-getimage.cache
-rw-r--r--   1 jason jason   9352 2008-09-24 21:23 .xsession-errors
jason@jason-hardy:~$ 




Note-

On my local desktop, everything works for me.
On my laptop exploring my share on my desktop, everything works for me.
On my local desktop as well as my laptop, I cannot delete files in curt/tyler/pam's directories... just like they can't delete files on their local computers from within their server share.

So, yeah, shouldn't be assuming. :P I was using my laptop as a neutral testing ground with this situation.

---

### Post by bab1 on 2008-09-24
A good example of people "[COLOR="RoyalBlue"]***separated by a common language".***[/COLOR]

We really need to see the directory structure [COLOR="Red"]*where the problem is*[/COLOR].  So if the problem is [COLOR="Blue"]/media/share/USER[/COLOR], then we should be looking at that.  In plain English, show us /media/share/ and /media/share/curt and /media/share/tyler and /media/share/pam.

[COLOR="Green"]*Just because you can do something doesn't mean you should do it.*[/COLOR]

```
[jason]
	path = /home/jason
	invalid users = curt, tyler, pam [COLOR="Red"]<-this is not needed[/COLOR]
	valid users = jason
	read only = No

[curt]
	path = /media/share/curt
	invalid users = pam, tyler [COLOR="Red"]<-this is not needed[/COLOR]
	valid users = curt, jason
	read only = No

```

[COLOR="Green"]*On the other hand, this is recommended.*[/COLOR]

```
[curt]
	path = /media/share/curt
	valid users = curt, jason
	read only = No
[COLOR="Red"]        create mask = 777
        directory mask = 777[/COLOR]


```

[COLOR="Green"]*Some good practice rules might be:*[/COLOR]

1. All Samba users must be part of the same group
 -- My users are all in the smbusers group.

2. All private directories should be controlled by the use of the [homes] share.  
 -- My users are all in the /smb/home path.  
 -- See mine below:
```
[homes]
        comment = Samba Home Directory
        path = /smb/home/%S  [COLOR="Blue"]<----This can be /media/share/%S[/COLOR]
        browseable = no
        guest ok = no
; Only the logged in user allowed
        valid users = %S +smbusers [COLOR="Blue"]<-- +smbusers is the group[/COLOR] 
        force group = smbusers
        writable = yes
        create mask = 770
        directory mask = 770

```

---

### Post by Roasted on 2008-09-24
I took your advice on removing invalid users and adding the 777 lines, but is the smbusers thing really necessary? I used to have this working perfectly, so I know it's possible to run without the additional smbusers thing. *shrug*

I'm just going to compare Jason (my folder, works) and Curt's. Whatever is wrong with Tyler, Pam, and Curt is the same thing, I know that much. So to keep things simple we'll just work with Curt here.

The following is a screenshot of Curt's permissions as well as mine. Is this what you guys wanted? Maybe I'm missing something but I wasn't sure what else you guys would need.. Hope this is it.


[http://s2.photobucket.com/albums/y36/Roasted/?action=view&current=samba1.png](http://s2.photobucket.com/albums/y36/Roasted/?action=view&current=samba1.png)

[http://s2.photobucket.com/albums/y36/Roasted/?action=view&current=samba2.png](http://s2.photobucket.com/albums/y36/Roasted/?action=view&current=samba2.png)

---

### Post by bab1 on 2008-09-24
So what happened when you added/deleted the various bits in smb.conf?  You did restart the smbd daemon; right?

Did you look to see if those permissions showed up on the newly created files and folders?

> but is the smbusers thing really necessary?

Jason, nothing is necessary, it just works more consistently.  I think the operative words are [COLOR="Blue"]"I used to have this working perfectly..."[/COLOR]  We want it to work now.  What changed?

The use of a common group allows for easier management.  It is not needed if the others can take care of themselves.  But they are not able (by your account), and you are the go to man!  It makes ***your*** life easier.

The screen shots don't really mean anything to me.  You need to capture the data of ls -l on the directory we are testing and paste it into a reply.  We can't help you very much if you can't supply the data.

I think it is a good idea on your part to only test one users directory.  Once that is correct you can apply it to the others.  As you said.  ;-)

---

### Post by Meson on 2008-09-25
We wanted to see the permissions from the command line.  So  you need to type "ls -al /media/share/curt" from the terminal.  Then you can copy and paste it into the thread.  Also, if you place the text within the CODE tags, it makes it a lot easier for us to read because stuff inside the code tags is displayed with a fixed-width font.  You see the difference?

```
~$ ls -al /media
total 28
drwxr-xr-x  7 root root 4096 2008-09-25 01:32 .
drwxr-xr-x 21 root root 4096 2008-09-15 00:43 ..
d---------  2 root root 4096 2008-09-22 23:02 usb1
d---------  2 root root 4096 2008-09-22 23:05 usb2
lrwxrwxrwx  1 root root    6 2008-09-14 22:46 cdrom -> cdrom0
d---------  2 root root 4096 2008-09-14 22:46 cdrom0
d---------  2 root root 4096 2008-09-22 19:34 external
drwxr-xr-x  7 root root 4096 2008-09-18 14:39 weirdo

```

vs

~$ ls -al /media
total 28
drwxr-xr-x  7 root root 4096 2008-09-25 01:32 .
drwxr-xr-x 21 root root 4096 2008-09-15 00:43 ..
d---------  2 root root 4096 2008-09-22 23:02 usb1
d---------  2 root root 4096 2008-09-22 23:05 usb2
lrwxrwxrwx  1 root root    6 2008-09-14 22:46 cdrom -> cdrom0
d---------  2 root root 4096 2008-09-14 22:46 cdrom0
d---------  2 root root 4096 2008-09-22 19:34 external
drwxr-xr-x  7 root root 4096 2008-09-18 14:39 weirdo

Much easier to read the first.

bab1 also makes a good point.  be sure to restart samba after you change the config file!  you can do this by typing "sudo /etc/init.d/smb restart" from the command line (where smb is the samba daemon - i'm not sure what the exact name is on your computer)

And look, if you've typed "sudo chmod -R 777 /media/share" into the command line, then restart samba - or even just restarted your whole computer - then the issue is not the file permissions.  Have you set the permissions like that?

---

### Post by Roasted on 2008-09-25
Yup. I did sudo chmod -R 777 /media/share

And yes, I restarted samba daemons.

edit-

Not to step on your toes, guys... I appreciate the help, but part of me is thinking I forgot one of my usual steps I take when I set up Samba. 

Perhaps what I should do is set up a guide for myself to set up Samba the way I usually like. Then I can post it here and you folks can critique it.

To do a basic start, all I basically do is this...

1 - Install Samba + SMBFS to my Ubuntu machine.
2 - Add users to my Ubuntu machine.
3 - Add users to Samba. I believe it's like sudo smbpasswd -a jason, etc.
4 - Edit the smb.conf file and paste in my existing smb.conf.
5 - On my shared hard drive, I create the user directories on it. When I did this last time, I granted 777 rights to each folder individually after creating it.
6 - Then I stop/start the Samba daemons.

Can you folks see anything blatantly wrong? After I get down some concrete steps I'm going to write these down and keep handy whenever I do a reinstall... such as soon whenever I install Intrepid...

---

