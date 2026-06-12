---
title: "Backlight Gonzo in Dell D600"
date: 2010-02-16
forum: Hardware
---

### Post by saskms on 2010-02-16
I have been up all night trying to solve this problem, and have not yet  found a successful workaround resolution to this (bug). 

At first. I though I had a blown backlight or an inverter. Every time I  booted, I would briefly get the Dell logo and then the screen would go  dark. I am running Koala on a Dell D600 laptop.

So, I lugged my old IBM monitor out of storage, and, voila, I now have a  monitor. But still no working laptop screen.

However, the strangest thing happened when I click **FN F8**. My  laptop screen flickers to life for a second or two! And, even more  curious, if I disconnect the battery cable, and click FN F8 the laptop  screen will sometimes stay on up to a minute before dimming again.

FN Up Arrow has seemingly no effect on the backlight, nor does  rebooting. 

Any help on what I am increasingly thinking is a software bug of sorts  would be greatly appreciated.

Ugh. I am at my wit's end. I tried using other LiveCDs, but still can't see my laptop screen, and I also unable to get into my BIOS configuration. 

What the heck is going on!? Thank you......

---

### Post by smc18 on 2010-02-16
> **saskms said:**
> I have been up all night trying to solve this problem, and have not yet  found a successful workaround resolution to this (bug). 

At first. I though I had a blown backlight or an inverter. Every time I  booted, I would briefly get the Dell logo and then the screen would go  dark. I am running Koala on a Dell D600 laptop.

So, I lugged my old IBM monitor out of storage, and, voila, I now have a  monitor. But still no working laptop screen.

However, the strangest thing happened when I click **FN F8**. My  laptop screen flickers to life for a second or two! And, even more  curious, if I disconnect the battery cable, and click FN F8 the laptop  screen will sometimes stay on up to a minute before dimming again.

FN Up Arrow has seemingly no effect on the backlight, nor does  rebooting. 

Any help on what I am increasingly thinking is a software bug of sorts  would be greatly appreciated.

Ugh. I am at my wit's end. I tried using other LiveCDs, but still can't see my laptop screen, and I also unable to get into my BIOS configuration. 

What the heck is going on!? Thank you......

It sounds like you already knew the answer but then second guessed yourself.

I'm also leaning towards a bad LCD backlight or inverter.  If you hook up an external and the external monitor works but the laptop LCD screen no longer works it's most likely the backlight or inverter.

Once the laptop is turned on, and your display goes dim, can you look very closely and still see images?  (Imagine if everything on the screen looks bright but then it goes dim, your text, GUI, login screen should still be seen very faintly up close.)

If you've tried to boot to Live CD's and the issue still happens, that makes me think it's even more likely your display is gone.  Booting off different distribution Live CD's makes me think it is not a software issue at all.

Here is another tip.  When you first turn on your laptop, does anything that would normally have white text appear pink or red?

Sadley, I do alot of hardware repair that includes LCD repair at work rather than cool server work, but alot of LCD's I repair, the backlight bulbs always glow red before they go dim/out.

---

### Post by saskms on 2010-02-16
Yes, it appears vaguely pinkish. Yet, with an external monitor connected, if I click FN F8 the laptop screen springs to life and appears totally normal with no anomalies in screen brightness or colour. 

It seems like something is forcing the laptop into dimming the backlight. IF the backlight were fried or the inverter was gobbled, surely I would not be able to see anything when I click on FN F8, right?

But the laptop screen is totally normal, if only for a few seconds, after I click FN F8. And if I disconnect the silly battery cable, and click FN F8 the laptop screen will stay totally normal for up to 20 seconds before dimming out again. 

My brain hurts. lol.

---

### Post by saskms on 2010-02-16
Surely there must be a way to force the backlight to stay on.......?

---

### Post by oldnoob on 2010-02-16
Sorry this is long but I'm a bit frustrated with backlight issues too.

I am having similar problems with Linux Mint 8 on a C640 and had these problems when running 8.04.  I'm giving Linux Mint a try since I just replaced the hard drive.  Of course Mint is based on Ubuntu.

I'm trying to recall what I did to the config with 8.04, but what I ended up with was I had to boot up with AC unplugged.  As soon as the BIOS screen was cleared I could plug it in and let the boot up continue.  Once up and running, I could unplug from AC (and back) with no problems.  The main thing was to make sure I turned on the laptop while unplugged from AC.

Now with Linux Mint 8, my problems are more complex.  I have to go through the entire boot process on battery, and I have to have the brightness (battery mode) in the BIOS set no higher than 5/8 of the way to max.  If I try to set the brightness higher than 5/8, or use AC, I'll get to the LinuxMint logo during the bootup but at the final step before the login screen, it goes black.  It's booting up fine but no backlight.  I end up using an LED at an angle to "barely" make out the screen so that I can login and logout.  Then I'll have to go back into the BIOS to set the brightness back to 5/8 or less.  The bottom line is boot up in battery, and I only get to use the brightness at 5/8.  It's useable, but not ideal.

The other thing I've discovered is that my brightness controls do not work on the keyboard.  At least that was working in 8.04.  

When I had the original problems with 8.04, I too suspected the inverter.  I went to one of the local computer shops where they have a number of Linux advocates and they convinced me it was not the inverter but related to the software and bootup process.  Based on my experiences over the last year or so, I agree.  But it is still a problem that annoys me.

---

### Post by waynefoutz on 2010-02-17
This is interesting. My last laptop was a C640, and my daughter's laptop is a D600. The C640 ran Intrepid with no problems, and my daughter's D600 is running Linux Mint 8, and the only problem on it is sometime it has a kernel panic coming out of hibernation.

---

