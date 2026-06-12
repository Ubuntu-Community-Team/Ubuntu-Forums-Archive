---
title: "eGalax TouchScreen Tablet pc"
date: 2010-05-26
forum: Hardware
---

### Post by RufusThorne on 2010-05-26
I converted my eee 701 into a tablet 

article here: [http://mothdesigns.co.uk/tablet/tablet_index.html]("http://mothdesigns.co.uk/tablet/tablet_index.html")


Ubuntu Netbook remi recognises my touch screen instantly after install, and it's great to see that. The axis are inverted, however. Moving up and down moves cursor left and right, and viceversa.
I am completely new to Linux, and netbook remix looks sooo good on the tablet, I need help sorting this out, so I can show off my ubuntu tablet. Please help guys!

My touchscreen is an eGalax - it works fine under Windows with drivers from the egalax site. I cannot find anything simialr in Ubuntu netbook remix, or any calibration tool.

Thank you in advance

-Rufus

---

### Post by Favux on 2010-05-26
Hi RufusThorne,

Welcome to Ubuntu forums!

Try this thread:  [http://ubuntuforums.org/showthread.php?p=9254202](http://ubuntuforums.org/showthread.php?p=9254202)  especially post #5.  Evtouch would probably be the other driver that works for your touch screen.

Hope this helps.

---

### Post by RufusThorne on 2010-05-27
Are those Terminal commands?
Do I need to type them every time I boot?

How can I enter Terminal commands when I have no physical keyboard, and rely entirely on an on-screen one?

Where is the shortcut for on-screen keyboard?

Thanks again for your insight.

---

### Post by Favux on 2010-05-27
Yes, they are terminal commands.  Copy and Paste?  Note, I'm not guaranteeing they'll work for you, you may need to alter them a little.

You don't have a usb keyboard to plug in?  You could also enter the commands through an onscreen keyboard like CellWriter.  For a tablet pc/slate you'd want at least CellWriter, Xournal, and EasyStroke.

If needed you can make a start up script.  Call it say .eGalax-axes.sh, make it executable (right click, Properties, Permissions tab), and set it up to run with auto-start so it is available with each session.

---

### Post by RufusThorne on 2010-05-27
Thanks, this is the help I needed!

How do I get CellWriter, Xournal, and EasyStroke in order to use as a tablet once more? Via built in package manager?

Once these modules are installed, how do I create shortcuts to them? and I have searched for hours for touch screen calibration, and the ability to 'swipe' through web pages.

Thanks again for your continued support.

---

### Post by Favux on 2010-05-27
Yes, they are available through Synaptic Package Manager.  To create a shortcut just right click on the destop and make a launcher for them.  Put their name in the command box.

---

### Post by RufusThorne on 2010-05-27
OK, nearly got this sorted. On Windows I had a permanent button on the taskbar that toggled OSK. Can I have something similar to this? Surfing the web, then clicking to return to home screen, then launching keyboard, and then going back to web-page again, justto fill in a form, is absurd.

As you can see from the link in Post 1, the machine has no physical keyboard and only a touch-screen and power button.

---

### Post by Favux on 2010-05-27
Well in Ubuntu you could drag the launcher into the panel.  I'm not sure about Netbook Remix, haven't used it.

The terminal commands for CellWriter to show itself or hide are:
```
cellwriter --show-window
cellwriter --hide-window

```

---

### Post by RufusThorne on 2010-05-27
> **Favux said:**
> Well in Ubuntu you could drag the launcher into the panel.  I'm not sure about Netbook Remix, haven't used it.

The terminal commands for CellWriter to show itself or hide are:
```
cellwriter --show-window
cellwriter --hide-window

```


OK, So I need to write a script which calls these arguments, and give it an icon, and find some way to always have that icon on top of the screen somehow...

Press-and-hold for right click doesn't seem to work as it did under windows?....

---

### Post by Favux on 2010-05-27
Right.  You could start with two separate launchers, one Show and one Hide, and enter the commands in the command box to begin with.

---

### Post by Favux on 2010-05-27
```
Press-and-hold for right click doesn't seem to work as it did under windows?.... 
```
Not sure what to do about that.  You could try Preferences > Assistive Technologies > Mouse Accesibility > & check "Trigger secondary click by holding down primary button".

---

### Post by Favux on 2010-05-27
Sorry, forum did another double post.

---

### Post by RufusThorne on 2010-06-06
OK, so to solve the inverted X-Y problem:

```
xinput set-prop --type=int --format=8 "eGalax Inc. USB TouchController" "Evdev Axes Swap" 1
```


(from the forum post quoted on page 1)

However I am stuck on this:

```
xinput set-prop --type=int --format=32 "eGalax Inc. USB TouchController" "Evdev Axis Calibration" 57 1938 162 1979
```

I need to generate my own coordinates from this application?
[http://www.freedesktop.org/wiki/Software/xinput_calibrator](http://www.freedesktop.org/wiki/Software/xinput_calibrator)

Does this also need doing every boot,or can I use the --persistent option or something similar?

---

