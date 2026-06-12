---
title: "out of frequency range for monitor"
date: 2005-10-19
forum: Hardware &amp; Laptops
---

### Post by swaroop on 2005-10-19
hi all..
recently i have got ubuntu-5.04 through shipit.......
i presently have dual boot with winxp and suse....
iam planing to switch to ubuntu
when i run the live cd all the things such as language settings,hardware detection,network detection done well...... 
but when it is about to start the live session the monitor is just showng a blank screen and after a few seconds it is showng a message that 
"OUT OF FREQUENCY RANGE"
"SET RESOLUTION LOWER OR SEE MONITORS USER GUIDE"
plz help me.......
i had an hp compaq presario sr1235il model pc
monitor is of compaq
the link for its drivers is 
[http://h10025.www1.hp.com/ewfrf/wc/softwareList?dlc=en&lc=en&product=435565&lang=en&cc=us&os=228](http://h10025.www1.hp.com/ewfrf/wc/softwareList?dlc=en&lc=en&product=435565&lang=en&cc=us&os=228)

---

### Post by ewz on 2005-10-19
Yes I have had this problem with Knoppix live CD it can't start X 
to fix it at the boot screen you can set your res- by passing this option,
*screen=1024x768 depth=16*  or what ever your res- is maybe 800x600 or 1280x1024 and depth can be 24 or 32
for notebooks you can use *fb1024x768*
I don't no if this works in ubuntu live but you could give it a try
hope this helps

---

### Post by swaroop on 2005-10-19
i tried those commands but they did not worked.....
i tried to configure in live-expert mode and there i set the screen rosolution to 1024x768 frequencey 60hz......... after the live sesson is about to start.......
the xserver login screan apperared for few seconds and again the screen went blank.......... this time i did not see the error messege like "frequency out of range".........
the same thing happened when i manually set the horizontal and vertical refresh rate manually seeing the user manul with expert mode.

---

### Post by _smd_ on 2005-11-12
This problem is happening to me also,  I never got this error msg until I upgraded to breezy badger in Oct '05.  I have tried recongifiguring my resolution and monitor settings and still nothing. I do not know what to do.

---

### Post by jscheiderer on 2005-12-22
I had this issue in Ubuntu v10.0 just yesterday. 
THIS IS HOW I FIXED IT, this may not be the best way, but it worked with minimal hair pulling ;)

1) REBOOT the machine and login as root or admin or whatever your su is called.

2) As su, GOTO SYSTEM - USERS and GROUPS. Create a new user (we'll call this user JIMBO2 for this example). This user will replace the 'defective' user (who we will call JIMBO1 for this example).

3) Still as su, go to the home folder of JIMBO1 and copy ALL files from that folder to the home folder of JIMBO2.

4) DELETE the ENTIRE HOME folder for JIMBO1 now. Also, delete the JIMBO1 user from the System - Users and Groups. I dont know if this step is necessary, but I did it to be sure no mix-ups occured.

5) Still as su and from within the JIMBO2 home folder, DELETE the DESKTOP folder and the special files here (I am not looking at it, but the icons will show text/binary on them and will be directly in the JIMBO2 home folder).

FINAL STEP: REBOOT and login as JIMBO2, recreate any desktop shortcuts and other settings that were user specific.

This is a messy colution I realize, but it worked on my system.. with minimal hair pulling. :)

---

### Post by jscheiderer on 2006-02-15
Still having out of range for some apps. Anyone got an answer???

---

