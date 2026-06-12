---
title: "Dell Vostro 5470 low audio output: POSSIBLE FIX"
date: 2014-10-19
forum: Hardware
---

### Post by Azshaari on 2014-10-19
Hello all :)
Hopely, this post will guide the lost wandering souls with bad audio out there.

First of, let me preface this stating a few things:
Im new to the ubuntu community as well as to ubuntu as a daily driver OS.
I have some experience handling console and common tasks, but otherwise im a complete newbie.

Secondly,  i am really really sorry if this post is not supposed be here. I've  been searching the Dell specific forum for a while but realized it was  going to be shut down soon. Ergo the closest near convergence point for  doubts about a particular laptop handling ubuntu should be here. If im  wrong, i insist, im really sorry.

And my point :)
Since most  people i read at the Dell forum are experiencing this same issue, I  wanted to create a new post because I stumbled upon a possible solution.
I  started reading some of the ALSA talk about how in this particular  model (vostro-5470 and possibly 5460 too) does not handle the jack pin  assignment correctly.
This laptop has and integrated subwoofer and  pretty decent forward speakers, using the ALC290 Realtek solution. In a Windows environment there are  several tools to handle the subwoofer in a GUI so sound is amazing over  the microsoft side of things (MS visual studio forces me to use windows).

Just  now I have applied a few changes. Half an hour ago I could barely listen  Youtube or VLC (both correctly configured) even at max volume. I used a  few commands on the alsa terminal and it stated I was using just mono  sound and no subwoofer was present. Right now im rocking at 70's Judas  Priest like a boss.
As I said above, the alsa talk took me to a  commit where I found a packages specific for this laptop, listed by  ubuntu and kernel versions.

I'd like to state that Im in no way  knowledgeable enough as to create such a driver for myself, nor even  assert if it works as intented, but it gives a significant upgrade over  the default experience. Also, I do NOT claim any part in the creation of  these files.

_Other posts around the same issue:_

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1211920](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1211920)    (post #40 by Mr. David Henningsson)
[http://ubuntuforums.org/showthread.php?t=2152776](http://ubuntuforums.org/showthread.php?t=2152776)

Run the following command:
sudo apt-get install dkms

Then download the correct files:
(please note that it is necessary to know which Ubuntu version you have. Be mindful of that)
[Solution]("https://code.launchpad.net/%7Eubuntu-audio-dev/+archive/ubuntu/alsa-daily/+packages")


Hope this helps guys, and infinite truckloads of gratitude to the fellows who managed to catch the issue code-wise.

_____________________________________________________________
UPDATE (oct-20):

I have noticed a few things: 
1. If using VLC player you must select PulseAudio Sound Server. This is accessed via the Tools menu > Preferences > Audio.
Why you cant use other settings is beyond me.

2. It results quite useful to use the Gnome ALSA Mixer, since it gives manual GUI control over your devices outside terminal environment.
You can get this tool searching via the Software Center.

3. For 5470 with 14.04.1 users, I have found that the Ubuntu sound settings recognize two devices: Analog Out and Speakers separately. For some odd reason, switching between these two seems to disable subwoofer momentarily, so I advice not to fiddle too much in that area for everyday use. It still isnt a good solution but hey, its something.

---

