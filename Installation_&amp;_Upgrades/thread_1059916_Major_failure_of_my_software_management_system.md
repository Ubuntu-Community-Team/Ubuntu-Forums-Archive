---
title: "Major failure of my software management system"
date: 2009-02-04
forum: Installation &amp; Upgrades
---

### Post by Adam N on 2009-02-04
i am new to linux and ubuntu and when i try to add or remove programs it says that there has been a major failure of my software management system. Below is the full text that is shown.

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

I have run both of these commands in the terminal in the order that is shown and i end up with this;

 sudo apt-get update
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Sources
Reading package lists... Done
adam@@@@@@@@:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.27-7 linux-headers-2.6.27-7-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  openjdk-6-jre-headless
Suggested packages:
  sun-java6-fonts
The following NEW packages will be installed:
  openjdk-6-jre-headless
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
Need to get 0B/25.2MB of archives.
After this operation, 75.0MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 149336 files and directories currently installed.)
Unpacking openjdk-6-jre-headless (from .../openjdk-6-jre-headless_6b12-0ubuntu6.1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/openjdk-6-jre-headless_6b12-0ubuntu6.1_i386.deb (--unpack):
 failed in buffer_write(fd) (10, ret=-1): backend dpkg-deb during `./usr/lib/jvm/java-6-openjdk/jre/lib/rt.jar': No space left on device
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/openjdk-6-jre-headless_6b12-0ubuntu6.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

I have done as much a i can and i have no idea what to do next. Sorry about the wall of text. 

Thanks in advance Adam

**[COLOR="Red"]SOLVED[/COLOR]**

---

### Post by avtolle on 2009-02-04
Looking at the error message, it indicates that your partition is (nearly) full. From terminal, to check do```
df -h
``` and see what it returns. You might also try running, from terminal```
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove
```to clean out the cache and to remove the kernel packages that are no longer required. Then, try again. Good luck.

---

### Post by Adam N on 2009-02-04
Thank you avtolle

I tried df -h, then this text appeared;

 df -h
Filesystem            Size  Used Avail Use% Mounted on
[COLOR="Red"]/dev/sda1             3.5G  3.1G  310M  91% /[/COLOR]
tmpfs                1008M     0 1008M   0% /lib/init/rw
varrun               1008M  104K 1008M   1% /var/run
varlock              1008M  4.0K 1008M   1% /var/lock
udev                 1008M  2.8M 1006M   1% /dev
tmpfs                1008M  104K 1008M   1% /dev/shm
lrm                  1008M  2.0M 1007M   1% /lib/modules/2.6.27-11-generic/volatile
overflow              1.0M 1020K  4.0K 100% /tmp

I'm guessing that the update is trying to be installed here but there is only 400mb left.

I tried sudo apt-get autoremove. This text came up;

sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  ca-certificates-java: Depends: openjdk-6-jre-headless but it is not installed or
                                 cacao-oj6-jre-headless but it is not installed or
                                 sun-java6-jre-headless but it is not installable
  openjdk-6-jre: Depends: openjdk-6-jre-headless (>= 6b12-0ubuntu6.1) but it is not installed
                 Recommends: pulseaudio (>= 0.9.12) but 0.9.10-2ubuntu9.3 is installed
  openjdk-6-jre-lib: Depends: openjdk-6-jre-headless (>= 6b11) but it is not installed
  rhino: Depends: default-jre-headless but it is not installed or
                  java5-runtime-headless
E: Unmet dependencies. Try using -f.
 
From what i can gather i think that i need to install default-jre-headless or java5-runtime-headless, when i tried to install them using sudo get-apt install <package name> it didn't work.

I have  retried;

sudo apt-get update and
sudo apt-get install -f

this then prompted the terminal to do;

Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main openjdk-6-jre-headless 6b12-0ubuntu6.1 [25.2MB]
3% [1 openjdk-6-jre-headless 764262/25.2MB 3%]

It updated 

Fetched 25.2MB in 6min31s (64.2kB/s)                                                                                        
(Reading database ... 149336 files and directories currently installed.)
Unpacking openjdk-6-jre-headless (from .../openjdk-6-jre-headless_6b12-0ubuntu6.1_i386.deb) ...
Setting up openjdk-6-jre-lib (6b12-0ubuntu6.1) ...
Setting up libaccess-bridge-java (1.24.0-0ubuntu2) ...
Setting up openjdk-6-jre-headless (6b12-0ubuntu6.1) ...
Segmentation fault
dpkg: error processing openjdk-6-jre-headless (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ca-certificates-java:
 ca-certificates-java depends on openjdk-6-jre-headless | cacao-oj6-jre-headless | sun-java6-jre-headless; however:
  Package openjdk-6-jre-headless is not configured yet.
  Package cacao-oj6-jre-headless is not installed.
  Package sun-java6-jre-headless is not installed.
dpkg: error processing ca-certificates-java (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of rhino:
 rhino depends on default-jre-headless | java5-runtime-headless; however:
  Package default-jre-headless is not installed.
  Package java5-runtime-headless is not installed.
  Package openjdk-6-jre-headless which provides java5-runtime-headless is not configured yet.
dpkg: error processing rhino (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                       dpkg: dependency problems prevent configuration of openjdk-6-jre:
 openjdk-6-jre depends on openjdk-6-jre-headless (>= 6b12-0ubuntu6.1); however:
  Package openjdk-6-jre-headless is not configured yet.
dpkg: error processing openjdk-6-jre (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 openjdk-6-jre-headless
 ca-certificates-java
 rhino
 openjdk-6-jre
E: Sub-process /usr/bin/dpkg returned an error code (1)

Reading through the text it seems that openjdk-6-headless did not install or had an error code.

Is this a major problem and if so is there anyway to solve it? I can now open up add/remove programs now, Thank you avtolle.

---

### Post by avtolle on 2009-02-04
It looks like your /tmp is totally full, and that the /dev/sda1 is very close to being full. First, try ```
sudo apt-get clean
```to see if that can clear out the cache, and free up some room. After you run that command, do```
df -h
```to see if that gives you any more room. If it does, then try to install again. 

You may also want to take a look to see if you have any downloaded files around that you don't need any more, such as a d/l of a DVD, or an iso d/l, etc., that you haven't deleted, and try to delete these to free up some more space. Again, from what I can tell, the lack of space is the major problem you are having with trying to install your updates. Finally, you may have a bunch of stuff in the hidden trash files; I've never had this issue, but many others have, so you might want to do a forum search on this topic. Good luck once again.

---

### Post by Adam N on 2009-02-04
sudo apt-get clean

I have used this command. I have also typed in df -h but it has had no noticable difference. I have emptyed the trash bin, i have not had this laptop long so i have not had a chance to fill it up and i don't use it to download iso's. When i tried to update it again it failed to download the files [it could be my internet] It says;

W: Some index files failed to download, they have been ignored or old ones used instead.

I am not sure what to do, i will probably try to reinstall the update when i can get the internet working on my laptop again [I am on my desktop.

Thanks again Avtolle

---

### Post by Adam N on 2009-02-04
Is there anyway that i can update/check for updates by using the terminal

Thanks in advance Adam

---

### Post by dstew on 2009-02-04
Another think to think about, to free up space, is removing older kernels, if you have more than one (look at the opening grub menu). You can do this from Synaptic.

---

### Post by avtolle on 2009-02-04
> **Adam N said:**
> Is there anyway that i can update/check for updates by using the terminal

Thanks in advance Adam
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Adam N on 2009-02-04
> **dstew said:**
> Another think to think about, to free up space, is removing older kernels, if you have more than one (look at the opening grub menu). You can do this from Synaptic.

i haven't had my eeepc for long and i have just installed linux. will there be any other kernels?

Thank you dstew

---

### Post by Adam N on 2009-02-04
> **avtolle said:**
> ```
sudo apt-get update
sudo apt-get upgrade
```

Thanks avtolle. The problem has been rectified for now but my drive is still too full.

---

### Post by avtolle on 2009-02-04
There will likely be other kernels as security fixes are made.

---

### Post by Adam N on 2009-02-04
> **dstew said:**
> Another think to think about, to free up space, is removing older kernels, if you have more than one (look at the opening grub menu). You can do this from Synaptic.

Please can you explain what the synaptic is please and how to access/use it? From what i have gathered from some quick research i have found it is a type of package manager.

I have managed to free 50.02mb by getting rid of some linux headings.

Thanks in advance Adam

---

### Post by scratman on 2009-02-04
As has been established, it looks like you're getting really short on disk space.  There are things you can do to resolve this.  Have you tried reducing the amount of disk space reserved for your browser and Email software?  I'm sure you can set Firefox to clear it's history on shutdown, or at least reduce it's cache to 10Mb.  If you use an email client, would it be worth setting it up just to access your emails, but not download them.  Or better yet, remove the software and log in using the website?  That way, you've not got space taken up by emails, and you can claim back the disk space taken up by the software.

Have a look through the Applications menu, is there anything there you don't want/need.  If so, get rid of it, you can always reinstall it at a later date.

Have you cleared the hidden files out of the trash?  Open Trash and click View > Show Hidden Files.  If there are any you can bin, do so.

Also, go to Places > Search For Files.  Click "Select more options" and then select "Size is at least" type something like 5000kb.  This will find any files above 5Mb, ie, most of your MP3, Video files etc.  If there's anything you can bin, again, do so.  Are there files you need to keep, but access seldom?  If so, compress them by right clicking and selecting create archive.  Remember to delete or back-up the originals, however, or else you are just creating more data. 

Finally, for about £15, you can pick up a 16Gb memory stick from the likes of Play, Amazon, Maplin etc.  Might be worth using one of them to store all of your documents, and just have the software on the Asus machine.

Hope some of this is useful.  If you've any questions, please get in touch.

Oh, and synaptic package manager is a very sophisticated software installer.  It allows you to search any piece of software provided by Canonical, as well as a huge amount of software provided by third parties.  It also installs any libraries as required by the software you install.  It provides access to far more software than Add/Remove in the applications menu.  However, if you know the names of any packages you wish to install, then opening the terminal and typing sudo apt-get install [package name] this will provide a similar function, but using far less system resources.

---

### Post by Adam N on 2009-02-09
I have opened the GRUB menu and i have found that i have six different kernels, they are;

Ubuntu 8.10 kernel 2.6.27 11 generic
Ubuntu 8.10 kernel 2.6.27 11 generic (recovery mode)
Ubuntu 8.10 kernel 2.6.27 9 generic 
Ubuntu 8.10 kernel 2.6.27 9 generic (recovery mode)
Ubuntu 8.10 kernel 2.6.27 7 generic
Ubuntu 8.10 kernel 2.6.27 7 generic (recovery mode)

How do i delete the kernels that are no longer needed?

Thanks in advance Adam

---

### Post by dstew on 2009-02-10
If you can boot the system, go to System --> Administration --> Synaptic and search for the kernels in the installed programs. Select the 4 oldest ones and mark them for uninstallation. Then, click the Apply button, and they will be removed.

---

### Post by Adam N on 2009-02-22
thankyou. I have decided that the best way is to boot from my 8gb USB

---

### Post by scratman on 2009-02-28
How's that working out for you.  If it's all OK, could you please mark this thread as solved?

---

### Post by Adam N on 2009-03-12
yes i have solved the problem. sorry i have not replied recently i have been busy with work. the main problem was the lack o space on my asus Adam

---

### Post by Adam N on 2009-05-14
I have installed Ubuntu on the 16gb hdd and i am now using that, thankyou for all of your help :)

---

