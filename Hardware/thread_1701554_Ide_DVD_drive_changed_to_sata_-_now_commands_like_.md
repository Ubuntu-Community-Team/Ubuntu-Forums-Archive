---
title: "Ide DVD drive changed to sata - now commands like eject do not work"
date: 2011-03-06
forum: Hardware
---

### Post by diddy1234 on 2011-03-06
Changed cdrom from ide to sata - now eject does not work
I was wondering how to fix the following problem.

My ide DVD drive stopped working so today I changed it to an sata dvd writer drive.

Only it is seen as /dev/sr0 or /dev/cdrom2

I now have the problem that commands like 'eject' and vobcopy no longer work.

If I type 'eject /dev/sr0' I get the drive to eject

But if I use vobcopy, even with the -i /dev/sr0 this does not work.

This is one thing about Linux (in general) that winds me up if hardware is changed.

Originally I could not even mount the drive as it did not exist in the fstab, so I added :-

#cdrom
/dev/cdrom2 /mnt/cdrom auto noauto,rw,users 0 0

This seems to work but is that correct ?

So how do I get the new DVD writer drive to work like the original DVD drive ?

Thanks in advance.

---

### Post by Hedgehog1 on 2011-03-06
diddy1234,

Another post asked about eject on SATA CD/DVD/BluRay last week.

I fooled around with mine (it was also not ejecting) and compared IDE vs SATA behavior in a Virtual Box version of Ubuntu.

I think I have it working.  If you would please repeat these same steps on your PC, we can  verify it:

SATA drives seem to work best if mounted in the '/media' directory.

1st step: Create a cdrom0 directory in the /media directory:

```
sudo mkdir /media/cdrom0
```

Next, edit the fstab file:

```
gksudo gedit /etc/fstab
```

Add the two lines in red (replacing any not-working CD mount commands):

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc   proc  nodev,noexec,nosuid  0  0  
# / was on /dev/sda5 during installation
UUID=f2fd03c5-2835-415c-8448-75473daf624a  /       ext4  errors=remount-ro    0  1  
# swap was on /dev/sda6 during installation
UUID=cb0c7226-150e-45ca-ba5c-2e161dc10f6a  none    swap  sw                   0  0  
[B][COLOR="Red"]# CD/DVD/BluRay
/dev/sr0                          /media/cdrom0  udf,iso9660 user,noauto,exec 0  0[/COLOR][/B]
```

Then please reboot and test the eject and mounting behavior as CDs are inserted.

***The Hedge***

:KS

p.s. using **auto** instead of **udf,iso9660** also seems to function
```
[B][COLOR="Red"]# CD/DVD/BluRay
/dev/sr0    /media/cdrom0  _auto_  user,noauto,exec  0  0[/COLOR][/B]
```

---

### Post by Hedgehog1 on 2011-03-06
Based on my testing, the above post seems to solve everything but:

*'When manually ejecting a SATA CD/DVD using the button on the drive, the CD/DVD ejects, but CD/DVD drive does not unmount like an IDE drive does'.*

***The Hedge***

---

### Post by diddy1234 on 2011-03-07
thanks for the replies

I tried your work around and had a bit of success.
However, when i try to use vobcopy I get :-


[Info] Device /media/cdrom0 mount on /dev/sr0

[Info] Path to dvd: /dev/sr0
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Could not open /dev/sr0 with libdvdcss.
libdvdread: Can't open /dev/sr0 for reading

[Error] Path thingy didn't work '/dev/sr0'
[Error] Try something like -i /cdrom, /dvd  or /mnt/dvd


Any ideas ?

---

### Post by Hedgehog1 on 2011-03-07
> **diddy1234 said:**
> thanks for the replies
 
I tried your work around and had a bit of success.
However, when i try to use vobcopy I get :-
 
 
[Info] Device /media/cdrom0 mount on /dev/sr0
 
[Info] Path to dvd: /dev/sr0
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Could not open /dev/sr0 with libdvdcss.
libdvdread: Can't open /dev/sr0 for reading
 
[Error] Path thingy didn't work '/dev/sr0'
[Error] Try something like -i /cdrom, /dvd or /mnt/dvd
 
 
Any ideas ?
 
Well, some success is better then none, I guess.
 
What is the -i option you used? I would think **-i /cdrom0/vobs **would be the correct choice. Did you use **auto** or **udf,iso9660** in your fstab file?
 
I wonder if the name has to be cdrom (instead of cdrom0) to make libdvdcss happy?
 
hmmm...
 
***The Hedge***
 
:KS
 
For Reference - I have not used vobcopy before:
```

 
**vobcopy** without any options will copy the title with the most chapters into files of 2GB size into the current working directory. **Options**
 
 -b, --begin SIZE[bkmg] begins to copy from the specified offset-size. Modifiers like b for 512-bytes, k for kilo-bytes, m for mega- and g for giga-bytes can be appended to the number. Example: vobcopy  -b 500m will start to copy from 500MB onward till the end.
 -e, --end SIZE[bkmg] similar to -b, this options lets you specify some size to stop before the end.
 -f, --force force the output to the specified directory even if vobcopy thinks there is not enough free space
 -F, --fast fast_factor speed up the copying (experimental). fast_factor is in the range 1 to 64
 -h, --help print the command line options available
 -i, --input-dir INPUT-DIR provide vobcopy with the path to the mounted dvd drive
 -l, --large-file write data into one file (needs large file support (LFS))
 -m, --mirror mirrors the whole dvd to harddisk. It will create a directory named after the dvd and copy the ifo, bup and vob files there. The title-vobs are decrypted during this.
 -n, --title-number TITLE-NUMBER specify which title vobcopy shall copy (default is title with most chapters). On the dvd, vts_01_x.vob specify the first title (mostly this is the main feature).
 -o, --output-dir OUTPUT-DIR specify the output-directory of the data. "stdout" or "-" redirect to stdout. Useful for pipeing it to /dev/null ;-) If you forget to pipe it to some place, your terminal will get garbled, so remember that typing "reset" and then Enter will rescue you.
 -q, --quiet all info- and error-messages of vobcopy will end up in the current directory in vobcopy.bla instead of stderr
 -O, --onefile **single_file**(s)_to_rip specify which single **file**(s) to rip. Parts of names can be given and all files which include the part will be copied. Files can be listed with comma separation. Example: -O video_ts.vob,bup will copy the single file video_ts.vob and all files containing bup -t, --name NAME you can give the file a name if you don't like the one from dvd. -t hallo will result in hallo.vob. (stdout or "-" are deprecated now) If you want to give it names like "Huh I like this movie", do it in quotation marks.
 -v, --verbose prints more information about whats going on (more verbose).
 -v -v prints the information given on command line into a log-file in the current directory for inclusion into a bugreport.
 -L LOGFILE-PATH tells vobcopy where to put the logfile instead of the default.
 -I, --info prints information about the titles, chapters and angles on the dvd.
 -V, --version prints version number.
 -1, --1st_alt_output_dir AUXILIARY-OUTPUT-DIR1 if the data doesn't fit on the first output-directory (specified behind -o) writing will continue here (and after -2 there and -3 and -4) -> the files will be split according to the remaining free space (try specifying the path _directly_ behind -1, _no_ space in between if you have troubles, this might be even necessary at -o...)
```

---

