---
title: "Trusty 64Bit not detecting webcam"
date: 2014-04-24
forum: Hardware
---

### Post by r_avital on 2014-04-24
Bug reported already in launchpad.

Same computer ran Saucy a week ago, built-in webcam worked fine in cheese and skype.  Now under Trusty, both reporting "no device found."

Running cheese in terminal, here's the output:
```
** Message: cheese-application.vala:291: Error during camera setup: No device found


(cheese:3261): cheese-CRITICAL **: cheese_camera_device_get_device_node: assertion 'CHEESE_IS_CAMERA_DEVICE (device)' failed

(cheese:3261): GLib-CRITICAL **: g_variant_new_string: assertion 'string != NULL' failed

(cheese:3261): GLib-GIO-CRITICAL **: g_settings_schema_key_type_check: assertion 'value != NULL' failed

(cheese:3261): GLib-CRITICAL **: g_variant_get_type_string: assertion 'value != NULL' failed

(cheese:3261): GLib-GIO-CRITICAL **: g_settings_set_value: key 'camera' in 'org.gnome.Cheese' expects type 's', but a GVariant of type '(null)' was given

** (cheese:3261): CRITICAL **: cheese_preferences_dialog_setup_resolutions_for_device: assertion 'device != NULL' failed


```

And lsusb doesn't find the webcam.  It did a week ago, in Saucy.  External webcam works fine.  Problem is not with cheese or skype, it's in the innards of Trusty.

[Oh, but it was absolutely critical to put in coding time and effort to disallow buttons on the right side... Heaven only knows what catastrophes have been prevented!]

---

### Post by mastablasta on 2014-04-24
what camera chip is it? does the lsusb identify them? 

mine is not working anymore (worked in 12.10, 13.04, 13.10) but only in skype. who uses Skype these days anyway, right? :-)

> [Oh, but it was absolutely critical to put in coding time and effort to disallow buttons on the right side... Heaven only knows what catastrophes have been prevented!]

LOL. +1 to that.

---

### Post by r_avital on 2014-04-24
Hey there,

I'm using this old and tired msi gx710 laptop as a test machine.  lsusb does not find the webcam.  In Saucy, on the same laptop, some 3 days ago, before I upgraded to Trusty, lsusb found the same webcam just fine, I can't remember the name of the chip.  Point is, Trusty is failing to recognize the webcam, and all other things are equal.

I only use skype when bosses and employers want me to work with them on skype, because they don't know any better.  So I'm sure I'm not the only one for whom this is a productivity issue.

---

### Post by monkeybrain20122 on 2014-04-24
Can you install a different kernel? [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

---

### Post by mastablasta on 2014-04-25
also might be good to get that chip info (use a live version of the older edition) and then see if there was similar issue in one of the distros that were using this kernel before Ubutnu (e.g. Arch linux, Debian Sid).  perhaps a solution was already found by someone out there. but to search for it chip would help. or you could try with model. but you know these models.. they sell under same basic model totaly different devices.

---

