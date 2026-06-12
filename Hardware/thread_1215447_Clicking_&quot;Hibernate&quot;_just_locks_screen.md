---
title: "Clicking &quot;Hibernate&quot; just locks screen"
date: 2009-07-17
forum: Hardware
---

### Post by guitarMan666 on 2009-07-17
I have a Dell Inspiron 1545 laptop that came with Ubuntu Intrepid on it.  After upgrading to Jaunty the behavior when "Hibernate" is clicked, either in the user applet on the panel or from the box that comes up when the power button is pressed, is identical to clicking "Lock Screen." It just brings up the screensaver and requests a password when the mouse is moved. The same thing happens when "Suspend" is chosen.

Any ideas what might be the matter?
Thanks in advance!

---

### Post by thychamp on 2009-07-27
I also recently purchased a Dell Inspiron 1545 pre-loaded with Ubuntu 8.10 that I subsequently upgraded to Ubuntu 9.04.

Suspend and hibernate just go to the "lock screen" as well.  How do I change this behavior so that it actually suspends and / or hibernates the laptop?

---

### Post by thychamp on 2009-07-27
I have been tried a suggestion from the following url:

[http://www.thinkwiki.org/wiki/Install_Ubuntu_8.10_(Intrepid_Ibex)_on_a_ThinkPad_T400#Suspend.2FHibernate]("http://www.thinkwiki.org/wiki/Install_Ubuntu_8.10_(Intrepid_Ibex)_on_a_ThinkPad_T400#Suspend.2FHibernate")

After doing the suggestion with the 00_CPU file it doesn't immediatly go to the "lock screen" anymore.  It seems to try to suspend then fails.  Ubuntu 9.04 must take you to the "lock screen" when suspend or hibernate fail.

Are there some log files that anyone can suggest that I look at to trouble-shoot the issue?  Since I am using the onboard graphics, I don't believe it is a video driver issue.  Could it be the Brocdcom STA wireless driver?

Thanks for any suggestions.  -Chad

---

### Post by thychamp on 2009-07-31
I got it working! Here is how.

I did some more research and found that there is a utility called uswsusp that can do suspend and hibernate.  I found information regarding it at this url: [http://www.linuxscrew.com/2007/09/06/get-suspendhibernate-working-fast-in-ubuntu-feisty-fawn-704/](http://www.linuxscrew.com/2007/09/06/get-suspendhibernate-working-fast-in-ubuntu-feisty-fawn-704/)

What I did was:

```
sudo apt-get install uswsusp
```

Then I simply tried:

```
sudo s2ram -f
```

**Viola it worked with a Dell Inspiron 1545.**  The information below is if you want to take it a step further.

_Creating a desktop icon:_
I created a desktop icon and updated visudo so that with a simple double click of the icon it goes to sleep.  More information about visudo I found here: [http://ubuntuswitch.blogspot.com/2008/02/ubuntu-shutdown-shortcut.html](http://ubuntuswitch.blogspot.com/2008/02/ubuntu-shutdown-shortcut.html)

To create a desktop icon I found that information here: [http://ubuntuforums.org/archive/index.php/t-413377.html](http://ubuntuforums.org/archive/index.php/t-413377.html)

_Having it work with HAL_
The first link I provided also describes how to get uswsusp to work when you click suspend or hibernate.  I tried it and it worked as well except that when the laptop came out of sleep the network was disabled and I had to reselect my wireless network.  It must be something with hal that causes this.  I find it to be convenient so I have been using the desktop link instead so that I don't have to deal with the network being turned off.

---

### Post by johndoe32102002 on 2009-08-07
I have a Winbook V350 laptop and the suspend works fine, but when I try to Hibernate, it simply locks the screen.  Is there a fix that works just for the Hibernate without changing the suspend?

---

### Post by thychamp on 2009-08-08
The quickest way would be to trying using uswsusp as I describe above and create a desktop icon that you can double click on to go into hibernate.  I would first try using uswsusp from the command line to verify that it will hibernate your system correctly.

If uswsusp doesn't work I don't know how you can get it working.

---

### Post by guitarMan666 on 2009-08-14
Will this work with the Power preferences?  I want it to suspend (to ram) on lid-close and I want it to hibernate (to hard drive and power off) on low battery.

---

### Post by thychamp on 2009-08-15
If you modify the hal scripts as described in the link then it will work through the power preferences.  If you do do that will you report back after a few weeks and let me know if all seems to work well?  I only did it that way for a few days then changed it to work only when I use the desktop icon.  I didn't like how I would have to reselect my wireless network again everytime it came back from suspend.

[http://www.linuxscrew.com/2007/09/06/get-suspendhibernate-working-fast-in-ubuntu-feisty-fawn-704/](http://www.linuxscrew.com/2007/09/06/get-suspendhibernate-working-fast-in-ubuntu-feisty-fawn-704/)

---

