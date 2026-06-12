---
title: "DVB-S2 HD channels scanning not work"
date: 2014-04-30
forum: Hardware
---

### Post by Chicheportiche_Dan on 2014-04-30
Hi,
I install tvheadup and after 3 days all work.
I have understand how it work. I have my oscam with my cccam to descramble the channels, and I see all channels on VLC and XBMC well.
But I have a problem (a big one), I think it's a bug.
All the multiplexes with DVB-S2 and 8PSK don't detect any channels.


For example :
I had these multiplexe manually (because automatic don't work to) and this detect no channel (no error in logs):
Astra 19.2 - 12012V - 29700 - 2/3 - DVB-S2 - 8PSK	
Hotbird 13.0 - 16681H - 27500 - 3/4 - DVB-S2 - 8PSK	
But if a channel is on a DVB-S QPSK multiplexe it work well for example MTV Live HD :
Hotbird 13.0 - 11075V - 27500 - 3/4 - DVB-S - QPSK	


I test on my Technisat SkyStar USB 2 HD CI and with this different configuration and it's the same bug :
1/ Raspberry PI + Raspbmc
2/ PC + ubuntu x64
3/ PC + debian i386


My card is recognised as STB0899 Multistandard on tvheadend but the dmseg log know it real name :
dvb-usb: found a 'Technisat SkyStar USB 2 HD CI' in cold state, will try to load a firmware
dvb-usb: found a 'Technisat SkyStar USB 2 HD CI' in warm state.
DVB: registering new adapter (Technisat SkyStar USB 2 HD CI)
dvb-usb: Technisat SkyStar USB 2 HD CI successfully initialized and connected.


I make the w_scan and scan and it's the same problem, it detect all channels except channel on DVBS2 multiplexes.


When I go on windows with the same PC and the same card with ProgDVB, all work fine and the HD channel are detected.
When I connect the dish on my dreambox all work fine too.


I think this is a driver problem so I update v4l with SVN but the same problem.


What can I do ?


Thanks

---

