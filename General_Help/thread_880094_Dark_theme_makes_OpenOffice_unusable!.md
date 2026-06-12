---
title: "Dark theme makes OpenOffice unusable!"
date: 2008-08-04
forum: General Help
---

### Post by blazemore on 2008-08-04
I have a lovely dark GTK theme. For most applications it works perfectly and integrates nicely.

OpenOffice.Org is a complete mess. The Writer (for example) has the dark grey of the theme as the page colour, and none of the icons show up in OpenOffice Formula.

Basically, can I fix it or do I have to use a light-coloured GTK theme?

---

### Post by alsamman on 2008-08-04
Hey, yeah that's what disappointed me when I wanted to have dark Gtk themes. OpenOffice writer page was black and so was all the other OpenOffice programs. You can partially fix the Writer problem by going to Tools>Options>OpenOffice.org>Appearance and messing around there, but if I were you, I would just stick to the lighter themes. Sorry:(

---

### Post by colobix on 2008-08-04
This will fixc your problem,
First of all you have to install the Wine windows emulator, now you can install and run windows applications like open office, now uninstall the linux version of open office, download and install the windows version.
You can now run open office with normal colours and stuff.
If you would like to change themes on your open office applications, you can download and install them as plugins.

[http://www.pcc-services.com/ooo-theme.html](http://www.pcc-services.com/ooo-theme.html)

---

### Post by atoc on 2008-08-04
> **colobix said:**
> This will fixc your problem,
First of all you have to install the Wine windows emulator, now you can install and run windows applications like open office, now uninstall the linux version of open office, download and install the windows version.
You can now run open office with normal colours and stuff.
If you would like to change themes on your open office applications, you can download and install them as plugins.

[http://www.pcc-services.com/ooo-theme.html](http://www.pcc-services.com/ooo-theme.html)
Kinda defeats the purpose of having a native version of OpenOffice, doesn't it?
It IS a viable workaround, I'll give you that, but it's much easier to just change to a lighter theme when using OpenOffice and switch back to a dark theme when done, than go thru all that trouble.
I'm just sayin'  ;)

---

### Post by blazemore on 2008-08-04
Is there a way to apply different themes to different applications?

---

### Post by colobix on 2008-08-04
Well, I suggest u give it a try. To me it works fine and i dont see any differance between the linux and windows version of openoffice.
The only thing u have to do is to create program launchers to the exe files.
So keep the dark theme, download and install the windows version of open office from [http://www.softpedia.com/progDownload/OpenOfficeorg-for-Windows-Download-5272.html](http://www.softpedia.com/progDownload/OpenOfficeorg-for-Windows-Download-5272.html)

I promise it works fine.
Good luck.n

Oh. and do NOT install it under c:
Change it to z;/home/yourfolder/OpenOffice so you can create a program launcher.

---

### Post by ZeldaFan on 2008-08-04
I believe that there is a package that specifically integrates openoffice with ubuntu's theme. If you are using the openoffice suite that came with your ubuntu installation, you might be able to find it through synaptic and then uninstall it. If not, you can try uninstalling openoffice entirely and using the linux version available from the website (not the repos). The specific package's name escapes me at the moment and I'm not at my linux system now, so that's all I help you with now. But I'll try finding the package for you ASAP.
PS - I have a hunch that the package is called openoffice.org-gnome

---

### Post by chunchengch on 2008-08-05
> **blazemore said:**
> I have a lovely dark GTK theme. For most applications it works perfectly and integrates nicely.

OpenOffice.Org is a complete mess. The Writer (for example) has the dark grey of the theme as the page colour, and none of the icons show up in OpenOffice Formula.

Basically, can I fix it or do I have to use a light-coloured GTK theme?

Some dark GTK themes are compatible well with the OpenOffice.Org, such as DigitalDark, if the OpenOffice.Org, especially Calc, messes up with the dark theme, you can remove packages openoffice.org-gtk and openoffice.org-gnome to use the default style of OpenOffice.Org.

[COLOR="Red"]$ sudo apt-get remove openoffice.org-gtk openoffice.org-gnome[/COLOR]

One day if you find a dark theme available, basically, you need only to install openoffice.org-gtk to make OpenOffice.Org to apply the theme.

[COLOR="Red"]$ sudo apt-get install openoffice.org-gtk[/COLOR]

---

### Post by calc on 2008-08-05
This is a known issue in OpenOffice.org, they put the program into High Contrast mode when the theme is dark. You can get icons back by installing openoffice.org-style-hicontrast, but they won't look that great.

[http://www.openoffice.org/issues/show_bug.cgi?id=80636](http://www.openoffice.org/issues/show_bug.cgi?id=80636)

---

### Post by tuxxy on 2008-08-05
Yes hi-contrast is fine for me, I had an error that all icons were missing aswell and text only at one time now that looks crazy.

---

### Post by donoterase on 2008-09-04
hello all. I was wondering if anyone has found another solution to this issue. I'm a mandriva user, but their forums suck when it comes to technical issues outside of the mandriva scope. I've also found that this forum 9/10 has helped me with my issues. I hope you all welcome me with open arms still!

Anyway, if no one has an alternative solution, I might be able to provide one. I'm on the PC at the moment, which runs XP, and my laptop is not currently with me.

---

### Post by donoterase on 2008-09-04
>  Re: Dark theme makes OpenOffice unusable!
Is there a way to apply different themes to different applications? 

Yes there is. I have "the" ultimate dark desktop IMO [http://www.gnome-look.org/content/show.php/Ultimate+Dark+Theme?content=88344]("http://www.gnome-look.org/content/show.php/Ultimate+Dark+Theme?content=88344") for those who would like to see a very usable dark desktop with a screenschot of openoffice workaround.

You can force an application to use a specific theme. For example, mandriva control centre (MCC) has fixed font colors that can't be forced to change with a theme configuration, so with my dark theme, the text was no where to be seen as the background and text were both black. I created a script that forced MCC to use a lighter theme. Simple. I did the same with openoffice, and will continue to do so to any other application that clashes with dark themes.

---

### Post by robotmechanic on 2008-09-19
Hey guys, I think I found the setting to fix *some* issues. A more complete fix/hack is linked and quoted below.

Change page color:

Open OpenOffice Writer
Click Tools --> Options --> OpenOffice.org dropdown box --> Appearance

From there, you can change the color of your page if that's your problem

If your Writer is in "High Contrast" mode try this:

Open OpenOffice Writer
Click Tools --> Options --> OpenOffice.org dropdown box --> Accessibility
Uncheck "Automatically detect high contrast mode of operating system"

If your OpenOffice is super screwed up by dark themes, try this neat hack from Adam Stovicek:

[http://www.rebelzero.com/fixes/ooodarkgtkworkaround]("http://www.rebelzero.com/fixes/ooodarkgtkworkaround")

> I'd been having issues with colors in OpenOffice.org applications while using a dark GTK2.0 theme for my Gnome environment. OpenOffice.org applications would start in a high contrast mode and would not display the pages with correct coloring. What you would see on the screen could be far different from what you print. Apparently this is a known bug at OpenOffice's bug tracker, but there's yet to be a fix. One commenter posts that it still persists in the 3.0 Beta.

The Ubuntu forums had this asked and answered with a workaround, but that broke with the new release of 8.04 Hardy Heron. I couldn't find an updated workaround and between desperation, aggravation, and a lack of patience, motivation set in and I went about to find one of my own.

First a short lesson. The shell scripts that run all of OO.o's applications are found in the following directory:

/usr/lib/openoffice/program/

Each of the OO.o applications has its own shell script.

    * swriter - OpenOffice.org Word Processor
    * scalc - OpenOffice.org Spreadsheet
    * sbase - OpenOffice.org Database
    * simpress - OpenOffice.org Presentation
    * smath - OpenOffice.org Math
    * sdraw - OpenOffice.org Drawing

Each of these executes one main shell script, soffice, while passing it an argument that defines what application you're planning on using. It's this file we'll be using in our workaround

In order to tell OO.o what theme to use, we set an environment variable pointing to the gtkrc file of that theme while we execute that script for that program. For instance, the following would launch OpenOffice.org Word Processor with Ubuntu's Human them:

sudo env GTK2_RC_FILES=/usr/share/themes/Human/gtk-2.0/gtkrc /usr/lib/openoffice/program/swriter

Two flaws with this is 1) because you need to root privileges to set environment variables, you inadvertently run OO.o applications with root privileges as well, and 2) it's a hassle to have to do this manually. You could edit each of the OO.o shell scripts and include the above environment variables such as...

#!/bin/sh

cmd='dirname "$0"'/soffice
exec "$cmd" -writer "$@"

...would become...

#!/bin/sh

cmd='dirname "$0"'/soffice
exec env GTK2_RC_FILES=/usr/share/themes/Human/gtk-2.0/gtkrc "$cmd" -writer "$@"

... but that would be a hassle to change them all over again if you change your mind in the future. I thought it best to edit just one. Unfortunately, this resulted in a small error in which I had to adjust another file to make it all work.

First thing I did was rename the soffice file. Open a terminal and at the command line just move it.

sudo mv /usr/lib/openoffice/program/soffice /usr/lib/openoffice/program/soffice1

Now, make a new soffice file.

sudo gedit /usr/lib/openoffice/program/soffice

Paste the following shell script code and save the file.

#!/bin/sh
env GTK2_RC_FILES=/usr/share/themes/Human/gtk-2.0/gtkrc /usr/lib/openoffice/program/soffice1 "$@"

Next, make it executable.

sudo chmod +x /usr/lib/openoffice/program/soffice

Here is what I though would be the end of it, but the original soffice script actually sets the name of the binary program that is used based on its own file name. Since we renamed it to soffice1, we also need to rename soffice.bin to soffice1.bin. (Brave souls can skip this and see the Plan B at the end.)

sudo mv /usr/lib/openoffice/program/soffice.bin /usr/lib/openoffice/program/soffice1.bin

Now, each and every OpenOffice.org app should launch using the Ubuntu Human theme to display the correct layout coloring. I had mixed results when using other themes. Some worked well while others didn't work at all. The dark theme that I'm using, Overglossed by TheRob, gives me dark-blue panel colors with some themed areas, but high contrast icons. Layout color was incorrect. Slickness-Black, also by TheRob, forces OO.o applications into their default high contrast mode. For myself, I'll stick with the Human theme so I can enjoy the graphs in my spreadsheets the way they were intended.

Now, this assumes that nothing about your OpenOffice.org installation will change any time soon. This workaround could very well break with a future update to OpenOffice.org. It would be very likely to break between Hardy Heron and Intrepid Ibex. But that's why we call this a workaround and not a fix.

If something needs clarifying, don't hesitate to ask.

Thanks to Adam Stovicek for figuring out this little hack. Try and see if these work.

---

### Post by donoterase on 2008-09-19
Hi again. The above hack previously mentioned is exactly how I get OpenOffice to work. I force it to use clearlooks-quicksilver. I can confirm that this hack does indeed work. 

NOTE: Some themes work better than others, so if you don't succeed at first, try using a different gtkrc file from another theme. Happy modding.

---

### Post by robotmechanic on 2008-09-19
Thanks for verifying donoterase, I was waiting until someone else tried it :)
Hopefully I'll get more courageous with these hacks as time goes on

---

### Post by donoterase on 2008-09-19
Not a problem. Another point worthy of mentioning is that this hack can be applied to other applications that don't work well with dark themes. For example, i use this hack to force gedit and Mandriva Control Center to use lighter themes for usability. Happy hacking. In the meantime please check out my dark theme here: [http://gnome-look.org/content/show.php/Divinorum-Revisited?content=89200&PHPSESSID=ea50aabd55d2206b1f80549fb3181d84]("http://gnome-look.org/content/show.php/Divinorum-Revisited?content=89200&PHPSESSID=ea50aabd55d2206b1f80549fb3181d84")

---

### Post by stovicek on 2008-09-22
> **robotmechanic said:**
> 
If your OpenOffice is super screwed up by dark themes, try this neat hack from Adam Stovicek:

[http://www.rebelzero.com/fixes/ooodarkgtkworkaround]("http://www.rebelzero.com/fixes/ooodarkgtkworkaround")

Thanks to Adam Stovicek for figuring out this little hack. Try and see if these work.
Unfortunately, I've come down with a bit of OCD over that website and overhauled it. This makes all the links people have graciously added to forums broken. My fault. Same text at it's new page:

[http://www.rebelzero.com/fixes/openofficeorg-dark-theme-workaround-with-ubuntu-804/8](http://www.rebelzero.com/fixes/openofficeorg-dark-theme-workaround-with-ubuntu-804/8)

---

### Post by raid996 on 2009-01-06
> **chunchengch said:**
> Some dark GTK themes are compatible well with the OpenOffice.Org, such as DigitalDark, if the OpenOffice.Org, especially Calc, messes up with the dark theme, you can remove packages openoffice.org-gtk and openoffice.org-gnome to use the default style of OpenOffice.Org.

[COLOR="Red"]$ sudo apt-get remove openoffice.org-gtk openoffice.org-gnome[/COLOR]

One day if you find a dark theme available, basically, you need only to install openoffice.org-gtk to make OpenOffice.Org to apply the theme.

[COLOR="Red"]$ sudo apt-get install openoffice.org-gtk[/COLOR]

This worked perfectly for me, and the result with my dark theme was quite good!
Thanx a lot

---

### Post by marko_4454 on 2009-02-12
robotmechanic, Thanks a lot. it worked great!

---

### Post by BDNiner on 2009-02-13
I don't know what I did but robotmechanic's fix did not work for me. None of the OOo apps will start now. I am completely removing OOo and starting over since I have version 3 installed and i believe that this solution is for version 2.x

*After a reinstall OOo now opens using the human theme when using my dark theme. Thanks for the solution.

---

### Post by kogger on 2009-02-23
Is there a way to do this with Skype? When I have Slickness-Black installed it gets really hard to see people's names when they're highlighted.

---

### Post by benhur99ph on 2009-02-28
> **chunchengch said:**
> Some dark GTK themes are compatible well with the OpenOffice.Org, such as DigitalDark, if the OpenOffice.Org, especially Calc, messes up with the dark theme, you can remove packages openoffice.org-gtk and openoffice.org-gnome to use the default style of OpenOffice.Org.

[COLOR="Red"]$ sudo apt-get remove openoffice.org-gtk openoffice.org-gnome[/COLOR]

One day if you find a dark theme available, basically, you need only to install openoffice.org-gtk to make OpenOffice.Org to apply the theme.

[COLOR="Red"]$ sudo apt-get install openoffice.org-gtk[/COLOR]

Thank you! This worked fine for me.

---

### Post by detroit/zero on 2009-02-28
I'm more curious to know which theme you're using that causes the problems.

I would do first as someone else suggested and try monkeying around with tools>options>appearance settings. It's all I had to do to make mine look right and usable. (screenshot attached)

The theme I'm using is [SlicknessBlack]("http://www.gnome-look.org/content/show.php/Slickness+Black?content=73210"), available at gnomelook.org Slickness allows you to set colors in the gnome-them-manager for various things - text input fields, windows, etc..

It's been a while since I had to worry about it, but I don't remember having to do a whole lot to make OOo look nice.

---

### Post by scoobymad555 on 2009-03-02
been running a dark theme for quite a while now mostly with success thanks to "color-manager" ....

using a custom variant of :

Aero-ion3.1 for controls
DarkX2-s for window borders
tangerine for icons
color-manager to adjust theme colours where required


Had good success for the most part .... only app that seems to struggle a bit is epiphany but firefox is ok so generally tend to defer to that. There's a couple of settings that can't be altered with color-manager but it's still being worked on so hopefully these will be available in the future :)

color-manager found here : [http://gnomecc.sourceforge.net/](http://gnomecc.sourceforge.net/)
(hope it helps! :) )


Some screengrabs of my desktop :-

[IMG]http://i43.photobucket.com/albums/e367/scoobymad555/Screenshot.png[/IMG]

[IMG]http://i43.photobucket.com/albums/e367/scoobymad555/Screenshot-1.png[/IMG]

[IMG]http://i43.photobucket.com/albums/e367/scoobymad555/Screenshot-1-1.png[/IMG]

---

### Post by detroit/zero on 2009-03-03
> **scoobymad555 said:**
> been running a dark theme for quite a while now mostly with success thanks to "color-manager" ....
Yeah, I can't believe I forgot to mention gnome-color-chooser. It's a handy app to have. Allows you to change a lot of options, colors, and even some fonts. Definitely worth checking out.

---

### Post by IConrad01 on 2009-03-19
Hello.  Just wanted to post here and say that running Ubuntu 8.10 (amd64) w/ multiple dark-themes, this hack has absolutely no effect for me.  It simply doesn't do anything at all.

For whatever reason, I can only view the high-contrast icons; regardless of which iconset I tell OOo to use.

---

### Post by calc on 2009-04-06
This apparently will be solved when OOo 3.2 is released, which will be in Ubuntu 10.04

[http://www.openoffice.org/issues/show_bug.cgi?id=35482](http://www.openoffice.org/issues/show_bug.cgi?id=35482)

---

### Post by FokkerCharlie on 2009-05-17
Cool

The hack on the previous page works well for me- I have SlicknessBlack installed, and use Darklooks with OOo.

10.4 is a long time away for this bug to be fixed, I think!

Charlie

---

### Post by Jameshardy88 on 2009-05-18
> **calc said:**
> This apparently will be solved when OOo 3.2 is released, which will be in Ubuntu 10.04

[http://www.openoffice.org/issues/show_bug.cgi?id=35482](http://www.openoffice.org/issues/show_bug.cgi?id=35482)

Well thats some good news at least, bit far off but better than nothing =)

---

### Post by artshark on 2009-12-13
hey i was having the same issue with my oo3 install
in the link, stoveick posts, a user generates a script to fix this. this script works for me except for this:
"Renaming old launch script...
Creating new launch script...
Giving new script executable permissions...
Renaming binary for compatibility...
mv: cannot stat `soffice.bin': No such file or directory
Complete :)
"
soffice.bin is perhaps something else in oo3, as this script was intended for 2. what should i change it to?
heres a link to the script: [http://aur.archlinux.org/packages/openoffice-dark-gtk-fix/openoffice-dark-gtk-fix/openoffice-dark-gtk-fix.sh](http://aur.archlinux.org/packages/openoffice-dark-gtk-fix/openoffice-dark-gtk-fix/openoffice-dark-gtk-fix.sh)
please help!!!!

---

### Post by garybrlow on 2010-01-12
Anyone tried using OOO3.2 release candidate? Xubuntu 9.10 uses a dark theme all is ok except the Menu Bar Text which seems to rendered in dark gray on black background. The text is there but you can hardly see them.

Cheers!

):P

---

### Post by artshark on 2010-01-12
> **garybrlow said:**
> Anyone tried using OOO3.2 release candidate? Xubuntu 9.10 uses a dark theme all is ok except the Menu Bar Text which seems to rendered in dark gray on black background. The text is there but you can hardly see them.

Cheers!

):P
promising. i rolled back to 2.4.1 for the moment. i'll try 3.2 when its officially released, perhaps

---

### Post by Macinbomzh on 2010-01-12
> **blazemore said:**
> Is there a way to apply different themes to different applications?

just create and log into the user of openoffice with startx and change the theme, it won't work with
Dust, I have no idea why. (worked in jaunty, didn't test in karmic)

---

### Post by warfacegod on 2010-01-12
I found an easier way than this link last week but lost it.

[http://www.rebelzero.com/fixes/openofficeorg-dark-theme-workaround-with-ubuntu-804/8]("http://www.rebelzero.com/fixes/openofficeorg-dark-theme-workaround-with-ubuntu-804/8")

---

### Post by Thomas Garman on 2010-02-05
[chunchengch]("http://ubuntuforums.org/member.php?u=285117")

Your approach worked perfectly for me.  Now my open office looks "normal" in the sense that it's a white background with icons etc even though my theme is "Slickness Black".

Thanks.

---

### Post by Hagar Delest on 2010-02-06
See that one (especially the end), it even brings back the default gray shading: [[Solved] OOO_FORCE_DESKTOP for dark themes]("http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=27216").

---

### Post by dmstudios on 2010-06-21
Go to Tools > Options > Appearance and change the document background to white. You can also change the default font color to black instead of automatic.

Cheers!

---

### Post by aCsbD6N5xj on 2010-07-10
Is there a way to do the same with gEdit? White font on a black page in this case is really tiring on my eyes and I use gEdit way more than OpenOffice.org

I looked for other gEdit color schemes but I couldn't find what I was looking for (White page and black font).

I use the Slickness Black Theme btw

---

