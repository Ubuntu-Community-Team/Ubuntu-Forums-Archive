---
title: "Use a web page or SWF file as a screensaver?"
date: 2008-08-08
forum: General Help
---

### Post by andrewkk on 2008-08-08
Is there a way to use a web page or SWF file as a screensaver?

Could Prism or Firefox be rigged up to do this?

---

### Post by sapg on 2010-07-13
I'd like to do something like this, did you ever find a solution?

---

### Post by andrewkk on 2010-07-13
Nope, sorry. It wasn't very important to me so I gave up looking. Still seems like there should be a way to do this though.

---

### Post by slidersv on 2011-01-08
> **andrewkk said:**
> Is there a way to use a web page or SWF file as a screensaver?

Could Prism or Firefox be rigged up to do this?

I wrote the guide on how to do it and posted it here:
[http://www.bitsonwire.com/?p=209]("http://www.bitsonwire.com/?p=209")

Here is an excerpt for people that are searching:
Step 1. Extract/Get SWF file you intend to use as a screensaver. If you have a MacOS screensaver, search the installation folder for SWF files using search tool. Put SWF file somewhere safe, where you won’t accidentally delete it. For example:
```
cd ~
mkdir .screensavers
copy flash_screensaver.swf ~/.screensavers
```

Step 2. Remove/Disable/Adjust your default screen saver so it does not conflict with xscreensaver. On ubuntu this can be accomplished using:
```
sudo apt-get remove gnome-screensaver
```

Step 3. Install xscreensaver and check if it works.
```
sudo apt-get install xscreensaver
```
On ubuntu: System > Preferences > Screensaver
And try setting some screensaver, click preview, and if it works, close the window.
(Note: this is important, launching xscreensaver for the first time will create configuration file in your home directory)

Step 4. Install Opera and Flash plugin, if you haven’t already
```
sudo apt-get install opera
sudo apt-get install flashplugin-nonfree
``` 
(Note: Opera can be substituted for any other browser that supports Kiosk Mode. Firefox for example can be used with R-kiosk plugin. Important thing is to use the browser that you won’t be using for anything else but the screensaver)

Step 5. Edit xscreensaver setting and create your own Flash screensaver.
For example, if your SWF file is located at
/home/user/.screensavers/flash_screensaver.swf
then add the following line to ~/.xscreensaver after “programs:”
```
"My Flash Screensaver"	opera -kioskmode /home/user/.screensavers/flash_screensaver.swf	\n\
```

Step 6. Set your screensaver as default in xscreensaver, and check how it works by clicking on preview.
(Note: Opera might take about 4-5 seconds to close after mouse move. You can press ALT+F4 to speed up the process. Other browsers might be quicker)

That’s it. Now you should have fully functional flash screensaver in linux. This method can be used to put up any web page as a screensaver. This method can also be used to install windows screensavers on linux by using wine and /s switch. Although that might require some tweaking because xscreensaver draws a root window over everything, and sometimes has problems drawing over wine.

---

### Post by perspectoff on 2011-01-08
If you were using Kubuntu (KDE), this would be trivial.

Kubuntu K menu -> System -> System Settings -> General -> Desktop ->

Screensaver -> Banners & Pictures -> Media Screen Saver -> Setup... -> Add..

You could then add any video in any format you choose, and in fact could use any number of media files, to be rotated randomly if you choose.

---

