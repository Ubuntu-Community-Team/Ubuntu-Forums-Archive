---
title: "pidgin not showing protocols"
date: 2008-08-19
forum: General Help
---

### Post by mordox on 2008-08-19
I am using Ubuntu 8.04.1 .
When I start pidgin and navigate to manage accounts and try to add a new user. I cannot see any protocols to select from.

See the attached screenshot.

What seems to be the problem ?

---

### Post by Saggy Peanuts on 2008-08-19
That is a puzzler...
Stupid question, but have you tried uninstalling and reinstalling through synaptic?

---

### Post by mordox on 2008-08-19
yes i have tried reinstalling through synaptic

---

### Post by Saggy Peanuts on 2008-08-19
That is wierd, the packages I have installed for pidgin are,
pidgin (obvious)
pidgin-otr
pidgin-data
you could try to install those. 
Then try the pidgin website and install the most recent version. Thats the best I can do im afraid. Bit of a strange one that.

---

### Post by mordox on 2008-08-21
I have them .. I already have these installed

ii  pidgin                                       1:2.4.1-1ubuntu2.1                                   graphical multi-protocol instant messaging client for X
ii  pidgin-data                                    1:2.4.1-1ubuntu2.1                                   multi-protocol instant messaging client - data files
ii  pidgin-encryption                              3.0-2                                                pidgin plugin that provides transparent encryption
ii  pidgin-extprefs                                0.7-2                                                extended preferences plugin for the instant messenger pidgin
ii  pidgin-festival                                2.2-1                                                pidgin plugin to hear incoming messages using voice synthesis
ii  pidgin-guifications                            2.14-3                                               toaster popups for pidgin
ii  pidgin-otr                                     3.1.0-1                                              Off-the-Record Messaging plugin for pidgin
ii  pidgin-plugin-pack                             2.0.0-1                                              30 useful plugins for pidgin
ii  pidgin-themes                                  0.2-1                                                Smiley themes collection for pidgin

---

### Post by Saggy Peanuts on 2008-08-21
Ok. Can you tell me what is listed within this folder:
/usr/lib/purple-2/

---

### Post by mordox on 2008-08-21
Contents of /usr/lib/purple-2/

autoaccept.so    irchelper.so        liboscar.so@       perl.so
autorejoin.so    irc-more.so         liboscar.so.0@     pidgin-libnotify.la
autoreply.so     joinpart.so         liboscar.so.0.0.0  pidgin-libnotify.so
bash.so          libaim.so           libqq.so           psychic.so
buddynote.so     libbonjour.so       libsametime.so     showoffline.so
dbus-example.so  libgg.so            libsimple.so       simfix.so
dice.so          libicq.so           libxmpp.so         slashexec.so
eight_ball.so    libirc.so           libyahoo.so        ssl-gnutls.so
festival.la      libjabber.so@       libzephyr.so       sslinfo.so
festival.so      libjabber.so.0@     listhandler.so     ssl-nss.so
flip.so          libjabber.so.0.0.0  log_reader.so      ssl.so
highlight.so     libmsn.so           newline.so         statenotify.so
idle.so          libmyspace.so       offlinemsg.so      tcl.so
ignore.so        libnovell.so        oldlogger.so

---

### Post by Saggy Peanuts on 2008-08-21
Damn, really thought that would have been it.
Which protocols, do you need it for. The only thing I can think of doing now is to try to rebuild them through accounts.xml within 
/home/<user>/.purple/
but I have no idea whether that will work or not.

---

### Post by TenPlus1 on 2008-08-21
Uninstall Pidgin, Pidgin-Data and Libpurple, goto [www.getdeb.net](www.getdeb.net) and download the latest Pidgin 2.50 .debs, install Pidgin-Data, Libpurple and Pidgin in that order and see if that helps...

---

### Post by mordox on 2008-08-21
solved.

<! This may not be shortest way !>

Remove all pidgin packages (remove completely option in synaptic)
Remove .purple directories from home directory.
Rebuild pidgin from source (v2.5.0) .Created accounts using that.

Now reinstall pidgin packages.



I had previously tried removing the .purple directories, but that had not worked.

I now have the following packgages
ii  pidgin                                         1:2.4.1-1ubuntu2.1                                   graphical multi-protocol instant messaging client for X
ii  pidgin-audacious                               2.0.0-1                                              pidgin integration with Audacious
ii  pidgin-data                                    1:2.4.1-1ubuntu2.1                                   multi-protocol instant messaging client - data files
ii  pidgin-dbg                                     1:2.4.1-1ubuntu2.1                                   Debugging symbols for Pidgin
ii  pidgin-encryption                              3.0-2                                                pidgin plugin that provides transparent encryption
ii  pidgin-extprefs                                0.7-2                                                extended preferences plugin for the instant messenger pidgin
ii  pidgin-festival                                2.2-1                                                pidgin plugin to hear incoming messages using voice synthesis
ii  pidgin-guifications                            2.14-3                                               toaster popups for pidgin
ii  pidgin-libnotify                               0.13-0ubuntu2                                        display notification bubbles in pidgin
ii  pidgin-musictracker                            0.4.1-1                                              Plugin for Pidgin which displays the current music track in your
ii  pidgin-otr                                     3.1.0-1                                              Off-the-Record Messaging plugin for pidgin
ii  pidgin-plugin-pack                             2.0.0-1                                              30 useful plugins for pidgin
ii  pidgin-themes                                  0.2-1                                                Smiley themes collection for pidgin



Note: I added some extra packages like pidgin-dbg

---

