---
title: "Changing the brightness of the screen"
date: 2006-10-20
forum: Hardware &amp; Laptops
---

### Post by Nevermore on 2006-10-20
I was a dapper user, under dapper everything worked out of the box for my laptop, once i switched to edgy i lost the hotkey service..
I can't make the hotkey work anymore, so, when i am on battery, the screen is tooo bright and eats my battery in very short time..
I am looking for something that allow me to change the brightness on the fly, and maybe retain the battery settings with an auto switch when i plug or unplug the AC..
any idea?
BTW why the hell i can't put screen saver time less than 11 minutes???

---

### Post by Kateikyoushi on 2006-10-20
You can set your screen's brightness in System >> Preferences >> Power Management can define different level for ac and battery mode. The FN keys work on my notebook did you update your system recently ?

---

### Post by Nevermore on 2006-10-20
i am making a fresh install of edgy..
and i encountered a first problem, when trying to install in two separate / and /home i get an error saying there is not / filesystem..
BTW seems that sound is not working as well
isn't that odd?

---

### Post by Nevermore on 2006-10-20
> **Kateikyoushi said:**
> You can set your screen's brightness in System >> Preferences >> Power Management can define different level for ac and battery mode. The FN keys work on my notebook did you update your system recently ?
truly talking
where did u find the brightness change for battery or ac power?
i am in system-preferences-power management
and the only thing i can change is the sleep of the screen, the suspend time, and the cpu speedfreq (to be on powersave than performance)..
but still, no hotkeys support and moreover no way to change the screen sleep to a more decent 2-3mins instead of the default 11!

---

### Post by Kateikyoushi on 2006-10-20
Right there under the sleep bar of the screen I can set brightness.
Do an update maybe you are using obsolate packages, till last week my hotkeys didn't work either.

[[IMG]http://img147.imageshack.us/img147/5861/powerve4.png[/IMG]](http://imageshack.us)

---

### Post by Nevermore on 2006-10-20
hey i've never seen the brighness bar here!!!
how is that?
and also the settings i can put is minimum 11minutes sleep time..
what can i do?

---

### Post by xyz on 2006-10-20
Just in case some of you guys have a Toshiba...I can also run the following command line:
```
echo "brightness:0" > /proc/acpi/toshiba/lcd
```
Adjust it to your own wish by changing 0 to whatever...

---

### Post by Nevermore on 2006-10-20
i have a panasonic
however seems that the module for panasonic (pcc) is not loaded
the sony one is loaded in error...
maybe is this the problem? how do i fix it?

---

### Post by Nevermore on 2006-10-20
i forced the removal of sony_acpi and installed pcc_acpi
unfortunately seems the module doesn't do much..
now pcc_acpi is loaded but i don't have a /proc/acpi/pcc
and like always i can't change brightness and hotkeys are down..

---

### Post by Nevermore on 2006-10-20
no ideas?

---

### Post by Nevermore on 2006-10-21
nothing to do.
i filed a bug..

---

### Post by jasonbuckingham on 2006-10-29
My power management does not have "screen brightness" choice...what to do? I am running Dapper/Gnome on a Dell Latitude D810.

---

### Post by deerstar on 2006-11-01
Have you seen the following page?
Panasonic R4: hotkeys and s3 don't work in edgy
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/62620](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/62620)

you can try
[http://librarian.launchpad.net/1916123/acpi-support_panasonic_tsk20060402.tar.gz](http://librarian.launchpad.net/1916123/acpi-support_panasonic_tsk20060402.tar.gz)

---

