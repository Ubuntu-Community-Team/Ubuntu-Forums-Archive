---
title: "HP Pavillion dv6000 with Nvidia 7150M - display problems"
date: 2009-10-16
forum: Hardware
---

### Post by gustafson on 2009-10-16
Hello.

I am a new Ubuntu user running Jaunty Jack and I managed to get the correct resolution with Nvidia x server settings app, and the Nvidia binary org 173 driver.  However, after going to system>preferences>display>x server display configuration I get the message "unable to create x config backup file" when I try to save x config backup.  Consequently, every time I log out or boot up I have to readjust the display settings.:guitar:

Is there somewhere I need to manually dump a config file?

thank you for any help.

---

### Post by Dark_Stang on 2009-10-16
Hmm, mine worked just fine with the 173 driver. Try updating to the 180 driver and see if that works better, that's what I'm running right now. Also, you can install the nvidia settings manager which works much better for nvidia cards.

---

### Post by gustafson on 2009-10-17
thank you for your help.  

I switched to the version 180 driver and readjusted the resolution in Nvidia X server settings.  I changed the resolution to 1200 x 800 in the Server display settings, then tried to save to x configuration file.  It wouldn't save and gave me "unable to create new x config backup file  '/etc/X11/xorg.conf.backup'. 

the resulting problem?

I have to readjust display when powering up, or logging on.

Also... have you had any boot errors with your dv6000?

dv6000 - amd - nvidia 7150m

---

### Post by VasiliyChem on 2009-10-17
Mmmm... As I remember, I have seen the solving on Russian site... But I've just forgotten it:(((
---
Added:
---
Here it is (it's something as facebook!)
   [This site]("http://vkontakte.ru/reg4464558") Using this link you will see the group named "Ubuntu Linix", and the answer is here! Try!
 I'm Russian, then, please, sorry for my mistakes, and, if it's possible, tell me the correct variant! thank you!))

---

### Post by gustafson on 2009-10-19
I still have to adjust resolution every time at boot up.  I have entered the command to give nvidia root permission, but Ubuntu still boots with 800x600 resolution.  

The boot issues appear to be unrelated.  I found a fix.  HP lists a bios update.  (ttp://h10025.www1.hp.com/ewfrf/wc/document?lc=en&dlc=en&cc=us&lang=en&docname=c01087277&product=1842155#c01087277_bios)

However, the script won't run in WINE so I have to reinstall vista (drag), run the bios update, and then reinstall UBUNTU.  If that doesn't work, my issues appear to qualify for a free repair.  

Still working on the graphics issue though.  I added Nividia x server settings to startup, entered the root command to give it root permission, and added it to menu.  I am new to UBUNTU so if I have missed something basic, let me know.

---

### Post by Dark_Stang on 2009-10-19
You are saving the xorg.conf file after making adjustments, right?

---

### Post by gustafson on 2009-10-21
when I push the button labeled "save to x configuration file" I get the message  "Unable to create new X config backup file '/etc/X11/xorg.conf.backup'."

Gustafson

---

### Post by gustafson on 2009-10-27
Solved my problem.  I upgraded to Karmic Koala and when I was asked if I wanted to use the graphics driver vender's tool I said no.  I could then adjust the resolution in a very limited window that would not come up in Jaunty Jack.

---

