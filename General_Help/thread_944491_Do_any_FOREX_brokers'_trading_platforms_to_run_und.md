---
title: "Do any FOREX brokers' trading platforms to run under Ubuntu?"
date: 2008-10-11
forum: General Help
---

### Post by AWittyUserName on 2008-10-11
I am a former windows xp user, and there are just a handful of applications I haven't been able to find substitutes for since moving to Ubuntu.

One of these is the supporting application required by a foreign currency discount broker.  Now, I am willing to use any broker as long as their trading platform runs on Linux, and they offer either gold spot trades or gold futures contracts in addition to major currencies.

I tried the following brokers.
GCI Financial - application installs under wine, application starts, but connection dies in moments. [http://www.gcitrading.com/](http://www.gcitrading.com/)
FXCM - wine install fails
MetaTrader4 - wine install fails
gftforex application - wine install fails
gftforex web interface - this worked but only a handful of instruments are available compared with what the resident application promises.  Boo.
Avatrader - website promises that the supporting application runs under Linux, but the sign-up form does not list USA as a possible location.  I don't want to lie on this form.  No response from support.

I have visited the live chat feature of most of these places, and the common response is "sorry windows only".  It is sad because I think most of these tools use Java.

Has anyone else had better luck?

---

### Post by Amurko on 2009-06-15
I'm curious too..  I'd like to have a Forex broker that'll fully function under Ubuntu, either through a web platform or a native Linux one.  Running it under wine isn't good enough..  there's no guarantee that the required future versions will also be wine compatible.

---

### Post by AgentZ86 on 2009-07-02
Hi all,

This is an old post, but I'll reply

I use MGFinancial for forex java trading,

But I can use MT4 with just about any platform that supports MT4

Here is a thread on this subject, and see my responses to it as I've not had any real trouble running the MT4 , however I don't like MT4 but this might help you.

MGfinancial I do not believe has any gold futures or not but you can check their site to see if they do.

[http://www.mgforex.com/Default.asp?fromSecure=true&&](http://www.mgforex.com/Default.asp?fromSecure=true&&)

I like the 3 pip spread and enjoy their java platform for my forex trading, their mobile leaves a little to be desired, however it is all there and available for mobile trading.

Anyhow I hope this helps

---

### Post by xyepblra on 2009-07-25
iTrader v7.5 by [www.kf-forex.ru](www.kf-forex.ru) can be installed under wine 1.1.26, although the broker company is Russian.

---

### Post by AWittyUserName on 2009-08-18
@AgentZ86 thanks.  will check it out

Ideally I'd like something that can be automated.  For example, I'd like to be able to load a conditional trading definition file, back test it with specific parameters, and save the resulting backtest report to a file, all without human interaction.

I guess that's just a pipe dream.

---

### Post by AgentZ86 on 2009-08-25
> **AWittyUserName said:**
> @AgentZ86 thanks.  will check it out

Ideally I'd like something that can be automated.  For example, I'd like to be able to load a conditional trading definition file, back test it with specific parameters, and save the resulting backtest report to a file, all without human interaction.

I guess that's just a pipe dream.

No, you can do it under wine also such as MT4 Metatrader

See here I've done it not problem.

[Click Here:]("http://ubuntuforums.org/showthread.php?t=587829")

---

### Post by UAhmad on 2009-09-06
Hi i try to install MT4 from FXCM (using both Crossover and Wine) but got an error on Liveupate. Using Ubuntu 9.10

Please any idea. Help

---

### Post by ice-boy on 2010-01-14
[ForexClub]("http://www.forexclub.biz")  for Linux support two softwares - [ModernForex]("http://download.fxclub.org/Modern/modernforex.deb") (Modern FX) and  [Rumus2]("http://download.fxclub.org/Rumus2/FxClub/Rumus2.deb") (Classic FX). Software you can find [here]("http://www.fxclub.org/tools_soft/") and [here]("http://www.fxclub.com/rumus/").

---

### Post by AgentZ86 on 2010-03-09
> **ice-boy said:**
> [ForexClub]("http://www.forexclub.biz")  for Linux support two softwares - [ModernForex]("http://download.fxclub.org/Modern/modernforex.deb") (Modern FX) and  [Rumus2]("http://download.fxclub.org/Rumus2/FxClub/Rumus2.deb") (Classic FX). Software you can find [here]("http://www.fxclub.org/tools_soft/") and [here]("http://www.fxclub.com/rumus/").

I've seen those too thanks

I've also recently been researching Oanda = [http://fxtrade.oanda.com/](http://fxtrade.oanda.com/) seems nice as well.

They have no min. deposit requirements and .9 spread on the EUR/USD which I'm excited about. I'm testing out the platform now

It's web based as well, and no download required just like MGfinancial

This I like a lot.

Happy trading

---

### Post by xyepblra on 2010-03-27
> **AgentZ86 said:**
> I've also recently been researching Oanda = [http://fxtrade.oanda.com/](http://fxtrade.oanda.com/) seems nice as well.
They have no min. deposit requirements and .9 spread on the EUR/USD which I'm excited about. I'm testing out the platform now
It's web based as well, and no download required just like MGfinancialSo, how do you find it? Can you share your impressions and experience?

---

### Post by trentscott on 2010-08-04
Oanda has a Java-based platform that runs under Ubuntu Linux -- I've noticed no compatibility issues whatsoever. Here's a guide on getting it setup:

[http://trentscott.com/2010/08/04/how-to-trade-forex-in-ubuntu-linux/](http://trentscott.com/2010/08/04/how-to-trade-forex-in-ubuntu-linux/)

---

### Post by AgentZ86 on 2010-11-20
> **xyepblra said:**
> So, how do you find it? Can you share your impressions and experience?

Old Post revival

Since MG financial shut down, likely due to the margin rules change CFTC requirement for 50:1 max leverage, but anyhow I've now been really testing and enjoying the Oanda platform.

It could use some slight more enhancements, but I love the ability to trade units, and not lots.

You can trade as little as 1 unit which is like a nano fractional lot.

So testing your strategy and trading a demo, then switching to a live account to see how live environment will work is great especially if your trading nano lots so you can test the live environment with practically NO money

Also you can open an account with NO min. if you like such as $10 bucks or so.

And test your live trading with 1 unit if you like

With the new leverage rules:
10k units for EUR/USD is about $250 of used margin
1k unit lot is about $25 of used margin
100 units lot is about $2.5 of used margin
10 unit is about .25 cents
1 unit is about .025 cents LOL super small but good for testing live trades.

And you if you are consistant and successful you could add a monthly increase of lets say $25 bucks or so and then increase your lots over time you could build a nice nest egg.

Thats if your small and want to build it.

Of course you would just put the lump sum and start makeing and taking profits, but I think Oanda fits every type of trader which I have grown to like.

Anyhow thats all I know

---

### Post by vodsdarov on 2011-01-05
Thanks for the review AgentZ86!

I've been researching for some days a convenient way to trade the forex in Ubuntu.

I'll take a closer look at Oanda.

---

### Post by AgentZ86 on 2011-01-06
> **vodsdarov said:**
> Thanks for the review AgentZ86!

I've been researching for some days a convenient way to trade the forex in Ubuntu.

I'll take a closer look at Oanda.

Hi,

After much review I've now been trading with them live

And one feature I very much like is the ability to create sub accounts

So for example:
If I want to test a strategy that uses only a couple EMA's and trade a full bodied candle when it crosses the EMA

Then I can open a sub account which will either create another profile of saved indicators or I could use my same profile for the sub account.
And lets say I want to test a strategy for only MACD crosses or something like that or perhaps only trade certain news releases.

In this case I could track my progress for each strategy and/or maybe even hedge since it's 2 separate accounts etc. 

Anyhow, I've been trading live now on Oanda thus far and it seems to be working really well stable across all Operating systems.
I'm not sure how responsive they are with news releases because I place advanced entries in advance of the news most of the time.

Main thing on Ubuntu 10.10 is you will have to use the real java plugin for your browser I don't think the ice tea didn't works properly for me with the Oanda platform but no biggie just uninstal it and install the java stuff.

Another feature is their news and also trading advice in the news section very informative to my pleasant surprise

Also I highly recommend the FPA (Forex Peace Army) to help with broker reviews,signal reviews, and managed account reviews.
Just about all broker have reviews so that you won't be scammed by a broker.
A lot to read through and you have to take some reviews as just someone who may have lost money and not a scam broker at all this is a great source of info and they provide free news signals that are right on most of the times.
They will give you at least 150 pips a month on news signals for free each month. See the Signal section and See Henry's signals and get on the email list. Again they offer this service for Free I was totally surprised and recently started adding the news signals to my already working technical strategy.

[http://www.forexpeacearmy.com/](http://www.forexpeacearmy.com/)

Anyhow, I hope this helps
Happy Trading

P.S
If I find any other good platforms for linux I'll be sure to post

---

### Post by tjones00 on 2011-02-19
As to Oanda you can also run all their java desktop clients without any webbrowser.

It's a great toy for anybody interested in forex as well since their free demo account never expires.

[http://fxtrade.oanda.com/trade-forex/fxtrade/desktop](http://fxtrade.oanda.com/trade-forex/fxtrade/desktop)

The green fxgame.jnlp is the demo account stand alone launcher. Download the file and launch it.

You can also make a self updating launcher for it just remember to use something like javaws /path/to/fxgame.jnlp as the execute command.

---

### Post by djordi on 2011-08-09
metatrader 4 under wine requires dlls which you can get with winetricks, read this:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=2893&iTestingId=60213](http://appdb.winehq.org/objectManager.php?sClass=version&iId=2893&iTestingId=60213)
been using this for ages under ubuntu 9 and 10

---

### Post by anismizi on 2011-10-06
Brother.Can you please tell me that,what is forex trading?

---

### Post by lisati on 2011-10-06
> **anismizi said:**
> Brother.Can you please tell me that,what is forex trading?

FOREX = [FOReign EXchange]("http://en.wikipedia.org/wiki/Forex")

---

### Post by pbanerjee on 2011-12-02
Oanda's FxTrade works like a charm.
I have mt4 running absolutely fine on wine 1.3.31. I use Lucid Lynx
My mt4 is MB trading UK demo and Oanda's live mt4 although I mostly use Oanda's FXTrade more than their mt4

---

### Post by eranhason on 2012-08-17
ThinkOrSwim by TD Ameritrade works great on any Linux

---

