---
title: "HAL Fails to acknowledge .is_audio_player"
date: 2009-08-03
forum: Hardware
---

### Post by Imunalia on 2009-08-03
I am starting to think that the name is no coincidence...

I am gonna give some quick back story,

I have a mobile phone that I use to play music all the time and it gets its music off of a microSD card. I use a card Reader to sync to the computer because the smart phone gets grouchy. When I used windows I could sync the card as if it were a media player and all was good. In Ubuntu Jaunty I have tried to sync with RythmBox and Banshee. Banshee being the preference as it has smart playlists that I can configure perfectly to fill my card up. Now to the problem, I learned quickly that hal will not see the card reader as a media device unless I tell it other wise. So I created the .is_audio_player on the memory card ejected it then reinserted and all was good. Flash ahead two months to now, I am tired of my music and want to load some new tracks onto my card so in I pop the card w/ reader and launch Banshee. It no longer see's it.... So I view the hidden files on my card in order to find out what is amiss and notice that my phone must have deleted the .is_audio_player. So I recreate it and again all is good. I start to sync to the card again but I forgot to delete the original music so I quit Banshee and manually deleted the music then fired Banshee up again. Now nothing I have tried can make the device appear as an audio player to Banshee.

I have tried the following:

-Format the card with a new label
-Completely remove and Reinstall banshee
-Poke around in Hal's FDI to see if a rouge entry has been created for the device, natta

What I know:

My laptop picks up the card in banshee with out a single hitch, except the music collecting is not on the laptop.... I have no idea what else to try and I am open to suggestions. If you would like a more hand on approach I am willing to provide VNC information.

Jeffrey

---

### Post by Imunalia on 2009-08-05
Some more information.

I think I have narrowed the problem down a bit, it appears that the auto behaviour for my card has been set incorrectly, for this reason the device loads as a camera card. As soon as that happens it overides the .is_audio_player. How can I go about resetting the device to ask what to do. It doesn't appear in the nautilus preference for a media card. Just for CD's and other similar devices. I think I am on the right track just need some help.

Jeff

Quick Reply:

The problem seemed to have fixed itself....go figure....

---

### Post by Chronon on 2009-08-05
MSC detection in HAL has been broken for quite a while in Jaunty.  I believe a fix is expected in Karmic.

---

