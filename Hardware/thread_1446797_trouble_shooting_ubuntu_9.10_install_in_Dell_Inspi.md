---
title: "trouble shooting ubuntu 9.10 install in Dell Inspiron 5100 - display problem"
date: 2010-04-04
forum: Hardware
---

### Post by khackbarth on 2010-04-04
I am trying to create an Ubuntu laptop using my old Dell Inspiron 5100 laptop.  The install itself was challenging because the laptop wouldn't boot from the CD no matter how I set the boot instructions.  I discovered that Ubuntu 9.10 had a dialog that lanched from windows and provides special software to support booting from the CD.
 
I was able to complete the installation but immediately noticed problems with the display.  The windows don't properly repaint when moved.  There are some artifacts at the top of the screen - horizonal lines.  Also I thought Firefox wasn't launching but in fact the window boarder was displaying but not the contents.  I could get the contents to display by launching the calculator and then dragging it across the face of the firefox window.
 
I've tried looking for additional drivers but I'm being told that there are no proprietary drivers in use and none suggested.
 
I've been able to run software update (though I had to figure out on my own that the box that was displaying on screen was asking for my admin password and not a progress bar - there was no label.
 
How can I begin troubleshooting and solving this problem?
 
Thanks,
Ken

---

### Post by bbrg548 on 2010-04-28
Go to System->Preferences->Appearance, and in the Appearance Preferences window go to the "Visual Effects" tab and select "none". This should make it usable.

I remember when the 5100 was my primary laptop there was a specific driver I had to use to get the effects working right. I'm trying to find it again so I can get it working the way I want.

---

### Post by khackbarth on 2010-04-29
THANKS!!  Made a huge difference.  Let me know if you find that special driver again.

---

### Post by fumandor on 2010-04-30
I second the request for the special driver.  I too have a Dell Inspiron 5100.  Figured out that you had to remove the special effects and now its usable but naturally it was the eye candy of wobly windows that im interested in ;)

---

