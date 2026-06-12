---
title: "Sort tsclient applet list alphabetically - howto patch"
date: 2008-08-26
forum: General Help
---

### Post by AikenDrum on 2008-08-26
Hi folks, 

I found [this thread]("http://ubuntuforums.org/showthread.php?t=745924") in the archives which pointed me in the right direction,  and then did the following to get the patch running in ubuntu 8.04.

Download tsclient .150 source from [http://transact.dl.sourceforge.net/sourceforge/tsclient/tsclient-0.150.tar.gz](http://transact.dl.sourceforge.net/sourceforge/tsclient/tsclient-0.150.tar.gz)

Download sort-list.patch from [http://sourceforge.net/tracker/download.php?group_id=192483&atid=941576&file_id=261203&aid=1865995](http://sourceforge.net/tracker/download.php?group_id=192483&atid=941576&file_id=261203&aid=1865995)

place the sort-list.patch file and the tar.gz in a folder together,  then unpack the tar file with 'tar xzvf tsclient-0.150.tar.gz'

apply the patch to the source with 'patch -p0 <sort-list.patch'

change into the tsclient-0.150 folder,  and './configure'   this will likely error out with some dependencies - eg one of mine was "checking for PACKAGE... configure: error: Package requirements (libpanelapplet-2.0) were not met:

No package 'libpanelapplet-2.0' found"

so resolve these by installing the required libraries - I usually just search synaptic for them, or google the "no package ....." bit to find what someone else has done to resolve the dependency.  There's probably a much neater way of doing this,  but this works for me :)  in this case it's 'libpanelappletmm-2.6-dev'

once the configure goes through - 'make'

then 'sudo checkinstall -D make install'   (you might need to install checkinstall with apt-get first)   This will make a deb package if you fancy sharing one,  and will also install the application.

if you just want to install without the deb etc,  just 'sudo make install'

once it's installed,  I found that for Ubuntu you have to copy a few files around.   otherwise the tsclient-applet on the gnome panel won't start.

in the source folder where you compiled tsclient after the patch - locate the 'applet' folder,  and copy the 'tsclient-applet' file you find there to /usr/lib/tsclient/

killall gnome-panel to restart the gnome panel and see your clients listed alphabetically.

hurrah !

This was tested on 2.6.24-19-generic and 2.6.23-ultimate  (kernelcheck is excellent)

I hope that helps someone :)  I expect that patch will make it into the next release of tsclient anyhow.  Apologies in advance if this isn't the tidiest way to achieve this.

Cheers.

---

### Post by animefan on 2008-11-27
better approach, which produces an installable deb package:

as user:
apt-get source tsclient
apt-get build-dep tsclient
cd tsclient-0.150/debian/patches/
wget -O 28_sort-list.patch 'http://sourceforge.net/tracker/download.php?group_id=192483&atid=941576&file_id=261203&aid=1865995'
wget -O 29_sort-quick-connect.patch 'http://sourceforge.net/tracker/download.php?group_id=192483&atid=941576&file_id=279861&aid=1982040'
cd ../..
dpkg-buildpackage -rfakeroot -uc -b
cd ..
sudo dpkg -i tsclient_0.150-1ubuntu3_i386.deb

logout from Gnome and enjoy your new shiny enhanced tsclient

---

### Post by AikenDrum on 2009-01-13
Excellent - didn't know you could just place the patch files under debian/patch.  

On 8.04 you still need to copy the tsclient-applet files across,  it seems to work ok on 8.10 though.

Cheers.

---

### Post by scottkicksbutt on 2009-01-20
This works perfectly - almost. The wget statements could not complete the download so I pasted the url into a browser and downloaded the patch(s) manually.  Oddly enough, the actual patch that was download was for links-0.92 (lynx) and not the tsclient patch so something with the url is a little off.  I downloaded the patch from the link a the bottom of this page - [http://sourceforge.net/tracker/index.php?func=detail&aid=1865995&group_id=192483&atid=941576]("http://sourceforge.net/tracker/index.php?func=detail&aid=1865995&group_id=192483&atid=941576") and followed the rest of the process.  Excellent post for those who are unfortunate enough to manage multiple windows servers.  I am running Intrepid  2.6.27-7-generic on a thinkpad t60p.

---

