---
title: "&quot;Fn&quot;+F7 does not work on IBM lenovo T60 (ubuntu 7.04)"
date: 2007-07-05
forum: Hardware &amp; Laptops
---

### Post by cseljatib on 2007-07-05
using fn+f7 keys should change the screen output between laptop LCD and/or external monitor (or at least is what happen when using windows XP), but nothing happens when using ubuntu 7.04 in a IBM lenovo T60.

I have saw some old post about it (no success at that time), and I wonder if someone knows the solution for Ubuntu 7.04. Please let me know

thanks in advance

---

### Post by ruffwuk on 2007-07-16
I have a T60 and am looking for the same solution.  I want to watch a dvd from my laptop to my high def TV which I have connected.  The Fn+F7 is a negatory.

---

### Post by Whoopie on 2007-07-18
Did you try that? -> [http://www.thinkwiki.org/wiki/Problem_with_video_output_switching#fglrx-Driver](http://www.thinkwiki.org/wiki/Problem_with_video_output_switching#fglrx-Driver) or [http://www.thinkwiki.org/wiki/Talk:Fglrx](http://www.thinkwiki.org/wiki/Talk:Fglrx)

Be aware that there's a bug in acpi-support which prevents my script to work: [https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/122684](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/122684)

Best regards,
Whoopie

---

### Post by cseljatib on 2007-07-27
Hi woopie,
I have tried the links that you told me, nevertheless they are kind of hard for me to follow. Here some questions:

in [http://www.thinkwiki.org/wiki/Problem_with_video_output_switching#fglrx-Driver](http://www.thinkwiki.org/wiki/Problem_with_video_output_switching#fglrx-Driver) appear
*Output switching with the Closed-Source ati-driver works: Just use # aticonfig --query-monitor and e.g. # aticonfig --enable-monitor...". You can use those two commands in a script, and bind them to FnF7*

but, where should I write this?, shoudl I open the terminal and what?, where, how? Sorry for so basic questions/

in the same link, you have an alternative solution. I did create the file /etc/acpi/events/ibmvideobtn and copy as you put there, and I have also created the file /etc/acpi/ibm-video.sh and do the same. I restarted, and it did not work.

i have also checked the solution in the link [http://www.thinkwiki.org/wiki/Talk:Fglrx](http://www.thinkwiki.org/wiki/Talk:Fglrx), and it did not work either.

You also gave a link for fixing a bug with this, nevertheless, when i open /usr/share/acpi-support/power-funcs, the file looks different the one that you mentioned, here is what i see
(between ***)
****
# a micro library of helper functions for the power scripts

umask 022;

PATH="$PATH:/usr/bin/X11"
POWERSTATE="/var/lib/acpi-support/powerstate"

getXuser() {
        user=`finger| grep -m1 ":$displaynum " | awk '{print $1}'`
	if [ x"$user" = x"" ]; then
		user=`finger| grep -m1 ":$displaynum" | awk '{print $1}'`
	fi
	if [ x"$user" != x"" ]; then
        	userhome=`getent passwd $user | cut -d: -f6`
        	export XAUTHORITY=$userhome/.Xauthority
	else
		export XAUTHORITY=""
	fi
}

getXconsole() {
	console=`fgconsole`;
	displaynum=`ps ax | grep -e 'X .* vt'$console | grep -v grep | sed -re 's!.*/X .*:([0-9]+).*!\1!'`
	if [ x"$displaynum" != x"" ]; then
		export DISPLAY=":$displaynum"	
		getXuser
	fi
}

getState() {
        /usr/bin/on_ac_power;
        if [ "$?" -eq 0 ]; then
                STATE="AC";
        elif [ "$?" -eq 1 ]; then
                STATE="BATTERY";
        fi
}
        
#check our state has actually changed
checkStateChanged() {
# do we have our state stashed?
        if [ -f "$POWERSTATE" ]; then
                OLDSTATE=$(<$POWERSTATE) 
                if [ "$STATE" = "$OLDSTATE" ]; then
                       exit 0
                else
#stash the new state
                        echo "$STATE" > $POWERSTATE
                fi
        else
#we need to stash the new state
                echo "$STATE" > $POWERSTATE
        fi
}

LAPTOP_MODE='/usr/sbin/laptop_mode'
HDPARM='/sbin/hdparm -q'

LIDSTATE='/var/lib/acpi-support/lidstate'

*****

Any suggestion??, I am using ubuntu 7.04 in a lenovo t60

thanks in advance

---

