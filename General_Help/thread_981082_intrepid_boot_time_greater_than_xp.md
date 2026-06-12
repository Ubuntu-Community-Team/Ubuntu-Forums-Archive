---
title: "intrepid boot time greater than xp"
date: 2008-11-13
forum: General Help
---

### Post by tgpraveen on 2008-11-13
i upgraded to intrepid a week back and have some probs which i think i might habve finally sorted out see this for more info
[http://ubuntuforums.org/showthread.php?t=977644](http://ubuntuforums.org/showthread.php?t=977644)


but now i am feelinng that my boot time has gone up specifically it takes around 1:50 secs to boot into ubuntu wheras for xp it takes 1:35 that with many progs on autostart in xp. i know my sys is old but still ubuntu shouldnt get beaten by xp.

---

### Post by prshah on 2008-11-13
> **tgpraveen said:**
> 
but now i am feelinng that my boot time has gone up specifically it takes around 1:50 secs to boot into ubuntu wheras for xp it takes 1:35 that with many progs on autostart in xp. 

You can install bootchart to see what is causing a delay in startup (if any):

Manually: Open a terminal (Applications-Accessories-Terminal) and give the command
```

sudo apt-get install bootchart
``` or just click: [Install bootchart]("apt://bootchart")

Now, on every boot a graphical progress chart is created in "/var/log/bootchart". Post the bootchart files for a clue as to what could be causing a delay.

---

### Post by tgpraveen on 2008-11-14
see the attached files and help me.

---

### Post by oilchangeguy on 2008-11-14
> **tgpraveen said:**
> i upgraded to intrepid a week back and have some probs which i think i might habve finally sorted out see this for more info
[http://ubuntuforums.org/showthread.php?t=977644](http://ubuntuforums.org/showthread.php?t=977644)


but now i am feelinng that my boot time has gone up specifically it takes around 1:50 secs to boot into ubuntu wheras for xp it takes 1:35 that with many progs on autostart in xp. i know my sys is old but still ubuntu shouldnt get beaten by xp.

the 15 second difference is not that great. that being said, please define old computer. please give cpu speed, amount of ram, and hard drive size. also understand xp is almost 10 years old. and designed to run on as little as 64mb of ram. ubuntu is a new operating system, with higher requirements than xp.

---

### Post by tgpraveen on 2008-11-14
pentium  4 2.4 Ghz
1.5 gb ram
internal hdd size 40gb 20 gb for ubuntu 20 for xp
pc around 5 yrs old
and the specs are greater than ubuntu min reqd specs
so..??

---

### Post by oilchangeguy on 2008-11-14
> **tgpraveen said:**
> pentium  4 2.4 Ghz
1.5 gb ram
internal hdd size 40gb 20 gb for ubuntu 20 for xp
pc around 5 yrs old
and the specs are greater than ubuntu min reqd specs
so..??

like i said 15 seconds is not that important. surely you have better things to do with your time, than to worry about 15 seconds.

and, where is it written that ubuntu WILL boot faster than xp?????????????

---

### Post by snowpine on 2008-11-14
Your boot times sound pretty normal to me; consistent with my experience on two different XP/Ubuntu dual-boot systems.

There are some good tips on these forums to speed up your boot time, though. :)

---

### Post by tgpraveen on 2008-11-14
true its not written anywhere

u know whatmy main concern is i love ubuntu a lot and can not see it go bloating and all
i mean 7.04 and 7.10 were much faster and responsive then 8.10 features cant come a t a price of performance else we will head for a ubuntu vista
so u understand my concern as the os matures it should not forget its core principles

---

### Post by prshah on 2008-11-14
> **tgpraveen said:**
> see the attached files and help me.

Well your system is booting into linux in a little over 31 seconds. Your chart looks fine.

That means that the balance 80 seconds is being lost in the loading of gdm and startup programs. Have you enabled autologin, or does that 1m50s include the time to complete user selection and password?

Now let's have a look at your /var/log/Xorg.0.log file.

---

### Post by tgpraveen on 2008-11-14
auto login enabled is there by any chance that network manager is causing the delay i have a feeling that the new version that shipped with this new version its the cause for half the probs.

when trying to upload the file i get an error

 Xorg.0.log:
Invalid File
Xorg.0.log.old:
Invalid File
Xorg.9.log:
Invalid File 

this error i get in the manage attachements window of this forum.

so what do i do next?

---

### Post by philinux on 2008-11-14
When I time intrepid with a stopwatch I get this

Grub to login = 30 secs.

Login to useable desktop =30 secs

However compiz or gnome hangs doing nothin for ~10 sec.

Turning off desktop effects stops the 10 second hang.

This vista laptop I'm on take over 3 minutes to get a useable desktop

---

### Post by prshah on 2008-11-14
> **tgpraveen said:**
> 
when trying to upload the file i get an error

Invalid File

so what do i do next?

The forum will not allow just any files to be uploaded. You should compress the file and load it here. Open a terminal (Applications-Accessories-Terminal) and ```
tar -cf ~/log.tar /var/log/Xorg.0.log 

``` This will create a "log.tar" file in your home directory. Upload this file here.

---

### Post by tgpraveen on 2008-11-14
here u r

hope that command didnt do any damage right i cant understand a thing of these cmds

---

### Post by tgpraveen on 2008-11-17
bump

---

### Post by prshah on 2008-11-17
> **tgpraveen said:**
> here u r


Looks fine. Maybe you need to check your autostarted programs and services. See System-Administration-Services and System-Preferences-Sessions and knock off any services/programs that you do not need.

You can also think about disabling Compiz, if you have it running. System-Preferences-Appearance-Visual Effects-None.

Or you can just live with it...

---

### Post by tgpraveen on 2008-11-18
k thx for ur help.

---

### Post by prshah on 2008-11-19
> **tgpraveen said:**
> 
but now i am feelinng that my boot time has gone up specifically it takes around 1:50 secs to boot into ubuntu 

I've recently found something that has made a dramatic improvement to my boot time: Take a look at my thread [Speed up your boot time upto 2X ! concurrency=shell works in Intrepid!]("http://ubuntuforums.org/showthread.php?t=987244")

Maybe this will help shave a lot of seconds off?

---

### Post by tgpraveen on 2008-11-19
sure will check it out

---

