---
title: "Brightness autoadjusts on kde 4 (tkpad x60)"
date: 2008-05-11
forum: Hardware
---

### Post by hanoc on 2008-05-11
Hi,

I have just installed kubuntu 8.05 with kde 4.0.3 on a Lenovo Thinkpad x60 and I am not abble to _permanently_ keep my monitor brightness to 100%.

I am able to get the brightness to 100% using the integrated controls of my laptop (Fn + Home), or even using kpowersave but, no matter the way I put the brightnes to the maximum it gets almost automatically to 10% (more or less).

This "auto dimm" occurs with the AC plugged or unplugged indistinctly.

I have selected a profile in kpowersave that sets the brightness to 100% but the screen still dimms.

I have no power saving settings active on "System Settings -> Display"

I have searched in google and in the forums but I am not able to find anyting related to my problem.

Does anyone know what can I search for?
Is there anything in KDE 4 that controls the brightness?

Any directions will be greatly appreciated.

Thanks!

---

### Post by hanoc on 2008-05-12
By the way, I forgotten to say that my graphics card is an Intel Corporation Mobile 945GM and my installed drivers is xserver-xorg-video-intel.

---

### Post by imhavoc on 2008-07-30
Did you ever get this figured out? I've got 50% brightness on my notebook, and no way to set the brightness or override the brightness setting.

Thanks.

---

### Post by hanoc on 2008-07-30
Hi,

No, unfortunatelly I did not solve this one.

Guys anyone?


What I did is find a "workarround"
In my particular laptop, if I set the brightness to the maximum (or to wichever level you choose)before ubuntu starts I "keep" that brightness.

I can't really tell if you have to set the level of the brightness because it's more a trial and error thing.

This does not solve the problem anyway. if you set the brightness to the maximum you'll get the brightness to the maximum until you reboot and change your brightness.
If you reduce the brigthness with the working ubuntu it just gets to the maximum again.

---

### Post by jdmulloy on 2008-09-24
Hi, I'm having the same issue on my Toshiba M100. A BIOS upgrade made it possible to control the screen brightness from Linux but now I'm having the issue you have described. The screen brightness will change back to its previous value whenever KDE4 is on the screen. If I adjust it in KDE3 or on the terminal it sticks, even if I switch back to KDE4.

As a workaround I set it statically to it's lowest setting with the following command in /etc/rc.local

echo 10 > /proc/acpi/video/GFX0/LCD/brightness

I also have a GMA 950.

This seems to be KDE4 related but I can't find a control for it in "System Settings" I can't figure out what part of KDE is doing it.

Anyone have any progress with this?

---

### Post by jdmulloy on 2008-09-24
I've found a workaround that works on my laptop. It turns out it's the screen saver causing it. Try disabling the screen saver auto start and see if that fixes the problem. It will still reset after you lock and unlock the screen because this activates the screen saver. Try it and let me know if it works.

---

### Post by jakkalsie on 2008-09-26
Hi Guys!

I had the same problem with my laptop. If I boot into KDE4 my screen brightness was very dark and to make matters worse my function buttons that sets the brightness were also not responding. After some research and playing around I found a solution.

Open a terminal window and run the following command:

guidance-power-manager

Your screen brightness should instantly go brighter and your function buttons should too work now.

If you get command not found, you will have to install it:

sudo aptitude install kde-guidance-powermanager

I created a symbolic link inside my ~/kde.4/Autostart directory so that it runs the program at logon without me having to manually run it every time.

ln -s /usr/bin/guidance-power-manager ~/.kde4/Autostart

Let me know if this works for you!

Chow: guitar:

---

### Post by MirzaD on 2008-10-04
**jdmulloy** thank you very much, i have been banging my head about this problem.

turning off "Start Automatically" option in screen saver really solves the problem:)

---

### Post by Penguin_Newbie on 2008-10-14
> **jdmulloy said:**
> I've found a workaround that works on my laptop. It turns out it's the screen saver causing it. Try disabling the screen saver auto start and see if that fixes the problem. It will still reset after you lock and unlock the screen because this activates the screen saver. Try it and let me know if it works.

You sir, are a saviour. I salute you. :)

---

### Post by jdmulloy on 2008-10-20
Just to let everyone know it seems this has been fixed in Intrepid. I upgraded a few days ago to Intrepid and I have not seen this issue. If/When you upgrade please lets us know if it works for you.

---

### Post by squil0 on 2008-10-28
Hi,
I have a fresh install of Kubuntu 8.10 beta, and the brightness still keeps resetting after a reboot. Any ideas?

---

### Post by zoniq on 2008-10-31
I had the same problem. Turning off the screensaver "Start automatically" is NOT checked solves the problem though.

---

### Post by squil0 on 2008-11-10
Yeah, it didn't solve the problem for me either.

---

### Post by ofir_k on 2008-12-01
> **jdmulloy said:**
> I've found a workaround that works on my laptop. It turns out it's the screen saver causing it. Try disabling the screen saver auto start and see if that fixes the problem. It will still reset after you lock and unlock the screen because this activates the screen saver. Try it and let me know if it works.

Worked for me. Thanks!

Lenovo 3000 N100 with Kubuntu 8.10 LiveCD

---

### Post by timmahhny on 2008-12-11
Thanks brother. That helped a great deal, it worked perfectly. I can now see:guitar:

> **jakkalsie said:**
> Hi Guys!

I had the same problem with my laptop. If I boot into KDE4 my screen brightness was very dark and to make matters worse my function buttons that sets the brightness were also not responding. After some research and playing around I found a solution.

Open a terminal window and run the following command:

guidance-power-manager

Your screen brightness should instantly go brighter and your function buttons should too work now.

If you get command not found, you will have to install it:

sudo aptitude install kde-guidance-powermanager

I created a symbolic link inside my ~/kde.4/Autostart directory so that it runs the program at logon without me having to manually run it every time.

ln -s /usr/bin/guidance-power-manager ~/.kde4/Autostart

Let me know if this works for you!

Chow: guitar:

---

