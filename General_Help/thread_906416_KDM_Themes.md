---
title: "KDM Themes"
date: 2008-08-31
forum: General Help
---

### Post by Mhurst1 on 2008-08-31
How do you change the KDM themes in Kubuntu 8.04.1?

---

### Post by Sycron on 2008-08-31
System-->Administration-->Login window-->Local

---

### Post by Mhurst1 on 2008-08-31
Thats for Ubuntu not Kubuntu.

---

### Post by Sycron on 2008-08-31
Sorry.

---

### Post by qpieus on 2008-08-31
System Settings > Appearance > Icons  (for icon themes)
System Settings > Appearance > Window Decorations and 
System Settings > Appearance > Style also have stuff you can change, like widgets and decorations.

I mostly change icon themes, which I get from kde-look.org.

You install a new icon theme from the System Settings > Appearance > Icons window. Near the bottom is an "Install new theme" button. You don't even need to untar the theme you download, just browse to the tar.gz file and selectit. As far as installing overall themes, I'm not as sure on how to do that (like I said, I've only messed around with icon themes). I did not see any other "Install new theme" buttons except on the Icons page.

---

### Post by Zorael on 2008-08-31
Changing KDM themes is tricky. As soon as you pick a theme or change the login background, it will stop importing kubuntu default settings for the greeter.

I'll copy/paste some excerpts from some earlier posts of mine.
> 

On the topic of configuring kdm, it works a bit weirdish. [FONT="Courier New"]/etc/kde3/kdm/kdmrc[/FONT] is the configuration file, with options concerning the whole X session. Obviously, this includes the login screen, so there's a proper Greeting section in there, with tags like the USETHEME= and THEME= ones we talked about earlier. HOWEVER, Kubuntu doesn't come with its "own" Kubuntu kdmrc, but rather with a file that overrides kdmrc settings, which would be the [FONT="Courier New"]/etc/default/kdm.d/20_kubuntu_default_settings[/FONT] file. If you use an application to change login manager settings, there's a chance that it modifies the kdmrc file, over which [FONT="Courier New"]20_kubuntu_default_settings[/FONT] take precedence. This, at least, is the case with the built-in Login Manager app under System Settings -> Advanced.

By design decision, upon start of KDM it reads [FONT="Courier New"]/etc/kde3/kdm/kdmrc[/FONT] and [FONT="Courier New"]backgroundrc[/FONT] (in the same folder). Then it considers their content to see if they're *unmodified* (kdmrc's THEME set to *@@@ToBeReplacedByDesktopBase@@@* and backgroundrc's WALLPAPER set to *default_blue.jpg*). If they are, it proceeds to import files from [FONT="Courier New"]/etc/default/kdm.d/[/FONT] and use their settings to override those found in the real kdmrc and backgroundrc files. If you use the Login Manager and change the background, it won't import the Kubuntu default settings and you lose your themed login (background no longer default_blue.jpg). Likewise, if you use another app that can manually set a theme, upon doing so, it won't import the Kubuntu defaults, and you lose your Kubuntu background (theme no longer @@@ToBeReplacedByDesktopBase@@@).

This isn't a big deal if you have apps with which to take care of it. Using only the default ones, though, there is no graphical interface to pick themes; the Login Manager under System Settings can change background and modify greeter text strings ("Welcome to <servername>, plrx login ktx"), along with some other non-theme related settings.

Better put, it isn't a big deal if you know what's *happening*. I just stumbled upon the Login Manager when exploring KDE's configurability and thought "..the hell, that's not the login background I have, *ker-change*". I went as far to reinstall to get it back.

I don't know how the KDM Theme Manager works. If it changes kdmrc and backgroundrc manually, be prepared for some unexpected behavior.

> While we're talking KDM and login appearance, this is how to change the pre-logged in backgrounds. Since I only have one user on this machine I changed them to the same pic. Made things smooth, no flashing backgrounds between login steps. Make backups of mentioned files first.

[list=1][*]Save wallpaper somewhere public. The default location is in [FONT="Courier New"]/usr/share/wallpapers/[/FONT].
[*]Modify the WALLPAPER= line in [FONT="Courier New"]/etc/default/kdm.d/20_kubuntu_default_settings[/FONT] to point to it. For instance, my line;
```
WALLPAPER="**/usr/share/wallpapers/Emotion/1280x1024.jpg**"
```
To my knowledge, it should scale it to fit the screen, so picking a low resolution version may be inadvisable.
[*]Modify your theme .xml file in [FONT="Courier New"]/usr/share/apps/kdm/themes/*<theme name>*[/FONT] to also point toward it. The line you want to alter is this one:
```
        <item type="pixmap" >
                <normal file="**/usr/share/wallpapers/Emotion/1280x1024.jpg**" />
                <pos width="100%" x="0" y="0" height="100%" />
```
[*]Change your own user's wallpaper to the same pic, through whatever GUI interface you're used to.
[*]Either:
[list][*]Reboot, or...
[*]...log out, Ctrl+Alt+F1 to get to textual interface, log in, restart kdm from there.
```
$ sudo /etc/init.d/kdm force-reload
```[/list]
[*]All done, rejoice.[/list]

---

