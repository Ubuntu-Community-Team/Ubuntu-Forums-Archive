---
title: "my hard drive will not format when i try to install"
date: 2009-09-26
forum: Installation &amp; Upgrades
---

### Post by dylanpyrodrake on 2009-09-26
ok i have to install a new os so i am installing the karmic koala alpha 5    and it won't let me format my hard drive "input/output error during read on /dev/sda"  and then it says "input/output error during write on /dev/sda"  it says the second one twice then it says ," The creation of swap space in partition #5 of SCSI1 (0,0,0) failed."   then it goes and takes me back to the screen that says where are you and wants me to choose the time zone againand i have done this entire prosses about 50times and it always says the same thing ok right now i'm using the try kubuntu feature with out change to your files but i want to be able to use the hard drive what should i do??????????????????????? ?????????????????????????????????????????????????????????????????????????????????????

---

### Post by mo0nykit on 2009-09-26
Hello!

I have tried reviving an old computer and installation freezes at more or less the same point (HDD format fail, loading additional components fail at around 30%). I did a memtest86+ and finally decided that corrupted RAM was the culprit. Are you sure your RAM is good?

---

### Post by dylanpyrodrake on 2009-09-26
well how would i be able to tell if it was or not

---

### Post by rreese6 on 2009-09-26
ok memtest from the LiveCD screen test memory. start it and go to bed.

but check to make sure that you have the power and the data cable securely plugged in on the HD.
if that looks good open a terminal (after you boot from the livecd and run the desktop.)
and type fdisk -l to see that the hd is functional.
if it looks like there is garbage there of fdisk fails, then most likely you have something wrong in bios or cabling.
check bios to make sure that the drive is listed as the first hd bootable (type setting : sata and pata).
Is the drive a PATA (IDE) or SATA?

if you can see the partitions with fdisk -l
then type```

sudo gparted
```
delete all partitions on the drive (if you are only putting Linux on it.) Hit apply., let it finish.
then close the terminal and hit the install icon again.

---

### Post by dylanpyrodrake on 2009-09-26
can i format the hard drive from the terminal konsole thing??? and if so whats the command ? thanks for your help be the way

---

### Post by rreese6 on 2009-09-26
run gparted in the terminal...it is a GUI program.
It will partition and format for you.

---

### Post by dylanpyrodrake on 2009-09-26
ok i installed it but it then said when tryed to run it that ,"Since GParted is a powerful tool capable of destroying partition tables and vast amounts of data, only root may run it."  what should i do i'm realy confused lol

---

### Post by mo0nykit on 2009-09-26
Okay, I'll assume you'll want to wipe out your hard disk to make way for your new Kubuntu installation. Everytime you need **root** privileges, prefix your commands with **sudo** ```
sudo gparted
```

---

### Post by dylanpyrodrake on 2009-09-26
ok i did all that but  it still gave me those writing messeges lol what should i do now?

---

### Post by mo0nykit on 2009-09-26
What are those writing messages? Kindly post them :)

---

### Post by dylanpyrodrake on 2009-09-26
"input/output error during read on /dev/sda" , "input/output error during write on /dev/sda" it says the second one twice then it says ," The creation of swap space in partition #5 of SCSI1 (0,0,0) failed."

---

### Post by mo0nykit on 2009-09-27
Okay, I've run into those errors before. RAM was the culprit. Did you do a memtest86+?

HOWTO:
1. Reboot from the Kubuntu CD.
2. On the first menu that comes up, select Test Memory.

---

### Post by rreese6 on 2009-09-27
If the Memory tests pass, then check cables to hard drive.
when you power up, enter BIOS and see if you can detect the hard drive.
 one other Item, is the hard drive SATA?

Now if your memory failed, then open case.
make sure power is off and unplugged.
touch the case with your hand to remove static.
take out memory one at a time. use the blank side of a bussiness card or a small piece of white paper (or match book cover) and rub gold connectors on both sides until shiny. re-insert card. do the same for other memory cards.
plugin power bot up machine and run memory test again from the LiveCD bootup menu.

---

### Post by dylanpyrodrake on 2009-09-27
ok thanks i will and by the way no cables (laptop )  does that make any difference by the way i didn't ask that ???

---

### Post by rreese6 on 2009-09-27
Knowing it is a laptop helps...now it either a bad hard drive or memory...unless we become more enlightened...what make and model of laptop is it?

---

### Post by dylanpyrodrake on 2009-09-27
it is a Tosiba Satellite L305-S5944    and is using a Western Digital Scorpio blue 250 GB hard drive

---

### Post by rreese6 on 2009-09-28
did you run the memory test from the LiveCD?
You need to do that.

---

