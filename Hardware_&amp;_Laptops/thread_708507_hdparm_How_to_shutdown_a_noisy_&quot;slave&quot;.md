---
title: "hdparm: How to shutdown a noisy &quot;slave&quot;"
date: 2008-02-26
forum: Hardware &amp; Laptops
---

### Post by zeiz on 2008-02-26
I googled a number of posts where people ask how to shutdown secondary HDD that's not in use. There are no comprehensive solution there, mostly no answer at all.
I also have a noisy "slave" (Matrox 40GB) with XP on it + a few pro-apps. Since I've been using Ubuntu as my main OS I almost never need that drive. I asked the forum and I got great link so I know how to shutdown the slave:
$ sudo hdparm -S1 /dev/sdb #Note: If to set S0 as recommended in the link to shut down immediately - no shutdown at all.
password:
 /dev/sdb
setting standby to 1 (5sec)
$
Then the drive shuts down in 50 (!) seconds. Nothing changes if I set -S2 (10sec) -same 50 sec to shutdown. It's interesting why it takes so long but that's not the question.
The question is where and how to SAVE this command. Otherwise if I had 4 drives I would need to type the routine 3 times after every reboot:mad:
I tried to edit /etc/hdparm.conf and it doesn't work for me anyway including "command line" option. There are a few files with "hdparm" in the OS. Which one to edit...and HOW?

PS. I don't have SCSI/SATA drives so it took me a bit to use /dev/sdb instead of /dev/hdb:)

---

### Post by lloyd_b on 2008-02-26
Suggestion: Add that command into "/etc/init.d/rc.local", under the "start" section:
 ```
   start)
        **/sbin/hdparm -S1 /dev/sdb**
        do_start
        ;;

```

It will then run at the end of the init process.

Lloyd B.

---

### Post by zeiz on 2008-02-26
It works, thank you! But...
I never edited files like this before that's why I probably got some errors. It went like this:
#! /bin/sh

PATH=/sbin:/bin:/usr/sbin:/usr/bin
[ -f /etc/default/rcS ] && . /etc/default/rcS
. /lib/lsb/init-functions

do_start() {
	if [ -x /etc/rc.local ]; then
		log_begin_msg "Running local boot scripts (/etc/rc.local)"
		/etc/rc.local
		log_end_msg $?
	fi
}

case "$1" in
    start)
	[COLOR="Red"]/sbin/hdparm -S1 /dev/sdb[/COLOR] # I added only this row, the rest was already here
	do_start
        ;;
    restart|reload|force-reload)
        echo "Error: argument '$1' not supported" >&2
        exit 3
        ;;
    stop)
        ;;
    *)
        echo "Usage: $0 start|stop" >&2
        exit 3
        ;;
esac

The error appeared right before I finished the editing, it wasn't there before!
That's why I tried to exchange "1" with "2"...but it didn't help.

After reboot I got the message at GUI start:
There was an error starting the GNOME Settings Daemon.
Some things, such as themes, sounds, or background settings may not work correctly.
The last error message was:
Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
GNOME will still try to restart the Settings Daemon next time you log in.

Actually nothing looked wrong except the message. I copied /etc/init.d/rc.local content (it was the same with the error) and rebooted again.
This time Gnome reported nothing but ...rc.local still contains the same error message.
Where I was wrong?:confused:

PS. Anyway the drive shuts down now automatically! :)

---

### Post by jocko on 2008-02-26
> **zeiz said:**
> It works, thank you! But...
I never edited files like this before that's why I probably got some errors. It went like this:
#! /bin/sh

PATH=/sbin:/bin:/usr/sbin:/usr/bin
[ -f /etc/default/rcS ] && . /etc/default/rcS
. /lib/lsb/init-functions

do_start() {
    if [ -x /etc/rc.local ]; then
        log_begin_msg "Running local boot scripts (/etc/rc.local)"
        /etc/rc.local
        log_end_msg $?
    fi
}

case "$1" in
    start)
    [COLOR=Red]/sbin/hdparm -S1 /dev/sdb[/COLOR] # I added only this row, the rest was already here
    do_start
        ;;
    restart|reload|force-reload)
[COLOR=Blue]         echo "Error: argument '$1' not supported" >&2[/COLOR]
        exit 3
        ;;
    stop)
        ;;
    *)
        echo "Usage: $0 start|stop" >&2
        exit 3
        ;;
esac

The error appeared right before I finished the editing, it wasn't there before!
That's why I tried to exchange "1" with "2"...but it didn't help.

After reboot I got the message at GUI start:
There was an error starting the GNOME Settings Daemon.
Some things, such as themes, sounds, or background settings may not work correctly.
The last error message was:
Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
GNOME will still try to restart the Settings Daemon next time you log in.

Actually nothing looked wrong except the message. I copied /etc/init.d/rc.local content (it was the same with the error) and rebooted again.
This time Gnome reported nothing but ...rc.local still contains the same error message.
Where I was wrong?:confused:

PS. Anyway the drive shuts down now automatically! :)

Contains what error message? The one I highlighted in blue above?
That should be there.

---

### Post by zeiz on 2008-02-26
> **jocko said:**
> Contains what error message? The one I highlighted in blue above?
That should be there.

Yes it is. But why? I believe it wasn't there before I did the editing. Everything works correct now but the error message... :shock:

---

### Post by jocko on 2008-02-27
> **zeiz said:**
> Yes it is. But why? I believe it wasn't there before I did the editing. Everything works correct now but the error message... :shock:

That is not an error message, it's a *command* that is *supposed* to be there and it *WAS* there before you edited the file. 
What it does more specifically, is that if you try to run the script with unavailable options ("restart", "reload", or "force-reload") it will inform you of this and tell you which options are avalable ("start" and "stop").

The error you got in gnome have nothing to do with this, unless it's because it couldnt read from your hard drive because it was suspended.
Why would you want your hard drive to suspend after only 5 seconds of inactivity? 
This will mean you will have to wait for the hard drive to spin up almost *every* time some program needs to access it, which will result in quite a slow down.

---

### Post by zeiz on 2008-02-27
Thanks a lot for the "error" explanation. The file looked too scary  and I didn't notice that the "error" was already there:oops:
As to the drive I set -S2 so it's 10sec looks like enough.It shuts down shortly after Gnome starts. I commented out that drive's partitions in fstab, they are not automounted now and they don't appear anymore on the desktop though I can mount them in Computer window. If I need XP I must reboot anyway. If I need some files from its storage partition...it feels fast enough.
So thanks again** jocko** and personal thanks to **lloyd_b** :)

---

