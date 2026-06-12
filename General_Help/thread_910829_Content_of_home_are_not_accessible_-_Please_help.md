---
title: "Content of /home are not accessible - Please help"
date: 2008-09-04
forum: General Help
---

### Post by prafullk on 2008-09-04
**Anybody Please Help**

I was running ubuntu in the live mode and after i clicked the install button, data of the /home directory of my already installed ubuntu got hidden or something. it still shows the memory occupied but instead of the data of home some files naming 
k01gdm
/home/K01usplash
/home/K16dhcdbd
/home/K20apport
/home/K20avahi-daemon
/home/K25hwclock.sh
/home/K39ufw
/home/K50alsa-utils
/home/K59mountoverflowtmp
/home/K99laptop-mode
/home/README
/home/S01linux-restricted-modules-common
/home/S15wpa-ifupdown
/home/S20sendsigs
/home/S30urandom
/home/S31umountnfs.sh
/home/S40umountfs
/home/S60umountroot
/home/S90reboot
are there two new files naming
/opt - 4.0 GB 
/usr - 4.0 GB
also got created .... is the data hidden in these files ???

all the data was very much of use to me is there any way to recover those hidden files ? anybody Please help

---

### Post by aloshbennett on 2008-09-05
Looks like you have all the contents of ./etc/rc6.d/ in your home.
Can you post the output the output of the following?

> ls -lda /*
ls -l /opt
ls -l /usr

If you remember the name of any of your files you had in your home directory, can you try > locate filename

---

### Post by prafullk on 2008-09-05
first of all thanks for the reply 
output of 'ls -lda /*' was
drwxr-xr-x   2 root root  4096 2008-08-29 09:59 /bin
drwxr-xr-x   3 root root  4096 2008-08-29 09:58 /boot
lrwxrwxrwx   1 root  999    11 2008-08-29 09:37 /cdrom -> media/cdrom
drwxr-xr-x  13 root root 14120 2008-08-26 03:10 /dev
drwxr-xr-x 122 root root  4096 2008-08-26 03:28 /etc
drwxr-xr-x   3 root root  4096 2008-08-29 09:52 /home
drwxr-xr-x   2 root root  4096 2008-07-02 06:16 /initrd
lrwxrwxrwx   1 root  999    33 2008-08-29 09:58 /initrd.img -> boot/initrd.img-2.6.24-19-generic
drwxr-xr-x  16 root root  4096 2008-08-29 09:59 /lib
drwx------   2 root root 16384 2008-08-29 09:36 /lost+found
drwxr-xr-x   4 root root  4096 2008-08-26 03:10 /media
drwxr-xr-x   2 root root  4096 2008-04-15 01:53 /mnt
drwxr-xr-x   2 root root  4096 2008-07-02 06:16 /opt
dr-xr-xr-x 111 root root     0 2008-08-26 03:09 /proc
drwxr-xr-x   8 root root  4096 2008-08-19 11:28 /root
drwxr-xr-x   2 root root  4096 2008-08-29 10:00 /sbin
drwxr-xr-x   2 root root  4096 2008-07-02 06:16 /srv
drwxr-xr-x  12 root root     0 2008-08-26 03:09 /sys
drwxrwxrwt  13 root root  4096 2008-08-26 03:38 /tmp
drwxr-xr-x  11 root root  4096 2008-07-02 06:18 /usr
drwxr-xr-x  15 root root  4096 2008-07-02 06:34 /var
lrwxrwxrwx   1 root  999    30 2008-08-29 09:58 /vmlinuz -> boot/vmlinuz-2.6.24-19-generic

output of 'ls -l /opt'
total 0

output of 'ls -l /usr'
total 136
drwxr-xr-x   2 root root 36864 2008-08-20 08:56 bin
drwxr-xr-x   2 root root  4096 2008-07-02 06:20 games
drwxr-xr-x  11 root root  4096 2008-07-02 06:21 include
drwxr-xr-x 163 root root 53248 2008-08-19 15:30 lib
drwxr-xr-x  10 root root  4096 2008-07-02 06:16 local
drwxr-xr-x   2 root root 12288 2008-08-29 10:00 sbin
drwxr-xr-x 291 root root 12288 2008-08-20 08:56 share
drwxrwsr-x   4 root src   4096 2008-07-02 06:36 src
drwxr-xr-x   2 root root  4096 2008-07-02 06:18 X11R6
 
and the locate command couldn't find anything

---

### Post by prafullk on 2008-09-05
plz help ......

---

### Post by prafullk on 2008-09-06
> **aloshbennett said:**
> Looks like you have all the contents of ./etc/rc6.d/ in your home.
Can you post the output the output of the following?



If you remember the name of any of your files you had in your home directory, can you try
first of all thanks for the reply
output of 'ls -lda /*' was
drwxr-xr-x 2 root root 4096 2008-08-29 09:59 /bin
drwxr-xr-x 3 root root 4096 2008-08-29 09:58 /boot
lrwxrwxrwx 1 root 999 11 2008-08-29 09:37 /cdrom -> media/cdrom
drwxr-xr-x 13 root root 14120 2008-08-26 03:10 /dev
drwxr-xr-x 122 root root 4096 2008-08-26 03:28 /etc
drwxr-xr-x 3 root root 4096 2008-08-29 09:52 /home
drwxr-xr-x 2 root root 4096 2008-07-02 06:16 /initrd
lrwxrwxrwx 1 root 999 33 2008-08-29 09:58 /initrd.img -> boot/initrd.img-2.6.24-19-generic
drwxr-xr-x 16 root root 4096 2008-08-29 09:59 /lib
drwx------ 2 root root 16384 2008-08-29 09:36 /lost+found
drwxr-xr-x 4 root root 4096 2008-08-26 03:10 /media
drwxr-xr-x 2 root root 4096 2008-04-15 01:53 /mnt
drwxr-xr-x 2 root root 4096 2008-07-02 06:16 /opt
dr-xr-xr-x 111 root root 0 2008-08-26 03:09 /proc
drwxr-xr-x 8 root root 4096 2008-08-19 11:28 /root
drwxr-xr-x 2 root root 4096 2008-08-29 10:00 /sbin
drwxr-xr-x 2 root root 4096 2008-07-02 06:16 /srv
drwxr-xr-x 12 root root 0 2008-08-26 03:09 /sys
drwxrwxrwt 13 root root 4096 2008-08-26 03:38 /tmp
drwxr-xr-x 11 root root 4096 2008-07-02 06:18 /usr
drwxr-xr-x 15 root root 4096 2008-07-02 06:34 /var
lrwxrwxrwx 1 root 999 30 2008-08-29 09:58 /vmlinuz -> boot/vmlinuz-2.6.24-19-generic

output of 'ls -l /opt'
total 0

output of 'ls -l /usr'
total 136
drwxr-xr-x 2 root root 36864 2008-08-20 08:56 bin
drwxr-xr-x 2 root root 4096 2008-07-02 06:20 games
drwxr-xr-x 11 root root 4096 2008-07-02 06:21 include
drwxr-xr-x 163 root root 53248 2008-08-19 15:30 lib
drwxr-xr-x 10 root root 4096 2008-07-02 06:16 local
drwxr-xr-x 2 root root 12288 2008-08-29 10:00 sbin
drwxr-xr-x 291 root root 12288 2008-08-20 08:56 share
drwxrwsr-x 4 root src 4096 2008-07-02 06:36 src
drwxr-xr-x 2 root root 4096 2008-07-02 06:18 X11R6

and the locate command couldn't find anything
Last edited by prafullk; 16 Hours Ago at 10:23 PM.
prafullk is online now Report Post   	Edit/Delete Message

---

### Post by aloshbennett on 2008-09-08
Ok. So you are sure the data is present somewhere because its eating up your space.
/opt shows empty but you say it is taking 4 GB space.
Hidden files?
Have you checked ls -la /opt ?

---

### Post by prafullk on 2008-09-09
well i formatted my drive.... nd neways thanx for the support......

---

