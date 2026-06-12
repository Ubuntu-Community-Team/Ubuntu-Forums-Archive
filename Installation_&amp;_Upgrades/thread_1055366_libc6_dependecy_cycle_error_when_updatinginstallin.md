---
title: "libc6 dependecy cycle error when updating/installing"
date: 2009-01-30
forum: Installation &amp; Upgrades
---

### Post by Teiji on 2009-01-30
Hi,

I tried to install a csh shell, but I keep getting this error:

E: Couldn't configure pre-depend libc6 for findutils, probably a dependency cycle.

That error also appears when I tried to update anything from the Update manager or the commandline.

Does anyone know how to fix that? Mainly, on how to install the csh shell.

---

### Post by Partyboi2 on 2009-01-31
You could try the last comment from [[COLOR=Blue]here[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/aptitude/+bug/124895")

---

### Post by Teiji on 2009-02-01
Thanks Partyboi2. I'm very new to Ubuntu and Unix, so I need some help on doing what Rodolfo mentioned.

Quoted from Rodolfo:

> After cleaning apt-get's cache, I tried one more time without good results; but with that I generated a "clean" cache (ie only with the debs I was needing).

How do I clean the apt-get's cache?

> Then did

cd /var/cache/apt/archives

and then

sudo dpkg --force-depends --install libc6_2.8~20080505-0ubuntu7_i386.deb findutils_4.4.0-2ubuntu3_i386.deb

of course the specific package names may differ.

Where do I get the libc6xxxxxxxxxxx.deb?

---

### Post by Partyboi2 on 2009-02-01
Actually you may not need to empty cache.
Open a terminal (Applications>Accessories>Terminal) then change into the /var/cache/apt/archives directory
```
cd /var/cache/apt/archives
```then use the list command to see what is there
```
ls
```look for libc6xxxxxxxxxxx.deb and findutilsxxxxxxxx.deb, then type
```
sudo dpkg --force-depends --install libc6xxxxxxxxxxx.deb findutilsxxxxxxxx.deb
``` using the correct name of the 2 deb packages from the output of the list command

---

### Post by Teiji on 2009-02-03
It doesn't work.

Here's what I did and the error I received.

ubuntu@ubuntu:~$ cd /var/cache/apt/archives
ubuntu@ubuntu:/var/cache/apt/archives$ ls
csh_20070713-1_i386.deb
findutils_4.4.0-2ubuntu3_i386.deb
gcc-4.3-base_4.3.2-1ubuntu12_i386.deb
libc6_2.8~20080505-0ubuntu8_i386.deb
libgcc1_1%3a4.3.2-1ubuntu12_i386.deb
libncurses5_5.6+20071124-1ubuntu2_i386.deb
lock
partial
tcsh_6.14.00-7ubuntu1_i386.deb
ubuntu@ubuntu:/var/cache/apt/archives$ sudo dpkg --force-depends --install libc6_2.8~20080505-0ubuntu8_i386.deb findutils_4.4.0-2ubuntu3_i386.deb
**dpkg: failed in buffer_read(fd): copy info file `/var/lib/dpkg/available': Input/output error**
ubuntu@ubuntu:/var/cache/apt/archives$

Anyone have any other solution? I need to install other shells beside the default one to do different assignments that my teacher give out. Please help me.

---

### Post by Partyboi2 on 2009-02-03
Open a terminal and backup the current available file
```
sudo mv /var/lib/dpkg/available /var/lib/dpkg/available.broken
```
then move available-old to available 
```
sudo mv /var/lib/dpkg/available-old /var/lib/dpkg/available
```
then try what you did before.
```
cd /var/cache/apt/archives
```
```
sudo dpkg --force-depends --install libc6_2.8~20080505-0ubuntu8_i386.deb findutils_4.4.0-2ubuntu3_i386.deb

```

---

### Post by Teiji on 2009-02-04
I received the same error as before. =/

dpkg: failed in buffer_read(fd): copy info file `/var/lib/dpkg/available': Input/output error

---

### Post by Partyboi2 on 2009-02-05
I am almost out of ideas. Try 
```
sudo apt-get clean
```This will remove the deb files in /var/cache/apt/archives. Then download the debs again.
```
sudo apt-get --reinstall install libc6
``````
sudo apt-get --reinstall install findutils
``` It will download fresh debs to /var/cache/apt/archives but probably will complain when it tries to reinstall those packages, but as long as the 2 packages have been downloaded again you should be able to proceed.
Then 
```
cd /var/cache/apt/archives
```then check that the newly downloaded debs are there
```
ls
``` then 
```
sudo dpkg --force-depends --install libc6_2.8~20080505-0ubuntu8_i386.deb findutils_4.4.0-2ubuntu3_i386.deb

```

---

### Post by Teiji on 2009-02-08
Thanks for the replies, but I still received the same error.
"dpkg: failed in buffer_read(fd): copy info file `/var/lib/dpkg/available': Input/output error"

Do you think it's because I'm running Ubuntu on a USB drive?

---

### Post by Teiji on 2009-02-09
Thank you partyboi for the replies, but I've given up on this. Partial install causes so much problems.

So I installed a FULL Ubuntu 8.10 this time and the problem isn't there anymore. :)

Topic closed.

---

