---
title: "&quot;places&quot; not working"
date: 2008-10-30
forum: General Help
---

### Post by helpineed on 2008-10-30
I have recently upgraded from Hardy Heron to Intrepid Ibex. Everything is working except that when I click on the 'Places' part of the menu bar, the menu drops down (like always), I click on the Home Folder part and gedit opens up complaining that /home/<my username> is a directory. This happens to all of the buttons that are supposed to bring up nautilus (which is working perfectly fine). 

Please can someone help me fix this problem - it is really annoying having to start up terminal to use the file browser.

---

### Post by scragar on 2008-10-30
open the file manager, right click any folder you like, and change it's default application back to "open folder"

EDIT: see attachment

---

### Post by helpineed on 2008-10-30
i feel so stupid :)

---

### Post by Harvs on 2008-10-30
Fantastic. I had the same problem (but it opened f-spot). This fixed it - many thanks!

---

### Post by lolwhites on 2008-10-30
I'm having a similar issue (it's made VLC the default file manager!) but when I try this solution I get the message

> Could not set as default application.

Could not set application as the default: Failed to create file '/home/xxxxxxx/.local/share/applications/mimeapps.list.77ETJU': Permission denied

---

### Post by lolwhites on 2008-10-30
Bump.
The only solution I've found by Googleing is the one scragar proposes, but it refuses to reset. I've tried running nautilus as root but no joy. Can someone please help?

---

### Post by scragar on 2008-10-30
ok, try it this way from a command line:
```
cd ~/.local/share/applications
echo "inode/directory=nautilus-folder-handler.desktop;vlc.desktop;" >> mimeapps.list

```

I would be intrested to see the permitions the folder is using though:
```
ls -l ~/.local/share/applications/ && ls -l ~/.local/share/
```
sounds like for some reason you don't have write perms(which is strange).

---

### Post by lolwhites on 2008-10-31
I tyoed in your commands and it responded *bash: mimeapps.list: Permission denied*, even when I ran it with sudo.

Permissions:
> -rwxr-xr-x 1 root root 10335 2008-10-30 16:33 bug-buddy.desktop
-rwxr-xr-x 1 root root    79 2008-10-30 16:33 defaults.list
-rwxr-xr-x 1 root root  2486 2008-10-30 16:33 firefox.desktop
-rwxr-xr-x 1 root root  2936 2008-10-30 16:33 gmenu-simple-editor.desktop
-rwxr-xr-x 1 root root  8823 2008-10-30 16:33 gnome-theme-installer.desktop
-rwxr-xr-x 1 root root  4749 2008-10-30 16:33 kde4-khangman.desktop
-rwxr-xr-x 1 root root  3365 2008-10-30 16:33 kde4-ksudoku.desktop
-rwxr-xr-x 1 root root  3004 2008-10-30 16:33 kde4-parley.desktop
-rwxr-xr-x 1 root root  4540 2008-10-30 16:33 kde4-systemsettings.desktop
-rwxr-xr-x 1 root root   871 2008-10-30 16:33 mimeapps.list
-rwxr-xr-x 1 root root   565 2008-10-30 16:33 mimeinfo.cache
-rwxr-xr-x 1 root root  8404 2008-10-30 16:33 orca.desktop
-rwxr-xr-x 1 root root   240 2008-10-30 16:33 python2.5.desktop
-rwxr-xr-x 1 root root   222 2008-10-30 16:33 seamonkey-composer.desktop
-rwxr-xr-x 1 root root   144 2008-10-30 16:33 userapp-audacity-JK04BU.desktop
-rwxr-xr-x 1 root root   146 2008-10-30 16:33 userapp-gpicview-YXI1IU.desktop
-rwxr-xr-x 1 root root   168 2008-10-30 16:33 userapp-scalc-ZB0UIU.desktop
-rwxr-xr-x 1 root root   131 2008-10-30 16:33 userapp-vlc-6WPYHU.desktop
-rwxr-xr-x 1 root root   131 2008-10-30 16:33 userapp-vlc-XCTUHU.desktop
-rwxr-xr-x 1 root root   134 2008-10-30 16:33 userapp-wine-XK3TFU.desktop
-rwxr-xr-x 1 root root   106 2008-10-30 16:33 vlc-usercreated-0.desktop
-rwxr-xr-x 1 root root   100 2008-10-30 16:33 vlc-usercreated-1.desktop
-rwxr-xr-x 1 root root    93 2008-10-30 16:33 vlc-usercreated-2.desktop
drwxr-xr-x 3 root root  4096 2008-10-30 16:24 wine
total 40
drwxr-xr-x 3 root   root   4096 2008-10-30 16:24 applications
drwxr-xr-x 4 root   root   4096 2008-10-30 16:24 audacious
drwxr-xr-x 2 root   root   4096 2008-10-30 16:24 desktop-directories
drwxr-xr-x 2 root   root   4096 2008-10-30 16:24 icons
drwxr-xr-x 3 root   root   4096 2008-10-30 16:24 Last.fm
drwxr-xr-x 7 root   root   4096 2008-10-30 16:24 mime
drwx------ 2 laurie laurie 4096 2008-10-30 16:51 totem
drwxr-xr-x 3 laurie laurie 4096 2008-10-31 07:56 tracker
drwx------ 4 laurie laurie 4096 2008-10-30 16:20 Trash
drwxr-xr-x 2 root   root   4096 2008-10-30 16:24 vlc

*Places* works fine on my wife's account on the same machine. I'm currently working around it by sticking a Nautilus launcher in the taskbar, but it's not really satisfactory.

---

### Post by scragar on 2008-10-31
huh? why does root own those files and not you?

run this command exactly as it's written:
```
sudo chown -R $USER:$USER ~/.local
```
and try to change the option again(should work via the gui now)

---

### Post by lolwhites on 2008-10-31
It worked! Many thanks.

---

### Post by abrianb on 2008-11-02
I have a similar problem, places won't work. When I right click places I do not get a GUI. Instead i get nothing. Any ideas?

---

### Post by garferi on 2009-04-26
In Ubuntu 9.04 (Gnome 2.26.2) when I right click on any folder and select properties there's no "Open with" tab. I think Gnome developers removed this, but I don't understand why...
Now you can't fix this problem and can't change your default file manager from Nautilus to anything else (e.g.: Dolphin, Thunar).
Any idea? Thank You!

---

### Post by abrianb on 2009-04-26
Try right clicking>open with other application then scroll down to open folder.
Hope that helps.

---

### Post by garferi on 2009-04-26
> **abrianb said:**
> Try right clicking>open with other application then scroll down to open folder.
Hope that helps.

Hi!

What you suggested just a temporary solution for that session. With the "Open with" tab method you can set association to folders permanently, but this function magically disappeared from the property window of folders.

---

### Post by scragar on 2009-04-27
> **garferi said:**
> Hi!

What you suggested just a temporary solution for that session. With the "Open with" tab method you can set association to folders permanently, but this function magically disappeared from the property window of folders.

```
gedit ~/.local/share/applications/mimeapps.list
```
Change the line starting:
```
inode/directory=
```
to read:
```
inode/directory=nautilus-folder-handler.desktop;
```

---

### Post by tentaro on 2009-04-27
I am having a similar problem with the exception that when I click on anything in places it appears to try to be opening and then the taskbar window just closes. I found the file manager finally but when I try to open that it's the same thing. It tries to open but then the box closes with no luck. Anyone have any ideas? 


There are only a few more little things that are holding me from switching from a Vista dual boot to just using Ubuntu. If I can get the 2 games I play alot to work in Wine and then get a working file manager/Places (both would be nice but I will live if only 1 of the 2 would work) then the rest is small stuff I can work out and I will be wipe my hard drive and load this up by itself.






Just editing this one so I can subscribe to the thread :)

---

### Post by scragar on 2009-04-28
> **tentaro said:**
> I am having a similar problem with the exception that when I click on anything in places it appears to try to be opening and then the taskbar window just closes. I found the file manager finally but when I try to open that it's the same thing. It tries to open but then the box closes with no luck. Anyone have any ideas? 


There are only a few more little things that are holding me from switching from a Vista dual boot to just using Ubuntu. If I can get the 2 games I play alot to work in Wine and then get a working file manager/Places (both would be nice but I will live if only 1 of the 2 would work) then the rest is small stuff I can work out and I will be wipe my hard drive and load this up by itself.


If nautilus is crashing you might try reinstalling it, see if that works:
```
sudo apt-get --reinstall install nautilus
```
If that doesn't work could you post the output of running nautilus from a command line?
```
nautilus
```
Please use the forums [noparse]```
 and 
```[/noparse] tags to keep it clean.

---

### Post by smalldog on 2009-05-24
> **scragar said:**
> ok, try it this way from a command line:
```
cd ~/.local/share/applications
echo "inode/directory=nautilus-folder-handler.desktop;vlc.desktop;" >> mimeapps.list

```

I would be intrested to see the permitions the folder is using though:
```
ls -l ~/.local/share/applications/ && ls -l ~/.local/share/
```
sounds like for some reason you don't have write perms(which is strange).

Dear Scragar, thanks a lot. I have same problem as lolwhites. And I follow you method, it really works for me but with some modification. I have to remove the item "vlc.desktop", otherwise gnome will using vlc to handle my request. It make me confuse is the item "vlc.desktop" - is it really necesary to let vlc to handle inode/directory request? What is the priority of multiple items that separate by semicolon on same line? I really hope someone can teach me. Anyway, thanks a lot):P

---

### Post by scragar on 2009-05-24
> **smalldog said:**
> Dear Scragar, thanks a lot. I have same problem as lolwhites. And I follow you method, it really works for me but with some modification. I have to remove the item "vlc.desktop", otherwise gnome will using vlc to handle my request. It make me confuse is the item "vlc.desktop" - is it really necesary to let vlc to handle inode/directory request? What is the priority of multiple items that separate by semicolon on same line? I really hope someone can teach me. Anyway, thanks a lot):P

That was copied from mine, I've got VLC to open folders since I tend to watch whole groups of movies one after another, I didn't actually think about it before I copy pasted it.

---

### Post by Rany . on 2009-06-02
Scragar, you made my day, thanks.

PS. Just got this problem when upgrading fom 8.04 to 9.04 today.

---

