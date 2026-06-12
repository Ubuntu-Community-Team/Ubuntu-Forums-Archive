---
title: "Assign PgUp and PgDn keys - eeePC"
date: 2009-07-20
forum: Hardware
---

### Post by llazarte on 2009-07-20
Hello, I am quite happy with my 1008HA, except that for using **PgUp** and **PgDn** keys it is necessary to press [COLOR=Navy]**Fn**[/COLOR] simultaneously.

I use those two keys quite frequently, and am getting a pain in my arm because of this :-s

Any hint as to how could I change the behaviour of those keys?

I would like to press PgUp and PgDn without the need of pressing Fn, to get Page Up and Down. Pressing Fn together with PgUp and PgDn could produce Up and Down.

Thanks for any help!
Leonardo

---

### Post by llazarte on 2009-07-25
The solution is to **remap** some keys, that is, to choose some _keys_ on your keyboard to peform certain _actions_.

In my case, I wanted to avoid having to press Fn together with Up or Down to get PageUp or PageDown.

**Step 0**: _Choose a key_, or a key combination, to perform the desired action. In my case, I wanted to reverse the behavior of pressing Up and Fn+Up and Down and Fn+Down. That means FOUR definitions: two key definitions (Up and Down) and two key combinations (Fn+Up and Fn+Down).
[B]
Step 2[/B]: _Discover_ how your system sees those keys, using the command "**xev**" and pressing the keys whose id you want to discover. In my case pressing Up, Down, Fn+Up and Fn+Down produced the result below, which means:

1. Pressing Down produces the _kyecode_ 116, which is assigned to the _action_ Down.

KeyPress event, serial 31, synthetic NO, window 0x3a00001,
    root 0xa5, subw 0x0, time 13735531, (165,-16), root(170,32),
    state 0x0, _keycode_ 116 (keysym 0xff54, _Down_), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

2. Pressing Up produces _keycode_ 111, assigned to _action_ Up.

KeyPress event, serial 34, synthetic NO, window 0x3a00001,
    root 0xa5, subw 0x0, time 13739005, (165,-16), root(170,32),
    state 0x0, keycode 111 (keysym 0xff52, Up), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

3. Pressing Fn+Down produces _keycode_ 117, assigned to _action_ Next (page down).

KeyPress event, serial 34, synthetic NO, window 0x3a00001,
    root 0xa5, subw 0x0, time 13751243, (165,-16), root(170,32),
    state 0x0, keycode 117 (keysym 0xff56, Next), same_screen YES,
    XKeysymToKeycode returns keycode: 105
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

4. Pressing Fn+Up produces _keycode_ 112, with _action_ Prior (page up).

KeyPress event, serial 34, synthetic NO, window 0x3a00001,
    root 0xa5, subw 0x0, time 13752671, (165,-16), root(170,32),
    state 0x0, keycode 112 (keysym 0xff55, Prior), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

Once you know the keycode of the keys you would like to use, and the name of the actions you want to perform, you can assign the desired actions to the chosen keys.


**Step 3**: The following four commands will produce the desired change, valid only for the present X session:

```
# xmodmap -e "keycode 116 = Next"; xmodmap -e "keycode 111 = Down" 
# xmodmap -e "keycode 117 = Prior"; xmodmap -e "keycode 112 = Up"
```[B]

Step 3b[/B]: To get these changes for every session, after issuing the commands above, create a file called .Xmodmap (or whatever), with the following command:

```
# xmodmap -pke > .Xmodmap
```Then, create a file called .**xinitrc** in your home directory, containing just the following line:
```
xmodmap .Xmodmap
```Good luck!

> Best reference found: [http://wiki.linuxquestions.org/wiki/Configuring_keyboards#The_Xmodmap.2FSetxkbmap_Method](http://wiki.linuxquestions.org/wiki/Configuring_keyboards#The_Xmodmap.2FSetxkbmap_Method)

---

### Post by majest on 2009-11-28
> **llazarte said:**
> The solution is to **remap** some keys, that is, to choose some _keys_ on your keyboard to peform certain _actions_.

In my case, I wanted to avoid having to press Fn together with Up or Down to get PageUp or PageDown.

**Step 0**: _Choose a key_, or a key combination, to perform the desired action. In my case, I wanted to reverse the behavior of pressing Up and Fn+Up and Down and Fn+Down. That means FOUR definitions: two key definitions (Up and Down) and two key combinations (Fn+Up and Fn+Down).
[B]
Step 2[/B]: _Discover_ how your system sees those keys, using the command "**xev**" and pressing the keys whose id you want to discover.

This is interesting. I had a brainstorm just now that I would like map Page Up/Down functions to CTRL+Arrow. On the EEEPC 1000 there is this tiny duplicate CTRL button right by the arrow keys that is basically useless.... unless it could be combined with arrow keys to do page up/down. Only one hand required!

Problem is the CTRL+arrow does not have an action associated with it. After running xev, it seems the system sees it as 2 separate keypresses rather than  a single function. How can this be changed?

Basically I would like to associate CTRL+Arrow to do PageUp/Down, or map the tiny CTRL button to be a Fn key instead.

---

### Post by llazarte on 2009-11-28
> **majest said:**
> This is interesting. I had a brainstorm just now that I would like map Page Up/Down functions to CTRL+Arrow. On the EEEPC 1000 there is this tiny duplicate CTRL button right by the arrow keys that is basically useless.... unless it could be combined with arrow keys to do page up/down. Only one hand required!

Problem is the CTRL+arrow does not have an action associated with it. After running xev, it seems the system sees it as 2 separate keypresses rather than  a single function. How can this be changed?

Basically I would like to associate CTRL+Arrow to do PageUp/Down, or map the tiny CTRL button to be a Fn key instead.

I suggest that you run "xev", and then take note of how is your "tiny CTRL button" identified while you press it.

Next step is to discover where to associate the action PageUp with the arrow key. That is, on .xinitrc (or whatever), you should check if this "tiny CTRL" changes the action of a given key. Just check, for example, by redefining key "a" to produce letter "b", on 1st, 2nd, 3rd, 4th position.

---

### Post by majest on 2009-11-28
> **llazarte said:**
> I suggest that you run "xev", and then take note of how is your "tiny CTRL button" identified while you press it.

Next step is to discover where to associate the action PageUp with the arrow key. That is, on .xinitrc (or whatever), you should check if this "tiny CTRL" changes the action of a given key. Just check, for example, by redefining key "a" to produce letter "b", on 1st, 2nd, 3rd, 4th position.

Hi - thanks for your reply :)

The tiny CTRL has the  following action:
KeyPress event, serial 36, synthetic NO, window 0x3800001,
    root 0xf9, subw 0x0, time 7211977, (607,255), root:(612,278),
    state 0x0, keycode 105 (keysym 0xffe4, Control_R), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

and the large CTRL button has:
KeyPress event, serial 36, synthetic NO, window 0x3800001,
    root 0xf9, subw 0x0, time 7107284, (668,202), root:(673,225),
    state 0x0, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False


Based on a little internet searching I learned of gconf-editor, and have made CTRLR+Up execute a command (gvim). This works, however I am unable to find a command associated with a PageUp keypress. The command would appear to be Next but putting this in gconf-editor, instead of gvim, results in nothing happening.

---

### Post by majest on 2009-11-28
I found something called xte which should have solved the problem. In gconf-editor -> apps -> metacity -> global keybindings and -> keybinding commands, I assigned command1 to execute xte "key Page_Up" in response to CTRL+Up arrow. Well it does something when I press those keys but not what I want. In Firefox it seems to switch between tabs but very erratically. This is odd.

---

### Post by majest on 2009-12-01
> **majest said:**
> I found something called xte which should have solved the problem. In gconf-editor -> apps -> metacity -> global keybindings and -> keybinding commands, I assigned command1 to execute xte "key Page_Up" in response to CTRL+Up arrow. Well it does something when I press those keys but not what I want. In Firefox it seems to switch between tabs but very erratically. This is odd.

Just a little bump :)  Any ideas?

---

### Post by grantbow on 2010-08-12
Another quick bump, I'm trying to do this same thing.

---

### Post by llazarte on 2010-08-13
Hi! (grantbow) Did you try the steps in the message from July 25th, 2009 04:09 AM?

By the way (majest), the name of action for PageUp seems to be "Prior".

---

### Post by grantbow on 2010-11-02
llazarte, thank you very much for your helpful replies. I am sorry for my delayed response but my computer was on loan for a few months, delaying my progress.

I found the following:
keycode 111 action is Up     - great, no change, arrow up
keycode 116 action is Down   - great, no change, arrow down
keycode 112 action is Prior  - great, no change, Page Up
keycode 117 action is Next   - great, no change, Page Down
keycode  37 action is Control_L - this is the Ctrl key

xev is very helpful in identifying single key presses but chorded keys seem a little odd to me. I'm not sure where to go from here to make sure it's mapped via X instead of the gnome workarounds mentioned by majest.

When I do Ctrl-"arrow up" I get the following where I clearly see the Ctrl key press and release but I don't see the keycode 111 used in those two rows of 0s in the middle where I think it should be:

KeyPress event, serial 33, synthetic NO, window 0x6800001,
    root 0x103, subw 0x6800002, time 5859674, (30,48), root:(853,101),
    state 0x10, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

FocusOut event, serial 36, synthetic NO, window 0x6800001,
    mode NotifyGrab, detail NotifyAncestor

MappingNotify event, serial 36, synthetic NO, window 0x0,
    request MappingKeyboard, first_keycode 8, count 248

FocusIn event, serial 37, synthetic NO, window 0x6800001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 37, synthetic NO, window 0x0,
    keys:  3   0   0   0   32  0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

KeyRelease event, serial 37, synthetic NO, window 0x6800001,
    root 0x103, subw 0x6800002, time 5860486, (30,48), root:(853,101),
    state 0x14, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

MappingNotify event, serial 37, synthetic NO, window 0x0,
    request MappingKeyboard, first_keycode 8, count 248

---

### Post by majest on 2011-01-09
To assign PgUp/PgDown to keyboard shorcuts, here is a solution that works for Firefox:

1. Install [keyconfig]("http://forums.mozillazine.org/viewtopic.php?t=72994") extension ([http://forums.mozillazine.org/viewtopic.php?t=72994](http://forums.mozillazine.org/viewtopic.php?t=72994))

2. Open keyconfig from Tools menu

3. Add Page Up shortcut: goDoCommand('cmd_scrollPageUp') (assign to CTRL+Up Arrow)

4. Add Page Down shortcut: goDoCommand('cmd_scrollPageDown') (assign to CTRL+Down Arrow)

5. Done, restart.

While you're at it, might as well disable the FireFox Help shortcut (F1 key) which always seems to get hit by accident :)

---

### Post by unagimiyagi on 2011-06-03
> **llazarte said:**
> The solution is to **remap** some keys, that is, to choose some _keys_ on your keyboard to peform certain _actions_.

In my case, I wanted to avoid having to press Fn together with Up or Down to get PageUp or PageDown.

**Step 0**: _Choose a key_, or a key combination, to perform the desired action. In my case, I wanted to reverse the behavior of pressing Up and Fn+Up and Down and Fn+Down. That means FOUR definitions: two key definitions (Up and Down) and two key combinations (Fn+Up and Fn+Down).
[B]
Step 2[/B]: _Discover_ how your system sees those keys, using the command "**xev**" and pressing the keys whose id you want to discover. In my case pressing Up, Down, Fn+Up and Fn+Down produced the result below, which means:

1. Pressing Down produces the _kyecode_ 116, which is assigned to the _action_ Down.

KeyPress event, serial 31, synthetic NO, window 0x3a00001,
    root 0xa5, subw 0x0, time 13735531, (165,-16), root(170,32),
    state 0x0, _keycode_ 116 (keysym 0xff54, _Down_), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

2. Pressing Up produces _keycode_ 111, assigned to _action_ Up.

KeyPress event, serial 34, synthetic NO, window 0x3a00001,
    root 0xa5, subw 0x0, time 13739005, (165,-16), root(170,32),
    state 0x0, keycode 111 (keysym 0xff52, Up), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

3. Pressing Fn+Down produces _keycode_ 117, assigned to _action_ Next (page down).

KeyPress event, serial 34, synthetic NO, window 0x3a00001,
    root 0xa5, subw 0x0, time 13751243, (165,-16), root(170,32),
    state 0x0, keycode 117 (keysym 0xff56, Next), same_screen YES,
    XKeysymToKeycode returns keycode: 105
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

4. Pressing Fn+Up produces _keycode_ 112, with _action_ Prior (page up).

KeyPress event, serial 34, synthetic NO, window 0x3a00001,
    root 0xa5, subw 0x0, time 13752671, (165,-16), root(170,32),
    state 0x0, keycode 112 (keysym 0xff55, Prior), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

Once you know the keycode of the keys you would like to use, and the name of the actions you want to perform, you can assign the desired actions to the chosen keys.


**Step 3**: The following four commands will produce the desired change, valid only for the present X session:

```
# xmodmap -e "keycode 116 = Next"; xmodmap -e "keycode 111 = Down" 
# xmodmap -e "keycode 117 = Prior"; xmodmap -e "keycode 112 = Up"
```[B]

Step 3b[/B]: To get these changes for every session, after issuing the commands above, create a file called .Xmodmap (or whatever), with the following command:

```
# xmodmap -pke > .Xmodmap
```Then, create a file called .**xinitrc** in your home directory, containing just the following line:
```
xmodmap .Xmodmap
```Good luck!


If i wish to swap the left control with the left alt, is this possible?  I am able to swap the keycodes, and xev shows that the keys have been swapped, but actually nothing has changed.  Is there something that needs to be different with these special keys?  I do have a standard macbook pro keyboard.

Thanks!

---

### Post by janv on 2011-06-04
Looks like the original question's still not really solved, so I'd like to add a bit.
The original xmodmap-way (post #2) only changes the keys, so the problem of needing two hands for a page-up or page-down command returns for the regular up and down actions. It may help if you use those actions less, but I really like the suggestion of majest in post #3. The solution. however, is only partial, and I don't like the idea of an additional program while Ubuntu has a very flexible keyboard functionality built in.

I managed to replace Fn-Down with AltGr-Down using the instructions of [http://people.uleth.ca/~daniel.odonnell/Blog/custom-keyboard-in-linuxx11]("http://people.uleth.ca/%7Edaniel.odonnell/Blog/custom-keyboard-in-linuxx11"). (I don't get this link to work directly - if necessary try copy and paste.) It describes how to make a small modification to a keyboard you are already using. Since I don't know what your keyboard settings are, I'll tell you about mine, and I hope you have something to go by. My netbook is a MSI Wind u100, with Ubuntu 10.04.
System>Preferences>Keyboard tells me the keyboard model I've been using is "Generic 105-key (Intl) PC", with the "USA" layout. Since this setting is basically OK, I based the modified version on this keyboard. As follows:

a. I added the following section to the file /usr/share/X11/xkb/symbols/us (at the end)

```
partial alphanumeric_keys
xkb_symbols "netbook" {

    name[Group1]= "USA - Netbook optimized";

    include "us(basic)"

    include "eurosign(5)"

    include "level3(ralt_switch)"

    key <UP> { [ Up, Up, Prior, Prior ] };
    key <LEFT> { [ Left, Left, Home, Home ] };
    key <DOWN> { [ Down, Down, Next, Next ] };
    key <RGHT> { [ Right, Right, End, End ] };

};
```I included "eurosign(5)" because my keyboard has an eurosign on the 5-key. You may have guessed: the lines starting with "key" define what the physical key does when pressed, Shift-pressed, 3rd-level-modifier-pressed and Shift-3rd-level-modifier-pressed (3rd-level-modifier: see below).
For "USA - Netbook optimized" you can choose whatever text you want. For "netbook" as well, but you need this string in the next step.

b. I added the following text to the file /usr/share/X11/xkb/rules/evdev.xml just below the similar section with name "euro". (Or somewhere else, just make sure that the section is in the <variantlist>-tag of the layout with the name "us".)

```
        <variant>
          <configItem>
            <name>netbook</name>
            <description>Netbook optimized</description>
          </configItem>
        </variant>

```The name-tag has the value as specified in the new section in the us-file. The description will show up in the list of variants of the layout, see below.

c. Using System>Preferences>Keyboard I selected "Add" to add a layout, then "United States" under Country and then the modification appears as "USA Netbook optimized" amongst the available variants. I selected it, and the modification is added to list of layouts.
I selected this new layout and then clicked "Options". I expanded the line saying "Key to choose 3rd level" and selected "Right Alt". This specifies which modifier key changes Up to PageUp. You may select "Right Ctrl" if you wish. After closing the Keyboard settings windows, it works. Also in Firefox, by the way.

What I'm not completely happy about is that the AltGr+arrowkeys keep working even if I switch to the original layout, and that I had to change system files. The modifications may be at risk at updates. I would rather have user-specific files overriding the default ones, but I don't know how to do that.

I'm curious if you get it to work as well.

---

### Post by rocksockdoc on 2012-01-26
My "Return" key under-side plastic spring levers broke somehow, so, I had to temporarily remap some other key to the Return key:
- [**How can I temporarily map the ENTER key to the SHIFT key (see picture)?  **]("http://ubuntuforums.org/showthread.php?t=1915657")

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=211473&stc=1&d=1327612744[/IMG]

Details are in the thread listed above.

Basically, a swap of the Return key with the Shift_R failed to work reciprocally; yet a swap of the Return key with the backslash key worked just fine both ways.

Here are the commands that worked:
$ xev
(ignore the first fifty lines or so)
PRESS: \
REPORTS: keycode **[COLOR=DarkRed]51[/COLOR]** is the **[COLOR=DarkRed]backslash[/COLOR]** behavior.

PRESS: Return
REPORTS: keycode [COLOR=DarkRed]**36** [/COLOR]is the[COLOR=DarkRed] **Return** [/COLOR]behavior.[COLOR=DarkRed]

[/COLOR]So, to swap those two keys:
$ xmodmap -e "keycode 51 = Return" 
$ xmodmap -e "keycode 36 = backslash"[COLOR=DarkRed]
[/COLOR]
To make these changes permanent, I created this Xmodmap file:
$ xmodmap -pke > ~/.Xmodmap

And, then I put this line in my ~/.Xinitrc:
  xmodmap ~/.Xmodmap

This worked fine for temporary reassignment of keys.

Now it's time to try to find a Lenovo X61 tablet PC keyboard underside plastic spring for the Return key![COLOR=DarkRed]
[/COLOR]

---

### Post by rocksockdoc on 2012-01-26
Interestingly, the change was NOT permanent! 

What happened was that there was NO MAPPING on the boot screen; but as  soon as I logged into the boot screen, up popped this question of  whether to load the keyboard re-map file or not:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=211501&stc=1&d=1327639812[/IMG]

Only after loading the keyboard map file did the mapping take effect.

So I'd say it works ... barely ... but it's good enough for now.

---

