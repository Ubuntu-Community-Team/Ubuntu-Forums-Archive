---
title: "Complete system freeze when mounting SMB share on a Time Capsule"
date: 2008-10-31
forum: General Help
---

### Post by haustier on 2008-10-31
Hi,

i have a complete system freezen (with blinking caps LED) on my Lenovo X300, 8.10 when mounting my the SMB share on my Time Capsule.

The share gets displayed for some seconds (i can access it), then the system is gone.

Regards, David

---

### Post by haustier on 2008-11-02
Sorry for bumpping, but this is very bad for me. I'd have to go back to vista if this will not work in Ubuntu. :(

---

### Post by harry.bush on 2008-11-02
i've got the exact same problem...complete freeze...must restart with the reset button.
i get the problem when browsing the files on the time capsule...i suspect i can browse the files that are stored in some cache but if i try going beyong, it freezes...

i have another problem which i believe might be related (see below)...do you have it also?

when shutting down, my computer hangs for ~10seconds on the following command
CIFS VFS: Server not responding

---

### Post by harry.bush on 2008-11-02
hi again,
i discovered a solution that fixes our little problem.
i'll write it up neatly for anyone else who might need it in the future

[SIZE="5"]HOWTO: Mount Time Capsule on Ubuntu[/SIZE]

1. Do not follow instructions found here: **[http://www.javaservercode.com/?p=43]("http://www.javaservercode.com/?p=43")**
If your TimeCapsule (TC) drive is mounted with cifs (or smbfs), you will get the problems described above (freeze/lock up/hanging at shutdown...)

2. The TC drive must be mounted using the AFP protocol. This can be done using afpfs-ng. You can download this app from **[here]("http://sourceforge.net/projects/afpfs-ng/")** and get some usage info from **[here]("http://alexthepuffin.googlepages.com/home")**.

3. If you get permission errors running
```
mount_afp afp://*username*:*passwd*@*TC-IP-address*/*sharename* */mount/point*
```
note that mount_afp is called with *your* own user's permissions and hence, 
[LIST]
it will not be able to mount the drive to a directory to which you don't have write access (e.g. /mnt/tc-drive)... so choose a mount point where your user can write (e.g. ~/tc-drive)
[/LIST]
[LIST]
it might not be able to read /etc/fuse.conf in which case, you'll need to run the following command (found **[here]("http://linux.dsplabs.com.au/forums/ubuntu-linux-help/ubuntu-fuse-failed-to-exec-fusermount-permission-denied-t70.html")**):
```
sudo chmod a+rwx /etc/fuse.conf
```
[/LIST]

[SIZE="4"]RECAP[/SIZE]
1. Install afpfs-ng
2. Edit /etc/fuse.conf and set permissions, user groups... appropriately
3. Add the appropriate line in /etc/fstab
4. Mount your drive via
```
sudo mount -a
```


All the problems described above should now be gone and your Time Capsule should work seamlessly in Ubuntu!!


This was my first post (second if you count the one above...) ever. I hope its not too disorganized to be useful!

---

### Post by nblender on 2008-12-10
That's not really a solution. First of all, afpfsd dies frequently. Second of all, it doesn't actually resolve the real problem which is an actual kernel panic on some CIFS access; not just with Time Capsule or Airport Extreme. It actually turns out to be a problem with some directory meta data.

I resolved this problem by discovering a whole lot of CIFS fixes on Dec. 3rd that seemed relevant.  I upgraded to 2.6.27.8 and the problem is now resolved against my Airport Extreme.  2.6.27.8 also fixed Alsa sound not working on my Mac Mini running 8.10.

---

### Post by alexthepuffin on 2008-12-30
I wrote afpfs-ng.  How does afpfsd die?


- Alex

---

### Post by nblender on 2009-01-05
SEGV after a short time.  I thought it was the binary package so I built it from source and got the same result.  I can try to get a stack trace for you when I'm back near the machine. It seemed to happen if the session idled.. ie: no data transferred for upwards of 20 minutes, afpfsd died.

---

### Post by zenobiaflex on 2009-03-02
Using Ubuntu 8.10

I want to try the AFP way of doing this as I will be accessing the files I want to transfer to the Time Capsule using my macbook.  The files will be coming from my Ubuntu Box. I have tried using CIFS, but I always get an error:

zenobiaflex@zenobiaflex-desktop:~$ sudo mount.cifs //192.168.0.195/"PocketUniverse"/STUFF /media/capsule -o pass=123456
[sudo] password for zenobiaflex:
mount error 13 = Permission denied
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)

This was following the most relevant steps I could find for mounting as a samba share. When I get home, I'd like to try the AFP route... but now I am wondering about the permissions and such... this is getting a bit confusing for me as I am not all that used to setting and dealing with permissions.  If I setup an account in Ubuntu that has the same username as the timecapsule folder and the same password... would this smooth out the process? I guess I am confused by the line in the thread that says "where the user does not have access"... which user?  The Time Capsule (as if it were a user) or the Ubuntu user...

---

