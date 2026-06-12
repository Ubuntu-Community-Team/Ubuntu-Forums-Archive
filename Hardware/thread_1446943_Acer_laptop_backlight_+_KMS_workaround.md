---
title: "Acer laptop backlight + KMS workaround"
date: 2010-04-04
forum: Hardware
---

### Post by FunkyRider on 2010-04-04
**UPDATE:** This works on Ubuntu 9.10 Karmic, 10.4 Lucid and 10.10 Maverick

Also works on other brands of laptops!

If you are like me, suffered for no KMS hack to make laptop backlight work, you can use the following method to bring **KMS AND backlight adjusting** together.

First, thanks for the post [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/397617](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/397617) to give me the idea to create a daemon script which continously monitor system level backlight value change and propagate the value to the pci bus to get it REALLY changed.

1. Remove the 'nomodeset' hack from grub kernel loading parameter, now you cannot adjust backlight, for a while :-)

2. Restart system, open terminal and type this command:

~$ lspci | grep VGA

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)


This number "00:02.0" is what you want to modify in the following script.

3. Copy the lines between the "###" mark, and save it as a file named something like 'backlight_d.sh', before saving, modify the number after pciset -s ##:##.# as the one you got from step 2

~$ gedit ./backlight_d.sh

########################################################
#!/bin/bash

old_b=9;
declare -i curr_b=240;
declare -i target_b=240;

while : ; do
b=`cat /sys/class/backlight/acpi_video0/brightness`;
delay="0.5"

if [ $old_b != $b ]; then
old_b=$b
let "target_b=$b * 20 + 12"
#printf "Target: %10d\n" $target_b
fi

hex_b=".";

if [ "$curr_b" -lt "$target_b" ] ; then
let "curr_b=$curr_b + 2"
if [ "$curr_b" -gt "$target_b" ] ; then
let "curr_b=$target_b"
fi

hex_b="-"
elif [ "$curr_b" -gt "$target_b" ] ; then
let "curr_b=$curr_b - 2"
if [ "$curr_b" -lt "$target_b" ] ; then
let "curr_b=$target_b"
fi

hex_b="-"
fi

if [ $hex_b != "." ] ; then
hex_b=`printf "%02X" $curr_b`
delay="0.005"
setpci -s 00:02.0 F4.B=$hex_b
fi

sleep $delay
done
########################################################

4. Copy it to /etc (in root mode) and make executable
# cp ./backlight_d.sh /etc/
# chmod +x /etc/backlight_d.sh

5. Add it to rc.local
# nano /etc/rc.local

Find the line 'exit 0', add BEFORE it:

########################################################

nohup /etc/backlight_d.sh &

########################################################


All done! Restart now and watch the backlight magically change!):P

UPDATE: I've modified the first post to include the latest update of the script, which offers smooth transition of backlight level.

---

### Post by the_cleaner on 2010-05-20
@FunkyRider
It looks like the modification in rc.local is blocking the execution of bootchart.
I've added the "&"-sign behind the script name and now bootchart works again as desired:
BEFORE: nohup /etc/backlight_d.sh
AFTER: nohup /etc/backlight_d.sh &

(See also [http://en.wikipedia.org/wiki/Nohup](http://en.wikipedia.org/wiki/Nohup), section Example)

Best regards

---

### Post by catchmeifu on 2010-07-22
Thanks a tonne this seemed to work for me except when I boot into windows I am dual booting I can restart and go straight into ubuntu and it keeps working but as soon as I go into windows and then back to ubuntu it stops working any ideas

---

### Post by Skildron on 2010-07-27
Thanks for this solution, this one has bugged my for some time. I modified your script some, because setpci writes hex values into the the hardware registers and with your solution, you never get back to the maximum of 0xFF brightness, instead only to 0x99, because the /sys/class/backlight/acpi_video0/brightness file, at least on my Acer Extensa 5635z with kubuntu karmic, contains only values from zero to nine. Here is my modified script:

#################################
#!/bin/sh

old_b='9';

while : ; do
        b=`cat /sys/class/backlight/acpi_video0/brightness`;

        if [ $old_b != $b ]; then
        #echo "Screen brightness level change: $old_b - $b"
        case $b in
                0) hex_b=1e ;;
                1) hex_b=37 ;;
                2) hex_b=50 ;;
                3) hex_b=69 ;;
                4) hex_b=82 ;;
                5) hex_b=96 ;;
                6) hex_b=b4 ;;
                7) hex_b=cd ;;
8) hex_b=e6 ;;
                9) hex_b=ff ;;
                *) hex_b=ff ;;
        esac
                old_b=$b
                #echo "executing setpci -s 00:02.0 F4.B=$hex_b"
                setpci -s 00:02.0 F4.B=$hex_b
        fi

        sleep 0.5
done
#################################

I started from the max brightness level 255 (0xFF) and went down in steps of 25 (0x19) to a min of 30 (0x1E). The stepping could of cause be choosen more or less steep and instead of the case instruction, some calculating formula would be possible, too.

Greetings, and once again thanks for your help
Skildron

---

### Post by FunkyRider on 2010-10-11
Been a while and just installed 10.10, thought I should make an update here.

The KMS+Backlight is STILL BROKEN on 10.10. It's probably the BIOS which is broken and I can't find any newer BIOS of this model from Acer.

The good news is this workaround still works on 10.10 so you can basically follow the step and fix it on 10.10.

Also thanks for the '&' part and updated script, they indeed makes the workaround seems more polished.

---

### Post by FunkyRider on 2010-10-13
Here is the ultimate backlight script:

What it does is it smoothly transit between brightness levels (like MacBook if you've ever experienced it). However I suspect that it only works if you have LED backlight screens but not sure about it.

Please try and give feedback!

###########################################

#!/bin/bash

old_b=9;
declare -i curr_b=240;
declare -i target_b=240;

while : ; do
b=`cat /sys/class/backlight/acpi_video0/brightness`;
delay="0.5"

if [ $old_b != $b ]; then
	old_b=$b
	let "target_b=$b * 20 + 12"
	#printf "Target: %10d\n" $target_b
fi

hex_b=".";

if [ "$curr_b" -lt "$target_b" ] ; then
	let "curr_b=$curr_b + 2"
	if [ "$curr_b" -gt "$target_b" ] ; then
		let "curr_b=$target_b"
	fi

	hex_b="-"
elif [ "$curr_b" -gt "$target_b" ] ; then
	let "curr_b=$curr_b - 2"
	if [ "$curr_b" -lt "$target_b" ] ; then
		let "curr_b=$target_b"
	fi

	hex_b="-"
fi

if [ $hex_b != "." ] ; then
	hex_b=`printf "%02X" $curr_b`
	delay="0.005"
	setpci -s 00:02.0 F4.B=$hex_b
fi

sleep $delay
done

---

### Post by FunkyRider on 2010-10-13
Bump...

Really sad to see that not a lot of people try it and all following other inferior workarounds.

---

### Post by Arla on 2010-10-14
Didn't work for me, Lenovo Y450, was hoping it might as it would resolve one of my two main issues with 10.10 (that and Suspend sometimes not working) I'm back to using nomodeset and acpi_backlight=vendor in 10.04.

---

### Post by rtomakov on 2010-10-15
Workaround works on eMachines e527.
 Nice work(around), FunkyRider!

---

### Post by Bedlore on 2010-10-23
I have a emachine E527 also but it hasn't worked for me, when executing the script manually I get the below output.

sudo ./backlight_d.sh 
[sudo] password for christina: 
./backlight_d.sh: 6: declare: not found
./backlight_d.sh: 7: declare: not found
./backlight_d.sh: 44: let: not found

Any advice to get this working please?

---

### Post by jlsm on 2010-10-26
Works perfectly with Lenovo 3000 G430. Its got the same Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07) chipset, so it made life easier for me.

I only have a few questions though...

* Does this workaround minimize battery consumption for my laptop (coz that's the primary reason I want to dim the backlight setting)

* Does continously monitoring the system level backlight value consume more battery than I save with the backlight dimmed; and

* Before using this workaround, I can still use the fn+up arrow, down arrow and see the brightness slider (though the screen doesn't brighten or dim when I use that, which led me to this thread in the first place). Is there a way to use the fn+arrow keys to change brightness setting with this workaround.

Still, this is an awesome workaround!


jlsm

---

### Post by FunkyRider on 2010-11-12
You don't have to worry about the script consuming power, it only wakes CPU up TWICE a second to check if backlight brightness requested value has changed so the effect is essentially equal to zero.

Also the backlight Fn keys are supposed to work. If it doesn't, try type this manually in console (non root should be fine):

cat /sys/class/backlight/acpi_video0/brightness

and joggle the fn+backlight keys and do it again. If the value does not change, you need to see if there is any dir rather than "acpi_video0", perhaps your backlight is detected as acpi_video1 or something similar.

ls /sys/class/backlight

and see what are the names of the dirs in that path.

Once you get a working path name which reflects your real backlight level when pressing the fn keys, modify the thread code and replace this "acpi_video0" with your own and it should work then.

---

### Post by DaV|d on 2011-01-08
Great workaround! good job!

---

### Post by luis2378 on 2011-03-27
Workaround works in emachines e525, but the bright controls are inverted.

Luis from uruguay.

---

