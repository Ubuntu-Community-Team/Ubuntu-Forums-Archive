---
title: "Audio CD trouble"
date: 2008-09-02
forum: General Help
---

### Post by moyam01 on 2008-09-02
I posted this in the Multimedia forum a couple of days ago and no one could help me, maybe you guys can be of more help.


Whenever I insert an 'Audio CD' I can see rhythm box quickly flash before me then immediately close. When I try to open the cd, it will let me, but then say that it either cannot find the file, or that the cd is not there depending on the program. I try to ls the drive from the command line, but it will not list any files. If you guys could help me that would be great. It will read other cd's just fine.

Here is my output for cat /etc/fstab:

/etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sdb2
UUID=45c4b8c5-2e2a-4ce3-9201-5cbb15606acb / ext3 relatime,errors=remount-ro 0 1
# /dev/sdb3
UUID=bae0a309-f502-4f97-a5ba-c6415da72ad2 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
## usbfs is the USB group in fstab file:
none /proc/bus/usb usbfs devgid=124,devmode=664 0 0

---

### Post by moyam01 on 2008-09-02
UPDATE: I can see the CD mounting, but when I click on the audio track VLC gives me the following error:

"Unable to open 'cdda://scd0/Track%201.wav'"

Sound Juicer gives me the following error

"Sound Juicer could not find any CD-ROM drives to read"

Someone please help me

---

### Post by moyam01 on 2008-09-03
anyone?

---

### Post by mc4man on 2008-09-03
> but when I click on the audio track

Can you explain that a little better - are you browsing the cd and d. left clicking or r. click - open with ?

Note - opening .wavs directly from the cd **can** be a bit of a problem due to the location - .gvfs cdda mount on scdx

what happens if you open vlc -> file -> open disk -> check audio cd -> ok ?

---

### Post by moyam01 on 2008-09-04
Sorry I was not clearer. I get the error message when I am browsing the cd (I click on the icon on the desktop after it mounts, and click the audio tracks).

I tried what you suggested in VLC, and it played just fine. Thanks a lot. I Also tried to right click open with, and sound juicer works as well. However when I try to open with rhythm box, I still se a brief flash and then it just crashes.

Why is it problematic (is it the mount point)? I am afraid I did not understnad the that part of your post "- .gvfs cdda mount on scdx" 

Thanks again. If there is a way to fix it so it works when I browse the cd, please let me now, but now at least I can start ripping my old cd's.

---

### Post by mc4man on 2008-09-04
> I am afraid I did not understnad the that part of your post "- .gvfs cdda mount on scdx"
Put an audio cd in and then go home folder -> .gvfs (a hidden dir., use Ctrl+h or view -> 'show hidden files'
Inside of there you will see 'cdda mount on scd[COLOR="Red"]x[/COLOR]', that's the location of the .wavs

Some apps cannot access 'directly' from that location, some can. (same as browsing desktop icon

rhythmbox should be able to
Try setting rhythmbox as default audio cd player and then try again, first by inserting an audio cd and seeing if rhythmbox autostarts and then try direct access

Note: there is no advantage to direct access with rhythmbox in terms of loading an individual track - if you try to load one it will still load the complete cd, above is more a test of rhythmbox than anything useful.

(you can switch back to soundjuicer as default if wanted afterwards

Another way to access default choices (vs. setting in file management -> media or nautilus -> edit -> preferences -> media) is when inserting your media hold down the shift button. you'll get a popup asking what to do and listing choices, whatever you choose becomes the new default setting

The gist of it is that your better off either setting a player to autostart (or in case of Amarok, autoplay) audio cd's or accessing the cd from **within** the players gui

---

### Post by moyam01 on 2008-09-07
I made rhythm box the default for opening up cd's. Now none of the programs can see the cd (sound juicer or rhythmbox), and it dosen,t matter if I right click or straight to the program, and the .gvfs folder is empty

EDIT:

Got it working again, but I set rhythm box to the default application for CD's and all it does is it briefly flashes before crashing. Also Right click -> Copy CD does not work, and it doesn't work through Brasero directly. If I can get the cd copying function working that would be great.

Thanks Again,
moyam01

---

