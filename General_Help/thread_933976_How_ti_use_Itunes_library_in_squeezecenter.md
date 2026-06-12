---
title: "How ti use Itunes library in squeezecenter"
date: 2008-09-30
forum: General Help
---

### Post by renewest on 2008-09-30
In his [blog entry]("http://shadow-file.blogspot.com/2008/09/itunes-and-squeezebox-integration.html") Zach Cutlip describes how to set various rights in order to use your Itunes library in Squeezecenter on Ubuntu.
Being new to Ubuntu I don't quite understand what is going on there and what to do in my specific situation. 

I keep my Itunes file on a Ubuntu server that has a Samba share (/home/rene/music) mapped to drive M: on my windows pc.
 
The Itunes library is located in
/home/rene/music/iTunes Library.xml

The music is in 
/home/rene/music/Itunes

---

### Post by MrFSL on 2008-09-30
In this blog it appears that the author is using acl's (Access Control Lists) 

In short - some file systems support there own permissions that are separate from the standard unix permissions you might be used to. These are manipulated with setfacl and viewed with getfacl.

EXT3 (the default file system for Ubuntu) can use acls but I do believe that you have to enable this at boot time.

Google yielded this link for more information: [http://www.vanemery.com/Linux/ACL/linux-acl.html](http://www.vanemery.com/Linux/ACL/linux-acl.html)

Now concerning your situation and setup... sorry don't use this technology so I don't think I can help. 

Best of luck.

---

### Post by knathraak on 2008-09-30
> **renewest said:**
> In his [blog entry]("http://shadow-file.blogspot.com/2008/09/itunes-and-squeezebox-integration.html") Zach Cutlip describes how to set various rights in order to use your Itunes library in Squeezecenter on Ubuntu.
Being new to Ubuntu I don't quite understand what is going on there and what to do in my specific situation. 

I keep my Itunes file on a Ubuntu server that has a Samba share (/home/rene/music) mapped to drive M: on my windows pc.
 
The Itunes library is located in
/home/rene/music/iTunes Library.xml

The music is in 
/home/rene/music/Itunes

Rene,

Can you  post the output of:
ls -lrd /home
ls -lrd /home/rene
ls -lrd /home/rene/music
ls -lr /home/rene/music/
ls -lr /home/rene/music/Itunes/

What I'm looking for is the perms on your Itunes library data base, the music, and on the path to those things.

We need to see if the squeezecenter use can traverse the path, and access those files.  I suspect not.  If that is the case, I can help you get those fix the problem without relaxing the perms too much.

Zach

---

### Post by knathraak on 2008-09-30
> **MrFSL said:**
> In this blog it appears that the author is using acl's (Access Control Lists) 

In short - some file systems support there own permissions that are separate from the standard unix permissions you might be used to. These are manipulated with setfacl and viewed with getfacl.

Yes, I used acls but that's partly because I like acls and every problem looks like an acl problem ;-) .  More seriously, it's because it allowed me the flexibility to give access to only the squeezecenter user without giving access to everyone else.  There are other ways though.  I don't recommend posix acls for just anyone.

Zach

---

### Post by renewest on 2008-09-30
Hi Here is my output:

rene@smallserver:~$ ls -lrd /home
drwxr-xr-x 3 root root 4096 2006-01-01 23:38 /home
rene@smallserver:~$ ls -lrd /home/rene
drwxr-xr-x 37 rene rene 4096 2008-09-29 17:21 /home/rene
rene@smallserver:~$ ls -lrd /home/rene/Music
drwxrwxrwx 5 rene rene 4096 2008-09-28 22:13 /home/rene/Music
rene@smallserver:~$ ls -lr /home/rene/Music
total 18696
drwxrwxrwx   2 nobody nogroup    4096 2008-09-26 17:59 iTunes Music
-rwxr--r--   1 nobody nogroup 9817655 2008-09-28 22:13 iTunes Library.xml
-rwxr--r--   1 nobody nogroup 9222403 2008-09-28 22:12 iTunes Library.itl
-rwxrw-rw-   1 nobody nogroup   28672 2008-09-26 15:11 iTunes Library Genius.itdb
-rwxrw-rw-   1 nobody nogroup   12288 2008-09-26 15:11 iTunes Library Extras.itdb
drwxrwxrwx 556 nobody nogroup   20480 2008-09-26 17:58 Itunes
drwxrwxrwx   4 nobody nogroup    4096 2008-09-26 17:59 Album Artwork
rene@smallserver:~$ ls -lr /home/rene/music/Itunes/
drwxrwxrwx  4 nobody nogroup 4096 2008-09-26 16:03 10CC

for all directories containing music. 

Rene

---

### Post by knathraak on 2008-09-30
> **renewest said:**
> 
drwxrwxrwx   2 nobody nogroup    4096 2008-09-26 17:59 iTunes Music
for all directories containing music. 
Rene

Hmm.. Actually your permissions are a bit too liberal, but that's not the problem here.  I'm not sure about this nobody/nogroup thing.  I wonder if that's samba-related?

How did you set up sharing?

Did you configure through the gui or by configuring smb.conf?

Can you attach your smb.conf, or possibly pm it to me?

Zach

---

### Post by renewest on 2008-09-30
Hi, I don't see anything in the samba config file related to this share. I set it up using the GUI.
Allow other people to write in this folder
Allow guest access.

I then access the folder as guest from my windows PC.

The rights have been set manually in a previous attempt to tackle this problem. The thought was grant everything if that doesn't solve the problem then it is not a rights problem.

Squeezecenter does actually create a song list by scanning the folders. It also plays these songs.
It also reads the Itunes library and shows the number of artists etc. At the end however, no song list after scanning.

---

### Post by knathraak on 2008-09-30
That explains the liberal perms on your iTunes.

I'm not quite sure I'm following what you're describing. with squeezecenter. 
> Squeezecenter does actually create a song list by scanning the folders. It also plays these songs.
It also reads the Itunes library and shows the number of artists etc. At the end however, no song list after scanning. Are you saying that when you have squeezecenter scan the files directly, it works, but when you tell it to use your iTunes database, that's when it doesn't show the songs?
I wonder if you could post (or pm to me) your squeezecenter logs.  they're in /var/log/squeezecenter.  You can tar them up with:
$ tar zcvf squeezecenter-logs.tar.gz /var/log/squeezecenter/
Also if you could post or pm your samba logs:
$ tar zcvf samba-logs.tar.gz /var/log/samba/  (<---you may need to use sudo to tar samba's logs)

Preferrably tar these up right after an unsuccessful iTunes scan in squeezecenter.

---

### Post by renewest on 2008-10-01
Yes, it is exactly as you say. Squeezecenter scans the music folders by itself resulting in a perfectly good list of music.. It's just when it uses the Itunes library that it does not work.

Scanner.log is 0 bytes , even with log settings on debug.

---

### Post by knathraak on 2008-10-01
> **renewest said:**
> 
Scanner.log is 0 bytes , even with log settings on debug.

No other log files in /var/log/squeezecenter/ ?  I have a server.log as well as a 0-byte perfmon.log.

What about in /var/log/samba?

What version of squeezecenter are you running?
Mine is: &#65279;SqueezeCenter Version: 7.2 - 22900
You can find out in the web interface under Settings->Satus

What user is squeezecenter running as?
$ ps-ef | grep squeezecenter

do you have a /etc/default/squeezecenter file?  What does it contain?

---

