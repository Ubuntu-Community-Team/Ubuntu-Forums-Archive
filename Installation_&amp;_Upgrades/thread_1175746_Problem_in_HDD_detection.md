---
title: "Problem in HDD detection"
date: 2009-06-01
forum: Installation &amp; Upgrades
---

### Post by joyneo04 on 2009-06-01
[SIZE=1]Dear all,[/SIZE]
 [SIZE=1]I am a new user of ubuntu.Recently i received the cd of ubuntu 9.04.Earlier i was using ubuntu 8.04.so to install the new version i formatted my hdd through the partition manager.After formatting i saw a block mentioning as unallocated one.so i tried to allocate it as new partition and when i click the applied button the whole cell was covered with black outline.then when i tried to install the newer version,in step 4 it was saying it can't detect the hard disk,saying no root file system mentioned.[/SIZE]
 [SIZE=1]I want to know whether my hard disk has gone for a toss,or what else can i do to make the hard disk again uasable with ubuntu....[/SIZE]
 

 [SIZE=1]Regards[/SIZE]
 [SIZE=1]Satyabrata Sarkar[/SIZE]
 [SIZE=1]+91-9740833897[/SIZE]

---

### Post by joyneo04 on 2009-06-01
[SIZE=1]Dear all,[/SIZE]
 [SIZE=1]I am a new user of ubuntu.Recently i received the cd of ubuntu 9.04.Earlier i was using ubuntu 8.04.so to install the new version i formatted my hdd through the partition manager.After formatting i saw a block mentioning as unallocated one.so i tried to allocate it as new partition and when i click the applied button the whole cell was covered with black outline.then when i tried to install the newer version,in step 4 it was saying it can't detect the hard disk,saying no root file system mentioned.[/SIZE]
 [SIZE=1]I want to know whether my hard disk has gone for a toss,or what else can i do to make the hard disk again uasable with ubuntu....[/SIZE]
 

 [SIZE=1]Regards[/SIZE]
 [SIZE=1]Satyabrata Sarkar[/SIZE]
 [SIZE=1]+91-9740833897[/SIZE]

---

### Post by 73ckn797 on 2009-06-01
If you have no other OS installed then boot again from the CD and delete all partitions and start over with a single partition. I have not experienced what you describe, however. If you get the same problem you will need to check the drive for errors. 

From boot disk go to terminal and enter ```
fsck
```and see what it will tell you. Maybe run the command as a first measure.

---

### Post by joyneo04 on 2009-06-01
sir,actually m giving you some details,
i was having 80gb hdd,
20gb , 20gb, nd 40gb.
my earlier version was installed in 20gb,so this  time i thought of making a partition of 8 gb from the 40gb section and install the new version in that section.i did it from the partition manager.but after formatting the drive that contains the earlier version i saw the .
   	 	 	 	 	 		 	 	   	 	 		 			20gb 			20gb 			8mb linux swap covered with maroon colour outline 			rest amount 			before change 		 		 			20gb  			20gb 			linux swap removed 			rest amount 			
		 		 			20gb formatted 			20gb 			unallocated section 			
		 		 			20gb 			20gb 			new partituion to do 			
		 		 			covered with black colour outline,wn tried to apply change 			covered with black colour outline,wn tried to apply change 			covered with black colour outline,wn tried to apply change 			
		 	  

this thing,this was the step done by me...kindly suggest.as m quite worried about the situiation.

---

### Post by joyneo04 on 2009-06-01
sir please find the attached sheet which will make you a little bit clear abot the problem,,,kindly suggest....

---

### Post by LewRockwell on 2009-06-01
If there is nothing on the hard drive that you need then I would use DBAN to totally clean the hard drive.  Then you can partition and install as you desire.

---

### Post by joyneo04 on 2009-06-01
what is dban and how can i run it

---

### Post by joyneo04 on 2009-06-01
kindly give me the whole procedure and links as i am a very beginner in this field...i use hit and trial method...so please do me this favour.

---

### Post by LewRockwell on 2009-06-01
[http://www.dban.org/](http://www.dban.org/)

---

### Post by joyneo04 on 2009-06-01
thanks a lot....your active coperation means a lot to me....

---

### Post by joyneo04 on 2009-06-01
sir....gt the answer....first running DBAN and then after making new partition...let me try this as well as yours one....thanks for your active cooperation....;)

---

### Post by LewRockwell on 2009-06-01
you could also use [http://www.killdisk.com/](http://www.killdisk.com/) if for some reason the DBAN doesn't work for you.

---

### Post by Cornbreadly on 2009-06-01
For simplicity's sake, you may just beable to reformat the partition in the installed.  Dban and killdisk will render the all information unrecoverable on the HD.  You do not need to do that for normal home usage.  

Select the guided option in the installer that wipes the HD.  That would be the easy way.

---

### Post by joyneo04 on 2009-06-02
Sir whatever you are saying i am unable to understand as i can't see any of these option....right now i trying to run dban but how to run it....i am giving you the entire procedure i was following.....

Downloaded thedban software.....
version was flash drive version.....
i connected my flashdrive into the usb port....
then i booted my computer....
it was showing....
GRUB loading stage 1.5
GRUB loading....please wait
Error 22,

what does it mean....

also i am giving you the config of my system...
Motherboar Mercury,Intel processor,80 gb SATA HDD, Linux new 9.04 version installer cd,.
Now provide me the step i have to follow.

please do bear with me as i am a very new user.

---

### Post by joyneo04 on 2009-06-02
please do me this favour...i will remain ever grateful to u all....

---

