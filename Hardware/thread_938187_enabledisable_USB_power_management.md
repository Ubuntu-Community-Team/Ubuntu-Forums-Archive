---
title: "enable/disable USB power management"
date: 2008-10-04
forum: Hardware
---

### Post by luismanson on 2008-10-04
Hi, a while ago y posted this idea: [http://brainstorm.ubuntu.com/idea/13573/](http://brainstorm.ubuntu.com/idea/13573/)
basically, a feture to be able to turn on/off USB devices from a GUI... this is very useful for laptop users to save battery power, and maybe something else... :P

So i read usb power management inside kernel Docs and found a simple way to accomplish this...
my only problem is that i don't know GTK programming nor lots of bash scripting...but at least i made this little script to find the devices and their name under /sys along with the device name OR USB ID if the name is not found and the current power status

```


#!/bin/sh

# APMPM - Advanced Poor Man Power Management
# Script to see power management status of USB devices
# by LuisManson - 08/10/08

declare -a ARRAYDEV
declare -a ARRAYPROD
declare -a ARRAYPWRSTATUS
let nprod=0

# funcion para consultar power/level
function query_level {
# level: on - auto - suspend

if [ -e $1/power/level ]; then
ARRAYPWRSTATUS[$nprod]=$(cat $devhome/power/level)
else if [ ! -e $devhome/power/level ]; then
ARRAYPWRSTATUS[$nprod]=NA
fi
fi
}


for idVendor in $(ls /sys/bus/usb/devices/*/idVendor); do
devhome=$(dirname $idVendor)
devlevel=$devhome/power/level

# if product, leo, else leo idvendor e idproduct
if [ -e $devhome/product ]; then
    ARRAYPROD[$nprod]="$devhome"
    ARRAYPRODDESC[$nprod]="$(cat $devhome/product)"
    query_level $devhome
    ((nprod++))
else if [ -e $devhome/idVendor ]; then
    ARRAYPROD[$nprod]="$devhome"
    ARRAYPRODDESC[$nprod]="$(cat $devhome/idVendor):$(cat $devhome/idProduct)"
    query_level $devhome
    ((nprod++))
fi
fi

done

echo -e "Description:\n"
echo -e "\tOn: Device ALLWAYS on"
echo -e "\tauto: managed by the kernel"
echo -e "\tsuspend: Device is suspended and autoresume is not allowed\n"



for element in $(seq 0 $((${#ARRAYPROD[@]} -1)))
  do
    echo -e "${ARRAYPROD[$element]}"\\n \\t "${ARRAYPRODDESC[$element]}"\\n \
    \\t Power status: ${ARRAYPWRSTATUS[$element]} \\n
done


```

BTW, yes, its nasty :P

---

### Post by luismanson on 2008-10-06
no one interested? :confused:

---

### Post by Beebock on 2008-10-19
Hi,

I am very interested in this for the NOVA-t-500 TV card. The usb goes intopower saves and then screws everything up.

Does this script allow you to disable things?

thanks
Ricahrd

---

### Post by watkin5 on 2008-11-22
> **Beebock said:**
> Hi,

Does this script allow you to disable things?

thanks
Ricahrd

No but...
change to root and you can echo on to disable the settings i.e 

sudo su
echo on > /sys/bus/usb/devices/5-8.4.1/power/level


P.S. Does anyone know why
sudo echo on > /sys/bus/usb/devices/5-8.4.1/power/level
gives a permission denined error?

P.P.S.
I had to change the first line of luismanson's script to !#/bin/bash

---

### Post by Lucas Roxo Mundim on 2009-01-23
Because when you do this:

$ sudo touch test
$ sudo echo 'hello' > test
bash: test: Permission denied

sudo executes echo 'hello' as root. Then bash tries to write the output to the file named test as the current user.

This will work:

sudo bash -c 'echo "hello" > test'

Hope it helps. :)

---

