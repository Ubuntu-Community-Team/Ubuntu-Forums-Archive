---
title: "Thunderbird Virus Scan"
date: 2008-08-09
forum: General Help
---

### Post by grege on 2008-08-09
I have searched a lot and this subject seems ignored. I do not want to get into a discussion about the need for virus scanning in Linux. This is for those who actually want scan for viruses, to ensure they do not forward a virus on to a poor Windows user.

Install Thunderbird, clamassassin, clamav, clam-freshclam.

Set up your accounts in Thunderbird. Then go Tools Add-ons and get more addons. You will need to setup a Mozilla account and get the add on "clamdrib". Download to you home folder, then in Thunderbird Tools Add-ons install clamdrib-0.2-tb.xpi

open a terminal window and sudo dpkg-reconfigure clamav-base

Accept all the defaults except

socket type change to TCP
IP address clamd will listen on: change to localhost

OK, restart your computer and open Thunderbird. Restarting will load clamav with the new settings and update the virus database.

Tools -> Add-ons -> clamdrib -> Preferences -> Test Settings  this will mconfirm everything is working.

Done.

This is much simpler than trying to set up a local mail server.

Any other suggestions or configuration ideas, please post your thoughts

:)

---

### Post by vgg on 2008-08-31
Thanks it's working well (even if I hope I'll never need such a protection, one reason for going to a non root account under linux by opposite to home Ms's products)
But I have 2 questions
-Why is clamassassin nedded ? (it thought camdrib conect directly to clamd, if this one is configured  through the real socket ant not only /tmp/clamd.socket). I didn't found any documentation on this add-on
-Does it scan only when getting mail through thunderbird or when sending too (the goal is to have protection, but not only : don't diffusing viruses to my windows's contact in case of infection does matter too)

-As an idea, I will try a freshclam (update antivirus) at bootime (useful when using linux as a workstation). 

Thanks for your last post, and if you have the answer, thanks in advance for that too

Vgg

---

### Post by vgg on 2008-09-06
Hi
I try without spamassasin and it seems too work too
By activating the log in my clamd.conf the scan is made everytime I open/preview a mail in thunderbird
In my logfile (/var/log/clamd.log : stream(127.0.0.1@1709): OK)

So the scan starts when you open/preview an incoming mail, not when you get or post one (in the difference whith the MS Window's style of doing that). The realtime protection (for not sending an infected file which as been optained not by a mail) will be with the dazuko system, but maybe it's a lot of works for limited risk)

For thoses who'll be intersted, I wrote an /etc/init.d/freshclam script for launching freshclam as a daemon at boot. It's an adaptation from the one launching clamd at boot (see installation doc of clamav). This script as been made on a fedora but if doens't work exactly the same on ubuntu (I didnt try actually), it must not be too difficult for adapting it
I suggest for those who use their Linux as home/workstation to activate a limited log (freshclam & clamd, 2M could be enough)..and sometimes verify everything is working well

--/etc/init.d/freshclam (then chkconfig --add freshclam for installing in differents rc?.d)

#! /bin/bash
#
# crond   Start/Stop the clam antivirus update daemon.
#
# chkconfig: 2345 71 40
# description: clamd is a standard Linux/UNIX program that scans for Virusesi, freshclam the update program.
# processname: freshclam
# config: /etc/freshclam.conf
# pidfile: /var/lock/subsys/freshclam

# Source function library.
. /etc/init.d/functions

RETVAL=0

# See how we were called.
#Verify 4 times a day
prog="freshclam"
progargs=" --quiet --daemon -c 4"
progdir="/usr/local/bin"

# Source configuration
if [ -f /etc/sysconfig/$prog ] ; then
	. /etc/sysconfig/$prog
fi

start() {
	echo -n $"Starting $prog: "
	# Don't allow files larger than 20M to be created, to limit DoS
	# Needs to be large enough to extract the signature files
	ulimit -f 20000
        LANG= daemon $progdir/$prog $progargs
	RETVAL=$?
	echo
	[ $RETVAL -eq 0 ] && touch /var/lock/subsys/freshclam
	return $RETVAL
}

stop() {
	echo -n $"Stopping $prog: "
	# Would be better to send QUIT first, then killproc if that fails
	killproc $prog
	RETVAL=$?
	echo
	[ $RETVAL -eq 0 ] && rm -f /var/lock/subsys/freshclam
	return $RETVAL
}

rhstatus() {
	status freshclam
}

restart() {
	stop
	start
}

case "$1" in
  start)
	start
	;;
  stop)
	stop
	;;
  restart)
	restart
	;;
  status)
	rhstatus
	;;
  *)
	echo $"Usage: $0 {start|stop|status|restart}"
	exit 1
esac

exit $?

---

### Post by thane1 on 2008-09-07
Found this thread.  Have been trying to get clamav to work for some time and have just installed clamdrib from Mozilla.  Have modified my /etc/clamav/clamd.conf file as directed in the Mozilla reviews by adding the lines, [COLOR="DarkRed"]TCPsocket 3310 [COLOR="Black"]and [COLOR="DarkRed"]TCPAddr localhost [COLOR="Black"][/COLOR][/COLOR][/COLOR][/COLOR]
My clamd.conf file is listed below:

#Automatically Generated by clamav-base postinst
#To reconfigure clamd run #dpkg-reconfigure clamav-base
#Please read /usr/share/doc/clamav-base/README.Debian.gz for details
LocalSocket /var/run/clamav/clamd.ctl
FixStaleSocket true
User clamav
AllowSupplementaryGroups true
ScanMail true
ScanArchive true
ArchiveMaxRecursion 5
ArchiveMaxFiles 1000
ArchiveMaxFileSize 10M
ArchiveMaxCompressionRatio 250
ArchiveLimitMemoryUsage false
ArchiveBlockEncrypted false
MaxDirectoryRecursion 15
FollowDirectorySymlinks false
FollowFileSymlinks false
ReadTimeout 180
MaxThreads 12
MaxConnectionQueueLength 15
StreamMaxLength 10M
LogSyslog false
LogFacility LOG_LOCAL6
LogClean false
LogVerbose false
PidFile /var/run/clamav/clamd.pid
DatabaseDirectory /var/lib/clamav
TemporaryDirectory /tmp
SelfCheck 3600
Foreground false
Debug false
ScanPE true
ScanOLE2 true
ScanHTML true
DetectBrokenExecutables false
MailFollowURLs false
ArchiveBlockMax false
ExitOnOOM false
LeaveTemporaryFiles false
AlgorithmicDetection true
ScanELF true
IdleTimeout 30
MailMaxRecursion 64
PhishingSignatures true
PhishingScanURLs true
PhishingRestrictedScan true
PhishingAlwaysBlockSSLMismatch false
PhishingAlwaysBlockCloak false
DetectPUA false
LogFile /var/log/clamav/clamav.log
LogTime true
LogFileUnlock false
LogFileMaxSize 0
TCPsocket 3310
TCPAddr localhost

My Thunderbird shows Clamdrib/Clamav enabled in the bottom right corner of the screen, when I run it.  However the description panel between the inbox emails pane and the preview pane, which describes the highlighted inbox email lists ClamAV status: CONNECTION PROBLEMS .  So I'm not sure if the clamav is actually working.  I seem to be able to forward emails to myself and successfully receive them.  Any ideas?  I'm running Ubuntu Hardy 8.04 and have installed clamav-daemon as instructed in clamdrib info.

---

### Post by vgg on 2008-09-08
Hi
Could you verify if the clamd is running (ps -aef | grep clamd)
If doesn't run, then launch it before (clamd)
You can test it through scanning the current director : clamdscan
I made my install manually (go to clamav.com, download the version, configure, make, then modify .conf file and add the start scripts) because my ubuntu is in a migration state (to a vbox instance) so I'm dealing a little bit with fedora and the yum install wasn't exactly what I wanted
So if you did it throuh packages maybe you have to add a start of clamd at bootime. You will find information in the clamav documentation (I took some samples on [http://www.freespamfilter.org/FC4.html](http://www.freespamfilter.org/FC4.html) but it's more than what we need for our purpose)
To be short, there're scripts for major distribution in the contrib subdirectoy (if you install manually) you've just to copy it

Good Luck

Vgg

---

### Post by thane1 on 2008-09-08
Hi vgg.  Thanks for help.  I checked the [COLOR="DarkRed"]ps -aef | grep clamd
[/COLOR] [COLOR="Black"]command you suggested, but I don't know what the output means.  Tried clamdscan and got error msg below.  But I've used what I understand from the instructions is the proper TCPsocket value of 3310.  So maybe my clamd isn't starting at boot time.  I'll check this out at first opportunity (probably tomorrow).  I looked at your fedora clamav manual info briefly.  I'm on Ubuntu 8.04 myself, so I'll have a look to see if there are any directory variations, etc.  
[/COLOR]

thane@thane-desktop:~$ ps -aef | grep clamd 
thane     7144  7122  0 17:47 pts/0    00:00:00 grep clamd 
thane@thane-desktop:~$  ps -aef | grep clamd 
thane     7184  7122  0 17:48 pts/0    00:00:00 grep clamd 
thane@thane-desktop:~$ clamdscan 
ERROR: Parse error at line 4: Unknown option TCPsocket. 
WARNING: Can't parse the configuration file. 

----------- SCAN SUMMARY ----------- 
Infected files: 0 
Time: 0.000 sec (0 m 0 s) 
thane@thane-desktop:~$ cat /etc/clamav/clamd.conf 
#Automatically Generated by clamav-base postinst 
#To reconfigure clamd run #dpkg-reconfigure clamav-base 
#Please read /usr/share/doc/clamav-base/README.Debian.gz for details 
TCPsocket 3310 
TCPAddr localhost 
LocalSocket /var/run/clamav/clamd.ctl 
FixStaleSocket true 
User clamav 

Many thanks for the help!

---

### Post by grege on 2008-09-09
thane1,

Apart from the private message info I sent I had one or two other thoughts.

When you ran sudo dpkg-reconfigure clamav-base, did you select 'enable email scanning"?

And did you add yourself to the clamav users group?

If anyone else is interested it is also possible to add virus scan to Evolution using a simple script.

[http://ubuntuforums.org/showthread.php?t=749085](http://ubuntuforums.org/showthread.php?t=749085)

I just don't like Evolution, but this solution worked for me until I moved to Thunderbird.

The very best was Claws Email, but there is some conflict between GPL versions of Clam and Claws and Claws have banned Clam. I wish they could resolve their issues as Claws has many powerful processing addons, but for the moment, not virus scan.

---

### Post by grege on 2008-09-09
thane1,

Looking at your posts your issue seems to be that clam is not functioning.

Might i suggest uninstalling everything 'clam" and removing all configuration files and then start again.

I did not have to do anything fancy, the straight forward install from the repos just worked.

You are using the 64bit version and I am using the 32bit, but it should not make a difference.

Once you can run clamdscan without error, then the Thunderbirs addon will probably work as well.

---

### Post by thane1 on 2008-09-10
Thanks again grege.  Just off to work shortly.  Was thinking myself last night that I should uninstall everything and I shall do that when I get back in.  Will post results.  Btw, I didn't add myself to a clam users' group as far as I know, although the small icon at the bottom right of the Tbird screen states, that Clam is enabled.  Will let you know and thanks.  Cheers

---

### Post by thane1 on 2008-09-10
Wowie,zowie.  Been trying to get clamav to work with Thunderbird for some time.  Here's what I had to do (thanks for pointers grege) to get clamav scanning email in Thunderbird with Ubuntu 8.04 amd64 hardy heron.  Started today by uninstalling all of my clamav programs, which were also in your list (apart from libclamav2 which was not available from my 64 bit repositories).  Uninstalled clamdrib through Thunderbird add-ons feature.  Installed the two hardy backports repositories (although I was a little leery about installing the proposed repositories, as you had).  Shut down then restarted computer, installed aforementioned clam progs, started Thunderbird and reinstalled clamdrib through tools,add-ons feature.  Retried sending myself a test email and got same result "clamav status: connection problems".  Googled and found a source for libclamav2 for amd64 hardy at   [https://launchpad.net/ubuntu/hardy/amd64/libclamav2/0.91.2-3ubuntu2](https://launchpad.net/ubuntu/hardy/amd64/libclamav2/0.91.2-3ubuntu2)   and downloaded and installed the .deb package.  Rebooted hardy checked to make sure (through Synaptic) that I had the package installed - all was well there.  Retried the Tbird and still had the same problem.  Checked Tbird's tools,add-ons,(clamdrib)preferences feature and my settings were the same as yours (enable,localhost,3310,100 secs (instead of your 20 secs) and label only.  Tried your 20 second value and still got the "failed" msg when testing through this page.  Checked my /etc/clamav/clamd.conf file and there were no listings for the localhost or the TCPsocket value of 3310.  This surprised me because although I had not manually added them to the conf file like I did yesterday, the tools,add-ons,preferences page showed them as being present.  Next I tried the sudo dpkg-reconfigure clamav-base command, which I also used yesterday and this time after making the two changes to 3310 and localhost, then accepting everything else as presented I rebooted.  Clamav now works with Thunderbird.  Thanks to you grege, to zaphod65 for the guidance and to k0b4y45h1 for making up clamdrib.  Its nice to be able to protect my Windows friends from forwarded Windows viruses.  Cheers.

---

### Post by RMJ1940 on 2008-11-27
Thank You Very Much. I have been working on this for days. Found your post and it worked first time. :) Thanks Again.  I'll be back for more. Bob Jones

---

### Post by Lorac1949 on 2009-01-07
I don't know if I'm missing anything, but with Gutsy, I've not been able to make Clamav work with Tbird. I uninstalled all Clam software and the clamdrib add-on in T-bird. I also ran the reconfig in Terminal. The "Enable" message and icon show in the lower right corner of T-bird, but the test of the add-on fails. Can anyone help me solve this puzzle?

I was hit with a virus yesterday and lost several e-mails. I didn't even know I had a virus until I ran a Clam scan last night. Ouch!:eek:


> **grege said:**
> thane1,

Looking at your posts your issue seems to be that clam is not functioning.

Might i suggest uninstalling everything 'clam" and removing all configuration files and then start again.

I did not have to do anything fancy, the straight forward install from the repos just worked.

You are using the 64bit version and I am using the 32bit, but it should not make a difference.

Once you can run clamdscan without error, then the Thunderbirs addon will probably work as well.

---

### Post by geofff on 2009-06-06
grege

I followed your instructions of 10th august 08 to the letter and couldn't get clamdrib to work. I installed and deinstalled a number of times but still got failure.

Then I installed clamav-daemon and it worked!

Can I suggest for others who may also follow your instructions to the letter that you edit your post of 10th August to include clamav-daemon.

But I'm so glad to get it working. Thankyou

---

### Post by jonsem.phooey on 2009-08-02
OK, I just upgraded to Kubuntu 9.04 and had to go through setting up clamdrib again and, silly, forgot to take notes last time.

Anyway, I don't think you need clamassassin, but you do need to make sure clamav-daemon is installed, it is not installed by default.

...and of course, TCP, 3310, localhost....all those things that have been said before.


just also add sudo apt-get install clamav-daemon

---

### Post by r_avital on 2009-11-20
FYI all,

The Wiki page on scanning email ([https://help.ubuntu.com/community/ScanningEmail#preview](https://help.ubuntu.com/community/ScanningEmail#preview)) states that you should add "TCPsocket 3310) to the clamd.conf file

I don't know if this is something that has changed since that page was written, but this had me running around in circles for an hour, including full removal/reinstall of clamav as suggested above, and the dpkg-reconfigure steps etc.

The correct entry is "TCPSocket 3310" (without quotes) - Upper-Case "S"

Hope this helps :)

---

### Post by Thelasko on 2010-01-30
When I run clamav-deamon restart it says:
```
ERROR: Parse error at line 54: Unknown option TCPsocket
ERROR: Can't open/parse the config file /etc/clamav/clamd.conf

```

Woops! post #15 right above me already covered this

TCPSocket people, not TCPsocket.

---

### Post by Thelasko on 2010-01-30
Second Question:  ClamAV says I have a virus in my Thunderbird settings folder.  How do I find it with Clamdrib?

---

### Post by Thelasko on 2010-02-05
Okay, now whenever I try to open an attachment with Thunderbird, it gives me the option to open it with "Virus Scanner" and that's it.  Anybody know how to fix this?

Never Mind.  This is an unrelated issue.  The problem is with the sender of the email.

---

### Post by madtom1999 on 2010-03-25
[https://help.ubuntu.com/community/ScanningEmail](https://help.ubuntu.com/community/ScanningEmail) was helpful in setting up clamdrib

However, as requested by someone earlier how can I run it on mail that has already been received - or do I just open everything?

---

### Post by dcstar on 2010-03-26
> **madtom1999 said:**
> [https://help.ubuntu.com/community/ScanningEmail](https://help.ubuntu.com/community/ScanningEmail) was helpful in setting up clamdrib

However, as requested by someone earlier how can I run it on mail that has already been received - or do I just open everything?

Depending on how the mail is stored, you can just run a normal Clamav scan on the files. Install the **clamtk** package.

---

### Post by Thelasko on 2010-03-28
> **dcstar said:**
> Depending on how the mail is stored, you can just run a normal Clamav scan on the files. Install the **clamtk** package.

In my experience, Thunderbird stores all email in one large file.  If a virus is found in one email, it will show the whole file as infected.

---

### Post by thane1 on 2011-07-26
Last I checked clamdrib wasn't maintained (probably more than a year or two ago) to be operable with the newer tbird versions.  I used to be happy to use it to protect my windows friends, when I forwarded emails to them.  It worked great.  However tbird is the email prog of choice for me and I have been "forced" to develop the attitude for some time now, that if somebody wants to use windows, they will have to be responsible for their own virus, etc self-protection.  Unfortunate, but I'm not about to start running mail servers, etc to be able to run antivirus progs to protect anybody running windows.  I have enough demands on my time as it is, to be continually updating my computers.  Would love to find an effective, easy to use av prog to protect my friends though.  cheers

---

### Post by Subito Piano on 2013-04-04
This thread is still helpful!  I had an email mess up my T-bird settings (yes, in Linux, twice!!!) -- so the last two days i've beefed up security.  This thread was great! I had to find the clamdrib thunderbird extension online, then I opened up the the install.rdf file  in the xpi and modified the maximum version number to match my version, installed it, then tweaked clamassassin's configuration as per your instructions voila! -- it works 

I also found the Thunderbayes++ extension (also not officially supported anymore, not the latest version anyway) and installed that to beef up spam protection (the jury is still out on that one) and found a neat little extension called "Allow HTML Temp" -- you set your mail to view in plain text to avoid any scripts (like what messed up my T-bird settings, idk HOW ](*,) ), then if you need to view an individual e-mail in html and  are confident it's legit, you simply click a button to view that ONE  e-mail in HTML.   Way cool. 8-)

So all this was not too hard for someone  like me, who is neither newbie nor expert.  Thanks for your help!!  :)

---

### Post by QIII on 2013-04-04
It is, however, very old.

From the Forums CoC:

> If a post is older than a year or so and hasn't had a new reply in that  time, instead of replying to it, create a new thread. In the software  world, a lot can change in a very short time, and doing things this way  makes it more likely that you will find the best information. You may  link to the original discussion in the new thread if you think it may be  helpful.
[I]
Thread **closed.**[/I]

---

