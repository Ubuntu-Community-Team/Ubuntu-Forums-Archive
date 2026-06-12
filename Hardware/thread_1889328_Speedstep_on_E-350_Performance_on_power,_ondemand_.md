---
title: "Speedstep on E-350: Performance on power, ondemand on battery - How?"
date: 2011-12-01
forum: Hardware
---

### Post by Corporation on 2011-12-01
I've got an E-350 processor, and have installed the cpu speed indicator. I have to manually switch between performance (1.6GHZ) and ondemand when I switch from power to battery. How can I make the machine do it automatically?

I'm on 11.10.

---

### Post by Mark Phelps on 2011-12-01
Sorry, but there may be no way to do this under 11.10.  Have seen threads referencing a utility that claims to allow you to set the CPU speed -- but the site says this does not work under Oneiric.

Have heard claims about the CPU scaling bug in recent kernel versions that is causing some PCs to run hot in Oneiric.  Haven't seen anyone solve this yet.

---

### Post by Racecar56 on 2011-12-02
You can use cpufreqd for this.

Install cpufreqd:
```
sudo apt-get install cpufreqd
```
Then run this enormous command:
```
sudo sh -c "echo '# this is a comment
# see CPUFREQD.CONF(5) manpage for a complete reference
#
# Note: ondemand/conservative Profiles are disabled because
#       they are not available on many platforms.

[General]
pidfile=/var/run/cpufreqd.pid
poll_interval=2
verbosity=4
[/General]

[Profile]
name=On Demand
minfreq=20%
maxfreq=80%
policy=ondemand
[/Profile]

[Profile]
name=Performance
minfreq=100%
maxfreq=100%
policy=performance
[/Profile]

[Rule]
name=AC On
ac=on
battery_interval=0-100
profile=Performance
[/Rule]

[Rule]
name=AC Off
ac=off
battery_interval=0-100
profile=On Demand
[/Rule]' > /etc/cpufreqd.conf"
```
Then finally, another command:
```
sudo service cpufreqd reload
```

I'm not so sure if it will work, as I am not using Ubuntu right now, but it should.

---

