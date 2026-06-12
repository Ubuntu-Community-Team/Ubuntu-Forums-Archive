---
title: "Presonus Firepod, jackd/freebob and Ubuntu"
date: 2007-04-27
forum: Hardware &amp; Laptops
---

### Post by shpongled on 2007-04-27
I tried following a lot of advice someone had posted about getting their firebox to work in Ubuntu.  Mine still does not however.  This is what happens when I try and run freebob from the jackd interface...

```
jackd 0.102.20
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
Freebob using Firewire port 0, node -1
Ieee1394Service::initialize: Could not get 1394 handle: Permission denied
Is ieee1394 and raw1394 driver loaded?
Fatal (devicemanager.cpp)[68] initialize: Could not initialize Ieee1349Service object
Fatal (freebob.cpp)[69] freebob_new_handle: Could not initialize device manager
FreeBoB ERR: FREEBOB: Error creating virtual device
cannot load driver module freebob
no message buffer overruns

```

If I look in my device manager, my presonus firepod is listed under the TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)

Any ideas on how to set this up?

---

### Post by dumbace on 2007-05-14
any kind advice would be very very appreciated .... I cant see my presonus firebox under ubuntustudio....
Thanks in advance
d.

---

### Post by thecreekninja on 2007-05-17
I just installed ubuntu studio on a fresh drive, opened a new PreSonus Firebox and it worked with ubuntu studio with one exception: I had to enter this command in the terminal(this has to be entered everytime you login):

sudo chmod o+rw /dev/raw1394

this was because I was getting "Could not get 1394 handle: Permission denied:"

I also had to enter Setup in Jack Control and change Driver to freebob and change the number of input channels and output channels to 10.  (I didn't know what to use cause it was defaulted to 0 so I just chose 10 and it worked)

I got this info form here:
[http://www.nabble.com/-linux-audio-user---dev-raw1394-permissions.-Using-firewire-interface-Focusrite-Saffire-t2835971.h](http://www.nabble.com/-linux-audio-user---dev-raw1394-permissions.-Using-firewire-interface-Focusrite-Saffire-t2835971.h)

---

### Post by dumbace on 2007-05-18
Thanx, 
I'll check it out as soon as possible and hope it works at least....

p.s.: btw, your links seems to get into denied access page

D

---

### Post by sengoku on 2007-05-18
> **dumbace said:**
> Thanx, 
I'll check it out as soon as possible and hope it works at least....

p.s.: btw, your links seems to get into denied access page

D

put 'tml' at the end of the link after .h and it works ok :)

i just got it working all fine using the instructions in that thread (i made raw1394 use audio group instead of disk, and freebob's my uncle)

---

### Post by dumbace on 2007-05-18
hey, can't believe it, it works:)

thanks for the useful advice...

I was much depressed because yesterday  I've just got the presonus staff's answer:

*There is nothing in the works, at the moment, for Linux based drivers. I have no specific timing for you either.  I will, however, pass this along to my software guys as you are not alone in the Linux world. It anything is released it will be posted on our website.*:mad:

as a whole noob I'd like to be able to make a script in order to avoid the everytime typing at every login...

cheers

---

### Post by sengoku on 2007-05-18
the better way (avoiding script) is to do this

```

sudo gedit /etc/udev/rules.d/40-permissions.rules

```

find this :

```

# IEEE1394 (firewire) devices
# Please note that raw1394 gives unrestricted, raw access to every single
# device on the bus and those devices may do anything as root on your system.
# Yes, I know it also happens to be the only way to rewind your video camera,
# but it's not going to be group "video", okay?
KERNEL=="raw1394",			GROUP="disk"
KERNEL=="dv1394*",			GROUP="video"
KERNEL=="video1394*",			GROUP="video"

```

and change it to 

```

KERNEL=="raw1394",			GROUP="audio"

```

they're right, it's not going to be group 'video' :D

hope this helps.

---

### Post by dumbace on 2007-05-19
sengoku,
you are my best friend...

thanks for all

D.

---

### Post by vivichrist on 2007-06-12
I can start jackd once maybe twice and then jackd refuses to work. note this is using realtime with lowlatency kernel and limits.conf modifications and jackd is not root. in the messages (qjackctl) the error is "can't create virtual device". have used gscanbus to force reset the firewire bus to no avail.

---

### Post by Carignan on 2007-07-04
> **thecreekninja said:**
> I just installed ubuntu studio on a fresh drive, opened a new PreSonus Firebox and it worked with ubuntu studio with one exception: I had to enter this command in the terminal(this has to be entered everytime you login):

sudo chmod o+rw /dev/raw1394

this was because I was getting "Could not get 1394 handle: Permission denied:"

I also had to enter Setup in Jack Control and change Driver to freebob and change the number of input channels and output channels to 10.  (I didn't know what to use cause it was defaulted to 0 so I just chose 10 and it worked)

I got this info form here:
[http://www.nabble.com/-linux-audio-user---dev-raw1394-permissions.-Using-firewire-interface-Focusrite-Saffire-t2835971.h](http://www.nabble.com/-linux-audio-user---dev-raw1394-permissions.-Using-firewire-interface-Focusrite-Saffire-t2835971.h)

I have a Presonus Firebox and I confirm!  this procedure works juste fine with a fresh install UbuntuStudio.:D

EDITED: the folowing statement is not true any more :"Sad that i have to enter this command at each boot :(  Maybe in the next release the Firebox "Will just work!"

now with the following procedure it work juste fine !
> 
Code:
[QUOTE]sudo gedit /etc/udev/rules.d/40-permissions.rules

find this :

Code:
> 
# IEEE1394 (firewire) devices
# Please note that raw1394 gives unrestricted, raw access to every single
# device on the bus and those devices may do anything as root on your system.
# Yes, I know it also happens to be the only way to rewind your video camera,
# but it's not going to be group "video", okay?
KERNEL=="raw1394",			GROUP="disk"
KERNEL=="dv1394*",			GROUP="video"
KERNEL=="video1394*",			GROUP="video"


and change it to

Code:
> 
KERNEL=="raw1394",			GROUP="audio"

they're right, it's not going to be group 'video' 

[/QUOTE]

---

### Post by vivichrist on 2007-07-09
yes I have read through the thread and actually I did silly
I added "MODE=0666" to that line in /etc/udev/rules.d/40-permissions.rules
and since removing this I think its fixed ... but....

---

### Post by BrNBrN on 2007-07-27
I ve tried many way that yours  but my sound card doesnt work.

is there any body help me to use firebox ?

**my jack setting is  **
[IMG]http://img357.imageshack.us/img357/350/1212by1.png[/IMG]


**my device maneger look like **
[IMG]http://img519.imageshack.us/img519/8852/devicekl7.png[/IMG]

I dont understand what can I do and why firebox doesnt  work.

Any help would be gratefull...

---

### Post by vivichrist on 2007-07-30
OK I would try sample rate: 48000
                  input channels: 2
                output channels: 2
                               priority: 75

---

### Post by BrNBrN on 2007-08-04
> **vivichrist said:**
> OK I would try sample rate: 48000
                  input channels: 2
                output channels: 2
                               priority: 75

My sound card is working now :)

My problem was priority and input output settings, When I had changed these, it worked.

Thank you so much vivichrist.

---

### Post by swedishfrog on 2008-03-03
If you're still having trouble with the Presonus Firepod, check out this post:
[http://ubuntuforums.org/showthread.php?t=713695&highlight=firepod]("http://ubuntuforums.org/showthread.php?t=713695&highlight=firepod")

---

