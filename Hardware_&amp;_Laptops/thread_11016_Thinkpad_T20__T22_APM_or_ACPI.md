---
title: "Thinkpad T20 / T22 APM or ACPI"
date: 2005-01-13
forum: Hardware &amp; Laptops
---

### Post by Poldi on 2005-01-13
hi. following the Ubuntu discussions since early October I still have a problem understanding the issues concerning notebook powermanagement.

I have several different Thinkpads working to various degrees.

most importantly, my Tinkpad T20 and T22 do not work at all power-management-wise.

what I know is: ACPI on those older machines is probably buggy and incomplete, so I should just not try at all and use APM instead.

now in this forum I constantly see 2 different oppinions regarding this:

a) just put apm=on, acpi=off and/or noacpi to your kernel parameters and start apm with your services and you will be fine using APM instead of ACPI from now on.

b) Ubuntus kernels do only include ACPI by default. you have to build your own APM-enabled kernel to make this work.

now what?

of course I tried the a) variant - to no avail. I do not want ram2hd hibernation, just a regular suspend with the ability to use either the Thinkpads Fn-keys or to just close the lid to suspend and reopen to awaken. this did work in OS/2 and every 2.4.x Linux-distro I tried. 

so: could anybody that has a T2* model working just try to take my hand and work me though this one step-by-step? I want to use a regular Warty Ubuntu if possible.

tanks a lot.

by the way: I have a Thinkpad R40 working via ACPI (to a certain degree) and an old Thinkpad 390 working via APM (without any special efford on my side).

kind regards,
Carsten

---

### Post by scott_b on 2005-01-13
I just installed ubuntu and was looking for a way to get APM up for my R40.  How did you get ACPI to work for your R40?  All I really care about is sleep, did you get that working? I would appreciate any help you could offer.

-Scott

---

### Post by bkuhn on 2005-04-26
Carsten,

I have had the same problem with a T20.  In fact, if I turn on APM, it goes to sleep fine, but when it wakes up, I get filesystem corruption and other horrible things.

I think either (a) Linux 2.6 doesn't work with these older laptops or (b) there is a BIOS update from IBM that might make some versions work and some not.  I am going to test (b) when I get a chance and will post my results.

---

### Post by wrwills on 2005-05-03
I encountered this same problem with a t22: sleep using apm causes strange behaviour: windows don't open properly; sound doesn't work any more; won't logout properly.  I tried the latest bios update from ibm.  It didn't help.

---

### Post by MemoryDump on 2005-05-25
[QUOTE=Poldi]hi. following the Ubuntu discussions since early October I still have a problem understanding the issues concerning notebook powermanagement.

I have several different Thinkpads working to various degrees.

most importantly, my Tinkpad T20 and T22 do not work at all power-management-wise.

what I know is: ACPI on those older machines is probably buggy and incomplete, so I should just not try at all and use APM instead.

now in this forum I constantly see 2 different oppinions regarding this:

a) just put apm=on, acpi=off and/or noacpi to your kernel parameters and start apm with your services and you will be fine using APM instead of ACPI from now on.

b) Ubuntus kernels do only include ACPI by default. you have to build your own APM-enabled kernel to make this work.

now what?

of course I tried the a) variant - to no avail. I do not want ram2hd hibernation, just a regular suspend with the ability to use either the Thinkpads Fn-keys or to just close the lid to suspend and reopen to awaken. this did work in OS/2 and every 2.4.x Linux-distro I tried. 

so: could anybody that has a T2* model working just try to take my hand and work me though this one step-by-step? I want to use a regular Warty Ubuntu if possible.

tanks a lot.

by the way: I have a Thinkpad R40 working via ACPI (to a certain degree) and an old Thinkpad 390 working via APM (without any special efford on my side).

kind regards,
Carsten[/QUOTE]


anyone have any further ideas on this "problem"? I'd really like to get my T22 working properly so I can avoid booting the "other" OS!!

thxs
-MD

---

### Post by sebausn on 2005-05-25
Hi guys!

I use apm on my T22 and had the same problem when I tried to suspend it.
I just figured out, that the problem is the sound! So I wrote a small script to unload the sound module and put it in 

/etc/apm/event.d/

to run it automatically:

#####################################
#!/bin/sh
case "$1" in
 resume)
  /sbin/modprobe snd-cs46xx
  sleep 5
  /etc/init.d/alsa start
  esd &
  ;;
 suspend)
   /usr/bin/killall /usr/lib/gnome-applets/mixer_applet2
   /usr/bin/killall esd
   /etc/init.d/alsa stop
   /bin/sleep 5
   /sbin/rmmod snd-cs46xx
   ;;
esac
#####################################

Don't forget to "chmod +x"  the file! Finally my TP works perfectly :)

Good luck!
Seb

---

### Post by MemoryDump on 2005-05-26
[QUOTE=sebausn]Hi guys!

I use apm on my T22 and had the same problem when I tried to suspend it.
I just figured out, that the problem is the sound! So I wrote a small script to unload the sound module and put it in 

/etc/apm/event.d/

to run it automatically:

#####################################
#!/bin/sh
case "$1" in
 resume)
  /sbin/modprobe snd-cs46xx
  sleep 5
  /etc/init.d/alsa start
  esd &
  ;;
 suspend)
   /usr/bin/killall /usr/lib/gnome-applets/mixer_applet2
   /usr/bin/killall esd
   /etc/init.d/alsa stop
   /bin/sleep 5
   /sbin/rmmod snd-cs46xx
   ;;
esac
#####################################

Don't forget to "chmod +x"  the file! Finally my TP works perfectly :)

Good luck!
Seb[/QUOTE]

Hi sebausn
what exactly did you do? I've inserted your script (/etc/apm/event.d/sound) & rebooted and I still get NO SOUND. Did you remove the acpi=off from your bootup?
I'd really like to get some sort of power management and at lease "some" sound working on my Thinkpad T22.

thxs
-MD

---

### Post by zorba on 2005-06-21
First of all, Hello Guys :)

On thinkpad T23 (AFAIR model 2647) all power management works perfectly on ACPI mode. Just after install everything works perfectly (with only one minor flaw described below)

[QUOTE=sebausn]
I use apm on my T22 and had the same problem when I tried to suspend it.
I just figured out, that the problem is the sound! So I wrote a small script to unload the sound module and put it in 
[/QUOTE]
Thanks a lot for this script, i have a similar problem with esd. Laptop suspended perfectly, resume is also made without any problem but when an attempt to play a sound by esd daemon is made, this process starts to eat's processor activity. I had to kill him, and run esd again.

EDIT: Sorry about answering on the discontinued product (topic found by search mode). Post dedicated to Hoary Hedgehog.

---

### Post by Z(L)o on 2006-11-05
Hello
thanks, I've switched to apm now, which seems to be pretty stable and doesn't give me headaches (fingers crossed) with coming back from hib. 
quesion:
now that i use apm pc goes to suspend every time i am closing the lid, which i want to change. 

where is the setting for that? 
in acpi it used to be somewhere here:
/etc/acpi/events/lidbtn 

do you know where it can be tweaked in APM? 

Thanks,

---

### Post by Mark Stosberg on 2006-11-05
> **Z(L)o said:**
> 
now that i use apm pc goes to suspend every time i am closing the lid, which i want to change. 


I believe there is a setting in the BIOS that turns off this signal when closing the lid. (I use a T20 myself).

---

