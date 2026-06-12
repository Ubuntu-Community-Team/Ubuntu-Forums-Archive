---
title: "Buggy Fingerprint Authentication after Attempt at Replacing Lightdm"
date: 2015-01-20
forum: Hardware
---

### Post by Jocbe on 2015-01-20
Hey,

Recently I've switched to Ubuntu 14.04 on my ThinkPad X230T. I set up fingerprint authentication and was happily using it both on the login screen and for authentication in the terminal and other prompts. 

Then, I tried replacing lightdm with gdm due to an unrelated issue. This didn't work properly, however (my installation of gdm seemed broken and wouldn't let me log in), and I switched back to lightdm. This attempted switch broke fingerprint authentication on my login screen. Whenever I try to log in after powering on the laptop from being suspended or off, the laptop initially doesn't react to any kinds of fingerprint authentication attempts. However, when I let the initial fingerprint authentication time out and press [ENTER] in the then appearing password prompt (which is an incorrect password, of course), I get another try at fingerprint authentication - this second time it always works flawlessly. 

I think sometimes it also displays a password prompt when I swipe my finger but that password prompt doesn't actually log me in when I type in my password - at least not until after the first fingerprint authentication timeout.

I've tried removing and reinstalling libpam-fprintd, disabling and re-enabling fingerprint authentication - all without success.

Given that fingerprint authentication worked flawlessly before, it seems to me that all I need to do is reset lightdm and/or the fingerprint authentication packets back to the state they were in when installed initially. I am not sure how to go about this, though - or does anyone have another, better idea?

Thank you!
Jocbe

---

