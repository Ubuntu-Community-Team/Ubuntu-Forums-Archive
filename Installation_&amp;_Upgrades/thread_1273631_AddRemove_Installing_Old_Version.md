---
title: "Add/Remove Installing Old Version"
date: 2009-09-23
forum: Installation &amp; Upgrades
---

### Post by CodeLab on 2009-09-23
Hello There,
I Am Quite A Newbie To Ubuntu....
I Had Installed And Uninstalled Several Times, But Never Actually Used It
So This Time, Quite Determined, I Installed XUbuntu 9.04

When Using Add/Remove Utility To Add New Applications, Its Installing Older Versions..
For Ex. I Installed VLC From Add Remove, It Installed 0.9.9a
Whereas The Latest Version On Official Site Is 1.0.2

I Installed Virtual Box From Add/Remove, It Installed Version 2.0.4
Whereas On Official Site Latest Version Is 3.0.<something>

So Why Is It Installing Older Versions Of Programs And How Can I Tell It To Install Newer Versions Instead...

---

### Post by ajgreeny on 2009-09-23
The reason for this is that each version of ubuntu has a fixed version of each package (for most packages at least) and the way to get newer versions of vlc is to add a ppa the details of which are here [http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html).

For VirtualBox go to the VB website [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads) and download the closed source version 3.0.6.  The OS version from the repos is missing quite a few utilities which make it less useful.

If you do a forum search you will find out many other things that have alternate ways to install newer versions, but be warned, some of them may be more prone to problems and crash occasionally.

---

