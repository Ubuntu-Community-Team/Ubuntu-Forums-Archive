---
title: "ttf-mscorefonts-installer fix or workaround needed"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by crysis on 2009-11-01
i have just installed karmic 64bit without any problem. but am unable to install practically any software via synaptic. It seems that almost all software needs "**ttf-mscorefonts-installer 3.0**". But it looks like this package failed to install everytime i try. Means i can't properly install any software i need via synaptic (including Wine, Restricted extras, Vlc,and many others) 

I get and error like this "**E: ttf-mscorefonts-installer: subprocess installed post-installation script returned error exit status 1**"

It looks like the server or links ttf-mscorefonts-installer tries to connect via internet is down or moved?

Please i need a fix/workaround to this problem ASAP. without this i'm stuck badly.

---

### Post by jjcv on 2009-11-01
> **crysis said:**
> I get and error like this "**E: ttf-mscorefonts-installer: subprocess installed post-installation script returned error exit status 1**"

It looks like the server or links ttf-mscorefonts-installer tries to connect via internet is down or moved?

Please i need a fix/workaround to this problem ASAP. without this i'm stuck badly.

Can you do this in a terminal"

sudo apt-get -f install

Then do a:

sudo apt-get install ttf-mscorefonts

If you get any errors cut and paste them into a message here.

---

### Post by crysis on 2009-11-02
well it looks like after a restart applications and codecs seem to work fine. the **ttf-mscorefonts-installer** installation is corrupt but not interfered with any applications.

it just that whenever i install any application apt tries to install **ttf-mscorefonts-installer** at some point and waste a lot of time. 

anyway here are the terminal output.


****@ubuntu:~$ **sudo apt-get -f install**
[sudo] password for ****: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up ttf-mscorefonts-installer (3.0) ...

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

--2009-11-02 23:14:51--  [http://downloads.sourceforge.net/corefonts/andale32.exe](http://downloads.sourceforge.net/corefonts/andale32.exe)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe](http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe) [following]
--2009-11-02 23:14:53--  [http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe](http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe)
Resolving nchc.dl.sourceforge.net... 211.79.60.17, 2001:e10:ffff:1f02::17
Connecting to nchc.dl.sourceforge.net|211.79.60.17|:80... failed: Connection timed out.
Connecting to nchc.dl.sourceforge.net|2001:e10:ffff:1f02::17|:80... failed: Network is unreachable.
--2009-11-02 23:14:58--  [http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
Resolving switch.dl.sourceforge.net... 130.59.138.21, 2001:620:0:1b::21
Connecting to switch.dl.sourceforge.net|130.59.138.21|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=switch.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=switch.dl.sourceforge.net) [following]
--2009-11-02 23:14:59--  [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=switch.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=switch.dl.sourceforge.net)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe](http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe) [following]
--2009-11-02 23:15:00--  [http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe](http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe)
Resolving nchc.dl.sourceforge.net... 211.79.60.17, 2001:e10:ffff:1f02::17
Connecting to nchc.dl.sourceforge.net|211.79.60.17|:80... failed: Connection timed out.
Connecting to nchc.dl.sourceforge.net|2001:e10:ffff:1f02::17|:80... failed: Network is unreachable.
--2009-11-02 23:15:05--  [http://mesh.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://mesh.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
Resolving mesh.dl.sourceforge.net... 213.203.218.122
Connecting to mesh.dl.sourceforge.net|213.203.218.122|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=mesh.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=mesh.dl.sourceforge.net) [following]
--2009-11-02 23:15:06--  [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=mesh.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=mesh.dl.sourceforge.net)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe](http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe) [following]
--2009-11-02 23:15:12--  [http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe](http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe)
Resolving nchc.dl.sourceforge.net... 211.79.60.17, 2001:e10:ffff:1f02::17
Connecting to nchc.dl.sourceforge.net|211.79.60.17|:80... failed: Connection timed out.
Connecting to nchc.dl.sourceforge.net|2001:e10:ffff:1f02::17|:80... failed: Network is unreachable.
--2009-11-02 23:15:18--  [http://dfn.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://dfn.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
Resolving dfn.dl.sourceforge.net... 194.95.236.6
Connecting to dfn.dl.sourceforge.net|194.95.236.6|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=dfn.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=dfn.dl.sourceforge.net) [following]
--2009-11-02 23:15:18--  [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=dfn.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=dfn.dl.sourceforge.net)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe](http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe) [following]
--2009-11-02 23:15:19--  [http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe](http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe)
Resolving nchc.dl.sourceforge.net... 211.79.60.17, 2001:e10:ffff:1f02::17
Connecting to nchc.dl.sourceforge.net|211.79.60.17|:80... failed: Connection timed out.
Connecting to nchc.dl.sourceforge.net|2001:e10:ffff:1f02::17|:80... failed: Network is unreachable.
--2009-11-02 23:15:24--  [http://heanet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://heanet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
Resolving heanet.dl.sourceforge.net... 193.1.193.66, 2001:770:18:aa40::c101:c142
Connecting to heanet.dl.sourceforge.net|193.1.193.66|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=heanet.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=heanet.dl.sourceforge.net) [following]
--2009-11-02 23:15:25--  [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=heanet.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=heanet.dl.sourceforge.net)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe](http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe) [following]
--2009-11-02 23:15:26--  [http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe](http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe)
Resolving nchc.dl.sourceforge.net... 211.79.60.17, 2001:e10:ffff:1f02::17
Connecting to nchc.dl.sourceforge.net|211.79.60.17|:80... failed: Connection timed out.
Connecting to nchc.dl.sourceforge.net|2001:e10:ffff:1f02::17|:80... failed: Network is unreachable.
--2009-11-02 23:15:31--  [http://jaist.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://jaist.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
Resolving jaist.dl.sourceforge.net... 150.65.7.130
Connecting to jaist.dl.sourceforge.net|150.65.7.130|:80... failed: Connection timed out.
Giving up.

--2009-11-02 23:15:36--  [http://nchc.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://nchc.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
Resolving nchc.dl.sourceforge.net... 211.79.60.17, 2001:e10:ffff:1f02::17
Connecting to nchc.dl.sourceforge.net|211.79.60.17|:80... failed: Connection timed out.
Connecting to nchc.dl.sourceforge.net|2001:e10:ffff:1f02::17|:80... failed: Network is unreachable.
--2009-11-02 23:15:41--  [http://ufpr.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://ufpr.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
Resolving ufpr.dl.sourceforge.net... 200.17.202.1, 200.236.31.1
Connecting to ufpr.dl.sourceforge.net|200.17.202.1|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=ufpr.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=ufpr.dl.sourceforge.net) [following]
--2009-11-02 23:15:43--  [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=ufpr.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=ufpr.dl.sourceforge.net)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe](http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe) [following]
--2009-11-02 23:15:45--  [http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe](http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe)
Resolving nchc.dl.sourceforge.net... 211.79.60.17, 2001:e10:ffff:1f02::17
Connecting to nchc.dl.sourceforge.net|211.79.60.17|:80... failed: Connection timed out.
Connecting to nchc.dl.sourceforge.net|2001:e10:ffff:1f02::17|:80... failed: Network is unreachable.
--2009-11-02 23:15:50--  [http://internode.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://internode.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
Resolving internode.dl.sourceforge.net... 150.101.135.12
Connecting to internode.dl.sourceforge.net|150.101.135.12|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=internode.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=internode.dl.sourceforge.net) [following]
--2009-11-02 23:15:51--  [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=internode.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=internode.dl.sourceforge.net)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe](http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe) [following]
--2009-11-02 23:15:55--  [http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe](http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe)
Resolving nchc.dl.sourceforge.net... 211.79.60.17, 2001:e10:ffff:1f02::17
Connecting to nchc.dl.sourceforge.net|211.79.60.17|:80... failed: Connection timed out.
Connecting to nchc.dl.sourceforge.net|2001:e10:ffff:1f02::17|:80... failed: Network is unreachable.
--2009-11-02 16:16:02--  [http://voxel.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://voxel.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
Resolving voxel.dl.sourceforge.net... 72.26.192.194
Connecting to voxel.dl.sourceforge.net|72.26.192.194|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=voxel.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=voxel.dl.sourceforge.net) [following]
--2009-11-02 16:16:04--  [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=voxel.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=voxel.dl.sourceforge.net)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe](http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe) [following]
--2009-11-02 16:16:05--  [http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe](http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe)
Resolving nchc.dl.sourceforge.net... 211.79.60.17, 2001:e10:ffff:1f02::17
Connecting to nchc.dl.sourceforge.net|211.79.60.17|:80... failed: Connection timed out.
Connecting to nchc.dl.sourceforge.net|2001:e10:ffff:1f02::17|:80... failed: Network is unreachable.
--2009-11-02 16:16:10--  [http://kent.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://kent.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
Resolving kent.dl.sourceforge.net... 212.219.56.167
Connecting to kent.dl.sourceforge.net|212.219.56.167|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=kent.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=kent.dl.sourceforge.net) [following]
--2009-11-02 16:16:11--  [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=kent.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=kent.dl.sourceforge.net)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe](http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe) [following]
--2009-11-02 16:16:17--  [http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe](http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe)
Resolving nchc.dl.sourceforge.net... 211.79.60.17, 2001:e10:ffff:1f02::17
Connecting to nchc.dl.sourceforge.net|211.79.60.17|:80... failed: Connection timed out.
Connecting to nchc.dl.sourceforge.net|2001:e10:ffff:1f02::17|:80... failed: Network is unreachable.
--2009-11-02 16:16:22--  [http://internap.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://internap.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
Resolving internap.dl.sourceforge.net... 64.7.222.131
Connecting to internap.dl.sourceforge.net|64.7.222.131|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: [http://prdownloads.sourceforge.net/corefonts/andale32.exe?download&failedmirror=internap.dl.sourceforge.net](http://prdownloads.sourceforge.net/corefonts/andale32.exe?download&failedmirror=internap.dl.sourceforge.net) [following]
--2009-11-02 16:16:24--  [http://prdownloads.sourceforge.net/corefonts/andale32.exe?download&failedmirror=internap.dl.sourceforge.net](http://prdownloads.sourceforge.net/corefonts/andale32.exe?download&failedmirror=internap.dl.sourceforge.net)
Resolving prdownloads.sourceforge.net... 216.34.181.59
Connecting to prdownloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe](http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe) [following]
--2009-11-02 16:16:25--  [http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe](http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe)
Resolving nchc.dl.sourceforge.net... 211.79.60.17, 2001:e10:ffff:1f02::17
Connecting to nchc.dl.sourceforge.net|211.79.60.17|:80... failed: Connection timed out.
Connecting to nchc.dl.sourceforge.net|2001:e10:ffff:1f02::17|:80... failed: Network is unreachable.
sha256sum: andale32.exe: No such file or directory
andale32.exe: FAILED open or read
sha256sum: WARNING: 1 of 1 listed file could not be read
Checksum mismatch for andale32.exe, aborting!
dpkg: error processing ttf-mscorefonts-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 ttf-mscorefonts-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by jjcv on 2009-11-02
> **crysis said:**
> 
Resolving prdownloads.sourceforge.net... 216.34.181.59
Connecting to prdownloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe](http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe) [following]
--2009-11-02 16:16:25--  [http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe](http://nchc.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe)
Resolving nchc.dl.sourceforge.net... 211.79.60.17, 2001:e10:ffff:1f02::17
Connecting to nchc.dl.sourceforge.net|211.79.60.17|:80... failed: Connection timed out.
Connecting to nchc.dl.sourceforge.net|2001:e10:ffff:1f02::17|:80... failed: Network is unreachable.
sha256sum: andale32.exe: No such file or directory
andale32.exe: FAILED open or read
sha256sum: WARNING: 1 of 1 listed file could not be read
Checksum mismatch for andale32.exe, aborting!
dpkg: error processing ttf-mscorefonts-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 ttf-mscorefonts-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)

The problem is that you are not able to get to nchc.dl.sourceforge.net and download **andale32.exe** a required parts for the installation to install ttf-mscorefonts.

Maybe it will resolve itself in a day or so.  Otherwise I would delete 

sudo apt-get remove ttf-mscorefonts

---

### Post by NovaSci on 2009-11-03
Had the same problem and after looking at a number of forums and the behavior during install it seems that the install script is accessing the wrong sourceforge address. I made the following changes to

/var/lib/dpkg/info/ttf-mscorefonts-installer.postinst

Add

MYURL="http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/"
MYMIRROR="?use_mirror=internode"

Just after

# Base URL for Microsoft fonts
# Can be more than one to try, but here we just use SF.net's redirection,
# which will work in most cases. The others serve as fallbacks to retry.

Then change (line 150 I believe) from

if ! wget --continue --tries=1 --dns-timeout=10 --connect-timeout=5 --read-timeout=300 $QUIET_ARG --directory-prefix . --no-directories --no-background $URLROOT$ff ; then

to

if ! wget --continue --tries=1 --dns-timeout=10 --connect-timeout=5 --read-timeout=300 $QUIET_ARG --directory-prefix . --no-directories --no-background $MYURL$ff$MYMIRROR ; then

Then go back to Synaptic and mark ttf-mscorefonts-installer for reinstallation. Click apply etc.

This worked for me. Although you might want to change the mirror.

Hope this is on some help

Regards

---

### Post by essius on 2009-11-04
> **NovaSci said:**
> 

/var/lib/dpkg/info/ttf-mscorefonts-installer.postinst



hey,
how do I open this as root so I can save the changes..?

Thanks

edit: After a cup of coffee my brain started to work again.
sudo gedit /var/lib/dpkg/info/ttf-mscorefonts-installer.postinst

---

### Post by NovaSci on 2009-11-04
> **essius said:**
> hey,
how do I open this as root so I can save the changes..?

Thanks

edit: After a cup of coffee my brain started to work again.
sudo gedit /var/lib/dpkg/info/ttf-mscorefonts-installer.postinst
From a command prompt / terminal and assuming gnome desktop (otherwise use editor of choice) use

sudo gedit  /var/lib/dpkg/info/ttf-mscorefonts-installer.postinst

You will of course need to enter the root password, but this will open the editor with root privileges (so be careful). This also assumes that you have tried and failed to install the  ttf-mscorefonts-installer and thus created the dpkg file.

Regards

Sorry - should have read to the bottom as you have already solved the problem

---

### Post by Zaq.Qwerty on 2009-11-05
Thank's NovaSci....
It works for me :lolflag:

Zaq

---

### Post by drpjkurian on 2009-11-15
> **NovaSci said:**
> From a command prompt / terminal and assuming gnome desktop (otherwise use editor of choice) use

sudo gedit  /var/lib/dpkg/info/ttf-mscorefonts-installer.postinst

You will of course need to enter the root password, but this will open the editor with root privileges (so be careful). This also assumes that you have tried and failed to install the  ttf-mscorefonts-installer and thus created the dpkg file.

Regards

Sorry - should have read to the bottom as you have already solved the problem



Hi Novasci

Well I did what you instructed, But it did not help me.

---

### Post by drpjkurian on 2009-11-15
Hi Guys

I have found the solution to this problem. Please visit the thread
[http://ubuntuforums.org/showthread.php?p=8322223&posted=1#post8322223](http://ubuntuforums.org/showthread.php?p=8322223&posted=1#post8322223)

With regards
Dr Kurian

---

### Post by kazuya on 2009-11-19
Thanks. Worked great for me. Time will tell. But thanks for linking guys.

---

