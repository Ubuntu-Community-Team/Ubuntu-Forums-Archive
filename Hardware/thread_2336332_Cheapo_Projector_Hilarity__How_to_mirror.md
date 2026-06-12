---
title: "Cheapo Projector Hilarity : How to mirror?"
date: 2016-09-07
forum: Hardware
---

### Post by nickTaylor1181 on 2016-09-07
Hi all

A while ago I accidentally bought one of these off Aliexpress

[http://www.trademe.co.nz/electronics-photography/projectors-screens/projectors/auction-1157123068.htm](http://www.trademe.co.nz/electronics-photography/projectors-screens/projectors/auction-1157123068.htm)

An [COLOR=#333333][FONT=Helvetica Neue]Android 4.4 Mini DLP Projector... fairly impressive in various ways.

[/FONT][/COLOR]Somewhat less impressive, is that (I think) they've installed an android OS on it (4.4.4), which is designed to work with a touch-screen/mouse... and this thing has a kind of 4-button joystick - left/right/up/down/enter/back/menu. So it's got the full compliment of android apps, hardly any of which work, because there isn't a touch-screen/mouse.

What I was looking for was a projector - which I could plug into my laptop to use as... well... a projector. Either a mirrored screen, or an extra monitor. 

Instead there seem to be a number of Mirroring Programs, all of which require windows/apple. I have never used any of these before, but as far as I can tell, they are:

1) Eshare
2) Miracast
3) Airplay

Does anyone know how to mirror my (ubuntu) laptop to the projector using any of these? Or better still, use the thing as a 2nd monitor?


Any help much appreciated.

---

### Post by TheFu on 2016-09-07
Connect an hdmi output from the laptop to the projector.
Run **lxrandr** and enable the projector (hdmi) video output.
Enjoy.

Hopefully, the hdmi output resolutions will auto-pick what the projector supports. If not, try the 60hz 720p and 480p output resolutions. Those are pretty universal.

---

### Post by nickTaylor1181 on 2016-09-10
Hiya - thanks for your reply.

When I run lxrandr it appears only to detect the laptop monitor itself... there's only one screen detected.

[http://weirdsky.com/miscImages/temp/Screenshot.png](http://weirdsky.com/miscImages/temp/Screenshot.png)

there is an HDMI cable... I'm not sure if this makes a difference, but the HDMI port on the projector says "HD Out".

I suspect quite strongly that someone has made the amazingly bad decision not to provide any way of actually using a wire from a computer to use the thing as a projector.  I think they've imagined it would drive the TV it's connected to via HDMI, and the only way of using it as a proper projector is to use some sort of wifi mirroring software.

And I can only find windows/apple versions of this software.

Unless I've got that completely wrong of course. That's how it looks from here though.

So... does anyone know how to get:

1) Eshare
2) Miracast
3) Airplay


To work with Ubuntu?
[COLOR=#000000]

[/COLOR]

---

### Post by TheFu on 2016-09-10
Ah. A projector that isn't just a projector. Hummmm.

It claims to run Kodi, so load that onto the device and use any DLNA server (Plex?) or shared storage (NFS preferred, but CIFS can work too) and go to town.  I've been running Kodi on a R-Pi v2 over a year. Works well teamed with PlexBMC addon.

---

### Post by nickTaylor1181 on 2016-09-11
Yea - bizarro. I can't believe they invented a projector that doesn't do the only thing that projectors normally do. It's basically a crippled cell-phone but with the ability to like... project.

I can share drives etc... I can access the "projector" file-system with the laptop - but what I'd like it to be able to do is stream youtube videos - but using the laptop as a controller because using a 2-axis remote controller to try to navigate the internet is a recipe for insanity.

Does the DLNA / Plex thing allow for streamed video?

---

### Post by TheFu on 2016-09-11
I have a firefox browser addon that is basically "Send to Kodi."  That works with youtube. It doesn't work with the Plex media server web interface - think that requires a plex online account to work (which I don't have and don't want).  There are lots and lots of kodi remote control apps for android too. I'd think those work well. I use the free Bubble UPnP app on a tablet for controlling DLNA stuff (servers AND clients) in the family room, but in another room, a normal WMC Remote is used with R-Pi running Kodi.

---

