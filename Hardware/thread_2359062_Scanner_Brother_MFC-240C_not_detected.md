---
title: "Scanner Brother MFC-240C not detected"
date: 2017-04-20
forum: Hardware
---

### Post by sp40140 on 2017-04-20
I recently did fresh install of 17.04 64bit Ubuntu. And now my MFC-240C all-in-one is giving me trouble. The printer driver installed fine. But the scanner isn't recognized.
I did have it working with 16.10 64bit though.
I followed Brother's instructions. (Which are simplified on this page by a kind spirit and this page helped last time I got it working on 16.10 : [https://sites.google.com/site/easylinuxtipsproject/15](https://sites.google.com/site/easylinuxtipsproject/15))
summary:
I ran Brother's driver install tool. No issues during run. I edited 40-libsane.rules to add entry for Brother scanner. 
I also edited 60-libsane.rules as suggested by a user in this thread ([https://ubuntuforums.org/showthread.php?t=2321613](https://ubuntuforums.org/showthread.php?t=2321613)) as he mentions that for 17.04 you need to work on that file.
I also tried suggestions from the thread mentioned above.
I also ran the individual .deb files from brother for my scanner. Again no errors.
As a last resort, I also added brother.conf file with proper entry in /etc/sane.d/ as someone suggested. It didn't work either. (I have since removed the entry as I was worried about any potential conflicts and I didn't have to do it on 16.10).
Ubuntu knows that there is a scanner attached, it gives me vendor and device ids.
Just that it doesn't get detected by any applications: sane (with gksudo), xsane, Gimp (just uses xsane though).

Now I am stuck as I have run out of things to try to sort this out.
Help.

---

### Post by pdc on 2017-04-20
thanks for this very good and very detailed post; most helpful;

Brother's instructions are detailed but seem to some to be in many places; so they provide an FAQ page but one needs to know where to look [http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&redirect=on](http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&redirect=on)

In one of the sections, they ask which category one's printer is in: yours in a brscan2

for the 16.10 they said ```
sudo apt-get install libusb-0.1-4
``` if you don't already have it in [http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&redirect=on#f00107](http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&redirect=on#f00107) 

and another section [http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&redirect=on#f00101](http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&redirect=on#f00101)

says ```
Copy the following files under /usr/lib64/ to /usr/lib/.
```

and there are a host that follow 

```
/usr/lib64/libbrscandec2.so.1.0.0
/usr/lib64/sane/libsane-brother2.so.1.0.7
/usr/lib64/sane/libsane-brother2.so.1
/usr/lib64/sane/libsane-brother2.so
/usr/lib64/libbrcolm2.so.1.0.1
/usr/lib64/libbrcolm2.so
/usr/lib64/libbrscandec2.so.1
/usr/lib64/libbrscandec2.so
/usr/lib64/libbrcolm2.so.1
```

If none of those are in /usr/lib then the format of the command is ```
sudo cp /usr/lib64/libbrscandec2.so.1.0.0 /usr/lib
``` ....... I have used the top line as an example and then you need to do the same format for the next eight lines: if we see if that works

Pjotr from the Mint forum who does the instructions: they offer brscan3 format commands and don't (to me) seem to cover all the variants

---

### Post by sp40140 on 2017-04-20
@pdc, thank you your suggestions. 
I already have libusb installed. However, I have newer version of it. And I can't find older one. And not I should be installing both versions anyway. Find below.
```

dell@DELL:~$ sudo apt-get install libusb-0.1-4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libusb-0.1-4
E: Couldn't find any package by glob 'libusb-0.1-4'
E: Couldn't find any package by regex 'libusb-0.1-4'

```
```

dell@DELL:~$ sudo dpkg -l | grep libusb
ii  libgusb2:amd64                                  0.2.9-1                                     amd64        GLib wrapper around libusb1
ii  libusb-1.0-0:amd64                              2:1.0.21-1                                  amd64        userspace USB programming library
ii  libusbmuxd4:amd64                               1.0.10-3                                    amd64        USB multiplexor daemon for iPhone and iPod Touch devices - library
dell@DELL:~$ 

```

Also, I have already copied all relevant files from lib64 to lib. It didn't work.
```

dell@DELL:~$ ls -ltr /usr/lib64/
total 60
-rwxr-xr-x 1 root root 37064 Dec  1  2009 libbrscandec2.so.1.0.0
lrwxrwxrwx 1 root root    33 Dec  1  2009 libbrscandec2.so.1 -> /usr/lib64/libbrscandec2.so.1.0.0
lrwxrwxrwx 1 root root    29 Dec  1  2009 libbrscandec2.so -> /usr/lib64/libbrscandec2.so.1
-rwxr-xr-x 1 root root 15072 Dec  1  2009 libbrcolm2.so.1.0.1
lrwxrwxrwx 1 root root    30 Dec  1  2009 libbrcolm2.so.1 -> /usr/lib64/libbrcolm2.so.1.0.1
lrwxrwxrwx 1 root root    26 Dec  1  2009 libbrcolm2.so -> /usr/lib64/libbrcolm2.so.1
drwxr-xr-x 2 root root  4096 Apr 20 19:40 sane
dell@DELL:~$ ls -ltr /usr/lib64/sane
total 112
-rwxr-xr-x 1 root root 112832 Dec  1  2009 libsane-brother2.so.1.0.7
lrwxrwxrwx 1 root root     41 Dec  1  2009 libsane-brother2.so.1 -> /usr/lib64/sane/libsane-brother2.so.1.0.7
lrwxrwxrwx 1 root root     37 Dec  1  2009 libsane-brother2.so -> /usr/lib64/sane/libsane-brother2.so.1
dell@DELL:~$ 

```
same files exist in /usr/lib as well (along with lots of other files not related to Brother MFC).

---

### Post by pdc on 2017-04-21
```
same files exist in /usr/lib
``` thanks; I had wondered if the Brother installer tool wouldn't be set up to recognise that you were brscan2 and thus copy those files already ........

one seems to get these issues with moving to new versions of things: the brave ones explore the issues and they slowly get resolved; best to look here [https://help.ubuntu.com/community/Scanners](https://help.ubuntu.com/community/Scanners) for troubleshooting: various diagnostics one can run to attempt to resolve the issues

at the risk of seeming a heretic, I often feel the Arch folks do very good wikis and here is there sane one [https://wiki.archlinux.org/index.php/SANE](https://wiki.archlinux.org/index.php/SANE) ..... one can run various command lines to diagnose and see if one can scan 

The SANE folks [http://www.sane-project.org/](http://www.sane-project.org/) also had an FAQ page but I can't currently find it 

17.04 finishes in Jan 2018 so you only have to live with it for 8 months; 18.04 will be the LTS release that should take folks through to 2023

---

### Post by TheFu on 2017-04-21
I have a tiny 14.04 VM for scanning only. Only power it up when necessary - about 3 days a year.  I have the same Brother all-in-one and never use it to actually print, BTW.  Have a $50 laserprinter for that. The ink costs were just too high, so after the first ink dried out, I never replaced it.

---

### Post by sp40140 on 2017-04-21
@pdc
Thank you for additional links, I will go over them. Hope to fix it.

@TheFu
I have win7 running in VMware and it works for scanning. Scanning is one of the very few things I have to boot windows for and I would like to avoid it if I can. This issue is no big trouble to me. And I also have old laser printer which works.
The troubleshooting is more out of curiosity/interest/not like having broken set-up. 
I can live with 17.04 not scanning.

---

### Post by TheFu on 2017-04-21
Yep. VMs are good for all sorts of unexpected things.  I'm addicted to scanning from anywhere on the network. Can't easily do that from Windows, but it is build-in thanks to X/Windows.

Have some friends with really old printers that never got driver updates from 32-bit WinXP.  They just put their XP install into a VM and power it up for printing only.  I have an old XP VM somewhere with a full MS-Office (pre-ribbon) install that I haven't used in about 5 yrs, but I never know if I'll need Visio at some point in the future, so it is still around.  Sadly, I've never found anything close to Visio in the F/LOSS world.  Folks who suggest Dia or any of the other graphics/outline tools simply don't understand the power of Visio.

Anyway, glad you have a workaround.

---

### Post by sp40140 on 2017-04-21
I will give it a try after a little while. Put this on back burner.

---

### Post by sp40140 on 2017-05-24
I was finally able to install libusb-0.1-4.
And it sorted out the problem.

---

