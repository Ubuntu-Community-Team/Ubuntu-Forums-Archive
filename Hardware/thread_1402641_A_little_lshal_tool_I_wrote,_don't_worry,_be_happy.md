---
title: "A little lshal tool I wrote, don't worry, be happy"
date: 2010-02-09
forum: Hardware
---

### Post by dyslexia on 2010-02-09
Match devices output by the *lshal* command, put each one in it's own file in a directory named 'lshal'.

Probably possible to do this without creating a directory each time; but I like being able to do commands like **more lshal/*** to get that familiar "overwhelmed by data" feeling.

```
# !/bin/bash
# Usage:  sholshal [parameters]
#
# Where [parameters] are items in the same line that must match for each device listed 
# by the lshal command.
#
# Return each device that contains matching lines as a separate file we create in the
# directory "lshal" (not the command) named by the device name on the first line of each 
# file.
#

#
# Example:
# sholshal vendor 1b96 - match lines which contain "vendor" followed by "1b96" elsewhere in the line
#            create a directory named lshal and place a file named for each matching device 
#            there.
#
# Note: in the unlikely event that we have a device name which begins with 'xx' this script will fail.



rm -rf lshal       # forget about previous trips, this is a new one!

mkdir lshal 

file="0"
lshal | while read a 
         do if [[ ! $a ]]  
            then file=$((++file))  
                else echo $a >> "lshal/xx"$file  
         fi ; done 
echo

param=""  
for i in $*  
    do param=$param"[[:print:]]*"$i 
done

echo  $param
echo

grep -l $param lshal/* | while read a 
        do grep $param $a 
#            echo "$a -> ${a/xx/ls}"
            b=lshal/$(head -n 1 $a | grep -wo "[^/]*[^']" | grep -v ".*=.*")
            echo "$a -> $b"
            mv $a $b 
        done 

rm lshal/xx*
echo


```

The usual procedure: copy into a file with a likely name (i.e. 'sholshal') and make executable

My output:

```


$ ./sholshal vendor 1b96

[[:print:]]*vendor[[:print:]]*1b96

usb_device.vendor_id = 7062 (0x1b96) (int)
lshal/xx46 -> lshal/usb_device_1b96_1_noserial
usb.vendor_id = 7062 (0x1b96) (int)
lshal/xx47 -> lshal/usb_device_1b96_1_noserial_if2
usb.vendor_id = 7062 (0x1b96) (int)
lshal/xx48 -> lshal/usb_device_1b96_1_noserial_if1
usb.vendor_id = 7062 (0x1b96) (int)
lshal/xx53 -> lshal/usb_device_1b96_1_noserial_if0

$ ./sholshal wacom

[[:print:]]*wacom

input.x11_driver = 'wacom' (string)
lshal/xx51 -> lshal/usb_device_1b96_1_noserial_if1_logicaldev_input_0
input.x11_driver = 'wacom' (string)
lshal/xx52 -> lshal/usb_device_1b96_1_noserial_if1_logicaldev_input

$ ./sholshal Pen

[[:print:]]*Pen

info.product = 'N-Trig Pen' (string)
input.product = 'N-Trig Pen' (string)
lshal/xx52 -> lshal/usb_device_1b96_1_noserial_if1_logicaldev_input

$ ./sholshal MultiTouch

[[:print:]]*MultiTouch

info.product = 'N-Trig MultiTouch' (string)
input.product = 'N-Trig MultiTouch' (string)
lshal/xx51 -> lshal/usb_device_1b96_1_noserial_if1_logicaldev_input_0



```

---

