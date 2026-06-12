---
title: "Keybord + function keys issues/IBM T41"
date: 2009-06-08
forum: Hardware
---

### Post by Gyorgy on 2009-06-08
Hi ,
i am asking support for below issues:


Machine : IBM T41, 89 keys, GB layout +3 volume setting buttons + On/Off button
OS  : Ubuntu Jaunty Jackalope (exclusive)

I am looking for a 'cure' on the next 4 items:

1/ Keyboard layout
   I was unable to find a keybord layout with 100% fit.
   Instead I am using 105 keys generic layout. It's not the best ...
   Is there any way to customize it ? To solve this ?



2/ Num lock

2.1 The function used from the Laptop's keybord BUT no LED feed-back...
    In case of using external keybord, the LED works...

2.2 In case of using external Keybord, and switching on the Num Lock, if the keybord is detached, 
    the 'Num lock' seems to be locked.. This means, the LED remains on, regardless the switching off the function.
    Moreover, whenever the laptop is suspended, than returned, it returns with 'Num Lock' on again.


3/ Volume / Display brightness  setting 
   The setting of these functions works properely from the own keyboard, BUT no graphic feed-back, no graphic reflection of it.
   In case the above functions are set from an external Keybord, the graphic feed-back works properely...
   Is this a setup issue ?

4/ Hibernate / Suspend
  The hibernation is slow, with a '...failed to thaw...' like error message in between. 
  The wake-up takes than long, almost as long as a boot...
  The Suspend works OK. However in this state, the laptop consumes the energy stored in the batteries ...
  Any thoughts ? Tips? 


I hope you already solved the above issues, or you might know the sollution...
Thank you in advance for your answers.

kind regards
Gyorgy Zold

---

### Post by Alvin Chiu on 2009-06-15
Hi,

I have a T40 with all of the problems you mentioned.  I can help you fix the num lock and the volume/display brightness problem; but these aren't 100% perfect.  They're more or less temporary hacks until I see these problems fixed in Karmic Koala (hopefully).

1. Num Lock
The problem with num lock is that (if you have the same keyboard layout as mine) to turn it on you have to do Shift+ScrLk.  However that is mapped to the OS functionality where you can control the mouse cursor by the keypad.  To fix this, I created a command which ran every time I logged into my account:

[LIST=1]
[*]Go to System>Preferences>Startup Applications.
[*]Click the Add button.  A dialog window will pop up.
[*]For the "Command" text box, type in [FONT=Courier New]xmodmap -e 'keycode 77 = Num_Lock'[FONT=Verdana].[/FONT][/FONT]
[*][FONT=Courier New][FONT=Verdana]For the "Name" text box I put in something like "Num Lock Fix" but it's up to you.[/FONT][/FONT]
[*][FONT=Courier New][FONT=Verdana]Click Save and then the item should appear on the list of startup applications.  Make sure that the box next to it is checked.[/FONT][/FONT]
[/LIST]
When you restart, it should fix the num lock problem and pressing Shift+ScrLk should activate Num Lock.  It's not a pretty fix; for instance it doesn't run until you log into your account, so if for some reason you need to use the keypad at the log in screen, you're out of luck.  As well, I haven't used my laptop with an external keyboard, so I don't know if this fix might mess up the num lock functionality of your external keyboard.

2. Volume/Brightness OSD
The Volume/Brightness bug seems to be happening to everyone with older ThinkPads running Jaunty.  You can use the volume and brightness keys, but there's no indicatior showing up on screen.  What I found for a solution (at least what I found in the forums) is that you should uninstall 'hotkey-setup' and install the version of 'hotkey-setup' that came with Intrepid.  Lucky for you I still have the link: [http://packages.ubuntu.com/intrepid/hotkey-setup](http://packages.ubuntu.com/intrepid/hotkey-setup).
What I found was that the volume indicator works "almost" perfectly.  The brightness indicator is sort of flaky at the moment.  If I hit brightness up or down the OSD always tells me that I'm at maximum brightness.  But at least I have indicators now instead of nothing.

3. Thaw problem
Yes, I have that problem, and unfortunately that exceeds the scope of my knowledge because I am a Linux n00b.  I think that error message means that some component of your laptop is not playing nice with Ubuntu's hibernation function.  I might (or you could) post something in the forums and see what answers you get.
Also, I think the suspend function is supposed to drain battery power, because it does for mine when it had Windows, and after I put Ubuntu on it.

Let me know how those fixes turned out on your T41.

---

