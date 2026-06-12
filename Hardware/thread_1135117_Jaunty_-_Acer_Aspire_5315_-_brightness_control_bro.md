---
title: "Jaunty - Acer Aspire 5315 - brightness control broken"
date: 2009-04-24
forum: Hardware
---

### Post by iTawm on 2009-04-24
I have an Acer Aspire 5315, and after upgrading to Jaunty, my brightness controls don't function very well.
I can lower the brightness no problem, but when trying to raise the brightness (using the keyboard shortcuts) it seems to increase by two steps, and then decrease by one, causing an ugly flickering effect, and the brightness gauge that pops up doesn't change to reflect how bright it actually is. Further, after it gets to a certain brightness level, it drops down to two steps above the minimum brightness (still showing as 0 brightness though)
I'm able to use the panel applet to actually control it, but doing this still causes the flickering effect on the screen, and it is prone to prolonged flickering when setting it to max brightness using the applet.

Are there are any workarounds or fixes for this?

---

### Post by mongoose550 on 2009-04-26
I've had exactly the same problem on my Aspire 5720 since upgrade to Jaunty, any help on this would be much appreciated!

---

### Post by MightySeb on 2009-04-26
I have the exact same problem.
My laptop is an "Acer Aspire 5315-2381"

When trying to adjust brightness, the screen seems to "flick" (like a strobe) three or four times between each brighness steps.

*******
Update :

These guys seems to have a similar problem too.
[http://ubuntuforums.org/showthread.php?t=1137705](http://ubuntuforums.org/showthread.php?t=1137705)

---

### Post by iTawm on 2009-04-29
I've found the source of the problems: gnome-power-manager
Looking at the info in the other thread, I checked to see if I could adjust it properly in another tty, no dice. Also, I tried uninstalling acpi-support. Another failure.
I noticed that the problem doesn't occur until after I've logged on, and only once logged into gnome - the problem didn't exist when no user was logged in on the tty with the X server running.
On a hunch, I checked out the scripts that run at login for GNOME. After disabling all of them that I thought could be the problem, to no avail, I decided to just turn all of them off and see if the problem really was in the startup applications. It was. I scrolled through and looked at the ones that had been on when I was going one-by-one, and decided that power-management was the most likely cause. I turned them all back on, sans power-management. Logged out, and logged back in. Miraculously, my brightness controls worked. I pulled up the power-management window via preferences, and when it started, my screen flickered again. Rapidly. And then the brightness control was gone. Killing gnome-power-manager fixed the problem though.

I went ahead and submitted a bug report: [https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/369169](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/369169)

---

### Post by dmm1983 on 2009-04-29
my problem only happens with the flick when you log in.
but other then that it works fine with the bright function keys.

my machine is a acer travelmate 2410 series, kubuntu 9.04

---

### Post by MightySeb on 2009-04-29
I can confirm that killing power-manager makes the brightness controls useable again.

My laptop is an Acer aspire 5315-2381.

Thanks for your efforts iTawm.

---

### Post by rodrigocastrillon on 2009-05-08
Same issue on mine Acer Aspire 5315-2940.
I disabled the gnome-power-manager on my startup and now brighness works properly... Let's hope that Ubuntu team fix it soon :)

Good job iTawm!

[COLOR="Red"][B]EDIT:
[/B][/COLOR]
Maybe a fix?? --> [https://bugs.launchpad.net/ubuntu/+source/hal-info/+bug/327707](https://bugs.launchpad.net/ubuntu/+source/hal-info/+bug/327707)
In the bug report, one poster says that bug is resolved in the latest hal-info... 
I'll try to install it, then I post the results here.


**[COLOR="Red"]EDIT2:[/COLOR]**
Installing a newer hal-info does not fix the issue.
But I noticied that there is a newer gnome-power-manager, that I'll try to compile ([gnome-power-manager_2.26.1.orig.tar.gz]("http://archive.ubuntu.com/ubuntu/pool/main/g/gnome-power-manager/?C=M;O=A")). I'll also try to install Intrepid's g-p-m and see how it performs...

[COLOR="Red"]**EDIT3**[/COLOR]
Well... Installing an older package does not work (brighness dont increase at all, using FN + >).
And after downloading a ton of dev packages, make gnome-power-manager_2.26.1 fails because the script looks for a file that does not exist (/usr/share/xml/gnome/xslt/docbook/omf/de - "de" is the file missing). This folder is created by package gnome-doc-utils.

:(

---

### Post by Stegga on 2009-05-20
There is a BRIGHTNESS widget thing, if you click on the panel (on top by default) and Add to Panel, there is a brightness 'icon' to add which overcomes this.

I have the Aspire 5710 and it works great.
Andrew

---

### Post by iTawm on 2009-05-20
> **Stegga said:**
> There is a BRIGHTNESS widget thing, if you click on the panel (on top by default) and Add to Panel, there is a brightness 'icon' to add which overcomes this.

I have the Aspire 5710 and it works great.
Andrew

I've already tried using the applet. See my first post :]
> **iTawm said:**
> I'm able to use the panel applet to actually control it, but doing this still causes the flickering effect on the screen, and it is prone to prolonged flickering when setting it to max brightness using the applet.

---

### Post by His on 2009-06-07
I've been having a same problem, I'm on a aspire 5720. Is anyone else having overheating issues too?

---

### Post by iTawm on 2009-06-08
> **His said:**
> I've been having a same problem, I'm on a aspire 5720. Is anyone else having overheating issues too?

Occasionally, in my case, I've found that controls for the fan cease after coming back from a suspended state induced by gnome-power-manager.

---

### Post by Person_1873 on 2009-06-10
i've been experiencing this problem also on an Acer Aspire 5315 laptop, can confirm brightness controls work flawlessly when you kill gnome-power-manager however the brightness applet ceases to work with this solution so i cannot confirm that this *"fix"* resolves the issue on that front

looking forward to a patch for this annoyance

---

### Post by MightySeb on 2009-06-11
> **His said:**
> I've been having a same problem, I'm on a aspire 5720. Is anyone else having overheating issues too?

For the overheating, I had a similar problem with my Acer 5315. I fixed it by updating the bios to the latest version.

On [Acer's website]("http://www.acer.ca/acer/service.do?LanguageISOCtxParam=en&miu10einu24.current.attN2B2F2EEF=3751&sp=page15e&ctx2.c2att1=27&miu10ekcond13.attN2B2F2EEF=3751&CountryISOCtxParam=CA&ctx1.att21k=1&CRC=719687231"), you can check the latest version of the bios...but the update utilty only works on Window$ XP/Vista.

---

### Post by iTawm on 2009-06-11
> **MightySeb said:**
> For the overheating, I had a similar problem with my Acer 5315. I fixed it by updating the bios to the latest version.

On [Acer's website]("http://www.acer.ca/acer/service.do?LanguageISOCtxParam=en&miu10einu24.current.attN2B2F2EEF=3751&sp=page15e&ctx2.c2att1=27&miu10ekcond13.attN2B2F2EEF=3751&CountryISOCtxParam=CA&ctx1.att21k=1&CRC=719687231"), you can check the latest version of the bios...but the update utilty only works on Window$ XP/Vista.

Fantastic, thanks for the info.
Guess I'll have to reinstall Vista sometime soon then.

---

