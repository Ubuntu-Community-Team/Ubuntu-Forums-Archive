---
title: "Update problems?"
date: 2009-07-02
forum: Installation &amp; Upgrades
---

### Post by GO%)$@*1 on 2009-07-02
I'm trying to update (I have about 10 updates to download and install) but I keep getting this error message:

E: /var/cache/apt/archives/lsb-base_4.0-0ubuntu0.9.04.1_all.deb: trying to overwrite `/etc/lsb-base-logging.sh', which is also in package splashy

I'm not very experienced in this area, but just by reading it, I can relate that I am having a problem with splashy when I boot. Something like error -10. I tried updating as root superuser:

```
sudo aptitude upgrade
```The terminal said that update was deprecated and changed it to "safe-upgrade" or the like. It didn't have any effect. I got


```

root@PRIVACY BLOCKED:/home/PRIVACY BLOCKED# sudo aptitude upgrade
W: The "upgrade" command is deprecated; use "safe-upgrade" instead.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages will be upgraded:
  language-selector language-selector-common libcompress-raw-zlib-perl 
  libpurple-bin libpurple0 linux-headers-2.6.28-13 
  linux-headers-2.6.28-13-generic linux-libc-dev lsb-base lsb-release 
  pidgin pidgin-data 
12 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/13.6MB of archives. After unpacking 45.1kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 118987 files and directories currently installed.)
Preparing to replace lsb-base 3.2-20ubuntu4 (using .../lsb-base_4.0-0ubuntu0.9.04.1_all.deb) ...
Unpacking replacement lsb-base ...
dpkg: error processing /var/cache/apt/archives/lsb-base_4.0-0ubuntu0.9.04.1_all.deb (--unpack):
 trying to overwrite `/etc/lsb-base-logging.sh', which is also in package splashy
Errors were encountered while processing:
 /var/cache/apt/archives/lsb-base_4.0-0ubuntu0.9.04.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
```
Help please. Sorry if I said or did stuff wrong because I made this account a time ago just to look at a file and this is my first time posting on it.

-kn

---

### Post by quixote on 2009-07-03
Possibly, this is a bug.  There's an incomprehensible (to me) [bug report for Ubuntu]("https://bugs.launchpad.net/ubuntu/+source/lsb/+bug/386770/+activity"), and [another one]("https://bugs.launchpad.net/kuki/+bug/394431") for a distro I haven't heard of.

Does this problem prevent all upgrading?  Or does it just complain, but otherwise everything is normal?  If the latter, I'd just not worry about it and hope one of the updates fixed it eventually.  But that's because I have no idea what's wrong :(

---

### Post by GO%)$@*1 on 2009-07-06
Quixote,

i couldn't make sense of the bug report either. And, in response to your question, no, the bug prevents me from upgrading at all, terminal or update manager. I've never had this before. 


Help
kn

---

### Post by earthpigg on 2009-07-06
```
dpkg: error processing /var/cache/apt/archives/lsb-base_4.0-0ubuntu0.9.04.1_all.deb (--unpack):
```

could just be a corrupted download?

have you tried using apt-get instead of aptitude to update?

if that didn't work, i would try removing the problematic .deb from the apt archive myself so that apt-get or aptitude would see that it is gone and download it over again:

```
sudo rm /var/cache/apt/archives/lsb-base_4.0-0ubuntu0.9.04.1_all.deb
```

---

### Post by Soul-Sing on 2009-07-06
or try this:
```
dpkg --clean-avail
apt-get update
```

---

### Post by GO%)$@*1 on 2009-07-06
I tried the code you guys gave me. I removed the .deb package. I also did a sudo apt-get upgrade. It took longer than usual. The terminal didn't get the "dpkg" command. Once I completed the commands, I tried using update manager to update. The "Install Updates" button didn't do anything, but the "Check" button did.I tried what I did before:

```
sudo aptitude upgrade
```

and got this as output:

```
private@private:~$ sudo aptitude upgrade
W: The "upgrade" command is deprecated; use "safe-upgrade" instead.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information        
Initializing package states... Done
Writing extended state information... Done
The following packages will be upgraded:
  hal language-selector language-selector-common libcompress-raw-zlib-perl 
  libhal-storage1 libhal1 libpurple-bin libpurple0 libtiff4 
  linux-headers-2.6.28-13 linux-headers-2.6.28-13-generic linux-libc-dev 
  lsb-base lsb-release pidgin pidgin-data ubuntu-tweak wine 
18 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 13.7MB/23.9MB of archives. After unpacking 475kB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 http://wine.budgetdedicated.com jaunty/main wine 1.1.25~winehq0~ubuntu~9.04-0ubuntu1 [8422kB]
Get:2 http://security.ubuntu.com jaunty-security/main libpurple-bin 1:2.5.5-1ubuntu8.3 [97.5kB]
Get:3 http://ppa.launchpad.net jaunty/main ubuntu-tweak 0.4.7.3-1~jaunty1 [1263kB]
Get:4 http://us.archive.ubuntu.com jaunty-updates/main lsb-base 4.0-0ubuntu0.9.04.1 [24.4kB]
Get:5 http://us.archive.ubuntu.com jaunty-updates/main libhal1 0.5.12~rc1+git20090403-0ubuntu4 [93.6kB]
Get:6 http://security.ubuntu.com jaunty-security/main pidgin-data 1:2.5.5-1ubuntu8.3 [1151kB]
Get:7 http://us.archive.ubuntu.com jaunty-updates/main libhal-storage1 0.5.12~rc1+git20090403-0ubuntu4 [22.7kB]
Get:8 http://us.archive.ubuntu.com jaunty-updates/main hal 0.5.12~rc1+git20090403-0ubuntu4 [395kB]
Get:9 http://security.ubuntu.com jaunty-security/main libpurple0 1:2.5.5-1ubuntu8.3 [1553kB]
Get:10 http://security.ubuntu.com jaunty-security/main libtiff4 3.8.2-11ubuntu0.9.04.1 [126kB]
Get:11 http://security.ubuntu.com jaunty-security/main pidgin 1:2.5.5-1ubuntu8.3 [519kB]
Fetched 13.7MB in 23s (579kB/s)                                                 
(Reading database ... 119837 files and directories currently installed.)
Preparing to replace wine 1.1.24~winehq0~ubuntu~9.04-0ubuntu1 (using .../wine_1.1.25~winehq0~ubuntu~9.04-0ubuntu1_i386.deb) ...
Unpacking replacement wine ...
Preparing to replace lsb-base 3.2-20ubuntu4 (using .../lsb-base_4.0-0ubuntu0.9.04.1_all.deb) ...
Unpacking replacement lsb-base ...
dpkg: error processing /var/cache/apt/archives/lsb-base_4.0-0ubuntu0.9.04.1_all.deb (--unpack):
 trying to overwrite `/etc/lsb-base-logging.sh', which is also in package splashy
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/lsb-base_4.0-0ubuntu0.9.04.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up wine (1.1.25~winehq0~ubuntu~9.04-0ubuntu1) ...
 * Setting kernel variables (/etc/sysctl.conf)...                        [ OK ] 
 * Setting kernel variables (/etc/sysctl.d/10-console-messages.conf)...  [ OK ] 
 * Setting kernel variables (/etc/sysctl.d/10-network-security.conf)...  [ OK ] 
 * Setting kernel variables (/etc/sysctl.d/30-tracker.conf)...           [ OK ] 
 * Setting kernel variables (/etc/sysctl.d/wine.sysctl.conf)...          [ OK ] 

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

Current status: 17 updates [-1].
```

I have no idea if that means the update was sucessful. I tried Update Manager again and got the same output:

```
E: /var/cache/apt/archives/lsb-base_4.0-0ubuntu0.9.04.1_all.deb: trying to overwrite `/etc/lsb-base-logging.sh', which is also in package splashy
```

At the next box, I got:

```
(Reading database ... 119841 files and directories currently installed.)
Preparing to replace lsb-base 3.2-20ubuntu4 (using .../lsb-base_4.0-0ubuntu0.9.0
4.1_all.deb ...
Unpacking replacement lsb-base ...
dpkg: error processing /var/cache/apt/archives/lsb-basee_4.0-0ubuntu0.9.04.1-all.
deb (--unpack):
 trying to overwrite `/etc/lsb-base-logging.sh`, which is also in package splash
y
Errors were encountered while processing:
 /var/cache/apt/archives/lsb-base_4.0-0ubuntu0.9.04.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install. Trying to recover:
```

I hade to copy all that by hand, so there might be a typo.

Please help!

---

### Post by Soul-Sing on 2009-07-06
try: ```
sudo apt-get -f install
``` to force an install of the file(s) that didn't get loaded because of the error. Then try: ```
sudo apt-get upgrade
``` again, and: ```
sudo apt-get -f install
```

---

### Post by GO%)$@*1 on 2009-07-07
> **leoquant said:**
> try: ```
sudo apt-get -f install
``` to force an install of the file(s) that didn't get loaded because of the error. Then try: ```
sudo apt-get upgrade
``` again, and: ```
sudo apt-get -f install
```
It worked! Thanks!

---

### Post by brnmcdnld720 on 2009-07-08
I had the same problem. None of that worked for me. I just un-checked the lsb-base update in the update manager and it updated  completely fine for me

---

### Post by GO%)$@*1 on 2009-07-09
That's weird...none of the updates would proceed on my computer.

If you can help me on other problems I have, that would be GREAT!

[http://ubuntuforums.org/showthread.php?t=1207067](http://ubuntuforums.org/showthread.php?t=1207067)

[http://ubuntuforums.org/showthread.php?t=1206972](http://ubuntuforums.org/showthread.php?t=1206972)

---

