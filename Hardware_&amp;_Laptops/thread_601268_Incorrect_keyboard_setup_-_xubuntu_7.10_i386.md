---
title: "Incorrect keyboard setup - xubuntu 7.10 i386"
date: 2007-11-03
forum: Hardware &amp; Laptops
---

### Post by sandman887 on 2007-11-03
Compaq evo N600c xubuntu 7.10 i386

I am running xubuntu 7.10 great, but I noticed when I tried making an alias in bash that the apostrophe key to the right of the semi-colon button produces a wierd apostrophe, the one that slants down to the left. Also, it requires me to press it twice to even get it. Also, the tilde button does the same thing, requiring me to press it twice, although this gives the correct character, the tilde. 

I can't write any code or aliases with this problem. I tried several different US keyboard layouts, and they all do the same thing. Anybody know what to do?

Thanks.

---

### Post by bakeneko on 2007-11-04
The problem:
You are using an ordinary US keyboard. As the result of a buggy keyboard setup in Xubuntu alternate install, you have ended up with a keyboard configuration that turns apostrophe and backtick into dead keys.

More on dead keys: [http://en.wikipedia.org/wiki/Dead_keys](http://en.wikipedia.org/wiki/Dead_keys)
More on the installer: [https://wiki.ubuntu.com/SaneInstallerKeyboard](https://wiki.ubuntu.com/SaneInstallerKeyboard)

Copy and paste this line into your terminal in X:
```
$ xmodmap -e "keycode 48 = 0x0027 0x0022"
```
This should allow you to temporarily use your apostrophe key in X. You could add this to your /etc/profile to apply the fix for every X terminal, but there are better ways. The fundamental error needs to be fixed in two spots. First, invoke the following:
```
$ sudo dpkg-reconfigure console-setup
```
For "**Keyboard model**", "**Generic 105-key (Intl) PC**" is probably a safe choice, or you can pick your keyboard out of the list.
For "**The origin of the keyboard**", pick "**U.S. English**".
For "**Keyboard layout**", pick "**U.S. English**" --*this is the important one.*
For the remaining choices, accept the defaults or adjust as desired.
After completing your choices, you should see:
> * Setting up console font and keymap... [ OK ]
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
(or similar)
This may take a minute. After this is complete, switch to a tty (ctrl-alt-f1 or similar) and enter:
```
$ sudo /etc/init.d/console-setup restart
``` 
When it's done, try typing some apostrophes and double quotes. Next, you will probably want to permanently fix your keymap in X. This involves a simple fix to /etc/X11/xorg.conf, but I'll advise backing it up beforehand to be safe.
```
$ sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```
Now open /etc/X11/xorg.conf in nano or your favorite text editor.
```
$ sudo nano /etc/X11/xorg.conf
```
You should see some lines similar to this:
>   Option	"XkbVariant"	"intl"
  Option	"XkbOptions"	"lv3:ralt_switch"
Delete them, save, and exit. Now, log out of any X sessions you may be running and switch to a tty. Enter the following to restart GDM:
```
$ sudo /etc/init.d/gdm restart
```
Or, just reboot. When this is done, log in as normal and try typing some apostrophes, double quotes, backticks and tildes.

---

### Post by zesty on 2008-01-20
"Woo Hoo, it's great"

I had the same exact problem, thanks for this post.  I have no idea how to exit a tty session but I printed these instructions to followed the commands.  My keyboard seems to be working perfectly now.

---

### Post by meisert on 2008-04-10
Thanks, this partially worked for me.  Some of my keys were fixed after restarting gdm.  The strange thing is that all of my keys seem to map correctly in the tty console, but not in my X Session.  The "/" and "*" key is mapping, but the "\" and "|" are not.   

My first attempts were at changing the keyboard layout within GNOME in System->Preferences->Keyboard.  But for some reason that didn't work.  Though I thought that it had worked on my last install of Ubuntu, when I ran into the same problem.  I'd be curious if others got this problem resolved using the GNOME tools as well?

I'll look some more in the forums and may try other keyboard configurations in the console-setup tool.

---

