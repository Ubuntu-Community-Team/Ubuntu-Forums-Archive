---
title: "[SOLVED] Acer Laptop - delete key doesn't work in Hardy"
date: 2008-04-25
forum: Hardware
---

### Post by mh114 on 2008-04-25
Hi, I upgraded from Gutsy to Hardy last night in my Acer Extensa 5220 laptop. So far things seems to be working correctly, but somehow the delete key on the keyboard stopped working! :confused:

Now when I press delete, it toggles my WLAN led. I press it, the led switches on, and when I press again it turns off. It doesn't seem to shutdown the WLAN though (in this model Ubuntu has the led off when the WLAN is on, and vice versa - but that isn't a problem for me)..

Any ideas how I can get the key working again? I use it quite a lot, in normal typing as well as, you guessed it, deleting stuff.. :) Any help is appreciated!

---

### Post by aaronhall555 on 2008-04-25
Try going to the menu at the top right: System>Preferences>Keyboard and make sure you have the correct keyboard layout and model, then try testing it in the test box that is provided.

---

### Post by mh114 on 2008-04-25
> **aaronhall555 said:**
> Try going to the menu at the top right: System>Preferences>Keyboard and make sure you have the correct keyboard layout and model, then try testing it in the test box that is provided.
I previously had a generic keymap set, and now set it to Acer Laptop, but it made no difference.. :( Thanks for the suggestion though.

---

### Post by mh114 on 2008-04-25
Any clues as to where start looking? I'd rather not go back to Gutsy.. :)

---

### Post by Whise on 2008-04-25
i can confirm this in acer extensa 5620z , only in hardy

---

### Post by mh114 on 2008-04-26
> **Whise said:**
> i can confirm this in acer extensa 5620z , only in hardy
Interesting. Hopefully this can be fixed somehow.. :-k

Btw, did you upgrade or do a clean install?

---

### Post by zombiepig on 2008-04-26
It's this bug: [https://bugs.launchpad.net/ubuntu/+bug/181057](https://bugs.launchpad.net/ubuntu/+bug/181057)
The fix is to edit the /usr/share/hal/fdi/information/10freedesktop/30-keymap-acer.fdi file, and remove line 141, which reads

```
<append key="input.keymap.data" type="strlist">e053:bluetooth</append> <!-- Bluetooth (toggle) on-to-off -->
```

Take that line right out, save and restart, and the problem is fixed.
It's fixed upstream now, so we shouldn't see it reoccur, but it totally sucks that this wasn't fixed before hardy was released :(

---

### Post by mh114 on 2008-04-26
> **zombiepig said:**
> It's this bug: [https://bugs.launchpad.net/ubuntu/+bug/181057](https://bugs.launchpad.net/ubuntu/+bug/181057)
The fix is to edit the /usr/share/hal/fdi/information/10freedesktop/30-keymap-acer.fdi file, and remove line 141, which reads

```
<append key="input.keymap.data" type="strlist">e053:bluetooth</append> <!-- Bluetooth (toggle) on-to-off -->
```

Take that line right out, save and restart, and the problem is fixed.
It's fixed upstream now, so we shouldn't see it reoccur, but it totally sucks that this wasn't fixed before hardy was released :(
That does indeed work. :) Thank you very much! Shame it slipped into Hardy..

---

### Post by gerymate on 2008-05-17
No, it's not a shame. 
I tried Fedora 9 some days ago and had the same problem there.

zombiepig's solution works here, too.

How can the thread be marked as [SOLVED]? Maybe the creator can set it?

---

### Post by mh114 on 2008-05-18
> **gerymate said:**
> How can the thread be marked as [SOLVED]? Maybe the creator can set it?

Sure, I'll set it.

---

### Post by rhaposo on 2008-05-24
I can also confirm this on an Acer 5210. Upgrade from Gutsy to Hardy and the Del key does not work (appears not to issue a key code so it looks like its mis mapped). And yes the key does work up to the point Xorg fires up. 

Ok, there is a bug filed for this at 
[https://bugs.launchpad.net/ubuntu/+bug/181057](https://bugs.launchpad.net/ubuntu/+bug/181057)
and this reply looks like a fix!


> zombiepig wrote on 2008-04-18: (permalink)

>Ok, i've tracked down the line which causes the problem, by >manually applying each change from the working hal keymap file.
>The problem is the line

>"<append key="input.keymap.data" >type="strlist">e053:bluetooth</append> <!-- Bluetooth (toggle) >on-to-off -->"
>on line 141 of /usr/share/hal/fdi/information/10freedesktop/30-keymap-acer.fdi

>Removing this line (and restarting) fixes the problem properly. >Removing it doesn't affect the bluetooth functionality either, >since it's the next line
>"<append key="input.keymap.data" >type="strlist">e054:bluetooth</append> <!-- Bluetooth (toggle) >off-to-on -->"
>which allows the bluetooth module to be switched toggled.

>So it's perfectly safe to remove line 141, retain full >functionality, and fix the delete key issue permanently! I'm >going to try and find a way of getting this fix upstream, and >hopefully a ubuntu dev can make the required change before >hardy release....

>(and thanks go to daniel eckl for finding the fix for this one!)


HTH

---

### Post by rhaposo on 2008-05-24
:confused:

---

### Post by DocViper on 2008-05-28
I have deleted the line 141 like posted - 
And my DEL Key still doesn't function !:confused:
What could be wrong ?
keyboad > laptop > acer is selected
Any ideas ?
System Ubuntu Hardy - Default installation - Acer 5220

[OKAY SOLVED]
Used the attached file to overwrite my existing... now everthing works fine with the "DEL" :-)

---

### Post by a-guest-user on 2008-08-04
I've got the same problem on an Acer Extensa 5210 -- I deleted afore-mentioned line, but that didn't help here.

@ DocViper: which attached file did you use? any chance to send me that file?

---

### Post by DocViper on 2008-08-05
the file is in the bug report threat:

[https://bugs.launchpad.net/ubuntu/+bug/181057](https://bugs.launchpad.net/ubuntu/+bug/181057)

scroll down till the comment:
[https://bugs.launchpad.net/ubuntu/+bug/181057/comments/31](https://bugs.launchpad.net/ubuntu/+bug/181057/comments/31)

and there is the file attached :)

and the comment below the mentioned relates to the 5210 acer

joe

---

### Post by a-guest-user on 2008-08-05
I tried both, but it doesn't help. What does help is /etc/init.d/hotkey-service restart, at least until reboot.

Any other ideas what I could do?

thanks

---

