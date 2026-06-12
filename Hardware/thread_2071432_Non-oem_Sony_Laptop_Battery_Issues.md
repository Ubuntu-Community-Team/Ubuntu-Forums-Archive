---
title: "Non-oem Sony Laptop Battery Issues"
date: 2012-10-15
forum: Hardware
---

### Post by Clockmender on 2012-10-15
Hello, Some help please.

I have a Sony Vaio Laptop, PCG-8112M whose original battery has died. I bought a non-oem battery and it seems incompatible. The battery light flashes amber and the battery will not charge. The laptop will not boot with the battery in place, but is happy to boot if I remove the battery. The laptop worked on the new battery until it was discharged. It seems Sony have inserted something into the BIOS to prevent non-oem batteries from being charged. All the help on the net points to deleting Windoze files (ISBMgr.exe) and the problem going away. This is of little use to Ubuntu users, so does anyone have a working solution to this problem. I have trawled this forum, and many others, to no avail, the best advice seems to be "buy a genuine Sony battery" but as these are about half the cost of a new laptop, this is not practical, anyway the laptop functions perfectly well aside from the battery issue. The other resolution seems to be to fire some new BIOS from a dodgy Chinese CD, supplied with the battery but blank in my version, and in any case this apparently only works with Windoze XP and not with the latest Sony BIOS. I cannot find any BIOS "fixes" in downloadable Linux format either.

I have done extensive homework on this and can find no solution myself, can anyone help please, other than telling me not to buy cheaper batteries!

Thanks
PS running Ubuntu 12.04,etc i.e. everything up to date.

Further info.
I have downloaded the SonyDriver.exe from the battery supplier and attempted to run it under Wine, and got the error message that my model was not supported or I have already updated the BIOS and should return it to its original state, I have done neither so have hit the buffers on this one! I have seen the hacks to break open the batteries and swap the circuit boards from one to the other - this does not seem like a good idea having seen model planes explode due to unwise use of lithium ion batteries.

---

### Post by Clockmender on 2012-10-16
OK so I have found ONE possible solution to the problem:

I found this:

[http://www.stevekamerman.com/2011/04/rebuilding-a-sony-vaio-battery/](http://www.stevekamerman.com/2011/04/rebuilding-a-sony-vaio-battery/)

This guy suggested that you take the old and new batteries apart and change the controller circuit board from the original Sony battery to the new non-oem one. GREAT CARE must of course be exercised.

I followed his instructions with the following additions:

1) Take the original battery apart SLOWLY by removing the screw covers (stick ons) and undo the screws. Prize the battery cover halves apart working from the connector outwards in both directions evenly until you have separated the two halves.

2) Prize the cells out of the lower case using a small piece of hard wood (lollipop sticks are good) leaving the circuit board and connector strips behind, the cells are only vaguely spot welded to the strips and come off easily, note the layout of the cells and circuit board - you need to reassemble the new one like this! - photographs or drawn diagrams are useful here.

3) Using an small and very sharp modelling knife gently and slowly cut the silicon away from the connector strips, circuit board and battery case. do this again SLOWLY and CAREFULLY so as not to damage or cut any connections to the circuit board, be particularly careful around the [COLOR="Red"]battery temperature sensor[/COLOR]. Lift out the circuit board once all connections to the case via the silicon has been removed (this took me over one hour!).

4) De-solder the connector strips from the circuit board using a small soldering iron and solder wick, be careful not to overheat the board or any components.

5) Repeat the procedures above on the new non-oem battery (mine had no silicon inside so was much faster and I did not need to remove the cells from any connector strips as there was only wires coming from the cells.

6) Solder the wires to the Sony circuit board in the same orientation as they where on the non-oem battery and close the two halves of the case with the four screws and glue if required (not in my case). Mine had four wires, black and red at the ends and blue and yellow at the battery intersections.

7) Fit new battery to laptop and "hey presto" laptop thinks its a Sony battery. My new one had nine cells and the original had six but it works well and one reboot confirmed the new power capacity.

I can't emphasise enough the need to proceed slowly and carefully and I advise keeping an eye on the laptop during its first full charge from empty. Like the guy says I ran the new battery right down until the computer stopped so that all the charge was gone, then recharge to max. My Vaio now boots with the new battery installed and runs well when only on battery power. I was not keen to do the BIOS patch and in a way was pleased when this failed, but it took me two hours of pondering the consequences before I finally started the circuit board replacement job. If you plan your job well, note all the steps and proceed with care and caution all should be well, no brute force is necessary only patience!

I would still like to see a better software based solution to either fire the necessary code to the new battery or the BIOS to convince the laptop that the battery is OK, so will leave this thread open for more solution suggestions.

Thanks and recognition should go to Steve Kamerman, whose website is quoted above.

---

### Post by Clockmender on 2012-10-19
Quick Progress Report

After several days running on mains input the battery has not got beyond "Mildly Warm" and charge level has been maintained. Vaio runs for approx 3 hours on the battery before hibernating (I set it to do that). I takes approx 3 hours to recharge the battery to full capacity. This whole processed was monitored by right-clicking on the battery icon in the task bar and opening the battery monitor sub-pane, which gives you a neat graph of discharge and recharge rates/times. Incidentally if you close this window with the X icon at the top it won't work again until you reboot - so use the "CLOSE" button (bottom right of window) instead! I have asked battery supplier to state on his website that his batteries are not generally suitable for Linux distros unless you change the circuit board, but I suspect hell will freeze over before that happens........

---

