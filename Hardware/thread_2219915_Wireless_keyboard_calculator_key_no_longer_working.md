---
title: "Wireless keyboard calculator key no longer working"
date: 2014-04-25
forum: Hardware
---

### Post by temporos on 2014-04-25
Hello, all. :)

I completed a clean install of Lubuntu 14.04 last weekend, and it's running much better on my system than my old 13.10 upgrade did. As with any new system installation, there are a few kinks to work out, and this time, one of the kinks is a keyboard key binding.

In all previous versions of Lubuntu, the calculator key on my Microsoft Wireless 8000 keyboard brought up the LXDE calculator, Galculator. Now, however, pressing the calculator button causes the session to log out. I checked the keyboard shortcuts xml, and I found this...
[I]
~/.config/lubuntu-rc.xml[/I]
```
<!-- Keybinding for calculator button-->   <keybind key="XF86Calculator">
   <action name="Execute">
      <command>lxsession-default calculator</command>
   </action>
</keybind>
```

First, I looked to make sure that the default calculator application for Openbox was Galculator. It was. Then, I tried running **lxsession-default calculator** in a terminal window, and it logged me out again. After logging back in, I opened a terminal window and ran **galculator**, which opened just fine. How can I fix this?

I wonder if there's a major bug hiding in the *lxsession-default* application, because the **lock** parameter doesn't work, either, even though the command in Openbox is set to **lxlock**. The screen is locked just fine by **lxlock**, but running **lxsession-default lock** does nothing.

---

### Post by temporos on 2014-04-25
**Workaround**

I didn't find a solution, but I did just now figure out a workaround to the problem. I don't know how long it will last, or if any updates will reset it.

I replaced this line...
```
<command>lxsession-default calculator</command>
```
with this...
```
<command>galculator</command>
```
and then saved and closed *lubuntu-rc.xml*. Seems to work after a logout/login.

---

### Post by temporos on 2014-05-04
Just FYI for anyone who's interested, all of these terminal commands cause an immediate logout. It seems pretty bad that a bug this overt would make it through the QA process for a LTS of Lubuntu. :-s

```
lxsession-default calculator
lxsession-default tasks
lxsession-default screensaver
lxsession-default lock
```
The only known workaround right now is to edit the *lubuntu-rc.xml* file entries pertaining to these commands.

---

### Post by DogMatix on 2014-05-06
I don't think this is a hardware issue. I'm having the exact same issue in Lubuntu 14.04. I stumbled across the problem when I enabled the Openbox right-click menu. Clicking on any entry that has a command that includes lxsession-default causes a system logout

i.e. an entry in menu.xml such as:
```
<item label="Calculator">
<action name="Execute"><command>lxsession-default calculator</command>
<startupnotify><enabled>yes</enabled></startupnotify>
</action>
</item>
```

Entering (for example) 'lxsession-default calculator' into a Terminal also causes a system logout. I am also getting this behaviour in a Lubuntu Utopic Development install. It must be a bug.

---

### Post by bapoumba on 2014-05-06
> **DogMatix said:**
> 
Entering (for example) 'lxsession-default calculator' into a Terminal also causes a system logout. I am also getting this behaviour in a Lubuntu Utopic Development install. It must be a bug.
Wow, just tried on lubuntu 14.04, fresh install from last week or so, and yes, logged me out ..
Will look around, have you ?

---

### Post by DogMatix on 2014-05-06
Just had a browse on Launchpad and couldn't see a bug report of anything similar. 

Internet Search Engines eventually led me to this post.

---

### Post by bapoumba on 2014-05-06
> **DogMatix said:**
> Just had a browse on Launchpad and couldn't see a bug report of anything similar. 

Internet Search Engines eventually led me to this post.
Same here, the only thing that a search engine brings up is this thread, when lxsession-default is associated to session log out..

To note, I saw a message about starting the calculator before the session logged out. Late here, will file a bug tomorrow linking to this thread if no one has done it.

---

### Post by DogMatix on 2014-05-06
I have started a bug on Launchpad. Please add more useful information:

[https://bugs.launchpad.net/ubuntu/+source/lxsession/+bug/1316832](https://bugs.launchpad.net/ubuntu/+source/lxsession/+bug/1316832)

---

### Post by bapoumba on 2014-05-07
> **DogMatix said:**
> I have started a bug on Launchpad. Please add more useful information:

[https://bugs.launchpad.net/ubuntu/+source/lxsession/+bug/1316832](https://bugs.launchpad.net/ubuntu/+source/lxsession/+bug/1316832)

Thanks, marked it as affecting me too, so that bumped it into confirmed.

---

### Post by DogMatix on 2014-05-07
Added lxsession-default-apps run.log as it littered with error messages.

---

### Post by bapoumba on 2014-05-07
So in the kern.log, I found this after reproducing the steps :
```
May  7 11:07:20 SonyBlue kernel: [ 4976.041315] lxsession[1331]: segfault at 0 ip 08050c88 sp bfd3fde0 error 4 in lxsession[8048000+35000]
```
Which got me to this : [https://bugzilla.novell.com/show_bug.cgi?id=629478#c2](https://bugzilla.novell.com/show_bug.cgi?id=629478#c2)
It's directed at lxsession-edit, but could it be the same explanation, ie not being able to connect to the X server ?

I have non relevant lines in lxsession-default-apps run.log such as this one :
```
(lxsession-default-apps:14069): Gtk-WARNING **: Attempting to add a widget with type GtkVBox to a container of type GtkAlignment, but the widget is already inside a container of type GtkAlignment, the GTK+ FAQ at http://library.gnome.org/devel/gtk-faq/stable/ explains how to reparent a widget.
```

/var/log/apport.log
```
ERROR: apport (pid 7475) Wed May  7 11:07:21 2014: called for pid 1331, signal 11, core limit 0
ERROR: apport (pid 7475) Wed May  7 11:07:21 2014: executable: /usr/bin/lxsession (command line "/usr/bin/lxsession -s Lubuntu -e LXDE")
ERROR: apport (pid 7475) Wed May  7 11:07:22 2014: gdbus call error: Error: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

ERROR: apport (pid 7475) Wed May  7 11:07:22 2014: debug: session gdbus call: 
ERROR: apport (pid 7475) Wed May  7 11:07:22 2014: this executable already crashed 2 times, ignoring
```
There is no crash log for today, even in /var/crash. I attached the crash report from yesterday.

---

### Post by DogMatix on 2014-05-07
I am seeing similar in apport.log
```
ERROR: apport (pid 14087) Wed May  7 09:19:52 2014: debug: session gdbus call: 
ERROR: apport (pid 14087) Wed May  7 09:19:52 2014: this executable already crashed 2 times, ignoring
ERROR: apport (pid 14706) Wed May  7 09:33:07 2014: called for pid 14317, signal 11, core limit 0
ERROR: apport (pid 14706) Wed May  7 09:33:07 2014: executable: /usr/bin/lxsession (command line "/usr/bin/lxsession -s Lubuntu -e LXDE")
ERROR: apport (pid 14706) Wed May  7 09:33:07 2014: gdbus call error: Error: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

```
 
Recreating the bug gave a .crash log with

```
Title: lxsession crashed with SIGSEGV in _vala_array_free()
```

---

### Post by temporos on 2014-11-02
Just past Halloween: zombie thread! XD

The latest update to Lubuntu 14.04 replaced the *lubuntu-rc.xml* file, and put it in a different location. The workarounds in my earlier posts in this thread still work (note, however, that they don't *solve* the problem), but the file has been moved to *~/.config/openbox/lubuntu-rc.xml*.

---

