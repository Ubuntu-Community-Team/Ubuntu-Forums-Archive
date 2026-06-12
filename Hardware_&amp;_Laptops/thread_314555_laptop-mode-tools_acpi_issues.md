---
title: "laptop-mode-tools acpi issues"
date: 2006-12-07
forum: Hardware &amp; Laptops
---

### Post by snype on 2006-12-07
okay. this is driving me nuts--
what I'm trying to accomplish: i want to run two commands everytime the computer is plugged in or un-plugged. i tried putting a script in the /etc/acpi/ac.d and the /et/acpi/battery.d  and they werent being run. i know that they are inturn being called from within power.sh-- my power.sh is unmodified and it does switch the laptop-mode on and off correctly but does not run the scripts withing ac.d and battery.d
when i sudo sh power.sh it has some errors:

snype@uno:/etc/acpi$ sudo sh power.sh
power.sh: 6: function: not found
Laptop mode enabled, active.
basename: missing operand
Try `basename --help' for more information.
basename: missing operand
Try `basename --help' for more information.
power.sh: 20: Syntax error: "}" unexpected



my power.sh:


#!/bin/bash

. /etc/default/acpi-support
. /usr/share/acpi-support/power-funcs

function laptop_mode_enable {
    $LAPTOP_MODE start
    
    for x in /sys/bus/ide/devices/*/block; do 
	drive=$(basename $(readlink $x));
	$HDPARM -S 12 /dev/$drive 2>/dev/null
	$HDPARM -B 1 /dev/$drive 2>/dev/null
    done
    
    for x in /sys/bus/scsi/devices/*/block; do 
	drive=$(basename $(readlink $x));
	$HDPARM -S 12 /dev/$drive 2>/dev/null
	$HDPARM -B 1 /dev/$drive 2>/dev/null
    done
}

function laptop_mode_disable {
    for x in /sys/bus/ide/devices/*/block; do 
	drive=$(basename $(readlink $x));
	$HDPARM -S 0 /dev/$drive 2>/dev/null
	$HDPARM -B 255 /dev/$drive 2>/dev/null
    done
    for x in /sys/bus/scsi/devices/*/block; do 
	drive=$(basename $(readlink $x));
	$HDPARM -S 0 /dev/$drive 2>/dev/null
	$HDPARM -B 255 /dev/$drive 2>/dev/null
    done
    $LAPTOP_MODE stop
}

getState;

checkStateChanged;

shopt -s nullglob

for x in /proc/acpi/ac_adapter/*; do
    grep -q off-line $x/state

    if [ $? = 0 ] && [ x$1 != xstop ]; then	
	for SCRIPT in /etc/acpi/battery.d/*.sh; do
	    . $SCRIPT
	done
	if [ x$ENABLE_LAPTOP_MODE = xtrue ]; then
	    (sleep 5 && laptop_mode_enable)&
	fi
    else
	for SCRIPT in /etc/acpi/ac.d/*.sh; do
	    . $SCRIPT
	done
	if [ x$ENABLE_LAPTOP_MODE = xtrue ]; then
	    (sleep 5 && laptop_mode_disable)&
	fi
    fi
done







any help will be appreciated. i'm actually rippin' mad about this as I've spent like 4 hours messing around with this.

---

