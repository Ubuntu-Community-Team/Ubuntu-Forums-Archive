---
title: "Ubuntu/Firefox/Hotmail(Microsoft Live) - Send Mail Bug/Error"
date: 2008-10-06
forum: General Help
---

### Post by Grams79 on 2008-10-06
It has something to do with Java I believe.... or AJAX.

When logging into Hotmail "Windows Live".
On Firefox 3.03 and Ubuntu 8.04.
----------------------------------------------------------------------
Upgrade your web browser
We recommend that you upgrade your web browser so you can get the most out of Windows Live Hotmail. Upgrading should only take a few minutes. To get started, choose one of the browsers below:

    * Microsoft Internet Explorer
    * Mozilla Firefox
    * Apple Safari

If you don't want to upgrade right now you can still _continue to Windows Live Hotmail_, but some parts of it may not work and it may not be displayed properly.
Got a mobile device? Check your e-mail by going to http:/mobile.live.com/hm.
----------------------------------------------------------------------

After selecting "continue to Windows Live Hotmail" I can view and read email.
The problem is that the option to switch from "Rich Text" editor is not working.
And can not switch to another editor mode like HTML and plain text.
The Rich Text editor is default and seems to be disabled as the options such as Bold are not selectable.
Can't even type in the message field...

WISH THERE WAS A WAY TO GET BACK TO CLASSIC HOTMAIL.
There is no way after you accept the new Live version.

:confused:
Hell.. you know what... Microsoft can kiss my butt.
I might move all my email registration to Google email.

Guess I am looking for a solution for my clients who I have talked into using Ubuntu.
Just today one of them ask me about the issue.
I told them I would try to get an answer.
Thanks in advance.

---

### Post by scouser73 on 2008-10-07
Yeah, I don't use Hotmail/Live but I have encountered it when helping a mate out.  Google is one of many excellent email providers, you should check out GMX also; [http://mail-eu.gmx.com/]("http://mail-eu.gmx.com/") They're a German company but they have offices in the States, pretty good too, I use them as well as Gmail.

---

### Post by Grams79 on 2008-10-07
Can't believe that I'm the only person to see this error on 5 different machines this month.
All latest Ubuntu and Firefox versions installed.

Did I post in the wrong forum area??
This is not a small bug and should be addressed.

If anyone has another post about this issue add the link here to string this problem.
Thanks!

---

### Post by esc1 on 2008-10-20
This problem is getting on my nerves as well.

---

### Post by cl0ckwork on 2008-10-20
same thing here, but i use hotmail for all my spam/subscriptions

gmail for real email that i use :lolflag:

---

### Post by Grams79 on 2008-10-21
I have a ton of clients who trusted me to install Ubuntu on their systems.
They all have the same error with Hotmail.
I've got nothing to give them as a solution other then switching to another email service.
Damn you Microsoft!! Damn you!!!!! lol

---

### Post by scouser73 on 2008-10-21
Tell your clients about Gmail, or GMX. [http://mail-eu.gmx.com/]("http://mail-eu.gmx.com/")

---

### Post by bhavin66 on 2008-10-27
same thing here, but i use hotmail for all my spam/subscriptions

---

### Post by klep on 2008-10-27
just a note to say ive got this same problem using firefox 2 and also opera 9. really seriously annoying. suggestions to change email providers are fairly unhelpful.

---

### Post by cl0ckwork on 2008-10-27
ummm... mine doesnt do that anymore...

using version--

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.4pre) Gecko/2008101118 Firefox/3.0.4pre (Swiftfox)

---

### Post by PooAvenger on 2008-10-30
Yeah i've got the same problem. anyone know if you can convert back to classic mode? or a solution?

---

### Post by koyote on 2008-10-31
Hi,

Exact same problem here. I have latest ubuntu, latest firefox and new hotmail. I want to change my email address, but i can't. Any help anyone?

---

### Post by cl0ckwork on 2008-11-01
no solution as of now.
microsoft sticks you with pretty much one option...


go to gmail =P
best solution ive found

---

### Post by timwaters on 2008-11-01
solution, found on these forums, for firefox, at least. Hotmail is still broken with Opera here.

in firefox:
about:config
change the value for general.useragent.vendor from Ubuntu to Firefox, and restart.

apparently this value gets reset every now and again.



The other way I've viewed hotmail on ubuntu is via crossover/wine and ie6

---

### Post by smoqueur on 2008-11-01
Hi,

I have the same problem on my Ubuntu hardy & firefox 3.0.3 "can't compose my mail on Hotmail" 

But i find a fine solution... :)
:confused: I think the problem is that M$ only want to work with Windows OS.

First step is to install "User Agent Switcher" Firefox extension.

Second step is to go to "tools/User Agent Switcher/Options" 

User Agent Strings/add

Description : Windows XP firefox 3.0.3
User Agent : Mozilla/5.0 (Windows; U; Windows NT 5.1; fr; rv:1.9.0.3) Gecko/2008092417 Firefox/3.0.3
App Name: Netscape
App Version : 5.0 (Windows; fr)
PlateForm : Win32

Third step is to switch to this User Agent on Hotmail 

*** Be careful I'm a Frenchie, so "; fr" must be change on your system ***

Bye :lolflag:

---

### Post by ash303 on 2008-11-01
Yeah, the problem is that with new Hotmail, Microsoft included a check to see if you aren't using Windows (or at least a check to see if you are running Ubuntu).

The solution timwaters proposes works but you should not set the value of general.useragent.vendor to "Firefox" but instead empty it. Also, in most cases, this value will be reset every time you restart Firefox. That is because this setting is part of the default settings of Firefox, not of your personal preferences. To fix this, go to /usr/lib/firefox-3.0.3/defaults/preferences, then edit ubuntu-useragent.js (using sudo of course). Replace the line

```
pref ("general.useragent.vendor", "Ubuntu");
```

by

```
pref ("general.useragent.vendor", "");
```

and restart Firefox. Hotmail should work now.

---

### Post by smoqueur on 2008-11-01
Sorry Ash 3.0.3 but your solution does not work :(

I just try it, after removing User Agent Switcher, I update the file ... Nope !!! 

My solution is working without files updates, you can use it only with M$ servers, and use "Default" to other web sites...

Sorry :lolflag:

---

### Post by scouser73 on 2008-11-01
You could just use an email client which would circumvent the problems you are encountering.

---

### Post by larryfroot on 2008-11-01
Hello, outraged of Tunbridge Wells here.

I sudo gedit'ed ubuntu-useragent to find it was empty. Blank. So I slapped in the line suggested above anyways. Still Hotmail refuses to allow me any sort of meaningful relationship...Ah well, all things change, rather pathetic to think of it...microsoft are claiming a 'mixed source' vision of the future whilst showing no sign of easing up on the practices that make damn sure people will have no favours owed to them on their way down.

Forum rules forbid me from stating the depth of feeling I have on the matter, but bunjie-jumping and sewage farms feature in my ideal justice to be meted out to supposedly intelligent people. 

Goodbye Hotmail.

---

### Post by scouser73 on 2008-11-01
> Hello, outraged of Tunbridge Wells here.:lolflag:

---

### Post by ash303 on 2008-11-01
> **smoqueur said:**
> Sorry Ash 3.0.3 but your solution does not work :(Hmm, that's strange, for me it is working. But one way or the other, that these kinds of hacks or plugins are necessary is ridiculous. Hotmail should just work with any modern browser and OS, as should any website. I have been using hotmail for 7 years, but I will switch to gmail, which doesn't need these kinds of draconic measures.

---

### Post by mike555 on 2008-11-01
You could use Thunderbird mail with the webmail & hotmail add-on  .......

---

### Post by davidevan on 2008-11-04
Has anyone come up with a fix for this?

---

### Post by davidevan on 2008-11-05
I can't verify that this works but others seem to have been successful with this fix (it's been posted by others in this thread):

[http://ubuntuforums.org/showpost.php?p=6060869&postcount=9](http://ubuntuforums.org/showpost.php?p=6060869&postcount=9)

I will try this when I get home and report back.

---

### Post by vandorjw on 2008-11-05
> **timwaters said:**
> 
...
in firefox:
about:config
change the value for general.useragent.vendor from Ubuntu to Firefox, and restart.....


My value is Firefox/3.03

I will change that to Firefox and see what it does then.

Cheers - CC7
-------------------------------------------
This was the result.
Didn't fix nor break Firefox

---

### Post by arron on 2008-11-05
Damn MS....  I will be switching to Gmail i think...

anyhow, this does work, I had the same problem where i couldn't edit the emails:
in firefox: open "about:config"
then change the value for "general.useragent.vendor" from "Ubuntu" to "Firefox", and restart your pc.

For restart, I had to literally restart my pc, exiting Firefox and reopening it didn't work.

---

### Post by Bramo on 2008-11-06
the "about:config" fix worked for me. As stated previously don't put in 'Firefox' just remove 'Ubuntu'

Also, there was no need to restart I just opened another tab and could compose in the Hotmail rich text control.

This isn't a great solution and as it's my girlfriend who uses hotmail I'll try and come up with a 'neater' solution.

PLAN A -> get her to switch to gmail.

PLAN B -> mess round with the user agent switcher thing.

:( It took me 3 seconds to get onto plan B...

---

### Post by Jorge_C on 2008-11-06
I was having problems with the new hotmail and opera 9.62, too.

To solve them: Help->Check for updates 

It'll tell you that no updates are available if you're using the latest version, but AFAIK it updates the browser.js and hotmail will work again for you. At least it does for me.

---

### Post by Bramo on 2008-11-06
Actually plan be worked as posted earlier by the French guy.

My solution is:
- Install Firefox user agent switcher plugin.
- From Firefox, "Tools - User Agent Switcher - Options - Options"
- Click "Add"

Set up a new user agent as follows (this is basically the same as the earlier one from the french guy, but I changed the 'fr' to 'en' where appropriate:

Description: Windows XP - Firefox 3
User Agent: Mozilla/5.0 (Windows; U; Windows NT 5.1; en; rv:1.9.0.3) Gecko/2008092417 Firefox/3.0.3
App Name: Netscape
App Version: 5.0 (Windows; en)
Platform: Win32
Vendor:
Vendor Sub:

It seems to work fine. You need to reapply the agent each restart. It'll have to do I guess.

---

### Post by High Frequency on 2008-11-06
Thanks smoqueur!!! Your solution works for me.

Long live to Ubuntu and its people!!!

---

### Post by jamesstansell on 2008-11-08
> You need to reapply the agent each restart.

I haven't needed the user agent switcher for a couple of years, but if I recall correctly, you could configure it to switch automatically for certain websites ...

---

### Post by Grams79 on 2008-11-11
Microsoft is simply saying to everyone without Windows.
"F" "U"
I don't remember Hotmail being a Microsoft territory when it started.
So why are some of us forced to use Microsoft products to use Microsoft services?
Because people in this world have no control and give it ALL away.

HERE HERE UBUNTU COMMUNITY TO SAVE THE DAY! 

Thanks for the attempts to fix this silly problem everyone.
:guitar:

---

### Post by ozzyprv on 2008-11-11
Ash303's solution @ post #16 worked for me.
Thanks.

---

### Post by ousama on 2008-11-14
Hello Ash303, you solution worked well, i'll diffuse it in my Mother Language. Thank you

---

### Post by pablomme on 2008-11-14
Just for the record, you can also bypass this by installing the Windows version of Firefox under Wine. I use the latest Wine from [www.winehq.org](www.winehq.org) (now at 1.1.8 ), so I don't know if version 1.0.1 in the Ubuntu repositories will cope well.

Probably the user agent switcher is a cleaner solution. I'm all for ditching WL HoTMaiL, this is not the first time it breaks Linux compatibility, and it won't be the last.

---

### Post by sigurnjak on 2008-11-14
As a root go to /usr/lib/firefox-3.0.3/defaults/preferences and open and edit ubuntu-useragent.js In a line where it says Ubuntu put Firefox and save . Restart firefox and pray ! Now if someone could verify this !

here is link to my post

[http://ubuntuforums.org/showthread.php?t=982436](http://ubuntuforums.org/showthread.php?t=982436)

c if it helps !:)

---

### Post by Beezleblub on 2008-11-15
Thanks sigurnjak !

Worked for me, Still worked after Reboot. 

Cheers !

---

### Post by boblemur on 2008-11-16
This is not a linux problem....


This happens to me in...

linux:
firefox
iceweasel (baicly the same)

windows
google chrome
IE
firefox

its no and off... but its not only a linux thing... however it does seem to happen to linux more oftern... its an odd problem but its not our problem... its hotmails screwup, i would love the old one back but i dont think you can...

if you log out and in again this may help :S or try a different browser, like opra maybe....

this is odd :S because you all seem to be linux related problems, but iv had this prob in windows firefox even IE... strange

---

### Post by amrlinuxroot on 2010-07-17
hallo i had prb with you tube and hotmail only i was see hotmail blank and i  cant acsess my mail as any way i fix this prb and i can say how y can fix same prb add google dns to your confiure

o try it out:

    * Configure your network settings to use the IP addresses 8.8.8.8 and 8.8.4.4 as your DNS servers or
    * Read our configuration instructions.

---

