---
title: "possible permanent fix for hotmail"
date: 2008-11-14
forum: General Help
---

### Post by sigurnjak on 2008-11-14
As a root go to /usr/lib/firefox-3.0.3/defaults/preferences and open and edit ubuntu-useragent.js  In a line where it says Ubuntu put Firefox and save . Restart firefox and pray ! Now if someone could  verify this  !

---

### Post by jakob.g on 2008-11-15
fix confirmed, works here. thanks!

---

### Post by sigurnjak on 2008-11-15
You are welcome ! Now we will have to see how long it will hold!:)

---

### Post by PocketDog on 2008-11-15
Yeah, edit the same thing from inside Firefox by typing **about:config** into the address bar, and editing the 'Ubuntu' user agent from there, no need for root.

---

### Post by sigurnjak on 2008-11-15
For some reason about:config changes to that particular modification would not stick after restarting firefox on my system  so i had to find an alternative way to accomplish same .Any other change worked fine.

---

### Post by GuruX on 2008-11-17
Works for me aswell. What would be the same solution for Opera?

---

### Post by sigurnjak on 2008-11-18
I really do not know . i do not use opera , in my experience it is still too buggy and there is no easy way to migrate  all of my settings from firefox . 

Also an update ! I just updated to firefox 3.04 and had to make same change to it in a newly created folder! 
/usr/lib/firefox-3.0.4/defaults/preference

[http://ubuntuforums.org/showthread.php?t=982436](http://ubuntuforums.org/showthread.php?t=982436)

As a root go to /usr/lib/firefox-3.0.4/defaults/preferences and open and edit ubuntu-useragent.js In a line where it says Ubuntu put Firefox and save

---

### Post by SamNSane on 2008-11-18
I've been watching threads like this one, and fuming at Hotmail, for a little while. Going into about:config and changing the general.useragent.vendor to "Firefox" worked for me, but I reverted to the default because I wanted to see if Microsoft was going to straighten this out. (I understand they've received "comments" on this issue.)

Following the update to Firefox 3.0.4 in Hardy I returned to Hotmail and logged in. Interestingly, I was taken right to my account instead of being shown the suggested upgrades page. When I went into about:config I still saw Ubuntu listed in general.useragent.vendor.

Does this mean that the folks running Hotmail finally pulled their head out?

---

### Post by sigurnjak on 2008-11-18
Really i do not know !As for me i had to make change because forwarding and some other things  would not work .

---

### Post by jweaver28 on 2008-11-20
Thanks, sigurnjak & Ehaunu (? the thread's getting so long and my memory so short!). I use hotmail for newsletters, required rebate addresses, etc. About a week ago, about a week after the forced upgrade to Live!, I noticed I wasn't able to send emails through firefox on my ubuntu boot, but was able to on the Vista boot. Queerly, I wasn't able to read my inbox (or anything in it) in Opera on the Vista boot, but was able to do so on the Ubuntu boot. 

I had noticed the useragent settings change hint after a google search, but it seems it has to be redone after every firefox upgrade (like last night's from 3.0.3 to 3.0.4) because Ubuntu's package insists on identifying itself as ubuntu rather than firefox. And I'm enough of a newbie or noob to appreciate a reminder to use the exact file to be changed as well as to use the sudo nautilus method instead of the file browser route!  

Anyway, I don't want to get caught in, much less burned by the flame war between Microsoft and Linux, which this thread seems headed toward. Sometimes it seems like a lot of guys posturing, which I don't need....

FYI, Hotmail hasn't responded to my feedback--and even their feedback choice process seemed convoluted, which displeased me. Of course, they may be shooting themselves in the foot by being so heavy-handed in promoting the use of Microsoft products (and they might well hate opera for the European litigation). Or it might simply be a low-level left hand not knowing what the right hand is doing.

---

### Post by PocketDog on 2008-11-20
Microsoft are on extremely shaky ground here; especially in Europe. Remember Netscape? Forcing a user to use a specific (expensive) vendor to access a public (free) service is almost certainly illegal.

---

### Post by SamNSane on 2008-11-20
I wouldn't interpret anything that's happening with Hotmail as any deliberate attempt by Microsoft to do any skullduggery. It's more like they're simply not aware of (or very concerned about) issues like this. All people who run large, commercial Web sites of any kind are constantly trying to gather data on what type and version of browser and OS are being run on the systems that access the sites. That helps them tailor the sites for the end users.

I don't think they want to control what browser you use so much as they want to be sure you can see "the pretty". They set the system up to look for given browsers with given capabilities so that the scripts will work for them -- you know, so that we can see the pretty cherry blossoms or whatever because that's so important to us when we want our e-mail!

;)

Anyway, when such a system gets any reply other than those that the Web designers accounted for (IE7/FF3) when designing for the ability to display the new eye candy, it just comes up with the message about needing to upgrade your browser. I doubt that they were thinking about deliberately defeating people who run Firefox under Ubuntu. It was the Ubuntu folks who decided to stick "Ubuntu" and "hardy" or "intrepid" in the config. Microsoft doesn't stick "Microsoft" or "Windows Vista" in the same place when Firefox is installed under Windows.

The changes the various sites are making in their visuals as they compete with each other have also been breaking Webmail extensions for Thunderbird at Yahoo, Gmail, and Hotmail off and on for months now. Again, probably not intentional.

If it is intentional, or even if it isn't intentional but persists, they'll lose some business.

---

