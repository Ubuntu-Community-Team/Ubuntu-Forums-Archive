---
title: "Ubuntu 9.10 Ideazon Merc zboard gaming keyboard"
date: 2010-01-25
forum: Hardware
---

### Post by Hex0x75 on 2010-01-25
I have read over several articles on here and the web on how to get an Ideazon Merc zboard gaming keyboard to work. I have tried various 'solutions' that never worked. I did however pick up on all the knowledge that was passed around and decided I would try something on my own.

What I did, was open gEdit and create a file to load the missing keymaps for the gaming keys on the keyboard. I did this, because all of the other keys work just fine (including the multimedia keys) right out of the box on a fresh install of Ubuntu 9.10. I will attach the file so that others might use it as well. What I would like to do however, is to have it load automatically on startup of the Xsession. If anyone knows how to do this, please reply to this post. Thanks in advance.

Edit: I have found how to do this by adding it to the Startup Applications. Now, it is enabled every time I log in. Life and gaming in linux just keep getting better and better. :)

As far as the file, save it to your home directory and run it with the command: sudo ./zboard.sh
This will load the missing keymaps for the gaming keys on the left side of the keyboard.

If this has helped you, I am glad that I could contribute back to the community that has done so much for me.

Just wanted to let everyone know that since I have upgraded to 10.04, that it is still working fine and flawless. 

Thanks,
:D

---

### Post by Eireocean on 2010-02-23
Heya,

You cannot believe how long I have struggled to get this going. Ran your script last night and .... works perfectly :)

Play WoW and my keyboard not being fully functional in Linux was the only thing keeping me back.

Big thanks again.

Cheers

---

### Post by Hex0x75 on 2010-03-06
Your welcome and thanks for the feedback. That was my issue also, playing WoW with it, it was also probably what drove me to work so hard on it..hehe

---

### Post by jacebenson on 2010-04-18
Now if only this worked for each board including the Wow keyset too

---

### Post by G1z3r on 2010-05-31
How do I do this, I am so illiterate with Unbuntu its not even funny. But hey we all have to start somewhere, I just want to be albe to use all my keys on my key board.

---

### Post by Hex0x75 on 2010-07-17
> **G1z3r said:**
> How do I do this, I am so illiterate with Unbuntu its not even funny. But hey we all have to start somewhere, I just want to be albe to use all my keys on my key board.

As far as the file, save it to your home directory and run it with the command: sudo ./zboard.sh
This will load the missing keymaps for the gaming keys on the left side of the keyboard.

To have it load every time, Go to System -> Preferences -> Startup Applications and click. Once there, make sure that you are on the Startup Programs tab and then click the add button. Select a name for it (I called mine just 'zboard'), click the browse button to where the zboard.sh file is, then add a comment if you like (I made mine 'Zboard Gaming Keyboard'). Then, just click the Add button in the lower right and you are all set.

Hope this helps. If not, then let me know where you are at and I will try to help the best that I can.

Hex0x75

---

### Post by Losergamer04 on 2010-10-26
First, thanks!  But, uhhh, my "e" key on my gaming keyboard isn't working when I do a test on it.  Any ideas?

BTW I'm running 10.10... and I hope this is being monitored still!

---

### Post by Losergamer04 on 2010-10-26
Errr, OK, so it works when you use it for game keys and mapping but it doesn't work when you try to type or do an input test.  Weird.

---

### Post by Hex0x75 on 2010-11-03
It is still being monitored. I am glad that it is working for you.

---

### Post by EdTheUniqueGeek on 2011-04-29
Does this shell script just remap the keys to what they are supposed to be on a standard US keyboard or is this a remapping according to the gaming pad insert? It looks like the latter to me.
This is what has happened to me, it's why I ask.

[http://forums.linuxmint.com/viewtopic.php?f=49&t=71568](http://forums.linuxmint.com/viewtopic.php?f=49&t=71568)

---

### Post by Hex0x75 on 2011-06-14
This is a remapping for the insert keys (gaming keys) so that they will work for gaming. I originally wrote it for WoW, but use it for PWI also. Which key are you having an issue with?

Looks like you are having an issue with the 'v' key. To find out what it is happening when you are pressing the key, in the terminal type 'xev' without the '

Next, press the 'v' key and look for the line that says: state 0x0, keycode 55 (keysym 0x76, v), same_screen YES,
This tells us that keycode 55 = v. If it doesn't, then you can remap that key with xmodmap as I have done with my shellscript to make it equal v. A good example would be whatever value that the keycode returned just write a line and add it to the shell script file like this: xmodmap -e "keycode 55 = v V"
This tells the computer that whatever keycode you got when pressing the 'v' key will now be 'v' or 'V' if shift is held.

I hope this helps.

---

### Post by Sebbis1981 on 2011-08-26
Hi. 
I have just downloaded this script and i too have issues with the "e" key. however,, using shift+e gives a big E, but a small one doest work at all.

Ran xev to check the keymap and this is what it gave me:

```
FocusIn event, serial 37, synthetic NO, window 0x4600001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 37, synthetic NO, window 0x0,
    keys:  1   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

FocusOut event, serial 37, synthetic NO, window 0x4600001,
    mode NotifyNormal, detail NotifyNonlinear

```

Has anyone got any fix for this?
I have no problem using the keyboard like this in games like forsaken world, but for WoW its pretty essential for my movement.

---

### Post by Sebbis1981 on 2011-08-26
Tab not working either.
Same type of "xev-message"

---

### Post by vem0m on 2011-09-24
I have been in other distros, and jsut came back to Kubuntu 11.04 beta 2. Anyhow as for the button "e" not working I have had this issue as well, but the problem is the button for some reason in KDE is being picked up as a shortcut key for "Search".

What this means is even though you set it to "e" it is still detected as the wrong key within Kubuntu(and I would assume other distros possibly including Ubuntu). 

In KDE I did the following:
System Settings > Shortcuts and Gestures

Once there I went to "Global Keyboard Shortcuts" on the left side then I dropped the box down to "khotkeys" And set "Search" to "Default: None"

After that I reboot the system and ran the script again, and presto, working as expected. Thanks for this amazing script. It makes things easy and works well I could not imagine using my keyboard or gaming on Linux without it. :)

---

### Post by Hex0x75 on 2012-04-28
Glad that it is working great for you. That is the reason for the script to help others. Great tip by the way on disabling the search button. It will help others as well.

---

### Post by Losergamer04 on 2012-05-15
Just an update, I've had issues with 12.04 and the script.  When using the Ctrl+Alt on the keyboard portion it would resize my windows.  I changed ```
xmodmap -e "keycode 91 = Control_L"
``` to ```
xmodmap -e "keycode 91 = Control_R"
```I hope future people find this to be of use.

---

### Post by Motorhead69 on 2012-05-20
I've added the number pad onto the original shell script. 

I can't seem to get the multiply key to work properly however you can press shift,ctrl, or alt and press * and that will work. 

The divide key on the number pad has the same keycode as the "s" key on the game pad so you'll want to have numlock off while playing games.

---

### Post by neowiz73 on 2013-02-04
very useful thread on this issue.  just wanted to add some notes.
the script file isn't necessary, you can also use in Ubuntu the startup applications to add an xmodmap command to a given non-executable text file. "xmodmap ~/.xmodmap-computer-name" 

in the ~/ or home directory in terminal type touch .xmodmap-"name", name being whatever you want to call it.  But typically using your computer name. open the file with gedit or your favorite text editor of choice. the lines should be set as so:
```
!number pad
keycode 119 = KP_Delete KP_1
keycode 145 = XF86Cut KP_2
keycode 141 = XF86Copy KP_3
keycode 118 = Insert KP_4
keycode 115 = End KP_5
keycode 117 = Next KP_6
keycode 144 = Find KP_7
keycode 110 = Home KP_8
keycode 112 = Prior KP_9
keycode 146 = Help KP_0
keycode 139 = Undo KP_Decimal
keycode 143 = XF86Paste KP_Add
!keycode 136 = s KP_Divide
keycode 152 = KP_Multiply KP_Multiply

! Multimediakeys
keycode 162 = XF86AudioPlay
keycode 174 = XF86AudioStop
keycode 160 = XF86AudioMute
keycode 173 = XF86AudioPrev
keycode 153 = XF86AudioNext
keycode 176 = XF86AudioRaiseVolume
keycode 164 = XF86AudioLowerVolume

! red area (movement)
keycode 181 = q
keycode 180 = w
keycode 225 = e
keycode 166 = a
keycode 136 = s
keycode 167 = d

! 1 to 11
keycode 87 = 1
keycode 88 = 2
keycode 89 = 3
keycode 83 = 4
keycode 84 = 5
keycode 85 = 6
keycode 79 = 7
keycode 80 = 8
keycode 81 = 9
keycode 90 = 0
keycode 86 = minus

! save, load, printscreen
keycode 137 = XF86Save
keycode 138= XF86Open
keycode 107 = Print Sys_Req 

! left area (score, voice)
keycode 140 = Caps_Lock
keycode 148 = Tab
keycode 163 = Alt_L
keycode 106 = Shift_L
keycode 91 = Control_R

! right area (reload, use)
keycode 164 = r
keycode 125 = f
keycode 194 = t
keycode 195 = g
keycode 196 = v
keycode 197 = b
keycode 142 = p
keycode 198 = c
keycode 63 = space

! [end] gamepad ofkeyboard (left)
```

Also I have added the functions for the multimedia keys and I commented out the function for the previous script for the s and divide.  I personally don't hardly ever use that part of the keypad.  Just delete the ! if you wish to use that function. 

I changed the save, load and printscreen keys.  the printscreen uses the built in function of the OS to capture a screen shot.  The others should serve a purpose other than just being a letter key.  But I haven't really been able to make them work correctly.

Other thoughts: the 7 key on the keypad only works if you press shift and then the key.  This has something to do with the keycode setting.
By default it is mapped to scancode: 70x2a 0x2a 0x2a 0x2a 0xe0 0x41  which is shift + KP_7
When using sudo showkey -s the scancode when pressed is 0xe0 0x41

When I try to set the scancode to the right keycode I get the error: KDSETKEYCODE: Invalid argument  when using "sudo setkeycodes e041 144"

will investigate further at some point.  But I have a feeling it will require different drivers or adjustments in the kernel and/or firmware. 

But at least the keyboard functions are mostly mapped out.

---

### Post by neowiz73 on 2013-02-05
Well after further trial and error, it would seem even though I got the error when i did the setkeycode command, after I rebooted the 7 key on the Keypad now works like it should, but my e key stopped working correctly on the Red Keypad.  

so I did a quick showkey command and the code for that e key is 0e65.  so i did another "sudo setkeycode 0e65 225" even though I got the same error as before I then rebooted anyway.  Now I have both the 7 and e keys working like they should.  

I've tested all the general keys and such to make sure none of them stopped working.  so far so good :)

---

### Post by Davorr on 2013-02-11
Hi.
What a great job!
My Z-board works now on Debian!!

But mine is a  french "azerty" Keyboard and now have a problem with several keys...
Like Neowiz, some keys type only with the "shift" ( In my case the red area with Z-up e-left and s-down)

I don't know to use setkeycode command on debian (unknown command)

Thanck you for help! (and excuse my poor english)

---

### Post by reko420 on 2013-04-01
anyone get this to work on 12.10 i run it and it runs but it doesnt change the keys i want 5 on the left to be minus and the g to be 5 so i switch them and it dosent change them when i press.

---

