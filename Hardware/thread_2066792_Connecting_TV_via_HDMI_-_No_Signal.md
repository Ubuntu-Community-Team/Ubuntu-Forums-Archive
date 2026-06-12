---
title: "Connecting TV via HDMI - No Signal"
date: 2012-10-05
forum: Hardware
---

### Post by stee1e on 2012-10-05
Just moved over to Ubuntu, liking it at the moment, but having a few teething problems.

My laptop (Dell XPS M1530) does not recognise my TV, when I was using Windows Vista I had no problems. Currently no video, no sound and is not recognised as a display under all settings->Displays 

Video card: Geforce 8600m GT - Current driver installed

Not sure what other info you would need

Help would be appreciated, thanks

---

### Post by Dale61 on 2012-10-06
I had a similar problem when I returned to Ubuntu.

My W7 laptop was used more often them not connected via HDMI cable, through my AV unit and then on to my HDTV.  Flawless.

However, when I tried the same with Ubuntu, nothing, nada, zilch.  One morning, having forgotten to pull the HDMI cable from the laptop, I fired it up into Ubuntu, and voila, suddenly I had a 'screen' on my TV.

I've since found that you have to connect everything BEFORE turning on the computer if you want to connect to a TV with a HDMI cable.  This may not be true for everyone, but it seems to be the case for me.

Try it and see what happens.

---

### Post by ahallubuntu on 2012-10-06
On my Dell laptop, to activate a second attached display, you use the Fn + F2 key to toggle modes (laptop display, laptop + external dual display, external display only).

I don't have any laptops that have HDMI, but I use HDMI all the time on two Ubuntu media servers connected to two TVs, and there is no issue plugging in the HDMI cable at any specific time.  It all works on both of them reliably and intuitively.

---

### Post by stee1e on 2012-10-07
Still having problems with the HDMI output.

When I plug it it, the HDMI channel on the TV freezes the last tv picture, splits it and it goes green.

Tried turning off the laptop and starting with it plugged in, no change.

Endless searches and I can't find anything to help 

ideas??

ta

---

### Post by BicyclerBoy on 2012-10-09
What video driver are you running?
The best soln is to use nVidia proprietary driver thru' jockey tool.

Your HDMI audio feed (if any) is S/PDIF feed via link cable from the mobo sound codec. 

There are useful logs to ponder over..
dmesg
cat /var/log/Xorg.0.log

---

### Post by eggsbenedict on 2012-10-09
Not sure if this helps or not, but with my ATI/AMD video card, I also had trouble with HDMI output at first.  Instead of going to Settings -> Displays, I had to play around with the Display manager in AMD Catalyst Control Center (CCC).  Here's what I'm getting at: with your card and latest drivers installed, check your applications and see if there is a Nvidia Settings application that is equivalent for your graphics card to what CCC is for mine.  Maybe someone more advanced than me will have an idea if anything like this is out there.

---

