---
title: "[SOLVED] Can't change Gnome themes"
date: 2008-11-30
forum: General Help
---

### Post by opus1 on 2008-11-30
I just removed Intrepid and installed Hardy.  I have my /home on another partition, so I just mapped to that and all my settings came back *except* the theme.  Instead of the human theme, I have something that looks like the default gnome theme (gray with a blue title bar, highlights in blue, really blocky buttons).  

Everytime I go to System > Preferences > Appearance and select any of the human themes, all the open windows change to the way I want, but then any window I open after that is back to the default gnome appearance.  The title bar and highlight colors often will change to what they are supposed to be, but the buttons and menus are all the ugly grey blocky style.

This looks identical to this post: [http://ubuntuforums.org/showthread.php?t=844888&highlight=can%27t+change+theme]("http://ubuntuforums.org/showthread.php?t=844888&highlight=can%27t+change+theme") His screenshots are exactly what I'm seeing.  Except the solution doesn't apply to me because I don't have the dark looks theme.  I tried changing the human theme based on his fix, but that was a mess. 

Other things I've tried:  
I've renamed the .gconf file and logged back in
I went through Synaptic and reinstalled the following items:

gtk2-engines-murrine
gtk2-engines-pixbuf
gtk2-engines-ubuntulooks
human-icon-theme
human-theme
ubuntu-gdm-themes
gnome-themes

I've tried other themes besides human.
Also tried: gtk-window-decorator --replace, metacity --replace and compiz --replace

Nothing works!!!!  Help!!!](*,)

What other information can I provide to help troubleshoot?  I haven't found a solution yet on the forums (maybe I'm not using the right keywords).  The closest I found was the link I posted above.

Any help would be fantastic.  I don't want to have to completely reinstall just to fix the dumb colors.

---

### Post by seren6ipity on 2008-11-30
Can you please restart without saving current session and post an image of the issue e.g. how it looks after applying human-theme.

---

### Post by opus1 on 2008-11-30
Sure, give me a minute here.

Just to help define the issue a little more.  I've noticed that menus related to Ubuntu (that is, the panel menus and menus in the appearances window) have the correct appearance (brownish background) while "external" apps (firefox, calculator, etc.) have the default blue background to the menus as well as the blocky appearance to the buttons.

I thought there might be some permission issue so I issued a 

```
$ find /home/bob/ -user root
``` 

But only one root owned file was found, and it's related to passwords.

---

### Post by opus1 on 2008-11-30
Here are the screen captures.  I tried to show what I was talking about with the two menu colors...

---

### Post by seren6ipity on 2008-11-30
Please go to your window manager and check if proper style is selected. Since am on xubuntu. I can not advise further on ubuntu options.

---

### Post by opus1 on 2008-11-30
Could someone direct me how to get to the window manager?  I've looked through the menu items and haven't found anything that matches that description...

---

### Post by eternalnewbee on 2008-12-01
How about disabling Visual Effects?
Go to: **Main Menu > System > Preferences > Appearance**, and click **None**.

---

### Post by Forlong on 2008-12-01
Try running:
```
gnome-settings-daemon
```

---

### Post by Ivo Moelans on 2008-12-01
Could you give the following information:
When you apply a theme, e.g. Human, and then in *Appearance Preferences* click on the *Customize...* button under the tab *Controls* Human should be selected and also under the tab *Window Border* Human should be selected.
Is this the case?

---

### Post by opus1 on 2008-12-07
Thanks everyone for the replies.  During the busy work week I typically don't spend much time at home, so I didn't see your replies.

I started messing with it yesterday morning (before checking here) and managed to fix it.

eternalnewbee:  I did try your suggestion yesterday and it had no effect.

Ivo Moelans: Yes, "human" was selected under the *Controls* and *Window Border* tabs.  Selecting these tabs would cause the controls in the "appearance" window to reset themselves to "human", but when I closed the window and opened it again, they would revert back to the gtk look I described above.

My fix is a strange one, though:  I selected a completely different theme ("Clearlooks") and then changed each element of the theme, one-by-one, until it matched "Human".

To be specific (for anyone else who might need this fix):  
[LIST=1]
[*]I went to **System** > **Preferences** > **Appearance**.
[*]On the "theme" tab I chose "Clearlooks".
[*]I clicked the "Customize" button at the bottom.
[*]On the "controls", "Icons" and "Window Border" tabs, I chose "human".
[*]On the "Colors" tab, I chose colors that matched the "Human" theme.
[/LIST]

This made all applications menus and buttons behave properly. 

Interestingly, I went back and selected the "human" theme and it reverted back to the annoying behavior I noted in my first post.  All three "Human" themes appear to be borked, but the other themes appear to work correctly (I may have stated otherwise above, but if I did, I was wrong).

Forlong : Do you want me to try your suggestions, or should I mark this as 'solved'?

Thank you everyone!

---

### Post by vernonrj on 2009-01-26
Hey Forlong, I was having a similar problem to opus. I tried typing gnome-settings-daemon into the terminal, and it fixed my problem. I was wondering what the problem might be and how I could prevent it in the future?

---

### Post by carlossl on 2010-09-07
Hi, I know it's been two years since this thread was opened, but I installed Karmic one week ago because its kernel is the only one that works with my laptop.

I'm having the same issues with my GTK engines, did someone find a solution to this problem? I opened [another thread here]("http://ubuntuforums.org/showthread.php?t=1570064") explaining my situation, hoping that someone can help me in the Gnome section.

---

### Post by Orion42 on 2011-03-09
This is my 1st time trying to help some one else.  When you go to the Appearance preferences did you see any errors/warnings pertaining to Ubuntulooks.  The Human-theme is the updated preferred engine but many older themes still point to wanting Ubuntulooks.  I mess around with themes and icons regularly and see this issue occasionally.
I just took a stab in the dark at this; if you need to know how to use Ubuntulooks over Human let me know.

---

