---
title: "dpkg: unrecoverable fatal error, aborting:"
date: 2009-08-05
forum: Installation &amp; Upgrades
---

### Post by gerryarmstrong on 2009-08-05
Guys I need some help...
This morning the Update Manager found some updates for me to install and I told it to go ahead and install them. One of the packages was adobe-flash that comes from the third party canonical servers and the update failed during that download due to loosing connection to the server for some reason.
Now when I attempt to do an upgrade I get the following message each time:

(Reading database ... dpkg: unrecoverable fatal error, aborting:
 unable to open files list file for package `libtheora0': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:

I went through the forum and did a number of things including moving the /var/dpkg/info directory and attempting to re-install the libtheora0 (sudo apt-get --reinstall install libtheora0) but it give me the same error each time.

I did the following as well with no errors reported:
sudo dpkg --configure -a
sudo apt-get autoclean
sudo apt-get clean

No luck, anytime I try to install anything now I get the same error. All other searching seems to point to re-installing the OS as the solution... I thought I had got away from that as a solution when I moved away from Windows! Any other suggestions will be greatly appreciated.

---

### Post by wojox on 2009-08-05
Try opening Synaptic
Click Custom Filters
Pick Broken

---

### Post by gerryarmstrong on 2009-08-05
Ok, I did that and then clicked on OK. Status bar at bottom is as follows:

26884 packages listed, 1504 installed, 0 broken. 20 to install/upgrade 0 to remove; 173 MB will be used

---

### Post by wojox on 2009-08-05
Did that resolve the issue?

---

### Post by gerryarmstrong on 2009-08-05
Sorry no, the problem is still the same. Any other suggestions welcomed!
I am hoping not to have to re-install to resolve this. :(

---

### Post by gerryarmstrong on 2009-08-13
Well I had to re-install Ubuntu to resolve this issue, nothing I tried worked.

---

### Post by gartss on 2010-10-22
Hi guys,

I know it is a pretty old post, but I get the solution, so if anybody also runs into that problem, he will get the solution too.

When the error appears, it is related with a certain package which info is corrupted in the dpkg database. In my situation, I get the following :

(Reading database ... 55%dpkg: unrecoverable fatal error, aborting:
 failed in buffer_read(fd): files list for package `kde-icons-oxygen': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)

So the solution is the following :

1. Go into the /var/lib/dpkg directory
2. Make a backup of the "status" file
3. Edit the "status" file
4. Search the package that gave the error
5. Just delete the lines from this package (but let all other lines that concern other packages even if they contains the broken package in their "Replaces" or "Depends" fields)

Personally, here are the lines that I deleted :

Package: kde-icons-oxygen
Status: purge ok installed
Priority: optional
Section: kde
Installed-Size: 42952
Maintainer: Kubuntu Developers <kubuntu-devel@lists.ubuntu.com>
Architecture: all
Source: oxygen-icons
Version: 4:4.3.5-0ubuntu1~karmic1
Replaces: dolphin (<< 4:4.1.86+svn902162), kdebase-data (<= 4:4.0.0-1), kmail (<< 4:4.3.2), libkdepim4 (<< 4:4.2.85), step (<< 4:4.3.0)
Suggests: kdebase (>= 4:4.1.0-1)
Description: Oxygen icon theme for KDE 4
 Oxygen is the standard icon theme for KDE 4.
Homepage: [http://www.kde.org/](http://www.kde.org/)
Original-Maintainer: Jonathan Riddell <jriddell@ubuntu.com>

6. Save changes in the "status" file
7. Run: sudo dpkg dpkg --configure -a
8. Force the reinstallation of missing dependencies (because now, there are some) : sudo apt-get -f install
I think that if the broken package does not depend on any other package (could be rare), just reinstall it : sudo apt-get install the_package
9. Everything is fine now :-) can update, upgrade, or install new packages !

Hope this will help someone !
Cheers,
Gartss

---

### Post by radarstreet on 2011-03-06
Thank you so much! This saved me from having to do a complete re-installation!

---

### Post by mustafa ibrahim on 2011-04-26
t@Mustafa-sr1:/home/mustafa# apt-get remove squid3
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
squid3
0 upgraded, 0 newly installed, 1 to remove and 96 not upgraded.
1 not fully installed or removed.
After this operation, 3,609kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 69462 files and directories currently installed.)
Removing squid3 ...
invoke-rc.d: unknown initscript, /etc/init.d/squid3 not found.
dpkg: error processing squid3 (--remove):
subprocess installed pre-removal script returned error exit status 100
update-rc.d: /etc/init.d/squid3: file does not exist
dpkg: error while cleaning up:
subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
squid3
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@Mustafa-sr1:/home/mustafa# apt-get purge squid3
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
squid3*
0 upgraded, 0 newly installed, 1 to remove and 96 not upgraded.
1 not fully installed or removed.
After this operation, 3,609kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 69462 files and directories currently installed.)
Removing squid3 ...
invoke-rc.d: unknown initscript, /etc/init.d/squid3 not found.
dpkg: error processing squid3 (--purge):
subprocess installed pre-removal script returned error exit status 100
update-rc.d: /etc/init.d/squid3: file does not exist
dpkg: error while cleaning up:
subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
squid3
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@Mustafa-sr1:/home/mustafa# rm -R /pathtofolder
rm: cannot remove `/pathtofolder': No such file or directory
root@Mustafa-sr1:/home/mustafa# rm- R/etc/squid
No command 'rm-' found, did you mean:
Command 'rmt' from package 'tar' (main)
Command 'rmt' from package 'dump' (universe)
Command 'rmf' from package 'nmh' (universe)
Command 'rmf' from package 'mailutils-mh' (universe)
Command 'rme' from package 'pvm-examples' (universe)
Command 'rmm' from package 'nmh' (universe)
Command 'rmm' from package 'mailutils-mh' (universe)
Command 'rm' from package 'coreutils' (main)
Command 'rm' from package 'safe-rm' (universe)
rm-: command not found
root@Mustafa-sr1:/home/mustafa# apt-get -R /pathtofolder
E: Command line option 'R' [from -R] is not known.
root@Mustafa-sr1:/home/mustafa# aptitude install squid3
The following partially installed packages will be configured:
squid3
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 96 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Setting up squid3 (3.1.6-1.1ubuntu1.1) ...
/var/lib/dpkg/info/squid3.postinst: 70: cannot open /etc/squid3/squid.conf: No s uch file
dpkg: error processing squid3 (--configure):
subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
squid3
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install. Trying to recover:

root@Mustafa-sr1:/home/mustafa# /var/mustafa/dpkg/info
bash: /var/mustafa/dpkg/info: No such file or directory
root@Mustafa-sr1:/home/mustafa# rm -rf squid*
root@Mustafa-sr1:/home/mustafa# rm -rf squid*
root@Mustafa-sr1:/home/mustafa# rm -rf squid*
root@Mustafa-sr1:/home/mustafa# apt-get install squid
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
squid-common
Suggested packages:
squid-cgi logcheck-database resolvconf
The following NEW packages will be installed:
squid squid-common
0 upgraded, 2 newly installed, 0 to remove and 96 not upgraded.
1 not fully installed or removed.
Need to get 0B/1,119kB of archives.
After this operation, 2,572kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
dpkg: unrecoverable fatal error, aborting:
statoverride file contains empty line
E: Sub-process /usr/bin/dpkg returned an error code (2)
root@Mustafa-sr1:/home/mustafa#

---

### Post by mustafa ibrahim on 2011-04-26
my problem here please help

[http://ubuntuforums.org/showthread.php?t=1739826](http://ubuntuforums.org/showthread.php?t=1739826)

---

### Post by mustafa ibrahim on 2011-04-26
so what i do now?



root@Mustafa-sr1:/home/mustafa# dpkg dpkg --configure -a
dpkg: need an action option

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;

Options marked [*] produce a lot of output - pipe it through `less' or `more' !

---

### Post by mediator on 2011-05-01
there was a typo in the above command, what worked for me is:
dpkg --configure -a

so remove 1 dpkg

ps. gartss, ty for psoting the solution, that saved me

---

### Post by amitlinux on 2011-11-20
THANKS SO MUCH, I was going to have to reinstall, but this worked liked a charm. again the command is dpkg --configure -a (only 1 dpkg)
What a relief

---

### Post by kurtkraut on 2012-08-23
> **gartss said:**
> Hi guys,

I know it is a pretty old post, but I get the solution, so if anybody also runs into that problem, he will get the solution too.



This happened to my main server today and I was pulling the hair out of my head in your detailed process fixed the issue very quickly. I'd like to enforce to people like me that found this old post that this works.

---

