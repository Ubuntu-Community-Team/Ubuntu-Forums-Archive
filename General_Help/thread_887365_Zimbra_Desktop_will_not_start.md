---
title: "Zimbra Desktop will not start"
date: 2008-08-12
forum: General Help
---

### Post by useResa on 2008-08-12
I have installed Zimbra Desktop Installer and did not have any issues during installation (opposed to what is posted [here]("http://ubuntuforums.org/showthread.php?t=886974")).

However, when I run the installer Applications --> Internet --> Zimbra Desktop Installer it ends with the message: "Failed to inject zimlets. Some features may be missing" (see attachment Zimbra-Installer.jpg)
When I start the application with the icon on the desktop I get the following error: "Couldn't start Yahoo! Zimbra Desktop server, giving up" (see attachment Zimbra-Error.png).

If I run the command from the launcher in a terminal this is the result
```
*** UpdateService: canUpdate?  testing /home/rdrijsen/zimbra/zdesktop/linux/prism/update.test
*** UpdateService: canUpdate?  testing /home/rdrijsen/zimbra/zdesktop/linux/prism/updates/0/update.test
*** UpdateService: can update
*** General: Reading Status File: /home/rdrijsen/zimbra/zdesktop/linux/prism/updates/0/update.status
*** UpdateService: _postUpdateProcessing: Downloading patch, resuming...
*** General: Reading Status File: /home/rdrijsen/zimbra/zdesktop/linux/prism/updates/0/update.status
*** Downloader: found existing patch [state=downloading]
*** Downloader: resuming download
*** Downloader: downloadUpdate: Downloading from http://files.zimbra.com/downloads/zdesktop/beta/1251/zdesktop_0_90_build_1251_linux_i686.sh to /home/rdrijsen/zimbra/zdesktop/linux/prism/updates/0/update.mar
Starting zdesktop
nohup: appending output to `nohup.out'
*** Downloader: onStartRequest: http://files.zimbra.com/downloads/zdesktop/beta/1251/zdesktop_0_90_build_1251_linux_i686.sh
*** Downloader.onProgress: onProgress: http://files.zimbra.com/downloads/zdesktop/beta/1251/zdesktop_0_90_build_1251_linux_i686.sh, 600000/51124812
*** Downloader.onProgress: onProgress: http://files.zimbra.com/downloads/zdesktop/beta/1251/zdesktop_0_90_build_1251_linux_i686.sh, 900000/51124812
*** Downloader: onStopRequest: http://files.zimbra.com/downloads/zdesktop/beta/1251/zdesktop_0_90_build_1251_linux_i686.sh, status = 2147500036
*** Downloader: Setting state to: downloading
```Anyone has any suggestion on what the issue could be?

---

### Post by useResa on 2008-08-12
I just tried starting it again but got the same error.
So once more ... hoping to get some more info ... started it again from the terminal. But since I was busy I did not respond immediately to the error message.
Going back to the terminal I noticed that a file is being downloaded (which can also be concluded from the last lines on my previous post), albeit at a very slow pace. See below:
```
*** Downloader.onProgress: onProgress: http://files.zimbra.com/downloads/zdesktop/beta/1251/zdesktop_0_90_build_1251_linux_i686.sh, 11400000/51124812
*** Downloader.onProgress: onProgress: http://files.zimbra.com/downloads/zdesktop/beta/1251/zdesktop_0_90_build_1251_linux_i686.sh, 11700000/51124812
*** Downloader.onProgress: onProgress: http://files.zimbra.com/downloads/zdesktop/beta/1251/zdesktop_0_90_build_1251_linux_i686.sh, 12000000/51124812
```
I think it is currently already downloading for nearly 15 minutes and it is only at approx 20%. If time permits I let it run until it is finished, hoping it will start afterwards.

---

### Post by useResa on 2008-08-12
Okay ... waited until everything was downloaded and indeed I got a message that a software update was available (see attachment).
So I installed the update (the old release was being removed in the process) but it ended with the same error as indicated in my first post.
"Failed to inject zimlets. Some features may be missing".
Here is the dump from the upgrade process
```
*** Downloader: onStopRequest: http://files.zimbra.com/downloads/zdesktop/beta/1251/zdesktop_0_90_build_1251_linux_i686.sh, status = 0
*** Downloader: server hash: a9d6cd0289c5950c9296a48c8ba89d99 client hash: a9d6cd0289c5950c9296a48c8ba89d99
*** Downloader: Setting state to: pending
Unpacking JRE ...
Preparing JRE ...
Starting Installer ...
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7ee9767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb7ee98b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0x8c2451bd]
#3 /tmp/zdupdate/update.sh.11759.dir/jre/lib/i386/xawt/libmawt.so [0x8c317dce]
#4 /tmp/zdupdate/update.sh.11759.dir/jre/lib/i386/xawt/libmawt.so [0x8c301d77]
#5 /tmp/zdupdate/update.sh.11759.dir/jre/lib/i386/xawt/libmawt.so [0x8c301ef3]
#6 /tmp/zdupdate/update.sh.11759.dir/jre/lib/i386/xawt/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x26) [0x8c302136]
#7 [0xb1782008]
#8 [0xb177bb6b]
#9 [0xb177bb6b]
#10 [0xb1779236]
#11 /tmp/zdupdate/update.sh.11759.dir/jre/lib/i386/server/libjvm.so [0xb7603eac]
#12 /tmp/zdupdate/update.sh.11759.dir/jre/lib/i386/server/libjvm.so [0xb77d3aa8]
#13 /tmp/zdupdate/update.sh.11759.dir/jre/lib/i386/server/libjvm.so [0xb7603cdf]
#14 /tmp/zdupdate/update.sh.11759.dir/jre/lib/i386/server/libjvm.so(JVM_DoPrivileged+0x32d) [0xb76617ed]
#15 /tmp/zdupdate/update.sh.11759.dir/jre/lib/i386/libjava.so(Java_java_security_AccessController_doPrivileged__Ljava_security_PrivilegedAction_2+0x3d) [0xb730d30d]
#16 [0xb1781898]
#17 [0xb177ba94]
#18 [0xb1779236]
#19 /tmp/zdupdate/update.sh.11759.dir/jre/lib/i386/server/libjvm.so [0xb7603eac]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7ee9767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb7ee981e]
#2 /usr/lib/libX11.so.6 [0x8c244518]
#3 /usr/lib/libX11.so.6(XGetVisualInfo+0x26) [0x8c23b0a6]
#4 /tmp/zdupdate/update.sh.11759.dir/jre/lib/i386/xawt/libmawt.so [0x8c3010b9]
#5 /tmp/zdupdate/update.sh.11759.dir/jre/lib/i386/xawt/libmawt.so [0x8c301303]
#6 /tmp/zdupdate/update.sh.11759.dir/jre/lib/i386/xawt/libmawt.so [0x8c301fa1]
#7 /tmp/zdupdate/update.sh.11759.dir/jre/lib/i386/xawt/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x26) [0x8c302136]
#8 [0xb1782008]
#9 [0xb177bb6b]
#10 [0xb177bb6b]
#11 [0xb1779236]
#12 /tmp/zdupdate/update.sh.11759.dir/jre/lib/i386/server/libjvm.so [0xb7603eac]
#13 /tmp/zdupdate/update.sh.11759.dir/jre/lib/i386/server/libjvm.so [0xb77d3aa8]
#14 /tmp/zdupdate/update.sh.11759.dir/jre/lib/i386/server/libjvm.so [0xb7603cdf]
#15 /tmp/zdupdate/update.sh.11759.dir/jre/lib/i386/server/libjvm.so(JVM_DoPrivileged+0x32d) [0xb76617ed]
#16 /tmp/zdupdate/update.sh.11759.dir/jre/lib/i386/libjava.so(Java_java_security_AccessController_doPrivileged__Ljava_security_PrivilegedAction_2+0x3d) [0xb730d30d]
#17 [0xb1781898]
#18 [0xb177ba94]
#19 [0xb1779236]
/usr/share/themes/Human/gtk-2.0/gtkrc:43: error: lexical error or unexpected token, expected valid token
0 [main] DEBUG zimbra.misc  - Setting connection pool size to 12
9 [main] DEBUG zimbra.misc  - Setting connection pool size to 12
1100 [main] DEBUG zimbra.sqltrace  - SELECT value FROM zimbra.config WHERE name = 'db.version' - 23ms, conn=32607422
oldDbVersion=52 newDbVersion=52
1114 [main] INFO zimbra.misc  - Database '/home/rdrijsen/zimbra/zdesktop/derby' shutdown.
9457 [main] DEBUG zimbra.misc  - Setting connection pool size to 12
9545 [main] DEBUG zimbra.sqltrace  - SELECT value FROM zimbra.config WHERE name = 'db.version' - 0ms, conn=13741320
oldDbVersion=52 newDbVersion=52
9561 [main] INFO zimbra.misc  - Database '/home/rdrijsen/zimbra/zdesktop/derby' shutdown.
```
It does not mean much to me, but maybe somebody else can make some sense out of it  ;)
All I notice is
```
/usr/share/themes/Human/gtk-2.0/gtkrc:43: error: lexical error or unexpected token, expected valid token
```
But I have no idea whether this is serious or not.

Starting it also resulted in the same error as indicated in my first post
"Couldn't start Yahoo! Zimbra Desktop server, giving up"
Starting it from terminal now gives
```
*** UpdateService: canUpdate?  testing /home/rdrijsen/zimbra/zdesktop/linux/prism/update.test
*** UpdateService: canUpdate?  testing /home/rdrijsen/zimbra/zdesktop/linux/prism/updates/0/update.test
*** UpdateService: can update
*** General: Reading Status File: /home/rdrijsen/zimbra/zdesktop/linux/prism/updates/0/update.status
*** UpdateService: _postUpdateProcessing: No Status, No Update
Starting zdesktop
nohup: appending output to `nohup.out'
```

So guess that after the update the situation has not changed :(

---

### Post by zakattack on 2008-08-13
I had the same problem

Try this...
[install_path]/zimbra/zdesktop start

Then double click the icon on the desktop. :guitar:

Z

---

### Post by Bronto on 2008-08-13
Same problem here.
On my workstation (**unmodified** Ubuntu 8.04) the install went flawlessly, Zimbra Desktop works as specified.

On my laptop (same **unmodified** distro) it fails to "inject zimlets".

Conclusion: Just another JavaCrap based application.

---

### Post by useResa on 2008-08-13
> **zakattack said:**
> I had the same problem
Try this...
[install_path]/zimbra/zdesktop start
Then double click the icon on the desktop. :guitar:
:lolflag:
Had to look for a while since I initially got an error.
The proper command is
[install_path]/zimbra/**zdesktop/**zdesktop start
Unfortunately it made no difference at all.
Strange thing is -- IMHO -- that after this command ps -ef | grep -i zdesktop also shows no processes.


> **Bronto said:**
> Same problem here.
On my workstation (**unmodified** Ubuntu 8.04) the install went flawlessly, Zimbra Desktop works as specified.
On my laptop (same **unmodified** distro) it fails to "inject zimlets".
Conclusion: Just another JavaCrap based application.
It indeed seems to be a "random" issue. A colleague of mine runs the same laptop, the same software and it works as intended.
No matter what I try ... just can not seem to get it working.

Hopefully someone can come with the "magic" tip.

---

### Post by Bronto on 2008-08-13
Same bug reported on a MAC: [http://bugzilla.zimbra.com/show_bug.cgi?id=26953](http://bugzilla.zimbra.com/show_bug.cgi?id=26953)

"Magic tip" from the assigned developer: "not important to fix".
(See [http://bugzilla.zimbra.com/show_bug.cgi?id=26953#c23](http://bugzilla.zimbra.com/show_bug.cgi?id=26953#c23))

---

### Post by useResa on 2008-08-13
> **Bronto said:**
> Same bug reported on a MAC: [http://bugzilla.zimbra.com/show_bug.cgi?id=26953](http://bugzilla.zimbra.com/show_bug.cgi?id=26953)
Thanks for the link ... interesting read ... except

> **Bronto said:**
> "Magic tip" from the assigned developer: "not important to fix".
(See [http://bugzilla.zimbra.com/show_bug.cgi?id=26953#c23](http://bugzilla.zimbra.com/show_bug.cgi?id=26953#c23))Sure hope that something will be done about it.

---

### Post by pvonbert on 2008-08-13
Strange, I've installed at work and at home w/o problems, following the instructions on their website.
The latest installed version is:
zdesktop_0_90_build_1249_linux_i686.sh
and if I am notr mistaken I run'ed as sudo
then added to Sessions Preferences|Startup Programs

/home/pvonbert/.zimbra/zdesktop/zdesktop start

as not to have it to run every time I log in any of those two machines. I still prefer Thunderbird, but at work they've moved all the email and calendaring system to Zimbra ....

---

### Post by useResa on 2008-08-14
> **pvonbert said:**
> Strange, I've installed at work and at home w/o problems, following the instructions on their website.
The strange thing indeed is that a colleague of mine also installed it without any issues.
 
> **pvonbert said:**
> The latest installed version is:
zdesktop_0_90_build_1249_linux_i686.sh
build 1249 was installed when using the package from the repositories, at least that is what I understand from the result of *aptitude show zdesktop*:
```
Package: zdesktop
New: yes
State: installed
Automatically installed: yes
Version: 0.90.1249beta-hardy1
Priority: extra
Section: partner/mail
Maintainer: Brian Thomason <[EMAIL="brian.thomason@canonical.com"]brian.thomason@canonical.com[/EMAIL]>
Uncompressed Size: 51.4M
Depends: debianutils, www-browser
Description: Yahoo! Zimbra Desktop
 Zimbra Desktop Edition is an open source email client that allows you to pull
 all your accounts into one place. It is a powerful productivity tool allowing
 important messages to be flagged wherever they arrive - and the best part might
 be that it allows you to read them all off line without an Internet connection.
 
 Installing this package will allow you launch the Zimbra installer directly
 within Ubuntu and begin to consolidate your web mail and work accounts and ease
 the burden that masses of email can be. There are stacks of other features to
 discover as well.
```
The latest version currently (20080813) is build 1251 (see [here]("http://www.zimbra.com/products/desktop_download.html")).
However the upgrade that I mentioned in [post #3]("http://ubuntuforums.org/showpost.php?p=5574482&postcount=3") seems to have taken it there.
Since the README.TXT in [install_path]/zimbra/zdesktop starts out with the following text
```
 
====================================================================
Yahoo! Zimbra Desktop README
====================================================================
0.90 (build 1251)

```
So AFAIK I am fully updated to the latest version.
 
> **pvonbert said:**
> then added to Sessions Preferences|Startup Programs
/home/pvonbert/.zimbra/zdesktop/zdesktop start
as not to have it to run every time I log in any of those two machines. If I get it working I'll keep that in mind.
 
> **pvonbert said:**
> I still prefer Thunderbird, but at work they've moved all the email and calendaring system to Zimbra ....I always use Thunderbird for my mail when I am online (our company uses Zimbra as well), but I like to have zdesktop running so that I can access my mail when I am off line.
 
[off topic]To sync your contacts between Zimbra and Thunderbird [Zindus ]("http://www.zindus.com/")works perfectly for me[/off topic]

---

### Post by pvonbert on 2008-08-14
I think I see the difference, I was a bit hasty in replying. I did not use the repos but the build from Zimbra site. Try that.

---

### Post by useResa on 2008-08-14
> **pvonbert said:**
> I think I see the difference, I was a bit hasty in replying. I did not use the repos but the build from Zimbra site. Try that.Okay ... I have followed your advice.
First I removed the packages by giving the command
```
sudo aptitude purge zdesktop
```
Next I made sure that the old installation was removed by giving the command
```
sudo rm -rf [install_path]/zimbra
```
Then I tried the installation as sudo
```
sudo  sh /home/rdrijsen/Software/Zimbra/zdesktop_0_90_build_1251_linux_i686.sh
```
This resulted in exactly the same error as I have had all the time:
"Failed to inject zimlets. Some features may be missing".
And when I tried to start ZDesktop it also ends up with the same error:
"Couldn't start Yahoo! Zimbra Desktop server, giving up"

So I removed everything again and ran the script without sudo.
Unfortunately ... no difference.

For those who maybe know Java, the log zdesktop.out (from [install_path]/zimbra/zdesktop/log) is attached.
It clearly states an exception, I just don't know what it means.

---

### Post by useResa on 2008-10-16
Today I have tried to install the latest version of Zimbra Desktop installer (zdesktop_0_91_build_1338_linux_i686.sh).
This is **not** the one that can be installed from the repositories, but the one available from [the Zimbra website]("http://www.zimbra.com/products/desktop.html"). 

This version installs and runs without issues now on my laptop.
So from my perspective .. this issue is solved.

---

### Post by tuvw840 on 2008-11-07
[img]http://www.tradewe.com/tradewe/tradewe13.jpg[/img][Lacoste polo](http://www.polooo.com) [Ed Hardy](http://www.tradewe.com/C_59-----Ed-Hardy.html) [ugg boot s](http://www.polooo.com/)[ugg brand boots](http://www.polooo.com/)

---

### Post by halovivek on 2009-01-09
> **useResa said:**
> Today I have tried to install the latest version of Zimbra Desktop installer (zdesktop_0_91_build_1338_linux_i686.sh).
This is **not** the one that can be installed from the repositories, but the one available from [the Zimbra website]("http://www.zimbra.com/products/desktop.html"). 

This version installs and runs without issues now on my laptop.
So from my perspective .. this issue is solved.

yahoo zimbra cannot be run from the sudo user. i tried and got the same error what you got. so i have run as normal user and i have installed that one and working fine with it. now i have posted the thread regarding this [here.]("http://ubuntuforums.org/showthread.php?t=1030223&highlight=yahoo+zimbra")

---

### Post by jrusso2 on 2009-01-09
I am running zdesktop 0_90_build 1278 on 8.04 and seems to run fine.  Maybe the earlier ones had a bug.

---

### Post by Sef on 2009-01-09
Moved to General Help.

---

### Post by brunoscunha on 2009-01-26
> **halovivek said:**
> yahoo zimbra cannot be run from the sudo user. i tried and got the same error what you got. so i have run as normal user and i have installed that one and working fine with it. now i have posted the thread regarding this [here.]("http://ubuntuforums.org/showthread.php?t=1030223&highlight=yahoo+zimbra")

I don't have such luck. After installing the latest version of zimbra it says some widgets could not be loaded and when I try to start zimbra, one more msg: Could not access Yahoo! Zimbra Desktop server. If issue persists after reinstall, please check logs for errors and report to forum.
In log folder, I have the following
[HTML]0    INFO  [main] log - Logging to org.slf4j.impl.Log4jLoggerAdapter(org.mortbay.log) via org.mortbay.log.Slf4jLog
382  INFO  [main] log - jetty-6.1.5
539  INFO  [main] log - No Transaction manager found - if your webapp requires one, please configure one.
Zimbra server process is running as uid=1000 euid=1000 gid=0 egid=0
Fatal error: terminating: can not start server with gid of 0[/HTML]

I don't have a clue what this log may mean. :(

---

### Post by useResa on 2009-01-27
> **brunoscunha said:**
> I don't have a clue what this log may mean. :(Sorry, but I also have no clue. What I can suggest is to have a look at the following threads at the Zimbra forums:
[LIST]
[*]**[zimbra desktop as a pop client to Domino 8.0.2]("http://www.zimbra.com/forums/installation-help/25585-zimbra-desktop-pop-client-domino-8-0-2-a.html")**
[*]**[Unable to access Yahoo account via Zimbra Desktop]("http://www.zimbra.com/forums/error-reports/24272-unable-access-yahoo-account-via-zimbra-desktop.html")**
[/LIST]Both indicate the same error message as you posted.

---

