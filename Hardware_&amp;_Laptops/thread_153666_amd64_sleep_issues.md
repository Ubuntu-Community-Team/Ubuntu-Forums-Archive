---
title: "amd64 sleep issues"
date: 2006-04-01
forum: Hardware &amp; Laptops
---

### Post by xinix on 2006-04-01
I tried this question in the dapper forum but didn't get a peep out of anyone so I'm trying the hardware forum. After all it is a more appropriate place to solve a hardware issue.  Here it goes:

So I'm trying to figure out how to get my system to go to sleep when not in use. First here are the relevant specs (need to know more? just ask) in case someone knows the magic dance to make it work :
CPU: AMD64 3200+
Mobo: Biostar N4SLI-A9 (not in SLI mode)

Originally I was having trouble getting the system to sleep. I'd select sleep from the options in the logout menu and it would fail. The screen would turn off and a second later it would come back on with a locked screen but never actually going to sleep. So then I monkeyed around in my BIOS and changed the suspend mode from S1 to S3. I also enabled the wake from S3 with USB option. This sort of worked. Now the computer goes to sleep but won't wake up. USB goes dead and when I hit the power button the power and hdd lights come on,fans whir, but the screen remains off. USB remains dead until I unplug and replug.  And trying to blindly shutdown ( switching to another tty...) doesn't work, so I don't think the system is waking. Hitting the reset button is the only way I've found to get out of this.  Yes it makes me cringe to.
 On the other hand, Hibernate works just fine, though it's not an instant on and off like sleeping. Atleast like sleeping on other OS's . Any suggestions?

If this is a bug that needs to be filed, what package would this be related to?

-Thanks

---

