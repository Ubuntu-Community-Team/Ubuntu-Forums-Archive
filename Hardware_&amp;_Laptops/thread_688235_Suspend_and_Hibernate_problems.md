---
title: "Suspend and Hibernate problems"
date: 2008-02-05
forum: Hardware &amp; Laptops
---

### Post by Aslund on 2008-02-05
Heya 

I have a Dell M65 and just installed Ubuntu Gutsy on it, everything runs great but have a problem with suspend and hibernate, which result in a black screen after trying to wake it up, although the system runs in the background. 
Have looked at many post regarding this subject, but the number of ideas and solutions are so many that I have no clue to where to start to fix this problem.
Hope you can give me some help regarding this matter.

Regards

Aslund

---

### Post by lian1238 on 2008-02-05
Hi, I also have this problem on my Acer Aspire 5580. What indicates that the system is running in the background?

For me, when I get the black screen (sometimes I don't get it), my usb optical mouse doesn't turn on the red light. So, I need to keep pressing (not hold!) the power button to "nudge" it awake. Sometimes I need to nudge it quite a few times. When the screen comes on and the mouse awakes, I know it's awake. Maybe that'll also work for you. I routinely need to suspend after a restart or cold boot, because my headphones don't work otherwise. Same problem in windows, and same solution.

---

### Post by Aslund on 2008-02-05
I have a 1½ min start up sound, if I suspend while it runs then it starts again when I go out of suspend.
I had hoped for a more "productive" solution. :)

---

### Post by steveneddy on 2008-02-05
You need to start somewhere. There are hundreds of threads about this very problem.

I suggest that you try one option at a time until you come up with a solution that works best for you.

Here is my reply on a similar thread:

Try adding **acpi_sleep=s3_mode** to the end of the kernel line in the

/boot/grub/menu.lst

file.

Like this.

```



title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
[COLOR="Red"]kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=dc5e4ce2-5607-4cc7-931c-9543f2caf229 ro quiet splash **[COLOR="Blue"]acpi_sleep=s3_mode[/COLOR]**[/COLOR]
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=dc5e4ce2-5607-4cc7-931c-9543f2caf229 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet


```

and you might want to try this

```


Try changing some of the options available on /etc/default/acpi-support

On my laptop, changing the
SAVE_VBE_STATE=true

and

POST_VIDEO=true

to false did the trick.


```

from [this thread]("http://ubuntuforums.org/showthread.php?p=4230703#post4230703")

---

### Post by Aslund on 2008-02-05
It starts to atleats do something, but when I press the power button while suspended it reboot my mashine instead of wake up from suspend.

---

### Post by noremac on 2008-02-05
> **Aslund said:**
> It starts to atleats do something, but when I press the power button while suspended it reboot my mashine instead of wake up from suspend.

I just recently tried putting my machine into suspend for the first time, and this is what mine does. It goes into suspend no problem, but when I push the power button, it will just reboot. If I press a key on the keyboard, the lights on the keyboard turn on but the computer does not start up.
-C

---

### Post by steveneddy on 2008-02-05
Anyone try the fixes I posted up there? :-|

---

### Post by Aslund on 2008-02-05
My last reply was actually after implementing your changes steveneddy.

---

### Post by steveneddy on 2008-02-05
I suspend my laptop by putting the laptop lid down.

It wakes up when the lid is raised.

Go to system --> Preferences --> Power Management and set the laptop lid control to see if it works better that way.

---

### Post by Aslund on 2008-02-05
When I close the lid it goes suspend allright, but when I open it then it goes reboot asp.

---

### Post by Aslund on 2008-02-05
hey, had some fun with trying out your idea and I made suspend work.
What I needed to do was to delete "acpi_sleep=s3_mode" and now it suspend as it did but also wakes up normally. 
Only funny thing is that Ubuntu claims that suspend did'nt work when it boots up although it just did :).

---

### Post by steveneddy on 2008-02-05
Cool - sometimes both things make suspend work and sometimes it's one or the other that get suspend working.

Glad you got it going.

---

### Post by Aslund on 2008-02-06
Yea, happy about it too, well, experienced this morning a strange problem.
When I started my computer after it had been in suspend over night my keyboard failed on me, the PC went fine out of suspend and I could use my mouse but the keyboard did'nt respond to anything. Had to reboot and then everything worked fine again :S.

---

### Post by Ryan Yo on 2008-02-06
Thanks for the tips steveneddy! They worked for me the first time I tried it, then went to a blank screen the second time and I haven't tried it again since. Aldo, when I did these two these two things, the wireless adapter gets turned off and I had to manually turn it back on. Any ideas as to how to fix this?

---

