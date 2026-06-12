---
title: "Need Help Updating BIOS on AO532h"
date: 2010-11-28
forum: Hardware
---

### Post by crucialhoax on 2010-11-28
Hello,

I read here: [https://help.ubuntu.com/community/AspireOne/532h](https://help.ubuntu.com/community/AspireOne/532h)  that the BIOS is "easily" updatable with a FreeDOS USB stick. Thing is every forum, tut, or manual I follow results in failure. The USB drive never boots the screen is black and says "FreeDOS" in the upper left corner. If I do get it that far. Most of the time the 3 BIOS files that are vital to the update do not fit because every tut is for a Floppy drive. Well all 3 files are too big for that. So I am screwed in that aspect as well. I would really like step by step instructions on  how to do this successfully because it fixes a major bug on this laptop. Any help is appreciated. Thanks!

---

### Post by crucialhoax on 2010-11-29
T T T
o h o
   e p 

Please I need help lol thanks again

---

### Post by PDA1 on 2010-11-29
[SIZE=4]Not sure if I can help but my friends Acer Aspire one had similar problems.  We had to download the program using Windows.  Here's the solution we used;

[FONT=Arial]1. Go to the following address- (it'll         download a zip file)(the file you'll need is attached herein)
      [/FONT][/SIZE]     [SIZE=4][FONT=Arial]
[http://global-download.acer.com/GDFiles/BIOS/BIOS/BIOS_Acer_3310_A_AOA110%20&%20AOA150.zip?acerid=633850493862245097&Step1=Netbook&Step2=Aspire](http://global-download.acer.com/GDFiles/BIOS/BIOS/BIOS_Acer_3310_A_AOA110%20&%20AOA150.zip?acerid=633850493862245097&Step1=Netbook&Step2=Aspire)

2.  Unzip the file (use Windows to unzip)

3.  Open the folder and copy two files to a formatted FAT
usb stick. Rename the file FLASHIT to FLASHIT.EXE and the second file
3309.fd(bios file) to ZG5IA32.FD 

3. Insert the usb stick into the usb** left hand side** make sure the charger is plugged in. 

4. Hold down keys fn+esc and power up the laptop.  When the power led begins to blink release the two buttons and press the power button just once, observe the usb stick flashing indicating it's flashing the bios. 
[/FONT][/SIZE][SIZE=4]...hope that helps
[/SIZE]

---

### Post by crucialhoax on 2010-11-30
I do not have windows installed on this machine. I do however have a windows machine I can use to make the bootable drive if its easier.

---

### Post by PDA1 on 2010-11-30
Yes, that's exactly how I did it- got the programs using Windows and installed them on a usb.

---

### Post by mebitek on 2010-11-30
to be sure that all should work like a charm I suggest:

1- disconnect your hard drive
2- connect a new one
3- install windows version needed by the manufacture flash utility
4- boot windows
5- flash your bios
6- disconnect the hard drive
7- connect the hard drive with ubuntu
8- enjoy

I say this cause I burn a bios with freedos tecnique, so I use this method to upgrade my bios.

cheers

---

### Post by PDA1 on 2010-11-30
The computer we fixed was a dual boot and at no time did we use the Windows os on that machine nor could we- the bios was messed up.

Try what I suggested.  I understand your frustration- all of the sites you look at show some simple solution that works for everyone...but  you.  That's what I thought until I tried the fix I mentioned.  For whatever reason the bios reflash has worked 2 times so far or about a years period of time.

---

### Post by crucialhoax on 2010-11-30
Alright Ill give it a shot then. Do I have to rename the files? The files you renames were different names to begin with.

---

### Post by PDA1 on 2010-11-30
CAUTION- DO NOT reflash you bios until you verify that the bios specified above is the exact one for your machine.

That said....


Rename the file FLASHIT to FLASHIT.EXE 

Rename 3309.fd(bios file) to ZG5IA32.FD 

Rename them precisely like that.

---

### Post by crucialhoax on 2010-11-30
Couldnt get it to work. Whomever posted that information on the laptop community docs needs to reply in here because its not as "easy" for everyone. I have tried dd tried grub tried everything.

---

### Post by PDA1 on 2010-11-30
Have you tried Ubuntu LiveCD?

---

### Post by crucialhoax on 2010-12-04
How would an ubuntu live cd help?

---

### Post by PDA1 on 2010-12-04
Live CD will at least get you booted into Ubuntu where you can either install it or just try it out.  The foregoing assumes you BIOS is ok.

Give it a try....it'll only take a few minutes to find out if you can boot into Ubuntu.

---

### Post by crucialhoax on 2010-12-05
I stated on the first page of this thread that the laptop that needs the BIOS update is using ubuntu and ubuntu only. So a live cd is a waste of time.

---

### Post by PDA1 on 2010-12-06
If you're so inclined I'll buy your computer from you.

Just send a PM telling how much you want for it.

---

### Post by crucialhoax on 2010-12-09
I appreciate your help but no thanks. Ill wait for a better solution.

---

### Post by crucialhoax on 2010-12-11
I created my own somewhat beat around the bush solution to the problem.

Step 1: 

Back up the drive using Clonezilla Live

Step 2:

Create a bootable Windows 7 usb drive

Step 3:

Boot into Gparted Live and format drive to ntfs

Step 4:

Install Windows 7

Step 5:

Install BIOS update straight from windows

Step 6:

Boot back into Clonezilla to restore previously saved image

Step 7:

Enjoy the fix :)

---

### Post by Maximus559 on 2010-12-31
I had this problem with my AO532h a while back. Here's what worked for me (as far as I can remember):

1) Follow the instructions [here]("http://www.bay-wolf.com/usbmemstick.htm") to create a bootable flash drive (note: you will need to use Windows).

2) Get the latest BIOS from acer [here]("http://global-download.acer.com/GDFiles/BIOS/BIOS/BIOS_Acer_1.25_A_A.zip?acerid=634139072709889300&Step1=Netbook&Step2=Aspire%20One&Step3=AO532h&OS=722&LC=en&BC=Acer&SC=PA_7") (1.25 at time of writing).

3) Copy the DOS version of the update utility to the flash drive.

4) Boot your netbook from the flash drive.

5) Run the batch file provided by Acer and you're done.

This BIOS update fixed a bug where the system would randomly go into standby mode when running on battery power.

---

