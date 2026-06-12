---
title: "Disabling touchpad when mouse plugged in"
date: 2014-03-22
forum: Hardware
---

### Post by frytek on 2014-03-22
Hi there, 
I'd like to share a working solution. 

I have read about it and I found some solutions based on udev rules but some people complain that this doesn't work for them. It seems it is quite difficult to implement for inexperienced users. So I thought about a script. A script which will be run every 10 seconds, checking if a mouse is plugged in. It it is, the touchpad will be automatically disabled. 

Here's the script: 

```

#!/bin/sh
# Created by andja in 2015
# this should run from udev rule in a perfect world
# make the following file /etc/udev/rules.d/01-touchpad.rules
# with the following content; replace username and script 
# location where needed: 
#SUBSYSTEM=="input", KERNEL=="mouse[0-9]*", ACTION=="add", ENV{DISPLAY}=":0", ENV{XAUTHORITY}="/home/username/.Xauthority", RUN+="/usr/local/bin/touchpad"
#SUBSYSTEM=="input", KERNEL=="mouse[0-9]*", ACTION=="remove", ENV{DISPLAY}=":0", ENV{XAUTHORITY}="/home/username/.Xauthority", RUN+="/usr/local/bin/touchpad"

#if it doesn't work, we'll do it in a dirty way, running from cron 
#every 10 seconds. again, adjust the script location. 
#* * * * *           /home/username/bin/touchpad  > /dev/null 2>&1
#* * * * * sleep 10; /home/username/bin/touchpad  > /dev/null 2>&1
#* * * * * sleep 20; /home/username/bin/touchpad  > /dev/null 2>&1
#* * * * * sleep 30; /home/username/bin/touchpad  > /dev/null 2>&1
#* * * * * sleep 40; /home/username/bin/touchpad  > /dev/null 2>&1
#* * * * * sleep 50; /home/username/bin/touchpad  > /dev/null 2>&1

#checking touchpad status
export status=$(synclient -l | grep TouchpadOff | awk '{print $3}')

#not sure what it has to do with display. copied from internet. 
#I guess that's for cron. 
export DISPLAY=:0

# grep below looks for ouse to match M or m, or for usb ids 
# wchich are needed if mouse is not reported as mouse but as 
# "Somecompany Pointer" or "Laser Optical" and so on.
# check it with lsusb and replace vendor symbols 0000:0000 
# with yours. alternatives are used as I have more than one
# mouse around. 

if [ "`/usr/bin/lsusb | /bin/grep -c 'ouse\|24ae:2000\|0000:0538'`" -ge 1 ]
#mouse present
   then 
#checking touchpad status
export status=$(synclient -l | grep TouchpadOff | awk '{print $3}')
#let's see if touchpad not off already, off = 1
      	if [ $status -ne 1 ] 
#if so, let's turn it off
		then 
        	/usr/bin/synclient TouchpadOff=1 
			notify-send -t 1000 "USB mouse plugged" "Your touchpad is now turned OFF"
		fi
  
else 
#mouse not present
#checking touchpad status
export status=$(synclient -l | grep TouchpadOff | awk '{print $3}')
#let's see if touchpad is already on, off = 0 
   		if [ $status -ne 0 ]
#if so, let's turn it on
		then 

		/usr/bin/synclient TouchpadOff=0 
   		notify-send -t 1000  "No USB mouse found" "Your touchpad is set to ON"
		fi		
fi 
   

```

As you can see, the script checks if there's a mouse device reported by lsusb. I chose only "ouse" because it might happen that some mouses are reported with or without capital M. I don't know if every mouse is reported as "Mouse" - if you're unsure, just issue the lsusb command with and without the mouse connected and compare the results. If necessary, choose a few letters long string from the mouse line and insert it into the script instead of "ouse". Or use vendor's ID like in the script. As the comment says, alternative IDs can be used. 

Save the script file, make chmod +x on it and check if it works while called manually. 


Now, if it works, we are going to add it to our cron. The problem is that cron can run scripts only once a minute while we want the script to react within 10 seconds after the mouse is plugged in or removed. The quick and dirty solution (as dirty as the entire project; I told you already that the proper way to do the above is to use udev rules - see coments in the script) is to start the script from cron with delays, using sleep. 

Run crontab -e and add the following lines (if you end up with vi, hit "i" first)
```
* * * * *           /path/to/your/touchpad/script > /dev/null 2>&1
* * * * * sleep 10; /path/to/your/touchpad/script > /dev/null 2>&1
* * * * * sleep 20; /path/to/your/touchpad/script > /dev/null 2>&1
* * * * * sleep 30; /path/to/your/touchpad/script > /dev/null 2>&1
* * * * * sleep 40; /path/to/your/touchpad/script > /dev/null 2>&1
* * * * * sleep 50; /path/to/your/touchpad/script > /dev/null 2>&1

``` 

replacing the path, accordingly, and making sure the last line is followed by single Enter. Save the file and you are done. (If you are in vi, hit Esc and type :wq). You should end with a script instance checking if the mouse is plugged in every 5 seconds and enabling / disabling your touchpad. 

Enjoy.

---

### Post by robsol on 2014-04-27
Sounds great but the script doesn't work for me.   Because I use tcsh?   /usr/bin/lsusb indeed shows "Mouse" 
and   /usr/bin/synclient TouchpadOff=1 works.  Do I need different test syntax?  Rob

OOPS - Forget the above, it works.  Don't know why not before.  Don't know how to delete the above.  Thanks anyhow!  Rob

---

