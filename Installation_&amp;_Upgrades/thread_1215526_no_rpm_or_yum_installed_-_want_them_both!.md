---
title: "no rpm or yum installed - want them both!"
date: 2009-07-17
forum: Installation &amp; Upgrades
---

### Post by spxrs on 2009-07-17
Hi, I haven't got rpm or yum installed for some reason. I think I need rpm before I could get yum to work anyhow (?).  apt-get always fails to find rpm or yum.   The synaptic package manager fails too. I try downloading the tar.gz files but they always fail at the make stage. Is my only option to try and get hold of the installation disks again? Thanks for any help!

---

### Post by Partyboi2 on 2009-07-17
Hi, can you open a terminal and post the output please to
```
sudo apt-get update
sudo apt-get install yum rpm
```

---

### Post by irv on 2009-07-17
If you are trying to install rpm's in Ubuntu, you can convert them to deb files. This was posted in 2006 by Strabes:
convert rpm to deb
sudo apt-get install alien
sudo alien -i /path/to/file.rpm

Here is his blog: [http://strabes.wordpress.com/2006/11/17/installing-rpm-packages-in-ubuntu/]("http://strabes.wordpress.com/2006/11/17/installing-rpm-packages-in-ubuntu/")

---

### Post by spxrs on 2009-07-17
> **Partyboi2 said:**
> Hi, can you open a terminal and post the output please to
```
sudo apt-get update
sudo apt-get install yum rpm
```

 Hi, Thanks for quick reply- here's the output:   (16:48)tom@~/~> sudo apt-get update Password: Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg                      Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_GB           Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty Release.gpg                             Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/main Translation-en_GB                  Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_GB     Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_GB       Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_GB     Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release                          Get: 1 [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty Release.gpg [197B]                  Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Translation-en_GB                 Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/restricted Translation-en_GB            Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/universe Translation-en_GB    Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/multiverse Translation-en_GB  Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates Release.gpg           Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/main Translation-en_GB Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/restricted Translation-en_GB Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty Release                       Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages          Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty Release                      Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates Release               Err [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty Release                                   Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages              Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources                     Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources               Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages                Get: 2 [http://www.osrts.info](http://www.osrts.info) edgy Release.gpg [1979B]                           Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/main Packages                           Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/restricted Packages                     Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/main Sources                            Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/restricted Sources                      Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/universe Packages                       Get: 3 [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty Release [9324B]                     Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources                 Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages              Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources               Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/universe Sources                        Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/multiverse Packages                     Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/multiverse Sources                      Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages                      404 Not Found Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages                404 Not Found Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources                       404 Not Found Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/main Packages                   Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/restricted Packages             Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/main Sources                    Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/restricted Sources              Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/main Packages                             404 Not Found Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources                 404 Not Found Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty Release                                Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/restricted Packages                       404 Not Found Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/main Sources                    404 Not Found Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages                  404 Not Found Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources                   404 Not Found Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages                404 Not Found Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/restricted Sources                        404 Not Found Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/universe Packages                         404 Not Found Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/universe Sources                          404 Not Found Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/multiverse Packages                       404 Not Found Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/multiverse Sources                        404 Not Found Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/main Packages                     404 Not Found Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources                 404 Not Found Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/restricted Packages               404 Not Found Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/main Sources            404 Not Found Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Packages                Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/restricted Sources      404 Not Found Get: 4 [http://www.osrts.info](http://www.osrts.info) edgy/spring Translation-en_GB [2035B] 99% [4 Translation-en_GB bzip2 0] [Connecting to [www.osrts.info](www.osrts.info) (216.240.187.10bzip2: (stdin) is not a bzip2 file. Ign [http://www.osrts.info](http://www.osrts.info) edgy/spring Translation-en_GB                         Get: 5 [http://www.osrts.info](http://www.osrts.info) edgy Release [1995B]                               Ign [http://www.osrts.info](http://www.osrts.info) edgy Release Get: 6 [http://www.osrts.info](http://www.osrts.info) edgy/spring Packages [2037B] 88% [6 Packages bzip2 0]bzip2: (stdin) is not a bzip2 file. Err [http://www.osrts.info](http://www.osrts.info) edgy/spring Packages   Sub-process bzip2 returned an error code (2) Fetched 17.6kB in 2s (6437B/s) Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz)  404 Not Found Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz)  404 Not Found Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/source/Sources.gz)  404 Not Found Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/source/Sources.gz)  404 Not Found Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz)  404 Not Found Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz)  404 Not Found Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz)  404 Not Found Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz)  404 Not Found Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz)  404 Not Found Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz)  404 Not Found Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/source/Sources.gz)  404 Not Found Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz)  404 Not Found Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/source/Sources.gz)  404 Not Found Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz)  404 Not Found Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz)  404 Not Found Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz)  404 Not Found Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz)  404 Not Found Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz)  404 Not Found Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/source/Sources.gz)  404 Not Found Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/source/Sources.gz)  404 Not Found Failed to fetch [http://www.osrts.info/~tvo/deb/dists/edgy/spring/binary-i386/Packages.bz2](http://www.osrts.info/~tvo/deb/dists/edgy/spring/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2) Reading package lists... Done W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783 W: GPG error: [http://www.osrts.info](http://www.osrts.info) edgy Release: The following signatures were invalid: NODATA 1 NODATA 2 W: You may want to run apt-get update to correct these problems E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by spxrs on 2009-07-17
> **irv said:**
> If you are trying to install rpm's in Ubuntu, you can convert them to deb files. This was posted in 2006 by Strabes:
convert rpm to deb
sudo apt-get install alien
sudo alien -i /path/to/file.rpm

Here is his blog: [http://strabes.wordpress.com/2006/11/17/installing-rpm-packages-in-ubuntu/](http://strabes.wordpress.com/2006/11/17/installing-rpm-packages-in-ubuntu/)

 Hi, Thanks for quick response - unfortunately the apt-get for alien also fails. Here's the response (if you're still interested!):   Reading package lists... Done Building dependency tree        Reading state information... Done The following packages were automatically installed and are no longer required:   beryl-core beryl-settings-bindings libberylsettings0 beryl-settings   beryl-plugins libemeraldengine0 beryl-plugins-data libberyldecoration0 Use 'apt-get autoremove' to remove them. The following extra packages will be installed:   debhelper dpkg-dev gettext intltool-debian librpm4 po-debconf rpm Suggested packages:   lsb-rpm lintian dh-make debian-keyring cvs gettext-doc Recommended packages:   libmail-sendmail-perl libcompress-zlib-perl The following NEW packages will be installed   alien debhelper dpkg-dev gettext intltool-debian librpm4 po-debconf rpm 0 upgraded, 8 newly installed, 0 to remove and 118 not upgraded. Need to get 4020kB/4051kB of archives. After unpacking 15.0MB of additional disk space will be used. Do you want to continue [Y/n]? y WARNING: The following packages cannot be authenticated!   dpkg-dev gettext intltool-debian po-debconf debhelper librpm4 rpm alien Install these packages without verification [y/N]? y Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/main dpkg-dev 1.13.24ubuntu6   404 Not Found Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/main gettext 0.16.1-1ubuntu2   404 Not Found Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/main po-debconf 1.0.8   404 Not Found Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/main debhelper 5.0.42ubuntu1   404 Not Found Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/main librpm4 4.4.1-14build1   404 Not Found Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/main rpm 4.4.1-14build1   404 Not Found Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/main alien 8.65   404 Not Found Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg-dev_1.13.24ubuntu6_all.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg-dev_1.13.24ubuntu6_all.deb)  404 Not Found Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gettext/gettext_0.16.1-1ubuntu2_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gettext/gettext_0.16.1-1ubuntu2_i386.deb)  404 Not Found Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/p/po-debconf/po-debconf_1.0.8_all.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/p/po-debconf/po-debconf_1.0.8_all.deb)  404 Not Found Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/d/debhelper/debhelper_5.0.42ubuntu1_all.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/d/debhelper/debhelper_5.0.42ubuntu1_all.deb)  404 Not Found Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/r/rpm/librpm4_4.4.1-14build1_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/r/rpm/librpm4_4.4.1-14build1_i386.deb)  404 Not Found Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/r/rpm/rpm_4.4.1-14build1_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/r/rpm/rpm_4.4.1-14build1_i386.deb)  404 Not Found Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/a/alien/alien_8.65_all.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/a/alien/alien_8.65_all.deb)  404 Not Found E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

---

### Post by earthpigg on 2009-07-17
worst case scenario, you could always compile from source.... but before we get that far, can you please elaborate for us _why_ you want to be able to install yum and rpm packages? 

there may be a simple alternative method you can use to achieve the same ends.

focus on the goal, not the method! :D

---

### Post by Simian Man on 2009-07-17
From the error messages, it really looks like your apt is not working at all.  Do you have internet access?

While it's possible to use rpm/yum on Debian distors and possible to use dpkg/apt on Red Hat distros, it really isn't a good idea.  If you prefer rpm/yum (I do as well), why not use Fedora or CentOS instead?

Or are you wanting to install a specific rpm package?

---

### Post by spxrs on 2009-07-17
> **earthpigg said:**
> worst case scenario, you could always compile from source.... but before we get that far, can you please elaborate for us _why_ you want to be able to install yum and rpm packages? 

there may be a simple alternative method you can use to achieve the same ends.

focus on the goal, not the method! :D

 Well, in both cases they seem handy for downloading and installing linux progs. apt-get always seems to fail, and using the tar.gz file always fails for me at make stage. I'm told rpm files will kind of install themselves more or less, though I've never had an opportunity to try it myself! I'm also told yum is what I really want for this, but I think I need rpm to run yum....

---

### Post by spxrs on 2009-07-17
> **Simian Man said:**
> From the error messages, it really looks like your apt is not working at all.  Do you have internet access?

While it's possible to use rpm/yum on Debian distors and possible to use dpkg/apt on Red Hat distros, it really isn't a good idea.  If you prefer rpm/yum (I do as well), why not use Fedora or CentOS instead?

Or are you wanting to install a specific rpm package?

 Not really a specific rpm package. I've just heard yum is the way to go to find, and successfully install a lot of useful progs. And I've always had probs installing new progs I download. most recently yum, rpm, and ntfsprog.

---

### Post by drs305 on 2009-07-17
The error messages indicate the sources.list is for feisty, which is no longer supported. 

If you really need the feisty repositories, you can add those from old.releases:
[http://old-releases.ubuntu.com/releases/]("http://old-releases.ubuntu.com/releases/")

I would recommend a clean install of a current release, but if you prefer:

For End of Life Updates:
[https://help.ubuntu.com/community/EOLUpgrades]("https://help.ubuntu.com/community/EOLUpgrades")

---

### Post by Simian Man on 2009-07-17
> **spxrs said:**
> Not really a specific rpm package. I've just heard yum is the way to go to find, and successfully install a lot of useful progs. And I've always had probs installing new progs I download. most recently yum, rpm, and ntfsprog.

apt-get will be able to install way more software on Ubuntu than yum would.  That is because Ubuntu creates packages and repositories that apt-get can use to install software for you.  On the other hand very few Ubuntu users use yum, so there won't be much software available for it.

I personally like yum (on Fedora) better than apt, but not because it can install more software.  I'd recommend fixing your apt error and getting used to how to use that (and the synaptic GUI) to install software.

---

### Post by spxrs on 2009-07-17
> **drs305 said:**
> The error messages indicate the sources.list is for feisty, which is no longer supported. 

If you really need the feisty repositories, you can add those from old.releases:
[http://old-releases.ubuntu.com/releases/](http://old-releases.ubuntu.com/releases/)

I would recommend a clean install of a current release, but if you prefer:

For End of Life Updates:
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

 Yes, I am running feisty fawn. So you are recommending that I install a more up-to-date version: how about Jaunty Jackalope?

---

### Post by drs305 on 2009-07-17
> **spxrs said:**
> Yes, I am running feisty fawn. So you are recommending that I install a more up-to-date version: how about Jaunty Jackalope?

I have found Jaunty to be a very good release. It will be supported until Oct 2010. The current long term release, Hardy, will be supported until April 2011. 

 Because you are running Feisty, you would need to either do a clean install or commit to a long upgrade process. If desired to make the transition a bit easier, you could move your /home to a separate partition in an attempt to keep most of your configuration settings. You can also create a list of your currently installed applications so you can import them all from a list on your new installation.

There have been many improvements to Ubuntu since Feisty.

---

### Post by irv on 2009-07-17
Here is the download URL: [http://www.ubuntu.com/getubuntu/download]("http://www.ubuntu.com/getubuntu/download")
I would first download the iso file and burn a CD. It will create a live CD. Boot with the CD and run Ubuntu from the CD first. Make sure you can get on the Internet and then do the install. This can be done by clicking on the install icon on the desktop. Just follow the prompts and if you are doing a nice clean install you can just use the whole drive and it will set it up for you. If you are running a windows OS on this computer, you might want to do a dual boot. Then you would chose the second option on the partitions part of the install.
Once you have Ubuntu 9.04 installed you can ask for help by starting a new thread for each problem you are having or just to ask questions. As you can see there are a lot of us out here ready to help.
Enjoy one of the best OS's out here, IMO.
Irv

---

### Post by earthpigg on 2009-07-17
> **spxrs said:**
> Yes, I am running feisty fawn. So you are recommending that I install a more up-to-date version: how about Jaunty Jackalope?

that would be prudent, yes.

[http://www.ubuntu.com/GetUbuntu/download](http://www.ubuntu.com/GetUbuntu/download)
> 
Ubuntu 9.04 Desktop (the latest version): Includes the latest enhancements and is maintained until 2010

Ubuntu 8.04 LTS Desktop: Released April 2008 and maintained until April 2011 &#8211; ideal for large deployments

if you dont want to need to upgrade till 2011, go with 8.04.

if you'd rather have more up-to-date stuff, but need to upgrade in 2010, then 9.04.

9.04 came out in the 4th month of 2009. 8.04 came out in the 4th month of 2008. and so on.


by using a version that is still officially supported, you can install things from the official ubuntu servers and never need to worry about compatibility, etc.

---

