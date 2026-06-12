---
title: "Increase Case/CPU Fan Speed Without ACPI?"
date: 2007-10-13
forum: Hardware &amp; Laptops
---

### Post by Githlar on 2007-10-13
I have an HP Pavilion a705w that was apparently purchased from Wal-Mart. In order to boot Ubuntu, I have to use the noacpi kernel option. I understand that ACPI is the module that manages power in the computer, e.g. increasing the fan speed when the system is getting hot.

So, I don't have ACPI working, but it has come to a point where I have to increase my fan speed because of the processing I do on my computer. Is there any way to do this without the ACPI module? Even if it's a permanent change, it's better than not having it.

If it's any help, I'm pretty sure it's just the battery that ACPI has problems with. Is there anyway to load the ACPI module without the battery?

---

### Post by Githlar on 2007-10-14
The fact that it still gets really hot here in Kansas (even though it's supposed to be fall...) also contributes to the fact that my computer is shutting down every 10 minutes or so while running an intensive shell script. At first I wasn't sure what was causing it, but I noted it was 85 degrees Fahrenheit in my house today and I figured that was a major contributor.

I repeat, even if it's a permanent change, I'll take that. I'm running a desktop, so I don't really have a battery to worry about.

---

### Post by digger95 on 2007-10-14
HI, 

I'll be  interested in what you find out since I have the exact same machine.  Both the rear case fan and cpu fan are thermal regulated and should speed up when the processor reaches 60C or so which is not happening.  These Prescott processors heat up fast too unfortunately.

By the way, mbmon works great with our board if you don't already have it installed.  In a terminal window its just:

sudo apt-get install mbmon

then to run it:

sudo mbmon

You'll at least get your system temps and fan speeds that way.

Dig

---

### Post by digger95 on 2007-10-14
Success!

I downloaded and installed lm-sensors through the synaptic package manager then ran 'sudo sensors-detect' in a terminal window.  It found the winbond w83627thf sensors for our  motherboard and automatically generated the script to start the required modules at boot.  Piece of cake.  I rebooted at this point.

Now when I run the 'sensors' command it correctly generates all the temps/fan data.

Then I ran 'sudo pwmconfig' to access and configure fan control.  That's where I'm at right now.  I DO now have control over my fans.  Woo hoo.  I just need to set the min/max temps and all that stuff and pwmconfig will generate the script.  Then I guess I need to autostart it at boot but haven't gotten that far yet.

For more info check out: [http://ubuntuforums.org/showthread.php?t=42737](http://ubuntuforums.org/showthread.php?t=42737)

It looks a lot more complicated than it really is.  I didn't have to set the fan divisor or patch pwmconfig first.

Good luck!

Dig

---

### Post by Githlar on 2007-10-14
Thank you for replying!

I did already have mbmon and lm-sensors installed. I did run sensors-detect and it found the sensors. But, I didn't know what to do after that point. Thanks very much.

---

### Post by Githlar on 2007-10-14
I got the fancontrol script running perfectly after a bit of tweaking, but I do have one question. Does the fancontrol script run at startup? If not, how can I make it run at startup?

---

### Post by digger95 on 2007-10-15
Hi Githlar,

I'm a newbie like you and got stuck on the last part... making the pwmconfig script run at boot.  If you get a chance please let me know what you did so I can do the same.  Thanks much.

Dig

---

### Post by Githlar on 2007-10-15
I found it somewhere... let me look...

[http://ubuntuforums.org/showthread.php?t=42737](http://ubuntuforums.org/showthread.php?t=42737)

Look under the "Starting fancontrol" section.

---

### Post by digger95 on 2007-11-06
Hi Githlar,

I posted this in the other thread as well but in case you miss it...

The latest Linux kernel (2.6.23.1) seems to have resolved a lot of acpi issues. The machine you and I have (HP Pavilion a705w) now runs perfectly without having to turn acpi=off at boot.

What's more, the cooling fan issue is resolved and the fans now work out of the box exactly as they did under WinXP with the proper temperature threshholds.  I scrapped the whole pwmconfig/fancontrol script and just let my fans run like they're supposed to under acpi control.

I even have system standby again.

Dig

---

### Post by s14sh3r on 2007-12-28
This is an old thread, but how do I upgrade to the new Linux kernel? I have an a705w and would like to be able to use acpi.

---

