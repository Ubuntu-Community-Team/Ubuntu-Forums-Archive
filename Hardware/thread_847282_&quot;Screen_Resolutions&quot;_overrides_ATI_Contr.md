---
title: "&quot;Screen Resolutions&quot; overrides ATI Control Center"
date: 2008-07-02
forum: Hardware
---

### Post by Harry Muscle on 2008-07-02
I'm trying to configure my Dell Vostro 1000 to work with an external monitor that has a different resolution than the internal screen.  I can get things to work fine using the ATI Control Center, however, as soon as I reboot things mess up.  When first booting up, the resolution is correct for the first 2 seconds or so, however, a split second before the menu bar, etc. appears the resolution changes to the resolution specified in the "Screen Resolutions" section in System | Preferences.

The problem is that in "Screen Resolutions" the maximum available resolution is 1280x800 (my internal screen resolution), however, I need a higher resolution for my external monitor.  ATI Control Center picks up on this and changes things fine, however, after the reboot, it's the "Screen Resolutions" setting that seems to override the ATI Control Center settings.

Is there anyway to either disable the "Screen Resolutions" and control everything thru the ATI Control Center?  Or possible, add additional resolutions to the list available in "Screen Resolutions"?

Thanks,
Harry

---

### Post by phidia on 2008-07-02
Do you know about twinview or is that not what your after?
There is a thread that might be related [here]("http://ubuntuforums.org/showthread.php?t=59650&highlight=twin+view"). 

There is [a thread]("http://ubuntuforums.org/showthread.php?t=832146&highlight=external+monitor") saying that ATI in linux doesn't support external monitors but I'm not a ATI expert. And while [this]("http://ubuntuforums.org/showthread.php?t=515573&highlight=external+monitor") is a long thread there is some info there.

---

### Post by Harry Muscle on 2008-07-02
Thanks for those links ... but they seem to address different issues that what I'm dealing with.  The first one seems to be about not being able to display to an external monitor at all ... I can do that as long as I use ATI Control Center to configure things.  The second one is about TwinView, which is not what I'm after.  I'l like to be able to use either the internal or external display, not both.  The third one is more about actual driver installation, which went fine on mine and it works great.  It's actually Ubuntu that's messing up what the driver is trying to do via the ATI Control Center.

Basically I'm hoping to find a way to either disable the resolution control in the "System | Preferences" section or to add resolutions that are not listed there already.

Thanks for those links though,
Harry

---

### Post by Harry Muscle on 2008-07-02
I did some more testing, and the problem seems to be that the ATI drivers prevent Ubuntu from properly detecting a second display.

Here's what I did.  I reinstalled Ubuntu and everything works just the way I want it to (external display is detected and listed in "Screen Resolutions" and has the correct resolution, etc.).  However, I need the proprietary drivers for my ATI card to work better.  However, as soon as I install the drivers (from the repository) the problem is back.  "Screen Resolutions" no longer lists a second display and the external monitor now has the wrong resolution.

So basically I can get things to work if I don't install the needed 3D drivers and I can get things to work with the 3D drivers if I use the ATI Control Center, however, as soon as I reboot the settings from the ATI Control Center get overridden by the "Screen Resolutions" settings which don't work if the ATI drivers are installed ... any help is highly appreciated.

Thanks,
Harry

---

### Post by markbuntu on 2008-07-02
You should not be using "Screen Resolutions" at all if you have the ati driver installed.

btw, how did you go about getting and installing the ati driver?

---

### Post by Harry Muscle on 2008-07-02
> **markbuntu said:**
> You should not be using "Screen Resolutions" at all if you have the ati driver installed.

btw, how did you go about getting and installing the ati driver?

I installed the drivers thru the Hardware Devices program build into Ubuntu.  I also tried everything by installing the drivers thru EnvyNG ... same problem with both methods of installation.

Btw, I'm not actually trying to use "Screen Resolutions", however, I figured out that it's the setting listed in "Screen Resolutions" that it's reverting back to.  So for example if I setup everything just right with the correct resolutions for the internal display and external display using the ATI Control Center however, prior to doing these changes, the "Screen Resolutions" listed the internal display (it doesn't detect the external display with the ATI driver installed) as 800x600 here's what will happen during boot up:

Graphical Interface comes up with correct resolution settings and then about 2 seconds later (before the menus appear, etc.) it will revert back to 800x600.  If "Screen Resolutions" has something else listed it will revert to whatever other resolution it has listed.

Thanks,
Harry

P.S.  I'm thinking the root cause of this might be that "Screen Resolutions" doesn't detect the external display when the ATI drivers are installed.  It does detect it though when the ATI drivers are not installed and everything works just fine then ... except for 3D acceleration, etc. which I need unfortunately.

---

