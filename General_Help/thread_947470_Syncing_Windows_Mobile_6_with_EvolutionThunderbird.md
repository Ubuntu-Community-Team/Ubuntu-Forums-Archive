---
title: "Syncing Windows Mobile 6 with Evolution/Thunderbird"
date: 2008-10-14
forum: General Help
---

### Post by OneRingShort on 2008-10-14
I know this has been put up several times, and a howto has been made, but it seems whatever I find is for older versions of Ubuntu or Windows Mobile and doesn't work anymore.

What I want to be able to do is sync WM6 with either Evolution or Thunderbird (don't have a preference, which ever is easier).  I don't care about email syncing, as I don't have it on my phone, but I do care about the contacts and calendars.

Every method I've seen seems very complex or round about (syncing with Google Calendar, exporting, and then importing?)  I've heard about the Multisync and Synce programs, but that's usually where the problems begin, and I can't get past those steps.

Does anyone know of a more direct or simple way to do this?  Can you sync through VirtualBox?  If you know a program that can do it _easily_, let me know (I would not be opposed to paying for it if it worked well without being too complex).

On a similar note, I've found that when I import a calendar as a .csv file into Evolution, it imports it into the contacts section, regardless of how I specify it.  Anyone know why?

I may be asking for a miracle to get this sync working, but it is the only thing left for me to configure on Ubuntu to get it to the way I like it.  I'm not saying that I'll drop the OS if it doesn't work, just that it'll make it all the better.

Matt

---

### Post by VeeDubb on 2008-10-26
I have a WM6 device which syncs just perfectly with Ubuntu 8.04

I VERY CAREFULLY followed EVERY LINE of the directions at [http://www.synce.org/moin/SynceWithUbuntu](http://www.synce.org/moin/SynceWithUbuntu)

They worked extremely well for me, but I will warn you: those directions will almost certainly NOT work if you've been trying other stuff and failing.  You'll have to track down and fully remove any packages you have installed with other how-to's or you'll need a clean install.  Sorry, just the way it is.

Also, if you get hung up at some point in that how-to, do NOT try to add in something else that you saw in another how-to.  No matter how sure you are that typeing synce-serial-start is going to help, DO NOT DO IT UNLESS THAT TUTORIAL SAYS SO.  

Sorry for the caps.  I wanted to be sure nobody missed that line.

Anyway, the only thing I could add to that, is that once you have everything working, I find it convenient to either modify your session, or create a start-up script that will run sync-engine int he background.  But do that ONLY AFTER you have a fully working sync set-up following those directions.

---

