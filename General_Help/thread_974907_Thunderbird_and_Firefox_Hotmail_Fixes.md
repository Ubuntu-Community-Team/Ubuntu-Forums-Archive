---
title: "Thunderbird and Firefox Hotmail Fixes"
date: 2008-11-07
forum: General Help
---

### Post by 2hot6ft2 on 2008-11-07
Found 3 possible solutions and tried all 3 plus a a little checking and finally got it working again. Since I've been pasting the fixes in a txt file I'll break them down.

To fix live hotmail in firefox I did both of these

1. In the address bar of Firefox put about:config hit enter, in the Find put general.useragent.vendor Select it and Right click on it then select Modify and change it to Firefox from Ubuntu, then restart Firefox.

2. In Firefox click on Tools then Add-Ons > Get Add Ons and put User Agent Switcher in the search and install it then follow the instructions in the quote below.

BEGIN QUOTE-----------------------
Install the User Agent and create a profile: (if you are using Firefox 3.x on Linux)

Descriptiong: Firefox 3.x (WinXP)
User Agent: Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US; rv:1.9.0.3) Gecko/2008092417 Firefox/3.0.3
App name: Mozilla Firefox
App Version: 5.0 (Windows; U; Windows NT 5.1; en-US; rv:1.9.0.3) Gecko/2008092417 Firefox/3.0.3
Platform: Win32
Vendor: {leave blank}
Vendor Sub: {leave blank}

and you'll be able to use the new Live Hotmail just fine! You'll even skip the dialog page that ask you to upgrade to IE, FireFox, etc..

I think this proves that Microsoft has intentionally gone out of their way AGAIN! need I say more?

--Doug

P.S.> if you are using Firefox 2.x on Linux:
Description: Firefox 2.x (Win2K)
User Agent: Mozilla/5.0 (Windows; U; Windows NT 5.0; en-US; rv:1.8.1.17) Gecko/20080829 Firefox/2.0.0.17
App Name: Mozilla Firefox
App version: 5.0 (Windows; U; Windows NT 5.0; en-US; rv:1.8.1.17) Gecko/20080829 Firefox/2.0.0.17
Platform: Win32

and if you are sick, go ahead and lie to Live Hotmail on a Windows machine using Firefox 2.x/3.x but claim you are on Linux .. and you'll be unable to use Live Hotmail correctly!

change the Platform to Linux and the Agent to "Mozzila/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.17) Gecko/20080922 Ubuntu/7.10 (gutsy) Firefox/2.0.0.17" (and app version to the "5.0 (X11 ..." part) and Platform to Linux!

(or equiv for Firefox 3.x which I won't bother to post)
dx9ss
END QUOTE-----------------

When I did this and went to hotmail to send a test email I could compose it but it wouldn't send it UNTIL I clicked on Tools > User Agent Switcher and selected the Firefox 3.x (WinXP) profile I had created. Once I did it sent it on its way.

****************************
Firefox fixed:D Now for Thunderbird
***************************

1. In Thunderbird Open Tools Add-ons dialog ->Webmail-Hotmail -> Preferences -> Change mode to WebDav. Restart Thunderbird

2. Check all your setting for ports and SMTP servers i.e.
Open Tools Add-ons dialog ->Webmail >Preferences and make sure the ports are still set.

3 Go thru your accounts settings and make sure both the ports AND the SMTP servers are set right (mine had changed):confused: I also had to change my SMTP to my email address ########@hotmail.com Once everything is as it should be restart Thunderbird and cross your fingers.

If it still doesn't work go back thru and check it again maybe you overlooked something. Good luck

P.S. I did NOT uninstall and reinstall my Webmail or Hotmail plugins in Thunderbird.

Hope this helps.:guitar:

And thanks to all the original posters of the info here as I was trying everything and going from thread to thread there wasn't any criss cross thread quoting planning ahead of time.

Mod or Admin please add the tags: Thunderbird, firefox, hotmail, live mail

---

### Post by 2hot6ft2 on 2008-11-09
The latest Thunderbird extension can be found here [http://groups.google.com/group/thunderbird-webmail-extension](http://groups.google.com/group/thunderbird-webmail-extension)

It also appears to work and you can set Tools>Add-ons> WebMail - Hotmail>Preferences to Hotmail Live (New Website)
:popcorn:

---

