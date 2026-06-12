---
title: "Ubuntu, Airsnort, and ipw2200?"
date: 2005-06-21
forum: Hardware &amp; Laptops
---

### Post by dezgot on 2005-06-21
I would like to use airsnort, and im using the version that is available through Synaptic, but I have no clue what I drivers I have to be running or what the "Network Settings" in the System menu should be set to.  I have an old (not Sonoma) centrino laptop with the ipw2200 wireless card that seems to work with whatever drivers Ubuntu puton it for connecting to networks without encryption, but not with airsnort.

I fiddled hopelessly with the wlan-ng tools, didn't get anything to happen in airsnort.

Is there a simple guide to getting centrino to work with airsnort in Ubuntu?  (or could someone help me?   :grin: )   

Thanks for any help, I'm looking to replace netstumbler with airsnort.

---

### Post by circussideshow on 2005-06-21
i also have the ipw2200 (cl56), and i was never able to get kismet OR airsnort to work with it.  kismet flat out says it doesnt work with the 2200, but im not sure about airsnort support... couldn't find anything on their site either.  for right now, i've just been using iwlist (it works better for me than netstumbler, i don't really need a pretty graph).  sorry i'm not much help, i just tried to get airsnort to work for like 2 days and gave up. :neutral:

---

### Post by luca_linux on 2005-06-22
Have you tried to update your ipw2200 driver to the latest version available (1.0.4)? The driver coming with Ubuntu is very old.
Here's a HowTo: [http://ubuntuforums.org/showthread.php?t=26623](http://ubuntuforums.org/showthread.php?t=26623)

---

### Post by dezgot on 2005-06-23
It's possible that airsnort might work with just new drivers?  I dont need to set up wlan-ng or anything?  I'll try it when im somewhere with better than dial up!

---

### Post by luca_linux on 2005-06-23
Yeah, I think it's really possible 'cause the version included in Ubuntu is 0.19, while the latest available is 1.0,4.

---

### Post by dezgot on 2005-06-26
Actually, after a little research, I found that the intel card doesn't support a required mode for airsnort (at least not in windows, i don't see how a hardware mode would be any more available in linux), so there will be no support for it, ever.

To get airsnort working, I had to use an old external  card (from another laptop i have), which is not gonna cut it because its range is absolutely horrible.

---

### Post by sinbad on 2005-07-05
Try this. If you have never used Kismet, it is definitely worth a look. I used it for a couple years with great success.
I haven't had the time to do it yet but it looks like the answer for Kismet anyhow....

[http://zioproto.serveftp.com/howto/ipw2200_kismet_howto.txt](http://zioproto.serveftp.com/howto/ipw2200_kismet_howto.txt)
(found here: [http://www.kismetwireless.net/Forum/General/Search/?SearchString=ipw2200&SearchType=Body+%2B+Subject](http://www.kismetwireless.net/Forum/General/Search/?SearchString=ipw2200&SearchType=Body+%2B+Subject) )


According to this, Airsnort will work when used in conjunction with Kismet

[http://sourceforge.net/forum/forum.php?thread_id=1297648&forum_id=104550](http://sourceforge.net/forum/forum.php?thread_id=1297648&forum_id=104550)

---

### Post by sinbad on 2005-07-07
Get the new (1.0.4) drivers.
Kismet and Airsnort work flawlessly when following the instructions in the above mentioned tutorial.

$ sudo iwconfig eth1 mode Monitor

---

### Post by cs378 on 2005-07-31
i did install kismet n airsnort n the newest ipw 1.0.6 driver

did the sudo iwconfig eth1 mode monitor

this show anything, i guess that is runnung with no error

after than i did

sudo kismet

kismet came out 
just this

```
root@csnetwork:/home/cs378 # kismet
Server options:  none
Client options:  none
Starting server...
Waiting for server to start before startuing UI...
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Enabling channel hopping.
Enabling channel splitting.
FATAL: Unknown capture source type 'ipw2200' in source 'ipw2200,eth1,ATHEROS'

root@csnetwork:/home/cs378 # sudo kismet
Server options:  none
Client options:  none
Starting server...
FATAL:  No 'suiduser' option in the config file.
Waiting for server to start before starting UI...
root@csnetwork:/home/cs378 #
``` 

notice w/o the sudo i get FATAL but with sudo i get nothing

help plz thx

---

### Post by ubuntu_demon on 2005-07-31
[QUOTE=cs378]i did install kismet n airsnort n the newest ipw 1.0.6 driver

did the sudo iwconfig eth1 mode monitor

this show anything, i guess that is runnung with no error

after than i did

sudo kismet

kismet came out 
just this

```
root@csnetwork:/home/cs378 # kismet
Server options:  none
Client options:  none
Starting server...
Waiting for server to start before startuing UI...
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Enabling channel hopping.
Enabling channel splitting.
FATAL: Unknown capture source type 'ipw2200' in source 'ipw2200,eth1,ATHEROS'

root@csnetwork:/home/cs378 # sudo kismet
Server options:  none
Client options:  none
Starting server...
FATAL:  No 'suiduser' option in the config file.
Waiting for server to start before starting UI...
root@csnetwork:/home/cs378 #
``` 

notice w/o the sudo i get FATAL but with sudo i get nothing

help plz thx[/QUOTE]
 some applications need root permissions to run. this is not a problem ... just a security feature.

---

### Post by sinbad on 2005-08-18
[QUOTE=ubuntu_demon]some applications need root permissions to run. this is not a problem ... just a security feature.[/QUOTE]

Actually that is not quite the case with Kismet. What is happening is a security feature.
Kismet needs root  to start and then drops from the root shell into a less privledged user's shell to run.

You _MUST_ edit the /ect/kismet/kismet.conf file to drop to your user account.

suiduser=youruseraccountnamehere

---

### Post by thezerogroup on 2005-08-30
I had the same problem, I fixed the user part....but still get:

FATAL: Unknown capture source type 'ipw2200; in source 'ipw2200,eth1,ATHEROS'

any ideas?

---

### Post by sinbad on 2005-09-10
Make sure that you are using the latest drivers, or at least 1.0.4

Make sure that your ipw2200 is eth1

$iwconfig

---

