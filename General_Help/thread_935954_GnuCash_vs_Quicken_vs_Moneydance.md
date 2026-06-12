---
title: "GnuCash vs Quicken vs Moneydance"
date: 2008-10-02
forum: General Help
---

### Post by tone33 on 2008-10-02
I currently use Quicken 2006 to manage my personal finances.  I don't use the online bill pay feature, but I do reconcile my accounts by downloading transactions, and track my investments and Quicken does it quite nicely.  But lately I've been bitten by the open source bug and I'm in search of an alternative.  I looked into this last year and decided to wait till things mature a little with open source money management tools.

I'm leaning towards GnuCash.  Also looking at MoneyDance, but it costs $$$ and isn't opensource :(.  I think I can do everything i need to in GnuCash.  Can folks share their experiences with either of these programs?

---

### Post by Ms_Angel_D on 2008-10-02
I haven't used either of the ones you mentioned however I do use KMyMoney available in the repo's it's said to be very easy for people who use Quicken to adapt.

You may want to take a look at this article: [Top 10 Linux financial tools]("http://blogs.techrepublic.com.com/10things/?p=372")

---

### Post by _sAm_ on 2008-10-02
I don't know myself, just going to try out GnuCash to see how it works. But they are free, so why don't you try them all and see if they do what you need. Be sure to take a look at HomeBank and Grisbi(you will find both in Synaptic).

[http://homebank.free.fr/](http://homebank.free.fr/)
[http://www.grisbi.org/index.en.html](http://www.grisbi.org/index.en.html)

---

### Post by callmebruce on 2008-10-07
I've used KMyMoney, GNUCash and Quicken. Neither KMyMoney nor GNUCash can compare to Quicken in either ease of use or integration with banks. Quicken is very straight-forward in setting up accounts and automating updating your transactions. With GNUCash I had to log on to each bank and download transactions as QIF and import them. With KMyMoney I was downloading manually and importing as QIF. I see KMyMoney now supports an OFX plugin. Still, you have to manually log on to your bank and download your transactions as OFX. Then import. All of that is automated in Quicken. 

If you already have a copy of Quicken, and if you have WINE installed on your PC, you might want to see if you can get Quicken to run under WINE. Quicken is not opensource, but it works. There is an awful lot to be said about an application working.

Me - I swapped back to KMyMoney. It is simple enough for me to use. I am using the stable version - but am thinking of going to the unstable version (if I can figure out how) for the budgeting reports. 

I also read the KMyMoney can be compiled to support online banking via OFX. I don't see that as an option with the stable version available through Synaptec. I'm searching for a version already compiled for Kubuntu that supports online banking.

I'm lazy - just the thought of logging on to multiple banks and credit card places to download transactions is no fun. I need the online banking part working.

---

### Post by callmebruce on 2008-10-08
Messed around with KMyMoney some more. I'm starting to like the OFX Web Connect. Basically, you go to you bank, select your transactions and format (OFX for me), and select. You then get prompted by your browser (I use Firefox) for the application. Click OK, and it automagically pops your OFX download into KMyMoney. Kind of nifty.

GNUCash was pretty cool, but the double entry accounting got a bit much for me. I prefer the ease of use of KMyMoney.

---

### Post by Subban on 2008-10-08
I've been using Moneydance for quite some time. It sounds like my usage is similar to yours in that I download the OFX (supports other formats too) and import it into Moneydance and proceed from there so I can see where my money goes.

The only downside I have with Moneydance is if the imported transaction has a changing reference then it seems to bypass Moneydances ability to try and repeat what category you assigned to it before, so for example I have to *constantly* put my expenditure at Somerfields (for groceries) in the the Personal:Groceries category and I can't find a way to fix it, all because Somerfields adds a Ref number to the transaction that Moneydance doesn't allow for. Moneydance does of course manage to get all other transactions right and repeat the correct category. Its not much of a problem to be fair, its very easy to select the correct category from a drop down before hitting 'record'.

Other than that Moneydance is very simple and more than competant for what I need so haven't looked at alternatives. I managed to use it from whithin a few minutes without reading the manual and have no previous experience with similar software. Oh, and the cost for Moneydance was almost insignificant something like under 20 quid.

---

### Post by SamNSane on 2008-10-08
I'm going to buck the tide just a little. You can trust me when I tell you I am NOT a business-oriented bloke. My wife, on the other hand, is a CPA in addition to being a systems analyst.

We used Dollars and $ense on Apple //e, Quicken and Money under DOS, Quicken and Money under several versions of Windows. Over the years I became downright appalled at just how horribly written Quicken and MS Money were. Intuit and MS just kept shoveling on the features without fixing terrible flaws in the software. And they kept creating new flaws while they were at it.

Heck, Money (if you download it instead of getting the disc) can't even be reliably reinstalled without jumping through a bunch of hoops for the lousy online vendor MS uses.

I finally had it one day and went looking for Open Source alternatives. I tried a number of them, but my wife fell in love with GnuCash (for Windows) when it was released last year. It's kind of funny because I had a HARD time dealing with the double-entry behavior, but my wife persisted in making me stick with GnuCash. Over time I've grown to love it. I don't think I could live with anything else now.

And it genuinely does get better with each new release (notwithstanding some odd bugs recently having to do with calendar controls in one version). But you report a bug at bugzilla on this app, and the developers get right back to you. I never got anyone at MS to acknowledge that ANYTHING was wrong with Money. And that is one nasty, stinky application!

After I got used to GnuCash and learned to tailor my data entry habits to match the way it works it wound up being FASTER to use than Money or Quicken -- at least for wifey and me.

---

### Post by tone33 on 2008-10-10
Thanks for all the replies.  I do have wine running and I will try to get Quicken running in the meantime, but I think for the long term I will start playing with GNUCash.  One of my biggest issues with quicken is that I have never gotten the one step update to work correctly.  So I have to go to each of my account's sites and download manually anyway.  I like the idea of having more control and a better understanding of my finances which is, i think, one good reason to switch to GNUCash.  Another is the fact that there won't be all these useless features that quicken tries to pack in to the product that i never use.  Yet another is that is gets me further away from depending on windows binaries.

I have a couple of 401K accounts that Quicken tracks fairly well - does GNUCash support investment accounts similiar to the way Quicken does?  I really thinking more about the functionality here, not a pretty wizard that makes the setup easy.

---

### Post by FluffyElmo on 2008-10-10
Slightly off topic, but something like logging into your bank to download transaction files is a task that would be pretty easy to automate. If you program, the Mechanize library is available for several languages and is designed for this sort of thing. Something like the iMacro ([https://addons.mozilla.org/en-US/firefox/addon/3863]("https://addons.mozilla.org/en-US/firefox/addon/3863")) Firefox plug-in might also work of you aren't a programmer 

Of course it depends on your bank, their site may make things difficult or impossible. But I think the reason GnuCash doesn't support automatic bank importing is not that it's difficult but that trying to maintain scripts for all the banks in the world is a daunting prospect to say the least.

---

### Post by tone33 on 2008-10-10
i do program, and will look into Mechanize - is it only in Ruby though?

---

### Post by FluffyElmo on 2008-10-10
I think if you google for "Mechanize Perl" or "Mechanize Python" it turns up libraries and examples. Probably for other languages as well, I believe (but am not sure) that they are all derived from the original Perl library.

I can only personally vouch for the Ruby version. I used it with hpricot to transfer data between two sites. I'm not actually a Ruby programmer. I just jumped in with one of the online examples and a free reference ('The Humble Ruby Book') and it went well. 

Though if you can get a similar library in a language you're familiar with that's usually the best option:)

---

### Post by tone33 on 2008-10-12
Just wanted to follow up on my experience thus far with GnuCash.  It's freakin awesome!  I'm learning a bit more using the double entry method, but I consider this a good thing.  One aspect on Quicken/Money I never liked was that it would setup your accounts automatically (i.e. link an asset to a liability account).  This is good and Quicken is supposed to do this, but it kept me from truly understanding how it works under the covers.  I will forge ahead with GnuCash - next up is setting up my monthly scheduled transactions.  So to anyone else interested i say try it out if your a nuts and bolts kinda person, but if you like the automation of other software then by all means stick with that.

---

### Post by Hei Ku on 2008-10-14
If you are interested on trying the unstable version of KMyMoney, you can install it from a Launchpad PPA here:
[https://edge.launchpad.net/~claydoh/+archive](https://edge.launchpad.net/~claydoh/+archive)

---

### Post by SamNSane on 2008-10-15
> **tone33 said:**
> Just wanted to follow up on my experience thus far with GnuCash.  It's freakin awesome!  I'm learning a bit more using the double entry method, but I consider this a good thing.  One aspect on Quicken/Money I never liked was that it would setup your accounts automatically (i.e. link an asset to a liability account).  This is good and Quicken is supposed to do this, but it kept me from truly understanding how it works under the covers.  I will forge ahead with GnuCash - next up is setting up my monthly scheduled transactions.  So to anyone else interested i say try it out if your a nuts and bolts kinda person, but if you like the automation of other software then by all means stick with that.

I had a feeling that you'd like GnuCash. I think the thing that most folks coming from Quicken and Money have trouble with is the idea that **everything** you spend money on or get money from is an account. That categories crap in the commercial products used to drive me nuts. Talk about obfuscation in the service of simplification!

---

### Post by tone33 on 2008-10-15
any ideas how to connect directly to online banking via ofx?  I saw something on the wiki... but looks like you have to rebuild the source??

---

### Post by SamNSane on 2008-10-16
> **tone33 said:**
> any ideas how to connect directly to online banking via ofx?  I saw something on the wiki... but looks like you have to rebuild the source??

I'm sorry to say we haven't even bothered. My wife usually handles the downloading of information from banks, etc. The fact is that the online connection features of Money and Quicken were highly unreliable anyway (at least with the institutions we use), so she always handled it manually or scripted the process of downloading and importing. She's doing the same with GnuCash in Windows.

I might look into this myself, only I'm using 2.2.4 from the regular repositories. I hadn't even noticed that 2.2.7 had been released. Should fix some problems with the calendar drop-down that were plaguing my wife so much in 2.2.6 that she reverted to an earlier version to await the new release. She'll be delighted to get the new one.

It looks like there are a lot of links to resources leading from [http://www.gnucash.org/](http://www.gnucash.org/). I hope you'll find the information concerning setting up connections. I'm going to look around for it this weekend.

---

### Post by lrf on 2008-12-28
Was Moneydance loaded on a 64 bit system?

---

### Post by Subban on 2008-12-28
> **lrf said:**
> Was Moneydance loaded on a 64 bit system?

If that question was directed at myself, then no, I run it on a normal 32bit Ubuntu install (though the CPU is a 64bit one). Its written in Java so it should be nice and portable (probably)

---

### Post by dcstar on 2008-12-28
> **Subban said:**
> If that question was directed at myself, then no, I run it on a normal 32bit Ubuntu install (though the CPU is a 64bit one). Its written in Java so it should be nice and portable (probably)

I run Moneydance on 64-bit 8.04 without any difference to running on 32-bit.

I have found it well worth the few dollars I paid for it a few years ago when I left Windows (and Quicken) and started using Ubuntu 4.10. I have had free version upgrades and functional extras in the form of new Extensions appear now and again - I would recommend it and you can run it cross-platform so you aren't locked into the O/S you are using at this very moment.

---

### Post by paxmark1 on 2009-01-06
gnucash still has an ancient bug via libgtkhtml that makes reports spill o   v  e   r  and not print data. Default font is 14 point and you are not even able to toggle landscape versus portrait for printing.  Bloody bother writing down by hand for the new years accounts for the opening balances.  However it does do well for my having to convert between Canadian and Us monies 

Still using it.  The support for it really sucks.

---

### Post by punkybouy on 2009-01-31
I left Quicken two years ago for Moneydance.  I had used Quicken for about 15 years and got tired of the advertising popping up in the later versions.  I exported data to Moneydance and it imported it quite nicely although I did use the opportunitiy to clean up my stock purchases over the years and that took me about 6 weeks and for that period I ran Quicken and Moneydance  in parallel.  I would suggest people do the same in case you run into any snags.
Moneydance relies on Java and for awhile there was a problem with Java and printing on Linux.  It may be fixed at this point I don't know. Java was not compliant with a newer version of CUPS.  Sun claimed it was a CUPS issue and the CUPS folks claimed Sun was not in compliance.  In any case Moneydance was caught in the middle.
Sometime last September I switched to a 64 bit version of Ubuntu and something happened to my Moneydance file.  Sometimes Windows, like for reconciling open up very large with no print in them. I have to open and reopen two or three times before they work properly.  The problem carries over to 32 bit machines if I move my moneydance file to them.
Because of this I switched to Gnucash and again have been running them both in parallel for the last several months.  I could not export Moneydance data to Gnucash.

---

### Post by sieve on 2009-04-01
I just heard about GnuCash.

I can live with not being able to automatically sync with financial institutions as long as the download then upload/import works fine.  

I can live with the double entry accounting.  In fact, I almost prefer that because it keeps it real.  One thing that bugs me about Quicken is the propensity to overautomate or hide the other side of a transaction.

For those who have used both Quicken and GnuCash, are there other key features or actions in Quicken that GnuCash doesn't do or does poorly?

---

### Post by shane2peru on 2009-05-02
I was a long time Quicken user, and moved lock stock and barrel to Linux.  Tried GNUCash for a year, and didn't much care for it.  I like the look and features that MoneyDance has.  I don't mind investing a little for apps on Linux, I spent way more money on Window's apps!  MoneyDance has been great, seems as though I'm having a bit of java problems running on 64bit Jaunty, not sure what to fault it at, but minor issues.  I did really like Quicken before.  Oh, we live in a foreign country, so we have to use foreign currencies, makes bookkeeping a little extra work.

Shane

---

### Post by pg-13(prostitute) on 2009-05-02
thanks for the post, i now will have to try some linux accounting software

about 10 years ago when i first started my business i decompiled quickbooks 3.0 for windows which was written with visual basic 3.0 so it was opensource on my computer for a while...

im thinking about programming some software for accounting after studying the barrons accounting books which are great

check em out at at barrons

i have yet to try linux software for accounting ill have to give it a try
ive been using MS Accounting lately but ive switched to linux pretty much fulltime so i might as well do my business accounting on their also

btw.  the accounting book i reccomended was barrons accounting by eisen. "the easy way"
its like $14.95 and the excersises will drill so much accounting info into your brain youll rock
barronseduc.com

---

### Post by jkarcz on 2009-05-02
I have about 13 yrs of quicken data and I didn't want to loose it.  So, about 2 years ago I imported all the quicken data into Moneydance.  It took me a few days but I got all the data imported.  I didn't have any complicated investments.  Moneydance doesn't handle investment account import/export very well.  I did the same for gnucash.  Both financial programs did the basics stuff really well, but for me, Quicken was much more polished.  I eventually installed Windows XP home inside a Virtual Machine using Virtualbox, just to run Quicken, hoping a better solution comes around.

Moneydance, at the time I was using it would always have one or two nagging bugs that took forever to get fixed.  Like tabbing through a transaction didn't always work, it lacked any forecasting functions, printing was hit or miss. The graphing and charting leaves a lot to be desired.  The developer did transition to difference graph generation engine, but it never felt quite complete.

Gnucash was overkill for what I needed.  It seemed geared for small businesses.  The graphing and charting was pretty decent though, but you had to set it all up yourself.

Quicken, maybe I'm just used to it.  I work and play in front of some form of linux desktop 8-12 hrs a day, probably longer if I paid closer attention, and do everything else with natively installed linux software, everything except quicken.  I'd give it up in a heartbeat when something better comes along.

---

### Post by Cuba71 on 2009-06-16
I've tried to import my Quicken data into Moneydance without success.

I also tried to start from scratch and I couldn't enter my investments information properly.

The double entry feature makes thing even more complicated.

The User Guide is more of a features list that a users manual.

---

### Post by flylow on 2011-04-11
New to the forum and I'm trying to get GnuCash set up and need to import data from my bank. I get this error when importing "Line 5: File does not appear to be in QIF format: C* Read Aborted". I bank at Chase and I'm sure I selected QIF for the download. Any ideas?
[https://picasaweb.google.com/JeffDHill/Apr112011#5594359050614821714]("https://picasaweb.google.com/JeffDHill/Apr112011#5594359050614821714")

---

### Post by claven123 on 2011-05-05
flylow, 

You seem to have resurrected an OLD message thread.  I would suggest starting a new message.  You'll get more help that way.

BTW, did you try the QFX format on the export from Chase?


I have to say to a previous poster (years previous) that there is good support for gnucash via the mailing list.  However, I will say the documentation is not always the best.  I personally love the program and couldn't get moneydance to import my data from quicken.

Dennis

---

