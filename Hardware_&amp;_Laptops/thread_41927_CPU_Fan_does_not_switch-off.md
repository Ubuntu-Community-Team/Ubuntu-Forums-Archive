---
title: "CPU Fan does not switch-off"
date: 2005-06-15
forum: Hardware &amp; Laptops
---

### Post by zz9ian on 2005-06-15
Hi,
    I have a compaq presario 720ap. I recently switched from debian sid to ubuntu (5.04). Everything seems to work perfectly fine (autodetect), except a problem that I had in sid persists in ubunu too. My CPU fan, once it starts, does not switch-off (the base of my laptop gets really hot - I can feel it when I touch it). The fan switches off fine in Windows-XP. Was wondering if anyone faced this problem and could suggest solutions or debugging tips.

Thanks.

---

### Post by bigbangbigbigbang on 2005-06-15
Is frequency scaling (powernowd) working?

---

### Post by mekanzoo on 2005-06-15
it happends to me too.... 
I have Fujitsu Lifebook E4010, it runs very hot.
I think powernowd is running.

---

### Post by zz9ian on 2005-06-15
Hi powernowd seems to be working 

root@vhost:/proc/acpi/battery/BAT0 # pgrep powernowd
6759

# ps -ef | grep powernowd
root      6759     1  0 20:36 ?        00:00:00 /usr/sbin/powernowd -q
root     12233  7171  0 21:07 pts/0    00:00:00 grep powernowd

The funny thing is /proc/acpi/fan has no files - I saw a friends machine an it had a file with some values indicating on or off in it.

What would you recommend that I use to monitor the temperature and acpi related params? gkrellm?

Thanks.

---

### Post by Odisej on 2005-06-18
Exactly the tread I was looking for. I have a Presario 723ea and haw installed Ubuntu recently. I too have a problem of fans being constantly on and I am searching for a solution to this problem. I am a tota newbie so all the information I will write is pure guessing.

My thoughts are that Powernow is working ok (this model comes with AMD Duron). When checking on the status of the processor it is at it's lower speed. The AMD processor is know to heat up but I do not experience the same constant fan on situation with Windows. Especially not after installing relevant VIA 4in1 drivers. So the problem must be with the new OS I installed.

Because the computer is already a couple of years old there is a difference between the sounds of the CPU fan and the graphics card fan (the second fan; at least I think it is there).:) And I think the problem is not the CPU but the graphics card (S3 twister K also not known for its, let's say, performance). In windows the second fan would usually only turn on if using 3d graphics. In Ubuntu it is on even if there is no sign of 3d. 

Please, help us as I would wish to use Ubuntu but due to this phenomenon of noise I would probably not stick with it if the solution cannot be found.

Let me just add another useful information. A while ago I was experimenting with another Linux distribution called Pingo (it is based on Fedora Core 2). I formated the disc after having a million problems (which Ubuntu seems to have solved), i.e. connecting to the windows server and remote desktop, sound,... And I also seem to remember that the fan problem was not there! I remember ACPI support with profiles was in the beta phase but it was still working as it should. I do not remember the name of the module nor anything else.:) Maybe somebody may explain this.

Thank you for your help. I really hope we can solve this as I am fascinated by Ubuntu.

Regards,

Odisej

---

### Post by keithpeter on 2005-06-18
Hello all

Very timely thead this one!

I'm running ubuntu on a small Dell L400 notebook (few years old, Pentium 3 700Mhz processor, APCI modules appear to be running, Powernowd does not appear to be present)

Under windows the fans cut in when the laptop gets warm and then slow down and cut out.

Under ubuntu, the situation is more complex. If I re-boot into Ubuntu after a Windows session and one of the fans is running, it stays running. If I boot into ubunto cold, the fan never comes on and after an hour or so the cpu temperature gets to 69 deg C.

The following 'proc' entries exist (among others)

/proc/acpi/thermal_zone/THRM/polling_frequency
/proc/acpi/thermal_zone/THRM/cooling_mode
/proc/acpi/thermal_zone/THRM/trip_points
/proc/acpi/thermal_zone/THRM/temperature
/proc/acpi/thermal_zone/THRM/state
/proc/acpi/processor/CPU0/power
/proc/acpi/processor/CPU0/limit
/proc/acpi/processor/CPU0/throttling
/proc/acpi/processor/CPU0/info
/proc/acpi/fan/FAN1/state
/proc/acpi/fan/FAN0/state

Having checked some values, I came accross this.....

keith@ubuntu:/$ cat /proc/acpi/thermal_zone/THRM/polling_frequency
<polling disabled>

Is it possible that Ubuntu is reading the starting state of the computer and then not updating? And how do I get it to poll the machine state properly?

Any pointers gratefully received  ](*,)

---

### Post by Odisej on 2005-06-19
An update: 

I wanted to do a small test and I uninstalled Ubuntu and installed Fedora Core 4. The effect was the same. Fans kept blowing even if I did not do any intensive tasks. Well, I decided to follow my idea about the graphics card and decided to change the driver I used from S3 ProSavage KN133 to S3 Savage4 (generic). The fans actually turned off although only once for now. I do not have much time these days to keep testing but I suggest you try the same maybe this could be a solution in Ubuntu. It is true that the driver I use now does not support 3d acceleration. I am not sure if KN133 does anyway.

Well, just a thought.

Odisej

---

### Post by snop on 2005-06-20
Hi,

Frequency scaling wasn't working for me either. I solved this loading the module "acpi_cpufreq":

```
sudo modprobe acpi_cpufreq
```

SnOp

---

### Post by pestilence4hr on 2005-06-22
[QUOTE=keithpeter]
Having checked some values, I came accross this.....

keith@ubuntu:/$ cat /proc/acpi/thermal_zone/THRM/polling_frequency
<polling disabled>

Is it possible that Ubuntu is reading the starting state of the computer and then not updating? And how do I get it to poll the machine state properly?
[/QUOTE]

I am having this exact same problem on my Gateway 450 laptop.  I found the solution at [this page.](http://www.piratehaven.org/~mike/index.cgi?gateway#Turning%20off%20the%20Fan) That script may not work for you (it didn't work for me right away), but a little editing fixed it:



```
function reset_trip_points
{
  if [ -f /proc/acpi/thermal_zone/THRM/trip_points -a -f /proc/acpi/thermal_zone/THRM/polling_frequency ]
  then

    ifs=$IFS
    IFS=" "
    for i in `cat /proc/acpi/thermal_zone/THRM/trip_points`
    do
      j="${i%% C*}"
      j="${j##* }"
      i=${i%%[ :]*}
      i=${i//[][]/}
      case "$i" in
        critical|hot|passive|active0|active1)
          eval "[ \"x\$$i\" = x0 ] && $i=\$j"
          ;;
      esac
    done
    IFS=$ifs

    echo $critical:$hot:$passive:$active0:$active1 > /proc/acpi/thermal_zone/THRM/trip_points 

    # Activate the kernel's temperature control system
    echo 30 > /proc/acpi/thermal_zone/THRM/polling_frequency 

    # It's safe to turn the fan off now.
    echo -n 3 > /proc/acpi/fan/FAN0/state
  fi
}

# Set the new value for the temperature you would like to change, or leave it
# at zero to get the default.
critical=93
hot=93
passive=92
active0=72
active1=50

# Make the Kernel handle CPU temperature management.
# Do this before the filesystem checks so that the fan will turn off and stop
# draining the battery.
reset_trip_points

```

The main thing that I changed was setting the temperatures (I think the parsing of the default values is broken).  They may need to be different for your machine, and note that they are in celsius.  Here's how you can get it working on startup.  Copy the contents of this script into a file called /etc/init.d/acpi-fans.  Then execute the following commands:
```

sudo chmod u+x /etc/init.d/acpi-fans
update-rc.d acpi-fans defaults 21
```

Hopefully this will fix your problem.  It fixed mine.

---

### Post by pestilence4hr on 2005-06-22
[QUOTE=keithpeter]
keith@ubuntu:/$ cat /proc/acpi/thermal_zone/THRM/polling_frequency
<polling disabled>
[/QUOTE]

I should also mention that if this is your only problem, the following is all that is needed to fix it (the above script will accomplish that, as well as allow you to set the temperature you would like the fan to kick on):
```

sudo -s
echo 30 > /proc/acpi/thermal_zone/THRM/polling_frequency
exit
```

---

### Post by keithpeter on 2005-06-22
[QUOTE=pestilence4hr]I should also mention that if this is your only problem, the following is all that is needed to fix it (the above script will accomplish that, as well as allow you to set the temperature you would like the fan to kick on):
```

sudo -s
echo 30 > /proc/acpi/thermal_zone/THRM/polling_frequency
exit
```[/QUOTE]

Many thanks for this - it appears to be working!

The current trip points on this Dell Latitude L400 with the 700 Mhz coppermine processor are set as follows

keith@ubuntu:~$ cat /proc/acpi/thermal_zone/THRM/trip_points
critical (S5):           99 C
passive:                 90 C: tc1=2 tc2=3 tsp=40 devices=0xcffee480
active[0]:               80 C: devices=0xcffeee40
active[1]:               65 C: devices=0xcffeeec0

and having issued the following command in a terminal window, the 'small' fan is cutting in around 65.

This laptop runs warm under Windows ME as well, so I'll try the script to set the trip
temparatures a bit lower over the weekend.

PS - can anyone recommend an 'overview' to the way hardware is handled and what
the /proc/ volatile variables do? I'd like to get my head around this a bit more

Cheers

---

### Post by keithpeter on 2005-06-23
[QUOTE=pestilence4hr]I should also mention that if this is your only problem, the following is all that is needed to fix it (the above script will accomplish that, as well as allow you to set the temperature you would like the fan to kick on):
```

sudo -s
echo 30 > /proc/acpi/thermal_zone/THRM/polling_frequency
exit
```[/QUOTE]

OK - newbie alert - how do I make this change permanent so it loads at the beginning of each session?

Just point me to a how-to as I need to learn this stuff

cheers

---

### Post by Odisej on 2005-06-27
An update: I have been using Fedora Core 4 for a week now. I am reporting that everything is working as it should on my Presario 723EA notebook. You may ask what does this have to do with Ubuntu... well, I am not sure if the same may be happening with Debian based Linux but it is worth trying:

 zz9ian: do you have your battery in the laptop when using Ubuntu? i noticed that the computer acts much more normally when it is inserted. Maybe you should try it too and report if that is the case with your system as well.

The idea of editing the acpi files in folders does not work on my laptop as the files are not there at all.

Odisej

---

### Post by bluebuzzard on 2005-07-01
I have the same problem on my Acer TM 240 with the fan running almost continually. Powernow is running ok but I don't have a THRM folder in /proc/acpi/thermal_zone  on my system, instead I have 2 folders THRC and THRS. I tried using the above script for both of these but it had no effect. Any suggestions anyone?
Thanks.

---

### Post by pestilence4hr on 2005-07-29
[QUOTE=keithpeter]OK - newbie alert - how do I make this change permanent so it loads at the beginning of each session?

Just point me to a how-to as I need to learn this stuff

cheers[/QUOTE]

What I did was add the script to /etc/init.d and then used update-rc.d to add it to system startup (make sure you chmod u+x the script).  tldp.org is a good place to go to learn more.

---

### Post by pestilence4hr on 2005-07-29
[QUOTE=Odisej]An update: I have been using Fedora Core 4 for a week now. I am reporting that everything is working as it should on my Presario 723EA notebook. You may ask what does this have to do with Ubuntu... well, I am not sure if the same may be happening with Debian based Linux but it is worth trying:
[/QUOTE]

I'm pretty sure it's a bug in the acpi modules that is specific to the ubuntu kernel that is in Hoary.  My fans worked fine in Warty, and also in Debian (sarge before it was released).  It's probably about time for a bug report.

---

### Post by pestilence4hr on 2005-07-29
[QUOTE=bluebuzzard]I have the same problem on my Acer TM 240 with the fan running almost continually. Powernow is running ok but I don't have a THRM folder in /proc/acpi/thermal_zone  on my system, instead I have 2 folders THRC and THRS. I tried using the above script for both of these but it had no effect. Any suggestions anyone?
Thanks.[/QUOTE]

I don't *think* it matters that you don't have a THRM folder, this is just a temperature probe that may be specific to certain hardware.  The thing that should indicate whether or not my fix will work for you is if issuing "cat /proc/acpi/thermal_zone/THRC/temperature" or "cat /proc/acpi/thermal_zone/THRS/temperature" when the temperature is below the lowest trip point causes the fan to stop.

---

### Post by adityanag on 2005-08-28
Ok, I have an IBM T43, and my fan is on all the time. I have a /proc/acpi/fan folder, but there are no files in it. Other people have FAN0/state and FAN1/state depending on the number of fans in the machine. 

The script in this thread uses a command  "echo -n 3 > /proc/acpi/fan/FAN0/state" to turn off the fan when not needed. But I don't have this file!!!

How do I monitor the fan on my machine? I have gone through the /proc/acpi directory, and while I can get my system temperature, cpu state, battery info ( for both my batteries) and all that, I can't seem to find a fan state variable.

My system temperature is always around 48-55 C, and powernowd works fine. CPU speed scaling is also working fine. The only problem is the constant noise of the fan, and the hit on battery life..

Any help on modding the script for a T-43 would be appreciated..

---

### Post by zealubuntu on 2005-09-12
[QUOTE=adityanag]Ok, I have an IBM T43, and my fan is on all the time. I have a /proc/acpi/fan folder, but there are no files in it. Other people have FAN0/state and FAN1/state depending on the number of fans in the machine. 

The script in this thread uses a command  "echo -n 3 > /proc/acpi/fan/FAN0/state" to turn off the fan when not needed. But I don't have this file!!!

How do I monitor the fan on my machine? I have gone through the /proc/acpi directory, and while I can get my system temperature, cpu state, battery info ( for both my batteries) and all that, I can't seem to find a fan state variable.

My system temperature is always around 48-55 C, and powernowd works fine. CPU speed scaling is also working fine. The only problem is the constant noise of the fan, and the hit on battery life..

Any help on modding the script for a T-43 would be appreciated..[/QUOTE]

I got a T43 too. Now I am using Ubuntoo Breezy.  Everything is fine except the FAN.

I do not have the /proc/acpi/fan/FAN0 directory either.

Any suggestions?

Thanks.

---

### Post by lagerman on 2005-09-13
I did just as everything that was mentioned....And it worked!! But now I have a new problem. I have a Netgear wg511 wireless card. And now I have no internet connection. :-? Any body have any ideas????

---

### Post by AgenT on 2005-09-20
[QUOTE=lagerman]I did just as everything that was mentioned....And it worked!! But now I have a new problem. I have a Netgear wg511 wireless card. And now I have no internet connection. :-? Any body have any ideas????[/QUOTE]

Maybe you fried your NetGear card when turning off your fan? 

Not sure how changing your power state would affect your network card? What exactly did you do and what is your laptop?

Also, I too am having problems where the fan status is not showing up. How does one control the fan without it?

---

### Post by lagerman on 2005-09-22
My network card is working now. All I did was restart my laptop. By the way it's a gateway 1450. Still new to linux but I am starting to like more and more everyday.
Thanks to this excellent community. :)

---

### Post by Panthios on 2005-10-01
What to do if my /proc/acpi/fan/ is empty??

---

### Post by decube on 2005-10-12
I have a Dell L400 also (running breezy), tried using the script without any luck :(
/proc/acpi/fan/ is empty.

---

### Post by AgenT on 2005-10-12
[quote=Panthios]What to do if my /proc/acpi/fan/ is empty??[/quote] 
Nothing. If it is empty it probably means it is supposed to be empty. If you read the posts above, this question was asked multiple times (by myself included). The answer it seems is that if it is empty, it should probably be empty. For example, some laptops do not allow fan control through the OS (like newer IBM Thinkpads) and so this directory will then be empty. This is actually done on purpose and the fan is controlled by the BIOS. Or, probably less likely, the (proc/kernel) system does not support control of the fan yet, in which case it will also be empty.

As to those that have the fan come on without shutting down and have an empty fan directory. You may have either 1) a "broken" laptop (BIOS is not controlling things right) or 2) not having your power saving features enabled (having the CPU run at full power the whole time which makes the heat sensors turn on the fan).

---

### Post by decube on 2005-10-13
I tried passing "acpi=off" to the kernel at boot, and that solved the problem.
The fan now operates as it should. Though I am a bit worried now something else wont work :)

---

### Post by AgenT on 2005-10-14
[quote=decube]I tried passing "acpi=off" to the kernel at boot, and that solved the problem.
The fan now operates as it should. Though I am a bit worried now something else wont work :)[/quote]

Strange since acpi should not be controlling the fan.

---

### Post by bereillyte on 2005-10-18
> Panthios said 
What to do if my /proc/acpi/fan/ is empty??

I too have an L400 and I do have the /proc files. A shot in the dark but it seems these "files" control the BIOS somehow. I recently updated my DSDT since the L400's is faulty and suspending started to work correctly. Since the DSDT also defines amongst other things how the Fans work, I wonder if that is wat you need to do

Providing a replacement DSDT appears to be tricky, but once you have gone through each step, it seems easy afterwards :-) 

The process is described in [here]("https://wiki.ubuntu.com/ACPIBattery")

---

### Post by mb2k on 2005-10-19
I would just queue up in the row of Thinkpad T42 users with that damn annoying fan sound all the time.

Why is the fan quiet under Windos 2000/ XP, and not under ubuntu/kubuntu ?

When the FAN would be only BIOS controlled, than why does it work under Windows and not in Linux ?

CPU Freq changing works great - 600mhz till 1.7ghz.

Does any body have tried to just "touch" the needed Fan files, and echoed them ?

This is really a mess, as this might going to be the reason for not switching to Linux on my mobile .... I HATE NOISE !

Thx 4 helping...:rolleyes:

---

### Post by AgenT on 2005-10-19
While your laptop may be an exception, the information that the BIOS controls the fan comes directly from IBM/Lenovo.

What you can easily do is call Lenovo and ask and then you will have a better idea on how to go about fixing this problem.

---

### Post by pirast on 2005-12-25
Guys, I need your help!

I just got a laptop, a Fujitsu Siemens Amilo Pro V2030. Everything works fine - excepting the fan. I tried everything that was mentioned in this thread but the fan does not stop. In Windows XP (I installed it because I wanted to test if the fan stops there) the fan switches off.

Please help me, I am really distressed.

Here are some pieces of information:

> sh-3.00# cd /proc/acpi/thermal_zone/THRM
sh-3.00# dir
cooling_mode  polling_frequency  state  temperature  trip_points
sh-3.00# cat polling_frequency
polling frequency:       30 seconds
sh-3.00# cat state
state:                   ok
sh-3.00# cat cooling_mode
cooling mode:   active
sh-3.00# cat temperature
temperature:             44 C
sh-3.00# cat trip_points
critical (S5):           110 C
passive:                 78 C: tc1=3 tc2=1 tsp=80 devices=0xcb9e17c0
active[0]:               60 C: devices=0xcbe9a8a0
sh-3.00#


> sh-3.00# echo  -n 3 > /proc/acpi/fan/FAN/state
sh-3.00# cat /proc/acpi/fan/FAN/state
status:                  on


Directory structure of /proc/acpi:

> 0       /proc/acpi/video/VGA/LCD
0       /proc/acpi/video/VGA/CRT
0       /proc/acpi/video/VGA
0       /proc/acpi/video
0       /proc/acpi/wmi
0       /proc/acpi/sony
0       /proc/acpi/hotkey
0       /proc/acpi/button/lid/LID
0       /proc/acpi/button/lid
0       /proc/acpi/button/power/PWRB
0       /proc/acpi/button/power/PWRF
0       /proc/acpi/button/power
0       /proc/acpi/button
0       /proc/acpi/battery/BAT0
0       /proc/acpi/battery
0       /proc/acpi/ac_adapter/ACAD
0       /proc/acpi/ac_adapter
0       /proc/acpi/thermal_zone/THRM
0       /proc/acpi/thermal_zone
0       /proc/acpi/processor/CPU0
0       /proc/acpi/processor
0       /proc/acpi/fan/FAN
0       /proc/acpi/fan
0       /proc/acpi/power_resource/PFAN
0       /proc/acpi/power_resource
0       /proc/acpi/embedded_controller
0       /proc/acpi


Thanks a lot,
Martin

---

### Post by Hezekiah on 2005-12-31
This may not be of much immediate assistance, but I have found SUSE 10.0 to be much better than (K)Ubuntu at keeping my laptop (Sony Vaio VGN-S260, 1.7ghz Centrino) cool and minimizing fan noise.  I'm not sure of the exact reason, but I imagine it has something to do with the power management software used - powernowd in Ubuntu and, I think, powersaved in SUSE.

This is a little frustrating, as I would prefer using Gnome and greatly prefer Ubuntu's Gnome setup to SUSE's.  However, as mentioned earlier in this thread, heat and noise can be a big concern on a laptop, so for the time being I think I'll be suffering through with SUSE on there and just keep Ubuntu for my desktop system where frequency scaling isn't really an issue.

I hope this helps somewhat.  It looks like Dapper will have powersaved in the universe repository, so perhaps something can be made to work there when the time comes.

---

### Post by pirast on 2005-12-31
Hi,
thanks for the tip! I tried OpenSuSE ~ 7 days ago and I found out that my fan switches off / is being controlled, too but only after I suspend. Suspend doesn't work in Ubuntu for me. But I feel that Opensuse with Gnome is a little bit slower at my laptop (190MB Ram) than Ubuntu.


Thank you for your reply,
Martin

---

### Post by Brando569 on 2006-01-08
i built my desktop myself and am using an Asus P4C800-E mobo and a P4 3.2ghz processor and when i go to start powernowd it says this "CPU frequency scaling inst supported." is this a hardware or software problem? also most all of the directories in /proc/acpi are empty :( these are the directories that i have empty:

embedded_controller
fan
power_resource
sony
thermal_zone
video
wmi

anyone know if there is any fix for this?

---

### Post by phidippus on 2006-01-13
I'm using Toshiba Tecra M3 and am having the fan noise problem. The CPU dynamics is controlled quite well, but fan stays constant high. I tried

sudo -s
echo 30 > /proc/acpi/thermal_zone/THRM/polling_frequency
exit

but there was no change. I looked at cooling_mode file and

cat /proc/acpi/thermal_zone/THRM/cooling_mode
<setting not supported>
cooling mode:   critical

Is this a problem?

---

### Post by mättu on 2006-09-05
Here's what I found out:
On my laptop (+-4 years old Compaq Evo800n) the fan almost never stops on ubuntu with acpi. WinXP: Very silent. 
Ubuntu with APM: Very silent, but no hiberation / suspend..
I should add that the fan is turned on during the BIOS-Screen an turns off as soon as WinXP / LinuxAPM has finished loading.

So i did:

cat /proc/acpi/thermal_zone/TZ1/trip_points
->
Trip points are at 40, 47 ... degree C

cd /proc/acpi/thermal_zone/TZ1
cat temperature state
showed approx 42-45 C and state: ok (for silent) at startup while it should be active[3] for the fans actual state (cooling at lowest rate)..

Now I did acpi-listen in a second terminal to see what happens when the 40C trip-point is passed.
acpi-listen showed NO message and the fan remained on, even at 38C or below.

Brute-force: Let our CPU do some work, until it reaches 57C, which takes about 40 sec. in my case. This can be done for example by some very simple perl program:
#! /usr/bin/perl
$e++ while(1);

I fired it up in a third terminal, let it do its work an checked 
cat temperature state every few seconds on terminal 1.

As soon as we reach 57C, terminal 2 (acpi-listen) displays a message concerning temperature.
I then shut down the silly perl program and wait, checking terminal 1 every few seconds for temperature & state. 
And as soon as we reach 40C, acpi-listen displays its message and the fan turns off!!
Now checking temp&state shows e.g.:
temperature:  39C
state:        ok

From this point on everything works fine. 

Helps?

What i am wondering about is if and how i could force a message to acpi (or some other concerned programs) to set the state of my fan corrctly at startup and if this would silence it when passing 40C. 

Greets 
:m)

---

