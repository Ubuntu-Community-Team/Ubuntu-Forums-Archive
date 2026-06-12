---
title: "Unofficial Starter Guide Tip..."
date: 2005-01-02
forum: General Help
---

### Post by LongTooth on 2005-01-02
I've just tried adding a multimedia pluggin to Firefox using the Starter guide. I have Mplayer installed and working with all downloaded video files but like so many on this forum 'embeded' files do not work. Thus my search for a solution. I thought this might help. I preformed these steps:


Q: How to install Multimedia Plug-in for Mozilla Firefox (Non-Pentium 4)?

   1. Read General Notes
   2. Read How to add extra repositories?
   3. Read How to install Multimedia Codecs?
   4.

      $ sudo apt-get install totem-xine
      $ sudo apt-get install mozplugger
      $ sudo gedit /etc/mozpluggerrc
   5. Find this section

      ...
      application/x-mplayer2: wmv,asf,mov: Windows Media
      video/x-ms-asf: asf,asx,wma,wax,wmv,wvx: Windows Media
      video/x-ms-wmv: wmv: Windows Media
              stream noisy ignore_errors: mplayer -really-quiet -nojoystick -nofs -wid $window -vo xv,x11 -ao esd,alsa9,oss,arts,null -zoom -osdlevel 0 "$file" </dev/null
      ...
   6. Add the following line below it

              stream noisy ignore_errors: totem "$file" </dev/null
   7. Save the edited file (sample)
   8. $ rm ~/.mozilla/pluginreg.dat

It did not work for me. I've removed all the packages installed. My concern is step #8. How do I go about reversing this procedure $ rm ~/.mozilla/pluginreg.dat? Or should I be concerned? 
Thanks.

---

### Post by Rancoras on 2005-01-02
I think that file is created when you install mozplugger.  I wouldn't worry about it.

---

