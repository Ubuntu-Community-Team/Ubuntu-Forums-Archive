---
title: "Need help installing hp notebook drivers ubuntu 8.04"
date: 2008-09-07
forum: General Help
---

### Post by omnispyder on 2008-09-07
Hello I have a hp dv9634ca notebook.   8.04 works great video sound.
But my video card is not working properly.  Im trying to get compiz to work but nothing happens.  Any idea how I can install my drivers.

when i goto my hardware drivers in applications, nothing shows up.

this is my hardware specs 

Driver - Audio  	Date  	Version  	
»  	Realtek High-Definition Audio Driver
	03-2008 	6.0.1.5548 A 	

Driver - Graphics 	Date 	Version 	
»  	Mobile Intel 965 Express Chipset Family Video Driver
	03-2008 	7.14.10.1437 A 	
»  	NVIDIA GeForce Series Video Driver
	03-2008 	7.15.11.7432 A 	

If anyone can help me install thses drivers and get compiz working id greatly appreciate it.

---

### Post by Washer on 2008-09-07
[apt:envyng-core]("apt:envyng-core")
[apt:envyng-gtk]("apt:envyng-gtk")
[apt:envyng-qt]("apt:envyng-qt")

---

### Post by ichundu on 2008-09-07
> **Washer said:**
> [apt:envyng-core]("apt:envyng-core")
[apt:envyng-gtk]("apt:envyng-gtk")
[apt:envyng-qt]("apt:envyng-qt")

^+1

get these EnvyNG packages.

> **omnispyder said:**
> 
Driver - Audio  	Date  	Version  	
»  	Realtek High-Definition Audio Driver
	03-2008 	6.0.1.5548 A 	

Driver - Graphics 	Date 	Version 	
»  	Mobile Intel 965 Express Chipset Family Video Driver
	03-2008 	7.14.10.1437 A 	
»  	NVIDIA GeForce Series Video Driver
	03-2008 	7.15.11.7432 A 	


are these the drivers that came with the utilities CD of your laptop? don't know which OS your laptop came with, but they probably are drivers meant for windows, you can't use them on linux.
install the display drivers with Envy and let ubuntu "take care" for audio and other drivers :)

---

