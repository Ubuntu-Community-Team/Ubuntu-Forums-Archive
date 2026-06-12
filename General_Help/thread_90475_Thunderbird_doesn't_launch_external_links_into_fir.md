---
title: "Thunderbird doesn't launch external links into firefox"
date: 2005-11-15
forum: General Help
---

### Post by dc2447 on 2005-11-15
Title says it all really.  Since doing a clean install of Breezy thunderbird doesn't spawn a firefox window when a hyperlink is clicked.

Firefox is my default browser - I have no such issues on a second system that was upgraded from hoary.

Anyone any ideas?

---

### Post by Pablo_Escobar on 2005-11-15
Heh, in Gnome there is a nice tool to setup a default browser, mail client and a terminal. I don't know how it's with KDE but I believe that Thunderbird not opening link in FF is a misconfiguration in default browser.

---

### Post by GoldBuggie on 2005-11-15
goto
```
Control Center->KDE Components->Component Chooser->Web Browser
```
and enter firefox as your default browser there. Everything should hopefully work after that.

---

### Post by chandra on 2005-11-15
[QUOTE=dc2447]Title says it all really.  Since doing a clean install of Breezy thunderbird doesn't spawn a firefox window when a hyperlink is clicked.

Firefox is my default browser - I have no such issues on a second system that was upgraded from hoary.

Anyone any ideas?[/QUOTE]

I have seen this appear so often on these forums that I made my own help file,
which  I reproduce below.  Do try it and let this forum know if it works, please:
===============================
Subject: Firefox-Thunderbird Integration
Acknowledgement: Ubuntu Forums: [http://ubuntuforums.org/showthread.php?t=22333&page=1&pp=10](http://ubuntuforums.org/showthread.php?t=22333&page=1&pp=10)
--------------
Purpose: Click on a mailto: link in Firefox to open that link in Thunderbird

Distribution/OS: Kubuntu Linux

HowTo:

1. cd ~/.mozilla/firefox/<SomeString.default>

2. If the file user.js does not exist, create it.

3. Append the following lines to the file:

//Firefox-Thunderbird mailto: Integration
user_pref("network.protocol-handler.app.mailto","/usr/bin/mozilla-thunderbird");

4. Close and restart Firefox, and test functionality.
--------------
Purpose: Click on an http: link in Thunderbird to open that link in Firefox

Distribution/OS: Kubuntu Linux

HowTo:

1. cd ~/.mozilla-thunderbird/<SomeString.default>

2. If the file user.js does not exist, create it.

3. Append the following lines to the file:

// Thunderbird-Firefox http: Integration
user_pref("network.protocol-handler.app.http", "/usr/bin/mozilla-firefox");

4. Close and restart Thunderbird, and test functionality.

UPDATE (17 Aug 05)
==================
See also:

Ubuntu Forums - HOWTO: The Definitive Firefox & Thunderbird "mailto" Fix
[http://ubuntuforums.org/showthread.php?t=18175](http://ubuntuforums.org/showthread.php?t=18175)

on how to fix a bug that came with an upgrade.

Alternatively and better,

edit

/usr/bin/mozilla-thunderbird

to replace all non-comment instances of

Mozilla-Thunderbird

by

mozilla-thunderbird
===============================

---

### Post by dc2447 on 2005-11-15
I'm not getting email notifications :(

> 3. Append the following lines to the file:

// Thunderbird-Firefox http: Integration
user_pref("network.protocol-handler.app.http", "/usr/bin/mozilla-firefox");

Was the right answer - much googling got me there but many thanks for the responses

---

### Post by teutontom on 2005-12-26
I have run into the same issue, firefox not opening from links in thunderbird. I have tried your solution, still no browser when I click a link. I have double checked the user.js that I created and everything is as you suggest. Any ideas what else I can try. Copying and pasteing links is a pain.
Thanks
Tom

---

### Post by Freddy on 2005-12-27
> I have run into the same issue, firefox not opening from links in thunderbird. I have tried your solution, still no browser when I click a link. I have double checked the user.js that I created and everything is as you suggest. Any ideas what else I can try. Copying and pasteing links is a pain.
Have you upgraded your Firefox to 1.5 with the help of Automatix ?. If so, your command for opening your browser should be only "firefox", change all mozilla-firefox to just firefox and it should work.   /// Freddan

---

### Post by TrinitronX on 2006-01-27
Instead of this method, I used the about:config utility within firefox.
Just put "about:config" for a url, and press enter.  You should see a list of firefox variables.  Right click and make a new string variable called "network.protocol-handler.app.mailto".  When it asks for the string, put "/usr/bin/mozilla-thunderbird".  Then restart firefox and test it out.
I'm not sure if there's an about:config type settings manager built into thunderbird though.

---

### Post by kosak on 2008-01-15
System> Preferences > Preferred Applications > Web browser Firefox option (or custom).

I had the same problem. I had Swiftfox, but had some troubles with their 3.0 beta and uninstalled it, just now I set the default to Firefox and It worked. 

Look at the attached picture. 

-kosak

---

### Post by drevicko on 2008-06-25
In Kubuntu with Thunderbird 2.0.0.14 and Firefox 3.0 I was able to use the config editor from within Thunderbird at Edit->Preferences->Advanced->General - "Config Editor" button.

In the Config Editor: right click->New->String
  Preference name : network.protocol-handler.app.http
  Value : /usr/bin/firefox

Note: the entry above has "/usr/bin/mozilla-firefox" - on my system there's no such thing (-;

I also setup https this way.

> **kosak said:**
> System> Preferences > Preferred Applications > Web browser Firefox option (or custom).

I had the same problem. I had Swiftfox, but had some troubles with their 3.0 beta and uninstalled it, just now I set the default to Firefox and It worked. 

Look at the attached picture. 

-kosak

Looks like you're using Mac OS..

---

