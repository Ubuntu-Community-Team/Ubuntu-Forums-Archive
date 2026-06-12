---
title: "Dell C540 needs a liveCD....."
date: 2010-06-04
forum: Hardware
---

### Post by Chuck_N on 2010-06-04
I   have a Dell  Latitude C540 laptop, with windows2000 corrupted, won't boot. 
 It has 640 meg RAM already. I'd like to format and install an OS that works.

I put in the liveCD for Ubuntu 10.04LL  and booted; it reads about 30 seconds,
then quits and attempts a windows boot.  Could this mean that Ubuntu  won't run with
this processor?  

 How do I go about finding if some other OS (PuppyLinux or Moblin or antiX or ?)
 or something WOULD be appropriate for this machine?

---

### Post by viralmeme on 2010-06-04
[http://forum.notebookreview.com/dell-inspiron-dell-studio/339218-inspiron-12500-wont-boot-cd.html](http://forum.notebookreview.com/dell-inspiron-dell-studio/339218-inspiron-12500-wont-boot-cd.html)

---

### Post by Chuck_N on 2010-06-04
some similarities here, however...

in my case the liveCD is attempting to boot
and quits after 1/2 minute.

I still wonder if Ubuntu won't work with this machine at all,
and if so, what other OS I should try.

---

### Post by Chuck_N on 2010-06-07
hmmmmmmmmm.................

I downloaded and built a liveCD for antiX
(designed for older computers with little RAM and old processors)

It works okay on my Presario

but when I attempt to boot the old Dell, I get the same results as I did with the liveCD Ubuntu

... it tries to boot for about 30 seconds, then proceeds to try a Windows boot from C:

and unfortunately that machine can't boot from C: as a result of a Trojan attack.

Maybe I need to format the harddrive?  But then, how can I do that if I can't get the machine booted?

How about if I have the drive formatted at a dealer? Could I then boot with liveCD and install to the harddrive?

---

### Post by anticapitalista on 2010-06-07
My guess is that your RAM isn't really 640MB. Maybe a dodgy stick somewhere.

Download DSL (Damn Small Linux) and see if that will boot. If it does, check how much RAM is really available and also you could use it to check your hard drive.

---

### Post by Chuck_N on 2010-06-07
I tried a 128-boot, then a 512-boot, then a 640-boot

each time I got a message regarding RAM size change.

each time system report was accurate regarding Ram size.

each time the CD boot-cycle did approx a dozen reads,
then gave up and tried a windows boot from C:

okay, now I put in a different cd-drive.
I got a successful  anti-X boot.
Followed by a successful  Ubuntu  boot.

I am now formatting the drive for Ubuntu only.

Hopefully that will give me a usable machine......

---

### Post by anticapitalista on 2010-06-07
So the cd drive was the problem.
Good luck with whatever distro you put on that box.

---

### Post by Chuck_N on 2010-06-07
okay, now I'm trying to install a 3com wireless adapter.  I have it plugged in and the light is on. 
Ubuntu Help says

[COLOR=SeaGreen]
[/COLOR][COLOR=SeaGreen]To connect to a wireless network:[/COLOR]
                                
[LIST=1]
[*]                     [COLOR=SeaGreen]Ensure that your wireless device is turned on.[/COLOR]
[*]                     [COLOR=SeaGreen]Click the Network Manager icon in the system  notification area.[/COLOR]
[*]                     [COLOR=SeaGreen]Under *Wireless Networks*  click on the network you want to connect to.[/COLOR]
[/LIST]
               
               [COLOR=SeaGreen]     If you have connected to the network previously, Ubuntu will  automatically      connect to the network where it is available.     [/COLOR]
               [COLOR=SeaGreen]     If you are connecting to a network for the first time, security  details may      be needed. If so, a dialog box will open.[/COLOR]

I have the Network Connections window open, which has tabs for Wired and Wireless and Broadband and VPN and DSL.  All of those are empty except Wired which has  Auto eth0
I tried a  LYNKSYS  adapter also. Same problem with both: nothing appears in the Wireless tab window.
Any ideas on how to proceed?

---

### Post by Chuck_N on 2010-06-09
okay, the 3com didn't work  and  the LinkSys didn't work.
As I recall, these didn't work on the Presario either, and for that reason
I ordered a  G/SKY  adapter, which I haven't tried yet.
(haven't had time to try it out on the Presario, which is running fine, for now, on Ethernet).

Tried it, not sure about the install; need to call my ISP and get some help....

More later.

---

