---
title: "Can Enable EXTRA effects?? help please"
date: 2009-08-03
forum: Installation &amp; Upgrades
---

### Post by conman1994 on 2009-08-03
i have the is m760 chipset and i cant enable the extra effects! what do i need to do, i just got ubuntu today:D

---

### Post by razorboy5 on 2009-08-03
check if ur graphics card is working

System -> Admin -> Hardware Drivers

mine wasn't installed when i first install ubuntu which is my Extras didn't turn on

---

### Post by conman1994 on 2009-08-03
it says there is no proproity drivers in use???

---

### Post by Possum Films on 2009-08-03
Go to System > Administration > Hardware Drivers

If there are any drivers listed there, select one of them and click on the "Activate" button at the bottom of the window. The computer will then download and install the driver and you should be able to use desktop effects once you restart the system. 

I hope this helps.

---

### Post by conman1994 on 2009-08-03
there is no drivers i can activate in the hardware drivers thing! there is nothing there... why

---

### Post by gettinoriginal on 2009-08-03
Welcome to Ubuntu   :D
System > Administration > Software Sources > be sure that the first four boxes are checked:
[ATTACH]123522[/ATTACH]
System > Administration > Synaptic Package Manager > enter password.  When Syanptic opens, in the search bar, type ubuntu-restricted-extras, then right click it and mark for installation, also the same for linux-restricted-modules and mark it for installation.  If they are already installed (green), mark them for reinstallation.
[ATTACH]123523[/ATTACH]
  Now click apply, and when it is done, System > Administration > Hardware Drivers, and there should be one to apply.  Now effects should work.

---

### Post by conman1994 on 2009-08-03
do i install all of the -restricted things? there is more than 1

---

### Post by gettinoriginal on 2009-08-03
Most of those are dependencies of the two and will be installed with them.

---

### Post by conman1994 on 2009-08-03
what u told meto do the first time didnt work

---

### Post by gettinoriginal on 2009-08-03
Did you restart your computer ??  My fault, left that step out.

---

### Post by conman1994 on 2009-08-04
i restarted and then went back into the hardware drivers, and still nothing

---

### Post by Humanum on 2009-08-04
Is the button checked ? meaning that the proprietary drivers are installed ?

---

### Post by conman1994 on 2009-08-04
WHEN I GO TO THE DRIVERS THING THERE IS NOTHING TO CHECK OR UNCHECK!!! there is nothing there

---

### Post by gettinoriginal on 2009-08-04
I am very sorry, and I can understand your frustration, but we are trying to help, so please do not yell.  Can you post a screenshot of the window you get when you do click on hardware drivers ??

---

### Post by conman1994 on 2009-08-04
this is what i get

---

### Post by dagrump on 2009-08-04
Have you searched for linux drivers for SIS graphics cards, with google?
I would not hold my breath till you get any effects. SIS in pretty weak w/ windows. I had an old cheap winbook laptop w/SIS hardware, utter junk.
I ran 6.06 worked so-so, no hardware acceleration though. Dog slow!
Sold to a guy for his wife to use, about half what I paid for it, and was glad to see it go. Good Luck, or look for a sucker & sell it.
*********
Was just looking & in Hardware & Laptops there's a thread you might want look at. It was near the bottom of the first page when I added this.

---

### Post by conman1994 on 2009-08-05
yes but there is nothing...

---

### Post by dagrump on 2009-08-05
What do you mean there's nothing in a google search?
 Did you look at the thread in the hardware & laptop section?

---

### Post by ithicine on 2009-08-05
The SiS m760 driver for Linux does not support accelerated graphics, and as a result of this there is no way to get the "extra" effects working.  The card hardly works any better under windows due to the very, very low bandwidth offered by this card.

I'm sorry, but using the "extra" effects is completely impossible with this card due partly to its low performance, and partly due to the way its drivers work.

---

### Post by conman1994 on 2009-08-05
oh ok thanks.....

---

