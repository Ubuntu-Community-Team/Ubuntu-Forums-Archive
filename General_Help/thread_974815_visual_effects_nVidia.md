---
title: "visual effects nVidia"
date: 2008-11-07
forum: General Help
---

### Post by O011235813 on 2008-11-07
Hey,

I apologize if this has been addressed in a previous thread, I looked through the forums and couldn't find it.

I am trying to enable the visual effects on my laptop. I have a dual gForce 7900 graphics cards. I get to the point where i can enable and install the drivers. After i do so, I restart, and I wind up with a black screen, and my terminal. 

How do iget from here to my desktop? and finish enabling the visual effects?

Note: I am very, very, new to Ubuntu, so i barely know how to use the terminal yet.

Thank you for all the help.

---

### Post by GlennW on 2008-11-07
First of all, welcome to Linux. The first thing is that you have to go to System>Administration>Hardware Drivers. Hopefully, there will be a driver that is there but requires activation. Once you activate the appropriate nVidia driver, you'll no doubt have to restart X (ctrl + atl + backspace). Then, if you haven't already installed compiz, open a terminal. Applications>Accessories>Terminal. Then when that terribly intimidating window opens (it's actually your best friend!) enter "sudo apt-get install compiz" without the quotation marks. That should do it.

The fun is just beginning..........

---

### Post by O011235813 on 2008-11-07
hey,

thanks. Yeah i enabled the correct drivers, and then restart. but for some reason, i can't get back to the Ubuntu desktop. It shows the Ubuntu loading screen, and then it goes to black background, white text, and it looks like the terminal.

"login:
password:"

and then i put in my username and password. and then it takes me to "daniel@computername: ~$"

I don't know where to go after this to get to my actual desktop. Thanks for the help, i really need it, and thanks for the welcome :D i hope i can get better at this over time.

---

### Post by O011235813 on 2008-11-08
idk if we are allowed to bump...but i really need help, thanks

bump

---

### Post by thelenko on 2008-11-08
I also am using the geforce7900gtx and had issues as well. A few times I got the black screen, a few times just very odd resolutions/refresh rate.

This is what worked for me:

Before installing the Nvidia drivers, fully update Ubuntu.

You can do this by going to:
System->Administration->Update Manager

After all updates are installed, restart your system. Now it appears to be safe to install the nvidia drivers.

It seems the current CD version of Ubuntu has something wrong with it that is causing this. Updating fixed it for me. I'm not sure if this is an isolated problem for the 7900, or for all nvidia cards.

---

### Post by O011235813 on 2008-11-08
argh...i did that...and then i enable the video drivers, and then it keeps taking me to that black screen. I don't know why...do manufactured laptops have something against....linux or something? lol Thank for all the help, i still need to figure out what i'm doing wrong.

---

### Post by alwayshere on 2008-11-08
the standard ubuntu theme does not like nvidia change theme to another 

go to system then preferences them appearance then double click on clearlooks or any but human 

see what happpens

---

### Post by O011235813 on 2008-11-08
hmm..that didn't work...so this is what i do...step by step, am i missing something?
1. Install Ubuntu
2. Install updates
3. restart
4. change the appearance to clearlooks
5. Install drivers
6. Install compiz
7. restart
8. Get to the black screen

that's a step by step of what i'm doing ... and it still doesn't work, thanks for any and all help again :D

---

### Post by O011235813 on 2008-11-08
is there any software that can just do the entire setup for me? i just run it, and it fixes the drivers and allows me to use the desktop effects?

Thank you.

---

### Post by alwayshere on 2008-11-08
i have heard of envy alot of people seen to use it but i never have

---

### Post by alwayshere on 2008-11-08
i found this page for how to with envy [http://albertomilone.com/pmwiki/pmwiki.php?n=Main.EnvyNG-InstructionsForUbuntu](http://albertomilone.com/pmwiki/pmwiki.php?n=Main.EnvyNG-InstructionsForUbuntu)

hope it helps

---

### Post by O011235813 on 2008-11-08
hey,

i figured it out, i don't think the latest version of Ubuntu supports some of the nvidia drivers, so i installed 8.04 and that's working now :D yaya 

now to figure out how to get the 3d cube working lol thanks for all the help :D

---

