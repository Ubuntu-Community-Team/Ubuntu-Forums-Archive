---
title: "Multiple Monitor Assistance Needed"
date: 2009-03-10
forum: Hardware
---

### Post by turiya on 2009-03-10
My current setup is a Dell Inspiron 600m attached to a Planar 1280x768 display. My graphics chipset is ATI. Whenever I run with both monitors the standard panels are on the built in laptop monitor and any application that goes to full screen is on that screen. My main problem is that I want to use the Planar display to watch movies while I work with applications on the laptop's built in screen, I need distraction to work, and I cannot get VLC to full screen onto the other display. I am unfamiliar with the internal workings of most of the settings files, I happen to get lucky and everything works fine without having to mess with anything. How do I change which display applications will fullscreen to?

---

### Post by Ceza on 2009-03-10
Hi Turiya,
   Ok, I was SO excited that I might be able to answer my first Linux question ever for someone else that I nearly screwed up my PC that my girlfriend uses. LOL!  Ok, I'm sure there are better ways to do this but I did actually manage to do as you are asking and it was "mostly" simple. 

I opened the CCC or ATI Catalyst Control Center but I didn't find any selection to choose the Primary Monitor like Windows has. So I clicked on the Display Manager and in the right side window you will see your 2 monitors and they will be numbered 1 and 2. Left click on the monitor 1 and drag it past your second monitor to the right and release. Now if it behaves like my girlfriends PC it will flash a bit and then you will see a crash window and under it you will see a window that says you have changed your settings and it will revert unless you click "Yes" within the 15 seconds. Click "Yes" to keep it.

Now here is the issue when you do this your screens will look the same. Meaning your task bar will still be in the same spot and your background pics will stay on the same monitors. But you will know the change occurred because you will need to move your mouse to the left to get to the right monitor instead of moving it between the 2 naturally. Basically it will act like your monitors are reversed even though the images and locations of stuff on the screens will be the same.

If you can live with that.. just start your distraction and you should notice it is now on the other screen when you pick full screen. 

I really hope this helps and that your ati driver doesn't crash like mine. BTW, even though mine crashed, it still worked perfectly and I am able to switch it back and forth although sometimes the CCC won't open and I need to reboot to get it to work again.

Good Luck!

Regards,
Ceza

---

### Post by ToFue on 2009-03-28
Ceza, can you post your /etc/X11/xorg.conf file?  

Can you succeed at this under windows (if installed on this machine)? I know there was a problem with laptops a few years ago, ATI cards in particular, that the VGA output was under-powered, making video rendering in dual graphics mode unattainable on the extended screen(desktop, whatever.. (at work when setting up presenters, we had to set them up on a single screen to render video to the second display device, though I doubt this is your issue)

 If that's not your issue, there are plenty of threads that can walk you through setting up xorg.conf and the device driver to get you what you're after which involve editing setting files by hand, binding your device, device driver, display, and screen together.  After that, there are other options available depending on your device and driver that can activate the gpu's acceleration features and so on.. among these settings is an option to eliminate dual taskbars on an extended desktop (such as setting the Xinerama option to 1).. however be careful that when you check out xorg.conf threads that you get information that applies to Your specific hardware situation, as you'll have much headache trying to get the x-server running again if it's inaccurate.. learn vim.

Check out this howto:

[http://ubuntuforums.org/showthread.php?t=221174&highlight=600m+dual+screen](http://ubuntuforums.org/showthread.php?t=221174&highlight=600m+dual+screen)


as far as getting a simple video to full-screen in the movie player,  right-click the video pane; this should allow a full-screen option..

---

