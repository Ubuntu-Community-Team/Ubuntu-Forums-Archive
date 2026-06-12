---
title: "Accessing Evolution from the command-line"
date: 2008-07-24
forum: General Help
---

### Post by DontThinkSo on 2008-07-24
I've been working on a script that will wake me up in the morning with some announcements. I'm using festival for tts and weather-utils to obtain a forecast (if you're interested). So far, it works as expected - thing is, I'd like to be able to have it pull my tasks/appointments from my evolution calendar and dictate them back to me (as a sort of reminder at the beginning of the day). I would also like to check for any new emails, and alert me if new ones have arrived.

Is there a way to access this information from the command line, so that it can be fed to festival? If so, how?

Oh, and for those interested, here's my script so far:

```
#!/bin/bash

weatherdata=`weather -c Santa\ Rosa -s CA -nvf | grep -e \\\\.\`date +%A\`\\\\.`

if  ((`date +%H` < 12)) 
then
	greeting="Good morning."
elif  ((`date +%H` < 17)) 
then
	greeting="Good afternoon."
else
	greeting="Good evening."
fi

echo "$greeting The time is currently `date +%l:%M` and `date +%S` seconds, on `date +%A%t%B%t%d%t%Y`" | aoss festival --tts

if [[ $weatherdata != "" ]]; then

	if [[ `echo $weatherdata | grep Sunny` != "" ]]; then
		inserttext=" sunny skies, and"
	fi
	
	echo "Expect$inserttext a high of `echo $weatherdata | awk {'print $4'} -` degrees fahrenheit, with `echo $weatherdata | awk {'print $5, $6, $7, $8'} -` " | aoss festival --tts
fi
```

If you want to test it, you may want to replace Santa Rosa, CA with your city/state. :)

Also, a related question: what does weather return when it's not expecting sunny skies? I'm guessing, "cloudy, rain, snow", but I'm not sure - if anyone knows, help would be appreciated.

<Edit> If you hope to test this, you'll need some dependencies; namely weather-util, festival (and a voice package for it; do an aptitude search festvox or search online for some better voices than the ones in the repos), and alsa-oss.

---

### Post by DontThinkSo on 2008-07-24
Well, after some poking around, I found the file that Evolution uses to store its calendar data, in ~/.evolution/calendar/local/system/calendar.ics. Here's a sample:

> BEGIN:VEVENT
UID:20080724T225854Z-6120-1000-1-2@keegan-desktop
DTSTAMP:20080724T225854Z
DTSTART;TZID=/softwarestudio.org/Tzfile/America/Los_Angeles:
 20080724T160000
DTEND;TZID=/softwarestudio.org/Tzfile/America/Los_Angeles:20080724T163000
TRANSP:OPAQUE
SEQUENCE:3
SUMMARY:Test Appointment
LOCATION:Keegan's House
CLASS:PUBLIC
CREATED:20080724T225931
LAST-MODIFIED:20080724T232438
END:VEVENT


Any ideas as to how I should parse this from within my script? It would need to be fast, even given a large number of events (I'm pretty sure they'll simply build up as I add them). Or, if anyone has any other suggestions, help is still appreciated...

---

### Post by DontThinkSo on 2008-07-24
Well, I sorta found workarounds for both of my problems.

I found a python script elsewhere on the forums that checks gmail for the number of new messages, and uses it for conky. I altered that script to suit my needs:

```
import os
import string
import sys
import time

#Enter your username and password below within double quotes
# eg. username="username" and password="password"

filename="/home/keegan/vox/emails"
username="******"
password="******"

emails=0


com="wget -O - https://"+username+":"+password+"@mail.google.com/mail/feed/atom --no-check-certificate"
temp=os.popen(com)
msg=temp.read()
index=string.find(msg,"<fullcount>")
index2=string.find(msg,"</fullcount>")
fc=int(msg[index+11:index2])

file = open(filename, "w")

if (int(fc)==0):
   file.write("You have no new e-mails.")
elif int(fc)==1:
   file.write("You have 1 new e-mail.")
else:
   file.write("You have "+str(fc)+" new e-mails.")
file.close
```

This creates a file in /home/keegan/vox that contains text that can will be read by festival.

I never found a good way to make it read tasks out of evolution, so I found my own method; it simply reads text out of a file in $HOME/Memos, with a file that represents that day, in the format of yyyymmdd. Here's the final script:

```
#!/bin/bash

curdate=`date +%Y%m%d`

python $HOME/vox/checkgmail.py


#Get the weather
weatherdata=`weather -c Santa\ Rosa -s CA -nvf | grep -e \\\\.\`date +%A\`\\\\.`

#Morning? Afternoon? Evening?
if  ((`date +%H` < 12)) 
then
	greeting="Good morning."
elif  ((`date +%H` < 17)) 
then
	greeting="Good afternoon."
else
	greeting="Good evening."
fi

#Time and date
echo "$greeting The time is currently `date +%l:%M` and `date +%S` seconds, on `date +%A%t%B%t%d%t%Y`" | aoss festival --tts

#Weather
if [[ $weatherdata != "" ]]; then

	if [[ `echo $weatherdata | grep Sunny` != "" ]]; then
		inserttext=" sunny skies, and"
	elif [[ `echo $weatherdata | grep Cloudy` != "" ]]; then
		inserttext=" cloudy skies, and"
	elif [[ `echo $weatherdata | grep Rain` != "" ]]; then
		inserttext=" rain, with"
	fi
	
	echo "Expect$inserttext a high of `echo $weatherdata | awk {'print $4'} -` degrees fahrenheit, with `echo $weatherdata | awk {'print $5, $6, $7, $8'} -` " | aoss festival --tts
fi

#How many emails do we have?

aoss festival --tts $HOME/vox/emails

#Read memos, if they exist.

if [ -e $HOME/Memos/$curdate ]; then
	aoss festival --tts $HOME/Memos/$curdate
else
	echo "You have no appointments or reminders for today." | aoss festival --tts
fi
```

---

