---
title: "Power Management and Sleep"
date: 2005-07-11
forum: Hardware &amp; Laptops
---

### Post by ux5b2 on 2005-07-11
Hello,

I have a Dell 700m laptop and have been running Ubuntu for a little while.  I have no how idea how to configure the power management for my laptop such as how to get the computer to go into to standby when I close the screen.  Does this involve acpi or apmd?  It seems like the laptop is running hotter than it did when I had windows installed.  Is it automatically stepping down the cpu depending on the load? If not, how do I get Ubuntu to dynamically control the clock speed so that it wont run so hot.  It seems to run hotter both on battery and ac. 

Any help is greatly appreciated.

---

### Post by Davor281 on 2005-07-11
For your laptop to go to sleep mode when the cover is closed do the following:

open the file /etc/default/acpi-support with 
"sudo vi /etc/default/acpi-support" command and uncoment the line saying "ACPI_SLEEP=true".
Uncoment meens delete the "#"sign.

Open the /etc/acpi/events/lidbtn file and change the line saying
"action=/etc/acpi/lid.sh"
to
"action=/etc/acpi/sleep.sh"

Restart laptop and sleep (suspend to RAM) should work on cover close.

As far as you CPU is concerned, are you sure you have a Pentium M or Athlon Mobile CPU?
To check the CPU freq do "cat /proc/cpuinfo", there you will see your current CPU Mhz.

I think that cpufreqd is used for CPU scaling, but I am not sure because I am not using Pentium M.

ENjoY

Davor.

---

### Post by jtang00 on 2005-07-12
Hello,

I recently installed Ubuntu 5.04 on my Dell 700m.  It also seems to me that the laptop is running hotter than in windows xp.  

I tried to to change the /etc/acpi/lid.sh to /etc/acpi/sleep.sh.  The laptop will go into standby mode when the lid is closed.  But when I re-open the lid, the computer hangs.
.  
The CPU does scale.  Try right click on the gnome panel and pick add to panel.  Scroll down and choose "CPU Frequency Scaling Monitor".  This adds a icon on the gnome panel that displays the cpu frenquency.

---

### Post by jc3835 on 2005-07-13
I'm going to see how long my battery lasts in WinXP and in Ubuntu HH. It seems to me that the battery isn't lasting nearly as long in Ubuntu as it does in WinXP, but I could be imagining things.
I have not noticed it running much hotter in Ubuntu than WinXP, as you guys are saying... anyone have a USB thermometer?!  :razz: 
I know that everything isn't equal, but I do expect similar battery life from each OS, when I'm only surfing and messaging and whatnot, nothing too intense like compiling a new kernel.
I have an Inspiron 6000 with the Centrino chipsets.

JC

---

### Post by wh0rd on 2005-08-13
I seem to have noticed that too that the battery runs out faster on Ubuntu Hoary than on Windows XP.  Could be that in some laptops in WIndows you can change the power profile of the laptop. I wonder if Ubuntu has a specific power management profile when it runs on battery?

---

### Post by JNik on 2005-08-22
[QUOTE=Davor281][SIZE=1]
open the file /etc/default/acpi-support with 
"sudo vi /etc/default/acpi-support" command and uncoment the line saying "ACPI_SLEEP=true".
Uncoment meens delete the "#"sign.

Open the /etc/acpi/events/lidbtn file and change the line saying
"action=/etc/acpi/lid.sh"
to
"action=/etc/acpi/sleep.sh"

Restart laptop and sleep (suspend to RAM) should work on cover close.
[/SIZE][/QUOTE]

I tried the above, but everytime ubuntu tries to suspend the system it crashes and I have to restart it. I have the 64bit version of ubuntu installed.

---

### Post by ISBB on 2005-08-24
[QUOTE=Davor281]For your laptop to go to sleep mode when the cover is closed do the following:

open the file /etc/default/acpi-support with 
"sudo vi /etc/default/acpi-support" command and uncoment the line saying "ACPI_SLEEP=true".
Uncoment meens delete the "#"sign.

Open the /etc/acpi/events/lidbtn file and change the line saying
"action=/etc/acpi/lid.sh"
to
"action=/etc/acpi/sleep.sh"

Restart laptop and sleep (suspend to RAM) should work on cover close.

As far as you CPU is concerned, are you sure you have a Pentium M or Athlon Mobile CPU?
To check the CPU freq do "cat /proc/cpuinfo", there you will see your current CPU Mhz.

I think that cpufreqd is used for CPU scaling, but I am not sure because I am not using Pentium M.

ENjoY

Davor.[/QUOTE]


No workie for me... made my computer lock up on Saving VESA state during boot...  i have a dell inspiron 7500

---

### Post by s_p_a_r_k_y on 2005-08-24
ACPI has a lot of problems under linux right now. I actually had more success with apmsleep 3 years ago than I have had with acpi...
One thing to see is where is the laptop hanging when it "wakes up". I'm not sure if its X or the kernel which is not waking up. You could try running the sleep script from the command line with X killed to see if it'll come back up to the console. If it does then we can presume X is the problem... I should also try this on my laptop but never really have time as i hate rebooting it and see it as a waste of 5 minutes if it doens't come back up and have to cold reboot it

---

### Post by mcarter on 2005-08-25
First, install the laptop-mode package, which enables a bunch of power-saving goodness.  I don't know why this doesn't install by default, but just search for laptop in Synaptic.

Also, with a Dell laptop, install the i8kutils package (search for i8k) which is the CPU temperature and fan control utilities for Dell laptops.  Your CPU will run about 30 degrees Celsius cooler.  Mine did.  ;-)

---

