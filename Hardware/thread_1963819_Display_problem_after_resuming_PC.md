---
title: "Display problem after resuming PC"
date: 2012-04-23
forum: Hardware
---

### Post by yfaney on 2012-04-23
Hello, I am using ASUS eeePC X101CH laptop and I installed the Ubuntu 11.10.

But it couldn't apply the Intel GMA 3600 display driver, so I compiled the 3.3.2 Kernel with the driver.

So now it works, but I've got another problem.

My display doesn't work as the following attached file after resuming the PC from sleep mode.

Before compiling the resuming process was OK.

So in summary,

Before compiling : Display Driver (No : VESA) / Resuming after sleep mode (O)
After compiling : Display driver (Y : GMA 3600) / Resuming after sleep mode (X)


If anyone knows or can guess what is the cause, please help me.

Thanks,

Best regards,
Younghwan Jang

P.S : Except screen everything is Ok, I cannot see through LCD but the system is not terminated.

---

### Post by dandnsmith on 2012-04-23
As you've found, this sort of thing is tricky to debug as you cannot see enough to extract any more detail.
The erroneous display looks like a sync problem - but I've no idea how this can happen. Possibly there is a way of applying some sort of re-sync to get the displaying when you do a resume.

I trust you've tried
a) sequences like Alt-Shift-2 (think that's the right sort to get an alternative terminal display)
b) checking the old parts of the logs, to see if anything gets posted when tou try to do the resume (after a reboot, of course)

---

### Post by yfaney on 2012-04-24
> **dandnsmith said:**
> As you've found, this sort of thing is tricky to debug as you cannot see enough to extract any more detail.
The erroneous display looks like a sync problem - but I've no idea how this can happen. Possibly there is a way of applying some sort of re-sync to get the displaying when you do a resume.

I trust you've tried
a) sequences like Alt-Shift-2 (think that's the right sort to get an alternative terminal display)
b) checking the old parts of the logs, to see if anything gets posted when tou try to do the resume (after a reboot, of course)
Thank you for your helping. I did as you said,
First of all a) also had a problem in console screen,
and now I'm doing b) with analyzing kern.log file.
If it finds I'll share what the problem is. Thank you.

Best regards,
Younghwan Jang

---

### Post by dandnsmith on 2012-04-24
Sorry about this - I posted the wrong codes for the alternate console (must have been aberrating). Ctrl-Alt-F1 will get you one (can also use any of F1 to F6), and Ctrl-Alt-F7 will get back to the normal graphics display.

---

