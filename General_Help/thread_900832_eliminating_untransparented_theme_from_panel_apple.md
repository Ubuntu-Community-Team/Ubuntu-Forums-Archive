---
title: "eliminating untransparented theme from panel applets"
date: 2008-08-25
forum: General Help
---

### Post by bigdee973 on 2008-08-25
how do i get into the system to eliminate the background images created from custom themes from these applets?  i want them to be transparent...look at the picture...see how the panel is transparent but the menu bar, clock, and notification bar?  well how would i go about eliminating that color and just making it transparent.  i know some other themes have it where its just transparent... any help would be fine..ALSO.. how would i go about changing the icons in the areas such as in the notification bar...i know how to do this with launchers but for instance, when i right click the network manager applet on the upper right it has no option of properities and no where to change icons.  i have a computer with wireless and someone wants to add a custom icon they seen on gnome-look.org to the wireless symbol.  thanks

[IMG]http://i94.photobucket.com/albums/l107/blasintildadeath/Screenshot-5.png[/IMG]

---

### Post by bigdee973 on 2008-08-26
bump

---

### Post by karasuman on 2008-08-26
It looks like your panel transparency is set properly for what you want...  I have all of those transparent except when they're selected/highlighted, and that's just the way they are.  Is your problem that they aren't transparent ever, or that you want them to stay transparent when you select them?

---

### Post by mfeltman on 2008-08-26
They're not transparent ever, for me.  I have the same question.  How can I modify the theme file to make Applications/Places/System etc all transparent like the rest of the panel?  I've opened up the theme in Nautilus/gedit and it looks like most gtk themes are almost entirely contained in the index.theme file as text declarations.  How can the opaque areas in the screenshot be made transparent?  For example, the way they are in 'Human'?

---

### Post by bigdee973 on 2008-08-26
now in this pic the theme is different even though it looks the same as  the previous picture, the theme in this one is the HUMAN theme and as you can see its transparent.  notice how in the other picture i have on top of this forum that the menu bar, notification area, clock, eyes and system monitor applet are not transparent.  the thing i want to do is be able to customize that background image in those sections that i circled.  not only do i want to make it transparent but also, for future customizations, be able to change those background images with a different background image whenever i choose to, just like i can to the panel where i can change the background image or change the trasnparency etc.  in certain themes they choose there own background images for the menu bar,clock,eyes, notification area, and all those other little applets you can add to the panel.. such as you can see on the first picture on top of this forum within the pink circles.  but how can i eliminate that and change it to have no background image or even give it an image or customization of my own???
[IMG]http://i94.photobucket.com/albums/l107/blasintildadeath/Screenshot-4.png[/IMG]

---

### Post by mfeltman on 2008-08-27
I spent most of last night combing through the index.theme file but it's very difficult to understand without docs.  Is there a theming HowTo for Gnome?

---

### Post by bigdee973 on 2008-08-27
yeah i want to know where extactly is the code that puts those images there... what file has the code to make it do that.  no answer so far... i guess no one really knows

---

### Post by linux_tech on 2008-08-28
Transparent windows-
[http://ubuntuforums.org/archive/index.php/t-397851.html](http://ubuntuforums.org/archive/index.php/t-397851.html)

For taskbar transparency- right click on the taskbar and go to properties.
Click the background tab and then the Solid Color button. You can then use the slider to control transparency

Always backup your /etc/X11/xorg.conf file before modifying it.

```
 sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup 
```

For a semi-transparent taskbar, you need to have compositing (desktop effects) enabled.
[http://community.livejournal.com/debian/194683.html](http://community.livejournal.com/debian/194683.html)

Have you checked out Beryl yet?

The New Users Guide to Beryl
[http://gentoo-wiki.com/Beryl](http://gentoo-wiki.com/Beryl)
[http://www.beryl-project.org/userguide.php](http://www.beryl-project.org/userguide.php)
[http://www.beryl-project.org/features.php](http://www.beryl-project.org/features.php)

Compiz transparency options- 
[http://www.ubuntu-unleashed.com/2007/08/howto-completely-transparent-shell-on.html](http://www.ubuntu-unleashed.com/2007/08/howto-completely-transparent-shell-on.html)
[http://forlong.blogage.de/entries/2007/8/29/How-to-set-up-Compiz-Fusion](http://forlong.blogage.de/entries/2007/8/29/How-to-set-up-Compiz-Fusion)

---

### Post by mfeltman on 2008-08-28
Linux_tech,

Thank you for your help, but I think you misunderstand our problem.  We know how to set the taskbar to transparent in the normal way, but in some themes, transparency is not correctly supported.  We would like to find out whether those themes can be modified/updated/corrected to support transparency in the way that Human does.  Ideally we'd like to find someone who knows the exact answer, but a good How-To for Gnome theming would be great.

---

### Post by Vexed Arcanist on 2008-08-28
This issue is related to the "controls" portion of your theme.  I am not a themer so I have no idea how to go about modifying this aspect.  I suggest you find out how and modify your chosen "control" accordingly. 

System>Preferences>Appearance>(theme tab)Customize Button>Control Tab

Now change controls around and notice some do and some don't have this issue with the Gnome Panel.

---

### Post by bigdee973 on 2008-08-28
> **Vexed Arcanist said:**
> This issue is related to the "controls" portion of your theme.  I am not a themer so I have no idea how to go about modifying this aspect.  I suggest you find out how and modify your chosen "control" accordingly. 

System>Preferences>Appearance>(theme tab)Customize Button>Control Tab

Now change controls around and notice some do and some don't have this issue with the Gnome Panel.
i have looked in that section you are mentioning a long long time ago but unfortunately there is no option to **_*[SIZE="4"]MODIFY[/SIZE]*_** the controls themes, HOWEVER!! you CAN change the _controls theme_ **_BUT _**the thing is that i want to _***MODIFY***_ it.  the thing is that the control theme that i have CHOSEN _automatically_ gives THAT white background that i do not want.  i do not want to switch the controls panel that i have selected i want to modify it the reason i dont want to change the panel is because its a rare panel and i really really like the theme BUT its just that pink circled area THAT I HAVE CIRCLED IN MY FIRST PICTURE LOOKS UGLY.  since linux is a customizable open source operating system i want to take advantage and fully customize it the way i want and the way to first start is to change the themes to the way i want it and then modify things with scripts but thats off the topic...i NEED to know how to eliminate that ugly white background that i circled in pink in the first image and make it look like the second picture WHERE I HAVE CIRCLED.  WHICH IN THE SECOND PICTURE IS all clear.  I want to modify my panel WITHOUT Having to switch control theme...i believe that section has to do with codes so changing the code i think will fix this but the thing is how do which is the code? what part of the codes in the file do i modify to change this theme? cuz i dont want that control panel theme for the PANEL (the CONTROLS THEME, changes the areas i have circled and also changes everthing else...its GTK THEME.  and if i switch the control panel i basically switch te gtk theme...somehow the controls theme is also connected to my PANEL. unfortunely the theme is very nice EXCEPT FOR THE PANEL THAT I HAVE CIRCLED and i mean the panel that says applicaitons places system, where the date and time are.  etc.  there are a ton of gtk themes that have that customize the PANEL in this way already for you but the thing is that i dont like that theme to show up. i just like the other parts of the theme that the themes change such as the scrolling bar. the color highlights etc.  i cant seem to get rid of those ugly looking backgrounds are modified to the panel by using these themes AND CONTROL THEMES. if i switch the control theme i also switch the other theme...its hard to explain i might make a video of it and post it on youtube...its not a hard thing to understand i hope.  but go ahead to look at it yourself...go to gnome look.org and downoad some gtk themes ... here is the link to my theme i want to modify [http://gnome-look.org/content/show.php?content=47955](http://gnome-look.org/content/show.php?content=47955)
now if u install it notice your PANEL.  its white like mines etc..now do what that gentlemen on top said and right click the panel and choose properties, click background and then click solid color and play with the transparency bar.  you'll notice everything gets transparent besides the palces i circled such as the menu bar etc.  and then click on what u said and change the control theme and choose human u will see that white section goes away...how can i modify the glossy pink theme to do the same thing to the panel such as human.  i hope u understand if no one does then i will post a video to better illustrate it

---

### Post by denham2010 on 2008-08-29
Hi,

Try having a look at this site:

[GTKRC Tutorial]("http://live.gnome.org/GnomeArt/Tutorials/GtkThemes")

It will guide you through how to change the settings on any widget in the GTK toolset, including panels and panel applets.

Cheers.

---

### Post by mfeltman on 2008-08-29
Thanks Vexed!  That's a leaping-off point!  :)

---

### Post by mfeltman on 2008-08-29
Denham: Glorious!

BigDee: What it comes down to is that you can't fix it through the GUI, you have to muck about in the theme source files instead.  Shouldn't be too difficult if you're used to markup languages like HTML or CSS.

---

### Post by mfeltman on 2008-08-29
BigDee I think what vexed is saying is that in the control theme you can experiment and see which control themes are correctly transparent and which aren't, then the source files can be compared.

---

### Post by bigdee973 on 2008-08-29
yes great this is a leap forward to where we want to go... if any of you happen to find the code that applies the themes for the panel let us know i will be fulfilling my part and finding it myself and if i find out i will post it for everyone to see so that they could modify the panel.

---

### Post by mfeltman on 2008-08-29
Well I've got a partial answer, after some experimentation.  It looks like certain engines being applied to GTK widgets either directly or by inheritance can interfere with transparency.

In *my* case it's the "smooth" engine in the Smooth Mech 1.1 theme I'm using.  I removed the "smooth" engine from everywhere in the file and voila: transparency.

The trouble is that this pretty much defeats the purpose of using the theme because taking away the pleasing gradients ruins it.  I'm trying to determine which gtk widget class is being used for:

The top panel
Applications/Places/Systems menu
Notification Icons
Volume Control
Panel Date/Time

So far I haven't found these specifically in the documentation.  You also have to worry about the gtk widget hierarchy/inheritance.  It's not a simple fix.

---

### Post by bigdee973 on 2008-08-29
> **mfeltman said:**
> Well I've got a partial answer, after some experimentation.  It looks like certain engines being applied to GTK widgets either directly or by inheritance can interfere with transparency.

In *my* case it's the "smooth" engine in the Smooth Mech 1.1 theme I'm using.  I removed the "smooth" engine from everywhere in the file and voila: transparency.

The trouble is that this pretty much defeats the purpose of using the theme because taking away the pleasing gradients ruins it.  I'm trying to determine which gtk widget class is being used for:

The top panel
Applications/Places/Systems menu
Notification Icons
Volume Control
Panel Date/Time

So far I haven't found these specifically in the documentation.  You also have to worry about the gtk widget hierarchy/inheritance.  It's not a simple fix.

hmmm, sounds like a whole bunch of code has to be added in order to seperate the panels from being affected just a suggested.  try to see which theme that has a transparented theme applied to the notification bar, menu bar etc...within the same engine and see the code within it.  check for some difference or some clues that make it act that way.  i will do the same in my end and see the differences and i will also speak with a theme maker from gnome-look at see what he has done to make his or her theme work the way it does just in case.

---

### Post by mfeltman on 2008-08-29
> **bigdee973 said:**
> hmmm, sounds like a whole bunch of code has to be added in order to seperate the panels from being affected just a suggested.  try to see which theme that has a transparented theme applied to the notification bar, menu bar etc...within the same engine and see the code within it.  check for some difference or some clues that make it act that way.  i will do the same in my end and see the differences and i will also speak with a theme maker from gnome-look at see what he has done to make his or her theme work the way it does just in case.

Well, the problem is that the areas being themed are not always being specifically themed.  Much of the styling is being applied by inheritance.  Also if one theme simply doesn't use any engines, or uses a different one than the "problem" theme, comparison won't buy you much.  For example I have a theme "Mist-Ivory" which is fully transparent, but it uses an engine called "mist" and is actually very small, using a base style and applying it globally.  The difference in this case would be simply "the 'smooth' engine" in general which is not the more specific answer I'm hoping to find.

---

### Post by mfeltman on 2008-08-29
To clarify, transparency doesn't have to be specifically APPLIED to a widget, it's that certain properties can be applied which negate transparency.  I haven't narrowed down exactly which ones, and even once I do they will likely apply specifically to my problem with the "smooth" gtk theming engine.  If you are having trouble with a different engine the specifics may not help you, but should at least provide you with some general hints.  Also the properties don't have to be applied to specific classes, they can be applied to broad "parent" classes and trickle down via inheritance, which means finding the specific classes to "fix" is more involved than simply inspecting theme files.  I have to muck around with the available gtkrc documentation.  So far I haven't found anything that seems comprehensive enough for my needs.


If anyone can help with the specific GTK class names for the widgets I've enumerated in my post above, it woudld be greatly appreciated.

---

### Post by bigdee973 on 2008-08-29
> **mfeltman said:**
> To clarify, transparency doesn't have to be specifically APPLIED to a widget, it's that certain properties can be applied which negate transparency.  I haven't narrowed down exactly which ones, and even once I do they will likely apply specifically to my problem with the "smooth" gtk theming engine.  If you are having trouble with a different engine the specifics may not help you, but should at least provide you with some general hints.  Also the properties don't have to be applied to specific classes, they can be applied to broad "parent" classes and trickle down via inheritance, which means finding the specific classes to "fix" is more involved than simply inspecting theme files.  I have to muck around with the available gtkrc documentation.  So far I haven't found anything that seems comprehensive enough for my needs.


If anyone can help with the specific GTK class names for the widgets I've enumerated in my post above, it woudld be greatly appreciated.

ok good job, we will find out surely, sooner or later its quite complex isnt it.. not simple at all but i think we will have an answer shortly or someone who can guide us closer and closer. im not much of a programmer myself im use to little coding.  but it should not be difficult i will be lookign further into this,

---

### Post by mfeltman on 2008-08-29
OK well bad news for me.  I started commenting out only portions of the engine "smooth" declarations from my theme.  Even with a completely empty block (no directives) following an engine "smooth" invocation, the lack of transparency still occurs.  I'd call this a bug in the GTK smooth theming engine.  I'm not sure where such a bug would be submitted, but I'm sure it must have already been...?

This means that no theme which uses the "smooth" engine will handle panel transparency correctly, at least not if the smooth engine is applied to any widget in the panel.  If I can find out the class names of every widget in the panel, I can try excluding each of them specifically from using the "smooth" engine, but other than that I see no solution, and if there's an unfortunate inheritance relationship between any "panel widget" and another widget where having the "smooth" engine is desirable, you'll simply be SOL.

---

### Post by mfeltman on 2008-08-29
I submitted a bug to gnome.bugzilla.org and it was closed as OBSOLETE within seconds.  Evidently it's a known issue but will not be fixed.  The 'smooth' engine is apparently slated for removal from GTK.  Not sure why.  Why break reverse compatibility with an unknown number of desktop themes rather than fix the problem?  I'm baffled.

---

### Post by bigdee973 on 2008-08-29
its very much like this with linux its a common thing but what i have also discovered is that with the themes that come packaged...u go into the folders and find the gtkrc file..in their there is code, someone told me put a # next to include "panelrc" up on top. but he said that some themes come coded in a different way i will ask him to take a look at the code of mine and submit it if he finds anything.  maybe there is a work around who knows but we will find out soon. so for those people pick ur favorite theme open the tar extract the file somewhere look into the folders and find the file called gtkrc and there should be code. find include "panelrc" if there is one then just put a comment symbol (#) next to it and it should make it transparent. but for those of you who dont im going to see how else you could modify it

---

### Post by denham2010 on 2008-08-29
Hi,

You can still use the smooth engine throughout your themes. Just don't have it apply to your panel style in the GTKRC file.

Find the following lines in your GTKRC (or add any that are missing) to apply a specific style to your panel and widgets: eg.

```
widget "*PanelWidget*" 					style "panel"
widget "*PanelApplet*" 					style "panel"
widget "*fast-user-switch*"				style "panel"
class "PanelApp*" 					style "panel"
class "PanelToplevel*" 					style "panel"
widget_class "*Mail*" 					style "panel"
widget_class "*notif*" 					style "panel"
widget_class "*Notif*" 					style "panel"
```

As you can see, these lines apply the style called "panel" to the panel widgets.

Next, locate the section in your GTKRC file for that style: eg.

```
style "panel"
{
	bg[SELECTED] = @selected_bg_color
}
```

(These 2 examples have been taken from the Human Theme).

If there is any reference to the smooth engine in the style definition for the panel, just remove it, or change it to an engine that supports transparency. Remembering though, some of the lines in the style may be engine specific, so a bit of a google on the engine of your choice will reveal the options available to you.

Cheers.

---

### Post by mfeltman on 2008-08-30
denham:

Brilliant!  Those class names were exactly what I needed!

Many thanks!!

---

### Post by mfeltman on 2008-08-30
Ack, denham I appended your code to the end of my gtkrc file but for some reason I still have no transparency on the main menu, notification icons, volume control, nor the panel date/time.

Thank you very much for your help in any case.

(Shouldn't a more specific style declaration override a previous one?  The Smooth engine is being applied in a default style block to widget_class "*".  Do I need to remove the more general declaration for this to work?

---

### Post by mfeltman on 2008-08-30
Aha!  I was able to cause this error to pop in the terminal:

> 
muppet@irving:~$ /home/muppet/.themes/Smooth-Mech-1.1/gtk-2.0/gtkrc:308: error: invalid string constant "panel", expected valid string constant

I don't understand.  Is "panel" not an allowed style name?  I tried changing it to "foo" but got the same error only replacing "panel" with "foo" in the message.

---

### Post by mfeltman on 2008-08-30
N/M I'm dumb.  I was putting the cart before the horse, or the style assignment before the style block...

:-)

Sadly, the transparency is still broken in the same areas.  I guess I need to make the overriding default style block more specific?

---

### Post by bigdee973 on 2008-08-30
well heres a simple work around that i should've thought about before.  some gentleman told me to do this:

It\'s realy simple thing to do and I\'ll try to explain...
1. If you want to change menu background you have to put your new image into themes directory (/home/yourname/.themes/nameoftheme/gtk-2.0/Menu-Menubar/menu.png)
2. Then change themes gtk.rc and other files so it will use your new images.

basically what you can do is go to the theme section in your home folder.  PRESS CTRL+H to show hidden files...the .theme file is hidden.. (/home/usernmae/.themes/thethemeyouwant/gtk2.0/) and find a folder called panel or menu bar of find the image called panel or menu bar or soemthing...reember everyone created the theme in a different way and its your job to find the image basically.   and find the image that refer to your panel.. and open the image up with GIMP. paint the image all white and then go to layer>transparency>color to alpha hit ok and you should have a transparent image that will be applied, save the file,  restart X with ctrl+alt+backspace and it should be applied.  the only problem is finding the panel background image.

---

### Post by mfeltman on 2008-08-30
Not the problem in my case.  Simple-Mech isn't using any images, it's the smooth engine at fault.

Two problems with the same symptom in this thread.  :-)

---

### Post by bigdee973 on 2008-08-30
> **mfeltman said:**
> Not the problem in my case.  Simple-Mech isn't using any images, it's the smooth engine at fault.

Two problems with the same symptom in this thread.  :-)

wow that truly sucks and theres nothing u can do to change that huh? not evening adding codes huh.

---

### Post by denham2010 on 2008-08-31
Hi,

Yes, the order and way you apply styles to widgets and classes makes a difference.

The order and layout of your style declarations will follow a hierarchy precedence.

It can be difficult to master, but if you have the patience, read over the following a few times:

[GnomeArt Gtk Theme Tutorials]("http://live.gnome.org/GnomeArt/Tutorials/GtkThemes")

Approximately half way down the page you will find a section titled "Applying the style".

This section goes into detail on how to apply styles using matches to get the hierarchy you need.


Also, the code I pasted eralier is just an example of the style declarations you need to make to apply a style to the appropriate widgets. The actual style block there does not add any transparency. You need to modify your own "panel" style declaration to include transparency code.


Cheers.

---

### Post by mfeltman on 2008-08-31
Thanks denham.  I thought it might follow the same sort of logic as CSS but it seems slightly different.  I have the more specific, "tranparent-friendly" styles applied last of all, so I thought that might be enough to make them take precedence over previous matches.  I'll have a look at that link.

---

### Post by bigdee973 on 2008-08-31
same here denham, im differently going to look into that link you gave us.

---

### Post by I wanted to leave on 2008-09-23
I have the same problem here using Overglossed theme. However I found the following lines in my .panelrc

widget_class "*Netstatus*" 		style "panel"
widget_class "*Tomboy*Tray*" 		style "panel"
widget "*fast-user-switch*" 		style "panel"
widget_class "*PanelToplevel*" 		style "panel"
class "Xfce*Panel*" 			style "panel"
widget_class "*Xfce*Panel*" 		style "panel"
widget_class "*PanelApplet*" 		style "panel"
widget_class "*PanelWidget*" 		style "panel"

#############################################################
#THIS MAKES THE [COLOR="Red"]APPLICATIONS PLACES SYSTEM MENU[/COLOR] ON THE PANEL
#USE PANEL STYLE
#############################################################


style "panelbar"
{
engine "pixmap"{

	image
	{
		function	= BOX
		state		= NORMAL
		file		= "panel/panel-bg.png"
		border		= { 3 , 3 , 3 , 3}
		stretch		= FALSE
	}

Am I on the right track here? Sorry, complete NooB...
I hope we all get some answers on this little problem

---

### Post by billybag on 2009-07-10
was this ever solved?

---

