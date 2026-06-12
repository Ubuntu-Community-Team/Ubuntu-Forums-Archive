---
title: "garmin communicator"
date: 2008-08-16
forum: General Help
---

### Post by dpwilson on 2008-08-16
Could someone please explain how I would get my Garmin c330 connected using Ubuntu 8.04 and also, does anyone know of a way to get garmin communicator working or an alternative that would do the same thing?

---

### Post by dpwilson on 2008-08-17
Anyone have an answer or advice?

---

### Post by mgmiller on 2008-08-17
After doing a little googling, the only thing I can think of would be to:

1) install wine
2) install the windows version of Firefox in wine
3) install the windows version of garmin communicator in wine.  It should install to the windows Firefox.

4) To do the garmin tricks, navigate using the windows version of Firefox installed in #2 above.

The only garmin experience I have in Linux is doing the updates for my nuvi.  I do them using wine and they work perfectly.

Good Luck.

---

### Post by dpwilson on 2008-08-17
Thanks will give it a try.

---

### Post by gregersrygg on 2009-07-30
> **mgmiller said:**
> 
1) install wine
2) install the windows version of Firefox in wine
3) install the windows version of garmin communicator in wine.  It should install to the windows Firefox.
4) To do the garmin tricks, navigate using the windows version of Firefox installed in #2 above.


Worked like a charm

---

### Post by CzarAlex on 2009-08-02
This is almost working for me. When I get to the install screen of the plugin, i can check the `I agree` box but cannot see any Install/Okay or Exit button and cannot proceed. Im using a laptop with a max resolution of 1024x768. The install box looks complete as I can see the 4 sides of it just no buttons. 

Suggestions?

---

### Post by mgmiller on 2009-08-02
Just to be sure you are seeing the whole window, try holding down the alt key and grab any lower part of the window and then try to move it up. 

Unlike Windows, you can grab anywhere and move it by holding the alt key.

Another way to do this is to left click the upper left corner of the window and select "Move".  You then use the up down arrow keys to make the whole window slide up and down.

Another thing you can try is doing the install in wine as a different version of windows.

When you startup wine config Applications > Wine > Configure Wine
You will be in the Applications tab.  Default settings should be high lighted.

Towards the bottom of the window is a drop down with Windows Version: and next to it you can select anything from Windows 2008 to Windows 2.0.  Sometimes XP works well, sometimes you need to install as if it was Windows 98, try a few different ones and see how it goes.  I have found that DVD decrypter and DVD shrink prefer NT 4.0 for example.

---

### Post by CzarAlex on 2009-08-02
Using Alt and moving the window didn't do anything. Next, I`ll try installing the plugin as another version of windows. If it helps, here is a screen shot of what I'm seeing.

---

### Post by mgmiller on 2009-08-02
I believe you are not seeing the whole window.  Try the clicking in the upper left corner trick.  Remember not to try to move your mouse after you select "Move", just use the up arrow key.

Sometimes, you can also move the window after selecting "Move" my moving the mouse straight up, but don't click it, just move the mouse.

---

### Post by CzarAlex on 2009-08-02
I think I`ll give up. I tried different version of windows in the wine config, running a virtual desktop at a higher resolution. Nothing. Same look on the box. 

I don't need some java or whatever installed do I? All I want to do is get my Geocache on with Linux :)

---

### Post by mgmiller on 2009-08-02
In the image you attached earlier, I don't see any of the window decorations that would surround a normal window.  Things like the maximize, minimize and close buttons in the upper right corner.  Are these things there?

---

### Post by CzarAlex on 2009-08-02
Negative. They are not. The aforementioned pic was just a section that contains the plugin dialog. I have yet to see any traditional mix/max/close icons on that screen regardless of measures exercised. Also, I am unable to close the install dialog by right clicking on its task bar icon and choosing close. Its grayed out.

---

### Post by mgmiller on 2009-08-02
Go back into the wine configuration and click on the "Graphics" tab.

In the Window Settings area, you should have "Allow the window manager to decorate the windows" checked and also "Allow the window manager to control the windows" checked.  The other 2 can be unchecked.  Click Apply and Ok at the bottom.

Then try rerunning the Garmin installer and see if it's any better.

---

### Post by Havok_Rocka on 2009-08-09
I have the same problem as Czar Alex. Somehow the splash-screen is not complete. If there is another solution to using the communicator plug-in, please let me know.

---

### Post by CzarAlex on 2009-08-09
I asked around at the Wine forums at WineHQ and they suggested I install some "Winetricks" or something. Doing so made no difference. :(

---

### Post by dalesd on 2009-10-06
So what would it take to get a Garmin Communicator Plugin for linux?  Is this something Garmin would have to release?  

BTW, I found this active thread over at garmin's developer forum.  If you want a garmin communicator plugin for linux, this might be a good place to ask for one.

[https://forums.garmin.com/showthread.php?t=1281](https://forums.garmin.com/showthread.php?t=1281)

---

### Post by dak-AD on 2009-11-08
install the windows version of firefox, then try to install CommunicatorPlugin.exe (from my.garmin.com) using wine. 

If that doesn't work ('Next' button neither visible nor tab-to-able), then open wineconfig, and, under 'graphics', increase the 'screen resolution' slider to the next setting up (for me, it was 172dpi) and click 'apply'.

Now, run the CommunicatorPlugin.exe thingy with wine again. note how the windows are effin massive now.

when the problem window pops up, use alt + left-mouse to try to drag the window upwards so you can see the bottom.

if this works, great! if, like me, it won't let you drag it up far enough, drag it down instead till it switeches desktops downwards (tweak your desktop switcher settings if you only have two, side-by-side, desktops -- you need one above the other): you should finally see the bottom of the window, with the very top of the 'Next' link for you to click.

once it's installed, set the dpi to whatever it was before and go to wine > applications > firefox > firefox to start the wine'd version of firefox, and use this to go to my.garmin.com. it says the plugin's installed (w00t!) but i haven't had a chance to check that it actually works yet.

---

### Post by sancho-pl on 2010-02-12
Check this out: [http://www.andreas-diesner.de/garminplugin/](http://www.andreas-diesner.de/garminplugin/)
Far better solution than using wine ;)

---

### Post by sd790 on 2010-03-28
Based on several posts from several different forums, this is what worked well for me with karmic.
1.  Download the windows versions of [Firefox]("http://www.mozilla.com/en-US/products/download.html?product=firefox-3.6.2&os=win&lang=en-US") and the [Garmin Communicator plugin]("http://www8.garmin.com/support/download_details.jsp?id=3608").
2.  Run these commands in a terminal: 
     [INDENT][FONT=Courier New]sudo apt-get install wine[/FONT]
[FONT=Courier New]    wget [http://kegel.com/wine/winetricks](http://kegel.com/wine/winetricks)[/FONT]
[FONT=Courier New]                                     sh winetricks corefonts dotnet20[/FONT]
[FONT=Courier New]                                     wine Firefox\ Setup\ 3.6.2.exe[/FONT]
[/INDENT] 3.  Open Applications --> Wine --> Configure Wine
4.  In the Graphics tab, change resolution to 172dpi.  Click OK.
5.  In a terminal run: 
 [INDENT][FONT=Courier New]wine CommunicatorPlugin_291.exe[/FONT]
[/INDENT] 6.  During installation, you will need to move the window up by holding down the alt key while dragging the window.  This will let you get to the buttons you need to complete the installation.
7.  Go back to the the resolution setting that you changed in step 3 and restore it back to 96dpi.
8.  Open Applications --> Wine --> Programs --> Mozilla Firefox --> Mozilla Firefox
9.  Use this instance of Firefox with your Garmin.

---

### Post by pabc on 2010-03-31
hmm. I've done all that. The garmin test pages says the plugin is installed fine but cant a garmin. Which is odd, as I know it's there and connected as I just imported a run off it into sporttacks (via mono).

I tried grabbing the latest USB drivers and installing them under wine which also appeared to work but still no joy.

---

### Post by fep1343 on 2010-07-22
To install garmin communicator in ubuntu Lucid see this:

[http://www.gpspassion.com/forumsen/topic.asp?TOPIC_ID=121878]("http://www.gpspassion.com/forumsen/topic.asp?TOPIC_ID=121878")

---

