---
title: "Unable to set Keycode - keytouch editor"
date: 2007-09-20
forum: Hardware &amp; Laptops
---

### Post by Uber Nooblett on 2007-09-20
I went through the whole detection process, but for some keys, where I dont automatically get a keycode, I am not able to select one and the prog therefore does is not able to create a valid keyboard file...

any ideas?

"The keyboard file has been saved successfully, but cannot yet be imported in keyTouch because it is not a valid keyboard file.

The keyboard file contains an empty keycode."

---

### Post by Sand Lee on 2007-10-28
You have to set a keycode manually (w/ the drop down menu) for one of your entries.

---

### Post by pete757 on 2008-01-06
I've had similar problems, here's a bit more information:

I recently installed keytouch (v2.3.0) and keytouch-editor (v3.1.1) on Ubuntu (kernel version 2.6.22-14-rt). I have been trying to configure keytouch for a Cyberlink remote control (this has a USB IR receiver). If I run keytouch-editor and choose the appropriate eventX device (in my case event4, which appears as a TopSeed Tech Corp. USB IR Combo Device). I can press any of the special multi-media keys and these are recognised by keytouch-editor. I have added all the keys to the configuration in the keytouch-editor. None of the keys appear to have a scancode (I think this is correct for a USB device).

I have a number of issues:

1. Pressing some of the keys results in the selection of a keycode, but for some it does not and I am unable to successfully select a valid keycode using the editor?
2. I can save the configuration file, but I get a warning message "The keyboard file contains an empty keycode".
3. If I open the configuration file I created in a text editor, and insert valid keycodes for each of the special keys, I am then able to open the file in keycode-editor and save without the warning.
4. I can then run keytouch, import the config file I created, and see all my key mappings. However I can't type in the "default setting" textbox (is this correct?).
5. No matter how I configure some of the keys in keytouch (i.e. program name or plugin action) pressing some of the keys have no effect.
6. I note that if I run the system/preferences/keyboard shortcuts utility, some of the special multimedia keys are detected (without keytouch running). How can I be sure keytouch is having any effect at all?

Thanks
Pete

---

### Post by Ashrael on 2008-01-07
I have the same problem, even if i have nor tried keytouch yet, i have tried different programs with the same result...Is there one of you who still has windows on a machine? If so, you could probably find the correct codes that it generates and we could figure out how to define them in a layout. I am going to search for my old windows driver cd....it should be on there somewhere...

i'll keep you posted..

---

### Post by Ashrael on 2008-01-07
Found the cd, installed the driver and programs under wine, they work (almost....) have not been able to find any codes yet......I' ll try it  later on a windows machine...will post..much later..

---

