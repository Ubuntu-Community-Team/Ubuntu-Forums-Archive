---
title: "Gnome wont load after fluxbox tinkering"
date: 2008-08-16
forum: General Help
---

### Post by dan93z28 on 2008-08-16
I hope this is the right section for this.  So i am having a little bit of an issue.  I have recently been messing around with fluxbox (which i have had installed for a while, just never really used), but now i am completely unable to load my Gnome desktop.  Things i did while in fluxbox included 
1) installed pysdm to allow access to my ntfs partition
2) edited my startup script to start kmix, set my own wallpaper, and start conky
3) installed gtk-chtheme to change the gtk theme.
4) edited the fluxbox keybindings to my likeing
5) attempted to alter my .gtkrc-2.0 file to change my icons, but it didnt work.

So after i did all this and messed around for a little bit i wanted to go back to my gnome desktop for whatever reason, and i noticed that the gtk theme was still the one i had set in fluxbox. i figured this was due to gtk-chtheme.  i use Gnome much more than fluxbox, so i just decided to uninstall it using
 
```
sudo apt-get remove gtk-chtheme
```

after that i noticed that the gtk theme could still not be changed through the appearance preferences in Gnome, so i tried restarting to see if that would help.

when i logged back in my desktop was moving very slowly and eventually froze.

desperate to get it back to the way it was it did alt+f4 to bring up the terminal and did 

```
sudo apt-get remove pysdm
```

in an attempt to revert everything back to normal. after rebooting i am completely unable to log into gnome. it shows the orange color of the default background, and a grey square up in the left hand corner, and nothing else happens.

Any ideas what i could've done to mess this up? any help would be greatly greatly appreciated.

---

### Post by Naatan on 2008-08-16
Try creating another profile (adduser <username>) and logging in to it.. if that works, then it means its your configuration files that are screwed up.

You can try removing (make a backup first) the ~/.gnome2 directory and then logging in.. 

You'd be loosing all your gnome settings though.

(to get into the terminal press the key combination: ctrl+alt+F1 - to get back to your gdm screen press: ctrl+alt+f7)

---

### Post by dan93z28 on 2008-08-16
I tried creating a new user and logging in under that name, and it worked, so im assuming i somehow messed up my configuration files. 

what do you think is the best way to go about troubleshooting this?

---

### Post by Naatan on 2008-08-16
Did you try removing the gnome2 directory?

You could try copying over the gnome2 configuration files from the newly created user one by one to see which one actually fixes your problem.. that is if you really insist on saving your gnome settings.

If I were you I would just delete your gnome2 settings and reconfigure gnome after logging in.. it shouldn't take too long

---

### Post by dan93z28 on 2008-08-16
yeah your probably right. i change all my settings on an almost daily basis anyway, so i guess it wouldnt be too big a deal.  thanks for your help.

---

### Post by RedSquirrel on 2008-08-16
> **dan93z28 said:**
> I have recently been messing around with fluxbox (which i have had installed for a while, just never really used), but now i am completely unable to load my Gnome desktop.  Things i did while in fluxbox included 
1) installed pysdm to allow access to my ntfs partition
2) edited my startup script to start kmix, set my own wallpaper, and start conky
3) installed gtk-chtheme to change the gtk theme.
4) edited the fluxbox keybindings to my likeing
5) attempted to alter my .gtkrc-2.0 file to change my icons, but it didnt work.

So after i did all this and messed around for a little bit i wanted to go back to my gnome desktop for whatever reason, and i noticed that the gtk theme was still the one i had set in fluxbox. i figured this was due to gtk-chtheme.  i use Gnome much more than fluxbox, so i just decided to uninstall it using
 
```
sudo apt-get remove gtk-chtheme
```after that i noticed that the gtk theme could still not be changed through the appearance preferences in Gnome, so i tried restarting to see if that would help.

With regard to the theming issue:

You don't have to remove gtk-chtheme. gtk-chtheme creates the file ~/.gtkrc-2.0. If you don't want the settings in that file to apply, you need to remove or rename that file.

Rename it:
```
mv ~/.gtkrc-2.0 ~/.gtkrc-2.0_backup
```OR remove it:
```
rm ~/.gtkrc-2.0
```Once ~/.gtkrc-2.0 no longer exists, the theme you set with GNOME should be shown in your GTK+ applications. (Edit: After you restart GNOME, of course. :))

---

