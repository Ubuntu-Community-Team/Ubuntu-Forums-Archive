---
title: "Hardy (KDE3) HP TC 1100 - definitive install guide"
date: 2008-10-13
forum: Hardware
---

### Post by mu3en on 2008-10-13
After some tribulation, finally got my hands on an HP TC1100 tablet:

[http://h18000.www1.hp.com/products/quickspecs/11755_na/11755_na.HTML](http://h18000.www1.hp.com/products/quickspecs/11755_na/11755_na.HTML)

The whole M$ Windows scam is so out of hand these days, so my very own Kubuntablet seemed the way to go.

A little research gave me two solid resources:

[http://timelady.com/blog/howtos-technical-guidestips/kubuntu-804-hp-tc1100-tablet-functions-howto/](http://timelady.com/blog/howtos-technical-guidestips/kubuntu-804-hp-tc1100-tablet-functions-howto/)

[http://ubuntuforums.org/showthread.php?t=563736](http://ubuntuforums.org/showthread.php?t=563736)

Thanks to those, and a fair bit of trial and error, it's about 95% functional. Look forward to ironing out the two remaining imperfections:

1. SD Card reader. (HP seem to rely heavily on Texas Instruments for their card readers, leaving them all pretty much useless to linux users.) There seems to be varying mileage in overcoming this firmware issue so far, so back to USB card readers for those times when it matters.

2. Unlock after screensaver/sleep. So far, I cannot figure out how to get on screen input at the password request screen. I disabled 'lock on resume' in the power manager settings (and unchecked 'Require password to stop' in the screensaver settings) to avoid the problem. (Seems Gnome manages this okay already...so maybe soon on KDE.)

To successfully create my HP Kubuntablet TC1100 I used:

1. USB CD/DVD drive.
2. Working Ethernet network with Internet access.
3. TC1100 docking station (or USB input devices).
4. Desktop or Alternate Kubuntu Hardy KDE3 CD.

Okay, preparations made, onto the install.

Phase 1: Basic Kubuntu Install.

I booted using the USB CD/DVD drive. I selected my wired card as the default network device (if you have DHCP on the network, great, otherwise manual styles) and set up the remaining preferences to my taste.

For partitioning, I used a manual setting to create a 20gb ext3 partition as / and a 19gb ext3 partition as /home. The remaining 1gb I set as swap.  (The default single partition style is fine too, I just like to keep settings and documents separate for future upgrades.)

I let the rest of the install finish normally and booted into the new system.

Phase 2: Getting functional.

Once you log into the new system, the shiny new Jockey hardware manager should pop up to tell you about the Nvidia Drivers. Before you try to enable them, make sure you have all the required repositories available (ample documentation is available in official documentation). The drivers should then install fine and will ask you for a reboot, which I did.

Once you log in again, it's nice to get the wifi up so you can get rid of the ethernet cable. Right clicking the knetworkmanager icon in the system tray and selecting the access point is all it takes.

Next, the tablet functionality: install wacom-tools with adept or in konsole:
**sudo apt-get install wacom-tools**

Then, download the xorg.conf provided at timelady.com to your home folder and run in konsole:
[B]sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.original
sudo cp ~/xorg.conf /etc/X11/xorg.conf[/B]

While the page is open, you can also get the rotate script from timelady.com and put it in your home folder (make sure you make it executable and accessible using the 'properties' entry in the dolphin contextual menu).

The final basic functionality is to get independent of the keyboard (so we're totally mobile - OH YEAAH...) install cellwriter with adept or in konsole:
**sudo apt-get install cellwriter**

As a safety measure, I went ahead and made sure to disable 'lock on resume' in the power manager settings and unchecked 'Require password to stop' in the screensaver settings.

To make cellwriter our default login method we have to edit three files and delete one:
1. /etc/kde3/kdm/Xsetup
2. /etc/kde3/kdm/Xstartup
3. /etc/kde3/kdm/kdmrc
4. /etc/default/kdm.d/20_kubuntu_default_settings
All these files must be written as root, you can do this using the 'edit as root' function in dolphin or use vi in konsole.

1. Xsetup: this runs stuff as root before the login window appears. We want cellwriter to launch so adding:
**cellwriter --keyboard-only --window-y=600 &**

to the end of the file should do do just that (the options are telling cellwriter not to use handwriting input and to put the keyboard somewhere sensible on the login screen).

2. Xstartup: this runs stuff as root before the session starts. I want to close the login cellwriter because it is run by root and because using it in your session can lead to major confusion. To do this we add:
**killall cellwriter**

under the ###commented lines at the beginning of the file, and above the if.

3. kdmrc: this configures various aspects of the login screen. It is the file used by the front end 'login manager' in kcontrol too, but is effectively overridden by 20_kubuntu_default_settings (which we will delete next). Here  we need to a. tweak some appearance settings and b. resolve the X server problem that occurs when you log out.

	a. The '[X-*-Greeter]' section should have a line:
**UseTheme=false**

and the line containing %%some theme information%% should be removed entirely.

	b. At the end of the '[X-*-Core] section' add the line:
**TerminateServer=true**

4. 20_kubuntu_default_settings: this has some special Kubuntu settings that faceplate the login. To remove these run in Konsole:
**sudo rm /etc/default/kdm.d/20_kubuntu_default_settings**

You can go and change around any other settings in kcontrol's 'login manager' module to match your visual style.

Basic mobile functionality should be ready to go, time to remove external input devices and reboot the machine. When you return to the login screen (which will look a little different anyway) you should be presented with a keyboard under the login window. After entering your password on it and hitting 'Login', the keyboard should disappear and your session should load up.

Having proved the tablet is mobile, at this point you may want to replug the external keyboard for convenience in phase 3.

Phase 3: Marginal tweaking.

Using xev in a konsole, side keys are all recognized as functional, although to different extents:
1. Dial Down = Page Down (Next)
2. Dial Up = Page Up (Prior)
3. Dial Press = Enter
4. Esc = Esc
5. Tab = Tab
6. Q = XF86LaunchA
7. 'monitor' = (no mapping, but code 151)
8. Power = Power

All of these work as expected, except the 'monitor key' and 'Q key', but for different reasons:

The Q key is simply not associated with any action, you can configure it under kcontrol's 'input actions' module: just create a new action and define the Q button as the key press.

The monitor button is not yet recognized, to map it, create a file called .xmodmap in your home folder with the text:
[B]keycode 151 = XF86HomePage
#keycode 99 = Up
#keycode 105= Down[/B]

The first line maps the 'monitor key' to something useable (XF86HomePage), I think this opens default browser at your homepage, but can now be changed using kcontrol as with the 'Q key'.
The next two line are #commented since they change the Dial Up/Down functions from Page Up/Down into Up/Down. I did this because I prefer the slower scrolling in web pages, and because I like to use the dial in general navigation. If you like, uncomment the lines.

To make sure these settings load at startup, I use a quick and dirty Autostart method:
With the KMenuEditor I created a new entry called xmodmap with the command:
**xmodmap ~/.xmodmap**

then I dragged that entry from the KMenuEditor list into ~/.kde/Autostart in dolphin and selected 'link here'.

That pretty much leaves only the three touch keys on the top of the tablet. This was by far the hardest part and I almost gave up. In the end, it wasn't actually all that hard, just need to follow instructions very closely and carefully. I hope the following explanation is easier for others.

First, download the source Wacom drivers (linuxwacom-0.8.0-3.tar.bz2) into your home folder from:
[http://linuxwacom.sourceforge.net/index.php/dl](http://linuxwacom.sourceforge.net/index.php/dl)

And install build-essential using adept or in konsole:
**sudo apt-get install build-essential**

Next, extract the source into your home folder (select 'extract here' in the dolphin context menu) and rename this folder 'wacomdriver' to make next steps simpler.

Using dolphin, navigate into ~/wacomdriver/src/xdrv/ and open wcmCommon.c with Kate.

Find the following section (I searched for 'Tablet PC buttons'):
[B]
	/* Tablet PC buttons. */
	if ( common->wcmTPCButton && !IsCursor(priv) && !IsPad(priv) && !IsEraser(priv) )
	{
		if ( buttons & 1 )
		{
			if ( !(priv->flags & TPCBUTTONS_FLAG) )
			{
				priv->flags |= TPCBUTTONS_FLAG;[/B]

Replace '**if ( buttons & 1 )**' with '**if ( buttons & 57 )**'. You can cross check that line here:
[http://ubuntuforums.org/showthread.php?t=574310](http://ubuntuforums.org/showthread.php?t=574310)

Next, open the wcmISDV4.c file in Kate.

Find the following section (I searched for Coordinate data bit check ):
[B]
	if ((n = xf86WcmSerialValidate(common,data)) > 0)
		return n;
	else
	{
		/* Coordinate data bit check */
		if (data[0] & 0x40)[/B]

And insert the following below it (above '/* pick up where we left off, minus relative values */'):

		[B]{
			if ((int)data[0] == 0xc1)
			{
				if (data[1] & 0x07)
				{
					ds = &common->wcmChannel[0].work;
					/* Now fool it into thiking it's in proximity */
					ds->proximity = 1;
					ds->buttons = ((data[1] & 0x07) << 3);
					xf86WcmEvent(common,0,ds);
				}
			}
			return common->wcmPktLength;
		}
	}[/B]

You can double check the section in a full post of an example file on page 2 at the same link:
[http://ubuntuforums.org/showthread.php?t=574310]("http://ubuntuforums.org/showthread.php?t=574310")

Next, open Konsole and navigate to ~/wacomdriver:
**cd ~/wacomdriver**

and configure the build by entering:
**./configure**

Navigate down to the xdrv folder:
**cd src/xdrv/**

And build the driver:
**sudo make wacom_drv.so**

After completing this should create wacom_drv.so in ~/wacomdriver/src/xdrv/ which you can see in dolphin.

Next KDE needs to be prepared to accept these new inputs from the driver. To do this we use xbindkeys, install using adept or in Konsole:
**sudo apt-get install xbindkeys**

Download the xbindkey configuration file from timelady.com and save it to your home folder as .xbindkeys

(To make sure we have full functionality after enabling these buttons, xournal should be installed using adept or in konsole:
**sudo apt-get install xournal**)

Using the same Autostart procedure as earlier :
With the KMenuEditor I created a new entry called xbindkeys with the command:
**xbindkeys ~/.xbindkeys**

then I dragged that entry from the KMenuEditor list into ~/.kde/Autostart in dolphin and selected 'link here'. Now we can log out to replace the stock driver with our newly built one and restart.

From the login menu select 'console login' and login at the console prompt. Next, backup the current driver:
**sudo mv /usr/lib/xorg/modules/input/wacom_drv.so ~/wacom_drv.so.stock**

And then replace it with the custom version:
**sudo cp ~/wacomdriver/src/xdrv/wacom_drv.so /usr/lib/xorg/modules/input/wacom_drv.so**

Now we can restart one last time, hopefully into a pretty much functional system:
**sudo shutdown -r now**

Phase 4. Clean Up & Final Tune.

after the reboot and login (without an external keyboard!?!) everything should now pretty much dance and sing. Apart from cosmetic changes, the only significant change I made was adding line in the /etc/kde3/kdm/Xsetup:
**~/rotate.sh &**

and replacing
**cellwriter --keyboard-only --window-y=600 &**

with
**cellwriter --keyboard-only --window-y=700 --window-x=64 &**

Which automatically presents the login screen and logs in in portrait mode (you can change the position of the login window further in /etc/kde3/kdm/kdmrc if you prefer too) which I like better than the default landscape mode.

That's it, hopefully you are now, like me, a proud Kubuntablet owner. It just gets better and better...

5. Software Selection.

My core communication and sketch functions were quickly solved, all the following can be installed using adept or in konsole:
**sudo apt-get install gimp inkscape vlc nvidia-settings skype**

I then added restricted format requirements as per the official documentation to make sure all my media plays nicely and added Japanese support via skim/anthy using the kcontrol  'Country/Region & Language' module.

6. Left Overs

As mentioned in the introduction, SD Card and locking are outstanding. I still have two unassigned buttons on the side ("Q key' & 'monitor key') which I need to decide what to use as. And of course I have my eyes and ears open in case I hear of any great software to add.

Thanks to all who contributed to make this possible, it's awesome stuff!

---

### Post by fma on 2008-12-12
Thanks for this usefull documentation.

Any idea how to show cellwriter window when lock screen is activated? I read that for gnome, it is possible to give the command 'cellwriter --xid' to show it up; what is the equivalent for KDE3?

---

