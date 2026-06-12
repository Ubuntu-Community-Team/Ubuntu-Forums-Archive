---
title: "Deskjet 5650"
date: 2005-07-06
forum: Hardware &amp; Laptops
---

### Post by asimon623 on 2005-07-06
Ok, I got this printer to work locally on the linux box, and I got my windows xp machines to finally be able to access CUPS configuration remotely and when I do add printer, it progresses to the next step, select model, but this DeskJet 5650 isn't a choice. What do I do.

---

### Post by skirkpatrick on 2005-07-06
I've got a Deskjet 5550 on my Ubuntu machine.

On the XP side, you need to either have the disc that came with the printer or download the driver from HP.  When you get to that step, select "Have Disk" and then browse to where the .inf file is.  Depending on whether you used the CD or the downloaded driver, you may have to dig down to get it.

I did notice that my XP machines seem to have some lag from the time I tell them to print until printing actually starts using Samba.  This doesn't happen on the one Win98 machine.  To solve this, my XP machines print directly to Cups using IPP.

---

### Post by asimon623 on 2005-07-06
thanks, you've been very helpful. I have lost my disk, and the only other option that HP gives is to use their installer, which doesn't give the url option of connection. Would it be possible to upload your cd?

---

### Post by manicka on 2005-07-06
[http://www.ubuntuforums.org/showthread.php?t=20384&highlight=samba+printing](http://www.ubuntuforums.org/showthread.php?t=20384&highlight=samba+printing)

---

### Post by manicka on 2005-07-06
or if you have an old pc lying around you could make a dedicated print server

[http://www.ubuntuforums.org/showpost.php?p=239958&postcount=7](http://www.ubuntuforums.org/showpost.php?p=239958&postcount=7)

---

### Post by skirkpatrick on 2005-07-06
Ok, I've tried to gather a couple of your threads together in one place.

In this one ([http://www.ubuntuforums.org/showthread.php?t=45945)](http://www.ubuntuforums.org/showthread.php?t=45945)), I talked about setting up Cups to print directly to it.  In this thread, I could have sworn I had seen where you couldn't get the correct driver loaded without going through the entire setup.  You can with the .exe you downloaded from HP.  When you run the .exe, cancel out.  It should have created a directory called "5600" (it did when I ran it).  When you go through the standard Add Printer and I said somewhere to click the button called "Have Disk", you'll need to browse to wherever the "5600" directory was created and then go to "enu\drivers\win2k_xp".  There you will find the .inf file, which sets up the driver.

Like I said in the other thread, printing with XP to Ubuntu is easier and faster printing through Cups instead of Samba.  Now if you'd like some more help on this, please don't create 3 more threads all about the same thing.

---

### Post by manicka on 2005-07-06
[QUOTE=skirkpatrick]Now if you'd like some more help on this, please don't create 3 more threads all about the same thing.[/QUOTE]

Hey, we've all been new to forums at one time or another. 
There's nicer ways to make your point than this.

---

### Post by skirkpatrick on 2005-07-07
That is true, I could have worded it differently.  However, if I've subscribed to this thread to receive emails to watch it to help and activity suddenly stops on this thread and starts up in one or more threads, I may not continue to be able to help unless I sift through 600+ updated topics a day.

---

