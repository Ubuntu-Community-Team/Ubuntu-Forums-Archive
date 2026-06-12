---
title: "firefox mailto: not working for thunderbird"
date: 2008-07-15
forum: General Help
---

### Post by wandalalakers on 2008-07-15
I have my settings as:

network.protocol-handler.app.mailto and /usr/bin/thunderbird but I still can't open mailto: links from firefox that I want to open thunderbird for email.

I'm sure my settings are correct.  This used to work when I had firefox 2 but can't remember if it stopped working after I upgraded to 3.

---

### Post by wandalalakers on 2008-07-15
I also have these settings:

    * network.protocol-handler.expose.mailto -> false
    * network.protocol-handler.external.mailto -> true
    * network.protocol-handler.warn-external.mailto -> false

---

### Post by silkstone on 2008-07-15
I also have all those values at default.

In FF, Edit > Preferences > Applications and see what is listed alongside 'mailto'.

Also System > Preferences > Preferred Applications and ensure that Thunderbird is the default Mail Reader.

---

### Post by wandalalakers on 2008-07-15
I tried making thunderbird the defaul mail client but that still didn't fix my problem.  I'll try making it the default again.  I'm using kubuntu by the way.

---

### Post by MickS on 2008-07-15
I have the same problem and have got round it by installing the simple mail extension to Firefox, not a perfect fix by any means but good enough for my needs.

Mick

---

### Post by pommyjohn on 2008-07-20
I have the same problem but the mailto is wrong how do I change it to Thunderbird please?

---

### Post by pommyjohn on 2008-07-20
i am using Firefox and Ubuntu, I select "use other" in the mailto line but how do i get to thunderbird from there?

---

### Post by fragos on 2008-07-20
Is Thunderbird set in Preferred Applications preferences? Also There were changes in Firefox 3 which even allow you to link mailto to the likes of Yahoo mail and Gmail. They envole the following parameter but the preferences should work.

gecko.handlerService.schemes.mailto.0.name

---

### Post by BobvanderPoel on 2008-09-09
Just hit with same bug after upgrading from 7.10 to 8.04. The problem appears to be only with folks using kubuntu installed over gnome. Two solutions:

1. use the firefox from mozilla, not the one supplied with kubuntu.

2. install the firefox-3.0-gnome-support  package. 

BTW, the key to the problem seems to be that if you go (in firefox) to edit->prefs->applications you get a empty window. Grabbing the above package fixed the problem.

This is for embedded mailto links and the 'send link' file option.

hope this helps.

---

### Post by wandalalakers on 2008-09-09
Installing the gnome support package didnt do anything for me.  I'll try installing firefox from mozilla.  thx
Neither fix is working for me.

---

### Post by wandalalakers on 2008-09-09
Here is the fix that worked for me.

[https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/222944](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/222944)

From Oliver:

Open firefox and enter "about:config" into the location bar.
Set the filter to "mailto". Locate the "network.protocol-handler.app.mailto" line, right-click and select "reset".
Close firefox.
Open nautilus/thunar/whatever and go to your firefox profile directory (/home/<user>/.mozilla/firefox/<some weird string>/)
There's a file called "mimeTypes.rdf". Remove it (or rename it, if you're the cautious type).
Start firefox again.
Right-click anywhere and select "Send Link...". A window should pop up that prompts you to choose your mailer application. Locate /usr/bin/thunderbird (or whatever is your preferred app). Click ok and the compose window should show up.

For the curious:
If you now take a look at the about:config page, you won't find the network.protocol-handler.app.mailto property anymore. It seems it is not used anymore in firefox 3, however having it still set after upgrading seems to seriously confuse firefox 3.

---

### Post by eudemus on 2009-06-04
Fantastic! That's saved my bacon nicely!

Eudemus

---

