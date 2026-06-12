---
title: "Weird Microphone Problems: Acer Aspire"
date: 2012-01-08
forum: Hardware
---

### Post by duncan12 on 2012-01-08
I know this has been posted before, however I have never been able to solve the problem.

On my Acer Aspire 5534, the built in microphone gives a fuzz and not the right sound. The temporary fix is:

Run ```
pavucontrol
``` and set the Output Devices (yes Output not Input, rather strange fix) to Front Left 0% and have Front Right up.

However this a) means my output volume is halved because it only uses the right speaker, and b) it sets itself back often so when using the microphone I have to constantly put it back to the Front left 0 and Front right up as it decides to change it back to both left and right being locked together (ie at the same volume).

I really don't understand why the Output balance has anything to do with the Input working, but there you go...

There is definitely no problem with the microphone itself - it worked way back then with windows, and it works fine during the time that temporary fix is in effect.

Side note: I have got it to work before with a bluetooth headset. However I'm wanting to use it with the built in microphone and the built in speaker.

So I'd like a fix that allows me to use my speakers as normal, and that has the microphone working.

It's kind of a hard problem to explain all the detail of, and if anybody wants more information about my setup that would be good.

Thanks in advance for any ideas.

---

### Post by duncan12 on 2012-01-14
Does anybody else with an Acer Aspire laptop have this problem? Does anyone have a possible fix? I don't know much about the Linux sound system...

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-01-14
Maybe this thread could help:

< [http://ubuntuforums.org/showthread.php?t=1579600](http://ubuntuforums.org/showthread.php?t=1579600) >

Please note that hasanarbab and I have different Acer models than yours, and that we had problems in Skype only. However, it's worth trying, because it fixed my problem.

---

### Post by madvinegar on 2012-01-14
I had the same problem in as acer aspire one 250 and I did the following to fix it.

Try to switch off one of your two speakers by setting the sound balance far left or far right.
If your mic will work, then download and install from ubuntu software center the "pulse audio volume control".

Open it. Go to the 4th tab (input devices), press the little button with a lock on it (so as to unlock the two channels from moving together), and switch off completely one of the two channels.

You can then set back your overall sound balance as it was before so as to get sound from both of your speakers.

This should do the trick.

---

### Post by duncan12 on 2012-01-14
@&#1058;&#1086;&#1084;&#1080;&#1094;a and @madvinegar Yes, I can get it to work by setting the Input as Front Left 0 and Front Right up, however the sliders seem to want to move themselves around. The fix works... but only for a little bit until I start to get either crackling or fuzz again.

> **&#1058 said:**
> Just wondering, does anyone know why this happens? Apparently, that's an Acer-specific problem, but what I don't get is why I have left and right channel for adjusting the input volume in Pulse Audio Settings, when my laptop has only one built-in microphone?
Yeah, it seems like there's the real microphone on the Left balance and some fuzz on the Right balance. I guess that's why there's the real noise coming through, however fuzz always wants to overtake it.

I'm very confused... I just need a way to make the sliders stay where I put them and not "auto-correct" themselves. I think that's what I need to do anyway, that would make the temporary fixes mentioned a more long-lasting fix.

Thanks for your help, but I still can't get it to work for more than a minute... :mad:

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-01-15
> **duncan12 said:**
> However the sliders seem to want to move themselves around. The fix works... but only for a little bit until I start to get either crackling or fuzz again.

That should happen only if your Skype is set up to automatically set volume levels for you. Go to Skype Options > Audio Settings and there uncheck the tickbox that lets Skype automatically adjust the volume. Let us know if that helps.


> **duncan12 said:**
> Yeah, it seems like there's the real microphone on the Left balance and some fuzz on the Right balance. I guess that's why there's the real noise coming through, however fuzz always wants to overtake it.

The noise doesn't come from any particular channel, because it doesn't matter whether you set left to 100% and right to 0% or left to 0% and right to 100%. The problem only seems to occur if both channels' volume is up. Pretty weird if you ask me, especially having in mind that there's only one built-in physical microphone on the computer.

---

### Post by aleoo on 2012-01-15
> **madvinegar said:**
> Try to switch off one of your two speakers by setting the sound balance far left or far right.
If your mic will work, then download and install from ubuntu software center the "pulse audio volume control".

Open it. Go to the 4th tab (input devices), press the little button with a lock on it (so as to unlock the two channels from moving together), and switch off completely one of the two channels.

Hi all..I was reading some forums and this thread caught my attention.
I tried to fix the problem in the way described above, but nothing changed: I always hear white noise instead of my voice when I execute the Skype test.
Can anybody help me? I posted some info in this thread for troubleshooting: 

[http://ubuntuforums.org/showthread.php?t=1908893](http://ubuntuforums.org/showthread.php?t=1908893)

---

### Post by aleoo on 2012-01-15
My internal mic does not work with sound recorder neither, 
even if I care more about let other skype users listen to my voice.
I also have Pulse Audio installed.
I need help!

---

### Post by duncan12 on 2012-01-15
> **&#1058 said:**
> That should happen only if your Skype is set up to automatically set volume levels for you. Go to Skype Options > Audio Settings and there uncheck the tickbox that lets Skype automatically adjust the volume. Let us know if that helps.My problem is not Skype specific, in fact I don't have Skype installed. 



> 
The noise doesn't come from any particular channel, because it doesn't matter whether you set left to 100% and right to 0% or left to 0% and right to 100%. The problem only seems to occur if both channels' volume is up. Pretty weird if you ask me, especially having in mind that there's only one built-in physical microphone on the computer.
My problem seems slightly different - its seemingly changing the Output Volume balance that lets the microphone sound come through, and it only works one way round,  if the right is up and left is down but not vice versa.

Im away for the next 5 days (wrote this from my phone) so can't get system info and might not answer posts,  but hopefully others with the same problem keep the thread going

---

