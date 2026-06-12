---
title: "Horrible Battery life under Feisty"
date: 2007-06-18
forum: Hardware &amp; Laptops
---

### Post by Apewall on 2007-06-18
Using Feisty with kernel 2.6.20-26.
ly 
I have ACPI enabled, configured, and its triggering fine, aswell as powernow-k8 for cpuscaling, and gpuscaling enabled for my video card in xorg.conf.

Using an MSI 1039B model laptop
Ati Radeon X1600 Mobility
Athlon64 Turion Mobility MT-40

My battery's charge listing is 48.8Wh, curretly max at 47.1Wh, but I only get 1 hour 30 minutes on Ubuntu Feisty, I get around 3 hours on WindowsXP, and was getting 3 hours 20 minutes on FedoraCore6, and 3 hours on my previous Dapper Drake installation.

Anything I'm forgetting to do?:(

---

### Post by lnxusr on 2007-06-18
Sounds like your GPU's frequency scaling might not be triggering properly. When running on batteries, run the command
```
aticonfig --list-powerstates
```
and post the output. 
I had similar trouble in Archlinux, but it turned out to be troublesome ATI drivers and ATI's ACPI script.

---

### Post by OsakaWilson on 2007-06-18
Same problem for me. I tried running the suggestedd command and got this:

xxxx@xxxx-laptop:~$ sudo aticonfig --list-powermodes
aticonfig: unrecognized option `--list-powermodes'
aticonfig: parsing the command-line failed.

I tried it without sudo too and it didn't work.

---

### Post by lnxusr on 2007-06-18
D'oh sorry, that command is 
```
aticonfig --list-powerstates
```
Maybe i should go to sleep :oops:

---

### Post by Apewall on 2007-06-20
```

  1: 209/135 Mhz  [Low Voltage]
  2: 392/135 Mhz
*3: 446/450 Mhz [default State]

```

I'll suppose the * indicates the current mode, which should be Low Voltage and not on max, How do i change this? :0

---

### Post by Jacks0n on 2007-06-20
```
sudo aticonfig --set-powerstate=NUM
```

change NUM to whatever number in that list. eg 1,2,3..

I've written a script to graphically change it. Incase you want it, here it is. but you need a program called zenity. it comes with ubuntu by default. copy the following into a text editor, save it. then type "sudo chmod +x /path/to/the/file/"

```

#!/bin/bash

for i in `aticonfig --list-powerstates | grep ':'` ; do
	if [[ -n `echo "$i" | grep '/'` ]]; then
		echo -n "SELECT " >> /tmp/list_powerstates
		echo -n "$i " >> /tmp/list_powerstates
	fi
done

FREQ=$(zenity --list --radiolist --column="Select" --column="Powerstate (MHz)" `cat /tmp/list_powerstates`)
NUM_SELECTED=$(aticonfig --list-powerstates | grep $FREQ | cut -d':' -f1 | sed 's/ //g' | sed 's/*//g')
CURRENT_NUM=$(aticonfig --list-powerstates | grep '*' | cut -d':' -f1 | sed 's/* //g')
PASSW=$(zenity --entry --title="Password" --text="Please enter your password:" --hide-text)
rm /tmp/list_powerstates
echo $PASSW | sudo -S aticonfig --set-powerstate=${NUM_SELECTED}
if [[ $? != "0" && $NUM_SELECTED != $CURRENT_NUM ]]; then
	zenity --error --title="Wrong Password" --text="Wrong password. Exiting..."
	exit 1	
fi

```

---

