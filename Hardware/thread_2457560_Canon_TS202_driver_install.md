---
title: "Canon TS202 driver install"
date: 2021-02-04
forum: Hardware
---

### Post by all-nighter on 2021-02-04
Hi all,
I have a Canon Pixma TS202 I'm trying to hook up to 20.01.1 LTS (Gnome 3.36.b) but so far it won't install the Canon driver. I D/L the Debian driver from their site and used Package Manager to extract the files but that's as far as I got. After adding the new printer, it searched for drivers but apparently didn't find  it
I've been using Windows until about a year ago and have used Ubuntu for some time. I I like it, but I have very little experience going 'under the hood' (command line) to do things such as installing drivers.  Does anyone have any experience with that model printer and his version of Linux? Any help would be much appreciated.
Jim

---

### Post by brian_p on 2021-02-04
I am disinclined to follow the Canon driver route when there may be a more modern technique available. Give the output of ```
lsusb -v | grep -A 3 bInterfaceClass.*7
```

---

### Post by all-nighter on 2021-02-05
I must be doing something wrong, as I get 'Couldn't open device, some information will be missing' after I hit enter after pasting that.  Am I missing something?   Also, when I tried the 'sudo' as in "sudo lsusb -v | grep -A 3 bInterfaceClass.*7" I got a column of  "can't get debug descriptor: Resource temporarily unavailable"

---

### Post by brian_p on 2021-02-05
> **all-nighter said:**
> I must be doing something wrong, as I get 'Couldn't open device, some information will be missing' after I hit enter after pasting that.  Am I missing something?   Also, when I tried the 'sudo' as in "sudo lsusb -v | grep -A 3 bInterfaceClass.*7" I got a column of  "can't get debug descriptor: Resource temporarily unavailable"

Do ```
lsusb -v | grep -A 3 bInterfaceClass.*7 > out.dat
``` and post the content of **out.dat**.

---

### Post by all-nighter on 2021-02-06
Sorry, Brian. Still no go.  I tried it with the printer installed after it found a 'gutenprint' driver. Then without the driver and again after deleting the printer from the machine. A real head-scratcher to be sure.
Jim

---

### Post by all-nighter on 2021-02-06
Sorry, Brian. Still no go.  I tried it with the printer installed after it found a 'gutenprint' driver. Then without the driver and again after deleting the printer from the machine. All I got was "Couldn't open device, some information will be missing"
 A real head-scratcher to be sure.
Jim
(also, I can't seem to delete duplicate posts)

(add) is there a way to use a driver for this machine that's a different model?  I'm pulling my hair out at this point.

---

### Post by brian_p on 2021-02-06
> **all-nighter said:**
> Sorry, Brian. Still no go.  I tried it with the printer installed after it found a 'gutenprint' driver. Then without the driver and again after deleting the printer from the machine. All I got was "Couldn't open device, some information will be missing"
 A real head-scratcher to be sure.

Does the command ```
lsub
``` show the printer?

> 
(also, I can't seem to delete duplicate posts)

I do not think you can. Don't worry about it, Jim.

> 
(add) is there a way to use a driver for this machine that's a different model?  I'm pulling my hair out at this point.

It should not be necessary and I do not want to go there. If lsusb cannot see the printer, there isn't any point in considering that route anyway.

---

### Post by all-nighter on 2021-02-09
Oddly enough, when I open 'printers' i shows it but Lsub (or Lsusb)  returns:

"Command 'lsub' not found, did you mean:

  command 'lsusb' from deb usbutils (1:012-2)
  command 'qsub' from deb gridengine-client (8.1.9+dfsg-9build2)
  command 'qsub' from deb slurm-wlm-torque (19.05.5-1)


Try: sudo apt install <deb name>"

And Lsusb gives me:

"Command 'Lsusb' not found, did you mean:


  command 'lsusb' from deb usbutils (1:012-2)


Try: sudo apt install <deb name>"

---

### Post by CelticWarrior on 2021-02-09
The command is '**lsusb**' (case sensitive).

---

### Post by all-nighter on 2021-02-16
Sorry for disappearing fr a while but I was called away and couldn't respond.

 Anyway, 'lsusb does show the root hub, the mouse and the keyboard but no printer even though the 'add printer' screen shows that Canon printer as if it was already installed.  Kind of making me crazy here.

---

