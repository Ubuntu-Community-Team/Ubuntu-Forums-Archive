---
title: "BUG: soft lockup detected on CPU#0!"
date: 2006-12-20
forum: Hardware &amp; Laptops
---

### Post by awarberg on 2006-12-20
Hi

I could not get my dell inspiron 6400 to boot this morning. So I booted up in the recovery mode and the boot process tells me:

[17179595.808000]: BUG: soft lockup detected on CPU#0!

And stops after this.

I recently upgraded the bios version from A09 to A11. Maybe this has something to do with it. 
Fortunately my Windows installation still works fine.

Can I bring Ubuntu back again somehow?

Regards
Andreas

---

### Post by benhall on 2006-12-20
Do you have ipw3945? There is a known bug which prevents boot when the wireless is turned off; go here to get a fixed ipw3945.ko

[https://bugs.launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/63418](https://bugs.launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/63418)

---

### Post by dwnichols on 2006-12-22
Hey Andreas,

  I too have that laptop and noticed the same problem..

---

### Post by shareMenaPeace on 2006-12-31
Thx for this hint, have same issue with d620

---

### Post by akaione on 2007-01-03
**Possible fix for this problem -- works for me:**
[I](NB: This fix are for somewhat knowledged users. Others please wait for someone more 
user-oriented to post a working "easy fix" or wait for a official update that resolves the 
problem)[/I]

Hardware tested on: Dell Inspiron 9400, Intel Mobile 945GM chipset (and ofcourse this 
includes the infamous Intel Pro Wireless 3945 chip).

First off: I've had this problem for three weeks -- I ran into it a mere three days after getting 
my brand new laptop. I've bugged the living h*ll out of people I know who knows more about 
Ubuntu and Linux kernels than me, and I'd like to thank them for putting up with me and my 
frustrations (Berge, Tollef, Morten, et. al.). 

**SHORT description of fix: **
Edit /etc/apt/sources.list and alter it so that it contains the Dapper sources.
Install the 2.6.15-27-686 kernel and restricted-modules-2.6.15-27-686 packages.
Boot the 2.6.15-27-686 kernel and verify that you can get a sucessful bootup.
Enter BIOS -- turn WiFi and Bluetooth completely off.
Disable the key for switching on and off WiFi/Bluetooth.
Reboot.
Boot the 2.6.15-27-686 kernel and verify that you can get a sucessful bootup.
Reboot.
Enter BIOS -- turn WiFi on.
Enable the key for switching on and off WiFi only for WiFi -- not for Bluetooth.
Reboot.
Boot the 2.6.15-27-686 kernel and verify that you can get a sucessful bootup.
Use the fn+f2-keycombo to enable WiFi -- push it only once.
Open a terminal and use iwconfig to configure the WiFi-device to suit your needs.


**The longer story:**
I tried upgrading to the unstable Feisty edition: had no luck the issue was still around with the 
rf_kill unwritable in /sys, and there was no way to make fn+f2 work the way it should. Any 
pushing of the keys spewed out the errors in dmesg like so many others have reported.

Then I tried to reinstall Edgy from the LiveCD and surprise, surprise, the machine froze with 
the soft lockup. To resolve this I used the Edgy ServerCD-installation and since it does not 
probe the ipw3945 at all, I got to install Edgy by hand from it. Others may want to use Dapper 
since it's a little less effort to install than a server-installation. 

I have tried a lot of kernels from Dapper, Edgy and Feisty (actually all vanilla kernels available I believe):
[INDENT]2.6.15-25-686
2.6.15-27-686
2.6.17-10-386
2.6.17-10-generic
2.6.19-7-generic
2.6.20-1-generic
2.6.20-2-generic
2.6.20-3-generic
[/INDENT]

The issue was present with all. To resolve it I had to fiddle A LOT with the BIOS:

Entering BIOS I switched off wireless completely, switched off bluetooth completely, set the 
special key for wifi/bluetooth to be disabled and rebooted. Verified that I could get 
2.6.20-2-generic (from Feisty) working and rebooted again. Back in BIOS i switched wireless 
on, set the key for wifi/bluetooth to be only for wifi enabled and rebooted again. 

I booted the 2.6.15-27-686 kernel from Dapper and to my big surprise I got no soft lockup. 
In a terminal I then had to use iwconfig to set parameters for the wireless card (eth1) as the 
Network Settings-utility would not allow me to configure it). 

Since I got WiFi working again I thought I could be so user-like stupid to push the button 
again, just to see if I could reproduce the failure; but it kept on working on the 2.6.15-27-686 
kernel. Even with being switched off and rebooted WiFi could be turned back on with the 
fn+f2-keys. (Booting the 2.6.17-10-generic kernel from Edgy ofcourse replicates the problem 
if pushing the fn+f2 switch to turn WiFi off and then booting..)

In the end I've now tested rebooting and switching the WiFi on and off in 2.6.15-25-686 and 
2.6.15-27-686. The 2.6.17-10-generic kernel from Edgy gives the dmesg output about the 
keys pushed not being recognized but after adding the modified ipw3945.o-module posted 
multiple places on this forum and on launchpad.net I could get the function to work and I can 
switch the kernel on and off.

Hope this helps someone.. and good luck! :)

---

### Post by Rhawi Dantas on 2007-01-23
Thanks man... you really did a great job.
I was battling with it for almost a month already.

---

### Post by fsanders on 2007-01-24
Fortunately, I was able to get around this same problem by turning on the wireless (using the switch on the laptop).  I have an IBM T60 Thinkpad running Edgy

---

### Post by matsurd on 2007-01-25
Hello,

I'm using Toshiba Satellite M115-S3154 (core duo), running Ubuntu 6.10 and had that same problem.
However, it only happens when i'm running on battery power... 
Tried turning off the second CPU from BIOS solved it, but ... i want to use both of them :D
Apparently it was caused by turning the CONTROL_HD_POWERMGMT on in the laptop-mode.conf
Turning it off solved it...now it can boot on battery again, YAY!  (hopefully for good)

Hope that helps.
(1st post in forum)

---

### Post by Surgeon General on 2007-02-06
seems up to now the bug is still there:

[LIST]
[*]Dell Inspiron 6400 (E1505) T2500
[*]Dapper upgraded to Edgy using alternate install CD
[*]kernel 2.6.17-10-generic SMP
[/LIST]

i didn't touch the BIOS settings and the only work around i do, until i found this thread, is to power off twice. on the 3rd power on it would boot fine as if nothing has happened.

i'm gonna try the suggested link.

---

### Post by Cannaregio on 2007-03-28
There are A LOT of threads with the same problem.
Definitely some developers should look into it.
"Three times switching" is NOT the right way to go, imho.
Similar things happened to me and the following could be useful for people with similar problems. Maybe. Maybe not. Worth trying.


```
BUG: soft lockup detected on CPU#0!
```

Happens imho
[LIST]
[*]when you have a dual boot config
[*]when you TURNED YOUR WIRELESS OFF inLinux
[*]when you did reboot in windows after that
[*]when you now tried to reboot in linux with wireless still off
[/LIST]

Solution (worked for me)
[LIST]
[*]Reboot in windows
[*]Return wireless on
[*]shutdown windoze and reboot linux
[/LIST]

So the point is to RESET WIRELESS ON.
Why this kind of bug/error 
should be/could be/probably is 
related with wireless beats me.

(this rig was 2.6.17-11-generic, 3945 ABG Intel wireless, ubuntu edgy on a Siemens Amilo S that has an annoying flashing wireless light that you always like to turn off if there's no connection even if it is actually not necessary: let it flash and avoid the problem)

Good luck.

---

### Post by seamus7 on 2007-03-30
I had to just turn my wireless off in the BIOS a couple of months ago because of this bug .. i'm also using edgy on a dell e1505 laptop intel core 2 duo with the ipw3945... turning off the wireless in the BIOS works for me cause i don't have a wireless router at home and i rarely go out to hotspots ... but i'm disappointed a solution hasn't been created yet ... 

i guess it's either a really tricky problem to solve or there are more pressing bugs to get to first ... oh well .. i can turn the wireless on and use it via my vista partition if the need arises ... so it's not a gigantic problem at least for me but it does discourage me from going wireless at home anytime soon...

(crossing my fingers)

---

### Post by fransurbo on 2007-04-12
For me this happens on a MacBook (black). There's no BIOS and I can't disable the WiFi anyway (no button/switch etc for this).

Also, it DO happen even if the wifi driver isn't loaded, but when it is (ndiswrapper) the soft lockup is almost guarantied if I hibernates or suspends the machine. It (the machine) usually survives the first hibernate/suspend but never the second...

And if I try to unload the module and then load it again (with or without hibernate/suspend), i get the soft lockup...

I'm running Feisty with kernel 2.6.20-1[2-4] and all of them show the same behaviour.

---

