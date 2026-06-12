---
title: "Symantec backup exec ralus solutioin"
date: 2009-09-04
forum: Installation &amp; Upgrades
---

### Post by emmaylots on 2009-09-04
INSTALLING RALUS (SYMANTEC BACKUP EXEC REMOTE AGENT FOR         LINUX) ON UBUNTU




STEP 1:

Download the RALUS components from: [http://esdownload.symantec.com/akdlm/CD/MTV/BEWS_11D.7170_LINUX-UNIX-MAC-NT4_AGENTS.2.tar.gz](http://esdownload.symantec.com/akdlm/CD/MTV/BEWS_11D.7170_LINUX-UNIX-MAC-NT4_AGENTS.2.tar.gz)

You may to login in with your Symantec Account.
Unzip the folder to a directory in your home director.
root@ubuntu:#: gzip &#8211;d  BEWS_11D.7170_LINUX-UNIX-MAC-NT4_AGENTS.2.tar.gz

Now untar the tarball archive using
root@ubuntu:#: tar &#8211;xvf  BEWS_11D.7170_LINUX-UNIX-MAC-NT4_AGENTS.2.tar

Giving you:
root@ubuntu#: ls
BEWS_11D.7170_LINUX-UNIX-MAC-NT4_AGENTS.2.tar  cdimg

Change directory to the cdimg folder

root@ubuntu#: cd cdimg
root@ubuntu#: ls
DOCS              installrams     pkgs            ramsinst.conf  uninstallralus      uninstallrams.pl
installralus      installrams.pl  RALUS64         RANT32NT4      uninstallralus.cmd  VxIF
installralus.cmd  messages        ralusinst.conf  scripts        uninstallralus.pl
installralus.pl   perl            RALUSx86        tools          uninstallrams

Change directory to the pkgs folder, this containing packages for different OS

root@ubuntu#: cd pkgs
root@ubuntu#: ls
AIX  Darwin  HPUX  Linux  SunOS
root@ubuntu#: cd Linux
root@ubuntu#: ls
ralusinst.conf  VRTSralus.tar.gz  VRTSvxmsa.tar.gz

Unzip and untar the two archives to give you:

root@ubuntu#: ls
VRTSralus-11.00.7170-0.i386.rpm VRTSvxmsa-4.4-021.i686.rpm

Copy both .rpm files to your home directory.

STEP 2:

We will now convert both files to .deb (debian packages)
First we need to install Alien and its dependencies and libstdc++5.
Alien is a package conversion tool that can convert between various Linux flavors and Solaris installers.
For example a rpm to a pkg file, a rpm to a deb file and vice versa.
First we install it using:

root@ubuntu#: apt-get install alien
The installer will prompt you that some dependencies will be installed and ask you to enter Y or N, enter Y and continue.
Now install libstdc++5
The Backup Exec package needs this to run.

root@ubuntu#: apt-get install libstdc++5
Complete the installation.

Now we are ready to convert the rpm packages to a debian package.

root@ubuntu#: alien &#8211;d &#8211;c (&#8220;c&#8221; informs Alien to execute scripts contained in the rpm package)

A debian package will be compiled in your home directory.


STEP 3:

The next step is to install the packages using dpkg

root@ubuntu#: dpkg &#8211;i vrtsralus_11.00.7170-1_i386.deb vrtsvxmsa_4.4-22_i386.deb

It will be installed under /opt folder. The folders created are: VRTS VRTSralus  VRTSvxms, all under /opt directory. 

A folder is also created under /etc. The folder is VRTSralus, this folder contains the config file &#8220;ralus.cfg&#8221; 
Here is a sample content of the file:
root@ubuntu:/etc/VRTSralus#: less ralus.cfg
Software\Symantec\Backup Exec For Windows\Backup Exec\Agent Browser\TcpIp\AdvertisementPort=6101
Software\Symantec\Backup Exec For Windows\Backup Exec\Debug\VXBSAlevel=5
Software\Symantec\Backup Exec For Windows\Backup Exec\Engine\Agents\Advertise All=1
Software\Symantec\Backup Exec For Windows\Backup Exec\Engine\Agents\Advertise Now=0
Software\Symantec\Backup Exec For Windows\Backup Exec\Engine\Agents\Advertised Name Ok List_1=ubuntu.testdomain.ng
Software\Symantec\Backup Exec For Windows\Backup Exec\Engine\Agents\Advertisement Purge=0
Software\Symantec\Backup Exec For Windows\Backup Exec\Engine\Agents\Advertising Disabled=0
Software\Symantec\Backup Exec For Windows\Backup Exec\Engine\Agents\Advertising Interval Minutes=10
Software\Symantec\Backup Exec For Windows\Backup Exec\Engine\Agents\Auto Discovery Enabled=1
Software\Symantec\Backup Exec For Windows\Backup Exec\Engine\Logging\RANT NDMP Debug Level=0
Software\Symantec\Backup Exec For Windows\Backup Exec\Engine\RALUS\Encoder=
Software\Symantec\Backup Exec For Windows\Backup Exec\Engine\RALUS\ShowTSAFS=
Software\Symantec\Backup Exec For Windows\Backup Exec\Engine\RALUS\SystemExclude1=/dev/*.*
Software\Symantec\Backup Exec For Windows\Backup Exec\Engine\RALUS\SystemExclude2=/proc/*.*
Software\Symantec\Backup Exec For Windows\Backup Exec\Engine\RALUS\SystemExclude3=/mnt/nss/pools/
Software\Symantec\Backup Exec For Windows\Backup Exec\Engine\RALUS\SystemExclude4=/mnt/nss/.pools/
Software\Symantec\Backup Exec For Windows\Backup Exec\Engine\RALUS\SystemExclude5=/sys/*.*
Software\Symantec\Backup Exec For Windows\Backup Exec\Engine\RALUS\SystemExclude6=/_admin/*.*
ralus.cfg (END)

I edited the file to reduce the Advertisement Interval minute to 10.

Also add this line to the config file to enable ralus detect the Backup Exec media server:
Software\Symantec\Backup Exec For Windows\Backup Exec\Engine\Agents\Agent Directory List 1=backupserver.domain.com


EDIT /etc/services file:

I also edited /etc/services file, and added:
 grfs               6101/tcp                         # Symantec Backup Exec Agent
Changed webmin to 10101, and instead added:
ndmp            10000/tcp                       # Network Data Management Protocol Veritas 
Backup Exec



EDIT /etc/modprobe to Disable IPv6:

Disable IPv6 as Backup Exec does not load properly when it is in use. Edit the file
"/etc/modprobe.d/aliases" and comment out the line "alias net-pf-10 ipv6". Then, edit the file
"/etc/modprobe.d/blacklist" and add the line "blacklist ipv6".


RESTART THE SERVER!



STEP 4:

Create a group called beoper:

root@ubuntu#: addgroup beoper

Now add the root user to this group:

root@ubuntu#:

adduser root beoper

You can now execute the startup script using:
root@ubuntu#: /opt/VRTSralus/bin/ VRTSralus.init start

You can also copy the file to /etc/init.d/
root@ubuntu#: cp /opt/VRTSralus/bin/ VRTSralus.init /etc/init.d/

So that you can start it from the /etc/init.d/folder.

To make it run as a service or at startup, you can easily edit the /etc/rc.local file and add the path to the script.
This will make sure it starts up at boot, and after all other services.
OR:
Preferably use Symlink to /etc/rc.X
root@ubuntu#: update-rc.d VRTSralus.init defaults

Check for errors at: 
root@ubuntu#: less /var/VRTSralus/beremote.service.log
or run: root@ubuntu#:  /opt/VRTSralus/bin/beremote --log-console

CHALLENGES:

a) The Symantec Backup Exec server was unable to detect RALUS. This will soon be resolved.
RESOLVED: 

I needed to add a line to the /etc/ralus.cfg. This will tell the agent the name of the Media server. Add the fully qualified host name.

b) Backup job wizard will require you to add a new account for the RALUS agent, make the account a restricted one. Preferably, add your default ubuntu sudo account to the beoper group, or enable root account. Then type in the log in details for the account of your choice.

c) After installation, I tried to start the ralus agent, but it failed. I later found out that libstdc++5 was not installed. The post I got this information from also contains this step, but I guessed I missed it, assuming that libstdc++5 was already installed. I had to install it then it worked.

---

### Post by ./redshift on 2009-09-10
Great writeup!  I have been meaning to install RALUS on one of my Ubuntu servers for awhile and finding this writeup prompted me to go ahead and do it.

I have a question, if you could help...  I have the agent installed and running, but I still cannot see it from the media server.  The media server is Backup Exec for Windows Servers 11d and I do have the RALUS serial number enabled in License Keys and Installations.

I am using a similar ralus.cfg to the one you posted in your thread, with the names changed to the hostnames of my Ubuntu server and BEWS media server, obviously.

Was there anything else you had to do to get the media server to "see" your remote Linux server?

Thanks,

---

### Post by emmaylots on 2009-09-14
> **./redshift said:**
> Great writeup!  I have been meaning to install RALUS on one of my Ubuntu servers for awhile and finding this writeup prompted me to go ahead and do it.

I have a question, if you could help...  I have the agent installed and running, but I still cannot see it from the media server.  The media server is Backup Exec for Windows Servers 11d and I do have the RALUS serial number enabled in License Keys and Installations.

I am using a similar ralus.cfg to the one you posted in your thread, with the names changed to the hostnames of my Ubuntu server and BEWS media server, obviously.

Was there anything else you had to do to get the media server to "see" your remote Linux server?

Thanks,



Hi Hi:

I guess you used the fqdn of the Backup server? Try and do an nslookup on your Linux server to see if it can resolve the fqdn to an IP address. If it doesn't you may need to add it to the hosts file or your dns server.

---

### Post by bighairbiggie on 2009-12-08
After a lot of debugging I found there is little that needs to be done to make the VRTSralus installer work properly on a Ubuntu 8 system.

The steps I did to allow VRTSralus to install (as root):

$ apt-get install rpm
$ cd /etc
$ ln -s . rc.d
$ cd /bin
$ ln -s /usr/bin/rpm .

Once you've done these steps, run the installer normally.

That should be all that's needed to make the installer "feel at home" (ie. like it's on a Red Hat system).  It worked on my system but I haven't tried on a pristine system.

John

---

### Post by Rubi1200 on 2011-11-11
Thread closed.

---

