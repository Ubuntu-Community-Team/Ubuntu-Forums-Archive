---
title: "Evolution, Thunderbird, Sync, Google Calendar, and so on"
date: 2008-11-17
forum: General Help
---

### Post by terribletrouble on 2008-11-17
I am not sure of the best location for this, rant, tips n tricks, developer coding, so general will do.

I am a business user, I have been using Ubuntu for 2 years now. I am in a complete corporate environment, and I struggle like mad, but I am very persistent and will do what ever I can to succeed. My two areas where most problems exist are:

[LIST]
[*]Mail/Calendar/Contacts, and keeping them in sync with a mobile device.
[*]Office documents.
[/LIST]

Clearly #1 is the trouble area. #2, seems to be taken care of with the recent addition of OO v3, available by adding the following to your rep: 
```

deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main

```

About 80% of the docs that I have opened in the new v3 seem to be good, although I am still seeing problems with headers/footers and so on. The issue is that colleagues email M$ Office 2007 docs around, without even thinking, and no one can go back to them and ask them to save the doc in a different format, and then send it onto you again. Anyhow, onto the main issue:

Before I get into the problems, we need to state what we wish to happen!

> 
Corporate users need a Mail, Contacts, Calendar application, that can be trusted (does not loose data...), which contains all possible fields (birthdays, spouse name, weight, you name it), that can be synchronized with a server (SyncML, Google Calendar,...?) and will handle updates, multi-language, different characters, code-pages, deletes, additions, modifications -- all the time, being trust-worthy!


I know what all of you are saying as you are reading this... Evolution and [Schedulworld]("http://www.scheduleworld.com"), maybe even Thunderbird and [Funambol]("http://www.funambol.com"). Well, nothing works!

Let me give you my most recent experience:

I have a Blackberry, so I sync, two-way, from Evolution to Scheduleworld, and my Blackberry picks it up. Well, the Funambol client on the Blackberry, will only only sync 1 month of past appointments, and 6 months of future appointments. Sounds great, the only problem is that my calendar contains lots of things from the past (need for expenses....) and the future, dentist, and so on. Once the Blackberry begins it's sync back to the Scheduleworld Server, all my calendar items outside the 7 month playing field, vanish into thin air!

Luckily, I have great backups, so quickly notice this, and revert back again.

Lets try something else, Evolution and Google Calendar, there is even a plugin for Google Calendar within Evolution. 

I start this, configure it, and I copy 2 weeks of appointments to my Google Calendar. Everything is looking great. There is a built in sync tool in google, to sync the Blackberry with the google calendar, all the meetings show up on my Blackberry, things are looking good. Back to Evolution, --and-- I can only see 2 days of appointments, and they are at the end of this week, seems quite random.

I decide to pull down the latest Evolution, 2.25.1, compile it, and give it a test, same problems.

I decide to Pull down Thunderbird & Lightning & Google Provider, give that a test. When someone sends me an invite, I cannot accept it into my Google Calendar, and in Thunderbird, there is no way to copy from a local calendar to the Google Calendar. You can save the message as an .ics file, then import it into the Google Calendar. So although I seem to have great access to my Google Calendar, it remains off limits to me!

I decide to give the Beta Thunderbird v3, a whirl, exactly the same.

I have investigated, Kontact, that seems like it has less support for Google Calendars.

I have tried Zimbra, both the client and the server - does not even come close.

The closest I think that I have come, is the following story I came across: [http://www.desktoplinux.com/news/NS9753307781.html]("http://www.desktoplinux.com/news/NS9753307781.html"). It links to PocketMac, which they say they are building a synchronize tool for Linux to Blackberry.

If you think that Windows Mobile (ala: HTC, Fuze, etc...) does any better, you are mistaken. The networking stack on Windows Mobile is so slow, that my 1800 contacts, take hours to sync over.

I did think for a second that maybe the T-Mobile G1 would solve.... forget it, out in the dark.

I don't know if anyone on the planet has actually managed to create a stable two-way synchronizing environment, that they wish to share, that can be trusted, like I remember from my days with Outlook, an Ipaq and Active Sync. Yes, I know it was slow and so on, but it did what I needed.

You will also note, I have not even mentioned contacts! Google contacts contain about a tenth of the fields that Outlook has, Evolution about two thirds, so as you embark on that area, you know you are going to loose data! All your birthdays, notes, vanish.

I actually cannot believe that something as fundamental as this, is not worked on more in the Linux community. 

> I often think, how does Mark Shuttleworth keep organized with his mobile device?

TT

---

### Post by Zaskoda on 2008-11-17
I second this. Tonight I'm trying to get my old palm to sync with Evolution and having problems. However, I'm not even sure why I'm trying. The goal is to connect everything to my google calendar. However, in my case, it seems that any *recurring* events on my google calendar do not show up at all on my evolution calendar. For me, this renders the solution useless.

In 8.04 I tried the thunderbird/sunbird solution with some other plugin that would sync with google calendar. It seemed to mostly work - it just crashed so often it wasn't worth using.

Applications across various devices have to talk - and talk effortlessly. This is a usable video editor are the two things killing the Ubuntu experience for me these days.

---

### Post by ireneshusband on 2008-11-30
IIRC, Funambol allows you to sync more than just the last month and next 6 months, but only if you pay for the extra service. Still not an ideal situation, but better than nothing.

---

### Post by Wharf Rat on 2008-11-30
TT
Shouted from the depths of the ether " You are not alone!"

1st.  I am marking this thread.

You actually mention multiple problems.
 RE: Office Documents
I tried to solve this by rolling out OO for Windows in my office.  Still I have people send me Docx files.  By chance, I was reviewing IBM's Symphony on my desktop at work (Windows).  When I clicked on an attachment (docx) in Outlook Symphony opened and translated it.  I was shocked.    This isn't an endorsement for Symphony which is really OO repackaged.

RE:  Outlook Functions + Blackberry
I use the above term because that is what we seek.  The functions of Outlook which I have to admit is the best part of MS Office and the least stable in my experience.


We currently use an IBM Linux server loaded with Exchange It, a product that mimics MS Exchange Server.  It works fine with Outlook but not Evolution (including Plugins). 

I still use Evolution on my laptop for mail using an IMAP setting.  Mail works, but no contacts, calendar, etc.

Thunderbird would work equally well.

I just discovered that IBM is dropping the Exchange It product line (Originally Nitix) in favor of Notes.  We will be upgrading to Notes in the next few weeks.  I will be happy to share any pain, err.. experiences.

So far, I have not found ANYTHING that works with a Blackberry and Linux expect the Barry code which allows me to charge my BB via USB ports.   I have tried every method I can find to set up a tethered modem.... nada!

Thanks for your comments on internet based solutions for the BB, I was going to try those. Guess I can wait to see what Lotus Notes holds.  It is supposed to sync with a BB -- at least the Windows apps.

Pocket Mac looks the most promising but is only being developed for Xandros and eeepc. :confused:

---

### Post by Magneto on 2008-11-30
This is where Im at now too with my HTC Touch. I had exported all my contacts and calendar to csv to import into evolution or sunbird but since I can't sync I'm just going to use VMware to mount my win partition and sync my phone to outlook/winxp via activesync like normal. I'm really surprised no one  has taken the initiative to advance linux - smartphone connectivity. 

I have 3 years of calendar data I need and google calendar wasnt going to be the fix for that anyway. I only really sync my phone for appointments, occasional contacts, tasks, notes and audio-video files. I use imap and Flexmail for my email needs. I could get away with everything but appointments and file transfer- which I can do now via my 8gb microsd card. 

Seems like these guys are able to do somethings in synce
[http://ubuntuforums.org/showthread.php?t=819802](http://ubuntuforums.org/showthread.php?t=819802)
but thats with the pocketpc platform not blackberry if memory serves.

---

### Post by tarahmarie on 2008-12-03
I'd like to add my voice to this one.  I have a T-Mobile G1, and I want DESPERATELY to sync it with Kontact.  

There should be no reason I can't sync Akregator with Google Reader as far as read/unread feeds.

I download my Gmail to Kmail on my desktop.  When I'm out and about, I get unread emails on my G1.  If there was a better way to do that, I'd be happier.  I'd especially like to be able to sync my Kmail trash with my Gmail trash--so I can delete emails in either place and have them show up in my Kmail trash.

My contacts don't properly export to Google, nor do they sync.

Let us not speak of the calendar.  I also have no To-Do lists on my G1.  THAT is the thing that causes me the most grief.  I used my WM5 device as an electronic scratchpad, and I need my G1 to operate the same way.

That To-Do list (Tasks, or whatever) would have been a deal-breaker if I had known about it in advance.

Kontact and the G1 SHOULD sync.

---

### Post by deadowl on 2008-12-03
Well, I've had problems with Evolution

1. Can't access repeating events with Google Calendar plugin
2. Can't download attachments from an exchange server.

I don't have all the fancy PDA stuff to worry about because I'm a dirt-poor college student. But if I had the money I would certainly have a PDA, and wouldn't want to have to put up with these problems.

---

### Post by tarahmarie on 2008-12-10
Well, I've heard that you can use GCalDaemon (or something like that) to sync Kontact with some stuff.  Does anyone know how to use that or whether it's in the repos yet?

---

### Post by deadowl on 2008-12-10
This guy made a .deb. I got it to work after a lot of fiddling.
[http://blog.philippheckel.com/2008/09/30/gcaldaemon-deb-package-for-ubuntu-kubuntu/](http://blog.philippheckel.com/2008/09/30/gcaldaemon-deb-package-for-ubuntu-kubuntu/)

I fell in love with it when my appointments showed up in my clock/calendar applet.

---

### Post by hyper_ch on 2008-12-10
regarding webmail, calendar, todo list I moved away from google and run now my own horde installation. The only thing that is missing in horde 3 is that different calendards cannot be differently colored.

However syncing todo and calendar works even with my old SE-K800i.

---

### Post by Magneto on 2008-12-10
> **hyper_ch said:**
> regarding webmail, calendar, todo list I moved away from google and run now my own horde installation. The only thing that is missing in horde 3 is that different calendards cannot be differently colored.

However syncing todo and calendar works even with my old SE-K800i.
how far forward and backward can horde store appointments? can it go years into the past?

---

### Post by hyper_ch on 2008-12-10
it can... although the syncing takes long then... 3k appointments were too much for my old SE-K800i... however 1.5k were ok.

---

### Post by Magneto on 2008-12-13
thanks i dont have  that many maybe 1000 at most- im gonna look into it

---

### Post by joker77 on 2009-01-01
I use a palm tx. I sync tasks, memos and calendar with evoulution. not interested in mail on the palm. Contacts: same problem mentioned by thread starter. My solution is to enter contacts in memos in palm, and later manually enter it in evolution. Then "copy to handheld" during sync. (I understand, not acceptable to people with ppc phones)

I know someone with a pocketpc (wm6.1) device who does similar limited PIM sync with finchsync and thunderbird and is quite happy. (on fedora)

---

### Post by theZoid on 2009-03-29
I'm trying various method of sync'ing Kontact in Kubuntu 9.04 with my Blackberry.  I used to use syncML with KDE 3.5 successfully with Kitchensync, but KDE4 I'm learning all over.  I wanted to sub to this thread also. Keep on it!  :D

---

### Post by rimbaud on 2009-03-31
> **deadowl said:**
> Well, I've had problems with Evolution

1. Can't access repeating events with Google Calendar plugin
2. Can't download attachments from an exchange server.



Oh yes indeed.  As I said on another thread:

"Unfortunately that is Evolution in a nut-shell. I have been using it for three years now with Exchange Server, and it has always been far too unreliable to recommend to any one else.

As to your point, I wouldn't bother with the Google Calendar sync: it works most of the time, but other times won't sync all the events or, even worse, fails to sync and deletes the event. I just directly use Google Calendar now.

Version 2.24.3 with Intrepid"

---

### Post by loeppel on 2009-08-12
> **hyper_ch said:**
> regarding webmail, calendar, todo list I moved away from google and run now my own horde installation. The only thing that is missing in horde 3 is that different calendards cannot be differently colored.

However syncing todo and calendar works even with my old SE-K800i.

How do you sync horde with your phone?

---

### Post by theZoid on 2009-08-12
I'm with everyone else....However, at least now I can convert my Outlook contacts for Evolution _directly_....it does work:

I can confirm it works…[http://outport.sourceforge.net/doc.php](http://outport.sourceforge.net/doc.php)

---

### Post by paai on 2009-09-22
I wish that I had the ear of Shuttleworth and his collegues with SuSE and Redhat. Too much effort goes in the eye candy, or in all kinds of esoteric applications, but syncing with a cellphone seems to beyond them all. And you call Linux ready for the desktop???

Myself, I have a Treo 650 and these antique Palm PDAs are perhaps the only handhelds that come anywhere near a working sync with Linux, depending on the calendar application you use it with.

Jpilot works every time, but it is serial only (no bluetooth) and it is a stand alone application. 

Kpilot worked reasonably well under KDE3, but it is irrevocably broken in KDE4 and the new Akonadi database underneath it is worse . Stay away fom it!

So far, Evolution seems to work even with bluetooth under the condition that I change preferences  from bluetooth to something else and back before every sync. But no  syncing with web calendars.

Last year I have been thinking about a new PDA, but after searching the internet, it became clear that absolutely no one is guaranteed to do a normal sync with any Linux application. And I am not going to fork out three or four hundred Euros for a gadget that I can't sync with my PC, so I hope that my Treo 650 will survive a few more years.

Perhaps it is time for a concerted effort to bring this problem under the eyes of the aforementioned COE's?

---

