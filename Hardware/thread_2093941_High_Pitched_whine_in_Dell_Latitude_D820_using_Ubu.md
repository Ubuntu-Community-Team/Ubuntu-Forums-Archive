---
title: "High Pitched whine in Dell Latitude D820 using Ubuntu 12.04"
date: 2012-12-12
forum: Hardware
---

### Post by Bhairava on 2012-12-12
Hello everyone,

I have a Dell Latitude D820. I am running Ubuntu 12.04. I removed Windows 7 completely (It was running fine then).
There seems to be a very high pitched sound coming from within the chassis.
This is not a speaker or a fan sound. Sort of a car horn that has been turned down in the background but held in place with a glue tape.
I tried the tweak at the support.dell.com website (the c3 state thing). 
It did not go away.
I observed that whenever I scroll (firefox only mostly using the touchpad or the arrow keys), the sound stops.
Also, when there is flickering of the the second LED light in between the power and the battery light (in the shape of a bin? I think a read or something) the sound stops.
I read blogs about c3 states which had switching off the Bluetooth Radio (I switched off the Bluetooth), removing USBs (There weren't any but I tried removing all attachments and also pretend removing :D ) but it doesn't seem to go away.
I have a pretty old laptop and they talked about motherboard fixes. 
I have to stick with this but the sound is like a portal for torment.
I really don't care if my laptop battery dries up in a minute, I could connect the AC adapter but I really need help from this .

I would really appreciate it if you could recommend something. 

Thanks !

---

### Post by Bhairava on 2012-12-14
Hello everyone,

Is there anyway this can be prevented? There must be someone who tried something wacky (hopefully something software related) and it worked fine. It's  really funny and I should be used to it by now but I am listening to music when I work so that I cannot hear it and I am fed up of that too.
I would really appreciate some help.

Thanks again !

---

### Post by Bhairava on 2012-12-15
The solution that worked for me has been underlined if you want to skip the whole story. :)

Ok. In my case, I think I may have found a work around.

I observed that the whine occurs only when there is no application running or when it has finished. So for example in the case of firefox, it may be open (which is running) but may not be fetching or getting data (that implies it is "not running" in this case).

I found that if you keep executing something making a fetch from a server or in the local machine itself, then the machine has no time to cry. (The genie who want to keep working).

So what I did was, [U]start Rhythmbox in the background (better than the whine). 
Then I realized that the whine stops even if you have the music muted which was wonderful. I had either last.fm or libre.fm up (based on the "fetch principle")[/U]; if I wanted to listen, I would unmute it or mute it if disinterested. 
It worked for me !

Hope it solves your problem ! Please post it if your solution works so that others can know as well ! ;)

---

