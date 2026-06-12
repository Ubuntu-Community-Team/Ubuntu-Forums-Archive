---
title: "ttf-mscorefonts-installer does not install (Mirrors down)"
date: 2009-10-02
forum: Installation &amp; Upgrades
---

### Post by &#1057;&#1090;&#1088;&#1072;&#1085;&#1085;&#1080;&#1082; on 2009-10-02
The mirror, which ttf-mscorefonts-installer uses are down, so it cannot update. Is there a way to change the mirror url? 

This is the output: 
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
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

--2009-10-02 16:42:44--  http://downloads.sourceforge.net/corefonts/andale32.exe
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://surfnet.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe [following]
--2009-10-02 16:42:45--  http://surfnet.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe
Resolving surfnet.dl.sourceforge.net... 32.1.6.32, 2001:620:0:1b::21
Connecting to surfnet.dl.sourceforge.net|32.1.6.32|:80... failed: Connection timed out.
Connecting to surfnet.dl.sourceforge.net|2001:620:0:1b::21|:80... failed: Network is unreachable.
--2009-10-02 16:42:50--  http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving switch.dl.sourceforge.net... 32.1.6.32, 2001:620:0:1b::21
Connecting to switch.dl.sourceforge.net|32.1.6.32|:80... failed: Connection timed out.
Connecting to switch.dl.sourceforge.net|2001:620:0:1b::21|:80... failed: Network is unreachable.
--2009-10-02 16:42:55--  http://mesh.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving mesh.dl.sourceforge.net... 213.203.218.122
Connecting to mesh.dl.sourceforge.net|213.203.218.122|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=mesh.dl.sourceforge.net [following]
--2009-10-02 16:42:55--  http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=mesh.dl.sourceforge.net
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://surfnet.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe [following]
--2009-10-02 16:42:56--  http://surfnet.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe
Resolving surfnet.dl.sourceforge.net... 32.1.6.32
Connecting to surfnet.dl.sourceforge.net|32.1.6.32|:80... failed: Connection timed out.
Giving up.

--2009-10-02 16:43:01--  http://dfn.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving dfn.dl.sourceforge.net... 194.95.236.6
Connecting to dfn.dl.sourceforge.net|194.95.236.6|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=dfn.dl.sourceforge.net [following]
--2009-10-02 16:43:13--  http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=dfn.dl.sourceforge.net
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://surfnet.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe [following]
--2009-10-02 16:43:13--  http://surfnet.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe
Resolving surfnet.dl.sourceforge.net... 32.1.6.32
Connecting to surfnet.dl.sourceforge.net|32.1.6.32|:80... failed: Connection timed out.
Giving up.

--2009-10-02 16:43:18--  http://heanet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving heanet.dl.sourceforge.net... 32.1.7.112, 2001:770:18:aa40::c101:c142
Connecting to heanet.dl.sourceforge.net|32.1.7.112|:80... failed: Connection timed out.
Connecting to heanet.dl.sourceforge.net|2001:770:18:aa40::c101:c142|:80... failed: Network is unreachable.
--2009-10-02 16:43:23--  http://jaist.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving jaist.dl.sourceforge.net... 150.65.7.130
Connecting to jaist.dl.sourceforge.net|150.65.7.130|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=jaist.dl.sourceforge.net [following]
--2009-10-02 16:43:24--  http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=jaist.dl.sourceforge.net
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://surfnet.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe [following]
--2009-10-02 16:43:25--  http://surfnet.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe
Resolving surfnet.dl.sourceforge.net... 32.1.6.32
Connecting to surfnet.dl.sourceforge.net|32.1.6.32|:80... failed: Connection timed out.
Giving up.

--2009-10-02 16:43:30--  http://nchc.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving nchc.dl.sourceforge.net... 32.1.14.16, 2001:e10:ffff:1f02::17
Connecting to nchc.dl.sourceforge.net|32.1.14.16|:80... failed: Connection timed out.
Connecting to nchc.dl.sourceforge.net|2001:e10:ffff:1f02::17|:80... failed: Network is unreachable.
--2009-10-02 16:43:35--  http://ufpr.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving ufpr.dl.sourceforge.net... 200.236.31.1, 200.17.202.1
Connecting to ufpr.dl.sourceforge.net|200.236.31.1|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=ufpr.dl.sourceforge.net [following]
--2009-10-02 16:43:38--  http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=ufpr.dl.sourceforge.net
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://surfnet.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe [following]
--2009-10-02 16:43:38--  http://surfnet.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe
Resolving surfnet.dl.sourceforge.net... 32.1.6.32
Connecting to surfnet.dl.sourceforge.net|32.1.6.32|:80... failed: Connection timed out.
Giving up.

--2009-10-02 16:43:43--  http://internode.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving internode.dl.sourceforge.net... 150.101.135.12
Connecting to internode.dl.sourceforge.net|150.101.135.12|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=internode.dl.sourceforge.net [following]
--2009-10-02 16:43:45--  http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=internode.dl.sourceforge.net
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://surfnet.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe [following]
--2009-10-02 16:43:45--  http://surfnet.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe
Resolving surfnet.dl.sourceforge.net... 32.1.6.32
Connecting to surfnet.dl.sourceforge.net|32.1.6.32|:80... failed: Connection timed out.
Giving up.

--2009-10-02 16:43:51--  http://voxel.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving voxel.dl.sourceforge.net... 208.122.31.3, 208.122.31.14, 208.122.31.27, ...
Connecting to voxel.dl.sourceforge.net|208.122.31.3|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=voxel.dl.sourceforge.net [following]
--2009-10-02 16:43:51--  http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=voxel.dl.sourceforge.net
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://surfnet.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe [following]
--2009-10-02 16:43:52--  http://surfnet.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe
Resolving surfnet.dl.sourceforge.net... 32.1.6.32
Connecting to surfnet.dl.sourceforge.net|32.1.6.32|:80... failed: Connection timed out.
Giving up.

--2009-10-02 16:43:57--  http://kent.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving kent.dl.sourceforge.net... 212.219.56.167
Connecting to kent.dl.sourceforge.net|212.219.56.167|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=kent.dl.sourceforge.net [following]
--2009-10-02 16:43:57--  http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=kent.dl.sourceforge.net
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://surfnet.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe [following]
--2009-10-02 16:43:57--  http://surfnet.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe
Resolving surfnet.dl.sourceforge.net... 32.1.6.32
Connecting to surfnet.dl.sourceforge.net|32.1.6.32|:80... failed: Connection timed out.
Giving up.

--2009-10-02 16:44:02--  http://internap.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving internap.dl.sourceforge.net... 69.88.152.3
Connecting to internap.dl.sourceforge.net|69.88.152.3|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: http://prdownloads.sourceforge.net/corefonts/andale32.exe?download&failedmirror=internap.dl.sourceforge.net [following]
--2009-10-02 16:44:03--  http://prdownloads.sourceforge.net/corefonts/andale32.exe?download&failedmirror=internap.dl.sourceforge.net
Resolving prdownloads.sourceforge.net... 216.34.181.59
Connecting to prdownloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://surfnet.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe [following]
--2009-10-02 16:44:04--  http://surfnet.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe
Resolving surfnet.dl.sourceforge.net... 32.1.6.32
Connecting to surfnet.dl.sourceforge.net|32.1.6.32|:80... failed: Connection timed out.
Giving up.

sha256sum: andale32.exe: No such file or directory
andale32.exe: FAILED open or read
sha256sum: WARNING: 1 of 1 listed file could not be read
Checksum mismatch for andale32.exe, aborting!
dpkg: error processing ttf-mscorefonts-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 ttf-mscorefonts-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by &#1057;&#1090;&#1088;&#1072;&#1085;&#1085;&#1080;&#1082; on 2009-10-02
Fixed by trying another ISP

---

### Post by ahmadz1991 on 2009-11-01
hello &#1057;&#1090;&#1088;&#1072;&#1085;&#1085;&#1080;&#1082;,, I have exactly the same problem right now,,, and it's turning my life into hell,,, i can't install any package,,, they all need mscorefonts

Anyway, u seem to have solved it,,
> **&#1057 said:**
> Fixed by trying another ISP

can u explain that please...

---

### Post by tjololo on 2009-11-04
I have the same problem. Would be nice if you could share your solution:)

---

