---
title: "CPU governor resets to &quot;Performance&quot; on reboot"
date: 2009-01-23
forum: Hardware
---

### Post by mzakharo on 2009-01-23
my CPU governor always resets to "performance" after a cold boot. If I use gnome applet to change it to "ondemand", the change is not permanent. Could you please help me change it permanently?

---

### Post by martinbaselier on 2009-01-23
One solution would be to edit /etc/rc.local
and add the following line before the exit 0 statement
```

echo -n ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

```

Afterwards, make sure rc.local is executed:
so enter in terminal. 
```

sudo chmod +x /etc/rc.local

```

---

### Post by mzakharo on 2009-01-23
Sorry, did not help :(

---

### Post by martinbaselier on 2009-01-23
Can you give the output of  "cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor"

Do you have a cpu0 directory under /sys/devices/system/cpu/ ?

---

### Post by mzakharo on 2009-01-23
1.
```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
```
gives an output of ```
performance
```
If I manually change the setting with the gnome applet, the output changes accordingly to "ondemand" - no problems. I cannot make this change last after restart however :(
2.
I have a cpu0 directory.

---

### Post by martinbaselier on 2009-01-23
You could uninstall the gnome-plugin; It's not a really nice solution though, but it's a workaround. I'm running xfce, so I don't think I can help you further. I just happened to have a similar problem; mine was that my xfce-plugin wouldn't start and I solved it this way. Good luck solving it.

---

### Post by mzakharo on 2009-01-23
I still need the plugin, so uninstalling it is not an option. Thanks anyways. I have exhausted google search and ubuntu forums on this one. This forum topic is my last resort before reinstalling the operating system :(

---

### Post by martinbaselier on 2009-01-23
You only need the plugin to change the governor with a GUI. You could also remove it from the panel and start it only when you want to change the governor.

---

### Post by mzakharo on 2009-01-23
the applet does not matter here. The governor goes to "performance" by default at the start of the operating system. I only use the applet to change it from its default value.

---

### Post by martinbaselier on 2009-01-23
That's strange. Could you output 'cat /etc/rc.local' and 'ls /etc/rc.local -l', just for me to be sure that's correct. It should be the last script run when starting, so it ought to do the trick.

---

### Post by mzakharo on 2009-01-23
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
echo -n ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
exit 0

```
and
```
-rwxr-xr-x 1 root root 538 2009-01-23 17:27 /etc/rc.local

```

---

### Post by martinbaselier on 2009-01-23
It's the same I have and here it works. I just can't take it, when I dive into a problem and I can't get it solved. On my own laptop I usually just leave it be and try again later, but anyway, I would advice you to google for 'login script' in combination with linux or ubuntu. I've done a bit of googling myself and I found that under /etc/gdm there are also login scripts.
You can find out if there's anything there changing the governor by: 
```

find /etc/gdm/* -exec cat {} \; | grep governor

```
It will give you a few errors that you can't use cat on a directory, but you can ignore that. 

I also saw that one of the script in /etc/init.d/ does something to the governor. It has no effect on my system though. I don't know which of the scripts it is, so I haven't checked into that further. 

Also locate rc.local will give you the location of the other rc.local scripts; maybe there's something in there?

---

### Post by mzakharo on 2009-01-23
well, I issued find command on /etc/gdm and it found nothing. However, after running
```
find /etc/init.d/* -exec cat {} \; | grep governor
```
it found the following: 

```
load_governor_modules() {
		load_governor_modules
        if [ ! -f /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor ]; then
	    if [ ! -d $x ] || [ ! -f $x"cpufreq/scaling_governor" ]; then
	    echo -n ondemand > $x"cpufreq/scaling_governor"
	if [ -f "$CPUFREQ/scaling_governor" ] && \
		[ -f "$CPUFREQ/scaling_available_governors" ] && \
		grep -q userspace "$CPUFREQ/scaling_available_governors"
	    if [ -f $x"cpufreq/scaling_governor" ]; then
		echo -n performance > $x"cpufreq/scaling_governor";

```

One if statement sets the performance governor, but how can I find which file the search result relates to?

---

### Post by martinbaselier on 2009-01-23
I've just sent out all the output to a text file in my home directory and used mousepad (texteditor) to open it and found out the name of the script:
(There will most probably be a better way to do it, but I don't know it yet.)

It's /etc/init.d/powernowd

It's used for starting the powernow daemon. I doubt that's causing it though. You can check if it's been started by type ps -e | grep power
(ps -e shows all the running processes.) 

I've found a pretty nice overview about boot and login scripts. 

[http://www.extremetech.com/article2/0,2845,2114121,00.asp](http://www.extremetech.com/article2/0,2845,2114121,00.asp)

And now I'm going to sleep (it's 2 o clock here). I'll check again tomorrow.

---

### Post by mzakharo on 2009-01-23
Thank you so much for all your efforts, martinbaselier. I really appreciate what you have done here. All of the links were useful and added to my knowledge of UNIX. I have realized that the "performance" governor is set on powernowd shutdown. I tired fooling arround with sysv-rc-conf, which was unsuccessful. So I just loaded synaptic package manager, issued a complete and clean removal of powernowd, and then its fresh installation. Everything works like a charm again :D I do not understand why it was not working, but who knows, linux works in mysterious ways ;)

---

### Post by martinbaselier on 2009-01-24
You're welcome. I'm glad it's solved. That's why I like linux, if there's a problem you can troubleshoot and pinpoint it, not like m$ where you get uncomprehensible errors and well I'll save you those frustrations.

BTW, I believe now you should change this thread tp [SOLVED]

---

### Post by whitediver on 2009-01-24
Thanks! That worked for me as well! I've been trying sort this out for the last day. It seems that we were both working on this together and you beat me for 15 minutes. well done!!!

---

### Post by mzakharo on 2009-01-24
Sorry for dumb question, but I could not find in ubuntu forums FAQ a tutorial on how to go about adding a [solved] to the title of a thread. Could someone please help me?

---

### Post by martinbaselier on 2009-01-25
Just edit your thread, then edit your message. Then you can change the thread title.

---

### Post by mzakharo on 2009-01-25
I am having troubles locating the link that allows me to edit the thread

---

### Post by martinbaselier on 2009-01-25
I just click on my name, then statistics, threads started by ..., the appropriate thread and then there's an edit button.

---

