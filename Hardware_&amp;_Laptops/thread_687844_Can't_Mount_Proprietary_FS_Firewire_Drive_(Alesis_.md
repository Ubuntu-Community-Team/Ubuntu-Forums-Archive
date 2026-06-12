---
title: "Can't Mount Proprietary FS Firewire Drive (Alesis HD24)"
date: 2008-02-04
forum: Hardware &amp; Laptops
---

### Post by tistria on 2008-02-04
I'm trying to capture audio off of an Alesis Fireport, which used a proprietary file system.  The Fireport is an adapter that connects the drive from a professional audio recorder to a standard PC over Firewire. Alesis does not make a Linux driver/decoder, but I found a third-party [program]("http://ringbreak.dnd.utwente.nl/~mrjb/hd24tools/index.html") that should read the data.  Problem is, it can't find the drive.  The drive isn't in my fstab, but I know the computer sees it, as there is a firewire entry in /dev/disk/by-id - it's labeled "ieee1394-001010030000787e:0:0"

How can I make the program find the drive when I can't mount the filesystem?

For reference, my fstab reads:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=04574483-1255-40bd-ab32-4cdb5eab25cd /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb1
UUID=8e5b2886-f46a-4cfd-8da8-4e94d53a4a1a /home           ext3    defaults        0       2
# /dev/sda5
UUID=dcf762c3-5188-499a-a2ca-ef09ce56a7aa none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

---

### Post by Yellow Pasque on 2008-02-04
Can you give the output of?:
```
sudo lshw -C disk
```
(I would just like to see the section pertaining to the firewire drive).

---

### Post by tistria on 2008-02-04
Here you go:

```
  *-disk
       description: SCSI Disk
       product: Maxtor 6K040L0
       vendor: Initio
       physical id: 0.0.0
       bus info: scsi@15:0.0.0
       logical name: /dev/sdc
       version: 4.61
       size: 38GB
       capabilities: 10000rpm

```

---

### Post by Yellow Pasque on 2008-02-04
> logical name: /dev/sdc
Ok, the manual says to mount it with an entry like the following in your fstab:
```
/dev/sdc   none   auto   devmode=0775   0   0
```

---

### Post by tistria on 2008-02-04
Once I mounted it in fstab, I was able to read the disc, but it turns out that my HDD was corrupted. I put in another drive (after modifying fstab) and it recognized it right away.  Thanks for your help.

---

### Post by veda_sticks on 2008-06-06
I'm having trouble with hd24tools, have searched alot and tried contacting the writter of this software with no luck.

Running hd24connect gives

/home/alex/HD24tools/hd24connect_bin: error while loading shared libraries: libportaudio.so.0: cannot open shared object file: No such file or directory

I have portaudio installed  and i know that this file definatly exists.

---

### Post by kleinebre on 2008-06-09
**I'm having trouble with hd24tools, have searched alot and tried contacting the writer of this software with no luck.**

Hi, I'm the author of HD24tools. Your email may have been trapped by the spam filters, but fortunately Google Alerts informed me that you had posted a question.

**/home/alex/HD24tools/hd24connect_bin: error while loading shared libraries: libportaudio.so.0: cannot open shared object file: No such file or directory. I have portaudio installed and i know that this file definitely exists.**

Which version of portaudio do you have installed, and where? By default, HD24connect assumes portaudio V18, which should be available from the regular apt repository. You will need to have both libportaudio.so.0 and libportaudio.so.0.0.18 in your library search path; check file /etc/ld.so.conf contains a line there. In my case, both files are in /usr/lib so there is a line saying 

  /usr/lib 

in ld.so.conf. After making sure that the path is in there, you can run 

  sudo ldconfig

to apply any changes.

Let me know how this works out for you. 

Best,
Marc

---

### Post by jmail524 on 2008-06-29
Hello,

I am having the same problem that veda_sticks is having.  I have checked my /usr/lib directory and the 2 required libraries are there.  Also, I added the line "/usr/lib" to my /etc/ld.so.conf file.  Then I ran sudo ldconfig but the error still persists.  Any other suggestions?

Thanks,
Brian

---

### Post by kleinebre on 2008-06-30
> **jmail524 said:**
> Hello,

I am having the same problem that veda_sticks is having.  I have checked my /usr/lib directory and the 2 required libraries are there.  Also, I added the line "/usr/lib" to my /etc/ld.so.conf file.  Then I ran sudo ldconfig but the error still persists.  Any other suggestions?

Thanks,
Brian

If you get into the hd24tools directory and type 

  ldd ./hd24connect 

what output do you get? Perhaps this sheds more light on the matter.

Other than that, you have a few options. You can contact me via instant messenger, or try building from the latest svn source (which can be found on hd24tools.com) - this latest version deals differently with the shared libraries; or you can contact me at my hotmail address (which is my username here @hotmail.com). I'm  sure we'll manage to figure it out.

Best,
Marc

---

### Post by jmail524 on 2008-06-30
Hi Marc,

When I use the command "ldd ./hd24connect" I get the message "not a dynamic executable".  I am using hd24tools version 0.9.2beta and have also tried version 0.9.1beta.  I just realized that the file name had i386 in it, I am running Ubuntu 8.04 AMD64 (64-bit).  Maybe that is my problem. Do I need an AMD64 version?

Thanks,
Brian

---

### Post by kleinebre on 2008-07-01
> **jmail524 said:**
> Hi Marc,

When I use the command "ldd ./hd24connect" I get the message "not a dynamic executable".  I am using hd24tools version 0.9.2beta and have also tried version 0.9.1beta.  I just realized that the file name had i386 in it, I am running Ubuntu 8.04 AMD64 (64-bit).  Maybe that is my problem. Do I need an AMD64 version?

Thanks,
Brian

Hmmm, interesting. As at the moment I haven't got a 64 bit machine to play around with, I can't be sure, but it sort of would make sense. It seems like the most sensible way to proceed is to build from source- I suggest you contact me directly on my hotmail (my username @hotmail.com) so that we can sort it out. This will also allow me to add a 64-bit build to the configuration.

In the current source tree, the hard dependency on libportaudio/libjack/libsndfile is replaced by 'soft' dependencies: if the libraries aren't there, the program will run with limited functionality, but at least it will still run.

Thanks,
Marc

---

### Post by kleinebre on 2008-07-12
Bi Brian,

As a result of our email session, I've put together a little document, COMPILING.txt and placed this in the doc directory in subversion. This document contains the instructions for building and compiling HD24tools.

For those building from source, keep in mind that the subversion repository contains the latest of the latest development version and should therefore be considered UNTESTED ALPHA CODE. If it corrupts your data, blows up your computer or runs off with your girlfriend, you'll be on your own.

---

