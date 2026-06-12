---
title: "Xrandr permanent settings"
date: 2010-11-21
forum: Hardware
---

### Post by Mortesins93 on 2010-11-21
Hello,
I have an ASUS laptop with a monitor hooked up. The laptop's screen doesn't work so I wanted to switch it off and I found the code to do it:
```
sudo xrandr --output LVDS --off
```
Now how do I put this as a permanent setting? I don't want to write it in the terminal everytime I login.
Thank you in advance

---

### Post by IcarusR on 2010-11-21
I believe you can use cron to run commands at boot. Not tried this myself though.
Create a script with your commands.
Edit the crontab with administrative privileges (see the section called "Root And Sudo"):

```
sudo crontab -e
```          

Insert the following line:

```
 @reboot /home/user/your-script
```

Replace /home/user/command with the full address to your script.
Save the file and exit.

Or add the path to your script to the end of /etc/rc.local.

```
/home/use/your-script
```

---

### Post by IcarusR on 2010-11-23
Just tried putting my own xrandr settings in a script & tried both ways I mentioned above to run at boot. Both fail miserably.

---

### Post by Fafler on 2010-11-23
I don't know about your first suggestion, haven't used cron that way.

As for your second, place if after the line saying
```
do_start() {

```

But it is still bad practice, as this is a boot script and might be executed before X is up and running. In that case, the script fails silently.

A place to put it would be ~/.xinitrc
Follow this guide to do so and learn how it works: [https://wiki.ubuntu.com/CustomXSession](https://wiki.ubuntu.com/CustomXSession)

Or even better, from the terminal, do:
```

echo "sudo xrandr --output LVDS --off" | sudo tee  /etc/X11/Xsession.d/70setoutput && sudo chmod +x /etc/X11/Xsession.d/70setoutput

```

Log out/in and enjoy ;-)

---

### Post by IcarusR on 2010-11-23
Fafler

> /etc/X11/Xsession.d/70setoutput

Works, have put the whole command in it rather than use it to call a script.

---

### Post by Mortesins93 on 2010-12-03
Fafler
I tried doing what you said but it doesn't work, so should the 70setoutput file exist already? If so, I don't have it. I created it and I wrote  the command in it and I added the execution permission and it does not work. What kind of script should it be? Should I put the "#!/bin/bash" at top of the file?
It is not a big problem because i created a script with a launcher on my top bar, I just have to click on it to shut the screen off, it's not a big deal.
Thank you anyways

---

