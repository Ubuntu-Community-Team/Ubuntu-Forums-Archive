---
title: "Dial-up script that automates things for you"
date: 2009-12-06
forum: Hardware
---

### Post by Trespasser on 2009-12-06
****First off I'd like to say I'm a beginner at bash scripting so be kind when you see some stupid lines of script that could have easily been done with one*****

Hi,
This is my completed scripts for people who use dial-up under Gnome (Karmic for me) as their means of connecting to the internet. The advantage of these scripts are they allow you to click on Desktop links you use most frequently which then activate wvdial, waits for a connection to be established, then calls your preferred browser (firefox in my case). Also, once you close out your browser the script offers to terminate the connection (Yes, just like Internet Explorer). You can choose "Yes" if you want to disconnect or "No" if you wish to click another Desktop link. Here's my first script, which I called myscript.sh, which basically carries out all the functions...

```

#!/bin/bash
# needs libnotify-bin to be installed (about 65 KBs)

# Function 1

function chk_if_online
{
if [ ! -f /var/run/ppp0.pid ]; then # if no ppp0.pid exists
until [ -e /var/run/ppp0.pid ]; # loop until value exists
do
sleep 0.1
done
notify-send "Connection established..."
Start_browser # first time connect after bootup
else # not first time connect after bootup
Oldpid="$(cat /var/run/ppp0.pid)" # Read current ppp* pid
Newpid=$Oldpid # Set Newpid = Oldpid

until [[ $Oldpid != $Newpid ]]; # Loop until condition met
do
Newpid="$(cat /var/run/ppp0.pid)" # Read current ppp* pid
done
notify-send "Connection established..."
Start_browser
fi
}

# Function 2

function Start_browser # start browser....
{
#notify-send "10 minute online time limit in effect"
$browser $url
until [ -e $(pidof $browser) ]; # give browser enough time to open
do
sleep 0.1
done
while ps ax | grep -v grep | grep $browser > /dev/null ; do # check if browser is running
sleep 0.5
done # when browser no longer running...ask to disconnect
#timer
zenity --question --text="Do you wish to disconnect?" --ok-label=Yes --cancel-label=No
if [ $? = 0 ]; then # FYI...(0)=Yes, (1)=No
disconnect
fi
if [ -e $(pidof $browser) ]; then
killall $browser
fi
}

# Function 3

function timer
{
FINISH_TIME=`date +%s`
SECONDS=$((FINISH_TIME - START_TIME))
if [ "$SECONDS" -gt "$TIME_LIMIT" ]; then
notify-send "Online time limit reached..." \ "Disconnecting"
disconnect
fi
}

# Function 4

function disconnect
{
killall wvdial >/dev/null # kill wvdial
notify-send "Disconnecting..."
kill $$
exit 0
}

# Main execution section

browser="firefox"
# Replace firefox with opera or epiphany-browser or chromium-browser or arora, or etc.
# Needs to be process name (open browser then look in System Monitor).
# Also, make sure your preferred browser is list as default in Preferred Applications

#TIME_LIMIT=600 # 10 minute time limit
#START_TIME=`date +%s`
link=$@

# Desktop links
if [ $link -eq 1 ]; then
url="http://my.yahoo.com/index.html"
fi
if [ $link -eq 2 ]; then
url="http://www.ebay.com/"
fi
if [ $link -eq 3 ]; then
url="http://www.facebook.com/home.php?"
fi
if [ $link -eq 4 ] ; then
url="http://www.ubuntuforums.org/"
fi
if [ $link -eq 5 ] ; then
url="http://www.google.com/ig"
fi
if [ $link -eq 6 ] ; then
url="http://mail.google.com/mail/#inbox"
fi
# add more url links here if you wish
# end of Desktop links

ps -ef | grep -v grep | grep wvdial > /dev/null

if [ $? = 1 ]; then # wvdial is not running...(0)=Yes, (1)=No
nohup wvdial 1>/dev/null 2>/dev/null & # dial...
chk_if_online
else # wvdial is running...start new link...
Start_browser
fi
```

To make Desktop links that call this script...right click in an open space on Desktop and choose Create Launcher...put in a name for your link (Facebook - Home, for example)...then in the Command line put...(the .scripts part is a hidden folder in my Home folder)...

bash /home/user-name/.scripts/myscript.sh 3

...the number at the end corresponds to the url link in the above script. Choose an icon for your link and click OK. You need to make a Desktop link for each url you wish to access from Desktop. Obviously, you need to change my url links to those you prefer.

As you can see, I put in a timer function at one point but decided to go with a cron job script instead. If you do not wish to use my cron job script but would like to use the timer then remove the "#" symbol in front of the following lines in the script...

#timer
#TIME_LIMIT=600 (600 seconds or 10 minutes...set to whatever you wish)
#START_TIME=`date +%s`
#notify-send "10 minute online time limit in effect"

The following is my cron job script ( I named it wvdial-browser-check.sh)...

```

#!/bin/bash
# cron job should look like this " */5 * * * * ~/.scripts/wvdial-browser-check.sh"
# Get dbus info
nautilus_pid=$(pgrep -u $LOGNAME -n nautilus)
eval $(tr '\0' '\n' < /proc/$nautilus_pid/environ | grep '^DBUS_SESSION_BUS_ADDRESS=')
export DBUS_SESSION_BUS_ADDRESS

browser="firefox"
# Replace firefox with opera or epiphany-browser or chromium-browser or arora, or etc
# needs to be process name (open browser then look in System Monitor).

wvdialpid=$(pidof wvdial)
browserpid=$(pidof $browser)
if [ -z $wvdialpid ]; then # checks if wvdial is running
echo ""
else
if [ -z $browserpid ]; then # if wvdial is running but browser is not, then...
notify-send "Disconnecting..."
killall wvdial
fi
fi
kill $$
exit
```

The command to use the cron job is in the script above. It checks every 5 minutes to see whether wvdial is running or not. If it is, but your browser isn't, then it disconnects for you. If wvdial is running, as well as your browser, then it doesn't disconnect.

I saved both scripts (myscript.sh and wvdial-browser-check.sh) in a hidden folder (.scripts) in my Home folder.

One last thing. You need to install wvdial (and it's dependencies) and libnotify-bin for some really nice notifications like "Connection established...", "Disconnecting...", "10 minute online time limit in effect", or "Online time limit reached..." \ "Disconnecting". Each notification will display for 5 seconds. Also, to create a cron job open Terminal and enter "crontab -e". Copy and paste your cron job command, then Ctrl+Alt+x, Y (yes) to save, then Enter.

I'm on DSL but my Dad is still forced to use dial-up so I made these scripts primarily so he  could use Linux. He has poor eyesight and his hands shake so making connecting and disconnecting very easy for him was what I wanted. Hope they help someone else.

Later...

---

### Post by Trespasser on 2009-12-10
Forget wvdial! Use pon/poff...plus you'll save about 3.5 MBs of disk space.

I've changed my script to conform to my switch to pon/poff. There's some differences between pon/poff and wvdial. Under wvdial when you boot up your computer /var/run/ppp0.pid doesn't exist (same with pon/poff) but on your subsequent dialouts ppp0.pid exists but the value changes...thus a different section in my last script to deal with that. Under pppd, /var/run/ppp0.pid is deleted each time you close your dialup connection. This fact simplified my new script a little bit. Here's my new script...

```

#!/bin/bash
# Needs libnotify-bin to be installed for notification messages (about 65 KBs)

# Function 1

function chk_if_online
{
until [ -e /var/run/ppp0.pid ]; do # loop until ppp0 pid exists
sleep 0.5
done
notify-send "Connection established..."
Start_browser
}

# Function 2

function Start_browser # start browser....
{
$browser $url &> /dev/null
until [ -e $(pidof $browser) ]; # give browser enough time to open
do
sleep 0.1
done
BrowserCheck=`ps ax | grep -v grep | grep $browser` # check if browser is running
if [ ! "$BrowserCheck" ]; then # if not, then ask to disconnect
zenity --question --text="Do you wish to disconnect?" --ok-label=Yes --cancel-label=No
if [ $? = 0 ]; then # FYI...(0)=Yes, (1)=No
disconnect
fi
fi
exit
}

# Function 3

function disconnect
{
poff
notify-send "Disconnecting..."
kill $$
exit
}

# Main execution section

browser="firefox"
# Replace firefox with opera, epiphany-browser, chromium-browser, arora, or etc.
# Needs to be process name (open browser then look in System Monitor)
# Also, make sure your browser of choice is listed as default in Preferred Applications

url="$@"
# make Desktop launchers with this format...bash /home/user-name/myscript.sh "http://mail.google.com/mail/#inbox"

killall $browser # make sure another instance of browser is not running

ps -ef | grep -v grep | grep pppd > /dev/null # check if pppd is running

if [ $? = 1 ]; then # if no, then...(0)=Yes, (1)=No
pon your-ISP's-name # dial...
chk_if_online
else # if yes, then start new Desktop link...
Start_browser
fi
```

Here's the script I call with a cron job to insure the connection is monitored to prevent forgetting to disconnect....

```

#!/bin/bash
# cron job should look something like this... */10 * * * * ~/.scripts/pppd-browser-check.sh
# Get dbus info...(needed for libnotify-bin)...
nautilus_pid=$(pgrep -u $LOGNAME -n nautilus)
eval $(tr '\0' '\n' < /proc/$nautilus_pid/environ | grep '^DBUS_SESSION_BUS_ADDRESS=')
export DBUS_SESSION_BUS_ADDRESS

browser="firefox"
# Replace firefox with opera, epiphany-browser, chromium-browser, arora, or etc.
# Needs to be process name (open browser then look in System Monitor)
# Also, make sure your browser of choice is listed as default in Preferred Applications

pppdpid=$(pidof pppd)
browserpid=$(pidof $browser)
if [ -z $pppdpid ]; then # pppd not running
echo ""
else
if [ -z $browserpid ]; then # if pppd is running but browser is not (-z=null -n=not null)
notify-send "Disconnecting..."
poff
fi
fi
kill $$
exit
```

When creating Desktop launchers use this format....

bash /home/user-name/.scripts/myscript.sh "http://mail.google.com/mail/#inbox"

Just drop the links you want to use between the quotation marks. Hope someone can use it. It makes dialup under Linux a whole lot easier.

Later...

---

### Post by Trespasser on 2009-12-16
I wanted to put this script out on the internet in an attempt to help other dial-up users (I'm on DSL but my Dad is on dial-up...yes, I wrote this for him). It really does make using dial-up a whole lot easier. I hope this helps someone

If you had previously been using wvdial in your dial-up setup you can uninstall it if you wish because you really don't need it with pppd.

To avoid trouble with permissions do..
sudo adduser user-name dip

Configure pppd with sudo pppconfig (during this process you will need to know the port your modem is configured to dialout on...in my case it was SHSF0).
 
You'll need to dialout at least once as root...
sudo pon ISP-Name

but after that you can dialout as a regular user...
pon ISP-Name

This version is much simpler than previous versions and works great (needs libnotify-bin installed for the cool notifications)...

```

#!/bin/bash

if [ ! -d ~/.scripts/counter ]; then # Does config directory exist?
mkdir ~/.scripts/counter
touch ~/.scripts/counter/end-time
fi

START_TIME=`date +%s`
echo "$START_TIME" > ~/.scripts/counter/end-time

browser="firefox" # Replace firefox with opera, epiphany-browser, arora, etc.

url="$@" # Desktop launcher should look something like this...
# bash /home/user-name/myscript.sh "http://www.google.com/ig", for example

ps -ef | grep -v grep | grep pppd > /dev/null # check if pppd is running
if [ $? = 1 ]; then # if not connected, then... (1)=No
pon Your-ISP # dial...
until [ -e /var/run/ppp0.pid ]; do # loop until ppp0 pid exists
sleep 1
done
sleep 2 # extra time for connection to establish
notify-send "Connection established..."
fi

$browser $url &> /dev/null
BrowserCheck=`ps ax | grep -v grep | grep $browser` # check if browser is running
if [ ! "$BrowserCheck" ]; then # if not, then ask to disconnect
zenity --question --text="Do you wish to disconnect?" --ok-label=Yes --cancel-label=No
if [ $? = 0 ]; then # FYI...(0)=Yes, (1)=No
poff
notify-send "Disconnecting..."
kill $$
fi
fi
END_TIME=`date +%s`
echo "$END_TIME" > ~/.scripts/counter/end-time
killall $browser # make sure another instance of browser is not running
exit
```

Here's the script that monitors the connection to check whether the browser is still open at certain intervals. Not really needed for most folks. It's mainly aimed at older folks (like my Dad) or real young people who might forget to disconnect...

```

#!/bin/bash
# cron job should look something like this... */10 * * * * ~/.scripts/pppd-browser-check.sh

browser="firefox" # Replace firefox with opera, epiphany-browser, arora, midori, etc.

nautilus_pid=$(pgrep -u $LOGNAME -n nautilus)
eval $(tr '\0' '\n' < /proc/$nautilus_pid/environ | grep '^DBUS_SESSION_BUS_ADDRESS=')
export DBUS_SESSION_BUS_ADDRESS

TIME_LIMIT=120 # <in seconds...time limit on open connection with browser closed
CHECK_TIME=`date +%s`
CLOSE_TIME="$(cat ~/.scripts/counter/end-time)"
SECONDS=$((CHECK_TIME - CLOSE_TIME))

pppdpid=$(pidof pppd)
if [ -z $pppdpid ]; then # pppd is not running
echo "$CHECK_TIME" > ~/.scripts/counter/end-time
else # pppd is running
if [ ! $(pidof $browser) ]; then # then, if pppd is running but browser is not
if [ "$SECONDS" -gt "$TIME_LIMIT" ]; then
poff
notify-send "Disconnecting..."
fi
fi
fi
kill $$
exit
```

These scripts work great for my Dad and me. If you have any questions please ask away.

I should have added that for a neat applet that displays your connection speed install netspeed (in repos). It's also useful for showing when a connection has been successfully established.

---

### Post by Trespasser on 2010-01-13
This pon dialup script waits for your primary and secondary DNS to show up in /var/log/messages before opening your browser. Much simpler and more dependable. I also suggest that you open /etc/ppp/options with your favorite text editor (as root) and enable persist (remove the "#" from in front of the entry) as well as maxfail (default is 10 if not enabled).You could also enable holdoff (recommended is 10 seconds but I put mine at 5). Persist starts the redial process if a connection is dropped. Hope this helps someone. 

```

#!/bin/bash

if [ ! -d ~/.scripts/counter ]; then  # Does config directory exist?
  mkdir ~/.scripts/counter
  touch ~/.scripts/counter/time-keeper
fi

START_TIME=`date +%s`
echo "$START_TIME" > ~/.scripts/counter/time-keeper

browser="firefox"   # Replace firefox with opera, epiphany-browser, arora, etc.
ISP=""   # Put your ISP name that you entered in pppconfig between the quotation marks
url="$@" # Desktop launcher should look something like this...
         # bash /home/user-name/myscript.sh "http://www.google.com/ig", for example

ps -ef | grep -v grep | grep pppd > /dev/null  # check if pppd is running
if [ $? = 1 ]; then                    # if not connected, then... (1)=No
  notify-send "Dialing..."
  pon $ISP                           # dial...
  while :; do
    tail -n 2 /var/log/messages | grep DNS  # Waits for primary and secondary DNS 
    if [ $? = 0 ]; then                     # to show up before opening browser
      break
    fi
  done
  notify-send "Connection established..."
fi

$browser $url &> /dev/null
BrowserCheck=`ps ax | grep -v grep | grep $browser` # check if browser is running
if [ ! "$BrowserCheck" ]; then     # if not, then ask to disconnect
  zenity --question --text="Do you wish to disconnect?        " --ok-label=Yes --cancel-label=No
    if [ $? = 0 ]; then            # (0)=Yes
       poff
       notify-send "Disconnecting..."
       kill $$
    fi
fi
END_TIME=`date +%s`
echo "$END_TIME" > ~/.scripts/counter/time-keeper
killall $browser    # make sure another instance of browser is not running
exit
```

---

