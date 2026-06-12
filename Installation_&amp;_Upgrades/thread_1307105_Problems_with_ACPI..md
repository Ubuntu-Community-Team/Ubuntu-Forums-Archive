---
title: "Problems with ACPI."
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by Incendia on 2009-10-30
I have issues with my laptop and Linux.

So far I have found Ubuntu 9.10 to be the most compatible distro (before its release it was Mandriva). My wireless finally works, it looks pretty, and it actually realises my graphics card exists.

Although, I still have ACPI problems. It **refuses** to boot without the options ACPI=Off and NolACPI. This isn't just Ubuntu: it is all distros.

Now, I thought I could live happily without ACPI and just use Linux when connected to the mains. However as it gets too hot I never manage to complete the installation of Ubuntu before my computer turns itself off.

This is obviously quiet upsetting and frustrating as you can imagine.

Do any of you have any ideas on how I can fix this?

Below is my hardware if that will be of assistance.
Thank you.

[ATTACH]133811[/ATTACH]

---

### Post by alex.rayu on 2009-10-31
Wow your computer turns off before you manage to install Ubuntu?

---

### Post by Incendia on 2009-10-31
> **alex.rayu said:**
> Wow your computer turns off before you manage to install Ubuntu?

Yes.

---

### Post by alex.rayu on 2009-10-31
Have you tried advanced options when booting from live cd? If that fails, there should be an alternative cd.

As far as I know acpi is controlled on the kernel level, so it is not something trivial. It is also very strange that that would not work for you out of the box.

---

### Post by Incendia on 2009-10-31
> **alex.rayu said:**
> Have you tried advanced options when booting from live cd? If that fails, there should be an alternative cd.

As far as I know acpi is controlled on the kernel level, so it is not something trivial. It is also very strange that that would not work for you out of the box.

What exactly do you mean by advanced options? When I push F6 I select nolacpi and acpi=off for it to work in the other options :/

I know it is strange, I've never had this problem before and it seems no one else is either. :/

---

### Post by kubug on 2009-10-31
Hi there, (came over from the CD Label thread)

Have you made sure that you don't have a hardware issue? Does Windows run stable? If it seems to run stable, try running "Orthos" or "Prime95" on your computer for a couple hours and see if it is stable.

Prime95 (32 bit) [Link]("http://files.extremeoverclocking.com/file.php?f=103") If you need 64 bit, just follow the link on that page.

If it the hardware test fails under Windows as well you may have some bad hardware somewhere.

The other option is to run the Memtest in Grub. When you boot up, press ESC when GRUB comes up. Select Memtest and let it go through a complete pass. 

If all of that brings no errors, at least you know that it is not a hardware problem you are facing.

---

### Post by Incendia on 2009-11-01
> **kubug said:**
> Hi there, (came over from the CD Label thread)

Have you made sure that you don't have a hardware issue? Does Windows run stable? If it seems to run stable, try running "Orthos" or "Prime95" on your computer for a couple hours and see if it is stable.

Prime95 (32 bit) [Link]("http://files.extremeoverclocking.com/file.php?f=103") If you need 64 bit, just follow the link on that page.

If it the hardware test fails under Windows as well you may have some bad hardware somewhere.

The other option is to run the Memtest in Grub. When you boot up, press ESC when GRUB comes up. Select Memtest and let it go through a complete pass. 

If all of that brings no errors, at least you know that it is not a hardware problem you are facing.


There is no issue with my hardware on Windows and I can't manage to install Grub. (As with no ACPI it overheats and turns itself of before it blows up as a safety thing. So I never manage to finish the installation).

---

### Post by kubug on 2009-11-01
ACPI handles your power management, including throttling down your CPU when not in use. Since in Windows your ACPI works, it will "step" your CPU down to consume a lower amount of power when not in use. This will also lower the CPU temperature, which seems to be the culprit in the restart issue you are having.

See, the issue is that your computer restarts when it gets hot. This should not happen, even with ACPI off. 

By running the Prime95 program in Windows, you are essentially doing the same thing as the Ubuntu install process... you are running the CPU 100% (or close to it). If you are getting an error within your Prime95 run, it points to either bad cooling on the CPU or something else. 

On the other hand, if the Prime95 run continues without a hitch for a couple hours, you can rest assured say that it is not the CPU overheating that causes the issue.

---

### Post by kubug on 2009-11-01
Oh, and I forgot, if you don't have GRUB, don't worry. You can select memtest on the install CD (Desktop CD) when you get the menu at the start. 

Try that one too to make sure your memory is ok as well.

---

### Post by Incendia on 2009-11-01
> **kubug said:**
> ACPI handles your power management, including throttling down your CPU when not in use. Since in Windows your ACPI works, it will "step" your CPU down to consume a lower amount of power when not in use. This will also lower the CPU temperature, which seems to be the culprit in the restart issue you are having.

See, the issue is that your computer restarts when it gets hot. This should not happen, even with ACPI off. 

By running the Prime95 program in Windows, you are essentially doing the same thing as the Ubuntu install process... you are running the CPU 100% (or close to it). If you are getting an error within your Prime95 run, it points to either bad cooling on the CPU or something else. 

On the other hand, if the Prime95 run continues without a hitch for a couple hours, you can rest assured say that it is not the CPU overheating that causes the issue.

There was nothing wrong with my CPU running at 100% on Windows for two hours. :/

> **kubug said:**
> Oh, and I forgot, if you don't have GRUB, don't worry. You can select memtest on the install CD (Desktop CD) when you get the menu at the start. 

Try that one too to make sure your memory is ok as well.

I've not done the memtest yet but what does it have to do with the ACPI not working?

---

### Post by GepettoBR on 2009-11-01
Have you checked all your BIOS options for any that might be related to the problem?

---

### Post by Incendia on 2009-11-01
> **GepettoBR said:**
> Have you checked all your BIOS options for any that might be related to the problem?

Unfortunately I haven't seen anything related to ACPI in the slightest that might solve the issue. :/

---

### Post by kubug on 2009-11-01
> **Incendia said:**
> 
I've not done the memtest yet but what does it have to do with the ACPI not working?

Mostly nothing. It's just a simple test, and then you can go from there knowing it's ok. Most trouble shooting of a PC is by trial and error.

Now, since it's not an overheating issue with your PC, we need to figure out why your computer is shutting down during the install.

Does it stop at the same spot everytime?

---

### Post by kubug on 2009-11-02
Ok, after searching your Laptop model and ACPI, I found your old threads. It would have been helpful to know that this is not a new problem (i.e. this is not your first time installing linux) and that you started to look into this a long time ago.

But I do believe there is a BIOS upgrade for your laptop, and that may fix the ACPI issues you have. It may not. But it's a start.

Here is the link: [http://support.packardbell.com/uk/item/index.php?i=7447720300&pi=platform_vesuvio_a]("http://support.packardbell.com/uk/item/index.php?i=7447720300&pi=platform_vesuvio_a")

Update your BIOS and try it again. 

Also, if that didn't work, here is a resource to find a possible fix:

[http://tuxmobil.org/pb.html]("http://tuxmobil.org/pb.html")

Let us know what happened.

---

### Post by GepettoBR on 2009-11-02
> **kubug said:**
> It would have been helpful to know that this is not a new problem (i.e. this is not your first time installing linux) and that you started to look into this a long time ago.

> **Incendia said:**
> Although, I still have ACPI problems. It **refuses** to boot without the options ACPI=Off and NolACPI. **This isn't just Ubuntu: it is all distros.**

Hmm...

---

### Post by kubug on 2009-11-02
What I meant with the comment was to list the previous steps he had already done to address the issue. If I would have known that I probably would not have suggested looking at his hardware, since it was a long time problem.

---

### Post by Incendia on 2009-11-04
> **kubug said:**
> Mostly nothing. It's just a simple test, and then you can go from there knowing it's ok. Most trouble shooting of a PC is by trial and error.

Now, since it's not an overheating issue with your PC, we need to figure out why your computer is shutting down during the install.

Does it stop at the same spot everytime?

No, it doesn't. :/

> **kubug said:**
> 

Here is the link: [http://support.packardbell.com/uk/item/index.php?i=7447720300&pi=platform_vesuvio_a]("http://support.packardbell.com/uk/item/index.php?i=7447720300&pi=platform_vesuvio_a")

Update your BIOS and try it again. 

Also, if that didn't work, here is a resource to find a possible fix:

[http://tuxmobil.org/pb.html]("http://tuxmobil.org/pb.html")

Let us know what happened.

I've tried that update before and it didn't change anything :/
& my laptop is not listed there.

---

### Post by kubug on 2009-11-04
The only reason why I suggest a BIOS update is that your BIOS version is 1.00. Most motherboards I have owned will go through 4 - 10 BIOS updates.

The page says it's for the EasyNote SL51 series laptops. Isn't that your laptop?

---

### Post by barnacleboy on 2009-11-04
Laptops and ACPI and Ubuntu haven't gone well for me either, I've just booted the live CD with boot options *noapic* and *nolapic*, don't enable ACPI later and all's well. I never used them anyway.

However, as far as I know, ACPI enables various power states such as sleep and hibernate. I wasn't aware of it regulating processor speed or temperature.

Perhaps it is a separate issue, not connected with ACPI?

Could someone either confirm or deny as to whether ACPI regulates overheating please, as I'm not certain.

Thanks.

---

### Post by kubug on 2009-11-05
> **barnacleboy said:**
> 

Could someone either confirm or deny as to whether ACPI regulates overheating please, as I'm not certain.

Thanks.

Here is a quick link: [http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface#Performance_states]("http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface#Performance_states")

By throttling the processor it keeps it cooler.

Anyways, I am not sure what chip is responsible for the ACPI on any given computer, and if there are ones to avoid. I wonder too if there is not a BIOS option to set that will allow you to still use ACPI. 

Most modern computers will allow you to change the "Speedstep", "Cool'n Quiet", etc settings. Turning these off may help. 

Also, changing the ACPI setting from "S3" to "S1" may improve things too.

---

### Post by Incendia on 2009-11-05
> **kubug said:**
> The only reason why I suggest a BIOS update is that your BIOS version is 1.00. Most motherboards I have owned will go through 4 - 10 BIOS updates.

The page says it's for the EasyNote SL51 series laptops. Isn't that your laptop?

I'll try it again when I'm on a broadband connection again :]

Hopefully it fixes my issue.

But I remember trying it not long ago late at night to get it to work; and remembering a very high pitched noise. but I was super super tired and can't remember what was happening.

I know I shouldn't do something as vital as a BIOS update when you don't even know your name :'')  LOL.

---

### Post by nevelshute on 2009-11-13
I have an issue with my computer switching off with no notice after I upgraded from 8.04, via 8.10 and 9.04, to 9.10. 

I have been using it over the past week and it has switched off 2-3 times. Today I was doing a big build and it gave up part way through. I endeavored to bring it up again to carry on but after 3-4 minutes it gave up again.

I have my old faithful 7.10 installed so tried to boot into that, but during the boot process it gave up. So it is a problem with the temperature of the processor.

I booted up with the SystemRescueCD and checked the temperature. cat /proc/acpi/thermal_zone/TZ01/temperature reported 85 degrees, which after a while felloff to 70.

I then retried ubuntu 9.10. The cat /proc/acpi/thermal_zone/TZ01/temperature there reported 40 degrees. I then kept checking it and it never augmented. After 5 minutes it switched off!!

I then booted up Ubuntu 7.10 and it reported 55 degrees.

Am still experimenting!

TA

Nev

---

### Post by kubug on 2009-11-13
> **nevelshute said:**
> I have an issue with my computer switching off with no notice after I upgraded from 8.04, via 8.10 and 9.04, to 9.10. 

I have been using it over the past week and it has switched off 2-3 times. Today I was doing a big build and it gave up part way through. I endeavored to bring it up again to carry on but after 3-4 minutes it gave up again.

I have my old faithful 7.10 installed so tried to boot into that, but during the boot process it gave up. So it is a problem with the temperature of the processor.

I booted up with the SystemRescueCD and checked the temperature. cat /proc/acpi/thermal_zone/TZ01/temperature reported 85 degrees, which after a while felloff to 70.

I then retried ubuntu 9.10. The cat /proc/acpi/thermal_zone/TZ01/temperature there reported 40 degrees. I then kept checking it and it never augmented. After 5 minutes it switched off!!

I then booted up Ubuntu 7.10 and it reported 55 degrees.

Am still experimenting!

TA

Nev

How old is your computer? Is it a laptop?

If it is a couple years old and you never done any "housecleaning" you may have to do that. With "housecleaning" I mean cleaning out all the fans and cooler from dust and hair (got any pets?) 

A lot of the overheating issues I have seen are simply hardware related, i.e. the air doesn't pass over the cooling elements. 

Check on that first and see if that fixes it.

---

### Post by kubug on 2009-11-13
Oh, and it's not good forum etiquette to take over someone else's thread. You should really start your own. ;)

---

### Post by nevelshute on 2009-11-13
This is an issue with my upgrade to Ubuntu 9.10. I only have the problem when I run Ubuntu 9.10. I am running VMware with WindowZ XP presently and doing a toolchain build using Ubuntu 7.10. I have noted the temperature and the fan speed and it can get upto 75 degrees, but the fan turns onto turbo and decreases the temperature and the computer does not switch off abruptly.

3 year old ACER Aspire 7720Z

I apologise if I have broken the etiquette rules, I have not asked for help, I just wanted to add relevant information to the thread as I thought that was what "thread" meant.

Nev

---

### Post by kubug on 2009-11-13
> **nevelshute said:**
> This is an issue with my upgrade to Ubuntu 9.10. I only have the problem when I run Ubuntu 9.10. I am running VMware with WindowZ XP presently and doing a toolchain build using Ubuntu 7.10. I have noted the temperature and the fan speed and it can get upto 75 degrees, but the fan turns onto turbo and decreases the temperature and the computer does not switch off abruptly.


Oh ok. As you can see, I was back on my hardware-bandwagon. I was on it because of your mention of 7.10 failing as well. 

Have you tried any of the kernel switches (noacpi etc.) and checked if it made a difference?

Doing some reading, a lot of people are complaining that their Laptops temperature went up in Karmic (from Jaunty). 

This thread talks about it. The only issue is that the fix that the thread presents doesn't work in Karmic anymore. 

[http://ubuntuforums.org/showthread.php?t=1036051]("http://ubuntuforums.org/showthread.php?t=1036051")

It mentions that a custom kernel for Karmic that has custom-DSDT enabled is necessary. If you are feeling adventurous here is a link for compiling your own kernel:

[http://blog.avirtualhome.com/2009/11/03/how-to-compile-a-kernel-for-ubuntu-karmic/]("http://blog.avirtualhome.com/2009/11/03/how-to-compile-a-kernel-for-ubuntu-karmic/")





> **nevelshute said:**
> 
I apologise if I have broken the etiquette rules, I have not asked for help, I just wanted to add relevant information to the thread as I thought that was what "thread" meant.


I am sorry if I came across "pushy", I misunderstood the intend of your post.

---

### Post by nevelshute on 2010-01-04
This was very helpfull, thanks.

I followed the instructions and had so many warnings on my dissassemble BIOS, that I reverted to updating my BIOS! All is now well.

 I have not dissassembled my new BIOS, just assume ACER is not using the broken Microsoft assembler anymore? 

THanks again.

>This thread talks about it. The only issue is that the fix that the thread presents doesn't >work in Karmic anymore. 

[>http://ubuntuforums.org/showthread.php?t=1036051]("http://ubuntuforums.org/showthread.php?t=1036051")

>It mentions that a custom kernel for Karmic that has custom-DSDT enabled is necessary. >If you are feeling adventurous here is a link for compiling your own kernel:

[>http://blog.avirtualhome.com/2009/11...ubuntu-karmic/]("http://blog.avirtualhome.com/2009/11/03/how-to-compile-a-kernel-for-ubuntu-karmic/")

---

