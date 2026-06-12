---
title: "Power issues with 8.04"
date: 2008-06-19
forum: Hardware
---

### Post by suby-luby on 2008-06-19
Dear All,

I have 8.04 installed on my laptop. On the day I was trying to install it, it got stuck somewhere and gave an error message, which when I researched people suggested unplugging the laptop from power and letting operate on battery power and then it will be fine. I also removed the quiet option from the kernel options and things went fine for the most part.

The problem now: Whenever I use my computer running from the battery, and then plug to power, Ubuntu never updates its state to reflect running from AC power. As a result, the screen keeps getting dimmer and dimmer (I guess because it is trying to save power).

Right now, to solve the problem I end up restarting the computer as a get around.

I wonder if there is a solution to these issues yet.

Thanks

---

### Post by phidia on 2008-06-19
Check the settings in System>Preferences>Power Management and be aware that the slider for dim display brightness in the "On Battery Power" tab needs to be set to a small % because it's the amount it dims the screen by. By default it's set too high IMO.

---

### Post by suby-luby on 2008-06-19
I do not see any slider to control the rate of dimness. I can only enable/disable it. 

Actually, I am more curious about why Ubuntu does not update its state when I plug it to a power supply. Somehow, it is stuck with the idea that I am using the battery

---

