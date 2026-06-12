---
title: "nvidia driver problem about libGL.so.1"
date: 2009-08-06
forum: Hardware
---

### Post by benzfish on 2009-08-06
hello, everyone.
I used ubuntu 9.04 os, and my question is 
I have a nvs140m graphic gard. And I download the nv-driver the vision of driver is 185.18.29. I just run "sh NVIDIA-...-.run", and during the process, there is a error message
[COLOR="Red"]"ERROR: The runtime configuration check failed for library libGL.so.185.18.29 (expected:'usr/lib/libGL.so.1',found:(not found)). The most likely reason for this is that the library was installed to the wrong location or that your system's dynamic loader configuration needs to be updated. Please check the OpenGL library installation prefix and /or the dynami loader configuration"[/COLOR]
Then I look up the directory /usr/lib the libGL.so.1 is right there. So, if you known the solution please help me. Thank you.

---

### Post by sandy8925 on 2009-08-06
You have to run the script with root permissions. For that you should do:

sudo sh NVIDIA-......-.run

And you should also stop any window managers that you have running. To do this press Ctrl + Alt + F1 .  A text-only terminal will open up. Login with username and password. To stop gnome display manager use the command:

sudo /etc/init.d/gdm stop

Then install the driver.

After that do:

sudo /etc/init.d/gdm start

and gnome will start up again. Don't know how it works for kde and other wm's.

---

### Post by benzfish on 2009-08-06
thanks sandy8925, but I known about this. I do what you said, and the ERROR message displayed. o~~,there is another thing, I used driver vision 180.51 before, and it works well. I just update the old vision to this new vision, and the ERROR message diaplayed. after that, the old vision can not worked anymore, even I reinstalled it.

---

### Post by Yellow Pasque on 2009-08-06
Maybe:
```
sudo ldconfig -v | grep libGL
```

---

### Post by benzfish on 2009-08-06
Thanks for Temüjin. But it's still not work.

---

### Post by gradinaruvasile on 2009-08-06
Did u uninstall the previous driver? With the --uninstall command line option.

---

### Post by benzfish on 2009-08-06
gradinaruvasile: I have not uninstall the previous vision driver, just install the new driver. But, when I see the ERROR message, I uninstall the driver of both new vision and old vision with the --uninstall command. But, after that, it still can not work. thank you.

---

