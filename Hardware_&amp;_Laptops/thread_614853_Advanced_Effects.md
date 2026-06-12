---
title: "Advanced Effects"
date: 2007-11-16
forum: Hardware &amp; Laptops
---

### Post by DoocesWild on 2007-11-16
I can't get my "normal" or "advanced" settings to work.  At first, as soon as I'd click either of them, I'd get a box that said "the composite extension is not available".  I changed from 0 to 1 the composite section in the conf file.  Now, it says "desktop effects could not be enabled"

Then I tried this:
2. Get Xorg.conf ready:
gconftool-2 -s '/apps/metacity/general/compositing_manager' --type bool true

Add the following in /etc/X11/xorg.conf:

Section "Extensions"
Option "Composite"
EndSection

In the "Device" section, add:
Option "AddARGBGLXVisuals" "True"

In the "Module" section, add:
Load "extmod"

Now, it flickers a few times, then says the same thing, "desktop effects could not be enabled"

I haven't tried anything else, so the answer to future questions of "have you tried...?" will result in a "no" :)

What should I try?  If there are some commands in terminal I should run to tell you guys what drivers/hardware I'm using, let me know and I'll gladly post anything I can.

Thanks in advance!

---

### Post by Necrome on 2007-11-16
I do not know too much about the commands from the terminal. But after the install, the initial setup of my gutsy did not have the compiz advanced desktop effects. To get them i had to:
System->Admin->Synaptic Package Manager->Settings->Repositories->Ubuntu S/W
I enabled them all
System->Admin->Synaptic Package Manager->Settings->Repositories->Third-Party S/W
I enabled them all
System->Admin->Synaptic Package Manager->Settings->Repositories->Updates
I enabled them all

I cannot confirm the security levels of all of these repositories. However, after enabling them you can find the compiz related stuff in the syanptic package manager. Downloading these enables you to see:
System->Preferences->Advanced Desktop Effects Settings

Hope this helps..

---

### Post by DoocesWild on 2007-11-16
Thank you very much.  When I get off work I can do this (can't connect my laptop to the company network).

---

### Post by DoocesWild on 2007-11-16
Actually, now that I look at this, I have already enabled all of the repositories.  What should I download while I'm in synaptics?

I'm up to date on everything

---

### Post by DoocesWild on 2007-11-17
I did a search for compiz and downloaded everything.  Yes, it does show an advanced menu now.  Should I be able to click normal or advanced settings?

---

### Post by Necrome on 2007-11-17
> **DoocesWild said:**
> I did a search for compiz and downloaded everything.  Yes, it does show an advanced menu now.  Should I be able to click normal or advanced settings?

Do the animations work now? You can click on the advanced settings and change/set the animations and all the controls.

---

