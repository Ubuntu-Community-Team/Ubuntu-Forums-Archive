---
title: "Nvidia Drivers"
date: 2008-10-23
forum: General Help
---

### Post by Arukas on 2008-10-23
I installed some restricted drivers for my nvidia card, my my graphics are still slugish.  Animations and some multimedia play really slow.  Is there something else I need to install? or was justing using synaptic all I can do?

---

### Post by qpieus on 2008-10-23
Check to see if the nvidia driver is being used. Open up the file /etc/X11/xorg.conf and look for the "Driver" line. If it says ```
Driver          "nvidia"
``` then the restricted nvidia driver is being used. If the Driver line says "nv", that is NOT the restricted nvidia driver.

Or use this command in a terminal```
grep nv /etc/X11/xorg.conf
``` This command will return the appropriate line from the xorg.conf file.

---

### Post by tuxxy on 2008-10-23
What card are you running there, if its latest models you may be better trying the drivers from nvidias homepage.

---

### Post by Arukas on 2008-10-23
In my file it says.

Driver		"nvidia"







> **tuxxy said:**
> What card are you running there, if its latest models you may be better trying the drivers from nvidias homepage.


I am using a 8800 GT.  How can I use an Nvidia driver from their site?

---

### Post by Arukas on 2008-10-23
I downloaded the latest driver from Nvidia, and it tells me I have to exit X to install it?  Does anyone know how to install the nvidia driver?

---

### Post by agathian on 2008-10-23
I had good success with EnvyNG, when installing hardy in my laptop. give it a spin - [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by Arukas on 2008-10-24
I can't find envy in the synaptic manager, and I have all the boxes check.  It says its in universe and i have it check.  Where do i get it?

---

### Post by Arukas on 2008-10-24
Okay I figured my problem out.  Its something I misunderstand.  i was looking for it in the sym installer, and it wasn't there.  I didn't realize i had to type the command to make it install.  

That actually solves answer my questions.  Thanks.

---

