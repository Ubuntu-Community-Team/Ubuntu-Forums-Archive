---
title: "[Poll] - Laptop battery life in Ubuntu"
date: 2007-01-06
forum: Hardware &amp; Laptops
---

### Post by thewillyway on 2007-01-06
Hey Everyone,

I was searching through the forums, looking for comparisons of battery life under Ubuntu and Windows XP, but I didn't find all of the results to be very conclusive. Some reported "Ubuntu battery killed their battery," others reported increases, but it'd be great to see some numbers instead!

I'm just curious because I'm dual booting Ubuntu and Windows, and even though everything works in Ubuntu, battery life is incredibly important to me. I would definitely solo-boot Ubuntu if battery life is about equal (10-20 mins) but I haven't had the time to set up tests (which programs do I run? how much time do I have to babysit my laptop to test, etc)

---

### Post by meng on 2007-01-06
My impression (no formal testing) is that it is the same.

---

### Post by thewillyway on 2007-01-06
Wow, fast response =)

---

### Post by meng on 2007-01-06
Unfortunately my notebook is currently "in the shop" and I can't do formal testing right now. Which is a shame because I was very curious about this very question.

---

### Post by ekka on 2007-01-07
I think Windows has better battery life than Ubuntu. This could be because of better power management like dimming the screen when on battery power and stuff like that. I am sure you can also do that in Ubuntu but haven’t figured out yet.

---

### Post by tweedledee on 2007-01-09
> **ekka said:**
> I think Windows has better battery life than Ubuntu. This could be because of better power management like dimming the screen when on battery power and stuff like that. I am sure you can also do that in Ubuntu but haven’t figured out yet.

Aside from the power settings available in Gnome settings (and I assume KDE, etc.), you can also enable laptop-mode.  You do this by setting the "laptop mode" line in /etc/default/acpi-support to true, then you can edit the /etc/laptop-mode/laptop-mode.conf file (which has lots of comments to explain) to control the power settings.  I assume if you set most of those parameters similar to what you had under Windows, you'd get similar life.

---

### Post by sonoftheclayr on 2007-01-10
I wouldn't know the battery light keeps flashing ;)
It was never a good battery anyway but when it did work I think I got 20mins out of it so you could say it was roughly the same as Windows :p

---

### Post by kerry_s on 2007-01-10
I didn't vote, on mine the battery meter is to fast, in other words it lies. I know from the specs it's suppose to last about 1hour 40 minutes. So i'll usually just use it for an hour and plug it back in.

acer aspire 3500
celeron M 1.4
512 ram
40 gig hd

On a side note it's not just ubuntu, i'm currently running PClinuxOS and it does the same thing.

---

### Post by NikoC on 2007-01-10
Getting the nearly the same amount of battery life in windows and ubuntu. My machine is a sony vaio VGN-S4HP.

---

### Post by cjr2k3 on 2007-01-10
Kubuntu manages my CPU scaling better, but Windows does have a better management with the screen and Bluethoot/wireless so i get about more 15min of batery in windows.

---

### Post by nsleiman on 2007-01-10
one hour 40 minutes, same as in windows! i think if we tune up the system we can get more life time out of it :)

---

### Post by noodles12 on 2007-01-10
windows has better management for me than ubuntu. In windows i use nhc to undervolt my processor and throttle it down. 

I can throttle the cpu speed down w/ laptop-mode but i havn't figured how to undervolt it yet.

---

### Post by ekka on 2007-01-11
> **tweedledee said:**
> Aside from the power settings available in Gnome settings (and I assume KDE, etc.), you can also enable laptop-mode.  You do this by setting the "laptop mode" line in /etc/default/acpi-support to true, then you can edit the /etc/laptop-mode/laptop-mode.conf file (which has lots of comments to explain) to control the power settings.  I assume if you set most of those parameters similar to what you had under Windows, you'd get similar life.

I am not aware of those settings, will definitely give it a try. Thanks for the tip.

---

### Post by thewillyway on 2007-01-15
Hmmm... I've actually been doing some more tweaking, and I can squeeze out some more battery life by working with aticonfig and wireless power settings.

With a dell e1505 with an ATI Mobility X1400, the video card power settings make a difference on the battery life. 

But even after my tweaks, windows still gets about 30 minutes more life than linux.

---

### Post by hardyn on 2007-01-15
I get about 40 more minutes using windows, it has to do mainly with the video driver, even playing with the fglrx driver, i cannot get the video card slowed down.  on battery the gpu fan never comes on using the windows ati driver. using the fglrx driver, the fan never shuts off, even with the powerlevel set to 0.  Hopefully ATI will get themselves figured out at some point.

---

### Post by earobinson on 2007-01-15
about the same for me

---

### Post by styson on 2007-01-16
> **hardyn said:**
> I get about 40 more minutes using windows, it has to do mainly with the video driver, even playing with the fglrx driver, i cannot get the video card slowed down.  on battery the gpu fan never comes on using the windows ati driver. using the fglrx driver, the fan never shuts off, even with the powerlevel set to 0.  Hopefully ATI will get themselves figured out at some point.

I have an Asus Z70Va with a 1.7Ghz Centrino and an ATI X700 Video card.  I get 3+ hours in XP and I get about 2.5 in Ubuntu 6.06.  The biggest difference is control over the video card and fan control.  In windows even when plugged in the fans run at lower RPM.  In Ubuntu they run much faster/louder.   Aside from that everything on the laptop works equally well.  I have enabled Laptop mode and went through the config file but it didn't seem to change much.

---

### Post by FFfanatic on 2007-01-18
I think my Acer Aspire 5102 beats you all in Ubuntu. In XP I could only get 2:45 hours if I turn down the cpu speed, display brightness lowest, no wireless, etc.. With Ubuntu, I can get about 3:10 with lowest cpu speed, lowest display brightness, and wireless on, etc. And that's only with the weak 6-cell battery. Dual core is amazing! :-D

---

### Post by Dygear on 2007-01-19
All in all about the same on the IBM / Lenovo Z61m thinkpad.

---

### Post by bvanaerde on 2007-01-25
Windows XP is definately faster, here on my laptop: there's about an hour in difference.

---

### Post by Quillz on 2007-01-25
Battery life seems about the same on my laptop, no matter what OS or distro I use.

---

### Post by earobinson on 2007-01-25
my battery just died, hope it wasent linux

---

### Post by demonhunter on 2007-01-29
It looks the same in both SO to me...

---

### Post by s3lf on 2007-02-03
Battery Life in WinXP is much longer (+1-2 hours!!) than in Ubuntu Edgy :(
I've got a Thinkpad T60, switched off bluetooth both in Win an Ubuntu just use firefox to surf the internet a little. WinXP consumes ~ 11W - Ubuntu minimum 16W :( Display at lowest lighting-level.

It's a Intel Centrinoe Due at 2Ghz - speedstepping seems to work as both cores run at 1Ghz - but the IBM tools in Windows seem to make a better job extending battery life ... why??

Alex

---

### Post by Strider42 on 2007-02-03
I would say XP is superior to Ubuntu.  I have seen a big decrease in battery life since installing Ubuntu on my Dell Inspiron.  I could probably get 3 hrs or more when running XP, but under Ubuntu that has dropped to approx 90 minutes :eek: 

I havent configured the OS to laptop mode yet, that's next.  I'll post results.

---

### Post by s3lf on 2007-02-06
I configured laptop mode ...  but even if my harddisk isn't running for minutes, battery time under ubuntu is only 2/3 from WinXP :(

---

### Post by macbuzz on 2007-02-06
Windows XP did no better or worse that Kubuntu Edgy but with Notebook Hardware Control, XP was significantly better on a Dell 600m.

I wish there was something similar to NHC for Ubuntu but haven't found anything like it yet.  I have tried some of the tools available within Kubuntu distro but everything seems to give me nothing more than average performance.

---

### Post by darkhatter on 2007-02-06
Windows XP has about 2 hours battery life:confused: , Suse got about 3 and half hours, and with Windows Vista I can get 4-5 depending on what I'm doing

---

### Post by s3lf on 2007-02-06
> **macbuzz said:**
> Windows XP did no better or worse that Kubuntu Edgy but with Notebook Hardware Control, XP was significantly better on a Dell 600m.

I wish there was something similar to NHC for Ubuntu but haven't found anything like it yet.  I have tried some of the tools available within Kubuntu distro but everything seems to give me nothing more than average performance.

There seem to be such tools .. but for me that don't bring an positive effect .. :(

[http://wiki.ubuntuusers.de/Prozessorspannung_absenken](http://wiki.ubuntuusers.de/Prozessorspannung_absenken) (german!)

based on [http://gentoo-wiki.com/HOWTO_Undervolt_a_Pentium_M_CPU](http://gentoo-wiki.com/HOWTO_Undervolt_a_Pentium_M_CPU)

You need a kernel patch to low cpu core voltage ... 

Has anyone experienced an significant energy saving by this method ??

Alex

---

### Post by Linuturk on 2007-02-06
I got longer battery life on my tablet because Toshiba had a utility that let me poweroff my cdrom drive.

---

### Post by spotdog14 on 2007-02-06
i dont really notice that much battery life difference between the two. I was actually very surprised by the power management that Ubuntu has, because based on other Linux builds that i have tried it has been horrible for a laptop. 

I have an Asus S5n with a 9 cell battery, and one thing that i have noticed is that the time remaining under Ubuntu does not jump around as much as it does under XP, though i have noticed that once it reads 0% remaining ill still have power for another 45 minutes or so. Ill get about 9-10 hours under XP with the lowest settings. I havent really tried and or remembered how long under Ubuntu. 

Oh and i dont get how the throttling works under Ubuntu, because when i add the little widget to my top panel to show CPU clock speed it always reads 600Mhz even though i have a 1.5Ghz P-M. But it does not feel like 600Mhz so i am pretty sure it is running at full speed, its just not showing it.

---

### Post by s3lf on 2007-02-06
> **Linuturk said:**
> I got longer battery life on my tablet because Toshiba had a utility that let me poweroff my cdrom drive.

did you manage this switching off under ubuntu ? would be interessting how it worked .. perhaps it work's for other notebooks, too.

---

### Post by bodycoach2 on 2007-02-06
I get better life with Ubuntu, but I had to setup frequency scaling to do it. Took me almost a week to figure it out, and another day to get it to work right. But, I can scale from 2.8 GHz to 349 MHz, so I can make the battery life go longer.

Now, if I could just get control of the fans.

---

### Post by ucsdrake on 2007-02-06
so far for me ubuntu has had a smaller battery life than Windows, however i havent played around with power settings so im guessing once ive fine tuned that aspect they will be very similar (if not id like Ubuntu to have longer battery life)

---

### Post by #Reistlehr- on 2007-02-09
well, if you could control brightness through linux, im sure you could save quite a bit of life. if i dont lower my brightness in windows, then boot into linux, it's nice and bright, and about 40 mins later, laptops dead.

also, by using acpi=off and noapic, so that my system will actually load, and wont crash x due to nvidia drivers, i cant use laptop-mode. since it's off, it doesnt read the file.

Edit: Also by disabling noapic so x doesnt crash, i lose battery functionality as in time left, and meters. i cant tell how much i have left, just stays at - 0:00

---

### Post by 23meg on 2007-02-09
Toshiba Tecra M4 tablet PC here, running about 20 minutes longer on Ubuntu.

---

### Post by mon_m on 2007-03-13
But is it fair to say that Windows has 30-60 more minutes on my laptop when I have a battery manager that dims/brightens my screen and variably cuts power to my processor?  Until there's something like that on Ubuntu, I think the poll has a bit of a discrepancy, yeah?

---

