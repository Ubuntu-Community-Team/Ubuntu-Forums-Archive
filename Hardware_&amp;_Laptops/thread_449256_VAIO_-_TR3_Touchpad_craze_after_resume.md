---
title: "VAIO - TR3 Touchpad craze after resume"
date: 2007-05-20
forum: Hardware &amp; Laptops
---

### Post by bence8810 on 2007-05-20
Hi,

On my laptop when I resume, I wont be able to scroll on the right side of the touchpad, which is an excellent function otherwise.

Should I modify my resume.sh and if so, how to get my scrolling back to work?

Also the touchpad is quite sensitive, and often time it picks up a tap which was not meant to be a tap, and this launches unnecessary applications, etc.

Thanks for any help,

Ben

---

### Post by bence8810 on 2007-05-20
Hi

The tapping sensitivity is solved by adding the following it my synaptic config in the xorg.conf

```
Option          "MaxTapTime"            "0"
```

Now it looks like this:

```
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
        Option          "MaxTapTime"            "0"
EndSection

```

What this does is to disable the Tapping on the touchpad, so when I want to click, i have to use the buttons below the pad. This I dont like 100%, but much better than the crazy touchpad.

If you play with the MaxTapTime variable, I think you can make the touchpad less sensitive. By default X takes the value of 180, and now I have it on 0. Between the two somewhere might be my ideal solution, but for now, I am happy its fixed by killing tapping.

The only outstanding thing remains the Resume-error of the scrolling.

This only happens from time to time, so its rather odd.

Any similar experience?

Thanks

Ben

---

### Post by magicrobotmonkey on 2007-05-23
yea i just started having the no scrolling on resume thing this week. Strangly, I have tapping disabled, but when the scrolling isn't working, tapping is, even though it shouldnt be. So its lik e the config is lost or something. I tried restarting X to reload the config in xorg.conf, but that didn't bring it back. Not sure what else to look at.

---

### Post by bence8810 on 2007-05-24
Hi

Yes, its the same for me. Tapping is re-enabled after the scrolling is lost. Its really annoying.

For me, the laptop mostly survives the 1st resume, and will start to freak out after that. Strangely, sometimes if I resume again after it has failed, it may come back to real life.

I wonder if there is anything we can incorporate in the resume script that will surely bring back the touchpad to live with real working conditions.

Any help is appreciated,

Ben

---

### Post by bence8810 on 2007-05-24
Hi

I kept testing for a while, and saw the following:

The first resume after a reboot is always successful, in terms of getting the Touchpad back in a state it should be. After the first resume, it is kind of rhapsodic, at times it works like it should, and at times it comes back with re-enabled tapping and scrolling not working.

If I suspend again, and resume, it starts working like it should. If I suspend and resume again, it may or may not brake.

It seems that it depends on something, but cannot make the links yet. Anybody with some ideas, or similar behaviour?

Thanks

Ben

---

### Post by leadweight on 2007-06-07
Same problem, no scrolling after second resume, SZ330PB.

Workaround is Ctrl-Alt-F1 followed by Ctrl-Alt-F7.

Its really too much trouble, login, keyring and reviving the touchpad, so I gave up.

---

### Post by bence8810 on 2007-06-07
By giving up you mean you give up on fixing it, and you do the CTRL ALT F1 and F7 back?

This way I assume you dont lose anything open? What I do it (CTRL + BACKSPACE)x2 this restarts X, but I lose everything, and have to type password, keyring, etc. Quite annoying.

I wonder if this CTRL ALT Fx works, can we script it in the resume script? I had to do it once with a Dell700m I had, so I can dig that up from somewhere.

Cheers

Ben

---

### Post by Laterix on 2007-06-08
> 
Workaround is Ctrl-Alt-F1 followed by Ctrl-Alt-F7.

Thanks for the tip! This is much better than reboot or restarting X

---

### Post by bence8810 on 2007-06-08
Hi,

I am not at home, but I dag up the script I wrote for an other laptop. Here it is:

```
#!/bin/bash

lid_state=/proc/acpi/button/lid/LID0/state

test -e $lid_state || exit 0

if cat $lid_state | grep closed > /dev/null
  then echo "lid closed -> suspending"
  rmmod ipw2200
  rmmod b44
  echo "mem" > /sys/power/state
  modprobe i830
  /root/emu/video_post
  chvt 1
  chvt 7
  modprobe ipw2200
  modprobe b44
  /etc/init.d/networking restart

else echo "lid opened -> resuming"
fi

```

And I believe this is the part that changes to 1 and then back to 7

```
  chvt 1
  chvt 7
```

As I am not home, I am unable to test it. Can someone check and see if it works?

Thanks, cheers

Ben

---

### Post by bence8810 on 2007-06-10
Hi,

I have solved the problem with the above mentioned help regarding the CTRL ALT F1 and F7. Here is what I did to automate the process. Of course if someone ever discovers the real reason why this problem occurs, I would like to know. Meantime here is the workaround how to get back a fully functioning touchpad on several Sony Vaios (But surely on the TR series).

```

##### At console #####
cat > /etc/acpi/resume.d/92-virtscreenchange.sh
chvt 1
chvt 7
CTRL + D (you actually have to press this, not write it)
##### We are now back at console #####
chmod 755 /etc/acpi/resume.d/92-virtscreenchange.sh
/etc/init.d/acpid restart

```

Once done with that, just suspend and resume back. You will see just after you get the password prompt your screen will briefly go to VT1 then back to VT7 where your Ubuntu desktop is located at.

So to sum it up, you need a file xx-name.sh in /etc/acpi/resume.d/ where xx represents a number between 01 and 99. Based on this number your script will be executed in a timely manner, 01 first, and 99 last. 

The file needs to contain

```
chvt 1
chvt 7
```

And it needs to be executable. Then a quick restart to acpid, and we should be ready to go. 

Hope this works for others as well as it did for me,

Cheers

Ben

---

### Post by leadweight on 2007-06-10
Well, I am glad that I bumbled into something useful.

How do you do the following:

Quote:
And it needs to be executable. Then a quick restart to acpid, and we should be ready to go.


Is there something that has to be done to the .sh file to make it executable?

---

### Post by bence8810 on 2007-06-10
Hi

It just needs to be executable, meaning that the file can not only be read and written to, but also executed.

If you are not familiar with permissions, read the man page of CHMOD, and you can also find lots of info on google about it.

For your quick fix, just do:
```

chmod 755 /etc/acpi/resume.d/xx-whateveryounamedit.sh
```

This should do it,

Cheers

Ben

---

### Post by leadweight on 2007-06-11
Yippie, I have this fix working on my SZ330!

I used gedit to create the script and changed the permissions using Nautilus and right clicking on the file.  The command lime may have unlimited power, but some of us are not so enabled.  Also I managed to get pam keyring to work so now waking the machine is a one password operation.

---

### Post by bence8810 on 2007-06-12
Nice, I am glad it works. And hope it works for others too.

Cheers

Ben

---

