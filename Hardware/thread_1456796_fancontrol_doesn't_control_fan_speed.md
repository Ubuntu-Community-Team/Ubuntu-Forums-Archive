---
title: "fancontrol doesn't control fan speed"
date: 2010-04-17
forum: Hardware
---

### Post by psyopper on 2010-04-17
So I've been working on quieting down my machine... i3-530 on a Gigabyte H55M-UD2H. Ubuntu 9.10, Kernel 2.6.33 from the PPA so that my onboard Intel video works properly (more importantly, doesn't crash).

lm_sensors 3.1.2 from the 10.04 repo's to actually detect my sensors, it8720-isa-0290 (3.1.1 in the 9.10 repo's wouldn't detect anything).

When I run pwmconfig it detects my two fans, one attached to the CPU_FAN header, and the other attached to the SYS_FAN header. Both fans are Nexus D12-SL12 1200 RPM 3 wire voltage regulated fans, not 4 wire PWM fans. pwmconfig can successfully control them:

```
$ sudo pwmconfig
# pwmconfig revision 5770 (2009-09-16)
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
   hwmon0/device is it8720

Found the following PWM controls:
   hwmon0/device/pwm1
   hwmon0/device/pwm2
   hwmon0/device/pwm3

Giving the fans some time to reach full speed...
Found the following fan sensors:
   hwmon0/device/fan1_input     current speed: 975 RPM
   hwmon0/device/fan2_input     current speed: 1104 RPM

Warning!!! This program will stop your fans, one at a time,
for approximately 5 seconds each!!!
This may cause your processor temperature to rise!!!
If you do not want to do this hit control-C now!!!
Hit return to continue: 

Testing pwm control hwmon0/device/pwm1 ...
  hwmon0/device/fan1_input ... speed was 975 now 286
    It appears that fan hwmon0/device/fan1_input
    is controlled by pwm hwmon0/device/pwm1
Would you like to generate a detailed correlation (y)? 
Would you like to generate a graphical plot using gnuplot (y)? 
    PWM 255 FAN 557
    PWM 240 FAN 379
    PWM 225 FAN 523 (probably incorrect)
    PWM 210 FAN 740 (probably incorrect)
    PWM 195 FAN 799 (probably incorrect)
    PWM 180 FAN 770 (probably incorrect)
    PWM 165 FAN 723 (probably incorrect)
    PWM 150 FAN 676 (probably incorrect)
    PWM 135 FAN 623 (probably incorrect)
    PWM 120 FAN 574 (probably incorrect)
    PWM 105 FAN 509 (probably incorrect)
    PWM 90 FAN 451
    PWM 75 FAN 392
    PWM 60 FAN 329
    PWM 45 FAN 222
    PWM 30 FAN 113
    PWM 28 FAN 0
    Fan Stopped at PWM = 28
    Hit return to continue...

  hwmon0/device/fan2_input ... speed was 1104 now 1102
    no correlation

Testing pwm control hwmon0/device/pwm2 ...
  hwmon0/device/fan1_input ... speed was 975 now 967
    no correlation
  hwmon0/device/fan2_input ... speed was 1104 now 485
    It appears that fan hwmon0/device/fan2_input
    is controlled by pwm hwmon0/device/pwm2
Would you like to generate a detailed correlation (y)? 
Would you like to generate a graphical plot using gnuplot (y)? 
    PWM 255 FAN 529
    PWM 240 FAN 528
    PWM 225 FAN 729 (probably incorrect)
    PWM 210 FAN 927 (probably incorrect)
    PWM 195 FAN 928 (probably incorrect)
    PWM 180 FAN 889 (probably incorrect)
    PWM 165 FAN 837 (probably incorrect)
    PWM 150 FAN 785 (probably incorrect)
    PWM 135 FAN 726 (probably incorrect)
    PWM 120 FAN 667 (probably incorrect)
    PWM 105 FAN 601
    PWM 90 FAN 537
    PWM 75 FAN 466
    PWM 60 FAN 396
    PWM 45 FAN 314
    PWM 30 FAN 175
    PWM 28 FAN 84
    PWM 26 FAN 0
    Fan Stopped at PWM = 26
    Hit return to continue...


Testing pwm control hwmon0/device/pwm3 ...
  hwmon0/device/fan1_input ... speed was 975 now 981
    no correlation
  hwmon0/device/fan2_input ... speed was 1104 now 1101
    no correlation

No correlations were detected.
There is either no fan connected to the output of hwmon0/device/pwm3,
or the connected fan has no rpm-signal connected to one of
the tested fan sensors. (Note: not all motherboards have
the pwm outputs connected to the fan connectors,
check out the hardware database on http://www.almico.com/forumindex.php)

Did you see/hear a fan stopping during the above test (n)? n

Testing is complete.
Please verify that all fans have returned to their normal speed.

```

So it appears that I do have positive control over the fans. If anyone is interested I can post screenshots from gnuplot. 

Here's the problem - no matter what kind of fan profile I configure in /etc/fancontrol the CPU_FAN throttles with CPU load and not against the cpu temp reported by sensors. The SYS_FAN always spins at 750 RPM, roughly 75% of it's rated speed. 

What can I do to positively take control of my fan speeds? 

I have tried a number of different things, it was just today that I fogured out the correlation between cpu load (NOT cpu temp) and the cpu fan speed.

---

### Post by psyopper on 2010-04-18
Well, I managed to get control back through fancontrol by disabling the CPU SmartFan control in the BIOS. The BIOS will then default all fans to 100% as a safety measure, but once I get into Ubuntu I can start fancontrol and get them back down to where I like them.

---

### Post by slickvguy on 2010-07-16
Just started playing around with lm-sensors, pwmconfig, & fancontrol. 

I have the same mobo. When I read your post, I thought "he must have PWM fans (4-pin) and not realize it". So I tried it myself. Son-of-a-gun... it works! I realize now that I was confused about a few things. 

This mobo has two fan headers: cpu and sys. The cpu header has the pwm pin but the sys fan header does not (pin 4 = 'reserved'). I have two fans: cpu fan (pwm) and rear case fan (3 pin). Up until now, I was using the 'cpu speedcontrol / auto' setting in the bios, and when monitoring the fan speeds, saw that when I stressed the cpu w/ prime or whatever, and the cpu temp went higher, so did the cpu fan speed. So far so good. But what confused me, is that the system fan also changed speeds (within a much narrower range) when the cpu temps would go up and down! (The system temps barely budged when I stressed for short periods of time, so I believe it's tied into the cpu temp - not the system temp).

This confused me, because although I knew that fans could be either voltage-controlled or PWM-controlled, I didn't think that the BIOS could and would do both methods to two different fans at the same time. Even when I changed the type of control to 'PWM' in the bios, it was still controlling the sys fan via pin 2. Would be nice if Gigabyte had documented this.  

Next...because of the name 'pwmconfig', I assumed that fancontrol couldn't control the sysfan's speed using pin 2/voltage - but now I happily see that it can. :) The values specified in the program (and config file) are weird, because they are supposedly 'pwm' values (not voltage), so I don't quite understand what that's about. Feel free to educate me. But fancontrol is definitely controlling BOTH of my fans. Oddly, both pwm1 AND pwm3 are linked to my cpu fan. While running pwmconfig, the curve was much smoother (and the values more consistent) using pwm3. Not sure why. Perhaps pwm1 is used for voltage control and pwm3 for pwm control of the cpu fan?

So glad that pwm2 can control my case fan (even though it's a 3-pinner!), and I finally got to see what the max rpms are of this fan (which the bios never came close to hitting). The bios was keeping the case fan speed too low (not sure what the algo is) which led to higher than normal case temps. Now I'm able to both quieten the &^%#$! stock heatsink's fan (until I replace the cooler) AND increase the 120mm system fan's speed in order to get better case cooling. Perfect.

lm-sensor doesn't seem to handle this mobo and it's IT8720F too well. Lots of weird stuff (especially w/ voltages). Also, w/ EIST etc. enabled, the cpu speed, voltage, and temps change a lot and start at much lower values than I would have expected. It's a relatively new system that I built, and I've never had a system where the idle cpu temp was (much) lower than the idle system temp (19C vs. 38C !) - so that threw me off a bit too.

Note for others who might make the same mistake: I ran into a bit of trouble w/ the /etc/fancontrol settings, which caused my fans to stop and alarms to go off each time I booted Ubuntu, which then forced me to turn off my pc quickly each time lest I fry my cpu. Not fun. But I used the 'recovery mode' from grub2's menu, root shell, and used nano to edit the file (I suppose I could have just renamed it or worst case use a 'liveusb'). 

I'm still not sure if the S20fancontrol symlinks were there the whole time, got put there when I installed lm-sensors (?), or was it when I ran pwmconfig or fancontrol? Would like to know.

Anyways...thanks for the original posts. They were the catalyst for good things! Sorry for the excessive length, but I wanted to help other GA-H55M-U2DH brothers who might go searching and hit upon this thread.

---

