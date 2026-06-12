---
title: "Account Lease time / Content filtering"
date: 2008-08-12
forum: General Help
---

### Post by crjackson on 2008-08-12
[COLOR="Sienna"][SIZE="5"][CENTER]**Timekeepr - Keep control of computer usage**[/CENTER][/SIZE][/COLOR]
[CENTER][[COLOR="Sienna"]_**timekpr**_[/COLOR]]("https://launchpad.net/timekpr") developers are [**[COLOR="blue"].nedberg]("http://ubuntuforums.org/member.php?u=193487")[/COLOR]**, [**[COLOR="blue"]forger]("http://ubuntuforums.org/member.php?u=178447")[/COLOR]**[/CENTER]

This program will track and control the computer usage of your kids. You can limit their daily usage and configure periods when they cannot log in.

Developers Even Nedberg  and Savvas Radevi&#263; (or .nedberg and forger) of the Ubuntu forums have rewritten the package using python as opposed to the bash shell script of it's previous form.  timekpr now has a full featured interface with the ability to change and grow as needed. The current version supports Ubuntu, Kubuntu and Xbuntu. Please report any bugs you find. Current status indicated below:

[LIST]
[*]Ubuntu [COLOR="White"]-[/COLOR]- Lucid, Karmic, Jaunty, Intrepid, Hardy
[*]Kubuntu - Lucid, Karmic, Jaunty, Intrepid, Hardy
[*]Xubuntu - Lucid, Karmic, Jaunty, Intrepid, Hardy
[/LIST]

[SIZE="5"][CENTER]**[COLOR="Red"]INSTRUCTIONS[/COLOR]**[/CENTER][/SIZE]
[CENTER][SIZE="4"]Please add the software repository as listed below, and install from synaptic or terminal.[/SIZE][/CENTER]

> **.nedberg said:**
> The PPAs have changed. For Stable Versions Use:
```
deb http://ppa.launchpad.net/timekpr-maintainers/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/timekpr-maintainers/ppa/ubuntu jaunty main
```
For Beta Versions Use:
```
deb http://ppa.launchpad.net/nedberg/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/nedberg/ppa/ubuntu jaunty main
```

[Follow these instructions for installing packages from these PPAs]("https://help.launchpad.net/Packaging/PPA#Adding%20a%20PPA%20to%20your%20Ubuntu%20repositories").

---

### Post by .nedberg on 2008-08-12
Never used dansguardian before, but I found this thread: [http://ubuntuforums.org/showthread.php?t=207008](http://ubuntuforums.org/showthread.php?t=207008)

EDIT: Also have a look here: [http://ubuntuforums.org/showthread.php?t=769671](http://ubuntuforums.org/showthread.php?t=769671) for a gui to configure dansguardian.

My children are not old enough to use computers yet, but I will have a look at this myself just to be prepared!

---

### Post by crjackson on 2008-08-13
Okay, I've found a home brewed script from this page called [Waggle Dance]("http://www.91courtstreet.net/wordpress/2008/02/03/how-to-limit-daily-desktop-usage-in-ubuntu/") it's supposed to do EXACTLY what I want, for EXACTLY the same reasons.

I had a little permissions issue during setting up the time limits for my test account, but I overcame that with sudo -i

I have two issues that I'm hoping someone (I posted to the script writer too) will help me with.

In my test scenario, I gave the user 300 seconds of use.  The script then added another 450 in grace time to log off.  I watched the clock ticking in the time keeping file but here's the problem(s);

1) None of the warning pop-ups activated (possibly due to allocated time was lower than grace period.  I changed grace period to 0 but it had no effect).

2) Once it kicked the test user off, it allowed an immediate re-login to the test account, and another 450 seconds were allowed thereby allowing the test user to login every few minutes.  It would be annoying but a determined child would do that all night long.

Could someone have a look at the script and help me modify it so that those problems are fixed please?

```
#!/bin/bash
###
# timekpr.sh - simple 
# watches gnome sessions and logs them out once the user has exceeded a set, per day limit
# /var/lib/timekpr/$username.time hold a count of seconds user has had a gnome session
# /var/lib/timekpr/$username hold the daily allowed seconds for the user
#
# you may need to install notify-send with: $apt-get install libnotify-bin
#
# Copyright 2008 Chris Jackson <chris@91courtstreet.net>
#
# This program is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# See <http://www.gnu.org/licenses/>. 
#

default_limit=87000 #all day
grace_period=450
poll_time=20

#Ubuntu uses alternatives so we look for x-session-manager instead of gnome-session
SESSION_MANAGER=x-session-manager

# get the usernames and PIDs of sessions

while(true); do
    sleep $poll_time
    pidlists=$( ps --no-heading -fC $SESSION_MANAGER | awk 'BEGIN{ FS=" " } { print $1 "," $2 }' )
    for pidlist in $pidlists; do
        # split username and pid - FIXME - I bet this would be faster with bash arrays and substitution 
        username=$( echo $pidlist | awk 'BEGIN{ FS=","} { print $1}' )
        pid=$( echo $pidlist | awk 'BEGIN{ FS=","} { print $2}' )
        if [[ ! -e "/var/lib/timekpr/$username" ]]
        then 
            echo $default_limit > /var/lib/timekpr/$username
        fi
        
        # if the time file is missing or was last touched yesterday, start over
        if [[ -e "/var/lib/timekpr/$username.time" && `( stat -c '%z' /var/lib/timekpr/$username.time|cut -c9,10 )` == `date +%d` ]]
        then 
            #add $poll_time seconds to it
            timekpr=$(( `cat /var/lib/timekpr/$username.time` + $poll_time ))
            echo $timekpr > /var/lib/timekpr/$username.time
        else
        	timekpr=$poll_time
            echo $timekpr > /var/lib/timekpr/$username.time
        fi

        echo $username, $pid, $timekpr
        
        if [[ $timekpr -gt `cat /var/lib/timekpr/$username` ]]
        then
            ## get the display and xauthority used by out session manager
            UDISPLAY=`grep -z DISPLAY \
                /proc/$pid/environ | sed -e 's/DISPLAY=//'`
            XAUTHORITY=`grep -z XAUTHORITY \
                /proc/$pid/environ | sed -e 's/XAUTHORITY=//'`
            
            # find DBUS session bus for this session
            DBUS_SESSION_BUS_ADDRESS=`grep -z DBUS_SESSION_BUS_ADDRESS \
                /proc/$pid/environ | sed -e 's/DBUS_SESSION_BUS_ADDRESS=//'`
            # use it - give a warning, then another one 1/2 way through grace_period
            XAUTHORITY="$XAUTHORITY" DISPLAY="$UDISPLAY" DBUS_SESSION_BUS_ADDRESS="$DBUS_SESSION_BUS_ADDRESS" \
                notify-send --icon=gtk-dialog-warning --urgency=critical -t 30000 "Daily Time Limit" "Your session time is about to expire! You have $grace_period sec. to save your work and logout."
            sleep $(($grace_period/2))   # FIXME: this gives other sessions a free grace_period added to their accounting

            XAUTHORITY="$XAUTHORITY" DISPLAY="$UDISPLAY" DBUS_SESSION_BUS_ADDRESS="$DBUS_SESSION_BUS_ADDRESS" \
                notify-send --icon=gtk-dialog-warning --urgency=critical -t 30000 "Daily Time Limit" "Your session time is about to expire! You have $(($grace_period/2)) sec. to save your work and logout."
            sleep $(($grace_period/2))   # FIXME: this gives other sessions a free grace_period added to their accounting

            XAUTHORITY="$XAUTHORITY" DISPLAY="$UDISPLAY" DBUS_SESSION_BUS_ADDRESS="$DBUS_SESSION_BUS_ADDRESS" \
                notify-send --icon=gtk-dialog-warning --urgency=critical -t 10000 "Shutting Down" "Shutting down session ($pid) now!" 
            # FIXME - should really check to see if user has logged out yet 
            sleep 10
            kill -HUP $pid    #this is a pretty bad way of killing a gnome-session, but we warned 'em
            
            ## uncomment the following to brutally kill all of the users processes
            sleep 10
            pkill -u $username  
            
            ## killing gnome-session should be more like:
            #DISPLAY=":0" XAUTHORITY="/tmp/.gdmEQ0V5T" SESSION_MANAGER="local/wretched:/tmp/.ICE-unix/$pid" su -c 'gnome-session-save --kill --silent' $username
            ## but this can still leave processes to cleanup - plus it's not easy to get SESSION_MANAGER
        fi
    done
done

```

---

### Post by .nedberg on 2008-08-13
To get the notifications:
```
# you may need to install notify-send with: $apt-get install libnotify-bin
```

Looks like it will not prevent a relogin. Short grace_period should "fix" this...

---

### Post by crjackson on 2008-08-13
> **.nedberg said:**
> To get the notifications:
```
# you may need to install notify-send with: $apt-get install libnotify-bin
```

Looks like it will not prevent a relogin. Short grace_period should "fix" this...

Okay, I installed the libnotify-bin and the grace period was changed to 0.  I'll try it again and see what happens.

---

### Post by crjackson on 2008-08-13
> **crjackson said:**
> Okay, I installed the libnotify-bin and the grace period was changed to 0.  I'll try it again and see what happens.

Installing libnotify gave me the missing notifications.  Lowering the grace period doesn't seem to do anything at all.


Anyone who knows how to make this work can feel free to jump in here...

---

### Post by .nedberg on 2008-08-13
OK.

I tested the script and it worked fine for me. I successfully locked myself out of my own computer! It did however let me log in again an imediatly showed a notifier informing I was about to get logged out again.

I sat grace_period to 50.
/var/lib/timekpr/<my username> had 100 in it
poll_time was unchanged at 20
I slightly edited the time for the pop-up notifiers from 30000 to 10000, giving a shorter notifier.

I did not try with grace_period = 0, that might be your problem... Set it low, but not 0. Allow someone to log out and save their work.

If the daily limit is set to 100 sec, grace_period to 50 and poll_time to 20, it will acctually take 180 seconds before the user is logged out.

---

### Post by crjackson on 2008-08-13
> **.nedberg said:**
> OK.

I tested the script and it worked fine for me. I successfully locked myself out of my own computer! It did however let me log in again an imediatly showed a notifier informing I was about to get logged out again.

I sat grace_period to 50.
/var/lib/timekpr/<my username> had 100 in it
poll_time was unchanged at 20
I slightly edited the time for the pop-up notifiers from 30000 to 10000, giving a shorter notifier.

I did not try with grace_period = 0, that might be your problem... Set it low, but not 0. Allow someone to log out and save their work.

If the daily limit is set to 100 sec, grace_period to 50 and poll_time to 20, it will acctually take 180 seconds before the user is logged out.

Cool, perhaps the 0 is the problem then.  I'll give it a shot and see what that does.

Do you know enough about scripting to answer this one?  Would it be possible to include some code that would check the date/time and only allow access between 0700-0000 hours each day?

I'm really trying to nail this thing down.  Thanks a bunch.

---

### Post by .nedberg on 2008-08-13
Pretty sure I can help with that! But I might not get back to you before after the weekend.

---

### Post by crjackson on 2008-08-13
> 
I slightly edited the time for the pop-up notifiers from 30000 to 10000, giving a shorter notifier.


Searching through the script, I found two(2) instances referencing the number 30000.  If I wanted to change that to 10000 as you have, would I simply change BOTH of those values?

---

### Post by crjackson on 2008-08-13
> **.nedberg said:**
> Pretty sure I can help with that! But I might not get back to you before after the weekend.

Thanks, I really appreciate your help.

---

### Post by .nedberg on 2008-08-14
I am at work now, so this is my verion of the script as I remember it from last night. You are right in editing both occurences of 30000 to 10000. This should not have anything to do with the script not working.

```

#!/bin/bash
###
# timekpr.sh - simple 
# watches gnome sessions and logs them out once the user has exceeded a set, per day limit
# /var/lib/timekpr/$username.time hold a count of seconds user has had a gnome session
# /var/lib/timekpr/$username hold the daily allowed seconds for the user
#
# you may need to install notify-send with: $apt-get install libnotify-bin
#
# Copyright 2008 Chris Jackson <chris@91courtstreet.net>
#
# This program is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# See <http://www.gnu.org/licenses/>. 
#

default_limit=87000 #all day
grace_period=50
poll_time=20

#Ubuntu uses alternatives so we look for x-session-manager instead of gnome-session
SESSION_MANAGER=x-session-manager

# get the usernames and PIDs of sessions

while(true); do
    sleep $poll_time
    pidlists=$( ps --no-heading -fC $SESSION_MANAGER | awk 'BEGIN{ FS=" " } { print $1 "," $2 }' )
    for pidlist in $pidlists; do
        # split username and pid - FIXME - I bet this would be faster with bash arrays and substitution 
        username=$( echo $pidlist | awk 'BEGIN{ FS=","} { print $1}' )
        pid=$( echo $pidlist | awk 'BEGIN{ FS=","} { print $2}' )
        if [[ ! -e "/var/lib/timekpr/$username" ]]
        then 
            echo $default_limit > /var/lib/timekpr/$username
        fi
        
        # if the time file is missing or was last touched yesterday, start over
        if [[ -e "/var/lib/timekpr/$username.time" && `( stat -c '%z' /var/lib/timekpr/$username.time|cut -c9,10 )` == `date +%d` ]]
        then 
            #add $poll_time seconds to it
            timekpr=$(( `cat /var/lib/timekpr/$username.time` + $poll_time ))
            echo $timekpr > /var/lib/timekpr/$username.time
        else
        	timekpr=$poll_time
            echo $timekpr > /var/lib/timekpr/$username.time
        fi

        echo $username, $pid, $timekpr
        
        if [[ $timekpr -gt `cat /var/lib/timekpr/$username` ]]
        then
            ## get the display and xauthority used by out session manager
            UDISPLAY=`grep -z DISPLAY \
                /proc/$pid/environ | sed -e 's/DISPLAY=//'`
            XAUTHORITY=`grep -z XAUTHORITY \
                /proc/$pid/environ | sed -e 's/XAUTHORITY=//'`
            
            # find DBUS session bus for this session
            DBUS_SESSION_BUS_ADDRESS=`grep -z DBUS_SESSION_BUS_ADDRESS \
                /proc/$pid/environ | sed -e 's/DBUS_SESSION_BUS_ADDRESS=//'`
            # use it - give a warning, then another one 1/2 way through grace_period
            XAUTHORITY="$XAUTHORITY" DISPLAY="$UDISPLAY" DBUS_SESSION_BUS_ADDRESS="$DBUS_SESSION_BUS_ADDRESS" \
                notify-send --icon=gtk-dialog-warning --urgency=critical -t 10000 "Daily Time Limit" "Your session time is about to expire! You have $grace_period sec. to save your work and logout."
            sleep $(($grace_period/2))   # FIXME: this gives other sessions a free grace_period added to their accounting

            XAUTHORITY="$XAUTHORITY" DISPLAY="$UDISPLAY" DBUS_SESSION_BUS_ADDRESS="$DBUS_SESSION_BUS_ADDRESS" \
                notify-send --icon=gtk-dialog-warning --urgency=critical -t 10000 "Daily Time Limit" "Your session time is about to expire! You have $(($grace_period/2)) sec. to save your work and logout."
            sleep $(($grace_period/2))   # FIXME: this gives other sessions a free grace_period added to their accounting

            XAUTHORITY="$XAUTHORITY" DISPLAY="$UDISPLAY" DBUS_SESSION_BUS_ADDRESS="$DBUS_SESSION_BUS_ADDRESS" \
                notify-send --icon=gtk-dialog-warning --urgency=critical -t 10000 "Shutting Down" "Shutting down session ($pid) now!" 
            # FIXME - should really check to see if user has logged out yet 
            sleep 10
            kill -HUP $pid    #this is a pretty bad way of killing a gnome-session, but we warned 'em
            
            ## uncomment the following to brutally kill all of the users processes
            sleep 10
            pkill -u $username  
            
            ## killing gnome-session should be more like:
            #DISPLAY=":0" XAUTHORITY="/tmp/.gdmEQ0V5T" SESSION_MANAGER="local/wretched:/tmp/.ICE-unix/$pid" su -c 'gnome-session-save --kill --silent' $username
            ## but this can still leave processes to cleanup - plus it's not easy to get SESSION_MANAGER
        fi
    done
done

```

---

### Post by crjackson on 2008-08-14
Great.  I've already made the modifications.  Now I need a method of blocking the login between specific times.  Idealy, I would be able to do a different setting for each user, something that would check the date/time stamp in their timer file.

If not that, then somehow insert a variable that I could adjust to prevent the scrip from resetting at 0000, and use 0600 instead.

This wouldn't be as effective as being able to lock out certain users between 0000-0600 but it would be an improvement.

---

### Post by .nedberg on 2008-08-14
I will have the script ready probably on Sunday or Monday (CET). It will limit login to between, say, 0700 and 2100 (configurable). I might also make it on a "per user" basis, I will have to see what I can manage by then. I am going to my brothers wedding tomorrow and therefore I don't have the time to finish it earlier. I am however close to a solution!

---

### Post by crjackson on 2008-08-14
> **.nedberg said:**
> I will have the script ready probably on Sunday or Monday (CET). It will limit login to between, say, 0700 and 2100 (configurable). I might also make it on a "per user" basis, I will have to see what I can manage by then. I am going to my brothers wedding tomorrow and therefore I don't have the time to finish it earlier. I am however close to a solution!

Great!  If this works out I really owe you.  Send me a PM with your paypal information and I'll make a donation.

Thanks...

---

### Post by .nedberg on 2008-08-17
OK,

here is the script:

/usr/local/bin/timekpr.sh
```

#!/bin/bash
###
# timekpr.sh - simple 
# watches gnome sessions and logs them out once the user has exceeded a set, per day limit
# /var/lib/timekpr/$username.time hold a count of seconds user has had a gnome session
# /var/lib/timekpr/$username hold the daily allowed seconds for the user
#
# you may need to install notify-send with: $apt-get install libnotify-bin
#
# Copyright 2008 Chris Jackson <chris@91courtstreet.net>
#
# This program is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# See <http://www.gnu.org/licenses/>. 
#

default_limit=86400 # All day, new users is given this value
grace_period=60 # how much time do we give to let the user log out?
poll_time=20 # How often the script should check the timelogs
from=7 # When is the users allowed to log in
to=22 # When is the users no longer allowed to be loged in


#Ubuntu uses alternatives so we look for x-session-manager instead of gnome-session
SESSION_MANAGER=x-session-manager

function logOut() {
## get the display and xauthority used by out session manager
            UDISPLAY=`grep -z DISPLAY \
                /proc/$pid/environ | sed -e 's/DISPLAY=//'`
            XAUTHORITY=`grep -z XAUTHORITY \
                /proc/$pid/environ | sed -e 's/XAUTHORITY=//'`
            
            echo -ne "\007"
            # find DBUS session bus for this session
            DBUS_SESSION_BUS_ADDRESS=`grep -z DBUS_SESSION_BUS_ADDRESS \
                /proc/$pid/environ | sed -e 's/DBUS_SESSION_BUS_ADDRESS=//'`
            # use it - give a warning, then another one 1/2 way through grace_period
            XAUTHORITY="$XAUTHORITY" DISPLAY="$UDISPLAY" DBUS_SESSION_BUS_ADDRESS="$DBUS_SESSION_BUS_ADDRESS" \
                notify-send --icon=gtk-dialog-warning --urgency=critical -t 10000 "$1" "Your session is about to expire! You have $grace_period sec to save your work and logout."
            sleep $(($grace_period/2))   # FIXME: this gives other sessions a free grace_period added to their accounting
            echo -ne "\007"
            XAUTHORITY="$XAUTHORITY" DISPLAY="$UDISPLAY" DBUS_SESSION_BUS_ADDRESS="$DBUS_SESSION_BUS_ADDRESS" \
                notify-send --icon=gtk-dialog-warning --urgency=critical -t 10000 "$1" "Your session is about to expire! You have $(($grace_period/2)) sec to save your work and logout."
            sleep $(($grace_period/2))   # FIXME: this gives other sessions a free grace_period added to their accounting

            XAUTHORITY="$XAUTHORITY" DISPLAY="$UDISPLAY" DBUS_SESSION_BUS_ADDRESS="$DBUS_SESSION_BUS_ADDRESS" \
                notify-send --icon=gtk-dialog-warning --urgency=critical -t 10 "Shutting Down" "Shutting down session ($pid) now!" 
            # FIXME - should really check to see if user has logged out yet 
            sleep 10
            kill -HUP $pid    #this is a pretty bad way of killing a gnome-session, but we warned 'em
            
            ## uncomment the following to brutally kill all of the users processes
            sleep 10
            pkill -u $username  
            
            ## killing gnome-session should be more like:
            #DISPLAY=":0" XAUTHORITY="/tmp/.gdmEQ0V5T" SESSION_MANAGER="local/wretched:/tmp/.ICE-unix/$pid" su -c 'gnome-session-save --kill --silent' $username
            ## but this can still leave processes to cleanup - plus it's not easy to get SESSION_MANAGER
        
}


	# get the usernames and PIDs of sessions

while(true); do
    pidlists=$( ps --no-heading -fC $SESSION_MANAGER | awk 'BEGIN{ FS=" " } { print $1 "," $2 }' )
    for pidlist in $pidlists; do
		
		# split username and pid - FIXME - I bet this would be faster with bash arrays and substitution 
		username=$( echo $pidlist | awk 'BEGIN{ FS=","} { print $1}' )
		pid=$( echo $pidlist | awk 'BEGIN{ FS=","} { print $2}' )
	      
	      # If the user is not enabled, give him $default_limit
	      if [[ ! -e "/var/lib/timekpr/$username" ]]; then
	      	echo $default_limit > /var/lib/timekpr/$username
	      fi
	      
	      if [[ -e "/var/lib/timekpr/$username.time" && `( stat -c '%z' /var/lib/timekpr/$username.time | cut -c9,10 )` == `date +%d` ]]; then
	      	# the time file exists and was last touched today, add $poll_time seconds to it
	            timekpr=$(( `cat /var/lib/timekpr/$username.time` + $poll_time ))
			echo $timekpr > /var/lib/timekpr/$username.time
		else  # the time file is missing or was last touched yesterday
			timekpr=$poll_time
			echo $timekpr > /var/lib/timekpr/$username.time
	      fi

	      echo $username, $pid, $timekpr
	      
	      # Is the user allowed to be loged in at this time?
	      # We take it for granted that if they are allowed to log in all day ($default_limit) then
	      # they can log in whenever they want, ie they are normal users
	      if [ $(cat /var/lib/timekpr/$username) -ne $default_limit ]; then
	      	# Are we out of hours?
		      if ( [ $(date +%k) -lt $from ] || [ $(date +%k) -ge $to ] ); then
		      	# Has the user been given extended log in hours?
		      	if [[ -e "/var/lib/timekpr/$username.allow" ]]; then
		      		# Was the extended log in hours given today?
		      		if [[ $(stat -c '%z' /var/lib/timekpr/$username.allow | cut -c9,10) != $(date +%d) ]]; then
						logOut "Only log in between $from and $to"
						rm /var/lib/timekpr/$username.allow
					fi
				else
					# User has not been given extended log in hours
					logOut "Only log in between $from and $to"
				fi
		      fi
		fi
		
		# Is the limit exeeded
	      if [[ $timekpr -ge `cat /var/lib/timekpr/$username` ]]
	      then
			logOut "Daily time limit"
		fi
	done
	# Wait a while before we check again
	sleep $poll_time
done

```

Limited users can only log in between 7 and 22 (configurable, see line 28 and 29).

In addition I created a script for "rewards". Run it with 'sudo addtime.sh <username> <minutes>' to add <minutes> to <username>s allowed log in time this day (does not expand log in hours (can't log in after 22)).

/usr/local/bin/addtime.sh
```

#!/bin/bash

if [ $# -ne 2 ]; then
	echo "Usage $(basename $0) <username> <time to add in minutes>"
	exit
fi  

adj=$(($2*60))
now=$(cat /var/lib/timekpr/$1.time)
new=$(($now-$adj))
echo $new > /var/lib/timekpr/$1.time
limit=$(cat /var/lib/timekpr/$1)
left=$(($limit-$new))
echo
echo "$2 minute(s) added to ${1}s account."
echo "$1 now has $(($left/60)) minute(s) left."
echo



```



And to expand log in hours we have the following script:
Run it with 'sudo extendlimits.sh <username>' to allow <username> to log in outside of limits (eg before 7 or after 22).

/usr/local/bin/extendlimits.sh
```

#!/bin/bash

if [ $# -ne 1 ]; then
	echo "Usage $(basename $0) <username>"
	exit
fi

if [[ -e "/var/lib/timekpr/$1.allow" ]]; then
	rm "/var/lib/timekpr/$1.allow"
	echo
	echo "$1 has been disallowed to log in outside of normal logon hours"
	echo
else
	touch /var/lib/timekpr/$1.allow
	echo
	echo "$1 has been allowed to log in outside of normal logon hours"
	echo
fi


```


Install the script as stated by the original author. I have not tested it this way, but it works when I run it from console. remember to 'chmod 744' all the scripts.

I recommend you keep $grace_period at least 60 seconds, so that the user has time to save their work and log out.

Richard Stallman once said: "A developer can either deserve a reward or demand it, but not both." You decide if you want to donate or not, I will not demand it :). I had fun making this, and I might get to use it when my daughters grow up (the oldes is only two years old at the moment).

Any way, my PayPal information is even [at] nedberg.net.

---

### Post by crjackson on 2008-08-17
GREAT!  I'll install the new script tonight and see how it goes.  I really thank you for your help.

---

### Post by crjackson on 2008-08-17
.nedberg

I have a problem.  The script won't restart on it's own after a reboot.  My youngest has already discovered that she can reboot when she runs out of time and she then gets unlimited time again (unless I run the scrip from a terminal myself).

I added the line **/usr/local/bin/timekpr & **to **/etc/rc.local** but it's not working.

What am I doing wrong here?

---

### Post by rpainter on 2008-08-17
This is a great script. I needed something like this. Thanks.

---

### Post by crjackson on 2008-08-17
> **rpainter said:**
> This is a great script. I needed something like this. Thanks.

If I knew how to do a feature request to Ubuntu I ask for something like this to built in to the GUI where you set up new user accounts.  It would be great if you could just include some time limits and time restrictions on the user accounts them selves when setting up the account.

---

### Post by stalkier on 2008-08-17
> **crjackson said:**
> If I knew how to do a feature request to Ubuntu I ask for something like this to built in to the GUI where you set up new user accounts.  It would be great if you could just include some time limits and time restrictions on the user accounts them selves when setting up the account.

I agree that would be a huge improvement on security (at home anyways). I also have 3 children underage so something like this is very much needed. :D

---

### Post by shane2peru on 2008-08-17
Ok, this thread is great!  I looked over the script, and must admit, I'm not that script capable!  I don't understand where you would configure the username and who is limited by this script.  How do you set the limited users?   

Shane

As for content filtering, I personally use opendns.com  with ddclient.  You do need to setup an account with opendns.com but it works excellent, and I have been very pleased with it.

PSS:  Oh, I wrote a very simplistic script that limits user times to 45 minutes for KDE desktop (not quite as intense as this script) here it is if anyone can use it or, make it better:
```

#!/bin/sh
# This script will log out a user after 45 minutes on the computer, it requires kshutdown to be installed on the machine. 

sleep 35m

kdialog --title "You have 10 minutes left" --passivepopup "10 minutes remaining" 5
sleep 8m

kdialog --title "You have 2 minutes left" --passivepopup "Please start closing all windows" 10
sleep 110

kdialog --title "You have 10 seconds left" --passivepopup "Close all Windows now." 5
sleep 10

kshutdown -l

exit 0
```

---

### Post by crjackson on 2008-08-17
> **shane2peru said:**
> Ok, this thread is great!  I looked over the script, and must admit, I'm not that script capable!  I don't understand where you would configure the username and who is limited by this script.  How do you set the limited users?   

Shane

As for content filtering, I personally use opendns.com  with ddclient.  You do need to setup an account with opendns.com but it works excellent, and I have been very pleased with it.

PSS:  Oh, I wrote a very simplistic script that limits user times to 45 minutes for KDE desktop (not quite as intense as this script) here it is if anyone can use it or, make it better:
```

#!/bin/sh
# This script will log out a user after 45 minutes on the computer, it requires kshutdown to be installed on the machine. 

sleep 35m

kdialog --title "You have 10 minutes left" --passivepopup "10 minutes remaining" 5
sleep 8m

kdialog --title "You have 2 minutes left" --passivepopup "Please start closing all windows" 10
sleep 110

kdialog --title "You have 10 seconds left" --passivepopup "Close all Windows now." 5
sleep 10

kshutdown -l

exit 0
```

Here is the [**_[SIZE="2"][COLOR="Blue"]timekpr blog[/COLOR][/SIZE]_**]("http://buck-nasty.blogspot.com/2008/09/timekeepr-keep-control-of-your-computer.html") with some basic instructions.  Read that first then the rest of this thread will make sense to you I think.

---

### Post by shane2peru on 2008-08-18
> **crjackson said:**
> Here is a [**_[SIZE="4"][COLOR="Blue"]link to my blog[/COLOR][/SIZE]_**]("http://buck-nasty.blogspot.com/2008/08/how-to-limit-daily-desktop-usage-in.html") with some basic instructions.  Read that first then the rest of this thread will make sense to you I think.

Ahhh, that was extremely helpfull!  Thanks for that link and blog!  Now I can setup accounts for my kids. :)

Shane

---

### Post by crjackson on 2008-08-18
> **shane2peru said:**
> Ahhh, that was extremely helpfull!  Thanks for that link and blog!  Now I can setup accounts for my kids. :)

Shane

Glad it helped.  Maybe if the concept becomes popular enough the devs will create a professional streamlined version built into the Accounts GUI some day.

---

### Post by shane2peru on 2008-08-18
> **crjackson said:**
> Glad it helped.  Maybe if the concept becomes popular enough the devs will create a professional streamlined version built into the Accounts GUI some day.

Yes, we are slipping behind M$ on this, because I heard that they already have this setup on Vista, or something of the nature that limits usage.  I think it is called parental controls or something.  I no longer have M$ on any of my computers, so I'm not sure, just heard about it.

Shane

---

### Post by crjackson on 2008-08-18
> **shane2peru said:**
> Yes, we are slipping behind M$ on this, because I heard that they already have this setup on Vista, or something of the nature that limits usage.  I think it is called parental controls or something.  I no longer have M$ on any of my computers, so I'm not sure, just heard about it.

Shane

Well, if the devs have no interest, I'm sure someone here will eventually make a GUI version for dummies like me.  I've seen many similar requests for something like this that dates back 3-4 years.  It will happen some day I'm sure.

---

### Post by egalvan on 2008-08-18
Is anyone familiar enough with Edubuntu (Educational Ubuntu) or Ubuntu CE (Christian Edition) to know if something similar is already set up?

Quickly scanning the home page; UbuntuCE  *"includes fully integrated web content parental controls powered by Dansguardian. A graphical tool to adjust the parental control settings has also been developed specifically for Ubuntu Christian Edition."*

Edubuntu has been around a couple years, and their is also

 *K12 Linux Terminal Server Project*
 [http://k12ltsp.org/contents.html](http://k12ltsp.org/contents.html)

This is based on Read Hat and the LTSP

 [http://www.ltsp.org/](http://www.ltsp.org/)


I'ms sure the school systems have grappled with this problem, perhaps they have a solutuion.


[COLOR="Red"]And MAJOR THANKS to .nedberg for his work.
 I hope every parent who benefits from his work will consider "tossing him a fin"/ Isn't your child worth it?

[/COLOR]


Sorry I can't do more legwork, I'm off to the firehouse for my shift.

E Galvan, Lt BFD

---

### Post by .nedberg on 2008-08-18
> **crjackson said:**
> .nedberg

I added the line **/usr/local/bin/timekpr & **to **/etc/rc.local** but it's not working.

What am I doing wrong here?

Is the script called /usr/local/bin/timekpr? Not /usr/local/bin/timekpr**.sh**? I will give it a go when I get home from work and the kids are in bed, to see if I can find the problem.

EDIT: I had a look at your blog and this seems to be the reason to your problem if that is exactly what you did!

@egalvan
I work at a school myself and this is not something we would use. Why limit the students log in time? dansguardian on the other hand would be interresting.

---

### Post by .nedberg on 2008-08-18
> **shane2peru said:**
> Ok, this thread is great!  I looked over the script, and must admit, I'm not that script capable!  I don't understand where you would configure the username and who is limited by this script.  How do you set the limited users?   


If you look [here]("http://www.91courtstreet.net/wordpress/2008/02/03/how-to-limit-daily-desktop-usage-in-ubuntu/") you will se that you can create a file at /var/lib/timekpr/<username> to limit an account. In that file you put the total amount of seconds that user is allowed to be logged in each day. A user without a file like this will not be limited.

---

### Post by .nedberg on 2008-08-18
> **crjackson said:**
> .nedberg

I added the line **/usr/local/bin/timekpr & **to **/etc/rc.local** but it's not working.

What am I doing wrong here?

I tested at home just now and it starts after a reeboot. I added the line '/usr/local/bin/timekpr**.sh** &' to /etc/rc.local.

I also updated the script just a little bit. It now makees a 'beep' in addition to showing the notification. This is just to make sure the user is aware and saves his/her work.

I will see if I can make different limits during the weekends :) Should not be a big problem. GUI? I don't know... I'm not that good at making GUI, and I don't know how to do it in Gnome (don't use it, and this script only works with it atm). I see how this would be more "wife friendly" as i call it, so we will have to see...

---

### Post by crjackson on 2008-08-18
> **.nedberg said:**
> I tested at home just now and it starts after a reeboot. I added the line '/usr/local/bin/timekpr**.sh** &' to /etc/rc.local.

I also updated the script just a little bit. It now makees a 'beep' in addition to showing the notification. This is just to make sure the user is aware and saves his/her work.

I will see if I can make different limits during the weekends :) Should not be a big problem. GUI? I don't know... I'm not that good at making GUI, and I don't know how to do it in Gnome (don't use it, and this script only works with it atm). I see how this would be more "wife friendly" as i call it, so we will have to see...

Okay thanks, It must be **.sh** I need.  I do have one question though.  How is midnight represented in the variable?  Is it 0 or 24?

If you are going to play with this some more, could you make a provision for a single username (mine) that would be exempted from all restrictions?  

This may already be addressed by the extendlimits script, but I haven't tried that or the rewards script just yet.  

I've been trying to get this one working on reboot.  Now that I have **.sh** information (duh...  I don't know why I didn't even consider that), I'll add that after work and dig into the other 2 scripts.

---

### Post by Dr Small on 2008-08-18
In response to your question about DansGuardian on your first post, it is a daemon, not a program. You configure it via config files in /etc/dansguardian. But DansGuardian can not run alone. It needs a cache-proxy such as Squid to run.

Here is a great guide on getting Squid and DansGuardian working together, that I followed and it worked:
[http://www.linux.com/articles/113733](http://www.linux.com/articles/113733)

Dr Small

---

### Post by crjackson on 2008-08-18
> **Dr Small said:**
> In response to your question about DansGuardian on your first post, it is a daemon, not a program. You configure it via config files in /etc/dansguardian. But DansGuardian can not run alone. It needs a cache-proxy such as Squid to run.

Here is a great guide on getting Squid and DansGuardian working together, that I followed and it worked:
[http://www.linux.com/articles/113733](http://www.linux.com/articles/113733)

Dr Small

Thanks Dr. Small - I understand that there is a Firefox addon that will allow me to content filter.  I'm going to look into that 1st as it seems less complicated.  I'm really loving this script that .nedberg is tuning to perfection.

Once this is nailed down on my kids compters, I'll be looking into the content issue.  Thanks much for your input.

---

### Post by crjackson on 2008-08-18
> **.nedberg said:**
> you can create a file at /var/lib/timekpr/<username> to limit an account. In that file you put the total amount of seconds that user is allowed to be logged in each day. 

A user without a file like this will not be limited.

It seems you may have answered a question for me before the fact.  I should be able to delete the file for my own username and thus my account wouldn't be restricted.  I'll give this a try tomorrow.

I would assume however, that since the scrip is running on boot, I would still be subjected to allowable login hours.

---

### Post by lswb on 2008-08-18
If you have a router on your home net you should check out its documentation also. Many of them can be configured to limit access by time of day & length of access time, and a password can be set to override the restrictions. Some routers can also be configured to use various content restriction services.

---

### Post by crjackson on 2008-08-18
> **lswb said:**
> If you have a router on your home net you should check out its documentation also. Many of them can be configured to limit access by time of day & length of access time, and a password can be set to override the restrictions. Some routers can also be configured to use various content restriction services.

I do have a router and it's good at what it does.  However, I wanted _computer time_ limited and controlled.  Not just _internet time_.  The router can't do that.

---

### Post by crjackson on 2008-08-18
> **.nedberg said:**
> I will see if I can make different limits during the weekends :) Should not be a big problem. GUI? I don't know... I'm not that good at making GUI, and I don't know how to do it in Gnome (don't use it, and this script only works with it atm). I see how this would be more "wife friendly" as i call it, so we will have to see...

I don't know much about programming but here's what I'm thinking.  timekpr.sh pulls numbers from a file named after it's particular user and fills the variables in the script.  

Would it be possible to either include in the same file (or different if needed) a set of numbers (i.e. 7, 22) which would be checked on login and fill script variables fo setting the login hours of operation for each user.  And even include a provision whereby if it finds the hours string "unlimited" or "0, 0" the user has unlimited login hours against the 24 hour login clock.

just food for thought by a simpleton...  I don't even know if it could work that way or not.

---

### Post by .nedberg on 2008-08-19
@crjackson:

Regarding your first question: If you remove /var/lib/timekpr/<your username> that file will acctually be created again by the script. But, you will be given the time limit of all day, and users with this limit will not be subject to the log in hours limiting (boundaries).

So, if you do not make a file at /var/lib/timekpr/<your username>, you will be able to log in whenever you want. (Or, you could just place the number 86400 (1 day in seconds) in that file.)

I am looking into the possibility of having different time limits and boundaries for every day of the week.

Thank you for the PayPal payment! I am now a "proffesional" developer! :)

---

### Post by mocoloco on 2008-08-19
Regarding content filtering, I messed with Dan's Guardian a year or so ago and found it a pain setting up squid and whatever else. The "gui" in Ubuntu Christian Edition was slight progress but still greatly lacking, mostly it had buttons to open the text files you manually edit. This may have changed by now though.
There's a firefox extension called [procon]("https://addons.mozilla.org/en-US/firefox/addon/1803") that works great for my needs. Lets you block by keywords or using a whitelist.  You can lock it down with a password once it's set up.
My oldest is 6 and only goes to the sites linked from the homepage I made for him, so there's not much concern for him surfing about, but sometimes there are older kids over and it's good not to have to think about where they go because it's whitelist only for his user. So I can't say how well the blacklisting filter works for daily use but I did play around with the other options and would say be sure to check "Render web pages after filtering"; may slightly slow down load times but otherwise pages show for a second before being blocked.

OS X was the first to do built-in parental controls as far as I know and now Vista also has a pretty good set, so yeah, Ubuntu and the Linux world need a good option here to help compete on a family computer.

---

### Post by crjackson on 2008-08-19
> **.nedberg said:**
> @crjackson:

Regarding your first question: If you remove /var/lib/timekpr/<your username> that file will acctually be created again by the script. But, you will be given the time limit of all day, and users with this limit will not be subject to the log in hours limiting (boundaries).

So, if you do not make a file at /var/lib/timekpr/<your username>, you will be able to log in whenever you want. (Or, you could just place the number 86400 (1 day in seconds) in that file.)

I am looking into the possibility of having different time limits and boundaries for every day of the week.

Thank you for the PayPal payment! I am now a "professional" developer! :)

That sounds great.  The original script created a *username file*  with 87000.  It was preventing me from logging in beyond the boundaries.  So am I to understand the file needs to have the exact *(magic)* number of 86400 and not greater to eliminate the login boundaries?

I just changed the **.sh** and it fixed the "load on reboot problem".   I'm changing the value in the *username file* to 86400.  I won't be able to test that until tonight.

---

### Post by .nedberg on 2008-08-19
Content filtering:

I just read a Norwegian artivle about OpenDNS. It can do content filtering!

[http://opendns.com/](http://opendns.com/)

You have to register and enter your IP, and set up your router to use OpenDNS. You can then filter your web traffic!

Have a look here for more info: [http://www.opendns.com/features/content_filtering/](http://www.opendns.com/features/content_filtering/)

---

### Post by .nedberg on 2008-08-19
> **crjackson said:**
> That sounds great.  The original script created a *username file*  with 87000.  It was preventing me from logging in beyond the boundaries.  So am I to understand the file needs to have the exact *(magic)* number of 86400 and not greater to eliminate the login boundaries?

I just changed the **.sh** and it fixed the "load on reboot problem".   I'm changing the value in the *username file* to 86400.  I won't be able to test that until tonight.

Yes, the original script used 8700, I changed it to 86400, exactly one day in seconds. If the file existed it would not be changed and you would be logged out...

---

### Post by BTMark on 2008-08-19
+1 to OpenDNS. I use it on a few of the computers here in the house to block off content. It slowed down browsing a bit, but it sure does the trick, and is easily customized with lists.


.nedberg, great work with this script, really a work of genius.

---

### Post by crjackson on 2008-08-19
> **.nedberg said:**
> Content filtering:

I just read a Norwegian artivle about OpenDNS. It can do content filtering!

[http://opendns.com/](http://opendns.com/)

You have to register and enter your IP, and set up your router to use OpenDNS. You can then filter your web traffic!

Have a look here for more info: [http://www.opendns.com/features/content_filtering/](http://www.opendns.com/features/content_filtering/)

Looking at it now.  Looks great so far, I'll test it out this week.

Regarding timekpr.sh; How is midnight represented in the variable? Is it 0 or 24?

---

### Post by shane2peru on 2008-08-19
+1 Opendns.com

It is great!  Install ddclient [sudo apt-get isntall ddclient]  answer the questions however you want when it installs.  Here is a sample of your ddclient conf file:  ```
sudo gedit /etc/ddclient.conf
```
> 
#
# /etc/ddclient.conf
ssl=yes
pid=/var/run/ddclient.pid
protocol=dyndns2
use=web, web=whatismyip.org
server=updates.opendns.com
login=[COLOR="Red"]username[/COLOR]
password=[COLOR="Red"]password[/COLOR]
[COLOR="Red"]name of your network on your opendns account[/COLOR]

You will need to edit all the red stuff.  You will need to setup an account with opendns, and setup a network.  Then you will need to decide how you want it to filter your computers.  This can also be setup at the router as well.  I then setup ddclient to run as a root crontab every 15 minutes to keep my ip address up to date.  It is fast, secure, and works very well.  I had trouble with DG's restrictivness not allowing me to access my own web site's cpanel, and sometimes uploading to my web page gave me problems.  OpenDNS has worked like a charm for me.

Shane

---

### Post by shane2peru on 2008-08-19
Just my two cents worth here.  When I setup a test user and limited his time to 20 minutes (for testing purposes)  I noticed that the harddrive was been accessed perhaps a bit more than normal or it seemed that way for me.  I recommend that you bumb up the check/poll time to every 60 seconds.  At most a user would gain an extra minute.  Is there anything that would be messed up by using the 60 second poll time?

Shane

---

### Post by .nedberg on 2008-08-20
> **crjackson said:**
> 
Regarding timekpr.sh; How is midnight represented in the variable? Is it 0 or 24?

I am not sure how bash represents midnight, but I guess 0. However, I know how the script will interpret it. If you want to allow someone to log in from midnight, set from=0. If you want them to be able to log in until midnight set to=24.

The script checks if the current hour is larger or equal to from, and if it is less than to. This way it does not matter how bash represents the hour.

I will probably start looking at the posibillity of different limits and boundaries tonight. This will change a lot of how the script works and every user will have to be set up again.

---

### Post by .nedberg on 2008-08-20
> **shane2peru said:**
> Just my two cents worth here.  When I setup a test user and limited his time to 20 minutes (for testing purposes)  I noticed that the harddrive was been accessed perhaps a bit more than normal or it seemed that way for me.  I recommend that you bumb up the check/poll time to every 60 seconds.  At most a user would gain an extra minute.  Is there anything that would be messed up by using the 60 second poll time?

Shane

I agree! Setting poll_time to 60 seconds only gives 40 seconds more to the user. Nothing is messed up by this. grace_period _should_ also be bigger than 60 seconds, but all this will give the user the ability to log in again and again and keep logged in for poll_time+grace_period. I will have a look at putting the logging into memory insted of files, that way poll_time can be as short as we want it to.

---

### Post by crjackson on 2008-08-20
> **.nedberg said:**
> I am not sure how bash represents midnight, but I guess 0. However, I know how the script will interpret it. If you want to allow someone to log in from midnight, set from=0. If you want them to be able to log in until midnight set to=24.

The script checks if the current hour is larger or equal to from, and if it is less than to. This way it does not matter how bash represents the hour.

I will probably start looking at the possibility of different limits and boundaries tonight. This will change a lot of how the script works and every user will have to be set up again.

Sounds good.  I did try 0 (end time) and it booted me off right away.  Setting it to 24 reached the desired result.

---

### Post by crjackson on 2008-08-20
> **.nedberg said:**
> I agree! Setting poll_time to 60 seconds only gives 40 seconds more to the user. Nothing is messed up by this. grace_period _should_ also be bigger than 60 seconds, but all this will give the user the ability to log in again and again and keep logged in for poll_time+grace_period. I will have a look at putting the logging into memory instead of files, that way poll_time can be as short as we want it to.

My Daughter has already been busted doing just that (logging in to get the extra poll+grace time).  They can't get very far though and soon get off the thing.  I'll probably leave the grace as it is.  It's long enough for a child that can't be pried away.  The polling thing however might be something to look at.

---

### Post by crjackson on 2008-08-20
> **.nedberg said:**
> Yes, the original script used 8700, I changed it to 86400, exactly one day in seconds. If the file existed it would not be changed and you would be logged out...

Okay, I changed it to 86400 and it works perfectly as you stated.

---

### Post by .nedberg on 2008-08-21
New version of the script! :)

You can now configure different limits and boundaries for each day of the week. I raised poll_time up to 60 seconds, and kept grace_period at 60 seconds too.

The new version also need a new config file at /var/lib/timekpr/<username> Each of these files should have the following format:
```

limit=( 345 345 345 345 170 345 345 )
from=( 7 7 7 7 7 7 7 )
to=( 22 22 22 22 23 22 22 )

```
where each of the seven numbers on a line stands for the value that certain day of week (sunday monday tuesday...).

An unrestricted user does not need this file, so don't make one for yourself ;).

Here is the new version:

```

#!/bin/bash
###
# timekpr.sh - simple 
# watches gnome sessions and logs them out once the user has exceeded a set, per day limit
# /var/lib/timekpr/$username.time hold a count of seconds user has had a gnome session
# /var/lib/timekpr/$username hold the daily allowed seconds for the user
#
# you may need to install notify-send with: $apt-get install libnotify-bin
#
# Copyright 2008 Chris Jackson <chris@91courtstreet.net>
# Further developed by Even Nedberg <code@nedberg.net>
#
# This program is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# See <http://www.gnu.org/licenses/>. 
#

default_limit=86400 # All day, new users is given this value
grace_period=60 # how much time do we give to let the user log out?
poll_time=60 # How often the script should check the timelogs
#from=7 # When is the users allowed to log in
#to=22 # When is the users no longer allowed to be loged in


#Ubuntu uses alternatives so we look for x-session-manager instead of gnome-session
SESSION_MANAGER=x-session-manager

function logOut() {
## get the display and xauthority used by out session manager
            UDISPLAY=`grep -z DISPLAY \
                /proc/$pid/environ | sed -e 's/DISPLAY=//'`
            XAUTHORITY=`grep -z XAUTHORITY \
                /proc/$pid/environ | sed -e 's/XAUTHORITY=//'`
            
            # find DBUS session bus for this session
            DBUS_SESSION_BUS_ADDRESS=`grep -z DBUS_SESSION_BUS_ADDRESS \
                /proc/$pid/environ | sed -e 's/DBUS_SESSION_BUS_ADDRESS=//'`
            # use it - give a warning, then another one 1/2 way through grace_period
            XAUTHORITY="$XAUTHORITY" DISPLAY="$UDISPLAY" DBUS_SESSION_BUS_ADDRESS="$DBUS_SESSION_BUS_ADDRESS" \
                notify-send --icon=gtk-dialog-warning --urgency=critical -t 10000 "$1" "Your session is about to expire! You have $grace_period sec to save your work and logout."
            sleep $(($grace_period/2))   # FIXME: this gives other sessions a free grace_period added to their accounting
            echo -ne "\007"
            XAUTHORITY="$XAUTHORITY" DISPLAY="$UDISPLAY" DBUS_SESSION_BUS_ADDRESS="$DBUS_SESSION_BUS_ADDRESS" \
                notify-send --icon=gtk-dialog-warning --urgency=critical -t 10000 "$1" "Your session is about to expire! You have $(($grace_period/2)) sec to save your work and logout."
            sleep $(($grace_period/2))   # FIXME: this gives other sessions a free grace_period added to their accounting
	    echo -ne "\007"
            XAUTHORITY="$XAUTHORITY" DISPLAY="$UDISPLAY" DBUS_SESSION_BUS_ADDRESS="$DBUS_SESSION_BUS_ADDRESS" \
                notify-send --icon=gtk-dialog-warning --urgency=critical -t 10 "Shutting Down" "Shutting down session ($pid) now!" 
            # FIXME - should really check to see if user has logged out yet 
            sleep 10
            kill -HUP $pid    #this is a pretty bad way of killing a gnome-session, but we warned 'em
            
            ## uncomment the following to brutally kill all of the users processes
            sleep 10
            pkill -u $username  
            
            ## killing gnome-session should be more like:
            #DISPLAY=":0" XAUTHORITY="/tmp/.gdmEQ0V5T" SESSION_MANAGER="local/wretched:/tmp/.ICE-unix/$pid" su -c 'gnome-session-save --kill --silent' $username
            ## but this can still leave processes to cleanup - plus it's not easy to get SESSION_MANAGER
        
}


	# get the usernames and PIDs of sessions

while(true); do
	
    pidlists=$( ps --no-heading -fC $SESSION_MANAGER | awk 'BEGIN{ FS=" " } { print $1 "," $2 }' )
    for pidlist in $pidlists; do
		
		# split username and pid - FIXME - I bet this would be faster with bash arrays and substitution 
		username=$( echo $pidlist | awk 'BEGIN{ FS=","} { print $1}' )
		pid=$( echo $pidlist | awk 'BEGIN{ FS=","} { print $2}' )
	      
	      # If the user is not enabled, give him $default_limit
	      if [[ -e "/var/lib/timekpr/$username" ]]; then
	      	source /var/lib/timekpr/$username
	      
	      
			if [[ -e "/var/lib/timekpr/$username.time" && `( stat -c '%z' /var/lib/timekpr/$username.time | cut -c9,10 )` == `date +%d` ]]; then
				# the time file exists and was last touched today, add $poll_time seconds to it
			      timekpr=$(( `cat /var/lib/timekpr/$username.time` + $poll_time ))
				echo $timekpr > /var/lib/timekpr/$username.time
			else  # the time file is missing or was last touched yesterday
				timekpr=$poll_time
				echo $timekpr > /var/lib/timekpr/$username.time
			fi

	      	echo $username, $pid, $timekpr
	      
			# Is the user allowed to be loged in at this time?
			# We take it for granted that if they are allowed to log in all day ($default_limit) then
			# they can log in whenever they want, ie they are normal users
			
			index=$(date +%w)
			
			if ( [[ $(date +%k) -lt ${from[$index]} ]] || [[ $(date +%k) -ge ${to[$index]} ]] ); then
				# Has the user been given extended log in hours?
				if [[ -e "/var/lib/timekpr/$username.allow" ]]; then
					# Was the extended log in hours given today?
					# 
					if [[ $(stat -c '%z' /var/lib/timekpr/$username.allow | cut -c1-10) != $(date +%Y-%m-%d) ]]; then
						logOut "Only log in between ${from[$index]} and ${to[$index]}"
						rm /var/lib/timekpr/$username.allow
					fi
				else
					# User has not been given extended log in hours
					logOut "Only log in between ${from[$index]} and ${to[$index]}"
				fi
			fi
			
		
			# Is the limit exeeded
			if [[ $timekpr -ge ${limit[$index]} ]]
			then
				logOut "Daily time limit"
			fi
		fi
	done
	# Wait a while before we check again
	sleep $poll_time
done


```

TODO:
- Find a way to prevent writing logged in time to disk, limit disk usage
- Log out a different way, not just kill the session!
- Make a GUI to configure the users.


For those of you following this thread, attached is a taste of what is to come. This is acctually working, but it is not writing the values to a file, and it does not allow different values for each day at the moment.

---

### Post by crjackson on 2008-08-21
Great!  You're the man!!!  I'm working a 32 hour shift right now, but when I finally get home I'll be updating the script.  I can't wait to try the GUI contorls when you are finished.

[B]1) I notice the use of Parentheses () in the user settings file around the actual settings.  Are these needed or are they there to show that a full group of numbers is to be used when creating the file?

2) Do the other 2 scripts (addtime & extendlimits) still work, or are they now dead?[/B]

---

### Post by crjackson on 2008-08-21
> **.nedberg said:**
> 
TODO:
- Find a way to prevent writing logged in time to disk, limit disk usage
- Log out a different way, not just kill the session!
- Make a GUI to configure the users.

1) Perhaps you can have it read the file time when the session is started, then base calculations against the timer clock, then write the final time to the file when the session is logged out or ended.

2) Currently, when I personally login to one of these timekpr monitored computers, there is an issue with logout (but only on MY master account).  If I log out, I get thrown back to a login screen that asks for MY passowrd (as opposed to 1st asking username).  That would be no problem, except that I can't activate the switch user button with the mouse.  I have found I can select "Switch User" with the Tab key and hitting enter to select.

I have no such problem if I personally never login.  All other users get dumped back to the standard username prompt (as in power-on boot-up) first.  It's only my account that causes this.

Do you think the script has anything to do with that since mine is the only unlimited account and it's the original account?

It's probably just a Gnome bug, but I've never noticed it before and wanted to run it past you.

3) The GUI is looking great.  I noticed that the interface asks for minutes as opposed to seconds that are stored in the timekpr data files.

---

### Post by .nedberg on 2008-08-22
> **crjackson said:**
> 

1) I notice the use of Parentheses () in the user settings file around the actual settings.  Are these needed or are they there to show that a full group of numbers is to be used when creating the file?
Yes, they are needed! It is an array, and they need to be defined that way in bash

> **crjackson said:**
> 
2) Do the other 2 scripts (addtime & extendlimits) still work, or are they now dead?
I didn't have a lot of time to test this version, but I see no reason why they shouldn't work.

---

### Post by .nedberg on 2008-08-22
> **crjackson said:**
> 1) Perhaps you can have it read the file time when the session is started, then base calculations against the timer clock, then write the final time to the file when the session is logged out or ended.

Yes, I am thinking in those ways. But there is a problem with multiuser systems. I need to figure out a way of storing the time a user has been logged in, if this "time" is from today or older, and both values need to be connected to the username. More than one user can be logged in at a time, and this causes some problems. But I am sure we will find a solution!

> **crjackson said:**
> 
2) Currently, when I personally login to one of these timekpr monitored computers, there is an issue with logout (but only on MY master account).  If I log out, I get thrown back to a login screen that asks for MY passowrd (as opposed to 1st asking username).  That would be no problem, except that I can't activate the switch user button with the mouse.  I have found I can select "Switch User" with the Tab key and hitting enter to select.



I have no such problem if I personally never login.  All other users get dumped back to the standard username prompt (as in power-on boot-up) first.  It's only my account that causes this.

Do you think the script has anything to do with that since mine is the only unlimited account and it's the original account?

It's probably just a Gnome bug, but I've never noticed it before and wanted to run it past you.

I don't think that has anything to do with the script. Can't see why it should... Try on that same computer without timekpr runnig?

> **crjackson said:**
> 
3) The GUI is looking great.  I noticed that the interface asks for minutes as opposed to seconds that are stored in the timekpr data files.
The user config file still needs seconds. But I thought it might be easier to configure it via GUI in minutes. At least I find it easier to deside how many minutes I want my kids to stay logged in in stead of seconds.

The GUI is not finished and changing this back to seconds is no problem, nor is changing it to hours...

The GUI also needs a way to reward the kids and extend/disable the boundaries.

---

### Post by crjackson on 2008-08-22
> **.nedberg said:**
> The user config file still needs seconds. But I thought it might be easier to configure it via GUI in minutes. At least I find it easier to deside how many minutes I want my kids to stay logged in in stead of seconds.

The GUI is not finished and changing this back to seconds is no problem, nor is changing it to hours...

The GUI also needs a way to reward the kids and extend/disable the boundaries.

I agree.  Minutes is much better.  There is no need to be percise right down to the second.  Adding the additional features to the GUI for rewards/extend/disable is the Crème De La Crème.

---

### Post by crjackson on 2008-08-22
.nedberg

I noticed that there is a major difference between the script headings where variables are set.  The last 2 lines have a pound sign (#) which appears to comment out those particualr lines. Is that correct?  Is this because those variables are now set inside of the username file?

[CENTER]Original version[/CENTER]
```
default_limit=86400 # All day, new users is given this value
grace_period=60 # how much time do we give to let the user log out?
poll_time=20 # How often the script should check the timelogs
**from=7 #** When is the users allowed to log in
**to=22 #** When is the users no longer allowed to be loged in
```

[CENTER]New version[/CENTER]
```
default_limit=86400 # All day, new users is given this value
grace_period=60 # how much time do we give to let the user log out?
poll_time=60 # How often the script should check the timelogs
**#from=7 #** When is the users allowed to log in
**#to=22 #** When is the users no longer allowed to be loged in
```

---

### Post by crjackson on 2008-08-24
I installed the latest version of the script on one of the kids systems today.  So far so good.

Regarding the log off issue I mentioned earlier.  I've narrowed it down to using Fast User Switching.  If I turn that off and required each user to fully log off before the next person logs on, no problem.

I guess I create a few accounts on my system with out a script to see if I get the same results (I suspect I will).  If so, then I'll be filing a bug report against the fast user switching module.

How goes the progress?

---

### Post by .nedberg on 2008-08-25
> **crjackson said:**
> .nedberg

I noticed that there is a major difference between the script headings where variables are set.  The last 2 lines have a pound sign (#) which appears to comment out those particualr lines. Is that correct?  Is this because those variables are now set inside of the username file?

Yes, that is correct!

---

### Post by .nedberg on 2008-08-25
> **crjackson said:**
> I installed the latest version of the script on one of the kids systems today.  So far so good.
sudo ln -s /home/<your_user_name>/.mythtv/au.xmltv

That is good to hear! I didn't do enough testing on the updated version, so I was curious to see how it worked.

[QUOTE=crjackson;5657960]
How goes the progress?

Not much has happened since last week. I attended another wedding this weekend and that was the reason I just released the new version without much testing.

I will see what I can do this week! Consentrating on the GUI now. Configuring the users is priority #1, then the rewards/extended boundaries.

---

### Post by crjackson on 2008-08-25
> **.nedberg said:**
> That is good to hear! I didn't do enough testing on the updated version, so I was curious to see how it worked.

Not much has happened since last week. I attended another wedding this weekend and that was the reason I just released the new version without much testing.

I will see what I can do this week! Concentrating on the GUI now. Configuring the users is priority #1, then the rewards/extended boundaries.

I just installed the new version today.  I'll know by tonight how it all works out.

I have changed the grace period for log off to 5 seconds.  You won't believe this but my 15 year old daughter keeps logging in for that 1 minuted time.  She gets kicked out and does it over and over again.  I figure with a 5 second grace, this will stop it.  I'm hoping that during login it poles the file for boundaries and will see the 5 second log off limit and kick her off right away.

---

### Post by .nedberg on 2008-08-25
I am thinking of a way of kicking out a user who is logging in without more time immediately. This will have to wait until gui is finished though.

And, never mind that "mythtv" line. I must have pasted something the wrong place...

---

### Post by crjackson on 2008-08-26
> **.nedberg said:**
> I am thinking of a way of kicking out a user who is logging in without more time immediately. This will have to wait until gui is finished though.

Yeah, that would be great.  Right now with the 5 second grace the 2 warnings pop up together and stack one over the other.  It's kind of messy but effective. I agree about the gui though, one task at at time.

---

### Post by .nedberg on 2008-08-30
OK, here we go!

The GUI is "finished". By that I mean that it is working, and I have not discovered any bugs. They are there, I am sure, and the GUI also lacks some options.

It looks a bit different than the screenshot from a previous post.

You can install it by running a single script (run it with sudo):
```

#!/bin/bash
wget nedberg.net/timekpr/addtime.sh -O /usr/local/bin/addtime.sh
wget nedberg.net/timekpr/extendlimits.sh -O /usr/local/bin/extendlimits.sh
wget nedberg.net/timekpr/timekpr.sh -O /usr/local/bin/timekpr.sh
wget nedberg.net/timekpr/timekprGUI.py -O /usr/local/bin/timekprGUI.py
wget nedberg.net/timekpr/Timekpr.glade -O /usr/local/bin/Timekpr.glade
chmod 744 /usr/local/bin/addtime.sh /usr/local/bin/extendlimits.sh /usr/local/bin/timekpr.sh /usr/local/bin/timekprGUI.py
if [ ! -d /var/lib/timekpr ]; then
	mkdir /var/lib/timekpr
fi

```
This script will make sure you have the latest version if I update it later.

You still need to edit /etc/rc.local to make the script run at boot.

Or you can just dl the attached files and place them in /usr/local/bin.

The GUI should be self explanatory, but here is a short how-to:

1. Select the user you wish to configure
2. Check "Use limits" if you want to use timed limits
2.1-1 Set the "Every day" limit or
2.1-2 Check "Configure single days" and set different limits for every day of the week
3. Check "Use boundaries" if you want to control when the user can log in
3.1-1 Set the "Every day" boundaries or
3.1-2 Check "configure single boundaries" and set different boundaries for every day of the week
4. Click "Apply" if you want to configure another user, OK if you are finished or Cancel to just exit.

To un-restrict a user, select the username, uncheck both "Use limits" and "Use boundaries" and click Apply/OK.

NOTE: The GUI is written in Python with GTK bindings. You need PyGTK to make it work. I am not sure if this is installed by default in Ubuntu, but I think so. I don't know much Python and even less GTK. The code needs to be rewritten, it is rather ugly. I concentrated on getting a working version, now we can clean it up and add features!

---

### Post by airtonix on 2008-08-30
> because I heard that they already have this setup on Vista, or something of the nature that limits usage

> OS X was the first to do built-in parental controls as far as I know and now Vista also has a pretty good set

If you have ever setup windows 2000, you will notice that this feature has been there since long before OSX or vista.

Yes this is a lacking feature.

---

### Post by crjackson on 2008-08-30
> **.nedberg said:**
> OK, here we go!

The GUI is "finished". By that I mean that it is working, and I have not discovered any bugs. They are there, I am sure, and the GUI also lacks some options.

It looks a bit different than the screenshot from a previous post.

You can install it by running a single script (run it with sudo):
```

#!/bin/bash
wget nedberg.net/timekpr/addtime.sh -O /usr/local/bin/addtime.sh
wget nedberg.net/timekpr/extendlimits.sh -O /usr/local/bin/extendlimits.sh
wget nedberg.net/timekpr/timekpr.sh -O /usr/local/bin/timekpr.sh
wget nedberg.net/timekpr/timekprGUI.py -O /usr/local/bin/timekprGUI.py
wget nedberg.net/timekpr/Timekpr.glade -O /usr/local/bin/Timekpr.glade
chmod 744 /usr/local/bin/addtime.sh /usr/local/bin/extendlimits.sh /usr/local/bin/timekpr.sh /usr/local/bin/timekprGUI.py
if [ ! -d /var/lib/timekpr ]; then
	mkdir /var/lib/timekpr
fi

```
This script will make sure you have the latest version if I update it later.

You still need to edit /etc/rc.local to make the script run at boot.

Or you can just dl the attached files and place them in /usr/local/bin.

The GUI should be self explanatory, but here is a short how-to:

1. Select the user you wish to configure
2. Check "Use limits" if you want to use timed limits
2.1-1 Set the "Every day" limit or
2.1-2 Check "Configure single days" and set different limits for every day of the week
3. Check "Use boundaries" if you want to control when the user can log in
3.1-1 Set the "Every day" boundaries or
3.1-2 Check "configure single boundaries" and set different boundaries for every day of the week
4. Click "Apply" if you want to configure another user, OK if you are finished or Cancel to just exit.

To un-restrict a user, select the username, uncheck both "Use limits" and "Use boundaries" and click Apply/OK.

NOTE: The GUI is written in Python with GTK bindings. You need PyGTK to make it work. I am not sure if this is installed by default in Ubuntu, but I think so. I don't know much Python and even less GTK. The code needs to be rewritten, it is rather ugly. I concentrated on getting a working version, now we can clean it up and add features!

Sounds great I'll give it a spin shortly.  I just had a tragic death in the family (3 actually. It was a train/car wreck) and I'll be going out of town for a bit to pay my respects.

I really appreciate your efforts and hard work as do many others.  I have several people at work using the previous version on their systems at home.

Thanks again.

---

### Post by crjackson on 2008-09-03
The new GUI works great. I tried to make a launcher for it but it wouldn't work.  I found that currently it requires glade to be in the same physical location as the GUI.  Do you know of a way to make a launcher (to be placed in system>administration).  It's a trivial consideration but suggested by (you guessed it...) My Wife.

---

### Post by steve_m1999 on 2008-09-07
I cannot get the installer to work I think that I have followed the directions. Here is what comes up in terminal window.

steve@mpc:~$ cd Desktop
steve@mpc:~/Desktop$ sudo bash timekpr_install.sh
--11:33:56--  [http://nedberg.net/timekpr/addtime.sh](http://nedberg.net/timekpr/addtime.sh)
'          => `/usr/local/bin/addtime.sh
Resolving nedberg.net... 195.47.247.59
Connecting to nedberg.net|195.47.247.59|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 377 [text/x-sh]

100%[====================================>] 377           --.--K/s             

' saved [377/377]B/s) - `/usr/local/bin/addtime.sh

--11:33:56--  [http://nedberg.net/timekpr/extendlimits.sh](http://nedberg.net/timekpr/extendlimits.sh)
'          => `/usr/local/bin/extendlimits.sh
Resolving nedberg.net... 195.47.247.59
Connecting to nedberg.net|195.47.247.59|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 368 [text/x-sh]

100%[====================================>] 368           --.--K/s             

' saved [368/368]B/s) - `/usr/local/bin/extendlimits.sh

--11:33:57--  [http://nedberg.net/timekpr/timekpr.sh](http://nedberg.net/timekpr/timekpr.sh)
'          => `/usr/local/bin/timekpr.sh
Resolving nedberg.net... 195.47.247.59
Connecting to nedberg.net|195.47.247.59|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 6,056 (5.9K) [text/x-sh]

100%[====================================>] 6,056         29.25K/s             

' saved [6056/6056]s) - `/usr/local/bin/timekpr.sh

--11:33:57--  [http://nedberg.net/timekpr/timekprGUI.py](http://nedberg.net/timekpr/timekprGUI.py)
'          => `/usr/local/bin/timekprGUI.py
Resolving nedberg.net... 195.47.247.59
Connecting to nedberg.net|195.47.247.59|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 10,763 (11K) [text/x-python]

100%[====================================>] 10,763        33.47K/s             

' saved [10763/10763] - `/usr/local/bin/timekprGUI.py

--11:33:58--  [http://nedberg.net/timekpr/Timekpr.glade](http://nedberg.net/timekpr/Timekpr.glade)
'          => `/usr/local/bin/Timekpr.glade
Resolving nedberg.net... 195.47.247.59
Connecting to nedberg.net|195.47.247.59|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 40,929 (40K) [text/plain]

100%[====================================>] 40,929        37.96K/s             

' saved [40929/40929] - `/usr/local/bin/Timekpr.glade

chmod: cannot access `/usr/local/bin/addtime.sh': No such file or directory
chmod: cannot access `/usr/local/bin/extendlimits.sh': No such file or directory
chmod: cannot access `/usr/local/bin/timekpr.sh': No such file or directory
timekpr_install.sh: line 10: syntax error near unexpected token `fi'
timekpr_install.sh: line 10: `fi'


It does create files addtime, extendtime, timekpr.sh, timekpr.glade, timekprGUI.py.

I am a nubie so I would appreciate any help.
Thanks Steve

---

### Post by crjackson on 2008-09-07
> **steve_m1999 said:**
> I cannot get the installer to work I think that I have followed the directions. Here is what comes up in terminal window.

steve@mpc:~$ cd Desktop
steve@mpc:~/Desktop$ sudo bash timekpr_install.sh
--11:33:56--  [http://nedberg.net/timekpr/addtime.sh](http://nedberg.net/timekpr/addtime.sh)
'          => `/usr/local/bin/addtime.sh
Resolving nedberg.net... 195.47.247.59
Connecting to nedberg.net|195.47.247.59|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 377 [text/x-sh]

100%[====================================>] 377           --.--K/s             

' saved [377/377]B/s) - `/usr/local/bin/addtime.sh

--11:33:56--  [http://nedberg.net/timekpr/extendlimits.sh](http://nedberg.net/timekpr/extendlimits.sh)
'          => `/usr/local/bin/extendlimits.sh
Resolving nedberg.net... 195.47.247.59
Connecting to nedberg.net|195.47.247.59|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 368 [text/x-sh]

100%[====================================>] 368           --.--K/s             

' saved [368/368]B/s) - `/usr/local/bin/extendlimits.sh

--11:33:57--  [http://nedberg.net/timekpr/timekpr.sh](http://nedberg.net/timekpr/timekpr.sh)
'          => `/usr/local/bin/timekpr.sh
Resolving nedberg.net... 195.47.247.59
Connecting to nedberg.net|195.47.247.59|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 6,056 (5.9K) [text/x-sh]

100%[====================================>] 6,056         29.25K/s             

' saved [6056/6056]s) - `/usr/local/bin/timekpr.sh

--11:33:57--  [http://nedberg.net/timekpr/timekprGUI.py](http://nedberg.net/timekpr/timekprGUI.py)
'          => `/usr/local/bin/timekprGUI.py
Resolving nedberg.net... 195.47.247.59
Connecting to nedberg.net|195.47.247.59|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 10,763 (11K) [text/x-python]

100%[====================================>] 10,763        33.47K/s             

' saved [10763/10763] - `/usr/local/bin/timekprGUI.py

--11:33:58--  [http://nedberg.net/timekpr/Timekpr.glade](http://nedberg.net/timekpr/Timekpr.glade)
'          => `/usr/local/bin/Timekpr.glade
Resolving nedberg.net... 195.47.247.59
Connecting to nedberg.net|195.47.247.59|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 40,929 (40K) [text/plain]

100%[====================================>] 40,929        37.96K/s             

' saved [40929/40929] - `/usr/local/bin/Timekpr.glade

chmod: cannot access `/usr/local/bin/addtime.sh': No such file or directory
chmod: cannot access `/usr/local/bin/extendlimits.sh': No such file or directory
chmod: cannot access `/usr/local/bin/timekpr.sh': No such file or directory
timekpr_install.sh: line 10: syntax error near unexpected token `fi'
timekpr_install.sh: line 10: `fi'


It does create files addtime, extendtime, timekpr.sh, timekpr.glade, timekprGUI.py.

I am a nubie so I would appreciate any help.
Thanks Steve

The problem seems to be that you don't have a directory on your system already called '/usr/local/bin/'.

Download the script under my last post called timekpr_install.sh and run it with sudo bash.  I just modified the script a little to create the folders your need.

---

### Post by DGortze380 on 2008-09-07
> **crjackson said:**
> The problem seems to be that you don't have a directory on your system already called '/usr/local/bin/'.

Download the script under my last post called timekpr_install.sh and run it with sudo bash.  I just modified the script a little to create the folders your need.

note: haven't read the whole thread...

seems like there's another issue with the logic in the script itself.

```

timekpr_install.sh: line 10: syntax error near unexpected token `fi'
timekpr_install.sh: line 10: `fi'

```

---

### Post by crjackson on 2008-09-07
> **DGortze380 said:**
> note: haven't read the whole thread...

seems like there's another issue with the logic in the script itself.

```

timekpr_install.sh: line 10: syntax error near unexpected token `fi'
timekpr_install.sh: line 10: `fi'

```

Did you try it again?  I got that error too at first and it went away after re-saving with gedit.

I just downloaded the file and ran it on a freshly installed system.  It worked perfectly for me.

---

### Post by steve_m1999 on 2008-09-07
That seemed to work but I had to gksu nautilus to get it to run in terminal.
Thanks for the help
Steve

---

### Post by crjackson on 2008-09-08
> **steve_m1999 said:**
> That seemed to work but I had to gksu nautilus to get it to run in terminal.
Thanks for the help
Steve

I should have mentioned that.  That's exactly how I do it.  I make a bookmark in the "root nautilus" menu so I can got straight to it.

I'm hoping that .nedberg will return when he has the time and help make a menu launcher for it.

---

### Post by crjackson on 2008-09-08
Post no longer needed.

---

### Post by billgoldberg on 2008-09-08
> **crjackson said:**
> Here's the deal,

I've got 4 underage children in the house and I need some software controls.  My wife was at a friends house and learned that their computers are configured to do the following.

Each child has there own Time limited user account.  Each account is allowed only a predefined about of user time.  The way it works is like this.  If the user is allowed 120 minutes, they can login and out as many times as they like, but the minutes are logged and when the limit is reached their access expires.

The next issue is content filtering.  I found dansguardian in the repositories and installed it.  The problem is I can't find any menu entries to activate it, and it also doesn't run by typing dansguardian from the terminal.

How do I activate this thing so that I can configure it?

Thanks...

This kind of thing isn't good for children.

Let them see the world as it really is instead of trying to shelter them from everything.

---

### Post by crjackson on 2008-09-08
> **billgoldberg said:**
> This kind of thing isn't good for children.

Let them see the world as it really is instead of trying to shelter them from everything.

Sorry Bill - Go hunt for a Knee-Jerk reaction elsewhere.  This is a support thread.

---

### Post by .nedberg on 2008-09-08
To install the script try this:
```

#!/bin/bash
if [ ! -d /usr/local/bin ]; then
sudo mkdir /usr/local/bin
fi
wget nedberg.net/timekpr/addtime.sh -O /usr/local/bin/addtime.sh
wget nedberg.net/timekpr/extendlimits.sh -O /usr/local/bin/extendlimits.sh
wget nedberg.net/timekpr/timekpr.sh -O /usr/local/bin/timekpr.sh
wget nedberg.net/timekpr/timekprGUI.py -O /usr/local/bin/timekprGUI.py
wget nedberg.net/timekpr/Timekpr.glade -O /usr/local/bin/Timekpr.glade
chmod 744 /usr/local/bin/addtime.sh /usr/local/bin/extendlimits.sh /usr/local/bin/timekpr.sh /usr/local/bin/timekprGUI.py
if [ ! -d /var/lib/timekpr ]; then
mkdir /var/lib/timekpr
fi

```
I thought the folder /usr/local/bin already existed... This version checks if it exists, and only creates it if it doesn't.

Launcher:
You should launch the GUI with 'gksudo /usr/local/bin/timekprGUI.py'.
In Ubuntu/Gnome you can right click your menu and select "Edit Menus", then add a new item wherever you want it. Make the command 'gksudo /usr/local/bin/timekprGUI.py', name it what ever you want and select an icon. You need to do this as your own user, and it cannot be run as an unprivileged user (make sure your kids are not in the sudoers group!).

---

### Post by crjackson on 2008-09-08
> **.nedberg said:**
> To install the script try this:
```

#!/bin/bash
if [ ! -d /usr/local/bin ]; then
sudo mkdir /usr/local/bin
fi
wget nedberg.net/timekpr/addtime.sh -O /usr/local/bin/addtime.sh
wget nedberg.net/timekpr/extendlimits.sh -O /usr/local/bin/extendlimits.sh
wget nedberg.net/timekpr/timekpr.sh -O /usr/local/bin/timekpr.sh
wget nedberg.net/timekpr/timekprGUI.py -O /usr/local/bin/timekprGUI.py
wget nedberg.net/timekpr/Timekpr.glade -O /usr/local/bin/Timekpr.glade
chmod 744 /usr/local/bin/addtime.sh /usr/local/bin/extendlimits.sh /usr/local/bin/timekpr.sh /usr/local/bin/timekprGUI.py
if [ ! -d /var/lib/timekpr ]; then
mkdir /var/lib/timekpr
fi

```
I thought the folder /usr/local/bin already existed... This version checks if it exists, and only creates it if it doesn't.

Launcher:
You should launch the GUI with 'gksudo /usr/local/bin/timekprGUI.py'.
In Ubuntu/Gnome you can right click your menu and select "Edit Menus", then add a new item wherever you want it. Make the command 'gksudo /usr/local/bin/timekprGUI.py', name it what ever you want and select an icon. You need to do this as your own user, and it cannot be run as an unprivileged user (make sure your kids are not in the sudoers group!).

I didn't know how to make that thing actually check for the existance of a directory :(  so I just told it to make one.  I'm glad you jumped in and fixed it up.

I tried the gksudo thing the other day and it didn't work.  It launched the GUI, but it would modify the file settings.  I'll give that a try again.  I was tired and may have done wrong somehow.

OH NO!!  No Kiddies with sudoers privileges - I haven't even given that to the wife yet.

---

### Post by crjackson on 2008-09-08
> **.nedberg said:**
> 
Launcher:
You should launch the GUI with 'gksudo /usr/local/bin/timekprGUI.py'.
In Ubuntu/Gnome you can right click your menu and select "Edit Menus", then add a new item wherever you want it. Make the command 'gksudo /usr/local/bin/timekprGUI.py', name it what ever you want and select an icon. You need to do this as your own user, and it cannot be run as an unprivileged user (make sure your kids are not in the sudoers group!).

I tried and can't get a Launcher to work with gksudo or sudo.  I've seen this before and it has something to do with being a script.  If you figure out how to make that work, please let me know.

---

### Post by crjackson on 2008-09-09
Well, I did find I can run it from a terminal by typing:
```
sudo bash -c "cd /usr/local/bin/ ; timekprGUI.py"
```

I even made a launcher & a script on the desktop with that command and still can't get it to work (other than in a terminal screen).

Place the attached scrip on your desktop and make it executable. Then click on the file and tell it to run in terminal.  Just clicking run won't work, it must run in terminal.

---

### Post by .nedberg on 2008-09-09
Not sure why your launcher will not work.

I just went to System -> Preferences -> Main Menu, I then added a 'New Item' under System -> Administration. In the launcher properties I selected:
Type: Application
Name: TimeKPR
Command: gksu /usr/local/bin/timekprGUI.py
Comment: Open timekpr configuration

This should work, you need to do it as your own user and it will not run from one of your kids account. So you need to log in and start it.

Oh, and I updated the GUI a bit, run the install script to get the new version!

WARNING: If you use the new GUI to reward/disable limits for a day you should press 'Cancel' when you want to exit. Pressing 'OK' will erase the settings for the currently selected user. I need to make the GUI read the settings and show them when a user is selected.

---

### Post by crjackson on 2008-09-09
> **.nedberg said:**
> Not sure why your launcher will not work.

I just went to System -> Preferences -> Main Menu, I then added a 'New Item' under System -> Administration. In the launcher properties I selected:
Type: Application
Name: TimeKPR
Command: gksu /usr/local/bin/timekprGUI.py
Comment: Open timekpr configuration

This should work, you need to do it as your own user and it will not run from one of your kids account. So you need to log in and start it.

Oh, and I updated the GUI a bit, run the install script to get the new version!


WARNING: If you use the new GUI to reward/disable limits for a day you should press 'Cancel' when you want to exit. Pressing 'OK' will erase the settings for the currently selected user. I need to make the GUI read the settings and show them when a user is selected.

Cool, I try the launcher again.  Is there a difference between gksudo, and gksu?  I didn't try gksu and that might be my problem.  In fact, I've never tried gksu for anything.

---

### Post by crjackson on 2008-09-09
Got the update, very nice...

Launcher thing just not working here (4 different systems).  I have no idea what it could be.

It won't run for me.  Here is the error I get from the terminal screen:
```
charles@charles-laptop:~$ gksu /usr/local/bin/timekprGUI.py
Traceback (most recent call last):
  File "/usr/local/bin/timekprGUI.py", line 235, in <module>
    tkg = timekprGUI()
  File "/usr/local/bin/timekprGUI.py", line 22, in __init__
    self.wTree = gtk.glade.XML(gladefile, "window1")
RuntimeError: could not create GladeXML object
charles@charles-laptop:~$
```

---

### Post by .nedberg on 2008-09-10
Looks like there might be a problem with your path.

Try
```

echo $PATH

```
and
```

sudo echo $PATH

```
Is /usr/local/bin listed? I don't remember changing my PATH variable, but if you tested on four systems then I probably did (if this is the problem...).

---

### Post by .nedberg on 2008-09-10
> **crjackson said:**
> Cool, I try the launcher again.  Is there a difference between gksudo, and gksu?  I didn't try gksu and that might be my problem.  In fact, I've never tried gksu for anything.

No, I don't think there is a difference. In fact I think gksudo is just an alias for gksu.

---

### Post by panther_sn on 2008-09-10
> **crjackson said:**
> Got the update, very nice...

Launcher thing just not working here (4 different systems).  I have no idea what it could be.

It won't run for me.  Here is the error I get from the terminal screen:
```
charles@charles-laptop:~$ gksu /usr/local/bin/timekprGUI.py
Traceback (most recent call last):
  File "/usr/local/bin/timekprGUI.py", line 235, in <module>
    tkg = timekprGUI()
  File "/usr/local/bin/timekprGUI.py", line 22, in __init__
    self.wTree = gtk.glade.XML(gladefile, "window1")
RuntimeError: could not create GladeXML object
charles@charles-laptop:~$
```


I am having the same probs, and checked my $PATH
and the response is 
```

taz@taz-desktop:~$ echo $PATH
/home/taz/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
taz@taz-desktop:~$ sudo echo $PATH
[sudo] password for taz: 
/home/taz/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

```
Any Ideas?

---

### Post by .nedberg on 2008-09-10
> **panther_sn said:**
> Hi I just installed these scripts and when I try to run  gksudo /usr/local/bin/timekprGUI.py

i get 
```

Traceback (most recent call last):
  File "/usr/local/bin/timekprGUI.py", line 235, in <module>
    tkg = timekprGUI()
  File "/usr/local/bin/timekprGUI.py", line 22, in __init__
    self.wTree = gtk.glade.XML(gladefile, "window1")
RuntimeError: could not create GladeXML object


```

Anyidea what this means or how I fix it


As you are the second person having this problem I am starting to think I messed up with the new version. Will have a look at it when I get home from work!

---

### Post by crjackson on 2008-09-10
It does the same thing on the older version too.  Here is the output of the path commands:

```
charles@MSI-K8N-NEO4-PLAT-SLI:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games


charles@MSI-K8N-NEO4-PLAT-SLI:~$ sudo echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
charles@MSI-K8N-NEO4-PLAT-SLI:~$ 
```

---

### Post by panther_sn on 2008-09-10
my output was```

taz@taz-desktop:~$ echo $PATH
/home/taz/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
taz@taz-desktop:~$ sudo echo $PATH
[sudo] password for taz: 
/home/taz/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

```

---

### Post by .nedberg on 2008-09-10
Could those of you having problems try again with the new version (run the installer script in an above post).

I think the Python script would look in /home/username for the .glade file and on my system it would find it. Therefor I did not get any errors, and the launcher worked for me. Renaming this file gave me the same error as you got. I fixed the script to use full path to the .glade file and successfully installed and ran it on my machine.

Give it a go!

---

### Post by .nedberg on 2008-09-10
Another small change.

1. Removed the 'OK' button.
2. Changed from 'Cancel' to 'Exit'

This is just temporary to prevent users from clicking 'OK' when they just wanted to reward or disable boundaries for a day. The 'OK' button might come back later (if it is needed at all...).

---

### Post by crjackson on 2008-09-10
10-4, I'll test it out when I get home tonight.

So, as it stands now, there is an APPLY button and an EXIT button.  To make global changes I would make my adjustments and then click apply > exit.

To just add rewards minutes or release boundires for the day, select user>adjust reward time>click reward button>click exit button.

---

### Post by crjackson on 2008-09-10
Just ran the install script again, the buttons are APPLY and Quit.  The launcher works perfectly now, and all is right with the world...  :)

.nedberg

I added a line to the install script to install libnotify.bin  Have a look and see if you think this is okay.  I just remember when I first installed the original script I didn't notice the commented section that to told me I may need to install libnotify.bin.  Because of this I got no notifications until you pointed me in the right direction, so I figured it might be a good idea to ensure it's installed regardless.  What do you think?

```
#!/bin/bash
if [ ! -d /usr/local/bin ]; then
sudo mkdir /usr/local/bin
fi
apt-get install libnotify-bin
wget nedberg.net/timekpr/addtime.sh -O /usr/local/bin/addtime.sh
wget nedberg.net/timekpr/extendlimits.sh -O /usr/local/bin/extendlimits.sh
wget nedberg.net/timekpr/timekpr.sh -O /usr/local/bin/timekpr.sh
wget nedberg.net/timekpr/timekprGUI.py -O /usr/local/bin/timekprGUI.py
wget nedberg.net/timekpr/Timekpr.glade -O /usr/local/bin/Timekpr.glade
chmod 744 /usr/local/bin/addtime.sh /usr/local/bin/extendlimits.sh /usr/local/bin/timekpr.sh /usr/local/bin/timekprGUI.py
if [ ! -d /var/lib/timekpr ]; then
mkdir /var/lib/timekpr
fi
```

---

### Post by panther_sn on 2008-09-10
Yep works beautifully awesome thanks .nedberg  just one question on the GUI should it say seconds or minutes for the time limits?

---

### Post by .nedberg on 2008-09-11
> **panther_sn said:**
> Yep works beautifully awesome thanks .nedberg  just one question on the GUI should it say seconds or minutes for the time limits?

The GUI uses minutes, while the script uses seconds. The calculations from minutes to seconds are done automagickal!

---

### Post by .nedberg on 2008-09-11
> **crjackson said:**
> 10-4, I'll test it out when I get home tonight.

So, as it stands now, there is an APPLY button and an EXIT button.  To make global changes I would make my adjustments and then click apply > exit.

To just add rewards minutes or release boundires for the day, select user>adjust reward time>click reward button>click exit button.

That is correct!

---

### Post by .nedberg on 2008-09-11
> **crjackson said:**
> Just ran the install script again, the buttons are APPLY and Quit.  The launcher works perfectly now, and all is right with the world...  :)

.nedberg

I added a line to the install script to install libnotify.bin  Have a look and see if you think this is okay.  I just remember when I first installed the original script I didn't notice the commented section that to told me I may need to install libnotify.bin.  Because of this I got no notifications until you pointed me in the right direction, so I figured it might be a good idea to ensure it's installed regardless.  What do you think?


Not a bad idea! I will have a look at how to check if it is installed and install if it is not. Not sure if apt-get returns an error if it is already installed.

---

### Post by crjackson on 2008-09-11
> **.nedberg said:**
> Not a bad idea! I will have a look at how to check if it is installed and install if it is not. Not sure if apt-get returns an error if it is already installed.

apt-get checks and if it's already installed it takes no action other than reporting it's already installed.  I was just thinking there may be a more efficient way doing this.

---

### Post by crjackson on 2008-09-13
Tonight was the acid test at my house.  The wife called me while I was at work and wanted to extend the time allowed for one of the kids.  I walked her through the "Disable Limits Today" use from the desktop launcher and it was perfect.

She was very pleased.  Tomorrow will be a good day  :)

---

### Post by crjackson on 2008-09-14
I spoke too soon.  There was confusion over the way the buttons work and she ended up clicking Apply which gave him unlimited use.  See what you think about this idea:

[LIST=1]
[*]Change the "Reward" button to read "Apply Reward"
[*]Change the "Disable limits today" button to "Release Boundaries"
[*]Change the "Quit" button to read "Exit"
[*]Change the "Apply" button to read "Apply Limits/Boundaries"
[/LIST]

Or some similar wording.  If it's able to load the previous settings for each user as you mentioned, that would prevent someone from accidently granting unlimited access by in inadvertently clicking the Apply button too.

---

### Post by .nedberg on 2008-09-15
The "Wife test" is a though one. I think we did well!

I will have a look at changing the wording on the buttons. 1. and 2. is easy and good ideas, 3. and 4, I don't know. Those are GTK standard buttons and can have the icons. Reading the settings is probably a better idea. I will have a look at it!

On the subject of wording: Is limits/boundaries good words to use? As I am not a native English/American speaker I think you might come up with a better solution than me.

---

### Post by crjackson on 2008-09-15
> **.nedberg said:**
> The "Wife test" is a though one. I think we did well!

I will have a look at changing the wording on the buttons. 1. and 2. is easy and good ideas, 3. and 4, I don't know. Those are GTK standard buttons and can have the icons. Reading the settings is probably a better idea. I will have a look at it!

On the subject of wording: Is limits/boundaries good words to use? As I am not a native English/American speaker I think you might come up with a better solution than me.

Don't bother with 3 / 4 then.  Wording of Limits / Boundaries...  Seems that Boundaries might be polished up a bit, but I'll have to think on that one.

---

### Post by forger on 2008-09-15
Could anyone debianize this and upload it at launchpad? I think this could be the next great addition for ubuntu (9.04) jaunty jackalope :)

---

### Post by .nedberg on 2008-09-15
> **forger said:**
> Could debianize this and upload it at launchpad? I think this could be the next great addition for ubuntu (9.04) jaunty jackalope :)

Oh my! That would be cool! But I do not think it is ready for prime time yet. It is still a bit rough around the edges and things will probably change a lot.

That said, inclusion in Ubuntu would be great!

---

### Post by forger on 2008-09-15
It would be better in launchpad, in case a lot of developers take interest in this, you could see who's adding what part of code:
[https://code.launchpad.net/](https://code.launchpad.net/)

Bazaar (the version control system) has a 5-minute-tutorial to get you started :)
[http://doc.bazaar-vcs.org/bzr.dev/en/mini-tutorial/index.html](http://doc.bazaar-vcs.org/bzr.dev/en/mini-tutorial/index.html)

I've looked at the script & GUI, it's great!

By the way, you have the path "/usr/bin/" in the GUI's .py file for the other "parts" of timekpr - remove them, that way it will read the script in the current directory

Also, you look in /home/ for users. You could make something in python out of this bash script:
```
cat /etc/passwd | cut -d: -f 1,3,6 | grep '1[0-9][0-9][0-9]\|5[0-9][0-9]' | grep "/home" | cut -d: -f1
```
(It creates a user list of UserIDs 1000+, default for Ubuntu, or 500+,default for Fedora)

I guess you could also use:
```
cat /etc/passwd | cut -d: -f 1,3,6 | grep "/home" | cut -d: -f1
```
..to get all users with "home", but that can include users created by the system, like syslog

---

### Post by forger on 2008-09-15
Also, can you set in the notification message the time left to be in minutes instead of seconds?

---

### Post by Dr Small on 2008-09-15
> **forger said:**
> It would be better in launchpad, in case a lot of developers take interest in this, you could see who's adding what part of code:
[https://code.launchpad.net/](https://code.launchpad.net/)

Bazaar (the version control system) has a 5-minute-tutorial to get you started :)
[http://doc.bazaar-vcs.org/bzr.dev/en/mini-tutorial/index.html](http://doc.bazaar-vcs.org/bzr.dev/en/mini-tutorial/index.html)


I have also written a guide for Bazaar, here at the forums. It may be useful:
[http://ubuntuforums.org/showthread.php?t=916132](http://ubuntuforums.org/showthread.php?t=916132)

Start a new project at Launchpad and then you can use bazaar for uploading the source. Then the community can maintain it, and eventually it may get in a version of ubuntu :)

---

### Post by .nedberg on 2008-09-15
OK

Launchpad project is found at [https://launchpad.net/timekpr](https://launchpad.net/timekpr).

I never used bazaar before so I might have done something wrong, but I think I got it! At least the code is in launchpad. Also I never used launchpad for a project before so this is all new to me.

I will try to make some updates soon.

---

### Post by .nedberg on 2008-09-15
> **forger said:**
> 
By the way, you have the path "/usr/bin/" in the GUI's .py file for the other "parts" of timekpr - remove them, that way it will read the script in the current directory

Initially I wrote it like that, but it did not work for anyone but me. I agree that using absolute paths is not a good idea and I need to figure this one out. It looked like it would look in the current working directory, not /usr/local/bin. Will fix this!
> **forger said:**
> 
Also, you look in /home/ for users. You could make something in python out of this bash script:
```
cat /etc/passwd | cut -d: -f 1,3,6 | grep '1[0-9][0-9][0-9]\|5[0-9][0-9]' | grep "/home" | cut -d: -f1
```
(It creates a user list of UserIDs 1000+, default for Ubuntu, or 500+,default for Fedora)

I guess you could also use:
```
cat /etc/passwd | cut -d: -f 1,3,6 | grep "/home" | cut -d: -f1
```
..to get all users with "home", but that can include users created by the system, like syslog
Thanks, I knew I should use /etc/passwd to find the users, but didn't have the time or energy to figure out the regex. I will have a look at the above code!


Thanks for your feedback! The script generally needs to be rewritten. I will probably try to change it to python some day...

---

### Post by .nedberg on 2008-09-15
> **forger said:**
> Also, can you set in the notification message the time left to be in minutes instead of seconds?

As the script is now it only has a 60 second grace period. This _should_ be longer, but there is a problem because a user is granted a new grace period on each log in. I would like to kick it up to 3-4 minutes, use several notifications, and prevent a new log in. Then I agree that notifying in minutes would make more sense. But as it stands now I think seconds are better

---

### Post by egalvan on 2008-09-15
> **crjackson said:**
> ,..Is there a difference between gksudo, and gksu?  I didn't try gksu and that might be my problem.  In fact, I've never tried gksu for anything.

A few days behind...
hope you don't mind... :)

The sudo command stands for "superuser do". 

The su command stands for "switch user", and allows you to become another user...if you don't provide a user, the su command defaults to the root account,


GKsu is a front end for su
GKsudo is a front end for sudo

[B]
Above ginned from assorted Linux docs.[/B]

---

### Post by .nedberg on 2008-09-15
New version. Get it from [launchpad]("https://launchpad.net/timekpr") or with the install script from an earlier post.

New or changed in this version:
- Notifications now show remaining time in minutes
- Grace period changed to 120 seconds
- Poll time changed to 45 seconds
- A user that has exceeded the daily limit will be kicked out after poll_time seconds! :) (hopefully making an end to users logging in again and again). This does not yet work when outside of boundaries!

---

### Post by crjackson on 2008-09-15
> **.nedberg said:**
> New version. Get it from [launchpad]("https://launchpad.net/timekpr") or with the install script from an earlier post.

New or changed in this version:
- Notifications now show remaining time in minutes
- Grace period changed to 120 seconds
- Poll time changed to 45 seconds
- A user that has exceeded the daily limit will be kicked out after poll_time seconds! :) (hopefully making an end to users logging in again and again). This does not yet work when outside of boundaries!

This is great Evan. Is it already available on launchpad?  I went to the link, but I didn't see any files in the dowload area.

I'll run the install script tonight and check out the changes.

---

### Post by crjackson on 2008-09-16
No longer needed

---

### Post by .nedberg on 2008-09-16
> **crjackson said:**
> This is great Evan. Is it already available on launchpad?  I went to the link, but I didn't see any files in the dowload area.

I'll run the install script tonight and check out the changes.

You need to go to the project page, select 'code' in the menu and then browse the source code. I need to make it avaliable at the download area to...

---

### Post by crjackson on 2008-09-16
> **.nedberg said:**
> You need to go to the project page, select 'code' in the menu and then browse the source code. I need to make it avaliable at the download area to...

ahh... I see it now.  Very cool...

---

### Post by forger on 2008-09-17
why did you choose LGPL license in launchpad by the way? :confused:

---

### Post by forger on 2008-09-17
I made a deb package: [ATTACH]85513[/ATTACH]
Do try it! :)

I made some changes of executables and filenames, as I believe it's better this way:
install_timekpr.sh -> (removed)
addtime.sh -> /usr/bin/timekpr-addtime
extendlimits.sh -> /usr/bin/timekpr-extendlimits
Timekpr.glade -> /usr/share/timekpr/timekpr.glade
timekprGUI.py -> /usr/bin/timekpr-gui
timekpr.sh -> /usr/bin/timekpr

About the licenses, checkout:
```
cat /usr/share/doc/timekpr/copyright
```

edit: No menu shortcut yet

---

### Post by .nedberg on 2008-09-17
> **forger said:**
> why did you choose LGPL license in launchpad by the way? :confused:

Because I selected the wrong one...:lolflag:
Changed it now to GPL v3.


Thanks for making the .deb package! I will have a look at it. How did you do it? I want to learn how to do that.

The new names are better than the original, I will keep that! Could you publish your changes to Launchpad or here at the forums? If you message me the scripts I will upload them to Launchpad, including the .deb file.

---

### Post by forger on 2008-09-17
* Added menu shortcut: System > Administration > Timekeeper
(the changes from the previous post still stand)

([see first post]("http://ubuntuforums.org/showthread.php?t=887769"))

---

### Post by forger on 2008-09-17
> **.nedberg said:**
> 
The new names are better than the original, I will keep that! Could you publish your changes to Launchpad or here at the forums? If you message me the scripts I will upload them to Launchpad, including the .deb file.

Here's how you add new people for development:
Make a new group/team: [https://launchpad.net/people/+newteam](https://launchpad.net/people/+newteam) (e.g. 'timekpr-maintainers')
Then you can add people in it, by clicking 'Add member'
Finally, you change the owner of the [timekpr]("http://launchpad.net/timekpr") to be that team

No offense, but it'd be best if you add me in that team (launchpad username: medigeek) so I can upload the changes I made,  so I can get the appropriate contribution karma points :D

---

### Post by forger on 2008-09-17
> **.nedberg said:**
> Because I selected the wrong one...:lolflag:
Changed it now to GPL v3.
Thanks for making the .deb package! I will have a look at it. How did you do it? I want to learn how to do that.

Changed the license to GPL :)
Making a deb package actually takes some experience and a bit of reading: [https://wiki.ubuntu.com/PackagingGuide/](https://wiki.ubuntu.com/PackagingGuide/)
When you finally make the package, it just takes some changes to be made when you want to add stuff to it and edit the changelog: [https://wiki.ubuntu.com/PackagingGuide/Recipes/Debdiff](https://wiki.ubuntu.com/PackagingGuide/Recipes/Debdiff)

---

### Post by forger on 2008-09-17
with GPLv3:
([see first post]("http://ubuntuforums.org/showthread.php?t=887769"))

The source:
[http://bazaar.launchpad.net/~timekpr-maintainers/timekpr/trunk/files](http://bazaar.launchpad.net/~timekpr-maintainers/timekpr/trunk/files)

edit: fixed the package, now it *really* shows copyright GPL

---

### Post by .nedberg on 2008-09-17
> **forger said:**
> Here's how you add new people for development:
Make a new group/team: [https://launchpad.net/people/+newteam](https://launchpad.net/people/+newteam) (e.g. 'timekpr-maintainers')
Then you can add people in it, by clicking 'Add member'
Finally, you change the owner of the [timekpr]("http://launchpad.net/timekpr") to be that team

Done!

> 
No offense, but it'd be best if you add me in that team (launchpad username: medigeek) so I can upload the changes I made,  so I can get the appropriate contribution karma points :D
No offence taken! I added you to the group. You seem to know your way around Launchpad better than me. Still figuring out how to use it...

---

### Post by forger on 2008-09-17
Finally! :D I managed to make lp:~timekpr-maintainers/timekpr/trunk as the main branch
Yours is set aside, because I couldn't upload to it. Now all all the team in timekpr-maintainers can upload/push to it. :)

To get it:
```
bzr update
```
or remove the old folder/branch and do:
```
bzr branch lp:timekpr
```

To upload
```
bzr push lp:timekpr
```

Woohoo! :guitar:

In case you want to build it:
```
sudo apt-get install devscripts
debuild -us -uc
```
(-us -uc is used when you don't want to sign the package)

---

### Post by UbuWu on 2008-09-17
Another easy way of filtering is using opendns. It has several categories of websites you can choose to be bloocked and doesn't require a program to be run.

---

### Post by crjackson on 2008-09-17
One thing that should be looked at is the **/etc/rc.local** file.  The installer should automatically append 
[B]
/usr/local/bin/timekpr.sh &[/B]

to the file, or whatever else will make it load on boot.  As it now stands, you still have to do that by hand after installing.  People installing deb files (or at least me) would expect that once the deb has executed, the package is fully installed.

---

### Post by .nedberg on 2008-09-17
> **crjackson said:**
> One thing that should be looked at is the **/etc/rc.local** file.  The installer should automatically append 
[B]
/usr/local/bin/timekpr.sh &[/B]

to the file, or whatever else with make it load on boot.  As it now stands, you still have to do that by hand after installing.  People installing deb files (or at least me) would expect that once the deb has executed, the package is fully installed.

You are correct. Maybe adding a start up script to /etc/init.d will be a better idea. It will also be needed when I get the time to rewrite everything to Python. It will need to be restarted when you change the configuration.

---

### Post by forger on 2008-09-17
> **crjackson said:**
> One thing that should be looked at is the **/etc/rc.local** file.  The installer should automatically append 
[B]
/usr/local/bin/timekpr.sh &[/B]

to the file, or whatever else with make it load on boot.  As it now stands, you still have to do that by hand after installing.  People installing deb files (or at least me) would expect that once the deb has executed, the package is fully installed.

Hold your horses, the developing has just began! I just made the debian package to ease up the testing purposes. I think we need an init.d script instead.
Either way, rc.local or init.d it requires reading :P In rc.local we have to find a way to add/remove/detect the line for timekpr

---

### Post by forger on 2008-09-17
um.. the configuration files should be in directory /etc/timekpr/ not in /var/lib/timekpr/

---

### Post by crjackson on 2008-09-17
> **.nedberg said:**
> You are correct. Maybe adding a start up script to /etc/init.d will be a better idea. It will also be needed when I get the time to rewrite everything to Python. It will need to be restarted when you change the configuration.

Cool, I hope you plan to maintain the install script for now.  It makes it so easy to get your updates as they come down the pike.

---

### Post by forger on 2008-09-17
I added an example init script, in "testing" folder:
[http://bazaar.launchpad.net/~timekpr-maintainers/timekpr/trunk/files](http://bazaar.launchpad.net/~timekpr-maintainers/timekpr/trunk/files)

---

### Post by forger on 2008-09-17
hm.. houston, we have a problem.
I made test deb package, and it seems that the init script runs the timekpr in the background as root, but it doesn't create the pid file /var/run/timekpr.pid (in simple english: if you remove the package it won't kill the running process or if you reinstall the package it will run two processes of timekpr).

---

### Post by .nedberg on 2008-09-17
New version including forger and my work

To get it
```

wget http://www.nedberg.net/install_timekpr.sh
sudo ./install_timekpr.sh

```
I will try and maintain the installer script alongside the development at launchpad.

- This version makes the gui remember (some of) the settings.

---

### Post by crjackson on 2008-09-17
> **.nedberg said:**
> New version including forger and my work

To get it
```

wget http://www.nedberg.net/install_timekpr.sh
sudo ./install_timekpr.sh

```
I will try and maintain the installer script alongside the development at launchpad.

- This version makes the gui remember (some of) the settings.

That's great, I was hoping you would.  I'll run it in the morning when I get home.

---

### Post by newbuntuxx on 2008-09-17
hey guys...great work...i'll download and test it. 

Since i am not a coder, but a i love reading code, i'll perhaps make a few grammatical and spelling corrections to the code comments...and also re-write some of them for efficiency and clarity.


crjackson, could you mark this thread as solved and edit your first post and write a small how-to showing how to download, install, and use this script.

.nedberg, keep up the good work. I wish I can code, I would've definitely  helped.

---

### Post by newbuntuxx on 2008-09-18
Hey,

here is an uninstall script:


```
#!/bin/bash
apt-get --purge remove libnotify-bin
#FIXME: need to stop all related running processes first
rm /usr/local/bin/addtime.sh
rm /usr/local/bin/extendlimits.sh
rm /usr/local/bin/timekpr.sh
rm /usr/local/bin/timekprGUI.py
rm /usr/local/bin/Timekpr.glade
```

obviously it is modest and needs work...

---

### Post by crjackson on 2008-09-18
> **newbuntuxx said:**
> i'll perhaps make a few grammatical and spelling corrections to the code comments...and also re-write some of them for efficiency and clarity.

Probably best to wait until development is finished.


> **newbuntuxx said:**
> crjackson, could you mark this thread as solved and edit your first post and write a small how-to showing how to download, install, and use this script.

Looking at other development threads and how they are handled, I'll leave it open since it's active and a work in progress.

---

### Post by forger on 2008-09-18
We could ask a moderator to transfer this to a more appropriate forum, say [programming talk]("http://ubuntuforums.org/forumdisplay.php?f=39")?

By the way, I started editing the timekpr bash script, trying to figure out how it works. I won't do any big changes without notifying you :)
And I'm still trying to figure out how to do the funky init script

---

### Post by newbuntuxx on 2008-09-18
it seems that the user's list in the GUI is populated by looking at all files/folders in the home directory and listing them. So, I got a few funny users like: lost and found, and "my pc" which is a file i had in my home  directory.

---

### Post by crjackson on 2008-09-18
> **newbuntuxx said:**
> it seems that the user's list in the GUI is populated by looking at all files/folders in the home directory and listing them. So, I got a few funny users like: lost and found, and "my pc" which is a file i had in my home  directory.

File a bug report on [Launchpad]("https://launchpad.net/timekpr")

---

### Post by shane2peru on 2008-09-18
Wow, been very busy, and I see I'm not the only one!  You guys are awesome!  Glad this project has been undertaken, when I get a chance, I'm going to re-read those last few pages, and figure out where the latest edition is and install it!  I'm still using an old edition that I manually installed! :lolflag:   This is a long overdue project!  Thanks all you guys that have pitched in and made it a reality!

Shane

---

### Post by forger on 2008-09-18
Yarr.. latest deb package:
([see first post]("http://ubuntuforums.org/showthread.php?t=887769"))

* New init.d script
* New source files/fixes

Simple english:
* Now it starts upon installing
* It runs in the background as root
* It works (Need confirmation on this one) :KS

---

### Post by forger on 2008-09-18
About the home users.. I think we could use:
```
cat /etc/passwd | cut -d: -f1,3 | grep ':\([1-9][0-9]\{3\}\|[5-9][0-9]\{2\}\)$'
```
It will get all users with uid from 500-9999 :)

In perl or python regex, it could be ':([1-9][0-9]{3}|[5-9][0-9]{2})$'
but I'm not sure, don't know much about python :(

---

### Post by .nedberg on 2008-09-19
> **crjackson said:**
> File a bug report on [Launchpad]("https://launchpad.net/timekpr")

Yes, that would be the preffered way of reporting bugs or problems. I will try to have a look at the user list this weekend.

---

### Post by forger on 2008-09-19
* Fixed the users list in timekpr-gui, it should now show only users with a set password (i.e. the real human users that can login)
* GUI requires admin privileges from within the program

Can someone test it out please?
([see first post]("http://ubuntuforums.org/showthread.php?t=887769"))

---

### Post by .nedberg on 2008-09-19
> **forger said:**
> * Fixed the users list in timekpr-gui, it should now show only users with a set password (i.e. the real human users that can login)
* GUI requires admin privileges from within the program

Can someone test it out please?
[ATTACH]85768[/ATTACH]

Great work! I would say .deb is the preffered install method now. Should I still maintain the install script?

I will start rewrinting timekpr into python then...

---

### Post by crjackson on 2008-09-19
> **forger said:**
> * Fixed the users list in timekpr-gui, it should now show only users with a set password (i.e. the real human users that can login)
* GUI requires admin privileges from within the program

Can someone test it out please?
[ATTACH]85768[/ATTACH]

Okay, I tested it out.  It installs just fine (would like to see those new icons though).  It still picks up "ftp" from my ftp server as a human user.

---

### Post by crjackson on 2008-09-19
> **.nedberg said:**
> Gret work! I would say .deb is the preffered install method now. Should I still maintain the install script?

I will start rewrinting timekpr into python then...

Personally I would like to see the install script maintained a while longer for an alternate install method.  Just my $0.02

---

### Post by crjackson on 2008-09-19
> **forger said:**
> Yarr.. latest deb package:
[ATTACH]85740[/ATTACH]

* New init.d script
* New source files/fixes

Simple english:
* Now it starts upon installing
* It runs in the background as root
* It works (Need confirmation on this one) :KS

By **"Now it starts upon installing"**. Do you mean that it's no longer required to make an entry in the **rc.local** file to cause boot time loading?

---

### Post by forger on 2008-09-19
> **crjackson said:**
> By **"Now it starts upon installing"**. Do you mean that it's no longer required to make an entry in the **rc.local** file to cause boot time loading?

correct, you can control it using:
```
sudo /etc/init.d/timekpr stop
sudo /etc/init.d/timekpr start
sudo /etc/init.d/timekpr restart
```

(and hopefully it will work as it worked on mine :P)

Can you install it and reboot and see if it's running?
```
ps aux | grep timekpr
```

---

### Post by forger on 2008-09-19
> **crjackson said:**
> It still picks up "ftp" from my ftp server as a human user.

:( well, a defined password in /etc/shadow is the only way I can think of to recognize real users.. I could limit the userids actually, what's the userid of your ftp?

```
cat /etc/passwd
```

---

### Post by crjackson on 2008-09-19
> **forger said:**
> correct, you can control it using:
```
sudo /etc/init.d/timekpr stop
sudo /etc/init.d/timekpr start
sudo /etc/init.d/timekpr restart
```

(and hopefully it will work as it worked on mine :P)

Can you install it and reboot and see if it's running?
```
ps aux | grep timekpr
```
```
charles@charles-desktop:~$ ps aux | grep timekpr
root      5056  0.0  0.0   2756  1232 ?        S    09:40   0:00 /bin/bash /usr/bin/timekpr
charles   5980  0.0  0.0   3004   752 pts/0    R+   09:42   0:00 grep timekpr
charles@charles-desktop:~$ 
```

---

### Post by crjackson on 2008-09-19
> **forger said:**
> :( well, a defined password in /etc/shadow is the only way I can think of to recognize real users.. I could limit the userids actually, what's the userid of your ftp?

```
cat /etc/passwd
```

```
charles@MSI-K8N-NEO4-PLAT-SLI:~$ cat /etc/passwd
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/bin/sh
bin:x:2:2:bin:/bin:/bin/sh
sys:x:3:3:sys:/dev:/bin/sh
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/bin/sh
man:x:6:12:man:/var/cache/man:/bin/sh
lp:x:7:7:lp:/var/spool/lpd:/bin/sh
mail:x:8:8:mail:/var/mail:/bin/sh
news:x:9:9:news:/var/spool/news:/bin/sh
uucp:x:10:10:uucp:/var/spool/uucp:/bin/sh
proxy:x:13:13:proxy:/bin:/bin/sh
www-data:x:33:33:www-data:/var/www:/bin/sh
backup:x:34:34:backup:/var/backups:/bin/sh
list:x:38:38:Mailing List Manager:/var/list:/bin/sh
irc:x:39:39:ircd:/var/run/ircd:/bin/sh
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/bin/sh
nobody:x:65534:65534:nobody:/nonexistent:/bin/sh
libuuid:x:100:101::/var/lib/libuuid:/bin/sh
dhcp:x:101:102::/nonexistent:/bin/false
syslog:x:102:103::/home/syslog:/bin/false
klog:x:103:104::/home/klog:/bin/false
hplip:x:104:7:HPLIP system user,,,:/var/run/hplip:/bin/false
avahi-autoipd:x:105:113:Avahi autoip daemon,,,:/var/lib/avahi-autoipd:/bin/false
gdm:x:106:114:Gnome Display Manager:/var/lib/gdm:/bin/false
pulse:x:107:116:PulseAudio daemon,,,:/var/run/pulse:/bin/false
messagebus:x:108:119::/var/run/dbus:/bin/false
avahi:x:109:120:Avahi mDNS daemon,,,:/var/run/avahi-daemon:/bin/false
polkituser:x:110:122:PolicyKit,,,:/var/run/PolicyKit:/bin/false
haldaemon:x:111:123:Hardware abstraction layer,,,:/var/run/hald:/bin/false
charles:x:1000:1000:Charles Jackson,,,:/home/charles:/bin/bash
proftpd:x:112:65534::/var/run/proftpd:/bin/false
ftp:x:113:65534::/home/ftp:/bin/false
vdr:x:114:125:VDR user,,,:/var/lib/vdr:/bin/false
clamav:x:115:126::/var/lib/clamav:/bin/false
saned:x:116:127::/home/saned:/bin/false
charles@MSI-K8N-NEO4-PLAT-SLI:~$ 
```

---

### Post by forger on 2008-09-19
Wonderful! Can you also check if it can actually prevent/limit a user from logging in?

---

### Post by crjackson on 2008-09-19
> **forger said:**
> Wonderful! Can you also check if it can actually prevent/limit a user from logging in?

I'll check in a minute.  I'm about to file a bug report.  If you have unrestricted users but last selected a restricted user, it will restrict the normally unrestricted user.

In other words, you must apply your changes to the desired user and apply/quit.  Then restart and select the next user and apply/quit

[Bug #272142]("https://bugs.launchpad.net/timekpr/+bug/272142")

---

### Post by crjackson on 2008-09-19
> **forger said:**
> Wonderful! Can you also check if it can actually prevent/limit a user from logging in?

It lets the user login and get 2 minutes.  Upon force logging him out, it locks the computer now and a hard reset is the only thing that brings it back.  It didn't use to do that.

[Bug #272147 ]("https://bugs.launchpad.net/timekpr/+bug/272147")

---

### Post by forger on 2008-09-19
hm.. is there a log we could use? I never really studied how timekpr works..
Hang on that thought by the way. I'll try it here during the weekend.

We could make a python function to totally lock up the file, similar to "usermod -L username", which puts "!" in front of the /etc/shadow encrypted password of the user. This way they won't be able to login at all!

I also found the best way to detect real/normal users, using the UID_MIN and UID_MAX userid boundaries:
```
import re

logindefs = open('/etc/login.defs')
uidminmax = re.compile('^UID_(?:MIN|MAX)\s+(\d+)',re.M).findall(logindefs.read(), 1)

if uidminmax[0] < uidminmax[1]:
	uidmin = uidminmax[0]
	uidmax = uidminmax[1]
else:
	uidmin = uidminmax[1]
	uidmax = uidminmax[0]

print "min",uidmin,"max",uidmax
```

---

### Post by .nedberg on 2008-09-19
The deb needs to create /var/log/timekpr, else saving of settings will fail.

Just commited a possible fix to bug272142.

---

### Post by forger on 2008-09-19
you mean /var/lib/timekpr ?
```
$ sudo ./timekpr-gui 
User=tester
Traceback (most recent call last):
  File "./timekpr-gui", line 328, in apply_clicked
    fileHandle = open(configFile, 'w')
IOError: [Errno 2] No such file or directory: '/var/lib/timekpr/tester'
```

edit: added it in the main timekpr

---

### Post by forger on 2008-09-19
New version, with .nedberg's possible bug fix:
  * Cleaned up timekpr and timekpr-gui
  * timekpr-gui shows users with userid within UID_MIN and UID_MAX
  * timekpr and timekpr-gui now check and create the default
    directory if necessary
  * Applied possible bugfix (LP: #272142)

**[COLOR="Red"]NOTE:[/COLOR]** Before getting this specific deb file, make sure you clear all your old timekpr-related configuration:
```

sudo apt-get purge timekpr
sudo killall -9 timekpr
sudo rm -f /var/lib/timekpr /etc/init.d/timekpr

```
This way you start clean and we know we're going together :KS

Here's the new version:
([see first post]("http://ubuntuforums.org/showthread.php?t=887769"))
Edit: Fixed the timekpr.glade path

I haven't tested its limitations yet, that's on my to-do list.
Let's hope it works now :)

---

### Post by crjackson on 2008-09-19
> **forger said:**
> New version, with .nedberg's possible bug fix:
  * Cleaned up timekpr and timekpr-gui
  * timekpr-gui shows users with userid within UID_MIN and UID_MAX
  * timekpr and timekpr-gui now check and create the default
    directory if necessary
  * Applied possible bugfix (LP: #272142)

**[COLOR="Red"]NOTE:[/COLOR]** Before getting this specific deb file, make sure you clear all your old timekpr-related configuration:
```

sudo apt-get purge timekpr
sudo killall -9 timekpr
sudo rm -f /var/lib/timekpr /etc/init.d/timekpr

```
This way you start clean and we know we're going together :KS

Here's the new version:
[ATTACH]85799[/ATTACH]

I haven't tested its limitations yet, that's on my to-do list.
Let's hope it works now :)

Not sure if this was supposed to remove the entry for my ftp server or not.  I purged all the old files and installed this deb.  Have a look at the screen shot of the dropdown for users.

---

### Post by forger on 2008-09-19
Get the newer one again, I re-uploaded a fixed version, changed the path to the right timekpr.glade
[http://ubuntuforums.org/attachment.php?attachmentid=85801&d=1221846576](http://ubuntuforums.org/attachment.php?attachmentid=85801&d=1221846576)

> Not sure if this was supposed to remove the entry for my ftp server or not. I purged all the old files and installed this deb. Have a look at the screen shot of the dropdown for users.

Can you post the output of:
```
grep 'UID_\(MIN\|MAX\)' /etc/login.defs
```

---

### Post by forger on 2008-09-19
By the way, are you sure you're using the right timekpr-gui ?
With the version you got, you wouldn't be able to view the window

With the new one:
```
sudo timekpr-gui
```
(without ./)

---

### Post by crjackson on 2008-09-19
Okay, purged and then cleaned out the directories manually because removing the package didn't do it.

Then I reinstalled and it seems to have completed with errors. However no launcher was created as before, and it won't run at all.

```
charles@MSI-K8N-NEO4-PLAT-SLI:~$ gksu '/usr/bin/timekpr-gui' 
Traceback (most recent call last):
  File "/usr/bin/timekpr-gui", line 347, in <module>
    tkg = timekprGUI()
  File "/usr/bin/timekpr-gui", line 64, in __init__
    self.wTree = gtk.glade.XML(self.gladefile, "window1")
RuntimeError: could not create GladeXML object
charles@MSI-K8N-NEO4-PLAT-SLI:~$ 
```

---

### Post by crjackson on 2008-09-19
> **forger said:**
> Get the newer one again, I re-uploaded a fixed version, changed the path to the right timekpr.glade
[http://ubuntuforums.org/attachment.php?attachmentid=85801&d=1221846576](http://ubuntuforums.org/attachment.php?attachmentid=85801&d=1221846576)



Can you post the output of:
```
grep 'UID_\(MIN\|MAX\)' /etc/login.defs
```

```
charles@MSI-K8N-NEO4-PLAT-SLI:~$ grep 'UID_\(MIN\|MAX\)' /etc/login.defs
UID_MIN 1000
UID_MAX 60000
charles@MSI-K8N-NEO4-PLAT-SLI:~$ 
```

---

### Post by crjackson on 2008-09-19
Newest version launched and the ftp entry is gone as well.  Looks good, just need a launcher now.

---

### Post by forger on 2008-09-19
edit: - ignore this post -

---

### Post by forger on 2008-09-19
The launcher is in System > Administration > Timekeeper, isn't it?

---

### Post by crjackson on 2008-09-19
It used to be, but I cleaned EVERYTHING out including menus to test the install and it did not create a launcher this time.

---

### Post by forger on 2008-09-19
check out ```
cat /usr/share/applications/timekpr.desktop
```Maybe you've hidden it or something.. It works here :)
By the way, I think I managed to fix timekpr, someone added "!" in the notify-send messages, that's why they wouldn't appear :P
We'll see how it goes

Try the new version:
([see first post]("http://ubuntuforums.org/showthread.php?t=887769"))

---

### Post by crjackson on 2008-09-19
> **forger said:**
> check out ```
cat /usr/share/applications/timekpr.desktop
```Maybe you've hidden it or something.. It works here :)
By the way, I think I managed to fix timekpr, someone added "!" in the notify-send messages, that's why they wouldn't appear :P
We'll see how it goes

Try the new version:
[ATTACH]85818[/ATTACH]

I'll try again when I get home from work.  What I actually did was to DELETE the menu item from the "Edit Menu" function.  Is it possible that this somehow prevented it from remaking the menu item when next installed?

Not sure what you mean about notifications not appearing.  The notifications worked fine for me on last test.

---

### Post by forger on 2008-09-19
hm.. maybe if you log out and log back in, the menus will get updated?

I'm on ubuntu intrepid 8.10 alpha 6, and the notify-send messages don't appear unfortunately:
> libnotify-Message: Unable to get session bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

After that, the process of the username wouldn't get killed, so I used "kill -TERM" and after that "kill -9" (not included in the deb version above) - seems to work as expected now.

---

### Post by crjackson on 2008-09-19
> **forger said:**
> hm.. maybe if you log out and log back in, the menus will get updated?

I'm on ubuntu intrepid 8.10 alpha 6, and the notify-send messages don't appear unfortunately:


After that, the process of the username wouldn't get killed, so I used "kill -TERM" and after that "kill -9" (not included in the deb version above) - seems to work as expected now.

Cool, I'll give it a good test drive this weekend.  I added an item to the blueprint section on launchpad.  Perhaps the notify-send issue relates more to the difference between intrepid and hardy than time keeper.

Come to think of it, I have seen times that menu items didn't appear until logoff/login was completed.  Perhaps that's the ticket.  I'll let you know.

---

### Post by crjackson on 2008-09-19
> **forger said:**
> check out ```
cat /usr/share/applications/timekpr.desktop
```Maybe you've hidden it or something.. It works here :)
By the way, I think I managed to fix timekpr, someone added "!" in the notify-send messages, that's why they wouldn't appear :P
We'll see how it goes

Try the new version:
[ATTACH]85818[/ATTACH]

```
charles@MSI-K8N-NEO4-PLAT-SLI:~$ cat /usr/share/applications/timekpr.desktop
[Desktop Entry]
Name=Timekeeper
Name[en_CA]=Timekeeper
Name[en_GB]=Timekeeper
Comment=Keep control of computer usage
Comment[en_CA]=Keep control of computer usage
Comment[en_GB]=Keep control of computer usage
Exec=gksu timekpr-gui
Icon=config-users
Terminal=false
Type=Application
Categories=GTK;System;Settings;
StartupNotify=true
Encoding=UTF-8
charles@MSI-K8N-NEO4-PLAT-SLI:~$ 
```

I'm going to remove the current install, and install the newer deb.  I logged off and on again.  Still no launcher as indicated above.

---

### Post by crjackson on 2008-09-19
> **forger said:**
> New version, with .nedberg's possible bug fix:
  * Cleaned up timekpr and timekpr-gui
  * timekpr-gui shows users with userid within UID_MIN and UID_MAX
  * timekpr and timekpr-gui now check and create the default
    directory if necessary
  * Applied possible bugfix (LP: #272142)

**[COLOR="Red"]NOTE:[/COLOR]** Before getting this specific deb file, make sure you clear all your old timekpr-related configuration:
```

sudo apt-get purge timekpr
sudo killall -9 timekpr
sudo rm -f /var/lib/timekpr /etc/init.d/timekpr

```
This way you start clean and we know we're going together :KS

Here's the new version:
[ATTACH]85801[/ATTACH]
Edit: Fixed the timekpr.glade path

I haven't tested its limitations yet, that's on my to-do list.
Let's hope it works now :)

Strange results when removing.  Here's the output...

```
charles@MSI-K8N-NEO4-PLAT-SLI:~$ sudo apt-get purge timekpr
[sudo] password for charles: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  timekpr*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 156kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 231121 files and directories currently installed.)
Removing timekpr ...
Purging configuration files for timekpr ...
charles@MSI-K8N-NEO4-PLAT-SLI:~$ sudo killall -9 timekpr
timekpr: no process killed
charles@MSI-K8N-NEO4-PLAT-SLI:~$ sudo rm -f /var/lib/timekpr /etc/init.d/timekpr
rm: cannot remove `/var/lib/timekpr': Is a directory
charles@MSI-K8N-NEO4-PLAT-SLI:~$ 
```

---

### Post by crjackson on 2008-09-20
Okay, tested the new deb and it's good.  I think that .nedberg is already aware that if it kicks you off the system due to logging in outside of the users allowable boundaries, you can log back in and get the full 2 minutes grace for logoff over and over again.

If you get kicked off for running out of time, then when you log back in you get less than a minute, no warning, and kicked out again :)

I still have no auto generated launcher in the system>admin menus, so I'll make one by hand.  Was the new launcher supposed to show a new icon?  If so tell me where it's located so I can make it look right.

Also... .nedberg, the user's configuration settings now hold properly and do not go forward to an unrestricted user.  **Mark that bug squished!!!**

---

### Post by forger on 2008-09-20
The icons aren't used yet, I have to figure out the license/copyright for them :)

I made a locking function and a logging function (/var/log/timekpr.log), will upload soon!

---

### Post by forger on 2008-09-20
([see first post]("http://ubuntuforums.org/showthread.php?t=887769"))

  * Old timekpr: timekpr.old (not in deb package)
  * Tidied up timekpr
  * New logging function: logkpr message - Log file: /var/log/timekpr.log
  * New lock/unlock functions: based on usermod -e (user expiration) since it shows a relative message - Would use -L to actually lock it, but it would just say 'wrong password' (I actually filed a [bug about this]("https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/272417"))
  * New variable for lock function: lock_lasts='1 hour'
  * New script to unlock a user account manually: timekpr-unlock username

Note: timekpr-unlock doesn't remove the username.logout file (i.e. they can log in, but they will be killed after 20 seconds or so, and the account will be locked again)

Note 2: if you want to clear the logfile, restart timekpr (it clears on every start of timekpr):
```
sudo /etc/init.d/timekpr restart
```

---

### Post by crjackson on 2008-09-20
The issue about creating a launcher seems to have been caused by deleting the thing manually.  I don't have this issue on any of the other 3 computers I'm using for testing.  The launcher is installed upon running the deb, and removed when the package is removed.  It's just on one machine that it won't update correctly.

---

### Post by crjackson on 2008-09-20
[Bug #272147]("https://bugs.launchpad.net/timekpr/+bug/272147")

After many hours of testing on multiple machines, I have been able to determine that this bug is invalid. It is machine specific and appears to be a problem with the particular Ubuntu install on the machine in question. Please mark this bug closed for the time being.

---

### Post by crjackson on 2008-09-20
> **forger said:**
> [ATTACH]85885[/ATTACH]

  * Old timekpr: timekpr.old (not in deb package)
  * Tidied up timekpr
  * New logging function: logkpr message - Log file: /var/log/timekpr.log
  * New lock/unlock functions: based on usermod -e (user expiration) since it shows a relative message - Would use -L to actually lock it, but it would just say 'wrong password' (I actually filed a [bug about this]("https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/272417"))
  * New variable for lock function: lock_lasts='1 hour'
  * New script to unlock a user account manually: timekpr-unlock username

Note: timekpr-unlock doesn't remove the username.logout file (i.e. they can log in, but they will be killed after 20 seconds or so, and the account will be locked again)

Note 2: if you want to clear the logfile, restart timekpr (it clears on every start of timekpr):
```
sudo /etc/init.d/timekpr restart
```

I just installed the new deb.  I'm not entirely clear what the new lock functions do for the end user as an administrator.  Could you please elaborate for me.?

---

### Post by forger on 2008-09-20
> **crjackson said:**
> The issue about creating a launcher seems to have been caused by deleting the thing manually.
I'm glad it's just one occurence, but it shouldn't be really a problem, try this:
```

sudo rm -f /usr/share/applications/timekpr.desktop
sudo apt-get install menu
update-menus -v
sudo update-menus -v

```

then reinstall the deb package and do one more time:
```
update-menus -v
sudo update-menus -v

```

let's hope that fixes it :)

---

### Post by forger on 2008-09-20
> **crjackson said:**
> I just installed the new deb.  I'm not entirely clear what the new lock functions do for the end user as an administrator.  Could you please elaborate for me.?

The lock function sets a username as expired

Event:
- Say a user with timekpr limitation logs in
- User's time is up, timekpr kills the login
- User logs in again, the process is killed after 10-40 seconds, and a file username.logout is created in /var/lib/timekpr/ folder (/var/lib/timekpr/username.logout)
- User logs in once more time, process gets killed one more time and account is set as expired. The expiration lasts by default one hour (set in lock_lasts variable in /usr/bin/timekpr).
It also creates a file /var/lib/timekpr/username.lock - do not remove it manually, as then you would: 1) lose the previous expiration date on the user account 2) have to reset the expiration date yourself
- The user cannot login anymore because their account is temporarily set as expired, they can login again after 1 hour (or whatever you set the lock_lasts to be)

If a user is locked and you would like to unlock the user before the 1 hour, you simply do:
```
sudo timekpr-unlock username
```I've tested it here and it worked - it's good to stop the users from intruding every so many times!

However, this doesn't cover the username.logout file.  If the username unlocked (either after one hour or after admin does time-unlock) and username.logout is still there (and is of today's date), then the user will get locked again.

It's a bit confusing, but we're still in development phase, it's clearly not done yet :)

I'm not that good with the GUI though, maybe .nedberg can include it as a "Clear lock" button :)

edit: that is.. if you all like the idea!

---

### Post by nothingspecial on 2008-09-20
I`d just like to say excellent work guys.

---

### Post by forger on 2008-09-20
hm.. the "disable boundaries" button isn't working as expected, the allow file is there, but the user is instantly killed, since the .logout file is there :\

---

### Post by crjackson on 2008-09-20
> **forger said:**
> The lock function sets a username as expired

Event:
- Say a user with timekpr limitation logs in
- User's time is up, timekpr kills the login
- User logs in again, the process is killed after 10-40 seconds, and a file username.logout is created in /var/lib/timekpr/ folder (/var/lib/timekpr/username.logout)
- User logs in once more time, process gets killed one more time and account is set as expired. The expiration lasts by default one hour (set in lock_lasts variable in /usr/bin/timekpr).
It also creates a file /var/lib/timekpr/username.lock - do not remove it manually, as then you would: 1) lose the previous expiration date on the user account 2) have to reset the expiration date yourself
- The user cannot login anymore because their account is temporarily set as expired, they can login again after 1 hour (or whatever you set the lock_lasts to be)

If a user is locked and you would like to unlock the user before the 1 hour, you simply do:
```
sudo timekpr-unlock username
```I've tested it here and it worked - it's good to stop the users from intruding every so many times!

However, this doesn't cover the username.logout file.  If the username unlocked (either after one hour or after admin does time-unlock) and username.logout is still there (and is of today's date), then the user will get locked again.

It's a bit confusing, but we're still in development phase, it's clearly not done yet :)

I'm not that good with the GUI though, maybe .nedberg can include it as a "Clear lock" button :)

edit: that is.. if you all like the idea!

I think it's a good feature.  However I think it would be better if - When the user is kicked off the very first time, the account is locked, and wouldn't be unlocked until the users normally allowed login time on the next day.  Unless the admin account were to bring up the the GUI and unlock the account with the disable boundaries button or some such action.

I think this would be a good way of preventing the repeated login attempts.  Instead of having the 60 min. hard-coded as a standard, why not use a variable and let it read the users config file.  The variable would tell the lock routine not to unlock until such time as in the user's config file for the next day.

If more time is needed say for school work or something, Have the disable boundaries button also reset the lock on the account to unlock.

---

### Post by crjackson on 2008-09-20
> **forger said:**
> hm.. the "disable boundaries" button isn't working as expected, the allow file is there, but the user is instantly killed, since the .logout file is there :\

I haven't tested it, however - Since the location of the script(s) have changed I would imagine it may be looking for files in the wrong place.  The main script has been the only thing I've tested so far, since it's the most important at the momemnt.

---

### Post by crjackson on 2008-09-20
> **forger said:**
> hm.. the "disable boundaries" button isn't working as expected, the allow file is there, but the user is instantly killed, since the .logout file is there :\

I haven't tested it, however - Since the location of the script(s) have changed I would imagine it may be looking for files in the wrong place.  The main script has been the only thing I've tested so far, since it's the most important at the moment.

By the way, would you happen to know how to remove "Switch User" from the main exit menu dialog?  It's broke on one of my main shared machines, and I really don't want to do a fresh install just to fix that.  I have 6 users on that system and it would be a real pain to set it all back up for each user.

Using the switch user will cause this machine to lockup when one of the users tries to logoff after switching.  It works fine when each person is forced to logoff before the next one can login.

---

### Post by crjackson on 2008-09-20
> **crjackson said:**
> 
By the way, would you happen to know how to remove "Switch User" from the main exit menu dialog?

Okay, figured this one out on my own...

Terminal>gconf-editor

desktop>gnome>lockdown>disable_user_switching and tick the check box

DONE!

---

### Post by crjackson on 2008-09-20
> **forger said:**
> [ATTACH]85885[/ATTACH]

  * Old timekpr: timekpr.old (not in deb package)
  * Tidied up timekpr
  * New logging function: logkpr message - Log file: /var/log/timekpr.log
  * New lock/unlock functions: based on usermod -e (user expiration) since it shows a relative message - Would use -L to actually lock it, but it would just say 'wrong password' (I actually filed a [bug about this]("https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/272417"))
  * New variable for lock function: lock_lasts='1 hour'
  * New script to unlock a user account manually: timekpr-unlock username

Note: timekpr-unlock doesn't remove the username.logout file (i.e. they can log in, but they will be killed after 20 seconds or so, and the account will be locked again)

Note 2: if you want to clear the logfile, restart timekpr (it clears on every start of timekpr):
```
sudo /etc/init.d/timekpr restart
```

forger,

When packaging the debs, would it be possible to insert the particular version number in the Help>About menu?  It would be useful so I can check to insure I have the correct version installed for testing.

---

### Post by crjackson on 2008-09-20
> **forger said:**
> I'm glad it's just one occurence, but it shouldn't be really a problem, try this:
```

sudo rm -f /usr/share/applications/timekpr.desktop
sudo apt-get install menu
update-menus -v
sudo update-menus -v

```

then reinstall the deb package and do one more time:
```
update-menus -v
sudo update-menus -v

```

let's hope that fixes it :)

Actually it didn't.  I have no launcher at all now.  I'll have to make one manually.

```
charles@MSI-K8N-NEO4-PLAT-SLI:~$ sudo killall -9 timekpr
charles@MSI-K8N-NEO4-PLAT-SLI:~$ sudo rm -f /var/lib/timekpr /etc/init.d/timekpr
rm: cannot remove `/var/lib/timekpr': Is a directory
charles@MSI-K8N-NEO4-PLAT-SLI:~$ sudo apt-get purge timekpr
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  timekpr*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 164kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 231383 files and directories currently installed.)
Removing timekpr ...
Purging configuration files for timekpr ...
charles@MSI-K8N-NEO4-PLAT-SLI:~$ cat /usr/share/applications/timekpr.desktop
cat: /usr/share/applications/timekpr.desktop: No such file or directory
charles@MSI-K8N-NEO4-PLAT-SLI:~$ sudo rm -f /usr/share/applications/timekpr.desktop
charles@MSI-K8N-NEO4-PLAT-SLI:~$ sudo apt-get install menu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
menu is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
charles@MSI-K8N-NEO4-PLAT-SLI:~$ update-menus -v
update-menus[14317]: Update-menus is run by user.
update-menus[14317]: Dpkg is not locking dpkg status area, good.
update-menus[14317]: Reading installed packages list...
update-menus[14317]: Reading translation rules in /etc/menu-methods/translate_menus.
update-menus[14317]: Reading menu-entry files in /home/charles/.menu/.
update-menus[14317]: 0 menu entries found (0 total).
update-menus[14317]: Reading menu-entry files in /etc/menu/.
update-menus[14317]: 0 menu entries found (0 total).
update-menus[14317]: Reading menu-entry files in /usr/lib/menu/.
update-menus[14317]: 1 menu entries found (1 total).
update-menus[14317]: Reading menu-entry files in /usr/share/menu/.
/usr/share/menu/cairo-dock: 1: Syntax error: word unexpected (expecting ")")
Execution of /usr/share/menu/cairo-dock generated no output or returned an error.
update-menus[14317]: file /usr/share/menu/openjdk-6-jre line 8:
Discarding entry requiring missing package openjdk-6-bin.
update-menus[14317]: 173 menu entries found (174 total).
update-menus[14317]: Reading menu-entry files in /usr/share/menu/default/.
update-menus[14317]: 0 menu entries found (174 total).
update-menus[14317]: Running menu-methods in /home/charles/.menu-methods/.
update-menus[14317]: Running menu-methods in /etc/menu-methods/.
update-menus[14317]: Running method: /etc/menu-methods/gnome-panel-data
charles@MSI-K8N-NEO4-PLAT-SLI:~$ sudo update-menus -v
update-menus[14326]: Dpkg is not locking dpkg status area, good.
update-menus[14326]: Reading installed packages list...
update-menus[14326]: Reading translation rules in /etc/menu-methods/translate_menus.
update-menus[14326]: Reading menu-entry files in /etc/menu/.
update-menus[14326]: 0 menu entries found (0 total).
update-menus[14326]: Reading menu-entry files in /usr/lib/menu/.
update-menus[14326]: 1 menu entries found (1 total).
update-menus[14326]: Reading menu-entry files in /usr/share/menu/.
/usr/share/menu/cairo-dock: 1: Syntax error: word unexpected (expecting ")")
Execution of /usr/share/menu/cairo-dock generated no output or returned an error.
update-menus[14326]: file /usr/share/menu/openjdk-6-jre line 8:
Discarding entry requiring missing package openjdk-6-bin.
update-menus[14326]: 173 menu entries found (174 total).
update-menus[14326]: Reading menu-entry files in /usr/share/menu/default/.
update-menus[14326]: 0 menu entries found (174 total).
update-menus[14326]: Running menu-methods in /etc/menu-methods/.
update-menus[14326]: Running method: /etc/menu-methods/gnome-panel-data
charles@MSI-K8N-NEO4-PLAT-SLI:~$ update-menus -v
update-menus[14394]: Update-menus is run by user.
update-menus[14394]: Dpkg is not locking dpkg status area, good.
update-menus[14394]: Reading installed packages list...
update-menus[14394]: Reading translation rules in /etc/menu-methods/translate_menus.
update-menus[14394]: Reading menu-entry files in /home/charles/.menu/.
update-menus[14394]: 0 menu entries found (0 total).
update-menus[14394]: Reading menu-entry files in /etc/menu/.
update-menus[14394]: 0 menu entries found (0 total).
update-menus[14394]: Reading menu-entry files in /usr/lib/menu/.
update-menus[14394]: 1 menu entries found (1 total).
update-menus[14394]: Reading menu-entry files in /usr/share/menu/.
/usr/share/menu/cairo-dock: 1: Syntax error: word unexpected (expecting ")")
Execution of /usr/share/menu/cairo-dock generated no output or returned an error.
update-menus[14394]: file /usr/share/menu/openjdk-6-jre line 8:
Discarding entry requiring missing package openjdk-6-bin.
update-menus[14394]: 173 menu entries found (174 total).
update-menus[14394]: Reading menu-entry files in /usr/share/menu/default/.
update-menus[14394]: 0 menu entries found (174 total).
update-menus[14394]: Running menu-methods in /home/charles/.menu-methods/.
update-menus[14394]: Running menu-methods in /etc/menu-methods/.
update-menus[14394]: Running method: /etc/menu-methods/gnome-panel-data
charles@MSI-K8N-NEO4-PLAT-SLI:~$ sudo update-menus -v
update-menus[14403]: Dpkg is not locking dpkg status area, good.
update-menus[14403]: Reading installed packages list...
update-menus[14403]: Reading translation rules in /etc/menu-methods/translate_menus.
update-menus[14403]: Reading menu-entry files in /etc/menu/.
update-menus[14403]: 0 menu entries found (0 total).
update-menus[14403]: Reading menu-entry files in /usr/lib/menu/.
update-menus[14403]: 1 menu entries found (1 total).
update-menus[14403]: Reading menu-entry files in /usr/share/menu/.
/usr/share/menu/cairo-dock: 1: Syntax error: word unexpected (expecting ")")
Execution of /usr/share/menu/cairo-dock generated no output or returned an error.
update-menus[14403]: file /usr/share/menu/openjdk-6-jre line 8:
Discarding entry requiring missing package openjdk-6-bin.
update-menus[14403]: 173 menu entries found (174 total).
update-menus[14403]: Reading menu-entry files in /usr/share/menu/default/.
update-menus[14403]: 0 menu entries found (174 total).
update-menus[14403]: Running menu-methods in /etc/menu-methods/.
update-menus[14403]: Running method: /etc/menu-methods/gnome-panel-data
charles@MSI-K8N-NEO4-PLAT-SLI:~$ 

```

---

### Post by forger on 2008-09-21
> **crjackson said:**
> Actually it didn't.  I have no launcher at all now.  I'll have to make one manually.

OK, I'm still not sure why it does that :(

> **crjackson said:**
> forger,
When packaging the debs, would it be possible to insert the particular version number in the Help>About menu?  It would be useful so I can check to insure I have the correct version installed for testing.

I can mention it in the changelog:
```
cat /usr/share/doc/timekpr/changelog.gz | gunzip
```
I'll mention from now on the [revision number]("http://bazaar.launchpad.net/%7Etimekpr-maintainers/timekpr/trunk/changes") of launchpad :)

.nedberg made quite some changes, I'll test them out soon

---

### Post by forger on 2008-09-21
Um.. I think I found a better locking option using PAM module with gdm, expect changes in the near future :)
and I think it's better to focus on making timekpr as a python program, so I won't be adding any more features

---

### Post by crjackson on 2008-09-21
> **forger said:**
> Um.. I think I found a better locking option using PAM module with gdm, expect changes in the near future :)
and I think it's better to focus on making timekpr as a python program, so I won't be adding any more features

I'll be watching for any new changes  :)

---

### Post by forger on 2008-09-21
([see first post]("http://ubuntuforums.org/showthread.php?t=887769"))
(Revision #31)

.nedberg made it actually work with the lock, I've tested it and it works ok
I believe it's better to start pythonizing the timekpr from now on, if any glitches/bugs detected, they'll be targeted in the python script :)

---

### Post by crjackson on 2008-09-21
> **forger said:**
> [ATTACH]85972[/ATTACH]
(Revision #31)

.nedberg made it actually work with the lock, I've tested it and it works ok
I believe it's better to start pythonizing the timekpr from now on, if any glitches/bugs detected, they'll be targeted in the python script :)

Sounds good.  I just download and installed the new deb.  Thanks for converting all this work to deb packages.  I'm keeping all this work progress on my blog for easy personal downloading when I install new Linux systems.

Savvas - Is there a place on launchpad where I can find the deb files to link to?  I've looked around and can't find the debs, only the source files.

Placing the file and a recent screen shot of the GUI in this post for linking and/or other interested parties.

---

### Post by forger on 2008-09-22
> **crjackson said:**
> 
Savvas - Is there a place on launchpad where I can find the deb files to link to?  I've looked around and can't find the debs, only the source files.

Placing the file and a recent screen shot of the GUI in this post for linking and/or other interested parties.

It's still rough around the edges, so I haven't created a ppa archive yet, plus I'm not that good with it, I have to read about [ppa uploading]("https://help.launchpad.net/Packaging/PPA") :lolflag:
I've uploaded the deb file with a "readme" file at: [http://savvas.radevic.com/timekpr/](http://savvas.radevic.com/timekpr/)
You can link it there or here in ubuntuforums, until we get a steady release :)

---

### Post by crjackson on 2008-09-22
forger, where is the proper place on launchpad to make suggestion for a change or feature?  Or would it be better if I just post it here?

I think it would be great, if when installing the deb, the package checks for previous installs, and removes the older version before installing the new version.  What do you think?

---

### Post by forger on 2008-09-23
I think you can suggest a bug-like feature using [http://bugs.launchpad.net/timekpr](http://bugs.launchpad.net/timekpr) but make sure you add the word "wishlist" in the subject, i.e. "wishlist - remove old version before installing"

I made a new deb package with what you asked for (more or less). It checks for older timekpr packages and replaces them ( hopefully :) ), can you test it out:
([see first post]("http://ubuntuforums.org/showthread.php?t=887769"))
Note: it contains an extra timekpr.conf, but it's not used yet, so ignore it.

Also, about that icon problem, can you do this and post back the output:
```
sudo find / -depth -name "*timekpr*.desktop*"
```
I think you may have leftovers somewhere that break it from showing up

---

### Post by crjackson on 2008-09-23
> **forger said:**
> I think you can suggest a bug-like feature using [http://bugs.launchpad.net/timekpr](http://bugs.launchpad.net/timekpr) but make sure you add the word "wishlist" in the subject, i.e. "wishlist - remove old version before installing"

I made a new deb package with what you asked for (more or less). It checks for older timekpr packages and replaces them ( hopefully :) ), can you test it out:
[ATTACH]86187[/ATTACH]
Note: it contains an extra timekpr.conf, but it's not used yet, so ignore it.

Also, about that icon problem, can you do this and post back the output:
```
sudo find / -depth -name "*timekpr*.desktop*"
```
I think you may have leftovers somewhere that break it from showing up

```
charles@MSI-K8N-NEO4-PLAT-SLI:~$ sudo find / -depth -name "*timekpr*.desktop*"
/usr/share/applications/timekpr.desktop
```

---

### Post by crjackson on 2008-09-23
Check new Bug Report [273664]("https://bugs.launchpad.net/timekpr/+bug/273664")

---

### Post by forger on 2008-09-23
bummer.. I thought maybe the fact that you created an icon manually could make the old one not show. Well alright, one final shot and I drop the case.

[COLOR=Red]**Important note**[/COLOR]:
This will remove *all* your locally defined mime-types and custom application menu shortcuts. mime-types are like windows extensions that link to default programs. It will rebuild the database with the default programs once you logout and log back in.
Only do this if you don't have a lot of customised "open with" file types!
That said, here's the command:
```

cd $HOME/.local/share
rm -rf mime icons applications desktop-directories

sudo update-mime-database /usr/share/mime/
sudo update-desktop-database

```Now log out and log back in, install/reinstall the new deb package and.. cross your fingers :)

---

### Post by crjackson on 2008-09-23
> **forger said:**
> bummer.. I thought maybe the fact that you created an icon manually could make the old one not show. Well alright, one final shot and I drop the case.

[COLOR=Red]**Important note**[/COLOR]:
This will remove *all* your locally defined mime-types and custom application menu shortcuts. mime-types are like windows extensions that link to default programs. It will rebuild the database with the default programs once you logout and log back in.
Only do this if you don't have a lot of customised "open with" file types!
That said, here's the command:
```

cd $HOME/.local/share
rm -rf mime icons applications desktop-directories

sudo update-mime-database /usr/share/mime/
sudo update-desktop-database

```Now log out and log back in, install/reinstall the new deb package and.. cross your fingers :)

I'm at work this time.  I'll have to wait until I get back home.  I'm not going to sweat it too much.  I tinker with my system a bunch and probably borked something.  I'll be installing Ibex when it's released and everything will hopefully function normally again - Until I Tinker it out of whack again :)

---

### Post by jeromio on 2008-09-23
This is fantastic. I just installed this on my kids' laptop. I don't yet know if it works, but I'm sure I'll find out soon enough.

BTW, I used the deb linked to in this thread (just a couple posts above). I got an error, unresolved dependency on libnotify-bin. I installed that manually and everything works.

Thank you.

---

### Post by crjackson on 2008-09-23
> **jeromio said:**
> This is fantastic. I just installed this on my kids' laptop. I don't yet know if it works, but I'm sure I'll find out soon enough.

BTW, I used the deb linked to in this thread (just a couple posts above). I got an error, unresolved dependency on libnotify-bin. I installed that manually and everything works.

Thank you.

I actually added that to the text.sh installer some time back.  I probably did it in such a way that's not friendly to the newer builds.  The developers .nedberg and forger are very active here so they will see your post.  I'm glad you are giving it a spin. It's a great tool.

---

### Post by crjackson on 2008-09-24
> **forger said:**
> bummer.. I thought maybe the fact that you created an icon manually could make the old one not show. Well alright, one final shot and I drop the case.

[COLOR=Red]**Important note**[/COLOR]:
This will remove *all* your locally defined mime-types and custom application menu shortcuts. mime-types are like windows extensions that link to default programs. It will rebuild the database with the default programs once you logout and log back in.
Only do this if you don't have a lot of customised "open with" file types!
That said, here's the command:
```

cd $HOME/.local/share
rm -rf mime icons applications desktop-directories

sudo update-mime-database /usr/share/mime/
sudo update-desktop-database

```Now log out and log back in, install/reinstall the new deb package and.. cross your fingers :)

BINGO!  It worked...

---

### Post by forger on 2008-09-24
> **jeromio said:**
> 
BTW, I used the deb linked to in this thread (just a couple posts above). I got an error, unresolved dependency on libnotify-bin. I installed that manually and everything works.

Bear in mind that it's under heavy development, wear your worker's helmet at all times :KS
What operating system are you using? libnotify-bin is in [debian]("http://packages.debian.org/search?keywords=libnotify-bin") and [ubuntu]("http://packages.ubuntu.com/search?keywords=libnotify-bin") repositories

---

### Post by crjackson on 2008-09-27
[[COLOR="Blue"]_Moved to Post #1_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=887769")

---

### Post by forger on 2008-09-28
FYI, I'm contributing to the code too :p
And we might have to change the name or ask for permission by the original author of 'timekpr' in order to get the full copyright properly, Even's working on that part :)

Edit: I have made a mini-page for the packages [here]("http://savvas.radevic.com/timekpr/") - version 0.1.0ubuntu9 will probably be the main "stable" one (for now at least, until we finish the python stuff and test it properly)

---

### Post by crjackson on 2008-09-28
[_[COLOR="Blue"]See Post#1[/COLOR]_]("http://ubuntuforums.org/showthread.php?t=887769")

---

### Post by bedege on 2008-09-29
Hello

I've downloaded and installed the .deb package of the bash version that Savvas/Forger made available. I use Xubuntu 8.04, i.e. Xfce instead of Gnome.

I tried to block my son's account using the GUI. But that did not work. My son can still log in after the limit hour is over. How can I check what went wrong ? Have you similar feedback from Xubunteros (I use gdm as login manager).

Also, I'm a bit puzzled on how to install the Python version from launchpad. I used bzr to download the source code, but still the install script downloads some other code from nedberg's site ? Can you please explain how one should install the code from launchpad ?

Cheers

---

### Post by forger on 2008-09-29
Which deb package? Reply with the output of these commands in terminal:
```
apt-cache policy timekpr
ls -l /usr/bin/x-session-manager
ls -l /etc/alternatives/x-session-manager
```
Also, upload the file /var/log/timekpr.log

The python version is not ready yet, a deb package will be ready for it when it is :)

---

### Post by crjackson on 2008-09-29
forger,

I've edited my very [_[COLOR="Blue"]first post[/COLOR]_]("http://ubuntuforums.org/showthread.php?t=887769") in this thread to include the latest deb, a screenshot, and some instructions. It might be a good idea to edit your posts with the older deb files and either remove them, or replace them with the current. This should avoid the confusion of someone downloading an early version. I think most users who are looking or interested will probably read the very first post so I've decided to keep it updated with the latest information.

---

### Post by bedege on 2008-09-29
> **forger said:**
> Which deb package?


Well, the .deb package I tested was downloaded from [here]("http://savvas.radevic.com/timekpr/timekpr_0.1.0ubuntu9_all.deb") and I believe it is actually the only available, no ?
I'm at work at the moment, so I'll post the results of above commands tonight.

Thks

---

### Post by crjackson on 2008-09-29
ignore

---

### Post by forger on 2008-09-29
> **crjackson said:**
> forger,

It might be a good idea to edit your posts with the older deb files and either remove them, or replace them with the current. 

Aye-aye sir! :)

---

### Post by forger on 2008-09-29
Done! You have a post with a deb package, remove it from the attachments :)
[http://ubuntuforums.org/showpost.php?p=5829614&postcount=199](http://ubuntuforums.org/showpost.php?p=5829614&postcount=199)

---

### Post by forger on 2008-09-29
> **bedege said:**
> I'm at work at the moment, so I'll post the results of above commands tonight.
Thks

Yep, it's probably xfce-related, reply with the commands output when you find time :)
Also bedege, you have a separate user account for your child where you applied the limits right?

---

### Post by crjackson on 2008-09-29
> **forger said:**
> Done! You have a post with a deb package, remove it from the attachments :)
[http://ubuntuforums.org/showpost.php?p=5829614&postcount=199](http://ubuntuforums.org/showpost.php?p=5829614&postcount=199)

I'm keeping the most current deb package there for users who find the thread for the first time (saves looking for other links). When there are newer versions, I replace that one with the newest build you have made.

---

### Post by forger on 2008-09-29
> **crjackson said:**
> I'm keeping the most current deb package there for users who find the thread for the first time (saves looking for other links). When there are newer versions, I replace that one with the newest build you have made.
That's in your first post, I agree.

But see "Attached Files" in [post #199]("http://ubuntuforums.org/showpost.php?p=5829614&postcount=199"), it says "timekpr_0.1.0ubuntu8_all.deb" :)
Here's how you remove it: Click "Edit" then "Go Advanced" then click on the "clip" icon and click "Manage attachments".
Then scroll down and click "Remove" on that deb package. Then scroll up, "Close window", and "Save changes" :)

---

### Post by crjackson on 2008-09-29
> **forger said:**
> That's in your first post, I agree.

But see "Attached Files" in [post #199]("http://ubuntuforums.org/showpost.php?p=5829614&postcount=199"), it says "timekpr_0.1.0ubuntu8_all.deb" :)
Here's how you remove it: Click "Edit" then "Go Advanced" then click on the "clip" icon and click "Manage attachments".
Then scroll down and click "Remove" on that deb package. Then scroll up, "Close window", and "Save changes" :)

I missed that one - Thanks...  It's gone!:)

---

### Post by bedege on 2008-09-29
Hello

Here are the results
```
benoit@tatihou:~$ apt-cache policy timekpr
timekpr:
  Installé*: 0.1.0ubuntu9
  Candidat*: 0.1.0ubuntu9
 Table de version*:
 *** 0.1.0ubuntu9 0
        100 /var/lib/dpkg/status
```
and
```
benoit@tatihou:~$ ls -l /usr/bin/x-session-manager
lrwxrwxrwx 1 root root 35 2008-01-03 00:33 /usr/bin/x-session-manager -> /etc/alternatives/x-session-manager
benoit@tatihou:~$ ls -l /etc/alternatives/x-session-manager
lrwxrwxrwx 1 root root 22 2008-08-27 21:08 /etc/alternatives/x-session-manager -> /usr/bin/xfce4-session
```

The content of /var/log/timekpr.log
```
benoit@tatihou:~$ cat /var/log/timekpr.log 
2008-09-29 22:41:03 +0200 Started timekpr
```

and yes, my kids are using a specific account, which I'm trying to limit in its time usage.

Hope this helps

---

### Post by SanskritFritz on 2008-09-29
Hi there, thanks for that script!
I'm using Kubuntu Hardy, and there are no notifications coming. I know this problem is not timekpr specific, as even 
```
notify-send "hello"
```doesnt do the magic. But please can you point me to the right direction with this problem? Do I have to install some kind of a "notification-demon" in KDE? I have the following packages installed:
libnotify-bin
libnotify-doc
libnotify1
python-notify

---

### Post by .nedberg on 2008-09-30
Yes, we know! The main script works, but no notifications show. I am not sure the GUI works either.

Right now development are going into pythonizing the script, making it easier to maintain and extend.

I am a Kubuntu/KDE user my self and I want to make a KDE version. This will have to wait until we reach a stable state though.

---

### Post by SanskritFritz on 2008-09-30
Ok, I understand this, but why is there no notification at all when I issue this command?
```
notify-send "hello"
``` Totally irrespectively of timekpr, sorry for offtopic.

---

### Post by .nedberg on 2008-09-30
notify-send uses dbus to get the session bus. KDE doesn't use dbus (at least not in KDE 3.5).

---

### Post by forger on 2008-09-30
> **bedege said:**
> The content of /var/log/timekpr.log
```
benoit@tatihou:~$ cat /var/log/timekpr.log 
2008-09-29 22:41:03 +0200 Started timekpr
```


There are no messages in the log file, that's really weird.
Here is what I want you to do:
1) System > Administration > Timekeeper
or run in terminal ```
gksu /usr/bin/timekpr-gui
```
2) Select the user you want to limit from the drop down list
3) Edit your limits properly, for testing purposes make it short, e.g. 2 minutes
4) Press Apply and then Quit
5) Log out your account
6) Log in with the limited user account
7) Let it pass the time period limit you applied, e.g. if you put 2 minutes, you should wait about 5 minutes (your limit + 3 minutes) for the program to kick the user automatically.
8 ) If the user _was not kicked_ post the reply of these commands:
```
ls -lR /var/lib/timekpr/
cat /var/lib/timekpr/*
cat /var/log/timekpr.log
```
If the user got kicked, well.. then it probably does the job? :)

---

### Post by bedege on 2008-09-30
Well, thanks Forger for your help. I did as proposed and was not kicked off my computer under my son's login...
```

benoit@tatihou:~$ ls -lR /var/lib/timekpr/
/var/lib/timekpr/:
total 4
-rw-r--r-- 1 root root 89 2008-09-30 22:58 guy
-rw-r--r-- 1 root root  0 2008-09-30 22:58 guy.allow
benoit@tatihou:~$ cat /var/lib/timekpr/*
limit=( 120 120 120 120 120 120 120 )
from=( 0 0 0 0 0 0 0 )
to=( 24 24 24 24 24 24 24 )
benoit@tatihou:~$ cat /var/log/timekpr.log 
2008-09-30 18:54:26 +0200 Started timekpr
```

Again, I'm using Xubuntu Hardy, so that might not help.

Cheers

---

### Post by forger on 2008-09-30
You have .allow that bypasses the system's check for the user.. but the weird thing is that there is no output, it should've caught the user :)
do this: ```
sudo rm -f /var/lib/timekpr/guy.allow
```

> Again, I'm using Xubuntu Hardy, so that might not help.
I know, but nevertheless, the program should kick the user.. maybe it doesn't use x-session-manager.
Just out of curiosity, does xfce have fast switching support? Is there a "Switch user" in Logout or Shutdown menus?
If there is, log in with your administrator account and then switch to user "guy". Then switch back to the administrator and execute this:
```
ps -fC x-session-manager
ps -fC xfce4-session
```

---

### Post by .nedberg on 2008-10-01
Just made a VM for Xubuntu Hardy, I'll answer this one:
> **forger said:**
> 
```
ps -fC x-session-manager
ps -fC xfce4-session
```

```
even@VM-XHardy:~$ ps -fC x-session-manager
UID        PID  PPID  C STIME TTY          TIME CMD
even      4833  4592  0 09:33 ?        00:00:00 x-session-manager
even@VM-XHardy:~$ ps -fC xfce4-session
UID        PID  PPID  C STIME TTY          TIME CMD
even@VM-XHardy:~$ 

```
I installed the script and limited my own user (did not get the time to add another user) and the script works fine. I do not know why bedege has problems with the script, but it looks like it should work fine with a vanilla Xubuntu.

---

### Post by .nedberg on 2008-10-01
I spoke too soon!

It looks like Xubuntu doesn't use x-session-manager in the same way as Ubuntu.

This is the output of the same commands when only logged in as a testuser

```

test1@VM-XHardy:~$ ps -fC x-session-manager
UID        PID  PPID  C STIME TTY          TIME CMD
test1@VM-XHardy:~$ ps -fC xfce4-session
UID        PID  PPID  C STIME TTY          TIME CMD
test1     4911  4854  0 10:07 ?        00:00:00 /usr/bin/xfce4-session

```

---

### Post by forger on 2008-10-01
Well.. we'll put that in our to-do list!
I wonder if we can kill using the pid of gnome-session, xfce4-session, etc. using for example /usr/share/xsessions/gnome.desktop for gnome :)
[http://packages.ubuntu.com/search?searchon=contents&keywords=-session&mode=&suite=hardy&arch=any](http://packages.ubuntu.com/search?searchon=contents&keywords=-session&mode=&suite=hardy&arch=any)
In kde it's probably [http://packages.ubuntu.com/hardy/ksmserver](http://packages.ubuntu.com/hardy/ksmserver) but as I remember, .nedberg you noted that you get kicked and that only notification isn't working (we could do that too with knotify I suppose)

edit: the problem is with pam.d services, I don't know if xfce and kde have for example files such as /etc/pam.d/kde

---

### Post by .nedberg on 2008-10-01
I'll give it another test in Kubuntu with an other user than my own. It might be that we get the same problem as Xubuntu.

Add it to TO-DO list!

---

### Post by SanskritFritz on 2008-10-01
I can confirm, kicking the user on time works well in Kubuntu.

---

### Post by .nedberg on 2008-10-01
> **SanskritFritz said:**
> I can confirm, kicking the user on time works well in Kubuntu.

Yes, I just finished testing and it works fine. Not sure about boundaries, but limits works fine. No notification though!

The launcher for timekpr-gui does not work, it need to be run with kdesu, not gksu as the .deb makes it (it shows in the menu, but without icon).

---

### Post by bedege on 2008-10-01
I see that .nedberg has already done the test w/ Xubuntu I could have done later tonight at home. Do you need more from me ?

What if I want to test the pythonized version of timekpr. How should I install it once I have downloaded the sources files from Launchapd ? I'm still unclear about that one.

---

### Post by .nedberg on 2008-10-01
> **bedege said:**
> I see that .nedberg has already done the test w/ Xubuntu I could have done later tonight at home. Do you need more from me ?

What if I want to test the pythonized version of timekpr. How should I install it once I have downloaded the sources files from Launchapd ? I'm still unclear about that one.

I don't think we need more info. But that might change.

About the pythonized version;
Short answer: don't install it!
Long answer: DL the source files and overwrite the according files on your machine. timekpr.py must be moved to /usr/bin/timekpr. But I warn you, I would NOT do this on a system you use! I am going to do it in a VM soon, if you want to help testing that is what you should do!

---

### Post by forger on 2008-10-01
I need someone with Xubuntu and someone with Kubuntu to post the output of:
```
ls -l /etc/pam.d/
```

thanks :)

---

### Post by SanskritFritz on 2008-10-01
Kubuntu:

```
frank@HomeC:~$ ls -l /etc/pam.d/
total 88
-rw-r--r-- 1 root root  182 2007-02-20 14:41 atd
-rw-r--r-- 1 root root  384 2008-04-03 03:02 chfn
-rw-r--r-- 1 root root  581 2008-04-03 03:02 chsh
-rw-r--r-- 1 root root  392 2008-07-01 22:49 common-account
-rw-r--r-- 1 root root  484 2008-07-01 22:50 common-auth
-rw-r--r-- 1 root root 1571 2008-07-01 22:50 common-password
-rw-r--r-- 1 root root  372 2008-07-01 22:49 common-session
-rw-r--r-- 1 root root  289 2008-04-08 20:02 cron
-rw-r--r-- 1 root root   69 2008-04-21 22:15 cupsys
-rw-r--r-- 1 root root  164 2008-05-07 09:58 kcheckpass
-rw-r--r-- 1 root root  345 2008-05-07 09:58 kdm
-rw-r--r-- 1 root root  389 2008-05-07 09:58 kdm-np
-rw-r--r-- 1 root root  168 2008-05-07 09:58 kscreensaver
-rw-r--r-- 1 root root 3224 2008-04-03 03:02 login
-rw-r--r-- 1 root root  520 2008-04-09 22:22 other
-rw-r--r-- 1 root root   92 2008-04-03 03:02 passwd
-rw-r--r-- 1 root root  105 2008-04-19 06:43 polkit
-rw-r--r-- 1 root root  168 2007-10-04 21:56 ppp
-rw-r--r-- 1 root root   69 2008-06-30 17:56 samba
-rw-r--r-- 1 root root 1272 2008-05-14 16:33 sshd
-rw-r--r-- 1 root root 2305 2008-04-03 03:02 su
-rw-r--r-- 1 root root   56 2008-02-25 12:22 sudo
```

---

### Post by forger on 2008-10-01
Cool, and Xubuntu uses gdm.. I was having double thoughts about using linux-pam, but now since all three of the main ones have /etc/pam.d/ service files I can continue to improve the restrictions :)
Edit: Forgot to explain, linux-pam will be used to block the user entirely from logging in using /etc/security/access.conf and /etc/security/time.conf - and timekpr-gui will take care of the details ( hopefully ;) )

---

### Post by forger on 2008-10-01
Here's a sneak-peek of the new experimental timekpr-gui, now that I got the hang of glade and python gtk I think I can expand and work it out properly:)

---

### Post by crjackson on 2008-10-01
> **forger said:**
> Here's a sneak-peek of the new experimental timekpr-gui, now that I got the hang of glade and python gtk I think I can expand and work it out properly:)

A true work of art. You and .nedberg are amazing... :D

I can't wait to see the next deb release.

---

### Post by jeromio on 2008-10-01
Indeed. Having some troubles with Kubuntu, looking forward to the new revision. Currently, on Kubuntu 8, it mostly works. I edited the gsu line to be kdesu in the launcher. 

The 2 issues I have are: 
1 - If the user locks her session (or if it auto-locks out due to time-out), the timer on timekpr keeps ticking, so they get logged off for the day. 
2 - There's no warning, users are just instantly logged off.

There is a 3rd, more minor issue which is that users can sometimes log back in and get 4 minutes before being logged off again. Seems to only work when they log back in immediately.

Even with those problems, this is still a very useful tool for easily putting boundaries on computer use.

---

### Post by .nedberg on 2008-10-02
> **forger said:**
> I need someone with Xubuntu and someone with Kubuntu to post the output of:
```
ls -l /etc/pam.d/
```


Xubuntu Hardy:
```

even@VM-XHardy:~$ ls -l /etc/pam.d/
total 80
-rw-r--r-- 1 root root  182 2007-02-20 14:41 atd
-rw-r--r-- 1 root root  384 2008-04-03 03:02 chfn
-rw-r--r-- 1 root root  581 2008-04-03 03:02 chsh
-rw-r--r-- 1 root root  392 2008-07-02 12:47 common-account
-rw-r--r-- 1 root root  484 2008-07-02 12:47 common-auth
-rw-r--r-- 1 root root 1571 2008-07-02 12:47 common-password
-rw-r--r-- 1 root root  372 2008-07-02 12:47 common-session
-rw-r--r-- 1 root root  289 2008-04-08 20:02 cron
-rw-r--r-- 1 root root   69 2008-04-21 22:15 cupsys
-rw-r--r-- 1 root root  400 2008-05-21 16:48 gdm
-rw-r--r-- 1 root root  316 2008-05-21 16:48 gdm-autologin
-rw-r--r-- 1 root root   56 2008-04-09 17:05 gnome-screensaver
-rw-r--r-- 1 root root 3224 2008-04-03 03:02 login
-rw-r--r-- 1 root root  520 2008-04-09 22:22 other
-rw-r--r-- 1 root root   92 2008-04-03 03:02 passwd
-rw-r--r-- 1 root root  105 2008-04-19 06:43 polkit
-rw-r--r-- 1 root root  168 2007-10-04 21:56 ppp
-rw-r--r-- 1 root root   69 2008-06-30 17:56 samba
-rw-r--r-- 1 root root 2305 2008-04-03 03:02 su
-rw-r--r-- 1 root root   56 2008-02-25 12:22 sudo

```

Ubuntu Intrepid:
```

even@VM-Intrepid:~$ ls -l /etc/pam.d/
total 80
-rw-r--r-- 1 root root  182 2008-07-10 17:01 atd
-rw-r--r-- 1 root root  384 2008-06-09 20:02 chfn
-rw-r--r-- 1 root root  581 2008-06-09 20:02 chsh
-rw-r--r-- 1 root root 1186 2008-09-30 14:37 common-account
-rw-r--r-- 1 root root 1221 2008-09-30 14:37 common-auth
-rw-r--r-- 1 root root 1584 2008-09-30 14:37 common-password
-rw-r--r-- 1 root root 1309 2008-09-30 14:37 common-session
-rw-r--r-- 1 root root  289 2008-09-09 21:45 cron
-rw-r--r-- 1 root root   69 2008-09-13 11:37 cups
-rw-r--r-- 1 root root  400 2008-09-04 14:53 gdm
-rw-r--r-- 1 root root  316 2008-09-04 14:53 gdm-autologin
-rw-r--r-- 1 root root   56 2008-09-10 22:23 gnome-screensaver
-rw-r--r-- 1 root root 3224 2008-06-09 20:02 login
-rw-r--r-- 1 root root  520 2008-09-16 09:12 other
-rw-r--r-- 1 root root   92 2008-06-09 20:02 passwd
-rw-r--r-- 1 root root  105 2008-08-06 10:24 polkit
-rw-r--r-- 1 root root  168 2008-06-23 14:12 ppp
-rw-r--r-- 1 root root   69 2008-09-12 16:23 samba
-rw-r--r-- 1 root root 2305 2008-06-09 20:02 su
-rw-r--r-- 1 root root  119 2008-09-01 15:17 sudo

```

---

### Post by .nedberg on 2008-10-02
> **jeromio said:**
> Indeed. Having some troubles with Kubuntu, looking forward to the new revision. Currently, on Kubuntu 8, it mostly works. I edited the gsu line to be kdesu in the launcher. 

The 2 issues I have are: 
1 - If the user locks her session (or if it auto-locks out due to time-out), the timer on timekpr keeps ticking, so they get logged off for the day. 
2 - There's no warning, users are just instantly logged off.

There is a 3rd, more minor issue which is that users can sometimes log back in and get 4 minutes before being logged off again. Seems to only work when they log back in immediately.

Even with those problems, this is still a very useful tool for easily putting boundaries on computer use.

@1 - We will see what we can do about that. We will have to find a way to see if the screen is locked or not. A restricted user should not do this the way the script works now.

@2 - No, there are no warnings in Kubuntu, we will start working on that when the Gnome version is "finished"

@3 - We could lock users immediately when they are logged out. We will see!

---

### Post by forger on 2008-10-02
Another sneak-peek.. I think this will be the final one:
[ATTACH]87070[/ATTACH]

* We managed to merge "Status", "Rewards" and "Unlock" tabs into one! (in other words: more control with less clicking :D)
* The final logo will probably be the padlock with the clock (modified version), since both are released with public domain licenses, and out of respect I'll be releasing the logo in public domain too :)
* I renamed the checkboxes for limits, still testing various names, I hope these labels are good :\ (Other candidates come to mind, such as "Limit access span" for the duration time limit)

---

### Post by SanskritFritz on 2008-10-02
Amazing stuff! Can't wait for the final Kubuntu version!!!! :D

---

### Post by crjackson on 2008-10-02
> **forger said:**
> Another sneak-peek.. I think this will be the final one:
[ATTACH]87070[/ATTACH]

* We managed to merge "Status", "Rewards" and "Unlock" tabs into one! (in other words: more control with less clicking :D)
* The final logo will probably be the padlock with the clock (modified version), since both are released with public domain licenses, and out of respect I'll be releasing the logo in public domain too :)
* I renamed the checkboxes for limits, still testing various names, I hope these labels are good :\ (Other candidates come to mind, such as "Limit access span" for the duration time limit)

I vote for:
Limit Duration
Limit Time Frame

Keep it simple and non-geekish sounding if possible. Better for "Users".

---

### Post by forger on 2008-10-03
I like the first one :)
I'm still unsure about "Limit time frame", but to be honest, in the end it doesn't really matter, as I can add a relatively huge tooltip (a small "popup") explaining what it does. I'll add "Limit time frame", any objections?

Can you also come up with any messages for their tooltips? Thanks :)

---

### Post by .nedberg on 2008-10-03
I liked "Access hours". But as you said it doesn't matter if it gets a tooltip!

---

### Post by bedege on 2008-10-03
> **forger said:**
> Cool, and Xubuntu uses gdm.. I was having double thoughts about using linux-pam, but now since all three of the main ones have /etc/pam.d/ service files I can continue to improve the restrictions :)
Edit: Forgot to explain, linux-pam will be used to block the user entirely from logging in using /etc/security/access.conf and /etc/security/time.conf - and timekpr-gui will take care of the details ( hopefully ;) )

Forger,
Are you referring to improvements you're committing to the python beta release these days ? In other words, shall I wait for this python version and forget the original bash scripts (the ones currently available in a deb package) if I want to use timekpr on Xubuntu 8.04 ?
Thks

---

### Post by forger on 2008-10-03
> **bedege said:**
> Forger,
Are you referring to improvements you're committing to the python beta release these days ? In other words, shall I wait for this python version and forget the original bash scripts (the ones currently available in a deb package) if I want to use timekpr on Xubuntu 8.04 ?
Thks

I can't guarantee nor promise anything, we focus on getting a working release for gnome, we'll see about xfce and kde in future releases. For now it's gnome only I'm afraid :(

---

### Post by bedege on 2008-10-03
> **forger said:**
> I can't guarantee nor promise anything, we focus on getting a working release for gnome, we'll see about xfce and kde in future releases. For now it's gnome only I'm afraid :(
OK, I perfectly understand your focus on Gnome at the moment. Have you identified the issue w/ Xfce though ?

---

### Post by forger on 2008-10-03
I think so, as Even revealed in a previous post, it probably handles the sessions and x-session-manager differently than gnome.
I believe it could work if we grab the "Exec" line and its command from each file in /usr/share/xsessions/ directory - this way we could get all the active sessions

Edit:
In my case (GNOME in Intrepid Ibex), the x-session-manager appears only after another person other than myself logs in.
```
$ ps -fC x-session-manager
UID        PID  PPID  C STIME TTY          TIME CMD

```
But if I detect gnome-session instead:
```

$ ps -fC gnome-session
UID        PID  PPID  C STIME TTY          TIME CMD
userer    8274  8205  0 15:15 ?        00:00:00 /usr/bin/gnome-session

```

---

### Post by crjackson on 2008-10-03
> **forger said:**
> I like the first one :)
I'm still unsure about "Limit time frame", but to be honest, in the end it doesn't really matter, as I can add a relatively huge tooltip (a small "popup") explaining what it does. I'll add "Limit time frame", any objections?

Can you also come up with any messages for their tooltips? Thanks :)

**Limit Duration**
Limits the druation of time the selected user can remain logged on each day. Un-checking this option removes the duration limits.

**Authorized Hours** (may be better than time frame?)
Limits the authorized hours of operation for the selected user. Un-checking this option removes authorization limits.

Ponder this and let me know...

-charles

---

### Post by forger on 2008-10-04
The following two weeks the project might go a bit slower, I'll be away for 4-5 days :)

See ya in a few days!

---

### Post by .nedberg on 2008-10-04
And I'll be away ten days after that. forger and I just had a talk and we have made plans for how to keep the project evolving when one of us are away. We are (hopefully) getting closer to a new release!

---

### Post by crjackson on 2008-10-04
That's great news, but you guys probably should take a break from it all. New ideas always spawn after a break from the frenzy.

Thanks for all the hard work.

---

### Post by forger on 2008-10-11
well after .nedberg's input, the new timekpr seems to be mostly working, I'll give it a spin tonight, see how it goes and start fixing glitches :)

---

### Post by crjackson on 2008-10-11
> **forger said:**
> well after .nedberg's input, the new timekpr seems to be mostly working, I'll give it a spin tonight, see how it goes and start fixing glitches :)

Good to hear...

---

### Post by forger on 2008-10-19
Ladies and gentlemen,
I'm sorry I couldn't find Even to approve the beta release, but I believe it's ripe enough for some beta testing! Even and I have done some basic testing, Charles Jackson (crjackson) has given it a swirl too, most of the stuff work as expected, features are automatically installed and activated.

Version 0.2.2~b1 (beta 1) released

I pushed the version up from 0.2.0 due to renaming it to beta for easier version tracking :)

Feeling risky? Get it here: [http://savvas.radevic.com/timekpr/](http://savvas.radevic.com/timekpr/)

All bugs reports welcome at [http://bugs.launchpad.net/timekpr](http://bugs.launchpad.net/timekpr)


Things to test:
check:
1) If there's a section "## TIMEKPR START" and "## TIMEKPR END" in files:
```
/etc/security/access.conf
/etc/security/time.conf

```

2) If you can see this code:
```
account required pam_time.so
account required pam_access.so
```
in these files:
```

/etc/pam.d/login
/etc/pam.d/gdm

```

The current file directory is:
- configuration at file /etc/timekpr.conf and folder /etc/timekpr/ (per user and .lock files)
- running files (.time .logout .late) at folder /var/lib/timekpr/
- various support files at folder
/usr/share/python-support/timekpr/
and folder
/usr/share/timekpr/

You can start stop timekpr:
```
sudo /etc/init.d/timekpr start
sudo /etc/init.d/timekpr stop
```

You can run timekpr in foreground (not as a service daemon) so you can see any crash problems:
```
sudo /etc/init.d/timekpr stop
sudo timekpr
```

You can see what's going on in the background in the log file:
```
/var/log/timekpr.log
```[/QUOTE]

---

### Post by crjackson on 2008-10-19
> **forger said:**
> Ladies and gentlemen,
I'm sorry I couldn't find Even to approve the beta release, but I believe it's ripe enough for some beta testing! Even and I have done some basic testing, Charles Jackson (crjackson) has given it a swirl too, most of the stuff work as expected, features are automatically installed and activated.

Version 0.2.2~b1 (beta 1) released

I pushed the version up from 0.2.0 due to renaming it to beta for easier version tracking :)

Feeling risky? Get it here: [http://savvas.radevic.com/timekpr/](http://savvas.radevic.com/timekpr/)

All bugs reports welcome at [http://bugs.launchpad.net/timekpr](http://bugs.launchpad.net/timekpr)


Things to test:
check:
1) If there's a section "## TIMEKPR START" and "## TIMEKPR END" in files:
```
/etc/security/access.conf
/etc/security/time.conf

```

2) If you can see this code:
```
account required pam_time.so
account required pam_access.so
```
in these files:
```

/etc/pam.d/login
/etc/pam.d/gdm

```

The current file directory is:
- configuration at file /etc/timekpr.conf and folder /etc/timekpr/ (per user and .lock files)
- running files (.time .logout .late) at folder /var/lib/timekpr/
- various support files at folder
/usr/share/python-support/timekpr/
and folder
/usr/share/timekpr/

You can start stop timekpr:
```
sudo /etc/init.d/timekpr start
sudo /etc/init.d/timekpr stop
```

You can run timekpr in foreground (not as a service daemon) so you can see any crash problems:
```
sudo /etc/init.d/timekpr stop
sudo timekpr
```

You can see what's going on in the background in the log file:
```
/var/log/timekpr.log
```

Thanks, so far so good. I'll let you know what I find.

btw - Nice new Avatar... :)

---

### Post by crjackson on 2008-10-19
Forger, I've checked for the listed files and entries you mentioned and EVERYTHING is in place. So far I haven't found any issues.

I'll be making some settings adjustments to the kids systems tomorrow and I'll let you know how it all turns out. Thanks to you and Even for all your hard work on this.

-Charles

---

### Post by forger on 2008-10-19
> **crjackson said:**
> btw - Nice new Avatar... :)
Thanks :D

by the way, I might release an rpm build (using alien). Any Fedora/RedHat/CentOS users around?

---

### Post by SanskritFritz on 2008-10-20
This still won't work in KDE, right?

---

### Post by forger on 2008-10-20
Well the notifications no, but forcing the user to log out works, if I remember correctly :)
Next release will include a few more buttons for the service (Start/Stop and "Service files" cleanup) and we'll search for a way to include support for kde and xfce

---

### Post by bedege on 2008-10-20
> **SanskritFritz said:**
> This still won't work in KDE, right?
And similarly, won't work with Xubuntu either ?

---

### Post by .nedberg on 2008-10-20
timekpr won't work in anything else than Ubuntu with Gnome at the moment. We will have a look at other DE when we feel the Gnome version is working satisfactory.

I am a KDE user myself and really want it to work!

---

### Post by SanskritFritz on 2008-10-20
> **.nedberg said:**
> I am a KDE user myself and really want it to work!Hopes, hopes... :)

---

### Post by .nedberg on 2008-10-20
I am not getting any notifications in Hardy. It does not get any DBUS_SESSION_BUS_ADDRESS and timekpr crashes. I am not reporting this as a bug yet, as I don't know if I am the only one with this problem. Intrepid works fine.

I have tested on two VirtualBox VMs of Hardy and one laptop, same problem on all of them.

/proc/<pid>/environ does not contain a DBUS_SESSION_BUS_ADDRESS!

I know timekpr used to work on the laptop and one of the VMs. The other VM is all new today and just updated (no backports or anything non-standard).

Timekpr should not crash when it cannot find dbus-address, maybe we should try with a try-except block?

I am back now and I will focus on testing and bug tracking for a while. It helps me read up on what forger has done while I was away. He has done some great work!

---

### Post by crjackson on 2008-10-20
> **.nedberg said:**
> I am not getting any notifications in Hardy. It does not get any DBUS_SESSION_BUS_ADDRESS and timekpr crashes. I am not reporting this as a bug yet, as I don't know if I am the only one with this problem. Intrepid works fine.


.nedberg,

I'll try to confirm this tonight when I get home. I've set up 3 systems with the latest build.

---

### Post by crjackson on 2008-10-21
> **.nedberg said:**
> I am not getting any notifications in Hardy. It does not get any DBUS_SESSION_BUS_ADDRESS and timekpr crashes. I am not reporting this as a bug yet, as I don't know if I am the only one with this problem. Intrepid works fine.

I have tested on two VirtualBox VMs of Hardy and one laptop, same problem on all of them.

/proc/<pid>/environ does not contain a DBUS_SESSION_BUS_ADDRESS!

I know timekpr used to work on the laptop and one of the VMs. The other VM is all new today and just updated (no backports or anything non-standard).

Timekpr should not crash when it cannot find dbus-address, maybe we should try with a try-except block?

I am back now and I will focus on testing and bug tracking for a while. It helps me read up on what forger has done while I was away. He has done some great work!

I just did a fresh install of Hardy 8.04.1 and installed the newest timekpr. I created an account called test and set time limits to 2 min.

I got no notifications and the user was never kicked off.

---

### Post by .nedberg on 2008-10-22
Bug#287012 is now fixed in revision 119.

This is just a temporary fix. We need to do something else to get the notifications working. We will probably start writing a client that will take care of the notifications. This will, hopefully, also result in a kde/xfce version :guitar:

DL timekpr.py from launchpad [here]("http://bazaar.launchpad.net/~timekpr-maintainers/timekpr/trunk/download/119/timekpr.py-20080921200211-me81g2w0v2jkzznp-1/timekpr.py?file_id=timekpr.py-20080921200211-me81g2w0v2jkzznp-1") and replace /usr/share/python-support/timekpr/timekpr.py with the new version.

Restart timekpr afterwards
```

sudo /etc/init.d/timekpr restart

```

As usual: Please report bugs at [https://bugs.launchpad.net/timekpr](https://bugs.launchpad.net/timekpr)

---

### Post by crjackson on 2008-10-22
> **.nedberg said:**
> Bug#287012 is now fixed in revision 119.

This is just a temporary fix. We need to do something else to get the notifications working. We will probably start writing a client that will take care of the notifications. This will, hopefully, also result in a kde/xfce version too :guitar:

DL timekpr.py from launchpad [here]("http://bazaar.launchpad.net/~timekpr-maintainers/timekpr/trunk/download/119/timekpr.py-20080921200211-me81g2w0v2jkzznp-1/timekpr.py?file_id=timekpr.py-20080921200211-me81g2w0v2jkzznp-1") and replace /usr/share/python-support/timekpr/timekpr.py with the new version.

As usual: Please report bugs at [https://bugs.launchpad.net/timekpr](https://bugs.launchpad.net/timekpr)

I'll grab it when I get home tonight...

---

### Post by forger on 2008-10-24
0.2.2~b2 beta 2 :)
[https://launchpad.net/timekpr/+announcement/1294](https://launchpad.net/timekpr/+announcement/1294)
[http://savvas.radevic.com/timekpr/](http://savvas.radevic.com/timekpr/)

---

### Post by crjackson on 2008-10-24
Thanks forger. You can also [**[COLOR="Blue"]get it here[/COLOR]**]("http://ubuntuforums.org/showthread.php?t=887769") on the first post of this thread :)

---

### Post by forger on 2008-10-24
I think they require you to login in order to download something, but thanks, didn't see that you had it posted :)

---

### Post by crjackson on 2008-10-24
> **forger said:**
> I think they require you to login in order to download something, but thanks, didn't see that you had it posted :)

It's posted there and on the blog. It's already been downloaded twice this morning from the blog.

---

### Post by forger on 2008-10-26
Just to notify the subscribers of this topic (if any), I've set up a blog at [http://timekpr.blogspot.com](http://timekpr.blogspot.com) - crjackson, .nedberg, nlaurance and I are set as permitted as authors :)

Also, there's a voting poll set up about the features that we'll focus on the following release!

---

### Post by dennus on 2008-10-26
Hi guys, do you need any help translating Timekpr into Dutch?

---

### Post by .nedberg on 2008-10-26
> **dennus said:**
> Hi guys, do you need any help translating Timekpr into Dutch?

Yes, eventually we will. We haven't reached the point where timekpr is easily translated yet, but it is planned in a future release. Right now we are focusing on putting the parts together, making it work with the major DEs and general clean up of the code. Adding support for more languages and translations will come. Follow this thread or the timekpr project at launchpad and you will know when we get there!

---

### Post by dennus on 2008-10-26
OK, I will....

---

### Post by SanskritFritz on 2008-11-08
Anyone played with this?
[http://torvalds-family.blogspot.com/2008/10/tracking-time-kids-spend-online.html](http://torvalds-family.blogspot.com/2008/10/tracking-time-kids-spend-online.html)

---

### Post by crjackson on 2008-11-08
> **SanskritFritz said:**
> Anyone played with this?
[http://torvalds-family.blogspot.com/2008/10/tracking-time-kids-spend-online.html](http://torvalds-family.blogspot.com/2008/10/tracking-time-kids-spend-online.html)

No, check it out and give us a report if you don't mind. It sounds very basic.

---

### Post by crjackson on 2008-11-15
Hey, did you guys notice we're on [SOFTPEDIA]("http://linux.softpedia.com/get/Utilities/Timekpr-42110.shtml") with 102 downloads from there?

Savvas - Did you put it there?

---

### Post by shane2peru on 2008-11-15
Hey, great app!!!  I haven't re-installed since the very early days, when you installed and setup the scripts yourself!  Love the GUI, it is very nice, my wife can use this to manage the kids accounts :D

Shane

---

### Post by crjackson on 2008-11-15
> **shane2peru said:**
> Hey, great app!!!  I haven't re-installed since the very early days, when you installed and setup the scripts yourself!  Love the GUI, it is very nice, my wife can use this to manage the kids accounts :D

Shane

Yes it has come a long way... :)

---

### Post by shane2peru on 2008-11-15
You guys have done a great job on this, that is for sure!  Thanks for the work you have done.

Shane

---

### Post by forger on 2008-11-16
Um, a small update (after so many days), .nedberg is playing around with separate application (timekpr-client), which would hopefully solve problems for XFCE and KDE and the notification popups etc.

I'm trying to make standardize our code to make a python package (called python eggs). Nicolas has been helping me a lot with this. I have it in a separate branch-site, it will be merged when it is finished.
[https://code.edge.launchpad.net/~medigeek/timekpr/experimental](https://code.edge.launchpad.net/~medigeek/timekpr/experimental)
(Let's just hope that I'll manage to make it work in the future)
It's going slowly, it will take some time to finish it, unless someone else more experienced than me finishes it up. Either way, I am not going to be very active until January, until I make this thing work (along with dbus communication between timekpr-daemon and timekpr-client).

Nicolas is actually trying to make things work for an enterprise (aka really stable) release in the future and timekpr command line, he's done a great job so far!

---

### Post by .nedberg on 2008-11-20
I have made a new .deb. It includes the new timekpr-client, along with some known and unknown bugs :)

- It should work just as good as b2 in Gnome (but perhaps be a bit more annoying to the user)
- I don't think it works in XFCE, but I would like feedback on weather the client works
- It should work in KDE4 and probably in KDE3

The new .deb is available at:
[http://www.nedberg.net/timekpr_0.2.2~b3_all.deb](http://www.nedberg.net/timekpr_0.2.2~b3_all.deb)

This version is _not_ recommended to replace b2 on a working install, it is just meant for testing.

I just made some changes to the .deb, if you already dl'ed it, do it again!

---

### Post by crjackson on 2008-11-20
> **.nedberg said:**
> I have made a new .deb. It includes the new timekpr-client, along with some known and unknown bugs :)

- It should work just as good as b2 in Gnome (but perhaps be a bit more annoying to the user)
- I don't think it works in XFCE, but I would like feedback on weather the client works
- It should work in KDE4 and probably in KDE3

The new .deb is available at:
[http://www.nedberg.net/timekpr_0.2.2~b3_all.deb](http://www.nedberg.net/timekpr_0.2.2~b3_all.deb)

This version is _not_ recommended to replace b2 on a working install, it is just meant for testing.

I just made some changes to the .deb, if you already dl'ed it, do it again!

I'll take it around the block for a spin this weekend. Should I anticipate anything in particular?

---

### Post by .nedberg on 2008-11-21
> **crjackson said:**
> I'll take it around the block for a spin this weekend. Should I anticipate anything in particular?

This is some of the things I can think of, I you can cover some of them I will be very pleased!

- Check if the client starts when a user logs in
- The client should give notifications with the time left every 15 minutes at first, then more often when time is running out.
- The client does not notify if the user is outside of time frame.
- If you can, check if the client works in XFCE
- Check if timekpr works when no access limits is set (only "Limit time frame")
- You will probably get a lot of notifications, at least when you are about to be logged out. The client will probably give some strange notifications at this time!
- KDE testing is needed, both 4 and 3

I haven't done much to timekpr, so it _should_ work as it used to.

---

### Post by crjackson on 2008-11-21
> **.nedberg said:**
> This is some of the things I can think of, I you can cover some of them I will be very pleased!

- Check if the client starts when a user logs in
- The client should give notifications with the time left every 15 minutes at first, then more often when time is running out.
- The client does not notify if the user is outside of time frame.
- If you can, check if the client works in XFCE
- Check if timekpr works when no access limits is set (only "Limit time frame")
- You will probably get a lot of notifications, at least when you are about to be logged out. The client will probably give some strange notifications at this time!
- KDE testing is needed, both 4 and 3

I haven't done much to timekpr, so it _should_ work as it used to.

Gotcha - I'll check as much of it as I can. I'll do an install of xbuntu and one of kubuntu. Down the road I would like to see an option for either turning off all those 15 minute notifications or adjusting them somehow. I kind of like the way they are now, and would like the option to keep them that way.

---

### Post by SanskritFritz on 2008-11-21
Wow, a long awaited release! As soon as I got the time i started to test this jewel at my Kubuntu Hardy. Here is the install log (there seems to be a problem):

> 
Do you want to install the software package? [y/N]:y
Selecting previously deselected package timekpr.
(Reading database ... 212341 files and directories currently installed.)
Unpacking timekpr (from timekpr_0.2.2~b3_all.deb) ...
Setting up timekpr (0.2.2~b3) ...
Installing new version of config file /etc/init.d/timekpr ...
Installing new version of config file /etc/timekpr.conf ...
[COLOR=Red]Couldn't find /etc/pam.d/gdm (oops?)[/COLOR]
Checking for pam_time.so in /etc/pam.d/login
Checking for pam_access.so in /etc/pam.d/login
 * Starting computer usage control daemon timekpr                                                                                                                [ OK ]After this I couldnt find the demon running in the task list. I set 10 minutes for another user, switched to it, and it constantly nags with "Your time is up" and if I click on the icon in the notification area, it says "You have 57 minutes and 15 seconds left". The user was never kicked, I guess because the demon is not running? I didnt restart the computer yet.
Please, please keep up the good work, this will be an awesome tool for us parents! I got 5 kids, its hard to keep up with the times allotted to use their account otherwise :-)

---

### Post by .nedberg on 2008-11-22
Look like there is a bug that makes timekpr.py crash in the .deb. It is because Bug#287012 is not entirely fixed.

In /usr/share/python-support/timekpr/timekprpam.py change getuserlimits into
```

def getuserlimits(u):
    """Gets user from-to time limitations defined in time.conf

    Argument: username
    Return example:
        [0] = from ['0', '0', '0', '0', '0', '0', '0']
        [1] = to ['24', '24', '24', '24', '24', '24', '24']

    """
[COLOR="Red"]    bf = ['0', '0', '0', '0', '0', '0', '0']
    bt =  ['24', '24', '24', '24', '24', '24', '24'][/COLOR]
    ls = parseutlist(parsetimeconf())
    for user, [bfrom, bto] in ls:
        if u == user:
            return [bfrom, bto]
    return [[COLOR="#ff0000"]bf, bt[/COLOR]]

```

Also in /usr/share/python-support/timekpr.py comment out lines 199, 200 and 202 to make it work in Kubuntu 8.10 (but sadly no notifications with the client :( ). It will not work in Ubuntu 8.04 if you do this!

---

### Post by .nedberg on 2008-11-22
I just put a new version of the .deb on my page (see earlier post for link). It reflects rev 145 and includes the changes to timekprpam.py. It does NOT include the changes to timekpr.py because that could break something more.

---

### Post by SanskritFritz on 2008-11-22
So, do I have to change this in the deb package? I did the change in the installed file, restarted the timekpr service (still dont see the process in the tastlist), and now the click on the icon tells me the correct time left, but, it doesnt count down, and the Time is up nag is still present.

EDIT: oops, didnt see your last post. I'll download it now, and report.

---

### Post by SanskritFritz on 2008-11-22
> **.nedberg said:**
> I just put a new version of the .deb on my page (see earlier post for link). It reflects rev 145 and includes the changes to timekprpam.py. It does NOT include the changes to timekpr.py because that could break something more.Ok, short test result: after installing the new deb, I saw the demon process running, but as soon I switched to the test user, it crashed. All I was able to find in the logs was this (frank is my user, with no restrictions, dani is the test user, with 10 minutes restriction):
```
2008-11-22 23:21:50 Starting timekpr version 0.2.2
2008-11-22 23:21:50 Variables: GRACEPERIOD: 120 POLLTIME: 45 DEBUGME: True LOCKLASTS: 1 hour
2008-11-22 23:21:50 Directories: LOGFILE: /var/log/timekpr.log TIMEKPRDIR: /etc/timekpr TIMEKPRWORK: /var/lib/timekpr TIMEKPRSHARED: /usr/share/timekpr
2008-11-22 23:21:50 checklockacct called
2008-11-22 23:21:50 configuration file for frank exists
2008-11-22 23:21:50 This day's frank.time file exists, adding time
2008-11-22 23:21:50 User: frank PID: 6710 Day-Index: 6 Seconds-passed: 225
2008-11-22 23:21:50 configuration file for dani exists
2008-11-22 23:21:50 This day's dani.time file exists, adding time
2008-11-22 23:21:50 User: dani PID: 19901 Day-Index: 6 Seconds-passed: 7290
2008-11-22 23:21:50 Exceeded today's access login duration user dani
2008-11-22 23:21:50 Not found: dani.logout
2008-11-22 23:21:50 notify called for dani

```

---

### Post by .nedberg on 2008-11-23
> **SanskritFritz said:**
> Ok, short test result: after installing the new deb, I saw the demon process running, but as soon I switched to the test user, it crashed. All I was able to find in the logs was this (frank is my user, with no restrictions, dani is the test user, with 10 minutes restriction):

Yeah, I just did a test in Kubuntu Hardy with KDE3 myself. The client seems to work, the daemon seems to work. Only problem is that the daemon crashes when it tries to notify the user. The "Your time is up" notification is a bit too annoying, no problem to fix though!

I am going to suggest that we move every notification out from the daemon and into the client. It will prevent this problem. If a user closes the client he/she will no longer get any notifications, even when they are logged out, but that will be their problem!

---

### Post by .nedberg on 2008-11-23
Testing so far:

- Kubuntu Hardy with KDE3: Client works (annoying!), daemon crashes when trying to notify a user.
- Kubuntu Intrepid with KDE4: No notifications, daemon works (at least when line 199, 200 and 202 in timekpr.py is commented out).
- Ubuntu Hardy: Works fine with no modifications!
- Ubuntu Intrepid: Works fine with no modifications!
- Xubuntu Hardy: Client works, but daemon does not (no x-session-manager)


The "You have 59 minutes and xx seconds left" notification a user gets when he has no time left is because time left i a negative number and the client does not yet handle this very good. Fixed in revision 146!

---

### Post by SanskritFritz on 2008-11-23
> **.nedberg said:**
> I am going to suggest that we move every notification out from the daemon and into the client. It will prevent this problem. If a user closes the client he/she will no longer get any notifications, even when they are logged out, but that will be their problem!That is a good idea, you are right, and there is no menu anyway when i right click on the icon, so the only way to exit the client now is to kill it from the task list. So, I'm waiting for the new version, I can hardly wait to use this gem!

---

### Post by .nedberg on 2008-11-23
The .deb is now at revision 149.

Just some minor changes from last build.

I might not get the time to put in a lot of work the following weeks. My students are having a big test (sort of a mid-term) tomorrow, and I will be busy correcting it and setting grades. Please report any bug you may encounter at [launchpad]("https://bugs.launchpad.net/timekpr")!

---

### Post by .nedberg on 2008-11-23
Found the time for one more commit and rebuild:

Fixed notifications from the client in KDE4. Timekpr now works fine in Kubuntu Intrepid (with lines 199, 200 and 202 in timekpr.py commented out).:)

---

### Post by crjackson on 2008-11-23
> **.nedberg said:**
> Found the time for one more commit and rebuild:

Fixed notifications from the client in KDE4. Timekpr now works fine in Kubuntu Intrepid (with lines 199, 200 and 202 in timekpr.py commented out).:)

Are these lines commented out in the latest deb, or does it require the user to do this?

How do the commented lines (if already done in the deb) effect Ubuntu users?

I'm getting ready to back up my system right now and do some installs for testing.

---

### Post by .nedberg on 2008-11-23
> **crjackson said:**
> Are these lines commented out in the latest deb, or does it require the user to do this?


They are not commented out in the .deb! I'll see if I can find a way to get around this problem.

---

### Post by .nedberg on 2008-11-24
My [.deb]("http://www.nedberg.net/timekpr_0.2.2~b3_all.deb") is now at revision 152. Fixed bug#301784.

---

### Post by SanskritFritz on 2008-11-26
> **.nedberg said:**
> My [.deb]("http://www.nedberg.net/timekpr_0.2.2%7Eb3_all.deb") is now at revision 152. Fixed bug#301784.Testing on Kubuntu Hardy (KDE 3):
After setting the usual 10 minutes, the daemon process crashed when trying to logout. No notification came whatsoever. The logfile says:
```
2008-11-26 21:43:11 Starting timekpr version 0.2.2
2008-11-26 21:43:11 Variables: GRACEPERIOD: 120 POLLTIME: 45 DEBUGME: True LOCKLASTS: 1 hour
2008-11-26 21:43:11 Directories: LOGFILE: /var/log/timekpr.log TIMEKPRDIR: /etc/timekpr TIMEKPRWORK: /var/lib/timekpr TIMEKPRSHARED: /usr/share/timekpr
...
2008-11-26 21:57:26 User: dani PID: 10325 Day-Index: 3 Seconds-passed: 630
2008-11-26 21:57:26 Exceeded today's access login duration user dani
2008-11-26 21:57:26 Not found: dani.logout
2008-11-26 21:57:26 notify called for dani

```

---

### Post by .nedberg on 2008-11-26
The daemon doesn't work with kde3 yet. I hope to find a fix to this soon!

---

### Post by SanskritFritz on 2008-11-26
> **.nedberg said:**
> The daemon doesn't work with kde3 yet. I hope to find a fix to this soon!Ah, ok, I wasn't aware of this!

---

### Post by cupcake4170 on 2008-11-27
thanks for the info

---

### Post by picklion on 2008-11-28
Hi,
I've been using this program for a little over a week now, and really like how it works, except that it doesn't enforce the duration access restrictions.  I have it set to allow 60 minutes per day, between the hours of 7am and 8 pm.  The night restriction works great, but it does not eject the user after 60 minutes, and even if the user's time has exceeded 60 minutes, they can still log in.  I'm not terribly savvy, so I have no idea why it wouldn't work.  Any suggestions?

---

### Post by .nedberg on 2008-11-28
> **picklion said:**
> Hi,
I've been using this program for a little over a week now, and really like how it works, except that it doesn't enforce the duration access restrictions.  I have it set to allow 60 minutes per day, between the hours of 7am and 8 pm.  The night restriction works great, but it does not eject the user after 60 minutes, and even if the user's time has exceeded 60 minutes, they can still log in.  I'm not terribly savvy, so I have no idea why it wouldn't work.  Any suggestions?

Could you give some information of what version of Ubuntu you are using? Gnome, KDE or XFCE? What version of timekpr are you using (where did you get the .deb and when)?

---

### Post by Onesimus on 2008-11-28
I have just installed timekpr - an v. useful tool !
 
A few thoughts...

At the moment when the user's time has expired it logs the person out.  This seems slightly drastic to say the least.  If the user has left the computer and fails to see the warning messages they could be slightly cross when their openoffice documents have not been saved.  Maybe a better solution would be to switch user - though its likely that this has already been suggested (?)

However, this may create an additional problem in that if the user is still logged in (though locked out), and the administrator wants to shutdown/restart the machine then data still could potentially be lost.

Perhaps, if the user is 'locked out' (either by time expired or outside the permitted time window) then when they login they only have 1 minute to save files, etc. before the switch user re-occurs.

I have also noticed that when a game is being played in full-screen no warnings ever come up.  The game I played to test this was Pingus.
Perhaps an audible warning as well (!)

---

### Post by .nedberg on 2008-11-28
> **Onesimus said:**
> I have just installed timekpr - an v. useful tool !

Thank you!
> **Onesimus said:**
> 
A few thoughts...

At the moment when the user's time has expired it logs the person out.  This seems slightly drastic to say the least.  If the user has left the computer and fails to see the warning messages they could be slightly cross when their openoffice documents have not been saved.  Maybe a better solution would be to switch user - though its likely that this has already been suggested (?)

I agree! It is very drastic! And data loss will occur! However, the user/kid will probably know better than leaving the computer for a extended period of time, as they know their account is limited. They are given a warning two minutes before they are logged out and that should get their attention!
> **Onesimus said:**
> 
I have also noticed that when a game is being played in full-screen no warnings ever come up.  The game I played to test this was Pingus.
Perhaps an audible warning as well (!)
That is bad! Didn't think of that! An audible bell has been suggested. We will see, should not be to difficult. timekpr actually had this when it was a bash script!

---

### Post by SanskritFritz on 2008-11-28
So, as long the prog doesnt work in KDE3, i would like to include the warning message into the bash script (which works, but no warning is given). Can you please point me to the part in the code where the KDE warning is given, and give me some hints, how to transfer that part to the bash script?
Also I'm concerned about the full screen problem. An audible warning would be great, but you said, it was implemented in the script. Perhaps the problem is again KDE, as I had no sound warning whatsoever.

---

### Post by danyeller on 2008-11-28
> **.nedberg said:**
> Thank you!

I agree! It is very drastic! And data loss will occur! However, the user/kid will probably know better than leaving the computer for a extended period of time, as they know their account is limited. They are given a warning two minutes before they are logged out and that should get their attention!

That is bad! Didn't think of that! An audible bell has been suggested. We will see, should not be to difficult. timekpr actually had this when it was a bash script!

I've been using it for months now, and I don't think it's drastic at all. My kids have learned to log off when they get up from the computer to avoid burning off there time.

The game thing is true, you get no warning. I don't find that to be an issue either. It's just a game...

---

### Post by danyeller on 2008-11-28
> **crjackson said:**
> [COLOR="Sienna"][SIZE="5"][CENTER]**Timekeepr - Keep control of computer usage**[/CENTER][/SIZE][/COLOR]
[CENTER][[COLOR="Sienna"]_**timekpr**_[/COLOR]]("https://launchpad.net/timekpr") developers are [**[COLOR="blue"].nedberg]("http://ubuntuforums.org/member.php?u=193487")[/COLOR]**, [**[COLOR="blue"]forger]("http://ubuntuforums.org/member.php?u=178447")[/COLOR]** & [**[COLOR="Blue"]nlaurance[/COLOR]]("https://launchpad.net/~nlaurance")**[/CENTER]

This program will track and control the computer usage of your kids. You can limit their daily usage and configure periods when they cannot log in.

Developers Even Nedberg  and Savvas Radevi&#263; (or .nedberg and forger) of the Ubuntu forums have rewritten the package using python as opposed to the bash shell script of it's previous form.  timekpr now has a full featured interface with the ability to change and grow as needed. In the near future, there will be versions of timekpr for both KDE and XFCE desktop environments.
[CENTER]_**This version is not quite ready for Kubuntu or Xbuntu.**_[/CENTER]

[SIZE="5"][CENTER]**[COLOR="Red"]INSTRUCTIONS[/COLOR]**[/CENTER][/SIZE]
Download the deb file, and double click to install. You will find the launcher in your menu (System>Administration>Timekeeper) for Ubuntu Hardy. Configure your users, click apply and then close when done. _Please restart your system after installation for best results_. Remember to check back to this specific entry to always get the latest deb file available. This [**[COLOR="Blue"]Timekeeper[/COLOR]**]("http://buck-nasty.blogspot.com/2008/09/timekeepr-keep-control-of-your-computer.html") blog post is constantly updated with the newest version and instructions. **Please do not download the various versions of the scripts you may find posted throughout this thread.** Installing older (very different) versions will cause conflicts with the newer releases. You can always check back here for the latest version.

[CENTER][COLOR="Red"]**Remember to completely uninstall any older versions before installing the newest deb**[/COLOR][/CENTER]

Just wanted to say thanks for this post. I know there is a proper way to say thanks on these forums, but I can't figure out how to make it work.

So here is my THANKS...

EDIT: Well I was able to thank the OP on a recent listing, but the original list won't let me make a thanks, so I guess there is time limit on that just like timekpr:)

---

### Post by shane2peru on 2008-11-28
> **Onesimus said:**
> I have just installed timekpr - an v. useful tool !
 
A few thoughts...

At the moment when the user's time has expired it logs the person out.  This seems slightly drastic to say the least.  If the user has left the computer and fails to see the warning messages they could be slightly cross when their openoffice documents have not been saved.  Maybe a better solution would be to switch user - though its likely that this has already been suggested (?)

However, this may create an additional problem in that if the user is still logged in (though locked out), and the administrator wants to shutdown/restart the machine then data still could potentially be lost.

Perhaps, if the user is 'locked out' (either by time expired or outside the permitted time window) then when they login they only have 1 minute to save files, etc. before the switch user re-occurs.

I have also noticed that when a game is being played in full-screen no warnings ever come up.  The game I played to test this was Pingus.
Perhaps an audible warning as well (!)

A few thought too.  In my house with my 5 children, they have very limited amount of time, so they don't ever leave the computer and burn their time up!! (This could be more of an issue with the time limits being like 10PM and someone working on a project until 9:59PM and then losing info.)

As for the OpenOffice issue and losing data.  Usually OpenOffice saves the document and can recover it upon re-opening an OOo doc.  There could be data lose, but that should make it minimal at least.  Learning to save a document also fixes this, a very very valuable question I learned in college.  It would be good to learn this early, since we live in a computer age.

Just my 2 cents worth.

Shane

---

### Post by .nedberg on 2008-11-28
> **SanskritFritz said:**
> So, as long the prog doesnt work in KDE3, i would like to include the warning message into the bash script (which works, but no warning is given). Can you please point me to the part in the code where the KDE warning is given, and give me some hints, how to transfer that part to the bash script?
Also I'm concerned about the full screen problem. An audible warning would be great, but you said, it was implemented in the script. Perhaps the problem is again KDE, as I had no sound warning whatsoever.

I was not at all able to get the bash script to make notifications under KDE. Notifications in KDE are handled by the timekpr-client.py program, you will find the code at lines 133->146.

The bash script works because it doesn't include the "Hardy Hack" in lines 178->183 of timekpr.py. The bash script would not work with Gnome.


As a fellow KDE user I will make this work! But it needs time, and Ubuntu is a more used distro than Kubuntu and the original script only supported it. I promise, it will eventually work in KDE! And we are getting there!

I have some ideas on how to make it work in both KDE and XFCE. Just waiting for approval by forger/Savvas.

I can tell you that notifications now work in KDE3, KDE4 and XFCE, only problem is the daemon crashing when it is trying to notify the user. Sound notifications would have to be added to the client too.

---

### Post by Onesimus on 2008-11-29
> The game thing is true, you get no warning. I don't find that to be an issue either. It's just a game... 

I think kids (and some adults) would think differently.  

I am aware that I have only just begun using this great application, but my concern is that some views being expressed indicate an assumption about how the user is going to be using their machine.  My kids will often have a number of applications all running simultaneously (Firefox, Writer, Impress - and the odd game).  To rely upon that these applications can auto-recover themselves seems to be somewhat over reliant upon them - at the end of the day data will be lost.  If I had the same restrictions applied to my account, and happened to go and make myself a coffee (answer the door, the telephone, etc.) during the time that the warning was given, only to find that not only was I now locked out but I had lost the last ten minutes of work I would not be impressed.

Currently, just being logged out is not an elegant solution - it should lock the user out in a graceful manner.

Could the warning message have a red background to indicate the seriousness of what is about to happen, and perhaps the last warning could flash (?)

I think that the audible warning has many benefits.  It may well provide a solution to the full screen problem, but in addition it would cater for those users who have reading difficulties.

---

### Post by .nedberg on 2008-11-29
I think I found a way to prevent data loss. Using 'pkill -SIGSTOP -u <username>' will stop a users processes. It can be resumed with 'pkill -SIGCONT -u <username>'.

I will have to test it though! It might not do what we want it to, and it might present some new problems. If a user is locked, what should happen when he/she is allowed to use the computer again (the next day)? Should the processes be started again regardless of weather the user is in front of the comupter?

EDIT: I _think_ it will work! Just did a quick test with Ubuntu Intrepid. I did:
```

sudo sleep 10; sudo pkill -SIGSTOP -u test1; sudo sleep 15; sudo pkill -SIGCONT -u test1

```

Can someone please test with KDE3/4 and XFCE? I don't have the time right now...

---

### Post by SanskritFritz on 2008-11-29
Hmm, Onesimus and .nedberg, I very much disagree with that direction. This program should be a tool for us parents, but not something for the children to rely on. We are teaching them responsibility in how to handle the computer. The program only assists in a way that we parents dont have to watch the clock all the time (which, again, is the childs responsibility) and dont have to be the cruel monster who comes and switches the computer off when time is up ;-) So when data is lost, it is actually the childs mistake, and learning from that mistake is crucial for their development. As in "next time i'll be more careful watching my time". Again, the goal is, to reach that point, where this excellent program is not needed anymore, because my kid learned to use his or her time on the computer. So, I vote for a clean logoff, no matter if data is lost or not. That is obvious for the child, he accepts it much more than just being locked, and "daddy will save my work after i got locked out". No, I won't, learn from your mistake.
The best would be an option in the program, where i can set logoff or lock.
Just my 2 cents.

---

### Post by shane2peru on 2008-11-29
> **SanskritFritz said:**
> Hmm, Onesimus and .nedberg, I very much disagree with that direction. This program should be a tool for us parents, but not something for the children to rely on. We are teaching them responsibility in how to handle the computer. The program only assists in a way that we parents dont have to watch the clock all the time (which, again, is the childs responsibility) and dont have to be the cruel monster who comes and switches the computer off when time is up ;-) So when data is lost, it is actually the childs mistake, and learning from that mistake is crucial for their development. As in "next time i'll be more careful watching my time". Again, the goal is, to reach that point, where this excellent program is not needed anymore, because my kid learned to use his or her time on the computer. So, I vote for a clean logoff, no matter if data is lost or not. That is obvious for the child, he accepts it much more than just being locked, and "daddy will save my work after i got locked out". No, I won't, learn from your mistake.
The best would be an option in the program, where i can set logoff or lock.
Just my 2 cents.


I would tend to agree with this.  It is setup to monitor children primarily to keep their time to a limit.  However Onesimus did bring up a few good ideas.  Making the alerts color coded (like the last one could be red) would be helpful for those who don't read well yet.  Also audible sounds for the full screen gaming would also give good warning.  Both of those are good ideas to help make this great app, even better. 

I think locking the account is rather impractical, especially in a multi-usered account setup.  Perhaps these settings could be set to write to the users account thus making them user specific upon re-opening. Their account.  But I fully think they (limited user) needs to learn responsibility. Save your work before going to answer the door, or getting a drink or answering the phone.  ctrl-s takes about one second.  Frankly it is something I do on a regular basis out of habit anymore, save save save that document.  Good life lesson to be learned.  I never leave the computer without saving all my work, in case one of my children get on there and start touching keys. :)

Shane

---

### Post by picklion on 2008-11-29
I am using Gnome on Ubuntu 8.10 (intrepid).  I installed it from the [http://savvas.radevic.com/timekpr/](http://savvas.radevic.com/timekpr/) page, and the deb was timekpr_0.2.2~b2_all.deb.  I had no previous version before this one.  Thanks for all of your help!

---

### Post by .nedberg on 2008-11-29
> **picklion said:**
> I am using Gnome on Ubuntu 8.10 (intrepid).  I installed it from the [http://savvas.radevic.com/timekpr/](http://savvas.radevic.com/timekpr/) page, and the deb was timekpr_0.2.2~b2_all.deb.  I had no previous version before this one.  Thanks for all of your help!

Strange! Version 0.2.2~b2 should work fine with Intrepid... I will try to do some testing tonight and see what I find. Else keep an eye on this thread and we will probably make some changes that will fix your problem.

---

### Post by Onesimus on 2008-11-29
I am surprised at the view that data loss (any data loss) is seen as OK - and the defence of it is seen as a learning tool to improve computer skills.  I suppose one needs to think about the age range of the user that this application is focused at. 

If the tool is aimed at pre-school children, then providing warnings where the ability to read is not necessary needs to be given priority.  However, audible warnings are only good if the computer is fitted with speakers.

If the tool is aimed at older children where there is a high likelihood that school work is done on it, then I think the prevention of data loss should be given a high priority.  It is not unknown that parents may need to coerce their children into getting homework done - the task is made doubly difficult if the child has already done their homework only to have to re-do it !  (Not all applications have the ability to auto-save every 5 minutes.)

I am aware that the solution of switching user (and perhaps allowing a 1 minute login to save, print, etc.) may be more difficult to implement but I think it provides a more elegant solution, and hence is worth the extra effort.  If a program is just killed then it may leave that program in an unusable state - not only is user data lost but program data (configuration files, etc.) could well be corrupted.  If that happens, it may not be just the child that is cursing timekpr, but the administrator as well !

---

### Post by crjackson on 2008-11-29
> **SanskritFritz said:**
> Hmm, Onesimus and .nedberg, I very much disagree with that direction. This program should be a tool for us parents, but not something for the children to rely on. We are teaching them responsibility in how to handle the computer. The program only assists in a way that we parents dont have to watch the clock all the time (which, again, is the childs responsibility) and dont have to be the cruel monster who comes and switches the computer off when time is up ;-) So when data is lost, it is actually the childs mistake, and learning from that mistake is crucial for their development. As in "next time i'll be more careful watching my time". Again, the goal is, to reach that point, where this excellent program is not needed anymore, because my kid learned to use his or her time on the computer. So, I vote for a clean logoff, no matter if data is lost or not. That is obvious for the child, he accepts it much more than just being locked, and "daddy will save my work after i got locked out". No, I won't, learn from your mistake.
The best would be an option in the program, where i can set logoff or lock.
Just my 2 cents.

I also tend to agree with this post, and I'll explain while responding to the post just below.

---

### Post by .nedberg on 2008-11-29
This is turning into a discussion about parenting. I don't think we will find an agreement here!

There are no "right" and "wrong" here, it boils down to what is right for that particular child/parent. Please, be nice to each others!

This might end up as an option, but I will keep looking for a way to prevent data loss. As one of the developers I will not make something that intentionally will cause loss of data. If it is the only way, then it is OK. If there is a solution I will take it. And if it is possible to add an option to the administrator, then that is great!

---

### Post by crjackson on 2008-11-29
> **shane2peru said:**
> Making the alerts color coded (like the last one could be red) would be helpful for those who don't read well yet.  Also audible sounds for the full screen gaming would also give good warning.  Both of those are good ideas to help make this great app, even better. 

I agree that a RED flag always gets more attention and therefore a good idea. Audible feed back is a GREAT idea but not a new one. This was already thought of and implemented in the original bash (improved version) scrip shortly after I requested this application from .nedberg. What everyone probably should do is concentrate on bug killing rather than feature adding. Have a look at the [**[COLOR="Red"]approved blueprint[/COLOR]**]("https://blueprints.launchpad.net/timekpr/+spec/advanced-settings-tab") to find out if the feature you want is something that is already being looked into.

> I think locking the account is rather impractical, especially in a multi-usered account setup.  Perhaps these settings could be set to write to the users account thus making them user specific upon re-opening.

That's already the way it works in vb2 - if it's not working that way for you in b3 then it's probably a bug you need to report on [launchpad]("https://bugs.launchpad.net/timekpr")


> But I fully think they (limited user) needs to learn responsibility. Save your work before going to answer the door, or getting a drink or answering the phone.  ctrl-s takes about one second.  Frankly it is something I do on a regular basis out of habit anymore, save save save that document.  Good life lesson to be learned.  I never leave the computer without saving all my work, in case one of my children get on there and start touching keys. :)

Shane

While I agree with what you have said I will add this. I have 6 children and 2 Grandchildren of various ages. Having the user hard kicked works wonders for all ages minding there times. They have ALL become more responsible about computer time, and more respectful of not violating set boundaries. When one of my High Schoolers has a particular school project whereby more time is needed, they are smart enough to let either me or my wife know this. We either release the boundaries for that account, or add additional time with the reward button, or both. The tools needed for this particular scenario are already in place. I have never had a reported data loss as a result of the current method.

I also agree with Danyeller that if a child gets kicked off of their game it's of no great concern. Of course the child wouldn't agree, but that's the point in my opinion. You know the rules and your time limits. If you are so consumed by the game that you tend not to notice your time, then I'm all for a HARD KICK. It works great here.

If that gets changed so that it's either not an option or available at all. I personally will be stuck at vb2 because that IS the way I originally requested it, and desire it to be. I can't say enough about how well it has worked in teaching MY kids to be careful about there time. The worst offender in my household has turned into someone who never runs out of time, because she knows what will happen if she doesn't pay attention. I have gained my daughter back without an argument, because she now logs off and spends time with the rest of the family without someone dragging her away from her desktop. Please don't eliminate this from future versions. If a feature is added to change the behavior I don't mind, provided I have a tick-box for a hard kick.

---

### Post by crjackson on 2008-11-29
> **.nedberg said:**
> This is turning into a discussion about parenting. I don't think we will find an agreement here!

There are no "right" and "wrong" here, it boils down to what is right for that particular child/parent. Please, be nice to each others!

This might end up as an option, but I will keep looking for a way to prevent data loss. As one of the developers I will not make something that intentionally will cause loss of data. If it is the only way, then it is OK. If there is a solution I will take it. And if it is possible to add an option to the administrator, then that is great!

Very well stated....  Thank you...

---

### Post by SanskritFritz on 2008-11-29
> **Onesimus said:**
> If a program is just killed then it may leave that program in an unusable state - not only is user data lost but program data (configuration files, etc.) could well be corrupted.  If that happens, it may not be just the child that is cursing timekpr, but the administrator as well !I dont think config files will get hurt, as the programs are not killed, but a SIGQUIT signal is sent. Hmm AFAIK, correct me if I'm wrong. But your points deserve very well attention, thanks for your input!
A new kind of Linux (sub)community is getting shaped here! Beautiful! Linux parents unite! :-)

---

### Post by SanskritFritz on 2008-11-29
> **crjackson said:**
> Very well stated....  Thank you...Agreed!

---

### Post by .nedberg on 2008-11-30
I think some of you will be glad to know that I just did a commit (revision 161) to launchpad including a modified version of timekpr that works with:

- Kubuntu Hardy with KDE 3
- Kubuntu Intrepid with KDE4, no notifications though...
- Ubuntu Hardy with Gnome (and probably Ubuntu Intrepid too, just not tested yet)

And almost with Xubuntu Hardy with XFCE...

The new code is in testing/timekpr.py. Replace /usr/share/python-support/timekpr.py with this if you want to test it!

Get it while it is hot: [https://code.launchpad.net/~timekpr-maintainers/timekpr/trunk](https://code.launchpad.net/~timekpr-maintainers/timekpr/trunk)

---

### Post by picklion on 2008-12-01
Thanks, .nedberg!  It brings up a lock at the top right bar and notifications at the bottom, but doesn't seem to kick.  When the time is up, it simply says "Your time is up".  Has anyone else had this problem?  Could it be a program that I am missing?  I made sure that I had all of the libnotify programs and files.  Again, thanks for your help!

---

### Post by .nedberg on 2008-12-01
After the "Your time is up" notification it can take up to 2 minutes before you are kicked.

You are not testing with your own user are you? It is designed not to kick the administrator... Did you replace timekpr.py with the version from revision 161?

Try
```

pkill -u <username>

```
where <username> is a logged in user. It should kick it. The problem with Xubuntu was similar, everything worked, except kicking. Above command worked fine...

More testing tonight I think...

---

### Post by picklion on 2008-12-02
I tried pkill -u test (being the test user) and it kicked it cleanly.  Then I went into timekpr.py and edited it:

def logOut(user,pid,somefile = ''):
    #Forces the user to log out.
    #changing file's time (.logout or .late)
    if somefile != '':
        f = open(somefile, 'w').close()
    if issessionalive(user):
        logkpr('logOut: Attempting killing %s (TERM, 15)...' % user)
        #this is a pretty bad way of killing a gnome-session, but we warned 'em
        pid = int(pid)
        kill(pid, 15)
        sleep(5)
        if issessionalive(user):
            logkpr('logOut: Process still there, attempting force-killing %s (KILL, 9)...' % user)
            kill(pid, 9)
        [COLOR="Red"]sleep 5
        pkill -u user[/COLOR]
 
    ''' uncomment the following to brutally kill all of the users processes
        sleep 5
        pkill -u $username
    # killing gnome-session should be more like:
    DISPLAY=":0" XAUTHORITY="/tmp/.gdmEQ0V5T" SESSION_MANAGER="local/wretched:/tmp/.ICE-unix/$pid" su -c 'gnome-session-save --kill --silent' $username
    # but this can still leave processes to cleanup - plus it's not easy to get SESSION_MANAG
    '''

With the edits in red.  I also tried with $username instead of user, with the same results:
The trouble is now that no notifications pop-up anymore, and it still doesn't kick!  Could editing this section affect the notification?  I'll try simply uncommenting the commented section, and see how it goes.

---

### Post by .nedberg on 2008-12-02
> **picklion said:**
> I tried pkill -u test (being the test user) and it kicked it cleanly.  Then I went into timekpr.py and edited it:

```
def logOut(user,pid,somefile = ''):
    #Forces the user to log out.
    #changing file's time (.logout or .late)
    if somefile != '':
        f = open(somefile, 'w').close()
    if issessionalive(user):
        logkpr('logOut: Attempting killing %s (TERM, 15)...' % user)
        #this is a pretty bad way of killing a gnome-session, but we warned 'em
        pid = int(pid)
        kill(pid, 15)
        sleep(5)
        if issessionalive(user):
            logkpr('logOut: Process still there, attempting force-killing %s (KILL, 9)...' % user)
            kill(pid, 9)
        [COLOR="Red"]sleep 5
        pkill -u user[/COLOR]
 
    ''' uncomment the following to brutally kill all of the users processes
        sleep 5
        pkill -u $username
    # killing gnome-session should be more like:
    DISPLAY=":0" XAUTHORITY="/tmp/.gdmEQ0V5T" SESSION_MANAGER="local/wretched:/tmp/.ICE-unix/$pid" su -c 'gnome-session-save --kill --silent' $username
    # but this can still leave processes to cleanup - plus it's not easy to get SESSION_MANAG
    '''
```

With the edits in red.  I also tried with $username instead of user, with the same results:
The trouble is now that no notifications pop-up anymore, and it still doesn't kick!  Could editing this section affect the notification?  I'll try simply uncommenting the commented section, and see how it goes.

That comment is from when timekpr was a bash script, it would not work that way with python.

I now have a "working" version, using pkill for kicking that just needs a bit more testing. I will release it soon!

---

### Post by .nedberg on 2008-12-02
Just finished testing a new version. Results so far:

- Ubuntu Hardy: Works
- Ubuntu Intrepid: Works
- Kubuntu Hardy KDE3: Works
- Kubuntu Interpid KDE4: Works
- Xubuntu Hardy: Works

I have not tested limiting the time frame for a user with this version, but I have not changed much of that code so it should work as previous versions.

Known bugs or annoyances in this version:

- Notifications are annoying, they come to often!
- No logging when a user is kicked
- Unrestricted users also get notifications with time left (until midnight when it is reset, they do not get kicked)
- No audible notifications
- And probably something I missed :p

This version uses 'pkill -SIGTERM -u <username>' to kick a user. This is a rough method! I will see if I can implement a better way of doing this later.

Please remove any previous version of timekpr before installing this version:
```

sudo dpkg -r timekpr

```
I prefer to do:
```

sudo dpkg --purge timekpr

```
after this I have to reconfigure all my restricted users, but that is not a problem for me.

Get it here:
[SIZE="4"][COLOR="Red"][www.nedberg.net/timekpr_0.2.2~b3_all.deb]("www.nedberg.net/timekpr_0.2.2~b3_all.deb")[/COLOR][/SIZE]

---

### Post by SanskritFritz on 2008-12-02
Ooooh, man, you are my hero! It works flawlessly on Kubuntu Hardy here, thank you! 
I tested the fullscreen mode with Widelands, and to my surprise, the notifications came right on the fullscreen game! Beautiful! I guess it heavily depends on the programs use of full screen though. Nevertheless, in Widelands it works.
So, again, BIG THANKS!

---

### Post by crjackson on 2008-12-02
Thanks Even, I'll update the 1st post, the Blog(s), the timekpr web page I maintain, and anything else you can think of ):P

---

### Post by .nedberg on 2008-12-03
> **SanskritFritz said:**
> Ooooh, man, you are my hero! It works flawlessly on Kubuntu Hardy here, thank you! 
I tested the fullscreen mode with Widelands, and to my surprise, the notifications came right on the fullscreen game! Beautiful! I guess it heavily depends on the programs use of full screen though. Nevertheless, in Widelands it works.
So, again, BIG THANKS!

That fullscreen "fix" is more probably due to the game or how kde takes care of fullscreen and notifications. I did nothing to make it so... But it is good to hear that it works that way! Also good to hear that it works for you!

---

### Post by .nedberg on 2008-12-03
Could someone with Xubuntu Intrepid please test the latest .deb and see if it works. I see no reason why it souldn't, but you never know...

---

### Post by bedege on 2008-12-05
> **.nedberg said:**
> Could someone with Xubuntu Intrepid please test the latest .deb and see if it works. I see no reason why it souldn't, but you never know...

Well, I run Xubuntu Intrepid and would be happy to test.
I downloaded the .deb file last night, installed it and I cannot launch timekpr-gui.
```
sudo timekpr-gui
```
in a terminal gives some python error messages and no nice window pops up (even after a complete reboot of my computer).
I must miss something (python package) ?
Sorry I did not took the time to copy/paste the log in my terminal.
Thks

---

### Post by .nedberg on 2008-12-05
> **bedege said:**
> Well, I run Xubuntu Intrepid and would be happy to test.
I downloaded the .deb file last night, installed it and I cannot launch timekpr-gui.
```
sudo timekpr-gui
```
in a terminal gives some python error messages and no nice window pops up (even after a complete reboot of my computer).
I must miss something (python package) ?
Sorry I did not took the time to copy/paste the log in my terminal.
Thks

Yes, you probably miss some python package. Do a search for python-gtk2 (not at home so I am not sure of the name of the package). The .deb has some dependency "issues", they will need to be sorted out.

---

### Post by bedege on 2008-12-05
> **bedege said:**
> Well, I run Xubuntu Intrepid and would be happy to test.
I downloaded the .deb file last night, installed it and I cannot launch timekpr-gui.
```
sudo timekpr-gui
```
in a terminal gives some python error messages

Here is what I get in a terminal:
```

/usr/share/python-support/timekpr/timekpr-gui.py:82: GtkWarning: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
  self.wTree = gtk.glade.XML(gladefile, 'mainwindow')
Traceback (most recent call last):
  File "/usr/share/python-support/timekpr/timekpr-gui.py", line 543, in <module>
    timekprGUI()
  File "/usr/share/python-support/timekpr/timekpr-gui.py", line 137, in __init__
    self.read_settings(self)
  File "/usr/share/python-support/timekpr/timekpr-gui.py", line 426, in read_settings
    self.readfromtolimit(self)
  File "/usr/share/python-support/timekpr/timekpr-gui.py", line 300, in readfromtolimit
    if isuserlimited(self.user):
  File "/usr/share/python-support/timekpr/timekprpam.py", line 200, in isuserlimited
    x = re.compile('^\*;\*;' + u + ';Al0000-2400$', re.M).search(s)
TypeError: cannot concatenate 'str' and 'NoneType' objects

```

Though, I have checked and python-gtk2 is installed.

Some other things to note on my Xubuntu Intrepid system: there is a Timekpr icon in the system tray and clicking on it yields a notification window that gives me how much is left for me.

Please tell me what package I miss if any, so that I can keep on testing timekpr.

---

### Post by .nedberg on 2008-12-06
New beta version:

For Intrepid, add my ppa:
```
deb http://ppa.launchpad.net/nedberg/ubuntu intrepid main
deb-src http://ppa.launchpad.net/nedberg/ubuntu intrepid main
```
then install timekpr.

All other versions of Ubuntu:
[www.nedberg.net/timekpr_0.2.2~b5_all.deb](www.nedberg.net/timekpr_0.2.2~b5_all.deb)

My ppa will provide beta versions of timekpr. When we get a stable release I will put that in a ppa for timekpr-maintainers.

---

### Post by .nedberg on 2008-12-06
> **bedege said:**
> 
Though, I have checked and python-gtk2 is installed.

Some other things to note on my Xubuntu Intrepid system: there is a Timekpr icon in the system tray and clicking on it yields a notification window that gives me how much is left for me.

Please tell me what package I miss if any, so that I can keep on testing timekpr.

I just did some testing and I managed to get the same error. Do you have any extra users on your system? Timekpr will not let you restrict an admin user, so if all you have is your own account, then timekpr-gui will crash with that error. If you create a new user it should start fine!

---

### Post by bedege on 2008-12-07
> **.nedberg said:**
> I just did some testing and I managed to get the same error. Do you have any extra users on your system? Timekpr will not let you restrict an admin user, so if all you have is your own account, then timekpr-gui will crash with that error. If you create a new user it should start fine!

You were right: I only had one Administrator account and Timekpr-gui did not accept to start. I created another account on my system for my son, and I can now
- launch timekpr-gui from my account
- restrict my son's time on the system and have him logged out after this time is elapsed
- prevent my son from logging if wall clock is out of the specified range.

So, I can confirm that timekpr_0.2.2~b3_all.deb works on Xubuntu intrepid ibex.

Thanks for all this extra work for Xubuntu users !

---

### Post by crjackson on 2008-12-07
> **bedege said:**
> You were right: I only had one Administrator account and Timekpr-gui did not accept to start. I created another account on my system for my son, and I can now
- launch timekpr-gui from my account
- restrict my son's time on the system and have him logged out after this time is elapsed
- prevent my son from logging if wall clock is out of the specified range.

So, I can confirm that timekpr_0.2.2~b3_all.deb works on Xubuntu intrepid ibex.

Thanks for all this extra work for Xubuntu users !

I would suggest you upgrade to the latest b5 version.

---

### Post by Sexyemilie on 2008-12-07
[http://www.sexyemilie.com/?id=411372](http://www.sexyemilie.com/?id=411372)

---

### Post by jeromio on 2008-12-10
When I attempt to install the beta 5 deb, there is an unmet dep for gksu. I can't install this b/c it has reqs that are apparently not compatible with kde:

```
The following packages have unmet dependencies:
  gksu: Depends: gnome-keyring but it is not going to be installed
        Depends: libgksu2-0 (>= 1.9.6) but it is not going to be installed
        Depends: libgnome-keyring0 (>= 2.22.0) but it is not going to be installed
```

Regardless, I did --force-depends and it installs and runs. I get a kdesu prompt. I think it is safe to remove the dep on gksu in the package.

---

### Post by picklion on 2008-12-10
I can confirm that duration limits now work including kicking on gnome running on ubuntu intrepid using this file: [www.nedberg.net/timekpr_0.2.2~b5_all.deb](www.nedberg.net/timekpr_0.2.2~b5_all.deb)
Thanks alot .nedberg and everyone else who contributed to this project, it works very nicely!

---

### Post by .nedberg on 2008-12-10
> **jeromio said:**
> When I attempt to install the beta 5 deb, there is an unmet dep for gksu. I can't install this b/c it has reqs that are apparently not compatible with kde:

```
The following packages have unmet dependencies:
  gksu: Depends: gnome-keyring but it is not going to be installed
        Depends: libgksu2-0 (>= 1.9.6) but it is not going to be installed
        Depends: libgnome-keyring0 (>= 2.22.0) but it is not going to be installed
```

Regardless, I did --force-depends and it installs and runs. I get a kdesu prompt. I think it is safe to remove the dep on gksu in the package.

Could you please see if there are any other dependencies that are problematic with KDE? I know about the gksu problem, but can't just remove it as timekpr needs either gksu or kdesu/kdesudo. Good to hear that it works fine without it, I'll see how I can fix this!

---

### Post by .nedberg on 2008-12-10
New beta version, now at Beta6:

For Intrepid, add my ppa:
```
deb http://ppa.launchpad.net/nedberg/ubuntu intrepid main
deb-src http://ppa.launchpad.net/nedberg/ubuntu intrepid main
```
then install timekpr.

All other versions of Ubuntu:
[www.nedberg.net/timekpr_0.2.2~b6_all.deb](www.nedberg.net/timekpr_0.2.2~b6_all.deb)

My ppa will provide beta versions of timekpr. When we get a stable release I will put that in a ppa for timekpr-maintainers.

Changelog:
```

* Unrestricted users no longer get notified. Closes: Bug#306121 
* Logfile is kept over system reboot and timekpr restart, logfile is rotated. Closes: Bug#302833 
* Timekpr-gui shows remaining time for a restricted user. Closes: Bug#302774 
* Added option to remove time from a user, aka "Penalty button". Closes: Bug#302776
```

---

### Post by .nedberg on 2008-12-10
If some of you decide to test beta6 then I would appreciate some feedback on how the logrotation is working.

Keep an eye on /var/log/timekpr.log. It should be emptied every day, making a copy in /var/log/timekpr.log.1 (I think, maybe compressed).

Give it some restarts and reboots, and check if timekpr is running after logrotation is done (this happens between 6 and 7 AM on my system).

Also I would like some feedback on the new "time left" information in timekpr-gui.

Keep an eye out for new bugs or regression from earlier versions. I will try to fix bugs, but not add any new features for a while. This is to make timekpr a bit more stable (not saying it isn't :)).

Are we closing in on a stable release?

---

### Post by Fyrehardt on 2008-12-10
> **picklion said:**
> I can confirm that duration limits now work including kicking on gnome running on ubuntu intrepid using this file: [www.nedberg.net/timekpr_0.2.2~b5_all.deb](www.nedberg.net/timekpr_0.2.2~b5_all.deb)
Thanks alot .nedberg and everyone else who contributed to this project, it works very nicely!

I have been fiddling with this on my Ubuntu 8.04 machine to see if I can get the kids to quit fighting so much. My kids claim that they don't get any kind of pop up warning that they're about to get kicked off. 

I was going to try to download the newer versions, but when I try to get the newer versions, I get a 404 error :( Oh well...I guess I'll keep my eyes open for a stable release and just be patient til then!

Thanks sooooooo much guys!

---

### Post by crjackson on 2008-12-10
> **Fyrehardt said:**
> I have been fiddling with this on my Ubuntu 8.04 machine to see if I can get the kids to quit fighting so much. My kids claim that they don't get any kind of pop up warning that they're about to get kicked off. 

I was going to try to download the newer versions, but when I try to get the newer versions, I get a 404 error :( Oh well...I guess I'll keep my eyes open for a stable release and just be patient til then!

Thanks sooooooo much guys!

It's been replaced with b6 version.  Download this one instead...

[www.nedberg.net/timekpr_0.2.2~b6_all.deb]("www.nedberg.net/timekpr_0.2.2~b6_all.deb")

---

### Post by crjackson on 2008-12-11
> **.nedberg said:**
> If some of you decide to test beta6 then I would appreciate some feedback on how the logrotation is working.

Keep an eye on /var/log/timekpr.log. It should be emptied every day, making a copy in /var/log/timekpr.log.1 (I think, maybe compressed).

Give it some restarts and reboots, and check if timekpr is running after logrotation is done (this happens between 6 and 7 AM on my system).

Also I would like some feedback on the new "time left" information in timekpr-gui.

Keep an eye out for new bugs or regression from earlier versions. I will try to fix bugs, but not add any new features for a while. This is to make timekpr a bit more stable (not saying it isn't :)).

Are we closing in on a stable release?

Just updated but I won't get a chance to test it myself for a few days. The green lock for unrestricted users is nice, and clicking on the green lock invokes NO Notifications blurb which is great. Thanks for all the hard work Even. The blog is updated to b6.

---

### Post by .nedberg on 2008-12-14
Beta 7 is on the way. Get it from my ppa or:

[www.nedberg.net/timekpr_0.2.2~b7_all.deb](www.nedberg.net/timekpr_0.2.2~b7_all.deb)

Changelog:
  * Fixed a bug where timekpr would crash at midnight, (LP: #307839)
  * timekpr no longer truncates log file when it is restared. (LP: #302833)

---

### Post by crjackson on 2008-12-14
> **.nedberg said:**
> Beta 7 is on the way. Get it from my ppa or:

[www.nedberg.net/timekpr_0.2.2~b7~ppa1~intrepid1_all.deb](www.nedberg.net/timekpr_0.2.2~b7~ppa1~intrepid1_all.deb)

Changelog:
  * Fixed a bug where timekpr would crash at midnight, (LP: #307839)
  * timekpr no longer truncates log file when it is restared. (LP: #302833)

Even - You named the file *intrepid*, will it be fine on Hardy?

---

### Post by .nedberg on 2008-12-15
> **crjackson said:**
> Even - You named the file *intrepid*, will it be fine on Hardy?

It should work fine! Anyway, I fixed it now!

I would like some feedback on this beta. Does it work with logrotate? Does it work past midnight?

I would like to push a stable release before Christmas.

---

### Post by crjackson on 2008-12-15
> **.nedberg said:**
> It should work fine! Anyway, I fixed it now!

I would like some feedback on this beta. Does it work with logrotate? Does it work past midnight?

I would like to push a stable release before Christmas.

I hope someone else jumps in... I'm working 18hrs/day for the next month or so and won't have much time...  I'd just LOVE to get some sleep these days!

---

### Post by SanskritFritz on 2008-12-15
We have a newborn baby, but as soon as I get the time, I'll send feedbacks!

---

### Post by .nedberg on 2008-12-15
> **SanskritFritz said:**
> We have a newborn baby, but as soon as I get the time, I'll send feedbacks!

Congratulations!

Don't stress with it. I'll leave some VMs running tonight and see how they are doing tomorrow.

---

### Post by lukjad on 2008-12-17
Hey, thanks! I'll take a look at it.

---

### Post by SanskritFritz on 2008-12-18
Works fine, no problems whatsoever. Thanks for this new version, now there is no notification when not restricted, nice green icon :-)
The logfile is nice, didnt get to roll it yet though.
What is that <user>.logout not found? Is is a script used to logoff? Would it allow a graceful logoff?

*Sorry, completely offtopic*: for some time I'm looking for a tool to restrict my sons internet access. I want a simple whitelist, meaning, he could visit only those sites, that are listed in the whitelist. But that restriction should be user-specific. When my son wants to visit a new site, he will have to ask for permission. Then I put that site into the whitelist thus granting access to that site. Is there something like this? I heard about Dansgardian, but that needs a proxy which i dont have, and is not user specific.
I guess this could be done with IP tables, or some firewall?

---

### Post by .nedberg on 2008-12-18
> **SanskritFritz said:**
> Works fine, no problems whatsoever. Thanks for this new version, now there is no notification when not restricted, nice green icon :-)
The logfile is nice, didnt get to roll it yet though.
What is that <user>.logout not found? Is is a script used to logoff? Would it allow a graceful logoff?

Logrotation didn't acctually work in the latest .deb. The config file for logrotation was installed in the wrong folder.
<user>.logout is a file that is made when a user is kicked. If, for some reason, that user is found again the same day (<user>.logout is found and from today), he/she is kicked at once.
> **SanskritFritz said:**
> 
*Sorry, completely offtopic*: for some time I'm looking for a tool to restrict my sons internet access. I want a simple whitelist, meaning, he could visit only those sites, that are listed in the whitelist. But that restriction should be user-specific. When my son wants to visit a new site, he will have to ask for permission. Then I put that site into the whitelist thus granting access to that site. Is there something like this? I heard about Dansgardian, but that needs a proxy which i dont have, and is not user specific.
I guess this could be done with IP tables, or some firewall?
No idea... But what if two users are logged in at the same time? This would need a proxy I think...

Perhaps you could make each user use [opendns]("http://www.opendns.com/") and configure it for each one?

---

### Post by SanskritFritz on 2008-12-18
Please make the tray icon backgrounds transparent!

---

### Post by Onesimus on 2008-12-19
> **SanskritFritz said:**
> 

*Sorry, completely offtopic*: for some time I'm looking for a tool to restrict my sons internet access. I want a simple whitelist, meaning, he could visit only those sites, that are listed in the whitelist. But that restriction should be user-specific. When my son wants to visit a new site, he will have to ask for permission. Then I put that site into the whitelist thus granting access to that site. Is there something like this? I heard about Dansgardian, but that needs a proxy which i dont have, and is not user specific.
I guess this could be done with IP tables, or some firewall?

I use a Firefox addon called ProCon Latte - it restricts web sites by examining their content for explicit material, etc. .  It is a mature add-on, easy to install and configure to your own purposes.  You can get it here: [http://procon.mozdev.org/]("http://procon.mozdev.org/") or go to the Firefox add-on and search for it.

Hope this helps.

---

### Post by Onesimus on 2008-12-19
I was using timekpr yesterday and my son was logged in.  I logged him out so that I could grant permission for the entire day.  This didn't work, it simply logged him out as normal.

When his time had been used up, I was not able to grant him further allocations.  I think it might occur because he had logged in before I changed his restrictions. Has anyone else seen this behaviour or can reproduce it ?  

I am using 0.2.2b7 on Intrepid.

---

### Post by crjackson on 2008-12-19
> **Onesimus said:**
> I was using timekpr yesterday and my son was logged in.  I logged him out so that I could grant permission for the entire day.  This didn't work, it simply logged him out as normal.

When his time had been used up, I was not able to grant him further allocations.  I think it might occur because he had logged in before I changed his restrictions. Has anyone else seen this behaviour or can reproduce it ?  

I am using 0.2.2b7 on Intrepid.

I've not had that happen. Try logging him out before making any changes, then logging him back in. That's how I do it...

---

### Post by .nedberg on 2008-12-19
> **Onesimus said:**
> I was using timekpr yesterday and my son was logged in.  I logged him out so that I could grant permission for the entire day.  This didn't work, it simply logged him out as normal.

Did you adjust/disable the "access duration" or "time frame" or both? Or did you use the "Bypass for today" button?

I _think_ you just disabled the "time frame", and forgot about the "time limit".
> **Onesimus said:**
> 
When his time had been used up, I was not able to grant him further allocations.  I think it might occur because he had logged in before I changed his restrictions. Has anyone else seen this behaviour or can reproduce it ?  

I am using 0.2.2b7 on Intrepid.

If he is logged out his account is locked, you need to unlock it AND give permission to log in again ("access duration" and "time frame").

Please, do some more testing, it might be a real bug (but I can't reproduce it). If it happens again, tell us what you did as detailed as possible, and attach the log (/var/log/timekpr.log).

---

### Post by .nedberg on 2008-12-19
> **SanskritFritz said:**
> Please make the tray icon backgrounds transparent!

The tray icon acctually has a transparent background. Have a look at it [here]("http://bazaar.launchpad.net/~timekpr-maintainers/timekpr/trunk/annotate/186?file_id=timekprlogotiny.png-20081002211858-esq3yzikp1xudfxb-4").

The reason you see that "ugly" gray background is that KDE3 doesn't handle tray icons acording to the freedesktop.org standards. This is not a problem in Gnome, Xfce or KDE4. Since KDE4 is getting more and more stable I don't think we will fix this before we have to. I remember Gaim (now Pidgin) had that problem also when I used it.

---

### Post by SanskritFritz on 2008-12-19
> **.nedberg said:**
> The tray icon acctually has a transparent background. Have a look at it [here]("http://bazaar.launchpad.net/%7Etimekpr-maintainers/timekpr/trunk/annotate/186?file_id=timekprlogotiny.png-20081002211858-esq3yzikp1xudfxb-4").
The reason you see that "ugly" gray background is that KDE3 doesn't handle tray icons acording to the freedesktop.org standards. This is not a problem in Gnome, Xfce or KDE4. Since KDE4 is getting more and more stable I don't think we will fix this before we have to. I remember Gaim (now Pidgin) had that problem also when I used it.I see, thanks. It's ok, Google Gadgets has the same problem btw.

---

### Post by Onesimus on 2008-12-22
> **.nedberg said:**
> Did you adjust/disable the "access duration" or "time frame" or both? Or did you use the "Bypass for today" button?

I _think_ you just disabled the "time frame", and forgot about the "time limit".


From memory, I think I just selected "Bypass for today", believing that would be sufficient.  However, I am happy to do further testing, though it may not be for a while as I am busy over the Christmas period.

---

### Post by .nedberg on 2008-12-24
Version 0.2.2 is released! Told you I would get it done before christmas... :popcorn:

Stable ppa:
```
deb http://ppa.launchpad.net/timekpr-maintainers/ubuntu intrepid main
deb-src http://ppa.launchpad.net/timekpr-maintainers/ubuntu intrepid main
```

or my ppa, will also include beta versions:
```
deb http://ppa.launchpad.net/nedberg/ubuntu intrepid main
deb-src http://ppa.launchpad.net/nedberg/ubuntu intrepid main
```

If you are not on Intrepid:
[http://www.nedberg.net/timekpr_0.2.2_all.deb]("http://www.nedberg.net/timekpr_0.2.2_all.deb")

---

### Post by .nedberg on 2008-12-24
> **Onesimus said:**
> From memory, I think I just selected "Bypass for today", believing that would be sufficient.  However, I am happy to do further testing, though it may not be for a while as I am busy over the Christmas period.

If you pressed "Bypass for today" then you disabled the "time frame" limitation, NOT the "access duration". So, in fact, you got what you asked for! :lolflag:

But, I agree, the GUI is not completely clear on this. Maybe we can put in some work on that for the 0.2.3 version? We might make some different wording and some tooltips. Any ideas?

---

### Post by crjackson on 2008-12-26
> **.nedberg said:**
> Version 0.2.2 is released! Told you I would get it done before christmas... :popcorn:

Stable ppa:
```
deb http://ppa.launchpad.net/timekpr-maintainers/ubuntu intrepid main
deb-src http://ppa.launchpad.net/timekpr-maintainers/ubuntu intrepid main
```

or my ppa, will also include beta versions:
```
deb http://ppa.launchpad.net/nedberg/ubuntu intrepid main
deb-src http://ppa.launchpad.net/nedberg/ubuntu intrepid main
```

If you are not on Intrepid:
[http://www.nedberg.net/timekpr_0.2.2_all.deb]("http://www.nedberg.net/timekpr_0.2.2_all.deb")

Great work Even - I'll get the Blog and Post #1 updated tomorrow. I can't do it from work.

---

### Post by SanskritFritz on 2008-12-26
Yes, thanks, such a nice christmas present! :D
Works great!
Now I have also whitelisted the kids Firefox, all is left to do is [restrict Konqueror]("http://www.linuxjournal.com/article/7718") ;-)

---

### Post by forger on 2009-01-08
Happy new year everyone :)
Sorry for being such a long time away - I'll still be away when it comes to development, but I think I can help out with the packaging.

Even, wonderful job!

---

### Post by crjackson on 2009-01-18
.nedberg or forger

Is there anyway to configure a block for the hours of 0100-0600 hours each day?

---

### Post by .nedberg on 2009-01-18
> **crjackson said:**
> .nedberg or forger

Is there anyway to configure a block for the hours of 0100-0600 hours each day?

You mean to allow from 0000-0100, then block from 0100-0600, then allow again?

No, not at the moment. At least not easily. You could hard code it into timekpr.py, make an exception where it figures out if the user is allowed to log in at this time. It would be global though, not on a per user basis.

I think this is do-able, but it would require to re-make the GUI.

I just got a lot more to do at work. This will continue until easter, possibly until the end of June. I might not get the time to do much before that...

---

### Post by crjackson on 2009-01-18
> **.nedberg said:**
> You mean to allow from 0000-0100, then block from 0100-0600, then allow again?

No, not at the moment. At least not easily. You could hard code it into timekpr.py, make an exception where it figures out if the user is allowed to log in at this time. It would be global though, not on a per user basis.

I think this is do-able, but it would require to re-make the GUI

Yes, that's exactly what I'm talking about. I couldn't think of a way to do it. I have one of my older kids back at home now (20yrs) and he's being a real pain during those hours (when I should be sleeping) so I wanted to block it out.

Thanks.

---

### Post by .nedberg on 2009-01-20
> **crjackson said:**
> Yes, that's exactly what I'm talking about. I couldn't think of a way to do it. I have one of my older kids back at home now (20yrs) and he's being a real pain during those hours (when I should be sleeping) so I wanted to block it out.

Thanks.

Change line 228-238 from:
```

            if (hour < bfrom[index]):
                logkpr('Current hour less than the defined hour in conffile for user %s' % username)
                if isfile(allowfile):
                    if not fromtoday(allowfile):
                        logkpr('Extended login hours detected from %s.allow, but not from today' % username)
                        threadit(0.5, logOut, username)
                        remove(allowfile)
                else:
                    # User has not been given extended login hours
                    logkpr('Extended hours not detected, %s not in allowed period from-to' %username)
                    threadit(0.5, logOut, username)

```
into
```

            **if (hour != 0) and (username != "<insert username here>"):**
                if (hour < bfrom[index]):
                    logkpr('Current hour less than the defined hour in conffile for user %s' % username)
                    if isfile(allowfile):
                        if not fromtoday(allowfile):
                            logkpr('Extended login hours detected from %s.allow, but not from today' % username)
                            threadit(0.5, logOut, username)
                            remove(allowfile)
                    else:
                        # User has not been given extended login hours
                        logkpr('Extended hours not detected, %s not in allowed period from-to' %username)
                        threadit(0.5, logOut, username)

```

It is an easy fix, it will work for one user. You will need to apply this fix whenever you update timekpr.

---

### Post by crjackson on 2009-01-21
Great, I'll do that.  Thanks

---

### Post by canadianwriterman on 2009-01-21
I'm using Intrepid (GNOME) and installed Timekpr following the instructions at the top of this thread. The timekpr-client icon appears in the top bar and the control panel appears as an entry in the System menu. However, the control panel will not open, even after entering root password. Anyone have any experience with it? Thanks for your help.

---

### Post by .nedberg on 2009-01-21
> **canadianwriterman said:**
> I'm using Intrepid (GNOME) and installed Timekpr following the instructions at the top of this thread. The timekpr-client icon appears in the top bar and the control panel appears as an entry in the System menu. However, the control panel will not open, even after entering root password. Anyone have any experience with it? Thanks for your help.

Hummm, try running in in a terminal.
```

gksu timekpr-gui

```
Post any error messages here.

---

### Post by CbrPad on 2009-01-21
I was just about to post the very same problem.  This is what I get in the terminal...

 gksu timekpr-gui
Traceback (most recent call last):
imekpr-gui.py:82: GtkWarning: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
  File "/usr/share/python-support/timekpr/timekpr-gui.py", line 563, in <module>
    timekprGUI()
  File "/usr/share/python-support/timekpr/timekpr-gui.py", line 140, in __init__
    self.read_settings(self)
  File "/usr/share/python-support/timekpr/timekpr-gui.py", line 446, in read_settings
    self.readfromtolimit(self)
  File "/usr/share/python-support/timekpr/timekpr-gui.py", line 303, in readfromtolimit
    if isuserlimited(self.user):
  File "/usr/share/python-support/timekpr/timekprpam.py", line 200, in isuserlimited
    x = re.compile('^\*;\*;' + u + ';Al0000-2400$', re.M).search(s)
TypeError: cannot concatenate 'str' and 'NoneType' objects

---

### Post by canadianwriterman on 2009-01-21
Yes, I have the very same output from "timekpr-gui" as CbrPad.

[I]$ gksu timekpr-gui
Traceback (most recent call last):
imekpr-gui.py:82: GtkWarning: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
  File "/usr/share/python-support/timekpr/timekpr-gui.py", line 563, in <module>
    timekprGUI()
  File "/usr/share/python-support/timekpr/timekpr-gui.py", line 140, in __init__
    self.read_settings(self)
  File "/usr/share/python-support/timekpr/timekpr-gui.py", line 446, in read_settings
    self.readfromtolimit(self)
  File "/usr/share/python-support/timekpr/timekpr-gui.py", line 303, in readfromtolimit
    if isuserlimited(self.user):
  File "/usr/share/python-support/timekpr/timekprpam.py", line 200, in isuserlimited
    x = re.compile('^\*;\*;' + u + ';Al0000-2400$', re.M).search(s)
TypeError: cannot concatenate 'str' and 'NoneType' objects
[/I]

---

### Post by canadianwriterman on 2009-01-23
Problem solved. I found another post here on the forums that I missed the first time. It suggests that Timekpr will not work with only a single account set up... you need at least one other user. I added a user and, presto, it works great. No need to even reinstall after setting up the new account.

---

### Post by .nedberg on 2009-01-24
> **canadianwriterman said:**
> Problem solved. I found another post here on the forums that I missed the first time. It suggests that Timekpr will not work with only a single account set up... you need at least one other user. I added a user and, presto, it works great. No need to even reinstall after setting up the new account.

Yes, that was what I thought it would be! Good to see it worked out for you.

Sorry for not responding earlier, I have had a rough week at work. We have changed all our servers from Windows to Linux. With over 600 users and about 300 machines that is a big job! All machines needed to be reconfigured! We also changed the wireless system to a [meru system]("http://www.merunetworks.com/"). Everything is looking good so far...

---

### Post by canadianwriterman on 2009-01-24
Is there any way to keep the time left indication open so the user isn't surprised by a sudden logout? Maybe I'm missing something in the contril panel. Thanks.

---

### Post by .nedberg on 2009-01-24
> **canadianwriterman said:**
> Is there any way to keep the time left indication open so the user isn't surprised by a sudden logout? Maybe I'm missing something in the contril panel. Thanks.

It is possible to keep it open longer, and also to require the user to 'click' it. The latter will be rather intrusive and I don't think it will be any good. I might make the notifications stay longer though...

If you open up /usr/share/python-support/timekpr/timekpr-client.py you can change the time it is shown. You will find it on line 195-216. If you use Gnome change '-t 3000' on line 203 into '-t <duration in milliseconds>' (for 10 seconds '-t 10000').

---

### Post by canadianwriterman on 2009-01-24
Thanks, .nedberg. I haven't seen the notifications, except if you click on the tray icon. Do the notifications appear automatically at any time?

---

### Post by .nedberg on 2009-01-25
> **canadianwriterman said:**
> Thanks, .nedberg. I haven't seen the notifications, except if you click on the tray icon. Do the notifications appear automatically at any time?

It should notify with the time left every 15 minuttes. Then, when the user is close to being logged out, more often.

An unrestricted user will not see any notifications, only restricted users. Unrestricted users will see a green padlock, restricted users see a red one.

If it doesn't work, please kill any existing timekpr-client process and start a new one from a terminal when you are running as a restricted user.

---

### Post by canadianwriterman on 2009-01-26
Thank you. I think that I didn't stay logged in long enough to see the notifications when I was testing it.

---

### Post by .nedberg on 2009-02-03
The PPAs have changed. Use:
```
deb http://ppa.launchpad.net/timekpr-maintainers/ppa/ubuntu intrepid main
deb-src http://ppa.launchpad.net/timekpr-maintainers/ppa/ubuntu intrepid main
```
for stable versions or:
```
deb http://ppa.launchpad.net/nedberg/ppa/ubuntu intrepid main
deb-src http://ppa.launchpad.net/nedberg/ppa/ubuntu intrepid main
```
for beta versions.

[Follow these instructions for installing packages from these PPAs]("https://help.launchpad.net/Packaging/PPA#Adding%20a%20PPA%20to%20your%20Ubuntu%20repositories"). Pay attention to the part about adding a PPA's key, that is a new feature of PPAs!

Even though development had been slow lately doesn't mean nothing is happening. I just commited a change to timekpr-gui that will allow for i18n translations of timekpr! I am also looking into giving more fine grained control over when a user can be logged in.

I will have a lot to do at work at least until easter, probably until July. I still "think" timekpr code :)

---

### Post by crjackson on 2009-02-03
Post #1 has been updated.  I'll get the blog page in a day or two.  Thanks Even...

---

### Post by .nedberg on 2009-02-05
i18n support

You can now helt translate timekpr (only the GUI so far) in launchpad. Please go to: [https://translations.launchpad.net/timekpr/trunk/+pots/timekpr](https://translations.launchpad.net/timekpr/trunk/+pots/timekpr) and start translating!

---

### Post by SanskritFritz on 2009-02-05
So I did! As a thank you for this wonderful work! So good I am able to contribute. As I now have switched to Archlinux, I plan to build a package of timekpr in the [AUR]("http://aur.archlinux.org/"), as time permits.

---

### Post by unrater on 2009-02-05
Portuguese is now in 83% :D

I liked this software and so I'll do an article about it in my blog!

---

### Post by SanskritFritz on 2009-02-21
I have a problem translating the items #8 and #9 into hungarian:
> **Error in Translation:**               'msgstr' is not a valid Python format string, unlike 'msgid'. Reason: In the directive number 2, the character 'p' is not a valid conversion specifier.
The string I try to put is 
> Applied reward of %(num)s minute(s) to account %(user)s
%(user) számára %(num) perc jutalmat adtam> Set access hours to 00-24 on %(day)s for account %(user)s
00-24 hozzáférés %(user) számára %(day) napon
What is the reason?

UPDATE:
When I prepend the %(num) and %(user) with the **s**, all is ok. What is that **s**?

---

### Post by .nedberg on 2009-02-21
> **SanskritFritz said:**
> 

UPDATE:
When I prepend the %(num) and %(user) with the **s**, all is ok. What is that **s**?

The **s** is for the substitution, the **num** and **user** is just so that translators can change the order of the words. I had some problems with this my self... The **s** was not included in my first tries and the translation did not work at all.

---

### Post by SanskritFritz on 2009-02-21
> **.nedberg said:**
> The **s** is for the substitution, the **num** and **user** is just so that translators can change the order of the words. I had some problems with this my self... The **s** was not included in my first tries and the translation did not work at all.Ah ok, so it's OK now, thanks!

---

### Post by SanskritFritz on 2009-02-21
.nedberg, I need some hints on how to build the program from the sources. I want to build an Archlinux package. I there a description somewhere on the lauchpad site?

---

### Post by .nedberg on 2009-02-22
> **SanskritFritz said:**
> .nedberg, I need some hints on how to build the program from the sources. I want to build an Archlinux package. I there a description somewhere on the launchpad site?

I don't know about Arch, but I used this how-to: [https://help.launchpad.net/Packaging/PPA](https://help.launchpad.net/Packaging/PPA)

Short answer: 'debuild -S -sa' in the source dir to make a source package, then upload it with dput.

To just make a .deb (the one I upload to my own server) for non-intrepid versions, I use 'debuild -us -uc' in the source dir.

I might publish a newer beta version soon, so those who use my ppa should decide if they want to use the stable ppa (from timekpr-maintainers) or my ppa with beta version. I would like it if some of you test the beta version, but I understand it if you want stable!

---

### Post by SanskritFritz on 2009-02-22
Ok, the question was not really about how to make the package, but rather, what to do if I want to install timekpr from the source? I examined the structure of the deb package, and there is no compilation phase as I can see it, am I right? Installing is merely just copying the files to their respective places, and running the different install scripts?

---

### Post by forger on 2009-02-23
> Installing is merely just copying the files to their respective places, and running the different install scripts?
Edit: No, there's no compilation, python .py files are taken straight away, copied and replaced where necessary.

Unfortunately, timekpr uses a lot of debian's packaging stuff. Debian handles a lot of the installation scripts. Arch gives you much more power by letting you decide how the installation goes in a single command script.

To package it properly you have to look at **every file** under debian/ folder, especially postinst (post-installation) and postrm (post-remove and post-purge) and control files.

I'm working on a transition to proper python setuptools packaging, which would make the install easier to every operating system, but it will take a while, with my exams, the ubuntu-cy management and other stuff in the way. It will be my top priority for April.

If anyone is interested to do this, be my guest. :)

---

### Post by forger on 2009-03-05
Hey everyone, good news!! In revision #205 I patched timekpr to include support for both Python 2.x and Python 3!

It needs testing of course, but from what I've tested with simple commands and running the gui, it seems it works!

Fortunately we do not use many dependencies, and hopefully we'll be able to test it real-time using python 3 when ubuntu moves to python3 - or if someone else wants to try it. :) (note: ubuntu jaunty will have python2.6 as default)

---

### Post by forger on 2009-03-14
If anyone likes real-time IRC discussion, join #timekpr at
[irc://chat.freenode.net/timekpr]("irc://chat.freenode.net/timekpr")

:D

Or through mibbit:
[http://widget.mibbit.com/?server=chat.freenode.net&channel=%23timekpr&noServerNotices=true&noServerMotd=true](http://widget.mibbit.com/?server=chat.freenode.net&channel=%23timekpr&noServerNotices=true&noServerMotd=true)

---

### Post by forger on 2009-03-14
I've stripped out the old scheduler plugin from the old versions of deluge-torrent, it could be useful for setting time restrictions. Attaching it for future purposes. :)

---

### Post by crjackson on 2009-04-08
With the up coming release of Jaunty, I'll be updating all my desktops. Are there any special considerations regarding the install of timekpr and it's repositories?

---

### Post by SanskritFritz on 2009-04-09
> **forger said:**
> If anyone likes real-time IRC discussion, join #timekpr at
[irc://chat.freenode.net/timekpr](irc://chat.freenode.net/timekpr)I failed to find that channel! Is it still alive?

---

### Post by .nedberg on 2009-04-09
> **SanskritFritz said:**
> I failed to find that channel! Is it still alive?

It is alive, I am connected right now.

In your irc-client connect to chat.freenode.net and join the channel #timekpr, at leaste that is what worked for me. I use Konversation to connect.

---

### Post by .nedberg on 2009-04-09
> **crjackson said:**
> With the up coming release of Jaunty, I'll be updating all my desktops. Are there any special considerations regarding the install of timekpr and it's repositories?

Not much, except that you will hit [Bug #344538]("https://bugs.launchpad.net/timekpr/+bug/344538").

I am thinking of making a Jaunty repository before the release. I also think I will make a new package with all the fixes so far. It is not much, but some bugs have been fixed and the translations will be included (at least the finished ones. Portuguese, Spanish and Czech still needs some work). I'll see if I can publish a beta this weekend so it can be tested!

---

### Post by SanskritFritz on 2009-04-09
> **.nedberg said:**
> It is alive, I am connected right now.

In your irc-client connect to chat.freenode.net and join the channel #timekpr, at leaste that is what worked for me. I use Konversation to connect.I guess it is not in the list? Sadly the only way to join a channel in Pidgin i know, is listing the channels.

---

### Post by .nedberg on 2009-04-09
> **SanskritFritz said:**
> I guess it is not in the list? Sadly the only way to join a channel in Pidgin i know, is listing the channels.
Try
```

/join #timekpr

```
in pidgin to join #timekpr after connecting to irc.freenode.net

---

### Post by crjackson on 2009-04-09
> **.nedberg said:**
> Not much, except that you will hit [Bug #344538]("https://bugs.launchpad.net/timekpr/+bug/344538").

I am thinking of making a Jaunty repository before the release. I also think I will make a new package with all the fixes so far. It is not much, but some bugs have been fixed and the translations will be included (at least the finished ones. Portuguese, Spanish and Czech still needs some work). I'll see if I can publish a beta this weekend so it can be tested!

That would be great if you could push a new package out before the Jaunty release. It should cut down on the bug reports during the OS transition. I'll wait for timekpr before I start to migrate my target desktops.

---

### Post by .nedberg on 2009-04-09
> **crjackson said:**
> That would be great if you could push a new package out before the Jaunty release. It should cut down on the bug reports during the OS transition. I'll wait for timekpr before I start to migrate my target desktops.

I am planning on making some builds and doing some testing tonight (in a few hours actually). Just have to eat and put the girls to bed :)

---

### Post by crjackson on 2009-04-09
> **.nedberg said:**
> I am planning on making some builds and doing some testing tonight (in a few hours actually). Just have to eat and put the girls to bed :)

Cool beans. I have one Jaunty desktop and one laptop for testing

---

### Post by .nedberg on 2009-04-09
> **crjackson said:**
> Cool beans. I have one Jaunty desktop and one laptop for testing

I'll PM you a link to a .deb for testing when I am done!

---

### Post by .nedberg on 2009-04-12
Please help translating if you can! We still have some work to do on Portuguese, Spanish and Czech. If you can help with any of those languages please do so at [https://translations.launchpad.net/timekpr](https://translations.launchpad.net/timekpr).

If you can translate into any other language please help out with that too! Any unfinished translations by next weekend (2009-04-19) will be left out of the next release!

By the way; there is a "bug" in Rosetta, the translations part of launchpad. There is one string, "translator-credits", that cannot be translated. You will be left with one untranslated string. That is fine, it will be taken care of internally by Launchpad.

If you need help with any of the strings ask in #timekpr on chat.freenode.net or post here.

---

### Post by .nedberg on 2009-04-18
Just wanted to let everyone know that version 0.3.0 has been released!

You can add the timekpr-maintainers PPA from [https://launchpad.net/~timekpr-maintainers/+archive/ppa](https://launchpad.net/~timekpr-maintainers/+archive/ppa) or use my PPA from [https://launchpad.net/~nedberg/+archive/ppa](https://launchpad.net/~nedberg/+archive/ppa).

My PPA will include beta version, while the timekpr-maintainers PPA will only provide stable version.

We have PPAs for Jaunty, Intrepid and Hardy.

Please report any bugs at [https://bugs.launchpad.net/timekpr](https://bugs.launchpad.net/timekpr)

I will try to publish a complete changelog from 0.2.2 later!

---

### Post by crjackson on 2009-04-18
> **.nedberg said:**
> Just wanted to let everyone know that version 0.3.0 has been released!

You can add the timekpr-maintainers PPA from [https://launchpad.net/~timekpr-maintainers/+archive/ppa](https://launchpad.net/~timekpr-maintainers/+archive/ppa) or use my PPA from [https://launchpad.net/~nedberg/+archive/ppa](https://launchpad.net/~nedberg/+archive/ppa).

My PPA will include beta version, while the timekpr-maintainers PPA will only provide stable version.

We have PPAs for Jaunty, Intrepid and Hardy.

Please report any bugs at [https://bugs.launchpad.net/timekpr](https://bugs.launchpad.net/timekpr)

I will try to publish a complete changelog from 0.2.2 later!

Thanks Even. I'll update the 1st post and the blog in a couple of days. I'm dead tired. I'm been remodeling a room and hanging drywall all day so I just don't have it in me right now. I just got the update for timkpr and haven't had a chance to play with it yet.  Thanks for all your hard work.

---

### Post by .nedberg on 2009-04-19
Changelog for version 0.3.0:

[LIST]
[*] Timekpr-gui gives a warning if no other user than administrator is present (Bugs [#345515]("https://bugs.edge.launchpad.net/timekpr/+bug/345515") and [#330261]("https://bugs.edge.launchpad.net/timekpr/+bug/330261"), thanks to [BearTM]("https://edge.launchpad.net/~beartm"))
[*] An administrator will not be able to restrict him self ([Bug ##286529]("https://bugs.edge.launchpad.net/timekpr/+bug/286529"))
[*] Removed hard reference to /etc/timekpr in timekpr-client.py ([Bug #314061]("https://bugs.edge.launchpad.net/timekpr/+bug/314061")), allows for configuration of timekpr dir (no gui for this)
[*] Added a man page ([Bug #302770]("https://bugs.edge.launchpad.net/timekpr/+bug/302770"))
[*] Added i18n support ([Bug #302782]("https://bugs.edge.launchpad.net/timekpr/+bug/302782")), this release includes translations for Danish, Finnish, French, German, Hungarian, Norwegian Bokmal and Swedish. Please help to [translate timekpr into more languages]("https://translations.launchpad.net/timekpr")!
[*] Timekpr works with Jaunty ([Bug #344538]("https://bugs.edge.launchpad.net/timekpr/+bug/344538"))
[*] Fixed packaging error for KDE ([Bug #345515]("https://bugs.edge.launchpad.net/timekpr/+bug/345515"))
[*] Fixed a bug that could kick any user who was logged in all day, also unrestricted users and administrators
[/LIST]

If you want to install/update please add one of the PPAs from my previous post or get timekpr from the [download page]("https://edge.launchpad.net/timekpr/+download").

---

### Post by anne_maree on 2009-06-01
.nedberg, you are a godsend :D

(although my kids don't seem to think so.....:p)

---

### Post by peterVG on 2009-07-02
Excellent app! Works great on my new Jaunty install. Thanks so much for a very important requirement for many parents. Saves (noob) me from writing a whole set of scripts and provides one of the final pieces in the puzzle to justify migrating our home computer from Windows XP and letting my five year old loose on it. Now I just need to find a way to enforce a site whitelist in Firefox just for his user account...

---

### Post by .nedberg on 2009-07-02
> **peterVG said:**
> Excellent app! Works great on my new Jaunty install. Thanks so much for a very important requirement for many parents. Saves (noob) me from writing a whole set of scripts and provides one of the final pieces in the puzzle to justify migrating our home computer from Windows XP and letting my five year old loose on it. Now I just need to find a way to enforce a site whitelist in Firefox just for his user account...

A whitelist can be set up in quite an easy way, if you don't want to allow more than a few pages.

Set up firefox to use a fake proxy, then set a list for the pages you want to allow. IIRC Firefox has a plugin that will prevent changing the proxy without a password.

Else I would go for OpenDNS!

---

### Post by peterVG on 2009-07-03
> **.nedberg said:**
> A whitelist can be set up in quite an easy way, if you don't want to allow more than a few pages.

Set up firefox to use a fake proxy, then set a list for the pages you want to allow. IIRC Firefox has a plugin that will prevent changing the proxy without a password.

Else I would go for OpenDNS!

Thanks .nedberg I'll try that. If that doesn't work  I'm going to try ProCon Latte, [https://addons.mozilla.org/en-US/firefox/addon/1803](https://addons.mozilla.org/en-US/firefox/addon/1803) or SquidGuard, [https://help.ubuntu.com/community/SquidGuard](https://help.ubuntu.com/community/SquidGuard)

---

### Post by forger on 2009-07-03
OpenDNS is relatively easy to set up, you change a couple of DNS servers on your router or your Ubuntu: [https://www.opendns.com/start/device/ubuntu](https://www.opendns.com/start/device/ubuntu)

By default it blocks only phishing sites. You can make an account though at OpenDNS. This will allow you to block by categories or by typing in some of the websites you wish, depending on your wishes. You need 


If you have a dynamic IP, you ought to set up [ddclient]("apt://ddclient") with [dnsomatic]("http://www.dnsomatic.com") (you don't have to re-register with dnsomatic, use your opensdns username/password to login), using these settings ( /etc/ddclient.conf ):

```
# Configuration file for ddclient generated by debconf
#
# /etc/ddclient.conf
ssl=yes
pid=/var/run/ddclient.pid

##
## DNS-O-Matic account-configuration
##
use=web, web=myip.dnsomatic.com
server=updates.dnsomatic.com,      \
protocol=dyndns2,                  \
login='MYUSERNAME',          \
password='MYPASSWORD'        \
all.dnsomatic.com
```
(where MYUSERNAME and MYPASSWORD are your username and password)

---

### Post by forger on 2009-07-11
ok people, I've been looking this through, and it seems that timekprpam.py will have to change drastically. It should support all instances of /etc/security/time.conf so I should do that properly by parsing all possible layouts:
a) to get the limits I need
b) without interfering with other limits

Here's a basic layout, I'll see how I can get this done after my exams (long wait, but worth it!). I've used **_python-pyparsing_** which is easy to use and understand and much more readable when compared to regex:
```
# Check out: http://www.rexx.com/~dkuhlman/python_201/python_201.html#SECTION007600000000000000000
from pyparsing import Word, alphas, alphanums, ZeroOrMore, OneOrMore, LineStart, LineEnd, Optional, Group, Combine, Suppress

# define grammar
# services;ttys;users;times
# ! = NOT, & = AND, | = OR
# * = ANY (can be used only once)

tconf_splitchar = Suppress(";")
tconf_commonchars = "*!"
tconf_commonops = "&|"
tconf_services = Group(OneOrMore(Word(alphanums + tconf_commonchars) + Optional(Word(tconf_commonops))))
tconf_ttys = Group(OneOrMore(Word(alphanums + tconf_commonchars) + Optional(Word(tconf_commonops))))
tconf_users = Group(OneOrMore(Word(alphanums + tconf_commonchars) + Optional(Word(tconf_commonops))))
tconf_times = Group(OneOrMore(Word(alphanums + tconf_commonchars + "-") + Optional(Word(tconf_commonops))))
tconf_parser = LineStart() + tconf_services + tconf_splitchar + tconf_ttys + tconf_splitchar + tconf_users + tconf_splitchar + tconf_times + Optional(tconf_splitchar) + LineEnd()


# input string
test = "xsh ; ttyp*;root;!WdMo0000-2400"
moo = "blank & test;tty* & !ttyp*;you|me;!WdMo0000-2400 | !TuFr0800-2400"

# parse input string
print test, "->", tconf_parser.parseString(test)
print moo, "->", tconf_parser.parseString(moo)
```

---

### Post by forger on 2009-07-18
I've done some important changes with setup.py:
```
------------------------------------------------------------
revno: 245
branch nick: timekpr
timestamp: Sat 2009-07-18 14:01:52 +0200
message:
  Fixed py_modules
------------------------------------------------------------
revno: 244
branch nick: timekpr
timestamp: Sat 2009-07-18 13:50:50 +0200
message:
  Updated setup.cfg and i18n/POTFILES.in
------------------------------------------------------------
revno: 243
branch nick: timekpr
timestamp: Sat 2009-07-18 13:48:04 +0200
message:
  Moved to timekpr
------------------------------------------------------------
revno: 242
branch nick: timekpr
timestamp: Sat 2009-07-18 13:46:58 +0200
message:
  Restored timekprcommon.py, timekprpam.py
------------------------------------------------------------
revno: 241
branch nick: timekpr
timestamp: Sat 2009-07-18 13:45:09 +0200
message:
  Restored *.py
------------------------------------------------------------
revno: 240
branch nick: timekpr
timestamp: Sat 2009-07-18 13:44:21 +0200
message:
  Fixes
------------------------------------------------------------
revno: 239
branch nick: timekpr
timestamp: Sat 2009-07-18 13:22:53 +0200
message:
  Include POTFILES.in
------------------------------------------------------------
revno: 238
branch nick: timekpr
timestamp: Sat 2009-07-18 13:16:52 +0200
message:
  Include timekpr-client.desktop.in
------------------------------------------------------------
revno: 237
branch nick: timekpr
timestamp: Sat 2009-07-18 13:01:48 +0200
message:
  Dropped old/
------------------------------------------------------------
revno: 236
branch nick: timekpr
timestamp: Sat 2009-07-18 12:47:57 +0200
message:
  Dropped locale directory
------------------------------------------------------------
revno: 235
branch nick: timekpr
timestamp: Sat 2009-07-18 12:41:09 +0200
message:
  Cleared TODO.txt, Disabled build_icons
------------------------------------------------------------
revno: 234
branch nick: timekpr
timestamp: Sat 2009-07-18 12:33:00 +0200
message:
  * Begin transformation (S.O.S. :-))
  * Dropped ez-setup, using python-distutils and python-distutils-extra
  * Dropped complexities - keep it simple
  * Created *.in templates for kde and gnome .desktop files
  * Nicolas as "code recommendations and guidance" contributor


```

WARNING: THE "trunk" is as of now **_REALLY UNSTABLE_**.
This is all new for me, so please be patient :oops:

---

### Post by crjackson on 2009-07-19
> **forger said:**
> OpenDNS is relatively easy to set up, you change a couple of DNS servers on your router or your Ubuntu: [https://www.opendns.com/start/device/ubuntu](https://www.opendns.com/start/device/ubuntu)

By default it blocks only phishing sites. You can make an account though at OpenDNS. This will allow you to block by categories or by typing in some of the websites you wish, depending on your wishes. You need 


If you have a dynamic IP, you ought to set up [ddclient]("apt://ddclient") with [dnsomatic]("http://www.dnsomatic.com") (you don't have to re-register with dnsomatic, use your opensdns username/password to login), using these settings ( /etc/ddclient.conf ):

```
# Configuration file for ddclient generated by debconf
#
# /etc/ddclient.conf
ssl=yes
#pid=/var/run/ddclient.pid

##
## DNS-O-Matic account-configuration
##
use=web, web=myip.dnsomatic.com
server=updates.dnsomatic.com,      \
protocol=dyndns2,                  \
login='MYUSERNAME',          \
password='MYPASSWORD'        \
all.dnsomatic.com
```
(where MYUSERNAME and MYPASSWORD are your username and password)

forger, will this prevent a laptop that roams to various hotspots from bypassing opendns filtering?  This is my current problem...

---

### Post by forger on 2009-07-19
> **crjackson said:**
> forger, will this prevent a laptop that roams to various hotspots from bypassing opendns filtering?  This is my current problem...

No idea, I don't have a laptop to test it out. Do try these though:

a) You might have to make it update more often than it does now:
```
gksu gedit /etc/default/ddclient
```

***daemon_interval*** is the variable you're looking for, it's expressed in seconds, but I think every 5 minutes is the limit for services like dyndns. :)

b) Also, there is the ***run_ipup*** that should be set to "**true**":
> 
# Set to "true" if ddclient should be run every time a new ppp connection is 
# established. This might be useful, if you are using dial-on-demand
run_ipup="true"

c) Finally, I think that you can set up a script in folder "/etc/network/if-up.d/". You could check the rest of the scripts to see how it works (never tried one)

Or you could try copying the ip-up.d script:
```
sudo cp /etc/ppp/ip-up.d/ddclient /etc/network/if-up.d/ddclient
```
(You need (b) first)
This should update ddclient every time you switch connection.

And reboot your computer.  Let me know if (c) works if you try it out :)

P.S. Don't forget to restart ddclient:
```
sudo /etc/init.d/ddclient restart
```

Um.. and remove the "#" in file /etc/ddclient.conf from the line with "pid=.." variable, that prevents it. In this case, you have to execute this to make it restart:
```
sudo killall ddclient
sudo /etc/init.d/ddclient start
```

---

### Post by crjackson on 2009-07-20
I've been very busy with a new job and I haven't had a chance to try it yet. I sure hope it works.  I'll let you know when I get the time to test it.

---

### Post by forger on 2009-07-24
In order to gather up everything, I would like to let you know that I will drop the [blog site]("http://timekpr.blogspot.com") (since it doesn't serve any specific purpose).
I will register timekpr in freshmeat ([www.freshmeat.net]("http://www.freshmeat.net")), where they actually control and fix your text and any publishing errors/typos. :)

Is this ok with you, crjackson & nedberg ?

---

### Post by forger on 2009-07-24
I've created the freshmeat project (will be available to public after they review it): [http://freshmeat.net/projects/timekpr](http://freshmeat.net/projects/timekpr)

I still need an "OK" from crjackson & nedberg to remove the blog :)

---

### Post by .nedberg on 2009-07-24
> **forger said:**
> 

Is this ok with you, crjackson & nedberg ?

OK!

I never understood why we needed a blog.

---

### Post by forger on 2009-07-25
It was to report the new releases, but now that I found freshmeat, it makes much more sense to put them there. Packagers etc will want that and usually subscribe at freshmeat. :)

crjackson? :)

---

### Post by crjackson on 2009-07-25
> **forger said:**
> I've created the freshmeat project (will be available to public after they review it): [http://freshmeat.net/projects/timekpr](http://freshmeat.net/projects/timekpr)

I still need an "OK" from crjackson & nedberg to remove the blog :)

Yes, that's fine with me too...

---

### Post by forger on 2009-07-26
In case  you're wondering, the reason for requiring the ok from both was that both of you were part of it, so I didn't want the wrong picture about my actions. Thanks again :)

---

### Post by coolnezz on 2009-10-14
cool program.

but how can I change the setting to 12 hours, instead for resetting the time every 24 hours?

thanks.

---

### Post by .nedberg on 2009-10-14
> **coolnezz said:**
> cool program.

but how can I change the setting to 12 hours, instead for resetting the time every 24 hours?

thanks.

Humm, I cannot think of an easy way to do this. It would require a lot of changes to the code. It is based on a day (24 hours), and dates. Changing to 12 hours would at least make the checking of dates useless.

On idea though:
Set up two accounts, block one after 12 (or any other time of day) and the other before. Make the user use both accounts. Not a great solution, but it should work.

---

### Post by coolnezz on 2009-10-14
hmm... i have like 10-15 users on a computer with different usernames.
although some don't login everyday, but some would like to use the computer again within that 24 hour period when the computer is not being used.  but i want all users to have 1 hour per login so others can use the computer fairly.

---

### Post by .nedberg on 2009-10-14
I don't think timekpr can be used that way without a lot of work. 

To use my idea you would have to create 20-30 users. That would be a lot of work and it would complicate things.

Sorry, can't help with much else!

---

### Post by coolnezz on 2009-10-15
yeah... i guess i'll just have to add additional minutes per user per day.  thanks tho!

---

### Post by coolnezz on 2009-10-15
btw... is there a way to make the popup notifier stay on longer? like 10 seconds or something?  i tried looking at a couple of timekpr config files but i couldn't find it.  thanks.

---

### Post by .nedberg on 2009-10-16
> **coolnezz said:**
> btw... is there a way to make the popup notifier stay on longer? like 10 seconds or something?  i tried looking at a couple of timekpr config files but i couldn't find it.  thanks.

Edit timekpr-client.py, somewhere around line 257, you will see:
```

getcmdoutput('notify-send --icon=gtk-dialog-warning --urgency=critical -t 3000 "' + title + '" "' + message + '"')

```

change '-t 3000' into something else. For 10 seconds, use '-t 10000'.

This will work in Gnome and XFCE, you can change it for KDE further down in the file, but I don't have the right revision to look it up. If you need it, just post the code here and I will tell you how to change it!

---

### Post by shane2peru on 2009-10-17
> **.nedberg said:**
> Edit timekpr-client.py, somewhere around line 257, you will see:
```

getcmdoutput('notify-send --icon=gtk-dialog-warning --urgency=critical -t 3000 "' + title + '" "' + message + '"')

```

change '-t 3000' into something else. For 10 seconds, use '-t 10000'.

This will work in Gnome and XFCE, you can change it for KDE further down in the file, but I don't have the right revision to look it up. If you need it, just post the code here and I will tell you how to change it!

Yes, I need to change mine too.  My kids always tell me they never see it.  Thanks for the info.  Perhaps a 5 second default may be better?  I'm sure for older children 3 seconds is more than sufficient. Just a thought.  I'm going to go excessive and put the 10 second warning. :)

Thanks for the GREAT app!!!  Very nice, and appreciated.

Shane

---

### Post by coolnezz on 2009-10-17
@ .nedberg

oh so that's the file. actually, i found that same file before and i did try changing that number to 30000, then 10000 but i didn't notice any time change on the notifier.  before i made a change it stayed on for ~5 seconds.  so i changed it to 10000 or something higher but it was still popping up for only 5 seconds.  maybe i was changing the section for KDE.  or perhaps i was editing the file from a different directory? i'm going to try again.  i'm using GNOME and XFCE.
just to make sure, can you please confirm which directory?

/usr/share/python-support/timekpr/timekpr-client.py

/var/lib/python-support/python2.5/timekpr-client.py

/var/lib/python-support/python2.6/timekpr-client.py


thanks a lot! :)

---

### Post by shane2peru on 2009-10-17
Hey, just found this neat little applet, it is timer-applet.  It can be configured to set on the panel and count down the time for you.  Really pretty neat, and as soon as a saw it I thought this would be a neat little gadget for time-kpr!  Ok, I admit I don't know how hard this would be to implement.  But I thought I would point it out.  It is pretty neat. 

Shane

---

### Post by coolnezz on 2009-10-18
> **shane2peru said:**
> Hey, just found this neat little applet, it is timer-applet.  It can be configured to set on the panel and count down the time for you.  Really pretty neat, and as soon as a saw it I thought this would be a neat little gadget for time-kpr!  Ok, I admit I don't know how hard this would be to implement.  But I thought I would point it out.  It is pretty neat. 

Shane



that would be really useful if people can see all the time how much time they have left.

---

### Post by jeromio on 2009-10-19
Feature request: store data remotely. 

I am in the process of setting up a 2nd laptop for my kids. I want them to be able to use whichever computer, but I don't want them to have the ability to basically double their computer time by just logging on to the 2nd one after time is up on the 1st. To me it seems like storing the time data on an NFS (or preferably SMB) share would solve this problem.

Along similar lines, I'd like the ability to remotely add time. So if a kid is working on an assignment, I could add time without having to log myself onto the computer they're using.

Thanks.

BTW, this app is working great and really helps to automate the process of monitoring/limiting computer use at my house. The computer also happens to be the only way to watch TV shows, so overall, timekpr is a great referee for slothitude.

---

### Post by .nedberg on 2009-10-19
> **jeromio said:**
> Feature request: store data remotely. 


Great idea!

This will have to wait until a later version! It could be configurable via an "Advanced" admin-gui.

For now, you can achieve this in two ways:
1. In timekprcommon.py change TIMEKPRDIR, TIMEKPRWORK and TIMEKPRSHARED into a path on an NFS or samba share.

or

2. Mount a NFS or samba share at the locations already in timekprcommon.py (/etc/timekpr, /var/lib/timekpr and /usr/share/timekpr).


Logging into two or more machines at the same time would be like burning a candle at both ends!

Please, if you try this, give some feedback on how it works out. And if you have the time, write up a blueprint / feature request on [https://launchpad.net/timekpr](https://launchpad.net/timekpr)!

---

### Post by .nedberg on 2009-10-19
> **shane2peru said:**
> Hey, just found this neat little applet, it is timer-applet.  It can be configured to set on the panel and count down the time for you.  Really pretty neat, and as soon as a saw it I thought this would be a neat little gadget for time-kpr!  Ok, I admit I don't know how hard this would be to implement.  But I thought I would point it out.  It is pretty neat. 

Shane

> **coolnezz said:**
> that would be really useful if people can see all the time how much time they have left.

Yes, that is a neat applet! It might get a bit hard to implement, but I am sure it would be do-able. It would, however, need different code for Gnome/KDE and perhaps also XFCE.

And people can already see how much time they have left by clicking on the timekpr icon.

I am not saying this won't happen, but I don't think I will put to much effort into it.

---

### Post by shane2peru on 2009-10-19
> **.nedberg said:**
> Yes, that is a neat applet! It might get a bit hard to implement, but I am sure it would be do-able. It would, however, need different code for Gnome/KDE and perhaps also XFCE.

And people can already see how much time they have left by clicking on the timekpr icon.

I am not saying this won't happen, but I don't think I will put to much effort into it.

No problem, as time allows!  No pun intended.  Perhaps even just the idea could be 'borrowed' and have something similar and not necessarily use that applet.  I'm quite pleased with timekpr the way it is, so if it doesn't get added, I'm not going to complain, just thought it would be a neat improvement if not too difficult.  Thanks for the work you have done!!!

Shane

---

### Post by .nedberg on 2009-10-19
> **coolnezz said:**
> @ .nedberg

oh so that's the file. actually, i found that same file before and i did try changing that number to 30000, then 10000 but i didn't notice any time change on the notifier.  before i made a change it stayed on for ~5 seconds.  so i changed it to 10000 or something higher but it was still popping up for only 5 seconds.  maybe i was changing the section for KDE.  or perhaps i was editing the file from a different directory? i'm going to try again.  i'm using GNOME and XFCE.
just to make sure, can you please confirm which directory?

/usr/share/python-support/timekpr/timekpr-client.py

/var/lib/python-support/python2.5/timekpr-client.py

/var/lib/python-support/python2.6/timekpr-client.py


thanks a lot! :)

Correct file is /usr/share/python-support/timekpr/timekpr-client.py

The code you need to change is on line 228. But it looks like it is not working! The popup only stays for about 10 sec on my comupter, whatever I use for -t.

---

### Post by coolnezz on 2009-10-23
> **.nedberg said:**
> 

And people can already see how much time they have left by clicking on the timekpr icon.





Yup. But some users are not computer savvy. they don't even know/care what icon is what.  unless you tell them of course, but that can be a hassle because different new users are using the computer everyday.  and some users don't even pay attention or just miss the popup notification because they're to engrossed with their web surfing.  that's why in my opinion a longer popup or a constant time countdown on the panel would really be helpful.  i think this is what they have on internet cafe timers if i'm not mistaken.

---

### Post by coolnezz on 2009-10-23
> **jeromio said:**
> Feature request: store data remotely. 

I am in the process of setting up a 2nd laptop for my kids. I want them to be able to use whichever computer, but I don't want them to have the ability to basically double their computer time by just logging on to the 2nd one after time is up on the 1st. To me it seems like storing the time data on an NFS (or preferably SMB) share would solve this problem.

Along similar lines, I'd like the ability to remotely add time. So if a kid is working on an assignment, I could add time without having to log myself onto the computer they're using.

Thanks.

BTW, this app is working great and really helps to automate the process of monitoring/limiting computer use at my house. The computer also happens to be the only way to watch TV shows, so overall, timekpr is a great referee for slothitude.


I think that's almost like an internet cafe timer.  server/client with remote time management.

---

### Post by .nedberg on 2009-10-27
Can someone using Karmic please report if timekpr is working or not. I don't think the notifier is working in Kubuntu, but if someone can test in X/K/Ubuntu and report here I would appreciate it.

If there is a problem I will see if I can fix it and release a new version by the end of the week.

If I have to do some changes to the code I will use the source from the released version, as the 'trunk' branch is not in a stable state atm.

---

### Post by crjackson on 2009-10-27
> **.nedberg said:**
> Can someone using Karmic please report if timekpr is working or not. I don't think the notifier is working in Kubuntu, but if someone can test in X/K/Ubuntu and report here I would appreciate it.

If there is a problem I will see if I can fix it and release a new version by the end of the week.

If I have to do some changes to the code I will use the source from the released version, as the 'trunk' branch is not in a stable state atm.

I'll test it tomorrow afternoon.  I'm at work right now and can't do it.

---

### Post by anne_maree on 2009-10-28
> **.nedberg said:**
> Can someone using Karmic please report if timekpr is working or not. I don't think the notifier is working in Kubuntu, but if someone can test in X/K/Ubuntu and report here I would appreciate it.

Hi .nedberg,

I've got a 'test' lappy I'm trying Ubuntu Karmic on, and am getting an error of


```
dpkg: unable to read filedescriptor flags for <package status and progress file desctiptor>: Bad file descriptor
```

using GDebi 0.5.9

If you want me to test any changes, I'm more than willing. I love timekpr. My kids hate it :p

---

### Post by .nedberg on 2009-10-29
> **anne_maree said:**
> Hi .nedberg,

I've got a 'test' lappy I'm trying Ubuntu Karmic on, and am getting an error of


```
dpkg: unable to read filedescriptor flags for <package status and progress file desctiptor>: Bad file descriptor
```

using GDebi 0.5.9

If you want me to test any changes, I'm more than willing. I love timekpr. My kids hate it :p

I just made a Ubuntu Karmic virtual machine and I am not seeing this error when I install timekpr.

After a quick test with a restricted account I can see that notifications are working.

EDIT: It also installs fine in Kubuntu, but no notifications
EDIT2: The user is also logged out in Ubuntu!
EDIT3: I managed to fix the notifications in Kubuntu!
EDIT4: And the user is kicked in Kubuntu, I am going to bed now...

---

### Post by .nedberg on 2009-10-31
Looks like Xubuntu is working fine too! I will do some more testing and see if I can publish a new release soon.

Look out for a beta release in my PPA, if it works I will publish in timekpr-maintainers PPA.

---

### Post by anne_maree on 2009-11-01
Upgraded a desktop to Karmic (from Jaunty), a netbook to Karmic (from Jaunty) and the spare lappy to Karmic (from the RC), and it works in all :)

The kids are not impressed :popcorn:

---

### Post by .nedberg on 2009-11-01
An updated version (0.3.1) is in the build queue on Launchpad for release in my PPA. Karmic will be first, then I will copy to Hardy/Intrepid/Jaunty.

After some testing in all four versions of X/K/Ubuntu, I will publish to timekpr-maintainers PPA.

EDIT: Argh, the build failed. My fault. I will try again later today!

---

### Post by .nedberg on 2009-11-01
> **anne_maree said:**
> Upgraded a desktop to Karmic (from Jaunty), a netbook to Karmic (from Jaunty) and the spare lappy to Karmic (from the RC), and it works in all :)

The kids are not impressed :popcorn:

Good to hear that updates are going fine! And that timekpr is still working.

I take it you are using normal Ubuntu with Gnome?

---

### Post by anne_maree on 2009-11-01
> **.nedberg said:**
> I take it you are using normal Ubuntu with Gnome?

Yep Yep. Just the standard, out of the box install, the main use of these computers is homework (and games of course!).

Your work with this is wonderful. Saves a lot of nagging of 'get off the computer' - they just log them out and that is that :D It also prevents the teenager from sitting on msn when he should be studying, much to his disgust.

---

### Post by .nedberg on 2009-11-02
I am experiencing some problems with the packaging. It builds fine, and installs, but something is wrong. It looks like the files install to the wrong places in Karmic. :(

I will need to look more into this, so I will not get the time to make a release anytime soon. I will keep you posted though!

---

### Post by .nedberg on 2009-11-05
I currently have beta packages of timekpr for Hardy, Intrepid, Jaunty and Karmic in [my PPA]("https://launchpad.net/~nedberg/+archive/ppa").

The release mostly contains fixes for notifications in Kubuntu/KDE4. I will have to do some more testing in all versions of Ubuntu. If anyone can help out it would be appreciated!

I had to build the packages on Jaunty, then copy to Karmic. If I built on Karmic, it would result in a Python error ("no module named _cairo"). I used the same trick earlier to make a Hardy package. Something has changed in Python and I need time to figure out what.

If this version works fine I will publish version 0.3.1 to timekpr-maintainers PPA soon!

---

### Post by .nedberg on 2009-11-08
OK, so I have done some testing this weekend (today actually). We currently have the following results for the beta version of timekpr 0.3.1:

Ubuntu 8.04: Works!
Ubuntu 9.04: Works!
Ubuntu 9.10: Works!
Kubuntu 8.04: Works!
Kubuntu 9.04: Works!
Kubuntu 9.10: Works!
Xubuntu 8.04: Works!
Xubuntu 9.04: Works!
Xubuntu 9.10: Works!

:popcorn:

Version 0.3.1 isn't very different from 0.3.0. It fixes a bug in KDE4.3 where the notifications did not show (reported as [Bug #302774]("https://bugs.launchpad.net/timekpr/+bug/302774")). The new version also contains better code for the formatting of the messages in the notifications.

I have done updates from previous versions of timekpr (0.3.0 and 0.2.2) and fresh installs. It all looks good! But if at all possible I would recommend a fresh install!

You can get the beta release from [my PPA]("https://launchpad.net/~nedberg/+archive/ppa"), or wait for the stable release in [timekpr-maintainers PPA]("https://launchpad.net/~timekpr-maintainers/+archive/ppa"). I will probably submit a release to my PPA tomorrow (November 9th). Launchpad has got a long build queue at the moment, so it won't show up in a couple of days. And then I need to copy the package to the different releases of Ubuntu.

---

### Post by .nedberg on 2009-11-09
I am happy to tell you that timekpr 0.3.1 is live. Get it while it is hot!

[https://launchpad.net/~timekpr-maintainers/+archive/ppa/](https://launchpad.net/~timekpr-maintainers/+archive/ppa/)
or
[https://launchpad.net/~nedberg/+archive/ppa](https://launchpad.net/~nedberg/+archive/ppa)

My PPA will contain changes and future beta releases, it might break your system. But please use it if you can!
[CENTER]
[IMG]https://launchpadlibrarian.net/18541084/timekpr-logo.png[/IMG][/CENTER]

---

### Post by .nedberg on 2010-01-03
I just copied version 0.3.2 from my PPA to timekpr-maintainers PPA. This version does not change much, but notifications might work in more DEs than KDE/Gnome/XFCE. I just added a default way to give notifications, hoping it will work in the current DE. I tested in LXDE (with Lubuntu), and it works fine!

Feedback on other DEs where it works is appreciated!

---

### Post by brandoncolorado on 2010-01-09
> **.nedberg said:**
> I just copied version 0.3.2 from my PPA to timekpr-maintainers PPA. This version does not change much, but notifications might work in more DEs than KDE/Gnome/XFCE. I just added a default way to give notifications, hoping it will work in the current DE. I tested in LXDE (with Lubuntu), and it works fine!

Feedback on other DEs where it works is appreciated!

Thanks for all of the work you do on this.

---

### Post by brandoncolorado on 2010-01-09
Just a note -- I don't get any countdown in Karmic.

---

### Post by .nedberg on 2010-01-10
> **brandoncolorado said:**
> Just a note -- I don't get any countdown in Karmic.

I am also seeing this in Ubuntu Karmic. I have no idea why. Will have another look at it later!

Is this happening to anybody else?

I tested in Gnome/KDE/XFCE and it is only in Gnome that the notifications is not showing.

---

### Post by brandoncolorado on 2010-01-10
After a reboot, I do notice a 2 minute warning.  However, after another reboot, I don't even see the timekpr-client anymore.  When I check running processes, it isn't there.  However, when I run it, it seems that the time is counting down.  After another reboot, the icon showed up, so maybe it is a glitch.

---

### Post by .nedberg on 2010-01-10
> **brandoncolorado said:**
> After a reboot, I do notice a 2 minute warning.  However, after another reboot, I don't even see the timekpr-client anymore.  When I check running processes, it isn't there.  However, when I run it, it seems that the time is counting down.  After another reboot, the icon showed up, so maybe it is a glitch.

Oh, time is counting! The client has nothing to do with that! I just want to find out why there is no notifications.

---

### Post by .nedberg on 2010-01-21
> **brandoncolorado said:**
> Just a note -- I don't get any countdown in Karmic.

Is this still the case? I just did some testing in Ubuntu Karmic and everything worked fine. Might have been some updates. I am not a Ubuntu user (I am a kperson), so I don't know when this might have happened.

---

### Post by crjackson on 2010-04-14
It sure is quiet in here lately.  Anything new on the horizon?

---

### Post by shane2peru on 2010-04-15
anyone try this on Lucid?  I have Lucid installed and just added the PPA, however I put lucid in the line, going to see if this will work.  

Shane

**EDIT:**  Well installed fine, and seems to work.  I setup the kids accounts I guess we will see how this goes.

---

### Post by .nedberg on 2010-04-16
> **shane2peru said:**
> anyone try this on Lucid?  I have Lucid installed and just added the PPA, however I put lucid in the line, going to see if this will work.  

Shane

**EDIT:**  Well installed fine, and seems to work.  I setup the kids accounts I guess we will see how this goes.

I have also done some testing the last few days. It seems to work fine! I have the latest version in my PPA for Lucid, not copied to timekpr-maintainers PPA yet. Will copy when I have done some more testing and Lucid is closer.

---

### Post by Onesimus on 2010-05-02
> **.nedberg said:**
> I have also done some testing the last few days. It seems to work fine! I have the latest version in my PPA for Lucid, not copied to timekpr-maintainers PPA yet. Will copy when I have done some more testing and Lucid is closer.

Is there any update on when timekpr might appear for Lucid ?

---

### Post by shane2peru on 2010-05-02
I'm using the karmic version of Timekpr on my Lucid install and it works great.  No problems.  I'm not 100% sure about all the warnings, but seems to kick the kids off after their aloted time. :)

Shane

---

### Post by .nedberg on 2010-05-02
Just copied to Lucid in timekpr-maintainers PPA. It is the same package as i Karmic.

[https://launchpad.net/~timekpr-maintainers/+archive/ppa](https://launchpad.net/~timekpr-maintainers/+archive/ppa)

---

### Post by crjackson on 2010-05-02
I'm posting this here because I keep forgetting the new ppa command for karmic / Lucid.

Just use the command below to add both the repository and the key at the same time.

```
sudo add-apt-repository ppa:timekpr-maintainers/ppa
```

---

### Post by shane2peru on 2010-07-19
Ok, I used this script for quite some time on my laptop, however because of some really technical reasons had to switch to a different distro to keep the laptop from overheating.  Can I get the latest python script?  and some basic installation instructions to port this to a different distro?  This is the greatest tool that I have ever used for my kids on the computer, and I really need it.  Thanks!

Shane

---

### Post by .nedberg on 2010-07-19
You should be able to find all you need here: [https://launchpad.net/timekpr](https://launchpad.net/timekpr)

I suggest trying with code from the stable branch, that is what the latest release is based on. I don't think trunk will work at all!

Savvas is working on changes that will probably ease up porting to other distros, but I have no idea how that is coming along.

---

### Post by shane2peru on 2010-07-21
Well, portability looks like it is still a ways off, mean time I came up with a highly portable, and very crude edition.  You all are the pro's so I'm posting it here for some critiques. :)

```

#!/bin/bash
# This script depends upon wmtimer, it is a crude script to log off a user after a certain amount of time.  Idea is all based on timekpr (https://launchpad.net/timekpr) , however they are more talented than I. :)
#Now requires: wmtimer zenity
time1=00:45:00
time2=00:15:00
time3=00:02:00

wmtimer -a -c -t $time1 -b & sleep 45m
killall wmtimer
zenity --info --text "You have 15 minutes left." &&
wmtimer -color red -a -c -t 00:00:10 -b & sleep 13m
zenity --info --text "Save your work! 2 Min Warning!"  & sleep 2m
killall wmtimer
pkill -KILL -u $USER
exit

```

I named it timelimit, and put it in /usr/bin  then created a .profile for each user, and put timelimit & in the profile.  It is crude, but functional for the time being.  Any bash script improvements are appreciated. :)  Thanks.

Shane

---

### Post by SanskritFritz on 2010-10-03
Loong time ago I promised to make an Archlinux AUR package. Well, today I uploaded the first version to AUR:
[http://aur.archlinux.org/packages.php?ID=41435](http://aur.archlinux.org/packages.php?ID=41435)
Thank you again for timekpr.

---

### Post by .nedberg on 2010-10-13
Hi everyone!

Just stopping by to tell you that I have copied timekpr into the Maverick section of timekpr-maintainers PPA.

Get it while it is hot: [https://launchpad.net/~timekpr-maintainers/+archive/ppa](https://launchpad.net/~timekpr-maintainers/+archive/ppa)

Nothing has changes since the earlier versions, so I have not done any extensive testing. But everything looks like it is working :)

---

### Post by .nedberg on 2010-11-14
Hi everyone.

As you all may have noticed, development on timekpr has been rather slow lately. Both Savvas/forger and I have had different things happening in our lives. In addition we recently became aware of a Gnome application called [Nanny]("http://projects.gnome.org/nanny/"). We both feel that Nanny has a better chance of getting all the features we all wanted to be put into timekpr, and Nanny also has a lot more backing.

Savvas and I have decided that we probably won't do much more coding on timekpr. We both might drop by to fix a bug or two or answer some questions.

Thanks to all of you for your support, kind words and help along the way. It was fun while it lasted, it is time to move one to something different.

---

### Post by anne_maree on 2010-11-14
Thanks for all your work over the past few years, .nedberg. You have saved the sanity of parents all over the world :)

---

### Post by shane2peru on 2010-11-15
> **.nedberg said:**
> Hi everyone.

As you all may have noticed, development on timekpr has been rather slow lately. Both Savvas/forger and I have had different things happening in our lives. In addition we recently became aware of a Gnome application called Nanny. We both feel that Nanny has a better chance of getting all the features we all wanted to be put into timekpr, and Nanny also has a lot more backing.

Savvas and I have decided that we probably won't do much more coding on timekpr. We both might drop by to fix a bug or two or answer some questions.

Thanks to all of you for your support, kind words and help along the way. It was fun while it lasted, it is time to move one to something different.

Ohh, sad to hear.  I read about the Nanny project a while ago.  I always liked Timekpr, very simple, straight forward and excellent!  Thank you for the time and effort that you all have put into it!

Shane

---

### Post by shane2peru on 2010-11-15
ohh, I just installed nanny, and logged into my kids account, it doesn't seem to log them out after their time limit! :(  I re-installed timekpr.  Nanny looks nice, and I think it will get there, but I was a little disappointed to find it not logging out, or closing session after the time limit.  I couldn't find any information on contacting or documentation for nanny.  If you know where there is current documentation I would love to see it.  Thanks!

Shane

---

### Post by shane2peru on 2011-04-08
I don't think that Nanny is being actively developed.  It hasn't had an update since May of 2010!  That is almost a year with nothing.  I looked on their web page, but nothing, I can't find any support for it either.  It doesn't limit the time as I think I stated in a last post.  With Natty on the horizon, I'm a little concerned about this whole thing.

Shane

---

### Post by .nedberg on 2011-04-08
> **shane2peru said:**
> I don't think that Nanny is being actively developed.  It hasn't had an update since May of 2010!  That is almost a year with nothing.  I looked on their web page, but nothing, I can't find any support for it either.  It doesn't limit the time as I think I stated in a last post.  With Natty on the horizon, I'm a little concerned about this whole thing.

Shane

I'll set up a virtual Natty install and try timekpr. I am copying it to my personal ppa right now. If it works I'll make a copy in the timekpr-maintainers ppa too.

If anybody has time to test, please do so. I am rather busy this weekend so I can't promise anything!

You can find my ppa here: [https://launchpad.net/~nedberg/+archive/ppa]("https://launchpad.net/~nedberg/+archive/ppa")

---

### Post by shane2peru on 2011-04-08
> **.nedberg said:**
> I'll set up a virtual Natty install and try timekpr. I am copying it to my personal ppa right now. If it works I'll make a copy in the timekpr-maintainers ppa too.

If anybody has time to test, please do so. I am rather busy this weekend so I can't promise anything!

You can find my ppa here: [https://launchpad.net/~nedberg/+archive/ppa]("https://launchpad.net/~nedberg/+archive/ppa")

I was planning on upgrading to the Natty next week and would be testing it regularly, perhaps I will test it out on a virtual install before hand.  I'm very glad, that even if improvements are not made it will be kept up. This is the ONLY app for such things on Linux and it gets used every single day on my computer, and has for a few years!  It is absolutely wonderful.  It is one of those things you install, setup, and forget about it, it just runs with no problems.

Shane

---

### Post by shane2peru on 2011-04-08
For your information.  I installed Natty 64bit desktop on a Virtual machine, and added your repo, installed fine, no problems.  I setup a test user, and tested them it kicked them off after 30min alloted time, and wouldn't let them log back on.  I will test outside of the specified time tomorrow.  I'm pleased over all.  

Shane

---

### Post by .nedberg on 2011-04-10
I have now copied timekpr into the Natty series in the timekpr-maintainers PPA. It should be available in a few moments. I have tested everything in a 32bit VM. It works! I have not done excessive testing, so it might break...

---

### Post by sweetleaf on 2011-04-16
Timekpr looks great, so I'm disappointed to learn that you've decided to stop developing it.

I tried Gnome Nanny (on Mint 10 = Ubuntu 10.10), but it doesn't work very well. It will block ports on a schedule, but it won't kick a user out of a login session, nor will it block a user from logging in. It's problematic even as a simple web blocker, because it doesn't have an informative tray icon--so you can waste time troubleshooting what appears to be a broken network connection if you forget that Nanny, with its never-changing icon, might be doing something in the background.

My use-case is self-control, not parental-control, and unfortunately it looks like timekpr isn't set up for this: my (admin) username does not appear as an option in the configuration menu. So that would be my feature request, if you were still developing the software. I might be interested in helping out, if you change your mind. I have little experience, but (like everyone else?) I'd like to learn Python. ;-)

---

### Post by Onesimus on 2011-04-18
> **sweetleaf said:**
> Timekpr looks great, so I'm disappointed to learn that you've decided to stop developing it.

My use-case is self-control, not parental-control, and unfortunately it looks like timekpr isn't set up for this: my (admin) username does not appear as an option in the configuration menu. So that would be my feature request, if you were still developing the software. I might be interested in helping out, if you change your mind. I have little experience, but (like everyone else?) I'd like to learn Python. ;-)

Why not create a second account that is non-adminstrative.  That way you benefit from the functionality of timekpr.  I think it has been designed not to block the admin user, otherwise they may get locked out and unable to get back in.

---

### Post by shane2peru on 2011-04-18
Ok, I clean installed Natty on my laptop (kids machine) and it got some testing today, it worked fine.  I disabled the Unity desktop that comes default with 11.04, and went with the Ubuntu Classic desktop.  Unity changed the way that notifications are set up or something, at any rate, I don't think the notification icon will show up if you use the unity desktop, that is a side note, if someone who wanted to learn python, wanted to dive into that and figure out the desktop notification thing that would be great. :)  If not, we will have to wait until a developer can get a hold of this project and upgrade that.  It is a rock solid app that just runs great.  I have used it for years, and literally don't know what I would do without it.

Shane

---

### Post by hunterkasy on 2011-04-19
this is the first time I looked into parental controls for ubuntu.  I don't understand why it is not included with the distro.  I do think the parental controls should be turned off by default, but it would be nice to have the option to configure a user for content filtering and time and apps filtering and limits.  

I did not read through this whole thread.  but is their a easy gui way of having a content filtering on ubuntu?

---

### Post by shane2peru on 2011-04-20
> **hunterkasy said:**
> this is the first time I looked into parental controls for ubuntu.  I don't understand why it is not included with the distro.  I do think the parental controls should be turned off by default, but it would be nice to have the option to configure a user for content filtering and time and apps filtering and limits.  

I did not read through this whole thread.  but is their a easy gui way of having a content filtering on ubuntu?

You can have a look here:  [http://ubuntuforums.org/showthread.php?t=843510](http://ubuntuforums.org/showthread.php?t=843510)

Shane

---

### Post by sweetleaf on 2011-04-21
> **Onesimus said:**
> [QUOTE=sweetleaf;10685621]My use-case is self-control, not parental-control, and unfortunately it looks like timekpr isn't set up for this
Why not create a second account that is non-adminstrative.  That way you benefit from the functionality of timekpr.[/QUOTE]

Hmm. It's a rare day when I don't use sudo for something. How much of a hassle is it for a non-admin user to accomplish admin tasks, if he knows an admin password? Is it just a matter of su'ing to the admin account before invoking sudo?

> I think it has been designed not to block the admin user, otherwise they may get locked out and unable to get back in.

It's an odd game, trying to use the computer to enforce self-control. Workrave has a "daily limit" control that could be helpful, but in practice I find it's too easy to disable or kill it. I imagine I might do the same with timekpr, as long as I could kill it using an admin password. I want the best of both worlds: total control over the processes running on my system, *except* for one timekpr/workrave/nanny type of process that locks up the system during certain hours or after too much time. There may not be any easy and safe way to achieve this.

---

### Post by WarrenL on 2011-07-13
After some searching I've just come across timekeepr, and it would seem on the face of it to meet my needs, that is, restricting my son's daily time logged in at the computer, and limiting him to certain hours.

However, whilst setting it up, I've discovered that it doesn't log his account out. If I have Ubuntu logged in under his account, the time runs out but everything just keeps trucking along until I log out the account myself, at which point it is locked.

Have I missed something out? I thought the whole point was to kick the user off when his/her time was up!

---

### Post by shane2peru on 2011-07-13
Actually it should indeed log him/her out.  That is the whole point of this application.  I have used it for years and it is a great application. Please go over the settings again as it may be something was over looked when you setup the account.  What desktop are you on?  I switched over to Kubuntu and it works with KDE.  I'm not sure about the new Unity desktop as I never did like it.  However with Gnome it worked for years, perhaps with the newer Gnome it has problems?  Not sure.

Shane

---

### Post by WarrenL on 2011-07-13
Hiya Shane,

I'm using it on Gnome (I've tried really hard, but I can't take to the Unity interface). My son is set up as a plain old garden variety desktop user. Nothing complicated. And to be honest there aren't many settings to fiddle with! I limited him to 1 hour every day, between 1500 and 1700 every day; there didn't seem to be anything else to do. The Timekeepr tray notifier tells him there's so many minutes/seconds left, and then nothing happens! But if I log out or switch users, Tom's account is then locked and I can't reaccess it.

I hope this isn't a bug that shows up in Natty. Timekeepr was the answer to all my problems!

Regards,
Warren

---

### Post by .nedberg on 2011-07-15
> **WarrenL said:**
> Hiya Shane,

I'm using it on Gnome (I've tried really hard, but I can't take to the Unity interface). My son is set up as a plain old garden variety desktop user. Nothing complicated. And to be honest there aren't many settings to fiddle with! I limited him to 1 hour every day, between 1500 and 1700 every day; there didn't seem to be anything else to do. The Timekeepr tray notifier tells him there's so many minutes/seconds left, and then nothing happens! But if I log out or switch users, Tom's account is then locked and I can't reaccess it.

I hope this isn't a bug that shows up in Natty. Timekeepr was the answer to all my problems!

Regards,
Warren

It might take up to 2 minutes before he is kicked! (After time has run out!)

---

### Post by WarrenL on 2011-07-15
Aha! I'll give it another go and report back.

Thanks for that.

---

### Post by WarrenL on 2011-07-16
And you were right!

I set up Timekeepr, switched to Tom, then left the computer alone for a while. I came back to find it had logged out Tom's account. I was simply expecting it to work straight away, but as you said, it takes a couple of minutes.

Thanks .nedberg!

Now, I've had a play with Nanny but I reckon Timekeepr is WAY better. It's sad to hear that you are no longer developing it.

---

### Post by .nedberg on 2011-07-24
> **WarrenL said:**
> And you were right!

I set up Timekeepr, switched to Tom, then left the computer alone for a while. I came back to find it had logged out Tom's account. I was simply expecting it to work straight away, but as you said, it takes a couple of minutes.

Thanks .nedberg!

Now, I've had a play with Nanny but I reckon Timekeepr is WAY better. It's sad to hear that you are no longer developing it.

Timekpr is designed to log off any restricted user after a set time. The timekpr-client notifies the user how much time is left. But because of a possible difference in the reported time and the real time used, the user is given an extra two minutes.

Yes, timekpr is no longer developed. I don't think I will take it up later. But it is open source so if someone wants to take over, then please do!

---

### Post by nothingspecial on 2011-07-24
I'm sad too......

......my kids hate that evil demon timekpr

:evil:

---

### Post by imaca on 2011-09-13
A big thanks to the developers, having been looking for something to do this for ages. Perfect.

---

### Post by foxy123 on 2011-10-24
Hi, any chance to update it for Oneiric?

---

### Post by CharlesA on 2011-10-24
I don't think it's under development any more.

Nevermind - I see that there was a PPA uploaded 4 hours ago.

[https://launchpad.net/~timekpr-maintainers/+archive/ppa](https://launchpad.net/~timekpr-maintainers/+archive/ppa)

See [here]("https://answers.launchpad.net/timekpr/+question/175814") about 11.10. :)

---

### Post by .nedberg on 2011-10-25
> **CharlesA said:**
> I don't think it's under development any more.


It isn't! I just copied the binary to the new PPA. I have not tested timekpr with 11.10, but got a mail that said it worked...

---

### Post by nothingspecial on 2011-10-25
I'll test it later.

After a few days, I'll let you know.

My kids will be so pleased, :-\"

---

### Post by foxy123 on 2011-10-25
> **.nedberg said:**
> It isn't! I just copied the binary to the new PPA. I have not tested timekpr with 11.10, but got a mail that said it worked...

According to [this]("http://askubuntu.com/questions/68918/how-do-i-restrict-my-kids-computing-time") Natty binaries do not work on Oneiric.

---

### Post by nothingspecial on 2011-10-25
It is running.

It requires that you use gdm rather than lightdm

Obviously I can not say whether it works until either the kids use their alloted time or it kicks them off when it should. And then lets them back in.

---

### Post by foxy123 on 2011-10-25
> **nothingspecial said:**
> It is running.

It requires that you use gdm rather than lightdm

Obviously I can not say whether it works until either the kids use their alloted time or it kicks them off when it should. And then lets them back in.

is there any way to use it with lightdm?

---

### Post by nothingspecial on 2011-11-04
I can happily confirm that timekpr is frustrating my kids as it always has.

Every aspect is working with oneiric.

:)

---

### Post by foxy123 on 2011-11-04
> **nothingspecial said:**
> I can happily confirm that timekpr is frustrating my kids as it always has.

Every aspect is working with oneiric.

:)

Unfortunately notifications do not work, which frustrates my daughter.

---

### Post by hawstom on 2011-11-22
This is how I got timekpr to work in Ubuntu 11.10 Oneiric:

(Note that the timekpr icon and notification do not work, which is frustrating for the kids, but the accounts do expire as required.  To get the full timekpr functionality for the kids, you need to switch to gnome desktop.  Maybe a kind user can step us through doing that.)

1.  Install the gdm login screen

Open the terminal and enter

```
sudo apt-get install gdm
```

2.  Activate the gdm login screen

Select gdm from the ensuing menu that appears after gdm gets installed.

If you already have gdm installed, use the following terminal command to set it current:

```
sudo dpkg-reconfigure gdm
```

3.  Add the timkpr repository to your sources

Now if you don't have timekpr installed yet, open the terminal again and add the timekpr repository to your software sources:

```
sudo add-apt-repository ppa:timekpr-maintainers/ppa
sudo apt-get-update

```

4.  Install timekpr

```
sudo apt-get install timekpr

```

Or install timekpr from Software Sources

5.  Run timekpr from an administrator account

Either search for timekpr in the Unity search (bleahh!) or start timekpr from the terminal:

```
sudo timekpr
```

6.  Test timekpr

You must have a non-administrator account set up for your children.  timekpr will let you set time limits for non-administrator accounts.  Set an account to have 1 minute of time.  Apply, exit, log out, and log in to the child's account.  Within 3 minutes the account should be automatically logged off.  If you want the child to have a timekpr icon and notifications, you will need to switch your Ubuntu desktop to Gnome (maybe a kind user can provide a step-through of how to install and switch to gnome for the children).

---

