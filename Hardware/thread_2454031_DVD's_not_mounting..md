---
title: "DVD's not mounting."
date: 2020-11-21
forum: Hardware
---

### Post by dsenkbeil on 2020-11-21
[COLOR=#000000][SIZE=3]Nothing happens when inserting DVD. Most Google search results in posts from years ago.  Hoping for something new that I missed. I've been at it for a day and a half so I'm sure i missed something in my info below. Other dvd's have had the same results.[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]
[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]VLC Gives error's[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]
[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3][COLOR=#FF0000]Playback failure:[/COLOR][/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]DVDRead could not open the disc "/dev/sr0".[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3][COLOR=#FF0000]Your input can't be opened:[/COLOR][/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]VLC is unable to open the MRL 'dvd:///dev/sr0'. Check the log for details.[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]
[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]Checked "Disks", Drive shows but shows "No media"[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]Checked "File Manager" - DVD not present.[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]
[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]Installed codec's etc. [/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]ubuntu-restricted-extras is already the newest version (66).[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]
[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]gavin@gavin-20-b310:~$ sudo dpkg-reconfigure libdvd-pkg[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]libdvd-pkg: guest package [libdvdcss2/1.4.2-1~local] is already installed.[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]
[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]Terminal:[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]cd /dev[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]ls -lt | less[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]
[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]lrwxrwxrwx  1 root root           3 Nov 21 11:18 dvd -> sr0[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]lrwxrwxrwx  1 root root           3 Nov 21 11:18 dvdrw -> sr0[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]lrwxrwxrwx  1 root root           3 Nov 21 11:18 cdrom -> sr0[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]lrwxrwxrwx  1 root root           3 Nov 21 11:18 cdrw -> sr0[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]brw-rw----+ 1 root cdrom    11,   0 Nov 21 11:18 sr0[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]
[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]gavin@gavin-20-b310:~$ cd /media[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]gavin@gavin-20-b310:/media$ sudo mkdir mydvd[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3][sudo] password for gavin:          [/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]mkdir: cannot create directory ‘mydvd’: File exists[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]gavin@gavin-20-b310:/media$ sudo mount /dev/sr0 /media/mydvd[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]mount: /media/mydvd: no medium found on /dev/sr0.[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]gavin@gavin-20-b310:/media$ sudo mount /dev/sr0 /media/mydvd[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]mount: /media/mydvd: no medium found on /dev/sr0.[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]gavin@gavin-20-b310:/media$ cd[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]gavin@gavin-20-b310:~$ eject /dev/sr0 (WORKS)[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]
[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]lshw shows[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3] *-cdrom[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]             description: DVD-RAM writer[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]             product: DVDRAM GT80N[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]             vendor: hp[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]             physical id: 0.0.0[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]             bus info: scsi@1:0.0.0[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]             logical name: /dev/cdrom[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]             logical name: /dev/cdrw[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]             logical name: /dev/dvd[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]             logical name: /dev/dvdrw[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]             logical name: /dev/sr0[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]             version: RA04[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]             configuration: ansiversion=5 status=nodisc[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]
[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]gavin@gavin-20-b310:~$ ls -l /dev/sr0[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]brw-rw----+ 1 root cdrom 11, 0 Nov 21 11:39 /dev/sr0[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]
[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]
[/SIZE][/COLOR]
[COLOR=#000000]
[/COLOR]

---

### Post by CelticWarrior on 2020-11-21
Welcome.

If you google "DVDRAM GT80N" you'll find lots of similar situations and unrelated to the OS.
Very likely hardware failure.

---

