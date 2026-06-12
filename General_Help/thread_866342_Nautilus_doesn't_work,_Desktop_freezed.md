---
title: "Nautilus doesn't work, Desktop freezed"
date: 2008-07-21
forum: General Help
---

### Post by SilkMonster0 on 2008-07-21
Hello community...

I was trying to program in GTK, then in Glib, without succes, so i started looking info and i found that i needed some libraries. So i went to Synaptic and installed them... Since then the desktop is freezed, there are no icons on it, and i can't click nor right-click on it.

I thought it wasn't a big deal, (i only have the Home icon on the desktop) but when i tried to run nautilus it didn't work, so i rebooted, but it was the same, and when i tried to run nautilus in Terminal this happened:

```
silk@Athlon:~$ nautilus
Initializing nautilus-share extension
seahorse nautilus module initialized
nautilus: symbol lookup error: nautilus: undefined symbol: g_file_query_filesystem_info_async
```

I freaked out, so i tried as root. and....

```
root@Athlon:/home/silk# nautilus
Initializing nautilus-share extension
seahorse nautilus module initialized
nautilus: symbol lookup error: nautilus: undefined symbol: g_file_query_filesystem_info_async
```

These are the Libs i installed, (Based on this [http://maestrodenada.com/manualanjuta/cp0/c0_2.html):](http://maestrodenada.com/manualanjuta/cp0/c0_2.html):) libgtkmm-2.4-1c2a, libgtkmm-2.4-dev, libgtkmm-2.4-doc libgnomeuimm-2.6-1c2a, libgnomeuimm-2.6-dev, libgnomeuimm-2.6-doc, libgnomeui-dev, libgnomeui-doc, libgtk2.0-dev y libgtk2.0-doc libglib2.0-dev y libglib2.0-doc

I really hope that someone can help me... PLEASE!! :frown:

Greetingz!

---

### Post by prince_niceguy on 2008-07-21
try deleting all the gnome settings using the following command

```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity
```

I have found nautilus to hang on me and was able to make it working by above command.

---

### Post by SilkMonster0 on 2008-07-21
Thanks for answering... i tried what you said but it didn't work... it's the same error... Thank you verry verry verry much anyway

---

### Post by prince_niceguy on 2008-07-22
do you have any network shares mounted? do you have a bookmark in nautilus referring to a disconnected drive? some time nautilus used to hang due to that too. though they have made it async it still hangs in my case when network connection is lost and network share is not there.

---

### Post by Gunman1982 on 2008-07-22
Take a look here: [http://ubuntuforums.org/showthread.php?t=770191]("http://ubuntuforums.org/showthread.php?t=770191")

---

### Post by blondebeard on 2008-07-22
hello there i know i can turn off nautilus to do other desktop efects before you go and start rm ing everything with out knowing what it does or how bad you can damage your system see if some how you mistakenly turned off your desk top do this...

alt F2 ---this will give you the run app. menu
gconf-editor [enter]---type that and another menu will pop up
now click on the app> tab then nautilus> tab then finaly preferences tab
you are in the right folder to do what we are trying to do now and that is to look to see if ''show_desktop'' is set to true click the box to set it to true. now if you want to see a different pic on every desktop turn it off and go into compiz and use that to animate the desktop. im not that good with english so if this how-to sucked leave a comment on what you need clarifide:confused:

---

### Post by SilkMonster0 on 2008-07-22
Thanks for answering everybody!!

> **prince_niceguy said:**
> do you have any network shares mounted? do you have a bookmark in nautilus referring to a disconnected drive? some time nautilus used to hang due to that too. though they have made it async it still hangs in my case when network connection is lost and network share is not there.
Yes i have a network share, but i tried unmounting and mounting again and it didn't work, and no, it's not refering to a disconnected drive... but thanks a lot.


> **Gunman1982 said:**
> Take a look here: [http://ubuntuforums.org/showthread.php?t=770191]("http://ubuntuforums.org/showthread.php?t=770191")
I already did before i made this post, but when i try to locate that file it doesn't exist, and i have no /usr/local/src/glib-2.15.4 nor similar. Thank you very very much.


> **blondebeard said:**
> hello there i know i can turn off nautilus to do other desktop efects before you go and start rm ing everything with out knowing what it does or how bad you can damage your system see if some how you mistakenly turned off your desk top do this...

alt F2 ---this will give you the run app. menu
gconf-editor [enter]---type that and another menu will pop up
now click on the app> tab then nautilus> tab then finaly preferences tab
you are in the right folder to do what we are trying to do now and that is to look to see if ''show_desktop'' is set to true click the box to set it to true. now if you want to see a different pic on every desktop turn it off and go into compiz and use that to animate the desktop. im not that good with english so if this how-to sucked leave a comment on what you need clarifide:confused:

Well i already tried to rm what prince_niceguy said, and i already tried the gconf-editor, but it didn't work... Thanks anyway.

I think that the libs i installed are the problem, since when i installed them my nautilus stopped working, and the desktop stopped working, and with the error it says something about g_file_query_filesystem_info_async i mean, there has to be the problem in there. I am really really freaked out... i actually downloaded fedora so if i can't solve this problem i'll uninstall ubuntu. Thanks for answering again!!!

Greetingz!

---

### Post by Mandler on 2010-02-26
I know that this problem was likely solved long ago, but just in case someone stumbles onto this posting as I did, I thought I'd share my experience.

I had the same problem as described by SilkMonster0. Right-clicking on the desktop had no effect. In fact, the desktop would not receive the focus (e.g., clicking it while a window was open, left the focus on the current window). I was also not able to use the workspace switcher in the panel. And lastly, items downloaded from websites did not appear on the desktop, albeit they did appear inside the Desktop folder. The strangest thing is that the problem came and went. 

In my case, I discovered that the ownership of /home/___/Desktop/ had been assigned to the root. I wasn't seeing its content because I didn't have permission. I don't know why I could still see the content while opening the Desktop folder in Nautilus. I changed the ownership and the problem was solved.

I suspect it had something to do with a backup program I was using, but I never tracked it down. I just switched programs.

---

