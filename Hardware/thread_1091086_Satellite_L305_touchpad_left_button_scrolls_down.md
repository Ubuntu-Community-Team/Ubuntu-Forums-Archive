---
title: "Satellite L305 touchpad left button scrolls down"
date: 2009-03-09
forum: Hardware
---

### Post by John Vance on 2009-03-09
Pressing the physical left button below the touchpad on my Toshiba Satellite L305 causes the current window to scroll down in addition to the expected left button action.  This occurs in every application with a scrollbar.  On the desktop pressing the left button cycles through the desktops.

Tapping on the touchpad causes proper simulated left button behavior and does not scroll the current window.  If I plug in a usb mouse the left button on that mouse also behaves properly and does not scroll the current window.

The physical left button was behaving properly until this afternoon.  It suddenly exhibited this behavior while my wife was using firefox.  She does not recall anything unusual happening before the left button started misbehaving.

Restarting the X server does not solve the problem.  Logging out and logging back in does not solve the problem.  Rebooting does not solve the problem.  The touchpad and buttons behave properly in Vista.  There do not appear to be any configuration settings in KDE 4.2.1 that address this issue.

Help?

EDIT: this is in Kubuntu 8.10 / KDE 4.2.1 with all updates (2.6.27-13 kernel)

---

### Post by John Vance on 2009-03-09
Lots of lookie-loos but nobody willing to hazard a reply, eh?

Here's some additional data.  Setting the mouse as left handed reverses the buttons, but the scroll event stays tied to the physical left button.  Reversing the direction of scroll (KDE System Settings | Keyboard & Mouse | General tab | Reverse scroll direction) makes pressing the left button cause the screen to scroll up. 

The physical left button behaves like you are rolling a scroll wheel one click, and then clicking the left mouse button.  When you try to click on a link, it causes the cursor to jump down from the link first, and then clicks on whatever is three lines below it.  Very annoying.

Again, any help would be appreciated here.

---

### Post by John Vance on 2009-03-10
xmodmap does nothing as far as I can tell.  xinput's documentation is a joke.  The man page is just BNF with no examples.  It might as well be line noise.

---

### Post by TomHum on 2009-03-10
Hello John

I have the same problem with my laptop (Acer Aspire). It started just today...virus?? Can't say what triggered it, but my girlfriend was also using the computer when it happened! 
Please let me know if find a fix. I have a partial fix....using a usb mouse as that works fine.

Tom

---

### Post by John Vance on 2009-03-14
It stopped today.  o_O

---

### Post by John Vance on 2009-04-25
The scroll event is back.  Switching to Gnome did not fix it.  Upgrading to Jaunty did not fix it.  Posting to this board resulted in no advice whatsoever.  I've mostly gone back to Vista on the laptop because it is far and away less annoying.  Also, power management works under Vista.  It does not work under Ubuntu Intrepid or Jaunty unless I suspend and resume first.

---

### Post by John Vance on 2009-10-31
This problem went away sometime this summer after a kernel update.  Karmic does not have this problem either.

Power management problems were solved in Karmic by adding the following parameter to the Ubuntu boot section, right after the "splash" directive:

acpi_osi="Linux"

Now lid close and plug/unplug events are handled properly by power management.  My Ubuntu laptop is finally usable as such! :D

---

