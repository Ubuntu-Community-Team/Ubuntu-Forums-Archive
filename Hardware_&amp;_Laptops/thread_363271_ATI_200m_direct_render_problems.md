---
title: "ATI 200m direct render problems"
date: 2007-02-16
forum: Hardware &amp; Laptops
---

### Post by sjb05004 on 2007-02-16
Just have a little problem with my ATI 200m on Edgy.  I had everything working on my first install with XGL, the video card, and Beryl.  Now everything seems to be the same as it was, however there is no direct rendering which won't allow Beryl to work properly.  I don't get a splash screen for beryl anymore.   I have tried to follow all the guides I could find including the original one I used with failed attempts.  If anyone has had this problem and solved it please guide me in the right direction as to what I should try now.  Thanks.

---

### Post by bjornolai on 2007-02-16
I'm in a simmilar boat, if thats any consilation.  Your using the fglrx driver i guess. If I'm not mistaken there was just a kernel upgrade in egdy (I might be wrong cause im running a lot of os). I think edgy stopped using my fglrx after such an upgrade because the driver doen't support the new kernel yet. 

If your supposed to use fglrx which I bthink try running $ fglrxinfo   to check if it's gone back to using mesa.

---

### Post by sjb05004 on 2007-02-16
yeah i'm using fglrx driver.  

fglrxinfo  in gde gives:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS Series Generic
OpenGL version string: 2.0.6286 (8.33.6)

glxinfo | grep render in gde gives:

direct rendering: Yes
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
OpenGL renderer string: RADEON XPRESS Series Generic


however in xgl... fglrxinfo is  the same:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS Series Generic
OpenGL version string: 2.0.6286 (8.33.6)

but glxinfo | grep render is not:

Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
OpenGL renderer string: RADEON XPRESS Series Generic

---

### Post by Wicca on 2007-02-16
Your 3D is working fine. When in XGL, glxinfo will always report that there's no rendering, because XGL uses it. So Beryl is not working for an other reason.
In the beryl menu, at 'choose window manager', what does it say? Beryl or Metacity? If you choose Beryl, what happens?

---

### Post by sjb05004 on 2007-02-16
it is usually on metacity.  when i change it to beryl everything starts to reload and then the screen goes completely white, however my cursor is still around. any ideas?

---

### Post by Motoxrdude on 2007-02-16
enter
```
glxgears
```
when in xgl. If it runs smooth then direct rendering is working. When in xgl it will say that direct rendering is off, but it is actually on btw.

---

### Post by Wicca on 2007-02-16
Well, ATi and Beryl is a dangerous combination, just read the forums :( 
You said that Beryl was working fine, but now it doesn't. When exactly did it stop working? Was it after a kernel-update,  or after a beryl-update? Mine Beryl stopped working when it wend from 1.99.2 to 1.99.9, about 2 weeks ago (ATi Radeon 9800 Pro here). Beryl started working again when I switched back to 1.99.2, and I've had no problems since then.

---

### Post by bjornolai on 2007-02-16
A friend had that white screen yesterday. There are other treads about this.. [http://ubuntuforums.org/showthread.php?t=336205](http://ubuntuforums.org/showthread.php?t=336205)
[http://pricechild.co.uk/?p=37](http://pricechild.co.uk/?p=37)

What I found from some reading was that running $ beryl  instead of $ beryl-xgl  made it work. However I do not think that is really a fix, but I know to little about these things to understand what it means.

---

### Post by sjb05004 on 2007-02-16
beryl used to work fine.  after a new install and following the same guide it is not.  glxgears runs smooth.  so maybe it is just beryl. would you suggest using compiz with ATI vs. Beryl?? if so i'll give it a try.

---

### Post by sjb05004 on 2007-02-16
Not sure if this will help any but the last time it worked well was about Jan 22.  From what I've been reading there are others getting this white screen after they have done standard updates for beryl, xgl, and some other rep.  They have also not had it working since Jan 22.  Anyone know what I could downgrade to reach the settings I had in mid Jan?

---

### Post by sjb05004 on 2007-02-17
not exactly sure what I did right, however beryl loads up fine now with all the eye candy.  i appreciate all the help. thanks.

---

### Post by Guajiro_NJ on 2007-02-26
I had the same problem with Beryl's white cube until today. Got on the Ubuntu support channel on IRC and a guy on there (TM4 - Thanks for the script man!) gave me the solution.

1) Create a file called '/usr/bin/startxglfix' (this is not the startxgl you created before!)

2) Add the following code to it:

[INDENT]```
#!/bin/sh
sleep 5
exec beryl-xgl --use-copy
```[/INDENT]

3) Save the file.

4) chmod a+x /usr/bin/startxglfix

5) Remove 'beryl-manager' from your Sessions Startups tab (go to System-> Preferences-> Sessions. Click on Startup Programs). 

6) Add '/usr/bin/startxglfix' to your Session Startup tab.

7) Click close.

8 ) Log out of your X session.

9) Log in to X, and make sure you select Xgl from you Sessions at the login screen.

10) You should see your default desktop now. Once your desktop has loaded, open a terminal. The terminal should have no border on it. (This is good!)

11) Run 'beryl-manager --no-force-window-manager' from this terminal.

12) You should see your desktop flicker for 5 seconds and then the Beryl splash should appear. If it does, move your terminal around and you should see the Beryl effects in play!

13) Finally, go back to Session Startups and add beryl-manager to the tab, but this time add it as 'beryl-manager --no-force-window-manager'.

This worked for me with an ATI Radeon Mobility X300 card on an Inspiron 6000 on the first try. Your mileage may vary, I posted this second hand from someone because I felt it was useful AND I couldn't find it anywhere on the web.

Credit goes to TM4 and who ever he leeched it from. :lolflag: 

Ubuntu -> :guitar:

---

