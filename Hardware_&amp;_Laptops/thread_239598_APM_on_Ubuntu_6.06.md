---
title: "APM on Ubuntu 6.06"
date: 2006-08-19
forum: Hardware &amp; Laptops
---

### Post by Jaxilian on 2006-08-19
How can I get suspend and sleep to work on my laptop?

when I type APM in console it says "No APM support in kernel"

and if I turn on the suspend and sleep and try it, my computer never wakes up . I have to turn off manually on powerbutton and do a coldstart to get back in again.

Any ideas?](*,)

---

### Post by nrwilk on 2006-08-19
I have the **exact** same issue and question.

I don't have any idea where to start looking, or what to be looking for.

---

### Post by Jaxilian on 2006-08-21
any have a solution for this? :-k

---

### Post by smelly_sox on 2006-08-21
I do not use APM on my laptop - DELL C640.
Whilst I do not know the specifics of your hardware I do know that ACPI is generally preferred over APM. Somewhere in the long history of BIOS chips parameters changed for operating systems to interact with the BIOS. ACPI is currently the default standard. I believe ACPI support is built into the Ubunutu 6.06 LTS kernel. (Someone correct me if I'm wrong about this).
Maybe you could google your laptop type to find out if you really need APM enabled. If you do then be aware that APM & ACPI do not like sharing a kernel. You will most likely have to *insmod* an APM module into your kernel and disable ACPI at boot time.
If you simply want to adjust your power settings go to 
System / Preferences / Power Management.
Regards

---

### Post by Jaxilian on 2006-08-21
I have a new laptop, well it was new 2005.

1.86Ghz centrino
2048Mb RAM
80Gb HD
ATi Radeon X600 mobility

fairly unknown brand....Zepto. Model is Znote 2415W

I tried ACPI, but it can only shut itself down...not back up again.
I will be most grateful on ideas about to solve this. I have good relation to the manufacturer, Zepto and they are looking into Linux at the moment, but I need to get this going to show them what Linux can do for their computers.:D 

Everything else works on it.....just not this suspend/sleep thing which ALOT of people use that use their computer for work. ](*,)

---

### Post by nrwilk on 2006-08-22
> **smelly_sox said:**
> ACPI is generally preferred over APM.


hehe, you've just displayed my newbieness in the topic of linux on laptops. :)

Yes, I'd rather use ACPI.  I didn't even know that APM was an alternative.  I just typed it in after I saw this post, got the same output, and figured it was a command to check acpi settings or something.

Anyway, what is the process someone would go through to try and get hibernate/suspend working on a laptop with acpi? :-k

---

### Post by Jaxilian on 2006-08-25
bump

---

### Post by hizaguchi on 2006-08-25
You can't have ACPI and APM both enabled at the same time.  ACPI is enabled by default, but you can switch this easily.  When you turn on the computer and the Grub menu comes up (may have to hit Esc to get it), just highlight the kernel you want to boot (top of the list most likely) and hit "e" (for edit).  You'll get an edit screen.  Move down to the "kernel" line and hit "e" again, then add "acpi=off apm=on" to the end.  Then hit ENTER and then "b" (for boot).  You'll start with APM instead of ACPI.  If everything works right, you can make the change permanent by editing /boot/grub/menu.lst.  You can do this directly and you'll have to change it every time you install a new kernel, or you can do it the proper way, which I don't know so search the forums. :)

---

### Post by Jaxilian on 2006-08-29
> **hizaguchi said:**
> You can't have ACPI and APM both enabled at the same time.  ACPI is enabled by default, but you can switch this easily.  When you turn on the computer and the Grub menu comes up (may have to hit Esc to get it), just highlight the kernel you want to boot (top of the list most likely) and hit "e" (for edit).  You'll get an edit screen.  Move down to the "kernel" line and hit "e" again, then add "acpi=off apm=on" to the end.  Then hit ENTER and then "b" (for boot).  You'll start with APM instead of ACPI.  If everything works right, you can make the change permanent by editing /boot/grub/menu.lst.  You can do this directly and you'll have to change it every time you install a new kernel, or you can do it the proper way, which I don't know so search the forums. :)


this does not work for me. If I do this then my sleep button stops working. If I try to suspend, it kicks me back to desktop.
Problem with waking up the pc after suspend still remains. :-k

---

### Post by rcd412 on 2006-08-29
are we sure its a problem with acpi and not gnome? There was an updated gnome powermanager someone made a deb, i would try updating it... if that doesn't work lol try kubuntu.

---

