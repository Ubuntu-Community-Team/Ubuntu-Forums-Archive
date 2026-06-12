---
title: "Evolution and new Google Calendar CalDAV capability"
date: 2008-07-29
forum: General Help
---

### Post by ufugu on 2008-07-29
Yesterday Google announced [CalDAV support for Google Calendar]("http://www.google.com/support/calendar/bin/answer.py?answer=99355").

I'm looking forward to trying this out when I get home, but meanwhile I'm wondering if anyone else has used this new CalDAV capability to get successful bidirectional syncing between Evolution and Google Calendar?

(I know from the forums that quite a few people are eager for two way syncing with Google and disappointed that Evolution didn't deliver as promised in the last Gnome release.)

---

### Post by tamoneya on 2008-07-29
ive already got it integrated with thunderbird and it works great. ( i have an extension that integrates thunderbird with sunbird).

---

### Post by amoore on 2008-07-30
Anyone know how to get this to work with Evolution?

---

### Post by drjimmy42 on 2008-07-31
I tried adding the google dav url as a caldav calendar but it doesn't work.

Lifehacker 
[http://lifehacker.com/399407/how-to-sync-any-desktop-calendar-with-google-calendar](http://lifehacker.com/399407/how-to-sync-any-desktop-calendar-with-google-calendar)

says to use the url of the format

[https://www.google.com/calendar/dav/youremail@gmail.com/user](https://www.google.com/calendar/dav/youremail@gmail.com/user)
...replacing [email]youremail@gmail.com[/email] with your actual email address.

But every time I do that the calendar doesn't load, and I go back to the properties of the CalDav calendar in evo and it has replaced the https:// with caldav://.

Any other ways to do this?

---

### Post by ProfessorPain on 2008-07-31
I tried following the google config instructions in Evolution 2.22.3.1 on Hardy 8.04:

[http://www.google.com/support/calendar/bin/answer.py?answer=99358](http://www.google.com/support/calendar/bin/answer.py?answer=99358)

But when I enter the information and try to sync, it won't work. When I open the calendar's preferences, the URL has been really messed up and changes into something like this:

caldav://gmail.com@gmail.co@gmail.c@gmail.@gmail@gmai@gma@gm@g@@www.google.com/calendar/dav/my.full.name@gmail.com/user

Really weird! Anyone know how to make this work?

---

### Post by drjimmy42 on 2008-07-31
Looks like evo has problems with the @ in the url

[http://groups.google.com/group/linux.debian.bugs.dist/browse_thread/thread/dcdca662687449cd](http://groups.google.com/group/linux.debian.bugs.dist/browse_thread/thread/dcdca662687449cd)

---

### Post by motang on 2008-07-31
> **tamoneya said:**
> ive already got it integrated with thunderbird and it works great. ( i have an extension that integrates thunderbird with sunbird).
Good to know, I shall try this out at home. Thanks.

---

### Post by prince_niceguy on 2008-08-05
Not working in evolution... is anyone able to do this integration?

---

### Post by moore.bryan on 2008-09-11
anyone find a solution to this?

---

### Post by Teleyinex on 2008-12-04
I have the same described problem. I think we have to wait until Evolution team releases a patch ;)

---

### Post by Locke_99GS on 2008-12-08
Evolution 2.24 has built-in support for Google Calenders.

Select New Calender, mark type as "Google", fill in account name, (*not* full email address, only the part before the @) selecty which calendar you wish to import, enable SSL if you wish, and hit OK.

The calendar in the gnome-panel's calender applet will sync itself with whatever you have set up in Evolution, as well.

---

### Post by prince_niceguy on 2008-12-08
Is it a two way sync??? does it sync on startup or on regular interval?? 

I have it setup but I think it sync only on startup.

---

### Post by Locke_99GS on 2008-12-08
It should sync at given intervals.

---

### Post by shane2peru on 2008-12-09
I have tried using this and it seems buggy yet.  Still not 100% IMHO.  I think the sync-ing thing was a problem, perhaps I will try to find how to sync it less often, like once a day.  

Shane

---

### Post by hyper_ch on 2008-12-09
I have used this far GCalDaemon to sync Kontact with GoogleCal - if anyone needs a howto I have bookmarked serveral pages that got me up and running.

---

### Post by prince_niceguy on 2008-12-09
> **hyper_ch said:**
> I have used this far GCalDaemon to sync Kontact with GoogleCal - if anyone needs a howto I have bookmarked serveral pages that got me up and running.

can you please put those bookmarks as links here. I too would like to use that for syncing.

---

### Post by hyper_ch on 2008-12-09
basically this here [http://www.chipbennett.net/wordpress/index.php/2008/06/how-to-synchronize-google-calendar-with-kde-pim-part-2/](http://www.chipbennett.net/wordpress/index.php/2008/06/how-to-synchronize-google-calendar-with-kde-pim-part-2/)

and this here: [http://gcaldaemon.sourceforge.net/usage-b.html#offline](http://gcaldaemon.sourceforge.net/usage-b.html#offline)

and this here: [http://www.terminally-incoherent.com/blog/2007/10/11/howto-two-way-sync-between-kontact-and-gcal/](http://www.terminally-incoherent.com/blog/2007/10/11/howto-two-way-sync-between-kontact-and-gcal/)

it's all for kontact but should work on evolution also.

---

### Post by Locke_99GS on 2008-12-09
> **shane2peru said:**
> I have tried using this and it seems buggy yet.  Still not 100% IMHO.  I think the sync-ing thing was a problem, perhaps I will try to find how to sync it less often, like once a day.  

Shane

I can't seem to get more that a single Google Calendar working at a time. A little aggravating. I'm sure (read: hope)it will get sorted out soon enough.

---

### Post by shane2peru on 2008-12-09
> **Locke_99GS said:**
> I can't seem to get more that a single Google Calendar working at a time. A little aggravating. I'm sure (read: hope)it will get sorted out soon enough.

Yes, I think the devs are on the right track and going to get this thing working soon enough.

Shane

---

### Post by toocer on 2009-02-11
I dont get the google calender to work with evolution, it seams that all the apiontments are not shown ? does anyone have a solution for this ?

Sorry for my bad english :( i hope you understand

---

### Post by prince_niceguy on 2009-02-11
seems the best way to use gcaldaemon and use it.. you can google for it to integrate with google calendar ... to much of googling in this :-)

---

### Post by Brigrat on 2009-02-21
never got evo and gcaldaemon to play nice, but did get it to work with Thunder-chicken.  Will keep at it till I get it to go.  The embedded google calendar in EVO just does not seem to work as I can only get it to pull maybe 6-12 out of 45 plus appointments per month.  Thunderbird work but when it sync's it freezes up for about 10-15 seconds and then resumes.   Not crazy about that but at least it is keeping my calendar going.  If I get it to fly rest assured I will post everything here...  best of luck to all...

---

### Post by mlissner on 2009-02-21
Yeah, Evolution doesn't work. It just doesn't. Thunderbird works quite well though. I got it to work with Lightning 0.9 + Google Provider (an add-on). I don't have too much of a problem with lag, but I imagine YMMV.

---

### Post by kyouens on 2009-03-04
I can confirm I'm having the same issue with multiple Google calendars in evolution.  I can't add them via CalDav because of the @ symbol bug and I can't use the built-in Google sync because not all my events show up.  Also, it seems to crash randomly (and I mean randomly . . )  I'm using Thunderbird + Lightning + Zimbra plugin for contacts sync and everything's working great.

I've got to say that I've never had much of a good experience with Evolution.  It seems like with Evo it's not uncommon to have a major release with critical bugs in core functions.  I just wish there were a way to more tightly integrate Thunderbird and Lightning/Sunbird into the Gnome desktop.

---

### Post by Cuba71 on 2009-04-21
I'm running Evolution 2.26.1 with Jaunty and today I finally got my CalDav calendar to synchronize both ways with Google calendar, now I have to work on my XP machine to do the same thing with Outlook.
I spoke too soon, now my Evolution Calendar is not running at all.  Stay tunned.

---

### Post by mlissner on 2009-04-21
Yeah, I tested this briefly, and it didn't really work. Configuration is now easy and straightforward, but push/pull fails. Miserably. Still.

---

### Post by Cuba71 on 2009-04-21
The depressing thing is that after I got it to work like a charm, all of a sudden, as soon as I click on the calendar button, Evolution crashes.
I deleted and reinstalled Evolution with the same results.
Stay tunned

---

### Post by mlissner on 2009-04-21
You know, Thunderbird almost never crashes. Just sayin'.

---

### Post by Cuba71 on 2009-04-21
Well, 3 hours later, I got it to work again, this time I learned by my previous mistake and backed up the settings.
I'll try to write some instructions.
:P:P

---

### Post by tanari on 2009-04-23
oh man!! where is instructions, I can't wait :)

---

### Post by Cuba71 on 2009-04-23
I'm sorry, I started a new thread with the instructions.

Here's the link

**[Evolution/CalDAV]("http://ubuntuforums.org/showthread.php?t=1132446")**

---

### Post by GammaStream on 2009-04-26
Sorted it out today. To do it is very easy, in the calendar tab of evolution right click to add new calendar and select google as type. Input your details and away you go. Will see how stable it is with time.

---

### Post by righdforsa on 2009-05-05
Just got this working, and it is hot! Used the following for the setup:

url: caldav://www.google.com/calendar/dav/$user@gmail.com/events
use SSL: checked
username: $user@gmail.com

---

### Post by klicki on 2009-10-30
> **righdforsa said:**
> Just got this working, and it is hot! Used the following for the setup:

url: caldav://www.google.com/calendar/dav/$user@gmail.com/events
use SSL: checked
username: $user@gmail.com
Fine, I am at the same point! :) But now I am becoming greedy! :cool: I want to add some group calendar from Google. The idea is to replace the part $user@gmail.com in the URL by the name of the group calendar, e.g. **bund_6127_%48amburger+%53%56#sports@group.v.calendar.google.com** for the famous football team HSV! (You need to keep your own Google ID in username field.)

:shock: Unfortunately Evolution 2.26.1 cuts the URL at 60 chars which effectively destroys the access to the calendar. ](*,)
Who can make this work?
:confused:

---

### Post by mlissner on 2009-10-30
> 
Who can make this work?
:confused:

Thunderbird 3 is still in beta, but works. Highly recommend it, if you can.

---

### Post by Cuba71 on 2009-10-30
What's the correct addres for the calendar?

Never mind, I got it

---

### Post by klicki on 2009-11-03
> **mlissner said:**
> Thunderbird 3 is still in beta, but works. Highly recommend it, if you can.
I wanted to use Sunbird, but I learned that the project has been dropped. Since I am bound to another Email program than Tunderbird, I will rather dump Evolution calendar and use Google Calendar online instead.
:)

---

### Post by Cuba71 on 2009-11-03
> **klicki said:**
> I wanted to use Sunbird, but I learned that the project has been dropped. Since I am bound to another Email program than Tunderbird, I will rather dump Evolution calendar and use Google Calendar online instead.
:)

I added the Hamburger SV group calendar to my Google calendars to Evo.

Then I tried to follow the instructions contained [here]("https://help.ubuntu.com/community/GoogleCalendarWithEvolution") to add Google calendars.

The results were that for some unknown reason, the HSV calendar doesn't show in the drop-down list.

And I keep looking for an Evolution config file that holds all the info regarding calendars and can't find it.

Will continue looking

---

### Post by frncz on 2009-11-03
I got my googlecalendar working with Evo, by following the CALDAV instructions but all past events are marked : <copy protection enabled> and disappear from my outlook lists.

This is terrible as I need a record of past events!

Any solution?

Thanks 

Mike

---

### Post by Cuba71 on 2009-11-03
> **frncz said:**
> I got my googlecalendar working with Evo, by following the CALDAV instructions but all past events are marked : <copy protection enabled> and disappear from my outlook lists.

This is terrible as I need a record of past events!

Any solution?

Thanks 

Mike

I don't understand, I have my Google calendar and Evo set up since April, and I'm able to see all my events back to the first day

---

### Post by klicki on 2009-11-04
> **frncz said:**
> I got my googlecalendar working with Evo, by following the CALDAV instructions but all past events are marked : <copy protection enabled> and disappear from my outlook lists.

This is terrible as I need a record of past events!
You are using Outlook? Maybe that's the problem! :D

---

### Post by klicki on 2009-11-04
> **Cuba71 said:**
> I added the Hamburger SV group calendar to my Google calendars to Evo.Do you get HSV events in Evo?? I don't have a problem syncing my own private calendar events between Google and Evo, but doing the same with the HSV group calendar won't work due the cut-off of the URL after 60 chars.

---

### Post by Cuba71 on 2009-11-04
> **klicki said:**
> Do you get HSV events in Evo?? I don't have a problem syncing my own private calendar events between Google and Evo, but doing the same with the HSV group calendar won't work due the cut-off of the URL after 60 chars.

I added HSV to my Calendars in Google and I can see the events when I login to Google but HSV doesn't show in the drop-down list of Google Calendars in Evo

---

### Post by frncz on 2009-11-04
> **klicki said:**
> You are using Outlook? Maybe that's the problem! :D

Yes, my University uses Microsoft Exchange

---

### Post by klicki on 2009-11-05
> **Cuba71 said:**
> I added HSV to my Calendars in Google and I can see the events when I login to Google but HSV doesn't show in the drop-down list of Google Calendars in Evo
What I did: I added a new calendar to Evo, type caldav, with URL
```
caldav://www.google.com/calendar/dav/bund_6127_%48amburger+%53%56#sports@group.v.calendar.google.com/events
```After that I am filling in my Google user name. Having saved this, Evo is asking me for my Google password, but the new calendar never gets a checkmark, because it cannot be read from Google. If you check it's properties, the URL is cut in the middle. :(

---

