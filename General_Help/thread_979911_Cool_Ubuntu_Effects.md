---
title: "Cool Ubuntu Effects"
date: 2008-11-12
forum: General Help
---

### Post by Ciwan on 2008-11-12
Hi Guys

I'm a n00b to Ubuntu. So go easy on me Please.

OK I have seen screenshots of the Desktops of people who use Ubuntu and their TaskBar (at the top) is "see-through" also I've watched a video on youtube and this guy who has Ubuntu has so many cool effects that he can do, something to do with compiz.

[http://uk.youtube.com/watch?v=E4Fbk52Mk1w](http://uk.youtube.com/watch?v=E4Fbk52Mk1w)

I would greatly appreciate it if someone can tell me how I can get them affects !

Thank You.

---

### Post by arkster00 on 2008-11-12
Hi. Please read the Great Desktop Effects FAQ thread that is stickied in this forum.

---

### Post by Ciwan on 2008-11-12
Thanks Arkster

I have enabled the Cube effect, but I don't know how to see it !! what do I press ??

Also there is nothing in the FAQ about "see-through" task bar !!

---

### Post by Seanuntu on 2008-11-12
The default key-bindings for the cube are:

ctrl+alt+left (rotate cube left)
ctrl+alt+right (rotate cube right)
ctrl+alt+mouse button 1 (move cube around with the mouse)

To make a task-bar transparent:
right click on the bar and click "Properties", on the "Background" tab choose "Solid Color", pick a color, and then adjust the slider for the level of transparency you like...

---

### Post by Ciwan on 2008-11-12
Hi Seanuntu

Thanks for the help bro, I've got the taskbar sorted, but in the screenshot that I saw, the title bar for the windows were also see-through (transparent)

How do I get them to be transparet ?

Thanks

---

### Post by SonicSteve on 2008-11-12
Different themes have transparent window borders. If you go to Gnome-look.org and look through the GTK2.x themes you'll find some have transparency. To install;
First download the theme file usually a tar.gz file
Then
1 click system
2. click preference
3. click appearance
4. Click install on the lower right corner and browse to the location you saved the theme.
5. That's it. 

Then you can customize it and tweek it to preference. Not all themes fully support customizations.

---

### Post by giantoz on 2008-11-12
theres probably another way to do this, but if you install ubuntu-tweak, and go to desktop-window settings; you can make titlebars transparent from there. you can also make your menus transparent this way (under compiz settings in ubuntu-tweak)

---

### Post by Ciwan on 2008-11-12
hmm all that sounds too complex, I thought compwiz was gonna give me the ability to have transparent title-bars.

I hate installing too much software. thus I have changed my mind, and I'll just live with the title-bars not being transparent :)

Thanks for your help guys :)

---

### Post by mrboojive on 2008-11-12
You can change the transparency of window title bars using the gconf-editor. See this thread:
[http://ubuntuforums.org/showthread.php?t=751002](http://ubuntuforums.org/showthread.php?t=751002)

---

### Post by kiran88pnjr on 2008-11-12
Hi,

Please install Emerald Theme Manager using Synaptic & get some emerald themes from [http://www.gnome-look.org/index.php?xcontentmode=103](http://www.gnome-look.org/index.php?xcontentmode=103). You will get every type of themes u want.

SORRY FOR MY POOR ENGLISH !\\:D/

---

### Post by steveneddy on 2008-11-12
WOW! In Compiz years that is a very old video.

OK - there is a link in my sig called Compiz that should be a first read about Compiz.

The other links are good links as well.

Here are some of my transparency tricks with Compiz.

> ## make gnome bar true transparent

if you are using compiz (desktop effects), you can add true transparency.
go to System->Prefs->Advanced desktop effects settings
Click on General opts.->Opacity settings, and add the following entry at top of the list:
Opacity windows: type=dock
Opacity windows values: 80 (adjust this to your like)

if you dont have the advanced desktop settings util, just install it:
sudo apt-get install compizconfig-settings-manager

this will make entire panel transparent

> ## Also make panel and menus transparent

Open CCSM

Go to General Settings

Go to Tab - Opacity Settings

Settings as follows:

dock 67
Menu 90
DropdownMenu 92
popupmenu 93

Link: [http://wiki.compiz-fusion.org/WindowMatching](http://wiki.compiz-fusion.org/WindowMatching)

Good Luck.

---

### Post by Ciwan on 2008-11-14
Hi Steve

> go to System->Prefs->Advanced desktop effects settings

There is no Advanced on my Ubuntu when I go to System > Prefs > ???

What is wrong on my system ? sorry I'm a total n00b :(

---

### Post by Ciwan on 2008-11-14
Hi Steve

> go to System->Prefs->Advanced desktop effects settings

There is no Advanced on my Ubuntu when I go to System > Prefs > ???

What is wrong on my system ? sorry I'm a total n00b :(

---

### Post by laurielegit on 2008-11-14
I think he means CompizConfig Settings Manager. I also have a problem as when I go to General Setting there is no option for Opacity Settings.

---

### Post by SonicSteve on 2008-11-14
Hi Guys,
Do this;
Open the terminal, applications>accessories>terminal
Type
sudo apt-get install compizconfig-settings-manager 
Or 
You can also search for it using Synaptic package manager under System>Administration. It should add an extra python package for you and install in short order.
This will install the advanced effects manager. You'll see it under preferences when it's done. It's a bit tricky in places but it do what you're looking for.

Edit;
I just tested this out, I really like the Dropdownmenu, and popupmenu options, it effects the apps, places, and system menu, and the right click menus.

---

### Post by laurielegit on 2008-11-14
> **SonicSteve said:**
> Hi Guys,
Do this;
Open the terminal, applications>accessories>terminal
Type
sudo apt-get install compizconfig-settings-manager 
Or 
You can also search for it using Synaptic package manager under System>Administration. It should add an extra python package for you and install in short order.
This will install the advanced effects manager. You'll see it under preferences when it's done. It's a bit tricky in places but it do what you're looking for.

I already have that pacage installed yet I don't have advanced settings. I think the advanced settings manager that you are looking for is just another name for CompizConfig Settings Manager

---

### Post by SonicSteve on 2008-11-14
> **laurielegit said:**
> I already have that pacage installed yet I don't have advanced settings. I think the advanced settings manager that you are looking for is just another name for CompizConfig Settings Manager

Please don't take this the wrong way.

Are you using the program? IE. actually clicking on system>preferences>advanced desktop effects settings. This should open up the config program which will allow you to tweak as instructed.

EDIT, 
Yes indeed the "advanced settings" and Compiz settings manager" are the same. Though I don't recall ever seeing it called compiz settings manager in the system menu. For some time now it's been called advanced desktop effects settings. A.D.E.S. is the menu name for the package compizconfig-settings-manager.

---

### Post by laurielegit on 2008-11-14
> **SonicSteve said:**
> Please don't take this the wrong way.

Are you using the program? IE. actually clicking on system>preferences>advanced desktop effects settings. This should open up the config program which will allow you to tweak as instructed.

EDIT, 
Yes indeed the "advanced settings" and Compiz settings manager" are the same. Though I don't recall ever seeing it called compiz settings manager in the system menu. For some time now it's been called advanced desktop effects settings. A.D.E.S. is the menu name for the package compizconfig-settings-manager.

ok, Im glad that's sorted. Now I would realy love truly transparent toolbars but I still don't have an opacity tab in the settings that come under general.

---

### Post by loomsen on 2008-11-14
It deferes a little bit from version to version where some settings can be found. In git opacify has an own button, but I think I remember in 0.7.4 or so it was the last tab under general options.

Or run this and edit the file manually, if you have it
```

ubuntu@ubuntu:~$ locate compiz | grep opacify
/usr/lib/compiz/libopacify.a
/usr/lib/compiz/libopacify.la
/usr/lib/compiz/libopacify.so
[color=red]/usr/share/compiz/opacify.xml[/COLOR]
/usr/share/gconf/schemas/compiz-opacify.schemas
ubuntu@ubuntu:~$ 

```

There maybe more files, maybe you don't find any... As I said 0.7.9 here. Telling your version could and prlly will be helpful here.

*edit*

You could look at ~/.config/compiz as well. If you have it, search the file for opacify...

---

### Post by laurielegit on 2008-11-14
> **loomsen said:**
> It deferes a little bit from version to version where some settings can be found. In git opacify has an own button, but I think I remember in 0.7.4 or so it was the last tab under general options.

Or run this and edit the file manually, if you have it
```

ubuntu@ubuntu:~$ locate compiz | grep opacify
/usr/lib/compiz/libopacify.a
/usr/lib/compiz/libopacify.la
/usr/lib/compiz/libopacify.so
[color=red]/usr/share/compiz/opacify.xml[/COLOR]
/usr/share/gconf/schemas/compiz-opacify.schemas
ubuntu@ubuntu:~$ 

```

There maybe more files, maybe you don't find any... As I said 0.7.9 here. Telling your version could and prlly will be helpful here.

*edit*

You could look at ~/.config/compiz as well. If you have it, search the file for opacify...

I just tried that but I think we have some confusion. I do have a Opacity option in my ccsm but it is not the same opacity as you are talking about. I am running 0.7.8 and my opacity option just makes the window I am hovering over become more opaque (and it dosn't work very well anyway). I want to be able to change the opacity of my Gnome tool bar which is very different from what the opacity option lets me do. Can someone please help?

EDIT: when i say i want my toolbars transparent i mean Truly transparent (including menu and all applets) not just the fake/untrue transparency i get from the properties menu of the toolbar.

---

### Post by SonicSteve on 2008-11-14
> **laurielegit said:**
> ok, Im glad that's sorted. Now I would realy love truly transparent toolbars but I still don't have an opacity tab in the settings that come under general.

When I open the Settings manager and click the general options button I have 7 tabs. Opacity settings is the last tab on the right for me. If it is there you will have to click the "new" button where it says window opacities and add the corresponding information for toolbars. Which toolbars are you referring to?

---

### Post by laurielegit on 2008-11-14
> **SonicSteve said:**
> When I open the Settings manager and click the general options button I have 7 tabs. Opacity settings is the last tab on the right for me. If it is there you will have to click the "new" button where it says window opacities and add the corresponding information for toolbars. Which toolbars are you referring to?

Ok...!!!! Under General Options in ccsm I have 6 Tabs. Opacity is not one of them. I have Opacity option once I come out of General Options (I think it's an plugin). I want my Toolbars (Gnome-Toolbar 2.24.1) to be truly transparent (I.E. Menus and things like clocks must also be transparent). I know how to do this if I can find the Opacity Tab. *That* is my problem. I am running a fully updated 8.10 (upgraded from 8.4; not a clean install) with good enough hardware to do anything reasonable. So were on earth is this Opacity Tab?

---

### Post by SonicSteve on 2008-11-14
I'm still running with 8.04 and my compiz manager is version 0.7.4 this must be why our settings manager has a different layout. There must a spot somewhere for you to add custom opacity commands in there. 

Does anyone have 0.7.8 that can help? I don't know if that's a standard version, I have a fully updated 8.04, and it seems that Intrepid 8.10 may be using 0.7.9

Perhaps you could post a screenshot of the opacity tab, or any tab you think may help us.

---

### Post by loomsen on 2008-11-14
No, Intrepid ships with 0.78...

---

### Post by RWright on 2008-11-16
I just right clicked on the panel and then went to the backgrounds tab and played with the slider until I got the transparency I wanted.

Hope that helps.

---

### Post by police512 on 2008-11-16
Hi, i have been using Kubuntu and Ubuntu for years, and i have never had a problem with it not booting!. But since you made this new version 8.10 i have the greatest problems with it. None of my computers besides my laptop will boot it, it always gets stuck on that loading bar. i managed to get it to boot on my laptop but when i put in a usb memory stick or anything else it freezes, i dont no y but all my computers are i386 which i have always used. i dont no y it wont boot on any computers besides my laptop but please can u help ? cuz this is annoying me

---

### Post by loomsen on 2008-11-16
Probably acpi related.

Try booting with acpi=off, if that doesn't do it try disabling apic and lapic.

At the start screen of a live cd hit F6 and then mark these 3 options, and see if it works.

Btw, you may want to change "that bar" into actually some useful output by removing splash from the boot command as well... Then you'll probably get to read what works and where he refuses further boot.

*edit*

Depending on how new your PCs are, and which vendor, you could as well suffer from some ugly Win-Recovery partition written to your ACPI.
But, if your PCs are really that new, they most likely would have 2 processors at least, so you wouldn't want to go with 32bit installs anyway...

---

### Post by mgmiller on 2008-11-17
It used to be in the general section in 8.04.  In 8.10 they split it out to a new section called "Opacity, Brightness & Saturation"

You need to click to turn it on and in the settings area,  look in the "Opacity" tab.  You will see a "Window Specific Settings" section with nothing in it.  You need to click the "New" button and put in the name you want.  Then move the slider to change the degree of transparency.  Some of the useful names for things are
Menu
DropdownMenu
dock
PopupMenu

I have most of these set to a value of 84, but your mileage will vary.

Notice the names are case sensitive, so use the capitals as I have shown above.  There is a long list of the available names somewhere, but these are the most common.

---

### Post by SonicSteve on 2008-11-18
> **police512 said:**
> Hi, i have been using Kubuntu and Ubuntu for years, and i have never had a problem with it not booting!. But since you made this new version 8.10 i have the greatest problems with it. None of my computers besides my laptop will boot it, it always gets stuck on that loading bar. i managed to get it to boot on my laptop but when i put in a usb memory stick or anything else it freezes, i dont no y but all my computers are i386 which i have always used. i dont no y it wont boot on any computers besides my laptop but please can u help ? cuz this is annoying me

Hi there,
if you really want help on this you need to create a new thread. The topic of this thread is Desktop Effects and enabling transparency effects. Even if people help you in this thread it will be no help to anyone else with the same problem. Nor will it get the kind of attention you're looking for.  A new thread with the topic stated clearly from the beginning is the best way to get help.

---

### Post by Nixie Pixel on 2008-11-20
Hi!

I had trouble finding the Opacity settings as well...it appears that their location has changed to be under Accessories in CCSM.

I am now able to adjust the opacity of various types of drop-down menus and such, but what I am really looking to do is to adjust the opacity of things like the title bar, scroll bar, and bottom status bar of applications such as Firefox without changing the opacity of the background (or foreground), or being able to adjust them separately.

I want my Firefox window to have transparent borders without killing the readability of the content of the window itself.  Is such a thing possible?

The [WindowMatching]("http://wiki.compiz-fusion.org/WindowMatching") page has a list of all sorts of different menus, but it doesn't seem to address this.

I appreciate any and all assistance!

Thanks,

~Nix

---

### Post by mgmiller on 2008-11-20
> I want my Firefox window to have transparent borders without killing the readability of the content of the window itself. Is such a thing possible?

Fire up gconf editor:
```
gconf-editor
```

And navigate to  apps > gwd  by clicking on the triangle to the left of apps in the left pane to open up its sub keys.   Then scroll down to gwd and left click it once to hilite it.

On the right side, the 2 lines you are interested in are 
metacity_theme_active_opacity
and 
metacity_theme_opacity  

The first affects the opacity of the active window border, the second, the opacity of the backgrounded window borders.

I have mine set to 1 and 0.75, where 1 is solid (no opacity) and 0.75 which is 75% opaque (or 25% transparent).

You can set these values to whatever you want by double clicking the entry and changing the number in the "value" field.

The changes take place immediately.  

You should set a bookmark in the gconf editor by clicking on Bookmarks > Add Bookmark  at the top of the window so you can easily get back to that spot again.

---

### Post by Nixie Pixel on 2008-11-20
Great, thank you!

Unfortunately, I still have two issues.  The first is that these settings appear to affect the title bar of the application, but not the scroll bar or the bottom status bar.

The second is that the window titles behind my current application are blurring with my focused application.

Do you know if I can adjust these somehow?

Thank you again!

---

### Post by amauk on 2008-11-20
to change the transparency of the panels, right click on them and select properties
in the background tab, select solid colour, and move the slider to transparent

---

### Post by mrboojive on 2008-11-20
I'm pretty sure there's no way to change the color of the scroll bar or the bottom status bar. They're all parts of the same window and I don't think Compiz has any way of controlling parts of windows.

---

### Post by mgmiller on 2008-11-20
> The second is that the window titles behind my current application are blurring with my focused application.

This is the annoying part about transparent title bars.  You need to try different combinations of active and inactive transparencies to find one that works.  Maybe only a little transparent, like 0.85 for the active bar and very transparent like 0.20 for the inactive one....

Some of the beryl window decorations allow for better control of the transparency of title bars and window frames, but that adds more complexity and controls.  It has also been abandoned, I think, in favor of the compiz-fusion you are now using.

If you want to try beryl, try searching the forums for info on how to install/enable/configure it.

---

### Post by Nixie Pixel on 2008-11-21
Ok, thank you for helping!

If there is no way to change the transparency of the scroll bar and/or bottom status bar, is there a way to change the transparency of a window but keep the text within the window opaque?

I will also take a look at Beryl to see if it can do what I want it to do.

Thanks again!

---

### Post by mrboojive on 2008-11-21
It depends on the application. Some specific apps (like the Gnome terminal and the Gnome panel) have their own settings that allow you to make just the background of the app transparent.
I don't think there's any way to do that for other applications right now, but something like that might be in a future version of Compiz. Here's a thread at the Compiz forums where they're talking about a feature sort of like that: [http://forum.compiz-fusion.org/showthread.php?t=7753](http://forum.compiz-fusion.org/showthread.php?t=7753)). It looks like Beryl might have had a plugin to do that.

---

### Post by mgmiller on 2008-11-22
In compiz-fuson, if you want to make the entire window, including the scroll bar and bottom status bar, transparent, hold down the alt key and move the scroll wheel on your mouse.  I find it does not enhance readability (quite the opposite) but you can quickly look at whats behind the current window and then just roll the scroll wheel back again to make it solid once more. 

 I suppose if you wanted it just a little transparent, just move the mouse wheel 3 or 4 clicks.

---

### Post by joffeloff on 2008-11-27
Opacity settings. WHERE?!?!?!

**[This guide]("http://sudosys.be/?q=fully_transparent_ubuntu")** mentions the tab. **[Doesn't exist]("http://www.isarapix.org/pix22/1227828512.png")** in mine. Yes, I've read the thread - there's no such thing as 'accessories' either.

Why do they move things around for no apparent reason whatsoever?! I know about a company that does this for every OS revision, their headquarters is in Redmond.. But they do it to make people get the illusion that they're buying something fundamentally new. WHY HERE?!?! I think I'm going to go nuts.

---

### Post by mgmiller on 2008-11-27
> Opacity settings. WHERE?!?!?!The guide you referenced was for the version in Hardy.

If you have the Intrepid version of ccsm, the opacity settings are no longer in a tab in the "General Settings" area.  
They are now in the "Accessibility" section.  
Look for "Opacity, Brightness and saturation".  

If you still don't see it, try typing the word opacity in the filter field in the top left corner of the compiz config settings manager.


Remember, compiz-fusion is evolving very rapidly, there are bound to be changes in its controls from time to time.  Compared to 2 years ago, ccsm is a dream, even if they change a few things around.

If you want even simpler gui controls, you could install the package:
```
sudo apt-get install simple-ccsm 
```Although it won't help with transparency, it does make quite a few of the basic settings much easier to use.

---

