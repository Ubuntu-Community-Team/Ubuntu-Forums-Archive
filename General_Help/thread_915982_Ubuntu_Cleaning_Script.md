---
title: "Ubuntu Cleaning Script"
date: 2008-09-10
forum: General Help
---

### Post by anotherdisciple on 2008-09-10
Has anyone ever made a clean-up script? Maybe something that pops up a zenity checklist that asks if you want to clean:

-Residual Config packages
-Partial Packages
-Locale Data
-Orphaned Packages
-Temporary Files
-Backup Files
-etc.

This is fairly simple to do if you have experience with the terminal... but I'm just curious for my friends who basically have me work on their linux box if it requires using the terminal.

---

### Post by kokkus on 2008-09-10
I don't think you need a script to do that. 
Just add these hardy commands to your startup script:

Clean cache:
sudo apt-get clean
sudo apt-get autoclean

Clean .bak files:
sudo rm /boot/*.bak

---

### Post by anotherdisciple on 2008-09-10
That's a good idea, but I'm looking for something that makes the option available rather than doing it every time you start your computer.

---

### Post by Ms_Angel_D on 2008-09-10
Check [This Thread]("http://ubuntuforums.org/showthread.php?t=905445") Post #12

---

### Post by forger on 2008-09-10
It shouldn't be that hard.. there's an example with zenity:
```
zenity --list --checklist --hide-column=2 --column "Do" --column "ID" --column "Description" \
TRUE 1 "Clean stuff" \
TRUE 2 "Mop the floor" \
FALSE 3 "Kill the penguin" \
FALSE 4 "Shutdown when done"
```
They'll return the id number of each row, which could be useful for further process, with say a perl script or bash

---

### Post by russlar on 2008-09-10
> **anotherdisciple said:**
> Has anyone ever made a clean-up script? Maybe something that pops up a zenity checklist that asks if you want to clean:

-Residual Config packages
-Partial Packages
-Locale Data
-Orphaned Packages
-Temporary Files
-Backup Files
-etc.

This is fairly simple to do if you have experience with the terminal... but I'm just curious for my friends who basically have me work on their linux box if it requires using the terminal.

sorry, didn't read the last line. If they want to do it w/o the terminal, just write a script. Have them double click it whenever they want to clean up.

---

### Post by Sycron on 2008-09-10
Yes, it's not so hard. Just a couple of fun time coding sh script. :P

---

### Post by forger on 2008-09-10
> **Sycron said:**
> Yes, it's not so hard. Just a couple of fun time coding sh script. :P

```

#!/bin/bash
#Clean up script

IFS='|'
cleanuplist=`zenity --list --checklist --hide-column=2 --column "Do" --column "ID" --column "Description" \
TRUE 1 "Clean stuff" \
TRUE 2 "Mop the floor" \
FALSE 3 "Kill the penguin" \
FALSE 4 "Shutdown when done"`
for i in $cleanuplist; do
	if [ "$i" = "1" ]; then
		echo "Number 1: This is the way we clean our stuff, clean our stuff.."
		#command 1
	fi
	if [ "$i" = "2" ]; then
		echo "Number 2: Woo! Mopping the floor!"
		#command 2
	fi
	if [ "$i" = "3" ]; then
		echo "Number 3: OMG! You shot the penguin! You cold murderer!"
		#command 3
	fi
done
unset IFS

```

The concept is there :)

---

### Post by Sycron on 2008-09-11
> **forger said:**
> ```

#!/bin/bash
#Clean up script

IFS='|'
cleanuplist=`zenity --list --checklist --hide-column=2 --column "Do" --column "ID" --column "Description" \
TRUE 1 "Clean stuff" \
TRUE 2 "Mop the floor" \
FALSE 3 "Kill the penguin" \
FALSE 4 "Shutdown when done"`
for i in $cleanuplist; do
	if [ "$i" = "1" ]; then
		echo "Number 1: This is the way we clean our stuff, clean our stuff.."
		#command 1
	fi
	if [ "$i" = "2" ]; then
		echo "Number 2: Woo! Mopping the floor!"
		#command 2
	fi
	if [ "$i" = "3" ]; then
		echo "Number 3: OMG! You shot the penguin! You cold murderer!"
		#command 3
	fi
done
unset IFS

```

The concept is there :)


So genius, intelligible sh script.

---

