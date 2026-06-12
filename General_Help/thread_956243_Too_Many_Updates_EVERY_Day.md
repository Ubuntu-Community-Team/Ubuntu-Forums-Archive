---
title: "Too Many Updates EVERY Day"
date: 2008-10-23
forum: General Help
---

### Post by RoboFish5000 on 2008-10-23
I'm fairly new to Ubuntu, but so far I think I've been getting the hang of everything except for one problem...

Recently (within the past couple weeks or so) I've had an obscene amounts of updates from the Update Manager. I'm getting between 4 and 18 updates a day with total file sizes between 1.0mb and 12.0mb. That's too much to be getting every day, and it seems to me that the update manager is always running, like it's hunting for silly things to update. I don't even know what any of the updates are! 12 updates for something called BIND? I have NO idea what that is (which may seem silly to some of you, for all I know bind is something very important).

Did I somehow get a virus? Or is Ubuntu just one of those operating systems that likes to update? (which is one of the main reasons I left windows...).

Please help, I'm worried about my computer.

---

### Post by melojo on 2008-10-23
What version of ubuntu are you using?  
8.10 is still in beta and I get a lot of updates.

---

### Post by b0b138 on 2008-10-23
goto system > administration > software sources. Under the updates tab, you can change how often it checks for updates, default is daily.

---

### Post by dcstar on 2008-10-23
> **melojo said:**
> What version of ubuntu are you using?  
8.10 is still in beta and I get a lot of updates.

Exactly, 8.04 has only had a few updates recently - I was actually worried about how **few** updates were appearing!

---

### Post by Cannaregio on 2008-10-23
> **RoboFish5000 said:**
> 12 updates for something called BIND? I have NO idea what that is (which may seem silly to some of you, for all I know bind is something very important).

Bind is old magic, and very prone to exploits, like sendmail.

Bind9 has been rewritten, needs finetuning.

Worth knowing what it is and how to use it, though.
If I were you :-)

More generally, there's no real need whatsoever to continuously update. It's just the old inescapable itch of the linux hacker of old, always on the edge, always fiddling instead of working, never really enjoying his box.

Get you ubuntu copy 4-5 months [COLOR="Blue"]after[/COLOR] the "official" new version came out and run it [COLOR="#0000ff"]without updates at all[/COLOR] until an even newer version has been already out for 4-5 months.

So, for instance, stick now to hardy and switch to ibex around february/march, not before. 
Then do NOT update at all until august. Then rince and redo.

This -if you want to live quietly- will avoid you various busloads of update problems :-)

---

### Post by Elfy on 2008-10-23
> **dcstar said:**
> Exactly, 8.04 has only had a few updates recently - I was actually worried about how **few** updates were appearing!

I'd worry if I was only getting <18 updates for intrepid _ it would feel as though they'd forsaken us :)

> **b0b138 said:**
> goto system > administration > software sources. Under the updates tab, you can change how often it checks for updates, default is daily.

While you are in there make sure that you'd don't have backports and proposed enabled as sources.

---

### Post by RoboFish5000 on 2008-10-23
> **melojo said:**
> What version of ubuntu are you using?  
8.10 is still in beta and I get a lot of updates.

I'm currently using Hardy (and - responding to Cannaregio - yes, coincidentally I started getting involved with Ubuntu very shortly after Hardy was released, so I guess that explains all of the updates).

Thanks to all of you for the very quick and thorough responses! I've fiddled with my update schedule, but what I'm getting from all of the responses is that updates are fairly common and are generally good.

Well that's good to hear.

One last question before I mark this as solved though: What would you say is "too many updates" and could all of these updates fill my hard drive? I'm on a laptop and don't exactly have much room to begin with. 15mb a day kind of adds up (or is it more often that things are *replaced* during updates instead of files just being dumped into your system?).

---

### Post by patrickballeux on 2008-10-23
> **RoboFish5000 said:**
> 
One last question before I mark this as solved though: What would you say is "too many updates" and could all of these updates fill my hard drive? I'm on a laptop and don't exactly have much room to begin with. 15mb a day kind of adds up (or is it more often that things are *replaced* during updates instead of files just being dumped into your system?).

They don't add, they replace...  So you can update over and over again without worrying about your free space on your harddrive.  Of course some updates can take a little more space, as some others will take less...  But the packages are not taking more spaces over time (There is a cache, but it is cleaned regularly to prevent this...)

---

### Post by sethvath on 2008-10-23
sudo apt-get autoremove
sudo apt-get autoclean

---

### Post by marshall.robert on 2008-10-23
i would just say, be thankful you dont have to reboot every time :P thats one blessing over windows any day (esp windows vista which is horrible at updating).

linux is a very fast moving operating system and so updates will be very frequent, it also means that you will be as secure as you can be since exploits are patched up with updates. it would be less of a pain i suppose if there was an option to install them automatically, but you can get them downloaded automatically.

as for disk space, i wouldnt worry, like whats been said before, it cleans out the cache regularly, but if you want to clean it out yourself you can type "sudo apt-get clean" in console.

---

