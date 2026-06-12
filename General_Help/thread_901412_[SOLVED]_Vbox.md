---
title: "[SOLVED] Vbox?"
date: 2008-08-26
forum: General Help
---

### Post by Yezinki on 2008-08-26
Hi there,

I downloaded the vbox, but how do I install it?

Thanks in advance!

---

### Post by Titan8990 on 2008-08-26
Vbox short for virtualbox?

---

### Post by Yezinki on 2008-08-26
[https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewFilteredProducts-SingleVariationTypeFilter;pgid=01RgaHqkAdxSR0EUQncsoQ3D00008Wk4P0rM;sid=nYEzWPeOqOMzWb86t1p7XRgpv8ujhjrLyGP8meqQUjtG0Q==](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewFilteredProducts-SingleVariationTypeFilter;pgid=01RgaHqkAdxSR0EUQncsoQ3D00008Wk4P0rM;sid=nYEzWPeOqOMzWb86t1p7XRgpv8ujhjrLyGP8meqQUjtG0Q==)

---

### Post by Yezinki on 2008-08-26
Yes,

---

### Post by tuxxy on 2008-08-26
Heres a guide to installing and setting up a virtual drive

[https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

---

### Post by Yezinki on 2008-08-26
I get this after the first command to install Virtualbox

ubuntu@ubuntu-laptop:~$ sudo apt-get install virtualbox-ose virtualbox-ose-source virtualbox-ose-modules-generic[sudo] password for ubuntu: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  virtualbox-ose-modules-generic: Depends: virtualbox-ose-modules-2.6.24-20-generic but it is not going to be installed
E: Broken packages
ubuntu@ubuntu-laptop:~$ 
ubuntu@ubuntu-laptop:~$ 
ubuntu@ubuntu-laptop:~$ 
ubuntu@ubuntu-laptop:~$ 
ubuntu@ubuntu-laptop:~$ 
ubuntu@ubuntu-laptop:~$ 
ubuntu@ubuntu-laptop:~$ 
ubuntu@ubuntu-laptop:~$ 
ubuntu@ubuntu-laptop:~$ 
ubuntu@ubuntu-laptop:~$ 
ubuntu@ubuntu-laptop:~$

---

### Post by WRDN on 2008-08-26
First run:

```
sudo apt-get install virtualbox-ose-modules-2.6.24-20-generic
```

Now, try to install Virtual Box again.

Alternatively, you can install it through Synaptic, and any unmet dependencies will be solved automatically.

---

### Post by Yezinki on 2008-08-26
Still the  same..



ubuntu@ubuntu-laptop:~$ sudo apt-get install virtualbox-ose-modules-2.6.24-20-generic
[sudo] password for ubuntu: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  virtualbox-ose-modules-2.6.24-20-generic: Depends: linux-image-2.6.24-20-generic but it is not installable
E: Broken packages
ubuntu@ubuntu-laptop:~$ 
ubuntu@ubuntu-laptop:~$

---

### Post by p_quarles on 2008-08-26
Try instead:
```
sudo apt-get install virtualbox-ose-modules-`uname -r`
```

---

### Post by Yezinki on 2008-08-26
Still at square 1........


ubuntu@ubuntu-laptop:~$ sudo apt-get install virtualbox - ose modules- ubuntu -r
[sudo] password for ubuntu: 
E: Command line option 'r' [from -r] is not known.
ubuntu@ubuntu-laptop:~$ 
ubuntu@ubuntu-laptop:~$

---

### Post by p_quarles on 2008-08-26
> **Yezinki said:**
> Still at square 1........


ubuntu@ubuntu-laptop:~$ sudo apt-get install virtualbox - ose modules- ubuntu -r
[sudo] password for ubuntu: 
E: Command line option 'r' [from -r] is not known.
ubuntu@ubuntu-laptop:~$ 
ubuntu@ubuntu-laptop:~$
Copy the command from my post exactly. What you entered isn't even close.

---

### Post by Yezinki on 2008-08-26
ubuntu@ubuntu-laptop:~$ sudo apt-get install virtualbox-ose-modules-ubuntu -r
E: Command line option 'r' [from -r] is not known.
ubuntu@ubuntu-laptop:~$ 
ubuntu@ubuntu-laptop:~$

---

### Post by Yezinki on 2008-08-26
Doesn't accept -r

ubuntu@ubuntu-laptop:~$ sudo apt-get install virtualbox-ose-modules- ubuntu -r
E: Command line option 'r' [from -r] is not known.
ubuntu@ubuntu-laptop:~$ 
ubuntu@ubuntu-laptop:~$ 
ubuntu@ubuntu-laptop:~$

---

### Post by p_quarles on 2008-08-26
Nor should it. You are not typing the command I gave you. 

It's simple. Please: just copy and paste the command I actually wrote.

---

### Post by Joeb454 on 2008-08-26
Please note that the `uname -r` part doesn't mean to type your username.

Literally enter ```
`uname -r`
``` where it states

---

### Post by Yezinki on 2008-08-26
Sorry I apologize the resolution is too low 1900x1200



ubuntu@ubuntu-laptop:~$ sudo apt-get install virtualbox-ose-modules-`uname -r`
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Recommended packages:
  virtualbox-ose
The following NEW packages will be installed:
  virtualbox-ose-modules-2.6.24-19-generic
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 327kB of archives.
After this operation, 918kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe virtualbox-ose-modules-2.6.24-19-generic 24.0.4 [327kB]
Fetched 327kB in 4s (67.2kB/s)                                   
Selecting previously deselected package virtualbox-ose-modules-2.6.24-19-generic.
(Reading database ... 95914 files and directories currently installed.)
Unpacking virtualbox-ose-modules-2.6.24-19-generic (from .../virtualbox-ose-modules-2.6.24-19-generic_24.0.4_i386.deb) ...
Setting up virtualbox-ose-modules-2.6.24-19-generic (24.0.4) ...

ubuntu@ubuntu-laptop:~$ 
ubuntu@ubuntu-laptop:~$ 



How do I start to work?

Thanks!

---

### Post by p_quarles on 2008-08-26
Now, run this:
```
sudo adduser `whoami` vboxusers
```
And then restart your session (log out, log back in).

Assuming everything else works, you'll now be able to run Virtualbox.

---

### Post by Yezinki on 2008-08-26
I did log out & in,..........but where is the Virtual box located?

Regards!

---

### Post by Yezinki on 2008-08-26
> **p_quarles said:**
> Now, run this:
```
sudo adduser `whoami` vboxusers
```
And then restart your session (log out, log back in).

Assuming everything else works, you'll now be able to run Virtualbox.

ubuntu@ubuntu-laptop:~$ sudo adduser `whoami` vboxusers
adduser: The group `vboxusers' does not exist.
ubuntu@ubuntu-laptop:~$

---

### Post by Yezinki on 2008-08-27
> **p_quarles said:**
> Now, run this:
```
sudo adduser `whoami` vboxusers
```
And then restart your session (log out, log back in).

Assuming everything else works, you'll now be able to run Virtualbox.

Hi there, 

You guys haver eally been helpful in guiding me how to install vbox but it wont run ?

Even after the command & log off & log in?

How do I make it to run?

Thanks!

---

### Post by p_quarles on 2008-08-27
Can you post the output of the following two commands?
```
cat /etc/groups
```
and
```
virtualbox
```
Please wrap the input inside the forum [noparse]```

```[/noparse] tags so it's easier to read. :)

---

### Post by Yezinki on 2008-08-27
Hi again,

Supposedly if I run Vbox the version, I can have only 1 OS ie Ubuntu.
 
Only 3 partitions for it.....root swap, & home.

Using Vbox how can I run other distros or Vista for that matter?

I wont have to install them?

So what is the advantage of installing a vbox & its hard drive when one can make a simple dual boot of the 2 OSs, that one works on or likes?

I'm no PC software engineer to spend months checking  different flavors of Linux.

Do you thinks that either of my machines ie Sony Vaio VGC-LS1 or Dell XPS 1710 have enough hardware to handle vbox?


Kindly care to clarify these queries?

---

### Post by Yezinki on 2008-08-27
ubuntu@ubuntu-laptop:~$ cat /etc/groups
cat: /etc/groups: No such file or directory
ubuntu@ubuntu-laptop:~$ 
ubuntu@ubuntu-laptop:~$

---

### Post by Yezinki on 2008-08-27
ubuntu@ubuntu-laptop:~$ virtualbox
The program 'virtualbox' is currently not installed.  You can install it by typing:
sudo apt-get install virtualbox-ose
bash: virtualbox: command not found
ubuntu@ubuntu-laptop:~$ 
ubuntu@ubuntu-laptop:~$

---

### Post by p_quarles on 2008-08-27
> **Yezinki said:**
> ubuntu@ubuntu-laptop:~$ cat /etc/groups
cat: /etc/groups: No such file or directory
ubuntu@ubuntu-laptop:~$ 
ubuntu@ubuntu-laptop:~$
Sorry, should be :
```
cat /etc/group
```
(no 's')
> **Yezinki said:**
> ubuntu@ubuntu-laptop:~$ virtualbox
The program 'virtualbox' is currently not installed.  You can install it by typing:
sudo apt-get install virtualbox-ose
bash: virtualbox: command not found
ubuntu@ubuntu-laptop:~$ 
ubuntu@ubuntu-laptop:~$
Well, that's your problem then. 
```
sudo apt-get install virtualbox-ose
```

---

### Post by Yezinki on 2008-08-27
You have included 64 images in your message. You are limited to using 8 images so please go back and correct the problem and then continue again.

Images include use of smilies, the BB code [img] tag and HTML <img> tags. The use of these is all subject to them being enabled by the administrator.

Where do I post?........in paste bin??

---

### Post by p_quarles on 2008-08-27
Umm, what?

---

### Post by Yezinki on 2008-08-27
For the 1st command:

[http://pastebin.com/m13216702](http://pastebin.com/m13216702)

---

### Post by Yezinki on 2008-08-27
2nd command:

ubuntu@ubuntu-laptop:~$ sudo apt-get install virtualbox-ose
[sudo] password for ubuntu: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libaudio2 libqt3-mt libxalan110 libxerces27
Suggested packages:
  nas libqt3-mt-mysql libqt3-mt-odbc libqt3-mt-psql xalan bridge-utils
  virtualbox-ose-source
The following NEW packages will be installed:
  libaudio2 libqt3-mt libxalan110 libxerces27 virtualbox-ose
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 12.4MB of archives.
After this operation, 39.2MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main libaudio2 1.9.1-1 [79.2kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main libqt3-mt 3:3.3.8-b-0ubuntu3 [3299kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe libxerces27 2.7.0-5 [1390kB]                                                                                                                                                              
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe libxalan110 1.10-3.1 [1241kB]                                                                                                                                                             
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe virtualbox-ose 1.5.6-dfsg-6ubuntu1 [6366kB]                                                                                                                                               
Fetched 12.4MB in 7min36s (27.1kB/s)                                                                                                                                                                                                        
Preconfiguring packages ...
Selecting previously deselected package libaudio2.
(Reading database ... 95919 files and directories currently installed.)
Unpacking libaudio2 (from .../libaudio2_1.9.1-1_i386.deb) ...
Selecting previously deselected package libqt3-mt.
Unpacking libqt3-mt (from .../libqt3-mt_3%3a3.3.8-b-0ubuntu3_i386.deb) ...
Selecting previously deselected package libxerces27.
Unpacking libxerces27 (from .../libxerces27_2.7.0-5_i386.deb) ...
Selecting previously deselected package libxalan110.
Unpacking libxalan110 (from .../libxalan110_1.10-3.1_i386.deb) ...
Selecting previously deselected package virtualbox-ose.
Unpacking virtualbox-ose (from .../virtualbox-ose_1.5.6-dfsg-6ubuntu1_i386.deb) ...
Setting up libaudio2 (1.9.1-1) ...

Setting up libqt3-mt (3:3.3.8-b-0ubuntu3) ...

Setting up libxerces27 (2.7.0-5) ...

Setting up libxalan110 (1.10-3.1) ...

Setting up virtualbox-ose (1.5.6-dfsg-6ubuntu1) ...
 * Starting VirtualBox host networking...                                                                                                                                                                                             [ OK ] 
 * Starting VirtualBox kernel module vboxdrv                                                                                                                                                                                          [ OK ] 

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
ubuntu@ubuntu-laptop:~$ 
ubuntu@ubuntu-laptop:~$

---

### Post by kerry_s on 2008-08-27
```
sudo su
apt-get install linux-headers-`uname -r` && ln -sf /usr/src/linux-headers-`uname -r` /usr/src/linux
apt-get install libxalan110 libxerces27 build-essential 
```

go here:
[https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI)

in platform select your ubuntu version
then just double click on it

```
sudo gedit /etc/group

add yourself to the vboxusers:x:###:you
```

---

### Post by Yezinki on 2008-08-27
ubuntu@ubuntu-laptop:~$ sudo su
[sudo] password for ubuntu: 
root@ubuntu-laptop:/home/ubuntu# apt-get install linux-headers-`uname -r` && ln -sf /usr/src/linux-headers-`uname -r` /usr/src/linux
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.24-19-generic is already the newest version.
linux-headers-2.6.24-19-generic set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@ubuntu-laptop:/home/ubuntu# apt-get install libxalan110 libxerces27 build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libxalan110 is already the newest version.
libxalan110 set to manually installed.
libxerces27 is already the newest version.
libxerces27 set to manually installed.
The following extra packages will be installed:
  dpkg-dev g++ g++-4.2 libc6-dev libstdc++6-4.2-dev libtimedate-perl linux-libc-dev patch
Suggested packages:
  debian-keyring g++-multilib g++-4.2-multilib gcc-4.2-doc libstdc++6-4.2-dbg glibc-doc manpages-dev libstdc++6-4.2-doc diff-doc
The following NEW packages will be installed:
  build-essential dpkg-dev g++ g++-4.2 libc6-dev libstdc++6-4.2-dev libtimedate-perl linux-libc-dev patch
0 upgraded, 9 newly installed, 0 to remove and 0 not upgraded.
Need to get 8704kB of archives.
After this operation, 34.3MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main linux-libc-dev 2.6.24-19.41 [696kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main libc6-dev 2.7-10ubuntu3 [3344kB]                                                                                                                                                              
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main libstdc++6-4.2-dev 4.2.3-2ubuntu7 [1187kB]                                                                                                                                                    
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main g++-4.2 4.2.3-2ubuntu7 [2784kB]                                                                                                                                                               
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main g++ 4:4.2.3-1ubuntu6 [1440B]                                                                                                                                                          
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main libtimedate-perl 1.1600-9 [30.1kB]                                                                                                                                                            
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main patch 2.5.9-4 [95.6kB]                                                                                                                                                                        
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main dpkg-dev 1.14.16.6ubuntu4 [559kB]                                                                                                                                                     
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main build-essential 11.3ubuntu1 [7066B]                                                                                                                                                           
Fetched 8704kB in 6min53s (21.0kB/s)                                                                                                                                                                                                        
Selecting previously deselected package linux-libc-dev.
(Reading database ... 96536 files and directories currently installed.)
Unpacking linux-libc-dev (from .../linux-libc-dev_2.6.24-19.41_i386.deb) ...
Selecting previously deselected package libc6-dev.
Unpacking libc6-dev (from .../libc6-dev_2.7-10ubuntu3_i386.deb) ...
Selecting previously deselected package libstdc++6-4.2-dev.
Unpacking libstdc++6-4.2-dev (from .../libstdc++6-4.2-dev_4.2.3-2ubuntu7_i386.deb) ...
Selecting previously deselected package g++-4.2.
Unpacking g++-4.2 (from .../g++-4.2_4.2.3-2ubuntu7_i386.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4%3a4.2.3-1ubuntu6_i386.deb) ...
Selecting previously deselected package libtimedate-perl.
Unpacking libtimedate-perl (from .../libtimedate-perl_1.1600-9_all.deb) ...
Selecting previously deselected package patch.
Unpacking patch (from .../patch_2.5.9-4_i386.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.14.16.6ubuntu4_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.3ubuntu1_i386.deb) ...
Setting up linux-libc-dev (2.6.24-19.41) ...
Setting up libc6-dev (2.7-10ubuntu3) ...
Setting up libtimedate-perl (1.1600-9) ...
Setting up patch (2.5.9-4) ...
Setting up dpkg-dev (1.14.16.6ubuntu4) ...
Setting up libstdc++6-4.2-dev (4.2.3-2ubuntu7) ...
Setting up g++-4.2 (4.2.3-2ubuntu7) ...
Setting up g++ (4:4.2.3-1ubuntu6) ...

Setting up build-essential (11.3ubuntu1) ...
root@ubuntu-laptop:/home/ubuntu# 
root@ubuntu-laptop:/home/ubuntu# 

Now what the vbox is being downloaded??

---

### Post by Yezinki on 2008-08-27
hi ........getting this error

---

### Post by kerry_s on 2008-08-27
> **Yezinki said:**
> hi ........getting this error

don't open it from firefox, go to the location you downloaded it to and double click on it.

and after it installs, don't forget to add yourself to the vbox group.
then log out and back in, it will then be in your menu under system tools. see pic

---

### Post by Yezinki on 2008-08-27
> **kerry_s said:**
> don't open it from firefox, go to the location you downloaded it to and double click on it.

and after it installs, don't forget to add yourself to the vbox group.
then log out and back in, it will then be in your menu under system tools. see pic

Thanks........in which folder is the download??

---

### Post by kerry_s on 2008-08-27
> **Yezinki said:**
> Thanks........in which folder is the download??

huh, looking at your screenshot you got it just fine. now just grab some iso's and get busy. :lolflag:

i been playing with vbox all day, i just cleaned it out before i saw your post, been at distrowatch just downloading things to try. fixen to try antix

---

### Post by Yezinki on 2008-08-27
Thanks alot........how do I install OSs on Vbox?

---

### Post by Yezinki on 2008-08-27
got to make an ISO image of an OS like Vista to start...using iso magic??

---

### Post by kerry_s on 2008-08-27
> **Yezinki said:**
> got to make an ISO image of an OS like Vista to start...using iso magic??

no you just point at the iso in the cdrom section.

hold on i'm in vbox now, ill be back.

okay, let's do a little practice run, first grab a iso, lets do slitaz it small so fast to download:

[http://mirror.pimentvert.com/slitaz/iso/1.0/slitaz-1.0.iso](http://mirror.pimentvert.com/slitaz/iso/1.0/slitaz-1.0.iso)

once you have the iso, open virtual box, click new
click next
put a name: slitaz
pick how much memory you want to give
click new
i use dynamic for the hd
pick the size, i usually use 5gb
click finish
click next
click finish
click settings
click the cdrom
click mount
click iso
click the little folder
click add
browse to your iso
double click it
click select
now click ok
then click start

that's it should boot right up.

---

### Post by Elfy on 2008-08-27
You can do it 2 ways -

1 - download an iso and then burn as an iso/image and boot vbox with it. Obviously if you have an install disc like xp or vista then pop the disc in and set a new virtual machine up.

2 - download the iso and rather than burn it, vbox will run the iso as it is, set the cdrom to read the iso, start and it will boot the iso

---

### Post by Yezinki on 2008-08-27
Thanks for your refined tested comments!

Regards!

---

### Post by kerry_s on 2008-08-27
> **Yezinki said:**
> Thanks for your refined tested comments!

Regards!

i put the steps exactly as i did it. see post #38. good luck.

---

### Post by Yezinki on 2008-08-27
hi why am I gettin this??

---

### Post by Elfy on 2008-08-27
You've got to be in the vbox users group - p_quarles (I think) gave you the command earlier

---

### Post by kerry_s on 2008-08-27
> **Yezinki said:**
> hi why am I gettin this??

yep, you forgot to put yourself in the vbox group.

gksu gedit /etc/group

look at the bottom for something like this:

```
vboxusers:x:103:
```

(you might have a different number than mine)

add your name to the end:

```
vboxusers:x:103:you
```

log out and back in

---

### Post by Yezinki on 2008-08-27
ubuntu@ubuntu-laptop:~$ vboxusers:x:124:Yezinki
bash: vboxusers:x:124:Yezinki: command not found
ubuntu@ubuntu-laptop:~$

---

### Post by Elfy on 2008-08-27
you're user is ubuntu is it not? 

You have to edit the file - > gksu gedit /etc/group

look at the bottom for something like this:

add to the bottom

vboxusers:x:103:[COLOR="Red"]you[/COLOR] - change you to username

It's not a command to run in terminal

---

### Post by Yezinki on 2008-08-27
[http://pastebin.com/m37d894b9](http://pastebin.com/m37d894b9)


What do I do next?

Thanks!

---

### Post by kerry_s on 2008-08-27
> **Yezinki said:**
> [http://pastebin.com/m37d894b9](http://pastebin.com/m37d894b9)


What do I do next?

Thanks!

log out and back in, you should be good.

you might want to read the doc's at least once, there's a pdf in /usr/share/doc/virtualbox or you can just grab one straight from the site:
[http://www.virtualbox.org/wiki/End-user_documentation](http://www.virtualbox.org/wiki/End-user_documentation)

---

### Post by Yezinki on 2008-08-27
I did as you told..logged out & than In.........now what do I do....

Thanks!

---

### Post by Elfy on 2008-08-28
You really would gain from following kerry_s's tip :) 

It is fairly simple to use once you've had a quick look - but using the New button will start the process and if it all goes wrong just start again, it won't damage your ubuntu - apart from a spare virtual harddrive which can be dealt with easily enough.

---

### Post by kerry_s on 2008-08-28
> **forestpixie said:**
> You really would gain from following kerry_s's tip :) 

It is fairly simple to use once you've had a quick look - but using the New button will start the process and if it all goes wrong just start again, it won't damage your ubuntu - apart from a spare virtual harddrive which can be dealt with easily enough.

you know my mind, depends on how many pills i'm on at the time. :lolflag:

---

