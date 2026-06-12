---
title: "Delay startup of programs"
date: 2008-08-14
forum: General Help
---

### Post by ragflan on 2008-08-14
**Situation**
Hi, I'm under Hardy Heron. I have a few applications running on start up like Avant Window Navigator, Drapes, Gnome-Do, Screenlets and such. 

I notice that from the moment I type my password to login, it takes a longer period of time for my Desktop to appear (especially the panel - up to 15-20 seconds later). If I remove some of the programs the session loads the environment faster.

**Problem 1**
I want to know if I can change something in the Sessions menu to add a delay to some programs' start up. 

For example, after I login how can I make the **program wait for 10-20 seconds before it auto-starts** giving time for the Desktop environment to be loaded up first. 

Can I implement this? 

**Problem 2**
I am not able to auto-start Firestarter GUI as it says something about not having privileges. I'm the sole user and I know the root password. How can I do this? Do I have to add a command as **sudo firestarter** instead of **firestarter**?


Thanks for the help!

---

### Post by ragflan on 2008-08-14
Anyone? I think this should be easy enough to implement for more seasoned users. I'm still looking for a how to.

---

### Post by ragflan on 2008-08-14
Okay, I found some answers. If I type sleep 5 && drapes, drapes loads up 5 seconds later. But this is not working for Session start up programs.

---

### Post by Vivaldi Gloria on 2008-08-14
> **ragflan said:**
> I am not able to auto-start Firestarter GUI as it says something about not having privileges. I'm the sole user and I know the root password. How can I do this? Do I have to add a command as **sudo firestarter** instead of **firestarter**?


Read my posts here:

[http://ubuntuforums.org/showthread.php?t=889611](http://ubuntuforums.org/showthread.php?t=889611)

You start graphical apps with gksudo, e.g.

```
gksudo nautilus
```

Do not start graphical apps with sudo. It may screw up things.

---

### Post by ragflan on 2008-08-14
> **Vivaldi Gloria said:**
> Read my posts here:

[http://ubuntuforums.org/showthread.php?t=889611](http://ubuntuforums.org/showthread.php?t=889611)

You start graphical apps with gksudo, e.g.

```
gksudo nautilus
```

Do not start graphical apps with sudo. It may screw up things.

Okay, thank you for that! Any help with delay start of programs?

---

### Post by rossjman1 on 2008-08-14
Have you tried going to the sessions window and then the Current Session tab? Highlight the program you want to delay the startup and change the order value to something higher? I'm not sure this will work, but it's worth a try.

---

### Post by ragflan on 2008-08-15
Adding **gksudo firestarter** for a Session didn't load Firestarter automatically. I'm still stuck without any solution. How do you start Firestarter automatically? The GUI I mean.

And to rossjman1, what do the numbers in the Current Session tab mean? Like 50, 40, 10? If I change to value to higher values, does that mean they will load up after the ones that have lower values?

---

### Post by Z-Funk on 2008-10-25
Regarding putting in a delay, I had a similar problem.  Instead of booting the problem directly, I chance the properties in the session manager to load a script.

just replace the direct executable file name with the path of the script with the delay you want preceeded by "sh".

---

### Post by dcstar on 2008-10-25
> **Z-Funk said:**
> Regarding putting in a delay, I had a similar problem.  Instead of booting the problem directly, I chance the properties in the session manager to load a script.

just replace the direct executable file name with the path of the script with the delay you want preceeded by "sh".

I have to delay the auto launch of Evolution (because if seems to regularly freeze up due to a file lock clash with the Evolution-notify program auto launch) with a "sleep" script, it seems to work.

---

### Post by Katinas on 2008-11-06
There is a [good blog post]("http://midnight-freak.blogspot.com/2008/09/delayed-startup-in-ubuntu.html") about it by Sogy.

In short: create a small script, which sleeps and runs, and call it instead of the original.

---

### Post by kliklik on 2009-08-05
You can also do it from the GUI without creating any additional files. For example, I have this for Pidgin:

Name: Pidgin
Command: sh -c "sleep 10 && pidgin &"

---

### Post by franciel on 2009-11-05
> **kliklik said:**
> You can also do it from the GUI without creating any additional files. For example, I have this for Pidgin:

Name: Pidgin
Command: sh -c "sleep 10 && pidgin &"

YEAAAHHHH brw... [português - brasil] Isso mesmo eu possuia o mesmo problema com o conky "Barra lateral de Monitores" quando a session terminava de carregar ele fica embaixo do background e não dava para ser visto, eu tinha que finalizar o processo e iniciar ele novamente, para que ficasse visível.
Em System>Preferences>Sessions Editei a linha para:
#sh -c "sleep 10 && /usr/bin/conky &"
E funcionou perfeitamente!!!
tks bro ...

---

### Post by franciel on 2009-11-05
I have de same problem with conky "lateral bar of monitors"
inthe System>Preferences>Sessions i have edit:
#sh -c "sleep 10 && /usr/bin/conky &"
And works!!!
=D
sorry poor english...

---

### Post by Induban on 2009-11-08
> **kliklik said:**
> You can also do it from the GUI without creating any additional files. For example, I have this for Pidgin:

Name: Pidgin
Command: sh -c "sleep 10 && pidgin &"

Thanks kliklik, I was looking all over for that solution, and yours did the trick! =D>

---

### Post by gresavage on 2009-12-26
yeah ... i come here all excited because i just solved this problem myself... anddd here i find out that it's just been solved using the same solution :(

too slow

---

### Post by Rod J on 2010-01-04
Thanks **kliklik** ... fixed it for me ... I had left out the double quotes and the & at the end and it wasn't working before.

---

### Post by lmellor on 2010-02-07
hi, could you help me by explaining how I could use this with a -m flag on the end of the command?

I am trying to get transmission to load up after 30 seconds but minimized to the notification area.

---

### Post by afrodeity on 2010-05-25
> **kliklik said:**
> You can also do it from the GUI without creating any additional files. For example, I have this for Pidgin:

Name: Pidgin
Command: sh -c "sleep 10 && pidgin &"

Sorry to be so ignorant, but where would I input this? I need pidgin to delay because its creating a conflict at startup.

---

### Post by hughyb on 2010-07-14
I have a citrix client I want to delay the start up of but following the instructions above I am tearing my hair out.  I am on Ubuntu 10.04 and have been editing the startup applications list (I presume this is the same as the "sessions" menu, which doesnt seem to exist on this version.

Below is the command that launches it and I want to delay it until the wireless connects


*/usr/lib/ICAClient/wfcmgr -icaroot /usr/lib/ICAClient -launch /home/kingsway/.ICAClient/cache/Programs/Citrix/CC4_20Anywhere_20Desktop.pnagent -drop %f*

Any help appreciated.

---

### Post by sinisterstuf on 2011-03-06
> Sorry to be so ignorant, but where would I input this? I need pidgin to delay because its creating a conflict at startup.
In startup applications, here: [http://www.techrecipes.net/application/gnome/automatically-run-program-on-startup](http://www.techrecipes.net/application/gnome/automatically-run-program-on-startup)

---

### Post by sinisterstuf on 2011-03-06
> **lmellor said:**
> hi, could you help me by explaining how I could use this with a -m flag on the end of the command?
I am trying to get transmission to load up after 30 seconds but minimized to the notification area.
in the list of **startup applications** ( [FONT=Lucida Console]System > Preferences > Startup Applications[/FONT] ) add a new entry by clicking **Add**. *Name* of the program will be Transmission, *comment* will be whatever description you want, *command* will be```
[COLOR=SeaGreen]sh -c "sleep 30 && /usr/bin/transmission **-m** &"[/COLOR]
```Check first that your transmission program is located in /usr/bin/ by typing
```
which transmission
```that'll tell you where it is. Although you can probably actually leave out the /usr/bin/ part if you want…

---

