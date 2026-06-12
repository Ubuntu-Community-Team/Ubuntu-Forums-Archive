---
title: "nvidia x server settings in karmic"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by jsimerly on 2009-10-29
Having a strange video problem since upgrading from 9.04 to 9.10.  In the NVIDIA X Server Settings app, I cannot get the X Server XVideo Settings to stick.

Whether the "Sync to VBlank" is checked or not, the hue value always resets to -1000.  First noticed this problem when playing locally-saved .flv and .mp4 files (streaming flash from 'net not affected),as skin tones are really psychedelic and blue sky looks brownish gray.

While video is playing, I start the Nvidia X Server Settings app, go into X Server XVideo settings and select reset hardware defaults, the colors in the playing video magically correct!

Stop the video, start again, and the hues are all off-color again.  Any help greatly appreciated.

---

### Post by Kaput1982 on 2009-10-30
Have you tried running nvidia settings as root?

In the terminal type "gksudo nvidia-settings" no quotes.  Make your changes and then save them to your xorg.conf.

See if that works.

---

### Post by wacky.banana on 2009-10-30
Just tried changing my nvidia settings as described above as I cannot get my choice of screen resolution settings to stick either. I get the following error message:

"Data incomplete in file /etc/X11/xorg.conf.
Undefined Device "(null)" referenced by Screen "Default Screen".

Can anyone advise how to resolve this problem please? In 9.04 I simply created a root account, opened that up through Gnome, made my changes and saved straight back to xorg. Just can't seem to do that in 9.10.

Appreciate any help.

Thanks

WB

---

### Post by jsimerly on 2009-10-30
Kaput, thanks for the suggestion.  Turned out to be a simple fix.  In the totem movie player which activates automatically when clicking on a local video file, the slider for hue value on the display tab under preferences was all the way to the left, just like it was under xserver texture settings.  Don't know why this app preference is apparently interconnected to nvidia settings, but I slid the totem hue back to the middle using the default hardware settings button and the videos look normal again.  Double-checked the nvidia settings and they, too, have normal values.

Banana, I initially had the same problem saving the xorg.conf file.  Found a great workaround somewhere else in the Ubuntu forums.

On the X Server Display Configuration, first apply the changes and make sure they give you the appearance you desired.  Then hit "Save to X Configuration File."  In the dialog box that opens up, click "Show preview" and very carefully copy every single character in that box to the clipboard.

Using your preferred command line editor, save the existing /etc/X11/xorg.conf file within that directory or move it to your home directory for safekeeping.  Create a new /etc/X11/xorg.conf and paste the clipboard contents into the new file.  Double check that it contains every single character from the nvidia preview pane.  Make sure that the new /etc/X11/xorg.conf is world readable.

Go back to the nvidia settings and just cancel your way out.

---

### Post by wacky.banana on 2009-10-30
jsimerly,

Thanks for the heads-up on my problem; appreciate it. Problem is when I hit the save to x configuration file button as you suggest I do not get a preview option. I simply get the error message I alluded to earlier.

If I click OK the whole sub-window simply disappears off screen and nothing esle happens. Very frustrating.

WB

---

### Post by oldrocker99 on 2009-10-30
My problem is that when I try to save the configuration, I get a "Failed to parse existing X config file '/etc/X11/xorg.conf'!" error message and the program exits. This happens whether I run it normally or use gksudo.

Here's my xorg.conf file:

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


Not much there. It's frustrating, to say the least. I'm going to continue to dig through the forums for a better xorg.conf file.

Anyone have any hints on why nvidia-settings is acting like this?

:guitar:

---

### Post by jsimerly on 2009-10-30
Banana and Rocker, agree completely that the behaviour of nvidia settings is very frustrating.  Unfortunately, I don't have an answer to why it behaves so badly.

However, don't give up on the workaround.  Here are a few additional steps that might get your display settings working; they worked for me.  Be very careful, as you will have root privileges when you do this.

At a command prompt, become the root administrator:

$username@yoursystem:~$sudo su -
enter your password when prompted

#cd /etc/X11
#cp xorg.conf /home/your_home_directory
#mv xorg.conf xorg.conf.backup
#cp xorg.conf.backup /home/your_home_directory

By moving the original xorg.conf into a different file name, you will probably be able to eliminate the parsing error (rocker) and get to the preview pane (banana) in the settings GUI in order to copy the contents into a new xorg.conf file.

If those steps still don't work, temporarily make the /etc/X11 directory world-writable (#chmod 777 /etc/X11) and try the nvidia-settings GUI again.  When you're done, don't forget to change back to world-readable and world-executable (#chmod 755 /etc/X11) only.

If something really bad happens and you can't log back into the graphical system, just drop to recovery prompt mode and copy the original xorg.conf that you saved in your home directory back into the /etc/X11 directory.

---

### Post by wacky.banana on 2009-10-31
Guys,

I persevered and found another way to solve this irritating problem. It's a great pity that Karmic got released with this bug in it but that's the way it is.

My end-to-end solution, using the graphical front end, was as follows:

- create a root account by opening a terminal then using the command sudo passwd root

- You will first be prompted for your own password, then asked to create a secure password for the new root account.

- Enter the new password twice then exit the terminal by using the command exit.

- next, switch user and at the graphical login prompt enter the following information: at the user prompt type root, at the password prompt type whatever password you setup for the root account. You are now logged in as a root user.

CARE - YOU CAN SCREW UP YOUR SYSTEM BIG TIME USING ROOT POWERS.I TAKE NO RESPONSIBILITY IF YOU DO SO!

- next, navigate to the xorg.conf file which is located at /etc/X11/xorg.cong

- make a copy of this file just in case things go badly wrong.

- open up the original file, clear the contents out and save the file again as an empty file, ie xorg.conf (but without anything in it).

- next open nvidia settings as normal, set your resolution, etc, then click on the save x configuration tab.

- a window will open up essentially looking for you to save the file to a location.

- within the window type /etc/X11/xorg.conf and the new settings will be saved.

PROBLEM SOLVED!

What a palaver. This process has got worse since 9.04

Hope this helps somebody else stuck with the same problem.

Once again thanks to everyone on this thread who tried to help; much appreciated.

WB

---

### Post by twidget on 2009-11-20
works for me. I used the command line method i.e
sudo cp /etc/X11/xorg.conf /home/username/xorg.conf.bu
gksudo nvidia-settings
 saved settings without errors  and display stayed the way it should be after reboot. thanks guys.:D

---

### Post by ricardisimo on 2009-11-20
How weird is this: I don't even have to use nvidia-settings, just launch it, shut it down, and then... Voilá! The blue-green skin is gone.

What's that all about? Is there a bug report in Launchpad I can append to?

---

### Post by P4man on 2010-01-27
ricardisimo, did you find a solution or open a bug report? I have the same thing, once in a while my video's look like this:

[[IMG]http://img5.imagebanana.com/img/0wew6h4r/thumb/screenshot_005.png[/IMG]](http://img5.imagebanana.com/view/0wew6h4r/screenshot_005.png)

Just opening nvidia settings (not even as root) fixes it.

---

### Post by muleyyy on 2010-03-18
Hi I have had this same problem with the resolution  not being saved

the problem is, the config file has retained the settings, i can open it up and view it in gedit, but the actual resolution remains the same!

i logged in as root user, and the resolution is remembered, but in my regular user account it defaults every time, even though the config file is saved correctly!

whats going on?!

---

### Post by wacky.banana on 2010-03-19
Chaps,

This thread just popped up in my inbox. See here for the solution to your problem, ie the sticking of settings in the non root profile:

[http://johnnydopefish.blogspot.com/2009/05/ubuntu-904-nvidia-failed-to-parse.html](http://johnnydopefish.blogspot.com/2009/05/ubuntu-904-nvidia-failed-to-parse.html)

WB

---

### Post by muleyyy on 2010-06-21
Hi I just though i ought to add an extra comment to this...

i previously had ubuntu installed alongside windows, well that could possibly be what was causing the problem, i uninstalled ubuntu, and created a dedicated partition for it on a spare hard drive that i managed to aquire. the resolution was automatically correctly selected for me!

So if your in the same boat as me, tried all these solutions and they didnt work, it might be worth trying the same thing

---

