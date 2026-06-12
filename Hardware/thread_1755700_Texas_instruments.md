---
title: "Texas instruments"
date: 2011-05-11
forum: Hardware
---

### Post by icasi on 2011-05-11
Hi everyone.
I have a problem with my calculator TI-89 Titanium. When I plug my the cable in to the computer nothing happens. I can't see that the calculator and the computer are connected. I installed Tilp2. I hope somebody can help me?
Thank you.

---

### Post by summoness on 2012-03-25
Run tilp2 as root using the following command
sudo tilp
enter your password

Then if it doesnt see it, right click on the device in the left hand column and select change device. it should be the first entry. possibly null

In the window that then opens click on the search magnifying glass to probe for devices.just above OK.
that will tell you the device found what cable and port etc your device is at.
use these settings and u should be able to connect. the only glitch i have found so far is that the screenshot does not show what is actually on the calculator, hence my finding your post.

Hope this helps.

---

### Post by summoness on 2012-03-25
upon further research through the ti manual and not finding what i was looking i played with tilp again and tried to take a screenshot. i noticed the same display with all chars on the screenshot. in the manual it stated about ensuring communication with the calculator by hitting the ready button. all was ok and by pure coincidence i hit the refresh screen capture and voila! up came the actual screen.

So for those of you with that problem all that is necessary is to refresh the screen capture.

---

