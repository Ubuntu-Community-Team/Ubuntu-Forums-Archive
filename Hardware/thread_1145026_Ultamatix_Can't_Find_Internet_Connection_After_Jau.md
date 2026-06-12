---
title: "Ultamatix Can't Find Internet Connection After Jaunty Upgrade - Any Ideas?"
date: 2009-05-01
forum: Hardware
---

### Post by OzzyFrank on 2009-05-01
Hi. After the upgrade to Jaunty 64-bit, **[COLOR="#4b0082"]Ultamatix[/COLOR]** can fire up, but when it searches for an internet connection, it finds none, and stops with the error message:

[B][COLOR="DarkRed"]Ultamatix :Alert![/COLOR]
[COLOR="Indigo"]Internet Disruption[/COLOR]
Please check that you are connected to the internet.
If you are connected and getting this message please try again later.[/B]

This happens without any other web activity, and of course I have tried a few times in case it really was something to do with the program having difficulties accessing the site and/or repos. I have even uninstalled it, downloaded the latest version, and installed it again, to no avail.

Has anyone else experienced this? Can anything be done about it? Thanks in advance.

Edit: Here is some output from trying to run Ultamatix via the terminal. First bit shows what is happening before the pause and subsequent connection failure:

**[COLOR="DarkRed"]check = os.popen3("ping getautomatix.com -c 1 -w 1");[/COLOR]**

... and what happens when it fails:

[B][COLOR="#8b0000"]--2009-05-01 23:27:55--  [http://www.getautomatix.com/files/example](http://www.getautomatix.com/files/example)
Resolving [www.getautomatix.com](www.getautomatix.com)... failed: Name or service not known.
wget: unable to resolve host address `[www.getautomatix.com](www.getautomatix.com)'[/COLOR][/B]

---

### Post by askopek on 2009-05-06
i am having the same problem, also on 64-bit jaunty.

---

### Post by mobiu5 on 2009-05-09
Having the same problem on the 32bit version of Jaunty.  Clean install too.

---

### Post by johnno56 on 2009-05-27
I am having the same problem. Only difference is, I am running with 8.04 Hardy.

Somehow, I do not think it is a "version related" problem. Is there any way to check the update log (if any) to see if there has been an update for Ultamatix? That would be the first place I would start looking. If so, maybe installing the previous version?

Regards

J

---

### Post by OzzyFrank on 2009-05-27
Hi Johnno - I think going backwards isn't an option, as since the days of Automatix I'm pretty sure I've had to get the latest version (manually) with each Ubuntu upgrade. There are a few apps that no longer work with each upgrade, and need to be downloaded and installed manually (don't ask me why they don't just make this easier by at least making it available through Synaptic), and I'm pretty sure Ultamatix is one of them. One day in the distant future they might even include apps like this in the upgrade (one can hope!).

Live long and prosper!

---

### Post by OzzyFrank on 2009-05-27
PS: Of course, even when it finally gets to the point Ultamatix and the like are just upgraded with the system without having to manually do so, one hopes the app can successfully connect to it's own motherloving web site! In this case it's [COLOR="DarkRed"]www.getautomatix.com[/COLOR] not [COLOR="Blue"]www.ultamatix.com[/COLOR], so I might see if I can contact the developer to point out the site the app needs to contact before it will even open is either fatally down or is not allowing access to Ultamatix.

---

### Post by OzzyFrank on 2009-06-09
I joined the Ultamatix forum (actually, the Ultimate Edition forum, which is the same thing) and seems the answer is that the repo is down. Still yet to receive and answer on when it is likely to be up again. Seems like one hell of a major ballsup to me, hehe.

---

### Post by mshtawythug on 2009-09-12
I have the exact same problem any one got the fix yet???

---

### Post by mshtawythug on 2009-09-12
i know that you have probably figured it out but this is for future resources 
i ve just found the solution go to 
[http://ultamatix.com/](http://ultamatix.com/)
download the latest version it works perfectly

---

### Post by OzzyFrank on 2009-09-12
Doesn't seem like anything is being done about it, as incredible as it sounds. At least people can still get all the multimedia codecs by installing [ubuntu-restricted-extras]("http://ubuntugenius.wordpress.com/2009/08/29/play-dvds-all-media-types-with-ubuntu-restricted-extras/").

---

### Post by OzzyFrank on 2009-09-12
Oh OK, well that's weird, if we are to believe the "repo is down", yet the latest version works but earlier ones don't. I did try that earlier, with no change, but now it looks like an uninstall then reinstall of the new version will correct things. I have to admit I actually wasn't all that fussed, but for newbies it makes things a lot easier (especially getting multimedia support), and for those who want all the stuff like Skype etc (that I don't). I'll have to give the new version a try later. Thanks for letting us know. Cheers

---

### Post by aysiu on 2009-09-12
If you're having trouble with Ultamatix, you can find support for it in the Ultamatix forum:
[http://forumubuntusoftware.info/viewforum.php?f=63](http://forumubuntusoftware.info/viewforum.php?f=63)

---

