---
title: "Verified by Visa &amp; Firefox Problems"
date: 2008-07-20
forum: General Help
---

### Post by sml on 2008-07-20
I have tried to make payments with a few different website recently and they are using the 'Verified by Visa' protection which is causing problems.

I enter my credit card details & numbers then submit. The Verified by Visa window appears and the Firefox browser says 'Additional plugins are required to display all the media on this page'.

Has anyone else had this problem? A screenshot is attached.

Looks like it is linked to this ...
[http://forums.webhostdir.com/showthread.php?t=21798](http://forums.webhostdir.com/showthread.php?t=21798)

---

### Post by PmDematagoda on 2008-07-20
Did you try clicking on the place that's asking you to download the plugin and see if that solves your problem?

---

### Post by sml on 2008-07-20
Yep ... 'no suitable plugins found' :(

I can't seem to find anyone else with a problem whilst searching ubuntu forums and linuxquestions.org? Odd.

---

### Post by OscarPapa on 2008-07-20
Try contacting Visa, I doubt they have been so inconsiderate as to only allow Windows users to use their payment system..:confused:

---

### Post by sml on 2008-07-20
Hmmm ... well my Australian bank does not care and cannot help.

Visa direct have limited (basically no) contact details which I emailed 2 weeks ago and no response.

I am surprised that I cannot find any related threads?

---

### Post by PmDematagoda on 2008-07-20
Is it possible for you to figure out exactly what the required plugin is? If you could, then we may be able to help you to install it.

---

### Post by sml on 2008-07-20
Here is the connection detail ...

---

### Post by BUSHYBOB on 2008-07-20
This might help

[http://www.secpay.com/news/3D.pdf](http://www.secpay.com/news/3D.pdf)

---

### Post by sml on 2008-07-20
> **BUSHYBOB said:**
> This might help

[http://www.secpay.com/news/3D.pdf](http://www.secpay.com/news/3D.pdf)

Thanks. It seems to explain how the system works, but no solutions or tech details regarding linux / browser compatibility requirements for the final password verification.

---

### Post by AnonCat on 2008-07-20
> **OscarPapa said:**
> Try contacting Visa, I doubt they have been so inconsiderate as to only allow Windows users to use their payment system..:confused:

The corporate world seems to think that Windows is the only OS out there.  I've had similar problems with making online payments to my credit card and insurance companies.

---

### Post by sml on 2008-07-20
Yes. I have also had similar problems in the past. I find it surprising that I cannot find any other reports of problems when googling for 5 hours.

---

### Post by Master Chief on 2008-07-20
You are probably using the latest, but just to be sure; which Mozilla Firefox version are you using?

Please enter:  ```
about:plugins
```
in the location bar and tell us which plug-ins are installed (names in bold only)

Visit that page and do a View Source. Look for the line with the plugin info (object) and tell me the UUID of it.

I wonder if Flash and Java on websites work for you?!?

---

### Post by sml on 2008-07-20
> **Master Chief said:**
> You are probably using the latest, but just to be sure; which Mozilla Firefox version are you using?

Please enter:  ```
about:plugins
```
in the location bar and tell us which plug-ins are installed (names in bold only)

Visit that page and do a View Source. Look for the line with the plugin info (object) and tell me the UUID of it.

I wonder if Flash and Java on websites work for you?!?

Thanks Master Chief ... here we go ..

Firefox v3.0

Flash & java work ok

about:plugins
 - Shockwave Flash
 - iTunes Application Detector
 - Default Plugin
 - Demo Print Plugin for unix/linux
 - Totem Web Browser Plugin 2.22.1
 - Helix DNA Plugin: RealPlayer G2 Plug-In Compatible (compatible; Totem)
 - VLC Multimedia Plugin (compatible Totem 2.22.1)
 - Windows Media Player Plug-in 10 (compatible; Totem)
 - DivX® Web Player
 - QuickTime Plug-in 7.2.0
 - GCJ Web Browser Plugin (using IcedTea) 1.0

These lines are the plugin I think ....

"https://secure5.arcot.com/installCCPlugin/"
var pluginInstallURL = "https://secure5.arcot.com/installCCPlugin/";
<OBJECT ID="VPASChipCardPlugin"

---

### Post by Master Chief on 2008-07-21
Ok so this is the "ChipCardPlugin" developed by "Arcot Systems" ([http://www.arcot.com/](http://www.arcot.com/))

The UUID is BTW "41B91E42-6366-11D4-90DB-0050DAC37F9F" and the installation URL to install the plugin under Windows XP is:
 
[https://secure5.arcot.com/installCCPlugin/us/ChipCardPlugin_winnt.cab](https://secure5.arcot.com/installCCPlugin/us/ChipCardPlugin_winnt.cab) 

It appears to work in a VirtualBox session with Windows XP installed. That might currently be the only way (well almost) out for now. Note however that I e-mailed the support crew to see what they can do for us Ubuntials.

That's all for now ;)

---

### Post by sml on 2008-07-21
Thanks Master Chief!

I emailed the support (plus all the marketing email addresses in the 'contact us' section of the website) asking if they provide support for linux.

Plus I emailed the merchants advising them of the poor website transaction feedback (Singapore Airlines and ProBikeKit.com).

I ended up completing the transaction on a PC at work .... it didn't even work with Firefox on a Winblows PC! Had to use Internet Explorer.

---

### Post by sml on 2008-07-21
Here is the email address for others that may wish to write to Arcot:

[email]support@arcot.com[/email]

---

### Post by Metal Micky on 2008-07-21
Just to let you know that this is a new issue we have been made aware of. I have contacted our technical team with regards to the problems that you have encountered and we are working to understand why and how it is happening and establish how we can resolve it. 

There are no known issues with Linux or Firefox (I am a firefox user myself, and have not had any issues and several of our merchants and issuers are Linux based), so initially it is surprising. We do appreciate you raising the issue with us and will aim to resolve it as soon as possible. 

One of the things we pride ourselves on is the stability of our solution, so rest assured, we will look to get this bug fixed asap.

---

### Post by Master Chief on 2008-07-21
@Metal Micky: great to see someone picking this up!

Additional info/observations:

I visited: [https://secure5.arcot.com/installCCPlugin/us/](https://secure5.arcot.com/installCCPlugin/us/)
and this showed up:

Your browser type is Netscape
Your system platform is Linux x86_64
Your OS Version is 

And with Windows XP I got this:

Your browser type is Netscape
Your system platform is Win32
Your OS Version is Windows NT

Which are both wrong. I checked the used browser sniffing (done in JavaScript) and that I tell you needs a serious re-write.

p.s. Windows 95, 98, ME and NT are considered to be insecure (no more updates/support from Microsoft) yet these are the only supported OS versions, at least if we have to believe the JS code!

---

### Post by sml on 2008-07-24
Wow .. thanks Metal Micky. I am surprised and impressed that you found this post and took the time to register & respond.

But when I visited this page, there were no options to download a linux compatible plugin :(  .... just Winblows
[https://secure5.arcot.com/installCCPlugin/us/](https://secure5.arcot.com/installCCPlugin/us/)

I was going to try the exe plugin with Wine but the link doesn't seem to work ...
[https://secure5.arcot.com/installCCPlugin/us/ChipCardPlugin_win9x.exe](https://secure5.arcot.com/installCCPlugin/us/ChipCardPlugin_win9x.exe)

---

### Post by sml on 2008-07-24
Bad news .. just needed to make another order on a Arcot protected website and it was also broken :(

This online shopping is really hard work when you can't make payments!

---

### Post by Master Chief on 2008-08-07
Ouch!  Have you seen this article:

"Net shoppers bullied into being Verified by Visa"

[http://www.theregister.co.uk/2008/08/07/verified_by_visa_compulsion/](http://www.theregister.co.uk/2008/08/07/verified_by_visa_compulsion/)

---

### Post by ~Las~ on 2009-05-10
I too ran in to Vbv problem but not this kind It displayed a message saying[COLOR=Red]

"Sorry, we do not support the browser version that you are using.

     Please download and install a correct version of browser before using Verified by Visa."[/COLOR] 
I found out it was due to google tool bar i was using .I removed it and now it works.Maybe some other addons might do the same.
    [COLOR=Red]



[/COLOR]

---

