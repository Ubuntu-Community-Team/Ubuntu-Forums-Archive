---
title: "add new keyboard shortcut?"
date: 2008-08-08
forum: General Help
---

### Post by pikaia on 2008-08-08
I've been to the Keyboard Shortcut menu, but the shortcut I'm looking for (xkill) is not there.  So I want to add xkill to my keyboard shortcuts for when a program crashes or hangs.  But I can't seem to figure this out.  I added xbindkeys and started configuring it, but whenever I click the "Get Key" button that crashes.  So no beans on that.  Is there an easy way to add this to my shortcuts list?  And Ctrl+Alt+ESC doesn't work.  Thats what I'm trying to add... I'm running Hardy.

Thanks.

---

### Post by yeaitsdark on 2008-08-08
Are you using Compiz by chance? If so you can go to System > Preferences > Advanced Desktop Effects Settings.

Click "General Options"

Click the "Commands" tab, and add a custom command, and a hot key there if you'd like.

---

### Post by drs305 on 2008-08-08
The compiz 'gui method' is a simple one to use. 

The traditional method to set keybindings & commands was through gconf-editor. You run "gconf-editor" and then scroll through the settings, adding a keybinding and then the run_command. But you can do the same thing in the command line. Read the entire post first.

Here is an example, which sets CTRL-P to invoke *xkill*:

```

gconftool-2 --set --type string /apps/metacity/keybinding_commands/command_12  'xkill'
gconftool-2 --set --type string /apps/metacity/global_keybindings/run_command_12 '<Control>P'

```

Note this example would still use the mouse since it creates a kill signal "X" that you use with the mouse to terminate an app - it's not a keyboard-only kill mechanism.

If you would like to do it manually, open "gconf-editor" then scroll through the listings by following the lines in the code (e.g. apps/metacity/global_keybindings).

It may be a better way to do it anyway as you can see if a keybinding has already been set for 'run_command_12' before you set/reset it.

---

### Post by pikaia on 2008-08-09
Ok.

I walked through the Compiz version and added xkill to the Command Line 0.  And under Key bindings for Line 0 I added Ctrl Alt Esc.  But that doesn't work.  I'd use the command line options given by drs, but I want to be able to learn it and not just copy and paste what you tell me.  I went to gconf-editor and my compiz addition was there but again, it doesn't work. It only lists the command 1, but has only the name, no keybindings or anything. Do I need to reset the X server?

EDIT:  I got it to work, but I had to change the keybindings.  I tried Control a instead and that worked fine.  I saw that 'switch panels' was using ctrl alt esc but even after deleting those entries it wouldn't work.  So I don't know if there are hidden entries someplace else.

---

### Post by drs305 on 2008-08-10
> **pikaia said:**
> I'd use the command line options given by drs, but I want to be able to learn it and not just copy and paste what you tell me.  I went to gconf-editor and my compiz addition was there but again, it doesn't work. It only lists the command 1, but has only the name, no keybindings or anything. Do I need to reset the X server?

EDIT:  I got it to work, but I had to change the keybindings.  I tried Control a instead and that worked fine.  I saw that 'switch panels' was using ctrl alt esc but even after deleting those entries it wouldn't work.  So I don't know if there are hidden entries someplace else.

I can't tell from the post whether you needed more guidance or not on how to set individual key bindings. If so, here is what you do. In this example, we will use *CTRL-P* to invoke the command *xkill*:

Open gconf-editor by running this in terminal:
```
gconf-editor
```

This opens the Configuration Editor window. The keybinding settings are located in apps/metacity/keybinding_commands (just like in the commands). Click on *apps* to expand it, then *metacity*, and finally *keybinding_commands*. Double-click one of the command numbers in the right pane and type the command you want run in the *Value* window (*xkill*).

Once you have set the command, return to the left window and click on *global_keybindings*.  In the right panel, select the command number you chose previously and type the *key combination* in the value window (*<Control>P*). You can read the notes below the right pane to learn about formats and options.

Gconf-editor is very powerful - there are hundreds of options which you can change via it's settings. Many, if not all, can be set via other methods but becoming familiar with gconf-editor unlocks the power to tweak many settings to the way you want ubuntu to work and feel. 

One of the biggest obstacles is knowing where the key you wish to change resides. The way to find it is to use the *Edit, Find* part of the menu or use CTRL-F. Best results are obtained by including "Search also in key names" when you are trying to find things in gconf-editor.

I can expand on how to use the commands in terminal if you need or desire it.

I'm on vacation and am not getting to the site as often as usual, but if you have any questions please post them here and you'll get a response in time.

---

### Post by ragflan on 2008-08-10
Get Ubuntu Tweak: [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/) It allows you to change the shortcuts easily. 

It also gives you the ability to change a lot of things easily. Some people say the packages (it allows you install) cannot be trusted or what not. But you can still use the application itself to change some settings without any problems.

You can change the shortcuts very easily through Ubuntu Tweak. 

Install Ubuntu Tweak (get the .deb file from the website) and then install it. 
It'll create a **menu shortcut under Applications -> System Tools**.
Open up Ubuntu Tweak.
From the **left-menu**, select Personal.
Select Shortcuts under Personal. 

You can change all the shortcuts easily here. Set xkill as what you want. I have it set as CTRL ALT Z and it works. 


You can also set some other options like Splash Screens, basic compiz effects, manage startup applications and such. Give it a try. Hope this helps.

---

