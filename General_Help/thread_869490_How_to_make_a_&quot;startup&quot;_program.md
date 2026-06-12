---
title: "How to make a &quot;startup&quot; program"
date: 2008-07-24
forum: General Help
---

### Post by Thrasonic on 2008-07-24
Hi all.  How do I get a program to start when I log in?  I want the compiz-fusion icon to start so I don't have to start it to kick in the effects.

---

### Post by ajmorris on 2008-07-24
> **Thrasonic said:**
> Hi all. How do I get a program to start when I log in? I want the compiz-fusion icon to start so I don't have to start it to kick in the effects.
 
Hi there,
To do this, it is simply a matter of going either into the kde control panel, or by way of the option in the menus, and going to startup options (or something like that, it is obvious when you see it :)
Then just add the compiz-fusion command to a new startup item.
 
AJ

---

### Post by ramjet_1953 on 2008-07-25
In GNOME do this:

1. Navigate to [COLOR="Blue"]System>Preferences>Sessions
[/COLOR]
2. When the window opens, click on the [COLOR="Blue"]Add Button[/COLOR].

3. When the next window opens, add this:

Name: [COLOR="Red"]Compiz Fusion Icon[/COLOR]
Command: [COLOR="Red"]fusion-icon --nostart[/COLOR]
Comment: [COLOR="Red"]Start and Manage Compiz Fusion
[/COLOR]

Click [COLOR="Blue"]OK[/COLOR] and then [COLOR="Blue"]close[/COLOR].

The next time that you boot your system, the icon will be in your taskbar.

Regards,
Roger :cool:

---

### Post by ajmorris on 2008-07-25
> **ramjet_1953 said:**
> In GNOME do this:
 
1. Navigate to [COLOR=blue]System>Preferences>Sessions[/COLOR]
 
2. When the window opens, click on the [COLOR=blue]Add Button[/COLOR].
 
3. When the next window opens, add this:
 
Name: [COLOR=red]Compiz Fusion Icon[/COLOR]
Command: [COLOR=red]fusion-icon --nostart[/COLOR]
Comment: [COLOR=red]Start and Manage Compiz Fusion[/COLOR]
 
 
Click [COLOR=blue]OK[/COLOR] and then [COLOR=blue]close[/COLOR].
 
The next time that you boot your system, the icon will be in your taskbar.
 
Regards,
Roger :cool:
 
he's using kde

---

### Post by Thrasonic on 2008-07-25
Hi guys.  So I used Kcontrol with the auto-start add-in to put it in there but it's not starting.  Here are some pics of what each page of the auto-start add-in looks like for compiz-fusion.  I also included what's going on in the terminal as well.  It seems like maybe there's a permissions issue?

---

### Post by Thrasonic on 2008-07-26
Bump

---

### Post by aktiwers on 2008-07-26
I guess this is not the right way to add it, but I usually just put:
```
compiz --replace
```

in the command field.

---

### Post by Thrasonic on 2008-07-26
bump

---

### Post by Thrasonic on 2008-07-26
bump

---

### Post by aktiwers on 2008-07-26
Maybe this will help you?
[https://help.ubuntu.com/community/CompositeManager/CompizFusion#Add%20Compiz%20Startup%20(optional](https://help.ubuntu.com/community/CompositeManager/CompizFusion#Add%20Compiz%20Startup%20(optional))

I dont use KDE so I cant be at more help :(

---

