---
title: "resolution too high, can I still use compiz or what are the alternatives?"
date: 2008-07-26
forum: General Help
---

### Post by Cruz on 2008-07-26
Hi there,

I have an ATI X800 and would like to configure a nice looking dual screen environment with extended desktop on my two 1280x1024 screens. I managed to get it working with the open source ati driver and xrandr, but the "nice looking" part still needs some work. I can't start compiz, because the combined resolution of the two screens is too large for the texture buffer of my graphics card. Here is the output of compiz-check (thanks for that great tool!)

```
Your resolution is 2560x1024 but the maximum 3D texture size that your
 graphics card is capable of is 2048x2048. Thus Compiz will not be able to run
 on this setup. You have to decrease the resolution first (in case you are
 using a dual-head setup, try disabling one monitor and run the script again). 
```

My questions about this:

Can I still manage to run compiz somehow? In the problem description above it says I could try to decrease the resolution "first" and then start compiz. Will that work if I go back to the large resolution after compiz is started?

Or is xrandr the wrong strategy if I really want to stick to the full resolution of 1280x1024 on both screens? Should I maybe use MergedFB instead? Or can I make the desktop look just as pretty without compiz too?


Thanks
Cruz

---

### Post by oedipuss on 2008-07-26
While nowhere as pretty as compiz, there's always the metacity (newly) built-in compositing manager.
 It can't do much more than shadows and transparency at the moment, but most importantly it can allow other apps which need compositing to run, such as avant window navigator. 
To enable it you just open gconf-editor (either through Applications/System/Configuration Editor, or just by typing 'gconf-editor' in a terminal), browse to "apps > metacity > general" and there activate the option "compositing_manager".

---

