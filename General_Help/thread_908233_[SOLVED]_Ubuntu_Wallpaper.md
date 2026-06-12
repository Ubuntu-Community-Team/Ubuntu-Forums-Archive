---
title: "[SOLVED] Ubuntu Wallpaper"
date: 2008-09-02
forum: General Help
---

### Post by smirnoff76 on 2008-09-02
Hi All wonder if you can help. 

I have been using Kubuntu for the last few months but decided last weekend to give Ubuntu a go. 

I have the system set up absolutely as I want it however there is a wallpaper that appears just before the GDM theme appears and also before the main desktop wallpaper appears after the after logging in. 
The wallpaper is just the plain soft brown and I have been trying to find it to no avail, I though that it would be in etc/backgrounds but it isn't there.
Can anyone tell me where it lives as I am wanting to overwrite the file with with my desktop wallpaper so that there is consistency during the log in process. 

Thanks in advance!

---

### Post by billgoldberg on 2008-09-02
> **smirnoff76 said:**
> Hi All wonder if you can help. 

I have been using Kubuntu for the last few months but decided last weekend to give Ubuntu a go. 

I have the system set up absolutely as I want it however there is a wallpaper that appears just before the GDM theme appears and also before the main desktop wallpaper appears after the after logging in. 
The wallpaper is just the plain soft brown and I have been trying to find it to no avail, I though that it would be in etc/backgrounds but it isn't there.
Can anyone tell me where it lives as I am wanting to overwrite the file with with my desktop wallpaper so that there is consistency during the log in process. 

Thanks in advance!

In "system -> administration -> login window", in the second tab, you can set the color for that to match your desktop.

I use compiz fusion "wallpaper" plugin to draw my wallpapers and during boot my wallpaper set with nautilus (like you do it now) is shown while gnome/compiz is loading.

To use that plugin, you need to be using compiz fusion 0.7.6 ([link to installing that]("http://linuxowns.wordpress.com/2008/07/09/update-compiz-fusion/")), and disable something in gconf-editor.

> We need to change a Gconf key to stop Nautilus from managing the desktop. Launch the Run Application dialog with Alt-F2 and run gconf-editor. Navigate to apps->nautilus->preferences and unselect the show_desktop option. Your desktop icons should disappear.

Open System->Preferences->CompizConfig Settings Manager. Find and enable the Wallpaper plugin, and configure it with a wallpaper image for each of your workspaces. You can use the up and down buttons to set which workspace gets which wallpaper.

Using that you will not be able to use desktop icons.

---

### Post by smirnoff76 on 2008-09-02
Thanks for that billgoldberg, that was doing my head in last night!!

Will have a play with the Compiz this evening me thinks :) 

Thanks again!!

---

### Post by sayakb on 2008-09-02
Please mark the thread as solved (Thread tools->Mark thread as solved)

---

