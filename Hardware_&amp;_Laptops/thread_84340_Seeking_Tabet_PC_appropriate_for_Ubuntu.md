---
title: "Seeking: Tabet PC appropriate for Ubuntu"
date: 2005-10-30
forum: Hardware &amp; Laptops
---

### Post by duus on 2005-10-30
hi.  i want to start looking around for a tablet pc that I can install ubuntu on...so before I start I just wanted to know any suggestions.

What I want:
i want a full-sized tablet with the touchscreen or stylus input that works.  I want wifi. 

what i don't need;
it doesn't need to replace my main machine--i just want something to carry around as a glorified pda kinda thing, editing documents, reading pdfs &c.  doesn't need keyboard or the rotating screen or anything.  simple, simple, simple.

any thoughts/success stories?  thanks.

---

### Post by bb002 on 2005-10-30
I think no matter the laptop there is going to be a bit of work involved to get everything working.

I have a Gateway Tablet M275 running Ubuntu 5.04 Hoary Hedgehog. I had to manually add the proper xorg lines which was easy, it was figuring out where the tablet was located that was a real pain. Most faqs talk about USB tablets only and the few that talk about serial tablets (which is what the m275's tablet is) only refer to /dev/ttyS0. It must be assumed that you'll try /dev/ttyS1 and so on but for a noob you must explictly tell them to try other serial ports. Took me there weeks before I found my tablet on /dev/ttyS1.


The ipw2200BG driver that comes with 5.04 works for WEP but WPA support isn't in the hoary's version.  I had to follow a HowTO located on this forums on how to manually update the ipw220BG driver to support WPA.

Now the only problem is getting a ON-Screen Keyboard working. tried GOK but it only loads after you login. I need one before i login. Basically I want one exactly like the On-Screen keyboard for windows xp tablet edition. So far I haven't seen anything like windows keyboard for linux.

Well I have no use for any of the tablet buttons so i have no idea if they work or not.

Overall I'm really liking Hoary on my M275. 

I tried Breezy but it broke many of the things that worked just fine in hoary. I revert back after a week of fussing around. I reverted because breezy had broken more than it had fixed (to be honest i haven't found anything yet on what it was fixed) and i still had no idea what else had broken since i couldn't get all the hardware to work. Here's the detail's my breezy experience: After installing breezy, no matter what i did the Xserver always defaulted to the external monitor port and shuts off the LCD. I had to press the function key and f3 to get the LCD to come on. Had to add HorizSync and VertRefresh to the monitor section of xorg.conf to get any resolution besides 640X480. During the installation the ethernet card was detected and configured but once installation was completed the ethernet card was no longer configured and trying to configure it with the networking tools failed . The wireless card wasn't detected by breezy at all. If this much had been broken hardware wise, I didn't want to even try to guess how much was broken software wise, especially since i had something that worked already.

I gave breezy the benefit of the doubt and tried it on my desktop with the same poor results. Hoary worked great other than I watch a lot of videos and hoary had issues playing some of them without the video and audio going out of sync after two minutes. breezy had this issue, too. Mandriva 2005LE played these files without trouble. My desktop is custom built and the only piece of hardware that doesn't have full linux support is my ati radeon 9200 AIW, i was suckered in by the box's label claiming linux support when in reality the linux drivers treat the card as a generic radeon. boo, ATI, boo. the video card happens to be the only piece of hardware that breezy detected right, even if it was only seen as a generic radeon. the onboard gigabit ethernet wasn't found (don't use it but it still was found) and the onboard sound was configured improperly (after fooling with the mixer setting i finally got the popping to stop when ever a sound was played). My 512MB jumpdrive wasn't reconized but on the m275 it was seen just fine (don't really understand that at all) but other usb devices were seen just fine.

---

