---
title: "overheating in ubuntu 11.10 on acer aspire 5750g"
date: 2011-11-05
forum: Hardware
---

### Post by avdmys on 2011-11-05
Hello,i use ubuntu 11.10 on my acer aspire 5750g

intel core i5-2410 2.3GHz
4GB RAM.
dual boot windows7 home premium and ubuntu.

i have no heating problems on windows7,but in ubuntu there is too much of heating my lm-sensors reading show

~# sensors
coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  **+61.0°C**  (high = +86.0°C, crit = +100.0°C)
Core 0:         **+61.0°C**  (high = +86.0°C, crit = +100.0°C)
Core 1:         **+58.0°C**  (high = +86.0°C, crit = +100.0°C)

After 5min of boot the touchpad,keybord,etc...starts getting heated.
The fan is running and making buzz at a considerable high speeds non-stop.
The battery life in ubuntu is 1hr40min whereas in windows7 it comes to 4hrs15min.

---

### Post by diasf on 2011-11-05
cpufreqd

---

### Post by avdmys on 2011-11-05
thanks  for the reply,
i installed cpufreqd........but did not do any good instead the cpu which was scaling the frequency on its own stopped and is constantly running 2.3GHz and the readings in lm-sensors are between 60°C-70°C........
so i removed the cpufreqd using apt-get remove cpufreqd.(but the heating still exists as before).

Thanks.

---

### Post by diasf on 2011-11-05
Well, the program by itself, not configured, won't do any good.
First, make sure it's on the "ondemand" governor, not conservative. Then you might consider customizing the cpufreqd.conf. The deamon is quite powerful, for instance I use it to "fix" a cooling problem in my laptop (flawed by design), making it never pass 75C, with considerable performance loss, but works... It can consider processing porcentage, battery porcentage, applications running and so on....

---

### Post by avdmys on 2011-11-05
I am using ubuntu from about 2 months or so.......i am still a beginner with Linux......so please help me in configuring the cpufreqd.conf.

First, the reason i said that cpu is not scaling freq is by:

~# cat /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_cur_freq 
2301000

cpu stays at this freq forever when cpufreqd is installed but when the cpufreqd is not installed the freq will be 800000 or 800MHz most of the time ,also it changes to higher freq when an extra processes is run....this is how i recognized that cpu is not scaling.I have checked it couple of times before posting.

so,looks like we need to configure the cpufreqd.conf.

Thanks.

---

### Post by avdmys on 2011-11-07
this is my current cpufreqd.conf.
# this is a comment
# see CPUFREQD.CONF(5) manpage for a complete reference
#
# Note: ondemand/conservative Profiles are disabled because
#       they are not available on many platforms.

[General]
pidfile=/var/run/cpufreqd.pid
poll_interval=2
verbosity=4
enable_remote=1
#remote_group=root
[/General]

#[acpi]
#acpid_socket=/var/run/acpid.socket
#[/acpi]

#[nforce2_atxp1]
#vcore_path=/some/path
#vcore_default=1500
#[/nforce2_atxp1]

#[sensors_plugin]
#sensors_conf=/some/file
#[/sensors_plugin]

#[Profile]
#name=On Demand High
#minfreq=40%
#maxfreq=100%
#policy=ondemand
#[/Profile]
#
#[Profile]
#name=On Demand Low
#minfreq=20%
#maxfreq=80%
#policy=ondemand
#[/Profile]

[Profile]
name=Performance High
minfreq=35%
maxfreq=100%
policy=ondemand
#exec_post=echo 8 > /proc/acpi/sony/brightness
[/Profile]

[Profile]
name=Performance Low
minfreq=80%
maxfreq=80%
policy=performance
[/Profile]

[Profile]
name=Powersave High
minfreq=60%
maxfreq=60%
policy=powersave
[/Profile]

[Profile]
name=Powersave Low
minfreq=40%
maxfreq=40%
policy=powersave
[/Profile]

#[Profile]
#name=Conservative High
#minfreq=33%
#maxfreq=100%
#policy=conservative
#[/Profile]
#
#[Profile]
#name=Conservative Low
#minfreq=0%
#maxfreq=66%
#policy=conservative
#[/Profile]

##
# Basic states
##
# when AC use performance mode
[Rule]
name=AC Rule
ac=on                    # (on/off)
profile=Performance High
[/Rule]
 
# stay in performance mode for the first minutes
[Rule]
name=AC Off - High Power
ac=off                   # (on/off)
battery_interval=70-100
#exec_post=echo 5 > /proc/acpi/sony/brightness
profile=Performance Low
[/Rule]

# conservative mode when not AC
[Rule]
name=AC Off - Medium Battery
ac=off                   # (on/off)
battery_interval=30-70
#exec_post=echo 3 > /proc/acpi/sony/brightness
profile=Powersave High
[/Rule]

# conservative mode when not AC
[Rule]
name=AC Off - Low Battery
ac=off                   # (on/off)
battery_interval=0-30
#exec_post=echo 3 > /proc/acpi/sony/brightness
profile=Powersave Low
[/Rule]

##
# Special Rules
##
# CPU Too hot!
[Rule]
name=CPU Too Hot
acpi_temperature=55-100
cpu_interval=50-100
profile=Performance Low
[/Rule]

# use performance mode if I'm watching a movie
# I don't care for batteries! 
# But don't heat too much.
[Rule]
name=Movie Watcher
programs=xine,mplayer,gmplayer,vlc
battery_interval=0-100
acpi_temperature=0-60
cpu_interval=0-100
profile=Performance High
[/Rule]


the changes that i have made are in:
 (current)
[Profile]
name=Performance High
minfreq=35%
maxfreq=100%
policy=ondemand
#exec_post=echo 8 > /proc/acpi/sony/brightness
[/Profile]

(before)
[Profile]
name=Performance High
minfreq=**100%**
maxfreq=100%
policy=**performance**
#exec_post=echo 8 > /proc/acpi/sony/brightness
[/Profile]

after the changes the cpu in working ondemand mode......but that has made no changes to the heating, it is still over 60°C.......
but the fan is not running very fast now.....

---

### Post by diasf on 2011-11-07
That's the default cpufreqd.conf...
It shows everything that can be done with it, not very useful as operating conf....

What I did:
2 profiles/Rules:
* one ondemand 0% - 100% for when the processor is "cold", that is, temperature less than 70C (in my case)
* one ondemand 0% -50% for when it's more than 70C.

Actually, my .conf is slightly more complex, but I started there. Make your own conf, takes a while to understand the language, but it will solve your problem.

---

### Post by LinuxFan999 on 2011-11-07
This laptop is actually known to run hot, under any OS.

---

### Post by thatguruguy on 2011-11-07
Install Jupiter.  [Here's how]("http://www.webupd8.org/2011/09/jupiter-applet-finally-available-for.html").

Set your performance profile to "High Performance" or "Power Saver".

---

### Post by diasf on 2011-11-08
Power saver usually just keeps the processor on the lowest frequency.... you'll run cold and slow. I considered it for mine, but with cpufreqd I can control how hot i can let my machine get... afterwards I saw no reason to install jupiter...

---

### Post by fuduntu on 2011-11-08
> **diasf said:**
> Power saver usually just keeps the processor on the lowest frequency.... you'll run cold and slow. I considered it for mine, but with cpufreqd I can control how hot i can let my machine get... afterwards I saw no reason to install jupiter...

What about all of the other things Jupiter offers, like retuning your kernel when you unplug?

---

### Post by diasf on 2011-11-08
?

Just reviewed the documentation... nothing that's there has anything to do with what you said. (Matter of fact, doesn't make sense). Further, all the features it provides (for power management), I have on cpufreqd, so no point loading another application to do what the deamon does by itself. And the other non-power related features are totally irrelevant for me anyway.

---

### Post by avdmys on 2011-11-08
> **LinuxFan999 said:**
> This laptop is actually known to run hot, under any OS.

no,in windows the laptop does not heat up......but in ubuntu it is heating up and the windows gives battery backup about 2hr 30min more than what ubuntu does(i get only 1hr30min of backup in ubuntu and 4hr in windows).

---

### Post by gautam_jat on 2011-11-08
oh dont worry friend.Even i have the same configuration like u in my lenovo laptop.And even my keyboard and touchpad and area around it gets heated.I just found out two reasons for this by my experience and these are
1. when u use 11.04 inside window, i.e through wubi.
2. Unity desktop requires graphic card, so it may also have a heating effect.
3. 11.04 is unstable, and it has many stability and hardware issues, so i suggest u using 10.04 lts, as i myself switched to it and now there is no such heating problem.

---

### Post by fuduntu on 2011-11-08
> **diasf said:**
> ?

Just reviewed the documentation... nothing that's there has anything to do with what you said. (Matter of fact, doesn't make sense). Further, all the features it provides (for power management), I have on cpufreqd, so no point loading another application to do what the deamon does by itself. And the other non-power related features are totally irrelevant for me anyway.

It does make sense, I would know, I wrote it.

Tell me, how does cpufreqd disable nmi watchdog, or adjust dirty writeback centisecs for example when you unplug?

---

### Post by diasf on 2011-11-08
I didn't mean the documentation (It's rather incomplete then, didn't see anything like that), but the part "like retuning your kernel when you unplug" on your previous post.

And I needed something that wouldn't let my processor above 70C anytime (plugged or not)..... which is particularly good when your laptop has problematic cooling

---

### Post by fuduntu on 2011-11-08
> **diasf said:**
> I didn't mean the documentation (It's rather incomplete then, didn't see anything like that), but the part "like retuning your kernel when you unplug" on your previous post.

And I needed something that wouldn't let my processor above 70C anytime (plugged or not)..... which is particularly good when your laptop has problematic cooling

So are you saying it doesn't retune the kernel?  My post that you replied too gave two examples of parameters that it changes when you unplug.

As for documentation, it's on the website:

[b]Automatically tunes the kernel for AC or battery
Automatically tunes hardware for AC or battery[/b]

- [http://www.jupiterapplet.org](http://www.jupiterapplet.org)

It's also discussed on the wiki including documentation on how to add additional parameters to be tuned.

- [https://sourceforge.net/apps/mediawiki/jupiter/index.php?title=Main_Page](https://sourceforge.net/apps/mediawiki/jupiter/index.php?title=Main_Page)

CPUFreqd is just one of many things that Jupiter manages. ;)

---

### Post by diasf on 2011-11-08
Advertising aside, the question involved a laptop overheating. What anything does when you plug or unplug doesn't really matter, since it will overheat plugged or not, and cpufreqd is the best way, imo, to solve it. 

And AFAIK, jupiter doesn't have an option to maximize clock speed while keeping the processor under XX celsius, does it? That would be handy and way more useful than a shortcut to enable/disable bluetooth for instance (afaik there's a default icon for that on the bluetooth manager, default on lxde at least, don't remember unity). And the only way I know of doing that is with a customized cpufreqd.conf

And don't get me wrong, I looked up jupiter when I had the problem, nice initiative and all.... but honestly, it may be easy for you to find the help topics there, but for me it wasn't, not even now. Mostly of the pages I saw read more like advertising than technical help. A manpage like page would go a long way. Again, this is a constructive critic. If you disagree, ignore and move along. No point getting this thread more OT than this....

---

### Post by LinuxFan999 on 2011-11-10
> **avdmys said:**
> no,in windows the laptop does not heat up......but in ubuntu it is heating up and the windows gives battery backup about 2hr 30min more than what ubuntu does(i get only 1hr30min of backup in ubuntu and 4hr in windows).
Yes, this laptop is known to run hot.

Look here: [http://www.notebookcheck.net/Review-Acer-Aspire-5750G-Notebook.46094.0.html](http://www.notebookcheck.net/Review-Acer-Aspire-5750G-Notebook.46094.0.html)

Scroll down to where it says "Temperature". You can see that this laptop does run hot.

---

### Post by clementprem on 2011-11-12
Had the same problem 
here is the solution
follow this link

<http://www.techytalk.info/linux-kernel-2-6-38-2-6-39-power-regression-workaround/>

my cpu is cooler that ever b4 ;)

---

### Post by avdmys on 2011-11-18
everyone, my problem is almost solved:)........

1. i updated the bios.

2. in bios there is a option on disabling nVidia graphic card as i dont need it unless i am playing game in windows.so i set graphic mode in bios to integrated from switchable.

now when i am in ubuntu i get 3hr35min of battery and temp does not cross 52°C.
i think temp less than 52°C is not bad at all......at least for now considering how hot it was before:).

EDIT:the bios was updated from the acer website.

---

