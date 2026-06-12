---
title: "Does installing themes have to be this hard?"
date: 2008-11-01
forum: General Help
---

### Post by framebuffer on 2008-11-01
Hi!

I am using 8.04 version of Ubuntu.

To be honest, I am getting really frustrated with customizing Ubuntu. To put it simply, I am unable to make any theme that I like work.

I downloaded the art manager and asked it to fetch Desktop themes. Its not showing any thumbnails and when I ask it to preview it gives: 

The image &#8220;file:///home/framebuffer/.gnome2/gnome-art/tmp/GTK2-Serenity-Shot.png&#8221; cannot be displayed, because it contains errors.

This happens for every preview.

Next, I wanted in install one of many themes available on the net but this one in particular:

[http://gnome-look.org/content/show.php/Glow+Ibex?content=87514](http://gnome-look.org/content/show.php/Glow+Ibex?content=87514)

After installing the theme from appearances > Theme The colours do change, but it looks nothing like the screenshot using widget factory.

The buttons look flatout ugly and the drop down menus and everything is nothing like the screenshot.

This happens with almost every theme. I have been using ubuntu since version 7.x and I have not been able to use any theme satisfactorily. I have no clue how people create beautiful desktops.

Next, for example, I tried installing:

[http://www.gnome-look.org/content/show.php/willibex?content=86844](http://www.gnome-look.org/content/show.php/willibex?content=86844)

It says "New themes have been successfully installed.", but never shows up in the theme manager. I can preview it from the widget factory, but I cannot select it from anywhere. It doesnt even ask me if I want to use it.

What am I missing? I checked synaptic and metacity is installed. With every theme, something or the other gets broken and it ends up looking nothing like the screenshots. :confused:

Are the screenshots gimped? Please help.

P.S: I am using everything out of the box

---

### Post by ciaramitaro on 2008-11-01
the themes in witch you posted basically only change the colors of the windows.

---

### Post by I wanted to leave on 2008-11-01
Are you also using Emerald and Compiz?

---

### Post by loomsen on 2008-11-01
```
art manager and asked it to fetch Desktop themes
```

Stop it.

Not a good program actually. It doesn't recognize mime types as it should, thats why you are not able to look at your thumbnails.

I used it once quite some time ago, downloaded a lot of wallpapers through it, just to notice that they were all claimed to be *.jpg but in fact some actually were jpg, others png tho (or other way round, can't remember.)

Much easier is to create folders in your home directory like this:

For themes: ```
 mkdir ~/.themes
```
Icons: ```
mkdir ~/.icons
```
fonts: ```
mkdir ~/.fonts
```

These folders will be parsed as well, and you should be able to easily access all your desired themes/icons/fonts instantly after unpacking them.

for example, if you want to install a theme called foo_bar,
you would extract the archive to ~/.themes/foo_bar/

Note: Some icon themes need a re-login to be read correctly.

---

### Post by framebuffer on 2008-11-01
> **bra10n said:**
> Are you also using Emerald and Compiz?

No.

---

### Post by framebuffer on 2008-11-01
> **ciaramitaro said:**
> the themes in witch you posted basically only change the colors of the windows.

In their xml files they are trying to do something to the buttons. Plus, the second one shows fine in widget factory, but doesn't allow itself to be chosen in the theme manager.

---

### Post by 3rdalbum on 2008-11-01
If everything becomes grey and ugly, then it means you don't have the correct theme engine installed.

If you get your themes from [www.gnome-look.org](www.gnome-look.org), the description usually tells you what theme engine to install to get it to work. The theme engines can usually be found in Synaptic Package Manager. Once they are installed, your themes will work alright.

The other problem you have, that it says "Theme has been correctly installed" is actually due to the modular nature of Linux theming. You can have just a window borders theme, or just a GTK (controls) theme, or just an icon theme, or just a cursor theme; or you can have the whole bundle. It looks like you've just installed a GTK theme.

If you click on the Customise button in Appearance, you will see a new window where you can fine-tune the theme. The GTK controls theme you installed will be listed under the "Controls" tab.

---

### Post by framebuffer on 2008-11-01
Thanks to 3rdalbum I was able to find the second theme, but the first one is still not working fine.

I do have the engines installed as I am not getting a grey window. The first theme changes the colors but replaces all the controls with flat ones.

---

### Post by ben2talk on 2008-11-01
> **3rdalbum said:**
> If everything becomes grey and ugly, then it means you don't have the correct theme engine installed.

If you get your themes from [www.gnome-look.org](www.gnome-look.org), the description usually tells you what theme engine to install to get it to work. The theme engines can usually be found in Synaptic Package Manager. Once they are installed, your themes will work alright.

The other problem you have, that it says "Theme has been correctly installed" is actually due to the modular nature of Linux theming. You can have just a window borders theme, or just a GTK (controls) theme, or just an icon theme, or just a cursor theme; or you can have the whole bundle. It looks like you've just installed a GTK theme.

If you click on the Customise button in Appearance, you will see a new window where you can fine-tune the theme. The GTK controls theme you installed will be listed under the "Controls" tab.

My sentiments exactly UNTIL I installed 8.10, Now I can't get themes to work in my account. Any further ideas?

---

### Post by framebuffer on 2008-11-01
This is where I have reached now.

I used the color from the first theme and controls from the second.

Yet, compare it with this:

[http://gnome-look.org/content/preview.php?preview=2&id=87514&file1=87514-1.jpg&file2=87514-2.jpg&file3=87514-3.jpg&name=Glow+Ibex](http://gnome-look.org/content/preview.php?preview=2&id=87514&file1=87514-1.jpg&file2=87514-2.jpg&file3=87514-3.jpg&name=Glow+Ibex)

When I activate this theme, it replaces all my controls with ugly ones. Curiously, the tabs are looking good though.

Any Ideas?

BTW: Unable to update to 8.1. AMD 64 Version giving some aperture more than 4GB error. Rest Assured, I do not have any aperture with more than 4 GBs.

---

### Post by ben2talk on 2008-11-08
I have a new tactic with themes. I tend to throw the tar.gz in the appearance window, and then delete it from the main window.

I then choose a combination of settings and save it with a name of my choice... My favourite examples (searchable in ubuntulooks and working beautifully in Ibex)

'A Slick Obsidian V'
Step 1 - install 'os v' theme
Step 2 - install 'slickness' and 'slickness black' and make sure that 'black-white 2 style' icons are in there.
Step 3 - the best cursor by far for me is 'obsidian' but 'silver' 3D chrome animated cursor is also really cool.
Don't be shy, SUNDAY has amazing controls, and they don't look like Macintosh, Metal-0.6 is similar (the same brushed steel as Sunday, but with a very blue theme). Leopardish has some hidden font themes - and makes my menu fonts look REALLY smooth, I wish I knew how! I'm stuck on this right now - can't change from Leopardish)

Now, select 'OS V' from window borders, and 'Sunday' controls, and an icon and save it as 'A Sunday OSV' or something. Delete the old themes, keep your own (you can delete the original, and save it again with your own name)

Don't forget to link them with your root folder to keep nice theming, unless you are worried about confusing root when you're working (I keep root unthemed now, so I won't accidentally delete everything with a Rootilus window).

That's basically it - don't fix it, just play with it and it's going to work. Learn to ignore the messages.

'

---

### Post by sirebral on 2008-11-08
Please look here for themes, icons, and some other cool customizing features.

[http://art.gnome.org/](http://art.gnome.org/)

It is actually really easy I thought.  Unzip, Drag and Drop into Appearance settings manager.

My biggest problem is using themes that utilize engines,  I am having a problem installing the required engine.  Not stressing it though.

---

