---
title: "Thunderbird/webmail stopped working after Windows Live update. &quot;negative vibes&quot;"
date: 2008-11-05
forum: General Help
---

### Post by madsc89 on 2008-11-05
About 10 hours ago, my "hotmail.com" looked different than it does now. I believe this update is the cause: [http://www.windowslive-hotmail.com/comingsoon/en-us/default.htm](http://www.windowslive-hotmail.com/comingsoon/en-us/default.htm)

It seems that this might have caused my Thunderbird/webmail to stop working.

When trying to download mail, I get this error: 
Alert
Sending of password did not succeed. Mail server localhost responded: negative vibes from <my username>@hotmail.com

When I press OK, I am told to reenter my password. I do that, and press OK. Nothing happens. When I push Get Mail, the problem repeats itself.

Both of the necessary servers are green, and the plug ins are fully updated. I've tried to restart both Thunderbird and the session.

Is it related to what I mentioned above?
Does anyone else experience this problem?
How can I fix this?

Thank you

---

### Post by James Dee on 2008-11-05
I have the same problem.
No idea how to solve it.

:guitar:

---

### Post by kellemes on 2008-11-05
Open Add-ons dialog -> Webmail-Hotmail -> Options -> Change mode to WebDav.
Works for me again..

---

### Post by theamber on 2008-11-05
> **kellemes said:**
> Open Add-ons dialog -> Webmail-Hotmail -> Options -> Change mode to WebDav.
Works for me again..
Where is that in firefox?

---

### Post by kellemes on 2008-11-05
> **theamber said:**
> Where is that in firefox?

I'm talking Thunderbird..

---

### Post by James Dee on 2008-11-05
Changing mode to WebDav worked for me.
Thnx kellemes...
):P

---

### Post by solitaire on 2008-11-05
I've the same problem here.

Ive tried all 3 options, none of them work (It was originally set to use WebDev.)

any other ideas?

---

### Post by kellemes on 2008-11-06
> **solitaire said:**
> I've the same problem here.

Ive tried all 3 options, none of them work (It was originally set to use WebDev.)

any other ideas?

Nope, a lot of folks have issues with this for some reason, WebDav doesn't work for everyone.
I can only advise to keep an eye on [the extensions website]("http://webmail.mozdev.org/index.html") and especially [there forum]("http://groups.google.com/group/thunderbird-webmail-extension") for info and updates.

---

### Post by solitaire on 2008-11-06
Looks like it's working now.

I removed ALL the WebMail components from Thunderbird and reinstalled them.
It's now Downloading all my Hotmail emails again :D

---

### Post by timcredible on 2008-11-06
think about it - you're using a microsoft email service with linux.  do you really expect that microsoft is going to let hotmail work with linux?  your best solution is to get another email account somewhere that's linux friendly (gmail, whatever), then go to a windows machine, login to your hotmail and forward all your mail from there to your new email address.  problem solved forever.

---

### Post by madsc89 on 2008-11-06
Didn't work for me either.

I'm am going to reinstall webmail plugins, but does that delete my emails? Is there a way to take a backup of my inbox?

Thank you

---

### Post by madsc89 on 2008-11-06
> **madsc89 said:**
> Didn't work for me either.

I'm am going to reinstall webmail plugins, but does that delete my emails? Is there a way to take a backup of my inbox?

Thank you

It did not delete my profile or my emails. However, it didn't solve the problem either...

Any other suggestions?

Thank you

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

---

### Post by andrewcauson on 2008-11-10
Hotmail only let you forward mail to other msn/ hotmail/ live accounts.

---

### Post by madsc89 on 2008-11-10
> 1. In Thunderbird Open Tools Add-ons dialog ->Webmail-Hotmail -> Preferences -> Change mode to WebDav. Restart Thunderbird

2. Check all your setting for ports and SMTP servers i.e.
Open Tools Add-ons dialog ->Webmail >Preferences and make sure the ports are still set.

3 Go thru your accounts settings and make sure both the ports AND the SMTP servers are set right (mine had changed) I also had to change my SMTP to my email address ########@hotmail.com Once everything is as it should be restart Thunderbird and cross your fingers.

If it still doesn't work go back thru and check it again maybe you overlooked something. Good luck

P.S. I did NOT uninstall and reinstall my Webmail or Hotmail plugins in Thunderbird.

Hope this helps.

Thanks for the effort, but I tried it three times, and still to no avail.

Any other suggestions?

Thank you

---

### Post by stoogiebuncho on 2008-11-17
Thanks for the fix, 2hot6ft2.  I just wanted to add a slight modification.

You can change the general.useragent.vendor in your user agent switcher profile, meaning you won't have to go into about:config to change it.  

So this is what you would do:

Install the User Agent and create a profile: (if you are using Firefox 3.x on Linux)

Descriptiong: Firefox 3.x (WinXP)
User Agent: Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US; rv:1.9.0.3) Gecko/2008092417 Firefox/3.0.3
App name: Mozilla Firefox
App Version: 5.0 (Windows; U; Windows NT 5.1; en-US; rv:1.9.0.3) Gecko/2008092417 Firefox/3.0.3
Platform: Win32
Vendor: Firefox
Vendor Sub: {leave blank}

Now you don't have to mess around with about:config at all.  :guitar:

---

### Post by paul.sild@hotmail.com on 2008-12-02
THANKYOU SO MUCH!

Solved for me!!

---

### Post by vlke on 2009-09-01
I had the same problem starting this morning (1 Sept. 2009). Until now everything was working fine. Today I started to get "negative vibe ..." message. My "mode" settings for "WebMail-Hotmail" were on WebDav so i changed it to "**HOTMAIL LIVE (new website)**" and it works again. 
Thank you.

---

### Post by Rocky1980 on 2009-09-02
I have tried all the above to get hotmail to work in Thunderbird, but with no luck at all :( However I have found out that the port in in the webmail prefs has changed from 110 to 995, thunderbird tells me that some OS`s block ports below 1024. The port is showing error in the box with a red led above it. How do I go about "opening" port 995 ???? 

Many thanks

---

### Post by Rocky1980 on 2009-09-02
UPDATE:

Sorry for the double post, but I have found another solution. First forget about all the web mail stuff.
1. Ask thunderbird to create a new email account (not a web mail just a basic email account)

2. Put in your hotmail address, set the pop3 to pop3.live.com 

3. In the server settings  go to security settings and click the SSL box (make use the use secure auth box is NOT clicked). This will game the portto 995.

4. Restart thunderbird

It worked for me and all my homtail emails now come into my local folder :)

---

### Post by happyisland on 2009-09-02
thanks for the help, Rocky. Your solution worked perfectly for me.

---

