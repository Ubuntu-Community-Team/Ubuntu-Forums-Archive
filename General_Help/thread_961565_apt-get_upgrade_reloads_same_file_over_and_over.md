---
title: "apt-get upgrade reloads same file over and over"
date: 2008-10-28
forum: General Help
---

### Post by whizbaby on 2008-10-28
Hello!
I created a repository on a server in my network using apt-mirror(worked fine), then used bozohttpd to make the repo available via http.
Back on a client with sources.list modified to point at my server, I can visit the repo with e.g. firefox and download files from it. Getting a file with wget doesnt present any problem and installing a single package with apt-get (I tried qgo) worked, too. Now to the weird part:
If I (after of course apt-get update) do an
```
apt-get upgrade
```
it seems apt downloads the same file over and over again
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  k3b
The following packages will be upgraded:
  acroread acroread-escript acroread-plugins gstreamer0.10-plugins-bad
  gtk2-engines-pixbuf libgtk2.0-0 libgtk2.0-bin libgtk2.0-common
  linux-headers-2.6.24-21 linux-headers-2.6.24-21-generic
  linux-image-2.6.24-21-generic linux-libc-dev mozilla-acroread
  thunderbird-locale-de thunderbird-locale-en-gb tzdata xkb-data
17 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 80.2MB/81.5MB of archives.
After this operation, 53.2kB of additional disk space will be used.
Do you want to continue [Y/n]? 
Get:1 http://soni hardy-updates/main linux-image-2.6.24-21-generic 2.6.24-21.43 [18.4MB]
Get:2 http://soni hardy-updates/main linux-image-2.6.24-21-generic 2.6.24-21.43 [18.4MB]
Get:3 http://soni hardy-updates/main linux-image-2.6.24-21-generic 2.6.24-21.43 [18.4MB]
14% [3 linux-image-2.6.24-21-generic 11801198/18.4MB 64%] [Connecting to packag
```
and so on if I hadn't stopped it(waited until 48 repetitions already). Anyone got an idea whats wrong with my setup? Downloading linux-image-2.6.24-21-generic with wget or a browser from the same location is working...

---

### Post by bodhi.zazen on 2008-10-28
hard to say from what you posted it appears as if the transfer is incomplete.

I would try, in order,

sudo apt-get update
sudo apt-get dist-upgrade
sudo aptitude upgrade

---

### Post by whizbaby on 2008-10-29
Thanks for the suggestions, but that was the first thing I tried :)
Indeed, the transfer is incomplete. But it restarts all the time. Here is the output of a couple of 'date; ls -lh /var/cache/apt/archives/partial' while apt-get is running:

```
Wed Oct 29 11:29:45 CET 2008
total 376K
-rw-r--r-- 1 root root 369K 2008-10-29 11:29 linux-image-2.6.24-21-generic_2.6.24-21.43_i386.deb

Wed Oct 29 11:29:46 CET 2008
total 4.6M
-rw-r--r-- 1 root root 4.6M 2008-10-29 11:29 linux-image-2.6.24-21-generic_2.6.24-21.43_i386.deb

Wed Oct 29 11:29:46 CET 2008
total 9.1M
-rw-r--r-- 1 root root 9.1M 2008-10-29 11:29 linux-image-2.6.24-21-generic_2.6.24-21.43_i386.deb

Wed Oct 29 11:29:47 CET 2008
total 14M
-rw-r--r-- 1 root root 14M 2008-10-29 11:29 linux-image-2.6.24-21-generic_2.6.24-21.43_i386.deb

Wed Oct 29 11:29:47 CET 2008
total 136K
-rw-r--r-- 1 root root 132K 2008-10-29 11:29 linux-image-2.6.24-21-generic_2.6.24-21.43_i386.deb

Wed Oct 29 11:29:49 CET 2008
total 18M
-rw-r--r-- 1 root root 18M 2008-10-29 11:29 linux-image-2.6.24-21-generic_2.6.24-21.43_i386.deb

```

it seems to restart at 0 when the fiel transfer is complete.
To provide a bit more info about the server:
hardy server installed, no extra software chosen during installation.
Installed apt-mirror and bozohttpd. Partition with mirror is mounted at /var/www/repo and I can see it there (and apt-cache on the client can, too) and load files with wget or install single programs (though not linux-image) on the clients.
If you need any specific info just tell me and ill post it.

p.s.: btw I can wget linux-image-2.6.24-21-generic-_2.6.24-21.43_i386.deb without problem...

---

### Post by whizbaby on 2008-10-30
Ok I got it sorted out (if anybody interested). It seems to be a bozohttpd issue because switching to apache2 'cured' the behaviour.
So: if you want to do an apt mirror accessible with http DONT use bozohttpd.,.

p.s.: I could easily reproduce the bozohttpd behaviour on three different servers I set up exactly like the first one, hardy from cd, apt-mirror + bozohttpd. Its simply not working without any complaint in any log. bozo too light it seems.

---

