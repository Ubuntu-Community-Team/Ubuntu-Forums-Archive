---
title: "Suspend and hibernate no longer work"
date: 2006-06-17
forum: Hardware &amp; Laptops
---

### Post by Halmonster on 2006-06-17
I've been running Dapper on my IBM ThinkPad T42 since a few days before the official final release.  Everything was great - both suspend and hibernate worked, and I could even link the suspend action to closing the laptop lid.  I was in heaven.

Then, yesterday, there were some updates, which I dutifully installed.  Alas, the new kernel (2.6.15-25-686) did a panic when I rebooted, so I dropped back to the previous kernel (2.6.15-23-686) instead.

But now today when I booted up my machine, neither suspend nor hibernate work.  If I click on the cute battery icon in the tray, it brings up a menu.  I click on 'Suspend" which is the first entry in the menu, and I get a cute dialog bubble which says:

  Suspend Problem
    Your computer failed to
    suspend.
    Check the FAQ page for
    common problems.

The FAQ page is a link to [http://www.gnome.org/projects/gnome-power-manager/faq.html](http://www.gnome.org/projects/gnome-power-manager/faq.html) which in my case is not helpful at all.

Any ideas?

Thanks,
Hal

---

### Post by DrSturgeon on 2006-06-17
Might not be the same issue, but...

I have a t43, and that pesky last kernel update broke suspend.  It now appears to suspend, except that the fan never turns off, and it won't wake up.

Anybody have any ideas?

---

### Post by DrSturgeon on 2006-06-17
Oh, and, to try to actually be helpful...

Check the syslog (/var/log/syslog) and look at what happened when you tried to suspend.  You might be able to figure out what's preventing it.

---

### Post by hugh on 2006-06-17
[QUOTE=DrSturgeon]Might not be the same issue, but...

I have a t43, and that pesky last kernel update broke suspend.  It now appears to suspend, except that the fan never turns off, and it won't wake up.

Anybody have any ideas?[/QUOTE]

Exact same problem with my T43.

---

### Post by DrSturgeon on 2006-06-17
Apparently we're not the only ones:

[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/50031](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/50031)

---

### Post by siriusnova on 2006-06-17
It's a confirmed bug that affects many thinkpad models including my T30

id suggest to revert back to the older (23) kernel till this gets fixed, its what i did

---

### Post by tstadler on 2006-06-18
I will confirm my t42 does this as well.

---

### Post by afilonov on 2006-06-18
Same with my t41

---

### Post by michaelbrown on 2006-06-18
I'd like to chime in and say that suspend/hibernate are also newly broken on my Dell Inspiron 9300. Well, to be precise, suspend/hibernate no longer work when called from the login screen. If I'm logged in, they work fine. The only thing I've seen in syslog that seems moderately suspicious is

 ibm_acpi: ec object not found

And to confirm: suspend/hibernate were working fine from every aspect before the new kernel update. Any ideas?

---

### Post by mh17 on 2006-06-19
It seems not to be a thinkpad problem. I've got the same troubles with my Acer Travelmate 242LC.

Michael

---

### Post by cneil on 2006-06-19
I've had the same problem with my Gateway 7510GX.  I tried to hibernate with the new kernel and got a kernel panic.

---

### Post by l.tambiah on 2006-06-19
The thinkpad suspend issue and hibernate can be solved with some hacks, but hibernate is very buggy in my opinion. But suspend works great see forum:

[http://www.ubuntuforums.org/showthread.php?t=187584](http://www.ubuntuforums.org/showthread.php?t=187584)

---

### Post by afilonov on 2006-06-20
acpi-support 0.85 fixes that problem (suspend, at least, didn't try hibernate yet). Just appeared in repository.

---

### Post by l.tambiah on 2006-06-20
[quote=afilonov]acpi-support 0.85 fixes that problem (suspend, at least, didn't try hibernate yet). Just appeared in repository.[/quote]

I have replaced the original code into the sleep.sh to test the new acpi-support 0.85 fixes. I am using an IBM Thinkpad R50e and I can confirm that both suspend and hibernate are now working!

However the hibernate function still produces brown lines on the screen when booting up from a hibernate. Although this doesnt disrupt the process it is clear that something is not quite right.

---

### Post by neoflight on 2006-06-21
[QUOTE=DrSturgeon]Might not be the same issue, but...

I have a t43, and that pesky last kernel update broke suspend.  It now appears to suspend, except that the fan never turns off, and it won't wake up.

Anybody have any ideas?[/QUOTE]


same symptom here in my T42 with dapper and 2.6.-15-25-686 kernel. and i have installed the thinkpad key stuff from synaptic and they dont work.... (the forward and back buttons, screen off, sleep etc)

---

### Post by ilmw on 2006-06-27
[QUOTE=l.tambiah]I have replaced the original code into the sleep.sh to test the new acpi-support 0.85 fixes. I am using an IBM Thinkpad R50e and I can confirm that both suspend and hibernate are now working!

However the hibernate function still produces brown lines on the screen when booting up from a hibernate. Although this doesnt disrupt the process it is clear that something is not quite right.[/QUOTE]

I have acpi-support 0.85 with 25-686 kernel. but neither suspend nor hibernate works. btw, my machine is Dell 700m. They worked well before i upgrade to 25-686. Anyone else has the same problem?

---

### Post by wobster on 2006-06-27
I can confirm this for a ACER TravelMate 3020.

---

### Post by markthecarp on 2006-06-27
[QUOTE=afilonov]acpi-support 0.85 fixes that problem (suspend, at least, didn't try hibernate yet). Just appeared in repository.[/QUOTE]
Which repository? 

Sleep is not working on my Toshiba Sat 1415-S173. Using the standard dapper repos I'm getting only acpi-support 0.84. 

I recently upgraded from breezy and started with the 2.6.15-25-686 kernel, never had *.23-686 installed. Actually started with hoary on this machine and this is the best it's ever been.

-mark

---

### Post by The Raven on 2006-06-27
I had an incident the first time I unplugged the power connector on the back of my Presario V2000. The screen went black and the laptop powered off without moving to battery back-up power. The odd thing about it was, is when I re-applied the a.c.-power the system booted out of a suspended state. I hadn't even closed the lid on my laptop.

 I haven't had that problem again, as I have removed a.c.-power from the laptop several times since then. 

 These type of bugs aren't anything but stupid wrinkles that will get smoothed out as the organized approach to handling different platforms matures with UBUNTU. It's all a part of development when dealing with a complexity like operating systems. You all are quite aware of that, I know.

 I do know this much, the ACPI power management tools need to be a darn site more configurable with several more power handling schemas.

 Hybernate, Suspend, Resume, Laptop power sheme, Desktop power scheme, Always On power schemes, Multimedia power schemes are all good considerations but the configurability needs expansion.

---

### Post by afilonov on 2006-07-08
> **markthecarp said:**
> Which repository? 


Sleep is not working on my Toshiba Sat 1415-S173. Using the standard dapper repos I'm getting only acpi-support 0.84. 

I recently upgraded from breezy and started with the 2.6.15-25-686 kernel, never had *.23-686 installed. Actually started with hoary on this machine and this is the best it's ever been.

-mark

Repository dapper-updates

---

### Post by gazza567 on 2006-07-09
My Compaq Presario's Suspend and Hibernation doesnt work under dapper. :( comes up with mot enough swap error and fails.

---

