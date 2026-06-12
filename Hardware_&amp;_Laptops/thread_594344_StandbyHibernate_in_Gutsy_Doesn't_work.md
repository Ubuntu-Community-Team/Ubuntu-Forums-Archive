---
title: "Standby/Hibernate in Gutsy Doesn't work"
date: 2007-10-27
forum: Hardware &amp; Laptops
---

### Post by insaneidiot on 2007-10-27
I can't get hibernate or standby to work.  I tried each one and all it does is flash a log in window and shuts off the screen.  I try to get back into the OS but nothing works.  I press the power button and nothing works.  I have to press the power button to turn it off and then turn it back on for it to do anything.  How do I fix this?

---

### Post by jasonmeansfriend on 2007-10-29
> **insaneidiot said:**
> I can't get hibernate or standby to work.  I tried each one and all it does is flash a log in window and shuts off the screen.  I try to get back into the OS but nothing works.  I press the power button and nothing works.  I have to press the power button to turn it off and then turn it back on for it to do anything.  How do I fix this?

bump 

same here, was googling the problem when i came across this post...

i click hibernate, and it "looks" like it is starting to hibernate...
then all there is is a black screen with a little command-prompt-style blinking cursor in the top left corner...
have to shut it down improperly (hold down power button) and restart...

hope someone can help...:confused:
if i figure out the answer, i'll let you know... :)

---

### Post by kaurman on 2007-10-29
Hi

I'm not sure about suspend but I've had similar problems with hibernation.

The first thing I'd check would be swap. Type 'free'  in terminal and see what you get.
If swap is not used at all or has a size of 0 this is most likely an issue.

You could also try installing a package called 'hibernate.' When this is installed you should be able to configure various values with configuration files located in //etc/hibernate (hopefully the path is correct :))   

Kaur

---

### Post by Depressed Man on 2007-10-29
Why would it be an issue if swap is 0?

---

### Post by insaneidiot on 2007-10-29
My swap is fine.  I have 2GB of swap and it's not even being used at the moment.  I'll try to install the "hibernate" package.

---

### Post by firefeather on 2007-10-29
I can't get it to work either. I'm running Gutsy and it does a very similar thing. I end up having to hold down my power button. It sometimes even happens when I just try to log off.

---

### Post by kaurman on 2007-10-29
> **Depressed Man said:**
> Why would it be an issue if swap is 0?
Because AFAIK hibernation writes its image to swap by default.
* When I say image I mean the file the computer reads to get back to pre hibernation state.

---

### Post by Depressed Man on 2007-10-29
Nevermind, I realized you meant the existence of swap [total] (not 0) rather then what's listed under the "used".

---

### Post by jasonmeansfriend on 2007-10-30
for a short while yesterday(2-3 hours) i had the bug (google it, you'll find it) of shutdown dialog not appearing until a minute later, and "Hibernate" and "Suspend" buttons missing

all i remember was that i was trying to follow someone's (not on ubuntu forums but somewhere else) tutorial for it. something about POST_VIDEO or something i think
after i changed back to my previous settings, shutdown dialog worked again perfect, but i'm back to the original problem of hibernate/suspend not working :(

and i tried the package 'hibernate' but what am i supposed to do with it? i couldn't figure that out.

thanks

---

### Post by juhl on 2007-10-30
I should have enough swap enabled, I have 1.427 MB swap, currently.

It seems that I can get it to sleep and wake properly (except for all the graphical bugs) when the power cord is disconnected,
but as soon as it is connected I have the problem.

Hibernate does not work at all.

---

### Post by kaurman on 2007-10-30
> **jasonmeansfriend said:**
> 

and i tried the package 'hibernate' but what am i supposed to do with it? i couldn't figure that out.

thanks

Hi!

There should be quite a few files in /etc/hibernate

You could try to mess with common.conf by opening terminal and typing ```
sudo gedit /etc/hibernate/common.conf

```

If you want to know more about the hibernate package type ```
man hibernate
``` in terminal.

---

### Post by stara on 2007-11-03
* First *
sudo gedit /etc/initramfs-tools/modules
add the following

vga16fb
fbcon
vesafb

sudo gedit /etc/modprobe.d/blacklist-framebuffer
comment out the following (add prefix #) so it would look like:

# blacklist vesafb
# blacklist vga16fb

last but not least, run the following in a terminal

sudo update-initramfs -u

* Second *
sudo gedit /etc/default/acpi-support
change 
MODULES_WHITELIST="" to MODULES_WHITELIST="vga16fb vesafb"
ENABLE_LAPTOP_MODE=false to ENABLE_LAPTOP_MODE=true

Nothing else, it's work for me FS A1630 with ATI Mobile 9700

---

### Post by insaneidiot on 2007-11-03
> **stara said:**
> * First *
sudo gedit /etc/initramfs-tools/modules
add the following

vga16fb
fbcon
vesafb

sudo gedit /etc/modprobe.d/blacklist-framebuffer
comment out the following (add prefix #) so it would look like:

# blacklist vesafb
# blacklist vga16fb

last but not least, run the following in a terminal

sudo update-initramfs -u

* Second *
sudo gedit /etc/default/acpi-support
change 
MODULES_WHITELIST="" to MODULES_WHITELIST="vga16fb vesafb"
ENABLE_LAPTOP_MODE=false to ENABLE_LAPTOP_MODE=true

Nothing else, it's work for me FS A1630 with ATI Mobile 9700

I tried every step that you posted but it still doesn't work.  I'm frustrated about it.  This is one of the reasons why I just can't ditch Windows entirely.  Thanks for helping though :)

---

### Post by amias on 2007-11-05
Its not working for me either ...

Am using a Soltek board with a VIA chipset and an Nvidia MX4000 .

---

### Post by kaurman on 2007-11-05
AFAIK from my own experience If you set enable_laptop_ mode to 'true' this may result in an extremely agressive powersaving policy which can harm your hdd. I'm no expert though. You should just do some research about laptop-mode to make sure it is set up safely.

---

### Post by khurrum1990 on 2007-11-05
Hi, hibernate was also broken with the latest Ubuntu 7.10 kernel 2.6.22-14 and there has been a bug report so the last working kernel is actually 2.6.22-12. I had the same problem and I went back to that kernel.
Also they will be releasing a fix for that kernel in a while as that bug is under high priority. If ur bug is due to the kernel then revert back to the first 7.10 kernel which was 2.6.22-12. Also tell us which VGA card u have?

---

### Post by jasonmeansfriend on 2008-02-02
FIXED IT!!!:):):):):):)

i don't know how i did it..  but here goes...

music is my hobby, so whenever i tried reinstalling ubuntu gutsy, i just without thinking upgrade to ubuntustudio-desktop... every time

well this time, (my 5th reinstall) i slowed down and realized i could install all the audio apps (individually though) in ubuntu, without ubuntustudio (that makes sense, right?)

boom, kept the default kernel (2.6.22-14-generic), and hibernate/suspend now WORKING!!!

hope this helps someone, though i doubt any of you use ubuntu studio...


p.s.: i just couldn't resist and installed ubuntustudio-theme :)

---

