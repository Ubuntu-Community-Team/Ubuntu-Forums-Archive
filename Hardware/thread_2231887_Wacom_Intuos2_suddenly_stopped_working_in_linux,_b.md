---
title: "Wacom Intuos2 suddenly stopped working in linux, but works in Windows"
date: 2014-06-28
forum: Hardware
---

### Post by Cristiano_Pruneri on 2014-06-28
I have used an Intuos2 12x18 to build a self-assembled Cintiq.

It has worked perfectly for more than six months, on my Ubuntu 13.10.

All of a sudden, yesterday something was updated, and when I booted up the next time, it has decided that she doesn't like Linux any more.

The tablet is detected, the led on the table goes green when I click with the pen (and refuses to do so when I unplug and replug it, which I know it "breaks" the communication with driver - so at some level the driver and the table do communicate).

Xorg.0.log doesn't show errors connected to the tablet, as far as I can tell.

Evtest shows that the tablet sends plenty of events, and with the actual values for pressure, position, button push etc.

All almost undistinguishables from the event sent by my old Graphire3 - which works pretty fine, really.

In all, it seems to be perfectly installed and working, but linux refuses to move the cursor or actually acknowledge any event from it.

I tried xinput list, it detects the tablet and its three tools. So does the Wacom control panel.

I tried to see if it was a problem of updates, and to boot from from a 12.04 and a clean 13.10 cd (problem, I did download these images today... is it possibe that
they already include any update that may have broken the driver? That's a question)

I have no more ideas.

On another hand, the tablet still works perfectly well in Windows7, without any visible glitch.

I am pretty disappointed. I really need that tablet to draw.

Anyone has any idea?

---

### Post by Cristiano_Pruneri on 2014-07-01
Update: I have take another look at the evtest log, and it appears that the value for the MSC_SERIAL event is always 0, independent from the tool I use ( I have two grip pens and a mouse) to prod the tablet.

Now, I realise that protocol V instruments sends the serial number, but why can't ubuntu simply fall back to a degraded functionality, instead of losing completely the tablet? 

After all, if I can't program differently each different pen I have, it is a minor setback.

Not having the tablet is a major problem for me.

---

