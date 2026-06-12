---
title: "Getting HP ProBook 4530s silent, maybe DSDT patching?"
date: 2012-06-23
forum: Hardware
---

### Post by Pay87 on 2012-06-23
Hello,
I just bought a HP ProBook 4530s.
After installing the hybrid driver from ATI the notebook is very cool.
The only problem is, that the fan is still very loud.

So I read through a lot of forums and found a tool for controlling the fan, but it is for Windows only :(

[http://www.computerbase.de/forum/showthread.php?t=1070494](http://www.computerbase.de/forum/showthread.php?t=1070494)

Now I try to do something similar for the Ubuntu Community.
The problem is that fancontrol is not detecting the fans.
Also there is no acpi entry for the fans..

I thought maybe it is possible by doing a DSDT patch, but I don't know where to start here.

Does someone have an idea how to fix this?

---

### Post by Redblade20XX on 2012-06-23
Have you tried looking into the BIOS for any option on fan control? 

If so and you still haven't found any check this out for a start point:
[]("https://help.ubuntu.com/community/ACPIBattery")[https://help.ubuntu.com/community/ACPIBattery#The_DSDT_for_your_notebook](https://help.ubuntu.com/community/ACPIBattery#The_DSDT_for_your_notebook)

-Red

---

### Post by Pay87 on 2012-06-23
> **Redblade20XX said:**
> Have you tried looking into the BIOS for any option on fan control? 

If so and you still haven't found any check this out for a start point:
[]("https://help.ubuntu.com/community/ACPIBattery")[https://help.ubuntu.com/community/ACPIBattery#The_DSDT_for_your_notebook](https://help.ubuntu.com/community/ACPIBattery#The_DSDT_for_your_notebook)

-Red

Thanks for your reply.
I looked into the BIOS options and also updated it to the latest version.
There is only a setting to disable the fan when on AC, but this does not solve the problem.

I decompiled the DSDT table, but I was not able to find the parts where the fan levels are set up. Maybe someone who already did some DSDT modding knows more about where to find the right values?

I attached the DSDT table to the post. :KS

---

### Post by davidryderuk on 2012-06-25
Hi,

Have you tried installing lm-sensors so that you can monitor the temperature?

1. Install lm-sensors.

```
sudo apt-get install lm-sensors
```

2. Run a script to detect possible sensors.

```
sudo sensors-detect
```

3. Print off temperatures.

```
sensors
```

[https://help.ubuntu.com/community/SensorInstallHowto](https://help.ubuntu.com/community/SensorInstallHowto)

Have you found the embedded controller? Hopefully you'll be able to detect it with the lspci tool. 

```
sudo lspci -nn
```



[http://linux.die.net/man/8/lspci](http://linux.die.net/man/8/lspci)


p.s. I found another link describing how the program was written:

[http://forum.notebookreview.com/hp-business-class-notebooks/657013-hp-probook-4530s-fan-always-help-dsdt-editing-nhc-acpi-module.html](http://forum.notebookreview.com/hp-business-class-notebooks/657013-hp-probook-4530s-fan-always-help-dsdt-editing-nhc-acpi-module.html)

---

### Post by Pay87 on 2012-06-25
Thanks for your research.
I also found the thread you linked and contacted the guy but he don't know how fix things in Linux and actually a other guy wrote the tool for Windows..

"sudo lspci -nn" gives me:

```

00:00.0 Host bridge [0600]: Intel Corporation 2nd Generation Core Processor Family DRAM Controller [8086:0104] (rev 09)
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0126] (rev 09)
00:16.0 Communication controller [0780]: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 [8086:1c3a] (rev 04)
00:1a.0 USB controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 [8086:1c2d] (rev 04)
00:1b.0 Audio device [0403]: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller [8086:1c20] (rev 04)
00:1c.0 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 [8086:1c10] (rev b4)
00:1c.1 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 [8086:1c12] (rev b4)
00:1c.2 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 [8086:1c14] (rev b4)
00:1c.3 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 [8086:1c16] (rev b4)
00:1c.5 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 [8086:1c1a] (rev b4)
00:1c.7 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 8 [8086:1c1e] (rev b4)
00:1d.0 USB controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 [8086:1c26] (rev 04)
00:1f.0 ISA bridge [0601]: Intel Corporation HM65 Express Chipset Family LPC Controller [8086:1c49] (rev 04)
00:1f.2 SATA controller [0106]: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller [8086:1c03] (rev 04)
23:00.0 System peripheral [0880]: JMicron Technology Corp. SD/MMC Host Controller [197b:2392] (rev 30)
23:00.2 SD Host controller [0805]: JMicron Technology Corp. Standard SD Host Controller [197b:2391] (rev 30)
23:00.3 System peripheral [0880]: JMicron Technology Corp. MS Host Controller [197b:2393] (rev 30)
24:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
25:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
26:00.0 USB controller [0c03]: NEC Corporation uPD720200 USB 3.0 Host Controller [1033:0194] (rev 04)

```

And my sensors:
```

Adapter: Virtual device
temp1:        +58.0°C  (crit = +128.0°C)
temp2:         +0.0°C  (crit = +128.0°C)
temp3:        +37.0°C  (crit = +128.0°C)
temp4:        +51.0°C  (crit = +128.0°C)
temp5:        +31.0°C  (crit = +128.0°C)
temp6:         +0.0°C  (crit = +128.0°C)
temp7:         +0.0°C  (crit = +128.0°C)
temp8:         +0.0°C  (crit = +128.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +57.0°C  (high = +86.0°C, crit = +100.0°C)
Core 0:         +54.0°C  (high = +86.0°C, crit = +100.0°C)
Core 1:         +57.0°C  (high = +86.0°C, crit = +100.0°C)

```

---

### Post by davidryderuk on 2012-06-26
I thought that since they described how the program worked in the thread, it might be possible to find tools to do the same thing in Linux.

Interacting with the Embedded Controller (EC) mentioned in the thread seems more difficult in Linux. I don't know much about it. I wrongly assumed that you could see it over PCI :oops: 

I did find a site describing how to read and write to the EC register. You would have to write a large part of the program from scratch though, so that probably doesn't help. 

The other approach would be to reduce the heat as much as possible, but it sounds like you've already done that. If you haven't already, try switching to the integrated graphics card.

[http://ubuntuforums.org/showthread.php?t=1930450](http://ubuntuforums.org/showthread.php?t=1930450)

---

### Post by Pay87 on 2012-06-27
Yes it seems not to be a easy task on linux.
The DSDT think would be a easy thing, if someone would know which lines are for the fans..

Even the guys who made the fan program for Windows didn't find it out.
Maybe I find a solution, then I will post again.. :D

---

### Post by k3mpaxl on 2012-12-01
I got it working!
If you're interested in controlling your Probook 4530s Fan, contact me!

Greetz
k3mpaxl

---

### Post by Pay87 on 2012-12-01
> **k3mpaxl said:**
> I got it working!
If you're interested in controlling your Probook 4530s Fan, contact me!

Greetz
k3mpaxl

Why not just posting here for all? :P

---

### Post by k3mpaxl on 2012-12-26
my solution isn't that good, but i will share it:

[https://dl.dropbox.com/u/4537271/4530s.zip](https://dl.dropbox.com/u/4537271/4530s.zip)

1. install:
sensors
perl (or be able to run .pl files)

2. extract and modify:
- fanslow.sh: on line 2, adjust the path to probook_ec.pl

- open a terminal 
- change to directory containing probook_ec.pl
- run "chmod a+x *.pl" 

3. test the fancontrol
- change to directory containing probook_ec.pl
- run "sudo ./probook_ec.pl FANOFF" ( your fan should stop )
- run "sudo ./probook_ec.pl FANRST" ( to reset the embedded controller. your fan will start running again)
- run "chmod a+x *.sh"
- run "sudo ./fanslow.sh" (your fan will be throttled with my script now!)

4. adding to system startup
- edit /etc/rc.local and add:

## starts here
cd /path/to/my/FanControl/
./fanslow.sh >> /var/log/fanspeed &>> /dev/null
## ends here

now your system will boot up with a silent fan.


please post your questions in this topic, i'll answer them.

k3mpaxl

---

### Post by N00b-un-2 on 2012-12-26
> **Pay87 said:**
> I thought maybe it is possible by doing a DSDT patch, but I don't know where to start here.


HP 4530S...
DSDT patching...

Ubuntu != OSX

There is no equivalent to dropping a modified DSDT.aml into /Extra on Linux.  The only reason such workarounds exist on *that other * OS is because that functionality is purposefully built in to the Chameleon boot loader.

---

### Post by pieceofcake on 2012-12-30
I read the script fanslow.sh. You did a great job !

On my ProBook 4330s, I am using "/sys/class/hwmon/hwmon1/device/temp1_input" instead of "sensors", it seems to cost less cpu.

---

### Post by k3mpaxl on 2013-01-01
> **pieceofcake said:**
> I read the script fanslow.sh. You did a great job !

On my ProBook 4330s, I am using "/sys/class/hwmon/hwmon1/device/temp1_input" instead of "sensors", it seems to cost less cpu.

Hi pieceofcake,
you're right. 

for those who receive a cpu temp value by running "tail /sys/class/hwmon/hwmon1/device/temp1_input | cut -b1-2", you can change line 28 of fanslow.sh:

#from:
    TMP=$(sensors | grep Physical | cut -b 18-19)

#to
    TMP=$(tail /sys/class/hwmon/hwmon1/device/temp1_input | cut -b1-2)

happy silent new year :-)

k3mpaxl

---

### Post by vickoxy on 2013-02-26
So how silent or loud is the fan under normal load (web surfing, office apps...)? Can you adjust temps and fanspeed (e.g. make it switch at 50C?)
Thanks!

---

### Post by k3mpaxl on 2013-02-26
> **vickoxy said:**
> So how silent or loud is the fan under normal load (web surfing, office apps...)? Can you adjust temps and fanspeed (e.g. make it switch at 50C?)
Thanks!

hi vickoxy,

i'm using ubuntu 12.04 on my probook 4530s for several month now. With my FanControl-Script, your system will be as silent as you hard drive is. It means: the fan will be off under 55°C. (If you're using a SSD your system will be noiseless!)

You can configure your temperatures by youself. I would recommend my settings like i distributed them in my dropbox link. Please set the setting "Fan always on on AC" to off in your system bios to gain full noise reduction. :)

I've got a HD3000 and a Radeon 6490M grafics card in my probook. if you're using a similar system, please make sure, you've got the driver installed and set the integrated grafic.

k3mpaxl

---

### Post by vickoxy on 2013-03-02
Need help here. I bought actually one Hp 2540p. And no pwm fancontrol. But i tried scripts (.sh) posted here, and they are partially working.
E.g.
```
sudo ./probook_ec.pl FANOFF
``` really stops the fan for few seconds, or even ```
sudo ./fanslow.sh
``` but how to manipulate with the data there, and make the compute to hold to it?
E.g. i would like to have Fan off until 60 Degrees. No idea what should i change to those files to make it working...

---

### Post by vickoxy on 2013-03-03
Help me please-don´t want to sell the laptop. And the progress is here-the fan is respnding to those .sh files, but it doesnt stick very long to it...

---

### Post by vickoxy on 2013-03-03
No one?

---

### Post by k3mpaxl on 2013-03-03
3 posts  in 15 hours? It's weekend. ;)
Try setting 'Fan always on on AC' to Off in BIOS.
the temps can be adjusted in fanslow.sh , look for value 55, this is the first step.

k3mpaxl

---

### Post by vickoxy on 2013-03-03
I did that (BIOS)-no change at all.
So, if i change value 55 to 65 (if thats Celsius) and run fanslow.sh, the fan stops for 3-4 sec. and then starts again-although the temperatures are not higher as 45-47 degrees.

```
linux@linux:~/4530s/FanControl$ sudo ./fanslow.sh
0:80:180:65
0:80:180:70
0:80:180:75

```

I tried to change other values too, but no change in fan behaviour-the script stops the fan only for few seconds...

Weekend-my days off-meaning i am trying to fix the computer... :-)

---

### Post by k3mpaxl on 2013-03-03
Change line 28 to
TMP=$(sensors | grep Physical | cut -b 18-19)

It should look like this:
TMP=$(tail /sys/class/hwmon/hwmon1/device/temp1_input | cut -b1-2)

---

### Post by vickoxy on 2013-03-03
```
linux@linux:~/4530s/FanControl$ sudo ./fanslow.sh
[sudo] password for linux: 
tail: »/sys/class/hwmon/hwmon1/device/temp1_input“ kann nicht zum Lesen geöffnet werden: Datei oder Verzeichnis nicht gefunden

```
The problem is that by me tempos are here:

> /sys/class/hwmon/hwmon0/device/temp1_input but temp 1 is always 0. 

See here too:
```
linux@linux:~/4530s/FanControl$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:         +0.0°C  (crit = +127.0°C)
temp2:         +0.0°C  (crit = +127.0°C)
temp3:        +11.0°C  (crit = +128.0°C)
temp4:        +37.0°C  (crit = +127.0°C)
temp5:         +0.0°C  (crit = +115.0°C)
temp6:        +26.7°C  (crit = +128.0°C)
temp7:         +0.0°C  (crit = +128.0°C)
temp8:        +39.0°C  (crit = +128.0°C)
temp9:        +44.0°C  (crit = +128.0°C)
temp10:       +59.0°C  (crit = +128.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +40.0°C  (high = +95.0°C, crit = +105.0°C)
Core 2:       +39.0°C  (high = +95.0°C, crit = +105.0°C)

```

So, the temp 8 ist the nearest to CPU temp.

So i change it that it look like here:
```
#!/bin/bash
LOGFILE=/var/log/fanspeed.log
ECFILE=/home/linux/4530s/FanControl/probook_ec.pl
COUNTER=60

######################################################

initOff()
{
  setFan 80
  sleep 2
  $ECFILE FANOFF
}

setFan()
{
  SPEED=$1
  $ECFILE := 0x2F $SPEED
}

getTempAvg()
{
  CUR=0
  CPUTEMP=0
  MAX=$1
  while [ $CUR -lt $MAX ]
  do
    TMP=$(tail /sys/class/hwmon/hwmon0/temp8_input | cut -b1-2)
    let CPUTEMP=$CPUTEMP $TMP
    let CUR=$CUR+1
    sleep 1
  done
  let CPUTEMP=$CPUTEMP/$MAX
}

detectNewSpeed()
{
  CPUTEMP=$1
  CNTMAX=$2
  INTERVAL=$3
  if [ $CPUTEMP -le 65 ]
  then
    if [ $COUNTER -ge $CNTMAX ]
    then
      NEWSPEED=FF
    else
      NEWSPEED=80
      let COUNTER=$COUNTER+$INTERVAL
    fi
  else
    let COUNTER=0
    if [ $CPUTEMP -ge 80 ]
    then
      NEWSPEED=0
    elif [ $CPUTEMP -ge 75 ]
    then
      NEWSPEED=49
    elif [ $CPUTEMP -ge 70 ]
    then
      NEWSPEED=59
    elif [ $CPUTEMP -ge 65 ]
    then
      NEWSPEED=65
    elif [ $CPUTEMP -ge 60 ]
    then
      NEWSPEED=74
    elif [ $CPUTEMP -gt 55 ]
    then
      NEWSPEED=80
    fi
  fi
  echo $1:$NEWSPEED:$2:$COUNTER
  setFan $NEWSPEED
}

##################################################

initOff

while [ true ]
do
INTERVAL=5
getTempAvg $INTERVAL
detectNewSpeed $CPUTEMP 180 $INTERVAL

done
```
But still no change:
```
linux@linux:~/4530s/FanControl$ sudo ./fanslow.sh
0:80:180:65
0:80:180:70
0:80:180:75
0:80:180:80
0:80:180:85
0:80:180:90
0:80:180:95
0:80:180:100
0:80:180:105
0:80:180:110
0:80:180:115
0:80:180:120
0:80:180:125
0:80:180:130

```

The fan is few secs off, and than starts again...
But i think we are near-just i am not expert-in dell i know there is a way to shut off BIOS fan control. It seems that after few secs HP Bios takes control over fan... How to avoid that?

---

### Post by k3mpaxl on 2013-03-04
> **vickoxy said:**
> 

So, the temp 8 ist the nearest to CPU temp.



using the following should solve your problem:

TMP=$(sensors | grep Core | cut -b18-22 | sort -n | tail -n 1) 

```

#!/bin/bash
LOGFILE=/var/log/fanspeed.log
ECFILE=/home/gregor/.4530s/FanControl/probook_ec.pl
COUNTER=100

######################################################

initOff()
{
  setFan 80
  sleep 2
  $ECFILE FANOFF
}

setFan()
{
  SPEED=$1
  $ECFILE := 0x2F $SPEED
}

getTempAvg()
{
  CUR=0
  CPUTEMP=0
  MAX=$1
  while [ $CUR -lt $MAX ]
  do
    #TMP=$(sensors | grep Physical | cut -b 18-19)
    TMP=$(sensors | grep Core | cut -b18-22 | sort -n | tail -n 1)
    let CPUTEMP=$CPUTEMP+$TMP
    let CUR=$CUR+1
    sleep 1
  done
  let CPUTEMP=$CPUTEMP/$MAX
}

detectNewSpeed()
{
  CPUTEMP=$1
  CNTMAX=$2
  INTERVAL=$3
  if [ $CPUTEMP -le 55 ]
  then
    if [ $COUNTER -ge $CNTMAX ]
    then
      NEWSPEED=FF
    else
      NEWSPEED=80
      let COUNTER=$COUNTER+$INTERVAL
    fi
  else
    let COUNTER=0
    if [ $CPUTEMP -ge 80 ]
    then
      NEWSPEED=0
    elif [ $CPUTEMP -ge 75 ]
    then
      NEWSPEED=49
    elif [ $CPUTEMP -ge 70 ]
    then
      NEWSPEED=59
    elif [ $CPUTEMP -ge 65 ]
    then
      NEWSPEED=65
    elif [ $CPUTEMP -ge 60 ]
    then
      NEWSPEED=74
    elif [ $CPUTEMP -gt 55 ]
    then
      NEWSPEED=80
    fi
  fi
  echo $1:$NEWSPEED:$2:$COUNTER
  setFan $NEWSPEED
}

##################################################

initOff

while [ true ]
do
INTERVAL=5
getTempAvg $INTERVAL
detectNewSpeed $CPUTEMP 180 $INTERVAL

done

```

k3mpaxl

---

### Post by vickoxy on 2013-03-04
Hi. Thanks for answer-i have some error now-and still no change in Fan Behavior.
```
^Clinux@linux:~/4530s/FanControl$ sudo ./fanslow.sh
./fanslow.sh: Zeile 30: let: CPUTEMP=0+.0°C: Syntax Fehler: Operator erwartet. (Fehlerverursachendes Zeichen ist \".0°C\").
./fanslow.sh: Zeile 30: let: CPUTEMP=0+.0°C: Syntax Fehler: Operator erwartet. (Fehlerverursachendes Zeichen ist \".0°C\").
./fanslow.sh: Zeile 30: let: CPUTEMP=0+.0°C: Syntax Fehler: Operator erwartet. (Fehlerverursachendes Zeichen ist \".0°C\").
./fanslow.sh: Zeile 30: let: CPUTEMP=0+.0°C: Syntax Fehler: Operator erwartet. (Fehlerverursachendes Zeichen ist \".0°C\").
./fanslow.sh: Zeile 30: let: CPUTEMP=0+.0°C: Syntax Fehler: Operator erwartet. (Fehlerverursachendes Zeichen ist \".0°C\").
0:80:180:105
./fanslow.sh: Zeile 30: let: CPUTEMP=0+.0°C: Syntax Fehler: Operator erwartet. (Fehlerverursachendes Zeichen ist \".0°C\").

```

---

### Post by k3mpaxl on 2013-03-04
> **vickoxy said:**
> Hi. Thanks for answer-i have some error now-and still no change in Fan Behavior.
```
^Clinux@linux:~/4530s/FanControl$ sudo ./fanslow.sh
./fanslow.sh: Zeile 30: let: CPUTEMP=0+.0°C: Syntax Fehler: Operator erwartet. (Fehlerverursachendes Zeichen ist \".0°C\").
./fanslow.sh: Zeile 30: let: CPUTEMP=0+.0°C: Syntax Fehler: Operator erwartet. (Fehlerverursachendes Zeichen ist \".0°C\").
./fanslow.sh: Zeile 30: let: CPUTEMP=0+.0°C: Syntax Fehler: Operator erwartet. (Fehlerverursachendes Zeichen ist \".0°C\").
./fanslow.sh: Zeile 30: let: CPUTEMP=0+.0°C: Syntax Fehler: Operator erwartet. (Fehlerverursachendes Zeichen ist \".0°C\").
./fanslow.sh: Zeile 30: let: CPUTEMP=0+.0°C: Syntax Fehler: Operator erwartet. (Fehlerverursachendes Zeichen ist \".0°C\").
0:80:180:105
./fanslow.sh: Zeile 30: let: CPUTEMP=0+.0°C: Syntax Fehler: Operator erwartet. (Fehlerverursachendes Zeichen ist \".0°C\").

```

finally: :-)
**TMP=$(sensors | grep Core | sed -e "s/ //g" | cut -f2 -d ":" | cut -b2-3 | sort -n | tail -n 1)**

---

### Post by vickoxy on 2013-03-04
Thanks. So, the fan stops for few secs but than it start again:
```
linux@linux:~/4530s/FanControl$ sudo ./fanslow.sh
[sudo] password for linux: 
0:80:180:65
0:80:180:70

```

So, not sure why. Could you tell me where are temps/fan speed adjustments, where can these be changed?

---

### Post by k3mpaxl on 2013-03-04
Could you please post the output of the following commands:

```
sensors | grep Core 
sensors | grep Core | sed -e "s/ //g"
sensors | grep Core | sed -e "s/ //g" | cut -f2 -d ":"
sensors | grep Core | sed -e "s/ //g" | cut -f2 -d ":" | cut -b2-3
sensors | grep Core | sed -e "s/ //g" | cut -f2 -d ":" | cut -b2-3 | sort -n 
sensors | grep Core | sed -e "s/ //g" | cut -f2 -d ":" | cut -b2-3 | sort -n | tail -n 1
```
[B]k3mpaxl
[/B]

---

### Post by vickoxy on 2013-03-04
```
linux@linux:~$ sensors | grep Core 
Core 0:       +40.0°C  (high = +95.0°C, crit = +105.0°C)
Core 2:       +37.0°C  (high = +95.0°C, crit = +105.0°C)

```

```
linux@linux:~$ sensors | grep Core | sed -e "s/ //g"
Core0:+42.0°C(high=+95.0°C,crit=+105.0°C)
Core2:+41.0°C(high=+95.0°C,crit=+105.0°C)

```

```
linux@linux:~$ sensors | grep Core | sed -e "s/ //g" | cut -f2 -d ":"
+41.0°C(high=+95.0°C,crit=+105.0°C)
+39.0°C(high=+95.0°C,crit=+105.0°C)

```

```
linux@linux:~$ sensors | grep Core | sed -e "s/ //g" | cut -f2 -d ":" | cut -b2-3
40
38
linux@linux:~$ 

```

```
linux@linux:~$ sensors | grep Core | sed -e "s/ //g" | cut -f2 -d ":" | cut -b2-3 | sort -n 
39
41

```

```
linux@linux:~$ sensors | grep Core | sed -e "s/ //g" | cut -f2 -d ":" | cut -b2-3 | sort -n | tail -n 1
40

```

---

### Post by k3mpaxl on 2013-03-04
The command to check the current cpu temp is correct.

An output like:
```

0:80:180:70
0:80:180:75
0:80:180:80
0:80:180:85
```

should not show up.

these numbers mean the following:

**CPUTEMP**:FANSPEED:Slow-Down-Limit:Slow-Down-Clock

I implemented this slow down-mechanism to avoid pulsing, once the timer reaches the limit, your fan will stop.

please check again fanslow.sh produces this output, post your fanslow.sh file here and post the output of this command:

```
sudo ./probook_ec.pl regs
```

---

### Post by vickoxy on 2013-03-04
fanslow.sh:
```
#!/bin/bash
LOGFILE=/var/log/fanspeed.log
ECFILE=/home/linux/4530s/FanControl/probook_ec.pl
COUNTER=60

######################################################

initOff()
{
  setFan 80
  sleep 2
  $ECFILE FANOFF
}

setFan()
{
  SPEED=$1
  $ECFILE := 0x2F $SPEED
}

getTempAvg()
{
  CUR=0
  CPUTEMP=0
  MAX=$1
  while [ $CUR -lt $MAX ]
  do
   TMP=$(sensors | grep Core | sed -e "s/ //g" | cut -f2 -d ":" | cut -b2-3 | sort -n | tail -n 1)
    let CPUTEMP=$CPUTEMP $TMP
    let CUR=$CUR+1
    sleep 1
  done
  let CPUTEMP=$CPUTEMP/$MAX
}

detectNewSpeed()
{
  CPUTEMP=$1
  CNTMAX=$2
  INTERVAL=$3
  if [ $CPUTEMP -le 65 ]
  then
    if [ $COUNTER -ge $CNTMAX ]
    then
      NEWSPEED=FF
    else
      NEWSPEED=80
      let COUNTER=$COUNTER+$INTERVAL
    fi
  else
    let COUNTER=0
    if [ $CPUTEMP -ge 80 ]
    then
      NEWSPEED=0
    elif [ $CPUTEMP -ge 75 ]
    then
      NEWSPEED=49
    elif [ $CPUTEMP -ge 70 ]
    then
      NEWSPEED=59
    elif [ $CPUTEMP -ge 65 ]
    then
      NEWSPEED=65
    elif [ $CPUTEMP -ge 60 ]
    then
      NEWSPEED=74
    elif [ $CPUTEMP -gt 55 ]
    then
      NEWSPEED=80
    fi
  fi
  echo $1:$NEWSPEED:$2:$COUNTER
  setFan $NEWSPEED
}

##################################################

initOff

while [ true ]
do
INTERVAL=5
getTempAvg $INTERVAL
detectNewSpeed $CPUTEMP 180 $INTERVAL

done
```

```
linux@linux:~/4530s/FanControl$ sudo ./fanslow.sh
[sudo] password for linux: 
0:80:180:65
0:80:180:70
0:80:180:75
0:80:180:80
0:80:180:85
0:80:180:90
0:80:180:95
0:80:180:100
0:80:180:105
0:80:180:110
0:80:180:115
0:80:180:120
0:80:180:125

```

```
linux@linux:~/4530s/FanControl$ sudo ./probook_ec.pl regs

  	00	01	02	03	04	05	06	07	|	08	09	0A	0B	0C	0D	0E	0F
  	__	__	__	__	__	__	__	__	|	__	__	__	__	__	__	__	__
00 |	190	251	146	1	98	129	2	0	|	172	192	78	0	209	147	0	0	
10 |	0	0	0	0	144	99	1	0	|	31	15	42	1	213	48	166	128	
20 |	0	0	0	0	0	0	0	0	|	00	0	0	0	0	0	0	
30 |	0	0	0	0	0	0	0	0	|	00	0	0	0	0	0	0	
40 |	0	0	0	0	0	0	0	0	|	00	0	0	0	0	0	0	
50 |	0	0	0	0	0	0	0	0	|	00	0	0	0	0	0	0	
60 |	0	0	0	0	0	0	0	0	|	00	0	0	0	0	0	0	
70 |	0	0	0	0	0	0	0	0	|	00	0	0	0	0	0	0	
80 |	0	0	4	1	16	1	0	20	|	15	236	19	255	255	178	19	255	
90 |	255	1	1	0	77	48	42	0	|	01	0	255	255	142	5	207	
A0 |	5	149	12	17	0	91	44	196	|	14	203	14	202	14	200	0	255	
B0 |	255	150	0	255	255	100	255	192	|	0100	0	0	65	0	255	255	
C0 |	255	255	255	255	255	255	255	0	|	032	95	211	62	51	51	54	
D0 |	54	76	76	76	76	0	0	0	|	2255	255	255	255	255	255	255	
E0 |	176	11	255	7	0	212	0	1	|	30	4	0	255	255	255	0	
F0 |	0	0	0	0	0	0	0	0	|	00	0	0	0	0	0	0	
linux@linux:~/4530s/FanControl$
```

---

### Post by Van78 on 2013-04-05
Hello

I am totally new to Linux (Mint 14) but however since I do alot of writing I need a silent PC and that without Windows...

I have two HP 2540P :) and of course the fan is bugging me alot. Bios is set to NOT always on.

Can you help me to get my HP silent please?

PS:
I am from Germany since I noticed some others here too...

thanks alot

---

### Post by ogrozion on 2013-04-07
Howdy folks, I've bought a 2540p, its running 12.1, and my fan is stucked (linux off, W7 normal)... Differently than yours, it stops during kernel bootup. The BIOS was updated to the last issue (03/2013). Did you had success with fancontrol? Or only with the fanslow.sh?
Thanks in advance, 
    Andrei Mörsch Franco

---

### Post by pasdeloup on 2014-03-02
Thank you, k3mpaxl ! Your post is some time ago, but I am happy I have found it. And it works perfectly :D

---

### Post by squid-thefloatingfrog on 2014-07-16
> **k3mpaxl said:**
> 
now your system will boot up with a silent fan.


[COLOR=#000000]k3mpaxl, thank you very much for posting your solution - and a well written and easy to follow solution to boot.

I owe you a beer - if you're ever in Yorkshire, UK get in touch.

Stephen[/COLOR]

---

### Post by k3mpaxl on 2014-10-12
Hi all,

at first, thanks for your nice feedback! It's nice to read that people using my script :)

I've rewitten my fan control code.
It's a normal system service now, setting the control instructions during the boot and resetting to normal behauvior on shutdown.
I also changed the fan spin up mechanism. This script is better for dual boot systems.

I'll upload it within the next days.

If you got any questions in upgrading your 4530s with a full hd display, changing the cpu or removing the dvd drive for an additional 2,5 hdd/ssd, send me a private message. :)

---

### Post by Daniyal_Javani on 2014-12-12
Hello
Sorry I'm newbie! And can't understand what should I do.
Could you please help me to do that?  
What is inside `/home/gregor/.4530s/FanControl/probook_ec.pl`?

I followed [this guide]("http://askubuntu.com/questions/22108/how-to-control-fan-speed") about how to control fan speed in Ubuntu, but it doesn't work with my laptop and got /usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed error.
  Previously in windows i'd do it with hpfancontrol from [here]("http://www.staff.uni-marburg.de/%7Eschmitzr/donate.html").

---

### Post by ronald801 on 2015-08-04
Wow! Works with my Probook 450 G2!

---

### Post by k3mpaxl on 2016-02-28
Hello,

after receiving several messages about my probook fan control script, I'd like to share my updated version with you.
I've written this script as a service. It will start with your boot sequence and stop when your pc shuts down.

It works on my Probook 4530s for several month now. You can use it on you own risk.


```

sudo mkdir /etc/fanspeed
sudo wget https://raw.githubusercontent.com/k3mpaxl/fanspeed/master/fanslow.sh -O /etc/fanspeed/fanslow.sh
sudo wget https://raw.githubusercontent.com/k3mpaxl/fanspeed/master/probook_ec.pl -O /etc/fanspeed/probook_ec.pl

sudo chmod a+x /etc/fanspeed/fanslow.sh
sudo chmod a+x /etc/fanspeed/probook_ec.pl

sudo wget https://raw.githubusercontent.com/k3mpaxl/fanspeed/master/init.d_fanspeed -O /etc/init.d/fanspeed

sudo chmod a+x /etc/init.d/fanspeed

sudo update-rc.d -f fanspeed defaults


```

k3mpaxl

---

### Post by xube on 2016-02-28
Thanks, Its perfect. I made tweaks for my Probook 450 G0, for example:
> 
TMP=$(cat /sys/class/hwmon/hwmon*/device/hwmon/hwmon1/temp1_input | cut -b1-2)

Also NEWSPEEDF to "F5" cause this is the slowest possible value for my fan. I cant set fan to OFF by "FF" value. Maybe its not possible or i am doing something wrong. I think "FF" just restart fan to safe default value.

I am interested about the variables in fanslow.sh file at the bottom. 

> #throttle down after $THROTTLESEC seconds
THROTTLESEC=30
#set fan off after on lowest setting for $THROTTLEOFF seconds
THROTTLEOFF=80
#temperatures in celsius
TEMPFANSTARTSPEED=52 #56
TEMPFANMAXSPEED=80



I think i understand only TEMPFANSTARTSPED. But what others? What does it mean?

Anyway, thank you very much.

---

### Post by k3mpaxl on 2016-02-29
My fancontrol script uses a parabola function to calculate the fanspeed.
The formula is (temp-maxtemp)*(temp+maxtemp)*(-24/1000), here is what this looks like on wolframalpha:
[http://www.wolframalpha.com/input/?i=plot+%28x-80%29+*+%28x%2B80%29+*+%28-24%2F1000%29,+from+x+%3D+18+to+80](http://www.wolframalpha.com/input/?i=plot+%28x-80%29+*+%28x%2B80%29+*+%28-24%2F1000%29,+from+x+%3D+18+to+80)

On the Probook 4530s, the fanspeed values go from 0 (maximum speed) to 80 (lowest speed), and FF means "Fan off".
This means, the **higher **the average **temperature **is, the **lower **the **fanspeed **value should be set (because lower fanspeed values mean higher speed). This is confusing, yes! 

 The value TEMPFANSTARTSPEED is the fan on/off switch temperature. TEMPFANMAXSPEED defines how fast the function calculates the maximum fan speed.

Once the avg cpu temperature is lower than the last temperature, the value THROTTLESEC defines how many seconds the mechanism must wait and keep the old speed until the fan gets lowered.

So, if you know you fanspeed maximum and minimum, you can create your own parabola function to calculate the desired fanspeed value. :-)

I hope, this will help you debugging my script.

k3mpaxl

---

### Post by micsu-z on 2016-12-17
It works on my HP 8460p
Wow, this solution is wonderful, k3mpaxl! Thanks!

---

