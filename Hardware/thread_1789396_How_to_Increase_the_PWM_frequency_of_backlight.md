---
title: "How to Increase the PWM frequency of backlight"
date: 2011-06-23
forum: Hardware
---

### Post by thmalmeida on 2011-06-23
I recently bought a Dell N4030 and I can feel the screen isn't confortable. The PWM frequency of backlight has a lower frequency and if you stay a long time front to the laptop it may cause some headache.

The brightness can decrease and increase by changing the pulse width, but the frequency it's always the same. What I wanna change, increasing.

I think it's possible if change something in kernel. I found an archive that may be related with this.

**/usr/src/linux-headers-2.6.38-8-generic/include/linux/pwm_backlight.h**

/*
 * Generic PWM backlight driver data - see drivers/video/backlight/pwm_bl.c
 */
#ifndef __LINUX_PWM_BACKLIGHT_H
#define __LINUX_PWM_BACKLIGHT_H

struct platform_pwm_backlight_data {
    int pwm_id;
    unsigned int max_brightness;
    unsigned int dft_brightness;
    unsigned int lth_brightness;
    **unsigned int pwm_period_ns;**
    int (*init)(struct device *dev);
    int (*notify)(struct device *dev, int brightness);
    void (*exit)(struct device *dev);
};

#endif

maybe I can change the variable **unsigned int pwm_period_ns;** decreasing the period, and then taking one upper frequency.

Does anybody can help me with it?

Thanks for all.

---

### Post by tgalati4 on 2011-06-23
Have you checked for any switches in the BIOS or acpitool?

sudo apt-get install acpitool
man acpitool
acpitool -e

Also check for some variables that you can set in:

/proc/acpi/video/VID/LCD0

The location of the brightness/pwm variable may be different from what I posted since I'm on a thinkpad, but the video display stuff is generally located in /proc/acpi/video

If you find it, you would use an echo statement to poke the correct value into the controlling file.

Here's a script called blink.sh that I use to blink my thinklight.  I use this for skype chat notification.


#!/bin/bash
# script for blinking my thinklight
# needs to be run by root
# depends on /usr/bin/seq
 
# if [ $# -ne 2 ] ; then
# echo &#8220;usage: $0 <NbrOfBlinks> <Frequency>&#8221;
# exit 1
# fi
 
NBR_OF_BLINKS=$1
FREQUENCY=$2
THINKLIGHT=/proc/acpi/ibm/light
 
for i in `seq $NBR_OF_BLINKS`
do
echo on > $THINKLIGHT
sleep $FREQUENCY
echo off > $THINKLIGHT
sleep $FREQUENCY
done

---

### Post by thmalmeida on 2011-06-23
I installed acpitool and when I run acpitool -e it only shows the battery and cpu information.

And isn't appear the directory "video" into  /proc/acpi/video/

After a little googling I found some people have used something like set drm intel and put some hexadecimal address and set the PWM. I didn't understand how to set it.

Have any other idea?

---

### Post by thmalmeida on 2011-06-23
In this link on the second comment by Patrick Shaaf

[http://us.generation-nt.com/answer/back-light-conflict-i915-vs-dell-laptop-help-201194071.html](http://us.generation-nt.com/answer/back-light-conflict-i915-vs-dell-laptop-help-201194071.html)

---

### Post by tgalati4 on 2011-06-24
That post turned on debugging mode for the Intel Direct Rendering Module (DRM) and it showed the brightness changing when switching back and forth between the graphical desktop and a text console.  So this is/was a bug in the brightness driver for the intel i915 chip.  

For your situation, look at the source code or the module switches for:

see drivers/video/backlight/pwm_bl.c

The pulse width may be hard-coded or provided by the BIOS and not changeable.  Sorry, but you will have to keep searching.  Is there a Windows utility to change the pulse width?

---

### Post by badDron on 2011-08-03
Any updates here? I'm also very interested, my new Thinkpad T520 breaks my vision.
> **tgalati4 said:**
> Sorry, but you will have to keep searching.  Is there a Windows utility to change the pulse width?
Yep. There is small utility for Windows that can set any PWM freq using Intel HD driver functions. So I hope that Indel driver for Linux also have such stuff.

---

### Post by piipo on 2012-11-18
> **badDron said:**
> There is small utility for Windows that can set any PWM freq using Intel HD driver functions. So I hope that Indel driver for Linux also have such stuff.

Hi, what is the name of this Windows utility?

Thank you!

---

### Post by wildmanne39 on 2012-11-19
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

