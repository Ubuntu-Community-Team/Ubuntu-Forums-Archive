---
title: "Black Screen, But Windows Show Up Ontop? Cube Shows Transparent Screens? DESKTOP GONE"
date: 2008-08-23
forum: General Help
---

### Post by YouSmeg118 on 2008-08-23
OK

Im writing this from Windows on the same laptop, so its not broken or anything.

[How it started]
I was on Synaptic Package Manager to uninstall Evolution, so i typed in evolution, marked everything to do with Evolution for removal, added a few progs which sounded cool... forget the names though. 

Anyway once i removed it i went into terminal, and it said it didnt exist, so i downloaded it. I went into my applications menu only to find my gnome-games gone, so i downloaded them...

And then i had a look in the boot/start-up option thingy above Synaptic in the System>Admin menu. I set the boot up to text instead of splash and rebooted... 

[Problem]
It all went fine until the mouse came up, on a black screen. Then a box asing me for my password pops up in the middle (this is normal), but the rest of the screen is completely blank. The Compiz splash screen shows over this. So i use the fire effect and it comes up, and it does display on the black screen. I went into the cube, only to find it was completely transaprent on all sides. I pressed print screen and went bac into the cube, and it was there, just a window on a blank side. (All the sides were blank). So i moved my mouse over to the corner to click the off  button, and i click where it would be but it dousnt work, so its not a case of the desktop being dark, its actually not there :(

Anyway i rebooted, and its there to stay. The login sound plays, then the creamy startup screen dissapears and it goes into the black.


Is this a known bug?

Please help... I hate Windows and im having to use it :'(

Thanks in advance btw

Byee


------
EDIT
I will put screenshots up in the morning
------

---

### Post by prshah on 2008-08-23
> **YouSmeg118 said:**
> 
Anyway i rebooted, and its there to stay. The login sound plays, then the creamy startup screen dissapears and it goes into the black.


Try the following:

1) Press Alt+F2 at the black screen, and if a window comes up, give the command ```
gnome-panel
```

2) Press ctrl+alt+F1, login, and give the command ```
sudo /etc/init.d/gdm restart
``` You should get two "[OK]"s'. Switch back to GUI with ctrl+alt+f7. Post back error messages, if any.

---

### Post by YouSmeg118 on 2008-08-24
I am writing this from Ubuntu :)

I did what you said, i booted up, i pressed alt+f2, nothing happened.

So i ctrl+alt+f1 and it brought up the comand line, i logged in, and typed in gnome-panel, and it tell me i didnt have it installed.

so i install it, and then run the command you gave me. It said something like it didnt exist, so scared to death i did a reboot.

When it loaded i got 6 error messages, screenshot.
[IMG]http://img34.picoodle.com/data/img34/3/8/24/f_Screenshot3m_d6feeb2.png[/IMG] 
So the desktop, and some of the top panel is black. I click Places to see if my stuff is still there, and all the links are dead. There is no link to computer or anything, heres a screenshot. 
[IMG]http://img27.picoodle.com/data/img27/3/8/24/f_Screenshot4m_df7b50d.png[/IMG]
I open opera, and its fine. Im using it now.
But my stuff is still there, as i was uploading the pics to Picoodle it shows the box with my stuff in there, shown here
[IMG]http://img34.picoodle.com/data/img34/3/8/24/f_Screenshot5m_9a70051.png[/IMG]

I alt+f2, type gnome-panel and enter, nothing happens. So i ctrl+alt+f1 and run that command again, and it still says 
```
Sudo: /ect/init.d/gdm: command not found
```

Here is a pic of the cube: It looks wierd.
[IMG]http://img34.picoodle.com/data/img34/3/8/24/f_Screenshot6m_6eea308.png[/IMG]
[CENTER]:( ](*,) :([/CENTER]

---

