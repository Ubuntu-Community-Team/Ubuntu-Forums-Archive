---
title: "noob to linux - need some help/guidance"
date: 2008-09-20
forum: General Help
---

### Post by Mudgy on 2008-09-20
Hi - I'm a 42 year old web designer/developer in Toronto, Canada, and use Mac's and PC's every day. A client bought me a brand new Acer Aspire One with Linux (my choice), and now I'm trying to learn more about "ubuntu" - and the groovy 3d cube/desktop effect.

Not sure if this will even work with my little laptop.

The other issue that I'm having is that the original desktop showed 3 icons in each category (games, work, etc.), then I did all the available upgrades - as recommended in the user manual - and after that, only 2 icons per category show up. 

I tried dragging icons into the available 3rd space, but when I 'drop' the icon, nothing happens. I can drag an icon onto one of the 2 existing favourites (or whatever you call them), and it will swap - so it does do something.

So my questions in a nutshell are:

1) how do I get 3 icons to show in my favourites for each desktop panel?

2) can I install/run ubuntu on this little Acer Aspire One with Linux (linpus lite is the version as I recall).

Any help would be appreciated - thanks,

Mike

---

### Post by 1/0 on 2008-09-20
1. The icon is actually just a textfile with the suffix .desktop located in the Desktop folder. Examples of how they should look:

```

[Desktop Entry]
Name=Opera
Comment=Opera Web Browser
Exec=[path to opera]
Icon=
Terminal=false
Type=Application
Categories=Application;Network;

```

```
[Desktop Entry]
Encoding=UTF-8
Type=Link
X-Enlightenment-Type=Removable
X-Enlightenment-Removable-State=Full
Name=Partition 1
Icon=drive-harddisk
Comment=Removable Device
URL=file://org/freedesktop/Hal/devices/volume_uuid_blablabla

```

You'll find the UUID by the following command in a terminal:

```
ls /dev/disk/by-uuid
```

2. There's a [wiki](https://help.ubuntu.com/community/AspireOne) on how to install Ubuntu on the Aspire One.

[edit]Not sure I understood correct. That is if its desktop icons you're asking for [/edit]

---

### Post by sayakb on 2008-09-20
1. Are you referring to the icons just towards the right side of the menu bar? Well, you might just have to drop an icon. Otherwise, right click on the panel, click **Add to panel** and select Application Launcher and the Forward button. Select among the programs which you want to add and press **Add.**
Btw, what do you want to add?

2. Laptop  specs please?

---

### Post by Mudgy on 2008-09-20
Thank you 1/0 - I found the uuid in the terminal window - not sure what to do with that.

I looked in the desktop folder (in the files section) and there are no files listed in the desktop section. I even tried showing hidden files.

Any suggestions? Cripes - I'm sure this is very basic for you guys - but it's all brand new to me. I look forward to being good at this one day soon, but for now, frankly - I suck!

thanks,

Mike

---

### Post by 1/0 on 2008-09-20
If its a desktop icon you want linking to a partition, UUID is needed. If you want a link to a program, folder or other things it is not needed. What do you want to link to? A folder or?

---

### Post by Mudgy on 2008-09-20
> **LinuxIsInnovation said:**
> 1. Are you referring to the icons just towards the right side of the menu bar? Well, you might just have to drop an icon. Otherwise, right click on the panel, click **Add to panel** and select Application Launcher and the Forward button. Select among the programs which you want to add and press **Add.**
Btw, what do you want to add?

2. Laptop  specs please?

acer aspire one - linux - 120GB HD, 512MB ram - blue.

On the home screen, there are 4 sections - Connect, Work, Fun, and Files. Within those, there are 2 icons showing (for example in Connect, it's showing Browser and Messenger). I'd like to add Email to that grouping.

When I first got this machine - 2 days ago - there were 3 icons in every category on the home page, then I did the updates, and there are only 2. I've used the Asus machine, and am not totally inept. You could drag and swap whatever program icons you wanted into that shaded area, and they would appear. I can drag and swap any of the existing 2 icons, but cannot add a 3rd - and there appears to be enough room, and there were 3 before I did the updates.

Also, to 1/0 - I did a search for .desktop on my machine, and found a xfce.desktop file - not exactly sure this is what I should be looking at, as it isn't very intuitive regarding which parameters to change - most values are "=Xfce 4" 

thanks,

Mike

---

### Post by Mudgy on 2008-09-20
Here is a picture of my desktop - hopefully this clarifies what the issue is, and what I'm trying to fix.

thanks - m.

---

### Post by 1/0 on 2008-09-20
Heh. You got me there! No idea about that. I'll have a look around and see if I can find something. 

Is that Ubuntu btw?

---

### Post by 1/0 on 2008-09-20
[Here's a video](http://www.youtube.com/watch?v=Daslydb3eVo) that explains something like what you're looking for and [here's](http://www.reghardware.co.uk/2008/09/05/ten_aspire_one_tips/page3.html) a guide. 

If its a program that you're trying to add; is it installed?

Also. You might want to look in the Xfce Settings manager for settings. If you can't open it from a menu, type *xfce-setting-show* in a terminal.

---

### Post by Mudgy on 2008-09-20
thanks - I'll have a peek at that later on - washing the car now - it's not ubuntu yet - just bone stock out of the box with the updates all downloaded. Something in the updates buggered it up.

Thanks again - I'll post my results later on.

Mike

---

### Post by Mudgy on 2008-09-20
in that video, she seems to 'right click' on the empty header area on the home screen to bring up a list of options - I can't get that to come up, or get any right click functions.

frustrating little thing so far! this should be dead simple.

there was an XML file that the person in the video was editing - maybe that would be better for me to tinker with.

any right-click solutions for the aspire one with linux?

i'll do a search too.

(this part should be much easier to solve - haven't even looked at switching it over to ubuntu yet).

i'm not afraid.

---

### Post by Mudgy on 2008-09-20
not so simple - no solutions out there yet.

going to read the manual.

another site said this about "RIGHT CLICK"

Enable the advanced menu. Linpus comes with a modified XFCE desktop. It is possible to get a Fluxbox like application menu when you right click on the desktop in XFCE. This is achieved by enabling “Show Desktop Menu on Right Click” option in the “Behavior” tab of the “Desktop preferences” XFCE dialog box.

However, I cannot figure out how to get to the XFCE dialog box - which is driving me crazy!

should have just bought the ibook for 3 times the price...but this thing is just so compact, and *should* work fine.

---

### Post by Mudgy on 2008-09-20
Hi Guys - I've done some poking around, and was all happy to find a desktop.xml file, and in that file (opened in firefox) was a desktop icon value set to "2" - which suggested to me that I'd have to change that to "3" to fix my issue.

However, when I double click and it opens in firefox, I can't edit it. When I try to open the containing folder, it says:

"Could not open folder. The nautilus file manager is not running ...

So how do I get the Nautilus file manager to run, or how can I edit that xml file in a different manner?

---

### Post by Mudgy on 2008-09-20
Here is the XML that I think is wrong - I highlighted the row that I question in dark red below:


<mcs-option>
<option name="brightness_0_0" type="int" value="0"/>
<option name="brightness_0_1" type="int" value="0"/>
<option name="color1_0_0" type="color" value="           15104,           23296,           35072,           65535"/>
<option name="color1_0_1" type="color" value="           15104,           23296,           35072,           65535"/>
<option name="color2_0_0" type="color" value="           15872,           26624,           40448,           65535"/>
<option name="color2_0_1" type="color" value="           15872,           26624,           40448,           65535"/>
<option name="colorstyle_0_0" type="int" value="0"/>
<option name="colorstyle_0_1" type="int" value="0"/>
**[COLOR="DarkRed"]<option name="desktopiconstyle" type="int" value="2"/>[/COLOR]**
<option name="icons_font_size" type="int" value="12"/>
<option name="icons_icon_size" type="int" value="64"/>
<option name="icons_use_system_font_size" type="int" value="0"/>
<option name="imagepath_0_0" type="string" value="/usr/share/xfce4/backdrops/wallpaper.png"/>
<option name="imagepath_0_1" type="string" value="/usr/share/xfce4/backdrops/wallpaper.png"/>
<option name="imagestyle_0_0" type="int" value="3"/>
<option name="imagestyle_0_1" type="int" value="3"/>
<option name="managedesktop-show-warning-on" type="int" value="0"/>
<option name="showdm" type="int" value="0"/>
<option name="showimage_0_0" type="int" value="1"/>
<option name="showimage_0_1" type="int" value="1"/>
<option name="showwl" type="int" value="0"/>
<option name="xineramastretch" type="int" value="1"/>
</mcs-option>

---

### Post by Mudgy on 2008-09-20
this little acer running linux sucks - it's going back on monday unless i get some kind of dramatic resolution to this stupid little issue.

how complicated do they need to make it? 

I figured out where the likely issue is - but then I can't edit the xml file with openoffice/writer - because the path where the file shows up when I search isn't navigable through the 'writer' software.

all i did was run the updates like I was supposed to.

is linux always this much fun? 

maybe you linux guys should go out and get married - it's almost as much fun.

---

### Post by Sef on 2008-09-20
> this little acer running linux sucks - it's going back on monday unless i get some kind of dramatic resolution to this stupid little issue.

how complicated do they need to make it? 

If the hardware makers would release their specs then this issue would go away.

> I figured out where the likely issue is - but then I can't edit the xml file with openoffice/writer - because the path where the file shows up when I search isn't navigable through the 'writer' software.

Use gedit to edit files.  From the terminal > gksudo gedit path_to_file

> all i did was run the updates like I was supposed to.


That's good you do.

> is linux always this much fun? 

maybe you linux guys should go out and get married - it's almost as much fun. 	

Sarcasm tends to turn people off from helping you.  We are all volunteers here, so at times threads get answered fast and at times slow.  If you want a faster response download Xchat IRC, it is available through add/remove.   The other option is to get paid support.

---

### Post by gregconquest on 2008-09-20
You asked in the original post about adding ubuntu to your system. Ubuntu is not really something you can add, it would be a change -- like moving from XP to Vista. Ubuntu is known for being easy to use. Some of the other netbook versions of linus are known for being difficult and limited . . .

Do a search for your netbook's name and ubuntu. If you have all of your data backed up off the machine, and if you have a system restore CD to put the system back to the way it was when you got it, then you've got nothing to lose, other than more time.

But even then, take a look
install ubuntu (netbook name)
and see if others are having an easy time or not.

And know that you probably want to (eventually) get the netbook remix version of ubuntu, but this would be added after a successful install of regular ubuntu. More info should be easy for you to find.

Good luck.
Greg

---

### Post by Mudgy on 2008-09-20
Hi Guys - sorry for the sarcasm - no offense intended - more of a poke at marriage being a never ending battle.

I managed to get into some desktop.xml file that I could edit - it opened in something very basic like a wordpad - and I changed that value that I questioned from "2" to "3" - and magically all my desktop menus disappeared!

I am left with the search box at the top, the status bar at the bottom right, and the shut down button - so that was obviously not the thing to tamper with!

I'm going to do the factory default at a buddy's house tomorrow - I only have a 1GB USB stick here, and my iMac G5 doesn't seem to want to boot from the provided backup/restore CD anyway - holding C at boot doesn't work, and I can't select it as a "startup disk".

I think I should just do the restore - then run the updates again and see what happens. Must have just been an anomaly if no one else has ever seen this problem.

If it does it again - then I'll exchange it and run the updates in store before I leave.

thanks,

Mike

---

### Post by mb_webguy on 2008-09-20
> **Mudgy said:**
> is linux always this much fun? 

maybe you linux guys should go out and get married - it's almost as much fun.

The problem is that you're using a very funky distribution of Linux with which the people on this forum apparently have no experience.  I certainly had no idea what I was looking at when I took a look at that screenshot you posted.  If it's Ubuntu, then it's been heavily modified by Acer.

Linux is not Windows.  There is a difference between the operating system and the graphical desktop environment.  Windows only has one desktop environment for its operating system available, so it's rarely necessary to differentiate between the two.  Actually, the two are so integrated with each other that it would be difficult to do so.

Linux, however, has numerous desktop environments available, and most are much more customizable than that of Windows.  Different distributions of Linux incorporate different desktop environments.  Ubuntu uses Gnome, while the Kubuntu variant uses KDE and the Xubuntu variant uses Xcfe.  As I said, from the screenshot you posted, I have no idea exactly what you're using.  A normal installation of Ubuntu, which uses a fairly default configuration of the Gnome desktop environment, looks like the attached screenshot.

Since we don't know exactly what you're using, there's only so much we can help you, especially since the problems you're having seem to be related more to the desktop environment than the Linux operating system.  If you'd like to install Ubuntu (or at least a version of Ubuntu that hasn't been so drastically altered by Acer, if that is the case with your laptop), then I think you'll find many people willing and able to help you with the installation and with any questions or problems you might have afterward.

As to your remark about "Linux people", I'll politely ignore it, since you're obviously speaking out of frustration.  I think you'll find, though, that "Linux people" are as varied and socially capable as any other portion of the general population.

---

### Post by Mudgy on 2008-09-21
Figured it out - thanks for the tips - and I would to apologize for venting my frustrations - it was wrong, and I should have just gone for a walk, or stepped away from the computer.

Anyway - ubuntu has NOTHING to do with my issues - I'm not even running ubuntu yet. The issue is with Acer's update on the Aspire One linux version.

After the update, many users (as I have discovered in an acer aspire forum) experienced the same issue and obvious frustration. Thankfully a member on that board posted a solution which I will share.

I also found that adding the XFCE menu helps a ton for accessing a wide variety of relevant menu items. You can add the menu by hitting "alt + F2" then entering:

xfce4-panel -a

Scroll down the list of items that appears, and drag the XFCE menu to the lower right task bar, dropping it in the location that you want.

To fix the 2 icons appearing vs. 3 (as it should be) - go to:

home/user/.config/xfce4/desktop/group-app.xml

You can find this by clicking on "My Files" in the FILES menu box on the landing page, then click on "My Disk" in the left pane. Be sure to go under the VIEW menu and select "Show Hidden Files".

Then double-click on the ".config" button in the right pane, and navigate to the file above. Double-click to open it.

Once it's open, copy the code below and paste it over the existing code, then save it and reboot. You will then have 3 icons in each menu box, and can drag your favourite items into the boxes.

Hope that helps - now that I've done that, I can start exploring ubunto.

Last point - not sure how to mark this as solved - so if an admin reads this - please mark as SOLVED. 

Thanks - Mike



    <?xml version="1.0" encoding="UTF-8"?>
    <xfdesktop>
       <upperbutton>/usr/share/desktop-directories/upperbutton.desktop</upperbutton>
            <setting exec="">/usr/share/desktop-directories/Settings.directory</setting>
            <help exec="">/usr/share/desktop-directories/help.directory</help>
    <group>
           <id>1</id>
           <sequence>0</sequence>
           <!--<directory_file title="" icon="" tag_background="/usr/share/backgrounds/images/blue-bk-title.png">/usr/share/desktop-directories/Internet.directory</directory_file>-->
           <directory_file exec="" tag_background="/usr/share/backgrounds/images/home-blue-title.png">/usr/share/desktop-directories/Connect.directory</directory_file>
           <background_picture>/usr/share/backgrounds/images/blue-bk.png</background_picture>
           <app is_arrow="1" name="" sequence="-1-10">/usr/share/applications/blue-more.desktop</app>
    </group>
      <group>
           <id>2</id>
           <sequence>1</sequence>
           <directory_file exec="" tag_background="/usr/share/backgrounds/images/home-orange-title.png">/usr/share/desktop-directories/Works.directory</directory_file>
           <background_picture>/usr/share/backgrounds/images/orange-bk.png</background_picture>
        <app is_arrow="1" name="" sequence="-1-10">/usr/share/applications/orange-more.desktop</app>
    </group>
      <group>
           <id>3</id>
           <sequence>2</sequence>
           <directory_file exec="" tag_background="/usr/share/backgrounds/images/home-yellow-title.png">/usr/share/desktop-directories/Fun.directory</directory_file>
           <background_picture>/usr/share/backgrounds/images/yellow-bk.png</background_picture>
        <app is_arrow="1" name="" sequence="-1-10">/usr/share/applications/yellow-more.desktop</app>
           
    </group> 

    <group>
        <id>4</id>
        <sequence>3</sequence>
           <directory_file exec="" tag_background="/usr/share/backgrounds/images/home-green-title.png">/usr/share/desktop-directories/Files.directory</directory_file>
        <background_picture>/usr/share/backgrounds/images/green-bk.png</background_picture>
        <app is_arrow="1" name="" sequence="-1-10">/usr/share/applications/green-more.desktop</app>
    </group>
    <group>
           <id>5</id>
           <sequence>4</sequence>
           <directory_file exec="" tag_background="/usr/share/backgrounds/images/blue-bk-title.png">/usr/share/desktop-directories/Connect.directory</directory_file>
           <background_picture>/usr/share/backgrounds/images/blue-bk-large.png</background_picture>
        <app is_arrow="1" name="" sequence="-10">/usr/share/applications/blue-back.desktop</app>
        <app sequence="5" acs="email">/usr/share/applications/AME.desktop</app>
             <app sequence="1" acs="im">/usr/share/applications/acerim.desktop</app>
             <app sequence="0">/usr/share/applications/linpus-web.desktop</app>
             <app sequence="2">/usr/share/applications/webmail.desktop</app>
           <app sequence="3">/usr/share/applications/googlemap.desktop</app>
    <!--         <app sequence="3">/usr/share/applications/luvcview.desktop</app>-->
    <!--         <app icon="ftp.png" name="FTP" sequence="3">/usr/share/applications/net-gftp.desktop</app>-->
    <!--    <app sequence="3" acs="rss">/usr/share/applications/acerrss.desktop</app> -->
        <app sequence="6">/usr/share/applications/acerrss.desktop</app>
        <app sequence="4">/usr/share/applications/edesktop/wikipedia.desktop</app>
    </group>
      <group>
           <id>6</id>
           <sequence>5</sequence>
           <directory_file exec="" tag_background="/usr/share/backgrounds/images/orange-bk-title.png">/usr/share/desktop-directories/Works.directory</directory_file>
           <background_picture>/usr/share/backgrounds/images/orange-bk-large.png</background_picture>
             
            <app is_arrow="1" name="" sequence="-10">/usr/share/applications/orange-back.desktop</app>
       <app sequence="0">/usr/share/applications/openoffice.org-1.9-writer.desktop</app>
       <app sequence="2">/usr/share/applications/openoffice.org-1.9-calc.desktop</app>
        <app sequence="1">/usr/share/applications/openoffice.org-1.9-impress.desktop</app>
        <app sequence="3">/usr/share/applications/acercalendar.desktop</app>
        <app sequence="4">/usr/share/applications/acercontact.desktop</app>
        <!--app icon="burning.png" name="CD/DVD Burning" sequence="4">/usr/share/applications/gnome-gcalctool.desktop</app>
        <app sequence="4">/opt/Adobe/Reader8/Resource/Support/AdobeReader.desktop</app>-->
        <app sequence="6">/usr/share/applications/galculator.desktop</app>         
        <!--app sequence="5">/usr/share/applications/gnome-dictionary.desktop</app-->         
       <!--    <app icon="snapshot.png" name="Snapshot" sequence="6">/usr/share/applications/gnome-screenshot.desktop</app>-->              
       <app sequence="5">/usr/share/applications/xpad.desktop</app>         
    </group>
      <group>
           <id>7</id>
           <sequence>6</sequence>
           <directory_file exec="" tag_background="/usr/share/backgrounds/images/yellow-bk-title.png">/usr/share/desktop-directories/Fun.directory</directory_file>
           <background_picture>/usr/share/backgrounds/images/yellow-bk-large.png</background_picture>
        <app is_arrow="1" name="" sequence="-10">/usr/share/applications/yellow-back.desktop</app>
             <app sequence="4">/usr/share/applications/pcmmvp.desktop</app>
             <app sequence="1">/usr/share/applications/pcmphoto.desktop</app>
             <!--<app icon="games.png" name="Games" sequence="2">/usr/share/applications/tuxpuck.desktop</app>-->
        <dir sequence="0" dir_id="1">/usr/share/desktop-directories/Games.directory</dir>
        <app sequence="5">/usr/share/applications/ucview.desktop</app>
             <!--app icon="voice_recorder.png" name="Voice Recorder" sequence="7">/usr/share/applications/realplay.desktop</app-->
             <app sequence="3">/usr/share/applications/kolourpaint.desktop</app>
             <app sequence="2">/usr/share/applications/gimp.desktop</app>
    <!--         <app icon="internetradio.png" name="Internet Radio" sequence="7">/usr/share/applications/realplay.desktop</app>
             <app icon="picture.png" sequence="8">/usr/share/applications/gthumb.desktop</app>-->
    </group>

    <group>
        <id>8</id>
        <sequence>7</sequence>
           <directory_file exec="" tag_background="/usr/share/backgrounds/images/green-bk-title.png">/usr/share/desktop-directories/Files.directory</directory_file>
        <background_picture>/usr/share/backgrounds/images/green-bk-large.png</background_picture>
       
        <app is_arrow="1" name="" sequence="-10">/usr/share/applications/green-back.desktop</app>
        <app sequence="2">/usr/share/applications/Document.desktop</app>
        <app sequence="5">/usr/share/applications/Picture.desktop</app>
        <app sequence="4">/usr/share/applications/Music.desktop</app>
        <app sequence="1">/usr/share/applications/Video.desktop</app>
        <app sequence="0">/usr/share/applications/Download.desktop</app>
             <app sequence="3">/usr/share/applications/Thunar.desktop</app>         
    </group>

    <group>
        <id>9</id>
        <sequence>8</sequence>
        <directory_file exec="" icon="" tag_background="/usr/share/backgrounds/images/gray-bk-title.png">/usr/share/desktop-directories/Settings.directory</directory_file>
        <background_picture>/usr/share/backgrounds/images/gray-bk-large.png</background_picture>
        <app is_arrow="1" name="" sequence="-10">/usr/share/applications/settings-back.desktop</app>
        <app sequence="6">/usr/share/applications/gsynaptics.desktop</app>
        <app sequence="5">/usr/share/applications/system-config-date.desktop</app>
        <app sequence="7">/usr/share/applications/linpus-printconf-gui.desktop</app>
        <app sequence="0">/usr/share/applications/xfce-display-settings.desktop</app>
        <app sequence="4">/usr/share/applications/sysinfo.desktop</app>
        <app sequence="8">/usr/share/applications/onlineupdate.desktop</app>
        <app sequence="9">/usr/share/applications/redhat-userpasswd.desktop</app>
        <app sequence="10">/usr/share/applications/keyboard_layout.desktop</app>
        <app sequence="2">/usr/share/applications/networkcenter.desktop</app>
        <app sequence="3">/usr/share/applications/audio.desktop</app>
        <app sequence="1">/usr/share/applications/powercenter.desktop</app>
        <app sequence="11">/usr/share/applications/linpus-scim-setup.desktop</app>
      </group>
    <dir id="1" parent_dir_id="0">
       <directory_file exec="" tag_background="/usr/share/backgrounds/images/yellow-bk-title.png">/usr/share/desktop-directories/FunGames.directory</directory_file>
           <background_picture>/usr/share/backgrounds/images/yellow-bk-large-games.png</background_picture>
    <!-->         <app sequence="0">/usr/share/applications/linpus-circuslinux.desktop</app><-->
             <app is_arrow="1" name="" sequence="-1-10">/usr/share/applications/yellow-back.desktop</app>

             <app sequence="9">/usr/share/applications/ltris.desktop</app>
       <app sequence="0">/usr/share/applications/linpus-frozen-bubble.desktop</app>
       <app sequence="1">/usr/share/applications/tuxpuck.desktop</app>
       <app sequence="2">/usr/share/applications/llk_linux.desktop</app>
       <app sequence="3">/usr/share/applications/supertux.desktop</app>
       <app sequence="4">/usr/share/applications/bubbleshooter.desktop</app>
       <app sequence="5">/usr/share/applications/ButterFlight.desktop</app>
       <app sequence="7">/usr/share/applications/snooker.desktop</app>
       <app sequence="6">/usr/share/applications/checkers.desktop</app>
       <app sequence="7">/usr/share/applications/mahjong.desktop</app>
       <app sequence="8">/usr/share/applications/volleyballey.desktop</app>
    </dir>
    </xfdesktop>

---

