---
title: "hardrive buying"
date: 2009-04-24
forum: Hardware
---

### Post by shadowlands on 2009-04-24
I would like to buy a harddrive for my acer laptop.  How do I pick a harddrive and what should I buy. This is the second hardrive I have killed.

---

### Post by Barry Carroll on 2009-04-24
Firstly you need to find out if your laptop takes ide or sata hard drives.  You should be able to find this out by looking at the specifications or post back the model number and we can figure it out.

After that it's down to the performance vs power question.  Do you want a faster 7200rpm drive or will a 5400rpm be ok.  I think the power consumption gap between them isn't as large as it used to be but still needs consideration.

How are your hard drives failing?  Are you also sure that it is a true hardware failure too?

---

### Post by shadowlands on 2009-04-25
no I am not sure it is a true hardrive problem? How would I test it?

---

### Post by NathanDS101 on 2009-04-25
do you safely turn off your computer and stuff because if you fryed 2 hard drives maybe your doing something wrong any problem on why it fryed any warning more detail please. Because if you buy another one you dont want that one to get fryed do you?

---

### Post by Barry Carroll on 2009-04-25
Just describe what is happening or what happened to make you think the hard-drive is dead.  What happens when you turn on your machine?

---

### Post by shadowlands on 2009-04-25
The computer started making a weird whining noise. Like it does not want to think.  The computer then slows down and goes gray and freezes up.  Sometimes when I restart it and it reboots I get 
got an error message telling me I could not lunch "Add/Remove" failed to execute child process "/usr/bin/gnome-app-install" (input/output error). 

At other times the error message is 
"[ 6138-205400] end_request: I/0 error, dev sda, sector 142342184" ?

---

### Post by WatchingThePain on 2009-04-25
Hmm I/O error.
Maybe the bios has a problem.
Does it emit beeping sounds?.

---

### Post by shadowlands on 2009-04-25
It does not make a beeping noise but it sounds strange. It makes a whinnying sound.

---

### Post by Barry Carroll on 2009-04-26
It does sound like a hardware problem now, but I have to wonder what the underlying cause is.  Do you think you could get your laptop running long enough to do:

```

sudo apt-get install smartmontools

sudo smartctl -H /dev/sda
sudo smartctl -a /dev/sda > diskreport.txt

```

The first smartctl command should tell you if the drive is healthy or not, as determined by SMART, and your disk also has to be smart capable.

The second smartctl command will give you a detailed report on your disk's stats.  If it runs ok please post back the results.

What is the exact model number of your acer laptop?

---

