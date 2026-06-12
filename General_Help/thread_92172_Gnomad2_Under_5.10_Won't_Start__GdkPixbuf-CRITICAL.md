---
title: "Gnomad2 Under 5.10 Won't Start:  GdkPixbuf-CRITICAL"
date: 2005-11-18
forum: General Help
---

### Post by shewbox on 2005-11-18
Using Ubuntu 5.10, I get the following error when trying to open Gnomad2 (i installed via apt-get):

ben@ubuntu:~$ gnomad2

(gnomad2:8134): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_from_file: assertion `error == NULL || *error == NULL' failed
The program 'gnomad2' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadWindow (invalid Window parameter)'.
  (Details: serial 930 error_code 3 request_code 1 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

Anyone have any ideas?

---

### Post by fog on 2005-11-27
I have the same problem with my Creative Jukebox 3 the last few days, after some updates.
Stop working, with the same error.
>  (gnomad2:11924): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_from_file: assertion `error == NULL || *error == NULL' failed
Xlib: unexpected async reply (sequence 0x79b)!

---

### Post by xsupernerdx on 2006-01-18
Has anyone figured this out? I was able to get Gnomad2 to run once and then it started giving me this error every time I try to run it - whether it was as user, sudo, or gksudo. Any help is appreciated.

---

### Post by pjstadig on 2006-02-06
I have the same problem.

---

### Post by pjstadig on 2006-02-06
I tried following the instructions at [http://ubuntuforums.org/showthread.php?t=33040](http://ubuntuforums.org/showthread.php?t=33040) and installing the latest versions of libnjb and gnomad2, but I still get the same error.

---

### Post by cbudden on 2006-02-06
I used the dapper packages to get my Creative Zen to work.  Here they are with the two config files for /etc/hotplug/usb/ - [http://www.sitesled.com/members/cbudden/gnomad2.zip](http://www.sitesled.com/members/cbudden/gnomad2.zip)

May fix your problem, may not.

Don't forget to restart hotplug before you try gnomad ( sudo /etc/init.d/hotplug restart )

Good Luck.

---

### Post by pjstadig on 2006-02-19
cbudden
I didn't try to install the packages, but I noticed the differences between the /etc/hotplug/usb/nomadjukebox file and the /etc/hotplug/usb/nomad.usermap file.

The nomad.usermap file in your zip archive has this extra line:
> # Creative Zen (Zen Micro variant)
nomadjukebox	0x0003	0x041e	0x411d	0x0000	0x0000	0x00	0x00	0x00	0x00	0x00	0x00	0x00000000


The nomadjukebox file changes the 6th and 7th lines from:
> DEVICEOWNER=root:audio
DEVICEPERMS=0666


to:

> DEVICEOWNER=CONSOLE
DEVICEPERMS=0600


I'll have to see if any of this helps.  Thanks.

---

### Post by nandes on 2006-02-25
[QUOTE=cbudden]I used the dapper packages to get my Creative Zen to work.  Here they are with the two config files for /etc/hotplug/usb/ - [http://www.sitesled.com/members/cbudden/gnomad2.zip](http://www.sitesled.com/members/cbudden/gnomad2.zip)

May fix your problem, may not.

Don't forget to restart hotplug before you try gnomad ( sudo /etc/init.d/hotplug restart )

Good Luck.[/QUOTE]

Installed your debs packages and now seems to work!

---

### Post by xsupernerdx on 2006-02-25
Sorry if this is a stupid question, but which debs did you install? I'd reaqlly like to get this working. Thanks in advance.

---

### Post by nandes on 2006-02-25
[QUOTE=xsupernerdx]Sorry if this is a stupid question, but which debs did you install? I'd reaqlly like to get this working. Thanks in advance.[/QUOTE]

the debs inside [http://www.sitesled.com/members/cbudden/gnomad2.zip]("http://www.sitesled.com/members/cbudden/gnomad2.zip")

---

### Post by xsupernerdx on 2006-02-27
Thanks for answering my dumb question. Unfortunately I still can't get Gnomad to work.

---

