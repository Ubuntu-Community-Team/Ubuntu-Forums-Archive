---
title: "The &quot;Everything Just Works&quot; Install Procedure"
date: 2009-06-17
forum: Installation &amp; Upgrades
---

### Post by travisrichardson1980 on 2009-06-17
Alright, guys, I'm new to the forum, but I've got a bit to contribute. I've been poring over Xubuntu for over a week, in a migration away from my "Everything Works" remaster of TinyME.

The effort was to remaster the Xubuntu disk in a way that included all packages required to autoplay DVDs and CDs, and have VLC, Frostwire, OpenOffice.Org, and Audacious pre-installed, and have all of the appropriate file defaults set. Alas, this installation totals up just over 3 gigs on disk, and after remastering, becomes an 890 mb disk image, which is impossible to burn on a regular CD, which is what most old "found" or "trashed-picked" white box computers have. I'll attempt a burn to DVD, and I may make the iso available if it works. That's a topic for later, though.

So I'm not letting my progress go to waste. Below, you'll find my "Everything Just Works" installation method for Xubuntu 9.04. It is already assumed that you are familiar with installing the OS and may be having trouble installing and configuring some very commonly used Windows-replacement programs.

Most importantly, the method I describe below does not require the use or addition of any repositories belonging to any other distributions,or any selection of additional software sources. In fact, it only requires the entry of a single line in to a terminal. The rest is done naturally, through point and click! 

What I've outlined will seem simplistic, but it has taken nearly a week to find answers to all of the questions that it addresses, and allows us to neatly avoid several pitfalls that have caused me MULTIPLE re-installations after a given failure. Hopefully, my work will help you guys avoid the myriad problems I faced when first migrating to this AMAZING operating system!! Next, we'll look at what this procedure will accomplish.



This procedure achieves the following:

** installs:**
    frostwire
    java
    flash
    xubuntu restriced packages
    audacious
    vlc
    dvd encrypted codecs
    mp3 codecs
    openoffice.org
    audio cd autorun and playback
    dvd autorun and playback

** fixes:**
    issues with frostwire/java failure
    audacious mp3 playback
    openoffice.org save format defaults 

** avoids:**
    difficult terminal commands
    unlocking any "non-xubuntu" repositories
    
    



Alright, if you're ready, we'll get to it!
    





** XUBUNTU 9.04 J.J. INSTALLATION NOTES for best results**

_ 1.make a clean install_

_ 2.console: sudo apt-get update_

_ 3.INSTALL FROSTWIRE_ next, BEFORE anything else!
      if you unlock the 'restricted packages' first,
      java seems to have problems installing later,
      and frostwire will not run correctly.
      - go to frostwire.com>downloads>ubuntu>and follow
        the prompt to install the package. java will
        install automatically.

_ 4.install the following, using add/remove:_
       -xubuntu restricted packages
       -openoffice
       -vlc
       -audacious

_ 5.make audacious the default for mp3 files in thunar:_
             -open thunar, right click any MP3 file,
             -choose "open with...", choose Audacious,
               and leave the "open all file of this type"
               checkmark in place. done.

_6.make DVDs and audio CDs autorun_
             -open thunar, choose edit>preferences>advanced
               >"configure" volume management
               >"multimedia" tab
             -Audio CD field, enter without quotes:
               "vlc cdda://"
             -CD/DVD field, enter following without quotes:
               "vlc /dev/sr0"

_7.openoffice - set microsoft formats as the save defaults:_
              -go to tools>options>load/save>general
                >document type
              -set text,presentation,spreadsheet to
                  97/2003/xp default

_8.install hidden DVD codecs:_
       (not available until "xubuntu restricted" package is intstalled)
    -open terminal       
    -sudo su (enter pwd at prompt)
        -cd /usr/share/doc/libdvdread4
        -input command:
        ./install-css.sh

_9.fix audacious MP3 playback_
       -preferences>audio>current output plugin:>OSS Output Plugin

_10.fix the taskbar sound control:_
click the sound icon on the top right, manager will open
      -click the add channel button, add "master" and close
      -right-click the sound icon and click OK to close again.
      -now the scroll wheel will adjust the volume when mouse is
       over the sound icon in the taskbar!


** And you're done! **

Be sure to watch for my next post, which addresses issues
regarding the cloning of hard drives, so that you can "roll
out" your newly mastered operating system, and avoid a
lengthy install time for each computer that you build!!

Thanks again for reading, I hope this has helped you!!

---

