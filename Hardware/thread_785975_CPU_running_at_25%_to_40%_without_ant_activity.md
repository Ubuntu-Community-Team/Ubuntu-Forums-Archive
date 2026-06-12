---
title: "CPU running at 25% to 40% without ant activity"
date: 2008-05-07
forum: Hardware
---

### Post by hempar on 2008-05-07
My computer CPU is always 25% to 49% active all time even I'm not running any application or any activity. How can i fix it.

---

### Post by tamoneya on 2008-05-07
the image didnt get uploaded.  Look at the attachment dialog box below the post window.

---

### Post by gnulogic on 2008-05-07
sudo apt-get remove evolution-data-server

---

### Post by NightwishFan on 2008-05-07
Upload the image with file attachments. Perhaps you did an install with a bad cd generally that is the reason for that happening. Check the cd for errors. Also what are your specs?

---

### Post by hempar on 2008-05-07
My Specs are in screen shot attachment.

Brand : Dell SC400
CPU : Pentium 4 2.4 GHz
Memory : Crucial 1.5 GB
Video Card : Nvidia ?

I am new to Ubuntu. Please let me know any more info needed but i had Ubuntu for two weeks and every thing is working fine so far (Video card, Sound Card and WiFi ). Only CPU is running high.

---

### Post by gnulogic on 2008-05-07
take a look at your processes tab it is being caused by a bug in the evolution-data-server.  

removing it with the command earlier will fix your problem with your cpu.

---

### Post by tamoneya on 2008-05-07
why do you think it is evolution-data-server.  It could be many things.  I personally had a similar problem a week ago.  It was an opera plugin that adapted the 32 bit flashplugin-nonfree to my 64 bit system.  But yeah you should take a screen shot of the processes tab.  That way we can see what is wrong and tell you what should be removed, added or editted.

---

### Post by hempar on 2008-05-07
Thank for quick reply gnulogic
 but evolution-data-server using 0% CPU in process and only system monitor using 2% CPU.

---

### Post by hempar on 2008-05-07
> **hempar said:**
> Thank for quick reply gnulogic
 but evolution-data-server using 0% CPU in process and only system monitor using 2% CPU.

My Process Screen shots

---

### Post by tamoneya on 2008-05-07
please hit the "% cpu" column header so that it sorts the tasks by % cpu usage.  This way we can zero in on the process that is eating your CPU cycles.  Then of course take another screenshot.

---

### Post by sdennie on 2008-05-07
It sounds similar to this thread: [http://ubuntuforums.org/showthread.php?t=772961](http://ubuntuforums.org/showthread.php?t=772961)

---

### Post by hempar on 2008-05-07
Screen Shot shorted by %CPU

---

### Post by tamoneya on 2008-05-07
that to me says that you are using a totla of 11% but if it is still sluggish you should look at the thread posted above since that appears to be the largest use of resources.

---

### Post by hempar on 2008-05-07
Thank you tamoneya and vor. I will check thread you said.

---

### Post by hempar on 2008-05-07
I installed htop. By htop reading CPU is running under 5%. Ubuntu Hardy System minitor reading incorrecty. Thank you folks.

---

