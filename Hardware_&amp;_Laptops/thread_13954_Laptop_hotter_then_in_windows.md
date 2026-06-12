---
title: "Laptop hotter then in windows"
date: 2005-02-03
forum: Hardware &amp; Laptops
---

### Post by dave9191 on 2005-02-03
Hey, I am trying to figure out why my laptop runs hotter with linux then with windows. Its a Vaio 505DP. The CPU has a nice fan cooling it. The HDD is on the left closest to me, and that stays pretty cool too. The section that warms up the most is above the cd drive on the right side. Now I dont know whats there and i cant figure it out. The cd drive takes most of the room there, and its also got the usb mem stick reader. Its not the cpu or hdd. I guess that the graphics chip would be closer to the cpu fan or not above the cd drive. 

It warms up pretty fast and stays warm even when the laptop isnt doing anything. I dont remember windows heating it up this much and not that part of the laptop. Id like to be able to keep the temp of this thing pretty cool if its not doing anything :)

---

### Post by knappen on 2005-02-03
Thats weird!

Open it up and see what it can be.

---

### Post by dave9191 on 2005-02-04
Despite how tempting it is to open it up and have a look, Id rather not take apart my new beuty :)

---

### Post by Monkey77 on 2005-02-04
I have noticed that on my Acer Aspire laptop the fan kicks in more often than when running WinXP Home.  

This happened on Fedora as well as Ubuntu.  

I did wonder if there was some sort of application that monitored the fan speeds and CPU temp of the system and allowed the user to adjust the settings?

I also my GPU is an nVIDIA which I think has a fan also.

---

### Post by valadil on 2005-02-04
My laptop runs pretty quietly in linux, provided its open.  Usually i'm running my laptop in class, so sometimes I have to close the lid and put it down for a while.  When I leave it alone like that the fans go crazy.  At first I thought it was teh screensavers using up more cpu than emacs had been, but after disabling the screensaver I found that that wasn't the case.

My guess (for the rest of you anyway) is that since Linux doesn't currently do cpu frequency scaling (correct me if I'm wrong here) your laptops are running as hot as possible.  Mine runs at 1.7ghz, but scales back to 1.2 if it doens't need the cpu cycles.  When I first got it the batteries would last for 3 hours if all I did was type shit but they'd only survive for 45 minutes if I played cpu intensive games.  The laptop also got too hot to touch for most of that time.

---

### Post by Technoviking on 2005-02-04
Some laptops do cpu frequency scaling, especially centrino based ones. Try installing powernowd package, worked for me on my Toshiba centrino laptop. You may need to upgrade to kernel from hoary for CPU scaling to work.

Mike

---

### Post by dave9191 on 2005-02-04
I have a centrino laptop, the cpu freq scaling works. I have that lovely gnome applet running telling my the current speed. And as soon as it hits full speed, the fan kicks in. And the cpu doesnt seem to get hotter then in windows. Its the other side of the laptop. Im thinking maybe the RAM??

I tried installing lm-sensors to measure temp and fan speed but it just said i dont have any sensors installed. I guess that might be the case since it doesnt have a windows app for that and the ones i tired didnt really work. 

The laptop never gets too hot to touch, but maybe too hot to keep on your lap. But its a lot hotter then windows makes it.

---

### Post by knappen on 2005-02-04
My AMD Mobile scales down nicely, however I think we are getting off track here.

Still think you should open it up :-)

---

### Post by tv123 on 2005-02-05
[QUOTE=dave9191]Hey, I am trying to figure out why my laptop runs hotter with linux then with windows. Its a Vaio 505DP. The CPU has a nice fan cooling it. The HDD is on the left closest to me, and that stays pretty cool too. The section that warms up the most is above the cd drive on the right side. Now I dont know whats there and i cant figure it out. The cd drive takes most of the room there, and its also got the usb mem stick reader. Its not the cpu or hdd. I guess that the graphics chip would be closer to the cpu fan or not above the cd drive. 

It warms up pretty fast and stays warm even when the laptop isnt doing anything. I dont remember windows heating it up this much and not that part of the laptop. Id like to be able to keep the temp of this thing pretty cool if its not doing anything :)[/QUOTE]

Hi Dave,

some of the things I do to keep things cool and quiet are:

1) I remove unwanted modules and services. Ubuntu does load too many kernel modules, and so I manually remove ones that I know are not needed ("lsmod" gives the list, "*modinfo *modname**" gives a brief description, and "modprobe -r *modname*" removes the named module, as you probably know).

2) If stale swap usage is going on, I do "*swaoff -a && swapon -a*" so that we use
RAM instead of a HD-hosted swap partition/file. Beware that if you don't have enough RAM to handle the current real memory needs of the running processes, "swapoff -a" may kill some running processes.

3) A neat "hack" I found is this: swsusp, which gets invoked by
*echo "disk" > /sys/power/state* cleans up unnecessary virtual memory pages
before doing the real disk-suspend. So, if you go through this step, when your machine resumes (if it does, as linux ACPI is still work-in-progress), then you should have significantly smaller memory usage. Then, if you do trick (2) above, you
should be back to "minimal" RAM usage. Actually, in my case, for whatever reason,
swsusp fails to suspend, after doing a memory cleanup, and this works out great because, it resumes without doing the suspend, putting me back to where I was, but with cleaned up virtual memory usage! I now use ACPI S3-suspend as I described in: [http://ubuntuforums.org/showthread.php?t=13428](http://ubuntuforums.org/showthread.php?t=13428) for real suspending, and it works almost great!

4) To make removing/adding services easy, I compiled the package "*gnome-system-tools*" so that it builds the "services" module, which for some unknown reason is skipped in the ubuntu version of this package (the version I have, at least). This makes working with services a snap. Post here if you need help in rebuilding this as an ubuian package or as an addon installed in /opt.

5) Build a custom kernel with only what you need, and for the exact platform (cpu) that you have (in my case, Pentium M, instead of default i386). The full set of
wiki pages on kernel building are at:

[http://www.ubuntulinux.org/wiki/KernelCompileHowto](http://www.ubuntulinux.org/wiki/KernelCompileHowto)

The method I liked is the one described in:
[http://www.ubuntulinux.org/wiki/KernelHowto](http://www.ubuntulinux.org/wiki/KernelHowto),
with the exception that, I use
*make-kpkg --initrd --append-to-version -my_ubu_version kernel_image kernel_headers*
as this also builds the necessary headers package (needed for compiling several third party programs), and the kernel_image package creates an initrd, without which my system does not boot.

6) This tip is something I haven't tried out. I think that the utility *hdparm* has much to offer in terms of optimizing disk-usage etc. You may want to read up on that.

7) As mentioned above, various power mgmt tools are there to make the cpu usage "optimal", although I found that Ubuntu does a great job of setting these things up so that they work well straight out-of-the-box!

Hope these tips help. Just ask for more if needed :)

Tom

---

### Post by knappen on 2005-02-05
Tom, that was great! I will also check my laptop.

Thanks!

---

### Post by Jspired on 2005-02-05
Great list of things to keep in mind, Tom.  Thanks so much!

---

### Post by tv123 on 2005-02-06
[QUOTE=knappen]Tom, that was great! I will also check my laptop.

Thanks![/QUOTE]
 knappen: one very handy tool for managing modules is the "modinfo" utility. "modiinfo module" gives a brief description of the module, along with the options etc.

---

### Post by knappen on 2005-02-06
[QUOTE=tv123]knappen: one very handy tool for managing modules is the "modinfo" utility. "modiinfo module" gives a brief description of the module, along with the options etc.[/QUOTE]

Thank you for the tip. It was really helpful.

---

### Post by dave9191 on 2005-02-07
tv123, that was great. Ill have to start looking into these things as soon as i have some spare time. Thats a hell of a lot of good advice. 

And i think that i may have worked out part of the secret of windows keeping the lappy cooler then linux. Good old suspend, i booted up windows the other day (looks down in shame) and left it on for comparison. When i came back it was nice and cold and sleeping like a baby. Probably the reason i never noticed it getting so hot b4.

---

### Post by knappen on 2005-02-07
Tom, perhaps a HOW TO!

:-)

---

### Post by tv123 on 2005-02-07
[QUOTE=dave9191]tv123, that was great. Ill have to start looking into these things as soon as i have some spare time. Thats a hell of a lot of good advice. 
[/QUOTE]

You're welcome, Dave. Jut doing a teeny bit to help :)

Ubuntu is rapidly emerging as a rather impressive linux distro, my hats off to
the project team!

TOm

---

### Post by tv123 on 2005-02-07
[QUOTE=knappen]Tom, perhaps a HOW TO!

:-)[/QUOTE]

Sure, I'll write one in a few days and submit it.

Thanks for suggesting.

Tom

---

