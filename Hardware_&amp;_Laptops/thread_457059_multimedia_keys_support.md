---
title: "multimedia keys support"
date: 2007-05-28
forum: Hardware &amp; Laptops
---

### Post by wykthorr on 2007-05-28
Hi,
I', running Ubuntu 7.04 on a NEC Versa P440. These machines have 5 extra keys above the keyboard (email, internet, previous track, play/pause, next track). My questions is how to setup these keys. I want the first two to start e-mail and the browser and the last three to be available in amarok as global hotkeys (pressing them in the amarok global hotkey config window doesen't do anyting).

Thanks in advance.

Regards,
Victor

---

### Post by aysiu on 2007-05-28
**Step 1**: In [the terminal](http://www.psychocats.net/ubuntu/terminal), type ```
xev
``` then press a multimedia key. Make note of the key code number (116, for example). Repeat for every multimedia key you want to use but that is not working.

**Step 2**: Create a script that maps that key to an F key by pasting this command into the terminal: ```
sudo nano /usr/local/bin/multikeys
``` This will open up an empty text file in a text editor. Paste in this text: ```
#!/bin/bash
xmodmap -e 'keycode 116=F13'
xmodmap -e 'keycode 229=F14'
xmodmap -e 'keycode 236=F15'
xmodmap -e 'keycode 178=F16'
#you can use F13 - F35
``` and modify each line for the key codes you actually have noted (the ones above are just examples). When you're done adding and modifying lines, save the file (Control-X, Y, Enter). Then, make it executable: ```
sudo chmod +x /usr/local/bin/multikeys
```

**Step 3**: Make *multikeys* an autostart application. If you're using KDE, you can symlink the script to your autostart directory: ```
sudo ln -s /usr/local/bin/multikeys ~/.kde/Autostart/multikeys
``` If you're using Gnome, add *multikeys* to System > Preferences > Session > Autostart.

You can also [use  *gconf-editor* to assign shortcuts for commands not available in System > Preferences > Keyboard Shortcuts](http://doc.gwos.org/index.php/GnomeKeyboardShortcut#B-_Using_metacity_.28the_default_GNOME_window_manager.29)

**Step 4**: Use your keyboard shortcut editor (System > Preferences > Keyboard Shortcuts in Gnome or the KMenu editor in KDE) to application (AmaroK, for example) to use the keyboard shortcuts you set before (F13, F14, etc.).

These instructions are a modification of [the ones given here for Mandriva](http://www.brunolinux.com/06-Fine_Tuning_Your_System/Multi_Media_Keys_in_Linux.html).

---

### Post by QwUo173Hy on 2007-06-04
Thanks Aysiu, you are very helpfull as always.

Using the System > Preferences > Keyboard Shortcuts in Gnome I was able to assign my special keys without any extra effort. Unfortunately, the ones for audio playback (for example) only work with Rhythmbox.

I ran the gconf editor and found that Rhythmbox was listed under 'apps' whereas Exaile was not. Is it possible for me to add this application here to give me this funcionality?

thanks,
Jarlath

<edit> I've also noticed Firefox is not listed and I have some web related multimedia keys. I guess its the same problem really but if you have any ideas .... Thanks!<edit>

---

### Post by aysiu on 2007-06-04
The standard Gnome shortcuts refer specifically to Rhythmbox (and Banshee, if you have that installed). If you want to assign shortcuts for Exaile, you'll have to figure out what commands Exaile uses and then create custom shortcuts using the instructions I gave in the previous post.

---

### Post by QwUo173Hy on 2007-06-04
I'm afraid I don't understand Aysiu. Keyboard shortcuts dont let you add in any new commands - only change the keys for existing ones. As for gnome-conf, it is not possible to add an application to it either.

So even if I knew, for example, that firefox reloaded when the command 'firefox --refresh' was issued, how do I link my F key with that ?

---

### Post by aysiu on 2007-06-04
You can add in new commands. Read the line right above **Step 4**.

---

### Post by ZeroXR on 2007-06-05
How would one go about assigning a key to the desired application?

I know the guide that was linked says to use gconf-editor to associate the command to the key... but it's just not working. I think I may be overlooking it, but any clarification would be great.

The key is "XF86AudioMedia" with a keycode of 237, I am trying to bind it to Amarok but it still references to Rhythmbox.

---

### Post by aysiu on 2007-06-05
If the key XF86AudioMedia works to launch Rhythmbox right now, then you want to disable that key in System > Preferences > Keyboard Shortcuts and then bind it in *gconf-editor* to AmaroK. See the attached screenshots for more details.

---

### Post by ZeroXR on 2007-06-05
That's weird... I did basically everything that was instructed and even double checked my screenshots and nothing worked.

Is a restart required for things to kick in? That's the only thing I haven't done.

---

### Post by aysiu on 2007-06-05
No, the changes should take instantly.

Let's see if it's a key assignment problem or a keybinding-to-command problem.

Can you try, instead of *XF86AudioMedia*, *<Control><Shift>a*? See if that will launch AmaroK. If that does, it's something to do with the key name. If it doesn't, there's something not connecting the command with the key assigned.

---

### Post by ZeroXR on 2007-06-05
Just tried your example and it's just not connecting with the command... :-(

---

### Post by QwUo173Hy on 2007-06-05
Thanks Aysiu - I had followed your post a few times and still missed that. I'll give it a try when I find out the command for firefox.

---

### Post by schdagi on 2007-06-17
Hi!

If i use the xev method u wrote nothing happens.
I mean i start xev, push my sleep button.Everythings works fine, but.
If i push any other media keys xev write nothing.Not even sense that a key were pushed.
I found this : [http://gentoo-wiki.com/HOWTO_Use_Multimedia_Keys#Introduction](http://gentoo-wiki.com/HOWTO_Use_Multimedia_Keys#Introduction)
How can i get the keyboard multimedia key scnacode and set a keycode for it?

(I'm using Ubuntu 7.04 with GNOME)

---

### Post by BrowneR on 2007-06-22
I have written an Amarok script to allow the use of multimedia keys in fiesty (and other gnome 2.18 distros).

There is no fuss at all - just load the script into amarok's script manager and configure the keys in
system-->preferences-->keyboard shortcuts

done.

get it here [http://kde-apps.org/content/show.php/Gnome+Multimedia+Keys?content=60910](http://kde-apps.org/content/show.php/Gnome+Multimedia+Keys?content=60910)
or install it directly from the Amarok script manager - its called "gnome multimedia keys".

this should be the fastest way to get it working.

any problems just send me a pm.

hope this helps. would love your feedback and bug reports.

---

### Post by aysiu on 2007-07-27
I don't know about other apps, but Rhythmbox already has the ability to pass commands through the command-line: ```
rhythmbox-client --play-pause
rhythmbox-client --next
rhythmbox-client --previous
rhythmbox-client --notify
``` For more info: ```
man rhythmbox-client
```

---

### Post by jolla on 2007-07-27
yes, this solution covers all the programs listed above not just Rhythmbox. With ReMoot and Lineak you can control the listed apps with your multimedia keys, not just Rhythmbox.

---

### Post by BrowneR on 2007-07-27
Control of Amarok can be achieved by using DCOP to send commands to the running process.
The following commands are all you need (as used by my script).
```

dcop amarok player playPause
dcop amarok player pause
dcop amarok player stop
dcop amarok player next
dcop amarok player prev

```

---

### Post by jolla on 2007-07-28
What [ReMoot ]("http://www.kde-apps.org/content/show.php/ReMoot?content=63140")does is that it combines all those DCOP (and other) calls and runs one of them dependent on which program that is running. That is, if Amarok is running it sends a "dcop amarok player playPause" if the play/pause button on your keyboard are pressed. If rhythmbox is running it sends the command "rhythmbox-client --play-pause" when the play/pause button is pressed. (needs [lineak or klineak ]("http://lineak.sourceforge.net/index.php?nav=download")running).

ReMoot also works with Xmms, Amarok, Kaffeine, Banshee, Quodlibet, Totem, Xine, Juk, Noatun and Kmplayer.

The beauty is that you can use your multimedia keys on your keyboard with more than ONE app. I like to use my  Numpad (wireless Logitech) as a remote for my music in Amarok and when I watch a movie on my PC-connected HD-TV, this is when  ReMoot comes handy, I don't have to remap those keys to work with multiple apps.

If you are inte perl programming (I'm not) check out the [source ]("http://www.kde-apps.org/content/show.php/ReMoot?content=63140")to get what it does.

Cheers!

---

### Post by QwUo173Hy on 2007-07-29
Jolla, I've been looking for something to use as a Multimedia remote control for my computer. What Logitech device is it exactly?

<edit> I found 2 decent looking devices.
[http://www.komplett.ie/k/ki.aspx?sku=338337](http://www.komplett.ie/k/ki.aspx?sku=338337)
and
[http://www.komplett.ie/k/ki.aspx?sku=307446](http://www.komplett.ie/k/ki.aspx?sku=307446)
</edit>

---

### Post by jolla on 2007-07-29
I'm using a Logitech diNovo notebook wireless at home and its great! At work I have the same but with bluetooth. 
[http://www.komplett.se/k/ki.aspx?sku=305380](http://www.komplett.se/k/ki.aspx?sku=305380)

I can recommend them both. beware of linux+BT... 

Anyway it works great with ReMoot and klineak, just love it! :-)

---

### Post by QwUo173Hy on 2007-07-29
Great, thanks! I'll look into it.

---

### Post by Narxysus on 2007-08-12
Though I didn't need to take the steps in this guide, I wanted to place this information here in case anyone else needed it: I have an Asus A6k laptop, and I wanted to map my multimedia keys and was going to go through this guide, but I discovered that there was no need.

I'm running Xubuntu Fiesty, and also installed is "hotkeys-setup" (which I would think is important).  I wanted to control XMMS via the multimedia keys, and I discovered that all I needed to do was go to Apps->Settings->Keyboard Settings and then choose the "Shortcuts" tab.  Then I added a new theme (because the default one can't be edited), then pressed "Add" to add a new shortcut.  I entered a command for XMMS (eg 'xmms -s' to stop play), pressed OK then when it asked to press the shortcut I just pressed the appropriate multimedia key and viola, it recognised and bound it.

Easy as pie!

---

### Post by rainwalker on 2007-09-03
I use KeyTouch to make my multimedia keys work with Amarok
[http://keytouch.sourceforge.net/](http://keytouch.sourceforge.net/)

---

### Post by RedSquirrel on 2007-09-03
> **aysiu said:**
> **Step 2**: Create a script that maps that key to an F key by pasting this command into the terminal: ```
sudo nano /usr/local/bin/multikeys
``` This will open up an empty text file in a text editor. Paste in this text: ```
#!/bin/bash
xmodmap -e 'keycode 116=F13'
xmodmap -e 'keycode 229=F14'
xmodmap -e 'keycode 236=F15'
xmodmap -e 'keycode 178=F16'
#you can use F13 - F35
``` and modify each line for the key codes you actually have noted (the ones above are just examples). 

Another way to do this is to create the file ~/.Xmodmap and put your settings in there. The settings in that file are loaded automatically by /etc/gdm/Xsession. If you don't use a display manager, then you can load ~/.Xmodmap in your ~/.xinitrc.

You can also create a global /etc/gdm/Xmodmap file that will be loaded for all users, but you would have to edit /etc/gdm/Xsession to load a global Xmodmap since it doesn't do that at the moment (not the last time I looked anyway ;)).

When you create ~/.Xmodmap, just put the *settings* in there, not the call to xmodmap:

```

keycode 116=F13
keycode 229=F14
...
...
```

---

### Post by tszanon on 2007-09-07
> **aysiu said:**
> You can also [use  *gconf-editor* to assign shortcuts for commands not available in System > Preferences > Keyboard Shortcuts](http://doc.gwos.org/index.php/GnomeKeyboardShortcut#B-_Using_metacity_.28the_default_GNOME_window_manager.29)
404, Not found. :(
Fortunately, Google still has it in cache. Since it's small, I'm pasting it here.
********
**HOWTO: Create Custom Keyboard Shortcuts**

The goal of this small HOWTO is to create a custom keyboard shortcut to run a software (like xmms, 3ddesk, ...) or what command line you want (xkill, transset 0.5, ...). Personally i use this trick to launch xkill, different values of transset and also alltray.

**A- Using xbindkeys, works for each desktop (KDE, GNOME, XFCE, ...)**

1- First install xbindkeys :
```
sudo apt-get install xbindkeys
```
2- Install xbindkeys-config, it's a GTK frontend for xbindkeys so it' easy to configure xbindkeys with that.
```
sudo apt-get install xbindkeys-config
```
3- Configuration Launch xbindkeys :
```
xbindkeys
```
Then launch the GUI :
```
xbindkeys-config
```

And then enjoy how it's easy to configure shortcuts with this GUI.

**B- Using metacity (the default GNOME window manager)**

In the example i give, i want to start xkill (graphical kill) using "Alt + a" shortcut.

1- Open GConf editor (Applications -> System Tools -> Configuration Editor), go to apps -> metacity -> keybinding_commands, and now choose a command, for my example I choose command_1. Edit command_1 writing xkill in order to run xkill (or every command you want to launch like in a terminal).

2- In the same directory go to global_keybindings. Edit command_1 (or the command you choose in part 1) with the wanted shortcut like that : <Alt>a (to use the windows key just edit the field with Super_L)

**Misc**

If you are looking for the name of a key, the tool xev will help you. Just type xev in a terminal then you will see an output for each key you hit. There are some output exemples of xev in the forum thread.

that's all !

Enjoy 
(Written By: [frodon]("http://ubuntuforums.org/member.php?u=23970"))

---

### Post by twiggyness2000 on 2007-09-18
Hi.  I'm working on Feisty right now with a Logitech _EX110_ and I figured I'd add my $.02:  I tried the gconf-editor, and when it didn't work I reverted all the settings and snooped around a bit.  There's another set of settings in apps>gnome_settings_daemon>keybindings which seem to perform the same function.  I cleared these (deleted the text from the field, as opposed to filling it with 'disabled') and tried the rest of the gconf-editor method again.  Success! My Audacious now responds to my multimedia keys after hours on the forum.  Hope this helps another poor soul.

---

### Post by kevinfitch83 on 2008-01-10
Thanks tszanon for mentioning xbindkeys. I was finally able to get my keyboard media quickplay buttons to work.

The only bad thing is neither xbindkeys nor xev will recognise the media quickplay buttons on my remote. Any idea how I might find their keycode? I have an hp pavilion dv6628us.

---

### Post by tszanon on 2008-01-10
> **kevinfitch83 said:**
> Thanks tszanon for mentioning xbindkeys. I was finally able to get my keyboard media quickplay buttons to work.

The only bad thing is neither xbindkeys nor xev will recognise the media quickplay buttons on my remote. Any idea how I might find their keycode? I have an hp pavilion dv6628us.

No, unfortunately I don't. My case was similar to yours: xev would recognize the event, but didn't give me the keycode. I had to guess them (hit and miss tactic :)) based on the fact that I knew the keycode of a nearby key. I was lucky.

I suggest you create a new thread for your problem. The only people still paying attention to this thread are probably only those who are still subscribed to it.

---

