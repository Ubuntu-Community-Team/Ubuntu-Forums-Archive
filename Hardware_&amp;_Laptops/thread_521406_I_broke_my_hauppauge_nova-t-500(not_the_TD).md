---
title: "I broke my hauppauge nova-t-500(not the TD)"
date: 2007-08-09
forum: Hardware &amp; Laptops
---

### Post by davidbattley on 2007-08-09
hi i've been experementing with fedora7 and ubuntu7.04 and some how ubuntu (ok it was me but  kinda i think but i'm very upset and it's easy to blame the os) broke my card . 
I'm triple booting because i was disapointed with the lack of mheg capable dvb software on windows so i thought i'd give linux a try. 
Anyway i couldn't get the card to load in ubuntu for a long while but i was happy enough using vista . i thought i'd give fedora a try and the card worked first time of asking no problems (apart from poor signal compared to mce ad fedora was unstable for me). 
Anyway having i noticed an odd quirk when ever i booted to vista (after having used fedora), mc would tell me there was no tuner but all i had to do was reselected them in task> settings et voila the card worked. well any i decided to boot in to ubuntu(having just shut down fedora) and low ad behold the card also worked brilliant! acept the same poor image qualitys compared to mc. so i thought ok you gave it your best and booted back into vista but this time the little reslected the card tricked didn't work the signal was just really poor and it wouldn't work again until remove the drivers and card then re installed them. 
Unfortunatley i did'nt learn my lesson and the next time i was using ubuntu i tried to watch tv and disater the card wasn't there(In dmseg |grep dvb) . so i though oh well i'll try vista but now the card gave me no signal on any channel and  disapeared ( dmesg |grep dvb) when i tried to use it in fedora.I get no signal what so ever.  so far i've tried the following :-
.uninstall & reinstall driver in windows

.uninstall driver and hardware shutting down and restarting without the card then with the card and reinstalling drivers

.both of the above with the old new and beta drivers
.reinstalling on ubuntu but not fedora yet

reload the card in fedora and ubuntu with modprobe the card is back but there is no signal in any OS

The linux howto all involve loading firmware I hope this hasn't bricked the card please someone tell me it can be fixed. Windows finds the card in mc wintv2k and progdvb but when i scan it gives me no channels the aerel and recption in my area is ok i've tried them on a TV. the how to to is the one here [http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI](http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI)
the firmware version on the site is diffrent to the one i used up until yesterday when after several hours of no joy i tried reinstalling the card in ubuntu with old and new firmware.
please i beg you some tell me it can be fixed i've googled day and night since monday and no one else has reported the problem which kinda makes me think i'm f*$!ed
oh bye the way the card gives no error message in vista mc  ubuntu/ fedora  mythtv and it gives zero signal on either tuner

---

