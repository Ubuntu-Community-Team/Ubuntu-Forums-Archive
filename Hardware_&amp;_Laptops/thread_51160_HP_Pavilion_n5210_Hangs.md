---
title: "HP Pavilion n5210 Hangs"
date: 2005-07-22
forum: Hardware &amp; Laptops
---

### Post by Jade Robbins on 2005-07-22
Hey guys, i installed ubuntu on my hp pavilion n5210 and install went fine, and it will even run in gnome as long as i don't do anything. But if i try to open the device manager, synaptic, or even if i surf in firefox too long it hangs up and i have to do a hard  reboot. It usually does some sort of goofy graphics thing when it freezes so i'm thinking maybe it might be a video card oddity?

I've tried just about everything i can think of to see what could be causing it to freeze (on batteries, plugged in, tried KDE but it doesn't last long) and any possible suggestions or ideas i would appriciate it.

---

### Post by Jade Robbins on 2005-07-25
[QUOTE=Jade Robbins]Hey guys, i installed ubuntu on my hp pavilion n5210 and install went fine, and it will even run in gnome as long as i don't do anything. But if i try to open the device manager, synaptic, or even if i surf in firefox too long it hangs up and i have to do a hard  reboot. It usually does some sort of goofy graphics thing when it freezes so i'm thinking maybe it might be a video card oddity?

I've tried just about everything i can think of to see what could be causing it to freeze (on batteries, plugged in, tried KDE but it doesn't last long) and any possible suggestions or ideas i would appriciate it.[/QUOTE]
 bump for any sort of help?

---

### Post by kokomo on 2005-07-25
Hey Jade, I've got the same problem with my new HP Pavilion zv6000.. It hangs when I login through gnome unless I switch to another terminal, but when I run something, like you said, it'll hang.  Let me know if you find a fix for this.  Thanks!

---

### Post by Jade Robbins on 2005-07-27
[QUOTE=kokomo]Hey Jade, I've got the same problem with my new HP Pavilion zv6000.. It hangs when I login through gnome unless I switch to another terminal, but when I run something, like you said, it'll hang.  Let me know if you find a fix for this.  Thanks![/QUOTE]
 bump for any help with even TRYING to diagnose a problem?!?!

---

### Post by Jade Robbins on 2005-07-28
[QUOTE=Jade Robbins]bump for any help with even TRYING to diagnose a problem?!?![/QUOTE]

no one?!?!?

---

### Post by supanova on 2005-07-28
Hi Jade

Let me guess you have an intel chipset something like the i915 (onboard)?

Type in

```
lspci
``` 

and post the results.

Also post your /etc/X11/xorg.conf file as well as whatever you find in /var/log/Xorg.0.log

There is a lot of known hassles with the Intel chipsets...

Ciao

---

### Post by Jade Robbins on 2005-07-29
[QUOTE=supanova]Hi Jade

Let me guess you have an intel chipset something like the i915 (onboard)?

Type in

```
lspci
``` 

and post the results.

Also post your /etc/X11/xorg.conf file as well as whatever you find in /var/log/Xorg.0.log

There is a lot of known hassles with the Intel chipsets...

Ciao[/QUOTE]
 allright i'm on it right now! the hard part is posting the results because it usually crashes before i can do much, i'll try to save them as a text file as quickly as possible though ;)

---

### Post by Jade Robbins on 2005-07-29
Here are those files! Thank you soooo much for any help you can give me :D

edit: lemmie host the log file on my webserver, one sec
edit2: [http://www.jaderobbins.com/Xorg.0.log.txt](http://www.jaderobbins.com/Xorg.0.log.txt)

Thanks again!

---

### Post by supanova on 2005-07-29
Hi Jade

You don't have a crappy intel chipset but Savage. 

Although it's also builtin as your lspci does not show an AGP bridge or anything

Try this:

```


Section "Device"
	Identifier	"S3 Inc. 86C270-294 Savage/IX-MV"
	Driver		"savage"
	BusID		"PCI:1:1:0"
                Option    "ShadowStatus" "true"
#                Option    "NoAccel"
EndSection

``` 

Also your monitor looks all wrong

```

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-38
	VertRefresh	43-72
EndSection

```

I would leave the Sync and Refresh out unless it's not detected your value look strange... but could be right if your using a laptop

You'll is the other section I have a "NoAccel" option commented out... if the "ShadowStatus" option does not work then try this.

Ciao

---

### Post by Jade Robbins on 2005-07-29
[QUOTE=supanova]Hi Jade

You don't have a crappy intel chipset but Savage. 

Although it's also builtin as your lspci does not show an AGP bridge or anything

Try this:

```


Section "Device"
	Identifier	"S3 Inc. 86C270-294 Savage/IX-MV"
	Driver		"savage"
	BusID		"PCI:1:1:0"
                Option    "ShadowStatus" "true"
#                Option    "NoAccel"
EndSection

``` 

Also your monitor looks all wrong

```

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-38
	VertRefresh	43-72
EndSection

```

I would leave the Sync and Refresh out unless it's not detected your value look strange... but could be right if your using a laptop

You'll is the other section I have a "NoAccel" option commented out... if the "ShadowStatus" option does not work then try this.

Ciao[/QUOTE]
 Holy Crap! that seems to have worked!  Didn't even have to do the NoAccel. Thank you so much sir, you are my hero!!!

---

### Post by Jade Robbins on 2005-08-01
[QUOTE=Jade Robbins]Holy Crap! that seems to have worked!  Didn't even have to do the NoAccel. Thank you so much sir, you are my hero!!![/QUOTE]
 The only problem i'm having now is periodic hangs where i can't do anything until it's done thinking. It works and everyhting, it's just a pain in the buttox. Any other ideas? :D

---

