---
title: "The Good, The Bad &amp; The Ugly - 48hrs with Karmic"
date: 2009-11-06
forum: Installation &amp; Upgrades
---

### Post by Donalb on 2009-11-06
Yes, I know there's an Installation experience thread...

I've been using Ubuntu about 3 years, full time about 2 years. I've installed it on family members laptops to reduce my own time spent fixing their systems. Hell, I've BOUGHT the "Powered By Ubuntu" system stickers!

I love it like I never loved a GUI, and I've used a lot of GUIs over 20 years. Despite all that time I'm a pointy/clicky person. I can cut & paste commands but no desire to do more than that, and then only when necessary.
Ubuntu is almost the OS I feel I deserve. (You know, as I've put up with shite like Wins 2.0, Millennium, Mac 8.0, what was the IBM one called?)

I went through 7.04, 7.10, 8.04 & 8.10.
I believe Ubuntu is bringing a great OS to the people. And that's to be desired. I've worked in various parts of the IT industry for 25 years.
I stayed with Intrepid for the last year because of the Intel graphics regression problems and because Intrepid is THE SINGLE GREATEST OS I ever used.[SIZE="1"]But I wanted more.[/SIZE]
(I found it weird that people say wait for an LTS if you want stability, when 9.04 was so broken in the Intel graphics area. I lost faith in the LTS idea because of that)...

I got Karmic installed 2 days ago, and it's given me lots to talk about, and the reason why I'm talking about 48 hours. 

My initial experience was more positive. 
But there's a pattern here. 
Many things that worked fine the first time & the first 24 hours but retrying them no longer work! And I've done nothing!


**The Good:**


:- I actually went to install Karmic last week, but the new Disk Analyser told me I had Bad Sectors on my HDD, enough to make me change my HDD (still under 3 year warranty). Very, very good, though an upgrade wouldn't have found it and it may have bit me worse in the long run. Another reason to go with Install rather than Upgrade. Love the Disk Analyser. I'm an obsessive geek when it come to my storage. 
 
:- I installed root as Ext4 and kept my /home as Ext 3. Seemed like a reasonable halfway house. Some of the new speed must be coming from this.
 
:- Intel graphics. For the first time under Karmic I have full effects on my external 19" LCD display running off my laptop. Previously on external display & laptop running together I had NO effects. Gnome-Do & Docky look great.

:- Everything feels faster and snappier. Boot is slightly faster.

:- Firefox 3.5. OOo 3.1. Google Earth text display is finally working. A lot of people had this problem with no fix.

:- The new notification systems is much better. Quite nice actually.


**The Bad**

:- I have always used an External VGA LCD display off my laptop. VGA was ALWAYS primary, laptop was secondary. I never had to set this (as I wouldn't have known how). Now however Laptop is primary and VGA secondary. With help of some others, I created a script which switched off both and reset Laptop as secondary and VGA as primary. (Searching this problem there are a good few others with this problem).
Until I rebooted, when it went back to the way it was. So I had to add the script as an Applet that I now have to run every time I restart. 
And then the applet only works about 1 time out of three. Both screens may not come back on, or may display garbage. Each time the script fails requires a logout. 

:- I was going to put the new Bluetooth Manager as good. Because the first time I ran it, it found my Nokia phone. AND I was able to open & explore the phone, a primary reason I've kept a Windows Dual-boot. BUT! yes but...when I actually came back to use it a second time and actually do some transferring, it found the phone again, but this time after communicating...nothing. No way to explore/transfer. Just like on Intrepid. Deleting the phone & finding again makes no difference. 


:- Media Monkey under Wine. First 24 hours ran great, faster screen refresh, to the extent I wrote some posts on Media Monkey thread in the forums. Today it only opens in mini-mode. Can't open the full screen. Restarting makes no difference. Thinking about nuking it but the WINE setup for MM was quite longish as I recall.

:- Panel applets seem to get screwed up. My Network Manger has been an almost completely blacked-out icon since install. Some panel applets occasionally seem to move position or display fragments without intervention. 

:-Customisation. I'm not talking about who likes or dislikes what colour or theme. But when you go into the theme chooser, why oh why isn't there yet a "Cancel" button so you can back out without changing anything? Please, hello, anyone?

:- System>Preferences>IBus Preferences. What the hell is that? Click it. You get:```
"IBus demon is not started. Do you want to start it now?
```  What. The. ****. 
Yeah, that'll really  help the average user. Just like "SCIM Input Method Setup", a great way to mess up your keyboard. 
What do we still have visible indecipherable options like these, and we're wasting time on "Ubuntu Software Centre"? 
I don't really care if *You* know what it is. I don't. And the system doesn't explain it.

:- Ubuntu One right now seems like a waste of time. It's kinda like Dropbox but with a worse setup, and not really what I want. I want to pick a few vital files, have them wherever it makes sense TO ME to keep them (like /home/documents/personal) and always have them updated to Ubuntu One. That's it. Online File backup & synchronisation. Otherwise, why bother? I've got plenty of hard back up.  (If Ubuntu One does, then it's still a fail as it's not obvious).

:- On the backup subject, it is BEYOND me why we continue to not have a reliable backup as standard in the Distro. Simple Backup was 5-starred/recommended in Ad/Remove previously, even though a) it had serious problems like filling your root to 100% b) it's officially dead. I dealt with SME backup in my last job, I've got a very good idea of the general requirements and most of the available options don't meet them.

:- Login Sound. Honestly. I needed Ubuntu-Tweak to switch it off now that Sessions is gone, which was where it was (still stupidly) previously.  Don't you think, I dunno, somewhere like System>Preferences>Sound might be a good place to put it? It's things like this that make wonder why 100 Papercuts wasn't 1000 Papercuts.


**The UGLY**

:- The new login screen. No, I haven't got the nice black new one. 
I've got a flat grey one that looks like it belong to Windows NT4 from 1995 and was cool, back then. And every time I get to it, I also get a tool-bar of language & keyboard options along the bottom. Why? Again, a lot of people out there have this login screen problem. After all, the nice new black one was visible when I tried the LIVECD. 
This is driving me nuts, since I'm restarting so much over the past few days but you may not care at all. Strokes for folks on this one.

:- Everywhere you went before people wrote "hey, you can customise EVERYTHING in Linux/GNOME". Well with GDM gone, that's no longer true. Keep your new Themes if you can't let <me> keep some of my customisation options, since I used my own theme anyway.    

:- I STILL can't arrange the icons on my Desktop as a simple small list view? Jesus ******* Montoya, hopping down O'Connell Street on a pogo stick as we used to say waaay back when requirements like this started to becomes obvious. Why ******* not? (No, the gconf settings that seem to, DON'T allow this.)



**_So where now?_**

I'm actually considering the Nuclear option and going back to Intrepid. But I'd miss the speed and eye-candy.
I haven't decided. 
If I can get help fixing the more glaring issues...*[FONT="Arial Black"]I'd love to stay. The neighbourhood is good & the folks next door seem nice and there's room for the dogs to play.[/FONT]*

I HATE the "x-release is not ready,it's a disaster" hysteria every time. This is my first ever "review" of a new release. 


Comments on a postcard please...

---

### Post by jheaton5 on 2009-11-06
[quote=Donalb]Yes, I know there's an Installation experience thread...[/quote]I'm sorry you are having this trouble with Karmic. Perhaps you should post this on that thread.  I suspect you won't get much help with this post because of the plethora of issues to resolve.  I suggest that you break your issues down into individual posts. If you do that people will be willing to tackle one issue but may not be willing to tackle many issues.  We all have other lives.

I have not experienced any of your issues.  In fact, I have done two fresh installs and one upgrade on three different machines.  They have been running over a week and I have had NO problems whatever.  I have to say thumbs up for Karmic.  But I do know that is not everyone's experience.  Good luck.

---

### Post by marin123 on 2009-12-04
THE UGLY:

about boot screen, this new one is really ugly, but you can download new xsplash screens and simply install it... i did and now i have pretty boot screen :)

---

### Post by cascade9 on 2009-12-04
> **Donalb said:**
> (I found it weird that people say wait for an LTS if you want stability, when 9.04 was so broken in the Intel graphics area. I lost faith in the LTS idea because of that)...

Just for your info, 9.04 isnt a LTS release. 8.04 and 6.06 are the LTS releases (and 10.04 will be when it comes out).

Aside from that, nice review, you've obviously thought about it, and posted exactly what your issues are. Good luck with whatever version you run. ;)

---

### Post by Lyleb on 2009-12-04
A LOT of work needs to be done for 10.04!!!!

---

### Post by Donalb on 2009-12-04
Update, 1 month later;

Well I stuck it out for the month and I've been submitting my few bugs, doing a few basic fixes where I could & seeing gradual improvements through updates. Things are much better now, 5 weeks after release, something I'll remember for next time!

:-The External VGA Display as Primary setting went back to where it was for the last few years about 2 weeks ago. I no longer have to run my script on startup. This is great and means much less resetting. 

:- System is more stable. Much more stable. Can't say if it was the kernel update that did it.

:- Haven't been travelling last few weeks, and since I'm wired at home,I haven't checked my wireless setting but I think there's been improvement here. Certainly I saw a bug fix that was supposed to fix the constantly having to re-activate the Broadcom STA.

:- Mobile 3G modem I sorted easily enough myself so I can't comment if it got an official fix.

:- There was also had the big bug with Nautilus hanging if Preview was enabled in folders where large files had been copied. This got a update bug fix this morning.

:- With Bluetooth I had to install Blueman since the default Bluetooth manager just wasn't doing anything. Blueman  worked a few times until it joined the ranks of the fallen a few days ago, refusing to allowing browsing of my phone. Haven't tried a reinstall yet.

:- Login screen. Nope, got nowhere on this. Have looked all over the place for solutions but nothing. No response to my posts on it. 
:-Also despite how easy it should be for some reason I can't get my alternative GRUB splash screen loaded.

:- Notification Area Applet icons. Problem went temporarily away if cycled Fn+F8 to cycle display modes. Problem went permanently away when I changed Icon theme.  

:- Gnome-Do hanging 100% of CPU, stopped after I disable the banshee plugin.

So I'm staying. I think the final decision came when the external display got fixed. Actually I guess the whole thing has re-affirmed my faith in OSS. 
If I was back on Wins, whether or not there was fix, it wouldn't be this transparent. But I'm also pretty sure that the issues like Display, Wireless & nautilus wouldn't have been fixed so quickly either. 
This process reminds me of the power the ordinary Linux users have to submit bugs, discuss with those responsible for investigating and fixing, also submit ideas, and even tell others why something still annoys us, and get help from others in the community.

By xmas I think I'll be ready to start installing Karmic on the older machines of those I have still on Intrepid.

Thanks to one and all of the people out there working to fix all these issues.

---

