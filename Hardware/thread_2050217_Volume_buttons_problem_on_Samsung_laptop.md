---
title: "Volume buttons problem on Samsung laptop"
date: 2012-08-30
forum: Hardware
---

### Post by staim on 2012-08-30
I have a new Samsung NP350V5C-S0ARU laptop with recent Ubuntu 12.04. It works almost perfecly except for one small, but nasty problem - volume buttons (Fn + F6-F8) do not work as expected:

When I press vol+ vol- or mute key this causes volume information popup window appear\disappear multiple times and volume is changing unpredicatably. In addition after this all the Unity panel (including dash) hangs out and do not respond mouse clicks (helps only X reloading). From other side brightness and tochpad toggle keys works perfectly.

- Already googled the topic, no luck
- samsung-tools are installed from ppa
- Buttons works inwindows ok (using official samsung drivers)
- xev doesn't show anything
- There is no bios updates for my laptop

Can anybody help on the topic?

---

### Post by backsideslappy on 2012-09-25
Certainly can't help here, but have the exact same model of computer (purchased last week) and am having the same problem with my volume Fn buttons.  Have tried almost all the other potential fixes for other builds that hang on Fn button presses, but so far nothing works.  Would be most interested to hear of any progress!

---

### Post by BigSilly on 2012-09-25
Had my own topic for a similar model [here]("http://ubuntuforums.org/showthread.php?t=2061273"). But I've since discovered a nice workaround [courtesy of a friendly reviewer on Amazon]("http://www.amazon.co.uk/review/R1AWZX7HELM30H/ref=cm_cd_notf_message?ie=UTF8&cdForum=FxRF7JFDLQDY57&cdPage=1&cdThread=Tx111KKZ389U6EV#Mx301UT6TFF247I") who is running Ubuntu on these models. See below his/her comment:

> 1. Go to System Setting>Keyboard>Shortcuts> and select the <Sound and Media> Tab.
2. On the right pane you will see Volume Mute, Volume Down and Volume Up
3. Go on each of them with the mouse pointer and left click on each of them one by one.
4. In each case <New Accelerator> will come up... Press the backspace key to disable the shortcut.
5. Repeat this for all three keys
6. Repeat the same procedure all over again, but this time as <New Accelerator> appears press F6, F7 and F8 for each function
(I assume F6 for Mute, F7 for Volume Down and F8 for Volume Up).
IMPORTANT: DO NOT press the Fn key.

Your new reassigned keys will work. If there is any problem repeat the whole sequence but reboot after step 5

This solved the issue for us. It's not really a fix as the poster acknowledges, but it does do the trick until the thing gets sorted properly. I personally suspect a kernel issue, but I've tried other distros and they're all the same.

Hope this helps. :)

---

### Post by backsideslappy on 2012-09-25
Thanks BigSilly - a workaround or not, that will suffice for me for now until somebody sorts out the issue - I have noticed others have had similar issues with the brightness buttons on dell machines etc, so suspect you are right about it being a kernel issue.

This will be fine for now, so long as I can stop myself from instinctively pressing the Fn button when I change the volume.

---

### Post by silent_shade on 2013-03-06
I've got a similar with Fn keys on the same laptop (Debian testing). Any time I press fn-key, touchpad goes down. So many thanks for the elegant idea! Would not call it a solution to the problem, but saved me anyway = )

---

