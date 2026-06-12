---
title: "searched &amp; tried various ATi Driver installs, no luck"
date: 2008-10-22
forum: Hardware
---

### Post by boosted on 2008-10-22
I need some expert help here.  I have tried a couple ways to get the ATi card on my HP laptop working.  Every time I go to reboot X fails to start.  I have to go edit xorg.conf and put vesa in there instead of fglrx.  

Here is the output of lspci | grep -i vga

```

01:05.0 VGA compatible controller: ATI Technologies Inc Radeon IGP 330M/340M/350M

```

Is this card even supported?
Please help me out with this....

Thanks

---

### Post by Isilion on 2008-10-22
Hi. Dont worry, i think i have the solution :) 
I have an ATI radeon 9800 pro and i had the same problems like you, and like a lot of users if you search in this forum. ATI driver cannot install by itself for some unknown reason. Here is how to install fglrx properly:

1st way. the easyest. Navigate trhough Applications/System/Software origins and activate multiverse, and activate canonical repositories. Then in console type "sudo apt-get update". when finished, open synaptic and search for "xorg-driver-fglrx" and related packages. Download and reboot. If you fail at getting to login screen use "xfix", and try 2nd way...

2nd way. manually.follow these steps:

-Download the driver from the ATI's website. then:

sudo apt-get install build-essential fakeroot dh-make debconf dkms cdbs 
debhelper libstdc++5 linux-headers-$(uname -r)

sh ati-driver-installer-8-9-x86.x86_64.run --buildpkg Ubuntu/hardy  <-- in my case that was drivers name, but use your drivers name instead

sudo gedit /etc/default/linux-restricted-modules-common

Add fglrx to DISABLED_MODULES in between the quotes.

sudo dpkg -i xorg-driver-fglrx_8.542-0ubuntu1_i386.deb fglrx-kernel-source_8.542-0ubuntu1_i386.deb fglrx-amdcccle_8.542-0ubuntu1_i386.deb xorg-driver-fglrx-dev_8.542-0ubuntu1_i386.deb fglrx-modaliases_8.542-0ubuntu1_i386.deb

sudo aticonfig --initial -f

then reboot. You may access to login screen without problems. if not, i cannot help you, but read this thread ([http://ubuntuforums.org/showthread.php?t=766699](http://ubuntuforums.org/showthread.php?t=766699))

if you success to login, open a console and type "fglrxinfo". You should see ATI. Also type "glxgears;fgl_glxgears" and run both gears to check GL is ok.

At this point, try to launch Compiz os some 3D game like TuxCart. I cannot tell for sure it works... as in my case. All is perfectly installed, but ATI's driver simply suck. Im using an  ATI Radeon 9800 Pro (if someone uses that card and works for him, tell me how plz)

---

### Post by Milkium on 2008-10-22
And if what they person above me said does not work, try using EnvyNG.

You can get it here: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

It does everything for you. :)

---

### Post by boosted on 2008-10-22
I did your first method and rebooted and I was able to log in.
I did this only:
1st way. the easyest. Navigate trhough Applications/System/Software origins and activate multiverse, and activate canonical repositories. Then in console type "sudo apt-get update". when finished, open synaptic and search for "xorg-driver-fglrx" and related packages. Download and reboot.

If there were more steps to that please let know.
When I tried fglrxinfo I get:
Mesa and not ATi  ???

Under System, Hardware Drivers there is no ATi driver just my WiFi.


I tried EnvyNG before I started this thread and that did not work.

---

### Post by boosted on 2008-10-22
any ideas?

---

### Post by ardvark71 on 2008-10-22
> **boosted said:**
> any ideas?

Hi...

What is the driver listed in your xorg.conf file?

Best Regards...

---

### Post by boosted on 2008-10-22
well right now it is "vesa"
I kept having to change it to that when fglrx made X fail to start.
I have found out that my card is not supported by fglrx.  I need to find ati drivers for the 330m/340m/350m  I have searched, but no luck with that.  I hope some experienced Linux user can help me get this working.  Thanks

---

### Post by ardvark71 on 2008-10-22
> **boosted said:**
> well right now it is "vesa"
I kept having to change it to that when fglrx made X fail to start.
I have found out that my card is not supported by fglrx.  I need to find ati drivers for the 330m/340m/350m  I have searched, but no luck with that.  I hope some experienced Linux user can help me get this working.  Thanks

Hi...

Others have had your same problem. I'm not sure how much this will help or if it will entail a change of Ubuntu versions but you can try the suggestions in this thread...

[http://ge.ubuntuforums.com/showthread.php?t=579596&](http://ge.ubuntuforums.com/showthread.php?t=579596&)

Best Regards...

---

### Post by boosted on 2008-10-23
tried using 'wargames' xorg.conf file example and again X failed to start.
[http://ge.ubuntuforums.com/showthread.php?t=579596&page=2](http://ge.ubuntuforums.com/showthread.php?t=579596&page=2)

Am I forgetting something.... doing something wrong?  I just don't understand why this won't work.  Very aggravating.

---

### Post by Dreamlocked on 2008-10-23
Have you tried the open source driver? There is an Ubuntu guide [here]("https://help.ubuntu.com/community/RadeonDriver").

If you still can't get into X after following this guide (don't forget to replace 'vesa' with 'ati' in your xorg.conf), then try replacing
```

Option          "AGPMode"        "8"

```

with 
```

Option          "AGPMode"        "1"

```

It's a little something I had to do to get my ATI radeon mobility 9700 working.

Edit : 
For any driver you try, try disabling AIGLX. It can sometimes cause problems too.
```

Section "ServerLayout"
        [...]
        Option          "AIGLX"         "false"
        [...]
EndSection

```

---

### Post by boosted on 2008-10-23
Well X started up fine.
I tried to just Enable the Normal Visual Effects and I got:
Desktop effects could not be enabled.

Am I missing something?  This card should at least be able to do the Normal setting.

edit:
glxinfo | grep "direct rendering"
shows
direct rendering: Yes

---

### Post by Dreamlocked on 2008-10-23
Run the following command :
```

grep "AIGLX" /var/log/Xorg.0.log

```
If it doesn't say "enabled", for Desktop effects, you need to re-enable AIGLX. Change false to true from my previous post, like so:

```

Section "ServerLayout"
        [...]
        Option          "AIGLX"         "true"
        [...]
EndSection

```

If you still get errors, I guess it would be helpful to post the outputs of
```

grep "(EE" /var/log/Xorg.0.log

```
and 
```

grep "(WW" /var/log/Xorg.0.log

```

---

### Post by Isilion on 2008-10-23
> **Milkium said:**
> And if what they person above me said does not work, try using EnvyNG.

You can get it here: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

It does everything for you. :)

Ill tell you that y use EnvyNG only for uninstall drivers only. EnvyNG for some reason fails too at installing ATI drivers. 

Anyway did you tryed 2nd way? that fixes xorg.conf pretty easy

---

