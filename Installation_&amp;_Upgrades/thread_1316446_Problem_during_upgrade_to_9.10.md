---
title: "Problem during upgrade to 9.10"
date: 2009-11-06
forum: Installation &amp; Upgrades
---

### Post by ihuntert on 2009-11-06
Before I post my question I want to say 2 things.
1) I dual boot with vista on my laptop, I like to play games online with friends.  And is the only reason I can access the internet right now.  I have ubuntu as my main os though.
and
2) During the upgrade the lid of my laptop was closed, thus interrupting the install.

So when I start my computer up I get the nice ubuntu loading screen, then

> 
One or more of the mounts listed in /etc/fstab cannot yet be mounted:
(ESC for recovery shell)
/: waiting for /dev/disk/by-uuid/lb18d72f-b5ce-45a2-a65e-38ea13b2057c
/tmp: waiting for (null)
swap: waiting for UUID=8dff2ab1-3c69-412e-873c-fa7954ffbed9I then press  [ESC], and then [ENTER], thus getting

> 
^[

mountall: Cancelled
init: mountall main process (825) terminated with Status 1
General error mounting filesystems
A maintenance shell will now be started.
CONTROL-D will terminate this shell and re-try.
root@ian-laptop:I waited for ten minutes (I am a little lost when it comes to computer programing, I do hope to learn how some day as I enjoy programing my calculator.  I do realize they are different beasts), and then pressed [CTRL]-[D] and it displayed

> 
root@ian-laptop: ~#exit
mountall start/starting
One or more of the mounts listed in /etc/fstab cannot yet be mounted:
(ESC for recovery shell)
/: waiting for /dev/disk/by-uuid/lb18d72f-b5ce-45a2-a65e-38ea13b2057c
/tmp: waiting for (null)
swap: waiting for UUID=8dff2ab1-3c69-412e-873c-fa7954ffbed9If you want to see what it all looks like together it is.

> 
One or more of the mounts listed in /etc/fstab cannot yet be mounted:
(ESC for recovery shell)
/: waiting for /dev/disk/by-uuid/lb18d72f-b5ce-45a2-a65e-38ea13b2057c
/tmp: waiting for (null)
swap: waiting for UUID=8dff2ab1-3c69-412e-873c-fa7954ffbed9
^[

mountall: Cancelled
init: mountall main process (825) terminated with Status 1
General error mounting filesystems
A maintenance shell will now be started.
CONTROL-D will terminate this shell and re-try.
root@ian-laptop: ~#exit
mountall start/starting
One or more of the mounts listed in /etc/fstab cannot yet be mounted:
 (ESC for recovery shell)
 /: waiting for /dev/disk/by-uuid/lb18d72f-b5ce-45a2-a65e-38ea13b2057c
 /tmp: waiting for (null)
 swap: waiting for UUID=8dff2ab1-3c69-412e-873c-fa7954ffbed9Now I'm 97% sure I have all the spacing and numbers and letters right, but some of the l's could be 1's and 1's could be l's, as I wrote this down on paper and my 1's and l's look the same.

I have tried Recovery mode for each item in grub I have, I just get text and the last five lines are always

> One or more of the mounts listed in /etc/fstab cannot yet be mounted:
  (ESC for recovery shell)
  /: waiting for /dev/disk/by-uuid/lb18d72f-b5ce-45a2-a65e-38ea13b2057c
  /tmp: waiting for (null)
  swap: waiting for UUID=8dff2ab1-3c69-412e-873c-fa7954ffbed9Please help me, I really like ubuntu and I would rather not have to buy a blank CD/DVD to re-install ubuntu.

---

### Post by chicoharv on 2009-11-06
I also have a problem but mine is I have to do a hard boot to close down or restart 9.10. My suggestion is that you uninstall from windows control panel and reinstall 9.04 until they get all the bugs out of the 9.10 upgrade. Also go to the Ubuntu site and ordwer a free cd . They will ship it free whrn available. My understanding is 9.10 only has these problems when installed by the upgrade method rather than a cd install. You miht try to repair thru the Vista control panel but not sure if this will work before you uninstall the ubuntu inside windows.

---

### Post by running_rabbit07 on 2009-11-06
Using your Windows, download and burn the Ubuntu 9.10 Alternate installer disk. Restart and select restore broken system. If that does not work, you will most likely have to reinstall. 

If you have data that you fear you may lose during this process, use a LiveCD to boot and copy needed data to a thumb drive. 

If you have the /home partiton set up, you shouldn't have much to worry about with reinstalling. 

If not, make that extra partition next time you are installing, it is a life saver.

Best of wishes. Let us know how it goes.

---

### Post by running_rabbit07 on 2009-11-06
> **chicoharv said:**
> I also have a problem but mine is I have to do a hard boot to close down or restart 9.10. My suggestion is that you uninstall from windows control panel and reinstall 9.04 until they get all the bugs out of the 9.10 upgrade. Also go to the Ubuntu site and ordwer a free cd . They will ship it free whrn available. My understanding is 9.10 only has these problems when installed by the upgrade method rather than a cd install. You miht try to repair thru the Vista control panel but not sure if this will work before you uninstall the ubuntu inside windows.

That may work if you are using Wubi, in that situation, I don't know much about it. I installed Wubi and a day later I installed the full version.

---

### Post by gmp34 on 2009-11-08
Fixed it on my side, it may work for you, here is the full story.

I hade the same problem, SWAP space not mouting at boot time, although no problems encountered during upgrade process.

My drive has 3 logical volume in the following order: Windows, Swap Linux, Linux.
Swap not mounting I obviously could not see it in the system monitoring, tab file system, either.
I discovered a nice feature un Administrator menu which is called "Disk tools (well it's in French for me :)).
Using this tool I saw that my Swap space was seen as "sub logical" drive of a "Win95" logical drive.
I decided to delete this partition "Win 95" and the supposed swap space going along with it.
Then started Gparted (disk graphic partition editor) to recreate the swap space at exactly the same location on the drive (the one left free by my deletion). Operation being complete, looking at this brand new swap partition the right click properties gives you the UUID
[IMG]/home/giebsay/Bureau/Gpatred_1.png[/IMG]
[IMG]/home/giebsay/Bureau/Capture-Informations à propos de -dev-sda2.png[/IMG]

The a quick edit of fstab replacing the existing UUID for the swap space by the one given by Gparted. Be carefull enough to check the number of digits and just comment out the previous fstab command line so that you don't have to worry about the syntax.
```
sudo gedit /etc/fstab
```

example of my fstab after modification:
```

# /dev/sda2
# UUID=083a555f-2a50-4e92-9df7-ac1559b754e7 none            swap    sw              0       0
UUID=0dd0ce0e-a80c-49f0-a2f7-0d9f84e65524 none            swap    sw              0       0

```

Have a try and good luck !

---

