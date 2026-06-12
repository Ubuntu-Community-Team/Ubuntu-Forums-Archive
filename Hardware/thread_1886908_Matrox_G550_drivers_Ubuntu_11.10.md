---
title: "Matrox G550 drivers Ubuntu 11.10"
date: 2011-11-25
forum: Hardware
---

### Post by misterblobby on 2011-11-25
Hi,

Does anyone know how to get the proprietary drivers installed on 11.10? The download comes with an install script, but says the driver is not supported with this version.

The default driver that installs with Ubuntu works fine most of the time, but won't run minecraft, which shuts down after going through he login process.

Thanks.

---

### Post by jerrrys on 2011-11-27
I have one of these cards and tried it while 11.10 was in alpha with no luck.  It ran gnome-classic, but nothing more.  So it found its way back to the scrap box, but I also would like to use it somewhere.

As far as drivers go, it ran on the generic drivers ok.  Matrox has a linux driver available for this card, but it has not been updated since something like 2005 so I did not even bother to try it. 

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Matrox&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Matrox&sa=Search&cof=FORID:9)

---

### Post by linas on 2011-12-10
FYI, I went to download the matrox "proprietary" drivers for the g550, and was surprised to get a tarball of source code, dating to 2005. I conclude that matrox is just not maintaining the drivers any longer.

---

### Post by linas on 2012-03-16
Update: I was never able to get my Matrox G550 to work. From what I can tell, my card is too new for any of the existing linux-Matrox drivers.  I think the problem is because my card has two DVI connectors; I think that there is some video-out chip that has to be told to send output to the DVI ports, instead of the (non-existent) VGA connectors.

The reason I suspect this is that, in fact, X11 and the full desktop does start, and does run, but the screen stays completely blank!  I know this because 1) it makes the usual desktop-starting sounds 2) I can very cleverly but blindly start a web browser, go to youtube, and start a video.  I get sound from that video; but the desktop stays utterly blank.  So that must mean that the graphics works, but the video feed is just not going to the connectors.

As I'm a kernel hacker, and a once-upon-a-time X11 graphics programmer, I tried to see if I could hack the device driver, but no luck, I could find nothing to control the video.  So now I own an expensive, useless card :-(

---

