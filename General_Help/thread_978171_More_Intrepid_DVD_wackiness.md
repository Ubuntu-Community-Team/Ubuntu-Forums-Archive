---
title: "More Intrepid DVD wackiness"
date: 2008-11-10
forum: General Help
---

### Post by punchdrunkgrunt on 2008-11-10
So, after upgrading to Kubuntu 8.10 I discovered I couldn't mount DVDs anymore. With a little help from this board I tweaked /etc/fstab, changing this:

/dev/hda /media/cdrom0 auto user,utf8,atime,noauto,rw,dev,exec,suid 0 0

to this:

/dev/scd0 /media/cdrom0 auto user,utf8,atime,noauto,rw,dev,exec,suid 0 0

and now dvds show up and mount when I click on them........at least, the DVDs that **I've** made. Commercial DVDs not only can't be mounted, they don't even show up in the drive. If I try to mount in Konsole it just says "no medium found."

FYI here's the output of lshw -C disk

*-disk                                 
       description: ATA Disk             
       product: SAMSUNG HM120JI          
       physical id: 0.0.0                
       bus info: scsi@0:0.0.0            
       logical name: /dev/sda            
       version: YF10
       serial: S0YPJ10P654738
       size: 111GiB (120GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=e686f016
  *-cdrom
       description: DVD writer
       product: DVD+-RW TS-L632D
       vendor: TSSTcorp
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/cdrw1
       logical name: /dev/dvd1
       logical name: /dev/dvdrw1
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: DE04
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 status=nodisc

That's with a commercial DVD in the drive.

Of course, even with DVD movies I've burned I still can't watch them. The sound is intermittent with VLC and Kaffeine keeps telling me to install libdvdcss even though it's already installed. I've added the Medibuntu repos and grabbed every damn codec I could find, but no joy. BTW everything was fine with 8.04.

If anyone knows what's going on I'd be grateful to hear about it.

TIA

---

### Post by mc4man on 2008-11-10
did you upgrade 8.04 or do a fresh install, the hda thing suggests an upgrade

Edit; just tried kaffeine which does work as long as the dvd device in it's xine engine settings matches your drive. In your case that's /dev/dvd1 (the default in xine ... is /dev/dvd
The libdvdcss warning is a generic 'somethings wrong' message which shows up if -
1. no libdvdcss2 is installed
2. no libxine1-ffmpeg is installed
3. wrong dvd device setting

You probably have your dvd drive listed twice in /etc/udev/rules.d/70-persistent-cd.rules
you can leave it as is or open the file in a text editor as root, remove the entries and reboot which should give you /dev/dvd, /dev/cdrom, ect. on that drive
If you decide to edit, remove everything under this line

# add the ENV{GENERATED}=1 flag to your own rules as well.

Note; if your drive is only listed once feel free to remove the 1 from each /dev/* (ex. change SYMLINK+="dvd1", to SYMLINK+="dvd", 

If you leave as is then adjust settings in apps as needed.(/dev/dvd and /dev/cdrom are the 2 most commonly used defaults - your /dev/dvd1 and /dev/cdrom1

As far as com. dvds, who knows, you can't play something that's not found.
 
Do note that removable media doesn't automount and remains 'unmounted' even after playing.
For instance insert a dvd, play with kaffeine and ck. in /media/cdrom - nothing.
Only after opening with dolphin does it show up.

So without 'mounting' the most you'll see in lshw with media inserted is 'ready', no mount, filesystem info as normally seen.

I think kubuntu 8.10 is as 'flaky' a release as I've ever seen, if you did do an upgrade as it appears, I'd consider a fresh install if things don't clear up.

---

