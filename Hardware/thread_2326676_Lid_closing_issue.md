---
title: "Lid closing issue"
date: 2016-06-03
forum: Hardware
---

### Post by The musmula on 2016-06-03
Hi everyone, here I am again with another problem that I hope you can help me out with.

When I close my laptop lid, nothing happens. I tried [this]("http://bit.ly/1O7Cb5L") already and I found some other posts about the matter which I can't find anymore for some reason but the point is: I'd like the computer to suspend to RAM once the lid is closed (like I defined in my power settings)

[ATTACH=CONFIG]269417[/ATTACH]

The laptop is an Acer ES1-531-C95L running Xubuntu 16.04 but the issue was there even when it was on Ubuntu. I'll try out Ubuntu Mate and Kubuntu on it in the next couple of days but I don't feel very optimistic about this particular issue :/

---

### Post by ajgreeny on 2016-06-03
Not sure if this will help in your situation but in my oldish netbook I have to have the machine set up to do the same action for both battery and plugged in to get this to work properly.

I had mine originally set to hibernate when on battery and suspend when plugged in and it would only suspend when on battery, even though hibernate was working fine after adding the appropriate  /etc/polkit-1/localauthority/50-local.d/com.ubuntu.enable-hibernate.pkla file.  I changed the setting to hibernate in both cases and now it works as I want it to.

I have not investigated this any further to see if it always does whatever is set in the plugged in selection, even if running on battery, but it now works as I want so I have left it alone.

---

### Post by The musmula on 2016-06-03
thanks for the reply, I tried that and sadly it didn't work. Can you tell me more about that .pkla file. I'm not familiar with it

---

### Post by ajgreeny on 2016-06-03
This is the thread about hibernation that still appears to work in 16.04 as well as 14.04.
[http://ubuntuforums.org/showthread.php?t=2219403](http://ubuntuforums.org/showthread.php?t=2219403)

---

### Post by martinr on 2016-06-04
Maybe you ran into the following problem, that was already present in Xubuntu 12.04. No Power management in lightdm (when no-one is logged in).
It is a [known bug]("https://bugs.launchpad.net/ubuntu/+source/lightdm-gtk-greeter/+bug/990887"). Here is a workaround from that bug report, that worked for me.

A workaround is to install a hook to the acpi event yourself: save the following file as /etc/acpi/local/lid.sh.post ( create the directory if it doesn&#8217;t exist) and set its executable bit (chmod u+x /etc/acpi/local/lid.sh.post):

```
#!/bin/bash

grep -q closed /proc/acpi/button/lid/*/state
if [ $? = 0 ]; then
   pm-suspend
fi

```

---

### Post by The musmula on 2016-06-05
Thanks for the link, ajgreeny, but that doesn't work for me either.
And the .post file solution sadly doesn't do it either :( I stumbled upon that in my initial googling and was disappointed. Oh well...

---

