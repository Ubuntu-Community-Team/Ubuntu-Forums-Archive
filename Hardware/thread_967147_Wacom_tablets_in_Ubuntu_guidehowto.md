---
title: "Wacom tablets in Ubuntu guide/howto"
date: 2008-11-01
forum: Hardware
---

### Post by Loïc2 on 2008-11-01
The [[COLOR="DarkRed"]Community wiki documentation[/COLOR]]("https://help.ubuntu.com/community/Wacom"), [[COLOR="DarkRed"]Configure Wacom Devices Using the .fdi File Method[/COLOR]]("https://help.ubuntu.com/community/Wacom.fdi") and for legacy xorg.conf use the [[COLOR="DarkRed"]example xorg.conf files[/COLOR]]("https://help.ubuntu.com/community/WacomTroubleshooting") are regularly being updated for Ubuntu 9.04 Jaunty Jackalope, but the guide is also geared towards each Ubuntu release starting with Ubuntu 6.04 Dapper Drake, and is updated for each new release.

This thread is the forum side of the wiki, if you have questions or want to add information to the guide but are not sure you'll be able to keep it clean and simple.

Basically for any Ubuntu release, always check first on [[COLOR="DarkRed"]The Linux Wacom Project[/COLOR]]("http://linuxwacom.sourceforge.net/") if the version of the linux wacom driver you have in your distribution supports your model of tablet - use System>Administration>Synaptic Package Manager or
```
dpkg -p wacom-tools  | grep Version
```

Note : as Intuos 4 users would have noticed, the driver in Ubuntu 9.04 or earlier doesn't support their model. See [[COLOR="DarkRed"]this thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1120029") for instructions on how to make your tablet supported.

If your tablet is supported, on Ubuntu 9.04 Jaunty Jackalope (and later) it should be fully recognised by default (pen, eraser, ExpressKeys, and mouse, even though mouse can be tricky), with input hotplug support, and without the need for any configuration. All configuration is now stored in /usr/share/hal/fdi/policy/20thirdparty/10-wacom.fdi - you can also copy that file to /etc/hal/fdi/policy/custom_wacom.fdi and edit it to adjust default options. Because of a bug in the 10-wacom.fdi file in Ubuntu 9.04, wacom devices won't appear in the graphical configuration utility wacomcpl. You can either use [[COLOR="DarkRed"]the custom .fdi file Favux has posted in this thread[/COLOR]]("http://ubuntuforums.org/showpost.php?p=7234134&postcount=176"), which should work with external USB Wacom tablets (and possibly other tablets), or use a script to change default Wacom device names in Ubuntu 9.04 to ones wacomcpl will recognise - see [[COLOR="DarkRed"]this thread[/COLOR]]("http://ubuntuforums.org/showpost.php?p=7143916&postcount=154"). Alternatively, you can continue to use any previous script using xsetwacom commands, provided you replace the name of the devices with the ones you get with ```
xinput -list
```

On releases older than Ubuntu 8.10 you only need to edit your /etc/X11/xorg.conf as in the wiki - you save time and run less risks to mess up your configuration. If it doesn't support your model and you can't upgrade to a more recent version, use the "Specific cases" part of the guide (many different contributors).

In Ubuntu 8.10 Intrepid Ibex, due to changes in Xorg, wacom support doesn't use xorg.conf by default, but the method used by Ubuntu 9.04 - except with less possibilities. Basically, if you plug your tablet it will work (if it doesn't unplug it and plug it again), but only the stylus is supported, and if you want to configure its properties you need to do it according to [[COLOR="DarkRed"]Wacom.fdi[/COLOR]]("https://help.ubuntu.com/community/Wacom.fdi").

If you want to use the eraser and the pad, you'll need to revert to the old method, which means adding lines in /etc/X11/xorg.conf following [[COLOR="DarkRed"]the guide[/COLOR]]("https://help.ubuntu.com/community/Wacom") and [[COLOR="DarkRed"]Example Lines for /etc/X11/xorg.conf[/COLOR]]("https://help.ubuntu.com/community/WacomTroubleshooting"). However, with the move away from using xorg.conf, it's becoming harder not to hose X (unless you reuse an old xorg.conf.

In Ubuntu 9.04, the distribution will probably revert to using xorg.conf to set up wacom devices, since the HAL method used in Ubuntu 8.10 doesn't allow anything more than the stylus, and even that doesn't work for TabletPC, serial tablets, and users who need to calibrate the stylus.

**[COLOR="Red"]_[CENTER]Note for Tablet PC users in Intrepid :[/CENTER]_[/COLOR]**
The problem you're facing is also a problem of configuration - compiling a driver might not help. According to The Linux Wacom Project, version 8.0 **already** supports Tablet PC, and the version that ships in Intrepid is even more recent (8.1.4). However, there's still a bug in 8.1.4 that might affect you where touching the tablet with the pen freezes the input. If you have that problem, then you can install the 8.1.6 drivers according to [[COLOR="DarkRed"]Installing the Lastest Driver in Ubuntu[/COLOR]]("https://help.ubuntu.com/community/Wacom/LatestDriver")

For the configuration, here's an explanation I got in one of the launchpad bug reports: the default configuration for Intrepid works for hotpluggable tablets. With a tablet PC, the wacom device is always there, and that's the problem (it won't be recognised).

I'm not an expert, but from what I've see people report in bug threads, for Tablet PC the best solution (maybe even the only one) is to revert to the old way to configure wacom devices, that is editing /etc/X11/xorg.conf . That is a bit risky, so make sure you have two operating system installed (the best is to have another Ubuntu installed on another partition, for example an LTS version like Ubuntu 8.04) so you can access the net and ask for help here if you hosed X. Having another Ubuntu would also allow you to continue any urgent and important work during the few hours / days it takes for one of us to reply to any problem you would have (there's time we'll be sleeping or away for the computer ;) ). It will also allow for easy editing of the xorg.conf you need to edit. Alternatively, you can also use a Live CD.

Tablet PC users want the Option B) in Intrepid (although you should always check first if, on your particular hardware, the default configuration in Intrepid works - just read the first few paragraphs of the guide to make sure) and either reuse an xorg.conf from a previous version of Ubuntu, or use the example lines at [[COLOR="DarkRed"]Example Lines for /etc/X11/xorg.conf[/COLOR]]("https://help.ubuntu.com/community/WacomTroubleshooting"). 

If you don't manage to configure it, please tell us. If you manage to get it to work, please tell us too, since I don't have any Tablet Pc to check if my advices really work.

[COLOR="Blue"]In your posts, please specify the model of your Wacom tablet, and the Ubuntu version you're using. If your Tablet won't work, a nice idea is to check and tell us if the model of your tablet is supported by the wacom driver provided by your version of Ubuntu (it will save everybody chacking and keep all the information in one post). You can also attach your xorg.conf file to your post (Chose "Go Advanced" then use the little paperclip icon[/COLOR]

[SIZE="5"][COLOR="Red"]Please do not paste your whole xorg.conf, or extract longer than a few lines - attach them instead. Same goes for very long error messages, if you don't know which lines are relevant it's better to attach the output.[/COLOR][/SIZE]

That would prevent the thread growing so big that nobody reads it before posting while the solution might be a few post away.
Remember : Go Advanced, then the little paperclip icon on top. Pretty please.

---

### Post by mesilliac on 2008-11-03
With the default setup (autoconfiguration via HAL, only stylus working), if you want to change the options for the stylus you can create a custom .fdi file and put it in /etc/hal/fdi/policy/. This preserves hotplugging while enabling you to configure your tablet

Here's mine as an example. You can add new options just by inserting more x11_options lines. Option names are the same as in xorg.conf.

/etc/hal/fdi/policy/mytabletrules.fdi
```

<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

<deviceinfo version="0.2">

  <device>
    <match key="info.capabilities" contains="input">
      <match key="info.product" contains="Wacom">
	<merge key="input.x11_options.TPCButton" type="string">on</merge>
	<merge key="input.x11_options.KeepShape" type="string">on</merge>
      </match>
    </match>
  </device>

</deviceinfo>

```

I didn't really know how to add this info neatly to the wiki, so here it is for now.

---

### Post by Loïc2 on 2008-11-03
Thanks a lot mesilliac, I used your post to create a new wiki page at [https://help.ubuntu.com/community/Wacom.fdi](https://help.ubuntu.com/community/Wacom.fdi) and linked the guide to this page (the same way we link to a separate page for xorg.conf options). Hope it's ok for you ;) and if you see more thing to add just go on and click "edit" or post it here.

I still haven't managed to configure my Cintiq 12wx properly, the cursor isn't aligned with the pen tip on all the screen and it's really annoying (wacomcpl is in Intrepid, but it doesn't detect neither the Cintiq nor another Intuos 3). If somebody manages to get it right first, you're welcome to help ;)

---

### Post by 123marra on 2008-11-04
Dear Loic2.

Yesterday I installed Ubuntu Intrepid Ibex (version 8.10), kernel 2.6.27 on my Acer TravelMate C110 tablet PC. Of course, the tablet/touch functionality was lost. I read quite a few posts and instructions on how to bring the tablet functionality back. I also downloaded a file 
linuxwacom-0.8.1-6.tar.bz2 from [http://linuxwacom.sourceforge.net](http://linuxwacom.sourceforge.net). 

Could you please let me know if my laptop will obtain the touch functionality after installing linuxwacom-0.8.1-6.tar.bz2the and (the most important question!) how I can compile that file(s) [linuxwacom-0.8.1-6.tar.bz2] into a running software. I am a new Linux user and definitely not an IT advanced one. I simply don't know the basics of compiling the software. Maybe you can refer me to a clear guide. I am afraid of doing something wrong, because then I won't be able to restore the default.

Thanks in advance

123marra

---

### Post by Arabiest on 2008-11-04
Thank u gents

---

### Post by Loïc2 on 2008-11-04
> **123marra said:**
> Could you please let me know if my laptop will obtain the touch functionality after installing linuxwacom-0.8.1-6.tar.bz2the and (the most important question!) how I can compile that file(s) [linuxwacom-0.8.1-6.tar.bz2] into a running software. I am a new Linux user and definitely not an IT advanced one. I simply don't know the basics of compiling the software.

Read the guide carefully, then the first post in this thread. In no way do we advise you to go and compile linuxwacom. In 99.9% of the cases, your hardware will be supported by the default wacom drivers provided by Intrepid (they're about same as compiling them from the file you downloaded).

If you type this in a terminal:
sudo dpkg -p wacom-tools | grep Version
You'll see that the version in Intrepid is 8.1.4, which isn't much different than your downloaded 8.1.6 in terms of hw support. Actually, it's newer than the Linux Wacom Project (LWP) official 8.0, which they say already support touch for tablets.

Now, with tablets PC in Intrepid the problem you're facing is a problem of configuration - compiling a driver won't help.

Explanation : the default configuration for Intrepid works for hotpluggable tablets. With a tablet PC, the wacom device is always there, and that's the problem (it won't be recognised).

I'm not an expert, but from what I've see people report in bug threads, for Tablet PC the best (maybe even the only) solution is to revert to the old way to configure wacom devices, that is editing /etc/X11/xorg.conf . That is a bit risky, so make sure you have two operanting system installed (the best is to have another Ubuntu installed on another partition, for example an LTS version like Ubuntu 8.04) so you can access the net and ask for help here if you hosed X. Having another Ubuntu would also allow you to continue any urgent and important work during the few hours / days it takes for one of us to reply to any problem you would have (there's time we'll be sleeping or away for the computer ;) ).

So read the guide carefully, you want the Option B) in Intrepid. I've updated the example configuration files at [https://help.ubuntu.com/community/WacomTroubleshooting](https://help.ubuntu.com/community/WacomTroubleshooting) with a warning for Tablet PC users, I'll edit the guide too (and maybe copy/paste this post at the beginning of the thread.

If you don't manage to configure it, please tell us. If you manage to get it to work, please tell us too, since I don't have any Tablet Pc to check if my advices really work.

---

### Post by 123marra on 2008-11-04
Dear Loic2,

Thanks a lot for your prompt reply.

I did exactly what you wrote in the Troubleshooting section. I accessed the xorg.conf file from the Terminal using the command line 

gedit/etc/X11/xorg.conf

The file xorg.conf was open then in a separate .txt file.

However, when I try to save the file after the changes were typed, the system tells me I don't have enough priviledges, so I can't save changes. As I posted above, the system was installed yesterday and I am an administrator. What can be wrong with my access rights then?

Hope to hearing from you soon.

Thanks in advance and regards,
123marra

---

### Post by 123marra on 2008-11-04
Dear Loic2.

Thanks a lot for your help. I report the results so far for installing table functionality for my Acer TravelMate C110 laptop running Ubuntu 8.10 Intrepid Ibex with kernel 2.6.27 (release date 30 October 2008):

1) Before your proposed changes (for wacom devices) my original 

/etc/X11/xorg.conf file had the following command lines (after a few paragraphs of text at the beginning of the file):

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

2) After I have posted the proposed changes, the complete string of command lines looks like this:

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerFlags"
        Option "AutoAddDevices" "False"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/input/wacom"      
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/input/wacom"    
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/input/wacom"   
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
EndSection

3) Answering my own question above, I have found on Internet a thread, exactly explaining why I did not have the rights to save the changes to the config file (/etc/X11/xorg.conf):

[http://ubuntuforums.org/archive/index.php/t-869748.html](http://ubuntuforums.org/archive/index.php/t-869748.html)

The solution is:

Go to the terminal via Applications --> Accessories --> Terminal

In the Terminal type the following:

gksudo gedit /etc/X11/xorg.conf

A window will appear asking for a password --> type an administrator password  --> a config file will then be open in a .txt format.

Make the changes (in my case just add extra command lines as you suggested) and save the file (an existing file will be replaced by a new one).

4) Closed the files and logged out from my account and logged in again. And bingo! my stylos works and I can use it as a mouse, clicking on icons, browsing through files, opening applications etc.

5) However, some other questions are still open:

a) Acer TravelMate C110 had a virtual keyboard, which was possible to use with a stylos. What happened to that functionality? It is present in Ubuntu and if yes, how to bring it to life? Maybe the same problem is applicable to other tablet PC's...

b) I tried to draw lines in OpenOffice.org Draw. It works but only until I release the pressure. Then the line becomes a picture and it is not possible to continue drawing / writing unless I click on a line drawing button. Does it means there is no handwriting recognition functionality in Ubuntu? If yes, then how can I find it? 

c) Do I need to install some other software (maybe also applicable to other devices) to solve the problems mentioned above or what I have now is as far as Ubuntu can get so far with a table functionality.

I would very much appreciate your answer.

Thank you in advance and with regards,

123marra

---

### Post by Loïc2 on 2008-11-04
> **123marra said:**
> I did exactly what you wrote in the Troubleshooting section. I accessed the xorg.conf file from the Terminal using the command line 

gedit/etc/X11/xorg.conf

All the advised commands on the guide and in this forum should be :
```
gksudo gedit/etc/X11/xorg.conf
```

I checked the guide and the example page, but I couldn't find any occurence where we forgot to use sudo and wrongly advised using
```
gedit/etc/X11/xorg.conf
```

Could you please point to the wrong occurence so we can correct it (and other people don't encounter your problem?

As for your other post, I've got to leave now and will probably not be able to reply before 24 hours. But here are some ideas off the top of my head:
a) virtual keyboard is an application like another - if you're talking about XP/Vista, your comp came with the application added (by the hw maker for instance). Have a look in synaptic, or google for it and ubuntu.
b) for drawing, I use Inkscape and Gimp, they work great. For handwriting recognition, you installed a desktop Ubuntu, I don't think it will come with an handwriting recognition app by default (same for desktop XP for example, unless I'm mistaken). Try to google it, look in synaptic or try to see what Nokia use for their Linux tablets, or check what the special version of Ubuntu Cannonical is developing for MID/nettop devices will use (can't remember the name). Then you'll just have to install the same program(s). In the future, you could also try a Live CD of their Ubuntu's special version, and if you like it install that instead of the default Ubuntu 8.10 for desktop use.

c) see above, yes, and it's 100% sure the software exist since Linux is already used in this manner. The hw rec software might be proprietary, but an open source version might already have been there for years, just that I never had to use it.

---

### Post by mesilliac on 2008-11-04
Some people do need the latest 0.8.1-6 linuxwacom drivers... they fix a bug where touching the pen to the tablet freezes input (essentially making the tablet useless in intrepid). *If you don't have this bug you probably don't need them.* Anyway, the linuxwacom drivers come with precompiled binaries so all you need to do is:

 * double click the linuxwacom-0.8.1-6.tar.bz2 file and extract it to your desktop (you can delete these later)
 * open a terminal (Accessories > Terminal)
 * type the following:
 ```

cd Desktop/linuxwacom-0.8.1-6/prebuilt
sudo ./uninstall
sudo ./install

```
 * Restart X by logging out, then logging in again

If this messes anything up for you, you can always go back to the default by running in a terminal:
```

sudo aptitude reinstall xserver-xorg-input-wacom wacom-tools

```

Just wanted to answer that because I know I've been worried about it in the past ;).

---

### Post by mesilliac on 2008-11-04
I was curious so I looked - ubuntu has a virtual keyboared installed by default but hidden. You can show the menu items for it by going to System > Preferences > Main Menu and enabling "onBoard" (seems to be under preferences for some reason).

For handwriting recognition you can use "cellwriter". Install it via Add/Remove, or using synaptic (System > Administration > Synaptic Package Manager).

I heard a while ago that "xournal" is a good journal / note taking app, but I've never used it myself (again, install using either add/remove or synaptic).

---

### Post by Loïc2 on 2008-11-04
mesilliac, thanks for correcting my mistakes. I edited my post and linked to your post ion both this thread and the guide. Your explanation on installing/deinstalling wacom drivers from the LWP is really good an clear, it would certainly help others if you could add it to the guide. Considering you already know the formating on the forums, it should be pretty straightforward - and me doing it would be a copy-paste in this case (which wouldn't be fair) since everything is there.

@123marra
For tablets apps, I did a bit of search, and indeed CellWriter is often advised. You'll get more apps on [http://luke.no-ip.org/x60tablet/](http://luke.no-ip.org/x60tablet/) (just scroll to the bottom of the page.

Hw recognition seems still limited to grid recognition, you can't link letters (yet) which is behind what exists elsewhere.

Summary of apps:
HW recognition :
CellWriter [http://risujin.org/cellwriter/](http://risujin.org/cellwriter/) it's in the repos, so just 
```
sudo apt-get install cellwriter
```

On-screen kb (mesilliac's one is already included, so maybe that's not so useful):
gok (Gnome, maybe the included one?), klavier (KDE), onscreen

Other :
Xournal, often cited, can annotate PDF (no hw recognition)
```
sudo apt-get install xournal
```

But as I said, the link above does a far better job, and links more apps, see especially [http://groundstate.ca/tabletsoft](http://groundstate.ca/tabletsoft) and check onenote (haven't been able to connect to their website though).

Basically, once you have a good setup, you can edit the page at [https://help.ubuntu.com/community/TabletPC](https://help.ubuntu.com/community/TabletPC) and add your experience - at the moment it's quite empty, and I'm sure many users face similar problems as you encounter.

Since I don't own any Tablet PC, I can't do the same as for Wacom tablets - only somebody that uses a Tablet will know what really work! I'm also interested in this subject, but unless Lenovo creates a 13,3' Thinkpad Tablet PC and prices it aggressively (<1000$, compared to their ~2000$ T60 :( ) I'll keep sitting on the fence...

---

### Post by Loïc2 on 2008-11-08
I did a big update on the [Example Lines for /etc/X11/xorg.conf]("https://help.ubuntu.com/community/WacomTroubleshooting") to better support serial tablet and Tablet PC users + verified there's no need for ```
Option "AutoAddDevices" "False"
```

However, since the configuration on [The Linux Wacom Project]("http://linuxwacom.sourceforge.net/") is quite outdated, I need someone with a Tablet Pc or a serial tablet to tell me where there wacom device appears in /dev/ - is it still /dev/wacom, or is it now /dev/input/wacom like on USB tablets? The LWP doc points to "/dev/ttyS0" :guitar:, which isn't always wrong by see, but is going to be a pain each time the number changes.

I also updated [the guide]("https://help.ubuntu.com/community/Wacom") and a few other wacom-related pages as well. And I asked upstream for the future of wacom devices configuration... which for them seems xorg.conf (along with a big white beard *à la* ZZ Top).

---

### Post by Xfcn on 2008-11-08
Well with my Wacom Bamboo and 8.10 on my Dell Inspiron E1505, I've got it working just fine with the default setup. I'd like to keep the ability to hot-swap, but I'd also like to be able to change the cursor speed. Right now it moves faster than I'd like.

---

### Post by 123marra on 2008-11-09
Dear Loic2,

You were right about the sudo command. I got confused and mixed things up. Sorry for it. 

Mesilliac, 

Thanks a lot as well for pointing out the virtual keyboard and other useful tips. Meanwhile I found a link 

[http://www.vafrous.com/articles.php?request=7](http://www.vafrous.com/articles.php?request=7) 

and installed Gournal. It works, but it is for an older version of Ubuntu (6.06) and I will delete it. 

Thanks a lot again and regards,
123marra

P.S. I have one little questions (a silly one ;): If I install a new program / application, them how do I display an icon for it on my desktop or put an icon into my Applications menu? It seems I can't just drag and drop it.

---

### Post by Loïc2 on 2008-11-09
> **Xfcn said:**
> I'd like to keep the ability to hot-swap, but I'd also like to be able to change the cursor speed. Right now it moves faster than I'd like.

According to the [[COLOR="Red"]list of xorg.conf options at the LWP[/COLOR]]("http://linuxwacom.sourceforge.net/index.php/howto/inputdev"), the option to change cursor speed is:
```
Option "Speed" "Rspeed"
                  sets the cursor's  relative  movement speed to Rspeed.  The default value is 1.0.  A Rspeed greater than 1.0 will speed up the cursor's  relative movement.  A Rspeed less than 1.0 but greater  than 0 will slow  down the  cursor's  relative movement. A Rspeed too close to 0 is not recommanded.
```

To add an option, create a custom_wacom.fdi file following the instructions at [[COLOR="Red"]Wacom.fdi[/COLOR]]("https://help.ubuntu.com/community/Wacom.fdi")

However, that option is only for the "cursor" device and at the moment only the configuration with xorg.conf (Option B) allow the use of the cursor (the mouse).

The stylus (=pen tip) device is usually set in absolute mode, where the whole screen is mapped to the surface of your tablet, which is the only decent way if you want to draw. In this situation, to solve your problem, no need to edit the wacom configuration - just set the stylus to "Window" instead of "Screen" when configuring Extended Input Devices in your drawing program - see [[COLOR="Red"]these guide screenshots[/COLOR]]("https://help.ubuntu.com/community/Wacom#Configuring%20the%20%22Extended%20Input%20Devices%22").

If you want to use the pen tip as a mouse, you can achieve that with the default solution (creating a custom_wacom.fdi file). The xorg option is :
```
Option "Mode" "Relative"
```
In your custom_wacom.fdi, the line would be:
```
   <merge key="input.x11_options.Mode" type="string">Relative</merge>
```

If that's what you want, I created a custom .fdi file for you and added the option - it's called Relative.fdi and i put it on the [[COLOR="Red"]Wacom.fdi page[/COLOR]]("https://help.ubuntu.com/community/Wacom.fdi") so it could benefit others. Just put it in /etc/hal/fdi/policy


> **123marra said:**
> P.S. I have one little questions (a silly one ;): If I install a new program / application, them how do I display an icon for it on my desktop or put an icon into my Applications menu? It seems I can't just drag and drop it.

Applications comming from Ubuntu repositories should install the icon themselves in one of the application menus (for this kind of apps it should be "Accessibility" or "Universal Access"). If it doesn't and is in Intrepid or Hardy repositories, please file a bug in Launchpad (that's a really important step, you'll be helping future users like you're helped by others). After that, as a quick fix, you can add the application on the top panel (next to the Firefox, Mail and Help icons) by right clicking and choosing "add to panel">Custom Application Launcher.

There's also a menu editor for Gnome menus, but I can't remember it. But please, please, file a bug in Lauchpad so it can be sorted out for everybody.

---

### Post by minibeardeath on 2008-11-10
i have a gateway 142-xl tablet pc, and i had my tablet working with hardy (using 8.1.5 build), but when installed intrepid, the tablet stoped working. i have gone in and tried option b (editing the xorg.conf), but it has not worked even though i simply uncommented that exaect configuration from b4. i have not yet tried to run the tablet w/o the "autoadddevices" "false", and i will be trying that once i get out of class. also, i am 95% sure that the tablet input is still @ /dev/ttyS0.
edit: on my machine, the tablet input is either /dev/ttyS0 or /dev/input/wacom

---

### Post by Loïc2 on 2008-11-10
> **minibeardeath said:**
> i have a gateway 142-xl tablet pc, and i had my tablet working with hardy (using 8.1.5 build), but when installed intrepid, the tablet stoped working. i have gone in and tried option b (editing the xorg.conf), but it has not worked even though i simply uncommented that exaect configuration from b4. i have not yet tried to run the tablet w/o the "autoadddevices" "false", and i will be trying that once i get out of class. 

Can you post your xorg.conf here? I think it's the little paperclip icon next to the smiley icon.
For now, possible candidates are:
- check you have uncommented ```
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
``` but if your previous xorg.conf was similar then you already have it;
- checking the ServerLayout section;
- remove /usr/share/hal/fdi/policy/20thirdparty/10-wacom.fdi and haven't a custom wacom.fdi in /etc/hal/fdi/policy ;
- try with /dev/input/wacom instead of /dev/ttys0
- try with or without the "AutoAddDevices" "false" option in the ServerFlags section.
```
Section "ServerFlags"
        Option "AutoAddDevices" "False"
EndSection
```
But usually you shouldn't need it.

Then you might be suffering from a bug in the 0.8.1.4 wacom drivers in Intrepid, so if the above doesn't work try to reinstall the drivers by downloading them from the Linux Wacom Project site. There's a link on the wiki that details how to do that, but I didn't try it and an user on a bug report had problems after installing the binaries (first method) so it's not 100% guaranteed to work. You could also compile them and install them, there again many people that try this method in the Forums have troubles too.

0.8.1.6 might get into Intrepid through some updates, which would make it simpler. Whaterver you do make sure to backup your xorg.conf and note what commands you can type to reinstall the drivers if X doesn't load.
```
sudo apt-get purge xserver-xorg-input-wacom wacom-tools
sudo apt-get install xserver-xorg-input-wacom wacom-tools
```

> **minibeardeath said:**
> edit: on my machine, the tablet input is either /dev/ttyS0 or /dev/input/wacom
 Thanks. We can maybe keep /dev/ttyS0 on the guide for the moment, since the example working xorg.conf for TabletPC I saw on Launchpad were also using it, but in the long term if other TabletPC users report /dev/input/wacom is also created for them it would make the example line simpler (no change between serial and USB).

---

### Post by Loïc2 on 2008-11-10
> **mesilliac said:**
> Anyway, the linuxwacom drivers come with precompiled binaries so all you need to do is:

 * double click the linuxwacom-0.8.1-6.tar.bz2 file and extract it to your desktop (you can delete these later)
 * open a terminal (Accessories > Terminal)
 * type the following:
 ```

cd Desktop/linuxwacom-0.8.1-6/prebuilt
sudo ./uninstall
sudo ./install

```


I got a post at [https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/295292/comments/3](https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/295292/comments/3) where the user say you need to add the --prefix=/usr option to configure "otherwise the updated driver is installed in /usr/local and isn't used".

mesilliac, since I never used this method, could you check if the option is needed so we could correct the wiki if needed?

The user also report some crashes after that, but he also encountered some with an Intrepid not updated (then the crash was solved, and reapeared after installing the 0.8.1.6 wacom drivers).

---

### Post by mesilliac on 2008-11-11
--prefix/usr is **not** necessary. The X driver is put in the correct place regardless.

The prebuilt scripts don't take command line options anyway.

---

### Post by Loïc2 on 2008-11-11
mesilliac, thanks for your quick reply. The user might have tried to compile it.
I've seen this line on some howtos:
```
./configure --enable-wacom --prefix=/usr
```
instead of just ./configure. Maybe it's the problem?

minibeardeath, you can try with mesilliac's method at [https://help.ubuntu.com/community/Wacom/LatestDriver](https://help.ubuntu.com/community/Wacom/LatestDriver) (Using the Pre-built binaries).

---

### Post by mesilliac on 2008-11-11
With ./configure too, the X driver goes in the right place. It's just the tools such as wacomcpl, xidump etc that get put in /usr/local. I'll add it to the configure line, to be consistent with the ubuntu package, but leaving it out won't cause problems with the driver.

--enable-wacom enables building of the kernel module, which usually isn't necessary. I'll add a line explaining this.

---

### Post by Loïc2 on 2008-11-11
Thank you. Hopefully it can help clarify the different contradicting information people get on the forums (not just Ubuntu forums) ;)

---

### Post by Xfcn on 2008-11-13
So the more I'm playing with this, the more I'm seeing that GIMP 2.6.1 isn't registering the PRESSURE at all, JUST the velocity. That bums me out. I use the pressure more than the velocity. Should I just go ahead and do the old-school XORG.conf work-around or what?

*EDIT* Upon looking, GIMP doesn't even list the tablet in the Extended Input Devices. I'm going to sac hot-swap ability for, you know, a properly functioning tablet.

*EDIT 2* Okay, simple enough. I edited xorg.conf and put in all the wacom fiddly bits and it shows up in GIMP 2.6.1 as "Wacom Bamboo" just fine, now. No muss. No fuss. Hot-swapping still works.

Here's what I did:

First, like any good Linux user, I made a wacom directory, then created a backup of my xorg.conf file in that directory in case I did Very Bad Things to my xserver.
```
mkdir wacom
cd wacom
sudo cp /etc/X11/xorg.conf .
sudo gedit /etc/X11/xorg.conf
```

Then, I edited the xorg.conf file. Added the following after Section "Screen" obtained from [Wacom Troubleshooting Help](https://help.ubuntu.com/community/WacomTroubleshooting):

```
Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/input/wacom" # USB ONLY?
#  Option        "Device"        "/dev/ttyS0"      # SERIAL ONLY
  Option        "Type"          "stylus"
#  Option        "ForceDevice"   "ISDV4"           # Tablet PC ONLY
  Option        "USB"           "on"               # USB ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/input/wacom" # USB ONLY?
#  Option        "Device"        "/dev/ttyS0"      # SERIAL ONLY
  Option        "Type"          "eraser"
#  Option        "ForceDevice"   "ISDV4"           # Tablet PC ONLY
  Option        "USB"           "on"               # USB ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/input/wacom" # USB ONLY?
#  Option        "Device"        "/dev/ttyS0"      # SERIAL ONLY
  Option        "Type"          "cursor"
#  Option        "ForceDevice"   "ISDV4"           # Tablet PC ONLY
  Option        "USB"           "on"               # USB ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "pad"
  Option        "Device"        "/dev/input/wacom"    # USB ONLY
#  Option        "Device"        "/dev/ttyS0"         # SERIAL ONLY
  Option        "Type"          "pad"
  Option        "USB"           "on"                  # USB ONLY
EndSection

```

Save, quit gEdit. CTRL+ALT+Backspace to reboot xserver et VOILA. GIMP now recognizes tablet with pressure AND velocity and hot-swapping still works. Bonus. Took like two minutes and it works for me. Your results may vary.

Also I'm using the included version of the wacom drivers, which is 0.8.1.4-0ubuntu3.

---

### Post by Loïc2 on 2008-11-13
Happy to know it works for you now ;)

Your xorg.conf extract is perfect, except it lacks the "ServerLayout" part...

---

### Post by Xfcn on 2008-11-13
Xorg doesn't seem to care terribly much about having it there, for whatever reason. I'll add it a bit later and let you know if it's all still working.

---

### Post by Malvazar on 2008-11-15
Ummm... Okay this is weird. I upgraded to 8,10 today and did the hole ordeal and ever thing you know, but my graphire 2 is only partly  working! My pen works fine but when I try to use my mouse it doesn't even recognize that I have it one the tablet. need some help?:confused:

---

### Post by Loïc2 on 2008-11-16
> **Malvazar said:**
> Ummm... Okay this is weird. I upgraded to 8,10 today and did the hole ordeal and ever thing you know, but my graphire 2 is only partly  working! My pen works fine but when I try to use my mouse it doesn't even recognize that I have it one the tablet. need some help?:confused:

That's hardly enough information.

Did you edit /etc/X11/xorg.conf, and can you attach it here?
"and ever thing you know" : for a Graphire 2, AFAIK, that's just editing the xorg.conf, nothing else. If you did something else, that may be the cause of the problem.

---

### Post by mesilliac on 2008-11-16
I've been playing around with tablet settings, hotplugging, HAL, xorg.conf, and I found some things out:

You can configure your tablet using both the default (HAL/.fdi) way, and through xorg.conf at the same time.

For xorg.conf setup to be recognised the tablet must be connected / plugged in / turned on when you log in.

If you hotplug your tablet after this, it will connect (stylus only) and work as in Option A.

With xorg.conf configured also, you can now do the old trick of switching to another virtual terminal and back: CTRL-ALT-F6 then CTRL-ALT-F7. This gives you the usual tablet functionality provided via Option B.

In this way, disabling "AutoAddDevices" in xorg.conf is definitely not needed. Furthermore, configuring via xorg.conf does not remove hotplug functionality.

I'd heard a couple reports to this effect, but what was going on was a little confusing. I hope this helps to clarify a bit.

---

### Post by brandon88tube on 2008-11-16
It would be nice if hotplugging worked for the mouse on the tablet. Yes, I use it lol :D

---

### Post by ace214 on 2008-11-17
I don't have a Wacom, but I have messed around with trying to configure my Finepoint for my tablet PC with the hal method before I read that it wouldn't work.

I'm not sure how the person above was able to not add a server layout section to his xorg.conf, but I would like to know. Since installing Intrepid, whenever I add the server layout to my xorg.conf, it gives me occasional flickering and color lines during use and always on shutdown. Sometimes shutdown even hangs.

Here's my xorg...
```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "InputDevice"
	Identifier	"Tablet"
	Driver		"fpit"
	Option		"Device"		"/dev/ttyS0"
	Option		"InvertY"
	Option		"MaximumXPosition"	"12550"
	Option		"MaximumYPosition"	"7650"
	Option		"MinimumXPosition"	"400"
	Option		"MinimumYPosition"	"400"
	Option		"SendCoreEvents"	"True"
	Option		"TrackRandR"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice 	"Tablet"
EndSection
```

For whatever reason, adding that server layout and putting the default screen in seems to mess with my video driver.

I'm using a Gateway cx2619.

---

### Post by gnocci on 2008-11-17
Just to tip off, used the option B (edited the x.org), in Intrepid with a Wacom Bamboo Fun, and worked perfectly. Pad, buttons, pen/eraser and pressure work. Don't have the mouse, so don't know about that. Won't hotplug (to be sure, deleted the wacom.fdi :))
Tested in GIMP and Inkscape.

---

### Post by minibeardeath on 2008-11-17
here is my xorg.conf (for the gateway c-142xl w/ serial tablet)
```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

# commented out by update-manager, HAL is now used
#Section "InputDevice"
#	Identifier	"Generic Keyboard"
#	Driver		"kbd"
#	Option		"XkbRules"	"xorg"
#	Option		"XkbModel"	"pc105"
#	Option		"XkbLayout"	"us"
#EndSection

# commented out by update-manager, HAL is now used
#Section "InputDevice"
#	Identifier	"Configured Mouse"
#	Driver		"mouse"
#	Option		"CorePointer"
#EndSection

# commented out by update-manager, HAL is now used
Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/input/ttyS0"   # SERIAL ONLY
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Serial Tablet PC ONLY
EndSection

# commented out by update-manager, HAL is now used
Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/input/ttyS0"          # SERIAL ONLY
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Serial Tablet PC ONLY
EndSection


# commented out by update-manager, HAL is now used
#Section "InputDevice"
#	Identifier	"Synaptics Touchpad"
#	Driver		"synaptics"
#	Option		"SendCoreEvents"	"true"
#	Option		"Device"	"/dev/psaux"
#	Option		"Protocol"	"auto-dev"
#	Option		"HorizEdgeScroll"	"0"
#EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"fglrx"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
# commented out by update-manager, HAL is now used
#	Inputdevice	"Synaptics Touchpad"
# commented out by update-manager, HAL is now used
	Inputdevice	"stylus"	"SendCoreEvents"
# commented out by update-manager, HAL is now used
	Inputdevice	"cursor"	"SendCoreEvents"
EndSection

Section "Module"
	Load		"glx"
EndSection

#Section "ServerFlags"
#	Option	"AutoAddDevices"	"False"
#EndSection
```

also, here is the method that i used to intsall wacom in hardy, and i think that this is why my tablet input is referenced to both /dev/ttyS0 and /dve/input/wacom.
[http://ubuntuforums.org/showthread.php?t=765915]("http://ubuntuforums.org/showthread.php?t=765915")

this week[end] when i get some time, i may do a clean reinstall (i only use linux for a backup partition/messing around) and i will report how that goes with the tablet. also, does anyone know if the tablets work in the 64-bit ubuntu?

---

### Post by Loïc2 on 2008-11-17
It does. No Adobe programmers where hurt during the production of the linuxwacom driver.

---

### Post by Loïc2 on 2008-11-17
> **ace214 said:**
> I don't have a Wacom, but I have messed around with trying to configure my Finepoint for my tablet PC with the hal method before I read that it wouldn't work.

I'm not sure how the person above was able to not add a server layout section to his xorg.conf, but I would like to know. Since installing Intrepid, whenever I add the server layout to my xorg.conf, it gives me occasional flickering and color lines during use and always on shutdown. Sometimes shutdown even hangs.

(Edited)

For whatever reason, adding that server layout and putting the default screen in seems to mess with my video driver.

I'm using a Gateway cx2619.

I don't know the fpit at all. For the ServerLayout section, it shouldn't create any problem, especially if you did a clean install of Intrepid.

You might have more chance creating a specific thread for your model of Tablet PC, of for the device type (fpit?).

You can also check with a previous working xorg.cong in Hardy, and if you never installed Hardy on it, even better, go for a Gutsy or Feisty install and check what a working xorg.conf file looks like in these previous versions of Ubuntu.

---

### Post by ace214 on 2008-11-17
> **Loïc2 said:**
> You can also check with a previous working xorg.cong in Hardy, and if you never installed Hardy on it, even better, go for a Gutsy or Feisty install and check what a working xorg.conf file looks like in these previous versions of Ubuntu.
Well, when I updated to Intrepid from Hardy before doing a clean install, it did the same thing. The tablet stuff was essentially the same.

---

### Post by Loïc2 on 2008-11-17
So with the same xorg.conf as in Hardy, you now have fickering and colored lines, whereas it was working flawlessly in Hardy?

If that's the case, you should open a bug in Launchpad (while still opening a thread in the forums if you want to get help) because it's a regression (put the tag "regression" in your bug report). Don't forget to attach the xorg.conf from Hardy if you still have it, and the relevant files for Intrepid.

To simplfy the process of collecting the files, don't open the bug yourself. Instead, create a launchpad account, then in a terminal in Intrepid, run the command:
```
ubuntu-bug xorg
```

---

### Post by daviebasite on 2008-11-26
Hi,
I'm trying to switch the function of the pen buttons on my graphire4 in ubuntu8.10 interpid without a success.
According to the guide I made a file in usr/share/hal/policy/wacom.fdi with this content: 
```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

<deviceinfo version="0.2">

  <device>
    <match key="info.capabilities" contains="input">
      <match key="info.product" contains="Wacom">
	<merge key="input.x11_driver" type="string">wacom</merge>
	<merge key="input.x11_options.Type" type="string">stylus</merge>
	<merge key="input.x11_options.Button2" type="string">button 3</merge>
	<merge key="input.x11_options.Button3" type="string">button 2</merge>
      </match>
  </device>

</deviceinfo>
```
but there is no difference at all, I tried different button numbers but the buttons still have their default functions. I tried even restart not only unplug/plug the device.
Can somebody help me?

---

### Post by mesilliac on 2008-11-26
Hi daviebasite,

Can you try without the extra "button" in the option string? i.e.:

```

  <merge key="input.x11_options.Button2" type="string">3</merge>
  <merge key="input.x11_options.Button3" type="string">2</merge>

```

---

### Post by daviebasite on 2008-11-26
> **mesilliac said:**
> Hi daviebasite,

Can you try without the extra "button" in the option string? i.e.:

```

  <merge key="input.x11_options.Button2" type="string">3</merge>
  <merge key="input.x11_options.Button3" type="string">2</merge>

```

Thanks for taking attention :) I tried your suggestion but still there's no difference.
 I made one test..
 I deleted 10-tabletPCs.fdi and 20-wacom.fdi files and also cleaned the tablet setting from xorg.conf. After reboot the tablet is working still by the same way with all extras, that makes me think that the tablet takes it's settings from somewhere else? Is this possible?
Currently I use only this wacom.fdi file in the ./policy folder with the above settings, but maybe it doesn't matter.

---

### Post by mesilliac on 2008-11-26
I'm a little confused by the file locations you're listing..

The main fdi file that configures the tablet on hotplug should be at

/usr/share/hal/fdi/policy/20thirdparty/10-wacom.fdi

If you make an additional custom fdi file it should be placed in

/etc/hal/fdi/policy/

Can you confirm these file locations?

---

### Post by Loïc2 on 2008-11-27
You can try to find it with the brute force way:
cd /
sudo find | grep .fdi > /tmp/fdi

Then open the resulting file and see if you find anything that could look like a wacom fdi file (you could also do sudo find | grep wacom.fdi , but you might have given your file another name).

Alternatively you could just configure it in xorg.conf and be done with (that way you can use the pad and the eraser). The fdi method is only useful if for whatever reason you don't want to plug your tablet at boot. If you can keep it plug, or just plug it at boot and then suspend, even unplugging it then plugging it again would be ok.

The guide for .fdi was made when we wrongly assumed it would be the future configuration file for wacom tablets, but since it won't be used after Intrepid (you'll still be able to use it if you prefer, but that won't be the default method) the .fdi method isn't so relevant anymore (for wacom tablets at least).

---

### Post by interknighterrant on 2008-11-28
Why this took me so long is beyond my comprehension... but I finally got my Toshiba R25-S3513 tablet PC working.  What gets me is that the solution was EXACTLY what was put before, it just took a while for me to get working.

Here is the problem I was having (note: past tense, problem solved just being added for future reference).  I would edit the xorg.conf file for my tablet PC, save the file, and then restart.  X apparently had a fatal problem with the file because, after restarting, it just showed a command line.  I had copied a backup of the default xorg.conf, so I just typed in my "sudo cp /etc/X11/xorg.conf.default /etc/X11/xorg.conf" then "sudo reboot" and after the restart it signed me back into Ubuntu no problems.

So, I go back, read through the wiki and some of the posts, try (from scratch) to edit my xorg.conf.  Long story short(er), I did this 3 or 4 times.

The ONLY thing I did different this time around was I didn't restart.  Not sure if I was just making typos the first half a dozen times, but just (AFTER SAVING ALL YOUR WORK) pressing ctrl+alt+backspace seemed to work best for me.  Picked up my stylus, eraser, etc without any problems.  For a split second, I thought it was going to have me use the command line again, but it showed the graphic login screen and I was a happy, happy man.
Here is my current xorg.conf file, in all it's functional glory (I spared you all the common, commented-out header stuff).

```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

# Retropad (classic NES controller converted into a USB controller)
Section "InputDevice"
	Identifier	"RetroPad 1"
	Driver		"joystick"
	Option		"Device"		"/dev/input/js0"
	Option		"DebugLevel"		"0"
	Option		"StartKeysEnabled"	"True"
	Option		"StartMouseEnabled"	"True"
	Option		"MapButton1"		"button=1"
	Option		"MapButton2"		"button=2"
	Option		"MapButton3"		"button=3"
	Option		"MapButton4"		"button=4"
	Option		"MapAxis1"		"mode=relative	axis=+1x	deadzone=5000"
	Option		"MapAxis2"		"mode=relative	axis=+1y	deadzone=5000"
EndSection

#wacom tablet attempt
Section "InputDevice"
	Identifier	"stylus"
	Driver		"wacom"
	Option		"Device"		"/dev/ttyS0"
	Option		"Type"			"stylus"
	Option		"ForceDevice"		"ISDV4"
EndSection

Section "InputDevice"
	Identifier	"eraser"
	Driver		"wacom"
	Option		"Device"		"/dev/ttyS0"
	Option		"Type"			"eraser"
	Option		"ForceDevice"		"ISDV4"
EndSection

Section "InputDevice"
	Identifier	"cursor"
	Driver		"wacom"
	Option		"Device"		"/dev/ttyS0"
	Option		"Type"			"cursor"
	Option		"ForceDevice"		"ISDV4"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice 	"stylus"		"SendCoreEvents"
	InputDevice 	"eraser"		"SendCoreEvents"
	InputDevice 	"cursor"		"SendCoreEvents"
EndSection
```

I just wanted to give a huge THANK YOU for everyone on this thread and who work on the wiki for giving me the information I needed to get this working again.  This works SO MUCH better than in Hardy for me.

Oh, and maybe I should have removed the retropad part of my xorg.conf file, but for anyone who buys that Retrozone retropad (classic NES controller that has been converted to a USB controller) it might be nice if google tags this post anyway, since I had to experiment a bit before getting this thing to work for me. [/rant] thanks again all.

---

### Post by daviebasite on 2008-11-28
> **mesilliac said:**
> I'm a little confused by the file locations you're listing..

The main fdi file that configures the tablet on hotplug should be at

/usr/share/hal/fdi/policy/20thirdparty/10-wacom.fdi

If you make an additional custom fdi file it should be placed in

/etc/hal/fdi/policy/

Can you confirm these file locations?

Thanks for that clearance :)
Somehow I've missed this in the guide, now when I added the lines for the buttons in the 
/etc/hal/fdi/policy/custom_wacom.fdi
everything work as expected :)
Thanks again!

---

### Post by Loïc2 on 2008-11-29
> **interknighterrant said:**
> Oh, and maybe I should have removed the retropad part of my xorg.conf file, but for anyone who buys that Retrozone retropad (classic NES controller that has been converted to a USB controller) it might be nice if google tags this post anyway, since I had to experiment a bit before getting this thing to work for me. [/rant] thanks again all.

That's nice. I'm sure it would be piked up by Google if you created a wiki page, for example at [https://help.ubuntu.com/community/RetrozoneRetropad](https://help.ubuntu.com/community/RetrozoneRetropad) - while there's not much chance it would be found in this thread ;)

Then we can add it to [https://help.ubuntu.com/community/InputDevices](https://help.ubuntu.com/community/InputDevices) (just need to create a Gamepad section).

If you want a model, click Edit on any wiki page you want to imitate the layout, then paste it in the page you want to create, and just replace the paragraphs you want to replace. Ask us if you need some help with the wiki.

---

### Post by tennisaddict on 2008-12-04
I just went through the "make stylus work" on my m275 process.  Essentially, I copied and pasted 123marra's xorg.conf and pasted it over mine.  The problem i'm having is that my trackpad's verticle scroll doesn't work anymore and also, I can't grab the scrollbar by double-clicking to drag it down.  I'm xubuntu and an m275.  This is really annoying, thanks for the help.

---

### Post by Loïc2 on 2008-12-06
tennisaddict, I don't know trackpads a lot, but could you please your whole xorg.conf (just attach it) so one can have a look? Hopefully you can also post the xorg.conf that was working before doing some modifications.

Alternatively, after you've backed up your xorg.conf, unplugged any external screen, and made sure you've got a live CD handy or another Linux install on the hard drive, you can do :
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Which will revert your xorg.cong to your original configuration (you'll lose the wacom configuration, but you can try again after you've recovered your trackpad).

---

### Post by edb66083 on 2008-12-08
I'm having trouble getting the stylus to work on a Compaq TC1000 Tablet. I followed all the instructions here and on the community pages, but am getting a complete blowup when I hit the CTRL-ALT-BKSPACE keys.

Here is my xorg.conf file:

```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/ttyS0"      # SERIAL ONLY
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"           # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/ttyS0"      # SERIAL ONLY
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"           # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/ttyS0"      # SERIAL ONLY
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"           # Tablet PC ONLY
EndSection

Section "ServerLayout"
  Identifier    "Default Layout"
  Screen        "Default Screen"
  InputDevice   "stylus"  "SendCoreEvents"
  InputDevice   "eraser"  "SendCoreEvents"
  InputDevice   "cursor"  "SendCoreEvents" # For non-LCD tablets only
EndSection
```

When I hit the CTRL-ALT-BKSPACE keys, it restarts and gives me an error box saying it is running low-resolution graphics and cannot restart. It then gives me some options to fix the graphics problem. If I push through without changing the graphics, I get a screen that I can't read.

Any help would be greatly appreciated.

---

### Post by Loïc2 on 2008-12-09
With a TabletPC, you shouldn't have a "cursor" section so just comment (add a # at the beginning of the lines) the "cursor" section and the "cursor" line in "ServerLayout".

If your stylus doesn't have an eraser at the back, do the same for "eraser".

I'm assuming your original xorg.conf was only including the sections "Device", 
"Monitor" and "Screen" (and not "ServerLayout"), please correct me if I'm wrong, and that you didn't change anything to these sections.

Fist try with the modifications suggested above. Then if it doesn't work just comment anything after the "Screen" section and try uncommenting the ServerLayout section while commenting everything inside except the lines Identifier and Screen.

When you get errors, try choosing the "repair" or "troubleshoot" options, I can't remember the names, but there's a way to see the logs. Try checking error messages in those (or attach - don't copy paste - the file /var/log/Xorg.0.log).

If you know Linux a bit, you can also go to a console (CTRL-ALT-F1, use CTRL-ALT-F7 to go back to X), stop gdm ( sudo /etc/init.d/gdm stop , or sudo killall gdm if you enjoy it) then start X with the startx command and you'll see the error messages in the console (that's how I found out xorg.conf need the Identifier and Screen lines in the  "ServerLayout" section, even though there's nothing in a default Intrepid xorg.conf).

---

### Post by edb66083 on 2008-12-09
Thanks for your fast reply, Loic2.

Okay, I tried what you suggested. BTW, your assumptions about the original xorg.conf file is correct.

I'm still getting errors, but was able to Troubleshoot and archive the xorg.0.log file. Here it is (it's not too long, so I'll just cut and paste):

```

X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux linux-tablet 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:20 UTC 2008 i586
Build Date: 24 October 2008  08:00:16AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Dec  9 20:01:43 2008
(==) Using config file: "/etc/X11/xorg.conf"
Parse error on line 64 of section ServerLayout in file /etc/X11/xorg.conf
	Unexpected EOF. Missing EndSection keyword?
(EE) Problem parsing the config file
(EE) Error parsing the config file

Fatal server error:
no screens found
(WW) xf86CloseConsole: KDSETMODE failed: Bad file descriptor
(WW) xf86CloseConsole: VT_GETMODE failed: Bad file descriptor
(WW) xf86OpenConsole: VT_GETSTATE failed: Bad file descriptor

```

Unexpected EOF. End of File? Missing EndSection? Line 64 (I think) is the EndSection line. I don't understand. Am I missing some more code?

Also, I don't know if it matters or not, but I am running Xubuntu 8.10, not Ubuntu, on this tablet.

Any ideas?

---

### Post by Loïc2 on 2008-12-10
edb66083, if you open your xorg.conf with a text editor, you'll see that line 64 is the line with 2 # just before the EndSection line. If you just plain remove this line, it should work (or try the xorg.conf I attached to this post, where I removed all the lines you don't need.

---

### Post by edb66083 on 2008-12-10
Yes, that's another step. Thank you Loic2.

I just copied your file as my new xorg.conf file, hit CTRL-ALT-BKSPACE, and it restarted without any errors. Yeah!

However, my stylus is still not working. I will try to attach the latest xorg.0.log for review. I'm thinking it's either some additional configuration or maybe something with hal?

Loic2, if you wouldn't mind looking over the attachment, I would appreciate it. Hopefully, it will be something obvious.

---

### Post by Loïc2 on 2008-12-11
edb66083, I was going to suggest you try /dev/ttyS2 instead of /dev/ttyS0, or check if /dev/input/wacom (or /dev/wacom) is created, and use that instead, but I first googled for you model of tablet "Compaq TC1000 Tablet wacom linux" and got this thread :
[http://osdir.com/mllinux.drivers.wacom/2007-09/msg00020.html](http://osdir.com/mllinux.drivers.wacom/2007-09/msg00020.html) (last message for the thread)

It seems like your model doesn't use a Wacom digitizer but a FinePoint's.

I googled your tablet model and finepoint, and there's a few howto: [this one for Debian]("http://linux-tablet-pc.dhs.org/#Pen") and [this one for Fedora]("http://www.zacharywhitley.com/linux/installation/Compaq_TC-1000.php#hardware_configuration-pen")

Assuming some the modules went upstream (the howto are quite old) it's possible you won't need to compile anything, but just remove all personnal entries you made to your xorg.conf and instead add this section :

```
Section "InputDevice"
Identifier "TC1000 pen"
Driver "tc1k"
Option "AlwaysCore" "on"
Option "Device" "/dev/ttyS0"
Option "BaudRate" "19200"
Option "MaximumXPosition" "8600"
Option "MinimumXPosition" "154"
Option "MaximumYPosition" "6485"
Option "MinimumYPosition" "110"
Option "InvertY"
EndSection
```

Hope it works.

If you search "TC1000" in the forums, you'll end up with [this post]("http://ubuntuforums.org/showpost.php?p=2522525&postcount=1") that has an xorg.conf with the pen working, and even a configuration for landscape/portrait mode. Trying replacing your whole xorg.conf with it might not work, but if you save yours first and are confident you can revert the changes in the console, you might just do it once just to try (this xorg.conf has stuff that don't belong in xorg.conf anymore, but else the pen and screen setup should be ok, and else it's a reference if you want to go further).

Edit: I looked for "tc1k" in Synaptic, but got nothing - in order for your pen to work there should be an xserver-xorg-input-tc1k installed, but it seems like you'll have to compile it yourself. If you're keen on keeping the laptop, I'd suggest you also open a bug report in Launchpad and maybe just an email to the ubuntu-x mailing list to see if they could package the driver. Apparently most TC1000 users gave up and resold it to get another hw, maybe that's why there might not be any driver in the repositories... and if no TC1000 user steps up to the task of creating bug reports and following with that, there's nothing the distribution can do.

There's also a [howto for Ubuntu]("http://www.rainbowbreeze.it/images/rainbow_sync/works/installations/tc1000_linux/tc1000_install.txt"), it's two year old but should work - see the PEN CONFIG section.

---

### Post by edb66083 on 2008-12-11
Thanks so much again, Loic2, for your help.

Though it is disappointing news. I have gone to that 'debian' website before, but thought I'd try the wacom drivers, since they seem to be universal with the latest ubuntu. But if they won't work, at least I know that, and can just move on from there.

I will try going through the instructions on the 'debian' page again. I was having trouble with compiling the driver, and getting it to the right location (at least I think that was my problem). Which is most likely why you suggested opening up a bug report so that ubuntu-x could do this for me! I will look into reporting this to them.

I definitely would like to keep this tablet. I won't get the money back that I put into it, and right now it doesn't have a fully functional OS to fetch a decent price. I completely erased Win XP that was on it. Full speed ahead and damn the torpedos!

I am very new to Ubuntu and Linux. I just started this past summer with a successful install of Hardy, after a few trys, on a rebuilt desktop that's working great, wifi and all. Some of the commands and procedures are still unclear to me, though. But this has been a very good learning experience for me so far.

I will try to keep you updated on my progress.

---

### Post by amheuwr on 2008-12-13
I have read this thread from start to finish. Have tinkered with xorg.conf and fdi file all to no avail. Have reset the files  back to how they were with my Bamboo Fun working with only the stylus and pen buttons  available. 
What I would like to know is if anyone has managed to get all the buttons on the pad  as well as the pressure sensitivity settings working  correctly? Seem to have wasted half my life now just trying to get  the tablet to work normally  instead of doing something constructive like working on my photos. In Heron I at least had some of the buttons available.
Apologies if I have missed something in this or any linked thread. 
If someone has been successful in fully configuring their Bamboo, would it be possible to post their full xorg.conf or the fdi for me to try and work out what needs to be done.

---

### Post by Loïc2 on 2008-12-13
The Bamboo Fun should be trivial, and take much less of your life than it took me finding the information, then making the wiki guide in the first place and updating it for each release since Dapper.

If you read the guides (they're linked to in the first post) you'll notice that the fdi method only gives access to the stylus. As the guides state, you need to configure your /etc/X11/xorg.conf according to [https://help.ubuntu.com/community/WacomTroubleshooting](https://help.ubuntu.com/community/WacomTroubleshooting)

Since your tablet is USB (correct me if I'm wrong) you should just need to paste the lines in the guide without modifications (you could remove all the lines that start with # though), not forgetting the ServerLayout part.

Don't forget to make a copy of your xorg.conf fist, and to make sure you can copy it back in case X fails to start after the modifications. You could also just reuse your Ubuntu 8.04 xorg.conf.

Please take the time to read the guides carrefully first. If you encounter any trouble, you can post your xorg.conf as an attachment and we can have a look. Just remember to also follow the main guide first (installation of the packages), you want Option B in Intrepid.

Then you can configure your buttons with wacomcpl (start it from a terminal).

---

### Post by amheuwr on 2008-12-13
> **Loïc2 said:**
> The Bamboo Fun should be trivial, and take much less of your life than it took me finding the information, then making the wiki guide in the first place and updating it for each release since Dapper. I do appreciate the time you have taken to create the wiki. Thank You.

> **Loïc2 said:**
> If you read the guides (they're linked to in the first post) you'll notice that the fdi method only gives access to the stylus. As the guides state, you need to configure your /etc/X11/xorg.conf according to [https://help.ubuntu.com/community/WacomTroubleshooting](https://help.ubuntu.com/community/WacomTroubleshooting)I have read the guides several times and have just struggled to get the tablet to behave. Have yet again spent a few hours tonight trying to get the damned tablet to work.

> **Loïc2 said:**
> Since your tablet is USB (correct me if I'm wrong) you should just need to paste the lines in the guide without modifications (you could remove all the lines that start with # though), not forgetting the ServerLayout part.Yes, your are quite right, my tablet is a USB and I have have done all the copying and pasting again. After the odd trashed xorg.conf and subsequent visit to the command line to recover things I have set up so as HAL is ignored for the tablet. Things are getting clearer for me. My small brain is finally clicking and I am reading the instructions more carefully ;-)


> **Loïc2 said:**
> Then you can configure your buttons with wacomcpl (start it from a terminal).Now this is the interesting bit. Why have I not seen any references to wacomcpl before? Again, my inability to read the instructions possibly? Started it up as you suggested and have had a play. Can definitely see how the buttons are configured just need to understand each part and what maps where. Keep getting lots of error messages. Unknown device error messages are received and an example is shown below.Trying to configure the "PAD"
[I][COLOR="Blue"]'unknown device "pad" or it is currently a core device
unknown device "pad" or it is currently a core device
    while executing
"wacomxi::bindevent . $device <ButtonPress> """
    (procedure "updateDevice" line 12)
    invoked from within
"updateDevice"
    (command bound to event)'[/COLOR][/I]
I will  continue to meddle. Thanks again for the advice=D>

---

### Post by Loïc2 on 2008-12-13
> **amheuwr said:**
> Now this is the interesting bit. Why have I not seen any references to wacomcpl before? Again, my inability to read the instructions possibly?

It's in the guide. First paragraph under "Ubuntu 8.10 Intrepid Ibex". Maybe third paragraph from the top.
[INDENT][I]Ubuntu 8.10 (Intrepid Ibex)

With Ubuntu 8.10, the configuration tool wacomcpl comes with the wacom-tools package. However, it won't work in the default setup (Option A), but will works if you have configured your tablet using Option B.[/I][/INDENT]
It's true I could have included screenshots like I did for The Gimp and Inkscape, but anyone that has ever used wacomcpl would understand why I didn't. However, it does the job.

> **amheuwr said:**
> I will  continue to meddle. Thanks again for the advice=D>

Don't forget to post your xorg.conf. Without it, it's hard to understand the problems, could be a ServerLayout error but I really don't know. If your xorg.conf is perfect and you're using the wacom drivers that came with Ubuntu (and never tried installing them by hand on that system), then it's possibly a bug in the 0.8.4 drivers, and it would be good to know.

Also, for disabling HAL you could just follow [this tip in the guide]("https://help.ubuntu.com/community/WacomTroubleshooting#Disabling%20Input%20Hotplug%20Through%20HAL%20for%20Your%20Wacom%20Tablet") and also erase any custom fdi file you've put in /etc/hal/fdi/policy .

Don't forget to plug your USB tablet before boot (actually before Xorg starts, but better safe than sorry) that way it will never be picked up by HAL, even if you still keep the fdi files, assuming of course your wacom device is properly configured in xorg.conf.

---

### Post by amheuwr on 2008-12-14
> **Loïc2 said:**
> 
Don't forget to post your xorg.conf. Without it, it's hard to understand the problems, could be a ServerLayout error but I really don't know. If your xorg.conf is perfect and you're using the wacom drivers that came with Ubuntu (and never tried installing them by hand on that system), then it's possibly a bug in the 0.8.4 drivers, and it would be good to know.


I think everything is set up correctly, but still get the errors mentioned  in my previous post i.e. when using wacomcpl. There are no fdi  issues. HAL disabled for the tablet. Most recent drivers  for wacom present on my 8.10 set up. My xorg.conf is shown below. 
```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

# commented out by update-manager, HAL is now used
#Section "InputDevice"
#	Identifier	"Generic Keyboard"
#	Driver		"kbd"
#	Option		"CoreKeyboard"
#	Option		"XkbRules"	"xorg"
#	Option		"XkbModel"	"pc105"
#	Option		"XkbLayout"	"us"
#EndSection

# commented out by update-manager, HAL is now used
#Section "InputDevice"
#	Identifier	"Configured Mouse"
#	Driver		"mouse"
#	Option		"CorePointer"
#	Option		"Device"	"/dev/input/mice"
#	Option		"Protocol"	"ImPS/2"
#	Option		"ZAxisMapping"	"4 5"
#	Option		"Emulate3Buttons"	"true"
#EndSection

# commented out by update-manager, HAL is now used
Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"	
	Option        "PressCurve"    "50,0,100,50"         # Custom preference
	Option        "Threshold"     "60"                  # sensetivity to do a "click"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

# commented out by update-manager, HAL is now used
Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

# commented out by update-manager, HAL is now used
Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

# commented out by update-manager, HAL is now used
Section "InputDevice"
	Driver		"wacom"
	Identifier	"pad"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"pad"
	Option		"USB"		"on"
EndSection

Section "Device"
	Identifier	"nVidia Corporation NV31 [GeForce FX 5600XT]"
	Boardname	"NVIDIA GeForce FX (generic)"
	Busid		"PCI:3:0:0"
	Driver		"nvidia"
	Screen	0
	Vendorname	"NVIDIA"
EndSection

Section "Monitor"
	Identifier	"LL-T17A4-B"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1400x1050@75" 155.85 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV31 [GeForce FX 5600XT]"
	Monitor		"LL-T17A4-B"
	Defaultdepth	24
	SubSection "Display"
		Virtual	1280	960
		Modes		"1152x864@75"	"1280x1024@75"	"1024x768@60"	"1280x960@60"	"1024x768@70"	"1280x1024@60"	"1024x768@75"	"1280x960@75"	"832x624@75"	"1400x1050@60"	"800x600@60"	"1400x1050@75"	"800x600@75"	"1600x1200@65"	"800x600@72"	"1600x1200@60"	"800x600@56"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
# commented out by update-manager, HAL is now used
#	Inputdevice	"Generic Keyboard"
# commented out by update-manager, HAL is now used
#	Inputdevice	"Configured Mouse"
	
	
# commented out by update-manager, HAL is now used
	InputDevice     "stylus"	"SendCoreEvents"
# commented out by update-manager, HAL is now used
	InputDevice     "cursor"	"SendCoreEvents"
# commented out by update-manager, HAL is now used
	InputDevice     "eraser"	"SendCoreEvents"
# commented out by update-manager, HAL is now used
	InputDevice	"pad"
EndSection
Section "Module"
	Load		"glx"
	Load		"v4l"
EndSection
Section "device" #   
	Identifier	"device1"
	Boardname	"NVIDIA GeForce FX (generic)"
	Busid		"PCI:3:0:0"
	Driver		"nvidia"
	Screen	1
	Vendorname	"NVIDIA"
EndSection
Section "screen" #   
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Modes		"640x480@60"	"640x480@72"	"640x480@75"	"800x600@56"	"800x600@72"	"800x600@75"	"800x600@60"	"832x624@75"	"1024x768@75"	"1024x768@70"	"1024x768@60"	"1152x864@75"	"1280x1024@75"	"1280x960@60"	"1280x1024@60"	"1280x960@75"	"1400x1050@60"	"1400x1050@75"	"1600x1200@65"	"1600x1200@60"
	EndSubSection
EndSection
Section "monitor" #   
	Identifier	"monitor1"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1400x1050@75" 155.85 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection
```

---

### Post by Loïc2 on 2008-12-15
Your xorg.conf shows that you upgraded to Ubuntu 8.10 - I had assumed it was an install from scratch. While in a perfect world upgrading should lead to the same results, it can also lead to some minor troubles - and since each configuration, user installed programs and modifications are different, it isn't possible to always get the same results as an installation from scratch.

Although your wacom configuration looks ok, your xorg.conf has also become quite messy - you can safely remove the commented lines for clarity, and maybe add a blank line between the EndSection and Section (second part of your xorg.conf. You also seem to have two screens plugged in - which means trying to regenerate your xorg.conf with "sudo dpkg-reconfigure -phigh xserver-xorg" can lead to real trouble (no X and no console mode...) - else it would have been a good idea to start from a new, clean xorg.conf.

Two things:
- you didn't really confirm what your problem is now - do you still have no eraser and no wacom mouse? Do some of the pad buttons work?
The error messages from wacomcpl are strange (I might have had similar errors when I was using the .fdi method), but on the other hand a program can output some error message while functionning normally. Wacomcpl pad buttons configuration is really messy, even with a perfect xorg.conf, so unless you describe your problem it's hard to guess.

- if you've got 5Go free space on your harddrive, you can try installing Ubuntu 8.10 from scratch in a new partitions (while keeping the one you already have) then configure your xorg.conf (try with just one screen plugged it at first) and see if it still doesn't work.

---

### Post by amheuwr on 2008-12-15
Thanks for the input. I now have things working OK. It is a matter of fiddling around with wacomcpl. I agree that my xorg.conf was a bit messy and have now tidied it up. Things looking good. Must admit to being a bit of a fiddler which doesn't make for a stable system, but hey, it is the only way to learn.

---

### Post by Loïc2 on 2008-12-18
I've just backported i386 and amd64 0.8.6 packages (from Jaunty) for Intrepid, they are on the [[COLOR="DarkRed"]Community wiki documentation[/COLOR]]("https://help.ubuntu.com/community/Wacom") along with install instructions.

I've tested them on amd64 and they work OK. Remember you still have to edit your xorg.conf properly ;)

Please test them and report if they work for you at [https://bugs.launchpad.net/intrepid-backports/+bug/309531](https://bugs.launchpad.net/intrepid-backports/+bug/309531) so they can be included in the -backport repositories.

---

### Post by chisayne on 2008-12-20
OK with the help of the guides and reading through other posts I've managed to get my Wacom tablet working, mouse and all. The only problem is the Back/Forward side buttons on the mouse don't seem to take the settings I'm giving them. Basically I want them to be back/forward in Firefox (Alt+left and Alt+right respectively). I've tried with both wacomcpl and xsetwacom to set Button5 to alt+left and Button4 to alt+right, but they end up for some reason sending alt+4 and alt+6 (firefox jumps to the 4th tab when I press the left button, 6th tab when I press the right). Anyone have any ideas that might help?

running ubuntu 8.10, wacom driver 0.8.1.4 (version packaged with intrepid)

Code I am using to set the keystrokes:
```
xsetwacom set cursor button4 "key core alt right"
xsetwacom set cursor button5 "key core alt left"
```

Any help would be greatly appreciated.

---

### Post by Loïc2 on 2008-12-20
chisayne, that doesn't have much to do with the wacom driver ;)

alt-right doesn't do anything in Firefox. Alt-NumpadRight does...

I don't know the exact terms to use in xorg to specify a right or left numpad button, but I think that's the reason for the problem - try to look for information on keyboard shortcuts. At the moment your shortcut are interpreted as the numers 4 and 6 on the numpad (you could also try deactivating the numpad before using the mouse buttons and see if that changes anything).

You could also simply assign different shortcuts to back/forward in Firefox (but then that's something Firefox experts will know better).

---

### Post by chisayne on 2008-12-20
Oy I feel like a total noob now. I didn't even think about numpad when I was trying to figure out the correlation between left/4 and right/6. As soon as I read that on your post I realized the problem - numlock. Turned off numlock, it works just as it should. However I use my numpad all the time so it looks like we're assigning new shortcuts in firefox, once I figure that one out. 

Thanks!

---

### Post by tazbo28 on 2008-12-21
ok so i believe i have installed the drivers, which were in the linuxwacom file i got 0.8.2. 

i did this is the terminal and it seemed to go through an install process. the only now is that my tablet doesnt do anything still. 

i modified my xorg.conf file to look like the one posted on page 1 of the thread, using the gksudo command. i changed the device to reflect my com1 port as well (my tablet is an Intuos 1 Serial type) to ttys0. still i get nothing upon reboot. i feel so lost now, not sure what to do. i was trying to follow the steps on the linux wacom project guide to get into wacdump as well, and everytime i type the command into my terminal it returns...

"root@vince-desktop:~# ./wacdump
bash: ./wacdump: No such file or directory"

whether i am root or not. same thing every time. ? ??????

im stuck, and i would really love to get my tablet working tonight if possible. thanks in advance.

---

### Post by Loïc2 on 2008-12-21
The error means wacdump isn't in the path. Just try
```
wacdump
```

Wacdump should be installed with the default Ubuntu wacom-tool packages.

Also, with the model of tablet you have, what was the point of installing 0.8.2 instead of the default wacom-tools and xserver-xorg-input-wacom in Intrepid? Your tablet isn't a brand new model, and with Intuos3-based having had perfect support for ages (even with Ubuntu default packages), I suppose yours (far older) would too...

Have a try with wacdump, if you still don't have it uninstall 0.8.2, reinstall the default packages in Ubuntu and make sure to plug your tablet before starting the computer.

Then you can also have a look in /dev/input/ or /dev/ and see if you have a wacom entry created (then you can use /dev/input/wacom or /dev/wacom in your xorg.conf instead of /dev/ttyS0 - I think there's an uppercase S anyway). You can also look in /dev/input/by-id/

Then you have to configure your xorg.conf **seriously**. The xorg.conf in first page is for **TabletPC**, it won't work for you Intuos1 at all. If you read the first post of the thread, or if you just read the guide, you'll see they point to a page with example xorg.conf lines for wacom devices.

If you have difficulties, you can Attach (not copy/paste) your xorg.conf here, but it's better if you try configuring it the right way first.

---

### Post by tazbo28 on 2008-12-21
SOOOO AWSOME---finally got it. ok well i typed in just wacdump in a new terminal. now the data screen/program thingy is running. it shows all the detailed info about the tablet live as i use it. and everything seems to be working even the side buttons.

now...how do i actually go about using the device? my xorg.conf file is actually back to default the way it was before i modified it. so do i modify it now?  if so should i follow the parameters on the linuxwacom guide. thnks.

---

### Post by Loïc2 on 2008-12-21
The answer is in my post just above yours ;)

---

### Post by tazbo28 on 2008-12-21
ok so i looked in the file -dev/input and the other one and i found nothing for the wacom tablet. so im assuming that i must make my entry ttyS0 then? 

other than that i tried to change the xorg.conf file to something similar to the attached below and got a graphics error that said something about parsing before it loaded ubuntu and asked to reconfigure the graphics in order to restart. so i did, still no tablet operation however. 

is my xorg file wrong? 


```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerFlags"
        Option 		"AutoAddDevices" "False"
EndSection

Section "InputDevice"
  	Driver          "wacom"
  	Identifier      "stylus"
  	Option          "Device"        "/dev/ttyS0"
  	Option          "Type"          "stylus"
EndSection

Section "InputDevice"
  	Driver          "wacom"
  	Identifier      "eraser"
  	Option          "Device"        "/dev/ttyS0"
  	Option          "Type"          "eraser"
EndSection

Section "InputDevice"
  	Driver          "wacom"
  	Identifier      "cursor"
  	Option          "Device"        "/dev/ttyS0"
  	Option          "Type"          "cursor"
EndSection

Section "ServerLayout"
  	Identifier      "Default Layout"
  	Screen          "Default Screen"
  	InputDevice     "stylus"  	"SendCoreEvents"
  	InputDevice     "eraser"  	"SendCoreEvents"
  	InputDevice     "cursor"  	"SendCoreEvents"
EndSection
```

---

### Post by tazbo28 on 2008-12-21
nevermind. im retarded. i must have been entering it wrong, cause now it works with the code i placed in the above post. i restarded. the tablet is actually really quite accurate. i dont think ill be making any changes or modifications to the xorg file anymore. until i check it out in Gimp i guess. but pretty much everything seems to be working great. 

also, can i delete the linuxwacom folders on my desktop now?

---

### Post by Loïc2 on 2008-12-21
Yes.

You can also safely remove the section:
```
Section "ServerFlags"
        Option 		"AutoAddDevices" "False"
EndSection
```

Which isn't necessary and might cause trouble with other stuff.

---

### Post by MGaddict2000 on 2008-12-22
Okay, I'm a noob at Ubuntu, this is my first full install of linux on a system, its a Gateway M275 with Hardy installed because 8.10 won't even boot up on the CD for any M275 users, but thats a different issue.

I've followed everything I can find haven't even found other M275 users w/ this problem so mabey I screwed something up someplace. I got the stylus working even in Gimp. Pressure works fine, I'm almost there. But the Right click button on my stylus does nothing. It was working fine when I had WinXP on this laptop so I doubt its the stylus. I tryed running wacomcpl and got this...

wacomcpl: using TCLLIBPATH="[list  /usr/local/lib ]"
Error in startup script: Data incomplete in file /etc/X11/xorg.conf
	Device section "Configured Video Device" must have a Driver line.
Problem when parsing config file
    while executing
"exec xsetwacom list"
    (procedure "createDeviceList" line 4)
    invoked from within
"createDeviceList "
    (procedure "createControls" line 8)
    invoked from within
"createControls"
    (file "/usr/local/bin/wacomcpl-exec" line 1835)

Here is my xorg.conf.....

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Identifier    "stylus"
	Driver        "wacom"
	Option        "Device"        "/dev/ttyS1"      # SERIAL ONLY
	Option        "Type"          "stylus"
	Option        "ForceDevice"   "ISDV4"           # Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier    "eraser"
	Driver        "wacom"
	Option        "Device"        "/dev/ttyS1"      # SERIAL ONLY
	Option        "Type"          "eraser"
	Option        "ForceDevice"   "ISDV4"           # Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier    "pad"
	Driver        "wacom"
	Option        "Device"        "/dev/ttyS1"         # SERIAL ONLY
	Option        "Type"          "pad"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
	InputDevice	"stylus"  "SendCoreEvents"
	InputDevice	"eraser"  "SendCoreEvents"
	InputDevice	"pad"                      # For Intuos3/CintiqV5/Graphire4/Bamboo tablets
EndSection

Any suggestions? I do know a lot of them had trouble with the screen rotation and keyboard keys but I haven't even tried to touch one of them till I think its safe. I don't get much free time to mess w/ this so it might be a day or so before I respond, but a suggestion would be appreciated.

---

### Post by Favux on 2008-12-22
Hi MGaddict2000,

Hopefully Loic2 or mesilliac will get to you soon.  In the mean time maybe try adding something like:
```
Option "Button2" "3" # make side-switch a right button
```

To here:
```
Section "InputDevice"
Identifier "stylus"
Driver "wacom"
Option "Device" "/dev/ttyS1" # SERIAL ONLY
Option "Type" "stylus"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
Option "Button2" "3" # make side-switch a right button
EndSection
```

It might be worth a shot.

---

### Post by Loïc2 on 2008-12-22
MGaddict2000, I'm not a stylus button expert because the first thing i do with a Wacom pen is remove all the rubber coating + side buttons so I don't have the feeling I'm trying to draw with a log ;)

wacomcpl errors are because default xorg.conf in Hardy (and later) don't configure much. If you really want to remove the error message, you can try generating your xorg with an nvidia/ati configuration tool (i don't know if Intel has the same) if you've got a card like that.

However, you're not saying if wacomcpl starts or not - error messages aren't always a problem, and if you're not clear we can assume anything.

"exec xsetwacom list" just kills the terminal here. Maybe "xsetwacom list dev"?

All aside, you should definitely try Favux idea. BTW, do you have an eraser at the back of your pen, and some pad buttons?

---

### Post by MGaddict2000 on 2008-12-22
Well the button thing now works, thanks a bunch for that. But wacomcpl still does not. That error is all I get then it goes back to prompt. I wacomcpl to calibrate my stylus which badly needs calibrating. I have an integrated intel video chip, but I'm curious, I see the same "default grapgics" on most peoples xorg.conf w/o a driver listed and I've not heard of them having problems. I"ll look into it though, Thanks.

---

### Post by Favux on 2008-12-22
Hi again MGaddict2000,

Now that I've thought about it, it seems to me I remember some people were having trouble with a bug in wacom-tools?  Touching stylus to screen froze it?  Something like that.  Maybe you're having the same, similar problem?  I can't remember which version, but it was pretty recent.  I am sure that it was fixed by linuxwacom 0.8.2 (their latest).  Maybe I read it on the Linux Wacom Project site?

Might be worth looking into.

---

### Post by Loïc2 on 2008-12-22
That bug shouldn't have anything to do with wacomcpl. I'm not even sure wacomcpl has been updated for quite a while.

MGaddict2000, did you try just adding the Driver line in your xorg.conf?
The section :
```
Section "Device"
Identifier "Configured Video Device"
EndSection
```

Could be modified like :
```
Section "Device"
    Identifier     "Configured Video Device"
    Driver         "xxx"
EndSection
```

Where xxx is the name of your driver.

By the way, the xorg.conf you pasted doesn't look like a default one (even without the wacom lines), since the lines aren't all aligned on the left by default.

---

### Post by Favux on 2008-12-22
Hi Loïc2,

You're probably right about the bug.  On the LWP site they say wacomcpl is updated in 0.8.2 with new features.  I have 0.8.2 installed, and frankly I can't see any difference in wacomcpl.

---

### Post by MGaddict2000 on 2008-12-23
I tried going to the linux-wacom project site and looked at it, does anybody have a precompiled version for Hardy? Folling the instructions to compile those drivers may be my next step, I'd just like to avoid that if at all possible. This tablet PC isn't new at all so I doubt they will make that much of a difference. From everything I've read, the only problem those fix is the lock up issue when you touch the screen, I'm not having that problem at all. Whats odd is There is a thread here...

[http://ubuntuforums.org/showthread.php?t=984634&highlight=M275]("http://ubuntuforums.org/showthread.php?t=984634&highlight=M275")

This guy didn't seem to have the same problem I'm having although I'm also having the same issues he is with a lot of it but he was able to use wacomcpl to configure everything. Is there a way to completely uninstall all the wacom drivers and reinstall them? I tried going into the package manager and having that reinstall them but it made no difference.

---

### Post by goggle5 on 2008-12-23
Having trouble with getting my tablet configured in Hardy ... I have a Graphire CTE-440.  I can move around and navigate BUT there is no pressure or sensitivity.  GIMP 'sees' it, but when looking under the Input Controllers it states: Device not available - Permission Denied

When I run ./configure --enable-wacom    
_I get the following (I am running under su):_

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.


_Here's part of the  config.log file:_



Any ideas/suggestions ???  I have not changed my xorg.conf file yet, because everytime I do, it seems to knock my Nividia settings out of whack.   I just want to see if I can get this figured out before I post that ...

---

### Post by MGaddict2000 on 2008-12-23
Alright, so I searched around and found just adding the line device "intel" to my xorg.conf gets rid of the errors when running wacomcpl, but wacomcpl pops up, select device has nothing listed and the only other thing in the window is Exit. I would include a screen shot but I don't think its needed. I know my pen is working because I've been using it. I just want to be able to orientate it because its really off.
Another problem I have is when I rotate the screen, the pen doesn't rotate, I think I found a site with a solution to the rotation thing so I'm going to try it tonight.
[http://luke.no-ip.org/x60tablet/#disk]("http://luke.no-ip.org/x60tablet/#disk")

---

### Post by Loïc2 on 2008-12-23
goggle5, there's no point updating your wacom drivers if you don't edit your xorg.conf.

You need to get your wacom devices configured, then if you've got some bugs but you know you have configured your xorg.conf well then there's a reason to try new drivers.

New drivers won't do anything either unless you configure your tablet. See the guide (links in first post) and the links from the guide to configuring your xorg.conf.

Then if you also need to update your drivers you can follow the link on installing them (try using the prebuilt binaries first). If you check, you'll see the line you use to install them isn't exactly right. But as I said it's not going to magically work unless you edit your xorg.conf. If you're afraid to mess up your configuration, make a copy from a console (CTRL-ALT-F1 then CTRL-ALT-F7 to come back to X) first and read the guide carefully before.

---

### Post by Loïc2 on 2008-12-23
MGaddict2000, for your question about precompiled binaries for Hardy the guide already has the answer (a link to a page explaining how to install prebuilt binaries or compiling the drivers).

Could you also answers the questions from last page, about your eraser/pad and your xorg.conf? Thanks.

---

### Post by MGaddict2000 on 2008-12-23
well, one, I'm not sure what the 'pad' device is. I thought it was necessary to make the rotate and keyboard buttons on my screen operate. If thats not what its refering to I"ll go ahead and remove it. As far as the eraser goes, I was told by Gateway, I could get a stylus with an eraser and it would work on this tablet, but since my stylus doesn't have one, I went ahead and commented that out. No use in fooling with something I don't have right now.
To give you a complete update, I went to another thread which had very straight foreward directions on compiling the new drivers for people with a bamboo tablet. I followed those which got me the newest drivers and a little farther on wacomcpl. BTW, if you read my post I left earlier, about two up from this one, I added a line to my xorg.conf file and my results are posted above. I couldn't find an intel cinfig util and it was not easy digging through all the crap out there, but I did get that far. Well, that combined with the new compiled drivers, get me to wacomcpl opening w/o errors, listing my pad and stylus. I click on stylus and then I can configure the buttons. But when I goto calibrate, I get this...

> unknown device "stylus" or it is currently a core device
unknown device "stylus" or it is currently a core device
    while executing
"wacomxi::bindevent .topleft.m $device <ButtonRelease>  {calibrationSequence 0 %0 %1}"
    (procedure "startCalibration" line 20)
    invoked from within
"startCalibration"
    (procedure "Calibration" line 22)
    invoked from within
"Calibration"
    invoked from within
".panel.calibrate invoke"
    ("uplevel" body line 1)
    invoked from within
"uplevel #0 [list $w invoke]"
    (procedure "tk::ButtonUp" line 22)
    invoked from within
"tk::ButtonUp .panel.calibrate"
    (command bound to event)

the two boxes pop up to calibrate but clicking on them does nothing. I'm getting closer, I'm just guessing its one little thing I'm missing someplace.

Once I get wacomcpl working I can continue on in the setting up screen rotations and such. Sounds like I may have to pick between rotating the screen or having compiz. but once again, got to fix this problem first, and no turning off compiz makes no difference towards this problem.

---

### Post by joshmuffin on 2008-12-23
Hey thanks for the tut it was really helpful.
Does anyone know if there is a program or script that will automate this process? Maybe even a .deb. Also does anyone know if support for wacom's will be included in the next release (jaunty jackalope)?

---

### Post by goggle5 on 2008-12-23
Thanks Loic2 on your input ... I had the tablet kind of working a few weeks back, but then I did a reinstall of Ubuntu and I cannot get it to take.  Now when I update my xorg.conf file with the Wacom sections it seems to mess with the Nividia settings??  all I get is an orange screen with no icons/taskbar/etc. and I have to reboot into terminal and restore my backup xorg file.  Any ideas/suggestions????

---

### Post by Loïc2 on 2008-12-23
@All: please do not paste your whole xorg.conf or large chunks of it, attach them instead. Same goes for error message. It's harder for the one that wants to help, and for those that will come after you it only inflates the thread so much that they won't want to read the whole thread before asking. For short extract, don't forget the # ("code") icon.

@MGaddict2000, google5 : could you please edit your previous posts and attach the files (and the error messages in the case of google5) instead? Nothing against you, but the 3 last pages have gotten a bit out of hand ;)
Also, please note xorg.conf has indentation for clarity - the contents of each section is a bit (3 to 6 spaces, but keep the same amount) to the right. It's like maths - you can solve a problem with really bad writting, but if you're stuck on an error you can't find you'll be better of rewriting it cleanly if you want the solution to appear.

google5:
SSection "ServerLayout" > Section "ServerLayout"
Also, why do you use Option "ForceDevice" when you obviously don't have a TabletPC (unless your "Graphire" is something different than a Wacom Graphire)? Pad don't use "SendCoreEvents" either. Was that really in the example lines on the wiki?

MGaddict2000:
I don't have any idea at the moment. However, even though you'll have to find the values by trial and error, you can use these commands in a script or on the command line (wacomcpl uses that method), they apply on the fly (keep a mouse at hand or your trackpad though ;) )

```
xsetwacom set stylus bottomy "33114"
xsetwacom set stylus bottomx "52653"
xsetwacom set stylus topy "490"
xsetwacom set stylus topx "313"
```

That's for a tablet with a bigger input resolution than yours (mine is Intus3 technology, yours should be half the resolution). Change the 4 numbers until you get whatever fits your TabletPC (it's never "perfect", even on windows, since there's a few layers between the screen cover and the Wacom capturing device).

---

### Post by goggle5 on 2008-12-23
Sorry about that ... I'm new to all of this

This link has the "SendCoreEvents" example that I followed:
[https://help.ubuntu.com/community/WacomTroubleshooting]("https://help.ubuntu.com/community/WacomTroubleshooting")

---

### Post by Loïc2 on 2008-12-23
That's ok. Thanks for editing your post. it's far easier to look at your xorg.conf that way.

The "SendCoreEvents" isn't for the "pad" line if you look carefully on the page you linked to. If you can find it in the page, please correct me because that would be a mistake.

You would also most probably want to use /dev/input/wacom instead of /dev/input/event0 (that's already in the page you linked at - again I'm not sure where you got event0). Your tablet will not always be at event0, it could be another event# (which makes it even harder for you to see what the problem is).

I've edited your xorg.conf with the modifications, see below.

---

### Post by goggle5 on 2008-12-23
Thanks for updating my xorg file ... 

I have updated my file and my system is taking it with no startup problems!

I am still getting this message when trying to run 
./configure --enable-wacom

"checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details."

I attached my config.log in a previous post ... any ideas or suggestions???

---

### Post by Loïc2 on 2008-12-23
goggle5, you tried compiling the drivers and installing by hand without even having a valid xorg.conf first. See [http://ubuntuforums.org/showpost.php?p=6422506&postcount=83](http://ubuntuforums.org/showpost.php?p=6422506&postcount=83)

- did you try  using the default wacom drivers in Ubuntu now your xorg.conf should be ok? See [https://help.ubuntu.com/community/Wacom/LatestDriver](https://help.ubuntu.com/community/Wacom/LatestDriver) but the link was in the guide.
- next step, if you're sure Ubuntu wacom drivers don't work for you with a valid xorg.conf, is installing the prebuilt binaries (see above link)
- if it still doesn't work, you can install with compilation first - see above link again, your command like isn't exactly what's advised.

---

### Post by goggle5 on 2008-12-23
I *finally* got my tablet working!!!!  

So I guess I kind of did everything in the incorrect order?

Thanks for all your help!!!

---

### Post by Loïc2 on 2008-12-23
Indeed, most people love to do things in reverse order when it comes to wacom drivers. Maybe comes from the idea that Linux couldn't be as simple as not requiring fidling with compiling everything from scratch. At least that's what I was telling you after your first post.

Well, you didn' think about recompiling your kernel though ;)

---

### Post by MGaddict2000 on 2008-12-24
Is there a way to display my current stylus calibration settings, it might make it a lot easer to adjust off that? and incase you still want to see it, here is my current xorg.conf I also commented out the 'pad' just incase that was the issue, but now the brightnes button on my screen doesn't work, so I'm guessing I was right about it controlling those buttons. I will usually disable everything that could cause a problem while I'm troubleshooting.

---

### Post by Favux on 2008-12-24
Hi again MGaddict2000,

You are no longer getting an error message when you run wacomcpl?  But in wacomcpl there is no "stylus" to click on (other options then appear)?  This sounds like wacom isn't detecting any input.  If this is the case, then since all you have is the stylus, maybe it is running through HAL?  I think fdi can handle the right button too (but it wasn't before, was it).  Do you even need xorg.conf?  Hmmm.  Let's see what you get with:
```
dmesg | grep Wacom
ls -l /dev/input/by-path
   &
lsmod
modinfo -d wacom
```
After calibrating with wacomcpl your settings should be stored in a .xinitrc file that you can then start with Sessions so it's available with each boot.  In terminal you type:
```
chmod +x ~/.xinitrc
```
Then go to System->Preferences->Session click on add and for the command write "~/.xinitrc" (without the quotes); this will work only for the user.  You can see ".xinitrc" in /home/user name but remember in View to select Show Hidden Files.

Rotation of the sylus etc. will only work if you tell X what's happened, see the scripts at:
[http://ubuntuforums.org/showthread.php?t=996830]("http://ubuntuforums.org/showthread.php?t=996830")

To further illustrate what I'm talking about I'll attach my xorg.conf and .xinitrc  .

---

### Post by MGaddict2000 on 2008-12-25
okay, I"m guessing this is in response to an earlier posting of mine. I've updated in post #85 what my current scenario is. If you read that you can see where I currently am. The stylus does show up now but when I click calibrate I get the error message Thats in that post. Also I am using Hardy. I got it to start working at all by updating my xorg.conf. But yes, the error messages that I got before wacomcpl even started has gone away by putting a driver "intel" in my xorg.conf. You can see my current xorg.conf in post #95. 

As far as the commands you have listed I have attached the results in a txt file.

That last one concerns me. "No such device" I figure that could be a problem. But could it also be caused by something else I had done? I don't know. My pen is still working. I just want to properly calibrate it. It doesn't go to the edges of the screen which makes it hard to do things like move scroll bars, slide objects to the next desktop, etc. I"m going to look into the link you gave me about the screen rotation though. Thanks.

---

### Post by Favux on 2008-12-25
Hi MGaddict2000,

Sorry, typo. It should have been dmesg.  Could you convert that output to an attachment? Loic2 will not be happy with that.  My suspicion was/is that you do not have a functioning Wacom module in the kernel.  Try the dmesg command above.  If no Wacom, try it after fresh boot.  If still no wacom you need to reinstall it.  How exactly did you install it, if you remember?

Edit:  From the output you do not have a Wacom kernel module; this is why xorg.conf, wacomcpl, etc. is not working right for you.  In dmesg, lsmod, or mod info you should have seen "wacom", it is not called "linuxwacom".  Still same question, how did you install the wacom stuff?

Again you could just stay with HAL, since your stylus is functioning, though it won't give you eraser.  Again I don't know about side buttons.  But there are custom fdi files for it that Loic2's wiki's have examples of.  I don't know if HAL does rotation, but you could try Tom Jaeger's wacomrotate daemon on my rotation HOW TO.

---

### Post by Roberto.Maurizzi on 2008-12-29
Abount Cintiq 12WX:
I think it should be useful to note somewhere in the official wiki that the Cintiq 12WX does NOT work under ubuntu 8.04 (and previous versions I'd say...) since the kernel driver doesn't support the USB ID of this Cintiq model.

The process to have it working should be similar to the one explained for the Bamboo, but I don't know for sure since I choose to update to Intrepix :-)

---

### Post by savanik on 2009-01-03
Hey guys,

I'm using a Gateway M275 with Ubuntu 8.10 and I managed to get the tablet working properly by doing the following:

1. Downloading the sources from The Linux Wacom project
2. Compiling the module to their specifications
3. Copying the files over from their build directory into my module directory (the install script did NOT work for some reason)
4. Editing xorg.conf by hand.

A few quick notes:
The precompiled version that came with the Linux Wacom download didn't work. Compile it from scratch. Instructions are on their site, including how to set up the build environment.

Don't know why the install script didn't work. As near as I can tell, it should have - had to go through it to find the proper directory to drop it into.

By far, the most painful part was editing xorg.conf. With 8.10, you literally have to add _everything_ back in, with the proper arguments. I don't know how many times I had to redo the 'Screen' section before my laptop would accept it. Attaching it for other people - you'll have to rename it to xorg.conf if you want to use it directly.

savanik

---

### Post by Favux on 2009-01-03
Hi savanik,

Good work!  Thanks for posting your xorg.conf.  You're not the only one with compiling problems.  Us TX2000 and TX2500 folks have been using:

[http://ubuntuforums.org/showthread.php?p=5469447#post5469447]("http://ubuntuforums.org/showthread.php?p=5469447#post5469447")

Now substituting 0.8.2 for 0.8.1-6.  Loic2's been trying to make that unecessary.

At his kernel install wiki:

[https://help.ubuntu.com/community/Wacom/LatestDriver]("https://help.ubuntu.com/community/Wacom/LatestDriver")

Did you try his note 2?  Where he tells you to try:
```
./configure --enable-wacom --prefix=/usr
```

I'm interested in your rotation script.  Do you have bezel buttons on your screen?  Do you pick up a keycode with xev?  If you do you could bind rotation to a bezel button.  Putting the launcher on a panel or in a dock would mean only a single click for rotation.

---

### Post by AlmightyMole on 2009-01-10
Hello, I appear to have no luck with my HP Pavilion tx2000. This is after following the [community docs]("https://help.ubuntu.com/community/Wacom/") on the subject, including compiling the 0.8.2-1 driver from [http://prdownloads.sourceforge.net/linuxwacom/linuxwacom-0.8.2-1.tar.bz2]("http://prdownloads.sourceforge.net/linuxwacom/linuxwacom-0.8.2-1.tar.bz2"). But still not a sausage.

lsusb gives ```
Bus 002 Device 006: ID 056a:0093 Wacom Co., Ltd
```
however nothing appears at /dev/input/wacom and wacomcpl appears to be rather blank. And Xorg.0.log entries seem to say that that the Xorg entries on the docs a load of tosh also. 

It all works smashingly in Vista and any assistance to get tablet working in Ubuntu would be much appreciated (Mainly because Ubuntu doesn't burn rather delicate areas when using it on my lap).

---

### Post by Favux on 2009-01-10
Hi AlmightyMole,

First step is getting you an xorg.conf.  Go to:

[http://ubuntuforums.org/showthread.php?t=996830]("http://ubuntuforums.org/showthread.php?t=996830")

At the bottom of the HOW TO is a TX2000 xorg.conf.  Be sure to back yours up first.  If you compare it to yours you will see quite a bit of difference.  The TX2000 is a USB Wacom tablet.  You do not need serial tablet entries.

Then we can deal with your linuxwacom driver problem.  What happens if you:
```
sudo su modprobe wacom
```
close your X session, reopen X (or just reboot) and then enter:
```
lsmod | grep wacom
```
?

---

### Post by AlmightyMole on 2009-01-10
I used the 
```
sudo su modprobe wacom
``` gave me 
```

mole@mole-laptop:~$ sudo su modprobe wacom
[sudo] password for mole: 
Unknown id: modprobe

```
And after resetting the X server:
```
mole@mole-laptop:~$ lsmod | grep wacom
wacom                  29824  0 
usbcore               175888  8 wacom,isp1760,uvcvideo,btusb,usbhid,ohci_hcd,ehci_hcd

```

At least the extra entries from that xorg.conf attached to the post you linked to now allows me to rotate the screen, thanks Favux.

---

### Post by Favux on 2009-01-10
Hi AlmightyMole,

Good that you have rotation.  Now we know that you do not have a linuxwacom kernel module present.  If you've exhausted Loic2's wacom wiki, and remember there is troubleshooting stuff there too, time to move on to gali98's tutorial.

Gali98 hasn't posted in a couple months.  So the linuxwacom driver version # is out of date.  Follow the tutorial exactly, read it carefully.  Copy and paste to terminal rather that type.  If you want substitute for 0.8.1-6 either 0.8.2 or the latest 0.8.2-1.  I know 0.8.2 works because I've done it.  The tutorial is at:

[http://ubuntuforums.org/showthread.php?p=5469447#post5469447]("http://ubuntuforums.org/showthread.php?p=5469447#post5469447")

Good luck!

---

### Post by AlmightyMole on 2009-01-11
Is all working now, murky beer cups for you assistance, I will have a look at that script you posted to rotate the screen on the correct events, so thanks again.

---

### Post by riesengreen on 2009-01-14
First of all, THANK YOU to everyone who has made it possible to use tablets with Ubuntu! I hope that at least a few of you read this.

I just paired my Bluetooth Graphire with my laptop, and have not configured settings in Gimp, Inkscape, etc., yet. I did not reconfigure xorg.conf, but rather just used the default setup in Intrepid.

Second, a question. Are there plans to make the tablet function as it does in Windows, where the tablet surface is mapped to the screen, and when you touch the tablet the cursor jumps to the corresponding position? Or should it be doing this now?

And last, thanks again!

---

### Post by crparis on 2009-01-16
Good day, all!

I haven't used Linux in years (I think it's been over a decade--gasp!) but recently installed Ubuntu on my home PC.  I dusted off my old skills and with just a bit of reading was able to get everything running.

I've got the module loaded and the tablet is working, but I have a strange calibration setting I can't figure out.  Specifically, the tablet only engages when the pen actually makes contact with the pad, so I am unable to move the cursor around without actually applying pressure and "clicking".  The eraser end of the stylus doesn't have this problem, and both have the same options for setting the default pressure.

I am using an old Art2 Serial working via a USB-based Serial adapter.

Thanks in advance for any tips!

--Clinton

---

### Post by Loïc2 on 2009-01-23
> **riesengreen said:**
> Second, a question. Are there plans to make the tablet function as it does in Windows, where the tablet surface is mapped to the screen, and when you touch the tablet the cursor jumps to the corresponding position? Or should it be doing this now?

The two settings exist in Linux two, what you're looking for is to set the tablet in Absolute mode (which is usually the default mode). Sometimes, you can also be confused by the fact that the graphic program you're using also allow the input to be set in Windows mode or in Screen more (you'll want Screen mode).

If you don't want to edit your xorg.conf, you'll have to follow the guide for editing the .fdi file (but copy it to /etc/hal/fdi/policy and edit it there) and add the option.

---

### Post by Loïc2 on 2009-01-23
> **crparis said:**
> Specifically, the tablet only engages when the pen actually makes contact with the pad, so I am unable to move the cursor around without actually applying pressure and "clicking".  The eraser end of the stylus doesn't have this problem, and both have the same options for setting the default pressure.

I am using an old Art2 Serial working via a USB-based Serial adapter

I don't know much about Serial tablet plugged in USB via an adapter. You can attach (not paste) your xorg.conf here, but I don't really think it's the problem.

The solution might be to download the latest stable drivers from the Linux Wacom Project (0.8.2.2), install them (binary or by compiling them), including maybe the kernel module, and see if it help, then if it doesn't ask your question in the linuxwacom-discuss mailing list, where somebody would have probably already faced this situation.

---

### Post by RoseKnight on 2009-01-26
> **Loïc2 said:**
> 
In Ubuntu 9.04, the distribution will probably revert to using xorg.conf to set up wacom devices, since the HAL method used in Ubuntu 8.10 doesn't allow anything more than the stylus, and even that doesn't work for TabletPC, serial tablets, and users who need to calibrate the stylus.


I'd like to state that it isn't HAL that prevents Ubuntu from using more than the Stylus. It is in fact the way the driver is set up and requires you to define a separate tablet for each device you use for the tablet.

In the HAL declaration for WACOM if you change "Stylus" to "Eraser" you now can only use the eraser instead of the stylus.

Please stop posting everywhere that this is Hal's fault for only recognizing one-single tablet connected to your PC.

(Sorry, I'm not certain as to how the computer detects the Tablet PC settings, but Hal will probably offer better support and hardware setting in the future as more work is done on it.)

---

### Post by albesan on 2009-01-28
hello team,

I finally got my mouse working following the instructions on the wiki. Thanks very much.

Now, something I can't figure out is how to set the mouse to be used by a left-handed user.

I have been looking through this thread, the wiki and searching elsewhere and came across methods using xmodmap and xinput:

[http://www.faqs.org/docs/Linux-HOWTO/Wacom-Tablet-HOWTO#_Toc465765724](http://www.faqs.org/docs/Linux-HOWTO/Wacom-Tablet-HOWTO#_Toc465765724)
(ancient page I know)

I have even installed the wacon tablet apps:

[http://alexmac.cc/tablet-apps/](http://alexmac.cc/tablet-apps/)

But it does not seem to work.

Everything else does, even the wheel scrolls the right way.
I am using the drivers available on synaptic, the latest ones on the wiki would not enable the wheel.

Apologies if this has already been discussed in the thread and/or I'm missing something really obvious.

thanks for any feedback


a.

Extra info:

Output of xmodmap -pp

albesan@copituxredux:~$ xmodmap -pp
There are 32 pointer buttons defined.

    Physical        Button
     Button          Code
        1              3
        2              2
        3              1
        4              4
        5              5
        6              6
        7              7
        8              8
        9              9
       10             10
       11             11
       12             12
       13             13
       14             14
       15             15
       16             16
       17             17
       18             18
       19             19
       20             20
       21             21
       22             22
       23             23
       24             24
       25             25
       26             26
       27             27
       28             28
       29             29
       30             30
       31             31
       32             32

The tablet is an old USB Wacom Graphire. Just a simple tablet with stylus and 3 buttoned mouse with wheel.

xorg.conf attached.

Thanks a lot

a.

---

### Post by emkeyen on 2009-01-29
I'm trying to make my Wacom Intuos 3 work on Ubuntu 8.10. I've followed the instructions on [https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom), installed packages and latest drivers from Linux Wacom Project, then edited xorg.conf as I need eraser and tablet buttons as well.

Entering GIMP preferences for Configure Extended Input Devices lists no stylus/tablet but "Macintosh mousebutton emulation", "Core Pointer" and "HID 04b9:048e" (mouse). Wacomcpl has just an empty list, nothing at all. I've tried to remove /usr/share/hal/fdi/policy/20thirdparty/10-wacom.fdi, which makes no difference either.

lsusb shows:
Bus 001 Device 069: ID 056a:00b1 Wacom Co., Ltd 
(where Device changes number after each hot plug)

more /proc/bus/input/devices shows:
I: Bus=0003 Vendor=056a Product=00b1 Version=0102
N: Name="Wacom Intuos3 6x8"
P: Phys=
S: Sysfs=/devices/pci0000:00/0000:00:02.0/usb1/1-2/1-2:1.0/input/input228
U: Uniq=
H: Handlers=mouse2 event5 js0 
B: EV=1f
B: KEY=18ff 0 1f00ff 0 0 0 0 0 0 0 0
B: REL=100
B: ABS=100 f00017f
B: MSC=1

ls /dev/input shows:
tablet-intuos3-6x8
wacom

Tried replacing wacom with tablet-intuos3-6x8 in /etc/X11/xorg.conf as well. No go. 

So. It seems to be there. Almost. Help is very much appreciated. I have no idea what to do next.

---

### Post by Loïc2 on 2009-01-29
> **RoseKnight said:**
> Please stop posting everywhere that this is Hal's fault for only recognizing one-single tablet connected to your PC.
First, I'm not really sure we have the same definition for ["everywhere"]("http://www.thefreedictionary.com/everywhere").

Second, I don't get what your problem is. The sentence you're quoting clearly says :
> the HAL method used in Ubuntu 8.10 doesn't allow anything more than the stylus
Indeed, the default method in Ubuntu 8.10 doesn't allow anything more than the stylus. For detailed explanation, please refer to the xorg and linuxwacom-devel/discuss mailing lists. For example, [[COLOR="Red"]here[/COLOR]]("http://lists.freedesktop.org/archives/xorg/2008-November/040233.html") are the opinion of two HAL developers:

> Daniel Stone wrote
On Thu, Nov 13, 2008 at 01:45:03PM +0100, Danny Kukawka wrote:
> Second: it's IMO the wrong way to use HAL as a config store for X at all. Yes, 
> there are ppl. saying: "Also other tools can use this information." but in 
> fact there are no other tools, except X, which need them. X should do this 
> task on it's own (maybe by using HAL or another tool to get some information 
> about a device to identify it).

As I've told you before, I agree with you that using HAL as a random and
arbitrary config store is wrong.  Most of it belongs in the kernel or
user-level configuration.  I'm not happy about the patch to add
arbitrary option passthrough to HAL/Xorg: I think it's generally the
wrong approach.

The information which I advocated storing was generally along the lines
of 'you can't really use this device without this information': things
like touchpad limits for Synaptics devices and so on, which can't be in
the kernel, but are required for the device to actually function in the
slightest.

> **RoseKnight said:**
> (Sorry, I'm not certain as to how the computer detects the Tablet PC settings, but Hal will probably offer better support and hardware setting in the future as more work is done on it.)
As for HAL being the method for the future, see HAL developer Danny Kukawka [[COLOR="Red"]here[/COLOR]]("http://sourceforge.net/mailarchive/message.php?msg_name=200811131345.05655.danny.kukawka%40web.de"):
> First: there are plans to replace HAL, which means it's to back the wrong 
horse since the current stuff need to replaced by another, not yet developed, 
tool to do the same like HAL. It need again adoptions in X and all the 
drivers which deliver currently some info via fdi files.

Now, even though the point of your post is still lost to me, there's parts I find even harder to understand:
> **RoseKnight said:**
> It is in fact the way the driver is set up and requires you to define a separate tablet for each device you use for the tablet.
The linuxwacom driver requires you to define each input device, where did you get the idea it requires defining a separate tablet for each input device?
As for needing to define each input device, how else could it know which input devices you're planing to use, since you can use multiple input devices with your tablet, and each has its own properties? As long as Xorg doesn't transmit to the driver the input devices and properties (which is not possible when Xorg relies on HAL for that), you don't get to use them.

> **RoseKnight said:**
> In the HAL declaration for WACOM if you change "Stylus" to "Eraser" you now can only use the eraser instead of the stylus.
What was exactly your point in stating the obvious?

---

### Post by Loïc2 on 2009-01-29
emkeyen, could you please attach (not copy/paste) your /etc/X11/xorg.conf in your post?
If you've only installed the packages in the repositories, deleted the .fdi file (no harm done) and modified xorg.conf, it should be trivial to get a working configuration, since Intuos 3 models have always been supported very well (I still have one).

albesan, we might need more information. Could you tell us the model of your tablet, attach your xorg.conf file, tell us the output of "xmodmap -pp", and if you're only using the Wacom mouse (no touchpad/USB or Serial mouse)? You can just edit your previous post if you want.

---

### Post by emkeyen on 2009-01-30
> **Loïc2 said:**
> emkeyen, could you please attach (not copy/paste) your /etc/X11/xorg.conf in your post?
If you've only installed the packages in the repositories, deleted the .fdi file (no harm done) and modified xorg.conf, it should be trivial to get a working configuration, since Intuos 3 models have always been supported very well (I still have one).


Here it is. Renamed copy txt. Commented out other stuff I tried with no luck. Missed something maybe?

---

### Post by RoseKnight on 2009-01-30
> **Loïc2 said:**
> 

The linuxwacom driver requires you to define each input device, where did you get the idea it requires defining a separate tablet for each input device?
As for needing to define each input device, how else could it know which input devices you're planing to use, since you can use multiple input devices with your tablet, and each has its own properties? As long as Xorg doesn't transmit to the driver the input devices and properties (which is not possible when Xorg relies on HAL for that), you don't get to use them.



Maybe I worded that wrong, The driver requires you to set-up a separate entry for each tool the tablet has. This in itself causes overlap errors in many systems.

If, for example, instead of the way the driver is now, It had entries like:

Section "InputDevice"
  Driver        "wacom"

  Tools Stylus "on"
  Tools Eraser "on"

EndSection


Instead of requiring multiple InputDevice entries Like the documentation portrays. [http://linuxwacom.sourceforge.net/index.php/howto/inputdev](http://linuxwacom.sourceforge.net/index.php/howto/inputdev)

Hal would be able to configure it no problem.

I'm not saying anything about Hal being the right way to do things, because I don't know. I do know that from what I see of the way X has to be set-up to use the driver from the LWProject.

Besides, by posting in this article and the community Wiki about the Ubuntu reverting back "probably" for jaunty, is you specifically taking a side against hal than trying to note the real problem.
Although it would be beneficial after when Jaunty is released without hal, that these documents are Noted: "Hal was removed for Jaunty"

---

### Post by Favux on 2009-01-30
Sorry, double post.

---

### Post by Favux on 2009-01-30
Hi RoseKnight,

I'm very sorry, I do not understand what point you're trying to make about HAL either.  If you're saying technically it could do what we tablet users need if the linuxwacom driver was different, OK.  The developers I was reading seemed unsure of that.  But anyway the point is moot.

David Zeuthen (a Fedora developer), who is a lead (if not the lead developer) on HAL has been planning to replace it with DeviceKit since at least May of 2008.  Please see:
[http://lists.freedesktop.org/archives/hal/2008-May/011560.html]("http://lists.freedesktop.org/archives/hal/2008-May/011560.html")
I think the plan was to have DeviceKit in Jaunty, but it doesn't look like it will make it.  But they'll start phasing it in.  Other links of interest:
[http://people.freedesktop.org/~david...dz-aug2008.pdf]("http://people.freedesktop.org/~david...dz-aug2008.pdf")
[http://lists.freedesktop.org/archive...hment-0001.pdf]("http://lists.freedesktop.org/archive...hment-0001.pdf")
I got all this from gnomeuser on a Jaunty thread:
[http://ubuntuforums.org/showthread.php?t=1042857]("http://ubuntuforums.org/showthread.php?t=1042857")

I hope this is helpful.

---

### Post by RoseKnight on 2009-01-31
> **Favux said:**
> 

I'm very sorry, I do not understand what point you're trying to make about HAL either.  If you're saying technically it could do what we tablet users need if the linuxwacom driver was different, OK.  The developers I was reading seemed unsure of that.  But anyway the point is moot.



correct sir.

Also, the driver seems to provoke overlap errors without hal.

---

### Post by Favux on 2009-01-31
Hi RoseKnight,

OK, now I understand.  From your perspective there is a problem/limitation with the LWP's linuxwacom driver/s.  Is it an architectural thing?

---

### Post by RoseKnight on 2009-01-31
I'm not quite sure about architectural, I never really got into driver coding.
But its interface is definitely a little off, and it is slightly erratic(albeit not as bad) in other systems that aren't hal. 
I've been thinking about writing to the author or posting in his mailing list, but I'm not quite sure how to phrase the message yet.

---

### Post by Loïc2 on 2009-01-31
> **RoseKnight said:**
> Besides, by posting in this article and the community Wiki about the Ubuntu reverting back "probably" for jaunty, is you specifically taking a side against hal than trying to note the real problem.
I went and asked people that would take the decisions. Nothing more. Since I got the answer from Ubuntu developers, Hal developers and developers from the Linux Wacom Project (please note that some HAL developers are also developers for the Linux Wacom drivers, which makes hard to understand your ideas about the linuxwacom drivers being at fault or needing to be modified).

I got those answers : the Ubuntu method in Intrepid to use HAL does not allow using multiple input devices for the wacom drivers, and Ubuntu developers would thus go back to the Xorg method (with the development of a graphical interface to enable Wacom devices in xorg.conf).

I fail to see where is the problem in me helping people in this thread, in the wiki, and stating the answers I got. If improving the .fdi HAL method would have been chosen for Jaunty, I'd have edited the wiki in consequence. Where am I taking sides?

If the butcher next door tells you he's not going to carry fish (and that he's not happy when people ask him to sell fish, or want to make him do so), and you kindly explain to others that this butcher isn't planning to carry fish, what is your reaction if somebody barges in and reproach you to take sides against the butcher?

> **RoseKnight said:**
> Although it would be beneficial after when Jaunty is released without hal, that these documents are Noted: "Hal was removed for Jaunty"

They won't, for the simple reason that HAL won't be removed from Jaunty. HAL was not created in order to configure Wacom devices, and the fact Jaunty will not allow configuration of more than one Wacom input device through HAL has no effect on other uses of HAL.

> **RoseKnight said:**
> I'm not saying anything about Hal being the right way to do things, because I don't know.
When you don't know what you're talking about, assuming people are wrong and telling them so is hardly the way to treat others.

If you're planning to fork HAL and continue maintaining it even though there's already plans to replace it, please go ahead. But this thread is not the place. The only point of you posting in this thread (instead of going to the right place, which in this case would be xorg mailing list or linuxwacom-devel) was telling me that I shouldn't say that Intrepid default method for configuring Wacom devices doesn't allow configuring more than one device, and that I shouldn't say that Ubuntu developers plans for Jaunty are to use the xorg.conf method again. I neither understand nor appreciate, for the reasons explained above. 

If you've got patches for HAL, linuxwacom drivers or Xorg, this thread isn't the place.

If you're ok with accusing people and reproaching them when the only thing they've done is researching their facts before speaking, please re-read the [Ubuntu code of conduct]("http://www.ubuntu.com/community/conduct") and the [Ubuntu Forums code of conduct]("http://ubuntuforums.org/index.php?page=policy").

**@albesan and emkeyen** Thanks for posting your xorg.conf. I've been busy addressing other matters than what I started this thread for, and since my time is limited it will probably take me a few days before I can find something useful. However, quick thoughs:
- both your xorg.conf looks ok, even if I'll have a better look afterwards.
- albesan, you might have a better chance asking in linuxwacom-discuss mailing list, it could be a bug in the linuxwacom drivers or not, but I've never used the Wacom mouse :p and don't know much about it. I'll have a look in the linuxwacom documentation else, but that will take a while. If you find the answer before, please tell us so we can also learn from it ;)

---

### Post by albesan on 2009-01-31
sure thing Loïc2, will have a look there and report back.

Thanks again.

a.

---

### Post by emkeyen on 2009-02-05
> **Loïc2 said:**
> 
**@albesan and emkeyen** Thanks for posting your xorg.conf. I've been busy addressing other matters than what I started this thread for, and since my time is limited it will probably take me a few days before I can find something useful. However, quick thoughs:
- both your xorg.conf looks ok, even if I'll have a better look afterwards.

Cheers. You have any idea what I can try to make it work?

Em.

---

### Post by EvanKroske on 2009-02-07
Sorry if this is a necro-bump, but I want my table to work! I have modified my xorg.conf several times, unplugged and replugged in my tablet, and I can still only get the stylus tip to be recognized. 

When I made this last change, the stylus tip stopped working and nothing started working. I unplugged the tablet and plugged it back in, and now, when I try to interact with the tablet, the blue light starts blinking in an unfamiliar pattern. If somebody can help me out, I'll really appreciate it.

---

### Post by phorgan1 on 2009-02-07
Thank you so much for this guide.  I'm using Ubuntu Ibex with a Bamboo Fun.  Everything works!!!  Thanks for the tip about flipping to a virtual terminal and back to get the eraser and pad to work without having to restart X.   The last thing I want to do is this.  xev shows that the wheel on the mouse and the input touch ring on the pad both generate mouse 4 and mouse 5 button events.  Comparing them to my logitech mouse I see the difference is that the logitech produces button press release events:
> ButtonPress event, serial 31, synthetic NO, window 0x4400001,
    root 0x7d, subw 0x0, time 12504098, (139,139), root:(146,189),
    state 0x0, button 4, same_screen YES

ButtonRelease event, serial 31, synthetic NO, window 0x4400001,
    root 0x7d, subw 0x0, time 12504098, (139,139), root:(146,189),
    state 0x800, button 4, same_screen YES

but the bamboo driver, for the mouse wheel is generating motion notify button release events. > MotionNotify event, serial 31, synthetic NO, window 0x4400001,
    root 0x7d, subw 0x0, time 12495696, (140,139), root:(147,189),
    state 0x0, is_hint 0, same_screen YES

ButtonRelease event, serial 31, synthetic NO, window 0x4400001,
    root 0x7d, subw 0x0, time 12495696, (140,139), root:(147,189),
    state 0x0, button 4, same_screen YES

bizarrely, the driver generates, for the input ring, a triplet of motion notify, button press for button 255, button release for button 4(or 5 depending on direction).
> MotionNotify event, serial 31, synthetic NO, window 0x4400001,
    root 0x7d, subw 0x0, time 13127000, (139,116), root:(146,166),
    state 0x0, is_hint 0, same_screen YES

ButtonPress event, serial 31, synthetic NO, window 0x4400001,
    root 0x7d, subw 0x0, time 13127176, (139,116), root:(146,166),
    state 0x0, button 255, same_screen YES

ButtonRelease event, serial 31, synthetic NO, window 0x4400001,
    root 0x7d, subw 0x0, time 13127176, (139,116), root:(146,166),
    state 0x0, button 5, same_screen YES

How do I map them to make them work?  Does anyone have a clue, or can you point me to another place to look?

Patrick

---

### Post by zazkia on 2009-02-10
Shrugs Here's my two cents, 


my ++: for those of you with compiling issues (concerning the expression keys) i solved mine by installing  libxtst-dev , 

 ( I found it through the synaptic, i'm not too handy with command lines; which brings me to... ) 

my ----: I gave up editing xorg.conf . I changed it according into something derived from hardy
(the input device option that isnt mentioned anymore?! ) 
it to-tal-ly smashed my X, 

if anyone is interested I have the old one somewhere... Why why why. 
anyways i have enough of it. I accidentally broke Vi during the process, had 2 xorg.confs that i couldnt rm and the only option left was the one suggested in the comment lines 
 sudo dpkg-reconfigure -phigh xserver-xorg

I'll draw a little with the mouse instead and then its bedtime

BTW the suggestion that the stylus does work, does that mean you cannot actually move the cursor without drawing? I cannot and its terribly annoying, I cannot write but in cursive.

---

### Post by poobslag on 2009-02-26
I have my tablet working mostly properly - but unplugging/replugging in the tablet still makes it unresponsive except for the tip.

I found a workaround here - [http://ubuntuforums.org/showthread.php?t=674738&page=3](http://ubuntuforums.org/showthread.php?t=674738&page=3) - which says to "switch to another virtual terminal" - so hit CTRL-ALT-F1, and then CTRL-ALT-F7, and that brings your tablet back into a good state

---

### Post by Loïc2 on 2009-03-02
> **EvanKroske said:**
> Sorry if this is a necro-bump, but I want my table to work! I have modified my xorg.conf several times, unplugged and replugged in my tablet, and I can still only get the stylus tip to be recognized.
You're using /dev/input/event0 in your /etc/X11/xorg.conf. See the guide on the Ubuntu wiki, but you most surely want to use /dev/input/wacom (plug your wacom tablet, and see what appears in /dev/input). Alternatively, you could also use what appears in /dev/input/by-id/

The reason is that your tablet won't always be assigned to /dev/input/event0, it could be any number instead of 0, like /dev/input/event1 for example.

This part in the Linux Wacom guide needs to be updated, the Linux Wacom developers are aware of that. However, nobody had the time to change the guide (and since the one changing that would have to check with the major distributions, and maybe also with *BSD / Solaris to see if they also create the symlink /dev/input/wacom, it's a more time-consuming job than it may appear).

> **EvanKroske said:**
> When I made this last change, the stylus tip stopped working and nothing started working.

You don't say what "this last change means". If it's adding the lines in your xorg.conf, it's normal, when the tablet is plugged in when X starts, xorg.conf takes precedence over the .fdi method, and since /dev/input/event0 most probably point to something else than your tablet, thus the tablet don't work at all.

---

### Post by Loïc2 on 2009-03-02
> **zazkia said:**
> my ----: I gave up editing xorg.conf . I changed it according into something derived from hardy
(the input device option that isnt mentioned anymore?! ) 
it to-tal-ly smashed my X, 
That's expected, it happened to me too at the time - that's why the guide warns you that editing xorg.conf in recent Ubuntu releases runs the risk of hosing X. Most probably the trouble was with your ServerLayout section, since that section is not there on recent xorg.conf you need to add it for the wacom tablet, but if you add it you also have to add lines at least for Identifier and Screen (see [https://help.ubuntu.com/community/WacomTroubleshooting](https://help.ubuntu.com/community/WacomTroubleshooting) which the guide links to). However, that's only a minimum, depending on your configuration you might have to add more.

> **zazkia said:**
> BTW the suggestion that the stylus does work, does that mean you cannot actually move the cursor without drawing? I cannot and its terribly annoying, I cannot write but in cursive.

If you're facing this problem, there's a possibility you're affected by a bug in the 0.8.4 drivers in Ubuntu, and might have to use the drivers straight from the Linux Wacom Project (use the most recent stable ones, like 0.8.2.1 or something). See [https://help.ubuntu.com/community/Wacom/LatestDriver](https://help.ubuntu.com/community/Wacom/LatestDriver) for an example.

However, as long as you don't have a valid configuration the results might not make a big difference.

---

### Post by Loïc2 on 2009-03-02
> **phorgan1 said:**
> How do I map them to make them work?  Does anyone have a clue, or can you point me to another place to look?

I've got no clue, I never used the mouse (and I'm also not sure I understand what you want to do :p ). You could have a look at the documentation on the Linux Wacom Project site, or ask in the linuxwacom-discuss mailing list (links are on the LWP site) - but google it first or check on the list archives, somebody might have faced the same problem before.

---

### Post by epopui on 2009-03-03
Hi 
Thank you for your hard work on producing a working manual on configuring a Wacom tablet in 8.10 

Q: I use my mouse with my left hand therefore the stylus also works that way which is not what I want - is there away to change the buttons on the stylus?   Mouse is set to left handed in >System>Mouse

Thank you,
Martin

---

### Post by M@s on 2009-03-07
Hello!

I have a problem with my Fujitsu-Siemens T4010D Tablet PC. At first I installed Ubuntu 8.10 from inside Windows XP, and then I got the drivers to work perfect without any issues. But since I formatted the whole drive and installed it again, I have this problem:
The first time I touch the screen with my pen after a boot, the whole screen turns black and this text appears for a second:

```
* Starting System Tools Backends system-tools-backends   [ OK ]
* Starting anac(h)ronistic cron anacron                        [ OK ]
* Starting deferred execution scheduler atd                    [ OK ]
* Starting periodic command scheduler crond                    [ OK ]
* Enabling additional executable binary formats binfmt-support [ OK ]
* Checking battery state...
/dev/sda:
setting Advanced Power Management level to 0xfe (254)
                                                               [ OK ]
```

Then it returns to login screen, and I have to sign in again. All the programs that was up running before is now gone. Fortunately the tablet now works excellent without trouble, until the next reboot...

Any idea how to solve this problem? I've tried with the drivers 0.8.1.4 and 0.8.1.6, no difference. I've also tried the 0.8.2-2 and [this guide](https://wiki.ubuntu.com/LaptopTestingTeam/FujitsuT4010D), but none of them worked at all.

Please also have a look at attached xorg.conf below.

Thanks.

---

### Post by Favux on 2009-03-08
Hi M@s,

So first you installed Ubuntu through Wubi in Windows?  And now you have installed Ubuntu directly on to your hard drive.

I'm not sure what's causing the problem.  Your xorg.conf is not properly configured, but at first glance what concerns me is:
```
Option		"UseFBDev"		"true"
```
What is that for?  Several of your xorg.conf entries are for an external Wacom graphics tablet not a tablet pc and we should be able to remove them.

Does your stylus have an eraser?  Does the stylus have buttons on it?  If so how many?

Please go to :

[http://ubuntuforums.org/showthread.php?t=1075239]("http://ubuntuforums.org/showthread.php?t=1075239") 

I made a first attempt at an xorg.conf for a T4010 user there.  And aussiedwarf joined us.  He has a Fujitsu T4010 that is setup.
(Is a Fujitsu Lifebook 4010D the same model?)

---

### Post by M@s on 2009-03-08
Hi Favux, thanks for your answer.

Yes, I first installed Ubuntu from Windows, but I don't know what it's called. I just mounted the .iso and started the installation. It's now installed through a netboot.

I have no idea what that line is for. I generated the xorg.conf file by the "dpkg-reconfigure" command, since I thought I accidentally deleted the file...
But now it turns out I hadn't, and that the xorg.conf is actually left empty after an Ubuntu network installation. I've now performed a new clean installation again, for a confirmation - xorg.conf is empty!

I know this wasn't the case when installing through Windows.

So, I think the problem is that the netboot installation and the CD installation doesn't do the same thing. And a netboot installation is the only alternative I have...

---

### Post by Favux on 2009-03-08
Hi M@s,

Hmmm.  Weird.

Well OK.  I will try to assemble a test xorg.conf for you from what you posted and from the others on the linked thread.  I'll post it there.

That'll take a little while, in the meantime could you post on that thread whether your stylus has an eraser? Does the stylus have buttons on it? If so how many?

---

### Post by &#24859; am best on 2009-03-08
Ok i need help T_T 

I've installed the wacom bamboo fun by using this guide and it works perfectly fine. 

But yesterday when i reboot my laptop, when i logged in, my menu taskbar is nowhere to be seen! I tried right-clicking and clicked "Terminal" but it never load. 

Please don't tell me i have to reformat T___T 

I think the xorg.conf is messed up... 

I'm using Linux Mint Gnome and i think any help from the Ubuntu perspective will definitely help!!

---

### Post by lhansen on 2009-03-24
Okay, here's my problem... I have an Intuos3 setup by copying and pasting the xorg from the howto. Things that work: stylus, pressure sensitivity, mouse tracking, clicking with mouse button 3, pad button 1. Things that don't work mouse scrolling, eraser, pad scrolling, other pad buttons (haven't tried to configure them). Also, after logging in with the updated xorg, all of my icons and fonts have reverted to an apparently simpler style. This has happened before when I was mucking with the xorg to get an external monitor working.

I'd like to at least get the mouse scrolling functioning. Any thoughts?

Here is the xorg.conf
```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
# sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
	Identifier "Laptop"
	Option "PreferredMode" "1280x800"
EndSection

Section "Monitor"
	Identifier "External"
	Option "PreferredMode" "1680x1050"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device "Intel 915"
	Monitor "Laptop"
	Defaultdepth 24

EndSection

Section "Module"
	Load "glx"
	Load "GLcore"
	Load "dri"
	Load "v4l"
EndSection

Section "InputDevice"
	Identifier "Generic Keyboard"
	Driver "kbd"
	Option "CoreKeyboard"
	Option "XkbRules" "xorg"
	Option "XkbModel" "pc105"
	Option "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier "Configured Mouse"
	Driver "mouse"
	Option "CorePointer"
	Option "Device" "/dev/input/mice"
	Option "Protocol" "ImPS/2"
	Option "ZAxisMapping" "4 5"
	Option "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier "Synaptics Touchpad"
	Driver "synaptics"
	Option "SendCoreEvents" "true"
	Option "Device" "/dev/psaux"
	Option "Protocol" "auto-dev"
	Option "HorizScrollDelta" "1"
	Option "SHMConfig" "true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/input/wacom" # USB ONLY?
#  Option        "Device"        "/dev/ttyS0"      # SERIAL ONLY
  Option        "Type"          "stylus"
#  Option        "ForceDevice"   "ISDV4"           # Tablet PC ONLY
  Option        "USB"           "on"               # USB ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/input/wacom" # USB ONLY?
#  Option        "Device"        "/dev/ttyS0"      # SERIAL ONLY
  Option        "Type"          "eraser"
#  Option        "ForceDevice"   "ISDV4"           # Tablet PC ONLY
  Option        "USB"           "on"               # USB ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/input/wacom" # USB ONLY?
#  Option        "Device"        "/dev/ttyS0"      # SERIAL ONLY
  Option        "Type"          "cursor"
#  Option        "ForceDevice"   "ISDV4"           # Tablet PC ONLY
  Option        "USB"           "on"               # USB ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "pad"
  Option        "Device"        "/dev/input/wacom"    # USB ONLY
#  Option        "Device"        "/dev/ttyS0"         # SERIAL ONLY
  Option        "Type"          "pad"
  Option        "USB"           "on"                  # USB ONLY
EndSection

# Uncomment the following section if you you have a TabletPC that supports touch
# Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "touch"
#  Option        "Device"        "/dev/ttyS0"       # SERIAL ONLY
#  Option        "Device"        "/dev/input/wacom" # USB ONLY
#  Option        "Type"          "touch"sudo gedit /etc/X11/xorg.conf
#  Option        "ForceDevice"   "ISDV4"            # Serial Tablet PC ONLY
#  Option        "USB"           "on"               # USB ONLY
# EndSection

Section "Device"
	Identifier "Intel 915"
	Boardname "Intel 915"
	Busid "PCI:0:2:0"
	Driver "intel"
	Option "monitor-Laptop" "Laptop"
	Option "monitor-External" "External"
EndSection

Section "ServerLayout"


  Identifier    "Default Layout"
  Screen        "Default Screen"
  InputDevice   "stylus"  "SendCoreEvents"
  InputDevice   "eraser"  "SendCoreEvents"
  InputDevice   "cursor"  "SendCoreEvents" # For non-LCD tablets only
  InputDevice   "pad"                      # For Intuos3/CintiqV5/Graphire4/Bamboo tablets
# InputDevice   "touch"   "SendCoreEvents" # Only a few TabletPCs support this type
EndSection

```

---

### Post by Gemnoc on 2009-04-03
Back in February, **phorgan1** asked how to activate the ExpressKeys on his Bamboo Fun.

Well if you're still monitoring this thread phorgan1, I've found a tutorial to enable the pad keys and round "trackpad" on the french Ubuntu-fr documentation site.

I've recopied the procedure in this thread (message #7):
[http://ubuntuforums.org/showthread.php?p=7003860#post7003860](http://ubuntuforums.org/showthread.php?p=7003860#post7003860)

Hope this helps!

---

### Post by RecoilUK on 2009-04-04
Just want to add. I have a Wacom Bamboo Fun and installed everything according to the wiki documentation, but my eraser would always act as a fatter pen nib.

You have to alter your xorg.conf file, before you install the wacom-tools package, then it will work as expected.

Thanks

---

### Post by Loïc2 on 2009-04-05
> **&#24859 said:**
> But yesterday when i reboot my laptop, when i logged in, my menu taskbar is nowhere to be seen! I tried right-clicking and clicked "Terminal" but it never load.

Sounds more like a problem with your configuration files in your home directory than anything Xorg related.
Try creating a new user, and see if the Menu taskbar is still missing.
Also, if you have another bar still there (the one at the bottom for example) it's easy to create another one, just right click on the existing one. You can add the menus anytime by right clicking also (something like "add to panel" then you chose one of the two menus to install).

---

### Post by Loïc2 on 2009-04-05
> **lhansen said:**
> Okay, here's my problem... I have an Intuos3 setup by copying and pasting the xorg from the howto. Things that work: stylus, pressure sensitivity, mouse tracking, clicking with mouse button 3, pad button 1. Things that don't work mouse scrolling, eraser, pad scrolling, other pad buttons (haven't tried to configure them).

I'd like to at least get the mouse scrolling functioning. Any thoughts?

Here is the xorg.conf
Try removing all the commented parts in your wacom lines (all the lines starting with #, and everything at the end of line that has # before, including removing the # themselves with what follows it.

That aside, there's not much else I can think of if you're using an Ubuntu 8.10 install from scratch (not an upgrade from 8.04 or anything) and have installed the defaults xserver-xorg-input-wacom and wacom-tools from the repositories. I've got the same setup, an Intuos3 A5, and everything is working, except probably the mouse since I never use it and don't put the lines for it in xorg.conf (switching between the pen and the wacom mouse is a pain when drawing, since you have to drop the pen, then pick up the mouse and first move it onto the wacom tablet, while with a normal mouse you can start using it as soon as your hand is on it). Maybe try it without any mouse lines and see if you've got the eraser working.

> **lhansen said:**
> Also, after logging in with the updated xorg, all of my icons and fonts have reverted to an apparently simpler style. This has happened before when I was mucking with the xorg to get an external monitor working.
That usually happens when you used sudo instead of gksudo for a graphical tool like the text editor gedit - with sudo, they leave the configuration in the user home directory (instead of /root), which changes the permissions.

I think you want your permissions set back to 755 instead of 777. Probably something like :
```
sudo chmod -R 755 /home/your_user_name/
```
Probably not the "perfect" Linux guru method, if somebody has any better line please tell me.

---

### Post by Loïc2 on 2009-04-05
To all:
Jaunty might eventually get input hotplug, no xorg.conf necessary method that enables all devices (pen, eraser, pad, #garb# mouse), even for serial tablets (most Tablet PC). That comes straight from Fedora, and if enough people can test it, it would be great to have it. We'd actually end up with the HAL method that wasn't supposed to work for multiple device peripherals ;)

If you can help testing, please read the thread on [ubuntu-devel]("https://lists.ubuntu.com/archives/ubuntu-devel/2009-March/027865.html") and use [this Launchpad bug report]("https://bugs.launchpad.net/bugs/355340").

I'll updates the places I can think of, but please do the same (Favux, can I let you inform TabletPC users in the threads you know of?).

---

### Post by m0ntels on 2009-04-05
I just installed the new Wacom files from Launchpad and it got my eraser working.  I already had pressure in Jaunty.  Still no pad buttons or scroll for me though.  I'm not the household artist though, so the pen and eraser are the only parts I know what to do with anyway.

---

### Post by Loïc2 on 2009-04-05
> **m0ntels said:**
> I just installed the new Wacom files from Launchpad and it got my eraser working.  I already had pressure in Jaunty.  Still no pad buttons or scroll for me though.  I'm not the household artist though, so the pen and eraser are the only parts I know what to do with anyway.

Thanks a lot for your testing and reporting. For the pad buttons, did you try if they works with, for example, System>Preferences>Keyboard shortcuts (try to select an action, then press one of the pad buttons)?

---

### Post by phorgan1 on 2009-04-05
> **Gemnoc said:**
> Back in February, **phorgan1** asked how to activate the ExpressKeys on his Bamboo Fun.

Well if you're still monitoring this thread phorgan1, I've found a tutorial to enable the pad keys and round "trackpad" on the french Ubuntu-fr documentation site.

I've recopied the procedure in this thread (message #7):
[http://ubuntuforums.org/showthread.php?p=7003860#post7003860](http://ubuntuforums.org/showthread.php?p=7003860#post7003860)

Hope this helps!

Well it generates things but not what I want for the keys and the scroll part's still inoperative and on jaunty the whole thing is iffy.  If I edit my xorg.conf to make my tablet work and restart X (RIGHT-ALT SYSRQ K) on jaunty, then things work better, though my eraser is pegged at the bottom left of the screen.  BUT  When I reboot, X is completely hosed and I have to drop to single user mode and comment out the changes in the ServerLayout section to be able to boot to a login.  Not getting much use out of my pad--did order a cool black bag for it though:)

Patrick

---

### Post by Favux on 2009-04-05
Hi Loïc2,

Sure, I would be happy to.

---

### Post by m0ntels on 2009-04-06
Well I've played with it some more and this is what happens...

The scroll pad works in Firefox for example, but not in Gimp.  I tried the keyboard shortcuts thing, and it just switches back to the default.  In Gimp, all the buttons and scroll pad just make it randomly stutter back and forth between different tools.

---

### Post by Saturn Lad on 2009-04-11
Well, I've been trying to follow the advice in this thread, as well as others, and am having mixed results with Wine applications.

I'm running Jaunty with version 0.8.2.2 of the wacom-tools and xserver-xorg-input-wacom packages. I have a USB Wacom Intuos 2 6x8.

[COLOR="Green"]GIMP[/COLOR] and [COLOR="Green"]Inkscape[/COLOR] seem to be working fine.

[COLOR="Green"]Photoshop CS2[/COLOR] through Wine 1.1.18 works fine. It has pressure sensitivity and properly responds to the eraser and buttons.
[COLOR="Green"]ArtRage 2.5 Starter Edition[/COLOR] also works fine, it supports pressure, angle, eraser...

[COLOR="Red"]Expression 3[/COLOR] in Wine has no pressure support.
[COLOR="Red"]Manga Studio 3[/COLOR] in Wine has no pressure support.
Manga Studio 4 is unusable in Wine, so I was really hoping I could keep using 3 in it.  This is one of the few things forcing me to boot to my Windows XP partition.  I imagine the inconsistency would point to a Wine issue, but the fact that it works in PS but not MS is strange.  It's also frustrating because a number of users have indicated that the pressure sensitivity works for them in Manga Studio 3 through Wine... however I think that was through the pre-hdi method of modifying xorg.conf.

Also, I am running dual monitors and would like to be able to map the wacom to one screen, so I can get better precision while drawing.  Has anything been done in that direction yet, since it appears that wacomcpl doesn't work with the new hal hotplug system?

Any ideas?
Thanks!

---

### Post by Saturn Lad on 2009-04-19
Found the bug report for the problem I'm seeing, it's still not fixed yet.

[http://bugs.winehq.org/show_bug.cgi?id=11846]("http://bugs.winehq.org/show_bug.cgi?id=11846")

Thanks for all the help in this thread though, it's been a great resource.

---

### Post by krylian on 2009-04-25
Hi,

I've configured my custom_wacom.fdi for my stylus. It goes well. But how can I add my eraser, pad and so on? I would like to make for my eraser and mouse an different mode as for my stylus. 
And how can I configre my buttons on my pad without overwrite my configuration for my stylus?
Is there anywhere a description for this?

At the moment my custom_wacom.fid looks like this:

```

  <device>
    <match key="info.capabilities" contains="input">
      <match key="info.product" contains="Wacom">
        <merge key="input.x11_driver" type="string">wacom</merge>
        <merge key="input.x11_options.Type" type="string">stylus</merge>
        <merge key="input.x11_options.Mode" type="string">Absolute</merge>
        <merge key="input.x11_options.TopX" type="string">0</merge>
        <merge key="input.x11_options.TopY" type="string">0</merge>
        <merge key="input.x11_options.BottomX" type="string">40639</merge>
        <merge key="input.x11_options.BottomY" type="string">25399</merge>
      </match>
      <match key="info.product" contains="WALTOP">
        <merge key="input.x11_driver" type="string">wacom</merge>
        <merge key="input.x11_options.Type" type="string">stylus</merge>
      </match>
    </match>
  </device>

```

---

### Post by Peter76 on 2009-04-25
I just upgraded to Jaunty, and now the pad of my Bamboo only scrolls up.... I tried overruling this by using ```
xsetwacom set pad relwup 5
xsetwacom set pad relwdn 4
``` but this doesn't work.... it only keeps scrolling up:-(
Anyone knows how to solve this?

---

### Post by Favux on 2009-04-25
Hi krylian,

I think it should look something like:
```
  <device>
    <match key="info.capabilities" contains="input">
      <match key="info.product" contains="Wacom">
        <merge key="input.x11_driver" type="string">wacom</merge>
        <merge key="input.x11_options.Type" type="string">stylus</merge>
        <append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
        <append key="wacom.types" type="strlist">eraser</append>
        <append key="wacom.types" type="strlist">pad</append>
        <merge key="input.x11_options.Button2" type="string">3</merge>
        <merge key="input.x11_options.Mode" type="string">Absolute</merge>
        <merge key="input.x11_options.TopX" type="string">0</merge>
        <merge key="input.x11_options.TopY" type="string">0</merge>
        <merge key="input.x11_options.BottomX" type="string">40639</merge>
        <merge key="input.x11_options.BottomY" type="string">25399</merge>
      </match>
      <match key="info.product" contains="WALTOP">
        <merge key="input.x11_driver" type="string">wacom</merge>
        <merge key="input.x11_options.Type" type="string">stylus</merge>
      </match>
    </match>
  </device>
```
Where I've added eraser, pad, and a stylus button as a right mouse click.  You may be able to add the options to stylus under stylus and then follow with eraser, pad, etc. (just to make things look organized).  I'm not sure about that because I am definitely not a .fdi guru.

Hi Peter76,

The "native" Jaunty linuxwacom 0.8.2-2 (as patched by Timo Aaltonen to support HAL and Xserver 1.6) doesn't support xsetwacom (and hence wacomcpl and it's .xinitrc).  This is because the callout from the .fdi file returns HAL/D-BUS names that aren't compatible with linuxwacom.  Rec discovered this on this thread:  [http://ubuntuforums.org/showthread.php?t=1122952](http://ubuntuforums.org/showthread.php?t=1122952)  And came up with a script to fix it.  He posted the script on Timo's launchpad feedback site:  [https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/355340](https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/355340)  And it looks like maybe Timo has now patched xorg-xserver to work correctly:  [https://launchpad.net/~tjaalton/+archive/ppa](https://launchpad.net/~tjaalton/+archive/ppa)  At least I'm hoping that's what the changelog means.

In the meantime if you want to experiment with the script and see if it lets you configure your tablet through wacomcpl and/or xsetwacom see Jaunty Users near the top here:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)  The link will take you to post #104 on that thread where gali98 has a HOW TO.  If your graphics tablet is working OK you probably don't need to do the part about compiling the 0.8.3-2 wacom.ko kernel driver, just the script part.

Edit:  It looks like ProhetofDoom found another way from the LWP site.  See post #8 here:  [http://ubuntuforums.org/showthread.php?p=7143989#post7143989](http://ubuntuforums.org/showthread.php?p=7143989#post7143989)  It is from Tom Jaeger.  He posted today at LWP another way to do things without rec's script:  [http://sourceforge.net/mailarchive/forum.php?thread_name=cc6cabec0904250703t5dd70a81t39160dcbb62d1031%40mail.gmail.com&forum_name=linuxwacom-discuss](http://sourceforge.net/mailarchive/forum.php?thread_name=cc6cabec0904250703t5dd70a81t39160dcbb62d1031%40mail.gmail.com&forum_name=linuxwacom-discuss)  Instead of "xsetwacom list" he suggests "xinput --list" and using those "names".

---

### Post by darkmoondancer on 2009-04-26
Hello! I need a bit of help. ^_^

I was having issues with my Bamboo Fun Tablet on Intrepid, and so I updated to Jaunty today, in hopes of having an easier time with it. 

And I did. The tablet is picked up in GIMP, and I managed to set the scroll wheel to work as well as the stylus being recognized. 

BUT, the problem I am having is with the pressure sensitivity of the stylus. 
Right now, the stroke will turn out lighter or darker depending on the pressure applied, but when I used this tablet on Windows it would also vary the thickness of the stroke according to the pressure, and that is the sensitivity I am more concerned with. 

Anyone know what I can do about this? Or is this just something that GIMP does not pick up on and I should be using a different art program? 

- DD

---

### Post by Gemnoc on 2009-04-26
I don't know how well you know Gimp, so forgive me if I'm saying something obvious to you.

I'm not sure about the exact terms, since my system is in French I'm translating the terms as I best think they must be in English.

When the brush/pencil/airbrush is active, you can change the brush dynamics in the options right underneath the toolbox. You have to click on "Brush Dynamics" to get the dropdown options. They give you options on pressure, speed and random, with such controls as opacity, ratio, color, size and hardness.

When I first started to fiddle with this, only opacity was ticked. It may be the case for you as well.

Hope this helps.

- G.

P.S. Would you mind explaining what exactly you did to make the scroll wheel and the stylus work? Are the eraser and the mouse working as well?

I'd like to upgrade to 9.04 but I want to be sure everything works on my Bamboo Fun, as it does right now on 8.10.

Thanks!

---

### Post by darkmoondancer on 2009-04-26
@ Gemnoc - Thanks for replying! 

I'm used to Adobe Photoshop and I'm trying to switch over to GIMP instead of trying to wrestle with Linux to install Photoshop. 

But those were exactly the settings I was looking for. Thank you! 

As for what I did to get my stylus and etc working: 

All I did (Using Jaunty), was setup my tablet using the setup CD. Just a simple open and install. 
Then I opened GIMP and went into Edit > Preferences > Input Devices > Configure Extended Input Devices

Once there, the drop-down called Devices: and choose each of the possible Wacom options, changing each one to "Screen" Mode and then just save in that window. Click "Close", and in the window underneath, click "Save Input Device Settings Now", then close. 

Once I did that, my stylus was working, as well as the mouse and the scroll wheel. 
The buttons do not work on mine though. 
*Note: My eraser was working as a paintbrush so at first I thought it wasn't registering, but I selected Eraser with that end of the stylus, and it has remembered that since. 

Hope this helps. 
If anything is confusing-sounding, let me know and I'll try to clarify my rambles. :) 

- DD

---

### Post by Gemnoc on 2009-04-27
You're welcome. Gimp has indeed a quirky UI.

So, straight up Jaunty install, the scroll wheel works, but the buttons don't. As I was afraid (and as infered by previous posters), some more tinkering seems to be needed...

Thanks for the info.

---

### Post by mesilliac on 2009-04-27
Hi, I've just managed to get my **Graphire Bluetooth** working, and the new hotplug functionality works brilliantly :).

It still needs a driver to be manually installed, so if anyone with the same tablet wants to get it working, try following the instructions at [http://ubuntuforums.org/showthread.php?t=674738&page=8#77](http://ubuntuforums.org/showthread.php?t=674738&page=8#77)

Now for some general wacom tablet info regarding settings:

[size=4]**custom .fdi files**[/size]

This simple .fdi file seems to work for calibrating both stylus and eraser (these are my preferred settings, adjust to taste):

/etc/hal/fdi/policy/custom_wacom.fdi
```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

<deviceinfo version="0.2">

  <device>
    <match key="input.x11_driver" contains="wacom">
      <match key="input.x11_options.Type" contains="stylus">
        <merge key="input.x11_options.TPCButton" type="string">on</merge>
        <merge key="input.x11_options.KeepShape" type="string">on</merge>
        <merge key="input.x11_options.Threshold" type="string">1</merge>
        <merge key="input.x11_options.PressCurve" type="string">50,0,100,50</merge>
      </match>
    </match>
    <match key="input.x11_driver" contains="wacom">
      <match key="input.x11_options.Type" contains="eraser">
        <merge key="input.x11_options.TPCButton" type="string">on</merge>
        <merge key="input.x11_options.KeepShape" type="string">on</merge>
        <merge key="input.x11_options.Threshold" type="string">1</merge>
        <merge key="input.x11_options.PressCurve" type="string">50,0,100,50</merge>
      </match>
    </match>
  </device>

</deviceinfo>
```

**[size=3]Does this work for anyone else?[/size]**
It should work for most Wacom tablets.

[size=3]***NOTE**: if your custom .fdi file contains the "hal-setup-wacom" callout it can crash your X... to stop it crashing, unplug your tablet.*[/size]

---

### Post by mallow on 2009-04-27
Hi, I`d like to share with you how I`ve managed to get my WACOM Intuos3 tablet working under jaunty. It was working on ubuntu 8.10 after I did what`s listed here: [https://help.ubuntu.com/community/Wacom]("https://help.ubuntu.com/community/Wacom") and here: [https://help.ubuntu.com/community/WacomTroubleshooting]("https://help.ubuntu.com/community/WacomTroubleshooting") and set express keys with wacomcpl.
After upgrade to jaunty, my tablet was still working, but express keys and touch strip on the pad didn`t. I`ve found solution here: [http://ubuntuforums.org/showthread.php?p=7143866#post7143866]("http://ubuntuforums.org/showthread.php?p=7143866#post7143866"). I`ve simply changed my /home/username/.xinitrc file to:
```
#!/bin/sh
xsetwacom set "Wacom Intuos3 6x8 pad" StripRDn "CORE KEY NumpadPlus"
xsetwacom set "Wacom Intuos3 6x8 pad" StripRUp "CORE KEY NumpadMinus"
xsetwacom set "Wacom Intuos3 6x8 pad" StripLDn "CORE KEY ["
xsetwacom set "Wacom Intuos3 6x8 pad" StripLUp "CORE KEY ]"
xsetwacom set "Wacom Intuos3 6x8 pad" Button8 "CORE KEY CTRL z"
xsetwacom set "Wacom Intuos3 6x8 pad" Button7 "CORE KEY CTRL y"
xsetwacom set "Wacom Intuos3 6x8 pad" Button6 "CORE KEY backslash"
xsetwacom set "Wacom Intuos3 6x8 pad" Button5 "CORE KEY '"
xsetwacom set "Wacom Intuos3 6x8 pad" Button4 "CORE KEY Tab"
xsetwacom set "Wacom Intuos3 6x8 pad" Button3 "CORE KEY SHIFT"
xsetwacom set "Wacom Intuos3 6x8 pad" Button2 "CORE KEY ALT"
xsetwacom set "Wacom Intuos3 6x8 pad" Button1 "CORE KEY CTRL"
xsetwacom set "Wacom Intuos3 6x8" "PressCurve" 50 0 100 50
```
The file is of course executable and filed under gnome-session-properties. Everything works fine except that if I unplug the tablet and plug it again I have to run /home/username/.xinitrc again. I remember that there was an option (somewhere in preferred applications) to run some app when graphic tablet is pluged in. Can`t find it though. Maybe that would do the trick. Besides, it would be great if there was a graphical tool to change Express Keys shortcuts and tablet`s sensivity as wacomcpl doesn`t work now (at least for me).

---

### Post by Guruji on 2009-04-27
same here, i got the express keys working on my bamboo fun with this

```
 #!/bin/sh

case "$1" in
  start|"")
# put this file in /etc/init.d/ and chmod +x
	xsetwacom set "Wacom BambooFun 6x8 pad" AbsWUp "core key -"    			# sending page up event when moving anti-clockwise 
	xsetwacom set "Wacom BambooFun 6x8 pad" AbsWDn "core key +"   			# sending  page down event when moving clockwise
	xsetwacom set "Wacom BambooFun 6x8 pad" button1 "core key CONTROL z"  	        # bouton <
	xsetwacom set "Wacom BambooFun 6x8 pad" button2 "core key Esc"  			# bouton FN1
	xsetwacom set "Wacom BambooFun 6x8 pad" button3 "core key CONTROL y"        		# bouton >
	xsetwacom set "Wacom BambooFun 6x8 pad" button4 "core key Enter"              	# bouton FN2

        ;;

  stop)
        ;;
  *)
        echo "Usage: wacomexpresskeys [start|stop]" >&2
        exit 3
        ;;
esac
```

but i have to start it manually everytime i plug in the tablet, if anyone knows how to start it automatically when you plug in the tablet, I'll be happy to hear from you!

---

### Post by Gemnoc on 2009-04-28
> **Guruji said:**
> but i have to start it manually everytime i plug in the tablet, if anyone knows how to start it automatically when you plug in the tablet, I'll be happy to hear from you!
Hey I've seen that script before! ;)

(Although I'm the one who posted it [here]("http://ubuntuforums.org/showpost.php?p=7003860&postcount=7"), I deserve absolutely no credit at all, because I just copy/pasted it from the French Ubuntu wiki. Besides, I wouldn't know how to debug my hardware even to save my own life! :oops:)

You just need to load the script at startup.

Go to System-->Preferences-->Sessions, 
add new program name: Wacom Express Keys
command: /etc/init.d/wacomexpresskeys

BTW On what Ubuntu release are you? I'm on 8.10 and I'd like to upgrade to 9.04, but not before I know that this procedure will still work (which I doubt), or that something else can be done to activate all buttons and the scroll wheel on the pad.

[Edit: re-read your message, I'm not sure that would work since you plug/unplug your tablet. Mine is always plugged so I can't be sure.]

---

### Post by ilpiero on 2009-04-28
Let' see if I can summarise a bit the situation (at least for the bamboo fun which is my tablet).
I'm talking about Ubuntu 9.04 jaunty (fresh istall).
The stylus is recognised and functional even if plugged afer the boot (hotplug).
The "wheel" works as the mouse wheel.
The pad buttons don't work (and you cannot set them under the "keyboard shortcuts" application)  unless you set them the with the xsetwacom command (via console).
The wacomcpl GUI doesn't work anymore unless you insert the wacom tablet devices (pad,stylus,eraser..) in the xorg.conf file, but that gives an x server error at startup if the tablet is not plugged in.

The way to make the table work completely seem to be making an executable script and start it with the system (haven't tried yet).

Cheers

---

### Post by Guruji on 2009-04-28
@gemnoc: if you keep your tablet pluged all the time, then no problem, the scrip works as usual. But if, like me, you plug it at any time, then it doesn't work, you need to start the script manually after pluging the tablet.... that's why I'm looking for a way to have the script starting automatically when you plug the tablet in.

@ilpiero: exactly.. but 
> The way to make the table work completely seem to be making an executable script and start it with the system
this will only work if your tablet is pluged in on startup, if not, start the script manually-

---

### Post by shatterblast on 2009-04-28
Deleted.  (For troubleshooting with Jaunty.)

---

### Post by ubootfanat on 2009-04-29
Hi!

Have a Wacom Bamboo here which works nearly breathtaking. Using Ubuntu 9.04 and Wacom-Tools 0.9.2.2.

Problem:
Scroll Wheel only works in one direction.
- yes I know this was already discussed in this thread
- I did what was said but it does not work for me

a few facts:
[LIST]
[*]tried to use xsetwacom to fix issue.
```

$ xsetwacom get "Wacom Bamboo pad" AbsWUp
5
$ xsetwacom get "Wacom Bamboo pad" AbsWDn
4

```
correct settings by default.


[*]so I checked it using xev. outcome was: scrolling in one direction fires MotionNotify - ButtonPress "Button 4" - ButtonRelease "button 4" - MotionNotivy, scrolling in the other direction fires only the MotionNotify-events.
```

MotionNotify event, serial 41, synthetic NO, window 0x4200001,
    root 0x13c, subw 0x4200002, time 18555754, (41,50), root:(48,92),
    state 0x0, is_hint 0, same_screen YES

```

[*]Then I mapped the AbsWUp-event to Button4 also. It worked. I could use the scrollpad in either direction to scroll down.

[*]Then I checked wacdump from [linuxwacom]("http://linuxwacom.sourceforge.net/"). I had to disable HAL to get this to work. But finally it says that every single button including little problem-scrollwheel do work correctly.

[*]next step was xidump from [linuxwacom]("http://linuxwacom.sourceforge.net/"). Anything worked except my scroll-wheel. Only one direction was recognized.

[*]next step was xinput
```

$ xinput query-state "Wacom Bamboo pad"
...
ButtonClass
	button[1]=up
	button[2]=up
	button[3]=up
	button[4]=up
ValuatorClass Mode=Relative Proximity=Out
	valuator[0]=7969
	valuator[1]=8433
	valuator[2]=0
	valuator[3]=0
	valuator[4]=0
	valuator[5]=71
...

```
xinput says there are only 4 buttons on tablet. valuator{5] hints to the scroll wheel counter so the scroll wheel might be on "pad".
[/LIST]

My static xorg.conf-setup which I used in previouse ubuntu versions (<9.04) worked fine with AbsWUp/Dn set to 4 and 5.

Could it be that HAL prevents the whole wacom-thing to grab a fifth button? or is there a problem with the driver itself, what I do not believe since it worked for me over the whole last year? or is there a problem with HAL and the mapping? because wacdump shows that all events are recongnized correctly. using xidump shows a missing scroll-event.

any ideas?

thanks in the meanwhile
 ubootfanat

---

### Post by shatterblast on 2009-04-29
I had the same issue if you're refering to the round "touch pad" on the top of the pad.  While working, I think sensitivity is a recognized issue for that device at the moment.  On mine, it does recognize either direction correctly.  How ever, it is very touchy in that it doesn't work consistently.  Instead, what I did is mapped CTRL + S to mine within wacomcpl on both directions.  That way at least it does something.  I use it to save documents.

---

### Post by ubootfanat on 2009-04-30
Hi!

Yes exactly. The round touchpad in the middle of the 4 padbuttons.

But let me repeat: the pad works perfectly, so does xsetwacom. But xinput seems to not allow a fifth key. The second direction is mapped to that fifth key which is interpreted as scroll-event in X. and without that fifth key there will be no scroll-down event in X. I checked my mouse to see that my search on the internet was correct. Mousewheel is also mapped to button 4 and 5. Also the touchpad and the emulated wheel of the tiny little stick in the middle of my keyboard of my laptop.

If I get over a solution I will post it here. Any other ideas in the meanwhile?

ubootfanat

---

### Post by mzuther on 2009-04-30
Hi!

If you want to have your Wacom tablet automatically configured every time its plugged in without manually running scripts or **xsetwacom**, see [http://help.ubuntu.com/community/Wacom.fdi]("http://help.ubuntu.com/community/Wacom.fdi").

In short, you'll need to remove (or comment out) all Wacom customisations from **/etc/X11/xorg.conf**.  Then create the file **/etc/hal/fdi/policy/custom_wacom.fdi** and enter your customisations.  Here's my setup for an Intuos 3 - I exchanged some mouse buttons for left handed use and the buttons on the stylus.  The pad button customisations don't work yet, I guess I'll have to do further research for key presses...

```
<?xml version="1.0" encoding="UTF-8"?>

<deviceinfo version="0.2">
  <device>

    <!-- Wacom Intuos3 (Stylus) -->
    <match key="input.x11_driver" contains="wacom">
      <match key="input.x11_options.Type" contains="stylus">
        <merge key="input.x11_options.Button1" type="string">1</merge>
        <merge key="input.x11_options.Button2" type="string">3</merge>
        <merge key="input.x11_options.Button3" type="string">2</merge>
        <merge key="input.x11_options.Mode" type="string">Absolute</merge>
        <merge key="input.x11_options.TPCButton" type="string">off</merge>
      </match>
    </match>

    <!-- Wacom Intuos3 (Eraser) -->
    <match key="input.x11_driver" contains="wacom">
      <match key="input.x11_options.Type" contains="eraser">
        <merge key="input.x11_options.Button1" type="string">1</merge>
        <merge key="input.x11_options.Mode" type="string">Absolute</merge>
      </match>
    </match>

    <!-- Wacom Intuos3 (Mouse) -->
    <match key="input.x11_driver" contains="wacom">
      <match key="input.x11_options.Type" contains="cursor">
        <merge key="input.x11_options.Button1" type="string">3</merge>
        <merge key="input.x11_options.Button2" type="string">2</merge>
        <merge key="input.x11_options.Button3" type="string">1</merge>
        <merge key="input.x11_options.Button4" type="string">5</merge>
        <merge key="input.x11_options.Button5" type="string">4</merge>
        <merge key="input.x11_options.Mode" type="string">Relative</merge>
      </match>
    </match>

    <!-- Wacom Intuos3 (ExpressKeys) -->
    <match key="input.x11_driver" contains="wacom">
      <match key="input.x11_options.Type" contains="pad">
        <merge key="input.x11_options.Button1" type="string">core key shift</merge>
        <merge key="input.x11_options.Button2" type="string">core key alt</merge>
        <merge key="input.x11_options.Button3" type="string">core key ctrl</merge>
        <merge key="input.x11_options.Button4" type="string">core key space</merge>
        <merge key="input.x11_options.Button5" type="string">core key shift</merge>
        <merge key="input.x11_options.Button6" type="string">core key alt</merge>
        <merge key="input.x11_options.Button7" type="string">core key ctrl</merge>
        <merge key="input.x11_options.Button8" type="string">core key space</merge>
        <merge key="input.x11_options.StripLDn" type="string">5</merge>
        <merge key="input.x11_options.StripLUp" type="string">4</merge>
        <merge key="input.x11_options.StripRDn" type="string">5</merge>
        <merge key="input.x11_options.StripRUp" type="string">4</merge>
      </match>
    </match>

  </device>
</deviceinfo>
```

When you're finished, just un- and replug the tablet (or restart your computer if you have a serial tablet).  Good luck!

Martin

---

### Post by ubootfanat on 2009-05-02
Hi!

Yes it should work like that in theory.

1. I still not get a button 5-event.
2. This nice option core key ... does not work either

my fdi:
```
<?xml version="1.0" encoding="UTF-8"?>

<deviceinfo version="0.2">
  <device>
    <match key="input.x11_driver" contains="wacom">
      <match key="input.x11_options.Type" contains="stylus">
        <merge key="input.x11_options.KeepShape" type="string">on</merge>
        <merge key="input.x11_options.Button2" type="string">3</merge>
        <merge key="input.x11_options.Button3" type="string">2</merge>
      </match>
    </match>

    <match key="input.x11_driver" contains="wacom">
      <match key="input.x11_options.Type" contains="pad">
        <merge key="input.x11_options.Button1" type="string">core key ctrl alt left</merge>
        <merge key="input.x11_options.Button2" type="string">1</merge>	
        <merge key="input.x11_options.Button3" type="string">core key ctrl alt right</merge>
        <merge key="input.x11_options.Button4" type="string">2</merge>
        <merge key="input.x11_options.AbsWUp" type="string">4</merge>
        <merge key="input.x11_options.AbsWDn" type="string">5</merge>
      </match>
    </match>
  </device>
</deviceinfo>
```

lshal output for "Wacom Bamboo pad"
```
udi = '/org/freedesktop/Hal/devices/usb_device_56a_65_noserial_if0_logicaldev_input_subdev_1'
  info.capabilities = {'input'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_56a_65_noserial_if0_logicaldev_input'  (string)
  info.product = 'Wacom Bamboo pad'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_56a_65_noserial_if0_logicaldev_input_subdev_1'  (string)
  input.device = '/dev/input/event9'  (string)
  input.x11_driver = 'wacom'  (string)
  input.x11_options.AbsWDn = '5'  (string)
  input.x11_options.AbsWUp = '4'  (string)
  input.x11_options.Button1 = 'core key ctrl alt left'  (string)
  input.x11_options.Button2 = '1'  (string)
  input.x11_options.Button3 = 'core key ctrl alt right'  (string)
  input.x11_options.Button4 = '2'  (string)
  input.x11_options.Type = 'pad'  (string)
```
fdi-file seems to work as it should

Xorg.0.log output for "Wacom Bamboo pad"
```
(II) config/hal: Adding input device Wacom Bamboo pad
(**) Wacom Bamboo pad: always reports core events
(**) Wacom Bamboo pad device is /dev/input/event9
(**) Wacom Bamboo pad is in relative mode
(**) WACOM: suppress value is 2
(**) Wacom Bamboo pad: reading USB link
(**) Wacom Bamboo pad: threshold = 30
(**) Wacom Bamboo pad: max x = 14760
(**) Wacom Bamboo pad: max y = 9225
(**) Wacom Bamboo pad: max z = 511
(**) Wacom Bamboo pad: button2 assigned to 1
(**) Wacom Bamboo pad: button4 assigned to 2
(**) Wacom Bamboo pad: serial speed 9600
(II) XINPUT: Adding extended input device "Wacom Bamboo pad" (type: Wacom Pad)
(==) Wacom device "Wacom Bamboo pad" top X=0 top Y=0 bottom X=14760 bottom Y=9225 resol X=2540 resol Y=2540

```
X neither understands the advanced button mappings for button 1 and 3 nor a fifth button for scrolling.

xev does not show any events for padbutton 1 and 3 and also no button 5 for scrolling.

is there anything I have to do to enable those advanced button mappings?
any ideas regarding the scroll event?

thanks
ubootfanat

---

### Post by ola on 2009-05-03
Seems to work fine on my Wacom Graphire 4 (USB)!

I set it up my as follows:
[LIST]
[*]The button closest to the pen tip to be right click
[*]The tablet to be in relative mode
[*]Slow down the cursor a little bit
[/LIST]

My custom FDI-file:
```

<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->
<deviceinfo version="0.2">
  <device>
    <match key="input.x11_driver" contains="wacom">
      <match key="input.x11_options.Type" contains="stylus">
       	<merge key="input.x11_options.Mode" type="string">Relative</merge>
       	<merge key="input.x11_options.Button2" type="string">3</merge>
       	<merge key="input.x11_options.Button3" type="string">2</merge>
       	<merge key="input.x11_options.Speed" type="string">0.9</merge>
      </match>
    </match>
    <match key="input.x11_driver" contains="wacom">
      <match key="input.x11_options.Type" contains="eraser">
       	<merge key="input.x11_options.Mode" type="string">Relative</merge>
      </match>
    </match>
  </device>
</deviceinfo>

```

---

### Post by mzuther on 2009-05-03
Hi!

My tablet (Wacom Intuos 3) runs fine under Ubuntu Janty using a **custom_wacom.fdi** file (see my post above).  However, setting a keystroke to one of the buttons doesn't work so far.

For example, when I try setting

```
<merge key="input.x11_options.Button1" type="string">core key space</merge>
```

adapted from what I would use with xsetwacom, I only get this warning in **/var/log/Xorg.0.log**:

```
(WW) Option "Button1" requires an integer value
```

So I wonder whether there's a way to add keystrokes to buttons without going back to use **/etc/X11/xorg.conf**.

Thanks,

Martin

---

### Post by Loïc2 on 2009-05-04
> **mzuther said:**
> Hi!

My tablet (Wacom Intuos 3) runs fine under Ubuntu Janty using a **custom_wacom.cpi** file (see my post above).  However, setting a keystroke to one of the buttons doesn't work so far.

```
(WW) Option "Button1" requires an integer value
```

So I wonder whether there's a way to add keystrokes to buttons without going back to use **/etc/X11/xorg.conf**.

AFAIR, wacomcpl only allowed the stylus side buttons to be assigned to either left, right or middle mouse button, so it's possible that's the only options that will work. That's probably why you get the error message - an integer value would be 1, 2 or 3 (for the respective mouse buttons).

If you want to troubleshoot it, however, here's a crude method:

You can use the xsetwacom command to pass parameters on the fly to your wacom devices. First, use ```
xinput --list
``` to get the name of your devices, which should be similar to the ones [in this post]("http://ubuntuforums.org/showpost.php?p=7158628&postcount=160"), also using an Intuos 3. Those lines are for the pad, yours sounds more like a stylus button, but that should follow the same principle (if i remember correctly, the stylus would be the string without any name of device at the end, like "Wacom Intuos3 6x8" instead of "Wacom Intuos3 6x8 pad" in the example).

If you got troubles, either revert to the /etc/X11/xorg.conf method to get a decent configuration from wacomcpl, or better just install Ubuntu 8.10 on a separate partition, configure /etc/X11/xorg.conf then use wacomcpl, and get the script it produces (.xinitrc), change the names "stylus"... by the names you have in Ubuntu 9.04 with ```
xinput --list
```, and execute the script in Ubuntu 9.04.

---

### Post by mzuther on 2009-05-04
Hi Loïc2,

I didn't know that I could use **xsetwacom** without having the respective entries in **/etx/X11/xorg.conf**, so thanks a lot!

I was actually trying to set up my pad buttons.  Anyway, these entries worked for stylus and pad buttons:

```
xsetwacom set "Wacom Intuos3 6x8" Button1 "CORE KEY SPACE"
xsetwacom set "Wacom Intuos3 6x8pad " Button1 "CORE KEY SPACE"
```

The only thing I wonder is why I can't set keys to buttons using the **custom_wacom.fdi** method.  It would be nice to have all in one file, wouldn't it?

Thanks again,

Martin

---

### Post by shatterblast on 2009-05-07
The "xinput --list" seems to work for me as well though I found my information from this [thread at the Linux Wacom Project site]("http://sourceforge.net/mailarchive/forum.php?thread_name=cc6cabec0904250703t5dd70a81t39160dcbb62d1031%40mail.gmail.com&forum_name=linuxwacom-discuss").  For Jaunty 9.04, I replaced various entries like "pad" with ""Wacom Bamboo pad"" and "stylus" with ""Wacom Bamboo"".  I also used the custom_wacom.FDI method, but I don't think it's required when using the "xsetwacom" settings method within a SH script.

Here are the contents of my personal xsetwacom_settings.SH file in case it helps anyone:

```
xsetwacom set "Wacom Bamboo pad" AbsWDn "core key  CTRL  SHIFT s"
xsetwacom set "Wacom Bamboo pad" AbsWUp "core key  CTRL  SHIFT s"
xsetwacom set "Wacom Bamboo pad" Button4 "core key  NumpadMinus "
xsetwacom set "Wacom Bamboo pad" Button3 "core key  NumpadPlus "
xsetwacom set "Wacom Bamboo pad" Button2 "core key  F12 "
xsetwacom set "Wacom Bamboo pad" Button1 "CORE KEY  Esc"
xsetwacom set "Wacom Bamboo" Suppress "15"
xsetwacom set "Wacom Bamboo" RawSample "15"
xsetwacom set "Wacom Bamboo" ClickForce "5"
xsetwacom set "Wacom Bamboo" PressCurve "0 0 100 100"
xsetwacom set "Wacom Bamboo" Accel "1"
xsetwacom set "Wacom Bamboo" SpeedLevel "4"
xsetwacom set "Wacom Bamboo" TPCButton "off"
xsetwacom set "Wacom Bamboo" mode "Relative"
xsetwacom set "Wacom Bamboo" Button3 "Button 3"
xsetwacom set "Wacom Bamboo" Button2 "Button 2"
xsetwacom set "Wacom Bamboo" Button1 "Button 1"
xsetwacom set "Wacom Bamboo eraser" Suppress "15"
xsetwacom set "Wacom Bamboo eraser" RawSample "15"
xsetwacom set "Wacom Bamboo eraser" ClickForce "5"
xsetwacom set "Wacom Bamboo eraser" PressCurve "0 0 100 100"
xsetwacom set "Wacom Bamboo eraser" Accel "1"
xsetwacom set "Wacom Bamboo eraser" SpeedLevel "4"
xsetwacom set "Wacom Bamboo eraser" mode "Relative"
xsetwacom set "Wacom Bamboo eraser" Button1 "Button 1"
xsetwacom set "Wacom Bamboo cursor" Accel "1"
xsetwacom set "Wacom Bamboo cursor" SpeedLevel "4"
```

As similarly mentioned in posts above, I add the file to the list of things started when logging in.  To do so, I make sure the SH file is executable.  In Gnome, placing a check mark next to "Allow executing file as program" under the Permissions tab in the file Properties works.  Also, using something like "sudo chmod +x xsetwacom_settings.sh" in a Terminal (or command shell) screen works.  After that, I visit System -> Preferences -> Startup Applications.  I have an entry added that uses:

sh "/home/your_profile_name_here(case_sensitive)/Wacom Settings/xsetwacom_settings.sh"

Behavior for my Wacom tablet afterwards behaves the same in Jaunty 9.04 as it did Intrepid 8.10.  Disconnections of the tablet require that the SH file be ran again while still logged in.  I also assume the settings for "xsetwacom" might work in a custom_wacom.FDI file instead with a few changes, but I am happy for now.

---

### Post by Favux on 2009-05-07
Hi everyone,

As you have discovered it looks like the problems with wacomcpl and the xsetwacom commands come from the default Jaunty 10-wacom.fdi not parsing the names HAL is returning correctly for linuxwacom to understand.  Cyberfish came up with a .fdi that does parse the HAL names correctly and as modified by gali98 works for our usb tablet pc's.

I modified it for usb external graphics tablets.  K-buntu says it works on his Wacom Bamboo Fun.  Wacomcpl etc. work for him without having to rename anything.

You can configure everything through wacomcpl (& .xinitrc) and xsetwacom as before.  You can also configure through the .fdi like you use to do with xorg.conf.  If you do not have, for eg. the Wacom mouse, you could remove the append cursor line in the first section and the cursor section following it.

**1) For usb Wacom tablets in Jaunty and Karmic**:  Jaunty ext graphics_test 2_10-wacom.fdi.txt

Remember this modified 10-wacom.fdi is for the 0.8.2-2 linuxwacom packages that come "default" with Jaunty:  xserver-xorg-input-wacom & wacom-tools

It looks like the modified .fdi also works with Karmic.

Just move and save the default 10-wacom.fdi in /usr/share/hal/fdi/policy/20thirdparty/ somewhere safe (after changing .fdi to .bak say) and substitute the attached .fdi.  After renaming it 10-wacom.fdi of course.  One way to do this is the following:

-First download the attached .fdi to your desktop.
-Then make a back up of the current "default" Jaunty 10-wacom.fdi by typing in a terminal:
```
sudo cp /usr/share/hal/fdi/policy/20thirdparty/10-wacom.fdi /home/yourusername/Desktop/10-wacom.bak
```
In Karmic the .fdi has been renamed to 10-linuxwacom.fdi.  So to back up the "default" Karmic .fdi:
```
sudo cp /usr/share/hal/fdi/policy/20thirdparty/10-linuxwacom.fdi /home/yourusername/Desktop/10-linuxwacom.bak
```
Where "yourusername" is the user name you are using.  Check that the "wacom.bak" is now on your Desktop and has the correct contents by right clicking on it and 'Open as a "text file"'.  You can move it to wherever you want in Nautilus (Places) later.  Close it.
-Now open the current 10-wacom.fdi as root in gedit with:
```
gksudo gedit /usr/share/hal/fdi/policy/20thirdparty/10-wacom.fdi
```
In Karmic use:
```
gksudo gedit /usr/share/hal/fdi/policy/20thirdparty/10-linuxwacom.fdi
```
Delete the entire contents (its safe, you've verified your backup).  Now copy and paste the entire contents of the downloaded modified wacom.fdi (you can right click on it and open it in another text editor) save and close.
-Reboot.

Now "xinput --list" and "xsetwacom list" entered in a terminal should agree with each other and return the linuxwacom names stylus, eraser, cursor (if you have the Wacom mouse), pad (tablet buttons), and touch.  With "xsetwacom list" working you are now able to use 'wacomcpl', the LWP's configuration and calibration gui.  Just enter 'wacomcpl' (without the quotes) in a terminal and the gui will pop up.  To set it up so that it's settings last through a reboot see ["Section 3:  Calibrating your Tablet"]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").

Intuos4 tablet users need a 'wacom.ko' (the usb kernel driver/module) newer than the default Jaunty 0.8.2-2 wacom.ko.  The default one doesn't allow usb communication to your tablet.  To compile the new 'wacom.ko' follow Section 1, and Section 1 only, of gali98's [Jaunty HOW TO in post #104]("http://ubuntuforums.org/showpost.php?p=7093065&postcount=104").  In Karmic the default 0.8.4-1 linuxwacom wacom.ko works fine, no need to compile anything.

To further set up your pad see shatterblast's [post #188]("http://ubuntuforums.org/showpost.php?p=7281908&postcount=188") on the following page.  For the Intuous4 pad see also ceridwen's [post #95]("http://ubuntuforums.org/showpost.php?p=7327894&postcount=95") on another thread.  That's the Intuos4 thread, lots of tips in it.

**2) For serial Wacom tablets in Jaunty and Karmic**:  serial-tablet&tablet-pc_test2_10-wacom.fdi.txt

The serial .fdi attached below seems to work.  Same instructions as in 1) above.  Because there are new serial tablets I added them by modeling the serial section match lines in the linuxwacom 0.8.5-6 .fdi.  The new multi-touch tablets will need to use at least linuxwacom 0.8.5-6 (or up).  With all the new tablet identifiers I decided to merge the serial tablet and tablet pc .fdi's to make things simpler.  Older serial tablets probably need to remove or comment out this line:
```
	<merge key="input.x11_options.ForceDevice" type="string">ISDV4</merge>
```
(The serial-graphics-tablet_test1 .fdi had 48 downloads.)

**3) For all (serial & usb & bluetooth) Wacom tablets and tablet pc's in Jaunty and Karmic**:  new-generic_rc2_10-linuxwacom.fdi.txt

The new-generic release candidate attached below is my attempt to construct a .fdi that works for all the Wacom tablets.  It adds support for the TX2000 and TX2500 (finally) tablet pc's.  And also the new Bamboo Pen and Touches and the new HP dv3-2250 multi-touch laptop (E2) (use the current development branch linuxwacom 0.8.5-7 series drivers).  RC2 is out because of the new serial tablets, see 2) above.  It's been mainly tested in Karmic.  Hopefully it will work without too many glitches.  (The new-generic_rc1 .fdi had 43 downloads.)

I added some labels so things aren't so mysterious.  If you are interested in trying it the instructions are in 1) above.

**Note**:  With the last few versions of linuxwacom (~0.8.10 and up) wacomcpl was modified to deal with the longer more descriptive names and no longer needs stylus, eraser, cursor, pad, or touch.  This means you can remove the *merge key="info.product"* lines or the *<!-- Wacom names "parser" -->* section if you want to.

---

### Post by shatterblast on 2009-05-07
> **Favux said:**
> Hi everyone,

As you have discovered it looks like the problems with wacomcpl and the xsetwacom commands come from the default Jaunty 10-wacom.fdi not parsing the names HAL is returning correctly for linuxwacom to understand.  Cyberfish came up with a .fdi that does parse the HAL names correctly and as modified by gali98 works for our usb tablet pc's.

I modified it for usb external graphics tablets.  K-buntu says it works on his Wacom Bamboo Fun.  Wacomcpl etc. work for him without having to rename anything.

If you're interested please test it and let me know if it works for you.  You can configure everything through wacomcpl (& .xinitrc) and xsetwacom as before.  You can also configure through the .fdi like you use to do with xorg.conf.  If it works for you please mention which tablet you have.  If you do not have, for eg. the Wacom mouse, you could remove the append cursor line in the first section and the cursor section following it.

Just move and save the default 10-wacom.fdi in /usr/share/hal/fdi/policy/20thirdparty/ somewhere safe (after changing .fdi to .bak say) and substitute the attached .fdi.  After renaming it 10-wacom.fdi of course.

If the usb .fdi works for you maybe something analogous can be done with the serial tablet's subsection of the 10-wacom.fdi?

I can confirm that this file when used properly does indeed appear to allow the configuration in "wacomcpl" again for Jaunty 9.04 with a USB Wacom Bamboo.  I didn't follow instructions carefully, which caused my GUI problems with the  Wacom tablet connected.  I corrected my mistake and had success after reading thoroughly.

---

### Post by Favux on 2009-05-07
Hi shatterblast, ubootfant, Sawer, crazybus, nebux, jjatria

Thanks for testing the .fdi.  Glad it worked for you.


So that's 12 Wacom tablets, 5 Bamboo's, a Bamboo Fun, a Cintiq 21UX, a Graphire2, and 4 Intuous4's it has worked for.  Looking good so far!

-The Cintiq 21UX user said it also fixed the TwinView problem he had been having.
-For the Intuos4 we had to substitute a newer (0.8.3-3) wacom.ko (the usb kernel driver) to get it working.  To get the Pad working see post #95 by ceridwen here:  [http://ubuntuforums.org/showthread.php?t=1120029&page=10](http://ubuntuforums.org/showthread.php?t=1120029&page=10)
-The Graphire2 user said everything worked except wacdump (a general HAL/.fdi problem?)

---

### Post by shatterblast on 2009-05-08
Mine is not a "Fun", but it is compatible with it.

---

### Post by Sawer on 2009-05-11
I'm  lost. How to I  put  the express key script in /etc/init.d and chmod +x? I do graphics stuff and an not much of a hacker.
Thanks

---

### Post by ubootfanat on 2009-05-12
Hi!

Solution of Favux works for my Wacom Bamboo on 9.04 also.

Still no fifth button recognized by X -> no scrolling
Giving a key mapping directly in .fdi does not work either

sl
ubootfanat

---

### Post by shatterblast on 2009-05-13
> **Sawer said:**
> I'm  lost. How to I  put  the express key script in /etc/init.d and chmod +x? I do graphics stuff and an not much of a hacker.
Thanks

To Sawer:

I ignored that part if you read my version of it in this post:

[http://ubuntuforums.org/showpost.php?p=7232505&postcount=175](http://ubuntuforums.org/showpost.php?p=7232505&postcount=175)

You might try using Favux's FDI file for simplicity, but please read directions carefully.  After that, try using "wacomcpl" from Applications -> Accessories -> Terminal (if you use Gnome).  It produces a configuration file.  Just rename that file into an .SH file if you want.  After that, put a command-line for it as "sh /folder_stuff/config_file_name.SH" in System -> Preferences -> Startup Applications.

You don't need to put that file into "/init.d/".

> **ubootfanat said:**
> Hi!

Solution of Favux works for my Wacom Bamboo on 9.04 also.

Still no fifth button recognized by X -> no scrolling
Giving a key mapping directly in .fdi does not work either

sl
ubootfanat

To ubootfanat:

Have you tried "wacomcpl" from a command shell / Terminal yet?  Maybe you will find the "fifth" button setting there?

---

### Post by ubootfanat on 2009-05-14
yes I tried all of that.

wacomcpl and xsetwacom show a correct mapping of the scroll wheel to button 4 and 5. but X does not recognize button5.

again a few details:
[LIST]
[*]xev shows buttons 1-4. the button5-mapped scrollwheeldirection does only show motion events.
[*]```
$ xinput list
...
"pad"	id=10	[XExtensionKeyboard]
Num_keys is 248
Min_keycode is 8
Max_keycode is 255
Num_buttons is 4   <--- whats that?
Num_axes is 6
...

```
[/LIST]

any ideas how (and where) hal adds the devices to xinput? maybe theres a bug there which only detects/reports 4 buttons of the pad.

thanks in the meanwhile
ubootfanat

---

### Post by Favux on 2009-05-14
Hi ubootfanat,

What's button4 (the scroll wheel up I guess) set to?

I wonder what happens if you add button5 to the pad section:
```
  <device>
    <match key="input.x11_options.Type" contains="pad">
      <merge key="info.product" type="string">pad</merge>
      <merge key="input.x11_options.Button5" type="string">5</merge>
    </match>
  </device>
```
It seems to me I've seen or there used to be a command something like "ButtonNo"   "5".  But I don't see it in the LWP HOW TO.  Maybe it's an Xinput command?

---

### Post by ubootfanat on 2009-05-14
thanks for replying. I tried all of that:

```

<merge key="input.x11_options.Button5" type="string">5</merge>
<merge key="input.x11_options.AbsWDn" type="string">5</merge>
<merge key="input.x11_options.RelWDn" type="string">5</merge>

```

still there is no button5 recognized by X.

I am wondering how xinput knows how many buttons are available for each input device. I have not found that info up to now. may it be part of the driver?

is there anyone else with a wacom bamboo and a missing scroll-event?

sl ubootfanat

---

### Post by Favux on 2009-05-14
Hi ubootfanat,

You may be right.  I know it is partly through a chain of .fdi's that are upstream of 10-wacom.fd.  For example the 10-TablePC.fdi in osvendor.  So maybe a .fdi upstream?  But the linuxwacom driver not covering a newish feature yet sounds possible too.  The development branch is up to 0.8.3-4 after all.  And Ron posted new udev rules about a month ago that included the Intuos4 etc.

---

### Post by Sawer on 2009-05-14
Still can't get my pad to work with my bamboo fun. wacomcpl shows up but  doesn't give options  for stylus.eraser,pad etc. The stylus works fine as a pointing device just the pad doesn't work. This is a real bummer.

---

### Post by shatterblast on 2009-05-15
> **ubootfanat said:**
> thanks for replying. I tried all of that:

```

<merge key="input.x11_options.Button5" type="string">5</merge>
<merge key="input.x11_options.AbsWDn" type="string">5</merge>
<merge key="input.x11_options.RelWDn" type="string">5</merge>

```

still there is no button5 recognized by X.

I am wondering how xinput knows how many buttons are available for each input device. I have not found that info up to now. may it be part of the driver?

is there anyone else with a wacom bamboo and a missing scroll-event?

sl ubootfanat

To ubootfanat:

How about going into Terminal and put in the below two lines?

xsetwacom set pad AbsWDn "core key  NumpadPlus "
xsetwacom set pad AbsWUp "core key  NumpadPlus "

Please report if you get an error message.  If the device is undetected, then you should get messages that mentions such.  Otherwise if you get no messages, try using your circular touch pad to see if you get "+" symbols.

Something I didn't mention is that I could revert to my original settings with Favux's FDI file.  It looks more like this:

```
xsetwacom set pad AbsWDn "core key  CTRL  SHIFT s"
xsetwacom set pad AbsWUp "core key  CTRL  SHIFT s"
xsetwacom set pad Button4 "core key  NumpadMinus "
xsetwacom set pad Button3 "core key  NumpadPlus "
xsetwacom set pad Button2 "core key  F12 "
xsetwacom set pad Button1 "CORE KEY  Esc"
xsetwacom set stylus Suppress "15"
xsetwacom set stylus RawSample "15"
xsetwacom set stylus ClickForce "5"
xsetwacom set stylus PressCurve "0 0 100 100"
xsetwacom set stylus Accel "1"
xsetwacom set stylus SpeedLevel "4"
xsetwacom set stylus TPCButton "off"
xsetwacom set stylus mode "Relative"
xsetwacom set stylus Button3 "Button 3"
xsetwacom set stylus Button2 "Button 2"
xsetwacom set stylus Button1 "Button 1"
xsetwacom set eraser Suppress "15"
xsetwacom set eraser RawSample "15"
xsetwacom set eraser ClickForce "5"
xsetwacom set eraser PressCurve "0 0 100 100"
xsetwacom set eraser Accel "1"
xsetwacom set eraser SpeedLevel "4"
xsetwacom set eraser mode "Relative"
xsetwacom set eraser Button1 "Button 1"
xsetwacom set cursor Accel "1"
xsetwacom set cursor SpeedLevel "4"
```

Else in a previous post, my settings worked properly without Favux's FDI file.

[http://ubuntuforums.org/showpost.php?p=7232505&postcount=175](http://ubuntuforums.org/showpost.php?p=7232505&postcount=175)

---

### Post by shatterblast on 2009-05-15
> **Sawer said:**
> Still can't get my pad to work with my bamboo fun. wacomcpl shows up but  doesn't give options  for stylus.eraser,pad etc. The stylus works fine as a pointing device just the pad doesn't work. This is a real bummer.

To Sawer:

Have you downloaded the FDI file from Favux yet?

[http://ubuntuforums.org/showpost.php?p=7234134&postcount=176](http://ubuntuforums.org/showpost.php?p=7234134&postcount=176)

Please make sure to rename it to:

10-Wacom.FDI

You can do this by right clicking on the file, erasing the entire name, and then just putting the new name in.  We can proceed after.

---

### Post by Sawer on 2009-05-15
shatterblast: Thanks I now have  my pad working sort of. The scroll ring only works  one way (up). how do I get this changed and how to I access wacomcpl? It shows up but it doesn't give me any options.
One of biggest problems is  finding the  files  to edit, I've done  searches for them but  don't find  any that can be edited.
As I've stated in other posts I'm not much of a geek, I do graphics stuff more than anything else, so please keep it as simple as possible.
It appears that the device is not found in wacomcpl or xsetwacom.
Thanks

---

### Post by shatterblast on 2009-05-15
> **Sawer said:**
> shatterblast: Thanks I now have  my pad working sort of. The scroll ring only works  one way (up). how do I get this changed and how to I access wacomcpl? It shows up but it doesn't give me any options.
One of biggest problems is  finding the  files  to edit, I've done  searches for them but  don't find  any that can be edited.
As I've stated in other posts I'm not much of a geek, I do graphics stuff more than anything else, so please keep it as simple as possible.
It appears that the device is not found in wacomcpl or xsetwacom.
Thanks

I'll assume you downloaded and renamed the FDI file from Favux.  I double-checked the file name, and it should be all lower case instead of the capital letters I suggested.  It should be:

10-wacom.fdi

For making things easy, we want this file on the "Desktop."  If it helps, you can go to:

Places -> Desktop -> ensure 10-wacom.fdi exists

Next, we require Terminal for copying the file to the target folder.  In Gnome, this can be found under Applications -> Accessories.  Type the following:

cd Desktop

You should see the prompt end with:

~/Desktop$

After that, type:

dir

Again, one of the files should be 10-wacom.fdi.  When all looks good, the next command is:

sudo cp 10-wacom.fdi /usr/share/hal/fdi/policy/20thirdparty/

The copy and paste functions help to avoid typing it out.  The previous command should cause a request for your password.  After it accepts the password, just reboot the computer.  Hopefully, "wacomcpl" will show some devices now.  If so, you can take the next steps of tweaking your tablet the way you like.

---

### Post by Sawer on 2009-05-16
Shatterblast:  I followed your instructions but end  up the same as before, no device showing in wacomcpl. It's acting like there isn't a driver installed, I've reinstalled the wacom packages synaptic with  no luck. My tablet shows up in /dev/input/by id, it also shows if I do lsmod. I hope you  have an other idea, thanks for your input and help.
Success yeh. I  got to thinking maybe something I had done messing with xorg and such might have  messed up everything. I reinstalled / and it works.
Thanks for all your help.

---

### Post by Sawer on 2009-05-16
I've been looking for the  past 2 hours  on how to get the scroll circle to work in bamboo. Most of what I read is in a foreign language. Would someone please help me decipher these?
Thanks

---

### Post by shatterblast on 2009-05-16
To Favux:

I'm starting to think a .DEB file should be made that includes the FDI file.  It might make installing the file easier.  Or maybe a script could be made that renames the original with a .BAK extension.  If so, another script could probably exist to restore the original.  I could also put something together with a bit of Java that gives the option of running two scripts like that.

---

### Post by shatterblast on 2009-05-16
> **Sawer said:**
> I've been looking for the  past 2 hours  on how to get the scroll circle to work in bamboo. Most of what I read is in a foreign language. Would someone please help me decipher these?
Thanks

xsetwacom set pad AbsWDn "core key NumpadPlus "
xsetwacom set pad AbsWUp "core key NumpadPlus "

I use these two lines in a script.  You can just replace NumpadPlus with whatever else.  You might use Wacomcpl to check what keys are assigned to what.

---

### Post by crazybus on 2009-05-17
I just got a intuos4 and it's listed in lsusb.  But it doesn't seem to do anything.  Not just the buttons but stylus as well.  I installed the custom .fdi above but that doesn't seemed to have helped.  As well as rebooted.  Any ideas?

---

### Post by Favux on 2009-05-17
Hi crazybus,

You will need to install the 0.8.3-3 wacom.ko.  Just the wacom.ko.  Do that part of the HOW TO on post #104 here:  [http://ubuntuforums.org/showthread.php?t=1038949&page=11](http://ubuntuforums.org/showthread.php?t=1038949&page=11)

That should get it working.

Hi shatterblast,

That sounds like a good idea if wacom in Jaunty will remain stable.  Except things may be in flux.  Maybe I should just improve the instructions?

---

### Post by crazybus on 2009-05-17
I copied the ko file and restarted but it still doesn't seem to work anyway.  Should I restore the original .fdi file or do something else?  Thanks so much in advance Favux

---

### Post by Favux on 2009-05-17
Hi crazybus,

You may need to add "wacom" to "/etc/modules" as in post #3 here:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)

---

### Post by crazybus on 2009-05-17
Thanks again.  With a restart it got it working.  However wacomcpl doesn't have any items in it.  I need the config file to make the tablet not be backtofront (cause I'm using it lefthanded) or so I assume after reading the forum.

---

### Post by Favux on 2009-05-17
Hi crazybus,

Good, you've got input from the tablet.  It sounds like you do not have the new .fdi correctly installed.

Is:
```
xsetwacom list
```
empty?  What do you see with?:
```
xinput --list
```
So you might want to check that over again.

For left-handed use see posts #76 and #80 on this thread where other Intuos4 users are:  [http://ubuntuforums.org/showthread.php?t=1120029&page=8](http://ubuntuforums.org/showthread.php?t=1120029&page=8)  Sanette in #80 has a good fix if your planning on only using the table lefthanded.

---

### Post by crazybus on 2009-05-17
xsetwacom list produces nothing

xinput --list gives this

"Wacom Intuos4 4x6"	id=7	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 7
	Num_axes is 6
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 31496
		Resolution is 1016
	Axis 1 :
		Min_value is 0
		Max_value is 19685
		Resolution is 1016
	Axis 2 :
		Min_value is 0
		Max_value is 2047
		Resolution is 1
	Axis 3 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 4 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 5 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
"Wacom Intuos4 4x6 pad"	id=8	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 7
	Num_axes is 6
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 31496
		Resolution is 1016
	Axis 1 :
		Min_value is 0
		Max_value is 19685
		Resolution is 1016
	Axis 2 :
		Min_value is 0
		Max_value is 2047
		Resolution is 1
	Axis 3 :
		Min_value is 0
		Max_value is 0
		Resolution is 1
	Axis 4 :
		Min_value is 0
		Max_value is 0
		Resolution is 1
	Axis 5 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
"Wacom Intuos4 4x6 cursor"	id=9	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 7
	Num_axes is 6
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 31496
		Resolution is 1016
	Axis 1 :
		Min_value is 0
		Max_value is 19685
		Resolution is 1016
	Axis 2 :
		Min_value is 0
		Max_value is 2047
		Resolution is 1
	Axis 3 :
		Min_value is -900
		Max_value is 899
		Resolution is 1
	Axis 4 :
		Min_value is -1023
		Max_value is 1023
		Resolution is 1
	Axis 5 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
"Wacom Intuos4 4x6 eraser"	id=10	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 7
	Num_axes is 6
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 31496
		Resolution is 1016
	Axis 1 :
		Min_value is 0
		Max_value is 19685
		Resolution is 1016
	Axis 2 :
		Min_value is 0
		Max_value is 2047
		Resolution is 1
	Axis 3 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 4 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 5 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1

---

### Post by Favux on 2009-05-17
Hi crazybus,

Please either box your output above in code tags (press the # above the text entry area when you're in Advanced) or delete it.

The .fdi is not installed correctly.  Your stylus is being seen as "Wacom Intuos4 4x6", and it is the prefix to the rest of your devices like pad.

I'll go improve the instructions for the .fdi on page 18 post #176.

---

### Post by crazybus on 2009-05-17
I'm not sure where I went wrong in copying it but I've fixed it now.

xsetwacom list gives

eraser           eraser    
cursor           cursor    
pad              pad       
stylus           stylus   

Thanks you SO much for all your help ):P

---

### Post by Favux on 2009-05-18
Hi crazybus,

Good job!  Nice work.  Are the entries really duplicated like that?  Does wacomcpl work?  See Section 3 here to use wacomcpl:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)

I'm worried you may have another wacom.fdi.

---

### Post by RyanGT on 2009-05-19
Thanks for this thread and all the hard work to make Wacom pads work in Linux.  I am running Jaunty and my Bamboo pad worked out-of-the box.  I modified the .fdi file according to post #176 and can now use wacomcpl to configure the keys on my pad.  Nice.

I have one more thing I would like to get working.  I don't know if this is a Wacom issue or a Gimp issue, but in windows, the eraser and stylus are automatically recognized as two different things and once I choose the eraser to be set up as Gimp's eraser, I can just flip the stylus over and erase.  I flip it back over and it automatically becomes the paintbrush I had associated with the stylus.  The two even have different brushes associated with them.  So far, in Jaunty, I have to manually switch to the eraser and change the brush size.  Can I make Gimp automatically recognize the two in Ubuntu?  Is this a Wacom setting or a Gimp one?  Does my question make sense?

Thanks,

Ryan

---

### Post by jschneider on 2009-05-19
My wacom tablet is working - out of the box. Thanks for everybody.

But (there is always a "but") clicking is *muuuch* too sensitive.
I tried to change nearly every paramter but very often a click happens while the pen is hovering *above* the tablet...

This is very annoying and working with the tablet is impossible.

Does anyone have a working wacom.fdi for that problem?

---

### Post by Gemnoc on 2009-05-19
@ RyanGT

Have you configured your Bamboo in Gimp as shown [in the wiki]("https://help.ubuntu.com/community/Wacom#Gimp")?

After you first select the eraser tool for your stylus' eraser in Gimp, it should be recognized afterwards, just like in Gimp for Windows.

If it doesn't, you can also go to the menu (not sure of the exact terms as my OS is in French) Windows/dockable windows/Device Status, and force the Wacom eraser to have the eraser tool as its default tool.

Hope it made sense...

---

### Post by Favux on 2009-05-19
Hi jschneider,

Have you calibrated with wacomcpl yet?  If not see Section 3 here:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)

It sounds like in the file wacomcpl generates, .xinitrc, you do not have this line:
```
xsetwacom set stylus TPCButton "on"
```
To check if I am correct just type it in a terminal and see if your stylus then behaves.

---

### Post by nebux on 2009-05-25
> **Favux said:**
> Hi everyone,

As you have discovered it looks like the problems with wacomcpl and the xsetwacom commands come from the default Jaunty 10-wacom.fdi not parsing the names HAL is returning correctly for linuxwacom to understand.  Cyberfish came up with a .fdi that does parse the HAL names correctly and as modified by gali98 works for our usb tablet pc's.

I modified it for usb external graphics tablets.  K-buntu says it works on his Wacom Bamboo Fun.  Wacomcpl etc. work for him without having to rename anything.

If you're interested please test it and let me know if it works for you.  You can configure everything through wacomcpl (& .xinitrc) and xsetwacom as before.  You can also configure through the .fdi like you use to do with xorg.conf.  If it works for you please mention which tablet you have.  If you do not have, for eg. the Wacom mouse, you could remove the append cursor line in the first section and the cursor section following it.

Remember this modified 10-wacom.fdi is for the 0.8.2-2 linuxwacom packages that come "default" with Jaunty.

Just move and save the default 10-wacom.fdi in /usr/share/hal/fdi/policy/20thirdparty/ somewhere safe (after changing .fdi to .bak say) and substitute the attached .fdi.  After renaming it 10-wacom.fdi of course.

-First download the attached .fdi to your desktop.
-Then make a back up of the current "default" Jaunty 10-wacom.fdi by typing in a terminal:
```
sudo cp /usr/share/hal/fdi/policy/20thirdparty/10-wacom.fdi /home/yourusername/Desktop/10-wacom.bak
```
Where "yourusername" is the user name you are using.  Check that the "wacom.bak" is now on your Desktop and has the correct contents by right clicking on it and 'Open as a "text file"'.  You can move it to wherever you want in Nautilus (Places) later.  Close it.
-Now open the current 10-wacom.fdi as root in gedit with:
```
gksudo gedit /usr/share/hal/fdi/policy/20thirdparty/10-wacom.fdi
```
Delete the entire contents (its safe, you've verified your backup).  Now copy and paste the entire contents of the downloaded modified wacom.fdi (you can right click on it and open it in another text editor) save and close.
-Reboot.

If the usb .fdi works for you maybe something analogous can be done with the serial tablet's subsection of the 10-wacom.fdi? this solution works for me. i just brought an wacom bamboo and now i need to test it better. anyway wacomcpl works

---

### Post by Sawer on 2009-05-26
Still can't get the circle  to move down in my bamboo fun. I don't know how to get into xsetwacom. Is there there an easy way to get this to  work? Please give very  instructions.
Thanks

---

### Post by pointym5 on 2009-06-01
Hi. I've got a Jaunty installation on an HP dv7t laptop.  I've just taken delivery on an Intuos 4, and it seems to not work at all. I'm not really sure where to start because I can't match up what I've seen (which is pretty much nothing) with all the diagnostics reported in this thread. The thing powers up, and since it's brand new out of the box I'm going to assume that it's functional.

I've got the 2 wacom packages installed.

The system sees the device when it's plugged in, and lsusb sees it with ID 056a:00b8.

All this talk about the tablets working "out of the box" - what does "working" mean? What should I be seeing if thing's working properly? What are the diagnostic steps I can take?

---

### Post by Favux on 2009-06-01
Hi pointym5,

It turns out that the Intuos4 is so new that the 0.8.2-2 linuxwacom drivers don't support it.  The 0.8.3 linuxwacom series is when Intuos4 support was added.  That's why it seems active but nothing happens.  After a little experimenting we discovered all we needed to do was substitute a 0.8.3 wacom.ko for the 0.8.2-2 wacom.ko and the tablet would work.  So see post #63 here:  [http://ubuntuforums.org/showthread.php?t=1120029&page=7](http://ubuntuforums.org/showthread.php?t=1120029&page=7)  and follow the instructions.  Then if you skim through the rest of the Intuos4 thread I think you'll find we answer most questions you'll have.

---

### Post by pointym5 on 2009-06-02
> **Favux said:**
> Hi pointym5,

It turns out that the Intuos4 is so new that the 0.8.2-2 linuxwacom drivers don't support it.  The 0.8.3 linuxwacom series is when Intuos4 support was added.  That's why it seems active but nothing happens.  After a little experimenting we discovered all we needed to do was substitute a 0.8.3 wacom.ko for the 0.8.2-2 wacom.ko and the tablet would work.  So see post #63 here:  [http://ubuntuforums.org/showthread.php?t=1120029&page=7](http://ubuntuforums.org/showthread.php?t=1120029&page=7)  and follow the instructions.  Then if you skim through the rest of the Intuos4 thread I think you'll find we answer most questions you'll have.

OK thanks.

Just an advisory note - when you link to posts in threads, be aware that not everybody has the same posts-per-page setting. For example, post number 63 in that thread is not on page 7 based on my (default) forum settings.

---

### Post by pointym5 on 2009-06-02
My new Intuos4 still does not work properly at all with Jaunty, and I'm having a terribly difficult time following all these links from thread to thread and from forum to forum.  I've been using Unix/Linux for 25 years now so I have no problems with basic things like editing configuration files etc, but it's just not clear to me what file does what, what command does what, nor where any sort of documentation on any of these things can be found.

Here's my xinput --list - looks a lot like one from earlier in this thread, but the explanation of what to do about it makes no sense at all to me:
```

"Wacom Intuos4 4x6 eraser"      id=8    [XExtensionKeyboard]
        Num_keys is 248
        Min_keycode is 8
        Max_keycode is 255
        Num_buttons is 7
        Num_axes is 6
        Mode is Absolute
        Motion_buffer is 256
        Axis 0 :
                Min_value is 0
                Max_value is 31496
                Resolution is 1016
        Axis 1 :
                Min_value is 0
                Max_value is 19685
                Resolution is 1016
        Axis 2 :
                Min_value is 0
                Max_value is 2047
                Resolution is 1
        Axis 3 :
                Min_value is -64
                Max_value is 63
                Resolution is 1
        Axis 4 :
                Min_value is -64
                Max_value is 63
                Resolution is 1
        Axis 5 :
                Min_value is 0
                Max_value is 1023
                Resolution is 1
"Wacom Intuos4 4x6 cursor"      id=9    [XExtensionKeyboard]
        Num_keys is 248
        Min_keycode is 8
        Max_keycode is 255
        Num_buttons is 7
        Num_axes is 6
        Mode is Relative
        Motion_buffer is 256
        Axis 0 :
                Min_value is 0
                Max_value is 31496
                Resolution is 1016
        Axis 1 :
                Min_value is 0
                Max_value is 19685
                Resolution is 1016
        Axis 2 :
                Min_value is 0
                Max_value is 2047
                Resolution is 1
        Axis 3 :
                Min_value is -900
                Max_value is 899
                Resolution is 1
        Axis 4 :
                Min_value is -1023
                Max_value is 1023
                Resolution is 1
        Axis 5 :
                Min_value is 0
                Max_value is 1023
                Resolution is 1
"Wacom Intuos4 4x6 pad" id=10   [XExtensionKeyboard]
        Num_keys is 248
        Min_keycode is 8
        Max_keycode is 255
        Num_buttons is 7
        Num_axes is 6
        Mode is Relative
        Motion_buffer is 256
        Axis 0 :
                Min_value is 0
                Max_value is 31496
                Resolution is 1016
        Axis 1 :
                Min_value is 0
                Max_value is 19685
                Resolution is 1016
        Axis 2 :
                Min_value is 0
                Max_value is 2047
                Resolution is 1
        Axis 3 :
                Min_value is 0
                Max_value is 0
                Resolution is 1
        Axis 4 :
                Min_value is 0
                Max_value is 0
                Resolution is 1
        Axis 5 :
                Min_value is 0
                Max_value is 1023
                Resolution is 1
"Wacom Intuos4 4x6"     id=11   [XExtensionKeyboard]
        Num_keys is 248
        Min_keycode is 8
        Max_keycode is 255
        Num_buttons is 7
        Num_axes is 6
        Mode is Absolute
        Motion_buffer is 256
        Axis 0 :
                Min_value is 0
                Max_value is 31496
                Resolution is 1016
        Axis 1 :
                Min_value is 0
                Max_value is 19685
                Resolution is 1016
        Axis 2 :
                Min_value is 0
                Max_value is 2047
                Resolution is 1
        Axis 3 :
                Min_value is -64
                Max_value is 63
                Resolution is 1
        Axis 4 :
                Min_value is -64
                Max_value is 63
                Resolution is 1
        Axis 5 :
                Min_value is 0
                Max_value is 1023
                Resolution is 1

```

The output of "wacdump" indicates to me that the tablet is not connected properly.

Here's one direct question: do the .fdi files need to go under /usr/share or in /etc/hal? 

Another question: if one is tweaking an fdi file, how do you know what to match on?  In other words, where is the stuff that those matching rules match coming from?  How can one look at it?  Where are all the various switches and parameters defined - is that a per-application thing?

Once I get this figured out I'd be happy to help (to the degree I'm capable) in updating the "How-To", because the current Jaunty section claiming that the tablets "just work" seems a little optimistic, given the existence of this long, complicated thread.  It seems many of them don't just work, and so having the diagnostic steps laid out clearly in the how-to would be much preferable to having to wind through all these (helpful, to be sure) threads.

---

### Post by pointym5 on 2009-06-02
> **Favux said:**
> Hi crazybus,

Good job!  Nice work.  Are the entries really duplicated like that?  Does wacomcpl work?  See Section 3 here to use wacomcpl:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)

I'm worried you may have another wacom.fdi.

I've just re-tried dropping your .fdi file into /usr/share, and now it seems to work similarly to what crazybus reported.  Wacomcpl works (well, I guess it works) and I don't have more than one .fdi file anywhere.

My Intuos 4 mouse doesn't work properly at all.  If I fiddle with the "wheel" gadget on the tablet (is that the "pad" device?), then the mouse works OK - right until I pick it up.  After that, it only causes mouse movement when it's above the tablet - in other words, if I slide it on the tablet, nothing happens, but when I pick it up, the cursor moves.

---

### Post by Favux on 2009-06-02
Hi pointym5,

Wow!  You've been busy.  I don't know what's wrong.

Basically the whole idea is to allow usb hotplugging.  That's what all the HAL .fdi stuff is about.

First no one is getting anything from wacdump now as far as I know.  So that's a red herring.  Ping Cheng at the LWP says once wacom_drv.so grabs the tablet, nothing else can access it. You can run wacdump before X starts. Or run xidump before wacomcpl starts.

The wacom.ko (0.3.8-5?) seems to be working.  In your xinput output before you used the new .fdi:
stylus = "Wacom Intuos4 4x6"
eraser = "Wacom Intuos4 4x6 eraser"
cursor = "Wacom Intuos4 4x6 cursor"
pad = "Wacom Intuos4 4x6 pad"

So "xsetwacom list" would be empty and wacomcpl wouldn't work.  You could rename the wacom devices in .xinitrc and then wacomcpl should work like they were doing on the Wacom thread.  You used the .fdi.  Wacomcpl now seems to work and is generating a .xinitrc.  Configuration options from the LWP HOWTO are here:  [http://linuxwacom.sourceforge.net/index.php/howto/xsetwacom](http://linuxwacom.sourceforge.net/index.php/howto/xsetwacom)
You may need to set:
```
CursorProx    integer (distance)       sets cursor distance margin for proximity-out 
				          in distance from the tablet surface

```

Or is there something else going on?  After 0.8.3-2 and 0.8.3-3 wacom.ko is there a problem?  With 0.8.3-4 and/or 0.8.3-5 do we need to do something different?  Another Intuos4 user reported TwinView didn't work for him until he added the wacom_drv.so from the compile where he got his wacom.ko.

---

### Post by Sawer on 2009-06-02
I now have my scroll ring working as it should. What I did was change the settings to button 4  to up in keystroke and button 5 to down in keystroke. Now my question is how to I get the settings to stick? My /home/scott/xinit/xinitirc is showing the right settings.

---

### Post by Favux on 2009-06-02
Hi Sawer,

Good deal.

Did you make the .xinitrc executable and add it to Startup Applications like it says in Section 3 here?:  [http://ubuntuforums.org/showthread.php?p=6546012#post6546012](http://ubuntuforums.org/showthread.php?p=6546012#post6546012)

---

### Post by pointym5 on 2009-06-02
I can't see that wacomcpl writes anything anywhere; it's certainly not giving me a .xinitrc file.

What does the button configuration screen mean?  In other words, what actual physical button is "button 1" (and the rest)? What is "slide switch mode"?  By asking these questions I think what I really mean is, is that stuff written down anywhere?

If I were to change that CursorProx thing, what would I set it to?  Would I do it to the "cursor" device?  Setting it to random numbers like 0 or 1 have no effect (though I can get the setting back and verify that it "took").

[edit]
When I set CursorProx to 255 (the maximum), then the mouse works differently. At that setting, it keeps working but in order to use it like a mouse - that is, to be able to pick it up, shift it across the surface of the tablet, and put it back down without the cursor moving in the meantime - well I have to lift the mouse way up in the air (like a few inches off the surface).  Repeated attempts got the number down to about 45, but I still have to lift the mouse pretty high off the surface so it's not really comfortable to use. It's almost as if there should be two numbers for devices like the mouse to bound the proximity from both directions. (In other words, the mouse should only operate when it's within a fairly tight fixed distance from the tablet.)  Of course I know basically nothing about the way the tablet and the driver work, so that may make no sense.

---

### Post by Favux on 2009-06-02
Hi pointym5,

The .xinitrc is a hidden file in your /home/username directory so in Nautilus you have to click View Hidden Files.  I'm sure you know that so is wacomcpl not working?  Typed in a terminal does the gui pop up?

Anyway ceridwen gives a mini tutorial on post #95 here:  [http://ubuntuforums.org/showthread.php?t=1120029&page=10](http://ubuntuforums.org/showthread.php?t=1120029&page=10)

And sanette and Lazarusrat are trying to configure everything in the .fdi.  Here's Lazarusrat's .fdi on post #73 here:  [http://ubuntuforums.org/showthread.php?t=1035029&page=8](http://ubuntuforums.org/showthread.php?t=1035029&page=8)

I was hoping you would be able to see a default CursorProx setting in you .xinitrc and go from there.  Other than whatever Wacom includes with the tablet for setting up in Windows the only "manual" is the LWP's HOWTO and stuff you can find on the web.

Maybe we should continue posting on the Intuos4 thread?  That's probably where the most help is.  I'm not sure they follow this thread.

---

### Post by Jakeyxu on 2009-06-02
> **Loïc2 said:**
> Read the guide carefully, then the first post in this thread. In no way do we advise you to go and compile linuxwacom. In 99.9% of the cases, your hardware will be supported by the default wacom drivers provided by Intrepid (they're about same as compiling them from the file you downloaded).
 
If you type this in a terminal:
sudo dpkg -p wacom-tools | grep Version
You'll see that the version in Intrepid is 8.1.4, which isn't much different than your downloaded 8.1.6 in terms of hw support. Actually, it's newer than the Linux Wacom Project (LWP) official 8.0, which they say already support touch for tablets.
 
Now, with tablets PC in Intrepid the problem you're facing is a problem of configuration - compiling a driver won't help.
 
Explanation : the default configuration for Intrepid works for hotpluggable tablets. With a tablet PC, the wacom device is always there, and that's the problem (it won't be recognised).
 
I'm not an expert, but from what I've see people report in bug threads, for Tablet PC the best (maybe even the only) solution is to revert to the old way to configure wacom devices, that is editing /etc/X11/xorg.conf .[size=1][walk in tub](http://www.walk-in-tub.cc)[/size] That is a bit risky, so make sure you have two operanting system installed (the best is to have another Ubuntu installed on another partition, for example an LTS version like Ubuntu 8.04) so you can access the net and ask for help here if you hosed X. Having another Ubuntu would also allow you to continue any urgent and important work during the few hours / days it takes for one of us to reply to any problem you would have (there's time we'll be sleeping or away for the computer ;) ).
 
So read the guide carefully, you want the Option B) in Intrepid. I've updated the example configuration files at [https://help.ubuntu.com/community/WacomTroubleshooting](https://help.ubuntu.com/community/WacomTroubleshooting) with a warning for Tablet PC users, I'll edit the guide too (and maybe copy/paste this post at the beginning of the thread.
 
If you don't manage to configure it, please tell us. If you manage to get it to work, please tell us too, since I don't have any Tablet Pc to check if my advices really work.
 
 
ohhhhh ...
I also think so...

---

### Post by Sawer on 2009-06-02
I have kde 3 interpid installed, so far I haven't been able to find startup applications. I'm getting tired well look somemore tomorrow.
Thanks for the input.

---

### Post by Dave M G on 2009-06-02
In previous versions of Ubuntu, I had my xorg.conf file set up so that my Wacom tablet was exactly how I like it.

In particular, I had it so that the pen would only work in one of my two monitors. In xorg.conf, the relevant lines looked like this (edited down a bit just to show the important sections):

```
Section "InputDevice"
Identifier     "stylus"
Option         "Twinview" "Horizontal"
Option         "ScreenNo" "0"
```

But now, those lines have been commented out by "HAL", like so:

```
# commented out by update-manager, HAL is now used
#Section "InputDevice"
#Identifier     "stylus"
#Option         "Twinview" "Horizontal"
#Option         "ScreenNo" "0"
```

HAL works fine mostly. My Wacom has pressure sensitivity and works mostly as I would expect.

But my pen (the stylus and eraser) is no longer constrained to one monitor as I would like.

After some research, I found I need to edit a "wacom.fdi" file.

I already have one at **/usr/share/hal/fdi/policy/20thirdparty/10-wacom.fdi**, but the online help says I should create one at **/etc/hal/fdi/policy/custom_wacom.fdi** and delete the old one. The **10-wacom.fdi** file has some default settings in it. The **custom_wacom.fd**i file doesn't exist yet.

While it pains me that I have to now embark on a whole new learning process after spending ages getting Wacom tablets to work with the old system, I guess I have no choice.

So my questions are:

Which fdi file do I use?

What setting do I put in them to emulate the xorg.conf file settings above.

Thank you for any advice.

---

### Post by Favux on 2009-06-02
Hi Dave M G,

See Lazarusrat's .fdi in the link in post #221 above.  He has some TwinView lines entered into his .fdi that may help you.

---

### Post by pointym5 on 2009-06-02
> **Favux said:**
> Hi pointym5,

The .xinitrc is a hidden file in your /home/username directory so in Nautilus you have to click View Hidden Files.  I'm sure you know that so is wacomcpl not working?  Typed in a terminal does the gui pop up?


The *wacomcpl* program "works" in that it puts up its little GUI and lets me do things. However, no output file is written. I'm not using Nautilus or anything; I do most everything from the command line. There is no .xinitrc file in my home directory, nor is there an "xinit" or ".xinit" directory with ".xinitrc" in it. I can try running it with *strace* to see if it's opening any files or anything I guess.

> 
Anyway ceridwen gives a mini tutorial [http://ubuntuforums.org/newreply.php?do=newreply&p=7390489&nojs=1#fcmenuon](http://ubuntuforums.org/newreply.php?do=newreply&p=7390489&nojs=1#fcmenuon) post #95 here:  [http://ubuntuforums.org/showthread.php?t=1120029&page=10](http://ubuntuforums.org/showthread.php?t=1120029&page=10)

And sanette and Lazarusrat are trying to configure everything in the .fdi.  Here's Lazarusrat's .fdi on post #73 here:  [http://ubuntuforums.org/showthread.php?t=1035029&page=8](http://ubuntuforums.org/showthread.php?t=1035029&page=8)

I was hoping you would be able to see a default CursorProx setting in you .xinitrc and go from there.  Other than whatever Wacom includes with the tablet for setting up in Windows the only "manual" is the LWP's HOWTO and stuff you can find on the web.

Maybe we should continue posting on the Intuos4 thread?  That's probably where the most help is.  I'm not sure they follow this thread.

Well the main thing for me at this point is the mouse, and nothing I've seen anywhere suggests how to do that.  I don't know what the "Intuos 4 thread" is.

---

### Post by Dave M G on 2009-06-02
> **Favux said:**
> See Lazarusrat's .fdi in the link in post #221 above.  He has some TwinView lines entered into his .fdi that may help you.

Thanks for responding.

So which fdi file do I put that in?

/usr/share/hal/fdi/policy/20thirdparty/10-wacom.fdi

or

/etc/hal/fdi/policy/custom_wacom.fdi

And if it's the second, do I delete the first one?

---

### Post by Favux on 2009-06-02
Hi Dave M G,

In "/usr/share/hal/fdi/policy/20thirdparty/10-wacom.fdi".  He modified the .fdi I posted in post #176 on this thread:  [http://ubuntuforums.org/showthread.php?t=967147&page=18](http://ubuntuforums.org/showthread.php?t=967147&page=18).

Hi pointym5,

Sorry the thread title is "Re: Wacom Intuos4 on Ubuntu" and you've been to it.  For instance the ceridwen mini tutorial is in it.

---

### Post by pointym5 on 2009-06-03
> **Favux said:**
> Hi Dave M G,

In "/usr/share/hal/fdi/policy/20thirdparty/10-wacom.fdi".  He modified the .fdi I posted in post #176 on this thread:  [http://ubuntuforums.org/showthread.php?t=967147&page=18](http://ubuntuforums.org/showthread.php?t=967147&page=18).

Hi pointym5,

Sorry the thread title is "Re: Wacom Intuos4 on Ubuntu" and you've been to it.  For instance the ceridwen mini tutorial is in it.

Ah, OK.  I'll post a "how to make mouse work" question there.  Thanks!!

---

### Post by arcadiec on 2009-06-03
> **ubootfanat said:**
> Hi!

Solution of Favux works for my Wacom Bamboo on 9.04 also.

Still no fifth button recognized by X -> no scrolling
Giving a key mapping directly in .fdi does not work either

sl
ubootfanat

Doesn't work for me either. I think the cause is Xorg's wacom driver, because before updating it to the most current version in Jaunty, the pad wheel didn't work at all... Still I have to verify this...

---

### Post by arcadiec on 2009-06-03
Upgrading to the xorg driver found in karmic didn't help either...
The 5th button still doesn't work...

---

### Post by Dave M G on 2009-06-03
I tried following the examples, and this is what I ended up with, but it doesn't work.

I am trying to get my Wacom to be in absolute mode for both stylus and eraser, and have both be constrained to only work within the left screen of my dual monitor set up.

Where did I go wrong?

```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->
<deviceinfo version="0.2">
  <device>
    <match key="input.x11_driver" contains="wacom">
      <match key="input.x11_options.Type" contains="stylus">
       	<merge key="input.x11_options.Mode" type="string">Absolute</merge>
       	<merge key="input.x11_options.Button2" type="string">3</merge>
       	<merge key="input.x11_options.Button3" type="string">2</merge>
       	<merge key="input.x11_options.Speed" type="string">0.9</merge>
        <merge key="input.x11_options.TwinView" type="string">Horizontal</merge>
        <merge key="input.x11_options.ScreenNo" type="string">0</merge>
      </match>
    </match>
    <match key="input.x11_driver" contains="wacom">
      <match key="input.x11_options.Type" contains="eraser">
       	<merge key="input.x11_options.Mode" type="string">Absolute</merge>
        <merge key="input.x11_options.TwinView" type="string">Horizontal</merge>
        <merge key="input.x11_options.ScreenNo" type="string">0</merge>
      </match>
    </match>
  </device>
</deviceinfo>
```

---

### Post by Sawer on 2009-06-03
My bad I have Jaunty kde3 installed. There on longer autostart pkg in synaptic, that would be the equal to startup manager in gnome. Thinking  about installing gnome, but I've used kde since I first started with Linux.

---

### Post by Favux on 2009-06-03
Hi Dave M G,

Notice Lazarusrat added the options to the appropriate sections of the .fdi I posted in post #176 in this thread.  I think that's your problem.

Hi Sawer,

Sorry I don't use KDE.  There must be a similar option for it.  Search around or ask someone who uses KDE.

---

### Post by Sawer on 2009-06-03
I just found an autostart deb. I have it installed getting ready to try it now.
Thanks

---

### Post by Sawer on 2009-06-03
Up and running works like a champ. 
Thanks again for your input.

---

### Post by Favux on 2009-06-03
Hi Sawer,

Good deal!

---

### Post by pointym5 on 2009-06-03
> **Favux said:**
> Hi Sawer,

Good deal!

Hey Favux, since you're the Wacom genius here have you checked the Intuos 4 thread? I've been trying to debug the driver to figure out why the mouse ("cursor") behavior is so bizarre, but I haven't made much progress.

---

### Post by Nate8nate on 2009-06-17
I have set up my Bamboo and everything works fine except setting the wheel to "Button 5."

Does anyone know how to fix this?

---

### Post by dh003i on 2009-06-22
Shatterblast's method works great for me.

---

### Post by TyrosCenva on 2009-06-25
Heya, I got my Wacom Bamboo today and I have one question about the settings.

**Intro:**
The Bamboo's active area has a 16:10 ratio and my screen is 4:3. One option to solve the ratio problem is to crop the tablet's active surface area to 4:3, thus leaving part of the active area unused.

**Goal:**
I would however like to crop the on-screen area that the tablet uses. So that the tablet can't reach the top and bottom part of the monitor screen.
This way I can use the full active area of the tablet on the portion of the screen that matters most (the Gimp window).

A little illustration might help:
============
############
############
############
============

Imagine that the whole drawing, including the = characters, is your monitor screen.
What I want is for the Wacom tablet to cover the middle area (the # characters) of the screen.

**Question:**
Is this possible, and if so, how do I do this?


Thanks in advance. :)

---

### Post by trx64 on 2009-06-25
Hi, I have a tx2000 tablet PC, now with touchscreen enabled and rotating screen.

I just have used Galium's fdi, wich enabled the touch. But the touch is the only option in wacomcpl. How do I enable the stylus?

Thanks to Galium for the fdi, easy and quick, just copy and paste, and thanks to Favux, by the How-to that enabled screen rotate.

---

### Post by Favux on 2009-06-25
Hi TyrosCenva,

I think you want the KeepShape option.  That's described here:  [http://linuxwacom.sourceforge.net/index.php/howto/inputdev](http://linuxwacom.sourceforge.net/index.php/howto/inputdev)  And the .fdi version of it would be:
```
<merge key="input.x11_options.KeepShape" type="string">on</merge>

```
I don't know if you'd want to set your X and Y also.

---

### Post by TyrosCenva on 2009-06-25
Thanks Favux, but I'm affraid that's not what I'm looking for.
The KeepShape option crops the active tablet area that the tablet will use. What I'd like to do is to crop the screen/display/monitor/X-windows area that the tablet will use. There's a subtle yet important difference between the two. :)
See it as if your mouse would stop at the inner edge of the taskbar and menubar so that you would not be able to reach the "Applications" menu for example. That's what I'm aiming for.

---

### Post by Favux on 2009-06-25
Hi TyrosCenva,

So KeepShape combined with:
```
<merge key="input.x11_options.TopX" type="string">?</merge>
<merge key="input.x11_options.TopY" type="string">?</merge>

```
affects the active area on the tablet, not the screen?

---

### Post by TyrosCenva on 2009-06-26
Favux, exactly. Just tried it to be sure. Top and Bottom X and Y affect the sensitive area the tablet uses.
I did notice a small advantage of KeepShape though, because now I can reach a few of the Gimp windows on the second monitor.

---

### Post by Matyy on 2009-07-02
Hej, first thanks, this topic helped me already get wacomcpl to work. I got an old old graphire3 worked as soon as I pluged it in, GIMP recognized it, just wacomcpl not. With the fdi from here there is no more problem. 

Well just one. You see, Graphire3 is kinda small, so I'd like to use that window mode in GIMP so I get most of the resolution. So if I set it to window mode I got two cursors, the one that is using the whole desktop (on two screens) and the other one who stays in the Gimp window. And that's quite a mess, since as soon as I leave the Gimp window with the "desktop-cursor" and I click, I activate something.

I had solved that before long time ago, but yeah, than one had to edit the xorg.conf, and I don't remember how, nor am I finding something, something with corepointer? No idea, nor do I know much bout this hal/fdi stuff.

Does anyone have a solution? Somehow I can set up stylus & eraser exclusively for gimp? Can I "disconnect" make the stylus & eraser from the normal mouse pointer?

---

### Post by crazybus on 2009-07-04
I installed kubuntu-desktop and am trying out KDE again.  But for some reason the tablet doesn't work as a mouse here.  I would have assumed all the files I installed would have worked here to since I don't remember any gnome specific things.  Can anyone kindly help?

Update:  I saw mentioned on another thread that someone's tablet stopped working after a large update.  That might be my problem in which case I can fix.

---

### Post by phorgan1 on 2009-08-04
I'm using a Bamboo Fun with Ubuntu Jaunty.  I went with the modified .fdi file and put it in /usr/share/hal/fdi/policy/20thirdparty replacing 10-wacom.fdi.  Now xinput --list lists the short versions, i.e. stylus, pad, cursor and erasor.  xsetwacom list still doesn't list anything and wacomcpl doesn't work.  Worse, the eraser in gimp is strange with two cursors one of which erases and the other which does not but shows up in the same place that the stylus would show up as at the same part of the pad.  The two cursors with the erasor vary in distance between each other and near the bottom left meet then cross as the stylus moves farther down or to the left.

After using the erasor with gimp the stylus won't work to get to the rest of the screen until I kill gimp.  Without the new 10-wacom.fdi and using a /etc/had/fdi/policy/customwacom.fdi things were working well.

Any thoughts?

Patrick

---

### Post by Sawer on 2009-08-04
Did you install the wacom tools in synpatic? Also  try wacomcpl Alt+ F2 what shows up there?

---

### Post by juancarlospaco on 2009-08-04
Theres a GUI to configure it, Wacom Control Panel *(is not wacom-tools package)*,
i see that on GTK-apps website...

---

### Post by Favux on 2009-08-04
Hi phorgan1,

You need to remove your customwacom.fdi in /etc/had/fdi/policy/.  That's why things are messed up.

I'd be careful with Wacom Control Panel and the other gui's.  Some make Wacom entries in your xorg.conf without asking.  You don't want that in Jaunty.  Just use wacomcpl (which is in wacom-tools) like Sawer said.

---

### Post by subverso on 2009-08-04
Hello people,

I read a lot and tried somethings to fix that. But no success.
I have edited my xinitrc like this:

```
xsetwacom set stylus TPCButton "off"
xsetwacom set stylus mode "Absolute"
xsetwacom set stylus Button3 "Button 2"
xsetwacom set stylus Button2 "Button 3"
xsetwacom set stylus Button1 "Button 1"
# run the primary system script
. /etc/X11/xinit/xinitrc
```

but everytime I restart or logoff, I lose my calibration config.

Someone could help me with this?
Thanks in advance

---

### Post by phorgan1 on 2009-08-04
> **Favux said:**
> Hi phorgan1,

You need to remove your customwacom.fdi in /etc/had/fdi/policy/.  That's why things are messed up.

I'd be careful with Wacom Control Panel and the other gui's.  Some make Wacom entries in your xorg.conf without asking.  You don't want that in Jaunty.  Just use wacomcpl (which is in wacom-tools) like Sawer said.

Actually I thought that I was clear that I switch away from doing that.  I don't have a customwacom.fdi.  So it's not my problem.  Any other guesses?  Because I'm stuck.

Patrick

---

### Post by Favux on 2009-08-04
Hi Patrick,

Ok, are you sure there aren't any Wacom entries in xorg.conf?  I would check on the new modified 10-wacom.fdi and make sure it's in place and complete.  Is there any chance you have a different version of wacom-tools installed, different from the default 0.8.2-2 xserver-xorg-input-wacom in Jaunty?

Hi subverso,

Follow Section 3 on the HOW TO here:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)  That should keep the settings through a restart.

---

### Post by phorgan1 on 2009-08-04
> **Favux said:**
> 
...elision here...

I'd be careful with Wacom Control Panel and the other gui's.  Some make Wacom entries in your xorg.conf without asking.  You don't want that in Jaunty.  Just use wacomcpl (which is in wacom-tools) like Sawer said.

If I only could!  I can for example do:

```
xsetwacom get pad AbsWUp
```

and it works!  But xsetwacom list or xsetwacom list dev don't do anything and neither does wacomcpl.

Patrick

---

### Post by phorgan1 on 2009-08-04
> **Sawer said:**
> Did you install the wacom tools in synpatic? Also  try wacomcpl Alt+ F2 what shows up there?

Yep wacom-tools are installed.  I don't know what wacomcpl Alt+F2 means.  Do you mean to bring up the run program dialog and run wacomcpl from in there?  If so, then there's no change.

---

### Post by Favux on 2009-08-04
Hi Patrick,

So say:
```
xsetwacom set pad AbsWUp "core key  CTRL  SHIFT s"
```
doesn't work for you?

---

### Post by Sawer on 2009-08-04
> **Favux said:**
> Hi Patrick,

Follow Section 3 on the HOW TO here:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)  That should keep the settings through a restart.

Maybe yes maybe no. I have 2 machines with the same basic install, one install it  holds the settings the other it doesn't go figure.

@phorgan did you restart after installing the the wacom tools?

---

### Post by phorgan1 on 2009-08-04
> **Favux said:**
> Hi Patrick,

Ok, are you sure there aren't any Wacom entries in xorg.conf?  I would check on the new modified 10-wacom.fdi and make sure it's in place and complete.  Is there any chance you have a different version of wacom-tools installed, different from the default 0.8.2-2 xserver-xorg-input-wacom in Jaunty?

Yep, checked xorg.conf, nothing there.  Checked the new modified, here's a copy here:```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

<deviceinfo version="0.2">
  <device>
    <match key="input.originating_device" contains="if0">
      <match key="info.product" contains="Wacom">
        <merge key="input.x11_driver" type="string">wacom</merge>
        <merge key="input.x11_options.Type" type="string">stylus</merge>
        <merge key="info.product" type="string">stylus</merge>
          <append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
          <append key="wacom.types" type="strlist">eraser</append>
          <append key="wacom.types" type="strlist">cursor</append>
          <append key="wacom.types" type="strlist">pad</append>
      </match>
    </match>
  </device>
  <device>
    <match key="input.x11_options.Type" contains="eraser">
      <merge key="info.product" type="string">eraser</merge>
    </match>
  </device>
  <device>
    <match key="input.x11_options.Type" contains="cursor">
      <merge key="info.product" type="string">cursor</merge>
    </match>
  </device>
  <device>
    <match key="input.x11_options.Type" contains="pad">
      <merge key="info.product" type="string">pad</merge>
    </match>
  </device>
</deviceinfo>

```
And I checked, I have the same version of wacom-tools.

---

### Post by phorgan1 on 2009-08-04
> **Favux said:**
> Hi Patrick,

So say:
```
xsetwacom set pad AbsWUp "core key  CTRL  SHIFT s"
```
doesn't work for you?
No, I didn't say that.  If I specify the device xsetwacom works.  What doesn't work is that it can't list the devices, and wacomcpl doesn't see the pad at all.

---

### Post by subverso on 2009-08-04
> **Favux said:**
> Hi Patrick,

Ok, are you sure there aren't any Wacom entries in xorg.conf?  I would check on the new modified 10-wacom.fdi and make sure it's in place and complete.  Is there any chance you have a different version of wacom-tools installed, different from the default 0.8.2-2 xserver-xorg-input-wacom in Jaunty?

Hi subverso,

Follow Section 3 on the HOW TO here:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)  That should keep the settings through a restart.

Real nice, Favux! It worked. 
Thanks a lot. Now, everything is working in my Intuos3.
Peaceout!

---

### Post by Favux on 2009-08-04
Hi subverso,

Good deal!  Glad everything is working.


Hi Patrick and Sawer,

It looks like you both may have the same problem.  Xinput lists the right names (does it for you too Sawer?) but "xsetwacom list" is blank and wacomcpl doesn't work.  Since xinput lists the correct names (maybe you could post it Patrick?) then the .fdi is working.  I don't understand the stuff about wrong parameter bottomX or whatever it is either Sawyer.

Maybe you both have a corrupt wacom-tools (bad version on same mirror?)?  I'd do a complete uninstall in Synaptics and reboot.  Maybe pick another mirror site.  Reinstall.

You're both in Jaunty (9.04)?  I have heard about bizarre one time/idiosyncratic errors apparently caused by Xserver 1.6.  I don't know how real that is.

Edit:  Oh, and you'll want to check that the 10-wacom.fdi is still the new modified one.  That it hasn't been knocked out.

---

### Post by Dave M G on 2009-08-20
Following the instructions on this thread, I have managed to get my Wacom tablet set up with all my preffered settings, except one.

My pen has two buttons on the side. Right now, the one closest to the tip is "button3", and the one furthest from the tip is "button2". I only know this from the behaviour of the mouse pointer, not because I have explicitly seen button settings in my 10-wacom.fdi file or anywhere else.

I want to change the button mapping so that the button close to the tip is "button2", and the one furthest is "button3".

I can not find the right settings, here or even trying to extrapolate from old xorg.conf settings from the linuxwacom project.

If someone could point out sample code of how to map buttons in 10-wacom.fdi, that would be appreciated.

Thank you for all your time and effort.

---

### Post by Favux on 2009-08-20
Hi Dave M G,

You can do that but why not configure them through wacomcpl stylus>tool buttons?

---

### Post by Dave M G on 2009-08-20
Thank you for responding.

> wacomcpl stylus>tool buttons

Took me a moment to grasp what you are saying.

You mean enter "wacompl" on the command line, and then in the interface that comes up select "Stylus", and set the tool buttons in the interface there.

I did that and it works, so thanks for the tip!

---

### Post by Favux on 2009-08-20
Hi Dave M G,

Exactly.  Sorry some times I take things too much for granted.  I should have expanded on the explanation.  Have you set wacomcpl to last through a reboot?  If not see "Section 3:  Calibrating your Tablet" here:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)

---

### Post by Dave M G on 2009-08-20
A follow up...

I like to use my tablet for both graphics applications, and for all other interface needs.

The difference is that when I'm just using the computer in general, I like my Wacom to be in "Relative" mode.

When I'm using a graphics software like "Inkscape", I like to be in "Absolute" mode for the more accurate curves.

I can switch them easily enough by going to "System->Settings->Graphics Tablet", or using wacompl from the command line (which I just learned about two minutes ago).

What would be super sweet is to set up a keyboard shortcut for switching between the two modes. Is that possible?

I suppose if I had a command line (or two) that switched from one to the other, I could set up a small script and somehow map a key combination in Compiz(?).

If anyone can tell me the command line for changing modes, and/or suggestion on how how to map keys.

I also have two buttons on my tablet itself. Perhaps they could be used?

Any advice would be much appreciated.

---

### Post by Favux on 2009-08-21
Hi Dave M G,

Sure.  The cli commands are:
```
xsetwacom set Stylus mode relative
```
and of course:
```
xsetwacom set Stylus mode absolute
```
From the LWP's HOWTO:  [http://linuxwacom.sourceforge.net/index.php/howto/xsetwacom](http://linuxwacom.sourceforge.net/index.php/howto/xsetwacom)

And to set up a launcher and deal with xev and key binding see:  [http://ubuntuforums.org/showthread.php?p=6274392](http://ubuntuforums.org/showthread.php?p=6274392)  Start about halfway down at "now with the preliminaries" etc.

---

### Post by llex_paul on 2009-08-21
hey all! I am new in ubuntu and i don't know many explication from here and i hope you have time to help me get my Wacon Intuos3 buttons and touch-strip work. A friend of mine help me install (pressure works like charm) my tablet but buttons and touch-strip didn't know how to make work and now i have to ask you help.

---

### Post by Favux on 2009-08-21
Hi llex_paul,

Welcome to the Ubuntu Forums!

Probably the easiest way is to use wacomcpl.  If you enter 'wacomcpl' in a terminal the linuxwacom calibration and configuration gui pops up.  To find out if you can use it enter in a terminal:
```
xsetwacom list
```
It should return stylus, eraser, cursor, and pad.  If it is blank you can not use wacomcpl.

To fix this go to post #176 on this thread:  [http://ubuntuforums.org/showthread.php?t=967147&page=18](http://ubuntuforums.org/showthread.php?t=967147&page=18)  and follow the instructions to install the modified 10-wacom.fdi.

Then to set up wacomcpl go to "Section 3: Calibrating your Tablet" here: [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949) and follow the instructions.

Now to set up your pad go to shatterblast's post #188 on this thread:  [http://ubuntuforums.org/showthread.php?t=967147&page=19](http://ubuntuforums.org/showthread.php?t=967147&page=19) to see how he set up his Bamboo's pad.  What he is doing is modifying the .xinitrc you worked on above.  Remember it is a hidden file so to see it check Show Hidden files in View in Places.

Good luck!

---

### Post by Dave M G on 2009-08-21
Favux,

Thanks! This is really great! I now have my tablet switching between relative and absolute mode on-the-fly with just some simple keystrokes.

This has made it possible to switch between graphics editing and other tasks so easy that I think my cumulative productive time at the computer just shot up considerably.

A couple notes for anyone who might be considering something similar:

The command line needs to be all lower case:
xsetwacom set stylus mode absolute
xsetwacom set stylus mode relative

Upper case "Stylus", as originally suggested, didn't work for me.

The other thing was that I use Compiz as my window manager, and in the interface there is a section called "commands", where one can simply assign a command to a sequence of buttons. On the upside, this was easier to set up. On the downside, this will only work in Compiz. If for any reason Compiz crashes or I need to switch to another window manager (rare, but happens once in a blue moon), then that key binding won't apply.

Oh, and one last thing. I originally intended to use super+1 and super+2 as my switching keys (the "super" key is the one that sometimes has a Windows logo on it... if you're not hardcore like me and took it off with rubbing alcohol!). For some reason, no binding with the super key would work, perhaps because of a conflict with another key binding. So instead I chose to alt+1 and alt+2 and that works fine.

I am totally psyched!

Thanks for all your help!

---

### Post by llex_paul on 2009-08-21
i hope it will work, but i will try it at my friend...i am afraid of the problems that may appear...(i heard that i can get in ubuntu crash if there is something wrong and i don't know a lot of things... is there any risk?). i hope you understand me...there is a lotttt of strange things in all of that codes for me:))

---

### Post by Favux on 2009-08-21
Hi llex_paul,

Sure, get your friend to help.  It's pretty safe to do.  Not likely to crash the system.  You will quickly learn things.


Hi Dave M G,

Great!  You're welcome.

---

### Post by adrianbowyer on 2009-08-25
Hi

I am running Jaunty and I have a Wacom Bamboo model CTE-650.  This doesn't quite work "out of the box", and I can't figure out why.

lsusb gives:

Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 002: ID 056a:0018 Wacom Co., Ltd 
Bus 005 Device 001: ID 0000:0000
.
. 

which seems to imply it's connected.  dmesg | tail gives:

[21878.842206] usb 5-2: new full speed USB device using ohci_hcd and address 2
[21879.067015] usb 5-2: configuration #1 chosen from 1 choice
[21879.140965] usbcore: registered new interface driver hiddev
[21879.141709] usbcore: registered new interface driver usbhid
[21879.142051] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver

which again seems to imply that it's there.  My /etc/X11/xorg.conf has all the old wacom stuff commented out:

.
.
# commented out by update-manager, HAL is now used
#	InputDevice     "stylus"	"SendCoreEvents"
# commented out by update-manager, HAL is now used
#	InputDevice     "cursor"	"SendCoreEvents"
# commented out by update-manager, HAL is now used
#	InputDevice     "eraser"	"SendCoreEvents"
.
.

and so on.

And yet the tablet won't control the mouse.

xinput --list gives:

"Virtual core pointer"	id=0	[XPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
"Virtual core keyboard"	id=1	[XKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"AT Translated Set 2 keyboard"	id=2	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"ImPS/2 Generic Wheel Mouse"	id=3	[XExtensionPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
"Macintosh mouse button emulation"	id=4	[XExtensionPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1

and I'm fairly sure none of those is the tablet.  Any idea what I'm missing?

---

### Post by Favux on 2009-08-25
Hi adrianbowyer,

See if in a terminal entering:
```
dmesg | grep [Ww]acom
```
returns Wacom stuff.

Check in Synaptic Package Manager that both 0.8.2-2 linuxwacom packages are installed:  xserver-xorg-input-wacom & wacom-tools  If not install them and reboot.  Then try dmesg again.

Before installing the linuxwacom packages check to see that in "/usr/share/hal/fdi/policy/20thirdparty/" there is a file called "10-wacom.fdi".  It should be there after you install the packages.

---

### Post by MartinGiese on 2009-08-26
> still there is no button5 recognized by X.

I am wondering how xinput knows how many buttons are available for each input device. I have not found that info up to now. may it be part of the driver?

is there anyone else with a wacom bamboo and a missing scroll-event?

sl ubootfanat

Yep, i have the same problem:
[LIST]
[*]scrolling one way (button 4) works, but not the button 5 way.
[*]xinput for the "pad" says "Num_buttons is 4"
[*]xidump only reports button 4 and not button 5 events
[*]binding AbsWUp or AbsWDn to "core key +" and the likes works.
[/LIST]
Any solution to this yet?

---

### Post by adrianbowyer on 2009-08-26
Hi Favux

Thanks for your reply.

dmesg | grep [Ww]acom

gives nothing.  

Both xserver-xorg-input-wacom and wacom-tools are installed, and have been all along.

/usr/share/hal/fdi/policy/20thirdparty/10-wacom.fdi exist, and again has been there all along.

---

### Post by Favux on 2009-08-26
Hi adrianbowyer,

It should have returned some Wacom stuff if things were working.

So first thing is are you sure the hardware is OK?  Does it work in Windows or on another machine?

How new is this model of Bamboo?  When did Wacom start manufacturing it, if you know?

It almost sounds like your wacom.ko isn't in place, isn't working, or doesn't work for your model of Bamboo.

The wacom.ko comes with the "linux image" for your kernel.  The "linux-image" has the default kernel modules.  In Synaptic Package Manager you could find the correct one for your kernel version, it should be checked as installed, and tell it to reinstall.  Then reboot.  See if that does anything.

Edit:  Another possiblity is that you need to add 'wacom' (without the quotes) to the end of your "/etc/modules" file.  Some systems don't seem to kick in the wacom.ko unless you do that.

---

### Post by shatterblast on 2009-08-27
Step 1)  Install wacom-tools from Synaptic if available.  Xserver-xorg-input-wacom should already be installed.

Step 2)  If you use a Bamboo, try running the attached script in this posting.


Step 3)  Several other types of Wacom tablets are compatible with the Bamboo.  If you still have trouble, go into Terminal and type:

```

xinput --list

```

Change the naming around as necessary in the attached script.

Step 4) If you still have trouble, use the 10-wacom.fdi file.  Usage of the file may still be necessary for tweaking to achieve desirable settings.  If so, the attached script will require changes in naming.

Good luck.

---

### Post by Favux on 2009-08-27
Hi shatterblast,

Would you be interested in testing the following?  Try using "stylus", "eraser", "cursor", and "pad" (with the quotes).  A tablet pc user said using "stylus" and "touch" (with the quotes) worked for him in his xsetwacom rotation commands.

Either way couldn't you rename the script .xinitrc and then have wacomcpl available?

---

### Post by adrianbowyer on 2009-08-27
The machine is dual-boot and the tablet works fine in Windows, so I don't think it's a hardware problem.

modprobe -l | grep -i wacom

gives

kernel/drivers/input/tablet/wacom.ko

so that seems to be in place.

[This page]("http://hardware4linux.info/component/31783/") seems to imply that I might need a newer driver.  I'll see what I can do there.

---

### Post by Favux on 2009-08-27
Hi adrianbowyer,

Sometimes when:
```
dmesg | grep [Ww]acom
```
returns nothing it means the the wacom.ko isn't kicking in.  Some setups require adding 'wacom' (without the quotes) to the end of the file 'modules' in '/etc/modules".  And then rebooting.  Why don't you try that first?

---

### Post by shatterblast on 2009-08-27
> **Favux said:**
> Hi shatterblast,

Would you be interested in testing the following?  Try using "stylus", "eraser", "cursor", and "pad" (with the quotes).  A tablet pc user said using "stylus" and "touch" (with the quotes) worked for him in his xsetwacom rotation commands.

It works only when using the 10-wacom.fdi file.  I remember that way works, but it took both more time and trouble-shooting.  It could perhaps still be the best solution for those with "tablet PCs" that have the function built into the computer itself.

> Either way couldn't you rename the script .xinitrc and then have wacomcpl available?

Yes.  However, a missed step somewhere may cause X11 to not boot-up correctly.  ".xinitrc" is just an SH script file.  The dot in front of it keeps people from damaging their settings on accident by hiding the file.

Still, I think my way is easier for starting.  The 10-wacom.fdi is best for advanced users who know the purposes of script files.

---

### Post by Favux on 2009-08-27
Hi shatterblast,

You could well be right.

But the user I mentioned had the default Jaunty 10-wacom.fdi and the quotes thing worked for him in his rotation script (which uses xsetwacom commands).  He didn't touch the wacom.fdi at all as I understand it.

---

### Post by AgedP on 2009-08-28
Thank you Favux.  Works well using Bamboo on Mint 7.0.
Some guidance tuning wacomcpl would be useful so as to get the best out of hardware and software.   I was able to configure the touch ring using plus and minus.
BTW I use version 0.8.4 which is later than version you used to develop your Howto.
Is there a significant difference?

---

### Post by Favux on 2009-08-28
Hi AgedP,

You're welcome.  That's several folks set up on Mint 7 that I'm aware of.  No real difference than installing on Jaunty I can detect.

Sure 0.8.4 has bug fixes, new features including supporting the Intuos4, Xserver 1.6, and more HAL support.  By the way my HOW TO was updated to 0.8.4 a while ago.  I'm only using production versions and the last one was 0.8.2-2.  Which isn't the same as the default Jaunty 0.8.2-2, because the Jaunty one is patched to support Xserver 1.6 and HAL.

Your right about 'wacomcpl', so I added some stuff to post #176.  See if that's better.  Let me know.

In my defense I thought I was just submitting the new .fdi for testing.  I figured at most a few more posts to get testers set up and then Loic2 and mesilliac and the rest would decide what to do with it.

---

### Post by adrianbowyer on 2009-08-29
Hi everyone - thanks for all your help.  I finally found the problem:

When I upgraded to Jaunty, I didn't overwrite /boot/grub/menu.list.  That meant that I was still running the old kernel, though I didn't notice...

Fixing that fixed everything.

Thanks again.

---

### Post by llex_paul on 2009-08-29
hey favux! it works, partial... but it's a big step forward and i want to 10x for your time! linux its greater day by day and i learn new things. GIMP is for my concept art paintings and it does a great job but is 30%  slower than PS...and i don't like that color piker cand pick only from one layer not from the color one layer back and that is a another big disadvantage if you work with layers....

now...lets get back to my biggest concern... my tablet butons don't work but now i can see that wacompl from the first step. could you help me to make buttons work?
[]("http://ubuntuforums.org/member.php?u=699990")

---

### Post by Favux on 2009-08-29
Hi llex_paul,

Good!  Nice job.

The newer version of Gimp is suppose to have some improvements so maybe you'll like the version in Karmic (9.10) better.  Out in a couple of months.

Now that you can use wacomcpl you should be able to fine tune things for your work flow.  If wacomcpl doesn't let you set up your buttons the way you want them you can edit it's .xinitrc.  That's in your "/home/yourusername/" directory.  If is a hidden file so you have to check Show Hidden Files in View.

The buttons are the 'pad'.  That's near the bottom of post #176 (where the .fdi is).  I show you where shatterblast sets up his Bamboo pad and ceridwen sets up his Intuos4 pad.  The LWP's HOWTO shows you how to use xsetwacom commands.  Those are the commands in wacomcpl's .xinitrc.  See:  [http://linuxwacom.sourceforge.net/index.php/howto/xsetwacom](http://linuxwacom.sourceforge.net/index.php/howto/xsetwacom)  Or you could google for someone else's Intuos3 setup.  I've seen a few.  Maybe on this thread?

Good luck!

Edit:  I found an example for you.  See near the bottom here:  [http://kaeru.my/articles/technical/setting-up-and-using-intuos-tablet-on-linux/ubuntu-setup](http://kaeru.my/articles/technical/setting-up-and-using-intuos-tablet-on-linux/ubuntu-setup)  He shows the button mapping and an example xsetwacom command.

---

### Post by Favux on 2009-08-29
Hi shatterblast and everyone,

I think around a year ago there was a discussion on linuxwacom discuss as to whether wacomcpl using .xinitrc was the right way to go.  They were wondering if making it part of the X script chain made sense give that the chain was being deprecated.

Loic2 worked hard to get a Wacom configuration gui into Jaunty.  Sort of like the one Wacom has for Windows.  I think the idea was you would check whatever configuration you wanted and it would edit xorg.conf or the 10-wacom.fdi for you.  He actually got Ubuntu to put a developer on it.  But the developer didn't have enough time to get it done for Jaunty.  I don't know how much fine tuning it would have allowed in pad (buttons) say.

Ping Cheng, the lead LWP developer, with his announcement of linuxwacom 0.8.4 also mentioned a new configuration/calibration gui.  At least I think that's what he was saying.  The link to it didn't work.  And a Ubuntu person inquired about it.  So there may be something new for Karmic, and I bet it doesn't use .xinitrc.  Isn't the LSB a .config file?  Anyway the impression I got is that it was an updated improved wacomcpl.

---

### Post by shatterblast on 2009-08-29
> **Favux said:**
> Hi shatterblast and everyone,

I think around a year ago there was a discussion on linuxwacom discuss as to whether wacomcpl using .xinitrc was the right way to go.  They were wondering if making it part of the X script chain made sense give that the chain was being deprecated.

Loic2 worked hard to get a Wacom configuration gui into Jaunty.  Sort of like the one Wacom has for Windows.  I think the idea was you would check whatever configuration you wanted and it would edit xorg.conf or the 10-wacom.fdi for you.  He actually got Ubuntu to put a developer on it.  But the developer didn't have enough time to get it done for Jaunty.  I don't know how much fine tuning it would have allowed in pad (buttons) say.

Ping Cheng, the lead LWP developer, with his announcement of linuxwacom 0.8.4 also mentioned a new configuration/calibration gui.  At least I think that's what he was saying.  The link to it didn't work.  And a Ubuntu person inquired about it.  So there may be something new for Karmic, and I bet it doesn't use .xinitrc.  Isn't the LSB a .config file?  Anyway the impression I got is that it was an updated improved wacomcpl.

That seems like good news.  I also think the work gone towards the Wacom Project and the integration for Ubuntu has gone well.  The obvious complication comes from the updates to Gnome and similar, which has its benefits and problems.

> **Favux said:**
> Hi shatterblast,

You could well be right.

But the user I mentioned had the default Jaunty 10-wacom.fdi and the quotes thing worked for him in his rotation script (which uses xsetwacom commands).  He didn't touch the wacom.fdi at all as I understand it.

Using the 10-wacom.fdi file from this forum thread changes the device names from " xinput --list " on my computer.  I only meant to highlight that concept.

---

### Post by Favux on 2009-08-29
Hi shatterblast,

> Using the 10-wacom.fdi file from this forum thread changes the device names from " xinput --list " on my computer.
Right.  And the modified wacom.fdi, because it changes the "xinput --list" names to stylus, eraser, cursor, and pad means "xsetwacom list" will return the same names.

Programs like wacomcpl and Blender that are hard coded to expect those names will then work.  As will the "standard" xsetwacom commands.

What I think the user was saying is that instead of in your script for stylus for e.g.:
```
xsetwacom set "Wacom Bamboo" Suppress "15"
xsetwacom set "Wacom Bamboo" RawSample "15"
xsetwacom set "Wacom Bamboo" ClickForce "5"
xsetwacom set "Wacom Bamboo" PressCurve "0 0 100 100"
xsetwacom set "Wacom Bamboo" Accel "1"
xsetwacom set "Wacom Bamboo" SpeedLevel "4"
xsetwacom set "Wacom Bamboo" TPCButton "off"
xsetwacom set "Wacom Bamboo" mode "Relative"
xsetwacom set "Wacom Bamboo" Button3 "Button 3"
xsetwacom set "Wacom Bamboo" Button2 "Button 2"
xsetwacom set "Wacom Bamboo" Button1 "Button 1"
```
this was working for him:
```
xsetwacom set "stylus" Suppress "15"
xsetwacom set "stylus" RawSample "15"
xsetwacom set "stylus" ClickForce "5"
xsetwacom set "stylus" PressCurve "0 0 100 100"
xsetwacom set "stylus" Accel "1"
and so on
```
Instead of the standard:
```
xsetwacom set stylus RawSample "15"
etc.
```
I was curious if this was so for you too without the modified wacom.fdi, i.e. using the default Jaunty 10-wacom.fdi.

---

### Post by llex_paul on 2009-08-30
i can't figure it out...i fund this thread [http://ubuntuforums.org/showpost.php?p=7158628&postcount=160](http://ubuntuforums.org/showpost.php?p=7158628&postcount=160)   and if i tried to do like him it didn't  let me save the changes because the ''location is incorrect ''...and if i change in wacompl something next time i open my laptop the setting are reseted.

---

### Post by Favux on 2009-08-30
Hi llex_paul,

Mallow's set up looks good for you!  But remember to keep/use 'pad', don't change it to "Wacom Intuos3 6x8 pad" like he does.  You have the new .fdi so you don't need to do that.

> and if i change in wacompl something next time i open my laptop the setting are reseted. 
Did you do **_Section 3:  Calibrating your tablet_** in the HOW TO here:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)  ?  That will keep your changes through a restart.  After the changes reboot.
> didn't let me save the changes because the ''location is incorrect ''
In Places (Nautilus) go to View and click on Show Hidden Files.  Then find '.xinitrc' in "/home/yourusername/".  Just click on 'yourusername' on the left.  Right click on '.xinitrc' and select "Open with Other Application".  Choose "Text Editor".  Make the changes you want and then Save and Close.

---

### Post by shatterblast on 2009-08-30
> **Favux said:**
> 
I was curious if this was so for you too without the modified wacom.fdi, i.e. using the default Jaunty 10-wacom.fdi.

No, but I might also have modified my Wacom tablet's internal firmware some months ago.  I tend to weird things like that.  It could be the naming works differently with me for some reason than with anyone else.

I might have over-assumed too much in thinking that what has affected me should also benefit everyone else.  Then again, I make situations difficult.

---

### Post by Favux on 2009-08-30
Hi shatterblast,

I don't know about that.

I can tell you I've been referring people to your post #188 as an example of how to set up the pad since you posted it!

---

### Post by llex_paul on 2009-08-31
> Now check the file "xinitrc" in "/etc/X11/xinit/". Everything in it should be commented out. If you see:
 	Code:
 	# invoke global X session script
. /etc/X11/Xsession 
comment it out like so:
 	Code:
 	# invoke global X session script
#. /etc/X11/Xsession


here i have a problem...i created that startup file and when i find that xinitrc from etc/x11/xinitrc and i open it and then i put that ''#'' in place, then i try to save and it says '' Could not save the file /etc/X11/xinit/xinitrc.   You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.'' ....then i restart without that ''#'' in front and when i logged in my laptop display keept flashing and open and close some windows...i went directly to that startup aplication and disable it an restart again. now my laptop is fine but my wacom buttons still don't work,,,cand you help me?

---

### Post by Favux on 2009-08-31
Hi llex_paul,

Sure.  You don't have permission because you are not editing as root.  Enter this in a terminal:
```
gksudo gedit /etc/X11/xinit/xinitrc
```
Put the comment in save and close.

Both gksudo and sudo make you root.  You use gksudo when using a graphical program like gedit (Text Editor).

What you are describing is the loop I was talking about.

---

### Post by strycore on 2009-08-31
I've been using my Wacom Volito 2 for a while now, but I've set up a new computer with Ubuntu 9.10 and I've had a strange behavior since. 

In Gimp or Inkscape, when I configure them to make use of the full functionnality of the tablet, the drawing position is shifted a few pixels beneath the real cursor. 

The bug has been reported on Launchpad here : 
[https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/419585](https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/419585)
and I've attached a screenshot describing this strange behavior in Gimp. 

Can this be fixed with the appropriate xsetwacom commands ?

---

### Post by Favux on 2009-08-31
Hi strycore,

It sounds like you probably tried 'wacomcpl' to recalibrate and that didn't work.  Wacomcpl uses xsetwacom commands for calibration like so:
```
xsetwacom set eraser bottomy "16630"
xsetwacom set eraser bottomx "26416"
xsetwacom set eraser topy "-101"
xsetwacom set eraser topx "66"
xsetwacom set stylus bottomy "16630"
xsetwacom set stylus bottomx "26416"
xsetwacom set stylus topy "-101"
xsetwacom set stylus topx "66"
```
Your calibrations would be different of course.

The bug report you link to may be marked as a duplicate to this one:  [https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/410267](https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/410267)  from this thread:  [http://ubuntuforums.org/showthread.php?t=1233845](http://ubuntuforums.org/showthread.php?t=1233845)  So they already know there's a problem.  Hopefully a fix soon.

This may be a bug in Xserver/Xinput or possibly linuxwacom.

---

### Post by shatterblast on 2009-08-31
> **Favux said:**
> Hi shatterblast,

I don't know about that.

I can tell you I've been referring people to your post #188 as an example of how to set up the pad since you posted it!

Okay, thank you.  I can tell you're covering the basis well.  I will check back later.

---

### Post by llex_paul on 2009-09-01
yess!! it works! i was starting to get discouraged after that loop, but now it's ok. 10x a lot favux!

---

### Post by Favux on 2009-09-01
Hi llex_paul,

Great!  You're welcome.  And you have your pad set up now?  Good.

---

### Post by Skiri-ki on 2009-09-15
Hi there,
I'm having a fun time configuring my tablet as well, but my problems seem to be a bit different than the ones mentioned up until now (as far as I read them and the search told me anyways).

I have had a graphire4 in a dual Monitor setup first so setting up my new Cintiq 12WX was rather easy. Everything works, but the Expresskeys. They just don't do anything while the Touchstrips on the other hand, do exactly what you'd expect them to.

Setup: Cintiq 12WX on Ubuntu 9.04 using a self compiled linuxwacom driver (which Version I guess is -0.8.2-2 but ain't sure anymore) with --enable-wacom and --enable-quirk-tablet-rescale (for twinview). Other versions wouldn't compile or just didn't work properly. 

Since I was more comfortable using xorg.conf, I disabled the 10-wacom.fdi at first and did everything through xorg.conf instead. Therefor I have entries in 
```
Section "ServerLayout"
#           ...	
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "pad"
EndSection

```
and 
```
Section "InputDevice"
  	Driver        "wacom"
  	Identifier    "pad"
  	Option        "Device"        "/dev/input/wacom"   # USB ONLY
  	Option        "Type"          "pad"
  	Option        "USB"           "on"                  # USB ONLY
	Option        "Twinview" "horizontal"
	Option 	      "TVResolution" "1280x800,1280x1024"
EndSection
```
as well as similar entries for the other 3 devices. (My xorg.conf is rather crowded and confusingly structured so I decided for extracts only)

At startup I set one of the two touchstrips to ',' and '.', the other one to 'm' and 'n' and assign the nummbers 3-9 and 0 via "xsetwacom set" as can be seen in the attached .initrc file. It addresses the device as "pad" (without quotes). As stated, the strips work, the buttons don't produce any output.

```
xinput list
``` gives me a "stylus", an "eraser", a "cursor"(I know it's pointless), a "pad" and a "Wacom Cintiq 12WX" (no idea where that last one comes from though). For the full output see the attached xinput list.txt.

xidump -l und xsetwacom list print out the same devices, only "Wacom Cintiq 12WX" is ignored by xsetwacom list. wacomcpl lists all devices (except "Wacom Cintiq 12WX") and can be used for configuration. If I open up the buttons keystrokes, it shows me their respective numbers as I set them via xsetwacom. 

xidump eraser and stylus work and xidump pad reacts to the strips as expected (Proximity changes from out to in AND key numbers are printed out (from 50-UP to 53-UP)).
It also tells me 
```
1253062601 - MappingNotify
```
at the very bottom. The number increases in increments of one if I press a keyboard key and touch the touchstrip again (only keyboard, it doesn't work with the mouse). If I do this to often my deskbar applet crashes on me oO.
If I press the buttons one at a time, nothing is registered, if i press two or more simultaneously, Proximity changes from out to in but NO key numbers are printed.

wacdump /dev/input/wacom and /dev/input/event4 identifies the Tablet as 
```

MODEL=Wacom Cintiq 12WX                 ROM=1.0-2
CLS=USB  VNDR=Wacom  DEV=Cintiq (V5)  SUB=DTZ-12wx

```
but won't show any activity at all.

(xidump is v0.8.3 wacdump is v0.8.2)


If I use the 10-wacom.fdi (exact copy of Favux's but still attached for quick references) xinput list and xidump -l print a second "stylus" instead of the "Wacom Cintiq 12WX" and wacomcpl also recognise a second stylus.

xidump stylus doesn't work, probably because of the second sytlus.

Once xidump produced any output with any device and is restarted with any device, it will not print anything for any of the devices, except "1253062601 - MappingNotify" once I hit a touchstrip. (It also does this without the .fdi though not after the first restart but about 2-5 restarts later.)

wacdump's behavior is unaffected by the use of 10-wacom.fdi

In any case (i.e. with or without .fdi)
using 
```
xsetwacom set pad StripRDn "CORE KEY l"
```
during runtime works, changing the numbers for the buttons to, say... letters, works probably too (since it won't complain), but doesn't effect the missing output of these buttons.


So far I tested everything I could come up with and am pretty confused by the results of some of the tests. If anybody can make sense of this, or even better still, has an idea on how to fix this, I'd be more than happy to try it ^^

---

### Post by Favux on 2009-09-16
Hi Skiri-ki,

I don't think I'd upgrade to Karmic just yet.  At least until they fix this bug:  [https://bugzilla.gnome.org/show_bug.cgi?id=588649](https://bugzilla.gnome.org/show_bug.cgi?id=588649)  Also described here:  [https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/410267](https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/410267)

And did you mean linuxwacom 0.8.3-2?  The 0.8.2-2 version doesn't support Xserver 1.6.  The default 0.8.2-2 in Jaunty isn't vanilla, it has been specially patched to support 1.6 and HAL.

And for a little more information on setting up "dual monitors" with the Citiq see this thread, starting at about post #61 here:  [http://ubuntuforums.org/showthread.php?t=1035029&highlight=cintiq&page=7](http://ubuntuforums.org/showthread.php?t=1035029&highlight=cintiq&page=7)

Hope this is helpful.

---

### Post by Skiri-ki on 2009-09-16
Ah that's two mistakes on my side, I'm still using Jaunty and I assumed it was 0.8.2-2 because wacdump -V returned 0.8.2 and 0.8.2-2 was the only sources I had from 0.8.2-*. On hindsight I just realized that wacdump (probably) wasn't self compiled but came along with the Update to 9.04
I tried a lot of the drivers with various Problems and can't remember which one I finally used, how can I check this without having to try them all out again?

Regarding the dual monitor setup, both my monitor and my cintiq work perfectly in Tvinview and thanks to configuring with quirk-tablet-rescale I can switch the tablet area between them by touching the edges of the tablet. I'll read through the tread anyways and see if I can find something that might help me. Thanks ^^

Edit:
I also just realized that using an .fdi alongside of the xorg.conf is making it all rather pointless, so I commented the wacom specific lines out of it. The result is, that only the previously secondary stylus is recognized and the mapping on the tablet screen is off, as it uses the 3:4 ratio of my normal monitor. Not even calibrating is possible like this, since the lower right calibrating square is below the screen. If I specify TwinView and TVResolution in the fdi, the mapping is at least switching to the monitor if I hit the edge of the cintiq screen, where to it maps perfectly.

Also, could it be necessary to not only use the self-compiled wacom.ko, but the wacom_drv.so too?

---

### Post by Favux on 2009-09-17
Hi Skiri-ki,

That's right, you use either the xorg.conf or the wacom.fdi, not both.  If you use xorg.conf you lose usb hot plugging.

> Also, could it be necessary to not only use the self-compiled wacom.ko, but the wacom_drv.so too? 
That's possible.

With the Ubuntu packaged version you can determine the version using the changelog in /usr/share/doc/xserveer-xorg-input-wacom or through Sypnaptic Package Manager or querying the apt-get list.  As far as I'm aware you can't find version from a self compiled package other than the label on the source code tar.  As Ping Cheng from LWP said to the same question:
> Utility programs and drivers are versioned separately except they
packaged together since kernel driver follows the kernel base versions
and X driver follows its X driver base.  The easiest way to make sure
your liuxwacom pieces are in-sync is to run the following:

download the driver package and unzip/untar it, then

cd linuxwacom-0.7.8-2/prebuilt
su
./uninstall
./install
From:  [http://www.mail-archive.com/linuxwacom-discuss@lists.sourceforge.net/msg01061.html](http://www.mail-archive.com/linuxwacom-discuss@lists.sourceforge.net/msg01061.html)  Despite this, as you know, both packages have to be the same version or things break.

To uninstall a linuxwacom compile see Appendix 4 here:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)

---

### Post by Loïc2 on 2009-09-17
Timo Aaltonen just uploaded 0.8.4.1 wacom packages for Ubuntu 9.10 Karmic, I've tested them and they work fine with an Intuos3 tablet (the Cintiq is another story, but thanks to the threads posted here by Favux I should be able to configure it too).

The packages are in his PPA, at [[COLOR="Red"]https://edge.launchpad.net/~tjaalton/+archive/ppa[/COLOR]]("https://edge.launchpad.net/~tjaalton/+archive/ppa")

**He needs more testers to vouch for them, especially Intuos 4 users. Anybody with a tablet would make a big difference if they could test them and vouch for it (or not if it's worse) at [[COLOR="Red"]https://bugs.launchpad.net/bugs/405800[/COLOR]]("https://bugs.launchpad.net/bugs/405800")**


Timo has been responsible for the wacom packages (and many other things) in Ubuntu for a long while, so you shouldn't worry about their provenance, except for the fact that it's still Linux wacom drivers we're talking about :rolleyes:

Basically, you shouldn't expect an easier configuration than in Jaunty, but not worse either, and they have a few bugfixes + support Intuos4 tablet. They're also a stable release (and a bugfix one, since 0.8.4.1 is a bug fix of 0.8.4), better supported upstream than a random development release (plus it's the latest upstream too), so it would be worth have it in Karmic.

Thanks a lot Favux for helping Wacom users in Ubuntu (me included, since I've got to try getting the Cintiq to work in Karmic now).

By the way, when I tested 0.8.4.1 in Karmic, the cursor wasn't off in the Gimp, only in Inkscape, so it could be an improvement (not necessarily due to the wacom drivers by themselves, but nice to take ;) ).

Don't upgrade to Karmic yet though - I'd advise a new install on a separate partition, since 1. there's still daily changes into Karmic 2. there's still the bug with the new xorg and Wacom tablets, at least in Inkscape.

I'll try updating the wiki a bit for Karmic, but only when the Cintiq will work ;)

I also tested [http://www.gtk-apps.org/content/show.php?action=content&content=104309](http://www.gtk-apps.org/content/show.php?action=content&content=104309) (saw the link from Favux) and it works with the default .fdi file in Ubuntu, which is really nice (even though it doesn't do all wacomcpl can do, but the part it does are far better).

---

### Post by Favux on 2009-09-17
Hi Loïc2,

Very good to hear from you.

It would be great if Timo got 0.8.4-1 (or even 0.8.4-2, out yesterday) into Karmic.

I'm looking forward to hearing how your setup in Karmic goes.

---

### Post by lemmof on 2009-09-20
I have seen many other people with this problem, but I have not seen an answer.

I can scroll up, but not down.

AKA: Button 5 doesn't work.

This is with a Bamboo Fun in Jaunty.  Is there no solution?  Did I miss it?

---

### Post by Skiri-ki on 2009-09-21
So now I tired not only using the wacom.ko but actually using 'make install' on the self compiled driver (both 8.4-2 and 8.3-2). And the result is, Expresskeys are working, Twinview mapping is off. The cursor reaches the bottom when the pen tip is only about still about 1/5 of the screens hight away from it. For the monitor it's either the same or it's stretched on the 3:4 monitor so that I reach the bottom of the screen as I reach the end of the tablet. Depending on different settings in xorg.conf. 

I got kinda frustrated and tried to undo everything I had done, so that I'd get a setup like a clean install would have had, uncommented the wacom devices in xorg.conf, used the original .fdi, installed purged and reinstalled wacom-tools and xserver-xorg-input-wacom, but whether installed or not, neither 'xinput list' nor 'xidump -l' show any wacom devices, at all. Infact, /dev/input/wacom has disapeared and 'wacdump' on any of the events shows no tablet specific input.

You see, I kinda managed to blow up everything. So before I step back into the booby trapped labyrinth, has anyone suggestions as to which ones I should disarm first?

---

### Post by Favux on 2009-09-22
Hi Skiri-ki,

I think you may have lost me.  But if I'm following:

First comment out the Wacom stuff in the xorg.conf.  In fact if you have a "ServerLayout" section comment that out too.  The default Jaunty uses the default 10-wacom.fdi and a nearly bare xorg.conf with just the video sections.

It sounds like you may have knocked out the compiled wacom.ko without reinstalling the default Jaunty wacom.ko.  As you know it's at "/lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko" where "uname -r" is your current kernel.  If you don't have a backup for the wacom.ko you can get it by reinstalling your kernel's "linux-image" through Synaptic Package Manager.  This is discussed in Appendix 4 here:  [http://ubuntuforums.org/showthread.php?p=6546012#post6546012](http://ubuntuforums.org/showthread.php?p=6546012#post6546012)

Good luck!

---

### Post by Loïc2 on 2009-09-22
For those using Karmic, the bug in libgtk that results in the input being offset from the cursor in GTK drawing programs (Inkscape, The Gimp) has been fixed upstream and also in Karmic with libgtk2.0-0 version 2.18. Input is now right where the cursor is (in Screen mode of course).

---

### Post by strycore on 2009-09-22
I don't see why the desktop team wouldn't accept this patch as it's not a major release but only a bugfix. 
And it's a pretty important bugfix since tablets are unusable without it. 

For the window mode, it don't recall it has ever worked for me, even in older releases. (Well, older is relative because i didn't have a tablet before Jaunty). 
I don't know how the Window mode is supposed to work but for me it was something different than Relative Mode, more like Absolute mode but limited to the window.
Anyway the "Window mode" always had an offset but a variable one, the patched bug had a constant offset determined by the size of the windows borders, rulers and such. 

The real relative mode (which i set by typing   xsetwacom set "Wacom Volito2 4x5" Mode relative ) has never worked, the cursor is stuck in the top left corner of the window.

---

### Post by Skiri-ki on 2009-09-22
I went and commented the Sevrerlayout out as well now.I had Installed the Linux-Imgae before. I purged it and the Wacom pakages, Then installed the Image, After that I threw the wacom packages back in again. Still absolutely no contact made between the tablet and linux. (besides it working as a screen of course.) Did I have to do anything besides that like shuffling or deleting some files in-between? Because that's all I found in the appendix you mentioned.

Could I maybe download the original wacom.ko somewhere or the patched Sources? Just to be sure if this Linux-Image thing worked or not, because it seems like it does not install anything besides documentation.

Also, I'm downloading Karmic to install on a free partition and help out with the testing now.

---

### Post by Favux on 2009-09-22
Hi Skiri-ki,

The wacom.ko comes in the "linux-image" package.  You can check by searching for wacom.ko in Package Search:  [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

You could have a conflict between linuxwacom versions, I suppose, if you didn't quite clean up the installs.  Or something else could be messed up.

I had another thought.  Looking at your first post I can't tell if the Cintiq 12WX worked for you with the default Jaunty linuxwacom packages and wacom.ko.  Were you getting stylus function or other indications of usb communication, say with "dmesg | grep [Ww]acom"?  If not just how new is the Cintiq 12WX?  If it came out in the last few months maybe it has the same problem the Intuos4 has?  The default 0.8-2-2 wacom.ko isn't new enough to supply usb communication?

If so you could try compiling a newer linuxwacom just for the wacom.ko and installing that, not the rest of the compile.  You can use Section 1 in gali98's HOW TO in post #104 to do that:  [http://ubuntuforums.org/showthread.php?t=1038949&page=11](http://ubuntuforums.org/showthread.php?t=1038949&page=11)  Does this make sense to you?

---

### Post by andrew frank on 2009-10-04
i try to get karmic on tablet (a fujitsu) working - but do not understand evtouch and do not see how to get the buttons connected. could you give me a hint how you achieved this on karmic? the instructions in the forum with xorg.conf are outdated (i do not have an xorg.conf anymore)
thank you   
andrew

---

### Post by shnurui on 2009-10-05
> **Favux said:**
> Hi everyone,

As you have discovered it looks like the problems with wacomcpl and the xsetwacom commands come from the default Jaunty 10-wacom.fdi not parsing the names HAL is returning correctly for linuxwacom to understand.  Cyberfish came up with a .fdi that does parse the HAL names correctly and as modified by gali98 works for our usb tablet pc's.

I modified it for usb external graphics tablets.  K-buntu says it works on his Wacom Bamboo Fun.  Wacomcpl etc. work for him without having to rename anything.

If you're interested please test it and let me know if it works for you.  You can configure everything through wacomcpl (& .xinitrc) and xsetwacom as before.  You can also configure through the .fdi like you use to do with xorg.conf.  If it works for you please mention which tablet you have.  If you do not have, for eg. the Wacom mouse, you could remove the append cursor line in the first section and the cursor section following it.

Remember this modified 10-wacom.fdi is for the 0.8.2-2 linuxwacom packages that come "default" with Jaunty:  xserver-xorg-input-wacom & wacom-tools

Just move and save the default 10-wacom.fdi in /usr/share/hal/fdi/policy/20thirdparty/ somewhere safe (after changing .fdi to .bak say) and substitute the attached .fdi.  After renaming it 10-wacom.fdi of course.  One way to do this is the following:

-First download the attached .fdi to your desktop.
-Then make a back up of the current "default" Jaunty 10-wacom.fdi by typing in a terminal:
```
sudo cp /usr/share/hal/fdi/policy/20thirdparty/10-wacom.fdi /home/yourusername/Desktop/10-wacom.bak
```
Where "yourusername" is the user name you are using.  Check that the "wacom.bak" is now on your Desktop and has the correct contents by right clicking on it and 'Open as a "text file"'.  You can move it to wherever you want in Nautilus (Places) later.  Close it.
-Now open the current 10-wacom.fdi as root in gedit with:
```
gksudo gedit /usr/share/hal/fdi/policy/20thirdparty/10-wacom.fdi
```
Delete the entire contents (its safe, you've verified your backup).  Now copy and paste the entire contents of the downloaded modified wacom.fdi (you can right click on it and open it in another text editor) save and close.
-Reboot.

Now "xinput --list" and "xsetwacom list" entered in a terminal should agree with each other and return the linuxwacom names stylus, eraser, cursor (if you have the Wacom mouse), and pad.  With "xsetwacom list" working you are now able to use 'wacomcpl', the LWP's configuration and calibration gui.  Just enter 'wacomcpl' (without the quotes) in a terminal and the gui will pop up.  To set it up so that it's settings last through a reboot see "Section 3:  Calibrating your Tablet" here:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)

Intuos4 tablet users need a 'wacom.ko' (the usb kernel driver/module) newer than the default Jaunty 0.8.2-2 wacom.ko.  The default one doesn't allow usb communication to your tablet.  To compile the new 'wacom.ko' follow Section 1, and Section 1 only, of gali98's Jaunty HOW TO in post #104 here:  [http://ubuntuforums.org/showthread.php?t=1038949&page=11](http://ubuntuforums.org/showthread.php?t=1038949&page=11)

To further set up your pad see shatterblast's post #188 on the following page.  For the Intuous4 pad see also ceridwen's post #95 here:  [http://ubuntuforums.org/showthread.php?t=1120029&page=10](http://ubuntuforums.org/showthread.php?t=1120029&page=10)  That's the Intuos4 thread, lots of tips in it.

If the usb .fdi works for you maybe something analogous can be done with the serial tablet's subsection of the 10-wacom.fdi?

where do you download this "modified .fdi" from?

---

### Post by Favux on 2009-10-05
It's in the "Attached Files" at the bottom of the post.  Click on it.

---

### Post by shnurui on 2009-10-05
How do I add the pressure curve to this mess?
Sensitivity is the only thing not working.

<deviceinfo version="0.2">
  <device>
    <match key="info.category" contains="input">
      <match key="info.product" contains="Wacom">
	<merge key="input.x11_driver" type="string">wacom</merge>
	<merge key="input.x11_options.Type" type="string">stylus</merge>
        <append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
        <append key="wacom.types" type="strlist">eraser</append>
        <append key="wacom.types" type="strlist">cursor</append>
        <append key="wacom.types" type="strlist">pad</append>
      </match>
      <match key="info.product" contains="WALTOP">
	<merge key="input.x11_driver" type="string">wacom</merge>
	<merge key="input.x11_options.Type" type="string">stylus</merge>
        <append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
        <append key="wacom.types" type="strlist">eraser</append>
        <append key="wacom.types" type="strlist">cursor</append>
        <append key="wacom.types" type="strlist">pad</append>
      </match>
    </match>

---

### Post by gilou on 2009-10-05
> **Loïc2 said:**
> Timo Aaltonen just uploaded 0.8.4.1 wacom packages for Ubuntu 9.10 Karmic, I've tested them and they work fine with an Intuos3 tablet (the Cintiq is another story, but thanks to the threads posted here by Favux I should be able to configure it too).

The packages are in his PPA, at [[COLOR="Red"]https://edge.launchpad.net/~tjaalton/+archive/ppa[/COLOR]]("https://edge.launchpad.net/~tjaalton/+archive/ppa")

**He needs more testers to vouch for them, especially Intuos 4 users. Anybody with a tablet would make a big difference if they could test them and vouch for it (or not if it's worse) at [[COLOR="Red"]https://bugs.launchpad.net/bugs/405800[/COLOR]]("https://bugs.launchpad.net/bugs/405800")**


Timo has been responsible for the wacom packages (and many other things) in Ubuntu for a long while, so you shouldn't worry about their provenance, except for the fact that it's still Linux wacom drivers we're talking about :rolleyes:

Basically, you shouldn't expect an easier configuration than in Jaunty, but not worse either, and they have a few bugfixes + support Intuos4 tablet. They're also a stable release (and a bugfix one, since 0.8.4.1 is a bug fix of 0.8.4), better supported upstream than a random development release (plus it's the latest upstream too), so it would be worth have it in Karmic.

Thanks a lot Favux for helping Wacom users in Ubuntu (me included, since I've got to try getting the Cintiq to work in Karmic now).

By the way, when I tested 0.8.4.1 in Karmic, the cursor wasn't off in the Gimp, only in Inkscape, so it could be an improvement (not necessarily due to the wacom drivers by themselves, but nice to take ;) ).

Don't upgrade to Karmic yet though - I'd advise a new install on a separate partition, since 1. there's still daily changes into Karmic 2. there's still the bug with the new xorg and Wacom tablets, at least in Inkscape.

I'll try updating the wiki a bit for Karmic, but only when the Cintiq will work ;)

I also tested [http://www.gtk-apps.org/content/show.php?action=content&content=104309](http://www.gtk-apps.org/content/show.php?action=content&content=104309) (saw the link from Favux) and it works with the default .fdi file in Ubuntu, which is really nice (even though it doesn't do all wacomcpl can do, but the part it does are far better).

Hello!

This method with ppa from timo works great.
I use it with a graphire 4 in ubuntu karmic.

 The scroll was ok but no actions could be done with the two buttons.

After install of wacom-tools and xserver-input-wacom from the ppa, there's also need to create a xorg.conf file reffering to wacom devices. Mine is : 

```

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	#Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
	Option		"PressCurve"	"50,0,100,50"# Custom preference
	Option		"Mode"	"Absolute"
	#Option	"Mode"		"Relative"
Option "USB" "on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	#Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
	Option		"PressCurve"	"50,0,100,50"# Custom preference
	Option		"Mode"	"Absolute"
	#Option	"Mode"		"Relative"
Option "USB" "on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	#Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
	Option		"Mode"	"Absolute"
	#Option	"Mode"		"Relative"
Option "USB" "on"
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "pad"
Option "Device" "/dev/input/wacom"
#Option "Device" "/dev/input/tablet-graphire4-4x5"
Option "Type" "pad"
Option "USB" "on"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
 	Screen "Default Screen"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
	InputDevice "pad"	"SendCoreEvents"
EndSection

```

Of course you need to restart X, and then xsetwacom works fine with buttons and scroll. I didn't try wacomcpl.

I prefer this method as we don't touch to hal files.


gilou

---

### Post by PeterH1 on 2009-10-05
Okay, I'm not sure if something similar was asked somewhere in the 30 pages of this thread that I didn't read (really, it is a lot), but I couldn't find anything like this anywhere. Please tell me I'm missing something incredibly simple here, I hate digging through terminal and stuff. Alright, so basically, I am running Ubuntu 9.04, and I bought a new Wacom Bamboo Fun (touch and pen), and it does not seem to be recognized. It doesn't function as a mouse or anything, but the lights light up and it behaves as though it's being used. I checked and made sure that this tablet is supported by the driver and it is. I also checked to make sure the hardware is fine by running it under Vista and everything worked smoothly. So now I'm at a loss.   System: Acer Extensa 5620-4621 Ubuntu 9.04 (64-bit)

---

### Post by shnurui on 2009-10-06
> **PeterH1 said:**
> Okay, I'm not sure if something similar was asked somewhere in the 30 pages of this thread that I didn't read (really, it is a lot), but I couldn't find anything like this anywhere. Please tell me I'm missing something incredibly simple here, I hate digging through terminal and stuff. Alright, so basically, I am running Ubuntu 9.04, and I bought a new Wacom Bamboo Fun (touch and pen), and it does not seem to be recognized. It doesn't function as a mouse or anything, but the lights light up and it behaves as though it's being used. I checked and made sure that this tablet is supported by the driver and it is. I also checked to make sure the hardware is fine by running it under Vista and everything worked smoothly. So now I'm at a loss.   System: Acer Extensa 5620-4621 Ubuntu 9.04 (64-bit)

did you install the wacom driver and tools from your system<admin<synaptic package manager?

Search for Wacom, and turn them on., if on, reinstall them.

---

### Post by Loïc2 on 2009-10-06
> **PeterH1 said:**
> Alright, so basically, I am running Ubuntu 9.04, and I bought a new Wacom Bamboo Fun (touch and pen), and it does not seem to be recognized. It doesn't function as a mouse or anything, but the lights light up and it behaves as though it's being used.
As shnurui just said, check first if the packages xserver-xorg-input-wacom and wacom-tools are already installed on your system - if not, install them (see [COLOR="Red"]https://help.ubuntu.com/community/Wacom[/COLOR]). Then reboot and  [COLOR="Red"][configure the "Extended Input Devices"]("https://help.ubuntu.com/community/Wacom#Configuring%20the%20%22Extended%20Input%20Devices%22")[/COLOR] and you should see your input devices appear along with the model of your tablet.

If there's a problem, use ```
xinput list
``` in a terminal, and see if the Wacom devices show.

---

### Post by da_Seeb on 2009-10-06
> hello,

trying to get a wacom bamboo running with ubuntu jaunty. Just downloaded, compiled and installed the linuxwacom 0.8.4-2 source.

Now only the stylus is working without ability to "click".

"xinput --list" gives the following output

[...]
"Wacom BambooFun 4x5"   id=5    [XExtensionPointer]
        Num_buttons is 32
        Num_axes is 2
        Mode is Absolute
        Motion_buffer is 256
        Axis 0 :
                Min_value is 0
                Max_value is 14760
                Resolution is 10000
        Axis 1 :
                Min_value is 0
                Max_value is 9225
                Resolution is 10000
[...]

So.. only two axis... that explains why I can only move the cursor... 

But eraser, pad etc is not shown anyway.


EDIT: Fixed this one! Had to install xserver-xorg-input-wacom before doing make install.

-----------------------------------------------------------------

Another problem:
###############

"xsetwacom set "Wacom BambooFun 4x5" Twinview none" gives segfault

What could be wrong here?

I have two 4:3 monitors connected to a ATI graphics card and fglrx driver. One monitor is right of the other and multi head is configured with xrandr. Now I want the bamboo to work only on the first monitor so I can use the tablet area better. Have tried several things with xsetwacom but could not get the desired result.... :(

---

### Post by PeterH1 on 2009-10-06
Sorry for the delay, I just got back. Yes, I'm quite sure that both Wacom-Tools and Xorg... are installed. They're all green in Synaptic. I had heard about and tried the "xinput" thing before, but I wasn't sure if it was not showing wacom or was just being cryptic about it. Here is the output: 
```
peter@peter-laptop:~$ xinput list
"Virtual core pointer"    id=0    [XPointer]
    Num_buttons is 32
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 0
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 0
"Virtual core keyboard"    id=1    [XKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"AT Translated Set 2 keyboard"    id=2    [XExtensionKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Video Bus"    id=3    [XExtensionKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Macintosh mouse button emulation"    id=4    [XExtensionPointer]
    Num_buttons is 32
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
"SynPS/2 Synaptics TouchPad"    id=5    [XExtensionPointer]
    Num_buttons is 12
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is 1472
        Max_value is 5472
        Resolution is 1
    Axis 1 :
        Min_value is 1408
        Max_value is 4448
        Resolution is 1
peter@peter-laptop:~$ 
```
Thanks for the quick response by the way.

EDIT: Woooow. Yeah, I can't believe I actually did that. I really had used that before, I guess I was just tired when I was typing this up. Anyway, this is the result of xinput list. I can't find wacom anywhere in it.

---

### Post by Loïc2 on 2009-10-07
> **da_Seeb said:**
> Another problem:
"xsetwacom set "Wacom BambooFun 4x5" Twinview none" gives segfault


That's a bug with linuxwacom 0.8.4.2. Previous versions don't suffer from it, pick any other one you want. Basically, your tablet should have been supported by the linuxwacom drivers shipped in Jaunty - is there any special feature you needed?

Also, could you please edit your quotes (only leaving the relevant line(s) ) so the page number doesn't grow too big (an user just complained the thread was too big ;) ).

> **PeterH1 said:**
> 
```
peter@peter-laptop:~$ xinput
usage :
    xinput get-feedbacks <device name>
(...)
    xinput list [--loop || --short || <device name>...]
peter@peter-laptop:~$ 
```


You need to type "xinput list" and not just "xinput". Please just edit you post above (what you quoted was just xinput list of options ;) ) - if "xinput list" output is big, just quote the relevant Wacom parts.

---

### Post by Allochtoon on 2009-10-10
Hi all, recently got my intuos 4 tablet working. I am left-handed and had to set this in x.org. 

However this X.org setting produces double (there are 8 ) devices showing up in The Gimp and Inkscape, because the driver creates the other 4.

Everytime i unplug the wacom i have to restart X to set it to left-handed mode.

When i restart The Gimp all the (wacom) input device settings get defaulted.

wacomcpl settings dont seem to work.

Is it possible to shift through the 4 shift modes of the "dialpad"?

How do i sort out these issues and program the buttons? I read that the OLED display isn't supported.

---

### Post by Favux on 2009-10-10
Hi Allochtoon,

Have you looked at post #176 here?:  [http://ubuntuforums.org/showthread.php?t=967147&page=18](http://ubuntuforums.org/showthread.php?t=967147&page=18)

After you're setup with wacomcpl working you could add to your .xinitrc script:
```
xsetwacom set stylus rotate HALF
xsetwacom set eraser rotate HALF
xsetwacom set cursor rotate HALF
```
or to the .fdi:
```
<merge key="input.x11_options.Rotate" type="string">HALF</merge>
```

---

### Post by Loïc2 on 2009-10-11
> **Allochtoon said:**
> However this X.org setting produces double (there are 8 ) devices showing up in The Gimp and Inkscape, because the driver creates the other 4.

Do those 4 duplicated devices have the same name as the 4 other ones?

Also, could you attach (not paste) your /etc/X11/xorg.conf to your post, and if you really want to use xorg.conf instead of the Ubuntu method, did you make sure to remove /usr/share/hal/fdi/policy/20thirdparty/10-linuxwacom.fdi ?

---

### Post by Allochtoon on 2009-10-12
Favux and Loïc2, thanks a bunch for your help. I removed all the lines in xorg.conf and now use the shell script for assigning the buttons and rotating the tablet. No .fdi aswell.

I now have 4 devices which i can correctly program in the gimp. Works great now.

OLED support and the dialpad shift functions are discussed here:
[http://www.nabble.com/Express-Keys-LED-OLED-Support-on-Intuos4--td25498409.html](http://www.nabble.com/Express-Keys-LED-OLED-Support-on-Intuos4--td25498409.html)

Seems to me it will be supported eventually.

---

### Post by Loïc2 on 2009-10-12
> **PeterH1 said:**
> Anyway, this is the result of xinput list. I can't find wacom anywhere in it.

Your tablet is quite recent, so it may be worth trying under Karmic. Could you boot a Karmic LiveCD, install wacom-tools in the live session, then plug your tablet and try "xinput --list" again?

---

### Post by PeterH1 on 2009-10-12
Good idea Loïc2, I'll give it a try. I'll edit back here when I'm done.

Edit: Okay, well I booted up with the Karmic Beta Live CD, and still had no responsive from my Wacom. I did the xinput list (and remembered list this time), and only found one thing different. There seems to be an extra entry: 

```
"Power Button"    id=4    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
```

But that's about it. Funny thing too, my touchpad wouldn't let me click with a tap, I had to use the button. Hm... Thanks for the help.

---

### Post by Allochtoon on 2009-10-13
which driver are you using? make sure u use wacom.ko if you have 2.6 kernel and are compiling.

---

### Post by PeterH1 on 2009-10-14
Okay, so I tried out the live CD as I said and it didn't work, but I'm thinking that actually makes sense. I mean, it doesn't work in the Fedora live CD either, and a live CD really doesn't need support for these things. I suppose that also explains why my mouse-click didn't work. I looked over the instructions for installing the Linuxwacom driver, and encountered the same problem that I had before (when I tried to install it in a different version). Typing: make /proc/bus/usb/devices , tells me that there is no such file or directory. I'm wondering if the Karmic idea is still worth a shot. Do you think I should try upgrading my Jaunty to Karmic Beta?

---

### Post by Allochtoon on 2009-10-14
> **PeterH1 said:**
> Okay, so I tried out the live CD as I said and it didn't work, but I'm thinking that actually makes sense. I mean, it doesn't work in the Fedora live CD either, and a live CD really doesn't need support for these things. I suppose that also explains why my mouse-click didn't work. I looked over the instructions for installing the Linuxwacom driver, and encountered the same problem that I had before (when I tried to install it in a different version). Typing: make /proc/bus/usb/devices , tells me that there is no such file or directory. I'm wondering if the Karmic idea is still worth a shot. Do you think I should try upgrading my Jaunty to Karmic Beta?

Try *On newer 2.6 systems, more /proc/bus/input/devices gives you*

As i said, you have to pay attention to the kernel version which the manual refers to. As problably is the case, and if that command will show no connected Wacom devices then continue the manual.
[http://linuxwacom.sourceforge.net/index.php/howto/testtablet](http://linuxwacom.sourceforge.net/index.php/howto/testtablet)

---

### Post by PeterH1 on 2009-10-14
> **Allochtoon said:**
>  As i said, you have to pay attention to the kernel version which the manual refers to. As problably is the case, and if that command will show no connected Wacom devices then continue the manual.
[http://linuxwacom.sourceforge.net/index.php/howto/testtablet](http://linuxwacom.sourceforge.net/index.php/howto/testtablet)

Woops. Yeah, I didn't try that command. Unfortunately, I won't be able to either until Gnome stops freezing. I went ahead and upgraded to Karmic. I figured I'd probably like to try it out anyway. Things were going alright until I tried to flatten my cube (by pressing control-alt-down). It froze there, so I restarted. Now it freezes every time I try to open in gnome. It'll start a session in failsafe-gnome, and in KDE, but it dies in gnome. I'm puzzled because I can't seem to find the network manager in failsafe-gnome, so I can't reinstall anything from there. Arg.

---

### Post by Favux on 2009-10-14
Hi PeterH1,

I'm pretty sure your model has the Product ID 0xd1 like TheguywholikesLINUX's tablet.  That model isn't supported by linuxwacom yet up to including 0.8.4-3.  You can check with lshal:
```
lshal>lshal.txt
```
or
```
lsusb
```
The good news is that kgingeri has nearly figured out how to add support for it to 0.8.4-3 and Ping Cheng has already said he'd accept a patch to the source code for 0.8.4-4 if kgingeri can get a tester or two verify it.  Please see this thread:  [http://ubuntuforums.org/showthread.php?t=1290251&highlight=tablet](http://ubuntuforums.org/showthread.php?t=1290251&highlight=tablet)

---

### Post by hocmin on 2009-10-14
I have a Wacom Bamboo 6x8 that worked find when I followed this guide back in the day ([http://ubuntuforums.org/showthread.php?t=765915]("http://ubuntuforums.org/showthread.php?t=765915")).  Now trying to follow HAL and running into some issues.  I followed Favux's guide ([http://ubuntuforums.org/showpost.php?p=7234134]("http://ubuntuforums.org/showpost.php?p=7234134")) and everything seemed to look good, with wacomcpl giving me the devices (style, pad, cursor, erasor).  However, only the buttons and the scroll wheel on the pad work.  The pad doesn't pick up on the stylus.  Thought it might be some bad luck and the stylus "went bad" but the mouse that came with it doesn't work on the pad either.  I've checked my xorg.conf and it's clean.  I see wacom in both lsusb and lshal (which I suppose is a "duh" since the buttons work).

I'm on Jaunty with a x86_64.  Attached is my xinput --list.  Thanks for any help.

---

### Post by Favux on 2009-10-14
Hi hocmin,

Your xinput looks right and you say everything shows up in wacomcpl.  Is there a specific program the stylus and puck are not working in or is it in general?

---

### Post by PeterH1 on 2009-10-14
Favux, Thank you, it appears that you are correct. I typed in lsusb, and discovered the wacom was in the list with ID 056a:00d1. If indeed there is no support for this yet, then I'll just use it in Win 7, and focus on the cool stuff that Ubuntu can do right now. Thanks for the help.

---

### Post by Loïc2 on 2009-10-15
> **PeterH1 said:**
> Okay, so I tried out the live CD as I said and it didn't work, but I'm thinking that actually makes sense. I mean, it doesn't work in the Fedora live CD either, and a live CD really doesn't need support for these things.
For the record, it does. If a tablet is supported by the linuxwacom drivers version offered by the distribution release, then it will work with the LiveCD, including pressure (can be tested with the Gimp, just need to configure the Extended Input Devices menu in the Gimp's preferences.

And if the version in the release you want to test has been updated since the LiveCD has been issued, updating while in the Live session (then maybe restarting X) should give about the same results.

> **PeterH1 said:**
> Unfortunately, I won't be able to either until Gnome stops freezing. I went ahead and upgraded to Karmic. I figured I'd probably like to try it out anyway. Things were going alright until I tried to flatten my cube (by pressing control-alt-down). It froze there, so I restarted. Now it freezes every time I try to open in gnome. It'll start a session in failsafe-gnome, and in KDE, but it dies in gnome. I'm puzzled because I can't seem to find the network manager in failsafe-gnome, so I can't reinstall anything from there. Arg.

Just switch to a Virtual Terminal (VT) at the login screen (or any time later) by pressing CTRL-ALT-F1 (up to F5 AFAIR) once or twice, and back to X with CTRL-ALT-F7. In the VT you can login as your user, and you've got a few options:
- nuke compiz configuration directory ```
rm -rf .compiz
``` and retry to login;
- create a new user ```
sudo adduser whatever_name_you_fancy
``` then back to X and login as this user. Then give him admin rights with System>Administration>User and Groups (obtaining security rights by selecting you first account when requested for an admin  autorization and using its password. With the new user you can do whatever you want graphically.

I don't have a clue where Gnome stores the settings for System>Preferences>Apparence, if you have it you could just edit the file and change the value, but the two above solutions should work.

---

### Post by Loïc2 on 2009-10-15
hocmin:
- did you do a clean reinstall or an upgrade?
- you shouldn't need wacomcpl (or changing the devices names to stylus/eraser/etc) with a tablet like that, unless you're using a dual screen setup.

Basically, with a supported tablet and a single screen setup, it might be better to just use Ubuntu (or Fedora, or whatever recent distribution) default setup first. To configure the devices, use a more recent tool than the ages-old wacomcpl, like the one at [http://www.gtk-apps.org/content/show.php/Wacom+Control+Panel?content=104309](http://www.gtk-apps.org/content/show.php/Wacom+Control+Panel?content=104309)
It should work with the new Wacom names, and then you only need to configure the Extended Input Devices in the graphic program of your choice.

That way, if something goes bad you can be sure it's Ubuntu default configuration, not a mistake from your part. Then the bug can be reported and hopefully fixed, while you can still start fiddling with a custom configuration later.

For example, on Karmic Beta I can just plug my tablet and start working with it. I only need to change the default .fdi file because I have a Cintiq that I want to use along the main monitor, the Intuos doesn't require any changes except settings that the app linked above (or a set of xsetwacom commands).

---

### Post by hocmin on 2009-10-15
> **Favux said:**
> Hi hocmin,

Your xinput looks right and you say everything shows up in wacomcpl.  Is there a specific program the stylus and puck are not working in or is it in general?
It's everything.  Before trying your guide I was following along with the guide from The Linux Wacom Project.  I was able to run wacdump on one of my events and I saw output for only the buttons; the position info and such never changed.  I'm not sure if it means anything, but since following your guide I haven't been able to find a device in /dev that gives me either now, but then I was really tired and frustrated last night. :-P

I'm taking it work today to see if it works on a windows machine.

---

### Post by hocmin on 2009-10-15
> **Loïc2 said:**
> hocmin:
- did you do a clean reinstall or an upgrade?
- you shouldn't need wacomcpl (or changing the devices names to stylus/eraser/etc) with a tablet like that, unless you're using a dual screen setup.

Basically, with a supported tablet and a single screen setup, it might be better to just use Ubuntu (or Fedora, or whatever recent distribution) default setup first. To configure the devices, use a more recent tool than the ages-old wacomcpl, like the one at [http://www.gtk-apps.org/content/show.php/Wacom+Control+Panel?content=104309](http://www.gtk-apps.org/content/show.php/Wacom+Control+Panel?content=104309)
It should work with the new Wacom names, and then you only need to configure the Extended Input Devices in the graphic program of your choice.

That way, if something goes bad you can be sure it's Ubuntu default configuration, not a mistake from your part. Then the bug can be reported and hopefully fixed, while you can still start fiddling with a custom configuration later.

For example, on Karmic Beta I can just plug my tablet and start working with it. I only need to change the default .fdi file because I have a Cintiq that I want to use along the main monitor, the Intuos doesn't require any changes except settings that the app linked above (or a set of xsetwacom commands).

For Jaunty?  I did an upgrade.  Been upgrading since 8.04, I believe.  If you're referring to clean install/upgrade with regard to the wacom drivers, I'm not sure what you mean.

I do have a dual monitor setup.

To go the default setup route, what would I need to do?  Simply replace the custom fdi with the old and try the more recent tools?

---

### Post by hocmin on 2009-10-15
Just tried getting my wacom to work on my windows work machine.  It appears the pad still isn't working (buttons do).  Going to try buying another pen but it looks like it wasn't a software issue.  Thanks for the help.

---

### Post by kcallis on 2009-10-16
The wacom stuff seems to be working for me just fine under 9.04 as well as beta 9.10. I am using a Toshiba R25-S3513 and just interested in one thing. I would love to make use of my tablet as a tablet. I want the auto rotation to work; The ability to get a decent virtual keyboard in place, etc. 
Does anyone have any how-to to get that working?

---

### Post by Favux on 2009-10-16
Hi kcallis,

There is a Rotation HOW TO here:  [http://ubuntuforums.org/showthread.php?p=6274392](http://ubuntuforums.org/showthread.php?p=6274392)

And a mini HOW TO on onscreen keyboards in post #8 here:  [http://ubuntuforums.org/showthread.php?t=1259154](http://ubuntuforums.org/showthread.php?t=1259154)  Unless you have a slate form factor I don't find it that useful.  I just install CellWriter and hide it in laptop and show it in tablet mode.  Up to you.

---

### Post by n1ete on 2009-10-22
Hi, i installed karmic yesterday on my x61 tablet and try to the wacom tablet is working out of the box but i get no devices in wacomcpl so tried this:

```
sudo gedit /etc/init.d/wacomtohal
``` and paste this code in: 
 ```
#! /bin/sh
## find any wacom devices
for udi in `hal-find-by-property --key input.x11_driver --string wacom`
do
type=`hal-get-property --udi $udi --key input.x11_options.Type`
## rewrite the names that the Xserver will use
hal-set-property --udi $udi --key info.product --string $type
done
``` then run : 
 ```
sudo chmod +x /etc/init.d/wacomtohal
sudo update-rc.d wacomtohal defaults 27
```after reboot the eraser and the touch config is shown in wacomcpl but no stylus config?

after this i tried the how-to from post #176 but nothing shows up in wacomcpl....

where is my error?
thanks and hi to everyone

---

### Post by MarilenCorciovei on 2009-10-22
I have just bought a Wacom Bamboo Pen and it worked like a charm on my Ubuntu Jaunty. Everything works in absolute mode but whenever I switch to "relative" mode the presure does not work anymore. I've also tried the linuxwacom-0.8.4-3 with the same behaviour.

xsetwacom set "Wacom Bamboo1" mode 0 (relative) => presure stops working
xsetwacom set "Wacom Bamboo1" mode 1 (absolute) => presure works ok.

I've googled it and searched this forum for hours without finding the same problem described. Does anywone knows of a solution?

Thanks in advance,
Len

---

### Post by Favux on 2009-10-23
Hi n1ete,

Welcome to Ubuntu Forums!

My suggestion is to try the Karmic release candidate out today and see if it fixes the problem.

There seems to be something wrong with Karmic beta for serial tablet pc's (and serial tablets?).  Some Fujitsu tablets do not see their stylus, the same as you:  [http://ubuntuforums.org/showthread.php?t=1280564&highlight=fujitsu](http://ubuntuforums.org/showthread.php?t=1280564&highlight=fujitsu)  And the bug report:  [https://bugs.edge.launchpad.net/ubuntu/+source/wacom-tools/+bug/383181](https://bugs.edge.launchpad.net/ubuntu/+source/wacom-tools/+bug/383181)  Also a Toshiba portege M750 reports the stylus is behaving strangely.  See starting with post #597 here:  [http://ubuntuforums.org/showthread.php?t=1038949&page=60](http://ubuntuforums.org/showthread.php?t=1038949&page=60)

You were right to use Rec's script, wacomtohal, since you have a serial tablet pc.  The wacom.fdi in post #176 on this thread is for usb tablets so it won't work for you.

Hope this helps.

---

### Post by Ubuntu Terrier on 2009-10-23
Hi all. I hope somebody can help me solve this rather annoying problem I have with my Intuos4 Medium tablet and Ubuntu.

On some areas on the corners of the tablet the pointer tends to wobble abnormally (it shakes) even though the pen is perfectly still.

I used to have Ubuntu 9.04 installed on my pc, but I couldn't bare this problem and in the end I reverted to Windows, where the stylus works flawlessly. I recently downloaded Ubuntu 9.10 RC and tried to install it on another pc to see if the problem in the mean time has been corrected, but even with a new OS and another PC, the wobbling problem is still there.

I tried to install a new wacom.ko kernel module from the newly released 0.8.5 development linux wacom drivers, but with no luck. This problem appears to be occurring only on Linux :(

If I increase the Suppress value to higher values (30-40) this issue is somewhat mitigated, but at the cost of a sluggish cursor response. It's not really a viable solution.

Does anybody else have this rather annoying problem on Ubuntu with the Intuos4 tablet?
Again, the tablet works perfectly on Windows.

---

### Post by amalgamis on 2009-10-23
I've spent the last two hours trying to configure my Intuos4 (large) to no avail.

Ubuntu 9.04
installed: wacom-tools 1:0.8.2.2-0ubuntu2
installed: xserver-xorg-input-wacom 1:0.2.2.2-0ubuntu2
have the wacom.ko kernal in /lib/modules/2.6.28-11-generic/kernal/drivers/input/tablet
Activated driver from Wacom install cd

I've attached my xorg.conf file which has a plethora of HAL comments in it and clearly shows no configuration for Wacom. Any help would be greatly appreciated. Cheers!

---

### Post by Favux on 2009-10-23
Hi amalgamis,

Welcome to Ubuntu Forums!

I'm not sure what:
> Activated driver from Wacom install cd
means.

Basically you need a newer wacom.ko (and only the wacom.ko) than the one provided with your Jaunty install (in the linux-images kernel package).  See post #176 on this thread here:  [http://ubuntuforums.org/showthread.php?t=967147&page=18](http://ubuntuforums.org/showthread.php?t=967147&page=18)  It gives you links to the HOW TO that shows you about compiling a wacom.ko and the Intous4 thread.

Hope this helps.

---

### Post by Loïc2 on 2009-10-23
> **amalgamis said:**
> I've spent the last two hours trying to configure my Intuos4 (large) to no avail.

Ubuntu 9.04
installed: wacom-tools 1:0.8.2.2-0ubuntu2
installed: xserver-xorg-input-wacom 1:0.2.2.2-0ubuntu2

0.8.2.2 doesn't support Intuos4 models. Ubuntu 9.10, to be released in 5 days, has 0.8.4 which should have partial support for your tablet.

I suggest you wait for Ubuntu 9.10 (or install the RC if you can't), or even just try booting an Ubuntu 9.10 RC LiveCD and plugging your tablet in the Live session. Don't try to change the defaults settings at first, just enable the extended input devices in your drawing program(s) and you should have it working. Only then should you start tweaking - if there's special settings you would like to change.

(or you can keep Jaunty and change the wacom.ko like Favux suggests, but else there's not much reasons to stick with Ubuntu 9.04 since it's not a LTS)

---

### Post by amalgamis on 2009-10-23
Thanks for the speedy response! 

I just edited the message to include info about the Wacom kernal: wacom.ko kernal in /lib/modules/2.6.28-11-generic/kernal/drivers/input/tablet

I followed a tutorial on this forum (unfortunately don't have the link) to get that into place, and everything went smoothly. Do I still need to go through the steps of your tutorial? I apologize for my knowledge being so elementary.

EDIT: good to know. Time to address the wacom.ko and see if I can fix this.

---

### Post by amalgamis on 2009-10-23
> **Favux said:**
> 
Basically you need a newer wacom.ko (and only the wacom.ko) than the one provided with your Jaunty install (in the linux-images kernel package).  See post #176 on this thread here:  [http://ubuntuforums.org/showthread.php?t=967147&page=18](http://ubuntuforums.org/showthread.php?t=967147&page=18)  It gives you links to the HOW TO that shows you about compiling a wacom.ko and the Intous4 thread.


Thanks for the warm welcome the forums!

I followed post #176 until the point where you say to compare "xinput --list" and "xsetwacom list", as "xsetwacom list" returns nothing in the terminal. I've attached the output of "xinput --list" below.

---

### Post by Favux on 2009-10-23
Hi amalgamis,

What your 'xinput --list' shows is that you haven't established usb communication with your tablet yet.  That's why there aren't any Wacom entries.  Did you reboot after installing the .fdi and wacom.ko?

Try compiling and installing the wacom.ko as per this HOW TO in post #104:  [http://ubuntuforums.org/showthread.php?t=1038949&page=11](http://ubuntuforums.org/showthread.php?t=1038949&page=11)  Remember just do "Section 1: Download source code, compile, and install linuxwacom kernel driver/module".  You are not installing a different version of linuxwacom.

---

### Post by amalgamis on 2009-10-23
> **Favux said:**
> Hi amalgamis,

What your 'xinput --list' shows is that you haven't established usb communication with your tablet yet.  That's why there aren't any Wacom entries.  Did you reboot after installing the .fdi and wacom.ko?

Try compiling and installing the wacom.ko as per this HOW TO in post #104:  [http://ubuntuforums.org/showthread.php?t=1038949&page=11](http://ubuntuforums.org/showthread.php?t=1038949&page=11)  Remember just do "Section 1: Download source code, compile, and install linuxwacom kernel driver/module".  You are not installing a different version of linuxwacom.

I've been rebooting as necessary in the tutorials. I had compiled and installed the wacom.ko as per the post you listed above before I asked for help here. I went ahead and tried it again, rebooted, stepped back through post #176, rebooted again, and just ran "xinput --list" and "xsetwacom list" with the same results from before. "xsetwacom list" returns nothing, and the output supplied by "xinput --list" is identical to that I pasted in the post above.  

The tablet is definitely connected (the LED light on it indicates so), so I'm a bit stumped. The only thing that I can come with is that perhaps this has to do with being connected to my Lenovo Mini-dock as opposed to a USB port on the laptop itself. The Microsoft mouse listed in the xinput output is attached to the dock via USB as well.

---

### Post by Favux on 2009-10-23
Hi amalgamis,

Sorry I didn't realize you had already run through gali98's HOW TO.

For some setups the wacom.ko doesn't auto-load for some reason.  I don't know why.  In a terminal:
```
lsmod
```
should show 'wacom', which is the wacom.ko kernel driver/module.  If it isn't there there is a way to 'force' it to load.  In "/etc/" add "wacom" (without the quotes) to the end of the "modules" file using:
```
gksudo gedit /etc/modules
```
Then reboot.  See if that does the trick.

---

### Post by amalgamis on 2009-10-23
> **Favux said:**
> Hi amalgamis,

Sorry I didn't realize you had already run through gali98's HOW TO.

For some setups the wacom.ko doesn't auto-load for some reason.  I don't know why.  In a terminal:
```
lsmod
```
should show 'wacom', which is the wacom.ko kernel driver/module.  If it isn't there there is a way to 'force' it to load.  In "/etc/" add "wacom" (without the quotes) to the end of the "modules" file using:
```
gksudo gedit /etc/modules
```
Then reboot.  See if that does the trick.

Voila!

So, the pen is now responding, but the Wacom mouse is not.

Thanks for walking through all of this with me.

---

### Post by Favux on 2009-10-23
Hi amalgamis,

Good!  Not a problem.  You're welcome.

I can't remember if the Wacom mouse (puck) was a problem for other Intuos4 users.  You can look through the same thread that ceridwen's pad post is on.

---

### Post by amalgamis on 2009-10-23
> **Favux said:**
> Hi amalgamis,

Good!  Not a problem.  You're welcome.

I can't remember if the Wacom mouse (puck) was a problem for other Intuos4 users.  You can look through the same thread that ceridwen's pad post is on.

I just discovered that the mouse works as long as it isn't resting on the tablet, but held just above it. Haha, strange...

---

### Post by amalgamis on 2009-10-24
Somewhere throughout our steps in activating the Wacom my soundcard was disabled. I've tried muting and unmuting different audio controllers to no avail. Any suggestions would be greatly appreciated.

---

### Post by Favux on 2009-10-24
Hi amalgamis,

You may have knocked out something in /etc/modules.  Did you make a backup or do you remember what it looked like?  Just make sure something isn't garbled now and wacom is last and on it's own line.

Was there something like "fuse" in there?

---

### Post by amalgamis on 2009-10-24
> **Favux said:**
> Hi amalgamis,

You may have knocked out something in /etc/modules.  Did you make a backup or do you remember what it looked like?  Just make sure something isn't garbled now and wacom is last and on it's own line.

Was there something like "fuse" in there?

Here is /etc/modules/ file as viewed in gedit:
```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc
sbp2
wacom

```
The only thing I changed was adding 'wacom' to the last line. I already tried removing 'wacom' and restarting the ubuntu, which deactivated the Wacom tablet but still did not repair the audio.

---

### Post by Favux on 2009-10-24
Hi amalgamis,

I don't know if "fuse" belongs in there in Jaunty but you could try it.  Put it before "wacom".

That's the only thing/place I can think of that would have disabled sound.  Everything looks fine in modules.  I don't see how anything else you did would affect sound.

We are way off topic and I don't know much about sound.  You may want to start a thread.  First find out what your sound card is:
```
aplay -l
```
See if that's the input selected.  Make sure all your sliders are up including PCM.  Make sure output is analog if your speakers are analog.

---

### Post by amalgamis on 2009-10-24
> **Favux said:**
> Hi amalgamis,

I don't know if "fuse" belongs in there in Jaunty but you could try it.  Put it before "wacom".


Hats off to you, again! I'm baffled as to why this worked, since it was never there in the first place, but at this point I'm tempted not to question a good thing. I now have a working Wacom tablet, and audio! Life is good. Thanks again for lending a hand.

---

### Post by DejitaruJin on 2009-10-28
Some searching led me here - specifically, to post #176, and the modified fdi file. However, rather than make the tablet show up in wacomcpl, the device still isn't listed, *and* I've lost scroll wheel support. This seems to be a problem.

I've got a Graphire4, on Karmic. I haven't messed around with the tablet prior to this, because the prospect of configuring it via CLI is *terrifying* ;)

Edit: Scratch that. The solution was... a power outage, apparently. Don't know, don't care, it works now :P

---

### Post by chris7777 on 2009-10-31
I am having problems with my graphire 4 working properly.  everything seems to work, except when I right click, it is like it registers it as a click, and paste for example, when I want to copy, I have to use edit to cut and paste.  is there a panel to adjust the settings?

---

### Post by Allochtoon on 2009-11-04
Hi all. In 9.10 my intuos4 is working without any configuration, that's great.  I still however have to run the following script to rotate the orientation and map the buttons. Can i automate this?

```
#script for lefthanded intuos 4 in The Gimp   

#flip to lefthanded mode
xsetwacom set 'Wacom Intuos4 6x9' rotate HALF
xsetwacom set 'Wacom Intuos4 6x9 eraser' rotate HALF
xsetwacom set 'Wacom Intuos4 6x9 cursor' rotate HALF
xsetwacom set 'Wacom Intuos4 6x9 pad' rotate HALF

#touchdial + middle button
xsetwacom set 'Wacom Intuos4 6x9 pad' AbsWDn "CORE KEY +" #clockwise
xsetwacom set 'Wacom Intuos4 6x9 pad' AbsWUp "CORE KEY -" #counterclockwise
xsetwacom set 'Wacom Intuos4 6x9 pad' Button1 "core key 1" #button of touchdial

#button 9 is top button
xsetwacom set 'Wacom Intuos4 6x9 pad' Button9 "core key  CTRL z"
xsetwacom set 'Wacom Intuos4 6x9 pad' Button8 "core key  CTRL y"
xsetwacom set 'Wacom Intuos4 6x9 pad' Button7 "core key 7"
xsetwacom set 'Wacom Intuos4 6x9 pad' Button6 "core key 6"
xsetwacom set 'Wacom Intuos4 6x9 pad' Button5 "core key 5"
xsetwacom set 'Wacom Intuos4 6x9 pad' Button4 "core key  SHIFT"
xsetwacom set 'Wacom Intuos4 6x9 pad' Button3 "core key  ALT"
xsetwacom set 'Wacom Intuos4 6x9 pad' Button2 "core key  CTRL"
#button 2 is bottom button

```

---

### Post by myquidproquo on 2009-11-04
Hi!

I've been trying to install the touchscreen in my hp dv3-2250ep laptop running karmic but I can't get it to calibrate. 

I'm using the beta driver 0.8.5-1 because it's the one that supports the 00e2 model and have followed the instructions in post #104.

By now I can get the screen to detect when I press it but the cursor stays in a limited square area in the top corner. Running wacomcpl I can't see no devices.

My 10-linuxwacom.fdi looks like this:

> <?xml version="1.0" encoding="ISO-8859-1"?>
<!-- this is probably a bit imprecise -->
<deviceinfo version="0.2">
  <device>
    <match key="input.originating_device" contains="if1">
	<match key="info.product" contains="Wacom">
		<merge key="input.x11_driver" type="string">wacom</merge>
		<merge key="input.x11_options.Type" type="string">touch</merge>
		<merge key="info.product" type="string">touch</merge>
		<merge key="input.x11_options.BottomY" type="string">16909</merge>
		<merge key="input.x11_options.BottomX" type="string">26947</merge>
		<merge key="input.x11_options.TopY" type="string">0</merge>
		<merge key="input.x11_options.TopX" type="string">0</merge>
	</match>
    </match>
  </device>

</deviceinfo>


I've tried to change BottomX and BottomY but I don't really know if that is the problem...
The screen is 13.3in ( 1366x768 ).

Thanks in advance :)

---

### Post by Favux on 2009-11-04
Hi myquidproquo,

So it's a Wacom touchscreen?  Does it include the digitizer (a stylus)?  Then maybe the .fdi in gali98's [HOW TO]("http://ubuntuforums.org/showpost.php?p=7093065&postcount=104") might help.

Or is it a N-trig digitizer?  Maybe try in a terminal:
```
lsusb
```
and see if you can find out what it is.

---

### Post by myquidproquo on 2009-11-04
No, it doesn't come with a stylus...I really don't know if it can work with one. 
I always use my fingers and in win7 I can use it like a cursor and make it zoom in/out with 2 fingers. (don't know if that's relevant)

lsusb:
> Bus 005 Device 002: ID 0458:0036 KYE Systems Corp. (Mouse Systems) Pocket Mouse LE
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 064e:a102 Suyin Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 002: ID 056a:00e2 Wacom Co., Ltd 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


So I've asked linuxwacom foruns about support for 00e2 and they said 0.8.5 would be the driver to use. 

dmesg | grep wacom
> [   11.971537] usbcore: registered new interface driver wacom
[   11.971542] wacom: v1.49-pc-2:USB Wacom Graphire and Wacom Intuos tablet driver


ls -l /dev/input/by-path:
> total 0
lrwxrwxrwx 1 root root  9 2009-11-04 23:31 pci-0000:00:1d.0-usb-0:1:1.0-event-mouse -> ../event7
lrwxrwxrwx 1 root root  9 2009-11-04 23:31 pci-0000:00:1d.0-usb-0:1:1.0-mouse -> ../mouse1
lrwxrwxrwx 1 root root  9 2009-11-04 23:31 pci-0000:00:1d.3-usb-0:2:1.0-event -> ../event8
lrwxrwxrwx 1 root root 10 2009-11-04 23:31 pci-0000:00:1d.7-usb-0:5:1.0-event -> ../event10
lrwxrwxrwx 1 root root  9 2009-11-04 23:31 platform-i8042-serio-0-event-kbd -> ../event5
lrwxrwxrwx 1 root root 10 2009-11-04 23:31 platform-i8042-serio-1-event-mouse -> ../event11
lrwxrwxrwx 1 root root  9 2009-11-04 23:31 platform-i8042-serio-1-mouse -> ../mouse3
lrwxrwxrwx 1 root root  9 2009-11-04 23:31 platform-lis3lv02d-event-joystick -> ../event9
lrwxrwxrwx 1 root root  6 2009-11-04 23:31 platform-lis3lv02d-joystick -> ../js0


I really don't know about n-trig...
The fdi I've used is based on that HOWTO...Just removed the stylus and eraser parts as I thought they wouldn't apply in my case.

---

### Post by Favux on 2009-11-04
Hi myquidproquo,

Alright, it is a Wacom touch tablet pc.  Maybe like their new Bamboo Pen & Touch tablets.

We're off topic for this thread so start a new thread with the information that you've posted.  I'll find you.  What we want to do next is look at your lshal.  In a terminal do "lshal>lshal.txt".  My guess is that your touch is on 'if0' instead of 'if1' since there apparently isn't a digitizer.  Any reviews describing the hardware in more detail?

---

### Post by coCoKNIght on 2009-11-08
Does anybody know where to find the karmic equivalent of the jaunty .fdi file to make changes to the configuration?

---

### Post by Favux on 2009-11-08
Hi coCoKNIght,

The Jaunty .fdi works in Karmic.  The name changes to 10-linuxwacom.fdi.

---

### Post by ricardopresto on 2009-11-12
Hi

I have an old serial port penpartner that has never worked at all with ubuntu (I feel like I should whisper this bit - it works with windows). I've just come across this thread and have tried adding 'wacom' to etc/modules, but still no luck. Does anyone have any ideas?

---

### Post by virgulem on 2009-11-16
Thans to Favux, I've finally gotten this thing to work (Wacom Intuos3). It was being recognized, but for some reason hal (xorg.log said Serial... it is USB) was not getting the info it needed when I opened a browser, switched (one keyboard two comps) from one comp to the next. I am also no longer using the USB port on the switch for Wacom. Everything works fine now. Thanks!! :D

---

### Post by Favux on 2009-11-16
Hi virgulem,

Welcome to Ubuntu Forums!

You're welcome.

---

### Post by Favux on 2009-11-16
Hi virgulem,

Welcome to Ubuntu Forums!

You're welcome.


Hi ricardopresto,

The wacom in modules is for wacom.ko which is a usb kernel driver.  You need to install SetSerial and find out which ttyS* serial port your penpartner is on.

---

### Post by emaydubya on 2009-11-16
Hello.
I have been trying all I can find for a long time now and I still have trouble.
I have tried a good, 50 or more times/reboots etc going over (and over) this and other forums and pages over a year now. It all worked fine at some stage.

I have a Waltop Graphics pad supplied by Aldi now using Koala.
As everyone has said, it did work, now it doesnt after the upgrade from Jaunty.

wacomcpl is ok, it can change button assignments to some degree.

There used to be a little app called tablet-tools or something. It showed the pen working with pressure as circles but I cannot find it anywhere. That made it easy to check for pressure rather than opening gimp every time. wacdump does not work for me (show the pen data) however xidump does.

I have the pen working without pressure using the full pad's area
While trying to get pressure working I have put in a Waltop.Rules file, added parts to xorg as well. No difference.
when I run 
[PHP]xsetwacom -x getdefault stylus PressCurve[/PHP]
I get
[PHP]Option  "PressCurve"    "0,0,100,100"[/PHP]
After I run
[PHP] xsetwacom set stylus PressCurve 0 15 85 100[/PHP]
I still get
[PHP]Option  "PressCurve"    "0,0,100,100"[/PHP]
I edit .xinitrc but still no change. I always shows 0,0,100,100

So the question is:
Where is it that I can change this default setting for PressCurve to what I want? Running xsetwacom does nothing.

And how long might it be before this problem is resolved at an install level (kernel level?)
I'm seriously thinking of going back to the dark side after 10 years of this kind of stuff. I'm getting too old now for all this. I just want my stuff to work.
Thanks.

---

### Post by Favux on 2009-11-16
Hi emaydubya,

Welcome to Ubuntu Forums!

The news is not good I'm afraid.  Starting maybe sometime with the 0.8.2-x linuxwacom drivers a table of Vendor and Product ID's was added to the wcmUSB.c in the linuxwacom source code.  That locked out non-wacom usb tablets.  The dev.s must have patched something to get it working in Jaunty.  But for some reason they didn't in Karmic.

We've hacked a patch to wcmUSB.c that again has Waltop working for some in Karmic.  There's two threads on this.  Post #3 on this [thread]("http://ubuntuforums.org/showthread.php?t=1315438") links to the first thread with the "patched" wacmUSB.c and Waltop .fdi.  The "patch" for sure could be improved.  The version of linuxwacom you'll need to use is now 0.8.4-4.

---

### Post by emaydubya on 2009-11-17
Thanks Favux.
Yeah, I've already done all you mentioned above and then some.
I'm just trying to change the [COLOR=#000000][COLOR=#0000bb]
[/COLOR][/COLOR][php]Option  "PressCurve"    "0,0,100,100"[/php]
[COLOR=#000000][COLOR=#dd0000][COLOR=Black]to something else as I just want to try it.It must be written somewhere.
I even put that option into xorg.conf, didn't work.
I cannot find or know the name of the file that needs editing.
If I make the change in .xinitrc in my /home[/COLOR] [COLOR=Black]folder the change does not stick.
(after a reboot even)

Also, Waltop have a driver now, August it was released. 
But it looks like you have to rebuild the kernel for it and I don't wanna be the first to try that.

[/COLOR][/COLOR][/COLOR][http://www.waltop.com.tw/download.asp?lv=0&id=2](http://www.waltop.com.tw/download.asp?lv=0&id=2)

Maybe I should start a new discussion about Waltop and this driver. I don't know what to do with it.

---

### Post by Favux on 2009-11-17
Hi emaydubya,

Those who've looked at it are telling me the Waltop driver is for the Intrepid kernel (2.6.27).

Alright, have you looked at "Section 3: Calibrating your Tablet" in this [HOW TO]("http://ubuntuforums.org/showthread.php?t=1038949")?  The file is wacomcpl's .xinitrc in your home directory.

A new thread for Waltop sounds like a good idea.

---

### Post by emaydubya on 2009-11-17
Hi Favux
Oh, it's already out of date
I found this thread earlier:
**Still can't get waltop/medion graphics tablet to work, can't build drivers in karmic  **
[http://ubuntuforums.org/showthread.php?p=8333159#post8333159](http://ubuntuforums.org/showthread.php?p=8333159#post8333159)
 and made a start but if course it's futile.
 My .xinitrc already has my changes but they do not stick.
```
xsetwacom set stylus TPCButton "on"
xsetwacom set stylus Button3 "Button 3"
xsetwacom set stylus Button2 "Button 2"
xsetwacom set stylus Button1 "Button 1"
xsetwacom set stylus Suppress "2"
xsetwacom set stylus RawSample "4"
xsetwacom set stylus ClickForce "9"
xsetwacom set stylus PressCurve "0,5,95,100"
xsetwacom set stylus bottomy "6250"
xsetwacom set stylus bottomx "10000"
xsetwacom set stylus topy "0"
xsetwacom set stylus topx "0"
# run the primary system script
. /etc/X11/xinit/xinitrc
```
I still get [COLOR=#000000][COLOR=#0000BB]Option  [/COLOR][COLOR=#DD0000]"PressCurve"    "0,0,100,100"  after I run  [/COLOR][/COLOR][COLOR=#000000][COLOR=#0000BB]xsetwacom set stylus PressCurve 0 5 95 100  [/COLOR][/COLOR]
[COLOR=#000000][COLOR=#DD0000]
[/COLOR][/COLOR]It doesnt change. 
I think I'll just give up on this and HOPE it gets fixed sometime..

Thanks anyway

---

### Post by ricardopresto on 2009-11-20
Hi Favux, thanks for replying.

setserial -g /dev/ttyS* yields the following:

/dev/ttyS0, UART: 16550A, Port: 0x03f8, IRQ: 4
/dev/ttyS1, UART: 16550A, Port: 0x02f8, IRQ: 3
/dev/ttyS2, UART: unknown, Port: 0x03e8, IRQ: 4
/dev/ttyS3, UART: unknown, Port: 0x02e8, IRQ: 3

where do i go from here? sorry to be such a dunce but these are unfamiliar waters as far as i'm concerned.

thanks for your help

ricardo

---

### Post by Favux on 2009-11-20
My apologies, double post.

---

### Post by Favux on 2009-11-20
Hi ricardopresto,

Good!  So now you add to "/etc/serial.conf":
```
/dev/ttyS0 port 0x03f8 irq 4 autoconfig
```
I'm assuming it's on ttyS0 and that 0x03f8 is the right port.  Then:
```
sudo /etc/init.d/setserial reload
```
It may not be active right away.  You may need to reboot a few times.  We also used to restart X a few times in there, but it's now a pain in Karmic.

Then we need to figure out why you aren't getting automatic support.  We want to find out what your Vendor and Product ID is:
```
xinput --list
```
```
more /proc/bus/input/devices
(and/or)
grep -i name /proc/bus/input/devices
```
```
ls -la /dev/tablet-event
```
```
lshal>ricardopresto_lshal-1.txt
```
You can post the ouputs as an attachment.

I should also mention that 64-bit Karmic seems to have a problem with serial tablets but 32-bit seems fine.

---

### Post by njholland on 2009-11-22
> **Favux said:**
> Hi everyone,

As you have discovered it looks like the problems with wacomcpl and the xsetwacom commands come from the default Jaunty 10-wacom.fdi not parsing the names HAL is returning correctly for linuxwacom to understand.  Cyberfish came up with a .fdi that does parse the HAL names correctly and as modified by gali98 works for our usb tablet pc's.

I modified it for usb external graphics tablets.  K-buntu says it works on his Wacom Bamboo Fun.  Wacomcpl etc. work for him without having to rename anything.

You can configure everything through wacomcpl (& .xinitrc) and xsetwacom as before.  You can also configure through the .fdi like you use to do with xorg.conf.  If you do not have, for eg. the Wacom mouse, you could remove the append cursor line in the first section and the cursor section following it.

Remember this modified 10-wacom.fdi is for the 0.8.2-2 linuxwacom packages that come "default" with Jaunty:  xserver-xorg-input-wacom & wacom-tools

It looks like the modified .fdi also works with Karmic.

Just move and save the default 10-wacom.fdi in /usr/share/hal/fdi/policy/20thirdparty/ somewhere safe (after changing .fdi to .bak say) and substitute the attached .fdi.  After renaming it 10-wacom.fdi of course.  One way to do this is the following:

-First download the attached .fdi to your desktop.
-Then make a back up of the current "default" Jaunty 10-wacom.fdi by typing in a terminal:
```
sudo cp /usr/share/hal/fdi/policy/20thirdparty/10-wacom.fdi /home/yourusername/Desktop/10-wacom.bak
```In Karmic the .fdi has been renamed to 10-linuxwacom.fdi.  So to back up the "default" Karmic .fdi:
```
sudo cp /usr/share/hal/fdi/policy/20thirdparty/10-linuxwacom.fdi /home/yourusername/Desktop/10-linuxwacom.bak
```Where "yourusername" is the user name you are using.  Check that the "wacom.bak" is now on your Desktop and has the correct contents by right clicking on it and 'Open as a "text file"'.  You can move it to wherever you want in Nautilus (Places) later.  Close it.
-Now open the current 10-wacom.fdi as root in gedit with:
```
gksudo gedit /usr/share/hal/fdi/policy/20thirdparty/10-wacom.fdi
```In Karmic use:
```
gksudo gedit /usr/share/hal/fdi/policy/20thirdparty/10-linuxwacom.fdi
```Delete the entire contents (its safe, you've verified your backup).  Now copy and paste the entire contents of the downloaded modified wacom.fdi (you can right click on it and open it in another text editor) save and close.
-Reboot.

Now "xinput --list" and "xsetwacom list" entered in a terminal should agree with each other and return the linuxwacom names stylus, eraser, cursor (if you have the Wacom mouse), and pad.  With "xsetwacom list" working you are now able to use 'wacomcpl', the LWP's configuration and calibration gui.  Just enter 'wacomcpl' (without the quotes) in a terminal and the gui will pop up.  To set it up so that it's settings last through a reboot see "Section 3:  Calibrating your Tablet" here:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)

Intuos4 tablet users need a 'wacom.ko' (the usb kernel driver/module) newer than the default Jaunty 0.8.2-2 wacom.ko.  The default one doesn't allow usb communication to your tablet.  To compile the new 'wacom.ko' follow Section 1, and Section 1 only, of gali98's Jaunty HOW TO in post #104 here:  [http://ubuntuforums.org/showthread.php?t=1038949&page=11](http://ubuntuforums.org/showthread.php?t=1038949&page=11)

To further set up your pad see shatterblast's post #188 on the following page.  For the Intuous4 pad see also ceridwen's post #95 here:  [http://ubuntuforums.org/showthread.php?t=1120029&page=10](http://ubuntuforums.org/showthread.php?t=1120029&page=10)  That's the Intuos4 thread, lots of tips in it.

If the usb .fdi works for you maybe something analogous can be done with the serial tablet's subsection of the 10-wacom.fdi?
Edit:  I made an attempt at a  serial .fdi attached below.  It hasn't been tested so no guarantees.  Same instructions as above.  I did remove the three identifiers I know are for serial tablet pc's:  WACf008;WACf009;FUJ02e5.


Hey peoples,

this is my first post as an ubuntu user. Always been windows before, so I have SOOO much learning to do. Doh! Still, I've made the change and am loving it.

First off, it is always an amazing, inspiriation to see how people in this community help each other out. If only people around the world could take note of that and apply it day to day. Oh well!!

But thanks so much for taking the time to post this lot, it sorted out my wacom straight off :)

I did find a reboot was key though, not just a log out and in. Hope this helps,

thanks again,

Nick.

---

### Post by ricardopresto on 2009-11-24
[quote=Favux;8355120]Hi ricardopresto,

Good!  So now you add to "/etc/serial.conf":
```
 /dev/ttyS0 port 0x03f8 irq 4 autoconfig 
``` I'm assuming it's on ttyS0 and that 0x03f8 is the right port.


Hi Favux.

No file in /etc called 'serial.conf'. There is a file with that name in /usr/share/doc/setserial - is that the one?

ricardo

---

### Post by Favux on 2009-11-24
Hi ricardopresto,

OK, just create it:
```
gksudo gedit /etc/serial.conf
```
add the line to it Save, Close, and reboot.

Oh, and what does the tablet have.  A stylus obviously.  Does the stylus have buttons?  How many?  Does it have an eraser?  Did the tablet come with a Wacom mouse?  Are there buttons on the tablet?

---

### Post by popiutyress on 2009-11-24
Hello everybody,
I am having trouble getting my intuos 3 to work with Ubuntu studio karmic. I have followed the tutorial by **Favux **(quoted here by** njholland** in post **#391**). This has got xsetwacom to list all the devices. 

Everything works exept ***Stylus Pressure sensitivity in Gimp*** . 

The eraser has pressure sensitivity and works perfectly.

When I run xinput -list The stylus show's up how it should do. 

I have looked every where for a solution and for the moment I have found none.

  I am running Gimp 2.6 in ubuntu studio. Is this a GIMP Issue?? I can't tell.
Thank you for your help.

Popiutyress

---

### Post by Allochtoon on 2009-11-25
> **popiutyress said:**
> Hello everybody,
I am having trouble getting my intuos 3 to work with Ubuntu studio karmic. I have followed the tutorial by **Favux **(quoted here by** njholland** in post **#391**). This has got xsetwacom to list all the devices. 

Everything works exept ***Stylus Pressure sensitivity in Gimp*** . 

The eraser has pressure sensitivity and works perfectly.

When I run xinput -list The stylus show's up how it should do. 

I have looked every where for a solution and for the moment I have found none.

  I am running Gimp 2.6 in ubuntu studio. Is this a GIMP Issue?? I can't tell.
Thank you for your help.

Popiutyress

I assume you set the input devices in The Gimp all to screen?
Just to make sure, the calligraphic tool in the gimp does not work pressure wise?

Inkscape has the same issue?

---

### Post by popiutyress on 2009-11-25
> I assume you set the input devices in The Gimp all to screen?
Just to make sure, the calligraphic tool in the gimp does not work pressure wise?

Inkscape has the same issue?

Hi, yes all the input devices are set to screen. No the calligraphic tool doesn't work in Gimp or in Incscape. I have just tried Inscape and the eraser works perfectly so I conclude that it is neither Gimp or Incscape that are at the root of the problem. It must be something to do with my tablet set up. If anyone hase any ideas how to fix this I would be very grateful !

---

### Post by ricardopresto on 2009-11-26
> **Favux said:**
> Hi ricardopresto,

OK, just create it:
```
gksudo gedit /etc/serial.conf
```add the line to it Save, Close, and reboot.

Oh, and what does the tablet have.  A stylus obviously.  Does the stylus have buttons?  How many?  Does it have an eraser?  Did the tablet come with a Wacom mouse?  Are there buttons on the tablet?

Still no luck :(

Tried it with ttyS0 and ttyS1. Rebooted several times.

The stylus has an eraser and one button. No buttons on the tablet, and no mouse.

ricardo

---

### Post by RoestVrijStaal on 2009-11-26
Hello everyone,

I'm a little bit confused with all this information. 
I had a Jaunty installation, configurated to work with my Bamboo One, thanks to the tutorial in the ubuntu forums.
However, after upgrading to Karmic, wacomcpl does not list my pen tablet anymore. 
I want to make the second stylus button as the 3rd-click-mousebutton.
I think I've got still the configuration of Jaunty. How I could fix it?

---

### Post by Favux on 2009-11-26
Hi ricardopresto,

Hmmm.  It seems like you should see some activity.


Hi RoestVrijStaal,

To get wacomcpl to work just follow the instructions in [post #176]("http://ubuntuforums.org/showpost.php?p=7234134&postcount=176").

---

### Post by RoestVrijStaal on 2009-11-27
> **Favux said:**
> 
Hi RoestVrijStaal,

To get wacomcpl to work just follow the instructions in [post #176]("http://ubuntuforums.org/showpost.php?p=7234134&postcount=176").

Hi Favux,
I followed the instructions and it worked for me. My tablet is running good now. Thank you very much :D

I have a small tuto for people who wants the same aspect ratio on their tablet as the aspect ratio of their screen: 
- Divide the width of the screen with the height of the screen, let's name the result of this 'index'.
- Go to wacomcpl, choose stylus and click on the tracking button.
- Multiply the XBottom with 'index', the result of this is the new value of BottomY.
- Click on OK and close wacomcpl to apply the new settings.

---

### Post by dcsundr on 2009-11-29
Hi everyone,

I found a post detailing an error with the Intuos4 here: 
http://ubuntuforums.org/showthread.php?t=1340911

Out of curiosity I checked my own Xorg.0.log (found in /var/log) and to my surprise I found that the line  

eraser - usbParse: dropping empty event for serial -1769990915  

was repeated over and over again in the log.

I could duplicate this behaviour by either placing the stylus or the mouse over the tablet. 

Can anyone please check their own Xorg.0.log file to see if you can also duplicate this? Further, if anyone can guess as to what's causing this can you please leave a post?    

PS: I found a scribble somewhere saying that this could be caused by bad communication between the wacom kernel module and the kernel but this was more a conjecture.    


System info: 

Ubuntu 9.10 (Karmic)  
Kernel: linux-image-2.6.31-15-generic  
Intuos4 4x6 w/ Mouse

---

### Post by Barbidoux on 2009-12-16
Hello

I'm new on this forum but I use ubuntu since version 5.04 (and english is not my first language, so please, be indulgent with me. I'll try to do my best).

I use a Wacom UD1212 (yeah, a good old serial model).

It take to me 2 or 3 Ubuntu version to understand how to add it in xorg.conf (and I was ashamed when I saw how simple it was when you know). So it worked fine until Jaunty (meaning it didn't work anymore after Jaunty's installation).

I tried to modify Jaunty's xorg.conf, but the best I had was a pen with 2 seconds delay in the same time that I losed the nvidia graphic card. So an unusable tablett with an unusable sreen was too much for me.

3 days ago, I just upgrade to Karmic with the secret hope that the plug&play would do it. Well, nice try, but **** ! That doesn't work.

I red almost all this thread and tried different things, but it is difficult to select what is for Jaunty or Karmic (alpha, beta or final release), USB or serial. I understand that Karmic doesn't use xorg.conf anymore. I tried this way and it just slow down Gnome without any move from stylus or pointer.

Everything containing "Wacom" is installed and the wacom driver seems to be "ubuntu 1.0.8.4.1" (I understand that it is the 8.4.1 version, so seems good to me).

xinput -list know nothing about "wacom" unless it is called "Virtual core pointer"
lsmod show that the wacom driver is loaded
xsetwacom list give nothing

I don't know where to begin.

Any idea is welcome before I have to buy a iMac and a new tablet to my wife (who is the wacom tablet user)

Thank you in advance

---

### Post by Favux on 2009-12-16
Hi Barbidoux,

Welcome to Ubuntu Forums!

You are using Karmic.  32-bit or 64-bit?  Be sure to use Update Manager and make sure your system is current.

What year did the Wacom UD1212 come out in?  If it is old enough we may need to add it to the wacom.fdi match line to get it to work.  To do that we will need to look at your lshal and see if your tablet returns a serial pnp identifier.  In a terminal:
```
lshal>Barbidoux_lshal.txt
```
Right click on it and compress it using Create Archive then attach it to your next post using Manage Attachments.

In the meantime you could try the serial .fdi in [post #176]("http://ubuntuforums.org/showpost.php?p=7234134&postcount=176").

Hope this is helpful.

---

### Post by Barbidoux on 2009-12-16
Hello

Thank you for this so fast answer.

Uname -a give :
[FONT=monospace]
Linux Poupette 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:01:29 UTC 2009 i686 GNU/Linux
[/FONT]
[FONT=monospace]So, I think this is a 32 bits version.

I hope you will find the joined file with lshal result.

I joined the content of /usr/share/hal/fdi/policy/20thirdparty/ [/FONT][FONT=monospace]where you will find the .fdi file I tried yesterday. It seems that it is the one of post 176.

Thank you for your help
[/FONT]

---

### Post by Favux on 2009-12-16
Hi Barbidoux,

I don't think it's included in the current match lines.  I think I see it, but I'll have to comb through a lot of serial sections to be sure.  You have it plugged in, correct?  Let's try:
```
grep -i name /proc/bus/input/devices
```
and see if we get lucky.  And maybe check:
```
xinput --list
```
again.

The other problem is that linuxwacom since 0.8.2-? has been adding Vendor and Product ID tables that have the effect of screening out non-wacom tablets.  So yours might be affected by that.

---

### Post by Barbidoux on 2009-12-16
Hello

grep -i name /proc/bus/input/devices
N: Name="Power Button"
N: Name="Power Button"
N: Name="Macintosh mouse button emulation"
N: Name="AT Translated Set 2 keyboard"
N: Name="HDA Digital PCBeep"
N: Name="ImExPS/2 Logitech Explorer Mouse"

xinput --list
"Virtual core pointer"	id=0	[XPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
"Virtual core keyboard"	id=1	[XKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Power Button"	id=2	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"AT Translated Set 2 keyboard"	id=3	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Power Button"	id=4	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"ImExPS/2 Logitech Explorer Mouse"	id=5	[XExtensionPointer]
	Type is MOUSE
	Num_buttons is 13
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
"Macintosh mouse button emulation"	id=6	[XExtensionPointer]
	Type is MOUSE
	Num_buttons is 5
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1


"that have the effect of screening out non-wacom tablets.  "
Well, it is a Wacom tablet with the official logo.
I'm not sure to understand what you mean.

---

### Post by Favux on 2009-12-16
Hmmm.  No luck there.

After getting lost in your lshal I'm no longer as confident that I see it.  But let's make a try anyway.  I updated the serial tablet .fdi in post #176.  Use that and add to this line:
```
      <match key="@info.parent:pnp.id" contains_outof="WACf;FUJ02e5;FUJ02e7">
```
PNP0501 like so:
```
      <match key="@info.parent:pnp.id" contains_outof="PNP0501;WACf;FUJ02e5;FUJ02e7">
```

The tablet has a stylus.  Does the stylus have an eraser?  Any buttons on the stylus?  Any other features/devices?

That's why I asked how old it was.  Some of the very old Wacom tablets linuxwacom doesn't support anymore.

---

### Post by Barbidoux on 2009-12-16
I modified the "match key" line as you suggested.

Everything is the same (xinput, lsmod, xsetwacom list), but it seems to me that the reboot was a little bit longer before the login screen (not sure if that help, but it is a free information).

I have a stylus with one button and no eraser.
I have a 4 buttons "mouse" (don't know english word for Wacom mouse with the magnifier (? not sure about that word too)).

And it's late for me now, I worked yesterday after midnight on this, I won't do a bis.

Thank you and good night (in case). I will continue tomorrow.

---

### Post by Favux on 2009-12-16
Hi Barbidoux,

Good night.

We need to take a look at lshal again and see what changed.

So the serial Wacom UD1212 came with a Wacom mouse (also called puck)?  Interesting.  So maybe I was correct to include cursor in the first serial .fdi?

It's possible you may have to try to configure through xorg.conf and setserial.

Edit:  Awesome!  It came out for the Mac(?) in 1994.  The Wacom ArtZII (UD1212-R).  Some of them were huge and I think it's the model they first introduced the eraser on.  They stopped selling it like 12 years ago.  Cool!  About 18 mo.s ago Ping (LWP) said linuxwacom supports it.  And some folks set it up in Feisty 7.04 in 5/07 using a Keyspan 8pin serial -> usb adapter:  [http://ubuntuforums.org/showthread.php?t=458747](http://ubuntuforums.org/showthread.php?t=458747)  So one way or the other we have a shot at getting it to work.

---

### Post by Allochtoon on 2009-12-16
> **dcsundr said:**
> Hi everyone,

I found a post detailing an error with the Intuos4 here: 
[http://ubuntuforums.org/showthread.php?t=1340911](http://ubuntuforums.org/showthread.php?t=1340911)

Out of curiosity I checked my own Xorg.0.log (found in /var/log) and to my surprise I found that the line  

eraser - usbParse: dropping empty event for serial -1769990915  

was repeated over and over again in the log.

I could duplicate this behaviour by either placing the stylus or the mouse over the tablet. 

Can anyone please check their own Xorg.0.log file to see if you can also duplicate this? Further, if anyone can guess as to what's causing this can you please leave a post?    

PS: I found a scribble somewhere saying that this could be caused by bad communication between the wacom kernel module and the kernel but this was more a conjecture.    


System info: 

Ubuntu 9.10 (Karmic)  
Kernel: linux-image-2.6.31-15-generic  
Intuos4 4x6 w/ Mouse

i got the same thing. also, sometimes registration of movements gets FUBAR and i have to rerun my 'xsetwacom' script to get it working again.

---

### Post by KratosAurion on 2009-12-16
Hello everyone,

This is my first post on the forum, though I have been reading this thread for a while now. So far, I have everything working on my Wacom Intuos 4 4x6 as per the instructions and tips everyone has pointed out so far, except that I can't seem to set the Click Force from the FDI. I have tried the variables ClickForce and Click_Force, and have tried looking around for an FDI that implements regulation of the Click Force, but have been unsuccessful so far. Any help would be very much appreciated.

Thanks,
Kratos

---

### Post by Favux on 2009-12-16
Hi Kratos,

Welcome to Ubuntu Forums!

Why not set the clickforce through wacomcpl?

---

### Post by KratosAurion on 2009-12-16
Hi Favux,

There is some sort of problem with my wacomcpl, so that it does not save my settings after each logon. The changes that I make to the FDI are always there, but the wacomcpl settings are always restored to whatever the FDI had set. I am not really sure why this happens...

---

### Post by Favux on 2009-12-17
Hi Kratos,

That should be easy to fix.  Have you set it up for a reboot as described in "Section 3: Calibrating your Tablet" in this [HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1")?

---

### Post by Barbidoux on 2009-12-17
@Favux
> About 18 mo.s ago Ping (LWP) said linuxwacom supports it.
It worked fine until Intrepid. I just had to remove some lines (concerning tablet PC) in xorg.conf and replace /dev/.../wacom with /dev/ttyS0.

When I tried to do the same in Jaunty about 6 month ago, it broke the graphic card configuration (at first I tried my old xorg.conf and then tried different mixes). I remember that at a time (perhaps will I find the xorg.conf of this try), I had the tablet working a bit. But the pointer followed the stylus on the screen with 1 or 2s delay (like a dog follow his master in the street). At this time, the graphic was so bad (nvidia driver KO) that it could perhaps explain this behavior but I'm not sure.

For the story, I think I bought it as a gift for my wife in 1996. I think I used Windows 95 and Corel Draw at this time. Since I didn't change my wife, I wonder why I would change a gift ! :lolflag:
One day, I had to repair it after connecting the wrong power supply (change a little electronic bug inside). 

Could it help if I connect it to a PC with Intrepid to see how it is configured ? I can eventually install a PC with this version.

I have a little Pen Partner (serial with pen and eraser if I remember), could it help if I try to connect it (it is younger than the big UD1212) ?

---

### Post by Favux on 2009-12-17
Hi Barbidoux,

Great stories!  :)

The wacom thing in xorg.conf means the wacom.rules didn't contain a symlink rule for it.  As I recall I looked for a rule for the PenPartner too and it wasn't there.  If we can figure out the identifier we could probably make one.

Let's look at the lshal again since you have the .fdi installed.  Let's see if it tells us anything.  I'm kind of scared we're actually trying to configure the serial port on the mother board.  But it was the only thing that looked close.

Anyway we should be able to get it through the xorg.conf.  It may be it is at a different baud rate then the default one, and that was your problem.  Along with the fact the Jaunty and Karmic xorg.conf's are touchy.  But I'm semi-good with them.

Oh, and we should probably start a separate thread.

---

### Post by Barbidoux on 2009-12-17
I'm at office at this time, so I can't test anything with the tablet.

How could we transfer this in a new thread ?

---

### Post by Favux on 2009-12-17
Just navigate to the Hardware & Laptops forum and click on the New Thread button on the top left.  You become the original poster on the thread.  Include any information you consider relevant that you've already posted in that first post.  Including of course your current lshal and Karmic xorg.conf.

Put some thought into the title so that it is descriptive.  We might get lucky and and someone who already knows the answer could help us out.

---

### Post by Barbidoux on 2009-12-17
Hello Favux.

I made a new thread called
[**"Old Wacom serial tablet is not recognized in karmic**"]("http://ubuntuforums.org/showthread.php?p=8516494#post8516494")

Hope the link is good

I go now to bed and I'm not sure I will ba able to follow experiments tomorrow.

Thank you again.

---

### Post by jomsa on 2009-12-17
Hi,

I am new around here so, be warned.

I've been using Ubuntu for few years (since 7.10 IIRC), Now i do 3D and 2D graphics. So i have many tools associated to this (3DConnexion navigator and Wacom tablet).  I used 7.10 for sometime, and then updated to 8.04 and thats when i got the Tablet. I managed to set it to work properly back then, and then i got second monitor for my setup and managed to get the tablet to work properly on that too (tablet drawing area mapped only to one monitor).
However due to some unrelated problems with other stuff, forced me to update to 9.10, the tablet went berserk. After while i managed to fix it to state where everything seems to work okay, but i cant map it back to only work in one monitor (using Twinview btw). I've googled around a lot about this, and it suggested me to use some dfi file, but that lead to nowhere.
I also read somewhere that before update from pre 9.04 one should have removed all Wacom related fdi and Xorg.conf settings, which i did not do (didnt know at the time anything about such), What is this about really?

Thank you!

ps. Having this marvelous decide lying on my desk unusuable is killing me...

ps2. Oh and the specs
Ubuntu 9.10 @ 64bit
Wacom Intuos 3 A5

---

### Post by Favux on 2009-12-17
Hi jomsa,

Welcome to Ubuntu Forums!

Which Wacom tablet do you have?  What does your xorg.conf look like?

---

### Post by jomsa on 2009-12-17
I am using the A5 one (6x9), xorg.conf is now quite empty really. But here it goes ->

```
Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "Acer V223W"
    HorizSync       31.0 - 84.0
    VertRefresh     56.0 - 77.0
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    Option         "AddARGBGLXVisuals" "True"
    DefaultDepth    24
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "DFP-0: nvidia-auto-select +0+0, DFP-1: 1680x1050_60 +1680+0"
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-1: 1680x1050_60 +0+0"
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection

Section "Device"
    Identifier     "Videocard0"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600 GT"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600 GT"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection
```

Also i am very unskilled in Linux matters. Its just tool for me really, dont have time to learn its insides afaik :S

---

### Post by Favux on 2009-12-17
Hi jomsa,

OK, you have the "Wacom Intuos3 A5 Tablet Pen and Mouse USB Mac/Win".  Is that correct?

Actually your xorg.conf is very full for Karmic.  That's because you have Nvidia and have set up TwinView.  Some folks don't even have a xorg.conf in Karmic!

Given that it is a usb tablet first you want to change the default wacom.fdi to a new one.  Either the first or third one in [post #176]("http://ubuntuforums.org/showpost.php?p=7234134&postcount=176").  Don't worry that you are new, just read it through a few times.  It has explanations and instructions.  And you can change things back if you need to.

---

### Post by jomsa on 2009-12-17
> **Favux said:**
> Hi jomsa,

OK, you have the "Wacom Intuos3 A5 Tablet Pen and Mouse USB Mac/Win".  Is that correct?

Yes, but you know what. After i copied the new dfi file, it just magicly started working! :D  It works now exactly as i want it to :D   I dont get it whats going on, but maybe my previous fdi was toast or something? Thanks anyway, this got resolved way faster than i expected! THANKS THANKS!!  Finally i can get back to work.

---

### Post by Favux on 2009-12-17
Hi jomsa,

You are welcome.  :)

---

### Post by llex_paul on 2009-12-21
hey all! i'm back with a little problem...i changed to ubuntu 9.10 and my tablet isn't working...i have problems with pressure...in the rest i think i can handle because i've done that before but pressure installed a friend of my and i don't know how. so can you please help me again:D my talbet is an intuos 3 and i'm using ubuntu 9.10

---

### Post by Favux on 2009-12-21
Hi again llex_paul,

It sounds like you installed the modified wacom.fdi, like before, at [post #176]("http://ubuntuforums.org/showpost.php?p=7234134&postcount=176").  Remember the name changes to 10-linuxwacom.fdi in Karmic.

To get pressure working in Gimp you have to configure the extended input devices.  See near the bottom of the [Wacom wiki]("https://help.ubuntu.com/community/Wacom").

And to remind you of what you did before you could start with your first post, [post #270]("http://ubuntuforums.org/showthread.php?p=7822038#post7822038").

Good luck!

---

### Post by Dave M G on 2009-12-23
Hello,

Since upgrading to 9.10, one setting has changed, and I would like to get it back.

I often switch between relative and absolute mode, with the following commands:

```
xsetwacom set stylus mode relative; xsetwacom set stylus twinview none
xsetwacom set stylus mode absolute; xsetwacom set stylus twinview horizontal ScreenNo 0
```

I have dual monitors. When in absolute mode, however, I don't want the width of the tablet to represent the width of both monitors. That relative screen space of both monitors is much wider than the space on the tablet, making for skewed lines when I draw in Inkscape or Gimp or Photoshop.

Before, I had it so that when I was in absolute mode, the space on the tablet corresponded to a space on the screen that was relatively equal in height and width. The usable space started from the left hand side of my two monitors.

This meant that while I was in absolute mode, there was a good chunk of space on the right that I could not access. But that was fine, because I had an accurate absolute mode for drawing with on the left.

I don't know what setting got changed, and I even tried to restore my previous fdi file from back ups.

How can I get absolute mode to not stretch to fill the width of both monitors, but instead be a relative size match for the size of the tablet?

I hope my question is clear.

Thank you for any advice.

---

### Post by PSIRockin on 2009-12-24
Hi, I followed the instructions for Karmic and replaced the original 10-linuxwacom.fdi with the provided one. I have a USB Wacom Bamboo. After it didn't work, I tried "xsetwacom list" and nothing comes up. There's also nothing from "xinput --list". Have I skipped a step?

---

### Post by Favux on 2009-12-24
Hi PSIRockin,

What is the Bamboo's model number?

---

### Post by PSIRockin on 2009-12-24
CTH-460.

Thanks for getting back so fast.

---

### Post by Favux on 2009-12-24
Hi PSIRockin,

Sure, 'tis the Season after all.

Ok the Bamboo Pen & Touch.  That's so new that the default linuxwacom 0.8.4-1 in Karmic doesn't support it.  Support is just being added and is in 0.8.5-8 but it still isn't quite working.  Most likely the next version will support your tablet.

To get it working go direct to the horses mouth and follow Ayuthia's instructions and use his patches in [post #1]("http://ubuntuforums.org/showpost.php?p=8283168&postcount=1") on the "Wacom Bamboo Pen and Touch Series Development".

Good luck!

Seasons greetings.

---

### Post by confubar on 2009-12-26
I got a new wacom intuos4.....  it does not work on my 9.04 and it turns out that this line is not supported  :shock: ](*,) :oops: :cry:
Someone should perhaps update this reference...

---

### Post by Favux on 2009-12-26
Hi confubar,

It is updated.  Go to [post #176]("http://ubuntuforums.org/showpost.php?p=7234134&postcount=176") and follow the instructions for a new wacom.fdi.  Then follow the link to gali98's HOW TO.  There you'll find the instructions to compile a new wacom.ko (the usb kernel driver/module) which is what you need to talk to your tablet.  There is also a link to ceridwen's post for setting up your pad.  That will get almost everything working.

Good luck!

---

### Post by confubar on 2009-12-28
> **Favux said:**
> Hi confubar,

It is updated.  Go to [post #176]("http://ubuntuforums.org/showpost.php?p=7234134&postcount=176") and follow the instructions for a new wacom.fdi.  Then follow the link to gali98's HOW TO.  There you'll find the instructions to compile a new wacom.ko (the usb kernel driver/module) which is what you need to talk to your tablet.  There is also a link to ceridwen's post for setting up your pad.  That will get almost everything working.

Good luck!
I saved a backup of 10-wacom.fdi, deleted the contents and saved it with the contents of Favux_Jaunty ext graphics_test 2_10-wacom.fdi.txt
Previously I had worked with the instructions in Gali98's  Install a LinuxWacom Kernel Driver for Tablet PC's 

I got this far:

  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/user/linuxwacom-0.8.4-4/src/2.6.28/wacom.mod.o
  LD [M]  /home/user/linuxwacom-0.8.4-4/src/2.6.28/wacom.ko
make[3]: Leaving directory `/usr/src/linux-headers-2.6.28-17-generic'
make[2]: Leaving directory `/home/user/linuxwacom-0.8.4-4/src/2.6.28'
make[1]: Leaving directory `/home/user/linuxwacom-0.8.4-4/src'
make[1]: Entering directory `/home/user/linuxwacom-0.8.4-4'
make[1]: Nothing to be done for `all-am'.
make[1]: Leaving directory `/home/user/linuxwacom-0.8.4-4'
user@dell-desktop:~/linuxwacom-0.8.4-4$ sudo cp ./src/2.6.28/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
[sudo] password for user: 
confubar@dell-desktop:~/linuxwacom-0.8.4-4$ sudo cp ./src/2.6.28/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
confubar@dell-desktop:~/linuxwacom-0.8.4-4$ 

Is there anything else I can try or do?

---

### Post by Favux on 2009-12-28
Hi confubar,

It looks like you successfully compiled the 0.8.4-4 wacom.ko and copied into place.  You also have the correct .fdi installed.

On some systems the wacom.ko doesn't auto-load.  Let's see if it is loaded:
```
lsmod | grep wacom
```

---

### Post by confubar on 2009-12-29
.... I tried it and got nothing...

---

### Post by Favux on 2009-12-29
Hi confubar,

Alright, that may be your problem.  Let's first try rebuilding all the module dependencies with:
```
sudo depmod -a
```
in a terminal.  Reboot and see if 'wacom' shows up in lsmod and your tablet now works.

If not we'll add 'wacom' (without the quotes) in the modules file in /etc/:
```
gksudo gedit /etc/modules
```
Save, Close, and reboot.

---

### Post by confubar on 2009-12-30
!!!Yippee yippee it works.
Thank you so very much!!!!!!!!!
:P=D>:-\"

---

### Post by Favux on 2009-12-30
Hi confubar,

Great!  You're welcome.  :)

---

### Post by GoodHumorJO on 2009-12-30
Hey,
I am running my Intuos3 on Karmic with the wacom drivers from the repository as well as the new .fdi. The problem is I cannot configure my tablet mouse or keypads. When I run xinput --list I get back that I have, "eraser", "stylus cursor", "stylus pad", and "stylus"; however, when I run xsetwacom list, I am fed back:
stylus       stylus
eraser      eraser

And in wacomcpl I can only configure my stylus and eraser.

Thanks for any help anyone can offer. If more information is needed that I haven't given let me know and I will have it up ASAP.

---

### Post by Favux on 2009-12-31
Hi GoodHumorJO,

Welcome to Ubuntu forums!

It sounds like you may not have good communication with your tablet.  Check your usb connection and make sure it's firmly seated on both ends.  Then try rebooting a few times.  Does the Wacom mouse and pad work on another system or Windows if you are dual booting?

Hope this helps.

---

### Post by GoodHumorJO on 2009-12-31
The odd thing, is the tablet mouse works, moves the cursor around, right and left click work right, and the 2 extra side buttons as well as the scroll wheel work, but they are not configurable via wacomcpl, and do not show up through either list commands. The biggest issue with it not being configurable is the mouse cursor move speed is mud slow, but if I use a true mouse or even just the pen things are fine. 

Some of this holds true for the keypads on the tablet as well, the buttons do things, however it is all unconfigurable and unlinisted. On Windows the tablet works fine, fully functional and fully configurable, and I seem close on Karmic, I can smell it!

---

### Post by Favux on 2009-12-31
Hi GoodHumorJO,

Hmmm.  Something weird going on.  So you have stylus, eraser, cursor, and pad.

Exactly which .fdi are you using?

Do you have another wacom.fdi anywhere?  Remember the .fdi in Karmic is 10-linuxwacom.fdi.  Do you have Wacom sections in your xorg.conf?

I need to see your lshal.  In a terminal enter:
```
lshal>GoodHumorJO_lshal.txt
```
Right click on it and compress it with Create Archive.  Then attach it with Manage Attachments on your next post.  Please do the same with your current wacom.fdi (except you don't need to compress it).

---

### Post by JAKEOTR on 2010-01-03
Hello....not to hijack the thread, but it seems this is the most likely place for a wacom question/problem. I have a serial ud-0608-r Digitizer II and could not get it to plug and play with 9.10. I finally got it to work using the guides for 8.10 (xorg config). But the last niggling problem is my cursor is very slow. It lags behind terribly. The stylus and the eraser work just fine, but the mouse function does not. I am able to use wacomcpl, and have tried different settings...I have tried speed settings in xorg and no luck there. Any have any ideas? Thanks

---

### Post by Enmi on 2010-01-09
> **GoodHumorJO said:**
> Hey,
I am running my Intuos3 on Karmic with the wacom drivers from the repository as well as the new .fdi. The problem is I cannot configure my tablet mouse or keypads. When I run xinput --list I get back that I have, "eraser", "stylus cursor", "stylus pad", and "stylus"; however, when I run xsetwacom list, I am fed back:
stylus       stylus
eraser      eraser

And in wacomcpl I can only configure my stylus and eraser.

Thanks for any help anyone can offer. If more information is needed that I haven't given let me know and I will have it up ASAP.

I have the exact same problem in my computer! And I have a basic Wacom Bamboo (the one with the 4 buttons and the pad on the top, not the Fun, just the Bamboo)

When I use the new .fdi file, the only options that show up when I run xsetwacom list are just that:
stylus       stylus
eraser      eraser

I included the lshal outputs and the fdi file I'm currently using, as Favux requested, I hope that can shed some light into this, as that's the ONLY thing that's gone wrong with my setup.

---

### Post by Favux on 2010-01-09
Hi Enmi,

Stylus and eraser set up OK in lshal.  The cursor and pad sections set up but indicate they aren't valid sub-devices.

What model Bamboo do you have?

Do you have a Wacom mouse for the Bamboo?  That's what the cursor is.

---

### Post by SergeantOreo on 2010-01-16
Hello Favux, (or anyone else)

I recently followed configured my Wacom Intuos3 tablet using your Wacom .fdi guide and the [Linux Wacom Project]("http://linuxwacom.sourceforge.net/index.php/howto/main") documentation, but have been experiencing many errors.

They seem to have started when I used wacomcpl and set up .xinitrc. The first problem is that wacomcpl lists duplicate entries (see screenshot.) The second is that the tablet has no pressure sensitivity; everything works perfectly, except for when I start drawing.

My .xinitrc can be seen [here]("http://www.pasteall.org/10356").

Thanks.

---

### Post by Favux on 2010-01-16
Hi SergeantOreo,

Make sure you don't have another wacom.fdi somewhere, or that sections aren't duplicated in your .fdi.  Also make sure there aren't any Wacom entries in your xorg.conf.

---

### Post by SergeantOreo on 2010-01-16
> **Favux said:**
> Hi SergeantOreo,

Make sure you don't have another wacom.fdi somewhere, or that sections aren't duplicated in your .fdi.  Also make sure there aren't any Wacom entries in your xorg.conf.

Favux,

I searched my system for another *10-linuxwacom.fdi* and did not find anything, and then checked the .fdi file for duplicate entries to no avail.

Also, could you clarify what you mean when you say to check for Wacom entries in my xorg.conf? I have a lot of entries that I added according to the [documentation]("http://linuxwacom.sourceforge.net/index.php/howto/x11") from the Linux Wacom Project..

Finally, my xorg.conf can be seen [here]("http://www.pasteall.org/10369").

---

### Post by Favux on 2010-01-17
Hi SergeantOreo,

The wacom entries in your xorg.conf are the problem.  You want to just use the .fdi in Karmic.  The xorg.conf is also executing and that is what is messing up the configuration of your Intuos3.  So remove or comment (#) them (the Wacom sections) out in your xorg.conf including the corresponding "ServerLayout" lines.  For example the stylus section:
```
#Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "stylus"
#  Option        "Device"        "/dev/input/wacom"    # USB ONLY
#  Option        "Type"          "stylus"
#  Option        "USB"           "on"                  # USB ONLY
#EndSection
```
and it's "ServerLayout" line:
```
#    InputDevice    "stylus"    "SendCoreEvents"
```
And you do not have at least touch.  Once you've cleaned that up you should be good.

---

### Post by daniele.rosa on 2010-01-17
Hi,

I am using the touch screen but it is not possible to activate the "mouse right button" dialog but holding down the finger on an item.
Of course I activated that feature for the mouse in the "Universal Access" and it works if I hold down the mouse left button.

Any idea?

Best,
Daniele

---

### Post by SergeantOreo on 2010-01-17
> **Favux said:**
> Hi SergeantOreo,

The wacom entries in your xorg.conf are the problem.  You want to just use the .fdi in Karmic.  The xorg.conf is also executing and that is what is messing up the configuration of your Intuos3.  So remove or comment (#) them (the Wacom sections) out in your xorg.conf including the corresponding "ServerLayout" lines.  For example the stylus section:
```
#Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "stylus"
#  Option        "Device"        "/dev/input/wacom"    # USB ONLY
#  Option        "Type"          "stylus"
#  Option        "USB"           "on"                  # USB ONLY
#EndSection
```and it's "ServerLayout" line:
```
#    InputDevice    "stylus"    "SendCoreEvents"
```And you do not have at least touch.  Once you've cleaned that up you should be good.

Hi Favux,

After removing all Wacom-related entries from my xorg.conf and restarting, pressure sensitivity and wacomcpl does not list duplicate entries; however, the only devices it lists now are the *stylus* and *eraser*. Do you have any suggestions?

Thanks.

---

### Post by Favux on 2010-01-17
Hi daniele.rosa,

I think you've done all you can.  I believe what you are asking for would be a new feature request to the LWP.  Since a bunch of Wacom multi-touch tablets have come out I know they are thinking of adding some new touch features for wacomcpl.  Gestures are present but not enabled through wacomcpl for example.  But they are pretty backlogged with other stuff they are doing.  But maybe this is the time to put the feature request in, with the understanding it may take a while.


Hi SergeantOreo,

Good!  You now have pressure.  And you can configure stylus, stylus buttons, and eraser with wacomcpl.

Check again that your .fdi is the one in [post #176]("http://ubuntuforums.org/showpost.php?p=7234134&postcount=176").

You haven't given me a lot of information.  You are in Karmic.  What other devices do you have?  Wacom mouse (cursor)?  Tablet buttons (pad)?  Do they work on another computer or in Windows?

Are you using the default linuxwacom in Karmic, 0.8.4-1?  Did you try to compile another version while you were looking at the LWP documentation?

---

### Post by SergeantOreo on 2010-01-17
> **Favux said:**
> 
Hi SergeantOreo,

Good!  You now have pressure.  And you can configure stylus, stylus buttons, and eraser with wacomcpl.

Check again that your .fdi is the one in [post #176]("http://ubuntuforums.org/showpost.php?p=7234134&postcount=176").

You haven't given me a lot of information.  You are in Karmic.  What other devices do you have?  Wacom mouse (cursor)?  Tablet buttons (pad)?  Do they work on another computer or in Windows?

Are you using the default linuxwacom in Karmic, 0.8.4-1?  Did you try to compile another version while you were looking at the LWP documentation?

Favux,

The .fdi that I used is [I]Favux_new-generic_rc2_10-linuxwacom.fdi.

[/I]My tablet is a Wacom Intuos3 6x8, with a mouse and pad (touchstrips and buttons). They work in Windows XP, and also in Ubuntu before I removed the wacom entries from xorg.conf; since doing that, only the stylus and eraser are listed in wacomcpl.

The linuxwacom driver I installed in Synaptic - version 1.0.8.4.1-0ubuntu4

---

### Post by Favux on 2010-01-17
Hmmm.  It should be working.  Hal-setup-wacom is obviously ok because you've got the eraser.  You're sure you removed all the wacom stuff from xorg.conf including lines in "ServerLayout"?  And your tablet is usb, correct?  Not serial.

We could look at your lshal:
```
lshal>SergeantOreo_lshal.txt
```
and your Xorg.0.log in /var/log/.  To upload them you need to compress them by right clicking and Create Archive.  Then you can attach them with Manage Attachments.

Yours is the second Intuos3 reporting this along with a Bamboo.

You might also want to try the Jaunty ext graphics_test 2 .fdi (the first one at post #176) and see if that makes a difference.

---

### Post by SergeantOreo on 2010-01-17
Yes, my tablet is usb.

I will give the other .fdi a whirl and let you know how it goes.
[B]
Edit:[/B] I switched out the suggested .fdi with Jaunty ext graphics_test 2 .fdi and simply put, nothing worked. The stylus was stuck in relative mode, wacomcpl did not list any devices, and I could not click on anything with the pen.

Also, I attached the files you requested.

---

### Post by Favux on 2010-01-17
Hi SergeantOreo,

OK, the Xorg.0.log shows everything setting up but ends with this error repeating many times:
```
eraser - usbParse: dropping empty event for serial 143682272
eraser - usbParse: dropping empty event for serial 143682272
eraser - usbParse: dropping empty event for serial 143682272
eraser - usbParse: dropping empty event for serial 143682272
eraser - usbParse: dropping empty event for serial 143682272
eraser - usbParse: dropping empty event for serial 143682272
eraser - usbParse: dropping empty event for serial 143682272
```
The lshal shows cursor and pad sections but seems to indicate the devices actually don't exist, just like the other Intuos3.

Given that the error is a usbParse error that could mean the wacom.ko from the linuxwacom drivers.  Looking at the LWP site I see "Fixed a serial number = 0 case in wcmUSB.c. Fixed a crash issue on Xserver 1.6 or later. Label 0.8.4-3."  Either or both could apply and wcmUSB.c is the source code for wacom.ko (the usb kernel driver/module).

So I think we're looking at the need to compile a newer linuxwacom.  I hope I'm right, because I don't want to have you doing that if not needed.  The version you would use is 0.8.4-4 at this [HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").

So I guess it's up to you if this seems reasonable and worth doing.  Since you are in Karmic I would uninstall wacom-tools with Synaptic and reboot before doing the compile.

---

### Post by SergeantOreo on 2010-01-17
> **Favux said:**
> Hi SergeantOreo,

OK, the Xorg.0.log shows everything setting up but ends with this error repeating many times:
```
eraser - usbParse: dropping empty event for serial 143682272
eraser - usbParse: dropping empty event for serial 143682272
eraser - usbParse: dropping empty event for serial 143682272
eraser - usbParse: dropping empty event for serial 143682272
eraser - usbParse: dropping empty event for serial 143682272
eraser - usbParse: dropping empty event for serial 143682272
eraser - usbParse: dropping empty event for serial 143682272
```
The lshal shows cursor and pad sections but seems to indicate the devices actually don't exist, just like the other Intuos3.

Given that the error is a usbParse error that could mean the wacom.ko from the linuxwacom drivers.  Looking at the LWP site I see "Fixed a serial number = 0 case in wcmUSB.c. Fixed a crash issue on Xserver 1.6 or later. Label 0.8.4-3."  Either or both could apply and wcmUSB.c is the source code for wacom.ko (the usb kernel driver/module).

So I think we're looking at the need to compile a newer linuxwacom.  I hope I'm right, because I don't want to have you doing that if not needed.  The version you would use is 0.8.4-4 at this [HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").

So I guess it's up to you if this seems reasonable and worth doing.  Since you are in Karmic I would uninstall wacom-tools with Synaptic and reboot before doing the compile.


Okay, I'll give the compiling a go then. :)

---

### Post by SergeantOreo on 2010-01-17
Under step 6 of the guide (copying the module), which command should I use, as I do not see one for 2.6.31 and linuxwacom 0.8.4-4; all of them are for linuxwacom 0.8.5 and up.

---

### Post by Favux on 2010-01-17
Use the Karmic one, it's the last one and is for 0.8.4-4 and kernel 0.2.6.31.

---

### Post by SergeantOreo on 2010-01-17
> **Favux said:**
> Use the Karmic one, it's the last one and is for 0.8.4-4 and kernel 0.2.6.31.

Using the last command, > sudo cp ./src/2.6.31/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko


the terminal prints: > cp: cannot stat `./src/2.6.31/wacom.ko': No such file or directory

What should I do now?

Thanks.



---

### Post by Favux on 2010-01-18
Hi SergeantOreo,

My unpacked 0.8.4-4 has a linuxwacom-0.8.4-4/src/2.6.31/ folder.  You can just dbl. click on the folder on your desktop and it should open up in Nautilus.  Then dbl. click on src and then 2.6.31 and see if a wacom.ko is there.  It should be there, if it isn't you could check the 2.6.28 and 2.6.27 folders but I doubt it will be in there.

Probably you missed a line you should have copied and pasted or left out " --enable-wacom" in:
```
./configure --enable-wacom --prefix=/usr
```
Actually the last one is probably the only way you wouldn't have seen some errors.

You could just repeat everything, making sure you haven't missed anything.  Read through the instructions carefully.

---

### Post by ranch hand on 2010-01-19
If a guy is looking at getting one of these buggers to run on 9.04 or more likely 9.10 is the Intios2 a good choice?

It seems to me that there has been little or no complaint about it being supported.

---

### Post by SergeantOreo on 2010-01-20
> **Favux said:**
> Hi SergeantOreo,

My unpacked 0.8.4-4 has a linuxwacom-0.8.4-4/src/2.6.31/ folder.  You can just dbl. click on the folder on your desktop and it should open up in Nautilus.  Then dbl. click on src and then 2.6.31 and see if a wacom.ko is there.  It should be there, if it isn't you could check the 2.6.28 and 2.6.27 folders but I doubt it will be in there.

Probably you missed a line you should have copied and pasted or left out " --enable-wacom" in:
```
./configure --enable-wacom --prefix=/usr
```
Actually the last one is probably the only way you wouldn't have seen some errors.

You could just repeat everything, making sure you haven't missed anything.  Read through the instructions carefully.


Okay, I was able to successfully compile linuxwacom several days ago, but wacomcpl still lists only the *stylus* and *eraser*.

---

### Post by Favux on 2010-01-20
Hi SergeantOreo,

That's funny (and not in a good way).  And you're sure the newly compiled wacom.ko was copied correctly into place over the old one?

Alright let's look at your lshal and Xorg.0.log again.  And that's with which .fdi?

---

### Post by SergeantOreo on 2010-01-20
> **Favux said:**
> Hi SergeantOreo,

That's funny (and not in a good way).  And you're sure the newly compiled wacom.ko was copied correctly into place over the old one?

Alright let's look at your lshal and Xorg.0.log again.  And that's with which .fdi?

Yes, at least I think so.. I used the command: > sudo cp /home/my username/Desktop/linuxwacom-0.8.4-4/src/2.6.31/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko

*The *.fdi I am using (as before) is *Favux_new-generic_rc2_10-linuxwacom.fdi.*

---

### Post by SergeantOreo on 2010-01-20
I am trying the guide again, and I see that I used a slightly different command in the part where *wacom.ko* is copied.

I used > sudo cp /home/my username/Desktop/linuxwacom-0.8.4-4/src/2.6.31/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko

instead of > sudo cp ./src/2.6.31/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko

**I am going through the guide again, by the way.**
**Do you think I should try adding entries for *just* the pad and mouse to xorg.conf?**

---

### Post by Favux on 2010-01-20
OK, the lshal and Xorg.0.log look cleaner (no xorg.conf entries).  Again it's saying the Wacom mouse and pad don't exist in lshal and also in Xorg.0.log.  Or at least that's my understanding of what it's saying.  Unless you truncated the Xorg.0.log the usb parse error is gone.

You can just boot into Windows and the Pad and Wacom mouse work?  If you are using a usb hub plug the tablet directly into the computer.  If not try changing the usb port you're plugged into.  And either way reboot.

Edit:  I wouldn't just yet.  Hold off on that sort of experiment for a bit.

---

### Post by SergeantOreo on 2010-01-20
> **Favux said:**
> OK, the lshal and Xorg.0.log look cleaner (no xorg.conf entries).  Again it's saying the Wacom mouse and pad don't exist in lshal and also in Xorg.0.log.  Or at least that's my understanding of what it's saying.  Unless you truncated the Xorg.0.log the usb parse error is gone.

You can just boot into Windows and the Pad and Wacom mouse work?  If you are using a usb hub plug the tablet directly into the computer.  If not try changing the usb port you're plugged into.  And either way reboot.

Edit:  I wouldn't just yet.  Hold off on that sort of experiment for a bit.

Yes, I am plugging it into a side usb port, not one of the ports on the back of the computer. I'll try switching and restart.
**After trying a usb port on the back of the case, there is still no difference; wacomcpl lists only the stylus and eraser.. :(**

---

### Post by Favux on 2010-01-20
Hi SergeantOreo,

OK, I'm stumped.  Hopefully I'm missing something obvious.

You might want to look at your Xorg.0.log and see if you have the usb parse error back.


@ ranch hand,

The Intuos2 is serial, correct?  A usb tablet might be better as serial tablets have been having toubles in Karmic.

---

### Post by ranch hand on 2010-01-20
No it is a usb connection.

---

### Post by Dimitree on 2010-01-21
Hello guys, i need little help with my Wacom bamboo 1 tablet.
I'm using Ubuntu 9.04 (because my DVB-S card works only on 9.04).
And i have dual monitor setup:
Nvidia driver from Nvidia website 190.53
TwinView enabled :: Main monitor Absolute 1680x1050 marked as first monitor :: second monitor (on the left) Absolute 1440x900.
I managed to make wacomcpl to start but i have one single problem.

When i use wacomcpl it doesn't matter what settings i put for the Screen number.
I set the mapping to Horizontal and then select Screen 0 or Screen 1 the result is the same.
The tablet starts working on the second monitor and it seams like it's using the resolution of the main monitor because the surface area extends a little to the main monitor.

Any idea why selecting Screen 0 or 1 makes the tablet work always on the second monitor and not the main one? And how to fix it? Or where should i look for problems?

Thank you in advance :(

---

### Post by SergeantOreo on 2010-01-21
> **Favux said:**
> Hi SergeantOreo,

OK, I'm stumped.  Hopefully I'm missing something obvious.

You might want to look at your Xorg.0.log and see if you have the usb parse error back.


Okay. Thanks loads for your help; I feel that I better understand the topic of linuxwacom a little better now. :)

Since the Linux Wacom Project can't give me the support I need for my tablet, I am going to use it in Windows XP with Photoshop instead..

Cheers!

---

### Post by psoulocybe on 2010-01-23
Anyone have Intuos3 working well in Photoshop CS2 using Crossover Linux?
The tablet is great in Gimp after using the custom .fdi, but in Photoshop, the eraser acts the same as the stylus, and I have no pressure sensitivity.
The only way I've seen someone with it working is using the old xorg.conf way of setting up wacom.

This is something I found on the Crossover support site: [codeweavers]("http://www.codeweavers.com/support/wiki/USBtoSerial")

---

### Post by ilcontegis on 2010-01-26
Guys, I have a really really big confusion...on this tread as on the net, everything is so messed up....do this if you have jaunty to that if you have karmic, don't do this if you have the bamboo, do that and this if you have the intuos 3 but not if you have the intuos 4.....

I would really appreciate if somebody could be so nice to tell me what should I do for my case. Please.

I have Karmic and a intuos4. The tablet is recognized by ubuntu, but is without any configuration. The pressure is working, but no eraser, and all the buttons (and the led screen) are not working.

Please tell me what should I do, In many guides they say that with the intous4 I should not configure anything (if I try nothing work anymore)....ok but, how can I make it work properly?

Thank you very much for your kind attention

---

### Post by Aphorism on 2010-01-31
Only the Jaunty works here. The "new-generic" lists only my eraser and stylus. Jaunty version for USB works as expected. Intuos 3 USB 6x11.

---

### Post by Favux on 2010-01-31
Hi Aphorism,

Thank you for the feedback.  You are in Jaunty?  The 'Jaunty ext graphics' for usb should really be 'Jaunty/Karmic ext graphics'.  It's sounding like the 'Wacom names "parser"' isn't working correctly for you in Jaunty.  Maybe the 'contains_not' filter/lines in it don't work right with the hal-setup-wacom or HAL version in Jaunty?  The 'contains_not' filter is suppose to screen out sub-devices that don't exist.

---

### Post by pdonadeo on 2010-02-07
This is a repost of [http://ubuntuforums.org/showthread.php?t=1366422](http://ubuntuforums.org/showthread.php?t=1366422)


Hi to all, I'm in trouble with my Wacom Graphire4 in Karmic. The situation is this: with a fresh new Ubuntu 9.10 installed (no upgrade) the Wacom tablet isn't even seen by the system.

Following [this post]("http://ubuntuforums.org/showpost.php?p=7234134&postcount=176") by Favux I was able so see the tablet via [FONT=Courier New]**xsetwacom list**[/FONT], but still have problems configuring pad button events.

I decided to switch to a text console (CTRL + ALT + F1) and turn Xorg off completely:

```
$ sudo service gdm stop
```

and try with:

```
$ wacdump /dev/input/wacom
```

but wacdump died with a segfault!

I decided to downgrade the wacom packages to the Jaunty version installing the versione 1:0.8.2.2-0ubuntu2:
[http://packages.ubuntu.com/jaunty/wacom-tools](http://packages.ubuntu.com/jaunty/wacom-tools)
and
[http://packages.ubuntu.com/jaunty/xserver-xorg-input-wacom](http://packages.ubuntu.com/jaunty/xserver-xorg-input-wacom)

In console wacdump works as expected (no more segfaults) and the tablet seems to generate all the correct events. So the tablet (I mean the hardware) works, it's something :-)

Next step: using xsetwacom to configure the tablet, and here are the problems: the software stack, I don't know where, can't associate the pad buttons and the scroll wheel on the Graphire4 to mouse button events.

Example:

```

xsetwacom set pad Button1 "core key A space"
xsetwacom set pad Button2 "core key B space"
xsetwacom set pad RelWDn "core key C space"
xsetwacom set pad RelWUp "core key D space"

```

produces the expected (dummy) result of printing a letter followed by a space on the terminal (under X) when the corresponding event occurs.

But when I try to associate the standard X events:

```

xsetwacom set pad Button1 "button 1"
xsetwacom set pad Button2 "button 3"
xsetwacom set pad RelWDn "button 5"
xsetwacom set pad RelWUp "button 4"

```

it simply doesn't work! I can't be more precise because **everything** seems to work but the generation of the low level mouse button events.


I have already searched extensively in this forum and I made some progresses, but I'm stuck here. Any ideas?

---

### Post by Aphorism on 2010-02-08
> **Favux said:**
> Hi Aphorism,
You are in Jaunty?  The 'Jaunty ext graphics' for usb should really be 'Jaunty/Karmic ext graphics'.  It's sounding like the 'Wacom names "parser"' isn't working correctly for you in Jaunty.  Maybe the 'contains_not' filter/lines in it don't work right with the hal-setup-wacom or HAL version in Jaunty?  The 'contains_not' filter is suppose to screen out sub-devices that don't exist.

No, in Karmic.

It only lists the two, where the USB only works fine.

---

### Post by ogromano on 2010-03-09
Hello all wise ubuntuforum-folk!

I'd appreciate some of your ubuntu-magic!!

After going through 80% of this thread and skimming the non-relevant parts, I have not been able to get my Wacom Bamboo Pen & Touch (CTH460) to work.
I've attached some screenshots and  the xlist output and also some terminal output to show what my system is doing.

I'm running Karmic 9.10 (Kernel 2.6.31-20-generic gnome 2.28.1) up to date from a clean install a couple of months ago.

- I've tried Favux's advice and also gali98's post 104 for the driver and still nothing.
- The tablet works perfectly in windows vista.
- I tried the xorg.conf edits and nothing.
- Changed the .fdi as recommended and nothing.
- lsusb states that it is connected.
- wacomcpl only draws the window on screen with no options to choose from.
- The light on the tablet shows activity upon using the pen or touch or buttons.

I'm still new to Linux so if you require anymore outputs please include the commands.

Thanks in advance for the help.

---

### Post by Ayuthia on 2010-03-09
> **ogromano said:**
> Hello all wise ubuntuforum-folk!

I'd appreciate some of your ubuntu-magic!!

After going through 80% of this thread and skimming the non-relevant parts, I have not been able to get my Wacom Bamboo Pen & Touch (CTH460) to work.
I've attached some screenshots and  the xlist output and also some terminal output to show what my system is doing.

I'm running Karmic 9.10 (Kernel 2.6.31-20-generic gnome 2.28.1) up to date from a clean install a couple of months ago.

- I've tried Favux's advice and also gali98's post 104 for the driver and still nothing.
- The tablet works perfectly in windows vista.
- I tried the xorg.conf edits and nothing.
- Changed the .fdi as recommended and nothing.
- lsusb states that it is connected.
- wacomcpl only draws the window on screen with no options to choose from.
- The light on the tablet shows activity upon using the pen or touch or buttons.

I'm still new to Linux so if you require anymore outputs please include the commands.

Thanks in advance for the help.

Have you tried this [thread]("http://ubuntuforums.org/showthread.php?t=1321238")?  ob1kenobi and others have been working on the development of it and it seems to be now in 0.8.5-10.

---

### Post by UncleZeiv on 2010-03-11
Hi,

  Wacom Graphire4 on Ubuntu 9.10, Karmic. Was working out of the box and correctly seen by Wacom Control Panel, but there was no way to set they pad keys. Tried the first fdi from Favux and now xsetwacom works, and I can set the keys. On the other hand, Wacom Control Panel doesn't work anymore... any ideas? It was pretty useful to set the pressure curves.

  Cheers!

---

### Post by BuffGuy900 on 2010-03-26
I have a similar problem with my Linux system

Only when tablet is in relative mode (as desired)

GIMP or Inkscape fixes the the drawing-tool coordinates at (0,0) on the WINDOW
or SCREEN (depending on program setting)

GIMP/Inkscape reports drawing-tool coordinates as if the the tool was placed at
(0,0) in the WINDOW or SCREEN
  This may be a negative value

The actual pointer (read by Kubuntu) exhibits desired/expected behavior
Therefore I can control menus, etc.

Since it happens in both GIMP and Inkscape, I think this is an issue with GTK

This does not occur when tablet is in absolute mode

Kubuntu 9.04 (Jaunty)
GTK v. 2.16.1-0ubuntu2
GIMP 2.6.6
Wacom Bamboo Fun 4x6


Also

[https://bugzilla.gnome.org/show_bug.cgi?id=154657](https://bugzilla.gnome.org/show_bug.cgi?id=154657)

---

### Post by BuffGuy900 on 2010-03-27
On that note, can **anybody** get GIMP to detect pressure sensitivity while using relative mode?

If so, can you post system specs / settings please?

(1) Ubuntu version
(2) Kernel version
(3) GTK version
(4) wacom version
(5) Wacom config method (FDI / Xorg.conf / wacomcpl)
(6) GIMP version

Thoughts?

---

### Post by JAKEOTR on 2010-03-28
Hello everyone...I have a Wacom UD0608R Digitizer ll serial tablet. I have everything working but the stylus is still flaky. I just need to get this working and it looks like 10.04 is not going to help. Can anyone tell me of other distros or older versions of Ubuntu (or anything for that matter) that work correctly with my tablet. I'll dual boot to another distro, use older versions of Gimp, whatever I have to do to get this operational! Please help, thanks

---

### Post by j.daniel on 2010-03-31
**Hello Forum,**

  Question: is it possible (via the HAL/fdi) to create multiple zones on the Intous? I seem to recollect that it was possible in xorg, but I have not seen anything like that when it comes to the HAL setup.

  Reason for asking is that I have a square Intuos2 and a 16:10 screen. Roughly half the area of my Intous will be unused if I want to map it proportionally, so I would like to use the otherwise wasted space for something useful.

  I'm running Karmic.

Cheers
/ Daniel

---

### Post by j.daniel on 2010-04-01
**Hi SergeantOreo & Favux,**

Just my $0.02: I haven't followed your whole thread, but it seems that you cannot see all devices when you use 'xsetwacom list'. I can't either, but I can modify them anyway... go figure.

I have replaced my original Karmic 10-linuxwacom.fdi with the modified fdi found in the first post, and after that I have (on my USB Intuos2) the following output from 'xsetwacom' which seems similar to what you describe:
[FONT="Courier New"]
daniel:~$ xsetwacom list
stylus           stylus    
eraser           eraser
[/FONT]

(I had nothing before I replaced the fdi). 'xinput' however gives me the following output:

[FONT="Courier New"]
daniel:~$ xinput --list | grep id=
"Virtual core pointer"	id=0	[XPointer]
"Virtual core keyboard"	id=1	[XKeyboard]
"AT Translated Set 2 keyboard"	id=2	[XExtensionKeyboard]
"ImExPS/2 Logitech Explorer Mouse"	id=3	[XExtensionPointer]
"stylus"	id=4	[XExtensionKeyboard]
"Power Button"	id=5	[XExtensionKeyboard]
"Power Button"	id=6	[XExtensionKeyboard]
"stylus pad"	id=7	[XExtensionKeyboard]
"stylus cursor"	id=8	[XExtensionKeyboard]
"eraser"	id=9	[XExtensionKeyboard]
"Macintosh mouse button emulation"	id=10	[XExtensionPointer]
[/FONT]

Even though xsetwacom does not list them, I can access and modify the 'stylus cursor' (haven't tried the pad) properties with commands like these:

[FONT="Courier New"]
daniel:~$ xsetwacom get stylus\ cursor mode
0
daniel:~$ xsetwacom get stylus mode
1
[/FONT]

FYI: I queried both the stylus and the cursor above to demonstrate that they are indeed different devices.

I hope this might be of some help.

Cheers!
/ Daniel

---

### Post by Obonic on 2010-04-05
I feel silly, but I'm not sure what I'm doing wrong.

I've tried everything I could think of.  I still can't get it to work.

I'm running karmic koala, and have an older serial tablet.  artZ II 6x8 (UD-0608-r)  That been giving me trouble.  It's hooked to a Serial to USB adaptor which might have something to do with it. 

I know I downloaded the Wacom tools and stuff I need, I just can't seem to get it to work.  

Any idea anyone? I'm still kinda of a noob so you might have to help me with baby steps.

---

### Post by spektre1 on 2010-04-22
Ok, so, I've done some digging on this already; Here's the problem.

 I'm running 10.4, and I understand that it's using DeviceKit now, which changes how HIDs work in the system. I have a Wacom Intuos 3 tablet and I'm trying to use it with Gimp. I've finally got it so it recognises and will use the pressure sensitivity, but I'm running a dual monitor setup, and there's apparently a known issue with Xinerama that causes it to map the tablet to the monitors funny. What it does is this: The tablet is split in half, with half on one monitor, half on the other... except for, the left half of the tablet maps to the left monitor's left half. Same on right, vice versa. So half my space is still unusable.
 It gets stranger.

 I loaded MyPaint to test functionality, and that kind of works. The paint cursor in that specific program shows up and maps like a default Windows multimonitor mapping would work(spanned across both monitors), with the X Cursor still mapping in the previous way I described. My preferred use case would be to have the tablet mapped to one display, and have a key to toggle which display on the tablet, which the wacom drivers in Windows allow for. I looked into the Wacom-tools, but apparently they no longer work in 10.4 because of the architecture changes. If I could even get it to map to a single monitor, this would be an acceptable work around.
Are there any suggestions?
I'm not even entirely sure who to contact to get this problem fixed, as I'm semi-competent with code, but not enough so to go digging through and attempting to fix it myself.

---

### Post by partymetroid on 2010-04-22
Hello.  I am running Ubuntu 10.04.  How do I go about changing the area of the tablet that is in use, so that I can change its aspect ratio to fit my screen?

If it helps I have a Wacom Inutos 6x8 tablet, and a monitor with a 16:10 aspect ratio.  Thank you. :)

---

### Post by j.daniel on 2010-04-22
**Hi partytmetroid,**

In Karmic (9.10) at least there are two ways: one "one shot" method and one permanent. Experiment with the "one shot" method and then when you're satisfied, fix it permanently. I hope that 10.4 have not changed this.

The "one shot" method is to use the xsetwacom command. The permanent is to modify the HAL .fdi files.

For the xsetwacom method, first run:
```
xinput --list | grep id=
```
...to see what your devices are called. You can see what my are called in post #488

To change the aspect ratio, you can manipulate the BottomY parameter. Do this to first query what the current parameter setting is and then set a new one (replacing 24000 with whatever you like).
```

xsetwacom get stylus BottomY
xsetwacom set stylus BottomY 24000

```

This will stay in effect until you unplug the tablet's USB cable or restart your computer.

For the permanent .fdi fix, there are two ways (note: I have not done this myself):
1) change the BottomY parameter or 2) enable the KeepShape parameter:

Copy the file ```
/usr/share/hal/fdi/policy/20thirdparty/10-linuxwacom.fdi
``` so you can restore it in case things get screwed up.

Open the file and figure out where the stylus is defined. Can't really help you here, I do not know the FDI file syntax, but I *believe* it is after lines that look something like this:
```
<merge key="input.x11_options.Type" type="string">stylus</merge>
<append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
<append key="wacom.types" type="strlist">eraser</append>
<append key="wacom.types" type="strlist">cursor</append>
<append key="wacom.types" type="strlist">pad</append>

```


Add either:
```
<merge key="input.x11_options.KeepShape" type="string">on</merge>
```

...or (again subtituting 24000 with whatever works for you)
```
<merge key="input.x11_options.BottomY" type="string">24000</merge>
```

...to the stylus (and you probably want to add it to the eraser as well).

These two parameters are explained in the wacom man page, leaf through ```
man wacom
```

Hope this helps 
/ Daniel

---

### Post by partymetroid on 2010-04-24
> **j.daniel said:**
> **Hi partytmetroid,**

In Karmic (9.10) at least there are two ways: one "one shot" method and one permanent. Experiment with the "one shot" method and then when you're satisfied, fix it permanently. I hope that 10.4 have not changed this.

The "one shot" method is to use the xsetwacom command. The permanent is to modify the HAL .fdi files.

For the xsetwacom method, first run:
```
xinput --list | grep id=
```...to see what your devices are called. You can see what my are called in post #488

To change the aspect ratio, you can manipulate the BottomY parameter. Do this to first query what the current parameter setting is and then set a new one (replacing 24000 with whatever you like).
```

xsetwacom get stylus BottomY
xsetwacom set stylus BottomY 24000

```This will stay in effect until you unplug the tablet's USB cable or restart your computer.

For the permanent .fdi fix, there are two ways (note: I have not done this myself):
1) change the BottomY parameter or 2) enable the KeepShape parameter:

Copy the file ```
/usr/share/hal/fdi/policy/20thirdparty/10-linuxwacom.fdi
``` so you can restore it in case things get screwed up.

Open the file and figure out where the stylus is defined. Can't really help you here, I do not know the FDI file syntax, but I *believe* it is after lines that look something like this:
```
<merge key="input.x11_options.Type" type="string">stylus</merge>
<append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
<append key="wacom.types" type="strlist">eraser</append>
<append key="wacom.types" type="strlist">cursor</append>
<append key="wacom.types" type="strlist">pad</append>

```
Add either:
```
<merge key="input.x11_options.KeepShape" type="string">on</merge>
```...or (again subtituting 24000 with whatever works for you)
```
<merge key="input.x11_options.BottomY" type="string">24000</merge>
```...to the stylus (and you probably want to add it to the eraser as well).

These two parameters are explained in the wacom man page, leaf through ```
man wacom
```Hope this helps 
/ Daniel
I'm pretty sure that Ubuntu rid itself of HAL with 10.04. :oops:

---

### Post by rbrown3rd on 2010-05-01
Hi guys.  I just rearranged my office and found my old Wacom Artpad II.  It is a serial device.  I upgraded to 10.04 a couple of days ago.  Is it possible to get the serial Artpad II on 10.04?

---

### Post by Favux on 2010-05-01
Hi rbrown3rd,

Sorry, I think the answer is no.  I don't believe non-ISDv4 serial devices work with xf86-input-wacom and Xserver 1.7.  See announcement near the top of the [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").  In fact you may need to go back to Hardy to get a Wacom Artpad II working right.

---

### Post by jomsa on 2010-05-06
> **spektre1 said:**
> 
 I'm running 10.4, and I understand that it's using DeviceKit now, which changes how HIDs work in the system. I have a Wacom Intuos 3 tablet and I'm trying to use it with Gimp. I've finally got it so it recognises and will use the pressure sensitivity, but I'm running a dual monitor setup,...

Ditto, Except i am using TwinView, and upon updating from 9.10 -> 10.04 i lost the setting that mapped the tablet only to one of the monitor. Everything else seems to work fine. I tried playing around with xsetwacom, but nothing happens. WacomCmp is empty too. though xsetwacom list dev lists some stuff. (pad, eraser and cursor). still using I3 A5. So how to get that setting back?

---

### Post by confubar on 2010-05-06
Waaaa, it stopped working. :frown:
I got my wacom intuos4 working once, and did it again after a kernel upgrade, with the instructions from Favux and gali98.
Suddenly, I have no idea why, the tablet does not work, at all. Rebooted, checked connections... nothing. The problem is not the tablet itself, because it works with a windows computer I tried.](*,)
Does anybody have any idea what the problem could be and how to fix it?:???:

---

### Post by Favux on 2010-05-07
Hi jomsa,

Check out posts #5 & #6 on this thread:  [http://ubuntuforums.org/showthread.php?t=1461978](http://ubuntuforums.org/showthread.php?t=1461978)  See if that works for you too.


Hi confubar,

Which version of Ubuntu are you using?  Jaunty, Karmic, Lucid, etc..  Can you think of anything that happened just before you lost the tablet?  Apparently unrelated updates or whatever.

---

### Post by jomsa on 2010-05-07
[FONT=monospace]This 

[/FONT]xsetwacom --list -v
Gives me this ->
```
Unknown command '--list'
Usage: xsetwacom [options] [command [arguments...]]

```

Repost of -> [http://ubuntuforums.org/showthread.php?p=9253182&posted=1#post9253182](http://ubuntuforums.org/showthread.php?p=9253182&posted=1#post9253182)

---

### Post by Favux on 2010-05-07
Try 'xsetwacom list -v'.

---

### Post by jomsa on 2010-05-07
List: Unknown argument '-v'

:D Fun aint it :D

---

### Post by Favux on 2010-05-07
Yep.  ;)

Let's see if your tablet shows up in:
```
xinput --list
```

---

### Post by jomsa on 2010-05-07
> **Favux said:**
> Yep.  ;)

Let's see if your tablet shows up in:
```
xinput --list
```

```
 Wacom Intuos3 6x8 eraser                    id=8    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos3 6x8 cursor                    id=9    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos3 6x8 pad                       id=10    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos3 6x8                           id=11    [slave  pointer  (2)]

```I mean if it wouldnt show, why would it work as good as it does? preasure sensitivity and such... dunno about the tablet key's as i dont use them too much really.

---

### Post by j.daniel on 2010-05-07
> **jomsa said:**
> [FONT=monospace]This 

[/FONT]xsetwacom --list -v
Gives me this ->
```
Unknown command '--list'
Usage: xsetwacom [options] [command [arguments...]]

```

Repost of -> [http://ubuntuforums.org/showthread.php?p=9253182&posted=1#post9253182](http://ubuntuforums.org/showthread.php?p=9253182&posted=1#post9253182)

Regarding this command: To see the parameters of xsetwacom, just run the command itself w/o any arguments. Then you can see that you've got it backwards:

```
xsetwacom -v list
```

...should do it

Cheers!
/ Daniel

---

### Post by jomsa on 2010-05-07
xsetwacom -v list works. And it lists ->

Wacom Intuos3 6x8 eraser eraser    
Wacom Intuos3 6x8 cursor cursor    
Wacom Intuos3 6x8 pad pad  

And the things suggested here -> [http://ubuntuforums.org/showthread.php?p=9253182&posted=1#post9253182](http://ubuntuforums.org/showthread.php?p=9253182&posted=1#post9253182) in post 5 - 6

Anything i try to "get" gives me 1. Except if i type parameter that does not exists.

xsetwacom get "Wacom Intuos3 6x8" BottomX
returns 1

xsetwacom get "Wacom Intuos3 6x8" SomeInvalidParameter
Get: Unknown parameter 'SomeInvalidParameter'

---

### Post by j.daniel on 2010-05-07
> **jomsa said:**
> xsetwacom -v list works. And it lists ->

Wacom Intuos3 6x8 eraser eraser    
Wacom Intuos3 6x8 cursor cursor    
Wacom Intuos3 6x8 pad pad  

And the things suggested here -> [http://ubuntuforums.org/showthread.php?p=9253182&posted=1#post9253182](http://ubuntuforums.org/showthread.php?p=9253182&posted=1#post9253182) in post 5 - 6

Anything i try to "get" gives me 1. Except if i type parameter that does not exists.

xsetwacom get "Wacom Intuos3 6x8" BottomX
returns 1

xsetwacom get "Wacom Intuos3 6x8" SomeInvalidParameter
Get: Unknown parameter 'SomeInvalidParameter'

Is there a "Wacom Intous3 6x8" device? Try to check the "full names" you see in the "xsetwacom list";
```
xsetwacom get Wacom\ Intous3\ 6x8\ cursor BottomX
```

Cheers!
/ Daniel

---

### Post by jomsa on 2010-05-07
xsetwacom get Wacom\ Intous3\ 6x8\ cursor BottomX

Returns:  1

---

### Post by Favux on 2010-05-07
Hi jomsa,

Could the xsetwacom part of your xf86-input-wacom been corrupted somehow?   You could try going to Synaptic Package Manager and telling it to reinstall xserver-xorg-input-wacom and rebooting.  That shouldn't hurt anything and might help.

---

### Post by jomsa on 2010-05-07
Tried, reinsalled booted, same thing. Returns 1.

Could it be that something from the previous installation (9.10) and all its crappy HAL FDI xorg  custom modifications be interfering?

---

### Post by Favux on 2010-05-07
I doubt it.  Xsetwacom list doesn't show the stylus like xinput list did (stylus = Wacom Intuos3 6x8).  Which bothers me.  Let's look at your Xorg.0.log in /var/log.  That often has coordinates too, so another reason to look at it.

---

### Post by jomsa on 2010-05-07
```
(II) config/udev: Adding input device Wacom Intuos3 6x8 (/dev/input/event6)
(**) Wacom Intuos3 6x8: Applying InputClass "evdev tablet catchall"
(**) Wacom Intuos3 6x8: Applying InputClass "Wacom class"
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.10.5
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(**) Option "Device" "/dev/input/event6"
(II) Wacom Intuos3 6x8: type not specified, assuming 'stylus'.
(II) Wacom Intuos3 6x8: other types will be automatically added.
(**) Wacom Intuos3 6x8: always reports core events
(II) Wacom Intuos3 6x8: hotplugging dependent devices.
(**) Option "Device" "/dev/input/event6"
(**) Wacom Intuos3 6x8 eraser: always reports core events
(II) XINPUT: Adding extended input device "Wacom Intuos3 6x8 eraser" (type: ERASER)
(--) Wacom Intuos3 6x8 eraser: using pressure threshold of 61 for button 1
(--) Wacom Intuos3 6x8 eraser: Wacom USB Intuos3 tablet speed=38400 maxX=40640 maxY=30480 maxZ=1023 resX=5080 resY=5080  tilt=enabled
(--) Wacom Intuos3 6x8 eraser: top X=0 top Y=0 bottom X=40640 bottom Y=30480 resol X=5080 resol Y=5080
(**) Option "Device" "/dev/input/event6"
(**) Wacom Intuos3 6x8 cursor: always reports core events
(II) XINPUT: Adding extended input device "Wacom Intuos3 6x8 cursor" (type: CURSOR)
(--) Wacom Intuos3 6x8 cursor: top X=0 top Y=0 bottom X=40640 bottom Y=30480 resol X=5080 resol Y=5080
(**) Option "Device" "/dev/input/event6"
(**) Wacom Intuos3 6x8 pad: always reports core events
(II) XINPUT: Adding extended input device "Wacom Intuos3 6x8 pad" (type: PAD)
(--) Wacom Intuos3 6x8 pad: top X=0 top Y=0 bottom X=40640 bottom Y=30480 resol X=5080 resol Y=5080
(II) Wacom Intuos3 6x8: hotplugging completed.
(II) XINPUT: Adding extended input device "Wacom Intuos3 6x8" (type: STYLUS)
(--) Wacom Intuos3 6x8: top X=0 top Y=0 bottom X=40640 bottom Y=30480 resol X=5080 resol Y=5080
(II) config/udev: Adding input device Wacom Intuos3 6x8 (/dev/input/mouse2)
(II) No input driver/identifier specified (ignoring)
```

the log contained shitload of stuff, but i think this was the most important bit?

---

### Post by confubar on 2010-05-07
Favux...
I am using jaunty, perhaps should go ahead and upgrade.
I let the update manager get some small odds and ends... not the kernel update: when I got that a while back I got the tablet working again by repeating what you had told me  to do. I poked around the update manager and didn't find any history of whatI had done.

---

### Post by Favux on 2010-05-07
Hi confubar,

You could try upgrading to Karmic.  It's about the same as Jaunty except 10-wacom.fdi becomes 10-linuxwacom.fdi.  I wouldn't go to Lucid just yet.  We're still trying to figure it out and Lucid lacks wacomcpl.  Or we could try to figure out what's happening if you're happy with Jaunty.


Hi jomsa,

I would have preferred to see the whole thing but from what you've showed it sure looks like the stylus is being rejected by the wacom driver and picked up by evdev.  Which doesn't make much sense.  How are you configuring?  Are you using just the 10-wacom.conf at /usr/lib/X11/xorg.conf.d/?

---

### Post by jomsa on 2010-05-07
I havent done any configuration really. I was on the hopes it would work from 9.10 directly, as it almost seemed to do.

The file 10-wacom.conf contains ->
```

Section "InputClass"
    Identifier "Wacom class"
    MatchProduct "Wacom|WACOM"
    MatchDevicePath "/dev/input/event*"
    Driver "wacom"
EndSection

Section "InputClass"
    Identifier "Wacom serial class"
    MatchProduct "Serial Wacom Tablet"
    Driver "wacom"
    Option "ForceDevice" "ISDV4"
EndSection

# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
    Identifier "Wacom N-Trig class"
    MatchProduct "HID 1b96:0001"
    MatchDevicePath "/dev/input/event*"
    Driver "wacom"
EndSection
```

---

### Post by Favux on 2010-05-07
Sorry, dbl. post.

---

### Post by Favux on 2010-05-07
OK, that looks correct.
> I havent done any configuration really.
In that case you wouldn't have any custom entries in /etc/X11/xorg.conf.d/.  Did you upgrade?  Were there Wacom entries in your xorg.conf?  Have you checked the contents?

We could try modifying a stylus button and see if that has any affect.  It should if the wacom driver has the stylus.
```
Section "InputClass"
    Identifier "Wacom class"
    MatchProduct "Wacom|WACOM"
    MatchDevicePath "/dev/input/event*"
    Driver "wacom"
    Option "Button2" "3"
EndSection
```

---

### Post by jomsa on 2010-05-07
Yeah i upgraded with the upgrade... automate,.. thingie. Forgot what it is called.
xorg.conf in /etc/X11 contains no mention of any kind about wacom.

Starting to feel annoying n00b... :S

---

### Post by Favux on 2010-05-07
Hi jomsa,

> Starting to feel annoying n00b... :S 
Don't, the Intuos3 has always been a little idiosyncratic.

So the conclusion is the match line is not picking up your Intuos3's stylus.  Maybe that's true with other Intuos3's?

So we need to follow the branch on the device tree that has your stylus.  See what's going on and if we can modify the match line.  To do that we need to look at udevadmin info:
```
udevadm info --export-db > $HOME/udevadm-info.txt
```
The whole thing.  Right click and compress it with Create Archive and attach to your next post.

Did you notice in your Xorg.0.log:
```
(--) Wacom Intuos3 6x8: top X=0 top Y=0 bottom X=40640 bottom Y=30480 resol X=5080 resol Y=5080

```
that bottom X & Y look like the sum of your two monitor's resolution?

---

### Post by jomsa on 2010-05-07
I have two monitors next to each other both running at 1680x1050 Now with my math, i cant make them to go over 10000 in any dimension :D Or then i am understanding something really wrong here. :S

I hope the attachment contains what you wanted.

---

### Post by pkchips on 2010-05-07
Hello guys, I'm getting a little confused and was hoping someone could help me.

I've tried to look through these threads and work things out for myself, and I now have the pen and the finger working as a pad. However, the buttons all seem to do the same thing: Move my mouse to the top left and open the GNOME menu.

I was wondering how to make my buttons work properly in Lucid? I don't understand the instructions here: [https://help.ubuntu.com/community/Wacom?highlight=((Wacom](https://help.ubuntu.com/community/Wacom?highlight=((Wacom)))

---

### Post by Favux on 2010-05-07
Hmmm.  The only Product I see is:
```
PRODUCT=56a/b1/102
```
With the first explicit stylus section looking like:
```
P: /devices/pci0000:00/0000:00:1a.1/usb4/4-1/4-1:1.0/input/input6
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1a.1/usb4/4-1/4-1:1.0/input/input6
E: PRODUCT=3/56a/b1/102
E: NAME="Wacom Intuos3 6x8"
E: EV==1f
E: KEY==1cff 1f00ff 0 0 0 0
E: REL==100
E: ABS==1000f00017f
E: MSC==1
E: MODALIAS=input:b0003v056Ap00B1e0102-e0,1,2,3,4,k100,101,102,103,104,105,106,107,110,111,112,113,114,140,141,142,143,144,145,146,147,14A,14B,14C,r8,a0,1,2,3,4,5,6,8,18,19,1A,1B,28,m0,lsfw
E: SUBSYSTEM=input
```
So do we just need to add?:
```
    MatchProduct "Wacom|WACOM|56a"
```

---

### Post by jomsa on 2010-05-07
> **Favux said:**
> Hmmm.  The only Product I see is:
```
PRODUCT=56a/b1/102
```With the first explicit stylus section looking like:
```
P: /devices/pci0000:00/0000:00:1a.1/usb4/4-1/4-1:1.0/input/input6
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1a.1/usb4/4-1/4-1:1.0/input/input6
E: PRODUCT=3/56a/b1/102
E: NAME="Wacom Intuos3 6x8"
E: EV==1f
E: KEY==1cff 1f00ff 0 0 0 0
E: REL==100
E: ABS==1000f00017f
E: MSC==1
E: MODALIAS=input:b0003v056Ap00B1e0102-e0,1,2,3,4,k100,101,102,103,104,105,106,107,110,111,112,113,114,140,141,142,143,144,145,146,147,14A,14B,14C,r8,a0,1,2,3,4,5,6,8,18,19,1A,1B,28,m0,lsfw
E: SUBSYSTEM=input
```So do we just need to add?:
```
    MatchProduct "Wacom|WACOM|56a"
```

Say what? To where? Huh? *fell of the cart*

---

### Post by pkchips on 2010-05-07
> **pkchips said:**
> Hello guys, I'm getting a little confused and was hoping someone could help me.

I've tried to look through these threads and work things out for myself, and I now have the pen and the finger working as a pad. However, the buttons all seem to do the same thing: Move my mouse to the top left and open the GNOME menu.

I was wondering how to make my buttons work properly in Lucid? I don't understand the instructions here: [https://help.ubuntu.com/community/Wacom?highlight=((Wacom](https://help.ubuntu.com/community/Wacom?highlight=((Wacom)))

Sorry, I forgot to mention I'm using the Bamboo pen & touch. The 4 buttons on the left aren't working as they should and I was wondering if there was a way to fix it?

My xsetwacom gives the following when listing verbose:

... Display is '(null)'.
... 'list' requested.
... Found device 'Virtual core XTEST pointer' (4).
... Found device 'Virtual core XTEST keyboard' (5).
... Found device 'Video Bus' (6).
... Found device 'Power Button' (7).
... Found device 'Sleep Button' (8).
... Found device 'Logitech USB-PS/2 Optical Mouse' (9).
... Found device 'AT Translated Set 2 keyboard' (10).
... Found device 'SynPS/2 Synaptics TouchPad' (11).
... Found device 'Macintosh mouse button emulation' (12).
... Found device 'Dell WMI hotkeys' (13).
... Found device 'Wacom Bamboo Craft Pen eraser' (14).
Wacom Bamboo Craft Pen eraser ERASER    
... Found device 'Wacom Bamboo Craft Pen' (15).
Wacom Bamboo Craft Pen STYLUS    
... Found device 'Wacom Bamboo Craft Finger pad' (16).
Wacom Bamboo Craft Finger pad PAD       
... Found device 'Wacom Bamboo Craft Finger' (17).
Wacom Bamboo Craft Finger TOUCH

---

### Post by Favux on 2010-05-07
Sorry jomsa,

In the usb snippet of 10-wacom.conf
```
Section "InputClass"
    Identifier "Wacom class"
    MatchProduct "Wacom|WACOM]56a"
    MatchDevicePath "/dev/input/event*"
    Driver "wacom"
    Option "Button2" "3"
EndSection
```


Hi pkchips,

It would look something like:
```
xsetwacom set "Wacom Bamboo Craft Finger pad" button1 "core key CONTROL z"
xsetwacom set "Wacom Bamboo Craft Finger pad" button2 "core key CONTROL y"
xsetwacom set "Wacom Bamboo Craft Finger pad" button3 "core key o"
xsetwacom set "Wacom Bamboo Craft Finger pad" button4 "core key p"
```
Use 'xinput --list' to check that the names are correct.  You can also use the ID numbers.  For xsetwacom commands see the [LWP's HOWTO]("http://linuxwacom.sourceforge.net/index.php/howto/xsetwacom").

You put them in a script, call it say .xsetwacom.sh, make it executable and add it to start up.

By the way you can toggle touch on and off with:
```
xsetwacom set "Wacom Bamboo Craft Finger" touch off
```

---

### Post by jomsa on 2010-05-07
Okay did it, but still getting just 1... Or what was the change supposed to do? (i rebooted just to be sure)

---

### Post by Favux on 2010-05-07
It returns 1 when the device doesn't exist, 0 when it's present.  So that didn't work.  You can remove the 56a.  Let me look again.  I don't see how you can have eraser without stylus.  This may actually be a bug in the xf86-input-wacom code.

Edit:  Ok, let's try:
```
Section "InputClass"
    Identifier "Wacom class"
    MatchProduct "Wacom|WACOM"
    MatchVendor "56a"
    MatchDevicePath "/dev/input/event*"
    Driver "wacom"
    Option "Button2" "3"
EndSection
```
As always back up 10-wacom.conf and be prepared to restore it from the command line if we break X.  There's some other stuff we could try.  But I think the syntax is for rules.d and won't work in a .conf.

Edit 2:  corrected ection to Section

---

### Post by jomsa on 2010-05-07
Well now it changed completely how it works.

xsetwacom list dev gives nothing. Also when i move the pen nothing happens, unless i press it against the pad. then it seems to act as normal mouse.

edit:
Actually this is strange, if i move my real mouse and then take the pen again i my hand, it works like it shuld (from above the pad) to the point when i touch the pad with it. Then it stops reacting.

---

### Post by Favux on 2010-05-07
Oops, truncated Section to ection.  Did you fix?

---

### Post by jomsa on 2010-05-07
Yyeah i noticed it before i made the modification. Still no go.

---

### Post by jomsa on 2010-05-08
I think i ... well we at irc channel, might have found the problem.  We purged all wacom related stuff from synaptic, and emptied the .deb thingie. And reisntalled it all. As we noticed te xsetwacom versio was omething like 0.1.6 or somesuch crap. as it should be something else. Now it atleast works.

---

### Post by Favux on 2010-05-08
Hi jomsa,

Great!  It's working!  :D

OK, let me try to rephrase.  See if I get this right.

What you discovered is you had the xsetwacom from 0.10.3 xf86-input-wacom with the 0.10.5 xf86-input-wacom X driver.  The 0.10.3 version was the first one included in Lucid, in alpha 3?  That was replaced by 0.10.5 for the Beta, rc, and final.  Do I have that right?

So you cleared everything and reinstalled the deb package xserver-xorg-input-wacom.  That got you 0.10.5 xf86-input-wacom driver and xsetwacom and now everything works?

How did you determine the version numbers of xsetwacom and xf86-input-wacom?  That would be very useful to know.

---

### Post by jomsa on 2010-05-08
xsetwacom -V  gave me 0.1.6 or something, and after asking around IRC someone said it should be 0.10.5 .. or something. After that i got instructions to purge Ubuntu of all Wacom related stuff via synaptic. And remove the installation packages that it keeps stored. And some strange folder, that i forget where it was, i think it was somewhere in my %home and hat files such as wacomcpl and such, removed that...  Then i restarted and made sure it definedly does not work. Then went againt to synaptic and reinstalled the xorgie thingie back. And after reboot, xsetwacom commands started to work again. And it shows proper version.

Sorry i allready forgot what the IRC dude told me to delete. And dont have backlog, and since i didnt know a bit what i was doing while following his instructions, i really dont know better than that :S

As i understood it .. it was like  the synaptic one was the right version, but it was overridden by some local / per user installation or something. Which was older version.

---

### Post by Favux on 2010-05-08
Hi Hi jomsa,

Thanks.  I think I gottcha.  You upgraded and wacom-tools and xsetwacom from linuxwacom 0.8.6 was still installed on your system.  Along with wacomcpl's .xinitrc in your home directory.  He showed you how to delete them.   That way the interference was removed.  And then you reinstalled xf86-input-wacom with it's xsetwacom version, which is the Lucid xserver-xorg-input-wacom.

---

### Post by mazui on 2010-05-09
Hello. I'm trying to get the pad buttons and strips to work. The buttons are ok as long as I use a-z and numbers, but when I try to use , and . (comma and period) nothing happens.

```
xsetwacom set "Wacom Intuos3 6x11 pad" Button5 "core key ,"
```

Xev says that , has the key code 0x2c and that . has 0x2e. I've tried using the code argument in xsetwacom, but it doesn't seem to do anything:

```
xsetwacom set "Wacom Intuos3 6x11 pad" Button5 "code 0x2e"
```


The strips doesn't work no matter what character I try to assign them to, but they do give a FocusOut event:

```
FocusOut event, serial 36, synthetic NO, window 0x4800001,
    mode NotifyGrab, detail NotifyNonlinear
```

This causes Compiz to show all windows, which is not what I want.


Any ideas on how to solve this?

---

### Post by himbert on 2010-05-09
Hello everybody
Im trying desperatly to get my Wacom Bamboo Pen & Touch working on Ubuntu 10.04 and since I didn't get any help from the german forum, I decided to ask here (Hope my english skills are acceptable).

I've already read several instructions and how-tos but they are always very confusing for a new user like me. Also they are often for older version of Ubuntu or for different tablets.

Now what I need is an easy and lucid step by step instruction how i can install my Wacom Bamboo Pen & Touch on Ubuntu Lucid Lynx please.

I would be very very thankfull if anyone can help me.

---

### Post by Favux on 2010-05-09
Hi himbert,

Welcome to Ubuntu forums!

Your English is better than my Deutsch, that's for sure.

First you want to compile linuxwacom 0.8.6-1 for the wacom.ko.  If you do it normally it will fail because the config picks up the /src/xdrv directory and tries to build the X driver.  Linuxwacom's X driver doesn't work with the Xserver 1.7 in Lucid.  So what you do is after:
```
./configure --enable-wacom --prefix=/usr
```
you change directory again to:
```
cd src/2.6.30
```
and then just do:
```
make

sudo cp wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko

sudo depmod -a
```
and reboot.  That skips the X driver and let's you compile the wacom.ko.

The X driver for Lucid is Xorg's xf86-input-wacom.  To get that you clone it from it's git repository and compile it.

This is all described in the [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").  Section 1 describes how to compile linuxwacom for the wacom.ko.  You shouldn't need to clone xf86-input-wacom because the default version in Lucid is 0.10.5 which supports your P&T.  There is a new gesture patch coming in a week or so.  Then it would be worth cloning the git.  This is described in Appendix 5.  Just skim through the HOW TO and then reread the relevant sections.  It's not as complicated as it looks, just a lot of explanation in there.

Hope this helps.

---

### Post by himbert on 2010-05-09
Great it worked! Thank you very much.

---

### Post by MarkoCro on 2010-05-18
Guys I have updated [http://help.ubuntu.com/community/Wacom]("http://help.ubuntu.com/community/Wacom") for Ubuntu 10.04. I have added Method 1 for editing Wacom options that works better than method that has already been there (I have left it under Method2 for people that have no luck with Method1). Please try and write here if it works, cause it should. Thanks. :)

---

### Post by Armence on 2010-05-20
I just got my Bamboo Pen & Touch and I'm trying to install it on Ubuntu Lucid Lynx 10.04. As of right now, I have no success. It does nothing at all.

It is correctly plugged into the USB port and I have restarted 2 or 3 times alread.

I have installed xserver-xorg-input-wacom

```
xsetwacom --list -v
```

returns

```
... Display is '(null)'.
... 'list' requested.
```

```
xinput --list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; USB Mouse                               	id=9	[slave  pointer  (2)]
&#9116;   &#8627; Chicony HP Wireless Receiver            	id=12	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=13	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Chicony HP Wireless Receiver            	id=10	[slave  keyboard (3)]
    &#8627; Chicony HP Wireless Receiver            	id=11	[slave  keyboard (3)]

```

It does appear to be recognized as a USB device:

```
lsusb
Bus 004 Device 003: ID 056a:00d1 Wacom Co., Ltd 
Bus 004 Device 002: ID 049f:008d Compaq Computer Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 005: ID 15d9:0a41 Dexon 
Bus 003 Device 002: ID 0416:5518 Winbond Electronics Corp. 4-Port Hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

But that is honestly a small consolation for the fact that it does not do anything... ;)

Any help would be greatly appreciated.

---

### Post by Favux on 2010-05-20
Hi Armence,

Welcome to Ubuntu forums!

You need to compaile a newer wacom.ko like I told himbert to do in post #537 above.  You don't have to worry about the extra directory change he had to do when using linuxwacom 1.0.8.6-2.  It now checks what Xserver is present and with 1.7 the build.in skips the X driver and will just give you the wacom.ko.

Hope this helps.

---

### Post by Armence on 2010-05-20
Thanks for the help. Unfortunately, it still does not work. When running the configure script, I get the following at the end:

```
----------------------------------------
  BUILD ENVIRONMENT:
       architecture - x86_64-linux-gnu
       linux kernel - yes 2.6.30
  module versioning - no 
      kernel source - yes /lib/modules/2.6.32-21-generic/build
     XFree86 source - no 
           Xorg SDK - yes /usr/include/xorg
          XSERVER64 - yes
           dlloader - yes
               XLib - yes /usr/lib
         xf86config - no
                TCL - yes /usr/include/tcl8.4
                 TK - yes /usr/include/tcl8.4
            ncurses - yes

  BUILD OPTIONS:
            wacom.o - yes
            wacdump - no 
             xidump - no 
        libwacomcfg - no
         libwacomxi - no
          xsetwacom - no
          wacomxrrd - no
              hid.o - no 
       wacom_drv.so - no /usr/lib/xorg/modules/input 
        wacom_drv.o - no
  wacom*_drv quirks - IsXExtensionPointer key-events dixScreenOrigins
----------------------------------------

Note: this package only supports Xorg server older than 1.6.5.
          You are running a newer version. 
Please build xf86-input-wacom instead.

You can build the kernel driver from this package though.

```

---

### Post by Favux on 2010-05-20
I think you're good despite the warning.  It says:
```
wacom.o - yes
```
so it is ready to build the wacom.ko.  And:
```
       wacom_drv.so - no /usr/lib/xorg/modules/input 
        wacom_drv.o - no

```
So the configure.in is not planning on building the X driver.

Are you saying that make then doesn't work?

---

### Post by Armence on 2010-05-20
It was my bad, I should have checked out the HowTo more carefully. I needed to also follow the xf86-input-wacom instructions. It works now...

---

### Post by Favux on 2010-05-20
Good!  :)

---

### Post by fidodo on 2010-05-22
I'm having some trouble getting my tablet pc (Lenovo X200) to work. So far I've gotten Wacom stylus input to work correctly, but I have a stylus/multitouch screen so I'm having trouble with the multitouch part.

I'm using 9.10 and I followed the guide [https://help.ubuntu.com/community/WacomTroubleshooting#serial](https://help.ubuntu.com/community/WacomTroubleshooting#serial).

What I'm noticing is that after I restart X, the stylus input works correctly, I'm able to run wacom tools and configure it, everything works great.

When I touch the screen with my finger it responds for a couple inputs and places the cursor in the top left and responds as if it were clicking. But after that all input stops, and not even the pen works anymore.

I tried commenting out the touch input section, and the same thing happens, except when I touch my finger nothing happens at all, but the stylus stops responding.

I feel like I'm close to getting it to work. Thanks for any help anyone can give me.

---

### Post by Favux on 2010-05-22
Hi fidodo,

I think this thread will help you get set up:  [http://ubuntuforums.org/showthread.php?t=1356075](http://ubuntuforums.org/showthread.php?t=1356075)  You can post any questions on it.

---

### Post by fidodo on 2010-05-22
Thanks Favux!

---

### Post by odd on 2010-05-23
Hi everyone

I also have Lenovo X200 TabletPC. I managed to get tablet and touchscreen work quite easy on Lucid (10.04) since it almost worked right from the Lucid LiveCD.
But from what I've noticed, changing pressure curve (with xsetwacom) doesn't seem to take effect. xsetwacom reports presscurve as 0,0,100,100, then I'm changing it to, say 50,0,100,0, xsetwacom says it's changed, but i don't see the difference on apps (Gimp, Xournal) - it still has too sensitive (hard to draw thin line - little more pressure causes max pressure in app).
And Gnome Tablet Apps ([http://alexmac.cc/tablet-apps/](http://alexmac.cc/tablet-apps/)) sees tablet devices, shows straight presscurve from bottom-left to top-right and I can't change it.
Any ideas?
I'm using xserver-xorg-input-wacom 1:0.10.5

---

### Post by odd on 2010-05-23
And I've checked it on my PC with Wacom Intuos3 (Lucid, 64bit though) - changing presscurve through xsetwacom works here, so the issue is tabletPC/x200-specific.

---

### Post by jetsam on 2010-05-23
Anybody know how to get the Waccom Mole Easter Egg going on the New Bamboo (That's the Bamboo, Trew You.)?

---

### Post by Favux on 2010-05-23
Hi odd,

That looks to be new.   You could try reinstalling xserver-xorg-input-wacom through Synaptic in case there was some kind of corruption of xsetwacom during the install.

The only pressure bug reported on LWP's bug tracker is about touch.  Assuming your Intous3 is usb it may be a problem with the ISD4 protocol for serial tablet pc.s.  I know that is being worked on.  Maybe you should post a bug if you don't find a solution:  [https://sourceforge.net/tracker/?group_id=69596&atid=525124](https://sourceforge.net/tracker/?group_id=69596&atid=525124)

---

### Post by bdpetersen on 2010-05-23
Hoping someone can help me figure out why I can't get "relative" mode to work on my Wacom tablets....

System is Lucid on a Thinkpad W701. There are two Wacom tablets I'm trying to get working, the Wacom digitizer that's built in on the Thinkpad, and a Wacom Intuos 2 (USB).

I installed linuxwacom, as in Favux's HOWTO, and wacom.ko shows up correctly with modinfo. I also installed the latest version of xf86-input-wacom (0.10.6), again as described in the HOWTO. Both tablets now work, but only in "absolute" mode. I've included the correct "Option" line in the 10-wacom.conf file, and played around with other ways of writing that file (see below), and nothing helps.

Only oddity I can find is that "xsetwacom -v list" doesn't show the tablets (returns "null"), which I'm assuming (based on what I've read here) isn't supposed to happen. The tablets show up as expected with lsusb and xinput.

I've tried several variants of the 10-wacom.conf file. First one is similar to the supplied version:

```
Section "InputClass"
	Identifier "Wacom class"
	MatchProduct "Wacom|WACOM"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
        Option "Mode" "Relative"
EndSection

Section "InputClass"
	Identifier "Wacom serial class"
	MatchProduct "Serial Wacom Tablet"
	Driver "wacom"
	Option "ForceDevice" "ISDV4"
        Option "Mode" "Relative"
EndSection

# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
	Identifier "Wacom N-Trig class"
	MatchProduct "HID 1b96:0001"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
        Option "Mode" "Relative"
EndSection
```

Second version is derived from the xorg.conf that worked for me with older releases of Ubuntu:

```
Section "InputDevice"
	Identifier	"stylus"
	Driver		"wacom"
	Option		"Device"	"/dev/input/event*"
	Option		"Type"	"stylus"
	Option		"Mode"	"Relative"
EndSection

Section "InputDevice"
	Identifier	"eraser"
	Driver		"wacom"
	Option		"Device"	"/dev/input/event*"
	Option		"Type"	"eraser"
	Option		"Mode"	"Relative"
EndSection

Section "InputDevice"
	Identifier	"cursor"
	Driver		"wacom"
	Option		"Device"	"/dev/input/event*"
	Option		"Type"	"cursor"
	Option		"Mode"	"Relative"
EndSection
```

Third version is the same as the second one, but replaces /dev/input/event* with /dev/input/wacom. Symbolic links for /dev/input/wacom do appear correctly (linked to /dev/input/event8, at the moment). This version actually *changes* something, but not for the better; "relative" mode still doesn't work, the pen movement on the tablets gets very jerky, and the laptop's touchpad stops working altogether.

Any guesses, assistance, or brilliant ideas would be much appreciated!!!

BarbP

---

### Post by MarkoCro on 2010-05-24
To bdpetersen:

Try ```
man wacom
``` so if something changed with Mode Relative option it would show there. If not, this is a bug. Go to [http://sourceforge.net/tracker/?atid=525124&group_id=69596&func=browse]("http://sourceforge.net/tracker/?atid=525124&group_id=69596&func=browse") and file a bug.

I havent tried xf86-input-wacom (0.10.6). Hope it will solve my problem with not being able to run Rythmboc, F-spot or Shotwell with my Bamboo One. When i run those programs, LED on my wacom starts to blink and Gnome crashes to login. Sometimes there is some D-Bus error message.

---

### Post by BuffGuy900 on 2010-05-24
Regarding relative mode, FYI these bugs exist:

[https://bugzilla.gnome.org/show_bug.cgi?id=614020](https://bugzilla.gnome.org/show_bug.cgi?id=614020)

and

[https://bugzilla.gnome.org/show_bug.cgi?id=154657](https://bugzilla.gnome.org/show_bug.cgi?id=154657)

---

### Post by abhiram.sharma on 2010-06-03
hello, 

I'm using lucid. and i've got my bamboo fun pen and touch to work.. Also, have been able to disable touch on it. Now I need to **customize the buttons** on it- and i've spent a LOT of time trying to do that...and- its really frustrating so far to set up this device- which i expected would work right out of the box :mad:

It would really help me if someone could tell me, for eg. how to set one of the strip keys to '[' (and another to ']' : then they'd increase/decrease brush size on gimp).

thank you

---

### Post by Favux on 2010-06-03
Hi abhiram.sharma,

Welcome to Ubuntu forums!

I think some of your problems with pad buttons are driver related.  The default xf86-input-wacom is 0.10.5 and fixes have been added since that.  So you might want to either download and compile the 0.10.6 tar or clone the git.

Assigning pad buttons I think is discussed around page 90 on the [Bamboo P&T development thread]("http://ubuntuforums.org/showthread.php?t=1321238").

I think the 'core' keyword has been deprecated.  If you clone the git a new 'man xsetwacom' has been added (in addition to the 'man wacom'.

Hope this helps.

---

### Post by abhiram.sharma on 2010-06-03
thank you,
just got it working :)
the following code configured the keys as i needed them:
```
xsetwacom set "Wacom BambooFun 2FG 6x8 Finger pad" button1 "core key SHIFT equal"
xsetwacom set "Wacom BambooFun 2FG 6x8 Finger pad" button2 "core key ALT x"
xsetwacom set "Wacom BambooFun 2FG 6x8 Finger pad" button3 "core key ALT z"
xsetwacom set "Wacom BambooFun 2FG 6x8 Finger pad" button4 "core key minus"
```
Now to adjust the pressure sensitivity- its just a little oversensitive by default i think, need it to be firmer..
Yes, only problem now is that after i restart i have to run the code again... there should be a way around that too..

---

### Post by Favux on 2010-06-03
Nice work!

Sure create a file, call it say .xetwacom.sh.  Add the commands.  In Properties make it executable/allow run as program.  Then set it up in Startup Applicatcions so it's run with each Session.

---

### Post by abhiram.sharma on 2010-06-03
Thank you so much :)
should have asked much earlier- would have saved a days time..

---

### Post by chris_0076 on 2010-06-03
Hey, I just upgraded to 10.04 about a week ago and have just now set up to get my tablet to work, well sort of.

This is what I currently have in my xsetwacom.sh file (which is added to my startup programs), and that works just fine. My problem is that it is taking the "CTRL" in in Ctrl z and Ctrl y as being Ctrl + Shift... any explanation?
```
xsetwacom set "Wacom BambooFun 4x5" "Button2" 3
xsetwacom set "Wacom BambooFun 4x5" "Button3" 2
xsetwacom set "Wacom BambooFun 4x5 pad" "Button1" "key CTRL"
xsetwacom set "Wacom BambooFun 4x5 pad" "Button2" "key SHIFT"
xsetwacom set "Wacom BambooFun 4x5 pad" "Button3" "key CTRL Y"
xsetwacom set "Wacom BambooFun 4x5 pad" "Button4" "key Ctrl Z"

```

---

### Post by KonfuseKitty on 2010-06-20
Hello all,

A total newbie needs your help!

Coming from the Apple Mac world, I built an AMD box two days ago, installed Ubuntu 32bit and 64bit on two different partitions, and started to play. Touch wood, everything's been going well - except for using my Wacom Graphire3 tablet.

Namely, Gimp seems to recognise the tablet, as I can use the stylus on the pad to paint with pressure sensitivity. The problem is that the cursor behaves in a manner that makes it impossible to move it about the screen. Whenever I move the cursor to a new position by hovering the stylus over the pad, after I lift the stylus and move it back toward where I started, the cursor also moves back. This gives the cursor movement an erratic, seemingly random quality. Very frustrating.

Adjusting the settings in Gimp to Window or Screen makes no difference. I then followed the advice given here at Ubuntu and added <Option "KeepShape" "on"> to the file 10-wacom.conf, as the advice suggests. This also makes no difference. I then tried downloading the driver again with <sudo apt-get install xserver-xorg-input-wacom wacom-tools> but got the reply that it's already the newest version.

I have read the HOWTO advice at the official Wacom Linux site, but I find it too confusing. It doesn't help that different advice seems to apply to different versions of Ubuntu.

I'm hoping someone here will be able to give me advice that I can apply with confidence and get this sorted. Particularly if compiling is involved, as I have never compiled anything before.

EDIT: I'm using Ubuntu Lucid Lynx 10.04.

---

### Post by majedaly on 2010-06-20
Hello,
I have a problem trying to install wacom on Fujitsu tablet t4010, with
UBUNTU 9.1 I tried installing linuxwacom-0.8.8-3 a and
linuxwacom-0.8.4-4 after doing the proper uninstall. I followed the
instructions for serial tablet>
I get the error 
 undefined symbol: xf86errno
(EE) Failed to load /usr/lib/xorg/modules/input//wacom_drv.so
(II) UnloadModule: "wacom"
(EE) Failed to load module "wacom" (loader failed, 7)


The tablet works fine on win 7, with the stylus, so it is not a hardware
problem.
Below is the unix version. I checked to see the driver in
the /usr/lib/xorg/modules/input 
and found the driver

Linux majed-laptop 2.6.31-22-generic #60-Ubuntu SMP Thu May 27 00:22:23
UTC 2010 i686 GNU/Linux

Please find attached the xorg.conf and the xorg.0.log files. 
Appreciate your support
Thanks

---

### Post by j.daniel on 2010-06-20
> **KonfuseKitty said:**
> Hello all,
The problem is that the cursor behaves in a manner that makes it impossible to move it about the screen. Whenever I move the cursor to a new position by hovering the stylus over the pad, after I lift the stylus and move it back toward where I started, the cursor also moves back. This gives the cursor movement an erratic, seemingly random quality. Very frustrating.


I am a little confused over what your problem is.

As I understand it, your stylus is set to "absolute" position and not "relative". In "absolute" mode, the same point on the pad always correspond to the same point on the screen; i.e if you lift the stylus and put it down somewhere else, the cursor will jump to the new position. In "relative" mode, it works like a mouse; you can lift the stylus, move it somewhere else and then when you put the stylus back on the pad, the cursor does not move.

If this is the problem, you need to change the mode of the stylus (and eraser too) to relative. Don't know how that is done on 10.04, but I think that you can find out from this thread. If my mind is serves me correctly it you do it with some Xorg like settings.

Edit: I believe the file is called *10-wacom.conf*. Do a *find / -xdev -name 10-wacom.conf* to find it.

Cheers
/ Daniel

---

### Post by KonfuseKitty on 2010-06-20
> **j.daniel said:**
> As I understand it, your stylus is set to "absolute" position and not "relative"

Thanks, Daniel. I've just done some tests that led me to believe this is indeed the case, the cursor position on screen corresponds to stylus position on the pad. I'll do some more searches and report back if I find a fix.

---

### Post by KonfuseKitty on 2010-06-20
OK, some progress. I have read through the thread and added <Option "Mode" "relative"> to 10-wacom.conf. This has done the trick, it works! But there's a new problem: I've lost pressure sensitivity. How can I get it back? I also note that the eraser behaves like a stylus, it paints instead of erasing. I don't know whether this is a new problem as I didn't test the eraser while the movement was absolute.

All help will be appreciated. In the meantime, I'm off to do some more searches...

---

### Post by Richard002 on 2010-06-23
Wacom introduced their first cordless pen and earned a reputation for producing high quality pen tablets. Tablets are quite easy to get the hang of once you familiarize yourself with the basic distinguishing characteristics.

---

### Post by ShiintoTenshi on 2010-06-24
Ok first off let me just say I'm a complete Newbie when it comes to  Linux. So I'm not even sure about half of what i've read here. But here  is the problem I have a Wacom Intuos 1 tablet that is serial connected  and I'm running Ubuntu 10.04 and it apparently isn't finding it or the  drivers are not working, because I can have the power on when I boot or  turn it on after and no difference. It will not register any movement of  the cursor from the stylus. 

Also as a side note, I don't even know how to edit the files I've seen  posted in some of the tutorials. Is there a command line or something  you have to open? Please have patients I'm trying to learn as I go. I  LOVE Linux so far with the exception of trying to get a few drivers to  work.

---

### Post by Favux on 2010-06-24
Hi ShiintoTenshi,

Welcome to Ubuntu forums!

I'm sorry to tell you serial tablet support was lost in the move to Xorg's xf86-input-wacom for the Xserver 1.7 in Lucid.  There are some patches to add serial support back in.  A couple folks have their serial tablets working using them.  See the Notice near the top of the [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").

Admittedly a little daunting for a newbie.  To open a terminal and run command line commands:  Applications > Accessories > Terminal.

Hope this helps.

---

### Post by ShiintoTenshi on 2010-06-27
Thank you for your advice maybe I'll get it working. LOL I was hoping it would be easy but you know what they say.....it's never easy.

---

### Post by ManDay on 2010-07-15
Hello, I've got a problem and I'm stuck.

So I've gone through everything on the WACOM LINUX PROJECT (WLP) page, compiling wacom.ko for the kernel, which probed well. Since wacom_drv on the WLP is out of date with X I used the one from the repos which I assume is fine.

The tablet worked ebfore I did that and it worked equally well afterwards. So I don't know whether my effort made a difference but I just wanted to mention it

Now i have some major problems i cant solve. The Stylus works including pressure but the tablet buttons (not to mention the indicator lights) do not work at all. When  I press a butto or touch the scrollwheel my cursor just randomly jumps into the upper-left corner of the screen and nothing else happen. If I touch the scroll wheel in GIMP I "oscillate" between two tools.

Now there are several weird issues:

first udev says that

/dev/input/
 wacom
 tablet-intuos4-6x9
 event6

are the devices associated and aliased with the tablet. but none of them gives any output with xxd no matter what I do (move the stylus, press a button, move the scrollwheel) - however, as I said, the stylus works - how can that even be possible?

What do I have to do to make the scrollwheel show up as a Mouse Wheel for X? I want to freely configure what happens if I press any of the buttons (what XFree86-event gets triggered)

Any help?  Please!

---

### Post by cheshirekow on 2010-07-21
First of all, I'm sorry for posting a reply as I'm sure the answer to my question is already in this thread. The problem is that I now have 10 tabs open in firefox because the wiki points to the forums which point back to parts of the wiki which points to supplementary documentation which points to certain posts in the forum thread... 

and now I'm completely lost. Maybe if I were 8 and still into choose-your-own adventure I would find this more fun.

I have a Wacom Bamboo Fun CTE 650. I'm running 10.04 and the default setup *mostly* works. The pen and eraser work fine, but all the buttons and the touch ring on the pad just move the cursor to the top left part of the screen. From reading the wiki it sounds like I need to abandon the default setup and edit xorg.conf (actually /usr/lib/X11/xorg.conf.d/10-wacom.conf). But then everything in the page on how to edit xorg.conf ([https://help.ubuntu.com/community/WacomTroubleshooting](https://help.ubuntu.com/community/WacomTroubleshooting)) seem to be for older versions and the copious "You could hose X if put one space character in the wrong place or if the moon is at the right phase and the planets are in certain alignment when you reboot" warnings are scaring me from actually trying anything.

So, what do I need to do to get the buttons on the pad working? Any help would be appreciated.

(P.S. I don't mean to complain about the forums/documentation, I appreciate that everyone has contributed all this information and I understand that the nature of community contribution leads to this sort of thing)

---

### Post by Favux on 2010-07-21
Hi Manday and cheshirekow,

There have been updates and fixes to xf86-input-wacom so that the default 0.10.5 is dated.  That's probably why you're not seeing pad support etc.  Try updating it by cloning the git.  You may want to update the wacom.ko also.  See I. and II. on the [Bamboo HOW TO]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1").

---

### Post by cheshirekow on 2010-07-22
> **Favux said:**
> There have been updates and fixes to xf86-input-wacom so that the default 0.10.5 is dated.  That's probably why you're not seeing pad support etc.  Try updating it by cloning the git.

Thanks. I built from the git trunk and the pad buttons work now. The touch ring is quite jittery, but at least it's semi-functional now. I'll look more into this problem later (maybe there are some threshold settings or something)

>   You may want to update the wacom.ko also.  See I. and II. on the [Bamboo HOW TO]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1").

FYI, I tried to update wacom.ko from the linuxwacom git, (I) from your link, but the configure script told me that it's only for X versions below [something] and that my X was newer and that I should use xf86-input-wacom instead.

---

### Post by Favux on 2010-07-22
Hi cheshirekow,

> FYI, I tried to update wacom.ko from the linuxwacom git, (I) from your link, but the configure script told me that it's only for X versions below [something] and that my X was newer and that I should use xf86-input-wacom instead.
You misread the warning.  It's telling you the linuxwacom X driver wacom_drv.so won't build on Xservers 1.7 and above so use xf86-input-wacom.  The wacom.ko is fine.  What was happening is the fact that the linuxwacom X driver wouldn't build was blocking wacom.ko from compiling so they made linuxwacom Xserver version aware in version 0.8.6-2.

---

### Post by theartemisg on 2010-07-25
Hopefully this one is simple.
I have Ubuntu 9.04 without much tweaking running on a 2-yr-old iMac.
I plug in my Wacom Intuos 3 graphics tablet,
and it seems to be recognized when plugged in,
but nothing happens when I try to use its pen.
Any idea why?

root@ubunmac:/home/arty# dpkg -l | grep wacom | sed s+'                 '++g
ii  wacom-tools               1:0.8.2.2-0ubuntu2      utilities for Wacom tablet devices
ii  xserver-xorg-input-wacom  1:0.8.2.2-0ubuntu2      X.Org X server -- Wacom input driver
root@ubunmac:/home/arty# xinput -list | grep -i wacom
"Wacom Intuos3 4x6"    id=5    [XExtensionKeyboard]
"Wacom Intuos3 4x6 pad"    id=6    [XExtensionKeyboard]
"Wacom Intuos3 4x6 cursor"    id=7    [XExtensionKeyboard]
"Wacom Intuos3 4x6 eraser"    id=8    [XExtensionKeyboard]

---

### Post by Favux on 2010-07-25
Hi theartemisg,

Welcome to Ubuntu forums!

Let's make sure the usb kernel driver wacom.ko is auto-loading.  Enter in a terminal:
```
lsmod | grep wacom
```

---

### Post by theartemisg on 2010-07-27
Hi [Favux]("http://ubuntuforums.org/member.php?u=699990"),
You hit the nail on the head.
No output from that command, so
I ran insmod on the wacom module,
and now it works!
Thank you very much!!

---

### Post by Gemnoc on 2010-08-07
> **Richard002 said:**
> Wacom tablets tools are really helpful for the artists and photographers in order to carry out their work efficiently. These tools are easy to use as well as modern and stylish in look. Images of any type can be scaled easily with the help of this particular tablet tool.
That totally useless post is a disguised spam. The link in the signature is unrelated to Wacom tablets !

---

### Post by sudopinion on 2010-08-09
My mouse cursor keeps dropping.* This problem plauged my old system with an intuos3 as well. Is there something conflicting with my tablet that would cause this? *during a drag operation the mouse suddenly drops (lets go) of whatever's being dragged. Please help. This is REALLY annoying and renders my tablet nearly useless in linux. Any help is appreciated. [email]sudopinion@yahoo.com[/email]

---

### Post by Nattydread69 on 2010-08-28
Hi All,
 I had my wacom bamboo pen tablet all set up and working fine on Ubuntu 8.10.
Now when I try to use it it doesn't work at all. I'm assuming some update killed it.

I followed all the instructions of the guide to reinstall it including recompiling he latest drivers. But nothing works.

I'd love some help,
thanks

---

### Post by Favux on 2010-08-28
Hi Nattydread69,

Wacom bamboo pen tablet model CTL460?

Did you really mean 8.10 (Intrepid)?  Or is that a typo and you meant 9.10 (Karmic)?  If Karmic, and a kernel update came through, you probably need to reinstall a new wacom.ko.  You might as well update to linuxwacom 0.8.8-8, if you haven't already.  See Section at the [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").

---

### Post by Nattydread69 on 2010-08-29
Hi Favux,
  yes the CTL-F60 and no its not a typo I really mean ubuntu 8.10 Intrepid.
I will try the link you suggested and report back soon...

Thanks!

---

### Post by Nattydread69 on 2010-08-29
Well I successfully completed section 1 of the how-to.
However still no joy with the Bamboo,

Halfway though the second section I get stuck with the building of xf86-input-wacom, I get that 
Requested 'xorg-server >= 1.7.0' but version of xorg-server is 1.5.2

I tried installing xorg-server from source but that seems to lead me to dependecy hell :(

Why is it now so hard to set up the bamboo?
I never had to do all of this the first time grrrr....

---

### Post by Favux on 2010-08-29
Since you are in Intrepid you do not need xf86-input-wacom.  That's the new X driver for Xservers 1.7 and above.

If Section 1, installing linuxwacom 0.8.8-8 ('sudo make install') didn't get the Bamboo working, then it could be a couple of things.

Check to see if the newly compiled wacom.ko is auto-loading:
```
lsmod | grep wacom
```
It should output the module wacom.

Or you don't have the xorg.conf configured.

I don't recognize the model # CTL-F60.  Which Bamboo tablet do you have again?  How new is it/when did it come out?

---

### Post by Nattydread69 on 2010-08-29
Hi Favux,
   Sorry it is the CTL-460 that was a typo this time!

OK so the module seems to be installed

modinfo -n wacom

gives:

/lib/modules/2.6.27-17-generic/kernel/drivers/input/tablet/wacom.ko


lsmod | grep wacom

gives 

wacom                  42624  0 
usbcore               149616  8 usbhid,uv
cvideo,snd_usb_audio,snd_usb_lib,wacom,ehci_hcd,ohci_hcd

my xorg.conf file looks like:

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"fglrx"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/input/wacom" # USB ONLY?
#  Option        "Device"        "/dev/ttyS0"      # SERIAL ONLY
  Option        "Type"          "stylus"
#  Option        "ForceDevice"   "ISDV4"           # Tablet PC ONLY
  Option        "USB"           "on"               # USB ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/input/wacom" # USB ONLY?
#  Option        "Device"        "/dev/ttyS0"      # SERIAL ONLY
  Option        "Type"          "eraser"
#  Option        "ForceDevice"   "ISDV4"           # Tablet PC ONLY
  Option        "USB"           "on"               # USB ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/input/wacom" # USB ONLY?
#  Option        "Device"        "/dev/ttyS0"      # SERIAL ONLY
  Option        "Type"          "cursor"
#  Option        "ForceDevice"   "ISDV4"           # Tablet PC ONLY
  Option        "USB"           "on"               # USB ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "pad"
  Option        "Device"        "/dev/input/wacom"    # USB ONLY
#  Option        "Device"        "/dev/ttyS0"         # SERIAL ONLY
  Option        "Type"          "pad"
  Option        "USB"           "on"                  # USB ONLY
EndSection

# Uncomment the following section if you you have a TabletPC that supports touch
# Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "touch"
#  Option        "Device"        "/dev/ttyS0"       # SERIAL ONLY
#  Option        "Device"        "/dev/input/wacom" # USB ONLY
#  Option        "Type"          "touch"
#  Option        "ForceDevice"   "ISDV4"            # Serial Tablet PC ONLY
#  Option        "USB"           "on"               # USB ONLY
# EndSection

Section "ServerLayout"
  Identifier    "Default Layout"
  Screen        "Default Screen"
  InputDevice   "stylus"  "SendCoreEvents"
  InputDevice   "eraser"  "SendCoreEvents"
  InputDevice   "cursor"  "SendCoreEvents" # For non-LCD tablets only
  InputDevice   "pad"                      # For Intuos3/CintiqV5/Graphire4/Bamboo tablets
# InputDevice   "touch"   "SendCoreEvents" # Only a few TabletPCs support this type
EndSection

---

### Post by Favux on 2010-08-29
That looks like the right wacom.ko.

The xorg.conf should look like:
```
Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
DefaultDepth 24
EndSection

Section "Module"
Load "glx"
EndSection

Section "Device"
Identifier "Configured Video Device"
Driver "fglrx"
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "stylus"
Option "Device" "/dev/input/wacom" # USB ONLY?
Option "Type" "stylus"
Option "USB" "on" # USB ONLY
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "stylus" "SendCoreEvents"
EndSection
```

If you followed the purge routine then the 60-wacom.rules are missing from udev and the wacom symlink won't work.  Did you?

---

### Post by Nattydread69 on 2010-08-29
Hey Favux,
   I corrected my xorg.conf and yes I had done the purge so I reinstalled the xserver-xorg-input-wacom wacom-tools packages and bingo its all working again,

thanks so much for your help :0)

from Natty

:o

---

### Post by Nattydread69 on 2010-08-29
mmm not working quite as it should though,
the cursor seems to freeze when I click the nib (left click)??

---

### Post by Favux on 2010-08-29
You most likely have caused a version conflict now by installing an older version, xserver-xorg-input-wacom & wacom-tools, over 0.8.8-8.  If the tablet is still working then somehow the compiled wacom.ko wasn't installed over.  You have to start over with Section 1 and use the purge routine again.  This time to get the symlink working use the unofficial updated wacom.rules attached to the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1") and follow the instructions in Appendix 3 in the [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").

---

### Post by Nattydread69 on 2010-08-29
I found the page that mentions the pointer freezing and installed the older packages and everything is as it should be.

Thanks for all the help

---

### Post by Favux on 2010-08-29
Hmmm.  What?

---

### Post by Nattydread69 on 2010-08-29
from this page:

> [https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom)

seems I had the bug mentioned too.

> Ubuntu 8.10 (Intrepid Ibex)

With Ubuntu 8.10, the configuration tool wacomcpl comes with the wacom-tools package. However, it won't work in the default setup (Option A), but will works if you have configured your tablet using Option B.

Tablet PC users need to use Option B (for a tentative explanation, see this post or read the whole thread).

Users might also be affected by a bug in the 8.1.4 version of the wacom drivers that comes with Ubuntu 8.10, where the input freeze when the pen touches the tablet. If that is the case for you, you can install updated drivers :

1. Download the updated packages :

    * If you are using an i386 (32bits) Ubuntu 8.10, download these two files :

      wacom-tools_0.8.1.6-1ubuntu2_i386.deb

      xserver-xorg-input-wacom_0.8.1.6-1ubuntu2_i386.deb
    * If you are using an amd64 (64bits) Ubuntu 8.10, download these files instead :

      wacom-tools_0.8.1.6-1ubuntu2_amd64.deb

      xserver-xorg-input-wacom_0.8.1.6-1ubuntu2_amd64.deb

---

### Post by bravebear on 2010-09-12
hi all,
what a wealth of info here!! I am still very confused regarding the changes in 10.04 Lucid. I have a Toshiba R25-3025 tablet with wacom serial thing screen. stylus works somewhat. Gimp shows pressure sensitivity. don't know how to set up the stylus button though. used to have it setup in 8.04, worked flawless. 10.04 is new install and I don't know how to get this to work. any idea how the stylus options/ button get set or how to adjust pressure sensitivity either system wide or in Gimp? pushing the stylus button in a browser window or in gedit pastes the clipboard content. very odd.
the confusing part is that the posts jump back and forth between 10.04 and non-10.04 settings, and it appears that those two are very different in terms of where the config files are and how to write options in them. is this right?

---

### Post by Favux on 2010-09-12
Hi bravebear,

You add this line:
```
      Option            "Button2"        "3"
```
to the serial snippet in 10-wacom.conf, after the driver line.  See Section 3 c) in the [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").  Section 4 has a link to sample xsetwacom scripts to adjust pressure, etc.

---

### Post by odd on 2010-09-12
@bravebear: tell me if it works for you, 'cause changing Pressure Curve on my Lenovo X200 tablet doesn't work - wondering if it's specific hardware or driver issue.

---

### Post by Favux on 2010-09-12
Hi odd,

If it's pressure then maybe the fix for pressure that was included in xf86-input-wacom 0.10.8 is what you need.  The default one in Lucid is 0.10.5.

To update it and the corresponding wacom.ko see I. & II. in the Bamboo P&T HOW TO:  [http://ubuntuforums.org/showpost.php?p=9496609&postcount=1](http://ubuntuforums.org/showpost.php?p=9496609&postcount=1)  or Sections 1 and 2 at the linuxwacom HOW TO:  [http://ubuntuforums.org/showpost.php?p=6546012&postcount=1](http://ubuntuforums.org/showpost.php?p=6546012&postcount=1)

---

### Post by bravebear on 2010-09-12
Thanks Favux. My confusion stems mainly from the change in naming convention from *Section "InputDevice"* in older Ubuntus to *Section "InputClass"* in 10.04 Lucid, and I'm hesitant to work on stuff until I know pretty well what I'm doing and where it's supposed to be going.
In that regard, the **[HOW TO: Install a LinuxWacom Kernel Driver for Tablet PC's]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1")** is great and made it clear to me, did not for some reason come across it before. Thank you for writing that, Favux. Will try it out in the next few days and report on outcome.

---

### Post by Allochtoon on 2010-09-12
For some reason, my intuos4 touchdial stopped working. I use a script to configure the buttons per application. Changing the script bindings doesnt work, all the other buttons work.

[B]These bindings dont work:
[/B]xsetwacom set 'Wacom Intuos4 6x9 pad' AbsWDn  "core key +" 
xsetwacom set 'Wacom Intuos4 6x9 pad' AbsWUp  "core key -" 

```

#script for lefthanded intuos 4 in The Gimp 
#flip to lefthanded mode
xsetwacom set 'Wacom Intuos4 6x9' rotate HALF
xsetwacom set 'Wacom Intuos4 6x9 eraser' rotate HALF
xsetwacom set 'Wacom Intuos4 6x9 cursor' rotate HALF
xsetwacom set 'Wacom Intuos4 6x9 pad' rotate HALF

#touchdial + middle button
xsetwacom set 'Wacom Intuos4 6x9 pad' AbsWDn  "core key +" #clockwise
xsetwacom set 'Wacom Intuos4 6x9 pad' AbsWUp  "core key -" #counterclockwise
xsetwacom set 'Wacom Intuos4 6x9 pad' Button1 "core key 1" #button of touchdial

#button 9 is top button
xsetwacom set 'Wacom Intuos4 6x9 pad' Button9 "core key  CTRL z"
xsetwacom set 'Wacom Intuos4 6x9 pad' Button8 "core key  CTRL y"
xsetwacom set 'Wacom Intuos4 6x9 pad' Button7 "core key ."
xsetwacom set 'Wacom Intuos4 6x9 pad' Button6 "core key ,"
xsetwacom set 'Wacom Intuos4 6x9 pad' Button5 "core key 5"
xsetwacom set 'Wacom Intuos4 6x9 pad' Button4 "core key  SHIFT"
xsetwacom set 'Wacom Intuos4 6x9 pad' Button3 "core key  ALT"
xsetwacom set 'Wacom Intuos4 6x9 pad' Button2 "core key  CTRL" 
#button 2 is bottom button

#'Wacom Intuos4 6x9 eraser'       extension
#'Wacom Intuos4 6x9 cursor'       extension
#'Wacom Intuos4 6x9 pad'          extension
#'Wacom Intuos4 6x9'              extension

```

---

### Post by Favux on 2010-09-13
Hi Allochtoon,

What release of Ubuntu are you use?

---

### Post by Allochtoon on 2010-09-14
> **Favux said:**
> Hi Allochtoon,

What release of Ubuntu are you use?

10.04.1 LTS. 

```

marco@allochtoon:~/SPSS15$ Xorg -version

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux allochtoon 2.6.32-24-generic #42-Ubuntu SMP Fri Aug 20 14:21:58 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=7d09c353-9722-41b8-9c40-4762a0693a8c ro quiet splash
Build Date: 21 July 2010  01:03:39PM
xorg-server 2:1.7.6-2ubuntu7.3 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.

```

my wacom module is 

```

marco@allochtoon:~/SPSS15$ modinfo wacom
filename:       /lib/modules/2.6.32-24-generic/kernel/drivers/input/tablet/wacom.ko
license:        GPL
description:    USB Wacom tablet driver
author:         Vojtech Pavlik <vojtech@ucw.cz>
license:        GPL
description:    USB Wacom tablet driver
author:         Vojtech Pavlik <vojtech@ucw.cz>
srcversion:     3B178A15F89C9B48B641174

```

Hope u can help me out :)

---

### Post by Favux on 2010-09-14
Hi Allochtoon,

First in Xserver 1.7 and up "core" is deprecated.  Just use "key etc.".

Are you using the default wacom.ko (usb kernel driver) and 0.10.5 xf86-input-wacom (the default X driver, wacom_drv.so, for Xserver 1.7 and up) for Lucid?  Or did you update either or both of them?

Also what actions are you trying to get from these commands?

xsetwacom set 'Wacom Intuos4 6x9 pad' AbsWDn "key +"
xsetwacom set 'Wacom Intuos4 6x9 pad' AbsWUp "key -"

---

### Post by KANahas on 2010-09-14
Hmm.  I think I'm stuck.  I've followed all the instructions to get my Wacom tablet (Bamboo Pen; CTL-460) to work, but I'm still getting nothing.  I am able to pull raw data from the tablet by using: ```
:~/linuxwacom-0.8.8-8$ sudo wacdump /dev/input/wacom

```

I have a feeling that there is a problem with how the data gets passed to X.  I'm also pretty sure that when I run xsetwacom or xidump, terminal should not return
```
[xsetwacom/xidump]: error while loading shared libraries: libxcb-xlib.so.0: cannot open shared object file: No such file or directory

```

I am fairly new to Ubuntu, and any help would be greatly appreciated. :)

BTW, I am running Ubuntu 10.04, kernel 2.6.32-24, and xorg-server 2:1.7.6-2ubuntu7.36 .


--KAN  :D

---

### Post by Favux on 2010-09-15
Hi KAN,

Welcome to Ubuntu forums!

I'm going to guess you've just compiled linuxwacom 0.8.8-8 and not xf86-input-wacom.  Please see the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1").

---

### Post by KANahas on 2010-09-15
Thank you for the warm welcome!  Well, I recompiled xf86-input-wacom.  Unfortunately, xsetwacom and xidump still do not work. :(  However, on the much more important side of things, my Bamboo Pen now works! :D  And that's what matters right? :P  Thank you very much, Favux!


--KAN  :D

---

### Post by Allochtoon on 2010-09-15
> **Favux said:**
> Hi Allochtoon,

First in Xserver 1.7 and up "core" is deprecated.  Just use "key etc.".

Are you using the default wacom.ko (usb kernel driver) and 0.10.5 xf86-input-wacom (the default X driver, wacom_drv.so, for Xserver 1.7 and up) for Lucid?  Or did you update either or both of them?

Also what actions are you trying to get from these commands?

xsetwacom set 'Wacom Intuos4 6x9 pad' AbsWDn "key +"
xsetwacom set 'Wacom Intuos4 6x9 pad' AbsWUp "key -"

[LIST]
I removed the 'core' from the command lines.
[/list]

[list] Since noting the problem with my touchdial (see last comment) i updated xf86-input-wacom to:
[http://sourceforge.net/projects/linuxwacom/files/xf86-input-wacom/xf86-input-wacom-0.10.8.tar.bz2/download](http://sourceforge.net/projects/linuxwacom/files/xf86-input-wacom/xf86-input-wacom-0.10.8.tar.bz2/download)

i removed the package xserver-xorg-input-wacom from the package manager.

i tried updating the usbkernel driver but got warned it didn't support xorg 1.7??:

```
Your wacom.ko is available under 
    /home/marco/Downloads/linuxwacom-0.8.8-8/src/2.6.30


NOTE: this package only supports Xorg server older than 1.7.
          You are running a newer version. 
Please build the X driver from xf86-input-wacom.

```
so i didnt install this module for testing. upon reboot i did install it. nothing changed except my script commands stopped working.

**IN SHORT** 
Wacom input is registered (be it flipped since i am lefthanded), pressing any button now puts the cursor to lefttop screen position but doesnt translate into a command. 

After updating both packages to the newest version when running my script i get these errors:
```
Property 'Wacom Rotation' does not exist on device.
Cannot find device 'Wacom Intuos4 6x9 eraser'.
Cannot find device 'Wacom Intuos4 6x9 cursor'.
Cannot find device 'Wacom Intuos4 6x9 pad'.
```

The biggest problem now however, is since i am lefthanded, i need to rotate the wacom input, nor does any button work now.
[/list]

[list]
with these commands:

```
xsetwacom set 'Wacom Intuos4 6x9 pad' AbsWDn "key +"
xsetwacom set 'Wacom Intuos4 6x9 pad' AbsWUp "key -"
```

I am trying to zoom in/out in Gimp, MyPaint etc with the touchdial; its a donut shaped ring which responds to your touch. This did work before. Everything else seems to work as before. Only the touchdial refused to work. Now i need to flip the orientation of the pad and programming of the buttons. I read about other methods before?
[/list]

Am i using a deprecated method?

BTW im using 64bit 10.04.1

your help is much appreciated :)

---

### Post by Favux on 2010-09-15
Hi KAN,

Good it works, progress!  Xidump and wacdump are not included with xf86-input-wacom and neither is wacomcpl.  However xsetwacom should work, it was rewritten for xf86-input-wacom.  The xsetwacom commands no longer work with the old Wacom device names like stylus, eraser, etc.  Instead they use the new longer more "descriptive" device names.  Enter in a terminal:
```
xinput --list
```
The output should contain the new "Device names" for stylus, etc.  Just substitute them in, with the quotes, in the xsetwacom commands.


Hi Allochtoon,

The warning:
> NOTE: this package only supports Xorg server older than 1.7.
          You are running a newer version. 
Please build the X driver from xf86-input-wacom.
is telling you not to use the X driver wacom_drv.so from linuxwacom on Xserver 1.7 or higher.  It won't work.  Instead you are suppose to use the wacom_drv.so from xf86-input-wacom which does work on Xserver's 1.7 and higher.  So with linuxwacom after a compile you don't do a 'sudo make install' after the 'make'.  However linuxwacom's usb kernel driver (wacom.ko) is needed and does work.  It's telling you where it is located after the compile so you can copy it into your kernel's modules directory.

I'm not quite sure from what you're saying what you did.  Did you install the newly compiled 0.8.8-8 linuxwacom wacom.ko?  If you removed xserver-xorg-input-wacom you no longer have the xf86-input-wacom X driver wacom_drv.so.  Did you then compile xf86-input-wacom by cloning the git repository?  If so you run into another problem, there is a new dependency and removing xserver-xorg-input-wacom removes xserver-xorg-input-all, and vice versa.  Which is needed.  So you need to reinstall xserver-xorg-input-wacom which will bring xserver-xorg-input-all along.  Then clone the xf86-input-wacom repository over your xserver-xorg-input-wacom.  That will get you the needed updated wacom_drv.so.

Follow?

---

### Post by Allochtoon on 2010-09-15
> **Favux said:**
> Hi KAN,

Good it works, progress!  Xidump and wacdump are not included with xf86-input-wacom and neither is wacomcpl.  However xsetwacom should work, it was rewritten for xf86-input-wacom.  The xsetwacom commands no longer work with the old Wacom device names like stylus, eraser, etc.  Instead they use the new longer more "descriptive" device names.  Enter in a terminal:
```
xinput --list
```
The output should contain the new "Device names" for stylus, etc.  Just substitute them in, with the quotes, in the xsetwacom commands.


Hi Allochtoon,

The warning:

is telling you not to use the X driver wacom_drv.so from linuxwacom on Xserver 1.7 or higher.  It won't work.  Instead you are suppose to use the wacom_drv.so from xf86-input-wacom which does work on Xserver's 1.7 and higher.  So with linuxwacom after a compile you don't do a 'sudo make install' after the 'make'.  However linuxwacom's usb kernel driver (wacom.ko) is needed and does work.  It's telling you where it is located after the compile so you can copy it into your kernel's modules directory.

I'm not quite sure from what you're saying what you did.  Did you install the newly compiled 0.8.8-8 linuxwacom wacom.ko?  If you removed xserver-xorg-input-wacom you no longer have the xf86-input-wacom X driver wacom_drv.so.  Did you then compile xf86-input-wacom by cloning the git repository?  If so you run into another problem, there is a new dependency and removing xserver-xorg-input-wacom removes xserver-xorg-input-all, and vice versa.  Which is needed.  So you need to reinstall xserver-xorg-input-wacom which will bring xserver-xorg-input-all along.  Then clone the xf86-input-wacom repository over your xserver-xorg-input-wacom.  That will get you the needed updated wacom_drv.so.

Follow?

i installed linuxwacom's usb kernel driver (wacom.ko)
```
marco@allochtoon:~/Downloads/linuxwacom-0.8.8-8$ sudo cp src/2.6.30/wacom.ko /lib/modules/2.6.32-24-generic/kernel/drivers/input/tablet/
```

installed: xserver-xorg-input-wacom
  xserver-xorg-input-all

latest git build of xf86-input-wacom compiles after installing xorg-macros 1.8.

rebooting now, should i continue using xsetwacom?

---

### Post by Favux on 2010-09-15
Looks good.  The xsetwacom commands should work for you now.

---

### Post by Allochtoon on 2010-09-15
> **Favux said:**
> Looks good.  The xsetwacom commands should work for you now.
thanks so much for your help favux it works now :)

---

### Post by jmexia on 2010-09-22
Hi All,

I have a Thinkpad X60 tablet.  The good news is that the stylus works OTB; however, I'm having issues recalibrating the stylus once I rotate my screen.  Because wacomcpl is no longer in Lucid, I can't figure out how to do it.  I apologize if this was already covered earlier in this thread.

Thanks,
J.

---

### Post by Favux on 2010-09-22
Hi J.,

Do you actually mean calibrating or do you mean the stylus doesn't rotate?

---

### Post by jmexia on 2010-09-22
Maybe I do mean the stylus does not rotate.

Thanks for the quick reply...J.

---

### Post by Favux on 2010-09-22
Alright, some rotation methods are at the [Rotation HOW TO]("http://ubuntuforums.org/showpost.php?p=6274392&postcount=1").  A method 1 script or method 3 should work for you.

As far as calibration, that should happen automatically when you rotate.  But you do need to be calibrated in one orientation (usu. landscape).  If that's a problem do you have an old .xinitrc from wacomcpl that shows your calibration?

---

### Post by jmexia on 2010-09-22
Thanks, Favux...I will give the scripts a try...I'm sure I can track down a copy of my xintrc file if need be.  Man, you're fast!!  Thanks again...

J.

---

### Post by jlbrewer on 2010-10-21
Hi,

I'm running 3 monitors under ATI Catalyst (if that matters) under Maverick with n Intuos4.  I've tried the "ScreenNo" and "MMonitor" options in the config file to lock the stylus to the center screen and haven't seen any results.  I know X is reading the config file because when I tried the "twinview" option, the cursor got locked to one side of the screen.  Any pointers?

---

### Post by oobu on 2010-11-07
hi,

I am on Karmic Koala  - 9.10. Just got a new Bamboo 'Pen and  Touch' (CTH460). I was hoping for plug-and-play support in Ubuntu :) but stuck right now.

I am not sure what I should do to have it working; I know about these sources:

[**HOW TO:  Install a LinuxWacom Kernel Driver for Tablet PC's**]("http://ubuntuforums.org/showthread.php?t=1038949")
                                  [URL="http://ubuntuforums.org/showthread.php?p=9496609#post9496609"]**HOW TO Set Up the Bamboo Pen & Touch in Lucid**** & Maverick and Other Wacom Tablets**.
[/URL]
and
the Ubuntu [community documentation]("https://help.ubuntu.com/community/Wacom").

All I have done so far is this:
> sudo apt-get install xserver-xorg-input-wacom wacom-toolsWhat do I have to do next? Follow the directions in the first howto or the second one or something else entirely, which is suited for Karmic Koala?

thanks,

---

### Post by Favux on 2010-11-07
Hi oobu,

Welcome to Ubuntu forums!

For Karmic follow the first HOW TO to compile linuxwacom paying attention to the directions for Karmic.  I'm thinking step 3 b) about the hid-ids is no longer needed.  I think the Ubuntu dev.s fixed it.  If so you'd just do step 3 a) like everyone else.  Let me know if I'm right.

You probably want to remove wacom-tools first though.  Compiling linuxwacom will get you the latest version of wacom tools and will include wacomcpl.

You don't need xf86-input-wacom with Karmic.

---

### Post by thorwil on 2010-11-09
In case anyone else has a serial Wacom tablet and wants to get it to work on 10.10:

The patch mentioned earlier here does not work with the xf86-input-wacom version in 10.10, but you can patch, build and use xf86-input-wacom-0.10.6, if you additionally apply the patch found on [http://www.mail-archive.com/linuxwacom-devel@lists.sourceforge.net/msg01079.html](http://www.mail-archive.com/linuxwacom-devel@lists.sourceforge.net/msg01079.html)

---

### Post by Favux on 2010-11-09
Hi thorwil,

Wow!  Nice work.

So xf86-input-wacom 0.10.6 with the serial tablet patch wouldn't work with Maverick's Xserver 1.9 until you used the additional patch?  Is that correct?

---

### Post by thorwil on 2010-11-09
Yes, corect. To be precise, xf86-input-wacom 0.10.6 does not build without the additional patch.

---

### Post by Favux on 2010-11-09
Thank you.  I'll add your work to the [HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").

---

### Post by riesengreen on 2010-11-27
Hi all:

And thanks for work on making tablets usable in Ubuntu! 

I am a 95% GUI-only user, and have been working on setting up my Bluetooth Graphire tablet for a couple of years (not kidding!).

After months and months of trying and failing, I am closer than ever! 

Progress so far:

1) installed updated bluez packages from the PPA below:
htps://launchpad.net/~yobbobandana/+archive/ppa
   >Bluetooth seems to be working. The tablet has been recognized and set up. I do not think that the Bluetooth connection is a problem.

2) edited xorg.conf
   >As in [Community Documentation]("https://help.ubuntu.com/community/Wacom"), under "Ubuntu 10.04 (Lucid Lynx): Method 1"

3) installed the package xserver-xorg-input-wacom using Synaptic Package Manager
   >Again, as in [Community Documentation]("https://help.ubuntu.com/community/Wacom")

Things were very promising up to step 3, when I attempted to install the second of the two necessary packages, wacom-tools.

I could not install the package, and the error message below was displayed:

[IMG]http://flic.kr/p/8WE7Qm[/IMG]

Error message read as follows:

Could not mark all packages for installation or upgrade
The following packages have unresolvable dependencies. Make sure that all required repositories are added and enabled in the preferences.

wacom-tools:

Package wacom-tools has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list
-

What do I need to do to install the wacom-tools package? If I need to add a software repository in Software Sources, I have been unable to determine which I need to add.

Any help is appreciated. Many thanks.

BMR

---

### Post by Favux on 2010-11-27
Hi riesengreen,

wacom-tools is no longer available starting with Lucid (X server 1.7 and up).  This is because the X driver for Wacom tablets was taken over by Xorg.  So it's now Xorg's xf86-input-wacom, not linuxwacom's, X driver wacom_drv.so.  The xserver-xorg-input-wacom package now contains different stuff in other words.  And the Xorg folks dropped several tools that linuxwacom had like wacomcpl, xidump, and wacdump.

It sounds like you have the tablet working.  I'm not sure you had to use the xorg.conf.  Could I see it?  I think maybe the wacom.conf in xorg.conf.d would have worked for you.

Good work on installing the ppa and getting the tablet working.  Sounds like your linux skills have progressed.  What did you need wacom-tools for?  It's not clear to me from your post.

By the way the Bluez patch for Maverick isn't available so don't try to upgrade to Maverick.

---

### Post by maarts on 2010-11-29
Hi,

thanks for this good howto!

I use an Intuos 4 (PTK-840) under Ubuntu 10.10 (xf86-input-wacom-0.10.8 ) and I set the keys with xsetwacom:

```

xsetwacom set "Wacom Intuos4 8x13 pad" Button9 "key Esc"

```And all keys works fine, but the "Esc" Key doesn't work.

```

xxx@xxx:~$ xsetwacom list mod
....
43 specialkeys are supported:
  ....
    f32
    f33
    f34
    f35
    esc
    Esc
    up
    down
    left
    right
    backspace
    Backspace

```Hm, and "xsetwacom list mod" view the supported keys...

How can I fix this problem?

thanks
maarts

---

### Post by Favux on 2010-11-29
Hi maarts,

Hmmm.  That should work.  It's in the 0.10.8 xsetwacom.c:
```
	{"esc", "Escape"}, {"Esc", "Escape"},
```
Have you tried it on another button?  Maybe there's a problem with 9.

By the way you can get the OLED's to work.

---

### Post by maarts on 2010-11-29
Hi Favux,

thanks for your replay!

I have tried it on another button, but it's the same problem. What can I do?

Yes, the OLED's work. Here my inspiration:

[http://ubuntuforums.org/showthread.php?p=9888901#post9888901](http://ubuntuforums.org/showthread.php?p=9888901#post9888901)

thanks
maarts

---

### Post by Favux on 2010-11-29
When you run the escape key command in a terminal do you get an error message?  What is it?

If you're interested sanette posted a slightly updated version of his take on Karg's OLED support (profiles) a few posts later.

---

### Post by maarts on 2010-11-30
Hi Favux,

there is no error message.

OK, I use xev and the ESC-Key on my keybord send the keycode 9, but the tablet send 8!! All the other keys from the tablet send correct keycodes.

My xmodmap:

```

! Converted keytable file to xmodmap file
! with mk_modmap by root@chanae.alphanet.ch vie nov 27 02:12:00 CET 1998
clear Mod1
clear Mod2
!  de-latin1.map: German keymap
!  Some changes due to Olaf Flebbe (flebbe@pluto.tat.physik.uni-tuebingen.de)
keycode   9 = Escape Escape
keycode  10 = 1 exclam
keycode  11 = 2 quotedbl twosuperior
keycode  12 = 3 section threesuperior
keycode  13 = 4 dollar dollar
keycode  14 = 5 percent
keycode  15 = 6 ampersand
keycode  16 = 7 slash braceleft
...

```

There is no keycode "8"?? What can I do?

Thanks
maarts

---

### Post by Favux on 2010-11-30
Hi maarts,

So if the Button in the 4-function touch control ring is Button1 the eighth express key is Button9.

Looking at xf86-input-wacom-0.10.8/tools/xsetwacom.c, xsetwacom seems to be set up to handle up to 32 buttons (1-32).  So that doesn't seem to be the problem.

Does Button9 work with anything else such as "key ctrl z"?  Is it only "key Esc" that doesn't work?  Does it work in Windows?

If it's not working in Linux you have to wonder if somewhere in the driver code it's being limited to 8 buttons.  Confusion over the fact there are 9 buttons but only 8 express keys somewhere?

---

### Post by maarts on 2010-11-30
Hi Favux,

> 
Does Button9 work with anything else such as "key ctrl z"?  Is it only "key Esc" that doesn't work?  Does it work in Windows?


If I set Button9 with the key: "key ctrl", it works. It is only "key Esc" that doesn't work on all the buttons! I don't have Windows.

Hm... any idea?

thanks
maarts

---

### Post by Favux on 2010-11-30
It's sounding more and more like a bug somewhere.

Could you move Esc to Button8 and what's on Button8 to Button9?  Does that work?  Or is that no good with your work flow?

---

### Post by maarts on 2010-11-30
Hi Favux,

I tried it on Button8, 7 and 6, but it didn't work. I think that's a bug. Can I update the xf86-input-wacom to 0.10.xx or is it another problem?

thanks
maarts

---

### Post by Favux on 2010-11-30
That was going to be my next suggestion.  There've been a lot of fixes since 0.10.8.

You'll want to clone the xf86-input-wacom git repository.  See the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1") step II. or the [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1") section 2.

---

### Post by maarts on 2010-11-30
Hi Favux,

I have update to 0.10.10, but there is the same problem...

??? :cry:

thanks
maart

---

### Post by Favux on 2010-11-30
I hope you mean 0.10.10+.  In other words you cloned it.  There's a known bug for tablet keys in the 0.10-9 snf 0.10-10 tars.  That was fixed a few patches later.

If so time to file a bug report.  You can either do that at linuxwacom-discuss:  [https://lists.sourceforge.net/lists/listinfo/linuxwacom-discuss](https://lists.sourceforge.net/lists/listinfo/linuxwacom-discuss)  or through their bug tracker:  [http://sourceforge.net/tracker/?group_id=69596&atid=525124](http://sourceforge.net/tracker/?group_id=69596&atid=525124)

---

### Post by maarts on 2010-12-01
Hi Favux,

yes, I cloned it.

The problem is in the xsetwacom.c or in XStringToKeysym. I will check the problem ...

I solved the problem temporary with the .Xmodmap (keycode   8 = Escape).

thanks
maarts

---

### Post by maarts on 2010-12-01
Hi Favux,

the problem is in keysym_to_keycode... The keysym is correct.

???

thanks
maarts

---

### Post by riesengreen on 2010-12-03
Hi

Thank you for your reply Favux! You wrote:

"It sounds like you have the tablet working. I'm not sure you had to use the xorg.conf. Could I see it? I think maybe the wacom.conf in xorg.conf.d would have worked for you."

I have copied and pasted my modified xorg.conf file for you below:

Section "InputClass"
	Identifier "Wacom class"
	MatchProduct "Wacom|WACOM"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
	#Option "Button2" "2"
        #Option "Button3" "3"
        Option "KeepShape" "on"
EndSection

Section "InputClass"
	Identifier "Wacom serial class"
	MatchProduct "Serial Wacom Tablet"
	Driver "wacom"
	Option "ForceDevice" "ISDV4"
EndSection

# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
	Identifier "Wacom N-Trig class"
	MatchProduct "HID 1b96:0001"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
EndSection

--

---

### Post by Favux on 2010-12-08
Hi riesengreen,

Sorry for the delayed response.  Lost track of your post.

Does your blue tooth Intuos3 hot plug with the xorg.conf?  If not you should be able to use the 10-wacom.conf I think.  At most we should only have to find a match line or two, with luck.

If you're going to use the xorg.conf and the match lines in the 10-wacom.conf are working you should disable them by commenting them out.  You don't want both active.

---

### Post by maarts on 2010-12-08
Hi,

I changed from Ubuntu 10.10 to 10.04 and I clone the xf86-input-wacom 0.10.10+. Now I can use only the half screen and half tablet (left side). Under 10.10 it works fine. I have a Intous ptk-840.

What is the problem?

thanks
maarts

EDIT: After restart it worked!

---

### Post by Favux on 2010-12-08
Good!  So you have everything worked out now?

---

### Post by maarts on 2010-12-08
Hi Favux,

no, it doesn't work!

I just updated from xf86-input-wacom 0.10.5 to 0.10.10+ (clone). With the 0.10.5 I can use the full screen, but the buttons did not work. After the update the buttons work, but I can use only the half screen and tablet.

xsetwacom get xxx BottomX --> 65024
xsetwacom get xxx BottomY --> 40640

What can I do?

thanks
maarts

---

### Post by Favux on 2010-12-08
Hi maarts,

Do you have more than one monitor?  That's what it sounds like.  The tablet is running split between the two.  They removed all the multi-monitor support stuff.

Except there is a new xsetwacom command.  I haven't used it before.  Let's see if we can figure it out:
```
xsetwacom set <device name> "MapToOutput" VGA1
```
This only applies once, so if you change output you have to rerun it.

---

### Post by maarts on 2010-12-08
Hi Favux,

thanks for your replay!

I have an external monitor and the LCD form the notebook. In this case I use only the external monitor. Xrandr give me the correct output, but the command show this:

"Server does not support transformation"

hm, if I tried only the notebook with the tablet, it is the same problem.

thanks
maarts

---

### Post by Favux on 2010-12-08
Tablet is plugged into laptop and laptop plugged into monitor?

Try disabling whatever you're using to output laptop display to monitor.  Let's see if it maps to the laptop lcd first.  Also do you know the name your display configuration is using for the laptop lcd and the name it is using for your external monitor?

---

### Post by maarts on 2010-12-08
Hi Favux,

1. yes.
2. the output from xrandr, only laptop:

```

Screen 0: minimum 320 x 200, current 1400 x 1050, maximum 8192 x 8192
VGA1 disconnected (normal left inverted right x axis y axis)
LVDS1 connected 1400x1050+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1400x1050      60.0*+   85.0     74.8     70.0     60.0  
   1280x1024      85.0     75.0     60.0  
   1280x960       85.0     60.0  
   1360x768       59.8  
   1152x864      100.0     85.1     85.0     75.0     75.0     70.0     60.0  
   1024x768       85.0     75.0     70.1     60.0  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  
DVI1 disconnected (normal left inverted right x axis y axis)
TV1 disconnected (normal left inverted right x axis y axis)

```

LVDS1 == laptop
VGA1 == monitor

laptop + tablet --> same problem

thanks
maarts

---

### Post by Favux on 2010-12-08
OK, I just checked and you haven't posted the output of 'xinput --list' so I don't know what your "Device names" are.

Try something like:
```
xsetwacom set <stylus> "MapToOutput" LVDS1
xsetwacom set <eraser> "MapToOutput" LVDS1
```
using the device name in quotes that xinput gives you for stylus or eraser.

---

### Post by kingpinzs on 2010-12-08
So I have installed ubuntu netbook and desktop verstions 10.10 on my compaq tc1000 tablet but non of them work with the touchpad and I cant get the linuxwacom driver to work. Any ideas?

---

### Post by Favux on 2010-12-09
Hi kingpinzs,

You're on the wrong thread.  The Compaq/HP TC1000 has the Fujitsu Finepoint digitizer, not Wacom.  You need the fpit driver.  See:  [http://ubuntuforums.org/showthread.php?t=1325644](http://ubuntuforums.org/showthread.php?t=1325644)

Either post on that thread or start your own, since that one is for Karmic not Maverick.  Check in Synaptic Package Manager that fpit is installed.

I think I helped someone with another type of tablet pc that also uses the fpit driver set up on Maverick a few weeks ago.  We may have used a fpit driver from a ppa.  Can't remember quite how we configured it.  I think through the xorg.conf.  Let me see if I can find that thread.

---

### Post by maarts on 2010-12-09
Hi Favux,

the device list from 'xinput --list':

```

...
Wacom Intuos4 8x13 eraser                   id=20    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos4 8x13 cursor                   id=21    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos4 8x13 pad                      id=22    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos4 8x13 stylus                   id=23    [slave  pointer  (2)]
...

```and

```

xsetwacom set "Wacom Intuos4 8x13 stylus" "MapToOutput" LVDS1
xsetwacom set "Wacom Intuos4 8x13 eraser" "MapToOutput" LVDS1

```But it is the same problem:

"Server does not support transformation"

What can I do?

thanks
maarts

---

### Post by maarts on 2010-12-09
Hi Favux,

I installed the xf86-input-wacom 0.10.8 from here:

[http://sourceforge.net/projects/linuxwacom/files/xf86-input-wacom/](http://sourceforge.net/projects/linuxwacom/files/xf86-input-wacom/)

and it worked fine.

I think it is a bug, but I don't have time to figure out the problem...

thanks
maarts

---

### Post by no.human.being on 2010-12-09
This is the method I used for Wacom tablet support. It does not require intervention with your X server. The installation of a third-party kernel module will be sufficient.

Just download the latest tarball from [here]("http://linuxwacom.sourceforge.net/index.php/dl"). Now open a shell, go to the place where you downloaded the tarball and do the following.

First, extract the tarball.

```

tar xvf linuxwacom-0.8.8-10.tar.bz2

```Of course if your tarball has a different version, enter the version number you downloaded. Now go into the extracted directory.

```

cd linuxwacom-0.8.8-10

```

Now run the following commands. The last command will require root permission.

```

./configure --enable-wacom
make
sudo make install

```

Now go into the "src" directory and have a look at the directories inside.

```

cd src
ls

```

Go into the latest "version directory" (currently that's "2.6.30") and view the directory listing.

```

cd 2.6.30
ls

```

There should be a file named "wacom.ko". Now, look where your "wacom.ko" is located.

```

locate wacom.ko

```

This might show several paths. Take the one with the latest kernel version and the file name "wacom.ko" at the end. Remember that path (without the "wacom.ko" at the end). In my case the path was "/lib/modules/2.6.35-23-generic/kernel/drivers/input/tablet". Your path may be different.

Now copy the "wacom.ko" file, that you have just built from source, into that path. Remember that your path may be different. Substitute with your path in this case. This will require root permission. Note that this is a dangerous operation and might cause your system not to boot. You might want to backup your old "wacom.ko" for recovery purposes.

```

sudo cp wacom.ko /lib/modules/2.6.35-23-generic/kernel/drivers/input/tablet

```

Now change into that path. Again, substitute if you have a different path.

```

cd /lib/modules/2.6.35-23-generic/kernel/drivers/input/tablet

```

Now load that kernel module. This will require root permission.

```

sudo modprobe wacom

```

Now the manual copying of the "wacom.ko" may not be the proper way of doing it (is it possible to use "insmod" instead?!), but it worked fine in my case. If you install a kernel update, your computer will no longer accept input from the tablet. In this case, you will have to repeat this procedure. Afterwards, your tablet will be functional again.

---

### Post by Favux on 2010-12-09
Hi maarts,

Nice job!  A shame you had to downgrade to the 0.10.8 tar though.  You miss a lot of fixes by going back to 0.10.8.  But it does look like you have discovered a bug.

I was going to say try disabling whatever is giving you the:
> VGA1 disconnected (normal left inverted right x axis y axis)

line, probably your video card configuration utility.  And then see if it maps correctly.  But since it works with 0.10.8 it seems likely it's due to a bug and this would have been a dead end.

I'm wondering if a bug has been introduced by the Xorg developer of xf86-input-wacom? Trying to do a transform using some upstream X server stuff that isn't in the current servers?  Did that while removing all the multi-monitor support for the driver lately?  Or just accidentally broke something?


Hi no.human.being,

Most setups require another flag on the configure line:
```
./configure --enable-wacom --prefix=/usr
```
and you probably want:
```
sudo depmod -a
```
before your modprobe line.  I assume you're installing on a release prior to Lucid or using an Xserver older than 1.7.

---

### Post by no.human.being on 2010-12-09
> **Favux said:**
> Hi no.human.being,

Most setups require another flag on the configure line:
```
./configure --enable-wacom --prefix=/usr
```and you probably want:
```
sudo depmod -a
```before your modprobe line.  I assume you're installing on a release prior to Lucid or using an Xserver older than 1.7.

No. This was on Ubuntu 10.10 with a 2.6.35-23-generic kernel.

---

### Post by Favux on 2010-12-09
Alright, then you do not need:
```
sudo make install
```
The linuxwacom X driver wacom_drv.so will not install on Xservers 1.7 or higher.  Since you are copying the compiled wacom.ko into place you are likely correct and you do not need the extra flag.

---

### Post by no.human.being on 2010-12-09
> **Favux said:**
> The linuxwacom X driver wacom_drv.so will not install on Xservers 1.7 or higher.  Since you are copying the compiled wacom.ko into place you are likely correct and you do not need the extra flag.

I'm having X.Org 1.9.0 installed. There is no need for an X driver. Just build and load the kernel module and you should be able to use the tablet as a pointing device (pressure sensitivity inside GIMP is also working).

---

### Post by Favux on 2010-12-09
Well xf86-input-wacom 0.10.8 is installed by default in Maverick.  That has Xorg's version of the wacom X driver and works on 1.7 and above.  It's in the xserver-xorg-input-wacom package.  Confusing because that's what linuxwacom was called pre-Lucid.

---

### Post by no.human.being on 2010-12-09
Why are they installing the X driver by default, but not the kernel driver? Also, what's inside the "wacom.ko" file, that's already coming with Ubuntu 10.10 when it's not a (functioning) tablet driver?

---

### Post by fillchiam on 2010-12-09
Hi, I've been having some problems since I upgraded to Maverick. I've got a Wacom Intuos4 M, and two screens (one laptop screen, 1680x1050px, and one Dell U2311H via HDMI to a HDMI switch, and then a HDMI-DVI adapter to the monitor, 1920x1080px) running in TwinView mode (my graphics card is a nVidia GeForce 8600M GT). I used to use
```
xsetwacom set "Wacom Intuos4 6x9 stylus" TwinView "horizontal"
```
to get it working properly with both screens on Lucid, but with Maverick that doesn't work, so the aspect ratio gets all messed up.
I wanted to try using MapToOutput, but when I checked xrandr I got this:
```
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 3600 x 1080, current 3600 x 1080, maximum 3600 x 1080
default connected 3600x1080+0+0 0mm x 0mm
   3600x1080      50.0* 
```

Apparently, it treats both monitors as one monitor (which I noticed when I tried to do screen resolution adjustments in games before, now that I think about it), and I am at a complete loss as for what to do.

Any ideas? :(

---

### Post by Favux on 2010-12-09
Hi no.human.being and fillchiam,

Linuxwacom used to contain the kernel and the X driver (actually it still does).  Not everyone was a fan because the X driver is suppose to be Xorg's.  So an agreement was reached and Xorg took over the X driver (xf86-input-wacom) starting with Xserver 1.7 (Lucid).  Meanwhile linuxwacom keeps the kernel driver and the legacy X driver.  Linuxwacom has a lot of big legacy clients.

Xorg's priority is to streamline the code to make maintaining it easier.  Wacom is by far the most complicated input driver.  This means a lot of user features have been eliminated because technically they don't belong in a driver.  That includes wacomcpl (wacom control panel), wacdump, xidump, and most recently the last of the multi-monitor support.

In the meantime the multitouch code linuxwacom came up with to support the new Wacom 2 finger touch devices turned into a problem.  The kernel came up with a new MT specification and the original linuxwacom version was noncompliant.  So linuxwacom has been updating their wacom.ko all along but the kernel stopped accepting them.  So Lucid has the 0.8.4-1 wacom.ko and Maverick has the 0.8.4-4 wacom.ko.  New MT code has been accepted for the 2.6.37 kernel.  So hopefully all fixed in Natty.

So to answer your question no.human.being there is a default wacom.ko with Maverick.  Unfortunately a bunch of new Wacom models are not in the default wacom.ko.  Which is why you have to compile a newer version.  And this will always be true for any model less than about 6 months old anyway.

fillchiam I gather there is suppose to be a way to do it.  We'll have to figure out what it is.  Since I've never set up a multi-monitor setup I haven't paid that much attention.  For brief periods I had it down, especially with nVidia cards.  Part of the problem is it was always changing anyway.

Since we know the monitors resolution together is seen as 3600x1080 let's see what happens if we treat it like it is one monitor.  So what monitor do you want to map to?  Laptop or external?  We could try mapping, if you wanted the tablet on the laptop, topx and y 0 and bottom X 1050 and bottom Y 1680, and vice versa if you wanted it the other way, and see if that does anything.

---

### Post by dsavi on 2010-12-24
I'm having a similar problem with mapping my Wacom Bamboo Fun Medium to a single 20" monitor, of course the twinview option is gone. Found something interesting while googling it yesterday:
[http://old.nabble.com/-ANNOUNCE--xf86-input-wacom-0.10.9-p30254032.html](http://old.nabble.com/-ANNOUNCE--xf86-input-wacom-0.10.9-p30254032.html)
> First of all: this release does not have TwinView support anymore. 
Users running X Servers 1.9 or later have a property in the X server that 
provides the same functionality (mapping the tablet to any section of the 
screen). Users of servers 1.8 are advised not to update if they require the 
TwinView functionality. 
That's all well and good, but I have no idea how to map it. My guess is that I'm going to start editing my xorg.conf. I have another problem too however.

The driver doesn't seem to be using enough data from my tablet, the lines aren't smooth if I draw quickly, like this:
[IMG]http://img17.imageshack.us/img17/6183/tabletwhat.png[/IMG]

Help would be appreciated. It's been a long time since I had so many problems with drivers on Linux. :|

---

### Post by Jarvo on 2010-12-24
Dear All
Newbie here so sorry if this is the wrong part of the forum to say this, I have Ubuntu 10.10 and a Wacom ET tablet.  It works well in WINE photo-shop 6 for both stylus/pressure and eraser  It works well with pressure not eraser in GIMP, However the mouse only scrolls  downwards (annoying) and the eraser doesn't work in GIMP. I tried making  fixes ,downloaded wacom control panel, I don't have wacom tools config  and I don't have a  clue how terminal really works. i just dumbly paste text that I read on the 'how to' forums. Is there a fix foe the mouse scroll bug? I don't want o undo the good settings I already have. I am getting round it by using a  regular mouse on the pad and swapping over to the stylus when I need to use it but it takes up a usb port

---

### Post by Favux on 2010-12-24
Hi Jarvo,

Wecome to Ubuntu forums!

Hi dsavi,

It looks like you are both on Maverick (10.10).  In which case you both would probably benefit from getting the latest version of the xf86-input-wacom by cloning its git repository.  There was a recent fix for scroll wheels and Bamboo P&T filtering logic, among other things.  I don't know for sure if it applies to the Wacom mouse but it's worth a try.

See II. in the [Bamboo P & T HOW TO]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1") or Section 2 in the [Wacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").

As I mentioned earlier there's suppose to be a new xsetwacom command (if your xf86-input-wacom is up to date enough) in the form of:
```
xsetwacom set <device name> "MapToOutput" VGA1
```
Which is suppose to only apply once, so if you change output you have to rerun it. We haven't figured out how to use it yet. So far trying to run it we get the error:
> "Server does not support transformation"
dsavi if you see the same error then I should file a bug report to LWP.

---

### Post by Jarvo on 2010-12-24
Fantastic the wacom graphire 2 now works perfectly. i followed section 1 of the link you gave me and it fell over at section 2.  I failed at this point cd ./Desktop tar xjvf util-macros-1.8.0.tar.bz when it said no such file or directory. But when I rebooted it works perfectly. Yipee , I am not to bothered if I only loaded 1/2 the code as long as it works.
Thanks Jarvo

---

### Post by dsavi on 2010-12-27
Thanks for your help again Favux. Updating to the development versions of xf86-input-wacom and input-wacom-0.10.10 (The new linuxwacom) fixed the worse problem (Non-smooth strokes), but I can't seem to get twinview to work, even with MapToOutput. This is probably because [FONT="Courier New"]xrandr -q[/FONT] doesn't display devices with which I can do [FONT="Courier New"]xsetwacom set <device> "MapToOutput" <output>[/FONT]. I'm not sure how I could configure my screens so that xrandr detects the devices with nVidia drivers (260.19.06).

---

### Post by Favux on 2010-12-27
Hi dsavi,

Interesting, so you got the wacom.ko from input-wacom 10.10 and that worked better.  By the way the plan is pair a release of that now with each point release of xf86-input-wacom.  So you'll be back to getting the whole LWP package.

What's your output of:
```
xrandr -q --verbose
```
look like?

If you're using the proprietary Nvidia driver isn't there a configuration applet that has multimonitor setup?  Then given its Nvidia the changes would show up in your xorg.conf in /etc/X11 I'd think.

---

### Post by dsavi on 2010-12-27
Yes, there is nvidia-settings which I use for configuring Twinview with my 2x20" monitors, works like a charm. The changes should show up, it edits xorg.conf and requires root privileges to run.

[FONT="Courier New"]xrandr -q --verbose[/FONT]:
```
Screen 0: minimum 1680 x 1050, current 3360 x 1050, maximum 3360 x 1050
default connected 3360x1050+0+0 (0x161) normal (normal) 0mm x 0mm
	Identifier: 0x160
	Timestamp:  3005835
	Subpixel:   unknown
	Clones:    
	CRTC:       0
	CRTCs:      0
	Transform:  1.000000 0.000000 0.000000
	            0.000000 1.000000 0.000000
	            0.000000 0.000000 1.000000
	           filter: 
  3360x1050 (0x161)  176.4MHz *current
        h: width  3360 start    0 end    0 total 3360 skew    0 clock   52.5KHz
        v: height 1050 start    0 end    0 total 1050           clock   50.0Hz
  1680x1050 (0x194)   90.0MHz
        h: width  1680 start    0 end    0 total 1680 skew    0 clock   53.5KHz
        v: height 1050 start    0 end    0 total 1050           clock   51.0Hz
  3360x1050 (0x1c6)  179.9MHz
        h: width  3360 start    0 end    0 total 3360 skew    0 clock   53.5KHz
        v: height 1050 start    0 end    0 total 1050           clock   51.0Hz
```

---

### Post by Favux on 2010-12-27
OK, it's adding your two 1680 x 1050's into one 3360 x 1050 monitor on Screen 0.  But it seems to be saying that one monitor, the minimum 1680 x 1050 is available.  I'm thinking the other monitor would be 1681 x 1050.

What does your xorg.conf look like?

---

### Post by dsavi on 2010-12-27
There's some junk in there as I have been playing with Xinerama to see if that would solve my problem:
```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 260.19.06  (buildd@palmer)  Mon Oct  4 16:01:38 UTC 2010


Section "ServerLayout"

# Removed Option "Xinerama" "0"
# Removed Option "Xinerama" "1"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "LG Electronics W2042"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600 GT"
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600 GT"
    BusID          "PCI:2:0:0"
    Screen          1
EndSection

Section "Screen"

# Removed Option "TwinView" "1"
# Removed Option "metamodes" "DFP-0: nvidia-auto-select +1680+0, DFP-1: nvidia-auto-select +0+0"
# Removed Option "TwinView" "0"
# Removed Option "metamodes" "DFP-0: nvidia-auto-select +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "DFP-0: nvidia-auto-select +1680+0, DFP-1: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-1: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by Favux on 2010-12-27
Do you remember what a fresh Nvidia xorg.conf looks like?  A backup?

I'm wondering if Twinview has been deprecated (dropped) in Maverick.

There seem to be two devices configured.

What does your:
```
xinput --list
```
output look like?

Using the "Device name" for stylus (in quotes) let's look at the output of:
```
xsetwacom list params
```
You can skip the button output.  Then:
```
xinput list-props "Device name"
```

---

### Post by dsavi on 2010-12-28
Here's an xorg.conf produced with nvidia-settings that doesn't have any junk in it, I found that nvidia-settings has an option to not merge anything, just display a clean file.

xorg.conf:
```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 260.19.06  (buildd@palmer)  Mon Oct  4 16:01:38 UTC 2010

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "LG Electronics W2042"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600 GT"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "DFP-0: nvidia-auto-select +1680+0, DFP-1: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

[FONT="Courier New"]xinput --list[/FONT]:
```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; USB Optical Mouse                       	id=8	[slave  pointer  (2)]
&#9116;   &#8627; Wacom BambooFun 2FG 6x8 Pen eraser      	id=11	[slave  pointer  (2)]
&#9116;   &#8627; Wacom BambooFun 2FG 6x8 Pen stylus      	id=12	[slave  pointer  (2)]
&#9116;   &#8627; Wacom BambooFun 2FG 6x8 Finger pad      	id=13	[slave  pointer  (2)]
&#9116;   &#8627; Wacom BambooFun 2FG 6x8 Finger touch    	id=14	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; Creative Technology Creative USB Headset	id=9	[slave  keyboard (3)]
    &#8627; Dell Dell USB Keyboard                  	id=10	[slave  keyboard (3)]
```

[FONT="Courier New"]xsetwacom list param[/FONT]:
```
TopX             - Bounding rect left coordinate in tablet units. 
TopY             - Bounding rect top coordinate in tablet units . 
DebugLevel       - Level of debugging trace for individual devices, default is 0 (off). 
CommonDBG        - Level of debugging statements applied to all devices associated with the same tablet. default is 0 (off). 
Suppress         - Number of points trimmed, default is 2. 
RawSample        - Number of raw data used to filter the points, default is 4. 
Screen_No        - Sets/gets screen number the tablet is mapped to, default is -1. 
PressCurve       - Bezier curve for pressure (default is 0 0 100 100). 
Mode             - Switches cursor movement mode (default is absolute/on). 
TPCButton        - Turns on/off Tablet PC buttons. default is off for regular tablets, on for Tablet PC. 
Touch            - Turns on/off Touch events (default is enable/on). 
Gesture          - Turns on/off multi-touch gesture events (default is enable/on). 
ZoomDistance     - Minimum distance for a zoom gesture (default is 50). 
ScrollDistance   - Minimum motion before sending a scroll gesture (default is 20). 
TapTime          - Minimum time between taps for a right click (default is 250). 
Capacity         - Touch sensitivity level (default is 3, -1 for none capacitive tools).
CursorProx       - Sets cursor distance for proximity-out in distance from the tablet.  (default is 10 for Intuos series, 42 for Graphire series).
Rotate           - Sets the rotation of the tablet. Values = NONE, CW, CCW, HALF (default is NONE).
RelWUp           - X11 event to which relative wheel up should be mapped. 
RelWDn           - X11 event to which relative wheel down should be mapped. 
AbsWUp           - X11 event to which absolute wheel up should be mapped. 
AbsWDn           - X11 event to which absolute wheel down should be mapped. 
StripLUp         - X11 event to which left strip up should be mapped. 
StripLDn         - X11 event to which left strip down should be mapped. 
StripRUp         - X11 event to which right strip up should be mapped. 
StripRDn         - X11 event to which right strip down should be mapped. 
RawFilter        - Enables and disables filtering of raw data, default is true/on.
Threshold        - Sets tip/eraser pressure threshold (default is 27)
xyDefault        - Resets the bounding coordinates to default in tablet units. 
mmonitor         - Turns on/off across monitor movement in multi-monitor desktop, default is on 
ToolID           - Returns the ID of the associated device. 
ToolSerial       - Returns the serial number of the associated device. 
TabletID         - Returns the tablet ID of the associated device. 
GetTabletID      - Returns the tablet ID of the associated device. 
MapToOutput      - Map the device to the given output. 
all              - Get value for all parameters.

```

[FONT="Courier New"]xinput list-props "Device Name"[/FONT]:
```
Device 'Wacom BambooFun 2FG 6x8 Pen stylus':
	Device Enabled (121):	1
	Coordinate Transformation Matrix (123):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (241):	0
	Device Accel Constant Deceleration (242):	1.000000
	Device Accel Adaptive Deceleration (243):	1.000000
	Device Accel Velocity Scaling (244):	10.000000
	Wacom Tablet Area (268):	0, 0, 21648, 13530
	Wacom Rotation (269):	0
	Wacom Pressurecurve (270):	0, 0, 100, 100
	Wacom Serial IDs (271):	211, 0, 2, 0
	Wacom Display Options (272):	-1, 0, 1
	Wacom Capacity (273):	-1
	Wacom Pressure Threshold (274):	27
	Wacom Sample and Suppress (275):	2, 4
	Wacom Enable Touch (276):	0
	Wacom Hover Click (277):	0
	Wacom Enable Touch Gesture (278):	0
	Wacom Touch Gesture Parameters (279):	50, 20, 250
	Wacom Tool Type (280):	"STYLUS" (283)
	Wacom Button Actions (281):	"None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0)
	Wacom Debug Levels (282):	0, 0

```

---

### Post by Favux on 2010-12-29
Hi dsavi,

I think we're getting somewhere.

I don't believe what xsetwacom is returning.  I think those multimonitor commands are gone, they just forgot to remove the comments for them from xsetwacom.

I'm guessing Nvidia knows there's two monitors from:
>     Option         "metamodes" "DFP-0: nvidia-auto-select +1680+0, DFP-1: nvidia-auto-select +0+0"

I'm thinking the key bit is in "xinput list-props "Device Name"
> Coordinate Transformation Matrix (123):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000

I believe before we can use the new xsetwacom command we need to set up a transformation Matrix in X.

Let's review.  I think you said your monitors have the same resolution which simplifies things for us.

The new method relies on a new xsetwacom command in the form:

xsetwacom set <device name> "MapToOutput" VGA1

However we've been seeing the error "Server does not support
transformation".  So either we were attempting it on Lucid's X server
1.7 (hybrid with some early 1.8 backported into it) or we need to
actually add the transformation.  Since you are in Maverick it would have to be the latter if you're seeing the same error.

This is a two monitor case.  You set up a linear transform (matrix):

xinput set-prop <left> --type=float "Coordinate Transformation Matrix" \
      0.5 0 0 0 1 0 0 0 1

xinput set-prop <right> --type=float "Coordinate Transformation Matrix" \
      0.5 0 0.5 0 1 0 0 0 1

The numbers are a 3x3 matrix read out row by row.
```
[ c0 c1 c2 ]   [ x ]
[ c3 c4 c5 ] * [ y ]
[ c6 c7 c8 ]   [ 1 ]
```
Since we're scaling from 0-1 if both monitors have the same resolution
you'd end up with:
```
  left:            right:
[ 0.5 0 0 ]     [ 0.5 0 0.5 ]
[ 0   1 0 ]     [ 0   1 0   ]
[ 0   0 1 ]     [ 0   0 0   ]

```
With the c2 = 0.5 on the right matrix being the offset.  I don't know
if you are allowed two digits to the right of the decimal.

And at this point you can use the xsetwacom command.

By the way i'm getting this from:
[http://www.mail-archive.com/xorg-devel@lists.x.org/msg08731.html](http://www.mail-archive.com/xorg-devel@lists.x.org/msg08731.html)

I was thinking xinput or Nvidia might give us the "Device name" of the left and right monitor for the two xinput commands.  But now I'm thinking from the 'xinput list-props' output you might use just one of the commands with the stylus "Device name" in the command appropriate to the monitor you want it on.  Follow?   So you'd want to check list-props for the stylus first to see if you now have the transformation matrix in there for the stylus before using the xsetwacom command.

---

### Post by SnickerSnack on 2010-12-29
Is this coordinate transformation matrix the trouble I'm having in the other thread?  [http://ubuntuforums.org/showpost.php?p=10294651&postcount=26](http://ubuntuforums.org/showpost.php?p=10294651&postcount=26)

Also, I'm currently back tracking through the thread to find how to update to the newest versions of the wacom drivers/tools.

---

### Post by Favux on 2010-12-29
Yes if you've updated to xf86-input-wacom 0.10-10+.  We're still not sure how to do it.  Maybe we just need the coordinate options for part of the virtual screen.  So it may be simpler than this.

I linked you to how to clone the git on the other thread with links to the Bamboo and linuxwacom HOW TO's.

So you're not going to try the older way or what?

---

### Post by SnickerSnack on 2010-12-30
I tried the old way here: [http://ubuntuforums.org/showpost.php?p=10294651&postcount=26](http://ubuntuforums.org/showpost.php?p=10294651&postcount=26), but it was quite frustrating, so I decided to try the new way.

Well, I got the newer version of the input driver by following section 2 of the how-to, but it didn't seem to work at all.  The stylus was off by default, and "xsetwacom list dev" returned nothing.  So, I reinstalled the old version for the time being, since it works fine when only display is active.

I'm going to try again at getting the old way to work.  It didn't occur to me earlier to try using negative values for TopX.  After reading the last post in a thread you linked earlier, I'm going to try again.

---

### Post by dsavi on 2010-12-30
Favux, thank you so much! I have *No idea* why that works, but it did.

A better way to explain that might be to use the left coordinate transform matrix if you want to use the left monitor, or the right coordinate transform matrix if you want the right monitor. (Just putting this there for people coming from google)

So for the left monitor:

```
xinput set-prop <stylus device name> --type=float "Coordinate Transformation Matrix" 0.5 0 0 0 1 0 0 0 1
```

And for the right:

```
xinput set-prop <stylus device name> --type=float "Coordinate Transformation Matrix" 0.5 0 0.5 0 1 0 0 0 1
```

Choose one of those commands according to which monitor you want to map your tablet to.

If I understand it right this particular matrix only works if both monitor resolutions are the same. (Correct me if I'm wrong)

---

### Post by Favux on 2010-12-30
Hi dsavi,

Great!  We finally figured it out!

Yes, you put it much better than I did.

Correct.  For the same resolution.  For different resolutions the coefficients would vary and for a 3 monitor setup there would be another matrix/xinput command for the third monitor.

To help others can you post your list-props with the "Device name" in it from 'xinput --list' so others can see the transform in it?  It'll tell us which monitor you chose also.  Please include the xsetwacom command you used too.

---

### Post by Favux on 2010-12-30
Hi dsavi, SnickerSnack, and everybody,

I've set up a preliminary HOW TO for the new method for dual and multi-monitors and the Wacom tablet here:  [http://ubuntuforums.org/showthread.php?t=1656089](http://ubuntuforums.org/showthread.php?t=1656089)

Comments, critiques, testers, and help with the math:  all feedback appreciated.  Please post on that thread.


dsavi, I'm also interested if the changes to the transformation matrix from the xinput command last through a reboot or if you need to set it up in a start up script.  My understanding is the xsetwacom command needs to be in a start up script to apply to each session.

---

### Post by Francus on 2011-01-16
I have a tablet pc (Toshiba m780 S7240) with a wacom diplay.
I installed Ubuntu 10.10 and the tablet seemed to work by default. At least it was possible to touch it and obtain a response.

However only one of the bezel buttons was working (the one to shutdown the pc) but the pointing device and the 3 other buttons are dead.

Also it would be nice to be able to configure the touch pressure.

I tried to follow the instructions found: installed utouch and xserver-xorg-input-wacom, but nothing changed. Also I am very afraid that going along meddling with it, without really knowing what I'm doing, I'll end definitely breaking it. Much more because it seems very complicated.

Also Instructions differentiate among USB and serial tablets and I do not even know what kind of tablet I have.

May be somebody knows something relatively simple to do just one time and that will possibly survive future kernel updates.;)

---

### Post by Favux on 2011-01-18
Hi Francus,

I would think you have a serial Wacom digitizer as that is what the M700 and M750 have.

So you don't need to worry about the usb kernel driver wacom.ko or a kernel update "breaking it".

With luck you should just need to clone the xf86-input-wacom (the X driver) git repository.  See part II. of the [Bamboo P & T HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562") and follow the instructions.

---

### Post by Francus on 2011-01-18
> **Favux said:**
> Hi Francus,

I would think you have a serial Wacom digitizer as that is what the M700 and M750 have.

So you don't need to worry about the usb kernel driver wacom.ko or a kernel update "breaking it".

With luck you should just need to clone the xf86-input-wacom (the X driver) git repository.  See part II. of the [Bamboo P & T HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562") and follow the instructions.

Hi Favux,
many thanks for your prompt replay
I tried to follow the clear instructions of part II, but it seems that something went wrong, when I arrived to "make", see the following,where Scrivania is Desktop in italian, and Nessuna operazione da eseguire per "all" means: no operation to be executed for "all":

```
f@Toshiba:~/Scrivania/util-macros-1.8.0$ make
make: Nessuna operazione da eseguire per "all".
f@Toshiba:~/Scrivania/util-macros-1.8.0$ sudo make install
make[1]: ingresso nella directory "/home/f/Scrivania/util-macros-1.8.0"
make[1]: Nessuna operazione da eseguire per "install-exec-am".
test -z "/usr/share/aclocal" || /bin/mkdir -p "/usr/share/aclocal"
 /usr/bin/install -c -m 644 'xorg-macros.m4' '/usr/share/aclocal/xorg-macros.m4'
test -z "/usr/share/util-macros" || /bin/mkdir -p "/usr/share/util-macros"
 /usr/bin/install -c -m 644 'INSTALL' '/usr/share/util-macros/INSTALL'
test -z "/usr/share/pkgconfig" || /bin/mkdir -p "/usr/share/pkgconfig"
 /usr/bin/install -c -m 644 'xorg-macros.pc' '/usr/share/pkgconfig/xorg-macros.pc'
make  install-data-hook
make[2]: ingresso nella directory "/home/f/Scrivania/util-macros-1.8.0"
rm -f /usr/share/aclocal/xorgversion.m4
make[2]: uscita dalla directory "/home/f/Scrivania/util-macros-1.8.0"
make[1]: uscita dalla directory "/home/f/Scrivania/util-macros-1.8.0"
f@Toshiba:~/Scrivania/util-macros-1.8.0$ 
```

---

### Post by Favux on 2011-01-18
Hi Francus,

I think you are good.  That's not an error.  It looks like you compiled macros 1.8 and it was installed.  You can check for the file in the directory and Properties on the file for the date.

---

### Post by Francus on 2011-01-19
> **Favux said:**
> Hi Francus,

I think you are good.  That's not an error.  It looks like you compiled macros 1.8 and it was installed.  You can check for the file in the directory and Properties on the file for the date.

Which file? A file called install-sh in folder util-macros-1.8.0? It was last modified mer 19 mag 2010 

Anyway I tried to go along and I seem to get an error:

> f@Toshiba:~/Scrivania/xf86-input-wacom$ ./autogen.sh --prefix=/usr
./autogen.sh: 9: autoreconf: not found


I am sorry if am making stupid questions, but many thanks for helping

---

### Post by Favux on 2011-01-20
Hi Francus,

The file is called xorg-macros.m4 and should be at "/usr/share/aclocal".

> ./autogen.sh: 9: autoreconf: not found 
It looks like you did not install the "autoconf" library.  The dependency line with all of the libraries and dependencies is long and extends past the edge of the box on the right.  Make sure you get the entire line.

---

### Post by juditk on 2011-01-27
My Wacom Pen doesn't work at all in Jaunty. Can I have some help please?

So far: 
1. I plugged it in because [this]("https://help.ubuntu.com/community/Wacom") said that it should work without additional configuration. The light turned on but nothing more. 
2. Then I Installed: "wacom-tools" and "xserver-xorg-input-wacom" from Synaptic. 
3. Copied xorg.conf to /etc/X11 and that made it crash. 
4. After that I installed the drivers that came with the tablet on another computer with windows xp and everything works, ...so the tablet is fine it just doesn't work with Ubuntu. 

Can someone explain what should I do or what thread I should read? So far nothing helped. I'm not a Linux expert so please tell me step by step. 

Thanks.

---

### Post by Favux on 2011-01-27
Hi juditk,

Jaunty is no longer supported so you won't get updates, not even security updates.  Karmic will be supported through April.  Are you sure you want to use Jaunty?

If so we can get your tablet working in Jaunty.  What tablet is it?  Is it a Wacom Bamboo Pen?  On the bottom of the tablet does it say CTL460?  If not please post the model #.  In a terminal enter:
```
lsusb
```
In the output we're looking for the Wacom line.  Please post it.

---

### Post by juditk on 2011-01-27
Yes it's Wacom Bamboo Pen. On the bottom it says CTL-460. 

And I don't mind if it's not supported anymore as long as I can use it.

---

### Post by Favux on 2011-01-27
Fine, let's continue on the thread you started.

---

### Post by pszpak on 2011-01-31
First thanks to those who have put the work in to make my bamboo pen and tablet work so well in Ubuntu 10.10x64!

My question is a matter of clarification.

As a left-hander, does these commands:
xsetwacom set stylus rotate HALF
xsetwacom set eraser rotate HALF

Entered into the cli, rotated tablet's surface? And that's all? Are there any other steps?

---

### Post by Favux on 2011-01-31
Well if you have touch you'd want to add that too.  Also if you want it as a "permanent" change you would want to add the commands to a start up script.

---

### Post by cutrock on 2011-02-23
I've tried a couple times to convert over to ubuntu as my primary OS, but I always get hung up on my mouse being sub-par. Hopefully someone here can guide me in the right direction.

I'm using the Bamboo Fun (CTE-450/K), and my mouse is much too sensitive. I have to lift it about a half inch off of the pad to keep it from dragging the cursor around with it. Is there any way to lower the sensitivity of the mouse pad so that I only have to lift the mouse slightly off of the pad to reset my mouse's position?

I've tried running through installing xf86-input-wacom-0.10.11 and using the wacom drivers available in the ubuntu software manager, but to no avail. Is there anyone here that might have solved this issue or have any idea on how to approach it?

---

### Post by Favux on 2011-02-23
Hi cutrock,

Welcome to Ubuntu forums!

Sure.  I'm assuming you're describing a Wacom tablet mouse.

The over acceleration issue is caused by the mouse being initialized as relative device. The Wacom tablet mouse has a higher resolution than the average mouse and the X server doesn't have an axis range to help scaling the movement, so it sends more events with higher data.  Consequently the default settings don't work too well, it's too fast.  Increasing Constant Deceleration for the device should slow it down to your preference.

Enter in a terminal:
```
xinput list
```
From the output figure out the mouse's(cursor's) device name and then enter in a terminal:
```
xinput list-props "device name"
```
If you see stuff like:
```

"Device Accel Constant Deceleration" 1.000000
"Device Accel Adaptive Deceleration" 1.000000
"Device Accel Velocity Scaling" 1.000000

```
Start increasing the values using say:
```
xinput set-prop "Wacom BambooFun 2FG 4x5 Finger touch" --type=float "Device Accel Constant Deceleration" 1.250000

```
and starting with Constant Deceleration until you find settings you like.

Since Rspeed has been removed from xsetwacom that's what you need to use.

Or I may have missed your point completely and all you need is to adjust CursorProximity.  In which case it's something like:
```
xsetwacom set "device name" CursorProximity "10"
```
*man xsetwacom* says "default is 10 for Intuos series, 42 for Graphire series" but doesn't mention the Bamboo.

---

### Post by cutrock on 2011-02-23
Thanks Favux, for the welcome and the help

To be more clear - the problem isn't that the cursor moves around on screen too quickly or accelerates too rapidly, but that I have to pick up the mouse too far off of the mousepad to keep the mousepad from picking up the movement.

I tried playing around with both the xinput and xsetwacom configuration tools, but nothing seemed to fix my mouse.

I feel like the
```
xsetwacom --set "Wacom BambooFun 4x5 cursor" CursorProximity 10
```
command is likely the solution, but it didn't seem to have any observable effect on my mouse's behavior. I used the corresponding --get tag to confirm that my command took, but my mouse remained sensitive even when lifted off of the pad.

I wasn't sure if a restart was necessary to see the effects of the command, but after a restart the same --get command showed that the value was still set at 42 (the default), and not the 10 that I had entered before.

I hope this helps narrow down my problem, thanks again for your help.

---

### Post by Favux on 2011-02-23
The xsetwacom commands are runtime commands and should apply as soon as they are entered in a terminal.  By the same token they don't last through a reboot unless entered in a start up script.  See example samples attached to post #2 on the [Bamboo P & T HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562") thread.

From what you're saying it may be that CursorProximity is no longer a user configurable parameter, despite appearing to be so in *man xsetwacom*.  I guess I'd try some other values and see if any of them make a difference.

Did you see anything in list-props about proximity?  Maybe we could go the xinput route?

Are you in Maverick with the default xf86-input-wacom-0.10.8 or did you keep 0.10.11?

---

### Post by cutrock on 2011-02-23
I wasn't able to try a whole lot of parameters in xsetwacom, but I did successfully change it from Absolute position to Relative position, so it must be working on some level.

I'm running 10.10

I'm not sure what the state of my xf86-input-wacom is right now - I successfully ran ./configure and make && make install with 0.10.11, so I'm assuming that this means I'm running 0.10.11, but I don't know how to tell for certain. 

I ran the command,
```
xinput list-props "Wacom BambooFun 4x5 cursor"
```

and the only parameters that looked reasonable were, 
"Wacom Proximity Threshold"
"Wacom Capacity"
"Wacom Sample and Suppress"
"Wacom Hover Click"

I hope this helps - thanks!

---

### Post by Favux on 2011-02-23
Let's look at the whole line for "Wacom Proximity Threshold".  Need to see the values.

"Wacom Hover Click" is whether you have TabletPCButton on or off for the stylus.  Other two shouldn't matter.

The Xorg.0.log in /var/log should tell you the version when it loads the Wacom X driver module.

Another thing to check is to see if you have two xsetwacom executables if xsetwacom commands aren't working or are working erratically.  Look in /usr/local/bin for xsetwacom (it should be in /usr/bin). If there it may mean you forgot the '--prefix=/usr' flag on the xf86-input-wacom configure line. In which case you may have a xsetwacom executable in both locations and are experiencing version conflict. Delete the one in the wrong location, i.e. /usr/local/bin.  The one you have left however may be from the default install so you might want to reinstall 0.10-11 if it has an old date in Properties.

---

### Post by cutrock on 2011-02-23
"Wacom Proximity Threshold" took values between 1 and 5. I didn't notice any difference when changing it, though. 

My Xorg.0.log showed that I'm using Wacom X driver 10.8

I did see that I had xsetwacom installed to /usr/local/bin, and I erased that. I then used Ubuntu Software Manager to remove the installed wacom package and tried to install xf86-linux-wacom-0.10.11 using the commands,

```

./configure --prefix=/usr --libdir=/usr/lib64
make
sudo make install

```

After my restart, my Xorg.0.log file is still saying that I'm using driver version 10.8.

I'm not really sure which drivers are installed at this point, since it's not registering in the Xorg.0.log file. I didn't do anything else with the linux-wacom files past those commands, so if anything else is necessary, then I probably haven't actually installed any drivers aside from the default ones.

---

### Post by Favux on 2011-02-23
The mistake was uninstalling xserver-xorg-input-wacom because that uninstalls xserver-xorg-input-all which you need installed for xf86-input-wacom to work.  That's a new dependency since Karmic.  And installing one will install the other.  Kind of doubt you needed the 64-bit flag either.

To get the latest version of xf86-input-wacom see part II. of the [Bamboo P & T HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").  Right now 0.10.11 has a bug that crashes the Cintiq and maybe the Intuos4.  I don't know about a Bamboo.  My PT works fine.

---

### Post by cutrock on 2011-02-24
EDIT2: I reformatted my ubuntu installation, and installed the drivers according to [the Bamboo Pen and Touch]("http://ubuntuforums.org/showthread.php?t=1515562") tutorial. The only hang up I had was unpacking the .tar.bz2 file - the git command downloaded a file called "download", so I had to use the line
```
tar xjvf download
``` instead. After that, everything went smoothly. My Xorg.0.log file now shows that I'm running linuxwacom "compiled for 1.9.0, module version = 0.10.11."

Unfortunately, after playing around with the CursorProximity parameter, my mouse problems don't seem to be at all affected. 


EDIT: I realized this morning that I also have an Xorg.1.log which still has the wacom  module version at 0.10.0 and an Xorg.2.log file which does have the wacom drivers, "compiled for 1.9.0, module version = 0.10.11". Is this the same as a Xorg.0.log file - should I delete the Xorg.0.log and Xorg.1.log files?


I reinstalled xserver-xorg-input-wacom through Ubuntu Software Center, and installed xf86-input-wacom according to the HOW TO.

However, this line,
```
sudo apt-get build-dep xf86-input-wacom
```
didn't run. Also, The file I downloaded is a .tar.gz, not a .tar.bz2, and I used it instead of the .tar.bz2.

After all of this, the file /var/log/Xorg.0.log still shows,
```
[  1239.332] 	compiled for 1.8.99.905, module version = 0.10.8
```

I really appreciate all the time and effort you've invested in this problem already - thanks a ton.

---

### Post by baneberry on 2011-03-08
I have everything almost working on a Wacom Bamboo Craft Pen. My needs for it are pretty basic. The trouble I am having is that when I tap a tab in web browser, it pulls up the right menu rather doing a single click. How do I get a tap with the pen to be like a single click of a mouse?

---

### Post by Favux on 2011-03-08
Hi baneberry,

Does it say CTL460 on the bottom of the tablet?

The default should be the stylus tip is a left click.  That's how it works for me in Firefox.  Do you have another browser?  Have you configured your stylus buttons with a script or something?  Maybe there's a typo assigning Button 1 (the tip) to 3 (right click)?

---

### Post by baneberry on 2011-03-08
Thanks!

It says CTL-461 on the bottom of the tablet. I'm using Firefox, but I also use Chrome. I haven't configured anything.  But I am competent at the command line and in emacs, if you have any suggestions about what to configure.

---

### Post by Favux on 2011-03-08
Let's figure out what the stylus tip thinks it is.  Enter in a terminal *xinput list* or *xsetwacom list* to figure out what the "device name" for the stylus is. Then in a terminal enter:
```
xsetwacom get "device name" Button1
```
Remember if you've updated your xf86-input-wacom to 0.10.11 or later to use Button 1 instead of Button1.

---

### Post by baneberry on 2011-03-09
I believe that I followed your directions.

$ [COLOR="Purple"]xsetwacom list[/COLOR]
Wacom Bamboo Craft Pen eraser           id: 11  type: ERASER    
Wacom Bamboo Craft Pen stylus           id: 12  type: STYLUS    
Wacom Bamboo Craft Finger pad           id: 13  type: PAD       
Wacom Bamboo Craft Finger touch         id: 14  type: TOUCH     

$ [COLOR="purple"]xsetwacom get 12 Button 1[/COLOR]
1

By the way, I'm using Kubuntu 11.04 64 bit.

---

### Post by Favux on 2011-03-09
Well that's the correct setting.  Stylus tip by default is left click or *Button 1 1*.

So is it some setting in Firefox or Kubuntu or Kubuntu Firefox or just because it's an alpha Natty version?  Does it work as a normal left click elsewhere?  If so this may be a Natty bug and you should file a bug report.  Can't imagine this is a deliberately planned behavior change.

PS:  So Kubuntu is finally going 64-bit.  Good.

---

### Post by baneberry on 2011-03-09
I was having the identical issue in Ubuntu 10.10, and my efforts to fix it ended up making the wacom driver unusable. It's why I installed 11.04.  

Is there someway I can reassign the button to a right click? Maybe the buttons are reversed for some reason on my tablet.

---

### Post by Favux on 2011-03-09
There was a change in button parameter names starting with xf86-input-wacom-0.10.11.  So I'm assuming that's what Natty has currently.  What was *Button1* became *Button 1*.  Any button setting can be changed by using the xsetwacom set command.
```
xsetwacom set "device name" Button X x
```
For example the current default is Button 2 3, by user demand.  3 is right click and 2 middle click.  So to change it back to a middle click:
```
xsetwacom set "device name" Button 2 2
```
You use "device name" because ID # changes with hot plugging.

You shouldn't need to mess with the stylus tip.  Default is 1 and that's the value you're getting with the xsetwacom get command.  So I'm thinking something else.  Is the Natty a clean install or did you upgrade over Maverick?

---

### Post by baneberry on 2011-03-09
I reassigned Buttons 1 and 2 and everything is working as it should. My demands for Wacom is simple. I'm slightly concerned by "You use "device name" because ID # changes with hot plugging."

I used 
```
 xsetwacom set 12 Button 1 3
 xsetwacom set 12 Button 2 1
```

to fix up my Stylus's clicking.

I was thinking of put this in some place so that it would be done at startup. Where would it go? /etc/X11/Xsessions? If the ID # changes will I have to code up something to account for the changes?

Thank you so much for your help! I had been an unwilling of Windows because hand issues require using Wacom. I am now Linux! I am free!

---

### Post by Favux on 2011-03-09
Good!

For the stylus it would be:
```

xsetwacom set "Wacom Bamboo Craft Pen stylus" Button 1 3
xsetwacom set "Wacom Bamboo Craft Pen stylus" Button 2 1
```

You can do it several ways.  I use a startup script with Startup Applications.  You can create a bin folder/directory to place your scripts in, i.e. /home/yourusername/bin.  See part IV. in the [Bamboo P & T HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").

By the way out of curiosity on the bottom of the tablet does it say CTH461?

---

### Post by baneberry on 2011-03-09
Thanks! It is indeed a CTH-461.

---

### Post by Carthorse on 2011-03-10
I've been reading various wacom set up threads for some time and the problem I was having is the tip was set to 3, which I've *just* found ^^. Every time I touched the pad, the right-click came up. Using the xsetwacom set 13 Button 1 1 has corrected this. Thanks, it's a start :) It was so frustrating, trying and failing to draw/photo-edit in GIMP! I'm using a Graphire 4 (CTE 440) with 10.10 (64bit, 2.6.35-27-generic) and this behaviour is as installed, no messing about by me. My other wacom, a Wacom One is the same. Scripts are a dark art to me, is there one for the Graphire4, enabling pressure, too? I could tinker with others but I'd probably spend weeks getting it wrong :( I was even toying with the idea of using another one and just removing stuff my Wacom doesn't have, like touch etc. I use my standard mouse left-handed, Wacom right-handed, so the pad buttons and scroll-wheel on the Wacom aren't essential, tbh.

If not, is there some-where I could find which button does what, as it does in Windows default? Then at least I'd have basic functionality.

xinput list
&#9121; Virtual core pointer                                  id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                   id=4    [slave  pointer  (2)]
&#9116;   &#8627; MLK Trust Deskset 16593                     id=9    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Graphire4 4x5 eraser               id=10    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Graphire4 4x5 cursor               id=11    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Graphire4 4x5 pad                   id=12    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Graphire4 4x5 stylus                id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                                id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                       id=6    [slave  keyboard (3)]
    &#8627; Power Button                                       id=7    [slave  keyboard (3)]
    &#8627; MLK Trust Deskset 16593                     id=8    [slave  keyboard (3)]

---

### Post by Favux on 2011-03-10
Hi Carthorse,

It sure sounds like button mapping is/got messed up somehow.  How long has this been going on for you in Maverick?

Anyway I'd like to work with you on a Graphire4 with a cursor to develop a script.  Don't have one for a Graphire4 yet and haven't finalized the cursor (Wacom tablet mouse) so that would be good.

So the stylus has 2 side buttons and an eraser.  The Wacom mouse has 3 buttons?  The pad has how many buttons?  How are they laid out?  Any scroll wheel or other such?

You use the get command with the "device name" (in quotes) and parameter to find out the current setting or the special "all" parameter.  Like so:
```

xsetwacom get "Wacom Graphire4 4x5 stylus" Button1
```
or
```

xsetwacom get "Wacom Graphire4 4x5 stylus" all
```
Then you just change get to set and add the parameter value at the end to change the setting.

---

### Post by Carthorse on 2011-03-10
Thanks! I'm very grateful for any assistance. Having this past year returned to photography, I wanted the finer control a stylus offers over a mouse.

I'm not using a Wacom mouse: The Graphire4 has two buttons at the top of the pad, above the drawing area, either side of a scroll-wheel. These are working as normal, the same as my usual normal mouse. (The buttons are reversed on my mouse but out of preference for using it left-handed. I don't need to do this for the Wacom pad buttons or wheel :)  )
The stylus, as you've noted: two side buttons and and eraser.
I've **always** had this problem with the mapping, right from 10.04. I never had a graphic tablet before that, so I can't comment on if it's 10.x specific. I even bought another Wacom (the Wacom One) to rule out hardware faults.
get "Wacom Graphire4 4x5 stylus" all
Option "Area" "0 0 10208 7424"
Option "ToolDebugLevel" "0"
Option "TabletDebugLevel" "0"
Option "Suppress" "4"
Option "RawSample" "2"
Option "PressureCurve" "0 0 100 100"get "Wacom Graphire4 4x5 stylus" all
Option "Area" "0 0 10208 7424"
Option "ToolDebugLevel" "0"
Option "TabletDebugLevel" "0"
Option "Suppress" "4"
Option "RawSample" "2"
Option "PressureCurve" "0 0 100 100"
Option "Mode" "Absolute"
Option "TabletPCButton" "off"
Option "Touch" "off"
Option "Gesture" "off"
Option "ZoomDistance" "50"
Option "ScrollDistance" "20"
Option "TapTime" "250"
Option "Capacity" "-1"
Property 'Wacom Proximity Threshold' does not exist on device.
Option "Rotate" "none"
Property 'Wacom Wheel Buttons' does not exist on device.
Property 'Wacom Wheel Buttons' does not exist on device.
Property 'Wacom Wheel Buttons' does not exist on device.
Property 'Wacom Wheel Buttons' does not exist on device.
Property 'Wacom Strip Buttons' does not exist on device.
Property 'Wacom Strip Buttons' does not exist on device.
Property 'Wacom Strip Buttons' does not exist on device.
Property 'Wacom Strip Buttons' does not exist on device.
Option "RawFilter" "on"
Option "Threshold" "27"
Option "ToolID" "288"
Option "ToolSerial" "0"
Option "TabletID" "21"

Option "Mode" "Absolute"
Option "TabletPCButton" "off"
Option "Touch" "off"
Option "Gesture" "off"
Option "ZoomDistance" "50"
Option "ScrollDistance" "20"
Option "TapTime" "250"
Option "Capacity" "-1"
Property 'Wacom Proximity Threshold' does not exist on device.
Option "Rotate" "none"
Property 'Wacom Wheel Buttons' does not exist on device.
Property 'Wacom Wheel Buttons' does not exist on device.
Property 'Wacom Wheel Buttons' does not exist on device.
Property 'Wacom Wheel Buttons' does not exist on device.
Property 'Wacom Strip Buttons' does not exist on device.
Property 'Wacom Strip Buttons' does not exist on device.
Property 'Wacom Strip Buttons' does not exist on device.
Property 'Wacom Strip Buttons' does not exist on device.
Option "RawFilter" "on"
Option "Threshold" "27"
Option "ToolID" "288"
Option "ToolSerial" "0"
Option "TabletID" "21"


Something has just occurred to me as I'm typing this: having my normal mouse buttons reversed, would this affect the Wacom's own default?
BTW, sorry for the list, not sure how to put it in a box.

---

### Post by Favux on 2011-03-10
OK, I'll whip up a script.  Take a few minutes.

The default xf86-input-wacom in Maverick is 0.10.8.  They're still fixing it up.  For example they just fixed the xsetwacom RawSample and Suppress parameters.  So depending on your results you might want to consider updating xf86-input-wacom.

To box something place it in between the code tags (click on # in the top right).

Edit:  4 buttons total or 2 buttons total on the tablet?

---

### Post by Favux on 2011-03-10
Alright the script is attached to the bottom of the post.  To download click on it.

To set it up to auto-start, download the attached file, and rename it .xsetwacom.sh (or whatever you want) and place it in your /home/yourusername directory or you could make a folder/directory called bin (/home/yourusername/bin) and place it there. Remember it will be a hidden file if you use the . in front. To enable the xsetwacom commands in the .xsetwacom.sh file to apply to Xserver through a reboot you enter in a terminal:
```
chmod +x ~/.xsetwacom.sh
```
or you could right click on the file and in Properties, in the Permission tab, check Execute as program. Then go to System->Preferences->Startup Applications and click on add and for the command write "sh /home/yourusername/.xsetwacom.sh" (without the quotes). You can also change your settings on the fly using the xsetwacom parameters in a terminal. They only apply during the current session.

Once the script is executable you can double click on it to apply it's settings or reboot to check the auto-start set up.

The idea is if you are happy with the defaults you comment them out with a # in front of the line.  Only leave active the lines that are actually modifying things.

It's also a good idea to set up your general or start up configuration script in a Launcher. That way if you change a xsetwacom setting to test something when you're done you can restore your general configuration. 

In Gnome right click on your Desktop and chose Create Launcher... In the Launcher enter a name. Then in the Command box add the entire path for the script. It's a good idea to select an icon also. Close and the profile script will now run when you double click on the Launcher.

---

### Post by Carthorse on 2011-03-10
I'm not seeing any difference?
BUT: If I change my mouse to right-hand in System>Preferences>Mouse, the stylus behaves itself. Back to being a pain when I change back to left-hand mouse. OR when I:
xsetwacom set 13 Button 1 1
After this, my stylus works enough to draw/select etc in GIMP using my right-hand, and my mouse works fine as a left-hand mouse.
I have the 1:0.10.99 xserver-xorg-input-wacom.
Indecently, the brush pressure works fine in Krita but not in GIMP. I guess this is GIMP specific and some settings within GIMP need to be changed. I think I've seen other threads regarding this, I'll look.
Getting there :)

---

### Post by Favux on 2011-03-10
Ahah!
> I have the 1:0.10.99 xserver-xorg-input-wacom.
Where did you get that from?  Maverick has 0.10.8.

---

### Post by Carthorse on 2011-03-10
Ah. I think it was while I was at the point of try anything :(
From [http://ppa.launchpad.net/irie/wacom/ubuntu](http://ppa.launchpad.net/irie/wacom/ubuntu) (maverick main)

---

### Post by Favux on 2011-03-10
OK, that explains it.  IRIE's just updated his PPA to 0.10.11+.  A bunch of parameter names changed with it, see:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xsetwacom#Table_of_New_Parameter_Names](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xsetwacom#Table_of_New_Parameter_Names)

So ClickForce is Threshold, PressCurve is PressureCurve, and Button1 would be Button 1.  That's probably why the button commands weren't working for you.  Make those changes to the script.

---

### Post by Carthorse on 2011-03-10
Done.:biggrin:

Thank you so much! Although GIMP still doesn't 'do' pressure, Krita does so that's no fault of the script or the graphic tablet :)
Not only do I have a working graphic tablet, I even understand a little of *why* it now works! I may even try to adapt it for my Bamboo One, put two launchers on the desktop. But that's by no means a priority, now the Graphire4's working! More of a 'lets see if..."
I'll save the original script somewhere safe and play with some basic customisation. But I'll always have your script to fall back on when I get it wrong lol.
Thanks again from an awkward customer with a right-hand tablet and left-hand mouse :)

---

### Post by Favux on 2011-03-10
Great!  Not a problem.

For pressure in Gimp and Inkscape etc. you have to configure the extended input devices.  See the screen shots near the bottom of the [Wacom wiki]("https://help.ubuntu.com/community/Wacom").

---

### Post by Carthorse on 2011-03-11
Thanks again, working fine :)
After a little digging, I've also managed to edit it, to include xinput commands to keep it (the Graphire4) mapped to the right-hand screen only. I have two screens, each different resolutions, set as twinview using nvidia binaries. My set-up is that I use the bigger right hand screen when editing photographs for it's size and that it's colour calibrated. The left hand screen is then free for frivolities, such as a dvd or Facebook :)
I'm probably a little unusual in that I'm comfortable with two-handed control, the mouse and the tablet, though this seems logical to me.

 Possibly of no interest to anyone else:
```
#Coordinate Transformation Matrix commands to restrict Wacom to right-hand screen. #The formula used was : 
#Left Monitor: Lh/(Lh+Rh) 0 0 0 Lv/Rv 0 0 0 1
#Right Monitor Rh/(Lh+Rh) 0 Lh/(Lh+Rh) 0 Rv/Rv 0 0 0 1
xinput set-prop "Wacom Graphire4 4x5 stylus" --type=float "Coordinate Transformation Matrix" 0.461538 0 0 0 .288461 0 0 0 1
xinput set-prop "Wacom Graphire4 4x5 stylus" --type=float "Coordinate Transformation Matrix" 0.538461 0 0.461538 0 1 0 0 0 1
xinput set-prop "Wacom Graphire4 4x5 cursor" --type=float "Coordinate Transformation Matrix" 0.461538 0 0 0 .288461 0 0 0 1
xinput set-prop "Wacom Graphire4 4x5 curso" --type=float "Coordinate Transformation Matrix" 0.538461 0 0.461538 0 1 0 0 0 1
xinput set-prop "Wacom Graphire4 4x5 eraser" --type=float "Coordinate Transformation Matrix" 0.461538 0 0 0 .288461 0 0 0 1
xinput set-prop "Wacom Graphire4 4x5 eraser" --type=float "Coordinate Transformation Matrix" 0.538461 0 0.461538 0 1 0 0 0 1
#The rest of the script from  Favux:
## Device names and ID numbers from 'xinput --list' entered in a terminal.
#
## In the example "Device name" not ID # is used.  Note if you use the
## xorg.conf the "Device names" will be stylus, eraser, touch, and pad.
#
## If you are hot plugging use "Device name" as ID # can change.
#
## ClickForce changes name to Threshold with xf86-input-wacom 0.10.9 (11-19-10)
## Lucid default - 0.10.5  Maverick default - 0.10.8
#
## Warning:  Changing Mode to either Absolute or Relative in stylus/eraser stops
## the mouse from being able to pull guidelines out of the ruler in Gimp.

## stylus = "Wacom Graphire4 4x5 stylus" = ID 13
xsetwacom set "Wacom Graphire4 4x5 stylus" Suppress "4"  # data pt.s trimmed, default is 4, 0-20
xsetwacom set "Wacom Graphire4 4x5 stylus" RawSample "2"  # data pt.s filtered, default is 2, 0-100
xsetwacom set "Wacom Graphire4 4x5 stylus" Threshold "27"  # pressure, default is 27, range is 0-2047
#xsetwacom set "Wacom Graphire4 4x5 stylus" Threshold "27"  # pressure, default is 27, range is 0-2047
xsetwacom set "Wacom Graphire4 4x5 stylus" PressureCurve "5 10 90 95" # Bezier curve, default is 0,0,100,100
xsetwacom set "Wacom Graphire4 4x5 stylus" TPCButton "off"  # stylus tip + button, or "off" for hover mode
#xsetwacom set "Wacom Graphire4 4x5 stylus" Mode "Absolute"  # or Relative
xsetwacom set "Wacom Graphire4 4x5 stylus" Button 1 "1"  # left mouse click
xsetwacom set "Wacom Graphire4 4x5 stylus" Button 2 "3"  # right mouse click
xsetwacom set "Wacom Graphire4 4x5 stylus" Button 3 "2"  # middle mouse click

## eraser = "Wacom Graphire4 4x5 eraser" = ID 10
xsetwacom set "Wacom Graphire4 4x5 eraser" Suppress "4"  # data pt.s trimmed, default is 4, 0-20
xsetwacom set "Wacom Graphire4 4x5 eraser" RawSample "2"  # data pt.s filtered, default is 2, 0-100
xsetwacom set "Wacom Graphire4 4x5 eraser" Threshold "27"  # pressure, default is 27, range is 0-2047
#xsetwacom set "Wacom Graphire4 4x5 stylus" Threshold "27"  # pressure, default is 27, range is 0-2047
xsetwacom set "Wacom Graphire4 4x5 eraser" PressureCurve "0 10 90 100" # Bezier curve, default is 0,0,100,100
#xsetwacom set "Wacom Graphire4 4x5 eraser" Mode "Absolute"  # or "Relative" cursor movement
xsetwacom set "Wacom Graphire4 4x5 eraser" Button 1 "1"

## pad = "Wacom Graphire4 4x5 pad" = ID 12
xsetwacom set "Wacom Graphire4 4x5 pad" Button 1 "key p"  # Paintbrush
xsetwacom set "Wacom Graphire4 4x5 pad" AbsWDn "key minus"  # Zoom out
xsetwacom set "Wacom Graphire4 4x5 pad" AbsWUp "key plus"  # Zoom in
xsetwacom set "Wacom Graphire4 4x5 pad" Button 2 "key ctrl z"  # Undo

## Developed with Carthorse
```

Sorry, Lh =Left Horizontal resolution, Rv=Right vertical resolution etc. Just to clarify, though I'm sure it wasn't hard to guess ;)

---

### Post by riesengreen on 2011-04-02
I just want to say thanks.

I have had a Wacom Graphire Bluetooth tablet for years, and have been on and off of this forum thread trying to get it to work for almost as long. 
Despite the best intentions of all involved I was never able to manage it myself. 
Recently, however, after upgrading to 10.10, I figured I would give it another try--and it worked!
If I understand correctly this is due to the work of those who improve each new version of the OS. I sure didn't do anything different!
So thanks to all those who have worked on this! I am grateful to be able to use this tool on Ubuntu!

=D>

---

### Post by moygara on 2011-04-03
I have an Intuos tablet that works in GIMP (all the pressure sensitivity options are on) but won't actually be pressure sensitive. The tablet works fine on other computers. Also Ubuntu is up to date.

---

### Post by Favux on 2011-04-03
Hi moygara,

Welcome to Ubuntu forums!

Is it an Intuos 3 or 4?

In Gimp's extended input devices did you set the stylus (and eraser) to screen like I mentioned to Carthorse above?  Right now Gimp seems to think the stylus is a mouse.

---

### Post by moygara on 2011-04-04
> **Favux said:**
> Hi moygara,

Welcome to Ubuntu forums!

Is it an Intuos 3 or 4?

In Gimp's extended input devices did you set the stylus (and eraser) to screen like I mentioned to Carthorse above?  Right now Gimp seems to think the stylus is a mouse.
I have an Intuos 4.I went to the "Input" dialog box in gimp -- the exact one shown here
   [https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom)
I set "Device" to "stylus" and mode to "Screen" as directed; I did
the same for Eraser and Cursor devices. Then I went to the paintbrush
box and turned on "opacity," "hardness," "size," and "colour" under
the "Pressure sensitivity" setting.
Didn't work -- again, I can use the stylus like a mouse, but no pressure
effects in the paintbrush.
Again, I'm running a standard Ubuntu 10.10. I haven't changed

   /usr/share/X11/xorg.conf.d/50-wacom.conf

at all. I left it exactly as it comes "out of the box."
Thanks!

---

### Post by Favux on 2011-04-04
Alright.  Do you see pressure effects while inking?  In other words is it only paintbrush where pressure isn't working?

First thing is does your Intuos4 have a Wacom tablet mouse/puck?  If not set the cursor (Wacom tablet mouse) back to the default disabled in Gimp.  See if that helps.

If not let's run some diagnostics.  In a terminal enter:
```
xinput list
```
and
```
xsetwacom list
```
and post the outputs.

---

### Post by moygara on 2011-04-07
The paintbrush is completely not effected by whatever pressure is on the stylus. I do have a puck, so I went ahead and did the inputs-

for xinput list-

&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=11	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos4 4x6 eraser                	id=12	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos4 4x6 cursor                	id=13	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos4 4x6 pad                   	id=14	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos4 4x6 stylus                	id=15	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Chicony USB 2.0 Camera                  	id=9	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=10	[slave  keyboard (3)]


for xinputwacom list-

Wacom Intuos4 4x6 eraser ERASER    
Wacom Intuos4 4x6 cursor CURSOR    
Wacom Intuos4 4x6 pad PAD       
Wacom Intuos4 4x6 stylus STYLUS

---

### Post by Favux on 2011-04-07
It sure seems like everything is correct and pressure should be working.

You've ruled out a hardware problem since you have pressure on other computers and I'm assuming in Windows.

Let's look at the outputs of:
```
xsetwacom get "Wacom Intuos4 4x6 stylus" Pressure
```
and
```
xinput list-props "Wacom Intuos4 4x6 stylus"
```

---

### Post by moygara on 2011-04-12
xsetwacom get "Wacom Intuos4 4x6 stylus" Pressure
Unknown parameter name 'Pressure'.

xinput list-props "Wacom Intuos4 4x6 stylus"
Device 'Wacom Intuos4 4x6 stylus':
	Device Enabled (141):	1
	Coordinate Transformation Matrix (143):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (259):	0
	Device Accel Constant Deceleration (260):	1.000000
	Device Accel Adaptive Deceleration (261):	1.000000
	Device Accel Velocity Scaling (262):	10.000000
	Wacom Tablet Area (572):	0, 0, 31496, 19685
	Wacom Rotation (573):	0
	Wacom Pressurecurve (574):	0, 0, 100, 100
	Wacom Serial IDs (575):	184, 0, 2, 0
	Wacom TwinView Resolution (576):	0, 0, 0, 0
	Wacom Display Options (577):	-1, 0, 1
	Wacom Screen Area (578):	0, 0, 1280, 800
	Wacom Proximity Threshold (579):	10
	Wacom Capacity (580):	-1
	Wacom Pressure Threshold (581):	27
	Wacom Sample and Suppress (582):	2, 4
	Wacom Enable Touch (583):	0
	Wacom Hover Click (584):	1
	Wacom Enable Touch Gesture (585):	0
	Wacom Touch Gesture Parameters (586):	50, 20, 250
	Wacom Tool Type (587):	"STYLUS" (595)
	Wacom Button Actions (588):	"None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0)

---

### Post by Favux on 2011-04-12
Sorry, my mistake.  I cut short the parameter name.
```
xsetwacom get "Wacom Intuos4 4x6 stylus" PressureCurve
```
list-props says it is set to the default, or linear setting:
> Wacom Pressurecurve (574): 0, 0, 100, 100
So it should be working.

---

### Post by moygara on 2011-04-22
Thanks!

---

### Post by chamira on 2011-04-29
Hello, upgraded to 11.04 last night and now my old Wacom tablet configurations have been wiped out. 

I suffer from RSI and I use this tablet set to be active in a very small area.

Previously I have followed your instructions and got it working. This time the changes are not being picked up. 

My 50-wacom.conf file is as below, with my additions to the TopX &etc. Those number are just guesses as I can't remember exactly what they were previously, I was hoping to set them with a bit of trial and error. 

Could you please have a look and tell me where I am doing things wrong?


Section "InputClass"
	Identifier "Wacom class"
# WALTOP needs a patched kernel driver, that isn't in mainline lk yet,
# so for now just let it fall through and be picked up by evdev instead.
#	MatchProduct "Wacom|WALTOP|WACOM"
	MatchProduct "Wacom|WACOM|Hanwang"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
EndSection

Section "InputClass"
	Identifier "Wacom serial class"
	MatchProduct "Serial Wacom Tablet"
	Driver "wacom"
EndSection

Section "InputClass"
        Identifier "Wacom serial class identifiers"
        MatchProduct "WACf|FUJ02e5|FUJ02e7"
        Driver "wacom"
EndSection


# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
	Identifier "Wacom N-Trig class"
	MatchProduct "HID 1b96:0001|N-Trig Pen"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
	Option "Button2" "3"
EndSection


Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/input/wacom" 
        Option          "TopX"        "100"     
        Option          "TopY"        "200"
        Option          "BottomX"     "800"
        Option          "BottomY"     "600"
EndSection

---

### Post by Favux on 2011-04-29
Hi chamira,

This snippet:
```
Section "InputDevice"
Driver "wacom"
Identifier "stylus"
Option "Device" "/dev/input/wacom"
Option "TopX" "100"
Option "TopY" "200"
Option "BottomX" "800"
Option "BottomY" "600"
EndSection 
```
isn't the correct syntax for xorg.conf.d since it is a xorg.conf section.  Remove it from 50-wacom.conf.  You would have to add the coordinate Options to the USB snippet below the wacom driver line.  However it would be better to do the following.

With Natty you now have Xserver 1.10 and can use a 52-wacom-options.conf in /etc/X11/xorg.conf.d to add Options for individual tablet input tools.  Follow the instructions at the Linux Wacom Project's mediawiki xf86-input-wacom HOWTO page:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xorg.conf.d](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xorg.conf.d)
and
[http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration)

---

### Post by chamira on 2011-04-29
Hello, I have followed your advice, and created a file **52-wacom-options.conf** in **/etc/X11/xorg.conf.d**

The content of this file is below:

```
Section "InputClass"
	Identifier "Wacom Graphire stylus"
        MatchDriver "wacom"
        MatchProduct "stylus"

        # Apply custom Options to this device below.
	Option "TopX" "-10"
	Option "TopY" "-20"
	Option "BottomX" "5013"
	Option "BottomY" "3711"
EndSection

Section "InputClass"
	Identifier "Wacom Graphire eraser"
        MatchDriver "wacom"
        MatchProduct "eraser"

        # Apply custom Options to this device below.
	Option "TopX" "-10"
	Option "TopY" "-20"
	Option "BottomX" "5013"
	Option "BottomY" "3711"
EndSection

Section "InputClass"
	Identifier "Wacom Graphire cursor"
        MatchDriver "wacom"
        MatchProduct "cursor"

        # Apply custom Options to this device below.
	Option "TopX" "-10"
	Option "TopY" "-20"
	Option "BottomX" "5013"
	Option "BottomY" "3711"
EndSection
```


The strange thing is the ERASER options are picked up and works (I need to turn the pen upside down) but the normal pointer (stylus or cursor?) does not seem to have picked up my options

When I checked the **xorg.0.log** file and it seems to have found my ERASER and CURSOR options, but not my STYLUS options, here's the relevant bit:
```
[  2580.994] (II) config/udev: Adding input device Wacom Graphire (/dev/input/event4)
[  2580.994] (**) Wacom Graphire: Applying InputClass "evdev tablet catchall"
[  2580.994] (**) Wacom Graphire: Applying InputClass "Wacom class"
[  2580.994] (II) LoadModule: "wacom"
[  2580.994] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[  2580.994] (II) Module wacom: vendor="X.Org Foundation"
[  2580.994] 	compiled for 1.10.0, module version = 0.10.11
[  2580.995] 	Module class: X.Org XInput Driver
[  2580.995] 	ABI class: X.Org XInput driver, version 12.3
[  2580.995] (II) Using input driver 'wacom' for 'Wacom Graphire'
[  2580.995] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[  2580.995] (**) Wacom Graphire: always reports core events
[  2580.995] (**) Option "Device" "/dev/input/event4"
[  2580.995] (II) Wacom Graphire: type not specified, assuming 'stylus'.
[  2580.995] (II) Wacom Graphire: other types will be automatically added.
[  2580.995] (--) Wacom Graphire stylus: using pressure threshold of 27 for button 1
[  2580.995] (--) Wacom Graphire stylus: Wacom USB Graphire tablet maxX=10206 maxY=7422 maxZ=511 resX=80000 resY=80000  tilt=disabled
[  2580.995] (II) Wacom Graphire stylus: hotplugging dependent devices.
[  2580.995] (**) Wacom Graphire eraser: Applying InputClass "evdev tablet catchall"
[  2580.995] (**) Wacom Graphire eraser: Applying InputClass "Wacom class"
[  2580.995] (**) Wacom Graphire eraser: Applying InputClass "Wacom Graphire eraser"
[  2580.995] (II) Using input driver 'wacom' for 'Wacom Graphire eraser'
[  2580.995] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[  2580.995] (**) Wacom Graphire eraser: always reports core events
[  2580.995] (**) Option "Device" "/dev/input/event4"
[  2580.995] (**) Option "TopX" "-10"
[  2580.995] (**) Option "TopY" "-20"
[  2580.995] (**) Option "BottomX" "5013"
[  2580.995] (**) Option "BottomY" "3711"
[  2580.995] (--) Wacom Graphire eraser: Wacom USB Graphire tablet maxX=10206 maxY=7422 maxZ=511 resX=80000 resY=80000  tilt=disabled
[  2580.996] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.0/usb2/2-9/2-9:1.0/input/input4/event4"
[  2580.996] (II) XINPUT: Adding extended input device "Wacom Graphire eraser" (type: ERASER)
[  2580.996] (--) Wacom Graphire eraser: top X=-10 top Y=-20 bottom X=5013 bottom Y=3711 resol X=80000 resol Y=80000
[  2580.996] (**) Wacom Graphire eraser: (accel) keeping acceleration scheme 1
[  2580.996] (**) Wacom Graphire eraser: (accel) acceleration profile 0
[  2580.996] (**) Wacom Graphire eraser: (accel) acceleration factor: 2.000
[  2580.996] (**) Wacom Graphire eraser: (accel) acceleration threshold: 4
[  2580.996] (**) Wacom Graphire cursor: Applying InputClass "evdev tablet catchall"
[  2580.996] (**) Wacom Graphire cursor: Applying InputClass "Wacom class"
[  2580.996] (**) Wacom Graphire cursor: Applying InputClass "Wacom Graphire cursor"
[  2580.996] (II) Using input driver 'wacom' for 'Wacom Graphire cursor'
[  2580.996] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[  2580.996] (**) Wacom Graphire cursor: always reports core events
[  2580.996] (**) Option "Device" "/dev/input/event4"
[  2580.997] (**) Option "TopX" "-10"
[  2580.997] (**) Option "TopY" "-20"
[  2580.997] (**) Option "BottomX" "5013"
[  2580.997] (**) Option "BottomY" "3711"
[  2580.997] (--) Wacom Graphire cursor: Wacom USB Graphire tablet maxX=10206 maxY=7422 maxZ=511 resX=80000 resY=80000  tilt=disabled
[  2580.997] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.0/usb2/2-9/2-9:1.0/input/input4/event4"
[  2580.997] (II) XINPUT: Adding extended input device "Wacom Graphire cursor" (type: CURSOR)
[  2580.997] (--) Wacom Graphire cursor: top X=-10 top Y=-20 bottom X=5013 bottom Y=3711 resol X=80000 resol Y=80000
[  2580.997] (**) Wacom Graphire cursor: (accel) keeping acceleration scheme 1
[  2580.997] (**) Wacom Graphire cursor: (accel) acceleration profile 0
[  2580.997] (**) Wacom Graphire cursor: (accel) acceleration factor: 2.000
[  2580.997] (**) Wacom Graphire cursor: (accel) acceleration threshold: 4
[  2580.997] (II) Wacom Graphire stylus: hotplugging completed.
[  2580.997] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.0/usb2/2-9/2-9:1.0/input/input4/event4"
[  2580.997] (II) XINPUT: Adding extended input device "Wacom Graphire stylus" (type: STYLUS)
[  2580.998] (--) Wacom Graphire stylus: top X=0 top Y=0 bottom X=10206 bottom Y=7422 resol X=80000 resol Y=80000
[  2580.998] (**) Wacom Graphire stylus: (accel) keeping acceleration scheme 1
[  2580.998] (**) Wacom Graphire stylus: (accel) acceleration profile 0
[  2580.998] (**) Wacom Graphire stylus: (accel) acceleration factor: 2.000
[  2580.998] (**) Wacom Graphire stylus: (accel) acceleration threshold: 4
[  2580.998] (II) config/udev: Adding input device Wacom Graphire (/dev/input/mouse1)
[  2580.998] (II) No input driver/identifier specified (ignoring)  
```


(I also noticed that throughout the documentation I found on this forum How To's the tablet area specifications are named "TopX" "top X" or "Area x1" - I am not sure which actually works but I stuck to "TopX" as that's what I saw on the xorg logs.)

If you could please just have another look at what I'm doing, I'd be really grateful. If I can't get this sorted out soon I will have to go back to Windows as I really can't use a mouse too long and using the full width of even this small graphics card is starting to niggle my wrist.

---

### Post by Favux on 2011-04-29
The Xorg.0.log shows the stylus was picked up:
```
[  2580.997] (II) XINPUT: Adding extended input device "Wacom Graphire stylus" (type: STYLUS)
[  2580.998] (--) Wacom Graphire stylus: top X=0 top Y=0 bottom X=10206 bottom Y=7422 resol X=80000 resol Y=80000
```
Let's see if xinput and xsetwacom see it.  Enter in a terminal:
```
xinput list
and
xsetwacom list
```
That'll also help us make sure there isn't some problem with the keywords.  TopX etc. is still correct for xorg.conf.d and xorg.conf Options.  They haven't yet been switched over to Area like the xsetwacom has.

Also Graphires can have a tablet mouse which is what the cursor is.  Do you have one?  I thought at least some Graphires have a pad or tablet buttons.  Does yours?

I seem to remember someone with a Graphire or earlier model also reporting the stylus didn't show up.

---

### Post by mister_k81 on 2011-05-02
I'm sorry if this question has been asked before, but there's just too much information in this thread for me to wade through to find the specific answer that I am looking for... 

Anyway I've just done a fresh install of 11.04 (32bit) and I have an older Graphire 4 (CTE640) tablet pen. The stylus part of the pen works fine right off the bat, but I cannot find any information on how to get the two pad buttons and scroll wheel to work. Most information I can find on how to solve this problem, is either really outdated or confuses me ;P  

I'm sure there's a solution to this issue, and hopefully someone can point me in the right direction. I should also point out that I have not updated the wacom drivers or altered any config files...

---

### Post by Favux on 2011-05-02
Hi mister_k81,

See [Tablet Configuration]("http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration") on the mediawiki.

---

### Post by grindboy on 2011-05-07
Hi Favux

I'm trying to get the wacom digitizer working in 11.04. i'm following the tablet configuration article you mentioned above. When I run *xinput list* I don't get any mention of wacom at all. the panel is definitely working in the BIOS and was working before 11.04. I'll post the actual output once my tablet has finished installing updates.

[edit] here's the output:

```
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Device USB Device                           id=7    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=8    [slave  keyboard (3)]
    &#8627; Device USB Device                           id=6    [slave  keyboard (3)]

```

---

### Post by Favux on 2011-05-07
Hi grindboy,

Ok, the system doesn't seem to see your tablet/digitizer at all.  Which model is it?  You have the default Natty Wacom drivers installed?

---

### Post by grindboy on 2011-05-07
It's the motion m1400. Natty is literally the default install with updates run. System's also running very slowly so don't feel like you have to bust a gut helping me fix this as I think 10.04 is the practical limit for this tablet so I'll probably end up back there (shame I didn't think to image my hdd)

---

### Post by Favux on 2011-05-07
OK.  Plus Natty has the kernel power bug that drains the battery currently.  It's a high priority problem with kernels 2.6.38 and 2.6.39.  So a fix will probably appear in an update relatively soon.

Right now my guess is there is some problem with matching in the two serial snippets in the 50-wacom.conf.  Need to add a keyword for the Motion M1400 or something to one of the snippets in xorg.conf.d.  Or just add xorg.conf sections for the Motion along with a ServerLayout to the xorg.conf.

---

### Post by grindboy on 2011-05-07
I'll probably switch back to 10.04 in that case. Thanks again Favux :D

---

### Post by JunoBox on 2011-05-10
After upgrade to Natty, read favux mediawiki pages and created the file /etc/X11/xorg.conf.d/52-wacom-options.conf

```
Section "InputClass"
    Identifier "Wacom Bamboo stylus options"
        MatchDriver "wacom"
    MatchProduct "stylus"

        # Apply custom Options to this device below.
    Option "button1" "1"
    Option "button2" "3"
    Option "button3" "2"
EndSection

Section "InputClass"
    Identifier "Wacom Bamboo eraser options"
        MatchDriver "wacom"
        MatchProduct "eraser"

        # Apply custom Options to this device below.
    Option "button1" "1"
    Option "button2" "3"
    Option "button3" "2"
EndSection

Section "InputClass"
    Identifier "Wacom Bamboo cursor options"
        MatchDriver "wacom"
        MatchProduct "cursor"

        # Apply custom Options to this device below.
    Option "Button1" "1"
    Option "Button2" "3"
    Option "Button3" "2"
EndSection

Section "InputClass"
    Identifier "Wacom Bamboo pad options"
        MatchDriver "wacom"
        MatchProduct "pad"

        # Apply custom Options to this device below.
    Option "Button1" "key alt left"
    Option "Button2" "key ctrl alt left"
    Option "Button3" "key alt right"
    Option "Button4" "key ctrl alt right"
    Option "AbsWheelUp" "key up"
    Option "AbsWheelDown" "key down"
EndSection
```The options are not applied. See xorg.0.log:
```
[ 83483.526] (II) config/udev: Adding input device Wacom Bamboo (/dev/input/mouse0)
[ 83483.526] (II) No input driver/identifier specified (ignoring)
[ 83483.526] (II) config/udev: Adding input device Wacom Bamboo (/dev/input/event7)
[ 83483.526] (**) Wacom Bamboo: Applying InputClass "evdev tablet catchall"
[ 83483.526] (**) Wacom Bamboo: Applying InputClass "Wacom class"
[ 83483.526] (II) Using input driver 'wacom' for 'Wacom Bamboo'
[ 83483.526] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[ 83483.526] (**) Wacom Bamboo: always reports core events
[ 83483.526] (**) Option "Device" "/dev/input/event7"
[ 83483.560] (II) Wacom Bamboo: type not specified, assuming 'stylus'.
[ 83483.560] (II) Wacom Bamboo: other types will be automatically added.
[ 83483.560] (--) Wacom Bamboo stylus: using pressure threshold of 27 for button 1
[ 83483.560] (--) Wacom Bamboo stylus: Wacom USB Bamboo tablet maxX=14760 maxY=9225 maxZ=511 resX=100000 resY=100000  tilt=disabled
[ 83483.560] (II) Wacom Bamboo stylus: hotplugging dependent devices.
[ 83483.560] (**) Wacom Bamboo eraser: Applying InputClass "evdev tablet catchall"
[ 83483.560] (**) Wacom Bamboo eraser: Applying InputClass "Wacom class"
[ 83483.560] (II) Using input driver 'wacom' for 'Wacom Bamboo eraser'
[ 83483.560] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[ 83483.560] (**) Wacom Bamboo eraser: always reports core events
[ 83483.560] (**) Option "Device" "/dev/input/event7"
[ 83483.600] (--) Wacom Bamboo eraser: Wacom USB Bamboo tablet maxX=14760 maxY=9225 maxZ=511 resX=100000 resY=100000  tilt=disabled
[ 83483.630] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.1/usb7/7-2/7-2:1.0/input/input27/event7"
[ 83483.630] (II) XINPUT: Adding extended input device "Wacom Bamboo eraser" (type: ERASER)
[ 83483.630] (--) Wacom Bamboo eraser: top X=0 top Y=0 bottom X=14760 bottom Y=9225 resol X=100000 resol Y=100000
[ 83483.631] (**) Wacom Bamboo eraser: (accel) keeping acceleration scheme 1
[ 83483.631] (**) Wacom Bamboo eraser: (accel) acceleration profile 0
[ 83483.631] (**) Wacom Bamboo eraser: (accel) acceleration factor: 2.000
[ 83483.631] (**) Wacom Bamboo eraser: (accel) acceleration threshold: 4
[ 83483.640] (**) Wacom Bamboo cursor: Applying InputClass "evdev tablet catchall"
[ 83483.640] (**) Wacom Bamboo cursor: Applying InputClass "Wacom class"
[ 83483.640] (II) Using input driver 'wacom' for 'Wacom Bamboo cursor'
[ 83483.640] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[ 83483.640] (**) Wacom Bamboo cursor: always reports core events
[ 83483.640] (**) Option "Device" "/dev/input/event7"
[ 83483.650] (--) Wacom Bamboo cursor: Wacom USB Bamboo tablet maxX=14760 maxY=9225 maxZ=511 resX=100000 resY=100000  tilt=disabled
[ 83483.650] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.1/usb7/7-2/7-2:1.0/input/input27/event7"
[ 83483.650] (II) XINPUT: Adding extended input device "Wacom Bamboo cursor" (type: CURSOR)
[ 83483.650] (--) Wacom Bamboo cursor: top X=0 top Y=0 bottom X=14760 bottom Y=9225 resol X=100000 resol Y=100000
[ 83483.650] (**) Wacom Bamboo cursor: (accel) keeping acceleration scheme 1
[ 83483.650] (**) Wacom Bamboo cursor: (accel) acceleration profile 0
[ 83483.650] (**) Wacom Bamboo cursor: (accel) acceleration factor: 2.000
[ 83483.650] (**) Wacom Bamboo cursor: (accel) acceleration threshold: 4
[ 83483.651] (**) Wacom Bamboo pad: Applying InputClass "evdev tablet catchall"
[ 83483.651] (**) Wacom Bamboo pad: Applying InputClass "Wacom class"
[ 83483.651] (II) Using input driver 'wacom' for 'Wacom Bamboo pad'
[ 83483.651] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[ 83483.651] (**) Wacom Bamboo pad: always reports core events
[ 83483.651] (**) Option "Device" "/dev/input/event7"
[ 83483.654] (--) Wacom Bamboo pad: Wacom USB Bamboo tablet maxX=14760 maxY=9225 maxZ=511 resX=100000 resY=100000  tilt=disabled
[ 83483.654] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.1/usb7/7-2/7-2:1.0/input/input27/event7"
[ 83483.654] (II) XINPUT: Adding extended input device "Wacom Bamboo pad" (type: PAD)
[ 83483.654] (**) Wacom Bamboo pad: (accel) keeping acceleration scheme 1
[ 83483.654] (**) Wacom Bamboo pad: (accel) acceleration profile 0
[ 83483.654] (**) Wacom Bamboo pad: (accel) acceleration factor: 2.000
[ 83483.654] (**) Wacom Bamboo pad: (accel) acceleration threshold: 4
[ 83483.654] (II) Wacom Bamboo stylus: hotplugging completed.
[ 83483.661] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.1/usb7/7-2/7-2:1.0/input/input27/event7"
[ 83483.661] (II) XINPUT: Adding extended input device "Wacom Bamboo stylus" (type: STYLUS)
[ 83483.661] (--) Wacom Bamboo stylus: top X=0 top Y=0 bottom X=14760 bottom Y=9225 resol X=100000 resol Y=100000
[ 83483.661] (**) Wacom Bamboo stylus: (accel) keeping acceleration scheme 1
[ 83483.661] (**) Wacom Bamboo stylus: (accel) acceleration profile 0
[ 83483.661] (**) Wacom Bamboo stylus: (accel) acceleration factor: 2.000
[ 83483.661] (**) Wacom Bamboo stylus: (accel) acceleration threshold: 4

```What I'm doing wrong?

---

### Post by Favux on 2011-05-10
Hi JunoBox,

Don't know, that looks basically right to me.

Now these Options for the stylus:
```
    Option "button1" "1"
    Option "button2" "3"
    Option "button3" "2"
```
are the current driver default.  So maybe that's part of the problem?  You don't need to respecify driver defaults.  You'd only use those Options if changing the Button2 or 3 assignments.  I don't know if button is case specific and wants to see B not b.

Right now there is a problem with Button4 thru 7 being reserved for scroll they haven't fixed.  So your Button4 may actually be 8.  I thought the scroll wheels were working.  Are up and down valid assignments?

I'm wondering a little about:
```
[ 83483.526] (II) Using input driver 'wacom' for 'Wacom Bamboo'
```
because I'm not seeing an input class for stylus.  But otherwise we see the input class for eraser, cursor, and pad.  So dependent device configuration in the 52-wacom-options seems recognized.  Are you using the default 50-wacom.conf?  Are you using any xsetwacom configuration?

---

### Post by xheyther on 2011-05-10
Hello there,

I just bought a Bamboo pen&touch and it works quite well with natty. The thing that bother me is that Gimp seems to misses some stroke from time to time (Inkscape doesn’t miss anything). It can happens more that 50% of the times or less frequently it's somewhat random.

I wasn't able to find any help on that but not being a native English speaker may render my queries ineffective.

Hope someone can help me.

Cheers !

---

### Post by JunoBox on 2011-05-11
> **Favux said:**
> Hi JunoBox,

Don't know, that looks basically right to me.

Now these Options for the stylus:
```
    Option "button1" "1"
    Option "button2" "3"
    Option "button3" "2"
```are the current driver default.  So maybe that's part of the problem?  You don't need to respecify driver defaults.  You'd only use those Options if changing the Button2 or 3 assignments.  I don't know if button is case specific and wants to see B not b.

Right now there is a problem with Button4 thru 7 being reserved for scroll they haven't fixed.  So your Button4 may actually be 8.  I thought the scroll wheels were working.  Are up and down valid assignments?

I'm wondering a little about:
```
[ 83483.526] (II) Using input driver 'wacom' for 'Wacom Bamboo'
```because I'm not seeing an input class for stylus.  But otherwise we see the input class for eraser, cursor, and pad.  So dependent device configuration in the 52-wacom-options seems recognized.  Are you using the default 50-wacom.conf?  Are you using any xsetwacom configuration?

The b or B in Button option doesn't matter. Both work.
The options I use to switch button 2 and 3 are not the default for the driver. That's why I switch them.
Up and Down options are valid for xsetwacom tool, but it will not be recognized by the driver as specified in the conf file. The driver seems far from complete to me....

The pad buttons are really strange.
When I don't put any options in the pad section then I see this in the log:
```
[ 78736.581] (**) Wacom Bamboo pad: Applying InputClass "evdev tablet catchall"
[ 78736.581] (**) Wacom Bamboo pad: Applying InputClass "Wacom class"
[ 78736.581] (**) Wacom Bamboo pad: Applying InputClass "Wacom Bamboo pad options"
[ 78736.581] (II) Using input driver 'wacom' for 'Wacom Bamboo pad'
[ 78736.581] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[ 78736.581] (**) Wacom Bamboo pad: always reports core events
[ 78736.581] (**) Option "Device" "/dev/input/event6"
[B][ 78736.590] (WW) Option "Button1" requires an integer value
[ 78736.590] (WW) Option "Button2" requires an integer value
[ 78736.590] (WW) Option "Button3" requires an integer value
[ 78736.590] (WW) Option "Button4" requires an integer value[/B]
[ 78736.590] (--) Wacom Bamboo pad: Wacom USB Bamboo tablet maxX=14760 maxY=9225 maxZ=511 resX=100000 resY=100000  tilt=disabled
[ 78736.600] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.1/usb7/7-2/7-2:1.0/input/input27/event6"
[ 78736.600] (II) XINPUT: Adding extended input device "Wacom Bamboo pad" (type: PAD)
[ 78736.600] (**) Wacom Bamboo pad: (accel) keeping acceleration scheme 1
[ 78736.600] (**) Wacom Bamboo pad: (accel) acceleration profile 0
[ 78736.600] (**) Wacom Bamboo pad: (accel) acceleration factor: 2.000
[ 78736.600] (**) Wacom Bamboo pad: (accel) acceleration threshold: 4

```See bold section. If I set explicit the options like:
Option "Button1" "1"
or
Option "Button1" 1
It's keeping the warning.

I using the default 50-wacom.conf file.

With xsetwacom tool I can set the pad buttons to the key assigments and also set the correct button behavior for the stylus. But I really want to get it working as hot plugging. I hate to run every time a script file to get the things working as it should.

Does the driver contains bugs? And where can I find new updates of the driver?

---

### Post by Favux on 2011-05-11
It sure looks like you've found a bug.  So the question is where is it?  Is it in xf86-input-wacom?  Or is the X server 1.10 not allowing configuration of dependent devices (the pad) the way it should and is suppose to?  I haven't tested this for myself yet.  I'll try to get to it soon.

The switch to the assignment of 3 to Button 2 and 2 to Button 3 was made months ago by user request.  So if that is no longer the default then there has been an inadvertent reversion to the old default.  Or at least I do not remember them doing that deliberately.  There has been a ton of work trying to straighten out button issues so that wouldn't surprise me terribly.  They still don't have it quite ironed out.  Hence the Button 4 is actually 8 deal.

You can get the tars here:  [http://sourceforge.net/projects/linuxwacom/files/](http://sourceforge.net/projects/linuxwacom/files/)

Or you can clone the xf86-input-wacom git repository by following the instructions for that in the [linuxwacom HOW TO]("http://ubuntuforums.org/showthread.php?t=1038949") or the [Bamboo Pen and Touch HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").

---

### Post by JunoBox on 2011-05-14
> **Favux said:**
> It sure looks like you've found a bug.  So the question is where is it?  Is it in xf86-input-wacom?  Or is the X server 1.10 not allowing configuration of dependent devices (the pad) the way it should and is suppose to?  I haven't tested this for myself yet.  I'll try to get to it soon.

The switch to the assignment of 3 to Button 2 and 2 to Button 3 was made months ago by user request.  So if that is no longer the default then there has been an inadvertent reversion to the old default.  Or at least I do not remember them doing that deliberately.  There has been a ton of work trying to straighten out button issues so that wouldn't surprise me terribly.  They still don't have it quite ironed out.  Hence the Button 4 is actually 8 deal.

You can get the tars here:  [http://sourceforge.net/projects/linuxwacom/files/](http://sourceforge.net/projects/linuxwacom/files/)

Or you can clone the xf86-input-wacom git repository by following the instructions for that in the [linuxwacom HOW TO]("http://ubuntuforums.org/showthread.php?t=1038949") or the [Bamboo Pen and Touch HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").

I have a workaround to set the options for the stylus:
If the section in the 50-wacom.conf being put into the 52-wacom-options.conf file then this will override the original section.
So remove the "stylus" section from the 52-wacom-options.conf file and insert the following section:
```
Section "InputClass"
    Identifier "Wacom class"
# WALTOP needs a patched kernel driver, that isn't in mainline lk yet,
# so for now just let it fall through and be picked up by evdev instead.
#    MatchProduct "Wacom|WALTOP|WACOM"
    MatchProduct "Wacom|WACOM|Hanwang"
    MatchDevicePath "/dev/input/event*"
    Driver "wacom"
    Option "Button1" "1"
    Option "Button2" "3"
    Option "Button3" "2"
EndSection

```

Second:
The "pad" will not accept key definitions through xorg configuration. That's a bug / missing feature.
But when I set the buttons for the pad with xsetwacom tool then they work ok. But this will only work for a very short moment. After I make use of the buttons (or scroll pad), it will not react anymore. This sounds to me as a bug.
I test it with the following command:
xinput test "Wacom Bamboo pad"
You get something like:
button press   1 a[3]=0 a[4]=0 a[5]=0 
motion a[3]=0 a[4]=0 a[5]=0 
button release 1 a[3]=0 a[4]=0 a[5]=0 

But then it stops suddenly. To get it working again I need to do unplug/plug-in the Bamboo again and run the xsetwacom commands. But soon after I used the pad again, it stops. The stylus, etc keeps working.

Hopefully this will be fixed very soon.

---

### Post by Favux on 2011-05-15
Hi JunoBox,

That was my mistake.  The static configuration files xorg.conf or xorg.conf.d (or the .fdi file for that matter) have never allowed anything but integer values assigned to pad Buttons as described in *man wacom*.  Only xsetwacom commands allow you to set keystrokes to pad Buttons.  I've updated [xorg.conf.d]("https://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xorg.conf.d") to reflect that.  Thank you for bringing that gaffe to my attention!

Regarding configuring the stylus in 52-wacom-options.conf.  It turns out that the parent device has to be handled differently.  If I treat it as a a tablet wide setting it works.  So think of it as the tablet/stylus.  Guessing from your xorg.0.log the stylus "device name" is "Wacom Bamboo stylus" in the *xinput list* output.  Which would make the parent device name "Wacom Bamboo".  So if you change the match from:
```

    Identifier "Wacom Bamboo stylus options"
    MatchDriver "wacom"
    MatchProduct "stylus"
```
to:
```

    Identifier "Wacom Bamboo stylus options"
    MatchDriver "wacom"
    MatchProduct "Wacom Bamboo"
```
it should work.  It does for me anyway.  Rather than importing the match from 50-wacom.conf and using the wacom driver line again which we'd prefer to avoid.

I'd appreciate if you would test that for me.  I need to discuss this with the dev.s because I think this behavior is different from what we expected with X server 1.10 and we probably need to get to the bottom of it.

The pad buttons failing after a little while could also be hardware related I suppose.  Make sure your USB connection is good on both ends and the usb port is supplying enough power/voltage.  If it weren't for the stylus still working I would think you are describing a hot plug event.  If the connection was dropped the xsetwacom pad button settings wouldn't last through a hotplug event.  You would need to reapply the xsetwacom commands again or use a monitor daemon or the Wdaemon.

---

### Post by JunoBox on 2011-05-15
Hi Favux,

I tried already if MatchProduct "Wacom Bamboo" was the solution, but it will not see it as "Wacom Bamboo" product. MatchProduct match never with the "stylus". Whatever you enter as value.

The hardware is not malfunction. The same system (and other systems) and Bamboo just working fine with Ubuntu 10.10 when I use xsetwacom. It will not loose the pad configuration in that setup. The problem must be in the Ubuntu 11.04 Xorg and/or wacom driver. It looks if Xorg or wacom driver stops processing the pad events for some reason. When I get the pad button configuration with xsetwacom tool, then it still keeps saying the correct keys are assigned.
I tested also with graphire4. The pad buttons also stops working after it is used once after I set some keys to it with xsetwacom. This happens with Ubuntu 11.04. Not with 10.x

Hopefully you and the dev's can find something to fix this.

---

### Post by Favux on 2011-05-15
Thanks, that's important info.  I may have already seen that but I was so focused on the parent device match I didn't pay much attention.

Can you post your output of *xinput list* please?  If you're willing I would like to see if there is another match or two we could try.

---

### Post by JunoBox on 2011-05-15
here's the output of xinput list:
```
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo eraser                         id=11    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo cursor                         id=12    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo pad                            id=13    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo stylus                         id=14    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=16    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Generic Mouse                          id=17    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; HID 413c:8157                               id=9    [slave  keyboard (3)]
    &#8627; Laptop_Integrated_Webcam_2M                 id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=15    [slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                            id=18    [slave  keyboard (3)]

```

---

### Post by Favux on 2011-05-15
Great!

Ok, it'll help if I explain my situation.  I have one of the newer Bamboo Pen and Touch tablets.  What that means is the kernel exports two kernel parent devices, the stylus and touch.  The dependent device for stylus is the eraser and for touch it is the pad.  Now for your Bamboo there will be only one parent device the stylus.  And the dependent devices are the "eraser", "cursor", and "pad".  And you say those dependent device matches work for you, correct?

Actually the two parent device names are exported as (shown in xinput list):
```
"Wacom Bamboo 2FG 4x5 Pen stylus"
and
"Wacom Bamboo 2FG 4x5 Finger touch"
```
If I try to match to "stylus" or "touch" or the entire "device name" using *MatchDriver "wacom"* it doesn't work.  But it does if I use what turns out to be the parent "device name" which appears to be Pen or Finger:
```
	MatchProduct "Wacom Bamboo 2FG 4x5 Pen"
or
	MatchProduct "Pen"
and
	MatchProduct "Wacom Bamboo 2FG 4x5 Finger"
or
	MatchProduct "Finger"
```
That seems to leave us with three keywords for you given that you're seeing:
> Wacom Bamboo stylus
We already know "stylus" doesn't work nor does "Wacom Bamboo".  Does "Wacom Bamboo stylus", "Bamboo", or "Wacom" work?

---

### Post by JunoBox on 2011-05-15
I tried already all the possible combinations of the keywords ;-)
But it will not match.

The other three dependent devices ("eraser", "cursor", and "pad") will match.

---

### Post by Favux on 2011-05-15
Alright, disappointing but very useful information.

So is that just your particular tablet model?  Or is it the other way and only because of the uniqueness of tablets with usb touch I can do the match?

If you are the general case then the choices become limited.  Add the tablet/stylus Options in the 50-wacom.conf.  Not real satisfactory because that is a distribution file.  Or have to repeat the general tablet/stylus match with the wacom driver line in the 52-wacom-options.conf.  Again not so ideal.

On to looking at the button issue.

---

### Post by Favux on 2011-05-17
Hi JunoBox,

I'm not seeing the pad button issue.  The BambooPT's like mine export touch from the kernel as a separate device and pad is a dependent of touch rather than the stylus as is the usual situation, like with your Bamboo.  So that might be making a difference.  Also the default Button mappings for the BambooPT are a little out there so that might be involved too.

There are already a couple of Launchpad bugs that may be related to your problem:
[https://bugs.edge.launchpad.net/ubuntu/+source/xf86-input-wacom/+bug/782756](https://bugs.edge.launchpad.net/ubuntu/+source/xf86-input-wacom/+bug/782756)
[https://bugs.edge.launchpad.net/ubuntu/+source/xf86-input-wacom/+bug/769477](https://bugs.edge.launchpad.net/ubuntu/+source/xf86-input-wacom/+bug/769477)

It's looking possible that this might be a Ubuntu Natty specific problem and not xf86-input-wacom, at least directly.

---

### Post by Gilbrilthor on 2011-06-27
I've decided to give my old wacom a try on Ubuntu(Natty). I've got it working in Ubuntu and inkscape uses it without a hitch. Gimp, however, has a problem that makes it nigh unusable. Every time I draw a line with pressure sensitivity activated, the brush stays at the end of my line even when I pick up the stylus. When I go to draw my next line, it is as if I am not even touching the pad at all. After I pick up my stylus again, the brush (i guess) resets itself and I can draw another line. This process repeats every time, so I get about half of my lines drawn. Any help on this would be much appreciated. 

Sorry, pretty new at this tablet thing and Ubuntu. If you need more info, just ask. I have no idea what to include in one of these things :)

---

### Post by Favux on 2011-06-27
Hi Gilbrilthor,

Welcom to Ubuntu forums!

I think that is a Unity bug that is discussed on another thread.  When you boot up Natty, at the log-in screen, there should be an option on the bottom for classic mode.  Choose that and see if the problem goes away in Gimp.

---

### Post by Gilbrilthor on 2011-06-27
Thanks Favux for the quick reply!

I first tried it in classic, which didn't fix the problem. I then tried classic with no effects and the problem went away. So I have no idea why that would affect it, but I am happy that I can now use my tablet in linux. Sorry if I posted in the wrong thread, I didn't even know what to call my problem :D

---

### Post by Favux on 2011-06-27
Hi Gilbrilthor,

Great!   You're fine, this was one of the correct threads to post to.  And your discovered yourself no effects.  My fault, I forgot to mention that.

Presumably the problem has something to do with the Unity plug-in to Compiz for Natty.  Hopefully they'll fix it shortly.

---

### Post by norman@littletank.org on 2011-07-01
I have just installed 11.04 and like many others my Wacom Bamboo MTE450 tablet will not work as it did in 9.04 and 9.10. 2 years ago the script given below was written for me which I used successfully until I upgraded and I wondered what I needed to change or modify to suit 11.04. The pen seems to be OK but the buttons on the pad do not respond.

Thanks in advance   Norman

#!/bin/bash

# If you set XSW in your environment it will override the
# script's default of /usr/bin/xsetwacom.
# If you set PAD and/or STYLUS then those override the script's
# defaults of 'Wacom Bamboo pad' and 'Wacom Bamboo' which are
# known correct for Ubuntu 9.04

# ------8<------[ Do not change this bit: ]-------------------

test "x$XSW" = "x" && XSW=/usr/bin/xsetwacom
test -x $XSW || { echo "Cannot find xsetwacom in /usr/bin"; exit 1; }

test "x$PAD" = "x" && PAD="Wacom Bamboo pad"
test "x$STYLUS" = "x" && STYLUS="Wacom Bamboo"

pad () {
  $XSW set "$PAD" "$@"
}

stylus () {
  $XSW set "$STYLUS" "$@"
}

# ------8<------[ Configurability from here down. ]-----------

# Define the Bamboo buttons
#
pad AbsWDn "CORE KEY + "		# circle zoom out
pad AbsWUp "CORE KEY - "		# circle zoom in
pad Button1 "CORE KEY CTRL /z"		# key 1 (<)	undo
pad Button2 "CORE KEY  CTRL"		# key 2 (FN1) CTRL
pad Button3 "CORE KEY SHIFT CTRL /e"	# key 3 (>) fill frame
pad Button4 "CORE KEY  SHIFT"		# key 4 (FN2) SHIFT

stylus TPCButton "off"			# side switch mode
stylus mode "Absolute"			# positioning mode
stylus Button1 "Button 1"		# pentip click left
stylus Button2 "Core Key x"		# Lower side switch Fg/Bg -> Bg/Fg
stylus Button3 "Button 2"		# Upper side switch click middle

---

### Post by lile001 on 2011-07-05
I've successfully got a Wacom Intuos 3 working under Ubuntu 10.04.  This is amazing, since like Murphy usually I find some way to goof it up.  

I've been searching through this thread and [https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom) for a while, but haven't been able to get the full jist of configuration.  Here is what I would like to do:

1.  Map one of the input buttons to middle click 
2. Map another one of the buttons to right click
3. Enable the touchpad area so I can use it to scroll. 
4. Disable the buttons on the pen since I only hit them by accident. 

I am sure I have stared right at these instructions and not recognized what I was looking at, since discussions like these usually get pretty geeky really fast.  How would I accomplish these tasks?

---

### Post by Favux on 2011-07-05
Hi lile001,

You want to begin by entering *xinput list* in a terminal.  That will tell you the "device names" you need to use in *xsetwacom set* commands.  See the Linux Wacom Project's mediawiki page [Tablet Configuration]("http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration#Intuos3").

I don't know if you can disable the stylus side buttons by setting them to O with xsetwacom.  But you can using an option in 10-wacom.conf in xorg.conf.d I think, since it works for pad buttons.

---

### Post by lile001 on 2011-07-05
> **Favux said:**
> Hi lile001,

You want to begin by entering *xinput list* in a terminal.  That will tell you the "device names" you need to use in *xsetwacom set* commands.  See the Linux Wacom Project's mediawiki page [Tablet Configuration]("http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration#Intuos3").

I don't know if you can disable the stylus side buttons by setting them to O with xsetwacom.  But you can using an option in 10-wacom.conf in xorg.conf.d I think, since it works for pad buttons.

Well, let's slow down.  I understood about half of the very helpful and intelligent stuff you said there, since I am completely and totally dense and a hopeless N00b.  

I am able to get this list of devices using xinput list (THANKS!) , but if I understand correctly, xsetwacom is used for setting things in only one session.  I'd like to put these options into xorg.conf.d (I think) so that the options are set every time I boot up.  I can edit the file, but I am not sure what to put in there.  
There is something [here]("http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xorg.conf.d") about typing this kind of stuff into the xorg.conf.d

     Option "Button2" "3"

however I have yet to come across anything that says which tablet button corresponds to "Button2".  The
Sourceforge HOW-TO blither seems to assume I already know how all this stuff works instead of explaining it 
from the get-go. Having read that and come away none the wiser, I am now asking here.  

I am guessing that the "3" comes from this xinput list? This doesn't 
make much sense yet, since in my list, "3" is a Virtual Core Keyboard.  


Am I on the right track?  are there some OPTION settings in xorg.conf.d that would achieve what I was trying to do?

---

### Post by Favux on 2011-07-05
> xsetwacom is used for setting things in only one session. I'd like to put these options into xorg.conf.d (I think) so that the options are set every time I boot up.
For the pad or tablet buttons you have to use xsetwacom commands.  This is because only starting with X Server 1.10 can you configure dependent devices in a .conf file in xorg.conf.d.  Lucid's default X Server is 1.7, so you can only configure the parent device or tablet wide settings.  Which in practice is the stylus.  And the eraser, and pad are dependent devices of the tablet/stylus.

1 = left click = stylus tip by default, so leave that one alone
2 = middle click
3 = right click

So:
```

Option "Button2" "0"
Option "Button3" "0

```
in xorg.conf.d should shut off your two stylus side buttons.

So what you do is put the xsetwacom commands in a file named whatever.sh and then right click on it and in Properties chose the Permissions tab and make the file executable.  Then you add the executable .sh file to your Startup Applications in Preferences.  That way the xsetwacom commands apply every time you boot.

---

### Post by lile001 on 2011-07-05
> **Favux said:**
> For the pad or tablet buttons you have to use xsetwacom commands. 

So what you do is put the xsetwacom commands in a file named whatever.sh and then right click on it and in Properties chose the Permissions tab and make the file executable.  Then you add the executable .sh file to your Startup Applications in Preferences.  That way the xsetwacom commands apply every time you boot.

OK, I'm not really getting the xsetwacom commands yet.  If I understand what you are talking about, i should just be able to type this into a terminal:
[INDENT]xsetwacom set "Wacom Intuos3 6x8 pad" Button 1 3
[/INDENT]which produces this:
[INDENT]Unknown parameter name 'Button'.

[/INDENT]Obviously I am still not getting this.  So here are two very specific questions:

1.  What exactly am I supposed to type into the executable .sh file to change one of the buttons to a right click? (would this also work in a terminal?)

2. Which "Button" maps to which key on the Wacom tablet?  Or do I just blindly try them until I guess the right one?

---

### Post by Favux on 2011-07-05
You're pretty much there.  The wiki is showing the new parameter names for xsetwacom:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xsetwacom](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xsetwacom)  But since you are using Lucid which has as default xf86-input-wacom-0.10.5 you use the old parameter name for buttons, i.e. Button1 not Button 1.
> xsetwacom set "Wacom Intuos3 6x8 pad" Button1 "3"
This should make your first pad button a right click.  By the way xf86-input-wacom-0.10.5 is in the package Ubuntu calls xserver-xorg-input-wacom.

> 1. What exactly am I supposed to type into the executable .sh file to change one of the buttons to a right click? (would this also work in a terminal?)

Right, you apply xsetwacom commands in a terminal.  By using .sh file, call it say xsetwacom.sh, you are telling the system to run the contents as shell commands so the contents are the xsetwacom commands in a terminal that do what you want done.  So if the above command works then in xsetwacom.sh you'd enter it exactly the same:
```
xsetwacom set "Wacom Intuos3 6x8 pad" Button1 "3"
```

> 2. Which "Button" maps to which key on the Wacom tablet? Or do I just blindly try them until I guess the right one? 
Either they go pretty much in order as the wiki shows or maybe buttons 4 to 7 are reserved for vertical and horizontal scroll.  So in that case Button4 becomes Button8 and the rest of the buttons are also offset by 4.

See what's happening is when they split the linuxwacom package into two separate pieces, the kernel driver and the X driver, rather than packaging them together, Xorg took over the X driver and renamed it xf86-input-wacom.  And xsetwacom was rewritten for the "new" driver.  Since Lucid's 0.10.5 is early in the process a lot of stuff is broken or doesn't work right.  The xf86-input-wacom-0.10.x series was suppose to be code clean up and simplification and not really to be used by users.  The first version that was suppose to be widely tested by users just came out, 0.11.0.  Unfortunately since linuxwacom doesn't work for X Server 1.7 and higher they didn't have a choice and so you have 0.10.x versions in Lucid, Maverick, and Natty.  Making a major pain for users.  But things have settled down again.  Most things are fixed and they are even adding functions back in.

---

### Post by lile001 on 2011-07-05
> **Favux said:**
>   So if the above command works then in xsetwacom.sh you'd enter it exactly the same:
```
xsetwacom set "Wacom Intuos3 6x8 pad" Button1 "3"
```


Hmm, I must have something very basic wrong.  When I enter this command, the buttons on the Wacom tablet always sets the focus to the "Panel" menu bar at the top of the screen, and right clicks on it, not in the window that I am pointing at.  Assuming I have done something so stupid Murphy wouldn't have even thought of it, what could this be?

---

### Post by lile001 on 2011-07-05
> **lile001 said:**
> Hmm, I must have something very basic wrong.  When I enter this command, the buttons on the Wacom tablet always sets the focus to the "Panel" menu bar at the top of the screen, and right clicks on it, not in the window that I am pointing at.  Assuming I have done something so stupid Murphy wouldn't have even thought of it, what could this be?

I was also successful in getting the touchpads to always control the "Panel" menu bar on the desktop.  However, none of the controls on the Wacom seem to pay attention to the window in focus.  They always cause the focus to jump to the "Panel" menu.  

:confused:

---

### Post by Favux on 2011-07-05
Alright.  Post the output of *xinput list* and *xsetwacom list*.

---

### Post by lile001 on 2011-07-07
> **Favux said:**
> Alright.  Post the output of *xinput list* and *xsetwacom list*.
Xsetwacom list and xinput list output is attached. I rebooted before doing this, which IIRC should remove any of the random settings that I was experimenting with to try to get any of this to work.

---

### Post by Favux on 2011-07-07
OK, the outputs look good.
> &#9116;   &#8627; Wacom Intuos3 6x8 eraser                	id=8	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos3 6x8 cursor                	id=9	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos3 6x8 pad                   	id=10	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos3 6x8                       	id=11	[slave  pointer  (2)]
> Wacom Intuos3 6x8 eraser ERASER    
Wacom Intuos3 6x8 cursor CURSOR    
Wacom Intuos3 6x8 pad PAD       
Wacom Intuos3 6x8 STYLUS 
The tablet is on the wacom drivers and you are using the correct "device name" for pad in the xsetwacom command.

When you say:
> the buttons on the Wacom tablet always sets the focus to the "Panel" menu bar at the top of the screen, and right clicks on it, not in the window that I am pointing at.
Are you saying the pointer arrow jumps up to the top or top left of the screen?

---

### Post by lile001 on 2011-07-07
> **Favux said:**
> OK, the outputs look good.


The tablet is on the wacom drivers and you are using the correct "device name" for pad in the xsetwacom command.

When you say:

Are you saying the pointer arrow jumps up to the top or top left of the screen?

Yes, when I press any of the buttons, the mouse pointer jumps to the top left corner of the screen.  If the button is set to click, then it clicks there, and if the button is set to right click, it right clicks up there.

---

### Post by Favux on 2011-07-07
The reason I've been avoiding saying cursor is that cursor in linuxwacom lingo means the Wacom tablet mouse.  However since everyone uses cursor for pointer arrow...

Shoot, you have a cursor jump bug.  We just finished fixing one for an Oneiric Launchpad bug report.  But that bug was kernel side and your Lucid 2.6.32 kernel doesn't have that problem.  As I recall you have an old bug where the driver was confused about the pad being Relative or Absolute.  That was fixed fairly quickly so I think xf86-input-wacom-0.10.8 or later has the fix:  [http://sourceforge.net/projects/linuxwacom/files/xf86-input-wacom/](http://sourceforge.net/projects/linuxwacom/files/xf86-input-wacom/)

In other words you'll have to upgrade your xf86-input-wacom from 0.10.5 to 0.10.8 or later.  Ubuntu has xf86-input-wacom in the xserver-xorg-input-wacom package.  0.10.8 still has the same xsetwacom parameter names pretty much so you won't have to change your xsetwacom commands.  You should skip 0.10.9 and 0.10.10 because they had other pad bugs.  With 0.10.11 or later you'd have to use the new parameter names.

So you'll have to compile a newer xf86-input-wacom to fix things or install say Irie Shinsuke's PPA.  Which also changes your default wacom.ko (the usb kernel driver) to input-wacom's wacom.ko.  The PPA link is above part I. on the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562") and how to compile a xf86-input-wacom tar is in part II. a) and b).  You'll have to change the version number to the one you selected.

Good luck!

---

### Post by lile001 on 2011-07-08
> **Favux said:**
>   That was fixed fairly quickly so I think xf86-input-wacom-0.10.8 or later has the fix:  [http://sourceforge.net/projects/linuxwacom/files/xf86-input-wacom/](http://sourceforge.net/projects/linuxwacom/files/xf86-input-wacom/)

In other words you'll have to upgrade your xf86-input-wacom from 0.10.5 to 0.10.8 or later.  Ubuntu has xf86-input-wacom in the xserver-xorg-input-wacom package.  0.10.8 still has the same xsetwacom parameter names pretty much so you won't have to change your xsetwacom commands.  You should skip 0.10.9 and 0.10.10 because they had other pad bugs.  With 0.10.11 or later you'd have to use the new parameter names.

So you'll have to compile etc etc

Good luck!

Holy crap!  I'm way in over my head.  How the heck do i compile this stuff? I just downloaded a tarball with a bunch of gibberish in it.  The heck with it, Ubuntu doesn't talk nice to tablets and I've been screwed.  I'll just sit a mouse next to the darned tablet and stab the right click button on that.  This is nuts!

---

### Post by norman@littletank.org on 2011-07-09
I am rapidly coming to q similar conclusion as yourself. My interest is in photography and, in my opinion, to be able to use the stylus with variable pressure is a most valuable asset. Therefore, as long as my stylus works I am prepared to forgo the buttons on the tablet and to use my keyboard instead.

---

### Post by lile001 on 2011-07-11
> **Favux said:**
> 

In other words you'll have to upgrade your xf86-input-wacom from 0.10.5 to 0.10.8 or later.  Ubuntu has xf86-input-wacom in the xserver-xorg-input-wacom package.  0.10.8 still has the same xsetwacom parameter names pretty much so you won't have to change your xsetwacom commands.  You should skip 0.10.9 and 0.10.10 because they had other pad bugs.  With 0.10.11 or later you'd have to use the new parameter names.

So you'll have to compile a newer xf86-input-wacom to fix things or install say Irie Shinsuke's PPA.  Which also changes your default wacom.ko (the usb kernel driver) to input-wacom's wacom.ko.  The PPA link is above part I. on the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562") and how to compile a xf86-input-wacom tar is in part II. a) and b).  You'll have to change the version number to the one you selected.

Good luck!

Oops! Wrong answer.  "You'll need to upgrade to the latest version of Ubuntu" is the correct answer.  I am always amazed when people identify the absolute most difficult way to solve a problem, when there is a blindingly easy way, that even a forehead-slapping N00B like myself can accomplish.  The packages recommended here, if I am not mistaken, are included in the latest version, while I am using 10.04 Lucid Lynx, one year out of date.   Upgrade in process now, I'll post if this works.

---

### Post by norman@littletank.org on 2011-07-12
> **lile001 said:**
> Oops! Wrong answer.  "You'll need to upgrade to the latest version of Ubuntu" is the correct answer.  I am always amazed when people identify the absolute most difficult way to solve a problem, when there is a blindingly easy way, that even a forehead-slapping N00B like myself can accomplish.  The packages recommended here, if I am not mistaken, are included in the latest version, while I am using 10.04 Lucid Lynx, one year out of date.   Upgrade in process now, I'll post if this works.

I do not believe that this is the answer. I am running a fully up to date Ubuntu 11.04 and I have the same problem with the pointer.

---

### Post by Favux on 2011-07-12
Hi Norman,

The Bamboo Pen support either somehow got lost or was never submitted to the kernel's linux-input.  However someone I don't recognize did submit it to linux-input in February 2011.  I thought that was in time for support for the Pen to be in Natty's 2.6.38 kernel, but maybe not.  But he got the pressure levels for the Pen wrong anyway, somehow using 256, so you'd still have to fix it.

I discovered that responding to some bug reports.  To make matters worse the Wacom site specification claimed 512 pressure levels for the Pen.  But my tester reported that was still wrong and that the Pen has 1024 levels like the other Bamboo Pen and Touches.  Ping and I submitted the fix for that to linux-input so the wacom.ko in Oneiric's 3.0 or whatever kernel will support the Bamboo Pen correctly.

In the meantime the input-wacom's wacom.ko does have the correct Bamboo Pen support.

So you can either install Irie's PPA, which takes only a few lines to do for editing Software Sources, with the instructions on the site. Or you can compile input-wacom as the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562") shows you how.  I just looked at Irie's PPA and while it is about 4 to 6 weeks out of date it should work.  And if you chose to compile you should probably use the latest xf86-input-wacom tar also.

---

### Post by lile001 on 2011-07-12
> **norman@littletank.org said:**
> I do not believe that this is the answer. I am running a fully up to date Ubuntu 11.04 and I have the same problem with the pointer.

Ya I am still having the same problem too on 11.04. Nice try.  Forget it, tablets don't work right in Ubuntu, at least for us normal mortals, and all this geeky stuff to remap the buttons is useless.  They work fine as pointers.  

There is actually a GUI for this!  It doesn't work in Ubuntu 11.04 yet, but apparently works in Ubunto 10.10.  According to the comments some people are having luck with it.  

[http://www.ubuntugeek.com/wacom-control-panel-easily-configure-wacom-tablet.html/comment-page-1#comment-106273](http://www.ubuntugeek.com/wacom-control-panel-easily-configure-wacom-tablet.html/comment-page-1#comment-106273)

Meanwhile, the mouse stays next to the tablet in case I need a right click [Grrrr.]  :(

---

### Post by lile001 on 2011-07-19
> **Favux said:**
> The reason I've been avoiding saying cursor is that cursor in linuxwacom lingo means the Wacom tablet mouse.  However since everyone uses cursor for pointer arrow...

Shoot, you have a cursor jump bug.  We just finished fixing one for an Oneiric Launchpad bug report.  But that bug was kernel side and your Lucid 2.6.32 kernel doesn't have that problem.  As I recall you have an old bug where the driver was confused about the pad being Relative or Absolute.  That was fixed fairly quickly so I think xf86-input-wacom-0.10.8 or later has the fix:  [http://sourceforge.net/projects/linuxwacom/files/xf86-input-wacom/](http://sourceforge.net/projects/linuxwacom/files/xf86-input-wacom/)

In other words you'll have to upgrade your xf86-input-wacom from 0.10.5 to 0.10.8 or later.  Ubuntu has xf86-input-wacom in the xserver-xorg-input-wacom package.  0.10.8 still has the same xsetwacom parameter names pretty much so you won't have to change your xsetwacom commands.  You should skip 0.10.9 and 0.10.10 because they had other pad bugs.  With 0.10.11 or later you'd have to use the new parameter names.

So you'll have to compile a newer xf86-input-wacom to fix things or install say Irie Shinsuke's PPA.  Which also changes your default wacom.ko (the usb kernel driver) to input-wacom's wacom.ko.  The PPA link is above part I. on the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562") and how to compile a xf86-input-wacom tar is in part II. a) and b).  You'll have to change the version number to the one you selected.

Good luck!


Alas, finally worked my way through all this geeky stuff, compiled xf86-input-wacom V11.1, went through [Bamboo P&T HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562") and Irie Shinsuke's PPA, but the same problem always still exists. Buttons always click on the top left corner of the screen, rather than the current window.  If anyone is reading this and expecting to see a Wacom Intuos tablet work on their Ubuntu system, then be warned.  It works OK as a pointer device for me in Ubuntu 11.04 Natty, but the buttons and slider won't work no matter what you try.

---

### Post by Favux on 2011-07-19
Really nice work lile001.  I know that was painful for you.

You're almost there.  So very close.  It turns out the cursor jump bug is a Ubuntu Natty  specific bug and not a problem with the Wacom driver.  We've got that word from on high (the linuxwacom developers).  But sanette has figured out a fix or work around for it.  See the last few pages of this thread:  [http://ubuntuforums.org/showthread.php?t=1062625&page=8](http://ubuntuforums.org/showthread.php?t=1062625&page=8)

So just apply the patch to the source code in the unpacked xf86-input-wacom folder before compiling and the stupid tablet should finally work for you in Natty.

---

### Post by alpha-buntu on 2011-08-07
hi, just want to log me in, too.

got a wacom bamboo pen & touch 461, pen is working very nicely out of the box, grats to you geeks!

but touch is jumpy :(

I tried the usual linux-"if it takes longer than 5 minutes to fix the but, it takes forever" approach, but have not  been lucky.

well. maybe it will work in ubuntu 11.10.. out of the box

---

### Post by psybi on 2011-08-21
Hello all!

i have a problem with my bambo pen (ctl-460), 
In ubuntu 11.04 there is the nice left bar/launcher, but to get there you have to get to the edge of the screen.. (top or side)
The problem is, that 9/10 times when i get near the edge my pen stops..
Only if i go really slowly i manage to get the launcher to open.
Is there a way to make my tablet thinks the screen is smaller, so when i get near the edge
of the tablet, i'll be already at the edge of the screen..

I searched my *** off for a fix, hopefully someone knows how to fix it.

Thanks :)

---

### Post by Favux on 2011-08-21
Hi psybi,

Welcome to Ubuntu forums!

xinput_calibrator is available in the Universal repo as xinput-calibrator.  So Software Center or Synaptic Package Manager.

Then once you have the calibration information:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Calibration](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Calibration)

Hope this helps.

---

### Post by psybi on 2011-08-22
Thanks you so much Favux! 
It's working great! :P

---

### Post by VaclavC on 2011-09-06
Hi all. I have problem with Intuos3 tablet under Natty. When I press stylus on tablet, it creates ButtonPress event, but it then does not create ButtonRelease event when I lift the pen. I must put the pen completely away from tablet and then it creates ButtonRelease event (probably when connection between tablet and pen is lost at all). Other buttons ("rubber" and two other on stylus) are working fine. Pressure sensitivity in gimp works fine, although I must set pressure curve to something like "0, 0, 20, 100" to draw without too much force. Here are outputs of relevant tools:

---

### Post by Favux on 2011-09-06
Hi VaclavC,

Usually you see this when the tablet is on the wrong driver such as evdev.  But your diagnostics look normal and the tablet is on the Wacom driver.

First thought is there is a problem with your stylus tip.  Have you tried replacing it?   If you don't have a replacement nib in the meantime you could try changing the xsetwacom parameter *Threshold* and see if that helps.  It is independent of the *PressureCurve* parameter.  Default is 27 with range of 0 to 2047.  Maybe start with 40 and go up in jumps of 20 or more?

You could also verify that it is a hardware problem if you see it on another OS or computer.

Also with Natty you might want to try selecting Classic or Classic without effects at the the bottom of the Log In screen and see if that helps.

---

### Post by VaclavC on 2011-09-06
I already tried to replace stylus tip, change threshold or use Classic without compiz. I'll try to connect the tablet to my laptop, which works fine with Intuos 2 and Natty. I don't have any windows computer (with access right to install something) to check it with official drivers.

---

### Post by foxy123 on 2011-10-11
My daughter keeps asking me to buy her a drawing tab because she's quite into drawing manga and stuff. I wonder what is the best one to buy? Some entry level but probably not too simple which is easy to configure under Ubuntu. I'm going to buy her an Asus netbook so I can install any Ubuntu version which supports Wacom tablets better.

---

### Post by Favux on 2011-10-11
Hi foxy123,

A Bamboo Pen or Bamboo One might fit the ticket.

Since some new models have come out you might get one just added to the drivers and so might have to update the Wacom driver in your Ubuntu install.  See instructions on the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").  Also has models at the top.

---

### Post by foxy123 on 2011-10-11
> **Favux said:**
> Hi foxy123,

A Bamboo Pen or Bamboo One might fit the ticket.

Since some new models have come out you might get one just added to the drivers and so might have to update the Wacom driver in your Ubuntu install.  See instructions on the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").  Also has models at the top.

Thanks a lot for that!

---

### Post by sjafri on 2011-10-24
hello guys I need suggestion
I considering to buy wacom for my ubuntu. I am using ubuntu 11.10, what I need is to some how replace my mouse, and occasionally used it to edit photo.
can I do that on ubuntu 11.10?

thank you so much for your reply and suggestion

---

### Post by Favux on 2011-10-24
Hi sjafri,

Consider getting a Bamboo Pen and Touch.  Try not to get one of the new models that just came out this month.  An older one should work out of the box in Oneiric.  It will handle photo retouching well and the the two finger multi-touch and/or the stylus would work in place of a mouse.  You'll want to update your xf86-input-wacom to get the latest gesture improvements, see the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").

If you don't want touch get a Bamboo Pen or a Bamboo One.

The new models of the Bamboo Ones and BambooPT's have just been or are just being submitted to the kernel so you can get them working with a little extra work.

---

### Post by sjafri on 2011-10-24
> **Favux said:**
> Hi sjafri,

Consider getting a Bamboo Pen and Touch.  Try not to get one of the new models that just came out this month.  An older one should work out of the box in Oneiric.  It will handle photo retouching well and the the two finger multi-touch and/or the stylus would work in place of a mouse.  You'll want to update your xf86-input-wacom to get the latest gesture improvements, see the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").

If you don't want touch get a Bamboo Pen or a Bamboo One.

The new models of the Bamboo Ones and BambooPT's have just been or are just being submitted to the kernel so you can get them working with a little extra work.

thank you so much for your suggestion, reply and information, so I know which one will work out of the box using Oneiric

---

### Post by odd on 2011-11-10
Hi everyone.

Hi Favux, I hope this time it's the right place to ask ;))
I've got Wacom Intuos3 6x8" USB and I would like to get the Wacom Airbrush pen tool to work on Lucid 64bit.
I've been playing around with wacom driver versions and stopped on 0.10.11-0ubuntu7 (from [ppa:doctormo/wacom-plus]("https://launchpad.net/~doctormo/+archive/wacom-plus")), which works fine if you remember to have backup of your 10-wacom.conf in (..)/xorg.conf.d/ (in case of missing;)).
So: everything works, pad buttons, pressure both in grip-pen & airbrush, erasers. The only thing I can't get to work properly is airbrush wheel. It doesn't show up in xsetwacom / xinput list and i can't change the AbsWheelDown/Up bindings. See outputs below:
xsetwacom list shows:
```
Wacom Intuos3 6x8 stylus        	id: 14	type: STYLUS    
Wacom Intuos3 6x8 eraser        	id: 11	type: ERASER    
Wacom Intuos3 6x8 cursor        	id: 12	type: CURSOR    
Wacom Intuos3 6x8 pad           	id: 13	type: PAD 
```   
xinput list shows (trimmed to relevant part):
```
&#9116;   &#8627; Wacom Intuos3 6x8 stylus                	id=14	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos3 6x8 eraser                	id=11	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos3 6x8 cursor                	id=12	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos3 6x8 pad                   	id=13	[slave  pointer  (2)]
```
xinput test "Wacom Intuos3 6x8 stylus" shows (trimmed):
```
motion a[0]=29994 a[1]=23033 a[2]=0 a[3]=19 a[4]=35 a[5]=0 
```
where a[5] value changes from -900 to 900 while scrolling the airbrush wheel from one end to another.
xsetwacom acts as follows:
```
$xsetwacom get "Wacom Intuos3 6x8 pad" AbsWheelUp
4

$xsetwacom get "Wacom Intuos3 6x8 pad" AbsWheelDown
5

$xsetwacom get "Wacom Intuos3 6x8 stylus" AbsWheelUp
Property 'Wacom Wheel Buttons' does not exist on device.

$xsetwacom set "Wacom Intuos3 6x8 pad" AbsWheelUp "key a"
Property 'Wacom Wheel Buttons' in an unexpected format. This is a bug.
```
Airbrush scrolwheel acts sometimes as scrollwheel (button 4,5) reporting constant scrolling unless I put the wheel to the bottom-extreme position. But now for example it does nothing on the desktop (except showing a[5] value changes in xinput test (need to further investigate that). 

Does anyone has Wacom Intuos3 airbrush pen working properly on Ubuntu? Internet is sadly silent on "Wacom Intuos3 airbrush" phrase.. :-)

---

### Post by Favux on 2011-11-10
I suppose it is possible they broke airbrush srollwheel support in xf86-input-wacom without being aware of that they did.  Or they renamed the scrollwheel parameter from AbsWheel to something else.  But:
> Airbrush scrollwheel acts sometimes as scrollwheel (button 4,5) reporting constant scrolling unless I put the wheel to the bottom-extreme position.
kind of makes sense.  Buttons 4 and 5 are reserved for vertical scrolling.  

So what we want to do is see what properties xinput and xsetwacom see for the stylus/airbrush.  What is the output of the following commands?:
```
xinput list-props "Wacom Intuos3 6x8 stylus"
```
and
```
xsetwacom get "Wacom Intuos3 6x8 stylus" all
```

I'm wondering if instead of something like:
```
xsetwacom set "Wacom Intuos3 6x8 stylus" AbsWheelDown "key minus"  # Zoom out
xsetwacom set "Wacom Intuos3 6x8 stylus" AbsWheelUp  "key plus"  # Zoom in
```
What we want is:
```
xsetwacom set "Wacom Intuos3 6x8 stylus" Button 4 "key minus"  # Zoom out
xsetwacom set "Wacom Intuos3 6x8 stylus" Button 5 "key plus"  # Zoom in
```
Or they could be using RelWheelUp and RelWheelDown.

---

### Post by odd on 2011-11-10
Thanks for quick reply, Favux.

Here are xinput and xsetwacom outputs:
$ xinput list-props "Wacom Intuos3 6x8 stylus"
```
Device 'Wacom Intuos3 6x8 stylus':
	Device Enabled (121):	1
	Device Accel Profile (246):	0
	Device Accel Constant Deceleration (247):	1.000000
	Device Accel Adaptive Deceleration (249):	1.000000
	Device Accel Velocity Scaling (250):	10.000000
	Wacom Tablet Area (280):	0, 0, 40640, 30480
	Wacom Rotation (281):	0
	Wacom Pressurecurve (282):	5, 10, 90, 95
	Wacom Serial IDs (283):	177, 0, 2, 0
	Wacom Capacity (284):	-1
	Wacom Pressure Threshold (285):	27
	Wacom Sample and Suppress (286):	2, 4
	Wacom Enable Touch (287):	0
	Wacom Hover Click (301):	0
	Wacom Enable Touch Gesture (288):	0
	Wacom Touch Gesture Parameters (289):	50, 20, 250
	Wacom Tool Type (290):	"STYLUS" (299)
	Wacom Button Actions (291):	"None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0)
	Wacom Debug Levels (292):	0, 0
```
$ xsetwacom get "Wacom Intuos3 6x8 stylus" all
```

Option "Area" "0 0 40640 30480"
'Button' requires exactly 1 value(s).
Option "ToolDebugLevel" "0"
Option "TabletDebugLevel" "0"
Option "Suppress" "2"
Option "RawSample" "4"
Option "PressureCurve" "5 10 90 95"
Option "Mode" "Absolute"
Option "TabletPCButton" "on"
Option "Touch" "off"
Option "Gesture" "off"
Option "ZoomDistance" "50"
Option "ScrollDistance" "20"
Option "TapTime" "250"
Property 'Wacom Proximity Threshold' does not exist on device.
Option "Rotate" "none"
Property 'Wacom Wheel Buttons' does not exist on device.
Property 'Wacom Wheel Buttons' does not exist on device.
Property 'Wacom Wheel Buttons' does not exist on device.
Property 'Wacom Wheel Buttons' does not exist on device.
Property 'Wacom Strip Buttons' does not exist on device.
Property 'Wacom Strip Buttons' does not exist on device.
Property 'Wacom Strip Buttons' does not exist on device.
Property 'Wacom Strip Buttons' does not exist on device.
Option "Threshold" "27"
Option "ToolID" "299"
Option "ToolSerial" "0"
Option "ToolSerialPrevious" "0"
Property 'Wacom Serial ID binding' does not exist on device.
Option "TabletID" "177"
```

And your xsetwacom set (...) "Button (...)" "key (...)" indeed gives no error but it doesn't do anything on the desktop. I did set:
```
$ xsetwacom set "Wacom Intuos3 6x8 stylus" Button 4 "key z"
$ xsetwacom set "Wacom Intuos3 6x8 stylus" Button 5 "key y"
```
but it gives me no output on scrolling the wheel (I suspected "zzzzzzzz" or "yyyyyyy" on terminal or sth:))
and:
```
$ xsetwacom get "Wacom Intuos3 6x8 stylus" Button 4
key +z -z 
$ xsetwacom get "Wacom Intuos3 6x8 stylus" Button 5
key +y -y
``` is this "key +z -z" outputs are normal?

---

### Post by Favux on 2011-11-10
Alright, the outputs don't seem to give us a clue unfortunately.  I'll try to look at the code and see if that will clue us in.

I'm not sure that the Button without error helps, because a stylus is suppose to have side buttons.

Are you just using the airbrush or alternating with a stylus?

Does Wacom give a more official/technical description of the airbrush?  You know model #, specifications, formal name, etc.

---

### Post by odd on 2011-11-10
I'm using airbrush (Wacom p/n: ZP-400E-01A) and standard grip-pen (ZP-501E-00A). I found [PDF manual]("http://www.wacom-asia.com/download/manuals/I3_e_EN.pdf") (3.3MB) for Intuos3 series, but not much in there. I'll do some diagnostics later under Windows7 (I found out from the manual that Wacom includes some software to diagnose) and see if everything's working ok there (it's not new pen, it shouldn't but maybe it's somehow malfunctional...) - I'll report here as soon as I can how it went.

EDIT: It's rather not broken, I reminds myself that I quick-tested it under Windows in Corel Painter and fingerwheel worked ok there.

---

### Post by Favux on 2011-11-11
Well it is in the code, for e.g.in wcmValidateDevice.c line #629:
```
			if (nmatch >= 2)
			{
				xf86Msg(X_CONFIG, "%s: Tool %d has type %s.\n",
					pInfo->name, serial, type);
				if ((strcmp(type, "pen") == 0) || (strcmp(type, "airbrush") == 0))
					ser->typeid = STYLUS_ID | ERASER_ID;
				else if (strcmp(type, "artpen") == 0)
					ser->typeid = STYLUS_ID;
				else if (strcmp(type, "cursor") == 0)
					ser->typeid = CURSOR_ID;
				else    xf86Msg(X_CONFIG, "%s: Invalid type %s, defaulting to pen.\n",
					pInfo->name, type);
			}
```
from just above that
```
		case BTN_TOOL_AIRBRUSH:
```
I assume that's how the wacom.ko kernel driver is declaring it.

Also from wcmCommon.c line #713
```
	v5 = ds->abswheel;
	if (IsStylus(priv) && !IsArtPen(ds))
	{
		/* Normalize abswheel airbrush data to Art Pen rotation range.
		 * We do not normalize Art Pen. They are already at the range.
		 */
		v5 = ds->abswheel * MAX_ROTATION_RANGE/
				(double)MAX_ABS_WHEEL + MIN_ROTATION;
	}
```
it appears AbsWheel is the correct parameter name.

So I guess the question is why isn't it seeing an "airbrush" for the string comparison in the if, else if block?  So now look at the wacom.ko code?

---

### Post by Favux on 2011-11-11
Well shoot.

Sure enough in wacom_wac.c at line #379:
```
		case 0x91b: /* Intuos3 Airbrush Eraser */
		case 0x80c: /* Intuos4 Marker Pen Eraser */
		case 0x80a: /* Intuos4 General Pen Eraser */
		case 0x4080a: /* Intuos4 Classic Pen Eraser */
		case 0x90a: /* Intuos4 Airbrush Eraser */
			wacom->tool[idx] = BTN_TOOL_RUBBER;
			break;

		case 0xd12:
		case 0x912:
		case 0x112:
		case 0x913: /* Intuos3 Airbrush */
		case 0x902: /* Intuos4 Airbrush */
			wacom->tool[idx] = BTN_TOOL_AIRBRUSH;
			break;
```

So the first xsetwacom set command should have worked.

Are we doing something wrong or is something broken?

---

### Post by odd on 2011-11-11
I did again a step-by-step as follows:
```

$ xsetwacom get "Wacom Intuos3 6x8 pad" AbsWheelDown
5

$ xsetwacom set "Wacom Intuos3 6x8 pad" AbsWheelDown "key minus"
Property 'Wacom Wheel Buttons' in an unexpected format. This is a bug.

$ xsetwacom set "Wacom Intuos3 6x8 stylus" AbsWheelDown "key minus"
Property 'Wacom Wheel Buttons' does not exist on device.

$ xsetwacom get "Wacom Intuos3 6x8 stylus" Button 5
5

$ xsetwacom set "Wacom Intuos3 6x8 stylus" Button 5 "key minus"
$ xsetwacom get "Wacom Intuos3 6x8 stylus" Button 5
key +minus -minus 

```
and wheel doesn't give me "minus", so I'm lost :-)
But take a look at this: I did some additional blind-shot settings and here what I get:
```

$ xsetwacom set "Wacom Intuos3 6x8 stylus" Button 5 5
$ xsetwacom get "Wacom Intuos3 6x8 stylus" Button 5
button +5 

$ xsetwacom set "Wacom Intuos3 6x8 stylus" Button 5 "Button 5"
$ xsetwacom get "Wacom Intuos3 6x8 stylus" Button 5
button +5 -5 

```
(Yeah, I tried revert it back to "5" output... :))

---

### Post by Favux on 2011-11-11
I wonder if this bug isn't affecting you?:  [http://sourceforge.net/mailarchive/forum.php?thread_name=20111031041028.GA1687%40yabbi.bne.redhat.com&forum_name=linuxwacom-discuss](http://sourceforge.net/mailarchive/forum.php?thread_name=20111031041028.GA1687%40yabbi.bne.redhat.com&forum_name=linuxwacom-discuss)  As you can see the fix is easy.

---

### Post by odd on 2011-11-11
Yep - it affects me...
//me: googling: "howto apply a patch wacom linux" ;P//
But what to patch? I've got this driver precompiled from the wacom-plus ppa in Lucid, so I guess I'll have to download&compile from sources - right?
It's not much of a problems for me, patching should not be a problem too but...
I'm generaly confused about the linux wacom driver versioning, naming etc. There's kernel wacom module (dkms?), some X-related xf86-something wacom module, and I don't know which to download/compile/patch/use and even which HOW-TO to stick to to not end in a dead-end :).
It gets even more complicated since I've got both USB Wacom Intuos3 AND TabletPC.

So.. is there are simple answer to which driver version I should use with USB Wacom Intuos on Lucid?

---

### Post by Favux on 2011-11-11
Generally if the default xf86-input-wacom for a release works you leave it alone.  That's more likely true for a tablet PC than a tablet, since the tablet PC is simpler.  Given how early the Lucid 0.10.5 was in the change over to xf86-input-wacom and all the changes and bug fixing etc. done since then probably best to go for at least 0.11.1 or just clone the git repository.

Part II. of the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562") shows you how to do either.  As does the [linuxwacom HOW TO]("http://ubuntuforums.org/showthread.php?t=1038949"), which also explains a lot of stuff.  When you have the uncompressed xf86-input-wacom folder that's when you can go into the source code and add the P.  Then compile it.

---

### Post by odd on 2011-11-11
Thx Favux. That cleared things for me.
I'll look into it later when I finish my work and get some sleep :-).

P.S.
I remember quite long time ago that there were a possibility of setting up wacom tablet in per-app routine, so that I could have different buttons settings (automaticaly changing) for, say Gimp, Inkscape, MyPaint and so on. Am I right? Is it still possible now on current wacom driver state?

---

### Post by Favux on 2011-11-11
Sure, you're talking about a Profile.  See:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration#Profiles](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration#Profiles)

---

### Post by odd on 2011-11-12
I've just checked under Win7 with Wacom Diagnostics: Airbrush fingerwheel working ok (showing values 0 to 1023 while scrolling). So the broken device is not the case (ugh!;-))

It also shows Device S/N - mine are:
Wacom Airbrush	0x07a00358
Wacom Grip-Pen	0x07201a99
Wacom Mouse	0x06c71e51 (I'm not using it, but I can test it:))
Don't know if this is helpful at all but.. ;-)

I'll try to apply the patch you mentioned & see if it will make any difference in airbrush fingerwheel issue.

---

### Post by SaintDanBert on 2012-01-29
Ubuntu has moved well beyond v10.04 and v10.10.  Wacom tablets continue to be used.  Why don't we have up-to-date information in this or a companion thread?

More important, perhaps, automatic, event-driven device detection -- especially where it intersects X11 configuration -- continues to be obscure and not well documented (... unless you already know how).

I have two Lenovo Thinkpad "Convertible" Tablet-PC workstation with built-in digitizers. One is the older X61t and one is the newer x220t.
Things are extremely similar, but the automatic detection and configuration does wildly different things in each case. That, and I really had to work to discover what was going on.  I'm still not sure that I have answers instead of guesses.

This should not be that arcane and mystery filled.

[/flame off]
~~~ 0;-Dan

---

### Post by Favux on 2012-01-29
Hi Dan,

These threads are up to date:
[http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)
[http://ubuntuforums.org/showthread.php?t=1515562](http://ubuntuforums.org/showthread.php?t=1515562)
[http://ubuntuforums.org/showpost.php?p=6274392&postcount=1](http://ubuntuforums.org/showpost.php?p=6274392&postcount=1)
[http://ubuntuforums.org/showthread.php?t=1656089](http://ubuntuforums.org/showthread.php?t=1656089)

The Wacom tablet applet in the GNOME 3.2 Control Panel (Oneiric) should help.  Initially the first version doesn't do much but more features have been added to the 3.4 version.  In addition a new library for Wacom tablets, libwacom, is being developed:  [http://linuxwacom.git.sourceforge.net/git/gitweb.cgi?p=linuxwacom/libwacom;a=shortlog;h=refs/heads/master](http://linuxwacom.git.sourceforge.net/git/gitweb.cgi?p=linuxwacom/libwacom;a=shortlog;h=refs/heads/master)  also see:  [http://www.hadess.net/2012/01/wacom-tablets-in-gnome-34.html](http://www.hadess.net/2012/01/wacom-tablets-in-gnome-34.html)  It is already used by the 3.4 gnome-settings-daemon and Control Panel applet.  Tablet model definition files are being added as I write at linuxwacom-devel.  So some of the configuration mysteries are being addressed.

In fact I am about to submit a wiki page on libwacom to the Linux Wacom Project's mediawiki.

---

### Post by SaintDanBert on 2012-01-30
Why are these threads not part of this one -- in fact or by reference?
Well... I suppose they are after your post, but my question remains valid.

Also, this thread is huge, in part because details for all sorts of *buntu editions are scattered through.  Having run v8.04, v8.10, then v10.04, v11.04 and v11.10, I can say that the world of wacom tablets was very different and changed in large ways with each successive change.
Doesn't it make sense to silo the details around the appropriate distro edition.

I never have heard or seen anyone say, "... put end-user config details in these files and those folders ..." Rather, I find all sorts of advice scattered all over the disk. 

very VERY frustrated,
~~~ 0;-Dan

---

### Post by SaintDanBert on 2012-01-30
> **Favux said:**
> Hi Dan,

These threads are up to date:
[http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)
[http://ubuntuforums.org/showthread.php?t=1515562](http://ubuntuforums.org/showthread.php?t=1515562)
[http://ubuntuforums.org/showpost.php?p=6274392&postcount=1](http://ubuntuforums.org/showpost.php?p=6274392&postcount=1)
[http://ubuntuforums.org/showthread.php?t=1656089](http://ubuntuforums.org/showthread.php?t=1656089)

The Wacom tablet applet in the GNOME 3.2 Control Panel (Oneiric) should help.  Initially the first version doesn't do much but more features have been added to the 3.4 version.

Does this forum have a tool to extract a very long thread into a downloadable whole? for printing?  for sifting?  for refactoring?

> **Favux said:**
>   In addition a new library for Wacom tablets, libwacom, is being developed:  [http://linuxwacom.git.sourceforge.net/git/gitweb.cgi?p=linuxwacom/libwacom;a=shortlog;h=refs/heads/master](http://linuxwacom.git.sourceforge.net/git/gitweb.cgi?p=linuxwacom/libwacom;a=shortlog;h=refs/heads/master)  also see:  [http://www.hadess.net/2012/01/wacom-tablets-in-gnome-34.html](http://www.hadess.net/2012/01/wacom-tablets-in-gnome-34.html)  

It is already used by the 3.4 gnome-settings-daemon and Control Panel applet.  Tablet model definition files are being added as I write at linuxwacom-devel.  So some of the configuration mysteries are being addressed.

I'm a technical writer and tablet(-PC) user.  How can I help.
Proofread?  Editorial? Writing?

> **Favux said:**
> In fact I am about to submit a wiki page on libwacom to the Linux Wacom Project's mediawiki.

Will we be able to load a package or three onto any v11.x or later edition or is everything embedded in Gnome 3.x? I use Linux Mint-12 as my path to v11.10. I never could wrap around the Gnome 3.x paradigm. While it seems interesting, there wasn't enough useful HOWTO to get my head warped(sic) rightly.

I can't wait to read more...
~~~ 0;-Dan

---

### Post by Favux on 2012-01-30
> Why are these threads not part of this one -- in fact or by reference?
Loic2 stopped participating on this thread or on the Ubuntu community wiki page that he started as a companion to this thread about 2 years ago.  Basically this is a zombie thread at this point.
> Also, this thread is huge, in part because details for all sorts of *buntu editions are scattered through. Having run v8.04, v8.10, then v10.04, v11.04 and v11.10, I can say that the world of wacom tablets was very different and changed in large ways with each successive change.
Doesn't it make sense to silo the details around the appropriate distro edition.

I never have heard or seen anyone say, "... put end-user config details in these files and those folders ..." Rather, I find all sorts of advice scattered all over the disk.

The Linux Wacom Project started a new mediawiki.  Well actually it is about 2 years old at this point, but it did not see much activity until I joined it about a year ago.  There is now plenty of useful content.  That's where most Wacom information is located now and it is pretty much release and distro independent.

Linux Wacom Project's mediawiki HOWTO page:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:HOWTO](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:HOWTO)
DeveloperPages HOWTO page:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:DeveloperPages](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:DeveloperPages)
legacy linuxwacom HOWTO page:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:Linuxwacom](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:Linuxwacom)
All accessible through the mediawiki Main Page:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Main_Page)
Linux Wacom Project's sourceforge home page:  [http://sourceforge.net/projects/linuxwacom/](http://sourceforge.net/projects/linuxwacom/)

---

### Post by lile001 on 2012-05-21
> **Favux said:**
> Loic2 stopped participating on this thread or on the Ubuntu community wiki page that he started as a companion to this thread about 2 years ago.  Basically this is a zombie thread at this point.

The Linux Wacom Project started a new mediawiki.  Well actually it is about 2 years old at this point, but it did not see much activity until I joined it about a year ago.  There is now plenty of useful content.  That's where most Wacom information is located now and it is pretty much release and distro independent.

Linux Wacom Project's mediawiki HOWTO page:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:HOWTO](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:HOWTO)
DeveloperPages HOWTO page:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:DeveloperPages](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:DeveloperPages)
legacy linuxwacom HOWTO page:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:Linuxwacom](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:Linuxwacom)
All accessible through the mediawiki Main Page:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Main_Page)
Linux Wacom Project's sourceforge home page:  [http://sourceforge.net/projects/linuxwacom/](http://sourceforge.net/projects/linuxwacom/)

fantastic!  Close the thread, please, whomever is the OP or guru of it!

---

### Post by Loïc2 on 2012-05-21
Yes, I haven't been using Ubuntu as my distribution of choice for quite a while now, and Wacom support in Linux has evolved since the beginning of those threads. I still kept an eye on the Ubuntu wiki Wacom page modifications, but the page won't be of much use once only newer versions of Ubuntu will remain supported (though I haven't found the Gimp and Inkscape explanations anywhere else, and that's  shame).

Favux knows far more than me about the new Xorg Wacom configuration, and has been the one helping people stuck with LW problems.

I've checked the LWP mediawiki, but it's really technical and doesn't have any step-by-step foolproof method for non-technical users (maybe they frown on screen caps and understandable documentation?), which is a shame. The LWP has never looked favorably upon end user documentation (I never got any interest from Ping into merging the simple Ubuntu Wiki approach in the official LWP doc at the time the page was relevant), but if someone would be nice enough to create an up to date one, that would certainly be a big help to users. Right now, it's like we went back 7 years in the past.

---

### Post by Favux on 2012-05-21
Hi Loïc2,

It's good to hear from you.

Do you feel the core of the mediawiki documentation for users is too technical?
[http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Wacom_Tablet_Set_Up](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Wacom_Tablet_Set_Up)
[http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration)
[http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Calibration](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Calibration)
[http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xsetwacom](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xsetwacom)
[http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xorg.conf.d](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xorg.conf.d)

Peter Hutterer, who is the lead developer of xf86-input-wacom, is sort of the editor.  And he is a bit rigorous.

He did make me rewrite quite a bit of stuff.  He wants the wiki to show users how and why to do things, not be a cookbook.  Hopefully I'm not distorting his viewpoint too much with that.  He also does not want Distro specific stuff if it can be avoided.

The reason I'm not a big fan of wikis is I don't appreciate spending time writing something only to have it rewritten.  I definitely do not want to spend time in editing wars.  For example in the first link Wacom_Tablet_Set_Up most of it was originally mine.  Then one of the LWP developers rewrote most of it.  Not much of my stuff is left.  The tablet specific suggestions in case you were wondering.  So my explanation of the BambooPT button problems disappeared.  And no real place to put it.  But his bold icon page format and what he did there are arguably an improvement to what was there before.  What can you do?

Since I am pretty much the only non-developer contributing as far as I can tell that might be part of the problem.  But if you present a cogent argument for something Peter will go along with it.

---

### Post by Loïc2 on 2012-05-21
> **Favux said:**
> Hi Loïc2,

It's good to hear from you.

Do you feel the core of the mediawiki documentation for users is too technical?
Hi Favux,
Good to see you still alive and kicking the LWP after all these years!

Yes, reading that documentation gives me headaches. I remember spending days fighting the old documentation, and I believe the purpose of LWP's documentation has remained the same - make artists change their careers and become Unix engineers!

> **Favux said:**
> Peter Hutterer, who is the lead developer of xf86-input-wacom, is sort of the editor.  And he is a bit rigorous.

He did make me rewrite quite a bit of stuff.  He wants the wiki to show users how and why to do things, not be a cookbook.  Hopefully I'm not distorting his viewpoint too much with that.

Yes, I had the same impression with Ping. Thing is, they're both engineers, and they reason like engineers, expecting people to learn the innards of the driver before they're allowed to use it. It's a smart move, in that it discourages most people before they have a chance to waste their developper time. Only those able to spend a few days reading the documentation remain, and those can be helped faster since they would have learnt most of the basic stuff by that time. At least in an engineer's dream world - meanwhile in the real world users get completely messed up, forcing the poor engineer to give them the step by step instructions he was trying to avoid in the first place...

> **Favux said:**
> The reason I'm not a big fan of wikis is I don't appreciate spending time writing something only to have it rewritten.  I definitely do not want to spend time in editing wars.
Well, that was the exact reason why I wrote the Ubuntu Wacom wiki page ;) - I knew I couldn't reliably be around to help people on forums, while if I could write a foolproof wiki page it would mean I'd only have to keep a loose eye on it every Ubuntu release or so ;)

That worked quite well actually, only had to do one big edit once, else people did edit the page and add information without rewritting the parts I wrote.

> **Favux said:**
> For example in the first link Wacom_Tablet_Set_Up most of it was originally mine.  Then one of the LWP developers rewrote most of it.  Not much of my stuff is left.  The tablet specific suggestions in case you were wondering.  So my explanation of the BambooPT button problems disappeared.  And no real place to put it.  But his bold icon page format and what he did there are arguably an improvement to what was there before.  What can you do?

Since I am pretty much the only non-developer contributing as far as I can tell that might be part of the problem.  But if you present a cogent argument for something Peter will go along with it.

I don't think my input would do more good than yours. They're the ones writting the code, and they have decided people should waste a few days of their lives before they're allowed to use that code. Can't argue with that, since we're not the ones writing the driver. In the OSS world, the one that makes the effort has the last word (as it should be).

At this point, I also don't have the luxury to throw away a few days of my life trying to make my tablet work on newer distributions. Maybe when I'm retired in 30 years, but I've got too much on my plate at the moment and with no end in sight. And I can't write or give advice on a configuration method I haven't understood.

If Peter doesn't want a cookbook, somebody will have to write it on another place than the LWP project, which will just keep looking down on any page that attempts to help everyone. It's not hard per see, but the one writing it needs to understand the steps, and descibe the simplest way to do it in layman's terms, without omiting even the most obvious step (like the necessary sudo, gksudo and the like).

For comparison, just check the [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Wacom_Tablet_Set_Up](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Wacom_Tablet_Set_Up), which is typical old timer Linux engineer documentation (and if you wrote that part, don't take it personnaly - the LWP didn't leave the one writing the documentation any chance to make it user-understandable):

> Under a modern X server using udev for hotplugging, xorg.conf.d is responsible for defining a tablet's default settings. Older servers may use HAL, and in rare cases an xorg.conf file is necessary. Regardless of which backend performs the setup, these are the ideal place to set system-wide defaults. For example, one could adjust the default rotation property for a Cintiq or TabletPC which is often used in a particular orientation. Perhaps you have a lot of electromagnetic interference near your workstation and feel that increasing the default "Suppress" value for all tablets would be useful. Developers may prefer to have debug information turned up by default, in order to log the events which occur as X starts up. 
**Here's what Joe user thinks:**
* What's udev? Now I need to Google udev and learn what it is, because how can I expect to understand the rest of the sentence if I don't know what it's talking about?
* What's xorg.conf.d? If I'm knowledgeable enough to guess it"s a file, where do I find it? If I'm knowledgeable enough to find it,  how do I make sure it's the right one, and not a simple model I'd have to move to the right place before it's used by the X server?
* What is HAL, and what does it eat in winter when the fields are barren?
* How do I know if I'm in one of the rare cases where an "xorg.conf file is necessary"?
* What is a backend, and do I need to know what "backend" my system is using? Where do I find that information, Google "backend Fedora/Ubuntu/Suse/Debian"? Will I look stupid if I ask people this question on LWP mailing list?
* "these are the ideal place to set system-wide defaults", why does this documentation acts as if it's told me the place to set the configuration, when actually the only thing it has done is throw names at me I don't understand, and made its purpose never to told me the actual place I will find them? 
* Why that scary about interferences and "Suppress" when the user reading that part still doesn't have any working tablet to be interfered or suppressed?

I'm happy following Peter's efforts making the LW driver better, and am eternally grateful for his work. At this point, I haven't been able to benefit _one bit_ from it, because I'm not the uber-user with plenty of time on his hands he's targeting. I was that user in the 90s, but I'm not anymore, and it's too bad the LWP only catered for that kind of user.

---

### Post by Favux on 2012-05-21
lol  I agree with pretty much everything you said.
> Under a modern X server using udev for hotplugging, xorg.conf.d is responsible for defining a tablet's default settings. Older servers may use HAL, and in rare cases an xorg.conf file is necessary. Regardless of which backend performs the setup, these are the ideal place to set system-wide defaults. For example, one could adjust the default rotation property for a Cintiq or TabletPC which is often used in a particular orientation. Perhaps you have a lot of electromagnetic interference near your workstation and feel that increasing the default "Suppress" value for all tablets would be useful. Developers may prefer to have debug information turned up by default, in order to log the events which occur as X starts up. 
Yep, that's Jason.  He's a new Wacom developer who joined the Project.  So Wacom is providing both him and Ping now.

My stuff on that page is the bottom section:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Wacom_Tablet_Set_Up#Tablet-Specific_Suggestions](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Wacom_Tablet_Set_Up#Tablet-Specific_Suggestions)  With some remaining fragments in the two sections above that one.  He sort of had to keep some of the Calibration stuff because I wrote that page and the matrix stuff for Dual Monitors.  So yeah I did get a wee bit mathematical with the matrices.  Oh well.  The actual calculations are fractions.

When I was a newbie I looked at doing some Ubuntu wiki stuff.  Back then it seemed the hurdles were pretty high.  Maybe I should revisit because how you set things up was shrewd.  I already have the max. number of HOW TO's I feel comfortable with.  Don't want to invest more time.

Ubuntu has been doing a new push to upgrade the wikis.  Maybe I should look into that and put up a "newbie" guide paired to a thread and hope others maintain it.  Have to find and read their new guidlines I suppose.  Ugh.

Once you invest some time learning how to set up your xsetwacom script and get it working you are basically done.  Very quick and simple to change things after that.

---

### Post by Loïc2 on 2012-05-22
> **Favux said:**
> Yep, that's Jason.  He's a new Wacom developer who joined the Project.  So Wacom is providing both him and Ping now.

Didn't know that. I thought it was only Peter Hutterer and Ping. It's good news.

> **Favux said:**
> My stuff on that page is the bottom section:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Wacom_Tablet_Set_Up#Tablet-Specific_Suggestions](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Wacom_Tablet_Set_Up#Tablet-Specific_Suggestions)  With some remaining fragments in the two sections above that one.

That part it great, it's written in a totally different style than the first part. Just a shame they don't want to do the beginning that clear... The paragraph I cited, along with the pages it links to (xorg.conf.d for example) makes a lot of assumptions about the reader, and will have lost most people already.

I checked the site more, and the [HOWTO]("http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:HOWTO") section is far better - did you write some of them?
The "Configuring X" is clear and doesn't assume a degree in computer science, however for actual configuration it refers to the xorg.cong.d page, which is not a howto and reverts to the old LWP style :( (I had to check with my wife what a "snippet" means in common English, and figure what it was in LWP parlance. Probably another developper term, configuration file is so 1970...)

> **Favux said:**
> When I was a newbie I looked at doing some Ubuntu wiki stuff.  Back then it seemed the hurdles were pretty high.  Maybe I should revisit because how you set things up was shrewd.  I already have the max. number of HOW TO's I feel comfortable with.  Don't want to invest more time.

Ubuntu has been doing a new push to upgrade the wikis.  Maybe I should look into that and put up a "newbie" guide paired to a thread and hope others maintain it.  Have to find and read their new guidlines I suppose.  Ugh.

Yes, the Ubuntu Wacom wiki page will have to be updated eventually. Right now it's still of for folks like me who keep an old spare Ubuntu/Mint install just for Wacom support ;) but once even 10.04 will reach end of life they'll probably nuke it without asking.

As for guidelines, I'm not sure there's much point. Wacom is a remote concern to Linux distributions, so they don't look closely, if ever at all ;)

Better would be to have it on the LWP, but they'd have to change their opinion of end users, allow pictures (the horror!) and maybe stuff are too distro-specific. That's something I'm not sure I understand though - isn't freedesktop there to set some defaults around the place that would make an 'Ubuntu Wacom'-like page a possibility?

> **Favux said:**
> Once you invest some time learning how to set up your xsetwacom script and get it working you are basically done.  Very quick and simple to change things after that.

Yes, I'm sure, but the initial investment is big without the ropes ;). I'm not trying before I understand!

Also, from a look at the LWP howtos, some you probably wrote, I'm not sure what's the official/best method - isn't it using xorg.conf.d (though there's not much explanation of possible options or methods to guess the right values), or is it xsetwacom?

---

### Post by lile001 on 2012-05-24
Loïc2 and Favux, you guys are on the right track here.  I am one of the knucklehead N00bs that wastes your time trying to figure out the documentation, and coming away befuddled by it as Favux can attest.  Anything that can be done to push back against the tendency of Engineers  to look down their noses at people who don't intimately understand their specialty is effort well spent! (BTW, I AM one, but not a computer engineer. Need a 4000 amp 480 volt electrical service, give me a call.)  Artists typically want tablets (and CAD operators and people like me with Carpal tunnel) and these folks may not understand the intricacies of Unix-like stuff.

---

### Post by Favux on 2012-05-24
Hi Loïc2,

Peter Hutterer is a Red Hat engineer who works on X.org stuff, in their graphics section.  Chris Bagwell has done a bunch of stuff for touch and gesture both in the kernel and xf86-input-wacom. So they've gone from 1 to 4 with a couple of others contributing.
> I checked the site more, and the HOWTO section is far better - did you write some of them?
Yes.  And some are by Peter and some are joint pages by Peter and myself.  I'd have to check, but I don't think anyone else has contributed much to the user HOW TO page.

xorg.conf.d snippet = xorg.conf section

Snippet is an X.org term.

It's all about hot plugging.  Linux didn't have a good hot plugging solution and X.org hadn't come up with one so the Distros went to HAL (hardware abstraction layer) and its .fdi files to configure.  The .fdi files were .xml files.  And that got the Distros modern usb hot plugging.

But people did not like HAL much.  X.org finally came up with their in house solution which was xorg.conf.d and its .conf files.  And that's what everyone switched to starting with X Server 1.8.  Except for Debian/Ubuntu.  They were so eager to get rid of HAL they took some early X Server 1.8 stuff and backported it into their "1.7".  So what they call X Server 1.7 is actually a hybrid and is a special case with its own problems, of course.

What happens is xorg.conf starts then immediately executes the xorg.conf.d(s) .conf files.  Then if anything is actually in xorg.conf those sections are executed.
> pictures (the horror!) and maybe stuff are too distro-specific.

Exactly, no way I'd be able to sneak Ubuntu screen shots in.
> I'm not sure what's the official/best method - isn't it using xorg.conf.d (though there's not much explanation of possible options or methods to guess the right values), or is it xsetwacom? 
Xsetwacom is the most flexible and lets you do the most, but they are run time commands and don't last through a hot plug unless you go to a bunch of trouble with wdaemon.  The xorg.cond.d .conf files Options (so called static options) do survive a hotplug.  But the plan is to get the GNOME Wacom Graphics Tablet applet up to speed and do most things through it.  Yes you heard right, finally a wacompl replacement!  Its coming along and is catching up to the KDE applet.


@ lile001,

Believe me I feel your pain.  With all of the changes in the last two years it has been hard to keep up.  And then trying to remember which applies to what release when you've got releases spanning two or three years is a bit of a challenge.

---

### Post by SaintDanBert on 2012-05-24
> **Favux said:**
> Hi Loïc2,

Believe me I feel your pain.  With all of the changes in the last two years it has been hard to keep up.  And then trying to remember which applies to what release when you've got releases spanning two or three years is a bit of a challenge.

I struggle to read this thread because of all of the variants that are discussed along the road. Your recent posts hint at better docs and details, but I must fail to understand the where because I don't find anything.  Can you please direct me to or repeat the list of things that mortals can read? 

At one point your wrote to **Loic2**:
> 
What happens is xorg.conf starts then immediately executes the xorg.conf.d(s) .conf files. Then if anything is actually in xorg.conf those sections are executed.
Do you really mean that the server processing is:
[list]
[*]read xorg.conf to establish some defaults
[*]read all xorg.conf.d/* and digest them
[*]process xorg.conf contents that are not "defaults"
[/list]
Is this right or am I missing something?

Thanks for your efforts, Favux.
~~~ 0;-Dan

PS/ Idle curiosity:  could you write a phonetic pronounciation of 
"Favux"?  What is the language or nationality.  My surname is St.André
and so names have always been a fascination.  0;-D

---

### Post by Hyaku on 2012-05-29
Hi guys!

I'm trying to configure my wacom to enable something like the "Force proportions" option from the windows drivers.
I tried the "KeepShape" option explained [[COLOR=Blue]here[/COLOR]]("https://help.ubuntu.com/community/Wacom"), but don't seems to work. Is the information of that page outdated or i'm doing something wrong ?


PD: I'm using Ubuntu 12.04

---

### Post by Favux on 2012-05-29
Hi Hyaku,

Welcome to Ubuntu forums!

Yes the information on KeepShape is outdated.  They disabled KeepShape a while ago.  You can demonstrate that to yourself by running:
```
xsetwacom get 8 KeepShape
```
Where 8 happened to be the ID number of my stylus from **xinput list**.  It'll return:
> Unknown parameter name 'KeepShape'.
They were planning on reactivating it but it hasn't happened yet.  You can view many of the available parameters by looking at **man xsetwacom** and **man wacom** in a terminal.  To see all the available parameters run:
```
xsetwacom list parameters
```
They don't all apply to all devices though.

So instead you need to use the Area parameter as demonstrated in [Calibration]("http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Calibration").

---

### Post by Hyaku on 2012-05-29
Thanks Favux!

Now i can get it working using the terminal. I tried to edit the xorg.conf file so i don't have to reconfigure the working area every time i restart, but didn't work.

I added these lines at the end of the file:

```
Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/ttyS0"              # SERIAL ONLY
  Option        "Device"        "/dev/input/wacom"        # USB ONLY
  Option        "Type"          "stylus"
  Option        "USB"           "on"                      # USB ONLY
  Option "TopX" "0"
  Option "TopY" "0"
  Option "BottomX" "60960"
  Option "BottomY" "34290"
EndSection
```

Is something wrong?

---

### Post by Favux on 2012-05-29
> Is something wrong? 
Yes.  Starting with Lucid you use xorg.conf.d snippets instead of xorg.conf sections.  You can hot plug the tablet with xorg.conf.d but not xorg.conf.  So you could use xorg.conf, but with a usb tablet not the best idea.

Likely you did not include a "ServerLayout" section with a Wacom stylus line which is why your xorg.conf section wasn't active.  Fortunately.  Because you have a serial line in there that needs to be removed or commented out:
```
#  Option        "Device"        "/dev/ttyS0"              # SERIAL ONLY
```
Anyway you probably want to remove that from xorg.conf.

This wiki page deals with xorg.conf.d:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xorg.conf.d](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xorg.conf.d)  Ask if you have questions.  It's a bit much to take in.

What tablet do you have anyway?

---

### Post by Hyaku on 2012-05-29
Ok, tried again.

I left the xorg.conf file as default. 
- I created a file called 52-wacom-options.conf at [I]/etc/X11/xorg.conf.d.  The file looks like this:

[/I]```
Section "InputClass"
    Identifier "Wacom Intuos3 9x12 stylus options"
    MatchProduct "Wacom|WACOM"
    MatchDevicePath "/dev/input/event*"
    Driver "wacom"

    Option "TopX" "0"
        Option "TopY" "0"
        Option "BottomX" "60960"
        Option "BottomY" "34290"
EndSection
```Still not working.  :(


I have an Intuos 3. Ubuntu recognizes it as Wacom Intuos3 9x12.

---

### Post by Favux on 2012-05-29
Nice job, looks like you got it right.

Should be working.  Did you restart?

---

### Post by Hyaku on 2012-05-29
Yes. I restarted again after seeing your message.

And still not working.

Are you sure everything is ok ?

---

### Post by Favux on 2012-05-29
Hmmm.  It looks right to me.  I don't think they've changed the coordinate Option parameter names and **man wacom** still has what you are using.

Try varying them and see if the changes show up in Xorg.0.log in /var/log.  Have you checked on your wacom-options.conf and made sure it is in the correct spot?

The other thing is the GNOME Wacom Graphics Tablet applet in System Settings.  They were talking about adding calibration to it.  But I don't see it, at least with my BambooPT.  But you should check if somehow you have that.  If not we can look with dconf-editor and see if there are somehow coordinate key values messing you up.

---

### Post by Hyaku on 2012-05-29
Here is what Xorg.0.log says. Looks like first loads my custom config but after that loads the default values :

```
15.702] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[    15.702] (**) Wacom Intuos3 9x12: always reports core events
[    15.702] (**) Option "Device" "/dev/input/event3"
[    15.702] (II) Wacom Intuos3 9x12: type not specified, assuming 'stylus'.
[    15.702] (II) Wacom Intuos3 9x12: other types will be automatically added.
[    15.702] (**) Option "TopX" "0"
[    15.702] (**) Option "TopY" "0"
[    15.702] (**) Option "BottomX" "60960"
[    15.702] (**) Option "BottomY" "34290"
[    15.702] (--) Wacom Intuos3 9x12 stylus: using pressure threshold of 27 for button 1
[    15.702] (--) Wacom Intuos3 9x12 stylus: Wacom USB Intuos3 tablet maxX=60960 maxY=45720 maxZ=1023 resX=200000 resY=200000  tilt=enabled
[    15.702] (II) Wacom Intuos3 9x12 stylus: hotplugging dependent devices.
[    15.702] (EE) Wacom Intuos3 9x12 stylus: Invalid type 'touch' for this device.
[    15.702] (II) Wacom Intuos3 9x12 stylus: hotplugging completed.
```
The Wacom Graphics Tablet applet don't shows any calibration related option.

Tomorrow i'll give it another try. Here is late.

Thanks again Favux!

---

### Post by abexman on 2012-06-01
Dumb question, did not see an answer on quick search. I have just installed Ubuntu 12.04 with a Wacom Graphire4. Seems to work well with defaults but the tablet scroll button does not seem to do anything and I don't see the scroll button in the "Wacom Graphics Tablet" settings as even an option?

---

### Post by Favux on 2012-06-01
Hi abexman,

Not a dumb question.  They accidentally broke the Graphire scroll wheel a while ago.  The fix was just commited to the xf86-input-wacom repository a couple of days ago.  So you will need to clone the xf86-input-wacom git repository and compile it.  See part II. of the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").

And use RelWheel as the parameter not AbsWheel, as in RelWheelUp and RelWheelDown, in your xsetwacom commands.

---

### Post by Chillyguess on 2012-06-09
Hi Favux, 

I posted a whiiiillllle back. But I've got a Thinkpad W510 and recently installed UBuntu 12.04 -> I'm not sure why, my INTUOS4 Wireless detects and installed okay, and it 'seems' to be working. But when I move my stylus, it doesn't detect it at all. All the lights are on within my tablet, I'm just not getting it to work. Also, USB mode only works if I plug it in BEFORE I restarted my laptop. Any ideas?

---

### Post by Favux on 2012-06-09
Hi Chillyguess,

You'll be happy to know Prezmo has almost finished implementing wireless support for the INTUOS4 Wireless.  Not sure how much of it is in Precise's 3.2 kernel but it is coming.

Part of that is I think they added a new keyword to the 50-wacom.conf match in xorg.conf.d for it in wireless mode so we need to keep that it mind.

Don't understand why you need to plug it in before a restart.  As far as I know it should be hot pluggable.

What is the output of:
```
xinput list
```
when it is working?  And when it isn't?  Is **wacom** in ***lsmod*** either way?

---

### Post by Chillyguess on 2012-06-09
Oh sweet! Can't wait for it to come then. :) 

My xinput list:

```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos4 WL stylus                 	id=10	[slave  pointer  (2)]
&#9116;   &#8627; Wacom ISDv4 E2 Finger touch             	id=11	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=13	[slave  pointer  (2)]
&#9116;   &#8627; TPPS/2 IBM TrackPoint                   	id=14	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos4 WL eraser                 	id=16	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos4 WL cursor                 	id=17	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos4 WL pad                    	id=18	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; Integrated Camera                       	id=9	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=12	[slave  keyboard (3)]
    &#8627; ThinkPad Extra Buttons     
```

How do I check if my wacom is in lsmode? Edit: never mind. Here is wacom with "0" in lsmod. :) 

```
chillyguess@chillyguess-ThinkPad-W510:~$ lsmod
Module                  Size  Used by
ppp_deflate            13038  0 
zlib_deflate           27139  1 ppp_deflate
bsd_comp               12994  0 
ppp_async              17539  1 
crc_ccitt              12667  1 ppp_async
option                 25849  2 
usb_wwan               20491  1 option
hidp                   22628  0 
vesafb                 13844  1 
snd_hda_codec_hdmi     32474  4 
rfcomm                 47604  12 
bnep                   18281  2 
parport_pc             32866  0 
ppdev                  17113  0 
arc4                   12529  2 
iwlwifi               328352  0 
joydev                 17693  0 
snd_hda_codec_conexant    62128  1 
nvidia              12336440  42 
mxm_wmi                12979  0 
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
wacom                  48346  0 
psmouse                87692  0 
serio_raw              13211  0 
snd_hda_intel          33773  4 
i7core_edac            28102  0 
edac_core              53746  1 i7core_edac
mac80211              506816  1 iwlwifi
cfg80211              205544  2 iwlwifi,mac80211
v4l2_compat_ioctl32    17128  1 videodev
usbserial              47077  7 option,usb_wwan
btusb                  18288  2 
bluetooth             180104  24 hidp,rfcomm,bnep,btusb
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi

```

---

### Post by Favux on 2012-06-09
For wireless I think you add to the 50-wacom.conf usb snippet in /usr/share/X11/xorg.conf.d PTK-540WL like so:
```
Section "InputClass"
	Identifier "Wacom class"
	MatchProduct "Wacom|WACOM|Hanwang|PTK-540WL"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
EndSection
```
Prezmo fixed the tablet's bluetooth name in the kernel's HID section to add Wacom so the standard match will eventually work, but that's further upstream in the kernel.  And he's been adding more featues as time goes by.  Chris has been working on the new wireless kit and they've been giving each other ideas on the battery monitoring and stuff.

Well that all looks good.  Don't know why you would have a problem with the laptop's touchscreen.  What do you see with:
```
xsetwacom list
```
and?
```
xinput list-props "Wacom Intuos4 WL stylus"
```

---

### Post by Chillyguess on 2012-06-09
Oh yep. I'll add those and see...

Meantime here is the codes... 

```

chillyguess@chillyguess-ThinkPad-W510:~$ xsetwacom list
Wacom ISDv4 E2 Finger touch     	id: 11	type: TOUCH     
Wacom Intuos4 WL stylus         	id: 10	type: STYLUS    
Wacom Intuos4 WL eraser         	id: 16	type: ERASER    
Wacom Intuos4 WL cursor         	id: 17	type: CURSOR    
Wacom Intuos4 WL pad            	id: 18	type: PAD       
chillyguess@chillyguess-ThinkPad-W510:~$ xinput list-props "Wacom Intuos4 WL stylus"
Device 'Wacom Intuos4 WL stylus':
	Device Enabled (121):	1
	Coordinate Transformation Matrix (123):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (242):	0
	Device Accel Constant Deceleration (243):	1.000000
	Device Accel Adaptive Deceleration (244):	1.000000
	Device Accel Velocity Scaling (245):	10.000000
	Device Node (239):	"/dev/input/event6"
	Wacom Tablet Area (252):	0, 0, 40840, 25400
	Wacom Rotation (253):	0
	Wacom Pressurecurve (254):	0, 0, 100, 100
	Wacom Serial IDs (255):	188, 109065206, 1050626, 0, 0
	Wacom Serial ID binding (256):	0
	Wacom Pressure Threshold (257):	27
	Wacom Sample and Suppress (258):	2, 4
	Wacom Enable Touch (259):	1
	Wacom Hover Click (260):	1
	Wacom Enable Touch Gesture (261):	0
	Wacom Touch Gesture Parameters (262):	0, 0, 250
	Wacom Tool Type (263):	"STYLUS" (241)
	Wacom Button Actions (264):	"None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0)
	Device Product ID (238):	1386, 188
	Wacom Debug Levels (265):	0, 0
chillyguess@chillyguess-ThinkPad-W510:~$ 


```

---

### Post by mindtravel3r on 2012-06-21
Hi Folks, 

I just installed Ubuntu 12.04 as a VM using VirtualBox on a Windows 7  Host.  I am pretty green when it comes to Ubuntu.  I can get to a  command line and I understand basically what it is, but I have no  practical experience using it.  

Here's my problem.  I have a Wacom Intuos 3, and a Microsoft wireless  mouse.  Both devices are recognized by the system and I can change  settings in the System Settings.  The tablet drivers appear to be  working.  I am seeing pressure sensitivity in Krita and can draw in the  program.  The problem is that the mouse and the tablet seem to be acting  independently.  When using the stylus the pointer is only visible over the drawing area.  As soon as I move to any of the tools, the cursor disappears. Is this normal behavior in Ubuntu?  It seems like I ought to be able to change tools with the stylus.  

In my Windows 7 environment,  the two are integrated and the pointer is  shared between them.  That would be the ideal, but I could live with two  pointers.   Does anyone know how to get the pointer visible for the  tablet device outside of the drawing area?  Any help you can provide is greatly appreciated.

Thanks, 

David

---

### Post by Favux on 2012-06-21
Hi mindtravel3r,

Welcome to Ubuntu forums!

I saw your other post but didn't answer it since I don't use VM's.

Rather than yell at you for double posting, since I realized probably no one answered your original post, I'll offer a guess.  You likely want some VirtualBox setting that allows sharing of the core pointer.  Or maybe they'd use something like master and/or slave pointer.  Some combination of those maybe.

---

### Post by mindtravel3r on 2012-06-22
Hi Favux,

Thanks for the reply and also for not yelling at me for double posting.  I did make an edit to the beginning of the original post before posting here saying that I was moving the question over here, but I should have made note of that in the post here as well.  I will try not do that in the future.

In regard to my issue, you got me thinking in the right direction.  I really didn't think it was the VM because everything else appeared to working so flawlessly.  After poking around in VirtualBox and finding nothing related to pointers, I decided to pull out an old hard drive and do a straight install on a different drive.  The tablet is working perfect, so I guess it was the VM.  Something else that was interesting, is that the Wacom driver is more functional allowing accelerator setting of the buttons.  The VM version only allowed a limited number of simple commands.  All-in-all I am pretty happy and my testing of the system continues.  I am on the verge of shelving Windows and moving over to Ubuntu for good.  I am very impressed with my experience this time around.  I am having one issue with the Software installer, but I will look for the appropriate place to post that as it has nothing to do with Wacom tablets.  

Thanks for helping me out.

Have a great day,

David

---

### Post by Favux on 2012-06-22
Good deal.

So it was the VirtualBox VM.  Sounds like it doesn't quite work seamlessly with the X Server's handling of the pointers.

Glad to hear your linux experience is going well this time around.

---

### Post by mindtravel3r on 2012-06-29
Been trying to map my buttons and I am only able to get buttons 1, 2 and  3 to work.  Buttons 4 through 8 are being set but there is no response  from the buttons.

I'm using an Intuos 3 (PTZ-930).  

I have also been trying to map the strips to zoom with Ctrl + and Ctrl - with no luck.

Here's the code I've been using:

root@velocitymicro:/home/david# xsetwacom set "Wacom Intuos3 9x12 pad" Button 8 "key Ctrl z"

root@velocitymicro:/home/david# xsetwacom set "Wacom Intuos3 9x12 pad" StripLeftDown "Key Ctrl -"

Are there issues with the older tablets?  It sure seems like it ought to work.

---

### Post by Favux on 2012-06-29
The X Server reserves buttons 4 to 7 for vertical and horizontal scroll.  So you have to use Button 8 for your Button 4 and then continue that offset of 4.  So Button 5 is Button 9 and so on.

"key minus"  # Zoom out

"key shift plus"  # Zoom in
Unless you have a European keyboard layout then it is:
"key plus"  # Zoom in

See:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration)

---

### Post by Temar09 on 2012-08-06
Sorry if this has already been asked, but I did not read all 85 pages.

It seems I'm unable to map a shortcut which uses the Windows-key to one of my pad buttons:

```

$ xsetwacom -V
0.14.0

$ xsetwacom set "Wacom Bamboo 16FG 6x8 Finger pad" Button 1 "key meta f12"
$ xsetwacom get "Wacom Bamboo 16FG 6x8 Finger pad" Button 1
key +Alt_L +F12 -F12

$ xsetwacom set "Wacom Bamboo 16FG 6x8 Finger pad" Button 1 "key super f12"
$ xsetwacom get "Wacom Bamboo 16FG 6x8 Finger pad" Button 1
key +(null) +F12 -F12

$ xsetwacom set "Wacom Bamboo 16FG 6x8 Finger pad" Button 1 "key Super_L f12"
$ xsetwacom get "Wacom Bamboo 16FG 6x8 Finger pad" Button 1
key +(null) +F12 -F12

```

According to "xev" my Windows key is reported as "Super_L" but whenever I use the "super" key in a key mapping it is reported as "(null)" and does not work.

Also many other keys are reported as "(null)", for example "f20". I really would like to use keys like "f20" for my pad-buttons to avoid conflicts with any other software. I could then map these "f20", "f21",... buttons (via KDE) to executable programs which switch to different operational modes.

How can I map these buttons without getting "(null)" values? If the upper f-buttons can not be mapped, how can I at least map my windows-key?

---

### Post by Hyaku on 2012-08-10
Hey guys! Do you know if is possible to run [COLOR=Blue]**[this]("http://libregraphicsworld.org/blog/entry/kcm-wacom-tablet-1.3-calibration-autorotation-global-shortcuts")**[/COLOR] on Gnome/Unity ?

---

### Post by Temar09 on 2012-08-10
> **Hyaku said:**
> Hey guys! Do you know if is possible to run [COLOR=Blue]**[this]("http://libregraphicsworld.org/blog/entry/kcm-wacom-tablet-1.3-calibration-autorotation-global-shortcuts")**[/COLOR] on Gnome/Unity ?

Yes it's possible but not feasible. To run this configuration tool you need many KDE libraries and even have to run the KDE background daemon kded.

Why don't you just use the Gnome settings tool?

---

### Post by Hyaku on 2012-08-10
I don't care to install as many libraries as needed and run kded if they don't break performance.

I already use the Gnome tablet tool, but it's really incomplete and lacks some features as the "force proportion" options and the profiles manager.

---

### Post by Favux on 2012-08-10
Hi Hyaku,

Why not just use Kubuntu then?

If you want to stay with Gnome you will likely need to disable the gnome-settings-daemon wacom plugin so it doesn't interfere with your new settings.  Install dconf-editor if not already installed with:
```
sudo apt-get install deconf-editor
```
Open it in a terminal with 'dconf-editor' and navigate to:  org.gnome.settings-daemon.plugins.gsdwacom.  Disable the active check box.  Log out and log back in.

---

### Post by Temar09 on 2012-08-11
> **Hyaku said:**
> I don't care to install as many libraries as needed and run kded if they don't break performance.


There are far more problems than you think. First of all, you would have to start the KDE background daemon manually on each startup, as it is not supposed to be run in a GNOME environment. Then you probably have to disable some default services which the background daemon would normally start in a KDE environment.

After all that, the configuration program can be used from within GNOME but you won't be able to use it in all its glory. You can configure your device, but you can not use the comfortable plasma widget to quick-switch between profiles or different tablet modes. Still you will be able to switch profiles within the configuration dialog.

As you can see, this configuration tool is designed for KDE and makes use of many KDE technologies which are not available in GNOME or Unity. So while it is possible to use this program to configure your device it really is not a practicable approach.

Last but not least, the (K)Ubuntu package of this configuration tool is broken. I think the Ubuntu packager made a mistake when packaging the software. He disabled KIO support which seems to be required to write the configuration file. However I created my own package of the latest version which works very well. If you have a 64bit system I could send you my package.


> 
I already use the Gnome tablet tool, but it's really incomplete and lacks some features as the "force proportion" options and the profiles manager.

Missing profile support is really bad, I agree.

---

### Post by Hyaku on 2012-08-11
Well, i'll simply try with Kubuntu then. Thank you guys!


@Termar09 : My english isn't very good and my linux knowledge is not better, so i don't know if i misunderstood you, but if you're saying that the wacom tool comes broken in the Kubuntu default installation, then of course i want those packages. :)

I have 64bit, so no problem with that.

---

### Post by Temar09 on 2012-08-11
> **Hyaku said:**
> @Termar09 : My english isn't very good and my linux knowledge is not better, so i don't know if i misunderstood you, but if you're saying that the wacom tool comes broken in the Kubuntu default installation, then of course i want those packages. :)


[http://wikisend.com/download/520604/kde-config-tablet_1.3.6git20120709-1_amd64.deb](http://wikisend.com/download/520604/kde-config-tablet_1.3.6git20120709-1_amd64.deb)

Compiled for (K)Ubuntu 12.04. It's compiled against KDE 4.9 but this shouldn't be a problem.

The file will be deleted by WikiSend.com after 7 days.

---

### Post by Hyaku on 2012-08-11
Thanks Termar09! Kubuntu installed and with your package everything is working OK.

---

### Post by Tekippie on 2012-08-11
I just got the latest Bamboo Pen with the fancy black/green design and it works plug & play in my Ubuntu 12.04. I have positioned the tablet in portret mode by default as it then serves as a mousepad nicely on my desk. but for Ubuntu to know it's in portret position I [found]("http://ubuntuforums.org/showpost.php?p=6274392&postcount=1") I have to run these commands;

$ xsetwacom set "Wacom Bamboo Connect Pen stylus" rotate ccw
$ xsetwacom set "Wacom Bamboo Connect Pen eraser" rotate ccw

FYI :)

---

### Post by pecazp on 2012-08-13
Hi,I'm recently back to linux and i have old but fully working Wacom Volito tablet. That is, fully working on Windows.

I have installed 12.04 Ubuntu 64bit and Kde desktop.

   My pen works like it should almost all the time in MyPaint but, sometimes it start drawing while i just hover half inch above surface of tablet and i was able to fix that by pulling out usb cable and than putting it back. That happened only couple of times, it usually works as expected. My problem is with Gimp where it does that all the time and that fix didn't work. 

I don't know where are settings for tablet, in System Settings device doesn't show. If that would help at all, because painting in MyPaint works as it should at least for painting, i have to select different tools with mouse because it freak out on hover and just clicks like crazy. Same when i go to top of the window or at taskbar (you know, min-max window ten times in couple seconds, also on hover).

Since this is the one of couple reasons for me to still have dual boot I'd be very grateful even if you just post any link that could lead me closer to explanation or solution to this problem.

Thank you and best wishes

---

### Post by Typhon on 2012-11-01
Yesterday I update to Ubuntu 12.10 and I experienced some troubles in getting my Intuos4 to work. 

When I enter the following command:
```
xsetwacom get "Wacom Intuos4 6x9 pad" Rotate HALF
```
I get this error:
> Property 'Wacom Rotation' does not exist on device.

---

### Post by Favux on 2012-11-01
Hi Typhon,

The Pad does not rotate.  Instead use stylus which will also rotate the eraser.  And you want to use set not get.
```
xsetwacom set "Wacom Intuos4 6x9 stylus" Rotate half
```
Assuming "Wacom Intuos4 6x9 stylus" is the parent device you see in the output of **xinput list**.  Also you should not need to capitalize half anymore.  See:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Rotation](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Rotation)

Additionally if you are using the Gnome version the Wacom Tablet applet in System Settings should give you a left hand orientation setting.

---

### Post by Typhon on 2012-11-01
Thanks, that works great. I noticed I'd been using old parameters in my Xsetwacom file.

---

### Post by Typhon on 2012-11-02
One more question and then I'll stop. :D
If I enter xsetwacom commands individually into terminal I get no errors. On the other hand, if I execute xsetwacom.sh script, I get the following messages:
> sh ./.xsetwacom.sh 
Unsupported offset into 'Wacom Button Actions' property.
Unsupported offset into 'Wacom Button Actions' property.
Cannot parse keyword '+' at position 1
Cannot parse keyword '-' at position 1
Unsupported offset into 'Wacom Button Actions' property.
Unsupported offset into 'Wacom Button Actions' property.

This is my current xsetwacom.sh for Intuos4:
```
#!/bin/sh

## stylus = ID ? = "Wacom Intuos4 6x9"
xsetwacom set "Wacom Intuos4 6x9 stylus" Suppress "2"  # data trimmed, 0-100
xsetwacom set "Wacom Intuos4 6x9 stylus" RawSample "10"  # default is 4, 1-100
xsetwacom set "Wacom Intuos4 6x9 stylus" Threshold "27"  # 0-2047
xsetwacom set "Wacom Intuos4 6x9 stylus" PressureCurve "0 0 100 100"
## 0 100   0 100  # ridiculously soft
## 0  50  50 100  # very soft
## 0   0 100 100  # linear, the default
## 50   0 100  50  # very firm
## 100 0 100 0  # unbelievably firm
xsetwacom set "Wacom Intuos4 6x9 stylus" Rotate half
xsetwacom set "Wacom Intuos4 6x9 stylus" TabletPCButton "off"
xsetwacom set "Wacom Intuos4 6x9 stylus" Button 1 "1"
xsetwacom set "Wacom Intuos4 6x9 stylus" Button 2 "2"
xsetwacom set "Wacom Intuos4 6x9 stylus" Button 3 "3"

## pad = ID ? = "Wacom Intuos4 6x9 pad"
xsetwacom set "Wacom Intuos4 6x9 pad" Button 2 "key ctrl"
xsetwacom set "Wacom Intuos4 6x9 pad" Button 3 "key alt"
xsetwacom set "Wacom Intuos4 6x9 pad" Button 4 "key shift"
xsetwacom set "Wacom Intuos4 6x9 pad" Button 5 "key tab"

xsetwacom set "Wacom Intuos4 6x9 pad" AbsWheelDown "+ "
xsetwacom set "Wacom Intuos4 6x9 pad" Button 1 "key space"  # button inside touchring
xsetwacom set "Wacom Intuos4 6x9 pad" AbsWheelUp "- "


xsetwacom set "Wacom Intuos4 6x9 pad" Button 6 "key b"
xsetwacom set "Wacom Intuos4 6x9 pad" Button 7 "key t"
xsetwacom set "Wacom Intuos4 6x9 pad" Button 8 "key c"
xsetwacom set "Wacom Intuos4 6x9 pad" Button 9 "key x"
```

---

### Post by Favux on 2012-11-02
Two things come to mind.

Have you tried eliminating the white spaces?  So "+" amd "-" instead.  Does that eliminate the error message?

Also do + and - still work?  You may need to use something like "Next" and "Prior" instead.

---

### Post by Typhon on 2012-11-02
No luck; still the same. Perhaps those key aren't supported anymore. 
Command "xsetwacom list modifiers" gives a list of supported keys (or at least I think it does). There is a huge number of F<number> keys (up to f35). I don't think any keyboard has that many F<number> keys :) so I suspect they mean something else. Any ideas?

---

### Post by Favux on 2012-11-02
> No luck; still the same. Perhaps those key aren't supported anymore. 
They are suppose to be.  I don't think AbsWheel was changed to RelWheel for the Intuos.  What version of xf86-input-wacom is the Quantal default?
```
xsetwacom -V
```

You can assign unused function keys to other things.

---

### Post by Typhon on 2012-11-02
```
xsetwacom -V
0.17.0
```

AbsWheel is still AbsWheel according to The Linux Wacom Project website. AbsWUp is now AbsWheelUp and AbsWDn is AbsWheelDown.

---

### Post by Favux on 2012-11-02
There were a few of commits relating to keysyms and wheel events after 0.17.0 came out.  0.18.0 just came out.  Just not sure it would help address your issue.  But if you want you could compile xf86-input-wacom to check.  See part II. a) on the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").  You'll need to change 0.15.0 to 0.18.0 where you encounter it.

---

### Post by marcoshamas on 2012-11-16
I've a problem on Ubuntu 12.04. My Intuos4 since yesterday started going crazy. 
For example on mypaint if I select a brush and then I move away with the pen it acts like I'm not releasing the pen and it starts to move the brush icons. It's not an hardware problem, because on the same computer I've Ubuntu Natty and is working fine.


A second question is about the ratio difference there is between my tablet (16/10) and my monitor. I'm using a dual monitor 1920x1080 (16/9) with twinview on a Nvidia GTX 570.
On KDE4 I know there is a GUI with an option to Force Proportions. But how do I do if I'm using Unity or XFCE?
It's a problem that I have on 12.04 and on Ubuntu Natty. I know that the second one is not anymore supported, but for several reasons I still need to use it.

---

### Post by Favux on 2012-11-16
Hi marcoshamas,

There was a rare update to xserver-xorg-input-wacom (xf86-input-wacom) within the last week or two in 12.04.  Wonder if that has anything to do with it?  Might want to consider reinstalling it, or the older version, or upgrade it.  Also a kernel update came through last day or two.

If the Gnome tablet applet in Unity's System Settings doesn't do it you can use the same method you would use for calibration:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Calibration](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Calibration)  But instead you would find the coordinates for the correct aspect ration and use them.  You will lose some active area off the tablet.

---

### Post by marcoshamas on 2012-11-16
> **Favux said:**
>  But instead you would find the coordinates for the correct aspect ration and use them.  You will lose some active area off the tablet.

Thanks it worked! I took the coordinates from KDE and so on a 1920x1080 with an intuos4 this is what I use:
xsetwacom set "Wacom Intuos4 6x9 stylus" Area 70 65 44704 25146
xsetwacom set "Wacom Intuos4 6x9 eraser" Area 70 65 44704 25146

About the problem I had with the tablet going crazy I was wrong. It was happening also in Ubuntu Natty. But now I know what is the cause. Yesterday I tried this nib for the first time:
[http://www.wacom.com.hk/preview/file/accessories/271/Intuos4_Grip_Pen_Stroke_Nibs.jpg](http://www.wacom.com.hk/preview/file/accessories/271/Intuos4_Grip_Pen_Stroke_Nibs.jpg)

Re-inserting the previous nib the pen started to work correctly.

---

### Post by Favux on 2012-11-16
Good job.  Nice of the KDE app. to save you from doing some ratios.  :)

How 'bout that.  Nice catch on the nib.  Was that suppose to be a replacement nib for your Intuos4 stylus?  Couldn't tell from the jpg.

---

### Post by marcoshamas on 2012-11-16
> **Favux said:**
> Good job.  Nice of the KDE app. to save you from doing some ratios.  :)

Thx :)
They also offer a nice GUI for the monitors. For example if I want I can use one monitor vertical and the other horizontal, though then it wasn't able to map correctly the tablet area. 
And also using the GUI the extra buttons were not configured properly. I had to load a script.

> How 'bout that.  Nice catch on the nib.  Was that suppose to be a replacement nib for your Intuos4 stylus?  Couldn't tell from the jpg.

It was a wacom spring-loaded nib. While the others are rigid this one is flexible nib because it is composed by two parts connected with a spring. But I prefer the normal nib.

---

### Post by fonsi2099 on 2013-02-15
Do you have any recomendation how to install dual boot ubuntu and android on to Android samsung tablet?

Thank you for any help

):P

---

### Post by abexman on 2013-03-12
All of a sudden, my Wacom tablet seems funny. I need to press-click several times to get it to recognize clicks. How do I uninstall and then reinstall the latest drivers? Im on Ubuntu 12.04. X.Org X Server 1.11.3 and 3.2.0-34-generic-pae

UPDATE: doh! just noticed the little plastic tip is broke no my wacom stylus! looks like Ill need to make a mechanical fix.

---

### Post by astump97 on 2013-07-03
This is a short experience report (not a request for help).  I have a Wacom Bamboo CTH-470, and I found that when I upgraded to Ubuntu 12.04, the device worked with wired and wireless connection (wireless is via the Wireless Accessory Kit sold separately by Wacom).  The only puzzle I had was getting the keys working.  I use xsetwacom to set parameters to the bamboo.  In particular, I disable Touch and Gesture.  Reading various forums out there, I was able to set buttons for use with mypaint this way:

```
xsetwacom --set "Wacom Bamboo 16FG 4x5 Finger pad" Button 1 "key x"
xsetwacom --set "Wacom Bamboo 16FG 4x5 Finger pad" Button 3 "key e"
xsetwacom --set "Wacom Bamboo 16FG 4x5 Finger pad" Button 8 "key z"
```

Note the weird button number 8.  Supposedly the button numbers get remapped, and maybe it is button 9 for that fourth physical button, as described on the [HOW TO thread]("http://ubuntuforums.org/showthread.php?t=1515562") for the Wacom Bamboo.  Now, I was disappointed that buttons weren't working when I connected wirelessly -- but it turns out this is just because the device gets a different name that way, so one needs another script:

```
xsetwacom --set "Wacom Wireless Receiver Finger pad" Button 1 "key x"
xsetwacom --set "Wacom Wireless Receiver Finger pad" Button 3 "key e"
xsetwacom --set "Wacom Wireless Receiver Finger pad" Button 8 "key z"
```

I'm just posting this as an FYI.

---

### Post by Cu Rua on 2013-07-15
o.o Such a long thread.... 

I have 10.04 lucid and a Bamboo Capture, and would like to configure it to work in GIMP and Inkscape. 

Every time I try to configure it in either program, it gives me this screen (sorry about the huge size!): 
[IMG]http://i1351.photobucket.com/albums/p798/Rachael_Torrey/hpim6932_zpsb9d5dc49.jpg[/IMG]

---

### Post by Favux on 2013-07-15
In the Device drop down menu select the device that says Wacom blah blah stylus and in the Mode drop down select Screen.  Do the same for eraser.  That will give your pen pressure in Gimp and Inkscape.

---

### Post by Cu Rua on 2013-07-15
There is no option for Wacom blah blah stylus or eraser T.T

---

### Post by Favux on 2013-07-15
Was the tablet plugged in?

You should also be able to see the stylus and eraser device names in a terminal in the output of the commands **xinput list** or **xsetwacom list**.

---

### Post by Cu Rua on 2013-07-15
Yup, tablet's plugged in. Little blue light turns brighter blue at a touch, white when the stylus comes into range. 

```
 
rachael@rachael-desktop:~$ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Kensington      USB/PS2 Wheel Mouse         id=8    [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation            id=10    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=9    [slave  keyboard (3)]
rachael@rachael-desktop:~$ 


```

---

### Post by Favux on 2013-07-15
OK, your tablet is not recognized in Lucid because it came out after Lucid did.  You need to compile a newer Wacom kernel driver/module that supports your tablet and also update the Wacom X driver.  See:  [http://forums.linuxmint.com/viewtopic.php?f=42&t=110408](http://forums.linuxmint.com/viewtopic.php?f=42&t=110408)  You can compare your model to the ones at the top of the HOW TO by running **lsusb** in a terminal and looking at the Wacom line in the output.

Although Lucid (10.04) was a LTS it is no longer supported.  You might want to consider installing Precise 12.04 which is also a LTS, but will have 5 years instead of 2 years of support.

---

### Post by Cu Rua on 2013-07-15
D: Lucid's not supported anymore?? That's....... gah. Thanks for the heads-up. I'll just upgrade and hope my computer doesn't explode. 

Thanks for all your help!

---

### Post by eanbowman on 2014-04-03
I still get this problem with Ubuntu 13.10. My eraser behaves as a pen.

By default the Wacom Tablet PC eraser is set to perform the same action as the pen with no obvious way to change it.

You would think that this would have been added to the Wacom Tablet configuration panel somehow?

Regardless, has anyone else fixed this problem in Ubuntu 13.10?

---

### Post by thecrazydudesrd on 2014-04-12
Hi, I'm hoping that this would reach the right people for this situation.

I have a Motion LE1700 laptop that I'm trying to migrate from Win XP to Ubuntu.  It's running quite well except the pressure sensitivity.  I've done a bit of looking but I can't find a way to adjust the pressure values.  According to what I've found trying to figure out pressure issues I found this way to test pressure in Wacom tech.

xinput --list "Serial Wacom Tablet stylus" | grep -B 1 -A 5 "Pressure"

It gives me the following verbatum

Detail for Valuator 2:
Label: Abs Pressure
Range: 0.000000 - 2048.000000
Resolution: 1 units/m
Mode: absolute
Current value: 22.000000
Class originated from: 12. Type: XIValuatorClass

Now I think the issue is the 2048 levels of sensitivity is WAAAAY to high for this laptop.  Acording to what I remember, this specific tablet and original pen can only accept 512 levels...

I'm wondering if anyone would be able to help me in adjusting this?  I know I could just use the curves and 'bandage' this but I want to truly fix it.

Thank you for your time.

---

### Post by foxy123 on 2014-12-11
Hi, I wonder how Intuos Pro tablet plays with Ubuntu? I am thinking to buy my daughter either small or medium one. BTW, any advice which one and how Pro compares to normal one?

---

