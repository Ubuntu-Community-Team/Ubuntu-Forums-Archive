---
title: "Averatec 3700 Sound Problem"
date: 2006-05-12
forum: Hardware &amp; Laptops
---

### Post by muadib on 2006-05-12
Hello,
I'm having trouble recording audio with my Averatec 3700 notebook using the Sound Recorder application with Ubuntu Dapper.
I have played with different sound levels using alsa mixer and made sure that the mic channel was not muted but I have had no success getting the mic to work.
I have also tried 2 different mics to make sure that the mic was not the problem.
I can confirm that audio output works with the card as I can listen to music with the laptop without a problem.
Thank you very much for any help with this matter,
Mathieu

---

### Post by ivansv on 2006-05-13
i,too have had sound problems with my laptop in linux until i discovered that acpi is the problem. when you install boot with "linux acpi=off" and ur sound problems will go away.

---

### Post by muadib on 2006-05-13
Thank you for the reply.

I have tried what you recommended but the problem persists.

I can play sound out of the card but have been unable to record with the mic.

Has anyone else had this problem ?

Mathieu

---

### Post by muadib on 2006-05-19
Hi,
Thank you very much.
I have the sound working now on my Averatec 3700, input and output.
For the recording to work, I had to turn run alsamixer, hit tab, and unmute turn on the capture channel by hitting the space bar.
Mathieu
muadib is online now   	Edit/Delete Message Reply With Quote Quick reply to this message Multi-Quote with this Post

---

### Post by cholly on 2006-06-16
I'd like to attempt to revive this thread. A search thorugh the forums yeilds a few threads but few resolutions. I have a similar problem where I 'lose' sound. It seems to be related to idle time or hibernation, even locking the screen. It also could have to do with the postion of Mars for all I know. 

Basically I have sound then after I hibernate, reboot, lock the screen, or eat a sandwich it no longer works. Unlike some, a reboot into linux does not solve it for me. I have had this problem from the frist day, and have not tried to adress it so I haven't tried loading or unlaoding drivers or configurations etc. I was hoping for some direction.

My only current solution is to reboot into WinXP at which time I hear an audible pop. I then restart and boot into linux (the default and preferred boot) and I will have sound again.

Aside from wifi troubleshooting  and this problem, I haven't used my WinXP install for anything else since I have installed Unbuntu (intially Breeze and it had the same problem). So it would be just peachy to rid myself of this problem and have one less reason to run that filthy OS on my shiny little laptop.

**Also @ivansv** could you elaborate on your comment. Do you mean to pass 'inux acpi=off' by putting it as a kernel option at the end of my /etc/grub/menu.lst line?

---

### Post by muadib on 2006-06-25
Hi,

I'd like to say that I have no problem with sound with this laptop, even after going in and out of suspend mode.

I have not had any luck bringing the laptop into hibernation using the /etc/acpi/hibernate.sh script.

Would appending acpi=off at boot time disable acpi functionality such as suspend ? 

Could it be that your sound levels are being changed by some application ? What kind of volume levels are you getting when you run alsamixer ? 

Mathieu

---

### Post by muadib on 2006-06-27
Just writing to say that I have gotten the laptop to hibernate, all I had to do was create a partition that was as big as my physical memory, turn it on as swap, and added the resume=/dev/hda(my swap partition number) and everything is working well now. Mathieu

---

