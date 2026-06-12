---
title: "How To Install Apt-Cacher-NG in Ubuntu Linux"
date: 2008-11-13
forum: General Help
---

### Post by docplastic on 2008-11-13
**The following procedure describes How To install the Apt-Cacher-NG package in Ubuntu Linux.**

(published at: [http://ubuntuforums.org/showthread.php?t=981085](http://ubuntuforums.org/showthread.php?t=981085))

Apt-Cacher-ng <http://www.unix-ag.uni-kl.de/~bloch/acng/> is a software package that keeps a cache on the disk, of Debian Packages and Release files.
When an apt-get issues a request for a file, Apt-Cacher intercepts it and if the file is already in the cache it serves it to the client immediately, otherwise it fetches the file from the Internet, saves it on disk, and then serves it to the client. This means that each package needs to be downloaded only once, in order to let several Debian machines to use it afterwards. 

Apt-Cacher-NG does not require an interpreter, nor a web server.
It does not: fork after server startup; create flag files; flock() files.
It uses native system functions (mmap, sendfile) to operate with few overhead.

**1. Install Apt-Cacher-NG on the server machine**
*1.1. Download & Install from Ubuntu pool*
sudo apt-get install apt-cacher-ng

**1.2 RECOMMENDED: build & install from latest sources**
sudo apt-get install libbz2-dev libfuse-dev # install support apps

# goto <http://ftp.debian.org/debian/pool/main/a/apt-cacher-ng/?C=M;O=D> and download the newest source:

cd $(mktemp -d) ; # create a temp dir and cd to it
wget [http://ftp.debian.org/debian/pool/main/a/apt-cacher-ng/apt-cacher-ng_0.4.6.orig.tar.gz](http://ftp.debian.org/debian/pool/main/a/apt-cacher-ng/apt-cacher-ng_0.4.6.orig.tar.gz)
# get the sources from the debian/ubuntu repositories
apt-get source apt-cacher-ng
cd $(ls -d apt-cacher-ng-*/)

# update package info to new version
(export DEBFULLNAME='dummy';export DEBEMAIL='dummy <dummy@example.com>';uupdate --upstream-version 0.4.6 ../apt-cacher-ng_0.4.6.orig.tar.gz)
cd ../"$(dpkg-parsechangelog | sed -n 's/^Source: //p')-0.4.6"

# customize maintainer data
grep '^Maintainer\|^Uploaders\|XSBC-Original-Maintainer' debian/control
sed -i '/^Maintainer/s/: .*/: dummy <dummy@example.com>/;/^Uploaders/s/: .*/: dummy <dummy@example.com>/;/XSBC-Original-Maintainer/d' debian/control;

# adjust runlevel arguments
sed -i 's/2 3 5/2 3 4 5/;s/0 6/0 1 6/' debian/apt-cacher-ng/etc/init.d/apt-cacher-ng # grep '2 3\|0 ' debian/apt-cacher-ng/etc/init.d/apt-cacher-ng
sed -i 's/2 3 5/2 3 4 5/;s/0 6/0 1 6/' debian/apt-cacher-ng.init # grep '2 3\|0 ' debian/apt-cacher-ng.init

# build the new package
(export DEBFULLNAME='dummy';export DEBEMAIL='dummy@example.com';debuild -i -us -uc);

cd .. ; cp -avf apt-cacher-ng*deb /home/ftp/it-sw-bin/
sudo apt-get purge libbz2-dev libfuse-dev # remove support apps

sudo dpkg -i apt-cacher-ng*deb && echo "apt-cacher-ng hold" | sudo dpkg --set-selections

**2. Configure (apply to server and each client machine)**
# search & replace 192.168.1.100 by the IP of the machine that will act as apt-cacher-ng server

# enable proxy usage by apt-get, aptitude, etc.
echo 'Acquire::http { Proxy "http://192.168.1.100:3142"; };' | sudo tee /etc/apt/apt.conf.d/01apt-cacher-ng-proxy

# enable proxy usage by Synaptic
sudo grep --color -i 'proxy' /root/.synaptic/synaptic.conf || sudo nano /root/.synaptic/synaptic.conf

# ...and overwrite the last line }; with: 
  useProxy "1";
  httpProxy "192.168.1.100";
  httpProxyPort "3142";
  ftpProxy "192.168.1.100";
  ftpProxyPort "3142";
  noProxy "";
};
sudo grep --color -i 'proxy' /root/.synaptic/synaptic.conf

# ...or enable proxy using the Synaptic GUI:
a) In Synaptic go to "Settings->Preferences->Network"
b) click "Manual Proxy Configuration"
c) enter:
	 HTTP Proxy:	192.168.1.100   3142
	 FTP Proxy:	192.168.1.100   3142
Click OK
Click Reload

sudo apt-get update # now update the apt-get system

**3. Import local .deb files**
test -x /var/cache/apt-cacher-ng/_import || sudo mkdir -p -m 2755 /var/cache/apt-cacher-ng/_import
sudo mv -uf /var/cache/apt/archives/*.deb /var/cache/apt-cacher-ng/_import/

sudo chown -R apt-cacher-ng.apt-cacher-ng /var/cache/apt-cacher-ng/_import

# start import at: <http://192.168.1.100:3142/acng-report.html?doImport=Start+Import#bottom>

# cleanup and update apt cache index files
sudo rm -fr \
/var/cache/apt-cacher-ng/_import \
/var/cache/apt/archives/*.deb \
/var/cache/apt/*cache.bin \
/var/lib/apt/lists/*Packages \
/var/lib/apt/lists/*Sources
sudo apt-get update

**4. To stop using the proxy**
# disable proxy usage
sudo rm /etc/apt/apt.conf.d/01apt-cacher-ng-proxy # by apt-get
sudo sed -i '/useProxy/s/1/0/' /root/.synaptic/synaptic.conf # by synaptic
sudo /etc/init.d/apt-cacher-ng stop # stop
sudo apt-get update
# do click Reload in the Synaptic GUI

# to completly remove the proxy from your system
#sudo apt-get purge apt-cacher-ng
#sudo rm -fr /var/cache/apt-cacher-ng

**5. Other: optional customizations**
# days before deleting unreferenced files
grep ExTreshold /etc/apt-cacher-ng/acng.conf
sudo sed -i 's/^ExTreshold:.*/ExTreshold: 15/' /etc/apt-cacher-ng/acng.conf

**6. Dashboard & manual**
# see the apt-cacher-ng dashboard at: <http://192.168.1.100:3142/acng-report.html>
# see apt-cacher-ng User Manual at: (right click at the link and open with your browser): <file:///usr/share/doc/apt-cacher-ng/html/index.html>
# Howtos: <http://www.unix-ag.uni-kl.de/~bloch/acng/html/howtos.html>
## -- END --

---

### Post by my_key on 2009-01-06
Thanks a lot! I've set it up on my slug (nslu2) running Debian Lenny. I've installed apt-cacher-ng from the repo's. It was already configured for Debian and Ubuntu, so from the server side this was plug 'n' play. For the clients I've used your settings. 

Apt-cacher-ng caches the repo's from the different versions of ubuntu quite nicely. It even nicely supports the different installs of intrepid in my home with different personal package archives (PPA, you know as in ppa.launchpad.net/*). 

Although the slug is a very slow machine (226 Mhz processor, 28 MB ram). I don't see any noticeable slowdown on htop.

I'm very impressed with this package and it will come in very handy since I live in Belgium, which has fair adsl speeds, but with stupidly low bandwidth flat-rates. And that is a nasty combination. 

The only bad thing about apt-cacher-ng is that the documentation tries to make everything look very difficult, but thanks to your help, it's not.

---

### Post by lord_alan on 2009-03-24
Thanks, that was clear and easy to follow.

And the cacher seems to be working fine ;-)

---

### Post by rozilla on 2009-04-03
what's the difference between apt-cacher and apt-cacher-ng? which one should i be installing?

---

### Post by docplastic on 2009-04-08
> **rozilla said:**
> what's the difference between apt-cacher and apt-cacher-ng? which one should i be installing?

You should use apt-cacher-ng as it is newer, faster, needs less resources and is better maintained.

M.

---

### Post by koshari on 2009-04-30
> 
echo 'Acquire::http { Proxy "http://localhost:3142"; };' | sudo tee /etc/apt/apt.conf.d/01proxy


so you run this on the client machines and thats it?

---

### Post by magicfab on 2009-05-02
Why "download the latest version" ? At least make it clear that requires manual updates/upgrades! apt-cacher-ng is already packaged in Ubuntu.

Step 3 also strikes me as unneeded.

---

### Post by reqlar on 2009-05-14
> **magicfab said:**
> Why "download the latest version" ? At least make it clear that requires manual updates/upgrades! apt-cacher-ng is already packaged in Ubuntu.

Step 3 also strikes me as unneeded.

Code for Step One:

> apt-get install apt-cacher-ngStep 3 is necessary in order to reload the repository indexes.  If you skip step 3, you will get an error when importing the local cache into apt-cacher-ng.

If you don't wish to use the GUI tools, then substitute the following code for Step 3:

> sudo apt-get updateAlso... I've tested **apt-cacher** and **apt-cacher-ng**...  I agree that **apt-cacher-ng** is SOOOO much faster!

):P  Enjoy!

---

### Post by expelledboy on 2009-06-13
Is it neccessary to add a proxy to synaptic? I assumed it used the proxy that you specified in apt.conf.d?

---

### Post by expelledboy on 2009-06-14
Also has anyone tried this offline?

I want to install a computer using net-boot-installer that fetches the pre-cached files from a server that is away from any sort of internet connection.

---

### Post by fourtyseven on 2009-07-07
To the OP, is all of what you said done on the server only? If so, what would need to be done on the client machines?
Also, can someone please explain the purpose of step 3?

---

### Post by expelledboy on 2009-07-08
> **fourtyseven said:**
> To the OP, is all of what you said done on the server only? If so, what would need to be done on the client machines?
Also, can someone please explain the purpose of step 3?

The described setup is to have a server-client running on the same machine. If you want to separate the two steps 2,3 and 4 are for the clients. Make sure you change all the references to localhost to the IP of the machine the proxy is installed on (the server).

Step 3 is to point synaptic to the proxy.. I dont think this is needed though?

---

### Post by blackxored on 2009-07-23
I got some problems with mapping for debian mirrors, when I need to pass debootstrap-mirror, to chroot envs, what URL you are pointing the mirror to, besides doing the proxy trick?

---

### Post by estebandid0 on 2009-10-27
Can someone explain me how to make it work on offline mode? or it does not work in offline mode?

I have a computer that does not have permanent internet because is at the mountains so I need that this works in offline mode so the rest of the computers from the school can get the updates

Thanks

---

### Post by docplastic on 2009-10-28
> **estebandid0 said:**
> Can someone explain me how to make it work on offline mode? or it does not work in offline mode?

As far as I know, it does not work in offline mode.

To work in offline mode, use google to search for: apt-zip, deb-downloader [http://www.deb-downloader.org/]("http://www.deb-downloader.org/"), or apt-offline

Or, even better, take a look here: [http://ubuntuforums.org/showthread.php?t=352460]("http://ubuntuforums.org/showthread.php?t=352460")

P.

---

### Post by ack.inc on 2009-11-16
Instead of enabling proxy via synaptic, i used apt-get update after creating the /etc/apt/apt.conf.d/02proxy file

Does this make a big difference? I'm getting the "no index files found" error on clicking the Start Import button.

Should I manually create the index files?(How can I do that?)



EDIT: the error disappeared once i set the host's synaptic proxy to localhost. Looks like the debs have all been imported! Thanks!

---

### Post by estebandid0 on 2009-11-16
Here is a good how to, it work to me very good, the only bad thing is does not work in offline mode

[http://www.ubuntugeek.com/apt-cacher-ng-http-download-proxy-for-software-packages.html](http://www.ubuntugeek.com/apt-cacher-ng-http-download-proxy-for-software-packages.html)

---

### Post by ack.inc on 2009-11-17
Is there a way to view detailed logs for apt-cacher-ng? I've been trying to find the log file for hours, with no joy.

Also, the acng-report.html has certain administrative functions that I don't want the average user to see/use.

Can one manually edit this page?

---

### Post by ack.inc on 2009-11-17
> **ack.inc said:**
> Is there a way to view detailed logs for apt-cacher-ng? I've been trying to find the log file for hours, with no joy.

Also, the acng-report.html has certain administrative functions that I don't want the average user to see/use.

Can one manually edit this page?

Actually, I'd rather there were a way to make it password-protected. What files do I need to look at?

Thanks for your time!

---

### Post by cong06 on 2010-02-17
Apt-cacher-ng has this option:
```

 61 # Days before considering an unreferenced file expired (to be deleted).
 62 # Warning: if the value is set too low and particular index files are not
 63 # available for some days (mirror downtime) there is a risk of deletion of
 64 # still usefull package files.
 65 ExTreshold: 4

```
Is there a way to disable it?
I was hoping something more like the feature in apt-cacher:
```

 62 # Apt-cacher can clean up its cache directory every 24 hours if you set
 63 # this directive to 1. Cleaning the cache can take some time to run
 64 # (generally in the order of a few minutes) and removes all package
 65 # files that are not mentioned in any existing 'Packages' lists. This
 66 # has the effect of deleting packages that have been superseded by an
 67 # updated 'Packages' list.
 68 clean_cache=1

```

---

### Post by davidshere on 2010-02-17
This tutorial seems much simpler:

[http://ubuntuforums.org/showthread.php?t=1327179](http://ubuntuforums.org/showthread.php?t=1327179)

---

### Post by carolineictwiki on 2010-03-22
When I follow the instructions, after step 2 I click 'Reload' in Synaptic GUI and it brings this error message:

[INDENT]Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/source/Sources.gz)  503  DNS error for hostname security.ubuntu.com: Name or service not known

[/INDENT]Trying to do $ sudo apt-get update results in the following

[INDENT]W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/binary-i386/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)

[/INDENT]I'm using a Squid proxy server - could this be interfering? 

Thanks!

-Caroline

---

### Post by docplastic on 2010-03-22
> **carolineictwiki said:**
> When I follow the instructions, after step 2 I click 'Reload' in Synaptic GUI and it brings this error message:

... 503 DNS error for hostname security.ubuntu.com ...

-Caroline

Try this:

1. Stop & flush Squid:
sudo /etc/init.d/squid stop
sudo rm -fr /var/spool/squid/*
sudo squid -z

2. Stop & flush apt-cacher-ng: 
sudo /etc/init.d/apt-cacher-ng stop
sudo rm -fr \
/var/cache/apt-cacher-ng/_import \
/var/cache/apt/archives/*.deb \
/var/cache/apt/*cache.bin \
/var/lib/apt/lists/*Packages \
/var/lib/apt/lists/*Sources

3. Start & test apt-cacher-ng
sudo /etc/init.d/apt-cacher-ng start
sudo aptitude update && sudo aptitude safe-upgrade

4. If it works as expected restart squid
sudo /etc/init.d/squid start

Note: this could also be related with <http://www.mail-archive.com/debian-bugs-closed@lists.debian.org/msg268705.html>, in which case you may need an upgrade to apt-cacher-ng_0.4.6-ubuntu1_i386.deb.

---

### Post by cong06 on 2010-03-22
> **carolineictwiki said:**
> 
```
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/binary-i386/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)
```

So you have requests going from squid to apt-cacher-ng? You have a local peer set up with squid?
```

# define the cache_peer
cache_peer localhost parent 3142 0 no-query proxy-only name=apt
# assign the cache_peer
cache_peer_access apt allow debian_index
cache_peer_access apt allow debian_package
cache_peer_access apt deny all
# never direct (ie don't cache) it's requests
never_direct allow debian_index
never_direct allow debian_package

```

---

### Post by carolineictwiki on 2010-03-23
DocPlastic: I followed your steps, but when I try to start it it returns a status of 'Fail'. It does allow me to 'restart' it. So it seems to be running...but it persists in the Synaptic error message, and the /acng-report.html shows a very tiny amount of data (see below) which doesn't seem right as I've been trying a number of downloads, none of which seem to be using the cache. 

How would I know what version I am using? It says in Syaptic, when I click on the apt-cacher-ng and choose properties that I'm using 0.4-1...
Period                Cache efficiency                                                           Requests                                 Data                                                           Hits                Misses                Total                                 Hits                Misses                Total                                       2010-03-22 03:38 - 2010-03-23 03:38 3739 (100.00%)0 (0.00%)3739 0.91 MiB (100.00%)0.00 MiB (0.00%)0.91 MiB2010-03-21 03:38 - 2010-03-22 03:38 1412 (100.00%)0 (0.00%)1412 0.34 MiB (100.00%)0.00 MiB (0.00%)0.34 MiB

---

### Post by carolineictwiki on 2010-03-23
So my 503 error is present for all my computers -and- the proxy server when trying to update, and a colleague is confirming, so it seems to be a bigger problem across Ghana right now.  Thanks for the help but I'll just have to wait for this to resolve!

++++++++++++++ In an unrelated question: ++++++++++++++++

In these and other instructions for apt-cacher-ng, I've noticed that sometimes you are directed to configure the apt-cacher-ng to
 
[INDENT]```
echo 'Acquire::http { Proxy "http://localhost:3142"; };' | sudo tee /etc/apt/apt.conf.d/01proxy 
```[/INDENT]
but I've also seen instructions to make the last file /02proxy or /01apt-cacher-ng-proxy.

Which one is correct? I suppose you have to use the same on all the clients and server?

---

### Post by cong06 on 2010-03-24
> **carolineictwiki said:**
> ```
echo 'Acquire::http { Proxy "http://localhost:3142"; };' | sudo tee /etc/apt/apt.conf.d/01proxy 
```
but I've also seen instructions to make the last file /02proxy or /01apt-cacher-ng-proxy.

Correct me if I'm wrong, but based off other ubuntu things that file name is split up with a number and name.
The number determines the order the files in /etc/apt/apt.conf.d/ are run, and the name is just a human description.

And based off the other files, I don't think it really matters much. You *probably* do it 99proxy if you wanted, but It makes sense that configuring the proxy *should* be one of the first steps...

Try a few different ones and see what happens! Let us know what you find. (or just pick one and stick to it... :P)

Note: if you're still worried, 01proxy works for me.

---

### Post by docplastic on 2010-03-24
> **carolineictwiki said:**
> 
...
but I've also seen instructions to make the last file /02proxy or /01apt-cacher-ng-proxy.
...
Which one is correct? I suppose you have to use the same on all the clients and server?

The first 2 digits (of that config file's name) give the order in which the config files are read inside the /etc/apt/apt.conf.d/ directory.
You will want the apt-cacher-ng file to be read early and, accordingly, you will be better naming it something like /01a...

The rest of the name doesn't matter.
The names do not need to be same in the clients and in the server.


P.

---

### Post by docplastic on 2010-03-24
01

---

### Post by docplastic on 2010-03-24
> **carolineictwiki said:**
> 
How would I know what version I am using? It says in Syaptic, when I click on the apt-cacher-ng and choose properties that I'm using 0.4-1...


That seems to be the standard Ubuntu 9.10 version. It is rather old by apt-cacher-ng standards! The current version is 0.4.6-

Try to build & install a new one from the latest sources. It is not as hard as it seems.


P.

---

### Post by sutch on 2010-05-13
I've run into some issues and ended up building apt-cacher-ng from source.  When attempting to use 'sudo apt-get update', I continue to see messages like:

[INDENT][FONT="Courier New"]Err [http://192.168.56.2](http://192.168.56.2) karmic-updates/multiverse Sources
  403  URL seems to be made for proxy but contains apt-cacher-ng port. Inconsistent apt configuration?[/FONT][/INDENT]

and like:

[INDENT][FONT="Courier New"]W: Failed to fetch [http://192.168.56.2:3142/us.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/source/Sources.gz](http://192.168.56.2:3142/us.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/source/Sources.gz)  403  URL seems to be made for proxy but contains apt-cacher-ng port. Inconsistent apt configuration?[/FONT][/INDENT]

I haven't gotten much troubleshooting information out of the logs on the server.  How can I track down where the problem is occurring?

---

### Post by sutch on 2010-05-14
> **sutch said:**
> I've run into some issues and ended up building apt-cacher-ng from source.  When attempting to use 'sudo apt-get update', I continue to see messages like:

[INDENT][FONT="Courier New"]Err [http://192.168.56.2](http://192.168.56.2) karmic-updates/multiverse Sources
  403  URL seems to be made for proxy but contains apt-cacher-ng port. Inconsistent apt configuration?[/FONT][/INDENT]

and like:

[INDENT][FONT="Courier New"]W: Failed to fetch [http://192.168.56.2:3142/us.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/source/Sources.gz](http://192.168.56.2:3142/us.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/source/Sources.gz)  403  URL seems to be made for proxy but contains apt-cacher-ng port. Inconsistent apt configuration?[/FONT][/INDENT]

I haven't gotten much troubleshooting information out of the logs on the server.  How can I track down where the problem is occurring?

Answering my own question...

It turns out that my kickstart configuration wrote the URLs for the Ubuntu repository to use the apt-cache-ng server AND it set the cache server in /etc/apt/apt.conf.d/01proxy, so some of the repository requests were being sent through the cache server using cache URLs.

---

### Post by ZioNemo on 2010-10-23
I installed apt-cacher-ng on Lucid using the repository.
Installation and importing my old .deb apparently worked fine, but synaptic says:

```
W: Impossibile recuperare http://it.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg  Impossibile connettersi a 192.168.1.2:3128 (192.168.1.2). - connect (111: Connessione rifiutata)
...

```
which is the Italian for:

```
W: Impossible to download http://it.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg  Impossible to connect to 192.168.1.2:3128 (192.168.1.2). - connect (111: Connection refused)

```
... or something similar.

This is repeated for all repositories with minimal variations.
What am I doing wrong?

---

### Post by Irregular Joe on 2010-10-23
ZioNemo: The default port that apt-cacher-ng listens on is 3142, not 3128. You can customize it on the server in the /etc/apt-cacher-ng/acng.conf file.  If you change that file, be certain to use 'sudo service apt-cacher-ng restart' to pick up the change on the server.

I hope that helps!

---

### Post by Urhixidur on 2011-02-15
**> 2. Configure (apply to server and each client machine)**
> # enable proxy usage by apt-get, aptitude, etc.
> echo 'Acquire::http { Proxy "http://192.168.1.100:3142"; };' | sudo tee /etc/apt/apt.conf.d/01apt-cacher-ng-proxy
> # using the Synaptic GUI:
> a) In Synaptic go to "Settings->Preferences->Network"
> b) click "Manual Proxy Configuration"
> c) enter:
> HTTP Proxy:    192.168.1.100   3142
> FTP Proxy:    192.168.1.100   3142
> Click OK
> Click Reload
>
> sudo aptitude update # now update the apt-get system

   Are we supposed to do the "echo 'Acquire..." as well as setting up the proxy in the Synaptic GUI, or is the latter operation redundant with the former?  The "or" in the text is not clear as to which previous clause it covers.

   Note that there is no "aptitude" on my sysytem, just "apt-get".
[B]
> 3. Import local .deb files[/B]
> test -x /var/cache/apt-cacher-ng/_import || sudo mkdir -p -m 2755 /var/cache/apt-cacher-ng/_import
> sudo mv -uf /var/cache/apt/archives/*.deb /var/cache/apt-cacher-ng/_import/
> sudo chown -R apt-cacher-ng.apt-cacher-ng /var/cache/apt-cacher-ng/_import
> # start import at: <http://192.168.1.100:3142/acng-report.html?doImport=Start+Import#bottom>
> # cleanup and update apt cache index files
>  sudo rm -fr \
>  /var/cache/apt-cacher-ng/_import \
>  /var/cache/apt/archives/*.deb \
>  /var/cache/apt/*cache.bin \
>  /var/lib/apt/lists/*Packages \
>  /var/lib/apt/lists/*Sources
>  sudo aptitude update

   Now I'm really confused.  My browser will NOT reach acng-report.html.  The connection waits forever.  (And yes, I'm using my machine's own IP, not 192.168.1.100 - I obtained it with ifconfig and checked it with ping)

   The "sudo rm -fr ..." command I did not run because it would completely wipe my cache, something I do not want.  It also seems dumb to rm /var/cache/apt/archives, since we've just mv'ed those files to /var/cache/apt-cacher-ng/_import.

   How do I get my browser to reach acng-report.html?

---

### Post by cong06 on 2011-02-15
> **Urhixidur said:**
> Are we supposed to do the "echo 'Acquire..." as well as setting up the proxy in the Synaptic GUI, or is the latter operation redundant with the former?  The "or" in the text is not clear as to which previous clause it covers.
If you set the proxy via commandline (/etc/apt/apt.conf.d) I know you only need to do it once.
However, seem to recall that Synaptic used a separate proxy for something. Perhaps if you set it via gui, then you also have to configure it for synaptic.

> **Urhixidur said:**
> Note that there is no "aptitude" on my sysytem, just "apt-get".
Either works.

> **Urhixidur said:**
> Now I'm really confused.  My browser will NOT reach acng-report.html.  The connection waits forever.  (And yes, I'm using my machine's own IP, not 192.168.1.100 - I obtained it with ifconfig and checked it with ping)

You're connecting to apt-cacher-ng on the machine you installed it on?
Go to:
[http://localhost:3142/acng-report.html](http://localhost:3142/acng-report.html)

> **Urhixidur said:**
> The "sudo rm -fr ..." command I did not run because it would completely wipe my cache, something I do not want.  It also seems dumb to rm /var/cache/apt/archives, since we've just mv'ed those files to /var/cache/apt-cacher-ng/_import.
Yeah, I agree. No reason to rm -rf. I would instead copy, and then if you want then cleared, run sudo apt-get autoclean.

---

### Post by docplastic on 2011-02-16
1. After successfully installing apt-cacher-ng and importing the /var/cache/apt/archives/*.deb files into apt-cacher-ng there will be no need whatsoever for any files both in /var/cache/apt-cacher-ng/_import/ and in /var/cache/apt/archives/*.deb

2. There will be instances were not following the stated rm -fr cleaning procedure will leave your system in an unusable state. I repeat: copy (or move) followed by autocleaning won't do the same as the stated rm -fr procedure.

3. Don't be so fast at calling dumb other people's work at trying to help other people, especially when:

"There are more things in heaven and earth, Horatio, Than are dreamt of in your philosophy.", Hamlet Act 1, scene 5, 159&#8211;167


P.

---

### Post by cong06 on 2011-02-16
> **docplastic said:**
> 1. After successfully installing apt-cacher-ng and importing the /var/cache/apt/archives/*.deb files into apt-cacher-ng there will be no need whatsoever for any files both in /var/cache/apt-cacher-ng/_import/ and in /var/cache/apt/archives/*.deb

True. However I try to stay away from "rm -rf" whenever possible because I have on many occasions accidentally mis-typed it.
Instead I prefer commands like 'rm *' while in the actual directory.
Especially if you copied from /var/cache/apt/archives/ there should be no folders that were copied that are of any consequence.
Also, as far as I know, apt-cacher-ng doesn't keep the files around after they're imported. It moves them (which is actually rather unfortunate for some of the things I try to do).

> **docplastic said:**
> 
2. There will be instances were not following the stated rm -fr cleaning procedure will leave your system in an unusable state. I repeat: copy (or move) followed by autocleaning won't do the same as the stated rm -fr procedure.
uh... Could you give an example? I can think of **no way** where refusing to "rm -rf" would leave the computer unstable.

> **docplastic said:**
> 
3. Don't be so fast at calling dumb other people's work at trying to help other people
I realize you can get offended when someone says it "seems dumb" but I prefer to think that we're all adults here and that the statement was reflecting a lack of understanding. Maybe it would be easiest if we all assume so, and you explain what you mean?

---

### Post by docplastic on 2011-02-17
> **cong06 said:**
> 
Also, as far as I know, apt-cacher-ng doesn't keep the files around after they're imported. It moves them (which is actually rather unfortunate for some of the things I try to do).

But it does. It even puts those .deb in directories just like a real Debian repository. Try: sudo find /var/cache/ -name "*.deb"

> **cong06 said:**
> 
uh... Could you give an example? I can think of **no way** where refusing to "rm -rf" would leave the computer unstable.

Hint: do sudo apt-clean (or autoclean) also remove lock files?

I am sure that, sooner or later, you will find the examples you are looking for...

---

### Post by cong06 on 2011-02-17
> **docplastic said:**
> But it does. It even puts those .deb in directories just like a real Debian repository. Try: sudo find /var/cache/ -name "*.deb"
Haha, No, I know how apt-cacher-ng works.
What I was refering to, is I wanted to import apt-cacher-ng files from one repository to another.
Eventually I decided that it made more sense to use rsync over ssh.


> **docplastic said:**
> 
Hint: do sudo apt-clean (or autoclean) also remove lock files?

I am sure that, sooner or later, you will find the examples you are looking for...

meh. I have no reason to prove for you that your reasoning is correct. For now I'll stick to my way of NOT using rm when I don't need to. If you feel you need to defend your theory, you can do that yourself ;).

---

### Post by bwakkie on 2011-02-28
I have Apt-cacher-NG running happily for a few mounth now. But I got a full disk so I decided to move the cache dir to a new disk.

new ext4 disk is mounted via fstab with commands:
UUID=49246007-b081-4a6d-b3e7-a2075358dd44 /home/extradisk/ ext4 noatime,data=writeback,barrier=0,nobh,errors=remount-ro

I created a new dir /home/extradisk/apt-cacher-ng and did the following commands:

stopped the ng server:
```
sudo /etc/init.d/apt-cacher-ng stop
```
then I moved all data:
```
mv /var/cache/apt-cacher-ng/* /home/extradisk/apt-cacher-ng
```

set the correct ownership etc:
```
sudo chown -R apt-cacher-ng:apt-cacher-ng /home/extradisk/apt-cacher-ng
sudo chmod -R 2755 /home/extradisk/apt-cacher-ng

```

point the config to the correct dir:
```
sudo vim /etc/apt-cacher-ng/acng.conf
```
and change the CacheDir: /home/extradisk/apt-cacher-ng


startup the server
```
sudo /etc/init.d/apt-cacher-ng start
```


happy installing,
cheers,

Bastiaan

---

