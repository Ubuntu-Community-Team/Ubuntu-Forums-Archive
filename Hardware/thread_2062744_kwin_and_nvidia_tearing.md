---
title: "kwin and nvidia tearing"
date: 2012-09-25
forum: Hardware
---

### Post by manorba on 2012-09-25
Hi everybody, this is my first post

i have been struggling lately with tearing both on desktop and video. i had cured it a while ago but it popped up again with the latest kubuntu update to 12.04 64bit.

this is my relevant setup: gtx 660 ti with 304.51 drivers, kwin 4.84, twinview set to clone between my main monitor and a hdtv (set to the main monitor resolution 1680x1050 but with refresh on auto).
nv-settings has vsync enabled everywhere (on the main monitor) and kwin settings has vsync on too together with 2.0 shaders and unredirect full screen.
As video player i have kmplayer and vlc both configured to take advantage of vdpau.

with these setting i managed to get rid of most of the tearing. what remains is a strange tearing effect that  happens only on the upper 1/5 of the screen or so. it is pretty noticeable if you jerk a small window around and in videos, and lately i found that this happens ony when the PoweMizer is set on "adaptive" and the card is running on slowest settings. switching to "max performance" cures the problem. But this is not a viable solution, as the 660ti is a pretty power hungry card and i'm not comfortable with it running at max setting on default. i've made some cross checking with a win7 64 bit partition where it works flawlessly even in adaptive mode.

is there a way to report a bug directly to nvidia linux developers?

ps. sorry if the issue has been already solved but a previous search in the forums achieved nothing. 

thx
manorba

---

### Post by rusty725 on 2012-11-19
Hi
have you solved this problem ? I'm having the same issue. tried all kind of drives on ubuntu 12.10 with several kernels.

---

