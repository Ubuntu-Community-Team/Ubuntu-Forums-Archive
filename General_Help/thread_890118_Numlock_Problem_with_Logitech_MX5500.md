---
title: "Numlock Problem with Logitech MX5500"
date: 2008-08-14
forum: General Help
---

### Post by terrrorr on 2008-08-14
Hello you all,

This post is same time a noob question and warning for all who wants to buy new Logitech MX 5500 Keyboard.

Problem: There is no Numlock key in MX 5500 keyboard
Annoyance: When i push any numberkey from numpad (intentionally or unintentionally), Ubuntu logs out current session from X. I haven't yet tested what happens when i'm using console

So... is there any other way to enable numlock than using a startup script.

---

### Post by terrrorr on 2008-08-15
Ok...

Here is more info. If i use console(eg ctrl+alt+f2), everything works fine. But when i'm running X all gets messed up (Even in terminal session). 

I thought that i could solve this out when i change keyboard layout, manufacture or layout options but... no winner...

is it Linux's, Ubuntu's or MX5500's problem... i do not know.

---

### Post by Chookah on 2008-10-08
I also have a Logitech MX5500 and am suffering this problem.
The numlock key does not exist, its been replaced by a "Clear Calculator" key, which makes the pc speaker beep every time its pressed.

If I open a text editor, the numpad keys 4 and 6 simply move the cursor the way the arrow keys would.

In SYSTEM > PREFERENCES > KEYBOARD, *Allow to control pointer using keyboard* is not enabled.  If I enable it, it controls the pointer ;)

The symbol keys on the numpad work (/ * - +) and enter, however the fullstop key does not.

---

### Post by Chookah on 2008-10-08
> **terrrorr said:**
> 
is it Linux's, Ubuntu's or MX5500's problem... i do not know.
I believe it could be a problem with ubuntu (or gnome?) as I booted into a live cd of mandriva a few days ago and the keypad worked fine...

---

### Post by Chookah on 2008-10-10
Well incase anyone reads this months/years into the future and has the same problem, i've found a workaround.

First, install numlockx
*sudo apt-get install numlockx*

Then create a script to turn it on.
*sudo gedit /etc/init.d/numlockon*

Enter these two lines of code to your blank script.  Save and close gedit.
[I]#!/bin/bash
numlockx on[/I]

Make your script executable
*sudo chmod +x /etc/init.d/numlockon*

Then type this thing that does something that makes it work..
*sudo update-rc.d /etc/init.d/numlockon defaults*



Reboot and enjoy having a functioning numpad!

---

### Post by Alehbye on 2008-10-10
> **Chookah said:**
> 

Then type this thing that does something that makes it work..
*sudo update-rc.d /etc/init.d/numlockon defaults*



When I enter this command, I get an error. Everything else completed normally.

*update-rc.d: /etc/init.d//etc/init.d/numlockon: file does not exist*

Now I know your looking at the "//" between init.d and etc, but I am copying and pasting the line. It's not there when I enter it. I've tried manually as well and still no go.

---

### Post by Chookah on 2008-10-10
> **Alehbye said:**
> When I enter this command, I get an error. Everything else completed normally.

*update-rc.d: /etc/init.d//etc/init.d/numlockon: file does not exist*

Now I know your looking at the "//" between init.d and etc, but I am copying and pasting the line. It's not there when I enter it. I've tried manually as well and still no go.
What happens if you enter this instead...
*sudo update-rc.d numlockon defaults*

---

### Post by JCM3000 on 2008-10-19
Thanks for that Chookah, it worked.

---

### Post by JPorter on 2010-07-09
There's a much simpler solution to this.

[LIST=1]
[*]Go into **System -> Preferences -> Keyboard**.
[*]In the **Layouts** tab, click **Options** on the bottom left.
[*]In the tree, find the section called **Miscellaneous Compatibility Options**.
[*]Under this section, check the option titled **Numeric keypad keys work as with Mac**.
[/LIST]

Worked perfectly for me, no muss no fuss... post and let me know if this helps any of you.

---

### Post by jpascald on 2010-07-14
HI
First of all thanks for your help.
I tried the different solutions proposed here (and yours...) but i'am afraid none of them does work.

Do you have another Idea ?

Thx a lot...

---

### Post by fragos on 2010-07-14
I purchase a Logitech K300 and after one day numlock would change the indicator but not the functioning of the numeric pad. I returned it for another K300 at Amazon and the 2nd one failed the same way. I tried the fixes above but they didn't help. I noticed the keypad function acted like a mouse and finally checked the keyboard preferences "Mouse Keys" tab and found it set. I don't know how that got set that way but once turned off the keypad works in both num lock on and off.

---

### Post by jpascald on 2010-07-15
Thx for your help, but I have already done what you proposed.
In fact what I did yesterday finally worked fine :
- Script numlockx on boot
- Disable "[I]Allow to control pointer using keyboard"
[/I]- I even modified my xorg.conf

Then some kind of magic, it worked.
This morning it doesn't work at all
I manually launched numlockx, worked, restarted to see, and no way no numeric keyboard....
then typed again and worked...... any idea, i pasted the script for numlock from here....

Any idea ?
Thx for all

---

### Post by Don Giovanni on 2010-07-22
> **JPorter said:**
> There's a much simpler solution to this.

[LIST=1]
[*]Go into **System -> Preferences -> Keyboard**.
[*]In the **Layouts** tab, click **Options** on the bottom left.
[*]In the tree, find the section called **Miscellaneous Compatibility Options**.
[*]Under this section, check the option titled **Numeric keypad keys work as with Mac**.
[/LIST]


Logitech MX5500 on Lucid, followed as above but at step 4. I just checked **Default numeric keypad keys** to get it working.

---

### Post by jpascald on 2010-07-23
Hi, thanks for your answer.

I already did what you propose, but sometimes it works immediately at startup, and sometimes i have to launch it by typing "numlockx" in a shell.
Never mind it works with that solution....

Thanks for your help

---

### Post by BridgeLife on 2010-08-01
Wow that was easy, now just for the problem with keyboard/mouse not being paired when i reboot or switch OS's...... ARG!!

---

### Post by zebx on 2010-08-02
Hello,
Same problem for me.

None solution solve my issue. I use 10.04TLS 64bit.
thanks for your support.

---

### Post by BridgeLife on 2010-08-04
> **BridgeLife said:**
> Wow that was easy, now just for the problem with keyboard/mouse not being paired when i reboot or switch OS's...... ARG!!

Wow did I speak too soon...... This worked perfectly for over 48 hours; even through multiple reboots and OS changes. Have not changed anything, then all of a it just stopped working and went back to previously behavior of non-working NUM Keys, went to the pref menu again to change it and it's still checked, tried un-checking it/re-checking/rebooting/etc/etc. Now nothing can make this work :-(

Can Ubuntu Add This Keyboard to the Keyboard Layouts under Logitech in Keyboard Pref screen, would be really useful to have a Keyboard fully supported. Not to mention the Connectivity problems with the BlueTooth Hub (Only on Ubuntu) that comes with KeyBoard/Mouse Combo; which is a completely different Bug......

Thanks in Advance

---

### Post by outleradam on 2010-08-09
> **JPorter said:**
> There's a much simpler solution to this.

[LIST=1]
[*]Go into **System -> Preferences -> Keyboard**.
[*]In the **Layouts** tab, click **Options** on the bottom left.
[*]In the tree, find the section called **Miscellaneous Compatibility Options**.
[*]Under this section, check the option titled **Numeric keypad keys work as with Mac**.
[/LIST]

Worked perfectly for me, no muss no fuss... post and let me know if this helps any of you.

Wow!  this worked well!  First thing to try!

---

### Post by jtliii on 2010-09-07
Thanks JPorter! That was the fix I was looking for.

---

### Post by Iolair_ban on 2010-10-01
Works well thanks

---

### Post by Iolair_ban on 2010-10-04
I also spoke to soon. The number pad returns to controlling the mouse instead of being a number pad, even with the mouse keys being unchecked and it being set to Mac default in preferences.
However I found something that does make it work, albeit this too may be temporary.
Under Prefrences > Keyboard > Layout [tab] > Options [button down the bottom left] > Numeric keypad layout selection > Unicode additions

This still works with all the symbols as per normal (telephone also works but it arranges the number pad like a telephone (swapped vertically). I'll see how this goes.

---

### Post by Iolair_ban on 2010-10-04
I also spoke to soon. The number pad returns to controlling the mouse instead of being a number pad, even with the mouse keys being unchecked and it being set to Mac default in preferences.
However I found something that does make it work, albeit this too may be temporary.
Under  the System Menu

Preferences > Keyboard > Layout [tab] > Options [button down the bottom left] > Numeric keypad layout selection > Unicode additions

This still works with all the symbols as per normal (telephone also works but it arranges the number pad like a telephone (swapped vertically). I'll see how this goes!!!

---

### Post by DraginMagik on 2010-12-19
i was having similar issues in that the settings suggested (Settings -> Pref -> Keyboard -> Layout -> Mis...) was not having an effect.  however, the "clear calc" key was able to act as a backspace.  so i went to the Mouse Keys tab and unchecked the box (Settings -> Pref -> Keyboard ->Mouse Keys -> Pointer can be controlled using the keypad).  numlock is now working.  woohoo!!!

i also did a restart after making the change...but then i was also crossing fingers and toes while having my cat perform a modified rain dance.  hate it when i run outta magic I.T. pixie dust.

---

### Post by Fidelis1507 on 2011-01-08
Alright, I have fought with this numlock problem for about an hour now. I have written the script for the numlock and went into system>preferences>keyboard>layout>misc. I was experimenting with default numeric keypad and numeric keypads work as with a mac, the way my keypad works is with both of these options check marked and the numlock on my keyboard off lmao, I do not know how this works out but it does. Thanks for all of your help, very much appreciated.

---

### Post by CausticVeritas on 2011-09-21
I finally figured out a fix for this, non of the other solutions worked for me but this did.  So hopefully it will help someone else.  

1) Go to System > Preferences > Keyboard
2) Go to the Mouse Keys tab
3) Uncheck "Pointer can be controlled using the keypad"

The number pad should be functioning as expected now.

Cheers!

---

