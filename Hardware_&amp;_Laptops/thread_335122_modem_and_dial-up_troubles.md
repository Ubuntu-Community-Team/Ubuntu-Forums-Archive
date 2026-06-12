---
title: "modem and dial-up troubles"
date: 2007-01-09
forum: Hardware &amp; Laptops
---

### Post by c4jjm on 2007-01-09
i just installed linux edubuntu on my pc, everything worked fine and it loaded perfectly but i have a problem with my modem. the wvdail app. shows that their is a modem, and then i entered the user name and the connection dial number. but when i tried to activate the connection is said failed and told me to check to see if the hardware was there. and when i tried the auto detect it said it couldn't find the modem card](*,) 
if it helps the modem card is: Lucent Win Modem on a n hp that is running windows 2000 and it has no problem connecting to the internet



and another problem i have is not being able to change system files because they are read only.
this because they are "system files" and i need to know how to get on as the "system" instead of my account please if anyone has a suggestion please tell me or e-mail me at [email]c4@att.net[/email]

---

### Post by Simanek on 2007-01-09
If your modem is a 'Win-Modem' you might be out of luck. Apparently the Win-modems aren't complete modems. In order to save money much of the Win-modem's functionality is handled by Windows in a proprietary fashion. I'm not guaranteeing that this is your case, but I thought you should know. I ended up using an external serial-port connected modem from Creative. I imagine they are going cheap.

As for altering 'system files', you will have to use the terminal and invoke the 'sudo' command. 'sudo' stands for Super User Do. Two things that will do you a lot of good for editing root files: (enter the following in a terminal)

sudo nautilus

This will start a new session of Nautilus (file browser) with root priveledges. This means that you can move, copy or delete root priveledged files.

sudo gedit somefile.conf

This will start gEdit with root priveleges and open the file named after gedit in the command (in this case, the file is 'somefile.conf').

Be careful. I'm not responsible for your actions, but you asked.

---

### Post by Simanek on 2007-01-09
If you are interested in learning a few things, I highly recommend listening to the episodes of Linux Reality, a podcast about using Linux. Here is the site: [http://www.linuxreality.com/](http://www.linuxreality.com/)

---

