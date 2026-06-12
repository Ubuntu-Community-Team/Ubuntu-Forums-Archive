---
title: "Thinkpad T400 ATI card problem"
date: 2008-10-30
forum: Hardware
---

### Post by cmaabb on 2008-10-30
Windoes xp & Ubuntu. Each time, after I use Ubuntu and get into windows, windows cannot recognize ATI card

---

### Post by bettlebrox on 2008-10-30
The T400 has 2 graphics cards, the ATI one, and an integrated Intel one for extended battery life. Windows can switch between the 2 to save batteries, at the moment Linux doesn't. If you haven't already, go into the BIOS and configure it so that only discrete graphics is enabled disable OS auto detect of the video and see if that helps.

I don't have a T400, but I've been researching getting one, what's your opinion of it?

---

### Post by cmaabb on 2008-10-30
A good choice for both business and game player,but you need to add memory if you'd like to use Vista

---

### Post by Andi_C on 2008-11-02
Hi!
I had the same problem with my T400 and winXP-Ubuntu switch..
Bettlebrox was right!! I had just to disable the auto OS detection in the BIOS.. now it is working amazing...
Thank you very much Battlebrox:)!! Yesterday I spent the whole day with this problem... 

I bought my T400 one month ago... it is a excellent laptop! i'm really happy! (memory should be added? I have 250GB that's enough, i think..)

greez Andi

---

### Post by bettlebrox on 2008-11-02
Cool that's good to know, I might get one in the next few months if I can get a good price on one.

---

### Post by trism on 2008-11-02
[QUOTE=bettlebrox;6068895]The T400 has 2 graphics cards, the ATI one, and an integrated Intel one for extended battery life. Windows can switch between the 2 to save batteries, at the moment Linux doesn't. [\QUOTE]

Note that the switchable graphics only work in Vista, not XP. It has to do with the new way that Vista handles video drivers, so switchable graphics will never work in XP.

I have a Thinkpad W500 which also has the switchable graphics in Vista. If I'm using Ubuntu, I have to go into BIOS and select either integrated or discrete graphics, and when I'm using Vista I must use the switchable option, it doesn't recognize the integrated or discreet alone. (I'm pretty sure that's because I only have the switchable graphics driver installed in Vista.)

The switchable graphics are really nice. When I use low power settings with the integrated card and a 9-cell + ultrabay battery I can get over 8 hours of battery life with WiFi on. But when I'm plugged in I can switch to the discrete card and have solid graphics power.

Unfortunately I can only switch on the fly in Vista (without even logging out like in the new Apple machines). With Linux I have to do a reboot and go into BIOS. I hope that one day it's possible in Linux, even if a log-out is required, though I doubt it would be an easy change. (This new Windows video driver model was probably the single biggest thing that was causing crashes in Vista when it first came out.)

Wow, that turned out to be a lot more long winded than I had planned. Basically, switchable graphics = sweet, but they don't work in Linux (yet).

---

