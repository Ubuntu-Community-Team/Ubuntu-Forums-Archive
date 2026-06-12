---
title: "Windows Live Hotmail not supported for Linux"
date: 2008-11-18
forum: General Help
---

### Post by ehsanul on 2008-11-18
Hotmail just upgraded to a new, better looking and neater version. However, I haven't been able to compose email messages after this upgrade, the message area just doesn't let me click it and type.

After I contacted their support team, this is the email I got back:

______________________________________________________________________

[COLOR="Blue"]Hello Ehsanul,
 
 
Thank you for writing back to Windows Live Hotmail Technical Support. This is Kristian and I gather that you are unable to compose an e-mail message or attach anything. I apologize for any inconvenience this may have caused.
         
Upon checking the information that you have provided us, we have noticed that you are using Linux to access Windows Live Hotmail. I regret to inform you that Linux is not currently a supported operating system of Windows Live Hotmail. This is the reason why you are encountering issues. In the meantime, I suggest that you use another computer with a different operating system to access your account. 
                  
We appreciate your continued support as we strive to provide you with the highest quality service available. Thank you for using Windows Live Hotmail.
 
 
Sincerely,
 
 
Kristian R.
Windows Live Hotmail Technical Support[/COLOR]
______________________________________________________________________


I just find it very hard to believe that Linux wouldn't be supported in an email service. I'd change, but my Hotmail address has been my main account for years. I'm sure someone else has had this problem, are there any workarounds? Thanks in advance!

---

### Post by amauk on 2008-11-18
what about installing a user agent switcher in firefox
(pretend you're using IE on Windows)

does that work?

---

### Post by brokenreality on 2008-11-18
I know that Mepis users are able to use Hotmail under linux, [http://mepislovers.org/forums/showthread.php?t=18227&highlight=hotmail](http://mepislovers.org/forums/showthread.php?t=18227&highlight=hotmail)  They might be able to help some.

---

### Post by cpetercarter on 2008-11-18
If it is possible to solve the problem simply by changing the Firefox user agent setting, then it suggests that it would be a trivial matter for Microsoft to support Linux in Hotmailin the first place.

---

### Post by ehsanul on 2008-11-18
Sweet, I just looked up the add-on, and it seems that it has worked for others, so I'll try it now. 

Here's what someone said:

[COLOR="Blue"]"In order to get it working it helps to clear your cookies, after doing so I was able to get Hotmail (which was recently, maliciously "upgraded" to break when run under Linux) to work. 5 stars, very useful!"[/COLOR]


If this is the case, then this is pretty damn low and dirty of Hotmail. I'm going to write back to their support team and complain.

---

### Post by brokenreality on 2008-11-18
> **ehsanul said:**
> Sweet, I just looked up the add-on, and it seems that it has worked for others, so I'll try it now. 

Here's what someone said:

[COLOR="Blue"]"In order to get it working it helps to clear your cookies, after doing so I was able to get Hotmail (which was recently, maliciously "upgraded" to break when run under Linux) to work. 5 stars, very useful!"[/COLOR]


If this is the case, then this is pretty damn low and dirty of Hotmail. I'm going to write back to their support team and complain.

Yeah you should defiantly email them back, but leave out how you did it, lol!!

---

### Post by ehsanul on 2008-11-18
Ok, it might have worked for that guy, but I'm still stuck with the same problem. I can confirm that the add-on is working, and I tried clearing cookies and cache, but it didn't do the trick. Any other ideas?

---

### Post by amauk on 2008-11-18
in Firefox, enter "about:config" in the address bar
this gets you into the internal settings

Change "general.useragent.vendor" from "Ubuntu" to "Firefox"

again,
clear cookies & cache, and retry

---

### Post by ehsanul on 2008-11-18
Thanks a lot amauk, that worked like a charm!

Damn, Windows is f***ed up for doing this...

---

### Post by ehsanul on 2008-11-18
My reply to the Windows Live Hotmail Support:

[COLOR="Blue"]
Dear Kristian R,

I'm very disappointed in the Hotmail team for doing this. I know for a fact now that this is not a compatibility issue, but that this has been put in place by the Hotmail team on purpose so that Hotmail would not work on Linux. Hotmail actually looks up the operating system being used, and if it's Linux, it breaks itself on purpose.

This is very low and dirty of Hotmail to do, and obviously an effect of being bought by Microsoft. If they want to get rid of Linux users using their email service, they should just be frank about it instead of acting like it's "not supported" for Linux (as if that is possible). Not all of us are stupid enough to fall for that. And if you really were sincere in your reply and were aware of this, then you would have told me the truth and maybe even provided me a workaround, instead of vaguely saying that "Linux is not currently a supported operating system of Windows Live Hotmail".

Sincerely,
Ehsanul[/COLOR]

---

### Post by mattiastbs on 2008-11-18
The "general.useragent.vendor" trick worked like a charm.. :)

I really hate microsoft for doing things like this..

//Mattias in Sweden

---

### Post by scouser73 on 2008-11-18
As an alternative to using a different PC as Microsoft say, you could try User Agent Switching; [http://johnbokma.com/mexit/2004/04/24/changinguseragent.html]("http://johnbokma.com/mexit/2004/04/24/changinguseragent.html")

There are a few threads in the forum about Hotmail, and people have posted the same solutions.

---

### Post by 3rdalbum on 2008-11-18
Wait a sec. I'm using Flock 2 on Ubuntu 8.10 (it's basically Firefox 3 underneath), and I just successfully sent an e-mail message from within Hotmail. 

EDIT: Replicated the problem on Firefox 3, and User Agent Switcher fixed the problem. WTF is going on? Flock doesn't give me the "Unsupported browser" message either. I wonder what Flock is identifying itself as?

---

### Post by RavanH on 2008-11-18
> **3rdalbum said:**
> Wait a sec. I'm using Flock 2 on Ubuntu 8.10 (it's basically Firefox 3 underneath), and I just successfully sent an e-mail message from within Hotmail. 

EDIT: Replicated the problem on Firefox 3, and User Agent Switcher fixed the problem. WTF is going on? Flock doesn't give me the "Unsupported browser" message either. I wonder what Flock is identifying itself as?

It is completely due to the setting general.useragent.vendor under about:config ... if it is Ubuntu, Hotmail blocks you off. If it is anything else (or blank) you will be fine. 

They seem to have something against Ubuntu. I wonder why ;)

---

### Post by Dark Angel on 2008-11-18
I regret to say it, but I don't think it's Hotmail's fault.  Someone decided to set the user agent name to "Ubuntu" instead of "Firefox".  The latter works fine, the former does not.  The Hotmail site grinds to a halt if it receives ANY invalid info there (blank is valid I believe).
Does this mean that someone at Ubuntu doesn't want us using Hotmail or they just didn't consider that this would matter?  I'm happy to stick with the latter, but it would be nice if the setting could be put back to normal.

---

### Post by hyper_ch on 2008-11-18
useragent != useragent.vendor ;)

They block linux on purpose.

---

### Post by scouser73 on 2008-11-18
Is there any reason why you don't use an email client for Hotmail?

---

### Post by hyper_ch on 2008-11-18
> **scouser73 said:**
> Is there any reason why you don't use an email client for Hotmail?

I'm sure there is :)

---

### Post by greenfrog on 2008-11-18
After you change about:config how do you get it to save?

Mine keeps defaulting to Ubuntu.

Thanks

---

### Post by philinux on 2008-11-18
I use Thunderbird with the Webmail/Hotmail addon. Works a treat. This way i don't have to visit their site very often.

[http://webmail.mozdev.org/installation.html](http://webmail.mozdev.org/installation.html)

---

### Post by philinux on 2008-11-18
> **greenfrog said:**
> After you change about:config how do you get it to save?

Mine keeps defaulting to Ubuntu.

Thanks

It doesn't save it reverts back to ubuntu when you restart firefox.
[https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/295176](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/295176)
Please feel free to comment.

---

### Post by amauk on 2008-11-18
I know it's a hassle to switch email providers
but this sort of behaviour is not acceptable

it's obvious they are intentionally blocking Ubuntu users

Do you really want an email provider that disrupts it's own service on a whim just because they can?

It's Microsoft's service, they set the rules
I say comply with their obvious wishes, and ditch their service

---

### Post by philinux on 2008-11-18
To be honest this is minor. All you have to do is click **continue** at the "upgrade your browser screen".
Someone made a mistake with branding. The general vendor should be firefox and not ubuntu

---

### Post by philinux on 2008-11-18
This fixes it for good. Without sudo :lolflag:
[http://ubuntuforums.org/showthread.php?t=961051](http://ubuntuforums.org/showthread.php?t=961051)

---

### Post by riahc3 on 2008-11-18
Im on Ubuntu 8.10 and Firefox as well and it works perfect for me....

I think its another issue.

---

### Post by sdowney717 on 2008-11-18
```
After you change about:config how do you get it to save?

Mine keeps defaulting to Ubuntu.

Thanks
```

you might need to delete your old firefox profile stored in folder .mozilla 

rename it to mozilla.old restart and you will get a new one.
Export your bookmarks so you can restore these into the new profile.

It also happened to me, I could not get it to hold the change.

---

### Post by sdowney717 on 2008-11-18
Well linux is the enemy so you cant really expect them to support it.
And you can expect them to perhaps actively work against it.

```
Hello Ehsanul,


Thank you for writing back to Windows Live Hotmail Technical Support. This is Kristian and I gather that you are unable to compose an e-mail message or attach anything. I apologize for any inconvenience this may have caused.

Upon checking the information that you have provided us, we have noticed that you are using Linux to access Windows Live Hotmail. I regret to inform you that Linux is not currently a supported operating system of Windows Live Hotmail. This is the reason why you are encountering issues. In the meantime, I suggest that you use another computer with a different operating system to access your account.

We appreciate your continued support as we strive to provide you with the highest quality service available. Thank you for using Windows Live Hotmail.


Sincerely,


Kristian R.
Windows Live Hotmail Technical Support
```

---

### Post by philinux on 2008-11-18
> **sdowney717 said:**
> ```
After you change about:config how do you get it to save?

Mine keeps defaulting to Ubuntu.

Thanks
```you might need to delete your old firefox profile stored in folder .mozilla 

rename it to mozilla.old restart and you will get a new one.
Export your bookmarks so you can restore these into the new profile.

It also happened to me, I could not get it to hold the change.
See post #24

---

### Post by timcredible on 2008-11-18
the only real solution is to not use a microsoft product for your email (do you really think microsoft will let linux users continue to use hotmail?).  get another account somewhere, doesn't matter where, gmail, yahoo, whatever, then go find a windows pc, log into hotmail and forward all your email to your new account, that way you still get all your hotmail mail, but never have to use hotmail.

---

### Post by RavanH on 2008-11-18
> **timcredible said:**
> the only real solution is to not use a microsoft product for your email (do you really think microsoft will let linux users continue to use hotmail?).  get another account somewhere, doesn't matter where, gmail, yahoo, whatever, then go find a windows pc, log into hotmail and forward all your email to your new account, that way you still get all your hotmail mail, but never have to use hotmail.

HAHA !! But then you did not count on the evil genius that M$ really is !! You cannot forward incoming messages from you hotmail account to another acount anymore... only if ... if ... if that other account is a ... yes ? HOTMAIL acount ! HAHA !! :evil:

(at least this is the case in my hotmail account that i wanted to forward to my o so enjoyed gmail)

Anyway, does MS Hotmail have a grudge against Linux / Ubuntu ? Well... I repeat the case:

**There is only one setting that will make the difference. It is that *useragent.vendor* that can be "Firefox" or empty but if it is "Ubuntu" (or Debian, OpenSUSE or ...) you will get blocked. And not only with that annoying message at login which you can pass but also when wanting to write a mail, you cannot do it. The javascript RTE is dead and to toggle to plain text you need ... javascript !! Nice catch22. Well thought through! :twisted:**

Is this not obvious? Still think it is unintentional or because they did not 'test' on Ubuntu Firefox but did test on any other linux distro ? 

I have solved this by installing the User Agent Switcher addon. I did not want to reset the *useragent.vendor* setting permanently because I think Ubuntu deserves the credit (at least in those visitor counter logs: Hurray for Ubuntu = Small step for man, giant crash for Windows!). 
Next I defined a new useragent under **Tools > User Agent Switcher > Options > Options > User Agent** where I set 
```
Name: Firefox for Hotmail
Useragent: Mozilla/5.0 (X11; U; Linux; nl-NL; rv:1.9.0.3) Gecko/2008101315 Firefox/3.0.3
```
The rest of the settings are unimportant. Then saved.

Now I mainly use the webmail plugin for Thunderbird to get my daily hotmail and there are tools to give access to Evolution too (search for hotway or hotwayd, better: use the link in my sig) but for those instances where I need to access hotmail via the web, I use the Firefox for Hotmail settings. This way I do not disguise my OS and browser to IE/Windows or anything and still get full access. Besides, when masking as IE/XP, Hotmail does not work really well at all on my 64bit setup. Furthermore I actually WANT them to see that I am one of those that is fed up with OS lockups and security issues all the time.

---

### Post by Dark9204 on 2008-11-18
Microsoft has gone too far, This is not acceptable!

It is clear that Microsoft are doing this on purpose, because it accepts anything but ubuntu under vendor!

As fast as i noticed this I switched to Gmail.

A big FU*K YOU TO MICROSOFT!

---

### Post by Sweet Spot on 2008-11-18
Has anybody Dug this yet ?  This info needs to be publicized in order to expose MS for being the pricks they really are. Where else should this be posted ?

---

### Post by PatrickVogeli on 2008-11-18
I don't get why anyone would like to use a hotmail account. There are lots of email providers which are far better than hotmail and don't have any problems with any os.

What's so speciall in hotmail that you can't change it?

---

### Post by ehsanul on 2008-11-18
> **philinux said:**
> To be honest this is minor. All you have to do is click **continue** at the "upgrade your browser screen".
Someone made a mistake with branding. The general vendor should be firefox and not ubuntu

If that was it, I would not have posted here for help. That was not the issue, I've had that problem for a long time and barely cared, since it's just a single click. 

The problem, if you read my post again, was the composing emails was not working, nor was attaching files. Basically, you could only send blank emails, with some subject, but no actual message. That is NOT minor, and it is not like the useragent.vendor setting would just make that break on its own (though I can't be sure). It seems more like Hotmail checking what it is, and breaking if it is "Ubuntu" or something, crazy as that sounds...

Even if it is the case that it just breaks cos of some error, the support team tried to make it look like a compatibility issue with Linux, which is pure ********.

---

### Post by ehsanul on 2008-11-18
> **riahc3 said:**
> Im on Ubuntu 8.10 and Firefox as well and it works perfect for me....

I think its another issue.

Different distributions vary, I'm on Ubuntu 8.04. It may be that the default useragent.vendor setting for Firefox isn't set to "Ubuntu" on your box. In any case, even if the case isn't Hotmail actively working against Linux users, the fact still remains that their support tried to make it look like the new Hotmail wasn't compatible with Linux, as if that makes any sense. That's pretty messed up.

---

### Post by ehsanul on 2008-11-18
> **Sweet Spot said:**
> Has anybody Dug this yet ?  This info needs to be publicized in order to expose MS for being the pricks they really are. Where else should this be posted ?

Here you go:  [Microsoft breaks Hotmail for Linux users]("http://digg.com/linux_unix/Microsoft_breaks_Hotmail_for_Linux_users")

Seems like a lot of people didn't get it and buried the article.

---

### Post by ehsanul on 2008-11-18
> **PatrickVogeli said:**
> I don't get why anyone would like to use a hotmail account. There are lots of email providers which are far better than hotmail and don't have any problems with any os.

What's so speciall in hotmail that you can't change it?

Well, it was my first account, and everyone knows it as my primary email address... It's pretty hard to change, especially when you've given your email out to potential employers as well as your friends, relatives and others.

---

### Post by ehsanul on 2008-11-18
If anyone's interested, I have here the latest reply from the Windows Live Hotmail Support Team:

[COLOR="Blue"]

Hello Ehsanul,
 
 
Thank you for writing back to Windows Live Hotmail Technical Support. This is Tyrone Rodney and I understand that you are having an issue using your Windows Live Hotmail account with Linux.

I appreciate your taking the time to send us your thoughts and suggestions about Windows Live Hotmail. We take feedback about Windows Live Hotmail product and service very seriously. It is through your comments and suggestions that we are able to know what our customers truly want. Although we are unable to take action on your comment immediately, rest assured that we are committed in upgrading the Windows Live Hotmail system to improve our service to you. You can expect to see many improvements in the near future.

You are valuable at Windows Live and we look forward to provide you with consistent and effective service. We appreciate your input and involvement in our Windows Live products.
 
 
Sincerely,
 
 
Tyrone Rodney
Windows Live Hotmail Technical Support
[/COLOR]

 


[COLOR="Green"]
--- Original Message ---
From : "Ehsanul Hoque"
Sent : Tuesday, November 18, 2008 7:55:34 AM UTC
To : "webcs.wlhm.00.00.en.syk.mnl.ts.t01.spt.00.em@css.one.microsoft.com"
Subject : RE: SRX1084734446ID - Windows Live Hotmail:Sending and receiving e-m:Writing and composing e-m

Dear Kristian R,

I'm very disappointed in the Hotmail team for doing this. I know for a fact now that this is not a compatibility issue, but that this has been put in place by the Hotmail team on purpose so that Hotmail would not work on Linux. Hotmail actually looks up the operating system being used, and if it's Linux, it breaks itself on purpose.

This is very low and dirty of Hotmail to do, and obviously an effect of being bought by Microsoft. If they want to get rid of Linux users using their email service, they should just be frank about it instead of acting like it's "not supported" for Linux (as if that is possible). Not all of us are stupid enough to fall for that. And if you really were sincere in your reply and were aware of this, then you would have told me the truth and maybe even provided me a workaround, instead of vaguely saying that "Linux is not currently a supported operating system of Windows Live Hotmail".

Sincerely,
Ehsanul[/COLOR]

---

### Post by Orographic on 2008-11-18
I wouldn't be as heated in any contact with Hotmail as the above post but its certainly worth dropping an email to them about it.

And for those that may not know it yet, Opera will run fine in Hotmail. I have it downloaded to access a IE only site that couldn't be accessed via the user agent switcher add-on approach.

I've now changed the general.useragent.vendor setting to 'Firefox' via 'about:config' and even after reboot it seems to work fine.

My question is, does changing it to Firefox cause any problems for general browsing?

---

### Post by hyper_ch on 2008-11-19
> **ehsanul said:**
> Well, it was my first account, and everyone knows it as my primary email address... It's pretty hard to change, especially when you've given your email out to potential employers as well as your friends, relatives and others.
Just setup an auto-forwarded and forwarded it all to your new email provider.

> **ehsanul said:**
> If anyone's interested, I have here the latest reply from the Windows Live Hotmail Support Team:[...]
It's just the usual marketing ******** of someone who has no clue what you're talking about...

---

### Post by ehsanul on 2008-11-19
> **hyper_ch said:**
> Just setup an auto-forwarded and forwarded it all to your new email provider.


It's just the usual marketing ******** of someone who has no clue what you're talking about...

Hotmail doesn't allow forwarding to other email providers...

---

### Post by hyper_ch on 2008-11-19
doest it allow auto-responders?

---

### Post by ken_do_san on 2008-11-19
I installed Flock browser, built on Firefox, but Hotmail doesn't post up the update your browser when I use it to log in, it just goes straight through to the inbox.  I can edit emails and write them as well now, no idea why Flock works and Firefox doesn't.

---

### Post by digitalbrain on 2008-11-19
> **Orographic said:**
> 

I've now changed the general.useragent.vendor setting to 'Firefox' via 'about:config' and even after reboot it seems to work fine.

My question is, does changing it to Firefox cause any problems for general browsing?

I don't think it causes any problems. When you change the vendor line, web sites won't get the information that you are using ubuntu, that's all I suppose. Just try it with some sites before and after changing this line (e.g. [www.ipaddresslocation.org](www.ipaddresslocation.org)). Anyway, I can't understand what microsoft is trying to do really. This is very interesting. Whether they are doing this on purpose or not, they will begin to lose some of their hotmail users. That's clear.

---

### Post by philinux on 2008-11-19
Causes no problems whatsoever here.

---

### Post by Sponzenbroekske on 2008-11-19
ESHANUL you didn't ask for a free copy of windows (vista) to access your hotmail account :p, they said "use another computer with windows on it", that is a nice workaround IF they give us another computer and a legal copy of windows and pay us for the extra time we spend starting up that ****. Windows users pay hundreds of euros/dollars to get an O/S (I did not say decent), and when they use FF they still need to mask it as IE, else they won't get on hotmail either. I don't mind paying for software or hardware or whatever but this is just lame. How come that linux can be bought at a reasonable price or even get freely and MS asks you for, I don't minimum 250 euros?
SHAME ON YOU MICROSOFT!!
To which mail address did you sent your complaint?

---

### Post by philinux on 2008-11-19
> **ken_do_san said:**
> I installed Flock browser, built on Firefox, but Hotmail doesn't post up the update your browser when I use it to log in, it just goes straight through to the inbox.  I can edit emails and write them as well now, no idea why Flock works and Firefox doesn't.

Check the general.useragent.vendor string it's using.

---

### Post by Sweet Spot on 2008-11-19
I used an Hotmail account for spam/junk and forum, account sign up stuff. However, I just closed the account and sent them a very informative feedback letter. They're services are NOT needed, period.

---

### Post by sigurnjak on 2008-11-19
Here is a link with my  fix !

[http://ubuntuforums.org/showthread.php?t=982436](http://ubuntuforums.org/showthread.php?t=982436)

So far all is fine even after few reboots. 

Hope it works for you guys !:)

---

### Post by RavanH on 2008-11-22
> **Orographic said:**
> I wouldn't be as heated in any contact with Hotmail as the above post but its certainly worth dropping an email to them about it.

And for those that may not know it yet, Opera will run fine in Hotmail. I have it downloaded to access a IE only site that couldn't be accessed via the user agent switcher add-on approach.

I've now changed the general.useragent.vendor setting to 'Firefox' via 'about:config' and even after reboot it seems to work fine.

My question is, does changing it to Firefox cause any problems for general browsing?

There should be no problem what so ever. It is just that Ubuntu will not ber recognized as the OS flavour you are using. One less point for Ubuntu in visitor stats on websites, that is all... 

No big deal but if you are happy about using Ubuntu, it is worth keeping at least THAT in your useragent specs ;) That is why I prefer using the User Agent Switcher and switch only for accessing my Hotmail (which I do rarely anyway).

---

### Post by SnakeHips on 2009-01-20
> **dark9204 said:**
> microsoft has gone too far, this is not acceptable!

It is clear that microsoft are doing this on purpose, because it accepts anything but ubuntu under vendor!

As fast as i noticed this i switched to gmail.

A big fu*k you to microsoft!

+1

---

### Post by hyper_ch on 2009-01-20
I found out today how I can forward incoming hotmail to other email accounts (also non-hotmail/msn/live ones). If someone's interested I could write a little howto.

---

### Post by SnakeHips on 2009-01-20
> **hyper_ch said:**
> I found out today how I can forward incoming hotmail to other email accounts (also non-hotmail/msn/live ones). If someone's interested I could write a little howto.

I guess i'd like to *zip* my hotmail stuff (folders/sddress book etc) and forward that to my new gmail - i'm totally shot of MS$ now ,but yeah a little howto wont go a miss.

cheers.

edit:
Export contacts thus:
contact list /manage /export (as .csv file)

---

### Post by SnakeHips on 2009-01-22
> **hyper_ch said:**
> I found out today how I can forward incoming hotmail to other email accounts (also non-hotmail/msn/live ones). If someone's interested I could write a little howto.

I found the easiest workaround to this was to set hotmail "on vacation" thats where they're goin forever - afterall lol) and included a message in my signature with new email addy and done the same with "reply-to".

One thing i've not worked out is how to export all the existing mail/folder's. I tried the "evolution" and "thunderbird" workarounds but it's a no go unless I cough up $20 for web-dev access :-(

---

### Post by Sprut1 on 2009-01-22
Well this is just Microsoft being Microsoft, they just make up their own laws.

I never cared for hotmail though as it sucks :)

---

### Post by hyper_ch on 2009-01-26
I published the howto now. Because I didn't know where to put it in here so I published it over at howtoforge:

[http://www.howtoforge.com/forwarding-hotmail-to-any-other-email-account](http://www.howtoforge.com/forwarding-hotmail-to-any-other-email-account)

---

### Post by daverich on 2009-01-26
it was for this reason i recently ditched my hotmail account and went over to google.

I think it's fair enough that they don't want linux users using their mail service.

Kind regards

Dave Rich.

---

### Post by -kg- on 2009-01-26
I can't figure it out.  I haven't done anything in Firefox to configure it, I've created new Hotmail accounts fairly recently, and I haven't had any of these problems.

To test it, I just logged into my Hotmail account and sent a test message to my sbcglobal account.  It worked perfectly, the message was there, and I even got the "recommendation to upgrade my browser message" and all, which I just bypassed.

I'm using Hardy and Firefox and am having no trouble whatsoever with Hotmail.  I can't figure it out.

Not that I'm a Micro$oft apologist or anything...I might just switch to Yahoo just for the principle of the thing, but I've had this Hotmail account forever.

---

### Post by RavanH on 2009-01-27
> **SnakeHips said:**
> I found the easiest workaround to this was to set hotmail "on vacation" thats where they're goin forever - afterall lol) and included a message in my signature with new email addy and done the same with "reply-to"...

Smart! Thanks for the tip :)

By the way, when I use Opera (excellent browser!) and set the site preferences (so only for the mail.live.com domain) to 'Mask as Internet Explorer' access to Hotmail poses no problem at all ;)

---

### Post by SnakeHips on 2009-01-31
> **RavanH said:**
> Smart! Thanks for the tip :)

By the way, when I use Opera (excellent browser!) and set the site preferences (so only for the mail.live.com domain) to 'Mask as Internet Explorer' access to Hotmail poses no problem at all ;)

Cool ,i'll take a look at that - thanks

---

### Post by luvmyMac on 2009-04-10
I rarely post to forums.  I just tried to open Hotmail (I use MAC OSX with Safari) and received a message that my Hotmail has no inbox; I was blocked from my Hotmail and it tried to force me sign up for Windows Live.  I did a Google search and found this forum, cleared my cookies, and was able to sign into Hotmail.

Just writing to say THANK YOU!

Because of this, I'm looking for a new email provider and a way to transfer all my folders to my new email.  If you know how, please share.  

I've had Hotmail "forever".  Do any of you have another email provider with lots of storage and good features that you like?

Thanks again for the Cookies tip!!

---

### Post by hyper_ch on 2009-04-10
why not host your own email?

---

### Post by luvmyMac on 2009-04-11
Because I'm somewhat technically-challenged, could you please explain how I host my own email?  Maybe you're talking about the Mail that came with my computer.  It's on my to-do list to figure out how to use it.  Also, I've somehow signed onto it at some point and have forgotten my password, so I can't access it.  I searched the Help menu but couldn't find anything on how to fix this.  Any or all advice appreciated :)  

Thanks for responding!

---

### Post by hyper_ch on 2009-04-11
with a lot of reading... also check out the server forum and [http://www.howtoforge.com](http://www.howtoforge.com)

---

### Post by callie510 on 2009-04-11
If you can access Hotmail mail with Thunderbird or any other mail client, you should be able to check it with Gmail! I have my Gmail set to receive mail from many email addresses (just to keep them all in one place). This can be extremely useful when migrating from another account, and also maintains the "from" correctly so you don't have to forward everything to yourself. Gmail is great! :) 

I will take a look at my settings to see if I can get Gmail to check a Hotmail account.

edit: It's easy!
Gmail -> Settings -> Accounts
Get Mail from Other Accounts -> Add Account you Own
Settings are pop3.live.com on port 995 and check SSL (it should fill these settings in automatically)
You can send mail as this account too if you set it up - it will leave people less confused if you appear to send "from" the same account they mail "to".

Anyways... dunno if this information was wanted, but it sure is useful.

---

### Post by luvmyMac on 2009-04-11
Thanks!  I think that my .Mac mail isn't working because you need a password from your ISP.  I may try phoning them and possibly Apple as well.  I also think that Apple may be charging for the service; it looks like it's part of a bundle of .Mac services costing $99 a year, so that may be why it's not working.  So I'll probably end up going with gmail or yahoo.

---

### Post by hyper_ch on 2009-04-11
well, hosting your own email would require a machine that is more or less 24/7 connected to the internet. Also a problem are dynamic ip addresses (and how often they change). Normal adsl here is about one new ip address every 24h. vdsl is about once a month.

If you have a static ip address then it's good to go.

If you don't have a static ip address you need (a) a tool that updates your ip and nameserver entries [there are free ones out there] (b) relay the outgoing mail through a real mail server as most mail servers reject incoming email from a dynamic ip.

It's not that difficult to setup.

---

### Post by luvmyMac on 2009-04-11
Thanks everyone!

I have a high-speed internet connection with cable and modem.  The IP address changes regularly; I'm not sure how often.  Is there a huge advantage to hosting your own email over using Gmail or Yahoo?  I can read about it, but I'd be scared of causing problems with my computer if I start doing something that I don't totally understand.  A lot of the technical talk in this forum goes over my head; my strengths are in other areas.

---

### Post by hyper_ch on 2009-04-11
the advantage is that you can do on the server everything you want it to be like... the disadvantage is you have to do everything on your own.

If you value your privacy you might want to run an own server.

---

### Post by hyper_ch on 2009-04-11
the advantage is that you can do on the server everything you want it to be like... the disadvantage is you have to do everything on your own.

If you value your privacy you might want to run an own server.

---

### Post by luvmyMac on 2009-04-13
Thanks for all the help!  I'll check out the HowtoForge website and the server forum.

---

### Post by lisati on 2009-04-13
I found out today (via another thread) how to get hotmail working in evolution (thunderbird should be similar). The details are as follows:

Incoming server: pop3.live.com
Username: [email]your_username@hotmail.com[/email]
Use secure connection: SSL
Authentication type: password

Outgoing server: smtp.live.com
Server requires authentication: yes
Security: SSL
Authentication: plain

[http://mailcall.spaces.live.com/Blog/cns!CC9301187A51FE33!44348.entry](http://mailcall.spaces.live.com/Blog/cns!CC9301187A51FE33!44348.entry)
Hope this helps.

---

