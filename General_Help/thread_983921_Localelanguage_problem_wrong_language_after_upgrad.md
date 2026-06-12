---
title: "Locale/language problem: wrong language after upgrade to 8.10"
date: 2008-11-16
forum: General Help
---

### Post by olifhar on 2008-11-16
***Update again!** Got things to work! ...well, mostly. I'm keeping this post as-is and answering my own question as a reply below.* 

***Update! ** After another futile logout/login && reboot/login, noticed that $LANGUAGE is different in a tty (i.e. outside of KDE). Seems to be a KDE specific thing. The output below is pulled from pseudoterminals.*

Just upgraded to Kubuntu; 8.10 Intepid Ibex, and it *looks* nice, but now I have to deal with the problems implied by any upgrade to a system rife with customizations I've forgotten I've made...

First among them is right after upgrade, a lot of my applications (which were in English before) have their menus and dialogs in Japanese. I can't quite figure out the pattern: most of the KDE apps are okay but Dolphin is not, Pidgin is in Japanese, GIMP is in English. Even [FONT="Courier New"]apt[/FONT] and its friends are in Japanese.

FUN!

Now, I'm learning Japanese on a casual basis, but needless to say, I'm not quite ready to embrace immersion on *this* level just yet. Not with my present skill level. For my purposes, it is the wrong language.

Okay, so I investigated and turned up [a few pages like this one]("http://blog.andrewbeacock.com/2007/01/how-to-change-your-default-locale-on.html"), which told me to take a look at some environment variables pulled up by [FONT="Courier New"]locale[/FONT]:
```
$ locale
LANG=en_US.UTF-8
[COLOR="Red"]LANGUAGE=ja[/COLOR]
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=

```

Aha, the offending environment variable! So I added the following lines[SIZE="1"](1)[/SIZE] to [FONT="Courier New"]/etc/environment[/FONT] (which was ominously empty except for setting [FONT="Courier New"]$PATH[/FONT].)

```
LANG='"en_US.UTF-8"'
LANGUAGE='"en_US.UTF-8"'
```

And then I ran [FONT="Courier New"]sudo dpkg-reconfigure locales[/FONT], logged out.

Didn't work, so I ran [FONT="Courier New"]sudo dpkg-reconfigure locales[/FONT], rebooted.

Didn't work. Pidgin, [FONT="Courier New"]aptitude[/FONT] and some elements of Dolphin are still in Japanese, which *looks* cool since I am dork, but are not what I want.

Any thoughts on where the [FONT="Courier New"]$LANGUAGE[/FONT] variable is finally set, if not in [FONT="Courier New"]/etc/environment[/FONT], and where I can change it? I've tried going to the 'System Settings'::'Regional & Language' panel and making sure the 'Country or Region' is set to 'United States of America'. I even stepped through the 'Select System Language' dialog and (as far as I can tell: all the prompts were in Japanese) selected English (ei-go, A-me-ri-ka) as the system language. It downloaded some packages, said something about logging in. I tried logging in and out, then rebooting: no go.

To summarize, here is what I'd like:
[LIST=1]
[*]English as the default language for all applications
[*]Japanese and other languages, like Chinese as *available* languages for input (meaning, I don't want to completely remove all other languages just to get English menus)
[/LIST]

It *feels* like it should be simple. Can someone point me in the right direction, show me how obvious it all is?:)

[COLOR="DimGray"](1) You may have noticed that I wrapped the double-quoted entry in single quotes. I did this on the second try, in hopes that it might be one of those shell thingies causing this whole mess. Doesn't look like it.[/COLOR]

---

### Post by olifhar on 2008-11-16
Here is how I got things back to English. Boy was I overlooking some obvious things, so there may be an even simpler way to do it.

After trial and error, I found the only thing that worked was DELETING all the other languages except the one I wanted (US English.)

Below are the steps to follow if you want to do the same thing. Note that these instructions assume you are the only user, or that all users will use the same default language. Also, I give the labels for the buttons in English. I'll try to post screenshots later so you can find them based on positioning.

[LIST=1]
[*]Go to KDE's System Settings (via the main menu: just type 'System Settings' into the filter.)
[*]Click on the icon labeled Regional & Language (on the 'General' tab)
[*]Select Country/Region & Language (should be selected by default).
[*]On the 'Locale' tab to the right, you should see the installed languages and the 'Country or Region'.
[*]If the information next to 'Country or Region' is wrong, click '(change...)' to fix it. Once done or if it's okay, go to the next step.
[*]In the box under 'Languages:' you should see the languages installed on your system. Hopefully the language you want is there: if not, click the button "Install New Language" to add it to the list. You will also need to click 'Add Language' so it appears in the list. Follow those instructions before going on to the next step.
[*]Now, for EACH of the languages you do NOT want as default, highlight its entry in the box and click the 'Remove' button.
[*]You should now be left with only the language you want as your default.
[*]Click the 'Apply' button.
[*]At this point, you may want to log out and back in to see if this has worked.
[*]Now, open up System Settings/Regional & Language again, if you logged out or closed it. Click the button 'Select System Language'. It may ask you if it's okay to do a network update; make sure you're connected to the internet, then say okay. A dialog will tell you if it was successful.
[*]The dialog box will now allow you to select the System Language from among a list of languages. Select the language you want. (I don't know what it *really* does, but I checked the "Enable support to enter complex characters" option.)
[*]Then click the 'Set System Language' button (which is the one with the check mark if this dialog is in a language other than English.)
[*]Now, back at the 'System Settings'/'Region & Language' window, click 'Apply'.
[*]Log out, log back. See if all this has worked-- open a few of the applications that had the wrong language before.
[*]If everything looks okay, you're done! Otherwise, give this a try: open up a console and run: ```
sudo dpkg-reconfigure locales
```
When you log out or restart , then log in, hopefully everything should be in the language you want.
[*]At this point, if you optionally do want support (menus/messages/console output) for other languages, you can try going to the 'Region & Language' and clicking 'Add' to put them back in the list.
[/LIST]

---

