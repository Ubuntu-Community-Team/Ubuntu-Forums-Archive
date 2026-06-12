---
title: "jack stops youtube , netflix and any video from playing"
date: 2018-09-11
forum: Hardware
---

### Post by wavesound on 2018-09-11
Hi All
After using Studio for over a year I now have a problem.

If I start jack as I always due to control my FCA 1616 I cannot play you-tube or Netflix on FF or Chrome.
(It just sits there with a white circle going round, then asks me to restart my device)

If I stop or quit Jack I can play videos, But I get loads off popping and loud cracks from the system on every page.

This has only just started happening.

Last Update was a few nights ago, no idea what got updated.

Any help cheers Bob


Ok here is  how I stopped this happening:

Open QjackCtl "Setup" window, then click on the "Options" tab. Uncheck "Execute script after Shutdown: killall jackd". If you did not make this change, then QjackCtl would stop the JACK server from running every time the program quits. Since PulseAudio is still expecting to use JACK after that, you shouldn't do this any more.
****************
I'll check a reboot
No Idea how it got changed, must have been the last update.

Wavesound

---

### Post by wavesound on 2018-09-11
> **wavesound said:**
> Hi All
After using Studio for over a year I now have a problem.

If I start jack as I always due to control my FCA 1616 I cannot play you-tube or Netflix on FF or Chrome.
(It just sits there with a white circle going round, then asks me to restart my device)

If I stop or quit Jack I can play videos, But I get loads off popping and loud cracks from the system on every page.

This has only just started happening.

Last Update was a few nights ago, no idea what got updated.

Any help cheers Bob


Ok here is  how I stopped this happening:

Open QjackCtl "Setup" window, then click on the "Options" tab. Uncheck "Execute script after Shutdown: killall jackd". If you did not make this change, then QjackCtl would stop the JACK server from running every time the program quits. Since PulseAudio is still expecting to use JACK after that, you shouldn't do this any more.
****************
I'll check a reboot
No Idea how it got changed, must have been the last update.

Wavesound


Lol oK it now seems I have to start chrome then start Jack for this to work! Complete opposite off what I used to do.

---

