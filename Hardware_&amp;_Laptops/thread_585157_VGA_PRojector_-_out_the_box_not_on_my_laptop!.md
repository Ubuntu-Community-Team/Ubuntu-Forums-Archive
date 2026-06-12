---
title: "VGA PRojector - out the box? not on my laptop!"
date: 2007-10-21
forum: Hardware &amp; Laptops
---

### Post by walding on 2007-10-21
Hi,

Gutsy is meant to work with VGA projectors out of the box.  But I can't get it to connect, whereas I could with Feisty!
I have the Nvidia-glx-new driver installed on my Asus A6VM laptop.  In Ubuntu, I can't get the projector to work.  I Kubuntu on the same laptop, I have to remove nvidia-glx-new and install nvidia-settings to get it to work.

I like the nvidia-glx-new driver.  Am I doing something wrong?

My projector is a Hitachi CP-RX60.  It's been working fine on the same laptop running Feisty, Edgy & DApper...

ANy help appreciated.

THanks!

---

### Post by dietrying on 2007-10-21
is it not possible to use the new NVIDIA-glx-new in combination with nvidia-settings? I think it should be possible to switch the output screen in the nvidia-settings tool? Wich way you switch the signal from your laptop to the projector?

---

### Post by walding on 2007-10-21
No - if I try to install nvidia-settings, it automatically removes nvidia-glx-new!
I can't "switch signal" as the Fn-F8 button has never managed that on this laptop running Linux (only Windows).  I just set it to clone permanently, which works just fine.

I had such high hopes for Gutsy, having read that the VGA would work "out the box".  Shame, really.

---

### Post by dietrying on 2007-10-21
on my notebook vga-out didn't work out of the box also (i945), but i got solved this by switching back to i810 driver.
But anyway for your problem, perhaps you could try to install the driver from the nvidia site if you want because on my desktop pc i did that (for another reason) and have nvida driver with nvidiasettings tool both installed and working.......don't know how good it will work for you, so it's on your own risk. 
I have no other ideas as far.......
greetings

---

### Post by steveneddy on 2007-10-21
I have thought about installing the proprietary driver to correct my issues. I don't think that I am ready yet because I don't like recompiling nVidia drivers after each kernel update.

:popcorn:

---

### Post by dietrying on 2007-10-21
I have thought about installing the proprietary driver to correct my issues. I don't think that I am ready yet because I don't like recompiling nVidia drivers after each kernel update.

i can understand that, i wouldn't like to prefer this option too, only if everything else doesn't work:guitar:

---

### Post by walding on 2007-10-22
Ah - I found this:  [https://bugs.launchpad.net/ubuntu/+source/nvidia-settings/+bug/72979](https://bugs.launchpad.net/ubuntu/+source/nvidia-settings/+bug/72979)

It appears that nvidia-settings is packaged with the nvidia-glx-new.  It's just not in the menu!  Must admit I had not tried to launch via Alt-F2.

I have to manually set up the projector as with Feisty, but at least I can get it to work.

---

### Post by jtprince on 2007-12-04
This burned me in a job interview in front of a large audience, actually.  I'd done several presentations under Feisty and Dapper (they both worked on bootup) and then under Gutsy I just got a 'no signal' [had to reboot to Windows (*gasp*) to do the presentation].  Today I found this wiki page  and worked with nvidia-settings to try and get it working for my latest presentation.  Using 'twin screens' I can get a portion of the screen displayed on the projector.  However, when I go in to change the resolution settings for the 'CRT' (projector), there are only 3 options: Auto, and two really low resolutions that would be impractical to actually use (something like 300x170 [I'm writing this from memory]).  Using the low resolutions I can show a small portion of my screen.  I really don't want to have to mess with xorg.conf if possible, but I'm guessing I will have to go in and add resolutions.

Since connecting to an LCD projector doesn't work out of the box anymore, does anyone have a sure-fire sequence in order to use an LCD project at a reasonable resolution (say 1024x768).  My feeling is that this is one of those areas that should 'just-work'.  (I'd still almost rather do my presentation on half a Ubuntu screen than the alternatives ;).  I'm using nvidia-glx-new [enabled the restricted drivers] with Nvidia GeForce Go5200 (64MB).  Thanks for any pointers.

---

