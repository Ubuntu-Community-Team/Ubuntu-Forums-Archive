---
title: "DVD upggrade hardy to jaunty"
date: 2009-06-29
forum: Installation &amp; Upgrades
---

### Post by stanley82 on 2009-06-29
I got the dvd with the Ubuntu user magazine from my local book store.  
First try at upgraded from hardy 64 to jaunty 64 failed as a couple of files (out of 400 Meg download) failed checksum.  Next try I got all these errors that  I copied and pasted into gedit for you.  The first three look really bad.  (U sure this is not an alpha dvd?)  The last one looks like I'll be dead once I reboot.  Gosh what a mess may become!!!!  I've tried making a bug report but since it's not in an app it's not accepted.  I even made a bug report using the terminal command "ubuntu-bug -p ubiquity" but once in the firefox window it did not understand ubipuity.  Right now I'm in a partial mess.  System is there but system/exit is not. Also the screen is 3cm to the left.
-----------------------------------------------------------------------
cat: /var/log/installer/syslog: Permission denied


Problem 1
Could not install '/media/cdrom0//pool/main/x/x11-utils/x11-utils_7.4+1build1_amd64.deb'

The upgrade will continue but the '/media/cdrom0//pool/main/x/x11-utils/x11-utils_7.4+1build1_amd64.deb' package 
may be in a not working state. Please consider submitting a bug report about it.

short read in buffer_copy (backend dpkg-deb during `./usr/share/man/man1/xmessage.1.gz')

Problem 2
Could not install '/media/cdrom0//pool/main/z/zenity/zenity_2.26.0-0ubuntu2_amd64.deb'

The upgrade will continue but the '/media/cdrom0//pool/main/z/zenity/zenity_2.26.0-0ubuntu2_amd64.deb' 
package may be in a not working state. Please consider submitting a bug report about it.

subprocess dpkg-split returned error exit status 2

Problem 3
Could not install '/media/cdrom0//pool/main/x/xterm/xterm_241-1ubuntu1_amd64.deb'

The upgrade will continue but the '/media/cdrom0//pool/main/x/xterm/xterm_241-1ubuntu1_amd64.deb' package 
may be in a not working state. Please consider submitting a bug report about it.

subprocess dpkg-split returned error exit status 2

Problem 4
Could not install 'xterm'

The upgrade will continue but the 'xterm' package may be in a not working state. Please consider 
submitting a bug report about it.

package xterm is already installed and configured

Problem 5
Could not install 'zenity'

The upgrade will continue but the 'zenity' package may be in a not working state. Please consider 
submitting a bug report about it.

package zenity is already installed and configured

Problem 6
Could not install 'x11-utils'

The upgrade will continue but the 'x11-utils' package may be in a not working state. Please consider 
submitting a bug report about it.

package x11-utils is already installed and configured

Problem 7
Sorry, the program "package_hook" closed unexpectedly.  (this was after
xterm failed to install and auto generated bug report).  So So so I'm going to 
ignore future crashes of theis program version.

Problem 8 
An error occurred while loading or saving configuration info for web browser.  
some of your config settings may not work right.

---

