---
title: "ThinkVantage button fails on 14.04"
date: 2014-05-08
forum: Hardware
---

### Post by fbugnon on 2014-05-08
Hi all,

I use to have the [COLOR=#0000cd]**Thinkvantage**[/COLOR] button assigned to launch the Terminal, simply by using [FONT=courier new]System Preferences > Keyboard > Shortcuts > Custom Shortcuts[/FONT] (and creating a [FONT=Courier New]gnome-terminal [/FONT]shortcut).

After upgrading to 14.04, I'm still able to create the custom shortcut and have it assigned to the **[COLOR=#0000cd]Thinkvantage[/COLOR]** button (attached image) that reads "Launch 1" as usually did, _BUT_ nothing happens when I press the **[COLOR=#0000cd]Thinkvantage[/COLOR]** button (Terminal doesn't launch, as expected).

I've tried to assigned the **[COLOR=#0000CD]Thinkvantage[/COLOR]** button to perform other actions (such as launch the Home Folder) and it also didn't work.
On the other hand, assigning different shortcuts/keyboard combinations to launch the gnome-terminal work perfectly.

This has been tested on a Lenovo ThinkPad _T60_ and also on a newer _X1 Carbon_.

Any suggestion?

---

### Post by fbugnon on 2014-05-08
Sorry, forgot to add screenshot:

[ATTACH=CONFIG]252999[/ATTACH]

---

### Post by tgalati4 on 2014-05-08
Run *xev* in a terminal.  Put the mouse cursor in the box then hit the BigBlue button and post what it says.  Sounds like a simple regression.  Finding it may take some time.

---

### Post by fbugnon on 2014-05-08
> **tgalati4 said:**
> Run *xev* in a terminal.  Put the mouse cursor in the box then hit the BigBlue button and post what it says.

Thank you.

Here what I got when pressing the ThinkVantage button:
```
MappingNotify event, serial 37, synthetic NO, window 0x0,
    request MappingKeyboard, first_keycode 8, count 248

KeyPress event, serial 37, synthetic NO, window 0x4200001,
    root 0x26f, subw 0x4200002, time 328676, (51,21), root:(838,73),
    state 0x0, keycode 156 (keysym 0x1008ff41, XF86Launch1), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 37, synthetic NO, window 0x4200001,
    root 0x26f, subw 0x4200002, time 328676, (51,21), root:(838,73),
    state 0x0, keycode 156 (keysym 0x1008ff41, XF86Launch1), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```

---

### Post by tgalati4 on 2014-05-08
So xserver is correctly detecting the key press and key release of BigBlue and assigning it as XF86Launch1 which is a user-defined launch key #1.

Now compare with what xmodmap thinks key 156 is:

```
xmodmap -pk | grep 156
```

It might look like:

tgalati4@Mint14-Extensa ~ $ xmodmap -pk | grep 156
    156    	0x1008ff41 (XF86Launch1)	0x0000 (NoSymbol)	0x1008ff41 (XF86Launch1)

---

### Post by fbugnon on 2014-05-09
> **tgalati4 said:**
>  Now compare with what xmodmap thinks key 156 is:

You're right, that gives me:

```
fabio@X1-Carbon:~$ xmodmap -pk | grep 156
    156    	0x1008ff41 (XF86Launch1)	0x0000 (NoSymbol)	0x1008ff41 (XF86Launch1)
```

But I don't know exactly what to do with this...  ;)

Thanks once again.

---

### Post by tgalati4 on 2014-05-09
It is possible that the bigblue button is being hijacked by the BIOS or by ACPI and processed as an "event" similar to the way the laptop lid sensor detects when the lid is closed and starts the suspend process.

I'm not on my Thinkpad (T43p) currently, so I can't verify this, but check for files in /proc/acpi/ibm.  

For instance on this Acer laptop, I have a lid button (sensor):

tgalati4@Mint14-Extensa /proc/acpi/button/lid/LID0 $ cat state
state:      open

If you find a bigblue button defined with a state in /proc/acpi then you can be pretty sure that it is being intercepted by ACPI before the user gets to it (as an xmodmap keycode).

I had a similar problem on my T43p with my blue "Access" button.  I forget the workaournd, but I had to jump through some hoops to get it to work.  I will do some searching.

One of these methods worked for me, but I don't remember which one.  So try each one, proceed carefully, take notes, undo the stuff that doesn't work.  Good luck.

[http://www.thinkwiki.org/wiki/ThinkPad_Button](http://www.thinkwiki.org/wiki/ThinkPad_Button)

---

### Post by AgentOrange96 on 2014-06-15
Did anyone figure this issue out? I'd like to map my ThinkVantage button as well.

---

### Post by jamesf2 on 2014-07-23
First question - is there a bug for this?  I'm not seeing one, and that would be the best way to get full attention.  I love having that button available for custom behavior - guaranteed not to clash with anything else :).

Then some observations: same problem on Thinkpad X230.  The key is definitely getting through to X, as when I hit it while focused on Emacs, Emacs responds with "<XF86Launch1> is undefined" - i.e. it's getting the keypress, but somehow Unity, or whatever part of the desktop deals with shortcuts, is not.

Implicit in the original report too, and for me, I can *define* it in the Keyboard settings dialog - i.e. I can click on a shortcut to choose the key, and when I press the button, "Launch1" is assigned.  So while I'm not very familiar with the division of responsibilities, I think it's getting past the low level, and not being swallowed by ACPI.

---

### Post by jamesf2 on 2014-07-23
Not finding one, I submitted a bug here: [https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1347638](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1347638)

---

