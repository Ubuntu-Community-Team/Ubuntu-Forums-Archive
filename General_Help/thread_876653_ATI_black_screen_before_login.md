---
title: "ATI black screen before login"
date: 2008-08-01
forum: General Help
---

### Post by zanemccaig on 2008-08-01
I first used the "restricted drivers" program to download and install my driver. I turned on compiz and everything worked great but then i installed a bunch of updates and it stopped working and when I would login It would make the sound i would get a white screen then it would quickly shut off again I fixed this by turning off the visual effects in failsafe gnome. then i reinstalled the driver with envy and once again it works great until i restart it then i get a black screen where my login should be. I went through the shells and then went back too tty7. once I got there it said that Ubuntu was running in low resolution i changed some settings in the menu i had there but it just booted an 800x600 crap that couldn't do visual effects. I uninstalled and reinstalled the driver and then restarted the computer same thing black screen of death but this time when i navigated around and back to tty7 i got the following message```
Exec failed for command "/tmp/firegl1.isse.dc6a1690.48927ea7.000a211e" (No such file or directory)
Exec failed for command "/tmp/firegl1.isse.dc6a1690.48927ea7.000a211e" (No such file or directory)
Exec failed for command "/tmp/firegl1.isse.dc6a1690.48927ea7.000a211e" (No such file or directory)
Exec failed for command "/tmp/firegl1.isse.dc6a1690.48927ea7.000a211e" (No such file or directory)
``` so far the only way I can get the driver to work is if i uninstall and reinstall everytime i turn the comp on or off. This is really annoying and if anyone could help me I would be very gratful. 
ps- this is my graphics card ATI Radeon X1200 series

---

### Post by Jamezracer on 2008-08-04
I have this same problem on a friend's computer who is new to linux. 2 days ago I installed linux, got it working, and it has been fine for 2 days, now she gets a blank screen at boot. gdm is a blanks screen and she can log in blindly and hear the login sound. this was with envyng. please help anyone

---

### Post by tuxxy on 2008-08-04
YOu could try reconfigure the xorg 

```

sudo dpkg-reconfigure xserver-xorg
```

then install the driver again, from system > admin > hardware drivers

---

### Post by zanemccaig on 2008-08-04
Thank you very much tuxxy that worked excellent for me i've rebooted my computer a couple of times and everything works perfectly!

---

### Post by tuxxy on 2008-08-05
Glad to hear zanem :)

---

