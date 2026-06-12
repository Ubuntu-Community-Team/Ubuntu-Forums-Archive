---
title: "P5Q asus mobo &amp; fancontrol / pwmconfig"
date: 2008-08-30
forum: Hardware
---

### Post by grigio on 2008-08-30
This mobo has a nice feature for powersaving called [six engine]("http://event.asus.com/mb/6engine/index.htm"). Is anybody able to use this feature on Linux? Or at least decrease the fan speed?

```
utente@utente-desktop:~$ pwmconfig 
This program will search your sensors for pulse width modulation (pwm)
controls, and test each one to see if it controls a fan on
your motherboard. Note that many motherboards do not have pwm
circuitry installed, even if your sensor chip supports pwm.

We will attempt to briefly stop each fan using the pwm controls.
The program will attempt to restore each fan to full speed
after testing. However, it is ** very important ** that you
physically verify that the fans have been to full speed
after the program has completed.

Found the following devices:
   hwmon0/device is coretemp
   hwmon1/device is coretemp
   hwmon2/device is w83627ehf

Found the following PWM controls:
   hwmon2/device/pwm1
   hwmon2/device/pwm2
   hwmon2/device/pwm3
   hwmon2/device/pwm4
There are no usable PWM outputs.
utente@utente-desktop:~$ sudo pwmconfig 
[sudo] password for utente: 
This program will search your sensors for pulse width modulation (pwm)
controls, and test each one to see if it controls a fan on
your motherboard. Note that many motherboards do not have pwm
circuitry installed, even if your sensor chip supports pwm.

We will attempt to briefly stop each fan using the pwm controls.
The program will attempt to restore each fan to full speed
after testing. However, it is ** very important ** that you
physically verify that the fans have been to full speed
after the program has completed.

Found the following devices:
   hwmon0/device is coretemp
   hwmon1/device is coretemp
   hwmon2/device is w83627ehf

Found the following PWM controls:
   hwmon2/device/pwm1
   hwmon2/device/pwm2
   hwmon2/device/pwm3
   hwmon2/device/pwm4
hwmon2/device/pwm4 is currently setup for automatic speed control.
In general, automatic mode is preferred over manual mode, as
it is more efficient and it reacts faster. Are you sure that
you want to setup this output for manual control? (n) 

Giving the fans some time to reach full speed...
Found the following fan sensors:
   hwmon2/device/fan1_input     current speed: 0 ... skipping!
   hwmon2/device/fan2_input     current speed: 2678 RPM
   hwmon2/device/fan3_input     current speed: 0 ... skipping!
   hwmon2/device/fan4_input     current speed: 0 ... skipping!
   hwmon2/device/fan5_input     current speed: 0 ... skipping!

Warning!!! This program will stop your fans, one at a time,
for approximately 5 seconds each!!!
This may cause your processor temperature to rise!!!
If you do not want to do this hit control-C now!!!
Hit return to continue: 

Testing pwm control hwmon2/device/pwm1 ...
  hwmon2/device/fan2_input ... speed was 2678 now 2657
    no correlation

No correlations were detected.
There is either no fan connected to the output of hwmon2/device/pwm1,
or the connected fan has no rpm-signal connected to one of
the tested fan sensors. (Note: not all motherboards have
the pwm outputs connected to the fan connectors,
check out the hardware database on http://www.almico.com/forumindex.php)

Did you see/hear a fan stopping during the above test (n)? 

Testing pwm control hwmon2/device/pwm2 ...
  hwmon2/device/fan2_input ... speed was 2678 now 2657
    no correlation

No correlations were detected.
There is either no fan connected to the output of hwmon2/device/pwm2,
or the connected fan has no rpm-signal connected to one of
the tested fan sensors. (Note: not all motherboards have
the pwm outputs connected to the fan connectors,
check out the hardware database on http://www.almico.com/forumindex.php)

Did you see/hear a fan stopping during the above test (n)? 

Testing pwm control hwmon2/device/pwm3 ...
  hwmon2/device/fan2_input ... speed was 2678 now 2678
    no correlation

No correlations were detected.
There is either no fan connected to the output of hwmon2/device/pwm3,
or the connected fan has no rpm-signal connected to one of
the tested fan sensors. (Note: not all motherboards have
the pwm outputs connected to the fan connectors,
check out the hardware database on http://www.almico.com/forumindex.php)

Did you see/hear a fan stopping during the above test (n)? 

Testing is complete.
Please verify that all fans have returned to their normal speed.

The fancontrol script can automatically respond to temperature changes
of your system by changing fanspeeds.
Do you want to set up its configuration file now (y)? y
What should be the path to your fancontrol config file (/etc/fancontrol)? y

Select fan output to configure, or other action:
1) Change INTERVAL     3) Save and quit
2) Just quit	       4) Show configuration
select (1-n): 4

Common Settings:
INTERVAL=10


Select fan output to configure, or other action:
1) Change INTERVAL     3) Save and quit
2) Just quit	       4) Show configuration
```

---

### Post by Penner on 2008-11-09
Your Motherboard can control fanspeed automatically: Enter BIOS go to Power then Hardware Monitor. Enable CPU Q-FAN Control and set CPU FAN Profile to Standard.

---

### Post by grigio on 2008-11-12
I know but I'd like to set it without rebooting everytime

---

### Post by blackpaw on 2008-11-23
ASUS also includes tools like "AI nap" that can bring the P5Q into a energy-saving state that (according to ASUS) only requires 10W of energy consumption... Would be neat to have that with Ubuntu.

Fan control via BIOS works like a charm! Super-silent system now :)

Basically all recent ASUS mainboards can control BIOS functions (overclocking, fan control, energy saving, etc.. from the OS, you can even upgrade the BIOS from the OS - however >> Windows only.. :(
I have contacted ASUS on this but I am not a developer..

---

### Post by Psykotik on 2009-02-20
Is there anything new, regarding this issue? Has someone found a bypass to get the same fan control as on windows?

---

### Post by Hazor on 2009-02-28
After finally finding this bit of information: [http://en.gentoo-wiki.com/wiki/Asus_P5Q-E#Hardware_Sensors](http://en.gentoo-wiki.com/wiki/Asus_P5Q-E#Hardware_Sensors)
Which enlightened me as to how to get the sensor chip on my P5Q SE Plus playing nicely with lm-sensors (The P5Q-E and P5Q SE Plus have the same Winbond sensor chip, it seems), I'm able to control the "chassis" fan (and I'm assuming "Power" fan also, but don't have anything plugged into it ATM to find out). The CPU fan, though, isn't taking orders, and right now it's running at a headache-inducing highest speed.
If you're using a different mobo your chip may already be supported properly (or possibly not at all), depending on your model, so you may not need to use that workaround I linked to.

First, disable Q-Fan control for each fan in the BIOS (except for the CPU fan, as I'm unable to control it - hence the aforementioned headache). Then, after booting and loading the module (if necessary for you), go to:
**/sys/class/hwmon/hwmon2/device**
(it might not be hwmon*2*. 0 and 1 are my two CPU cores. If you have a single- or quad-core (or maybe other sensor things) your number will probably be different, so just poke around until you find files named like fan1_alarm, fan1_div, etc. etc. ad nauseum.)

The files pwm1, pwm2, etc. are what control the fan speed, and they take numbers 0-255. The program pwmconfig will give you a correlation to RPM (you might have to run it as root). To find the current number on the first fan, use:
**cat pwm1**
To change its speed, use:
**sudo sh -c 'echo 150 > pwm1'**
The 150 you can change to your liking, between 0 and 255.

For my board, fan1 (i.e., fan1_input etc. and pwm1 etc.) is the "Chassis" fan, fan2 is  the CPU fan, and I'm assuming fan3 is going to be the "Power" fan. There is also fan4_* and pwm4* files there, and fan5_* files but no pwm5* files. My mobo only has 3 connectors though (CPU, "Power", and "Chassis"). So I'm assuming those files are are there simply because the chip has the ability to control 5(4?) fans.

For anyone interested, specifications on the P5Q SE Plus:
[http://usa.asus.com/products.aspx?modelmenu=2&model=2561&l1=3&l2=11&l3=709&l4=0](http://usa.asus.com/products.aspx?modelmenu=2&model=2561&l1=3&l2=11&l3=709&l4=0)

Now I'm going to go turn Q-Fan control back on for the CPU fan before the noise of it running at 1600+ RPMs gives me a real headache. :X

Edit: Um. Kay. Now with Q-Fan re-enabled for the CPU fan I have to echo the speed to pwm2 in order to change fan1's speed, and that change is reflected in pwm1 while pwm2 still reflects the CPU fan's speed.. This is nonsense. =X
That is to say,
**sudo sh -c 'echo 100 > pwm1'** does nothing, but:
**sudo sh -c 'echo 100 > pwm2'** changes the content of pwm1 to 100, while pwm2 still reports the CPU fan's speed, which is 88 at the moment.

---

### Post by grigio on 2009-04-26
Are there improvements in Jaunty?

---

### Post by tnttrx on 2009-12-04
Are there any improvements in Karmic?

---

### Post by grigio on 2009-12-30
any news about how to control the fan speed via (Software) Linux?

---

### Post by grigio on 2010-08-22
up

---

### Post by tnttrx on 2010-08-22
I have Asus P5Q Premium mobo. It has 5 fan headers:
1x CPU FAN
3x Chassis FAN
1x Power FAN

I'm using Gentoo amd64 with kernel 2.6.34-gentoo-r3, but guess there's no big difference for Ubuntu.

CPU FAN is controled by BIOS and cannot be controled by lm_sensors.
Chassis FANs can be conntroled by changing pwm, but echoing value in
pwm2 changes ALL 3 Chassis FANs.
Power FAN cannot be controled.

So, I've connected both CPU and system FAN to Chassis FAN headers.
Using lm_sensors and fancontrol, I was able to make config file that
would monitor just one temperature and set all fans accordingly.

I wanted to monitor both Motherboard and CPU temperature, so I've made
changes to fancontrol script. It is not pretty, it isn't useable for
general population and _it_controls_just_one_pwm_ (and that one pwm should control all 3 Chassis FANs on P5Q Premium), but I still decided
to post it here just in case someone needs something similar.

What I've done:
1. removed setting of pwm at the end of the loop in function UpdateFanSpeeds
2. added one variable to "remember" biggest pwm calculated during all
runs through the loop
3. set the biggest value to pwm output once we've finished all runs
through the loop

That way, if CPU is too hot, fans will be set by CPU sensor. If case sensor reports too high temperature, fans will be set according to this sensor. Highest PWM value is used each time.

```
--- fancontrol.original 2010-01-28 20:13:18.837213507 +0100
+++ fancontrol.v0.1     2010-01-28 20:13:46.227212974 +0100
@@ -254,6 +254,7 @@
 # main function
 function UpdateFanSpeeds {
       let fcvcount=0
+       let biggestpwm=0
       while (( $fcvcount < ${#AFCPWM[@]} )) # go through all pwm outputs
       do
               #hopefully shorter vars will improve readability:
@@ -326,18 +327,21 @@
                       wait $!
                 fi
               fi
-               echo $pwmval > $pwmo # write new value to pwm output
-               if [ $? -ne 0 ]
-               then
-                       echo "Error writing PWM value to $DIR/$pwmo"
-                       restorefans 1
-               fi
-               if [ "$DEBUG" != "" ]
-               then
-                       echo "new pwmval=$pwmval"
+               if (( $biggestpwm < $pwmval ))
+                   then biggestpwm=$pwmval
               fi
               let fcvcount=$fcvcount+1
       done
+       echo $biggestpwm > ${AFCPWM[0]} # write the biggest pwm value to
pwm output
+       if [ $? -ne 0 ]
+       then
+               echo "Error writing PWM value to $DIR/$pwmo"
+               restorefans 1
+       fi
+       if [ "$DEBUG" != "" ]
+       then
+               echo "new pwmval=$biggestpwm"
+       fi
 }

 echo 'Enabling PWM on fans...'
```

---

### Post by Anubis on 2010-11-01
I have three of these boards. Why on earth would you turn off qfan? I have no issues such as these. Why would I even want to have to control my fan speeds manually?

---

### Post by tnttrx on 2010-11-01
> **Anubis said:**
> I have three of these boards. Why on earth would you turn off qfan? I have no issues such as these. Why would I even want to have to control my fan speeds manually?

because I want to speed-up my case fans when CPU starts to get hot, too, even if mobo sensor is still pretty cold.

---

### Post by grigio on 2011-10-27
are there news about how to control the fans via software (not BIOS)?

---

### Post by malteworld on 2012-12-22
> **grigio said:**
> any news about how to control the fan speed via (Software) Linux?

I dug around on that issue a while ago: In a bug report the developer of lm_sensors made a user run a few tests and concluded, there is nothing he can do, because the sensor chip firmware is broken (it writes to the wrong addresses internally).
If you are intersted in details, I can probably find that bug report again.

---

### Post by howefield on 2012-12-22
Old thread back to sleep.

---

