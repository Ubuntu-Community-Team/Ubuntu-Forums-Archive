---
title: "Seeking guidance: How to install touchscreen driver on a P1120"
date: 2006-04-17
forum: Hardware &amp; Laptops
---

### Post by Longwing on 2006-04-17
I very recently acquired a Fujitsu Lifebook P1120 with the express purpose of installing Linux on it. I chose Ubuntu and 90% of my hardware was running before I even found my way to the desktop. The one missing piece is the P1120's touchscreen display. The "eraser mouse" works already, so it's not like my system is unusable, but the touchscreen would certainly be a faster, geekier, and cooler way to navigate.

I'm not running completely blind on this one, as I have some information (and a driver!), but I'm basically a total noob, and I'd appreciate some handholding and a little advice.

**My decision to go with the P1120 was fueled, in part, by [this page]("http://www.interstice.com/journals/Simon/20030911.html").** 
Knowing that others had managed to install and configure Ubuntu on this exact same hardware gave me the confidence to plunk down the cash on eBay. One section of the page addresses the touchscreen, and mentions a custom driver...

**Which leads to [this page]("http://ariescomputing.com/lifebook/").**
So now I've got the sourcecode for the driver, along with a ".patch" file to make it compatible with 2.6 kernels. (This is important, as I'd already updated my kernel to solve a completely different problem.)

**What I need:**
**1)** Information on compiling this the right way, particularly on including a ".patch" file. Searching google gives me thousands of guides on how to do this to the kernel, but none on how to do it for totally separate programs.

**2)** After compiling, I need some serious hand-holding. The page's documentation is minimal, mentioning need for the joystick module? What's the module name? How do I check to see if it's loaded? What should I add to my config files? Which config files? This is, frankly, where I get lost.

Any help would be greatly appreciated.

---

### Post by Longwing on 2006-04-17
**Update:**
I'm currently in contact with the maintainer of said page, and he believes he has a solution to the problem. I'll post more here when I've got better information.

---

### Post by Armein Z. R. Langi on 2006-10-19
Joytouch solve my problem right away!

After spending frustrating googling on this subject (P1120 touchscreen on Ubuntu), I think the best solution is Joytouch ([http://www.interstice.com/journals/simon/20060413.html](http://www.interstice.com/journals/simon/20060413.html)) by Simon Funk.

I installed Xubuntu 6.06.1 (using USB CDROM and Instlux. It is a long story.  I had to use Kubuntu alternate CD to get into text based ubuntu, then 'sudo apt-cdrom add', insert the Xubuntu CD, and 'sudo apt-get install xubuntu-desktop').

Wow, everything works perfectly (including wireless lan) in about 30 minutes!  Except, of course, the touch screen.  I had to use **a usb mouse** temprorarily because the erase stick is ackward to use for me.

Now, googling for P1120 touchscreen ubuntu always points to solutions with changing xconfig parameters.  Until I tried Joytouch... 

After download it to my home directory, and unarchived it, it was ready... except nothing happened first... turned out the USB mouse had to be removed.  So after restarting, run joytouch.... voila, the touchscreen pointer just worked! Great job Simon Funk!

---

### Post by envmyz on 2007-05-16
Has anyone got this joytouch to work on Ubuntu Fiesty 7.04?

I'm having one heck of a time getting results.  I've tried just about every other method with no success.

Thanks to anyone that replies

---

### Post by Longwing on 2007-05-16
Joytouch is working fine for me in Xubuntu 7.04. [Here's a current link to the page.]("http://sifter.org/%7Esimon/journal/20060413.html") Simon Funk, Joytouch creator, asks that you email him if the program works for you. His email is also available on the Joytouch page. I won't repost it here, since I've no permission from him.

Given that it works in Xubuntu, you shouldn't have any trouble setting it up for Ubuntu or Kubuntu. It's not actually a driver or other highly integrated solution. The tiny program runs like any normal program in the background as you work.

Once you've got the configuration to where you like it, you can tell it to start with the OS. I'll post some more detailed instructions as soon as I can recall them.

---

### Post by envmyz on 2007-05-17
Thanks,
What are the steps to setup (install) joytouch?  I ran sudo make for the joytouch directly and it came up with at least 20 errors, mainly libs/toybox file or folder not found.  I'm pretty new to Linux (2 weeks now) so bare with me.

Thanks

Chris

EDIT:
Nevermind, Im a NOOB I wasnt executing the program correctly. sudo ./joytouch works perfectly!! WooHoo for touchscreen in Ubuntu! Mr. Funk is the MAN! :guitar:

---

### Post by Longwing on 2007-05-17
Joytouch doesn't need compiling, it's already a binary. (The equivalent of a .exe file) To run it, simply navigate to the directory in question and type "joytouch". If using a file manager, you can just double click on the icon.

The only problem is that this will activate the default config, which might not match your touchscreen. I believe that "joytouch -help" should give you a list of commands.

I wish I had more time to give a full explanation, but I'm unfortunately quite busy. I'll post a step-by-step version as soon as I can reference it from my own laptop.

Heh, just read your edit. You probably don't even need to sudo it. If I recall correctly, it will work without needing root access.

---

### Post by objbuilder on 2008-04-08
Here's a follow-up post for anyone still struggling with setup issues. All this information is great but there's still a few little nagging issues to be resolved... so here's how:

First, you'll want to have joytouch start whenever you boot into X so to do this... add your joytouch start command to ~/.bashrc

Second, joytouch is killed whenever your laptop hibernates so you'll want to automatically restart joytouch upon waking up. I tried adding an entry to /etc/acpi/resume.d/ but for whatever reason it is ignored. So what I ended up doing is adding the following snippet to /etc/acpi/power.sh.

if [ "$(pidof joytouch)" ]
then
    bogus="nothing"
else
    # process not found
    su obj -c "(export DISPLAY=':0.0'; /home/obj/bin/joytouch-1.2/runjoy &)"
    echo "Started up joytouch"
fi

This assumes 'obj' is your UID and 'runjoy' is the name of the startup script with your calibration settings. There's probably better ways to do this.. but I'm short on bash skills.

Along the same lines, your mouse will also be disabled upon waking. To enable it again, push Fn-F4 two times.

Finally, I have gnome setup to automatically log me in. However, gnome still requires your password whenever it wakes up from hibernation. You can change these settings by opening up Applications > System Tools > Configuration Editor. Then navigate to: apps > gnome-power-manager, then scroll through the properties on the right and disable the "lock_on_xxx" options.

Hope this helps someone out there. I'm pretty happy with my setup now.  :)

---

### Post by objbuilder on 2008-04-09
It turns out that power.sh is usually called upon waking up, but sometimes it's not. Soooooo..... here are the updated scriptlets:

**In /etc/acpi/runjoy:**
[FONT="Courier New"]if ! apid=$(pidof joytouch);
then
   su obj -c "export DISPLAY=':0.0';/home/obj/joytouch-1.2/joytouch 'cal=490.925,0.016875,3.98858e-05,285.709,-2.06357e-06,0.0100274'&"
   logger Started joytouch
fi[/FONT]

Create a symbolic link in **/etc/rc5.d/** to runjoy:
[FONT="Courier New"]ln -s /etc/acpi/runjoy /etc/rc5.d/S99runjoy[/FONT]

In **In /etc/acpi/lid.sh:**
[FONT="Courier New"]if onbattery=`acpi|grep discharging`;
then
   if apid=$(pidof joytouch);
   then
      killall joytouch
      logger Stopped joytouch
   fi
fi[/FONT]

Create symbolic link in **/etc/acpi/resume.d/** to runjoy:
[FONT="Courier New"]ln -s /etc/acpi/runjoy /etc/acpi/resume.d/95-runjoy.sh[/FONT]

This starts joytouch upon booting and successfully sleeps and wakes up from suspending, however still has a problem in that the system won't hibernate until you kill joytouch.

---

### Post by RIRI!!! on 2008-07-18
Thanks!!!!!!!!!!:ks

---

