---
title: "Old xorg.conf scroll fix won't work in 8.10."
date: 2008-10-30
forum: General Help
---

### Post by animaniac on 2008-10-30
SOLVED- read the later posts.


The new xorg.conf file is different and i can't get this old fix to work.

This is what the current file looks like:

> Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

As you can see it lacks InputDevice of the previous versions, and adding these lines doesnt work either. any ideas on how to get it to work, the old fix is below.

>  Re: Middle mouse button to be used as scroll.
Enable TrackPoint middle-button scrolling

To use the blue middle TrackPoint button as a scroll wheel (using the red TrackPoint itself to scroll up and down), do the following. In a terminal, enter these commands:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-original
sudo gedit /etc/X11/xorg.conf

In the editor, find the section headed Section “InputDevice” / Identifier “Configured Mouse” and the following lines above the “EndSection” line:

Option "EmulateWheel" "true"
Option "EmulateWheelButton" "2"

Save the file. Logout, restart X with Ctrl-Alt-Backspace, and log in again.

Source for this item: Many ThinkPad-related sites, confirmed by experiment.

Copied from this excellent how-to. Works great on my T42 and contains lots of other good stuff and links to even more.
__________________
'Those who are willing to sacrifice essential liberties for temporary security deserve neither liberty nor security.' - Benjamin Franklin

Registered Linux User#407002 / Registered Ubuntu User#1806 
[http://ubuntuforums.org/showpost.php?p=780792&postcount=5]("http://ubuntuforums.org/showpost.php?p=780792&postcount=5")

---

### Post by animaniac on 2008-10-31
bump

---

### Post by Haiatola on 2008-10-31
I'm having the same problem. Guess something got changed with the new xorg version...

---

### Post by Geekboy on 2008-10-31
I just installed on a Thinkpad T61P and am having the same issues.  Anyone know where to make this change?

---

### Post by animaniac on 2008-10-31
yeah, i use the trackpoint on my t42 as my primary mouse too. as for a fix, ive been lookin, but i aint got nothin.

---

### Post by daphreak on 2008-11-01
Instead of modifying your xorg.conf, create a new file called /etc/hal/fdi/policy/mouse-wheel.fdi with the following contents:

    <match key=”info.product” string=”TPPS/2 IBM TrackPoint”>
    <merge key=”input.x11_options.EmulateWheel” type=”string”>true</merge>
    <merge key=”input.x11_options.EmulateWheelButton” type=”string”>2</merge>
    <merge key=”input.x11_options.XAxisMapping” type=”string”>6 7</merge>
    <merge key=”input.x11_options.YAxisMapping” type=”string”>4 5</merge>
    <merge key=”input.x11_options.ZAxsisMapping” type=”string”>4 5</merge>
    <merge key=”input.x11_options.Emulate3Buttons” type=”string”>true</merge>
    </match>

Many people have had good luck with this on thinkpads. I, however, do not have it working yet. Hope this helps some of you.

---

### Post by animaniac on 2008-11-01
sweet,
that didn't work, but i tried the few different variations of that floating arround on the intarwebs, this one worked for me:

<match key="info.product" string="TPPS/2 IBM TrackPoint">
 <merge key="input.x11_options.EmulateWheel" type="string">true</merge>
 <merge key="input.x11_options.EmulateWheelButton" type="string">2</merge>
 <merge key="input.x11_options.ZAxsisMapping" type="string">4 5</merge>
 <merge key="input.x11_options.Emulate3Buttons" type="string">true</merge>
</match>


Otherwise, heres another solution that might work:

> Chris Jones Says:
September 23, 2008 at 12:52 pm

Using the latest stuff in Intrepid, I can get this working via xinput:

xinput set-int-prop &#8220;TPPS/2 IBM TrackPoint&#8221; &#8220;Wheel Emulation&#8221; 8 1
xinput set-int-prop &#8220;TPPS/2 IBM TrackPoint&#8221; &#8220;Wheel Emulation Button&#8221; 8 2

that enables wheel emulation and ties it to button 2 (ie middle mouse button).

see &#8220;man xinput&#8221; and &#8220;xinput list&#8221; to find the right device name, and then &#8220;xinput list-props DEVICENAME&#8221; to find out what it can do. As an example, these are the commands I ran to figure out the various things I needed to know:

xinput list => &#8220;TPPS/2 IBM TrackPoint&#8221;
xinput list-props &#8220;TPPS/2 IBM TrackPoint&#8221; => &#8220;Wheel Emulation&#8221;/&#8221;Wheel Emulation Button&#8221;


Just look here:
[http://mvogt.wordpress.com/2008/08/15/xorg-evdev-and-emulatewheel/](http://mvogt.wordpress.com/2008/08/15/xorg-evdev-and-emulatewheel/)

---

### Post by crustache on 2008-11-01
Does this mean only people who know how to write xml scripts can get a 5 buttons mouse to work in Intrepid? That's not user friendly at all.

---

### Post by vloris on 2008-11-02
What's more userfriendly about writing xorg.conf then about writing xml configfiles?

Otherwise, thanks, this is exactly the solution I was looking for! Is there any general documentation around what can be done with those fdi configfiles?

---

### Post by animaniac on 2008-11-02
> **vloris said:**
> Is there any general documentation around what can be done with those fdi configfiles?

There seems to be, a quick search revealed [_[COLOR="Blue"]this here documentation[/COLOR]_]("http://www.google.com/custom?hl=en&client=google-csbe&cof=FORID:11%3BAH:left%3BCX:Ubuntu%2520Website%3BL:http://www.google.com/coop/intl/en/images/custom_search_sm.gif%3BLH:65%3BLP:1%3BVLC:%23551a8b%3BGFNT:%23666666%3BDIV:%23cccccc%3BNWS:1%3B&ad=w9&adkw=AELymgXbbHaH1UPn3PCpkuKad8rTCV9xadZHsnmS1F0Miyj_laLMWOvvJhcRPWnAlMuEq_FiNv-_bAMVsZVP3lu0Rg6IfHQPLHZTVapyCGKssTVheaeuQJ0&rurl=http://search.ubuntu.com/results2.html%3Fcx%3D009650792990864903260%253A-lsdjshi1tu%26cof%3DFORID%253A11%26ie%3DUTF-8%26q%3Dhal%2Bfdi%26sa%3DSearch%26google_rsg%3D__B_lURC2yVGOmn_WD1fjnf5_60dY%3D&q=hal+fdi+more:documentation&cx=009650792990864903260:-lsdjshi1tu&sa=N&oi=coopctx&resnum=0&ct=col1&cd=1")

Although i wouldn't say its easy enough to find without knowing exactly what it is you need to do to get something working.

---

### Post by IT-Joker on 2008-11-02
Anyone has idea whether/how it's possible to configure the side buttons of a 5-button mouse this way?
I have tried something, but no success so far :(

---

### Post by sethd32 on 2008-11-02
For my Thinkpad T42, I created the file /etc/hal/fdi/policy/mouse-wheel.fdi

with:

<match key="info.product" string="TPPS/2 IBM TrackPoint">
<merge key="input.x11_options.EmulateWheel" type="string">true</merge>
<merge key="input.x11_options.EmulateWheelButton" type="string">2</merge>
<merge key="input.x11_options.ZAxsisMapping" type="string">4 5</merge>
<merge key="input.x11_options.Emulate3Buttons" type="string">true</merge>
</match>

It worked perfectly after a reboot.  Thanks to all who helped!

---

### Post by ltmon on 2008-11-02
I got this working with the FDI file on a T61P, however I seem to lose my settings after a suspend-resume cycle.

Scrolling with the trackpoint stops working, and using xinput to try and get it going again doesn't seem to help.

Any ideas why this dies after a suspend-resume and how to fix?

Thanks,

L.

---

### Post by mlilien on 2008-11-03
When I try  xinput list-props “TPPS/2 IBM TrackPoint”, I get an error about not being able to find the device.  However, when I use 3, the id I see when I use xinput list, I get a list of the properties.

Similarly, when I call "xinput set-int-prop “TPPS/2 IBM TrackPoint” “Wheel Emulation” 8 1", I get an error about not being able to find the device.  So, I assume that I need to call something to the effect of "xinput set-int-prop 3 “Wheel Emulation” 8 1", but that gives me an Invalid format error.  So, I'm guessing I need some kind of index instead of "Wheel Emulation", but I don't know if that's the case.

Any ideas?

Thanks.

---

### Post by mlilien on 2008-11-03
I must've typed something wrong, because I tried it again, and now it works.  So, you can ignore my previous post.

---

### Post by Haiatola on 2008-11-03
Unfortunately for me this didn't work. I'm using a pleomax 9 button mouse (I don't even want the 4 extra multimedia buttons to work) and nothing I've tried works as far as getting the mousewheel working again. Any tips? :(

EDIT: On a whim I plugged the mouse on another usb port and it works now... What the hell?
Unfortunately now I don't know if it had anything to do with the mouse-wheel.fdi deal, I'll report back later.

---

### Post by rlonnborg on 2008-11-11
I too have tried the mouse file and still have no scroll feature.

---

### Post by jsully1 on 2008-11-16
> **ltmon said:**
> I got this working with the FDI file on a T61P, however I seem to lose my settings after a suspend-resume cycle.

Scrolling with the trackpoint stops working, and using xinput to try and get it going again doesn't seem to help.

Any ideas why this dies after a suspend-resume and how to fix?

Thanks,

L.
Same problem - doesn't seem to work after suspend.  Anyone have any success?

---

### Post by kwesadilo on 2008-11-20
> **ltmon said:**
> I got this working with the FDI file on a T61P, however I seem to lose my settings after a suspend-resume cycle.

I have the same problem (same machine even). I notice that after I resume, the middle button still works for clicking, just not for scrolling. Also, after I suspend-resume and lose scrolling, it will sometimes come back after suspending and resuming again. I haven't done enough testing to say whether there is a pattern to how many suspend-resumes it takes to make middle-button scrolling come back, but I think it is usually three or fewer. After it comes back, it will go away again the next time I suspend.

Edit: I also tried the xinput commands. My "WheelEmulation" and "WheelEmulation Button" options were already set to the values that they needed to be set to get middle-button scrolling. I checked while scrolling was not working. Using xinput set-int-prop didn't change anything.

---

### Post by jsully1 on 2008-11-24
> **kwesadilo said:**
> I have the same problem (same machine even). I notice that after I resume, the middle button still works for clicking, just not for scrolling. Also, after I suspend-resume and lose scrolling, it will sometimes come back after suspending and resuming again. I haven't done enough testing to say whether there is a pattern to how many suspend-resumes it takes to make middle-button scrolling come back, but I think it is usually three or fewer. After it comes back, it will go away again the next time I suspend.

Edit: I also tried the xinput commands. My "WheelEmulation" and "WheelEmulation Button" options were already set to the values that they needed to be set to get middle-button scrolling. I checked while scrolling was not working. Using xinput set-int-prop didn't change anything.

On further inspection, it actually seems like scrolling is not broken, just really really **really** slow.  If you try to scroll in a window and really slam the trackpoint up, you'll get a line or two out of it.  Can anyone else reproduce?

---

### Post by kwesadilo on 2008-11-27
> **jsully1 said:**
> On further inspection, it actually seems like scrolling is not broken, just really really **really** slow.  If you try to scroll in a window and really slam the trackpoint up, you'll get a line or two out of it.  Can anyone else reproduce?

That doesn't seem to be the case for me. I pushed until the Trackpoint nub started striking the B, G, or H keys. At that point, pressing those keys did something that kept it from scrolling (auto-find in Firefox and return to the active prompt in Terminal). I turned auto-find off, and I pushed until the nub started to come off, but it still didn't scroll. Maybe I'll try it with different nubs when I get back to school on Monday.

I should point out that when middle-button scroll isn't working, and I'm pushing the middle button, the Trackpoint won't move the mouse, just as it does when scrolling actually works. The touchpad, however, will move the mouse while the middle button is pressed. This would seem to lend credence to the idea that the computer is at least trying to scroll. It looks like the computer will accept input from both the Trackpoint and the touchpad at the same time in general. This includes scrolling with the side of the touchpad while holding the middle mouse button. I don't know whether that information is useful or not.

---

### Post by ltmon on 2008-12-07
This seems fixed for me upon upgrading to KDE 4.1.3

---

### Post by phxdemon on 2008-12-16
Hey guys, linux noob here ):P   In regards to this post.
Re: Middle mouse button to be used as scroll.
Enable TrackPoint middle-button scrolling

To use the blue middle TrackPoint button as a scroll wheel (using the red TrackPoint itself to scroll up and down), do the following. In a terminal, enter these commands:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-original
sudo gedit /etc/X11/xorg.conf

In the editor, find the section headed Section &#8220;InputDevice&#8221; / Identifier &#8220;Configured Mouse&#8221; and the following lines above the &#8220;EndSection&#8221; line:

Option "EmulateWheel" "true"
Option "EmulateWheelButton" "2"

Save the file. Logout, restart X with Ctrl-Alt-Backspace, and log in again.

Source for this item: Many ThinkPad-related sites, confirmed by experiment.

Copied from this excellent how-to. Works great on my T42 and contains lots of other good stuff and links to even more.
__________________
'Those who are willing to sacrifice essential liberties for temporary security deserve neither liberty nor security.' - Benjamin Franklin

Registered Linux User#407002 / Registered Ubuntu User#1806 




after I enter this command into terminal

sudo gedit /etc/X11/xorg.conf


I don't see anything that says 

&#8220;InputDevice&#8221; / Identifier &#8220;Configured Mouse&#8221;

Any ideas?   The help would be greatly appreciated because I use the middle scroll button on my thinkpad r50 religiously and not having it work is really bothering me.


I checked lenovo's website to see if there is any sort of additional driver for the mouse and found nothing.

---

### Post by amdalex on 2008-12-16
They just said ^that^ fix no longer works in 8.10.

---

### Post by kwesadilo on 2008-12-17
> **phxdemon said:**
> In the editor, find the section headed Section &#8220;InputDevice&#8221; / Identifier &#8220;Configured Mouse&#8221; and the following lines above the &#8220;EndSection&#8221; line:

Option "EmulateWheel" "true"
Option "EmulateWheelButton" "2"

Save the file. Logout, restart X with Ctrl-Alt-Backspace, and log in again.


These lines were already in my file, but they were commented out, because HAL is used for input devices now. I tried uncommenting them, and it appears (with minimal testing) to have fixed my problem. Hopefully, I'll be able to find a solution that uses HAL like it's supposed to, but this will certainly work in the meantime, assuming it doesn't conflict with HAL in some way that I haven't observed yet.

Update: Nevermind. It stopped working again.

---

### Post by tomerzz on 2008-12-27
anything new on this? nothing seem to work after suspend/resume

---

### Post by ltmon on 2008-12-28
I'm now using KDE 4.2, and *most* of the time it's fine. Every once in a while after resuming it is back to it's old behaviour.

Not sure what other people are finding.

---

### Post by kwesadilo on 2009-01-06
This reminds me of when my wireless networking wouldn't work after I put the computer to sleep and woke it up again. That problem occurred because the service that runs my wireless card wasn't getting restarted upon resume from standby. I fixed this by adding the service to the list of services to be restarted.

Perhaps a similar error is causing this trackpoint problem. I don't know where to look for a log of the services being started and stopped at various times. I was messing around with grep and /var/log/syslog before and after going to sleep and waking, but nothing helpful turned up. If someone knows more about this kind of thing than me, I would appreciate their help.

---

### Post by 3rods on 2009-02-09
X61 non-tablet, same scroll issue after sleep/resume, restarting X <CTRL+ALT+BKSP> fixes issue. 

I know this isn't a fix, but maybe it helps narrow down where to look.

---

### Post by tomerzz on 2009-02-10
T42 same issue. I enter "standby" and resume once again to get the scroll back to work.

---

### Post by jackling on 2009-04-19
> **sethd32 said:**
> For my Thinkpad T42, I created the file /etc/hal/fdi/policy/mouse-wheel.fdi

with:

<match key="info.product" string="TPPS/2 IBM TrackPoint">
<merge key="input.x11_options.EmulateWheel" type="string">true</merge>
<merge key="input.x11_options.EmulateWheelButton" type="string">2</merge>
<merge key="input.x11_options.ZAxsisMapping" type="string">4 5</merge>
<merge key="input.x11_options.Emulate3Buttons" type="string">true</merge>
</match>

It worked perfectly after a reboot.  Thanks to all who helped!

This worked for my X60! Thanks.

---

