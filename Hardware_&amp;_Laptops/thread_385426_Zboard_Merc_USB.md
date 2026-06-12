---
title: "Zboard Merc USB"
date: 2007-03-15
forum: Hardware &amp; Laptops
---

### Post by Moordrik on 2007-03-15
I have looked everywhere, and have come to a dead end.  I've seen mention of using xkb to get the left side of the MERC keyboard working and also mention of a patch to xkb to get it to fully recognize keyboard similar to the MERC.  The patch link is dead, and there doesn't seem to be any definitive guide out there that explains what needs to be done to get this thing working.  What I would like, if anyone knows is:

1) Does the patch for xkb that I saw (makes it recognize 16 bit scan codes) still apply considering the version of xkb that is shipping now.

2) Does anyone know of a guide that can give me a crash course in how xkb works.

3) How to determine what the scan codes are for the gaming side (left side) of the MERC.

4) What the process is to create a keyboard for xkb for the MERC is.


Any pointers to guides, personal knowledge, anything at all you can contribute to this effort would be appreciated.  I'm not going to sit around and wait for Ideazon to decide to do something if the tools to make this happen already exist in xkb.

---

### Post by Moordrik on 2007-03-15
Ok I have a few things figured out here.  First I discovered xev to get the scan codes.  That lead me to xmodmap, but that didn't suite what I was after (no repeat on keys) so I ventured to xvkbd which got almost everything working.  The only problem I have is with the WSAD, and strafing.  That doesn't seem to want to work in World of War Craft, my entire motivation to make this work.


I am binding it like this:
```

##save each binding in a file, then call it with xbindkeys -f *filename*

"xvkbd -xsendevent -text "w""
c:xxx  ### where XXX is the keycode returned by xev  

```



I've tried setting the repeat to 50 miliseconds thinking it might be too slow for wow, but it doesn't work.  The best I can get is the character flinches.  Wow does see the characters being generated, in the keyboard map I can set it all day long.

Does this need to be some sort of key down, key up event I wonder?  Can xvkbd do this?????

---

### Post by Moordrik on 2007-03-21
I see what the problem is with the red directional keys (WASD plus QE strafe).  It appears that key repeat is not enabled on them.  I checked the documentation on xvkbd regarding keyrepeating.....it says it's enabled by default, so now I am sitting here trying to understand why it doesn't seem to work????????????



Anyone have any suggestions???

---

### Post by Moordrik on 2007-03-23
Since no one seems interested I guess I give up.  I'm not a wizzard of keyboard functionality, but I at least gave it some effort.  I just don't understand why there is absolutely no one who either has a clue what "might" get me where I need go next to make this work, or who cares enough to bother to post a reply.  I expected as much from ideazon, since they cater to Windows, but I had thought someone would have at least offered "have you tried....".  Before you even **THINK** of flaming me with you should have searched the forums, I did.  I tried all the hacks, which got me close, but no cigar.  All I have asked is direction and I'll do it myself, all I got was silence.  I've used linux for a long time, in the work place, but on servers.  With all the hype I thought the time had finally come for Linux on the desktop, especially with the great things I heard about Ubuntu, the forums, etc. but I haven't seen it though.  The only posts in this thread or Meesh's (which was old and unanswered) was myself.  I even posted to his/her's to show how far I had gotten hoping someone would have a "oh yeah do this and it will work" moment.  Absolutely nothing.  Lots of views, probably people hoping that someone will figure it out for them, but nothing in a response.

As much as I hate using Windows, at least the stuff works, even if I have to deal with crappy security, viruses, and random bugs.  What choice does average joe user have really?  He/she won't have the patience to learn bash, read the cryptic garbage documentation of xvkbd or xbindkeys.  They will just throw up their hands and say.."where did I put that copy of windows".  If you really want Linux on the Desktop to suceed, then you going to have to start answering people with the tough questions.  Sure, ideazon "could" release drivers for linux, but why should they.  There is absolutely nothing in it for them.  Until they feel there are enough customers even in a particular flavor of linux they won't bother.  I could buy a different keyboard, but why should I?  I was more than willing to work on this, but for all my efforts nobody gave a S###!  

Yes, I am a gamer, it's one of the many functions I use my computer for besides C++ programming (student), work (open office works fine), and personal finance and business activities.  True, the only thing that doesn't work out is the gaming, although WoW does run sweet under Wine.  I could always dual boot, but why would I?  What's the point of maintaining two OS's?  If one does everything, and the other doesn't, why would you do it???  I'm still chained to Microsoft either way.  

This is someones opportunity to prove I misjudge this forum, and this community.  I'm still willing to do the work, all I want is a shove in the right direction to make this work.  I'm not expecting much, even if it comes to, it just can't be done would be more than the crickets I'm hearing right now.  I'll give it another week, if it's more of the same then that's it, no point in even bashing my head against the wall.  I'll just wait another decade for Linux to get it's act together.....maybe.

---

### Post by Mr. Pig on 2007-03-24
Hell, I'm interested. I googled "Gentoo ZBoard" and your post is on the first page - google must think it's worth something. I'm going to watch this thread - if you do continue to work on this please post it here. Although I'd enjoy to have the left side of my keyboard working, I can't even get my numpad to function correctly. It uses the alternate keys (Delete, Insert, ect) and not the numbers (even with num-lock on). If you do not have this problem or you know a solution please let me know.

Also note: I am not running Ubuntu (as you may have noticed from what I googled); I am running Gentoo. I've been looking for drivers for quite some time as well.

---

### Post by Lord Illidan on 2007-03-24
> **Moordrik said:**
> Since no one seems interested I guess I give up.  I'm not a wizzard of keyboard functionality, but I at least gave it some effort.  I just don't understand why there is absolutely no one who either has a clue what "might" get me where I need go next to make this work, or who cares enough to bother to post a reply.  I expected as much from ideazon, since they cater to Windows, but I had thought someone would have at least offered "have you tried....".  Before you even **THINK** of flaming me with you should have searched the forums, I did.  I tried all the hacks, which got me close, but no cigar.  All I have asked is direction and I'll do it myself, all I got was silence.  I've used linux for a long time, in the work place, but on servers.  With all the hype I thought the time had finally come for Linux on the desktop, especially with the great things I heard about Ubuntu, the forums, etc. but I haven't seen it though.  The only posts in this thread or Meesh's (which was old and unanswered) was myself.  I even posted to his/her's to show how far I had gotten hoping someone would have a "oh yeah do this and it will work" moment.  Absolutely nothing.  Lots of views, probably people hoping that someone will figure it out for them, but nothing in a response.

As much as I hate using Windows, at least the stuff works, even if I have to deal with crappy security, viruses, and random bugs.  What choice does average joe user have really?  He/she won't have the patience to learn bash, read the cryptic garbage documentation of xvkbd or xbindkeys.  They will just throw up their hands and say.."where did I put that copy of windows".  If you really want Linux on the Desktop to suceed, then you going to have to start answering people with the tough questions.  Sure, ideazon "could" release drivers for linux, but why should they.  There is absolutely nothing in it for them.  Until they feel there are enough customers even in a particular flavor of linux they won't bother.  I could buy a different keyboard, but why should I?  I was more than willing to work on this, but for all my efforts nobody gave a S###!  

Yes, I am a gamer, it's one of the many functions I use my computer for besides C++ programming (student), work (open office works fine), and personal finance and business activities.  True, the only thing that doesn't work out is the gaming, although WoW does run sweet under Wine.  I could always dual boot, but why would I?  What's the point of maintaining two OS's?  If one does everything, and the other doesn't, why would you do it???  I'm still chained to Microsoft either way.  

This is someones opportunity to prove I misjudge this forum, and this community.  I'm still willing to do the work, all I want is a shove in the right direction to make this work.  I'm not expecting much, even if it comes to, it just can't be done would be more than the crickets I'm hearing right now.  I'll give it another week, if it's more of the same then that's it, no point in even bashing my head against the wall.  I'll just wait another decade for Linux to get it's act together.....maybe.

Hell, do you think that everyone has a Zboard? If I had one, I'd try to help you. Since I don't have one, and you've already tried xev and xmodmap, the two tools I would have recommended anyway, I can only suggest using google..

If Ideazon released the drivers, there might be incentive for more users to switch to Linux, but if Ideazon hang around then it just becomes a vicious circle, imho.

Also, what's the idea that every average joe has a zboard?

I think you should be going at Ideazon, not at Ubuntu nor these forums. Perhaps noone knows how to help..I for one sure don't. I'd like to...but hell, how can I?

---

### Post by Moordrik on 2007-03-24
That's just the point.  If the linux community is going to sit around and wait for a hardware manufacturer to "see the the light", it was over before it started.  They have no motivation to even attempt it.  

Also, I don't proclaim "every average Joe" has a zboard, but just about every new machine on the market today ships with a keyboard, and a lot of those have "extra's" that work fine in windows, but not under linux.  I don't expect anyone to say "yep do this, and this, and this, and your good".  What I expected was "have you thought of this.....or take a ganders at this site for ideas..."  all I got till I blew my top was crickets.  I would have been happy if even one knowledgeable person on doing this kind of thing simply said "your just bashing your head, we aren't ready for that kind of thing yet".  That would have been at least an answer.  I haven't completely given up......just yet.  To reiterate my gripe it's simply (and there are two more articles on Digg.com today) it's irresponsible to push linux on the desktop if the support isn't going to be there.  I don't blame Ideazon, I don't blame linux, I blame the hype.  I know I'm not the only person wondering why there isn't anything out there to facilitate mapping a keyboard that's not a standard PC10X so extra's work (barring keytouch), even if it's without all the bells and whistle's like Zengine.  It is nice to see some responses regarding this finally, although it would have been better if that had been the situation from the start.  You would be surprised how many Zboard Merc owners have wanted to goto linux, but haven't because there is just no support.  I've also noticed this thread is ranking in google....although I'm not sure why, lack of competitive information I'm assuming.  Please understand one thing, I'm not bashing Ubuntu really, just the hype.  I know there are people in the OSS community you bust their collective arses to make things happen, and I wouldn't for a moment trash their efforts.  I'm focusing on the lack of support for the end user in the community when the message being delivered is come to this side, we are here for you.

A couple quick things I want to make clear.  I'm not trashing Ubuntu the OS, it's a GREAT start, solid, and very nice looking (especially if you setup beryl), the community support needs to catch up.  In a couple more years, when my BS in programming is done, and I have the experience and knowledge to accomplish this (if it's not done already) I will try again to develop a solution, even if it means creating it myself.  Heck if someone has a site that explains it, in a manner that's not hard to digest (ie well formed docs) I'll keep plowing on it.  I'm not asking for the world, just a map to it.  


On the key pad part post above you I haven't looked at that yet, but I did read a lot about setting Options under xorg.conf, you probably don't have the Option for the keypad there, so it's not being used.  If I get a second and can find that article, and try it, I will let you know what happens.  Worst case scenario on that one is using xev to get the scancodes, and xvkbd to make they do what they should (I think).  I'll look at it either way man, and post the config if I get it to work.


Moordrik.

---

### Post by Mr. Pig on 2007-03-24
I just took a look at it and there are two problems.

1. The numpad keycodes are set to the numbers on the gamepad on the Merc keyboard. (so the numpad is not functional without some form of key mapper - I've been using xmodmap).

2. Numlock DOES NOT change the keycodes for the numpad as expected. Therefore, rebinding the keycodes would remove their original intended function (delete, page down, etc).

So, I'm wondering if anyone knows if xmodmap can change what function a given keycode has based on whether numlock or capslock is enabled. In case you ever feel like developing something; I'm rather fluent in C++, Basic, PHP, and Python, however, I learned C++ with standard Windows libs and some are different (although not by much) on Linux.

[Edit]
Found it - I think. Testing now...
keycode <keycode> = <command 1> <command 2>

[Edit 2]
Yup - it worked. I'll be posting a working config soon.

---

### Post by Mr. Pig on 2007-03-24
**Look at page 4 for an application that will handle all this for you.**
--------------------------------------------------
ZBoard Config for xmodmap
**Note:** This config is not complete - it is just a sample.
All XF86 commands have yet to be tested.

*Last updated March 25, 2007 @ 5:52PM (EST/EDT)*

```
! ZBoard MERC Keyboard Config
! Created by Matt 'aka Mr. Pig' Razza

! [START] Multimedia Keys (Music)
keycode 162 = XF86AudioPlay
keycode 164 = XF86AudioStop
keycode 160 = XF86AudioMute
keycode 144 = XF86AudioPrev
keycode 153 = XF86AudioNext
keycode 176 = XF86AudioRaiseVolume
keycode 174 = XF86AudioLowerVolume
! [END] Multimedia Keys (Music)

! [START] Program Load (Custom - I, II, III) Keys
! keycode 182 =
! keycode 183 =
! keycode 184 =
! [END] Program Load (Custom - I, II, III) Keys

! [START] Numpad
keycode 245 = BackSpace KP_0
keycode 107 = Delete KP_1
keycode 188 = XF86Cut KP_2
keycode 248 = XF86Copy KP_3
keycode 106 = Insert KP_4
keycode 103 = End KP_5
keycode 105 = Next KP_6
keycode 122 = XF86ModeLock KP_7
keycode 97 = Home KP_8
keycode 99 = Prior KP_9
keycode 192 = plus
keycode 82 = minus
keycode 198 = asterisk
keycode 232 = slash
! [END] Numpad

! [START] Gamepad of Keyboard (LEFT)
! Red Area (Movement)
! keycode 231 = q
! keycode 130 = w
! keycode 122 = e
! keycode 234 = a
! keycode 232 = s
! keycode 233 = d

! Left Area (Score, Voice)
! keycode 140 = Caps_Lock
! keycode 161 = Tab
! keycode 236 = Alt_L
! keycode 112 = Shift_L
! keycode 91 = Control_L

! Right Area (Reload, Use)
! keycode 230 = r
! keycode 157 = f
! keycode 247 = v
! keycode 170 = c
! keycode 93 = t
! keycode 131 = g
! keycode 132 = b
! keycode 63 = space
! keycode 191 = p
! [END] Gamepad of Keyboard (LEFT)
```

! = comment
The keycode's commented are either unset by default or are the gamepad - the gamepad has some keycodes overlapping with the numpad. I am considering creating a program to manage the keyboard via xmodmap, much like Zboard utility. In order for me to create this program - *some* interest must be shown in the project. Please post here to show your support.

---

### Post by Moordrik on 2007-03-25
I will have to take a look at that Pig, xmodmap was one of the first solutions I employed to make the left side work, it did, but keyrepeat did not work. Which is also part of the problem I'm having now with xvkbd (even though it's supposed to be enabled by default).  I would be estatic if the problem I am seeing is just simply because I had been playing with different tools and just messed up the keyboard.  You've made my morning. =)

---

### Post by Mr. Pig on 2007-03-25
Key repeat is function for me - I think - if I hold 1 on the numpad down it does spam 1's.

I'll be creating the config for the left side (gamepad) of the keyboard now - or later today. Good luck!

---

### Post by Mr. Pig on 2007-03-25
Major problem! - The keycodes from the numpad and the left side of the keyboard overlap.

See:
```
! ZBoard MERC Keyboard Config
! Created by Matt 'aka Mr. Pig' Razza

! [START] Multimedia Keys (Music)
keycode 162 = XF86AudioPlay
keycode 164 = XF86AudioStop
keycode 160 = XF86AudioMute
keycode 144 = XF86AudioPrev
keycode 153 = XF86AudioNext
keycode 176 = XF86AudioRaiseVolume
keycode 174 = XF86AudioLowerVolume
! [END] Multimedia Keys (Music)

! [START] Program Load (Custom - I, II, III) Keys
! keycode 182 =
! keycode 183 =
! keycode 184 =
! [END] Program Load (Custom - I, II, III) Keys

! [START] Numpad
keycode 245 = BackSpace KP_0
keycode 107 = Delete KP_1
keycode 188 = XF86Cut KP_2
keycode 248 = XF86Copy KP_3
keycode 106 = Insert KP_4
keycode 103 = End KP_5
keycode 105 = Next KP_6
keycode 122 = XF86ModeLock KP_7
keycode 97 = Home KP_8
keycode 99 = Prior KP_9
keycode 192 = plus
keycode 82 = minus
keycode 198 = asterisk
keycode 232 = slash
! [END] Numpad

! [START] Gamepad of Keyboard (LEFT)
! Red Area (Movement)
! keycode 231 = q
! keycode 130 = w
! keycode 122 = e
! keycode 234 = a
! keycode 232 = s
! keycode 233 = d

! Left Area (Score, Voice)
! keycode 140 = Caps_Lock
! keycode 161 = Tab
! keycode 236 = Alt_L
! keycode 112 = Shift_L
! [END] Gamepad of Keyboard (LEFT)
```

---

### Post by Moordrik on 2007-03-25
I see that, but that's an overwhelming concern really.  It would be quite easy to load a xmodmap config when playing a game and load a regular config when not in a game.  You could even script it so that it loads a game config when starting say WoW, then set it back again when you exit the game.  What I am seeing though is that key repeat on the down red arrow is not present.  I load your config and it gives me a / but only a single one, it will not repeat.  The question I have though is is there something you can send to the keyboard to tell it to autorepeat that key, and if so what?  Is it different for every keyboard, and how would you figure out what to send if it is.  If we can figure that out, the rest is downhill.

---

### Post by Mr. Pig on 2007-03-25
Good point. In xev, when you hold a key, does it keep spamming the keycode keyDown command? It does for me - it pauses for a sec, and then starts spamming it - when I lift it up it sends the keyUp command.

I'll finish the xmodmap config and post it - maybe I'll even code a program/service to detect games and change the settings dynamically - we'll see based on the interest this receives.

---

### Post by Moordrik on 2007-03-25
On most keys yes autorepeat is on, but specifically the red Down arrow is not autorepeating.  I've even tried to explicitly tell it to autorepeat again, this time using the following

```
xset r on 232
```
that is, if I'm not mistaken, the keycode for the red down arrow, also slash on the num pad


this is what I am getting when I run xev on that specific key

```
KeyPress event, serial 29, synthetic NO, window 0x2800001,
    root 0x156, subw 0x0, time 2333263955, (169,-11), root:(174,37),
    state 0x0, keycode 232 (keysym 0x2f, slash), same_screen YES,
    XKeysymToKeycode returns keycode: 61
    XLookupString gives 1 bytes: (2f) "/"
    XmbLookupString gives 1 bytes: (2f) "/"
    XFilterEvent returns: False

KeyRelease event, serial 29, synthetic NO, window 0x2800001,
    root 0x156, subw 0x0, time 2333263955, (169,-11), root:(174,37),
    state 0x0, keycode 232 (keysym 0x2f, slash), same_screen YES,
    XKeysymToKeycode returns keycode: 61
    XLookupString gives 1 bytes: (2f) "/"
    XFilterEvent returns: False

```

When I press that key I get the keydown and keyup right after each other no matter how long I hold that key down.

Could it be your loading something different in your xorg.conf???  Can you paste the keyboard section from your xorg.conf setup so I can compare and see if I have something wonky loading?


I dropped out of X for a bit to run showkey -s and see if the overlap between the num pad and game keys were in fact the same, which they are (darn).  Had a thought that if the Hex values were different slightly could map the overlap ones to unused keycodes.  It was a hail Mary idea, but oh well.

---

### Post by Mr. Pig on 2007-03-25
Sure thing, it's auto-repeating for me. Give me a sec to post my xorg.conf file - I think I have 101-key keyboard.

```
Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection
```
```
Section "ServerLayout"
	.  .  .
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection
```

I do not remember entering that in my xorg.conf file oddly enough I could have sworn I typed more than that in the InputDevice section.

---

### Post by Moordrik on 2007-03-25
```
Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection
```

Is what I have.

And 
```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

```

---

### Post by Mr. Pig on 2007-03-25
When I get a chance tonight I'll look into the xorg settings.

[Edit]
There is no real change between mine and yours - the only "difference" is the Option         "XkbOptions" "lv3:ralt_switch" line but that *shouldn't* be causing any problems. I wonder what's wrong with your keyboard/set-up.

---

### Post by Moordrik on 2007-03-25
I think with all the playing around I've done over the past couple weeks I may have hosed my install causing the difference between what your seeing and myself.  It's the only explanation I can think of for why autorepeat on the red arrows is working for you, but not myself.

If that's the case I guess I'm going to have to purge and reinstall and pick up where I left off again.  It's gonna take a few days though.  Let's see if I can get to where you are.

---

### Post by Mr. Pig on 2007-03-25
Alright, also note that I am not running Ubuntu that auto configures everything so who knows what the Ubuntu installed could have done.

[Edit]
I will begin work on a basic keyboard xmodmap switcher soon - one that will fit my current needs and that I will be able to expand on later.

---

### Post by Moordrik on 2007-03-28
Some time ago I had sent a support request into Ideazon regarding the Merc keyboard and linux support.  Basically I was curious how it worked so I could try to figure it out.  I updated the request when Mr. Pig related that there were keys that overlap (number pad and game pad).  This is what they sent me today regarding my requests for information.  They seem ready to support anyone who has the skill and desire to work on support for this.  I've blacked out my personal email address as well as the developer who provided the answer though to protect privacy.  If anyone truly wants to champion this let me know and I will provide the unadultered information.


Enclosed: saved ODI file of email in a zip file(sorry don't have PDF or another open solution on this machine atm)

---

### Post by Mr. Pig on 2007-03-28
Could you change the format at all (TIFF, JPEG, Word Document?) - I can't open that file - as I hope I made clear I am very involved in creating a solution at the moment.

---

### Post by Moordrik on 2007-03-28
Sending you the message in HTML with everything included.

---

### Post by Mr. Pig on 2007-03-28
You have my contact information?

[EDIT]
Thanks much.

---

### Post by Moordrik on 2007-03-28
Updated Letter From Ideazon.  This one is in HTML so anyone should be able to read it (don't mind the activex warning.....I can't kill it (copied from GMAIL)).

---

### Post by Moordrik on 2007-03-29
This seems strange.....the hex codes from xev and the ones provided by Ideazon are not the same.  I think I understand what they are saying, in a odd kind of way.  The question is how to Get Ubuntu to view what the keyboard is sending the "correct" way.  I'm sure this isn't and oddity since it conforms to a "standard", so what needs to be done to make this see eye for eye???

---

### Post by Mr. Pig on 2007-03-29
I wish I knew... I'll be spending next week googling a lot of **** and post any progress here.

To be honest - I have no idea how the e-mail they sent you helps us. It seems like it's about Windows only - Linux does not have multimedia codes linked to the keyboard my default, and I can't get the codes to match either.

Just a thought - what keyboard driver does Windows give the keyboard - more or less - what driver should we set xOrg to? 102/103? Or what - maybe xOrg is just smashing the keys together because of the driver. I doubt that will accomplish anything but it's worth a try.

---

### Post by Moordrik on 2007-03-30
I'm just guessing at this but it almost seems like the issue here isn't that it's a "windows" thing, but how the keyboard driver is looking at what it is receiving.  They referrence 0C as the code page they conform to in the HID Spec, but we don't see those Hex codes when we use Xev against the keyboard.  I'm wondering if this is a issue of kbd not recognizing this, it being a "needs to be developed further" problem with USB support of HID devices, or what it is at this point.  I was really hoping someone with some background in how this works would take a look at this and either come forward and give some feedback on what is going on here.  But if need be a reading we shall go, hopefully it's documented somewhere.

---

### Post by Lord Illidan on 2007-03-30
How about getting them to install linux on a computer and try out their own keyboard and write a driver for it?

Cost - their own time, only...Linux is free

I mean, I'd like to help, but I have no zboard keyboard, and wouldn't need one anyway, and even if I had one, I doubt I'd be able to help.

Get them tor realise that if Linux is supported, it will be a boon to them. When I see that a manufacturer has linux compatible hardware, I'll buy more readily from it.

---

### Post by Moordrik on 2007-03-30
I understand what your saying, and I agree it would be best if they directly support it with their own efforts, but from what I have seen on their forums they have their hands full atm trying to get their Vista Drivers stable and debugged.  I'm not saying they won't dive in eventually, but at this point all they are offering (at least in their response) is technical support to the community to see this through.  
 
I understand where you coming from as far as assitance.  I was actually hoping you might have an idea of what the problem "could" be, call it a hail marry if you will.  I don't know about Pig (he/she seems to have more experience than I) but I am pretty sure I'm in over my head as far as knowledge, but I'm going to try to learn what I need asap.  If anyone knows someone, or if they are versed in creating keyboard drivers and mappings for linux and Xorg please, if you would give pointers where you can.  This is completely alien and untested waters.

---

### Post by Mr. Pig on 2007-03-31
Well, I have the basic layout for my program done - about two or so hours spent on it and if people have a working xModMap it will decide when to enable the game keypad and when to enable the numpad. That's pretty much all I need at the moment. Expect it by Monday because I'll finally have the weekend to work on it.

---

### Post by Moordrik on 2007-03-31
Wow Pig that was FAST. I only wish I could figure out why certain red arrows on my Merc don't play nice (no key repeat).

---

### Post by Mr. Pig on 2007-04-01
Yeah, they repeat correctly for me - I've been playing UT 2004 (in other words -> the red keys work) for all of today (so maybe tuesday) depends if I can get motivated to finish it.

It is function however, just like missing the whole config file parsing system that's pretty much the only reason I'm making it. XD The sad part is I already have classes that do ALL of this on Windows in my mrStandard.dll I made.... if only it would compile here.

For you gentoo users:
I will be making an ebuild so keep your overlay's ready ;)

For everyone else:
standard make, make install stuff

[EDIT]
Yeah, expect it by tom; all the code is complete I just need to connect it all together and do some final testing...

---

### Post by Moordrik on 2007-04-01
Yeah thinking about using a different distro of Ubuntu.  Put XUbuntu on the kids computer, that use XFCE, that's what your using for your desktop correct?  It might be just something in all the autosetup features of Ubuntu, if all else fails I might try Gentoo, or (don't want to) fedora core 6.

---

### Post by Lord Illidan on 2007-04-02
> **Mr. Pig said:**
> Yeah, they repeat correctly for me - I've been playing UT 2004 (in other words -> the red keys work) for all of today (so maybe tuesday) depends if I can get motivated to finish it.

It is function however, just like missing the whole config file parsing system that's pretty much the only reason I'm making it. XD The sad part is I already have classes that do ALL of this on Windows in my mrStandard.dll I made.... if only it would compile here.

For you gentoo users:
I will be making an ebuild so keep your overlay's ready ;)

For everyone else:
standard make, make install stuff

[EDIT]
Yeah, expect it by tom; all the code is complete I just need to connect it all together and do some final testing...

Great work, mr pig, when I get a zboard, I will know where to look :)

---

### Post by Mr. Pig on 2007-04-02
> **Moordrik said:**
> Yeah thinking about using a different distro of Ubuntu.  Put XUbuntu on the kids computer, that use XFCE, that's what your using for your desktop correct?  It might be just something in all the autosetup features of Ubuntu, if all else fails I might try Gentoo, or (don't want to) fedora core 6.

Yeah, I use XFCE4.4 - you should keep your current Ubuntu install for a little bit though to see if we can fix the problem. It'd be nice to be able to tell people why it's not working.:)

[EDIT]
It's 100% functional now. All I need to do is decide where I want to put the config files and create the make files as well as an ebuild.

---

### Post by Mr. Pig on 2007-04-02
Download now and test it!
[http://www.valdegames.com/pig/wordpress/2007/04/02/merc-zboard-%e2%80%9cdriver%e2%80%9d-finished/](http://www.valdegames.com/pig/wordpress/2007/04/02/merc-zboard-%e2%80%9cdriver%e2%80%9d-finished/)

Now we need to get your xmodmap working Moordrik

---

### Post by Mr. Pig on 2007-04-04
For those with the key repeat problem (Moordirk for one) please let me know if you can get it working. I think I will add an option for the next version to have it update (remove and then re-add) key repeat to all changed keys; even though xmodmap should handle it.

Example for keycode 128:
```
xset -r 128
xset r 128
```

---

### Post by Moordrik on 2007-04-06
I tried stripping keyrepeat xset -r 232 then adding it again xset r 232 but nothing changed.

---

### Post by Moordrik on 2007-04-06
I have completely blown away Ubuntu and reinstalled 6.10, still same problem.  I have NO idea what is being set that is making this not work.........sigh

---

### Post by Mr. Pig on 2007-04-06
What version of xorg are you running? (I have no idea what the default is for Ubuntu)

---

### Post by Moordrik on 2007-04-07
This is what comes standard in Ubuntu 6.10

X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 x86_64 
Current Operating System: Linux Ubuntu64-610-Chef 2.6.17-11-generic #2 SMP Thu Feb 1 18:03:05 UTC 2007 x86_64
Build Date: 07 July 2006
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Module Loader present

---

### Post by Mr. Pig on 2007-04-07
Hmmm... I'm running 7.1 - I could upgrade to 7.2....

7.1 and 7.1.1 should be the same basic install... weird.

---

### Post by Moordrik on 2007-04-07
I am about to drop Gentoo onto this box to see if it's a distro issue or something else.

---

### Post by Mr. Pig on 2007-04-07
That sounds like a plan make sure you use the minimal install disk...

Don't use the graphical installer.

---

### Post by cilquirm on 2007-04-09
I've got a zboard merc keyboard also, playing ( or trying to play ) WoW in Linux.

I'm also running Ubuntu ( 7.04 beta -- Fiesty Fawn ) and I came across the same problem with only WSAD keys repeating, namely the E & D keys.

One thing I did notice was that the keyboard itself is not sending the codes to repeat, that is to say, soon as I press the red W or red Q key, only one keycode is sent, and that's all she wrote.


Also, on Fiesty Fawn, the 'driver' that I downloaded from Mr. Pig's site gives me the "commandline:1" error, but I'm still investigating that.

I'd be glad to help test or try things out to try and get a solution working.

Kudos to you guys for all your hard work.

---

### Post by Mr. Pig on 2007-04-10
It's not that the keyboard is not sending the key repeats, it's that xorg ignores them. On my Gentoo install I have all the keys on the zBoard repeating with no problems.

In terms of my "driver" please send me the command line you used to launch it and all of it's output. I can direct you from there. As I said before I haven't been able to test it other than what I can do on my Gentoo box. So as much data you can give me on this problem the better... seems like an xmodmap problem...

Small update to the driver:
[http://www.valdegames.com/pig/wordpress/2007/04/10/merc-zboard-driver-version-011/](http://www.valdegames.com/pig/wordpress/2007/04/10/merc-zboard-driver-version-011/)

To make sure you always have the latest version keep an eye on:
[http://www.valdegames.com/pig/wordpress/](http://www.valdegames.com/pig/wordpress/)

---

### Post by ineluki12 on 2007-05-17
I've never dealt with this stuff before, so this comment may seem totally noobish, but have you tried switching your 'legacy support for usb devices'--or whatever it's called--in the BIOS, Moordrik? I'm wondering if this has an effect on the way the OS receives the signals from your keyboard. Again, I have NO idea what I'm talking about, but if you've tried everything else software-wise, you might give this a shot. :-k

EDIT: I'm addressing your problem achieving consistent results with the non-repeating keys.

---

### Post by Mr. Pig on 2007-05-17
That's a good idea, although I don't think it may make a differnece - everything is worth trying.

---

### Post by ac_dispatcher on 2007-05-17
Mr. Pig

I found this thread a-la google.  Let me say thank you. 

I am also having the repeating problem with the red arrow keys in Kubuntu.  Just for the heck of it I installed (via live cd) Mepis / PClinuxOS and they both worked fine.

So I am confident its a (k)ubuntu issue.  Im a returning linus user so I can be much help - sorry.  

I even tried to copy the Mepis xorg.conf to the Kubuntu installation and still nogo.

Ill keep trying

---

### Post by Mr. Pig on 2007-05-18
Thanks, it's good to know it's an Ubuntu problem.

---

### Post by ac_dispatcher on 2007-05-20
Well 

Ive tried a fews things just to say I tried.

I first tried different kernels - custom and a Mepis kernel - nogo

Then I also tried to copy an entire /etc/X11 folder over to my Kubuntu and boot it up - long shot I know.

Still didnt work.  Anyone have any other ideas?  Ill try stuff that may even break the system.

---

### Post by ac_dispatcher on 2007-05-20
Think it may be wine?

Maybe try and install a different wine version?

**scratch that - it cant be a wine issue it it happens everywhere.

---

### Post by Mr. Pig on 2007-05-24
Yeah. I no longer use Ubuntu... for what I assume to be obvious reasons. So I can't help that much... that and the fact that I haven't booted to Linux for some time as I have been busy working on the game I am producing.

---

### Post by Linux_Noob30 on 2007-07-10
Hi

Well i'm a linux newbie and have just migrated from MS.

What i wanted to know was that I have downloaded the latest files.
And cant seem to get it to install at all.
I get the compile.sh sorted but once i try the install.sh it says that this file/directory is not found.

I am using linux mint 3.0

If you could shed some light it would be appreciated.

Thanks

---

### Post by Mr. Pig on 2007-07-16
> **Linux_Noob30 said:**
> Hi

Well i'm a linux newbie and have just migrated from MS.

What i wanted to know was that I have downloaded the latest files.
And cant seem to get it to install at all.
I get the compile.sh sorted but once i try the install.sh it says that this file/directory is not found.

I am using linux mint 3.0

If you could shed some light it would be appreciated.

Thanks

E-Mail me
mrazza {at} valdegames.com

---

### Post by ulmcnoob on 2007-09-23
running xmodmap in 7.04 feisty and repeat not working on q a s d (231 232 233 234)
xset r to no avail.
as well as r (230)

it seems ubuntu will not let you set repeat on keycodes >200

(edit) scratch that. v (247) does repeat. so
change range to >229 and <235

---

### Post by watermelonjam on 2008-01-04
I have good news.  You can patch Gutsy to enable key repeating for the Zboard MERC gamepad.  This is not a nicely packaged patch, but here it is anyways:

--- /usr/src/linux-source-2.6.22/drivers/hid/hid-input.c        2007-07-08 19:32:17.000000000 -0400
+++ hid-input.c 2008-01-03 18:36:12.000000000 -0500
@@ -665,6 +665,11 @@
 
                                default:    goto ignore;
                        }
+
+                       /* Special case - Ideazon Zboard MERC gaming keyboard */
+                       if (device->vendor == 0x1038 && device->product == 0x210) {
+                               set_bit(EV_REP, input->evbit);
+                       }
                        break;
 
                case HID_UP_HPVENDOR:   /* Reported on a Dutch layout HP5308 */




If you still have key detection problems with games (i.e., ETQW) after that, switch your xorg.conf file over to using evdev drivers for keyboard and mouse.  Here's the relevant part of mine:

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Default Screen" 0 0
    InputDevice    "Generic Keyboard" "Core Keyboard"
    InputDevice    "Generic Keyboard 2" "AlwaysCore"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
    Load           "v4l"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "evdev"
        Option          "Phys"  "usb-*-4/input0"
        Option          "evBits"      "+1"
        Option          "keyBits"      "~1-255 ~352-511"
        Option          "Pass"     "3"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard 2"
        Driver          "evdev"
        Option          "Phys"  "usb-*-4/input1"
        Option          "evBits"      "+1"
        Option          "keyBits"      "~1-255 ~352-511"
        Option          "Pass"     "3"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "evdev"
    Option         "Phys"       "usb-*-6/input0"
    Option         "CorePointer"
    Option         "evBits" "+1-2"
    Option         "keyBits" "~272-287"
    Option         "relBits" "~0-2 ~6 ~8"
    Option         "Pass" "3"
    Option         "SampleRate" "200"
    Option         "Resolution" "1600"
EndSection

The mouse section enabled the game to recognize the extra buttons on my MX518 as "button4 - button8".  With the default xorg mouse driver, all of them were button1-button3.

Good luck.

---

### Post by jimmyjiii on 2008-05-02
Hi 

I*have the same non-repeating problem. I actually have a MERC*and another keyboard with keys with the same Keycodes and they do not repeat either. 

Is there any low level way to change the keycodes ?*

I didn't understood what watermelonjam said. 

Any idea why the Zboard has two physical addresses ? : 

cat /proc/bus/input/devices
```

I: Bus=0003 Vendor=1038 Product=0210 Version=0111
N: Name="Ideazon Zboard Gaming Keyboard"
P: Phys=usb-0000:00:1d.0-2/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.0/usb3/3-2/3-2:1.0/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=120013
B: KEY=10000 7 ff9f207a c14057ff febeffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0003 Vendor=1038 Product=0210 Version=0111
N: Name="Ideazon Zboard Gaming Keyboard"
P: Phys=usb-0000:00:1d.0-2/input1
S: Sysfs=/devices/pci0000:00/0000:00:1d.0/usb3/3-2/3-2:1.1/input/input2
U: Uniq=
H: Handlers=kbd event2 
B: EV=13
B: KEY=2000000 3878 d8011001 e0000 0 0 0
B: MSC=10

```

---

### Post by ac_dispatcher on 2008-05-04
Im bumping this thread to give more data that I have found.

I have tried with many different Distros to get the extra gaming keys to work. In some distros the keys would not repeat and others some would work - some would not.

I thought it was a Xorg issue but now I don't think so.

I just reinstalled PClinuxOS and before I did an update I tried the merc keyboard via the xmod mapping. Every key worked wonderfully. All keys repeated and worked the way I had always wanted. Then I did an update to my system. The system updated the original 2.6.18 kernel to a newer 2.6.24 kernel. On boot some of the keys no longer worked. Thankfully the update didn't remove the old 2.6.18 kernel so I rebooted via that. All keys again worked great.

My conclusion is the kernel was the source of the problem and solution.

I have tried to roll a vanilla 2.6.25 kernel with the old 2.6.18 config (just changing the proc type) and it did not work. Oh well Ill stick with the old 2.6.18 kernel for as long as I can.

I tried to copy the above post code and make a .patch file for the 2.6.25 vanilla but the patch failed  - but I'm not to familiar with home grown patches.  I have always kept the xorg file as standard and not like the above with evdev.

---

### Post by WanderingOtaku on 2008-06-16
Well the activity on this has been slow, but I am posting again because I would really love to get this working in Ubuntu. It is probably one of the few things keeping me going back to Windows  on a regular basis. I enjoy playing games with the keypad.

I have followed the instructions on installing Mr. Pig's zboard config file, and the commands work. When I use zboard-config --CheckZboard, it tells me this:
Your Zboard is not compatible with the default configurations.
However, this program may still be of use.

Is there some other way to configure it?

As for the patch a few posts up, I am unsure how to use that. I am not too knowledgeable on how linux/ubuntu works, so I am slowly learning.

I tried to use it in wow. The red arrow keys don't work, nor do the number pads. Well, I take that back. 1 and 7, and then I think 6 and 11 move me forward and back, and turn side to side. I can go back in and check if someone wants to know for sure.

Any help is appreciated.

---

### Post by remicks916 on 2008-06-17
I too am having the same problem as Otaku in 8.04, whenever I hit the "W" key on the left hand side it launches firefox(?) and the "S" key outputs a "/"... if anyone can help that would be freakin awesome :D

---

### Post by Falkon MX-5 on 2008-06-18
> **remicks916 said:**
> I too am having the same problem as Otaku in 8.04, whenever I hit the "W" key on the left hand side it launches firefox(?) and the "S" key outputs a "/"... if anyone can help that would be freakin awesome :D

Hey, saw this on here while also searching for answers.  I run Debian and the Gnome desktop.  In the settings, gnome has set hotkeys already for web browser, calculator, e-mail, etc.  I had to reset them by going to System on the menu, then to Preferences, then to Keyboard Shortcuts.  There should be something relevant in KDE and possibly XFCE.  

I bound these shortcuts to the hotkeys on the top.

---

### Post by remicks916 on 2008-06-19
> **Falkon MX-5 said:**
> Hey, saw this on here while also searching for answers.  I run Debian and the Gnome desktop.  In the settings, gnome has set hotkeys already for web browser, calculator, e-mail, etc.  I had to reset them by going to System on the menu, then to Preferences, then to Keyboard Shortcuts.  There should be something relevant in KDE and possibly XFCE.  

I bound these shortcuts to the hotkeys on the top.

Thanks, this solved a couple small issues I was having, but still unable to get this to work properly in games thru Wine/Crossover :( I miss playing Guild Wars with my extra keys, it makes it so much easier :D

---

### Post by remicks916 on 2008-06-21
Quick Update: Now if I hold shift and hit Home or End on my keypad it sets the numlock on while the shift key is pressed down.... :(

---

### Post by viodream on 2008-07-16
For me not run the W and E keys from red keyboard (gaming pad).
Any idea? I probe xmodmap and the mr.pigs program.
--------(SOLVED WITH XEV)


but i have a problem with repeat non-keys :(
I probe AntiX and in this distro all keys repeat perfectly, but in ubuntu linux redkeys no repeat.

---

