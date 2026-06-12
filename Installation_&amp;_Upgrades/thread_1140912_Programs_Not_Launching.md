---
title: "Programs Not Launching"
date: 2009-04-28
forum: Installation &amp; Upgrades
---

### Post by BHammond1 on 2009-04-28
Hey, I recently upgraded to Jaunty Jackalope from Intrepid. It runs fine, but on many necessary programs (Pidgin, CD burner software, Package Manager, Upgrade Manager, etc.) they do not run. They pop up as "starting" on the bottom toolbar but after about a minute they disappear and the program doesn't load.

This is something I would like to get fixed ASAP because at the moment I can't even load back to Intrepid because my burning software won't work.

---

### Post by Anthon on 2009-04-28
have you looked in the system logs ( ls -lrt /var/log, then tail <recently updated filenames>)? 
You can also try to start the app from the commandline (assuming that one starts) and see if there is some output. 
Could be that the Python version that is selected is not the 'normal' one. I have had similar problems after installing Python from source (without making sure that all the extension libraries that Ubuntu relies upon, were available for the new Python version).

---

### Post by BHammond1 on 2009-04-28
I hate to sound like a total newbie, but could you explain to me how to do that? Any help would be GREATLY appreciated.

By the way, I've attempted to launch Pidgin from Terminal using the "pidgin &" command. Dunno if this helps, but below is the response that I get:

(Pidgin:4355): GStreamer-CRITICAL **: gst_element_register: assertion `g_type_is_a (type, GST_TYPE_ELEMENT)' failed

---

### Post by Anthon on 2009-04-28
What you did for pidgin is ok, although I would not have started it in the background with '&', if it is going to kill itself anyway?
Was that the only message and the last one before the program exited?

Have you started any of the others in the same way (without the '&') and compared the last before exit messages? It seems unlikely to me that the package manager uses gstreamer, but you never know.

Also: did you logout/login or reboot after updating. Sometimes that helps when quirks occur after an update.

---

### Post by Ticketoride on 2009-04-28
> **BHammond1 said:**
> .. many necessary programs (Pidgin, CD burner software, Package Manager, Upgrade Manager, etc.) they do not run. They pop up as "starting" on the bottom toolbar but after about a minute they disappear and the program doesn't load.
Yeah, I'd say on average 10% of the Software does not launch ...

---

### Post by BHammond1 on 2009-04-28
> **Anthon said:**
> What you did for pidgin is ok, although I would not have started it in the background with '&', if it is going to kill itself anyway?
Was that the only message and the last one before the program exited?

Have you started any of the others in the same way (without the '&') and compared the last before exit messages? It seems unlikely to me that the package manager uses gstreamer, but you never know.

Also: did you logout/login or reboot after updating. Sometimes that helps when quirks occur after an update.

Yeah, I've restarted and logged in again multiple times. 

Here's the error message with Brasero:

> (brasero:5362): GLib-GObject-WARNING **: cannot register existing type `GstValve'

(brasero:5362): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(brasero:5362): GStreamer-CRITICAL **: gst_element_register: assertion `g_type_is_a (type, GST_TYPE_ELEMENT)' failed

And with Pidgin:

> (pidgin:5406): GStreamer-CRITICAL **: gst_element_register: assertion `g_type_is_a (type, GST_TYPE_ELEMENT)' failed

Both of these are the last and only messages I get via Terminal. With the command for Pidgin, Terminal also locks on that command and I have to exit out of it to get back to a command line.

The major programs I've found that have this problem are Pidgin, the Add/Remove Programs option, and both Brasero and GnomeBaker. Others, such as Gmail Notify, Firefox, or Open Office, seem to work fine.

---

### Post by Anthon on 2009-04-28
Maybe just a stupid question but have you looked at your disk space? There is at least one report on launchpad of someone having this message because of a full disk.

---

### Post by BHammond1 on 2009-04-28
> **Anthon said:**
> Maybe just a stupid question but have you looked at your disk space? There is at least one report on launchpad of someone having this message because of a full disk.

I actually hadn't before you mentioned it, but now I have and I have over 115 GB free.

I'd go back to Intrepid in an instant, but since I can't get any CD burning software to work I can't do a clean install. Argh.

---

