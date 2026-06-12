---
title: "[SOLVED] Ubuntu suddenly became slow and some other wired things happend"
date: 2008-09-13
forum: General Help
---

### Post by JanBart on 2008-09-13
Ubuntu became suddenly (well there will be obviously a reason, but i don't know it) verry slow. 
Also my bookmarks (in firefox) are gone and even songbird don't recognise his own library (and thus fails to start => crashes when i try)
When i try delete installed programs  (via install/delete software, standard in ubuntu) I can't because there's "something wrong with the mmap"

What's the problem and what should i do to solve it?

I'm running:
Ubuntu 8.04
Firefox 3.0.1
Songbird (well, I can't see it anymore, but I think it was the most recent songbird)

P.S.: I'm sorry for my bad English.. it isn't my standard language...

---

### Post by SunnyRabbiera on 2008-09-13
what are your computers specs?

---

### Post by JanBart on 2008-09-13
Dell inspiron 6400 T2400 (Dualcore)
(1.83 GHz, 2MB L2 cache, 667 MHz FSB)
Kernel Linux 2.6.24-19-generic
GNOME 2.22.3
Memory: 1009,9 MiB

Is there something more you need to know?

---

### Post by shineymcshine on 2008-09-13
My recent Ubuntu install has also become ridiculously slow all of a sudden. I launched firestarter over an hour ago and the window just pooped up now! 

Do any apps other than songbird fail to launch? Try launching from console and posting the output. Running things from console can often shed more light on the problem...

---

### Post by JanBart on 2008-09-13
Ok, i did, but i think they don't give the correct error...

----- Firefox -----

[I]jan-bart@JB-laptop:~$ firefox

(firefox:9237): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)[/I]



I get this warning, but finaly, firefox launched (much later and without bookmarks)



----- Songbird -----
[I]jan-bart@JB-laptop:~$ /opt/Songbird/songbird

(songbird:9331): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
No space left on device

(crashreporter:9459): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
jan-bart@JB-laptop:~$ 
** (crashreporter:9459): WARNING **: Invalid borders specified for theme pixmap:
        /home/jan-bart/.themes/Mac4Lin_GTK_v0.4/gtk-2.0/Buttons/button-default.png,
borders don't fit within the image[/I]

Than i get a pop-up window that says:

[I]"Songbird is unable to start.

Songbird has detected that your Library is corrupt and cannot be read.

In order for Songbird to function correctly, your library needs to be deleted. This action cannot be undone. You will lose subscriptions, playlists and track metadata edited in Songbird.

Your media files are safe and will not be deleted, but you'll need to rescan them.

      [Delete Library and Restart]  [Continue Anyway]"[/I]

Than, whatever option I choose:

[I]"The application had problem and crashed.

Unfortunately the crash reporter is unable to submit a report for this crash.

Details: The application did not identify itself.

                                   [close]"[/I]
---------------

All other applications seem to work (but slow). 
Only with Kmess I had this error:

[I]"There was an error setting up inter-process communications for KDE.
The message returned by the system was:

Could not read network connection list.
/home/jan-bart/.DCOPserver_JB-laptop_0

Please check that the "dcopserver" program is running!

   [ok]"[/I]


But after clicking on the "ok" button everything seems to work as it should.

---

### Post by JanBart on 2008-09-13
Well, I used the "Disk Usage Analyzer" and saw that my home map was used for 100%...
Maybe that's the reason of the error's?:confused:

---

### Post by JanBart on 2008-09-13
Hmmzzz... i've deleted some (big) files, but he's still saying 100%...
Even after a couple of reboots... 
I don't get it...

---

### Post by nikgare on 2008-09-13
You need to empty the trash can!

WHat's the output of this:

df -h

---

### Post by JanBart on 2008-09-13
No, i don't think it has anything to do with my trashcan.
But meanwhile my dad found the problem (and the solution) I think.

My backup program i was using, tooks his backups on /media/disk.
This is supposed to be a external device, but that device was mounted on /media/disk-1 (I don't know why actually).
So because of /media is a directory under / .. all my back-ups were stored under / .
(wich was obviously not supposed to happen)
I will now delete all the files (over 70GB) and let you know if it worked.

---

### Post by JanBart on 2008-09-13
Ok, so here it was:

an-bart@JB-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              78G   77G   67G  100% /
varrun                505M  156K  505M   1% /var/run
varlock               505M     0  505M   0% /var/lock
udev                  505M   80K  505M   1% /dev
devshm                505M   12K  505M   1% /dev/shm
lrm                   505M   39M  467M   8% /lib/modules/2.6.24-19-generic/volatile
overflow              1,0M   40K  984K   4% /tmp
gvfs-fuse-daemon       78G  7,4G   67G  10% /home/jan-bart/.gvfs
/dev/sdb1             147G  766M  147G   1% /media/disk-1
/dev/sdb2              48G   20G   28G  42% /media/Backup 1


and now it is:
an-bart@JB-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              78G  7,4G   67G  10% /
varrun                505M  156K  505M   1% /var/run
varlock               505M     0  505M   0% /var/lock
udev                  505M   80K  505M   1% /dev
devshm                505M   12K  505M   1% /dev/shm
lrm                   505M   39M  467M   8% /lib/modules/2.6.24-19-generic/volatile
overflow              1,0M   40K  984K   4% /tmp
gvfs-fuse-daemon       78G  7,4G   67G  10% /home/jan-bart/.gvfs
/dev/sdb1             147G  766M  147G   1% /media/disk-1
/dev/sdb2              48G   20G   28G  42% /media/Backup 1

Well, i rebooted and everything works faster, but i'm still unable to start firefox with bookmarks or songbird (at all)...

---

### Post by JanBart on 2008-09-13
It isn't the perfect solution but it worked for me.
I deleted the .songbird and the .firefox map in de home-directory (they are hidden files). Luckily enough i use foxmarks, so none of my bookmarks were lost. It was a pitty tough that my whole music-library had to be scanned again...

but after all.. they do work now! :popcorn:

---

### Post by Amadu on 2009-04-14
chown <user>:<user> /home/<user>/.songbird
chown <user>:<user> /home/<user>/.mozilla
;)

---

