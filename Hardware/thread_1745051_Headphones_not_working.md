---
title: "Headphones not working"
date: 2011-04-30
forum: Hardware
---

### Post by sikuneh on 2011-04-30
I have a pair of Sennheiser PC 350 headphones and they don't seem to output any sounds in Ubuntu 11.04. It's not the audio or the laptop because when I unplug the headphones the sound is just fine. I checked their website and didn't see a driver, is there any way to fix this?

---

### Post by C.C.C.P. on 2011-04-30
What kind of laptop are you using?

---

### Post by sikuneh on 2011-04-30
My laptop is a Dell Studio Laptop 1747. Do you need the specs?

---

### Post by C.C.C.P. on 2011-04-30
Try to open  /etc/modprobe.d/alsa-base.conf  [FONT=monospace]and add following line, then reboot[/FONT]
options snd-hda-intel model=m51va

---

### Post by sikuneh on 2011-04-30
I'm having a sort of permissions issue atm. I am the administrator but I can't do hardly anything. For example: I can't modify the alsa-base.conf file. This may not be the place to ask it but I have been having this problem since I upgraded to 11.04. Installed using WUBI.

---

### Post by C.C.C.P. on 2011-04-30
Just open the terminal and type 
> sudo gedit   /etc/modprobe.d/alsa-base.conf 
it will open gedit with root rights
just find the other lines like this, and add
>  options snd-hda-intel model=m51va 	
save the file close it and reboot, hope it is going to fix it!

---

### Post by sikuneh on 2011-04-30
No luck. Any other ideas?

---

### Post by C.C.C.P. on 2011-04-30
What kind of sound card you have?

---

### Post by sikuneh on 2011-04-30
"IDT High Definition Audio CODEC" I think.

---

### Post by Novacaptain on 2011-04-30
I have the same model laptop as you, and had the same problem, too. 

Did you check this thread?
[http://ubuntuforums.org/showthread.php?t=1743872](http://ubuntuforums.org/showthread.php?t=1743872) 

The solution is basically the same/similar as to what has been posted here (the difference is that I'm not using WUBI, though, I have my installation on a separate partition).

What happens when you try: 

gksudo gedit   /etc/modprobe.d/alsa-base.conf

---

### Post by cymbaline42 on 2011-04-30
Just a thought, but do you know whether your auxiliary input (where you insert the headphone jack) is working?  Maybe there is some kind of loose conduct or it is damaged?

---

### Post by sikuneh on 2011-04-30
My headphone jack works just fine in Windows. 

Does it have to be a proper restart because I haven't been able to properly shut down since 11.04; which I already have a support ticket.

Edit:
Thanks, it finally works. I'm not entirely sure what fixed it but I have a good idea that it was restarting (even if it didn't fully complete restarting). I'm not entirely sure. I also went [here](http://www.techrecipes.net/operatingsystem/ubuntu/fix-no-sound-headphone-jack-dell-xps-studio-16).

---

