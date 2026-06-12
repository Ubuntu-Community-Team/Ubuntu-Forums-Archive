---
title: "Remapping laptop keys"
date: 2011-07-16
forum: Hardware
---

### Post by Glum_Reaper on 2011-07-16
Hi all,

I wonder if someone can help me. I've been googling this but haven't managed to make it work yet.

I've been running ubuntu on my macbook for a while. Previously, things 'just worked' - pretty much. But after the dist-upgrade to 11.04, I didn't really like Unity so decided to try XFCE. I liked it so decided to stick with it. However, I can't get the keyboard to work as it did under Gnome.

The problem is with the mac alt and apple keys - I had them remapped to ALT and CTRL, but I can't get them working under XFCE.

I've used XEV to get the keycodes, and then I've put the following lines into my  /etc/rc.local file:
xmodmap -e 'keycode 133 = Control_L'
xmodmap -e 'keycode 64 = Alt_L'

But they don't seem to work. The lines don't noticeably do anything when run in a terminal either.

The majority of the solutions I've seen point to using xmodmap. So what have I done wrong?

Thanks!


TL;DR: How can I rebind the ALT and CTRL keys for XFCE on my macbook? Xmodmap isn't working for me.

---

### Post by Bucky Ball on 2011-07-16
In Xfce, have you tried going to the applications icon (if it is the same for you) Settings>Keyboard>Applications Shortcuts and having a tweak there?

Xfce is actually much less complicated when it comes to keybinding and some other things.

---

### Post by Glum_Reaper on 2011-07-16
Thanks for the suggestion Bucky Ball.

The XFCE Keyboard > Application Shortcuts control panel does recognise the apple key (as 'SUPER_L') and allow me to assign a program to it. 

However I don't know how I can use this to make it mimic the functionality of the CTRL key.

---

### Post by Bucky Ball on 2011-07-16
With ya, me either. ;)

Hang on. First you're asked for the command then the key combination. Can't you just then hit the control key? Or am I missing something?

---

### Post by Glum_Reaper on 2011-07-16
Hmmm. I've given it a go. The first prompt ('Shortcut Command') doesn't pick up anything if I press a modifier key. As a test I tried just entering a normal letter key, and assigning this to the apple key. But it doesn't work, I think the Shortcut you enter is run as if it's a program.

Also, I can't try using the CTRL key because I don't have one. ;)

---

### Post by Bucky Ball on 2011-07-16
> **Glum_Reaper said:**
> 

Also, I can't try using the CTRL key because I don't have one. ;)

Ahh, of course! 

Well, how about going to the apps icon, Settings>Xfce 4 Settings Manager>Keyboard>Applications Shortcut?

Those two never show the same shortcuts for me so you never know, it might work for you ...

---

### Post by Glum_Reaper on 2011-07-16
Thanks for the continued suggestions Bucky Ball.

I had a try with the settings manager. It seems like it is also expecting to run a program from the Application Shortcut, rather than supply a keycode.

---

### Post by Toz on 2011-07-16
If you go to Settings->Manager, Keyboard, Layout tab, you can choose a macbook layout. Does this work?

---

### Post by Glum_Reaper on 2011-07-21
Hi Toz,

Thanks for your reply. Unfortunately that does not work. It did under Gnome, and the Gnome keyboard settings panel actually had a tickbox to swap different behaviours of the macbook modifier keys. However the XFCE keyboard settings panel lacks these options.

It's frustrating because I feel it must be something quite simple! I also can't understant why the suggested answers to use xmodmap, that I keep finding, don't work.

---

### Post by enimeizoo on 2011-07-24
At what runlevel is executed the rc.local file? xmodmap needs an x server (runlevel 5 I believe).

Does it work when you type it in a terminal?

Usually, the xmodmap config is stored in a .Xmodmap file in your home directory. I believe gnome loads it by default, you have an option to do so in kde, to, but I don't know about xfce.

Hope it helps.

(edit) if you want/need to have it outside of a graphic session, xmodmap isn't the right program, you might want to have a look at loadkeys.
(edit2) I just checked, rc.local is supposed to be run before any runlevel is reached, so xmodmap can't do its job.

---

### Post by Glum_Reaper on 2011-07-25
Hi Enimeizoo,

Thanks for your very helpful response.

I wasn't sure what runlevel rc.local is called at, but as your edit says - it looks like it's not the right place to put xmodmap.

Xmodmap doesn't work though even if I just run it in the console. I'm reading the man page for loadkeys now. Thanks for the tip!

---

### Post by Glum_Reaper on 2011-07-25
Can anyone help me with loadkeys, too?

I've been googling and have read the man page. As I understand it, I can use loadkeys to load a keyboard map, either one of the pre-supplied, or a custom one. However I can't work out where I can get a sample keyboard map to customise. Dumpkeys works and spits out a lot of information, can I just do:
```
dumpkeys > file
```
Then modify this file and pass it to loadkeys? Would I need everything dumpkeys produces or just one section?

The loadkeys man page says to look in /usr/share/keymaps or /usr/src/linux/drivers/char for custom keyboard files. I've also seen references to pre-supplied ones existing in /usr/lib/kdb/keymaps. However none of these directories exist on my machine.

Thanks,

Glum

---

### Post by enimeizoo on 2011-07-25
> **Glum_Reaper said:**
> Hi Enimeizoo,

Thanks for your very helpful response.

I wasn't sure what runlevel rc.local is called at, but as your edit says - it looks like it's not the right place to put xmodmap.

Xmodmap doesn't work though even if I just run it in the console. I'm reading the man page for loadkeys now. Thanks for the tip!

In what console did you run it? if it is the virtual terminal (eg: no graphics), it is normal, you have to specify for what other display (which has to use a X server) you want it, if you have any other. I meant a terminal emulator, like konsole, xterm or something that runs through a X server. And did you get an error? Did you try the verbose option? Does "xmodmap -pke" give you an output? It should give you the whole keyboard mapping in a way that it can be fed back to xmodmap.
Again, if you do have a graphical environment, I would really advice for a .Xmodmap file. It is higher level, and I think easier. Are you actually running ubuntu? (whatever desktop version, it doesn't matter)
If xfce doesn't offer you to load the file on boot, just create a ~/.Xmodmap file with the instructions you want. It should look like that (part of mine) :

```
keycode  11 = eacute 2 eacute 2 asciitilde onehalf
keycode  12 = quotedbl 3 quotedbl 3 numbersign onethird
keycode  20 = parenright degree parenright degree bracketright hyphen
keycode  21 = equal plus equal plus braceright plusminus
keycode  22 = BackSpace NoSymbol BackSpace NoSymbol BackSpace
keycode  23 = Tab ISO_Left_Tab Tab ISO_Left_Tab Tab ISO_Left_Tab
keycode  24 = a A aring Aring adiaeresis Adiaeresis
keycode  25 = z Z z Z guillemotleft less
keycode  26 = e E e E EuroSign cent
keycode  27 = r R r R registered registered
keycode  28 = t T t T trademark Tslash

```Then, check if you have a .profile file in your home directory. If you do, add the following line (preferably in the end, with a few comments) :
```
xmodmap .Xmodmap
```You could (actually should), test the existence of the file beforehand, but it doesn't matter since xmodmap will ignore a non-existent file anyway.

Besides, if you define a keyboard configuration in your rc.local or something really low level like that, your system might override it since the keyboard detection/configuration might happen later during the booting process. So, if you want to use xmodmap, you can edit your ~/.profile or ~/.xsession . 
If you really need/want to use loadkeys (yes, I insist a bit, but it really doesn't seem to me it is needed, and touching stuff at the kernel level is often a bad idea), you would rather edit a ~/.bashrc file. The later your command is executed, the better. For the last time, it is only needed when you need to have these modifications in a virtual terminal. So if you don't use it often, just like most of ubuntu users, it is not needed.

If for some reason it you want your settings in the console, you probably want to feed it the whole dumpkeys output, where you have modified what needs to be. And, yes, you can just dumpkeys, modify, and feed it back to loadkeys.

Maybe try a 'locate keymaps' to find the directories. Or use find if locate doesn't work. I don't have these directories either, so the man is probably out of date (or written for some other distrib), but the locate command does find a lot of available keymaps.

So, for the last time, try to see if you can't get xmodmap to work unless you know you really need loadkeys.

Good luck!

---

### Post by Glum_Reaper on 2011-07-26
Hi again,

And thanks for the detailed and helpful reply.

I've been trying xmodmap through the normal 'Terminal Emulator' in the XFCE menu. (Which I now see is the Gnome terminal.) Though I've also tried it in xterm.

The strange thing is, using some more of your suggestions it seems like xmodmap is working, but it isn't.

If I do:
```
xmodmap -v -e 'keycode 133 = Control_L'
```
It comes back with:
```
! 1:  keycode 133 = Control_L
        keycode 0x85 = Control_L
!
! executing work queue
!
        keycode 0x85 = Control_L

```
Which makes it look like it's working. Futhermore, if I run xev before and after xmodmap, I get these from pressing the key in question.
Before running xmodmap:
```
state 0x40, keycode 133 (keysym 0xffeb, Super_L), same_screen YES,
```
After running xmodmap:
```
state 0x40, keycode 133 (keysym 0xffe3, Control_L), same_screen YES,
    XKeysymToKeycode returns keycode: 37
```

So it's as if it's working, but then the key still doesn't work as a CTRL. Even in the terminal, trying that key and + or - (which according to the menu, zooms in and out) just types those symbols. Nor do other programs recognise the key for their CTRL key shortcuts. "Xmodmap -pke" does spit out a list of keycodes, and running this before and after "xmodmap -e etc" does show the change.

I did try, too, creating the file (~/.xmodmap) with the command in, then adding "xmodmap .xmodmap" to my ~/.profile file. After a reboot though this didn't seem to do anything. 

I feel like I'm missing something really obvious here that is preventing xmodmap from working for me! Is it that XFCE is running in some environment where xmodmap in the terminal cannot affect it?

Again, your help is much appreciated.

---

### Post by enimeizoo on 2011-07-26
The ~/.profile and ~/.xmodmap thing won't work if it doesn't work with the terminal command, it is just normal.

But that is just weird it doesn't work. What is the output of 'xmodmap -pm' .

(edit) I wasn't paying attention to the xev output. The fact that the state is the same during the keypress and keyrelease events shows that the key isn't a modifier key. You have to add it to the modifier list.
```
xmodmap -e 'add control = Control_L'
```

After that it should work.

---

### Post by Glum_Reaper on 2011-07-29
Hi again,

I've been doing some more testing, and the weirdness of this grows. I'll explain further down. Hopefully this post won't be too much of a ramble! Firstly to the hard data (such as it is).

I've been using the 'xmodmap -pm' that you suggested, along with xev, to test the key in question before and after running each xmodmap command. Here are the results:

Before running anything (just after boot).

Xmodmap -pm:

```
xmodmap:  up to 4 keys per modifier, (keycodes in parentheses):

shift       Shift_L (0x32),  Shift_R (0x3e)
lock        Caps_Lock (0x42)
control     Control_L (0x25),  Control_R (0x69)
mod1        Alt_L (0x40),  Meta_L (0xcd)
mod2        Num_Lock (0x4d)
mod3      
mod4        Super_L (0x85),  Super_R (0x86),  Super_L (0xce),  Hyper_L (0xcf)
mod5        ISO_Level3_Shift (0x5c),  Mode_switch (0xcb)
```

I notice Super_L is listed as mod4. I don't know what this means though.
From xev, pressing the key:

```
KeyPress event, serial 33, synthetic NO, window 0x3000001,
    root 0xad, subw 0x0, time 156568, (164,-9), root:(715,311),
    state 0x0, keycode 133 (keysym 0xffeb, Super_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 33, synthetic NO, window 0x3000001,
    root 0xad, subw 0x0, time 156648, (164,-9), root:(715,311),
    state 0x40, keycode 133 (keysym 0xffeb, Super_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False
```

So next I entered the line you suggested to add a modifier: xmodmap -e 'add control = Control_L'.

Xmodmap -pm then gave me:
```
shift       Shift_L (0x32),  Shift_R (0x3e)
lock        Caps_Lock (0x42)
control     Control_L (0x25),  Control_R (0x69)
mod1        Alt_L (0x40),  Meta_L (0xcd)
mod2        Num_Lock (0x4d)
mod3      
mod4        Super_L (0x85),  Super_R (0x86),  Super_L (0xce),  Hyper_L (0xcf)
mod5        ISO_Level3_Shift (0x5c),  Mode_switch (0xcb)
```

And xev gave me:

```
KeyPress event, serial 33, synthetic NO, window 0x3600001,
    root 0xad, subw 0x0, time 196372, (169,-15), root:(720,305),
    state 0x0, keycode 133 (keysym 0xffeb, Super_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 33, synthetic NO, window 0x3600001,
    root 0xad, subw 0x0, time 196428, (169,-15), root:(720,305),
    state 0x40, keycode 133 (keysym 0xffeb, Super_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False
```

I couldn't see any difference in either output. So next I ran the original command to map the key: xmodmap -e 'keycode 133 = Control_L'

Afterwards, xmodmap -pm produced:

```
shift       Shift_L (0x32),  Shift_R (0x3e)
lock        Caps_Lock (0x42)
control     Control_L (0x25),  Control_R (0x69)
mod1        Alt_L (0x40),  Meta_L (0xcd)
mod2        Num_Lock (0x4d)
mod3      
mod4        Control_L (0x85),  Super_R (0x86),  Super_L (0xce),  Hyper_L (0xcf)
mod5        ISO_Level3_Shift (0x5c),  Mode_switch (0xcb)
```

Note that on mod4, Super_L has changed to Control_L with the same (0x85) keycode. Xev produced the following output:

```
KeyPress event, serial 33, synthetic NO, window 0x3400001,
    root 0xad, subw 0x0, time 359211, (167,-5), root:(718,315),
    state 0x0, keycode 133 (keysym 0xffe3, Control_L), same_screen YES,
    XKeysymToKeycode returns keycode: 37
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 33, synthetic NO, window 0x3400001,
    root 0xad, subw 0x0, time 359371, (167,-5), root:(718,315),
    state 0x40, keycode 133 (keysym 0xffe3, Control_L), same_screen YES,
    XKeysymToKeycode returns keycode: 37
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False
```

Again, as before, xev now shows the key to be Control_L. So it looks like it's working. And yet when I tried switching back into chromium and hitting CTRL+T, no new tab. In the terminal any CTRL+keystrokes just send the key to the console.

But this is where it gets weird, after doing the testing above I gave up and went back to what else I was doing: some 3D work in Blender. After a mistake I instinctively hit CTRL+Z, and it worked! I tried a few more shortcut keys and confirmed that yes, CTRL was now working in Blender. I switched back to chromium, even tried closing and opening, but the CTRL shortcuts still didn't work. Same in Thunar, same in the terminal. The only place CTRL works is in Blender.

So now I'm even more confused. It looks for all the world like xmodmap is working as you would expect, but the only program that picks this up is Blender!

---

### Post by enimeizoo on 2011-07-29
Okay, I think it is my bad from the beginning.

If I am right this time, you gotta do things in the right order. First you want to remove Super_L from modifier mod4.
Just to do things right, remove Control_L from modifier control. We will re-add it once we will have remapped keycode 133.
Then, you remap keycode 133 to control_L
And finally, you add control_L to the control modifier.

Just put these lines in a file, say .xmodmap and run 'xmodmap .xmodmap'
```

remove mod4 = Super_L
remove control = Control_L
keycode 133 = Control_L
add control = Control_L

```

Sorry for all the troubles, it should be ok, this time. Really sorry.

And the reason why it worked with blender is that blender probably isn't watching at the state you get when you have a keypress event, but is watching for the control key to be pressed and released. Not sure it is clear, but it probably doesn't use the modifier system, but rely on keysyms. Is blender based on Qt?

---

### Post by Glum_Reaper on 2011-07-30
Hi Enimeizoo,

I salute you, for you are a genius! :)

Following your process makes it work in all applications. I'm not sure if Blender uses Qt, but it could be.

Just so I'm clear in my head then: is my understanding below roughly correct?

The instruction I saw on various sites to use xmodmap to add the keycode for CTRL to the 'super' key was broadly correct. But because I was trying to remap a key that was already a modifier key, things were getting a little confused and so I need to remove the modifier then remap the key then re-add the modifier.

Thanks very much for all your help!

Glum

---

### Post by enimeizoo on 2011-07-31
Yep, this is right. Remapping a modifier requires some precautions. The general idea is to clear the modifier list, do your stuff with keycodes, and then reassign modifiers. Some people even advice to clear ALL of the modifiers before changing a single one, and then reassign all of them. It does save trouble, actually.

There is nothing really complicated, I just got stupidly confused for some reason. (I do appreciate the compliment, though :P )

And about blender, it doesn't, it not only use it's own graphical toolkit, but also it's own event system (qt does something special about keyboard events, too, that is why I though it could be qt). Great, I know one more useless thing, thanks to my curiosity!

glad it finally worked out!

---

### Post by macmadness86 on 2012-04-22
Thank you very much for solving this issue of exchanging the Apple Command Key with the Control Key (although it is not really an exchange, more of a shared functionality from observance of the results).

I was wondering if you geniuses could figure out a way to get the gnome "Key to choose 3rd level" with the selection "Any Alt key" working that why I can use my left alt key to select the @ sign. Its easy to do in GNOME but I would rather have XCFE running as it is simpler and quick.

thanks in advance
--macmadness86

---

