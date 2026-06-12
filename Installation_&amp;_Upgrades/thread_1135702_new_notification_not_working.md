---
title: "new notification not working"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by everytimeref on 2009-04-24
Hi,

I've upgraded from 8.10 to 9.04 and found that the new notifications are not working.

notify-osd is installed and shows as running in system monitor but doesn't seem to do anything.

Where are the Notify preferences???

---

### Post by ricardogorayeb on 2009-04-24
i am with the same problem... somebody can help us?:(:(:confused::confused:

---

### Post by Zyphrexi on 2009-04-24
I typed 'notif' then tabbed to see what popped up. It's notification-properties that you should be running. currently on my box (which isn't fully updated) no matter where I tell it to put the notification it's always in the top right corner. 

remember kiddies... type and tab are your friends. =) GL ppls

---

### Post by Wandering Wombat on 2009-04-24
This thread may interest you, there are a few options discussed

[http://ubuntuforums.org/showthread.php?t=1122292](http://ubuntuforums.org/showthread.php?t=1122292)

---

### Post by everytimeref on 2009-04-25
Thanks guys these replies were really useful that "type and Tab" thing is going to be invaluable.

I wasn't actually talking about update notifications, but since reading that thread, have reverted back to the old icon anyway: I removed the lower panel in favour of a Cairo Dock so I'm not even sure if I'd see a minimised window! 

The smoky glass notifications seem to be working now (although the only notification I've had so far is when Rhythm box changes track and I've got a funky plugin for that anyway!)

The volume notification tray icon is also interesting, in intrepid you could just roll your mouse over it and use a scroll wheel to change the volume, now you have to click on it first (like in windows!) before you can change volume. It's a very petty distinction I'll admit but it's those wonderful usability tricks that make Ubuntu such a joy...
There are a couple of things in Jaunty- the volume applet being one, the Smaller launch progress bar another, that make me think that ubuntu is catering a bit more for laptops as opposed to pure desktops. That isn't a criticism as much as an observation.

---

### Post by diafanos on 2009-04-25
> **everytimeref said:**
> 
The volume notification tray icon is also interesting, in intrepid you could just roll your mouse over it and use a scroll wheel to change the volume, now you have to click on it first (like in windows!) before you can change volume. It's a very petty distinction I'll admit but it's those wonderful usability tricks that make Ubuntu such a joy...


I don't think so...
I can use my mouse wheel to increase/decrease volume.
Just hover over volume icon and use the wheel.
It works perfectly (for me at least):)

---

### Post by everytimeref on 2009-04-25
> **diafanos said:**
> I don't think so...
I can use my mouse wheel to increase/decrease volume.
Just hover over volume icon and use the wheel.
It works perfectly (for me at least):)


Yes, you're right!, it's just the volume bar that doesn't appear. Sorry Ubuntu:redface::redface:

---

### Post by chrisinspace on 2009-04-25
The new notification system isn't working for me at all.  I still have the old Intrepid-style notifications.  I have tested with Network Manager and Rythmbox, both of which were supposed to be integrated into the the notification system.

---

### Post by diafanos on 2009-04-25
> **chrisinspace said:**
> The new notification system isn't working for me at all.  I still have the old Intrepid-style notifications.  I have tested with Network Manager and Rythmbox, both of which were supposed to be integrated into the the notification system.

They are integrated into the notification system, so you probably have to see them. Sometimes notifications are not working with my rhythmbox, either.

Did you check if notifications are at least working properly with pidgin?


**[out-of-topic mode on]**

I didn't know that there is a city in USA called Alexandria, also.
I'm quite impressed:-P:-P
Do you know how its name came from?

**[out-of-topic mode off]**

---

### Post by raiwo on 2009-04-25
i don't get 'new updates are available' notifications, did a fresh install with 9.04 beta and there has been several updates since but no notifications even once!

---

### Post by FokkerCharlie on 2009-04-25
My notifications aren't working- when I run notification-properties in a terminal, choose 'preview', I get the following message


Error while displaying notification: Message did not receive a reply (timeout by message bus)

I'm still stuck with the old-style notifications!  Any ideas?

Charlie

EDIT: SOLVED!

sudo apt-get install notify-osd did the trick for me.  Don't know why the upgrade didn't sort this out, but there you go.

Toodle-pip!

Charlie

---

### Post by chrisinspace on 2009-04-26
> **diafanos said:**
> They are integrated into the notification system, so you probably have to see them. Sometimes notifications are not working with my rhythmbox, either.

Did you check if notifications are at least working properly with pidgin?


**[out-of-topic mode on]**

I didn't know that there is a city in USA called Alexandria, also.
I'm quite impressed:-P:-P
Do you know how its name came from?

**[out-of-topic mode off]**

I haven't tried Pigdin yet.  I'll give that a shot.

To answer your off-topic, we are one of the oldest cities in America.  George Washington's home, Mt Vernon is actually here.  I can't imagine any other source for the name than Egypt.

---

### Post by diafanos on 2009-04-26
> **chrisinspace said:**
> 
To answer your off-topic, we are one of the oldest cities in America.  George Washington's home, Mt Vernon is actually here.  I can't imagine any other source for the name than Egypt.

You' re absolutely right, but Alexandria of Egypt is one -the most famous- of many (at least 20) cities that have been founded by the Greek king, Alexander the Great.
There is an Alexandria city in Greece, too...

(Sorry for the off-topic, but I'm too proud of my ancestors, to not mention this :-))

---

### Post by chrisinspace on 2009-04-26
> **FokkerCharlie said:**
> 
EDIT: SOLVED!

sudo apt-get install notify-osd did the trick for me.  Don't know why the upgrade didn't sort this out, but there you go.

This worked for me, too.  Strange that the upgrade didn't include the component automatically.  Thanks to everyone for your help.  The new notifications look great with my theme.

---

