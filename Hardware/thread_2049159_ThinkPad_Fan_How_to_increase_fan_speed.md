---
title: "ThinkPad Fan: How to increase fan speed?"
date: 2012-08-28
forum: Hardware
---

### Post by Sicadastra on 2012-08-28
When I see posts on ThinkPad Fan the most common reason why people install it is because of fan noise, however my problem is more on fan speed, or the lack of it.

I'm not exactly technology savvy so I'd like to ask help on how to increase the fan speed because despite what I believe I installed properly there are times when my CPU temperature would reach 94 Celsius and I had to manually shut my laptop immediately to avoid damage.

I was able to successfully install ThinkPad Fan Control. Can I increase the fan speed via the GUI? If yes, how? I can't understand the hw-ctrld so I'm hesitant to tinker with the settings for fear of damage.

[[IMG]http://s11.postimage.org/hp3x15sqn/Screenshot_at_2012_08_28_13_48_15.jpg[/IMG]]("http://postimage.org/image/hp3x15sqn/")


Also, I checked the tpfand.conf and again, I'm not sure if I should edit it.

[[IMG]http://s11.postimage.org/6n3fggo1r/Screenshot_at_2012_08_28_13_42_01.jpg[/IMG]]("http://postimage.org/image/6n3fggo1r/")


I also used this command ```
sudo gedit /etc/default/thinkfan
``` to edit 'START=yes'.

[[IMG]http://s16.postimage.org/bah7iu8up/Screenshot_at_2012_08_28_13_51_43.jpg[/IMG]]("http://postimage.org/image/bah7iu8up/")


Another command I edited is this ```
sudo gedit /etc/thinkfan.conf
``` to add the sensor list, and the temperature table below.

[[IMG]http://s14.postimage.org/cim5qptil/Screenshot_at_2012_08_28_13_53_10.jpg[/IMG]]("http://postimage.org/image/cim5qptil/")


But despite all that I did my temperature-fan speed settings is not followed based on PSensors. It shows that my temperature is 73C and according to the fan speed table (on the sticky note), my fan speed should be at level 7 already which is at 3468 RPM but my current fan speed is only at 2784.

I know that I should also have my laptop cleaned and reapplied with thermal paste, but for the moment I can't do that so I'm hoping I can increase the fan speed until I can go to the service center to get this cleaned.

I'm using ThinkPadR61i Ubuntu 12.04 64-bit 160GB HDD, 4GB RAM. 

I hope someone can help me on this. :(

[[IMG]http://s16.postimage.org/3l71l9l5d/Screenshot_at_2012_08_28_14_11_26.jpg[/IMG]]("http://postimage.org/image/3l71l9l5d/")

ETA: It seems like i don't have thinkpad_acpi installed. Is it also important for ThinkFan to work? Is there a post where I can follow a step-by-step instruction on how to install it? Reading the file's READ ME isn't very helpful to me.

---

### Post by maxpro4u on 2012-08-28
Try blowing out the laptop with compressed air. My thinkpad was running hot and after blowing out the dust it is running about 20C cooler!

---

