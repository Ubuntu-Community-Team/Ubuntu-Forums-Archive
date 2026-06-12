---
title: "Possible Way To Sync Ipod Touch Via USB!!"
date: 2008-10-20
forum: Hardware
---

### Post by The Creator on 2008-10-20
I think i found the way to sync the ipod touch via usb on ubuntu without wireless, wine, or vmware or anything that emulates another os though wine is technically an "Application layer." I was hunting for this because i have grown sick of the 5 hour waits to get my ipod synced via wireless. The project's name is [iFuse]("http://matt.colyer.name/projects/iphone-linux/index.php?title=Main_Page") and claims to have figured out this mysterious encryption issue. 

>  iFuse and libiphone

iFuse allows you to mount an iPhone or iPod Touch under Linux using the USB cable. You can view and edit the files similar to a normal USB disk drive. iFuse does not require "jailbreaking" or voiding your warranty and works without needing extra software installed on the phone (such as `ssh`).
What is it?

libiphone is a software library that talks the native Apple USB protocols that the iPhone uses. Unlike other projects, `libiphone` does not depends on using any existing `.dll` or `.so` libraries from Apple.

iFuse is a FUSE filesystem driver which uses `libiphone` to connect to devices without jailbreak. iFuse is using the native Apple "AFC" protocol, over the normal USB cable in order to access the iPhone's (or iPod Touch's) media files under Linux.
Does it work yet?

Yes! As of 2008-09-02, iFuse is currently able to read and write files and directories and will quite happily copy 10GB+ of files without problems, allowing you to do a backup under Linux. However at this point it is recommended only for use by developers ...to ensure that there are no unexpected issues.
What can it do?

Once the iPhone is mounted, you can copy on, or copy off any media files that live inside the `/var/root/Media` chroot directory. This includes photographs and music files.

Photos: These are EXIF/JPEGs stored in the DCIM hierarchy. With iFuse you can use the `.jpg` files directly, or the use the existing USB 'PTP' camera interface.

MP3 player: the iPhone uses a proprietary database format to store song information and playlists, simply copying extra music to the iPhone's filesystem without updating this database will not work. `libgpod (svn)` and `gtkpod` can be used to update and re-sign the song database and make new music show up on players using firmware versions up to 1.3.

    * Note for libgpod users: Apple's cryptographic signing algorithm changed with the new 2.0+ firmware. The new algorithm has not been discovered yet and `libgpod` will be unable to re-sign the database. If you try to update the song database on 2.0 devices, your music library will be destroyed and require restoring through iTunes. This problem is not with iFuse and applies equally to all the `ssh`-based mounting methods. To assist, you can help reverse-engineer the new signing algorithm with the GtkPod team. 

Addressbook/Calendar: these databases live outside of the chroot. You can currently only access/update the files directly on phones that have been jailbroken. There is an experimental module for Conduit Syncing from a jailbroken phone.

Work is in progress to reverse-engineer more the backup/sync protocols and to make Addressbook access possible using the "proper" protocols.
Known bugs

As of 2008-09-02, there are still some threading/locking issues. A workaround is to use `ifuse <mountpoint> -s` which will force single-threaded mode until the issue can be finally tracked down. 

Could someone compile this and check if it does work. I am not skilled enough to do so. This would be a huge help to all iphone and ipod touch users. If this does work I don't know what would be stopping gtkpod or amorok from syncing with the ipod touch and iphone for they can do it when it is mounted via ssh so that part must already be worked out. 

I believe this may be the key to finally getting usb syncing of the iphone and ipod touch in ubuntu.

---

### Post by jpeddicord on 2008-10-29
Moved to Hardware & Laptops; is a question not a tutorial.

---

### Post by teolemon on 2009-04-07
[https://bugs.edge.launchpad.net/ubuntu/+bug/296351](https://bugs.edge.launchpad.net/ubuntu/+bug/296351)
There's a link to the packages.

---

### Post by Blue Wolf on 2009-05-21
I just followed the link to the iFuse website and added the repo and install it using terminal.  Now when I connect my iPhone 3G it mounts as a disk drive and camera.  I can now access the iPhone's filing system.

Good find :p

---

### Post by Josh61980 on 2009-05-21
Hello,
I have an iPone 3G.  I tried to use ifuse it did mount the partition as belonging to root. So it did not allow me to edit anything on my iPhone. I was wondering if you did anything else to get it to work. I figure the touch and iPhone are similar enough I may be able to use your advice , thank you.

---

### Post by barkadoodle on 2009-07-07
Using iFuse I was also able to mount my touch to ubuntu.  I can now view and listen to all my music on my iPod with Rhythmbox.  With GtkPod, I can also see my songs on my iPod, and I tried to copy music to it, which sorta worked halfway.  GtkPod was able to copy the songs to my iPod, but it didn't seem to update the music database, so they don't show up in my iPod interface, but Rhythmbox sees them and plays them.  I can also see them through the file system.

Does someone have an idea of how to refresh the music database so I can actually see the songs in the iPod software?

---

### Post by emshains on 2009-07-07
I use itunnel with the iphoneOS 3.0. It is faster, I think. But there is no support for the native media player, so I have to use an alternative in stead, which sucks.

---

### Post by hermibo on 2009-07-08
> **barkadoodle said:**
> Using iFuse I was also able to mount my touch to ubuntu.  I can now view and listen to all my music on my iPod with Rhythmbox.  With GtkPod, I can also see my songs on my iPod, and I tried to copy music to it, which sorta worked halfway.  GtkPod was able to copy the songs to my iPod, but it didn't seem to update the music database, so they don't show up in my iPod interface, but Rhythmbox sees them and plays them.  I can also see them through the file system.

Does someone have an idea of how to refresh the music database so I can actually see the songs in the iPod software?


Hi, if try it on the same way but till now i cant refresh the data base.
i can play the songs on rhythmbox, but ipod dont show them. to load all songs i change to win vista.
but thats not the way i want.
i think we have to wait if this problem will be fixed in future!

hermibo

---

### Post by The Creator on 2009-08-26
Sorry I have been away from this so long. If we can edit the files on the iphone via usb and we can update the database via wifi we are there. We just need to put the two systems together... Is there anyone that can do this? It would make a bunch of iphone users so much more happy. I will attempt with ipod convenience and this and see if i can find a way to do it with both packages. I will report back. I suspect it would be as simple as setting up a local alias for that folder....

---

### Post by realn on 2009-11-02
I also tried iFuse and iTUnnel.
ifuse is a mistery to me. I installed it through Synaptic, then I compiled it. 
 I couldn't find the mount.fuse.ifuse and libiphone-initconf executables. The project page doesn't have tutorial, it's a mes- this doesn't mean that I don't see any potential in it, it seems like a good app.

 iTunnel - it's straightforward, i was hooked to my iPhone in 60 seconds. The only problem - the speed is around 300KBPS. 
 
 Anyway, I am impressed with the fact that such apps are out, and that - again - you can do more on Linux because of some nice guys.

 PS I've been able to sync wirelessly my iPodTouch for a long time now, but I was hoping that through the cable I would get greater speed. That's why I am a little dissapointed.

---

### Post by EtienneMarc on 2009-11-10
> **barkadoodle said:**
> Using iFuse I was also able to mount my touch to ubuntu.  I can now view and listen to all my music on my iPod with Rhythmbox.  With GtkPod, I can also see my songs on my iPod, and I tried to copy music to it, which sorta worked halfway.  GtkPod was able to copy the songs to my iPod, but it didn't seem to update the music database, so they don't show up in my iPod interface, but Rhythmbox sees them and plays them.  I can also see them through the file system.

Does someone have an idea of how to refresh the music database so I can actually see the songs in the iPod software?

I've exactly the same problem.
The transfer seems to be ok, but nothing updated on the Ipod side.

I saw that a new directory has been created ("iPod_Controls" instead of "iTune_Controls" according my memory).

Thanks for your help.
EtienneM

---

### Post by realn on 2009-11-10
I managed to get itunnel and also usbmuxd+iproxy+ifuse working.
Here are the speeds I got:
1) itunnel - 400-500 KBps in write mode and more or less the double in read mode

2) iproxy + ifuse - 800-900 KBps in write mode

3) iproxy + sshfs - 1.1-1.2 MBps in write mode

 I think I'll stick to the third option, still I was expecting a greater speed through wired connection.

 PS I am using the following line in /etc/fstab in order to mount through sshfs (after the usbmuxd launches itself and after I manually launch the iproxy tool: "iproxy 3333 22")
sshfs#root@localhost:/var/mobile/Media /home/my_user/ipod fuse user,port=3333,uid=1003,gid=1003,umask=000,allow_other 0 0

I am using gtkpod on Kubuntu KK to synchronize the iPod, it works perfectly with music&photo synchronization.

---

### Post by funfrank on 2010-01-12
hey realn and others,

how did you get gtkpod to sync with your touch after connecting with itunnel?  

I manage to connect with itunnel no problem.  I use 2.x and managed to change the hash and correct the fireguid.  gtkpod apparently has no problem with my touch.  

But when I place songs in my gtkpod repository.... there's no sync with the touch.  

any idea?

funfrank

---

### Post by realn on 2010-02-16
Hi, sorry for the late reply.

Here are the steps to connect to the iPod touch

1) launch iTunnel

itunnel 8888

where 8888 is the port no. used for ssh-ing the iPod

2) manually mount the iPod 

I have this line in the /etc/fstab (attention, it's only ONE line)

sshfs#root@localhost:/var/mobile/Media /home/myuser/ipod fuse user,port=8888,uid=xxxx,gid=xxxx,umask=000,allow_other 0 0

please replace the xxxx with your uid and gid numbers
You have to have sshfs installed in order to be able to use it
There are some packages, I think they are called ipod-convenience, or smth, like this, which does the same thing, basically.

3) you can now see if the ipod touch is mounted correctly

my_favourite_file_browser /home/myuser/ipod

if you can see the file system of the iPod, everything should be fine

4) As for sync-ing with gtkpod, this should be the least of the problem

- create a new iPod
- create new playlists (it seems you can do it only by clicking the button "new playlist", there's no menu item for it)
- populate playlist by drag&drop files to the play list window (on the right)
- click on "save changes"
- you should be able to see and play the music (maybe a iPod restart is needed, just in case)

Here is my iPod properties, just for your info (i get these by right clicking the iPod and then "edit ipod properties")
- iPod mountpoint : /home/myuser/ipod
- iTunesDB backup : /home/myuser/.gtkpod/backupDB_2
- model           : xA627

I hope it helps, please make sure you have the iPod mounted correctly, then everything else should follow smoothly.

---

### Post by realn on 2010-04-22
Tried also ifuse - write speed ~ 700 KBps; read speed ~ 2MBps;
Tried also WiFi connection using sshfs - write speed ~ 900 KBps; read speed ~ 900 KBps.

Conclusion - iFuse for read, sshfs over wifi for write.

---

