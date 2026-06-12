---
title: "Changing the Ubuntu Icon next to the &quot;applications&quot; menu"
date: 2008-07-20
forum: General Help
---

### Post by earthpigg on 2008-07-20
I'd like to replace the ubuntu icon next to the applications menu.

things i have tried:

[this]("http://ubuntuforums.org/showthread.php?t=388281") and [this,]("http://linfo.wordpress.com/2006/03/24/custom-ubuntu-menu-logo/") and a bunch of other stuff from google and forum search results... i replace the file i think it is, but i still have the brown ubuntu icon sitting there when i restart.

but those both seem to be for prev versions of ubuntu... any heron-specific instructions around?

thanks in advance! :)

---

### Post by earthpigg on 2008-07-20
bump! 

been trying different stuff for the last hour, no luck

---

### Post by Execute_Method on 2008-07-20
Ok, 

The first link will only work (edit gconf to use a custom icon) if the object_type is set to "menu-object" not the standard "menu-bar" that you are talking about.


the second link kinda put you on the right track, but had the path wrong. Most themes are now using scalable icons for about everything, so what you have to do is:

1. know the name of your icon theme.
2. navigate to usr/share/icons/*theme folder*/scalable/places/
3. in there will be a file "distribution-logo.svg"
4. name the logo you want to use as the same exact name
5. paste it into the folder, replacing the old one

remember you need to be superuser to replace this file, so either "sudo" in terminal when you copy new file in, or if you like the gui use: alt-f2 gksu nautilus to open nautilus as super user

---

### Post by earthpigg on 2008-07-20
thank you for the concise info, Execute_Method.

i think im about 95% done figuring this out.

ive got all the appropriate/possible icons in the theme i am using replaced.... but, when i copy them to my desktop, they show the old ubuntu logo still. when i double click and OPEN them, they show what i want them to show - but chillin on my desktop they show what "that" file name USED to contain.... how to i reset the thumbnails or whatever?

i think it is looking at what it *thinks* my little 2kb svg file should be, and not what it is.

---

### Post by earthpigg on 2008-07-20
bump!

c'mon guys! tried restarting... :(

---

### Post by earthpigg on 2008-07-20
bump?

:(

---

### Post by rossjman1 on 2008-07-20
Is it not gconfig > apps > panel > objects > menu_bar_screen0 > custom_icon and use_custom_icon?
*edit: nevermind, tried it for myself*

---

### Post by bodhi.zazen on 2008-07-21
You are on the wrong path , lol

change the icon in :

/usr/share/icons/Human/**24x24**/places/start-here.png

(not scalable)

Then you do not need to restart, just restart the panel :

```
killall gnome-panel
```

---

### Post by rossjman1 on 2008-07-21
I'm having the same problem. I replaced the start-here.png with a custom icon, and there are also links (distributor-logo.png, gnome-main-menu.png, and novell-button.png) that point to start-here.png. Gnome-panel is still displaying the old icon. Is there like a command for updating gnome-panel's image cache (or whatever). I replaced my nm-applet icons, and I had to run a sudo dpkg-reconfigure command.
Also, I'm not using the Human theme or Human icons.

[I]Edit: When I change my icon theme from etiquette to Human, the icon does change. I would like the same for etiquette, but there is no etiquette folder in /usr/share/icons. The only thing in /usr/share/icons/default is an index.theme file. Here are the contents:
```
[Icon Theme]
Inherits=Human 
```[/I]

---

### Post by ericesque on 2008-07-21
you should find icon themes that you installed in  ~/.icons

---

### Post by earthpigg on 2008-07-21
still no luck!

ubuntu hates me :(

---

### Post by bodhi.zazen on 2008-07-21
> **earthpigg said:**
> still no luck!

ubuntu hates me :(

See my post above. If you like I can give you screen shots ::

Post your icon here as an attachment (24x24) :)

---

### Post by earthpigg on 2008-07-21
i did what your post above said :(

my icon is attached :)

---

### Post by nick_h on 2008-07-21
It works for me using your icon.

Just replace the file using the path in bodhi.zazen's post.

---

### Post by earthpigg on 2008-07-21
hrm... here, anyone want to take a look and tell me what i am missing? the file is, ofc, the same 24x24 that i uploaded in my previous post.

[http://i109.photobucket.com/albums/n59/earthpiglite/icon-1.jpg]("http://i109.photobucket.com/albums/n59/earthpiglite/icon-1.jpg")

i can switch icon sets and the icon near the applications menu changes to whatever is part of that set... put no luck getting mine in there.

---

### Post by bodhi.zazen on 2008-07-21
did you re-start the panel ?

```
killall gnome-panel
```

You have to replace the icon in the theme you are using (if it is not human) also some themes use "gnome".

---

### Post by earthpigg on 2008-07-21
> **bodhi.zazen said:**
> did you re-start the panel ?

```
killall gnome-panel
```


yup, check the red circle way off to the upper right.

any more "it could be..." type suggestions? :(

---

### Post by mc4man on 2008-07-21
@ earthpigg 
If it's still not working do as was posted, change icon in /usr/share/icons/Human/24x24/places but first change your _theme to human_, not the icons (customize) (as seen in your screenshot) 
Do the killall and the icon should change.
If you want to change the theme the icon will revert so then go into /usr/share/icons/gnome/24x24/places and do the same thing. After that you can change themes and or customize and the icon should stay

---

### Post by earthpigg on 2008-07-22
no luck, mc4man.

QUESTION:

if i go ahead and backup, and then delete ALL icon sets in /usr/share/icons... will it simply recreate gnome standard icon sets that i can then try to modify with more simplicity? or will i jack my mojo all up?

edit: i have no idea if it would matter, but this i am not on a fresh install... started with gutsy, upgraded to heron.

---

### Post by earthpigg on 2008-07-23
bump!!

---

### Post by rossjman1 on 2008-07-23
> **earthpigg said:**
> hrm... here, anyone want to take a look and tell me what i am missing? the file is, ofc, the same 24x24 that i uploaded in my previous post.

[http://i109.photobucket.com/albums/n59/earthpiglite/icon-1.jpg]("http://i109.photobucket.com/albums/n59/earthpiglite/icon-1.jpg")

i can switch icon sets and the icon near the applications menu changes to whatever is part of that set... put no luck getting mine in there.
Are you using the Human icon theme? If you are using a custom installed theme replace the start-here.png/start-here.svg with your custom icon. Icon themes are stored in ~/.icons so the start-here.png should be located in ~/.icons/theme-name/scalable/places/start-here.png or ~/.icons/theme-name/24x24/places/start-here.png. Hope that helps!

Also, after replacing the file do this command in the terminal
```
gtk-update-icon-cache ~/.icons/THEME-NAME/
```

---

### Post by ericesque on 2008-07-29
are you naming your icon

gnome-main-menu.png        ??

have you tried 

start-here.png      as well??

---

### Post by ad_267 on 2008-07-29
If start-here.png doesn't work in the 24x24 directory try putting it in scalable/start-here.png in the theme directory. That's worked for me before.

---

### Post by johnny9794 on 2008-08-12
> **bodhi.zazen said:**
> You are on the wrong path , lol

change the icon in :

/usr/share/icons/Human/**24x24**/places/start-here.png

(not scalable)

Then you do not need to restart, just restart the panel :

```
killall gnome-panel
```

Omy I have been beating my head off the wall, messing with the svg images and scalable, Thanx bodhi this work to perfect made me jump out of my seat with excitement, but I used gnome icon set for my preference, screenshot below, Thanx a Million.

Edit: by the way I am running 8.04.1

---

### Post by fencer on 2008-08-25
> **johnny9794 said:**
> Omy I have been beating my head off the wall, messing with the svg images and scalable, Thanx bodhi this work to perfect made me jump out of my seat with excitement, but I used gnome icon set for my preference, screenshot below, Thanx a Million.

Edit: by the way I am running 8.04.1[-X

almost nice job xD , but after driving myself crazy and making a lot of research without success, I found a video (in spanish) that made me realize how sucking easy this was.

You dont have to change/replace any file, or gettin as root, or going to any folder :-P

just follow the next steps

To customized the main menu icon:

1.Open up the terminal (applications>accessories>terminal)

Insert this code In the terminal (applications>accessories>terminal):

gconf-editor

The configuration editor opens, then open these folders in the left panel (apps>panel>objects)

You will see a list of objects in the pane locate the one that says (menu_object) next to object_type in the right pane.

Once this is located scroll down and locate the use custom icon entry and select it.

Scroll back up and double click the custom icon entry, this will open a new window asking for the path to the icon you wish to use. Enter the path in the value field and click OK

/home/USERNAME/path-to-the-icon/icon.png :popcorn:

here the result:

[[IMG]http://img179.imageshack.us/img179/4286/pantallazows4.th.png[/IMG]](http://img179.imageshack.us/img179/4286/pantallazows4.png)

---

### Post by rossjman1 on 2008-08-27
> **fencer said:**
> [-X

almost nice job xD , but after driving myself crazy and making a lot of research without success, I found a video (in spanish) that made me realize how sucking easy this was.

You dont have to change/replace any file, or gettin as root, or going to any folder :-P

just follow the next steps

To customized the main menu icon:

1.Open up the terminal (applications>accessories>terminal)

Insert this code In the terminal (applications>accessories>terminal):

gconf-editor

The configuration editor opens, then open these folders in the left panel (apps>panel>objects)

You will see a list of objects in the pane locate the one that says (menu_object) next to object_type in the right pane.

Once this is located scroll down and locate the use custom icon entry and select it.

Scroll back up and double click the custom icon entry, this will open a new window asking for the path to the icon you wish to use. Enter the path in the value field and click OK

/home/USERNAME/path-to-the-icon/icon.png :popcorn:

here the result:

[[IMG]http://img179.imageshack.us/img179/4286/pantallazows4.th.png[/IMG]](http://img179.imageshack.us/img179/4286/pantallazows4.png)

That doesn't work with the Applications/Places/System menu...

---

