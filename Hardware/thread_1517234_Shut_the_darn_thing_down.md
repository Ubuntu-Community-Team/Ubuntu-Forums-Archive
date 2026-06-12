---
title: "Shut the darn thing down"
date: 2010-06-24
forum: Hardware
---

### Post by valiant32 on 2010-06-24
Is there anyway under the sun to shut down a computer running Lucid. Our office requires all machines to be shut down after hours and we are having a heckava time doing this. Can someone put forth a method that can be applied by an IT dept that has been administering Windows on a Novell network for eons.

---

### Post by Yarui on 2010-06-24
Your question is a bit vague, I'm not sure exactly how you want to shut it down.  If you are saying you want the computer to shut down automatically at a specified time then you could just use cron.

[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

I'm not experienced with using cron, so I'm not sure if there is a standard function that you can use to shut down at a specified time.  You can probably tell it to execute a specific command at your scheduled time, but if not you can definitely have it run a script, so you could just make a script that contains the following command.

```
shutdown -hP now
```Make sure to chmod the script file so that it is executable, then have cron run that script at your scheduled time.  The user profile that cron uses to run this script would, of course, need to have the ability to execute a system shutdown.

---

### Post by valiant32 on 2010-06-24
Thank you for your reply,we want the machines so shutdown by the shutdown command on the units.

---

### Post by migs73 on 2010-06-25
Are you just asking how to shut down a machine under normal circumstances?

i.e. go to top right corner on the panel and click on the on/off/standby button and go to the bottom of the list and select shutdown. Then select shut down from the prompt. Done.
If the button is not on the panel, just right click on the panel and select 'add to panel' and look for the 'shutdown computer' applet. Click 'add to panel' and then use that instead (slightly different menu though).

---

### Post by valiant32 on 2010-06-25
We know how to shut down them normally but they just reboot. The bosses have decided to bite the bullet and install new machines running Win7. The IT department convinced them there was no sure way to assure the operators could successful secure the Unbuntu boxes, sooo we are out. I urged keeping the Linux OS but could not overcome opposition to the Lucid shutdown bug. Thanks for all the help from the ubuntu forums.

---

### Post by dino99 on 2010-06-25
you might find the solution there:

[http://www.google.fr/#hl=fr&source=hp&q=cronjob%2Bshutdown%2Bubuntu&aq=o&aqi=&aql=&oq=&gs_rfai=&fp=dd2586ce8c3c8dc7](http://www.google.fr/#hl=fr&source=hp&q=cronjob%2Bshutdown%2Bubuntu&aq=o&aqi=&aql=&oq=&gs_rfai=&fp=dd2586ce8c3c8dc7)

---

### Post by valiant32 on 2010-06-25
Thank you Dino, but it does not matter now, one of the last acts the ubuntu system did was place the Dell order. Thank you for your interest.

---

### Post by pricetech on 2010-06-25
Wow.  Talk about knee jerk reaction.  Sound like your bosses hated Ubuntu to begin with and were just looking for an excuse.  I deal with that kind of irrational prejudice from time to time myself, and it's sad.

---

### Post by valiant32 on 2010-06-25
Yes it was and I did not have the weight to go against the IT dept. I know Ubuntu would have been better for the company - any how an order for 60 workstations and 2 servers went to Dell. Thank you all for trying to help me.

---

