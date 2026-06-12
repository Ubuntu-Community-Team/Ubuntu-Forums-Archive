---
title: "Restricted Drivers [Graphics]"
date: 2009-06-28
forum: Hardware
---

### Post by 0pul3nce on 2009-06-28
I'm tempted to just ignore any messages i get from Ubuntu now, because last time i clicked on a message about restricted drivers for my graphics card i went through the *activate* and then i killed my computer, and nothing would work, i had to reformat ect...

Under 
System > Hardware Drivers

I get this message, 

"No proprietary drivers are in use on this system.

Proprietary drivers do not have public source code that ubuntu developers are free to modify. They represent a risk to you because they are only available on the type of coputer chosen by the manufacturer, and security updates to them depend solely on the responsiveness of the manufacturer. Ubuntu cannot fix or improve these drivers"

In the box below it then says

"Nvidia accelerated graphics driver (version 180) [Recommended]"

In the box below it then says

"3D-accelerated proprietary graphics driver for NVIDIA cards.

This driver is required to fully utilise the 3D potential of NVIDIA graphics cards, as well as provide 2D acceleration of newer cards.

If you wish to enable desktop effects, this driver is required.

If this driver is not enabled, you will not be able to enable desktop effects and will not be able to run software that requires 3D acceleration, such as some games."

Below that is says THIS DRIVER IS NOT ACTIVATED. From previous experience when i clicked activate my machine wouldn't boot up.

please could you advise me how to proceed.

----------The graphics card i have is nvidia 8600 Inno3D

---

### Post by howefield on 2009-06-28
> **0pul3nce said:**
> please could you advise me how to proceed.

Have you tried an earlier nvidia driver ?

eg, my hardware driver gives me the option of 173 or 180

In any event, have a look at clonezilla or similar which will take an image of your drive and at least allow you the comfort of being able to reimage your disk in the event of disaster,  in a matter of minutes.

---

### Post by Dysport on 2009-06-28
> **howefield said:**
> 
In any event, have a look at clonezilla or similar which will take an image of your drive and at least allow you the comfort of being able to reimage your disk in the event of disaster,  in a matter of minutes.

That would be my advice too. Back your current configuration up - personally I'd just tar everything in an archive on an externeal drive - and try the driver. From _my experience_ the current proprietary NVidia drivers work just fine, so you could risk doing it without a "backup parashute". But then again something always can go wrong, so backing up won't hurt.

Here's a simple terminal-command for a full system backup (you may need root access):

```
cd / && tar cvpzf backup.tgz --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/media /
```

Then just move the backup.tgz from your root directory to the backup location (eg. external or network drive).

---

### Post by 0pul3nce on 2009-06-28
I finally got it working this time.

Btw could anyone tell me why i can't use the quick reply box at the bottom of the screen

---

### Post by wizardfait on 2009-06-28
I know I have an ATI instead of an NVidia card, but I reciently tried installing a proprietary driver, as opposed to the free one, and it prevented me from booting up as well. My advice to you, if you don't want to use a backup method, find out what packages it's installing, and write down the names of them, or at least one of them, then if it breaks, boot into recovery mode (Or w/e Ubuntu calls it (Sorry, more of a Windows guy, but I'm learning... :D)) and drop to a root prompt (With networking if you want) and then run synaptic or just apt-get remove the package. And make sure it fixes dependencies. (I  know going through synaptic, it'll warn you that you've "broken" some things, and allow you to tell it to automatically fix them (By removing them).

---

### Post by howefield on 2009-06-28
> **0pul3nce said:**
> I finally got it working this time.

Btw could anyone tell me why i can't use the quick reply box at the bottom of the screen

Good to hear you are sorted.

To use the quick reply box, you need to "activate" it by clicking on the bottom right icon of the post you are replying to.

---

### Post by 0pul3nce on 2009-06-29
> **howefield said:**
> Good to hear you are sorted.

To use the quick reply box, you need to "activate" it by clicking on the bottom right icon of the post you are replying to.
like this...I think i've got the quick reply working. Thanks for the advice.

---

### Post by 0pul3nce on 2009-07-12
Is there a way i can delete this?

---

