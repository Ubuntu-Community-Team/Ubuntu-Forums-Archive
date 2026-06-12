---
title: "Hauppage HVR 1950 (win tv) problems"
date: 2009-08-30
forum: Hardware
---

### Post by greenwom on 2009-08-30
i have a desktop that i've tried mythbuntu on ant it installs great.

I add my tuner card and get nothing.  I added it as DVB (as many of the guides state).  Nothing works.  I reinstalled 9.04 and installed the firmware.  I know get /dev/Video0 and when I run xawtv it starts the card (I get the red led to light up).

So from this point what do I need to do to get this working in Myth?
Also I'm going to be running Boxee.  How can I use this remote in Boxee.  Boxee.  I've been messing around with lircd and haven't gotten anywhere.

I've google'd the tar out of this and need help...

documentation is strong on this one.

---

### Post by greenwom on 2009-08-30
Well after some digging and playing around HERE it goes

install irw and the lirc stuff from the repos

installed myth-control-center

used the hvr-1300 setting in the infrared tab

created a file Lircmap.xml in the boxee folder

```
/home/user/.boxee/UserData/Lircmap.xml
```

then got the right contents from this thread at boxee's forum

[http://forum.boxee.tv/archive/index.php/t-4784.html](http://forum.boxee.tv/archive/index.php/t-4784.html)

Here is the contents of the file

[HTML]<!-- This file contains the mapping of LIRC keys to XBMC keys used in Keymap.xml -->
<!-- -->
<!-- How to add remotes -->
<!-- <remote device="name_Lirc_calls_the_remote"> -->
<!-- -->
<!-- For the commands the layout following layout is used -->
<!-- <XBMC_COMMAND>LircButtonName</XBMC_COMMAND> -->
<!-- -->
<!-- For a list of XBMC_COMMAND's check out the <remote> sections of keymap.xml -->

<lircmap>
<remote device="Hauppauge_350">
<pause>Pause</pause>
<stop>Stop</stop>
<forward>Forward</forward>
<reverse>Rewind</reverse>
<left>Left</left>
<right>Right</right>
<up>Up</up>
<down>Down</down>
<select>OK</select>
<pageplus>Ch+</pageplus>
<pageminus>Ch-</pageminus>
<back>Back/Exit</back>
<menu>PreviousMenu</menu>
<play>Play</play>
<info>Menu/i</info>
<skipplus>SkipForward</skipplus>
<skipminus>Replay/SkipBackward</skipminus>
<display>Teletext</display>
<start>Go</start>
<record>Record</record>
<volumeplus>Vol+</volumeplus>
<volumeminus>Vol-</volumeminus>
<mute>Mute</mute>
<power>Power</power>
<myvideo>Videos</myvideo>
<mymusic>Music</mymusic>
<mypictures>Pictures</mypictures>
<mytv>TV</mytv>
<one>One</one>
<two>Two</two>
<three>Three</three>
<four>Four</four>
<five>Five</five>
<six>Six</six>
<seven>Seven</seven>
<eight>Eight</eight>
<nine>Nine</nine>
<zero>Zero</zero>
<delete>Red</delete>
<mymusic>Green</mymusic>
<mypictures>Yellow</mypictures>
<myvideo>Blue</myvideo>
</remote>
</lircmap>[/HTML]

Now boxee is working with the remote and it's the best :guitar:

---

