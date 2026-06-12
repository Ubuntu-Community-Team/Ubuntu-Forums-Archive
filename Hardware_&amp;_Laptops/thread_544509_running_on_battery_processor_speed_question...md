---
title: "running on battery processor speed question.."
date: 2007-09-06
forum: Hardware &amp; Laptops
---

### Post by spotdog14 on 2007-09-06
Ok, i have a strange problem. Well i guess its not that strange, but what ever. My laptop has a Pentium-M in it, and it speed steps/scales fine, usually running at 600mhz then scaling up to 1.5Ghz when needed. 

And this is fine for when running on AC because it keeps the laptop nice and cool. Anyways what i would like it to do is not scale up when running on batteries? Is there any way to do this that will not effect the way it scales during AC power?

---

### Post by codesplice on 2007-09-06
So you want it to run only at 600mhz when on battery?  My Inspiron does this by default.... it steps the speed down for when using battery power.

Check in your BIOS settings for SpeedStep options - if all else fails, you can disable SpeedStep which will force the processor to run at the lower clock speed.

Good luck.

---

### Post by luisjorge on 2007-10-26
Hello!

If your laptop doesn't do that automatically (my inspiron doesn't), you can check if your laptop runs fine with "laptop mode" enabled.

First, enable "laptop-mode". Type into a terminal:

```
sudo gedit /etc/default/acpi-support
```

A file will open, and at the end of the page (line 69 more or less), you will find the option "ENABLE_LAPTOP_MODE=". If it says "false", replace that with "true".
Save and close the file.

Then, in the terminal, type: 
```
sudo gedit /etc/laptop-mode/laptop-mode.conf
```

Another file will open, and here you can adjust the settings you want for laptop mode, starting with enabling or not laptop-mode when on battery power and when running on AC power. There are many options, including CPU scaling and maximum throttling, so you can set it to your liking.
When finished, just save the file and close it. I would recommend a reboot and test if this works.

Since laptop-mode doesn't work with all computers, and some of them hang when enabling this mode, check if there are any problems with your laptop. If everything works fine, then you can use this feature.

Hope this helps solving your problem!:)

Luis Jorge.

---

