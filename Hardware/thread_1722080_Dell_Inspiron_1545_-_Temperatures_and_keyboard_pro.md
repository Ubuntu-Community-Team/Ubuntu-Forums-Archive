---
title: "Dell Inspiron 1545 - Temperatures and keyboard problem"
date: 2011-04-05
forum: Hardware
---

### Post by Unisio on 2011-04-05
Hello!

I installed Ubuntu 10.10 on my half year old Dell Inspiron 1545/9985 and encountered two problems.

The fan doesn't seem to accelerate when reaching 49°C which it usually does in Windows and pushes CPU and GPU temps back to 38°C - 40°C. Idle degrees are around 50°C for all censors which is 10°C higher compared to Windows (HDD temperature is about the same I guess, slight higher maybe).
lm-sensors doesn't seem to be able to read fan speed either and when I try "sudo fancontrol" in the terminal I get the error 
"Loading configuration from /etc/fancontrol ...
Error: Can't read configuration file"

It never seems to actually boost the fan when reaching higher temperatures either, it's a loud laptop normally but I hear almost nothing using Ubuntu.

Is there a way to fix this or is the Inspiron incompatible with Ubuntu at the moment?

The other problem is that when using my laptop keyboard it sometimes skips to another part in the text, minimizes windows or changes tab automatically. This has never happened before!

What should I do? :confused:

---

### Post by jd.jayded on 2011-05-24
Right...I have an inspiron 1520 and had fan issues.
I fixed them using i8kutils, which is derived from the source code of i8k for windows, which was reverse engineered from Dell code.

Note that i8k will let you run a fan on a dell at 0 (off), 1 (slow), or 2 (fast), and that there is a left and a right fan setting. Right and left don't seem to have anything to do with physical location- my machine has a fan on the left and thinks it's the right fan.

i8kfan - 0 sets the right fan to 0 (off), left unchanged
i8kfan - 1 sets the right fan to 1 (slow), left unchanged
i8kfan - 2 sets the right fan to 2 (fast), left unchanged

i8kfan 2 - sets the left fan to 2 (fast), right unchanged.

i8kfan 2 2 sets both to fast

Here are my instructions

Install the i8k utility:
sudo apt-get install i8kutils

Create a fan script (I called it fan.sh), you will need to know the path to it:
#!/bin/sh
#Author jd.jayded
#note: the temperatures set here may be overly conservative. Set as you wish.
fan1=25 #turn fan on to 1
fan2=45 #turn fan on to 2
fanBack1=35 #turn fan back to 1
minFan2=30 #minium time for fan to be spinning on mode two (seconds)
minFan1=0 #minimum time for fan to be spinning on mode one (seconds), set to zero because it can be necessary to increase speeds

while true ; do
    i=`i8kctl temp | tr -dc '[0-9]'` #i8kctl temp gives you current temperature, piped to trim to one numbers
    if [ $i -ge $fan1 ] ; #if it's greater than or equal to fan1
    then
        if [ $i -ge $fan2 ] ;
        then
            i8kfan 2 2
            sleep $minFan2
        else
            if [ $i -ge $fanBack1 ] ;
            then
                sleep $minFan2
            else
                i8kfan 1 1
                sleep $minFan1
            fi
        fi
    else
        i8kfan 0 0
    fi
    sleep 1s #run every second, not counting sleep used as a minimum amount of time to have a fan on
done


Create a start up script. I called it startup.sh
#!/bin/sh
modprobe i8k
/path/to/fan.sh #location of the fan script


Now execute these commands:
sudo ln -s -T /path/to/startup.sh /etc/init.d/startup.sh
sudo update-rc.d [startup script name] defaults

The first command gives you a symbolic link to your startup script in the /etc/init.d directory
The  second command adds the startup script to the default runlevels. It's  automatically run when you turn on the computer. That will give you  warnings because I didn't bother learning the proper format for a  System-V init script. man update-rc.d for more about init scripts.

EDIT: sorry about the tabbing dying. I'm new to these forums.

---

### Post by cbr_king on 2011-09-04
Is this working for the Dell L70xxx series? There is no confirmation in this thread.

---

### Post by Unisio on 2012-05-07
Thanks for the replies!

One year later with the same problem. I haven't used Ubuntu since 10.10 because graphic drivers acting up in 11.04 and 11.10 thankfully that seems to have been sorted out in 12.04.

Thanks for the guide however that did not work for me, the fans are still in "lazy mode" (I guess setting 1?) and temperatures are still acting up: [http://ubuntuone.com/73gEpdsQnRWatKiUBdI4K5](http://ubuntuone.com/73gEpdsQnRWatKiUBdI4K5) . The graph shows the computer in average load with Spotify, Xchat and the Software Center in use. Otherwise temperatures seem to idle pretty much at 50 - 52 degrees which is pretty high imo. 

How do I revert the changes made by using the guide?

Has anyone come up with a solution to the Inspiron temperature problem? I've tried another guide [http://ubuntuforums.org/showthread.php?t=1636686](http://ubuntuforums.org/showthread.php?t=1636686) which didn't work either.

---

