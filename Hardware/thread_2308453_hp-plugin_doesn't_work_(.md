---
title: "hp-plugin doesn't work :("
date: 2016-01-03
forum: Hardware
---

### Post by koszyk.spamowy on 2016-01-03
I've downloaded hplip from their website. Instalation frozen when is  run from non-root user, so I've run it as root. But hp-plugin doesn't  work as root ;( If I use non-root user, it doesn't response like this: [http://www.zimagez.com/zimage/przechwycenieobrazuekranu2016-01-0223-53-08.php](http://www.zimagez.com/zimage/przechwycenieobrazuekranu2016-01-0223-53-08.php)

  
How can I use my printer (HP LJ 1102w) on this system? I have older  xubuntus on other machines and there are no problems with this printer.

---

### Post by ajgreeny on 2016-01-03
I remember having the exact same problem a few years ago with the same printer where the plugin was not available.
I tried again after a few days and all worked as expected, so it may be the same story for you; wait a few days and see if you can get the plugin when you try again.
Or have I misunderstood you; do you already have the plugin downloaded but can not install it?

However, regarding your user/root problem of running the did you install hplip exactly as shown in the hplip website by running command ```
sh hplip-3.15.9.run
``` for whatever version of hplip you have.
Did you really need to use the latest version from the website; why not use the repos version which will be recent enough for that printer?

---

### Post by koszyk.spamowy on 2016-01-03
I really need this printer for my business work starting Monday. Maybe is this possible to download plugin manually?

---

### Post by brian-mccumber on 2016-01-03
I don't know how you tried to install it but I found this maybe it will help. This suggests opening a terminal and typing in hp-setup and then following prompts. I guess this would be after the correct version of hplip is installed. I apologize if you've already tried it this way, but I couldn't know what you have already tried.

[http://hplipopensource.com/node/309](http://hplipopensource.com/node/309)

---

### Post by Bucky Ball on 2016-01-03
HPLip is right there in the repositories. Software Centre. Any reason you didn't install that one?

---

### Post by koszyk.spamowy on 2016-01-03
> **Bucky Ball said:**
> HPLip is right there in the repositories. Software Centre. Any reason you didn't install that one?

It doesn't work too ;( 


> I don't know how you tried to install it but I found this maybe it will help.


i do it:   [https://youtu.be/_Y_Ire4SMvc](https://youtu.be/_Y_Ire4SMvc)



(BTW: Where is in this forum button: NEW POSTS?)

---

### Post by Bucky Ball on 2016-01-03
Top left> Quick Links> New Posts.

---

### Post by oldfred on 2016-01-03
New posts is big red button in upper left corner. But you have to choose which forum to post in first. No button on home page as that does not know where you want thread to be. 
see thumbnail in post #3
 [http://ubuntuforums.org/showthread.php?t=2054969](http://ubuntuforums.org/showthread.php?t=2054969)

I download hplip from HP site, and run it as it says. But it normally asks for your sudo password as part of the install. I do find new installs create a new printer unless I say otherwise and old printer is left as default and does not work. I have to use HP Device Manager to make sure settings are correct.

---

### Post by koszyk.spamowy on 2016-01-03
> **oldfred said:**
> 
I download hplip from HP site, and run it as it says. But it normally asks for your sudo password as part of the install. I do find new installs create a new printer unless I say otherwise and old printer is left as default and does not work. I have to use HP Device Manager to make sure settings are correct.

So what can I do now? I have problem and there is no information on google :( All troubleshootings leads to this informaction. RUN HP-SETUP. But it doesn't work ;(

---

### Post by brian-mccumber on 2016-01-03
Could you try to run hp-setup from the terminal by typing just hp-setup and post any errors you are seeing? You can also try to run hp-plugin from the terminal also.

---

### Post by koszyk.spamowy on 2016-01-03
> **brian-mccumber said:**
> Could you try to run hp-setup from the terminal by typing just hp-setup and post any errors you are seeing? You can also try to run hp-plugin from the terminal also.


I've send screenshot next YT film... What else I can send? THERE IS NO ERROR. Program is waiting and waiting and waiting. Even in debug level.

---

### Post by brian-mccumber on 2016-01-03
Did you run it by using gksudo hp-setup from the terminal? I found this article here and it says there is a bug that if you use just sudo hp-setup it will not download the plugin. 

> 

[LIST]
[*=left]gksudo hp-setup
[/LIST]
[COLOR=#333333][FONT=Ubuntu]It must be run using gksudo otherwise the downloaded pluggin will fail.

[/FONT][/COLOR]https://help.ubuntu.com/community/HPPrinterInstallation


For your future reference any app that utilizes a gui should be run from the terminal using gksudo not just sudo. And you may have to install gksudo the first time you try to use it.

---

### Post by Bucky Ball on 2016-01-03
> **brian-mccumber said:**
> For your future reference any app that utilizes a gui should be run from the terminal using gksudo not just sudo. And you may have to install gksudo the first time you try to use it.

+1.

---

### Post by dave205 on 2016-01-03
HP printers....ugh.  :)   I had an issue recently and found the hplip to have issues.  Here is where I outlined "the fix". 
[http://ubuntuforums.org/showthread.php?t=2302231](http://ubuntuforums.org/showthread.php?t=2302231)

hope that helps.

---

### Post by koszyk.spamowy on 2016-01-04
> **dave205 said:**
> HP printers....ugh.  :)   I had an issue recently and found the hplip to have issues.  Here is where I outlined "the fix". 
[http://ubuntuforums.org/showthread.php?t=2302231](http://ubuntuforums.org/showthread.php?t=2302231)

hope that helps.


No :( I have got python-dev installed. 

> **brian-mccumber said:**
> Did you run it by using gksudo hp-setup from the terminal? 

No. hp-setup and hp-plugin should be run as non-root! On other machines it works without sudo and other. It is not this problem...

---

