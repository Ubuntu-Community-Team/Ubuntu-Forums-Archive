---
title: "Just some non sense"
date: 2009-11-04
forum: Installation &amp; Upgrades
---

### Post by hgraham on 2009-11-04
My experience upgrading from 9.04 to 9.10.  Several problems occurred.  The major problem  was the inability to connect to the internet after update and/or fresh install.  The following mitigated the problem

sudo pppoeconf (follow the defaults)

sudo pon dsl-provider

You get no panel icon showing you are connected but I was connected.  I await a formal fix.  To log in after shutdown you must use

sudo pon dsl-provider

The second major frustration was with wine.  I have an old program Bookshelf98 that I like.  It installed fine in 9.04 with what I suppose to be wine 1.0.  I went through the same install with 9.10 and wine 1.2.  The problem was that I expected my win program to show up in applications/wine/programs like it did before.  But I discovered it is now located in applications/other  Who knew?  Many things are better in 9.10 but these were my problems.

Does anybody know?  I like to listen to shoutcast and live365 (old time radio)  These sites seem to like xmms audio players.  To listen well, I need a player that I can increase the default audio buffer, I need an equalizer and I need a player that will automaticly reconnect to a droped stream.  In windows my best bet was itunes.  Does anybody know if there is an xmms player or something as suitable to listen to streaming shoutcast and live365?  Any suggestions will be greatly appreciated.  

Thanks for your attention, It has been great fun installing the upgrade

Howard

---

